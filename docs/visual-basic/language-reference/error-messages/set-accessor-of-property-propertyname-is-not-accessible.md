---
title: "&#39; Set &#39; erişimci özelliği &#39; &lt;propertyname&gt;&#39; erişilebilir değil"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31102
- bc31102
helpviewer_keywords:
- BC31102
ms.assetid: 6f7b31b7-3656-4ae1-8851-90f5f4c6950a
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9256a09b719ad3890e1d7c2cc23ffb0d40eec62f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="39set39-accessor-of-property-39ltpropertynamegt39-is-not-accessible"></a>&#39; Set &#39; erişimci özelliği &#39; &lt;propertyname&gt;&#39; erişilebilir değil
Özelliğin erişimi olmadığında bir özelliğin değerini depolamak bir deyim çalışır `Set` yordamı.  
  
 Varsa [Set deyimi](../../../visual-basic/language-reference/statements/set-statement.md) daha kısıtlayıcı bir erişimle daha düzeyi işaretlenmiş kendi [Property deyimi](../../../visual-basic/language-reference/statements/property-statement.md), aşağıdaki durumlarda özellik değerini ayarlama girişimi başarısız olabilir:  
  
-   `Set` Deyimi işaretlenmiş [özel](../../../visual-basic/language-reference/modifiers/private.md) ve arama sınıf veya yapı özelliği tanımlanır dışında kodudur.  
  
-   `Set` Deyimi işaretlenmiş [korumalı](../../../visual-basic/language-reference/modifiers/protected.md) ve çağıran kodun sınıf veya özellik tanımlanır yapı içinde değil veya türetilmiş bir sınıf içinde değil.  
  
-   `Set` Deyimi işaretlenmiş [arkadaş](../../../visual-basic/language-reference/modifiers/friend.md) ve çağrıyı yapan kod özelliği tanımlanır aynı bütünleştirilmiş kodda değil.  
  
 **Hata Kimliği:** BC31102  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Denetim özellik tanımlama kaynak kodu varsa, bildirme göz önünde bulundurun `Set` özelliği olarak aynı erişim düzeyini yordamı.  
  
-   Özellik tanımlama kaynak kodu denetimi yok ya da kısıtlamanız gerekir `Set` yordamı erişim düzeyine özelliği kendisini deneyin birden fazla özellik değeri bir bölgeye daha iyi erişimi olan kod ayarlar deyimi taşımak özellik.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özellik yordamları](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)  
 [Nasıl yapılır: bir özelliği karışık erişim düzeyleriyle bildirme](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
