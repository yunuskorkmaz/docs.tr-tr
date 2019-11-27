---
title: Where Tümcesi
ms.date: 07/20/2015
f1_keywords:
- vb.QueryWhere
helpviewer_keywords:
- Where statement [Visual Basic]
- queries [Visual Basic], Where
- Where clause [Visual Basic]
ms.assetid: 48b5c2c5-3181-429c-8545-894296798c89
ms.openlocfilehash: 60b7ebe96ce0c4580c36675b2e4aa5f9888732c3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349623"
---
# <a name="where-clause-visual-basic"></a>Where Tümcesi (Visual Basic)
Bir sorgu için filtreleme koşulunu belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
Where condition  
```  
  
## <a name="parts"></a>Bölümler  
 `condition`  
 Gerekli. Koleksiyonda geçerli öğenin değerlerinin çıkış koleksiyonuna dahil edilip edilmeyeceğini belirleyen bir ifade. İfade bir `Boolean` değeri veya bir `Boolean` değerinin eşdeğerini olarak değerlendirilmelidir. Koşul `True`olarak değerlendirilirse, öğe sorgu sonucuna dahil edilir; Aksi takdirde, öğe sorgu sonucundan çıkarılır.  
  
## <a name="remarks"></a>Açıklamalar  
 `Where` yan tümcesi yalnızca belirli ölçütlere uyan öğeleri seçerek sorgu verilerini filtrelemenizi sağlar. Değerleri, `Where` yan tümcesinin `True` değerlendirmesine neden olan öğeler sorgu sonucuna dahil edilir; diğer öğeler hariç tutulur. `Where` yan tümcesinde kullanılan ifade, değeri sıfır olduğunda `False` değerlendirilen bir tamsayı gibi bir `Boolean` veya `Boolean`eşdeğerini değerlendirmelidir. `And`, `Or`, `AndAlso`, `OrElse`, `Is`ve `IsNot`gibi mantıksal işleçleri kullanarak bir `Where` yan tümcesinde birden çok ifadeyi birleştirebilirsiniz.  
  
 Varsayılan olarak, sorgu ifadeleri erişilene kadar değerlendirilmez — Örneğin, veri bağladığında veya bir `For` döngüsünde yinelendiğinde. Sonuç olarak, `Where` yan tümcesi sorguya erişilene kadar değerlendirilmez. `Where` yan tümcesinde kullanılan sorguya harici değerleriniz varsa, sorgu yürütüldüğü sırada `Where` yan tümcesinde uygun değerin kullanıldığından emin olun. Sorgu yürütme hakkında daha fazla bilgi için, bkz. [Ilk LINQ sorgunuzu yazma](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).  
  
 Koleksiyondaki geçerli öğeden bir değer üzerinde hesaplama veya işlem gerçekleştirmek için, bir `Where` yan tümcesindeki işlevleri çağırabilirsiniz. Bir işlevi `Where` yan tümcesinde çağırmak, sorgunun ne zaman yerine tanımlanmadığında hemen yürütülmesine neden olabilir. Sorgu yürütme hakkında daha fazla bilgi için, bkz. [Ilk LINQ sorgunuzu yazma](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki sorgu ifadesi, `customers` koleksiyonundaki her bir `Customer` nesnesi için bir Aralık değişkeni `cust` bildirmek üzere bir `From` yan tümcesi kullanır. `Where` yan tümcesi, belirtilen bölgedeki müşterilere çıktıyı kısıtlamak için Aralık değişkenini kullanır. `For Each` döngüsü, sorgu sonucundaki her bir müşteri için şirket adını görüntüler.  
  
 [!code-vb[VbSimpleQuerySamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#23)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `Where` yan tümcesindeki `And` ve `Or` mantıksal işleçler kullanır.  
  
 [!code-vb[VbSimpleQuerySamples#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#31)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic LINQ 'e giriş](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Sorgular](../../../visual-basic/language-reference/queries/index.md)
- [From Yan Tümcesi](../../../visual-basic/language-reference/queries/from-clause.md)
- [Select Yan Tümcesi](../../../visual-basic/language-reference/queries/select-clause.md)
- [For Each...Next Deyimi](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
