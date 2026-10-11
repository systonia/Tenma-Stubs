# Tenma Stubs

Stubs of [Tenma](https://github.com/systonia/Tenma)'s PHP API for IDEs and PHPStan.

Tenma embeds its PHP API (`Tenma::serve()`, `Tenma::async()`, `Tenma\Http\Request`, `Tenma\Fs`, ...) in its binary, so IDEs and static analysis don't know it on their own. This package describes it: signatures and doc comments, empty bodies.

```bash
composer require --dev tenma/stubs
```

- **PhpStorm, Intelephense:** pick up `tenma.php` from `vendor/`, nothing else to do.
- **PHPStan:** with [`phpstan/extension-installer`](https://github.com/phpstan/extension-installer) the package's `extension.neon` is included automatically. Without it:

  ```neon
  includes:
      - vendor/tenma/stubs/extension.neon
  ```

The stubs are never autoloaded, so nothing changes at runtime: under Tenma the real classes are there, under FPM there is no `Tenma` class. Code that runs under both checks with `class_exists(Tenma::class)`.

## Updating

`tenma.php` is generated, don't edit it. With a Tenma binary of the version you want:

```bash
tenma --stubs > tenma.php
```

## License

MIT, see [LICENSE](LICENSE).
