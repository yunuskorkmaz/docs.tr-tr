---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: kodun bölümlerini daraltma ve gizleme (Visual Basic)'
title: 'Nasıl yapılır: Kodun Bölümlerini Daraltma ve Gizleme'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic, code collapsing
- Visual Basic, code hiding
- Visual Basic code, collapsing and hiding
ms.assetid: b770e8f5-e07d-491a-ab4b-a977980f9ba2
ms.openlocfilehash: b93a2190bd6266c6f9fa5cb06eb249ca174c8067
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475974"
---
# <a name="how-to-collapse-and-hide-sections-of-code-visual-basic"></a>Nasıl yapılır: Kodun Bölümlerini Daraltma ve Gizleme (Visual Basic)

`#Region`Yönergesi Visual Basic dosyalarındaki kodun bölümlerini daraltmanıza ve gizlemenizi sağlar. `#Region`Yönergesi, Visual Studio Code düzenleyicisini kullanırken genişletebileceğiniz veya daraltabileceğiniz bir kod bloğu belirtmenize olanak tanır. Kodu seçici olarak gizleyebilme, dosyalarınızı daha yönetilebilir ve okumayı daha kolay hale getirir. Daha fazla bilgi için bkz. [anahat oluşturma](/visualstudio/ide/outlining).

`#Region` yönergeleri gibi kod bloğu semantiğini destekler `#If...#End If` . Bu, bir blokta başlayamayacağı ve başka bir blokta bitemeyeceği anlamına gelir; başlangıç ve bitiş aynı blokta olmalıdır. `#Region` işlevler içinde yönergeler desteklenmez.

## <a name="to-collapse-and-hide-a-section-of-code"></a>Kodun bir bölümünü daraltmak ve gizlemek için

`#Region`Aşağıdaki örnekte olduğu gibi, kod bölümünü ve `#End Region` deyimleri arasına yerleştirin:

[!code-vb[VbVbalrConditionalComp#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#6)]

`#Region`Blok, bir kod dosyasında birden çok kez kullanılabilir; Bu nedenle, kullanıcılar, daraltılması için daraltılabilen kendi yordam ve sınıf bloklarını tanımlayabilir. `#Region` bloklar Ayrıca diğer blokların içinde de yer alabilir `#Region` .

> [!NOTE]
> Kodu gizleme, derleme yapılmasını engellemez ve `#If...#End If` deyimlerini etkilemez.

## <a name="see-also"></a>Ayrıca bkz.

- [Koşullu Derleme](conditional-compilation.md)
- [#Region yönergesi](../../language-reference/directives/region-directive.md)
- [#If... Sonra... #Else yönergeler](../../language-reference/directives/if-then-else-directives.md)
- [Anahat Oluşturma](/visualstudio/ide/outlining)
