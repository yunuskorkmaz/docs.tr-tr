---
title: WCF Hizmetlerine Windows Mağazası İstemci Uygulaması ile Erişme
ms.date: 03/30/2017
ms.assetid: e2002ef4-5dee-4a54-9d87-03b33d35fc52
ms.openlocfilehash: a7d87e6014f26842c35b0d1bf5028682a4cf69e5
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59294866"
---
# <a name="accessing-wcf-services-with-a-windows-store-client-app"></a>WCF Hizmetlerine Windows Mağazası İstemci Uygulaması ile Erişme
Windows 8, Windows Store uygulamaları adı verilen bir uygulama yeni bir tür tanıtır. Bu uygulamaları dokunmatik ekran arabirimi geçici bir çözüm olarak tasarlanmıştır. .NET framework 4.5, WCF hizmetlerini çağırmak Windows Store uygulamaları etkinleştirir.  
  
## <a name="wcf-support-in-windows-store-applications"></a>Windows Store uygulamalarında WCF desteği  
 WCF işlevlerinin bir alt kümesini bir Windows Store uygulaması içinde bulunan, daha fazla ayrıntı için aşağıdaki bölümlere bakın.  
  
> [!IMPORTANT]
>  WCF tarafından kullanıma sunulan yerine WinRT dağıtım API'leri kullanın. Daha fazla bilgi edinmek, [WinRT dağıtım API](https://go.microsoft.com/fwlink/?LinkId=236265)  
  
> [!WARNING]
>  Bir Windows çalışma zamanı bileşeni için bir web hizmeti başvurusu eklemek için hizmet Başvurusu Ekle kullanımı desteklenmiyor.  
  
### <a name="supported-bindings"></a>Desteklenen bağlamaları  
 Aşağıdaki WCF bağlamaları, Windows Store uygulamalarında desteklenir:  
  
1. <xref:System.ServiceModel.BasicHttpBinding>  
  
2. <xref:System.ServiceModel.NetTcpBinding>  
  
3. <xref:System.ServiceModel.NetHttpBinding>  
  
4. <xref:System.ServiceModel.Channels.CustomBinding>
  
 Aşağıdaki bağlama öğeleri Windows Store uygulamalarında desteklenir.  
  
1. <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
  
2. <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
  
3. <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>  
  
4. <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
5. <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
6. <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
7. <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
8. <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
9. <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
 Hem metin ve ikili kodlamaları desteklenmektedir. Tüm WCF aktarma modları desteklenir. Daha fazla bilgi edinmek, [ileti aktarma akışı](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md).  
  
### <a name="add-service-reference"></a>Hizmet Başvurusu Ekle  
 Bir WCF hizmeti bir Windows Store uygulamasından çağırmak için Visual Studio 2012'in hizmet Başvurusu Ekle özelliğini kullanın. Hizmet bir Windows Store uygulaması içinde işiniz bittiğinde Başvurusu Ekle'nın bazı değişiklikler fark edeceksiniz. İlk yapılandırma dosyası yoksa oluşturulur. Kodda yapılandırılmalıdır için yapılandırma dosyaları, Windows Store uygulamaları kullanmayın. Bu yapılandırma kodu hizmet Başvurusu Ekle tarafından oluşturulan References.cs dosyasında bulunabilir. Bu dosyayı görmek için Çözüm Gezgini'nde "Tüm dosyaları göster" seçtiğinizden emin olun. Dosya hizmet başvuruları ve ardından Proje içinde Reference.svcmap düğümleri altında bulunur. WCF hizmetleri Windows Store uygulaması içinde oluşturulan tüm işlemler zaman uyumsuz görev tabanlı zaman uyumsuz desen kullanma olacaktır. Daha fazla bilgi için [zaman uyumsuz görevleri - görevler ile zaman uyumsuz programlama basitleştirmek](https://msdn.microsoft.com/magazine/ff959203.aspx).  
  
 Yapılandırma artık kod içinde oluşturulmuş olduğu için hizmet başvurusunu her güncelleştirildiğinde Reference.cs dosyasında yapılan değişikliklerin üzerine yazılır. Bu durumu ortadan kaldırmak için istemci proxy sınıfınızda uygulayabileceğiniz kısmi bir yöntemin içinde yapılandırma kod oluşturulur. Kısmi yöntem şu şekilde bildirilir:  
  
```csharp  
static partial void Configure(System.ServiceModel.Description.ServiceEndpoint serviceEndpoint,  
            System.ServiceModel.Description.ClientCredentials clientCredentials);  
```  
  
 Ardından, bu kısmi metodu uygulayın ve bağlama veya uç nokta istemci proxy Sınıfınız içinde aşağıdaki gibi değiştirin:  
  
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
 Aşağıdaki seri hale getiricileri genişletme, Windows Store uygulamalarında desteklenir:  
  
1. DataContractSerializer  
  
2. DataContractJsonSerializer  
  
