---
title: Olay &#39; &lt;eventname1&gt; &#39; olay uygulayamaz &#39; &lt;eventname2&gt; &#39; arabirimde &#39; &lt;arabirimi&gt; &#39; çünkü kendi temsilci türleri &#39; &lt;delegate1&gt; &#39; ve &#39; &lt;delegate2&gt; &#39; eşleşmiyor
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31423
- bc31423
helpviewer_keywords:
- BC31423
ms.assetid: 2e754b66-5836-48ff-9697-b9c0d7085f18
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 41f5984458eb17db04f20b292a0d80783093dcb4
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="event-39lteventname1gt39-cannot-implement-event-39lteventname2gt39-on-interface-39ltinterfacegt39-because-their-delegate-types-39ltdelegate1gt39-and-39ltdelegate2gt39-do-not-match"></a>Olay &#39; &lt;eventname1&gt; &#39; olay uygulayamaz &#39; &lt;eventname2&gt; &#39; arabirimde &#39; &lt;arabirimi&gt; &#39; çünkü kendi temsilci türleri &#39; &lt;delegate1&gt; &#39; ve &#39; &lt;delegate2&gt; &#39; eşleşmiyor
Olay temsilci türü olay arabiriminde temsilci türü eşleşmediği için Visual Basic olaya uygulanamıyor. Bu hata, bir arabirim, birden çok olayı tanımlayın ve bunları aynı olay ile birlikte uygulama girişimi ortaya çıkabilir. Bir olay iki uygulayabilir veya yalnızca tüm olayları uygulanırsa, daha fazla olay kullanılarak bildirilen `As` sözdizimi ve aynı temsilci türü belirtin.  
  
 **Hata Kimliği:** BC31423  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Olayları ayrı ayrı uygulayın.  
  
     —veya—  
  
-   Arabirimi kullanarak olayları tanımlayan `As` sözdizimi ve aynı temsilci türü belirtin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Event Deyimi](../../../visual-basic/language-reference/statements/event-statement.md)  
 [Delegate Deyimi](../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [Olaylar](../../../visual-basic/programming-guide/language-features/events/index.md)
