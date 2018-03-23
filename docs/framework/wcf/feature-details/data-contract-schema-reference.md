---
title: Veri Sözleşmesi Şema Başvurusu
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- data contracts [WCF], schema reference
ms.assetid: 9ebb0ebe-8166-4c93-980a-7c8f1f38f7c0
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 57ccc812aab5df0a9acd99bdcde327d56e4bad8d
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2018
---
# <a name="data-contract-schema-reference"></a>Veri Sözleşmesi Şema Başvurusu
Bu konu, XML Şeması (tarafından kullanılan XSD) alt açıklar <xref:System.Runtime.Serialization.DataContractSerializer> ortak dil tanımlamak için XML serileştirmesi için çalışma zamanı (CLR) türleri.  
  
## <a name="datacontractserializer-mappings"></a>DataContractSerializer eşlemeleri  
 `DataContractSerializer` Gelen meta verileri verildiğinde CLR türleri için XSD eşleyen bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] bir meta veri uç noktası kullanarak hizmet veya [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Veri sözleşmesi seri hale getirici](../../../../docs/framework/wcf/feature-details/data-contract-serializer.md).  
  
 `DataContractSerializer` Ayrıca Web Hizmetleri Açıklama Dili (WSDL) veya XSD belgelere erişmek ve Hizmetleri veya istemciler için veri sözleşmeleri oluşturmak için Svcutil.exe kullanıldığında XSD CLR Türleri ile eşleştirir.  
  
 Bu belgede belirtilen gereksinimlere uygun XML Şeması Örnekleri kullanan CLR Türleri eşlenebilir `DataContractSerializer`.  
  
### <a name="support-levels"></a>Destek düzeyleri  
 `DataContractSerializer` İçin belirli bir XML Şeması özelliği aşağıdaki düzeyde destek sağlar:  
  
-   **Desteklenen**. Bu özelliğin CLR türleri veya öznitelikleri (veya her ikisi de) kullanarak açık eşleme `DataContractSerializer`.  
  
-   **Göz ardı**. Özelliği tarafından alınan şemalarında izin `DataContractSerializer`, ancak kod oluşturma üzerinde hiçbir etkisi olmaz.  
  
-   **Yasak**. `DataContractSerializer` Özelliğini kullanarak bir şema almayı desteklemiyor. Örneğin, bu tür bir özelliği kullanan bir şema ile WSDL erişirken Svcutil.exe kullanmaya geri döner <xref:System.Xml.Serialization.XmlSerializer> yerine. Varsayılan olarak budur.  
  
## <a name="general-information"></a>Genel bilgiler  
  
