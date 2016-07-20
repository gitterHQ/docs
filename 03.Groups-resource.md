# Groups


## Group schema

 - `id`: Group ID.
 - `name`: Group name.
 - `uri`: Group URI on Gitter.
 - `backedBy`: Security descriptor. Describes the backing object we get permissions from.
    - `type`: `[null|'ONE_TO_ONE'|'GH_REPO'|'GH_ORG'|'GH_USER']`
    - `linkPath`: Represents how we find the backing object given the type
 - `avatarUrl`: Base avatar URL (add `s` parameter to size)


## List Groups

List groups the current user is in.

### Parameters

 - *none*

```
GET /v1/groups
```

Try it from the CLI:
```
'demo api-access';
{
  "verb": "get",
  "resource": "{{api_url}}/v1/groups"
}
```

```json
[
  {
    "id": "57542c12c43b8c601976fa66",
    "name": "gitterHQ",
    "uri": "gitterHQ",
    "backedBy": {
        "type": "GH_ORG",
        "linkPath": "gitterHQ"
    },
    "avatarUrl": "http://gitter.im/api/private/avatars/group/i/577ef7e4e897e2a459b1b881"
  },
  {
    "id": "577faf61a7d5727908337209",
    "name": "i-love-cats",
    "uri": "i-love-cats",
    "backedBy": {
        "type": null
    },
    "avatarUrl": "http://gitter.im/api/private/avatars/group/i/577faf61a7d5727908337209"
  }
]
```



## Create Group

**This is a private API.** You need to use the Gitter ecosystem to start a community.

### Parameters

 - `name`: Group name.
 - `uri`: Group URI on Gitter.
 - `security`: Security descriptor. Describes the backing object we get permissions from.
    - `type`: `[null|'ONE_TO_ONE'|'GH_REPO'|'GH_ORG'|'GH_USER']`
    - `linkPath`: Represents how we find the backing object given the type
 - `invites`: Array of users
    - `username`: Gitter username
    - `githubUsername`: GitHub username
    - `twitterUsername`: Twitter username
    - `emailAddress`: Manual email address


Try it from the CLI:
```
'demo api-access';
{
  "verb": "post",
  "resource": "{{api_url}}/v1/rooms",
  "data": {
    "uri": "gitterhq/sandbox"
  }
}
```


## Group sub-resources

### Rooms

#### List rooms under group

List of rooms nested under the specified group.

```
GET /v1/groups/:groupId/rooms
```

Try it from the CLI:
```
'demo api-access';
{
  "verb": "get",
  "resource": "{{api_url}}/v1/groups/57542c12c43b8c601976fa66/groups"
}
```


#### Create room under group

**This is a private API.** You need to use the Gitter ecosystem to create a room.

Create room nested under the specified group.

### Parameters

 - `name`: Room name.
 - `topic`: Room topic/description
 - `security`: Security descriptor. Describes the backing object we get permissions from. (defaults to `'PUBLIC'`)
    - `security`: `'PUBLIC'|'PRIVATE'`
    - `type`: `null|'ONE_TO_ONE'|'GH_REPO'|'GH_ORG'|'GH_USER'`
    - `linkPath`: Represents how we find the backing object given the type
 - `source`: Tracking info for stats

```
POST /v1/groups/:groupId/rooms
```

Try it from the CLI:
```
'demo api-access';
{
  "verb": "post",
  "resource": "{{api_url}}/v1/groups/57542c12c43b8c601976fa66/groups",
  "data": {
     "name": "gitterhq/sandbox"
  }
}
```
