# Manjaro is not ARCH!
A lot of Manjaro users I have talked to say that Manjaro is just Arch
with an installer. However, this is fundamentally wrong!

Manjaro maintains a separate repository which is not in sync with Arch's
main repositories which means Manjaro is not *just* Arch. To add to that,
even Manjaro wiki states that it is not Arch [1]! To quote the wiki,

> In fact, the differences between Manjaro and Arch are far greater than
> the differences between the popular Ubuntu distribution and its many
> derivatives, including Mint and Zorin.

# Own repository
Manjaro claims to be stable just by delaying packages for a week. This
is not an approach a stable distribution would take at all!

## The problems introduced
If Manjaro had to be actually stable, it needs to hold back the AUR packages
as well. It has to maintain its AUR that is in sync with the Manjaro repos.

Say that a package in the AUR depends on a library, say libxyz. And libxyz is
in the main repos, not in the AUR. The package is updated so that it relies
on the new features introduced in libxyz's version 1.1 however Manjaro delays
packages so libxyz is still on 1.0 in Manjaro. If you update the package in
Manjaro, it will break because Manjaro holds back packages. So the only
way Manjaro can be stable is by literally forking all the Arch related
repositories including the AUR and keeping them in sync.

## Official Statement
Manjaro came out with an official statement that stated that it is the user's fault for having faulty updates[2]. They claim the following:
> When you’re updating your system and you have an issue with any installed package installed - your immediate thought is - the update is at Manjaro fault.
> No - it is not - you are
> While Manjaro provides the updates the result is yours.

This post was problematic for quite a few reasons:
1. It blames YOU, the USER, for the update breaking your system.
2. Manjaro is an entry-level distro, and a simple task like updating shouldn't require you to `chroot` and have to fix the machine
3. Manjaro is based off of Arch, which is much less of a problem to update

# Security
Manjaro is not really a secure distro.

Their own updater had a security vulnerability which wasn't fixed
until recently [3]. This is actually a core package, not an extra or
community package. To quote the list,

> I have discovered an issue with one of your core Manjaro packages,
> `manjaro-system` 20180716-1 and earlier.
> The issue allows a local attacker to execute a Denial of Service,
> Arbitrary Code Execution, and Privilege Escalation attack.

The amount of attacks that can be done due to the vulnerability is a
lot!

The Manjaro updater [4] does all the bad practices that one could do in
a general Linux system and Arch Linux system specifically. Each time
the system updates, they reinstall some packages to "fix" issues and
they use the `--no-confirm` flag (force) everytime they do so and
various other odd sequence of commands which are just as bad, if not
more.

In an update, password less updates in pamac (Manjaro's AUR helper)
were sneaked in and from the look in the issue [5] made concerning this,
the change was made to look like a "feature". This is a major security
issue considering that packages in AUR are not checked by Arch Linux
maintainers (and Manjaro does not maintain its own either). Some AUR
packages were found to be malware in the past. So think about a casual
user (Manjaro's target demographic are not really power users) installing
a harmless-looking AUR package that could potentially mess their system!

# SSL Certificates
Manjaro let their SSL certificates expire not once but twice [6]!
The first time, they asked the users to use a private window and/or change
the system time [7].
The second time when the SSL certificates expired, they did the same [8].

# Links
[1] https://wiki.manjaro.org/index.php?title=Manjaro:_A_Different_Kind_of_Beast

[2] https://web.archive.org/web/20201008153014/https://forum.manjaro.org/t/what-is-wrong-i-am-not-to-blame/30565

[3] https://lists.manjaro.org/pipermail/manjaro-security/2018-August/000785.html

[4] https://gitlab.manjaro.org/packages/core/manjaro-system/blob/master/manjaro-update-system.sh#L34

[5] https://gitlab.manjaro.org/applications/pamac/issues/719

[6] https://www.reddit.com/r/linux/comments/4inrut/manjaros_ssl_certificate_expired_again/

[7] https://web.archive.org/web/20150409112614/https://manjaro.github.io/

[8] https://web.archive.org/web/20160512210401/https://manjaro.github.io/
