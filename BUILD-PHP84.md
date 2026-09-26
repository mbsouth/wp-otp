# WP-OTP PHP 8.4 dependency refresh

This build updates WP-OTP for PHP 8.4 and modern OTPHP/php-qrcode APIs.

## Build the vendor directory

Requirements:

- PHP 8.4+
- Composer 2.x

From this directory run:

```bash
composer update --no-dev --prefer-dist --optimize-autoloader
```

Then verify:

```bash
composer check-platform-reqs
php -l admin/class-wp-otp-admin.php
php -l public/class-wp-otp-public.php
php -l wp-otp.php
```

The plugin intentionally uses OTPHP's immutable `withLabel()` / `withIssuer()` API and supplies an `InternalClock` so it does not depend on OTPHP's deprecated implicit clock fallback.

The QR code is generated locally with chillerlan/php-qrcode; no OTP provisioning URI needs to be sent to a third-party QR service in the default configuration.
