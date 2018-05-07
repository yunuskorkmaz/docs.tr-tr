---
title: ASP.NET Web Hizmetlerini Geliştirmeye Göre WCF ile Karşılaştırma
ms.date: 03/30/2017
ms.assetid: f362d00e-ce82-484f-9d4f-27e579d5c320
ms.openlocfilehash: fcf2d204d9d59a29024ff09d92be2a7b9339fce9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="comparing-aspnet-web-services-to-wcf-based-on-development"></a>ASP.NET Web Hizmetlerini Geliştirmeye Göre WCF ile Karşılaştırma
Windows Communication Foundation (WCF) programlanmış ve ASP.NET Web Hizmetleri gibi yapılandırılması WCF uygulamaları etkinleştirmek ve davranışlarını taklit etmek için bir ASP.NET uyumluluk modu seçeneğine sahiptir. Aşağıdaki bölümlerde ASP.NET Web Hizmetleri karşılaştırın ve WCF ne iki teknolojiyi kullanarak uygulamaları geliştirmek için gerekli olduğuna bağlı olarak.  
  
## <a name="data-representation"></a>Veri temsili  
 ASP.NET Web hizmetiyle geliştirme genellikle hizmet kullanmaktır herhangi karmaşık veri türlerini tanımlama ile başlar. ASP.NET kullanır <xref:System.Xml.Serialization.XmlSerializer> iletim ya da hizmet için XML ve .NET Framework türleri tarafından gösterilen veriler Çevir ve .NET Framework nesnelerini XML olarak alınan veriler çevir. ASP.NET hizmeti kullanmaktır karmaşık veri türlerini tanımlama gerektiren .NET Framework'ün tanımı sınıfları <xref:System.Xml.Serialization.XmlSerializer> XML gelen ve giden seri hale getirebilir. Bu tür sınıflar el ile yazılmış veya komut satırı XML şemaları/veri türleri destek yardımcı programı kullanarak XML şemasındaki türlerinin tanımlarını üretilen XSD.exe'nin.  
  
 Ne zaman .NET Framework tanımlayan sınıflar bilmeniz anahtar sorunların bir listesi aşağıda verilmiştir <xref:System.Xml.Serialization.XmlSerializer> XML gelen ve giden seri hale getirebilir:  
  
-   Yalnızca genel alanlar ve .NET Framework nesnelerin özelliklerini XML çevrilir.  
  
-   Koleksiyon sınıfları örneklerini hale getirilebilir XML sınıflar ya da uygularsanız <xref:System.Collections.IEnumerable> veya <xref:System.Collections.ICollection> arabirimi.  
  
-   Sınıfları uygulayan <xref:System.Collections.IDictionary> gibi arabirim <xref:System.Collections.Hashtable>, XML'de serileştirilir.  
  
-   Çoğu öznitelik türlerinde mükemmel <xref:System.Xml.Serialization> ad alanı .NET Framework sınıf ve üyeleri sınıfın örnekleri, XML'de nasıl temsil edildiğini denetlemek için eklenebilir.  
  
 WCF uygulaması geliştirme de genellikle karmaşık türler tanımıyla başlar. ASP.NET Web Hizmetleri olarak aynı .NET Framework türlerini kullanmak için WCF yapılabilir.  
  
 WCF<xref:System.Runtime.Serialization.DataContractAttribute> ve <xref:System.Runtime.Serialization.DataMemberAttribute> türdeki örneklerin XML ve hangi belirli alanlar veya türünün özelliklerini serileştirilmesi için aşağıdaki örnek kodda gösterildiği gibi olduğundan seri hale olduğunu belirtmek için .NET Framework türleri eklenebilir.  
  
```  
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
  
 <xref:System.Runtime.Serialization.DataContractAttribute> Sıfır veya daha fazla bir tür alanları veya özellikler olmak anlamına gelir serileştirildiği while <xref:System.Runtime.Serialization.DataMemberAttribute> belirli bir alan veya özelliği seri hale olduğunu gösterir. <xref:System.Runtime.Serialization.DataContractAttribute> Bir sınıf veya yapı uygulanabilir. <xref:System.Runtime.Serialization.DataMemberAttribute> Bir alan veya bir özellik için uygulanabilir ve ortak veya özel alanlar ve öznitelik uygulanan özellikler olabilir. Türleri örneklerini <xref:System.Runtime.Serialization.DataContractAttribute> uygulanan içinde WCF veri sözleşmeleri gibi bunları olarak denir. XML'de serileştirilir kullanarak <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
 Aşağıdaki kullanımı arasındaki önemli farklılıkları listesidir <xref:System.Runtime.Serialization.DataContractSerializer> ve kullanarak <xref:System.Xml.Serialization.XmlSerializer> ve çeşitli özniteliklerini <xref:System.Xml.Serialization> ad alanı.  
  
-   <xref:System.Xml.Serialization.XmlSerializer> Ve özniteliklerini <xref:System.Xml.Serialization> ad alanı .NET Framework türleri XML Şeması'nda tanımlanan herhangi bir geçerli türüne eşlenir olanak tanımak için tasarlanmıştır ve bu nedenle sağlarlar türü XML'de nasıl temsil üzerinden çok kesin bir denetim için. <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.DataContractAttribute> Ve <xref:System.Runtime.Serialization.DataMemberAttribute> bir türü XML'de nasıl temsil üzerinde çok az denetim sağlar. Ad alanları ve türü ve alanlar veya XML ve alanlar ve Özellikler XML'de görünme sırasını özelliklerinde temsil etmek için kullanılan adları yalnızca belirtebilirsiniz:  
  
    ```  
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
  
     Tarafından belirlenen şey .NET türü temsil etmek için kullanılan XML yapısı hakkında <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
