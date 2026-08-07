# Illuvia — Privacy policy

**Last updated: 6 August 2026 · Applies to Illuvia 1.0.0 for Windows**

## The short version

Illuvia does not collect anything. It has no servers, no accounts and no
analytics, and it makes no network connections of its own. Everything you type
stays in files on your PC, under your Windows account.

## What Illuvia stores, and where

Everything you enter — tasks, checklists, transactions, accounts, payment plans,
wishlist items, vehicles, settings — is written to files in your own user
folder:

```
%APPDATA%\Gagofed\Illuvia\database\
```

That is the folder whether Illuvia was installed from the Microsoft Store or
run from a plain build: the data does not live inside the installed package.

Those files are **encrypted at rest** with AES-256. The key is generated on your
PC the first time Illuvia runs and is kept in the Windows Credential Manager,
protected for your Windows account (DPAPI). It is never derived from your PIN or
password, and it never leaves the machine. Someone copying the files to another
PC, or reading them from another Windows account, cannot decrypt them.

Illuvia also writes a plain-text diagnostic log:

```
%APPDATA%\Gagofed\Illuvia\logs\illuvia.log
```

It records what the app did — which module loaded, how many records were read,
what an error said — so a problem can be understood after the fact. It is
capped at 5 MB with up to three rotated files, it is never sent anywhere, and
you can delete it at any time. It is not encrypted, so if you send it to us for
support, read it first.

## What Illuvia does not do

- **No data collection.** No usage statistics, no crash reporting, no analytics,
  no advertising, no profiling, no identifiers of any kind.
- **No accounts.** There is nothing to register, and no e-mail address is
  required to use the app.
- **No network.** The app package declares no internet capability, and the
  application makes no requests. It works with the network cable unplugged.
- **No third parties.** Nothing you enter is shared with anyone, because there
  is no one to share it with.

## The two times something leaves the app

**Opening a link.** If you save a shop link with a wishlist item, or use the
donation link, tapping it hands the address to your default browser. From that
point on you are on that website, under its privacy policy, not ours. Illuvia
itself does not fetch the page.

**Making a backup.** A backup is one file holding everything, saved where you
choose. You decide how it leaves the machine:

- **Export without a password** (the default). The file is written as readable JSON.
  This is the one way to inspect a backup or to open it with anything other than
  Illuvia, and it is exactly as private as the place you put it. If you have
  saved service credentials on a payment plan (see below), Illuvia warns you
  before writing: they are in that file in plain text.
- **Export with a password.** The file is sealed with AES-256, using a key
  derived from your password (Argon2id). It can be restored on any machine, and
  it cannot be opened without that password — nobody can recover it for you.

The copies Illuvia writes for itself — the automatic ones, and the safety copy
taken before a restore or an import — are always sealed with this PC's key.
They stay in Illuvia's own folder, and uninstalling the app leaves them there
along with everything else.

## Passwords you save for other services

A payment plan can hold the username and password of the service it pays for —
your electricity account, a subscription — because that is where you look for
them. They are stored like every other field: in the database, encrypted at
rest, on this PC only. They are never sent anywhere, and Illuvia has no way to
use them for anything.

Two things follow. They travel inside a backup, which is what makes a restore
put your data back as it was; and an **unprotected export** therefore contains
them in plain text, which is why Illuvia warns you before writing one.

## The app lock

The PIN or password that opens Illuvia is a different thing, and it is never
stored. What is stored is an Argon2id hash of it, with a random salt, in the
Windows Credential Manager alongside the encryption key. Windows Hello, if you
enable it, is handled entirely by Windows; Illuvia receives only a yes or no and
never sees biometric data.

## Deleting your data

Settings → Security → *Empty every module* erases everything you have entered.
Next to it, *Erase all data* also removes the encryption key and the
credential, which is what the "I forgot my PIN" flow does.

**Uninstalling Illuvia does not delete your data.** Windows removes the
application and leaves the folders above where they are, so that reinstalling
finds everything as you left it. If you want the data gone as well, use one of
the two commands first, or delete `%APPDATA%\Gagofed\Illuvia\` yourself — that
folder holds the database, the log and the automatic copies.

Backups you exported yourself are never touched by any of these — only you know
where they are.

## Children

Illuvia is a general-purpose personal organiser. It is not directed at children
and collects no information from anyone, of any age.

## Changes to this policy

If a future version of Illuvia ever changes what it does with your data, this
page will be updated before that version is published, and the change will be
described in the release notes.

## Contact

Questions about this policy: **illuvia.dev@gmail.com**
