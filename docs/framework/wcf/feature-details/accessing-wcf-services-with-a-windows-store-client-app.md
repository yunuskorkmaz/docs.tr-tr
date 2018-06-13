---
title: WCF Hizmetlerine Windows Mağazası İstemci Uygulaması ile Erişme
ms.date: 03/30/2017
ms.assetid: e2002ef4-5dee-4a54-9d87-03b33d35fc52
ms.openlocfilehash: aca0c4e4daecc1b7a2474130eb36b9ead1c538bd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33491965"
---
# <a name="accessing-wcf-services-with-a-windows-store-client-app"></a><span data-ttu-id="20aaa-102">WCF Hizmetlerine Windows Mağazası İstemci Uygulaması ile Erişme</span><span class="sxs-lookup"><span data-stu-id="20aaa-102">Accessing WCF Services with a Windows Store Client App</span></span>
<span data-ttu-id="20aaa-103">Windows 8 uygulamanın Windows mağazası uygulamaları adı verilen yeni bir türü sunar.</span><span class="sxs-lookup"><span data-stu-id="20aaa-103">Windows 8 introduces a new type of application called Windows Store applications.</span></span> <span data-ttu-id="20aaa-104">Bu uygulamalar, dokunmatik ekran arabirimini tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="20aaa-104">These applications are designed around a touch screen interface.</span></span> <span data-ttu-id="20aaa-105">.NET framework 4.5, WCF hizmetleri çağırmak Windows mağazası uygulamaları etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="20aaa-105">.NET Framework 4.5 enables Windows Store applications to call WCF services.</span></span>  
  
## <a name="wcf-support-in-windows-store-applications"></a><span data-ttu-id="20aaa-106">Windows mağazası uygulamalarında WCF desteği</span><span class="sxs-lookup"><span data-stu-id="20aaa-106">WCF Support in Windows Store Applications</span></span>  
 <span data-ttu-id="20aaa-107">WCF işlevlerinin bir alt kümesini bir Windows mağazası uygulama içinde kullanılabilir, daha fazla ayrıntı için aşağıdaki bölümlere bakın.</span><span class="sxs-lookup"><span data-stu-id="20aaa-107">A subset of WCF functionality is available from within a Windows Store application, see the following sections for more details.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="20aaa-108">WCF tarafından kullanıma sunulan yerine WinRT dağıtım API'leri kullanın.</span><span class="sxs-lookup"><span data-stu-id="20aaa-108">Use the WinRT syndication APIs instead of those exposed by WCF.</span></span> <span data-ttu-id="20aaa-109">Daha fazla bilgi için [WinRT dağıtım API](http://go.microsoft.com/fwlink/?LinkId=236265)</span><span class="sxs-lookup"><span data-stu-id="20aaa-109">For more information see, [WinRT Syndication API](http://go.microsoft.com/fwlink/?LinkId=236265)</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="20aaa-110">Windows çalışma zamanı bileşeni bir web hizmeti başvuru eklemek için hizmet Başvurusu Ekle kullanımı desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="20aaa-110">Using Add Service Reference to add a web service reference to a Windows Runtime Component isn’t supported.</span></span>  
  
### <a name="supported-bindings"></a><span data-ttu-id="20aaa-111">Desteklenen bağlamaları</span><span class="sxs-lookup"><span data-stu-id="20aaa-111">Supported Bindings</span></span>  
 <span data-ttu-id="20aaa-112">Aşağıdaki WCF bağlamaları Windows mağazası uygulamalarında desteklenir:</span><span class="sxs-lookup"><span data-stu-id="20aaa-112">The following WCF bindings are supported in Windows Store Applications:</span></span>  
  
1.  <xref:System.ServiceModel.BasicHttpBinding>  
  
2.  <xref:System.ServiceModel.NetTcpBinding>  
  
3.  <xref:System.ServiceModel.NetHttpBinding>  
  
4.  <xref:System.ServiceModel.Channels.CustomBinding>
  
 <span data-ttu-id="20aaa-113">Aşağıdaki bağlama öğeleri Windows mağazası uygulamalarında desteklenir</span><span class="sxs-lookup"><span data-stu-id="20aaa-113">The following binding elements are supported in Windows Store Applications</span></span>  
  
