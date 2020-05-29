---
title: ASP.NET Web Hizmetlerini Geliştirmeye Göre WCF ile Karşılaştırma
ms.date: 03/30/2017
ms.assetid: f362d00e-ce82-484f-9d4f-27e579d5c320
ms.openlocfilehash: c5a2145a6d7b631a666df94eb0c1fc53cbc3c55f
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202258"
---
# <a name="comparing-aspnet-web-services-to-wcf-based-on-development"></a>ASP.NET Web Hizmetlerini Geliştirmeye Göre WCF ile Karşılaştırma

Windows Communication Foundation (WCF), WCF uygulamalarının ASP.NET Web Hizmetleri gibi programlanmış ve yapılandırılmış olmasını sağlamak ve davranışlarını taklit etmek için bir ASP.NET uyumluluk modu seçeneği vardır. Aşağıdaki bölümlerde, her iki teknolojiyi de kullanarak uygulama geliştirmek için gereklere bağlı olarak ASP.NET Web Hizmetleri ve WCF karşılaştırılmaktadır.

## <a name="data-representation"></a>Veri gösterimi

Bir Web hizmetinin ASP.NET ile geliştirilmesi genellikle hizmetin kullanacağı karmaşık veri türlerini tanımlamaya başlar. ASP.NET, <xref:System.Xml.Serialization.XmlSerializer> bir hizmete veya bir hizmete iletim için .NET Framework türleri tarafından temsil edilen VERILERI XML 'e çevirmek ve XML olarak alınan verileri .NET Framework nesnelerine dönüştürmek için kullanır. Bir ASP.NET hizmetinin kullanacağı karmaşık veri türlerini tanımlama, <xref:System.Xml.Serialization.XmlSerializer> XML 'den ve öğesinden seri hale getirebilen .NET Framework sınıflarının tanımını gerektirir. Bu tür sınıflar el ile yazılabilir veya komut satırı XML şemaları/veri türleri destek yardımcı programı olan xsd. exe kullanılarak XML şemasında türlerin tanımlarından oluşturulabilir.

Aşağıda, <xref:System.Xml.Serialization.XmlSerializer> XML 'den ve öğesinden seri hale getirebilen .NET Framework sınıfları tanımlarken bildiğiniz önemli sorunların bir listesi verilmiştir:

- Yalnızca .NET Framework nesnelerinin ortak alanları ve özellikleri XML olarak çevrilir.

- Koleksiyon sınıflarının örnekleri yalnızca, sınıflar veya arabirimini uygularsa XML olarak seri hale getirilebilir <xref:System.Collections.IEnumerable> <xref:System.Collections.ICollection> .

- Arabirimini uygulayan sınıflar, gibi <xref:System.Collections.IDictionary> <xref:System.Collections.Hashtable> , XML içine serileştirilemiyor.

- Ad alanındaki harika birçok öznitelik türü, <xref:System.Xml.Serialization> sınıf ÖRNEKLERININ XML 'de nasıl temsil edileceğini denetlemek için bir .NET Framework sınıfına ve üyelerine eklenebilir.

WCF uygulama geliştirme genellikle karmaşık türlerin tanımıyla de başlar. WCF, ASP.NET Web Hizmetleri ile aynı .NET Framework türlerini kullanacak şekilde yapılabilir.

WCF <xref:System.Runtime.Serialization.DataContractAttribute> ve, <xref:System.Runtime.Serialization.DataMemberAttribute> TÜRÜN örneklerinin XML 'e serileştirilmekte olduğunu ve aşağıdaki örnek kodda gösterildiği gibi türün hangi belirli alan veya özelliklerinin serileştirildiğine işaret etmek için .NET Framework türlerine eklenebilir.

```csharp
//Example One:
[DataContract]
public class LineItem
{
    [DataMember]
    public string ItemNumber;
    [DataMember]
    public decimal Quantity;
    [DataMember]
    public decimal UnitPrice;
}

//Example Two:
public class LineItem
{
    [DataMember]
    private string itemNumber;
    [DataMember]
    private decimal quantity;
    [DataMember]
    private decimal unitPrice;

    public string ItemNumber
    {
      get
      {
          return this.itemNumber;
      }

      set
      {
          this.itemNumber = value;
      }
    }

    public decimal Quantity
    {
        get
        {
            return this.quantity;
        }

        set
        {
            this.quantity = value;
        }
    }

    public decimal UnitPrice
    {
      get
      {
          return this.unitPrice;
      }

      set
      {
          this.unitPrice = value;
      }
    }
}

//Example Three:
public class LineItem
{
     private string itemNumber;
     private decimal quantity;
     private decimal unitPrice;

     [DataMember]
     public string ItemNumber
     {
       get
       {
          return this.itemNumber;
       }

       set
       {
           this.itemNumber = value;
       }
     }

     [DataMember]
     public decimal Quantity
     {
          get
          {
              return this.quantity;
          }

          set
          {
             this.quantity = value;
          }
     }

     [DataMember]
     public decimal UnitPrice
     {
          get
          {
              return this.unitPrice;
          }

          set
          {
              this.unitPrice = value;
          }
     }
}
```

<xref:System.Runtime.Serialization.DataContractAttribute>Bir türün alan veya özelliklerinin sıfır veya daha fazla seri hale getirildiğini, ancak <xref:System.Runtime.Serialization.DataMemberAttribute> belirli bir alanın veya özelliğin serileştirilme olduğunu gösterir. <xref:System.Runtime.Serialization.DataContractAttribute>Bir sınıfa veya yapıya uygulanabilir. , <xref:System.Runtime.Serialization.DataMemberAttribute> Bir alana veya özelliğe uygulanabilir ve özniteliğin uygulandığı alanlar ve Özellikler herkese açık veya özel olabilir. Bunlara uygulanmış olan türlerin örnekleri, <xref:System.Runtime.Serialization.DataContractAttribute> WCF 'de veri sözleşmeleri olarak adlandırılır. Kullanılarak XML olarak serileştirilir <xref:System.Runtime.Serialization.DataContractSerializer> .

Aşağıda, kullanarak <xref:System.Runtime.Serialization.DataContractSerializer> ve diğer <xref:System.Xml.Serialization.XmlSerializer> ad alanının çeşitli özniteliklerinin kullanılmasıyla arasındaki önemli farklılıkların bir listesi verilmiştir <xref:System.Xml.Serialization> .

