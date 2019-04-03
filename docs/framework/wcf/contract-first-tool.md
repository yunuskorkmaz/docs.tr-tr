---
title: Önce Anlaşma Aracı
ms.date: 03/30/2017
ms.assetid: 0a880690-f460-4475-a5f4-9f91ce08fcc6
ms.openlocfilehash: ad0566eaff08d27e8368f091388adda7376a37ef
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819625"
---
# <a name="contract-first-tool"></a>Önce Anlaşma Aracı
Hizmet sözleşmeleri, genellikle var olan hizmetlerden oluşturulan gerekir. İçinde [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], veri sözleşme sınıfları oluşturulabilir otomatik olarak önce anlaşma aracı kullanarak mevcut hizmetlerden. Önce anlaşma aracı kullanmak için XML şema tanımı dosyası (XSD) yerel olarak indirilmelidir; aracın HTTP üzerinden uzak veri sözleşmeleri içeri aktarılamıyor.

 Önce anlaşma aracı, derleme görevi olarak Visual Studio 2012 ile tümleşiktir. Proje, kolayca değişiklikleri temel alınan hizmet sözleşmesindeki benimseyebilirsiniz derleme görevi tarafından oluşturulan kod dosyaları Proje oluşturulur, her zaman oluşturulur.

 Önce anlaşma aracı aktarabileceğiniz şema türleri aşağıdakileri kapsamaktadır:

```xml
<xsd:complexType>
<xsd:simpleType>
```

 Temel öğeler gibi olmaları durumunda basit türler oluşturulmayacak `Int16` veya `String`; karmaşık türde ise türleri oluşturulmayacak `Collection`. Türleri de oluşturulmayacak başka bir parçası olmaları durumunda `xsd:complexType`. Bu durumlarda, türleri projedeki varolan türleri için bunun yerine başvurulur.

## <a name="adding-a-data-contract-to-a-project"></a>Bir veri anlaşması bir projeye ekleniyor
 Önce anlaşma aracı kullanılmadan önce hizmet sözleşmesi (XSD) projeye eklenmelidir. Bu genel amaçları için aşağıdaki Sözleşme Sözleşme öncelikli işlevleri göstermek için kullanılır. Bu hizmet tanımı Bing'in arama API'si tarafından kullanılan hizmet sözleşmesinin küçük bir alt kümesidir.

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

 Yukarıdaki hizmet sözleşmesi projeye eklemek için projeyi sağ tıklayıp **yeni Ekle...** . Şema tanımı Şablonları iletişim WCF bölmesinden seçin ve SampleContract.xsd yeni dosya adı. Kopyalayın ve yukarıdaki kod yeni dosyanın kod görünümüne yapıştırabilirsiniz.

## <a name="configuring-contract-first-options"></a>Önce anlaşma seçeneklerini yapılandırma
 Sözleşme öncelikli seçenekler WCF proje özellikleri menüsünde yapılandırılabilir. Sözleşme ilk geliştirmesi etkinleştirmek için seçin **etkinleştirme XSD türü tanım dili olarak** onay kutusuna WCF sayfası, Proje Özellikleri penceresi.

 ![Sözleşme ilk geliştirmesi etkin ile WCF seçeneklerinin ekran görüntüsü.](./media/contract-first-tool/contract-first-options.png)

 Gelişmiş özelliklerini yapılandırmak için Gelişmiş düğmesine tıklayın.

 ![Gelişmiş sözleşme kodu oluşturma ayarları iletişim kutusu.](./media/contract-first-tool/advanced-contract-settings.png)

 Gelişmiş ayarlar aşağıdaki anlaşmalarından alınan kod oluşturma için yapılandırılabilir. Ayarlar, yalnızca tüm proje dosyaları için yapılandırılabilir; ayarları tek tek dosyalar için şu anda yapılandırılamaz.

-   **Serializer mod**: Bu ayar, hangi seri hale getirici hizmet sözleşme dosyaları okumak için kullanılan belirler. Zaman **XML serileştiricisi** seçildiğinde **koleksiyon türleri** ve **yeniden türleri** seçenekleri devre dışı bırakıldı. Bu seçenekler yalnızca uygulamak **veri sözleşmesi serileştiricisi**.

-   **Türleri yeniden kullan**: Bu ayar, türün yeniden kullanımı için hangi kitaplıkların kullanıldığı belirtir. Bu ayar yalnızca geçerlidir **Serializer mod** ayarlanır **veri sözleşmesi serileştiricisi**.

-   **Koleksiyon türü**: Bu ayar, koleksiyon veri türü için kullanılacak tam veya bütünleştirilmiş kodla nitelenen tür belirtir. Bu ayar yalnızca geçerlidir **Serializer mod** ayarlanır **veri sözleşmesi serileştiricisi**.

-   **Sözlük türü**: Bu ayar, sözlük veri türü için kullanılacak tam veya bütünleştirilmiş kodla nitelenen tür belirtir.

-   **EnableDataBinding**: Bu ayar uygulanmayacağını belirtir <xref:System.ComponentModel.INotifyPropertyChanged> veri bağlama uygulamak için tüm veri türlerinde arabirimi.

