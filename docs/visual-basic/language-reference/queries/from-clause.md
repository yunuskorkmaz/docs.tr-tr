---
title: From Tümcesi (Visual Basic)
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
ms.openlocfilehash: 781902f1bf28bd029c8d9825aee155a6691cbae9
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004784"
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
|`element`|Gerekli. Koleksiyonun öğeleri boyunca yinelemek için kullanılan bir *Aralık değişkeni* . Sorgu `collection` ' de yineleme yaparken, `collection` ' ın her üyesine başvurmak için bir Aralık değişkeni kullanılır. Sıralanabilir bir tür olmalıdır.|  
|`type`|İsteğe bağlı. @No__t türü-0. @No__t-0 belirtilmemişse, `element` türü `collection` ' den çıkarsanamıyor.|  
|`collection`|Gerekli. Sorgulanacak koleksiyona başvurur. Sıralanabilir bir tür olmalıdır.|  
  
## <a name="remarks"></a>Açıklamalar  
 @No__t-0 yan tümcesi, bir sorgunun kaynak verilerini ve kaynak koleksiyondaki bir öğeye başvurmak için kullanılan değişkenleri belirlemek için kullanılır. Bu değişkenlere *Aralık değişkenleri*denir. @No__t-0 yan tümcesi, yalnızca toplanmış sonuçları döndüren bir sorguyu tanımlamak için `Aggregate` yan tümcesinin kullanıldığı durumlar dışında, bir sorgu için gereklidir. Daha fazla bilgi için bkz. [toplama yan tümcesi](../../../visual-basic/language-reference/queries/aggregate-clause.md).  
  
 Birleştirilecek birden çok koleksiyonu belirlemek için bir sorguda birden fazla `From` yan tümcesi belirtebilirsiniz. Birden çok koleksiyon belirtildiğinde, bunlar birbirinden bağımsız olarak yinelenir veya ilişkili olmaları durumunda bunlara katılabilirler. @No__t-0 yan tümcesini kullanarak veya açıkça `Join` veya `Group Join` yan tümceleri kullanarak koleksiyonlar ekleyebilirsiniz. Alternatif olarak, tek bir `From` yan tümcesinde birden çok Aralık değişkeni ve koleksiyonlar belirterek, her ilgili Aralık değişkeni ve koleksiyon diğerlerinden virgülle ayrılır. Aşağıdaki kod örneği `From` yan tümcesi için her iki sözdizimi seçeneğini gösterir.  
  
 [!code-vb[VbSimpleQuerySamples#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#21)]  
  
 @No__t-0 yan tümcesi, bir `For` döngüsünün kapsamına benzer bir sorgunun kapsamını tanımlar. Bu nedenle, bir sorgunun kapsamındaki her @no__t 0 Aralık değişkeni benzersiz bir ada sahip olmalıdır. Bir sorgu için birden çok `From` yan tümcesi belirtebileceğiniz için, sonraki `From` yan tümceleri `From` yan tümcesindeki Aralık değişkenlerine başvurabilir veya önceki bir `From` yan tümcesindeki Aralık değişkenlerine başvurabilir. Örneğin, aşağıdaki örnek, ikinci yan tümcesindeki koleksiyonun ilk yan tümcesindeki Range değişkeninin bir özelliğine dayandığı iç içe `From` yan tümcesini gösterir.  
  
 [!code-vb[VbSimpleQuerySamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#22)]  
  
 Her `From` yan tümcesine sorgu iyileştirmek için ek sorgu yan tümcelerinin herhangi bir birleşimi gelebilir. Sorguyu aşağıdaki yollarla geliştirebilirsiniz:  
  
- Birden çok koleksiyonu dolaylı olarak `From` ve `Select` yan tümceleri kullanarak veya `Join` veya `Group Join` yan tümceleri kullanarak açıkça birleştirin.  
  
- Sorgu sonucunu filtrelemek için `Where` yan tümcesini kullanın.  
  
- @No__t-0 yan tümcesini kullanarak sonucu sıralayın.  
  
- Benzer sonuçları, `Group By` yan tümcesini kullanarak birlikte gruplandırın.  
  
- Tüm sorgu sonucu için değerlendirmek üzere toplama işlevlerini belirlemek için `Aggregate` yan tümcesini kullanın.  
  
- Değeri bir koleksiyon yerine bir ifade tarafından belirlenen bir yineleme değişkenini tanıtmak için `Let` yan tümcesini kullanın.  
  
- Yinelenen sorgu sonuçlarını yoksaymak için `Distinct` yan tümcesini kullanın.  
  
- @No__t-0, `Take`, `Skip While` ve `Take While` yan tümcelerini kullanarak döndürülecek sonuç parçalarını belirler.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki sorgu ifadesi, `customers` koleksiyonundaki her bir `Customer` nesnesi için bir Aralık değişkeni `cust` olarak bildirmek üzere bir `From` yan tümcesi kullanır. @No__t-0 yan tümcesi, belirtilen bölgedeki müşterilere çıktıyı kısıtlamak için Aralık değişkenini kullanır. @No__t-0 döngüsü sorgu sonucunda her müşteri için şirket adını görüntüler.  
  
 [!code-vb[VbSimpleQuerySamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#23)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sorgular](../../../visual-basic/language-reference/queries/index.md)
- [Visual Basic LINQ 'e giriş](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [For Each...Next Deyimi](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [For...Next Deyimi](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Select Yan Tümcesi](../../../visual-basic/language-reference/queries/select-clause.md)
- [Where Yan Tümcesi](../../../visual-basic/language-reference/queries/where-clause.md)
- [Aggregate Yan Tümcesi](../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [Distinct Yan Tümcesi](../../../visual-basic/language-reference/queries/distinct-clause.md)
- [Join Yan Tümcesi](../../../visual-basic/language-reference/queries/join-clause.md)
- [Group Join Yan Tümcesi](../../../visual-basic/language-reference/queries/group-join-clause.md)
- [Order By Yan Tümcesi](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [Let Yan Tümcesi](../../../visual-basic/language-reference/queries/let-clause.md)
- [Skip Yan Tümcesi](../../../visual-basic/language-reference/queries/skip-clause.md)
- [Take Yan Tümcesi](../../../visual-basic/language-reference/queries/take-clause.md)
- [Skip While Yan Tümcesi](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [Take While Yan Tümcesi](../../../visual-basic/language-reference/queries/take-while-clause.md)
