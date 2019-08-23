---
title: .NET Uzaktan İletişimden WCF'ye Taşınma
ms.date: 03/30/2017
ms.assetid: 16902a42-ef80-40e9-8c4c-90e61ddfdfe5
ms.openlocfilehash: 71e26ddd93605b02031aecba280e382528378ba6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943029"
---
# <a name="migrating-from-net-remoting-to-wcf"></a><span data-ttu-id="e772f-102">.NET Uzaktan İletişimden WCF'ye Taşınma</span><span class="sxs-lookup"><span data-stu-id="e772f-102">Migrating from .NET Remoting to WCF</span></span>
<span data-ttu-id="e772f-103">Bu makalede, .NET Remoting kullanan bir uygulamanın Windows Communication Foundation (WCF) kullanmak üzere nasıl geçirileceği açıklanır.</span><span class="sxs-lookup"><span data-stu-id="e772f-103">This article describes how to migrate an application that uses .NET Remoting to use Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="e772f-104">Bu ürünler arasındaki benzer kavramları karşılaştırır ve daha sonra WCF 'de birkaç genel uzaktan Iletişim senaryosu gerçekleştirmeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="e772f-104">It compares similar concepts between these products and then describes how to accomplish several common Remoting scenarios in WCF.</span></span>  
  
 <span data-ttu-id="e772f-105">.NET uzaktan Iletişim yalnızca geriye dönük uyumluluk için desteklenen eski bir üründür.</span><span class="sxs-lookup"><span data-stu-id="e772f-105">.NET Remoting is a legacy product that is supported only for backward compatibility.</span></span> <span data-ttu-id="e772f-106">İstemci ve sunucu arasında ayrı güven düzeylerini koruyamadığından, karma güven ortamlarında güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="e772f-106">It is not secure across mixed-trust environments because it cannot maintain the separate trust levels between client and server.</span></span> <span data-ttu-id="e772f-107">Örneğin, hiç bir .NET Remoting uç noktasını Internet 'e veya güvenilmeyen istemcilere sunmamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e772f-107">For example, you should never expose a .NET Remoting endpoint to the Internet or to untrusted clients.</span></span> <span data-ttu-id="e772f-108">Mevcut uzaktan Iletişim uygulamalarının daha yeni ve daha güvenli teknolojilere geçirilmesi önerilir.</span><span class="sxs-lookup"><span data-stu-id="e772f-108">We recommend existing Remoting applications be migrated to newer and more secure technologies.</span></span> <span data-ttu-id="e772f-109">Uygulamanın tasarımı yalnızca HTTP kullanıyorsa ve yeniden karşılaşırsanız, ASP.NET Web API 'SI önerilir.</span><span class="sxs-lookup"><span data-stu-id="e772f-109">If the application’s design uses only HTTP and is RESTful, we recommend ASP.NET Web API.</span></span> <span data-ttu-id="e772f-110">Daha fazla bilgi için bkz. ASP.NET Web API.</span><span class="sxs-lookup"><span data-stu-id="e772f-110">For more information, see ASP.NET Web API.</span></span> <span data-ttu-id="e772f-111">Uygulama SOAP 'yi temel alıyorsa veya TCP gibi http olmayan protokoller gerektiriyorsa, WCF önerilir.</span><span class="sxs-lookup"><span data-stu-id="e772f-111">If the application is based on SOAP or requires non-Http protocols such as TCP, we recommend WCF.</span></span>  

## <a name="comparing-net-remoting-to-wcf"></a><span data-ttu-id="e772f-112">.NET uzaktan iletişimini WCF ile karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="e772f-112">Comparing .NET Remoting to WCF</span></span>  
 <span data-ttu-id="e772f-113">Bu bölüm, .NET uzaktan Iletişim uygulamasının temel yapı taşlarını WCF eşdeğerlerine göre karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="e772f-113">This section compares the basic building blocks of .NET Remoting with their WCF equivalents.</span></span> <span data-ttu-id="e772f-114">Bu yapı taşlarını daha sonra WCF 'de bazı yaygın istemci-sunucu senaryoları oluşturmak için kullanacağız. Aşağıdaki grafik, .NET uzaktan Iletişim ve WCF arasındaki önemli benzerlikleri ve farklılıkları özetler.</span><span class="sxs-lookup"><span data-stu-id="e772f-114">We will use these building blocks later to create some common client-server scenarios in WCF.The following chart summarizes the main similarities and differences between .NET Remoting and WCF.</span></span>  
  
||<span data-ttu-id="e772f-115">.NET uzaktan iletişim</span><span class="sxs-lookup"><span data-stu-id="e772f-115">.NET Remoting</span></span>|<span data-ttu-id="e772f-116">WCF</span><span class="sxs-lookup"><span data-stu-id="e772f-116">WCF</span></span>|  
|-|-------------------|---------|  
|<span data-ttu-id="e772f-117">Sunucu türü</span><span class="sxs-lookup"><span data-stu-id="e772f-117">Server type</span></span>|<span data-ttu-id="e772f-118">Subclass MarshalByRefObject</span><span class="sxs-lookup"><span data-stu-id="e772f-118">Subclass MarshalByRefObject</span></span>|<span data-ttu-id="e772f-119">[ServiceContract] özniteliğiyle işaretle</span><span class="sxs-lookup"><span data-stu-id="e772f-119">Mark with [ServiceContract] attribute</span></span>|  
|<span data-ttu-id="e772f-120">Hizmet işlemleri</span><span class="sxs-lookup"><span data-stu-id="e772f-120">Service operations</span></span>|<span data-ttu-id="e772f-121">Sunucu türündeki ortak Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e772f-121">Public methods on server type</span></span>|<span data-ttu-id="e772f-122">[OperationContract] özniteliğiyle işaretle</span><span class="sxs-lookup"><span data-stu-id="e772f-122">Mark with [OperationContract] attribute</span></span>|  
|<span data-ttu-id="e772f-123">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="e772f-123">Serialization</span></span>|<span data-ttu-id="e772f-124">ISerializable veya [Serializable]</span><span class="sxs-lookup"><span data-stu-id="e772f-124">ISerializable or [Serializable]</span></span>|<span data-ttu-id="e772f-125">DataContractSerializer veya XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="e772f-125">DataContractSerializer or XmlSerializer</span></span>|  
|<span data-ttu-id="e772f-126">Geçirilen nesneler</span><span class="sxs-lookup"><span data-stu-id="e772f-126">Objects passed</span></span>|<span data-ttu-id="e772f-127">Değere göre veya başvuruya göre</span><span class="sxs-lookup"><span data-stu-id="e772f-127">By-value or by-reference</span></span>|<span data-ttu-id="e772f-128">Yalnızca değere göre</span><span class="sxs-lookup"><span data-stu-id="e772f-128">By-value only</span></span>|  
|<span data-ttu-id="e772f-129">Hatalar/özel durumlar</span><span class="sxs-lookup"><span data-stu-id="e772f-129">Errors/exceptions</span></span>|<span data-ttu-id="e772f-130">Herhangi bir serileştirilebilir özel durum</span><span class="sxs-lookup"><span data-stu-id="e772f-130">Any serializable exception</span></span>|<span data-ttu-id="e772f-131">FaultContract\<TDetail ></span><span class="sxs-lookup"><span data-stu-id="e772f-131">FaultContract\<TDetail></span></span>|  
|<span data-ttu-id="e772f-132">İstemci proxy nesneleri</span><span class="sxs-lookup"><span data-stu-id="e772f-132">Client proxy objects</span></span>|<span data-ttu-id="e772f-133">Kesin olarak yazılan saydam proxy 'ler bulunan MarshalByRefObjects adresinden otomatik olarak oluşturulur</span><span class="sxs-lookup"><span data-stu-id="e772f-133">Strongly typed transparent proxies are created automatically from MarshalByRefObjects</span></span>|<span data-ttu-id="e772f-134">Türü kesin belirlenmiş proxy 'ler, ChannelFactory\<ile isteğe bağlı olarak oluşturulur ></span><span class="sxs-lookup"><span data-stu-id="e772f-134">Strongly typed proxies are generated on-demand using ChannelFactory\<TChannel></span></span>|  
|<span data-ttu-id="e772f-135">Platform gerekli</span><span class="sxs-lookup"><span data-stu-id="e772f-135">Platform required</span></span>|<span data-ttu-id="e772f-136">Hem istemci hem de sunucu Microsoft OS ve .NET kullanmalıdır</span><span class="sxs-lookup"><span data-stu-id="e772f-136">Both client and server must use Microsoft OS and .NET</span></span>|<span data-ttu-id="e772f-137">Platformlar arası</span><span class="sxs-lookup"><span data-stu-id="e772f-137">Cross-platform</span></span>|  
|<span data-ttu-id="e772f-138">İleti biçimi</span><span class="sxs-lookup"><span data-stu-id="e772f-138">Message format</span></span>|<span data-ttu-id="e772f-139">Özel</span><span class="sxs-lookup"><span data-stu-id="e772f-139">Private</span></span>|<span data-ttu-id="e772f-140">Sektör standartları (SOAP, WS-\*, vb.)</span><span class="sxs-lookup"><span data-stu-id="e772f-140">Industry standards (SOAP, WS-\*, etc.)</span></span>|  
  
### <a name="server-implementation-comparison"></a><span data-ttu-id="e772f-141">Sunucu uygulama karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="e772f-141">Server Implementation Comparison</span></span>  
  
#### <a name="creating-a-server-in-net-remoting"></a><span data-ttu-id="e772f-142">.NET uzaktan Iletişim kutusunda sunucu oluşturma</span><span class="sxs-lookup"><span data-stu-id="e772f-142">Creating a Server in .NET Remoting</span></span>  
 <span data-ttu-id="e772f-143">.NET uzaktan Iletişim sunucusu türleri MarshalByRefObject 'den türetilmelidir ve istemcinin çağırabilmesine ve aşağıdaki gibi arama yöntemlerini tanımlamalıdır:</span><span class="sxs-lookup"><span data-stu-id="e772f-143">.NET Remoting server types must derive from MarshalByRefObject and define methods the client can call, like the following:</span></span>  
  
```csharp
public class RemotingServer : MarshalByRefObject  
{  
    public Customer GetCustomer(int customerId) { … }  
}  
```  
  
 <span data-ttu-id="e772f-144">Bu sunucu türünün genel yöntemleri, istemcilerin kullanabildiği ortak sözleşme olur.</span><span class="sxs-lookup"><span data-stu-id="e772f-144">The public methods of this server type become the public contract available to clients.</span></span>  <span data-ttu-id="e772f-145">Sunucunun ortak arabirimi ve onun uygulamasıyla arasında ayrım yoktur, her ikisini de bir tür işler.</span><span class="sxs-lookup"><span data-stu-id="e772f-145">There is no separation between the server’s public interface and its implementation – one type handles both.</span></span>  
  
 <span data-ttu-id="e772f-146">Sunucu türü tanımlandıktan sonra, aşağıdaki örnekte olduğu gibi istemciler için kullanılabilir hale getirilebilir:</span><span class="sxs-lookup"><span data-stu-id="e772f-146">Once the server type has been defined, it can be made available to clients, like in the following example:</span></span>  
  
