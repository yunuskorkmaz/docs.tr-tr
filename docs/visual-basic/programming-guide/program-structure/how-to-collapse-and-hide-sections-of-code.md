---
title: 'Nasıl yapılır: Kodun Bölümlerini Daraltma ve Gizleme (Visual Basic)'
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic, code collapsing
- Visual Basic, code hiding
- Visual Basic code, collapsing and hiding
ms.assetid: b770e8f5-e07d-491a-ab4b-a977980f9ba2
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4497c9586182cca9e2be97dc39e5ccb242725d25
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
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
