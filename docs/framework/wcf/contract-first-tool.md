---
title: Önce Anlaşma Aracı
ms.date: 03/30/2017
ms.assetid: 0a880690-f460-4475-a5f4-9f91ce08fcc6
ms.openlocfilehash: f061f4dd37861c1cf3dd0cc8318de9f0f65b90e4
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
---
# <a name="contract-first-tool"></a>Önce Anlaşma Aracı
Hizmet sözleşmeleri genellikle varolan Hizmetleri'nden oluşturulması gerekir. İçinde [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], veri sözleşmesi sınıfları oluşturulabilir otomatik olarak önce anlaşma aracı kullanarak mevcut Hizmetleri'nden. Önce anlaşma aracı kullanmak için XML şeması tanım dosyası (XSD) yerel olarak yüklenmelidir; Aracı, HTTP üzerinden uzak veri sözleşmeleri içeri aktarılamıyor.  
  
 Önce anlaşma aracı tümleştirilmiş [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] derleme görevi olarak. Böylece proje kolayca temel alınan hizmet sözleşmesini değişiklikleri benimseyebilirsiniz derleme görevi tarafından oluşturulan kod dosyaları proje yerleşik olarak bulunan her zaman oluşturulur.  
  
 Önce anlaşma aracı alabilir şema türleri şunlardır:  
  
```xml  
<xsd:complexType>  
<xsd:simpleType>  
```  
  
 Basit türler, değil temelleri gibi olmaları durumunda oluşturulmayacak `Int16` veya `String`; karmaşık türleri, değil türünde iseler oluşturulmayacak `Collection`. Türleri de olmayan oluşturulmayacak başka bir parçası ise `xsd:complexType`. Bu durumlarda, türleri projedeki mevcut türleri için bunun yerine başvurulacak.  
  
## <a name="adding-a-data-contract-to-a-project"></a>Projeye bir veri sözleşmesi ekleme  
 Önce anlaşma Aracı'nı kullanmadan önce hizmet sözleşmesi (XSD) projeye eklenmelidir. Bu genel bakışta amaçları doğrultusunda, aşağıdaki Sözleşme Sözleşme ilk işlevleri göstermek için kullanılır. Bu hizmet tanımı Bing'ın arama API tarafından kullanılan hizmet sözleşmesini küçük bir alt kümesidir.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema id="ServiceSchema"  
    targetNamespace="http://tempuri.org/ServiceSchema.xsd"  
    elementFormDefault="qualified"  
    xmlns="http://tempuri.org/ServiceSchema.xsd"  
    xmlns:mstns="http://tempuri.org/ServiceSchema.xsd"  
    xmlns:xs="http://www.w3.org/2001/XMLSchema"  
>  
  <xs:complexType name="SearchRequest">  
    <xs:sequence>  
      <xs:element minOccurs="0" maxOccurs="1" name="Version" type="xs:string" default="2.2" />  
      <xs:element minOccurs="0" maxOccurs="1" name="Market" type="xs:string" />  
      <xs:element minOccurs="0" maxOccurs="1" name="UILanguage" type="xs:string" />  
      <xs:element minOccurs="1" maxOccurs="1" name="Query" type="xs:string" />  
      <xs:element minOccurs="1" maxOccurs="1" name="AppId" type="xs:string" />  
      <xs:element minOccurs="0" maxOccurs="1" name="Latitude" type="xs:double" />  
      <xs:element minOccurs="0" maxOccurs="1" name="Longitude" type="xs:double" />  
      <xs:element minOccurs="0" maxOccurs="1" name="Radius" type="xs:double" />  
    </xs:sequence>  
  </xs:complexType>  
  <xs:simpleType name="WebSearchOption">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="DisableHostCollapsing" />  
      <xs:enumeration value="DisableQueryAlterations" />  
    </xs:restriction>  
  </xs:simpleType>  
