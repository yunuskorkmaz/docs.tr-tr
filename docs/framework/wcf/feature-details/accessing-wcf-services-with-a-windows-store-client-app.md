---
title: WCF Hizmetlerine Windows Mağazası İstemci Uygulaması ile Erişme
ms.date: 03/30/2017
ms.assetid: e2002ef4-5dee-4a54-9d87-03b33d35fc52
ms.openlocfilehash: b4b91c103aa91e3b2c9e811c642a8347c7db1a88
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185477"
---
# <a name="accessing-wcf-services-with-a-windows-store-client-app"></a>WCF Hizmetlerine Windows Mağazası İstemci Uygulaması ile Erişme
Windows 8, Windows Mağazası uygulamaları adı verilen yeni bir uygulama türünü sunar. Bu uygulamalar dokunmatik ekran arabirimi etrafında tasarlanmıştır. .NET Framework 4.5, Windows Mağazası uygulamalarının WCF hizmetlerini aramasını sağlar.  
  
## <a name="wcf-support-in-windows-store-applications"></a>Windows Mağazası Uygulamalarında WCF Desteği  
 WCF işlevselliğinin bir alt kümesi bir Windows Mağazası uygulaması içinden edinilebilir, daha fazla ayrıntı için aşağıdaki bölümlere bakın.  
  
> [!IMPORTANT]
> WCF tarafından maruz kalanlar yerine WinRT sendikasyon API'lerini kullanın. Daha fazla bilgi için bkz: [WinRT Sendikasyon API](xref:Windows.Web.Syndication)  
  
> [!WARNING]
> Windows Runtime Bileşenine web hizmeti başvurusu eklemek için Hizmet Başvurusu Ekle'nin kullanılması desteklenmez.  
  
### <a name="supported-bindings"></a>Desteklenen Ciltler  
 Aşağıdaki WCF bağlamaları Windows Mağazası Uygulamalarında desteklenir:  
  
1. <xref:System.ServiceModel.BasicHttpBinding>  
  
2. <xref:System.ServiceModel.NetTcpBinding>  
  
3. <xref:System.ServiceModel.NetHttpBinding>  
  
4. <xref:System.ServiceModel.Channels.CustomBinding>
  
 Windows Mağazası Uygulamalarında aşağıdaki bağlama öğeleri desteklenir  
  
1. <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
  
2. <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
  
3. <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>  
  
4. <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
5. <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
6. <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
7. <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
8. <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
9. <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
 Hem Metin hem de İkili kodlamalar desteklenir. Tüm WCF aktarım modları desteklenir. Daha fazla bilgi için bkz: [Akış İleti Aktarımı](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md).  
  
### <a name="add-service-reference"></a>Hizmet Başvurusu Ekle  
 Bir Windows Mağazası uygulamasından WCF hizmetini aramak için Visual Studio 2012'nin Hizmet Başvurusu Ekle özelliğini kullanın. Bir Windows Mağazası uygulaması içinde yapıldığında Hizmet Başvurusu Ekle işlevinde birkaç değişiklik fark edeceksiniz. İlk olarak hiçbir yapılandırma dosyası oluşturulur. Windows Mağazası uygulamaları yapılandırma dosyalarını kullanmadığından, kod olarak yapılandırılmaları gerekir. Bu yapılandırma kodu, Hizmet Başvurusu Ekle tarafından oluşturulan References.cs dosyasında bulunabilir. Bu dosyayı görmek için çözüm gezgininde "Tüm Dosyaları Göster"i seçtiğinizden emin olun. Dosya, Hizmet Başvuruları altında ve ardından proje içinde Reference.svcmap düğümleri altında yer alacaktır. Bir Windows Mağazası uygulaması içinde WCF hizmetleri için oluşturulan tüm işlemler, Görev tabanlı eşzamanlı desen kullanılarak eşzamanlı olacaktır. Daha fazla bilgi için [Bkz. Async Görevleri - Görevlerile Eşzamanlı Programlamayı Basitleştirin.](https://docs.microsoft.com/archive/msdn-magazine/2010/september/async-tasks-simplify-asynchronous-programming-with-tasks)  
  
 Yapılandırma artık kod olarak oluşturulduğundan, Reference.cs dosyasında yapılan tüm değişiklikler, hizmet başvurusu her güncelleştirilse üzerine yazılır. Bu durumu gidermek için yapılandırma kodu, istemci proxy sınıfınızda uygulayabileceğiniz kısmi bir yöntem içinde oluşturulur. Kısmi yöntem aşağıdaki gibi beyan edilir:  
  
```csharp  
static partial void Configure(System.ServiceModel.Description.ServiceEndpoint serviceEndpoint,  
            System.ServiceModel.Description.ClientCredentials clientCredentials);  
```  
  
 Daha sonra bu kısmi yöntemi uygulayabilir ve istemci proxy sınıfınızdaki bağlama veya bitiş noktasını aşağıdaki gibi değiştirebilirsiniz:  
  
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
 Aşağıdaki serializers Windows Mağazası uygulamalarında desteklenir:  
  
