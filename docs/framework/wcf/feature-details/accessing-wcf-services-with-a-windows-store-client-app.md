---
title: "WCF Hizmetlerine Windows Mağazası İstemci Uygulaması ile Erişme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e2002ef4-5dee-4a54-9d87-03b33d35fc52
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: df5e05b1896ee272e286102a6c9433fad51b3c98
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="accessing-wcf-services-with-a-windows-store-client-app"></a>WCF Hizmetlerine Windows Mağazası İstemci Uygulaması ile Erişme
Windows 8 uygulamanın Windows mağazası uygulamaları adı verilen yeni bir türü sunar. Bu uygulamalar, dokunmatik ekran arabirimini tasarlanmıştır. .NET framework 4.5, WCF hizmetleri çağırmak Windows mağazası uygulamaları etkinleştirir.  
  
## <a name="wcf-support-in-windows-store-applications"></a>Windows mağazası uygulamalarında WCF desteği  
 WCF işlevlerinin bir alt kümesini bir Windows mağazası uygulama içinde kullanılabilir, daha fazla ayrıntı için aşağıdaki bölümlere bakın.  
  
> [!IMPORTANT]
>  WCF tarafından kullanıma sunulan yerine WinRT dağıtım API'leri kullanın. Daha fazla bilgi için [WinRT dağıtım API](http://go.microsoft.com/fwlink/?LinkId=236265)  
  
> [!WARNING]
>  Windows çalışma zamanı bileşeni bir web hizmeti başvuru eklemek için hizmet Başvurusu Ekle kullanımı desteklenmiyor.  
  
### <a name="supported-bindings"></a>Desteklenen bağlamaları  
 Aşağıdaki WCF bağlamaları Windows mağazası uygulamalarında desteklenir:  
  
1.  <xref:System.ServiceModel.BasicHttpBinding>  
  
2.  <xref:System.ServiceModel.NetTcpBinding>  
  
3.  <xref:System.ServiceModel.NetHttpBinding>  
  
4.  <xref:System.ServiceModel.Channels.CustomBinding>
  
 Aşağıdaki bağlama öğeleri Windows mağazası uygulamalarında desteklenir  
  
1.  <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
  
2.  <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
  
3.  <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>  
  
4.  <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
5.  <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
6.  <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
7.  <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
8.  <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
9. <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
 Metin ve ikili kodlamaları desteklenir. Tüm WCF aktarım modlarını desteklenir. Daha fazla bilgi için [ileti aktarma akışı](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md).  
  