- <xref:System.Xml.Serialization.XmlSerializer>Ve <xref:System.Xml.Serialization> ad alanının öznitelikleri, .NET Framework türlerini XML şemasında tanımlanmış herhangi bir geçerli türle eşlemenizi sağlamak üzere tasarlanmıştır ve bu nedenle BIR türün XML 'de nasıl temsil edildiği konusunda çok kesin bir denetim sağlar. <xref:System.Runtime.Serialization.DataContractSerializer> <xref:System.Runtime.Serialization.DataContractAttribute> Ve <xref:System.Runtime.Serialization.DataMemberAttribute> bir türün XML 'de nasıl temsil edildiği konusunda çok az denetim sağlar. Yalnızca türü ve içindeki alanları ya da özellikleri temsil etmek için kullanılan ad alanlarını ve adları, XML 'de alan ve özelliklerin bulunduğu diziyi belirtebilirsiniz:

  ```csharp
  [DataContract(
  Namespace="urn:Contoso:2006:January:29",
  Name="LineItem")]
  public class LineItem
  {
        [DataMember(Name="ItemNumber",IsRequired=true,Order=0)]
        public string itemNumber;
        [DataMember(Name="Quantity",IsRequired=false,Order = 1)]
        public decimal quantity;
        [DataMember(Name="Price",IsRequired=false,Order = 2)]
        public decimal unitPrice;
  }
  ```

  .NET türünü temsil etmek için kullanılan XML yapısına ilişkin diğer her şey, tarafından belirlenir <xref:System.Runtime.Serialization.DataContractSerializer> .

- Bir türün XML 'de nasıl temsil edildiği konusunda çok fazla denetime izin verilmez, serileştirme işlemi için yüksek düzeyde öngörülebilir hale gelir ve bu <xref:System.Runtime.Serialization.DataContractSerializer> nedenle iyileştirilmesi kolaylaşır. Tasarımının pratik bir avantajı <xref:System.Runtime.Serialization.DataContractSerializer> daha iyi performans, yaklaşık yüzde on daha iyi performans.

- İle birlikte kullanılacak öznitelikleri, <xref:System.Xml.Serialization.XmlSerializer> türünün hangi alanların veya ÖZELLIKLERIN XML olarak serileştirildiği göstermez, <xref:System.Runtime.Serialization.DataMemberAttribute> için için öğesinin, <xref:System.Runtime.Serialization.DataContractSerializer> açıkça hangi alanların veya özelliklerin serileştirildiği gösterilir. Bu nedenle, veri sözleşmeleri, bir uygulamanın gönderileceği ve alınacağı verilerin yapısı hakkında açık sözleşmelerdir.

- <xref:System.Xml.Serialization.XmlSerializer>Yalnızca bir .NET nesnesinin ortak ÜYELERINI XML 'e çevirebilir, <xref:System.Runtime.Serialization.DataContractSerializer> Bu üyelerin erişim değiştiricilerinden bağımsız olarak nesne üyelerini XML 'e çevirebilir.

- Türlerin genel olmayan üyelerini XML olarak seri hale getirebilmek sonucunda, XML 'de seri hale geyebilen <xref:System.Runtime.Serialization.DataContractSerializer> çeşitli .net türlerinde daha az kısıtlama içerir. Özellikle, arabirimini uygulayan gibi XML türlerine çeviri yapabilir <xref:System.Collections.Hashtable> <xref:System.Collections.IDictionary> . , <xref:System.Runtime.Serialization.DataContractSerializer> Türün tanımını değiştirmek veya bir sarmalayıcı geliştirmek zorunda kalmadan, önceden var olan herhangi bir .NET türünün ÖRNEKLERINI XML olarak seri hale getirmek çok daha olasıdır.

- <xref:System.Runtime.Serialization.DataContractSerializer>Bir türün genel olmayan üyelerine erişebilmekte olan başka bir sonuç ise tam güven gerektirmesidir, ancak bunu yapmaz <xref:System.Xml.Serialization.XmlSerializer> . Tam güven kodu erişim izni, kodun yürütüldüğü kimlik bilgileri kullanılarak erişilebilen bir makinedeki tüm kaynaklara tam erişim sağlar. Tam güvenilir kod, makinenizde bulunan tüm kaynaklara eriştiği için bu seçenek dikkatli kullanılmalıdır.

- , <xref:System.Runtime.Serialization.DataContractSerializer> Sürüm oluşturma için bazı destek içerir:

  - , <xref:System.Runtime.Serialization.DataMemberAttribute> <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> Önceki sürümlerde mevcut olmayan bir veri sözleşmesinin yeni sürümlerine eklenen üyeler için yanlış değeri atanabilen bir özelliğe sahiptir ve böylece sözleşmenin daha yeni sürümüne sahip uygulamaların önceki sürümleri işleyebilmesini sağlar.

  - Bir veri sözleşmesinin <xref:System.Runtime.Serialization.IExtensibleDataObject> arabirimini uygulaması sayesinde, bir <xref:System.Runtime.Serialization.DataContractSerializer> veri sözleşmesinin daha yeni sürümlerinde tanımlanan üyelerin, sözleşmenin önceki sürümleriyle uygulamalar aracılığıyla geçişine izin verebilir.

Tüm farklılıklara rağmen, <xref:System.Xml.Serialization.XmlSerializer> Varsayılan olarak bir türü seri hale getirilen XML, <xref:System.Runtime.Serialization.DataContractSerializer> bir türü seri hale getirilen XML ile aynıdır, ancak XML için ad alanı açıkça tanımlanmıştır. Her iki serileştiriciyle birlikte kullanılmak üzere öznitelikleri olan aşağıdaki sınıf, ile ve arasında anlamsal özdeş XML 'e çevrilir <xref:System.Xml.Serialization.XmlSerializer> <xref:System.Runtime.Serialization.DataContractAttribute> :

```csharp
[Serializable]
[XmlRoot(Namespace="urn:Contoso:2006:January:29")]
[DataContract(Namespace="urn:Contoso:2006:January:29")]
public class LineItem
{
     [DataMember]
     public string ItemNumber;
     [DataMember]
     public decimal Quantity;
     [DataMember]
     public decimal UnitPrice;
}
```

Windows yazılım geliştirme seti (SDK), [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)adlı bir komut satırı aracı içerir. ASP.NET Web hizmetleriyle kullanılan xsd. exe aracı gibi, Svcutil. exe, XML şemasından .NET veri türlerinin tanımlarını oluşturabilir. Türler, XML <xref:System.Runtime.Serialization.DataContractSerializer> şeması tarafından tanımlanan BIÇIMDE XML yayıyorsa, veri sözleşmelerdir; Aksi takdirde, kullanılarak serileştirme amaçlıdır <xref:System.Xml.Serialization.XmlSerializer> . Svcutil. exe, kendi anahtarını kullanarak veri sözleşmelerinden bir XML şeması da oluşturabilir `dataContractOnly` .

