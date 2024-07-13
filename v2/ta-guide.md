# CSXL Application v2 Guide for Existing Developers

> Written by Ajay Gandecha for the CSXL Web Application and for COMP 423: Foundations of Software Engineering.<br>
> *Last Updated: 7/13/2024*

👋 Hey, Ajay here - I hope you had a teriffic summer! A significant amount has changed in XL site since LDOC (full changelog 👀: [`v1.7.0...v1.10.5`](https://github.com/unc-csxl/csxl.unc.edu/compare/v1.7.0...v1.10.5)). In the time since May, the CSXL repo has gone through many changes:
* Upgrade to the latest Angular version with many new features and conventions
* Upgrade from Material 2 to the new Material 3 design system, standard to the most modern Android OS release.
* Many new features and refactors to existing features, including:
  * "My Courses" feature and Office Hours
  * Hiring of UTAs
  * *many existing features redesigned!*

The goal of this document and accompanying resources is to walk through all of these changes. ***If you will be a UTA for COMP 423 in the Fall or develop for the CSXL site, read this carefully!*** There will also be accompanying resources and videos where needed as well.

✨ If you have any questions throughout, please reach out to me on the CSXL Slack! ✨

## Table of Contents
1. [Chapter I: Upgrade to Angular v18](#ch1)
2. [Chapter II: Adoption of Material 3](#ch2)
3. [Chapter III: New Features](#ch3)
4. [Chapter IV: New Features](#ch4)


# Chapter I: Upgrade to Angular v18 <a name="ch1"></a>

This chapter will di

## Introduction to Reactive Objects using Angular Signals

One of the most significant changes in the Angular upgrade transforms how we deal with ***"reactive objects"*** in our Angular components and service. Reactive objects allow us to create objects in our *component TS* code such that, when its value changes, the screen automatically updates to reflect its new value.

Consider the following example. On the CSXL site, the site admin is able to *create, edit, and delete* the organizations that appear on the Organizations page. On this admin page, there is a "Delete" button next to every organization. When we press this button, we want to (1) delete the organization via an API call, then (2) update the page to no longer show the deleted organization.

Consider the following component:

<table>
 <tr><th width="520">`OrganizationAdminComponent` - TS</th><th width="520">`OrganizationAdminComponent` - HTML</th></tr>
<tr>
<td>
 
```ts
@Component(...)
class OrganizationAdminComponent {

  // Store the list of organizations
  organizations: Organization[];

  // ... (many items omitted)

  deleteOrganization(slug: string) {
    this.http.delete('/api/organizations/' + slug)
      .subscribe((newOrgList) => {
        this.organizations = newOrgList;
      });
  }
}
```

</td>
 <td>
  
```html
<div>
  <organization-card
    *ngFor="let organization of organizations"
    [organization]="organization"
  />
</div>
```

</td>
</tr>
</table>

This seems simple enough, however in this situation, you would likely notice that the page's content does not update. Many students in COMP 423, my group included, would resort to calling a redirect here, refreshing the page and causing the data to properly update. However, this is a bad user experience, as the screen redirects and flashes white for a few milliseconds after every deletion.

We wanted a way to ensure that we could upate this data and that the UI updates accordingly without having to refresh the page.

This is where the infamous **`RxObject`** was born. You can find the code for `RxObject` [here](https://github.com/unc-csxl/csxl.unc.edu/blob/v1.7.0/frontend/src/app/rx-object.ts).

### Recap of `RxObject`

`RxObject` abstracted a RxJS `Observable`, exposed via the object's `.value$` field, to which frontend UI could subscribe to. `RxObject` also encapsulated a `ReplaySubject` object, which would hold the current state ("value") that the object should be storing.

Recall the relationship between *subjects* and *observers* in COMP 301. Observers *observe* the subject for changes. Whenever the subject changes, observers (those observing) are notified of these changes.

In a more colloquial example, consider a live scoreboard beween UNC and Duke. In this case, the subject would be the scoreboard and the observers are the spectators. Whenever UNC scores, the scoreboard updates, and the observers / spectators are notified of a change in the score.

In RxJS, a `ReplaySubject` is a special type of subject that essentially *replays*, or repeats, whenever a new observer begins to observe it. In our basketball example, this is equivalent to a friend arriving late to the game, but still being able to see the score. Even though the scoreboard only updates whenever a basketball player scores, the current score is still visible on the screen even if changes are not occuring to the score at the moment.

In `RxObject`, the `ReplaySubject` was essentially like the scoreboard that that preserved the current state, or value, that the object was supposed to hold. Then, the `Observable`, which was defined as `value$: Observable<T> = this.subject.asObservable();`, could be subscribed to by the UI to await changes in the subject's value. Any time the value stored by the `ReplaySubject` changed, anyone subscribed to the `.value$` observable would recieve the new update.

`RxObject` was also an *abstract class* that had to be implemented differently depending on the type of value stored. For example, to solve the organization list problem, a [separate `RxOrganizationList` class](https://github.com/unc-csxl/csxl.unc.edu/blob/ff80dd5535d910d84639d036ac01115db7aed89c/frontend/src/app/organization/rx-organization.ts#L13-L32
) was created. This object would then encapsulate a value of type `Organization[]`.

Our example from above can be rewritten using `RxOrganizationList`:
<table>
 <tr><th width="520">`OrganizationAdminComponent` - TS</th><th width="520">`OrganizationAdminComponent` - HTML</th></tr>
<tr>
<td>
 
```ts
@Component(...)
class OrganizationAdminComponent {

  // Store a reactive list of organizations
  organizations: RxOrganizationList;

  // ... (many items omitted)

  deleteOrganization(slug: string) {
    this.http.delete('/api/organizations/' + slug)
      .subscribe((_) => {
        this.organizations.removeOrganization(slug);
      });
  }
}
```

</td>
 <td>
  
```html
<div>
  <organization-card
    *ngFor="let organization of
      (organizations.value$ | async)"
    [organization]="organization"
  />
</div>
```

</td>
</tr>
</table>

This solution worked, and despite its verbosity, was our preferred solution to solving such problems in our codebase whenever we needed our pages to dynamically update. However, as of the newest version of Angular, there is now a better built-in way that transforms how we define and interact with reactive objects. This construction is called the Angular Signal.

### Introduction to Angular Signals

## HTML Syntax Changes


# Chapter II: Adoption of Material 3 <a name="ch2"></a>

## Introduction to Material 3

## The Material 3 Theme

## Implementation of Global Styling through SCSS Files

## Material 3 Conventions

### The `Pane` Widget

# Chapter III: New Site-Wide Conventions <a name="ch3"></a>

## Pagination

### New Pagination Conventions

### Frontend Pagination Abstraction

## Separation of Entities and Models

## SQLAlchemy Conventions

### Using `JoinedLoad` for Querying with Joins

### Indexing for Faster Queries

# Chapter IV: New Features <a name="ch4"></a>

## My Courses Feature

## Hiring Feature