### <a name="add-service-reference"></a>Hizmet Başvurusu Ekle  
 Bir Windows mağazası uygulamasından bir WCF hizmetini çağırmak için Visual Studio 2012'in hizmet Başvurusu Ekle özelliğini kullanın. Hizmet bir Windows mağazası uygulama içinde işiniz bittiğinde Başvurusu Ekle işlevselliğini birkaç değişiklik fark edersiniz. Önce herhangi bir yapılandırma dosyası oluşturulur. Kodda yapılandırılmalıdır için Windows mağazası uygulamaları yapılandırma dosyaları kullanmayın. Bu yapılandırma kodunu hizmet Başvurusu Ekle tarafından oluşturulan References.cs dosyasında bulunabilir. Bu dosyayı görmek için Çözüm Gezgini'nde "Tüm dosyaları göster" seçmek emin olun. Dosya hizmeti başvuruları ve sonra projeyi içinde Reference.svcmap düğümleri altında yer alır. Windows mağazası uygulaması içinde WCF hizmetleri için oluşturulan tüm işlemleri görev tabanlı zaman uyumsuz desen kullanarak zaman uyumsuz olacaktır. Daha fazla bilgi için bkz: [görev tabanlı zaman uyumsuz desen](http://msdn.microsoft.com/magazine/ff959203.aspx).  
  
 Yapılandırma şimdi kodda oluşturulduğundan, hizmet başvurusu her güncelleştirildiğinde Reference.cs dosyasında yapılan değişiklikler üzerine. Bu durumu düzeltmek için istemci proxy sınıfınızda uygulayabileceğiniz bir kısmi yöntemi içinde yapılandırma kodu oluşturulur. Kısmi yöntemini aşağıdaki gibi bildirdi:  
  
```csharp  
static partial void Configure(System.ServiceModel.Description.ServiceEndpoint serviceEndpoint,  
            System.ServiceModel.Description.ClientCredentials clientCredentials);  
```  
  
 Ardından, kısmi bu yöntemi uygulaması ve bağlama veya uç nokta istemci proxy sınıfınızda aşağıdaki gibi değiştirin:  
  
```csharp  
public partial class Service1Client : System.ServiceModel.ClientBase<MetroWcfClient.ServiceRefMultiEndpt.IService1>, MetroWcfClient.ServiceRefMultiEndpt.IService1  
    {   
        static partial void Configure(System.ServiceModel.Description.ServiceEndpoint serviceEndpoint,   
            System.ServiceModel.Description.ClientCredentials clientCredentials)  
        {  
            if (serviceEndpoint.Name ==   
                    ServiceRefMultiEndpt.Service1Client.EndpointConfiguration.BasicHttpBinding_IService1.ToString())  
            {  
                serviceEndpoint.Binding.SendTimeout = new System.TimeSpan(0, 1, 0);  
            }  
            else if (serviceEndpoint.Name ==   
                    ServiceRefMultiEndpt.Service1Client.EndpointConfiguration.BasicHttpBinding_IService11.ToString())  
            {  
                serviceEndpoint.Binding.SendTimeout = new System.TimeSpan(0, 1, 0);  
                clientCredentials.UserName.UserName = "username1";  
                clientCredentials.UserName.Password = "password";  
            }  
            else if (serviceEndpoint.Name ==   
                    ServiceRefMultiEndpt.Service1Client.EndpointConfiguration.NetTcpBinding_IService1.ToString())  
            {  
                serviceEndpoint.Binding.Name = "MyTcpBinding";  
                serviceEndpoint.Address = new System.ServiceModel.EndpointAddress("net.tcp://localhost/tcp");  
            }  
        }  
    }  
```  
  
### <a name="serialization"></a>Serileştirme  
 Aşağıdaki serileştiricileri Windows mağazası uygulamalarında desteklenir:  
  
1.  DataContractSerializer  
  
2.  DataContractJsonSerializer  
  
3.  XmlSerializer  
  
> [!WARNING]
>  XmlDictionaryWriter.Write(DateTime) şimdi DateTime nesnesi bir dize yazar.  
  
### <a name="security"></a>Güvenlik  
 Aşağıdaki güvenlik modu Windows mağazası uygulamalarında desteklenir  
  
1.  <xref:System.ServiceModel.SecurityMode.None>  
  
2.  <xref:System.ServiceModel.SecurityMode.Transport>  
  
3.  <!--zz <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredentials> --> `System.ServiceModel.SecurityMode.TransportWithMessageCredentials`
  
4.  <!--zz <xref:System.ServiceModel.SecurityMode.TransportCredentialOnly>  --> `System.ServiceModel.SecurityMode.TransportCredentialOnly`
  
 Aşağıdaki istemci kimlik bilgisi türlerinin Windows mağazası uygulamalarında desteklenir  
  
1.  Yok.  
  
2.  Temel  
  
3.  Özet  
  
4.  Anlaşma  
  
5.  NTLM  
  
6.  Windows  
  
7.  Kullanıcı adı (ileti güvenliği)  
  
8.  Windows (taşıma güvenliği)  
  
 Erişim ve varsayılan Windows kimlik bilgileri göndermek Windows mağazası uygulamaları Package.appmanifest dosyası içinde bu işlevi etkinleştirmeniz gerekir. Bu dosyayı açın ve yetenekleri sekmesini seçin ve "Varsayılan Windows kimlik bilgileri" seçin. Bu etki alanı kimlik bilgileri gerektiren intranet kaynaklarına bağlanmak uygulama sağlar.  
  
> [!IMPORTANT]
>  Çapraz makine çağrı yapmak Windows mağazası uygulamaları için sırayla "Ev/iş ağı" adlı başka bir özelliği etkinleştirmeniz gerekir. Bu ayar, Özellikleri sekmesi altında Package.appmanifest dosyasında değildir. Ev/iş ağı onay kutusunu seçin. Bu kullanıcının ağlara gelen ve giden erişim yerler ev ve iş gibi güvenilir uygulamanızı sağlar. Kritik gelen bağlantı noktalarının her zaman engellenir. Internet'te hizmetlerine erişmek için Internet (istemci) özelliği da etkinleştirmeniz gerekir.  
  
### <a name="misc"></a>Çeşitli  
 Aşağıdaki sınıflar kullanımını Windows mağazası uygulamaları için desteklenir:  
  
1.  <xref:System.ServiceModel.ChannelFactory>  
  
2.  <!--zz <xref:System.ServiceModel.DuplexChannelFactory> --> `System.ServiceModel.DuplexChannelFactory`
  
3.  <xref:System.ServiceModel.CallbackBehaviorAttribute>  
  
### <a name="defining-service-contracts"></a>Hizmet sözleşmelerini tanımlama  
 Görev tabanlı zaman uyumsuz desen kullanarak zaman uyumsuz hizmet işlemleri yalnızca tanımlama öneririz. Bu, bir hizmet işlemi çağrılırken Windows mağazası uygulamaları yanıt verebilir durumda kalmasını sağlar.  
  
> [!WARNING]
>  Eşzamanlı bir işlem tanımlarsanız, hiçbir özel durum olsa da, yalnızca zaman uyumsuz işlemleri tanımlamak için kesinlikle önerilir.  
  
### <a name="calling-wcf-services-from-windows-store-applications"></a>WCF hizmetlerine Windows mağazası uygulamasından çağırma  
 Önceden belirtildiği gibi tüm yapılandırma oluşturulan proxy sınıfı GetBindingForEndpoint yönteminde kodda yapılmalıdır. Bir hizmet işlemi çağrılırken, aşağıdaki kod parçacığında gösterildiği gibi tüm görev tabanlı zaman uyumsuz yöntem çağırma aynı yapılır.  
  
```csharp  
void async SomeMethod()  
{  
    ServiceClient proxy = new ServiceClient();  
    Task<T> results = await proxy.CallAsync(param1, param2);  
    T result = results.Result;  
    if (result.Success)  
    {  
       // Do something with result  
    }  
}  
```  
  
 Async anahtar sözcüğü zaman uyumsuz çağrı ve bekleme anahtar zaman uyumsuz yöntem çağrılırken hale yöntemine kullanımına dikkat edin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows mağazası uygulamaları günlüğündeki WCF](http://blogs.msdn.com/b/piyushjo/archive/2011/09/22/wcf-in-win8-metro-styled-apps-absolutely-supported.aspx)  
 [WCF Windows mağazası istemcileri ve güvenlik](http://blogs.msdn.com/b/piyushjo/archive/2011/10/11/calling-a-wcf-service-from-a-metro-application-adding-security.aspx)  
 [Windows mağazası uygulamaları ve çapraz makine çağrıları](http://blogs.msdn.com/b/piyushjo/archive/2011/10/22/calling-a-wcf-service-from-a-metro-application-cross-machine-scenario.aspx)  
 [Bir Windows mağazası uygulamasından azure'da dağıtılan bir WCF Hizmeti çağırma](http://blogs.msdn.com/b/piyushjo/archive/2011/10/22/calling-a-wcf-service-from-a-metro-application-cross-machine-scenario.aspx)  
 [WCF Güvenliğini Programlama](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)  
 [Bağlamalar](../../../../docs/framework/wcf/bindings.md)
