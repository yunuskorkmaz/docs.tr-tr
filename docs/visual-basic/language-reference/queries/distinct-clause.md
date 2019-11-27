---
title: Distinct Tümcesi
ms.date: 07/20/2015
f1_keywords:
- vb.QueryDistinct
helpviewer_keywords:
- Distinct clause [Visual Basic]
- Distinct statement [Visual Basic]
- queries [Visual Basic], Distinct
ms.assetid: 86f42614-0d8f-4ffc-b888-ce8a37a8d36a
ms.openlocfilehash: 94471898807ef4552564c3e01465f2b2f6211d0c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74335373"
---
# <a name="distinct-clause-visual-basic"></a>Distinct Tümcesi (Visual Basic)
Sonraki sorgu yan tümcelerinde yinelenen değerleri ortadan kaldırmak için geçerli aralık değişkeninin değerlerini kısıtlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
Distinct  
```  
  
## <a name="remarks"></a>Açıklamalar  
 `Distinct` yan tümcesini kullanarak benzersiz öğelerin bir listesini döndürebilirsiniz. `Distinct` yan tümcesi sorgunun yinelenen sorgu sonuçlarını yoksaymasına neden olur. `Distinct` yan tümcesi, `Select` yan tümcesi tarafından belirtilen tüm dönüş alanları için yinelenen değerler için geçerlidir. `Select` yan tümcesi belirtilmemişse, `Distinct` yan tümcesi, `From` yan tümcesinde tanımlanan sorgu için Aralık değişkenine uygulanır. Aralık değişkeni sabit bir tür değilse, sorgu Yalnızca türün tüm üyeleri var olan bir sorgu sonucuyla eşleşiyorsa sorgu sonucunu yoksayar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki sorgu ifadesi bir müşteri listesini ve müşteri siparişlerinin bir listesini birleştirir. `Distinct` yan tümcesi, benzersiz müşteri adları ve sipariş tarihlerinin listesini döndürmek için eklenmiştir.  
  
 [!code-vb[VbSimpleQuerySamples#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#20)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic LINQ 'e giriş](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Sorgular](../../../visual-basic/language-reference/queries/index.md)
- [From Yan Tümcesi](../../../visual-basic/language-reference/queries/from-clause.md)
- [Select Yan Tümcesi](../../../visual-basic/language-reference/queries/select-clause.md)
- [Where Yan Tümcesi](../../../visual-basic/language-reference/queries/where-clause.md)
