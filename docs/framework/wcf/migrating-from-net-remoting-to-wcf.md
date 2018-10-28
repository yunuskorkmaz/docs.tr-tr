---
title: .NET Uzaktan İletişimden WCF'ye Taşınma
ms.date: 03/30/2017
ms.assetid: 16902a42-ef80-40e9-8c4c-90e61ddfdfe5
ms.openlocfilehash: 91cbfa33c6645fbc0a8d9b513e3a59799114a710
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50039601"
---
# <a name="migrating-from-net-remoting-to-wcf"></a><span data-ttu-id="690e6-102">.NET Uzaktan İletişimden WCF'ye Taşınma</span><span class="sxs-lookup"><span data-stu-id="690e6-102">Migrating from .NET Remoting to WCF</span></span>
<span data-ttu-id="690e6-103">Bu makalede, Windows Communication Foundation (WCF) kullanmak için .NET uzaktan iletişim kullanan bir uygulamayı geçirmek açıklar.</span><span class="sxs-lookup"><span data-stu-id="690e6-103">This article describes how to migrate an application that uses .NET Remoting to use Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="690e6-104">Bu ürünler arasındaki benzer kavramları karşılaştırır ve ardından WCF birkaç ortak uzaktan iletişim senaryolarında nasıl yapılacağını anlatmaktadır.</span><span class="sxs-lookup"><span data-stu-id="690e6-104">It compares similar concepts between these products and then describes how to accomplish several common Remoting scenarios in WCF.</span></span>  
  
 <span data-ttu-id="690e6-105">.NET uzaktan iletişim yalnızca geriye dönük uyumluluk için desteklenmeyen eski bir üründür.</span><span class="sxs-lookup"><span data-stu-id="690e6-105">.NET Remoting is a legacy product that is supported only for backward compatibility.</span></span> <span data-ttu-id="690e6-106">İstemci ve sunucu arasında ayrı güven düzeyleri koruyamadığını çünkü karma güven ortamlar genelinde güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="690e6-106">It is not secure across mixed-trust environments because it cannot maintain the separate trust levels between client and server.</span></span> <span data-ttu-id="690e6-107">Örneğin, bir .NET uzaktan iletişim uç noktası internet veya güvenilmeyen istemcilere hiçbir zaman sunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="690e6-107">For example, you should never expose a .NET Remoting endpoint to the Internet or to untrusted clients.</span></span> <span data-ttu-id="690e6-108">Varolan uzaktan iletişim öneririz uygulamalar için daha yeni ve daha güvenli teknolojiler geçişi.</span><span class="sxs-lookup"><span data-stu-id="690e6-108">We recommend existing Remoting applications be migrated to newer and more secure technologies.</span></span> <span data-ttu-id="690e6-109">Uygulama tasarımının yalnızca HTTP kullanan RESTful ise, ASP.NET Web API öneririz.</span><span class="sxs-lookup"><span data-stu-id="690e6-109">If the application’s design uses only HTTP and is RESTful, we recommend ASP.NET Web API.</span></span> <span data-ttu-id="690e6-110">Daha fazla bilgi için bkz: ASP.NET Web API.</span><span class="sxs-lookup"><span data-stu-id="690e6-110">For more information, see ASP.NET Web API.</span></span> <span data-ttu-id="690e6-111">Uygulama üzerinde SOAP tabanlı ya da Http olmayan protokolleri TCP gibi gerektirir, WCF öneririz.</span><span class="sxs-lookup"><span data-stu-id="690e6-111">If the application is based on SOAP or requires non-Http protocols such as TCP, we recommend WCF.</span></span>  

## <a name="comparing-net-remoting-to-wcf"></a><span data-ttu-id="690e6-112">.NET uzaktan iletişim için WCF ile karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="690e6-112">Comparing .NET Remoting to WCF</span></span>  
 <span data-ttu-id="690e6-113">Bu bölüm .NET uzaktan iletişim temel yapı taşlarını WCF eşdeğerleri ile karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="690e6-113">This section compares the basic building blocks of .NET Remoting with their WCF equivalents.</span></span> <span data-ttu-id="690e6-114">Bu yapı taşlarını daha sonra bazı istemci-sunucu senaryoları WCF'de oluşturmak için kullanacağız. Aşağıdaki grafikte, ana arasındaki benzerlikleri ve farkları .NET uzaktan iletişim ve WCF özetler.</span><span class="sxs-lookup"><span data-stu-id="690e6-114">We will use these building blocks later to create some common client-server scenarios in WCF.The following chart summarizes the main similarities and differences between .NET Remoting and WCF.</span></span>  
  
||<span data-ttu-id="690e6-115">.NET uzaktan iletişim</span><span class="sxs-lookup"><span data-stu-id="690e6-115">.NET Remoting</span></span>|<span data-ttu-id="690e6-116">WCF</span><span class="sxs-lookup"><span data-stu-id="690e6-116">WCF</span></span>|  
|-|-------------------|---------|  
|<span data-ttu-id="690e6-117">Sunucu türü</span><span class="sxs-lookup"><span data-stu-id="690e6-117">Server type</span></span>|<span data-ttu-id="690e6-118">Subclass MarshalByRefObject</span><span class="sxs-lookup"><span data-stu-id="690e6-118">Subclass MarshalByRefObject</span></span>|<span data-ttu-id="690e6-119">[ServiceContract] özniteliği ile işaretleyin</span><span class="sxs-lookup"><span data-stu-id="690e6-119">Mark with [ServiceContract] attribute</span></span>|  
|<span data-ttu-id="690e6-120">Hizmet işlemleri</span><span class="sxs-lookup"><span data-stu-id="690e6-120">Service operations</span></span>|<span data-ttu-id="690e6-121">Sunucu türü genel yöntemleri</span><span class="sxs-lookup"><span data-stu-id="690e6-121">Public methods on server type</span></span>|<span data-ttu-id="690e6-122">[OperationContract] özniteliği ile işaretleyin</span><span class="sxs-lookup"><span data-stu-id="690e6-122">Mark with [OperationContract] attribute</span></span>|  
|<span data-ttu-id="690e6-123">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="690e6-123">Serialization</span></span>|<span data-ttu-id="690e6-124">ISerializable veya [Serializable]</span><span class="sxs-lookup"><span data-stu-id="690e6-124">ISerializable or [Serializable]</span></span>|<span data-ttu-id="690e6-125">DataContractSerializer veya XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="690e6-125">DataContractSerializer or XmlSerializer</span></span>|  
|<span data-ttu-id="690e6-126">Geçirilen nesneleri</span><span class="sxs-lookup"><span data-stu-id="690e6-126">Objects passed</span></span>|<span data-ttu-id="690e6-127">Değere göre veya başvuruya göre</span><span class="sxs-lookup"><span data-stu-id="690e6-127">By-value or by-reference</span></span>|<span data-ttu-id="690e6-128">Değere göre yalnızca</span><span class="sxs-lookup"><span data-stu-id="690e6-128">By-value only</span></span>|  
|<span data-ttu-id="690e6-129">Hataları/özel durumları</span><span class="sxs-lookup"><span data-stu-id="690e6-129">Errors/exceptions</span></span>|<span data-ttu-id="690e6-130">Herhangi bir seri hale getirilebilir özel durumu</span><span class="sxs-lookup"><span data-stu-id="690e6-130">Any serializable exception</span></span>|<span data-ttu-id="690e6-131">FaultContract\<TDetail ></span><span class="sxs-lookup"><span data-stu-id="690e6-131">FaultContract\<TDetail></span></span>|  
|<span data-ttu-id="690e6-132">İstemci proxy nesneleri</span><span class="sxs-lookup"><span data-stu-id="690e6-132">Client proxy objects</span></span>|<span data-ttu-id="690e6-133">Kesin türü belirtilmiş saydam proxy'lerin bulunan MarshalByRefObjects için otomatik olarak oluşturulur</span><span class="sxs-lookup"><span data-stu-id="690e6-133">Strongly typed transparent proxies are created automatically from MarshalByRefObjects</span></span>|<span data-ttu-id="690e6-134">Kesin türü belirtilmiş bir proxy oluşturulur üzerine ChannelFactory kullanarak\<TChannel ></span><span class="sxs-lookup"><span data-stu-id="690e6-134">Strongly typed proxies are generated on-demand using ChannelFactory\<TChannel></span></span>|  
|<span data-ttu-id="690e6-135">Gereken platformu</span><span class="sxs-lookup"><span data-stu-id="690e6-135">Platform required</span></span>|<span data-ttu-id="690e6-136">Microsoft OS hem .NET hem istemci hem de sunucu kullanmanız gerekir</span><span class="sxs-lookup"><span data-stu-id="690e6-136">Both client and server must use Microsoft OS and .NET</span></span>|<span data-ttu-id="690e6-137">Platformlar arası</span><span class="sxs-lookup"><span data-stu-id="690e6-137">Cross-platform</span></span>|  
|<span data-ttu-id="690e6-138">İleti biçimi</span><span class="sxs-lookup"><span data-stu-id="690e6-138">Message format</span></span>|<span data-ttu-id="690e6-139">Özel</span><span class="sxs-lookup"><span data-stu-id="690e6-139">Private</span></span>|<span data-ttu-id="690e6-140">Endüstri standartları (SOAP, WS-\*, vb..)</span><span class="sxs-lookup"><span data-stu-id="690e6-140">Industry standards (SOAP, WS-\*, etc.)</span></span>|  
  
### <a name="server-implementation-comparison"></a><span data-ttu-id="690e6-141">Sunucu uygulaması karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="690e6-141">Server Implementation Comparison</span></span>  
  
