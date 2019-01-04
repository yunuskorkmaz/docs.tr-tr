---
title: "Nasıl yapılır: Yönetilen kodu DCOM'dan WCF'ye geçirme"
ms.date: 03/30/2017
ms.assetid: 52961ffc-d1c7-4f83-832c-786444b951ba
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 202737692bae14ada229ee2c92a6630a3ed71344
ms.sourcegitcommit: 3b9b7ae6771712337d40374d2fef6b25b0d53df6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54030080"
---
# <a name="how-to-migrate-managed-code-dcom-to-wcf"></a><span data-ttu-id="128d8-102">Nasıl yapılır: Yönetilen kodu DCOM'dan WCF'ye geçirme</span><span class="sxs-lookup"><span data-stu-id="128d8-102">How to: Migrate Managed-Code DCOM to WCF</span></span>
<span data-ttu-id="128d8-103">Windows Communication Foundation (WCF) önerilen ve güvenli Dağıtılmış Bileşen Nesne Modeli (DCOM) üzerinden sunucular ve istemciler dağıtılmış bir ortamda arasındaki çağrıların yönetilen kod için seçimdir.</span><span class="sxs-lookup"><span data-stu-id="128d8-103">Windows Communication Foundation (WCF) is the recommended and secure choice over Distributed Component Object Model (DCOM) for managed code calls between servers and clients in a distributed environment.</span></span> <span data-ttu-id="128d8-104">Bu makale nasıl kod DCOM'dan WCF'ye aşağıdaki senaryolar için geçirme için.</span><span class="sxs-lookup"><span data-stu-id="128d8-104">This article shows how you to migrate code from DCOM to WCF for the following scenarios.</span></span>  
  
-   <span data-ttu-id="128d8-105">Uzak Hizmet, bir nesneyi değere göre istemciye döndürür.</span><span class="sxs-lookup"><span data-stu-id="128d8-105">The remote service returns an object by-value to the client</span></span>  
  
-   <span data-ttu-id="128d8-106">İstemci bir nesneyi değere göre uzak hizmetine gönderir.</span><span class="sxs-lookup"><span data-stu-id="128d8-106">The client sends an object by-value to the remote service</span></span>  
  
-   <span data-ttu-id="128d8-107">Uzak Hizmet, bir nesne başvuru tarafından istemciye döndürür.</span><span class="sxs-lookup"><span data-stu-id="128d8-107">The remote service returns an object by-reference to the client</span></span>  
  
 <span data-ttu-id="128d8-108">Güvenlik nedeniyle, bir nesne başvuruya göre istemciden hizmete gönderme WCF'de izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="128d8-108">For security reasons, sending an object by-reference from the client to the service is not allowed in WCF.</span></span> <span data-ttu-id="128d8-109">İstemci ve sunucu arasında sürekli bir konuşma gerektiren bir senaryo, bir çift yönlü hizmet kullanarak WCF'de gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="128d8-109">A scenario that requires a conversation back and forth between client and server can be achieved in WCF using a duplex service.</span></span>  <span data-ttu-id="128d8-110">Çift yönlü hizmetler hakkında daha fazla bilgi için bkz: [çift yönlü Hizmetler](../../../docs/framework/wcf/feature-details/duplex-services.md).</span><span class="sxs-lookup"><span data-stu-id="128d8-110">For more information about duplex services, see [Duplex Services](../../../docs/framework/wcf/feature-details/duplex-services.md).</span></span>  
  
 <span data-ttu-id="128d8-111">WCF hizmetleri ve istemciler için bu hizmetleri oluşturma hakkında daha fazla ayrıntı için bkz. [temel WCF programlama](../../../docs/framework/wcf/basic-wcf-programming.md), [Hizmetleri Tasarlama ve uygulama](../../../docs/framework/wcf/designing-and-implementing-services.md), ve [istemci derleme](../../../docs/framework/wcf/building-clients.md).</span><span class="sxs-lookup"><span data-stu-id="128d8-111">For more details about creating WCF services and clients for those services, see [Basic WCF Programming](../../../docs/framework/wcf/basic-wcf-programming.md), [Designing and Implementing Services](../../../docs/framework/wcf/designing-and-implementing-services.md), and [Building Clients](../../../docs/framework/wcf/building-clients.md).</span></span>  
  
## <a name="dcom-example-code"></a><span data-ttu-id="128d8-112">DCOM örnek kod</span><span class="sxs-lookup"><span data-stu-id="128d8-112">DCOM example code</span></span>  
 <span data-ttu-id="128d8-113">Bu senaryolar için WCF kullanan gösterilmiştir DCOM arabirimleri aşağıdaki yapıya sahiptir:</span><span class="sxs-lookup"><span data-stu-id="128d8-113">For these scenarios, the DCOM interfaces that are illustrated using WCF have the following structure:</span></span>  
  
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
  
