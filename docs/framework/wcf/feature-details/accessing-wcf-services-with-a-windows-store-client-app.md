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
# <a name="accessing-wcf-services-with-a-windows-store-client-app"></a><span data-ttu-id="ad0c5-102">WCF Hizmetlerine Windows Mağazası İstemci Uygulaması ile Erişme</span><span class="sxs-lookup"><span data-stu-id="ad0c5-102">Accessing WCF Services with a Windows Store Client App</span></span>
<span data-ttu-id="ad0c5-103">Windows 8, Windows Mağazası uygulamaları adı verilen yeni bir uygulama türünü sunar.</span><span class="sxs-lookup"><span data-stu-id="ad0c5-103">Windows 8 introduces a new type of application called Windows Store applications.</span></span> <span data-ttu-id="ad0c5-104">Bu uygulamalar dokunmatik ekran arabirimi etrafında tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="ad0c5-104">These applications are designed around a touch screen interface.</span></span> <span data-ttu-id="ad0c5-105">.NET Framework 4.5, Windows Mağazası uygulamalarının WCF hizmetlerini aramasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="ad0c5-105">.NET Framework 4.5 enables Windows Store applications to call WCF services.</span></span>  
  
## <a name="wcf-support-in-windows-store-applications"></a><span data-ttu-id="ad0c5-106">Windows Mağazası Uygulamalarında WCF Desteği</span><span class="sxs-lookup"><span data-stu-id="ad0c5-106">WCF Support in Windows Store Applications</span></span>  
 <span data-ttu-id="ad0c5-107">WCF işlevselliğinin bir alt kümesi bir Windows Mağazası uygulaması içinden edinilebilir, daha fazla ayrıntı için aşağıdaki bölümlere bakın.</span><span class="sxs-lookup"><span data-stu-id="ad0c5-107">A subset of WCF functionality is available from within a Windows Store application, see the following sections for more details.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ad0c5-108">WCF tarafından maruz kalanlar yerine WinRT sendikasyon API'lerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="ad0c5-108">Use the WinRT syndication APIs instead of those exposed by WCF.</span></span> <span data-ttu-id="ad0c5-109">Daha fazla bilgi için bkz: [WinRT Sendikasyon API](xref:Windows.Web.Syndication)</span><span class="sxs-lookup"><span data-stu-id="ad0c5-109">For more information see, [WinRT Syndication API](xref:Windows.Web.Syndication)</span></span>  
  
> [!WARNING]
> <span data-ttu-id="ad0c5-110">Windows Runtime Bileşenine web hizmeti başvurusu eklemek için Hizmet Başvurusu Ekle'nin kullanılması desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="ad0c5-110">Using Add Service Reference to add a web service reference to a Windows Runtime Component isn’t supported.</span></span>  
  
### <a name="supported-bindings"></a><span data-ttu-id="ad0c5-111">Desteklenen Ciltler</span><span class="sxs-lookup"><span data-stu-id="ad0c5-111">Supported Bindings</span></span>  
 <span data-ttu-id="ad0c5-112">Aşağıdaki WCF bağlamaları Windows Mağazası Uygulamalarında desteklenir:</span><span class="sxs-lookup"><span data-stu-id="ad0c5-112">The following WCF bindings are supported in Windows Store Applications:</span></span>  
  
1. <xref:System.ServiceModel.BasicHttpBinding>  
  
2. <xref:System.ServiceModel.NetTcpBinding>  
  
3. <xref:System.ServiceModel.NetHttpBinding>  
  
4. <xref:System.ServiceModel.Channels.CustomBinding>
  
 <span data-ttu-id="ad0c5-113">Windows Mağazası Uygulamalarında aşağıdaki bağlama öğeleri desteklenir</span><span class="sxs-lookup"><span data-stu-id="ad0c5-113">The following binding elements are supported in Windows Store Applications</span></span>  
  
1. <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
  
2. <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
  
3. <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>  
  