1.  <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
  
2.  <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
  
3.  <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>  
  
4.  <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
5.  <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
6.  <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
7.  <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
8.  <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
9. <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
 <span data-ttu-id="20aaa-114">Metin ve ikili kodlamaları desteklenir.</span><span class="sxs-lookup"><span data-stu-id="20aaa-114">Both Text and Binary encodings are supported.</span></span> <span data-ttu-id="20aaa-115">Tüm WCF aktarım modlarını desteklenir.</span><span class="sxs-lookup"><span data-stu-id="20aaa-115">All WCF transfer modes are supported.</span></span> <span data-ttu-id="20aaa-116">Daha fazla bilgi için [ileti aktarma akışı](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md).</span><span class="sxs-lookup"><span data-stu-id="20aaa-116">For more information see, [Streaming Message Transfer](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md).</span></span>  
  
### <a name="add-service-reference"></a><span data-ttu-id="20aaa-117">Hizmet Başvurusu Ekle</span><span class="sxs-lookup"><span data-stu-id="20aaa-117">Add Service Reference</span></span>  
 <span data-ttu-id="20aaa-118">Bir Windows mağazası uygulamasından bir WCF hizmetini çağırmak için Visual Studio 2012'in hizmet Başvurusu Ekle özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="20aaa-118">To call a WCF service from a Windows Store application, use the Add Service Reference feature of Visual Studio 2012.</span></span> <span data-ttu-id="20aaa-119">Hizmet bir Windows mağazası uygulama içinde işiniz bittiğinde Başvurusu Ekle işlevselliğini birkaç değişiklik fark edersiniz.</span><span class="sxs-lookup"><span data-stu-id="20aaa-119">You will notice a few changes in the functionality of Add Service Reference when done within a Windows Store application.</span></span> <span data-ttu-id="20aaa-120">Önce herhangi bir yapılandırma dosyası oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="20aaa-120">First no configuration file is generated.</span></span> <span data-ttu-id="20aaa-121">Kodda yapılandırılmalıdır için Windows mağazası uygulamaları yapılandırma dosyaları kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="20aaa-121">Windows Store applications do not use configuration files, so they must be configured in code.</span></span> <span data-ttu-id="20aaa-122">Bu yapılandırma kodunu hizmet Başvurusu Ekle tarafından oluşturulan References.cs dosyasında bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="20aaa-122">This configuration code can be found in the References.cs file generated by Add Service Reference.</span></span> <span data-ttu-id="20aaa-123">Bu dosyayı görmek için Çözüm Gezgini'nde "Tüm dosyaları göster" seçmek emin olun.</span><span class="sxs-lookup"><span data-stu-id="20aaa-123">To see this file, make sure to select "Show All Files" in the solution explorer.</span></span> <span data-ttu-id="20aaa-124">Dosya hizmeti başvuruları ve sonra projeyi içinde Reference.svcmap düğümleri altında yer alır.</span><span class="sxs-lookup"><span data-stu-id="20aaa-124">The file will be located under the Service References and then Reference.svcmap nodes within the project.</span></span> <span data-ttu-id="20aaa-125">Windows mağazası uygulaması içinde WCF hizmetleri için oluşturulan tüm işlemleri görev tabanlı zaman uyumsuz desen kullanarak zaman uyumsuz olacaktır.</span><span class="sxs-lookup"><span data-stu-id="20aaa-125">All operations generated for WCF services within a Windows Store application will be asynchronous using the Task-based asynchronous pattern.</span></span> <span data-ttu-id="20aaa-126">Daha fazla bilgi için bkz: [görev tabanlı zaman uyumsuz desen](http://msdn.microsoft.com/magazine/ff959203.aspx).</span><span class="sxs-lookup"><span data-stu-id="20aaa-126">For more information, see [Task-based Asynchronous Pattern](http://msdn.microsoft.com/magazine/ff959203.aspx).</span></span>  
  
 <span data-ttu-id="20aaa-127">Yapılandırma şimdi kodda oluşturulduğundan, hizmet başvurusu her güncelleştirildiğinde Reference.cs dosyasında yapılan değişiklikler üzerine.</span><span class="sxs-lookup"><span data-stu-id="20aaa-127">Because configuration is now generated in code, any changes made in the Reference.cs file would be overwritten every time the service reference is updated.</span></span> <span data-ttu-id="20aaa-128">Bu durumu düzeltmek için istemci proxy sınıfınızda uygulayabileceğiniz bir kısmi yöntemi içinde yapılandırma kodu oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="20aaa-128">To remedy this situation the configuration code is generated within a partial method, which you can implement in your client proxy class.</span></span> <span data-ttu-id="20aaa-129">Kısmi yöntemini aşağıdaki gibi bildirdi:</span><span class="sxs-lookup"><span data-stu-id="20aaa-129">The partial method is declared as follows:</span></span>  
  
```csharp  
static partial void Configure(System.ServiceModel.Description.ServiceEndpoint serviceEndpoint,  
            System.ServiceModel.Description.ClientCredentials clientCredentials);  
```  
  
 <span data-ttu-id="20aaa-130">Ardından, kısmi bu yöntemi uygulaması ve bağlama veya uç nokta istemci proxy sınıfınızda aşağıdaki gibi değiştirin:</span><span class="sxs-lookup"><span data-stu-id="20aaa-130">You can then implement this partial method and change the binding or endpoint in your client proxy class as follows:</span></span>  
  
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
  
### <a name="serialization"></a><span data-ttu-id="20aaa-131">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="20aaa-131">Serialization</span></span>  
 <span data-ttu-id="20aaa-132">Aşağıdaki serileştiricileri Windows mağazası uygulamalarında desteklenir:</span><span class="sxs-lookup"><span data-stu-id="20aaa-132">The following serializers are supported in Windows Store applications:</span></span>  
  
1.  <span data-ttu-id="20aaa-133">DataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="20aaa-133">DataContractSerializer</span></span>  
  
2.  <span data-ttu-id="20aaa-134">DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="20aaa-134">DataContractJsonSerializer</span></span>  
  
3.  <span data-ttu-id="20aaa-135">XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="20aaa-135">XmlSerializer</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="20aaa-136">XmlDictionaryWriter.Write(DateTime) şimdi DateTime nesnesi bir dize yazar.</span><span class="sxs-lookup"><span data-stu-id="20aaa-136">XmlDictionaryWriter.Write(DateTime) now writes the DateTime object as a string.</span></span>  
  
### <a name="security"></a><span data-ttu-id="20aaa-137">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="20aaa-137">Security</span></span>  
 <span data-ttu-id="20aaa-138">Aşağıdaki güvenlik modu Windows mağazası uygulamalarında desteklenir</span><span class="sxs-lookup"><span data-stu-id="20aaa-138">The following security modes are supported in Windows Store applications</span></span>  
  
1.  <xref:System.ServiceModel.SecurityMode.None>  
  
2.  <xref:System.ServiceModel.SecurityMode.Transport>  
  
3.  <!--zz <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredentials> --> `System.ServiceModel.SecurityMode.TransportWithMessageCredentials`
  
4.  <!--zz <xref:System.ServiceModel.SecurityMode.TransportCredentialOnly>  --> `System.ServiceModel.SecurityMode.TransportCredentialOnly`
  
 <span data-ttu-id="20aaa-139">Aşağıdaki istemci kimlik bilgisi türlerinin Windows mağazası uygulamalarında desteklenir</span><span class="sxs-lookup"><span data-stu-id="20aaa-139">The following client credential types are supported in Windows Store applications</span></span>  
  
1.  <span data-ttu-id="20aaa-140">Yok.</span><span class="sxs-lookup"><span data-stu-id="20aaa-140">None</span></span>  
  
2.  <span data-ttu-id="20aaa-141">Temel</span><span class="sxs-lookup"><span data-stu-id="20aaa-141">Basic</span></span>  
  
3.  <span data-ttu-id="20aaa-142">Özet</span><span class="sxs-lookup"><span data-stu-id="20aaa-142">Digest</span></span>  
  
4.  <span data-ttu-id="20aaa-143">Anlaşma</span><span class="sxs-lookup"><span data-stu-id="20aaa-143">Negotiate</span></span>  
  
5.  <span data-ttu-id="20aaa-144">NTLM</span><span class="sxs-lookup"><span data-stu-id="20aaa-144">NTLM</span></span>  
  
6.  <span data-ttu-id="20aaa-145">Windows</span><span class="sxs-lookup"><span data-stu-id="20aaa-145">Windows</span></span>  
  
7.  <span data-ttu-id="20aaa-146">Kullanıcı adı (ileti güvenliği)</span><span class="sxs-lookup"><span data-stu-id="20aaa-146">Username (Message Security)</span></span>  
  
8.  <span data-ttu-id="20aaa-147">Windows (taşıma güvenliği)</span><span class="sxs-lookup"><span data-stu-id="20aaa-147">Windows (Transport Security)</span></span>  
  
 <span data-ttu-id="20aaa-148">Erişim ve varsayılan Windows kimlik bilgileri göndermek Windows mağazası uygulamaları Package.appmanifest dosyası içinde bu işlevi etkinleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="20aaa-148">In order for Windows Store applications to access and send default Windows credentials, you must enable this functionality within the Package.appmanifest file.</span></span> <span data-ttu-id="20aaa-149">Bu dosyayı açın ve yetenekleri sekmesini seçin ve "Varsayılan Windows kimlik bilgileri" seçin.</span><span class="sxs-lookup"><span data-stu-id="20aaa-149">Open this file and select the Capabilities tab and select "Default Windows Credentials".</span></span> <span data-ttu-id="20aaa-150">Bu etki alanı kimlik bilgileri gerektiren intranet kaynaklarına bağlanmak uygulama sağlar.</span><span class="sxs-lookup"><span data-stu-id="20aaa-150">This allows the application to connect to intranet resources that require domain credentials.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="20aaa-151">Çapraz makine çağrı yapmak Windows mağazası uygulamaları için sırayla "Ev/iş ağı" adlı başka bir özelliği etkinleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="20aaa-151">In order for Windows Store applications to make cross machine calls you must enable another capability called "Home/Work Networking".</span></span> <span data-ttu-id="20aaa-152">Bu ayar, Özellikleri sekmesi altında Package.appmanifest dosyasında değildir. Ev/iş ağı onay kutusunu seçin.</span><span class="sxs-lookup"><span data-stu-id="20aaa-152">This setting is also in the Package.appmanifest file under the Capabilities tab. Select the Home/Work Networking checkbox.</span></span> <span data-ttu-id="20aaa-153">Bu kullanıcının ağlara gelen ve giden erişim yerler ev ve iş gibi güvenilir uygulamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="20aaa-153">This gives your application inbound and outbound access to the networks of the user’s trusted places like home and work.</span></span> <span data-ttu-id="20aaa-154">Kritik gelen bağlantı noktalarının her zaman engellenir.</span><span class="sxs-lookup"><span data-stu-id="20aaa-154">Inbound critical ports are always blocked.</span></span> <span data-ttu-id="20aaa-155">Internet'te hizmetlerine erişmek için Internet (istemci) özelliği da etkinleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="20aaa-155">For accessing services on the internet you must also enable Internet (Client) capability.</span></span>  
  
### <a name="misc"></a><span data-ttu-id="20aaa-156">Çeşitli</span><span class="sxs-lookup"><span data-stu-id="20aaa-156">Misc</span></span>  
 <span data-ttu-id="20aaa-157">Aşağıdaki sınıflar kullanımını Windows mağazası uygulamaları için desteklenir:</span><span class="sxs-lookup"><span data-stu-id="20aaa-157">The use of the following classes is supported for Windows Store Applications:</span></span>  
  
1.  <xref:System.ServiceModel.ChannelFactory>  
  
2.  <!--zz <xref:System.ServiceModel.DuplexChannelFactory> --> `System.ServiceModel.DuplexChannelFactory`
  
3.  <xref:System.ServiceModel.CallbackBehaviorAttribute>  
  
### <a name="defining-service-contracts"></a><span data-ttu-id="20aaa-158">Hizmet sözleşmelerini tanımlama</span><span class="sxs-lookup"><span data-stu-id="20aaa-158">Defining Service Contracts</span></span>  
 <span data-ttu-id="20aaa-159">Görev tabanlı zaman uyumsuz desen kullanarak zaman uyumsuz hizmet işlemleri yalnızca tanımlama öneririz.</span><span class="sxs-lookup"><span data-stu-id="20aaa-159">We recommend only defining asynchronous service operations using the task-based async pattern.</span></span> <span data-ttu-id="20aaa-160">Bu, bir hizmet işlemi çağrılırken Windows mağazası uygulamaları yanıt verebilir durumda kalmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="20aaa-160">This ensures Windows Store applications remain responsive while calling a service operation.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="20aaa-161">Eşzamanlı bir işlem tanımlarsanız, hiçbir özel durum olsa da, yalnızca zaman uyumsuz işlemleri tanımlamak için kesinlikle önerilir.</span><span class="sxs-lookup"><span data-stu-id="20aaa-161">While no exception will be thrown if you define a synchronous operation, it is strongly recommended to only define asynchronous operations.</span></span>  
  
### <a name="calling-wcf-services-from-windows-store-applications"></a><span data-ttu-id="20aaa-162">WCF hizmetlerine Windows mağazası uygulamasından çağırma</span><span class="sxs-lookup"><span data-stu-id="20aaa-162">Calling WCF Services from Windows Store Applications</span></span>  
 <span data-ttu-id="20aaa-163">Önceden belirtildiği gibi tüm yapılandırma oluşturulan proxy sınıfı GetBindingForEndpoint yönteminde kodda yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="20aaa-163">As mentioned before all configuration must be done in code in the GetBindingForEndpoint method in the generated proxy class.</span></span> <span data-ttu-id="20aaa-164">Bir hizmet işlemi çağrılırken, aşağıdaki kod parçacığında gösterildiği gibi tüm görev tabanlı zaman uyumsuz yöntem çağırma aynı yapılır.</span><span class="sxs-lookup"><span data-stu-id="20aaa-164">Calling a service operation is done the same as calling any task-based asynchronous method as shown in the following code snippet.</span></span>  
  
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
  
 <span data-ttu-id="20aaa-165">Async anahtar sözcüğü zaman uyumsuz çağrı ve bekleme anahtar zaman uyumsuz yöntem çağrılırken hale yöntemine kullanımına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="20aaa-165">Notice the use of the async keyword on the method making the asynchronous call and the await keyword when calling the asynchronous method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20aaa-166">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="20aaa-166">See Also</span></span>  
 [<span data-ttu-id="20aaa-167">Windows mağazası uygulamaları günlüğündeki WCF</span><span class="sxs-lookup"><span data-stu-id="20aaa-167">WCF in Windows Store Apps Blog</span></span>](http://blogs.msdn.com/b/piyushjo/archive/2011/09/22/wcf-in-win8-metro-styled-apps-absolutely-supported.aspx)  
 [<span data-ttu-id="20aaa-168">WCF Windows mağazası istemcileri ve güvenlik</span><span class="sxs-lookup"><span data-stu-id="20aaa-168">WCF Windows Store Clients and Security</span></span>](http://blogs.msdn.com/b/piyushjo/archive/2011/10/11/calling-a-wcf-service-from-a-metro-application-adding-security.aspx)  
 [<span data-ttu-id="20aaa-169">Windows mağazası uygulamaları ve çapraz makine çağrıları</span><span class="sxs-lookup"><span data-stu-id="20aaa-169">Windows Store Apps and Cross Machine Calls</span></span>](http://blogs.msdn.com/b/piyushjo/archive/2011/10/22/calling-a-wcf-service-from-a-metro-application-cross-machine-scenario.aspx)  
 [<span data-ttu-id="20aaa-170">Bir Windows mağazası uygulamasından azure'da dağıtılan bir WCF Hizmeti çağırma</span><span class="sxs-lookup"><span data-stu-id="20aaa-170">Calling a WCF Service Deployed in Azure from a Windows Store App</span></span>](http://blogs.msdn.com/b/piyushjo/archive/2011/10/22/calling-a-wcf-service-from-a-metro-application-cross-machine-scenario.aspx)  
 [<span data-ttu-id="20aaa-171">WCF Güvenliğini Programlama</span><span class="sxs-lookup"><span data-stu-id="20aaa-171">Programming WCF Security</span></span>](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)  
 [<span data-ttu-id="20aaa-172">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="20aaa-172">Bindings</span></span>](../../../../docs/framework/wcf/bindings.md)
