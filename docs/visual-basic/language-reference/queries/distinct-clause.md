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
ms.openlocfilehash: 5aecffbce036500d294d03a925798d51f1269af6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401400"
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
