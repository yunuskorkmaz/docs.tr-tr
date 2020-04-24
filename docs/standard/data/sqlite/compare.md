---
title: System. Data. SQLite ile karşılaştırma
ms.date: 12/13/2019
description: Microsoft. Data. SQLite ve System. Data. SQLite kitaplıkları arasındaki bazı farklılıkları açıklar.
ms.openlocfilehash: 076bbc6f746cf9296c96ec73047397a21a3b2558
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75900707"
---
# <a name="comparison-to-systemdatasqlite"></a>System. Data. SQLite ile karşılaştırma

2005 ' de, Robert Simpson tarafından oluşturulan System. Data. SQLite, ADO.NET 2,0 için bir SQLite sağlayıcıdır. 2010 ' de, SQLite ekibi, projenin bakımını ve geliştirilmesini gerçekleştirmektedir. Ayrıca, mono ekibinin kodu mono. Data. SQLite olarak 2007 ' de ele aldığı de dikkat edin. System. Data. SQLite, uzun bir geçmişe sahiptir ve Visual Studio Araçları ile eksiksiz ve tam özellikli bir ADO.NET sağlayıcısına sahiptir. Yeni sürümler .NET Framework her sürümü ile uyumlu derlemeleri .NET Compact Framework 2,0 sürümüne ve hatta 3,5 ' ye göndermeye devam eder.

.NET Core 'un ilk sürümü (2016 ' de yayımlanmıştır), .NET ' in tek, hafif, modern ve platformlar arası bir uygulamasıdır. Eski API 'Ler ve daha modern alternatifler olan API 'Ler kasıtlı olarak kaldırılmıştır. ADO.NET, DataSet API 'lerden herhangi birini (DataTable ve DataAdapter dahil) içermiyor.

Entity Framework ekibi, System. Data. SQLite codebase 'i biraz tanımıştı. EF ekibinin bir üyesi olan Brice Lambson, SQLite ekibinin 5 ve 6 Entity Framework sürümleri için destek eklemesini daha önce yardımcı olmuştur. Brice Ayrıca, .NET Core 'un planlanmasıyla aynı anda bir SQLite ADO.NET sağlayıcısı 'nın kendi uygulamasını kullanmaya da deneme oldu. Uzun bir tartışmadan sonra Entity Framework ekibi, Brice 'ın prototip temelinde Microsoft. Data. SQLite oluşturmaya karar verdi. Bu, .NET Core 'un hedeflerine uyum sağlayacak yeni bir hafif ve modern uygulama oluşturmalarına olanak tanır.

Daha modern bir örnek olarak, System. Data. SQLite ve Microsoft. Data. SQLite içinde [Kullanıcı tanımlı bir işlev](user-defined-functions.md) oluşturma kodu aşağıda verilmiştir.

```csharp
// System.Data.SQLite
connection.BindFunction(
    new SQLiteFunctionAttribute("ceiling", 1, FunctionType.Scalar),
    (Func<object[], object>)((object[] args) => Math.Ceiling((double)((object[])args[1])[0])),
    null);

// Microsoft.Data.Sqlite
connection.CreateFunction(
    "ceiling",
    (double arg) => Math.Ceiling(arg));
```

2017 ' de, .NET Core 2,0 bir stratejide değişiklik yaşadı. .NET Framework uyumluluğun .NET Core 'un başarısı için hayati öneme sahip olduğuna karar verdi. Veri kümesi API 'Leri de dahil olmak üzere, kaldırılan çoğu API 'Ler geri eklendi. Bunun gibi birçok konuda olduğu gibi, System. Data. SQLite 'un de .NET Core 'a geçmesine izin vermez. Ancak Microsoft. Data. sqlite ' un basit ve modern olması için özgün hedefi, hala kalır. Microsoft. Data. SQLite tarafından uygulanmayan ADO.NET API 'Leri hakkında ayrıntılar için bkz. [ADO.net kısıtlamaları](adonet-limitations.md) .

