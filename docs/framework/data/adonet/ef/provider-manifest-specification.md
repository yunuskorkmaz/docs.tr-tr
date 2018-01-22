---
title: "Sağlayıcı bildirimi belirtimi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bb450b47-8951-4f99-9350-26f05a4d4e46
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 85096406ae8996713d4861c805d75af42d8c1813
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="provider-manifest-specification"></a>Sağlayıcı bildirimi belirtimi
Bu bölümde, nasıl bir veri deposu sağlayıcısı türler ve İşlevler veri deposunda destekleyebilir anlatılmaktadır.  
  
 Varlık Hizmetleri belirli veri depolama sağlayıcısı bağımsız olarak çalışır henüz hala modelleri, eşlemeleri ve sorguları bir temel alınan veri deposuyla nasıl etkileşim açıkça tanımlamak bir veri sağlayıcı sağlar. Bir Soyutlama Katmanı varlık Hizmetleri yalnızca bir özel veri deposu veya veri sağlayıcısı hedeflenen.  
  
 Sağlayıcının desteklediği türleri, doğrudan veya dolaylı olarak temel alınan veritabanı tarafından desteklenir. Bu tür mutlaka tam deposu türlerini ancak sağlayıcının kullandığı desteklemek için türleri olmayan [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Sağlayıcı/deposu türlerini varlık veri modeli (EDM) terimler açıklanmıştır.  
  
 Veri deposu tarafından desteklenen işlevler için parametre ve dönüş türleri'EDM koşullarını belirtilir.  
  
## <a name="requirements"></a>Gereksinimler  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Ve veri deposuna veri geri ve İleri içinde bilinen herhangi bir veri kaybı veya kesme olmadan türlerini geçirebilmek için gerekir.  
  
 Sağlayıcı bildirimi tasarım zamanında veri deposunda bir bağlantı açmak zorunda kalmadan araçları tarafından yüklenebilir olması gerekir.  
  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Önemli bir durumdur, ancak temel alınan veri deposu çalışmıyor olabilir. Zaman EDM yapıları (tanımlayıcıları ve örneğin tür adları) tanımlanan ve kullanılan bildiriminde kullandıkları gerekir [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] büyük-küçük harf duyarlılığı. Büyük küçük harfe duyarlı veri deposu öğeleri sağlayıcı bildiriminde görünüyorsa, bu büyük/küçük harf sağlayıcı bildiriminde tutulması gerekir.  
  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Tüm veri sağlayıcıları için bir sağlayıcı bildirimi gerektirir. Bir sağlayıcı sahip olmayan bir sağlayıcı kullanmayı denerseniz ile bildirim [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], bir hata iletisi alır.  
  
 Özel durum türleri aşağıdaki tabloda açıklanmaktadır [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] sağlayıcı etkileşiminin özel durumları ortaya zaman throw:  
  
|Sorun|Özel Durum|  
|-----------|---------------|  
|Sağlayıcı GetProviderManifest içinde DbProviderServices desteklemiyor.|ProviderIncompatibleException|  
|Eksik sağlayıcı bildirimi: sağlayıcının döndürdüğü `null` sağlayıcı bildirimi almaya çalışırken.|ProviderIncompatibleException|  
|Geçersiz sağlayıcı bildirimi: sağlayıcı bildirimi almaya çalışırken geçersiz XML sağlayıcı döndürür.|ProviderIncompatibleException|  
  
## <a name="scenarios"></a>Senaryolar  
 Bir sağlayıcı, aşağıdaki senaryolarda desteklemesi gerekir:  
  
### <a name="writing-a-provider-with-symmetric-type-mapping"></a>Simetrik türü eşlemesi sahip bir sağlayıcı yazma  
 İçin bir sağlayıcı yazma [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] eşleme yönü bakılmaksızın tek bir EDM türü her depo türü burada eşleştirir. Tür sistemi basit olduğundan veya EDM türleri eşleşir, karşılık gelen çok basit bir eşleşme EDM türüne sahip olan bir sağlayıcı türü için simetrik bir çözüm kullanabilirsiniz.  
  
 Kendi etki alanı basitliği ve statik bildirim temelli sağlayıcı bildirimi üreten kullanabilirsiniz.  
  
 İki bölüme sahip bir XML dosyasına yazma:  
  
-   "EDM karşılık gelen" depo türü veya işlev açısından ifade sağlayıcısı türlerinin listesi. Depolama türleri karşılık gelen EDM türleri sahip. Depo işlevleri karşılık gelen EDM işlevleri vardır. Örneğin, varchar bir SQL Server türüdür ancak karşılık gelen EDM türü dizedir.  
  
-   Parametre ve dönüş türleri'EDM koşullarını burada belirtilmiştir sağlayıcısı tarafından desteklenen işlevlerin listesi.  
  
### <a name="writing-a-provider-with-asymmetric-type-mapping"></a>Asimetrik türü eşlemesi sahip bir sağlayıcı yazma  
 Ne zaman, bir veri deposu sağlayıcısı için yazma [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], bazı türleri sağlayıcısı EDM türü eşlemesinden farklı için eşleme EDM sağlayıcısı türü. EDM PrimitiveTypeKind.String(MaxLength=4000) nvarchar(4000) eşlemeleri sırada örneği için sınırsız EDM PrimitiveTypeKind.String nvarchar(4000) sağlayıcısında eşleme.  
  
 İki bölüme sahip bir XML dosyasına yazma:  
  
-   Sağlayıcı türlerinin bir listesini EDM terimleriyle ifade edilen ve her iki yön için eşleme tanımlayın: EDM sağlayıcısı ve sağlayıcı EDM.  
  
-   Parametre ve dönüş türleri'EDM koşullarını burada belirtilmiştir sağlayıcısı tarafından desteklenen işlevlerin listesi.  
  
## <a name="provider-manifest-discoverability"></a>Sağlayıcı bildirimi bulunabilirliği  
 Bildirim varlık Hizmetleri (örneğin araçları veya sorgu) birkaç bileşen türü tarafından dolaylı olarak kullanılır, ancak daha fazla meta veri kullanımı ile tarafından doğrudan işlevden meta verileri yükleyicisi depolayın.  
  
 ![dfb3d02b&#45;7a8c&#45;4d51&#45;ac5a&#45;a73d8aa145e6](../../../../../docs/framework/data/adonet/ef/media/dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6.gif "dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6")  
  
 Ancak, belirli bir sağlayıcı mağazaya veya aynı deponun farklı sürümlerini destekleyebilir. Bu nedenle, bir sağlayıcı her desteklenen veri deposu için farklı bir bildirim bildirilmesi gerekir.  
  
### <a name="provider-manifest-token"></a>Sağlayıcı bildirim belirteci  
 Bir veri deposu bağlantısı açıldığında, sağlayıcı sağ bildirimi döndürmek bilgi için sorgulayabilirsiniz. Bu bağlantı bilgilerini kullanılabilir olduğu veya ne zaman mağazaya bağlanmanıza mümkün değildir çevrimdışı senaryolarda mümkün olmayabilir. Kullanarak bildirim tanımlamak `ProviderManifestToken` özniteliği `Schema` .ssdl dosyasındaki öğesi. Bu öznitelik için gerekli bir biçim yoktur; Sağlayıcı bağlantı deposuna açmadan bildirim tanımlamak için gereken en düşük bilgileri seçer.  
  
 Örneğin:  
  
```xml  
<Schema Namespace="Northwind" Provider="System.Data.SqlClient" ProviderManifestToken="2005" xmlns:edm="http://schemas.microsoft.com/ado/2006/04/edm/ssdl" xmlns="http://schemas.microsoft.com/ado/2006/04/edm/ssdl">  
```  
  
## <a name="provider-manifest-programming-model"></a>Sağlayıcı bildirimi programlama modeli  
 Sağlayıcıları türetilen <xref:System.Data.Common.DbXmlEnabledProviderManifest>, bunları kendi bildirimleri bildirimli olarak belirtmek veren. Aşağıdaki çizimde bir sağlayıcısının sınıf hiyerarşisi gösterir:  
  
 ![None](../../../../../docs/framework/data/adonet/ef/media/d541eba3-2ee6-4cd1-88f5-89d0b2582a6c.gif "d541eba3-2ee6-4cd1-88f5-89d0b2582a6c")  
  
### <a name="discoverability-api"></a>Bulunabilirliği API  
 Sağlayıcı bildirimi (Storeıtemcollection) depolamak meta verileri yükleyicisi tarafından yüklenen, veri kullanarak ya da bağlantı veya sağlayıcı bildirim belirteci depolar.  
  
#### <a name="using-a-data-store-connection"></a>Bir veri deposu bağlantısı kullanarak  
 Veri depoladığınızda bağlantının kullanılabilir olması, DbProviderManifest döndüren GetProviderManifest yönteme geçirilen belirteç döndürülecek DbProvderServices.GetProviderManifestToken çağırın. Bu yöntem GetDbProviderManifestToken sağlayıcının uygulaması için atar.  
  
```  
public string GetProviderManifestToken(DbConnection connection);  
public DbProviderManifest GetProviderManifest(string manifestToken);  
```  
  
#### <a name="using-a-provider-manifest-token"></a>Sağlayıcı bildirim belirteci kullanma  
 Çevrimdışı senaryosu için belirteç SSDL gösteriminden çekilir. SSDL bir ProviderManifestToken belirtmenizi sağlar (bkz [şema öğesi (SSDL)](http://msdn.microsoft.com/library/fec75ae4-7f16-4421-9265-9dac61509222) daha fazla bilgi için). Örneğin, bir bağlantı açılamadı, SSDL bildirimi hakkında bilgi belirten bir sağlayıcı bildirim belirteci ' var.  
  
```  
public DbProviderManifest GetProviderManifest(string manifestToken);  
```  
  
### <a name="provider-manifest-schema"></a>Sağlayıcı bildirimi şeması  
 Her sağlayıcı için tanımlanan bilgileri şeması meta verileri tarafından kullanılması için statik bilgileri içerir:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema elementFormDefault="qualified"  
   xmlns:xs="http://www.w3.org/2001/XMLSchema"  
   targetNamespace="http://schemas.microsoft.com/ado/2006/04/edm/providermanifest"  
   xmlns:pm="http://schemas.microsoft.com/ado/2006/04/edm/providermanifest">  
  
  <xs:element name="ProviderManifest">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="Types" type="pm:TTypes" minOccurs="1" maxOccurs="1" />  
        <xs:element name="Functions" type="pm:TFunctions" minOccurs="0" maxOccurs="1"/>  
      </xs:sequence>  
      <xs:attribute name="Namespace" type="xs:string" use="required"/>  
    </xs:complexType>  
  </xs:element>  
  <xs:complexType name="TVersion">  
    <xs:attribute name="Major" type="xs:int" use="required" />  
    <xs:attribute name="Minor" type="xs:int" use="required" />  
    <xs:attribute name="Build" type="xs:int" use="required" />  
    <xs:attribute name="Revision" type="xs:int" use="required" />  
  </xs:complexType>  
  
  <xs:complexType name="TIntegerFacetDescription">  
    <xs:attribute name="Minimum" type="xs:int" use="optional" />  
    <xs:attribute name="Maximum" type="xs:int" use="optional" />  
    <xs:attribute name="DefaultValue" type="xs:int" use="optional" />  
    <xs:attribute name="Constant" type="xs:boolean" default="false" />  
  </xs:complexType>  
  
  <xs:complexType name="TBooleanFacetDescription">  
    <xs:attribute name="DefaultValue" type="xs:boolean" use="optional" />  
    <xs:attribute name="Constant" type="xs:boolean" default="true" />  
  </xs:complexType>  
  
  <xs:complexType name="TDateTimeFacetDescription">  
    <xs:attribute name="Constant" type="xs:boolean" default="false" />  
  </xs:complexType>  
  
  <xs:complexType name="TFacetDescriptions">  
    <xs:choice maxOccurs="unbounded">  
      <xs:element name="Precision" minOccurs="0" maxOccurs="1" type="pm:TIntegerFacetDescription"/>  
      <xs:element name="Scale" minOccurs="0" maxOccurs="1" type="pm:TIntegerFacetDescription"/>  
      <xs:element name="MaxLength" minOccurs="0" maxOccurs="1" type="pm:TIntegerFacetDescription"/>  
      <xs:element name="Unicode" minOccurs="0" maxOccurs="1" type="pm:TBooleanFacetDescription"/>  
      <xs:element name="FixedLength" minOccurs="0" maxOccurs="1" type="pm:TBooleanFacetDescription"/>  
    </xs:choice>  
  </xs:complexType>  
  
  <xs:complexType name="TType">  
    <xs:sequence>  
      <xs:element name="FacetDescriptions" type="pm:TFacetDescriptions" minOccurs="0" maxOccurs="1"/>  
    </xs:sequence>  
    <xs:attribute name="Name" type="xs:string" use="required"/>  
    <xs:attribute name="PrimitiveTypeKind" type="pm:TPrimitiveTypeKind" use="required" />  
  </xs:complexType>  
  
  <xs:complexType name="TTypes">  
    <xs:sequence>  
      <xs:element name="Type" type="pm:TType" minOccurs="0" maxOccurs="unbounded"/>  
    </xs:sequence>  
  </xs:complexType>  
  
  <xs:attributeGroup name="TFacetAttribute">  
    <xs:attribute name="Precision" type="xs:int" use="optional"/>  
    <xs:attribute name="Scale" type="xs:int" use="optional"/>  
    <xs:attribute name="MaxLength" type="xs:int" use="optional"/>  
    <xs:attribute name="Unicode" type="xs:boolean" use="optional"/>  
    <xs:attribute name="FixedLength" type="xs:boolean" use="optional"/>  
  </xs:attributeGroup>  
  
  <xs:complexType name="TFunctionParameter">  
    <xs:attribute name="Name" type="xs:string" use="required" />  
    <xs:attribute name="Type" type="xs:string" use="required" />  
    <xs:attributeGroup ref="pm:TFacetAttribute" />  
    <xs:attribute name="Mode" type="pm:TParameterDirection" use="required" />  
  </xs:complexType>  
  
  <xs:complexType name="TReturnType">  
    <xs:attribute name="Type" type="xs:string" use="required" />  
    <xs:attributeGroup ref="pm:TFacetAttribute" />  
  </xs:complexType>  
  
  <xs:complexType name="TFunction">  
    <xs:choice minOccurs="0" maxOccurs ="unbounded">  
      <xs:element name ="ReturnType" type="pm:TReturnType" minOccurs="0" maxOccurs="1" />  
      <xs:element name="Parameter" type="pm:TFunctionParameter" minOccurs="0" maxOccurs="unbounded"/>  
    </xs:choice>  
    <xs:attribute name="Name" type="xs:string" use="required" />  
    <xs:attribute name="Aggregate" type="xs:boolean" use="optional" />  
    <xs:attribute name="BuiltIn" type="xs:boolean" use="optional" />  
    <xs:attribute name="StoreFunctionName" type="xs:string" use="optional" />  
    <xs:attribute name="NiladicFunction" type="xs:boolean" use="optional" />  
    <xs:attribute name="ParameterTypeSemantics" type="pm:TParameterTypeSemantics" use="optional" default="AllowImplicitConversion" />  
  </xs:complexType>  
  
  <xs:complexType name="TFunctions">  
    <xs:sequence>  
      <xs:element name="Function" type="pm:TFunction" minOccurs="0" maxOccurs="unbounded"/>  
    </xs:sequence>  
  </xs:complexType>  
  
  <xs:simpleType name="TPrimitiveTypeKind">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="Binary"/>  
      <xs:enumeration value="Boolean"/>  
      <xs:enumeration value="Byte"/>  
      <xs:enumeration value="Decimal"/>  
      <xs:enumeration value="DateTime"/>  
      <xs:enumeration value="Time"/>  
      <xs:enumeration value="DateTimeOffset"/>          
      <xs:enumeration value="Double"/>  
      <xs:enumeration value="Guid"/>  
      <xs:enumeration value="Single"/>  
      <xs:enumeration value="SByte"/>  
      <xs:enumeration value="Int16"/>  
      <xs:enumeration value="Int32"/>  
      <xs:enumeration value="Int64"/>  
      <xs:enumeration value="String"/>  
    </xs:restriction>  
  </xs:simpleType>  
  
  <xs:simpleType name="TParameterDirection">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="In"/>  
      <xs:enumeration value="Out"/>  
      <xs:enumeration value="InOut"/>  
    </xs:restriction>  
  </xs:simpleType>  
  
  <xs:simpleType name="TParameterTypeSemantics">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="ExactMatchOnly" />  
      <xs:enumeration value="AllowImplicitPromotion" />  
      <xs:enumeration value="AllowImplicitConversion" />  
    </xs:restriction>  
  </xs:simpleType>  
</xs:schema>  
```  
  
#### <a name="types-node"></a>Türleri düğümü  
 Sağlayıcı bildiriminde türleri düğümünü veri deposu veya sağlayıcısı aracılığıyla yerel olarak desteklenen türleri hakkında bilgi içerir.  
  
##### <a name="type-node"></a>Türü düğümü  
 Her tür düğümünün EDM açısından bir sağlayıcı türü tanımlar. Tür düğüm adı sağlayıcı türü ve bu tür eşlemesi açıklamak için eşlendiği model türünü ve modelleri için ilgili bilgiler açıklanmaktadır.  
  
 Bu tür bilgiler sağlayıcı bildiriminde express için her TypeInformation bildirim her türü için birden fazla model açıklamaları tanımlamanız gerekir:  
  
|Öznitelik adı|Veri Türü|Gerekli|Varsayılan Değer|Açıklama|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|Ad|Dize|Evet|yok|Sağlayıcıya özel veri türü adı|  
|PrimitiveTypeKind|PrimitiveTypeKind|Evet|yok|EDM türü adı|  
  
###### <a name="function-node"></a>İşlev düğümü  
 Her işlevi sağlayıcı üzerinden kullanılabilen tek bir işlevi tanımlar.  
  
|Öznitelik adı|Veri Türü|Gerekli|Varsayılan Değer|Açıklama|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|Ad|Dize|Evet|yok|İşlevin tanımlayıcı/adı|  
|ReturnType|Dize|Hayır|Geçersiz kılma|İşlevin EDM dönüş türü|  
|Toplama|Boole değeri|Hayır|False|İşlevi bir toplama işlevinde ise true|  
|BuiltIn|Boole değeri|Hayır|Doğru|Veri deposuna işlevi oluşturulursa true|  
|StoreFunctionName|Dize|Hayır|\<Adı >|Veri deposunda işlev adı.  Bir işlev adlarını yeniden yönlendirilmesini düzeyi için sağlar.|  
|NiladicFunction|Boole değeri|Hayır|False|İşlev parametreleri gerektirmez ve hiçbir parametre olmadan çağrılırsa true|  
|ParameterType<br /><br /> Semantiği|ParameterSemantics|Hayır|AllowImplicit<br /><br /> Dönüştürme|Sorgu ardışık düzen parametre türü değiştirme ile nasıl ele alması gerektiğini seçeneği:<br /><br /> -   ExactMatchOnly<br />-   AllowImplicitPromotion<br />-   AllowImplicitConversion|  
  
 **Parametreleri düğümü**  
  
 Her işlevi bir veya daha fazla parametre düğümlerinin bir koleksiyonu vardır.  
  
|Öznitelik adı|Veri Türü|Gerekli|Varsayılan Değer|Açıklama|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|Ad|Dize|Evet|yok|Tanımlayıcı/parametrenin adı.|  
|Tür|Dize|Evet|yok|Parametrenin EDM türü.|  
|Mod|Parametre<br /><br /> Yön|Evet|yok|Parametre yönü:<br /><br /> -   in<br />-out<br />-ınout|  
  
##### <a name="namespace-attribute"></a>Namespace özniteliği  
 Her bir veri deposu sağlayıcısı, bir ad alanı veya grup bildiriminde tanımlanan bilgileri için ad alanları tanımlamanız gerekir. Bu ad alanı varlık SQL sorgularında işlevlerini ve türlerini adlarını çözmek için kullanılabilir. Örneğin: SqlServer. Bu ad alanı varlık SQL sorguları tarafından desteklenen standart işlevleri için varlık Hizmetleri tarafından tanımlanan kurallı ad alanı, EDM, farklı olmalıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Entity Framework Veri Sağlayıcısı Yazma](../../../../../docs/framework/data/adonet/ef/writing-an-ef-data-provider.md)