#### <a name="creating-a-server-in-net-remoting"></a><span data-ttu-id="690e6-142">.NET uzaktan iletişim'de bir sunucu oluşturma</span><span class="sxs-lookup"><span data-stu-id="690e6-142">Creating a Server in .NET Remoting</span></span>  
 <span data-ttu-id="690e6-143">.NET uzaktan iletişim sunucu türleri, MarshalByRefObject öğesinden türetilir ve istemci, aşağıdaki gibi çağırabileceğiniz yöntemler tanımlayın:</span><span class="sxs-lookup"><span data-stu-id="690e6-143">.NET Remoting server types must derive from MarshalByRefObject and define methods the client can call, like the following:</span></span>  
  
```csharp
public class RemotingServer : MarshalByRefObject  
{  
    public Customer GetCustomer(int customerId) { … }  
}  
```  
  
 <span data-ttu-id="690e6-144">Bu sunucu türü genel yöntemleri genel sözleşmenin istemciler için kullanılabilir hale gelir.</span><span class="sxs-lookup"><span data-stu-id="690e6-144">The public methods of this server type become the public contract available to clients.</span></span>  <span data-ttu-id="690e6-145">Sunucunun ortak arabirim ve uygulaması arasında hiçbir ayrım yoktur: bir tür hem de işler.</span><span class="sxs-lookup"><span data-stu-id="690e6-145">There is no separation between the server’s public interface and its implementation – one type handles both.</span></span>  
  
 <span data-ttu-id="690e6-146">Sunucu türü tanımlandıktan sonra istemciler için kullanılabilir aşağıdaki örnekte ister:</span><span class="sxs-lookup"><span data-stu-id="690e6-146">Once the server type has been defined, it can be made available to clients, like in the following example:</span></span>  
  
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
  
 <span data-ttu-id="690e6-147">Uzaktan iletişim türünü yapılandırma dosyalarını kullanarak da dahil, bir sunucu olarak kullanılabilir hale getirmek için birçok yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="690e6-147">There are many ways to make the Remoting type available as a server, including using configuration files.</span></span> <span data-ttu-id="690e6-148">Bu yalnızca bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="690e6-148">This is just one example.</span></span>  
  
#### <a name="creating-a-server-in-wcf"></a><span data-ttu-id="690e6-149">WCF'de bir sunucu oluşturma</span><span class="sxs-lookup"><span data-stu-id="690e6-149">Creating a Server in WCF</span></span>  
 <span data-ttu-id="690e6-150">WCF eşdeğer adımda, iki tür--' % s'genel "hizmet sözleşmesi" ve somut uygulama oluşturmayı içerir.</span><span class="sxs-lookup"><span data-stu-id="690e6-150">The equivalent step in WCF involves creating two types -- the public "service contract" and the concrete implementation.</span></span> <span data-ttu-id="690e6-151">İlk [ServiceContract] ile işaretli bir arabirim olarak bildirilir.</span><span class="sxs-lookup"><span data-stu-id="690e6-151">The first is declared as an interface marked with [ServiceContract].</span></span> <span data-ttu-id="690e6-152">İstemciler için kullanılabilir olan yöntemler [OperationContract] ile işaretli:</span><span class="sxs-lookup"><span data-stu-id="690e6-152">Methods available to clients are marked with [OperationContract]:</span></span>  
  
```csharp
[ServiceContract]  
public interface IWCFServer  
{  
    [OperationContract]  
    Customer GetCustomer(int customerId);  
}  
```  
  
 <span data-ttu-id="690e6-153">Sunucu uygulaması aşağıdaki örnekte gibi ayrı bir somut sınıf tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="690e6-153">The server’s implementation is defined in a separate concrete class, like in the following example:</span></span>  
  
```csharp
public class WCFServer : IWCFServer  
{  
    public Customer GetCustomer(int customerId) { … }  
}  
```  
  
 <span data-ttu-id="690e6-154">Bu tür tanımladıktan sonra WCF sunucunun istemciler için kullanılabilir hale getirilebilir aşağıdaki örnekte ister:</span><span class="sxs-lookup"><span data-stu-id="690e6-154">Once these types have been defined, the WCF server can be made available to clients, like in the following example:</span></span>  
  
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
>  <span data-ttu-id="690e6-155">TCP örneklerin her ikisi de bunları mümkün olduğu kadar benzer tutmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="690e6-155">TCP is used in both examples to keep them as similar as possible.</span></span> <span data-ttu-id="690e6-156">HTTP kullanan örnekler için bu konunun ilerleyen bölümlerinde senaryo kılavuzlarına bakın.</span><span class="sxs-lookup"><span data-stu-id="690e6-156">Refer to the scenario walk-throughs later in this topic for examples using HTTP.</span></span>  
  
 <span data-ttu-id="690e6-157">Yapılandırmak için birçok yolu vardır ve WCF hizmetlerini barındırmak için.</span><span class="sxs-lookup"><span data-stu-id="690e6-157">There are many ways to configure and to host WCF services.</span></span> <span data-ttu-id="690e6-158">"Kendini" bilinen tek bir örnek budur.</span><span class="sxs-lookup"><span data-stu-id="690e6-158">This is just one example, known as "self-hosted".</span></span> <span data-ttu-id="690e6-159">Daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="690e6-159">For more information, see the following topics:</span></span>  
  
-   [<span data-ttu-id="690e6-160">Nasıl yapılır: Bir Hizmet Anlaşması Tanımlama</span><span class="sxs-lookup"><span data-stu-id="690e6-160">How to: Define a Service Contract</span></span>](how-to-define-a-wcf-service-contract.md)  
  
-   [<span data-ttu-id="690e6-161">Yapılandırma Dosyalarını Kullanarak Hizmetleri Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="690e6-161">Configuring Services Using Configuration Files</span></span>](configuring-services-using-configuration-files.md)  
  
-   [<span data-ttu-id="690e6-162">Barındırma Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="690e6-162">Hosting Services</span></span>](hosting-services.md)  
  
### <a name="client-implementation-comparison"></a><span data-ttu-id="690e6-163">İstemci uygulaması karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="690e6-163">Client Implementation Comparison</span></span>  
  
#### <a name="creating-a-client-in-net-remoting"></a><span data-ttu-id="690e6-164">.NET uzaktan iletişim'de bir istemci oluşturma</span><span class="sxs-lookup"><span data-stu-id="690e6-164">Creating a Client in .NET Remoting</span></span>  
 <span data-ttu-id="690e6-165">Bir .NET uzaktan iletişim sunucu nesnesi kullanılabilir yapıldıktan sonra bu istemciler tarafından gibi aşağıdaki örnekte tarafından kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="690e6-165">Once a .NET Remoting server object has been made available, it can be consumed by clients, like in the following example:</span></span>  
  
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
  
 <span data-ttu-id="690e6-166">Activator.GetObject() döndürülen RemotingServer örneği bilinen bir "saydam Ara sunucusu olarak."</span><span class="sxs-lookup"><span data-stu-id="690e6-166">The RemotingServer instance returned from Activator.GetObject() is known as a "transparent proxy."</span></span> <span data-ttu-id="690e6-167">İstemcide RemotingServer türü için genel API uygular, ancak farklı bir işlem veya makine çalışan sunucu nesnesi tüm yöntemleri çağırın.</span><span class="sxs-lookup"><span data-stu-id="690e6-167">It implements the public API for the RemotingServer type on the client, but all the methods call the server object running in a different process or machine.</span></span>  
  
#### <a name="creating-a-client-in-wcf"></a><span data-ttu-id="690e6-168">WCF'de bir istemci oluşturma</span><span class="sxs-lookup"><span data-stu-id="690e6-168">Creating a Client in WCF</span></span>  
 <span data-ttu-id="690e6-169">Proxy açıkça oluşturmak için bir kanal fabrikası kullanarak WCF eşdeğer adım içerir.</span><span class="sxs-lookup"><span data-stu-id="690e6-169">The equivalent step in WCF involves using a channel factory to create the proxy explicitly.</span></span> <span data-ttu-id="690e6-170">Proxy nesnesi gibi uzaktan iletişim, aşağıdaki örnekte sunucu üzerindeki işlemler gibi çağırmak için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="690e6-170">Like Remoting, the proxy object can be used to invoke operations on the server, like in the following example:</span></span>  
  
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
  
 <span data-ttu-id="690e6-171">Bu örnekte, en çok uzak örneğe benzer olduğundan kanal düzeyinde programlama gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="690e6-171">This example shows programming at the channel level because it is most similar to the Remoting example.</span></span> <span data-ttu-id="690e6-172">Ayrıca kullanılabilir **hizmet Başvurusu Ekle** yaklaşım Visual Studio'da, istemci programlama basitleştirmek için kod oluşturur.</span><span class="sxs-lookup"><span data-stu-id="690e6-172">Also available is the **Add Service Reference** approach in Visual Studio that generates code to simplify client programming.</span></span> <span data-ttu-id="690e6-173">Daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="690e6-173">For more information, see the following topics:</span></span>  
  
-   [<span data-ttu-id="690e6-174">İstemci Kanal Düzeyi Programlama</span><span class="sxs-lookup"><span data-stu-id="690e6-174">Client Channel-Level Programming</span></span>](./extending/client-channel-level-programming.md)  
  
-   [<span data-ttu-id="690e6-175">Nasıl yapılır: ekleme, güncelleştirme veya hizmet başvurusunu Kaldır</span><span class="sxs-lookup"><span data-stu-id="690e6-175">How to: Add, Update, or Remove a Service Reference</span></span>](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference)  
  
### <a name="serialization-usage"></a><span data-ttu-id="690e6-176">Serileştirme kullanım</span><span class="sxs-lookup"><span data-stu-id="690e6-176">Serialization Usage</span></span>  
 <span data-ttu-id="690e6-177">.NET uzaktan iletişim hem de WCF istemci ve sunucu arasında nesneleri göndermek için serileştirme kullanmak, ancak bunlar bu önemli bakımlardan ayrılır:</span><span class="sxs-lookup"><span data-stu-id="690e6-177">Both .NET Remoting and WCF use serialization to send objects between client and server, but they differ in these important ways:</span></span>  
  
