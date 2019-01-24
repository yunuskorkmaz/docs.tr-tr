---
title: ASP.NET Web Hizmetlerini Geliştirmeye Göre WCF ile Karşılaştırma
ms.date: 03/30/2017
ms.assetid: f362d00e-ce82-484f-9d4f-27e579d5c320
ms.openlocfilehash: 6bf9743410d3138efd5f3ea151b58f61e46ef683
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54496799"
---
# <a name="comparing-aspnet-web-services-to-wcf-based-on-development"></a>ASP.NET Web Hizmetlerini Geliştirmeye Göre WCF ile Karşılaştırma
Windows Communication Foundation (WCF) WCF programlanmış ve ASP.NET Web Hizmetleri gibi yapılandırılmış uygulamaların sağlar ve davranışlarını taklit etmek için ASP.NET uyumluluk modu seçeneği vardır. Aşağıdaki bölümlerde ASP.NET Web hizmetlerini karşılaştırın ve WCF ne hem teknolojiler kullanarak uygulama geliştirmek için gerekli olduğuna bağlı olarak.  
  
## <a name="data-representation"></a>Veri gösterimi  
 Bir Web hizmeti ASP.NET ile geliştirme genellikle hizmet kullanmaktır herhangi bir karmaşık veri türlerini tanımlama ile başlar. ASP.NET dayanır <xref:System.Xml.Serialization.XmlSerializer> iletilmesi için veya bir hizmet için XML .NET Framework türleri tarafından temsil edilen veri Çevir ve .NET Framework nesnelerini XML olarak alınan veriler çevir. ASP.NET hizmeti kullanmaktır karmaşık veri türlerini tanımlanmasını gerektirir tanımını .NET Framework sınıfları <xref:System.Xml.Serialization.XmlSerializer> XML gelen ve giden serileştirebiliyorsa. Bu tür sınıflar el ile yazılmış veya komut satırı XML şemaları/veri türleri desteği yardımcı programı kullanarak XML şema türlerinin tanımlarını üretilen XSD.exe'nin.  
  
 Ne zaman .NET Framework tanımlayan sınıflar bilmeniz gereken temel sorunların bir listesini verilmiştir <xref:System.Xml.Serialization.XmlSerializer> XML gelen ve giden serileştirebiliyorsa:  
  
-   Yalnızca ortak alanları ve .NET Framework nesnelerin özelliklerini, XML'e çevrilir.  
  
-   Koleksiyon sınıfları seri hale getirilemiyor XML'e sınıflar ya da uygularsanız <xref:System.Collections.IEnumerable> veya <xref:System.Collections.ICollection> arabirimi.  
  
-   Uygulayan sınıflar <xref:System.Collections.IDictionary> gibi arabirim <xref:System.Collections.Hashtable>, XML'e seri hale getirilemiyor.  
  
-   Çoğu öznitelik türlerini harika <xref:System.Xml.Serialization> ad alanı, bir .NET Framework sınıf ve üyelerine sınıfının örneklerini XML içinde nasıl gösterileceğini denetlemek için eklenebilir.  
  
 WCF uygulaması geliştirme de genellikle karmaşık tür tanımı ile başlar. WCF aynı .NET Framework türleri ASP.NET Web hizmetlerini kullanmak için yapılabilir.  
  
 WCF<xref:System.Runtime.Serialization.DataContractAttribute> ve <xref:System.Runtime.Serialization.DataMemberAttribute> türün örneklerinin içine XML ve hangi belirli alanlar veya tür özelliklerini seri hale getirilmesi için aşağıdaki örnek kodda gösterildiği gibi seri hale olduğunu belirtmek için .NET Framework türleri eklenebilir.  
  
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
  
 <xref:System.Runtime.Serialization.DataContractAttribute> Sıfır veya daha fazla türün alanlarına veya özelliklerine olması anlamına gelir serileştirildiği while <xref:System.Runtime.Serialization.DataMemberAttribute> belirli bir alan veya özellik serileştirilecek olduğunu gösterir. <xref:System.Runtime.Serialization.DataContractAttribute> Bir sınıf veya yapı için uygulanabilir. <xref:System.Runtime.Serialization.DataMemberAttribute> Bir alan veya özellik için uygulanabilir ve alanlar ve Özellikler öznitelik uygulandığı genel veya özel olabilir. Sahip türleri örneklerini <xref:System.Runtime.Serialization.DataContractAttribute> uygulanan WCF'de veri sözleşmeleri olarak bunları için başvurulur. XML olarak serileştirilme şeklini kullanarak <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
 Aşağıdakileri kullanarak arasındaki önemli farklar listesidir <xref:System.Runtime.Serialization.DataContractSerializer> ve kullanarak <xref:System.Xml.Serialization.XmlSerializer> ve çeşitli özniteliklerini <xref:System.Xml.Serialization> ad alanı.  
  
-   <xref:System.Xml.Serialization.XmlSerializer> Ve özniteliklerini <xref:System.Xml.Serialization> ad alanı, XML Şeması'nda tanımlanan herhangi bir geçerli türü .NET Framework türleriyle eşlemek olanak sağlamak için tasarlanmıştır ve bu nedenle sağlamaları için bir tür XML'de nasıl temsil edildiğini üzerinde kesin denetim. <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.DataContractAttribute> Ve <xref:System.Runtime.Serialization.DataMemberAttribute> türü XML'de nasıl temsil edildiğini üzerinde çok az bir denetim sağlar. Yalnızca ad alanları ve tür ve alanlarını veya XML ve alanlar ve Özellikler XML dosyasında göründükleri sıra özelliklerinde temsil etmek için kullanılan adları belirtebilirsiniz:  
  
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
  
     .NET türü temsil etmek için kullanılan XML yapısı hakkında diğer her şey belirlenir <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