-   Nasıl bir XML dosyasında gösterilemeyecek kadar türüdür kadar denetim vermeyerek seri hale getirme işlemi için yüksek oranda tahmin edilebilir hale <xref:System.Runtime.Serialization.DataContractSerializer>ve böylelikle, en iyi duruma getirmek daha kolay. Tasarımını pratik bir yararı <xref:System.Runtime.Serialization.DataContractSerializer> daha iyi performans, yaklaşık olarak yüzde onluk daha iyi performans.  
  
-   Öznitelikleri ile kullanılmak üzere <xref:System.Xml.Serialization.XmlSerializer> hangi alanların ya da türünün özelliklerini XML sıralanır ancak göstermiyor <xref:System.Runtime.Serialization.DataMemberAttribute> ile kullanılmak üzere <xref:System.Runtime.Serialization.DataContractSerializer> açıkça hangi alanların ya da özellikleri seri gösterir. Bu nedenle, veri sözleşmeleri göndermek ve almak için bir uygulama olan verileri yapısı hakkında açık sözleşmeleri altındadır.  
  
-   <xref:System.Xml.Serialization.XmlSerializer> Yalnızca Genel üyeler .NET nesnesinin XML çevirebilir <xref:System.Runtime.Serialization.DataContractSerializer> nesneleri üyeleri bu üyeler erişim değiştiricileri bağımsız olarak XML çevirebilir.  
  
-   XML ortak olmayan üyeler türleri serileştirmek çalışabilme gruplarındaki sonucu olarak <xref:System.Runtime.Serialization.DataContractSerializer> çeşitli XML serileştirebilen .NET türleri üzerinde daha az kısıtlamaları vardır. Özellikle, XML türleri gibi içine çevirebilir <xref:System.Collections.Hashtable> uygulayan <xref:System.Collections.IDictionary> arabirimi. <xref:System.Runtime.Serialization.DataContractSerializer> Türü tanımını değiştirin ya da bir sarmalayıcı için geliştirme gerek kalmadan XML halinde önceden var olan tüm .NET türünün örneklerini serileştirmek çok daha yüksektir.  
  
-   Başka bir sonucu <xref:System.Runtime.Serialization.DataContractSerializer> bir türün genel olmayan üyeleri erişebildiklerinden olduğundan tam güven gerektirir ancak <xref:System.Xml.Serialization.XmlSerializer> desteklemez. Tam güven kodu erişim izni altında kod yürütüyor kimlik bilgileri kullanılarak erişilebilir bir makine tüm kaynaklara tam erişim sağlar. Bu seçenek tam olarak güvenilen kod makinenizde tüm kaynakları erişir gibi dikkatli kullanılmalıdır.  
  
-   <xref:System.Runtime.Serialization.DataContractSerializer> Sürüm oluşturma için bazı destek içerir:  
  
    -   <xref:System.Runtime.Serialization.DataMemberAttribute> Sahip bir <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> false değeri, böylece uygulamaların olmasını sözleşme daha yeni sürümü ile izin verecek şekilde bir veri Sözleşmesi'nın önceki sürümlerinde, mevcut olmayan yeni sürümlerine eklenen üyeler için atanabilir özelliği önceki sürümlerde işlemek kullanabilirsiniz.  
  
    -   Uygulayan bir veri sözleşmesi sahip <xref:System.Runtime.Serialization.IExtensibleDataObject> arabirimi, bir izin verebilir <xref:System.Runtime.Serialization.DataContractSerializer> veri sözleşmesi uygulamalarıyla daha yeni sürümlerinde sözleşme önceki sürümleriyle tanımlanan üyeleri geçirmek için.  
  
 Tüm farklılıklar, XML, öğesine rağmen <xref:System.Xml.Serialization.XmlSerializer> serileştiren bir türü varsayılan olarak anlam olarak hangi içine XML aynıdır <xref:System.Runtime.Serialization.DataContractSerializer> ad alanı XML açıkça tanımlanmış için sağlanan bir tür serileştirir. Öznitelikleri serileştiricileri her ikisi de ile kullanmak için aşağıdaki sınıf tarafından anlamsal olarak aynı XML veri dönüştürülür <xref:System.Xml.Serialization.XmlSerializer> ve göre <xref:System.Runtime.Serialization.DataContractAttribute>:  
  
