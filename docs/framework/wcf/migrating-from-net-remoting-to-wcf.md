---
title: .NET Uzaktan İletişimden WCF'ye Taşınma
ms.date: 03/30/2017
ms.assetid: 16902a42-ef80-40e9-8c4c-90e61ddfdfe5
ms.openlocfilehash: 8dcc019017195fd55231fbea3493d4c53d500cb3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183959"
---
# <a name="migrating-from-net-remoting-to-wcf"></a><span data-ttu-id="a32f3-102">.NET Uzaktan İletişimden WCF'ye Taşınma</span><span class="sxs-lookup"><span data-stu-id="a32f3-102">Migrating from .NET Remoting to WCF</span></span>
<span data-ttu-id="a32f3-103">Bu makalede, Windows Communication Foundation (WCF) kullanmak için .NET Remoting kullanan bir uygulamanın nasıl geçirilen açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a32f3-103">This article describes how to migrate an application that uses .NET Remoting to use Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="a32f3-104">Bu ürünler arasındaki benzer kavramları karşılaştırır ve wcf'de birkaç yaygın Remoting senaryosunun nasıl gerçekleştirileceğine açıklanır.</span><span class="sxs-lookup"><span data-stu-id="a32f3-104">It compares similar concepts between these products and then describes how to accomplish several common Remoting scenarios in WCF.</span></span>  
  
 <span data-ttu-id="a32f3-105">.NET Remoting, yalnızca geriye dönük uyumluluk için desteklenen eski bir üründür.</span><span class="sxs-lookup"><span data-stu-id="a32f3-105">.NET Remoting is a legacy product that is supported only for backward compatibility.</span></span> <span data-ttu-id="a32f3-106">İstemci ve sunucu arasındaki ayrı güven düzeylerini koruyamadığından karışık güven ortamları arasında güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="a32f3-106">It is not secure across mixed-trust environments because it cannot maintain the separate trust levels between client and server.</span></span> <span data-ttu-id="a32f3-107">Örneğin, .NET Remoting bitiş noktasını Hiçbir zaman Internet'e veya güvenilmeyen istemcilere maruz bırakmamalısınız.</span><span class="sxs-lookup"><span data-stu-id="a32f3-107">For example, you should never expose a .NET Remoting endpoint to the Internet or to untrusted clients.</span></span> <span data-ttu-id="a32f3-108">Mevcut Remoting uygulamalarının daha yeni ve daha güvenli teknolojilere geçirilmelerini öneririz.</span><span class="sxs-lookup"><span data-stu-id="a32f3-108">We recommend existing Remoting applications be migrated to newer and more secure technologies.</span></span> <span data-ttu-id="a32f3-109">Uygulamanın tasarımı yalnızca HTTP kullanıyorsa ve RESTful ise, Web API ASP.NET öneririz.</span><span class="sxs-lookup"><span data-stu-id="a32f3-109">If the application’s design uses only HTTP and is RESTful, we recommend ASP.NET Web API.</span></span> <span data-ttu-id="a32f3-110">Daha fazla bilgi için ASP.NET Web API'ye bakın.</span><span class="sxs-lookup"><span data-stu-id="a32f3-110">For more information, see ASP.NET Web API.</span></span> <span data-ttu-id="a32f3-111">Uygulama SOAP'a dayanıyorsa veya TCP gibi Http dışı protokoller gerektiriyorsa, WCF'yi öneririz.</span><span class="sxs-lookup"><span data-stu-id="a32f3-111">If the application is based on SOAP or requires non-Http protocols such as TCP, we recommend WCF.</span></span>  

## <a name="comparing-net-remoting-to-wcf"></a><span data-ttu-id="a32f3-112">.NET Remoting ile WCF karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="a32f3-112">Comparing .NET Remoting to WCF</span></span>  
 <span data-ttu-id="a32f3-113">Bu bölümde .NET Remoting'in temel yapı taşları WCF eşdeğerleri ile karşılaştırılır.</span><span class="sxs-lookup"><span data-stu-id="a32f3-113">This section compares the basic building blocks of .NET Remoting with their WCF equivalents.</span></span> <span data-ttu-id="a32f3-114">Bu yapı taşlarını daha sonra WCF'de bazı ortak istemci sunucu senaryoları oluşturmak için kullanacağız.</span><span class="sxs-lookup"><span data-stu-id="a32f3-114">We will use these building blocks later to create some common client-server scenarios in WCF.</span></span> <span data-ttu-id="a32f3-115">Aşağıdaki grafikte .NET Remoting ve WCF arasındaki temel benzerlikler ve farklar özetlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="a32f3-115">The following chart summarizes the main similarities and differences between .NET Remoting and WCF.</span></span>  
  
||<span data-ttu-id="a32f3-116">.NET uzaktan iletişim</span><span class="sxs-lookup"><span data-stu-id="a32f3-116">.NET Remoting</span></span>|<span data-ttu-id="a32f3-117">WCF</span><span class="sxs-lookup"><span data-stu-id="a32f3-117">WCF</span></span>|  
|-|-------------------|---------|  
|<span data-ttu-id="a32f3-118">Sunucu türü</span><span class="sxs-lookup"><span data-stu-id="a32f3-118">Server type</span></span>|<span data-ttu-id="a32f3-119">Alt sınıf MarshalByRefObject</span><span class="sxs-lookup"><span data-stu-id="a32f3-119">Subclass MarshalByRefObject</span></span>|<span data-ttu-id="a32f3-120">[ServiceContract] özniteliği ile işaretle</span><span class="sxs-lookup"><span data-stu-id="a32f3-120">Mark with [ServiceContract] attribute</span></span>|  
|<span data-ttu-id="a32f3-121">Servis işlemleri</span><span class="sxs-lookup"><span data-stu-id="a32f3-121">Service operations</span></span>|<span data-ttu-id="a32f3-122">Sunucu türünde genel yöntemler</span><span class="sxs-lookup"><span data-stu-id="a32f3-122">Public methods on server type</span></span>|<span data-ttu-id="a32f3-123">[OperationContract] özniteliği ile işaretle</span><span class="sxs-lookup"><span data-stu-id="a32f3-123">Mark with [OperationContract] attribute</span></span>|  
|<span data-ttu-id="a32f3-124">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="a32f3-124">Serialization</span></span>|<span data-ttu-id="a32f3-125">ISerializable veya [Serializable]</span><span class="sxs-lookup"><span data-stu-id="a32f3-125">ISerializable or [Serializable]</span></span>|<span data-ttu-id="a32f3-126">DataContractSerializer veya XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="a32f3-126">DataContractSerializer or XmlSerializer</span></span>|  
|<span data-ttu-id="a32f3-127">Geçen nesneler</span><span class="sxs-lookup"><span data-stu-id="a32f3-127">Objects passed</span></span>|<span data-ttu-id="a32f3-128">Değer veya referans</span><span class="sxs-lookup"><span data-stu-id="a32f3-128">By-value or by-reference</span></span>|<span data-ttu-id="a32f3-129">Yalnızca göredeğer</span><span class="sxs-lookup"><span data-stu-id="a32f3-129">By-value only</span></span>|  
|<span data-ttu-id="a32f3-130">Hatalar/özel durumlar</span><span class="sxs-lookup"><span data-stu-id="a32f3-130">Errors/exceptions</span></span>|<span data-ttu-id="a32f3-131">Herhangi bir serializable özel durum</span><span class="sxs-lookup"><span data-stu-id="a32f3-131">Any serializable exception</span></span>|<span data-ttu-id="a32f3-132">Arıza\<Sözleşme Detay></span><span class="sxs-lookup"><span data-stu-id="a32f3-132">FaultContract\<TDetail></span></span>|  
|<span data-ttu-id="a32f3-133">İstemci proxy nesneleri</span><span class="sxs-lookup"><span data-stu-id="a32f3-133">Client proxy objects</span></span>|<span data-ttu-id="a32f3-134">Güçlü bir şekilde yazılan saydam yakınlıklar MareşalByRefObjects'ten otomatik olarak oluşturulur</span><span class="sxs-lookup"><span data-stu-id="a32f3-134">Strongly typed transparent proxies are created automatically from MarshalByRefObjects</span></span>|<span data-ttu-id="a32f3-135">Güçlü dakti-sa'lar ChannelFactory\<TChannel kullanılarak isteğe bağlı olarak oluşturulur></span><span class="sxs-lookup"><span data-stu-id="a32f3-135">Strongly typed proxies are generated on-demand using ChannelFactory\<TChannel></span></span>|  
|<span data-ttu-id="a32f3-136">Platform gerekli</span><span class="sxs-lookup"><span data-stu-id="a32f3-136">Platform required</span></span>|<span data-ttu-id="a32f3-137">Hem istemci hem de sunucu Microsoft OS ve .NET kullanmalıdır</span><span class="sxs-lookup"><span data-stu-id="a32f3-137">Both client and server must use Microsoft OS and .NET</span></span>|<span data-ttu-id="a32f3-138">Platformlar arası</span><span class="sxs-lookup"><span data-stu-id="a32f3-138">Cross-platform</span></span>|  
|<span data-ttu-id="a32f3-139">İleti biçimi</span><span class="sxs-lookup"><span data-stu-id="a32f3-139">Message format</span></span>|<span data-ttu-id="a32f3-140">Özel</span><span class="sxs-lookup"><span data-stu-id="a32f3-140">Private</span></span>|<span data-ttu-id="a32f3-141">Endüstri standartları (SOAP, WS-\*, vb.)</span><span class="sxs-lookup"><span data-stu-id="a32f3-141">Industry standards (SOAP, WS-\*, etc.)</span></span>|  
  
### <a name="server-implementation-comparison"></a><span data-ttu-id="a32f3-142">Sunucu Uygulama Karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="a32f3-142">Server Implementation Comparison</span></span>  
  
