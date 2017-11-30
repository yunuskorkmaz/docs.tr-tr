---
title: Shadows (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bb767c372cc05d61d569227af8eef0dc3c67489b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
  
 [Class deyimi](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Const deyimi](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [Declare deyimi](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Delegate deyimi](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Dim deyimi](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Enum deyimi](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [Event deyimi](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Function deyimi](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Interface deyimi](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Property deyimi](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Structure deyimi](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Sub deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Paylaşılan](../../../visual-basic/language-reference/modifiers/shared.md)  
 [Statik](../../../visual-basic/language-reference/modifiers/static.md)  
 [Özel](../../../visual-basic/language-reference/modifiers/private.md)  
 [Me, My, MyBase ve MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [Devralma temelleri](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
 [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
 [Aşırı yüklemeler](../../../visual-basic/language-reference/modifiers/overloads.md)  
 [Geçersiz kılınabilir](../../../visual-basic/language-reference/modifiers/overridable.md)  
 [Geçersiz kılmaları](../../../visual-basic/language-reference/modifiers/overrides.md)  
 [Visual Basic'de gölgeleme](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
