================================
UserGroup Membership Certificate
================================

Summary
=======

Bob, as a friend of Alice, is automatically granted the right to get the AES keys which can decrypt the posts of Alice, because Alice told the world that whoever that can prove their ownership of the Facebook account of Bob can get them. This is a proof of membership of Bob in the UserGroup whose construction is "all friends of Alice".

Siri, as a friend of Alice, will notify Alice their friendship if Alice fails to notice that.

Background
==========

This concept is designed for the implementation of [[cooperative friendship discovery mechanism]] and [[saturation key retrieval mechanism]].

Purpose
=======

See [[UserGroup Abstraction Model]].

Algorithms
==========

Payload Structure (v1)
======================

Input for EC_Sign
-----------------

```
BEGIN-Maskbook-FriendshipCertificate-PAYLOAD
Network: Facebook~2019
Time: 1554808298340
MyId: neruthes.d5e2f043
FriendId: jackworks
END-Maskbook-FriendshipCertificate-PAYLOAD
```

Input for ECDH_Enc
------------------

```
BEGIN-Maskbook-FriendshipCertificate-PAYLOAD
Network: Facebook~2019
Time: 1554808298340
MyId: neruthes.d5e2f043
FriendId: jackworks
END-Maskbook-FriendshipCertificate-PAYLOAD
BEGIN-Maskbook-Signature-PAYLOAD
XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
END-Maskbook-Signature-PAYLOAD
```

Payload Structure (v2)
======================

Input for EC_Sign
-----------------

```
BEGIN-Maskbook-UserGroupMembershipCertificate-PAYLOAD
Network: Facebook~2019
Time: 1554808298340
UserGroupId: maskbookshanghai
AdminId: neruthes.d5e2f043
MemberId: jackworks
END-Maskbook-UserGroupMembershipCertificate-PAYLOAD
```

Input for ECDH_Enc
------------------

```
BEGIN-Maskbook-UserGroupMembershipCertificate-PAYLOAD
Network: Facebook~2019
Time: 1554808298340
UserGroupId: maskbookshanghai
AdminId: neruthes.d5e2f043
MemberId: jackworks
END-Maskbook-UserGroupMembershipCertificate-PAYLOAD
BEGIN-Maskbook-Signature-PAYLOAD
XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
END-Maskbook-Signature-PAYLOAD
```
