---
title: Shadows (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Shadows
- shadows
helpviewer_keywords:
- shadowing
- duplicate names [Visual Basic]
- scope [Visual Basic], shadowing
- Shadows keyword [Visual Basic]
- names [Visual Basic], shadowing
ms.assetid: 6bf687cd-0544-4797-b51b-911125ec57c6
ms.openlocfilehash: 4ca4ec48ee63b71447056a2c5cb68e8948f27ad0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604659"
---
# <a name="shadows-visual-basic"></a>Shadows (Visual Basic)
Bildirilen bir programlama öğesi redeclares ve bir aynı adlı öğesi ya da bir taban sınıf içinde aşırı yüklenmiş öğelerin gizler belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
 Gölgeleme ana amacı (olarak da bilinen olduğu *adıyla gizleme*) sınıf üyeleri tanımını korumak için. Taban sınıf, bir önceden tanımlamış aynı ada sahip bir öğe oluşturan bir değişiklik uygulanabilir. Bu durumda, `Shadows` değiştiricisi zorlar başvuran üyesine çözümlenmesi sınıfınız üzerinden tanımlanmış, yerine yeni bir temel sınıf öğesi için.  
  
 Hem gölgeleme ve geçersiz kılma devralınan bir öğeyi yeniden tanımlamanız, ancak iki yaklaşım arasında önemli farklılıklar vardır. Daha fazla bilgi için bkz: [Visual Basic'de gölgeleme](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).  
  
## <a name="rules"></a>Kurallar  
  
-   **Bildirim bağlamı.** Kullanabileceğiniz `Shadows` yalnızca sınıf düzeyinde. Bu bildirimi bağlamının anlamına gelir bir `Shadows` öğesi bir sınıf olmalıdır ve bir kaynak dosyasını, ad alanı, arabirim, modülü, yapısı veya yordamı olamaz.  
  
     Bir tek bildirimi deyimde yalnızca bir gölgeleme öğesi bildirebilirsiniz.  
  
-   **Birleşik değiştirici.** Belirtemeyeceğiniz `Shadows` ile birlikte `Overloads`, `Overrides`, veya `Static` aynı bildirimi.  
  
-   **Öğe türleri.** Bildirilen öğe herhangi bir tür başka herhangi bir tür ile gölge. Bir özellik veya başka bir özellik veya yordam yordamla gölge, parametreler ve dönüş türü taban sınıf özelliği veya yordam eşleştiğinden gerekmez.  
  
-   **Erişme.** Taban sınıfı gölgeli öğesinde da shadows türetilmiş sınıf içinde normalde gelen kullanılamıyor. Ancak, aşağıdaki maddeler geçerlidir.  
  
    -   Gölgeleme öğesi kendisine başvuran kod erişilebilir durumda değilse, başvuru gölgeli öğesine çözümlenir. Örneğin, varsa bir `Private` öğesi shadows erişim izni yok kod bir temel sınıf öğesi `Private` öğe temel sınıf öğesi yerine erişir.  
  
    -   Bir öğenin gölge, gölgeli öğe temel sınıf türü ile bildirilmedi nesnesi aracılığıyla erişmeye devam edebilirsiniz. Üzerinden de erişebilirsiniz `MyBase`.  
  
 `Shadows` Değiştiricisi bu bağlamlarında kullanılabilir:  
  
 [Class Deyimi](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Const Deyimi](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [Declare Deyimi](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Delegate Deyimi](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Dim Deyimi](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Enum Deyimi](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [Event Deyimi](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Function Deyimi](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Interface Deyimi](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Property Deyimi](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Structure Deyimi](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Shared](../../../visual-basic/language-reference/modifiers/shared.md)  
 [Static](../../../visual-basic/language-reference/modifiers/static.md)  
 [Private](../../../visual-basic/language-reference/modifiers/private.md)  
 [Me, My, MyBase ve MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [Devralma Temelleri](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
 [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
 [Overloads](../../../visual-basic/language-reference/modifiers/overloads.md)  
 [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)  
 [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)  
 [Visual Basic'de gölgeleme](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