#### <a name="creating-a-server-in-net-remoting"></a><span data-ttu-id="a32f3-143">.NET Remoting'de Sunucu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a32f3-143">Creating a Server in .NET Remoting</span></span>  
 <span data-ttu-id="a32f3-144">.NET Remoting sunucu türleri MarshalByRefObject'ten türemiş olmalı ve istemcinin çağırabileceği yöntemleri tanımlamalıdır:</span><span class="sxs-lookup"><span data-stu-id="a32f3-144">.NET Remoting server types must derive from MarshalByRefObject and define methods the client can call, like the following:</span></span>  
  
```csharp
public class RemotingServer : MarshalByRefObject  
{  
    public Customer GetCustomer(int customerId) { … }  
}  
```  
  
 <span data-ttu-id="a32f3-145">Bu sunucu türünün ortak yöntemleri istemcilerin kullanabileceği ortak sözleşme haline gelir.</span><span class="sxs-lookup"><span data-stu-id="a32f3-145">The public methods of this server type become the public contract available to clients.</span></span>  <span data-ttu-id="a32f3-146">Sunucunun ortak arabirimi ile uygulanması arasında ayrım yoktur – bir tür her ikisini de işler.</span><span class="sxs-lookup"><span data-stu-id="a32f3-146">There is no separation between the server’s public interface and its implementation – one type handles both.</span></span>  
  
 <span data-ttu-id="a32f3-147">Sunucu türü tanımlandıktan sonra, aşağıdaki örnekte olduğu gibi istemcilerin kullanımına sunulabilir:</span><span class="sxs-lookup"><span data-stu-id="a32f3-147">Once the server type has been defined, it can be made available to clients, like in the following example:</span></span>  
  
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
  
 <span data-ttu-id="a32f3-148">Yapılandırma dosyalarını kullanmak da dahil olmak üzere Remoting türünü sunucu olarak kullanılabilir hale getirmenin birçok yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="a32f3-148">There are many ways to make the Remoting type available as a server, including using configuration files.</span></span> <span data-ttu-id="a32f3-149">Bu sadece bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="a32f3-149">This is just one example.</span></span>  
  
#### <a name="creating-a-server-in-wcf"></a><span data-ttu-id="a32f3-150">WCF'de Sunucu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a32f3-150">Creating a Server in WCF</span></span>  
 <span data-ttu-id="a32f3-151">WCF'deki eşdeğer adım, iki tür -kamu "hizmet sözleşmesi" ve somut uygulama olmak üzere oluşturulmasını içeriyor.</span><span class="sxs-lookup"><span data-stu-id="a32f3-151">The equivalent step in WCF involves creating two types -- the public "service contract" and the concrete implementation.</span></span> <span data-ttu-id="a32f3-152">İlki [ServiceContract] ile işaretlenmiş bir arabirim olarak bildirilir.</span><span class="sxs-lookup"><span data-stu-id="a32f3-152">The first is declared as an interface marked with [ServiceContract].</span></span> <span data-ttu-id="a32f3-153">İstemciler için kullanılabilen yöntemler [OperationContract] ile işaretlenir:</span><span class="sxs-lookup"><span data-stu-id="a32f3-153">Methods available to clients are marked with [OperationContract]:</span></span>  
  
```csharp
[ServiceContract]  
public interface IWCFServer  
{  
    [OperationContract]  
    Customer GetCustomer(int customerId);  
}  
```  
  
 <span data-ttu-id="a32f3-154">Sunucunun uygulaması aşağıdaki örnekte olduğu gibi ayrı bir somut sınıfta tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="a32f3-154">The server’s implementation is defined in a separate concrete class, like in the following example:</span></span>  
  
```csharp
public class WCFServer : IWCFServer  
{  
    public Customer GetCustomer(int customerId) { … }  
}  
```  
  
 <span data-ttu-id="a32f3-155">Bu türler tanımlandıktan sonra, WCF sunucusu aşağıdaki örnekte olduğu gibi istemcilerin kullanımına sunulabilir:</span><span class="sxs-lookup"><span data-stu-id="a32f3-155">Once these types have been defined, the WCF server can be made available to clients, like in the following example:</span></span>  
  
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
> <span data-ttu-id="a32f3-156">TCP, her iki örnekte de mümkün olduğunca benzer tutmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a32f3-156">TCP is used in both examples to keep them as similar as possible.</span></span> <span data-ttu-id="a32f3-157">HTTP'yi kullanan örnekler için bu konunun ilerleyen yerlerine bakın.</span><span class="sxs-lookup"><span data-stu-id="a32f3-157">Refer to the scenario walk-throughs later in this topic for examples using HTTP.</span></span>  
  
 <span data-ttu-id="a32f3-158">WCF hizmetlerini yapılandırmanın ve barındırmanın birçok yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="a32f3-158">There are many ways to configure and to host WCF services.</span></span> <span data-ttu-id="a32f3-159">Bu sadece bir örnektir, "kendi kendine barındırılan" olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="a32f3-159">This is just one example, known as "self-hosted".</span></span> <span data-ttu-id="a32f3-160">Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:</span><span class="sxs-lookup"><span data-stu-id="a32f3-160">For more information, see the following topics:</span></span>  
  
- [<span data-ttu-id="a32f3-161">Nasıl yapılır: Bir Hizmet Anlaşması Tanımlama</span><span class="sxs-lookup"><span data-stu-id="a32f3-161">How to: Define a Service Contract</span></span>](how-to-define-a-wcf-service-contract.md)  
  
