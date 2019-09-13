---
title: WCF Hizmetlerine Windows Mağazası İstemci Uygulaması ile Erişme
ms.date: 03/30/2017
ms.assetid: e2002ef4-5dee-4a54-9d87-03b33d35fc52
ms.openlocfilehash: 7a50454c5189c48704adfaaed2c90d2638dd677f
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928968"
---
# <a name="accessing-wcf-services-with-a-windows-store-client-app"></a>WCF Hizmetlerine Windows Mağazası İstemci Uygulaması ile Erişme
Windows 8, Windows Mağazası uygulamaları adlı yeni bir uygulama türü sunar. Bu uygulamalar dokunmatik ekran arabirimi etrafında tasarlanmıştır. .NET Framework 4,5, Windows Mağazası uygulamalarının WCF hizmetlerini çağırmasını sağlar.  
  
## <a name="wcf-support-in-windows-store-applications"></a>Windows Mağazası uygulamalarında WCF desteği  
 WCF işlevselliğinin bir alt kümesi bir Windows Mağazası uygulaması içinden edinilebilir, daha fazla ayrıntı için aşağıdaki bölümlere bakın.  
  
> [!IMPORTANT]
> WCF tarafından sunulmayan yerine WinRT dağıtım API 'Lerini kullanın. Daha fazla bilgi için bkz. [WinRT dağıtım API 'si](https://go.microsoft.com/fwlink/?LinkId=236265)  
  
> [!WARNING]
> Bir Windows Çalışma Zamanı bileşenine Web hizmeti başvurusu eklemek için Hizmet Başvurusu Ekle kullanmak desteklenmez.  
  
### <a name="supported-bindings"></a>Desteklenen bağlamalar  
 Windows Mağazası uygulamalarında aşağıdaki WCF bağlamaları desteklenir:  
  
1. <xref:System.ServiceModel.BasicHttpBinding>  
  
2. <xref:System.ServiceModel.NetTcpBinding>  
  
3. <xref:System.ServiceModel.NetHttpBinding>  
  
4. <xref:System.ServiceModel.Channels.CustomBinding>
  
 Windows Mağazası uygulamalarında aşağıdaki bağlama öğeleri desteklenir  
  
1. <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
  
2. <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
  
3. <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>  
  
4. <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
5. <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
6. <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
7. <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
8. <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
9. <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
 Hem metin hem de Ikili kodlamalar desteklenir. Tüm WCF aktarım modları desteklenir. Daha fazla bilgi için bkz. [akış Ileti aktarımı](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md).  
  
### <a name="add-service-reference"></a>Hizmet Başvurusu Ekle  
 Bir Windows Mağazası uygulamasından bir WCF hizmetini çağırmak için, Visual Studio 2012 Hizmet Başvurusu Ekle özelliğini kullanın. Windows Mağazası uygulamasında yapıldığında Hizmet Başvurusu Ekle işlevselliğinde birkaç değişiklik olduğunu fark edeceksiniz. İlk olarak hiçbir yapılandırma dosyası oluşturulmaz. Windows Mağazası uygulamaları yapılandırma dosyalarını kullanmaz, bu nedenle kodda yapılandırılması gerekir. Bu yapılandırma kodu, Hizmet Başvurusu Ekle tarafından oluşturulan References.cs dosyasında bulunabilir. Bu dosyayı görmek için Çözüm Gezgini 'nde "tüm dosyaları göster" seçeneğini belirlediğinizden emin olun. Dosya, hizmet başvurularının altında bulunur ve ardından proje içindeki. svcmap düğümlerine başvuracaktır. Bir Windows Mağazası uygulaması içindeki WCF Hizmetleri için oluşturulan tüm işlemler, görev tabanlı zaman uyumsuz model kullanılarak zaman uyumsuz olacaktır. Daha fazla bilgi için bkz. [zaman uyumsuz görevler-görevlerle zaman uyumsuz programlamayı kolaylaştırın](https://msdn.microsoft.com/magazine/ff959203.aspx).  
  
 Yapılandırma artık kodda oluşturulduğundan, hizmet başvurusunun her güncelleştirildiği her seferinde Reference.cs dosyasında yapılan tüm değişikliklerin üzerine yazılacak. Bu durumu gidermek için yapılandırma kodu, istemci proxy sınıfınız içinde uygulayabileceğiniz kısmi bir yöntemde oluşturulur. Kısmi Yöntem şu şekilde bildirilmiştir:  
  
```csharp  
static partial void Configure(System.ServiceModel.Description.ServiceEndpoint serviceEndpoint,  
            System.ServiceModel.Description.ClientCredentials clientCredentials);  
```  
  
 Daha sonra bu kısmi yöntemi uygulayabilir ve istemci proxy sınıfınızın bağlama veya uç noktasını aşağıdaki şekilde değiştirebilirsiniz:  
  
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
 Windows Mağazası uygulamalarında aşağıdaki serileştiriciler desteklenir:  
  
1. DataContractSerializer  
  
2. DataContractJsonSerializer  
  
3. Çağrılamıyor  
  
> [!WARNING]
> XmlDictionaryWriter. Write (DateTime) şimdi DateTime nesnesini bir dize olarak yazar.  
  
### <a name="security"></a>Güvenlik  

Windows Mağazası uygulamalarında aşağıdaki güvenlik modları desteklenir:
  
1. <xref:System.ServiceModel.SecurityMode.None>  
  
2. <xref:System.ServiceModel.SecurityMode.Transport>  
  
3. <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>
  
4. <xref:System.ServiceModel.SecurityMode.Message>
  
Aşağıdaki istemci kimlik bilgisi türleri Windows Mağazası uygulamalarında desteklenir:
  
1. Yok.  
  
2. Temel  
  
3. bilgisi  
  
4. 'Nin  
  
5. NT  
  
6. Windows  
  
7. Kullanıcı adı (Ileti güvenliği)  
  
8. Windows (taşıma güvenliği)  
  
 Windows Mağazası uygulamalarının varsayılan Windows kimlik bilgilerini erişmesi ve gönderebilmesi için, bu işlevselliği Package. AppManifest dosyası içinde etkinleştirmeniz gerekir. Bu dosyayı açın ve yetenekler sekmesini seçin ve "varsayılan Windows kimlik bilgileri" ni seçin. Bu, uygulamanın etki alanı kimlik bilgileri gerektiren intranet kaynaklarına bağlanmasına izin verir.  
  
> [!IMPORTANT]
> Windows Mağazası uygulamalarının çapraz makine çağrıları yapması için, "Ev/Iş ağı" adlı başka bir özelliği etkinleştirmeniz gerekir. Bu ayar ayrıca Yetenekler sekmesi altındaki Package. AppManifest dosyasında bulunur. Ev/Iş ağı onay kutusunu seçin. Bu, uygulamanıza giriş ve çalışma gibi kullanıcının güvenilen yerlerinin ağlarına gelen ve giden erişim sağlar. Gelen kritik bağlantı noktaları her zaman engellenir. Internet 'teki hizmetlere erişim için Internet (Istemci) özelliğini de etkinleştirmeniz gerekir.  
  
### <a name="misc"></a>Çeşitli  
 Aşağıdaki sınıfların kullanımı Windows Mağazası uygulamaları için desteklenir:  
  
1. <xref:System.ServiceModel.ChannelFactory>  
  
2. <xref:System.ServiceModel.DuplexChannelFactory%601>
  
3. <xref:System.ServiceModel.CallbackBehaviorAttribute>  
  
### <a name="defining-service-contracts"></a>Hizmet sözleşmelerini tanımlama  
 Yalnızca görev tabanlı zaman uyumsuz model kullanarak zaman uyumsuz hizmet işlemlerini tanımlamayı öneririz. Bu, bir hizmet işlemi çağrılırken Windows Mağazası uygulamalarının yanıt vermeye devam eder.  
  
> [!WARNING]
> Zaman uyumlu bir işlem tanımlarsanız hiçbir özel durum oluşturulmaz, ancak yalnızca zaman uyumsuz işlemler tanımlamanız önerilir.  
  
### <a name="calling-wcf-services-from-windows-store-applications"></a>Windows Mağazası uygulamalarından WCF Hizmetleri çağırma  
 Oluşturulan proxy sınıfında GetBindingForEndpoint yöntemindeki kodda tüm yapılandırma yapılmalıdır. Bir hizmet işleminin çağrılması, aşağıdaki kod parçacığında gösterildiği gibi herhangi bir görev tabanlı zaman uyumsuz yöntemi çağırma ile aynı şekilde yapılır.  
  
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
  
 Zaman uyumsuz çağrıyı yapan yöntemde async anahtar sözcüğünün kullanımını ve zaman uyumsuz yöntemi çağırırken await anahtar sözcüğünü kullanmayı unutmayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Mağazası uygulamaları blogu 'nda WCF](https://blogs.msdn.microsoft.com/piyushjo/2011/09/21/wcf-in-windows-8-metro-styled-apps-absolutely-supported/)
- [WCF Windows Mağazası Istemcileri ve güvenliği](https://blogs.msdn.microsoft.com/piyushjo/2011/10/11/calling-a-wcf-service-from-a-metro-application-adding-security/)
- [Windows Mağazası uygulamaları ve çapraz makine çağrıları](https://blogs.msdn.microsoft.com/piyushjo/2011/10/21/calling-a-wcf-service-from-a-metro-application-cross-machine-scenario/)
- [Azure 'da dağıtılan bir WCF hizmetini bir Windows Mağazası uygulamasından çağırma](https://blogs.msdn.com/b/piyushjo/archive/2011/10/22/calling-a-wcf-service-from-a-metro-application-cross-machine-scenario.aspx)
- [WCF Güvenliğini Programlama](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)
- [Bağlamalar](../../../../docs/framework/wcf/bindings.md)
