---
title: Sağlayıcı Bildirimi Belirtimi
ms.date: 03/30/2017
ms.assetid: bb450b47-8951-4f99-9350-26f05a4d4e46
ms.openlocfilehash: cc58bbc82f3930f087b5da0c64afb4f9f03e905b
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854495"
---
# <a name="provider-manifest-specification"></a>Sağlayıcı Bildirimi Belirtimi
Bu bölümde, bir veri deposu sağlayıcısının veri deposundaki türleri ve işlevleri nasıl destekleyebileceği açıklanmaktadır.  
  
 Varlık hizmetleri belirli bir veri deposu sağlayıcısından bağımsız olarak çalışır, ancak bir veri sağlayıcısının model, eşlemeler ve sorguların temel alınan bir veri deposuyla nasıl etkileşim kuracağını açıkça tanımlamasına olanak tanır. Bir soyutlama katmanı olmadan, varlık Hizmetleri yalnızca belirli bir veri deposuna veya veri sağlayıcısına hedeflenebilir.  
  
 Sağlayıcının desteklediği türler, temel alınan veritabanı tarafından doğrudan veya dolaylı olarak desteklenir. Bu türlerin tam depo türleri olması gerekmez, ancak sağlayıcının Entity Framework desteklemek için kullandığı türler. Sağlayıcı/depolama türleri Varlık Veri Modeli (EDM) koşullarında açıklanmıştır.  
  
 Veri deposunun desteklediği işlevlerin parametresi ve dönüş türleri EDM koşullarında belirtilmiştir.  
  
## <a name="requirements"></a>Gereksinimler  
 Entity Framework ve veri deposunun verileri, herhangi bir veri kaybı veya kesilme olmadan bilinen türlerde geri ve ileri geçirebilmesi gerekir.  
  
 Sağlayıcı bildirimi, veri deposuna bir bağlantı açmak zorunda kalmadan tasarım zamanında araçlar tarafından yüklenebilir olmalıdır.  
  
 Entity Framework büyük/küçük harfe duyarlıdır, ancak temel alınan veri deposu olmayabilir. EDM yapıtlar (örneğin, tanımlayıcılar ve tür adları) tanımlandıklarında ve bildiriminde kullanıldığında, Entity Framework büyük/küçük harf duyarlılığı kullanmalıdır. Büyük/küçük harfe duyarlı olabilecek veri deposu öğeleri sağlayıcı bildiriminde görünürse, bu büyük/küçük harf sağlayıcısı bildiriminde saklanması gerekir.  
  
 Entity Framework tüm veri sağlayıcıları için bir sağlayıcı bildirimi gerektirir. Entity Framework bir sağlayıcı bildirimine sahip olmayan bir sağlayıcıyı kullanmayı denerseniz, bir hata alırsınız.  
  
 Aşağıdaki tabloda, sağlayıcı etkileşimi üzerinden özel durumlar ortaya çıktığında Entity Framework özel durumların türleri açıklanmaktadır:  
  
|Sorun|Özel Durum|  
|-----------|---------------|  
|Sağlayıcı, DbProviderServices 'de GetProviderManifest 'i desteklemiyor.|ProviderIncompatibleException|  
|Eksik sağlayıcı bildirimi: sağlayıcı, sağlayıcı `null` bildirimini almaya çalışırken döndürüyor.|ProviderIncompatibleException|  
|Geçersiz sağlayıcı bildirimi: sağlayıcı, sağlayıcı bildirimini almaya çalışırken geçersiz XML döndürüyor.|ProviderIncompatibleException|  
  
## <a name="scenarios"></a>Senaryolar  
 Sağlayıcı aşağıdaki senaryoları desteklemelidir:  
  
### <a name="writing-a-provider-with-symmetric-type-mapping"></a>Simetrik tür eşleme ile sağlayıcı yazma  
 Eşleme yönüne bakılmaksızın her bir mağaza türünün tek bir EDM türüne eşlendiği Entity Framework için bir sağlayıcı yazabilirsiniz. Bir EDM türüne karşılık gelen çok basit eşlemeye sahip bir sağlayıcı türü için, tür sistemi basit veya EDM türleriyle eşleştiğinden, simetrik bir çözüm kullanabilirsiniz.  
  
 Etki alanını basitlik olarak kullanabilir ve statik bir bildirime dayalı sağlayıcı bildirimi oluşturabilirsiniz.  
  
 İki bölümden oluşan bir XML dosyası yazarsınız:  
  
- Bir depo türü veya işlevinin "EDM karşılığı" olarak ifade edilen sağlayıcı türlerinin listesi. Depo türlerinde karşılık gelen EDM türleri var. Depo işlevlerinde karşılık gelen EDM işlevleri vardır. Örneğin, varchar bir SQL Server türüdür, ancak karşılık gelen EDM türü dizedir.  
  
