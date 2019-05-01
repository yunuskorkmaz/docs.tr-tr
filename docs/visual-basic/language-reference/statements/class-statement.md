---
title: Class Deyimi (Visual Basic)
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
ms.openlocfilehash: 68401571645d77a41b827c13b3cfc3674076e218
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945047"
---
# <a name="class-statement-visual-basic"></a>Class Deyimi (Visual Basic)
Bir sınıfın adını bildirir ve değişkenleri, özellikleri, olayları ve sınıfı oluşturan yordamların tanımını tanıtır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
|`attributelist`|İsteğe bağlı. Bkz: [öznitelik listesi](../../../visual-basic/language-reference/statements/attribute-list.md).|  
|`accessmodifier`|İsteğe bağlı. Aşağıdakilerden biri olabilir:<br /><br /> -   [Genel](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [Korumalı](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [arkadaş](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [Özel](../../../visual-basic/language-reference/modifiers/private.md)<br />-   [Korumalı Friend](../../language-reference/modifiers/protected-friend.md)<br />- [Özel korumalı](../../language-reference/modifiers/private-protected.md)<br/><br/> Bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`Shadows`|İsteğe bağlı. Bkz: [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).|  
|`MustInherit`|İsteğe bağlı. Bkz: [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).|  
|`NotInheritable`|İsteğe bağlı. Bkz: [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md).|  
|`Partial`|İsteğe bağlı. Kısmi bir sınıf tanımlaması gösterir. Bkz: [kısmi](../../../visual-basic/language-reference/modifiers/partial.md).|  
|`name`|Gerekli. Bu sınıfın adı. Bkz: [bildirilen öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`Of`|İsteğe bağlı. Bu genel bir sınıf olduğunu belirtir.|  
|`typelist`|İfadesini kullanıyorsanız gereklidir [,](../../../visual-basic/language-reference/statements/of-clause.md) anahtar sözcüğü. Bu sınıf için tür parametreleri listesi. Bkz: [türü listesinde](../../../visual-basic/language-reference/statements/type-list.md).|  
|`Inherits`|İsteğe bağlı. Bu sınıf başka bir sınıfın üyelerini devralır gösterir. Bkz: [Inherits deyimi](../../../visual-basic/language-reference/statements/inherits-statement.md).|  
|`classname`|İfadesini kullanıyorsanız gereklidir `Inherits` deyimi. Bu sınıfın türetildiği sınıfın adı.|  
|`Implements`|İsteğe bağlı. Bu sınıf, bir veya daha fazla arabirimin üyelerini uyguladığını belirtir. Bkz: [uygulayan deyimi](../../../visual-basic/language-reference/statements/implements-statement.md).|  
|`interfacenames`|İfadesini kullanıyorsanız gereklidir `Implements` deyimi. Bu sınıfın uyguladığı arayüzlerin adları.|  
|`statements`|İsteğe bağlı. Bu sınıfın üyeleri tanımlayan deyimler.|  
|`End Class`|Gerekli. Sonlandırır `Class` tanımı.|  
  
## <a name="remarks"></a>Açıklamalar  
 A `Class` deyimi yeni bir veri türü tanımlar. A *sınıfı* nesne yönelimli programlama (OOP) temel bir yapı taşıdır. Daha fazla bilgi için [nesneler ve sınıflar](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).  
  
 Kullanabileceğiniz `Class` yalnızca düzeyinde ad alanında veya modülde. Başka bir deyişle *bildirim içeriğinin* bir sınıf kaynak dosyası, ad alanı, sınıf, yapı, modül veya arabirimi olması gerekir ve bir yordam veya blok olamayacağı için. Daha fazla bilgi için [bildirim bağlamları ve varsayılan erişim düzeyleri](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Bir sınıfın her örneği, tüm diğer örneklerden bağımsız bir ömrü vardır. Bu yaşam tarafından oluşturulduğunda başlar bir [New işleci](../../../visual-basic/language-reference/operators/new-operator.md) yan tümcesi veya bir işlev gibi <xref:Microsoft.VisualBasic.Interaction.CreateObject%2A>. Örneğine işaret eden tüm değişkenleri olarak ayarlanmış kestiğinde [hiçbir şey](../../../visual-basic/language-reference/nothing.md) veya diğer sınıfların örneklerini.  
  
 Sınıflar için varsayılan [arkadaş](../../../visual-basic/language-reference/modifiers/friend.md) erişim. Erişim değiştiricileri ile kullanıcıların erişim düzeylerini ayarlayabilirsiniz. Daha fazla bilgi için [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="rules"></a>Kurallar  
  
- **İç içe geçme.** İçindeki başka bir sınıf tanımlayabilir. Dış sınıfa *sınıfını içeren*, ve iç sınıfa bir *iç içe sınıf*.  
  
- **Devralma.** Sınıf kullanıyorsa [devralan deyimi](../../../visual-basic/language-reference/statements/inherits-statement.md), yalnızca bir temel sınıf veya arabirim belirtebilirsiniz. Birden fazla öğesinden bir sınıf devralınamaz.  
  
     Bir sınıf daha kısıtlayıcı bir erişim düzeyine sahip başka bir sınıfı devralamaz. Örneğin, bir `Public` sınıfı devralamaz bir `Friend` sınıfı.  
  
     Bir sınıf içinde iç içe geçmiş bir sınıfı devralamaz.  
  
- **Uygulama.** Sınıf kullanıyorsa [Implements deyimi](../../../visual-basic/language-reference/statements/implements-statement.md), belirttiğiniz her arabirim tarafından tanımlanan her üyeyi uygulamalısınız `interfacenames`. Bu konuda bir özel bir temel sınıf üyesinin reimplementation ' dir. Daha fazla bilgi için bkz: "Reimplementation" [uygular](../../../visual-basic/language-reference/statements/implements-clause.md).  
  
- **Varsayılan özellik.** Bir sınıf, en fazla bir özellik olarak belirtebilirsiniz, *varsayılan özellik*. Daha fazla bilgi için [varsayılan](../../../visual-basic/language-reference/modifiers/default.md).  
  
## <a name="behavior"></a>Davranış  
  
- **Erişim düzeyi.** Bir sınıf her bir üyeyi kendi erişim düzeyiyle bildirebilirsiniz. Sınıf üyeleri için varsayılan değer [genel](../../../visual-basic/language-reference/modifiers/public.md) erişim, değişkenler ve sabitler, dışında varsayılan [özel](../../../visual-basic/language-reference/modifiers/private.md) erişim. Bir sınıf daha üyelerinin birden sınırlı erişimi sınıf erişim düzeyi önceliklidir.  
  
- **Kapsam.** Kendi içeren ad alanı, sınıf, yapı veya modül kapsamdadır kullanılan bir sınıftır.  
  
     Her sınıf üyesi kapsamını tüm sınıftır.  
  
     **Yaşam süresi.** Visual Basic statik sınıfların desteklemez. Statik sınıf işlevsel denk bir modül tarafından sağlanabilir. Daha fazla bilgi için [Module deyimi](../../../visual-basic/language-reference/statements/module-statement.md).  
  
     Sınıf üyelerinin ömürleri nasıl ve nerede beyan edildiklerine bağlıdır bağlı olarak var. Daha fazla bilgi için [Visual Basic'de ömür](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md).  
  
- **Nitelik.** Sınıf dışındaki kod, bir üyenin adını söz konusu sınıfın adıyla nitelemeniz gerekir.  
  
     İç içe geçmiş bir sınıf içinde kod programlama öğesine nitelenmemiş bir başvuru yaparsa, Visual Basic öğe için ilk kez ardından sınıfın kapsayan sınıf içinde iç içe geçmiş sınıf içinde vb. en dıştaki içeren öğede arar.  
  
## <a name="classes-and-modules"></a>Sınıflar ve modüller  
 Bu öğeleri birçok benzerlikler, ancak bazı önemli farklar da mevcuttur.  
  
- **Terimler.** Visual Basic'in önceki sürümlerindeki tanımak modülleri iki tür: *sınıf modülleri* (.cls dosyaları) ve *Standart modüller* (.bas dosyaları). Bu sürümdeki çağırır *sınıfları* ve *modülleri*sırasıyla.  
  
- **Paylaşılan üyeler.** Bir sınıfın üyesi bir paylaşılan olup veya örnek üye denetleyebilirsiniz.  
  
- **Nesne yönü.** Nesne yönelimli sınıflardır, ancak modüller değildir. Bir veya birden fazla örneğini bir sınıf oluşturabilirsiniz. Daha fazla bilgi için [nesneler ve sınıflar](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte bir `Class` bir sınıf ve birkaç üye tanımlama deyimini.  
  
 [!code-vb[VbVbalrStatements#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#62)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nesneler ve Sınıflar](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [Yapılar ve Sınıflar](../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
- [Interface Deyimi](../../../visual-basic/language-reference/statements/interface-statement.md)
- [Module Deyimi](../../../visual-basic/language-reference/statements/module-statement.md)
- [Property Deyimi](../../../visual-basic/language-reference/statements/property-statement.md)
- [Nesne ömrü: Nesnelerin nasıl oluşturulduğunu ve yok](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
- [Visual Basic'de genel türler](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Nasıl yapılır: Genel Bir Sınıf Kullanma](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