-   Nasıl bir XML içinde temsil edilmesini türüdür kadar denetim vermeyerek seri hale getirme işlemi için son derece tahmin edilebilir hale <xref:System.Runtime.Serialization.DataContractSerializer>ve böylece iyileştirmek daha kolay. Tasarımını pratik bir yararı <xref:System.Runtime.Serialization.DataContractSerializer> daha iyi performans, yaklaşık olarak yüzde 10 oranında daha iyi performans.  
  
-   İle kullanmak için öznitelikler <xref:System.Xml.Serialization.XmlSerializer> hangi alanların veya özelliklerin türü XML serileştirilme şeklini ise göstermez <xref:System.Runtime.Serialization.DataMemberAttribute> ile kullanılmak üzere <xref:System.Runtime.Serialization.DataContractSerializer> hangi alanların veya özelliklerin serileştirilmiş açıkça gösterir. Dolayısıyla, veri sözleşmeleri, göndermek ve almak için bir uygulama olan verilerin yapısı hakkında açık anlaşmaları altındadır.  
  
-   <xref:System.Xml.Serialization.XmlSerializer> Yalnızca genel üyeleri bir .NET nesnesini XML'e, çevirebilir <xref:System.Runtime.Serialization.DataContractSerializer> nesnelerin üyelerini XML'e erişim değiştiricileri bu üyelerin bağımsız olarak çevirebilir.  
  
-   Türleri ortak olmayan üyeleri, XML'e seri hale getirmek için söz konusu kümelerdeki <xref:System.Runtime.Serialization.DataContractSerializer> daha az XML'e serileştirebiliyorsa .NET türleri çeşitli kısıtlamalar vardır. Özellikle, XML türlerini gibi çevirebilir <xref:System.Collections.Hashtable> uygulayan <xref:System.Collections.IDictionary> arabirimi. <xref:System.Runtime.Serialization.DataContractSerializer> Türünün tanımını değiştirin veya bunun için bir sarmalayıcı geliştirme gerek kalmadan tüm önceden mevcut olan .NET türüne XML örneklerini serileştirmek çok daha yüksektir.  
  
-   Başka bir sonucu <xref:System.Runtime.Serialization.DataContractSerializer> bir türün genel olmayan üyeleri erişebildiklerinden olan tam güven gerektirir ancak <xref:System.Xml.Serialization.XmlSerializer> desteklemez. Tam güven kodu erişim izni altında kodu yürüten kimlik bilgileri kullanılarak erişilebilecek bir makinedeki tüm kaynakların tam erişim sağlar. Tam olarak güvenilen kod makinenizde tüm kaynaklara erişir gibi bu seçeneği dikkatli kullanılmalıdır.  
  
-   <xref:System.Runtime.Serialization.DataContractSerializer> Bazı sürüm oluşturma desteği içerir:  
  
    -   <xref:System.Runtime.Serialization.DataMemberAttribute> Sahip bir <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> böylece uygulamaların olmasını sözleşmenin daha yeni sürümü izin verecek şekilde önceki sürümlerde, mevcut olmayan bir veri anlaşması yeni sürümlerine eklenen üyeler için false değeri atanabilir özelliği önceki sürümlerde işlemek kullanabilirsiniz.  
  
    -   Uygulama bir veri anlaşması sahip <xref:System.Runtime.Serialization.IExtensibleDataObject> arabirimi, bir izin verebilir <xref:System.Runtime.Serialization.DataContractSerializer> uygulamalar üzerinden bir veri anlaşması daha yeni sürümlerinde sözleşme önceki sürümleriyle tanımlanan üyeler geçirilecek.  
  
 Tüm farklılıklar da XML'e rağmen <xref:System.Xml.Serialization.XmlSerializer> serileştiren bir türü varsayılan olarak anlamı da XML'e aynıdır <xref:System.Runtime.Serialization.DataContractSerializer> ad alanı XML açıkça tanımlanmış için sağlanan bir türü seri hale getirir. Anlamsal olarak aynı XML tarafından öznitelikleri hem seri hale getiricileri genişletme ile kullanmak için aşağıdaki sınıf çevrilir <xref:System.Xml.Serialization.XmlSerializer> ve <xref:System.Runtime.Serialization.DataContractAttribute>:  
  
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
  
 Windows Yazılım Geliştirme Seti (SDK) adlı bir komut satırı aracı içerir [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). ASP.NET Web Hizmetleri ile kullanılan XSD.exe'nin aracını gibi Svcutil.exe XML şema .NET veri türlerinin tanımlarını oluşturabilir. Veri sözleşmeleri, türleridir <xref:System.Runtime.Serialization.DataContractSerializer> XML XML şeması tarafından tanımlanan biçimde gönderebilir; Aksi takdirde, bunlar serileştirme kullanmak için tasarlanmıştır <xref:System.Xml.Serialization.XmlSerializer>. Svcutil.exe ayrıca oluşturabileceği bir XML Şeması veri sözleşmelerden kullanarak kendi `dataContractOnly` geçin.  
  
> [!NOTE]
>  ASP.NET Web hizmetlerini kullanın ancak <xref:System.Xml.Serialization.XmlSerializer>ve WCF ASP.NET uyumluluk modunun ASP.NET Web hizmetlerini davranışını taklit eden WCF hizmetleri sağlar, ASP.NET uyumluluk seçeneğini kullanarak bir kısıtlamaz <xref:System.Xml.Serialization.XmlSerializer>. Bir kullanmaya devam edebilirsiniz <xref:System.Runtime.Serialization.DataContractSerializer> ASP.NET uyumluluk modunda çalışan hizmetleri ile.  
  
