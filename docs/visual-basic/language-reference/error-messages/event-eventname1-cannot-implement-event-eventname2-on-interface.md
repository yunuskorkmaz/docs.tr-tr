---
title: "Olay &#39; &lt;eventname1&gt;&#39; olay &#39; uygulayamaz&lt; eventname2&gt;&#39; arabirimi &#39;&lt; Arabirim&gt;&#39; çünkü bunların temsilci türleri &#39;&lt; delegate1&gt;&#39; ve &#39;&lt; delegate2&gt;&#39; eşleşmiyor"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31423
- bc31423
helpviewer_keywords: BC31423
ms.assetid: 2e754b66-5836-48ff-9697-b9c0d7085f18
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b0fcbbf8a6e23270e4dcbf9d813c773e1522a92a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="event-39lteventname1gt39-cannot-implement-event-39lteventname2gt39-on-interface-39ltinterfacegt39-because-their-delegate-types-39ltdelegate1gt39-and-39ltdelegate2gt39-do-not-match"></a>Olay &#39; &lt;eventname1&gt;&#39; olay &#39; uygulayamaz&lt; eventname2&gt;&#39; arabirimi &#39;&lt; Arabirim&gt;&#39; çünkü bunların temsilci türleri &#39;&lt; delegate1&gt;&#39; ve &#39;&lt; delegate2&gt;&#39; eşleşmiyor
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]Olay temsilci türü olay arabiriminde temsilci türü eşleşmediği için bir olay uygulayamaz. Bu hata, bir arabirim, birden çok olayı tanımlayın ve bunları aynı olay ile birlikte uygulama girişimi ortaya çıkabilir. Bir olay iki uygulayabilir veya yalnızca tüm olayları uygulanırsa, daha fazla olay kullanılarak bildirilen `As` sözdizimi ve aynı temsilci türü belirtin.  
  
 **Hata Kimliği:** BC31423  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Olayları ayrı ayrı uygulayın.  
  
     —veya—  
  
-   Arabirimi kullanarak olayları tanımlayan `As` sözdizimi ve aynı temsilci türü belirtin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Event deyimi](../../../visual-basic/language-reference/statements/event-statement.md)  
 [Delegate deyimi](../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [Olayları](../../../visual-basic/programming-guide/language-features/events/index.md)
