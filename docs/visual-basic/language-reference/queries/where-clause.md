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
ms.openlocfilehash: 5ecfc523573a6ab8142a04557156a3819eed440e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54662302"
---
# <a name="where-clause-visual-basic"></a>Where Tümcesi (Visual Basic)
Bir sorgu için filtreleme koşulunu belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Where condition  
```  
  
## <a name="parts"></a>Bölümler  
 `condition`  
 Gerekli. Bir ifade koleksiyondaki geçerli öğe değerlerini çıkış koleksiyonda bulunup bulunmadığını belirler. İfade değerlendirilmelidir bir `Boolean` değeri veya eşdeğer bir `Boolean` değeri. İçin değerlendirilen koşul yoksa `True`öğe sorgu sonucuna dahil, aksi takdirde, sorgu sonucu öğe çıkarılır.  
  
## <a name="remarks"></a>Açıklamalar  
 `Where` Yan tümcesi yalnızca belirli ölçütlere uyan öğeleri seçerek sorgu verilerini filtrelemek etkinleştirir. Değerleri neden öğeleri `Where` yan tümcesi için değerlendirilecek `True` sorgu sonucunda; dahil edilen diğer öğeleri hariç tutulur. Kullanılan ifade bir `Where` yan tümcesi gerekir değerlendirmek için bir `Boolean` veya eşdeğer bir `Boolean`, değerlendiren bir tamsayı gibi `False` değeri sıfır olduğunda. Birden çok ifadeleri birleştirebilirsiniz bir `Where` mantıksal işleçler gibi kullanarak yan tümcesi `And`, `Or`, `AndAlso`, `OrElse`, `Is`, ve `IsNot`.  
  
 Varsayılan olarak, bunlar erişene kadar sorgu ifadeleri değerlendirilmeyen — Örneğin, olduklarında veri bağlama veya içinde aracılığıyla tekrarlayan bir `For` döngü. Sonuç olarak, `Where` yan tümce sorgu erişinceye kadar değerlendirilmez. Değerleri için kullanılan sorgu dış olup olmadığını `Where` yan tümcesi, uygun değeri olarak kullanıldığından emin olun `Where` sorgu yürütüldüğünde zaman yan tümcesi. Sorgu yürütme hakkında daha fazla bilgi için bkz: [bilgisayarınızı ilk LINQ sorgusu yazma](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).  
  
 İşlevler içinde çağırabilirsiniz bir `Where` yan geçerli öğe koleksiyonundaki bir hesaplama veya bir değer işlemi gerçekleştirin. Bir işlev arayan bir `Where` yan tümcesi, erişildiğinde ne zaman yerine tanımlanan hemen yürütülecek sorgu neden olabilir. Sorgu yürütme hakkında daha fazla bilgi için bkz: [bilgisayarınızı ilk LINQ sorgusu yazma](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki sorgu ifadesi kullanan bir `From` yan tümcesinin aralık değişkenini bildirmek için `cust` her `Customer` nesnesine `customers` koleksiyonu. `Where` Yan tümcesi, çıkış belirtilen bölgeden müşterilere kısıtlamak için aralık değişkeni kullanır. `For Each` Döngü, her müşteri için şirket adı sorgu sonucu görüntüler.  
  
 [!code-vb[VbSimpleQuerySamples#23](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/where-clause_1.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte `And` ve `Or` mantıksal işleçler `Where` yan tümcesi.  
  
 [!code-vb[VbSimpleQuerySamples#31](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/where-clause_2.vb)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Visual Basic'de LINQ'e giriş](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Sorgular](../../../visual-basic/language-reference/queries/index.md)
- [From Yan Tümcesi](../../../visual-basic/language-reference/queries/from-clause.md)
- [Select Yan Tümcesi](../../../visual-basic/language-reference/queries/select-clause.md)
- [For Each...Next Deyimi](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
