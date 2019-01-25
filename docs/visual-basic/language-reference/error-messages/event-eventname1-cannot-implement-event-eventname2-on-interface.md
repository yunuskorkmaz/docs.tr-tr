---
title: Olay &#39; &lt;eventname1&gt; &#39; olayını uygulayamaz &#39; &lt;eventname2&gt; &#39; arabirimde &#39; &lt;arabirimi&gt; &#39; nedeni Temsilci türleri &#39; &lt;delegate1&gt; &#39; ve &#39; &lt;delegate2&gt; &#39; eşleşmiyor
ms.date: 07/20/2015
f1_keywords:
- vbc31423
- bc31423
helpviewer_keywords:
- BC31423
ms.assetid: 2e754b66-5836-48ff-9697-b9c0d7085f18
ms.openlocfilehash: 024e260f12d3497d64f26e59521f016ad439ebb6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54638221"
---
# <a name="event-39lteventname1gt39-cannot-implement-event-39lteventname2gt39-on-interface-39ltinterfacegt39-because-their-delegate-types-39ltdelegate1gt39-and-39ltdelegate2gt39-do-not-match"></a>Olay &#39; &lt;eventname1&gt; &#39; olayını uygulayamaz &#39; &lt;eventname2&gt; &#39; arabirimde &#39; &lt;arabirimi&gt; &#39; nedeni Temsilci türleri &#39; &lt;delegate1&gt; &#39; ve &#39; &lt;delegate2&gt; &#39; eşleşmiyor
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
