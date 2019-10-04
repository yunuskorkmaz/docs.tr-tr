---
title: "Nasıl yapılır: yönetilen kod DCOM 'u WCF 'ye geçirme"
ms.date: 03/30/2017
ms.assetid: 52961ffc-d1c7-4f83-832c-786444b951ba
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 42edce63856b629511faeb165362da18ea3cecad
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833625"
---
# <a name="how-to-migrate-managed-code-dcom-to-wcf"></a><span data-ttu-id="cc60f-102">Nasıl yapılır: yönetilen kod DCOM 'u WCF 'ye geçirme</span><span class="sxs-lookup"><span data-stu-id="cc60f-102">How to: Migrate Managed-Code DCOM to WCF</span></span>
<span data-ttu-id="cc60f-103">Windows Communication Foundation (WCF) dağıtılmış bir ortamdaki sunucular ve istemciler arasındaki yönetilen kod çağrıları için dağıtılmış bileşen nesne modeli (DCOM) üzerinde önerilen ve güvenli seçenektir.</span><span class="sxs-lookup"><span data-stu-id="cc60f-103">Windows Communication Foundation (WCF) is the recommended and secure choice over Distributed Component Object Model (DCOM) for managed code calls between servers and clients in a distributed environment.</span></span> <span data-ttu-id="cc60f-104">Bu makalede, aşağıdaki senaryolar için DCOM 'dan WCF 'ye nasıl kod geçirebileceğiniz gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="cc60f-104">This article shows how you to migrate code from DCOM to WCF for the following scenarios.</span></span>  
  
- <span data-ttu-id="cc60f-105">Uzak hizmet, istemciye bir nesne değeri döndürür</span><span class="sxs-lookup"><span data-stu-id="cc60f-105">The remote service returns an object by-value to the client</span></span>  
  
- <span data-ttu-id="cc60f-106">İstemci, uzak hizmete bir nesne olarak değer gönderir</span><span class="sxs-lookup"><span data-stu-id="cc60f-106">The client sends an object by-value to the remote service</span></span>  
  
- <span data-ttu-id="cc60f-107">Uzak hizmet, istemciye başvuruya göre bir nesne döndürür</span><span class="sxs-lookup"><span data-stu-id="cc60f-107">The remote service returns an object by-reference to the client</span></span>  
  
 <span data-ttu-id="cc60f-108">Güvenlik nedenleriyle, istemciden hizmete bir nesne başvuruya göre gönderilmesi WCF 'de buna izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="cc60f-108">For security reasons, sending an object by-reference from the client to the service is not allowed in WCF.</span></span> <span data-ttu-id="cc60f-109">Bir çift yönlü hizmet kullanılarak, istemci ve sunucu arasında geri ve ileri bir konuşma gerektiren bir senaryo WCF 'de elde edilebilir.</span><span class="sxs-lookup"><span data-stu-id="cc60f-109">A scenario that requires a conversation back and forth between client and server can be achieved in WCF using a duplex service.</span></span>  <span data-ttu-id="cc60f-110">Çift yönlü hizmetler hakkında daha fazla bilgi için bkz. [çift yönlü hizmetler](../wcf/feature-details/duplex-services.md).</span><span class="sxs-lookup"><span data-stu-id="cc60f-110">For more information about duplex services, see [Duplex Services](../wcf/feature-details/duplex-services.md).</span></span>  
  
 <span data-ttu-id="cc60f-111">Bu hizmetler için WCF Hizmetleri ve istemcileri oluşturma hakkında daha fazla bilgi için bkz. [Temel WCF programlama](../wcf/basic-wcf-programming.md), [Hizmetleri tasarlama ve uygulama](../wcf/designing-and-implementing-services.md)ve [istemci oluşturma](../wcf/building-clients.md).</span><span class="sxs-lookup"><span data-stu-id="cc60f-111">For more details about creating WCF services and clients for those services, see [Basic WCF Programming](../wcf/basic-wcf-programming.md), [Designing and Implementing Services](../wcf/designing-and-implementing-services.md), and [Building Clients](../wcf/building-clients.md).</span></span>  
  
## <a name="dcom-example-code"></a><span data-ttu-id="cc60f-112">DCOM örnek kodu</span><span class="sxs-lookup"><span data-stu-id="cc60f-112">DCOM example code</span></span>  
 <span data-ttu-id="cc60f-113">Bu senaryolar için, WCF kullanılarak gösterilen DCOM arabirimleri aşağıdaki yapıya sahiptir:</span><span class="sxs-lookup"><span data-stu-id="cc60f-113">For these scenarios, the DCOM interfaces that are illustrated using WCF have the following structure:</span></span>  
  
```csharp  
[ComVisible(true)]  
[Guid("AA9C4CDB-55EA-4413-90D2-843F1A49E6E6")]  
public interface IRemoteService  
{  
   Customer GetObjectByValue();  
   IRemoteObject GetObjectByReference();  
   void SendObjectByValue(Customer customer);  
}  
  
[ComVisible(true)]  
[Guid("A12C98DE-B6A1-463D-8C24-81E4BBC4351B")]  
public interface IRemoteObject  
{  
}  
  
public class Customer  
{  
}  
```  
  
