---
title: ".NET Uzaktan İletişimden WCF'ye Taşınma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 16902a42-ef80-40e9-8c4c-90e61ddfdfe5
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6b387e100ff881c5394b6a77716a733b3928eae9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="migrating-from-net-remoting-to-wcf"></a><span data-ttu-id="007c6-102">.NET Uzaktan İletişimden WCF'ye Taşınma</span><span class="sxs-lookup"><span data-stu-id="007c6-102">Migrating from .NET Remoting to WCF</span></span>
<span data-ttu-id="007c6-103">Bu makalede, Windows Communication Foundation (WCF) kullanmak için .NET uzaktan iletişim kullanan bir uygulamayı geçirmek üzere açıklar.</span><span class="sxs-lookup"><span data-stu-id="007c6-103">This article describes how to migrate an application that uses .NET Remoting to use Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="007c6-104">Bu ürünler arasında benzer kavram karşılaştırır ve WCF birkaç ortak Remoting senaryolarda yüklemenin nasıl yapılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="007c6-104">It compares similar concepts between these products and then describes how to accomplish several common Remoting scenarios in WCF.</span></span>  
  
 <span data-ttu-id="007c6-105">.NET uzaktan iletişim yalnızca geriye dönük uyumluluk için desteklenen eski bir üründür.</span><span class="sxs-lookup"><span data-stu-id="007c6-105">.NET Remoting is a legacy product that is supported only for backward compatibility.</span></span> <span data-ttu-id="007c6-106">İstemci ve sunucu arasındaki ayrı güven düzeyleri korunamaz olduğundan karma güven ortamlar genelinde güvenli değil.</span><span class="sxs-lookup"><span data-stu-id="007c6-106">It is not secure across mixed-trust environments because it cannot maintain the separate trust levels between client and server.</span></span> <span data-ttu-id="007c6-107">Örneğin, bir .NET uzaktan iletişim uç noktası Internet veya güvenilmeyen istemciler için hiçbir zaman maruz bırakmamalısınız.</span><span class="sxs-lookup"><span data-stu-id="007c6-107">For example, you should never expose a .NET Remoting endpoint to the Internet or to untrusted clients.</span></span> <span data-ttu-id="007c6-108">Varolan Remoting öneririz uygulamalar için daha yeni ve daha güvenli teknolojiler geçirilmiş.</span><span class="sxs-lookup"><span data-stu-id="007c6-108">We recommend existing Remoting applications be migrated to newer and more secure technologies.</span></span> <span data-ttu-id="007c6-109">Uygulamanın tasarım yalnızca HTTP kullanır ve RESTful ise, ASP.NET Web API öneririz.</span><span class="sxs-lookup"><span data-stu-id="007c6-109">If the application’s design uses only HTTP and is RESTful, we recommend ASP.NET Web API.</span></span> <span data-ttu-id="007c6-110">Daha fazla bilgi için bkz: ASP.NET Web API.</span><span class="sxs-lookup"><span data-stu-id="007c6-110">For more information, see ASP.NET Web API.</span></span> <span data-ttu-id="007c6-111">Uygulama üzerinde SOAP tabanlı veya Http olmayan protokolleri TCP gibi gerekiyorsa, WCF öneririz.</span><span class="sxs-lookup"><span data-stu-id="007c6-111">If the application is based on SOAP or requires non-Http protocols such as TCP, we recommend WCF.</span></span>  

## <a name="comparing-net-remoting-to-wcf"></a><span data-ttu-id="007c6-112">.NET uzaktan iletişim için WCF karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="007c6-112">Comparing .NET Remoting to WCF</span></span>  
 <span data-ttu-id="007c6-113">Bu bölümde, .NET uzaktan iletişim temel yapı taşlarının WCF eşdeğerlerine ile karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="007c6-113">This section compares the basic building blocks of .NET Remoting with their WCF equivalents.</span></span> <span data-ttu-id="007c6-114">Bu yapı taşları daha sonra bazı genel istemci-sunucu senaryolar WCF'de oluşturmak için kullanacağız. Aşağıdaki grafikte ana benzerlikler ve .NET uzaktan iletişim ve WCF arasındaki farklar özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="007c6-114">We will use these building blocks later to create some common client-server scenarios in WCF.The following chart summarizes the main similarities and differences between .NET Remoting and WCF.</span></span>  
  
||<span data-ttu-id="007c6-115">.NET uzaktan iletişim</span><span class="sxs-lookup"><span data-stu-id="007c6-115">.NET Remoting</span></span>|<span data-ttu-id="007c6-116">WCF</span><span class="sxs-lookup"><span data-stu-id="007c6-116">WCF</span></span>|  
|-|-------------------|---------|  
|<span data-ttu-id="007c6-117">Sunucu türü</span><span class="sxs-lookup"><span data-stu-id="007c6-117">Server type</span></span>|<span data-ttu-id="007c6-118">Bir alt kümesi MarshalByRefObject</span><span class="sxs-lookup"><span data-stu-id="007c6-118">Subclass MarshalByRefObject</span></span>|<span data-ttu-id="007c6-119">[ServiceContract] özniteliği ile işaretleme</span><span class="sxs-lookup"><span data-stu-id="007c6-119">Mark with [ServiceContract] attribute</span></span>|  
|<span data-ttu-id="007c6-120">Hizmet işlemleri</span><span class="sxs-lookup"><span data-stu-id="007c6-120">Service operations</span></span>|<span data-ttu-id="007c6-121">Sunucu türü üzerinde genel yöntemler</span><span class="sxs-lookup"><span data-stu-id="007c6-121">Public methods on server type</span></span>|<span data-ttu-id="007c6-122">[OperationContract] özniteliği ile işaretleme</span><span class="sxs-lookup"><span data-stu-id="007c6-122">Mark with [OperationContract] attribute</span></span>|  
|<span data-ttu-id="007c6-123">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="007c6-123">Serialization</span></span>|<span data-ttu-id="007c6-124">ISerializable veya [Serializable]</span><span class="sxs-lookup"><span data-stu-id="007c6-124">ISerializable or [Serializable]</span></span>|<span data-ttu-id="007c6-125">DataContractSerializer veya XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="007c6-125">DataContractSerializer or XmlSerializer</span></span>|  
|<span data-ttu-id="007c6-126">Geçirilen nesneleri</span><span class="sxs-lookup"><span data-stu-id="007c6-126">Objects passed</span></span>|<span data-ttu-id="007c6-127">Değer tarafından veya başvuru tarafından</span><span class="sxs-lookup"><span data-stu-id="007c6-127">By-value or by-reference</span></span>|<span data-ttu-id="007c6-128">Tarafından yalnızca değeri</span><span class="sxs-lookup"><span data-stu-id="007c6-128">By-value only</span></span>|  
|<span data-ttu-id="007c6-129">Hataları/özel durumlar</span><span class="sxs-lookup"><span data-stu-id="007c6-129">Errors/exceptions</span></span>|<span data-ttu-id="007c6-130">Seri hale getirilebilir özel durumları</span><span class="sxs-lookup"><span data-stu-id="007c6-130">Any serializable exception</span></span>|<span data-ttu-id="007c6-131">FaultContract\<TDetail ></span><span class="sxs-lookup"><span data-stu-id="007c6-131">FaultContract\<TDetail></span></span>|  
|<span data-ttu-id="007c6-132">İstemci proxy nesneleri</span><span class="sxs-lookup"><span data-stu-id="007c6-132">Client proxy objects</span></span>|<span data-ttu-id="007c6-133">Kesin türü belirtilmiş saydam proxy'leri bulunan MarshalByRefObjects için otomatik olarak oluşturulur</span><span class="sxs-lookup"><span data-stu-id="007c6-133">Strongly typed transparent proxies are created automatically from MarshalByRefObjects</span></span>|<span data-ttu-id="007c6-134">Kesin türü belirtilmiş proxy'leri üretilen isteğe bağlı ChannelFactory kullanma\<TChannel ></span><span class="sxs-lookup"><span data-stu-id="007c6-134">Strongly typed proxies are generated on-demand using ChannelFactory\<TChannel></span></span>|  
|<span data-ttu-id="007c6-135">Gereken platformu</span><span class="sxs-lookup"><span data-stu-id="007c6-135">Platform required</span></span>|<span data-ttu-id="007c6-136">İstemci ve sunucu Microsoft OS ve .NET kullanmanız gerekir</span><span class="sxs-lookup"><span data-stu-id="007c6-136">Both client and server must use Microsoft OS and .NET</span></span>|<span data-ttu-id="007c6-137">Platformlar arası</span><span class="sxs-lookup"><span data-stu-id="007c6-137">Cross-platform</span></span>|  
|<span data-ttu-id="007c6-138">İleti biçimi</span><span class="sxs-lookup"><span data-stu-id="007c6-138">Message format</span></span>|<span data-ttu-id="007c6-139">Özel</span><span class="sxs-lookup"><span data-stu-id="007c6-139">Private</span></span>|<span data-ttu-id="007c6-140">Endüstri standartları (SOAP, WS-*, vb..)</span><span class="sxs-lookup"><span data-stu-id="007c6-140">Industry standards (SOAP, WS-*, etc.)</span></span>|  
  
### <a name="server-implementation-comparison"></a><span data-ttu-id="007c6-141">Sunucu uygulaması karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="007c6-141">Server Implementation Comparison</span></span>  
  
#### <a name="creating-a-server-in-net-remoting"></a><span data-ttu-id="007c6-142">.NET uzaktan iletişim bir sunucu oluşturma</span><span class="sxs-lookup"><span data-stu-id="007c6-142">Creating a Server in .NET Remoting</span></span>  
 <span data-ttu-id="007c6-143">.NET uzaktan iletişim sunucu türleri, MarshalByRefObject öğesinden türetilen ve istemci, aşağıdaki gibi çağırabilirsiniz yöntemleri tanımlayın:</span><span class="sxs-lookup"><span data-stu-id="007c6-143">.NET Remoting server types must derive from MarshalByRefObject and define methods the client can call, like the following:</span></span>  
  
