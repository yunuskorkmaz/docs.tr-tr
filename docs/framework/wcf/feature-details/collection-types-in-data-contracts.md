---
title: Veri Sözleşmelerinde Koleksiyon Türleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- collection types [WCF], data contracts
- data contracts [WCF], collection types
- collection types [WCF]
ms.assetid: 9b45b28e-0a82-4ea3-8c33-ec0094aff9d5
ms.openlocfilehash: a10b7c5295407cfbb36446581a4b75670e37bc6a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84579755"
---
# <a name="collection-types-in-data-contracts"></a>Veri Sözleşmelerinde Koleksiyon Türleri

*Koleksiyon* , belirli bir türdeki öğelerin listesidir. .NET Framework, bu tür listeler diziler veya diğer çeşitli türler (genel liste, genel <xref:System.ComponentModel.BindingList%601> , veya) kullanılarak temsil edilebilir <xref:System.Collections.Specialized.StringCollection> <xref:System.Collections.ArrayList> . Örneğin, bir koleksiyon belirli bir müşteri için adreslerin listesini tutabilir. Bu koleksiyonlara, gerçek türlerine bakılmaksızın *liste koleksiyonları*denir.

Bir öğe ("Key") ve diğeri ("Value") arasındaki ilişkiyi temsil eden özel bir koleksiyon biçimi vardır. .NET Framework, bunlar ve genel sözlük gibi türler tarafından temsil edilir <xref:System.Collections.Hashtable> . Örneğin, bir ilişki koleksiyonu bir şehri ("anahtar") kendi popülasyonu ("değer") ile eşleyebilir. Bu koleksiyonlara, gerçek türlerine bakılmaksızın *Sözlük koleksiyonları*denir.

Koleksiyonlar, veri anlaşması modelinde özel bir işleme alır.

<xref:System.Collections.IEnumerable>Diziler ve genel Koleksiyonlar dahil olmak üzere arabirimi uygulayan türler koleksiyonlar olarak tanınır. Bunlar, <xref:System.Collections.IDictionary> veya genel arabirimlerini uygulayan türler <xref:System.Collections.Generic.IDictionary%602> Sözlük koleksiyonlarıdır; diğerleri liste koleksiyonlarıdır.

Koleksiyon türlerinde, bir yöntemi `Add` ve parametresiz bir oluşturucuyu olması gibi ek gereksinimler, aşağıdaki bölümlerde ayrıntılı olarak ele alınmıştır. Bu, koleksiyon türlerinin hem serileştirilmiş hem de seri durumdan çıkarılabilmesini sağlar. Bu, bazı koleksiyonların genel (parametresiz oluşturucusu olmadığından) gibi doğrudan desteklenmediği anlamına gelir <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> . Bununla birlikte, bu kısıtlamaları atlama hakkında daha fazla bilgi için bu konunun devamındaki "koleksiyon arabirim türleri ve salt okuma koleksiyonları kullanma" bölümüne bakın.

Koleksiyonlarda bulunan türlerin veri sözleşme türleri olması veya başka türlü seri hale getirilebilir olması gerekir. Daha fazla bilgi için bkz. [veri sözleşmesi serileştiricisi tarafından desteklenen türler](types-supported-by-the-data-contract-serializer.md).

Ne olduğu ve geçerli bir koleksiyon olarak kabul edildiği hakkında daha fazla bilgi için, bu konunun "Gelişmiş koleksiyon kuralları" bölümünde koleksiyonları serileştirme hakkındaki bilgilere bakın.

## <a name="interchangeable-collections"></a>Değiştirilebilir Koleksiyonlar

Aynı türdeki tüm liste koleksiyonları aynı veri sözleşmesine sahip olacak şekilde değerlendirilir ( <xref:System.Runtime.Serialization.CollectionDataContractAttribute> Bu konunun ilerleyen kısımlarında açıklandığı gibi özniteliği kullanılarak özelleştirilmedikleri sürece). Bu nedenle, örneğin, aşağıdaki veri sözleşmeleri eşdeğerdir.

