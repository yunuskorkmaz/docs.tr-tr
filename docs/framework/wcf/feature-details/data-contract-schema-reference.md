---
title: Veri Sözleşmesi Şema Başvurusu
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts [WCF], schema reference
ms.assetid: 9ebb0ebe-8166-4c93-980a-7c8f1f38f7c0
ms.openlocfilehash: 04d1f753e5788460404942a21a29e1612f674e90
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593574"
---
# <a name="data-contract-schema-reference"></a>Veri Sözleşmesi Şema Başvurusu

Bu konu, <xref:System.Runtime.Serialization.DataContractSerializer> XML serileştirmesi için ortak dil çalışma zamanı (CLR) türlerini tarif etmek üzere tarafından kullanılan XML şemasının (xsd) alt kümesini açıklar.

## <a name="datacontractserializer-mappings"></a>DataContractSerializer eşlemeleri

Meta veriler, `DataContractSerializer` meta veri uç noktası veya [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)kullanılarak BIR Windows Communication Foundation (WCF) hizmetinden VERILDIĞINDE CLR türlerini xsd olarak eşler. Daha fazla bilgi için bkz. [veri sözleşmesi serileştiricisi](data-contract-serializer.md).

`DataContractSerializer`Ayrıca, Svcutil. exe dosyası Web Hizmetleri Açıklama Dili (wsdl) veya xsd belgelerine erişmek için kullanıldığında ve hizmetler veya istemciler için veri sözleşmeleri oluştururken de xsd 'YI clr türlerine eşler.

Yalnızca bu belgede belirtilen gereksinimlere uyan XML şema örnekleri kullanılarak CLR türleriyle eşlenebilir `DataContractSerializer` .

### <a name="support-levels"></a>Destek düzeyleri

, `DataContractSerializer` Belirli BIR XML şeması özelliği için aşağıdaki destek düzeylerini sağlar:

- **Desteklenir**. Kullanılarak bu özellikten CLR türlerine veya özniteliklerine (veya her ikisine) açık eşleme vardır `DataContractSerializer` .

- **Yoksayıldı**. Özelliği tarafından içeri aktarılan şemalarda, `DataContractSerializer` ancak kod üretimi üzerinde hiçbir etkisi yoktur.

- **Yasak**. `DataContractSerializer`Özelliği kullanılarak şemanın içeri aktarılmasını desteklemez. Örneğin, bu tür bir özelliği kullanan bir şemaya sahip bir WSDL 'ye erişirken Svcutil. exe, bunun yerine kullanmaya geri döner <xref:System.Xml.Serialization.XmlSerializer> . Bu varsayılan olarak olur.

## <a name="general-information"></a>Genel Bilgiler

