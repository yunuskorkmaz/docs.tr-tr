---
title: Let Yan Tümcesi
ms.date: 07/20/2015
f1_keywords:
- vb.QueryLet
helpviewer_keywords:
- queries [Visual Basic], Let
- Let clause [Visual Basic]
- Let statement [Visual Basic]
ms.assetid: 981aa516-16eb-4c53-b1f1-5aa3e82f316e
ms.openlocfilehash: a6ff3fc80a2b6752c61a8b8f7d4ce62b5a46baad
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90869880"
---
# <a name="let-clause-visual-basic"></a>Let Tümcesi (Visual Basic)

Bir değeri hesaplar ve sorgu içindeki yeni bir değişkene atar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
Let variable = expression [, ...]  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`variable`|Gereklidir. Sağlanan ifadenin sonuçlarına başvurmak için kullanılabilecek bir diğer ad.|  
|`expression`|Gereklidir. Değerlendirilecek ve belirtilen değişkene atanacak bir ifade.|  
  
## <a name="remarks"></a>Açıklamalar  

 `Let`Yan tümcesi her sorgu sonucu için değerleri hesaplamanızı ve bir diğer ad kullanarak bunları başvurmanızı sağlar. Diğer ad yan tümce gibi diğer yan tümcelerde kullanılabilir `Where` . `Let`Yan tümcesi, sorguda yer alan bir ifade yan tümcesi için bir diğer ad belirtebileceğiniz ve ifade yan tümcesinin her kullanıldığı her seferinde diğer adı yerine geçecek bir sorgu deyimi oluşturmanıza olanak sağlar.  
  
 Yan tümcesine herhangi bir sayıda `variable` ve `expression` atama ekleyebilirsiniz `Let` . Her atamayı virgülle ayırın (,).  
  
## <a name="example"></a>Örnek  

 Aşağıdaki kod örneği, `Let` ürünlerde yüzde 10 indirimli iskontoyu hesaplamak için yan tümcesini kullanır.  
  
 [!code-vb[VbSimpleQuerySamples#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#16)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic'de LINQ'e Giriş](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [Sorgular](index.md)
- [Select yan tümcesi](select-clause.md)
- [From yan tümcesi](from-clause.md)
- [WHERE yan tümcesi](where-clause.md)
