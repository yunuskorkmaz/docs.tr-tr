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
ms.openlocfilehash: 00a2e52bd6669869bb2e25bc2857f1598da5763f
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56971253"
---
# <a name="distinct-clause-visual-basic"></a>Distinct Tümcesi (Visual Basic)
Sonraki sorgu yan tümceleri içinde yinelenen değerleri ortadan kaldırmak için geçerli aralık değişkeni değerlerini sınırlandırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Distinct  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanabileceğiniz `Distinct` yan benzersiz öğelerin listesini döndürür. `Distinct` Yan tümcesi yinelenen sorgu sonuçlarını yok saymak sorgu neden olur. `Distinct` Yan tümcesi tüm alanlar tarafından belirtilen döndürmek için yinelenen değerlere uygulanan `Select` yan tümcesi. Hayır ise `Select` yan tümcesi belirtildiğinde, `Distinct` yan tümcesinin aralık değişkeni içinde belirtilen sorgu için uygulanan `From` yan tümcesi. Aralık değişkeni bir sabit türü değilse, türün tüm üyeleri varolan bir sorgu sonucu eşleşiyorsa sorgu yalnızca bir sorgu sonucunu yoksayar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki sorgu ifadesi, müşterilerin listesini ve müşteri siparişlerinin listesi birleştirir. `Distinct` Benzersiz Müşteri adlarının bir listesini döndürür ve sipariş tarihlerini yan tümcesi dahildir.  
  
 [!code-vb[VbSimpleQuerySamples#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#20)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Visual Basic'de LINQ'e giriş](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Sorgular](../../../visual-basic/language-reference/queries/index.md)
- [From Yan Tümcesi](../../../visual-basic/language-reference/queries/from-clause.md)
- [Select Yan Tümcesi](../../../visual-basic/language-reference/queries/select-clause.md)
- [Where Yan Tümcesi](../../../visual-basic/language-reference/queries/where-clause.md)