-   **Excludedtypes'a**: Bu ayar, başvurulan derlemelerden dışlanacak tam veya bütünleştirilmiş kodla nitelenen türlerin listesini belirtir. Bu ayar yalnızca geçerlidir **Serializer mod** ayarlanır **veri sözleşmesi serileştiricisi**.

-   **GenerateInternalTypes**: Bu ayar iç olarak işaretlenmiş sınıfların oluşturulup oluşturulmayacağını belirtir. Bu ayar yalnızca geçerlidir **Serializer mod** ayarlanır **veri sözleşmesi serileştiricisi**.

-   **GenerateSerializableTypes**: Bu ayar ile sınıfların oluşturulup oluşturulmayacağını belirtir <xref:System.SerializableAttribute> özniteliği. Bu ayar yalnızca geçerlidir **Serializer mod** ayarlanır **veri sözleşmesi serileştiricisi**.

-   **ImportXMLTypes**: Bu ayar uygulamak için veri sözleşmesi serileştiricisi yapılandırılıp yapılandırılmayacağını belirtir <xref:System.SerializableAttribute> özniteliği sınıflarına <xref:System.Runtime.Serialization.DataContractAttribute> özniteliği.  Bu ayar yalnızca geçerlidir **Serializer mod** ayarlanır **veri sözleşmesi serileştiricisi**.

-   **SupportFx35TypedDataSets**: Bu ayar, .NET Framework 3.5 için oluşturulmuş, türü belirlenmiş veri kümeleri için ek işlevler sağlamasına olanak belirtir. Zaman **Serializer mod** ayarlanır **XML serileştiricisi**, <xref:System.Data.Design.TypedDataSetSchemaImporterExtensionFx35> uzantısı bu değeri True olarak ayarlandığında XML şema içeri Aktarıcı için eklenir. Zaman **Serializer mod** ayarlanır **veri sözleşmesi serileştiricisi**, türü <xref:System.DateTimeOffset> bu değeri False olarak ayarlandığında başvurularından dahil edilmeyecek şekilde bir <xref:System.DateTimeOffset> her zaman oluşturulur eski çerçeve sürümleri için.

-   **InputXsdFiles**: Bu ayar, girdi dosyası listesini belirtir. Her dosya geçerli bir XML Şeması içermelidir.

-   **Dil**: Bu ayar, oluşturulan sözleşme kodunun dilini belirtir. Ayarı tarafından tanınan <xref:System.CodeDom.Compiler.CodeDomProvider>.

-   **NamespaceMappings**: Bu ayar, XSD hedef ad alanından eşlemeleri için CLR ad uzayını belirtir. Her eşleme, şu biçimi kullanmalıdır:

    ```xml
    "<Schema Namespace>, <CLR Namespace>"
    ```

     XML seri hale getirici, yalnızca aşağıdaki biçimde bir eşleme kabul eder:

    ```xml
    "*, <CLR Namespace>"
    ```

-   **OutputDirectory**: Bu ayar, kod dosyaları oluşturulacağı dizini belirtir.

 Ayarları, proje oluşturulduğunda Hizmet anlaşması türleri hizmet sözleşmesi dosyaları oluşturmak için kullanılır.

## <a name="using-contract-first-development"></a>Sözleşme ilk geliştirmesi kullanma
 Hizmet sözleşmesi projeye eklemeye ve yapı ayarları onaylanıyor derledikten sonra projeyi tuşlarına basarak **F6**. Hizmet sözleşmesi içerisinde tanımlanan türleri, ardından Proje için kullanılabilir olacaktır.

 Hizmet sözleşmesi içerisinde tanımlanan türler kullanmak için bir başvuru ekleyin. `ContractTypes` geçerli ad alanı altında:

```csharp
using MyProjectNamespace.ContractTypes;
```

 Hizmet sözleşmesi içerisinde tanımlanan türleri aşağıda gösterildiği gibi proje çözümlenebilir gibi olur:

 ![İlk birkaç harfini yazdıktan sonra Intellisense'te gösteren SearchRequest sınıfı.](./media/contract-first-tool/service-contract-types.png)

 Araç tarafından oluşturulan türler GeneratedXSDTypes.cs dosyasında oluşturulur. Bir dosya oluşturulur \<proje dizini > /obj/\<derleme yapılandırması > Varsayılan olarak /XSDGeneratedCode/ dizin. Bu konunun başında örnek şeması şu şekilde dönüştürülür:

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
 Hataları ve Uyarıları XSD şeması ayrıştırma karşılaşılan hatalar ve Uyarılar oluşturmak gibi görünecektir.

## <a name="interface-inheritance"></a>Devralma arabirimi
 Sözleşme ilk geliştirmesi ile arabirimi devralma kullanmak mümkün değildir; Bu, başka işlem arabirimleri davranmasına yol ile tutarlıdır. Temel arabirim devralan bir arabirim kullanmak için iki ayrı bir uç nokta kullanın. Devralınan sözleşme ilk uç noktayı kullanır ve ikinci uç nokta temel arabirim uygular.