-   Şema ad alanını konusunda açıklandığı [XML Şeması](http://go.microsoft.com/fwlink/?LinkId=95475). Bu belgede "xs" öneki kullanılır.  
  
-   Herhangi bir şema olmayan ad alanı özniteliklerle göz ardı edilir.  
  
-   Tüm ek açıklamaları (dışında olanlar bu belgede açıklanan) göz ardı edilir.  
  
### <a name="xsschema-attributes"></a>\<xs: Schema >: öznitelikleri  
  
|Öznitelik|DataContract|  
|---------------|------------------|  
|`attributeFormDefault`|Yoksayıldı.|  
|`blockDefault`|Yoksayıldı.|  
|`elementFormDefault`|Nitelenmiş olmalıdır. Tüm öğeleri tarafından desteklendiği bir şema için nitelenmelidir `DataContractSerializer`. Bu iki ayar tarafından gerçekleştirilebilir xs:schema/@elementFormDefault "tam" veya ayarlayarak xs:element/@form için "tam" her tek öğe bildiriminde.|  
|`finalDefault`|Yoksayıldı.|  
|`Id`|Yoksayıldı.|  
|`targetNamespace`|Desteklenen ve veri sözleşmesi ad alanına eşlenir. Bu özniteliği belirtilmezse, boş ad alanı kullanılır. Ayrılmış ad olamaz http://schemas.microsoft.com/2003/10/Serialization/.|  
|`version`|Yoksayıldı.|  
  
### <a name="xsschema-contents"></a>\<xs:schema>: contents  
  
|İçindekiler|Şema|  
|--------------|------------|  
|`include`|Desteklenen. `DataContractSerializer` Xs destekler: içerir ve xs:import. Ancak, Svcutil.exe kısıtlayan aşağıdaki `xs:include/@schemaLocation` ve `xs:import/@location` meta verileri yerel dosyadan yüklendiğinde başvuruyor. Şema dosyaların listesini bir bant dışı mekanizması aracılığıyla ve değil aracılığıyla geçirilmelidir `include` böyle bir durumda; `include`d şema belgeleri yok sayılır.|  
|`redefine`|Alınamaz. Kullanımını `xs:redefine` tarafından yasaklanmış `DataContractSerializer` güvenlik nedenleriyle: `x:redefine` gerektirir `schemaLocation` izlemelidir. Bazı durumlarda DataContract kullanarak Svcutil.exe kullanımını sınırlar `schemaLocation`.|  
|`import`|Desteklenen. `DataContractSerializer` destekleyen `xs:include` ve `xs:import`. Ancak, Svcutil.exe kısıtlayan aşağıdaki `xs:include/@schemaLocation` ve `xs:import/@location` meta verileri yerel dosyadan yüklendiğinde başvuruyor. Şema dosyaların listesini bir bant dışı mekanizması aracılığıyla ve değil aracılığıyla geçirilmelidir `include` böyle bir durumda; `include`d şema belgeleri yok sayılır.|  
|`simpleType`|Desteklenen. Bkz: `xs:simpleType` bölümü.|  
|`complexType`|Desteklenen veri sözleşmeleri eşlenir. Bkz: `xs:complexType` bölümü.|  
|`group`|Yoksayıldı. `DataContractSerializer` kullanımını desteklemez `xs:group`, `xs:attributeGroup`, ve `xs:attribute`. Bu bildirimler alt olarak sayılır `xs:schema`, içinden başvurulamaz ancak `complexType` veya diğer desteklenen yapıları.|  
|`attributeGroup`|Yoksayıldı. `DataContractSerializer` kullanımını desteklemez `xs:group`, `xs:attributeGroup`, ve `xs:attribute`. Bu bildirimler alt olarak sayılır `xs:schema`, içinden başvurulamaz ancak `complexType` veya diğer desteklenen yapıları.|  
|`element`|Desteklenen. Genel bir öğe bildirimi (GED) konusuna bakın.|  
|`attribute`|Yoksayıldı. `DataContractSerializer` kullanımını desteklemez `xs:group`, `xs:attributeGroup`, ve `xs:attribute`. Bu bildirimler alt olarak sayılır `xs:schema`, içinden başvurulamaz ancak `complexType` veya diğer desteklenen yapıları.|  
|`notation`|Yoksayıldı.|  
  
## <a name="complex-types--xscomplextype"></a>Complex Types – \<xs:complexType>  
  
### <a name="general-information"></a>Genel bilgiler  
 Her karmaşık tür \<xs:complexType > bir veri sözleşmesine eşler.  
  
### <a name="xscomplextype-attributes"></a>\<xs:complexType >: öznitelikleri  
  
|Öznitelik|Şema|  
|---------------|------------|  
|`abstract`|False olmalıdır (varsayılan).|  
|`block`|Alınamaz.|  
|`final`|Yoksayıldı.|  
|`id`|Yoksayıldı.|  
|`mixed`|False olmalıdır (varsayılan).|  
|`name`|Desteklenen ve veri sözleşme adına eşlenir. Adında nokta varsa girişiminde türü bir iç türüyle eşleştirmek için yapılır. Örneğin, adlandırılmış bir karmaşık tür `A.B` bir veri sözleşmesi eşlemeleri type diğer bir deyişle bir iç veri sözleşme adına sahip bir türde `A`, ancak böyle bir veri türü yalnızca sözleşme varsa. Birden fazla iç içe geçme düzeyini mümkündür: Örneğin, `A.B.C` iç türünde olmalıdır, ancak yalnızca yapabilirsiniz `A` ve `A.B` hem de mevcut.|  
  
### <a name="xscomplextype-contents"></a>\<xs:complexType >: içeriği  
  
|İçindekiler|Şema|  
|--------------|------------|  
|`simpleContent`|Uzantıları alınamaz.<br /><br /> Kısıtlama yalnızca verilir `anySimpleType`.|  
|`complexContent`|Desteklenen. "Devralma" konusuna bakın.|  
|`group`|Alınamaz.|  
|`all`|Alınamaz.|  
|`choice`|Yasak|  
|`sequence`|Desteklenen bir veri sözleşmesi veri üyeleri eşlenir.|  
|`attribute`|Yasak, olsa bile kullanın (bir özel durumla) = "prohibited". Yalnızca isteğe bağlı öznitelik standart seri hale getirme şeması ad alanından desteklenir. Programlama modeli veri sözleşmesi veri üyeleri için harita değil. Şu anda yalnızca bir öznitelik anlama sahiptir ve ISerializable bölümünde ele alınmıştır. Diğerleri yoksayılır.|  
|`attributeGroup`|Alınamaz. İçinde [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] v1 yayın `DataContractSerializer` varlığını yoksayar `attributeGroup` içinde `xs:complexType`.|  
|`anyAttribute`|Alınamaz.|  
|(boş)|Veri sözleşmesi hiçbir veri üyeleri ile eşlenir.|  
  
### <a name="xssequence-in-a-complex-type-attributes"></a>\<xs: Sequence > bir karmaşık türde: öznitelikleri  
  
|Öznitelik|Şema|  
|---------------|------------|  
|`id`|Yoksayıldı.|  
|`maxOccurs`|1 (varsayılan) olmalıdır.|  
|`minOccurs`|1 (varsayılan) olmalıdır.|  
  
### <a name="xssequence-in-a-complex-type-contents"></a>\<xs: Sequence > bir karmaşık türde: içeriği  
  
|İçindekiler|Şema|  
|--------------|------------|  
|`element`|Her bir örnek veri üyesi eşler.|  
|`group`|Alınamaz.|  
|`choice`|Alınamaz.|  
|`sequence`|Alınamaz.|  
|`any`|Alınamaz.|  
|(boş)|Veri sözleşmesi hiçbir veri üyeleri ile eşlenir.|  
  
## <a name="elements--xselement"></a>Elements – \<xs:element>  
  
### <a name="general-information"></a>Genel bilgiler  
 `<xs:element>` Aşağıdaki bağlamlarda oluşabilir:  
  
-   İçinde oluşabilir bir `<xs:sequence>`, normal (toplama olmayan) veri sözleşmesi veri üyesi açıklar. Bu durumda, `maxOccurs` özniteliği 1 olmalıdır. (0 değerine izin verilmiyor).  
  
-   İçinde oluşabilir bir `<xs:sequence>`, bir koleksiyon veri sözleşmesi veri üyesi açıklar. Bu durumda, `maxOccurs` özniteliği "sınırsız" veya 1'den büyük olmalıdır.  
  
-   İçinde oluşabilir bir `<xs:schema>` bir genel öğesi bildirimi (GED) olarak.  
  
### <a name="xselement-with-maxoccurs1-within-an-xssequence-data-members"></a>\<xs:Element > ile maxOccurs = 1 içinde bir \<xs: Sequence > (veri üyeleri)  
  
|Öznitelik|Şema|  
|---------------|------------|  
|`ref`|Alınamaz.|  
|`name`|Desteklenen veri üye adı eşlenir.|  
|`type`|Desteklenen veri üyesi eşlenir yazın. Daha fazla bilgi için türü/ilkel eşleme bakın. Aksi durumda belirtilen (ve anonim bir tür içermiyor), `xs:anyType` varsayılır.|  
|`block`|Yoksayıldı.|  
|`default`|Alınamaz.|  
|`fixed`|Alınamaz.|  
|`form`|Nitelenmiş olmalıdır. Bu öznitelik aracılığıyla ayarlanabilir `elementFormDefault` üzerinde `xs:schema`.|  
|`id`|Yoksayıldı.|  
|`maxOccurs`|1.|  
|`minOccurs`|Eşlendiği <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> veri üyenin özelliği (`IsRequired` true olduğunda `minOccurs` 1'dir).|  
|`nillable`|Tür eşlemesi etkiler. Türü/ilkel eşleme bakın.|  
  
### <a name="xselement-with-maxoccurs1-within-an-xssequence-collections"></a>\<xs:Element > maxOccurs ile > 1 içinde bir \<xs: Sequence > (koleksiyonu)  
  
-   Eşleşen bir <xref:System.Runtime.Serialization.CollectionDataContractAttribute>.  
  
-   Koleksiyon türleri yalnızca bir xs:element içinde bir xs: Sequence izin verilir.  
  
 Koleksiyonlar aşağıdaki türde olabilir:  
  
-   Normal koleksiyonları (örneğin, diziler).  
  
-   Sözlük koleksiyonları (bir değer diğerine; eşleme Örneğin, bir <xref:System.Collections.Hashtable>).  
  
-   Bir sözlük ve bir anahtar/değer çifti türünde bir dizi arasındaki tek fark oluşturulan programlama modelidir. Belirli bir türde bir sözlük koleksiyonu olduğunu belirtmek için kullanılan bir şema ek açıklama mekanizması vardır.  
  
 Kuralları `ref`, `block`, `default`, `fixed`, `form`, ve `id` öznitelikleridir toplama olmayan servis talebi ile aynıdır. Diğer öznitelikleri aşağıdaki tabloda içerir.  
  
|Öznitelik|Şema|  
|---------------|------------|  
|`name`|Desteklenen, eşlenir <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> özelliğinde `CollectionDataContractAttribute` özniteliği.|  
|`type`|Desteklenen, koleksiyonda depolanan türüne eşlenir.|  
|`maxOccurs`|1'den büyük veya "sınırsız". DC şema "sınırsız" kullanmanız gerekir.|  
|`minOccurs`|Yoksayıldı.|  
|`nillable`|Tür eşlemesi etkiler. Bu öznitelik için Sözlük koleksiyonları göz ardı edilir.|  
  
### <a name="xselement-within-an-xsschema-global-element-declaration"></a>\<xs:Element > içinde bir \<xs: Schema > Genel öğe bildirimi  
  
-   Bir genel öğesi bildirimi (bir şema türü olarak aynı ad ve ad alanı olan veya kendi içinde anonim bir tür tanımlayan GED) türüyle ilişkili olarak kabul edilir.  
  
-   Şema verme: ilişkili GEDs her oluşturulan türü için basit ve karmaşık oluşturulur.  
  
-   Seri durumdan çıkarma/seri hale getirme: ilişkili GEDs kök öğe türü için kullanılır.  
  
-   Şema alma: ilişkili GEDs gerekli değildir ve (türlerini tanımlayın sürece) aşağıdaki kuralları izlerseniz göz ardı edilir.  
  
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
|`type`|Desteklenen ve (anonim bir tür öğeyi içeren sürece) ilişkili türü için ilişkili GEDs eşleşmesi gerekir.|  
  
### <a name="xselement-contents"></a>\<xs:element>: contents  
  
|İçindekiler|Şema|  
|--------------|------------|  
|`simpleType`|Supported.*|  
|`complexType`|Supported.*|  
|`unique`|Yoksayıldı.|  
|`key`|Yoksayıldı.|  
|`keyref`|Yoksayıldı.|  
|(boş)|Desteklenen.|  
  
 \* Kullanırken `simpleType` ve `complexType,` anonim türler için eşleme olduğundan, anonim olmayan türleri ile aynıdır, hiçbir anonim veri sözleşmeleri olmasını dışında ve bir adlandırılmış veri sözleşmesi öğesi adından türetilen oluşturulan bir ad ile oluşturulur. Anonim türler için kurallar aşağıdaki listede yer almaktadır:  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulama ayrıntılarını: varsa `xs:element` adı nokta içeremez, dış veri sözleşmesi türü için bir iç türü anonim tür eşler. Nokta adı içeriyorsa, sonuçta ortaya çıkan veri sözleşmesi türü bağımsızdır (iç bir tür değil).  
  
-   İç türü üretilen veri sözleşme adı noktayla, öğeyi ve "Türü" dize adını ve ardından dış türü veri sözleşmesi adıdır.  
  
-   İle bir veri sözleşmesi bir tür adı zaten var, benzersiz bir ad oluşturulana kadar "1", "2", "3", vb. ekleyerek adı benzersiz yapılır.  
  
## <a name="simple-types---xssimpletype"></a>Basit türler - \<xs:simpleType >  
  
### <a name="xssimpletype-attributes"></a>\<xs:simpleType >: öznitelikleri  
  
|Öznitelik|Şema|  
|---------------|------------|  
|`final`|Yoksayıldı.|  
|`id`|Yoksayıldı.|  
|`name`|Desteklenen veri eşlenir adı sözleşme.|  
  
### <a name="xssimpletype-contents"></a>\<xs:simpleType >: içeriği  
  
|İçindekiler|Şema|  
|--------------|------------|  
|`restriction`|Desteklenen. Numaralandırma veri sözleşmeleri eşlenir. Bu öznitelik, numaralandırma düzeni eşleşmiyorsa yoksayılır. Bkz: `xs:simpleType` kısıtlamaları bölümü.|  
|`list`|Desteklenen. Numaralandırma veri sözleşmeleri bayrak eşler. Bkz: `xs:simpleType` bölümünde listelenmiştir.|  
|`union`|Alınamaz.|  
  
### <a name="xsrestriction"></a>\<xs:restriction>  
  
-   Karmaşık tür kısıtlamaları yalnızca için temel desteklenen = "`xs:anyType`".  
  
-   Basit türü kısıtlamalarını `xs:string` sahip olmayan bir kısıtlama modelleri dışında `xs:enumeration` numaralandırma veri sözleşmelerine eşlenir.  
  
-   Diğer tüm basit tür kısıtlamaları bunlar kısıtlama türlerine eşlenir. Örneğin, bir kısıtlaması `xs:int` gibi bir tamsayıya eşlemeleri `xs:int` kendisi yapar. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] eşleme, ilkel türü türü/ilkel eşleme bakın.  
  
### <a name="xsrestriction-attributes"></a>\<xs:restriction >: öznitelikleri  
  
|Öznitelik|Şema|  
|---------------|------------|  
|`base`|Desteklenen bir basit tür olmalıdır veya `xs:anyType`.|  
|`id`|Yoksayıldı.|  
  
### <a name="xsrestriction-for-all-other-cases-contents"></a>\<xs:restriction > tüm diğer durumlarda: içeriği  
  
|İçindekiler|Şema|  
|--------------|------------|  
|`simpleType`|Varsa, desteklenen bir ilkel türünden türetilmelidir.|  
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
  
### <a name="xsrestriction-for-enumerations-attributes"></a>\<xs:restriction > numaralandırmalar için: öznitelikleri  
  
|Öznitelik|Şema|  
|---------------|------------|  
|`base`|Varsa, olmalıdır `xs:string`.|  
|`id`|Yoksayıldı.|  
  
### <a name="xsrestriction-for-enumerations-contents"></a>\<xs:restriction > numaralandırmalar için: içeriği  
  
|İçindekiler|Şema|  
|--------------|------------|  
|`simpleType`|Varsa, bir numaralandırma kısıtlama veri sözleşmesi (Bu bölüm) tarafından desteklenmesi gerekir.|  
|`minExclusive`|Yoksayıldı.|  
|`minInclusive`|Yoksayıldı.|  
|`maxExclusive`|Yoksayıldı.|  
|`maxInclusive`|Yoksayıldı.|  
|`totalDigits`|Yoksayıldı.|  
|`fractionDigits`|Yoksayıldı.|  
|`length`|Alınamaz.|  
|`minLength`|Alınamaz.|  
|`maxLength`|Alınamaz.|  
|`enumeration`|Desteklenen. Numaralandırma "id" göz ardı edilir ve "value" numaralandırma veri sözleşmesi değer adı eşler.|  
|`whiteSpace`|Alınamaz.|  
|`pattern`|Alınamaz.|  
|(boş)|Desteklenen, boş bir numaralandırma türü eşlenir.|  
  
 Aşağıdaki kod bir C# numaralandırma sınıfı gösterir.  
  
```  
public enum MyEnum  
{  
   first = 3,  
   second = 4,  
   third =5  
```  
  
 }  
  
 Aşağıdaki şemada Bu sınıf eşlendiği `DataContractSerializer`. Numaralandırma değerleri 1'den, başlatırsanız `xs:annotation` blokları oluşturulmaz.  
  
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
 `DataContractSerializer` MAPS Numaralandırma türleri ile işaretlenen `System.FlagsAttribute` için `xs:list` türetilen `xs:string`. Başka `xs:list` Çeşitlemeler desteklenir.  
  