```csharp
TcpChannel channel = new TcpChannel(8080);  
ChannelServices.RegisterChannel(channel, ensureSecurity : true);  
RemotingConfiguration.RegisterWellKnownServiceType(  
    typeof(RemotingServer),   
    "RemotingServer",   
    WellKnownObjectMode.Singleton);  
Console.WriteLine("RemotingServer is running.  Press ENTER to terminate...");  
Console.ReadLine();  
```  
  
 <span data-ttu-id="e772f-147">Yapılandırma dosyalarını kullanma dahil, uzaktan Iletişim türünü sunucu olarak kullanılabilir hale getirmek için birçok yol vardır.</span><span class="sxs-lookup"><span data-stu-id="e772f-147">There are many ways to make the Remoting type available as a server, including using configuration files.</span></span> <span data-ttu-id="e772f-148">Bu yalnızca bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="e772f-148">This is just one example.</span></span>  
  
#### <a name="creating-a-server-in-wcf"></a><span data-ttu-id="e772f-149">WCF 'de sunucu oluşturma</span><span class="sxs-lookup"><span data-stu-id="e772f-149">Creating a Server in WCF</span></span>  
 <span data-ttu-id="e772f-150">WCF 'deki eşdeğer adım iki tür oluşturmayı içerir--genel "hizmet sözleşmesi" ve somut uygulama.</span><span class="sxs-lookup"><span data-stu-id="e772f-150">The equivalent step in WCF involves creating two types -- the public "service contract" and the concrete implementation.</span></span> <span data-ttu-id="e772f-151">İlki [ServiceContract] ile işaretlenmiş bir arabirim olarak bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e772f-151">The first is declared as an interface marked with [ServiceContract].</span></span> <span data-ttu-id="e772f-152">İstemciler için kullanılabilir yöntemler [OperationContract] ile işaretlenir:</span><span class="sxs-lookup"><span data-stu-id="e772f-152">Methods available to clients are marked with [OperationContract]:</span></span>  
  
```csharp
[ServiceContract]  
public interface IWCFServer  
{  
    [OperationContract]  
    Customer GetCustomer(int customerId);  
}  
```  
  
 <span data-ttu-id="e772f-153">Sunucunun uygulanması, aşağıdaki örnekte olduğu gibi ayrı bir somut sınıfta tanımlanmıştır:</span><span class="sxs-lookup"><span data-stu-id="e772f-153">The server’s implementation is defined in a separate concrete class, like in the following example:</span></span>  
  
```csharp
public class WCFServer : IWCFServer  
{  
    public Customer GetCustomer(int customerId) { … }  
}  
```  
  
 <span data-ttu-id="e772f-154">Bu türler tanımlandıktan sonra, aşağıdaki örnekte olduğu gibi WCF sunucusu istemciler için kullanılabilir hale getirilebilir:</span><span class="sxs-lookup"><span data-stu-id="e772f-154">Once these types have been defined, the WCF server can be made available to clients, like in the following example:</span></span>  
  
```csharp
NetTcpBinding binding = new NetTcpBinding();  
Uri baseAddress = new Uri("net.tcp://localhost:8000/wcfserver");  
  
using (ServiceHost serviceHost = new ServiceHost(typeof(WCFServer), baseAddress))  
{  
    serviceHost.AddServiceEndpoint(typeof(IWCFServer), binding, baseAddress);  
    serviceHost.Open();  
  
    Console.WriteLine($"The WCF server is ready at {baseAddress}.");
    Console.WriteLine("Press <ENTER> to terminate service...");  
    Console.WriteLine();  
    Console.ReadLine();  
}  
```  
  
> [!NOTE]
> <span data-ttu-id="e772f-155">TCP her iki örnekte de, mümkün olduğunca benzer şekilde devam etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e772f-155">TCP is used in both examples to keep them as similar as possible.</span></span> <span data-ttu-id="e772f-156">HTTP kullanan örnekler için bu konunun ilerleyen kısımlarında yer alarak izlenecek yol-kılavuzlarına bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="e772f-156">Refer to the scenario walk-throughs later in this topic for examples using HTTP.</span></span>  
  
 <span data-ttu-id="e772f-157">WCF hizmetlerini yapılandırmak ve barındırmak için birçok yol vardır.</span><span class="sxs-lookup"><span data-stu-id="e772f-157">There are many ways to configure and to host WCF services.</span></span> <span data-ttu-id="e772f-158">Bu, "kendiliğinden konak" olarak bilinen tek bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="e772f-158">This is just one example, known as "self-hosted".</span></span> <span data-ttu-id="e772f-159">Daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="e772f-159">For more information, see the following topics:</span></span>  
  
- [<span data-ttu-id="e772f-160">Nasıl yapılır: Hizmet sözleşmesi tanımlama</span><span class="sxs-lookup"><span data-stu-id="e772f-160">How to: Define a Service Contract</span></span>](how-to-define-a-wcf-service-contract.md)  
  
