---
title: From Yan Tümcesi
ms.date: 07/20/2015
f1_keywords:
- vb.QueryFrom
- vb.QueryFromIn
- vb.QueryFromLet
helpviewer_keywords:
- queries [Visual Basic], From
- From clause [Visual Basic]
- From statement [Visual Basic]
ms.assetid: 83e3665e-68a0-4540-a3a3-3d777a0f95d5
ms.openlocfilehash: 33680f49247b3b2a6082b3a6b27ca64f8401e42d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396187"
---
# <a name="from-clause-visual-basic"></a>From Tümcesi (Visual Basic)
Bir veya daha fazla Aralık değişkenini ve sorgulanacak bir koleksiyonu belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
From element [ As type ] In collection [ _ ]  
  [, element2 [ As type2 ] In collection2 [, ... ] ]  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`element`|Gereklidir. Koleksiyonun öğeleri boyunca yinelemek için kullanılan bir *Aralık değişkeni* . Bir Aralık değişkeni, `collection` sorgu ile yineleme yaparken öğesinin her üyesine başvurmak için kullanılır `collection` . Sıralanabilir bir tür olmalıdır.|  
|`type`|İsteğe bağlı. Türü `element` . Hayır `type` belirtilmemişse, türü `element` öğesinden çıkarsanamıyor `collection` .|  
|`collection`|Gereklidir. Sorgulanacak koleksiyona başvurur. Sıralanabilir bir tür olmalıdır.|  
  
## <a name="remarks"></a>Açıklamalar  
 `From`Yan tümcesi, bir sorgunun kaynak verilerini ve kaynak koleksiyondaki bir öğeye başvurmak için kullanılan değişkenleri belirlemek için kullanılır. Bu değişkenlere *Aralık değişkenleri*denir. Yan tümcesi, `From` bir sorgu için, `Aggregate` yan tümcesinin yalnızca toplanmış sonuçları döndüren bir sorguyu belirlemek için kullanılması dışında, gereklidir. Daha fazla bilgi için bkz. [toplama yan tümcesi](aggregate-clause.md).  
  
 `From`Birleştirilecek birden çok koleksiyonu belirlemek için bir sorguda birden çok yan tümce belirtebilirsiniz. Birden çok koleksiyon belirtildiğinde, bunlar birbirinden bağımsız olarak yinelenir veya ilişkili olmaları durumunda bunlara katılabilirler. `Select`Yan tümcesini kullanarak veya açıkça `Join` veya yan tümceleri kullanarak koleksiyonları birleştirebilirsiniz `Group Join` . Alternatif olarak, tek bir yan tümce içinde birden fazla Aralık değişkeni ve koleksiyonlar belirterek `From` , her ilgili Aralık değişkeni ve koleksiyon diğerlerinden virgülle ayırarak belirtebilirsiniz. Aşağıdaki kod örneğinde yan tümce için her iki sözdizimi seçeneği gösterilmektedir `From` .  
  
 [!code-vb[VbSimpleQuerySamples#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#21)]  
  
 `From`Yan tümcesi, bir döngünün kapsamına benzer bir sorgunun kapsamını tanımlar `For` . Bu nedenle, `element` bir sorgunun kapsamındaki her Aralık değişkeninin benzersiz bir adı olmalıdır. `From`Bir sorgu için birden çok yan tümce belirtebileceğiniz için, sonraki `From` yan tümceler yan tümcesindeki Aralık değişkenlerine başvurabilir `From` veya bir önceki yan tümcedeki Aralık değişkenlerine başvurabilirler `From` . Örneğin, aşağıdaki örnek, `From` ikinci yan tümcesindeki koleksiyonun ilk yan tümcesindeki Range değişkeninin bir özelliğine dayandığı iç içe geçmiş bir yan tümce gösterir.  
  
 [!code-vb[VbSimpleQuerySamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#22)]  
  
 Her `From` yan tümce, sorguyu iyileştirmek için ek sorgu yan tümcelerinin herhangi bir birleşimi tarafından izlenebilir. Sorguyu aşağıdaki yollarla geliştirebilirsiniz:  
  
- `From`Ve `Select` yan tümcelerini kullanarak veya açıkça `Join` veya `Group Join` yan tümceleri kullanarak birden çok koleksiyonu örtülü olarak birleştirin.  
  
- `Where`Sorgu sonucunu filtrelemek için yan tümcesini kullanın.  
  
- Yan tümcesini kullanarak sonucu sıralayın `Order By` .  
  
- Yan tümcesini kullanarak benzer sonuçları birlikte gruplandırın `Group By` .  
  
- `Aggregate`Tüm sorgu sonucu için değerlendirmek üzere toplama işlevlerini belirlemek için yan tümcesini kullanın.  
  
- `Let`Değeri bir koleksiyon yerine bir ifade tarafından belirlenen bir yineleme değişkeni tanıtmak için yan tümcesini kullanın.  
  
- `Distinct`Yinelenen sorgu sonuçlarını yoksaymak için yan tümcesini kullanın.  
  
- ,, `Skip` `Take` `Skip While` , Ve `Take While` yan tümceleri kullanarak döndürülecek sonuç parçalarını belirler.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki sorgu ifadesi, `From` koleksiyondaki her bir nesne için bir Aralık değişkeni bildirmek üzere bir yan tümce kullanır `cust` `Customer` `customers` . `Where`Yan tümcesi, belirtilen bölgedeki müşterilere çıktıyı kısıtlamak için Aralık değişkenini kullanır. `For Each`Döngü, sorgu sonucunda her müşteri için şirket adını görüntüler.  
  
 [!code-vb[VbSimpleQuerySamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#23)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sorgular](index.md)
- [Visual Basic'de LINQ'e Giriş](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [For Each...Next Deyimi](../statements/for-each-next-statement.md)
- [For...Next Deyimi](../statements/for-next-statement.md)
- [Select yan tümcesi](select-clause.md)
- [WHERE yan tümcesi](where-clause.md)
- [Aggregate Yan Tümcesi](aggregate-clause.md)
- [Distinct Yan Tümcesi](distinct-clause.md)
- [JOIN yan tümcesi](join-clause.md)
- [Group Join Yan Tümcesi](group-join-clause.md)
- [Order By Yan Tümcesi](order-by-clause.md)
- [Let yan tümcesi](let-clause.md)
- [Skip Yan Tümcesi](skip-clause.md)
- [Take Yan Tümcesi](take-clause.md)
- [Skip While Yan Tümcesi](skip-while-clause.md)
- [Take While Yan Tümcesi](take-while-clause.md)
