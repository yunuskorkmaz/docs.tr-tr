---
title: Structure ekstresi (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.Structure
- Structure
helpviewer_keywords:
- user-defined types [Visual Basic], Structure statement
- compound data types [Visual Basic]
- Structure keyword [Visual Basic]
- Structure statement [Visual Basic]
- UDT (user-defined types)
- types [Visual Basic], user-defined
ms.assetid: 9bd1deea-2a89-4cdc-812c-6dcbb947c391
ms.openlocfilehash: cec04880dd7cadc627ab090a45468dbad83c8d84
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583206"
---
# <a name="structure-statement"></a>Structure Yapısı
Bir yapının adını bildirir ve yapının içerdiği değişkenlerin, özelliklerin, olayların ve yordamların tanımını tanıtır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
[ <attributelist> ] [ accessmodifier ] [ Shadows ] [ Partial ] _  
Structure name [ ( Of typelist ) ]  
    [ Implements interfacenames ]  
    [ datamemberdeclarations ]  
    [ methodmemberdeclarations ]  
End Structure  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`attributelist`|İsteğe bağlı. Bkz. [öznitelik listesi](../../../visual-basic/language-reference/statements/attribute-list.md).|  
|`accessmodifier`|İsteğe bağlı. Aşağıdakilerden biri olabilir:<br /><br /> -   [ortak](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [korumalı](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [arkadaş](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [özel](../../../visual-basic/language-reference/modifiers/private.md)<br />- [korumalı arkadaş](../../language-reference/modifiers/protected-friend.md)<br/>- [özel korumalı](../../language-reference/modifiers/private-protected.md) <br /><br /> [Visual Basic erişim düzeylerine](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)bakın.|  
|`Shadows`|İsteğe bağlı. Bkz. [gölgeler](../../../visual-basic/language-reference/modifiers/shadows.md).|  
|`Partial`|İsteğe bağlı. Yapının kısmi bir tanımını gösterir. [Kısmi](../../../visual-basic/language-reference/modifiers/partial.md)gör.|  
|`name`|Gerekli. Bu yapının adı. Bkz. [tanımlanmış öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`Of`|İsteğe bağlı. Bunun genel bir yapı olduğunu belirtir.|  
|`typelist`|[Anahtar sözcüğünü](../../../visual-basic/language-reference/statements/of-clause.md) kullanıyorsanız gereklidir. Bu yapının tür parametrelerinin listesi. Bkz. [tür listesi](../../../visual-basic/language-reference/statements/type-list.md).|  
|`Implements`|İsteğe bağlı. Bu yapının bir veya daha fazla arabirimin üyelerini uyguladığını gösterir. Bkz. [Implements açıklaması](../../../visual-basic/language-reference/statements/implements-statement.md).|  
|`interfacenames`|@No__t_0 ifadesini kullanıyorsanız gereklidir. Bu yapının uyguladığı arabirimlerin adları.|  
|`datamemberdeclarations`|Gerekli. Yapının *veri üyelerini* bildiren sıfır veya daha fazla `Const`, `Dim`, `Enum` veya `Event` deyimleri.|  
|`methodmemberdeclarations`|İsteğe bağlı. @No__t_0, `Operator`, `Property` veya `Sub` yordamlarının, yapının *Yöntem üyeleri* olarak işlev gösteren sıfır veya daha fazla bildirimi.|  
|`End Structure`|Gerekli. @No__t_0 tanımını sonlandırır.|  
  
## <a name="remarks"></a>Açıklamalar  
 @No__t_0 deyiminiz, özelleştirebileceğiniz bir bileşik değer türü tanımlar. *Yapı* , önceki Visual Basic sürümlerindeki Kullanıcı tanımlı tür (udt) genelleştirmesidir. Daha fazla bilgi için bkz. [yapılar](../../../visual-basic/programming-guide/language-features/data-types/structures.md).  
  
 Yapılar sınıflarla aynı özelliklerin birçoğunu destekler. Örneğin, yapıların özellikleri ve yordamları olabilir, arabirimler uygulayabilir ve parametreli oluşturuculara sahip olabilirler. Ancak, devralma, bildirimler ve kullanım gibi alanlardaki yapılar ve sınıflar arasında önemli farklılıklar vardır. Ayrıca, sınıflar başvuru türleridir ve yapılardır değer türlerdir. Daha fazla bilgi için bkz. [yapılar ve sınıflar](../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md).  
  
 Yalnızca ad alanı veya modül düzeyinde `Structure` kullanabilirsiniz. Bu, bir yapının *bildirim bağlamının* bir kaynak dosya, ad alanı, sınıf, yapı, modül veya arabirim olması ve bir yordam veya blok olamayacağı anlamına gelir. Daha fazla bilgi için bkz. [bildirim bağlamları ve varsayılan erişim düzeyleri](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Varsayılan yapılar [arkadaş](../../../visual-basic/language-reference/modifiers/friend.md) erişimine sahiptir. Erişim değiştiricilerini kullanarak erişim düzeylerini ayarlayabilirsiniz. Daha fazla bilgi için bkz. [Visual Basic erişim düzeyleri](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="rules"></a>Kurallar  
  
- **İç içe geçme.** Bir yapıyı diğeri içinde tanımlayabilirsiniz. Dış yapıya *kapsayan yapı*denir ve iç yapıya *iç içe yapı*denir. Ancak, iç içe bir yapının üyelerine kapsayan yapı aracılığıyla erişemezsiniz. Bunun yerine, iç içe yapının veri türünün bir değişkenini bildirmeniz gerekir.  
  
- **Üye bildirimi.** Bir yapının her üyesini bildirmeniz gerekir. Bir yapıyla hiçbir şey devraldığı için bir yapı üyesi [korunamıyor](../../../visual-basic/language-reference/modifiers/protected.md) veya `Protected Friend`. Ancak, yapının kendisi `Protected` veya `Protected Friend` olabilir.  
  
     Bir yapıda sıfır veya daha fazla paylaşılmayan değişken ya da paylaşılmayan, özel olmayan olaylar bildirebilirsiniz. Bazıları paylaşılmamış olsa bile yalnızca sabitler, Özellikler ve yordamlar olamaz.  
  
- **Başlatılmasında.** Bir yapının paylaşılmayan veri üyesinin değerini, bildiriminin bir parçası olarak başlatılamaz. Bu tür bir veri üyesini yapıda parametreli bir Oluşturucu aracılığıyla ya da yapının bir örneğini oluşturduktan sonra üyeye bir değer atamanız gerekir.  
  
- **Devralmayı.** Bir yapı, tüm yapıların devraldığı <xref:System.ValueType> dışındaki herhangi bir türden devralınabilir. Özellikle, bir yapı diğerinden devralınabilir.  
  
     @No__t_1 belirtmek için bile, bir yapı tanımında [Inherits ifadesini](../../../visual-basic/language-reference/statements/inherits-statement.md) kullanamazsınız.  
  
- **Paylaşır.** Yapı [Implements ifadesini](../../../visual-basic/language-reference/statements/implements-statement.md)kullanıyorsa, `interfacenames` belirttiğiniz her arabirim tarafından tanımlanan her üyeyi uygulamanız gerekir.  
  
- **Varsayılan özellik.** Bir yapı [varsayılan değiştiricisini kullanarak](../../../visual-basic/language-reference/modifiers/default.md) en çok bir özelliği *varsayılan özelliği*olarak belirtebilir. Daha fazla bilgi için bkz. [Default](../../../visual-basic/language-reference/modifiers/default.md).  
  
## <a name="behavior"></a>Davranış  
  
- **Erişim düzeyi.** Bir yapı içinde, her üyeyi kendi erişim düzeyiyle bildirebilirsiniz. Tüm yapı üyeleri varsayılan olarak [genel](../../../visual-basic/language-reference/modifiers/public.md) erişime sahiptir. Yapının kendisine daha kısıtlı bir erişim düzeyi varsa, erişim değiştiricilerine erişim düzeylerini ayarlasanız bile bu, erişimi otomatik olarak kısıtlar.  
  
- **Kapsam.** Bir yapı, kapsayan ad alanı, sınıf, yapı veya modül genelinde kapsamdadır.  
  
     Her yapı üyesinin kapsamı tüm yapısıdır.  
  
- **Süre.** Bir yapının yaşam süresi yoktur. Bunun yerine, bu yapının her örneğinin diğer tüm örneklerden bağımsız bir yaşam süresi vardır.  
  
     Bir örneğin yaşam süresi, [Yeni bir işleç](../../../visual-basic/language-reference/operators/new-operator.md) yan tümcesi tarafından oluşturulduğunda başlar. Bu, kendisini tutan değişkenin ömrü sona erdiğinde sona erer.  
  
     Bir yapı örneğinin ömrünü genişletemezsiniz. Statik yapı işlevselliğine yaklaşık bir modül tarafından sağlanır. Daha fazla bilgi için bkz. [module deyimleri](../../../visual-basic/language-reference/statements/module-statement.md).  
  
     Yapı üyelerinin yaşam sürelerinin nasıl ve nerede bildirilmesine bağlı olarak yaşam süreleri vardır. Daha fazla bilgi için bkz. [Class deyimindeki](../../../visual-basic/language-reference/statements/class-statement.md)"Lifetime".  
  
- **Yeter.** Bir yapının dışındaki kodun bir üyenin adını bu yapının adıyla nitelemeniz gerekir.  
  
     İç içe yerleştirilmiş bir yapı içindeki kod, bir programlama öğesine nitelenmemiş bir başvuru yaparsa, Visual Basic iç içe yapıdaki öğeyi, ardından kapsayan yapısını ve bu öğeyi en dıştaki içeren en dıştaki öğeyi arar. Daha fazla bilgi için bkz. [bildirilmemiş öğelere başvurular](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
- **Bellek tüketimi.** Tüm bileşik veri türlerinde olduğu gibi, üyelerinin nominal depolama ayırmalarını birlikte ekleyerek bir yapının toplam bellek tüketimini güvenle hesaplayabilirsiniz. Ayrıca, bellekteki depolama sırasının bildirimin sıralamayla aynı olduğunu güvenli bir şekilde varsayamaz. Bir yapının depolama yerleşimini denetetmeniz gerekiyorsa, <xref:System.Runtime.InteropServices.StructLayoutAttribute> özniteliğini `Structure` ifadesine uygulayabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir çalışan için ilgili verilerin bir kümesini tanımlamak üzere `Structure` ifadesini kullanır. Veri öğelerinin duyarlılığını yansıtmak için `Public`, `Friend` ve `Private` üyelerinin kullanımını gösterir. Ayrıca yordamı, özelliği ve olay üyelerini gösterir.  
  
 [!code-vb[VbVbalrStatements#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#57)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Class Deyimi](../../../visual-basic/language-reference/statements/class-statement.md)
- [Interface Deyimi](../../../visual-basic/language-reference/statements/interface-statement.md)
- [Module Deyimi](../../../visual-basic/language-reference/statements/module-statement.md)
- [Dim Deyimi](../../../visual-basic/language-reference/statements/dim-statement.md)
- [Const Deyimi](../../../visual-basic/language-reference/statements/const-statement.md)
- [Enum Deyimi](../../../visual-basic/language-reference/statements/enum-statement.md)
- [Event Deyimi](../../../visual-basic/language-reference/statements/event-statement.md)
- [Operator Deyimi](../../../visual-basic/language-reference/statements/operator-statement.md)
- [Property Deyimi](../../../visual-basic/language-reference/statements/property-statement.md)
- [Yapılar ve Sınıflar](../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
