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
