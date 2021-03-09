# MinIO Docker Compose

![stack](./docs/stack.svg)

Deploy MinIO on Docker Compose.

Distributed instances are now accessible on the host at ports 9000, proceed to access the Web browser at <http://127.0.0.1:9000/>. Here 4 MinIO server instances are reverse proxied through Nginx load balancing.

## MinIO Console

A graphical user interface for MinIO <https://github.com/minio/console>


## Install MinIO Client

```bash
brew install minio/stable/mc
mc --autocompletion # Shell autocompletion
```

## Install MinIO Stack

- Nginx
- console UI
- minio1
- minio2
- minio3
- minio4

```bash
docker-compose pull
docker-compose up
```

## Generate Configuration

```bash
mc ls
# mc: Configuration written to `/Users/mhmd/.mc/config.json`. Please update your access credentials.
# mc: Successfully created `/Users/mhmd/.mc/share`.
# mc: Initialized share uploads `/Users/mhmd/.mc/share/uploads.json` file.
# mc: Initialized share downloads `/Users/mhmd/.mc/share/downloads.json` file.
```

## Update Configuration

Add access key and secret key, update alias to match use case.

```bash
code /Users/mhmd/.mc/config.json
```

```json
{
	"version": "10",
	"aliases": {
		"gcs": {
			"url": "https://storage.googleapis.com",
			"accessKey": "YOUR-ACCESS-KEY-HERE",
			"secretKey": "YOUR-SECRET-KEY-HERE",
			"api": "S3v2",
			"path": "dns"
		},
		"mac": {
			"url": "http://localhost:9000",
			"accessKey": "minio",
			"secretKey": "minio123",
			"api": "S3v4",
			"path": "auto"
		},
		"play": {
			"url": "https://play.min.io",
			"accessKey": "YOUR-ACCESS-KEY-HERE",
			"secretKey": "YOUR-SECRET-KEY-HERE",
			"api": "S3v4",
			"path": "auto"
		},
		"s3": {
			"url": "https://s3.amazonaws.com",
			"accessKey": "YOUR-ACCESS-KEY-HERE",
			"secretKey": "YOUR-SECRET-KEY-HERE",
			"api": "S3v4",
			"path": "dns"
		}
	}
}
```

## List MinIO Buckets

```bash
mc ls mac
```

## Create MinIO Buckets

```bash
mc mb mac/test-mc-client
# Bucket created successfully `mac/test-mc-client`.
```

## Access UIs

- console UI: <http://localhost:9090>
- MinIO UI: <http://localhost:9000>