---
title: 'Nasıl yapılır: Kodun Bölümlerini Daraltma ve Gizleme'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic, code collapsing
- Visual Basic, code hiding
- Visual Basic code, collapsing and hiding
ms.assetid: b770e8f5-e07d-491a-ab4b-a977980f9ba2
ms.openlocfilehash: c11affe9c4dd4251ba8ff4b87029d314970b5fcb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404855"
---
# <a name="how-to-collapse-and-hide-sections-of-code-visual-basic"></a>Nasıl yapılır: Kodun Bölümlerini Daraltma ve Gizleme (Visual Basic)

`#Region`Yönergesi Visual Basic dosyalarındaki kodun bölümlerini daraltmanıza ve gizlemenizi sağlar. `#Region`Yönergesi, Visual Studio Code düzenleyicisini kullanırken genişletebileceğiniz veya daraltabileceğiniz bir kod bloğu belirtmenize olanak tanır. Kodu seçici olarak gizleyebilme, dosyalarınızı daha yönetilebilir ve okumayı daha kolay hale getirir. Daha fazla bilgi için bkz. [anahat oluşturma](/visualstudio/ide/outlining).

`#Region`yönergeleri gibi kod bloğu semantiğini destekler `#If...#End If` . Bu, bir blokta başlayamayacağı ve başka bir blokta bitemeyeceği anlamına gelir; başlangıç ve bitiş aynı blokta olmalıdır. `#Region`işlevler içinde yönergeler desteklenmez.

## <a name="to-collapse-and-hide-a-section-of-code"></a>Kodun bir bölümünü daraltmak ve gizlemek için

`#Region`Aşağıdaki örnekte olduğu gibi, kod bölümünü ve `#End Region` deyimleri arasına yerleştirin:

[!code-vb[VbVbalrConditionalComp#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#6)]

`#Region`Blok, bir kod dosyasında birden çok kez kullanılabilir; Bu nedenle, kullanıcılar, daraltılması için daraltılabilen kendi yordam ve sınıf bloklarını tanımlayabilir. `#Region`bloklar Ayrıca diğer blokların içinde de yer alabilir `#Region` .

> [!NOTE]
> Kodu gizleme, derleme yapılmasını engellemez ve `#If...#End If` deyimlerini etkilemez.

## <a name="see-also"></a>Ayrıca bkz.

- [Koşullu Derleme](conditional-compilation.md)
- [#Region yönergesi](../../language-reference/directives/region-directive.md)
- [#If... Sonra... #Else yönergeler](../../language-reference/directives/if-then-else-directives.md)
- [Anahat Oluşturma](/visualstudio/ide/outlining)
