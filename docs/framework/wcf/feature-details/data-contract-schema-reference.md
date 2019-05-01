---
title: Veri Sözleşmesi Şema Başvurusu
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts [WCF], schema reference
ms.assetid: 9ebb0ebe-8166-4c93-980a-7c8f1f38f7c0
ms.openlocfilehash: a4ddaaea2133a8adf5271628f442644194a7f453
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61857187"
---
# <a name="data-contract-schema-reference"></a>Veri Sözleşmesi Şema Başvurusu
Bu konu, XML Şeması (tarafından kullanılan XSD) alt açıklar <xref:System.Runtime.Serialization.DataContractSerializer> açıklayan ortak dil çalışma zamanı (CLR) için XML serileştirme türleri.  
  
## <a name="datacontractserializer-mappings"></a>DataContractSerializer eşlemeleri  
 `DataContractSerializer` Meta verileri, meta veri uç noktası'nı kullanarak bir Windows Communication Foundation (WCF) hizmetinden dışarı aktardığınızda, CLR türleri için XSD eşler veya [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Daha fazla bilgi için [veri sözleşmesi serileştiricisi](../../../../docs/framework/wcf/feature-details/data-contract-serializer.md).  
  
 `DataContractSerializer` Ayrıca Web Hizmetleri Açıklama Dili (WSDL) veya XSD belgelere erişmek ve veri sözleşmeleri Hizmetleri veya istemciler için üretmek için Svcutil.exe kullanıldığında XSD CLR türleriyle eşleştirir.  
  
 Bu belgede belirtilen gereksinimlere uygun XML Şeması Örnekleri kullanarak CLR türlerine eşlenebilir `DataContractSerializer`.  
  
### <a name="support-levels"></a>Destek düzeyleri  
 `DataContractSerializer` Aşağıdaki Destek düzeyleri için belirli bir XML Şeması özelliği sağlar:  
  
- **Desteklenen**. Bu özelliğin CLR türleri veya öznitelikleri (veya her ikisi de) kullanarak açık bir eşleme yoktur `DataContractSerializer`.  
  
- **Yoksayılan**. Özelliği tarafından alınan şemalar izin `DataContractSerializer`, ancak kod oluşturma üzerinde hiçbir etkisi olmaz.  
  
- **Yasak**. `DataContractSerializer` Özelliğini kullanarak bir şema almayı desteklemiyor. Örneğin, bu tür bir özelliği kullanan bir şema ile bir WSDL erişirken Svcutil.exe geri kullanarak döner <xref:System.Xml.Serialization.XmlSerializer> yerine. Bu, varsayılan olarak açıktır.  
  
## <a name="general-information"></a>Genel bilgiler  
  
