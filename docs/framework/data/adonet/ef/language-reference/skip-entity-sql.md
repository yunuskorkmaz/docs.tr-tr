---
title: Atla (varlık SQL)
ms.date: 03/30/2017
ms.assetid: e2139412-8ea4-451b-8f10-91af18dfa3ec
ms.openlocfilehash: e8ef529ea8d2be2ef8eb3a2eb606e7ca8bf13f0a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61797752"
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
>  İçinde [!INCLUDE[ssVersion2000](../../../../../../includes/ssversion2000-md.md)], anahtar olmayan sütun ORDER BY ile Atla kullanarak hatalı sonuçlar döndürebilir. Anahtar olmayan sütun yinelenen veri varsa birden çok belirtilen sayıda satırı atlanabilir. Bu nasıl Atla için çevrilir nedeniyle, [!INCLUDE[ssVersion2000](../../../../../../includes/ssversion2000-md.md)]. Örneğin, aşağıdaki kodda beşten fazla satır varsa atlanabilir `E.NonKeyColumn` yinelenen değerlere sahip:  
>   
>  `SELECT [E] FROM Container.EntitySet AS [E] ORDER BY [E].[NonKeyColumn] DESC SKIP 5L`  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] İçinde sorgu [nasıl yapılır: Sorgu sonuçları sayfası aracılığıyla](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100)) ORDER BY işleci bir SELECT deyiminde döndürülen nesneler üzerinde kullanılan sıralama düzeni belirlemek için ATLAMALI olarak kullanır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)
- [Nasıl yapılır: Sorgu sonuçları sayfasından](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))
- [Disk Belleği](../../../../../../docs/framework/data/adonet/ef/language-reference/paging-entity-sql.md)
- [TOP](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
