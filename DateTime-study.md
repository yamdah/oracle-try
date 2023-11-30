# DateTime-study

## 学習環境
* SQLDeveloperを使用

## テーブル準備
```
DROP TABLE t_date1;                                            <!-- テーブルのリセット -->

CREATE TABLE t_date1 (date_id   NUMBER PRIMARY KEY,
                      date_str  VARCHAR2(100));

INSERT INTO t_date1 VALUES (1, '2023/12/15 12:43:00');
INSERT INTO t_date1 VALUES (2, '2023/12/17 09:38:50');
INSERT INTO t_date1 VALUES (3, '2023/12/20 20:26:41');
INSERT INTO t_date1 VALUES (4, '2023/12/24 21:40:16');
INSERT INTO t_date1 VALUES (5, '2023/12/29 10:30:19');
```

## 年月日時について
* TO_DATEコマンド
* 文字リテラルからの変換
```
SELECT TO_DATE(date_str, 'YYYY/MM/DD HH24:MI:SS') FROM t_date1;
```

