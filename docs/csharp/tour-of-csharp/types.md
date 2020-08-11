---
title: 'Türleri ve üyelerini tanımlama-C turu #'
description: Programların yapı taşları türlerdir. C# ' de sınıflar, yapılar, arabirimler ve daha fazlasını oluşturma hakkında bilgi edinin.
ms.date: 08/06/2020
ms.openlocfilehash: 69d6f0fe1e11f287fb5e385761fc210a61929d10
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/11/2020
ms.locfileid: "88068547"
---
# <a name="types-and-members"></a>Türler ve Üyeler

## <a name="classes-and-objects"></a>Sınıflar ve nesneler

*Sınıflar* C# türlerinin en temel larıdır. Bir sınıf, durumu (alanları) ve eylemleri (Yöntemler ve diğer işlev üyelerini) tek bir birimde birleştiren bir veri yapısıdır. Sınıf, *nesne*olarak da bilinen sınıf *örnekleri* için bir tanım sağlar. Sınıflar, *Devralma* ve çok *biçimlilik*desteği, *türetilmiş sınıfların* *temel sınıfları*genişletebileceği ve özelleştirilebilecek mekanizmalar.

Yeni sınıflar sınıf bildirimleri kullanılarak oluşturulur. Sınıf bildirimi, üst bilgiyle başlar. Üst bilgi şunları belirtir:

- Sınıfın öznitelikleri ve değiştiriciler
- Sınıfın adı
- Temel sınıf (bir [taban sınıftan](#base-classes)devralınırken)
- Sınıf tarafından uygulanan Arabirimler.

Üst bilgi, sınırlayıcılar ve arasında yazılmış üye bildirimlerinin listesinden oluşan sınıf gövdesinden gelir `{` `}` .

Aşağıdaki kod, adlı basit bir sınıfın bir bildirimini gösterir `Point` :

:::code language="csharp" source="./snippets/shared/Types.cs" ID="PointClass":::

Sınıf örnekleri `new` , yeni bir örnek için bellek ayıran işleç kullanılarak oluşturulur, örneği başlatmak için bir oluşturucu çağırır ve örneğe bir başvuru döndürür. Aşağıdaki deyimler iki nesne oluşturur `Point` ve bu nesnelere başvuruları iki değişken halinde depolar:

:::code language="csharp" source="./snippets/shared/Types.cs" ID="CreatePoints":::

Nesne artık erişilebilir olmadığında bir nesnenin kapladığı bellek otomatik olarak geri kazanılır. C# ' ta nesneleri açıkça serbest bırakmak gerekli değildir veya mümkün değildir.

### <a name="type-parameters"></a>Tür parametreleri

Genel sınıflar [***tür parametrelerini***](../programming-guide/generics/index.md)tanımlar. Tür parametreleri, açılı ayraçlar içine alınmış tür parametre adlarının bir listesidir. Tür parametreleri sınıf adını izler. Daha sonra tür parametreleri sınıfının üyelerini tanımlamak için sınıf bildirimlerinin gövdesinde kullanılabilir. Aşağıdaki örnekte, öğesinin tür parametreleri `Pair` `TFirst` ve `TSecond` :

:::code language="csharp" source="./snippets/shared/Types.cs" ID="DefinePairClass":::

Tür parametrelerini almak için belirtilen bir sınıf türüne *Genel sınıf türü*denir. Yapı, arabirim ve temsilci türleri de genel olabilir.
Genel sınıf kullanıldığında, tür parametrelerinin her biri için tür bağımsız değişkenlerinin sağlanması gerekir:

:::code language="csharp" source="./snippets/shared/Types.cs" ID="CreatePairObject":::

Yukarıda olduğu gibi, tür bağımsız değişkenlerine sahip genel bir tür, `Pair<int,string>` oluşturulmuş bir *tür*olarak adlandırılır.

### <a name="base-classes"></a>Temel sınıflar

Sınıf bildirimi, bir temel sınıf belirtebilir. Sınıf adını ve tür parametrelerini, iki nokta üst üste ve temel sınıfın adına uygulayın. Temel sınıf belirtiminin atlanması, türden türetmeye benzer `object` . Aşağıdaki örnekte, öğesinin temel sınıfı `Point3D` olur `Point` . İlk örnekte, öğesinin temel sınıfı `Point` Şu şekilde olur `object` :

:::code language="csharp" source="./snippets/shared/Types.cs" ID="Create3DPoint":::

Bir sınıf, temel sınıfının üyelerini devralır. Devralma, bir sınıfın temel sınıfının neredeyse tüm üyelerini dolaylı olarak içerdiği anlamına gelir. Bir sınıf örneği ve statik oluşturucuları ve sonlandırıcıyı almaz. Türetilmiş bir sınıf, devraldığı üyelere yeni üyeler ekleyebilir, ancak devralınan bir üyenin tanımını kaldıramıyorum. Önceki örnekte, `Point3D` `X` ve `Y` üyelerini devralır `Point` ve her `Point3D` örnek üç özellik içerir,, `X` `Y` ve `Z` .

Bir sınıf türünden, temel sınıf türlerinden herhangi birine örtük bir dönüştürme vardır. Bir sınıf türünün değişkeni, bu sınıfın bir örneğine veya türetilmiş herhangi bir sınıfın örneğine başvurabilir. Örneğin, önceki sınıf bildirimleri verildiğinde, türünde bir değişken `Point` bir `Point` veya a başvurabilir `Point3D` :

:::code language="csharp" source="./snippets/shared/Types.cs" ID="ImplicitCastToBase":::

## <a name="structs"></a>Yapılar

Sınıflar devralmayı ve çok biçimliliği destekleyen türleri tanımlar. Bunlar, türetilmiş sınıfların hiyerarşileri temelinde gelişmiş davranışlar oluşturmanızı sağlar. Buna karşılık [***Yapı***](../language-reference/builtin-types/struct.md) türleri, birincil amacı veri değerlerini depolamak olan daha basit türlerdir. Yapılar temel bir tür bildiremeyebilir; örtülü olarak türeteler <xref:System.ValueType?displayProperty=nameWithType> . `struct`Bir türden başka türler türetilemiyor `struct` . Örtülü olarak mühürlenirler.

:::code language="csharp" source="./snippets/shared/Types.cs" ID="PointStruct":::

## <a name="interfaces"></a>Arabirimler

[***Arabirim***](../programming-guide/interfaces/index.md) , sınıflar ve yapılar tarafından uygulanabilecek bir sözleşmeyi tanımlar. Arabirim, Yöntemler, özellikler, olaylar ve Dizin oluşturucular içerebilir. Bir arabirim genellikle tanımladığı üyelerin uygulamalarını sağlamaz; yalnızca arabirimini uygulayan sınıflar veya yapılar tarafından sağlanması gereken üyeleri belirtir.

Arabirimler ***birden fazla devralma***kullanabilir. Aşağıdaki örnekte, arabirimi `IComboBox` hem hem de öğesinden devralır `ITextBox` `IListBox` .

:::code language="csharp" source="./snippets/shared/Types.cs" ID="FirstInterfaces":::

Sınıflar ve yapılar birden çok arabirim uygulayabilir. Aşağıdaki örnekte, sınıfı `EditBox` hem hem de uygular `IControl` `IDataBound` .

:::code language="csharp" source="./snippets/shared/Types.cs" ID="ImplementInterfaces":::

Bir sınıf veya yapı belirli bir arabirimi uygularsa, bu sınıfın veya yapının örnekleri örtülü olarak bu arabirim türüne dönüştürülebilir. Örneğin:

:::code language="csharp" source="./snippets/shared/Types.cs" ID="UseInterfaces":::

## <a name="enums"></a>Numaralandırmalar

Sabit [***listesi***](../language-reference/builtin-types/enum.md) türü bir sabit değerler kümesini tanımlar. Aşağıdaki, `enum` farklı kök vegetables değerlerini tanımlayan sabitleri bildirir:

:::code language="csharp" source="./snippets/shared/Types.cs" ID="EnumDeclaration":::

Ayrıca, `enum` bayrak olarak birlikte kullanılacak bir de tanımlayabilirsiniz. Aşağıdaki bildirim dört mevsimler için bir bayraklar kümesi bildirir. Tüm mevsimleri içeren bir değer de dahil olmak üzere mevsimlerin herhangi bir birleşimi uygulanabilir `All` :

:::code language="csharp" source="./snippets/shared/Types.cs" ID="FlagsEnumDeclaration":::

Aşağıdaki örnekte, önceki Numaralandırmaların bildirimleri gösterilmektedir:

:::code language="csharp" source="./snippets/shared/Types.cs" ID="UsingEnums":::

## <a name="nullable-types"></a>Null atanabilir türler

Herhangi bir türdeki değişkenler ***null atanamaz*** veya ***null yapılabilir***olarak belirtilebilir. Null atanabilir bir değişken `null` , değer olmadığını gösteren ek bir değer tutabilir. Null yapılabilir değer türleri (yapılar veya numaralandırmalar) tarafından temsil edilir <xref:System.Nullable%601?displayProperty=nameWithType> . Null yapılamayan ve Nullable başvuru türleri, her ikisi de temel alınan başvuru türü tarafından temsil edilir. Ayrım, derleyici tarafından okunan meta veriler ve bazı kitaplıklar tarafından temsil edilir. Derleyici, null yapılabilir başvurular, önce değeri denetlenmeden başvurulduğunu uyarı verir `null` . Derleyici aynı zamanda olabilecek bir değere null atanamaz başvurular atandığında uyarı da sağlar `null` . Aşağıdaki örnek, ***null atanabilir bir int***bildirir ve ' a başlatılıyor `null` . Ardından, değerini olarak ayarlar `5` . Aynı şekilde ***null olabilen bir dize***ile aynı kavramı gösterir. Daha fazla bilgi için bkz. [Nullable değer türleri](../language-reference/builtin-types/nullable-value-types.md) ve [null yapılabilir başvuru türleri](../nullable-references.md).

:::code language="csharp" source="./snippets/shared/Types.cs" ID="DeclareNullable":::

## <a name="tuples"></a>Demetler

C#, hafif bir veri yapısındaki birden çok veri öğesini gruplamak için kısa sözdizimi sağlayan [***tanımlama gruplarını***](../language-reference/builtin-types/value-tuples.md)destekler. `(` `)` Aşağıdaki örnekte gösterildiği gibi, ve arasındaki üyelerin türlerini ve adlarını bildirerek bir tanımlama grubu örneğini oluşturabilirsiniz:

:::code language="csharp" source="./snippets/shared/Types.cs" ID="DeclareTuples":::

Tanımlama grupları, bir sonraki makalede açıklanan yapı taşlarını kullanmadan, birden fazla üye içeren veri yapısına bir alternatif sağlar.

>[!div class="step-by-step"]
>[Önceki](index.md) 
> [Sonraki](program-building-blocks.md)
