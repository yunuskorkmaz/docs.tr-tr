---
title: 'Nasıl yapılır: Yönetilen Kodu DCOM’dan WCF’ye Geçirme'
ms.date: 03/30/2017
ms.assetid: 52961ffc-d1c7-4f83-832c-786444b951ba
ms.openlocfilehash: 2576e88c25ae381e90ec7d613efb648048145b3b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181385"
---
# <a name="how-to-migrate-managed-code-dcom-to-wcf"></a><span data-ttu-id="424c9-102">Nasıl yapılır: Yönetilen Kodu DCOM’dan WCF’ye Geçirme</span><span class="sxs-lookup"><span data-stu-id="424c9-102">How to: Migrate Managed-Code DCOM to WCF</span></span>
<span data-ttu-id="424c9-103">Windows Communication Foundation (WCF), dağıtılmış bir ortamda sunucular ve istemciler arasında yönetilen kod çağrıları için Dağıtılmış Bileşen Nesne Modeli (DCOM) yerine önerilen ve güvenli bir seçimdir.</span><span class="sxs-lookup"><span data-stu-id="424c9-103">Windows Communication Foundation (WCF) is the recommended and secure choice over Distributed Component Object Model (DCOM) for managed code calls between servers and clients in a distributed environment.</span></span> <span data-ttu-id="424c9-104">Bu makalede, aşağıdaki senaryolar için dcom'dan WCF'ye kodu nasıl geçirtilebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="424c9-104">This article shows how you to migrate code from DCOM to WCF for the following scenarios.</span></span>  
  
- <span data-ttu-id="424c9-105">Uzak hizmet, bir nesneyi istemciye göre döndürür</span><span class="sxs-lookup"><span data-stu-id="424c9-105">The remote service returns an object by-value to the client</span></span>  
  
- <span data-ttu-id="424c9-106">İstemci uzak hizmete bir nesneyi by-value gönderir</span><span class="sxs-lookup"><span data-stu-id="424c9-106">The client sends an object by-value to the remote service</span></span>  
  