## <a name="the-service-returns-an-object-by-value"></a><span data-ttu-id="cc60f-114">Hizmet bir nesne değere göre döndürüyor</span><span class="sxs-lookup"><span data-stu-id="cc60f-114">The service returns an object by-value</span></span>  
 <span data-ttu-id="cc60f-115">Bu senaryo için, bir hizmet çağrısı yaparsınız ve IT yöntemi sunucudan istemciye değer ile geçirilen bir nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="cc60f-115">For this scenario, you make a call to a service and it method returns an object, which is passed by-value from the server to the client.</span></span> <span data-ttu-id="cc60f-116">Bu senaryo aşağıdaki COM çağrısını temsil eder:</span><span class="sxs-lookup"><span data-stu-id="cc60f-116">This scenario represents the following COM call:</span></span>  
  
```csharp  
public interface IRemoteService  
{  
    Customer GetObjectByValue();  
}  
```  
  
 <span data-ttu-id="cc60f-117">Bu senaryoda istemci, uzak hizmetten bir nesnenin serisi kaldırılmış bir kopyasını alır.</span><span class="sxs-lookup"><span data-stu-id="cc60f-117">In this scenario, the client receives a deserialized copy of an object from the remote service.</span></span> <span data-ttu-id="cc60f-118">İstemci, hizmete geri çağrı yapmadan bu yerel kopyayla etkileşime geçebilir.</span><span class="sxs-lookup"><span data-stu-id="cc60f-118">The client can interact with this local copy without calling back to the service.</span></span>  <span data-ttu-id="cc60f-119">Diğer bir deyişle, istemci garanti edilir çünkü yerel kopyada Yöntemler çağrıldığında hizmetin hiçbir şekilde ilgili olmaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="cc60f-119">In other words, the client is guaranteed the service will not be involved in any way when methods on the local copy are called.</span></span> <span data-ttu-id="cc60f-120">WCF her zaman değere göre hizmetten nesneleri döndürür, bu nedenle aşağıdaki adımlarda normal bir WCF hizmeti oluşturma açıklanır.</span><span class="sxs-lookup"><span data-stu-id="cc60f-120">WCF always returns objects from the service by value, so the following steps describe creating a regular WCF service.</span></span>  
  
### <a name="step-1-define-the-wcf-service-interface"></a><span data-ttu-id="cc60f-121">1\. Adım: WCF hizmeti arabirimini tanımlama</span><span class="sxs-lookup"><span data-stu-id="cc60f-121">Step 1: Define the WCF service interface</span></span>  
 <span data-ttu-id="cc60f-122">WCF hizmeti için bir ortak arabirim tanımlayın ve [<xref:System.ServiceModel.ServiceContractAttribute>] özniteliğiyle işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="cc60f-122">Define a public interface for the WCF service and mark it with the [<xref:System.ServiceModel.ServiceContractAttribute>] attribute.</span></span>  <span data-ttu-id="cc60f-123">İstemcilere göstermek istediğiniz yöntemleri [<xref:System.ServiceModel.OperationContractAttribute>] özniteliğiyle işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="cc60f-123">Mark the methods you want to expose to clients with the [<xref:System.ServiceModel.OperationContractAttribute>] attribute.</span></span> <span data-ttu-id="cc60f-124">Aşağıdaki örnek, bir istemcinin çağırabilmesi için sunucu tarafı arabirimi ve arabirim yöntemlerini tanımlamak üzere bu özniteliklerin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="cc60f-124">The following example shows using these attributes to identify the server-side interface and interface methods a client can call.</span></span> <span data-ttu-id="cc60f-125">Bu senaryo için kullanılan yöntem kalın olarak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="cc60f-125">The method used for this scenario is shown in bold.</span></span>  
  
```csharp  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.ServiceModel.Web;   
. . .  
[ServiceContract]  
public interface ICustomerManager  
{  
    [OperationContract]  
    void StoreCustomer(Customer customer);  
  
    [OperationContract]     Customer GetCustomer(string firstName, string lastName);   
  
}  
```  
  
