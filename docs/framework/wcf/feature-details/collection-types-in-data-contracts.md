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
ms.openlocfilehash: 810238ee631808dac472456f910eb52f8bbf550c
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2019
ms.locfileid: "68363817"
---
# <a name="collection-types-in-data-contracts"></a>Veri Sözleşmelerinde Koleksiyon Türleri

*Koleksiyon* , belirli bir türdeki öğelerin listesidir. .NET Framework, bu tür listeler diziler veya diğer çeşitli türler (genel liste, genel <xref:System.ComponentModel.BindingList%601>, <xref:System.Collections.Specialized.StringCollection>veya <xref:System.Collections.ArrayList>) kullanılarak temsil edilebilir. Örneğin, bir koleksiyon belirli bir müşteri için adreslerin listesini tutabilir. Bu koleksiyonlara, gerçek türlerine bakılmaksızın *liste koleksiyonları*denir.

Bir öğe ("Key") ve diğeri ("Value") arasındaki ilişkiyi temsil eden özel bir koleksiyon biçimi vardır. .NET Framework, bunlar <xref:System.Collections.Hashtable> ve genel sözlük gibi türler tarafından temsil edilir. Örneğin, bir ilişki koleksiyonu bir şehri ("anahtar") kendi popülasyonu ("değer") ile eşleyebilir. Bu koleksiyonlara, gerçek türlerine bakılmaksızın *Sözlük koleksiyonları*denir.

Koleksiyonlar, veri anlaşması modelinde özel bir işleme alır.

Diziler ve genel Koleksiyonlar <xref:System.Collections.IEnumerable> dahil olmak üzere arabirimi uygulayan türler koleksiyonlar olarak tanınır. Bunlar, <xref:System.Collections.IDictionary> veya genel <xref:System.Collections.Generic.IDictionary%602> arabirimlerini uygulayan türler sözlük koleksiyonlarıdır; diğerleri liste koleksiyonlarıdır.

Koleksiyon türlerinde, bir yöntemi `Add` ve parametresiz bir oluşturucuyu olması gibi ek gereksinimler, aşağıdaki bölümlerde ayrıntılı olarak ele alınmıştır. Bu, koleksiyon türlerinin hem serileştirilmiş hem de seri durumdan çıkarılabilmesini sağlar. Bu, bazı koleksiyonların genel <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> (parametresiz oluşturucusu olmadığından) gibi doğrudan desteklenmediği anlamına gelir. Bununla birlikte, bu kısıtlamaları atlama hakkında daha fazla bilgi için bu konunun devamındaki "koleksiyon arabirim türleri ve salt okuma koleksiyonları kullanma" bölümüne bakın.

Koleksiyonlarda bulunan türlerin veri sözleşme türleri olması veya başka türlü seri hale getirilebilir olması gerekir. Daha fazla bilgi için bkz. [veri sözleşmesi serileştiricisi tarafından desteklenen türler](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md).

Ne olduğu ve geçerli bir koleksiyon olarak kabul edildiği hakkında daha fazla bilgi için, bu konunun "Gelişmiş koleksiyon kuralları" bölümünde koleksiyonları serileştirme hakkındaki bilgilere bakın.

## <a name="interchangeable-collections"></a>Değiştirilebilir Koleksiyonlar

Aynı türdeki tüm liste koleksiyonları aynı veri sözleşmesine sahip olacak şekilde değerlendirilir (Bu konunun ilerleyen kısımlarında açıklandığı gibi <xref:System.Runtime.Serialization.CollectionDataContractAttribute> özniteliği kullanılarak özelleştirilmedikleri sürece). Bu nedenle, örneğin, aşağıdaki veri sözleşmeleri eşdeğerdir.

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

Liste koleksiyonlarına benzer şekilde, aynı anahtar ve değer türlerine sahip tüm sözlük koleksiyonları aynı veri sözleşmesine sahip olacak şekilde değerlendirilir ( <xref:System.Runtime.Serialization.CollectionDataContractAttribute> özniteliği tarafından özelleştirilmediği müddetçe).

Yalnızca koleksiyon denklemesiyle ilgili olarak önemli olan veri sözleşmesi türü .NET türleri değildir. Diğer bir deyişle, type1 koleksiyonu, type1 ve type2 eşdeğer veri sözleşmeleri içeriyorsa bir type2 koleksiyonuna eşdeğer olarak kabul edilir.

Genel olmayan koleksiyonlar, türü `Object`genel koleksiyonlarla aynı veri sözleşmesine sahip olarak kabul edilir. (Örneğin, ve <xref:System.Collections.ArrayList> <xref:System.Collections.Generic.List%601> `Object` genel için veri sözleşmeleri aynıdır.)

## <a name="using-collection-interface-types-and-read-only-collections"></a>Koleksiyon arabirim türleri ve salt okunurdur koleksiyonları kullanma

Koleksiyon arabirim türleri (<xref:System.Collections.IEnumerable>, <xref:System.Collections.IDictionary>, genel <xref:System.Collections.Generic.IDictionary%602>veya bu arabirimlerden türetilmiş arabirimler), gerçek koleksiyon türleri için koleksiyon veri sözleşmeleri ile eşdeğer olan koleksiyon veri sözleşmeleri olarak da düşünülür. Bu nedenle, bir koleksiyon arabirim türü olarak serileştirilmekte olan türü bildirmek mümkündür ve sonuçlar gerçek bir koleksiyon türü kullanılmış gibi aynı olur. Örneğin, aşağıdaki veri sözleşmeleri eşdeğerdir.

