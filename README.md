# oracle-try

## CREATE テーブル - Sample
```
CREATE TABLE KOKYAKU (
    "KOKYAKU_ID"   VARCHAR2(10) NOT NULL,
    "NAME" VARCHAR2(60),
    "JUSHO" VARCHAR2(100),
    CONSTRAINT "KOKYAKU_PK" PRIMARY KEY ( "KOKYAKU_ID" )
);

CREATE TABLE CARD (
    "CARD_NUM" CHAR(16) NOT NULL,
    "KOKYAKU_ID"   VARCHAR2(10) NOT NULL,
    "STATUS" CHAR(1) NOT NULL,
    CONSTRAINT "CARD_PK" PRIMARY KEY ( "CARD_NUM" )
);

CREATE TABLE KOKYAKU_EXPORT_OK (
    "KOKYAKU_ID"   VARCHAR2(10) NOT NULL,
    "NAME" VARCHAR2(60),
    "JUSHO" VARCHAR2(100),
    CONSTRAINT "KOKYAKU_EXPORT_OK_PK" PRIMARY KEY ( "KOKYAKU_ID" )
);

CREATE TABLE KOKYAKU_EXPORT_NG (
    "KOKYAKU_ID"   VARCHAR2(10) NOT NULL,
    "NAME" VARCHAR2(60),
    "JUSHO" VARCHAR2(100),
    CONSTRAINT "KOKYAKU_EXPORT_NG_PK" PRIMARY KEY ( "KOKYAKU_ID" )
);
```

## テーブル作成（外部キーを使う）
* 参照元になる親テーブルを先に作ってから、テーブルを作成する
```
create table address (addressID number(20), 
                      prefecture　varchar2(50) NOT NULL,
                      city varchar2(50) NOT NULL,
                      street varchar2(50) NOT NULL,
                      building varchar2(100),
                      CONSTRAINT addressID PRIMARY KEY (addressID)
                    　);
```

* 参照する側のテーブル
```
create table membership (memberID number(5),
                         memberName varchar2(20) NOT NULL,
                         email varchar2(100) NOT NULL,
                         address number(20) NOT NULL,
                         expiration varchar2(10) NOT NULL
                            CHECK (expiration IN ('Y', 'N')),
                         CONSTRAINT memberID PRIMARY KEY (memberID),
                         CONSTRAINT address FOREIGN KEY (address) REFERENCES address (addressID)
                        );
```
## INSERT文
* 参照元から順に 
```
insert into address values(1000, '東京', 'A区', 'abc', '猫ビル');
insert into address values(1001, '東京', 'A区', 'cde', '犬ビル');
insert into address values(1002, '東京', 'A区', 'fgh', '馬マンション');
insert into address values(1010, '東京', 'B区', 'xyz', '赤ビル');
insert into address values(1011, '東京', 'B区', 'vwx', '青ビル');
insert into address values(1020, '東京', 'C区', 'ac', '野球ビル');

insert into membership values(10001, '田中太郎', 'abc123@email.com', 1002, 'Y');
insert into membership values(10002, '坂本武', 'a33123@email.com', 1020, 'Y');
insert into membership values(10003, '吉原次郎', 'bc2123@email.com', 1011, 'Y');
insert into membership values(10004, '所沢健太', 'a11123@email.com', 1020, 'Y');
insert into membership values(10005, '雨宮涼子', 'b33123@email.com', 1010, 'Y');
insert into membership values(10006, '倉田真由美', 'c43123@email.com', 1002, 'Y');
insert into membership values(10007, '久保田壮', 'add123@email.com', 1002, 'Y');
insert into membership values(10008, '小池千佳', 'abd123@email.com', 1001, 'Y');
insert into membership values(10009, 'Michael Jackson', 'fbc123@email.com', 1020, 'Y');
insert into membership values(10010, '浜田洋平', 'abc124@email.com', 1011, 'Y');
insert into membership values(10011, '山田三郎', 'abr211@email.com', 1002, 'Y');
insert into membership values(10012, '近石康', 'abf323@email.com', 1001, 'Y');
```
