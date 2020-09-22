---
title: "'<eventname1>' ile '<eventname2>' temsilci türleri eşleşmediğinden '<interface>' olayı '<delegate1>' arabiriminde '<delegate2>' olayını uygulayamaz."
ms.date: 07/20/2015
f1_keywords:
- vbc31423
- bc31423
helpviewer_keywords:
- BC31423
ms.assetid: 2e754b66-5836-48ff-9697-b9c0d7085f18
ms.openlocfilehash: b1e0728a4f865b432b142df4ded1efddb376201e
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874325"
---
# <a name="event-eventname1-cannot-implement-event-eventname2-on-interface-interface-because-their-delegate-types-delegate1-and-delegate2-do-not-match"></a>'\<eventname1>' ile '\<eventname2>' temsilci türleri eşleşmediğinden '\<interface>' olayı '\<delegate1>' arabiriminde '\<delegate2>' olayını uygulayamaz.

Olayın temsilci türü arabirimdeki olayın temsilci türüyle eşleşmediğinden Visual Basic bir olay uygulayamaz. Bu hata, bir arabirimde birden çok olay tanımladığınızda ve ardından bunları aynı olayla birlikte uygulamaya çalıştığınızda ortaya çıkabilir. Bir olay, yalnızca tüm uygulanan olaylar `As` söz dizimi kullanılarak bildirilirse ve aynı temsilci türünü belirtirseniz iki veya daha fazla olay uygulayabilir.  
  
 **Hata kimliği:** BC31423  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Olayları ayrı olarak uygulayın.  
  
     —veya—  
  
- Sözdizimini kullanarak arabirimdeki olayları tanımlayın `As` ve aynı temsilci türünü belirtin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Event Deyimi](../statements/event-statement.md)
- [Delegate Deyimi](../statements/delegate-statement.md)
- [Ekinlikler](../../programming-guide/language-features/events/index.md)