- Şema ad alanı anlatıldığı [XML Şeması](https://go.microsoft.com/fwlink/?LinkId=95475). Bu belgede "xs" öneki kullanılır.  
  
- Bir şema olmayan ad alanı ile herhangi bir özniteliği yok sayılır.  
  
- Ek açıklamaları (olanlar dışında bu belgede açıklanan) göz ardı edilir.  
  
### <a name="xsschema-attributes"></a>\<xs: Schema >: öznitelikler  
  
|Öznitelik|DataContract|  
|---------------|------------------|  
|`attributeFormDefault`|Yoksayıldı.|  
|`blockDefault`|Yoksayıldı.|  
|`elementFormDefault`|Nitelenmelidir. Tüm öğeler için bir şema tarafından desteklenen nitelenmelidir `DataContractSerializer`. Bu iki ayar tarafından gerçekleştirilebilir xs:schema/@elementFormDefault "tam" veya ayarlayarak xs:element/@form için "tam" her tek öğe bildiriminde.|  
|`finalDefault`|Yoksayıldı.|  
|`Id`|Yoksayıldı.|  
|`targetNamespace`|Desteklenen ve veri anlaşması ad alanıyla eşlendi. Bu öznitelik belirtilmezse boş ad alanı kullanılır. Ayrılmış ad alanı olamaz `http://schemas.microsoft.com/2003/10/Serialization/`.|  
|`version`|Yoksayıldı.|  
  
### <a name="xsschema-contents"></a>\<xs:schema>: contents  
  
|İçindekiler|Şema|  
|--------------|------------|  
|`include`|Desteklenen. `DataContractSerializer` Xs destekler: içerir ve xs:import. Ancak, Svcutil.exe sınırlar aşağıdaki `xs:include/@schemaLocation` ve `xs:import/@location` meta verileri bir yerel dosyadan yüklendiğinde başvuruyor. Şema dosyalarını listesi aracılığıyla değil ve bir bant dışı mekanizması aracılığıyla geçirilmelidir `include` böyle bir durumda; `include`d şema belgeleri yok sayılır.|  
|`redefine`|Yasak. Kullanımını `xs:redefine` tarafından yasaklanmış `DataContractSerializer` güvenlik nedenleriyle: `x:redefine` gerektirir `schemaLocation` izlemelidir. Bazı durumlarda, DataContract kullanarak Svcutil.exe kullanımını kısıtlayan `schemaLocation`.|  
|`import`|Desteklenen. `DataContractSerializer` destekleyen `xs:include` ve `xs:import`. Ancak, Svcutil.exe sınırlar aşağıdaki `xs:include/@schemaLocation` ve `xs:import/@location` meta verileri bir yerel dosyadan yüklendiğinde başvuruyor. Şema dosyalarını listesi aracılığıyla değil ve bir bant dışı mekanizması aracılığıyla geçirilmelidir `include` böyle bir durumda; `include`d şema belgeleri yok sayılır.|  
|`simpleType`|Desteklenen. Bkz: `xs:simpleType` bölümü.|  
|`complexType`|Desteklenen veri sözleşmeleri eşlenir. Bkz: `xs:complexType` bölümü.|  
|`group`|Yoksayıldı. `DataContractSerializer` kullanımını desteklemiyor `xs:group`, `xs:attributeGroup`, ve `xs:attribute`. Bu bildirimleri alt öğeleri dikkate alınmaz `xs:schema`, içinde başvurulmuş ancak `complexType` veya desteklenen diğer yapıları.|  
|`attributeGroup`|Yoksayıldı. `DataContractSerializer` kullanımını desteklemiyor `xs:group`, `xs:attributeGroup`, ve `xs:attribute`. Bu bildirimleri alt öğeleri dikkate alınmaz `xs:schema`, içinde başvurulmuş ancak `complexType` veya desteklenen diğer yapıları.|  
|`element`|Desteklenen. Genel öğe bildirimi (hazırlanmış) bakın.|  
|`attribute`|Yoksayıldı. `DataContractSerializer` kullanımını desteklemiyor `xs:group`, `xs:attributeGroup`, ve `xs:attribute`. Bu bildirimleri alt öğeleri dikkate alınmaz `xs:schema`, içinde başvurulmuş ancak `complexType` veya desteklenen diğer yapıları.|  
|`notation`|Yoksayıldı.|  
  
## <a name="complex-types--xscomplextype"></a>Karmaşık türler – \<xs:complexType >  
  
### <a name="general-information"></a>Genel bilgiler  
 Her bir karmaşık türü \<xs:complexType > bir veri sözleşmesine eşler.  
  
### <a name="xscomplextype-attributes"></a>\<xs:complexType >: öznitelikler  
  
|Öznitelik|Şema|  
|---------------|------------|  
|`abstract`|False olmalıdır (varsayılan).|  
|`block`|Yasak.|  
|`final`|Yoksayıldı.|  
|`id`|Yoksayıldı.|  
|`mixed`|False olmalıdır (varsayılan).|  
|`name`|Desteklenen ve veri anlaşması adına eşlenir. Adında nokta varsa, bir iç türü için eşleme türü için girişiminde yapılır. Örneğin, adında bir karmaşık tür `A.B` veri anlaşması eşlenir tür veri anlaşması adına sahip bir türün bir iç türü `A`, ancak böyle bir veri türü yalnızca sözleşme yoksa. Birden fazla iç içe geçme düzeyine mümkündür: Örneğin, `A.B.C` bir iç türünde olması gerekir, ancak yalnızca olabilir `A` ve `A.B` her ikisi de mevcut.|  
  
### <a name="xscomplextype-contents"></a>\<xs:complexType >: içeriği  
  
|İçindekiler|Şema|  
|--------------|------------|  
|`simpleContent`|Uzantıları yasaktır.<br /><br /> Kısıtlama yalnızca verilir `anySimpleType`.|  
|`complexContent`|Desteklenen. "Devralma" konusuna bakın.|  
|`group`|Yasak.|  
|`all`|Yasak.|  
|`choice`|Yasak|  
|`sequence`|Desteklenen bir veri anlaşması veri üyeleri eşlenir.|  
|`attribute`|Yasak, bile kullanın (bir durumla) = "prohibited". Yalnızca standart serileştirme Şema ad alanından isteğe bağlı öznitelikleri desteklenir. Programlama modeli veri anlaşması veri üyeleri eşlemeyin. Şu anda yalnızca tek bir özniteliğe anlamı vardır ve ISerializable bölümde ele alınmıştır. Diğerleri yoksayılır.|  
|`attributeGroup`|Yasak. WCF v1 sürümdeki `DataContractSerializer` varlığını yoksayar `attributeGroup` içinde `xs:complexType`.|  
|`anyAttribute`|Yasak.|  
|(boş)|Bir veri anlaşması hiçbir veri üyeleri ile eşlenir.|  
  
### <a name="xssequence-in-a-complex-type-attributes"></a>\<xs:Sequence > bir karmaşık türde: öznitelikler  
  
|Öznitelik|Şema|  
|---------------|------------|  
|`id`|Yoksayıldı.|  
|`maxOccurs`|1 (varsayılan) olmalıdır.|  
|`minOccurs`|1 (varsayılan) olmalıdır.|  
  
### <a name="xssequence-in-a-complex-type-contents"></a>\<xs:Sequence > bir karmaşık türde: içeriği  
  
|İçindekiler|Şema|  
|--------------|------------|  
|`element`|Her örnek, bir veri üyesini eşler.|  
|`group`|Yasak.|  
|`choice`|Yasak.|  
|`sequence`|Yasak.|  
|`any`|Yasak.|  
|(boş)|Bir veri anlaşması hiçbir veri üyeleri ile eşlenir.|  
  
## <a name="elements--xselement"></a>Öğeleri – \<xs:element >  
  
### <a name="general-information"></a>Genel bilgiler  
 `<xs:element>` şu bağlamlarda oluşabilir:  
  
- İçinde ortaya çıkabilir bir `<xs:sequence>`, bir normal (koleksiyon dışı) veri anlaşması veri üyesi açıklar. Bu durumda, `maxOccurs` öznitelik 1 olmalıdır. (0 değerine izin verilmez).  
  
- İçinde ortaya çıkabilir bir `<xs:sequence>`, bir koleksiyon veri anlaşması veri üyesi açıklar. Bu durumda, `maxOccurs` 1'den büyük veya "sınırsız" özniteliği olmalıdır.  
  
- İçinde ortaya çıkabilir bir `<xs:schema>` bir genel öğe bildirimi (hazırlanmış) olarak.  
  
### <a name="xselement-with-maxoccurs1-within-an-xssequence-data-members"></a>\<xs:Element > ile maxOccurs = 1 içinde bir \<xs:sequence > (veri üyeleri)  
  
|Öznitelik|Şema|  
|---------------|------------|  
|`ref`|Yasak.|  
|`name`|Desteklenen veri üye adına eşlenir.|  
|`type`|Desteklenen veri üyesi eşlenir yazın. Daha fazla bilgi için türü/temel eşleme bakın. Aksi takdirde belirtilen (ve anonim bir tür içermiyor), `xs:anyType` varsayılır.|  
|`block`|Yoksayıldı.|  
|`default`|Yasak.|  
|`fixed`|Yasak.|  
|`form`|Nitelenmelidir. Bu öznitelik aracılığıyla ayarlanabilir `elementFormDefault` üzerinde `xs:schema`.|  
|`id`|Yoksayıldı.|  
|`maxOccurs`|1.|  
|`minOccurs`|Eşlendiği <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> veri üyesi özelliği (`IsRequired` true olduğunda `minOccurs` 1'dir).|  
|`nillable`|Tür eşlemesi etkiler. Eşleme türü/temel bakın.|  
  
### <a name="xselement-with-maxoccurs1-within-an-xssequence-collections"></a>\<xs:Element > ile maxOccurs > 1 içinde bir \<xs:sequence > (koleksiyonlar)  
  
- Eşleyen bir <xref:System.Runtime.Serialization.CollectionDataContractAttribute>.  
  
- Koleksiyon türlerini yalnızca xs: element'ine bir xs:sequence içinde izin verilir.  
  
 Koleksiyonlar aşağıdaki türde olabilir:  
  
- Normal koleksiyonları (örneğin, diziler).  
  
- Sözlük koleksiyonları (bir değer diğerine; eşleme Örneğin, bir <xref:System.Collections.Hashtable>).  
  
- Bir sözlük ve bir anahtar/değer çifti türünde bir dizi arasındaki tek fark oluşturulan programlama modelidir. Verilen tür için bir sözlük koleksiyon olduğunu belirtmek için kullanılan bir şema ek açıklama mekanizması yoktur.  
  
 Kuralları `ref`, `block`, `default`, `fixed`, `form`, ve `id` öznitelikleri olan koleksiyon dışı çalışması için olanla aynıdır. Diğer öznitelikler aşağıdaki tabloda içerir.  
  
|Öznitelik|Şema|  
|---------------|------------|  
|`name`|Desteklenen eşlenir <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> özelliğinde `CollectionDataContractAttribute` özniteliği.|  
|`type`|Desteklenen bir koleksiyonda depolanan türü eşlenir.|  
|`maxOccurs`|1'den büyük veya "sınırsız". DC şema "sınırsız" kullanmanız gerekir.|  
|`minOccurs`|Yoksayıldı.|  
|`nillable`|Tür eşlemesi etkiler. Bu öznitelik sözlüğü koleksiyonlar için göz ardı edilir.|  
  
### <a name="xselement-within-an-xsschema-global-element-declaration"></a>\<xs:Element > içinde bir \<xs: Schema > Genel öğe bildirimi  
  
- Bir genel öğe bildirimi (bir şema türü olarak aynı ad ve ad alanı sahip veya anonim bir tür içinde kendisini tanımlayan hazırlanmış) türüyle ilişkili olduğu söylenir.  
  
- Şema dışarı aktarma: ilişkili GEDs her oluşturulan türü için hem basit hem de karmaşık oluşturulur.  
  
- Seri durumundan çıkarma/seri hale getirme:, ilişkili GEDs kök öğe türü için kullanılır.  
  
- Şema içeri aktarma: ilişkili GEDs gerekli değildir ve (türleri tanımlamadığınız sürece) aşağıdaki kurallar izlerseniz göz ardı edilir.  
  
|Öznitelik|Şema|  
|---------------|------------|  
|`abstract`|İlişkili GEDs için false olmalıdır.|  
|`block`|İçinde ilişkili GEDs alınamaz.|  
|`default`|İçinde ilişkili GEDs alınamaz.|  
|`final`|İlişkili GEDs için false olmalıdır.|  
|`fixed`|İçinde ilişkili GEDs alınamaz.|  
|`id`|Yoksayıldı.|  
|`name`|Desteklenen. İlişkili GEDs tanımına bakın.|  
|`nillable`|İlişkili GEDs için doğru olması gerekir.|  
|`substitutionGroup`|İçinde ilişkili GEDs alınamaz.|  
|`type`|Desteklenen ve (anonim bir tür öğeyi içeren sürece) için ilişkili GEDs türüyle eşleşmelidir.|  
  
### <a name="xselement-contents"></a>\<xs:Element >: içeriği  
  
|İçindekiler|Şema|  
|--------------|------------|  
|`simpleType`|Supported.*|  
|`complexType`|Supported.*|  
|`unique`|Yoksayıldı.|  
|`key`|Yoksayıldı.|  
|`keyref`|Yoksayıldı.|  
|(boş)|Desteklenen.|  
  
 \* Kullanırken `simpleType` ve `complexType,` anonim türler için eşleme olduğundan, anonim olmayan türleri ile aynıdır, hiçbir anonim veri sözleşmeleri olmasını dışında ve böylece öğe adından türetilir oluşturulan bir adla adlandırılmış veri anlaşması oluşturulur. Anonim türler için kuralları aşağıdaki listede verilmiştir:  
  
- WCF uygulama Ayrıntısı: Varsa `xs:element` adının nokta içermediğinden, dış veri anlaşması türü için bir iç türü anonim tür eşler. Adı bir nokta içeriyorsa, sonuçta elde edilen veri anlaşması türü bağımsızdır (iç bir tür değil).  
  
- Oluşturulan veri sözleşmesi iç türü veri anlaşması adına bir nokta, öğe ve dize "Türü" adını dış türündeki adıdır.  
  
- İle bir veri anlaşması ad zaten var, adı benzersiz bir ad oluşturulana kadar "1", "2", "3", vb. eklenerek benzersiz yapılır.  
  
## <a name="simple-types---xssimpletype"></a>Basit türler - \<xs:simpleType >  
  
### <a name="xssimpletype-attributes"></a>\<xs:simpleType >: öznitelikler  
  
|Öznitelik|Şema|  
|---------------|------------|  
|`final`|Yoksayıldı.|  
|`id`|Yoksayıldı.|  
|`name`|Desteklenen veri eşlenir adı sözleşme.|  
  
### <a name="xssimpletype-contents"></a>\<xs:simpleType>: contents  
  
|İçindekiler|Şema|  
|--------------|------------|  
|`restriction`|Desteklenen. Sabit listesi veri sözleşmeleri eşlenir. Bu öznitelik, numaralandırma desenle eşleşmez gözardı edilir. Bkz: `xs:simpleType` kısıtlamaları bölümü.|  
|`list`|Desteklenen. Bayrak sabit listesi veri sözleşmeleri eşlenir. Bkz: `xs:simpleType` bölümünde listelenir.|  
|`union`|Yasak.|  
  
### <a name="xsrestriction"></a>\<xs:restriction>  
  
- Karmaşık tür kısıtlamalar için temel desteklenen = "`xs:anyType`".  
  
- Basit türü kısıtlamalarını `xs:string` sahip olmayan herhangi bir kısıtlama modelleri dışındaki `xs:enumeration` numaralandırma veri sözleşmelerine eşlenir.  
  
- Tüm diğer basit tür kısıtlamaları, bunlar kısıtlama türlerine eşlenir. Örneğin, bir kısıtlaması `xs:int` gibi bir tamsayı değerine eşleyen `xs:int` kendisi yapar. Türü/temel eşleme ilkel tür eşlemesi hakkında daha fazla bilgi için bkz.  
  
### <a name="xsrestriction-attributes"></a>\<xs:restriction >: öznitelikler  
  
|Öznitelik|Şema|  
|---------------|------------|  
|`base`|Desteklenen bir basit tür olmalıdır veya `xs:anyType`.|  
|`id`|Yoksayıldı.|  
  
### <a name="xsrestriction-for-all-other-cases-contents"></a>\<xs:restriction > diğer tüm durumlarda: içeriği  
  
|İçindekiler|Şema|  
|--------------|------------|  
|`simpleType`|Varsa, desteklenen bir temel türünden türetilmesi gerekir.|  
|`minExclusive`|Yoksayıldı.|  
|`minInclusive`|Yoksayıldı.|  
|`maxExclusive`|Yoksayıldı.|  
|`maxInclusive`|Yoksayıldı.|  
|`totalDigits`|Yoksayıldı.|  
|`fractionDigits`|Yoksayıldı.|  
|`length`|Yoksayıldı.|  
|`minLength`|Yoksayıldı.|  
|`maxLength`|Yoksayıldı.|  
|`enumeration`|Yoksayıldı.|  
|`whiteSpace`|Yoksayıldı.|  
|`pattern`|Yoksayıldı.|  
|(boş)|Desteklenen.|  
  
## <a name="enumeration"></a>Sabit Listesi  
  
### <a name="xsrestriction-for-enumerations-attributes"></a>\<xs:restriction > Sabit listeleri için: öznitelikler  
  
|Öznitelik|Şema|  
|---------------|------------|  
|`base`|Varsa, olmalıdır `xs:string`.|  
|`id`|Yoksayıldı.|  
  
### <a name="xsrestriction-for-enumerations-contents"></a>\<xs:restriction > Sabit listeleri için: içeriği  
  
|İçindekiler|Şema|  
|--------------|------------|  
|`simpleType`|Varsa, bir sabit listesi kısıtlama veri anlaşması (Bu bölümde) tarafından desteklenmesi gerekir.|  
|`minExclusive`|Yoksayıldı.|  
|`minInclusive`|Yoksayıldı.|  
|`maxExclusive`|Yoksayıldı.|  
|`maxInclusive`|Yoksayıldı.|  
|`totalDigits`|Yoksayıldı.|  
|`fractionDigits`|Yoksayıldı.|  
|`length`|Yasak.|  
|`minLength`|Yasak.|  
|`maxLength`|Yasak.|  
|`enumeration`|Desteklenen. Sabit listesi "id" dikkate alınmaz ve "value" değeri sabit listesi veri anlaşması adına eşlenir.|  
|`whiteSpace`|Yasak.|  
|`pattern`|Yasak.|  
|(boş)|Desteklenir, boş bir numaralandırma türü eşlenir.|  
  
 Aşağıdaki kod, C# sabit listesi sınıfı gösterir.  
  
```csharp  
public enum MyEnum  
{  
  first = 3,  
  second = 4,  
  third =5  
}  
```  
  
 Aşağıdaki şemada Bu sınıf eşlendiği `DataContractSerializer`. Sabit listesi değerleri 1'den başlatırsanız `xs:annotation` blokları oluşturulmaz.  
  
```xml  
<xs:simpleType name="MyEnum">  
<xs:restriction base="xs:string">  
 <xs:enumeration value="first">  
  <xs:annotation>  
   <xs:appinfo>  
    <EnumerationValue   
     xmlns="http://schemas.microsoft.com/2003/10/Serialization/">  
     3  
    </EnumerationValue>  
   </xs:appinfo>  
  </xs:annotation>  
 </xs:enumeration>  
 <xs:enumeration value="second">  
  <xs:annotation>  
   <xs:appinfo>  
    <EnumerationValue   
     xmlns="http://schemas.microsoft.com/2003/10/Serialization/">  
     4  
    </EnumerationValue>  
   </xs:appinfo>  
  </xs:annotation>  
 </xs:enumeration>  
</xs:restriction>  
</xs:simpleType>  
```  
  
### <a name="xslist"></a>\<xs:list>  
 `DataContractSerializer` Haritalar Numaralandırma türleri ile işaretlenen `System.FlagsAttribute` için `xs:list` türetilen `xs:string`. Başka hiçbir `xs:list` çeşitlemeleri desteklenir.  
  
### <a name="xslist-attributes"></a>\<xs:list >: öznitelikler  
  
|Öznitelik|Şema|  
|---------------|------------|  
|`itemType`|Yasak.|  
|`id`|Yoksayıldı.|  
  
### <a name="xslist-contents"></a>\<xs:list >: içeriği  
  
|İçindekiler|Şema|  
|--------------|------------|  
|`simpleType`|Kısıtlaması olmalıdır `xs:string` kullanarak `xs:enumeration` modeli.|  
  
 Numaralandırma değeri 2 ilerleme (bayrakları için varsayılan) gücünü izlemiyorsa, değeri depolanan `xs:annotation/xs:appInfo/ser:EnumerationValue` öğesi.  
  
 Örneğin, aşağıdaki kod, bir numaralandırma türü işaretler.  
  
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
  
 Bu tür, aşağıdaki şemanın eşler.  
  
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
                <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Se  
rialization/">16</EnumerationValue>  
              </xs:appinfo>  
            </xs:annotation>  
          </xs:enumeration>  
          <xs:enumeration value="AuthWindowsLiveID">  
            <xs:annotation>  
              <xs:appinfo>  
                <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Se  
rialization/">64</EnumerationValue>  
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
 Bir veri anlaşması başka bir veri sözleşme devralabilir. Bu tür veri sözleşmeleri kullanarak uzantı türleri tarafından türetilmiş ve bir temel harita `<xs:extension>` XML Şeması yapısı.  
  
 Bir veri anlaşması bir koleksiyon veri anlaşması ' devralamaz.  
  
 Örneğin, aşağıdaki kod, bir veri sözleşmedir.  
  
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
  
 Bu veri sözleşme aşağıdaki XML şema türü bildirimi için eşler.  
  
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
  
### <a name="xscomplexcontent-attributes"></a>\<xs:complexContent >: öznitelikler  
  
|Öznitelik|Şema|  
|---------------|------------|  
|`id`|Yoksayıldı.|  
|`mixed`|False olmalıdır.|  
  
### <a name="xscomplexcontent-contents"></a>\<xs:complexContent >: içeriği  
  
|İçindekiler|Şema|  
|--------------|------------|  
|`restriction`|Temel durumlar hariç, Yasak, = "`xs:anyType`". İkinci içeriğini yerleştirmeye eşdeğer `xs:restriction` doğrudan kapsayıcı altına `xs:complexContent`.|  
|`extension`|Desteklenen. Veri anlaşma devralma eşlenir.|  
  
### <a name="xsextension-in-xscomplexcontent-attributes"></a>\<xs:extension> in \<xs:complexContent>: attributes  
  
|Öznitelik|Şema|  
|---------------|------------|  
|`id`|Yoksayıldı.|  
|`base`|Desteklenen. Bu tür öğesinden devralır eşlemeleri için temel veri anlaşması türü.|  
  
### <a name="xsextension-in-xscomplexcontent-contents"></a>\<xs:Extension > içinde \<xs:complexContent >: içeriği  
 Kuralları aynıdır `<xs:complexType>` içeriği.  
  
 Varsa bir `<xs:sequence>` sağlanır, kendi üyesi öğeleri eşlemek için türetilmiş veri anlaşması içinde mevcut olan ek veri üyeleri.  
  
 Türetilmiş bir tür bir öğe temel türde aynı ada sahip bir öğe içeriyorsa, benzersiz olması için oluşturulan bir ada sahip bir veri üyesinin yinelenen öğe bildirimi eşler. Pozitif tamsayı veri üye adına ("Üye1", "üye2" vb.) eklenen benzersiz bir ad bulunana kadar. Buna karşılık:  
  
- Bir temel veri sözleşmesi veri üyesi olarak aynı ada ve türe sahip bir veri üyesi türetilmiş veri anlaşması varsa `DataContractSerializer` türetilen türde de bu karşılık gelen öğe oluşturur.  
  
- Temel veri anlaşması ancak farklı bir tür veri üyesi olarak aynı ada sahip bir veri üyesi türetilmiş veri anlaşması varsa `DataContractSerializer` türünde bir öğe ile bir şema alır `xs:anyType` hem türetilen tür bildirimleri, hem de temel türü. Orijinal tür adının de korunur `xs:annotations/xs:appInfo/ser:ActualType/@Name`.  
  
 Her iki Çeşitleme ile ilgili veri üyeleri bazında bağlıdır belirsiz bir içerik modeli, bir şemaya neden olabilir.  
  
## <a name="typeprimitive-mapping"></a>Tür/temel eşleme  
 `DataContractSerializer` Temel türler için XML Şeması aşağıdaki eşlemeyi kullanır.  
  
|XSD türü|.NET türü|  
|--------------|---------------|  
|`anyType`|<xref:System.Object>.|  
|`anySimpleType`|<xref:System.String>.|  
|`duration`|<xref:System.TimeSpan>.|  
|`dateTime`|<xref:System.DateTime>.|  
|`dateTimeOffset`|<xref:System.DateTime> ve <xref:System.TimeSpan> kaydırmanın. DateTimeOffset serileştirme aşağıya bakın.|  
|`time`|<xref:System.String>.|  
|`date`|<xref:System.String>.|  
|`gYearMonth`|<xref:System.String>.|  
|`gYear`|<xref:System.String>.|  
|`gMonthDay`|<xref:System.String>.|  
|`gDay`|<xref:System.String>.|  
|`gMonth`|<xref:System.String>.|  
|`boolean`|<xref:System.Boolean>|  
|`base64Binary`|<xref:System.Byte> dizisi.|  
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
  
## <a name="iserializable-types-mapping"></a>Eşleme ISerializable türler  
 İçinde [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] sürüm 1.0, <xref:System.Runtime.Serialization.ISerializable> Kalıcılık ya da veri aktarımı için nesneleri serileştirmek için genel bir mekanizma olarak kullanıma sunulmuştur. Kullanabileceğiniz birçok [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] türleri uygulayan `ISerializable` ve uygulamalar arasında geçirilebilir. <xref:System.Runtime.Serialization.DataContractSerializer> doğal olarak için destek sağlar `ISerializable` sınıfları. `DataContractSerializer` Eşler `ISerializable` uygulama şema türü, yalnızca QName türü tarafından (tam adı) değişir ve etkili bir şekilde özellik koleksiyonlarıdır. Örneğin, `DataContractSerializer` eşler <xref:System.Exception> aşağıdaki XSD türüne `http://schemas.datacontract.org/2004/07/System` ad alanı.  
  
```xml  
<xs:complexType name="Exception">  
 <xs:sequence>  
  <xs:any minOccurs="0" maxOccurs="unbounded"   
      namespace="##local" processContents="skip"/>  
 </xs:sequence>  
 <xs:attribute ref="ser:FactoryType"/>  
</xs:complexType>  
```  
  
 İsteğe bağlı öznitelik `ser:FactoryType` veri sözleşme serileştirme içinde bildirilen şema türü seri durumdan çıkarabiliyorsa bir Üreteç sınıfını başvuruyor. Fabrika sınıfı Bilinen türlerin koleksiyonuna bir parçası olarak `DataContractSerializer` kullanılan örnek. Bilinen türler hakkında daha fazla bilgi için bkz: [veri sözleşme bilinen türleri](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).  
  
## <a name="datacontract-serialization-schema"></a>DataContract serileştirme şeması  
 Bir dizi Şemaları dışarı tarafından `DataContractSerializer` türleri, öğeleri ve bir özel veri sözleşme serileştirme ad öznitelikleri kullanın:  
  
 `http://schemas.microsoft.com/2003/10/Serialization`
  
 Eksiksiz bir veri sözleşme serileştirme şeması bildirimi verilmiştir.  
  
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
  
 Aşağıdakiler dikkate alınmalıdır:  
  
- `ser:char` tür Unicode karakterlerini temsil etmek için sunulan <xref:System.Char>.  
  
- `valuespace` , `xs:duration` Sıralı bir küme için daha az için eşlenebilir bir <xref:System.TimeSpan>.  
  
- `FactoryType` öğesinden türetilen türler dışarı şemalar kullanılır <xref:System.Runtime.Serialization.ISerializable>.  
  
## <a name="importing-non-datacontract-schemas"></a>DataContract olmayan şemaları alma  
 `DataContractSerializer` sahip `ImportXmlTypes` seçeneği için uygun olmayan şemaları alma izni `DataContractSerializer` XSD profili (bkz <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> özelliği). Bu seçeneğin ayarlanması `true` kabul DSCP şema türleri ve bunları aşağıdaki uygulama için eşleme sağlayan <xref:System.Xml.Serialization.IXmlSerializable> dizisi sarmalama <xref:System.Xml.XmlNode> (yalnızca sınıf adını farklıdır).  
  
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
  
## <a name="datetimeoffset-serialization"></a>DateTimeOffset seri hale getirme  
 <xref:System.DateTimeOffset> Türü bir basit tür olarak işlenmez. Bunun yerine, bu iki bölümleri içeren karmaşık bir öğe olarak serileştirilir. İlk bölümü tarih saat ve ikinci bölümü, tarih saati uzaklığı temsil eder. Aşağıdaki kodda bir örneğini serileştirilmiş bir DateTimeOffset değer gösterilir.  
  
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
  
 Şeması aşağıdaki gibidir.  
  
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
