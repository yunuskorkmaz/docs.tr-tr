---
title: Sağlayıcı bildirimi belirtimi
ms.date: 03/30/2017
ms.assetid: bb450b47-8951-4f99-9350-26f05a4d4e46
ms.openlocfilehash: 409653fa415e62ff0591e09ad4771c5951689b24
ms.sourcegitcommit: c6f69b0cf149f6b54483a6d5c2ece222913f43ce
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55904608"
---
# <a name="provider-manifest-specification"></a>Sağlayıcı bildirimi belirtimi
Bu bölümde, nasıl bir veri deposu sağlayıcısı türleri ve işlevleri veri deposunda destekleyebileceğini açıklanmaktadır.  
  
 Varlık Hizmetleri belirli veri depolama sağlayıcısının bağımsız olarak çalışır ancak hala modelleri, eşlemeler ve sorguları bir temel alınan veri deposuyla nasıl etkileşim açıkça tanımlamak bir veri sağlayıcı sağlar. Bir Soyutlama Katmanı varlık Hizmetleri yalnızca belirli bir veri deposu ya da veri sağlayıcısı hedeflenecek.  
  
 Sağlayıcının desteklediği türleri, doğrudan veya dolaylı olarak temel alınan veritabanı tarafından desteklenir. Bu tür mutlaka tam deposu türlerini ancak sağlayıcısı kullanan desteklemek için türleri olmayan [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Varlık veri modeli (EDM) koşullarını sağlayıcısı depolama türleri açıklanmaktadır.  
  
 Veri deposu tarafından desteklenen işlevler için parametre ve dönüş türleri'EDM koşullarını belirtilir.  
  
## <a name="requirements"></a>Gereksinimler  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Ve bilinen türler kesilmesi veya veri kaybı olmadan sürekli içinde veri geçirebilmek için gereken veri deposu.  
  
 Sağlayıcı bildirimi tasarım zamanında veri deposuna bağlantı açmak zorunda kalmadan araçlar tarafından yüklenebilir olması gerekir.  
  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Çalışması büyük/küçük harfe duyarlıdır, ancak temel alınan veri deposu çalışmıyor olabilir. Zaman EDM yapıtları (tanımlayıcıları ve örneğin tür adları) tanımlandığını ve kullanıldığını bildiriminde kullandıkları gerekir [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] büyük küçük harf duyarlılığı. Büyük küçük harfe duyarlı veri deposu öğeleri sağlayıcı bildiriminde görünüyorsa, bu büyük/küçük harf sağlayıcı bildiriminde tutulması gerekir.  
  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Tüm veri sağlayıcıları için bir sağlayıcı bildirimi gerektirir. Bir sağlayıcı yok. bir sağlayıcı kullanmayı denerseniz ile bildirim [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], bir hata alırsınız.  
  
 Aşağıdaki tabloda tür özel durumlar açıklanmaktadır [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] sağlayıcı etkileşimi özel durumlar ortaya çıktığında throw:  
  
|Sorun|Özel Durum|  
|-----------|---------------|  
|Sağlayıcı GetProviderManifest DbProviderServices içinde desteklemez.|ProviderIncompatibleException|  
|Sağlayıcı bildirimi eksik: sağlayıcının döndürdüğü `null` sağlayıcı bildirimi alınmaya çalışılırken.|ProviderIncompatibleException|  
|Geçersiz sağlayıcı bildirimi: sağlayıcı geçersiz XML sağlayıcı bildirimi alınmaya çalışılırken döndürür.|ProviderIncompatibleException|  
  
## <a name="scenarios"></a>Senaryolar  
 Bir sağlayıcı, aşağıdaki senaryolarda desteklemesi gerekir:  
  
### <a name="writing-a-provider-with-symmetric-type-mapping"></a>Simetrik tür eşlemesine sahip bir sağlayıcı yazma  
 Sağlayıcı için yazabileceğiniz [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] eşleme yönü bağımsız olarak tek bir EDM türü her depo türü burada eşleştirir. Karşılık gelen çok basit eşlemesi bir EDM türü için bir sağlayıcı türü, tür sisteminde basit olduğu için veya EDM türleri eşleşen simetrik bir çözüm kullanabilirsiniz.  
  
 Kendi etki alanı basitliği ve bir statik bildirim temelli sağlayıcı bildirimi üreten kullanabilirsiniz.  
  
 İki bölüme sahip bir XML dosyası yazma:  
  
-   "EDM karşılığı" deposu tür veya işlev açısından ifade sağlayıcısı türlerinin listesi. Store türlerin karşılığı EDM türleri vardır. Store işlevlerin karşılık gelen EDM işlevleri vardır. Örneğin, bir SQL Server türü varchar, ancak karşılık gelen EDM türü dize.  
  
-   Burada parametre ve dönüş türleri'EDM koşullarını ifade edilir sağlayıcısı tarafından desteklenen işlevlerin listesi.  
  
### <a name="writing-a-provider-with-asymmetric-type-mapping"></a>Asimetrik tür eşlemesine sahip bir sağlayıcı yazma  
 Ne zaman, bir veri deposu sağlayıcısı için yazma [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], bazı türleri sağlayıcısı EDM türü eşlemesinden farklı için eşleme sağlayıcısı için EDM türü. Örneğin, nvarchar(4000) için EDM PrimitiveTypeKind.String(MaxLength=4000) eşleştirir. sırasında nvarchar(4000) sağlayıcısı için sınırsız EDM PrimitiveTypeKind.String eşlenebilir.  
  
 İki bölüme sahip bir XML dosyası yazma:  
  
-   Sağlayıcı türlerinin bir listesini EDM terimleriyle ifade edilen ve her iki yön için eşleme tanımlayın: EDM sağlayıcısı ve sağlayıcı EDM.  
  
-   Burada parametre ve dönüş türleri'EDM koşullarını ifade edilir sağlayıcısı tarafından desteklenen işlevlerin listesi.  
  
## <a name="provider-manifest-discoverability"></a>Sağlayıcı bildirimi bulunabilirlik  
 Bildirim dolaylı olarak varlık Hizmetleri (örneğin, araçları veya sorgu) birçok bileşen türleri tarafından kullanılır ancak daha fazla veri kullanımı meta verileri tarafından doğrudan kullanılabilir meta veri yükleyici depolayın.  
  
 ![dfb3d02b&#45;7a8c&#45;4d 51&#45;ac5a&#45;a73d8aa145e6](../../../../../docs/framework/data/adonet/ef/media/dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6.gif "dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6")  
  
 Ancak, belirli bir sağlayıcı farklı mağazalarda veya aynı deponun'ün farklı sürümlerini desteklemiyor olabilir. Bu nedenle, bir sağlayıcı her desteklenen veri deposu için farklı bir bildirim bildirilmesi gerekir.  
  
### <a name="provider-manifest-token"></a>Sağlayıcı bildirimi belirteci  
 Bir veri deposu bağlantısı açıldığında, sağlayıcı doğru bildirimi döndürmek bilgi için sorgulayabilirsiniz. Bu bağlantı bilgileri kullanılabildiği değil veya ne zaman mağazaya bağlanmanıza mümkün değildir çevrimdışı senaryolarda mümkün olmayabilir. Bildirim kullanarak tanımlamak `ProviderManifestToken` özniteliği `Schema` .ssdl dosyasındaki öğesi. Bu öznitelik için gerekli bir biçim vardır; Sağlayıcı bir bildirim mağazaya bir bağlantı açmaya gerek kalmadan tanımlamak için gereken en düşük bilgi seçer.  
  
 Örneğin:  
  
```xml  
<Schema Namespace="Northwind" Provider="System.Data.SqlClient" ProviderManifestToken="2005" xmlns:edm="http://schemas.microsoft.com/ado/2006/04/edm/ssdl" xmlns="http://schemas.microsoft.com/ado/2006/04/edm/ssdl">  
```  
  
## <a name="provider-manifest-programming-model"></a>Sağlayıcı bildirimi programlama modeli  
 Sağlayıcıları türetilen <xref:System.Data.Common.DbXmlEnabledProviderManifest>, bunları kendi bildirimleri bildirimli olarak belirtmek sağlar. Aşağıdaki çizimde bir sağlayıcı sınıf hiyerarşisini gösterir:  
  
 ![Hiçbiri](../../../../../docs/framework/data/adonet/ef/media/d541eba3-2ee6-4cd1-88f5-89d0b2582a6c.gif "d541eba3-2ee6-4cd1-88f5-89d0b2582a6c")  
  
### <a name="discoverability-api"></a>API keşfedilebilirliğini  
 Sağlayıcı bildirimi (storeıtemcollection'ın) meta verileri Store yükleyicisi tarafından yüklenen, veri kullanılarak bağlantı veya sağlayıcı bildirimi belirteci depolama.  
  
#### <a name="using-a-data-store-connection"></a>Data Store bağlantı kullanma  
 Verileri depolamak bağlantısı kullanılabilir, DbProvderServices.GetProviderManifestToken DbProviderManifest döndüren GetProviderManifest yöntemine geçirilen bir belirteç döndürecek şekilde çağırın. Bu yöntem, sağlayıcının uygulanmasına GetDbProviderManifestToken atar.  
  
```  
public string GetProviderManifestToken(DbConnection connection);  
public DbProviderManifest GetProviderManifest(string manifestToken);  
```  
  
#### <a name="using-a-provider-manifest-token"></a>Sağlayıcı bildirimi belirteciyle  
 Çevrimdışı senaryosu, belirteç SSDL temsilinden çekilir. SSDL bir ProviderManifestToken belirtmenizi sağlar (bkz [şema öğesi (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#schema-element-ssdl) daha fazla bilgi için). Örneğin, bir bağlantı açılamıyor, SSDL bildirimi hakkında bilgi belirten sağlayıcısı bildirimi belirtece sahip.  
  
```  
public DbProviderManifest GetProviderManifest(string manifestToken);  
```  
  
### <a name="provider-manifest-schema"></a>Sağlayıcı bildirim şeması  
 Her hizmet sağlayıcısı için tanımlanan bilgileri şemasını meta veriler tarafından tüketilen statik bilgilerini içerir:  
  
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
  
#### <a name="types-node"></a>Düğüm türleri  
 Sağlayıcı bildirimi türleri düğümünde veri deposu tarafından veya sağlayıcısı aracılığıyla yerel olarak desteklenen türleri hakkında bilgi içerir.  
  
##### <a name="type-node"></a>Düğüm türü  
 Her tür düğümünün EDM açısından sağlayıcı türünü tanımlar. Türü düğüm adı sağlayıcı türü ve bu tür eşlemesi açıklamak için eşlendiği model türünü ve modelleri için ilgili bilgiler açıklanmaktadır.  
  
 Bu tür bilgisi sağlayıcı bildirimi express için her TypeInformation bildirimi her türü için birden fazla model açıklamaları tanımlamanız gerekir:  
  
|Öznitelik adı|Veri Türü|Gerekli|Varsayılan Değer|Açıklama|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|Ad|Dize|Evet|yok|Sağlayıcıya özel veri türü adı|  
|PrimitiveTypeKind|PrimitiveTypeKind|Evet|yok|EDM türü adı|  
  
###### <a name="function-node"></a>Düğüm işlevi  
 Her işlev sağlayıcısı tek bir işlevi tanımlar.  
  
|Öznitelik adı|Veri Türü|Gerekli|Varsayılan Değer|Açıklama|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|Ad|Dize|Evet|yok|Tanımlayıcı/işlevin adı|  
|ReturnType|Dize|Hayır|Geçersiz kılma|EDM işlevin dönüş türü|  
|Toplama|Boole değeri|Hayır|False|İşlev bir toplama işlevi ise true|  
|BuiltIn|Boole değeri|Hayır|Doğru|İşlevi veri deposuna oluşturulursa true|  
|StoreFunctionName|Dize|Hayır|\<Adı >|Veri deposundaki işlev adı.  İşlev adları yeniden yönlendirilmesi için bir düzeyi sağlar.|  
|NiladicFunction|Boole değeri|Hayır|False|İşlev parametreleri gerektirmez ve hiçbir parametre olmadan çağrılırsa true|  
|ParameterType<br /><br /> Semantiği|ParameterSemantics|Hayır|AllowImplicit<br /><br /> Dönüştürme|Sorgu işlem hattı parametre türü değiştirme ile nasıl ele alması gerektiğini Seçimi:<br /><br /> -ExactMatchOnly<br />-Allowımplicitpromotion<br />-Allowımplicitconversion|  
  
 **Parametreleri düğümü**  
  
 Her işlev bir veya daha fazla parametre düğümleri koleksiyonu vardır.  
  
|Öznitelik adı|Veri Türü|Gerekli|Varsayılan Değer|Açıklama|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|Ad|Dize|Evet|yok|Tanımlayıcı/parametrenin adı.|  
|Tür|Dize|Evet|yok|Parametrenin EDM türü.|  
|Mod|Parametre<br /><br /> Yön|Evet|yok|Parametre yönü:<br /><br /> -içinde<br />-out<br />-ınout|  
  
##### <a name="namespace-attribute"></a>Namespace özniteliği  
 Her bir veri deposu sağlayıcısı ad alanı veya ad alanı bildiriminde tanımlanan bilgi grubu tanımlamanız gerekir. Bu ad alanı Entity SQL sorguları, işlevi ve türü adlarını çözümlemek için kullanılabilir. Örneğin: SqlServer. Bu ad alanı Entity SQL sorguları tarafından desteklenen standart işlev için varlık Hizmetleri tarafından tanımlanan kurallı ad alanı, EDM, farklı olmalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Entity Framework Veri Sağlayıcısı Yazma](../../../../../docs/framework/data/adonet/ef/writing-an-ef-data-provider.md)
