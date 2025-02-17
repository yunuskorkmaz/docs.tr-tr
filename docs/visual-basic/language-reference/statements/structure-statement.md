---
description: 'Daha fazla bilgi edinin: yapı ekstresi'
title: Structure Yapısı
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
ms.openlocfilehash: 338abe359491f02c25bdb33d996fb639f58f8b35
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99741074"
---
# <a name="structure-statement"></a>Structure Yapısı

Bir yapının adını bildirir ve yapının içerdiği değişkenlerin, özelliklerin, olayların ve yordamların tanımını tanıtır.

## <a name="syntax"></a>Syntax

```vb
[ <attributelist> ] [ accessmodifier ] [ Shadows ] [ Partial ] _
Structure name [ ( Of typelist ) ]
    [ Implements interfacenames ]
    [ datamemberdeclarations ]
    [ methodmemberdeclarations ]
End Structure
```

## <a name="parts"></a>Bölümler

|Süre|Tanım|
|---|---|
|`attributelist`|İsteğe bağlı. Bkz. [öznitelik listesi](attribute-list.md).|
|`accessmodifier`|İsteğe bağlı. Aşağıdakilerden biri olabilir:<br /><br /> -   [Geneldir](../modifiers/public.md)<br />-   [Korunamadı](../modifiers/protected.md)<br />-   [Dost](../modifiers/friend.md)<br />-   [Özelleştirme](../modifiers/private.md)<br />- [Korumalı arkadaş](../modifiers/protected-friend.md)<br/>- [Özel korumalı](../modifiers/private-protected.md) <br /><br /> [Visual Basic erişim düzeylerine](../../programming-guide/language-features/declared-elements/access-levels.md)bakın.|
|`Shadows`|İsteğe bağlı. Bkz. [gölgeler](../modifiers/shadows.md).|
|`Partial`|İsteğe bağlı. Yapının kısmi bir tanımını gösterir. [Kısmi](../modifiers/partial.md)gör.|
|`name`|Gereklidir. Bu yapının adı. Bkz. [tanımlanmış öğe adları](../../programming-guide/language-features/declared-elements/declared-element-names.md).|
|`Of`|İsteğe bağlı. Bunun genel bir yapı olduğunu belirtir.|
|`typelist`|[Anahtar sözcüğünü](of-clause.md) kullanıyorsanız gereklidir. Bu yapının tür parametrelerinin listesi. Bkz. [tür listesi](type-list.md).|
|`Implements`|İsteğe bağlı. Bu yapının bir veya daha fazla arabirimin üyelerini uyguladığını gösterir. Bkz. [Implements açıklaması](implements-statement.md).|
|`interfacenames`|İfadesini kullanıyorsanız gereklidir `Implements` . Bu yapının uyguladığı arabirimlerin adları.|
|`datamemberdeclarations`|Gereklidir. `Const` `Dim` `Enum` `Event` Yapının *veri üyelerini* bildiren sıfır veya daha fazla,, veya ifadesi.|
|`methodmemberdeclarations`|İsteğe bağlı. `Function` `Operator` `Property` `Sub` Yapının *Yöntem üyeleri* olarak işlev gösteren sıfır veya daha fazla bildirim,, veya yordamlar.|
|`End Structure`|Gereklidir. Tanımı sonlandırır `Structure` .|

## <a name="remarks"></a>Açıklamalar

`Structure`İfade, özelleştirebileceğiniz bir bileşik değer türü tanımlar. *Yapı* , önceki Visual Basic sürümlerindeki Kullanıcı tanımlı tür (udt) genelleştirmesidir. Daha fazla bilgi için bkz. [yapılar](../../programming-guide/language-features/data-types/structures.md).

Yapılar sınıflarla aynı özelliklerin birçoğunu destekler. Örneğin, yapıların özellikleri ve yordamları olabilir, arabirimler uygulayabilir ve parametreli oluşturuculara sahip olabilirler. Ancak, devralma, bildirimler ve kullanım gibi alanlardaki yapılar ve sınıflar arasında önemli farklılıklar vardır. Ayrıca, sınıflar başvuru türleridir ve yapılardır değer türlerdir. Daha fazla bilgi için bkz. [yapılar ve sınıflar](../../programming-guide/language-features/data-types/structures-and-classes.md).

`Structure`Yalnızca ad alanı veya modül düzeyinde kullanabilirsiniz. Bu, bir yapının *bildirim bağlamının* bir kaynak dosya, ad alanı, sınıf, yapı, modül veya arabirim olması ve bir yordam veya blok olamayacağı anlamına gelir. Daha fazla bilgi için bkz. [bildirim bağlamları ve varsayılan erişim düzeyleri](declaration-contexts-and-default-access-levels.md).

Varsayılan yapılar [arkadaş](../modifiers/friend.md) erişimine sahiptir. Erişim değiştiricilerini kullanarak erişim düzeylerini ayarlayabilirsiniz. Daha fazla bilgi için bkz. [Visual Basic erişim düzeyleri](../../programming-guide/language-features/declared-elements/access-levels.md).

## <a name="rules"></a>Kurallar

- **İç içe geçme.** Bir yapıyı diğeri içinde tanımlayabilirsiniz. Dış yapıya *kapsayan yapı* denir ve iç yapıya *iç içe yapı* denir. Ancak, iç içe bir yapının üyelerine kapsayan yapı aracılığıyla erişemezsiniz. Bunun yerine, iç içe yapının veri türünün bir değişkenini bildirmeniz gerekir.