### <a name="xslist-attributes"></a>\<xs:list >: öznitelikleri  
  
|Öznitelik|Şema|  
|---------------|------------|  
|`itemType`|Alınamaz.|  
|`id`|Yoksayıldı.|  
  
### <a name="xslist-contents"></a>\<xs:list >: içeriği  
  
|İçindekiler|Şema|  
|--------------|------------|  
|`simpleType`|Sınırlama listesinden olmalıdır `xs:string` kullanarak `xs:enumeration` modeli.|  
  
 Numaralandırma değeri 2 progression (varsayılan) bayraklarının gücünü izlemiyorsa değeri depolanan `xs:annotation/xs:appInfo/ser:EnumerationValue` öğesi.  
  
 Örneğin, aşağıdaki kod bir numaralandırma türü işaretler.  
  
```  
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
  
 Bu tür için aşağıdaki şema eşler.  
  
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
 Veri sözleşmesi başka bir veri sözleşmesi devralabilirsiniz. Bu tür veri sözleşmeleri eşlemek için bir taban ve kullanarak uzantı türleri tarafından türetilmiş `<xs:extension>` XML Şeması yapısı.  
  
 Veri sözleşmesi bir koleksiyon veri sözleşmesi devralır olamaz.  
  
 Örneğin, aşağıdaki kod, bir veri sözleşmedir.  
  
```  
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
  
 Bu veri sözleşmesi için aşağıdaki XML şema türü bildirimi eşler.  
  
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
  
