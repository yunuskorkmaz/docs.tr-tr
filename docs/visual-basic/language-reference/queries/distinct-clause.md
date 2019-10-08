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
ms.openlocfilehash: e8d3e38261a04c4d29faab351d24d6710413b09a
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004794"
---
# <a name="distinct-clause-visual-basic"></a>Distinct Tümcesi (Visual Basic)
Sonraki sorgu yan tümcelerinde yinelenen değerleri ortadan kaldırmak için geçerli aralık değişkeninin değerlerini kısıtlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
Distinct  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Benzersiz öğelerin bir listesini döndürmek için `Distinct` yan tümcesini kullanabilirsiniz. @No__t-0 yan tümcesi sorgunun yinelenen sorgu sonuçlarını yoksaymasına neden olur. @No__t-0 yan tümcesi, `Select` yan tümcesi tarafından belirtilen tüm dönüş alanları için yinelenen değerler için geçerlidir. @No__t-0 yan tümcesi belirtilmemişse, `Distinct` yan tümcesi `From` yan tümcesinde tanımlanan sorgu için Aralık değişkenine uygulanır. Aralık değişkeni sabit bir tür değilse, sorgu Yalnızca türün tüm üyeleri var olan bir sorgu sonucuyla eşleşiyorsa sorgu sonucunu yoksayar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki sorgu ifadesi bir müşteri listesini ve müşteri siparişlerinin bir listesini birleştirir. @No__t-0 yan tümcesi, benzersiz müşteri adları ve sipariş tarihlerinin listesini döndürmek için dahil edilmiştir.  
  
 [!code-vb[VbSimpleQuerySamples#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#20)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic LINQ 'e giriş](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Sorgular](../../../visual-basic/language-reference/queries/index.md)
- [From Yan Tümcesi](../../../visual-basic/language-reference/queries/from-clause.md)
- [Select Yan Tümcesi](../../../visual-basic/language-reference/queries/select-clause.md)
- [Where Yan Tümcesi](../../../visual-basic/language-reference/queries/where-clause.md)
