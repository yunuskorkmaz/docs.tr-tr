---
title: Kısmi (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 8f8e7e992ce312f7f7bf2c9dbad4d14fbb095de1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54690715"
---
# <a name="partial-visual-basic"></a>Kısmi (Visual Basic)
Bir tür bildirimi türü kısmi tanımı olduğunu gösterir.  
  
 Kullanarak, çeşitli bildirimler arasında bir tür tanımı ayırabilirsiniz `Partial` anahtar sözcüğü. İstediğiniz sayıda farklı kaynak dosyaları istediğiniz sayıda kısmi bildirimleri kullanabilirsiniz. Ancak, tüm bildirimler aynı derleme ve aynı ad olmalıdır.  
  
> [!NOTE]
>  Visual Basic destekler *kısmi yöntemler*, hangi genellikle uygulanır kısmi sınıflar. Daha fazla bilgi için [kısmi yöntemler](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md) ve [Sub deyimi](../../../visual-basic/language-reference/statements/sub-statement.md).  
  
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
|`attrlist`|İsteğe bağlı. Bu türüne uygulanan özniteliklerin listesi. İçine almalısınız [öznitelik listesi](../../../visual-basic/language-reference/statements/attribute-list.md) açılı ayraçlar içinde (`< >`).|  
|`accessmodifier`|İsteğe bağlı. Bu tür kod erişip belirtir. Bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`Shadows`|İsteğe bağlı. Bkz: [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).|  
|`MustInherit`|İsteğe bağlı. Bkz: [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).|  
|`NotInheritable`|İsteğe bağlı. Bkz: [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md).|  
|`name`|Gerekli. Bu türün adı. Tanımlanan tüm diğer kısmi bildirimlerinde aynı tür adıyla eşleşmelidir.|  
|`Of`|İsteğe bağlı. Bu genel bir tür olduğunu belirtir. Bkz: [Visual Basic'de genel türler](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).|  
|`typelist`|İfadesini kullanıyorsanız gereklidir [,](../../../visual-basic/language-reference/statements/of-clause.md). Bkz: [türü listesinde](../../../visual-basic/language-reference/statements/type-list.md).|  
|`Inherits`|İsteğe bağlı. Bkz: [Inherits deyimi](../../../visual-basic/language-reference/statements/inherits-statement.md).|  
|`classname`|İfadesini kullanıyorsanız gereklidir `Inherits`. Sınıf veya bu sınıfın türetildiği arabirimin adı.|  
|`Implements`|İsteğe bağlı. Bkz: [uygulayan deyimi](../../../visual-basic/language-reference/statements/implements-statement.md).|  
|`interfacenames`|İfadesini kullanıyorsanız gereklidir `Implements`. Bu türün uyguladığı arayüzlerin adları.|  
|`variabledeclarations`|İsteğe bağlı. Bir ek değişkeni ve tür için olaylar bildirmek deyimler.|  
|`proceduredeclarations`|İsteğe bağlı. Bildirme ve türü için ek yordamlar tanımlama deyimleri.|  
|`End Class` veya `End Structure`|Bu kısmi sona erer `Class` veya `Structure` tanımı.|  
  
## <a name="remarks"></a>Açıklamalar  
 Visual Basic, kullanıcı tarafından yazılan kodu ayrı kaynak dosyalarında oluşturulan kod ayırmak için kısmi sınıf tanımları kullanır. Örneğin, **Windows Form Tasarımcısı** denetimleri için kısmi sınıflar gibi tanımlar <xref:System.Windows.Forms.Form>. Bu denetimler oluşturulan kodda değiştirmeniz gerekir.  
  
 Kısmi bir tür oluştururken, sınıf, yapı, arabirimi ve değiştiricisinin kullanımı ve devralma için olanlar gibi modülü oluşturma için tüm kuralları geçerlidir.  
  
## <a name="best-practices"></a>En İyi Yöntemler  
  
-   Normal koşullar altında tek bir türde geliştirme arasında iki veya daha fazla bildirimleri bölmeniz gerekir değil. Bu nedenle, çoğu durumda gerekmeyen `Partial` anahtar sözcüğü.  
  
-   Okunabilirlik için her bir kısmi bildirimi bir tür içermelidir `Partial` anahtar sözcüğü. Derleyicinin anahtar sözcüğü atlamak en fazla bir kısmi bildirimi sağlar; iki veya daha fazla Bunu atlarsanız, derleyici bir hata bildirir.  
  
## <a name="behavior"></a>Davranış  
  
-   **Bildirimleri birleşimi.** Derleyicinin tür tüm kısmi bildirimleri birleşimi değerlendirir. Kısmi her tanımındaki her değiştiricisi türün tamamı için geçerlidir ve her kısmi tanımındaki her üye, türün tamamı için kullanılabilir.  
  
-   **Tür promosyonu modülleri kısmi türler için izin verilmiyor.** Kısmi bir tanımını modül içinde ise, o türün tür yükseltme otomatik olarak engellenmediğinden olur. Böyle bir durumda, kısmi tanımları kümesini beklenmeyen sonuçlar ve hatta derleyici hataları neden olabilir. Daha fazla bilgi için [tür promosyonu](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).  
  
     Yalnızca tam yollarının aynı olduğunda derleyici kısmi tanımları birleştirir.  
  
 `Partial` Anahtar sözcüğü bu bağlamda kullanılabilir:  
  
 [Class Deyimi](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Structure Deyimi](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, sınıf tanımını böler `sampleClass` alanına iki bildirimler, her biri farklı bir tanımlar `Sub` yordamı.  
  
 [!code-vb[VbVbalrKeywords#3](../../../visual-basic/language-reference/codesnippet/VisualBasic/partial_1.vb)]  
  
 İki kısmi tanım önceki örnekte, aynı kaynak dosyada veya iki farklı kaynak dosyalarında olabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Class Deyimi](../../../visual-basic/language-reference/statements/class-statement.md)
- [Structure Deyimi](../../../visual-basic/language-reference/statements/structure-statement.md)
- [Tür Yükseltme](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)
- [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)
- [Visual Basic'de genel türler](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Kısmi Yöntemler](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