4. <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
5. <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
6. <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
7. <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
8. <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
9. <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
 <span data-ttu-id="ad0c5-114">Hem Metin hem de İkili kodlamalar desteklenir.</span><span class="sxs-lookup"><span data-stu-id="ad0c5-114">Both Text and Binary encodings are supported.</span></span> <span data-ttu-id="ad0c5-115">Tüm WCF aktarım modları desteklenir.</span><span class="sxs-lookup"><span data-stu-id="ad0c5-115">All WCF transfer modes are supported.</span></span> <span data-ttu-id="ad0c5-116">Daha fazla bilgi için bkz: [Akış İleti Aktarımı](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md).</span><span class="sxs-lookup"><span data-stu-id="ad0c5-116">For more information see, [Streaming Message Transfer](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md).</span></span>  
  
### <a name="add-service-reference"></a><span data-ttu-id="ad0c5-117">Hizmet Başvurusu Ekle</span><span class="sxs-lookup"><span data-stu-id="ad0c5-117">Add Service Reference</span></span>  
 <span data-ttu-id="ad0c5-118">Bir Windows Mağazası uygulamasından WCF hizmetini aramak için Visual Studio 2012'nin Hizmet Başvurusu Ekle özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="ad0c5-118">To call a WCF service from a Windows Store application, use the Add Service Reference feature of Visual Studio 2012.</span></span> <span data-ttu-id="ad0c5-119">Bir Windows Mağazası uygulaması içinde yapıldığında Hizmet Başvurusu Ekle işlevinde birkaç değişiklik fark edeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="ad0c5-119">You will notice a few changes in the functionality of Add Service Reference when done within a Windows Store application.</span></span> <span data-ttu-id="ad0c5-120">İlk olarak hiçbir yapılandırma dosyası oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ad0c5-120">First no configuration file is generated.</span></span> <span data-ttu-id="ad0c5-121">Windows Mağazası uygulamaları yapılandırma dosyalarını kullanmadığından, kod olarak yapılandırılmaları gerekir.</span><span class="sxs-lookup"><span data-stu-id="ad0c5-121">Windows Store applications do not use configuration files, so they must be configured in code.</span></span> <span data-ttu-id="ad0c5-122">Bu yapılandırma kodu, Hizmet Başvurusu Ekle tarafından oluşturulan References.cs dosyasında bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="ad0c5-122">This configuration code can be found in the References.cs file generated by Add Service Reference.</span></span> <span data-ttu-id="ad0c5-123">Bu dosyayı görmek için çözüm gezgininde "Tüm Dosyaları Göster"i seçtiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="ad0c5-123">To see this file, make sure to select "Show All Files" in the solution explorer.</span></span> <span data-ttu-id="ad0c5-124">Dosya, Hizmet Başvuruları altında ve ardından proje içinde Reference.svcmap düğümleri altında yer alacaktır.</span><span class="sxs-lookup"><span data-stu-id="ad0c5-124">The file will be located under the Service References and then Reference.svcmap nodes within the project.</span></span> <span data-ttu-id="ad0c5-125">Bir Windows Mağazası uygulaması içinde WCF hizmetleri için oluşturulan tüm işlemler, Görev tabanlı eşzamanlı desen kullanılarak eşzamanlı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="ad0c5-125">All operations generated for WCF services within a Windows Store application will be asynchronous using the Task-based asynchronous pattern.</span></span> <span data-ttu-id="ad0c5-126">Daha fazla bilgi için [Bkz. Async Görevleri - Görevlerile Eşzamanlı Programlamayı Basitleştirin.](https://docs.microsoft.com/archive/msdn-magazine/2010/september/async-tasks-simplify-asynchronous-programming-with-tasks)</span><span class="sxs-lookup"><span data-stu-id="ad0c5-126">For more information, see [Async Tasks - Simplify Asynchronous Programming with Tasks](https://docs.microsoft.com/archive/msdn-magazine/2010/september/async-tasks-simplify-asynchronous-programming-with-tasks).</span></span>  
  
 <span data-ttu-id="ad0c5-127">Yapılandırma artık kod olarak oluşturulduğundan, Reference.cs dosyasında yapılan tüm değişiklikler, hizmet başvurusu her güncelleştirilse üzerine yazılır.</span><span class="sxs-lookup"><span data-stu-id="ad0c5-127">Because configuration is now generated in code, any changes made in the Reference.cs file would be overwritten every time the service reference is updated.</span></span> <span data-ttu-id="ad0c5-128">Bu durumu gidermek için yapılandırma kodu, istemci proxy sınıfınızda uygulayabileceğiniz kısmi bir yöntem içinde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ad0c5-128">To remedy this situation the configuration code is generated within a partial method, which you can implement in your client proxy class.</span></span> <span data-ttu-id="ad0c5-129">Kısmi yöntem aşağıdaki gibi beyan edilir:</span><span class="sxs-lookup"><span data-stu-id="ad0c5-129">The partial method is declared as follows:</span></span>  
  