[!code-csharp[c_collection_types_in_data_contracts#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#1)]
[!code-vb[c_collection_types_in_data_contracts#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#1)]

Serileştirme sırasında, belirtilen tür bir arabirim olduğunda, kullanılan gerçek örnek türü bu arabirimi uygulayan herhangi bir tür olabilir. Daha önce tartışılan kısıtlamalar (parametresiz bir oluşturucuya ve bir `Add` yönteme sahip) uygulanmaz. Örneğin, genel <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>türünde bir veri üyesini doğrudan bildiremeseniz bile Customer2 içindeki adresleri <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> genel bir adres örneğine ayarlayabilirsiniz.

Seri durumdan çıkarma sırasında, belirtilen tür bir arabirim olduğunda, serileştirme altyapısı, belirtilen arabirimi uygulayan bir tür seçer ve tür oluşturulur. Bilinen türler mekanizması ( [veri sözleşmesinin bilinen türlerinde](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)açıklanmıştır) burada hiçbir etkiye sahip değildir; tür seçimi WCF 'de yerleşik olarak bulunur.

## <a name="customizing-collection-types"></a>Koleksiyon türlerini özelleştirme

Koleksiyon türlerini, birkaç kullanımı bulunan <xref:System.Runtime.Serialization.CollectionDataContractAttribute> özniteliğini kullanarak özelleştirebilirsiniz.

Koleksiyon türlerini özelleştirme interchangeability koleksiyonu, bu nedenle bu özniteliği mümkün olduğunda uygulamaktan kaçınmak için genellikle önerilir. Bu sorun hakkında daha fazla bilgi için, bu konunun devamındaki "Gelişmiş koleksiyon kuralları" bölümüne bakın.

### <a name="collection-data-contract-naming"></a>Koleksiyon veri anlaşması adlandırma

Ad koleksiyon türlerini adlandırma kuralları, [veri anlaşması adlarında](../../../../docs/framework/wcf/feature-details/data-contract-names.md)açıklandığı şekilde, düzenli veri sözleşme türlerini adlandırmakla benzerdir, ancak bazı önemli farklılıklar vardır:

- Özniteliği, <xref:System.Runtime.Serialization.DataContractAttribute> özniteliği yerine adı özelleştirmek için kullanılır. <xref:System.Runtime.Serialization.CollectionDataContractAttribute> <xref:System.Runtime.Serialization.CollectionDataContractAttribute> Özniteliği `Name` ve özellikleri`Namespace` de vardır.

- <xref:System.Runtime.Serialization.CollectionDataContractAttribute> Özniteliği uygulandığında, koleksiyon türleri için varsayılan ad ve ad alanı, koleksiyonda bulunan türlerin adlarına ve ad alanlarına bağlıdır. Bunlar, koleksiyon türünün adı ve ad alanından etkilenmemektedir. Bir örnek için, aşağıdaki türlere bakın.

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

<xref:System.Runtime.Serialization.CollectionDataContractAttribute> Ancak öznitelik uygulandığında, öznitelik üzerinde hiçbir özellik ayarlanmamışsa bile koleksiyon özelleştirilmiş bir koleksiyon veri anlaşması haline gelir. Koleksiyon veri sözleşmesinin adı ve ad alanı, daha sonra koleksiyon türüne bağlıdır. Bir örnek için, aşağıdaki türe bakın.

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

- `Name` Ve`Namespace` özelliklerini kullanarak adlandırmanın daha fazla özelleştirmesini sağlayabilirsiniz. Aşağıdaki sınıfa bakın.

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

`CustomerList` Örneklerde, Koleksiyonlar dizeler içeriyordu. Dize ilkel türü için veri sözleşmesi adı "String" olduğundan, yinelenen öğe "\<String >" idi.

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

Yinelenen öğenin ad alanı her zaman koleksiyon veri sözleşmesinin ad alanıyla aynıdır ve bu, daha önce açıklandığı gibi `Namespace` özelliği kullanılarak özelleştirilebilir.

### <a name="customizing-dictionary-collections"></a>Sözlük koleksiyonlarını özelleştirme

Sözlük koleksiyonları, her girdinin bir anahtara ve ardından bir değere sahip olduğu, temel olarak giriş listesidir. Normal listelerle olduğu gibi, <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> özelliğini kullanarak, yinelenen öğeye karşılık gelen öğe adını değiştirebilirsiniz.

Ayrıca, <xref:System.Runtime.Serialization.CollectionDataContractAttribute.KeyName%2A> ve <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ValueName%2A> özelliklerini kullanarak anahtar ve değeri temsil eden öğe adlarını değiştirebilirsiniz. Bu öğelerin ad alanları, koleksiyon veri sözleşmesinin ad alanıyla aynıdır.

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

Diğer koleksiyonların veya koleksiyon arabirimlerinin yerine polymorphically kullandığınızda, bilinen türlere koleksiyon türleri eklemeniz gerekmez. Örneğin, türünde <xref:System.Collections.IEnumerable> bir veri üyesi bildirirseniz ve <xref:System.Collections.ArrayList>örneğini göndermek için kullanırsanız, bilinen türlere eklemeniz <xref:System.Collections.ArrayList> gerekmez.

Koleksiyon olmayan türlerin yerine koleksiyonlar polymorphically kullandığınızda, bunların bilinen türlere eklenmesi gerekir. Örneğin, türünde `Object` bir veri üyesi bildirirseniz ve <xref:System.Collections.ArrayList>örneğini göndermek için kullanıyorsa, bilinen türlere ekleyin <xref:System.Collections.ArrayList> .

Bu, herhangi bir eşdeğer koleksiyon polymorphically seri hale getirme yapmanıza izin vermez. Örneğin, önceki örnekteki bilinen türler <xref:System.Collections.ArrayList> listesine eklediğinizde, bu, denk bir veri sözleşmesine sahip olsa bile `Array of Object` sınıfı atamanıza izin vermez. Bu, koleksiyon dışı türler için serileştirme üzerinde düzenli olarak bilinen türler davranışından farklı değildir, ancak koleksiyonların büyük bir olasılıkla daha yaygın olması nedeniyle koleksiyonlar durumunda anlaşılması özellikle önemlidir.

Serileştirme sırasında, belirli bir veri sözleşmesi için verilen herhangi bir kapsamda yalnızca bir tür tanınverilebilir ve eşdeğer koleksiyonların hepsi aynı veri sözleşmelerine sahiptir. Bu, önceki örnekte, hem hem de <xref:System.Collections.ArrayList> `Array of Object` bilinen türleri aynı kapsamda ekleyemeyeceğiniz anlamına gelir. Bu, koleksiyon olmayan türler için bilinen türler davranışına eşdeğerdir, ancak koleksiyonlar için anlaşılması özellikle önemlidir.

Bilinen türler, koleksiyonların içerikleri için de gerekli olabilir. Örneğin, <xref:System.Collections.ArrayList> aslında `Type1` ve `Type2`örnekleri içeriyorsa, bu türlerin her ikisi de bilinen türlere eklenmelidir.

Aşağıdaki örnek, koleksiyonlar ve bilinen türler kullanılarak düzgün şekilde oluşturulmuş bir nesne grafiğini gösterir. Örnek biraz contrived, çünkü gerçek bir uygulamada normalde aşağıdaki veri üyelerini olarak `Object`tanımlamaz ve bu nedenle bilinen tür/çok biçimlilik sorunları yoktur.

[!code-csharp[c_collection_types_in_data_contracts#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#6)]
[!code-vb[c_collection_types_in_data_contracts#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#6)]

Seri durumdan çıkarma sırasında, belirtilen tür bir koleksiyon türüdür, gönderilen tür, gerçekten gönderilen türden bağımsız olarak oluşturulur. Belirtilen tür bir koleksiyon arabirimse, seri hale getirici, bilinen türler açısından, örnek oluşturulacak bir tür seçer.

Ayrıca, seri durumdan çıkarma sırasında, belirtilen tür bir koleksiyon türü değilse ancak bir koleksiyon türü gönderiliyorsa, bilinen türler listesinden eşleşen bir koleksiyon türü alınır. Seri durumdan çıkarma sırasında bilinen türler listesine koleksiyon arabirim türleri eklemek mümkündür. Bu durumda, seri durumdan çıkarma altyapısı, örnek oluşturulacak bir tür seçer.

## <a name="collections-and-the-netdatacontractserializer-class"></a>Koleksiyonlar ve NetDataContractSerializer sınıfı

Sınıf kullanımda olduğunda, dizi olmayan özelleştirilmemiş koleksiyon türleri ( <xref:System.Runtime.Serialization.CollectionDataContractAttribute> özniteliği olmadan) özel anlamlarını kaybeder. <xref:System.Runtime.Serialization.NetDataContractSerializer>

<xref:System.SerializableAttribute> Özniteliği ile işaretlenen özelleştirilmemiş koleksiyon türleri, <xref:System.SerializableAttribute> özniteliğe veya <xref:System.Runtime.Serialization.ISerializable> arabirim kurallarına göre <xref:System.Runtime.Serialization.NetDataContractSerializer> sınıf tarafından yine de seri hale getirilebilir.

<xref:System.Runtime.Serialization.NetDataContractSerializer> Sınıf kullanımda olsa bile, özelleştirilmiş koleksiyon türleri, koleksiyon arabirimleri ve diziler hala koleksiyonlar olarak değerlendirilir.

## <a name="collections-and-schema"></a>Koleksiyonlar ve şema

Tüm eşdeğer koleksiyonlar, XML şeması tanım dili (XSD) şemasında aynı temsilde sahiptir. Bu nedenle, normalde, oluşturulan istemci kodunda, sunucuda bulunan bir koleksiyon türünü almaz. Örneğin, sunucu bir veri sözleşmesini genel <xref:System.Collections.Generic.List%601> tamsayı veri üyesi ile kullanabilir, ancak oluşturulan istemci kodunda aynı veri üyesi bir tamsayılar dizisi haline gelebilir.

Sözlük koleksiyonları, sözlüklerin olduğunu belirten, WCF 'ye özgü bir şema ek açıklaması ile işaretlenir; Aksi takdirde, anahtar ve değer içeren girişleri içeren basit listelerden ayırt edilemez. Koleksiyonların veri sözleşmesi şemasında nasıl temsil edildiği hakkında tam bir açıklama için bkz. [veri sözleşmesi şema başvurusu](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md).

Varsayılan olarak, içeri aktarılan koddaki özelleştirilmemiş koleksiyonlar için türler oluşturulmaz. Liste koleksiyonu türlerinin veri üyeleri diziler olarak içeri aktarılır ve sözlük toplama türlerinin veri üyeleri genel sözlük olarak içeri aktarılır.

Ancak, özelleştirilmiş koleksiyonlar için, <xref:System.Runtime.Serialization.CollectionDataContractAttribute> özniteliğiyle işaretlenen ayrı türler oluşturulur. (Şemadaki özelleştirilmiş bir koleksiyon türü, varsayılan ad alanı, ad, yinelenen öğe adı veya anahtar/değer öğesi adlarını kullanmayan bir öğedir.) Bu türler, liste türleri ve sözlük türleri için <xref:System.Collections.Generic.List%601> genel sözlük için genel 'den türetilen boş türlerdir.

Örneğin, sunucusunda aşağıdaki türlere sahip olabilirsiniz.

[!code-csharp[c_collection_types_in_data_contracts#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#7)]
[!code-vb[c_collection_types_in_data_contracts#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#7)]

Şema verildiğinde ve geri aktarıldığında, oluşturulan istemci kodu aşağıdakine benzerdir (okuma kolaylığı için özellikler yerine alanlar gösterilir).

[!code-csharp[c_collection_types_in_data_contracts#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#8)]
[!code-vb[c_collection_types_in_data_contracts#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#8)]

Oluşturulan kodda varsayılan olanlardan farklı türler kullanmak isteyebilirsiniz. Örneğin, Kullanıcı arabirimi bileşenlerine bağlamayı kolaylaştırmak için veri <xref:System.ComponentModel.BindingList%601> üyelerinize ait normal diziler yerine genel ' i kullanmak isteyebilirsiniz.

Oluşturulacak koleksiyon türlerini seçmek için şemayı içeri aktarırken <xref:System.Runtime.Serialization.ImportOptions.ReferencedCollectionTypes%2A> <xref:System.Runtime.Serialization.ImportOptions> nesnenin özelliğine kullanmak istediğiniz koleksiyon türlerinin bir listesini geçirin. Bu türlere *başvurulan koleksiyon türleri*denir.

Genel türlere başvurulduklarında, bunların tamamen açık genel türler veya tam kapalı genel türler olması gerekir.

> [!NOTE]
> Svcutil. exe aracını kullanırken, bu başvuru **/CollectionType** komut satırı anahtarı kullanılarak gerçekleştirilebilir (kısa biçim: **/CT**). Ayrıca, **/Reference** anahtarını kullanarak başvurulan koleksiyon türleri için derlemeyi belirtmeniz gerektiğini unutmayın (kısa biçim: **/r**). Tür geneldir ise, arkasından bir geri tırnak işareti ve genel parametre sayısı gelmelidir. Arka tırnak (\`), tek tırnak (') karakteriyle karıştırılmamalıdır. **/CollectionType** anahtarını birden çok kez kullanarak, birden fazla başvurulan koleksiyon türünü belirtebilirsiniz.

Örneğin, tüm listelerin genel <xref:System.Collections.Generic.List%601>olarak içeri aktarılmasını sağlamak için.

```console
svcutil.exe MyService.wsdl MyServiceSchema.xsd /r:C:\full_path_to_system_dll\System.dll /ct:System.Collections.Generic.List`1
```

Herhangi bir koleksiyonu içeri aktarırken, başvurulan koleksiyon türlerinin bu listesi taranır ve bir veri üyesi türü (özelleştirilmemiş koleksiyonlar için) veya türetilmek üzere temel bir tür olarak bulunursa en iyi eşleşen koleksiyon kullanılır (özelleştirilmiş koleksiyonlar için). Sözlükler yalnızca sözlüklere göre eşleşir, ancak listeler listelerle eşleştirilir.

Örneğin, genel <xref:System.ComponentModel.BindingList%601> ve <xref:System.Collections.Hashtable> başvurulan türler listesine eklerseniz, önceki örnek için oluşturulan istemci kodu aşağıdakine benzerdir.

[!code-csharp[c_collection_types_in_data_contracts#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#9)]
[!code-vb[c_collection_types_in_data_contracts#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#9)]

Koleksiyon arabirimi türlerini, başvurulan koleksiyon türlerinizin bir parçası olarak belirtebilirsiniz, ancak geçersiz koleksiyon türleri belirtemezsiniz (hiçbir yöntem veya ortak Oluşturucu olmayan `Add` gibi).

Kapalı bir genel, en iyi eşleşme olarak kabul edilir. (Genel olmayan türler kapalı genel `Object`türlerine eşdeğer olarak kabul edilir). Örneğin <xref:System.Collections.Generic.List%601> , genel <xref:System.DateTime> <xref:System.Collections.ArrayList> türleri genel (Genel açık) ise ve başvurulan koleksiyon türse, aşağıdakiler oluşturulur. <xref:System.ComponentModel.BindingList%601>

[!code-csharp[c_collection_types_in_data_contracts#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#10)]
[!code-vb[c_collection_types_in_data_contracts#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#10)]

Liste koleksiyonları için yalnızca aşağıdaki tablodaki durumlar desteklenir.

|Başvurulan tür|Başvurulan tür tarafından uygulanan arabirim|Örnek|Tür şöyle işlenir:|
|---------------------|----------------------------------------------|-------------|----------------------|
|Genel olmayan veya kapalı genel (herhangi bir sayıda parametre)|Genel olmayan|`MyType : IList`<br /><br /> veya<br /><br /> `MyType<T> : IList`<br /><br /> Burada T =`int`|Kapalı genel `Object` (örneğin, `IList<object>`)|
|Genel olmayan veya kapalı genel (koleksiyon türüyle eşleşmesi gerekmeyen parametre sayısı)|Kapalı genel|`MyType : IList<string>`<br /><br /> veya<br /><br /> `MyType<T> : IList<string>`Burada T =`int`|Kapalı genel (örneğin, `IList<string>`)|
|Herhangi bir sayıda parametreyle Genel kapalı|Tür parametrelerinden herhangi birini kullanarak genel ' i açın|`MyType<T,U,V> : IList<U>`<br /><br /> Burada T =`int`, U =`string`, V =`bool`|Kapalı genel (örneğin, `IList<string>`)|
|Genel 'i tek bir parametreyle aç|Türün parametresini kullanarak genel ' i açın|`MyType<T> : IList<T>`, T açık|Genel açık (örneğin, `IList<T>`)|

Bir tür birden fazla liste koleksiyonu arabirimi uygularsa, aşağıdaki kısıtlamalar geçerlidir:

- Tür, farklı türlerde genel <xref:System.Collections.Generic.IEnumerable%601> (veya türetilen arabirimlerini) birden çok kez uygularsa, tür geçerli bir başvurulan koleksiyon türü olarak kabul edilmez ve yok sayılır. Bu, bazı uygulamalar geçersiz olsa bile veya açık genel türler kullanıyorsa geçerlidir. Örneğin <xref:System.Collections.Generic.IEnumerable%601> , genel <xref:System.Collections.Generic.IEnumerable%601> `int` ' i ve genel ' i uygulayan bir tür, bir `Add` tür `int` veya kabul eden bir yöntem olmasına bakılmaksızın hiçbir şekilde başvurulan bir koleksiyon ya da başka bir tür olarak kullanılamaz. ya da `Add` T türünde bir parametre kabul eden bir yöntem ya da her ikisi. `int`

- Tür bir genel koleksiyon arabirimini de <xref:System.Collections.IList>uygularsa, genel koleksiyon arabirimi türü <xref:System.Object>kapalı bir genel değilse tür hiçbir şekilde başvurulan koleksiyon türü olarak kullanılmaz.

Sözlük koleksiyonları için yalnızca aşağıdaki tablodaki durumlar desteklenir.

|Başvurulan tür|Başvurulan tür tarafından uygulanan arabirim|Örnek|Tür olarak değerlendirildi|
|---------------------|----------------------------------------------|-------------|---------------------|
|Genel olmayan veya kapalı genel (herhangi bir sayıda parametre)|<xref:System.Collections.IDictionary>|`MyType : IDictionary`<br /><br /> veya<br /><br /> `MyType<T> : IDictionary`Burada T =`int`|Kapalı genel`IDictionary<object,object>`|
|Kapalı genel (herhangi bir sayıda parametre)|<xref:System.Collections.Generic.IDictionary%602>, kapalı|`MyType<T> : IDictionary<string, bool>`Burada T =`int`|Kapalı genel (örneğin, `IDIctionary<string,bool>`)|
|Kapalı genel (herhangi bir sayıda parametre)|Genel <xref:System.Collections.Generic.IDictionary%602>, herhangi bir anahtar veya değerden biri kapalı, diğeri açık ve türün parametrelerinden birini kullanıyor|`MyType<T,U,V> : IDictionary<string,V>`Burada T =`int`, U =`float`, V =`bool`<br /><br /> veya<br /><br /> `MyType<Z> : IDictionary<Z,bool>`Burada Z =`string`|Kapalı genel (örneğin, `IDictionary<string,bool>`)|
|Kapalı genel (herhangi bir sayıda parametre)|Genel <xref:System.Collections.Generic.IDictionary%602>, her iki anahtar ve değer açıktır ve her biri türün parametrelerinden birini kullanır|`MyType<T,U,V> : IDictionary<V,U>`Burada T =`int`, U =`bool`, V =`string`|Kapalı genel (örneğin, `IDictionary<string,bool>`)|
|Açık genel (iki parametre)|Genel <xref:System.Collections.Generic.IDictionary%602>, açık, her iki türün genel parametrelerini göründükleri sırada kullanır|`MyType<K,V> : IDictionary<K,V>`, K ve V her ikisi açık|Genel açık (örneğin, `IDictionary<K,V>`)|

Tür hem hem de <xref:System.Collections.IDictionary> generic <xref:System.Collections.Generic.IDictionary%602>uygularsa, yalnızca genel <xref:System.Collections.Generic.IDictionary%602> olarak kabul edilir.

Kısmi Genel türlere başvurulması desteklenmez.

Yinelenen öğelere izin verilmez, örneğin, <xref:System.Collections.Generic.List%601> ' ın hem genel `Integer` `Integer` hem de genel koleksiyonunu <xref:System.Runtime.Serialization.ImportOptions.ReferencedCollectionTypes%2A>' a ekleyemezsiniz; çünkü bu, bir tamsayılar listesi bulunduğunda hangisini kullanacağınızı belirlemeyi olanaksız kılar şemaya. Yinelemeler, yalnızca şemada yinelenen sorunları ortaya çıkaran bir tür varsa algılanır. Örneğin, içeri aktarılan şema tamsayılar listesini içermiyorsa <xref:System.Collections.Generic.List%601> , içinde <xref:System.Runtime.Serialization.ImportOptions.ReferencedCollectionTypes%2A>öğesinin `Integer` hem genel `Integer` hem de genel koleksiyonuna sahip olmasına izin verilir, ancak hiçbir etkisi yoktur.

## <a name="advanced-collection-rules"></a>Gelişmiş koleksiyon kuralları

### <a name="serializing-collections"></a>Koleksiyonlar serileştiriliyor

Serileştirme için koleksiyon kurallarının bir listesi aşağıda verilmiştir:

- Koleksiyon türlerini (koleksiyon koleksiyonlarına sahip) birleştirmek için izin verilir. Pürüzlü Diziler koleksiyonların koleksiyonları olarak değerlendirilir. Çok boyutlu diziler desteklenmiyor.

- Bayt ve dizi <xref:System.Xml.XmlNode> dizileri, Koleksiyonlar değil, temel öğeler olarak kabul edilen özel dizi türlerdir. Bir bayt dizisini seri hale getirmek, her bayt için ayrı bir öğe yerine Base64 kodlamalı verilerin bir öbeğini içeren tek bir XML öğesinde sonuçlanır. Dizisinin <xref:System.Xml.XmlNode> nasıl işlendiği hakkında daha fazla bilgi için bkz. [Data Contracts 'de XML ve ADO.net Types](../../../../docs/framework/wcf/feature-details/xml-and-ado-net-types-in-data-contracts.md). Tabii ki, bu özel türler kendilerine katılabilirler: bir bayt dizisi dizisi, her biri Base64 kodlamalı verilerin bir öbeğini içeren birden çok XML öğesiyle sonuçlanır.

- <xref:System.Runtime.Serialization.DataContractAttribute> Öznitelik bir koleksiyon türüne uygulanırsa, tür bir koleksiyon olarak değil, düzenli bir veri anlaşması türü olarak değerlendirilir.

- Bir koleksiyon türü <xref:System.Xml.Serialization.IXmlSerializable> arabirimini uyguluyorsa, aşağıdaki kurallar bir tür `myType:IList<string>, IXmlSerializable`verildiğinde geçerlidir:

  - Belirtilen tür ise `IList<string>`, tür bir liste olarak serileştirilir.

  - Belirtilen tür ise `myType`olarak `IXmlSerializable`serileştirilir.

  - Belirtilen tür ise `IXmlSerializable`, ancak yalnızca bilinen türler listesine eklediğinizde `IXmlSerializable` `myType` olarak serileştirilir.

- Koleksiyonlar serileştirilir ve aşağıdaki tabloda gösterilen yöntemler kullanılarak seri durumdan çıkarılmakta.

|Koleksiyon türü uygular|Serileştirme sırasında çağrılan Yöntem (ler)|Seri durumdan çıkarma sırasında çağrılan metot (ler)|
|--------------------------------|-----------------------------------------|-------------------------------------------|
|Yorlar<xref:System.Collections.Generic.IDictionary%602>|`get_Keys`, `get_Values`|Genel ekleme|
|<xref:System.Collections.IDictionary>|`get_Keys`, `get_Values`|`Add`|
|Yorlar<xref:System.Collections.Generic.IList%601>|Genel <xref:System.Collections.Generic.IList%601> Dizin Oluşturucu|Genel ekleme|
|Yorlar<xref:System.Collections.Generic.ICollection%601>|Sının|Genel ekleme|
|<xref:System.Collections.IList>|<xref:System.Collections.IList>Dizinleyic|`Add`|
|Yorlar<xref:System.Collections.Generic.IEnumerable%601>|`GetEnumerator`|Uygun türde (genel parametrenin türü `Add` veya temel türlerinden biri) bir parametre alan, statik olmayan bir yöntem. Seri hale getirici, hem serileştirme hem de seri durumundan çıkarma sırasında koleksiyon türünü bir koleksiyon olarak değerlendirmek için bu tür bir yöntem bulunmalıdır.|
|<xref:System.Collections.IEnumerable>(ve bu <xref:System.Collections.ICollection>nedenle ondan türetilen)|`GetEnumerator`|`Add` Türünde`Object`bir parametre alan, statik olmayan bir yöntem. Seri hale getirici, hem serileştirme hem de seri durumundan çıkarma sırasında koleksiyon türünü bir koleksiyon olarak değerlendirmek için bu tür bir yöntem bulunmalıdır.|

Yukarıdaki tabloda, koleksiyon arabirimleri azalan öncelik sırasına göre listelenmiştir. Bu, örneğin, bir tür hem hem de <xref:System.Collections.IList> generic <xref:System.Collections.Generic.IEnumerable%601>uygularsa, koleksiyonun serileştirildiği <xref:System.Collections.IList> ve bu kurallara göre seri durumdan çıkarılmasıdır.

- Seri durumdan çıkarma sırasında, seri hale getiricinin her iki serileştirme de bir koleksiyon olarak bir koleksiyon olarak değerlendirmek için mevcut olması gereken parametresiz oluşturucuyu çağırarak, önce bir türün örneği oluşturularak, tüm koleksiyonların serisi kaldırılır. seri.

- Aynı genel koleksiyon arabirimi birden çok kez uygulanırsa (örneğin, <xref:System.Collections.Generic.ICollection%601> bir tür hem genel `Integer` hem de genel <xref:System.Collections.Generic.ICollection%601> <xref:System.String>' i uygularsa) ve daha yüksek öncelikli bir arabirim bulunamazsa, koleksiyon geçerli bir koleksiyon olarak değerlendirilmez.

- Koleksiyon türlerinde, <xref:System.SerializableAttribute> özniteliğe uygulanan özniteliği bulunabilir ve <xref:System.Runtime.Serialization.ISerializable> arabirimi uygulayabilir. Bunların her ikisi de yok sayılır. Ancak, tür koleksiyon türü gereksinimlerini tam olarak karşılamıyorsa (örneğin, `Add` yöntemi eksikse), tür bir koleksiyon türü olarak kabul edilmez ve bu <xref:System.SerializableAttribute> nedenle öznitelik ve <xref:System.Runtime.Serialization.ISerializable> arabirim, türün seri hale getirilebilir olup olmadığı.

- Özniteliğini özelleştirmek için bir koleksiyona özniteliği uygulamak, <xref:System.SerializableAttribute> önceki geri dönüş mekanizmasını kaldırır. <xref:System.Runtime.Serialization.CollectionDataContractAttribute> Bunun yerine, özelleştirilmiş bir koleksiyon koleksiyon türü gereksinimlerini karşılamıyorsa, bir <xref:System.Runtime.Serialization.InvalidDataContractException> özel durum oluşturulur. Özel durum dizesi genellikle belirli bir türün geçerli bir koleksiyon (hiçbir yöntem yok `Add` , parametresiz Oluşturucu vb.) olarak değerlendirilmediğini açıklayan bilgileri içerir. bu nedenle, genellikle hata ayıklama için <xref:System.Runtime.Serialization.CollectionDataContractAttribute> özniteliği uygulamak yararlı olur çalışmaları.

### <a name="collection-naming"></a>Koleksiyon adlandırma

Aşağıda, koleksiyon adlandırma kurallarının bir listesi verilmiştir:

- Tüm sözlük toplama verileri sözleşmeleri için varsayılan ad alanı ve temel türler `http://schemas.microsoft.com/2003/10/Serialization/Arrays` içeren liste toplama veri sözleşmeleri için ad alanı kullanılarak geçersiz kılınmadığı sürece. Yerleşik xsd türlerine `char`ve, `Timespan`ve `Guid` türlerine eşlenen türler, bu amaçla temel elemanlar olarak kabul edilir.

- Ad alanı kullanılarak geçersiz kılınmadığı sürece, ilkel olmayan türler içeren koleksiyon türleri için varsayılan ad alanı, koleksiyonda yer alan türdeki veri sözleşmesi ad alanıyla aynıdır.

- Ad kullanılarak geçersiz kılınmadığı takdirde, liste toplama veri sözleşmeleri için varsayılan ad, koleksiyonda bulunan türün veri sözleşmesi adıyla birlikte "ArrayOf" dizesidir. Örneğin, genel tamsayılar listesinin veri sözleşme adı "Arrayofınt" ' dir. Veri sözleşmesi adının `Object` "anyType" olduğunu ve bu nedenle genel olmayan <xref:System.Collections.ArrayList> listelerin veri sözleşmesi adının "ArrayOfanyType" olduğunu aklınızda bulundurun.

Sözlük toplama veri sözleşmeleri için varsayılan ad, kullanılarak `Name`geçersiz kılınmamışsa, anahtar türünün veri sözleşmesi adı ile birleştirilmiş "arrayofkeyary" dizesidir ve ardından değer türünün veri sözleşmesi adı gelir. Örneğin, bir dize ve tamsayı genel sözlüğünün veri sözleşme adı "Arrayofkeyvalueofstringınt" ' dir. Ayrıca, anahtar veya değer türleri basit türler değilse, anahtar ve değer türlerinin veri sözleşmesi ad alanlarının ad alanı karması ada eklenir. Ad alanı karmaları hakkında daha fazla bilgi için bkz. [veri sözleşmesi adları](../../../../docs/framework/wcf/feature-details/data-contract-names.md).

Her sözlük toplama veri sözleşmesinin, Sözlükteki bir girişi temsil eden bir yardımcı veri sözleşmesi vardır. Adı, sözlük veri sözleşmesi ile aynıdır, "ArrayOf" öneki hariç ve ad alanı sözlük veri sözleşmesiyle aynı. Örneğin, "Arrayofkeyvalueofstringınt" Sözlük veri sözleşmesi için, "Keyvalueofstringınt" veri sözleşmesi sözlükte bir girişi temsil eder. Bu veri sözleşmesinin adını, sonraki bölümde açıklandığı gibi `ItemName` özelliğini kullanarak özelleştirebilirsiniz.

Genel tür adlandırma kuralları, [veri anlaşması adlarında](../../../../docs/framework/wcf/feature-details/data-contract-names.md)açıklandığı gibi, koleksiyon türlerine tam olarak uygulanır; diğer bir deyişle, genel tür parametrelerini göstermek için ad içinde küme ayraçları kullanabilirsiniz. Ancak, küme ayraçları içindeki sayılar, koleksiyonda yer alan türler değil genel parametrelere başvurur.

## <a name="collection-customization"></a>Koleksiyon özelleştirmesi

Aşağıdaki <xref:System.Runtime.Serialization.CollectionDataContractAttribute> özniteliğin kullanımları yasaktır ve bir <xref:System.Runtime.Serialization.InvalidDataContractException> özel durumla sonuçlanır:

- Özniteliği, <xref:System.Runtime.Serialization.CollectionDataContractAttribute> özniteliğin uygulandığı bir türe veya türetilen türlerden birine uygulama. <xref:System.Runtime.Serialization.DataContractAttribute>

- <xref:System.Runtime.Serialization.CollectionDataContractAttribute> Özniteliğini arabirimini<xref:System.Xml.Serialization.IXmlSerializable> uygulayan bir türe uygulama.

- <xref:System.Runtime.Serialization.CollectionDataContractAttribute> Öznitelik koleksiyon olmayan bir türe uygulanıyor.

- Sözlük olmayan bir <xref:System.Runtime.Serialization.CollectionDataContractAttribute.KeyName%2A> türe <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ValueName%2A> uygulanan bir <xref:System.Runtime.Serialization.CollectionDataContractAttribute> özniteliği ayarlamaya çalışılıyor.

### <a name="polymorphism-rules"></a>Çok biçimlilik kuralları

Daha önce belirtildiği gibi, <xref:System.Runtime.Serialization.CollectionDataContractAttribute> özniteliği kullanarak koleksiyonları özelleştirmek koleksiyon interchangeability etkileyebilir. İki özelleştirilmiş koleksiyon türü yalnızca ad, ad alanı, öğe adı ve anahtar ve değer adları (sözlük koleksiyonları ise) eşleşiyorsa eşit kabul edilebilir.

Özelleştirmeler nedeniyle, başka bir koleksiyon veri sözleşmesinin beklenen bir şekilde kullanılması mümkündür. Bunun kaçınılması gerekir. Aşağıdaki türlere bakın.

[!code-csharp[c_collection_types_in_data_contracts#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#11)]
[!code-vb[c_collection_types_in_data_contracts#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#11)]

Bu durumda, öğesinin `Marks1` bir örneği `testMarks`atanabilir. Ancak, `Marks2` veri sözleşmesi `IList<int>` veri sözleşmesine eşit kabul edilmediğinden kullanılmamalıdır. Veri sözleşmesinin adı "Marks2" ve "arrayofınt" değil, yinelenen öğe adı\<"Mark >" ve "\<int >" değil.

Aşağıdaki tablodaki kurallar, koleksiyonların çok biçimli atama için geçerlidir.

|Bildirilmeyen tür|Özelleştirilmemiş bir koleksiyon atama|Özelleştirilmiş bir koleksiyon atama|
|-------------------|--------------------------------------------|---------------------------------------|
|Nesne|Sözleşme adı serileştirilir.|Sözleşme adı serileştirilir.<br /><br /> Özelleştirme kullanılır.|
|Koleksiyon arabirimi|Sözleşme adı serileştirilmedi.|Sözleşme adı serileştirilmedi.<br /><br /> Özelleştirme kullanılmıyor.\*|
|Özelleştirilmeyen koleksiyon|Sözleşme adı serileştirilmedi.|Sözleşme adı serileştirilir.<br /><br /> Özelleştirme kullanılıyor. * *|
|Özelleştirilmiş koleksiyon|Sözleşme adı serileştirilir. Özelleştirme kullanılmıyor.\*\*|Sözleşme adı serileştirilir.<br /><br /> Atanan tür özelleştirmesi kullanılır.\*\*|

\*<xref:System.Runtime.Serialization.NetDataContractSerializer> Sınıfı ile, bu durumda özelleştirme kullanılır. <xref:System.Runtime.Serialization.NetDataContractSerializer> Sınıf Ayrıca bu durumda gerçek tür adını serileştirir, bu nedenle seri kaldırma beklendiği gibi çalışmaktadır.

\*\*Bu durumlar, şema geçersiz örneklerle sonuçlanır ve bu nedenle kaçınılmalıdır.

Anlaşma adının seri hale getirilme durumunda, atanan koleksiyon türü bilinen türler listesinde olmalıdır. Tersi de geçerlidir: adın seri hale getirilmediği durumlarda, türü bilinen türler listesine eklemek gerekli değildir.

Türetilmiş türdeki bir dizi, temel tür dizisine atanabilir. Bu durumda, türetilmiş türün anlaşma adı her bir yinelenen öğe için serileştirilir. Örneğin `Book` , bir tür türünden türetiliyor `LibraryItem`, dizisine bir dizisi `Book` `LibraryItem`atayabilirsiniz. Bu, diğer koleksiyon türleri için de geçerlidir. Örneğin, bir `Generic List of Book` `Generic List of LibraryItem`öğesine atayamazsınız. Bununla birlikte, örnek içeren `Generic List of LibraryItem` `Book` bir de atayabilirsiniz. Hem dizide hem de dizi olmayan durumda, `Book` bilinen türler listesinde olmalıdır.

## <a name="collections-and-object-reference-preservation"></a>Koleksiyonlar ve nesne başvuru koruması

Seri hale getirici, nesne başvurularını koruyan bir modda işlevler, nesne başvurusu koruması da koleksiyonlar için de geçerlidir. Özellikle, nesne kimliği tüm koleksiyonlar ve koleksiyonlarda bulunan bireysel öğeler için korunur. Sözlüklerde, nesne kimliği hem anahtar/değer çifti nesneleri hem de tek anahtar ve değer nesneleri için korunur.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Serialization.CollectionDataContractAttribute>