- <span data-ttu-id="424c9-107">Uzak hizmet istemciye bir nesne by-reference döndürür</span><span class="sxs-lookup"><span data-stu-id="424c9-107">The remote service returns an object by-reference to the client</span></span>  
  
 <span data-ttu-id="424c9-108">Güvenlik nedenleriyle, istemciden hizmete bir nesne nin gönderilmesine WCF'de izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="424c9-108">For security reasons, sending an object by-reference from the client to the service is not allowed in WCF.</span></span> <span data-ttu-id="424c9-109">İstemci ve sunucu arasında ileri geri görüşme gerektiren bir senaryo, çift yönlü bir hizmet kullanılarak WCF'de elde edilebilir.</span><span class="sxs-lookup"><span data-stu-id="424c9-109">A scenario that requires a conversation back and forth between client and server can be achieved in WCF using a duplex service.</span></span>  <span data-ttu-id="424c9-110">Çift yönlü hizmetler hakkında daha fazla bilgi için [Bkz. Çift Yönlü Hizmetler.](../wcf/feature-details/duplex-services.md)</span><span class="sxs-lookup"><span data-stu-id="424c9-110">For more information about duplex services, see [Duplex Services](../wcf/feature-details/duplex-services.md).</span></span>  
  
 <span data-ttu-id="424c9-111">WCF hizmetleri ve bu hizmetler için istemcioluşturma hakkında daha fazla bilgi için, [Temel WCF Programlama,](../wcf/basic-wcf-programming.md) [Tasarım ve Hizmetleri Uygulama](../wcf/designing-and-implementing-services.md)ve Bina [İstemcibölümü'ne](../wcf/building-clients.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="424c9-111">For more details about creating WCF services and clients for those services, see [Basic WCF Programming](../wcf/basic-wcf-programming.md), [Designing and Implementing Services](../wcf/designing-and-implementing-services.md), and [Building Clients](../wcf/building-clients.md).</span></span>  
  
## <a name="dcom-example-code"></a><span data-ttu-id="424c9-112">DCOM örnek kodu</span><span class="sxs-lookup"><span data-stu-id="424c9-112">DCOM example code</span></span>  
 <span data-ttu-id="424c9-113">Bu senaryolar için, WCF kullanılarak resimlenen DCOM arabirimleri aşağıdaki yapıya sahiptir:</span><span class="sxs-lookup"><span data-stu-id="424c9-113">For these scenarios, the DCOM interfaces that are illustrated using WCF have the following structure:</span></span>  
  
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
  
## <a name="the-service-returns-an-object-by-value"></a><span data-ttu-id="424c9-114">Hizmet nesneyi değere göre döndürür</span><span class="sxs-lookup"><span data-stu-id="424c9-114">The service returns an object by-value</span></span>  
 <span data-ttu-id="424c9-115">Bu senaryo için, bir hizmete çağrı yaparsınız ve bu yöntem sunucudan istemciye göre geçirilen bir nesneyi döndürür.</span><span class="sxs-lookup"><span data-stu-id="424c9-115">For this scenario, you make a call to a service and it method returns an object, which is passed by-value from the server to the client.</span></span> <span data-ttu-id="424c9-116">Bu senaryo aşağıdaki COM çağrısını temsil eder:</span><span class="sxs-lookup"><span data-stu-id="424c9-116">This scenario represents the following COM call:</span></span>  
  
```csharp  
public interface IRemoteService  
{  
    Customer GetObjectByValue();  
}  
```  
  
 <span data-ttu-id="424c9-117">Bu senaryoda, istemci uzak hizmetten bir nesnenin deserialized kopyasını alır.</span><span class="sxs-lookup"><span data-stu-id="424c9-117">In this scenario, the client receives a deserialized copy of an object from the remote service.</span></span> <span data-ttu-id="424c9-118">İstemci, hizmete geri çağırmadan bu yerel kopyayla etkileşim kurabilir.</span><span class="sxs-lookup"><span data-stu-id="424c9-118">The client can interact with this local copy without calling back to the service.</span></span>  <span data-ttu-id="424c9-119">Başka bir deyişle, istemci, yerel kopyadaki yöntemler çağrıldığında hizmetin hiçbir şekilde dahil olmayacağını garanti edecektir.</span><span class="sxs-lookup"><span data-stu-id="424c9-119">In other words, the client is guaranteed the service will not be involved in any way when methods on the local copy are called.</span></span> <span data-ttu-id="424c9-120">WCF nesneleri her zaman hizmetten değere göre döndürür, bu nedenle aşağıdaki adımlar normal bir WCF hizmeti oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="424c9-120">WCF always returns objects from the service by value, so the following steps describe creating a regular WCF service.</span></span>  
  
### <a name="step-1-define-the-wcf-service-interface"></a><span data-ttu-id="424c9-121">Adım 1: WCF hizmet arabirimini tanımlayın</span><span class="sxs-lookup"><span data-stu-id="424c9-121">Step 1: Define the WCF service interface</span></span>  
 <span data-ttu-id="424c9-122">WCF hizmeti için ortak bir arabirim tanımlayın ve []<xref:System.ServiceModel.ServiceContractAttribute>özniteliğiyle işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="424c9-122">Define a public interface for the WCF service and mark it with the [<xref:System.ServiceModel.ServiceContractAttribute>] attribute.</span></span>  <span data-ttu-id="424c9-123">[ ]<xref:System.ServiceModel.OperationContractAttribute>özniteliği ile istemcilere maruz bırakmak istediğiniz yöntemleri işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="424c9-123">Mark the methods you want to expose to clients with the [<xref:System.ServiceModel.OperationContractAttribute>] attribute.</span></span> <span data-ttu-id="424c9-124">Aşağıdaki örnek, sunucu tarafı arabirimini ve istemcinin çağırabileceği arabirim yöntemlerini tanımlamak için bu öznitelikleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="424c9-124">The following example shows using these attributes to identify the server-side interface and interface methods a client can call.</span></span> <span data-ttu-id="424c9-125">Bu senaryo için kullanılan yöntem kalın olarak gösterilir.</span><span class="sxs-lookup"><span data-stu-id="424c9-125">The method used for this scenario is shown in bold.</span></span>  
  
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
  
### <a name="step-2-define-the-data-contract"></a><span data-ttu-id="424c9-126">Adım 2: Veri sözleşmesini tanımlama</span><span class="sxs-lookup"><span data-stu-id="424c9-126">Step 2: Define the data contract</span></span>  
 <span data-ttu-id="424c9-127">Ardından, hizmet ve istemcileri arasında verilerin nasıl değiş tokuş edileceğini açıklayan bir veri sözleşmesi oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="424c9-127">Next you should create a data contract for the service, which will describe how the data will be exchanged between the service and its clients.</span></span>  <span data-ttu-id="424c9-128">Veri sözleşmesinde açıklanan sınıflar [ ]<xref:System.Runtime.Serialization.DataContractAttribute>özniteliği ile işaretlenmelidir.</span><span class="sxs-lookup"><span data-stu-id="424c9-128">Classes described in the data contract should be marked with the [<xref:System.Runtime.Serialization.DataContractAttribute>] attribute.</span></span> <span data-ttu-id="424c9-129">Hem istemci hem de sunucu tarafından görülebilmesini istediğiniz tek<xref:System.Runtime.Serialization.DataMemberAttribute>tek özellikler veya alanlar [ ] özniteliği ile işaretlenmelidir.</span><span class="sxs-lookup"><span data-stu-id="424c9-129">The individual properties or fields you want visible to both client and server should be marked with the [<xref:System.Runtime.Serialization.DataMemberAttribute>] attribute.</span></span> <span data-ttu-id="424c9-130">Veri sözleşmesinde bir sınıftan türetilen türlerin izin verilmesini istiyorsanız,<xref:System.Runtime.Serialization.KnownTypeAttribute>bunları [ ] özniteliğiyle tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="424c9-130">If you want types derived from a class in the data contract to be allowed, you must identify them with the [<xref:System.Runtime.Serialization.KnownTypeAttribute>] attribute.</span></span> <span data-ttu-id="424c9-131">WCF yalnızca hizmet arabirimindeki türleri ve bilinen türler olarak tanımlanan türleri serihale veya deserialize eder.</span><span class="sxs-lookup"><span data-stu-id="424c9-131">WCF will only serialize or deserialize types in the service interface and types identified as known types.</span></span> <span data-ttu-id="424c9-132">Bilinen bir tür olmayan bir tür kullanmaya çalışırsanız, bir özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="424c9-132">If you attempt to use a type that is not a known type, an exception will occur.</span></span>  
  
 <span data-ttu-id="424c9-133">Veri sözleşmeleri hakkında daha fazla bilgi için [Bkz. Veri Sözleşmeleri.](../wcf/samples/data-contracts.md)</span><span class="sxs-lookup"><span data-stu-id="424c9-133">For more information about data contracts, see [Data Contracts](../wcf/samples/data-contracts.md).</span></span>  
  
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
  
### <a name="step-3-implement-the-wcf-service"></a><span data-ttu-id="424c9-134">Adım 3: WCF hizmetini uygulayın</span><span class="sxs-lookup"><span data-stu-id="424c9-134">Step 3: Implement the WCF service</span></span>  
 <span data-ttu-id="424c9-135">Ardından, önceki adımda tanımladığınız arabirimi uygulayan WCF hizmet sınıfını uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="424c9-135">Next, you should implement the WCF service class that implements the interface you defined in the previous step.</span></span>  
  
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
  
### <a name="step-4-configure-the-service-and-the-client"></a><span data-ttu-id="424c9-136">Adım 4: Hizmeti ve istemciyi yapılandır</span><span class="sxs-lookup"><span data-stu-id="424c9-136">Step 4: Configure the service and the client</span></span>  
 <span data-ttu-id="424c9-137">Bir WCF hizmetini çalıştırmak için, belirli bir WCF bağlama kullanarak bu hizmet arabirimini belirli bir URL'de gösteren bir bitiş noktası bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="424c9-137">To run a WCF service, you need to declare an endpoint that exposes that service interface at a specific URL using a specific WCF binding.</span></span> <span data-ttu-id="424c9-138">Bağlama, istemcilerin ve sunucunun iletişim kurması için aktarım, kodlama ve protokol ayrıntılarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="424c9-138">A binding specifies the transport, encoding and protocol details for the clients and server to communicate.</span></span> <span data-ttu-id="424c9-139">Genellikle hizmet projesinin yapılandırma dosyasına (web.config) bağlamalar eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="424c9-139">You typically add bindings to the service project’s configuration file (web.config).</span></span> <span data-ttu-id="424c9-140">Aşağıdaki örnek hizmet için bağlayıcı bir giriş gösterir:</span><span class="sxs-lookup"><span data-stu-id="424c9-140">The following shows a binding entry for the example service:</span></span>  
  
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
  
 <span data-ttu-id="424c9-141">Ardından, istemciyi hizmet tarafından belirtilen bağlama bilgileriyle eşleşecek şekilde yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="424c9-141">Next, you need to configure the client to match the binding information specified by the service.</span></span> <span data-ttu-id="424c9-142">Bunu yapmak için, istemcinin uygulama yapılandırmasına (app.config) aşağıdakileri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="424c9-142">To do so, add the following to the client’s application configuration (app.config) file.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <endpoint name="customermanager"
                address="http://localhost:8083/CustomerManager"
                binding="basicHttpBinding"
                contract="Shared.ICustomerManager"/>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="step-5-run-the-service"></a><span data-ttu-id="424c9-143">Adım 5: Hizmeti çalıştırın</span><span class="sxs-lookup"><span data-stu-id="424c9-143">Step 5: Run the service</span></span>  
 <span data-ttu-id="424c9-144">Son olarak, servis uygulamasına aşağıdaki satırları ekleyerek ve uygulamayı başlatarak konsol uygulamasında kendi kendine barındırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="424c9-144">Finally, you can self-host it in a console application by adding the following lines to the service app, and starting the app.</span></span> <span data-ttu-id="424c9-145">Bir WCF hizmet uygulaması barındırmak için diğer yollar hakkında daha fazla bilgi için, [Hosting Hizmetleri](../wcf/hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="424c9-145">For more information about other ways to host a WCF service application, [Hosting Services](../wcf/hosting-services.md).</span></span>  
  
```csharp  
ServiceHost customerServiceHost = new ServiceHost(typeof(CustomerService));  
customerServiceHost.Open();  
```  
  
### <a name="step-6-call-the-service-from-the-client"></a><span data-ttu-id="424c9-146">Adım 6: Hizmeti istemciden arayın</span><span class="sxs-lookup"><span data-stu-id="424c9-146">Step 6: Call the service from the client</span></span>  
 <span data-ttu-id="424c9-147">Hizmeti istemciden aramak için, hizmet için bir kanal fabrikası oluşturmanız ve `GetCustomer` yöntemi doğrudan istemciden doğrudan aramanızı sağlayacak bir kanal istemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="424c9-147">To call the service from the client, you need to create a channel factory for the service, and request a channel, which will enable you to directly call the `GetCustomer` method directly from the client.</span></span> <span data-ttu-id="424c9-148">Kanal, hizmetin arabirimini uygular ve sizin için temel istek/yanıt mantığını işler.</span><span class="sxs-lookup"><span data-stu-id="424c9-148">The channel implements the service’s interface and handles the underlying request/reply logic for you.</span></span>  <span data-ttu-id="424c9-149">Bu yöntem çağrısından gelen iade değeri, hizmet yanıtının deserialized kopyasıdır.</span><span class="sxs-lookup"><span data-stu-id="424c9-149">The return value from that method call is the deserialized copy of the service response.</span></span>  
  
```csharp  
ChannelFactory<ICustomerManager> factory =
     new ChannelFactory<ICustomerManager>("customermanager");  
ICustomerManager service = factory.CreateChannel();  
Customer customer = service.GetCustomer("Mary", "Smith");  
```  
  
## <a name="the-client-sends-a-by-value-object-to-the-server"></a><span data-ttu-id="424c9-150">İstemci sunucuya bir by-value nesnesi gönderir</span><span class="sxs-lookup"><span data-stu-id="424c9-150">The client sends a by-value object to the server</span></span>  
 <span data-ttu-id="424c9-151">Bu senaryoda, istemci sunucuya bir nesne gönderir, yan değer.</span><span class="sxs-lookup"><span data-stu-id="424c9-151">In this scenario, the client sends an object to the server, by-value.</span></span> <span data-ttu-id="424c9-152">Bu, sunucunun nesnenin deserialized kopyasını alacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="424c9-152">This means that the server will receive a deserialized copy of the object.</span></span>  <span data-ttu-id="424c9-153">Sunucu bu kopyadaki yöntemleri arayabilir ve istemci koduna geri arama yapılmadığını garanti edebilir.</span><span class="sxs-lookup"><span data-stu-id="424c9-153">The server can call methods on that copy and be guaranteed there is no callback into client code.</span></span> <span data-ttu-id="424c9-154">Daha önce de belirtildiği gibi, normal WCF veri değişimleri ayrı değerdir.</span><span class="sxs-lookup"><span data-stu-id="424c9-154">As mentioned previously, normal WCF exchanges of data are by-value.</span></span>  <span data-ttu-id="424c9-155">Bu, bu nesnelerden birinde arama yöntemlerinin yalnızca yerel olarak yürütüleceğini garanti eder – istemciye kod çağırmaz.</span><span class="sxs-lookup"><span data-stu-id="424c9-155">This guarantees that calling methods on one of these objects executes locally only – it will not invoke code on the client.</span></span>  
  
 <span data-ttu-id="424c9-156">Bu senaryo aşağıdaki COM yöntemi çağrısını temsil eder:</span><span class="sxs-lookup"><span data-stu-id="424c9-156">This scenario represents the following COM method call:</span></span>  
  
```csharp  
public interface IRemoteService  
{  
    void SendObjectByValue(Customer customer);  
}  
```  
  
 <span data-ttu-id="424c9-157">Bu senaryo, ilk örnekte gösterildiği gibi aynı hizmet arabirimi ve veri sözleşmesi kullanır.</span><span class="sxs-lookup"><span data-stu-id="424c9-157">This scenario uses the same service interface and data contract as shown in the first example.</span></span> <span data-ttu-id="424c9-158">Buna ek olarak, istemci ve hizmet aynı şekilde yapılandırılacaktır.</span><span class="sxs-lookup"><span data-stu-id="424c9-158">In addition, the client and service will be configured in the same way.</span></span> <span data-ttu-id="424c9-159">Bu örnekte, nesneyi göndermek ve aynı şekilde çalıştırmak için bir kanal oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="424c9-159">In this example, a channel is created to send the object and run the same way.</span></span> <span data-ttu-id="424c9-160">Ancak, bu örnek için, bir nesneyi değere göre geçirerek hizmeti çağıran bir istemci oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="424c9-160">However, for this example, you will create a client that calls the service, passing an object by-value.</span></span> <span data-ttu-id="424c9-161">İstemcinin hizmet sözleşmesinde çağıracağı hizmet yöntemi kalın olarak gösterilir:</span><span class="sxs-lookup"><span data-stu-id="424c9-161">The service method the client will call in the service contract is shown in bold:</span></span>  
  
```csharp  
[ServiceContract]  
public interface ICustomerManager  
{  
    [OperationContract]     void StoreCustomer(Customer customer);  
  
    [OperationContract]  
    Customer GetCustomer(string firstName, string lastName);  
}  
```  
  
### <a name="add-code-to-the-client-that-sends-a-by-value-object"></a><span data-ttu-id="424c9-162">Bir yan değer nesnesi gönderen istemciye kod ekleme</span><span class="sxs-lookup"><span data-stu-id="424c9-162">Add code to the client that sends a by-value object</span></span>  
 <span data-ttu-id="424c9-163">Aşağıdaki kod, istemcinin yeni bir yan değer müşteri nesnesi nasıl oluşturduğunu, `ICustomerManager` hizmetle iletişim kurmak için bir kanal oluşturduğunu ve müşteri nesnesini bu nesneye nasıl gönderdiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="424c9-163">The following code shows how the client creates a new by-value customer object, creates a channel to communicate with the `ICustomerManager` service, and sends the customer object to it.</span></span>  
  
 <span data-ttu-id="424c9-164">Müşteri nesnesi seri hale getirilecek ve hizmete gönderilir ve bu nesnenin yeni bir kopyasına hizmet tarafından deserialized.</span><span class="sxs-lookup"><span data-stu-id="424c9-164">The customer object will be serialized, and sent to the service, where it is deserialized by the service into a new copy of that object.</span></span>  <span data-ttu-id="424c9-165">Hizmetin bu nesne üzerinde çağırdığı tüm yöntemler yalnızca sunucuda yerel olarak yürütülür.</span><span class="sxs-lookup"><span data-stu-id="424c9-165">Any methods the service calls on this object will execute only locally on the server.</span></span> <span data-ttu-id="424c9-166">Bu kodun türetilmiş bir türü ( )`PremiumCustomer`göndermeyi gösterdiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="424c9-166">It’s important to note that this code illustrates sending a derived type (`PremiumCustomer`).</span></span>  <span data-ttu-id="424c9-167">Hizmet sözleşmesi bir `Customer` nesne bekler, ancak hizmet<xref:System.Runtime.Serialization.KnownTypeAttribute>veri söylecisi de izin `PremiumCustomer` verildiğini belirtmek için [ ] özniteliğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="424c9-167">The service contract expects a `Customer` object, but the service data contract uses the [<xref:System.Runtime.Serialization.KnownTypeAttribute>] attribute to indicate that `PremiumCustomer` is also allowed.</span></span>  <span data-ttu-id="424c9-168">WCF, bu hizmet arabirimi aracılığıyla başka bir türü serileştirme veya deserialize etme girişimlerinde başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="424c9-168">WCF will fail attempts to serialize or deserialize any other type via this service interface.</span></span>  
  
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
  
## <a name="the-service-returns-an-object-by-reference"></a><span data-ttu-id="424c9-169">Hizmet başvuru ile bir nesne döndürür</span><span class="sxs-lookup"><span data-stu-id="424c9-169">The service returns an object by reference</span></span>  
 <span data-ttu-id="424c9-170">Bu senaryo için, istemci uygulaması uzak hizmeti bir çağrı yapar ve yöntem istemciye hizmetten başvuru ile geçirilen bir nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="424c9-170">For this scenario, the client app makes a call to the remote service and the method returns an object, which is passed by reference from the service to the client.</span></span>  
  
 <span data-ttu-id="424c9-171">Daha önce de belirtildiği gibi, WCF hizmetleri her zaman nesneyi değerolarak döndürer.</span><span class="sxs-lookup"><span data-stu-id="424c9-171">As mentioned previously, WCF services always return object by value.</span></span>  <span data-ttu-id="424c9-172">Ancak, <xref:System.ServiceModel.EndpointAddress10> sınıfı kullanarak benzer bir sonuç elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="424c9-172">However, you can achieve a similar result by using the <xref:System.ServiceModel.EndpointAddress10> class.</span></span>  <span data-ttu-id="424c9-173">Sunucuda <xref:System.ServiceModel.EndpointAddress10> oturum dolusu ara başvuru nesnesi elde etmek için istemci tarafından kullanılabilecek serileştirilebilir bir by-value nesnesidir.</span><span class="sxs-lookup"><span data-stu-id="424c9-173">The <xref:System.ServiceModel.EndpointAddress10> is a serializable by-value object that can be used by the client to obtain a sessionful by-reference object on the server.</span></span>  
  
 <span data-ttu-id="424c9-174">Bu senaryoda gösterilen WCF'deki başvuru nesnesinin davranışı DCOM'dan farklıdır.</span><span class="sxs-lookup"><span data-stu-id="424c9-174">The behavior of the by-reference object in WCF shown in this scenario is different than DCOM.</span></span>  <span data-ttu-id="424c9-175">DCOM'da, sunucu bir başvuru nesnesini doğrudan istemciye döndürebilir ve istemci bu nesnenin sunucuda yürüten yöntemlerini çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="424c9-175">In DCOM, the server can return a by-reference object to the client directly, and the client can call that object’s methods, which execute on the server.</span></span>  <span data-ttu-id="424c9-176">Ancak WCF'de döndürülen nesne her zaman değer eve dir.</span><span class="sxs-lookup"><span data-stu-id="424c9-176">In WCF, however, the object returned is always by-value.</span></span>  <span data-ttu-id="424c9-177">İstemci, temsil edilen bu yan <xref:System.ServiceModel.EndpointAddress10> değer nesnesini almalı ve kendi oturumlu by-reference nesnesini oluşturmak için kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="424c9-177">The client must take that by-value object, represented by <xref:System.ServiceModel.EndpointAddress10> and use it to create its own sessionful by-reference object.</span></span>  <span data-ttu-id="424c9-178">İstemci yöntemi sunucuda oturum nesnesi yürütme çağırır. Başka bir deyişle, WCF'deki bu başvuru nesnesi, oturum lu olarak yapılandırılan normal bir WCF hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="424c9-178">The client method calls on the sessionful object execute on the server.In other words, this by-reference object in WCF is a normal WCF service that is configured to be sessionful.</span></span>  
  
 <span data-ttu-id="424c9-179">WCF'de oturum, iki uç nokta arasında gönderilen birden çok iletiyi ilişkilendirme yoludur.</span><span class="sxs-lookup"><span data-stu-id="424c9-179">In WCF, a session is a way of correlating multiple messages sent between two endpoints.</span></span>  <span data-ttu-id="424c9-180">Bu, istemci bu hizmete bağlantı ulaştığında istemci ve sunucu arasında bir oturum oluşturulacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="424c9-180">This means that once a client obtains a connection to this service, a session will be established between the client and the server.</span></span>  <span data-ttu-id="424c9-181">İstemci, bu tek oturumdaki tüm etkileşimleri için sunucu tarafındaki nesnenin tek bir benzersiz örneğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="424c9-181">The client will use a single unique instance of the server-side object for all its interactions within this single session.</span></span> <span data-ttu-id="424c9-182">Oturumlu WCF sözleşmeleri, bağlantı yönelimli ağ isteği/yanıt kalıplarına benzer.</span><span class="sxs-lookup"><span data-stu-id="424c9-182">Sessionful WCF contracts are similar to connection-oriented network request/response patterns.</span></span>  
  
 <span data-ttu-id="424c9-183">Bu senaryo aşağıdaki DCOM yöntemi yle temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="424c9-183">This scenario is represented by the following DCOM method.</span></span>  
  
```csharp  
public interface IRemoteService  
{  
    IRemoteObject GetObjectByReference();  
}  
```  
  
### <a name="step-1-define-the-sessionful-wcf-service-interface-and-implementation"></a><span data-ttu-id="424c9-184">Adım 1: Oturumlu WCF hizmet arabirimini ve uygulamasını tanımlayın</span><span class="sxs-lookup"><span data-stu-id="424c9-184">Step 1: Define the Sessionful WCF service interface and implementation</span></span>  
 <span data-ttu-id="424c9-185">İlk olarak, oturum nesnesi içeren bir WCF hizmet arabirimi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="424c9-185">First, define a WCF service interface that contains the sessionful object.</span></span>  
  
 <span data-ttu-id="424c9-186">Bu kodda, oturum oluşturan nesne, `ServiceContract` onu normal bir WCF hizmet arabirimi olarak tanımlayan öznitelik ile işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="424c9-186">In this code, the sessionful object is marked with the `ServiceContract` attribute, which identifies it as a regular WCF service interface.</span></span>  <span data-ttu-id="424c9-187">Buna ek <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> olarak, özellik bir oturum hizmeti olacağını belirtmek için ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="424c9-187">In addition, the <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> property is set to indicate it will be a sessionful service.</span></span>  
  
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
  
 <span data-ttu-id="424c9-188">Aşağıdaki kod hizmet uygulamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="424c9-188">The following code shows the service implementation.</span></span>  
  
 <span data-ttu-id="424c9-189">Hizmet [ServiceBehavior] özniteliği ile işaretlenir ve instanceContextMode özelliği her oturum için bu tür benzersiz bir örnek oluşturulması gerektiğini belirtmek için InstanceContextMode.PerSessions olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="424c9-189">The service is marked with the [ServiceBehavior] attribute, and its InstanceContextMode property set to InstanceContextMode.PerSessions to indicate that a unique instance of this type should be created for each session.</span></span>  
  
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
  
### <a name="step-2-define-the-wcf-factory-service-for-the-sessionful-object"></a><span data-ttu-id="424c9-190">Adım 2: Oturum daki nesne için WCF fabrika hizmetini tanımlayın</span><span class="sxs-lookup"><span data-stu-id="424c9-190">Step 2: Define the WCF factory service for the sessionful object</span></span>  
 <span data-ttu-id="424c9-191">Oturum oluşturabilen nesneyi oluşturan hizmet tanımlanmalı ve uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="424c9-191">The service that creates the sessionful object must be defined and implemented.</span></span> <span data-ttu-id="424c9-192">Aşağıdaki kod, bunun nasıl yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="424c9-192">The following code shows how to do this.</span></span> <span data-ttu-id="424c9-193">Bu kod, bir nesneyi döndüren başka bir <xref:System.ServiceModel.EndpointAddress10> WCF hizmeti oluşturur.</span><span class="sxs-lookup"><span data-stu-id="424c9-193">This code creates another WCF service that returns an <xref:System.ServiceModel.EndpointAddress10> object.</span></span>  <span data-ttu-id="424c9-194">Bu, oturum dolu nesneyi oluşturmak için kullanabileceği bir bitiş noktasının serileştirilebilir biçimidir.</span><span class="sxs-lookup"><span data-stu-id="424c9-194">This is a serializable form of an endpoint the can use to create the session-full object.</span></span>  
  
```csharp  
[ServiceContract]  
    public interface ISessionBoundFactory  
    {  
        [OperationContract]  
        EndpointAddress10 GetInstanceAddress();  
    }  
```  
  
 <span data-ttu-id="424c9-195">Bu hizmetin uygulanması aşağıda veda edileb'dir.</span><span class="sxs-lookup"><span data-stu-id="424c9-195">The following is the implementation of this service.</span></span> <span data-ttu-id="424c9-196">Bu uygulama, oturumlu nesneler oluşturmak için bir singleton kanal fabrika tutar.</span><span class="sxs-lookup"><span data-stu-id="424c9-196">This implementation maintains a singleton channel factory to create sessionful objects.</span></span>  <span data-ttu-id="424c9-197">Çağrıldığında, `GetInstanceAddress` bir kanal oluşturur ve <xref:System.ServiceModel.EndpointAddress10> bu kanalla ilişkili uzak adrese işaret eden bir nesne oluşturur.</span><span class="sxs-lookup"><span data-stu-id="424c9-197">When `GetInstanceAddress` is called, it creates a channel and creates an <xref:System.ServiceModel.EndpointAddress10> object that points to the remote address associated with this channel.</span></span>   <span data-ttu-id="424c9-198"><xref:System.ServiceModel.EndpointAddress10>istemciye göre değer olarak döndürülebilen bir veri türüdür.</span><span class="sxs-lookup"><span data-stu-id="424c9-198"><xref:System.ServiceModel.EndpointAddress10> is a data type that can be returned to the client by-value.</span></span>
  
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
  
### <a name="step-3-configure-and-start-the-wcf-services"></a><span data-ttu-id="424c9-199">Adım 3: WCF hizmetlerini yapılandırın ve başlatın</span><span class="sxs-lookup"><span data-stu-id="424c9-199">Step 3: Configure and start the WCF services</span></span>  
 <span data-ttu-id="424c9-200">Bu hizmetleri barındırmak için sunucunun yapılandırma dosyasına (web.config) aşağıdaki eklemeleri yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="424c9-200">To host these services, you will need to make the following additions to the server’s configuration file (web.config).</span></span>  
  
1. <span data-ttu-id="424c9-201">Oturum `<client>` açan nesnenin bitiş noktasını açıklayan bir bölüm ekleyin.</span><span class="sxs-lookup"><span data-stu-id="424c9-201">Add a `<client>` section that describes the endpoint for the sessionful object.</span></span>  <span data-ttu-id="424c9-202">Bu senaryoda, sunucu da bir istemci olarak hareket eder ve bunu etkinleştirmek için yapılandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="424c9-202">In this scenario, the server also acts as a client and must be configured to enable this.</span></span>  
  
2. <span data-ttu-id="424c9-203">`<services>` Bölümde, fabrika ve oturum nesnesi için hizmet bitiş noktalarını bildirin.</span><span class="sxs-lookup"><span data-stu-id="424c9-203">In the `<services>` section, declare service endpoints for the factory and sessionful object.</span></span>  <span data-ttu-id="424c9-204">Bu, istemcinin hizmet uç noktalarıyla iletişim <xref:System.ServiceModel.EndpointAddress10> kurmasını, oturum alabilme kanalını edinmesini ve oluşturmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="424c9-204">This enables the client to communicate with the service endpoints, acquire the <xref:System.ServiceModel.EndpointAddress10> and create the sessionful channel.</span></span>  
  
 <span data-ttu-id="424c9-205">Aşağıdaki bu ayarları ile örnek bir yapılandırma dosyasıdır:</span><span class="sxs-lookup"><span data-stu-id="424c9-205">The following is an example configuration file with these settings:</span></span>  
  
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
  
 <span data-ttu-id="424c9-206">Hizmeti kendi kendine barındırmak için bir konsol uygulamasına aşağıdaki satırları ekleyin ve uygulamayı başlatın.</span><span class="sxs-lookup"><span data-stu-id="424c9-206">Add the following lines to a console application, to self-host the service, and start the app.</span></span>  
  
```csharp  
ServiceHost factoryHost = new ServiceHost(typeof(SessionBoundFactory));  
factoryHost.Open();  
  
ServiceHost sessionBoundServiceHost = new ServiceHost(  
typeof(MySessionBoundObject));  
sessionBoundServiceHost.Open();  
```  
  
### <a name="step-4-configure-the-client-and-call-the-service"></a><span data-ttu-id="424c9-207">Adım 4: İstemciyi yapılandırın ve hizmeti arayın</span><span class="sxs-lookup"><span data-stu-id="424c9-207">Step 4: Configure the client and call the service</span></span>  
 <span data-ttu-id="424c9-208">Projenin uygulama yapılandırma dosyasına (app.config) aşağıdaki girişleri yaparak istemciyi WCF hizmetleriyle iletişim kuracak şekilde yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="424c9-208">Configure the client to communicate with the WCF services by making the following entries in the project’s application configuration file (app.config).</span></span>  
  
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
  
 <span data-ttu-id="424c9-209">Hizmeti aramak için aşağıdakileri yapmak için kodu istemciye ekleyin:</span><span class="sxs-lookup"><span data-stu-id="424c9-209">To call the service, add the code to the client to do the following:</span></span>  
  
1. <span data-ttu-id="424c9-210">`ISessionBoundFactory` Hizmetiçin bir kanal oluşturun.</span><span class="sxs-lookup"><span data-stu-id="424c9-210">Create a channel to the `ISessionBoundFactory` service.</span></span>  
  
2. <span data-ttu-id="424c9-211">`ISessionBoundFactory` Bir <xref:System.ServiceModel.EndpointAddress10> nesne elde etmek için hizmet çağırmak için kanalı kullanın.</span><span class="sxs-lookup"><span data-stu-id="424c9-211">Use the channel to invoke the `ISessionBoundFactory` service an obtain an <xref:System.ServiceModel.EndpointAddress10> object.</span></span>  
  
3. <span data-ttu-id="424c9-212"><xref:System.ServiceModel.EndpointAddress10> Oturum lu bir nesne elde etmek için kanal oluşturmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="424c9-212">Use the <xref:System.ServiceModel.EndpointAddress10> to create a channel to obtain a sessionful object.</span></span>  
  
4. <span data-ttu-id="424c9-213">Çağrı `SetCurrentValue` ve `GetCurrentValue` yöntemleri göstermek için aynı nesne örneği birden çok arama arasında kullanılır kalır.</span><span class="sxs-lookup"><span data-stu-id="424c9-213">Call the `SetCurrentValue` and `GetCurrentValue` methods to demonstrate it remains the same object instance is used across multiple calls.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="424c9-214">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="424c9-214">See also</span></span>

- [<span data-ttu-id="424c9-215">Temel WCF Programlama</span><span class="sxs-lookup"><span data-stu-id="424c9-215">Basic WCF Programming</span></span>](../wcf/basic-wcf-programming.md)
- [<span data-ttu-id="424c9-216">Hizmetleri Tasarlama ve Uygulama</span><span class="sxs-lookup"><span data-stu-id="424c9-216">Designing and Implementing Services</span></span>](../wcf/designing-and-implementing-services.md)
- [<span data-ttu-id="424c9-217">İstemci Derleme</span><span class="sxs-lookup"><span data-stu-id="424c9-217">Building Clients</span></span>](../wcf/building-clients.md)
- [<span data-ttu-id="424c9-218">Çift Yönlü Hizmetler</span><span class="sxs-lookup"><span data-stu-id="424c9-218">Duplex Services</span></span>](../wcf/feature-details/duplex-services.md)