```  
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
  
 Windows Yazılım Geliştirme Seti (SDK) adlı bir komut satırı aracı içerir [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). ASP.NET Web Hizmetleri ile kullanılan XSD.exe'nin aracı gibi Svcutil.exe XML şemasından .NET veri türlerinin tanımlarını oluşturabilir. Veri sözleşmeleri varsa türleridir <xref:System.Runtime.Serialization.DataContractSerializer> XML XML şeması tarafından tanımlanan biçimde yayma; Aksi halde, bunlar serileştirme kullanmak için tasarlanmıştır <xref:System.Xml.Serialization.XmlSerializer>. Svcutil.exe de üretebilir XML Şeması veri sözleşmelerinden kullanarak kendi `dataContractOnly` geçin.  
  
> [!NOTE]
>  Kullanım ASP.NET Web Hizmetleri olsa da <xref:System.Xml.Serialization.XmlSerializer>ve WCF ASP.NET uyumluluk modu yapar ASP.NET Web Hizmetleri davranışını taklit eden WCF hizmetleri, ASP.NET uyumluluğu seçeneği kullanılarak birine kısıtlamaz <xref:System.Xml.Serialization.XmlSerializer>. Bir kullanmaya devam edebilirsiniz <xref:System.Runtime.Serialization.DataContractSerializer> ASP.NET uyumluluk modunda çalışan hizmetleri ile.  
  
## <a name="service-development"></a>Hizmet geliştirme  
 ASP.NET kullanarak bir hizmeti geliştirmek için onu eklemek için her zamanki <xref:System.Web.Services.WebService> bir sınıfa öznitelik ve <xref:System.Web.Services.WebMethodAttribute> hizmetinin operations olacak o sınıfın yöntemlerden herhangi birini için:  
  
```  
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
  
 ASP.NET 2.0 sunulan öznitelik ekleme seçeneğiniz <xref:System.Web.Services.WebService> ve <xref:System.Web.Services.WebMethodAttribute> bir arabirime yerine bir sınıf ve arabirimini uygulayan bir sınıf yazmak için:  
  
