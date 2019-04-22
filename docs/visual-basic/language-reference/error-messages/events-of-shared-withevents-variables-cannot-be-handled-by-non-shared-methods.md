---
title: Paylaşılan WithEvents değişkenlerinin olayları paylaşılmayan yöntemler tarafından işlenemez
ms.date: 07/20/2015
f1_keywords:
- bc30594
- vbc30594
helpviewer_keywords:
- BC30594
ms.assetid: 5b9fceb4-ab11-41bb-ad3b-6f1a9da8ae7e
ms.openlocfilehash: 2b32043898986b3e3e68fab18c5f907843d7691c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58838657"
---
# <a name="events-of-shared-withevents-variables-cannot-be-handled-by-non-shared-methods"></a>Paylaşılan WithEvents değişkenlerinin olayları paylaşılmayan yöntemler tarafından işlenemez
Bildirilen bir değişken `Shared` değiştiricisi paylaşılan bir değişkendir. Paylaşılan değişken tam olarak bir depolama konumunu tanımlar. Bildirilen bir değişken `WithEvents` değiştiricisi onaylar değişkeni ait olduğu tür değişken başlatır olay kümesini işler. Bir değeri bir değişkene atandığında, özellik tarafından oluşturulan `WithEvents` bildirimi var olan herhangi bir olay işleyici unhooks ve yeni olay işleyicisi'kurmak kancaları `Add` yöntemi.  
  
 **Hata Kimliği:** BC30594  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Olay işleyici bildirmek `Shared`.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Shared](../../../visual-basic/language-reference/modifiers/shared.md)
- [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)