- Sağlayıcı tarafından desteklenen ve parametre ve dönüş türlerinin EDM koşullarında ifade edildiği işlevlerin listesi.  
  
### <a name="writing-a-provider-with-asymmetric-type-mapping"></a>Asimetrik tür eşleme ile sağlayıcı yazma  
 Entity Framework için bir veri deposu sağlayıcısı yazarken, bazı türler için EDM-sağlayıcıya tür eşlemesi sağlayıcıdan EDM tür eşleştirmesinden farklı olabilir. Örneğin, sınırlandırılmamış EDM PrimitiveTypeKind. String, sağlayıcıdaki nvarchar (4000) ile eşleşirken, nvarchar (4000), EDM PrimitiveTypeKind. String (MaxLength = 4000) ile eşlenir.  
  
 İki bölümden oluşan bir XML dosyası yazarsınız:  
  
- EDM koşullarında ifade edilen ve her iki yön için eşlemeyi tanımlayan sağlayıcı türlerinin listesi: EDM-sağlayıcı ve sağlayıcıdan EDM.  
  
- Sağlayıcı tarafından desteklenen ve parametre ve dönüş türlerinin EDM koşullarında ifade edildiği işlevlerin listesi.  
  
## <a name="provider-manifest-discoverability"></a>Sağlayıcı bildirimi bulunabilirliği  
 Bildirim, varlık hizmetlerindeki (örneğin, araçlar veya sorgu) çeşitli bileşen türleri tarafından dolaylı olarak kullanılır, ancak veri deposu meta veri yükleyicisinin kullanımı aracılığıyla meta veriler tarafından daha doğrudan yararlanılabilir.  
  
 ![dfb3d02b&#45;7a8c&#45;4d51&#45;AC5A&#45;a73d8aa145e6](./media/dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6.gif "dfb3d02b-7a8c-4d51-AC5A-a73d8aa145e6")  
  
 Ancak, belirli bir sağlayıcı aynı deponun farklı mağazalarını veya farklı sürümlerini destekleyebilir. Bu nedenle, bir sağlayıcı desteklenen her veri deposu için farklı bir bildirim rapormalıdır.  
  
### <a name="provider-manifest-token"></a>Sağlayıcı bildirim belirteci  
 Bir veri deposu bağlantısı açıldığında sağlayıcı, doğru bildirimi döndürecek bilgileri sorgulayabilir. Bu, bağlantı bilgilerinin kullanılamadığı veya depoya bağlanamamasının mümkün olmadığı çevrimdışı senaryolarda mümkün olmayabilir. . Ssdl dosyasındaki `ProviderManifestToken` `Schema` öğesinin özniteliğini kullanarak bildirimi belirler. Bu öznitelik için gerekli biçim yok; sağlayıcı, depoya bir bağlantı açmadan bir bildirimi tanımlamak için gereken en düşük bilgileri seçer.  
  
 Örneğin:  
  
```xml  
<Schema Namespace="Northwind" Provider="System.Data.SqlClient" ProviderManifestToken="2005" xmlns:edm="http://schemas.microsoft.com/ado/2006/04/edm/ssdl" xmlns="http://schemas.microsoft.com/ado/2006/04/edm/ssdl">  
```  
  
## <a name="provider-manifest-programming-model"></a>Sağlayıcı bildirimi programlama modeli  
 Sağlayıcılar öğesinden <xref:System.Data.Common.DbXmlEnabledProviderManifest>türetilir, bu da kendilerine bildirimleri bildirimli olarak belirtmelerini sağlar. Aşağıdaki çizimde bir sağlayıcının sınıf hiyerarşisi gösterilmektedir:  
  
 ![Hiçbiri](./media/d541eba3-2ee6-4cd1-88f5-89d0b2582a6c.gif "d541eba3-2ee6-4cd1-88f5-89d0b2582a6c")  
  
### <a name="discoverability-api"></a>Keşfedilebilirlik API 'SI  
 Sağlayıcı bildirimi, bir veri deposu bağlantısı veya sağlayıcı bildirim belirteci kullanılarak mağaza meta veri yükleyicisi (StoreItemCollection) tarafından yüklenir.  
  
#### <a name="using-a-data-store-connection"></a>Veri deposu bağlantısı kullanma  
 Veri deposu bağlantısı kullanılabilir olduğunda, ' i döndüren <xref:System.Data.Common.DbProviderServices.GetProviderManifestToken%2A?displayProperty=nameWithType> <xref:System.Data.Common.DbProviderServices.GetProviderManifest%2A> <xref:System.Data.Common.DbProviderManifest>yöntemine geçirilen belirteci döndürmek için çağırın. Bu yöntem, sağlayıcının uygulamasını `GetDbProviderManifestToken`devreder.  
  
```csharp
public string GetProviderManifestToken(DbConnection connection);  
public DbProviderManifest GetProviderManifest(string manifestToken);  
```  
  
#### <a name="using-a-provider-manifest-token"></a>Sağlayıcı bildirim belirteci kullanma  
 Çevrimdışı senaryo için, belirteç SSDL gösteriminden çekilir. SSDL, bir ProviderManifestToken belirtmenize olanak tanır (daha fazla bilgi için bkz. [şema öğesi (ssdl)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#schema-element-ssdl) ). Örneğin, bir bağlantı açılamadığı için SSDL, bildirimle ilgili bilgileri belirten bir sağlayıcı bildirim belirtecine sahiptir.  
  
```  
public DbProviderManifest GetProviderManifest(string manifestToken);  
```  
  
### <a name="provider-manifest-schema"></a>Sağlayıcı bildirim şeması  
 Her sağlayıcı için tanımlanan bilgilerin şeması, meta veriler tarafından tüketilen statik bilgileri içerir:  
  
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
  
#### <a name="types-node"></a>Türler düğümü  
 Sağlayıcı bildirimindeki türler düğümü, veri deposu tarafından veya sağlayıcı aracılığıyla yerel olarak desteklenen türler hakkında bilgi içerir.  
  
##### <a name="type-node"></a>Tür düğümü  
 Her tür düğüm, EDM açısından bir sağlayıcı türü tanımlar. Tür düğümü, sağlayıcı türünün adını ve eşlendiği model türüyle ilgili bilgileri ve bu tür eşlemeyi açıklar.  
  
 Bu tür bilgilerini sağlayıcı bildiriminde ifade etmek için her TypeInformation bildiriminin her bir tür için birkaç model açıklaması tanımlaması gerekir:  
  
|Öznitelik adı|Veri Türü|Gerekli|Varsayılan Değer|Açıklama|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|Ad|Dize|Evet|yok|Sağlayıcıya özgü veri türü adı|  
|PrimitiveTypeKind|PrimitiveTypeKind|Evet|yok|EDM türü adı|  
  
###### <a name="function-node"></a>İşlev düğümü  
 Her Işlev, sağlayıcı aracılığıyla kullanılabilen tek bir işlevi tanımlar.  
  
|Öznitelik adı|Veri Türü|Gerekli|Varsayılan Değer|Açıklama|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|Ad|Dize|Evet|yok|İşlevin tanımlayıcısı/adı|  
|'Indaki|Dize|Hayır|Kağıt|İşlevin EDM dönüş türü|  
|Toplama|Boole değeri|Hayır|False|İşlev bir toplama işlevse doğru|  
|Yerleik|Boole değeri|Hayır|Doğru|İşlev veri deposunda yerleşik ise doğru|  
|StoreFunctionName|Dize|Hayır|\<Ad >|Veri deposundaki işlev adı.  İşlev adlarının yeniden yönlendirme düzeyine izin verir.|  
|NiladicFunction|Boole değeri|Hayır|False|İşlev parametre gerektirmiyorsa ve parametre olmadan çağrılırsa doğru|  
|ParameterType<br /><br /> İçeriyor|Parametersemantik|Hayır|Allowwimplicit<br /><br /> Dönüştürme|Sorgu işlem hattının parametre türü değiştirme ile nasıl ele alınacağını seçme:<br /><br /> - ExactMatchOnly<br />-Allowimplicitpromosyonu<br />-AllowImplicitConversion|  
  
 **Parameters düğümü**  
  
 Her işlevde bir veya daha fazla parametre düğümü koleksiyonu vardır.  
  
|Öznitelik adı|Veri Türü|Gerekli|Varsayılan Değer|Açıklama|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|Ad|Dize|Evet|yok|Parametrenin tanımlayıcı/adı.|  
|Tür|Dize|Evet|yok|Parametrenin EDM türü.|  
|Mod|Parametre<br /><br /> Yön|Evet|yok|Parametrenin yönü:<br /><br /> -ın<br />-Out<br />-InOut|  
  
##### <a name="namespace-attribute"></a>Namespace özniteliği  
 Her veri deposu sağlayıcısı, bildirimde tanımlanan bilgiler için bir ad alanı veya ad alanı grubu tanımlamalıdır. Bu ad alanı, işlev ve tür adlarını çözümlemek için Entity SQL sorgularında kullanılabilir. Örneğin: SqlServer. Bu ad alanı, Entity SQL sorguları tarafından desteklenecek standart işlevler için varlık Hizmetleri tarafından tanımlanan EDM ad alanından farklı olmalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity Framework Veri Sağlayıcısı Yazma](writing-an-ef-data-provider.md)
