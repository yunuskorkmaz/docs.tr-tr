---
title: Class Deyimi
ms.date: 05/12/2018
f1_keywords:
- vb.Class
helpviewer_keywords:
- class modules
- Class statement [Visual Basic]
- classes [Visual Basic], fields
- fields [Visual Basic], of classes
- class types [Visual Basic], class statements
- classes [Visual Basic], creating
- classes [Visual Basic], data members
- data members [Visual Basic], of classes
ms.assetid: f2664f38-eb5a-4d4b-a374-1d041521fb6c
ms.openlocfilehash: 3cb276f134e90ce3b3009234eb980d89477e0d09
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354156"
---
# <a name="class-statement-visual-basic"></a>Class Deyimi (Visual Basic)
Bir sınıfın adını bildirir ve sınıfın içerdiği değişkenlerin, özelliklerin, olayların ve yordamların tanımını tanıtır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
[ <attributelist> ] [ accessmodifier ] [ Shadows ] [ MustInherit | NotInheritable ] [ Partial ] _  
Class name [ ( Of typelist ) ]  
    [ Inherits classname ]  
    [ Implements interfacenames ]  
    [ statements ]  
End Class  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`attributelist`|İsteğe bağlı. Bkz. [öznitelik listesi](../../../visual-basic/language-reference/statements/attribute-list.md).|  
|`accessmodifier`|İsteğe bağlı. Aşağıdakilerden biri olabilir:<br /><br /> -   [genel](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [korumalı](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [arkadaş](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [özel](../../../visual-basic/language-reference/modifiers/private.md)<br />-   [korumalı arkadaş](../../language-reference/modifiers/protected-friend.md)<br />- [özel korumalı](../../language-reference/modifiers/private-protected.md)<br/><br/> [Visual Basic erişim düzeylerine](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)bakın.|  
|`Shadows`|İsteğe bağlı. Bkz. [gölgeler](../../../visual-basic/language-reference/modifiers/shadows.md).|  
|`MustInherit`|İsteğe bağlı. Bkz. [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).|  
|`NotInheritable`|İsteğe bağlı. [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)öğesine bakın.|  
|`Partial`|İsteğe bağlı. Sınıfın kısmi bir tanımını gösterir. [Kısmi](../../../visual-basic/language-reference/modifiers/partial.md)gör.|  
|`name`|Gerekli. Bu sınıfın adı. Bkz. [tanımlanmış öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`Of`|İsteğe bağlı. Bunun genel bir sınıf olduğunu belirtir.|  
|`typelist`|[Anahtar sözcüğünü](../../../visual-basic/language-reference/statements/of-clause.md) kullanıyorsanız gereklidir. Bu sınıf için tür parametrelerinin listesi. Bkz. [tür listesi](../../../visual-basic/language-reference/statements/type-list.md).|  
|`Inherits`|İsteğe bağlı. Bu sınıfın başka bir sınıfın üyelerini devraldığını gösterir. Bkz. [Inherits açıklaması](../../../visual-basic/language-reference/statements/inherits-statement.md).|  
|`classname`|`Inherits` ifadesini kullanıyorsanız gereklidir. Bu sınıfın türetildiği sınıfın adı.|  
|`Implements`|İsteğe bağlı. Bu sınıfın bir veya daha fazla arabirimin üyelerini uyguladığını gösterir. Bkz. [Implements açıklaması](../../../visual-basic/language-reference/statements/implements-statement.md).|  
|`interfacenames`|`Implements` ifadesini kullanıyorsanız gereklidir. Bu sınıfın uyguladığı arabirimlerin adları.|  
|`statements`|İsteğe bağlı. Bu sınıfın üyelerini tanımlayan deyimler.|  
|`End Class`|Gerekli. `Class` tanımını sonlandırır.|  
  
## <a name="remarks"></a>Açıklamalar  
 `Class` bir ifade yeni bir veri türünü tanımlar. *Sınıf* , nesne odaklı programlama (OOP) temel yapı taşıdır. Daha fazla bilgi için bkz. [nesneler ve sınıflar](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).  
  
 Yalnızca ad alanı veya modül düzeyinde `Class` kullanabilirsiniz. Diğer bir deyişle, bir sınıf için *Bildirim bağlamı* bir kaynak dosya, ad alanı, sınıf, yapı, modül veya arabirim olmalıdır ve bir yordam veya blok olamaz. Daha fazla bilgi için bkz. [bildirim bağlamları ve varsayılan erişim düzeyleri](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Bir sınıfın her örneği, diğer tüm örneklerden bağımsız olarak yaşam süresine sahiptir. Bu ömür, [Yeni bir işleç](../../../visual-basic/language-reference/operators/new-operator.md) yan tümcesi veya <xref:Microsoft.VisualBasic.Interaction.CreateObject%2A>gibi bir işlev tarafından oluşturulduğunda başlar. Örneğe işaret eden tüm değişkenler [Nothing](../../../visual-basic/language-reference/nothing.md) veya diğer sınıfların örneklerine ayarlandığında sonlanır.  
  
 Sınıfların varsayılan olarak [arkadaş](../../../visual-basic/language-reference/modifiers/friend.md) erişimi. Erişim değiştiricilerini kullanarak erişim düzeylerini ayarlayabilirsiniz. Daha fazla bilgi için bkz. [Visual Basic erişim düzeyleri](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="rules"></a>Kurallar  
  
- **İç içe geçme.** Bir sınıfı diğeri içinde tanımlayabilirsiniz. Dış sınıfa *kapsayan sınıf*denir ve iç sınıfa *iç içe sınıf*denir.  
  
- **Devralmayı.** Sınıf [Inherits ifadesini](../../../visual-basic/language-reference/statements/inherits-statement.md)kullanıyorsa yalnızca bir temel sınıf veya arabirim belirtebilirsiniz. Bir sınıf birden fazla öğeden devralınabilir.  
  
     Bir sınıf daha kısıtlayıcı erişim düzeyine sahip başka bir sınıftan devralınabilir. Örneğin, bir `Public` sınıfı `Friend` sınıfından devralınabilir.  
  
     Bir sınıf, içinde iç içe geçmiş bir sınıftan devralınabilir.  
  
- **Paylaşır.** Sınıf [Implements ifadesini](../../../visual-basic/language-reference/statements/implements-statement.md)kullanıyorsa, `interfacenames`belirttiğiniz her arabirim tarafından tanımlanan her üyeyi uygulamanız gerekir. Bunun bir özel durumu, bir temel sınıf üyesinin yeniden uygulamasıdır. Daha fazla bilgi için, bkz. [uygulamadaki](../../../visual-basic/language-reference/statements/implements-clause.md)"yeniden uygulama".  
  
- **Varsayılan özellik.** Bir sınıf, en az bir özelliği *varsayılan özelliği*olarak belirtebilir. Daha fazla bilgi için bkz. [Default](../../../visual-basic/language-reference/modifiers/default.md).  
  
## <a name="behavior"></a>Davranış  
  
- **Erişim düzeyi.** Bir sınıf içinde, her üyeyi kendi erişim düzeyiyle bildirebilirsiniz. Sınıf üyeleri varsayılan olarak [özel](../../../visual-basic/language-reference/modifiers/private.md) erişim için varsayılan olarak, değişkenler ve sabitler hariç [genel](../../../visual-basic/language-reference/modifiers/public.md) erişime açıktır. Bir sınıf, üyelerinden birine göre daha kısıtlı erişime sahip olduğunda, sınıf erişim düzeyi önceliklidir.  
  
- **Kapsam.** Bir sınıf, kapsayan ad alanı, sınıf, yapı veya modül genelinde kapsamdadır.  
  
     Her sınıf üyesinin kapsamı tüm sınıftır.  
  
     **Süre.** Visual Basic statik sınıfları desteklemez. Statik bir sınıfın işlevsel eşdeğeri bir modül tarafından sağlanır. Daha fazla bilgi için bkz. [module deyimleri](../../../visual-basic/language-reference/statements/module-statement.md).  
  
     Sınıf üyeleri, nasıl ve nerede bildiridiklerine bağlı olarak yaşam süreleri vardır. Daha fazla bilgi için [Visual Basic ömrü](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)' ne bakın.  
  
- **Yeter.** Bir sınıf dışındaki kodun bir üyenin adını bu sınıfın adı ile nitelemeniz gerekir.  
  
     İç içe yerleştirilmiş bir sınıf içindeki kod, bir programlama öğesine nitelenmemiş bir başvuru yaparsa, Visual Basic iç içe geçmiş sınıfta, ardından kapsayan sınıfında ve bu öğeyi en dıştaki içeren en dıştaki öğe için bir kez arar.  
  
## <a name="classes-and-modules"></a>Sınıflar ve modüller  
 Bu öğelerin birçok benzerlikleri vardır ancak bazı önemli farklılıklar da vardır.  
  
- **Terminolojiyi.** Önceki Visual Basic sürümleri iki tür modül tanır: *sınıf modülleri* (. CLS dosyaları) ve *Standart modüller* (. bas dosyaları). Geçerli sürüm, sırasıyla bu *sınıfları* ve *modülleri*çağırır.  
  
- **Paylaşılan Üyeler.** Bir sınıfın bir üyesinin paylaşılan bir veya örnek üye olup olmadığını kontrol edebilirsiniz.  
  
- **Nesne yönü.** Sınıflar nesne yönelimlidir, ancak modüller değildir. Bir sınıfın bir veya daha fazla örneğini oluşturabilirsiniz. Daha fazla bilgi için bkz. [nesneler ve sınıflar](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir sınıfı ve birkaç üyeyi tanımlamak için bir `Class` ifadesini kullanır.  
  
 [!code-vb[VbVbalrStatements#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#62)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nesneler ve Sınıflar](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [Yapılar ve Sınıflar](../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
- [Interface Deyimi](../../../visual-basic/language-reference/statements/interface-statement.md)
- [Module Deyimi](../../../visual-basic/language-reference/statements/module-statement.md)
- [Property Deyimi](../../../visual-basic/language-reference/statements/property-statement.md)
- [Nesne Ömrü: Nesneleri Oluşturma ve Yok Etme](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
- [Visual Basic genel türler](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Nasıl yapılır: Genel Bir Sınıf Kullanma](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
