---
description: 'Hakkında daha fazla bilgi edinin: BC30594: paylaşılan WithEvents değişkenlerinin olayları paylaşılmayan yöntemler tarafından işlenemez'
title: Paylaşılan WithEvents değişkenlerinin olayları paylaşılmayan yöntemler tarafından işlenemez
ms.date: 07/20/2015
f1_keywords:
- bc30594
- vbc30594
helpviewer_keywords:
- BC30594
ms.assetid: 5b9fceb4-ab11-41bb-ad3b-6f1a9da8ae7e
ms.openlocfilehash: f9e8bf6e0d365c4ee747deb6be0e809904d87117
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796424"
---
# <a name="bc30594-events-of-shared-withevents-variables-cannot-be-handled-by-non-shared-methods"></a>BC30594: paylaşılan WithEvents değişkenlerinin olayları paylaşılmayan yöntemler tarafından işlenemez

Değiştiriciyle belirtilen bir değişken `Shared` paylaşılan bir değişkendir. Paylaşılan değişken tam olarak bir depolama konumunu tanımlar. Değiştirici ile belirtilen bir değişken, `WithEvents` değişkenin ait olduğu türün, değişkenin oluşturulduğu olay kümesini işlediğini onaylar. Değişkene bir değer atandığında, bildirim tarafından oluşturulan özellik `WithEvents` mevcut olay işleyicisinin kancalarını kaldırır ve yöntemi aracılığıyla yeni olay işleyicisini takar `Add` .

 **Hata kimliği:** BC30594

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- Olay işleyicinizi bildirin `Shared` .

## <a name="see-also"></a>Ayrıca bkz.

- [Paylaşılan](../modifiers/shared.md)
- [WithEvents](../modifiers/withevents.md)
