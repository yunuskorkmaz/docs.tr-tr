---
title: "ASP.NET Web Hizmetlerini Geliştirmeye Göre WCF ile Karşılaştırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f362d00e-ce82-484f-9d4f-27e579d5c320
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c12bd11cee62cd769f7dffc142806fa5ab1b0137
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="comparing-aspnet-web-services-to-wcf-based-on-development"></a>ASP.NET Web Hizmetlerini Geliştirmeye Göre WCF ile Karşılaştırma
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]etkinleştirmek için bir ASP.NET uyumluluk modu seçeneği sahip [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] programlanmış ve yapılandırılmış olması uygulamalar gibi ASP.NET Web Hizmetleri ve davranışlarını taklit etmek. Aşağıdaki bölümlerde ASP.NET Web Hizmetleri karşılaştırın ve [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ne iki teknolojiyi kullanarak uygulamaları geliştirmek için gerekli olduğuna bağlı olarak.  
  
## <a name="data-representation"></a>Veri temsili  
 ASP.NET Web hizmetiyle geliştirme genellikle hizmet kullanmaktır herhangi karmaşık veri türlerini tanımlama ile başlar. ASP.NET kullanır <xref:System.Xml.Serialization.XmlSerializer> iletim ya da hizmet için XML ve .NET Framework türleri tarafından gösterilen veriler Çevir ve .NET Framework nesnelerini XML olarak alınan veriler çevir. ASP.NET hizmeti kullanmaktır karmaşık veri türlerini tanımlama gerektiren .NET Framework'ün tanımı sınıfları <xref:System.Xml.Serialization.XmlSerializer> XML gelen ve giden seri hale getirebilir. Bu tür sınıflar el ile yazılmış veya komut satırı XML şemaları/veri türleri destek yardımcı programı kullanarak XML şemasındaki türlerinin tanımlarını üretilen XSD.exe'nin.  
  
 Ne zaman .NET Framework tanımlayan sınıflar bilmeniz anahtar sorunların bir listesi aşağıda verilmiştir <xref:System.Xml.Serialization.XmlSerializer> XML gelen ve giden seri hale getirebilir:  
  
-   Yalnızca genel alanlar ve .NET Framework nesnelerin özelliklerini XML çevrilir.  
  
-   Koleksiyon sınıfları örneklerini hale getirilebilir XML sınıflar ya da uygularsanız <xref:System.Collections.IEnumerable> veya <xref:System.Collections.ICollection> arabirimi.  
  
-   Sınıfları uygulayan <xref:System.Collections.IDictionary> gibi arabirim <xref:System.Collections.Hashtable>, XML'de serileştirilir.  
  
-   Çoğu öznitelik türlerinde mükemmel <xref:System.Xml.Serialization> ad alanı .NET Framework sınıf ve üyeleri sınıfın örnekleri, XML'de nasıl temsil edildiğini denetlemek için eklenebilir.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]uygulama geliştirme de genellikle karmaşık türler tanımıyla başlar. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]ASP.NET Web Hizmetleri olarak aynı .NET Framework türlerini kullanmak için yapılabilir.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] <xref:System.Runtime.Serialization.DataContractAttribute> Ve <xref:System.Runtime.Serialization.DataMemberAttribute> türdeki örneklerin XML ve hangi belirli alanlar veya türünün özelliklerini serileştirilmesi için aşağıdaki örnekte gösterildiği gibi içine serileştirilecek olduğunu belirtmek için .NET Framework türleri eklenebilir kod.  
  
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
  
 <xref:System.Runtime.Serialization.DataContractAttribute> Sıfır veya daha fazla bir tür alanları veya özellikler olmak anlamına gelir serileştirildiği while <xref:System.Runtime.Serialization.DataMemberAttribute> belirli bir alan veya özelliği seri hale olduğunu gösterir. <xref:System.Runtime.Serialization.DataContractAttribute> Bir sınıf veya yapı uygulanabilir. <xref:System.Runtime.Serialization.DataMemberAttribute> Bir alan veya bir özellik için uygulanabilir ve ortak veya özel alanlar ve öznitelik uygulanan özellikler olabilir. Türleri örneklerini <xref:System.Runtime.Serialization.DataContractAttribute> uygulanan veri sözleşmelerinde gibi bunları olarak denir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. XML'de serileştirilir kullanarak <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
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
  
-   Başka bir sonucu <xref:System.Runtime.Serialization.DataContractSerializer> bir türün genel olmayan üyeleri erişebildiklerinden olduğundan tam güven gerektirir ancak <xref:System.Xml.Serialization.XmlSerializer> desteklemez. Tam güven kodu erişim izni altında kod yürütüyor kimlik bilgilerini kullanarak erişim olabilir bir makine üzerindeki tüm kaynaklara tam erişim verin. Tüm kaynaklar için makinenizdeki tam olarak güvenilen kod erişir gibi bu seçenekleri dikkatli kullanılmalıdır.  
  
-   <xref:System.Runtime.Serialization.DataContractSerializer> Sürüm oluşturma için bazı destek içerir:  
  
    -   <xref:System.Runtime.Serialization.DataMemberAttribute> Sahip bir <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> false değeri, böylece uygulamaların olmasını sözleşme daha yeni sürümü ile izin verecek şekilde bir veri Sözleşmesi'nın önceki sürümlerinde, mevcut olmayan yeni sürümlerine eklenen üyeler için atanabilir özelliği önceki sürümlerde işlemek kullanabilirsiniz.  
  
    -   Uygulayan bir veri sözleşmesi sahip <xref:System.Runtime.Serialization.IExtensibleDataObject> arabirimi, bir izin verebilir <xref:System.Runtime.Serialization.DataContractSerializer> veri sözleşmesi uygulamalarıyla daha yeni sürümlerinde sözleşme önceki sürümleriyle tanımlanan üyeleri geçirmek için.  
  
 Tüm farklılıklar, XML, öğesine rağmen <xref:System.Xml.Serialization.XmlSerializer> serileştiren bir türü varsayılan olarak anlam olarak hangi içine XML aynıdır <xref:System.Runtime.Serialization.DataContractSerializer> ad alanı XML açıkça tanımlanmış için sağlanan bir tür serileştirir. Öznitelikleri serileştiricileri her ikisi de ile kullanmak için aşağıdaki sınıf tarafından anlamsal olarak aynı XML içine çevrilen <xref:System.Xml.Serialization.XmlSerializer> ve göre <xref:System.Runtime.Serialization.DataContractAttribute>:  
  
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
  
 Windows Yazılım Geliştirme Seti (SDK) adlı bir komut satırı aracı içerir [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). ASP.NET Web Hizmetleri ile kullanılan XSD.exe'nin aracı gibi Svcutil.exe XML şemasından .NET veri türlerinin tanımlarını oluşturabilir. Veri sözleşmeleri varsa türleridir <xref:System.Runtime.Serialization.DataContractSerializer> XML XML şeması tarafından tanımlanan biçimde yayma; Aksi halde, bunlar serileştirme kullanmak için tasarlanmıştır <xref:System.Xml.Serialization.XmlSerializer>. Aracı, Svcutil.exe, XML şeması kullanarak veri sözleşmelerinden oluşturmak için de yapılabilir, `/dataContractOnly` geçin.  
  
> [!NOTE]
>  Kullanım ASP.NET Web Hizmetleri olsa da <xref:System.Xml.Serialization.XmlSerializer>, ve [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ASP.NET uyumluluk modu yapar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Hizmetleri, ASP.NET Web Hizmetleri davranışını taklit eden, ASP.NET uyumluluğu seçeneği kullanılarak birine kısıtlamaz <xref:System.Xml.Serialization.XmlSerializer>. Bir kullanmaya devam edebilirsiniz <xref:System.Runtime.Serialization.DataContractSerializer> ASP.NET uyumluluk modunda çalışan hizmetleri ile.  
  
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
  
 A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmeti, bir veya daha fazla tanımlayarak sağlanır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uç noktaları. Bir uç nokta bir adresi, bağlama ve hizmet sözleşmesini tarafından tanımlanır. Hizmet bulunduğu adresi tanımlar. Bağlama hizmetiyle iletişim kurma belirtir. Hizmet Sözleşmesi Hizmet gerçekleştirebileceğiniz işlemler tanımlar.  
  
 Hizmet sözleşmesi genellikle ilk olarak, ekleyerek tanımlanan <xref:System.ServiceModel.ServiceContractAttribute> ve <xref:System.ServiceModel.OperationContractAttribute> bir arabirim için:  
  
```  
[ServiceContract]  
public interface IEcho  
{  
     [OperationContract]  
     string Echo(string input);  
}  
```  
  
 <xref:System.ServiceModel.ServiceContractAttribute> Arabirimi tanımlar belirten bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet sözleşmesini ve <xref:System.ServiceModel.OperationContractAttribute> , varsa, arabirim yöntemleri hizmet sözleşmesinin işlemleri tanımlayan gösterir.  
  
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
  
 Bir hizmet sözleşmesini uygulayan bir sınıf olarak bir hizmet türünün adlandırılır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 Bir adresi ve bir bağlama hizmet türü ile ilişkilendirmek için sonraki adım olacaktır. Genellikle yapılır yapılandırma dosyasında, dosyanın doğrudan düzenleyerek veya ile sağlanan bir yapılandırma Düzenleyicisi'ni kullanarak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Bir yapılandırma dosyası bir örneği burada verilmiştir.  
  
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
|NetTcpBinding|Güvenli, güvenilir, yüksek performanslı iletişimine [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bir ağ üzerinden yazılım varlıklar.|  
|NetNamedPipeBinding|Güvenli, güvenilir, yüksek performanslı iletişimine [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aynı makine üzerinde yazılım varlıklar.|  
|NetMsmqBinding|Arasındaki iletişimi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] MSMQ kullanarak yazılım varlıklar.|  
|MsmqIntegrationBinding|Arasındaki iletişimi bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] yazılım varlık ve MSMQ kullanarak başka bir yazılım varlık.|  
|NetPeerTcpBinding|Arasındaki iletişimi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Windows Eşler arası ağ iletişimi kullanarak yazılım varlıklar.|  
  
 Sistem tarafından sağlanan bağlama <xref:System.ServiceModel.BasicHttpBinding>, ASP.NET Web Hizmetleri tarafından desteklenen protokolleri kümesi içerir.  
  
 Özel bağlamalar için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulamaları kolayca bağlama öğesi koleksiyonları sınıflar olarak tanımlanan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] tekil protokollerin uygulamak için kullanır. Yeni bağlama öğeleri, ek protokoller temsil etmek için yazılabilir.  
  
 Hizmet türleri iç davranışını ailesi davranışları adlı sınıfları, özellikleri kullanılarak ayarlanabilir. Burada, <xref:System.ServiceModel.ServiceBehaviorAttribute> sınıfı hizmet türü birden çok iş parçacıklı olduğunu belirtmek için kullanılır.  
  
```  
[ServiceBehavior(ConcurrencyMode=ConcurrencyMode.Multiple]  
public class DerivativesCalculatorServiceType: IDerivativesCalculator  
```  
  
 Bazı davranışları ister <xref:System.ServiceModel.ServiceBehaviorAttribute>, öznitelikler. Diğer yöneticiler ayarlamak için istediğiniz özelliklere sahip olanları uygulama yapılandırmasında değiştirilebilir.  
  
 Hizmet türlerini programlama sık kullanılan olarak yapılan <xref:System.ServiceModel.OperationContext> sınıfı. Kendi statik <xref:System.ServiceModel.OperationContext.Current%2A> özelliği bir işlem çalıştığından bağlamı ile ilgili bilgilere erişim sağlar. <xref:System.ServiceModel.OperationContext>her ikisi de benzer <xref:System.Web.HttpContext> ve <xref:System.EnterpriseServices.ContextUtil> sınıfları.  
  
## <a name="hosting"></a>Barındırma  
 ASP.NET Web Hizmetleri, bir sınıf kitaplığı derlemeye derlenir. Hizmet dosyası adlı bir dosya uzantısı .asmx sahip ve içeren koşuluyla olan bir `@ WebService` hizmeti ve onu bulunduğu derleme kodunu içeren sınıf tanımlar yönergesi.  
  
```  
<%@ WebService Language="C#" Class="Service,ServiceAssembly" %>  
```  
  
 Hizmet dosyası, ASP.NET uygulama kökü Internet Information Services (IIS) kopyalanır ve derleme o uygulama kökü \bin alt kopyalanır. Uygulama sonra Tekdüzen Kaynak Konum Belirleyicisi (URL)'uygulama kök hizmet dosyasının kullanılarak erişilebilir.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]IIS 5.1 veya 6.0, Windows İşlem Etkinleştirme Hizmeti (IIS 7. 0'da, bir parçası olarak sağlanan WAS) içinde ve herhangi bir .NET uygulama içinde Hizmetleri taşımalarına barındırılabilir. IIS 5.1 veya 6.0 hizmetinde barındırmak için hizmet iletişimleri Aktarım Protokolü olarak HTTP kullanmanız gerekir.  
  
 Bir hizmet WAS veya IIS 5.1, 6.0 içinde barındırmak için aşağıdaki adımları kullanın:  
  