> [!NOTE]
> ASP.NET Web Hizmetleri tarafından kullanılsa da WCF <xref:System.Xml.Serialization.XmlSerializer> ASP.NET uyumluluk modu, WCF hizmetleri ASP.NET Web hizmetlerinin davranışını taklit etse de ASP.NET uyumluluk seçeneği, bir ile kullanımını kısıtlamaz <xref:System.Xml.Serialization.XmlSerializer> . Bunlardan biri, <xref:System.Runtime.Serialization.DataContractSerializer> ASP.NET uyumluluk modunda çalışan hizmetlerini kullanmaya devam edebilir.

## <a name="service-development"></a>Hizmet geliştirme

ASP.NET kullanarak bir hizmet geliştirmek için, <xref:System.Web.Services.WebService> özniteliği bir sınıfa eklemek ve <xref:System.Web.Services.WebMethodAttribute> hizmetin işlemleri olması gereken sınıf ' metotlarından birine eklemektir:

```csharp
[WebService]
public class Service : T:System.Web.Services.WebService
{
    [WebMethod]
    public string Echo(string input)
    {
       return input;
    }
}
```

ASP.NET 2,0, <xref:System.Web.Services.WebService> <xref:System.Web.Services.WebMethodAttribute> bir sınıfı yerine özniteliği ve bir arabirime ekleme ve arabirimi uygulamak için bir sınıf yazma seçeneğini sunmuştur:

```csharp
[WebService]
public interface IEcho
{
    [WebMethod]
    string Echo(string input);
}

public class Service : IEcho
{

   public string Echo(string input)
   {
        return input;
    }
}
```

Bu seçeneğin kullanılması tercih edilmelidir çünkü özniteliğe sahip arabirim, <xref:System.Web.Services.WebService> hizmet tarafından gerçekleştirilen işlemler için, aynı sözleşmeyi farklı yollarla uygulayabilecek çeşitli sınıflarla yeniden kullanılabilen işlemler için bir sözleşme oluşturur.

Bir veya daha fazla WCF uç noktası tanımlayarak bir WCF hizmeti sağlanır. Bir uç nokta, bir adres, bağlama ve hizmet sözleşmesi tarafından tanımlanır. Adres, hizmetin nerede olduğunu tanımlar. Bağlama, hizmetle nasıl iletişim kuracağını belirtir. Hizmet sözleşmesi, hizmetin gerçekleştirebileceği işlemleri tanımlar.

Hizmet sözleşmesi genellikle, bir arabirim eklenerek ve ' den önce tanımlanmıştır <xref:System.ServiceModel.ServiceContractAttribute> <xref:System.ServiceModel.OperationContractAttribute> :

```csharp
[ServiceContract]
public interface IEcho
{
     [OperationContract]
     string Echo(string input);
}
```

<xref:System.ServiceModel.ServiceContractAttribute>Arabirimin BIR WCF hizmeti sözleşmesi tanımladığını ve <xref:System.ServiceModel.OperationContractAttribute> arabirimin yöntemlerinin, varsa hizmet sözleşmesinin işlemlerini tanımladığını belirtir.

Bir hizmet sözleşmesi tanımlandıktan sonra, sınıfı hizmet sözleşmesinin tanımlandığı arabirimi uygulayarak bir sınıfta uygulanır:

```csharp
public class Service : IEcho
{
    public string Echo(string input)
    {
       return input;
    }
}
```

Bir hizmet sözleşmesini uygulayan bir sınıf, WCF 'de hizmet türü olarak adlandırılır.

Bir sonraki adım, bir adresi ve bağlamayı bir hizmet türüyle ilişkilendirmekte. Bu, genellikle dosyayı doğrudan düzenleyerek veya WCF ile birlikte sunulan bir yapılandırma Düzenleyicisi kullanılarak bir yapılandırma dosyasında yapılır. Yapılandırma dosyasına bir örnek aşağıda verilmiştir.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
     <system.serviceModel>
      <services>
      <service name="Service ">
       <endpoint
        address="EchoService"
        binding="basicHttpBinding"
        contract="IEchoService "/>
      </service>
      </services>
     </system.serviceModel>
