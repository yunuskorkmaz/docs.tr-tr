---
title: Toplu İşleme
ms.date: 12/13/2019
description: Tek bir komutta SQL deyimlerinin bir toplu işini yürütmeyi öğrenin.
ms.openlocfilehash: 0799784471520bb279db6a4b5879ad30945bdebb
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447057"
---
# <a name="batching"></a>Toplu İşleme

SQLite, toplu işlem SQL deyimlerini tek bir komutta birlikte yerel olarak desteklemez. Ancak ilgili bir ağ olmadığından, yine de performansa gerçekten yardımcı olmaz. Ancak Microsoft. Data. SQLite, diğer ADO.NET sağlayıcıları gibi davranması için bir kolaylık olarak deyimin toplu işleme uygulamasını uygular.

Çağrılırken <xref:System.Data.Common.DbCommand.ExecuteReader%2A?displayProperty=nameWithType>, deyimler, sonuçları döndüren ilk birine yürütülür. Çağırmak <xref:System.Data.Common.DbDataReader.NextResult%2A?displayProperty=nameWithType> , sonuçları döndürene veya toplu işin sonuna gelene kadar deyimleri yürütmeye devam eder. Tarafından <xref:System.Data.Common.DbDataReader.Dispose%2A?displayProperty=nameWithType> `NextResult()`kullanılmayan <xref:System.Data.Common.DbDataReader.Close%2A> kalan deyimleri çağırma veya yürütme. Bir veri okuyucusunu atlamazsanız, Sonlandırıcı kalan deyimleri yürütmeye çalışır, ancak karşılaştığı hatalar yok sayılır. Bu nedenle, toplu işlemler kullanılırken `DbDataReader` nesneleri atmak önemlidir.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/BatchingSample/Program.cs?name=snippet_Batching)]

## <a name="see-also"></a>Ayrıca bkz.

* [Toplu ekleme](bulk-insert.md)
