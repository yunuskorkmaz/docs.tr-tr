---
title: Sağlayıcı Bildirimi Belirtimi
ms.date: 03/30/2017
ms.assetid: bb450b47-8951-4f99-9350-26f05a4d4e46
ms.openlocfilehash: 28bae8a6e249aa1fdab3c67759c8f8575cbdaa10
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149732"
---
# <a name="provider-manifest-specification"></a>Sağlayıcı Bildirimi Belirtimi
Bu bölümde, bir veri deposu sağlayıcısının veri deposundaki türleri ve işlevleri nasıl destekleyebilir ilerler.  
  
 Varlık Hizmetleri, belirli bir veri deposu sağlayıcısından bağımsız olarak çalışır, ancak yine de bir veri sağlayıcısının modellerin, eşlemelerin ve sorguların temel bir veri deposuyla nasıl etkileşimde olduğunu açıkça tanımlamasına olanak tanır. Bir soyutlama katmanı olmadan, Varlık Hizmetleri yalnızca belirli bir veri deposuveya veri sağlayıcısını hedefleyebilir.  
  
 Sağlayıcının desteklediği türler, temel veritabanı tarafından doğrudan veya dolaylı olarak desteklenir. Bu türler tam depo türleri değil, sağlayıcının Varlık Çerçevesini desteklemek için kullandığı türlerdir. Sağlayıcı/depo türleri Varlık Veri Modeli (EDM) terimlerinde açıklanmıştır.  
  
 Veri deposu tarafından desteklenen işlevler için parametre ve iade türleri EDM terimleriyle belirtilir.  
  
## <a name="requirements"></a>Gereksinimler  
 Varlık Çerçevesi ve veri deposunun, herhangi bir veri kaybı veya kesilme olmaksızın bilinen türlerde verileri ileri geri aktarabilmesi gerekir.  
  
 Sağlayıcı bildirimi, veri deposuna bağlantı açmak zorunda kalmadan tasarım zamanında araçlar tarafından yüklenebilir olmalıdır.  
  
 Varlık Çerçevesi büyük/küçük harf duyarlıdır, ancak temel veri deposu olmayabilir. EDM yapıları (tanımlayıcılar ve tür adları, örneğin) tanımlandığında ve bildirimde kullanıldığında, Varlık Çerçevesi durum hassasiyetini kullanmaları gerekir. Örnek olay açısından duyarlı olabilecek veri depolama öğeleri sağlayıcı bildiriminde görünürse, kasanın sağlayıcı bildiriminde tutulması gerekir.  
  
 Varlık Çerçevesi, tüm veri sağlayıcıları için bir sağlayıcı bildirimi gerektirir. Varlık Çerçevesi ile sağlayıcı bildirimi olmayan bir sağlayıcı kullanmaya çalışırsanız, bir hata alırsınız.  
  
 Aşağıdaki tabloda, sağlayıcı etkileşimi yoluyla özel durumlar ortaya çıktığında Varlık Çerçevesi'nin atacağı özel durum türleri açıklanmaktadır:  
  
|Sorun|Özel durum|  
|-----------|---------------|  
|Sağlayıcı, DbProviderServices'te GetProviderManifest'i desteklemez.|Providerıncompatibleexception|  
|Eksik sağlayıcı bildirimi: `null` sağlayıcı bildirimini almaya çalışırken sağlayıcı geri döner.|Providerıncompatibleexception|  
|Geçersiz sağlayıcı bildirimi: sağlayıcı bildirimini almaya çalışırken sağlayıcı geçersiz XML'i döndürür.|Providerıncompatibleexception|  
  
## <a name="scenarios"></a>Senaryolar  
 Sağlayıcı aşağıdaki senaryoları desteklemelidir:  
  
### <a name="writing-a-provider-with-symmetric-type-mapping"></a>Simetrik Tip Eşlemeli Sağlayıcı Yazma  
 Eşleme yönü ne olursa olsun, her mağaza türü tek bir EDM türüne eşlem ler yaptığı Entity Framework için bir sağlayıcı yazabilirsiniz. EDM türüne karşılık gelen çok basit eşleme türüne sahip bir sağlayıcı türü için, tür sistemi basit olduğundan veya EDM türleri ile eşleştiğinden simetrik bir çözüm kullanabilirsiniz.  
  
 Etki alanlarının basitliğini kullanabilir ve statik bir bildirim sağlayıcı bildirimi oluşturabilirsiniz.  
  
 İki bölümden bir XML dosyası yazarsınız:  
  
- Bir mağaza türü veya işlevinin "EDM muadili" açısından ifade edilen sağlayıcı türlerinin listesi. Mağaza türlerinin benzer EDM türleri vardır. Mağaza işlevleri karşılık gelen EDM işlevlerine sahiptir. Örneğin, varchar bir SQL Server türüdür, ancak karşılık gelen EDM türü dizedir.  
  
