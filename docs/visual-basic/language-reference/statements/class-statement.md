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
ms.openlocfilehash: 3b64597fcd7453c20ed295fe263eeaa8783b20ae
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866037"
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
|`attributelist`|İsteğe bağlı. Bkz. [öznitelik listesi](attribute-list.md).|  
|`accessmodifier`|İsteğe bağlı. Aşağıdakilerden biri olabilir:<br /><br /> -   [Geneldir](../modifiers/public.md)<br />-   [Korunamadı](../modifiers/protected.md)<br />-   [Dost](../modifiers/friend.md)<br />-   [Özelleştirme](../modifiers/private.md)<br />-   [Korumalı arkadaş](../modifiers/protected-friend.md)<br />- [Özel korumalı](../modifiers/private-protected.md)<br/><br/> [Visual Basic erişim düzeylerine](../../programming-guide/language-features/declared-elements/access-levels.md)bakın.|  
|`Shadows`|İsteğe bağlı. Bkz. [gölgeler](../modifiers/shadows.md).|  
|`MustInherit`|İsteğe bağlı. Bkz. [MustInherit](../modifiers/mustinherit.md).|  
|`NotInheritable`|İsteğe bağlı. [NotInheritable](../modifiers/notinheritable.md)öğesine bakın.|  
|`Partial`|İsteğe bağlı. Sınıfın kısmi bir tanımını gösterir. [Kısmi](../modifiers/partial.md)gör.|  
|`name`|Gereklidir. Bu sınıfın adı. Bkz. [tanımlanmış öğe adları](../../programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`Of`|İsteğe bağlı. Bunun genel bir sınıf olduğunu belirtir.|  
|`typelist`|[Anahtar sözcüğünü](of-clause.md) kullanıyorsanız gereklidir. Bu sınıf için tür parametrelerinin listesi. Bkz. [tür listesi](type-list.md).|  
|`Inherits`|İsteğe bağlı. Bu sınıfın başka bir sınıfın üyelerini devraldığını gösterir. Bkz. [Inherits açıklaması](inherits-statement.md).|  
|`classname`|İfadesini kullanıyorsanız gereklidir `Inherits` . Bu sınıfın türetildiği sınıfın adı.|  
|`Implements`|İsteğe bağlı. Bu sınıfın bir veya daha fazla arabirimin üyelerini uyguladığını gösterir. Bkz. [Implements açıklaması](implements-statement.md).|  
|`interfacenames`|İfadesini kullanıyorsanız gereklidir `Implements` . Bu sınıfın uyguladığı arabirimlerin adları.|  
|`statements`|İsteğe bağlı. Bu sınıfın üyelerini tanımlayan deyimler.|  
|`End Class`|Gereklidir. Tanımı sonlandırır `Class` .|  
  
## <a name="remarks"></a>Açıklamalar  

 Bir `Class` ifade yeni bir veri türünü tanımlar. *Sınıf* , nesne odaklı programlama (OOP) temel yapı taşıdır. Daha fazla bilgi için bkz. [nesneler ve sınıflar](../../programming-guide/language-features/objects-and-classes/index.md).  
  
 `Class`Yalnızca ad alanı veya modül düzeyinde kullanabilirsiniz. Diğer bir deyişle, bir sınıf için *Bildirim bağlamı* bir kaynak dosya, ad alanı, sınıf, yapı, modül veya arabirim olmalıdır ve bir yordam veya blok olamaz. Daha fazla bilgi için bkz. [bildirim bağlamları ve varsayılan erişim düzeyleri](declaration-contexts-and-default-access-levels.md).  
  
 Bir sınıfın her örneği, diğer tüm örneklerden bağımsız olarak yaşam süresine sahiptir. Bu ömür, [Yeni bir işleç](../operators/new-operator.md) yan tümcesi veya gibi bir işlev tarafından oluşturulduğunda başlar <xref:Microsoft.VisualBasic.Interaction.CreateObject%2A> . Örneğe işaret eden tüm değişkenler [Nothing](../nothing.md) veya diğer sınıfların örneklerine ayarlandığında sonlanır.  
  
 Sınıfların varsayılan olarak [arkadaş](../modifiers/friend.md) erişimi. Erişim değiştiricilerini kullanarak erişim düzeylerini ayarlayabilirsiniz. Daha fazla bilgi için bkz. [Visual Basic erişim düzeyleri](../../programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="rules"></a>Kurallar  
  
- **İç içe geçme.** Bir sınıfı diğeri içinde tanımlayabilirsiniz. Dış sınıfa *kapsayan sınıf*denir ve iç sınıfa *iç içe sınıf*denir.  
  
- **Devralmayı.** Sınıf [Inherits ifadesini](inherits-statement.md)kullanıyorsa yalnızca bir temel sınıf veya arabirim belirtebilirsiniz. Bir sınıf birden fazla öğeden devralınabilir.  
  
     Bir sınıf daha kısıtlayıcı erişim düzeyine sahip başka bir sınıftan devralınabilir. Örneğin, bir `Public` sınıf sınıfından devralınabilir `Friend` .  
  
     Bir sınıf, içinde iç içe geçmiş bir sınıftan devralınabilir.  
  
- **Paylaşır.** Sınıf [Implements ifadesini](implements-statement.md)kullanıyorsa, içinde belirttiğiniz her arabirim tarafından tanımlanan her üyeyi uygulamanız gerekir `interfacenames` . Bunun bir özel durumu, bir temel sınıf üyesinin yeniden uygulamasıdır. Daha fazla bilgi için, bkz. [uygulamadaki](implements-clause.md)"yeniden uygulama".  
  
- **Varsayılan özellik.** Bir sınıf, en az bir özelliği *varsayılan özelliği*olarak belirtebilir. Daha fazla bilgi için bkz. [Default](../modifiers/default.md).  
  
## <a name="behavior"></a>Davranış  
  
- **Erişim düzeyi.** Bir sınıf içinde, her üyeyi kendi erişim düzeyiyle bildirebilirsiniz. Sınıf üyeleri varsayılan olarak [özel](../modifiers/private.md) erişim için varsayılan olarak, değişkenler ve sabitler hariç [genel](../modifiers/public.md) erişime açıktır. Bir sınıf, üyelerinden birine göre daha kısıtlı erişime sahip olduğunda, sınıf erişim düzeyi önceliklidir.  
  
- **Kapsam.** Bir sınıf, kapsayan ad alanı, sınıf, yapı veya modül genelinde kapsamdadır.  
  
     Her sınıf üyesinin kapsamı tüm sınıftır.  
  
     **Süre.** Visual Basic statik sınıfları desteklemez. Statik bir sınıfın işlevsel eşdeğeri bir modül tarafından sağlanır. Daha fazla bilgi için bkz. [module deyimleri](module-statement.md).  
  
     Sınıf üyeleri, nasıl ve nerede bildiridiklerine bağlı olarak yaşam süreleri vardır. Daha fazla bilgi için [Visual Basic ömrü](../../programming-guide/language-features/declared-elements/lifetime.md)' ne bakın.  
  
- **Yeter.** Bir sınıf dışındaki kodun bir üyenin adını bu sınıfın adı ile nitelemeniz gerekir.  
  
     İç içe yerleştirilmiş bir sınıf içindeki kod, bir programlama öğesine nitelenmemiş bir başvuru yaparsa, Visual Basic iç içe geçmiş sınıfta, ardından kapsayan sınıfında ve bu öğeyi en dıştaki içeren en dıştaki öğe için bir kez arar.  
  
## <a name="classes-and-modules"></a>Sınıflar ve modüller  

 Bu öğelerin birçok benzerlikleri vardır ancak bazı önemli farklılıklar da vardır.  
  
- **Terimler.** Önceki Visual Basic sürümleri iki tür modül tanır: *sınıf modülleri* (. CLS dosyaları) ve *Standart modüller* (. bas dosyaları). Geçerli sürüm, sırasıyla bu *sınıfları* ve *modülleri*çağırır.  
  
- **Paylaşılan Üyeler.** Bir sınıfın bir üyesinin paylaşılan bir veya örnek üye olup olmadığını kontrol edebilirsiniz.  
  
- **Nesne yönü.** Sınıflar nesne yönelimlidir, ancak modüller değildir. Bir sınıfın bir veya daha fazla örneğini oluşturabilirsiniz. Daha fazla bilgi için bkz. [nesneler ve sınıflar](../../programming-guide/language-features/objects-and-classes/index.md).  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek bir `Class` sınıfı ve birkaç üyeyi tanımlamak için bir ifade kullanır.  
  
 [!code-vb[VbVbalrStatements#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#62)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nesneler ve sınıflar](../../programming-guide/language-features/objects-and-classes/index.md)
- [Yapılar ve Sınıflar](../../programming-guide/language-features/data-types/structures-and-classes.md)
- [Interface Deyimi](interface-statement.md)
- [Module Deyimi](module-statement.md)
- [Property Deyimi](property-statement.md)
- [Nesne Ömrü: Nesneleri Oluşturma ve Yok Etme](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
- [Visual Basic genel türler](../../programming-guide/language-features/data-types/generic-types.md)
- [Nasıl yapılır: Genel Bir Sınıf Kullanma](../../programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
