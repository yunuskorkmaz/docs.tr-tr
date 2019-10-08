---
title: Where Tümcesi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryWhere
helpviewer_keywords:
- Where statement [Visual Basic]
- queries [Visual Basic], Where
- Where clause [Visual Basic]
ms.assetid: 48b5c2c5-3181-429c-8545-894296798c89
ms.openlocfilehash: 404dd848058f7e5c9bc8a74b6d89df18c6c55fad
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005006"
---
# <a name="where-clause-visual-basic"></a>Where Tümcesi (Visual Basic)
Bir sorgu için filtreleme koşulunu belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
Where condition  
```  
  
## <a name="parts"></a>Bölümler  
 `condition`  
 Gerekli. Koleksiyonda geçerli öğenin değerlerinin çıkış koleksiyonuna dahil edilip edilmeyeceğini belirleyen bir ifade. İfade `Boolean` değeri veya `Boolean` değerinin eşdeğerini olarak değerlendirilmelidir. Koşul `True` olarak değerlendirilirse, öğe sorgu sonucuna dahil edilir; Aksi takdirde, öğe sorgu sonucundan çıkarılır.  
  
## <a name="remarks"></a>Açıklamalar  
 @No__t-0 yan tümcesi yalnızca belirli ölçütlere uyan öğeleri seçerek sorgu verilerini filtrelemenizi sağlar. Değerleri `Where` yan tümcesinin `True` olarak değerlendirilmesine neden olan öğeler sorgu sonucuna dahil edilir; diğer öğeler hariç tutulur. @No__t-0 yan tümcesinde kullanılan ifade, değeri sıfır olduğunda `False` ' i değerlendiren bir tamsayı gibi bir `Boolean` veya `Boolean` eşdeğerini değerlendirmelidir. @No__t-0 yan tümcesinde birden çok ifadeyi `And`, `Or`, `AndAlso`, `OrElse`, `Is` ve `IsNot` gibi mantıksal işleçler kullanarak birleştirebilirsiniz.  
  
 Varsayılan olarak, sorgu ifadeleri erişilene kadar değerlendirilmez — Örneğin, veri bağladığında veya bir `For` döngüsüyle aracılığıyla tekrarlandırılır. Sonuç olarak, `Where` yan tümcesi sorguya erişilene kadar değerlendirilmez. @No__t-0 yan tümcesinde kullanılan sorguya harici değerleriniz varsa, sorgu yürütüldüğü sırada `Where` yan tümcesinde uygun değerin kullanıldığından emin olun. Sorgu yürütme hakkında daha fazla bilgi için, bkz. [Ilk LINQ sorgunuzu yazma](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).  
  
 Koleksiyondaki geçerli öğeden bir değer üzerinde hesaplama veya işlem gerçekleştirmek için bir `Where` yan tümcesindeki işlevleri çağırabilirsiniz. Bir `Where` yan tümcesinde bir işlevi çağırmak sorgunun ne zaman tanımlanmadığında değil, sorgunun doğrudan yürütülmesine neden olabilir. Sorgu yürütme hakkında daha fazla bilgi için, bkz. [Ilk LINQ sorgunuzu yazma](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki sorgu ifadesi, `customers` koleksiyonundaki her bir `Customer` nesnesi için bir Aralık değişkeni `cust` olarak bildirmek üzere bir `From` yan tümcesi kullanır. @No__t-0 yan tümcesi, belirtilen bölgedeki müşterilere çıktıyı kısıtlamak için Aralık değişkenini kullanır. @No__t-0 döngüsü sorgu sonucunda her müşteri için şirket adını görüntüler.  
  
 [!code-vb[VbSimpleQuerySamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#23)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek `Where` yan tümcesinde `And` ve `Or` mantıksal işleçler kullanır.  
  
 [!code-vb[VbSimpleQuerySamples#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#31)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic LINQ 'e giriş](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Sorgular](../../../visual-basic/language-reference/queries/index.md)
- [From Yan Tümcesi](../../../visual-basic/language-reference/queries/from-clause.md)
- [Select Yan Tümcesi](../../../visual-basic/language-reference/queries/select-clause.md)
- [For Each...Next Deyimi](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
