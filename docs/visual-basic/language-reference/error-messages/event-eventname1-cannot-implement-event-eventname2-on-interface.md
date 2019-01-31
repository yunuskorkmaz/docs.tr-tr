---
title: "'<eventname1>' ile '<eventname2>' temsilci türleri eşleşmediğinden '<interface>' olayı '<delegate1>' arabiriminde '<delegate2>' olayını uygulayamaz."
ms.date: 07/20/2015
f1_keywords:
- vbc31423
- bc31423
helpviewer_keywords:
- BC31423
ms.assetid: 2e754b66-5836-48ff-9697-b9c0d7085f18
ms.openlocfilehash: 3ec3e7bb2f28bf8c4dd38bc71e11193456860021
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55272857"
---
# <a name="event-eventname1-cannot-implement-event-eventname2-on-interface-interface-because-their-delegate-types-delegate1-and-delegate2-do-not-match"></a>Olay '\<eventname1 >' olayını uygulayamaz '\<eventname2 >' arabiriminde '\<arabirimi >' için temsilci türleri\<delegate1 >' ve '\<delegate2 >' eşleşmiyor
Visual Basic olaya uygulanamıyor arabirimdeki olayın temsilci türü olay temsilci türü eşleşmiyor. Bu hata, bir arabirimde birden çok olayı tanımlayın ve bunları aynı olay ile birlikte uygulama girişimi oluşabilir. Bir olay iki uygulayabilir veya yalnızca tüm olayları uygulanırsa, daha fazla olay kullanılarak bildirilen `As` söz dizimi ve aynı temsilci türünü belirtin.  
  
 **Hata Kimliği:** BC31423  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Olayları ayrı ayrı uygular.  
  
     —veya—  
  
-   Arabirimi kullanarak olayları tanımlamanız `As` söz dizimi ve aynı temsilci türünü belirtin.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Event Deyimi](../../../visual-basic/language-reference/statements/event-statement.md)
- [Delegate Deyimi](../../../visual-basic/language-reference/statements/delegate-statement.md)
- [Olaylar](../../../visual-basic/programming-guide/language-features/events/index.md)
