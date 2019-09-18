---
title: 'Nasıl yapılır: Kodun bölümlerini daraltma ve gizleme (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic, code collapsing
- Visual Basic, code hiding
- Visual Basic code, collapsing and hiding
ms.assetid: b770e8f5-e07d-491a-ab4b-a977980f9ba2
ms.openlocfilehash: 4f11982cc0aa7654c1e456fb15d918a68bc4791b
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71054114"
---
# <a name="how-to-collapse-and-hide-sections-of-code-visual-basic"></a>Nasıl yapılır: Kodun bölümlerini daraltma ve gizleme (Visual Basic)

`#Region` Yönergesi Visual Basic dosyalarındaki kodun bölümlerini daraltmanıza ve gizlemenizi sağlar. `#Region` Yönergesi, Visual Studio Code düzenleyicisini kullanırken genişletebileceğiniz veya daraltabileceğiniz bir kod bloğu belirtmenize olanak tanır. Kodu seçici olarak gizleyebilme, dosyalarınızı daha yönetilebilir ve okumayı daha kolay hale getirir. Daha fazla bilgi için bkz. [anahat oluşturma](/visualstudio/ide/outlining).

`#Region`yönergeleri gibi `#If...#End If`kod bloğu semantiğini destekler. Bu, bir blokta başlayamayacağı ve başka bir blokta bitemeyeceği anlamına gelir; başlangıç ve bitiş aynı blokta olmalıdır. `#Region`işlevler içinde yönergeler desteklenmez.

## <a name="to-collapse-and-hide-a-section-of-code"></a>Kodun bir bölümünü daraltmak ve gizlemek için

Aşağıdaki örnekte olduğu gibi, kod bölümünü `#Region` ve `#End Region` deyimleri arasına yerleştirin:

[!code-vb[VbVbalrConditionalComp#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#6)]

`#Region` Blok, bir kod dosyasında birden çok kez kullanılabilir; Bu nedenle, kullanıcılar, daraltılması için daraltılabilen kendi yordam ve sınıf bloklarını tanımlayabilir. `#Region`bloklar Ayrıca diğer `#Region` blokların içinde de yer alabilir.

> [!NOTE]
> Kodu gizleme, derleme yapılmasını engellemez ve deyimlerini etkilemez `#If...#End If` .

## <a name="see-also"></a>Ayrıca bkz.

- [Koşullu Derleme](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [#Region Yönergesi](../../../visual-basic/language-reference/directives/region-directive.md)
- [#If...Then...#Else Yönergesi](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [Anahat Oluşturma](/visualstudio/ide/outlining)