</configuration>
```

Bağlama, uygulamayla iletişim kurmak için protokoller kümesini belirtir. Aşağıdaki tabloda, genel seçenekleri temsil eden sistem tarafından sunulan bağlamalar listelenmektedir.

|Adı|Amaç|
|----------|-------------|
|Kullanmayı|WS-BasicProfile 1,1 ve temel güvenlik profili 1,0 ' i destekleyen Web Hizmetleri ve istemcilerle birlikte çalışabilirlik.|
|WSHttpBinding|HTTP üzerinden WS-* protokollerini destekleyen Web Hizmetleri ve istemcilerle birlikte çalışabilirlik.|
|WSDualHttpBinding|Bir ilk ileti alıcısının doğrudan ilk gönderene yanıt içermediği, ancak bir süre içinde, WS-* protokolleriyle birlikte HTTP kullanarak istediğiniz sayıda yanıtı aktarabileceği çift yönlü HTTP iletişimi.|
|WSFederationBinding|Bir hizmetin kaynaklarına erişimin, açıkça tanımlanmış bir kimlik bilgisi sağlayıcısı tarafından verilen kimlik bilgilerine göre denetlenebileceği HTTP iletişimi.|
|NetTcpBinding|Ağ genelindeki WCF yazılım varlıkları arasında güvenli, güvenilir, yüksek performanslı iletişim.|
|NetNamedPipeBinding|Aynı makinede WCF yazılım varlıkları arasında güvenli, güvenilir, yüksek performanslı iletişim.|
|NetMsmqBinding|MSMQ kullanarak WCF yazılım varlıkları arasındaki iletişim.|
|MsmqIntegrationBinding|Bir WCF yazılım varlığı ile başka bir yazılım varlığı arasında MSMQ kullanarak iletişim.|
|NetPeerTcpBinding|Windows Eşler arası ağ kullanarak WCF yazılım varlıkları arasında iletişim.|

Sistem tarafından sunulan bağlama, <xref:System.ServiceModel.BasicHttpBinding> ASP.NET Web Hizmetleri tarafından desteklenen protokol kümesini içerir.

WCF uygulamaları için özel bağlamalar, WCF 'nin tek tek protokolleri uygulamak için kullandığı bağlama öğesi sınıflarının koleksiyonları olarak kolayca tanımlanır. Yeni bağlama öğeleri, ek protokolleri temsil etmek için yazılabilir.

Hizmet türlerinin iç davranışı, davranışlar adlı bir sınıf ailesinin özellikleri kullanılarak ayarlanabilir. Burada, <xref:System.ServiceModel.ServiceBehaviorAttribute> sınıf, hizmet türünün çok iş parçacıklı olduğunu belirtmek için kullanılır.

```csharp
[ServiceBehavior(ConcurrencyMode=ConcurrencyMode.Multiple)]
public class DerivativesCalculatorServiceType: IDerivativesCalculator
```

Gibi bazı davranışlar <xref:System.ServiceModel.ServiceBehaviorAttribute> öznitelikleri vardır. Kullanıcılar, yöneticilerin ayarlamak istedikleri özelliklere sahip olanlar, bir uygulamanın yapılandırmasında değiştirilebilir.

Programlama hizmeti türlerinde, sınıfının sık kullanılan kullanımı yapılır <xref:System.ServiceModel.OperationContext> . Statik <xref:System.ServiceModel.OperationContext.Current%2A> özelliği, bir işlemin çalıştığı bağlam hakkındaki bilgilere erişim sağlar. <xref:System.ServiceModel.OperationContext>, <xref:System.Web.HttpContext> ve <xref:System.EnterpriseServices.ContextUtil> sınıflarına benzerdir.

## <a name="hosting"></a>Barındırma

ASP.NET Web Hizmetleri bir sınıf kitaplığı derlemesine derlenir. Service File adlı bir dosya,. asmx uzantısına sahiptir ve `@ WebService` hizmet için kodu ve bulunduğu derlemeyi içeren sınıfı tanımlayan bir yönerge içerir.

`<%@ WebService Language="C#" Class="Service,ServiceAssembly" %>`

Hizmet dosyası Internet Information Services (IIS) içinde bir ASP.NET uygulama köküne kopyalanır ve derleme bu uygulama kökünün \bin alt dizinine kopyalanır. Daha sonra uygulama, uygulama kökündeki hizmet dosyasının Tekdüzen Kaynak Konum Belirleyicisi (URL) kullanılarak erişilebilir.

WCF Hizmetleri IIS 5,1 veya 6,0 ' de, IIS 7,0 'nin bir parçası olarak sunulan Windows Işlem etkinleştirme hizmeti (WAS) ve herhangi bir .NET uygulaması içinde kolayca barındırılabilir. IIS 5,1 veya 6,0 ' de bir hizmeti barındırmak için hizmetin iletişim aktarım protokolü olarak HTTP kullanması gerekir.

IIS 5,1, 6,0 veya içinde bir hizmet barındırmak için aşağıdaki adımları kullanın:

1. Hizmet türünü bir sınıf kitaplığı derlemesinde derleyin.

2. Hizmet türünü tanımlamak için bir yönergesi ile. svc uzantılı bir hizmet dosyası oluşturun `@ ServiceHost` :

    `<%@ServiceHost language="c#" Service="MyService" %>`

3. Hizmet dosyasını bir sanal dizine ve derlemeye bu sanal dizinin \bin alt dizinine kopyalayın.

4. Yapılandırma dosyasını sanal dizine kopyalayın ve Web. config olarak adlandırın.

Uygulamaya daha sonra uygulama kökündeki hizmet dosyasının URL 'SI kullanılarak erişilebilir.

Bir .NET uygulamasında bir WCF hizmetini barındırmak için, hizmet türünü uygulama tarafından başvurulan bir sınıf kitaplığı derlemesinde derleyin ve uygulamayı, sınıfı kullanarak hizmeti barındıracak şekilde programlayabilirsiniz <xref:System.ServiceModel.ServiceHost> . Aşağıdakiler, gerekli temel programlama örneğidir:

```csharp
string httpBaseAddress = "http://www.contoso.com:8000/";
string tcpBaseAddress = "net.tcp://www.contoso.com:8080/";

Uri httpBaseAddressUri = new Uri(httpBaseAddress);
Uri tcpBaseAddressUri = new Uri(tcpBaseAddress);

Uri[] baseAddresses = new Uri[] {
 httpBaseAddressUri,
 tcpBaseAddressUri};