```csharp
public class RemotingServer : MarshalByRefObject  
{  
    public Customer GetCustomer(int customerId) { … }  
}  
```  
  
 <span data-ttu-id="007c6-144">Genel yöntemler bu sunucu türü ortak sözleşme istemciler için kullanılabilir olur.</span><span class="sxs-lookup"><span data-stu-id="007c6-144">The public methods of this server type become the public contract available to clients.</span></span>  <span data-ttu-id="007c6-145">Sunucunun ortak arabirimi ile uygulaması arasında hiçbir ayrım – bir türü hem de işler.</span><span class="sxs-lookup"><span data-stu-id="007c6-145">There is no separation between the server’s public interface and its implementation – one type handles both.</span></span>  
  
 <span data-ttu-id="007c6-146">Sunucu türü tanımlandıktan sonra istemciler için kullanılabilir aşağıdaki örnekte ister:</span><span class="sxs-lookup"><span data-stu-id="007c6-146">Once the server type has been defined, it can be made available to clients, like in the following example:</span></span>  
  
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
  
 <span data-ttu-id="007c6-147">Uzaktan iletişim türünü yapılandırma dosyalarını kullanma da dahil, bir sunucu olarak kullanılabilir hale getirmek için birçok yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="007c6-147">There are many ways to make the Remoting type available as a server, including using configuration files.</span></span> <span data-ttu-id="007c6-148">Bu yalnızca bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="007c6-148">This is just one example.</span></span>  
  
#### <a name="creating-a-server-in-wcf"></a><span data-ttu-id="007c6-149">WCF'de bir sunucu oluşturma</span><span class="sxs-lookup"><span data-stu-id="007c6-149">Creating a Server in WCF</span></span>  
 <span data-ttu-id="007c6-150">WCF eşdeğer adımda iki tür--genel "hizmet sözleşmesi" ve somut uygulaması oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="007c6-150">The equivalent step in WCF involves creating two types -- the public "service contract" and the concrete implementation.</span></span> <span data-ttu-id="007c6-151">İlk [ServiceContract] ile işaretli bir arabirim olarak bildirilir.</span><span class="sxs-lookup"><span data-stu-id="007c6-151">The first is declared as an interface marked with [ServiceContract].</span></span> <span data-ttu-id="007c6-152">İstemciler için kullanılabilir yöntemleri [OperationContract] ile işaretli:</span><span class="sxs-lookup"><span data-stu-id="007c6-152">Methods available to clients are marked with [OperationContract]:</span></span>  
  
```csharp
[ServiceContract]  
public interface IWCFServer  
{  
    [OperationContract]  
    Customer GetCustomer(int customerId);  
}  
```  
  
 <span data-ttu-id="007c6-153">Sunucu uygulaması aşağıdaki örnekte gibi ayrı somut sınıfında tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="007c6-153">The server’s implementation is defined in a separate concrete class, like in the following example:</span></span>  
  
```csharp
public class WCFServer : IWCFServer  
{  
    public Customer GetCustomer(int customerId) { … }  
}  
```  
  
 <span data-ttu-id="007c6-154">Bu tür tanımladıktan sonra WCF sunucunun istemciler için kullanılabilir hale getirilebilir aşağıdaki örnekte ister:</span><span class="sxs-lookup"><span data-stu-id="007c6-154">Once these types have been defined, the WCF server can be made available to clients, like in the following example:</span></span>  
  
```csharp
NetTcpBinding binding = new NetTcpBinding();  
Uri baseAddress = new Uri("net.tcp://localhost:8000/wcfserver");  
  
using (ServiceHost serviceHost = new ServiceHost(typeof(WCFServer), baseAddress))  
{  
    serviceHost.AddServiceEndpoint(typeof(IWCFServer), binding, baseAddress);  
    serviceHost.Open();  
  
    Console.WriteLine(String.Format("The WCF server is ready at {0}.",  
                                    baseAddress));  
    Console.WriteLine("Press <ENTER> to terminate service...");  
    Console.WriteLine();  
    Console.ReadLine();  
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="007c6-155">TCP örneklerin her ikisi de mümkün olduğu kadar benzer tutmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="007c6-155">TCP is used in both examples to keep them as similar as possible.</span></span> <span data-ttu-id="007c6-156">HTTP kullanan örnekler için bu konunun ilerleyen bölümlerinde senaryo kılavuzlarına başvurun.</span><span class="sxs-lookup"><span data-stu-id="007c6-156">Refer to the scenario walk-throughs later in this topic for examples using HTTP.</span></span>  
  
 <span data-ttu-id="007c6-157">Yapılandırmak için birçok yolu vardır ve WCF hizmetlerini barındırmak için.</span><span class="sxs-lookup"><span data-stu-id="007c6-157">There are many ways to configure and to host WCF services.</span></span> <span data-ttu-id="007c6-158">Bu "kendi kendini barındıran" bilinen yalnızca bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="007c6-158">This is just one example, known as "self-hosted".</span></span> <span data-ttu-id="007c6-159">Daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="007c6-159">For more information, see the following topics:</span></span>  
  
-   [<span data-ttu-id="007c6-160">Nasıl yapılır: Bir Hizmet Anlaşması Tanımlama</span><span class="sxs-lookup"><span data-stu-id="007c6-160">How to: Define a Service Contract</span></span>](how-to-define-a-wcf-service-contract.md)  
  
-   [<span data-ttu-id="007c6-161">Yapılandırma Dosyalarını Kullanarak Hizmetleri Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="007c6-161">Configuring Services Using Configuration Files</span></span>](configuring-services-using-configuration-files.md)  
  
-   [<span data-ttu-id="007c6-162">Barındırma Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="007c6-162">Hosting Services</span></span>](hosting-services.md)  
  
### <a name="client-implementation-comparison"></a><span data-ttu-id="007c6-163">İstemci uygulaması karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="007c6-163">Client Implementation Comparison</span></span>  
  
#### <a name="creating-a-client-in-net-remoting"></a><span data-ttu-id="007c6-164">.NET uzaktan iletişim içinde bir istemci oluşturma</span><span class="sxs-lookup"><span data-stu-id="007c6-164">Creating a Client in .NET Remoting</span></span>  
 <span data-ttu-id="007c6-165">Bir .NET uzaktan iletişim sunucu nesnesi kullanılabilir yapıldıktan sonra istemciler tarafından gibi aşağıdaki örnekte tüketilebilir:</span><span class="sxs-lookup"><span data-stu-id="007c6-165">Once a .NET Remoting server object has been made available, it can be consumed by clients, like in the following example:</span></span>  
  
```csharp
TcpChannel channel = new TcpChannel();  
ChannelServices.RegisterChannel(channel, ensureSecurity : true);  
RemotingServer server = (RemotingServer)Activator.GetObject(  
                            typeof(RemotingServer),   
                            "tcp://localhost:8080/RemotingServer");  
  
RemotingCustomer customer = server.GetCustomer(42);  
Console.WriteLine(String.Format("Customer {0} {1} received.",   
                                 customer.FirstName, customer.LastName));  
```  
  
 <span data-ttu-id="007c6-166">Activator.GetObject() döndürülen RemotingServer örneği bir "saydam proxy." adı verilir</span><span class="sxs-lookup"><span data-stu-id="007c6-166">The RemotingServer instance returned from Activator.GetObject() is known as a "transparent proxy."</span></span> <span data-ttu-id="007c6-167">İstemcide RemotingServer türü için genel API'si uygular, ancak farklı bir işlem veya makine çalışan sunucu nesnesi tüm yöntemlerini çağırın.</span><span class="sxs-lookup"><span data-stu-id="007c6-167">It implements the public API for the RemotingServer type on the client, but all the methods call the server object running in a different process or machine.</span></span>  
  
#### <a name="creating-a-client-in-wcf"></a><span data-ttu-id="007c6-168">WCF'de bir istemci oluşturma</span><span class="sxs-lookup"><span data-stu-id="007c6-168">Creating a Client in WCF</span></span>  
 <span data-ttu-id="007c6-169">WCF'de eşdeğer adımı proxy açıkça oluşturmak için bir kanal fabrikası kullanarak içerir.</span><span class="sxs-lookup"><span data-stu-id="007c6-169">The equivalent step in WCF involves using a channel factory to create the proxy explicitly.</span></span> <span data-ttu-id="007c6-170">Proxy nesnesi Remoting gibi aşağıdaki örnekte sunucu üzerindeki işlemler gibi çağırmak için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="007c6-170">Like Remoting, the proxy object can be used to invoke operations on the server, like in the following example:</span></span>  
  
```csharp
NetTcpBinding binding = new NetTcpBinding();  
String url = "net.tcp://localhost:8000/wcfserver";  
EndpointAddress address = new EndpointAddress(url);  
ChannelFactory<IWCFServer> channelFactory =   
    new ChannelFactory<IWCFServer>(binding, address);  
IWCFServer server = channelFactory.CreateChannel();  
  
Customer customer = server.GetCustomer(42);  
Console.WriteLine(String.Format("  Customer {0} {1} received.",  
                    customer.FirstName, customer.LastName));  