</xs:schema>  
```  
  
 Yukarıdaki hizmet sözleşmesini projeye eklemek için projesine sağ tıklatın ve **yeni Ekle...** . Şema tanımı Şablonları iletişim WCF bölmesinden seçin ve SampleContract.xsd yeni dosya adı. Yukarıdaki kodu kopyalayıp yeni dosya kodu görünüme yapıştırın.  
  
## <a name="configuring-contract-first-options"></a>Önce anlaşma seçeneklerini yapılandırma  
 Önce anlaşma seçenekleri WCF proje özelliklerini menüsünde yapılandırılabilir. Önce anlaşma geliştirme etkinleştirmek için seçin **etkinleştirmek XSD türü tanım dili olarak** onay kutusunu proje penceresinin WCF sayfasındaki.  
  
 ![WCF proje seçenekleri gösteren sözleşme&#45;ilk](../../../docs/framework/wcf/media/contractfirstoptions.png "ContractFirstOptions")  
  
 Gelişmiş özelliklerini yapılandırmak için Gelişmiş düğmesini tıklatın.  
  
 ![Sözleşme Gelişmiş&#45;ilk özellikleri](../../../docs/framework/wcf/media/contractfirstadvanced.png "ContractFirstAdvanced")  
  
 Gelişmiş ayarlar aşağıdaki sözleşmeleri kod oluşturma için yapılandırılabilir. Ayarları, yalnızca tüm projedeki dosyaları için yapılandırılabilir; ayarları için tek tek dosyalar şu anda yapılandırılamaz.  
  
-   **Seri hale getirici modu**: Bu ayarı, hangi seri hale getirici hizmet sözleşmesi dosyaları okumak için kullanılan belirler. Zaman **XML serileştiriciyi** seçili **koleksiyon türleri** ve **yeniden türleri** seçenekleri devre dışı bırakılır. Bu seçenekler yalnızca geçerli **veri sözleşmesi seri hale getirici**.  
  
-   **Türleri yeniden**: Bu ayar, hangi kitaplıkların türü yeniden kullanılmak üzere kullanılan belirtir. Bu ayar yalnızca geçerlidir **seri hale getirici modu** ayarlanır **veri sözleşmesi seri hale getirici**.  
  
-   **Koleksiyon türü**: Bu ayar, koleksiyon veri türü için kullanılacak tam veya bütünleştirilmiş kod tam türünü belirtir. Bu ayar yalnızca geçerlidir **seri hale getirici modu** ayarlanır **veri sözleşmesi seri hale getirici**.  
  
-   **Sözlük türü**: Bu ayar, sözlük veri türü için kullanılacak tam veya bütünleştirilmiş kod tam türünü belirtir.  
  
-   **EnableDataBinding**: uygulamak bu ayarı belirtir <xref:System.ComponentModel.INotifyPropertyChanged> veri bağlama uygulamak için tüm veri türleri arabirimi.  
  
-   **ExcludedTypes**: Bu ayar, başvurulan derlemelerden çıkarılacak tam veya bütünleştirilmiş kod tam türlerinin bir listesini belirtir. Bu ayar yalnızca geçerlidir **seri hale getirici modu** ayarlanır **veri sözleşmesi seri hale getirici**.  
  
-   **GenerateInternalTypes**: Bu ayarı olarak iç işaretlenmiş sınıfları oluşturulup oluşturulmayacağını belirtir. Bu ayar yalnızca geçerlidir **seri hale getirici modu** ayarlanır **veri sözleşmesi seri hale getirici**.  
  
-   **GenerateSerializableTypes**: Bu ayar sınıflarıyla oluşturulup oluşturulmayacağını belirtir <xref:System.SerializableAttribute> özniteliği. Bu ayar yalnızca geçerlidir **seri hale getirici modu** ayarlanır **veri sözleşmesi seri hale getirici**.  
  
-   **ImportXMLTypes**: Bu ayarı uygulamak için veri sözleşmesi seri hale getirici yapılandırılıp yapılandırılmayacağını belirtir <xref:System.SerializableAttribute> olmadan sınıflarını özniteliğini <xref:System.Runtime.Serialization.DataContractAttribute> özniteliği.  Bu ayar yalnızca geçerlidir **seri hale getirici modu** ayarlanır **veri sözleşmesi seri hale getirici**.  
  
-   **SupportFx35TypedDataSets**: Bu ayar için .net oluşturulan yazılan veri kümeleri için ek işlevler sağlamasına belirtir Framework 3.5. Zaman **seri hale getirici modu** ayarlanır **XML serileştiriciyi**, <xref:System.Data.Design.TypedDataSetSchemaImporterExtensionFx35> uzantı bu değeri True olarak ayarlandığında için XML Şeması içeri Aktarıcı eklenir. Zaman **seri hale getirici modu** ayarlanır **veri sözleşmesi seri hale getirici**, türü <xref:System.DateTimeOffset> bu değeri False olarak ayarlandığında başvurularından dışlanıp böylece bir <xref:System.DateTimeOffset> her zaman oluşturulur eski framework sürümleri için.  
  
-   **InputXsdFiles**: Bu ayar giriş dosyaların listesini belirtir. Her bir dosyanın geçerli bir XML Şeması içermesi gerekir.  
  
-   **Dil**: Bu ayar, oluşturulan sözleşme kod dilini belirtir. Bu ayar tarafından tanınan olmalıdır <xref:System.CodeDom.Compiler.CodeDomProvider>.  
  
-   **NamespaceMappings**: XSD hedef ad eşlemelerini CLR ad alanları için bu ayarı belirtir. Her eşleme aşağıdaki biçimi kullanmalıdır:  
  
    ```xml  
    "<Schema Namespace>, <CLR Namespace>"  
    ```  
  
     XML serileştiriciyi yalnızca şu biçimdeki bir eşleme kabul eder:  
  
    ```xml  
    "*, <CLR Namespace>"  
    ```  
  
-   **Çıktıdizini**: Bu ayar, kod dosyaları oluşturulmayacak dizini belirtir.  
  
 Ayarları, proje yapılandırıldığında hizmet sözleşmesi dosyalarından hizmet sözleşme türleri oluşturmak için kullanılır.  
  
## <a name="using-contract-first-development"></a>Önce anlaşma geliştirme kullanma  
 Hizmet sözleşmesi projeye ekleme ve yapılandırma ayarlarını onaylama yapı sonra projeyi tuşlarına basarak **F6**. Hizmet sözleşmesinde tanımlanan türler sonra projede kullanılmak üzere kullanılabilir.  
  
 Hizmet sözleşmesinde tanımlanan türlerden birisini kullanmak için bir başvuru ekleyin `ContractTypes` geçerli ad alanı altında:  
  
```csharp  
using MyProjectNamespace.ContractTypes;  
```  
  
 Hizmet sözleşmesinde tanımlanan türler sonra aşağıda gösterildiği gibi projede çözümlenebilir olacaktır.  
  
 ![Bir hizmet sözleşmesi türetilmiş türler kullanarak](../../../docs/framework/wcf/media/contractfirsttypes.png "ContractFirstTypes")  
  
 Aracı tarafından oluşturulan türleri GeneratedXSDTypes.cs dosyasında oluşturulur. Dosya oluşturulur \<proje dizini > /obj/\<yapı yapılandırması > Varsayılan olarak /XSDGeneratedCode/ dizin. Bu konunun başındaki örnek şema gibi dönüştürülür:  
  
```csharp
//------------------------------------------------------------------------------  
// <auto-generated>  
//     This code was generated by a tool.  
//     Runtime Version:4.0.30319.17330  
//  
//     Changes to this file may cause incorrect behavior and will be lost if  
//     the code is regenerated.  
// </auto-generated>  
//------------------------------------------------------------------------------  
  
