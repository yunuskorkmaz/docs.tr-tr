---
title: Distinct Yan Tümcesi
ms.date: 07/20/2015
f1_keywords:
- vb.QueryDistinct
helpviewer_keywords:
- Distinct clause [Visual Basic]
- Distinct statement [Visual Basic]
- queries [Visual Basic], Distinct
ms.assetid: 86f42614-0d8f-4ffc-b888-ce8a37a8d36a
ms.openlocfilehash: 49eaab2e6a8c48d61518ea51ef2f644b6eb48314
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875285"
---
# <a name="distinct-clause-visual-basic"></a>Distinct Tümcesi (Visual Basic)

Sonraki sorgu yan tümcelerinde yinelenen değerleri ortadan kaldırmak için geçerli aralık değişkeninin değerlerini kısıtlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
Distinct  
```  
  
## <a name="remarks"></a>Açıklamalar  

 `Distinct`Yan tümcesini kullanarak benzersiz öğelerin bir listesini döndürebilirsiniz. `Distinct`Yan tümce sorgunun yinelenen sorgu sonuçlarını yoksaymasına neden olur. `Distinct`Yan tümcesi, yan tümcesi tarafından belirtilen tüm dönüş alanları için yinelenen değerler için geçerlidir `Select` . Hiçbir `Select` yan tümce belirtilmemişse yan tümce, `Distinct` yan tümcesinde tanımlanan sorgu için Aralık değişkenine uygulanır `From` . Aralık değişkeni sabit bir tür değilse, sorgu Yalnızca türün tüm üyeleri var olan bir sorgu sonucuyla eşleşiyorsa sorgu sonucunu yoksayar.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki sorgu ifadesi bir müşteri listesini ve müşteri siparişlerinin bir listesini birleştirir. `Distinct`Yan tümcesi, benzersiz müşteri adları ve sipariş tarihlerinin listesini döndürmek için dahil edilmiştir.  
  
 [!code-vb[VbSimpleQuerySamples#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#20)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic'de LINQ'e Giriş](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [Sorgular](index.md)
- [From yan tümcesi](from-clause.md)
- [Select yan tümcesi](select-clause.md)
- [WHERE yan tümcesi](where-clause.md)