## <a name="service-development"></a>Hizmet geliştirme  
 ASP.NET kullanarak bir hizmeti geliştirmek için eklemek için her zamanki geçtiğine <xref:System.Web.Services.WebService> öznitelik bir sınıfa ve <xref:System.Web.Services.WebMethodAttribute> herhangi bir hizmet işlemlerini olacak bu sınıfı yöntemleri:  
  
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
  
 ASP.NET 2.0 kullanılmaya öznitelik ekleme seçeneğiniz <xref:System.Web.Services.WebService> ve <xref:System.Web.Services.WebMethodAttribute> bir arabirim yerine bir sınıf ve arabirim uygulamak için bir sınıf yazma:  
  
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
  
 Bu seçeneği kullanarak, tercih edilen, olmasını çünkü arabirimiyle <xref:System.Web.Services.WebService> özniteliği aynı sözleşme farklı şekillerde uygulayabilir, çeşitli sınıflarla yeniden kullanılabilir bir hizmet tarafından gerçekleştirilen işlemleri için bir sözleşmeyi oluşturur.  
  
 Bir WCF hizmeti bir veya daha fazla WCF bitiş noktalarını tanımlayarak sağlanır. Bir uç nokta bir adresi, bağlama ve hizmet sözleşmesi tarafından tanımlanır. Hizmet bulunduğu adresin tanımlar. Bağlama hizmeti ile iletişim kurma belirtir. Hizmet sözleşmesi, hizmet gerçekleştirebileceği işlemleri tanımlar.  
  
 Hizmet sözleşmesi genellikle ilk olarak ekleyerek tanımlanan <xref:System.ServiceModel.ServiceContractAttribute> ve <xref:System.ServiceModel.OperationContractAttribute> bir arabirim için:  
  
```csharp  
[ServiceContract]  
public interface IEcho  
{  
     [OperationContract]  
     string Echo(string input);  
}  
```  
  
 <xref:System.ServiceModel.ServiceContractAttribute> Arabirimi bir WCF hizmet sözleşmesini tanımlayan belirtir ve <xref:System.ServiceModel.OperationContractAttribute> , varsa, arabirimin yöntemlerini hizmet sözleşmesi işlemlerini tanımlayan gösterir.  
  
 Bir hizmet sözleşmesini tanımlandıktan sonra hizmet sözleşmesi tanımlandığı arabirimini uygulayan sınıf sağlayarak bir sınıfta uygulanır:  
  
```csharp  
public class Service : IEcho  
{  
    public string Echo(string input)  
    {  
       return input;  
    }  
}  
```  
  
 Bir hizmet sözleşmesini uygulayan bir sınıf, bir hizmet olarak WCF'de türüne adlandırılır.  
  
 Sonraki adım, bir adresi ve bir bağlama bir hizmet türü ile ilişkilendirin sağlamaktır. Bu, genellikle bir yapılandırma dosyasında, dosyanın doğrudan düzenleyerek veya WCF ile sağlanan bir yapılandırma Düzenleyicisi'ni kullanarak gerçekleştirilir. Bir yapılandırma dosyası örneği aşağıdadır.  
  
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
  
 Bağlama uygulamayla iletişim protokolleri belirtir. Aşağıdaki tabloda, sık kullanılan seçenekleri temsil eden sistem tarafından sağlanan bağlamalar listeler.  
  
|Ad|Amaç|  
|----------|-------------|  
|BasicHttpBinding|Web Hizmetleri ve temel güvenlik profili 1.0 ve 1.1 WS-BasicProfile destekleyen istemciler ile birlikte çalışabilirlik.|  
|WSHttpBinding|Web Hizmetleri ve desteği WS - istemcileri ile birlikte çalışabilirlik * protokolleri HTTP üzerinden.|  
|WSDualHttpBinding|Çift yönlü HTTP iletişimi, bir ilk ileti alıcısı doğrudan ilk göndereni yanıtlamak değil, ancak yanıt herhangi bir sayıda in conformity with WS - HTTP kullanarak bir süre iletebilen * protokoller.|  
|WSFederationBinding|Bir hizmeti kaynaklarına erişimi denetlenebilir, HTTP iletişimi bir açıkça tanımlanmış kimlik bilgisi sağlayıcısı tarafından verilen kimlik bilgilerini temel.|  
|NetTcpBinding|Bir ağ üzerinden WCF yazılım varlıklar arasında güvenli, güvenilir ve yüksek performanslı iletişim.|  
|NetNamedPipeBinding|WCF yazılım varlıkları aynı makinede arasındaki iletişimi güvenli, güvenilir ve yüksek performans.|  
|NetMsmqBinding|MSMQ kullanarak WCF yazılım varlıklar arasındaki iletişim.|  
|MsmqIntegrationBinding|Bir WCF yazılım varlık ve MSMQ kullanarak başka bir yazılım varlığı arasındaki iletişim.|  
|NetPeerTcpBinding|Windows Eşler arası ağ iletişimi kullanarak WCF yazılım varlıklar arasındaki iletişim.|  
  
 Sistem tarafından sağlanan bağlama <xref:System.ServiceModel.BasicHttpBinding>, ASP.NET Web Hizmetleri tarafından desteklenen protokolleri kümesi içerir.  
  
 Özel bağlamalar WCF uygulamaları için kolayca bağlama öğesi sınıflarının tekil protokollerin uygulamak için WCF kullanan bir koleksiyon olarak tanımlanır. Ek protokollerin temsil etmek için yeni bağlama öğeleri yazılabilir.  
  
 Hizmet türlerini iç davranışını davranışları adlı sınıflar ailesini özelliklerini kullanarak ayarlanabilir. Burada, <xref:System.ServiceModel.ServiceBehaviorAttribute> sınıfı hizmet türü birden çok iş parçacıklı değer olduğunu belirtmek için kullanılır.  
  
