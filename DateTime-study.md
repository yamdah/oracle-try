# DateTime-study

## 学習環境
* SQLDeveloperを使用

## テーブル準備
```
CREATE TABLE t_date1 (id       NUMBER PRIMARY KEY,
                      date_str VARCHAR2(50));

INSERT INTO t_date1 VALUES (1, '2023/12/15 12:43:00');
```

## 年月日時について
* TO_DATEコマンド
* 文字リテラルからの変換
```
SELECT TO_DATE(date_str, 'YYYY/MM/DD HH24:MI:SS') FROM t_date1;
```