- **Üye bildirimi.** Bir yapının her üyesini bildirmeniz gerekir. [](../modifiers/protected.md) `Protected Friend` Bir yapıyla hiçbir şey devraldığı için bir yapı üyesi korunamıyor veya Ancak, yapının kendisi `Protected` veya olabilir `Protected Friend` .
  
     Bir yapıda sıfır veya daha fazla paylaşılmayan değişken ya da paylaşılmayan, özel olmayan olaylar bildirebilirsiniz. Bazıları paylaşılmamış olsa bile yalnızca sabitler, Özellikler ve yordamlar olamaz.

- **Başlatılmasında.** Bir yapının paylaşılmayan veri üyesinin değerini, bildiriminin bir parçası olarak başlatılamaz. Bu tür bir veri üyesini yapıda parametreli bir Oluşturucu aracılığıyla ya da yapının bir örneğini oluşturduktan sonra üyeye bir değer atamanız gerekir.

- **Devralmayı.** Bir yapı <xref:System.ValueType> , tüm yapıların devraldığı dışındaki herhangi bir türden devralınabilir. Özellikle, bir yapı diğerinden devralınabilir.

     Bir yapı tanımında [Inherits ifadesini](inherits-statement.md) belirtmek için bile kullanamazsınız <xref:System.ValueType> .

- **Paylaşır.** Yapı [Implements ifadesini](implements-statement.md)kullanıyorsa, içinde belirttiğiniz her arabirim tarafından tanımlanan her üyeyi uygulamanız gerekir `interfacenames` .

- **Varsayılan özellik.** Bir yapı [varsayılan değiştiricisini kullanarak](../modifiers/default.md) en çok bir özelliği *varsayılan özelliği* olarak belirtebilir. Daha fazla bilgi için bkz. [Default](../modifiers/default.md).

## <a name="behavior"></a>Davranış

- **Erişim düzeyi.** Bir yapı içinde, her üyeyi kendi erişim düzeyiyle bildirebilirsiniz. Tüm yapı üyeleri varsayılan olarak [genel](../modifiers/public.md) erişime sahiptir. Yapının kendisine daha kısıtlı bir erişim düzeyi varsa, erişim değiştiricilerine erişim düzeylerini ayarlasanız bile bu, erişimi otomatik olarak kısıtlar.

- **Kapsam.** Bir yapı, kapsayan ad alanı, sınıf, yapı veya modül genelinde kapsamdadır.

     Her yapı üyesinin kapsamı tüm yapısıdır.

- **Süre.** Bir yapının yaşam süresi yoktur. Bunun yerine, bu yapının her örneğinin diğer tüm örneklerden bağımsız bir yaşam süresi vardır.

     Bir örneğin yaşam süresi, [Yeni bir işleç](../operators/new-operator.md) yan tümcesi tarafından oluşturulduğunda başlar. Bu, kendisini tutan değişkenin ömrü sona erdiğinde sona erer.

     Bir yapı örneğinin ömrünü genişletemezsiniz. Statik yapı işlevselliğine yaklaşık bir modül tarafından sağlanır. Daha fazla bilgi için bkz. [module deyimleri](module-statement.md).

     Yapı üyelerinin yaşam sürelerinin nasıl ve nerede bildirilmesine bağlı olarak yaşam süreleri vardır. Daha fazla bilgi için bkz. [Class deyimindeki](class-statement.md)"Lifetime".

- **Yeter.** Bir yapının dışındaki kodun bir üyenin adını bu yapının adıyla nitelemeniz gerekir.

     İç içe yerleştirilmiş bir yapı içindeki kod, bir programlama öğesine nitelenmemiş bir başvuru yaparsa, Visual Basic iç içe yapıdaki öğeyi, ardından kapsayan yapısını ve bu öğeyi en dıştaki içeren en dıştaki öğeyi arar. Daha fazla bilgi için bkz. [bildirilmemiş öğelere başvurular](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).

- **Bellek tüketimi.** Tüm bileşik veri türlerinde olduğu gibi, üyelerinin nominal depolama ayırmalarını birlikte ekleyerek bir yapının toplam bellek tüketimini güvenle hesaplayabilirsiniz. Ayrıca, bellekteki depolama sırasının bildirimin sıralamayla aynı olduğunu güvenli bir şekilde varsayamaz. Bir yapının depolama yerleşimini denetetmeniz gerekirse, <xref:System.Runtime.InteropServices.StructLayoutAttribute> özniteliğini `Structure` ifadeye uygulayabilirsiniz.

## <a name="example"></a>Örnek

Aşağıdaki örnek, `Structure` bir çalışan için ilgili verilerin bir kümesini tanımlamak üzere ifadesini kullanır. `Public` `Friend` `Private` Veri öğelerinin duyarlılığını yansıtmak için,, ve üyelerinin kullanımını gösterir. Ayrıca yordamı, özelliği ve olay üyelerini gösterir.

[!code-vb[VbVbalrStatements#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#57)]

' Nin nasıl kullanılacağı hakkında daha fazla bilgi için `Structure` bkz. [yapı değişkeni](../../programming-guide/language-features/data-types/structure-variables.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Class Deyimi](class-statement.md)
- [Interface Deyimi](interface-statement.md)
- [Module Deyimi](module-statement.md)
- [Dim Deyimi](dim-statement.md)
- [Const Deyimi](const-statement.md)
- [Enum Deyimi](enum-statement.md)
- [Event Deyimi](event-statement.md)
- [Operator Deyimi](operator-statement.md)
- [Property Deyimi](property-statement.md)
- [Yapılar ve Sınıflar](../../programming-guide/language-features/data-types/structures-and-classes.md)
