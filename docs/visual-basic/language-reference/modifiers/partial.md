---
title: "Kısmi (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Partial
- partial
helpviewer_keywords:
- structures [Visual Basic], partial
- classes [Visual Basic]
- partial, types [Visual Basic]
- partial, structures
- partial, classes [Visual Basic]
- classes [Visual Basic], partial
- Partial keyword [Visual Basic]
- type promotion
ms.assetid: 7adaef80-f435-46e1-970a-269fff63b448
caps.latest.revision: "36"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5129ef7737b1b07317d47f8d18e9aceb668bf05a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="partial-visual-basic"></a>Kısmi (Visual Basic)
Tür bildirimi kısmi tanım türü olduğunu gösterir.  
  
 Kullanarak birkaç bildirimler arasında bir tür tanımını bölebilirsiniz `Partial` anahtar sözcüğü. İstediğiniz sayıda farklı kaynak dosyalar istediğiniz sayıda kısmi bildirimleri kullanabilirsiniz. Ancak, tüm bildirimler aynı bütünleştirilmiş kodda ve aynı ad olmalıdır.  
  
> [!NOTE]
>  Visual Basic destekler *kısmi yöntemler*, hangi genellikle uygulanır kısmi sınıflar. Daha fazla bilgi için bkz: [kısmi yöntemler](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md) ve [Sub deyimi](../../../visual-basic/language-reference/statements/sub-statement.md).  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
[ <attrlist> ] [ accessmodifier ] [ Shadows ] [ MustInherit | NotInheritable ] _  
Partial { Class | Structure | Interface | Module } name [ (Of typelist) ]  
    [ Inherits classname ]  
    [ Implements interfacenames ]  
    [ variabledeclarations ]  
    [ proceduredeclarations ]  
{ End Class | End Structure }  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`attrlist`|İsteğe bağlı. Bu türü için geçerli öznitelikler listesi. İçine almalısınız [öznitelik listesi](../../../visual-basic/language-reference/statements/attribute-list.md) açılı ayraç (`< >`).|  
|`accessmodifier`|İsteğe bağlı. Bu tür hangi kod erişip belirtir. Bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`Shadows`|İsteğe bağlı. Bkz: [gölgeleri](../../../visual-basic/language-reference/modifiers/shadows.md).|  
|`MustInherit`|İsteğe bağlı. Bkz: [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).|  
|`NotInheritable`|İsteğe bağlı. Bkz: [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md).|  
|`name`|Gerekli. Bu tür adı. Tüm diğer kısmi bildirimlerinde aynı türde tanımlanan adıyla eşleşmelidir.|  
|`Of`|İsteğe bağlı. Bu genel bir tür olduğunu belirtir. Bkz: [Visual Basic'de genel türler](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).|  
|`typelist`|Kullanırsanız, gerekli [,](../../../visual-basic/language-reference/statements/of-clause.md). Bkz: [yazın listesi](../../../visual-basic/language-reference/statements/type-list.md).|  
|`Inherits`|İsteğe bağlı. Bkz: [Inherits deyimi](../../../visual-basic/language-reference/statements/inherits-statement.md).|  
|`classname`|Kullanırsanız, gerekli `Inherits`. Sınıf veya bu sınıf türetilen arabirim adı.|  
|`Implements`|İsteğe bağlı. Bkz: [uygulayan deyimi](../../../visual-basic/language-reference/statements/implements-statement.md).|  
|`interfacenames`|Kullanırsanız, gerekli `Implements`. Bu tür uygulayan arabirimleri adları.|  
|`variabledeclarations`|İsteğe bağlı. Ek değişkenleri ve tür için olaylar declare deyimlerini.|  
|`proceduredeclarations`|İsteğe bağlı. Bildirme ve türü için ek yordamlar tanımlama deyimleri.|  
|`End Class`veya`End Structure`|Bu kısmi sona `Class` veya `Structure` tanımı.|  
  
## <a name="remarks"></a>Açıklamalar  
 Visual Basic parçalı sınıf tanımları oluşturulan kod kullanıcı tarafından yazılan kodu ayrı kaynak dosyalarında ayırmak için kullanır. Örneğin, **Windows Form Tasarımcısı** denetimleri için kısmi sınıflar gibi tanımlar <xref:System.Windows.Forms.Form>. Bu denetimler oluşturulan kodda değiştirmemeniz gerekir.  
  
 Sınıfı, yapısı, arabirim ve değiştirici kullanım ve devralma için olanlar gibi modülü oluşturma için tüm kuralları kısmi türü oluştururken uygulayın.  
  
## <a name="best-practices"></a>En İyi Yöntemler  
  
-   Normal koşullar altında tek bir türü geliştirme iki veya daha fazla bildirimler arasında bölmek değil. Bu nedenle, çoğu durumda, gerekmeyen `Partial` anahtar sözcüğü.  
  
-   Okunabilirlik için bir türün kısmi her bildirimi içermelidir `Partial` anahtar sözcüğü. Derleyici anahtar sözcüğü atlamak en çok bir kısmi bildirimi sağlar; iki veya daha fazla atlarsanız, derleyici bir hata bildirir.  
  
## <a name="behavior"></a>Davranış  
  
-   **Bildirimleri birleşimi.** Derleyici türü tüm kısmi bildirimlerinde birleşimi değerlendirir. Her değiştiricisi her kısmi tanımından tüm türü için geçerlidir ve her kısmi tanımından her bir üyenin tüm türü kullanılabilir.  
  
-   **Tür promosyonu modüllerinde kısmi türleri için izin verilmiyor.** Kısmi bir tanımı içinde bir modül türü tür yükseltme otomatik olarak engellenmediğinden ise. Böyle bir durumda, kısmi tanımları kümesini beklenmeyen sonuçlara ve hatta derleyici hataları neden olabilir. Daha fazla bilgi için bkz: [tür yükseltme](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).  
  
     Yalnızca tam yollarına aynı zaman derleyici kısmi tanımları birleştirir.  
  
 `Partial` Anahtar sözcüğü bu bağlamlarında kullanılabilir:  
  
 [Class deyimi](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Structure deyimi](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek sınıfının tanımını böler `sampleClass` iki bildirimleri her biri farklı bir tanımlar `Sub` yordamı.  
  
 [!code-vb[VbVbalrKeywords#3](../../../visual-basic/language-reference/codesnippet/VisualBasic/partial_1.vb)]  
  
 Önceki örnekte iki kısmi tanımları, aynı kaynak dosyasında veya iki farklı kaynak dosyalar olabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Class deyimi](../../../visual-basic/language-reference/statements/class-statement.md)  
 [Structure deyimi](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [Tür promosyonu](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)  
 [Gölgeleri](../../../visual-basic/language-reference/modifiers/shadows.md)  
 [Visual Basic'de genel türler](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Kısmi yöntemler](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
