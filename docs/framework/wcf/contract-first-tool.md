---
title: Önce Anlaşma Aracı
ms.date: 03/30/2017
ms.assetid: 0a880690-f460-4475-a5f4-9f91ce08fcc6
ms.openlocfilehash: 36e1a3e19f802ca5b74cf50f5bcd57c167e31e33
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291700"
---
# <a name="contract-first-tool"></a>Önce Anlaşma Aracı
Hizmet sözleşmelerinin genellikle varolan hizmetlerden oluşturulması gerekir. .NET Framework 4.5 ve sonraki sürümlerinde, ilk sözleşme aracı kullanılarak varolan hizmetlerden otomatik olarak veri sözleşmesi sınıfları oluşturulabilir. Sözleşmenin ilk aracını kullanmak için XML şema tanım dosyasının (XSD) yerel olarak indirilmesi gerekir; araç, HTTP üzerinden uzaktan veri sözleşmeleri içe aktaramaz.

 Sözleşme ilk aracı Visual Studio entegre edilmiştir 2012 bir yapı görevi olarak. Yapı görevi tarafından oluşturulan kod dosyaları, projenin temel hizmet sözleşmesindeki değişiklikleri kolayca benimseyebilmeleri için proje her oluşturulduğunda oluşturulur.

 Sözleşmeilk aracının içe aktarabileceği şema türleri şunlardır:

```xml
<xsd:complexType>
 <xsd:simpleType>
 </xsd:simpleType>
</xsd:complexType>
```

 Basit türler gibi `Int16` ilkel veya eğer `String`oluşturulmaz; türünde `Collection`ise karmaşık türleri oluşturulmayacaktır. Türler, başka bir `xsd:complexType`ürünün parçasıysa da oluşturulmayacaktır. Tüm bu durumlarda, türler projedeki varolan türlere başvurulacaktır.

## <a name="adding-a-data-contract-to-a-project"></a>Projeye veri sözleşmesi ekleme
 Sözleşmenin ilk aracının kullanılabilmesi için hizmet sözleşmesinin (XSD) projeye eklenmesi gerekir. Bu genel bakışın amaçları için, sözleşmenin ilk işlevlerini göstermek için aşağıdaki sözleşme kullanılacaktır. Bu hizmet tanımı, Bing'in arama API'si tarafından kullanılan hizmet sözleşmesinin küçük bir alt kümesidir.

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

 Yukarıdaki hizmet sözleşmesini projeye eklemek için projeye sağ tıklayın ve **Yeni Ekle...'yu**seçin. Şablonlar iletişim kutusunun WCF bölmesinden Şema Tanımı'nı seçin ve yeni dosya SampleContract.xsd'yi adlandırın. Yukarıdaki kodu yeni dosyanın kod görünümüne kopyalayıp yapıştırın.

## <a name="configuring-contract-first-options"></a>Sözleşme ilk seçeneklerini yapılandırma
 Sözleşme ilk seçenekleri bir WCF projesinin Özellikler menüsünde yapılandırılabilir. Sözleşmenin ilk geliştirmesini etkinleştirmek için, proje özellikleri penceresinin WCF sayfasında **XSD'yi Tür Tanımı Dili olarak etkinleştir'i** seçin.

 ![Sözleşme ilk geliştirme etkin WCF Seçenekleri ekran görüntüsü.](./media/contract-first-tool/contract-first-options.png)

 Gelişmiş özellikleri yapılandırmak için Gelişmiş düğmesini tıklatın.

 ![Gelişmiş Sözleşme Kodu Oluşturma Ayarları iletişim kutusu.](./media/contract-first-tool/advanced-contract-settings.png)

 Aşağıdaki gelişmiş ayarlar sözleşmelerden kod oluşturma için yapılandırılabilir. Ayarlar yalnızca projedeki tüm dosyalar için yapılandırılabilir; ayarlar şu anda tek tek dosyalar için yapılandırılamaz.

- **Serializer Modu**: Bu ayar, hizmet sözleşme dosyalarını okumak için hangi serializer'ın kullanılacağını belirler. **XML Serializer** seçildiğinde, Koleksiyon Türleri ve **Yeniden Kullanma** **Türleri** seçenekleri devre dışı bırakılır. Bu seçenekler yalnızca **Veri Sözleşmesi Serializer**için geçerlidir.

- **Yeniden Kullanım Türleri**: Bu ayar, tür yeniden kullanımı için hangi kitaplıkların kullanıldığını belirtir. Bu ayar yalnızca **Serializer Modu** **Veri Sözleşmesi Serializer'a**ayarlanırsa geçerlidir.

- **Toplama Türü**: Bu ayar, toplama veri türü için kullanılacak tam nitelikli veya montaj nitelikli türü belirtir. Bu ayar yalnızca **Serializer Modu** **Veri Sözleşmesi Serializer'a**ayarlanırsa geçerlidir.

- **Sözlük Türü**: Bu ayar, sözlük veri türü için kullanılacak tam nitelikli veya derleme nitelikli türü belirtir.

- **EnableDataBinding**: Bu ayar, veri <xref:System.ComponentModel.INotifyPropertyChanged> bağlamayı uygulamak için tüm veri türlerinde arabirimin uygulanıp uygulanmayacağını belirtir.

