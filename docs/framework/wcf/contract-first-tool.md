---
description: 'Hakkında daha fazla bilgi edinin: Contract-First aracı'
title: Önce Anlaşma Aracı
ms.date: 03/30/2017
ms.assetid: 0a880690-f460-4475-a5f4-9f91ce08fcc6
ms.openlocfilehash: 6455fa866afd440e70062f8433356b13fe163a8c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99736407"
---
# <a name="contract-first-tool"></a>Önce Anlaşma Aracı

Hizmet sözleşmelerinin genellikle mevcut hizmetlerden oluşturulması gerekir. .NET Framework 4,5 ve üzeri sürümlerde, veri sözleşmesi sınıfları otomatik olarak, sözleşme ilk Aracı kullanılarak mevcut hizmetlerden otomatik olarak oluşturulabilir. İlk sözleşme aracını kullanmak için, XML şema tanımı dosyası (XSD) yerel olarak indirilmelidir; Araç, uzak veri sözleşmelerini HTTP aracılığıyla alamaz.

 Sözleşme ilk aracı, Visual Studio 2012 derleme görevi olarak tümleşiktir. Derleme görevi tarafından oluşturulan kod dosyaları proje her oluşturulduğunda oluşturulur, böylece projenin temel hizmet sözleşmesindeki değişiklikleri kolayca benimseyebilmesini sağlayabilirsiniz.

 Sözleşme-ilk aracının içeri aktarabileceğiniz şema türleri şunlardır:

```xml
<xsd:complexType>
 <xsd:simpleType>
 </xsd:simpleType>
</xsd:complexType>
```

 Basit türler, veya gibi temel elemanlar oluşturulduklarında üretilmeyecektir `Int16` `String` ; karmaşık türler türlerse üretilmeyecektir `Collection` . Türler başka bir parçasıysa de oluşturulmazlar `xsd:complexType` . Tüm bu durumlarda, bunlara bunun yerine, proje içindeki var olan türlere başvurulur.

## <a name="adding-a-data-contract-to-a-project"></a>Bir projeye veri sözleşmesi ekleme

 Sözleşmenin ilk aracı kullanılmadan önce, servis sözleşmesinin (XSD) projeye eklenmesi gerekir. Bu genel bakışın amaçları doğrultusunda, sözleşmenin ilk işlevlerini göstermek için aşağıdaki sözleşme kullanılacaktır. Bu hizmet tanımı, Bing arama API 'SI tarafından kullanılan hizmet sözleşmesinin küçük bir alt kümesidir.

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

 Yukarıdaki hizmet sözleşmesini projeye eklemek için projeye sağ tıklayın ve **Yeni Ekle...** seçeneğini belirleyin. Şablonlar iletişim kutusunun WCF bölmesinden şema tanımı ' nı seçin ve yeni Sample Contract. xsd dosyasını adlandırın. Yukarıdaki kodu kopyalayıp yeni dosyanın kod görünümüne yapıştırın.

## <a name="configuring-contract-first-options"></a>Sözleşme ilk seçeneklerini yapılandırma

 Sözleşme-ilk seçenekleri bir WCF projesinin Özellikler menüsünde yapılandırılabilir. Sözleşmenin ilk geliştirmeyi etkinleştirmek için, Proje Özellikleri penceresinin WCF sayfasında **xsd türü tanım dilini etkinleştir** onay kutusunu seçin.

 ![Sözleşmenin ilk geliştirmesi etkin olan WCF seçeneklerinin ekran görüntüsü.](./media/contract-first-tool/contract-first-options.png)

 Gelişmiş özellikleri yapılandırmak için Gelişmiş düğmesine tıklayın.

 ![Gelişmiş sözleşme kodu oluşturma ayarları iletişim kutusu.](./media/contract-first-tool/advanced-contract-settings.png)

 Aşağıdaki gelişmiş ayarlar sözleşmelerden kod üretimi için yapılandırılabilir. Ayarlar, yalnızca projedeki tüm dosyalar için yapılandırılabilir; ayarlar şu anda tek tek dosyalar için yapılandırılamaz.

- **Serileştirici modu**: Bu ayar, hizmet sözleşmesi dosyalarını okumak için hangi seri hale getiricinin kullanıldığını belirler. **XML serileştirici** seçildiğinde, **koleksiyon türleri** ve **yeniden kullanım türleri** seçenekleri devre dışıdır. Bu seçenekler yalnızca **veri sözleşmesi serileştiricisi** için geçerlidir.

- **Türleri yeniden kullan**: Bu ayar, tür yeniden kullanımı için hangi kitaplıkların kullanıldığını belirtir. Bu ayar yalnızca **seri hale getirici modu** **veri sözleşmesi serileştiricisi** olarak ayarlandıysa geçerlidir.

- **Koleksiyon türü**: Bu ayar, koleksiyon veri türü için kullanılacak tam veya bütünleştirilmiş kod nitelikli türü belirtir. Bu ayar yalnızca **seri hale getirici modu** **veri sözleşmesi serileştiricisi** olarak ayarlandıysa geçerlidir.

- **Sözlük türü**: Bu ayar, sözlük veri türü için kullanılacak tam veya bütünleştirilmiş kod nitelikli türü belirtir.