- [<span data-ttu-id="e772f-161">Yapılandırma Dosyalarını Kullanarak Hizmetleri Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e772f-161">Configuring Services Using Configuration Files</span></span>](configuring-services-using-configuration-files.md)  
  
- [<span data-ttu-id="e772f-162">Barındırma Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="e772f-162">Hosting Services</span></span>](hosting-services.md)  
  
### <a name="client-implementation-comparison"></a><span data-ttu-id="e772f-163">İstemci uygulama karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="e772f-163">Client Implementation Comparison</span></span>  
  
#### <a name="creating-a-client-in-net-remoting"></a><span data-ttu-id="e772f-164">.NET Remoting 'te Istemci oluşturma</span><span class="sxs-lookup"><span data-stu-id="e772f-164">Creating a Client in .NET Remoting</span></span>  
 <span data-ttu-id="e772f-165">.NET uzaktan Iletişim sunucusu nesnesi kullanılabilir duruma getirildikten sonra, aşağıdaki örnekte olduğu gibi istemciler tarafından tüketilebilir:</span><span class="sxs-lookup"><span data-stu-id="e772f-165">Once a .NET Remoting server object has been made available, it can be consumed by clients, like in the following example:</span></span>  
  
```csharp
TcpChannel channel = new TcpChannel();  
ChannelServices.RegisterChannel(channel, ensureSecurity : true);  
RemotingServer server = (RemotingServer)Activator.GetObject(  
                            typeof(RemotingServer),   
                            "tcp://localhost:8080/RemotingServer");  
  
RemotingCustomer customer = server.GetCustomer(42);  
Console.WriteLine($"Customer {customer.FirstName} {customer.LastName} received.");
```  
  
 <span data-ttu-id="e772f-166">Etkinleştirici. GetObject () öğesinden döndürülen RemotingServer örneği "saydam proxy" olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="e772f-166">The RemotingServer instance returned from Activator.GetObject() is known as a "transparent proxy."</span></span> <span data-ttu-id="e772f-167">İstemcideki RemotingServer türü için ortak API 'yi uygular, ancak tüm yöntemler farklı bir işlemde veya makinede çalışan sunucu nesnesini çağırır.</span><span class="sxs-lookup"><span data-stu-id="e772f-167">It implements the public API for the RemotingServer type on the client, but all the methods call the server object running in a different process or machine.</span></span>  
  
#### <a name="creating-a-client-in-wcf"></a><span data-ttu-id="e772f-168">WCF 'de Istemci oluşturma</span><span class="sxs-lookup"><span data-stu-id="e772f-168">Creating a Client in WCF</span></span>  
 <span data-ttu-id="e772f-169">WCF 'deki eşdeğer adım, ara sunucuyu açıkça oluşturmak için bir kanal fabrikası kullanmayı içerir.</span><span class="sxs-lookup"><span data-stu-id="e772f-169">The equivalent step in WCF involves using a channel factory to create the proxy explicitly.</span></span> <span data-ttu-id="e772f-170">Uzaktan Iletişim gibi, proxy nesnesi, aşağıdaki örnekte olduğu gibi, sunucu üzerindeki işlemleri çağırmak için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="e772f-170">Like Remoting, the proxy object can be used to invoke operations on the server, like in the following example:</span></span>  
  
```csharp
NetTcpBinding binding = new NetTcpBinding();  
String url = "net.tcp://localhost:8000/wcfserver";  
EndpointAddress address = new EndpointAddress(url);  
ChannelFactory<IWCFServer> channelFactory =   
    new ChannelFactory<IWCFServer>(binding, address);  
IWCFServer server = channelFactory.CreateChannel();  
  
Customer customer = server.GetCustomer(42);  
Console.WriteLine($"  Customer {customer.FirstName} {customer.LastName} received.");
```  
  
 <span data-ttu-id="e772f-171">Bu örnek, en çok uzaktan Iletişim örneğine benzer olduğundan, kanal düzeyinde programlama gösterir.</span><span class="sxs-lookup"><span data-stu-id="e772f-171">This example shows programming at the channel level because it is most similar to the Remoting example.</span></span> <span data-ttu-id="e772f-172">Ayrıca, Visual Studio 'da istemci programlamayı basitleştirecek kod üreten **hizmet başvurusu Ekle** yaklaşımı de mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="e772f-172">Also available is the **Add Service Reference** approach in Visual Studio that generates code to simplify client programming.</span></span> <span data-ttu-id="e772f-173">Daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="e772f-173">For more information, see the following topics:</span></span>  
  
- [<span data-ttu-id="e772f-174">İstemci Kanal Düzeyi Programlama</span><span class="sxs-lookup"><span data-stu-id="e772f-174">Client Channel-Level Programming</span></span>](./extending/client-channel-level-programming.md)  
  
- [<span data-ttu-id="e772f-175">Nasıl yapılır: Hizmet başvurusu ekleme, güncelleştirme veya kaldırma</span><span class="sxs-lookup"><span data-stu-id="e772f-175">How to: Add, Update, or Remove a Service Reference</span></span>](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference)  
  
### <a name="serialization-usage"></a><span data-ttu-id="e772f-176">Serileştirme kullanımı</span><span class="sxs-lookup"><span data-stu-id="e772f-176">Serialization Usage</span></span>  
 <span data-ttu-id="e772f-177">Hem .NET Remoting hem de WCF, nesneleri istemci ile sunucu arasında göndermek için serileştirme kullanır, ancak bu önemli yollarla farklılık gösterir:</span><span class="sxs-lookup"><span data-stu-id="e772f-177">Both .NET Remoting and WCF use serialization to send objects between client and server, but they differ in these important ways:</span></span>  
  
1. <span data-ttu-id="e772f-178">Bunlar, serileştirildiklerinizi göstermek için farklı serileştiriciler ve kurallar kullanır.</span><span class="sxs-lookup"><span data-stu-id="e772f-178">They use different serializers and conventions to indicate what to serialize.</span></span>  
  
2. <span data-ttu-id="e772f-179">.NET uzaktan Iletişim, bir katmanda Yöntem veya özellik erişiminin, güvenlik sınırları genelinde olan diğer katmanda kod yürütmesine olanak tanıyan "başvuruya göre" serileştirmesini destekler.</span><span class="sxs-lookup"><span data-stu-id="e772f-179">.NET Remoting supports "by reference" serialization that allows method or property access on one tier to execute code on the other tier, which is across security boundaries.</span></span> <span data-ttu-id="e772f-180">Bu özellik güvenlik açıklarını açığa çıkarır ve uzaktan Iletişim uç noktalarının güvenilmeyen istemcilere hiçbir şekilde gösterilmemesi için önemli nedenlerden biridir.</span><span class="sxs-lookup"><span data-stu-id="e772f-180">This capability exposes security vulnerabilities and is one of the main reasons why Remoting endpoints should never be exposed to untrusted clients.</span></span>  
  
3. <span data-ttu-id="e772f-181">Uzaktan Iletişim tarafından kullanılan serileştirme geri çevrildi (serileştirilmeyen öğeleri açıkça hariç bırakır) ve WCF serileştirme kabul etme (hangi üyelerin serileştirilmek için açıkça işaretlenmesi).</span><span class="sxs-lookup"><span data-stu-id="e772f-181">Serialization used by Remoting is opt-out (explicitly exclude what not to serialize) and WCF serialization is opt-in (explicitly mark which members to serialize).</span></span>  
  
#### <a name="serialization-in-net-remoting"></a><span data-ttu-id="e772f-182">.NET Remoting 'de serileştirme</span><span class="sxs-lookup"><span data-stu-id="e772f-182">Serialization in .NET Remoting</span></span>  
 <span data-ttu-id="e772f-183">.NET uzaktan Iletişim, istemci ve sunucu arasında nesneleri serileştirmek ve seri durumdan çıkarmak için iki yolu destekler:</span><span class="sxs-lookup"><span data-stu-id="e772f-183">.NET Remoting supports two ways to serialize and deserialize objects between the client and server:</span></span>  
  
- <span data-ttu-id="e772f-184">*Değere göre* – nesnenin değerleri katman sınırları genelinde serileştirilir ve diğer katmanda bu nesnenin yeni bir örneği oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e772f-184">*By value* – the values of the object are serialized across tier boundaries, and a new instance of that object is created on the other tier.</span></span> <span data-ttu-id="e772f-185">Bu yeni örneğin yöntemlere veya özelliklerine yapılan çağrılar yalnızca yerel olarak yürütülür ve özgün nesneyi veya katmanı etkilemez.</span><span class="sxs-lookup"><span data-stu-id="e772f-185">Any calls to methods or properties of that new instance execute only locally and do not affect the original object or tier.</span></span>  
  
- <span data-ttu-id="e772f-186">*Başvuruya göre* – özel bir "nesne başvurusu" katman sınırları genelinde serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="e772f-186">*By reference* – a special "object reference" is serialized across tier boundaries.</span></span> <span data-ttu-id="e772f-187">Bir katman bu nesnenin yöntemleriyle veya özellikleriyle etkileşime geçtiğinde, özgün katmandaki özgün nesneye geri iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="e772f-187">When one tier interacts with methods or properties of that object, it communicates back to the original object on the original tier.</span></span> <span data-ttu-id="e772f-188">Başvuruya göre nesneler, istemci veya istemciden sunucuya kadar her iki yönde de akabilir.</span><span class="sxs-lookup"><span data-stu-id="e772f-188">By-reference objects can flow in either direction – server to client, or client to server.</span></span>  
  
 <span data-ttu-id="e772f-189">Remoting 'teki değer tabanlı türler, [Serializable] özniteliğiyle işaretlenir veya aşağıdaki örnekte olduğu gibi ISerializable uygular:</span><span class="sxs-lookup"><span data-stu-id="e772f-189">By-value types in Remoting are marked with the [Serializable] attribute or implement ISerializable, like in the following example:</span></span>  
  
```csharp
[Serializable]  
public class RemotingCustomer  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
    public int CustomerId { get; set; }  
}  
```  
  
 <span data-ttu-id="e772f-190">Başvuruya göre türler, aşağıdaki örnekte olduğu gibi MarshalByRefObject sınıfından türetilir:</span><span class="sxs-lookup"><span data-stu-id="e772f-190">By-reference types derive from the MarshalByRefObject class, like in the following example:</span></span>  
  
```csharp
public class RemotingCustomerReference : MarshalByRefObject  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
    public int CustomerId { get; set; }  
}  
```  
  
 <span data-ttu-id="e772f-191">Uzaktan Iletişimin başvuru nesnelerinin etkilerini anlamak son derece önemlidir.</span><span class="sxs-lookup"><span data-stu-id="e772f-191">It is extremely important to understand the implications of Remoting’s by-reference objects.</span></span> <span data-ttu-id="e772f-192">Herhangi bir katman (istemci veya sunucu) diğer katmana başvuruya göre bir nesne gönderiyorsa, tüm yöntem, nesnenin sahip olduğu katmanda yürütülür.</span><span class="sxs-lookup"><span data-stu-id="e772f-192">If either tier (client or server) sends a by-reference object to the other tier, all method calls execute back on the tier owning the object.</span></span> <span data-ttu-id="e772f-193">Örneğin, sunucu tarafından döndürülen bir başvuruya göre nesne üzerinde Yöntemler çağıran bir istemci, sunucuda kod yürütür.</span><span class="sxs-lookup"><span data-stu-id="e772f-193">For example, a client calling methods on a by-reference object returned by the server will execute code on the server.</span></span> <span data-ttu-id="e772f-194">Benzer şekilde, istemci tarafından sağlanmış bir başvuru nesnesi üzerinde Yöntemler çağıran bir sunucu, kodu istemciye geri yürütür.</span><span class="sxs-lookup"><span data-stu-id="e772f-194">Similarly, a server calling methods on a by-reference object provided by the client will execute code back on the client.</span></span> <span data-ttu-id="e772f-195">Bu nedenle, .NET Remoting kullanımı yalnızca tam olarak güvenilen ortamlarda önerilir.</span><span class="sxs-lookup"><span data-stu-id="e772f-195">For this reason, the use of .NET Remoting is recommended only within fully-trusted environments.</span></span> <span data-ttu-id="e772f-196">Güvenli bir .NET Remoting uç noktasının güvenilir olmayan istemcilere açık olması, uzaktan Iletişim sunucusu saldırılara karşı savunmasız hale getirir.</span><span class="sxs-lookup"><span data-stu-id="e772f-196">Exposing a public .NET Remoting endpoint to untrusted clients will make a Remoting server vulnerable to attack.</span></span>  
  
#### <a name="serialization-in-wcf"></a><span data-ttu-id="e772f-197">WCF 'de serileştirme</span><span class="sxs-lookup"><span data-stu-id="e772f-197">Serialization in WCF</span></span>  
 <span data-ttu-id="e772f-198">WCF yalnızca değere göre serileştirme destekler.</span><span class="sxs-lookup"><span data-stu-id="e772f-198">WCF supports only by-value serialization.</span></span> <span data-ttu-id="e772f-199">İstemci ve sunucu arasında Exchange için bir tür tanımlamanın en yaygın yolu aşağıdaki örnekte gibidir:</span><span class="sxs-lookup"><span data-stu-id="e772f-199">The most common way to define a type to exchange between client and server is like in the following example:</span></span>  
  
```csharp
[DataContract]  
public class WCFCustomer  
{  
    [DataMember]  
    public string FirstName { get; set; }  
  
    [DataMember]  
    public string LastName { get; set; }  
  
    [DataMember]  
    public int CustomerId { get; set; }  
}  
```  
  
 <span data-ttu-id="e772f-200">[DataContract] özniteliği bu türü, istemci ile sunucu arasında seri hale getirileve seri durumdan çıkarılacak bir şekilde tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e772f-200">The [DataContract] attribute identifies this type as one that can be serialized and deserialized between client and server.</span></span> <span data-ttu-id="e772f-201">[DataMember] özniteliği, serileştirme için tek tek özellikleri veya alanları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e772f-201">The [DataMember] attribute identifies the individual properties or fields to serialize.</span></span>  
  
 <span data-ttu-id="e772f-202">WCF, katmanlar arasında bir nesne gönderdiğinde, yalnızca değerleri seri hale getirir ve diğer katmanda nesnenin yeni bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e772f-202">When WCF sends an object across tiers, it serializes only the values and creates a new instance of the object on the other tier.</span></span> <span data-ttu-id="e772f-203">Nesne değerleri yalnızca yerel olarak oluşur; diğer katmanla aynı şekilde .NET Remoting ile başvuru nesneleriyle iletişim kurmazlar.</span><span class="sxs-lookup"><span data-stu-id="e772f-203">Any interactions with the values of the object occur only locally – they do not communicate with the other tier the way .NET Remoting by-reference objects do.</span></span> <span data-ttu-id="e772f-204">Daha fazla bilgi için bkz. [serileştirme ve seri durumundan çıkarma](./feature-details/serialization-and-deserialization.md).</span><span class="sxs-lookup"><span data-stu-id="e772f-204">For more information, see [Serialization and Deserialization](./feature-details/serialization-and-deserialization.md).</span></span>  
  
### <a name="exception-handling-capabilities"></a><span data-ttu-id="e772f-205">Özel durum Işleme özellikleri</span><span class="sxs-lookup"><span data-stu-id="e772f-205">Exception Handling Capabilities</span></span>  
  
#### <a name="exceptions-in-net-remoting"></a><span data-ttu-id="e772f-206">.NET Remoting 'teki özel durumlar</span><span class="sxs-lookup"><span data-stu-id="e772f-206">Exceptions in .NET Remoting</span></span>  
 <span data-ttu-id="e772f-207">Bir uzak sunucu tarafından oluşturulan özel durumlar serileştirilir, istemciye gönderilir ve başka bir özel durum gibi istemcide yerel olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e772f-207">Exceptions thrown by a Remoting server are serialized, sent to the client, and thrown locally on the client like any other exception.</span></span> <span data-ttu-id="e772f-208">Özel özel durumlar, özel durum türünü alt sınıflama tarafından, [Serializable] ile işaretleyerek oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="e772f-208">Custom exceptions can be created by sub-classing the Exception type and marking it with [Serializable].</span></span>   <span data-ttu-id="e772f-209">Çoğu Framework özel durumu zaten bu şekilde işaretlenir, bu sayede sunucuda sunucu tarafından oluşturulması, serileştirilmesi ve yeniden oluşturulması sağlanır.</span><span class="sxs-lookup"><span data-stu-id="e772f-209">Most framework exceptions are already marked in this way, allowing most to be thrown by the server, serialized, and re-thrown on the client.</span></span> <span data-ttu-id="e772f-210">Bu tasarım geliştirme sırasında kullanışlı olsa da, sunucu tarafı bilgileri istenmeden istemciye daha da açıklanamaz.</span><span class="sxs-lookup"><span data-stu-id="e772f-210">Though this design is convenient during development, server-side information can inadvertently be disclosed to the client.</span></span> <span data-ttu-id="e772f-211">Bu, uzaktan Iletişimin yalnızca tam güvenilir ortamlarda kullanılması gereken pek çok nedenden biridir.</span><span class="sxs-lookup"><span data-stu-id="e772f-211">This is one of many reasons Remoting should be used only in fully-trusted environments.</span></span>  
  
#### <a name="exceptions-and-faults-in-wcf"></a><span data-ttu-id="e772f-212">WCF 'de özel durumlar ve hatalar</span><span class="sxs-lookup"><span data-stu-id="e772f-212">Exceptions and Faults in WCF</span></span>  
 <span data-ttu-id="e772f-213">WCF, yanlışlıkla bilginin açığa çıkmasına yol açacağından sunucudan istemciye rastgele özel durum türleri döndürülmesine izin vermez.</span><span class="sxs-lookup"><span data-stu-id="e772f-213">WCF does not allow arbitrary exception types to be returned from the server to the client because it could lead to inadvertent information disclosure.</span></span> <span data-ttu-id="e772f-214">Bir hizmet işlemi beklenmeyen bir özel durum oluşturursa, istemci üzerinde genel amaçlı bir FaultException oluşturulmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="e772f-214">If a service operation throws an unexpected exception, it causes a general purpose FaultException to be thrown on the client.</span></span> <span data-ttu-id="e772f-215">Bu özel durum, sorunun neden veya nerede oluştuğunu ve bazı uygulamalar için yeterli bilgi taşımaz.</span><span class="sxs-lookup"><span data-stu-id="e772f-215">This exception does not carry any information why or where the problem occurred, and for some applications this is sufficient.</span></span> <span data-ttu-id="e772f-216">İstemciye daha zengin hata bilgilerini iletmeniz gereken uygulamalar, bir hata sözleşmesini tanımlayarak bunu yapın.</span><span class="sxs-lookup"><span data-stu-id="e772f-216">Applications that need to communicate richer error information to the client do this by defining a fault contract.</span></span>  
  
 <span data-ttu-id="e772f-217">Bunu yapmak için ilk olarak hata bilgilerini taşıyan bir [DataContract] türü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e772f-217">To do this, first create a [DataContract] type to carry the fault information.</span></span>  
  
```csharp
[DataContract]  
public class CustomerServiceFault  
{  
    [DataMember]  
    public string ErrorMessage { get; set; }  
  
    [DataMember]  
    public int CustomerId {get;set;}  
}  
```  
  
 <span data-ttu-id="e772f-218">Her bir hizmet işlemi için kullanılacak hata sözleşmesini belirtin.</span><span class="sxs-lookup"><span data-stu-id="e772f-218">Specify the fault contract to use for each service operation.</span></span>  
  
```csharp
[ServiceContract]  
public interface IWCFServer  
{  
    [OperationContract]  
    [FaultContract(typeof(CustomerServiceFault))]  
    Customer GetCustomer(int customerId);  
}  
```  
  
 <span data-ttu-id="e772f-219">Sunucu, bir FaultException oluşturarak hata koşullarını raporlar.</span><span class="sxs-lookup"><span data-stu-id="e772f-219">The server reports error conditions by throwing a FaultException.</span></span>  
  
```csharp
throw new FaultException<CustomerServiceFault>(  
    new CustomerServiceFault() {   
        CustomerId = customerId,   
        ErrorMessage = "Illegal customer Id"   
    });  
```  
  
 <span data-ttu-id="e772f-220">İstemci sunucuya bir istek yaptığında hataları normal özel durumlar olarak yakalayabilir.</span><span class="sxs-lookup"><span data-stu-id="e772f-220">And whenever the client makes a request to the server, it can catch faults as normal exceptions.</span></span>  
  
```csharp
try  
{  
    Customer customer = server.GetCustomer(-1);  
}  
catch (FaultException<CustomerServiceFault> fault)  
{  
    Console.WriteLine($"Fault received: {fault.Detail.ErrorMessage}");
}  
```  
  
 <span data-ttu-id="e772f-221">Hata sözleşmeleri hakkında daha fazla bilgi için bkz <xref:System.ServiceModel.FaultException>.</span><span class="sxs-lookup"><span data-stu-id="e772f-221">For more information about fault contracts, see <xref:System.ServiceModel.FaultException>.</span></span>  
  
### <a name="security-considerations"></a><span data-ttu-id="e772f-222">Güvenlik Değerlendirmeleri</span><span class="sxs-lookup"><span data-stu-id="e772f-222">Security Considerations</span></span>  
  
#### <a name="security-in-net-remoting"></a><span data-ttu-id="e772f-223">.NET Remoting 'de güvenlik</span><span class="sxs-lookup"><span data-stu-id="e772f-223">Security in .NET Remoting</span></span>  
 <span data-ttu-id="e772f-224">Bazı .NET uzaktan Iletişim kanalları, kanal katmanında (IPC ve TCP) kimlik doğrulaması ve şifreleme gibi güvenlik özelliklerini destekler.</span><span class="sxs-lookup"><span data-stu-id="e772f-224">Some .NET Remoting channels support security features such as authentication and encryption at the channel layer (IPC and TCP).</span></span> <span data-ttu-id="e772f-225">HTTP kanalı, kimlik doğrulaması ve şifreleme için Internet Information Services (IIS) kullanır.</span><span class="sxs-lookup"><span data-stu-id="e772f-225">The HTTP channel relies on Internet Information Services (IIS) for both authentication and encryption.</span></span> <span data-ttu-id="e772f-226">Bu desteğe rağmen, .NET Remoting güvenli olmayan bir iletişim protokolünü güvenilir hale getirmek ve yalnızca tam güvenilir ortamlarda kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e772f-226">Despite this support, you should consider .NET Remoting an unsecure communication protocol and use it only within fully-trusted environments.</span></span> <span data-ttu-id="e772f-227">Internet veya güvenilmeyen istemcilere genel bir uzaktan Iletişim uç noktası sunmaz.</span><span class="sxs-lookup"><span data-stu-id="e772f-227">Never expose a public Remoting endpoint to the Internet or untrusted clients.</span></span>  
  
#### <a name="security-in-wcf"></a><span data-ttu-id="e772f-228">WCF'de Güvenlik</span><span class="sxs-lookup"><span data-stu-id="e772f-228">Security in WCF</span></span>  
 <span data-ttu-id="e772f-229">WCF, .NET uzaktan Iletişim kutusunda bulunan güvenlik açıklarına yönelik güvenlik açıklarını ele almak için göz önünde bulundurularak tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="e772f-229">WCF was designed with security in mind, in part to address the kinds of vulnerabilities found in .NET Remoting.</span></span> <span data-ttu-id="e772f-230">WCF hem aktarım hem de ileti düzeyinde güvenlik sağlar ve kimlik doğrulama, yetkilendirme, şifreleme gibi birçok seçenek sunar.</span><span class="sxs-lookup"><span data-stu-id="e772f-230">WCF offers security at both the transport and message level, and offers many options for authentication, authorization, encryption, and so on.</span></span> <span data-ttu-id="e772f-231">Daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="e772f-231">For more information, see the following topics:</span></span>  
  
- [<span data-ttu-id="e772f-232">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="e772f-232">Security</span></span>](./feature-details/security.md)  
  
- [<span data-ttu-id="e772f-233">WCF güvenlik kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e772f-233">WCF Security Guidance</span></span>](./feature-details/security-guidance-and-best-practices.md)  
  
## <a name="migrating-to-wcf"></a><span data-ttu-id="e772f-234">WCF 'ye geçiş</span><span class="sxs-lookup"><span data-stu-id="e772f-234">Migrating to WCF</span></span>  
  
### <a name="why-migrate-from-remoting-to-wcf"></a><span data-ttu-id="e772f-235">Neden uzaktan Iletişim 'ten WCF 'ye geçirilir?</span><span class="sxs-lookup"><span data-stu-id="e772f-235">Why Migrate from Remoting to WCF?</span></span>  
  
- <span data-ttu-id="e772f-236">**.NET uzaktan Iletişim, eski bir üründür.**</span><span class="sxs-lookup"><span data-stu-id="e772f-236">**.NET Remoting is a legacy product.**</span></span> <span data-ttu-id="e772f-237">[.NET Remoting](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507%28v=vs.100%29)' de açıklandığı gibi, eski bir ürün olarak kabul edilir ve yeni geliştirme için önerilmez.</span><span class="sxs-lookup"><span data-stu-id="e772f-237">As described in [.NET Remoting](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507%28v=vs.100%29), it is considered a legacy product and is not recommended for new development.</span></span> <span data-ttu-id="e772f-238">WCF veya ASP.NET Web API 'SI, yeni ve mevcut uygulamalar için önerilir.</span><span class="sxs-lookup"><span data-stu-id="e772f-238">WCF or ASP.NET Web API are recommended for new and existing applications.</span></span>  
  
- <span data-ttu-id="e772f-239">**WCF platformlar arası standartları kullanır.**</span><span class="sxs-lookup"><span data-stu-id="e772f-239">**WCF uses cross-platform standards.**</span></span> <span data-ttu-id="e772f-240">WCF, platformlar arası birlikte çalışabilirlik ile tasarlanmıştı ve birçok sektör standardını (SOAP, WS-Security, WS-Trust, vb.) destekler.</span><span class="sxs-lookup"><span data-stu-id="e772f-240">WCF was designed with cross-platform interoperability in mind and supports many industry standards (SOAP, WS-Security, WS-Trust, etc.).</span></span> <span data-ttu-id="e772f-241">Bir WCF hizmeti, Windows dışındaki işletim sistemlerinde çalışan istemcilerle birlikte çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="e772f-241">A WCF service can interoperate with clients running on operating systems other than Windows.</span></span> <span data-ttu-id="e772f-242">Uzaktan iletişim, birincil olarak hem sunucu hem de istemci uygulamaların bir Windows işletim sisteminde .NET Framework kullanarak çalıştırdığı ortamlar için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="e772f-242">Remoting was designed primarily for environments where both the server and client applications run using the .NET framework on a Windows operating system.</span></span>  
  
- <span data-ttu-id="e772f-243">**WCF yerleşik güvenliğe sahiptir.**</span><span class="sxs-lookup"><span data-stu-id="e772f-243">**WCF has built-in security.**</span></span> <span data-ttu-id="e772f-244">WCF güvenlik göz önünde bulundurularak tasarlandı ve kimlik doğrulama, aktarım düzeyi güvenliği, ileti düzeyi güvenlik vb. için birçok seçenek sunar. Uzaktan iletişim, uygulamaların birlikte çalışabilmesini ve güvenilir olmayan ortamlarda güvenli hale getirmek üzere tasarlanmadığı için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="e772f-244">WCF was designed with security in mind and offers many options for authentication, transport level security, message level security, etc. Remoting was designed to make it easy for applications to interoperate but was not designed to be secure in non-trusted environments.</span></span> <span data-ttu-id="e772f-245">WCF hem güvenilen hem de güvenilmeyen ortamlarda çalışacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="e772f-245">WCF was designed to work in both trusted and non-trusted environments.</span></span>  
  
### <a name="migration-recommendations"></a><span data-ttu-id="e772f-246">Geçiş önerileri</span><span class="sxs-lookup"><span data-stu-id="e772f-246">Migration Recommendations</span></span>  
 <span data-ttu-id="e772f-247">.NET uzaktan Iletişim 'dan WCF 'ye geçiş için önerilen adımlar aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="e772f-247">The following are the recommended steps to migrate from .NET Remoting to WCF:</span></span>  
  
- <span data-ttu-id="e772f-248">**Hizmet sözleşmesini oluşturun.**</span><span class="sxs-lookup"><span data-stu-id="e772f-248">**Create the service contract.**</span></span> <span data-ttu-id="e772f-249">Hizmet arabirimi türlerinizi tanımlayın ve bunları [ServiceContract] özniteliğiyle işaretleyin. İstemcilerin [OperationContract] ile çağrı yapmasına izin verilecek tüm yöntemleri işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="e772f-249">Define your service interface types, and mark them with the [ServiceContract] attribute.Mark all the methods the clients will be allowed to call with [OperationContract].</span></span>  
  
- <span data-ttu-id="e772f-250">**Veri sözleşmesini oluşturun.**</span><span class="sxs-lookup"><span data-stu-id="e772f-250">**Create the data contract.**</span></span> <span data-ttu-id="e772f-251">Sunucu ve istemci arasında değiş tokuş edilecek veri türlerini tanımlayın ve bunları [DataContract] özniteliğiyle işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="e772f-251">Define the data types that will be exchanged between server and client, and mark them with the [DataContract] attribute.</span></span> <span data-ttu-id="e772f-252">İstemcinin [DataMember] ile kullanmasına izin verilecek tüm alanları ve özellikleri işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="e772f-252">Mark all the fields and properties the client will be allowed to use with [DataMember].</span></span>  
  
- <span data-ttu-id="e772f-253">**Hata sözleşmesini oluşturun (isteğe bağlı).**</span><span class="sxs-lookup"><span data-stu-id="e772f-253">**Create the fault contract (optional).**</span></span> <span data-ttu-id="e772f-254">Hatalarla karşılaşıldığında sunucu ile istemci arasında değiş tokuş edilecek türleri oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e772f-254">Create the types that will be exchanged between server and client when errors are encountered.</span></span> <span data-ttu-id="e772f-255">Bu türleri seri hale getirilebilir hale getirmek için [DataContract] ve [DataMember] ile işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="e772f-255">Mark these types with [DataContract] and [DataMember] to make them serializable.</span></span> <span data-ttu-id="e772f-256">[OperationContract] ile işaretlediğiniz tüm hizmet işlemleri için, hangi hataların dönebileceği göstermek için bunları [FaultContract] ile de işaretleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e772f-256">For all service operations you marked with [OperationContract], also mark them with [FaultContract] to indicate which errors they may return.</span></span>  
  
- <span data-ttu-id="e772f-257">**Hizmeti yapılandırın ve barındırın.**</span><span class="sxs-lookup"><span data-stu-id="e772f-257">**Configure and host the service.**</span></span> <span data-ttu-id="e772f-258">Hizmet sözleşmesi oluşturulduktan sonra, bir sonraki adım, hizmeti bir uç noktada kullanıma sunmak için bir bağlama yapılandırmaktır.</span><span class="sxs-lookup"><span data-stu-id="e772f-258">Once the service contract has been created, the next step is to configure a binding to expose the service at an endpoint.</span></span> <span data-ttu-id="e772f-259">Daha fazla bilgi için bkz [. uç noktalar: Adresler, bağlamalar ve sözleşmeler](./feature-details/endpoints-addresses-bindings-and-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="e772f-259">For more information, see [Endpoints: Addresses, Bindings, and Contracts](./feature-details/endpoints-addresses-bindings-and-contracts.md).</span></span>  
  
 <span data-ttu-id="e772f-260">Uzaktan Iletişim uygulaması WCF 'ye geçirildiğinde, .NET uzaktan Iletişim üzerinde bağımlılıkları kaldırmak yine de önemlidir.</span><span class="sxs-lookup"><span data-stu-id="e772f-260">Once a Remoting application has been migrated to WCF, it is still important to remove dependencies on .NET Remoting.</span></span> <span data-ttu-id="e772f-261">Bu, tüm uzaktan Iletişim açıklarının uygulamadan kaldırılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="e772f-261">This ensures that any Remoting vulnerabilities are removed from the application.</span></span> <span data-ttu-id="e772f-262">Bu adımlar şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="e772f-262">These steps include the following:</span></span>  
  
- <span data-ttu-id="e772f-263">**MarshalByRefObject kullanımını durdur.**</span><span class="sxs-lookup"><span data-stu-id="e772f-263">**Discontinue use of MarshalByRefObject.**</span></span> <span data-ttu-id="e772f-264">MarshalByRefObject türü yalnızca uzaktan Iletişim için bulunur ve WCF tarafından kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="e772f-264">The MarshalByRefObject type exists only for Remoting and is not used by WCF.</span></span> <span data-ttu-id="e772f-265">Alt sınıf MarshalByRefObject olan herhangi bir uygulama türü kaldırılmalı veya değiştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="e772f-265">Any application types that sub-class MarshalByRefObject should be removed or changed.</span></span>  
  
- <span data-ttu-id="e772f-266">**[Serializable] ve ISerializable kullanımını durdur.**</span><span class="sxs-lookup"><span data-stu-id="e772f-266">**Discontinue use of [Serializable] and ISerializable.**</span></span> <span data-ttu-id="e772f-267">[Serializable] özniteliği ve ISerializable arabirimi, başlangıçta güvenilen ortamlarda türleri seri hale getirmek için tasarlanmıştır ve uzaktan Iletişim tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e772f-267">The [Serializable] attribute and ISerializable interface were originally designed to serialize types within trusted environments, and they are used by Remoting.</span></span> <span data-ttu-id="e772f-268">WCF serileştirme, [DataContract] ve [DataMember] ile işaretlenmiş türlere dayanır.</span><span class="sxs-lookup"><span data-stu-id="e772f-268">WCF serialization relies on types being marked with [DataContract] and [DataMember].</span></span> <span data-ttu-id="e772f-269">Bir uygulama tarafından kullanılan veri türleri ISerializable veya [Serializable] kullanmak için değil [DataContract] kullanacak şekilde değiştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="e772f-269">Data types used by an application should be modified to use [DataContract] and not to use ISerializable or [Serializable].</span></span>  
  
### <a name="migration-scenarios"></a><span data-ttu-id="e772f-270">Geçiş senaryoları</span><span class="sxs-lookup"><span data-stu-id="e772f-270">Migration Scenarios</span></span>  
 <span data-ttu-id="e772f-271">Şimdi, WCF 'de aşağıdaki genel uzaktan Iletişim senaryolarını nasıl gerçekleştireceğinizi görelim:</span><span class="sxs-lookup"><span data-stu-id="e772f-271">Now let’s see how to accomplish the following common Remoting scenarios in WCF:</span></span>  
  
1. <span data-ttu-id="e772f-272">Sunucu istemciye bir nesne değeri döndürür</span><span class="sxs-lookup"><span data-stu-id="e772f-272">Server returns an object by-value to the client</span></span>  
  
2. <span data-ttu-id="e772f-273">Sunucu, istemciye başvuruya göre bir nesne döndürür</span><span class="sxs-lookup"><span data-stu-id="e772f-273">Server returns an object by-reference to the client</span></span>  
  
3. <span data-ttu-id="e772f-274">İstemci sunucuya bir nesne değere göre gönderir</span><span class="sxs-lookup"><span data-stu-id="e772f-274">Client sends an object by-value to the server</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e772f-275">İstemciden sunucuya bir nesne başvuruya göre göndermeye, WCF 'de izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="e772f-275">Sending an object by-reference from the client to the server is not allowed in WCF.</span></span>  
  
 <span data-ttu-id="e772f-276">Bu senaryolarla okurken, .NET uzaktan Iletişim için temel arabirimlerimizin aşağıdaki örnekteki gibi göründüğünü varsayın.</span><span class="sxs-lookup"><span data-stu-id="e772f-276">When reading through these scenarios, assume our baseline interfaces for .NET Remoting look like the following example.</span></span> <span data-ttu-id="e772f-277">Yalnızca WCF 'nin eşdeğer işlevselliği uygulamak için nasıl kullanılacağını göstermek istediğimizden, .NET Remoting uygulaması burada önemli değildir.</span><span class="sxs-lookup"><span data-stu-id="e772f-277">The .NET Remoting implementation is not important here because we want to illustrate only how to use WCF to implement equivalent functionality.</span></span>  
  
```csharp
public class RemotingServer : MarshalByRefObject  
{  
    // Demonstrates server returning object by-value  
    public Customer GetCustomer(int customerId) {…}  
  
    // Demonstrates server returning object by-reference  
    public CustomerReference GetCustomerReference(int customerId) {…}  
  
    // Demonstrates client passing object to server by-value  
    public bool UpdateCustomer(Customer customer) {…}  
}  
```  
  
#### <a name="scenario-1-service-returns-an-object-by-value"></a><span data-ttu-id="e772f-278">Senaryo 1: Hizmet bir nesne değere göre döndürüyor</span><span class="sxs-lookup"><span data-stu-id="e772f-278">Scenario 1: Service Returns an Object by Value</span></span>  
 <span data-ttu-id="e772f-279">Bu senaryoda istemciye değerine göre bir nesne döndüren bir sunucu gösterilir.</span><span class="sxs-lookup"><span data-stu-id="e772f-279">This scenario demonstrates a server returning an object to the client by value.</span></span> <span data-ttu-id="e772f-280">WCF her zaman sunucudan değere göre nesneleri döndürür, bu nedenle aşağıdaki adımlar normal bir WCF hizmetinin nasıl oluşturulacağını açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="e772f-280">WCF always returns objects from the server by value, so the following steps simply describe how to build a normal WCF service.</span></span>  
  
1. <span data-ttu-id="e772f-281">WCF hizmeti için bir ortak arabirim tanımlayarak başlayın ve [ServiceContract] özniteliğiyle işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="e772f-281">Start by defining a public interface for the WCF service and mark it with the [ServiceContract] attribute.</span></span> <span data-ttu-id="e772f-282">İstemcimizin çağıracağız sunucu tarafı yöntemleri belirlemek için [OperationContract] kullanıyoruz.</span><span class="sxs-lookup"><span data-stu-id="e772f-282">We use [OperationContract] to identify the server-side methods our client will call.</span></span>  
  
   ```csharp
   [ServiceContract]  
   public interface ICustomerService  
   {  
       [OperationContract]  
       Customer GetCustomer(int customerId);  
  
       [OperationContract]  
       bool UpdateCustomer(Customer customer);  
   }  
   ```  
  
2. <span data-ttu-id="e772f-283">Bir sonraki adım, bu hizmet için veri sözleşmesinin oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="e772f-283">The next step is to create the data contract for this service.</span></span> <span data-ttu-id="e772f-284">Bunu, [DataContract] özniteliğiyle işaretlenmiş sınıflar (arabirimler değil) oluşturarak yapacağız.</span><span class="sxs-lookup"><span data-stu-id="e772f-284">We do this by creating classes (not interfaces) marked with the [DataContract] attribute.</span></span> <span data-ttu-id="e772f-285">Hem istemci hem de sunucu için görünür olmasını istediğimiz her bir özellik veya alan [DataMember] ile işaretlenmiş.</span><span class="sxs-lookup"><span data-stu-id="e772f-285">The individual properties or fields we want visible to both client and server are marked with [DataMember].</span></span> <span data-ttu-id="e772f-286">Türetilmiş türlerin izin verilmesini istiyoruz, bunları tanımlamak için [KnownType] özniteliğini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e772f-286">If we want derived types to be allowed, we must use the [KnownType] attribute to identify them.</span></span> <span data-ttu-id="e772f-287">WCF, bu hizmet için yalnızca seri hale getirilebilir veya seri durumdan çıkarılan türler hizmet arabirimindeki ve bu "bilinen türler" olur.</span><span class="sxs-lookup"><span data-stu-id="e772f-287">The only types WCF will allow to be serialized or deserialized for this service are those in the service interface and these "known types".</span></span> <span data-ttu-id="e772f-288">Bu listede olmayan başka bir türü alışverişi yapılmaya çalışılması reddedilir.</span><span class="sxs-lookup"><span data-stu-id="e772f-288">Attempting to exchange any other type not in this list will be rejected.</span></span>  
  
   ```csharp
   [DataContract]  
   [KnownType(typeof(PremiumCustomer))]  
   public class Customer  
   {  
       [DataMember]  
       public string FirstName { get; set; }  
  
       [DataMember]  
       public string LastName { get; set; }  
  
       [DataMember]  
       public int CustomerId { get; set; }  
   }  
  
   [DataContract]  
   public class PremiumCustomer : Customer   
   {  
       [DataMember]  
       public int AccountId { get; set; }  
   }  
   ```  
  
3. <span data-ttu-id="e772f-289">Ardından, hizmet arabirimi için uygulama sağlıyoruz.</span><span class="sxs-lookup"><span data-stu-id="e772f-289">Next, we provide the implementation for the service interface.</span></span>  
  
   ```csharp  
   public class CustomerService : ICustomerService  
   {  
       public Customer GetCustomer(int customerId)  
       {  
           // read from database  
       }  
  
       public bool UpdateCustomer(Customer customer)  
       {  
           // write to database  
       }  
   }  
   ```  
  
4. <span data-ttu-id="e772f-290">WCF hizmetini çalıştırmak için belirli bir WCF bağlamasını kullanarak bu hizmet arabirimini belirli bir URL 'de kullanıma sunan bir uç nokta bildirmemiz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e772f-290">To run the WCF service, we need to declare an endpoint that exposes that service interface at a specific URL using a specific WCF binding.</span></span> <span data-ttu-id="e772f-291">Bu, genellikle aşağıdaki bölümler sunucu projesinin Web. config dosyasına eklenerek yapılır.</span><span class="sxs-lookup"><span data-stu-id="e772f-291">This is typically done by adding the following sections to the server project’s web.config file.</span></span>  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <services>  
          <service name="Server.CustomerService">  
            <endpoint address="http://localhost:8083/CustomerService"  
                      binding="basicHttpBinding"  
                      contract="Shared.ICustomerService" />  
          </service>  
        </services>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
5. <span data-ttu-id="e772f-292">WCF hizmeti daha sonra aşağıdaki kodla başlatılabilir:</span><span class="sxs-lookup"><span data-stu-id="e772f-292">The WCF service can then be started with the following code:</span></span>  
  
   ```csharp
   ServiceHost customerServiceHost = new ServiceHost(typeof(CustomerService));  
       customerServiceHost.Open();  
   ```  
  
     <span data-ttu-id="e772f-293">Bu ServiceHost başlatıldığında, uygun sözleşmeyi, bağlamayı ve uç noktayı oluşturmak için Web. config dosyasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="e772f-293">When this ServiceHost is started, it uses the web.config file to establish the proper contract, binding and endpoint.</span></span> <span data-ttu-id="e772f-294">Yapılandırma dosyaları hakkında daha fazla bilgi için bkz. [yapılandırma dosyalarını kullanarak hizmetleri yapılandırma](./configuring-services-using-configuration-files.md).</span><span class="sxs-lookup"><span data-stu-id="e772f-294">For more information about configuration files, see [Configuring Services Using Configuration Files](./configuring-services-using-configuration-files.md).</span></span> <span data-ttu-id="e772f-295">Sunucunun başlatılmasına yönelik bu stil, kendi kendine barındırma olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="e772f-295">This style of starting the server is known as self-hosting.</span></span> <span data-ttu-id="e772f-296">WCF hizmetlerini barındırmak için diğer seçimler hakkında daha fazla bilgi edinmek için bkz. [barındırma hizmetleri](./hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="e772f-296">To learn more about other choices for hosting WCF services, see [Hosting Services](./hosting-services.md).</span></span>  
  
6. <span data-ttu-id="e772f-297">İstemci projenin App. config dosyasının, hizmetin uç noktası için eşleşen bağlama bilgilerini bildirmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="e772f-297">The client project’s app.config must declare matching binding information for the service’s endpoint.</span></span> <span data-ttu-id="e772f-298">Visual Studio 'da bunu yapmanın en kolay yolu, App. config dosyasını otomatik olarak güncelleştirecek **hizmet başvurusu Ekle**kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="e772f-298">The easiest way to do this in Visual Studio is to use **Add Service Reference**, which will automatically update the app.config file.</span></span> <span data-ttu-id="e772f-299">Alternatif olarak, aynı değişiklikler el ile de eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="e772f-299">Alternatively, these same changes can be added manually.</span></span>  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <client>  
          <endpoint name="customerservice"  
                    address="http://localhost:8083/CustomerService"  
                    binding="basicHttpBinding"  
                    contract="Shared.ICustomerService"/>  
        </client>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
     <span data-ttu-id="e772f-300">**Hizmet başvurusu Ekle**kullanma hakkında daha fazla bilgi için bkz [. nasıl yapılır: Hizmet başvurusu](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference)ekleyin, güncelleştirin veya kaldırın.</span><span class="sxs-lookup"><span data-stu-id="e772f-300">For more information about using **Add Service Reference**, see [How to: Add, Update, or Remove a Service Reference](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference).</span></span>  
  
7. <span data-ttu-id="e772f-301">Artık WCF hizmetini istemciden çağırabiliriz.</span><span class="sxs-lookup"><span data-stu-id="e772f-301">Now we can call the WCF service from the client.</span></span> <span data-ttu-id="e772f-302">Bu, söz konusu hizmet için bir kanal fabrikası oluşturup bunu bir kanal için sorarak ve bu kanalda istediğiniz yöntemi doğrudan çağırarak yaptık.</span><span class="sxs-lookup"><span data-stu-id="e772f-302">We do this by creating a channel factory for that service, asking it for a channel, and directly calling the method we want on that channel.</span></span> <span data-ttu-id="e772f-303">Kanal hizmetin arabirimini gerçekleştirdiğinden ve temel alınan istek/yanıt mantığını bizim için işletiğinden bunu yapabiliriz.</span><span class="sxs-lookup"><span data-stu-id="e772f-303">We can do this because the channel implements the service’s interface and handles the underlying request/reply logic for us.</span></span> <span data-ttu-id="e772f-304">Bu yöntem çağrısından gelen dönüş değeri, sunucu yanıtının Serisi kaldırılan kopyasıdır.</span><span class="sxs-lookup"><span data-stu-id="e772f-304">The return value from that method call is the deserialized copy of the server’s response.</span></span>  
  
   ```csharp
   ChannelFactory<ICustomerService> factory =  
       new ChannelFactory<ICustomerService>("customerservice");  
   ICustomerService service = factory.CreateChannel();  
   Customer customer = service.GetCustomer(42);  
   Console.WriteLine($"  Customer {customer.FirstName} {customer.LastName} received.");
   ```  
  
 <span data-ttu-id="e772f-305">Sunucudan istemciye WCF tarafından döndürülen nesneler her zaman değere göre yapılır.</span><span class="sxs-lookup"><span data-stu-id="e772f-305">Objects returned by WCF from the server to the client are always by value.</span></span> <span data-ttu-id="e772f-306">Nesneler, sunucu tarafından gönderilen verilerin seri durumdan çıkarılmakta.</span><span class="sxs-lookup"><span data-stu-id="e772f-306">The objects are deserialized copies of the data sent by the server.</span></span> <span data-ttu-id="e772f-307">İstemci, geri çağırmalar aracılığıyla sunucu kodu çağırma tehlikiyeti olmadan bu yerel kopyalara Yöntemler çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="e772f-307">The client can call methods on these local copies without any danger of invoking server code through callbacks.</span></span>  
  
#### <a name="scenario-2-server-returns-an-object-by-reference"></a><span data-ttu-id="e772f-308">Senaryo 2: Sunucu, başvuruya göre bir nesne döndürüyor</span><span class="sxs-lookup"><span data-stu-id="e772f-308">Scenario 2: Server Returns an Object By Reference</span></span>  
 <span data-ttu-id="e772f-309">Bu senaryoda, istemciye başvuruya göre bir nesne sağlayan sunucu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e772f-309">This scenario demonstrates the server providing an object to the client by reference.</span></span> <span data-ttu-id="e772f-310">.NET uzaktan Iletişim kutusunda, bu, başvuruya göre seri hale getirilen MarshalByRefObject öğesinden türetilen herhangi bir tür için otomatik olarak işlenir.</span><span class="sxs-lookup"><span data-stu-id="e772f-310">In .NET Remoting, this is handled automatically for any type derived from MarshalByRefObject, which is serialized by-reference.</span></span> <span data-ttu-id="e772f-311">Bu senaryonun bir örneği, birden çok istemcinin bağımsız oturumlı sunucu tarafı nesnelerine sahip olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="e772f-311">An example of this scenario is allowing multiple clients to have independent sessionful server-side objects.</span></span> <span data-ttu-id="e772f-312">Daha önce belirtildiği gibi, bir WCF hizmeti tarafından döndürülen nesneler her zaman değere göre yapılır, bu nedenle bir başvuruya göre nesnenin doğrudan eşdeğeri olmaz, ancak bir <xref:System.ServiceModel.EndpointAddress10> nesne kullanarak başvuru semantiğine benzer bir şey elde etmek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="e772f-312">As previously mentioned, objects returned by a WCF service are always by value, so there is no direct equivalent of a by-reference object, but it is possible to achieve something similar to by-reference semantics using an <xref:System.ServiceModel.EndpointAddress10> object.</span></span> <span data-ttu-id="e772f-313">Bu, istemci tarafından sunucuda bir sessionby başvuruya göre nesne almak için kullanılabilen, seri hale getirilebilir bir nesne nesnesidir.</span><span class="sxs-lookup"><span data-stu-id="e772f-313">This is a serializable by-value object that can be used by the client to obtain a sessionful by-reference object on the server.</span></span> <span data-ttu-id="e772f-314">Bu, bağımsız oturumlarla aynı sunucu tarafı nesneleriyle birden çok istemcisine sahip olan senaryoya izin vermez.</span><span class="sxs-lookup"><span data-stu-id="e772f-314">This enables the scenario of having multiple clients with independent sessionful server-side objects.</span></span>  
  
1. <span data-ttu-id="e772f-315">İlk olarak, sessionobject nesnesine karşılık gelen bir WCF hizmeti sözleşmesi tanımlamamız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e772f-315">First, we need to define a WCF service contract that corresponds to the sessionful object itself.</span></span>  
  
   ```csharp
   [ServiceContract(SessionMode = SessionMode.Allowed)]  
       public interface ISessionBoundObject  
       {  
           [OperationContract]  
           string GetCurrentValue();  
  
           [OperationContract]  
           void SetCurrentValue(string value);  
       }  
   ```  
  
    > [!TIP]
    >  <span data-ttu-id="e772f-316">Oturumsuz nesnenin [ServiceContract] ile işaretlendiğine dikkat edin. Bu, normal bir WCF hizmeti arabirimi haline gelir.</span><span class="sxs-lookup"><span data-stu-id="e772f-316">Notice that the sessionful object is marked with [ServiceContract], making it a normal WCF service interface.</span></span> <span data-ttu-id="e772f-317">SessionMode özelliği ayarlandığında, bu bir sessionservice olacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e772f-317">Setting the SessionMode property indicates it will be a sessionful service.</span></span> <span data-ttu-id="e772f-318">WCF 'de oturum, iki uç nokta arasında gönderilen birden fazla iletiyi eş bir şekilde ilişkilendirme yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="e772f-318">In WCF, a session is a way of correlating multiple messages sent between two endpoints.</span></span> <span data-ttu-id="e772f-319">Bu, bir istemci bu hizmete bir bağlantı edinirse, istemci ile sunucu arasında bir oturum kurulacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="e772f-319">This means that once a client obtains a connection to this service, a session will be established between the client and the server.</span></span> <span data-ttu-id="e772f-320">İstemci, bu tek oturumdaki tüm etkileşimleri için sunucu tarafı nesnesinin tek bir benzersiz örneğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="e772f-320">The client will use a single unique instance of the server-side object for all its interactions within this single session.</span></span>  
  
2. <span data-ttu-id="e772f-321">Daha sonra, bu hizmet arabiriminin uygulamasını sağlamamız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e772f-321">Next, we need to provide the implementation of this service interface.</span></span> <span data-ttu-id="e772f-322">Bunu [ServiceBehavior] ile belirterek ve InstanceContextMode 'i ayarlayarak, her oturum için bu türün benzersiz bir örneğini kullanmak istediğimizi anladık.</span><span class="sxs-lookup"><span data-stu-id="e772f-322">By denoting it with [ServiceBehavior] and setting the InstanceContextMode, we tell WCF we want to use a unique instance of this type for an each session.</span></span>  
  
   ```csharp
   [ServiceBehavior(InstanceContextMode = InstanceContextMode.PerSession)]  
       public class MySessionBoundObject : ISessionBoundObject  
       {  
           private string _value;  
  
           public string GetCurrentValue()  
           {  
               return _value;  
           }  
  
           public void SetCurrentValue(string val)  
           {  
               _value = val;  
           }  
  
       }  
   ```  
  
3. <span data-ttu-id="e772f-323">Şimdi bu oturumsuz nesnenin bir örneğini elde etmek için bir yol gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="e772f-323">Now we need a way to obtain an instance of this sessionful object.</span></span> <span data-ttu-id="e772f-324">Bunu, bir EndpointAddress10 nesnesi döndüren başka bir WCF hizmeti arabirimi oluşturarak yapacağız.</span><span class="sxs-lookup"><span data-stu-id="e772f-324">We do this by creating another WCF service interface that returns an EndpointAddress10 object.</span></span> <span data-ttu-id="e772f-325">Bu, istemcinin oturumsuz nesneyi oluşturmak için kullanabileceği bir uç noktanın seri hale getirilebilir bir biçimidir.</span><span class="sxs-lookup"><span data-stu-id="e772f-325">This is a serializable form of an endpoint that the client can use to create the sessionful object.</span></span>  
  
   ```csharp
   [ServiceContract]  
       public interface ISessionBoundFactory  
       {  
           [OperationContract]  
           EndpointAddress10 GetInstanceAddress();  
       }  
   ```  
  
     <span data-ttu-id="e772f-326">Bu WCF hizmetini uyguladık:</span><span class="sxs-lookup"><span data-stu-id="e772f-326">And we implement this WCF service:</span></span>  
  
   ```csharp
   public class SessionBoundFactory : ISessionBoundFactory  
       {  
           public static ChannelFactory<ISessionBoundObject> _factory =   
               new ChannelFactory<ISessionBoundObject>("sessionbound");  
 
           public SessionBoundFactory()  
           {  
           }  
  
           public EndpointAddress10 GetInstanceAddress()  
           {  
               IClientChannel channel = (IClientChannel)_factory.CreateChannel();  
               return EndpointAddress10.FromEndpointAddress(channel.RemoteAddress);  
           }  
       }  
   ```  
  
     <span data-ttu-id="e772f-327">Bu uygulama, oturumsuz nesneler oluşturmak için tek bir kanal fabrikası sağlar.</span><span class="sxs-lookup"><span data-stu-id="e772f-327">This implementation maintains a singleton channel factory to create sessionful objects.</span></span> <span data-ttu-id="e772f-328">GetInstanceAddress () çağrıldığında, bir kanal oluşturur ve bu kanalla ilişkili uzak adresi etkin bir şekilde işaret eden bir EndpointAddress10 nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e772f-328">When GetInstanceAddress() is called, it creates a channel and creates an EndpointAddress10 object that effectively points to the remote address associated with this channel.</span></span> <span data-ttu-id="e772f-329">EndpointAddress10 yalnızca istemciye değere göre döndürülebilecek bir veri türüdür.</span><span class="sxs-lookup"><span data-stu-id="e772f-329">EndpointAddress10 is simply a data type that can be returned to the client by-value.</span></span>  
  
4. <span data-ttu-id="e772f-330">Aşağıdaki örnekte gösterildiği gibi aşağıdaki iki şeyi yaparak sunucunun yapılandırma dosyasını değiştirmemiz gerekir:</span><span class="sxs-lookup"><span data-stu-id="e772f-330">We need to modify the server’s configuration file by doing the following two things as shown in the example below:</span></span>  
  
    1. <span data-ttu-id="e772f-331">Oturumsuz \<nesnenin bitiş noktasını açıklayan bir istemci > bölümü bildirin.</span><span class="sxs-lookup"><span data-stu-id="e772f-331">Declare a \<client> section that describes the endpoint for the sessionful object.</span></span> <span data-ttu-id="e772f-332">Bu durum, sunucu aynı zamanda bir istemci görevi görtiğinden gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e772f-332">This is necessary because the server also acts as a client in this situation.</span></span>  
  
    2. <span data-ttu-id="e772f-333">Fabrika ve oturumsuz nesne için uç noktalar bildirin.</span><span class="sxs-lookup"><span data-stu-id="e772f-333">Declare endpoints for the factory and sessionful object.</span></span> <span data-ttu-id="e772f-334">Bu, istemcinin EndpointAddress10 almak ve Oturumsuz kanalı oluşturmak için hizmet uç noktalarıyla iletişim kurmasına izin vermek için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e772f-334">This is necessary to allow the client to communicate with the service endpoints to acquire the EndpointAddress10 and to create the sessionful channel.</span></span>  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
         <client>  
          <endpoint name="sessionbound"  
                    address="net.tcp://localhost:8081/SessionBoundObject"  
                    binding="netTcpBinding"  
                    contract="Shared.ISessionBoundObject"/>  
        </client>  
        <services>  
          <service name="Server.CustomerService">  
            <endpoint address="http://localhost:8083/CustomerService"  
                      binding="basicHttpBinding"  
                      contract="Shared.ICustomerService" />  
          </service>  
          <service name="Server.MySessionBoundObject">  
            <endpoint address="net.tcp://localhost:8081/SessionBoundObject"  
                      binding="netTcpBinding"  
                      contract="Shared.ISessionBoundObject" />  
          </service>  
          <service name="Server.SessionBoundFactory">  
            <endpoint address="net.tcp://localhost:8081/SessionBoundFactory"  
                      binding="netTcpBinding"  
                      contract="Shared.ISessionBoundFactory" />  
          </service>  
        </services>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
     <span data-ttu-id="e772f-335">Bu hizmetleri başlatabiliriz:</span><span class="sxs-lookup"><span data-stu-id="e772f-335">And then we can start these services:</span></span>  
  
   ```csharp
   ServiceHost factoryHost = new ServiceHost(typeof(SessionBoundFactory));  
   factoryHost.Open();  
  
   ServiceHost sessionHost = new ServiceHost(typeof(MySessionBoundObject));  
   sessionHost.Open();  
   ```  
  
5. <span data-ttu-id="e772f-336">Bu uç noktaları projenin App. config dosyasında bildirerek istemciyi yapılandıracağız.</span><span class="sxs-lookup"><span data-stu-id="e772f-336">We configure the client by declaring these same endpoints in its project’s app.config file.</span></span>  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <client>  
          <endpoint name="customerservice"  
                    address="http://localhost:8083/CustomerService"  
                    binding="basicHttpBinding"  
                    contract="Shared.ICustomerService"/>  
          <endpoint name="sessionbound"  
                    address="net.tcp://localhost:8081/SessionBoundObject"  
                    binding="netTcpBinding"  
                    contract="Shared.ISessionBoundObject"/>  
          <endpoint name="factory"  
                    address="net.tcp://localhost:8081/SessionBoundFactory"  
                    binding="netTcpBinding"  
                    contract="Shared.ISessionBoundFactory"/>  
        </client>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
6. <span data-ttu-id="e772f-337">Bu oturumsuz nesneyi oluşturmak ve kullanmak için, istemcinin aşağıdaki adımları yapması gerekir:</span><span class="sxs-lookup"><span data-stu-id="e772f-337">In order to create and use this sessionful object, the client must do the following steps:</span></span>  
  
    1. <span data-ttu-id="e772f-338">ISessionBoundFactory hizmetine bir kanal oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e772f-338">Create a channel to the ISessionBoundFactory service.</span></span>  
  
    2. <span data-ttu-id="e772f-339">Bu kanalı, bir EndpointAddress10 almak için bu hizmeti çağırmak üzere kullanın.</span><span class="sxs-lookup"><span data-stu-id="e772f-339">Use that channel to invoke that service to obtain an EndpointAddress10.</span></span>  
  
    3. <span data-ttu-id="e772f-340">Oturumsuz bir nesne almak için bir kanal oluşturmak için EndpointAddress10 kullanın.</span><span class="sxs-lookup"><span data-stu-id="e772f-340">Use the EndpointAddress10 to create a channel to obtain a sessionful object.</span></span>  
  
    4. <span data-ttu-id="e772f-341">Birden çok çağrıda aynı örnekle kaldığını göstermek için sessionobject nesnesiyle etkileşime geçin.</span><span class="sxs-lookup"><span data-stu-id="e772f-341">Interact with the sessionful object to demonstrate it remains the same instance across multiple calls.</span></span>  
  
   ```csharp
   ChannelFactory<ISessionBoundFactory> channelFactory =   
       new ChannelFactory<ISessionBoundFactory>("factory");  
   ISessionBoundFactory sessionFactory = channelFactory.CreateChannel();  
  
   EndpointAddress10 address1 = sessionFactory.GetInstanceAddress();  
   EndpointAddress10 address2 = sessionFactory.GetInstanceAddress();  
  
   ChannelFactory<ISessionBoundObject> sessionObjectFactory1 =   
       new ChannelFactory<ISessionBoundObject>(new NetTcpBinding(),   
                                               address1.ToEndpointAddress());  
   ChannelFactory<ISessionBoundObject> sessionObjectFactory2 =   
       new ChannelFactory<ISessionBoundObject>(new NetTcpBinding(),   
                                               address2.ToEndpointAddress());  
  
   ISessionBoundObject sessionInstance1 = sessionObjectFactory1.CreateChannel();  
   ISessionBoundObject sessionInstance2 = sessionObjectFactory2.CreateChannel();  
  
   sessionInstance1.SetCurrentValue("Hello");  
   sessionInstance2.SetCurrentValue("World");  
  
   if (sessionInstance1.GetCurrentValue() == "Hello" &&  
       sessionInstance2.GetCurrentValue() == "World")  
   {  
       Console.WriteLine("sessionful server object works as expected");  
   }  
   ```  
  
 <span data-ttu-id="e772f-342">WCF her zaman nesneleri değere göre döndürür, ancak EndpointAddress10 kullanımı aracılığıyla başvuru semantiğinin eşdeğerini desteklemek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="e772f-342">WCF always returns objects by value, but it is possible to support the equivalent of by-reference semantics through the use of EndpointAddress10.</span></span> <span data-ttu-id="e772f-343">Bu, istemcinin, diğer herhangi bir WCF hizmeti gibi etkileşime girebileceği bir sessionwcf hizmeti örneği istemesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="e772f-343">This permits the client to request a sessionful WCF service instance, after which it can interact with it like any other WCF service.</span></span>  
  
#### <a name="scenario-3-client-sends-server-a-by-value-instance"></a><span data-ttu-id="e772f-344">Senaryo 3: İstemci sunucuya göre bir örnek gönderir</span><span class="sxs-lookup"><span data-stu-id="e772f-344">Scenario 3: Client Sends Server a By-Value Instance</span></span>  
 <span data-ttu-id="e772f-345">Bu senaryoda, temel olmayan bir nesne örneğini sunucuya göre sunucusuna gönderen istemci gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e772f-345">This scenario demonstrates the client sending a non-primitive object instance to the server by value.</span></span> <span data-ttu-id="e772f-346">WCF yalnızca değere göre nesneler gönderdiğinden, bu senaryo normal WCF kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e772f-346">Because WCF only sends objects by value, this scenario demonstrates normal WCF usage.</span></span>  
  
1. <span data-ttu-id="e772f-347">Senaryo 1 ' de aynı WCF hizmetini kullanın.</span><span class="sxs-lookup"><span data-stu-id="e772f-347">Use the same WCF Service from Scenario 1.</span></span>  
  
2. <span data-ttu-id="e772f-348">Yeni bir değere göre nesne oluşturmak için istemcisini kullanın, ıcustomerservice hizmetiyle iletişim kurmak için bir kanal oluşturun ve nesneyi buna gönderin.</span><span class="sxs-lookup"><span data-stu-id="e772f-348">Use the client to create a new by-value object (Customer), create a channel to communicate with the ICustomerService service, and send the object to it.</span></span>  
  
   ```csharp
   ChannelFactory<ICustomerService> factory =  
       new ChannelFactory<ICustomerService>("customerservice");  
   ICustomerService service = factory.CreateChannel();  
   PremiumCustomer customer = new PremiumCustomer {   
   FirstName = "Bob",   
   LastName = "Jones",   
   CustomerId = 43,   
   AccountId = 99};  
   bool success = service.UpdateCustomer(customer);  
   Console.WriteLine($"  Server returned {success}.");
   ```  
  
     <span data-ttu-id="e772f-349">Müşteri nesnesi serileştirilir ve sunucuya gönderilir ve bu nesnenin yeni bir kopyasına seri hale gelir.</span><span class="sxs-lookup"><span data-stu-id="e772f-349">The customer object will be serialized, and sent to the server, where it is deserialized into a new copy of that object.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="e772f-350">Bu kod ayrıca, türetilmiş bir tür göndermeyi de gösterir (PremiumCustomer).</span><span class="sxs-lookup"><span data-stu-id="e772f-350">This code also illustrates sending a derived type (PremiumCustomer).</span></span> <span data-ttu-id="e772f-351">Hizmet arabirimi bir müşteri nesnesi bekliyor, ancak Customer sınıfında [KnownType] özniteliğine de PremiumCustomer de izin verildi.</span><span class="sxs-lookup"><span data-stu-id="e772f-351">The service interface expects a Customer object, but the [KnownType] attribute on the Customer class indicated PremiumCustomer was also allowed.</span></span> <span data-ttu-id="e772f-352">WCF, bu hizmet arabirimi aracılığıyla başka herhangi bir türü serileştirme veya serisini kaldırma girişiminde bulunamaz.</span><span class="sxs-lookup"><span data-stu-id="e772f-352">WCF will fail any attempt to serialize or deserialize any other type through this service interface.</span></span>  
  
 <span data-ttu-id="e772f-353">Normal WCF verileri alışverişi değere göre yapılır.</span><span class="sxs-lookup"><span data-stu-id="e772f-353">Normal WCF exchanges of data are by value.</span></span> <span data-ttu-id="e772f-354">Bu, bu veri nesnelerinden birindeki yöntemlerin çağrılması için yalnızca yerel olarak yürütülür; diğer katmanda kod çağırmaz.</span><span class="sxs-lookup"><span data-stu-id="e772f-354">This guarantees that invoking methods on one of these data objects executes only locally – it will not invoke code on the other tier.</span></span> <span data-ttu-id="e772f-355">Sunucudan döndürülen başvuru nesneleri gibi bir şeye ulaşmak mümkün olsa da, bir istemcinin sunucuya başvuruya göre bir nesne geçirmesi mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="e772f-355">While it is possible to achieve something like by-reference objects returned *from* the server, it is not possible for a client to pass a by-reference object *to* the server.</span></span> <span data-ttu-id="e772f-356">Bir çift yönlü hizmet kullanılarak, istemci ve sunucu arasında geri ve ileri bir konuşma gerektiren bir senaryo WCF 'de elde edilebilir.</span><span class="sxs-lookup"><span data-stu-id="e772f-356">A scenario that requires a conversation back and forth between client and server can be achieved in WCF using a duplex service.</span></span> <span data-ttu-id="e772f-357">Daha fazla bilgi için bkz. [çift yönlü hizmetler](./feature-details/duplex-services.md).</span><span class="sxs-lookup"><span data-stu-id="e772f-357">For more information, see [Duplex Services](./feature-details/duplex-services.md).</span></span>  
  
## <a name="summary"></a><span data-ttu-id="e772f-358">Özet</span><span class="sxs-lookup"><span data-stu-id="e772f-358">Summary</span></span>  
 <span data-ttu-id="e772f-359">.NET Remoting, yalnızca tam olarak güvenilen ortamlarda kullanılması amaçlanan bir iletişim çerçevesidir.</span><span class="sxs-lookup"><span data-stu-id="e772f-359">.NET Remoting is a communication framework intended to be used only within fully-trusted environments.</span></span> <span data-ttu-id="e772f-360">Eski bir üründür ve yalnızca geriye dönük uyumluluk için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="e772f-360">It is a legacy product and supported only for backward compatibility.</span></span> <span data-ttu-id="e772f-361">Yeni uygulamalar oluşturmak için kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="e772f-361">It should not be used to build new applications.</span></span> <span data-ttu-id="e772f-362">Buna karşılık, WCF güvenlik göz önünde bulundurularak tasarlanmıştır ve yeni ve mevcut uygulamalar için önerilir.</span><span class="sxs-lookup"><span data-stu-id="e772f-362">Conversely, WCF was designed with security in mind and is recommended for new and existing applications.</span></span> <span data-ttu-id="e772f-363">Microsoft, mevcut uzaktan Iletişim uygulamalarının WCF veya ASP.NET Web API 'SI kullanacak şekilde geçirilmesini önerir.</span><span class="sxs-lookup"><span data-stu-id="e772f-363">Microsoft recommends that existing Remoting applications be migrated to use WCF or ASP.NET Web API instead.</span></span>
