---
title: İşlemler
ms.date: 12/13/2019
description: İşlemleri nasıl kullanacağınızı öğrenin.
ms.openlocfilehash: 4b72a1573a560ffd1bfd0f54d46ab3b135280976
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447141"
---
# <a name="transactions"></a>İşlemler

İşlemler, birden çok SQL deyimini veritabanına tek bir atomik birim olarak işlenen tek bir iş biriminde gruplandırmenizi sağlar. İşlemdeki herhangi bir deyim başarısız olursa, önceki deyimler tarafından yapılan değişiklikler geri alınabilir. İşlem başlatıldığında veritabanının ilk durumu korunur. Bir işlemin kullanılması, veritabanında aynı anda çok sayıda değişiklik yaparken SQLite 'un performansını da artırır.

## <a name="concurrency"></a>Eşzamanlılık

SQLite 'ta, tek seferde veritabanında bekleyen değişikliklere yalnızca bir işlem izin verilir. Bu nedenle, başka bir işlemin tamamlanabilmesi çok uzun sürerse <xref:Microsoft.Data.Sqlite.SqliteCommand> <xref:Microsoft.Data.Sqlite.SqliteConnection.BeginTransaction%2A> ve `Execute` yöntemlerine yapılan çağrılar zaman aşımına uğrar.

Kilitleme, yeniden denemeler ve zaman aşımları hakkında daha fazla bilgi için bkz. [veritabanı hataları](database-errors.md).

## <a name="isolation-levels"></a>Yalıtım düzeyleri

İşlem, SQLite içinde varsayılan olarak **seri hale getirilebilir** . Bu yalıtım düzeyi, bir işlem içinde yapılan tüm değişikliklerin tamamen yalıtılmış olmasını güvence altına alır. İşlemin dışında yürütülen diğer deyimler işlemin değişikliklerinden etkilenmez.

SQLite, paylaşılan bir önbellek kullanılırken **read UNCOMMITTED** öğesini de destekler. Bu düzey, kirli okuma, tekrarlanabilir okuma ve hayalet düzeylerine izin verir:

- Bir işlemde bekleyen değişiklikler işlem dışında bir sorgu tarafından döndürüldüğünde *kirli okuma* oluşur, ancak işlemdeki değişiklikler geri alınır. Sonuçlar veritabanına hiçbir daha önce teslim edilmemiş verileri içerir.

- Bir işlem aynı satırı iki kez sorguladığında, *tekrarlanabilir bir okuma* gerçekleşir, ancak başka bir işlem tarafından iki sorgu arasında değiştirildiğinden sonuçlar farklıdır.

- *Hayali* nesnelerin, bir işlem sırasında bir sorgunun where yan tümcesini karşılamak için değiştirilen veya eklenen satırlardır. İzin veriliyorsa aynı sorgu aynı işlemde iki kez yürütüldüğünde aynı sorgu farklı satırlar döndürebilir.

Microsoft. Data. SQLite, <xref:Microsoft.Data.Sqlite.SqliteConnection.BeginTransaction%2A> geçirilen IsolationLevel 'ı en düşük düzey olarak değerlendirir. Gerçek yalıtım düzeyi READ UNCOMMITTED veya Serializable olarak yükseltilir.

Aşağıdaki kod, bir kirli okumayı benzetir. Bağlantı dizesinin `Cache=Shared`içermesi gerektiğini göz önünde bulundurun.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DirtyReadSample/Program.cs?name=snippet_DirtyRead)]
