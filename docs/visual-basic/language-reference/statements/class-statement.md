---
title: Class Deyimi (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Class
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
caps.latest.revision: "29"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: df86ef0eec67d96f2f997dc5dac7ee2357c6362b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="class-statement-visual-basic"></a>Class Deyimi (Visual Basic)
Bir sınıfın adını bildirir ve tanımını değişkenleri, özellikleri, olayları ve sınıfı oluşur yordamları sunar.  
  
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
|`accessmodifier`|İsteğe bağlı. Aşağıdakilerden biri olabilir:<br /><br /> -   [Ortak](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [Korumalı](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Arkadaş](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [Özel](../../../visual-basic/language-reference/modifiers/private.md)<br />-   `Protected Friend`<br /><br /> Bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`Shadows`|İsteğe bağlı. Bkz: [gölgeleri](../../../visual-basic/language-reference/modifiers/shadows.md).|  
|`MustInherit`|İsteğe bağlı. Bkz: [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).|  
|`NotInheritable`|İsteğe bağlı. Bkz: [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md).|  
|`Partial`|İsteğe bağlı. Kısmi bir sınıf tanımını gösterir. Bkz: [kısmi](../../../visual-basic/language-reference/modifiers/partial.md).|  
|`name`|Gerekli. Bu sınıfın adı. Bkz: [bildirilen öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`Of`|İsteğe bağlı. Bu genel bir sınıf olduğunu belirtir.|  
|`typelist`|Kullanırsanız, gerekli [,](../../../visual-basic/language-reference/statements/of-clause.md) anahtar sözcüğü. Bu sınıf için tür parametreleri listesi. Bkz: [yazın listesi](../../../visual-basic/language-reference/statements/type-list.md).|  
|`Inherits`|İsteğe bağlı. Bu sınıf başka bir sınıf üyeleri devralır gösterir. Bkz: [Inherits deyimi](../../../visual-basic/language-reference/statements/inherits-statement.md).|  
|`classname`|Kullanırsanız, gerekli `Inherits` deyimi. Bu sınıf türetilen sınıfın adı.|  
|`Implements`|İsteğe bağlı. Bu sınıf bir veya daha fazla arabirimin üyelerini uyguladığını gösterir. Bkz: [uygulayan deyimi](../../../visual-basic/language-reference/statements/implements-statement.md).|  
|`interfacenames`|Kullanırsanız, gerekli `Implements` deyimi. Bu sınıf uygulayan arabirimleri adları.|  
|`statements`|İsteğe bağlı. Bu sınıf üyeleri tanımlama deyimleri.|  
|`End Class`|Gerekli. Sonlandırır `Class` tanımı.|  
  
## <a name="remarks"></a>Açıklamalar  
 A `Class` deyimi yeni bir veri türü tanımlar. A *sınıfı* nesne odaklı programlama (OOP) temel bir yapı taşıdır. Daha fazla bilgi için bkz: [nesneler ve sınıflar](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).  
  
 Kullanabileceğiniz `Class` yalnızca ad alanı veya düzeyinde modülü. Yani *bildirimi bağlam* bir sınıf bir kaynak dosya, ad alanı, sınıf, yapısı, modül veya arabirimi olmalı ve bir yordam veya blok olamaz. Daha fazla bilgi için bkz: [bildirim bağlamları ve varsayılan erişim düzeyleri](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Her bir sınıf örneği diğer tüm örneklerini bağımsız bir ömrü vardır. Tarafından oluşturulduğunda bu ömrü başlayan bir [New işleci](../../../visual-basic/language-reference/operators/new-operator.md) yan tümcesi veya gibi bir işlev tarafından <xref:Microsoft.VisualBasic.Interaction.CreateObject%2A>. Tüm değişkenleri örneğini işaret ayarlanmış kestiğinde [hiçbir şey](../../../visual-basic/language-reference/nothing.md) veya diğer sınıfların örnekleri.  
  
 Varsayılan olarak sınıfları [arkadaş](../../../visual-basic/language-reference/modifiers/friend.md) erişim. Erişim değiştiricileri ile erişim düzeylerine göre ayarlayabilirsiniz. Daha fazla bilgi için bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="rules"></a>Kurallar  
  
-   **İç içe geçirme.** İçindeki başka bir sınıf tanımlayabilirsiniz. Dış sınıf adlı *sınıfı içeren*, ve iç sınıfı adı verilen bir *iç içe geçmiş sınıf*.  
  
-   **Devralma.** Sınıf kullanıyorsa [Inherits deyimi](../../../visual-basic/language-reference/statements/inherits-statement.md), yalnızca bir temel sınıf veya arabirim belirtebilirsiniz. Bir sınıf birden fazla öğesinden devralınan olamaz.  
  
     Bir sınıf daha kısıtlayıcı erişim düzeyine sahip başka bir sınıftan devralınan olamaz. Örneğin, bir `Public` olamaz sınıf devralma bir `Friend` sınıfı.  
  
     Bir sınıf içinde iç içe bir sınıftan devralınan olamaz.  
  
-   **Uygulaması.** Sınıf kullanıyorsa [Implements deyimi](../../../visual-basic/language-reference/statements/implements-statement.md), belirttiğiniz her arabirim tarafından tanımlanan her üye uygulamalıdır `interfacenames`. Bu konuda bir özel bir temel sınıf üyenin yeniden uygulama ' dir. Daha fazla bilgi için bkz: "yeniden uygulama" [uygulayan](../../../visual-basic/language-reference/statements/implements-clause.md).  
  
-   **Varsayılan özellik.** Bir sınıf en çok bir özellik olarak belirtebilirsiniz, *varsayılan özellik*. Daha fazla bilgi için bkz: [varsayılan](../../../visual-basic/language-reference/modifiers/default.md).  
  
## <a name="behavior"></a>Davranış  
  
-   **Erişim düzeyi.** Bir sınıf her üye kendi erişim düzeyi ile bildirebilir. Sınıf üyeleri için varsayılan değer [ortak](../../../visual-basic/language-reference/modifiers/public.md) erişim, değişkenleri ve sabitleri dışında varsayılan [özel](../../../visual-basic/language-reference/modifiers/private.md) erişim. Bir sınıf daha üyeleri birden sınırlı erişimi sınıf erişim düzeyi önceliklidir.  
  
-   **Kapsamı.** Kendi içeren ad alanı, sınıf, yapı veya modülü boyunca kapsamdaki bir sınıftır.  
  
     Her sınıf üyesi kapsamını tüm bir sınıftır.  
  
     **Yaşam süresi.** Visual Basic statik sınıflar desteklemez. Statik sınıf işlevsel denk bir modül tarafından sağlanır. Daha fazla bilgi için bkz: [Module deyimi](../../../visual-basic/language-reference/statements/module-statement.md).  
  
     Sınıf üyeleri nasıl ve nerede bildirilir bağlı olarak ömürleri vardır. Daha fazla bilgi için bkz: [Visual Basic'de ömür](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md).  
  
-   **Niteliğe.** Kod bir sınıf dışında bir üyenin adını o sınıfın adını nitelemeniz gerekir.  
  
     Kod iç içe bir sınıf içinde bir programlama öğesi nitelenmemiş bir başvuru yaparsa, Visual Basic öğe için önce iç içe geçmiş sınıfında, ardından kapsayan sınıfı, vb. dıştaki içeren öğesine arar.  
  
## <a name="classes-and-modules"></a>Sınıfları ve modülleri  
 Benzer şekilde bu öğelere sahip, ancak de önemli bazı farklar vardır.  
  
-   **Terminolojisi.** Visual Basic önceki sürümlerini tanıması modülleri iki tür: *sınıf modülleri* (.cls dosyaları) ve *Standart modüller* (.bas dosyaları). Bunlar geçerli sürümü çağırır *sınıfları* ve *modülleri*sırasıyla.  
  
-   **Paylaşılan üyeler.** Bir sınıf üyesi paylaşılan olup veya örnek üyesine kontrol edebilirsiniz.  
  
-   **Nesne yönü.** Nesne odaklı sınıfları, ancak modüller değildir. Bir veya daha fazla bir sınıfın örneklerini oluşturabilirsiniz. Daha fazla bilgi için bkz: [nesneler ve sınıflar](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanan bir `Class` deyimi bir sınıf ve birkaç üye tanımlayın.  
  
 [!code-vb[VbVbalrStatements#62](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/class-statement_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nesneler ve sınıflar](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [Yapılar ve sınıflar](../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)  
 [Interface deyimi](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [Module deyimi](../../../visual-basic/language-reference/statements/module-statement.md)  
 [Property deyimi](../../../visual-basic/language-reference/statements/property-statement.md)  
 [Nesne ömrü: Nesneleri oluşturma ve yok etme](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)  
 [Visual Basic'de genel türler](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Nasıl yapılır: genel bir sınıf kullanma](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