1. DataContractSerializer  
  
2. DataContractJsonSerializer  
  
3. Xmlserializer  
  
> [!WARNING]
> XmlDictionaryWriter.Write(DateTime) şimdi bir dize olarak DateTime nesnesi yazar.  
  
### <a name="security"></a>Güvenlik  

Aşağıdaki güvenlik modları Windows Mağazası uygulamalarında desteklenir:
  
1. <xref:System.ServiceModel.SecurityMode.None>  
  
2. <xref:System.ServiceModel.SecurityMode.Transport>  
  
3. <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>
  
4. <xref:System.ServiceModel.SecurityMode.Message>
  
Aşağıdaki istemci kimlik bilgileri türleri Windows Mağazası uygulamalarında desteklenir:
  
1. None  
  
2. Temel  
  
3. Özet  
  
4. Anlaşma  
  
5. NTLM  
  
6. Windows  
  
7. Kullanıcı adı (İleti Güvenliği)  
  
8. Windows (Aktarım Güvenliği)  
  
 Windows Mağazası uygulamalarının varsayılan Windows kimlik bilgilerine erişebilmesi ve göndermesi için bu işlevselliği Package.appmanifest dosyasında etkinleştirmeniz gerekir. Bu dosyayı açın ve Özellikler sekmesini seçin ve "Varsayılan Windows Kimlik Bilgileri"ni seçin. Bu, uygulamanın etki alanı kimlik bilgileri gerektiren intranet kaynaklarına bağlanmasını sağlar.  
  
> [!IMPORTANT]
> Windows Mağazası uygulamalarının makineler arası arama yapabilmesi için "Ev/İş Ağı" adı verilen başka bir özelliği etkinleştirmeniz gerekir. Bu ayar, Özellikler sekmesi altındaki Package.appmanifest dosyasında da yer alıyor. Ev/İş Ağı onay kutusunu seçin. Bu, uygulamanızın kullanıcının ev ve iş gibi güvenilir yerlerinin ağlarına gelen ve giden erişim sağlar. Gelen kritik bağlantı noktaları her zaman engellenir. Internet'teki hizmetlere erişmek için Internet (İstemci) özelliğini de etkinleştirmeniz gerekir.  
  
### <a name="misc"></a>Çeşitli  
 Aşağıdaki sınıfların kullanımı Windows Mağazası Uygulamaları için desteklenir:  
  
1. <xref:System.ServiceModel.ChannelFactory>  
  
2. <xref:System.ServiceModel.DuplexChannelFactory%601>
  
3. <xref:System.ServiceModel.CallbackBehaviorAttribute>  
  
### <a name="defining-service-contracts"></a>Hizmet Sözleşmelerinin Tanımlanması  
 Yalnızca görev tabanlı async deseni kullanarak eşzamanlı hizmet işlemlerini tanımlamanızı öneririz. Bu, Windows Mağazası uygulamalarının bir hizmet işlemini ararken yanıt vermeye devam edilmesini sağlar.  
  
> [!WARNING]
> Senkron bir işlem tanımlarsanız özel durum atılmazken, yalnızca eşzamanlı işlemleri tanımlamanız önerilir.  
  
### <a name="calling-wcf-services-from-windows-store-applications"></a>Windows Mağazası Uygulamalarından WCF Hizmetlerini Arama  
 Daha önce de belirtildiği gibi, oluşturulan proxy sınıfında getBindingForEndpoint yönteminde tüm yapılandırma kod içinde yapılmalıdır. Bir hizmet işlemini çağırmak, aşağıdaki kod snippet'inde gösterildiği gibi görev tabanlı eşyoknöz yöntemi çağırmakla aynı şekilde yapılır.  
  
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
  
 Asynchronous metod'u ararken asynchronous arama ve bekleyen anahtar kelime yönteminde async anahtar kelimesinin kullanımına dikkat edin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Mağazası Apps Blog WCF](https://docs.microsoft.com/archive/blogs/piyushjo/wcf-in-windows-8-metro-styled-apps-absolutely-supported)
- [WCF Windows Mağazası İstemcileri ve Güvenliği](https://docs.microsoft.com/archive/blogs/piyushjo/calling-a-wcf-service-from-a-metro-application-adding-security)
- [Windows Mağazası Uygulamaları ve Çapraz Makine Aramaları](https://docs.microsoft.com/archive/blogs/piyushjo/calling-a-wcf-service-from-a-metro-application-cross-machine-scenario)
- [Windows Mağazası Uygulamasından Azure'da Dağıtılan Bir WCF Hizmeti çağırma](https://docs.microsoft.com/archive/blogs/piyushjo/calling-a-wcf-service-from-a-metro-application-cross-machine-scenario)
- [WCF Güvenliğini Programlama](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)
- [Bağlamalar](../../../../docs/framework/wcf/bindings.md)
