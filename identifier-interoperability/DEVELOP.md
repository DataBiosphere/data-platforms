# Development for the Identifier Interoperability Document

## minid Registration

As a demonstration of how to use minids, this repository has been given
a minid using the below method:

### Install dependencies

I started by [generating an ORCID](https://orcid.org/my-orcid) for myself, if you haven't already done
so. This helps with provenance for identifiers you ask to have created.

The minid client is available via pypi and is in the `requirements.txt`
of this repository.

```
virtualenv env
source env/bin/activate
pip install -r requirements.txt
```

### Create a minid account

Then following the directions from https://github.com/fair-research/minid

```
minid --register_user --email <email> --name "<name>" --orcid  0000-0001-6683-2270
```

I received an email with a code that will be added to the registration 
process later.

### Test Register an Item

We want to register the README.md of this document, and hopefully some way 
it can be retrieved. From the directory of this repository:

```
✗ minid --register --title "Identifier Interoperability" README.md --locations "https://raw.githubusercontent.com/DataBiosphere/identifier-interoperability/master/README.md" "https://github.com/DataBiosphere/identifier-interoperability/blob/master/README.md" --code <MY_CODE> --test
2018-04-25 08:23:24,886 - INFO - Computing checksum for README.md using None
creating algorithm
2018-04-25 08:23:24,886 - INFO - Checking if the TEST entity 690a921e4a076fe889fdee13791b50a79e9a9d636cdb3ac1cd015b1991e43d01 already exists on the server: http://minid.bd2k.org/minid
2018-04-25 08:23:25,085 - INFO - Creating new identifier
2018-04-25 08:23:26,856 - INFO - Created/updated minid: ark:/99999/fk40p28s1b
```

Great, we generated a test ARK using a minid that could be registered 
at the bd2k minid service!

Let's do it one more time, but this time remove the `--test` flag.

```
minid --register --title "Identifier Interoperability" README.md --locations "https://raw.githubusercontent.com/DataBiosphere/identifier-interoperability/master/README.md" "https://github.com/DataBiosphere/identifier-interoperability/blob/master/README.md" --code <MY_CODE>
2018-04-25 08:30:13,663 - INFO - Computing checksum for README.md using None
creating algorithm
2018-04-25 08:30:13,664 - INFO - Checking if the entity 690a921e4a076fe889fdee13791b50a79e9a9d636cdb3ac1cd015b1991e43d01 already exists on the server: http://minid.bd2k.org/minid
2018-04-25 08:30:13,879 - INFO - Creating new identifier
2018-04-25 08:30:15,672 - INFO - Created/updated minid: ark:/57799/b93t21
```

Now we have a real minid for this document! You can test it out by using
an identifier resolver like [n2t.net](https://n2t.net).

http://n2t.net/ark:/57799/b93t21

This also points us to the host authority, minid.bd2k.org, that hosts a 
service that can return a JSON form of our minid document.

```
curl -H "Accept: application/json" http://minid.bd2k.org/minid/landingpage/ark:/57799/b9040f
{ [.....]
      "link": "https://github.com/DataBiosphere/identifier-interoperability/blob/master/README.md", 
      "uri": "https://github.com/DataBiosphere/identifier-interoperability/blob/master/README.md"
  [.....] }
```

Note that we can see a link to our repository in the minid service's
metadata!

### Updating a minid

When changes are made that should be reflected, either in the checksum, maintainer, or list of
URLs, the minid Python client can be used again, `minid --update`.

