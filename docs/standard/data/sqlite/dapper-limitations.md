---
title: Kaber sınırlamaları
ms.date: 12/13/2019
description: Kaber kullanırken karşılaştığınız kısıtlamaların bazılarını açıklar.
ms.openlocfilehash: 396507f25f591a9ab5c3bb07c0af6fd8d175e4ea
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901205"
---
# <a name="dapper-limitations"></a>Kaber sınırlamaları

Microsoft. Data. SQLite ile [kaber](https://stackexchange.github.io/Dapper/)kullanılırken dikkat etmeniz gereken bazı sınırlamalar vardır.

## <a name="parameters"></a>Parametreler

SQLite parametre adları büyük/küçük harfe duyarlıdır. SQL 'de kullanılan parametre adlarının anonim nesne özellikleri ile eşleştiğinden emin olun. Sorun [#18861](https://github.com/dotnet/efcore/issues/18861) bu deneyimi iyileştirir.

Paber aynı zamanda, `@` ön eki kullanmak için parametreler bekliyor. Diğer ön ekler çalışmaz.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DapperSample/Program.cs?name=snippet_Parameter)]

## <a name="data-types"></a>Veri türleri

Kaber, SqliteDataReader Dizin oluşturucuyu kullanarak değerleri okur. Bu dizin oluşturucunun dönüş türü Object, yani yalnızca Long, Double, String veya Byte [] değerlerini döndürdüğüne gelir. Daha fazla bilgi için bkz. [veri türleri](types.md). Kaber, bu ve diğer temel türler arasındaki dönüştürmelerin çoğunu işler. Ne yazık ki,, `DateTimeOffset`veya `Guid` `TimeSpan`işlemez. Sonuçlarınızda bu türleri kullanmak istiyorsanız tür işleyicileri oluşturun.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DapperSample/Program.cs?name=snippet_TypeHandlers)]

Sorgulama yapmadan önce tür işleyicilerini eklemeyi unutmayın.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DapperSample/Program.cs?name=snippet_AddTypeHandlers)]

## <a name="see-also"></a>Ayrıca bkz.

* [Veri türleri](types.md)
* [Zaman uyumsuz sınırlamalar](async.md)