```  
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
  
 Bu seçeneği kullanarak olduğundan tercih edilen, olması için arabirimle <xref:System.Web.Services.WebService> özniteliği oluşturduğunu aynı sözleşme farklı şekillerde uygulayabilir çeşitli sınıflarıyla yeniden hizmeti tarafından gerçekleştirilen işlemler için bir sözleşmede.  
  
 Bir WCF hizmeti bir veya daha fazla WCF uç noktaları tanımlayarak sağlanır. Bir uç nokta bir adresi, bağlama ve hizmet sözleşmesini tarafından tanımlanır. Hizmet bulunduğu adresi tanımlar. Bağlama hizmetiyle iletişim kurma belirtir. Hizmet Sözleşmesi Hizmet gerçekleştirebileceğiniz işlemler tanımlar.  
  
 Hizmet sözleşmesi genellikle ilk olarak, ekleyerek tanımlanan <xref:System.ServiceModel.ServiceContractAttribute> ve <xref:System.ServiceModel.OperationContractAttribute> bir arabirim için:  
  
```  
[ServiceContract]  
public interface IEcho  
{  
     [OperationContract]  
     string Echo(string input);  
}  
```  
  
 <xref:System.ServiceModel.ServiceContractAttribute> Arabirimi bir WCF hizmet sözleşmesini tanımlayan belirtir ve <xref:System.ServiceModel.OperationContractAttribute> , varsa, arabirim yöntemleri hizmet sözleşmesinin işlemleri tanımlayan gösterir.  
  
 Bir hizmet sözleşmesini tanımlandıktan sonra hizmet sözleşmesi tanımlandığı arabirimini uygulayan sınıf sağlayarak bir sınıfta uygulanır:  
  
```  
public class Service : IEcho  
{  
    public string Echo(string input)  
    {  
       return input;  
    }  
}  
```  
  
 Bir hizmet sözleşmesini uygulayan bir sınıf içinde WCF hizmet olarak yazmak için denir.  
  
 Bir adresi ve bir bağlama hizmet türü ile ilişkilendirmek için sonraki adım olacaktır. Genellikle bir yapılandırma dosyasında, dosyanın doğrudan düzenleyerek veya WCF ile sağlanan yapılandırma Düzenleyicisi kullanılarak yapılır. Bir yapılandırma dosyası bir örneği burada verilmiştir.  
  
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
  
 Bağlama uygulamayla iletişim kurmak için protokol kümesini belirtir. Aşağıdaki tabloda ortak seçenekleri temsil eden sistem tarafından sağlanan bağlamalar listeler.  
  
|Ad|Amaç|  
|----------|-------------|  
|BasicHttpBinding|Web Hizmetleri ve WS-BasicProfile 1.1 ve temel güvenlik profili 1.0 destekleyen istemciler ile birlikte çalışabilirlik.|  
|WSHttpBinding|Web Hizmetleri ve desteği WS - istemcileri ile birlikte çalışabilirlik * HTTP üzerinden iletişim kuralları.|  
|WSDualHttpBinding|Çift yönlü HTTP iletişimi, ilk ileti alıcısı doğrudan ilk göndereni yanıtlamak değil, ancak yanıt herhangi bir sayıda in conformity with WS - HTTP kullanarak bir süre boyunca ileten * protokoller.|  
|WSFederationBinding|Bir hizmeti kaynaklarına erişimi denetlenebilir, HTTP iletişimi açıkça tanımlanmış kimlik bilgisi sağlayıcısı tarafından verilen kimlik bilgileri temel.|  
|NetTcpBinding|Bir ağ üzerinden WCF yazılım varlıklar arasındaki iletişimi güvenli, güvenilir ve yüksek performans.|  
|NetNamedPipeBinding|Aynı makine üzerinde WCF yazılım varlıklar arasındaki iletişimi güvenli, güvenilir ve yüksek performans.|  
|NetMsmqBinding|MSMQ kullanarak WCF yazılım varlıklar arasındaki iletişim.|  
|MsmqIntegrationBinding|Bir WCF yazılım varlık ve MSMQ kullanarak başka bir yazılım varlık arasındaki iletişim.|  
|NetPeerTcpBinding|Windows Eşler arası ağ iletişimi kullanarak WCF yazılım varlıklar arasındaki iletişim.|  
  
 Sistem tarafından sağlanan bağlama <xref:System.ServiceModel.BasicHttpBinding>, ASP.NET Web Hizmetleri tarafından desteklenen protokolleri kümesi içerir.  
  
 Özel bağlamalar WCF uygulamaları için kolayca tekil protokollerin uygulamak için WCF kullanır bağlama öğe sınıfları koleksiyon olarak tanımlanır. Yeni bağlama öğeleri, ek protokoller temsil etmek için yazılabilir.  
  
 Hizmet türleri iç davranışını ailesi davranışları adlı sınıfları, özellikleri kullanılarak ayarlanabilir. Burada, <xref:System.ServiceModel.ServiceBehaviorAttribute> sınıfı hizmet türü birden çok iş parçacıklı olduğunu belirtmek için kullanılır.  
  
```  
[ServiceBehavior(ConcurrencyMode=ConcurrencyMode.Multiple]  
public class DerivativesCalculatorServiceType: IDerivativesCalculator  
```  
  
 Bazı davranışları ister <xref:System.ServiceModel.ServiceBehaviorAttribute>, öznitelikler. Diğer yöneticiler ayarlamak için istediğiniz özelliklere sahip olanları uygulama yapılandırmasında değiştirilebilir.  
  
 Hizmet türlerini programlama sık kullanılan olarak yapılan <xref:System.ServiceModel.OperationContext> sınıfı. Kendi statik <xref:System.ServiceModel.OperationContext.Current%2A> özelliği bir işlem çalıştığından bağlamı ile ilgili bilgilere erişim sağlar. <xref:System.ServiceModel.OperationContext> her ikisi de benzer <xref:System.Web.HttpContext> ve <xref:System.EnterpriseServices.ContextUtil> sınıfları.  
  
## <a name="hosting"></a>Barındırma  
 ASP.NET Web Hizmetleri, bir sınıf kitaplığı derlemeye derlenir. Hizmet dosyası adlı bir dosya uzantısı .asmx sahip ve içeren koşuluyla olan bir `@ WebService` hizmeti ve onu bulunduğu derleme kodunu içeren sınıf tanımlar yönergesi.  
  
```  
<%@ WebService Language="C#" Class="Service,ServiceAssembly" %>  
```  
  
 Hizmet dosyası, ASP.NET uygulama kökü Internet Information Services (IIS) kopyalanır ve derleme o uygulama kökü \bin alt kopyalanır. Uygulama sonra Tekdüzen Kaynak Konum Belirleyicisi (URL)'uygulama kök hizmet dosyasının kullanılarak erişilebilir.  
  
 WCF hizmetleri taşımalarına IIS 5.1 veya 6.0, Windows İşlem Etkinleştirme Hizmeti (IIS 7. 0'da, bir parçası olarak sağlanan WAS) içinde ve herhangi bir .NET uygulama içinde barındırılabilir. IIS 5.1 veya 6.0 hizmetinde barındırmak için hizmet iletişimleri Aktarım Protokolü olarak HTTP kullanmanız gerekir.  
  
 Bir hizmet WAS veya IIS 5.1, 6.0 içinde barındırmak için aşağıdaki adımları kullanın:  
  
1.  Sınıf kitaplığı derlemesini hizmet türü derleyin.  
  
2.  .Svc uzantısına sahip bir hizmet dosyası oluşturma bir `@ ServiceHost` yönergesi hizmet türünü tanımlamak için:  
  
    ```  
    <%@ServiceHost language="c#" Service="MyService" %>  
    ```  
  
3.  Bir sanal dizin ve bu sanal dizine \bin alt derlemeye hizmet dosyasını kopyalayın.  
  
4.  Yapılandırma dosyasını sanal dizine kopyalayın ve Web.config adlandırın.  
  
 Uygulama daha sonra uygulama kökü hizmet dosyasında URL'yi kullanarak erişilebilir.  
  
 .NET uygulaması içindeki bir WCF Hizmeti barındırma için uygulama tarafından başvurulan bir sınıf kitaplığı derlemesini hizmet türü derlemek ve ana bilgisayar hizmeti kullanarak uygulamaya program <xref:System.ServiceModel.ServiceHost> sınıfı. Gerekli temel programlama örneği verilmiştir:  
  
```  
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
  
 Bu örnek, bir veya daha fazla aktarım protokolleri için adresleri oluşturma işlemi belirtilen nasıl gösterir bir <xref:System.ServiceModel.ServiceHost>. Bu adresler temel adresleri olarak adlandırılır.  
  
 Herhangi bir WCF Hizmeti uç noktası için sağlanan adresi, bir taban adresi uç noktanın konağının göreli bir adrestir. Konağın her iletişim Aktarım Protokolü için bir taban adresi olabilir. Önceki yapılandırma dosyasında örnek yapılandırmasında <xref:System.ServiceModel.BasicHttpBinding> HTTP uç noktası kullanımları Aktarım Protokolü olarak şekilde uç noktası adresi seçili `EchoService`, ana bilgisayarın HTTP temel göre adresidir. Ana bilgisayarın söz konusu olduğunda önceki örnekte, HTTP temel adresi olduğunu http://www.contoso.com:8000/. IIS ya da WAS içinde barındırılan bir hizmet için taban adresi hizmetin hizmet dosyasının URL'dir.  
  
 IIS veya WAS ve hangi HTTP ile Aktarım Protokolü olarak yalnızca, yapılandırılmış barındırılan yalnızca hizmetlerine WCF ASP.NET uyumluluk modu seçeneğini kullanmak için yapılabilir. Bu seçenek açma aşağıdaki adımları gerektirir.  
  
1.  Programcı eklemelisiniz <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> özniteliği için hizmet türü ve ASP.NET uyumluluk modunda izin verilen veya gerekli belirtin.  
  
    ```  
    [System.ServiceModel.Activation.AspNetCompatibilityRequirements(  
          RequirementsMode=AspNetCompatbilityRequirementsMode.Require)]  
    public class DerivativesCalculatorServiceType: IDerivativesCalculator  
    ```  
  
2.  Yönetici, uygulamayı ASP.NET uyumluluğu modunu kullanacak şekilde yapılandırmanız gerekir.  
  
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
  
     WCF uygulamaları, kendi hizmet dosyalarda .svc yerine .asmx uzantısı olarak kullanmak için de yapılandırılabilir.  
  
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
  
     Bu seçenek .asmx hizmeti dosyaları URL'lerini WCF kullanmak için bir hizmet değiştirirken kullanmak üzere yapılandırılmış istemciler değiştirmek zorunda kalmaktan kaydedebilirsiniz.  
  
## <a name="client-development"></a>İstemci geliştirme  
 İstemcileri ASP.NET Web Hizmetleri için giriş olarak .asmx dosyanın URL'sini sağlar WSDL.exe komut satırı aracı kullanılarak oluşturulur. WCF tarafından sağlanan karşılık gelen bir araçtır [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Hizmet sözleşmesi tanımını ve bir WCF istemcisi sınıfının tanımını kod modülüyle oluşturur. Ayrıca, adresi ve hizmet bağlama ile bir yapılandırma dosyası oluşturur.  
  
 Uzak Hizmet istemcisi programlama göre zaman uyumsuz bir desen program genellikle tavsiye edilir. Her zaman WSDL.exe aracı tarafından oluşturulan kodu hem bir zaman uyumlu ve zaman uyumsuz desen varsayılan olarak sağlar. Tarafından oluşturulan kodu [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) için ya da Desen belirtebilirsiniz. Bu, varsayılan olarak zaman uyumlu desenini sağlar. Aracı ile yürütülürse `/async` geçiş için zaman uyumsuz desen oluşturulan kod sağlar.  
  
 ASP tarafından oluşturulan WCF istemci sınıfları adlandıran garantisi yoktur. NET'in WSDL.exe aracı, varsayılan olarak, WCF istemci sınıfları Svcutil.exe aracı tarafından oluşturulan adlarında eşleşir. Özellikle, sınıf özelliklerini adlarını sahip kullanılarak serileştirilmesi <xref:System.Xml.Serialization.XmlSerializer> varsayılan olarak, WSDL.exe aracıyla geçerli olmadığı Svcutil.exe aracı tarafından oluşturulan kodu soneki özelliği verilir.  
  
## <a name="message-representation"></a>İleti gösterimi  
 Gönderilen ve ASP.NET Web Hizmetleri tarafından alınan SOAP iletilerine üstbilgileri özelleştirilebilir. Öğesinden türetilmiş bir sınıf <xref:System.Web.Services.Protocols.SoapHeader> üstbilgi yapısını tanımlamak için ve ardından <xref:System.Web.Services.Protocols.SoapHeaderAttribute> üstbilgi varlığını göstermek için kullanılır.  
  
```  
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
  
 WCF öznitelikleri sağlar <xref:System.ServiceModel.MessageContractAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute>, ve <xref:System.ServiceModel.MessageBodyMemberAttribute> hizmeti tarafından gönderilen ve alınan SOAP iletilerine yapısını tanımlamak için.  
  
```  
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
  
 İletileri yapısı bir ASP.NET Web hizmeti kodu tarafından kapsanan ancak bu söz dizimini iletileri yapısını açık bir temsili üretir. Ayrıca, ASP.NET sözdiziminde ileti üstbilgilerini hizmet özellikleri olarak gibi gösterilir `ProtocolHeader` özelliği önceki örnekte, iletilerin özelliklerini daha doğru bir şekilde gösterilen WCF sözdiziminde ise. Ayrıca, WCF uç noktaları yapılandırma için eklenecek ileti üstbilgilerini sağlar.  
  
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
  
 Seçeneği, istemci veya hizmet için kod infrastructural protokol üstbilgisinde herhangi bir referans önlemek sağlar: üst uç nokta nasıl yapılandırıldığını nedeniyle iletileri eklenir.  
  
## <a name="service-description"></a>Hizmet Açıklaması  
 Bir HTTP GET isteği bir ASP.NET Web hizmeti .asmx dosyası için WSDL sorgu ile verme hizmet açıklamak için WSDL oluşturmak ASP.NET neden olur. Döndürür WSDL isteğine yanıt olarak.  
  
 ASP.NET 2.0 yaptığı bir hizmeti Web Hizmetleri birlikte işlerliği kuruluşun temel Profil 1.1 ile uyumlu olduğunu doğrulamak olası (WS-ı) ve hizmet WSDL uyumlu olduğunu talep eklemek için. Diğer bir deyişle Bitti'yi kullanarak `ConformsTo` ve `EmitConformanceClaims` parametrelerinin <xref:System.Web.Services.WebServiceBindingAttribute> özniteliği.  
  
```  
[WebService(Namespace = "http://tempuri.org/")]  
[WebServiceBinding(  
     ConformsTo = WsiProfiles.BasicProfile1_1,  
     EmitConformanceClaims=true)]  
public interface IEcho  
```  
  
 Bir hizmet için ASP.NET oluşturur WSDL özelleştirilebilir. Özelleştirmeleri, türetilmiş bir sınıf oluşturarak yapılır <xref:System.Web.Services.Description.ServiceDescriptionFormatExtension> WSDL öğeler eklemek için.  
  
 IIS 51 içinde barındırılan bir HTTP uç noktası ile bir WCF hizmeti .svc dosyası için WSDL sorgu ile bir HTTP GET isteği veren, 6.0 veya WAS hizmeti açıklamak için WSDL ile yanıtlamak WCF neden olur. Bir .NET uygulama içinde barındırılan bir hizmete HTTP temel adresine WSDL sorgu ile bir HTTP GET isteği verme etkisi aynı de ayarlandıysa true.  
  
 Ancak, WCF ayrıca bir hizmet açıklamak için oluşturur WSDL WS-MetadataExchange isteklerine yanıt verir. ASP.NET Web Hizmetleri, WS-MetadataExchange istekleri için yerleşik destek yok.  
  
 WCF oluşturur WSDL kapsamlı bir şekilde özelleştirilebilir. <xref:System.ServiceModel.Description.ServiceMetadataBehavior> Sınıfı WSDL özelleştirmek için bazı özellikleri sağlar. WCF WSDL oluşturmak değil ancak yerine belirtilen bir URL'de statik WSDL dosyası kullanmak için de yapılandırılabilir.  
  
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
 ASP.NET Web Hizmetleri içinde işlenmeyen özel durumlar istemcilere SOAP hataları döndürülür. Aynı zamanda açıkça örneklerini atabilirsiniz <xref:System.Web.Services.Protocols.SoapException> sınıfı ve istemciye iletilen bir SOAP hatası içeriğini daha fazla denetime sahip olursunuz.  
  
 WCF hizmetlerinde işlenmeyen özel durumlar istemcilere hassas bilgilerin yanlışlıkla'nda özel durumlara yararlanılmasını önlemek için SOAP hataları olarak döndürülmez. Bir yapılandırma ayarı, hata ayıklama amacıyla istemcilere döndürülen özel durum işlenmemiş için sağlanmıştır.  
  
 SOAP hataları istemcilere döndürmek için genel tür örneklerini atabilirsiniz <xref:System.ServiceModel.FaultException%601>kullanarak verileri sözleşme genel tür olarak türü. Ayrıca ekleyebileceğiniz <xref:System.ServiceModel.FaultContractAttribute> öznitelikleri bir işlem verim hataları belirtmek için işlemleri.  
  
```  
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
  
 Olası hataları sonuçlarında hizmeti WSDL içinde tanıtılan bunları yapmak, hangi hataları düşündüğünüz programcıların izin vermeden bir işlemden neden ve uygun catch deyimleri yazma.  
  
```  
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
 Bir ASP.NET Web hizmeti uygulamak için kullanılan sınıfın türetildiği <xref:System.Web.Services.WebService>.  
  
```  
public class Service : WebService, IEcho  
{  
  
 public string Echo(string input)  
 {  
  return input;  
 }  
}  
```  
  
 Bu durumda, sınıf kullanmak için programlanabilir <xref:System.Web.Services.WebService> sınıfı içerik özelliği erişmek için temel bir <xref:System.Web.HttpContext> nesnesi. <xref:System.Web.HttpContext> Nesnesi olabilir güncelleştirme ve uygulama özelliğini kullanarak uygulama durum bilgilerini almak için kullanılan ve güncelleştirmek ve onun oturum özelliğini kullanarak oturum durumu bilgilerini almak için kullanılabilir.  
  
 ASP.NET, burada oturum durum bilgisi oturum özelliği kullanılarak önemli ölçüde denetim sağlar <xref:System.Web.HttpContext> gerçekten depolanır. Tanımlama bilgileri, bir veritabanı, geçerli sunucunun bellek veya atanmış bir sunucu bellek depolanabilir. Seçimi hizmetin yapılandırma dosyasında yapılır.  
  
 WCF genişletilebilen nesneler için durum yönetimini sağlar. Genişletilebilir nesneleridir uygulayan nesneler <xref:System.ServiceModel.IExtensibleObject%601>. En önemli Genişletilebilir nesneler <xref:System.ServiceModel.ServiceHostBase> ve <xref:System.ServiceModel.InstanceContext>. `ServiceHostBase` tüm hizmet örneklerinin yazdığı aynı konakta durumu erişebilir, sağlamanıza olanak tanır ancak `InstanceContext` içinde bir hizmet türü'nın aynı örneğini çalıştıran herhangi bir kod tarafından erişilebilecek durumu korumanıza olanak sağlar.  
  
 Burada, hizmet türü `TradingSystem`, sahip bir <xref:System.ServiceModel.ServiceBehaviorAttribute> belirtir aynı WCF istemci örneğinden tüm çağrıları hizmet türü'nın aynı örneğinin yönlendirilir.  
  
```  
[ServiceBehavior(InstanceContextMode = InstanceContextMode.PerSession)]  
public class TradingSystem: ITradingService  
```  
  
 Sınıf `DealData`, bir hizmet türünün aynı örneğinde çalışan herhangi bir kod tarafından erişilebilecek bir durum tanımlar.  
  
```  
internal class DealData: IExtension<InstanceContext>  
{  
 public string DealIdentifier = null;  
 public Trade[] Trades = null;  
}  
```  
  
 Hizmet sözleşmesi işlemlerden birini uygulayan hizmet türüne ilişkin kodda bir `DealData` durum nesnesi geçerli hizmet türü örneği durumuna eklenir.  
  
```  
string ITradingService.BeginDeal()  
{  
 string dealIdentifier = Guid.NewGuid().ToString();  
 DealData state = new DealData(dealIdentifier);  
 OperationContext.Current.InstanceContext.Extensions.Add(state);  
 return dealIdentifier;  
}  
```  
  
 Bu durum nesnesi alınır ve başka bir hizmet sözleşmenin işlemleri uygulayan kod tarafından değiştirilebilir.  
  
```  
void ITradingService.AddTrade(Trade trade)  
{  
 DealData dealData =  OperationContext.Current.InstanceContext.Extensions.Find<DealData>();  
 dealData.AddTrade(trade);  
}  
```  
  
 ASP.NET üzerinde denetim sağlar ancak burada bilgilerinde durum <xref:System.Web.HttpContext> gerçekten sınıfı depolanır, WCF, en az ilk sürümünde genişletilebilen nesneler depolandığı üzerinden hiçbir denetim sağlar. Bir WCF hizmetini ASP.NET uyumluluk modu seçmek için en iyi neden meydana gelir. Yapılandırılabilir durum yönetimi kesinlik temelli sonra ASP.NET uyumluluk modu kullanmama sağlar, özelliklerini kullanabilmeniz <xref:System.Web.HttpContext> sınıfı tam olarak ASP.NET ve yapılandırmak için kullanıldıkları haliyle burada durum kullanılarakyönetilenbilgisi<xref:System.Web.HttpContext> sınıfı depolanır.  
  
## <a name="security"></a>Güvenlik  
 ASP.NET Web Hizmetleri güvenli hale getirme seçenekleri herhangi bir IIS uygulama güvenliğini sağlamak için olanlardır. WCF uygulamalar yalnızca IIS içinde aynı zamanda herhangi bir .NET yürütülebilir dosya içinde barındırılan olduğundan, WCF uygulamalarının güvenliğini sağlama seçeneklerini IIS tesis bağımsız yapılması gerekir. Ancak, ASP.NET Web Hizmetleri için sağlanan özellikleri de ASP.NET uyumluluk modunda çalışan WCF hizmetleri için kullanılabilir.  
  
### <a name="security-authentication"></a>Güvenlik: kimlik doğrulaması  
 IIS olarak seçebileceğiniz Anonim erişim veya kimlik doğrulama modları çeşitli uygulamalara erişimi denetleme olanakları sağlar: Windows kimlik doğrulaması, Özet kimlik doğrulaması, temel kimlik doğrulaması ve .NET Passport kimlik doğrulaması. Windows kimlik doğrulaması seçeneği, ASP.NET Web Hizmetleri erişimi denetlemek için kullanılabilir. Ancak, WCF uygulamaları IIS içinde barındırıldığında, IIS kimlik doğrulamanın diğer çeşitli seçenekler arasından Windows kimlik doğrulamasını destekleyen WCF kendisi tarafından yönetilecek şekilde uygulama anonim erişime izin vermek için yapılandırılmalıdır. Yerleşik diğer seçenekler, kullanıcı adı belirteçleri, X.509 sertifikaları, SAML belirteçleri ve CardSpace kart içerir, ancak özel kimlik doğrulama mekanizmaları de tanımlanabilir.  
  
### <a name="security-impersonation"></a>Güvenlik: kimliğe bürünme  
 ASP.NET kimlik öğesi, bir ASP.NET Web hizmeti belirli bir kullanıcının kimliğine bürünmek için yapılabilir veya hangi kullanıcının kimlik bilgilerinin geçerli istekle sağlanan sağlar. Bu öğe, kimliğe bürünme ASP.NET uyumluluk modunda çalışan WCF uygulamalarını yapılandırmak için kullanılabilir.  
  
 WCF yapılandırma sistemi kimliğine bürünmek için belirli bir kullanıcı atamak için kendi kimlik öğesi sağlar. Ayrıca, WCF istemcileri ve Hizmetleri bağımsız olarak kimliğe bürünme için yapılandırılabilir. İstemciler, istekleri aktarırken geçerli kullanıcının kimliğine bürünmek için yapılandırılabilir.  
  
```xml  
<behaviors>  
     <behavior name="DerivativesCalculatorClientBehavior">  
      <clientCredentials>  
      <windows allowedImpersonationLevel="Impersonation"/>  
      </clientCredentials>  
     </behavior>  
</behaviors>  
```  
  
 Hizmet işlemleri hangi kullanıcının kimlik bilgilerinin geçerli istekle sağlanan kimliğine bürünmek için yapılandırılabilir.  
  
```  
[OperationBehavior(Impersonation = ImpersonationOption.Required)]  
public void Receive(Message input)  
```  
  
### <a name="security-authorization-using-access-control-lists"></a>Güvenlik: Erişim denetimi listeleri kullanarak Yetkilendirme  
 Erişim denetim listeleri (ACL'ler) .asmx dosyalara erişimi kısıtlamak için kullanılabilir. Ancak, WCF .svc dosyalarını ACL'lerin dışında ASP.NET uyumluluk modunda göz ardı edilir.  
  
### <a name="security-role-based-authorization"></a>Güvenlik: Rol tabanlı yetkilendirme  
 IIS Windows kimlik doğrulaması seçeneği birlikte ASP.NET yapılandırma dil tarafından sağlanan yetkilendirme öğesi ile kullanıcılara atanmış olan Windows gruplarını temel alan ASP.NET Web Hizmetleri için rol tabanlı yetkilendirme kolaylaştırmak için kullanılabilir . ASP.NET 2.0 sunulan daha genel bir rol tabanlı yetkilendirme mekanizması: rol sağlayıcıları.  
  
 Rol sağlayıcıları tüm atanmış bir kullanıcı için rolleri hakkında enquiring için temel bir arabirim uygulamak, ancak farklı bir kaynaktan bu bilgileri almak nasıl her rol sağlayıcısı bilir sınıflarıdır. ASP.NET 2.0 rol atamalarını Windows Server 2003 Yetkilendirme Yöneticisi'nden alabilirsiniz rol atamalarını bir Microsoft SQL Server veritabanı ve başka alabilen bir rol sağlayıcı sağlar.  
  
 Rol sağlayıcı mekanizması WCF uygulaması da dahil olmak üzere tüm .NET uygulamasında gerçekte ASP.NET bağımsız olarak kullanılabilir. WCF uygulaması için şu örnek yapılandırma nasıl bir ASP.NET rol sağlayıcıyı kullanımı yoluyla bir seçeneğe gösterilir <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>.  
  
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
  
### <a name="security-claims-based-authorization"></a>Güvenlik: Talep tabanlı yetkilendirme  
 Bir WCF en önemli yeniliklerden talepleri temelinde korunan kaynaklara erişimi yetkilendirmek için kapsamlı desteğidir. Talep türü, bir hak ve bir değer, bir sürücüleri lisans, örneğin oluşur. Biri taşıyıcı'nin doğum tarihi olan taşıyıcı hakkında talepler kümesi kolaylaştırır. Talep değeri sürücünün doğum tarihi olsa da bu talep türünü doğum tarihi, ' dir. Bir talep taşıyıcı confers sağ taşıyıcı talebin değeri ile neler yapabileceğinizi belirtir. Doğum tarihi sürücünün talep durumunda elinde hangisi: Doğum tarihi ancak, örneğin olamaz, sürücü sahip, üzerinde değişiklik. Talep tabanlı yetkilendirme, rol talep türü olduğundan rol tabanlı bir yetkilendirme barındırır.  
  
 Talep tabanlı yetkilendirme gerekliliklerini işlemin ve bu karşılaştırma sonucunu bağlı olarak talepler kümesi karşılaştırma vererek ya da işlemi erişimi reddetme gerçekleştirilir. WCF ' bir değer atayarak talep tabanlı yetkilendirme, bir kez yeniden çalıştırmak için bir sınıf belirtebilirsiniz `ServiceAuthorizationManager` özelliği <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>.  
  
```xml  
<behaviors>  
     <behavior name='ServiceBehavior'>  
     <serviceAuthorization   
     serviceAuthorizationManagerType=  
                   'Service.AccessChecker, Service' />  
     </behavior>  
</behaviors>  
```  
  
 Talep tabanlı yetkilendirme çalıştırmak için kullanılan sınıfları öğesinden türetilmelidir <xref:System.ServiceModel.ServiceAuthorizationManager>, geçersiz kılmak için yalnızca bir yöntemi olan `AccessCheck()`. WCF hizmet işlemini çağrılır ve sağlar bu yöntemi çağırır bir <xref:System.ServiceModel.OperationContext> kullanıcı talebini sahip nesne, kendi `ServiceSecurityContext.AuthorizationContext` özelliği. WCF mu hangi güvenlik belirteci kullanıcı hakkında talepleri atayarak iş bırakır kimlik doğrulaması için sağlanan kullanıcı bu talep ilgili işlem için yeterli olup olmadığını değerlendirmek, görev.  
  
 Kimlik doğrulama mekanizması tamamen bağımsız talep tabanlı yetkilendirme kodu kolaylaştırır WCF güvenlik herhangi bir tür otomatik olarak talep derler yüksek oranda önemli bir yenilik belirteci olmasıdır. Bunun aksine, ACL'ler ya da roller ASP.NET kullanarak yetkilendirmeyi yakından Windows kimlik doğrulaması olarak bağlıdır.  
  
### <a name="security-confidentiality"></a>Güvenlik: gizlilik  
 ASP.NET Web Hizmetleri ile değiştirilen iletilerin gizliliğini aktarım düzeyinde uygulamayı IIS içinde Güvenli Köprü Metni Aktarım Protokolü (HTTPS) kullanacak şekilde yapılandırarak güvence altına alınabilir. Aynı içinde IIS barındırılan WCF uygulamalar için yapılabilir. Ancak, dışında IIS barındırılan WCF uygulamaları güvenli aktarım protokolünü kullanmak için de yapılandırılabilir. Daha da önemlisi, WCF uygulamaları, bunlar, WS-güvenlik protokolünü kullanarak taşınacağını önce iletileri güvenli hale getirmek için de yapılandırılabilir. WS güvenliği kullanarak ileti gövdesi güvenliğini sağlama ilkemiz aracılar son hedefine ulaşmadan önce iletilmesi izin verir.  
  
## <a name="globalization"></a>Genelleştirme  
 ASP.NET yapılandırma dil tek tek Hizmetleri için kültür belirtmenize olanak tanır. WCF ASP.NET uyumluluk modunda dışında bu yapılandırma ayarını desteklemiyor. ASP.NET uyumluluğu modunu kullanmayan bir WCF Hizmeti yerelleştirme için hizmet türü kültüre özgü derlemeler içine derleyin ve her kültüre özgü derlemesi için ayrı kültüre özgü uç noktalar vardır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ASP.NET Web Hizmetlerini Amaç ve Kullanılan Standartları Temel Alarak WCF ile Karşılaştırma](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used.md)