namespace TestXSD3.ContractTypes  
{  
    using System.Xml.Serialization;  
  
    /// <remarks/>  
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.Xml", "4.0.30319.17330")]  
    [System.SerializableAttribute()]  
    [System.Diagnostics.DebuggerStepThroughAttribute()]  
    [System.ComponentModel.DesignerCategoryAttribute("code")]  
    [System.Xml.Serialization.XmlTypeAttribute(Namespace="http://tempuri.org/ServiceSchema.xsd")]  
    [System.Xml.Serialization.XmlRootAttribute(Namespace="http://tempuri.org/ServiceSchema.xsd", IsNullable=true)]  
    public partial class SearchRequest  
    {  
  
        private string versionField;  
  
        private string marketField;  
  
        private string uILanguageField;  
  
        private string queryField;  
  
        private string appIdField;  
  
        private double latitudeField;  
  
        private bool latitudeFieldSpecified;  
  
        private double longitudeField;  
  
        private bool longitudeFieldSpecified;  
  
        private double radiusField;  
  
        private bool radiusFieldSpecified;  
  
        public SearchRequest()  
        {  
            this.versionField = "2.2";  
        }  
  
        /// <remarks/>  
        [System.ComponentModel.DefaultValueAttribute("2.2")]  
        public string Version  
        {  
            get  
            {  
                return this.versionField;  
            }  
            set  
            {  
                this.versionField = value;  
            }  
        }  
  
