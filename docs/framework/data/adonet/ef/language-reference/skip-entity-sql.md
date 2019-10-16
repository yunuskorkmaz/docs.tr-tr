---
title: Atla (Entity SQL)
ms.date: 03/30/2017
ms.assetid: e2139412-8ea4-451b-8f10-91af18dfa3ec
ms.openlocfilehash: 75140384823588b8f6785de00b0ab3cd17314a3f
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319335"
---
# <a name="skip-entity-sql"></a>Atla (Entity SQL)

ORDER BY yan tümcesindeki SKIP alt yan tümcesini kullanarak fiziksel sayfalama işlemi gerçekleştirebilirsiniz. SKIP, ORDER BY yan tümcesinde ayrı olarak kullanılamaz.

## <a name="syntax"></a>Sözdizimi

```sql
[ SKIP n ]
```

## <a name="arguments"></a>Arguments

`n` \
Atlanacak öğe sayısı.

## <a name="remarks"></a>Açıklamalar

ORDER BY yan tümcesinde bir SKIP ifadesi Sub yan tümcesi varsa, sonuçlar sıralama belirtimine göre sıralanır ve sonuç kümesi, atlama ifadesinden hemen sonra gelen sonraki satırdan başlayan satırları içerir. Örneğin, 5 ' i atlamak ilk beş satırı atlar ve altıncı satırdan ileriye geri dönecektir.

> [!NOTE]
> Aynı sorgu ifadesinde hem TOP Modifier hem de SKIP alt yan tümcesi mevcutsa [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgusu geçersizdir. ÜST ifade sınır ifadesine değiştirilerek sorgunun yeniden yazılması gerekir.

> [!NOTE]
> SQL Server 2000 ' de, anahtar olmayan sütunlarda SıRALAMA ile atla kullanılması yanlış sonuçlar döndürebilir. Anahtar olmayan sütunda Yinelenen veriler varsa, belirtilen sayıda satırdan daha fazla satır atlanmayabilir. Bunun nedeni, atlama 'nin SQL Server 2000 ' de çevrilmesine neden olur. Örneğin, aşağıdaki kodda `E.NonKeyColumn` yinelenen değerler varsa beş satırdan daha fazla satır atlanabilir:
>
> ```sql
> SELECT [E] FROM Container.EntitySet AS [E] ORDER BY [E].[NonKeyColumn] DESC SKIP 5L
> ```

[Sorgu sonuçları aracılığıyla](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100)) [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgusu, Select ifadesinde döndürülen nesnelerde kullanılan sıralama düzenini BELIRTMEK için SKIP Ile order by işlecini kullanır.

## <a name="see-also"></a>Ayrıca bkz.

- [ORDER BY](order-by-entity-sql.md)
- [Nasıl yapılır: sorgu sonuçları aracılığıyla sayfa oluşturma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))
- [Disk Belleği](paging-entity-sql.md)
- [TOP](top-entity-sql.md)
