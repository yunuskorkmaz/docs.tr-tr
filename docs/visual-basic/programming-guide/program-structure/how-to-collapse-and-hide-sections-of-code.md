---
title: 'Nasıl yapılır: Kodun Bölümlerini Daraltma ve Gizleme'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic, code collapsing
- Visual Basic, code hiding
- Visual Basic code, collapsing and hiding
ms.assetid: b770e8f5-e07d-491a-ab4b-a977980f9ba2
ms.openlocfilehash: e7aacdc3f41199127b00d276b382ec4a5f258da0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347403"
---
# <a name="how-to-collapse-and-hide-sections-of-code-visual-basic"></a>Nasıl yapılır: Kodun Bölümlerini Daraltma ve Gizleme (Visual Basic)

`#Region` yönergesi, Visual Basic dosyalardaki kodun bölümlerini daraltmanıza ve gizlemenize olanak sağlar. `#Region` yönergesi, Visual Studio Code düzenleyicisini kullanırken genişletebileceğiniz veya daraltabileceğiniz bir kod bloğu belirtmenize olanak tanır. Kodu seçici olarak gizleyebilme, dosyalarınızı daha yönetilebilir ve okumayı daha kolay hale getirir. Daha fazla bilgi için bkz. [anahat oluşturma](/visualstudio/ide/outlining).

`#Region` yönergeler, `#If...#End If`gibi kod bloğu semantiğini destekler. Bu, bir blokta başlayamayacağı ve başka bir blokta bitemeyeceği anlamına gelir; başlangıç ve bitiş aynı blokta olmalıdır. işlevler içinde `#Region` yönergeleri desteklenmez.

## <a name="to-collapse-and-hide-a-section-of-code"></a>Kodun bir bölümünü daraltmak ve gizlemek için

Aşağıdaki örnekte olduğu gibi `#Region` ve `#End Region` deyimleri arasına kod bölümünü yerleştirin:

[!code-vb[VbVbalrConditionalComp#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#6)]

`#Region` bloğu bir kod dosyasında birden çok kez kullanılabilir; Bu nedenle, kullanıcılar, sırayla daraltılabilen kendi yordam ve sınıf bloklarını tanımlayabilir. `#Region` blokları, diğer `#Region` blokları içinde de iç içe olabilir.

> [!NOTE]
> Kodun gizlenmesi, derlenmemesini engellemez ve `#If...#End If` deyimlerini etkilemez.

## <a name="see-also"></a>Ayrıca bkz.

- [Koşullu Derleme](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [#Region Yönergesi](../../../visual-basic/language-reference/directives/region-directive.md)
- [#If...Then...#Else Yönergesi](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [Anahat Oluşturma](/visualstudio/ide/outlining)