        /// <remarks/>  
        public string Market  
        {  
            get  
            {  
                return this.marketField;  
            }  
            set  
            {  
                this.marketField = value;  
            }  
        }  
  
        /// <remarks/>  
        public string UILanguage  
        {  
            get  
            {  
                return this.uILanguageField;  
            }  
            set  
            {  
                this.uILanguageField = value;  
            }  
        }  
  
        /// <remarks/>  
        public string Query  
        {  
            get  
            {  
                return this.queryField;  
            }  
            set  
            {  
                this.queryField = value;  
            }  
        }  
  
        /// <remarks/>  
        public string AppId  
        {  
            get  
            {  
                return this.appIdField;  
            }  
            set  
            {  
                this.appIdField = value;  
            }  
        }  
  
        /// <remarks/>  
        public double Latitude  
        {  
            get  
            {  
                return this.latitudeField;  
            }  
            set  
            {  
                this.latitudeField = value;  
            }  
        }  
  
        /// <remarks/>  
        [System.Xml.Serialization.XmlIgnoreAttribute()]  
        public bool LatitudeSpecified  
        {  
            get  
            {  
                return this.latitudeFieldSpecified;  
            }  
            set  
            {  
                this.latitudeFieldSpecified = value;  
            }  
        }  
  
        /// <remarks/>  
        public double Longitude  
        {  
            get  
            {  
                return this.longitudeField;  
            }  
            set  
            {  
                this.longitudeField = value;  
            }  
        }  
  
        /// <remarks/>  
        [System.Xml.Serialization.XmlIgnoreAttribute()]  
        public bool LongitudeSpecified  
        {  
            get  
            {  
                return this.longitudeFieldSpecified;  
            }  
            set  
            {  
                this.longitudeFieldSpecified = value;  
            }  
        }  
  
        /// <remarks/>  
        public double Radius  
        {  
            get  
            {  
                return this.radiusField;  
            }  
            set  
            {  
                this.radiusField = value;  
            }  
        }  
  
        /// <remarks/>  
        [System.Xml.Serialization.XmlIgnoreAttribute()]  
        public bool RadiusSpecified  
        {  
            get  
            {  
                return this.radiusFieldSpecified;  
            }  
            set  
            {  
                this.radiusFieldSpecified = value;  
            }  
        }  
    }  
  
    /// <remarks/>  
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.Xml", "4.0.30319.17330")]  
    [System.SerializableAttribute()]  
    [System.Xml.Serialization.XmlTypeAttribute(Namespace="http://tempuri.org/ServiceSchema.xsd")]  
    [System.Xml.Serialization.XmlRootAttribute(Namespace="http://tempuri.org/ServiceSchema.xsd", IsNullable=false)]  
    public enum WebSearchOption  
    {  
  
        /// <remarks/>  
        DisableHostCollapsing,  
  
        /// <remarks/>  
        DisableQueryAlterations,  
    }  
}  
```  
  
## <a name="errors-and-warnings"></a>Hatalar ve uyarılar  
 Hataları ve Uyarıları XSD şema ayrıştırma karşılaşılan hataları ve Uyarıları oluşturmak gibi görünür.  
  
## <a name="interface-inheritance"></a>Arabirim devralma  
 Önce anlaşma geliştirme ile arabirimi devralma kullanmak mümkün değildir; Bu, diğer işlemlerini arabirimleri davranmasına yol tutarlıdır. Temel arabirim devralan bir arabirim kullanmak için iki ayrı uç nokta kullanın. Birinci uç nokta devralınan sözleşme kullanan ve ikinci uç nokta temel arabirimi uygular.