```csharp  
[ServiceBehavior(ConcurrencyMode=ConcurrencyMode.Multiple]  
public class DerivativesCalculatorServiceType: IDerivativesCalculator  
```  
  
 Bazı davranışları ister <xref:System.ServiceModel.ServiceBehaviorAttribute>, öznitelikler. Diğer yöneticiler ayarlamak için isteyeceği özelliklere sahip olanları uygulama yapılandırmasında değiştirilebilir.  
  
 Hizmet türlerini programlamada, sık kullanılan oluşuyor <xref:System.ServiceModel.OperationContext> sınıfı. Kendi statik <xref:System.ServiceModel.OperationContext.Current%2A> özelliği işleminin çalıştığı bağlamı bilgilerine erişim sağlar. <xref:System.ServiceModel.OperationContext> her ikisi için de benzer <xref:System.Web.HttpContext> ve <xref:System.EnterpriseServices.ContextUtil> sınıfları.  
  
## <a name="hosting"></a>Barındırma  
 ASP.NET Web Hizmetleri, bir sınıf kitaplık derlemesine derlenir. Hizmet dosyası adlı bir dosya uzantısı .asmx sahip ve içeren koşuluyla olan bir `@ WebService` hizmet ve onu bulunduğu bütünleştirilmiş kod için kod içeren sınıf tanımlayan yönergesi.  
  