```  
  
 <span data-ttu-id="007c6-171">Bu örnek en Remoting örnektekine benzer olduğundan kanal düzeyinde programlama gösterir.</span><span class="sxs-lookup"><span data-stu-id="007c6-171">This example shows programming at the channel level because it is most similar to the Remoting example.</span></span> <span data-ttu-id="007c6-172">Ayrıca kullanılabilir **hizmet Başvurusu Ekle** yaklaşım Visual Studio'da, programlama istemci basitleştirmek için kod oluşturur.</span><span class="sxs-lookup"><span data-stu-id="007c6-172">Also available is the **Add Service Reference** approach in Visual Studio that generates code to simplify client programming.</span></span> <span data-ttu-id="007c6-173">Daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="007c6-173">For more information, see the following topics:</span></span>  
  
-   [<span data-ttu-id="007c6-174">İstemci Kanal Düzeyi Programlama</span><span class="sxs-lookup"><span data-stu-id="007c6-174">Client Channel-Level Programming</span></span>](./extending/client-channel-level-programming.md)  
  
-   [<span data-ttu-id="007c6-175">Nasıl yapılır: ekleme, güncelleştirme veya hizmet başvurusunu kaldırma</span><span class="sxs-lookup"><span data-stu-id="007c6-175">How to: Add, Update, or Remove a Service Reference</span></span>](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference)  
  
### <a name="serialization-usage"></a><span data-ttu-id="007c6-176">Seri hale getirme kullanımı</span><span class="sxs-lookup"><span data-stu-id="007c6-176">Serialization Usage</span></span>  
 <span data-ttu-id="007c6-177">.NET uzaktan iletişim ve WCF istemci ve sunucu arasında nesneleri göndermek için seri hale getirme kullanır, ancak bunlar bu önemli farklar:</span><span class="sxs-lookup"><span data-stu-id="007c6-177">Both .NET Remoting and WCF use serialization to send objects between client and server, but they differ in these important ways:</span></span>  
  
1.  <span data-ttu-id="007c6-178">Bunlar farklı serileştiricileri ve kuralları ne serileştirmek belirtmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="007c6-178">They use different serializers and conventions to indicate what to serialize.</span></span>  
  
2.  <span data-ttu-id="007c6-179">.NET uzaktan iletişim güvenlik sınırları boyunca olan diğer katmanda, kod yürütmek için bir katmana yöntemi veya özelliği erişim sağlar. "tarafından başvurusu" serileştirme destekler.</span><span class="sxs-lookup"><span data-stu-id="007c6-179">.NET Remoting supports "by reference" serialization that allows method or property access on one tier to execute code on the other tier, which is across security boundaries.</span></span> <span data-ttu-id="007c6-180">Bu özellik, güvenlik açıkları gösterir ve neden uzak uç noktaları asla güvenilmeyen istemcilere açılmamalıdır temel nedenlerinden biridir.</span><span class="sxs-lookup"><span data-stu-id="007c6-180">This capability exposes security vulnerabilities and is one of the main reasons why Remoting endpoints should never be exposed to untrusted clients.</span></span>  
  
3.  <span data-ttu-id="007c6-181">Uzaktan iletişim tarafından kullanılan serileştirme çevirin (açıkça dışarıda bırakmak serileştirmek için hangi değil) ve WCF serileştirme kabulü (seri hale getirmek için hangi üyeleri açıkça işaretleyin).</span><span class="sxs-lookup"><span data-stu-id="007c6-181">Serialization used by Remoting is opt-out (explicitly exclude what not to serialize) and WCF serialization is opt-in (explicitly mark which members to serialize).</span></span>  
  
#### <a name="serialization-in-net-remoting"></a><span data-ttu-id="007c6-182">.NET uzaktan iletişim serileştirme</span><span class="sxs-lookup"><span data-stu-id="007c6-182">Serialization in .NET Remoting</span></span>  
 <span data-ttu-id="007c6-183">.NET uzaktan iletişim seri hale getirmek ve istemci ve sunucu arasında nesneleri seri durumdan için iki yol destekler:</span><span class="sxs-lookup"><span data-stu-id="007c6-183">.NET Remoting supports two ways to serialize and deserialize objects between the client and server:</span></span>  
  
-   <span data-ttu-id="007c6-184">*Değere göre* – nesnenin değerlerini katmanı sınırlarında serileştirilen ve söz konusu nesne yeni bir örneğini diğer katmanında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="007c6-184">*By value* – the values of the object are serialized across tier boundaries, and a new instance of that object is created on the other tier.</span></span> <span data-ttu-id="007c6-185">Yöntemleri ya da bu yeni örnek özelliklerini yapılan her çağrı yalnızca yerel olarak yürütün ve özgün nesne veya katmanı etkilemez.</span><span class="sxs-lookup"><span data-stu-id="007c6-185">Any calls to methods or properties of that new instance execute only locally and do not affect the original object or tier.</span></span>  
  
-   <span data-ttu-id="007c6-186">*Başvuruya göre* – özel bir "nesne başvurusu" katmanı sınırlarında serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="007c6-186">*By reference* – a special "object reference" is serialized across tier boundaries.</span></span> <span data-ttu-id="007c6-187">Yöntemleri ya da bu nesnenin özellikleri ile bir katman etkileşim kurduğunda özgün katman özgün nesneye geri iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="007c6-187">When one tier interacts with methods or properties of that object, it communicates back to the original object on the original tier.</span></span> <span data-ttu-id="007c6-188">Başvuru tarafından nesneleri herhangi bir yönde – sunucudan istemciye ya da istemciden sunucuya akabilir.</span><span class="sxs-lookup"><span data-stu-id="007c6-188">By-reference objects can flow in either direction – server to client, or client to server.</span></span>  
  
 <span data-ttu-id="007c6-189">Remoting değeri tarafından türlerinde [Serializable] özniteliğiyle işaretlenmiş veya ISerializable, aşağıdaki örnekte gibi uygulama:</span><span class="sxs-lookup"><span data-stu-id="007c6-189">By-value types in Remoting are marked with the [Serializable] attribute or implement ISerializable, like in the following example:</span></span>  
  
```csharp
[Serializable]  
public class RemotingCustomer  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
    public int CustomerId { get; set; }  
}  
```  
  
 <span data-ttu-id="007c6-190">Başvuru tarafından türleri MarshalByRefObject sınıfından aşağıdaki örnekte gibi türetilen:</span><span class="sxs-lookup"><span data-stu-id="007c6-190">By-reference types derive from the MarshalByRefObject class, like in the following example:</span></span>  
  
```csharp
public class RemotingCustomerReference : MarshalByRefObject  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
    public int CustomerId { get; set; }  
}  
```  
  
 <span data-ttu-id="007c6-191">Remoting'in başvuru tarafından nesneleri etkilerini anlamak oldukça önemlidir.</span><span class="sxs-lookup"><span data-stu-id="007c6-191">It is extremely important to understand the implications of Remoting’s by-reference objects.</span></span> <span data-ttu-id="007c6-192">(İstemci veya sunucu) ya da katmanı için diğer katmanı tarafından başvuru nesnesi gönderirse, tüm yöntem çağrıları geri nesnenin sahibi olan katmanında yürütün.</span><span class="sxs-lookup"><span data-stu-id="007c6-192">If either tier (client or server) sends a by-reference object to the other tier, all method calls execute back on the tier owning the object.</span></span> <span data-ttu-id="007c6-193">Örneğin, sunucu tarafından döndürülen başvuru tarafından nesnesi üzerinde yöntemleri çağırma istemci kodu sunucuda yürütülür.</span><span class="sxs-lookup"><span data-stu-id="007c6-193">For example, a client calling methods on a by-reference object returned by the server will execute code on the server.</span></span> <span data-ttu-id="007c6-194">Benzer şekilde, istemci tarafından sağlanan bir başvuru tarafından nesnesinde yöntemleri çağırma bir sunucu kodu istemci üzerinde yürütülür.</span><span class="sxs-lookup"><span data-stu-id="007c6-194">Similarly, a server calling methods on a by-reference object provided by the client will execute code back on the client.</span></span> <span data-ttu-id="007c6-195">Bu nedenle, yalnızca tam güvenilir ortamlar içinde .NET uzaktan iletişim kullanılması önerilir.</span><span class="sxs-lookup"><span data-stu-id="007c6-195">For this reason, the use of .NET Remoting is recommended only within fully-trusted environments.</span></span> <span data-ttu-id="007c6-196">Güvenilmeyen istemciler için genel bir .NET uzaktan iletişim uç nokta gösterme, bir uzak sunucu saldırılara karşı savunmasız hale getirir.</span><span class="sxs-lookup"><span data-stu-id="007c6-196">Exposing a public .NET Remoting endpoint to untrusted clients will make a Remoting server vulnerable to attack.</span></span>  
  
#### <a name="serialization-in-wcf"></a><span data-ttu-id="007c6-197">WCF'de seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="007c6-197">Serialization in WCF</span></span>  
 <span data-ttu-id="007c6-198">WCF yalnızca değer tarafından serileştirme destekler.</span><span class="sxs-lookup"><span data-stu-id="007c6-198">WCF supports only by-value serialization.</span></span> <span data-ttu-id="007c6-199">Aşağıdaki örnekte istemci ve sunucu arasında exchange için bir türü tanımlamak için en yaygın yolu gibidir:</span><span class="sxs-lookup"><span data-stu-id="007c6-199">The most common way to define a type to exchange between client and server is like in the following example:</span></span>  
  
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
  
 <span data-ttu-id="007c6-200">[DataContract] özniteliği serileştirilmiş ve istemci ile sunucu arasında seri bu türü biri olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="007c6-200">The [DataContract] attribute identifies this type as one that can be serialized and deserialized between client and server.</span></span> <span data-ttu-id="007c6-201">[DataMember] özniteliği ayrı ayrı özellikler veya alanlar serileştirmek için tanımlar.</span><span class="sxs-lookup"><span data-stu-id="007c6-201">The [DataMember] attribute identifies the individual properties or fields to serialize.</span></span>  
  
 <span data-ttu-id="007c6-202">WCF katmanları arasında bir nesne gönderdiğinde, yalnızca değerleri serileştirir ve diğer katmanında nesnesinin yeni bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="007c6-202">When WCF sends an object across tiers, it serializes only the values and creates a new instance of the object on the other tier.</span></span> <span data-ttu-id="007c6-203">Nesnenin değerleriyle herhangi bir etkileşimi yalnızca yerel olarak – ortaya bunlar şekilde .NET uzaktan iletişim başvuru tarafından Nesneleri'ne diğer katmanı ile iletişim kurmazlar.</span><span class="sxs-lookup"><span data-stu-id="007c6-203">Any interactions with the values of the object occur only locally – they do not communicate with the other tier the way .NET Remoting by-reference objects do.</span></span> <span data-ttu-id="007c6-204">Daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="007c6-204">For more information, see the following topics:</span></span>  
  
-   [<span data-ttu-id="007c6-205">Serileştirme ve Seri Durumdan Çıkarma</span><span class="sxs-lookup"><span data-stu-id="007c6-205">Serialization and Deserialization</span></span>](./feature-details/serialization-and-deserialization.md)  
  
-   [<span data-ttu-id="007c6-206">Windows Communication Foundation'da seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="007c6-206">Serialization in Windows Communication Foundation</span></span>](http://msdn.microsoft.com/magazine/cc163569.aspx)  
  
### <a name="exception-handling-capabilities"></a><span data-ttu-id="007c6-207">Özel durum işleme özellikleri</span><span class="sxs-lookup"><span data-stu-id="007c6-207">Exception Handling Capabilities</span></span>  
  
#### <a name="exceptions-in-net-remoting"></a><span data-ttu-id="007c6-208">.NET uzaktan iletişim özel durumları</span><span class="sxs-lookup"><span data-stu-id="007c6-208">Exceptions in .NET Remoting</span></span>  
 <span data-ttu-id="007c6-209">Bir uzak sunucu tarafından oluşturulan özel durumları istemciye gönderilen, serileştirilen ve başka bir özel durum gibi istemci üzerinde yerel olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="007c6-209">Exceptions thrown by a Remoting server are serialized, sent to the client, and thrown locally on the client like any other exception.</span></span> <span data-ttu-id="007c6-210">Özel durumları, özel durum türü alt classing ve [Serializable] ile işaretleme tarafından oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="007c6-210">Custom exceptions can be created by sub-classing the Exception type and marking it with [Serializable].</span></span>   <span data-ttu-id="007c6-211">Çoğu framework özel durumları zaten sıralanabilir ve istemcide yeniden oluşturulması için sunucu tarafından oluşturulan çoğu izin vererek bu şekilde işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="007c6-211">Most framework exceptions are already marked in this way, allowing most to be thrown by the server, serialized, and re-thrown on the client.</span></span> <span data-ttu-id="007c6-212">Bu tasarım geliştirme sırasında kullanışlı olsa da, sunucu tarafı bilgileri yanlışlıkla istemciye çıkarılabilecek.</span><span class="sxs-lookup"><span data-stu-id="007c6-212">Though this design is convenient during development, server-side information can inadvertently be disclosed to the client.</span></span> <span data-ttu-id="007c6-213">Bu, yalnızca tam güvenilir ortamlarında Remoting kullanılması gereken birçok nedenden biri.</span><span class="sxs-lookup"><span data-stu-id="007c6-213">This is one of many reasons Remoting should be used only in fully-trusted environments.</span></span>  
  
#### <a name="exceptions-and-faults-in-wcf"></a><span data-ttu-id="007c6-214">Özel durumlar ve WCF hataları</span><span class="sxs-lookup"><span data-stu-id="007c6-214">Exceptions and Faults in WCF</span></span>  
 <span data-ttu-id="007c6-215">WCF bilgilerin yanlışlıkla açığa çıkmasına için sunucudan istemciye döndürülecek rasgele özel durum türleri izin vermiyor.</span><span class="sxs-lookup"><span data-stu-id="007c6-215">WCF does not allow arbitrary exception types to be returned from the server to the client because it could lead to inadvertent information disclosure.</span></span> <span data-ttu-id="007c6-216">Bir hizmet işlemi beklenmeyen bir özel durum oluşturursa, genel amaçlı FaultException istemcide durum oluşturulmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="007c6-216">If a service operation throws an unexpected exception, it causes a general purpose FaultException to be thrown on the client.</span></span> <span data-ttu-id="007c6-217">Bu özel durumun neden veya burada bir hata oluştu ve bazı uygulamalar için bu yeterli herhangi bir bilgi taşımaz.</span><span class="sxs-lookup"><span data-stu-id="007c6-217">This exception does not carry any information why or where the problem occurred, and for some applications this is sufficient.</span></span> <span data-ttu-id="007c6-218">Gereken uygulamalar istemci yapmak için daha zengin hata bilgisi bu hataya sözleşmesi tanımlayarak iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="007c6-218">Applications that need to communicate richer error information to the client do this by defining a fault contract.</span></span>  
  
 <span data-ttu-id="007c6-219">Bunu yapmak için önce hata bilgilerini taşımak için bir [DataContract] türü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="007c6-219">To do this, first create a [DataContract] type to carry the fault information.</span></span>  
  
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
  
 <span data-ttu-id="007c6-220">Her hizmet işlemi için kullanılacak hatalı sözleşme belirtin.</span><span class="sxs-lookup"><span data-stu-id="007c6-220">Specify the fault contract to use for each service operation.</span></span>  
  
```csharp
[ServiceContract]  
public interface IWCFServer  
{  
    [OperationContract]  
    [FaultContract(typeof(CustomerServiceFault))]  
    Customer GetCustomer(int customerId);  
}  
```  
  
 <span data-ttu-id="007c6-221">Sunucu, bir FaultException atma tarafından hata koşulları bildirir.</span><span class="sxs-lookup"><span data-stu-id="007c6-221">The server reports error conditions by throwing a FaultException.</span></span>  
  
```csharp
throw new FaultException<CustomerServiceFault>(  
    new CustomerServiceFault() {   
        CustomerId = customerId,   
        ErrorMessage = "Illegal customer Id"   
    });  
