---
title: 'Nasıl yapılır: Daraltma ve gizleme (Visual Basic) kod bölümlerini'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic, code collapsing
- Visual Basic, code hiding
- Visual Basic code, collapsing and hiding
ms.assetid: b770e8f5-e07d-491a-ab4b-a977980f9ba2
ms.openlocfilehash: bbce0e4a2427843ed9d9d51b25684db8c54ba69a
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56980132"
---
# <a name="how-to-collapse-and-hide-sections-of-code-visual-basic"></a>Nasıl yapılır: Daraltma ve gizleme (Visual Basic) kod bölümlerini
`#Region` Yönergesi daraltma ve gizleme Visual Basic dosyalarında kod bölümlerini olanak sağlar. `#Region` Yönergesi Visual Studio Kod Düzenleyicisi'ni kullanırken genişletebileceğiniz kodu veya daralt bloğunu belirtmenize olanak sağlar. Kod seçmeli olarak gizleyebilme yeteneği dosyalarınızı daha yönetilebilir ve okunması kolay hale getirir. Daha fazla bilgi için [anahat](/visualstudio/ide/outlining).  
  
 `#Region` kod bloğu semantiği gibi destek yönergeleri `#If...#End If`. Bu, bir blok içinde başlar ve diğerinde anlamına gelir; Başlangıç ve bitiş aynı blok içinde olması gerekir. `#Region` yönergeleri içindeki işlevleri desteklenmez.  
  
### <a name="to-collapse-and-hide-a-section-of-code"></a>Daralt ve kodun bir bölümünü gizlemek için  
  
-   Arasında kod bölümünün yerleştirin `#Region` ve `#End Region` ifadeleri, aşağıdaki örnekte olduğu gibi:  
  
     [!code-vb[VbVbalrConditionalComp#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#6)]  
  
     `#Region` Blok kullanılan bir kod dosyasında birden çok kez; bu nedenle, kullanıcılar kendi blokları yordamlar ve sırasıyla daratılmadan sınıfları tanımlayabilir. `#Region` Bloklar da iç içe geçirilemez birbirine `#Region` engeller.  
  
    > [!NOTE]
    >  Kod gizleme Eylemi'ni engellemez ve etkilemez `#If...#End If` deyimleri.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Koşullu Derleme](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [#Region Yönergesi](../../../visual-basic/language-reference/directives/region-directive.md)
- [#If...Then...#Else Yönergesi](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [Anahat Oluşturma](/visualstudio/ide/outlining)
