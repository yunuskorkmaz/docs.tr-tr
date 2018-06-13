---
title: '&#39;Alma&#39; özelliği erişimcisi &#39; &lt;propertyname&gt; &#39; erişilebilir değil'
ms.date: 07/20/2015
f1_keywords:
- vbc31103
- bc31103
helpviewer_keywords:
- BC31103
ms.assetid: 3c346c32-7669-4b04-841d-7a9df9cb703e
ms.openlocfilehash: 0972c0909f8b07aa1c6700ec32d1a1ca55d00cc1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590211"
---
# <a name="39get39-accessor-of-property-39ltpropertynamegt39-is-not-accessible"></a>&#39;Alma&#39; özelliği erişimcisi &#39; &lt;propertyname&gt; &#39; erişilebilir değil
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
 [Özellik Yordamları](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)  
 [Nasıl yapılır: Bir Özelliği Karışık Erişim Düzeyleriyle Bildirme](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