Microsoft. Data. SQLite öğesine yeni özellikler eklendiğinde, System. Data. SQLite tasarımı hesaba alınır. Mümkün olduğunda, aralarında kolayca geçiş yapmak için iki arasındaki değişiklikleri en aza indirmek için deneyeceğiz.

## <a name="data-types"></a>Veri türleri

Microsoft. Data. SQLite ve System. Data. SQLite arasındaki en büyük fark, veri türlerinin işlenme biçimi. [Veri türlerinde](types.md)açıklandığı gibi, Microsoft. Data. SQLite, her türlü rastgele dizenin sütun türü olarak belirtilmesini sağlayan ve yalnızca dört temel türe sahip olan SQLite 'un temeldeki süslemesini gizlemeyi denemez: tamsayı, gerçek, metın ve BLOB.

System. Data. SQLite, doğrudan .NET türlerine eşlenen sütun türlerine ek semantik uygular. Bu, sağlayıcıya daha kesin bir biçimde tür kullanımını sağlar ancak bazı kaba kenarlara sahiptir. Örneğin, SELECT deyimlerinde ifadelerin sütun türlerini belirtmek için yeni bir SQL deyimi (türler) tanıtmaları gerekiyordu.

## <a name="connection-strings"></a>Bağlantı dizeleri

Microsoft. Data. SQLite daha az sayıda [bağlantı dizesi](connection-strings.md) anahtar kelimiştir. Aşağıdaki tabloda, yerine kullanılabilecek alternatifler gösterilmektedir.

| Sözcükle          | Yapıyı                                         |
| ---------------- | --------------------------------------------------- |
| Önbellek Boyutu       | Gönder`PRAGMA cache_size = <pages>`                  |
| Varsayılan Zaman Aşımı  | SqliteConnection üzerinde DefaultTimeout özelliğini kullanın |
| FailIfMissing    | `Mode=ReadWrite` kullan                                |
| FullUri          | Veri kaynağı anahtar sözcüğünü kullanma                         |
| Günlük modu     | Gönder`PRAGMA journal_mode = <mode>`                 |
| Eski biçim    | Gönder`PRAGMA legacy_file_format = 1`                |
| En fazla sayfa sayısı   | Gönder`PRAGMA max_page_count = <pages>`              |
| Sayfa Boyutu        | Gönder`PRAGMA page_size = <bytes>`                   |
| Salt Okunur        | `Mode=ReadOnly` kullan                                 |
| Zaman Uyumlu      | Gönder`PRAGMA synchronous = <mode>`                  |
| Kullanılmamışsa              | Veri kaynağı anahtar sözcüğünü kullanma                         |
| UseUTF16Encoding | Gönder`PRAGMA encoding = 'UTF-16'`                   |

## <a name="authorization"></a>Yetkilendirme

Microsoft. Data. SQLite, SQLite 'un yetkilendirme geri aramasını ortaya çıkaran bir API 'ye sahip değil. Bu özellik hakkında geri bildirim sağlamak için sorun [#13835](https://github.com/dotnet/efcore/issues/13835) kullanın.

## <a name="data-change-notifications"></a>Veri değişikliği bildirimleri

Microsoft. Data. SQLite, SQLite 'un veri değişikliği bildirimlerini açığa çıkaran bir API 'ye sahip değil. Bu özellik hakkında geri bildirim sağlamak için sorun [#13827](https://github.com/dotnet/efcore/issues/13827) kullanın.

## <a name="virtual-table-modules"></a>Sanal tablo modülleri

Microsoft. Data. SQLite, sanal tablo modülleri oluşturmak için API içermiyor. Bu özellik hakkında geri bildirim sağlamak için sorun [#13823](https://github.com/dotnet/efcore/issues/13823) kullanın.

## <a name="see-also"></a>Ayrıca bkz.

* [Veri türleri](types.md)
* [Bağlantı dizeleri](connection-strings.md)
* [Şifreleme](encryption.md)
* [ADO.NET sınırlamaları](adonet-limitations.md)
* [Kaber sınırlamaları](dapper-limitations.md)