1.  <span data-ttu-id="690e6-178">Bunlar farklı seri hale getiricileri genişletme ve kuralları seri hale getirmek ne belirtmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="690e6-178">They use different serializers and conventions to indicate what to serialize.</span></span>  
  
2.  <span data-ttu-id="690e6-179">.NET uzaktan iletişim güvenlik sınırları arasında olan diğer katmanındaki kod yürütmek için bir katmanda metot veya özellik erişimi sağlayan "başvuru tarafından" serileştirme destekler.</span><span class="sxs-lookup"><span data-stu-id="690e6-179">.NET Remoting supports "by reference" serialization that allows method or property access on one tier to execute code on the other tier, which is across security boundaries.</span></span> <span data-ttu-id="690e6-180">Bu özellik, güvenlik açıklarını ortaya çıkaran ve neden uzak uç noktaları asla güvenilmeyen istemcilere açılmamalıdır temel nedenlerinden biridir.</span><span class="sxs-lookup"><span data-stu-id="690e6-180">This capability exposes security vulnerabilities and is one of the main reasons why Remoting endpoints should never be exposed to untrusted clients.</span></span>  
  
3.  <span data-ttu-id="690e6-181">Uzaktan iletişim tarafından kullanılan seri hale getirme çevirme (seri hale getirmek için hangi değil açıkça hariç) ve WCF seri hale getirme kabul etme (seri hale getirmek için hangi üyelerin açıkça işaretleyin).</span><span class="sxs-lookup"><span data-stu-id="690e6-181">Serialization used by Remoting is opt-out (explicitly exclude what not to serialize) and WCF serialization is opt-in (explicitly mark which members to serialize).</span></span>  
  
#### <a name="serialization-in-net-remoting"></a><span data-ttu-id="690e6-182">.NET uzaktan iletişim serileştirme</span><span class="sxs-lookup"><span data-stu-id="690e6-182">Serialization in .NET Remoting</span></span>  
 <span data-ttu-id="690e6-183">.NET uzaktan iletişim, istemci ve sunucu arasında nesneleri seri hale getrime ve iki yolu destekler:</span><span class="sxs-lookup"><span data-stu-id="690e6-183">.NET Remoting supports two ways to serialize and deserialize objects between the client and server:</span></span>  
  
-   <span data-ttu-id="690e6-184">*Değere göre* : nesnenin değerleri katman sınırlarında serileştirilme şeklini ve o nesnenin yeni bir örneğini başka bir katmanında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="690e6-184">*By value* – the values of the object are serialized across tier boundaries, and a new instance of that object is created on the other tier.</span></span> <span data-ttu-id="690e6-185">Yöntemleri veya yeni bu örneğin özelliklerini yapılan her çağrı yalnızca yerel olarak yürütün ve özgün nesne veya katmanı etkilemez.</span><span class="sxs-lookup"><span data-stu-id="690e6-185">Any calls to methods or properties of that new instance execute only locally and do not affect the original object or tier.</span></span>  
  
-   <span data-ttu-id="690e6-186">*Başvuruya göre* – özel bir "nesne başvurusu" katman sınırlarında serileştirilmiş.</span><span class="sxs-lookup"><span data-stu-id="690e6-186">*By reference* – a special "object reference" is serialized across tier boundaries.</span></span> <span data-ttu-id="690e6-187">Yöntem ya da o nesnenin özellikleri ile bir katman etkileşim kurduğunda orijinal katman özgün nesneye geri iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="690e6-187">When one tier interacts with methods or properties of that object, it communicates back to the original object on the original tier.</span></span> <span data-ttu-id="690e6-188">Başvuruya göre nesneleri, her iki yönünde – sunucudan istemciye ya da istemciden sunucuya akabilir.</span><span class="sxs-lookup"><span data-stu-id="690e6-188">By-reference objects can flow in either direction – server to client, or client to server.</span></span>  
  
 <span data-ttu-id="690e6-189">Uzaktan iletişim tarafından değer türleri [Serializable] özniteliğiyle işaretlenmiş olduğundan veya ISerializable, aşağıdaki örnekte gibi uygulayın:</span><span class="sxs-lookup"><span data-stu-id="690e6-189">By-value types in Remoting are marked with the [Serializable] attribute or implement ISerializable, like in the following example:</span></span>  
  
```csharp
[Serializable]  
public class RemotingCustomer  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
    public int CustomerId { get; set; }  
}  
```  
  
 <span data-ttu-id="690e6-190">Başvuruya göre türleri MarshalByRefObject sınıfından, aşağıdaki örnekte gibi türetilir:</span><span class="sxs-lookup"><span data-stu-id="690e6-190">By-reference types derive from the MarshalByRefObject class, like in the following example:</span></span>  
  
```csharp
public class RemotingCustomerReference : MarshalByRefObject  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
    public int CustomerId { get; set; }  
}  
```  
  
 <span data-ttu-id="690e6-191">Uzaktan iletişimi'nın başvuruya göre nesnelerin etkilerini anlamak son derece önemlidir.</span><span class="sxs-lookup"><span data-stu-id="690e6-191">It is extremely important to understand the implications of Remoting’s by-reference objects.</span></span> <span data-ttu-id="690e6-192">Her iki katmanı (istemci veya sunucu) bir katman için bir başvuruya göre nesne gönderirse, tüm yöntem çağrıları geri nesnenin sahibi olan katmanında yürütün.</span><span class="sxs-lookup"><span data-stu-id="690e6-192">If either tier (client or server) sends a by-reference object to the other tier, all method calls execute back on the tier owning the object.</span></span> <span data-ttu-id="690e6-193">Örneğin, sunucu tarafından döndürülen bir başvuruya göre nesne üzerinde yöntemleri çağırmak bir istemci, sunucu üzerinde kod yürütülür.</span><span class="sxs-lookup"><span data-stu-id="690e6-193">For example, a client calling methods on a by-reference object returned by the server will execute code on the server.</span></span> <span data-ttu-id="690e6-194">Benzer şekilde, istemci tarafından sağlanan bir başvuruya göre nesne üzerinde yöntemleri çağırmak bir sunucu, istemci üzerinde kod yürütülür.</span><span class="sxs-lookup"><span data-stu-id="690e6-194">Similarly, a server calling methods on a by-reference object provided by the client will execute code back on the client.</span></span> <span data-ttu-id="690e6-195">Bu nedenle, sadece tam güvenilir ortamlar içinde .NET uzaktan iletişim kullanımı önerilir.</span><span class="sxs-lookup"><span data-stu-id="690e6-195">For this reason, the use of .NET Remoting is recommended only within fully-trusted environments.</span></span> <span data-ttu-id="690e6-196">Güvenilmeyen istemciler için genel bir .NET uzaktan iletişim uç noktayı kullanıma sunmayı bir uzak sunucu saldırılara açık hale getirir.</span><span class="sxs-lookup"><span data-stu-id="690e6-196">Exposing a public .NET Remoting endpoint to untrusted clients will make a Remoting server vulnerable to attack.</span></span>  
  
#### <a name="serialization-in-wcf"></a><span data-ttu-id="690e6-197">Wcf'de seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="690e6-197">Serialization in WCF</span></span>  
 <span data-ttu-id="690e6-198">WCF yalnızca değere göre serileştirme destekler.</span><span class="sxs-lookup"><span data-stu-id="690e6-198">WCF supports only by-value serialization.</span></span> <span data-ttu-id="690e6-199">Aşağıdaki örnekte istemci ve sunucu değişimi için bir tür tanımlamak için en yaygın yolu gibidir:</span><span class="sxs-lookup"><span data-stu-id="690e6-199">The most common way to define a type to exchange between client and server is like in the following example:</span></span>  
  
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
  
 <span data-ttu-id="690e6-200">[DataContract] özniteliği sıralanabilir ve istemci ile sunucu arasında seri durumdan bu türün biri olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="690e6-200">The [DataContract] attribute identifies this type as one that can be serialized and deserialized between client and server.</span></span> <span data-ttu-id="690e6-201">[DataMember] özniteliği, ayrı özellikler ve alanları serileştirmek için tanımlar.</span><span class="sxs-lookup"><span data-stu-id="690e6-201">The [DataMember] attribute identifies the individual properties or fields to serialize.</span></span>  
  
 <span data-ttu-id="690e6-202">WCF katmanlarda nesneyi gönderdiğinde, değerler yalnızca serileştirir ve diğer katmanında nesnesinin yeni bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="690e6-202">When WCF sends an object across tiers, it serializes only the values and creates a new instance of the object on the other tier.</span></span> <span data-ttu-id="690e6-203">Değerlerle tüm etkileşimler nesnesinin yalnızca yerel olarak – ortaya yolu .NET uzaktan iletişim başvuruya göre Nesneleri'ne diğer katmanla iletişim kurarlar değil.</span><span class="sxs-lookup"><span data-stu-id="690e6-203">Any interactions with the values of the object occur only locally – they do not communicate with the other tier the way .NET Remoting by-reference objects do.</span></span> <span data-ttu-id="690e6-204">Daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="690e6-204">For more information, see the following topics:</span></span>  
  
-   [<span data-ttu-id="690e6-205">Serileştirme ve Seri Durumdan Çıkarma</span><span class="sxs-lookup"><span data-stu-id="690e6-205">Serialization and Deserialization</span></span>](./feature-details/serialization-and-deserialization.md)  
  
