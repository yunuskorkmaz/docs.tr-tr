---
title: Paylaşılan WithEvents değişkenlerinin olayları paylaşılmayan yöntemler tarafından işlenemez
ms.date: 07/20/2015
f1_keywords:
- bc30594
- vbc30594
helpviewer_keywords:
- BC30594
ms.assetid: 5b9fceb4-ab11-41bb-ad3b-6f1a9da8ae7e
ms.openlocfilehash: f61f4cd17b1bb3088117e0a0d91b186fd40db3b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33585177"
---
# <a name="events-of-shared-withevents-variables-cannot-be-handled-by-non-shared-methods"></a>Paylaşılan WithEvents değişkenlerinin olayları paylaşılmayan yöntemler tarafından işlenemez
İle bildirilen bir değişken `Shared` değiştiricisi paylaşılan bir değişkendir. Paylaşılan değişken tam olarak bir depolama konumu tanımlar. İle bildirilen bir değişken `WithEvents` değiştiricisi onaylar değişkeni ait olduğu türü değişkeni başlatır olay kümesini işler. Değişkene bir değer atandığında, özellik tarafından oluşturulan `WithEvents` bildirim varolan herhangi bir olay işleyicisini unhooks ve yeni olay işleyicisi kancalarını `Add` yöntemi.  
  
 **Hata Kimliği:** BC30594  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Olay işleyici bildirmek `Shared`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Shared](../../../visual-basic/language-reference/modifiers/shared.md)  
 [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)
