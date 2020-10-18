---
title: Paylaşılan WithEvents değişkenlerinin olayları paylaşılmayan yöntemler tarafından işlenemez
ms.date: 07/20/2015
f1_keywords:
- bc30594
- vbc30594
helpviewer_keywords:
- BC30594
ms.assetid: 5b9fceb4-ab11-41bb-ad3b-6f1a9da8ae7e
ms.openlocfilehash: 02039b81251e59a951a0fe37ec2c9534b458b6a5
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161926"
---
# <a name="bc30594-events-of-shared-withevents-variables-cannot-be-handled-by-non-shared-methods"></a>BC30594: paylaşılan WithEvents değişkenlerinin olayları paylaşılmayan yöntemler tarafından işlenemez

Değiştiriciyle belirtilen bir değişken `Shared` paylaşılan bir değişkendir. Paylaşılan değişken tam olarak bir depolama konumunu tanımlar. Değiştirici ile belirtilen bir değişken, `WithEvents` değişkenin ait olduğu türün, değişkenin oluşturulduğu olay kümesini işlediğini onaylar. Değişkene bir değer atandığında, bildirim tarafından oluşturulan özellik `WithEvents` mevcut olay işleyicisinin kancalarını kaldırır ve yöntemi aracılığıyla yeni olay işleyicisini takar `Add` .

 **Hata kimliği:** BC30594

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- Olay işleyicinizi bildirin `Shared` .

## <a name="see-also"></a>Ayrıca bkz.

- [Shared](../modifiers/shared.md)
- [WithEvents](../modifiers/withevents.md)
