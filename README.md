# docker-php-minimal
A collection of Dockerfiles for different versions of a very barebones PHP.

## Purpose
These docker images provide a minimalistic version of PHP for a large number
of PHP versions.  The built PHP is not your typical PHP as it is built as
follows:

* All optional extensions are not built or included.
* The following functions are disabled from running: `system`, `shell_exec`,
  `passthru`, `proc_open`, `popen`, and `ini_set`.
* Error display is turned off but errors are logged instead.
* A 1MB memory limit s enforced.
* URL and file opening disabled.

This provides a locked down PHP that should be unable to escape and do
anything nasty on the system, especially if combined with limits on CPU usage,
execution time, etc.  Most of these restrictions can be easily modified via
modifying the `php.ini`.

## Usage
Building a docker image with the PHP version you need is a two-step process.
In the first step, you build an archlinux package for PHP inside of a docker
image based on [nubs/arch-build].

```bash
docker run --interactive --tty --rm --volume "$(pwd)/php-5.6.0/php:/package" nubs/arch-build

# Using short-options:
# docker run -i -t --rm -v "$(pwd)/php-5.6.0/php:/package" nubs/arch-build
```

For the second step you build a docker image with the built PHP package
installed.  This image will be used to run your code.

```bash
docker build --tag php-5.6.0 php-5.6.0
docker run -i -t --rm php-5.6.0 php -i
```

### Using docker-compose
Alternatively, if you have docker-compose installed, you can run the above
steps like this instead:

```bash
docker-compose run php560build
docker-compose run php560 php -i
```

## License
docker-php-minimal is licensed under the MIT license.  See [LICENSE](LICENSE)
for the full license text.

[nubs/arch-build]: https://github.com/nubs/arch-build
