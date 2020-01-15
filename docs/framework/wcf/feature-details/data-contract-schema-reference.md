---
title: Veri Sözleşmesi Şema Başvurusu
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts [WCF], schema reference
ms.assetid: 9ebb0ebe-8166-4c93-980a-7c8f1f38f7c0
ms.openlocfilehash: af183fa02ea3ec98f316979198624351d9b25f21
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/15/2020
ms.locfileid: "75963365"
---
# <a name="data-contract-schema-reference"></a>Veri Sözleşmesi Şema Başvurusu

Bu konu, XML serileştirmesi için ortak dil çalışma zamanı (CLR) türlerini tarif etmek üzere <xref:System.Runtime.Serialization.DataContractSerializer> tarafından kullanılan XML şemasının (XSD) alt kümesini açıklar.

## <a name="datacontractserializer-mappings"></a>DataContractSerializer eşlemeleri

`DataContractSerializer` meta veriler, meta veri uç noktası veya [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)kullanılarak bir WINDOWS COMMUNICATION FOUNDATION (WCF) HIZMETINDEN aktarıldığında CLR türlerini xsd ile eşler. Daha fazla bilgi için bkz. [veri sözleşmesi serileştiricisi](../../../../docs/framework/wcf/feature-details/data-contract-serializer.md).

Ayrıca, Web Hizmetleri Açıklama Dili (WSDL) veya XSD belgelerine erişmek ve hizmetler veya istemciler için veri sözleşmeleri oluşturmak için Svcutil. exe kullanıldığında `DataContractSerializer` XSD 'yi CLR türlerine eşler.

Yalnızca bu belgede belirtilen gereksinimlere uyan XML şema örnekleri, `DataContractSerializer`kullanılarak CLR türleriyle eşleştirilebilir.

### <a name="support-levels"></a>Destek Düzeyleri

`DataContractSerializer`, belirli bir XML şeması özelliği için aşağıdaki destek düzeylerini sağlar:

- **Desteklenir**. `DataContractSerializer`kullanarak bu özellikten CLR türlerine veya özniteliklerine (ya da her ikisine) açık eşleme vardır.

- **Yoksayıldı**. Özelliğe `DataContractSerializer`tarafından içeri aktarılan şemalarda izin verilir, ancak kod üretimi üzerinde hiçbir etkisi yoktur.

- **Yasak**. `DataContractSerializer`, özelliği kullanarak bir şemanın içeri aktarılmasını desteklemez. Örneğin, bu tür bir özelliği kullanan bir şemaya sahip bir WSDL 'ye erişirken Svcutil. exe, bunun yerine <xref:System.Xml.Serialization.XmlSerializer> kullanmaya geri döner. Bu varsayılan olarak olur.

## <a name="general-information"></a>Genel Bilgiler

