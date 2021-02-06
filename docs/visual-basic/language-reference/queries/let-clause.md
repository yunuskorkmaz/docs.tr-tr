---
description: 'Daha fazla bilgi edinin: Let tümcesi (Visual Basic)'
title: Let Yan Tümcesi
ms.date: 07/20/2015
f1_keywords:
- vb.QueryLet
helpviewer_keywords:
- queries [Visual Basic], Let
- Let clause [Visual Basic]
- Let statement [Visual Basic]
ms.assetid: 981aa516-16eb-4c53-b1f1-5aa3e82f316e
ms.openlocfilehash: 88a7d96bb790a1e6ec5adfa4337c51f807930168
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99653647"
---
# <a name="let-clause-visual-basic"></a>Let Tümcesi (Visual Basic)

Bir değeri hesaplar ve sorgu içindeki yeni bir değişkene atar.  
  
## <a name="syntax"></a>Syntax  
  
```vb  
Let variable = expression [, ...]  
```  
  
## <a name="parts"></a>Bölümler  
  
|Süre|Tanım|  
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
