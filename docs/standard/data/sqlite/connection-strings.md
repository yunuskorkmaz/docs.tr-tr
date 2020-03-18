---
title: Bağlantı dizeleri
ms.date: 12/13/2019
description: Desteklenen anahtar kelimeler ve bağlantı dizeleri değerleri.
ms.openlocfilehash: bb54d152bac62a86c2a49192cf678a745159164e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400451"
---
# <a name="connection-strings"></a>Bağlantı dizeleri

Veritabanına nasıl bağlanılmayı belirtmek için bir bağlantı dizesi kullanılır. Microsoft.Data.Sqlite'deki bağlantı dizeleri, standart [ADO.NET sözdizimini](../../../framework/data/adonet/connection-strings.md) yarı sütunlu ayrılmış anahtar kelimeler ve değerler listesi olarak izler.

## <a name="keywords"></a>Anahtar sözcükler

Aşağıdaki bağlantı dize anahtar kelimeleri Microsoft.Data.Sqlite ile kullanılabilir:

### <a name="data-source"></a>Veri kaynağı

Veritabanı dosyasına giden yol. *DataSource* (boşluk olmadan) ve *Dosya Adı* bu anahtar kelimenin diğer adlarıdır.

SQLite, yollara geçerli çalışma dizinine göre davranır. Mutlak yollar da belirtilebilir.

**Boşsa,** SQLite bağlantı kapatıldığında silinen geçici bir disk veritabanı oluşturur.

, `:memory:`bellek içi veritabanı kullanılırsa. Daha fazla bilgi için Bellek [İçi veritabanlarına](in-memory-databases.md)bakın.

Değiştirme dizesiyle `|DataDirectory|` başlayan yollar, göreli yollarla aynı şekilde işlenir. Ayarlanırsa, yollar DataDirectory uygulama etki alanı özelliği değerine göre yapılır.

Bu anahtar kelime aynı zamanda [URI Dosya adlarını](https://www.sqlite.org/uri.html)da destekler.

### <a name="mode"></a>Mod

Bağlantı modu.

| Değer           | Açıklama                                                                                        |
| --------------- | -------------------------------------------------------------------------------------------------- |
| ReadWriteCreate | Okuma ve yazma için veritabanını açar ve yoksa oluşturur. Bu varsayılandır. |
| ReadWrite       | Okuma ve yazma için veritabanını açar.                                                        |
| ReadOnly        | Veritabanını salt okunur modunda açar.                                                              |
| Bellek          | Bellek içi bir veritabanı açar.                                                                       |

### <a name="cache"></a>Önbellek

Bağlantı tarafından kullanılan önbelleğe alma modu.

| Değer   | Açıklama                                                                                    |
| ------- | ---------------------------------------------------------------------------------------------- |
| Varsayılan | Temel SQLite kitaplığın varsayılan modunu kullanır. Bu varsayılandır.                   |
| Özel | Her bağlantı özel bir önbellek kullanır.                                                          |
| Paylaşımlı  | Bağlantılar önbelleği paylaşır. Bu mod, işlem ve tablo kilitleme davranışını değiştirebilir. |

### <a name="password"></a>Parola

Şifreleme anahtarı. Belirtildiğinde, `PRAGMA key` bağlantıyı açtıktan hemen sonra gönderilir.

> [!WARNING]
> Şifreleme yerel SQLite kitaplığı tarafından desteklenmediği zaman parolanın hiçbir etkisi yoktur.

### <a name="foreign-keys"></a>Yabancı Anahtarlar

Yabancı anahtar kısıtlamalarının etkinleştirilip etkinleştirilemeyeceğini gösteren bir değer.

| Değer   | Açıklama
| ------- | --- |
| True    | Bağlantıyı `PRAGMA foreign_keys = 1` açtıktan hemen sonra gönderir.
| False   | Bağlantıyı `PRAGMA foreign_keys = 0` açtıktan hemen sonra gönderir.
| (boş) | `PRAGMA foreign_keys`Göndermiyor. Bu varsayılandır. |

yerel SQLite kitaplığını derlemek için SQLITE_DEFAULT_FOREIGN_KEYS e_sqlite3'da olduğu gibi yabancı anahtarları etkinleştirmeye gerek yoktur.

### <a name="recursive-triggers"></a>Özyinelemeli tetikleyiciler

Özyinelemeli tetikleyicileri etkinleştirip etkinleştirmeyeceğini gösteren bir değer.

| Değer | Açıklama                                                                 |
| ----- | --------------------------------------------------------------------------- |
| True  | Bağlantıyı `PRAGMA recursive_triggers` açtıktan hemen sonra gönderir. |
| False | `PRAGMA recursive_triggers`Göndermiyor. Bu varsayılandır.              |

## <a name="connection-string-builder"></a>Bağlantı dize oluşturucu

Bağlantı dizeleri oluşturmanın güçlü bir şekilde yazılmış bir yolu olarak kullanabilirsiniz. <xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder> Ayrıca bağlantı string enjeksiyon saldırılarını önlemek için kullanılabilir.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/EncryptionSample/Program.cs?name=snippet_ConnectionStringBuilder)]

## <a name="examples"></a>Örnekler

### <a name="basic"></a>Temel

Geliştirilmiş eşzamanlılık için paylaşılan önbelleği olan temel bağlantı dizesi.

```ConnectionString
Data Source=Application.db;Cache=Shared
```

### <a name="encrypted"></a>Şifreli

Şifreli bir veritabanı.

```ConnectionString
Data Source=Encrypted.db;Password=MyEncryptionKey
```

### <a name="read-only"></a>Salt okunur

Uygulama tarafından değiştirilemeyen salt okunur veritabanı.

```ConnectionString
Data Source=Reference.db;Mode=ReadOnly
```

### <a name="in-memory"></a>Bellek içi

Özel, hafıza içi bir veritabanı.

```ConnectionString
Data Source=:memory:
```

### <a name="sharable-in-memory"></a>Bellekte sharable

*Sharable*adıyla tanımlanan sharable, in-memory veritabanı.

```ConnectionString
Data Source=Sharable;Mode=Memory;Cache=Shared
```

## <a name="see-also"></a>Ayrıca bkz.

* [ADO.NET Bağlantı Dizeleri](../../../framework/data/adonet/connection-strings.md)
* [Bellek veritabanları](in-memory-databases.md)
* [İşlemler](transactions.md)
