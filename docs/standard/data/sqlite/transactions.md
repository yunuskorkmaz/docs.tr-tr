---
title: İşlemler
ms.date: 09/08/2020
description: İşlemleri nasıl kullanacağınızı öğrenin.
ms.openlocfilehash: 50c4cd1023eac892cafc3ae4395e9168bd8e9f36
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90678868"
---
# <a name="transactions"></a>İşlemler

İşlemler, birden çok SQL deyimini veritabanına tek bir atomik birim olarak işlenen tek bir iş biriminde gruplandırmenizi sağlar. İşlemdeki herhangi bir deyim başarısız olursa, önceki deyimler tarafından yapılan değişiklikler geri alınabilir. İşlem başlatıldığında veritabanının ilk durumu korunur. Bir işlemin kullanılması, veritabanında aynı anda çok sayıda değişiklik yaparken SQLite 'un performansını da artırır.

## <a name="concurrency"></a>Eşzamanlılık

SQLite 'ta, tek seferde veritabanında bekleyen değişikliklere yalnızca bir işlem izin verilir. Bu nedenle, <xref:Microsoft.Data.Sqlite.SqliteConnection.BeginTransaction%2A> `Execute` <xref:Microsoft.Data.Sqlite.SqliteCommand> başka bir işlemin tamamlanamayacak kadar uzun sürme durumunda ve üzerinde yapılan çağrılar zaman aşımına uğrar.

Kilitleme, yeniden denemeler ve zaman aşımları hakkında daha fazla bilgi için bkz. [veritabanı hataları](database-errors.md).

## <a name="isolation-levels"></a>Yalıtım düzeyleri

İşlem, SQLite içinde varsayılan olarak **seri hale getirilebilir** . Bu yalıtım düzeyi, bir işlem içinde yapılan tüm değişikliklerin tamamen yalıtılmış olmasını güvence altına alır. İşlemin dışında yürütülen diğer deyimler işlemin değişikliklerinden etkilenmez.

SQLite, paylaşılan bir önbellek kullanılırken **read UNCOMMITTED** öğesini de destekler. Bu düzey, kirli okuma, tekrarlanabilir okuma ve hayalet düzeylerine izin verir:

- Bir işlemde bekleyen değişiklikler işlem dışında bir sorgu tarafından döndürüldüğünde *kirli okuma* oluşur, ancak işlemdeki değişiklikler geri alınır. Sonuçlar veritabanına hiçbir daha önce teslim edilmemiş verileri içerir.

- Bir işlem aynı satırı iki kez sorguladığında, *tekrarlanabilir bir okuma* gerçekleşir, ancak başka bir işlem tarafından iki sorgu arasında değiştirildiğinden sonuçlar farklıdır.

- *Hayali* nesnelerin, bir işlem sırasında bir sorgunun where yan tümcesini karşılamak için değiştirilen veya eklenen satırlardır. İzin veriliyorsa aynı sorgu aynı işlemde iki kez yürütüldüğünde aynı sorgu farklı satırlar döndürebilir.

Microsoft. Data. SQLite, geçirilen IsolationLevel 'ı <xref:Microsoft.Data.Sqlite.SqliteConnection.BeginTransaction%2A> En düşük düzey olarak değerlendirir. Gerçek yalıtım düzeyi READ UNCOMMITTED veya Serializable olarak yükseltilir.

Aşağıdaki kod, bir kirli okumayı benzetir. Bağlantı dizesinin içermesi gerektiğini göz önünde bulundurun `Cache=Shared` .

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DirtyReadSample/Program.cs?name=snippet_DirtyRead)]

## <a name="deferred-transactions"></a>Ertelenmiş işlemler

Microsoft. Data. SQLite sürüm 5,0 ' den başlayarak, işlemler ertelenebilir. Bu, ilk komut yürütülene kadar veritabanındaki gerçek işlemin oluşturulmasını erteler. Ayrıca, bu işlem, bir okuma işleminden, komutlarının gerektiğinde bir yazma işlemine aşamalı olarak yükseltilmesine neden olur. Bu işlem sırasında veritabanına eş zamanlı erişimi etkinleştirmek için yararlı olabilir.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DeferredTransactionSample/Program.cs?name=snippet_DeferredTransaction)]

> [!WARNING]
> Ertelenmiş bir işlem içindeki komutlar, veritabanı kilitliyken işlemin bir okuma işleminden bir yazma işlemine yükseltilmesine neden olursa başarısız olabilir. Bu durumda, uygulamanın tüm işlemi yeniden denemesi gerekir.
