---
title: Paylaşılan WithEvents değişkenlerinin olayları paylaşılmayan yöntemler tarafından işlenemez
ms.date: 07/20/2015
f1_keywords:
- bc30594
- vbc30594
helpviewer_keywords:
- BC30594
ms.assetid: 5b9fceb4-ab11-41bb-ad3b-6f1a9da8ae7e
ms.openlocfilehash: fc163c1069aa6f41766664e0fa5f5a9c34a1f73d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409575"
---
# <a name="events-of-shared-withevents-variables-cannot-be-handled-by-non-shared-methods"></a>Paylaşılan WithEvents değişkenlerinin olayları paylaşılmayan yöntemler tarafından işlenemez
Değiştiriciyle belirtilen bir değişken `Shared` paylaşılan bir değişkendir. Paylaşılan değişken tam olarak bir depolama konumunu tanımlar. Değiştirici ile belirtilen bir değişken, `WithEvents` değişkenin ait olduğu türün, değişkenin oluşturulduğu olay kümesini işlediğini onaylar. Değişkene bir değer atandığında, bildirim tarafından oluşturulan özellik `WithEvents` mevcut olay işleyicisinin kancalarını kaldırır ve yöntemi aracılığıyla yeni olay işleyicisini takar `Add` .  
  
 **Hata kimliği:** BC30594  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Olay işleyicinizi bildirin `Shared` .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Shared](../modifiers/shared.md)
- [WithEvents](../modifiers/withevents.md)