- **Dışlanmış Tipler**:Bu ayar, başvurulan derlemelerin dışında tutulacak tam nitelikli veya derleme nitelikli türlerin listesini belirtir. Bu ayar yalnızca **Serializer Modu** **Veri Sözleşmesi Serializer'a**ayarlanırsa geçerlidir.

- **GenerateInternalTypes**: Bu ayar, dahili olarak işaretlenmiş sınıfların oluşturup oluşturmayacağını belirtir. Bu ayar yalnızca **Serializer Modu** **Veri Sözleşmesi Serializer'a**ayarlanırsa geçerlidir.

- **GenerateSerializableTypes**: Bu ayar öznitelik ile <xref:System.SerializableAttribute> sınıflar oluşturmak için olup olmadığını belirtir. Bu ayar yalnızca **Serializer Modu** **Veri Sözleşmesi Serializer'a**ayarlanırsa geçerlidir.

- **ImportXMLTypes**: Bu ayar, öznitelik olmadan <xref:System.SerializableAttribute> <xref:System.Runtime.Serialization.DataContractAttribute> sınıflara öznitelik uygulamak için veri sözleşmesi serializer yapılandırılıp yapılandırılması nı belirtir.  Bu ayar yalnızca **Serializer Modu** **Veri Sözleşmesi Serializer'a**ayarlanırsa geçerlidir.

- **SupportFx35TypedDataSets**: Bu ayar, .NET Framework 3.5 için oluşturulan yazılı veri kümeleri için ek işlevsellik sağlanıp sağlanmayacağını belirtir. **Serializer Modu** **XML Serializer**olarak <xref:System.Data.Design.TypedDataSetSchemaImporterExtensionFx35> ayarlandığında, bu değer True olarak ayarlandığında uzantı XML şema içe aktarıcısına eklenir. **Serializer Modu** Veri **Sözleşmesi Serializer**olarak <xref:System.DateTimeOffset> ayarlandığında, bu değer False olarak ayarlandığında tür Başvurular <xref:System.DateTimeOffset> dışında tutulur, böylece eski çerçeve sürümleri için her zaman bir a oluşturulur.

- **InputXsdFiles**: Bu ayar, giriş dosyalarının listesini belirtir. Her dosya geçerli bir XML şeması içermelidir.

- **Dil**: Bu ayar, oluşturulan sözleşme kodunun dilini belirtir. Ayar tarafından <xref:System.CodeDom.Compiler.CodeDomProvider>tanınabilir olmalıdır.

- **NamespaceMappings**: Bu ayar, XSD Hedef Ad Alanlarından CLR ad alanlarına eşlemeleri belirtir. Her eşleme aşağıdaki biçimi kullanmalıdır:

    ```xml
    "Schema Namespace, CLR Namespace"
    ```

     XML Serializer yalnızca aşağıdaki biçimde bir eşleme kabul eder:

    ```xml
    "*, CLR Namespace"
    ```

- **OutputDirectory**: Bu ayar, kod dosyalarının oluşturulacağı dizini belirtir.

 Ayarlar, proje oluşturulurken hizmet sözleşmesi dosyalarından hizmet sözleşmesi türleri oluşturmak için kullanılır.

## <a name="using-contract-first-development"></a>Sözleşme-ilk geliştirme kullanma
 Hizmet sözleşmesini projeye ekledikten ve yapı ayarlarını doğruladıktan sonra **F6**tuşuna basarak projeyi oluşturun. Hizmet sözleşmesinde tanımlanan türler daha sonra projede kullanılabilir olacaktır.

 Hizmet sözleşmesinde tanımlanan türleri kullanmak için `ContractTypes` geçerli ad alanı altında bir başvuru ekleyin:

```csharp
using MyProjectNamespace.ContractTypes;
```

 Hizmet sözleşmesinde tanımlanan türler, aşağıda gösterildiği gibi projede çözülebilir olacaktır:

 ![SearchRequest sınıfı ilk birkaç harfi yazdıktan sonra IntelliSense'de gösteriliyor.](./media/contract-first-tool/service-contract-types.png)

 Araç tarafından oluşturulan türler GeneratedXSDTypes.cs dosyasında oluşturulur. Dosya, varsayılan olarak \<proje dizininde>/obj/\<yapı yapılandırması>/XSDGeneratedCode/ dizininde oluşturulur. Bu makalenin başındaki örnek şema aşağıdaki gibi dönüştürülür:

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
 XSD şema ayrıştırma karşılaşılan hatalar ve uyarılar yapı hataları ve uyarılar olarak görünür.

## <a name="interface-inheritance"></a>Arayüz Devralma
 Sözleşme-ilk geliştirme ile arayüz kalıtım kullanmak mümkün değildir; bu, arabirimlerin diğer işlemlerde nasıl davranış biçimiyle tutarlıdır. Temel arabirimi devralan bir arabirim kullanmak için iki ayrı uç nokta kullanın. İlk uç nokta devralınan sözleşmeyi kullanır ve ikinci uç nokta temel arabirimi uygular.