## <a name="the-service-returns-an-object-by-value"></a><span data-ttu-id="128d8-114">Hizmet bir nesne tarafından değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="128d8-114">The service returns an object by-value</span></span>  
 <span data-ttu-id="128d8-115">Bu senaryo için bir değere göre istemcinin sunucudan geçirilen nesneye yöntemi döndürür ve bir hizmeti çağrı yapmak.</span><span class="sxs-lookup"><span data-stu-id="128d8-115">For this scenario, you make a call to a service and it method returns an object, which is passed by-value from the server to the client.</span></span> <span data-ttu-id="128d8-116">Bu senaryo, COM çağrısını temsil eder:</span><span class="sxs-lookup"><span data-stu-id="128d8-116">This scenario represents the following COM call:</span></span>  
  
```csharp  
public interface IRemoteService  
{  
    Customer GetObjectByValue();  
}  
```  
  
 <span data-ttu-id="128d8-117">Bu senaryoda, istemci uzak hizmetten bir nesneyi seri durumdan çıkarılmış bir kopyasını alır.</span><span class="sxs-lookup"><span data-stu-id="128d8-117">In this scenario, the client receives a deserialized copy of an object from the remote service.</span></span> <span data-ttu-id="128d8-118">İstemci hizmete geri çağırmaya gerek kalmadan bu yerel bir kopya ile etkileşim kurabilir.</span><span class="sxs-lookup"><span data-stu-id="128d8-118">The client can interact with this local copy without calling back to the service.</span></span>  <span data-ttu-id="128d8-119">Diğer bir deyişle, istemci yerel kopya yöntemler çağrıldığında hizmeti herhangi bir yolla dahil olacaktır değil garanti edilir.</span><span class="sxs-lookup"><span data-stu-id="128d8-119">In other words, the client is guaranteed the service will not be involved in any way when methods on the local copy are called.</span></span> <span data-ttu-id="128d8-120">Aşağıdaki adımlar, normal bir WCF hizmeti oluşturma açıklar. Bu nedenle WCF her zaman nesneleri hizmetten değere göre döndürür.</span><span class="sxs-lookup"><span data-stu-id="128d8-120">WCF always returns objects from the service by value, so the following steps describe creating a regular WCF service.</span></span>  
  
### <a name="step-1-define-the-wcf-service-interface"></a><span data-ttu-id="128d8-121">1. Adım: WCF hizmet arabirimi tanımlayın</span><span class="sxs-lookup"><span data-stu-id="128d8-121">Step 1: Define the WCF service interface</span></span>  
 <span data-ttu-id="128d8-122">WCF hizmeti için ortak bir arabirim tanımlayın ve kendisiyle işaretlemek [<xref:System.ServiceModel.ServiceContractAttribute>] özniteliği.</span><span class="sxs-lookup"><span data-stu-id="128d8-122">Define a public interface for the WCF service and mark it with the [<xref:System.ServiceModel.ServiceContractAttribute>] attribute.</span></span>  <span data-ttu-id="128d8-123">İstemciler için kullanıma sunmak istediğiniz yöntemlerini işaretlemek [<xref:System.ServiceModel.OperationContractAttribute>] özniteliği.</span><span class="sxs-lookup"><span data-stu-id="128d8-123">Mark the methods you want to expose to clients with the [<xref:System.ServiceModel.OperationContractAttribute>] attribute.</span></span> <span data-ttu-id="128d8-124">Aşağıdaki örnek, bir istemci çağırabilirsiniz arabirim yöntemleri ve sunucu tarafı arabirimi tanımlamak için bu öznitelikler kullanarak gösterir.</span><span class="sxs-lookup"><span data-stu-id="128d8-124">The following example shows using these attributes to identify the server-side interface and interface methods a client can call.</span></span> <span data-ttu-id="128d8-125">Bu senaryo için kullanılan yöntem kalın olarak gösterilir.</span><span class="sxs-lookup"><span data-stu-id="128d8-125">The method used for this scenario is shown in bold.</span></span>  
  
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
  
