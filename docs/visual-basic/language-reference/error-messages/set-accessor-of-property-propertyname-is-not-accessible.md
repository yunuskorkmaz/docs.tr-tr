---
title: '&#39;Ayarlama&#39; özelliği erişimcisi &#39; &lt;propertyname&gt; &#39; erişilebilir değil'
ms.date: 07/20/2015
f1_keywords:
- vbc31102
- bc31102
helpviewer_keywords:
- BC31102
ms.assetid: 6f7b31b7-3656-4ae1-8851-90f5f4c6950a
ms.openlocfilehash: d047d03755de89d4740482db4845d5db72003ac0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="39set39-accessor-of-property-39ltpropertynamegt39-is-not-accessible"></a>&#39;Ayarlama&#39; özelliği erişimcisi &#39; &lt;propertyname&gt; &#39; erişilebilir değil
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
 [Özellik Yordamları](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)  
 [Nasıl yapılır: Bir Özelliği Karışık Erişim Düzeyleriyle Bildirme](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
