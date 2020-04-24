---
title: Bağlantı dizeleri
ms.date: 12/13/2019
description: Desteklenen anahtar sözcükler ve bağlantı dizelerinin değerleri.
ms.openlocfilehash: bb54d152bac62a86c2a49192cf678a745159164e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400451"
---
# <a name="connection-strings"></a>Bağlantı dizeleri

Bir bağlantı dizesi, veritabanına nasıl bağlanılacağını belirtmek için kullanılır. Microsoft. Data. SQLite içindeki bağlantı dizeleri standart [ADO.net söz dizimini](../../../framework/data/adonet/connection-strings.md) , noktalı virgülle ayrılmış bir anahtar sözcük ve değer listesi olarak izler.

## <a name="keywords"></a>Anahtar sözcükler

Aşağıdaki bağlantı dizesi anahtar sözcükleri Microsoft. Data. SQLite ile kullanılabilir:

### <a name="data-source"></a>Veri kaynağı

Veritabanı dosyasının yolu. *Veri kaynağı* (boşluk olmadan) ve *dosya adı* bu anahtar sözcüğünün diğer adlarıdır.

SQLite, yolları geçerli çalışma dizinine göre değerlendirir. Mutlak yollar da belirtilebilir.

**Boşsa**, SQLite bağlantı kapalıyken silinen geçici bir disk üzerinde veritabanı oluşturur.

İse `:memory:`, bellek içi bir veritabanı kullanılır. Daha fazla bilgi için bkz. [bellek içi veritabanları](in-memory-databases.md).

`|DataDirectory|` Değiştirme dizesiyle başlayan yollar göreli yollarla aynı şekilde değerlendirilir. Ayarlanırsa, yollar DataDirectory uygulama etki alanı özellik değerine göre yapılır.

Bu anahtar sözcük ayrıca [URI dosya adlarını](https://www.sqlite.org/uri.html)destekler.

### <a name="mode"></a>Mod

Bağlantı modu.

| Değer           | Açıklama                                                                                        |
| --------------- | -------------------------------------------------------------------------------------------------- |
| ReadWriteCreate | Veritabanını okumak ve yazmak için açar ve yoksa oluşturur. Bu varsayılandır. |
| ReadWrite       | Veritabanını okumak ve yazmak için açar.                                                        |
| ReadOnly        | Veritabanını salt okuma modunda açar.                                                              |
| Bellek          | Bellek içi veritabanı açar.                                                                       |

### <a name="cache"></a>Önbellek

Bağlantı tarafından kullanılan önbelleğe alma modu.

| Değer   | Açıklama                                                                                    |
| ------- | ---------------------------------------------------------------------------------------------- |
| Varsayılan | Temel alınan SQLite kitaplığının varsayılan modunu kullanır. Bu varsayılandır.                   |
| Özel | Her bağlantı özel bir önbellek kullanır.                                                          |
| Paylaşımlı  | Bağlantılar bir önbelleği paylaşır. Bu mod işlem ve tablo kilitleme davranışını değiştirebilir. |

### <a name="password"></a>Parola

Şifreleme anahtarı. Belirtildiğinde, `PRAGMA key` bağlantı açıldıktan hemen sonra gönderilir.

> [!WARNING]
> Şifreleme yerel SQLite kitaplığı tarafından desteklenmiyorsa parolanın hiçbir etkisi yoktur.

### <a name="foreign-keys"></a>Yabancı anahtarlar

Yabancı anahtar kısıtlamalarının etkinleştirilip etkinleştirilmeyeceğini gösteren bir değer.

| Değer   | Açıklama
| ------- | --- |
| True    | Bağlantıyı `PRAGMA foreign_keys = 1` açtıktan hemen sonra gönderir.
| False   | Bağlantıyı `PRAGMA foreign_keys = 0` açtıktan hemen sonra gönderir.
| olmamalıdır | Göndermez `PRAGMA foreign_keys`. Bu varsayılandır. |

E_sqlite3 gibi, yerel SQLite kitaplığı derlemek için SQLITE_DEFAULT_FOREIGN_KEYS kullanıldığında yabancı anahtarların etkinleştirilmesi gerekmez.

### <a name="recursive-triggers"></a>Özyinelemeli Tetikleyiciler

Özyinelemeli tetikleyicilerin etkinleştirilip etkinleştirilmeyeceğini gösteren bir değer.

| Değer | Açıklama                                                                 |
| ----- | --------------------------------------------------------------------------- |
| True  | Bağlantıyı `PRAGMA recursive_triggers` açtıktan hemen sonra gönderir. |
| False | Göndermez `PRAGMA recursive_triggers`. Bu varsayılandır.              |

## <a name="connection-string-builder"></a>Bağlantı dizesi Oluşturucu

Bağlantı dizelerini oluşturmak <xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder> için türü kesin belirlenmiş bir yöntem olarak kullanabilirsiniz. Bağlantı dizesi ekleme saldırılarını engellemek için de kullanılabilir.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/EncryptionSample/Program.cs?name=snippet_ConnectionStringBuilder)]

## <a name="examples"></a>Örnekler

### <a name="basic"></a>Temel

İyileştirilmiş eşzamanlılık için paylaşılan önbelleği olan temel bir bağlantı dizesi.

```ConnectionString
Data Source=Application.db;Cache=Shared
```

### <a name="encrypted"></a>Şifreli

Şifrelenmiş bir veritabanı.

```ConnectionString
Data Source=Encrypted.db;Password=MyEncryptionKey
```

### <a name="read-only"></a>Salt okunur

Uygulama tarafından değiştirilemeyen salt biçimli bir veritabanı.

```ConnectionString
Data Source=Reference.db;Mode=ReadOnly
```

### <a name="in-memory"></a>Bellek içi

Özel, bellek içi veritabanı.

```ConnectionString
Data Source=:memory:
```

### <a name="sharable-in-memory"></a>Paylaşılabilir bellek içi

*Paylaşılabilir*adıyla tanımlanan paylaşılabilir, bellek içi veritabanı.

```ConnectionString
Data Source=Sharable;Mode=Memory;Cache=Shared
```

## <a name="see-also"></a>Ayrıca bkz.

* [ADO.NET içinde bağlantı dizeleri](../../../framework/data/adonet/connection-strings.md)
* [Bellek içi veritabanları](in-memory-databases.md)
* [İşlemler](transactions.md)
