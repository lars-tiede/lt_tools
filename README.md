# My tools and configs

Automated installation of tools and dotfiles I use on some/all machines I have access to.

**This is work-in-progress and not ready for use yet.**

Basic ideas:
- use Ansible to distribute and install tools and dotfiles.
  - this gives me the ability to use tailored configuration templates and painlessly install missing tools, all idempotently.
  - it also makes it really easy to update config "everywhere".
- use git to make everything available everywhere, and to be able to edit everything everywhere.
  - code and templates are stored safely and versioned in a publicly hosted repository.
  - wherever Ansible distributes and installs stuff, the repository is available and ready for working on it.
- have a few helper scripts to make common tasks (such as "render me this dotfile template locally on this machine right now") simple and fast.


## Installation

*Recursively* clone this repository into `~/lt_tools` on your 'main machine' (or the one you'll use to distribute your configs from for the first time).

```sh
~$ git clone --recursive https://github.com/lars-tiede/lt_tools.git
```


## License

[MIT](LICENSE.txt)