- Parametre ve dönüş türlerinin EDM terimleriyle ifade edildiği sağlayıcı tarafından desteklenen işlevlerin listesi.  
  
### <a name="writing-a-provider-with-asymmetric-type-mapping"></a>Asimetrik Tip Eşlemeli Sağlayıcı Yazma  
 Varlık Çerçevesi için bir veri deposu sağlayıcısı yazarken, bazı türler için EDM'den sağlayıcıya tür eşleme sağlayıcısından EDM türüeşlemeden farklı olabilir. Örneğin, sınırsız EDM PrimitiveTypeKind.String sağlayıcıda nvarchar(4000) ile eşlenebilirken, nvarchar(4000) EDM PrimitiveTypeKind.String(MaxLength=4000) ile eşlenir.  
  
 İki bölümden bir XML dosyası yazarsınız:  
  
- EDM terimleriyle ifade edilen sağlayıcı türlerinin listesi ve her iki yön için eşleme tanımlayın: EDM-to-sağlayıcı ve sağlayıcı-EDM.  
  
- Parametre ve dönüş türlerinin EDM terimleriyle ifade edildiği sağlayıcı tarafından desteklenen işlevlerin listesi.  
  
## <a name="provider-manifest-discoverability"></a>Sağlayıcı Manifesto Keşfedilebilirlik  
 Bildirim, Varlık Hizmetleri'ndeki (Araçlar veya Sorgu gibi) dolaylı olarak birkaç bileşen türü tarafından kullanılır, ancak veri deposu meta veri yükleyicisinin kullanımı yoluyla meta veriler tarafından daha doğrudan yararlanılır.  
  
 ![dfb3d02b&#45;7a8c&#45;4d51&#45;ac5a&#45;a73d8aa145e6](./media/dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6.gif "dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6")  
  
 Ancak, belirli bir sağlayıcı farklı mağazaları veya aynı mağazanın farklı sürümlerini destekleyebilir. Bu nedenle, bir sağlayıcı desteklenen her veri deposu için farklı bir bildirim rapor etmelidir.  
  
### <a name="provider-manifest-token"></a>Sağlayıcı Bildirimi Belirteci  
 Bir veri deposu bağlantısı açıldığında, sağlayıcı doğru bildirimi döndürmek için bilgi sorgulayabilir. Bu, bağlantı bilgilerinin kullanılamadığı çevrimdışı senaryolarda veya mağazaya bağlanmanın mümkün olmadığı durumlarda mümkün olmayabilir. .ssdl `ProviderManifestToken` dosyasındaki öğenin `Schema` özniteliğini kullanarak bildirimi tanımlayın. Bu öznitelik için gerekli bir biçim yoktur; sağlayıcı, mağazaya bağlantı açmadan bir bildirimi tanımlamak için gereken minimum bilgileri seçer.  
  
 Örnek:  
  
```xml  
<Schema Namespace="Northwind" Provider="System.Data.SqlClient" ProviderManifestToken="2005" xmlns:edm="http://schemas.microsoft.com/ado/2006/04/edm/ssdl" xmlns="http://schemas.microsoft.com/ado/2006/04/edm/ssdl">  
```  
  
## <a name="provider-manifest-programming-model"></a>Sağlayıcı Manifesto Programlama Modeli  
 <xref:System.Data.Common.DbXmlEnabledProviderManifest>Sağlayıcılar, bildirimlerini bildirimsel olarak belirtmelerini sağlayan, Aşağıdaki resimde bir sağlayıcının sınıf hiyerarşisi gösterilmektedir:  
  
 ![Yok](./media/d541eba3-2ee6-4cd1-88f5-89d0b2582a6c.gif "d541eba3-2ee6-4cd1-88f5-89d0b2582a6c")  
  
### <a name="discoverability-api"></a>Keşfedilebilirlik API'si  
 Sağlayıcı bildirimi, bir veri deposu bağlantısı veya sağlayıcı bildirimi kullanılarak Store Meta data yükleyici (StoreItemCollection) tarafından yüklenir.  
  
#### <a name="using-a-data-store-connection"></a>Veri Deposu Bağlantısı Kullanma  
 Veri deposu bağlantısı kullanılabilir olduğunda, <xref:System.Data.Common.DbProviderServices.GetProviderManifestToken%2A?displayProperty=nameWithType> <xref:System.Data.Common.DbProviderServices.GetProviderManifest%2A> döndüren <xref:System.Data.Common.DbProviderManifest>yönteme geçirilen belirteci döndürmek için arayın. Bu yöntem sağlayıcının uygulanmasına yetki `GetDbProviderManifestToken`verir.  
  
```csharp
public string GetProviderManifestToken(DbConnection connection);  
public DbProviderManifest GetProviderManifest(string manifestToken);  
```  
  
#### <a name="using-a-provider-manifest-token"></a>Sağlayıcı Bildirimi Belirteci Kullanma  
 Çevrimdışı senaryo için belirteç SSDL gösteriminden seçilir. SSDL, daha fazla bilgi için bir ProviderManifestToken belirtmenize olanak tanır (daha fazla bilgi için [Bkz. Şema Elemanı (SSDL).](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#schema-element-ssdl) Örneğin, bir bağlantı açılamıyorsa, SSDL'de bildirimle ilgili bilgileri belirten bir sağlayıcı bildirimi belirteç vardır.  
  
```csharp
public DbProviderManifest GetProviderManifest(string manifestToken);  
```  
  
### <a name="provider-manifest-schema"></a>Sağlayıcı Manifesto Şeması  
 Her sağlayıcı için tanımlanan bilgi şeması, meta veriler tarafından tüketilecek statik bilgileri içerir:  
  
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
  
#### <a name="types-node"></a>Tür Düğümü  
 Sağlayıcı bildirimindeki Tür düğümü, veri deposu veya sağlayıcı aracılığıyla yerel olarak desteklenen Türler hakkında bilgi içerir.  
  
##### <a name="type-node"></a>Tip Düğümü  
 Her Tür düğümü EDM açısından bir sağlayıcı türünü tanımlar. Tür düğümü sağlayıcı türünün adını ve eşlenere eşlenebilen model türüyle ilgili bilgileri açıklar ve bu tür eşlemi açıklamak için yönlerini gösterir.  
  
 Sağlayıcı bildiriminde bu tür bilgileri ifade etmek için, her TypeInformation bildiriminin her Tür için birkaç farklı açıklama tanımlaması gerekir:  
  
|Öznitelik Adı|Veri Türü|Gerekli|Varsayılan Değer|Açıklama|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|Adı|Dize|Evet|yok|Sağlayıcıya özel veri türü adı|  
|Primitivetypekind|Primitivetypekind|Evet|yok|EDM türü adı|  
  
###### <a name="function-node"></a>Fonksiyon Düğümü  
 Her İşlev sağlayıcı aracılığıyla kullanılabilen tek bir işlevi tanımlar.  
  
|Öznitelik Adı|Veri Türü|Gerekli|Varsayılan Değer|Açıklama|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|Adı|Dize|Evet|yok|İşlevin tanımlayıcısı/adı|  
|Returntype|Dize|Hayır|Void|Fonksiyonun EDM dönüş türü|  
|Toplama|Boole|Hayır|False|İşlev bir toplu işlevse doğru|  
|Yerleşik|Boole|Hayır|True|İşlev veri deposunda yerleşikse doğru|  
|StoreFunctionName|Dize|Hayır|\<İsim>|Veri deposundaki Işlev Adı.  İşlev adlarının yeniden yönlendirme düzeyini sağlar.|  
|NiladicFunction|Boole|Hayır|False|İşlev parametreleri gerektirmiyorsa ve herhangi bir parametre olmadan çağrılırsa doğru|  
|ParametreTürü<br /><br /> Semantiği|ParametreSemantics|Hayır|İzin Kolaylığı<br /><br /> Dönüştürme|Sorgu ardışık lığı parametre türü ikame ile nasıl başa çıkmalıdır seçimi:<br /><br /> - ExactMatchOnly<br />- İzin Basitlik Promosyon<br />- İzin Basit dönüşüm|  
  
 **Parametreler Düğümü**  
  
 Her işlevin bir veya daha fazla Parametre düğümü nden oluşan bir koleksiyonu vardır.  
  
|Öznitelik Adı|Veri Türü|Gerekli|Varsayılan Değer|Açıklama|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|Adı|Dize|Evet|yok|Parametrenin tanımlayıcısı/adı.|  
|Tür|Dize|Evet|yok|Parametrenin EDM türü.|  
|Mod|Parametre<br /><br /> Yön|Evet|yok|Parametrenin yönü:<br /><br /> - içinde<br />- çıkış<br />- inout|  
  
##### <a name="namespace-attribute"></a>Namespace Öznitelik  
 Her veri deposu sağlayıcısı, bildirimde tanımlanan bilgiler için bir ad alanı veya ad alanı grubu tanımlamalıdır. Bu ad alanı, işlevve tür adlarını çözmek için Entity SQL sorgularında kullanılabilir. Örneğin: SqlServer. Bu ad alanı, Entity SQL sorguları tarafından desteklenen standart işlevler için Entity Services tarafından tanımlanan kanonik ad alanı EDM'den farklı olmalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity Framework Veri Sağlayıcısı Yazma](writing-an-ef-data-provider.md)