### <a name="step-2-define-the-data-contract"></a><span data-ttu-id="cc60f-126">2\. Adım: veri sözleşmesini tanımlama</span><span class="sxs-lookup"><span data-stu-id="cc60f-126">Step 2: Define the data contract</span></span>  
 <span data-ttu-id="cc60f-127">Daha sonra hizmet için bir veri sözleşmesi oluşturmanız gerekir, bu, hizmetin ve istemcilerinin arasında verilerin nasıl değiş tokuş olacağını anlatmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cc60f-127">Next you should create a data contract for the service, which will describe how the data will be exchanged between the service and its clients.</span></span>  <span data-ttu-id="cc60f-128">Veri sözleşmesinde açıklanan sınıflar [<xref:System.Runtime.Serialization.DataContractAttribute>] özniteliğiyle işaretlenmelidir.</span><span class="sxs-lookup"><span data-stu-id="cc60f-128">Classes described in the data contract should be marked with the [<xref:System.Runtime.Serialization.DataContractAttribute>] attribute.</span></span> <span data-ttu-id="cc60f-129">Hem istemci hem de sunucu için görünür olmasını istediğiniz bireysel özellikler veya alanlar [<xref:System.Runtime.Serialization.DataMemberAttribute>] özniteliğiyle işaretlenmelidir.</span><span class="sxs-lookup"><span data-stu-id="cc60f-129">The individual properties or fields you want visible to both client and server should be marked with the [<xref:System.Runtime.Serialization.DataMemberAttribute>] attribute.</span></span> <span data-ttu-id="cc60f-130">Veri sözleşmesindeki bir sınıftan türetilmiş türlerin izin verilmesini istiyorsanız, bunları [<xref:System.Runtime.Serialization.KnownTypeAttribute>] özniteliğiyle belirlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="cc60f-130">If you want types derived from a class in the data contract to be allowed, you must identify them with the [<xref:System.Runtime.Serialization.KnownTypeAttribute>] attribute.</span></span> <span data-ttu-id="cc60f-131">WCF yalnızca hizmet arabirimindeki türleri ve bilinen türler olarak tanımlanan türleri seri hale getir veya seri durumdan çıkaracaktır.</span><span class="sxs-lookup"><span data-stu-id="cc60f-131">WCF will only serialize or deserialize types in the service interface and types identified as known types.</span></span> <span data-ttu-id="cc60f-132">Bilinen bir tür olmayan bir türü kullanmaya çalışırsanız, bir özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="cc60f-132">If you attempt to use a type that is not a known type, an exception will occur.</span></span>  
  
 <span data-ttu-id="cc60f-133">Veri sözleşmeleri hakkında daha fazla bilgi için bkz. [veri sözleşmeleri](../wcf/samples/data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="cc60f-133">For more information about data contracts, see [Data Contracts](../wcf/samples/data-contracts.md).</span></span>  
  
```csharp  
[DataContract]  
[KnownType(typeof(PremiumCustomer))]  
public class Customer  
{  
    [DataMember]  
    public string Firstname;  
    [DataMember]  
    public string Lastname;  
    [DataMember]  
    public Address DefaultDeliveryAddress;  
    [DataMember]  
    public Address DefaultBillingAddress;  
}  
 [DataContract]  
public class PremiumCustomer : Customer  
{  
    [DataMember]  
    public int AccountID;  
}  
  
 [DataContract]  
public class Address  
{  
    [DataMember]  
    public string Street;  
    [DataMember]  
    public string Zipcode;  
    [DataMember]  
    public string City;  
    [DataMember]  
    public string State;  
    [DataMember]  
    public string Country;  
}  
```  
  
### <a name="step-3-implement-the-wcf-service"></a><span data-ttu-id="cc60f-134">3\. Adım: WCF hizmetini uygulama</span><span class="sxs-lookup"><span data-stu-id="cc60f-134">Step 3: Implement the WCF service</span></span>  
 <span data-ttu-id="cc60f-135">Ardından, önceki adımda tanımladığınız arabirimi uygulayan WCF hizmeti sınıfını uygulamalısınız.</span><span class="sxs-lookup"><span data-stu-id="cc60f-135">Next, you should implement the WCF service class that implements the interface you defined in the previous step.</span></span>  
  
```csharp  
public class CustomerService: ICustomerManager    
{  
    public void StoreCustomer(Customer customer)  
    {  
        // write to a database  
    }  
    public Customer GetCustomer(string firstName, string lastName)  
    {  
        // read from a database  
    }  
}  
```  
  
### <a name="step-4-configure-the-service-and-the-client"></a><span data-ttu-id="cc60f-136">4\. Adım: hizmeti ve istemciyi yapılandırma</span><span class="sxs-lookup"><span data-stu-id="cc60f-136">Step 4: Configure the service and the client</span></span>  
 <span data-ttu-id="cc60f-137">Bir WCF hizmetini çalıştırmak için belirli bir WCF bağlamasını kullanarak bu hizmet arabirimini belirli bir URL 'de kullanıma sunan bir uç nokta bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="cc60f-137">To run a WCF service, you need to declare an endpoint that exposes that service interface at a specific URL using a specific WCF binding.</span></span> <span data-ttu-id="cc60f-138">Bir bağlama, iletişim kuracak istemciler ve sunucu için Aktarım, kodlama ve protokol ayrıntılarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="cc60f-138">A binding specifies the transport, encoding and protocol details for the clients and server to communicate.</span></span> <span data-ttu-id="cc60f-139">Genellikle, hizmet projesinin yapılandırma dosyasına (Web. config) bağlama eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="cc60f-139">You typically add bindings to the service project’s configuration file (web.config).</span></span> <span data-ttu-id="cc60f-140">Aşağıda örnek hizmet için bir bağlama girişi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="cc60f-140">The following shows a binding entry for the example service:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="Server.CustomerService">  
        <endpoint address="http://localhost:8083/CustomerManager"   
                  binding="basicHttpBinding"  
                  contract="Shared.ICustomerManager" />  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="cc60f-141">Ardından, istemciyi, hizmet tarafından belirtilen bağlama bilgileriyle eşleşecek şekilde yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="cc60f-141">Next, you need to configure the client to match the binding information specified by the service.</span></span> <span data-ttu-id="cc60f-142">Bunu yapmak için, istemcinin uygulama yapılandırma (App. config) dosyasına aşağıdakini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cc60f-142">To do so, add the following to the client’s application configuration (app.config) file.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <endpoint name="customermanager"   
                address="http://localhost:8083/CustomerManager"   
                binding="basicHttpBinding"   
                contract="Shared.ICustomerManager"/>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="step-5-run-the-service"></a><span data-ttu-id="cc60f-143">5\. Adım: hizmeti çalıştırma</span><span class="sxs-lookup"><span data-stu-id="cc60f-143">Step 5: Run the service</span></span>  
 <span data-ttu-id="cc60f-144">Son olarak, hizmet uygulamasına aşağıdaki satırları ekleyerek ve uygulamayı başlatarak bir konsol uygulamasında kendi kendine barındırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cc60f-144">Finally, you can self-host it in a console application by adding the following lines to the service app, and starting the app.</span></span> <span data-ttu-id="cc60f-145">Bir WCF hizmet uygulamasını [barındırma hizmetleri, barındırma hizmetleri](../wcf/hosting-services.md)hakkında daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="cc60f-145">For more information about other ways to host a WCF service application, [Hosting Services](../wcf/hosting-services.md).</span></span>  
  
```csharp  
ServiceHost customerServiceHost = new ServiceHost(typeof(CustomerService));  
customerServiceHost.Open();  
```  
  
### <a name="step-6-call-the-service-from-the-client"></a><span data-ttu-id="cc60f-146">6\. Adım: istemciden hizmeti çağırma</span><span class="sxs-lookup"><span data-stu-id="cc60f-146">Step 6: Call the service from the client</span></span>  
 <span data-ttu-id="cc60f-147">Hizmeti istemciden çağırmak için, hizmet için bir kanal fabrikası oluşturmanız ve bir kanal istemeniz gerekir ve bu, doğrudan istemciden doğrudan `GetCustomer` yöntemini çağırmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="cc60f-147">To call the service from the client, you need to create a channel factory for the service, and request a channel, which will enable you to directly call the `GetCustomer` method directly from the client.</span></span> <span data-ttu-id="cc60f-148">Kanal, hizmetin arabirimini uygular ve temel alınan istek/yanıt mantığını sizin için işler.</span><span class="sxs-lookup"><span data-stu-id="cc60f-148">The channel implements the service’s interface and handles the underlying request/reply logic for you.</span></span>  <span data-ttu-id="cc60f-149">Bu yöntem çağrısından gelen dönüş değeri, hizmet yanıtının Serisi kaldırılan kopyasıdır.</span><span class="sxs-lookup"><span data-stu-id="cc60f-149">The return value from that method call is the deserialized copy of the service response.</span></span>  
  
```csharp  
ChannelFactory<ICustomerManager> factory =   
     new ChannelFactory<ICustomerManager>("customermanager");  
ICustomerManager service = factory.CreateChannel();  
Customer customer = service.GetCustomer("Mary", "Smith");  
```  
  
## <a name="the-client-sends-a-by-value-object-to-the-server"></a><span data-ttu-id="cc60f-150">İstemci sunucuya bir değere göre nesnesi gönderiyor</span><span class="sxs-lookup"><span data-stu-id="cc60f-150">The client sends a by-value object to the server</span></span>  
 <span data-ttu-id="cc60f-151">Bu senaryoda, istemci sunucuya bir nesne gönderir ve değeri göre.</span><span class="sxs-lookup"><span data-stu-id="cc60f-151">In this scenario, the client sends an object to the server, by-value.</span></span> <span data-ttu-id="cc60f-152">Bu, sunucunun, serisi kaldırılan nesnenin bir kopyasını alacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="cc60f-152">This means that the server will receive a deserialized copy of the object.</span></span>  <span data-ttu-id="cc60f-153">Sunucu söz konusu kopyada yöntemleri çağırabilir ve istemci koduna geri çağırma olmadığı garantisini alabilir.</span><span class="sxs-lookup"><span data-stu-id="cc60f-153">The server can call methods on that copy and be guaranteed there is no callback into client code.</span></span> <span data-ttu-id="cc60f-154">Daha önce belirtildiği gibi, verilerin normal WCF değişimlerinin değeri şunlardır.</span><span class="sxs-lookup"><span data-stu-id="cc60f-154">As mentioned previously, normal WCF exchanges of data are by-value.</span></span>  <span data-ttu-id="cc60f-155">Bu, bu nesnelerden birine çağırma yöntemlerinin yalnızca yerel olarak yürütüldüğünden emin olur; istemcide kod çağırmaz.</span><span class="sxs-lookup"><span data-stu-id="cc60f-155">This guarantees that calling methods on one of these objects executes locally only – it will not invoke code on the client.</span></span>  
  
 <span data-ttu-id="cc60f-156">Bu senaryo aşağıdaki COM yöntemi çağrısını temsil eder:</span><span class="sxs-lookup"><span data-stu-id="cc60f-156">This scenario represents the following COM method call:</span></span>  
  
```csharp  
public interface IRemoteService  
{  
    void SendObjectByValue(Customer customer);  
}  
```  
  
 <span data-ttu-id="cc60f-157">Bu senaryo, ilk örnekte gösterildiği gibi aynı hizmet arabirimini ve veri sözleşmesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="cc60f-157">This scenario uses the same service interface and data contract as shown in the first example.</span></span> <span data-ttu-id="cc60f-158">Ayrıca, istemci ve hizmet aynı şekilde yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="cc60f-158">In addition, the client and service will be configured in the same way.</span></span> <span data-ttu-id="cc60f-159">Bu örnekte, nesneyi göndermek ve aynı şekilde çalıştırmak için bir kanal oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="cc60f-159">In this example, a channel is created to send the object and run the same way.</span></span> <span data-ttu-id="cc60f-160">Ancak, bu örnekte, bir nesneyi değere göre geçirerek hizmeti çağıran bir istemci oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="cc60f-160">However, for this example, you will create a client that calls the service, passing an object by-value.</span></span> <span data-ttu-id="cc60f-161">İstemcinin hizmet sözleşmesinde çağırabilecek hizmet yöntemi kalın olarak gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="cc60f-161">The service method the client will call in the service contract is shown in bold:</span></span>  
  
```csharp  
[ServiceContract]  
public interface ICustomerManager  
{  
    [OperationContract]     void StoreCustomer(Customer customer);  
  
    [OperationContract]  
    Customer GetCustomer(string firstName, string lastName);  
}  
```  
  
### <a name="add-code-to-the-client-that-sends-a-by-value-object"></a><span data-ttu-id="cc60f-162">İstemciye değer nesnesi gönderen istemciye kod ekleme</span><span class="sxs-lookup"><span data-stu-id="cc60f-162">Add code to the client that sends a by-value object</span></span>  
 <span data-ttu-id="cc60f-163">Aşağıdaki kod, istemcisinin yeni bir değerli müşteri nesnesi nasıl oluşturduğunu gösterir, `ICustomerManager` hizmeti ile iletişim kurmak için bir kanal oluşturur ve müşteri nesnesini bu sunucuya gönderir.</span><span class="sxs-lookup"><span data-stu-id="cc60f-163">The following code shows how the client creates a new by-value customer object, creates a channel to communicate with the `ICustomerManager` service, and sends the customer object to it.</span></span>  
  
 <span data-ttu-id="cc60f-164">Müşteri nesnesi serileştirilir ve hizmete gönderilir; burada hizmet tarafından bu nesnenin yeni bir kopyasına kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="cc60f-164">The customer object will be serialized, and sent to the service, where it is deserialized by the service into a new copy of that object.</span></span>  <span data-ttu-id="cc60f-165">Bu nesne üzerindeki hizmet çağrılarının her türlü yöntemi yalnızca sunucuda yerel olarak yürütülür.</span><span class="sxs-lookup"><span data-stu-id="cc60f-165">Any methods the service calls on this object will execute only locally on the server.</span></span> <span data-ttu-id="cc60f-166">Bu kodun türetilmiş bir tür (`PremiumCustomer`) gönderdiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="cc60f-166">It’s important to note that this code illustrates sending a derived type (`PremiumCustomer`).</span></span>  <span data-ttu-id="cc60f-167">Hizmet sözleşmesi `Customer` nesnesi bekler, ancak hizmet veri anlaşması `PremiumCustomer` ' nin da izin verildiğini belirtmek için [<xref:System.Runtime.Serialization.KnownTypeAttribute>] özniteliğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="cc60f-167">The service contract expects a `Customer` object, but the service data contract uses the [<xref:System.Runtime.Serialization.KnownTypeAttribute>] attribute to indicate that `PremiumCustomer` is also allowed.</span></span>  <span data-ttu-id="cc60f-168">WCF, bu hizmet arabirimi aracılığıyla başka herhangi bir türü seri hale getirmeye veya seri durumdan çıkarmasına çalışır.</span><span class="sxs-lookup"><span data-stu-id="cc60f-168">WCF will fail attempts to serialize or deserialize any other type via this service interface.</span></span>  
  
```csharp  
PremiumCustomer customer = new PremiumCustomer();  
customer.Firstname = "John";  
customer.Lastname = "Doe";  
customer.DefaultBillingAddress = new Address();  
customer.DefaultBillingAddress.Street = "One Microsoft Way";  
customer.DefaultDeliveryAddress = customer.DefaultBillingAddress;  
customer.AccountID = 42;  
  
ChannelFactory<ICustomerManager> factory =  
   new ChannelFactory<ICustomerManager>("customermanager");  
ICustomerManager customerManager = factory.CreateChannel();  
customerManager.StoreCustomer(customer);  
```  
  
## <a name="the-service-returns-an-object-by-reference"></a><span data-ttu-id="cc60f-169">Hizmet, başvuruya göre bir nesne döndürüyor</span><span class="sxs-lookup"><span data-stu-id="cc60f-169">The service returns an object by reference</span></span>  
 <span data-ttu-id="cc60f-170">Bu senaryo için, istemci uygulaması uzak hizmete bir çağrı yapar ve yöntemi hizmetten istemciye başvuru ile geçirilen bir nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="cc60f-170">For this scenario, the client app makes a call to the remote service and the method returns an object, which is passed by reference from the service to the client.</span></span>  
  
 <span data-ttu-id="cc60f-171">Daha önce belirtildiği gibi, WCF Hizmetleri nesneyi her zaman değere göre döndürür.</span><span class="sxs-lookup"><span data-stu-id="cc60f-171">As mentioned previously, WCF services always return object by value.</span></span>  <span data-ttu-id="cc60f-172">Ancak, <xref:System.ServiceModel.EndpointAddress10> sınıfını kullanarak benzer bir sonuç elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cc60f-172">However, you can achieve a similar result by using the <xref:System.ServiceModel.EndpointAddress10> class.</span></span>  <span data-ttu-id="cc60f-173">@No__t-0, istemci tarafından sunucuda bir sessionby başvuruya göre nesne elde etmek için kullanılabilen, seri hale getirilebilir değer olan bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="cc60f-173">The <xref:System.ServiceModel.EndpointAddress10> is a serializable by-value object that can be used by the client to obtain a sessionful by-reference object on the server.</span></span>  
  
 <span data-ttu-id="cc60f-174">Bu senaryoda gösterilen WCF 'deki başvuruya göre nesnesinin davranışı, DCOM 'dan farklıdır.</span><span class="sxs-lookup"><span data-stu-id="cc60f-174">The behavior of the by-reference object in WCF shown in this scenario is different than DCOM.</span></span>  <span data-ttu-id="cc60f-175">DCOM 'da, sunucu istemciye doğrudan başvuruya göre bir nesne döndürebilir ve istemci, sunucuda yürütülen bu nesnenin yöntemlerini çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="cc60f-175">In DCOM, the server can return a by-reference object to the client directly, and the client can call that object’s methods, which execute on the server.</span></span>  <span data-ttu-id="cc60f-176">Ancak, WCF 'de döndürülen nesne her zaman değeri ile belirlenir.</span><span class="sxs-lookup"><span data-stu-id="cc60f-176">In WCF, however, the object returned is always by-value.</span></span>  <span data-ttu-id="cc60f-177">İstemci, <xref:System.ServiceModel.EndpointAddress10> ile temsil edilen bu değere göre nesneyi almalıdır ve kendi sessionby başvurusu nesnesini oluşturmak için onu kullanır.</span><span class="sxs-lookup"><span data-stu-id="cc60f-177">The client must take that by-value object, represented by <xref:System.ServiceModel.EndpointAddress10> and use it to create its own sessionful by-reference object.</span></span>  <span data-ttu-id="cc60f-178">İstemci yöntemi, sunucuda yürütülen oturumsuz nesneye çağrı yapılır. Diğer bir deyişle, WCF 'deki bu başvuruya göre bu nesne, sessionmek üzere yapılandırılmış normal bir WCF hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="cc60f-178">The client method calls on the sessionful object execute on the server.In other words, this by-reference object in WCF is a normal WCF service that is configured to be sessionful.</span></span>  
  
 <span data-ttu-id="cc60f-179">WCF 'de oturum, iki uç nokta arasında gönderilen birden fazla iletiyi eş bir şekilde ilişkilendirme yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="cc60f-179">In WCF, a session is a way of correlating multiple messages sent between two endpoints.</span></span>  <span data-ttu-id="cc60f-180">Bu, bir istemci bu hizmete bir bağlantı edinirse, istemci ile sunucu arasında bir oturum kurulacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="cc60f-180">This means that once a client obtains a connection to this service, a session will be established between the client and the server.</span></span>  <span data-ttu-id="cc60f-181">İstemci, bu tek oturumdaki tüm etkileşimleri için sunucu tarafı nesnesinin tek bir benzersiz örneğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="cc60f-181">The client will use a single unique instance of the server-side object for all its interactions within this single session.</span></span> <span data-ttu-id="cc60f-182">Oturumsuz WCF sözleşmeleri, bağlantıya dayalı ağ isteği/yanıt desenlerine benzer.</span><span class="sxs-lookup"><span data-stu-id="cc60f-182">Sessionful WCF contracts are similar to connection-oriented network request/response patterns.</span></span>  
  
 <span data-ttu-id="cc60f-183">Bu senaryo, aşağıdaki DCOM yöntemiyle temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="cc60f-183">This scenario is represented by the following DCOM method.</span></span>  
  
```csharp  
public interface IRemoteService  
{  
    IRemoteObject GetObjectByReference();  
}  
```  
  
### <a name="step-1-define-the-sessionful-wcf-service-interface-and-implementation"></a><span data-ttu-id="cc60f-184">1\. Adım: oturumsuz WCF hizmeti arabirimini ve uygulamasını tanımlama</span><span class="sxs-lookup"><span data-stu-id="cc60f-184">Step 1: Define the Sessionful WCF service interface and implementation</span></span>  
 <span data-ttu-id="cc60f-185">İlk olarak, sessionobject nesnesini içeren bir WCF hizmeti arabirimi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="cc60f-185">First, define a WCF service interface that contains the sessionful object.</span></span>  
  
 <span data-ttu-id="cc60f-186">Bu kodda, sessionobject nesnesi, normal bir WCF hizmeti arabirimi olarak tanımlayan `ServiceContract` özniteliğiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="cc60f-186">In this code, the sessionful object is marked with the `ServiceContract` attribute, which identifies it as a regular WCF service interface.</span></span>  <span data-ttu-id="cc60f-187">Ayrıca, <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> özelliği, oturum bir hizmet olacağını belirtecek şekilde ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="cc60f-187">In addition, the <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> property is set to indicate it will be a sessionful service.</span></span>  
  
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
  
 <span data-ttu-id="cc60f-188">Aşağıdaki kod, hizmet uygulamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="cc60f-188">The following code shows the service implementation.</span></span>  
  
 <span data-ttu-id="cc60f-189">Hizmet, [ServiceBehavior] özniteliğiyle işaretlenir ve InstanceContextMode özelliği, her oturum için bu türün benzersiz bir örneğinin oluşturulması gerektiğini belirtmek için InstanceContextMode. PerSessions olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="cc60f-189">The service is marked with the [ServiceBehavior] attribute, and its InstanceContextMode property set to InstanceContextMode.PerSessions to indicate that a unique instance of this type should be created for each session.</span></span>  
  
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
  
### <a name="step-2-define-the-wcf-factory-service-for-the-sessionful-object"></a><span data-ttu-id="cc60f-190">2\. Adım: oturumsuz nesne için WCF fabrikası hizmetini tanımlama</span><span class="sxs-lookup"><span data-stu-id="cc60f-190">Step 2: Define the WCF factory service for the sessionful object</span></span>  
 <span data-ttu-id="cc60f-191">Oturumsuz nesneyi oluşturan hizmetin tanımlanması ve uygulanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="cc60f-191">The service that creates the sessionful object must be defined and implemented.</span></span> <span data-ttu-id="cc60f-192">Aşağıdaki kod bunun nasıl yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="cc60f-192">The following code shows how to do this.</span></span> <span data-ttu-id="cc60f-193">Bu kod, <xref:System.ServiceModel.EndpointAddress10> nesnesi döndüren başka bir WCF hizmeti oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cc60f-193">This code creates another WCF service that returns an <xref:System.ServiceModel.EndpointAddress10> object.</span></span>  <span data-ttu-id="cc60f-194">Bu, oturum tam nesnesini oluşturmak için kullanabileceği bir uç noktanın seri hale getirilebilir bir biçimidir.</span><span class="sxs-lookup"><span data-stu-id="cc60f-194">This is a serializable form of an endpoint the can use to create the session-full object.</span></span>  
  
```csharp  
[ServiceContract]  
    public interface ISessionBoundFactory  
    {  
        [OperationContract]  
        EndpointAddress10 GetInstanceAddress();  
    }  
```  
  
 <span data-ttu-id="cc60f-195">Bu hizmetin uygulanması aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="cc60f-195">The following is the implementation of this service.</span></span> <span data-ttu-id="cc60f-196">Bu uygulama, oturumsuz nesneler oluşturmak için tek bir kanal fabrikası sağlar.</span><span class="sxs-lookup"><span data-stu-id="cc60f-196">This implementation maintains a singleton channel factory to create sessionful objects.</span></span>  <span data-ttu-id="cc60f-197">@No__t-0 çağrıldığında, bir kanal oluşturur ve bu kanalla ilişkili uzak adresi işaret eden bir <xref:System.ServiceModel.EndpointAddress10> nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cc60f-197">When `GetInstanceAddress` is called, it creates a channel and creates an <xref:System.ServiceModel.EndpointAddress10> object that points to the remote address associated with this channel.</span></span>   <span data-ttu-id="cc60f-198"><xref:System.ServiceModel.EndpointAddress10>, istemciye değere göre döndürülebilecek bir veri türüdür.</span><span class="sxs-lookup"><span data-stu-id="cc60f-198"><xref:System.ServiceModel.EndpointAddress10> is a data type that can be returned to the client by-value.</span></span>
  
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
  
### <a name="step-3-configure-and-start-the-wcf-services"></a><span data-ttu-id="cc60f-199">3\. Adım: WCF hizmetlerini yapılandırma ve başlatma</span><span class="sxs-lookup"><span data-stu-id="cc60f-199">Step 3: Configure and start the WCF services</span></span>  
 <span data-ttu-id="cc60f-200">Bu hizmetleri barındırmak için, sunucunun yapılandırma dosyasına (Web. config) aşağıdaki eklemeleri yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="cc60f-200">To host these services, you will need to make the following additions to the server’s configuration file (web.config).</span></span>  
  
1. <span data-ttu-id="cc60f-201">Sessionobject nesnesinin bitiş noktasını açıklayan `<client>` bölümü ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cc60f-201">Add a `<client>` section that describes the endpoint for the sessionful object.</span></span>  <span data-ttu-id="cc60f-202">Bu senaryoda, sunucu istemci olarak da çalışır ve bunu etkinleştirmek üzere yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="cc60f-202">In this scenario, the server also acts as a client and must be configured to enable this.</span></span>  
  
2. <span data-ttu-id="cc60f-203">@No__t-0 bölümünde, fabrika ve oturumsuz nesnenin hizmet uç noktalarını bildirin.</span><span class="sxs-lookup"><span data-stu-id="cc60f-203">In the `<services>` section, declare service endpoints for the factory and sessionful object.</span></span>  <span data-ttu-id="cc60f-204">Bu, istemcinin hizmet uç noktalarıyla iletişim kurmasını sağlar, <xref:System.ServiceModel.EndpointAddress10> ' ı alın ve Oturumsuz kanalı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cc60f-204">This enables the client to communicate with the service endpoints, acquire the <xref:System.ServiceModel.EndpointAddress10> and create the sessionful channel.</span></span>  
  
 <span data-ttu-id="cc60f-205">Aşağıdaki ayarlara sahip örnek bir yapılandırma dosyası aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="cc60f-205">The following is an example configuration file with these settings:</span></span>  
  
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
  
 <span data-ttu-id="cc60f-206">Bir konsol uygulamasına, hizmeti kendinden barındırmak ve uygulamayı başlatmak için aşağıdaki satırları ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cc60f-206">Add the following lines to a console application, to self-host the service, and start the app.</span></span>  
  
```csharp  
ServiceHost factoryHost = new ServiceHost(typeof(SessionBoundFactory));  
factoryHost.Open();  
  
ServiceHost sessionBoundServiceHost = new ServiceHost(  
typeof(MySessionBoundObject));  
sessionBoundServiceHost.Open();  
```  
  
### <a name="step-4-configure-the-client-and-call-the-service"></a><span data-ttu-id="cc60f-207">4\. Adım: istemciyi yapılandırma ve hizmeti çağırma</span><span class="sxs-lookup"><span data-stu-id="cc60f-207">Step 4: Configure the client and call the service</span></span>  
 <span data-ttu-id="cc60f-208">İstemcisini, projenin uygulama yapılandırma dosyasında (App. config) aşağıdaki girişleri yaparak WCF hizmetleriyle iletişim kuracak şekilde yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="cc60f-208">Configure the client to communicate with the WCF services by making the following entries in the project’s application configuration file (app.config).</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
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
  
 <span data-ttu-id="cc60f-209">Hizmeti çağırmak için, aşağıdakileri yapmak üzere istemciye kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="cc60f-209">To call the service, add the code to the client to do the following:</span></span>  
  
1. <span data-ttu-id="cc60f-210">@No__t-0 hizmetine bir kanal oluşturun.</span><span class="sxs-lookup"><span data-stu-id="cc60f-210">Create a channel to the `ISessionBoundFactory` service.</span></span>  
  
2. <span data-ttu-id="cc60f-211">@No__t-0 hizmetini çağırmak için kanalı kullanın <xref:System.ServiceModel.EndpointAddress10> nesnesi edinin.</span><span class="sxs-lookup"><span data-stu-id="cc60f-211">Use the channel to invoke the `ISessionBoundFactory` service an obtain an <xref:System.ServiceModel.EndpointAddress10> object.</span></span>  
  
3. <span data-ttu-id="cc60f-212">Oturumsuz bir nesne elde etmek üzere bir kanal oluşturmak için <xref:System.ServiceModel.EndpointAddress10> kullanın.</span><span class="sxs-lookup"><span data-stu-id="cc60f-212">Use the <xref:System.ServiceModel.EndpointAddress10> to create a channel to obtain a sessionful object.</span></span>  
  
4. <span data-ttu-id="cc60f-213">Birden çok çağrıda aynı nesne örneğinin kullanıldığını göstermek için `SetCurrentValue` ve `GetCurrentValue` yöntemlerini çağırın.</span><span class="sxs-lookup"><span data-stu-id="cc60f-213">Call the `SetCurrentValue` and `GetCurrentValue` methods to demonstrate it remains the same object instance is used across multiple calls.</span></span>  
  
```csharp  
ChannelFactory<ISessionBoundFactory> factory =  
        new ChannelFactory<ISessionBoundFactory>("factory");  
  
ISessionBoundFactory sessionBoundFactory = factory.CreateChannel();  
  
EndpointAddress10 address = sessionBoundFactory.GetInstanceAddress();  
  
ChannelFactory<ISessionBoundObject> sessionBoundObjectFactory =  
    new ChannelFactory<ISessionBoundObject>(  
        new NetTcpBinding(),  
        address.ToEndpointAddress());  
  
ISessionBoundObject sessionBoundObject =  
        sessionBoundObjectFactory.CreateChannel();  
  
sessionBoundObject.SetCurrentValue("Hello");  
if (sessionBoundObject.GetCurrentValue() == "Hello")  
{  
    Console.WriteLine("Session-full instance management works as expected");  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="cc60f-214">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cc60f-214">See also</span></span>

- [<span data-ttu-id="cc60f-215">Temel WCF programlama</span><span class="sxs-lookup"><span data-stu-id="cc60f-215">Basic WCF Programming</span></span>](../wcf/basic-wcf-programming.md)
- [<span data-ttu-id="cc60f-216">Hizmetleri tasarlama ve uygulama</span><span class="sxs-lookup"><span data-stu-id="cc60f-216">Designing and Implementing Services</span></span>](../wcf/designing-and-implementing-services.md)
- [<span data-ttu-id="cc60f-217">Istemcileri derleme</span><span class="sxs-lookup"><span data-stu-id="cc60f-217">Building Clients</span></span>](../wcf/building-clients.md)
- [<span data-ttu-id="cc60f-218">Çift yönlü hizmetler</span><span class="sxs-lookup"><span data-stu-id="cc60f-218">Duplex Services</span></span>](../wcf/feature-details/duplex-services.md)