3. XmlSerializer  
  
> [!WARNING]
>  XmlDictionaryWriter.Write(DateTime) şimdi bir DateTime nesnesini bir dize olarak yazar.  
  
### <a name="security"></a>Güvenlik  

Aşağıdaki güvenlik modu Windows Store uygulamalarında desteklenir:
  
1. <xref:System.ServiceModel.SecurityMode.None>  
  
2. <xref:System.ServiceModel.SecurityMode.Transport>  
  
3. <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>
  
4. <xref:System.ServiceModel.SecurityMode.Message>
  
Aşağıdaki istemci kimlik bilgisi türlerinin Windows Store uygulamalarında desteklenir:
  
1. Yok.  
  
2. Temel  
  
3. Özet  
  
4. Anlaşma  
  
5. NTLM  
  
6. Windows  
  
7. Kullanıcı adı (ileti güvenliği)  
  
8. Windows (aktarım güvenliği)  
  
 Erişim ve varsayılan Windows kimlik bilgilerini göndermek Windows Store uygulamaları için sırada Package.appmanifest dosyası içinde bu işlevi etkinleştirmeniz gerekir. Bu dosyayı açmak, özellikleri sekmesini seçin ve "Varsayılan Windows kimlik bilgileri" seçin. Bu, uygulama etki alanı kimlik bilgileri gerektiren intranet kaynaklarına bağlanmanıza imkan sağlar.  
  
> [!IMPORTANT]
>  Çapraz makine çağrıları yapmak Windows Store uygulamaları için sırayla "Ev/iş ağı" adlı başka bir özelliği etkinleştirmeniz gerekir. Bu ayar, Özellikler sekmesi altındaki Package.appmanifest dosyasındaki desteklenir. Ev/iş ağı onay kutusunu işaretleyin. Bu, kullanıcının ağlara gelen ve giden erişimi, ev ve iş yerleri gibi güvenilen uygulamanızı sağlar. Önemli gelen bağlantı noktalarının her zaman engellenir. Internet'te hizmetlerine erişmek için aynı zamanda Internet (istemci) özelliği etkinleştirmeniz gerekir.  
  
### <a name="misc"></a>Çeşitli  
 Aşağıdaki sınıflar kullanımı, Windows Store uygulamaları için desteklenir:  
  
1. <xref:System.ServiceModel.ChannelFactory>  
  
2. <xref:System.ServiceModel.DuplexChannelFactory%601>
  
3. <xref:System.ServiceModel.CallbackBehaviorAttribute>  
  
### <a name="defining-service-contracts"></a>Hizmet sözleşmelerini tanımlama  
 Yalnızca görev tabanlı zaman uyumsuz deseni kullanılarak zaman uyumsuz hizmet işlemleri tanımlama öneririz. Bu, Windows Store uygulamalarını bir hizmet işlemi çağrılırken yanıt verebilir durumda kalmasını sağlar.  
  
> [!WARNING]
>  Eşzamanlı bir işlem tanımlarsanız, hiçbir özel durum sırasında yalnızca zaman uyumsuz işlemleri tanımlamak için önemle tavsiye edilir.  
  
### <a name="calling-wcf-services-from-windows-store-applications"></a>WCF hizmetleri Windows Store uygulamalarından çağırma  
 Daha önce belirtildiği gibi tüm yapılandırma oluşturulan proxy sınıfı GetBindingForEndpoint yönteminde kodda yapılmalıdır. Bir hizmet işlemi çağrılırken, aşağıdaki kod parçacığında gösterildiği gibi tüm görev tabanlı zaman uyumsuz yöntem çağırma aynı gerçekleştirilir.  
  
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
  
 Async anahtar sözcüğü zaman uyumsuz yöntemini çağıran, zaman uyumsuz çağrı ve await anahtar sözcüğü yapmadan yöntemi kullanımına dikkat edin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF'de Windows Store Apps blogu](https://blogs.msdn.com/b/piyushjo/archive/2011/09/22/wcf-in-win8-metro-styled-apps-absolutely-supported.aspx)
- [WCF Windows Store istemcileri ve güvenlik](https://blogs.msdn.com/b/piyushjo/archive/2011/10/11/calling-a-wcf-service-from-a-metro-application-adding-security.aspx)
- [Windows Store uygulamaları ve çapraz makine çağrıları](https://blogs.msdn.com/b/piyushjo/archive/2011/10/22/calling-a-wcf-service-from-a-metro-application-cross-machine-scenario.aspx)
- [Azure'da Windows Store uygulamasında dağıtılan bir WCF Hizmeti çağırma](https://blogs.msdn.com/b/piyushjo/archive/2011/10/22/calling-a-wcf-service-from-a-metro-application-cross-machine-scenario.aspx)
- [WCF Güvenliğini Programlama](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)
- [Bağlamalar](../../../../docs/framework/wcf/bindings.md)
