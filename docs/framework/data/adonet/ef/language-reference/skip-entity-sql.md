---
title: Atla (varlık SQL)
ms.date: 03/30/2017
ms.assetid: e2139412-8ea4-451b-8f10-91af18dfa3ec
ms.openlocfilehash: 88d4c9c987f451e9a653d5b9c213e7158670ed4b
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67662133"
---
# <a name="skip-entity-sql"></a>Atla (varlık SQL)
Fiziksel disk belleği SKIP alt yan tümcesi ORDER BY yan tümcesinde kullanarak gerçekleştirebilirsiniz. SKIP ayrı olarak from ORDER BY yan tümcesi kullanılamaz.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
[ SKIP n ]  
```  
  
## <a name="arguments"></a>Arguments  
 `n`  
 Atlanacak öğe sayısı.  
  
## <a name="remarks"></a>Açıklamalar  
 ORDER BY yan tümcesinde bir SKIP ifadesi alt yan tümcesi varsa, sonuçları sıralama belirtimine göre sıralanır ve sonraki satırdaki Atla ifadesinden hemen sonra başlayan satırları sonuç kümesini içerir. Örneğin, Atla 5 ilk beş satırları atlar ve Altıncı satırdan ileriye doğru döndürür.  
  
> [!NOTE]
>  Bir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu üst değiştiricisi hem SKIP alt yan tümcesi, aynı sorgu ifadesinde mevcut olması durumunda geçerli değil. Sorgu TOP ifadesi sınırı ifade değiştirerek yazılması.  
  
> [!NOTE]
>  SQL Server 2000'de, anahtar olmayan sütun ORDER BY ile Atla kullanarak hatalı sonuçlar döndürebilir. Anahtar olmayan sütun yinelenen veri varsa birden çok belirtilen sayıda satırı atlanabilir. SQL Server 2000 için Atla nasıl çevrilir nedeniyle budur. Örneğin, aşağıdaki kodda beşten fazla satır varsa atlanabilir `E.NonKeyColumn` yinelenen değerlere sahip:  
>   
>  `SELECT [E] FROM Container.EntitySet AS [E] ORDER BY [E].[NonKeyColumn] DESC SKIP 5L`  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] İçinde sorgu [nasıl yapılır: Sorgu sonuçları sayfası aracılığıyla](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100)) ORDER BY işleci bir SELECT deyiminde döndürülen nesneler üzerinde kullanılan sıralama düzeni belirlemek için ATLAMALI olarak kullanır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)
- [Nasıl yapılır: Sorgu sonuçları sayfasından](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))
- [Disk Belleği](../../../../../../docs/framework/data/adonet/ef/language-reference/paging-entity-sql.md)
- [TOP](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
