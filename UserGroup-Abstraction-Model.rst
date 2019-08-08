==================================
Saturation Key Retrieval Mechanism
==================================

Purpose
=======

Every group of users, virtual or real, static or dynamic, should be identifiable across every node of the network and every member of the group should be able to retrieve necessary keys to decrypt the contents which they legitimately qualify decrypting by providing certain proof of their membership of the group.

Basics
======

Example
-------

In the context of Facebook, specifically, there are several scenarios how people interact in timelines.

=============== ================================= ===============================================================================
Type            Description                       Group ID
=============== ================================= ===============================================================================
Virtual Group   Friends of Alice                  `FB::{ fb_uid_Alice }>>>F0`
Virtual Group   Friends of friends Alice          `FB::{ fb_uid_Alice }>>>F1`
Virtual Group   Certain selected friends of Alice `FB::{ fb_uid_Alice }>>>FS>>>{ SHA512({ fb_uid_Bob }+{ fb_uid_Siri }+...) }`
Real Group      Closed Group                      `FB::{ fb_uid_Group }>>>G0`
=============== ================================= ===============================================================================

In order to make sure the Group ID being constructed can be universally unique in the cosmos of Maskbook, in respect to expectation on portability to other social networks, I suggest composing it in such a way.

Rules
-----

**Basic Parts**

- Social network identifier, `[0-9A-Z\-]{2,128}`
- 2 colons, `::`
- Group primary identifier (publisher UID for virtual group, group UID for real group), base64 if necessary (supposedly never)

**Optional Parts**

- 3 greater marks, `>>>`
- Group type code, `[0-9A-Z]{2,8}`
- 3 greater marks, `>>>`
- Group secondary identifier (defined in each scenario)

**Default Generation of Group Secondary Identifier**

- Make an ordered array of UIDs of participating members, sorted by Unicode dictionary order.
- Join the array by `+++` to make a string.
- Calculate SHA512 of the string and the output encoding should be hex uppercase.

Authority
=========

Every UserGroup must have at least 1 administrator who manages the issuance and revocation of membership of the UserGroup. Each category of UserGroup may have their respective administrator selection policy.

For example, the `F0` group of Alice is administered by and only by Alice herself, and a closed group is administered by its public administrators.

The basic principle is, a group is administered by those who are publicly endorsed by the social network service to be eligible moderators of the group.

Change of Username
==================

Change of username may occur, although infrequent.
