---
title: "Türetilmiş sınıflar temel sınıf olayları oluşturamaz"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30029
- bc30029
helpviewer_keywords: BC30029
ms.assetid: 63afa1c6-2f93-4512-a2f0-372455979771
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 70dde8b96980adfd618e38b9ce142cdec56a6b13
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="derived-classes-cannot-raise-base-class-events"></a>Türetilmiş sınıflar temel sınıf olayları oluşturamaz
Bir olay, içinde bildirildiği yalnızca bildirim alanından yükseltilebilir. Bu nedenle, bir sınıfın başka bir sınıf, hatta bir onu türetildiği olaylarından yükseltemez.  
  
 **Hata Kimliği:** BC30029  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Taşıma `Event` deyimi veya `RaiseEvent` aynı sınıfta; bu nedenle deyimi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Event deyimi](../../../visual-basic/language-reference/statements/event-statement.md)  
 [RaiseEvent deyimi](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