### <a name="xscomplexcontent-attributes"></a>\<xs:complexContent>: attributes  
  
|Öznitelik|Şema|  
|---------------|------------|  
|`id`|Yoksayıldı.|  
|`mixed`|False olmalıdır.|  
  
### <a name="xscomplexcontent-contents"></a>\<xs:complexContent>: contents  
  
|İçindekiler|Şema|  
|--------------|------------|  
|`restriction`|Yasak, temel dışında = "`xs:anyType`". İkinci içeriğini yerleştirmek için eşdeğer olan `xs:restriction` doğrudan kapsayıcısı altında `xs:complexContent`.|  
|`extension`|Desteklenen. Veri sözleşmesi devralma eşlenir.|  
  
### <a name="xsextension-in-xscomplexcontent-attributes"></a>\<xs:extension> in \<xs:complexContent>: attributes  
  
|Öznitelik|Şema|  
|---------------|------------|  
|`id`|Yoksayıldı.|  
|`base`|Desteklenen. Bu tür öğesinden devralınan eşlemeleri temel veri sözleşmesi yazın.|  
  
### <a name="xsextension-in-xscomplexcontent-contents"></a>\<xs:extension> in \<xs:complexContent>: contents  
 Kuralları aynıdır `<xs:complexType>` içeriği.  
  
 Varsa bir `<xs:sequence>` sağlanır, kendi üyesi türetilmiş veri sözleşmede ek veri üyelerin eşlemeniz öğeleri.  
  
 Türetilmiş bir tür bir taban türü bir öğe ile aynı ada sahip bir öğe içeriyorsa, yinelenen bir öğe bildirimi benzersiz olması için oluşturulan bir ada sahip bir veri üye eşler. Pozitif tamsayı numaraları veri üye adı ("Üye1", "üye2" vb.) eklenen benzersiz bir ad bulunana kadar. Buna karşılık:  
  
