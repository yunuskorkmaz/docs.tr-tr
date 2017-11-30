---
title: "&#39; Al &#39; erişimci özelliği &#39; &lt;propertyname&gt;&#39; erişilebilir değil"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31103
- bc31103
helpviewer_keywords: BC31103
ms.assetid: 3c346c32-7669-4b04-841d-7a9df9cb703e
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 167e040570af1fc78ce48f5e930e54981ba909ae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="39get39-accessor-of-property-39ltpropertynamegt39-is-not-accessible"></a>&#39; Al &#39; erişimci özelliği &#39; &lt;propertyname&gt;&#39; erişilebilir değil
Bir deyim özelliğin erişimi olmadığında bir özelliğin değerini almaya çalışır `Get` yordamı.  
  
 Varsa [alma deyimi](../../../visual-basic/language-reference/statements/get-statement.md) daha kısıtlayıcı bir erişimle daha düzeyi işaretlenmiş kendi [Property deyimi](../../../visual-basic/language-reference/statements/property-statement.md), aşağıdaki durumlarda özellik değerini okuma girişimi başarısız olabilir:  
  
-   `Get` Deyimi işaretlenmiş [özel](../../../visual-basic/language-reference/modifiers/private.md) ve arama sınıf veya yapı özelliği tanımlanır dışında kodudur.  
  
-   `Get` Deyimi işaretlenmiş [korumalı](../../../visual-basic/language-reference/modifiers/protected.md) ve çağıran kodun sınıf veya özellik tanımlanır yapı içinde değil veya türetilmiş bir sınıf içinde değil.  
  
-   `Get` Deyimi işaretlenmiş [arkadaş](../../../visual-basic/language-reference/modifiers/friend.md) ve çağrıyı yapan kod özelliği tanımlanır aynı bütünleştirilmiş kodda değil.  
  
 **Hata Kimliği:** BC31103  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Denetim özellik tanımlama kaynak kodu varsa, bildirme göz önünde bulundurun `Get` özelliği olarak aynı erişim düzeyini yordamı.  
  
-   Özellik tanımlama kaynak kodu denetimi yok ya da kısıtlamanız gerekir `Get` yordamı erişim düzeyine özelliği kendisini deneyin birden çok daha iyi erişimi olan bir bölge kodu için özellik değeri okuyan deyimi taşımak özellik.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özellik yordamları](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)  
 [Nasıl yapılır: bir özelliği karışık erişim düzeyleriyle bildirme](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