[!code-csharp[c_collection_types_in_data_contracts#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#0)]
[!code-vb[c_collection_types_in_data_contracts#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#0)]

Her iki veri sözleşmesi de aşağıdaki koda benzer şekilde XML ile sonuçlanır.

```xml
<PurchaseOrder>
    <customerName>...</customerName>
    <items>
        <Item>...</Item>
        <Item>...</Item>
        <Item>...</Item>
        ...
    </items>
    <comments>
        <string>...</string>
        <string>...</string>
        <string>...</string>
        ...
    </comments>
</PurchaseOrder>
```

Koleksiyon interchangeability, örneğin, sunucuda performans için iyileştirilmiş bir koleksiyon türü ve istemcideki Kullanıcı arabirimi bileşenlerine bağlanacak şekilde tasarlanan bir koleksiyon türü kullanmanıza olanak sağlar.

Liste koleksiyonlarına benzer şekilde, aynı anahtar ve değer türlerine sahip tüm sözlük koleksiyonları aynı veri sözleşmesine sahip olacak şekilde değerlendirilir (özniteliği tarafından özelleştirilmediği müddetçe <xref:System.Runtime.Serialization.CollectionDataContractAttribute> ).

Yalnızca koleksiyon denklemesiyle ilgili olarak önemli olan veri sözleşmesi türü .NET türleri değildir. Diğer bir deyişle, type1 koleksiyonu, type1 ve type2 eşdeğer veri sözleşmeleri içeriyorsa bir type2 koleksiyonuna eşdeğer olarak kabul edilir.

Genel olmayan koleksiyonlar, türü genel koleksiyonlarla aynı veri sözleşmesine sahip olarak kabul edilir `Object` . (Örneğin, ve genel için veri sözleşmeleri <xref:System.Collections.ArrayList> <xref:System.Collections.Generic.List%601> `Object` aynıdır.)

## <a name="using-collection-interface-types-and-read-only-collections"></a>Koleksiyon arabirim türleri ve salt okunurdur koleksiyonları kullanma

Koleksiyon arabirim türleri ( <xref:System.Collections.IEnumerable> , <xref:System.Collections.IDictionary> , genel <xref:System.Collections.Generic.IDictionary%602> veya bu arabirimlerden türetilmiş arabirimler), gerçek koleksiyon türleri için koleksiyon veri sözleşmeleri ile eşdeğer olan koleksiyon veri sözleşmeleri olarak da düşünülür. Bu nedenle, bir koleksiyon arabirim türü olarak serileştirilmekte olan türü bildirmek mümkündür ve sonuçlar gerçek bir koleksiyon türü kullanılmış gibi aynı olur. Örneğin, aşağıdaki veri sözleşmeleri eşdeğerdir.

[!code-csharp[c_collection_types_in_data_contracts#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#1)]
[!code-vb[c_collection_types_in_data_contracts#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#1)]

Serileştirme sırasında, belirtilen tür bir arabirim olduğunda, kullanılan gerçek örnek türü bu arabirimi uygulayan herhangi bir tür olabilir. Daha önce tartışılan kısıtlamalar (parametresiz bir oluşturucuya ve bir `Add` yönteme sahip) uygulanmaz. Örneğin, <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> genel türünde bir veri üyesini doğrudan bildiremeseniz bile Customer2 içindeki adresleri genel bir adres örneğine ayarlayabilirsiniz <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> .

Seri durumdan çıkarma sırasında, belirtilen tür bir arabirim olduğunda, serileştirme altyapısı, belirtilen arabirimi uygulayan bir tür seçer ve tür oluşturulur. Bilinen türler mekanizması ( [veri sözleşmesinin bilinen türlerinde](data-contract-known-types.md)açıklanmıştır) burada hiçbir etkiye sahip değildir; tür seçimi WCF 'de yerleşik olarak bulunur.

## <a name="customizing-collection-types"></a>Koleksiyon türlerini özelleştirme

Koleksiyon türlerini <xref:System.Runtime.Serialization.CollectionDataContractAttribute> , birkaç kullanımı bulunan özniteliğini kullanarak özelleştirebilirsiniz.

Koleksiyon türlerini özelleştirme interchangeability koleksiyonu, bu nedenle bu özniteliği mümkün olduğunda uygulamaktan kaçınmak için genellikle önerilir. Bu sorun hakkında daha fazla bilgi için, bu konunun devamındaki "Gelişmiş koleksiyon kuralları" bölümüne bakın.

### <a name="collection-data-contract-naming"></a>Koleksiyon veri anlaşması adlandırma

Ad koleksiyon türlerini adlandırma kuralları, [veri anlaşması adlarında](data-contract-names.md)açıklandığı şekilde, düzenli veri sözleşme türlerini adlandırmakla benzerdir, ancak bazı önemli farklılıklar vardır:

- <xref:System.Runtime.Serialization.CollectionDataContractAttribute>Özniteliği, özniteliği yerine adı özelleştirmek için kullanılır <xref:System.Runtime.Serialization.DataContractAttribute> . <xref:System.Runtime.Serialization.CollectionDataContractAttribute>Özniteliği `Name` ve özellikleri de vardır `Namespace` .

- <xref:System.Runtime.Serialization.CollectionDataContractAttribute>Özniteliği uygulandığında, koleksiyon türleri için varsayılan ad ve ad alanı, koleksiyonda bulunan türlerin adlarına ve ad alanlarına bağlıdır. Bunlar, koleksiyon türünün adı ve ad alanından etkilenmemektedir. Bir örnek için, aşağıdaki türlere bakın.

  ```csharp
  public CustomerList1 : Collection<string> {}
  public StringList1 : Collection<string> {}
  ```

Her iki tür ' veri anlaşması adı "CustomerList1" veya "StringList1" değil "ArrayOfstring". Bu, kök düzeyindeki bu türlerden herhangi birinin serileştirilmesi, aşağıdaki koda benzer bir XML üretir.

```xml
<ArrayOfstring>
    <string>...</string>
    <string>...</string>
    <string>...</string>
    ...
</ArrayOfstring>
```

Bu adlandırma kuralı, bir dize listesini temsil eden özelleştirilmeyen bir türün aynı veri sözleşmesine ve XML gösterimine sahip olduğundan emin olmak için seçilmiştir. Bu, koleksiyonu interchangeability mümkün hale getirir. Bu örnekte, CustomerList1 ve StringList1 tamamen değiştirilebilir.

Ancak <xref:System.Runtime.Serialization.CollectionDataContractAttribute> Öznitelik uygulandığında, öznitelik üzerinde hiçbir özellik ayarlanmamışsa bile koleksiyon özelleştirilmiş bir koleksiyon veri anlaşması haline gelir. Koleksiyon veri sözleşmesinin adı ve ad alanı, daha sonra koleksiyon türüne bağlıdır. Bir örnek için, aşağıdaki türe bakın.

[!code-csharp[c_collection_types_in_data_contracts#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#2)]
[!code-vb[c_collection_types_in_data_contracts#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#2)]

Serileştirilmiş olduğunda, elde edilen XML aşağıdakine benzer.

```xml
<CustomerList2>
    <string>...</string>
    <string>...</string>
    <string>...</string>
    ...
</CustomerList2>
```

Bunun artık özelleştirilmemiş türlerin XML gösterimine eşit olmadığına dikkat edin.

- `Name`Ve `Namespace` özelliklerini kullanarak adlandırmanın daha fazla özelleştirmesini sağlayabilirsiniz. Aşağıdaki sınıfa bakın.

  [!code-csharp[c_collection_types_in_data_contracts#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#3)]
  [!code-vb[c_collection_types_in_data_contracts#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#3)]

Elde edilen XML aşağıdakine benzer.

```xml
<cust_list>
    <string>...</string>
    <string>...</string>
    <string>...</string>
    ...
</cust_list>
```

Daha fazla bilgi için bu konunun ilerleyen bölümlerindeki "Gelişmiş koleksiyon kuralları" bölümüne bakın.

### <a name="customizing-the-repeating-element-name-in-list-collections"></a>Liste koleksiyonlarında yinelenen öğe adını özelleştirme

Liste koleksiyonları yinelenen girdiler içerir. Normalde, her bir yinelenen giriş, koleksiyonda bulunan türün veri sözleşmesi adına göre adlı bir öğe olarak temsil edilir.

`CustomerList`Örneklerde, Koleksiyonlar dizeler içeriyordu. Dize temel türü için veri sözleşmesi adı "String" olduğundan, yinelenen öğe " \<string> " idi.

Ancak, <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> özelliği <xref:System.Runtime.Serialization.CollectionDataContractAttribute> özniteliğinde kullanarak, bu yinelenen öğe adı özelleştirilebilir. Bir örnek için, aşağıdaki türe bakın.

[!code-csharp[c_collection_types_in_data_contracts#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#4)]
[!code-vb[c_collection_types_in_data_contracts#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#4)]

Elde edilen XML aşağıdakine benzer.

```xml
<CustomerList4>
    <customer>...</customer>
    <customer>...</customer>
    <customer>...</customer>
    ...
</CustomerList4>
```

Yinelenen öğenin ad alanı her zaman koleksiyon veri sözleşmesinin ad alanıyla aynıdır ve bu, `Namespace` daha önce açıklandığı gibi özelliği kullanılarak özelleştirilebilir.

### <a name="customizing-dictionary-collections"></a>Sözlük koleksiyonlarını özelleştirme

Sözlük koleksiyonları, her girdinin bir anahtara ve ardından bir değere sahip olduğu, temel olarak giriş listesidir. Normal listelerle olduğu gibi, özelliğini kullanarak, yinelenen öğeye karşılık gelen öğe adını değiştirebilirsiniz <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> .

Ayrıca, ve özelliklerini kullanarak anahtar ve değeri temsil eden öğe adlarını değiştirebilirsiniz <xref:System.Runtime.Serialization.CollectionDataContractAttribute.KeyName%2A> <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ValueName%2A> . Bu öğelerin ad alanları, koleksiyon veri sözleşmesinin ad alanıyla aynıdır.

Bir örnek için, aşağıdaki türe bakın.

[!code-csharp[c_collection_types_in_data_contracts#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#5)]
[!code-vb[c_collection_types_in_data_contracts#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#5)]

Serileştirilmiş olduğunda, elde edilen XML aşağıdakine benzer.

```xml
<CountriesOrRegionsWithCapitals>
    <entry>
        <countryorregion>USA</countryorregion>
        <capital>Washington</capital>
    </entry>
    <entry>
        <countryorregion>France</countryorregion>
        <capital>Paris</capital>
    </entry>
    ...
</CountriesOrRegionsWithCapitals>
```

Sözlük koleksiyonları hakkında daha fazla bilgi için bu konunun devamındaki "Gelişmiş koleksiyon kuralları" bölümüne bakın.

## <a name="collections-and-known-types"></a>Koleksiyonlar ve bilinen türler

Diğer koleksiyonların veya koleksiyon arabirimlerinin yerine polymorphically kullandığınızda, bilinen türlere koleksiyon türleri eklemeniz gerekmez. Örneğin, türünde bir veri üyesi bildirirseniz <xref:System.Collections.IEnumerable> ve örneğini göndermek için kullanırsanız <xref:System.Collections.ArrayList> , <xref:System.Collections.ArrayList> bilinen türlere eklemeniz gerekmez.

Koleksiyon olmayan türlerin yerine koleksiyonlar polymorphically kullandığınızda, bunların bilinen türlere eklenmesi gerekir. Örneğin, türünde bir veri üyesi bildirirseniz `Object` ve örneğini göndermek için kullanıyorsa <xref:System.Collections.ArrayList> , <xref:System.Collections.ArrayList> bilinen türlere ekleyin.

Bu, herhangi bir eşdeğer koleksiyon polymorphically seri hale getirme yapmanıza izin vermez. Örneğin, <xref:System.Collections.ArrayList> önceki örnekteki bilinen türler listesine eklediğinizde, bu, `Array of Object` denk bir veri sözleşmesine sahip olsa bile sınıfı atamanıza izin vermez. Bu, koleksiyon dışı türler için serileştirme üzerinde düzenli olarak bilinen türler davranışından farklı değildir, ancak koleksiyonların büyük bir olasılıkla daha yaygın olması nedeniyle koleksiyonlar durumunda anlaşılması özellikle önemlidir.

Serileştirme sırasında, belirli bir veri sözleşmesi için verilen herhangi bir kapsamda yalnızca bir tür tanınverilebilir ve eşdeğer koleksiyonların hepsi aynı veri sözleşmelerine sahiptir. Bu, önceki örnekte, hem hem de <xref:System.Collections.ArrayList> `Array of Object` bilinen türleri aynı kapsamda ekleyemeyeceğiniz anlamına gelir. Bu, koleksiyon olmayan türler için bilinen türler davranışına eşdeğerdir, ancak koleksiyonlar için anlaşılması özellikle önemlidir.

Bilinen türler, koleksiyonların içerikleri için de gerekli olabilir. Örneğin, <xref:System.Collections.ArrayList> aslında ve örnekleri içeriyorsa `Type1` `Type2` , bu türlerin her ikisi de bilinen türlere eklenmelidir.

Aşağıdaki örnek, koleksiyonlar ve bilinen türler kullanılarak düzgün şekilde oluşturulmuş bir nesne grafiğini gösterir. Örnek biraz contrived, çünkü gerçek bir uygulamada normalde aşağıdaki veri üyelerini olarak tanımlamaz `Object` ve bu nedenle bilinen tür/çok biçimlilik sorunları yoktur.

[!code-csharp[c_collection_types_in_data_contracts#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#6)]
[!code-vb[c_collection_types_in_data_contracts#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#6)]

Seri durumdan çıkarma sırasında, belirtilen tür bir koleksiyon türüdür, gönderilen tür, gerçekten gönderilen türden bağımsız olarak oluşturulur. Belirtilen tür bir koleksiyon arabirimse, seri hale getirici, bilinen türler açısından, örnek oluşturulacak bir tür seçer.

Ayrıca, seri durumdan çıkarma sırasında, belirtilen tür bir koleksiyon türü değilse ancak bir koleksiyon türü gönderiliyorsa, bilinen türler listesinden eşleşen bir koleksiyon türü alınır. Seri durumdan çıkarma sırasında bilinen türler listesine koleksiyon arabirim türleri eklemek mümkündür. Bu durumda, seri durumdan çıkarma altyapısı, örnek oluşturulacak bir tür seçer.

## <a name="collections-and-the-netdatacontractserializer-class"></a>Koleksiyonlar ve NetDataContractSerializer sınıfı

<xref:System.Runtime.Serialization.NetDataContractSerializer>Sınıf kullanımda olduğunda, dizi olmayan özelleştirilmemiş koleksiyon türleri ( <xref:System.Runtime.Serialization.CollectionDataContractAttribute> özniteliği olmadan) özel anlamlarını kaybeder.

Özniteliği ile işaretlenen özelleştirilmemiş koleksiyon türleri, <xref:System.SerializableAttribute> <xref:System.Runtime.Serialization.NetDataContractSerializer> <xref:System.SerializableAttribute> özniteliğe veya arabirim kurallarına göre sınıf tarafından yine de seri hale getirilebilir <xref:System.Runtime.Serialization.ISerializable> .

Sınıf kullanımda olsa bile, özelleştirilmiş koleksiyon türleri, koleksiyon arabirimleri ve diziler hala koleksiyonlar olarak değerlendirilir <xref:System.Runtime.Serialization.NetDataContractSerializer> .

## <a name="collections-and-schema"></a>Koleksiyonlar ve şema

Tüm eşdeğer koleksiyonlar, XML şeması tanım dili (XSD) şemasında aynı temsilde sahiptir. Bu nedenle, normalde, oluşturulan istemci kodunda, sunucuda bulunan bir koleksiyon türünü almaz. Örneğin, sunucu bir veri sözleşmesini genel <xref:System.Collections.Generic.List%601> tamsayı veri üyesi ile kullanabilir, ancak oluşturulan istemci kodunda aynı veri üyesi bir tamsayılar dizisi haline gelebilir.

Sözlük koleksiyonları, sözlüklerin olduğunu belirten, WCF 'ye özgü bir şema ek açıklaması ile işaretlenir; Aksi takdirde, anahtar ve değer içeren girişleri içeren basit listelerden ayırt edilemez. Koleksiyonların veri sözleşmesi şemasında nasıl temsil edildiği hakkında tam bir açıklama için bkz. [veri sözleşmesi şema başvurusu](data-contract-schema-reference.md).

Varsayılan olarak, içeri aktarılan koddaki özelleştirilmemiş koleksiyonlar için türler oluşturulmaz. Liste koleksiyonu türlerinin veri üyeleri diziler olarak içeri aktarılır ve sözlük toplama türlerinin veri üyeleri genel sözlük olarak içeri aktarılır.

Ancak, özelleştirilmiş koleksiyonlar için, özniteliğiyle işaretlenen ayrı türler oluşturulur <xref:System.Runtime.Serialization.CollectionDataContractAttribute> . (Şemadaki özelleştirilmiş bir koleksiyon türü, varsayılan ad alanı, ad, yinelenen öğe adı veya anahtar/değer öğesi adlarını kullanmayan bir öğedir.) Bu türler, <xref:System.Collections.Generic.List%601> liste türleri ve sözlük türleri Için genel sözlük Için genel 'den türetilen boş türlerdir.

Örneğin, sunucusunda aşağıdaki türlere sahip olabilirsiniz.

[!code-csharp[c_collection_types_in_data_contracts#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#7)]
[!code-vb[c_collection_types_in_data_contracts#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#7)]

Şema verildiğinde ve geri aktarıldığında, oluşturulan istemci kodu aşağıdakine benzerdir (okuma kolaylığı için özellikler yerine alanlar gösterilir).

[!code-csharp[c_collection_types_in_data_contracts#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#8)]
[!code-vb[c_collection_types_in_data_contracts#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#8)]

Oluşturulan kodda varsayılan olanlardan farklı türler kullanmak isteyebilirsiniz. Örneğin, <xref:System.ComponentModel.BindingList%601> Kullanıcı arabirimi bileşenlerine bağlamayı kolaylaştırmak için veri üyelerinize ait normal diziler yerine genel ' i kullanmak isteyebilirsiniz.

Oluşturulacak koleksiyon türlerini seçmek için <xref:System.Runtime.Serialization.ImportOptions.ReferencedCollectionTypes%2A> <xref:System.Runtime.Serialization.ImportOptions> şemayı içeri aktarırken nesnenin özelliğine kullanmak istediğiniz koleksiyon türlerinin bir listesini geçirin. Bu türlere *başvurulan koleksiyon türleri*denir.

Genel türlere başvurulduklarında, bunların tamamen açık genel türler veya tam kapalı genel türler olması gerekir.

> [!NOTE]
> Svcutil. exe aracını kullanırken, bu başvuru **/CollectionType** komut satırı anahtarı kullanılarak gerçekleştirilebilir (kısa biçim: **/CT**). Ayrıca, **/Reference** anahtarını kullanarak başvurulan koleksiyon türleri için derlemeyi belirtmeniz gerektiğini unutmayın (kısa biçim: **/r**). Tür geneldir ise, arkasından bir geri tırnak işareti ve genel parametre sayısı gelmelidir. Arka tırnak ( \` ), tek tırnak (') karakteriyle karıştırılmamalıdır. **/CollectionType** anahtarını birden çok kez kullanarak, birden fazla başvurulan koleksiyon türünü belirtebilirsiniz.

Örneğin, tüm listelerin genel olarak içeri aktarılmasını sağlamak için <xref:System.Collections.Generic.List%601> .

```console
svcutil.exe MyService.wsdl MyServiceSchema.xsd /r:C:\full_path_to_system_dll\System.dll /ct:System.Collections.Generic.List`1
```

Herhangi bir koleksiyonu içeri aktarırken, başvurulan koleksiyon türlerinin bu listesi taranır ve bir veri üyesi türü (özelleştirilmemiş koleksiyonlar için) veya türetilmek üzere temel bir tür olarak bulunursa en iyi eşleşen koleksiyon kullanılır (özelleştirilmiş koleksiyonlar için). Sözlükler yalnızca sözlüklere göre eşleşir, ancak listeler listelerle eşleştirilir.

Örneğin, genel <xref:System.ComponentModel.BindingList%601> ve <xref:System.Collections.Hashtable> başvurulan türler listesine eklerseniz, önceki örnek için oluşturulan istemci kodu aşağıdakine benzerdir.

[!code-csharp[c_collection_types_in_data_contracts#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#9)]
[!code-vb[c_collection_types_in_data_contracts#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#9)]

Koleksiyon arabirimi türlerini, başvurulan koleksiyon türlerinizin bir parçası olarak belirtebilirsiniz, ancak geçersiz koleksiyon türleri belirtemezsiniz (hiçbir `Add` Yöntem veya ortak Oluşturucu olmayan gibi).

Kapalı bir genel, en iyi eşleşme olarak kabul edilir. (Genel olmayan türler kapalı genel türlerine eşdeğer olarak kabul edilir `Object` ). Örneğin, genel türleri genel <xref:System.Collections.Generic.List%601> <xref:System.DateTime> <xref:System.ComponentModel.BindingList%601> (Genel açık) ise ve <xref:System.Collections.ArrayList> başvurulan koleksiyon türse, aşağıdakiler oluşturulur.

[!code-csharp[c_collection_types_in_data_contracts#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#10)]
[!code-vb[c_collection_types_in_data_contracts#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#10)]

Liste koleksiyonları için yalnızca aşağıdaki tablodaki durumlar desteklenir.

|Başvurulan tür|Başvurulan tür tarafından uygulanan arabirim|Örnek|Tür şöyle işlenir:|
|---------------------|----------------------------------------------|-------------|----------------------|
|Genel olmayan veya kapalı genel (herhangi bir sayıda parametre)|Genel olmayan|`MyType : IList`<br /><br /> veya<br /><br /> `MyType<T> : IList`<br /><br /> Burada T =`int`|Kapalı genel `Object` (örneğin, `IList<object>` )|
|Genel olmayan veya kapalı genel (koleksiyon türüyle eşleşmesi gerekmeyen parametre sayısı)|Kapalı genel|`MyType : IList<string>`<br /><br /> veya<br /><br /> `MyType<T> : IList<string>`Burada T =`int`|Kapalı genel (örneğin, `IList<string>` )|
|Herhangi bir sayıda parametreyle Genel kapalı|Tür parametrelerinden herhangi birini kullanarak genel ' i açın|`MyType<T,U,V> : IList<U>`<br /><br /> Burada T = `int` , U = `string` , V =`bool`|Kapalı genel (örneğin, `IList<string>` )|
|Genel 'i tek bir parametreyle aç|Türün parametresini kullanarak genel ' i açın|`MyType<T> : IList<T>`, T açık|Genel açık (örneğin, `IList<T>` )|

Bir tür birden fazla liste koleksiyonu arabirimi uygularsa, aşağıdaki kısıtlamalar geçerlidir:

- Tür, <xref:System.Collections.Generic.IEnumerable%601> farklı türlerde genel (veya türetilen arabirimlerini) birden çok kez uygularsa, tür geçerli bir başvurulan koleksiyon türü olarak kabul edilmez ve yok sayılır. Bu, bazı uygulamalar geçersiz olsa bile veya açık genel türler kullanıyorsa geçerlidir. Örneğin, genel ' i uygulayan bir tür ya da herhangi bir tür ya da tür bir <xref:System.Collections.Generic.IEnumerable%601> `int` parametre ya <xref:System.Collections.Generic.IEnumerable%601> `int` `Add` `int` `Add` da her ikisi de kabul eden bir yöntem ya da kabul etmeksizin bağımsız olarak, başvurulan bir koleksiyon olarak hiçbir şekilde kullanılamaz.

- Tür bir genel koleksiyon arabirimini de uygularsa <xref:System.Collections.IList> , genel koleksiyon arabirimi türü kapalı bir genel değilse tür hiçbir şekilde başvurulan koleksiyon türü olarak kullanılmaz <xref:System.Object> .

Sözlük koleksiyonları için yalnızca aşağıdaki tablodaki durumlar desteklenir.

|Başvurulan tür|Başvurulan tür tarafından uygulanan arabirim|Örnek|Tür olarak değerlendirildi|
|---------------------|----------------------------------------------|-------------|---------------------|
|Genel olmayan veya kapalı genel (herhangi bir sayıda parametre)|<xref:System.Collections.IDictionary>|`MyType : IDictionary`<br /><br /> veya<br /><br /> `MyType<T> : IDictionary`Burada T =`int`|Kapalı genel`IDictionary<object,object>`|
|Kapalı genel (herhangi bir sayıda parametre)|<xref:System.Collections.Generic.IDictionary%602>, kapalı|`MyType<T> : IDictionary<string, bool>`Burada T =`int`|Kapalı genel (örneğin, `IDIctionary<string,bool>` )|
|Kapalı genel (herhangi bir sayıda parametre)|Genel <xref:System.Collections.Generic.IDictionary%602> , herhangi bir anahtar veya değerden biri kapalı, diğeri açık ve türün parametrelerinden birini kullanıyor|`MyType<T,U,V> : IDictionary<string,V>`Burada T = `int` , U = `float` , V =`bool`<br /><br /> veya<br /><br /> `MyType<Z> : IDictionary<Z,bool>`Burada Z =`string`|Kapalı genel (örneğin, `IDictionary<string,bool>` )|
|Kapalı genel (herhangi bir sayıda parametre)|Genel <xref:System.Collections.Generic.IDictionary%602> , her iki anahtar ve değer açıktır ve her biri türün parametrelerinden birini kullanır|`MyType<T,U,V> : IDictionary<V,U>`Burada T = `int` , U = `bool` , V =`string`|Kapalı genel (örneğin, `IDictionary<string,bool>` )|
|Açık genel (iki parametre)|Genel <xref:System.Collections.Generic.IDictionary%602> , açık, her iki türün genel parametrelerini göründükleri sırada kullanır|`MyType<K,V> : IDictionary<K,V>`, K ve V her ikisi açık|Genel açık (örneğin, `IDictionary<K,V>` )|

Tür hem <xref:System.Collections.IDictionary> hem de Generic uygularsa <xref:System.Collections.Generic.IDictionary%602> , yalnızca genel <xref:System.Collections.Generic.IDictionary%602> olarak kabul edilir.

Kısmi Genel türlere başvurulması desteklenmez.

Yinelenen öğelere izin verilmez, örneğin, ' ın hem genel <xref:System.Collections.Generic.List%601> `Integer` hem de genel koleksiyonunu `Integer` <xref:System.Runtime.Serialization.ImportOptions.ReferencedCollectionTypes%2A> ' a ekleyemezsiniz, çünkü bu, şemada bir tamsayılar listesi bulunduğunda hangisini kullanacağınızı belirlemeyi olanaksız hale getirir. Yinelemeler, yalnızca şemada yinelenen sorunları ortaya çıkaran bir tür varsa algılanır. Örneğin, içeri aktarılan şema tamsayılar listesini içermiyorsa, içinde öğesinin hem genel hem de genel koleksiyonuna sahip olmasına izin verilir, <xref:System.Collections.Generic.List%601> `Integer` `Integer` <xref:System.Runtime.Serialization.ImportOptions.ReferencedCollectionTypes%2A> ancak hiçbir etkisi yoktur.

## <a name="advanced-collection-rules"></a>Gelişmiş koleksiyon kuralları

### <a name="serializing-collections"></a>Koleksiyonlar serileştiriliyor

Serileştirme için koleksiyon kurallarının bir listesi aşağıda verilmiştir:

- Koleksiyon türlerini (koleksiyon koleksiyonlarına sahip) birleştirmek için izin verilir. Pürüzlü Diziler koleksiyonların koleksiyonları olarak değerlendirilir. Çok boyutlu diziler desteklenmiyor.

- Bayt ve dizi dizileri <xref:System.Xml.XmlNode> , Koleksiyonlar değil, temel öğeler olarak kabul edilen özel dizi türlerdir. Bir bayt dizisini seri hale getirmek, her bayt için ayrı bir öğe yerine Base64 kodlamalı verilerin bir öbeğini içeren tek bir XML öğesinde sonuçlanır. Dizisinin nasıl işlendiği hakkında daha fazla bilgi için <xref:System.Xml.XmlNode> bkz. [Data Contracts 'de XML ve ADO.net Types](xml-and-ado-net-types-in-data-contracts.md). Tabii ki, bu özel türler kendilerine katılabilirler: bir bayt dizisi dizisi, her biri Base64 kodlamalı verilerin bir öbeğini içeren birden çok XML öğesiyle sonuçlanır.

- <xref:System.Runtime.Serialization.DataContractAttribute>Öznitelik bir koleksiyon türüne uygulanırsa, tür bir koleksiyon olarak değil, düzenli bir veri anlaşması türü olarak değerlendirilir.

- Bir koleksiyon türü arabirimini uyguluyorsa <xref:System.Xml.Serialization.IXmlSerializable> , aşağıdaki kurallar bir tür verildiğinde geçerlidir `myType:IList<string>, IXmlSerializable` :

  - Belirtilen tür ise, `IList<string>` tür bir liste olarak serileştirilir.

  - Belirtilen tür ise `myType` olarak serileştirilir `IXmlSerializable` .

  - Belirtilen tür ise, `IXmlSerializable` `IXmlSerializable` ancak yalnızca bilinen türler listesine eklediğinizde olarak serileştirilir `myType` .

- Koleksiyonlar serileştirilir ve aşağıdaki tabloda gösterilen yöntemler kullanılarak seri durumdan çıkarılmakta.

|Koleksiyon türü uygular|Serileştirme sırasında çağrılan Yöntem (ler)|Seri durumdan çıkarma sırasında çağrılan metot (ler)|
|--------------------------------|-----------------------------------------|-------------------------------------------|
|Yorlar<xref:System.Collections.Generic.IDictionary%602>|`get_Keys`, `get_Values`|Genel ekleme|
|<xref:System.Collections.IDictionary>|`get_Keys`, `get_Values`|`Add`|
|Yorlar<xref:System.Collections.Generic.IList%601>|Genel <xref:System.Collections.Generic.IList%601> Dizin Oluşturucu|Genel ekleme|
|Yorlar<xref:System.Collections.Generic.ICollection%601>|Sının|Genel ekleme|
|<xref:System.Collections.IList>|<xref:System.Collections.IList>Dizinleyic|`Add`|
|Yorlar<xref:System.Collections.Generic.IEnumerable%601>|`GetEnumerator`|`Add`Uygun türde (genel parametrenin türü veya temel türlerinden biri) bir parametre alan, statik olmayan bir yöntem. Seri hale getirici, hem serileştirme hem de seri durumundan çıkarma sırasında koleksiyon türünü bir koleksiyon olarak değerlendirmek için bu tür bir yöntem bulunmalıdır.|
|<xref:System.Collections.IEnumerable>(ve <xref:System.Collections.ICollection> Bu nedenle ondan türetilen)|`GetEnumerator`|`Add`Türünde bir parametre alan, statik olmayan bir yöntem `Object` . Seri hale getirici, hem serileştirme hem de seri durumundan çıkarma sırasında koleksiyon türünü bir koleksiyon olarak değerlendirmek için bu tür bir yöntem bulunmalıdır.|

Yukarıdaki tabloda, koleksiyon arabirimleri azalan öncelik sırasına göre listelenmiştir. Bu, örneğin, bir tür hem hem de Generic uygularsa <xref:System.Collections.IList> <xref:System.Collections.Generic.IEnumerable%601> , koleksiyonun serileştirildiği ve bu kurallara göre seri durumdan çıkarılmasıdır <xref:System.Collections.IList> .

- Seri durumdan çıkarma sırasında, seri hale getiricinin hem serileştirme hem de seri durumundan çıkarma sırasında koleksiyon türünü bir koleksiyon olarak işlemesi için mevcut olması gereken parametresiz oluşturucuyu çağırarak bir türün örneği oluşturularak, tüm koleksiyonların serisi kaldırılır.

- Aynı genel koleksiyon arabirimi birden çok kez uygulanırsa (örneğin, bir tür hem genel hem de genel ' i uygularsa <xref:System.Collections.Generic.ICollection%601> `Integer` <xref:System.Collections.Generic.ICollection%601> <xref:System.String> ) ve daha yüksek öncelikli bir arabirim bulunamazsa, koleksiyon geçerli bir koleksiyon olarak değerlendirilmez.

- Koleksiyon türlerinde, <xref:System.SerializableAttribute> özniteliğe uygulanan özniteliği bulunabilir ve <xref:System.Runtime.Serialization.ISerializable> arabirimi uygulayabilir. Bunların her ikisi de yok sayılır. Ancak, tür koleksiyon türü gereksinimlerini tam olarak karşılamıyorsa (örneğin, `Add` yöntemi eksikse), tür bir koleksiyon türü olarak değerlendirilmez ve bu nedenle, <xref:System.SerializableAttribute> <xref:System.Runtime.Serialization.ISerializable> türün seri hale getirilebilir olup olmadığını belirlemekte öznitelik ve arabirim kullanılır.

- <xref:System.Runtime.Serialization.CollectionDataContractAttribute>Özniteliğini özelleştirmek için bir koleksiyona özniteliği uygulamak, <xref:System.SerializableAttribute> önceki geri dönüş mekanizmasını kaldırır. Bunun yerine, özelleştirilmiş bir koleksiyon koleksiyon türü gereksinimlerini karşılamıyorsa, bir <xref:System.Runtime.Serialization.InvalidDataContractException> özel durum oluşturulur. Özel durum dizesi genellikle belirli bir türün geçerli bir koleksiyon (hiçbir yöntem yok, parametresiz Oluşturucu vb.) olarak kabul edilmediğini açıklayan bilgileri içerir `Add` . bu nedenle, genellikle <xref:System.Runtime.Serialization.CollectionDataContractAttribute> hata ayıklama amacıyla özniteliği uygulamak yararlı olur.

### <a name="collection-naming"></a>Koleksiyon adlandırma

Aşağıda, koleksiyon adlandırma kurallarının bir listesi verilmiştir:

- Tüm sözlük toplama verileri sözleşmeleri için varsayılan ad alanı ve temel türler içeren liste toplama veri sözleşmeleri için `http://schemas.microsoft.com/2003/10/Serialization/Arrays` ad alanı kullanılarak geçersiz kılınmadığı sürece. Yerleşik XSD türlerine `char` `Timespan` ve, ve türlerine eşlenen türler `Guid` , bu amaçla temel elemanlar olarak kabul edilir.

- Ad alanı kullanılarak geçersiz kılınmadığı sürece, ilkel olmayan türler içeren koleksiyon türleri için varsayılan ad alanı, koleksiyonda yer alan türdeki veri sözleşmesi ad alanıyla aynıdır.

- Ad kullanılarak geçersiz kılınmadığı takdirde, liste toplama veri sözleşmeleri için varsayılan ad, koleksiyonda bulunan türün veri sözleşmesi adıyla birlikte "ArrayOf" dizesidir. Örneğin, genel tamsayılar listesinin veri sözleşme adı "Arrayofınt" ' dir. Veri sözleşmesi adının `Object` "anyType" olduğunu ve bu nedenle genel olmayan listelerin veri sözleşmesi adının <xref:System.Collections.ArrayList> "ArrayOfanyType" olduğunu aklınızda bulundurun.

Sözlük toplama veri sözleşmeleri için varsayılan ad, kullanılarak geçersiz kılınmamışsa `Name` , anahtar türünün veri sözleşmesi adı ile birleştirilmiş "Arrayofkeyary" dizesidir ve ardından değer türünün veri sözleşmesi adı gelir. Örneğin, bir dize ve tamsayı genel sözlüğünün veri sözleşme adı "Arrayofkeyvalueofstringınt" ' dir. Ayrıca, anahtar veya değer türleri basit türler değilse, anahtar ve değer türlerinin veri sözleşmesi ad alanlarının ad alanı karması ada eklenir. Ad alanı karmaları hakkında daha fazla bilgi için bkz. [veri sözleşmesi adları](data-contract-names.md).

Her sözlük toplama veri sözleşmesinin, Sözlükteki bir girişi temsil eden bir yardımcı veri sözleşmesi vardır. Adı, sözlük veri sözleşmesi ile aynıdır, "ArrayOf" öneki hariç ve ad alanı sözlük veri sözleşmesiyle aynı. Örneğin, "Arrayofkeyvalueofstringınt" Sözlük veri sözleşmesi için, "Keyvalueofstringınt" veri sözleşmesi sözlükte bir girişi temsil eder. Bu veri sözleşmesinin adını `ItemName` , sonraki bölümde açıklandığı gibi özelliğini kullanarak özelleştirebilirsiniz.

Genel tür adlandırma kuralları, [veri anlaşması adlarında](data-contract-names.md)açıklandığı gibi, koleksiyon türlerine tam olarak uygulanır; diğer bir deyişle, genel tür parametrelerini göstermek için ad içinde küme ayraçları kullanabilirsiniz. Ancak, küme ayraçları içindeki sayılar, koleksiyonda yer alan türler değil genel parametrelere başvurur.

## <a name="collection-customization"></a>Koleksiyon özelleştirmesi

Aşağıdaki <xref:System.Runtime.Serialization.CollectionDataContractAttribute> özniteliğin kullanımları yasaktır ve bir <xref:System.Runtime.Serialization.InvalidDataContractException> özel durumla sonuçlanır:

- Özniteliği, <xref:System.Runtime.Serialization.DataContractAttribute> <xref:System.Runtime.Serialization.CollectionDataContractAttribute> özniteliğin uygulandığı bir türe veya türetilen türlerden birine uygulama.

- <xref:System.Runtime.Serialization.CollectionDataContractAttribute>Özniteliğini arabirimini uygulayan bir türe uygulama <xref:System.Xml.Serialization.IXmlSerializable> .

- <xref:System.Runtime.Serialization.CollectionDataContractAttribute>Öznitelik koleksiyon olmayan bir türe uygulanıyor.

- <xref:System.Runtime.Serialization.CollectionDataContractAttribute.KeyName%2A> <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ValueName%2A> <xref:System.Runtime.Serialization.CollectionDataContractAttribute> Sözlük olmayan bir türe uygulanan bir özniteliği ayarlamaya çalışılıyor.

### <a name="polymorphism-rules"></a>Çok biçimlilik kuralları

Daha önce belirtildiği gibi, özniteliği kullanarak koleksiyonları özelleştirmek <xref:System.Runtime.Serialization.CollectionDataContractAttribute> koleksiyon interchangeability etkileyebilir. İki özelleştirilmiş koleksiyon türü yalnızca ad, ad alanı, öğe adı ve anahtar ve değer adları (sözlük koleksiyonları ise) eşleşiyorsa eşit kabul edilebilir.

Özelleştirmeler nedeniyle, başka bir koleksiyon veri sözleşmesinin beklenen bir şekilde kullanılması mümkündür. Bunun kaçınılması gerekir. Aşağıdaki türlere bakın.

[!code-csharp[c_collection_types_in_data_contracts#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#11)]
[!code-vb[c_collection_types_in_data_contracts#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#11)]

Bu durumda, öğesinin bir örneği `Marks1` atanabilir `testMarks` . Ancak, veri `Marks2` sözleşmesi veri sözleşmesine eşit kabul edilmediğinden kullanılmamalıdır `IList<int>` . Veri sözleşmesinin adı "Marks2" ve "Arrayofınt" değil ve yinelenen öğe adı "" ve "" değil \<mark> \<int> .

Aşağıdaki tablodaki kurallar, koleksiyonların çok biçimli atama için geçerlidir.

|Bildirilmeyen tür|Özelleştirilmemiş bir koleksiyon atama|Özelleştirilmiş bir koleksiyon atama|
|-------------------|--------------------------------------------|---------------------------------------|
|Nesne|Sözleşme adı serileştirilir.|Sözleşme adı serileştirilir.<br /><br /> Özelleştirme kullanılır.|
|Koleksiyon arabirimi|Sözleşme adı serileştirilmedi.|Sözleşme adı serileştirilmedi.<br /><br /> Özelleştirme kullanılmıyor.\*|
|Özelleştirilmeyen koleksiyon|Sözleşme adı serileştirilmedi.|Sözleşme adı serileştirilir.<br /><br /> Özelleştirme kullanılıyor. * *|
|Özelleştirilmiş koleksiyon|Sözleşme adı serileştirilir. Özelleştirme kullanılmıyor.\*\*|Sözleşme adı serileştirilir.<br /><br /> Atanan tür özelleştirmesi kullanılır.\*\*|

\*Sınıfı ile <xref:System.Runtime.Serialization.NetDataContractSerializer> , bu durumda özelleştirme kullanılır. <xref:System.Runtime.Serialization.NetDataContractSerializer>Sınıf Ayrıca bu durumda gerçek tür adını serileştirir, bu nedenle seri kaldırma beklendiği gibi çalışmaktadır.

\*\*Bu durumlar, şema geçersiz örneklerle sonuçlanır ve bu nedenle kaçınılmalıdır.

Anlaşma adının seri hale getirilme durumunda, atanan koleksiyon türü bilinen türler listesinde olmalıdır. Tersi de geçerlidir: adın seri hale getirilmediği durumlarda, türü bilinen türler listesine eklemek gerekli değildir.

Türetilmiş türdeki bir dizi, temel tür dizisine atanabilir. Bu durumda, türetilmiş türün anlaşma adı her bir yinelenen öğe için serileştirilir. Örneğin, bir tür türünden `Book` türetiliyor, dizisine bir `LibraryItem` dizisi atayabilirsiniz `Book` `LibraryItem` . Bu, diğer koleksiyon türleri için de geçerlidir. Örneğin, bir `Generic List of Book` öğesine atayamazsınız `Generic List of LibraryItem` . Bununla birlikte, örnek içeren bir de atayabilirsiniz `Generic List of LibraryItem` `Book` . Hem dizide hem de dizi olmayan durumda, `Book` bilinen türler listesinde olmalıdır.

## <a name="collections-and-object-reference-preservation"></a>Koleksiyonlar ve nesne başvuru koruması

Seri hale getirici, nesne başvurularını koruyan bir modda işlevler, nesne başvurusu koruması da koleksiyonlar için de geçerlidir. Özellikle, nesne kimliği tüm koleksiyonlar ve koleksiyonlarda bulunan bireysel öğeler için korunur. Sözlüklerde, nesne kimliği hem anahtar/değer çifti nesneleri hem de tek anahtar ve değer nesneleri için korunur.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Serialization.CollectionDataContractAttribute>