using(ServiceHost host = new ServiceHost(
typeof(Service), //"Service" is the name of the service type baseAddresses))
{
     host.Open();

     […] //Wait to receive messages
     host.Close();
}
```

Bu örnek, bir veya daha fazla Aktarım Protokolü adresinin bir oluşturma sırasında nasıl belirtildiği gösterilmektedir <xref:System.ServiceModel.ServiceHost> . Bu adreslere taban adresler denir.

WCF hizmetinin herhangi bir uç noktası için belirtilen adres, uç noktanın ana adresinin temel adresiyle ilişkili bir adrestir. Ana bilgisayar her iletişim Aktarım Protokolü için bir temel adrese sahip olabilir. Önceki yapılandırma dosyasındaki örnek yapılandırmada, <xref:System.ServiceModel.BasicHttpBinding> uç nokta için seçilen, aktarım protokolü olarak http 'yi kullanır, bu nedenle uç noktanın adresi `EchoService` ana bilgisayarın http taban adresine görelidir. Yukarıdaki örnekteki ana bilgisayar söz konusu olduğunda, HTTP temel adresi olur `http://www.contoso.com:8000/` . IIS veya WAS içinde barındırılan bir hizmet için temel adres, hizmetin hizmet dosyasının URL 'sidir.

Yalnızca IIS veya WAS 'da barındırılan ve yalnızca Aktarım Protokolü olarak HTTP ile yapılandırılmış olan hizmetler, WCF ASP.NET uyumluluk modu seçeneğini kullanacak şekilde yapılabilir. Bu seçeneği açık olarak açmak aşağıdaki adımları gerektirir.

1. Programcının <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> özniteliği hizmet türüne eklemesi ve ASP.NET uyumluluk modunun izin verileceğini veya gerekli olduğunu belirtmesi gerekir.

    ```csharp
    [System.ServiceModel.Activation.AspNetCompatibilityRequirements(
          RequirementsMode=AspNetCompatibilityRequirementsMode.Require)]
    public class DerivativesCalculatorServiceType: IDerivativesCalculator
    ```

2. Yöneticinin uygulamayı ASP.NET uyumluluk modunu kullanacak şekilde yapılandırması gerekir.

    ```xml
    <configuration>
         <system.serviceModel>
          <services>
          […]
          </services>
          <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>
        </system.serviceModel>
    </configuration>
    ```

    WCF uygulamaları,. svc yerine hizmet dosyaları için uzantısı olarak. asmx kullanacak şekilde de yapılandırılabilir.

    ```xml
    <system.web>
         <compilation>
          <compilation debug="true">
          <buildProviders>
           <remove extension=".asmx"/>
           <add extension=".asmx"
            type="System.ServiceModel.ServiceBuildProvider,
            System.ServiceModel,
            Version=3.0.0.0,
            Culture=neutral,
            PublicKeyToken=b77a5c561934e089" />
          </buildProviders>
          </compilation>
         </compilation>
    </system.web>
    ```

    Bu seçenek, WCF 'yi kullanmak üzere bir hizmeti değiştirirken. asmx hizmet dosyalarının URL 'Lerini kullanmak üzere yapılandırılmış istemcileri değiştirmenize gerek kalmadan sizi kaydedebilir.

## <a name="client-development"></a>İstemci Geliştirme

ASP.NET Web Hizmetleri için istemciler,. asmx dosyasının URL 'sini girdi olarak sağlayan WSDL. exe komut satırı aracı kullanılarak oluşturulur. WCF tarafından sunulan ilgili araç [ServiceModel meta veri yardımcı programı aracıdır (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Hizmet sözleşmesinin tanımına ve bir WCF istemci sınıfının tanımına sahip bir kod modülü oluşturur. Ayrıca, hizmetin adresi ve bağlamasını içeren bir yapılandırma dosyası da oluşturur.

Uzak bir hizmetin istemcisinin programlama aşamasında, genellikle zaman uyumsuz bir modele göre programlanması önerilir. WSDL. exe aracı tarafından oluşturulan kod her zaman hem zaman uyumlu hem de zaman uyumsuz bir model için varsayılan olarak sağlar. [ServiceModel meta veri yardımcı programı (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tarafından oluşturulan kod, her iki model için de sağlayabilir. Varsayılan olarak zaman uyumlu model sağlar. Araç, anahtarla yürütülürse `/async` , oluşturulan kod zaman uyumsuz model için sağlar.

ASP tarafından oluşturulan WCF istemci sınıflarında adların garantisi yoktur. NET ' in WSDL. exe aracı, varsayılan olarak, Svcutil. exe aracı tarafından oluşturulan WCF istemci sınıflarında adları eşleştirin. Özellikle, kullanılarak serileştirilmesi gereken sınıfların özelliklerinin adları, <xref:System.Xml.Serialization.XmlSerializer> Varsayılan olarak, WSDL. exe aracında bir durum olmayan Svcutil. exe aracı tarafından oluşturulan koddaki sonek özelliği verilirler.

## <a name="message-representation"></a>İleti temsili

ASP.NET Web Hizmetleri tarafından gönderilen ve alınan SOAP iletilerinin üstbilgileri özelleştirilebilir. Bir sınıf, <xref:System.Web.Services.Protocols.SoapHeader> üstbilginin yapısını tanımlamak için öğesinden türetilir ve sonra <xref:System.Web.Services.Protocols.SoapHeaderAttribute> üstbilginin varlığını göstermek için kullanılır.

```csharp
public class SomeProtocol : SoapHeader
{
     public long CurrentValue;
     public long Total;
}

[WebService]
public interface IEcho
{
     SomeProtocol ProtocolHeader
     {
      get;
     set;
     }

     [WebMethod]
     [SoapHeader("ProtocolHeader")]
     string PlaceOrders(PurchaseOrderType order);
}

public class Service: WebService, IEcho
{
     private SomeProtocol protocolHeader;

     public SomeProtocol ProtocolHeader
     {
         get
         {
              return this.protocolHeader;
         }

         set
         {
              this.protocolHeader = value;
         }
     }

     string PlaceOrders(PurchaseOrderType order)
     {
         long currentValue = this.protocolHeader.CurrentValue;
     }
}
```

WCF, <xref:System.ServiceModel.MessageContractAttribute> <xref:System.ServiceModel.MessageHeaderAttribute> <xref:System.ServiceModel.MessageBodyMemberAttribute> bir hizmet tarafından GÖNDERILEN ve alınan SOAP iletilerinin yapısını betimleyen,, ve özniteliklerini sağlar.

```csharp
[DataContract]
public class SomeProtocol
{
     [DataMember]
     public long CurrentValue;
     [DataMember]
     public long Total;
}

[DataContract]
public class Item
{
     [DataMember]
     public string ItemNumber;
     [DataMember]
     public decimal Quantity;
     [DataMember]
     public decimal UnitPrice;
}

[MessageContract]
public class ItemMessage
{
     [MessageHeader]
     public SomeProtocol ProtocolHeader;
     [MessageBody]
     public Item Content;
}

[ServiceContract]
public interface IItemService
{
     [OperationContract]
     public void DeliverItem(ItemMessage itemMessage);
}
```

Bu sözdizimi, iletilerin yapısının açık bir gösterimini verir, ancak iletilerin yapısı bir ASP.NET Web hizmeti kodu tarafından kapsanır. Ayrıca, ASP.NET sözdiziminde, ileti üstbilgileri hizmetin özellikleri olarak temsil edilir (örneğin, `ProtocolHeader` önceki örnekteki özelliği), WCF sözdiziminde, iletilerin özellikleri olarak daha doğru şekilde temsil edilir. Ayrıca, WCF, ileti üstbilgilerinin uç noktaların yapılandırmasına eklenmesine izin verir.

```xml
<service name="Service ">
     <endpoint
      address="EchoService"
      binding="basicHttpBinding"
      contract="IEchoService ">
      <headers>
      <dsig:X509Certificate
       xmlns:dsig="http://www.w3.org/2000/09/xmldsig#">
       ...
      </dsig:X509Certificate>
      </headers>
     </endpoint>
</service>
```

Bu seçenek, bir istemci veya hizmet için koddaki altyapısal protokol üst bilgilerine yönelik herhangi bir başvuruyu önlemenize olanak sağlar: uç noktanın nasıl yapılandırıldığına ilişkin olarak üstbilgiler iletilere eklenir.

## <a name="service-description"></a>Hizmet Açıklaması

ASP.NET bir Web hizmetinin. asmx dosyası için bir HTTP GET isteği verme, WSDL sorgusu, ASP.NET 'nin hizmeti betimleyen WSDL oluşturmasına neden olur. İsteğin yanıtı olarak WSDL döndürür.

ASP.NET 2,0, bir hizmetin Web Hizmetleri ile birlikte çalışabilirlik kuruluşunun (WS-ı) 1,1 temel profiliyle uyumlu olduğunu doğrulamak ve hizmetin WSDL 'ye uyumlu olduğunu bir talep eklemek mümkün hale gelir. Bu, `ConformsTo` özniteliğinin ve parametreleri kullanılarak yapılır `EmitConformanceClaims` <xref:System.Web.Services.WebServiceBindingAttribute> .

```csharp
[WebService(Namespace = "http://tempuri.org/")]
[WebServiceBinding(
     ConformsTo = WsiProfiles.BasicProfile1_1,
     EmitConformanceClaims=true)]
public interface IEcho
```

Bir hizmet için ASP.NET üreten WSDL özelleştirilebilir. Özelleştirmeler <xref:System.Web.Services.Description.ServiceDescriptionFormatExtension> , WSDL 'ye öğe eklemek için türetilmiş bir sınıfı oluşturularak yapılır.

IIS 51, 6,0 veya üzerinde barındırılan bir HTTP uç noktası ile bir WCF hizmetinin. svc dosyası için WSDL sorgu WSDL ile HTTP GET isteği verme, WCF 'nin hizmeti tanımlamasını sağlamak üzere WSDL ile yanıt vermesini sağlar. HttpGetEnabled, true olarak ayarlandıysa, bir .NET uygulaması içinde barındırılan bir hizmetin HTTP taban adresine WSDL ile bir HTTP GET isteği verilmesi aynı etkiye sahiptir.

Bununla birlikte, WCF Ayrıca bir hizmeti tanımlamaya yönelik oluşturduğu WSDL ile WS-MetadataExchange isteklerini de yanıtlar. ASP.NET Web Hizmetleri, WS-MetadataExchange istekleri için yerleşik desteğe sahip değildir.

WCF tarafından oluşturulacak WSDL, kapsamlı bir şekilde özelleştirilebilir. <xref:System.ServiceModel.Description.ServiceMetadataBehavior>Sınıfı, WSDL 'yi özelleştirmek için bazı tesisler sağlar. WCF Ayrıca, WSDL oluşturmak için yapılandırılabilir, ancak belirli bir URL 'de statik bir WSDL dosyası kullanmak yerine kullanılabilir.

```xml
<behaviors>
     <behavior name="DescriptionBehavior">
     <metadataPublishing
      enableMetadataExchange="true"
      enableGetWsdl="true"
      enableHelpPage="true"
      metadataLocation=
      "http://localhost/DerivativesCalculatorService/Service.WSDL"/>
     </behavior>
</behaviors>
```

## <a name="exception-handling"></a>Özel Durum İşleme

ASP.NET Web hizmetlerinde, işlenmemiş özel durumlar istemcilere SOAP hatası olarak döndürülür. Ayrıca, sınıfının örneklerini açıkça oluşturabilir <xref:System.Web.Services.Protocols.SoapException> ve istemciye ILETILEN SOAP hatasının içeriği üzerinde daha fazla denetime sahip olabilirsiniz.

WCF hizmetlerinde, önemli bilgilerin yanlışlıkla özel durumlar üzerinden gösterilmesini engellemek için işlenmemiş özel durumlar istemcilere SOAP hatası olarak döndürülmez. Bir yapılandırma ayarı, istemcilere hata ayıklama amacıyla geri döndürülen işlenmemiş özel durumları sağlamak için sağlanır.

İstemcilere SOAP hataları döndürmek için, genel tür <xref:System.ServiceModel.FaultException%601> olarak veri sözleşmesi türünü kullanarak genel türün örneklerini silebilirsiniz. Ayrıca, <xref:System.ServiceModel.FaultContractAttribute> bir işlemin sağlayabileceği hataları belirtmek için işlemlere öznitelikler ekleyebilirsiniz.

```csharp
[DataContract]
public class MathFault
{
     [DataMember]
     public string operation;
     [DataMember]
     public string problemType;
}

[ServiceContract]
public interface ICalculator
{
     [OperationContract]
     [FaultContract(typeof(MathFault))]
     int Divide(int n1, int n2);
}
```

Bunun yapılması, hizmet için WSDL 'de tanıtılmakta olan hataların, istemci programcılarının hangi hataların bir işlemden neden olduğunu tahmin etmesinin yanı sıra uygun catch deyimlerini yazabileceğini tahmin etmenize neden olur.

```csharp
try
{
     result = client.Divide(value1, value2);
}
catch (FaultException<MathFault> e)
{
 Console.WriteLine("FaultException<MathFault>: Math fault while doing "
  + e.Detail.operation
  + ". Problem: "
  + e.Detail.problemType);
}
```

## <a name="state-management"></a>Durum yönetimi

Bir ASP.NET Web hizmetini uygulamak için kullanılan sınıf öğesinden türetilebilir <xref:System.Web.Services.WebService> .

```csharp
public class Service : WebService, IEcho
{

 public string Echo(string input)
 {
  return input;
 }
}
```

Bu durumda, sınıfı <xref:System.Web.Services.WebService> bir nesneye erişmek için temel sınıfın ' Context özelliğini kullanmak üzere programlanabilir <xref:System.Web.HttpContext> . Nesnesi, uygulama <xref:System.Web.HttpContext> özelliği kullanılarak uygulama durumu bilgilerini güncelleştirmek ve almak için kullanılabilir ve oturum özelliğini kullanarak oturum durumu bilgilerini güncelleştirmek ve almak için kullanılabilir.

ASP.NET, uygulamasının oturum durumu bilgilerinin, aslında ' ın Session özelliği kullanılarak eriştiği konuma göre önemli bir denetim sağlar <xref:System.Web.HttpContext> . Tanımlama bilgilerinde, bir veritabanında, geçerli sunucu belleğinde veya belirlenen bir sunucunun belleğinde depolanabilir. Bu seçenek, hizmetin yapılandırma dosyasında yapılır.

WCF, durum yönetimi için Genişletilebilir nesneler sağlar. Genişletilebilir nesneler, uygulayan nesnelerdir <xref:System.ServiceModel.IExtensibleObject%601> . En önemli Genişletilebilir nesneler <xref:System.ServiceModel.ServiceHostBase> ve ' dir <xref:System.ServiceModel.InstanceContext> . `ServiceHostBase`aynı ana bilgisayardaki tüm hizmet türlerinin tümünün erişebileceği durumu korumanıza olanak sağlar, ancak `InstanceContext` aynı hizmet türü örneğinde çalışan herhangi bir kod tarafından erişilebilen durumu korumanıza olanak sağlar.

Burada, hizmet türü, `TradingSystem` <xref:System.ServiceModel.ServiceBehaviorAttribute> aynı WCF istemci örneğindeki tüm çağrıların hizmet türünün aynı örneğine yönlendirildiğini belirten bir içerir.

```csharp
[ServiceBehavior(InstanceContextMode = InstanceContextMode.PerSession)]
public class TradingSystem: ITradingService
```

Sınıfı, `DealData` bir hizmet türünün aynı örneğinde çalışan herhangi bir kod tarafından erişilebilen durumu tanımlar.

```csharp
internal class DealData: IExtension<InstanceContext>
{
 public string DealIdentifier = null;
 public Trade[] Trades = null;
}
```

Hizmet sözleşmesinin işlemlerinden birini uygulayan hizmet türünün kodunda, `DealData` hizmet türünün geçerli örneğinin durumuna bir durum nesnesi eklenir.

```csharp
string ITradingService.BeginDeal()
{
 string dealIdentifier = Guid.NewGuid().ToString();
 DealData state = new DealData(dealIdentifier);
 OperationContext.Current.InstanceContext.Extensions.Add(state);
 return dealIdentifier;
}
```

Bu durum nesnesi daha sonra hizmet sözleşmesinin işlemlerini uygulayan kod tarafından alınabilir ve değiştirilebilir.

```csharp
void ITradingService.AddTrade(Trade trade)
{
 DealData dealData =  OperationContext.Current.InstanceContext.Extensions.Find<DealData>();
 dealData.AddTrade(trade);
}
```

ASP.NET, sınıftaki durum bilgilerinin <xref:System.Web.HttpContext> gerçekten depolandığı, WCF 'nin en azından ilk sürümünde, Genişletilebilir nesnelerin depolandığı yerde denetim sunmayacak şekilde denetim sağlar. Bu, bir WCF hizmeti için ASP.NET uyumluluk modunu seçmenin en iyi nedenini oluşturur. Yapılandırılabilir durum yönetimi gerekliyse, ASP.NET uyumluluk modu için kullanılması, sınıfın tesislerini <xref:System.Web.HttpContext> ASP.net ' de kullanıldıkları şekilde kullanmanıza ve ayrıca sınıfı kullanılarak yönetilen durum bilgilerinin nerede depolandığını yapılandırmanıza olanak tanır <xref:System.Web.HttpContext> .

## <a name="security"></a>Güvenlik

ASP.NET Web hizmetlerini güvenli hale getirmek için seçenekler, herhangi bir IIS uygulamasının güvenliğini sağlamaya yönelik olanlardır. WCF uygulamaları yalnızca IIS içinde değil, ancak herhangi bir .NET yürütülebilir dosyası içinde barındırılabilecek olduğundan, WCF uygulamalarının güvenliğini sağlamaya yönelik seçenekler IIS 'nin tesislerden bağımsız yapılmalıdır. Ancak, ASP.NET Web Hizmetleri için sağlanan tesisler ASP.NET uyumluluk modunda çalışan WCF Hizmetleri için de kullanılabilir.

### <a name="security-authentication"></a>Güvenlik: kimlik doğrulaması

IIS, anonim erişimi veya çeşitli kimlik doğrulama modlarını seçebileceğiniz uygulamalara erişimi denetlemek için tesis sağlar: Windows kimlik doğrulaması, Özet kimlik doğrulaması, temel kimlik doğrulaması ve .NET Passport kimlik doğrulaması. Windows kimlik doğrulama seçeneği, ASP.NET Web hizmetlerine erişimi denetlemek için kullanılabilir. Ancak, WCF uygulamaları IIS içinde barındırılıyorsa, IIS 'nin uygulamaya anonim erişime izin verecek şekilde yapılandırılması gerekir, böylece kimlik doğrulaması, diğer çeşitli seçenekler arasında Windows kimlik doğrulamasını destekler. Yerleşik diğer seçenekler Kullanıcı adı belirteçleri, X. 509.440 sertifikaları, SAML belirteçleri ve CardSpace kartını içerir, ancak özel kimlik doğrulama mekanizmaları de tanımlanabilir.

### <a name="security-impersonation"></a>Güvenlik: kimliğe bürünme

ASP.NET, belirli bir kullanıcının kimliğine bürünmek için bir ASP.NET Web hizmeti 'nin veya geçerli istekle ilgili kimlik bilgilerinin sağlandığı bir kimlik öğesi sağlar. Bu öğe, ASP.NET uyumluluk modunda çalışan WCF uygulamalarında kimliğe bürünme yapılandırmak için kullanılabilir.

WCF yapılandırma sistemi, belirli bir kullanıcıyı kimliğe bürünmek üzere atamak için kendi kimlik öğesi sağlar. Ayrıca, WCF istemcileri ve Hizmetleri, kimliğe bürünme için bağımsız olarak yapılandırılabilir. İstemciler istekleri aktarırken geçerli kullanıcının kimliğine bürünmek üzere yapılandırılabilir.

```xml
<behaviors>
     <behavior name="DerivativesCalculatorClientBehavior">
      <clientCredentials>
      <windows allowedImpersonationLevel="Impersonation"/>
      </clientCredentials>
     </behavior>
</behaviors>
```

Hizmet işlemleri, geçerli istek ile hangi kullanıcının kimlik bilgilerinin sağlandığını taklit etmek üzere yapılandırılabilir.

```csharp
[OperationBehavior(Impersonation = ImpersonationOption.Required)]
public void Receive(Message input)
```

### <a name="security-authorization-using-access-control-lists"></a>Güvenlik: Access Control listelerini kullanarak yetkilendirme

Access Control listeleri (ACL 'Ler),. asmx dosyalarına erişimi kısıtlamak için kullanılabilir. Bununla birlikte, WCF. svc dosyalarındaki ACL 'Ler ASP.NET uyumluluk modu dışında yok sayılır.

### <a name="security-role-based-authorization"></a>Güvenlik: rol tabanlı yetkilendirme

IIS Windows kimlik doğrulaması seçeneği, kullanıcıların atandığı Windows gruplarını temel alan ASP.NET Web Hizmetleri için rol tabanlı yetkilendirmeyi kolaylaştırmak üzere ASP.NET yapılandırma dili tarafından sunulan yetkilendirme öğesiyle birlikte kullanılabilir. ASP.NET 2,0, daha genel rol tabanlı bir yetkilendirme mekanizması sunmuştur: rol sağlayıcıları.

Rol sağlayıcıları, bir kullanıcının atandığı roller hakkında temel bir arabirim uygulayan sınıflardır, ancak her bir rol sağlayıcısı bu bilgilerin farklı bir kaynaktan nasıl alınacağını bilir. ASP.NET 2,0, Microsoft SQL Server veritabanından rol atamalarını alan ve Windows Server 2003 Yetkilendirme Yöneticisi 'nden rol atamalarını alan bir rol sağlayıcısı sağlar.

Rol sağlayıcı mekanizması, WCF uygulaması da dahil olmak üzere herhangi bir .NET uygulamasında ASP.NET bağımsız olarak bağımsız olarak kullanılabilir. Bir WCF uygulaması için aşağıdaki örnek yapılandırma, bir ASP.NET rol sağlayıcısının kullanımını, ' nin tarafından seçilen bir seçenek olduğunu gösterir <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> .

```xml
<system.serviceModel>
     <services>
         <service name="Service.ResourceAccessServiceType"
             behaviorConfiguration="ServiceBehavior">
             <endpoint
              address="ResourceAccessService"
              binding="wsHttpBinding"
              contract="Service.IResourceAccessContract"/>
         </service>
     </services>
     <behaviors>
       <behavior name="ServiceBehavior">
       <serviceAuthorization principalPermissionMode="UseAspNetRoles"/>
      </behavior>
     </behaviors>
</system.serviceModel>
```

### <a name="security-claims-based-authorization"></a>Güvenlik: talep tabanlı yetkilendirme

WCF 'nin en önemli yeniliklerinden biri, talebe göre korumalı kaynaklara erişimi yetkilendirmek için tam destek sağlar. Talepler, örneğin, bir türü, bir sağ ve bir değer, bir sürücü lisansı olan bir tür içerir. Taşıyıcı hakkında bir talepler kümesi oluşturur ve bunlardan biri, taşıyıcının Doğum tarihidir. Bu talebin türü Doğum tarihidir, talebin değeri ise sürücünün Doğum tarihidir. Bir talebin, taşıyıcının bu sırada ne yapabileceğini belirtir. Sürücünün Doğum tarihi talebi söz konusu olduğunda, doğru sahip olur: sürücü söz konusu Doğum tarihine sahiptir ancak örneğin, bunu değiştirebilir. Roller bir talep türü olduğundan, talep tabanlı yetkilendirme rol tabanlı yetkilendirmeyi barındırır.

Talepler temelinde yetkilendirme, bir talep kümesi, işlemin erişim gereksinimleriyle karşılaştırılarak ve bu karşılaştırmanın sonucuna bağlı olarak, işleme erişim izni verirken veya reddettikten sonra yapılır. WCF 'de, özelliğine bir değer atayarak, talep tabanlı yetkilendirmeyi çalıştırmak için kullanılacak bir sınıf belirtebilirsiniz `ServiceAuthorizationManager` <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> .

```xml
<behaviors>
     <behavior name='ServiceBehavior'>
     <serviceAuthorization
     serviceAuthorizationManagerType=
                   'Service.AccessChecker, Service' />
     </behavior>
</behaviors>
```

Talep tabanlı yetkilendirmeyi çalıştırmak için kullanılan sınıflar <xref:System.ServiceModel.ServiceAuthorizationManager> , geçersiz kılmak için yalnızca bir yöntemi olan öğesinden türetilmelidir `AccessCheck()` . WCF, her bir hizmet işlemi çağrıldığında bu yöntemi çağırır ve <xref:System.ServiceModel.OperationContext> , özelliği içinde Kullanıcı için talepler içeren bir nesne sağlar `ServiceSecurityContext.AuthorizationContext` . WCF, kullanıcı hakkındaki talepleri, kullanıcının kimlik doğrulaması için verdiği herhangi bir güvenlik belirteciyle, bu taleplerin söz konusu işlem için yeterli olup olmadığını değerlendirme görevini atan bir kullanıcı hakkında bilgi veren çalışmalardır.

Bu WCF, her türlü güvenlik belirtecinin taleplerini otomatik olarak ayrıştırır. Bu, talebe dayalı olarak kimlik doğrulama mekanizmasından bağımsız olarak yetkilendirme kodu oluşturduğundan yüksek ölçüde önemli bir yeniliği oluşturur. Bunun aksine, ASP.NET içindeki ACL 'Leri veya rolleri kullanarak yetkilendirme, Windows kimlik doğrulamasına yakından bağlıdır.

### <a name="security-confidentiality"></a>Güvenlik: Gizlilik

ASP.NET Web hizmetleriyle değiştirilen iletilerin gizliliği, IIS içindeki uygulamayı Güvenli Köprü Metni Aktarım Protokolü (HTTPS) kullanacak şekilde yapılandırarak Aktarım düzeyinde olabilir. IIS içinde barındırılan WCF uygulamaları için de aynı işlem yapılabilir. Ancak, IIS dışında barındırılan WCF uygulamaları da güvenli bir aktarım protokolü kullanacak şekilde yapılandırılabilir. Daha önemli olan WCF uygulamaları, WS-Security protokolü kullanılarak, gönderilmeden önce iletilerin güvenliğini sağlamak için de yapılandırılabilir. WS-Security kullanarak yalnızca bir iletinin gövdesini güvenli hale getirmek, BT 'nin son hedefine ulaşmadan önce aracıların genelinde confidentially aktarılmasını sağlar.

## <a name="globalization"></a>Genelleştirme

ASP.NET yapılandırma dili, tek tek hizmetler için kültürü belirtmenize olanak tanır. WCF, ASP.NET uyumluluk modu dışında bu yapılandırma ayarını desteklemez. ASP.NET uyumluluk modunu kullanmayan bir WCF hizmetini yerelleştirmek için, hizmet türünü kültüre özgü Derlemelerle derleyin ve kültüre özgü her derleme için kültüre özgü ayrı uç noktalara sahip yapın.

## <a name="see-also"></a>Ayrıca bkz.

- [ASP.NET Web Hizmetlerini Amaç ve Kullanılan Standartları Temel Alarak WCF ile Karşılaştırma](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used.md)