-   Bir türetilmiş veri sözleşmesi bir temel veri sözleşmesi veri üyesi olarak aynı ad ve türe sahip bir veri üyesi varsa `DataContractSerializer` türetilen türde de bu karşılık gelen öğesi oluşturur.  
  
-   Bir türetilmiş veri sözleşmesi veri üyesi temel veri sözleşmesi ancak farklı bir tür olarak aynı ada sahip bir veri üyesi varsa `DataContractSerializer` bir şema türü bir öğesiyle alır `xs:anyType` temel türü ve türetilen tür bildirimleri. Özgün tür adı olarak korunur `xs:annotations/xs:appInfo/ser:ActualType/@Name`.  
  
 Her iki Çeşitlemeler, ilgili veri üyeleri terabayt bağlı bir belirsiz içerik modeli ile bir şemaya neden olabilir.  
  
## <a name="typeprimitive-mapping"></a>Türü/temel eşleme  
 `DataContractSerializer` Aşağıdaki eşleme XML Şeması ilkel türler için kullanır.  
  
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
  
## <a name="iserializable-types-mapping"></a>Eşleme ISerializable türleri  
 İçinde [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] sürüm 1.0, `ISerializable` Kalıcılık veya veri aktarımı için nesneleri serileştirmek için genel bir mekanizma olarak sunulmuştur. Vardır birçok [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] türleri uygulayan `ISerializable` ve uygulamalar arasında geçirilebilir. `DataContractSerializer` doğal olarak için destek sağlar `ISerializable` sınıfları. `DataContractSerializer` Eşlemeleri `ISerializable` yalnızca QName türü tarafından (tam adı) farklıdır ve etkili bir şekilde özellik koleksiyonları olan uygulama şema türü. Örneğin, `DataContractSerializer` eşlemeleri <xref:System.Exception> içinde aşağıdaki XSD türüne http://schemas.datacontract.org/2004/07/System ad alanı.  
  