- **EnableDataBinding**: Bu ayar, <xref:System.ComponentModel.INotifyPropertyChanged> veri bağlamayı uygulamak için tüm veri türlerinde arabirimin uygulanıp etkinleştirilmeyeceğini belirtir.

- **ExcludedTypes**: Bu ayar, başvurulan derlemelerden dışlanacak tam veya bütünleştirilmiş kod nitelikli türlerin listesini belirtir. Bu ayar yalnızca **seri hale getirici modu** **veri sözleşmesi serileştiricisi** olarak ayarlandıysa geçerlidir.

- **GenerateInternalTypes**: Bu ayar, iç olarak işaretlenmiş sınıfların oluşturulup oluşturulmayacağını belirtir. Bu ayar yalnızca **seri hale getirici modu** **veri sözleşmesi serileştiricisi** olarak ayarlandıysa geçerlidir.

- **GenerateSerializableTypes**: Bu ayar özniteliği ile sınıfların oluşturulup oluşturulmayacağını belirtir <xref:System.SerializableAttribute> . Bu ayar yalnızca **seri hale getirici modu** **veri sözleşmesi serileştiricisi** olarak ayarlandıysa geçerlidir.

- **ImportXmlTypes**: Bu ayar, veri sözleşmesi serileştiricinin özniteliği olmayan sınıflara özniteliğe uygulamak üzere yapılandırılacağını belirtir <xref:System.SerializableAttribute> <xref:System.Runtime.Serialization.DataContractAttribute> .  Bu ayar yalnızca **seri hale getirici modu** **veri sözleşmesi serileştiricisi** olarak ayarlandıysa geçerlidir.

- **SupportFx35TypedDataSets**: Bu ayar, .NET Framework 3,5 için oluşturulan tür veri kümeleri için ek işlevsellik sağlayıp sağlamadığınızı belirtir. **Seri hale getirici modu** **XML seri hale getirici** olarak ayarlandığında, <xref:System.Data.Design.TypedDataSetSchemaImporterExtensionFx35> Bu değer true olarak ayarlandığında uzantı XML şeması içeri aktarıcıya eklenecektir. **Seri hale getirici modu** , **veri sözleşmesi seri hale getirici** olarak ayarlandığında, <xref:System.DateTimeOffset> Bu değer false olarak ayarlandığında tür başvurulardan dışlanır, böylece <xref:System.DateTimeOffset> daha eski Framework sürümleri için her zaman oluşturulur.

- **InputXsdFiles**: Bu ayar, giriş dosyalarının listesini belirtir. Her dosya geçerli bir XML şeması içermelidir.

- **Dil**: Bu ayar, oluşturulan sözleşme kodunun dilini belirtir. Ayar tarafından tanınabilir olmalıdır <xref:System.CodeDom.Compiler.CodeDomProvider> .

- **NamespaceMappings**: Bu ayar, xsd hedefi ad alanlarından clr ad alanlarına eşleştirmeleri belirtir. Her eşleme şu biçimi kullanmalıdır:

    ```xml
    "Schema Namespace, CLR Namespace"
    ```

     XML seri hale getirici aşağıdaki biçimde yalnızca bir eşlemeyi kabul eder:

    ```xml
    "*, CLR Namespace"
    ```

- **OutputDirectory**: Bu ayar, kod dosyalarının oluşturulacağı dizini belirtir.

 Bu ayarlar, proje oluşturulduğunda hizmet sözleşmesi dosyalarından hizmet sözleşmesi türleri oluşturmak için kullanılacaktır.

## <a name="using-contract-first-development"></a>Sözleşmenin ilk geliştirmeyi kullanma

 Hizmet sözleşmesini projeye ekledikten ve derleme ayarlarını onayladıktan sonra, **F6** tuşuna basarak projeyi derleyin. Daha sonra hizmet sözleşmesinde tanımlanan türler projede kullanılabilir olacaktır.

 Hizmet sözleşmesinde tanımlanan türleri kullanmak için `ContractTypes` geçerli ad alanının altına bir başvuru ekleyin:

```csharp
using MyProjectNamespace.ContractTypes;
```

 Bu durumda, hizmet sözleşmesinde tanımlanan türler aşağıda gösterildiği gibi projede çözülebilir:

 ![İlk birkaç harf yazdıktan sonra IntelliSense 'de gösteren SearchRequest sınıfı.](./media/contract-first-tool/service-contract-types.png)

 Araç tarafından oluşturulan türler GeneratedXSDTypes.cs dosyasında oluşturulur. Dosya \<project directory> Varsayılan olarak/obj/ \<build configuration> /XSDGeneratedCode/dizininde oluşturulur. Bu makalenin başındaki örnek şema aşağıdaki şekilde dönüştürülür:

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

 XSD şeması ayrıştırılırken karşılaşılan hatalar ve uyarılar, derleme hataları ve uyarılar olarak görünür.

## <a name="interface-inheritance"></a>Arabirim devralma

 Öncelikle, sözleşmenin ilk geliştirmeyle Arabirim devralma kullanılması mümkün değildir; Bu, arabirimlerin diğer işlemlerde davranış şekli ile tutarlıdır. Temel arabirim devralan bir arabirim kullanmak için iki ayrı uç nokta kullanın. İlk uç nokta devralınan sözleşmeyi kullanır ve ikinci uç nokta temel arabirimi uygular.