```csharp  
static partial void Configure(System.ServiceModel.Description.ServiceEndpoint serviceEndpoint,  
            System.ServiceModel.Description.ClientCredentials clientCredentials);  
```  
  
 <span data-ttu-id="ad0c5-130">Daha sonra bu kısmi yöntemi uygulayabilir ve istemci proxy sınıfınızdaki bağlama veya bitiş noktasını aşağıdaki gibi değiştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ad0c5-130">You can then implement this partial method and change the binding or endpoint in your client proxy class as follows:</span></span>  
  
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
  
### <a name="serialization"></a><span data-ttu-id="ad0c5-131">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="ad0c5-131">Serialization</span></span>  
 <span data-ttu-id="ad0c5-132">Aşağıdaki serializers Windows Mağazası uygulamalarında desteklenir:</span><span class="sxs-lookup"><span data-stu-id="ad0c5-132">The following serializers are supported in Windows Store applications:</span></span>  
  
1. <span data-ttu-id="ad0c5-133">DataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="ad0c5-133">DataContractSerializer</span></span>  
  
2. <span data-ttu-id="ad0c5-134">DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="ad0c5-134">DataContractJsonSerializer</span></span>  
  
3. <span data-ttu-id="ad0c5-135">Xmlserializer</span><span class="sxs-lookup"><span data-stu-id="ad0c5-135">XmlSerializer</span></span>  
  
> [!WARNING]
> <span data-ttu-id="ad0c5-136">XmlDictionaryWriter.Write(DateTime) şimdi bir dize olarak DateTime nesnesi yazar.</span><span class="sxs-lookup"><span data-stu-id="ad0c5-136">XmlDictionaryWriter.Write(DateTime) now writes the DateTime object as a string.</span></span>  
  
### <a name="security"></a><span data-ttu-id="ad0c5-137">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="ad0c5-137">Security</span></span>  

<span data-ttu-id="ad0c5-138">Aşağıdaki güvenlik modları Windows Mağazası uygulamalarında desteklenir:</span><span class="sxs-lookup"><span data-stu-id="ad0c5-138">The following security modes are supported in Windows Store applications:</span></span>
  
1. <xref:System.ServiceModel.SecurityMode.None>  
  
2. <xref:System.ServiceModel.SecurityMode.Transport>  
  
3. <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>
  
4. <xref:System.ServiceModel.SecurityMode.Message>
  
<span data-ttu-id="ad0c5-139">Aşağıdaki istemci kimlik bilgileri türleri Windows Mağazası uygulamalarında desteklenir:</span><span class="sxs-lookup"><span data-stu-id="ad0c5-139">The following client credential types are supported in Windows Store applications:</span></span>
  
1. <span data-ttu-id="ad0c5-140">None</span><span class="sxs-lookup"><span data-stu-id="ad0c5-140">None</span></span>  
  
2. <span data-ttu-id="ad0c5-141">Temel</span><span class="sxs-lookup"><span data-stu-id="ad0c5-141">Basic</span></span>  
  
3. <span data-ttu-id="ad0c5-142">Özet</span><span class="sxs-lookup"><span data-stu-id="ad0c5-142">Digest</span></span>  
  
4. <span data-ttu-id="ad0c5-143">Anlaşma</span><span class="sxs-lookup"><span data-stu-id="ad0c5-143">Negotiate</span></span>  
  
5. <span data-ttu-id="ad0c5-144">NTLM</span><span class="sxs-lookup"><span data-stu-id="ad0c5-144">NTLM</span></span>  
  
