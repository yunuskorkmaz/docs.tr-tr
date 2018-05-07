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
ms.openlocfilehash: 0b61a52a366fb37a0834c9223bc8b7f099354d16
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="where-clause-visual-basic"></a>Where Tümcesi (Visual Basic)
Bir sorgu için bir filtre koşulu belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Where condition  
```  
  
## <a name="parts"></a>Bölümler  
 `condition`  
 Gerekli. Koleksiyondaki geçerli öğe için değerleri çıktı koleksiyonunda dahil edilip edilmeyeceğini belirler bir ifade. İfade değerlendirilmelidir bir `Boolean` değeri veya eşdeğer bir `Boolean` değeri. Koşul değerlendirilirse `True`öğesi sorgu sonucu dahil; tersi durumda, gelen sorgu sonucu öğe dışlandı.  
  
## <a name="remarks"></a>Açıklamalar  
 `Where` Yan tümcesi, yalnızca belirli ölçütlere uyan öğeleri seçerek verileri Sorgulama filtre olanak tanır. Değerleri neden öğeleri `Where` olarak değerlendirilmesi için yan tümceyi `True` sorgu sonucu; dahil diğer öğeleri hariç tutulur. Kullanılan ifade bir `Where` gerekir yan tümcesi değerlendirmek için bir `Boolean` veya eşdeğer bir `Boolean`, değerlendiren bir tamsayı gibi `False` değeri sıfır olduğunda. Birden çok ifadelerinde birleştirebilirsiniz bir `Where` mantıksal işleçler gibi kullanılarak by yan tümcesi `And`, `Or`, `AndAlso`, `OrElse`, `Is`, ve `IsNot`.  
  
 Bunlar erişim kadar varsayılan olarak, sorgu ifadeleri değerlendirilmeyen — Örneğin, olduklarında veri bağlama veya içinde aracılığıyla tekrarlayan bir `For` döngü. Sonuç olarak, `Where` yan tümcesi sorgu erişim kadar değerlendirilmez. Değerleri için kullanılan sorgu dış varsa `Where` yan tümcesi, uygun değeri olarak kullanıldığından emin olun `Where` sorgu yürütüldüğünde zaman yan tümcesi. Sorgu yürütme hakkında daha fazla bilgi için bkz: [yazma bilgisayarınızı ilk LINQ sorgusu](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).  
  
 İşlevler içinde çağırabilirsiniz bir `Where` koleksiyondaki geçerli öğeden bir hesaplama veya bir değer işlemi gerçekleştirmek için yan tümcesi. Bir işlev arayan bir `Where` yan tümcesi, erişildiğinde ne zaman yerine tanımlanan hemen yürütülecek sorgu neden olabilir. Sorgu yürütme hakkında daha fazla bilgi için bkz: [yazma bilgisayarınızı ilk LINQ sorgusu](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki sorgu ifade kullanan bir `From` yan tümcesinin aralık değişkeni bildirmek için `cust` her `Customer` nesnesinde `customers` koleksiyonu. `Where` Yan tümcesi, çıkış müşterilere belirtilen bölgesinden kısıtlamak için aralık değişkeni kullanır. `For Each` Döngü sorgu sonucunda her müşteri için şirket adını görüntüler.  
  
 [!code-vb[VbSimpleQuerySamples#23](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/where-clause_1.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanır `And` ve `Or` mantıksal işleçler `Where` yan tümcesi.  
  
 [!code-vb[VbSimpleQuerySamples#31](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/where-clause_2.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic'de LINQ'e giriş](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Sorgular](../../../visual-basic/language-reference/queries/queries.md)  
 [From Yan Tümcesi](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Select Yan Tümcesi](../../../visual-basic/language-reference/queries/select-clause.md)  
 [For Each...Next Deyimi](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
