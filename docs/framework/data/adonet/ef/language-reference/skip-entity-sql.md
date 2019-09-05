---
title: Atla (Entity SQL)
ms.date: 03/30/2017
ms.assetid: e2139412-8ea4-451b-8f10-91af18dfa3ec
ms.openlocfilehash: 19d3001fb8f226b02f16167dfb51ce1caa80ba3b
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249229"
---
# <a name="skip-entity-sql"></a>Atla (Entity SQL)

ORDER BY yan tümcesindeki SKIP alt yan tümcesini kullanarak fiziksel sayfalama işlemi gerçekleştirebilirsiniz. SKIP, ORDER BY yan tümcesinde ayrı olarak kullanılamaz.

## <a name="syntax"></a>Sözdizimi

```
[ SKIP n ]
```

## <a name="arguments"></a>Arguments

`n` \
Atlanacak öğe sayısı.

## <a name="remarks"></a>Açıklamalar

ORDER BY yan tümcesinde bir SKIP ifadesi Sub yan tümcesi varsa, sonuçlar sıralama belirtimine göre sıralanır ve sonuç kümesi, atlama ifadesinden hemen sonra gelen sonraki satırdan başlayan satırları içerir. Örneğin, 5 ' i atlamak ilk beş satırı atlar ve altıncı satırdan ileriye geri dönecektir.

> [!NOTE]
> Aynı sorgu ifadesinde hem top Modifier hem de SKIP alt yan tümcesi mevcutsa sorgugeçersizdir.[!INCLUDE[esql](../../../../../../includes/esql-md.md)] ÜST ifade sınır ifadesine değiştirilerek sorgunun yeniden yazılması gerekir.

> [!NOTE]
> SQL Server 2000 ' de, anahtar olmayan sütunlarda SıRALAMA ile atla kullanılması yanlış sonuçlar döndürebilir. Anahtar olmayan sütunda Yinelenen veriler varsa, belirtilen sayıda satırdan daha fazla satır atlanmayabilir. Bunun nedeni, atlama 'nin SQL Server 2000 ' de çevrilmesine neden olur. Örneğin, aşağıdaki kodda yinelenen değerler varsa `E.NonKeyColumn` beş satırdan daha fazla satır atlanabilir:
>
> `SELECT [E] FROM Container.EntitySet AS [E] ORDER BY [E].[NonKeyColumn] DESC SKIP 5L`

[!INCLUDE[esql](../../../../../../includes/esql-md.md)] Sorgu[nasıl yapılır: Sorgu sonuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100)) aracılığıyla sayfa, Select ifadesinde döndürülen nesnelerde kullanılan sıralama düzenini belirtmek için SKIP ile order by işlecini kullanır.

## <a name="see-also"></a>Ayrıca bkz.

- [ORDER BY](order-by-entity-sql.md)
- [Nasıl yapılır: Sorgu sonuçları aracılığıyla sayfa](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))
- [Disk Belleği](paging-entity-sql.md)
- [TOP](top-entity-sql.md)