-   [<span data-ttu-id="690e6-206">Windows Communication Foundation'da seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="690e6-206">Serialization in Windows Communication Foundation</span></span>](https://msdn.microsoft.com/magazine/cc163569.aspx)  
  
### <a name="exception-handling-capabilities"></a><span data-ttu-id="690e6-207">Özel durum işleme özellikleri</span><span class="sxs-lookup"><span data-stu-id="690e6-207">Exception Handling Capabilities</span></span>  
  
#### <a name="exceptions-in-net-remoting"></a><span data-ttu-id="690e6-208">.NET uzaktan iletişim özel durumları</span><span class="sxs-lookup"><span data-stu-id="690e6-208">Exceptions in .NET Remoting</span></span>  
 <span data-ttu-id="690e6-209">Bir uzak sunucu tarafından oluşturulan özel durumları istemciye gönderilen, serileştirilmiş ve gibi başka bir özel durum istemci üzerinde yerel olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="690e6-209">Exceptions thrown by a Remoting server are serialized, sent to the client, and thrown locally on the client like any other exception.</span></span> <span data-ttu-id="690e6-210">Özel durumları [Serializable] ile işaretlemeyi ve özel durum türü alt classing tarafından oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="690e6-210">Custom exceptions can be created by sub-classing the Exception type and marking it with [Serializable].</span></span>   <span data-ttu-id="690e6-211">Çoğu framework özel durumları zaten serileştirilmiş ve istemcide yeniden durum sunucusu tarafından oluşturulan çoğu izin vererek, bu şekilde işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="690e6-211">Most framework exceptions are already marked in this way, allowing most to be thrown by the server, serialized, and re-thrown on the client.</span></span> <span data-ttu-id="690e6-212">Bu tasarım geliştirme sırasında kullanışlı olsa da, sunucu tarafı bilgileri istemciye yanlışlıkla çıkarılabilecek.</span><span class="sxs-lookup"><span data-stu-id="690e6-212">Though this design is convenient during development, server-side information can inadvertently be disclosed to the client.</span></span> <span data-ttu-id="690e6-213">Bu, yalnızca tamamen güvenilen ortamlarda Remoting kullanılması gereken çok sayıda gerekçe biridir.</span><span class="sxs-lookup"><span data-stu-id="690e6-213">This is one of many reasons Remoting should be used only in fully-trusted environments.</span></span>  
  
#### <a name="exceptions-and-faults-in-wcf"></a><span data-ttu-id="690e6-214">Özel durum ve hataları wcf'de</span><span class="sxs-lookup"><span data-stu-id="690e6-214">Exceptions and Faults in WCF</span></span>  
 <span data-ttu-id="690e6-215">WCF rastgele bir özel durum türlerini bilgilerin yanlışlıkla açığa çıkmasına için sunucudan istemciye döndürülmesine izin vermez.</span><span class="sxs-lookup"><span data-stu-id="690e6-215">WCF does not allow arbitrary exception types to be returned from the server to the client because it could lead to inadvertent information disclosure.</span></span> <span data-ttu-id="690e6-216">Bir hizmet işlemi beklenmeyen bir özel durum oluşturursa, bir genel amaçlı FaultException istemcide harekete geçirilmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="690e6-216">If a service operation throws an unexpected exception, it causes a general purpose FaultException to be thrown on the client.</span></span> <span data-ttu-id="690e6-217">Bu durum, neden ya da burada bir hata oluştu ve bazı uygulamalar için bu yeterli herhangi bir bilgi içermez.</span><span class="sxs-lookup"><span data-stu-id="690e6-217">This exception does not carry any information why or where the problem occurred, and for some applications this is sufficient.</span></span> <span data-ttu-id="690e6-218">Gereken uygulamalar istemci yapmak için daha zengin hata bilgileri hatalı sözleşme tanımlayarak iletişim.</span><span class="sxs-lookup"><span data-stu-id="690e6-218">Applications that need to communicate richer error information to the client do this by defining a fault contract.</span></span>  
  
 <span data-ttu-id="690e6-219">Bunu yapmak için önce hata bilgilerini taşımak için [DataContract] türü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="690e6-219">To do this, first create a [DataContract] type to carry the fault information.</span></span>  
  
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
  
 <span data-ttu-id="690e6-220">Her hizmet işlemi için kullanılacak hatalı sözleşme belirtin.</span><span class="sxs-lookup"><span data-stu-id="690e6-220">Specify the fault contract to use for each service operation.</span></span>  
  
```csharp
[ServiceContract]  
public interface IWCFServer  
{  
    [OperationContract]  
    [FaultContract(typeof(CustomerServiceFault))]  
    Customer GetCustomer(int customerId);  
}  
```  
  
 <span data-ttu-id="690e6-221">Sunucu bir FaultException özel durum atma hata koşulları bildirir.</span><span class="sxs-lookup"><span data-stu-id="690e6-221">The server reports error conditions by throwing a FaultException.</span></span>  
  
```csharp
throw new FaultException<CustomerServiceFault>(  
    new CustomerServiceFault() {   
        CustomerId = customerId,   
        ErrorMessage = "Illegal customer Id"   
    });  
```  
  
 <span data-ttu-id="690e6-222">Ve istemci, sunucuya istek yaptığında, normal özel durumlar olarak hatalar yakalayabilir.</span><span class="sxs-lookup"><span data-stu-id="690e6-222">And whenever the client makes a request to the server, it can catch faults as normal exceptions.</span></span>  
  
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
  
 <span data-ttu-id="690e6-223">Hata sözleşmeleri hakkında daha fazla bilgi için bkz. <xref:System.ServiceModel.FaultException>.</span><span class="sxs-lookup"><span data-stu-id="690e6-223">For more information about fault contracts, see <xref:System.ServiceModel.FaultException>.</span></span>  
  
### <a name="security-considerations"></a><span data-ttu-id="690e6-224">Güvenlik Değerlendirmeleri</span><span class="sxs-lookup"><span data-stu-id="690e6-224">Security Considerations</span></span>  
  
#### <a name="security-in-net-remoting"></a><span data-ttu-id="690e6-225">.NET uzaktan iletişim güvenlik</span><span class="sxs-lookup"><span data-stu-id="690e6-225">Security in .NET Remoting</span></span>  
 <span data-ttu-id="690e6-226">Bazı .NET uzaktan iletişim kanalları, kimlik doğrulaması ve şifrelemeyi kanal katmanında (IPC ve TCP) gibi güvenlik özelliklerini destekler.</span><span class="sxs-lookup"><span data-stu-id="690e6-226">Some .NET Remoting channels support security features such as authentication and encryption at the channel layer (IPC and TCP).</span></span> <span data-ttu-id="690e6-227">HTTP kanalı, kimlik doğrulama ve şifreleme için Internet Information Services (IIS) kullanır.</span><span class="sxs-lookup"><span data-stu-id="690e6-227">The HTTP channel relies on Internet Information Services (IIS) for both authentication and encryption.</span></span> <span data-ttu-id="690e6-228">Bu destek rağmen bir güvenli olmayan bir iletişim protokolü .NET uzaktan iletişim göz önünde bulundurun ve sadece tam güvenilir ortamlar içinde kullanın.</span><span class="sxs-lookup"><span data-stu-id="690e6-228">Despite this support, you should consider .NET Remoting an unsecure communication protocol and use it only within fully-trusted environments.</span></span> <span data-ttu-id="690e6-229">Hiçbir zaman Internet veya güvenilmeyen istemciler için genel bir uzak uç nokta kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="690e6-229">Never expose a public Remoting endpoint to the Internet or untrusted clients.</span></span>  
  
#### <a name="security-in-wcf"></a><span data-ttu-id="690e6-230">WCF'de Güvenlik</span><span class="sxs-lookup"><span data-stu-id="690e6-230">Security in WCF</span></span>  
 <span data-ttu-id="690e6-231">WCF ile göz önünde bulundurularak, kısmen türlerini .NET uzaktan iletişim'de bulunan güvenlik açıklarına yönelik olarak tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="690e6-231">WCF was designed with security in mind, in part to address the kinds of vulnerabilities found in .NET Remoting.</span></span> <span data-ttu-id="690e6-232">WCF güvenlik hem aktarım hem de ileti düzeyinde sunar ve kimlik doğrulama, yetkilendirme, şifreleme ve benzeri pek çok seçenek sunar.</span><span class="sxs-lookup"><span data-stu-id="690e6-232">WCF offers security at both the transport and message level, and offers many options for authentication, authorization, encryption, and so on.</span></span> <span data-ttu-id="690e6-233">Daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="690e6-233">For more information, see the following topics:</span></span>  
  
-   [<span data-ttu-id="690e6-234">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="690e6-234">Security</span></span>](./feature-details/security.md)  
  
-   [<span data-ttu-id="690e6-235">WCF Güvenlik Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="690e6-235">WCF Security Guidance</span></span>](./feature-details/security-guidance-and-best-practices.md)  
  
## <a name="migrating-to-wcf"></a><span data-ttu-id="690e6-236">WCF'ye taşınma</span><span class="sxs-lookup"><span data-stu-id="690e6-236">Migrating to WCF</span></span>  
  
### <a name="why-migrate-from-remoting-to-wcf"></a><span data-ttu-id="690e6-237">Neden uzaktan iletişimden WCF'ye geçirme?</span><span class="sxs-lookup"><span data-stu-id="690e6-237">Why Migrate from Remoting to WCF?</span></span>  
  
-   <span data-ttu-id="690e6-238">**.NET uzaktan iletişim eski bir üründür.**</span><span class="sxs-lookup"><span data-stu-id="690e6-238">**.NET Remoting is a legacy product.**</span></span> <span data-ttu-id="690e6-239">Bölümünde anlatıldığı gibi [.NET uzaktan iletişim](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507%28v=vs.100%29), eski bir ürün olarak kabul edilir ve yeni geliştirme projeleri için önerilmez.</span><span class="sxs-lookup"><span data-stu-id="690e6-239">As described in [.NET Remoting](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507%28v=vs.100%29), it is considered a legacy product and is not recommended for new development.</span></span> <span data-ttu-id="690e6-240">WCF veya ASP.NET Web API yeni ve mevcut uygulamalar için önerilir.</span><span class="sxs-lookup"><span data-stu-id="690e6-240">WCF or ASP.NET Web API are recommended for new and existing applications.</span></span>  
  
-   <span data-ttu-id="690e6-241">**WCF platformlar arası standartlar kullanır.**</span><span class="sxs-lookup"><span data-stu-id="690e6-241">**WCF uses cross-platform standards.**</span></span> <span data-ttu-id="690e6-242">WCF ile platformlar arası birlikte çalışabilirlik düşünülerek tasarlanmıştır ve çoğu endüstri standartları destekler (SOAP, WS-Security, WS-Trust, vs.).</span><span class="sxs-lookup"><span data-stu-id="690e6-242">WCF was designed with cross-platform interoperability in mind and supports many industry standards (SOAP, WS-Security, WS-Trust, etc.).</span></span> <span data-ttu-id="690e6-243">Bir WCF hizmeti, Windows dışındaki işletim sistemleri üzerinde çalışan istemciler ile çalışabilirler.</span><span class="sxs-lookup"><span data-stu-id="690e6-243">A WCF service can interoperate with clients running on operating systems other than Windows.</span></span> <span data-ttu-id="690e6-244">Uzaktan iletişim, öncelikle bir Windows işletim sisteminde .NET framework kullanarak sunucu ve istemci uygulamaları çalıştırdığı ortamlar için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="690e6-244">Remoting was designed primarily for environments where both the server and client applications run using the .NET framework on a Windows operating system.</span></span>  
  
-   <span data-ttu-id="690e6-245">**WCF yerleşik güvenlik sahiptir.**</span><span class="sxs-lookup"><span data-stu-id="690e6-245">**WCF has built-in security.**</span></span> <span data-ttu-id="690e6-246">WCF güvenlik düşünülerek tasarlanmıştır ve kimlik doğrulaması, aktarım düzeyi güvenlik, ileti düzeyi güvenlik, vb. pek çok seçenek sunar. Uzaktan iletişim uygulamalarını çalışmak kolaylaştırmak için tasarlanmıştır ancak güvenilir olmayan ortamlarda güvenli olacak şekilde tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="690e6-246">WCF was designed with security in mind and offers many options for authentication, transport level security, message level security, etc. Remoting was designed to make it easy for applications to interoperate but was not designed to be secure in non-trusted environments.</span></span> <span data-ttu-id="690e6-247">WCF, güvenilir ve güvenilir olmayan ortamlarda çalışacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="690e6-247">WCF was designed to work in both trusted and non-trusted environments.</span></span>  
  
### <a name="migration-recommendations"></a><span data-ttu-id="690e6-248">Geçiş önerileri</span><span class="sxs-lookup"><span data-stu-id="690e6-248">Migration Recommendations</span></span>  
 <span data-ttu-id="690e6-249">.NET uzaktan iletişimden WCF'ye geçirme önerilen adımlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="690e6-249">The following are the recommended steps to migrate from .NET Remoting to WCF:</span></span>  
  
-   <span data-ttu-id="690e6-250">**Hizmet sözleşmesi oluşturun.**</span><span class="sxs-lookup"><span data-stu-id="690e6-250">**Create the service contract.**</span></span> <span data-ttu-id="690e6-251">Hizmet arabirimi türlerinizi tanımlamak ve bunları [ServiceContract] özniteliği ile işaretleyin. İstemciler [OperationContract] ile çağırmak için izin verilecek tüm yöntemleri işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="690e6-251">Define your service interface types, and mark them with the [ServiceContract] attribute.Mark all the methods the clients will be allowed to call with [OperationContract].</span></span>  
  
-   <span data-ttu-id="690e6-252">**Veri sözleşmesi oluşturun.**</span><span class="sxs-lookup"><span data-stu-id="690e6-252">**Create the data contract.**</span></span> <span data-ttu-id="690e6-253">Sunucu ve istemci arasında değiş tokuş ve bunları [DataContract] özniteliği ile işaretleyin veri türlerini tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="690e6-253">Define the data types that will be exchanged between server and client, and mark them with the [DataContract] attribute.</span></span> <span data-ttu-id="690e6-254">Bir istemci kullanın [DataMember] ile izin verilecek tüm alanlar ve Özellikler'i işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="690e6-254">Mark all the fields and properties the client will be allowed to use with [DataMember].</span></span>  
  
-   <span data-ttu-id="690e6-255">**Hatalı sözleşme oluşturma (isteğe bağlı).**</span><span class="sxs-lookup"><span data-stu-id="690e6-255">**Create the fault contract (optional).**</span></span> <span data-ttu-id="690e6-256">Hatalarla karşılaştı, sunucu ve istemci arasında alınıp türleri oluşturun.</span><span class="sxs-lookup"><span data-stu-id="690e6-256">Create the types that will be exchanged between server and client when errors are encountered.</span></span> <span data-ttu-id="690e6-257">Bu türler ile [DataContract] ve [DataMember] serileştirilebilir hale getirmek için bu seçeneği işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="690e6-257">Mark these types with [DataContract] and [DataMember] to make them serializable.</span></span> <span data-ttu-id="690e6-258">Bunları [OperationContract] ile işaretli tüm hizmet işlemleri için de [döndürme olasılığı hangi hatalarını belirtmek için FaultContract] ile işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="690e6-258">For all service operations you marked with [OperationContract], also mark them with [FaultContract] to indicate which errors they may return.</span></span>  
  
-   <span data-ttu-id="690e6-259">**Yapılandırma ve hizmet barındırın.**</span><span class="sxs-lookup"><span data-stu-id="690e6-259">**Configure and host the service.**</span></span> <span data-ttu-id="690e6-260">Hizmet sözleşmesi oluşturulduktan sonra sonraki adım bir uç nokta adresindeki hizmet kullanıma sunmak için bir bağlama yapılandırmaktır.</span><span class="sxs-lookup"><span data-stu-id="690e6-260">Once the service contract has been created, the next step is to configure a binding to expose the service at an endpoint.</span></span> <span data-ttu-id="690e6-261">Daha fazla bilgi için [uç noktalar: adresler, bağlamalar ve sözleşmeleri](./feature-details/endpoints-addresses-bindings-and-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="690e6-261">For more information, see [Endpoints: Addresses, Bindings, and Contracts](./feature-details/endpoints-addresses-bindings-and-contracts.md).</span></span>  
  
 <span data-ttu-id="690e6-262">Bir uzaktan uygulama WCF'ye geçirilmiş olan sonra .NET uzaktan iletişim bağımlılıkları kaldırın yine de önemlidir.</span><span class="sxs-lookup"><span data-stu-id="690e6-262">Once a Remoting application has been migrated to WCF, it is still important to remove dependencies on .NET Remoting.</span></span> <span data-ttu-id="690e6-263">Bu, herhangi bir uzaktan iletişim açığını uygulamadan kaldırılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="690e6-263">This ensures that any Remoting vulnerabilities are removed from the application.</span></span> <span data-ttu-id="690e6-264">Bu adımlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="690e6-264">These steps include the following:</span></span>  
  
-   <span data-ttu-id="690e6-265">**MarshalByRefObject bırakmaktır.**</span><span class="sxs-lookup"><span data-stu-id="690e6-265">**Discontinue use of MarshalByRefObject.**</span></span> <span data-ttu-id="690e6-266">MarshalByRefObject türü, yalnızca uzaktan iletişim için bulunmaktadır ve WCF tarafından kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="690e6-266">The MarshalByRefObject type exists only for Remoting and is not used by WCF.</span></span> <span data-ttu-id="690e6-267">MarshalByRefObject alt sınıf herhangi bir uygulama türünün kaldırılan veya değiştirilen.</span><span class="sxs-lookup"><span data-stu-id="690e6-267">Any application types that sub-class MarshalByRefObject should be removed or changed.</span></span> <span data-ttu-id="690e6-268">MarshalByRefObject türü, yalnızca uzaktan iletişim için bulunmaktadır ve WCF tarafından kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="690e6-268">The MarshalByRefObject type exists only for Remoting and is not used by WCF.</span></span> <span data-ttu-id="690e6-269">MarshalByRefObject alt sınıf herhangi bir uygulama türünün kaldırılan veya değiştirilen.</span><span class="sxs-lookup"><span data-stu-id="690e6-269">Any application types that sub-class MarshalByRefObject should be removed or changed.</span></span>  
  
-   <span data-ttu-id="690e6-270">**[Serializable] kullanımı ve ISerializable bırakmaktır.**</span><span class="sxs-lookup"><span data-stu-id="690e6-270">**Discontinue use of [Serializable] and ISerializable.**</span></span> <span data-ttu-id="690e6-271">[Serializable] özniteliği ve ISerializable arabirimini başlangıçta güvenilir ortamlar içinde türleri serileştirmek için tasarlanmıştır ve Uzaktan iletişim tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="690e6-271">The [Serializable] attribute and ISerializable interface were originally designed to serialize types within trusted environments, and they are used by Remoting.</span></span> <span data-ttu-id="690e6-272">WCF seri hale getirme [DataContract] ile işaretlenen türler ve [DataMember] kullanır.</span><span class="sxs-lookup"><span data-stu-id="690e6-272">WCF serialization relies on types being marked with [DataContract] and [DataMember].</span></span> <span data-ttu-id="690e6-273">Bir uygulama tarafından kullanılan veri türleri [DataContract] kullanın ve ISerializable veya [Serializable] kullanmayacak şekilde değiştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="690e6-273">Data types used by an application should be modified to use [DataContract] and not to use ISerializable or [Serializable].</span></span> <span data-ttu-id="690e6-274">[Serializable] özniteliği ve ISerializable arabirimini başlangıçta güvenilir ortamlar içinde türleri serileştirmek için tasarlanmıştır ve Uzaktan iletişim tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="690e6-274">The [Serializable] attribute and ISerializable interface were originally designed to serialize types within trusted environments, and they are used by Remoting.</span></span> <span data-ttu-id="690e6-275">WCF seri hale getirme [DataContract] ile işaretlenen türler ve [DataMember] kullanır.</span><span class="sxs-lookup"><span data-stu-id="690e6-275">WCF serialization relies on types being marked with [DataContract] and [DataMember].</span></span> <span data-ttu-id="690e6-276">Bir uygulama tarafından kullanılan veri türleri [DataContract] kullanın ve ISerializable veya [Serializable] kullanmayacak şekilde değiştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="690e6-276">Data types used by an application should be modified to use [DataContract] and not to use ISerializable or [Serializable].</span></span>  
  
### <a name="migration-scenarios"></a><span data-ttu-id="690e6-277">Geçiş senaryoları</span><span class="sxs-lookup"><span data-stu-id="690e6-277">Migration Scenarios</span></span>  
 <span data-ttu-id="690e6-278">Artık aşağıdaki ortak uzaktan iletişim senaryolarında WCF yerine getirmeyi bakalım:</span><span class="sxs-lookup"><span data-stu-id="690e6-278">Now let’s see how to accomplish the following common Remoting scenarios in WCF:</span></span>  
  
1.  <span data-ttu-id="690e6-279">Sunucu istemciye bir nesne tarafından değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="690e6-279">Server returns an object by-value to the client</span></span>  
  
2.  <span data-ttu-id="690e6-280">Sunucu bir nesne başvuru tarafından istemciye döndürür.</span><span class="sxs-lookup"><span data-stu-id="690e6-280">Server returns an object by-reference to the client</span></span>  
  
3.  <span data-ttu-id="690e6-281">İstemci bir nesneyi değere göre sunucuya gönderir.</span><span class="sxs-lookup"><span data-stu-id="690e6-281">Client sends an object by-value to the server</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="690e6-282">Bir nesne başvuruya göre istemciden sunucuya gönderme WCF'de izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="690e6-282">Sending an object by-reference from the client to the server is not allowed in WCF.</span></span>  
  
 <span data-ttu-id="690e6-283">Bu senaryolar üzerinden okurken aşağıdaki örnekteki gibi .NET uzaktan iletişim için sunduğumuz temel arabirimleri konum varsayılır.</span><span class="sxs-lookup"><span data-stu-id="690e6-283">When reading through these scenarios, assume our baseline interfaces for .NET Remoting look like the following example.</span></span> <span data-ttu-id="690e6-284">.NET uzaktan iletişim uygulaması WCF eşdeğer bir işlevselliği uygulamak için yalnızca nasıl kullanılacağını örneklendiren istediğimizden burada önemli değildir.</span><span class="sxs-lookup"><span data-stu-id="690e6-284">The .NET Remoting implementation is not important here because we want to illustrate only how to use WCF to implement equivalent functionality.</span></span>  
  
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
  
#### <a name="scenario-1-service-returns-an-object-by-value"></a><span data-ttu-id="690e6-285">Senaryo 1: Hizmet bir nesne değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="690e6-285">Scenario 1: Service Returns an Object by Value</span></span>  
 <span data-ttu-id="690e6-286">Bu senaryo, bir nesne istemciye değere göre döndürmenin bir sunucu gösterir.</span><span class="sxs-lookup"><span data-stu-id="690e6-286">This scenario demonstrates a server returning an object to the client by value.</span></span> <span data-ttu-id="690e6-287">Aşağıdaki adımları normal bir WCF hizmeti oluşturmak nasıl tanımlamaları yeterlidir, böylece WCF her zaman nesneleri sunucudan değere göre döndürür.</span><span class="sxs-lookup"><span data-stu-id="690e6-287">WCF always returns objects from the server by value, so the following steps simply describe how to build a normal WCF service.</span></span>  
  
1.  <span data-ttu-id="690e6-288">WCF hizmeti için ortak bir arabirim tanımlayarak işe başlamak ve [ServiceContract] özniteliği ile işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="690e6-288">Start by defining a public interface for the WCF service and mark it with the [ServiceContract] attribute.</span></span> <span data-ttu-id="690e6-289">[OperationContract] istemcimizin çağıran sunucu taraflı yöntemleri tanımlamak için kullanırız.</span><span class="sxs-lookup"><span data-stu-id="690e6-289">We use [OperationContract] to identify the server-side methods our client will call.</span></span>  
  
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
  
2.  <span data-ttu-id="690e6-290">Sonraki adım, bu hizmet için veri anlaşması oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="690e6-290">The next step is to create the data contract for this service.</span></span> <span data-ttu-id="690e6-291">[DataContract] özniteliği ile işaretlenmiş sınıfların (arabirimler değil) oluşturarak bunu.</span><span class="sxs-lookup"><span data-stu-id="690e6-291">We do this by creating classes (not interfaces) marked with the [DataContract] attribute.</span></span> <span data-ttu-id="690e6-292">Tek tek özellikler veya alanları hem istemci hem de sunucu görünür istiyoruz, [DataMember] ile işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="690e6-292">The individual properties or fields we want visible to both client and server are marked with [DataMember].</span></span> <span data-ttu-id="690e6-293">İzin verilmesi için türetilen türlerin istiyoruz, biz bunları tanımlamak için [KnownType] özniteliğini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="690e6-293">If we want derived types to be allowed, we must use the [KnownType] attribute to identify them.</span></span> <span data-ttu-id="690e6-294">WCF türleri yalnızca, serileştirilecek veya seri durumdan çıkarılmakta olan bu hizmet için hizmet arabirimi ve bu "bilinen türler" olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="690e6-294">The only types WCF will allow to be serialized or deserialized for this service are those in the service interface and these "known types".</span></span> <span data-ttu-id="690e6-295">Bu listede olmayan herhangi bir türü exchange çalışılıyor reddedilir.</span><span class="sxs-lookup"><span data-stu-id="690e6-295">Attempting to exchange any other type not in this list will be rejected.</span></span>  
  
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
  
3.  <span data-ttu-id="690e6-296">Ardından, hizmet arabirimi uygulamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="690e6-296">Next, we provide the implementation for the service interface.</span></span>  
  
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
  
4.  <span data-ttu-id="690e6-297">WCF hizmeti çalıştırmak için belirli bir WCF bağlamayı kullanarak belirli bir URL'den bu hizmet arabirimi kullanıma sunan bir uç nokta bildirmek ihtiyacımız var.</span><span class="sxs-lookup"><span data-stu-id="690e6-297">To run the WCF service, we need to declare an endpoint that exposes that service interface at a specific URL using a specific WCF binding.</span></span> <span data-ttu-id="690e6-298">Bu durum genellikle aşağıdaki bölümlerde sunucu projenin web.config dosyasına ekleyerek gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="690e6-298">This is typically done by adding the following sections to the server project’s web.config file.</span></span>  
  
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
  
5.  <span data-ttu-id="690e6-299">WCF hizmeti, ardından aşağıdaki kod ile başlatılabilir:</span><span class="sxs-lookup"><span data-stu-id="690e6-299">The WCF service can then be started with the following code:</span></span>  
  
   ```csharp
   ServiceHost customerServiceHost = new ServiceHost(typeof(CustomerService));  
       customerServiceHost.Open();  
   ```  
  
     <span data-ttu-id="690e6-300">Bu ServiceHost başlatıldığında, uygun sözleşmeyi, bağlamayı ve uç nokta oluşturmak için web.config dosyasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="690e6-300">When this ServiceHost is started, it uses the web.config file to establish the proper contract, binding and endpoint.</span></span> <span data-ttu-id="690e6-301">Yapılandırma dosyaları hakkında daha fazla bilgi için bkz. [yapılandırma dosyalarını kullanarak Hizmetleri Yapılandırma](./configuring-services-using-configuration-files.md).</span><span class="sxs-lookup"><span data-stu-id="690e6-301">For more information about configuration files, see [Configuring Services Using Configuration Files](./configuring-services-using-configuration-files.md).</span></span> <span data-ttu-id="690e6-302">Sunucu başlangıç bu stil, kendi kendine barındırma olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="690e6-302">This style of starting the server is known as self-hosting.</span></span> <span data-ttu-id="690e6-303">WCF hizmetleri barındırma için diğer seçenekler hakkında daha fazla bilgi için bkz: [barındırma hizmetleri](./hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="690e6-303">To learn more about other choices for hosting WCF services, see [Hosting Services](./hosting-services.md).</span></span>  
  
6.  <span data-ttu-id="690e6-304">İstemci projenin app.config hizmet uç noktası için eşleşen bağlama bilgileri belirtmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="690e6-304">The client project’s app.config must declare matching binding information for the service’s endpoint.</span></span> <span data-ttu-id="690e6-305">Visual Studio'da bunu yapmanın en kolay yolu kullanmaktır **hizmet Başvurusu Ekle**, hangi otomatik olarak güncelleştirilir app.config dosyası.</span><span class="sxs-lookup"><span data-stu-id="690e6-305">The easiest way to do this in Visual Studio is to use **Add Service Reference**, which will automatically update the app.config file.</span></span> <span data-ttu-id="690e6-306">Alternatif olarak, aynı değişiklikleri el ile eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="690e6-306">Alternatively, these same changes can be added manually.</span></span>  
  
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
  
     <span data-ttu-id="690e6-307">Kullanma hakkında daha fazla bilgi için **hizmet Başvurusu Ekle**, bkz: [nasıl yapılır: ekleme, güncelleştirme veya hizmet başvurusunu kaldırın](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference).</span><span class="sxs-lookup"><span data-stu-id="690e6-307">For more information about using **Add Service Reference**, see [How to: Add, Update, or Remove a Service Reference](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference).</span></span>  
  
7.  <span data-ttu-id="690e6-308">Şimdi biz WCF Hizmeti istemciden çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="690e6-308">Now we can call the WCF service from the client.</span></span> <span data-ttu-id="690e6-309">Bu hizmet için kanal fabrikası oluşturma için bir kanal isteyen ve doğrudan bu kanalda istiyoruz yöntemi çağırma bunu.</span><span class="sxs-lookup"><span data-stu-id="690e6-309">We do this by creating a channel factory for that service, asking it for a channel, and directly calling the method we want on that channel.</span></span> <span data-ttu-id="690e6-310">Kanal hizmet arabirimi uygulayan ve bizim için temel alınan istek/yanıt mantığı işler çünkü biz bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="690e6-310">We can do this because the channel implements the service’s interface and handles the underlying request/reply logic for us.</span></span> <span data-ttu-id="690e6-311">Bu yöntem çağrısının dönüş değeri, sunucunun yanıt seri durumdan çıkarılmış kopyasıdır.</span><span class="sxs-lookup"><span data-stu-id="690e6-311">The return value from that method call is the deserialized copy of the server’s response.</span></span>  
  
   ```csharp
   ChannelFactory<ICustomerService> factory =  
       new ChannelFactory<ICustomerService>("customerservice");  
   ICustomerService service = factory.CreateChannel();  
   Customer customer = service.GetCustomer(42);  
   Console.WriteLine(String.Format("  Customer {0} {1} received.",  
           customer.FirstName, customer.LastName));  
   ```  
  
 <span data-ttu-id="690e6-312">WCF tarafından sunucudan istemciye döndürülen nesneleri tarafından her zaman değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="690e6-312">Objects returned by WCF from the server to the client are always by value.</span></span> <span data-ttu-id="690e6-313">Sunucu tarafından gönderilen verileri seri durumdan çıkarılmış kopyalarını nesneleridir.</span><span class="sxs-lookup"><span data-stu-id="690e6-313">The objects are deserialized copies of the data sent by the server.</span></span> <span data-ttu-id="690e6-314">İstemci, sunucu kodu çağırmalarla çağırma herhangi olma tehlikesi olmadan bu yerel kopyalar üzerinde yöntemleri çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="690e6-314">The client can call methods on these local copies without any danger of invoking server code through callbacks.</span></span>  
  
#### <a name="scenario-2-server-returns-an-object-by-reference"></a><span data-ttu-id="690e6-315">Senaryo 2: Sunucu başvuruya göre bir nesne döndürür</span><span class="sxs-lookup"><span data-stu-id="690e6-315">Scenario 2: Server Returns an Object By Reference</span></span>  
 <span data-ttu-id="690e6-316">Bu senaryo, bir nesne başvurusu tarafından istemciye sağlayan sunucu gösterir.</span><span class="sxs-lookup"><span data-stu-id="690e6-316">This scenario demonstrates the server providing an object to the client by reference.</span></span> <span data-ttu-id="690e6-317">.NET uzaktan iletişim'de bu otomatik olarak MarshalByRefObject öğesinden türetilen her tür için işlenir başvuruya göre sıralanmış olan.</span><span class="sxs-lookup"><span data-stu-id="690e6-317">In .NET Remoting, this is handled automatically for any type derived from MarshalByRefObject, which is serialized by-reference.</span></span> <span data-ttu-id="690e6-318">Bu senaryoya örnek olarak, bağımsız kapatamaması sunucu tarafı nesneleri birden çok istemci izin verir.</span><span class="sxs-lookup"><span data-stu-id="690e6-318">An example of this scenario is allowing multiple clients to have independent sessionful server-side objects.</span></span> <span data-ttu-id="690e6-319">Daha önce belirtildiği gibi bir WCF hizmeti tarafından döndürülen nesne her zaman değere göre bu yüzden bir başvuruya göre nesnesinin doğrudan bir eşdeğer ancak başvuruya göre semantiği kullanarak benzer bir şey elde etmek olası bir <xref:System.ServiceModel.EndpointAddress10> nesne.</span><span class="sxs-lookup"><span data-stu-id="690e6-319">As previously mentioned, objects returned by a WCF service are always by value, so there is no direct equivalent of a by-reference object, but it is possible to achieve something similar to by-reference semantics using an <xref:System.ServiceModel.EndpointAddress10> object.</span></span> <span data-ttu-id="690e6-320">Bu sunucuda kapatamaması başvuru tarafından nesnesini almak için istemci tarafından kullanılan bir değer tarafından seri hale getirilebilir bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="690e6-320">This is a serializable by-value object that can be used by the client to obtain a sessionful by-reference object on the server.</span></span> <span data-ttu-id="690e6-321">Bu, birden fazla istemciyle sunucu tarafı nesneleri kapatamaması bağımsız olması, senaryosu sağlar.</span><span class="sxs-lookup"><span data-stu-id="690e6-321">This enables the scenario of having multiple clients with independent sessionful server-side objects.</span></span>  
  
1.  <span data-ttu-id="690e6-322">İlk olarak biz kapatamaması nesnenin kendisine karşılık gelen bir WCF Hizmeti sözleşmesi tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="690e6-322">First, we need to define a WCF service contract that corresponds to the sessionful object itself.</span></span>  
  
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
    >  <span data-ttu-id="690e6-323">Oturum nesnesi [ServiceContract] ile işaretli, normal yapmadan WCF hizmet arabirimi dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="690e6-323">Notice that the sessionful object is marked with [ServiceContract], making it a normal WCF service interface.</span></span> <span data-ttu-id="690e6-324">Sessionmode'u ayarlama özelliği kapatamaması hizmet olacaktır gösterir.</span><span class="sxs-lookup"><span data-stu-id="690e6-324">Setting the SessionMode property indicates it will be a sessionful service.</span></span> <span data-ttu-id="690e6-325">WCF'de, oturum, birden çok ileti iki uç nokta arasında gönderilen ilişkilendirme bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="690e6-325">In WCF, a session is a way of correlating multiple messages sent between two endpoints.</span></span> <span data-ttu-id="690e6-326">Bu, istemci bu hizmet için bir bağlantı alır, sonra oturumu istemci ve sunucu arasında kurulur, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="690e6-326">This means that once a client obtains a connection to this service, a session will be established between the client and the server.</span></span> <span data-ttu-id="690e6-327">İstemci bu oturumla içinde için tüm etkileşimler bir tek benzersiz bir sunucu tarafı nesne örneği kullanın.</span><span class="sxs-lookup"><span data-stu-id="690e6-327">The client will use a single unique instance of the server-side object for all its interactions within this single session.</span></span>  
  
2.  <span data-ttu-id="690e6-328">Ardından, bu hizmet arabiriminin uygulamasını sağlamak ihtiyacımız var.</span><span class="sxs-lookup"><span data-stu-id="690e6-328">Next, we need to provide the implementation of this service interface.</span></span> <span data-ttu-id="690e6-329">[ServiceBehavior] ile belirten ve InstanceContextMode ayarlayarak, biz WCF her oturum için benzersiz bir örnek bu türde kullanılacak istiyoruz söyleyin.</span><span class="sxs-lookup"><span data-stu-id="690e6-329">By denoting it with [ServiceBehavior] and setting the InstanceContextMode, we tell WCF we want to use a unique instance of this type for an each session.</span></span>  
  
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
  
3.  <span data-ttu-id="690e6-330">Şimdi bu kapatamaması nesne örneği elde etmek için bir yol gerekir.</span><span class="sxs-lookup"><span data-stu-id="690e6-330">Now we need a way to obtain an instance of this sessionful object.</span></span> <span data-ttu-id="690e6-331">EndpointAddress10 nesneyi döndürür. başka bir WCF Hizmeti arabirimi oluşturarak bunu.</span><span class="sxs-lookup"><span data-stu-id="690e6-331">We do this by creating another WCF service interface that returns an EndpointAddress10 object.</span></span> <span data-ttu-id="690e6-332">Bu istemci kapatamaması nesnesi oluşturmak için kullanabileceğiniz bir uç nokta seri hale getirilebilir bir biçimidir.</span><span class="sxs-lookup"><span data-stu-id="690e6-332">This is a serializable form of an endpoint that the client can use to create the sessionful object.</span></span>  
  
   ```csharp
   [ServiceContract]  
       public interface ISessionBoundFactory  
       {  
           [OperationContract]  
           EndpointAddress10 GetInstanceAddress();  
       }  
   ```  
  
     <span data-ttu-id="690e6-333">Ve biz bu WCF Hizmeti uygulayın:</span><span class="sxs-lookup"><span data-stu-id="690e6-333">And we implement this WCF service:</span></span>  
  
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
  
     <span data-ttu-id="690e6-334">Bu uygulama kapatamaması nesneleri oluşturmak için singleton kanal fabrikası tutar.</span><span class="sxs-lookup"><span data-stu-id="690e6-334">This implementation maintains a singleton channel factory to create sessionful objects.</span></span> <span data-ttu-id="690e6-335">GetInstanceAddress() çağrıldığında, bir kanal oluşturur ve etkili bir şekilde bu kanal ile ilişkili uzak adresini işaret eden EndpointAddress10 nesne oluşturur.</span><span class="sxs-lookup"><span data-stu-id="690e6-335">When GetInstanceAddress() is called, it creates a channel and creates an EndpointAddress10 object that effectively points to the remote address associated with this channel.</span></span> <span data-ttu-id="690e6-336">EndpointAddress10 yalnızca istemci tarafından değeri olarak döndürülebilecek bir veri türü var.</span><span class="sxs-lookup"><span data-stu-id="690e6-336">EndpointAddress10 is simply a data type that can be returned to the client by-value.</span></span>  
  
4.  <span data-ttu-id="690e6-337">Biz aşağıdaki örnekte gösterildiği gibi iki şunları yaparak sunucunun yapılandırma dosyasını değiştirmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="690e6-337">We need to modify the server’s configuration file by doing the following two things as shown in the example below:</span></span>  
  
    1.  <span data-ttu-id="690e6-338">Bildirme bir \<istemci > kapatamaması nesne için uç nokta açıklayan bölümü.</span><span class="sxs-lookup"><span data-stu-id="690e6-338">Declare a \<client> section that describes the endpoint for the sessionful object.</span></span> <span data-ttu-id="690e6-339">Bunun gerekli olmasının nedeni, sunucunun da bu durumda istemci olarak davranır.</span><span class="sxs-lookup"><span data-stu-id="690e6-339">This is necessary because the server also acts as a client in this situation.</span></span>  
  
    2.  <span data-ttu-id="690e6-340">Uç noktaları için Fabrika ve sessionful nesne bildirir.</span><span class="sxs-lookup"><span data-stu-id="690e6-340">Declare endpoints for the factory and sessionful object.</span></span> <span data-ttu-id="690e6-341">Bu istemci, hizmet uç noktaları ile EndpointAddress10 alma ve oturum kanalı oluşturmak için iletişim kurmasına izin vermek gereklidir.</span><span class="sxs-lookup"><span data-stu-id="690e6-341">This is necessary to allow the client to communicate with the service endpoints to acquire the EndpointAddress10 and to create the sessionful channel.</span></span>  
  
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
  
     <span data-ttu-id="690e6-342">' İ tıklatın ve ardından şu hizmetlerin başlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="690e6-342">And then we can start these services:</span></span>  
  
   ```csharp
   ServiceHost factoryHost = new ServiceHost(typeof(SessionBoundFactory));  
   factoryHost.Open();  
  
   ServiceHost sessionHost = new ServiceHost(typeof(MySessionBoundObject));  
   sessionHost.Open();  
   ```  
  
5.  <span data-ttu-id="690e6-343">Bu aynı uç noktaları, projenin app.config dosyasında bildirerek istemcinin yapılandırıyoruz.</span><span class="sxs-lookup"><span data-stu-id="690e6-343">We configure the client by declaring these same endpoints in its project’s app.config file.</span></span>  
  
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
  
6.  <span data-ttu-id="690e6-344">Bu oturumdaki nesnesi oluşturma ve kullanma hakkında bilgi için istemci aşağıdakileri yapmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="690e6-344">In order to create and use this sessionful object, the client must do the following steps:</span></span>  
  
    1.  <span data-ttu-id="690e6-345">ISessionBoundFactory hizmete bir kanal oluşturun.</span><span class="sxs-lookup"><span data-stu-id="690e6-345">Create a channel to the ISessionBoundFactory service.</span></span>  
  
    2.  <span data-ttu-id="690e6-346">Bu kanal, bir EndpointAddress10 almak için bu hizmeti çağırmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="690e6-346">Use that channel to invoke that service to obtain an EndpointAddress10.</span></span>  
  
    3.  <span data-ttu-id="690e6-347">EndpointAddress10 kapatamaması bir nesne elde etmek için bir kanal oluşturmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="690e6-347">Use the EndpointAddress10 to create a channel to obtain a sessionful object.</span></span>  
  
    4.  <span data-ttu-id="690e6-348">Birden çok çağrı aynı örneğini kalır göstermek için kapatamaması nesne ile etkileşim kurun.</span><span class="sxs-lookup"><span data-stu-id="690e6-348">Interact with the sessionful object to demonstrate it remains the same instance across multiple calls.</span></span>  
  
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
  
 <span data-ttu-id="690e6-349">WCF değere göre her zaman nesnelerini döndürür, ancak başvuruya göre semantiği EndpointAddress10 genelindeki denk desteklemek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="690e6-349">WCF always returns objects by value, but it is possible to support the equivalent of by-reference semantics through the use of EndpointAddress10.</span></span> <span data-ttu-id="690e6-350">Bu istemcinin sonra Bu raporla herhangi bir WCF hizmeti gibi etkileşim kurmasını kapatamaması bir WCF hizmeti örneği isteği izin verir.</span><span class="sxs-lookup"><span data-stu-id="690e6-350">This permits the client to request a sessionful WCF service instance, after which it can interact with it like any other WCF service.</span></span>  
  
#### <a name="scenario-3-client-sends-server-a-by-value-instance"></a><span data-ttu-id="690e6-351">Senaryo 3: Sunucu istemci, bir değere göre örneği gönderir.</span><span class="sxs-lookup"><span data-stu-id="690e6-351">Scenario 3: Client Sends Server a By-Value Instance</span></span>  
 <span data-ttu-id="690e6-352">Bu senaryo, temel olmayan nesne örneği, değere göre sunucuya gönderme istemci gösterir.</span><span class="sxs-lookup"><span data-stu-id="690e6-352">This scenario demonstrates the client sending a non-primitive object instance to the server by value.</span></span> <span data-ttu-id="690e6-353">WCF nesneleri değerine göre yalnızca gönderir. çünkü bu senaryo normal WCF kullanım gösterir.</span><span class="sxs-lookup"><span data-stu-id="690e6-353">Because WCF only sends objects by value, this scenario demonstrates normal WCF usage.</span></span>  
  
1.  <span data-ttu-id="690e6-354">Senaryo 1 aynı WCF hizmetinden kullanın.</span><span class="sxs-lookup"><span data-stu-id="690e6-354">Use the same WCF Service from Scenario 1.</span></span>  
  
2.  <span data-ttu-id="690e6-355">İstemci, yeni bir değere göre nesne (müşteri) oluşturmak, ICustomerService hizmetiyle iletişim kurmak için bir kanal oluşturmak ve nesne göndermek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="690e6-355">Use the client to create a new by-value object (Customer), create a channel to communicate with the ICustomerService service, and send the object to it.</span></span>  
  
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
  
     <span data-ttu-id="690e6-356">Müşteri nesnesi seri hale getirilmiş ve o nesnenin yeni bir kopyasını nereden serisi sunucuya gönderilir.</span><span class="sxs-lookup"><span data-stu-id="690e6-356">The customer object will be serialized, and sent to the server, where it is deserialized into a new copy of that object.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="690e6-357">Bu kod Ayrıca, türetilmiş bir tür (PremiumCustomer) gönderme gösterir.</span><span class="sxs-lookup"><span data-stu-id="690e6-357">This code also illustrates sending a derived type (PremiumCustomer).</span></span> <span data-ttu-id="690e6-358">Hizmet arabirimi müşteri nesnesi bekliyor, ancak müşteri sınıfı [KnownType] özniteliğini PremiumCustomer de izin belirtilen.</span><span class="sxs-lookup"><span data-stu-id="690e6-358">The service interface expects a Customer object, but the [KnownType] attribute on the Customer class indicated PremiumCustomer was also allowed.</span></span> <span data-ttu-id="690e6-359">WCF serileştirmek veya bu hizmet arabirimi aracılığıyla herhangi bir türü seri durumdan girişimleri başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="690e6-359">WCF will fail any attempt to serialize or deserialize any other type through this service interface.</span></span>  
  
 <span data-ttu-id="690e6-360">Veri değişimleri normal WCF tarafından değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="690e6-360">Normal WCF exchanges of data are by value.</span></span> <span data-ttu-id="690e6-361">Bu garanti bu veri nesneleri birinde yöntemlerini çağırma, yalnızca yerel olarak yürütür: kod bir katman çağırma kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="690e6-361">This guarantees that invoking methods on one of these data objects executes only locally – it will not invoke code on the other tier.</span></span> <span data-ttu-id="690e6-362">Başvuru ile döndürülen nesne gibi bir şey elde etmek mümkün olmakla birlikte *gelen* sunucuya bir istemci bir başvuruya göre nesneyi geçirmek mümkün değildir *için* sunucu.</span><span class="sxs-lookup"><span data-stu-id="690e6-362">While it is possible to achieve something like by-reference objects returned *from* the server, it is not possible for a client to pass a by-reference object *to* the server.</span></span> <span data-ttu-id="690e6-363">İstemci ve sunucu arasında sürekli bir konuşma gerektiren bir senaryo, bir çift yönlü hizmet kullanarak WCF'de gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="690e6-363">A scenario that requires a conversation back and forth between client and server can be achieved in WCF using a duplex service.</span></span> <span data-ttu-id="690e6-364">Daha fazla bilgi için [çift yönlü Hizmetler](./feature-details/duplex-services.md).</span><span class="sxs-lookup"><span data-stu-id="690e6-364">For more information, see [Duplex Services](./feature-details/duplex-services.md).</span></span>  
  
## <a name="summary"></a><span data-ttu-id="690e6-365">Özet</span><span class="sxs-lookup"><span data-stu-id="690e6-365">Summary</span></span>  
 <span data-ttu-id="690e6-366">.NET uzaktan iletişim sadece tam güvenilir ortamlar içinde kullanılmak üzere bir iletişim çerçevedir.</span><span class="sxs-lookup"><span data-stu-id="690e6-366">.NET Remoting is a communication framework intended to be used only within fully-trusted environments.</span></span> <span data-ttu-id="690e6-367">Bu, eski bir üründür ve yalnızca geriye dönük uyumluluk için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="690e6-367">It is a legacy product and supported only for backward compatibility.</span></span> <span data-ttu-id="690e6-368">Yeni uygulamalar oluşturmak için kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="690e6-368">It should not be used to build new applications.</span></span> <span data-ttu-id="690e6-369">Buna karşılık, WCF güvenlik düşünülerek tasarlanmıştır ve yeni ve mevcut uygulamalar için önerilir.</span><span class="sxs-lookup"><span data-stu-id="690e6-369">Conversely, WCF was designed with security in mind and is recommended for new and existing applications.</span></span> <span data-ttu-id="690e6-370">Microsoft önerir, mevcut uzaktan iletişim uygulamalarını geçişi WCF veya ASP.NET Web API'si yerine kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="690e6-370">Microsoft recommends that existing Remoting applications be migrated to use WCF or ASP.NET Web API instead.</span></span>