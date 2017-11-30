---
title: "Paylaşılan WithEvents değişkenlerinin olayları paylaşılmayan yöntemler tarafından işlenemez"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30594
- vbc30594
helpviewer_keywords: BC30594
ms.assetid: 5b9fceb4-ab11-41bb-ad3b-6f1a9da8ae7e
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 53372927b88df3946583564492df42170f302739
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="events-of-shared-withevents-variables-cannot-be-handled-by-non-shared-methods"></a>Paylaşılan WithEvents değişkenlerinin olayları paylaşılmayan yöntemler tarafından işlenemez
İle bildirilen bir değişken `Shared` değiştiricisi paylaşılan bir değişkendir. Paylaşılan değişken tam olarak bir depolama konumu tanımlar. İle bildirilen bir değişken `WithEvents` değiştiricisi onaylar değişkeni ait olduğu türü değişkeni başlatır olay kümesini işler. Değişkene bir değer atandığında, özellik tarafından oluşturulan `WithEvents` bildirim varolan herhangi bir olay işleyicisini unhooks ve yeni olay işleyicisi kancalarını `Add` yöntemi.  
  
 **Hata Kimliği:** BC30594  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Olay işleyici bildirmek `Shared`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Paylaşılan](../../../visual-basic/language-reference/modifiers/shared.md)  
 [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)
