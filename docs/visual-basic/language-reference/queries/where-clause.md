---
title: Where Tümcesi (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QueryWhere
helpviewer_keywords:
- Where statement [Visual Basic]
- queries [Visual Basic], Where
- Where clause [Visual Basic]
ms.assetid: 48b5c2c5-3181-429c-8545-894296798c89
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8c2572f513d00bc72e869cf28d382be799f7a303
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 [Sorguları](../../../visual-basic/language-reference/queries/queries.md)  
 [From yan tümcesi](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Select tümcesi](../../../visual-basic/language-reference/queries/select-clause.md)  
 [For Each... Sonraki deyim](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