6. <span data-ttu-id="ad0c5-145">Windows</span><span class="sxs-lookup"><span data-stu-id="ad0c5-145">Windows</span></span>  
  
7. <span data-ttu-id="ad0c5-146">Kullanıcı adı (İleti Güvenliği)</span><span class="sxs-lookup"><span data-stu-id="ad0c5-146">Username (Message Security)</span></span>  
  
8. <span data-ttu-id="ad0c5-147">Windows (Aktarım Güvenliği)</span><span class="sxs-lookup"><span data-stu-id="ad0c5-147">Windows (Transport Security)</span></span>  
  
 <span data-ttu-id="ad0c5-148">Windows Mağazası uygulamalarının varsayılan Windows kimlik bilgilerine erişebilmesi ve göndermesi için bu işlevselliği Package.appmanifest dosyasında etkinleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ad0c5-148">In order for Windows Store applications to access and send default Windows credentials, you must enable this functionality within the Package.appmanifest file.</span></span> <span data-ttu-id="ad0c5-149">Bu dosyayı açın ve Özellikler sekmesini seçin ve "Varsayılan Windows Kimlik Bilgileri"ni seçin.</span><span class="sxs-lookup"><span data-stu-id="ad0c5-149">Open this file and select the Capabilities tab and select "Default Windows Credentials".</span></span> <span data-ttu-id="ad0c5-150">Bu, uygulamanın etki alanı kimlik bilgileri gerektiren intranet kaynaklarına bağlanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="ad0c5-150">This allows the application to connect to intranet resources that require domain credentials.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ad0c5-151">Windows Mağazası uygulamalarının makineler arası arama yapabilmesi için "Ev/İş Ağı" adı verilen başka bir özelliği etkinleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ad0c5-151">In order for Windows Store applications to make cross machine calls you must enable another capability called "Home/Work Networking".</span></span> <span data-ttu-id="ad0c5-152">Bu ayar, Özellikler sekmesi altındaki Package.appmanifest dosyasında da yer alıyor. Ev/İş Ağı onay kutusunu seçin.</span><span class="sxs-lookup"><span data-stu-id="ad0c5-152">This setting is also in the Package.appmanifest file under the Capabilities tab. Select the Home/Work Networking checkbox.</span></span> <span data-ttu-id="ad0c5-153">Bu, uygulamanızın kullanıcının ev ve iş gibi güvenilir yerlerinin ağlarına gelen ve giden erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="ad0c5-153">This gives your application inbound and outbound access to the networks of the user’s trusted places like home and work.</span></span> <span data-ttu-id="ad0c5-154">Gelen kritik bağlantı noktaları her zaman engellenir.</span><span class="sxs-lookup"><span data-stu-id="ad0c5-154">Inbound critical ports are always blocked.</span></span> <span data-ttu-id="ad0c5-155">Internet'teki hizmetlere erişmek için Internet (İstemci) özelliğini de etkinleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ad0c5-155">For accessing services on the internet you must also enable Internet (Client) capability.</span></span>  
  
### <a name="misc"></a><span data-ttu-id="ad0c5-156">Çeşitli</span><span class="sxs-lookup"><span data-stu-id="ad0c5-156">Misc</span></span>  
 <span data-ttu-id="ad0c5-157">Aşağıdaki sınıfların kullanımı Windows Mağazası Uygulamaları için desteklenir:</span><span class="sxs-lookup"><span data-stu-id="ad0c5-157">The use of the following classes is supported for Windows Store Applications:</span></span>  
  
1. <xref:System.ServiceModel.ChannelFactory>  
  
2. <xref:System.ServiceModel.DuplexChannelFactory%601>
  
3. <xref:System.ServiceModel.CallbackBehaviorAttribute>  
  
