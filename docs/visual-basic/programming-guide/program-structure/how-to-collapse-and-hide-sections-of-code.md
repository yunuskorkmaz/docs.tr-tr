---
title: 'Nasıl yapılır: Kodun Bölümlerini Daraltma ve Gizleme (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic, code collapsing
- Visual Basic, code hiding
- Visual Basic code, collapsing and hiding
ms.assetid: b770e8f5-e07d-491a-ab4b-a977980f9ba2
ms.openlocfilehash: f6c272b7ac016258d99873512cb789bba6739727
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-collapse-and-hide-sections-of-code-visual-basic"></a>Nasıl yapılır: Kodun Bölümlerini Daraltma ve Gizleme (Visual Basic)
`#Region` Yönergesi daraltma ve Visual Basic dosyaları kodda bölümlerini gizleme olanak sağlar. `#Region` Yönergesi Visual Studio Kod Düzenleyicisi'ni kullanırken, genişletebilirsiniz kodu veya daralt bloğunu belirtmenize olanak sağlar. Seçime bağlı olarak kod gizleme olanağı dosyalarınızı daha yönetilebilir ve okuması daha kolay hale getirir. Daha fazla bilgi için bkz: [anahat](/visualstudio/ide/outlining).  
  
 `#Region` yönergeleri kod bloğu semantiği gibi destek `#If...#End If`. Bu, tek bir blok olarak başlar ve başka bir programda bitiş anlamına gelir; Başlangıç ve bitiş aynı bloğunda olması gerekir. `#Region` yönergeleri içinde işlevleri desteklenmez.  
  
### <a name="to-collapse-and-hide-a-section-of-code"></a>Daraltma ve kod bir bölümünü gizlemek için  
  
-   Kod arasında bölümünü yerleştirin `#Region` ve `#End Region` aşağıdaki örnekteki gibi deyimleri:  
  
     [!code-vb[VbVbalrConditionalComp#6](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/how-to-collapse-and-hide-sections-of-code_1.vb)]  
  
     `#Region` Blok kullanılan kod dosyasında birden çok kez; bu nedenle, kullanıcılar kendi bloklarını yordamları ve sırasıyla daraltılabilen sınıflar tanımlayabilir. `#Region` blokları de iç içe geçirilemez diğer içinde `#Region` engeller.  
  
    > [!NOTE]
    >  Kod gizleme derlenmiş gelen engellemez ve etkilemez `#If...#End If` deyimleri.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Koşullu Derleme](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 [#Region Yönergesi](../../../visual-basic/language-reference/directives/region-directive.md)  
 [#If...Then...#Else Yönergesi](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [Anahat Oluşturma](/visualstudio/ide/outlining)
