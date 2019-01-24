---
title: Varsayılan (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Default
helpviewer_keywords:
- defaults, properties
- properties [Visual Basic], default
- default properties, in Visual Basic
- Default keyword [Visual Basic]
- default properties
ms.assetid: 45fce9b9-d212-4b2d-ab86-6e359b8b57af
ms.openlocfilehash: b63fa66c9cda1e439e3917ca62377f68028fc049
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54497847"
---
# <a name="default-visual-basic"></a>Varsayılan (Visual Basic)
Bir özellik için varsayılan özelliği, sınıf, yapı veya arabirim tanımlar.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir sınıf, yapı veya arabirim özelliklerinden en fazla birine atayabilirsiniz *varsayılan özellik*, koşuluyla özellik en az bir parametre alır. Kod, bir üye belirtilmeden bir sınıf veya yapı için bir başvuru yaparsa, Visual Basic varsayılan özelliğinin bu başvuruyu çözümler.  
  
 Varsayılan Özellikler kaynak kod-harfler küçük azalmasına neden olabilir, ancak bunlar kodunuzu okunacak daha zor hale getirebilir. Bir sınıf veya yapı adı başvuru yaptığında çağıran kod, sınıf veya yapı, birlikte bilinen değilse, bu başvuruyu sınıf veya yapının kendisi veya varsayılan bir özellik olup erişen belirli olamaz. Bu, derleyici hataları veya Zarif çalışma zamanı mantık hataları neden olabilir.  
  
 Her zaman kullanarak biraz varsayılan özellik hata olasılığını azaltabilirsiniz [Option Strict deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md) derleyici tür denetlemesini ayarlanacak `On`.  
  
 Bir önceden tanımlanmış sınıf veya yapı kodunuzda belirlemeniz gerekir, varsayılan bir özellik sahip olup olmadığını ve bu durumda kullanmayı planlıyorsanız, onun adı nedir?  
  
 Bu dezavantajların nedeniyle varsayılan özellikleri tanımlamaya değil dikkate almalısınız. Kod okunabilirlik açısından, ayrıca her zaman tüm özelliklere açıkça başvuran göz önünde bulundurun, hatta özellikleri varsayılan.  
  
 `Default` Bu bağlamda değiştirici kullanılabilir:  
  
 [Property Deyimi](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: Bildirme ve Visual Basic'te bir varsayılan özelliğini çağırın](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)
- [Anahtar Sözcükler](../../../visual-basic/language-reference/keywords/index.md)