```xml  
<xs:complexType name="Exception">  
 <xs:sequence>  
  <xs:any minOccurs="0" maxOccurs="unbounded"   
      namespace="##local" processContents="skip"/>  
 </xs:sequence>  
 <xs:attribute ref="ser:FactoryType"/>  
</xs:complexType>  
```  
  
 İsteğe bağlı öznitelik `ser:FactoryType` veri sözleşmesi seri hale getirme içinde bildirilen şema türü seri durumdan bir Üreteç sınıfını başvuruyor. Fabrika sınıfı bilinen türleri koleksiyonunu bir parçası olması `DataContractSerializer` kullanılan örnek. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] bilinen türlerini, bkz: [veri sözleşmesi bilinen türleri](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).  
  
## <a name="datacontract-serialization-schema"></a>DataContract seri hale getirme şeması  
 Bir dizi Şemaları dışarı tarafından `DataContractSerializer` türler, öğeleri ve özel bir veri sözleşmesi seri hale getirme ad alanındaki öznitelikler kullanın:  
  
 http://schemas.microsoft.com/2003/10/Serialization  
  
 Bütün bir veri sözleşmesi seri hale getirme şema bildirimi verilmiştir.  
  
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
  
-   `ser:char` Unicode karakterler türü temsil etmek için sunulan <xref:System.Char>.  
  
