---
title: Distinct Tümcesi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryDistinct
helpviewer_keywords:
- Distinct clause [Visual Basic]
- Distinct statement [Visual Basic]
- queries [Visual Basic], Distinct
ms.assetid: 86f42614-0d8f-4ffc-b888-ce8a37a8d36a
ms.openlocfilehash: 4b0ce12f6361d3dc6e5cc3601e96fc3a9bcf3841
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603983"
---
# <a name="distinct-clause-visual-basic"></a>Distinct Tümcesi (Visual Basic)
Yinelenen değerler sonraki sorgu yan tümcelerinde ortadan kaldırmak için geçerli aralık değişkeni değerlerini kısıtlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Distinct  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanabileceğiniz `Distinct` benzersiz öğeleri listesini döndürmek için yan tümcesi. `Distinct` Yan tümcesi yinelenen sorgu sonuçları yoksaymak sorgu neden olur. `Distinct` Yan tümcesi tüm tarafından belirtilen alanları dönmek için yinelenen değerler geçerlidir `Select` yan tümcesi. Öyle değilse `Select` yan tümcesi belirtilirse, `Distinct` yan tümcesinin aralık değişkeni tanımlanan sorgu için uygulanan `From` yan tümcesi. Aralık değişkeni bir sabit türü değilse türdeki tüm üyelerin varolan bir sorgu sonuç eşleşiyorsa sorgu yalnızca bir sorgu sonucu göz ardı eder.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki sorgu ifadesi müşterilerin listesini ve müşteri siparişleri listesini birleştirir. `Distinct` Benzersiz Müşteri adlarının bir listesini döndürür ve tarihleri sipariş yan tümcesi eklenmiştir.  
  
 [!code-vb[VbSimpleQuerySamples#20](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/distinct-clause_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic'de LINQ'e giriş](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Sorgular](../../../visual-basic/language-reference/queries/queries.md)  
 [From Yan Tümcesi](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Select Yan Tümcesi](../../../visual-basic/language-reference/queries/select-clause.md)  
 [Where Yan Tümcesi](../../../visual-basic/language-reference/queries/where-clause.md)