1.  Sınıf kitaplığı derlemesini hizmet türü derleyin.  
  
2.  .Svc uzantısına sahip bir hizmet dosyası oluşturma bir `@ ServiceHost` yönergesi hizmet türünü tanımlamak için:  
  
    ```  
    <%@ServiceHost language="c#" Service="MyService" %>  
    ```  
  
3.  Bir sanal dizin ve bu sanal dizine \bin alt derlemeye hizmet dosyasını kopyalayın.  
  
4.  Yapılandırma dosyasını sanal dizine kopyalayın ve Web.config adlandırın.  
  
 Uygulama daha sonra uygulama kökü hizmet dosyasında URL'yi kullanarak erişilebilir.  
  
 Ana bilgisayar için bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet içinde .NET uygulaması, uygulama tarafından başvurulan bir sınıf kitaplığı derlemesini hizmet türü derleyin ve ana bilgisayar hizmeti kullanarak uygulamaya program <xref:System.ServiceModel.ServiceHost> sınıfı. Gerekli temel programlama örneği verilmiştir:  
  
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
  
 İçin herhangi bir uç nokta sağlanan adresi bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet uç noktanın ana bilgisayarın bir taban adresi göreli bir adresidir. Konağın her iletişim Aktarım Protokolü için bir taban adresi olabilir. Önceki yapılandırma dosyasında örnek yapılandırmasında <xref:System.ServiceModel.BasicHttpBinding> HTTP uç noktası kullanımları Aktarım Protokolü olarak şekilde uç noktası adresi seçili `EchoService`, ana bilgisayarın HTTP temel göre adresidir. Önceki örnekte konak söz konusu olduğunda HTTP temel http://www.contoso.com:8000 adresidir /. IIS ya da WAS içinde barındırılan bir hizmet için taban adresi hizmetin hizmet dosyasının URL'dir.  
  
 Yalnızca IIS veya WAS ve hangi HTTP ile Aktarım Protokolü olarak yalnızca, yapılandırılmış barındırılan hizmetleri, kullanılacak yapılabilir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ASP.NET uyumluluk modu seçeneği. Bu seçenek açma aşağıdaki adımları gerektirir.  
  
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
  
     [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]uygulamaları, kendi hizmet dosyalarda .svc yerine .asmx uzantısı olarak kullanmak için de yapılandırılabilir.  
  
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
  
     Seçeneği, .asmx hizmeti dosyaları URL'lerini kullanmak için bir hizmet değiştirirken kullanmak üzere yapılandırılmış istemciler değiştirmek zorunda kalmaktan kaydedebilirsiniz, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## <a name="client-development"></a>İstemci geliştirme  
 İstemcileri ASP.NET Web Hizmetleri için giriş olarak .asmx dosyanın URL'sini sağlar WSDL.exe komut satırı aracı kullanılarak oluşturulur. Tarafından sağlanan karşılık gelen aracı [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] olan [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Kod modülü hizmet sözleşmesi tanımını ve tanımını oluşturan bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci sınıfı. Ayrıca, adresi ve hizmet bağlama ile bir yapılandırma dosyası oluşturur.  
  
 Uzak Hizmet istemcisi programlama göre zaman uyumsuz bir desen program genellikle tavsiye edilir. Her zaman WSDL.exe aracı tarafından oluşturulan kodu hem bir zaman uyumlu ve zaman uyumsuz desen varsayılan olarak sağlar. Tarafından oluşturulan kodu [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) için ya da Desen belirtebilirsiniz. Bu, varsayılan olarak zaman uyumlu desenini sağlar. Aracı ile yürütülürse `/async` geçiş için zaman uyumsuz desen oluşturulan kod sağlar.  
  
 Adları garanti [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ASP tarafından oluşturulan istemci sınıfları. NET'in WSDL.exe aracı, varsayılan olarak, eşleşen adlarında [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Svcutil.exe aracı tarafından oluşturulan istemci sınıfları. Özellikle, sınıf özelliklerini adlarını sahip kullanılarak serileştirilmesi <xref:System.Xml.Serialization.XmlSerializer> varsayılan olarak, WSDL.exe aracıyla geçerli olmadığı Svcutil.exe aracı tarafından oluşturulan kodu soneki özelliği verilir.  
  
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
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Öznitelikleri sağlar <xref:System.ServiceModel.MessageContractAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute>, ve <xref:System.ServiceModel.MessageBodyMemberAttribute> hizmeti tarafından gönderilen ve alınan SOAP iletilerine yapısını tanımlamak için.  
  
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
  
 İletileri yapısı bir ASP.NET Web hizmeti kodu tarafından kapsanan ancak bu söz dizimini iletileri yapısını açık bir temsili üretir. Ayrıca, ASP.NET sözdiziminde ileti üstbilgilerini hizmet özellikleri olarak gibi gösterilir `ProtocolHeader` özelliği önceki örnekte, ancak içinde [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sözdizimi, bunlar daha doğru bir şekilde iletileri özellikleri olarak gösterilen. Ayrıca, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uç yapılandırma için eklenecek ileti üstbilgilerini sağlar.  
  
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
  
 Bir HTTP GET isteği .svc dosyası için WSDL sorgu verme, bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmeti 6.0 veya WAS nedenleri gibi IIS 51 içinde barındırılan bir HTTP uç noktası ile [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet açıklamak için WSDL ile yanıtlayın. Bir .NET uygulama içinde barındırılan bir hizmete HTTP temel adresine WSDL sorgu ile bir HTTP GET isteği verme etkisi aynı de ayarlandıysa true.  
  
 Ancak, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ayrıca bir hizmet açıklamak için oluşturur WSDL WS-MetadataExchange isteklerine yanıt verir. ASP.NET Web Hizmetleri, WS-MetadataExchange istekleri için yerleşik destek yok.  
  
 WSDL, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] oluşturur kapsamlı bir şekilde özelleştirilebilir. <xref:System.ServiceModel.Description.ServiceMetadataBehavior> Sınıfı WSDL özelleştirmek için bazı özellikleri sağlar. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WSDL oluşturmak değil ancak yerine bir statik WSDL dosyası belirtilen URL'de kullanacak şekilde de yapılandırılabilir.  
  
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
  
 İçinde [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Hizmetleri, İşlenmeyen özel durumlar alınmadı istemcilere hassas bilgilerin yanlışlıkla'nda özel durumlara yararlanılmasını önlemek için SOAP hataları olarak. Bir yapılandırma ayarı, hata ayıklama amacıyla istemcilere döndürülen özel durum işlenmemiş için sağlanmıştır.  
  
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
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Genişletilebilen nesneler için durum yönetimini sağlar. Genişletilebilir nesneleridir uygulayan nesneler <xref:System.ServiceModel.IExtensibleObject%601>. En önemli Genişletilebilir nesneler <xref:System.ServiceModel.ServiceHostBase> ve <xref:System.ServiceModel.InstanceContext>. `ServiceHostBase`tüm hizmet örneklerinin yazdığı aynı konakta durumu erişebilir, sağlamanıza olanak tanır ancak `InstanceContext` içinde bir hizmet türü'nın aynı örneğini çalıştıran herhangi bir kod tarafından erişilebilecek durumu korumanıza olanak sağlar.  
  
 Burada, hizmet türü `TradingSystem`, sahip bir <xref:System.ServiceModel.ServiceBehaviorAttribute> belirtir tüm çağırdığı aynı [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci örneği, hizmet türü'nın aynı örneğinin yönlendirilir.  
  
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
  
 ASP.NET üzerinde denetim sağlar ancak burada bilgilerinde durum <xref:System.Web.HttpContext> sınıfı gerçekte depolanan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], en az ilk sürümünde genişletilebilen nesneler depolandığı hiçbir denetim sağlar. ASP.NET uyumluluk modu seçmek için en iyi neden oluşturan bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet. Yapılandırılabilir durum yönetimi kesinlik temelli sonra ASP.NET uyumluluk modu kullanmama sağlar, özelliklerini kullanabilmeniz <xref:System.Web.HttpContext> sınıfı tam olarak ASP.NET ve yapılandırmak için kullanıldıkları haliyle burada durum kullanılarakyönetilenbilgisi<xref:System.Web.HttpContext> sınıfı depolanır.  
  
## <a name="security"></a>Güvenlik  
 ASP.NET Web Hizmetleri güvenli hale getirme seçenekleri herhangi bir IIS uygulama güvenliğini sağlamak için olanlardır. Çünkü [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulamaları kalmayıp aynı zamanda tüm .NET yürütülebilir, güvenliğini sağlamaya yönelik seçenekler içinden IIS içinde barındırılması [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulamaları yapılmalı IIS tesis bağımsız. Ancak, ASP.NET Web Hizmetleri için sağlanan özellikleri de kullanılabilir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ASP.NET uyumluluk modunda çalışan hizmetler.  
  
### <a name="security-authentication"></a>Güvenlik: kimlik doğrulaması  
 IIS olarak seçebileceğiniz Anonim erişim veya kimlik doğrulama modları çeşitli uygulamalara erişimi denetleme olanakları sağlar: Windows kimlik doğrulaması, Özet kimlik doğrulaması, temel kimlik doğrulaması ve .NET Passport kimlik doğrulaması. Windows kimlik doğrulaması seçeneği, ASP.NET Web Hizmetleri erişimi denetlemek için kullanılabilir. Ancak, ne zaman [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulamaları barındırıldığı IIS içinde IIS kimlik doğrulamanın tarafından yönetilecek şekilde uygulama anonim erişime izin vermek için yapılandırılmış olmalıdır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kendisine ait diğer çeşitli arasında Windows kimlik doğrulamasını destekliyor mu Seçenekler. Yerleşik diğer seçenekler, kullanıcı adı belirteçleri, X.509 sertifikaları, SAML belirteçleri ve CardSpace kart içerir, ancak özel kimlik doğrulama mekanizmaları de tanımlanabilir.  
  
### <a name="security-impersonation"></a>Güvenlik: kimliğe bürünme  
 ASP.NET kimlik öğesi, bir ASP.NET Web hizmeti belirli bir kullanıcının kimliğine bürünmek için yapılabilir veya hangi kullanıcının kimlik bilgilerinin geçerli istekle sağlanan sağlar. Bu öğe, kimliğe bürünme yapılandırmak için kullanılan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ASP.NET uyumluluk modunda çalışan uygulamalar.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Yapılandırma sistemi kimliğine bürünmek için belirli bir kullanıcı atamak için kendi kimlik öğesi sağlar. Ayrıca, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemciler ve hizmetler bağımsız olarak yapılandırılabilir kimliğe bürünme için. İstemciler, istekleri aktarırken geçerli kullanıcının kimliğine bürünmek için yapılandırılabilir.  
  
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
 Erişim denetim listeleri (ACL'ler) .asmx dosyalara erişimi kısıtlamak için kullanılabilir. Ancak, ACL'ler [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] .svc dosyalarını yok sayılır dışında ASP.NET uyumluluk modunda.  
  
### <a name="security-role-based-authorization"></a>Güvenlik: Rol tabanlı yetkilendirme  
 IIS Windows kimlik doğrulaması seçeneği birlikte ASP.NET yapılandırma dil tarafından sağlanan yetkilendirme öğesi ile kullanıcılara atanmış olan Windows gruplarını temel alan ASP.NET Web Hizmetleri için rol tabanlı yetkilendirme kolaylaştırmak için kullanılabilir . ASP.NET 2.0 sunulan daha genel bir rol tabanlı yetkilendirme mekanizması: rol sağlayıcıları.  
  
 Rol sağlayıcıları tüm atanmış bir kullanıcı için rolleri hakkında enquiring için temel bir arabirim uygulamak, ancak farklı bir kaynaktan bu bilgileri almak nasıl her rol sağlayıcısı bilir sınıflarıdır. ASP.NET 2.0 rol atamalarını Windows Server 2003 Yetkilendirme Yöneticisi'nden alabilirsiniz rol atamalarını bir Microsoft SQL Server veritabanı ve başka alabilen bir rol sağlayıcı sağlar.  
  
 Rol sağlayıcı mekanizması gerçekte ASP.NET bağımsız olarak herhangi bir .NET uygulamasında kullanılabilir dahil olmak üzere bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulama. Aşağıdaki örnek yapılandırma için bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulama nasıl gösterir ASP.NET rol sağlayıcıyı kullanımı yoluyla bir seçeneğe <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>.  
  
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
 En önemli yenilikler biri [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] talepleri temelinde korunan kaynaklara erişimi yetkilendirmek için kapsamlı desteğidir. Talep türü, bir hak ve bir değer, bir sürücüleri lisans, örneğin oluşur. Biri taşıyıcı'nin doğum tarihi olan taşıyıcı hakkında talepler kümesi kolaylaştırır. Talep değeri sürücünün doğum tarihi olsa da bu talep türünü doğum tarihi, ' dir. Bir talep taşıyıcı confers sağ taşıyıcı talebin değeri ile neler yapabileceğinizi belirtir. Doğum tarihi sürücünün talep durumunda elinde hangisi: Doğum tarihi ancak, örneğin olamaz, sürücü sahip, üzerinde değişiklik. Talep tabanlı yetkilendirme, rol talep türü olduğundan rol tabanlı bir yetkilendirme barındırır.  
  
 Talep tabanlı yetkilendirme gerekliliklerini işlemin ve bu karşılaştırma sonucunu bağlı olarak talepler kümesi karşılaştırma vererek ya da işlemi erişimi reddetme gerçekleştirilir. İçinde [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], bir değer atayarak talep tabanlı yetkilendirme, bir kez yeniden çalıştırmak için bir sınıf belirtebilir `ServiceAuthorizationManager` özelliği <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>.  
  
```xml  
<behaviors>  
     <behavior name='ServiceBehavior'>  
     <serviceAuthorization   
     serviceAuthorizationManagerType=  
                   'Service.AccessChecker, Service' />  
     </behavior>  
</behaviors>  
```  
  
 Talep tabanlı yetkilendirme çalıştırmak için kullanılan sınıfları öğesinden türetilmelidir <xref:System.ServiceModel.ServiceAuthorizationManager>, geçersiz kılmak için yalnızca bir yöntemi olan `AccessCheck()`. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Hizmet işlemini çağrılır ve sağlar, bu yöntemi çağırır bir <xref:System.ServiceModel.OperationContext> kullanıcı talebini sahip nesne, kendi `ServiceSecurityContext.AuthorizationContext` özelliği. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]hangi güvenlik belirteci kullanıcı hakkında talepleri atayarak iş bırakır kimlik doğrulaması için sağlanan kullanıcı mu bu talep ilgili işlem için yeterli olup olmadığını değerlendirmek, görev.  
  
 Olduğunu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] talep otomatik olarak derler talep tabanlı yetkilendirme kodu kimlik doğrulama mekanizmasını tamamen bağımsız yaptığından güvenlik herhangi bir tür yüksek oranda önemli bir yenilik belirtecidir. Bunun aksine, ACL'ler ya da roller ASP.NET kullanarak yetkilendirmeyi yakından Windows kimlik doğrulaması olarak bağlıdır.  
  
### <a name="security-confidentiality"></a>Güvenlik: gizlilik  
 ASP.NET Web Hizmetleri ile değiştirilen iletilerin gizliliğini aktarım düzeyinde uygulamayı IIS içinde Güvenli Köprü Metni Aktarım Protokolü (HTTPS) kullanacak şekilde yapılandırarak güvence altına alınabilir. Aynı yapılabilir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] IIS içinde barındırılan uygulamalar. Ancak, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] IIS dışında barındırılan uygulamalara güvenli aktarım protokolünü kullanmak üzere yapılandırılabilir. Daha da önemlisi, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulamalar da bunlar, WS-güvenlik protokolünü kullanarak taşınacağını önce iletileri güvenli şekilde yapılandırılabilir. WS güvenliği kullanarak ileti gövdesi güvenliğini sağlama ilkemiz aracılar son hedefine ulaşmadan önce iletilmesi izin verir.  
  
## <a name="globalization"></a>Genelleştirme  
 ASP.NET yapılandırma dil tek tek Hizmetleri için kültür belirtmenize olanak tanır. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Bu yapılandırma ayarı dışında ASP.NET uyumluluk modunda desteklemiyor. Yerelleştirme için bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] değil ASP.NET Uyumluluk modunu kullanmak, hizmet türü kültüre özgü derlemeler içine derlemek ve ayrı kültüre özgü uç noktaları her kültüre özgü derlemesi için hizmet.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ASP.NET Web Hizmetlerini Amaç ve Kullanılan Standartları Temel Alarak WCF ile Karşılaştırma](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used.md)