```  
  
 <span data-ttu-id="007c6-222">Ve istemcisi sunucuya istekte olduğunda, normal özel durumlar olarak hatalar yakalayabilir.</span><span class="sxs-lookup"><span data-stu-id="007c6-222">And whenever the client makes a request to the server, it can catch faults as normal exceptions.</span></span>  
  
```csharp
try  
{  
    Customer customer = server.GetCustomer(-1);  
}  
catch (FaultException<CustomerServiceFault> fault)  
{  
    Console.WriteLine(String.Format("Fault received: {0}",  
    fault.Detail.ErrorMessage));  
}  
```  
  
 <span data-ttu-id="007c6-223">Hataya sözleşmeleri hakkında daha fazla bilgi için bkz: <xref:System.ServiceModel.FaultException>.</span><span class="sxs-lookup"><span data-stu-id="007c6-223">For more information about fault contracts, see <xref:System.ServiceModel.FaultException>.</span></span>  
  
### <a name="security-considerations"></a><span data-ttu-id="007c6-224">Güvenlik Değerlendirmeleri</span><span class="sxs-lookup"><span data-stu-id="007c6-224">Security Considerations</span></span>  
  
#### <a name="security-in-net-remoting"></a><span data-ttu-id="007c6-225">.NET uzaktan iletişim güvenliği</span><span class="sxs-lookup"><span data-stu-id="007c6-225">Security in .NET Remoting</span></span>  
 <span data-ttu-id="007c6-226">Bazı .NET uzaktan iletişim kanalları kimlik doğrulama ve şifrelemeyi (IPC ve TCP) kanal katmanında gibi güvenlik özelliklerini destekler.</span><span class="sxs-lookup"><span data-stu-id="007c6-226">Some .NET Remoting channels support security features such as authentication and encryption at the channel layer (IPC and TCP).</span></span> <span data-ttu-id="007c6-227">HTTP kanalı, kimlik doğrulama ve şifreleme için Internet Information Services (IIS) kullanır.</span><span class="sxs-lookup"><span data-stu-id="007c6-227">The HTTP channel relies on Internet Information Services (IIS) for both authentication and encryption.</span></span> <span data-ttu-id="007c6-228">Bu destek rağmen güvenli olmayan bir iletişim protokolü .NET uzaktan iletişim göz önünde bulundurun ve yalnızca tam güvenilir ortamlar içinde kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="007c6-228">Despite this support, you should consider .NET Remoting an unsecure communication protocol and use it only within fully-trusted environments.</span></span> <span data-ttu-id="007c6-229">Hiçbir zaman İnternet'te veya güvenilmeyen istemciler için genel bir uzak uç nokta kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="007c6-229">Never expose a public Remoting endpoint to the Internet or untrusted clients.</span></span>  
  
#### <a name="security-in-wcf"></a><span data-ttu-id="007c6-230">WCF'de Güvenlik</span><span class="sxs-lookup"><span data-stu-id="007c6-230">Security in WCF</span></span>  
 <span data-ttu-id="007c6-231">WCF ile göz önünde bulundurularak, kısmen .NET uzaktan iletişim içinde bulunan güvenlik açıklarına türlerini gidermek için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="007c6-231">WCF was designed with security in mind, in part to address the kinds of vulnerabilities found in .NET Remoting.</span></span> <span data-ttu-id="007c6-232">WCF taşıma ve ileti düzeyinde güvenlik sunar ve kimlik doğrulama, yetkilendirme, şifreleme vb. için birçok seçenek sunar.</span><span class="sxs-lookup"><span data-stu-id="007c6-232">WCF offers security at both the transport and message level, and offers many options for authentication, authorization, encryption, and so on.</span></span> <span data-ttu-id="007c6-233">Daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="007c6-233">For more information, see the following topics:</span></span>  
  
-   [<span data-ttu-id="007c6-234">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="007c6-234">Security</span></span>](./feature-details/security.md)  
  
-   [<span data-ttu-id="007c6-235">WCF Güvenlik Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="007c6-235">WCF Security Guidance</span></span>](./feature-details/security-guidance-and-best-practices.md)  
  
## <a name="migrating-to-wcf"></a><span data-ttu-id="007c6-236">Wcf'ye taşınma</span><span class="sxs-lookup"><span data-stu-id="007c6-236">Migrating to WCF</span></span>  
  
### <a name="why-migrate-from-remoting-to-wcf"></a><span data-ttu-id="007c6-237">Neden uzaktan iletişimden WCF'ye geçirme?</span><span class="sxs-lookup"><span data-stu-id="007c6-237">Why Migrate from Remoting to WCF?</span></span>  
  
-   <span data-ttu-id="007c6-238">**.NET uzaktan iletişim eski bir üründür.**</span><span class="sxs-lookup"><span data-stu-id="007c6-238">**.NET Remoting is a legacy product.**</span></span> <span data-ttu-id="007c6-239">Bölümünde açıklandığı gibi [.NET uzaktan iletişim](http://msdn.microsoft.com/library/vstudio/72x4h507\(v=vs.100\).aspx), eski bir ürün olarak kabul edilir ve yeni geliştirme projeleri için önerilmez.</span><span class="sxs-lookup"><span data-stu-id="007c6-239">As described in [.NET Remoting](http://msdn.microsoft.com/library/vstudio/72x4h507\(v=vs.100\).aspx), it is considered a legacy product and is not recommended for new development.</span></span> <span data-ttu-id="007c6-240">WCF veya ASP.NET Web API yeni ve mevcut uygulamalar için önerilir.</span><span class="sxs-lookup"><span data-stu-id="007c6-240">WCF or ASP.NET Web API are recommended for new and existing applications.</span></span>  
  
-   <span data-ttu-id="007c6-241">**WCF platformlar arası standartlar kullanır.**</span><span class="sxs-lookup"><span data-stu-id="007c6-241">**WCF uses cross-platform standards.**</span></span> <span data-ttu-id="007c6-242">WCF ile platformlar arası birlikte çalışabilirlik aklınızda tasarlanmıştır ve çoğu endüstri standartları destekler (SOAP, WS-Security, WS-Trust, vs.).</span><span class="sxs-lookup"><span data-stu-id="007c6-242">WCF was designed with cross-platform interoperability in mind and supports many industry standards (SOAP, WS-Security, WS-Trust, etc.).</span></span> <span data-ttu-id="007c6-243">Bir WCF Hizmeti Windows dışındaki işletim sistemlerinde çalışan istemcileri ile çalışabilirler.</span><span class="sxs-lookup"><span data-stu-id="007c6-243">A WCF service can interoperate with clients running on operating systems other than Windows.</span></span> <span data-ttu-id="007c6-244">Remoting, birincil sunucu ve istemci uygulamaları bir Windows işletim sisteminde .NET framework kullanılarak çalıştırdığı ortamlar için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="007c6-244">Remoting was designed primarily for environments where both the server and client applications run using the .NET framework on a Windows operating system.</span></span>  
  
-   <span data-ttu-id="007c6-245">**WCF yerleşik güvenlik sahiptir.**</span><span class="sxs-lookup"><span data-stu-id="007c6-245">**WCF has built-in security.**</span></span> <span data-ttu-id="007c6-246">WCF güvenlik göz önünde bulundurularak ile tasarlanmıştır ve kimlik doğrulama, taşıma düzeyi güvenliği, ileti düzeyi güvenlik vb. için birçok seçenek sunar. Remoting birlikte çalışmak üzere uygulamalar için kolaylaştırmak için tasarlanmıştır ancak güvenilir olmayan ortamlarda güvenli olacak şekilde tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="007c6-246">WCF was designed with security in mind and offers many options for authentication, transport level security, message level security, etc. Remoting was designed to make it easy for applications to interoperate but was not designed to be secure in non-trusted environments.</span></span> <span data-ttu-id="007c6-247">WCF, güvenilir ve güvenilir olmayan ortamlarda çalışmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="007c6-247">WCF was designed to work in both trusted and non-trusted environments.</span></span>  
  
### <a name="migration-recommendations"></a><span data-ttu-id="007c6-248">Geçiş önerileri</span><span class="sxs-lookup"><span data-stu-id="007c6-248">Migration Recommendations</span></span>  
 <span data-ttu-id="007c6-249">.NET uzaktan iletişimden WCF'ye geçirme için önerilen adımları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="007c6-249">The following are the recommended steps to migrate from .NET Remoting to WCF:</span></span>  
  
-   <span data-ttu-id="007c6-250">**Hizmet sözleşmesi oluşturun.**</span><span class="sxs-lookup"><span data-stu-id="007c6-250">**Create the service contract.**</span></span> <span data-ttu-id="007c6-251">Hizmet arabirimi türlerini tanımlayın ve bunları [ServiceContract] özniteliğiyle işaretleyin. İstemciler [OperationContract] ile çağırmak için izin verilecek tüm yöntemleri işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="007c6-251">Define your service interface types, and mark them with the [ServiceContract] attribute.Mark all the methods the clients will be allowed to call with [OperationContract].</span></span>  
  
-   <span data-ttu-id="007c6-252">**Veri sözleşmesi oluşturun.**</span><span class="sxs-lookup"><span data-stu-id="007c6-252">**Create the data contract.**</span></span> <span data-ttu-id="007c6-253">İstemci ve sunucu arasında alınıp ve [DataContract] özniteliğiyle işaretlerken veri türlerini tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="007c6-253">Define the data types that will be exchanged between server and client, and mark them with the [DataContract] attribute.</span></span> <span data-ttu-id="007c6-254">İstemci [DataMember] ile kullanmasına izin tüm alanları ve özellikleri işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="007c6-254">Mark all the fields and properties the client will be allowed to use with [DataMember].</span></span>  
  
-   <span data-ttu-id="007c6-255">**Hatalı Sözleşme (isteğe bağlı) oluşturun.**</span><span class="sxs-lookup"><span data-stu-id="007c6-255">**Create the fault contract (optional).**</span></span> <span data-ttu-id="007c6-256">Hatalarla karşılaştığında, istemci ve sunucu arasında alınıp türleri oluşturun.</span><span class="sxs-lookup"><span data-stu-id="007c6-256">Create the types that will be exchanged between server and client when errors are encountered.</span></span> <span data-ttu-id="007c6-257">Bu türleriyle [DataContract] ve [DataMember] seri hale getirilebilir yapmak için işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="007c6-257">Mark these types with [DataContract] and [DataMember] to make them serializable.</span></span> <span data-ttu-id="007c6-258">[OperationContract] ile işaretli tüm hizmet işlemleri için Ayrıca bunları [bunlar döndürebilir hangi hatalarını belirtmek için FaultContract] ile işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="007c6-258">For all service operations you marked with [OperationContract], also mark them with [FaultContract] to indicate which errors they may return.</span></span>  
  
-   <span data-ttu-id="007c6-259">**Hizmetini barındırır ve yapılandırın.**</span><span class="sxs-lookup"><span data-stu-id="007c6-259">**Configure and host the service.**</span></span> <span data-ttu-id="007c6-260">Hizmet sözleşmesi oluşturulduktan sonra sonraki adım hizmetin bir uç noktada kullanıma sunmak için bir bağlama yapılandırmaktır.</span><span class="sxs-lookup"><span data-stu-id="007c6-260">Once the service contract has been created, the next step is to configure a binding to expose the service at an endpoint.</span></span> <span data-ttu-id="007c6-261">Daha fazla bilgi için bkz: [uç noktalar: adresler, bağlamalar ve sözleşmeler](./feature-details/endpoints-addresses-bindings-and-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="007c6-261">For more information, see [Endpoints: Addresses, Bindings, and Contracts](./feature-details/endpoints-addresses-bindings-and-contracts.md).</span></span>  
  
 <span data-ttu-id="007c6-262">Remoting uygulama için WCF geçirildikten sonra .NET uzaktan iletişim bağımlılıkları kaldırın hala önemlidir.</span><span class="sxs-lookup"><span data-stu-id="007c6-262">Once a Remoting application has been migrated to WCF, it is still important to remove dependencies on .NET Remoting.</span></span> <span data-ttu-id="007c6-263">Bu, herhangi bir uzak açığını uygulamadan kaldırılır sağlar.</span><span class="sxs-lookup"><span data-stu-id="007c6-263">This ensures that any Remoting vulnerabilities are removed from the application.</span></span> <span data-ttu-id="007c6-264">Bu adımlar şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="007c6-264">These steps include the following:</span></span>  
  
-   <span data-ttu-id="007c6-265">**MarshalByRefObject kullanımını durdur.**</span><span class="sxs-lookup"><span data-stu-id="007c6-265">**Discontinue use of MarshalByRefObject.**</span></span> <span data-ttu-id="007c6-266">MarshalByRefObject türü yalnızca uzaktan iletişim için mevcut ve WCF tarafından kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="007c6-266">The MarshalByRefObject type exists only for Remoting and is not used by WCF.</span></span> <span data-ttu-id="007c6-267">MarshalByRefObject alt sınıf tüm uygulama türleri kaldırılan veya değiştirilen.</span><span class="sxs-lookup"><span data-stu-id="007c6-267">Any application types that sub-class MarshalByRefObject should be removed or changed.</span></span> <span data-ttu-id="007c6-268">MarshalByRefObject türü yalnızca uzaktan iletişim için mevcut ve WCF tarafından kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="007c6-268">The MarshalByRefObject type exists only for Remoting and is not used by WCF.</span></span> <span data-ttu-id="007c6-269">MarshalByRefObject alt sınıf tüm uygulama türleri kaldırılan veya değiştirilen.</span><span class="sxs-lookup"><span data-stu-id="007c6-269">Any application types that sub-class MarshalByRefObject should be removed or changed.</span></span>  
  
-   <span data-ttu-id="007c6-270">**[Serializable] kullanımını ve ISerializable durdur.**</span><span class="sxs-lookup"><span data-stu-id="007c6-270">**Discontinue use of [Serializable] and ISerializable.**</span></span> <span data-ttu-id="007c6-271">[Serializable] özniteliği ve ISerializable arabirimi başlangıçta güvenilen ortamlar içinde türleri serileştirmek için tasarlanmıştır ve bunlar tarafından uzaktan iletişim kullanılır.</span><span class="sxs-lookup"><span data-stu-id="007c6-271">The [Serializable] attribute and ISerializable interface were originally designed to serialize types within trusted environments, and they are used by Remoting.</span></span> <span data-ttu-id="007c6-272">WCF seri hale getirme [DataContract] ile işaretli türleri ve [DataMember] dayanır.</span><span class="sxs-lookup"><span data-stu-id="007c6-272">WCF serialization relies on types being marked with [DataContract] and [DataMember].</span></span> <span data-ttu-id="007c6-273">Bir uygulama tarafından kullanılan veri türleri [DataContract] kullanın ve ISerializable veya [Serializable] kullanmayacak şekilde değiştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="007c6-273">Data types used by an application should be modified to use [DataContract] and not to use ISerializable or [Serializable].</span></span> <span data-ttu-id="007c6-274">[Serializable] özniteliği ve ISerializable arabirimi başlangıçta güvenilen ortamlar içinde türleri serileştirmek için tasarlanmıştır ve bunlar tarafından uzaktan iletişim kullanılır.</span><span class="sxs-lookup"><span data-stu-id="007c6-274">The [Serializable] attribute and ISerializable interface were originally designed to serialize types within trusted environments, and they are used by Remoting.</span></span> <span data-ttu-id="007c6-275">WCF seri hale getirme [DataContract] ile işaretli türleri ve [DataMember] dayanır.</span><span class="sxs-lookup"><span data-stu-id="007c6-275">WCF serialization relies on types being marked with [DataContract] and [DataMember].</span></span> <span data-ttu-id="007c6-276">Bir uygulama tarafından kullanılan veri türleri [DataContract] kullanın ve ISerializable veya [Serializable] kullanmayacak şekilde değiştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="007c6-276">Data types used by an application should be modified to use [DataContract] and not to use ISerializable or [Serializable].</span></span>  
  
### <a name="migration-scenarios"></a><span data-ttu-id="007c6-277">Geçiş senaryoları</span><span class="sxs-lookup"><span data-stu-id="007c6-277">Migration Scenarios</span></span>  
 <span data-ttu-id="007c6-278">Şimdi aşağıdaki ortak Remoting senaryolarda WCF gerçekleştirmek nasıl görelim:</span><span class="sxs-lookup"><span data-stu-id="007c6-278">Now let’s see how to accomplish the following common Remoting scenarios in WCF:</span></span>  
  
1.  <span data-ttu-id="007c6-279">Sunucu istemciye bir nesne tarafından-değeri döndürür</span><span class="sxs-lookup"><span data-stu-id="007c6-279">Server returns an object by-value to the client</span></span>  
  
2.  <span data-ttu-id="007c6-280">Sunucu istemciye bir nesne başvuru tarafından döndürür</span><span class="sxs-lookup"><span data-stu-id="007c6-280">Server returns an object by-reference to the client</span></span>  
  
3.  <span data-ttu-id="007c6-281">İstemci bir nesne tarafından-değeri sunucusuna gönderir.</span><span class="sxs-lookup"><span data-stu-id="007c6-281">Client sends an object by-value to the server</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="007c6-282">WCF'de bir nesne başvuru tarafından istemciden sunucuya gönderme izin verilmiyor.</span><span class="sxs-lookup"><span data-stu-id="007c6-282">Sending an object by-reference from the client to the server is not allowed in WCF.</span></span>  
  
 <span data-ttu-id="007c6-283">Bu senaryolar üzerinden okunurken .NET uzaktan iletişim için bizim temel arabirimleri gibi aşağıdaki örneğe varsayalım.</span><span class="sxs-lookup"><span data-stu-id="007c6-283">When reading through these scenarios, assume our baseline interfaces for .NET Remoting look like the following example.</span></span> <span data-ttu-id="007c6-284">.NET uzaktan iletişim uygulaması WCF eşdeğer işlevsellik uygulamak için yalnızca nasıl kullanılacağını göstermek istiyoruz çünkü burada önemli değildir.</span><span class="sxs-lookup"><span data-stu-id="007c6-284">The .NET Remoting implementation is not important here because we want to illustrate only how to use WCF to implement equivalent functionality.</span></span>  
  
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
  
#### <a name="scenario-1-service-returns-an-object-by-value"></a><span data-ttu-id="007c6-285">Senaryo 1: Hizmet bir nesne değeri döndürür</span><span class="sxs-lookup"><span data-stu-id="007c6-285">Scenario 1: Service Returns an Object by Value</span></span>  
 <span data-ttu-id="007c6-286">Bu senaryo, bir nesne değeri tarafından istemciye göndermeden bir sunucu gösterir.</span><span class="sxs-lookup"><span data-stu-id="007c6-286">This scenario demonstrates a server returning an object to the client by value.</span></span> <span data-ttu-id="007c6-287">Aşağıdaki adımlar yalnızca normal bir WCF hizmeti oluşturma açıklamak için WCF her zaman nesneleri sunucudan değere göre döndürür.</span><span class="sxs-lookup"><span data-stu-id="007c6-287">WCF always returns objects from the server by value, so the following steps simply describe how to build a normal WCF service.</span></span>  
  
1.  <span data-ttu-id="007c6-288">WCF hizmeti için ortak bir arabirim tanımlayarak başlatın ve [ServiceContract] özniteliğiyle işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="007c6-288">Start by defining a public interface for the WCF service and mark it with the [ServiceContract] attribute.</span></span> <span data-ttu-id="007c6-289">[OperationContract] istemci çağıracak sunucu tarafı yöntemlerinin tanımlamak için kullanırız.</span><span class="sxs-lookup"><span data-stu-id="007c6-289">We use [OperationContract] to identify the server-side methods our client will call.</span></span>  
  
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
  
2.  <span data-ttu-id="007c6-290">Sonraki adım, bu hizmet için veri sözleşmesi oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="007c6-290">The next step is to create the data contract for this service.</span></span> <span data-ttu-id="007c6-291">Biz [DataContract] özniteliğiyle işaretlenmiş sınıflar (arabirimler değil) oluşturarak bunu.</span><span class="sxs-lookup"><span data-stu-id="007c6-291">We do this by creating classes (not interfaces) marked with the [DataContract] attribute.</span></span> <span data-ttu-id="007c6-292">Ayrı ayrı özellikler veya alanlar hem istemci hem de sunucu görünür istiyoruz [DataMember] ile işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="007c6-292">The individual properties or fields we want visible to both client and server are marked with [DataMember].</span></span> <span data-ttu-id="007c6-293">İzin verilmesi için türetilen türlerin istiyoruz, biz [KnownType] özniteliği bunları tanımlamak için kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="007c6-293">If we want derived types to be allowed, we must use the [KnownType] attribute to identify them.</span></span> <span data-ttu-id="007c6-294">Yalnızca türü WCF serileştirilecek veya bu hizmeti için hizmet arabirimi ve bu "bilinen türlerini" de serisi olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="007c6-294">The only types WCF will allow to be serialized or deserialized for this service are those in the service interface and these "known types".</span></span> <span data-ttu-id="007c6-295">Bu listede olmayan herhangi bir türü exchange çalışılıyor reddedilir.</span><span class="sxs-lookup"><span data-stu-id="007c6-295">Attempting to exchange any other type not in this list will be rejected.</span></span>  
  
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
  
3.  <span data-ttu-id="007c6-296">Ardından, hizmet arabirimi uygulamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="007c6-296">Next, we provide the implementation for the service interface.</span></span>  
  
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
  
4.  <span data-ttu-id="007c6-297">WCF hizmetini çalıştırmak için belirli bir WCF bağlamayı kullanarak belirli bir URL, bu hizmet arabirimi kullanıma sunan bir uç nokta bildirmek ihtiyacımız.</span><span class="sxs-lookup"><span data-stu-id="007c6-297">To run the WCF service, we need to declare an endpoint that exposes that service interface at a specific URL using a specific WCF binding.</span></span> <span data-ttu-id="007c6-298">Bu durum genellikle aşağıdaki bölümlerde sunucu projenin web.config dosyasına ekleyerek yapılır.</span><span class="sxs-lookup"><span data-stu-id="007c6-298">This is typically done by adding the following sections to the server project’s web.config file.</span></span>  
  
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
  
5.  <span data-ttu-id="007c6-299">WCF hizmet sonra aşağıdaki kodla başlatılabilir:</span><span class="sxs-lookup"><span data-stu-id="007c6-299">The WCF service can then be started with the following code:</span></span>  
  
   ```csharp
   ServiceHost customerServiceHost = new ServiceHost(typeof(CustomerService));  
       customerServiceHost.Open();  
   ```  
  
     <span data-ttu-id="007c6-300">Bu ServiceHost başlatıldığında, web.config dosyasının uygun sözleşme ve bağlama bitiş noktası kurmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="007c6-300">When this ServiceHost is started, it uses the web.config file to establish the proper contract, binding and endpoint.</span></span> <span data-ttu-id="007c6-301">Yapılandırma dosyaları hakkında daha fazla bilgi için bkz: [yapılandırma dosyalarını kullanarak Hizmetleri Yapılandırma](./configuring-services-using-configuration-files.md).</span><span class="sxs-lookup"><span data-stu-id="007c6-301">For more information about configuration files, see [Configuring Services Using Configuration Files](./configuring-services-using-configuration-files.md).</span></span> <span data-ttu-id="007c6-302">Sunucu başlatma bu stili kendi kendine barındırma olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="007c6-302">This style of starting the server is known as self-hosting.</span></span> <span data-ttu-id="007c6-303">WCF hizmetlerini barındırmak için diğer seçenekler hakkında daha fazla bilgi için bkz: [barındırma hizmetleri](./hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="007c6-303">To learn more about other choices for hosting WCF services, see [Hosting Services](./hosting-services.md).</span></span>  
  
6.  <span data-ttu-id="007c6-304">İstemci projenin app.config hizmet uç noktası için eşleşen bağlama bilgileri belirtmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="007c6-304">The client project’s app.config must declare matching binding information for the service’s endpoint.</span></span> <span data-ttu-id="007c6-305">Visual Studio'da bunu yapmanın en kolay yolu kullanmaktır **hizmet Başvurusu Ekle**, hangi otomatik olarak güncelleştirilecek app.config dosyası.</span><span class="sxs-lookup"><span data-stu-id="007c6-305">The easiest way to do this in Visual Studio is to use **Add Service Reference**, which will automatically update the app.config file.</span></span> <span data-ttu-id="007c6-306">Alternatif olarak, aynı değişiklikleri el ile eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="007c6-306">Alternatively, these same changes can be added manually.</span></span>  
  
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
  
     <span data-ttu-id="007c6-307">Kullanma hakkında daha fazla bilgi için **hizmet Başvurusu Ekle**, bkz: [nasıl yapılır: ekleme, güncelleştirme veya hizmet başvurusunu kaldırma](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference).</span><span class="sxs-lookup"><span data-stu-id="007c6-307">For more information about using **Add Service Reference**, see [How to: Add, Update, or Remove a Service Reference](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference).</span></span>  
  
7.  <span data-ttu-id="007c6-308">Şimdi biz istemciden WCF Hizmeti çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="007c6-308">Now we can call the WCF service from the client.</span></span> <span data-ttu-id="007c6-309">Biz bu hizmet için bir kanal fabrikası oluşturma için bir kanal soran ve doğrudan bu kanalda istiyoruz yöntemi çağırma bunu.</span><span class="sxs-lookup"><span data-stu-id="007c6-309">We do this by creating a channel factory for that service, asking it for a channel, and directly calling the method we want on that channel.</span></span> <span data-ttu-id="007c6-310">Kanal hizmetin arabirimini uygulayan ve bize için temel alınan istek/yanıt mantığı işler çünkü bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="007c6-310">We can do this because the channel implements the service’s interface and handles the underlying request/reply logic for us.</span></span> <span data-ttu-id="007c6-311">Bu yöntem çağrısının dönüş değerini sunucunun yanıt seri durumdan çıkarılmış kopyasıdır.</span><span class="sxs-lookup"><span data-stu-id="007c6-311">The return value from that method call is the deserialized copy of the server’s response.</span></span>  
  
   ```csharp
   ChannelFactory<ICustomerService> factory =  
       new ChannelFactory<ICustomerService>("customerservice");  
   ICustomerService service = factory.CreateChannel();  
   Customer customer = service.GetCustomer(42);  
   Console.WriteLine(String.Format("  Customer {0} {1} received.",  
           customer.FirstName, customer.LastName));  
   ```  
  
 <span data-ttu-id="007c6-312">WCF tarafından sunucudan istemciye döndürülen her zaman değeriyle nesneleridir.</span><span class="sxs-lookup"><span data-stu-id="007c6-312">Objects returned by WCF from the server to the client are always by value.</span></span> <span data-ttu-id="007c6-313">Sunucu tarafından gönderilen verileri seri durumdan çıkarılmış kopyalarını nesneleridir.</span><span class="sxs-lookup"><span data-stu-id="007c6-313">The objects are deserialized copies of the data sent by the server.</span></span> <span data-ttu-id="007c6-314">İstemci, sunucu kodu geri çağırma hiçbir tehlike olmadan bu yerel kopyalar üzerinde yöntemleri çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="007c6-314">The client can call methods on these local copies without any danger of invoking server code through callbacks.</span></span>  
  
#### <a name="scenario-2-server-returns-an-object-by-reference"></a><span data-ttu-id="007c6-315">Senaryo 2: Sunucu başvuruya göre bir nesne döndürür</span><span class="sxs-lookup"><span data-stu-id="007c6-315">Scenario 2: Server Returns an Object By Reference</span></span>  
 <span data-ttu-id="007c6-316">Bu senaryo, bir nesne başvurusu tarafından istemciye sağlayan sunucuda gösterir.</span><span class="sxs-lookup"><span data-stu-id="007c6-316">This scenario demonstrates the server providing an object to the client by reference.</span></span> <span data-ttu-id="007c6-317">.NET uzaktan çalışma, bu otomatik olarak MarshalByRefObject öğesinden türetilmiş herhangi bir tür için işlenir başvuru tarafından olduğu seri hale getirilmiş.</span><span class="sxs-lookup"><span data-stu-id="007c6-317">In .NET Remoting, this is handled automatically for any type derived from MarshalByRefObject, which is serialized by-reference.</span></span> <span data-ttu-id="007c6-318">Bu senaryo örneği süre sonuyla sunucu tarafı nesneleri bağımsız sağlamak birden çok istemciye izin verir.</span><span class="sxs-lookup"><span data-stu-id="007c6-318">An example of this scenario is allowing multiple clients to have independent sessionful server-side objects.</span></span> <span data-ttu-id="007c6-319">Daha önce belirtildiği gibi bir WCF hizmeti tarafından döndürülen nesne her zaman değer ile bu yüzden bir başvuru olarak nesnesinin doğrudan bir eşdeğer ancak semantiği başvuru olarak kullanılacak benzer bir şey elde etmek olası bir <xref:System.ServiceModel.EndpointAddress10> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="007c6-319">As previously mentioned, objects returned by a WCF service are always by value, so there is no direct equivalent of a by-reference object, but it is possible to achieve something similar to by-reference semantics using an <xref:System.ServiceModel.EndpointAddress10> object.</span></span> <span data-ttu-id="007c6-320">Bu sunucu üzerindeki bir süre sonuyla başvurusu tarafından nesnesi edinmek için istemci tarafından kullanılan bir değer tarafından seri hale getirilebilir nesnesidir.</span><span class="sxs-lookup"><span data-stu-id="007c6-320">This is a serializable by-value object that can be used by the client to obtain a sessionful by-reference object on the server.</span></span> <span data-ttu-id="007c6-321">Bu süre sonuyla sunucu tarafı nesneleri bağımsız ile birden çok istemciye sahip olmanın senaryo sağlar.</span><span class="sxs-lookup"><span data-stu-id="007c6-321">This enables the scenario of having multiple clients with independent sessionful server-side objects.</span></span>  
  
1.  <span data-ttu-id="007c6-322">İlk olarak, biz süre sonuyla nesnenin kendisine karşılık gelen bir WCF Hizmeti sözleşmesi tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="007c6-322">First, we need to define a WCF service contract that corresponds to the sessionful object itself.</span></span>  
  
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
    >  <span data-ttu-id="007c6-323">Normal bir WCF Hizmeti arabirimi kolaylaştırarak süre sonuyla nesnesi [ServiceContract] ile işaretli olduğundan, dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="007c6-323">Notice that the sessionful object is marked with [ServiceContract], making it a normal WCF service interface.</span></span> <span data-ttu-id="007c6-324">SessionMode ayarlama özelliği, bir süre sonuyla hizmet olacaktır belirtir.</span><span class="sxs-lookup"><span data-stu-id="007c6-324">Setting the SessionMode property indicates it will be a sessionful service.</span></span> <span data-ttu-id="007c6-325">WCF'de, bir oturum iki uç noktaları arasında gönderilen birden fazla ileti bağıntı bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="007c6-325">In WCF, a session is a way of correlating multiple messages sent between two endpoints.</span></span> <span data-ttu-id="007c6-326">Bu, bir istemci bu hizmet için bir bağlantı alır sonra bir oturum istemci ve sunucu arasında kurulacak olduğunu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="007c6-326">This means that once a client obtains a connection to this service, a session will be established between the client and the server.</span></span> <span data-ttu-id="007c6-327">İstemci bu tek oturum içinde kendi etkileşimler için sunucu tarafı nesnesi tek bir benzersiz örneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="007c6-327">The client will use a single unique instance of the server-side object for all its interactions within this single session.</span></span>  
  
2.  <span data-ttu-id="007c6-328">Ardından, biz bu hizmet arabirimi uyarlamasını sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="007c6-328">Next, we need to provide the implementation of this service interface.</span></span> <span data-ttu-id="007c6-329">[ServiceBehavior] ile belirten ve InstanceContextMode ayarını, biz WCF Biz bu tür benzersiz bir örnek bir her oturum için kullanmak istediğiniz söyleyin.</span><span class="sxs-lookup"><span data-stu-id="007c6-329">By denoting it with [ServiceBehavior] and setting the InstanceContextMode, we tell WCF we want to use a unique instance of this type for an each session.</span></span>  
  
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
  
3.  <span data-ttu-id="007c6-330">Şimdi bu süre sonuyla nesne örneği elde etmek için bir yol gerekir.</span><span class="sxs-lookup"><span data-stu-id="007c6-330">Now we need a way to obtain an instance of this sessionful object.</span></span> <span data-ttu-id="007c6-331">Biz bunu bir EndpointAddress10 nesnesi başka bir WCF Hizmeti arabirimi oluşturarak yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="007c6-331">We do this by creating another WCF service interface that returns an EndpointAddress10 object.</span></span> <span data-ttu-id="007c6-332">Bu istemci süre sonuyla nesnesi oluşturmak için kullanabileceğiniz bir uç nokta seri hale getirilebilir biçimidir.</span><span class="sxs-lookup"><span data-stu-id="007c6-332">This is a serializable form of an endpoint that the client can use to create the sessionful object.</span></span>  
  
   ```csharp
   [ServiceContract]  
       public interface ISessionBoundFactory  
       {  
           [OperationContract]  
           EndpointAddress10 GetInstanceAddress();  
       }  
   ```  
  
     <span data-ttu-id="007c6-333">Biz bu WCF hizmetini ve uygulamak:</span><span class="sxs-lookup"><span data-stu-id="007c6-333">And we implement this WCF service:</span></span>  
  
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
  
     <span data-ttu-id="007c6-334">Bu uygulama süre sonuyla nesneleri oluşturmak için bir singleton kanal fabrikası tutar.</span><span class="sxs-lookup"><span data-stu-id="007c6-334">This implementation maintains a singleton channel factory to create sessionful objects.</span></span> <span data-ttu-id="007c6-335">GetInstanceAddress() çağrıldığında bir kanal oluşturur ve etkili bir şekilde bu kanal ile ilişkilendirilen uzak adres işaret eden bir EndpointAddress10 nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="007c6-335">When GetInstanceAddress() is called, it creates a channel and creates an EndpointAddress10 object that effectively points to the remote address associated with this channel.</span></span> <span data-ttu-id="007c6-336">EndpointAddress10 istemci tarafından değerinin döndürülebilecek yalnızca bir veri türüdür.</span><span class="sxs-lookup"><span data-stu-id="007c6-336">EndpointAddress10 is simply a data type that can be returned to the client by-value.</span></span>  
  
4.  <span data-ttu-id="007c6-337">Aşağıdaki örnekte gösterildiği gibi iki şunları yaparak sunucu yapılandırma dosyasını değiştirmek ihtiyacımız var:</span><span class="sxs-lookup"><span data-stu-id="007c6-337">We need to modify the server’s configuration file by doing the following two things as shown in the example below:</span></span>  
  
    1.  <span data-ttu-id="007c6-338">Bildirme bir \<istemci > süre sonuyla nesne için uç noktaya açıklayan bölümü.</span><span class="sxs-lookup"><span data-stu-id="007c6-338">Declare a \<client> section that describes the endpoint for the sessionful object.</span></span> <span data-ttu-id="007c6-339">Bu, sunucunun da bu durumda istemci olarak davrandığı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="007c6-339">This is necessary because the server also acts as a client in this situation.</span></span>  
  
    2.  <span data-ttu-id="007c6-340">Uç noktaları Fabrika ve sessionful nesnesinin bildirin.</span><span class="sxs-lookup"><span data-stu-id="007c6-340">Declare endpoints for the factory and sessionful object.</span></span> <span data-ttu-id="007c6-341">Bu istemcinin hizmet uç noktaları ile EndpointAddress10 almaya ve süre sonuyla kanal oluşturmak için iletişim sağlamak gereklidir.</span><span class="sxs-lookup"><span data-stu-id="007c6-341">This is necessary to allow the client to communicate with the service endpoints to acquire the EndpointAddress10 and to create the sessionful channel.</span></span>  
  
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
  
     <span data-ttu-id="007c6-342">Ve ardından Biz bu hizmetleri başlatabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="007c6-342">And then we can start these services:</span></span>  
  
   ```csharp
   ServiceHost factoryHost = new ServiceHost(typeof(SessionBoundFactory));  
   factoryHost.Open();  
  
   ServiceHost sessionHost = new ServiceHost(typeof(MySessionBoundObject));  
   sessionHost.Open();  
   ```  
  
5.  <span data-ttu-id="007c6-343">Biz, istemci kendi projenin app.config dosyasını aynı Bu uç noktaları bildirerek yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="007c6-343">We configure the client by declaring these same endpoints in its project’s app.config file.</span></span>  
  
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
  
6.  <span data-ttu-id="007c6-344">Oluşturun ve bu süre sonuyla nesnesini kullanmak için istemci aşağıdakileri yapmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="007c6-344">In order to create and use this sessionful object, the client must do the following steps:</span></span>  
  
    1.  <span data-ttu-id="007c6-345">ISessionBoundFactory hizmet bir kanal oluşturun.</span><span class="sxs-lookup"><span data-stu-id="007c6-345">Create a channel to the ISessionBoundFactory service.</span></span>  
  
    2.  <span data-ttu-id="007c6-346">Bu kanal, bir EndpointAddress10 elde etmek için o hizmetini çağırmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="007c6-346">Use that channel to invoke that service to obtain an EndpointAddress10.</span></span>  
  
    3.  <span data-ttu-id="007c6-347">Bir süre sonuyla nesnesi elde etmek için bir kanal oluşturmak için EndpointAddress10 kullanın.</span><span class="sxs-lookup"><span data-stu-id="007c6-347">Use the EndpointAddress10 to create a channel to obtain a sessionful object.</span></span>  
  
    4.  <span data-ttu-id="007c6-348">Aynı örneği arasında birden fazla çağrı kalır göstermek için süre sonuyla nesnesi ile etkileşim.</span><span class="sxs-lookup"><span data-stu-id="007c6-348">Interact with the sessionful object to demonstrate it remains the same instance across multiple calls.</span></span>  
  
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
  
 <span data-ttu-id="007c6-349">WCF, nesneler her zaman değeri döndürür. ancak başvuru tarafından semantiği EndpointAddress10 kullanımı ile denk desteklemek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="007c6-349">WCF always returns objects by value, but it is possible to support the equivalent of by-reference semantics through the use of EndpointAddress10.</span></span> <span data-ttu-id="007c6-350">Bu daha sonra onu ile herhangi bir WCF hizmeti gibi etkileşim kurabilen bir süre sonuyla WCF hizmet örneği istemesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="007c6-350">This permits the client to request a sessionful WCF service instance, after which it can interact with it like any other WCF service.</span></span>  
  
#### <a name="scenario-3-client-sends-server-a-by-value-instance"></a><span data-ttu-id="007c6-351">Senaryo 3: Sunucu istemcisi, bir değer tarafından örneği gönderir.</span><span class="sxs-lookup"><span data-stu-id="007c6-351">Scenario 3: Client Sends Server a By-Value Instance</span></span>  
 <span data-ttu-id="007c6-352">Bu senaryo, temel olmayan nesne örneği sunucuya değeriyle gönderme istemci gösterir.</span><span class="sxs-lookup"><span data-stu-id="007c6-352">This scenario demonstrates the client sending a non-primitive object instance to the server by value.</span></span> <span data-ttu-id="007c6-353">WCF değeriyle yalnızca nesneleri gönderdiğinden, bu senaryo normal WCF kullanım gösterir.</span><span class="sxs-lookup"><span data-stu-id="007c6-353">Because WCF only sends objects by value, this scenario demonstrates normal WCF usage.</span></span>  
  
1.  <span data-ttu-id="007c6-354">Senaryo 1 aynı WCF hizmetinden kullanın.</span><span class="sxs-lookup"><span data-stu-id="007c6-354">Use the same WCF Service from Scenario 1.</span></span>  
  
2.  <span data-ttu-id="007c6-355">Yeni bir değer tarafından nesnesi (müşteri) oluşturmak, ICustomerService hizmetiyle iletişim kurmak için bir kanal oluşturmak ve nesne göndermek için istemci kullanın.</span><span class="sxs-lookup"><span data-stu-id="007c6-355">Use the client to create a new by-value object (Customer), create a channel to communicate with the ICustomerService service, and send the object to it.</span></span>  
  
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
   Console.WriteLine(String.Format("  Server returned {0}.", success));  
   ```  
  
     <span data-ttu-id="007c6-356">Müşteri nesnesi seri hale getirilmiş ve burada söz konusu nesne yeni bir kopyasını serisi ve sunucuya gönderilen.</span><span class="sxs-lookup"><span data-stu-id="007c6-356">The customer object will be serialized, and sent to the server, where it is deserialized into a new copy of that object.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="007c6-357">Bu kod ayrıca türetilmiş bir tür (PremiumCustomer) gönderme gösterir.</span><span class="sxs-lookup"><span data-stu-id="007c6-357">This code also illustrates sending a derived type (PremiumCustomer).</span></span> <span data-ttu-id="007c6-358">Hizmet arabirimi müşteri nesnesi bekliyor, ancak müşteri sınıfı [KnownType] öznitelikte PremiumCustomer de izin gösterilir.</span><span class="sxs-lookup"><span data-stu-id="007c6-358">The service interface expects a Customer object, but the [KnownType] attribute on the Customer class indicated PremiumCustomer was also allowed.</span></span> <span data-ttu-id="007c6-359">WCF serileştirmek veya bu hizmeti arabirimi aracılığıyla herhangi bir türü seri durumdan girişimleri başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="007c6-359">WCF will fail any attempt to serialize or deserialize any other type through this service interface.</span></span>  
  
 <span data-ttu-id="007c6-360">Normal WCF alışverişleri veri tarafından değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="007c6-360">Normal WCF exchanges of data are by value.</span></span> <span data-ttu-id="007c6-361">Bu garanti altına alır. Bu veri nesneleri birinde yöntemlerini çağırma, yalnızca yerel olarak yürütür – kod bir katman çağırma kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="007c6-361">This guarantees that invoking methods on one of these data objects executes only locally – it will not invoke code on the other tier.</span></span> <span data-ttu-id="007c6-362">Başvuru tarafından döndürülen nesne gibi bir şey elde etmek mümkün olmakla birlikte *gelen* sunucu tarafından başvuru nesnesi geçirmek için bir istemci yoktur *için* sunucu.</span><span class="sxs-lookup"><span data-stu-id="007c6-362">While it is possible to achieve something like by-reference objects returned *from* the server, it is not possible for a client to pass a by-reference object *to* the server.</span></span> <span data-ttu-id="007c6-363">İstemci ve sunucu arasında geri ve ileri bir konuşma gerektiren bir senaryo çift yönlü hizmetini kullanarak WCF'de elde edilebilir.</span><span class="sxs-lookup"><span data-stu-id="007c6-363">A scenario that requires a conversation back and forth between client and server can be achieved in WCF using a duplex service.</span></span> <span data-ttu-id="007c6-364">Daha fazla bilgi için bkz: [çift yönlü Hizmetler](./feature-details/duplex-services.md).</span><span class="sxs-lookup"><span data-stu-id="007c6-364">For more information, see [Duplex Services](./feature-details/duplex-services.md).</span></span>  
  
