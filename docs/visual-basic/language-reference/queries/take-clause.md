---
title: Take Tümcesi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTake
helpviewer_keywords:
- Take statement [Visual Basic]
- queries [Visual Basic], Take
- Take clause [Visual Basic]
ms.assetid: 77bf87b2-1476-4456-957f-fee922fbad8c
ms.openlocfilehash: 0dddb411af1b4ee269e091c07553a94589d90b2c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604035"
---
# <a name="take-clause-visual-basic"></a>Take Tümcesi (Visual Basic)
Belirtilen sayıda bitişik öğeyi koleksiyonu başından döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Take count  
```  
  
## <a name="parts"></a>Bölümler  
 `count`  
 Gerekli. Bir değer veya sıradaki döndürülecek sayısını veren ifade.  
  
## <a name="remarks"></a>Açıklamalar  
 `Take` Yan tümcesinde belirtilen sayıda sonuç listesini başından bitişik öğeyi dahil etmek bir sorgu neden olur. Eklenecek öğe sayısı tarafından belirtilen `count` parametresi.  
  
 Kullanabileceğiniz `Take` yan tümcesiyle birlikte `Skip` herhangi bir sorgu segment veri aralığını döndürülecek yan tümcesi. Bunu yapmak için aralığın ilk öğenin dizini geçirmek `Skip` yan tümcesi ve aralığa boyutunu `Take` yan tümcesi. Bu durumda, `Take` yan tümcesinde belirtilen, sonra `Skip` yan tümcesi.  
  
 Kullandığınızda `Take` yan tümcesinin sorgudaki de ihtiyacınız olabilecek sonuçları etkinleştirecek bir sırada döndürüldüğünden emin olmak `Take` amaçlanan sonuçlara dahil etmek için yan tümcesi. Sorgu sonuçlarını sıralama hakkında daha fazla bilgi için bkz: [Order By yan tümcesi](../../../visual-basic/language-reference/queries/order-by-clause.md).  
  
 Kullanabileceğiniz `TakeWhile` yan tümcesini yalnızca belirli öğeler, sağlanan bir koşula göre döndürülmesi gerektiğini belirtin.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde `Take` yan tümcesi ile birlikte `Skip` sayfaları sorguda veri döndürmek için yan tümcesi. GetCustomers işlev kullanır `Skip` sağlanan başlangıç dizini kadar değeri ve kullandığı listesinde müşterileri atlamak için yan tümceyi `Take` yan tümcesi bu dizin değerden başlayan müşteriler, bir sayfaya dönün.  
  
 [!code-vb[VbSimpleQuerySamples#1](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/take-clause_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic'de LINQ'e giriş](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Sorgular](../../../visual-basic/language-reference/queries/queries.md)  
 [Select Yan Tümcesi](../../../visual-basic/language-reference/queries/select-clause.md)  
 [From Yan Tümcesi](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Order By Yan Tümcesi](../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [Take While Yan Tümcesi](../../../visual-basic/language-reference/queries/take-while-clause.md)  
 [Skip Yan Tümcesi](../../../visual-basic/language-reference/queries/skip-clause.md)
