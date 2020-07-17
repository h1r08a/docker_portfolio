# Docker環境

## Django, Postgres
### [起動] 
- webディレクトリの中に開発環境用の.envファイルを配置
- dbディレクトリのなかに.env.dbファイルを配置
```
docker-compose up -d
``` 
#### DBを先に起動しないとエラーが起こることがある
```
docker-compose up db -d
```
#### Pythonの中に入る
```
docker-compose exec web ash

```
#### データベースの中に入る
```
docker-compose exec db psql -U <username> -d <database>

```

### [停止]
```
docker-compose down
```

## Django, Postgres, Nginx, Gunicorn
### [起動]
```
docker-compose -f docker-compose.prod.yml up -d
```

### [停止]
```
docker-compose -f docker-compose.prod.yml down
```