- [<span data-ttu-id="a32f3-162">Yapılandırma Dosyalarını Kullanarak Hizmetleri Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a32f3-162">Configuring Services Using Configuration Files</span></span>](configuring-services-using-configuration-files.md)  
  
- [<span data-ttu-id="a32f3-163">Barındırma Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="a32f3-163">Hosting Services</span></span>](hosting-services.md)  
  
### <a name="client-implementation-comparison"></a><span data-ttu-id="a32f3-164">İstemci Uygulama Karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="a32f3-164">Client Implementation Comparison</span></span>  
  
#### <a name="creating-a-client-in-net-remoting"></a><span data-ttu-id="a32f3-165">.NET Remoting'de İstemci Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a32f3-165">Creating a Client in .NET Remoting</span></span>  
 <span data-ttu-id="a32f3-166">Bir .NET Remoting sunucu nesnesi kullanıma sunulduktan sonra, aşağıdaki örnekte olduğu gibi istemciler tarafından tüketilebilir:</span><span class="sxs-lookup"><span data-stu-id="a32f3-166">Once a .NET Remoting server object has been made available, it can be consumed by clients, like in the following example:</span></span>  
  
```csharp
TcpChannel channel = new TcpChannel();  
ChannelServices.RegisterChannel(channel, ensureSecurity : true);  
RemotingServer server = (RemotingServer)Activator.GetObject(  
                            typeof(RemotingServer),
                            "tcp://localhost:8080/RemotingServer");  
  
RemotingCustomer customer = server.GetCustomer(42);  
Console.WriteLine($"Customer {customer.FirstName} {customer.LastName} received.");
```  
  
 <span data-ttu-id="a32f3-167">Activator.GetObject() döndürülen RemotingServer örneği "saydam proxy" olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="a32f3-167">The RemotingServer instance returned from Activator.GetObject() is known as a "transparent proxy."</span></span> <span data-ttu-id="a32f3-168">İstemcide RemotingServer türü için genel API uygular, ancak tüm yöntemler farklı bir işlem veya makinede çalışan sunucu nesnesini çağırır.</span><span class="sxs-lookup"><span data-stu-id="a32f3-168">It implements the public API for the RemotingServer type on the client, but all the methods call the server object running in a different process or machine.</span></span>  
  
#### <a name="creating-a-client-in-wcf"></a><span data-ttu-id="a32f3-169">WCF'de İstemci Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a32f3-169">Creating a Client in WCF</span></span>  
 <span data-ttu-id="a32f3-170">WCF eşdeğer adım açıkça proxy oluşturmak için bir kanal fabrikası kullanarak içerir.</span><span class="sxs-lookup"><span data-stu-id="a32f3-170">The equivalent step in WCF involves using a channel factory to create the proxy explicitly.</span></span> <span data-ttu-id="a32f3-171">Remoting gibi proxy nesnesi de aşağıdaki örnekte olduğu gibi sunucudaki işlemleri çağırmak için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="a32f3-171">Like Remoting, the proxy object can be used to invoke operations on the server, like in the following example:</span></span>  
  
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
  
 <span data-ttu-id="a32f3-172">Bu örnek, Remoting örneğine en çok benzediği için programlamayı kanal düzeyinde gösterir.</span><span class="sxs-lookup"><span data-stu-id="a32f3-172">This example shows programming at the channel level because it is most similar to the Remoting example.</span></span> <span data-ttu-id="a32f3-173">Ayrıca, Visual Studio'da istemci programlamayı basitleştirmek için kod üreten **Hizmet Başvurusu Ekle** yaklaşımı da mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="a32f3-173">Also available is the **Add Service Reference** approach in Visual Studio that generates code to simplify client programming.</span></span> <span data-ttu-id="a32f3-174">Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:</span><span class="sxs-lookup"><span data-stu-id="a32f3-174">For more information, see the following topics:</span></span>  
  
- [<span data-ttu-id="a32f3-175">İstemci Kanal Düzeyi Programlama</span><span class="sxs-lookup"><span data-stu-id="a32f3-175">Client Channel-Level Programming</span></span>](./extending/client-channel-level-programming.md)  
  
- [<span data-ttu-id="a32f3-176">Nasıl yapilir: Hizmet Başvurusu Ekleme, Güncelleştirme veya Kaldırma</span><span class="sxs-lookup"><span data-stu-id="a32f3-176">How to: Add, Update, or Remove a Service Reference</span></span>](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference)  
  
### <a name="serialization-usage"></a><span data-ttu-id="a32f3-177">Serileştirme Kullanımı</span><span class="sxs-lookup"><span data-stu-id="a32f3-177">Serialization Usage</span></span>  
 <span data-ttu-id="a32f3-178">Hem .NET Remoting hem de WCF, istemci ve sunucu arasında nesneleri göndermek için serileştirme kullanır, ancak bunlar şu önemli şekillerde farklılık gösterir:</span><span class="sxs-lookup"><span data-stu-id="a32f3-178">Both .NET Remoting and WCF use serialization to send objects between client and server, but they differ in these important ways:</span></span>  
  
1. <span data-ttu-id="a32f3-179">Neyi seri hale getirmek için farklı serializers ve kurallar kullanırlar.</span><span class="sxs-lookup"><span data-stu-id="a32f3-179">They use different serializers and conventions to indicate what to serialize.</span></span>  
  
2. <span data-ttu-id="a32f3-180">.NET Remoting, bir katmanda yöntem veya özellik erişiminin diğer katmanda, güvenlik sınırlarının ötesinde olan kodu yürütmesine olanak tanıyan "referans" serileştirmeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="a32f3-180">.NET Remoting supports "by reference" serialization that allows method or property access on one tier to execute code on the other tier, which is across security boundaries.</span></span> <span data-ttu-id="a32f3-181">Bu özellik güvenlik açıklarını ortaya çıkarır ve Remoting uç noktalarının asla güvenilmeyen istemcilere maruz kalmaması için temel nedenlerden biridir.</span><span class="sxs-lookup"><span data-stu-id="a32f3-181">This capability exposes security vulnerabilities and is one of the main reasons why Remoting endpoints should never be exposed to untrusted clients.</span></span>  
  
3. <span data-ttu-id="a32f3-182">Remoting tarafından kullanılan serileştirme devre dışı bırakma (serileştirmeme ne hariç) ve WCF serileştirme opt-in (açıkça hangi üyeleri serileştirmek için işaret) olduğunu.</span><span class="sxs-lookup"><span data-stu-id="a32f3-182">Serialization used by Remoting is opt-out (explicitly exclude what not to serialize) and WCF serialization is opt-in (explicitly mark which members to serialize).</span></span>  
  
#### <a name="serialization-in-net-remoting"></a><span data-ttu-id="a32f3-183">.NET Remoting'de serileştirme</span><span class="sxs-lookup"><span data-stu-id="a32f3-183">Serialization in .NET Remoting</span></span>  
 <span data-ttu-id="a32f3-184">.NET Remoting, istemci ve sunucu arasındaki nesneleri serihale ve deserialize etmenin iki yolunu destekler:</span><span class="sxs-lookup"><span data-stu-id="a32f3-184">.NET Remoting supports two ways to serialize and deserialize objects between the client and server:</span></span>  
  
- <span data-ttu-id="a32f3-185">*Değer* olarak – nesnenin değerleri katman sınırları arasında seri hale getirilir ve bu nesnenin yeni bir örneği diğer katmanda oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a32f3-185">*By value* – the values of the object are serialized across tier boundaries, and a new instance of that object is created on the other tier.</span></span> <span data-ttu-id="a32f3-186">Bu yeni örneğin yöntemlerine veya özelliklerine yapılan tüm çağrılar yalnızca yerel olarak yürütülür ve özgün nesneyi veya katmanı etkilemez.</span><span class="sxs-lookup"><span data-stu-id="a32f3-186">Any calls to methods or properties of that new instance execute only locally and do not affect the original object or tier.</span></span>  
  
- <span data-ttu-id="a32f3-187">*Referans olarak* – özel bir "nesne başvurusu" katman sınırları arasında seri hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="a32f3-187">*By reference* – a special "object reference" is serialized across tier boundaries.</span></span> <span data-ttu-id="a32f3-188">Bir katman, o nesnenin yöntemleri veya özellikleriyle etkileşime girdiğinde, özgün katmandaki özgün nesneye geri iletir.</span><span class="sxs-lookup"><span data-stu-id="a32f3-188">When one tier interacts with methods or properties of that object, it communicates back to the original object on the original tier.</span></span> <span data-ttu-id="a32f3-189">Başvuru nesneleri her iki yönde de akabilir – sunucudan istemciye veya istemciden sunucuya.</span><span class="sxs-lookup"><span data-stu-id="a32f3-189">By-reference objects can flow in either direction – server to client, or client to server.</span></span>  
  
 <span data-ttu-id="a32f3-190">Remoting'deki yan değer türleri aşağıdaki örnekte olduğu gibi [Serializable] özniteliği ile işaretlenir veya ISerializable'ı uygular:</span><span class="sxs-lookup"><span data-stu-id="a32f3-190">By-value types in Remoting are marked with the [Serializable] attribute or implement ISerializable, like in the following example:</span></span>  
  
```csharp
[Serializable]  
public class RemotingCustomer  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
    public int CustomerId { get; set; }  
}  
```  
  
 <span data-ttu-id="a32f3-191">Başvuru türleri aşağıdaki örnekte olduğu gibi MarshalByRefObject sınıfından türetilmiştir:</span><span class="sxs-lookup"><span data-stu-id="a32f3-191">By-reference types derive from the MarshalByRefObject class, like in the following example:</span></span>  
  
```csharp
public class RemotingCustomerReference : MarshalByRefObject  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
    public int CustomerId { get; set; }  
}  
```  
  
 <span data-ttu-id="a32f3-192">Remoting'in referans nesnelerinin sonuçlarını anlamak son derece önemlidir.</span><span class="sxs-lookup"><span data-stu-id="a32f3-192">It is extremely important to understand the implications of Remoting’s by-reference objects.</span></span> <span data-ttu-id="a32f3-193">Katmandan biri (istemci veya sunucu) diğer katmana bir by-reference nesnesi gönderirse, tüm yöntem çağrıları nesneye sahip olan katmanda yürütülür.</span><span class="sxs-lookup"><span data-stu-id="a32f3-193">If either tier (client or server) sends a by-reference object to the other tier, all method calls execute back on the tier owning the object.</span></span> <span data-ttu-id="a32f3-194">Örneğin, sunucu tarafından döndürülen bir başvuru nesnesi üzerinde arama yöntemleri çağıran bir istemci sunucuda kod yürütecektir.</span><span class="sxs-lookup"><span data-stu-id="a32f3-194">For example, a client calling methods on a by-reference object returned by the server will execute code on the server.</span></span> <span data-ttu-id="a32f3-195">Benzer şekilde, istemci tarafından sağlanan bir başvuru nesnesi üzerinde arama yöntemleri bir sunucu istemci üzerinde kodu geri yürütecektir.</span><span class="sxs-lookup"><span data-stu-id="a32f3-195">Similarly, a server calling methods on a by-reference object provided by the client will execute code back on the client.</span></span> <span data-ttu-id="a32f3-196">Bu nedenle, .NET Remoting'in kullanımı yalnızca tam güvenilen ortamlarda önerilir.</span><span class="sxs-lookup"><span data-stu-id="a32f3-196">For this reason, the use of .NET Remoting is recommended only within fully-trusted environments.</span></span> <span data-ttu-id="a32f3-197">Bir public .NET Remoting bitiş noktasını güvenilmeyen istemcilere vermek, Remoting sunucusunun saldırıya açık olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="a32f3-197">Exposing a public .NET Remoting endpoint to untrusted clients will make a Remoting server vulnerable to attack.</span></span>  
  
#### <a name="serialization-in-wcf"></a><span data-ttu-id="a32f3-198">WCF'de serileştirme</span><span class="sxs-lookup"><span data-stu-id="a32f3-198">Serialization in WCF</span></span>  
 <span data-ttu-id="a32f3-199">WCF yalnızca yan değer serileştirmeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="a32f3-199">WCF supports only by-value serialization.</span></span> <span data-ttu-id="a32f3-200">İstemci ve sunucu arasında alışverişyapmak için bir tür tanımlamak için en yaygın yolu aşağıdaki örnekte olduğu gibi:</span><span class="sxs-lookup"><span data-stu-id="a32f3-200">The most common way to define a type to exchange between client and server is like in the following example:</span></span>  
  
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
  
 <span data-ttu-id="a32f3-201">[DataContract] özniteliği, bu türü istemci ve sunucu arasında serileştirilebilen ve deserialize edilebilen bir tür olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a32f3-201">The [DataContract] attribute identifies this type as one that can be serialized and deserialized between client and server.</span></span> <span data-ttu-id="a32f3-202">[DataMember] özniteliği, seri hale getirmek için tek tek özellikleri veya alanları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a32f3-202">The [DataMember] attribute identifies the individual properties or fields to serialize.</span></span>  
  
 <span data-ttu-id="a32f3-203">WCF bir nesneyi katmanlar arasında gönderdiğinde, yalnızca değerleri seri hale eder ve diğer katmandaki nesnenin yeni bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a32f3-203">When WCF sends an object across tiers, it serializes only the values and creates a new instance of the object on the other tier.</span></span> <span data-ttu-id="a32f3-204">Nesnenin değerleri ile herhangi bir etkileşim yalnızca yerel olarak oluşur - onlar diğer katman ile iletişim yok .NET Remoting by-reference nesneleri yapmak.</span><span class="sxs-lookup"><span data-stu-id="a32f3-204">Any interactions with the values of the object occur only locally – they do not communicate with the other tier the way .NET Remoting by-reference objects do.</span></span> <span data-ttu-id="a32f3-205">Daha fazla bilgi için [serileştirme ve deserialization'a](./feature-details/serialization-and-deserialization.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="a32f3-205">For more information, see [Serialization and Deserialization](./feature-details/serialization-and-deserialization.md).</span></span>  
  
### <a name="exception-handling-capabilities"></a><span data-ttu-id="a32f3-206">Özel Durum İşleme Yetenekleri</span><span class="sxs-lookup"><span data-stu-id="a32f3-206">Exception Handling Capabilities</span></span>  
  
#### <a name="exceptions-in-net-remoting"></a><span data-ttu-id="a32f3-207">.NET Remoting'deki özel durumlar</span><span class="sxs-lookup"><span data-stu-id="a32f3-207">Exceptions in .NET Remoting</span></span>  
 <span data-ttu-id="a32f3-208">Remoting sunucusu tarafından atılan özel durumlar seri hale getirilir, istemciye gönderilir ve diğer özel durumlar gibi istemciye yerel olarak atılır.</span><span class="sxs-lookup"><span data-stu-id="a32f3-208">Exceptions thrown by a Remoting server are serialized, sent to the client, and thrown locally on the client like any other exception.</span></span> <span data-ttu-id="a32f3-209">Özel özel durumlar, Özel Durum türünü alt sınıflayarak ve [Serializable] ile işaretleyerek oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="a32f3-209">Custom exceptions can be created by sub-classing the Exception type and marking it with [Serializable].</span></span>   <span data-ttu-id="a32f3-210">Çoğu çerçeve özel durumu zaten bu şekilde işaretlenir ve çoğu sunucu tarafından atılmasına, seri hale getirilmesine ve istemciye yeniden atılmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="a32f3-210">Most framework exceptions are already marked in this way, allowing most to be thrown by the server, serialized, and re-thrown on the client.</span></span> <span data-ttu-id="a32f3-211">Bu tasarım geliştirme sırasında kullanışlı olsa da, sunucu tarafındaki bilgiler istemeden istemciye açıklanabilir.</span><span class="sxs-lookup"><span data-stu-id="a32f3-211">Though this design is convenient during development, server-side information can inadvertently be disclosed to the client.</span></span> <span data-ttu-id="a32f3-212">Bu, Remoting'in yalnızca tam güvenilen ortamlarda kullanılmasının birçok nedenidir.</span><span class="sxs-lookup"><span data-stu-id="a32f3-212">This is one of many reasons Remoting should be used only in fully-trusted environments.</span></span>  
  
#### <a name="exceptions-and-faults-in-wcf"></a><span data-ttu-id="a32f3-213">WCF'deki Özel Durumlar ve Hatalar</span><span class="sxs-lookup"><span data-stu-id="a32f3-213">Exceptions and Faults in WCF</span></span>  
 <span data-ttu-id="a32f3-214">WCF, yanlışlıkla bilgi ifşasına yol açabileceğinden, rasgele özel durum türlerinin sunucudan istemciye döndürülmesine izin vermez.</span><span class="sxs-lookup"><span data-stu-id="a32f3-214">WCF does not allow arbitrary exception types to be returned from the server to the client because it could lead to inadvertent information disclosure.</span></span> <span data-ttu-id="a32f3-215">Bir hizmet işlemi beklenmeyen bir özel durum atarsa, genel amaçlı bir hata özel durum istemcisi üzerine atılmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="a32f3-215">If a service operation throws an unexpected exception, it causes a general purpose FaultException to be thrown on the client.</span></span> <span data-ttu-id="a32f3-216">Bu özel durum, sorunun neden veya nerede oluştuğu hakkında herhangi bir bilgi taşımaz ve bazı uygulamalar için bu yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="a32f3-216">This exception does not carry any information why or where the problem occurred, and for some applications this is sufficient.</span></span> <span data-ttu-id="a32f3-217">İstemciye daha zengin hata bilgilerini iletmesi gereken uygulamalar, hata sözleşmesi tanımlayarak bunu yapar.</span><span class="sxs-lookup"><span data-stu-id="a32f3-217">Applications that need to communicate richer error information to the client do this by defining a fault contract.</span></span>  
  
 <span data-ttu-id="a32f3-218">Bunu yapmak için, önce hata bilgilerini taşımak için bir [DataContract] türü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a32f3-218">To do this, first create a [DataContract] type to carry the fault information.</span></span>  
  
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
  
 <span data-ttu-id="a32f3-219">Her hizmet işlemi için kullanılacak hata sözleşmesini belirtin.</span><span class="sxs-lookup"><span data-stu-id="a32f3-219">Specify the fault contract to use for each service operation.</span></span>  
  
```csharp
[ServiceContract]  
public interface IWCFServer  
{  
    [OperationContract]  
    [FaultContract(typeof(CustomerServiceFault))]  
    Customer GetCustomer(int customerId);  
}  
```  
  
 <span data-ttu-id="a32f3-220">Sunucu, hata özel durumlarını bir Hata Özel Durum atarak bildirir.</span><span class="sxs-lookup"><span data-stu-id="a32f3-220">The server reports error conditions by throwing a FaultException.</span></span>  
  
```csharp
throw new FaultException<CustomerServiceFault>(  
    new CustomerServiceFault() {
        CustomerId = customerId,
        ErrorMessage = "Illegal customer Id"
    });  
```  
  
 <span data-ttu-id="a32f3-221">İstemci sunucuya bir istekte bulunsa, hataları normal özel durumlar olarak yakalayabilir.</span><span class="sxs-lookup"><span data-stu-id="a32f3-221">And whenever the client makes a request to the server, it can catch faults as normal exceptions.</span></span>  
  
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
  
 <span data-ttu-id="a32f3-222">Hata sözleşmeleri hakkında daha <xref:System.ServiceModel.FaultException>fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="a32f3-222">For more information about fault contracts, see <xref:System.ServiceModel.FaultException>.</span></span>  
  
### <a name="security-considerations"></a><span data-ttu-id="a32f3-223">Güvenlikle İlgili Dikkat Edilmesi Gerekenler</span><span class="sxs-lookup"><span data-stu-id="a32f3-223">Security Considerations</span></span>  
  
#### <a name="security-in-net-remoting"></a><span data-ttu-id="a32f3-224">.NET Remoting'de güvenlik</span><span class="sxs-lookup"><span data-stu-id="a32f3-224">Security in .NET Remoting</span></span>  
 <span data-ttu-id="a32f3-225">Bazı .NET Remoting kanalları, kanal katmanındaki kimlik doğrulama ve şifreleme (IPC ve TCP) gibi güvenlik özelliklerini destekler.</span><span class="sxs-lookup"><span data-stu-id="a32f3-225">Some .NET Remoting channels support security features such as authentication and encryption at the channel layer (IPC and TCP).</span></span> <span data-ttu-id="a32f3-226">HTTP kanalı, hem kimlik doğrulaması hem de şifreleme için Internet Information Services'a (IIS) dayanır.</span><span class="sxs-lookup"><span data-stu-id="a32f3-226">The HTTP channel relies on Internet Information Services (IIS) for both authentication and encryption.</span></span> <span data-ttu-id="a32f3-227">Bu desteğe rağmen, .NET Güvenli olmayan bir iletişim protokolünü yeniden ifade etmeyi ve yalnızca tam güvenilen ortamlarda kullanmayı düşünmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="a32f3-227">Despite this support, you should consider .NET Remoting an unsecure communication protocol and use it only within fully-trusted environments.</span></span> <span data-ttu-id="a32f3-228">Genel Remoting bitiş noktasını asla Internet'e veya güvenilmeyen istemcilere ifşa etmeyin.</span><span class="sxs-lookup"><span data-stu-id="a32f3-228">Never expose a public Remoting endpoint to the Internet or untrusted clients.</span></span>  
  
#### <a name="security-in-wcf"></a><span data-ttu-id="a32f3-229">WCF'de Güvenlik</span><span class="sxs-lookup"><span data-stu-id="a32f3-229">Security in WCF</span></span>  
 <span data-ttu-id="a32f3-230">WCF, kısmen .NET Remoting'de bulunan güvenlik açıklarını gidermek için güvenlik göz önünde bulundurularak tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="a32f3-230">WCF was designed with security in mind, in part to address the kinds of vulnerabilities found in .NET Remoting.</span></span> <span data-ttu-id="a32f3-231">WCF hem aktarım hem de ileti düzeyinde güvenlik sunar ve kimlik doğrulama, yetkilendirme, şifreleme ve benzeri birçok seçenek sunar.</span><span class="sxs-lookup"><span data-stu-id="a32f3-231">WCF offers security at both the transport and message level, and offers many options for authentication, authorization, encryption, and so on.</span></span> <span data-ttu-id="a32f3-232">Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:</span><span class="sxs-lookup"><span data-stu-id="a32f3-232">For more information, see the following topics:</span></span>  
  
- [<span data-ttu-id="a32f3-233">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="a32f3-233">Security</span></span>](./feature-details/security.md)  
  
- [<span data-ttu-id="a32f3-234">WCF Güvenlik Rehberi</span><span class="sxs-lookup"><span data-stu-id="a32f3-234">WCF Security Guidance</span></span>](./feature-details/security-guidance-and-best-practices.md)  
  
## <a name="migrating-to-wcf"></a><span data-ttu-id="a32f3-235">WCF'ye geçiş</span><span class="sxs-lookup"><span data-stu-id="a32f3-235">Migrating to WCF</span></span>  
  
### <a name="why-migrate-from-remoting-to-wcf"></a><span data-ttu-id="a32f3-236">Neden Remoting'den WCF'ye geçiş?</span><span class="sxs-lookup"><span data-stu-id="a32f3-236">Why Migrate from Remoting to WCF?</span></span>  
  
- <span data-ttu-id="a32f3-237">**.NET Remoting eski bir üründür.**</span><span class="sxs-lookup"><span data-stu-id="a32f3-237">**.NET Remoting is a legacy product.**</span></span> <span data-ttu-id="a32f3-238">[.NET Remoting'de](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507%28v=vs.100%29)açıklandığı gibi, eski bir ürün olarak kabul edilir ve yeni geliştirme için önerilmez.</span><span class="sxs-lookup"><span data-stu-id="a32f3-238">As described in [.NET Remoting](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507%28v=vs.100%29), it is considered a legacy product and is not recommended for new development.</span></span> <span data-ttu-id="a32f3-239">WCF veya ASP.NET Web API'si yeni ve varolan uygulamalar için önerilir.</span><span class="sxs-lookup"><span data-stu-id="a32f3-239">WCF or ASP.NET Web API are recommended for new and existing applications.</span></span>  
  
- <span data-ttu-id="a32f3-240">**WCF çapraz platform standartları kullanır.**</span><span class="sxs-lookup"><span data-stu-id="a32f3-240">**WCF uses cross-platform standards.**</span></span> <span data-ttu-id="a32f3-241">WCF, platformlar arası birlikte çalışabilirlik göz önünde bulundurularak tasarlanmıştır ve birçok endüstri standardına (SOAP, WS-Security, WS-Trust, vb.) destek vermektedir.</span><span class="sxs-lookup"><span data-stu-id="a32f3-241">WCF was designed with cross-platform interoperability in mind and supports many industry standards (SOAP, WS-Security, WS-Trust, etc.).</span></span> <span data-ttu-id="a32f3-242">Bir WCF hizmeti, Windows dışındaki işletim sistemlerinde çalışan istemcilerle birlikte çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="a32f3-242">A WCF service can interoperate with clients running on operating systems other than Windows.</span></span> <span data-ttu-id="a32f3-243">Remoting, öncelikle windows işletim sisteminde .NET Framework kullanılarak hem sunucu hem de istemci uygulamalarının çalıştığı ortamlar için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="a32f3-243">Remoting was designed primarily for environments where both the server and client applications run using .NET Framework on a Windows operating system.</span></span>
  
- <span data-ttu-id="a32f3-244">**WCF yerleşik güvenlik vardır.**</span><span class="sxs-lookup"><span data-stu-id="a32f3-244">**WCF has built-in security.**</span></span> <span data-ttu-id="a32f3-245">WCF güvenlik göz önünde bulundurularak tasarlanmıştır ve kimlik doğrulama, aktarım düzeyi güvenliği, ileti düzeyi güvenliği, vb. için birçok seçenek sunar. Remoting, uygulamaların birlikte çalışmasını kolaylaştırmak için tasarlanmıştır, ancak güvenilmeyen ortamlarda güvenli olacak şekilde tasarlanmamaktadır.</span><span class="sxs-lookup"><span data-stu-id="a32f3-245">WCF was designed with security in mind and offers many options for authentication, transport level security, message level security, etc. Remoting was designed to make it easy for applications to interoperate but was not designed to be secure in non-trusted environments.</span></span> <span data-ttu-id="a32f3-246">WCF hem güvenilir hem de güvenilmeyen ortamlarda çalışacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="a32f3-246">WCF was designed to work in both trusted and non-trusted environments.</span></span>  
  
### <a name="migration-recommendations"></a><span data-ttu-id="a32f3-247">Geçiş Önerileri</span><span class="sxs-lookup"><span data-stu-id="a32f3-247">Migration Recommendations</span></span>  
 <span data-ttu-id="a32f3-248">.NET Remoting'den WCF'ye geçiş için önerilen adımlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="a32f3-248">The following are the recommended steps to migrate from .NET Remoting to WCF:</span></span>  
  
- <span data-ttu-id="a32f3-249">**Hizmet sözleşmesini oluşturun.**</span><span class="sxs-lookup"><span data-stu-id="a32f3-249">**Create the service contract.**</span></span> <span data-ttu-id="a32f3-250">Hizmet arabirimi türlerinizi tanımlayın ve [ServiceContract] özniteliğiyle işaretleyin. Müşterilerin [OperationContract] ile aramalarına izin verilecek tüm yöntemleri işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="a32f3-250">Define your service interface types, and mark them with the [ServiceContract] attribute.Mark all the methods the clients will be allowed to call with [OperationContract].</span></span>  
  
- <span data-ttu-id="a32f3-251">**Veri sözleşmesini oluşturun.**</span><span class="sxs-lookup"><span data-stu-id="a32f3-251">**Create the data contract.**</span></span> <span data-ttu-id="a32f3-252">Sunucu ve istemci arasında değiş tokuş edilecek veri türlerini tanımlayın ve bunları [DataContract] özniteliğiyle işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="a32f3-252">Define the data types that will be exchanged between server and client, and mark them with the [DataContract] attribute.</span></span> <span data-ttu-id="a32f3-253">İstemcinin kullanmasına izin verilecek tüm alanları ve özellikleri [DataMember] ile işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="a32f3-253">Mark all the fields and properties the client will be allowed to use with [DataMember].</span></span>  
  
- <span data-ttu-id="a32f3-254">**Hata sözleşmesini oluşturun (isteğe bağlı).**</span><span class="sxs-lookup"><span data-stu-id="a32f3-254">**Create the fault contract (optional).**</span></span> <span data-ttu-id="a32f3-255">Hatalarla karşılaşıldığında sunucu ve istemci arasında değiş tokuş edilecek türleri oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a32f3-255">Create the types that will be exchanged between server and client when errors are encountered.</span></span> <span data-ttu-id="a32f3-256">Serileştirilebilir hale getirmek için bu türleri [DataContract] ve [DataMember] ile işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="a32f3-256">Mark these types with [DataContract] and [DataMember] to make them serializable.</span></span> <span data-ttu-id="a32f3-257">[OperationContract] ile işaretlediğiniz tüm hizmet işlemleri için, hangi hataları geri getirebileceklerini belirtmek için bunları [Hata Sözleşmesi] ile işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="a32f3-257">For all service operations you marked with [OperationContract], also mark them with [FaultContract] to indicate which errors they may return.</span></span>  
  
- <span data-ttu-id="a32f3-258">**Hizmeti yapılandırın ve barındırın.**</span><span class="sxs-lookup"><span data-stu-id="a32f3-258">**Configure and host the service.**</span></span> <span data-ttu-id="a32f3-259">Hizmet sözleşmesi oluşturulduktan sonra, bir sonraki adım, hizmeti bir bitiş noktasında ortaya çıkarmak için bir bağlama yapılandırmaktır.</span><span class="sxs-lookup"><span data-stu-id="a32f3-259">Once the service contract has been created, the next step is to configure a binding to expose the service at an endpoint.</span></span> <span data-ttu-id="a32f3-260">Daha fazla bilgi için [Bkz. Uç Noktalar: Adresler, Ciltler ve Sözleşmeler.](./feature-details/endpoints-addresses-bindings-and-contracts.md)</span><span class="sxs-lookup"><span data-stu-id="a32f3-260">For more information, see [Endpoints: Addresses, Bindings, and Contracts](./feature-details/endpoints-addresses-bindings-and-contracts.md).</span></span>  
  
 <span data-ttu-id="a32f3-261">Bir Remoting uygulaması WCF'ye geçirildikten sonra ,.NET Remoting'e olan bağımlılıkları kaldırmak yine de önemlidir.</span><span class="sxs-lookup"><span data-stu-id="a32f3-261">Once a Remoting application has been migrated to WCF, it is still important to remove dependencies on .NET Remoting.</span></span> <span data-ttu-id="a32f3-262">Bu, Remoting güvenlik açıklarının uygulamadan kaldırılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="a32f3-262">This ensures that any Remoting vulnerabilities are removed from the application.</span></span> <span data-ttu-id="a32f3-263">Bu adımlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="a32f3-263">These steps include the following:</span></span>  
  
- <span data-ttu-id="a32f3-264">**MarshalByRefObject kullanımını durdurun.**</span><span class="sxs-lookup"><span data-stu-id="a32f3-264">**Discontinue use of MarshalByRefObject.**</span></span> <span data-ttu-id="a32f3-265">MarshalByRefObject türü yalnızca Remoting için vardır ve WCF tarafından kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="a32f3-265">The MarshalByRefObject type exists only for Remoting and is not used by WCF.</span></span> <span data-ttu-id="a32f3-266">Alt sınıf MarshalByRefObject kaldırılmalıdır veya değiştirilmelidir herhangi bir uygulama türleri.</span><span class="sxs-lookup"><span data-stu-id="a32f3-266">Any application types that sub-class MarshalByRefObject should be removed or changed.</span></span>  
  
- <span data-ttu-id="a32f3-267">**[Serializable] ve ISerializable kullanımını durdurun.**</span><span class="sxs-lookup"><span data-stu-id="a32f3-267">**Discontinue use of [Serializable] and ISerializable.**</span></span> <span data-ttu-id="a32f3-268">[Serializable] öznitelik ve ISerializable arabirimi başlangıçta güvenilen ortamlarda türleri serileştirmek için tasarlanmıştır ve Remoting tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a32f3-268">The [Serializable] attribute and ISerializable interface were originally designed to serialize types within trusted environments, and they are used by Remoting.</span></span> <span data-ttu-id="a32f3-269">WCF serileştirmesi, [DataContract] ve [DataMember] ile işaretlenmiş türlere dayanır.</span><span class="sxs-lookup"><span data-stu-id="a32f3-269">WCF serialization relies on types being marked with [DataContract] and [DataMember].</span></span> <span data-ttu-id="a32f3-270">Bir uygulama tarafından kullanılan veri türleri [DataContract] kullanmak ve ISerializable veya [Serializable] kullanmak için değiştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="a32f3-270">Data types used by an application should be modified to use [DataContract] and not to use ISerializable or [Serializable].</span></span>  
  
### <a name="migration-scenarios"></a><span data-ttu-id="a32f3-271">Geçiş Senaryoları</span><span class="sxs-lookup"><span data-stu-id="a32f3-271">Migration Scenarios</span></span>  
 <span data-ttu-id="a32f3-272">Şimdi WCF'de aşağıdaki ortak Remoting senaryolarının nasıl gerçekleştirileceğine bakalım:</span><span class="sxs-lookup"><span data-stu-id="a32f3-272">Now let’s see how to accomplish the following common Remoting scenarios in WCF:</span></span>  
  
1. <span data-ttu-id="a32f3-273">Sunucu istemciye bir nesne yan değer döndürür</span><span class="sxs-lookup"><span data-stu-id="a32f3-273">Server returns an object by-value to the client</span></span>  
  
2. <span data-ttu-id="a32f3-274">Sunucu istemciye bir nesne by-reference döndürür</span><span class="sxs-lookup"><span data-stu-id="a32f3-274">Server returns an object by-reference to the client</span></span>  
  
3. <span data-ttu-id="a32f3-275">İstemci sunucuya bir nesneyi göre değer gönderir</span><span class="sxs-lookup"><span data-stu-id="a32f3-275">Client sends an object by-value to the server</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a32f3-276">WCF'de istemciden sunucuya nesne gönderme izni verilmez.</span><span class="sxs-lookup"><span data-stu-id="a32f3-276">Sending an object by-reference from the client to the server is not allowed in WCF.</span></span>  
  
 <span data-ttu-id="a32f3-277">Bu senaryoları okurken,.NET Remoting için temel arabirimlerimizin aşağıdaki örnek gibi göründüğünü varsayalım.</span><span class="sxs-lookup"><span data-stu-id="a32f3-277">When reading through these scenarios, assume our baseline interfaces for .NET Remoting look like the following example.</span></span> <span data-ttu-id="a32f3-278">.NET Remoting uygulaması burada önemli değildir, çünkü yalnızca eşdeğer işlevselliği uygulamak için WCF'nin nasıl kullanılacağını göstermek istiyoruz.</span><span class="sxs-lookup"><span data-stu-id="a32f3-278">The .NET Remoting implementation is not important here because we want to illustrate only how to use WCF to implement equivalent functionality.</span></span>  
  
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
  
#### <a name="scenario-1-service-returns-an-object-by-value"></a><span data-ttu-id="a32f3-279">Senaryo 1: Hizmet Nesneyi Değere Göre Döndürür</span><span class="sxs-lookup"><span data-stu-id="a32f3-279">Scenario 1: Service Returns an Object by Value</span></span>  
 <span data-ttu-id="a32f3-280">Bu senaryo, bir nesneyi istemciye değer olarak döndüren bir sunucuyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="a32f3-280">This scenario demonstrates a server returning an object to the client by value.</span></span> <span data-ttu-id="a32f3-281">WCF nesneleri her zaman sunucudan değer olarak döndürür, bu nedenle aşağıdaki adımlar normal bir WCF hizmetinin nasıl oluşturulabildiğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="a32f3-281">WCF always returns objects from the server by value, so the following steps simply describe how to build a normal WCF service.</span></span>  
  
1. <span data-ttu-id="a32f3-282">WCF hizmeti için ortak arabirim tanımlayarak başlayın ve [ServiceContract] özniteliği ile işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="a32f3-282">Start by defining a public interface for the WCF service and mark it with the [ServiceContract] attribute.</span></span> <span data-ttu-id="a32f3-283">İstemcimizin çağıracağı sunucu tarafındaki yöntemleri tanımlamak için [OperationContract] kullanırız.</span><span class="sxs-lookup"><span data-stu-id="a32f3-283">We use [OperationContract] to identify the server-side methods our client will call.</span></span>  
  
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
  
2. <span data-ttu-id="a32f3-284">Bir sonraki adım, bu hizmet için veri sözleşmesi oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="a32f3-284">The next step is to create the data contract for this service.</span></span> <span data-ttu-id="a32f3-285">Bunu, [DataContract] özniteliği ile işaretlenmiş sınıflar (arabirimler değil) oluşturarak yapıyoruz.</span><span class="sxs-lookup"><span data-stu-id="a32f3-285">We do this by creating classes (not interfaces) marked with the [DataContract] attribute.</span></span> <span data-ttu-id="a32f3-286">Hem istemci hem de sunucu tarafından görülebilmesini istediğimiz tek tek özellikler veya alanlar [DataMember] ile işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="a32f3-286">The individual properties or fields we want visible to both client and server are marked with [DataMember].</span></span> <span data-ttu-id="a32f3-287">Türemiş türlerine izin verilmesini istiyorsak, bunları tanımlamak için [KnownType] özniteliğini kullanmalıyız.</span><span class="sxs-lookup"><span data-stu-id="a32f3-287">If we want derived types to be allowed, we must use the [KnownType] attribute to identify them.</span></span> <span data-ttu-id="a32f3-288">WCF'nin bu hizmet için seri hale getirilmesine veya seri hale getirilmesine izin verecek tek türleri, hizmet arabirimindeki ler ve bu "bilinen türler"dir.</span><span class="sxs-lookup"><span data-stu-id="a32f3-288">The only types WCF will allow to be serialized or deserialized for this service are those in the service interface and these "known types".</span></span> <span data-ttu-id="a32f3-289">Bu listede olmayan başka bir tür değiştirme girişimi reddedilecektir.</span><span class="sxs-lookup"><span data-stu-id="a32f3-289">Attempting to exchange any other type not in this list will be rejected.</span></span>  
  
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
  
3. <span data-ttu-id="a32f3-290">Ardından, hizmet arabirimi için uygulama sağlar.</span><span class="sxs-lookup"><span data-stu-id="a32f3-290">Next, we provide the implementation for the service interface.</span></span>  
  
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
  
4. <span data-ttu-id="a32f3-291">WCF hizmetini çalıştırmak için, belirli bir WCF bağlama kullanarak bu hizmet arabirimini belirli bir URL'de ortaya çıkaran bir bitiş noktası beyan etmemiz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a32f3-291">To run the WCF service, we need to declare an endpoint that exposes that service interface at a specific URL using a specific WCF binding.</span></span> <span data-ttu-id="a32f3-292">Bu genellikle sunucu projesinin web.config dosyasına aşağıdaki bölümleri ekleyerek yapılır.</span><span class="sxs-lookup"><span data-stu-id="a32f3-292">This is typically done by adding the following sections to the server project’s web.config file.</span></span>  
  
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
  
5. <span data-ttu-id="a32f3-293">WCF hizmeti daha sonra aşağıdaki kodla başlatılabilir:</span><span class="sxs-lookup"><span data-stu-id="a32f3-293">The WCF service can then be started with the following code:</span></span>  
  
   ```csharp
   ServiceHost customerServiceHost = new ServiceHost(typeof(CustomerService));  
       customerServiceHost.Open();  
   ```  
  
     <span data-ttu-id="a32f3-294">Bu ServiceHost başlatıldığında, uygun sözleşme, bağlama ve bitiş noktası kurmak için web.config dosyasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="a32f3-294">When this ServiceHost is started, it uses the web.config file to establish the proper contract, binding and endpoint.</span></span> <span data-ttu-id="a32f3-295">Yapılandırma dosyaları hakkında daha fazla bilgi için [bkz.](./configuring-services-using-configuration-files.md)</span><span class="sxs-lookup"><span data-stu-id="a32f3-295">For more information about configuration files, see [Configuring Services Using Configuration Files](./configuring-services-using-configuration-files.md).</span></span> <span data-ttu-id="a32f3-296">Sunucuyu başlatma bu stil kendi kendine barındırma olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="a32f3-296">This style of starting the server is known as self-hosting.</span></span> <span data-ttu-id="a32f3-297">WCF hizmetlerini barındırmak için diğer seçenekler hakkında daha fazla bilgi edinmek için [Barındırma Hizmetleri'ne](./hosting-services.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="a32f3-297">To learn more about other choices for hosting WCF services, see [Hosting Services](./hosting-services.md).</span></span>  
  
6. <span data-ttu-id="a32f3-298">İstemci projenin app.config hizmetin bitiş noktası için eşleşen bağlayıcı bilgileri bildirmelidir.</span><span class="sxs-lookup"><span data-stu-id="a32f3-298">The client project’s app.config must declare matching binding information for the service’s endpoint.</span></span> <span data-ttu-id="a32f3-299">Visual Studio'da bunu yapmanın en kolay yolu, app.config dosyasını otomatik olarak güncelleştiren **Hizmet Başvurusu Ekle'yi**kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="a32f3-299">The easiest way to do this in Visual Studio is to use **Add Service Reference**, which will automatically update the app.config file.</span></span> <span data-ttu-id="a32f3-300">Alternatif olarak, bu aynı değişiklikler el ile eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="a32f3-300">Alternatively, these same changes can be added manually.</span></span>  
  
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
  
     <span data-ttu-id="a32f3-301">**Hizmet Başvurusu Ekle'yi**kullanma hakkında daha fazla bilgi için [bkz.](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference)</span><span class="sxs-lookup"><span data-stu-id="a32f3-301">For more information about using **Add Service Reference**, see [How to: Add, Update, or Remove a Service Reference](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference).</span></span>  
  
7. <span data-ttu-id="a32f3-302">Artık müşteriden WCF servisini arayabiliriz.</span><span class="sxs-lookup"><span data-stu-id="a32f3-302">Now we can call the WCF service from the client.</span></span> <span data-ttu-id="a32f3-303">Bunu, bu hizmet için bir kanal fabrikası oluşturarak, bir kanal isteyerek ve doğrudan o kanalda istediğimiz yöntemi arayarak yapıyoruz.</span><span class="sxs-lookup"><span data-stu-id="a32f3-303">We do this by creating a channel factory for that service, asking it for a channel, and directly calling the method we want on that channel.</span></span> <span data-ttu-id="a32f3-304">Bunu yapabiliriz, çünkü kanal hizmetin arabirimini uygular ve bizim için temel istek/yanıt mantığını işler.</span><span class="sxs-lookup"><span data-stu-id="a32f3-304">We can do this because the channel implements the service’s interface and handles the underlying request/reply logic for us.</span></span> <span data-ttu-id="a32f3-305">Bu yöntem çağrısından gelen iade değeri, sunucunun yanıtının deserialized kopyasıdır.</span><span class="sxs-lookup"><span data-stu-id="a32f3-305">The return value from that method call is the deserialized copy of the server’s response.</span></span>  
  
   ```csharp
   ChannelFactory<ICustomerService> factory =  
       new ChannelFactory<ICustomerService>("customerservice");  
   ICustomerService service = factory.CreateChannel();  
   Customer customer = service.GetCustomer(42);  
   Console.WriteLine($"  Customer {customer.FirstName} {customer.LastName} received.");
   ```  
  
 <span data-ttu-id="a32f3-306">WCF tarafından sunucudan istemciye döndürülen nesneler her zaman değere göredir.</span><span class="sxs-lookup"><span data-stu-id="a32f3-306">Objects returned by WCF from the server to the client are always by value.</span></span> <span data-ttu-id="a32f3-307">Nesneler, sunucu tarafından gönderilen verilerin seri olarak kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="a32f3-307">The objects are deserialized copies of the data sent by the server.</span></span> <span data-ttu-id="a32f3-308">İstemci, geri aramayoluyla sunucu kodu çağırma tehlikesi olmadan bu yerel kopyalarda yöntemleri çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="a32f3-308">The client can call methods on these local copies without any danger of invoking server code through callbacks.</span></span>  
  
#### <a name="scenario-2-server-returns-an-object-by-reference"></a><span data-ttu-id="a32f3-309">Senaryo 2: Sunucu Başvuruya Göre Bir Nesneyi Döndürür</span><span class="sxs-lookup"><span data-stu-id="a32f3-309">Scenario 2: Server Returns an Object By Reference</span></span>  
 <span data-ttu-id="a32f3-310">Bu senaryo, istemciye başvuru yla bir nesne sağlayan sunucuyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="a32f3-310">This scenario demonstrates the server providing an object to the client by reference.</span></span> <span data-ttu-id="a32f3-311">.NET Remoting'de bu işlem, başvuru tarafından serihale getirilmiş olan MarshalByRefObject'ten türetilen herhangi bir tür için otomatik olarak işlenir.</span><span class="sxs-lookup"><span data-stu-id="a32f3-311">In .NET Remoting, this is handled automatically for any type derived from MarshalByRefObject, which is serialized by-reference.</span></span> <span data-ttu-id="a32f3-312">Bu senaryoya örnek olarak, birden çok istemcinin bağımsız oturumlu sunucu tarafı nesnelerine sahip olmasını sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="a32f3-312">An example of this scenario is allowing multiple clients to have independent sessionful server-side objects.</span></span> <span data-ttu-id="a32f3-313">Daha önce de belirtildiği gibi, bir WCF hizmeti tarafından döndürülen nesneler her zaman değere göredir, bu nedenle başvuru saladeği doğrudan <xref:System.ServiceModel.EndpointAddress10> eşdeğeri yoktur, ancak bir nesne kullanarak başvuru salatiğine benzer bir şey elde etmek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="a32f3-313">As previously mentioned, objects returned by a WCF service are always by value, so there is no direct equivalent of a by-reference object, but it is possible to achieve something similar to by-reference semantics using an <xref:System.ServiceModel.EndpointAddress10> object.</span></span> <span data-ttu-id="a32f3-314">Bu, istemci tarafından sunucuda oturum dolu bir by-reference nesnesi elde etmek için kullanılabilecek serileştirilebilir bir yan değer nesnesidir.</span><span class="sxs-lookup"><span data-stu-id="a32f3-314">This is a serializable by-value object that can be used by the client to obtain a sessionful by-reference object on the server.</span></span> <span data-ttu-id="a32f3-315">Bu, bağımsız oturumlu sunucu tarafı nesneleri ile birden çok istemciye sahip olma senaryosunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="a32f3-315">This enables the scenario of having multiple clients with independent sessionful server-side objects.</span></span>  
  
1. <span data-ttu-id="a32f3-316">İlk olarak, oturum oluşturan nesnenin kendisine karşılık gelen bir WCF hizmet sözleşmesi tanımlamamız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a32f3-316">First, we need to define a WCF service contract that corresponds to the sessionful object itself.</span></span>  
  
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
    > <span data-ttu-id="a32f3-317">Oturum oluşturan nesnenin [ServiceContract] ile işaretlendiğini ve bu nedenle normal bir WCF hizmet arabirimi yaptığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="a32f3-317">Notice that the sessionful object is marked with [ServiceContract], making it a normal WCF service interface.</span></span> <span data-ttu-id="a32f3-318">SessionMode özelliğinin ayarlanması, bunun oturum lu bir hizmet olacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a32f3-318">Setting the SessionMode property indicates it will be a sessionful service.</span></span> <span data-ttu-id="a32f3-319">WCF'de oturum, iki uç nokta arasında gönderilen birden çok iletiyi ilişkilendirme yoludur.</span><span class="sxs-lookup"><span data-stu-id="a32f3-319">In WCF, a session is a way of correlating multiple messages sent between two endpoints.</span></span> <span data-ttu-id="a32f3-320">Bu, istemci bu hizmete bağlantı ulaştığında istemci ve sunucu arasında bir oturum oluşturulacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="a32f3-320">This means that once a client obtains a connection to this service, a session will be established between the client and the server.</span></span> <span data-ttu-id="a32f3-321">İstemci, bu tek oturumdaki tüm etkileşimleri için sunucu tarafındaki nesnenin tek bir benzersiz örneğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="a32f3-321">The client will use a single unique instance of the server-side object for all its interactions within this single session.</span></span>  
  
2. <span data-ttu-id="a32f3-322">Sonra, bu hizmet arabiriminin uygulanmasını sağlamamız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a32f3-322">Next, we need to provide the implementation of this service interface.</span></span> <span data-ttu-id="a32f3-323">[ServiceBehavior] ile ifade ederek ve InstanceContextMode ayarlayarak, WCF'ye her oturum için bu türbenzersiz bir örnek kullanmak istediğimizi söyleriz.</span><span class="sxs-lookup"><span data-stu-id="a32f3-323">By denoting it with [ServiceBehavior] and setting the InstanceContextMode, we tell WCF we want to use a unique instance of this type for an each session.</span></span>  
  
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
  
3. <span data-ttu-id="a32f3-324">Şimdi bu oturumlu nesnenin bir örneğini elde etmek için bir yol gerekir.</span><span class="sxs-lookup"><span data-stu-id="a32f3-324">Now we need a way to obtain an instance of this sessionful object.</span></span> <span data-ttu-id="a32f3-325">Bunu, Bir EndpointAddress10 nesnesi döndüren başka bir WCF hizmet arabirimi oluşturarak yapıyoruz.</span><span class="sxs-lookup"><span data-stu-id="a32f3-325">We do this by creating another WCF service interface that returns an EndpointAddress10 object.</span></span> <span data-ttu-id="a32f3-326">Bu, istemcinin oturum oluşturabilecek nesneyi oluşturmak için kullanabileceği bir bitiş noktasının serileştirilebilir biçimidir.</span><span class="sxs-lookup"><span data-stu-id="a32f3-326">This is a serializable form of an endpoint that the client can use to create the sessionful object.</span></span>  
  
   ```csharp
   [ServiceContract]  
       public interface ISessionBoundFactory  
       {  
           [OperationContract]  
           EndpointAddress10 GetInstanceAddress();  
       }  
   ```  
  
     <span data-ttu-id="a32f3-327">Ve bu WCF hizmetini uyguluyoruz:</span><span class="sxs-lookup"><span data-stu-id="a32f3-327">And we implement this WCF service:</span></span>  
  
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
  
     <span data-ttu-id="a32f3-328">Bu uygulama, oturumlu nesneler oluşturmak için bir singleton kanal fabrika tutar.</span><span class="sxs-lookup"><span data-stu-id="a32f3-328">This implementation maintains a singleton channel factory to create sessionful objects.</span></span> <span data-ttu-id="a32f3-329">GetInstanceAddress() çağrıldığında, bir kanal oluşturur ve bu kanalla ilişkili uzak adresi etkili bir şekilde işaret eden bir EndpointAddress10 nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a32f3-329">When GetInstanceAddress() is called, it creates a channel and creates an EndpointAddress10 object that effectively points to the remote address associated with this channel.</span></span> <span data-ttu-id="a32f3-330">EndpointAddress10 yalnızca istemciye göre döndürülebilen bir veri türüdür.</span><span class="sxs-lookup"><span data-stu-id="a32f3-330">EndpointAddress10 is simply a data type that can be returned to the client by-value.</span></span>  
  
4. <span data-ttu-id="a32f3-331">Aşağıdaki örnekte gösterildiği gibi aşağıdaki iki şeyi yaparak sunucunun yapılandırma dosyasını değiştirmemiz gerekir:</span><span class="sxs-lookup"><span data-stu-id="a32f3-331">We need to modify the server’s configuration file by doing the following two things as shown in the example below:</span></span>  
  
    1. <span data-ttu-id="a32f3-332">Oturum \<açan nesnenin bitiş noktasını açıklayan bir istemci> bölümü bildirin.</span><span class="sxs-lookup"><span data-stu-id="a32f3-332">Declare a \<client> section that describes the endpoint for the sessionful object.</span></span> <span data-ttu-id="a32f3-333">Sunucu da bu durumda bir istemci olarak hareket eder, çünkü bu gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a32f3-333">This is necessary because the server also acts as a client in this situation.</span></span>  
  
    2. <span data-ttu-id="a32f3-334">Fabrika ve oturum alagelen nesne için uç noktalarını bildirin.</span><span class="sxs-lookup"><span data-stu-id="a32f3-334">Declare endpoints for the factory and sessionful object.</span></span> <span data-ttu-id="a32f3-335">Bu, istemcinin EndpointAddress10'u elde etmek ve oturum lu kanalı oluşturmak için hizmet bitiş noktalarıyla iletişim kurmasına izin vermek için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a32f3-335">This is necessary to allow the client to communicate with the service endpoints to acquire the EndpointAddress10 and to create the sessionful channel.</span></span>  
  
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
  
     <span data-ttu-id="a32f3-336">Ve sonra şu hizmetleri başlatabiliriz:</span><span class="sxs-lookup"><span data-stu-id="a32f3-336">And then we can start these services:</span></span>  
  
   ```csharp
   ServiceHost factoryHost = new ServiceHost(typeof(SessionBoundFactory));  
   factoryHost.Open();  
  
   ServiceHost sessionHost = new ServiceHost(typeof(MySessionBoundObject));  
   sessionHost.Open();  
   ```  
  
5. <span data-ttu-id="a32f3-337">İstemciyi, projesinin app.config dosyasında aynı uç noktaları beyan ederek yapılandırıyoruz.</span><span class="sxs-lookup"><span data-stu-id="a32f3-337">We configure the client by declaring these same endpoints in its project’s app.config file.</span></span>  
  
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
  
6. <span data-ttu-id="a32f3-338">Bu oturumlu nesneyi oluşturmak ve kullanmak için istemci aşağıdaki adımları yapmalıdır:</span><span class="sxs-lookup"><span data-stu-id="a32f3-338">In order to create and use this sessionful object, the client must do the following steps:</span></span>  
  
    1. <span data-ttu-id="a32f3-339">ISessionBoundFactory hizmetiiçin bir kanal oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a32f3-339">Create a channel to the ISessionBoundFactory service.</span></span>  
  
    2. <span data-ttu-id="a32f3-340">Bir EndpointAddress10 almak için bu hizmeti çağırmak için bu kanalı kullanın.</span><span class="sxs-lookup"><span data-stu-id="a32f3-340">Use that channel to invoke that service to obtain an EndpointAddress10.</span></span>  
  
    3. <span data-ttu-id="a32f3-341">Oturum lu bir nesne elde etmek için bir kanal oluşturmak için EndpointAddress10'u kullanın.</span><span class="sxs-lookup"><span data-stu-id="a32f3-341">Use the EndpointAddress10 to create a channel to obtain a sessionful object.</span></span>  
  
    4. <span data-ttu-id="a32f3-342">Birden çok aramada aynı örnek olarak kaldığını göstermek için oturuma uygun nesneyle etkileşimkurun.</span><span class="sxs-lookup"><span data-stu-id="a32f3-342">Interact with the sessionful object to demonstrate it remains the same instance across multiple calls.</span></span>  
  
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
  
 <span data-ttu-id="a32f3-343">WCF nesneleri her zaman değere göre döndürür, ancak EndpointAddress10'u kullanarak referans semantik eşdeğerini desteklemek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="a32f3-343">WCF always returns objects by value, but it is possible to support the equivalent of by-reference semantics through the use of EndpointAddress10.</span></span> <span data-ttu-id="a32f3-344">Bu, istemcinin oturum lu bir WCF hizmeti örneği istemesine izin verir ve bundan sonra diğer WCF hizmetleri gibi onunla etkileşimkurabilir.</span><span class="sxs-lookup"><span data-stu-id="a32f3-344">This permits the client to request a sessionful WCF service instance, after which it can interact with it like any other WCF service.</span></span>  
  
#### <a name="scenario-3-client-sends-server-a-by-value-instance"></a><span data-ttu-id="a32f3-345">Senaryo 3: İstemci Sunucuya Bir By-Value Örneği Gönderir</span><span class="sxs-lookup"><span data-stu-id="a32f3-345">Scenario 3: Client Sends Server a By-Value Instance</span></span>  
 <span data-ttu-id="a32f3-346">Bu senaryo, istemcinin sunucuya değer bazında ilkel olmayan bir nesne örneği gönderdiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a32f3-346">This scenario demonstrates the client sending a non-primitive object instance to the server by value.</span></span> <span data-ttu-id="a32f3-347">WCF nesneleri yalnızca değere göre gönderdiğinden, bu senaryo normal WCF kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a32f3-347">Because WCF only sends objects by value, this scenario demonstrates normal WCF usage.</span></span>  
  
1. <span data-ttu-id="a32f3-348">Senaryo 1'deki aynı WCF Hizmetini kullanın.</span><span class="sxs-lookup"><span data-stu-id="a32f3-348">Use the same WCF Service from Scenario 1.</span></span>  
  
2. <span data-ttu-id="a32f3-349">İstemciyi yeni bir yan değer nesnesi (Müşteri) oluşturmak, ICustomerService hizmetiyle iletişim kurmak için bir kanal oluşturmak ve nesneyi ona göndermek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="a32f3-349">Use the client to create a new by-value object (Customer), create a channel to communicate with the ICustomerService service, and send the object to it.</span></span>  
  
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
  
     <span data-ttu-id="a32f3-350">Müşteri nesnesi seri hale getirilecek ve sunucuya gönderilir ve bu nesnenin yeni bir kopyasına dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="a32f3-350">The customer object will be serialized, and sent to the server, where it is deserialized into a new copy of that object.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="a32f3-351">Bu kod, türetilmiş bir tür (PremiumCustomer) göndermeyi de gösterir.</span><span class="sxs-lookup"><span data-stu-id="a32f3-351">This code also illustrates sending a derived type (PremiumCustomer).</span></span> <span data-ttu-id="a32f3-352">Hizmet arabirimi bir Müşteri nesnesi bekler, ancak Müşteri sınıfındaki [KnownType] özniteliği premiumcustomer'a da izin verildiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a32f3-352">The service interface expects a Customer object, but the [KnownType] attribute on the Customer class indicated PremiumCustomer was also allowed.</span></span> <span data-ttu-id="a32f3-353">WCF, bu hizmet arabirimi aracılığıyla başka bir türü serihale veya deserialize etme girişimlerini başarısız alacaktır.</span><span class="sxs-lookup"><span data-stu-id="a32f3-353">WCF will fail any attempt to serialize or deserialize any other type through this service interface.</span></span>  
  
 <span data-ttu-id="a32f3-354">Normal WCF veri değişimleri değere göredir.</span><span class="sxs-lookup"><span data-stu-id="a32f3-354">Normal WCF exchanges of data are by value.</span></span> <span data-ttu-id="a32f3-355">Bu, bu veri nesnelerinden birine çağrı yöntemlerinin yalnızca yerel olarak yürütüleceğini garanti eder – diğer katmanda kod çağırmaz.</span><span class="sxs-lookup"><span data-stu-id="a32f3-355">This guarantees that invoking methods on one of these data objects executes only locally – it will not invoke code on the other tier.</span></span> <span data-ttu-id="a32f3-356">Sunucudan döndürülen by-reference nesneleri gibi *from* bir şey elde etmek mümkün olsa da, istemcinin bir ara başvuru nesnesini *sunucuya* geçirmesi mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="a32f3-356">While it is possible to achieve something like by-reference objects returned *from* the server, it is not possible for a client to pass a by-reference object *to* the server.</span></span> <span data-ttu-id="a32f3-357">İstemci ve sunucu arasında ileri geri görüşme gerektiren bir senaryo, çift yönlü bir hizmet kullanılarak WCF'de elde edilebilir.</span><span class="sxs-lookup"><span data-stu-id="a32f3-357">A scenario that requires a conversation back and forth between client and server can be achieved in WCF using a duplex service.</span></span> <span data-ttu-id="a32f3-358">Daha fazla bilgi için [Çift Yönlü Hizmetler'e](./feature-details/duplex-services.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="a32f3-358">For more information, see [Duplex Services](./feature-details/duplex-services.md).</span></span>  
  
## <a name="summary"></a><span data-ttu-id="a32f3-359">Özet</span><span class="sxs-lookup"><span data-stu-id="a32f3-359">Summary</span></span>  
 <span data-ttu-id="a32f3-360">.NET Remoting, yalnızca tam güvenilen ortamlarda kullanılmak üzere tasarlanmış bir iletişim çerçevesidir.</span><span class="sxs-lookup"><span data-stu-id="a32f3-360">.NET Remoting is a communication framework intended to be used only within fully-trusted environments.</span></span> <span data-ttu-id="a32f3-361">Eski bir üründür ve yalnızca geriye dönük uyumluluk için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="a32f3-361">It is a legacy product and supported only for backward compatibility.</span></span> <span data-ttu-id="a32f3-362">Yeni uygulamalar oluşturmak için kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="a32f3-362">It should not be used to build new applications.</span></span> <span data-ttu-id="a32f3-363">Tam tersine, WCF güvenlik göz önünde bulundurularak tasarlanmıştır ve yeni ve mevcut uygulamalar için önerilir.</span><span class="sxs-lookup"><span data-stu-id="a32f3-363">Conversely, WCF was designed with security in mind and is recommended for new and existing applications.</span></span> <span data-ttu-id="a32f3-364">Microsoft, varolan Remoting uygulamalarının WCF veya ASP.NET Web API'sını kullanmak üzere geçirilmelerini önerir.</span><span class="sxs-lookup"><span data-stu-id="a32f3-364">Microsoft recommends that existing Remoting applications be migrated to use WCF or ASP.NET Web API instead.</span></span>