## <a name="summary"></a><span data-ttu-id="007c6-365">Özet</span><span class="sxs-lookup"><span data-stu-id="007c6-365">Summary</span></span>  
 <span data-ttu-id="007c6-366">.NET uzaktan iletişim, yalnızca tam güvenilir ortamlarında kullanılmak üzere bir iletişim çerçevedir.</span><span class="sxs-lookup"><span data-stu-id="007c6-366">.NET Remoting is a communication framework intended to be used only within fully-trusted environments.</span></span> <span data-ttu-id="007c6-367">Eski bir üründür ve yalnızca geriye dönük uyumluluk için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="007c6-367">It is a legacy product and supported only for backward compatibility.</span></span> <span data-ttu-id="007c6-368">Yeni uygulama oluşturmak için kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="007c6-368">It should not be used to build new applications.</span></span> <span data-ttu-id="007c6-369">Buna karşılık, WCF göz önünde bulundurularak ile tasarlanmıştır ve yeni ve mevcut uygulamalar için önerilir.</span><span class="sxs-lookup"><span data-stu-id="007c6-369">Conversely, WCF was designed with security in mind and is recommended for new and existing applications.</span></span> <span data-ttu-id="007c6-370">Microsoft, varolan önerir uzaktan iletişim uygulamalarını geçirilirken WCF veya ASP.NET Web API kullanın.</span><span class="sxs-lookup"><span data-stu-id="007c6-370">Microsoft recommends that existing Remoting applications be migrated to use WCF or ASP.NET Web API instead.</span></span>