-   `valuespace` , `xs:duration` Sıralı kümesine daha az için eşlenebilir bir <xref:System.TimeSpan>.  
  
-   `FactoryType` türetilmiş türden dışarı şemalarında kullanılan <xref:System.Runtime.Serialization.ISerializable>.  
  
## <a name="importing-non-datacontract-schemas"></a>DataContract olmayan şemalarını içeri aktarma  
 `DataContractSerializer` sahip `ImportXmlTypes` alma için uymayan şemaların izin vermek için seçeneği `DataContractSerializer` XSD profil (bkz: <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> özelliği). Bu seçeneğin ayarlanması `true` uyumsuz şema türleri ve aşağıdaki uygulama için eşleme sağlar <xref:System.Xml.Serialization.IXmlSerializable> bir dizi kaydırma <xref:System.Xml.XmlNode> (yalnızca sınıf adını farklıdır).  
  
```  
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
 <xref:System.DateTimeOffset> Türü basit tür olarak işlenmez. Bunun yerine, bu iki bölümleri içeren karmaşık bir öğe olarak serileştirilir. İlk bölümü tarih saat ve ikinci bölümü uzaklık tarih saati temsil eder. Seri hale getirilmiş bir DateTimeOffset değer örneği aşağıdaki kodda gösterilir.  
  
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
         <xs:elementname="OffsetMinutes" type="xs:short"  
         minOccurs="1" maxOccurs="1" />  
      </xs:sequence>  
   </xs:complexType>  
</xs:schema>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 <xref:System.Runtime.Serialization.XsdDataContractImporter>  
 [Veri Anlaşmalarını Kullanma](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