- Şema ad alanı [XML şemasında](https://www.w3.org/2001/XMLSchema)açıklanmaktadır. "Xs" ön eki bu belgede kullanılıyor.

- Şema olmayan bir ad alanı olan herhangi bir öznitelik yok sayılır.

- Tüm ek açıklamalar (Bu belgede açıklananlar dışında) yok sayılır.

### <a name="xsschema-attributes"></a>\<xs:schema>: öznitelikler

|Öznitelik|DataContract|
|---------------|------------------|
|`attributeFormDefault`|LIP.|
|`blockDefault`|LIP.|
|`elementFormDefault`|Nitelenmiş olmalıdır. Şemanın desteklenmesi için tüm öğelerin nitelendirilmelidir `DataContractSerializer` . Bu, herhangi bir xs:schema/@elementFormDefault öğe bildiriminde "nitelikli" veya xs:element/@form "nitelikli" olarak ayarlanarak gerçekleştirilebilir.|
|`finalDefault`|LIP.|
|`Id`|LIP.|
|`targetNamespace`|Desteklenir ve veri sözleşmesi ad alanıyla eşleştirilir. Bu öznitelik belirtilmemişse boş ad alanı kullanılır. Ayrılmış ad alanı olamaz `http://schemas.microsoft.com/2003/10/Serialization/` .|
|`version`|LIP.|

### <a name="xsschema-contents"></a>\<xs:schema>: içerik

|İçindekiler|Şema|
|--------------|------------|
|`include`|Destekleniyor. `DataContractSerializer`xs: include ve xs: import destekler. Ancak, Svcutil. exe `xs:include/@schemaLocation` `xs:import/@location` yerel bir dosyadan meta veriler yüklendiğinde aşağıdaki ve başvuruları kısıtlar. Şema dosyalarının listesi, bu durumda değil, bant dışı bir mekanizmaya geçirilmelidir `include` ; `include` d şema belgeleri yok sayılır.|
|`redefine`|Inı. Öğesinin kullanımı `xs:redefine` `DataContractSerializer` Güvenlik nedeniyle yasaktır: bunun `x:redefine` `schemaLocation` izlenmesinin gerekli olması gerekir. Bazı durumlarda, DataContract kullanan Svcutil. exe ' nin kullanımını kısıtlar `schemaLocation` .|
|`import`|Destekleniyor. `DataContractSerializer``xs:include`, ve destekler `xs:import` . Ancak, Svcutil. exe `xs:include/@schemaLocation` `xs:import/@location` yerel bir dosyadan meta veriler yüklendiğinde aşağıdaki ve başvuruları kısıtlar. Şema dosyalarının listesi, bu durumda değil, bant dışı bir mekanizmaya geçirilmelidir `include` ; `include` d şema belgeleri yok sayılır.|
|`simpleType`|Destekleniyor. Bölümüne bakın `xs:simpleType` .|
|`complexType`|Desteklenir, veri sözleşmeleri ile eşlenir. Bölümüne bakın `xs:complexType` .|
|`group`|LIP. `DataContractSerializer``xs:group`, ve kullanımını desteklemez `xs:attributeGroup` `xs:attribute` . Bu bildirimler, öğesinin alt öğesi olarak yok sayılır `xs:schema` , ancak içinden `complexType` veya desteklenen diğer yapılardan başvurulamaz.|
|`attributeGroup`|LIP. `DataContractSerializer``xs:group`, ve kullanımını desteklemez `xs:attributeGroup` `xs:attribute` . Bu bildirimler, öğesinin alt öğesi olarak yok sayılır `xs:schema` , ancak içinden `complexType` veya desteklenen diğer yapılardan başvurulamaz.|
|`element`|Destekleniyor. Bkz. genel öğe bildirimi (ŞLı).|
|`attribute`|LIP. `DataContractSerializer``xs:group`, ve kullanımını desteklemez `xs:attributeGroup` `xs:attribute` . Bu bildirimler, öğesinin alt öğesi olarak yok sayılır `xs:schema` , ancak içinden `complexType` veya desteklenen diğer yapılardan başvurulamaz.|
|`notation`|LIP.|

## <a name="complex-types--xscomplextype"></a>Karmaşık türler –\<xs:complexType>

### <a name="general-information"></a>Genel Bilgiler

Her karmaşık tür \<xs:complexType> bir veri sözleşmesine eşlenir.

### <a name="xscomplextype-attributes"></a>\<xs:complexType>: öznitelikler

|Öznitelik|Şema|
|---------------|------------|
|`abstract`|False (varsayılan) olmalıdır.|
|`block`|Inı.|
|`final`|LIP.|
|`id`|LIP.|
|`mixed`|False (varsayılan) olmalıdır.|
|`name`|Desteklenir ve veri sözleşmesi adına eşlenir. Adda dönemler varsa, türü bir iç türle eşlemek için bir girişimde bulunuldu. Örneğin, adlı karmaşık bir tür, veri sözleşmesi `A.B` adına sahip bir türün iç türü olan bir veri sözleşmesi türüyle eşlenir `A` , ancak bu tür bir veri anlaşması türü varsa. Birden fazla iç içe geçme olabilir: Örneğin, `A.B.C` bir iç tür olabilir, ancak yalnızca `A` ve `A.B` her ikisi de vardır.|

### <a name="xscomplextype-contents"></a>\<xs:complexType>: içerik

|İçindekiler|Şema|
|--------------|------------|
|`simpleContent`|Uzantılar yasaktır.<br /><br /> Kısıtlamaya yalnızca öğesinden izin verilir `anySimpleType` .|
|`complexContent`|Destekleniyor. Bkz. "devralma".|
|`group`|Inı.|
|`all`|Inı.|
|`choice`|Yasak|
|`sequence`|Desteklenir, bir veri sözleşmesinin veri üyeleriyle eşlenir.|
|`attribute`|Use = "yasaklanmış" (bir özel durum) olsa bile yasak. Yalnızca standart serileştirme şeması ad alanındaki isteğe bağlı öznitelikler desteklenir. Veri sözleşmesi programlama modelindeki veri üyeleriyle eşlemeirler. Şu anda yalnızca bir özniteliğin anlamı vardır ve ISerializable bölümünde ele alınmıştır. Diğerlerinin hepsi yok sayılır.|
|`attributeGroup`|Inı. WCF v1 sürümünde, `DataContractSerializer` içinde varlığını yoksayar `attributeGroup` `xs:complexType` .|
|`anyAttribute`|Inı.|
|olmamalıdır|Veri üyesi olmayan bir veri sözleşmesine eşlenir.|

### <a name="xssequence-in-a-complex-type-attributes"></a>\<xs:sequence>karmaşık bir tür: öznitelikler

|Öznitelik|Şema|
|---------------|------------|
|`id`|LIP.|
|`maxOccurs`|1 (varsayılan) olmalıdır.|
|`minOccurs`|1 (varsayılan) olmalıdır.|

### <a name="xssequence-in-a-complex-type-contents"></a>\<xs:sequence>karmaşık bir tür: içerikler

|İçindekiler|Şema|
|--------------|------------|
|`element`|Her örnek bir veri üyesine eşlenir.|
|`group`|Inı.|
|`choice`|Inı.|
|`sequence`|Inı.|
|`any`|Inı.|
|olmamalıdır|Veri üyesi olmayan bir veri sözleşmesine eşlenir.|

## <a name="elements--xselement"></a>Ög\<xs:element>

### <a name="general-information"></a>Genel Bilgiler

`<xs:element>`, aşağıdaki bağlamlarda gerçekleşebilir:

- `<xs:sequence>`Normal (koleksiyon olmayan) bir veri sözleşmesinin veri üyesini açıklayan bir içinde meydana gelebilir. Bu durumda, `maxOccurs` öznitelik 1 olmalıdır. (0 değerine izin verilmez).

- Bir `<xs:sequence>` koleksiyon veri sözleşmesinin veri üyesini açıklayan bir içinde meydana gelebilir. Bu durumda, `maxOccurs` öznitelik 1 veya "sınırsız" değerinden büyük olmalıdır.

- Bu, bir `<xs:schema>` genel öğe bildirimi (şlı) olarak bir içinde gerçekleşebilir.

### <a name="xselement-with-maxoccurs1-within-an-xssequence-data-members"></a>\<xs:element>(veri üyeleri) içinde maxOccurs = 1 ile \<xs:sequence>

|Öznitelik|Şema|
|---------------|------------|
|`ref`|Inı.|
|`name`|Desteklenir, veri üyesi adı ile eşlenir.|
|`type`|Desteklenir, veri üyesi türüyle eşlenir. Daha fazla bilgi için bkz. tür/temel öğe eşleme. Belirtilmemişse (ve öğe anonim bir tür içermiyorsa) `xs:anyType` varsayılır.|
|`block`|LIP.|
|`default`|Inı.|
|`fixed`|Inı.|
|`form`|Nitelenmiş olmalıdır. Bu öznitelik, üzerinden ayarlanabilir `elementFormDefault` `xs:schema` .|
|`id`|LIP.|
|`maxOccurs`|1|
|`minOccurs`|<xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A>Bir veri üyesinin özelliğine eşlenir ( `IsRequired` 1 olduğunda doğru olur `minOccurs` ).|
|`nillable`|Tür eşlemesini etkiler. Bkz. tür/temel eşleme.|

### <a name="xselement-with-maxoccurs1-within-an-xssequence-collections"></a>\<xs:element>(koleksiyonlar) içinde maxOccurs>1 ile \<xs:sequence>

- İle eşlenir <xref:System.Runtime.Serialization.CollectionDataContractAttribute> .

- Koleksiyon türlerinde, xs: Sequence içinde yalnızca bir xs: element öğesine izin verilir.

 Koleksiyonlar aşağıdaki türlerde olabilir:

- Normal Koleksiyonlar (örneğin, diziler).

- Sözlük koleksiyonları (bir değeri başka bir değerle eşleme; Örneğin, a <xref:System.Collections.Hashtable> ).

- Bir sözlük ile anahtar/değer çifti türündeki bir dizi arasındaki tek fark, oluşturulan programlama modelidir. Belirli bir türün sözlük koleksiyonu olduğunu göstermek için kullanılabilecek bir şema ek açıklaması mekanizması vardır.

,,,, `ref` `block` `default` Ve özniteliklerinin kuralları `fixed` , `form` `id` koleksiyon olmayan durum için ile aynıdır. Diğer öznitelikler aşağıdaki tabloda yer alır.

|Öznitelik|Şema|
|---------------|------------|
|`name`|Desteklenir, <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> özniteliğinde özelliği ile eşlenir `CollectionDataContractAttribute` .|
|`type`|Desteklenir, koleksiyonda depolanan türle eşlenir.|
|`maxOccurs`|1 ' den büyük veya "sınırsız". DC şeması "sınırsız" kullanmalıdır.|
|`minOccurs`|LIP.|
|`nillable`|Tür eşlemesini etkiler. Bu öznitelik, sözlük koleksiyonları için yok sayılır.|

### <a name="xselement-within-an-xsschema-global-element-declaration"></a>\<xs:element>genel bir \<xs:schema> öğe bildirimi içinde

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
|`name`|Destekleniyor. İlişkili GEDs tanımına bakın.|
|`nillable`|İlişkili GEDs 'ler için doğru olmalıdır.|
|`substitutionGroup`|İlişkili GEDs 'de yasak.|
|`type`|Desteklenir ve ilişkili GEDs için ilişkili tür ile eşleşmelidir (öğe anonim bir tür içermiyorsa).|

### <a name="xselement-contents"></a>\<xs:element>: içerik

|İçindekiler|Şema|
|--------------|------------|
|`simpleType`|Desteklenir. *|
|`complexType`|Desteklenir. *|
|`unique`|LIP.|
|`key`|LIP.|
|`keyref`|LIP.|
|adet|Destekleniyor.|

\*Anonim `simpleType` `complexType,` türler için ve eşlemesini kullandığınızda anonim olmayan türler için aynı, anonim veri sözleşmeleri olmaması dışında, adlandırılmış bir veri sözleşmesinin oluşturulduğu ve öğe adından türetilmiş oluşturulmuş bir adla aynı olması gerekir. Anonim türlerin kuralları aşağıdaki listede verilmiştir:

- WCF uygulama ayrıntısı: `xs:element` ad nokta içermiyorsa, anonim tür dış veri sözleşmesi türünün bir iç türüyle eşlenir. Ad nokta içeriyorsa, sonuçta elde edilen veri anlaşması türü bağımsızdır (bir iç tür değildir).

- İç türün üretilen veri sözleşme adı, dış türün veri sözleşmesinin adı ve ardından bir nokta, öğenin adı ve "tür" dizesi gelir.

- Böyle bir ada sahip bir veri sözleşmesi zaten varsa, benzersiz bir ad oluşturuluncaya kadar "1", "2", "3" vb. eklenerek ad benzersiz hale getirilir.

## <a name="simple-types---xssimpletype"></a>Basit türler-\<xs:simpleType>

### <a name="xssimpletype-attributes"></a>\<xs:simpleType>: öznitelikler

|Öznitelik|Şema|
|---------------|------------|
|`final`|LIP.|
|`id`|LIP.|
|`name`|Desteklenir, veri sözleşmesi adıyla eşlenir.|

### <a name="xssimpletype-contents"></a>\<xs:simpleType>: içerik

|İçindekiler|Şema|
|--------------|------------|
|`restriction`|Destekleniyor. Sabit listesi veri sözleşmeleri ile eşlenir. Bu öznitelik, numaralandırma düzeniyle eşleşmezse yok sayılır. `xs:simpleType`Kısıtlamalar bölümüne bakın.|
|`list`|Destekleniyor. Bayrak sıralama veri sözleşmeleri ile eşlenir. `xs:simpleType`Listeler bölümüne bakın.|
|`union`|Inı.|

### \<xs:restriction>

- Karmaşık tür kısıtlamaları yalnızca Base = "" için desteklenir `xs:anyType` .

- ' Nin farklı kısıtlama modelleri bulunmayan basit tür kısıtlamaları, `xs:string` `xs:enumeration` sabit listesi veri sözleşmeleri ile eşleştirilir.

- Diğer tüm basit tür kısıtlamaları, kısıttıkları türlere eşlenir. Örneğin, `xs:int` tam olarak olduğu gibi, bir tamsayı ile eşleme kısıtlaması `xs:int` . İlkel tür eşlemesi hakkında daha fazla bilgi için bkz. tür/temel eşleme.

### <a name="xsrestriction-attributes"></a>\<xs:restriction>: öznitelikler

|Öznitelik|Şema|
|---------------|------------|
|`base`|Desteklenen bir basit tür veya olmalıdır `xs:anyType` .|
|`id`|LIP.|

### <a name="xsrestriction-for-all-other-cases-contents"></a>\<xs:restriction>diğer tüm durumlar için: içerikler

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
|adet|Destekleniyor.|

## <a name="enumeration"></a>Sabit Listesi

### <a name="xsrestriction-for-enumerations-attributes"></a>\<xs:restriction>Numaralandırmalar için: öznitelikler

|Öznitelik|Şema|
|---------------|------------|
|`base`|Varsa, olmalıdır `xs:string` .|
|`id`|LIP.|

### <a name="xsrestriction-for-enumerations-contents"></a>\<xs:restriction>Numaralandırmalar için: içerikler

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
|`enumeration`|Destekleniyor. "Kimlik" numaralandırması yok sayılır ve "değer" sabit listesi veri sözleşmesindeki değer adıyla eşlenir.|
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

Bu sınıf, tarafından aşağıdaki şemaya eşlenir `DataContractSerializer` . Numaralandırma değerleri 1 ' den başlar, `xs:annotation` bloklar oluşturulmaz.

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

### \<xs:list>

`DataContractSerializer`ile işaretlenmiş numaralandırma türlerini `System.FlagsAttribute` `xs:list` öğesinden türetilmişle eşleştirir `xs:string` . Başka `xs:list` Çeşitlemeler desteklenmez.

### <a name="xslist-attributes"></a>\<xs:list>: öznitelikler

|Öznitelik|Şema|
|---------------|------------|
|`itemType`|Inı.|
|`id`|LIP.|

### <a name="xslist-contents"></a>\<xs:list>: içerik

|İçindekiler|Şema|
|--------------|------------|
|`simpleType`|Modelinin kullanım kısıtlaması olmalıdır `xs:string` `xs:enumeration` .|

Sabit listesi değeri 2 ilerleme değerinin (bayraklar için varsayılan) bir kuvvetle eşleşmezse, değer `xs:annotation/xs:appInfo/ser:EnumerationValue` öğesinde depolanır.

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

Bir veri sözleşmesi, başka bir veri sözleşmesinden devralınabilir. Bu tür veri sözleşmeleri bir temel ile eşlenir ve XML şema yapısı kullanılarak uzantı türlerine göre türetilir `<xs:extension>` .

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

### <a name="xscomplexcontent-attributes"></a>\<xs:complexContent>: öznitelikler

|Öznitelik|Şema|
|---------------|------------|
|`id`|LIP.|
|`mixed`|False olmalıdır.|

### <a name="xscomplexcontent-contents"></a>\<xs:complexContent>: içerik

|İçindekiler|Şema|
|--------------|------------|
|`restriction`|Yasak, temel = "" dışında `xs:anyType` . İkincisi, öğesinin içeriğini `xs:restriction` doğrudan kapsayıcısının altına yerleştirmeye eşdeğerdir `xs:complexContent` .|
|`extension`|Destekleniyor. Veri sözleşmesi devralmayla eşlenir.|

### <a name="xsextension-in-xscomplexcontent-attributes"></a>\<xs:extension>içinde \<xs:complexContent> : öznitelikler

|Öznitelik|Şema|
|---------------|------------|
|`id`|LIP.|
|`base`|Destekleniyor. Bu türün devraldığı temel veri sözleşmesi türüyle eşlenir.|

### <a name="xsextension-in-xscomplexcontent-contents"></a>\<xs:extension>içinde \<xs:complexContent> : içerik

Kurallar, içerik için ile aynıdır `<xs:complexType>` .

Bir `<xs:sequence>` sağlanmışsa, üye öğeleri türetilmiş veri sözleşmesindeki diğer veri üyeleriyle eşlenir.

Türetilmiş bir tür, temel türdeki bir öğeyle aynı ada sahip bir öğe içeriyorsa, yinelenen öğe bildirimi benzersiz olması için oluşturulan bir adla veri üyesine eşlenir. Benzersiz bir ad bulunana kadar ("member1", "member2" vb.) veri üyesi adına pozitif tamsayı numaraları eklenir. Buna karşılık

- Türetilmiş bir veri sözleşmesinin, temel veri sözleşmesindeki bir veri üyesi ile aynı ada ve türe sahip bir veri üyesi varsa, `DataContractSerializer` Bu ilgili öğeyi türetilmiş tür içinde oluşturur.

- Türetilmiş bir veri sözleşmesinin, temel veri sözleşmesindeki bir veri üyesi ile aynı ada sahip bir veri üyesi, ancak farklı bir tür varsa, bu, `DataContractSerializer` `xs:anyType` hem temel türdeki hem de türetilmiş tür bildirimlerinde türü bir olan bir şemayı içeri aktarır. Özgün tür adı ' de korunur `xs:annotations/xs:appInfo/ser:ActualType/@Name` .

Her iki çeşitleme de, ilgili veri üyelerinin sırasına bağlı olarak belirsiz bir içerik modeli olan bir şemaya neden olabilir.

## <a name="typeprimitive-mapping"></a>Tür/basit eşleme

, `DataContractSerializer` XML şeması temel türleri için aşağıdaki eşlemeyi kullanır.

|XSD türü|.NET türü|
|--------------|---------------|
|`anyType`|<xref:System.Object>.|
|`anySimpleType`|<xref:System.String>.|
|`duration`|<xref:System.TimeSpan>.|
|`dateTime`|<xref:System.DateTime>.|
|`dateTimeOffset`|<xref:System.DateTime>ve <xref:System.TimeSpan> daha fazla. Aşağıdaki DateTimeOffset serileştirme ' i inceleyin.|
|`time`|<xref:System.String>.|
|`date`|<xref:System.String>.|
|`gYearMonth`|<xref:System.String>.|
|`gYear`|<xref:System.String>.|
|`gMonthDay`|<xref:System.String>.|
|`gDay`|<xref:System.String>.|
|`gMonth`|<xref:System.String>.|
|`boolean`|<xref:System.Boolean>|
|`base64Binary`|<xref:System.Byte>dizide.|
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

.NET Framework sürüm 1,0 ' de, <xref:System.Runtime.Serialization.ISerializable> kalıcı veya veri aktarımı için nesneleri serileştirmek üzere genel bir mekanizma olarak sunulmuştur. `ISerializable`Uygulamaları arasında geçirilebileceğini ve uygulayan birçok .NET Framework türü vardır. <xref:System.Runtime.Serialization.DataContractSerializer>doğal olarak sınıflar için destek sağlar `ISerializable` . `DataContractSerializer` `ISerializable` Yalnızca türün QName (nitelenmiş adı) ile farklı olan ve etkin özellik koleksiyonları olan eşleme uygulama şeması türleri. Örneğin, `DataContractSerializer` <xref:System.Exception> ad alanında aşağıdaki xsd türüyle eşlenir `http://schemas.datacontract.org/2004/07/System` .

```xml
<xs:complexType name="Exception">
 <xs:sequence>
  <xs:any minOccurs="0" maxOccurs="unbounded"
      namespace="##local" processContents="skip"/>
 </xs:sequence>
 <xs:attribute ref="ser:FactoryType"/>
</xs:complexType>
```

`ser:FactoryType`Veri sözleşmesi serileştirme şemasında belirtilen isteğe bağlı öznitelik, türü seri durumdan çıkarılabilecek bir fabrika sınıfına başvurur. Factory sınıfı, kullanılan örneğin bilinen türler koleksiyonunun bir parçası olmalıdır `DataContractSerializer` . Bilinen türler hakkında daha fazla bilgi için bkz. [veri sözleşmesi bilinen türler](data-contract-known-types.md).

## <a name="datacontract-serialization-schema"></a>DataContract serileştirme şeması

`DataContractSerializer`Özel bir veri sözleşmesi serileştirme ad alanındaki kullanım türleri, öğeler ve öznitelikler tarafından dışarıya aktarılmış bir dizi şema:

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

- `ser:char`, türünün Unicode karakterlerini temsil edecek şekilde sunulmuştur <xref:System.Char> .

- , `valuespace` ' `xs:duration` A eşlenecek şekilde, sıralı bir küme için azaltılır <xref:System.TimeSpan> .

- `FactoryType`, öğesinden türetilmiş türlerden aktarılmış şemalarda kullanılır <xref:System.Runtime.Serialization.ISerializable> .

## <a name="importing-non-datacontract-schemas"></a>DataContract olmayan şemaları içeri aktarma

`DataContractSerializer``ImportXmlTypes`XSD profiliyle uyumlu olmayan şemaların içeri aktarılması için izin verme seçeneği vardır `DataContractSerializer` (bkz <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> . özelliği). Bu seçeneğin ayarlanması `true` , uyumsuz şema türlerinin kabul edilmesini sağlar ve bunları aşağıdaki uygulamayla eşleyerek, <xref:System.Xml.Serialization.IXmlSerializable> dizisini sarmalayarak <xref:System.Xml.XmlNode> (yalnızca sınıf adı farklıdır).

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

<xref:System.DateTimeOffset>Temel bir tür olarak değerlendirilmez. Bunun yerine, iki bölümden oluşan karmaşık bir öğe olarak serileştirilir. İlk bölüm Tarih saatini temsil eder ve ikinci bölüm Tarih saatinden itibaren olan sapmayı temsil eder. Aşağıdaki kodda serileştirilmiş bir DateTimeOffset değeri örneği gösterilmektedir.

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
- [Veri Anlaşmalarını Kullanma](using-data-contracts.md)