### <a name="defining-service-contracts"></a><span data-ttu-id="ad0c5-158">Hizmet Sözleşmelerinin Tanımlanması</span><span class="sxs-lookup"><span data-stu-id="ad0c5-158">Defining Service Contracts</span></span>  
 <span data-ttu-id="ad0c5-159">Yalnızca görev tabanlı async deseni kullanarak eşzamanlı hizmet işlemlerini tanımlamanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="ad0c5-159">We recommend only defining asynchronous service operations using the task-based async pattern.</span></span> <span data-ttu-id="ad0c5-160">Bu, Windows Mağazası uygulamalarının bir hizmet işlemini ararken yanıt vermeye devam edilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="ad0c5-160">This ensures Windows Store applications remain responsive while calling a service operation.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="ad0c5-161">Senkron bir işlem tanımlarsanız özel durum atılmazken, yalnızca eşzamanlı işlemleri tanımlamanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="ad0c5-161">While no exception will be thrown if you define a synchronous operation, it is strongly recommended to only define asynchronous operations.</span></span>  
  
### <a name="calling-wcf-services-from-windows-store-applications"></a><span data-ttu-id="ad0c5-162">Windows Mağazası Uygulamalarından WCF Hizmetlerini Arama</span><span class="sxs-lookup"><span data-stu-id="ad0c5-162">Calling WCF Services from Windows Store Applications</span></span>  
 <span data-ttu-id="ad0c5-163">Daha önce de belirtildiği gibi, oluşturulan proxy sınıfında getBindingForEndpoint yönteminde tüm yapılandırma kod içinde yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ad0c5-163">As mentioned before all configuration must be done in code in the GetBindingForEndpoint method in the generated proxy class.</span></span> <span data-ttu-id="ad0c5-164">Bir hizmet işlemini çağırmak, aşağıdaki kod snippet'inde gösterildiği gibi görev tabanlı eşyoknöz yöntemi çağırmakla aynı şekilde yapılır.</span><span class="sxs-lookup"><span data-stu-id="ad0c5-164">Calling a service operation is done the same as calling any task-based asynchronous method as shown in the following code snippet.</span></span>  
  
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
  
 <span data-ttu-id="ad0c5-165">Asynchronous metod'u ararken asynchronous arama ve bekleyen anahtar kelime yönteminde async anahtar kelimesinin kullanımına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="ad0c5-165">Notice the use of the async keyword on the method making the asynchronous call and the await keyword when calling the asynchronous method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad0c5-166">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ad0c5-166">See also</span></span>

- [<span data-ttu-id="ad0c5-167">Windows Mağazası Apps Blog WCF</span><span class="sxs-lookup"><span data-stu-id="ad0c5-167">WCF in Windows Store Apps Blog</span></span>](https://docs.microsoft.com/archive/blogs/piyushjo/wcf-in-windows-8-metro-styled-apps-absolutely-supported)
- [<span data-ttu-id="ad0c5-168">WCF Windows Mağazası İstemcileri ve Güvenliği</span><span class="sxs-lookup"><span data-stu-id="ad0c5-168">WCF Windows Store Clients and Security</span></span>](https://docs.microsoft.com/archive/blogs/piyushjo/calling-a-wcf-service-from-a-metro-application-adding-security)
- [<span data-ttu-id="ad0c5-169">Windows Mağazası Uygulamaları ve Çapraz Makine Aramaları</span><span class="sxs-lookup"><span data-stu-id="ad0c5-169">Windows Store Apps and Cross Machine Calls</span></span>](https://docs.microsoft.com/archive/blogs/piyushjo/calling-a-wcf-service-from-a-metro-application-cross-machine-scenario)
- [<span data-ttu-id="ad0c5-170">Windows Mağazası Uygulamasından Azure'da Dağıtılan Bir WCF Hizmeti çağırma</span><span class="sxs-lookup"><span data-stu-id="ad0c5-170">Calling a WCF Service Deployed in Azure from a Windows Store App</span></span>](https://docs.microsoft.com/archive/blogs/piyushjo/calling-a-wcf-service-from-a-metro-application-cross-machine-scenario)
- [<span data-ttu-id="ad0c5-171">WCF Güvenliğini Programlama</span><span class="sxs-lookup"><span data-stu-id="ad0c5-171">Programming WCF Security</span></span>](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)
- [<span data-ttu-id="ad0c5-172">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="ad0c5-172">Bindings</span></span>](../../../../docs/framework/wcf/bindings.md)
