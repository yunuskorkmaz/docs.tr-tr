---
title: '&#39;Alma&#39; erişimci özelliğin &#39; &lt;propertyname&gt; &#39; erişilebilir değil'
ms.date: 07/20/2015
f1_keywords:
- vbc31103
- bc31103
helpviewer_keywords:
- BC31103
ms.assetid: 3c346c32-7669-4b04-841d-7a9df9cb703e
ms.openlocfilehash: 10b7168ac40ca7c7d696cd63cd823454f404bb94
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54582220"
---
# <a name="39get39-accessor-of-property-39ltpropertynamegt39-is-not-accessible"></a>&#39;Alma&#39; erişimci özelliğin &#39; &lt;propertyname&gt; &#39; erişilebilir değil
Özelliğin erişimi olmadığında bir özelliğin değerini almak bir deyim çalışır `Get` yordamı.  
  
 Varsa [alma deyimi](../../../visual-basic/language-reference/statements/get-statement.md) ile daha kısıtlayıcı bir erişim düzeyi daha işaretlenmiş kendi [Property deyimi](../../../visual-basic/language-reference/statements/property-statement.md), aşağıdaki durumlarda özellik değerini okuma girişimi başarısız olabilir:  
  
-   `Get` Deyimi işaretlenmiş [özel](../../../visual-basic/language-reference/modifiers/private.md) ve çağrıldığı koda bir sınıf veya yapı özelliği tanımlanır dışında.  
  
-   `Get` Deyimi işaretlenmiş [korumalı](../../../visual-basic/language-reference/modifiers/protected.md) ve çağıran kod değil, sınıf veya yapı özelliği tanımlanır, ya da türetilen bir sınıfta değil.  
  
-   `Get` Deyimi işaretlenmiş [arkadaş](../../../visual-basic/language-reference/modifiers/friend.md) ve çağıran kod özelliği tanımlanır derlemede değil.  
  
 **Hata Kimliği:** BC31103  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Özellik tanımlama kaynak kodu denetim varsa bildirmeyi göz önünde bulundurun `Get` yordamla aynı erişim düzeyi özelliği olarak.  
  
-   Özellik tanımlama kaynak kodu denetim sahibi olmadığınız ya da kısıtlamanız gerekir `Get` yordamı erişim düzeyi özelliği kendisini deneyin birden fazla özellik değeri daha iyi erişimi olan bir bölge kodu okuyan deyim taşımak özellik.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Özellik Yordamları](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
- [Nasıl yapılır: Bir özelliği karışık erişim düzeyleriyle bildirme](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