### <a name="step-2-define-the-data-contract"></a><span data-ttu-id="128d8-126">2. Adım: Veri sözleşmesi tanımlayın</span><span class="sxs-lookup"><span data-stu-id="128d8-126">Step 2: Define the data contract</span></span>  
 <span data-ttu-id="128d8-127">Ardından, nasıl veri hizmet ve istemcileri arasında değiş tokuş anlatmaktadır hizmeti için bir veri sözleşmesi oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="128d8-127">Next you should create a data contract for the service, which will describe how the data will be exchanged between the service and its clients.</span></span>  <span data-ttu-id="128d8-128">Veri sözleşmede açıklanan sınıfları ile işaretlenmemelidir [<xref:System.Runtime.Serialization.DataContractAttribute>] özniteliği.</span><span class="sxs-lookup"><span data-stu-id="128d8-128">Classes described in the data contract should be marked with the [<xref:System.Runtime.Serialization.DataContractAttribute>] attribute.</span></span> <span data-ttu-id="128d8-129">Hem istemci hem de sunucu görünür istediğiniz alanlar ve özellikler ile işaretlenmelidir [<xref:System.Runtime.Serialization.DataMemberAttribute>] özniteliği.</span><span class="sxs-lookup"><span data-stu-id="128d8-129">The individual properties or fields you want visible to both client and server should be marked with the [<xref:System.Runtime.Serialization.DataMemberAttribute>] attribute.</span></span> <span data-ttu-id="128d8-130">Türetilen bir sınıfta izin verilmesi için veri anlaşması türleri istiyorsanız tanımlamalıdır [<xref:System.Runtime.Serialization.KnownTypeAttribute>] özniteliği.</span><span class="sxs-lookup"><span data-stu-id="128d8-130">If you want types derived from a class in the data contract to be allowed, you must identify them with the [<xref:System.Runtime.Serialization.KnownTypeAttribute>] attribute.</span></span> <span data-ttu-id="128d8-131">WCF yalnızca serileştirmek veya hizmet arabirimi türlerinde ve bilinen türleri olarak tanımlanan türler seri durumdan.</span><span class="sxs-lookup"><span data-stu-id="128d8-131">WCF will only serialize or deserialize types in the service interface and types identified as known types.</span></span> <span data-ttu-id="128d8-132">Bilinen bir tür değil bir tür kullanmayı denerseniz, bir özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="128d8-132">If you attempt to use a type that is not a known type, an exception will occur.</span></span>  
  
 <span data-ttu-id="128d8-133">Veri sözleşmeleri hakkında daha fazla bilgi için bkz: [veri sözleşmeleri](../../../docs/framework/wcf/samples/data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="128d8-133">For more information about data contracts, see [Data Contracts](../../../docs/framework/wcf/samples/data-contracts.md).</span></span>  
  
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
  
### <a name="step-3-implement-the-wcf-service"></a><span data-ttu-id="128d8-134">3. Adım: WCF hizmet ekleme</span><span class="sxs-lookup"><span data-stu-id="128d8-134">Step 3: Implement the WCF service</span></span>  
 <span data-ttu-id="128d8-135">Ardından, önceki adımda tanımladığınız arabirimi uygulayan WCF hizmet sınıfı uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="128d8-135">Next, you should implement the WCF service class that implements the interface you defined in the previous step.</span></span>  
  
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
  
### <a name="step-4-configure-the-service-and-the-client"></a><span data-ttu-id="128d8-136">4. Adım: Hizmet ve istemci yapılandırma</span><span class="sxs-lookup"><span data-stu-id="128d8-136">Step 4: Configure the service and the client</span></span>  
 <span data-ttu-id="128d8-137">Bir WCF hizmeti çalıştırmak için belirli bir WCF bağlamayı kullanarak belirli bir URL'den bu hizmet arabirimi kullanıma sunan bir uç nokta bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="128d8-137">To run a WCF service, you need to declare an endpoint that exposes that service interface at a specific URL using a specific WCF binding.</span></span> <span data-ttu-id="128d8-138">Bağlama istemciler ve sunucu iletişim kurmak için taşıma, kodlama ve protokolü ayrıntılarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="128d8-138">A binding specifies the transport, encoding and protocol details for the clients and server to communicate.</span></span> <span data-ttu-id="128d8-139">Genellikle hizmet projesinin yapılandırma dosyasında (web.config) bağlamaları ekleyin.</span><span class="sxs-lookup"><span data-stu-id="128d8-139">You typically add bindings to the service project’s configuration file (web.config).</span></span> <span data-ttu-id="128d8-140">Aşağıdaki örnek hizmeti için bir bağlayıcı giriş gösterir:</span><span class="sxs-lookup"><span data-stu-id="128d8-140">The following shows a binding entry for the example service:</span></span>  
  
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
  
 <span data-ttu-id="128d8-141">Ardından, hizmet tarafından belirtilen bağlama bilgileri eşleşecek şekilde istemciyi yapılandırmak gerekir.</span><span class="sxs-lookup"><span data-stu-id="128d8-141">Next, you need to configure the client to match the binding information specified by the service.</span></span> <span data-ttu-id="128d8-142">Bunu yapmak için istemci uygulama yapılandırma (app.config) dosyasına aşağıdakileri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="128d8-142">To do so, add the following to the client’s application configuration (app.config) file.</span></span>  
  
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
  
### <a name="step-5-run-the-service"></a><span data-ttu-id="128d8-143">5. Adım: Hizmet çalıştırma</span><span class="sxs-lookup"><span data-stu-id="128d8-143">Step 5: Run the service</span></span>  
 <span data-ttu-id="128d8-144">Son olarak, bunu bir konsol uygulamasında aşağıdaki satırları hizmet uygulamasına ekleme ve uygulama başlatma Self barındırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="128d8-144">Finally, you can self-host it in a console application by adding the following lines to the service app, and starting the app.</span></span> <span data-ttu-id="128d8-145">Bir WCF Hizmeti uygulamasını barındırmak için kullanabileceğiniz diğer yöntemler hakkında daha fazla bilgi için [barındırma hizmetleri](../../../docs/framework/wcf/hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="128d8-145">For more information about other ways to host a WCF service application, [Hosting Services](../../../docs/framework/wcf/hosting-services.md).</span></span>  
  
```csharp  
ServiceHost customerServiceHost = new ServiceHost(typeof(CustomerService));  
customerServiceHost.Open();  
```  
  
### <a name="step-6-call-the-service-from-the-client"></a><span data-ttu-id="128d8-146">6. Adım: Hizmet istemciden çağırın</span><span class="sxs-lookup"><span data-stu-id="128d8-146">Step 6: Call the service from the client</span></span>  
 <span data-ttu-id="128d8-147">İstemciden hizmeti çağırmak için hizmeti için kanal fabrikası oluşturma ve doğrudan çağırmak sağlayacak bir kanal istek gerekir `GetCustomer` yöntemi doğrudan istemci.</span><span class="sxs-lookup"><span data-stu-id="128d8-147">To call the service from the client, you need to create a channel factory for the service, and request a channel, which will enable you to directly call the `GetCustomer` method directly from the client.</span></span> <span data-ttu-id="128d8-148">Kanal, hizmetin arabirimi uygulayan ve temel alınan istek/yanıt mantığını sizin yerinize çözer.</span><span class="sxs-lookup"><span data-stu-id="128d8-148">The channel implements the service’s interface and handles the underlying request/reply logic for you.</span></span>  <span data-ttu-id="128d8-149">Bu yöntem çağrısının dönüş değerini hizmet yanıt seri durumdan çıkarılmış kopyasıdır.</span><span class="sxs-lookup"><span data-stu-id="128d8-149">The return value from that method call is the deserialized copy of the service response.</span></span>  
  
```csharp  
ChannelFactory<ICustomerManager> factory =   
     new ChannelFactory<ICustomerManager>("customermanager");  
ICustomerManager service = factory.CreateChannel();  
Customer customer = service.GetCustomer("Mary", "Smith");  
```  
  
## <a name="the-client-sends-a-by-value-object-to-the-server"></a><span data-ttu-id="128d8-150">İstemci bir değere göre nesne sunucuya gönderir.</span><span class="sxs-lookup"><span data-stu-id="128d8-150">The client sends a by-value object to the server</span></span>  
 <span data-ttu-id="128d8-151">Bu senaryoda, bir nesneye sunucuya istemci gönderir değere göre.</span><span class="sxs-lookup"><span data-stu-id="128d8-151">In this scenario, the client sends an object to the server, by-value.</span></span> <span data-ttu-id="128d8-152">Bu, sunucu nesne seri durumdan çıkarılmış bir kopyasını aldığından anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="128d8-152">This means that the server will receive a deserialized copy of the object.</span></span>  <span data-ttu-id="128d8-153">Sunucu üzerinde bu kopyayı yöntemleri çağırabilir ve istemci koda hiçbir geri çağırma yok garanti.</span><span class="sxs-lookup"><span data-stu-id="128d8-153">The server can call methods on that copy and be guaranteed there is no callback into client code.</span></span> <span data-ttu-id="128d8-154">Daha önce belirtildiği gibi normal WCF değişimleri veri değere göre ' dir.</span><span class="sxs-lookup"><span data-stu-id="128d8-154">As mentioned previously, normal WCF exchanges of data are by-value.</span></span>  <span data-ttu-id="128d8-155">Bu garanti Bu nesnelerden birini metotları çağırma yerel olarak yalnızca yürütür – istemci kodu çağırma kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="128d8-155">This guarantees that calling methods on one of these objects executes locally only – it will not invoke code on the client.</span></span>  
  
 <span data-ttu-id="128d8-156">Bu senaryo aşağıdaki COM yöntem çağrısını temsil eder:</span><span class="sxs-lookup"><span data-stu-id="128d8-156">This scenario represents the following COM method call:</span></span>  
  
```csharp  
public interface IRemoteService  
{  
    void SendObjectByValue(Customer customer);  
}  
```  
  
 <span data-ttu-id="128d8-157">Bu senaryo, ilk örnekte gösterildiği gibi aynı hizmet arabirimi ve veri sözleşmesi kullanır.</span><span class="sxs-lookup"><span data-stu-id="128d8-157">This scenario uses the same service interface and data contract as shown in the first example.</span></span> <span data-ttu-id="128d8-158">Ayrıca, hizmet ve istemci aynı şekilde yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="128d8-158">In addition, the client and service will be configured in the same way.</span></span> <span data-ttu-id="128d8-159">Bu örnekte, nesne gönderin ve aynı şekilde çalıştırmak için bir kanal oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="128d8-159">In this example, a channel is created to send the object and run the same way.</span></span> <span data-ttu-id="128d8-160">Ancak, bu örnekte, bir nesneyi değere göre geçirme hizmetini çağıran bir istemci oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="128d8-160">However, for this example, you will create a client that calls the service, passing an object by-value.</span></span> <span data-ttu-id="128d8-161">İstemci hizmet sözleşmesindeki çağıracak hizmet yöntemi kalın olarak gösterilir:</span><span class="sxs-lookup"><span data-stu-id="128d8-161">The service method the client will call in the service contract is shown in bold:</span></span>  
  
```csharp  
[ServiceContract]  
public interface ICustomerManager  
{  
    [OperationContract]     void StoreCustomer(Customer customer);  
  
    [OperationContract]  
    Customer GetCustomer(string firstName, string lastName);  
}  
```  
  
### <a name="add-code-to-the-client-that-sends-a-by-value-object"></a><span data-ttu-id="128d8-162">Değere göre nesne gönderen istemciye kod ekleyin</span><span class="sxs-lookup"><span data-stu-id="128d8-162">Add code to the client that sends a by-value object</span></span>  
 <span data-ttu-id="128d8-163">Aşağıdaki kodun gösterdiği istemci yeni bir değere göre müşteri nesnesi oluşturur nasıl ile iletişim kurmak için bir kanal oluşturur `ICustomerManager` hizmet ve müşteri nesnesi için gönderir.</span><span class="sxs-lookup"><span data-stu-id="128d8-163">The following code shows how the client creates a new by-value customer object, creates a channel to communicate with the `ICustomerManager` service, and sends the customer object to it.</span></span>  
  
 <span data-ttu-id="128d8-164">Müşteri nesnesi seri hale getirilmiş ve burada, hizmet tarafından bu nesne yeni bir kopyasını seri durumda hizmetine gönderilir.</span><span class="sxs-lookup"><span data-stu-id="128d8-164">The customer object will be serialized, and sent to the service, where it is deserialized by the service into a new copy of that object.</span></span>  <span data-ttu-id="128d8-165">Hizmetine çağrı yapan, bu nesne üzerinde herhangi bir yöntem yalnızca yerel olarak yürütülür sunucusunda.</span><span class="sxs-lookup"><span data-stu-id="128d8-165">Any methods the service calls on this object will execute only locally on the server.</span></span> <span data-ttu-id="128d8-166">Bu kod gönderme türetilmiş bir türü göstermektedir dikkat edin önemlidir (`PremiumCustomer`).</span><span class="sxs-lookup"><span data-stu-id="128d8-166">It’s important to note that this code illustrates sending a derived type (`PremiumCustomer`).</span></span>  <span data-ttu-id="128d8-167">Hizmet sözleşmesi bekliyor bir `Customer` nesne, ancak hizmet veri sözleşme kullanır [<xref:System.Runtime.Serialization.KnownTypeAttribute>] belirtmek için özniteliği `PremiumCustomer` da izin verilir.</span><span class="sxs-lookup"><span data-stu-id="128d8-167">The service contract expects a `Customer` object, but the service data contract uses the [<xref:System.Runtime.Serialization.KnownTypeAttribute>] attribute to indicate that `PremiumCustomer` is also allowed.</span></span>  <span data-ttu-id="128d8-168">WCF serileştirmek veya bu hizmet arabirimi aracılığıyla herhangi bir türü seri durumdan girişimleri başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="128d8-168">WCF will fail attempts to serialize or deserialize any other type via this service interface.</span></span>  
  
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
  
## <a name="the-service-returns-an-object-by-reference"></a><span data-ttu-id="128d8-169">Hizmet başvuruya göre bir nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="128d8-169">The service returns an object by reference</span></span>  
 <span data-ttu-id="128d8-170">Bu senaryo için istemci uygulaması uzak hizmet çağrıda bulunur ve istemci hizmeti başvuru tarafından geçirilen nesneyi yöntemi döndürür.</span><span class="sxs-lookup"><span data-stu-id="128d8-170">For this scenario, the client app makes a call to the remote service and the method returns an object, which is passed by reference from the service to the client.</span></span>  
  
 <span data-ttu-id="128d8-171">Daha önce belirtildiği gibi WCF hizmetleri değere göre her zaman nesnesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="128d8-171">As mentioned previously, WCF services always return object by value.</span></span>  <span data-ttu-id="128d8-172">Ancak, kullanarak benzer bir sonuç elde edebileceğiniz <xref:System.ServiceModel.EndpointAddress10> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="128d8-172">However, you can achieve a similar result by using the <xref:System.ServiceModel.EndpointAddress10> class.</span></span>  <span data-ttu-id="128d8-173"><xref:System.ServiceModel.EndpointAddress10> Sunucuda kapatamaması başvuru tarafından nesnesini almak için istemci tarafından kullanılan bir değer tarafından seri hale getirilebilir nesnesidir.</span><span class="sxs-lookup"><span data-stu-id="128d8-173">The <xref:System.ServiceModel.EndpointAddress10> is a serializable by-value object that can be used by the client to obtain a sessionful by-reference object on the server.</span></span>  
  
 <span data-ttu-id="128d8-174">Bu senaryoda gösterildiği WCF başvuruya göre nesnesinde davranışını DCOM farklıdır.</span><span class="sxs-lookup"><span data-stu-id="128d8-174">The behavior of the by-reference object in WCF shown in this scenario is different than DCOM.</span></span>  <span data-ttu-id="128d8-175">DCOM, sunucunun bir başvuruya göre nesne istemciye doğrudan döndürebilir ve istemcinin sunucuda yürütülür nesnenin yöntemleri çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="128d8-175">In DCOM, the server can return a by-reference object to the client directly, and the client can call that object’s methods, which execute on the server.</span></span>  <span data-ttu-id="128d8-176">WCF'de, ancak döndürülen nesne olduğundan her zaman değere göre.</span><span class="sxs-lookup"><span data-stu-id="128d8-176">In WCF, however, the object returned is always by-value.</span></span>  <span data-ttu-id="128d8-177">İstemci tarafından temsil edilen bu değere göre nesne almalıdır <xref:System.ServiceModel.EndpointAddress10> ve kendi başvuru tarafından kapatamaması nesnesi oluşturmak için bunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="128d8-177">The client must take that by-value object, represented by <xref:System.ServiceModel.EndpointAddress10> and use it to create its own sessionful by-reference object.</span></span>  <span data-ttu-id="128d8-178">İstemci yöntem çağrılarını kapatamaması nesnesindeki sunucuda yürütülür. Diğer bir deyişle, bu başvuruya göre wcf'de kapatamaması olacak şekilde yapılandırıldığında normal bir WCF Hizmeti nesnedir.</span><span class="sxs-lookup"><span data-stu-id="128d8-178">The client method calls on the sessionful object execute on the server.In other words, this by-reference object in WCF is a normal WCF service that is configured to be sessionful.</span></span>  
  
 <span data-ttu-id="128d8-179">WCF'de, oturum, birden çok ileti iki uç nokta arasında gönderilen ilişkilendirme bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="128d8-179">In WCF, a session is a way of correlating multiple messages sent between two endpoints.</span></span>  <span data-ttu-id="128d8-180">Bu, istemci bu hizmet için bir bağlantı alır, sonra oturumu istemci ve sunucu arasında kurulur, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="128d8-180">This means that once a client obtains a connection to this service, a session will be established between the client and the server.</span></span>  <span data-ttu-id="128d8-181">İstemci bu oturumla içinde için tüm etkileşimler bir tek benzersiz bir sunucu tarafı nesne örneği kullanın.</span><span class="sxs-lookup"><span data-stu-id="128d8-181">The client will use a single unique instance of the server-side object for all its interactions within this single session.</span></span> <span data-ttu-id="128d8-182">Ağ bağlantısı yönelik istek/yanıt desenlerini kapatamaması WCF sözleşmeleri benzerdir.</span><span class="sxs-lookup"><span data-stu-id="128d8-182">Sessionful WCF contracts are similar to connection-oriented network request/response patterns.</span></span>  
  
 <span data-ttu-id="128d8-183">Bu senaryo aşağıdaki DCOM yöntemi tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="128d8-183">This scenario is represented by the following DCOM method.</span></span>  
  
```csharp  
public interface IRemoteService  
{  
    IRemoteObject GetObjectByReference();  
}  
```  
  
### <a name="step-1-define-the-sessionful-wcf-service-interface-and-implementation"></a><span data-ttu-id="128d8-184">1. Adım: Uygulama ve Sessionful WCF hizmet arabirimi tanımlayın</span><span class="sxs-lookup"><span data-stu-id="128d8-184">Step 1: Define the Sessionful WCF service interface and implementation</span></span>  
 <span data-ttu-id="128d8-185">İlk olarak, kapatamaması nesne içeren bir WCF Hizmeti arabirimi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="128d8-185">First, define a WCF service interface that contains the sessionful object.</span></span>  
  
 <span data-ttu-id="128d8-186">Bu kodda kapatamaması nesne ile işaretlenmiş `ServiceContract` özniteliği normal bir WCF Hizmeti arabirimi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="128d8-186">In this code, the sessionful object is marked with the `ServiceContract` attribute, which identifies it as a regular WCF service interface.</span></span>  <span data-ttu-id="128d8-187">Ayrıca, <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> özelliği kapatamaması hizmet olacaktır belirtmek için ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="128d8-187">In addition, the <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> property is set to indicate it will be a sessionful service.</span></span>  
  
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
  
 <span data-ttu-id="128d8-188">Aşağıdaki kod, hizmet uygulamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="128d8-188">The following code shows the service implementation.</span></span>  
  
 <span data-ttu-id="128d8-189">Hizmet [ServiceBehavior] özniteliği ile işaretli ve her oturum için benzersiz bir örnek bu türde oluşturulması gerektiğini belirtmek için InstanceContextMode.PerSessions için kendi InstanceContextMode özelliğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="128d8-189">The service is marked with the [ServiceBehavior] attribute, and its InstanceContextMode property set to InstanceContextMode.PerSessions to indicate that a unique instance of this type should be created for each session.</span></span>  
  
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
  
### <a name="step-2-define-the-wcf-factory-service-for-the-sessionful-object"></a><span data-ttu-id="128d8-190">2. Adım: WCF factory hizmeti kapatamaması nesnesi tanımlayın</span><span class="sxs-lookup"><span data-stu-id="128d8-190">Step 2: Define the WCF factory service for the sessionful object</span></span>  
 <span data-ttu-id="128d8-191">Kapatamaması nesnesini oluşturan hizmet tanımlı ve uygulanan gerekir.</span><span class="sxs-lookup"><span data-stu-id="128d8-191">The service that creates the sessionful object must be defined and implemented.</span></span> <span data-ttu-id="128d8-192">Aşağıdaki kod, bunun nasıl yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="128d8-192">The following code shows how to do this.</span></span> <span data-ttu-id="128d8-193">Veren başka bir WCF hizmeti bu kod oluşturur bir <xref:System.ServiceModel.EndpointAddress10> nesne.</span><span class="sxs-lookup"><span data-stu-id="128d8-193">This code creates another WCF service that returns an <xref:System.ServiceModel.EndpointAddress10> object.</span></span>  <span data-ttu-id="128d8-194">Bu bir uç nokta can seri hale getirilebilir bir tür, tam oturum nesnesi oluşturmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="128d8-194">This is a serializable form of an endpoint the can use to create the session-full object.</span></span>  
  
```csharp  
[ServiceContract]  
    public interface ISessionBoundFactory  
    {  
        [OperationContract]  
        EndpointAddress10 GetInstanceAddress();  
    }  
```  
  
 <span data-ttu-id="128d8-195">Aşağıda, bu hizmet uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="128d8-195">Following is the implementation of this service.</span></span> <span data-ttu-id="128d8-196">Bu uygulama kapatamaması nesneleri oluşturmak için singleton kanal fabrikası tutar.</span><span class="sxs-lookup"><span data-stu-id="128d8-196">This implementation maintains a singleton channel factory to create sessionful objects.</span></span>  <span data-ttu-id="128d8-197">Zaman `GetInstanceAddress` olan çağrılır, bir kanal oluşturur ve oluşturur bir <xref:System.ServiceModel.EndpointAddress10> bu kanal ile ilişkili uzak adresini işaret eden bir nesne.</span><span class="sxs-lookup"><span data-stu-id="128d8-197">When `GetInstanceAddress` is called, it creates a channel and creates an <xref:System.ServiceModel.EndpointAddress10> object that points to the remote address associated with this channel.</span></span>   <span data-ttu-id="128d8-198"><xref:System.ServiceModel.EndpointAddress10> İstemci tarafından değeri olarak döndürülebilecek bir veri türü var.</span><span class="sxs-lookup"><span data-stu-id="128d8-198"><xref:System.ServiceModel.EndpointAddress10> is a data type that can be returned to the client by-value.</span></span>  
  
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
  
### <a name="step-3-configure-and-start-the-wcf-services"></a><span data-ttu-id="128d8-199">3. Adım: Yapılandırma ve WCF hizmetlerini başlatma</span><span class="sxs-lookup"><span data-stu-id="128d8-199">Step 3: Configure and start the WCF services</span></span>  
 <span data-ttu-id="128d8-200">Bu hizmetler barındırmak için sunucu yapılandırma dosyasında (web.config) aşağıdaki eklemeler olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="128d8-200">To host these services, you will need to make the following additions to the server’s configuration file (web.config).</span></span>  
  
1.  <span data-ttu-id="128d8-201">Ekleme bir `<client>` kapatamaması nesne için uç nokta açıklayan bölümü.</span><span class="sxs-lookup"><span data-stu-id="128d8-201">Add a `<client>` section that describes the endpoint for the sessionful object.</span></span>  <span data-ttu-id="128d8-202">Bu senaryoda, sunucu da bir istemci olarak davranır ve bu ayarı etkinleştirmek için yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="128d8-202">In this scenario, the server also acts as a client and must be configured to enable this.</span></span>  
  
2.  <span data-ttu-id="128d8-203">İçinde `<services>` bölümünde, Fabrika ve sessionful nesne için hizmet uç noktalarını bildirir.</span><span class="sxs-lookup"><span data-stu-id="128d8-203">In the `<services>` section, declare service endpoints for the factory and sessionful object.</span></span>  <span data-ttu-id="128d8-204">Bu hizmet uç noktaları ile iletişim kurmak, almak istemci sağlar <xref:System.ServiceModel.EndpointAddress10> ve oturum kanalı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="128d8-204">This enables the client to communicate with the service endpoints, acquire the <xref:System.ServiceModel.EndpointAddress10> and create the sessionful channel.</span></span>  
  
 <span data-ttu-id="128d8-205">Bu ayarlarla örnek bir yapılandırma dosyası aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="128d8-205">Following is an example configuration file with these settings:</span></span>  
  
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
  
 <span data-ttu-id="128d8-206">Barındırılan hizmet için bir konsol uygulaması için aşağıdaki satırları ekleyin ve uygulamayı başlatın.</span><span class="sxs-lookup"><span data-stu-id="128d8-206">Add the following lines to a console application, to self-host the service, and start the app.</span></span>  
  
```csharp  
ServiceHost factoryHost = new ServiceHost(typeof(SessionBoundFactory));  
factoryHost.Open();  
  
ServiceHost sessionBoundServiceHost = new ServiceHost(  
typeof(MySessionBoundObject));  
sessionBoundServiceHost.Open();  
```  
  
### <a name="step-4-configure-the-client-and-call-the-service"></a><span data-ttu-id="128d8-207">4. Adım: İstemciyi yapılandırma ve hizmet çağrısı</span><span class="sxs-lookup"><span data-stu-id="128d8-207">Step 4: Configure the client and call the service</span></span>  
 <span data-ttu-id="128d8-208">Projenin uygulama yapılandırma dosyasına (app.config) aşağıdaki girdileri yaparak WCF hizmetleri ile iletişim kuracak istemci yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="128d8-208">Configure the client to communicate with the WCF services by making the following entries in the project’s application configuration file (app.config).</span></span>  
  
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
  
 <span data-ttu-id="128d8-209">Hizmeti çağırmak için aşağıdakileri yapmak için istemci kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="128d8-209">To call the service, add the code to the client to do the following:</span></span>  
  
1.  <span data-ttu-id="128d8-210">Bir kanal oluşturmaya `ISessionBoundFactory` hizmeti.</span><span class="sxs-lookup"><span data-stu-id="128d8-210">Create a channel to the `ISessionBoundFactory` service.</span></span>  
  
2.  <span data-ttu-id="128d8-211">Çağrılacak kanalı kullanmaya `ISessionBoundFactory` elde bir hizmet bir <xref:System.ServiceModel.EndpointAddress10> nesne.</span><span class="sxs-lookup"><span data-stu-id="128d8-211">Use the channel to invoke the `ISessionBoundFactory` service an obtain an <xref:System.ServiceModel.EndpointAddress10> object.</span></span>  
  
3.  <span data-ttu-id="128d8-212">Kullanım <xref:System.ServiceModel.EndpointAddress10> kapatamaması bir nesne elde etmek için bir kanal oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="128d8-212">Use the <xref:System.ServiceModel.EndpointAddress10> to create a channel to obtain a sessionful object.</span></span>  
  
4.  <span data-ttu-id="128d8-213">Çağrı `SetCurrentValue` ve `GetCurrentValue` arasında birden çok çağrı yöntemleri aynı nesne örneği kaldığı göstermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="128d8-213">Call the `SetCurrentValue` and `GetCurrentValue` methods to demonstrate it remains the same object instance is used across multiple calls.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="128d8-214">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="128d8-214">See Also</span></span>  
 [<span data-ttu-id="128d8-215">Temel WCF Programlama</span><span class="sxs-lookup"><span data-stu-id="128d8-215">Basic WCF Programming</span></span>](../../../docs/framework/wcf/basic-wcf-programming.md)  
 [<span data-ttu-id="128d8-216">Hizmetleri Tasarlama ve Uygulama</span><span class="sxs-lookup"><span data-stu-id="128d8-216">Designing and Implementing Services</span></span>](../../../docs/framework/wcf/designing-and-implementing-services.md)  
 [<span data-ttu-id="128d8-217">İstemci Derleme</span><span class="sxs-lookup"><span data-stu-id="128d8-217">Building Clients</span></span>](../../../docs/framework/wcf/building-clients.md)  
 [<span data-ttu-id="128d8-218">Çift Yönlü Hizmetler</span><span class="sxs-lookup"><span data-stu-id="128d8-218">Duplex Services</span></span>](../../../docs/framework/wcf/feature-details/duplex-services.md)