```  
<%@ WebService Language="C#" Class="Service,ServiceAssembly" %>  
```  
  
 Internet Information Services (IIS) ASP.NET uygulama kökü hizmet dosyası kopyalanır ve derleme, uygulama kök \bin alt kopyalanır. Uygulama ardından Tekdüzen Kaynak Konum Belirleyicisi (URL) ' hizmet dosyasının uygulama kökü kullanılarak erişilebilir.  
  
 WCF hizmetlerinde IIS 5.1 veya 6.0, Windows İşlem Etkinleştirme Hizmeti (IIS 7. 0'da, bir parçası olarak sağlanan WAS) ve herhangi bir .NET uygulama içinde kolayca barındırılabilir. IIS 5.1 veya 6.0 hizmet barındırmak için hizmet iletişimleri Aktarım Protokolü olarak HTTP kullanmanız gerekir.  
  
 IIS 5.1, 6.0 veya WAS içinde bir hizmet ana bilgisayar için aşağıdaki adımları kullanın:  
  
1.  Hizmet türü bir sınıf kitaplık derlemesine içine derleyin.  
  
2.  .Svc uzantısına sahip bir hizmet dosyası oluşturma bir `@ ServiceHost` yönergesi hizmet türünü tanımlamak için:  
  
    ```  
    <%@ServiceHost language="c#" Service="MyService" %>  
    ```  
  
3.  Bir sanal dizin ve bu sanal dizine \bin alt derlemeye hizmet dosyasını kopyalayın.  
  
4.  Yapılandırma dosyasını sanal dizine kopyalayın ve bunu Web.config olarak adlandırın.  
  
 Uygulama daha sonra uygulama kökü hizmet dosyasında URL'si kullanılarak erişilebilir.  
  
 Bir .NET uygulamasından bir WCF Hizmeti barındırma için hizmet türü uygulama tarafından başvurulan bir sınıf kitaplık derlemesine derlemek ve konak hizmetini kullanarak uygulamayı programlama <xref:System.ServiceModel.ServiceHost> sınıfı. Gerekli temel programlama örneği verilmiştir:  
  
```csharp  
string httpBaseAddress = "http://www.contoso.com:8000/";  
string tcpBaseAddress = "net.tcp://www.contoso.com:8080/";  
  
Uri httpBaseAddressUri = new Uri(httpBaseAddress);  
Uri tcpBaseAddressUri = new Uri(tcpBaseAddress);  
  
Uri[] baseAdresses = new Uri[] {   
 httpBaseAddressUri,  
 tcpBaseAddressUri};  
  
using(ServiceHost host = new ServiceHost(  
typeof(Service), //"Service" is the name of the service type baseAdresses))  
{  
     host.Open();  
  
     […] //Wait to receive messages  
     host.Close();  
}  
```  
  
 Bu örnek, bir veya daha fazla aktarım protokolleri için adresleri oluşumunu nasıl belirtilen gösterir. bir <xref:System.ServiceModel.ServiceHost>. Bu adresler taban adresi adlandırılır.  
  
 Herhangi bir WCF Hizmeti uç noktası için sağlanan adresi, temel bir uç noktanın ana bilgisayar adresini göre adresidir. Konak her iletişim Aktarım Protokolü için bir temel adresine sahip olabilir. Önceki yapılandırma dosyasında örnek yapılandırmasında <xref:System.ServiceModel.BasicHttpBinding> HTTP uç noktası kullanımıyla ilgili Aktarım Protokolü bu nedenle, uç nokta adresini seçili `EchoService`, ana bilgisayarın HTTP temel adresi göre. Önceki örnekte konağın söz konusu olduğunda, HTTP temel adresi olduğundan `http://www.contoso.com:8000/`. IIS veya WAS içinde barındırılan bir hizmet için taban adresi hizmetin hizmet dosyası URL'sidir.  
  
 Yalnızca hizmetler IIS veya WAS ve hangi HTTP ile Aktarım Protokolü yalnızca, yapılandırılmış barındırılan WCF ASP.NET uyumluluk modu seçeneğini kullanmak için yapılabilir. Bu seçeneği etkinleştirmek için aşağıdaki adımları gerektirir.  
  
1.  Programcı eklemelisiniz <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> özniteliği için hizmet türü ve ASP.NET uyumluluk modunun izin verilen veya gerekli belirtin.  
  
    ```csharp  
    [System.ServiceModel.Activation.AspNetCompatibilityRequirements(  
          RequirementsMode=AspNetCompatbilityRequirementsMode.Require)]  
    public class DerivativesCalculatorServiceType: IDerivativesCalculator  
    ```  
  
2.  Yönetici, ASP.NET uyumluluk modunun kullanmak için uygulamayı yapılandırmanız gerekir.  
  
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
  
     WCF uygulamaları, kendi hizmet dosyalarda .svc yerine .asmx bir uzantısı olarak kullanmak için de yapılandırılabilir.  
  
    ```xml  
    <system.web>  
         <compilation>  
          <compilation debug="true">  
          <buildProviders>  
           <remove extension=".asmx"/>  
           <add extension=".asmx"   
            type="System.ServiceModel.ServiceBuildProvider,   
            Systemm.ServiceModel,   
            Version=3.0.0.0,   
            Culture=neutral,   
            PublicKeyToken=b77a5c561934e089" />  
          </buildProviders>  
          </compilation>  
         </compilation>  
    </system.web>  
    ```  
  
     Bu seçenek, WCF kullanmak için hizmet değiştirilirken .asmx hizmeti dosyaları URL'lerini kullanmak üzere yapılandırılmış istemciler değiştirmek zorunda kalmaktan kaydedebilirsiniz.  
  
## <a name="client-development"></a>İstemci geliştirme  
 ASP.NET Web Hizmetleri için istemcileri, giriş olarak .asmx dosyasının URL'sini sağlayan WSDL.exe komut satırı aracını kullanarak oluşturulur. WCF tarafından sağlanan karşılık gelen aracı [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Bu, bir kod modülü ile hizmet sözleşmesi tanımını ve bir WCF istemcisi sınıfının tanımını oluşturur. Ayrıca, hizmetin bağlamasını ve adresini içeren bir yapılandırma dosyası oluşturur.  
  
 Uzak bir hizmete istemcisini programlamada zaman uyumsuz bir modele göre program genellikle tavsiye edilir. Her zaman WSDL.exe araç tarafından oluşturulan kodu, bir zaman uyumlu hem de zaman uyumsuz bir desenin için varsayılan olarak sağlar. Tarafından oluşturulan kodu [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) için ya da bir desen girebilirsiniz. Bu, varsayılan olarak zaman uyumlu desenini sağlar. Aracı ile yürütülürse `/async` geçiş için zaman uyumsuz desen oluşturulan kodu sağlar.  
  
 ASP tarafından oluşturulan WCF istemci sınıfları adları bir garanti yoktur. Varsayılan olarak, NET WSDL.exe aracı Svcutil.exe araç tarafından oluşturulan WCF istemci sınıfları adlarında eşleştirin. Özellikle, özelliklerin sınıflarının adları olan kullanarak serileştirilecek <xref:System.Xml.Serialization.XmlSerializer> WSDL.exe aracı ile çalışması değil Svcutil.exe aracı tarafından oluşturulan kodu soneki özelliği varsayılan olarak, verilen olan.  
  
## <a name="message-representation"></a>İleti gösterimi  
 ASP.NET Web Hizmetleri tarafından alınan SOAP iletilerinin üstbilgisi özelleştirilebilir. Öğesinden türetilen bir sınıf <xref:System.Web.Services.Protocols.SoapHeader> başlık yapısını tanımlamak için ve ardından <xref:System.Web.Services.Protocols.SoapHeaderAttribute> üst bilgisi varlığını göstermek için kullanılır.  
  
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
  
 WCF öznitelikleri sağlar <xref:System.ServiceModel.MessageContractAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute>, ve <xref:System.ServiceModel.MessageBodyMemberAttribute> SOAP iletilerini bir hizmeti tarafından gönderilen ve alınan yapısını tanımlamak için.  
  
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
public class ItemMesage  
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
  
 İletileri yapısı, bir ASP.NET Web hizmeti kodunu tarafından kapsanan ise bu söz dizimi yapısı iletileri, açık bir temsilini verir. Ayrıca, ASP.NET sözdiziminde, ileti üstbilgileri hizmet özellikleri olarak gibi gösterilir `ProtocolHeader` önceki örnekte, özellik daha doğru bir şekilde iletileri özellikleri olarak gösterilen WCF sözdiziminde ise. Ayrıca, WCF uç noktaları yapılandırmanız için eklenecek ileti üstbilgileri sağlar.  
  
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
  
 Seçenek, herhangi bir istemci veya hizmet için kodunda altyapısal protokol üstbilgileri başvuru kaçınmak olanak tanır: uç nokta nasıl yapılandırıldığını nedeniyle ileti üstbilgileri eklenir.  
  
## <a name="service-description"></a>Hizmet Açıklaması  
 WSDL sorgu ile bir ASP.NET Web hizmetinin .asmx dosyası için bir HTTP GET isteği verme, WSDL hizmet oluşturmak ASP.NET neden olur. Bunu döndüren WSDL isteğe yanıt olarak.  
  
 ASP.NET 2.0 yapılan bu hizmet Web Hizmetleri birlikte çalışabilirlik kuruluşun Basic Profile 1.1 ile uyumlu olduğunu doğrulamak olası (WS-ı) ve hizmet içinde WSDL uyumlu bir talep eklemek için. Diğer bir deyişle bitti kullanarak `ConformsTo` ve `EmitConformanceClaims` parametrelerinin <xref:System.Web.Services.WebServiceBindingAttribute> özniteliği.  
  
```csharp  
[WebService(Namespace = "http://tempuri.org/")]  
[WebServiceBinding(  
     ConformsTo = WsiProfiles.BasicProfile1_1,  
     EmitConformanceClaims=true)]  
public interface IEcho  
```  
  
 ASP.NET, bir hizmet için üretir. WSDL özelleştirilebilir. Özelleştirmeleri, türetilmiş sınıf oluşturarak yapılır <xref:System.Web.Services.Description.ServiceDescriptionFormatExtension> için WSDL öğeleri eklemek için.  
  
 IIS 51 içinde barındırılan bir HTTP uç noktası ile ' % s'sorgu WSDL .svc dosyasının bir WCF Hizmeti ile bir HTTP GET isteği verme, 6.0 veya WAS'ta WCF hizmet WSDL ile yanıt neden olur. Bir .NET uygulamasında barındırılan bir hizmete HTTP temel adresine WSDL sorgu ile bir HTTP GET isteği veren aynı etkiye sahiptir de ayarlanmışsa true.  
  
 Ancak, WCF Ayrıca, bir hizmet oluşturduğu WSDL WS-MetadataExchange isteklerine yanıt verir. ASP.NET Web hizmetlerini WS-MetadataExchange istekleri için yerleşik destek yok.  
  
 WCF oluşturur WSDL kapsamlı olarak özelleştirilebilir. <xref:System.ServiceModel.Description.ServiceMetadataBehavior> Sınıfı WSDL özelleştirmeye yönelik bazı özellikleri sağlar. WCF WSDL oluşturulmayacağını, ancak bunun yerine belirtilen URL'de statik bir WSDL dosyasını kullanmak için de yapılandırılabilir.  
  
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
 ASP.NET Web Hizmetleri, işlenmemiş özel durumlar, SOAP hataları istemcilere döndürülür. Örneklerini de açıkça oluşturabilecek <xref:System.Web.Services.Protocols.SoapException> sınıfı ve istemciye gönderilen bir SOAP hatası içeriği hakkında daha fazla denetime sahip.  
  
 WCF hizmetleri, işlenmemiş özel durumlar istemcilere hassas bilgiler özel durumların yanlışlıkla yararlanılmasını önlemek için SOAP hataları olarak döndürülmez. Bir yapılandırma ayarı, hata ayıklama amacıyla, istemcilere döndürülen özel durum işlenmemiş için sağlanmıştır.  
  
 SOAP hataları istemcilere dönmek için genel türün örneklerini oluşturabilecek <xref:System.ServiceModel.FaultException%601>kullanarak veri anlaşması türü olarak genel tür. Ayrıca ekleyebilirsiniz <xref:System.ServiceModel.FaultContractAttribute> öznitelikleri, işlemleri bir işlem yield hataları belirlemek için.  
  
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
  
 Olası hataları sonuçlarında hizmeti için WSDL içinde tanıtılan şekilde yaptığını, hangi hataların öngörmek programcılar rotasyonunun bir işlemden neden ve uygun catch deyimleri yazma.  
  
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
  
## <a name="state-management"></a>Durum Yönetimi  
 Bir ASP.NET Web hizmeti uygulamak için kullanılan sınıfı türetilen <xref:System.Web.Services.WebService>.  
  
```csharp  
public class Service : WebService, IEcho  
{  
  
 public string Echo(string input)  
 {  
  return input;  
 }  
}  
```  
  
 Bu durumda, sınıf kullanılacak programlanabilir <xref:System.Web.Services.WebService> erişmek için sınıfın bağlam özelliğini temel bir <xref:System.Web.HttpContext> nesne. <xref:System.Web.HttpContext> Nesnesi olabilir güncelleştirme ve kendi uygulama özelliğini kullanarak uygulama durum bilgilerini almak için kullanılan ve güncelleştirme ve kendi oturumu özelliğini kullanarak oturum durumu bilgilerini almak için kullanılabilir.  
  
 ASP.NET, burada oturum durum bilgileri oturumu özelliği kullanılarak önemli ölçüde denetim sağlar <xref:System.Web.HttpContext> gerçekten depolanır. Tanımlama bilgileri, bir veritabanı, geçerli sunucu belleği veya atanmış bir sunucu belleği depolanabilir. Seçim hizmet yapılandırma dosyasında yapılır.  
  
 WCF genişletilebilen nesneler için durum yönetimi sağlar. Genişletilebilen nesneler olan uygulayan nesneler <xref:System.ServiceModel.IExtensibleObject%601>. En önemli Genişletilebilir nesneler <xref:System.ServiceModel.ServiceHostBase> ve <xref:System.ServiceModel.InstanceContext>. `ServiceHostBase` tüm hizmet örneklerinin türleri, aynı ana bilgisayarda durumu erişebilir, tutmanıza olanak sağlayan while `InstanceContext` içinde bir hizmet türünün aynı örneğini çalıştıran herhangi bir kod tarafından erişilebilir durumda tutmanıza olanak sağlar.  
  
 Burada, hizmet türü `TradingSystem`, sahip bir <xref:System.ServiceModel.ServiceBehaviorAttribute> belirten tüm çağrıların aynı WCF istemci örneğinin aynı hizmet türü örneğine yönlendirilir.  
  
```csharp  
[ServiceBehavior(InstanceContextMode = InstanceContextMode.PerSession)]  
public class TradingSystem: ITradingService  
```  
  
 Sınıf `DealData`, bir hizmet türünün aynı örneğinde çalışan herhangi bir kod tarafından erişilebilecek bir durum tanımlar.  
  
```csharp  
internal class DealData: IExtension<InstanceContext>  
{  
 public string DealIdentifier = null;  
 public Trade[] Trades = null;  
}  
```  
  
 Hizmet türünün hizmet sözleşmesinin işlemlerden uygulayan kod bir `DealData` durum nesnesi, geçerli hizmet türü örneği durumuna eklenir.  
  
```csharp  
string ITradingService.BeginDeal()  
{  
 string dealIdentifier = Guid.NewGuid().ToString();  
 DealData state = new DealData(dealIdentifier);  
 OperationContext.Current.InstanceContext.Extensions.Add(state);  
 return dealIdentifier;  
}  
```  
  
 Bu durum nesnesi alınır ve başka bir hizmet sözleşme işlemleri uygulayan kodu tarafından değiştirildi.  
  
```csharp  
void ITradingService.AddTrade(Trade trade)  
{  
 DealData dealData =  OperationContext.Current.InstanceContext.Extensions.Find<DealData>();  
 dealData.AddTrade(trade);  
}  
```  
  
 ASP.NET üzerinde denetim sağlar. burada bilgileri durum <xref:System.Web.HttpContext> sınıfı gerçekten depolanan, WCF, en az ilk sürümde genişletilebilen nesneler depolandığı üzerinde hiçbir denetim sağlar. Bir WCF hizmeti için ASP.NET uyumluluk modunun seçmeye yönelik en iyi nedeni oluşturur. Yapılandırılabilir durum yönetimi, kesinlik temelli sonra için ASP.NET uyumluluk modunun edilmesiyle akreditasyonlu kullanmanıza olanak verir <xref:System.Web.HttpContext> sınıf tam olarak, ASP.NET ve yapılandırmak için kullanılabilir olduğu durum kullanılarakyönetilenbilgileri<xref:System.Web.HttpContext> sınıfı depolanır.  
  
## <a name="security"></a>Güvenlik  
 ASP.NET Web hizmetlerinin güvenliğini sağlamak için seçenekleri herhangi bir IIS uygulama güvenliğini sağlamak için olanlardır. WCF uygulamaları barındırılabilir, yalnızca IIS içinde aynı zamanda herhangi bir .NET yürütülebilir dosya içinde olduğundan, WCF uygulamalarının güvenliğini sağlama seçenekleri IIS akreditasyonlu bağımsız olarak yapılmalıdır. Ancak, ASP.NET Web Hizmetleri için sağlanan özellikleri de ASP.NET uyumluluk modunda çalışan WCF hizmetleri için kullanılabilir.  
  
### <a name="security-authentication"></a>Güvenlik: Kimlik doğrulaması  
 IIS tarafından anonim erişim veya kimlik doğrulama modları çeşitli seçebilirsiniz uygulamalara erişimi denetlemek için olanakları sağlar: Windows kimlik doğrulamasını, Özet kimlik doğrulaması, temel kimlik doğrulaması ve .NET Passport kimlik doğrulaması. ASP.NET Web hizmetlerini erişimi denetlemek için Windows kimlik doğrulaması seçeneği kullanılabilir. Ancak, WCF uygulamaları IIS içinde barındırıldığında, söz konusu kimlik doğrulamasını çeşitli seçenekler arasında Windows kimlik doğrulamasını destekleyen WCF kendisi tarafından yönetilebilmesi için uygulama anonim erişime izin vermek için IIS yapılandırılmalıdır. Kullanıcı adı belirteçleri, X.509 sertifikaları, SAML belirteçlerini ve CardSpace kart yerleşik diğer seçenekleri içerir, ancak özel kimlik doğrulama mekanizmaları da tanımlanabilir.  
  
### <a name="security-impersonation"></a>Güvenlik: Kimliğe bürünme  
 ASP.NET, ASP.NET Web hizmeti, belirli bir kullanıcının kimliğine bürünmesine yapılabilir veya hangi kullanıcının kimlik bilgilerinin geçerli istekle birlikte sağlanan bir kimlik öğesi sağlar. Bu öğe, kimliğe bürünme ASP.NET uyumluluk modunda çalışan WCF uygulamaları yapılandırmak için kullanılabilir.  
  
 WCF yapılandırma sistemi, belirli bir kullanıcının kimliğine bürünmek üzere atamak için kendi kimlik öğesi sağlar. Ayrıca, WCF istemciler ve hizmetler bağımsız olarak kimliğe bürünme için yapılandırılabilir. İstemci isteklerini iletebileceği, geçerli kullanıcının kimliğine bürünmek için yapılandırılabilir.  
  
```xml  
<behaviors>  
     <behavior name="DerivativesCalculatorClientBehavior">  
      <clientCredentials>  
      <windows allowedImpersonationLevel="Impersonation"/>  
      </clientCredentials>  
     </behavior>  
</behaviors>  
```  
  
 Hizmet işlemleri, hangi kullanıcının kimlik bilgilerinin geçerli istekle birlikte sağlanan kimliğine bürünmek için yapılandırılabilir.  
  
```csharp  
[OperationBehavior(Impersonation = ImpersonationOption.Required)]  
public void Receive(Message input)  
```  
  
### <a name="security-authorization-using-access-control-lists"></a>Güvenlik: Yetkilendirme, erişim denetim listeleri kullanma  
 Erişim denetim listeleri (ACL'ler) .asmx dosyalara erişimi kısıtlamak için kullanılabilir. Ancak, WCF .svc dosyalarını ACL'lerin dışında ASP.NET uyumluluk modunda yoksayılır.  
  
### <a name="security-role-based-authorization"></a>Güvenlik: Rol tabanlı yetkilendirme  
 IIS Windows kimlik doğrulaması seçeneği birlikte ASP.NET yapılandırma dil tarafından sağlanan yetkilendirme öğesi ile kullanıcılara atanmış olan Windows gruplarını temel alan bir ASP.NET Web Hizmetleri için rol tabanlı yetkilendirme kolaylaştırmak için kullanılabilir . ASP.NET 2.0 kullanılmaya daha genel bir rol tabanlı yetkilendirme mekanizması: rol sağlayıcıları.  
  
 Rol sağlayıcıları tamamı enquiring kendisine atanmış bir kullanıcı rolleri hakkında temel bir arabirim uygular, ancak her rol sağlayıcısını farklı bir kaynaktan bu bilgileri almak nasıl bilir sınıflardır. ASP.NET 2.0, rol atamaları, Windows Server 2003 Yetkilendirme Yöneticisi'nden alabileceğiniz bir Microsoft SQL Server veritabanı ve başka bir rol atamaları alabileceğiniz bir rol sağlayıcısı sağlar.  
  
 Rol sağlayıcı mekanizması gerçekten WCF uygulaması da dahil olmak üzere bir .NET uygulamasında ASP.NET bağımsız olarak kullanılabilir. WCF uygulaması için aşağıdaki örnek yapılandırma nasıl bir ASP.NET rol sağlayıcıyı kullanımı yoluyla bir seçeneğe gösterilir <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>.  
  
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
  
### <a name="security-claims-based-authorization"></a>Güvenlik: Beyana Dayalı Yetkilendirme  
 WCF en önemli yeniliklerden taleplere göre korumalı kaynaklara erişimi yetkilendirmek için kapsamlı desteklemesidir. Talep türü, bir hak ve bir değer, bir sürücü lisans, örneğin oluşur. Doğum tarihi taşıyıcı'nın biri olan taşıyıcı hakkında talepler kümesi kolaylaştırır. Talep değeri sürücünün doğum tarihi olsa da bu talebi doğum tarihi, türüdür. Bir talep üzerinde taşıyıcı confers sağ taşıyıcı talebin değer ile neler yapabileceğinizi belirtir. Doğum tarihi sürücünün talep söz konusu olduğunda, sağ mülkü olduğundan: sürücü doğum tarihi ancak, örneğin yükleyemediği sahip, üzerinde değişiklik. Beyana dayalı yetkilendirme, rol talep türü olduğundan rol tabanlı yetkilendirme barındırır.  
  
 Taleplere göre yetkilendirme Karşılaştırma işleminin ve bu karşılaştırma sonucunu bağlı olarak erişim gereksinimlerini için talepler kümesi vererek ya da işlemi erişimi reddetmeden gerçekleştirilir. WCF'de, beyana dayalı yetkilendirme, bir değere atayarak yeniden çalıştırmak için kullanılacak bir sınıf belirtebilirsiniz `ServiceAuthorizationManager` özelliği <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>.  
  
```xml  
<behaviors>  
     <behavior name='ServiceBehavior'>  
     <serviceAuthorization   
     serviceAuthorizationManagerType=  
                   'Service.AccessChecker, Service' />  
     </behavior>  
</behaviors>  
```  
  
 Beyana dayalı yetkilendirme çalıştırmak için kullanılan sınıfların türetilmesi gereken <xref:System.ServiceModel.ServiceAuthorizationManager>, geçersiz kılmak için yalnızca bir yöntem olan `AccessCheck()`. WCF hizmeti bir işlem çağrılır ve sağlar, yöntemini çağırır bir <xref:System.ServiceModel.OperationContext> kullanıcı için talepleri olan bir nesne içinde kendi `ServiceSecurityContext.AuthorizationContext` özelliği. WCF çalışır, hangi güvenlik belirteci kullanıcı hakkında talepleri derleyerek bırakan kimlik doğrulaması için belirtilen kullanıcı bu talepleri söz konusu işlem için yeterli olup olmadığını değerlendirmek, görev.  
  
 Kimlik doğrulama mekanizması tamamen bağımsız taleplere göre yetkilendirme kodunu kolaylaştırır WCF güvenlik herhangi bir türden otomatik olarak talep çeviren son derece önemli bir yenilik belirteci olmasıdır. Aksine, ASP.NET'te ACL'leri ya da rolleri kullanarak yetkilendirme için Windows kimlik doğrulaması yakından bağlanır.  
  
### <a name="security-confidentiality"></a>Güvenlik: Gizliliği  
 ASP.NET Web Hizmetleri ile değiştirilen iletilerin gizliliğini taşıma düzeyinde IIS içinde uygulamayı Güvenli Köprü Metni Aktarım Protokolü (HTTPS) kullanacak şekilde yapılandırarak güvence altına alınabilir. Aynı içinde IIS barındırılan WCF uygulamaları için yapılabilir. Ancak, dışında IIS barındırılan WCF uygulamaları güvenli aktarım protokolünü kullanmak için de yapılandırılabilir. Daha da önemlisi, WCF uygulamaları, bunlar, WS-güvenlik protokolü kullanarak taşınacağını önce iletileri güvenli hale getirmek için de yapılandırılabilir. WS-güvenlik kullanarak ileti gövdesi güvenli hale getirme aracılar son hedefine ulaşmadan önce ilkemiz aktarılan izin verir.  
  
## <a name="globalization"></a>Genelleştirme  
 ASP.NET yapılandırma dil, tek tek Hizmetleri için kullanılacak kültürü belirtmenize olanak sağlar. WCF ASP.NET uyumluluk modunda, yapılandırma ayarı dışında desteklemez. ASP.NET uyumluluk modunun kullanılmaması bir WCF Hizmeti yerelleştirmek için hizmet türü kültüre özgü derlemeler içine derleyin ve her bir kültüre özgü derleme için ayrı kültüre özgü uç sahip.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ASP.NET Web Hizmetlerini Amaç ve Kullanılan Standartları Temel Alarak WCF ile Karşılaştırma](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used.md)