- Şema ad alanı [XML şemasında](https://www.w3.org/2001/XMLSchema)açıklanmaktadır. "Xs" ön eki bu belgede kullanılıyor.

- Şema olmayan bir ad alanı olan herhangi bir öznitelik yok sayılır.

- Tüm ek açıklamalar (Bu belgede açıklananlar dışında) yok sayılır.

### <a name="xsschema-attributes"></a>\<xs: Schema >: öznitelikler

|Öznitelik|DataContract|
|---------------|------------------|
|`attributeFormDefault`|LIP.|
|`blockDefault`|LIP.|
|`elementFormDefault`|Nitelenmiş olmalıdır. Bir şemanın `DataContractSerializer`tarafından desteklenmesi için tüm öğelerin nitelenmiş olması gerekir. Bu, xs:schema/@elementFormDefault "nitelikli" olarak ayarlanarak veya her bir öğe bildiriminde xs:element/@form "Qualified" olarak ayarlanarak gerçekleştirilebilir.|
|`finalDefault`|LIP.|
|`Id`|LIP.|
|`targetNamespace`|Desteklenir ve veri sözleşmesi ad alanıyla eşleştirilir. Bu öznitelik belirtilmemişse boş ad alanı kullanılır. Ayrılmış ad alanı `http://schemas.microsoft.com/2003/10/Serialization/`olamaz.|
|`version`|LIP.|

### <a name="xsschema-contents"></a>\<xs: Schema >: içerikler

|İçindekiler|Şema|
|--------------|------------|
|`include`|Desteklenen. `DataContractSerializer` xs: include ve xs: import destekler. Ancak, Svcutil. exe, meta veriler yerel bir dosyadan yüklendiğinde aşağıdaki `xs:include/@schemaLocation` ve `xs:import/@location` başvurularını kısıtlar. Şema dosyalarının listesi, bu durumda `include` değil, bant dışı bir mekanizmaya geçirilmelidir; `include`d şema belgeleri yok sayılır.|
|`redefine`|Inı. `xs:redefine` kullanımı, güvenlik nedenleriyle `DataContractSerializer` yasaktır: `x:redefine`, `schemaLocation` 'in izlenmesinin gerekli olmasını gerektirir. Bazı durumlarda, DataContract kullanan Svcutil. exe `schemaLocation`kullanımını kısıtlar.|
|`import`|Desteklenen. `DataContractSerializer` `xs:include` ve `xs:import`destekler. Ancak, Svcutil. exe, meta veriler yerel bir dosyadan yüklendiğinde aşağıdaki `xs:include/@schemaLocation` ve `xs:import/@location` başvurularını kısıtlar. Şema dosyalarının listesi, bu durumda `include` değil, bant dışı bir mekanizmaya geçirilmelidir; `include`d şema belgeleri yok sayılır.|
|`simpleType`|Desteklenen. `xs:simpleType` bölümüne bakın.|
|`complexType`|Desteklenir, veri sözleşmeleri ile eşlenir. `xs:complexType` bölümüne bakın.|
|`group`|LIP. `DataContractSerializer` `xs:group`, `xs:attributeGroup`ve `xs:attribute`kullanımını desteklemez. Bu bildirimler `xs:schema`alt öğeleri olarak yok sayılır, ancak `complexType` veya desteklenen diğer yapıların içinde başvurulamaz.|
|`attributeGroup`|LIP. `DataContractSerializer` `xs:group`, `xs:attributeGroup`ve `xs:attribute`kullanımını desteklemez. Bu bildirimler `xs:schema`alt öğeleri olarak yok sayılır, ancak `complexType` veya desteklenen diğer yapıların içinde başvurulamaz.|
|`element`|Desteklenen. Bkz. genel öğe bildirimi (ŞLı).|
|`attribute`|LIP. `DataContractSerializer` `xs:group`, `xs:attributeGroup`ve `xs:attribute`kullanımını desteklemez. Bu bildirimler `xs:schema`alt öğeleri olarak yok sayılır, ancak `complexType` veya desteklenen diğer yapıların içinde başvurulamaz.|
|`notation`|LIP.|

## <a name="complex-types--xscomplextype"></a>Karmaşık türler – \<xs: complexType >

### <a name="general-information"></a>Genel Bilgiler

Her karmaşık tür \<xs: complexType > bir veri sözleşmesine eşlenir.

### <a name="xscomplextype-attributes"></a>\<xs: complexType >: öznitelikler

|Öznitelik|Şema|
|---------------|------------|
|`abstract`|False (varsayılan) olmalıdır.|
|`block`|Inı.|
|`final`|LIP.|
|`id`|LIP.|
|`mixed`|False (varsayılan) olmalıdır.|
|`name`|Desteklenir ve veri sözleşmesi adına eşlenir. Adda dönemler varsa, türü bir iç türle eşlemek için bir girişimde bulunuldu. Örneğin, `A.B` adlı karmaşık bir tür, `A`veri sözleşmesi adına sahip bir türün iç türü olan bir veri sözleşmesi türüyle eşlenir, ancak bu tür bir veri anlaşması türü varsa. Birden fazla iç içe geçme olabilir: Örneğin, `A.B.C` bir iç tür olabilir, ancak yalnızca `A` ve `A.B` ikisi de vardır.|

### <a name="xscomplextype-contents"></a>\<xs: complexType >: içerikler

|İçindekiler|Şema|
|--------------|------------|
|`simpleContent`|Uzantılar yasaktır.<br /><br /> Kısıtlamaya yalnızca `anySimpleType`izin verilir.|
|`complexContent`|Desteklenen. Bkz. "devralma".|
|`group`|Inı.|
|`all`|Inı.|
|`choice`|Yasak|
|`sequence`|Desteklenir, bir veri sözleşmesinin veri üyeleriyle eşlenir.|
|`attribute`|Use = "yasaklanmış" (bir özel durum) olsa bile yasak. Yalnızca standart serileştirme şeması ad alanındaki isteğe bağlı öznitelikler desteklenir. Veri sözleşmesi programlama modelindeki veri üyeleriyle eşlemeirler. Şu anda yalnızca bir özniteliğin anlamı vardır ve ISerializable bölümünde ele alınmıştır. Diğerlerinin hepsi yok sayılır.|
|`attributeGroup`|Inı. WCF v1 sürümünde, `DataContractSerializer` `xs:complexType`içindeki `attributeGroup` varlığını yoksayar.|
|`anyAttribute`|Inı.|
|olmamalıdır|Veri üyesi olmayan bir veri sözleşmesine eşlenir.|

### <a name="xssequence-in-a-complex-type-attributes"></a>\<xs: dizi > karmaşık türde: öznitelikler

|Öznitelik|Şema|
|---------------|------------|
|`id`|LIP.|
|`maxOccurs`|1 (varsayılan) olmalıdır.|
|`minOccurs`|1 (varsayılan) olmalıdır.|

### <a name="xssequence-in-a-complex-type-contents"></a>\<xs: dizi > karmaşık türde: içerikler

|İçindekiler|Şema|
|--------------|------------|
|`element`|Her örnek bir veri üyesine eşlenir.|
|`group`|Inı.|
|`choice`|Inı.|
|`sequence`|Inı.|
|`any`|Inı.|
|olmamalıdır|Veri üyesi olmayan bir veri sözleşmesine eşlenir.|

## <a name="elements--xselement"></a>Öğeler – \<xs: element >

### <a name="general-information"></a>Genel Bilgiler

`<xs:element>`, aşağıdaki bağlamlarda gerçekleşebilir:

- Düzenli (koleksiyon olmayan) bir veri sözleşmesinin veri üyesini açıklayan bir `<xs:sequence>`içinde meydana gelebilir. Bu durumda `maxOccurs` özniteliği 1 olmalıdır. (0 değerine izin verilmez).

- Bu, bir koleksiyon veri sözleşmesinin veri üyesini açıklayan bir `<xs:sequence>`içinde meydana gelebilir. Bu durumda `maxOccurs` özniteliği 1 ' den büyük veya "sınırsız" olmalıdır.

- Bir `<xs:schema>` içinde genel bir öğe bildirimi (ŞLı) olarak meydana gelebilir.

### <a name="xselement-with-maxoccurs1-within-an-xssequence-data-members"></a>\<xs: element >, bir \<xs: Sequence > (veri üyeleri) içinde maxOccurs = 1 ile

|Öznitelik|Şema|
|---------------|------------|
|`ref`|Inı.|
|`name`|Desteklenir, veri üyesi adı ile eşlenir.|
|`type`|Desteklenir, veri üyesi türüyle eşlenir. Daha fazla bilgi için bkz. tür/temel öğe eşleme. Belirtilmemişse (ve öğesi anonim bir tür içermiyorsa), `xs:anyType` varsayılır.|
|`block`|LIP.|
|`default`|Inı.|
|`fixed`|Inı.|
|`form`|Nitelenmiş olmalıdır. Bu öznitelik, `xs:schema``elementFormDefault` aracılığıyla ayarlanabilir.|
|`id`|LIP.|
|`maxOccurs`|1\.|
|`minOccurs`|Bir veri üyesinin <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> özelliğine eşlenir (`minOccurs` 1 olduğunda`IsRequired` true 'dur).|
|`nillable`|Tür eşlemesini etkiler. Bkz. tür/temel eşleme.|

### <a name="xselement-with-maxoccurs1-within-an-xssequence-collections"></a>\<xs: element >, \<xs: Sequence > (koleksiyonlar) içinde maxOccurs > 1

- Bir <xref:System.Runtime.Serialization.CollectionDataContractAttribute>eşler.

- Koleksiyon türlerinde, xs: Sequence içinde yalnızca bir xs: element öğesine izin verilir.

 Koleksiyonlar aşağıdaki türlerde olabilir:

- Normal Koleksiyonlar (örneğin, diziler).

- Sözlük koleksiyonları (bir değeri başka bir değerle eşleme; Örneğin, bir <xref:System.Collections.Hashtable>).

- Bir sözlük ile anahtar/değer çifti türündeki bir dizi arasındaki tek fark, oluşturulan programlama modelidir. Belirli bir türün sözlük koleksiyonu olduğunu göstermek için kullanılabilecek bir şema ek açıklaması mekanizması vardır.

`ref`, `block`, `default`, `fixed`, `form`ve `id` özniteliklerinin kuralları koleksiyon olmayan durum ile aynıdır. Diğer öznitelikler aşağıdaki tabloda yer alır.

|Öznitelik|Şema|
|---------------|------------|
|`name`|Desteklenir, `CollectionDataContractAttribute` özniteliğinde <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> özelliği ile eşlenir.|
|`type`|Desteklenir, koleksiyonda depolanan türle eşlenir.|
|`maxOccurs`|1 ' den büyük veya "sınırsız". DC şeması "sınırsız" kullanmalıdır.|
|`minOccurs`|LIP.|
|`nillable`|Tür eşlemesini etkiler. Bu öznitelik, sözlük koleksiyonları için yok sayılır.|

### <a name="xselement-within-an-xsschema-global-element-declaration"></a>\<xs: element > bir \<xs: Schema > Genel öğe bildirimi

- Şemadaki bir türle aynı ada ve ad alanına sahip olan veya kendisi içinde anonim bir tür tanımlayan genel öğe bildirimi (ŞLı), türle ilişkili olarak söylenir.

- Şema dışarı aktarma: ilişkili GEDs, hem basit hem de karmaşık oluşturulan her tür için oluşturulur.

- Seri durumdan çıkarma/serileştirme: ilişkili GEDs, tür için kök öğe olarak kullanılır.

- Şema içeri aktarma: ilişkili GEDs 'ler gerekli değildir ve aşağıdaki kurallara uyar (türleri tanımladıkça).

|Öznitelik|Şema|
|---------------|------------|
|`abstract`|İlişkili GEDs 'ler için false olmalıdır.|
|`block`|İlişkili GEDs 'de yasak.|
|`default`|İlişkili GEDs 'de yasak.|
|`final`|İlişkili GEDs 'ler için false olmalıdır.|
|`fixed`|İlişkili GEDs 'de yasak.|
|`id`|LIP.|
|`name`|Desteklenen. İlişkili GEDs tanımına bakın.|
|`nillable`|İlişkili GEDs 'ler için doğru olmalıdır.|
|`substitutionGroup`|İlişkili GEDs 'de yasak.|
|`type`|Desteklenir ve ilişkili GEDs için ilişkili tür ile eşleşmelidir (öğe anonim bir tür içermiyorsa).|

### <a name="xselement-contents"></a>\<xs: element >: içerikler

|İçindekiler|Şema|
|--------------|------------|
|`simpleType`|Desteklenir. *|
|`complexType`|Desteklenir. *|
|`unique`|LIP.|
|`key`|LIP.|
|`keyref`|LIP.|
|(boş)|Desteklenen.|

anonim türler için `simpleType` ve `complexType,` eşleme kullanılırken \* anonim olmayan türler için aynı olduğunda, anonim veri sözleşmeleri olmaması dışında, adlandırılmış bir veri sözleşmesinin oluşturulması ve bu nedenle, öğe adından elde edilen oluşturulmuş bir ada sahip olması gerekir. Anonim türlerin kuralları aşağıdaki listede verilmiştir:

- WCF uygulama ayrıntısı: `xs:element` adı nokta içermiyorsa, anonim tür dış veri sözleşmesi türünün bir iç türüyle eşlenir. Ad nokta içeriyorsa, sonuçta elde edilen veri anlaşması türü bağımsızdır (bir iç tür değildir).

- İç türün üretilen veri sözleşme adı, dış türün veri sözleşmesinin adı ve ardından bir nokta, öğenin adı ve "tür" dizesi gelir.

- Böyle bir ada sahip bir veri sözleşmesi zaten varsa, benzersiz bir ad oluşturuluncaya kadar "1", "2", "3" vb. eklenerek ad benzersiz hale getirilir.

## <a name="simple-types---xssimpletype"></a>Basit türler-\<xs: simpleType >

### <a name="xssimpletype-attributes"></a>\<xs: simpleType >: öznitelikler

|Öznitelik|Şema|
|---------------|------------|
|`final`|LIP.|
|`id`|LIP.|
|`name`|Desteklenir, veri sözleşmesi adıyla eşlenir.|

### <a name="xssimpletype-contents"></a>\<xs: simpleType >: içerik

|İçindekiler|Şema|
|--------------|------------|
|`restriction`|Desteklenen. Sabit listesi veri sözleşmeleri ile eşlenir. Bu öznitelik, numaralandırma düzeniyle eşleşmezse yok sayılır. `xs:simpleType` kısıtlamalar bölümüne bakın.|
|`list`|Desteklenen. Bayrak sıralama veri sözleşmeleri ile eşlenir. `xs:simpleType` listeleri bölümüne bakın.|
|`union`|Inı.|

### <a name="xsrestriction"></a>\<xs: kısıtlama >

- Karmaşık tür kısıtlamaları yalnızca Base = "`xs:anyType`" için desteklenir.

- `xs:enumeration` dışındaki kısıtlama modelleri olmayan `xs:string` basit tür kısıtlamaları, sabit listesi veri sözleşmeleri ile eşleştirilir.

- Diğer tüm basit tür kısıtlamaları, kısıttıkları türlere eşlenir. Örneğin, bir `xs:int` kısıtlaması, tıpkı `xs:int` olduğu gibi bir tamsayı ile eşlenir. İlkel tür eşlemesi hakkında daha fazla bilgi için bkz. tür/temel eşleme.

### <a name="xsrestriction-attributes"></a>\<xs: restriction >: öznitelikler

|Öznitelik|Şema|
|---------------|------------|
|`base`|Desteklenen bir basit tür veya `xs:anyType`olmalıdır.|
|`id`|LIP.|

### <a name="xsrestriction-for-all-other-cases-contents"></a>\<xs: kısıtlama > diğer tüm durumlarda: içerikler

|İçindekiler|Şema|
|--------------|------------|
|`simpleType`|Varsa, desteklenen bir temel türden türetilmiş olmalıdır.|
|`minExclusive`|LIP.|
|`minInclusive`|LIP.|
|`maxExclusive`|LIP.|
|`maxInclusive`|LIP.|
|`totalDigits`|LIP.|
|`fractionDigits`|LIP.|
|`length`|LIP.|
|`minLength`|LIP.|
|`maxLength`|LIP.|
|`enumeration`|LIP.|
|`whiteSpace`|LIP.|
|`pattern`|LIP.|
|(boş)|Desteklenen.|

## <a name="enumeration"></a>Numaralandırma

### <a name="xsrestriction-for-enumerations-attributes"></a>\<xs:, numaralandırmalar için kısıtlama >: öznitelikler

|Öznitelik|Şema|
|---------------|------------|
|`base`|Varsa, `xs:string`olması gerekir.|
|`id`|LIP.|

### <a name="xsrestriction-for-enumerations-contents"></a>\<xs:, numaralandırmalar için kısıtlama >: içerikler

|İçindekiler|Şema|
|--------------|------------|
|`simpleType`|Varsa, veri anlaşması (Bu bölüm) tarafından desteklenen bir numaralandırma kısıtlaması olmalıdır.|
|`minExclusive`|LIP.|
|`minInclusive`|LIP.|
|`maxExclusive`|LIP.|
|`maxInclusive`|LIP.|
|`totalDigits`|LIP.|
|`fractionDigits`|LIP.|
|`length`|Inı.|
|`minLength`|Inı.|
|`maxLength`|Inı.|
|`enumeration`|Desteklenen. "Kimlik" numaralandırması yok sayılır ve "değer" sabit listesi veri sözleşmesindeki değer adıyla eşlenir.|
|`whiteSpace`|Inı.|
|`pattern`|Inı.|
|olmamalıdır|Desteklenir, boş sabit listesi türüne eşlenir.|

 Aşağıdaki kod bir C# numaralandırma sınıfını gösterir.

```csharp
public enum MyEnum
{
  first = 3,
  second = 4,
  third =5
}
```

Bu sınıf, `DataContractSerializer`tarafından aşağıdaki şemaya eşlenir. Numaralandırma değerleri 1 ' den başlar `xs:annotation` bloklar oluşturulmaz.

```xml
<xs:simpleType name="MyEnum">
  <xs:restriction base="xs:string">
    <xs:enumeration value="first">
      <xs:annotation>
        <xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">
          3
          </EnumerationValue>
        </xs:appinfo>
      </xs:annotation>
    </xs:enumeration>
    <xs:enumeration value="second">
      <xs:annotation>
        <xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">
          4
          </EnumerationValue>
        </xs:appinfo>
      </xs:annotation>
    </xs:enumeration>
  </xs:restriction>
</xs:simpleType>
```

### <a name="xslist"></a>\<xs: List >

`DataContractSerializer`, `System.FlagsAttribute` ile işaretlenen numaralandırma türlerini `xs:string`türetilmiş `xs:list` olarak eşleştirir. Başka `xs:list` çeşitlemeleri desteklenmez.

### <a name="xslist-attributes"></a>\<xs: List >: öznitelikler

|Öznitelik|Şema|
|---------------|------------|
|`itemType`|Inı.|
|`id`|LIP.|

### <a name="xslist-contents"></a>\<xs: List >: Contents

|İçindekiler|Şema|
|--------------|------------|
|`simpleType`|`xs:enumeration` modeli kullanılarak `xs:string` kısıtlaması olmalıdır.|

Numaralandırma değeri 2 ilerlemenin gücünden (bayraklar için varsayılan) eşleşmezse, değer `xs:annotation/xs:appInfo/ser:EnumerationValue` öğesinde depolanır.

Örneğin, aşağıdaki kod bir numaralandırma türünü bayraklar.

```csharp
[Flags]
public enum AuthFlags
{
  AuthAnonymous = 1,
  AuthBasic = 2,
  AuthNTLM = 4,
  AuthMD5 = 16,
  AuthWindowsLiveID = 64,
}
```

Bu tür aşağıdaki şemaya eşlenir.

```xml
<xs:simpleType name="AuthFlags">
    <xs:list>
      <xs:simpleType>
        <xs:restriction base="xs:string">
          <xs:enumeration value="AuthAnonymous" />
          <xs:enumeration value="AuthBasic" />
          <xs:enumeration value="AuthNTLM" />
          <xs:enumeration value="AuthMD5">
            <xs:annotation>
              <xs:appinfo>
                <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">16</EnumerationValue>
              </xs:appinfo>
            </xs:annotation>
          </xs:enumeration>
          <xs:enumeration value="AuthWindowsLiveID">
            <xs:annotation>
              <xs:appinfo>
                <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">64</EnumerationValue>
              </xs:appinfo>
            </xs:annotation>
          </xs:enumeration>
        </xs:restriction>
      </xs:simpleType>
    </xs:list>
  </xs:simpleType>
```

## <a name="inheritance"></a>Devralma

### <a name="general-rules"></a>Genel kurallar

Bir veri sözleşmesi, başka bir veri sözleşmesinden devralınabilir. Bu tür veri sözleşmeleri bir temel ile eşlenir ve `<xs:extension>` XML şema yapısı kullanılarak uzantı türlerine göre türetilir.

Veri sözleşmesi bir koleksiyon veri sözleşmesinden devralınabilir.

Örneğin, aşağıdaki kod bir veri sözleşmedir.

```csharp
[DataContract]
public class Person
{
  [DataMember]
  public string Name;
}
[DataContract]
public class Employee : Person
{
  [DataMember]
  public int ID;
}
```

Bu veri sözleşmesi, aşağıdaki XML Şeması tür bildirimiyle eşlenir.

```xml
<xs:complexType name="Employee">
 <xs:complexContent mixed="false">
  <xs:extension base="tns:Person">
   <xs:sequence>
    <xs:element minOccurs="0" name="ID" type="xs:int"/>
   </xs:sequence>
  </xs:extension>
 </xs:complexContent>
</xs:complexType>
<xs:complexType name="Person">
 <xs:sequence>
  <xs:element minOccurs="0" name="Name"
    nillable="true" type="xs:string"/>
 </xs:sequence>
</xs:complexType>
```

### <a name="xscomplexcontent-attributes"></a>\<xs: complexContent >: öznitelikler

|Öznitelik|Şema|
|---------------|------------|
|`id`|LIP.|
|`mixed`|False olmalıdır.|

### <a name="xscomplexcontent-contents"></a>\<xs: complexContent >: içerikler

|İçindekiler|Şema|
|--------------|------------|
|`restriction`|Yasak, Base = "`xs:anyType`" dışında. İkincisi, `xs:restriction` içeriğini doğrudan `xs:complexContent`kapsayıcısının altına yerleştirmeye eşdeğerdir.|
|`extension`|Desteklenen. Veri sözleşmesi devralmayla eşlenir.|

### <a name="xsextension-in-xscomplexcontent-attributes"></a>\<xs:extension> in \<xs:complexContent>: attributes

|Öznitelik|Şema|
|---------------|------------|
|`id`|LIP.|
|`base`|Desteklenen. Bu türün devraldığı temel veri sözleşmesi türüyle eşlenir.|

### <a name="xsextension-in-xscomplexcontent-contents"></a>\<xs: \<xs: complexContent >: Contents içindeki uzantı >

Kurallar `<xs:complexType>` içeriğiyle aynı.

Bir `<xs:sequence>` sağlanmışsa, üye öğeleri türetilmiş veri sözleşmesinde bulunan ek veri üyeleriyle eşlenir.

Türetilmiş bir tür, temel türdeki bir öğeyle aynı ada sahip bir öğe içeriyorsa, yinelenen öğe bildirimi benzersiz olması için oluşturulan bir adla veri üyesine eşlenir. Benzersiz bir ad bulunana kadar ("member1", "member2" vb.) veri üyesi adına pozitif tamsayı numaraları eklenir. Buna karşılık

- Türetilmiş bir veri sözleşmesinin, temel veri sözleşmesindeki bir veri üyesi ile aynı ada ve türe sahip bir veri üyesi varsa `DataContractSerializer` türetilen türde bu karşılık gelen öğeyi oluşturur.

- Türetilmiş bir veri sözleşmesinin, temel veri sözleşmesindeki bir veri üyesi ile aynı ada sahip bir veri üyesi, ancak farklı bir tür varsa, `DataContractSerializer` hem temel tür hem de türetilmiş tür bildirimlerinde `xs:anyType` türündeki bir öğeyi içeren bir şemayı içeri aktarır. Özgün tür adı `xs:annotations/xs:appInfo/ser:ActualType/@Name`saklanır.

Her iki çeşitleme de, ilgili veri üyelerinin sırasına bağlı olarak belirsiz bir içerik modeli olan bir şemaya neden olabilir.

## <a name="typeprimitive-mapping"></a>Tür/basit eşleme

`DataContractSerializer`, XML şeması temel türleri için aşağıdaki eşlemeyi kullanır.

|XSD türü|.NET türü|
|--------------|---------------|
|`anyType`|<xref:System.Object>.|
|`anySimpleType`|<xref:System.String>.|
|`duration`|<xref:System.TimeSpan>.|
|`dateTime`|<xref:System.DateTime>.|
|`dateTimeOffset`|<xref:System.DateTime> ve konum için <xref:System.TimeSpan>. Aşağıdaki DateTimeOffset serileştirme ' i inceleyin.|
|`time`|<xref:System.String>.|
|`date`|<xref:System.String>.|
|`gYearMonth`|<xref:System.String>.|
|`gYear`|<xref:System.String>.|
|`gMonthDay`|<xref:System.String>.|
|`gDay`|<xref:System.String>.|
|`gMonth`|<xref:System.String>.|
|`boolean`|<xref:System.Boolean>|
|`base64Binary`|<xref:System.Byte> dizi.|
|`hexBinary`|<xref:System.String>.|
|`float`|<xref:System.Single>.|
|`double`|<xref:System.Double>.|
|`anyURI`|<xref:System.Uri>.|
|`QName`|<xref:System.Xml.XmlQualifiedName>.|
|`string`|<xref:System.String>.|
|`normalizedString`|<xref:System.String>.|
|`token`|<xref:System.String>.|
|`language`|<xref:System.String>.|
|`Name`|<xref:System.String>.|
|`NCName`|<xref:System.String>.|
|`ID`|<xref:System.String>.|
|`IDREF`|<xref:System.String>.|
|`IDREFS`|<xref:System.String>.|
|`ENTITY`|<xref:System.String>.|
|`ENTITIES`|<xref:System.String>.|
|`NMTOKEN`|<xref:System.String>.|
|`NMTOKENS`|<xref:System.String>.|
|`decimal`|<xref:System.Decimal>.|
|`integer`|<xref:System.Int64>.|
|`nonPositiveInteger`|<xref:System.Int64>.|
|`negativeInteger`|<xref:System.Int64>.|
|`long`|<xref:System.Int64>.|
|`int`|<xref:System.Int32>.|
|`short`|<xref:System.Int16>.|
|`Byte`|<xref:System.SByte>.|
|`nonNegativeInteger`|<xref:System.Int64>.|
|`unsignedLong`|<xref:System.UInt64>.|
|`unsignedInt`|<xref:System.UInt32>.|
|`unsignedShort`|<xref:System.UInt16>.|
|`unsignedByte`|<xref:System.Byte>.|
|`positiveInteger`|<xref:System.Int64>.|

## <a name="iserializable-types-mapping"></a>ISerializable türleri eşleme

.NET Framework sürüm 1,0 ' de, <xref:System.Runtime.Serialization.ISerializable> kalıcı veya veri aktarımı için nesneleri serileştirmek üzere genel bir mekanizma olarak sunulmuştur. `ISerializable` uygulayan ve uygulamalar arasında geçirilebilecek pek çok .NET Framework türü vardır. <xref:System.Runtime.Serialization.DataContractSerializer> doğal olarak `ISerializable` sınıfları için destek sağlar. `DataContractSerializer`, yalnızca türün QName (nitelenmiş adı) ile farklı `ISerializable` uygulama şeması türlerini eşleştirir ve etkin özellik koleksiyonlarıdır. Örneğin, `DataContractSerializer` <xref:System.Exception> `http://schemas.datacontract.org/2004/07/System` ad alanında aşağıdaki XSD türüne eşlenir.

```xml
<xs:complexType name="Exception">
 <xs:sequence>
  <xs:any minOccurs="0" maxOccurs="unbounded"
      namespace="##local" processContents="skip"/>
 </xs:sequence>
 <xs:attribute ref="ser:FactoryType"/>
</xs:complexType>
```

Veri sözleşmesi serileştirme şemasında bildirildiği `ser:FactoryType` isteğe bağlı öznitelik, türü seri durumdan çıkarılabilecek bir fabrika sınıfına başvurur. Factory sınıfı, kullanılan `DataContractSerializer` örneğinin bilinen türler koleksiyonunun bir parçası olmalıdır. Bilinen türler hakkında daha fazla bilgi için bkz. [veri sözleşmesi bilinen türler](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).

## <a name="datacontract-serialization-schema"></a>DataContract serileştirme şeması

`DataContractSerializer` tarafından dışarıya aktarılmış bir dizi şema, özel bir veri sözleşmesi serileştirme ad alanından türler, öğeler ve öznitelikler kullanır:

`http://schemas.microsoft.com/2003/10/Serialization`

Aşağıda, tüm veri anlaşması serileştirme şeması bildirimi verilmiştir.

```xml
<xs:schema attributeFormDefault="qualified"
   elementFormDefault="qualified"
   targetNamespace =
    "http://schemas.microsoft.com/2003/10/Serialization/"
   xmlns:xs="http://www.w3.org/2001/XMLSchema"
   xmlns:tns="http://schemas.microsoft.com/2003/10/Serialization/">

 <!-- Top-level elements for primitive types. -->
 <xs:element name="anyType" nillable="true" type="xs:anyType"/>
 <xs:element name="anyURI" nillable="true" type="xs:anyURI"/>
 <xs:element name="base64Binary"
       nillable="true" type="xs:base64Binary"/>
 <xs:element name="boolean" nillable="true" type="xs:boolean"/>
 <xs:element name="byte" nillable="true" type="xs:byte"/>
 <xs:element name="dateTime" nillable="true" type="xs:dateTime"/>
 <xs:element name="decimal" nillable="true" type="xs:decimal"/>
 <xs:element name="double" nillable="true" type="xs:double"/>
 <xs:element name="float" nillable="true" type="xs:float"/>
 <xs:element name="int" nillable="true" type="xs:int"/>
 <xs:element name="long" nillable="true" type="xs:long"/>
 <xs:element name="QName" nillable="true" type="xs:QName"/>
 <xs:element name="short" nillable="true" type="xs:short"/>
 <xs:element name="string" nillable="true" type="xs:string"/>
 <xs:element name="unsignedByte"
       nillable="true" type="xs:unsignedByte"/>
 <xs:element name="unsignedInt"
       nillable="true" type="xs:unsignedInt"/>
 <xs:element name="unsignedLong"
       nillable="true" type="xs:unsignedLong"/>
 <xs:element name="unsignedShort"
       nillable="true" type="xs:unsignedShort"/>

 <!-- Primitive types introduced for certain .NET simple types. -->
 <xs:element name="char" nillable="true" type="tns:char"/>
 <xs:simpleType name="char">
  <xs:restriction base="xs:int"/>
 </xs:simpleType>

 <!-- xs:duration is restricted to an ordered value space,
    to map to System.TimeSpan -->
 <xs:element name="duration" nillable="true" type="tns:duration"/>
 <xs:simpleType name="duration">
  <xs:restriction base="xs:duration">
   <xs:pattern
     value="\-?P(\d*D)?(T(\d*H)?(\d*M)?(\d*(\.\d*)?S)?)?"/>
   <xs:minInclusive value="-P10675199DT2H48M5.4775808S"/>
   <xs:maxInclusive value="P10675199DT2H48M5.4775807S"/>
  </xs:restriction>
 </xs:simpleType>

 <xs:element name="guid" nillable="true" type="tns:guid"/>
 <xs:simpleType name="guid">
  <xs:restriction base="xs:string">
   <xs:pattern value="[\da-fA-F]{8}-[\da-fA-F]{4}-[\da-fA-F]{4}-[\da-fA-F]{4}-[\da-fA-F]{12}"/>
  </xs:restriction>
 </xs:simpleType>

 <!-- This is used for schemas exported from ISerializable type. -->
 <xs:attribute name="FactoryType" type="xs:QName"/>
</xs:schema>
```

Aşağıdakiler not edilmelidir:

- `ser:char`, <xref:System.Char>türündeki Unicode karakterlerini temsil edecek şekilde sunulmuştur.

- `xs:duration` `valuespace`, bir <xref:System.TimeSpan>eşleştirileceğinden, sıralı bir küme ile azaltılır.

- `FactoryType`, <xref:System.Runtime.Serialization.ISerializable>türetilen türlerden aktarılmış şemalarda kullanılır.

## <a name="importing-non-datacontract-schemas"></a>DataContract olmayan şemaları içeri aktarma

`DataContractSerializer`, `DataContractSerializer` XSD profiliyle uyumlu olmayan şemalardan içeri aktarmaya izin veren `ImportXmlTypes` seçeneğine sahiptir (bkz. <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> özelliği). Bu seçeneğin `true` ayarlanması, uyumsuz şema türlerinin kabul edilmesine ve bunları aşağıdaki uygulamayla eşleştirmenize <xref:System.Xml.XmlNode> <xref:System.Xml.Serialization.IXmlSerializable> (yalnızca sınıf adı farklıdır).

```csharp
[GeneratedCodeAttribute("System.Runtime.Serialization", "3.0.0.0")]
[System.Xml.Serialization.XmlSchemaProviderAttribute("ExportSchema")]
[System.Xml.Serialization.XmlRootAttribute(IsNullable=false)]
public partial class Person : object, IXmlSerializable
{
  private XmlNode[] nodesField;
  private static XmlQualifiedName typeName =
new XmlQualifiedName("Person","http://Microsoft.ServiceModel.Samples");
  public XmlNode[] Nodes
  {
    get {return this.nodesField;}
    set {this.nodesField = value;}
  }
  public void ReadXml(XmlReader reader)
  {
    this.nodesField = XmlSerializableServices.ReadNodes(reader);
  }
  public void WriteXml(XmlWriter writer)
  {
    XmlSerializableServices.WriteNodes(writer, this.Nodes);
  }
  public System.Xml.Schema.XmlSchema GetSchema()
  {
    return null;
  }
  public static XmlQualifiedName ExportSchema(XmlSchemaSet schemas)
  {
    XmlSerializableServices.AddDefaultSchema(schemas, typeName);
    return typeName;
  }
}
```

## <a name="datetimeoffset-serialization"></a>DateTimeOffset serileştirme

<xref:System.DateTimeOffset> ilkel bir tür olarak değerlendirilmez. Bunun yerine, iki bölümden oluşan karmaşık bir öğe olarak serileştirilir. İlk bölüm Tarih saatini temsil eder ve ikinci bölüm Tarih saatinden itibaren olan sapmayı temsil eder. Aşağıdaki kodda serileştirilmiş bir DateTimeOffset değeri örneği gösterilmektedir.

```xml
<OffSet xmlns:a="http://schemas.datacontract.org/2004/07/System">
  <DateTime i:type="b:dateTime" xmlns=""
    xmlns:b="http://www.w3.org/2001/XMLSchema">2008-08-28T08:00:00
  </DateTime>
  <OffsetMinutes i:type="b:short" xmlns=""
   xmlns:b="http://www.w3.org/2001/XMLSchema">-480
   </OffsetMinutes>
</OffSet>
```

Şema aşağıdaki gibidir.

```xml
<xs:schema targetNamespace="http://schemas.datacontract.org/2004/07/System">
   <xs:complexType name="DateTimeOffset">
      <xs:sequence minOccurs="1" maxOccurs="1">
         <xs:element name="DateTime" type="xs:dateTime"
         minOccurs="1" maxOccurs="1" />
         <xs:element name="OffsetMinutes" type="xs:short"
         minOccurs="1" maxOccurs="1" />
      </xs:sequence>
   </xs:complexType>
</xs:schema>
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- <xref:System.Runtime.Serialization.XsdDataContractImporter>
- [Veri Anlaşmalarını Kullanma](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
