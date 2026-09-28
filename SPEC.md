# Property Portal Feature Specification

## Product summary

The Property Portal helps people find, list, and manage real estate for sale or rent. The initial market is Yangon and Mandalay, with future cities and townships added through managed location data. The product serves owners, agents, buyers/renters, staff, and administrators.

The web portal is the first user experience. A mobile app follows after the web workflows and API contract are stable.

## Product goals

- Help buyers and renters find suitable properties quickly and confidently.
- Give owners and agents a clear way to create, publish, and manage listings.
- Make listing quality visible through review, reporting, and moderation workflows.
- Give each account role an appropriate dashboard and set of actions.
- Support Yangon and Mandalay at launch, with future locations managed as product data.
- Include rich sample listings for local development and product review.

## Initial release exclusions

- Payments, deposits, escrow, or commission settlement.
- Legal conveyancing, title registration, or ownership verification.
- Automated property valuation.
- Map-drawn search areas.
- Public chat, voice, or video calling.
- Multi-country tax or regulatory workflows.

## People and capabilities

### Owner

- Create, edit, preview, submit, pause, and archive owned listings.
- Add, order, and update listing photos.
- See listing state and moderation feedback.
- Review inquiries about owned listings.
- Manage profile and contact preferences.

### Agent

- Manage listings they own or are assigned to manage.
- Create and update listings for an owner or agency.
- Review assigned inquiries.
- Maintain their public agent or agency profile.

### Buyer/renter

- Browse and filter published listings.
- Save and remove favorite listings.
- Submit inquiries and view inquiry history.
- Report incorrect, duplicate, suspicious, or inappropriate listings.
- Manage profile and contact preferences.

### Staff

- Review submitted listings and moderation queues.
- Publish, request changes, reject, pause, or archive listings as permitted.
- Triage and resolve listing reports.
- Maintain locations, categories, amenities, and other listing reference data.
- View operational activity and moderation history.

### Admin

- Perform staff capabilities.
- Manage users, role assignments, agencies, and staff permissions.
- Manage system settings and review audit history.
- Restore or correct listings and moderation decisions where needed.

## Property discovery

- The home page presents Buy and Rent entry points.
- Visitors can search by text, city, township, category, and transaction intent.
- Search results support price, bedroom, bathroom, floor area, land area, furnishing, and amenity filters as data is available.
- Results can be sorted by newest, price ascending, price descending, or relevance.
- Search state should be shareable and retained when navigating between results and details.
- Listing cards show a representative image, title, location, price, transaction intent, category, and key property facts.
- Empty, loading, and recoverable error states explain what a visitor can do next.
- Public listing detail shows images, price, description, location, facts, amenities, advertiser information, and contact/report actions.
- Exact private addresses and advertiser contact details are not public by default.

## Listing creation and lifecycle

Listing creation collects:

1. Sale or rent intent and property category.
2. Title and description.
3. Price, currency, and rent period when applicable.
4. City and township, with optional more specific location.
5. Property facts such as bedrooms, bathrooms, floors, floor area, land area, year built, furnishing, and parking.
6. Amenities and features.
7. Photos, ordering, captions, and alternative text.
8. Contact preferences.
9. Preview and save/submit actions.

Owners and agents can save work and resume drafts. At least one image is expected before review submission. They can view moderation feedback and correct a listing. A change to a published listing may require review again, according to the moderation policy.

Listing states:

- `DRAFT`: editable and private.
- `SUBMITTED`: awaiting review.
- `CHANGES_REQUESTED`: edits are required before review can continue.
- `PUBLISHED`: visible in public discovery.
- `PAUSED`: temporarily hidden.
- `REJECTED`: not approved for public display.
- `ARCHIVED`: no longer actively marketed.
- `EXPIRED`: no longer current and hidden from public discovery.

Each state change records the previous and new state, the actor, time, and an optional reason. Only authorized server actions can change listing state.

## Categories and locations

Initial categories include land, apartment, house, condo, villa, shop/retail, office, warehouse/industrial, building, room, and other. Categories have display names and may be grouped hierarchically.

Initial cities are Yangon and Mandalay. Location data can follow this hierarchy:

```text
Country or region
└── City
    └── Township
        └── Neighborhood or ward (optional)
```

Location records may include alternate/localized names and coordinates. The initial search experience needs city and township selection.

## Favorites, inquiries, and reports

### Favorites

- Authenticated buyers/renters can save or unsave a published listing.
- Users can view their saved listings.
- Saved searches may be added later with a name and notification preferences.

### Inquiries

- An authenticated buyer/renter can send a message about a listing and choose a preferred contact method.
- The inquiry goes to the owner, assigned agent, or configured listing recipient.
- The sender can see their inquiry history and status.
- The recipient can mark an inquiry new, contacted, in progress, closed, or spam.
- Inquiry submission is protected against spam and excessive requests.

### Reports

Users can report incorrect information, duplicates, suspected fraud, offensive content, wrong location/category, unavailable properties, or another concern. Staff can assign, review, resolve, or dismiss a report and record the outcome.

## Dashboards

### Owner and agent dashboard

- Listing overview with status and moderation feedback.
- Add, edit, preview, pause, and archive listing actions according to access.
- Listing media management.
- Inquiry overview for owned or assigned listings.

### Buyer/renter dashboard

- Favorite listings.
- Inquiry history and status.
- Profile and contact preferences.

### Staff dashboard

- Counts for submitted listings, published listings, unresolved reports, users, and recent inquiries.
- Moderation queue filters for status, location, category, date, and assignee.
- Listing review with content, images, history, and moderation actions.
- Report triage and reference data management.

### Admin dashboard

- Staff dashboard capabilities.
- User and role management.
- Agency and permission management.
- Audit history and system settings.

## Sample content

Development and review data should be repeatable and safe to recreate. It should include:

- Yangon and Mandalay with multiple townships each.
- Each initial property category and both sale and rent listings.
- Varied prices, property sizes, facts, amenities, and listing ages.
- Accounts for all five roles and at least one sample agency.
- Examples of the main listing lifecycle states.
- Sample property images with known usage rights or local fixtures.
- Favorites, inquiries, reports, and moderation history examples as those features become available.
- Fictional names and contact information only. Demo credentials are for local development and must never be used for production accounts.

## Web experience

- Primary pages: home, buy, rent, search results, property details, sign in/register, account, favorites, inquiries, listing dashboard, listing editor, and staff/admin dashboards.
- The experience is responsive, keyboard accessible, and usable with assistive technology.
- Visitors can switch between light and dark appearance; the selected theme is remembered on that device.
- Forms provide clear field-level validation and recoverable error states.
- Listing pages have shareable URLs and useful page metadata.
- The web experience follows the established Property Portal visual system.

## Mobile experience

The mobile app follows the web MVP and supports sign in, browse/search, property details, favorites, inquiries, and selected owner/agent listing tasks. Later enhancements may include notifications, deep links, offline support, and camera-based photo uploads.

## Success criteria for the first usable release

- A visitor can browse and filter sale and rental listings in Yangon and Mandalay and open property details.
- An owner or agent can create a listing with images and see it in their dashboard.
- Buyers/renters can save listings and submit inquiries.
- Staff can review listings and resolve reports.
- Admins can manage users and role assignments.
- All role permissions are enforced by the service, and private contact data is protected.
- Sample content demonstrates the supported roles, locations, categories, and listing lifecycle.
