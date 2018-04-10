---
title: Varsayılan (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Default
helpviewer_keywords:
- defaults, properties
- properties [Visual Basic], default
- default properties, in Visual Basic
- Default keyword [Visual Basic]
- default properties
ms.assetid: 45fce9b9-d212-4b2d-ab86-6e359b8b57af
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 18126a0a5b6254da0b43e806b3de1f5b2127e6a9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="default-visual-basic"></a>Varsayılan (Visual Basic)
Bir özelliğin varsayılan özelliği sınıf, yapı veya arabirim tanımlar.  
  
## <a name="remarks"></a>Açıklamalar  
 Sınıf, yapı veya arabirim ve özelliklerini en fazla bir belirleyebileceğiniz *varsayılan özellik*, koşuluyla özelliği en az bir parametre alır. Kod bir üye belirtilmeden bir sınıf veya yapı için bir başvuru yaparsa, Visual Basic bu varsayılan özellik referansı çözümler.  
  
 Varsayılan Özellikler kaynak kod-karakterlerini küçük azalmasına neden olabilir, ancak bunlar kodunuzu okumak daha zor hale getirebilir. Sınıf veya yapı adı için bir başvuru yaptığında, çağrıyı yapan kod, sınıf veya yapı, bilinen değilse, bu başvuru sınıf veya yapı kendisini veya varsayılan bir özellik mi erişen belirli olamaz. Bu derleyici hataları veya Zarif çalışma zamanı mantık hataları neden olabilir.  
  
 Her zaman kullanarak varsayılan özellik hataları olasılığını biraz azaltabilir [Option Strict deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md) denetlemesini derleyici türünü ayarlamak için `On`.  
  
 Önceden tanımlanmış sınıf veya yapı kodunuzda belirlemeniz gerekir varsayılan bir özellik olup olmadığını ve bu durumda kullanmayı planlıyorsanız, ne adıdır.  
  
 Bu olumsuzlukları nedeniyle varsayılan özellikleri tanımlamaya değil göz önünde bulundurmalısınız. Kod okunabilirlik için ayrıca her zaman tüm özelliklerini açıkça başvuran göz önünde bulundurun, hatta özellikleri varsayılan.  
  
 `Default` Bu bağlamda değiştirici kullanılabilir:  
  
 [Property deyimi](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: bildirme ve Visual Basic'te varsayılan özelliğini çağırın](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)  
 [Anahtar sözcükler](../../../visual-basic/language-reference/keywords/index.md)
