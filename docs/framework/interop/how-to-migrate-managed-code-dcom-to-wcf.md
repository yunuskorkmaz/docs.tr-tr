---
title: 'Nasıl yapılır: Yönetilen Kodu DCOM’dan WCF’ye Geçirme'
ms.date: 03/30/2017
ms.assetid: 52961ffc-d1c7-4f83-832c-786444b951ba
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 187bff7c75ba2a0887e3c5728a484a9231936511
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33392752"
---
# <a name="how-to-migrate-managed-code-dcom-to-wcf"></a><span data-ttu-id="f6cd0-102">Nasıl yapılır: Yönetilen Kodu DCOM’dan WCF’ye Geçirme</span><span class="sxs-lookup"><span data-stu-id="f6cd0-102">How to: Migrate Managed-Code DCOM to WCF</span></span>
<span data-ttu-id="f6cd0-103">Windows Communication Foundation (WCF), güvenli ve önerilen seçenek yönetilen kod çağrıları sunucular ve istemciler dağıtılmış bir ortama arasında Dağıtılmış Bileşen Nesne Modeli (DCOM) üzerinden içindir.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-103">Windows Communication Foundation (WCF) is the recommended and secure choice over Distributed Component Object Model (DCOM) for managed code calls between servers and clients in a distributed environment.</span></span> <span data-ttu-id="f6cd0-104">Bu makalede gösterilmektedir nasıl kod DCOM'dan WCF'ye aşağıdaki senaryolar için geçirme için.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-104">This article shows how you to migrate code from DCOM to WCF for the following scenarios.</span></span>  
  
-   <span data-ttu-id="f6cd0-105">Uzak Hizmet istemciye bir nesne tarafından-değeri döndürür</span><span class="sxs-lookup"><span data-stu-id="f6cd0-105">The remote service returns an object by-value to the client</span></span>  
  
-   <span data-ttu-id="f6cd0-106">İstemci bir nesne tarafından-değeri uzak hizmetine gönderir.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-106">The client sends an object by-value to the remote service</span></span>  
  
-   <span data-ttu-id="f6cd0-107">Uzak Hizmet bir nesne başvuru tarafından istemciye döndürür.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-107">The remote service returns an object by-reference to the client</span></span>  
  
 <span data-ttu-id="f6cd0-108">Güvenlik nedeniyle, bir nesne başvuru tarafından istemciden hizmete gönderme WCF içinde izin verilmiyor.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-108">For security reasons, sending an object by-reference from the client to the service is not allowed in WCF.</span></span> <span data-ttu-id="f6cd0-109">İstemci ve sunucu arasında geri ve ileri bir konuşma gerektiren bir senaryo çift yönlü hizmetini kullanarak WCF'de elde edilebilir.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-109">A scenario that requires a conversation back and forth between client and server can be achieved in WCF using a duplex service.</span></span>  <span data-ttu-id="f6cd0-110">Çift yönlü hizmetler hakkında daha fazla bilgi için bkz: [çift yönlü Hizmetler](../../../docs/framework/wcf/feature-details/duplex-services.md).</span><span class="sxs-lookup"><span data-stu-id="f6cd0-110">For more information about duplex services, see [Duplex Services](../../../docs/framework/wcf/feature-details/duplex-services.md).</span></span>  
  
 <span data-ttu-id="f6cd0-111">WCF hizmetleri ve istemciler bu hizmetlerin oluşturma hakkında daha fazla bilgi için bkz: [temel WCF programlama](../../../docs/framework/wcf/basic-wcf-programming.md), [Hizmetleri Tasarlama ve uygulama](../../../docs/framework/wcf/designing-and-implementing-services.md), ve [istemci derleme](../../../docs/framework/wcf/building-clients.md).</span><span class="sxs-lookup"><span data-stu-id="f6cd0-111">For more details about creating WCF services and clients for those services, see [Basic WCF Programming](../../../docs/framework/wcf/basic-wcf-programming.md), [Designing and Implementing Services](../../../docs/framework/wcf/designing-and-implementing-services.md), and [Building Clients](../../../docs/framework/wcf/building-clients.md).</span></span>  
  
## <a name="dcom-example-code"></a><span data-ttu-id="f6cd0-112">DCOM örnek kod</span><span class="sxs-lookup"><span data-stu-id="f6cd0-112">DCOM example code</span></span>  
 <span data-ttu-id="f6cd0-113">Bu senaryolarda, WCF kullanarak gösterilmiştir DCOM arabirimleri aşağıdaki yapı ayarlanmıştır:</span><span class="sxs-lookup"><span data-stu-id="f6cd0-113">For these scenarios, the DCOM interfaces that are illustrated using WCF have the following structure:</span></span>  
  
```  
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
  
## <a name="the-service-returns-an-object-by-value"></a><span data-ttu-id="f6cd0-114">Hizmet bir nesne tarafından-değeri döndürür</span><span class="sxs-lookup"><span data-stu-id="f6cd0-114">The service returns an object by-value</span></span>  
 <span data-ttu-id="f6cd0-115">Bu senaryo için bir değer tarafından sunucudan istemciye geçirilir nesne yöntemi döndürür ve bir hizmet için bir çağrı olun.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-115">For this scenario, you make a call to a service and it method returns an object, which is passed by-value from the server to the client.</span></span> <span data-ttu-id="f6cd0-116">Bu senaryo aşağıdaki COM çağrısını temsil eder:</span><span class="sxs-lookup"><span data-stu-id="f6cd0-116">This scenario represents the following COM call:</span></span>  
  
```  
public interface IRemoteService  
{  
    Customer GetObjectByValue();  
}  
```  
  
 <span data-ttu-id="f6cd0-117">Bu senaryoda, istemci uzak hizmetinden bir nesne seri durumdan çıkarılmış bir kopyasını alır.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-117">In this scenario, the client receives a deserialized copy of an object from the remote service.</span></span> <span data-ttu-id="f6cd0-118">İstemci hizmete geri çağırma olmadan bu yerel bir kopya ile etkileşim kurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-118">The client can interact with this local copy without calling back to the service.</span></span>  <span data-ttu-id="f6cd0-119">Diğer bir deyişle, istemci yerel kopya yöntemler çağrıldığında hizmet herhangi bir şekilde dahil olacaktır değil garanti edilmez.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-119">In other words, the client is guaranteed the service will not be involved in any way when methods on the local copy are called.</span></span> <span data-ttu-id="f6cd0-120">Aşağıdaki adımlar, normal bir WCF hizmeti oluşturma açıklamaktadır şekilde WCF her zaman nesneleri hizmetinden değere göre döndürür.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-120">WCF always returns objects from the service by value, so the following steps describe creating a regular WCF service.</span></span>  
  
### <a name="step-1-define-the-wcf-service-interface"></a><span data-ttu-id="f6cd0-121">1. adım: WCF Hizmeti arabirimi tanımlama</span><span class="sxs-lookup"><span data-stu-id="f6cd0-121">Step 1: Define the WCF service interface</span></span>  
 <span data-ttu-id="f6cd0-122">WCF hizmeti için ortak bir arabirim tanımlayın ve ile işaretleyin [<xref:System.ServiceModel.ServiceContractAttribute>] özniteliği.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-122">Define a public interface for the WCF service and mark it with the [<xref:System.ServiceModel.ServiceContractAttribute>] attribute.</span></span>  <span data-ttu-id="f6cd0-123">İstemcilerle kullanıma sunmak istediğiniz yöntemleri işaretleme [<xref:System.ServiceModel.OperationContractAttribute>] özniteliği.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-123">Mark the methods you want to expose to clients with the [<xref:System.ServiceModel.OperationContractAttribute>] attribute.</span></span> <span data-ttu-id="f6cd0-124">Aşağıdaki örnek, bir istemci çağırabilirsiniz arabirim yöntemleri ve sunucu tarafı arabirimi tanımlamak için bu öznitelikleri kullanma gösterir.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-124">The following example shows using these attributes to identify the server-side interface and interface methods a client can call.</span></span> <span data-ttu-id="f6cd0-125">Bu senaryo için kullanılan yöntem kalın olarak gösterilir.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-125">The method used for this scenario is shown in bold.</span></span>  
  
```  
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
  
### <a name="step-2-define-the-data-contract"></a><span data-ttu-id="f6cd0-126">2. adım: veri sözleşmesi tanımlayın</span><span class="sxs-lookup"><span data-stu-id="f6cd0-126">Step 2: Define the data contract</span></span>  
 <span data-ttu-id="f6cd0-127">Sonraki nasıl veri hizmet ve istemcileri arasında alınıp verilecek anlatmaktadır hizmeti için bir veri sözleşmesi oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-127">Next you should create a data contract for the service, which will describe how the data will be exchanged between the service and its clients.</span></span>  <span data-ttu-id="f6cd0-128">Veri sözleşmesi açıklanan sınıflar ile işaretlenmelidir [<xref:System.Runtime.Serialization.DataContractAttribute>] özniteliği.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-128">Classes described in the data contract should be marked with the [<xref:System.Runtime.Serialization.DataContractAttribute>] attribute.</span></span> <span data-ttu-id="f6cd0-129">Tek tek özellikleri veya hem istemci hem de sunucu görünür istediğiniz alanları ile işaretlenmelidir [<xref:System.Runtime.Serialization.DataMemberAttribute>] özniteliği. İzin verilmesi için veri sözleşmesindeki sınıfından türetilmiş türler istiyorsanız tanımlamalıdır [<xref:System.Runtime.Serialization.KnownTypeAttribute>] özniteliği.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-129">The individual properties or fields you want visible to both client and server should be marked with the [<xref:System.Runtime.Serialization.DataMemberAttribute>] attribute.If you want types derived from a class in the data contract to be allowed, you must identify them with the [<xref:System.Runtime.Serialization.KnownTypeAttribute>] attribute.</span></span> <span data-ttu-id="f6cd0-130">WCF yalnızca serileştirmek veya hizmet arayüzündeki türleri ve bilinen türleri olarak tanımlanan türler seri durumdan.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-130">WCF will only serialize or deserialize types in the service interface and types identified as known types.</span></span> <span data-ttu-id="f6cd0-131">Bilinen bir türe sahip olmayan bir tür kullanmayı denerseniz, bir özel durum meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-131">If you attempt to use a type that is not a known type, an exception will occur.</span></span>  
  
 <span data-ttu-id="f6cd0-132">Veri sözleşmeleri hakkında daha fazla bilgi için bkz: [veri sözleşmeleri](../../../docs/framework/wcf/samples/data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="f6cd0-132">For more information about data contracts, see [Data Contracts](../../../docs/framework/wcf/samples/data-contracts.md).</span></span>  
  
```  
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
  
### <a name="step-3-implement-the-wcf-service"></a><span data-ttu-id="f6cd0-133">3. adım: WCF Hizmeti uygulama</span><span class="sxs-lookup"><span data-stu-id="f6cd0-133">Step 3: Implement the WCF service</span></span>  
 <span data-ttu-id="f6cd0-134">Ardından, önceki adımda tanımlanan arabirimini uygulayan WCF hizmet sınıfı uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-134">Next, you should implement the WCF service class that implements the interface you defined in the previous step.</span></span>  
  
```  
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
  
### <a name="step-4-configure-the-service-and-the-client"></a><span data-ttu-id="f6cd0-135">4. adım: hizmet ve istemci yapılandırma</span><span class="sxs-lookup"><span data-stu-id="f6cd0-135">Step 4: Configure the service and the client</span></span>  
 <span data-ttu-id="f6cd0-136">Bir WCF hizmetini çalıştırmak için belirli bir WCF bağlamayı kullanarak belirli bir URL, bu hizmet arabirimi kullanıma sunan bir uç nokta bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-136">To run a WCF service, you need to declare an endpoint that exposes that service interface at a specific URL using a specific WCF binding.</span></span> <span data-ttu-id="f6cd0-137">Bağlama istemciler ve sunucu iletişim kurmak Aktarım, kodlama ve protokol ayrıntılarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-137">A binding specifies the transport, encoding and protocol details for the clients and server to communicate.</span></span> <span data-ttu-id="f6cd0-138">Genellikle hizmet projesinin yapılandırma dosyasında (web.config) bağlamaları ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-138">You typically add bindings to the service project’s configuration file (web.config).</span></span> <span data-ttu-id="f6cd0-139">Aşağıdaki örnek hizmeti için bir bağlama girişi gösterir:</span><span class="sxs-lookup"><span data-stu-id="f6cd0-139">The following shows a binding entry for the example service:</span></span>  
  
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
  
 <span data-ttu-id="f6cd0-140">Ardından, istemci hizmeti tarafından belirtilen bağlama bilgileri eşleşecek şekilde yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-140">Next, you need to configure the client to match the binding information specified by the service.</span></span> <span data-ttu-id="f6cd0-141">Bunu yapmak için aşağıdaki istemci uygulaması (app.config) yapılandırma dosyasına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-141">To do so, add the following to the client’s application configuration (app.config) file.</span></span>  
  
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
  
### <a name="step-5-run-the-service"></a><span data-ttu-id="f6cd0-142">5. adım: hizmet çalıştırma</span><span class="sxs-lookup"><span data-stu-id="f6cd0-142">Step 5: Run the service</span></span>  
 <span data-ttu-id="f6cd0-143">Son olarak, bunu bir konsol uygulamasında aşağıdaki satırları hizmet uygulamasına ekleme ve uygulama başlatma Self barındırabilir.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-143">Finally, you can self-host it in a console application by adding the following lines to the service app, and starting the app.</span></span> <span data-ttu-id="f6cd0-144">Bir WCF Hizmeti uygulamasını barındırmak için diğer yolları hakkında daha fazla bilgi için [barındırma hizmetleri](../../../docs/framework/wcf/hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="f6cd0-144">For more information about other ways to host a WCF service application, [Hosting Services](../../../docs/framework/wcf/hosting-services.md).</span></span>  
  
```  
ServiceHost customerServiceHost = new ServiceHost(typeof(CustomerService));  
customerServiceHost.Open();  
```  
  
### <a name="step-6-call-the-service-from-the-client"></a><span data-ttu-id="f6cd0-145">6. adım: hizmet istemciden çağırın.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-145">Step 6: Call the service from the client</span></span>  
 <span data-ttu-id="f6cd0-146">Hizmeti istemciden çağırmak için bir kanal fabrikası hizmeti oluşturmanız ve doğrudan çağırmak sağlayacak bir kanal istemek için gereken `GetCustomer` doğrudan istemciden yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-146">To call the service from the client, you need to create a channel factory for the service, and request a channel, which will enable you to directly call the `GetCustomer` method directly from the client.</span></span> <span data-ttu-id="f6cd0-147">Kanal hizmetin arabirimini uygulayan ve temel alınan istek/yanıt mantığı işler.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-147">The channel implements the service’s interface and handles the underlying request/reply logic for you.</span></span>  <span data-ttu-id="f6cd0-148">Bu yöntem çağrısının dönüş değerini, hizmet yanıtı seri durumdan çıkarılmış kopyasıdır.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-148">The return value from that method call is the deserialized copy of the service response.</span></span>  
  
```  
ChannelFactory<ICustomerManager> factory =   
     new ChannelFactory<ICustomerManager>("customermanager");  
ICustomerManager service = factory.CreateChannel();  
Customer customer = service.GetCustomer("Mary", "Smith");  
```  
  
## <a name="the-client-sends-a-by-value-object-to-the-server"></a><span data-ttu-id="f6cd0-149">İstemci bir değer tarafından nesnesi sunucuya gönderir.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-149">The client sends a by-value object to the server</span></span>  
 <span data-ttu-id="f6cd0-150">Bu senaryoda, bir nesneye sunucuya istemci gönderir tarafından değeri.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-150">In this scenario, the client sends an object to the server, by-value.</span></span> <span data-ttu-id="f6cd0-151">Bu, sunucunun nesne seri durumdan çıkarılmış bir kopyasını alacak anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-151">This means that the server will receive a deserialized copy of the object.</span></span>  <span data-ttu-id="f6cd0-152">Sunucu yöntemleri Bu kopyada çağırabilir ve istemci koda hiçbir geri çağırma olduğu garanti.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-152">The server can call methods on that copy and be guaranteed there is no callback into client code.</span></span> <span data-ttu-id="f6cd0-153">Daha önce belirtildiği gibi verileri normal WCF alışverişleri değer tarafından şunlardır.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-153">As mentioned previously, normal WCF exchanges of data are by-value.</span></span>  <span data-ttu-id="f6cd0-154">Bu garanti Bu nesnelerden birini yöntemleri çağırma yerel olarak yalnızca yürütür – istemci kodu çağırma kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-154">This guarantees that calling methods on one of these objects executes locally only – it will not invoke code on the client.</span></span>  
  
 <span data-ttu-id="f6cd0-155">Bu senaryo aşağıdaki COM yöntemi çağrısını temsil eder:</span><span class="sxs-lookup"><span data-stu-id="f6cd0-155">This scenario represents the following COM method call:</span></span>  
  
```  
public interface IRemoteService  
{  
    void SendObjectByValue(Customer customer);  
}  
```  
  
 <span data-ttu-id="f6cd0-156">Bu senaryo, ilk örnekte gösterildiği gibi aynı hizmet arabirimi ve veri sözleşmesi kullanır.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-156">This scenario uses the same service interface and data contract as shown in the first example.</span></span> <span data-ttu-id="f6cd0-157">Ayrıca, istemci ve hizmet aynı şekilde yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-157">In addition, the client and service will be configured in the same way.</span></span> <span data-ttu-id="f6cd0-158">Bu örnekte, nesne göndermek ve aynı şekilde çalıştırmak için bir kanal oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-158">In this example, a channel is created to send the object and run the same way.</span></span> <span data-ttu-id="f6cd0-159">Ancak, bu örnekte, bir nesne tarafından-değeri geçirme hizmeti çağıran bir istemci oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-159">However, for this example, you will create a client that calls the service, passing an object by-value.</span></span> <span data-ttu-id="f6cd0-160">İstemci hizmet sözleşmesinde çağıracak hizmet yöntemi kalın olarak gösterilir:</span><span class="sxs-lookup"><span data-stu-id="f6cd0-160">The service method the client will call in the service contract is shown in bold:</span></span>  
  
```  
[ServiceContract]  
public interface ICustomerManager  
{  
    [OperationContract]     void StoreCustomer(Customer customer);  
  
    [OperationContract]  
    Customer GetCustomer(string firstName, string lastName);  
}  
```  
  
### <a name="add-code-to-the-client-that-sends-a-by-value-object"></a><span data-ttu-id="f6cd0-161">Bir değer tarafından nesnesi gönderir istemci kodu ekleyin</span><span class="sxs-lookup"><span data-stu-id="f6cd0-161">Add code to the client that sends a by-value object</span></span>  
 <span data-ttu-id="f6cd0-162">Aşağıdaki kod gösterdiği istemci yeni bir değer tarafından müşteri nesnesi oluşturur nasıl ile iletişim kurmak için bir kanal oluşturur `ICustomerManager` hizmet ve müşteri nesnesi gönderir.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-162">The following code shows how the client creates a new by-value customer object, creates a channel to communicate with the `ICustomerManager` service, and sends the customer object to it.</span></span>  
  
 <span data-ttu-id="f6cd0-163">Müşteri nesnesi seri hale getirilmiş ve burada bu hizmet tarafından söz konusu nesne yeni bir kopyasını seri durumdan olan hizmete gönderilen.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-163">The customer object will be serialized, and sent to the service, where it is deserialized by the service into a new copy of that object.</span></span>  <span data-ttu-id="f6cd0-164">Hizmet çağrıları bu nesne üzerinde herhangi bir yöntem yalnızca yerel olarak yürütecek sunucusunda. Bu kod türetilmiş bir tür gönderme gösterir dikkate almak önemlidir (`PremiumCustomer`).</span><span class="sxs-lookup"><span data-stu-id="f6cd0-164">Any methods the service calls on this object will execute only locally on the server.It’s important to note that this code illustrates sending a derived type (`PremiumCustomer`).</span></span>  <span data-ttu-id="f6cd0-165">Hizmet sözleşmesi bekliyor bir `Customer` nesne ancak hizmet verileri sözleşme kullanır [<xref:System.Runtime.Serialization.KnownTypeAttribute>] özniteliğini belirtmek için `PremiumCustomer` de izin verilir.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-165">The service contract expects a `Customer` object, but the service data contract uses the [<xref:System.Runtime.Serialization.KnownTypeAttribute>] attribute to indicate that `PremiumCustomer` is also allowed.</span></span>  <span data-ttu-id="f6cd0-166">WCF serileştirmek veya bu hizmeti arabirimi aracılığıyla herhangi bir türü seri durumdan girişimleri başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-166">WCF will fail attempts to serialize or deserialize any other type via this service interface.</span></span>  
  
```  
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
  
## <a name="the-service-returns-an-object-by-reference"></a><span data-ttu-id="f6cd0-167">Hizmet başvuruya göre bir nesne döndürür</span><span class="sxs-lookup"><span data-stu-id="f6cd0-167">The service returns an object by reference</span></span>  
 <span data-ttu-id="f6cd0-168">Bu senaryo için istemci uygulaması uzak hizmet için bir çağrı yapar ve yöntem başvuru hizmetinden istemci tarafından geçirilen bir nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-168">For this scenario, the client app makes a call to the remote service and the method returns an object, which is passed by reference from the service to the client.</span></span>  
  
 <span data-ttu-id="f6cd0-169">Daha önce belirtildiği gibi WCF hizmetleri zaman nesnesi tarafından dönüş değeri.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-169">As mentioned previously, WCF services always return object by value.</span></span>  <span data-ttu-id="f6cd0-170">Ancak, kullanarak benzer bir sonuç elde edebilirsiniz <xref:System.ServiceModel.EndpointAddress10> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-170">However, you can achieve a similar result by using the <xref:System.ServiceModel.EndpointAddress10> class.</span></span>  <span data-ttu-id="f6cd0-171"><xref:System.ServiceModel.EndpointAddress10> Sunucuda süre sonuyla başvuru tarafından nesnesi edinmek için istemci tarafından kullanılan bir değer tarafından seri hale getirilebilir nesnesidir.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-171">The <xref:System.ServiceModel.EndpointAddress10> is a serializable by-value object that can be used by the client to obtain a sessionful by-reference object on the server.</span></span>  
  
 <span data-ttu-id="f6cd0-172">Bu senaryoda gösterildiği WCF tarafından başvuru nesnesinde davranışını DCOM farklıdır.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-172">The behavior of the by-reference object in WCF shown in this scenario is different than DCOM.</span></span>  <span data-ttu-id="f6cd0-173">DCOM, sunucu tarafından başvuru nesnesi istemciye doğrudan döndürebilir ve istemci sunucuda yürütmek o nesnenin yöntemleri çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-173">In DCOM, the server can return a by-reference object to the client directly, and the client can call that object’s methods, which execute on the server.</span></span>  <span data-ttu-id="f6cd0-174">WCF'de, ancak döndürülen nesne olduğundan her zaman tarafından-değeri.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-174">In WCF, however, the object returned is always by-value.</span></span>  <span data-ttu-id="f6cd0-175">İstemci tarafından temsil edilen bu değer tarafından nesnesi almalıdır <xref:System.ServiceModel.EndpointAddress10> ve kendi süre sonuyla başvuru tarafından nesnesi oluşturmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-175">The client must take that by-value object, represented by <xref:System.ServiceModel.EndpointAddress10> and use it to create its own sessionful by-reference object.</span></span>  <span data-ttu-id="f6cd0-176">İstemci yöntem çağrılarını süre sonuyla nesnesinde sunucuda yürütün. Diğer bir deyişle, bu başvuru tarafından WCF süre sonuyla olacak şekilde yapılandırıldığında normal bir WCF Hizmeti nesnedir.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-176">The client method calls on the sessionful object execute on the server.In other words, this by-reference object in WCF is a normal WCF service that is configured to be sessionful.</span></span>  
  
 <span data-ttu-id="f6cd0-177">WCF'de, bir oturum iki uç noktaları arasında gönderilen birden fazla ileti bağıntı bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-177">In WCF, a session is a way of correlating multiple messages sent between two endpoints.</span></span>  <span data-ttu-id="f6cd0-178">Bu, bir istemci bu hizmet için bir bağlantı alır sonra bir oturum istemci ve sunucu arasında kurulacak olduğunu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-178">This means that once a client obtains a connection to this service, a session will be established between the client and the server.</span></span>  <span data-ttu-id="f6cd0-179">İstemci bu tek oturum içinde kendi etkileşimler için sunucu tarafı nesnesi tek bir benzersiz örneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-179">The client will use a single unique instance of the server-side object for all its interactions within this single session.</span></span> <span data-ttu-id="f6cd0-180">Süre sonuyla WCF sözleşmeleri bağlantı odaklı ağ istek/yanıt desenlerini benzerdir.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-180">Sessionful WCF contracts are similar to connection-oriented network request/response patterns.</span></span>  
  
 <span data-ttu-id="f6cd0-181">Bu senaryo aşağıdaki DCOM yöntemi tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-181">This scenario is represented by the following DCOM method.</span></span>  
  
```  
public interface IRemoteService  
{  
    IRemoteObject GetObjectByReference();  
}  
```  
  
### <a name="step-1-define-the-sessionful-wcf-service-interface-and-implementation"></a><span data-ttu-id="f6cd0-182">1. adım: uygulama ve Sessionful WCF Hizmeti arabirimi tanımlayın</span><span class="sxs-lookup"><span data-stu-id="f6cd0-182">Step 1: Define the Sessionful WCF service interface and implementation</span></span>  
 <span data-ttu-id="f6cd0-183">İlk olarak, süre sonuyla nesnesini içeren bir WCF Hizmeti arabirimi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-183">First, define a WCF service interface that contains the sessionful object.</span></span>  
  
 <span data-ttu-id="f6cd0-184">Bu kodda süre sonuyla nesnesi ile işaretlenen `ServiceContract` normal bir WCF Hizmeti arabirimi tanımlayan özniteliği.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-184">In this code, the sessionful object is marked with the `ServiceContract` attribute, which identifies it as a regular WCF service interface.</span></span>  <span data-ttu-id="f6cd0-185">Ayrıca, <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> özelliği süre sonuyla bir hizmet olarak göstermek için ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-185">In addition, the <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> property is set to indicate it will be a sessionful service.</span></span>  
  
```  
[ServiceContract(SessionMode = SessionMode.Allowed)]  
public interface ISessionBoundObject  
{  
    [OperationContract]  
    string GetCurrentValue();  
  
    [OperationContract]  
    void SetCurrentValue(string value);  
}  
```  
  
 <span data-ttu-id="f6cd0-186">Aşağıdaki kod, hizmet uygulamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-186">The following code shows the service implementation.</span></span>  
  
 <span data-ttu-id="f6cd0-187">Hizmet [ServiceBehavior] özniteliğiyle işaretlenmiş ve bu tür benzersiz bir örnek her oturum için oluşturulması gerektiğini belirtmek için InstanceContextMode.PerSessions için kendi InstanceContextMode özelliğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-187">The service is marked with the [ServiceBehavior] attribute, and its InstanceContextMode property set to InstanceContextMode.PerSessions to indicate that a unique instance of this type should be created for each session.</span></span>  
  
```  
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
  
### <a name="step-2-define-the-wcf-factory-service-for-the-sessionful-object"></a><span data-ttu-id="f6cd0-188">2. adım: süre sonuyla nesnesi için WCF Fabrika hizmeti tanımlayın</span><span class="sxs-lookup"><span data-stu-id="f6cd0-188">Step 2: Define the WCF factory service for the sessionful object</span></span>  
 <span data-ttu-id="f6cd0-189">Süre sonuyla nesnesi oluşturur hizmet tanımlı ve uygulanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-189">The service that creates the sessionful object must be defined and implemented.</span></span> <span data-ttu-id="f6cd0-190">Aşağıdaki kod bunun nasıl yapılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-190">The following code shows how to do this.</span></span> <span data-ttu-id="f6cd0-191">Bu kod döndürür başka bir WCF Hizmeti oluşturur bir <xref:System.ServiceModel.EndpointAddress10> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-191">This code creates another WCF service that returns an <xref:System.ServiceModel.EndpointAddress10> object.</span></span>  <span data-ttu-id="f6cd0-192">Bu seri hale getirilebilir bir uç nokta can biçimidir oturum tam nesnesi oluşturmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-192">This is a serializable form of an endpoint the can use to create the session-full object.</span></span>  
  
```  
[ServiceContract]  
    public interface ISessionBoundFactory  
    {  
        [OperationContract]  
        EndpointAddress10 GetInstanceAddress();  
    }  
```  
  
 <span data-ttu-id="f6cd0-193">Bu hizmet uygulaması aşağıdadır.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-193">Following is the implementation of this service.</span></span> <span data-ttu-id="f6cd0-194">Bu uygulama süre sonuyla nesneleri oluşturmak için bir singleton kanal fabrikası tutar.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-194">This implementation maintains a singleton channel factory to create sessionful objects.</span></span>  <span data-ttu-id="f6cd0-195">Zaman `GetInstanceAddress` olan adlı bir kanal oluşturur ve oluşturur bir <xref:System.ServiceModel.EndpointAddress10> bu kanal ile ilişkili uzak adresine işaret eden nesne.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-195">When `GetInstanceAddress` is called, it creates a channel and creates an <xref:System.ServiceModel.EndpointAddress10> object that points to the remote address associated with this channel.</span></span>   <span data-ttu-id="f6cd0-196"><xref:System.ServiceModel.EndpointAddress10> İstemci tarafından değerinin döndürülen bir veri türüdür.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-196"><xref:System.ServiceModel.EndpointAddress10> is a data type that can be returned to the client by-value.</span></span>  
  
```  
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
  
### <a name="step-3-configure-and-start-the-wcf-services"></a><span data-ttu-id="f6cd0-197">Adım 3: Yapılandırma ve WCF hizmetlerini başlatın</span><span class="sxs-lookup"><span data-stu-id="f6cd0-197">Step 3: Configure and start the WCF services</span></span>  
 <span data-ttu-id="f6cd0-198">Bu hizmetler barındırmak için sunucu yapılandırma dosyasında (web.config) aşağıdaki eklemeler yapmak gerekir.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-198">To host these services, you will need to make the following additions to the server’s configuration file (web.config).</span></span>  
  
1.  <span data-ttu-id="f6cd0-199">Ekleme bir `<client>` süre sonuyla nesne için uç noktaya açıklayan bölümü.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-199">Add a `<client>` section that describes the endpoint for the sessionful object.</span></span>  <span data-ttu-id="f6cd0-200">Bu senaryoda, sunucu da bir istemci olarak davranır ve bu ayarı etkinleştirmek için yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-200">In this scenario, the server also acts as a client and must be configured to enable this.</span></span>  
  
2.  <span data-ttu-id="f6cd0-201">İçinde `<services>` bölümünde, hizmet uç noktaları Fabrika ve sessionful nesnesinin bildirin.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-201">In the `<services>` section, declare service endpoints for the factory and sessionful object.</span></span>  <span data-ttu-id="f6cd0-202">Bu hizmet uç noktaları ile iletişim kurmak için alma istemci sağlar <xref:System.ServiceModel.EndpointAddress10> ve süre sonuyla kanal oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-202">This enables the client to communicate with the service endpoints, acquire the <xref:System.ServiceModel.EndpointAddress10> and create the sessionful channel.</span></span>  
  
 <span data-ttu-id="f6cd0-203">Bu ayarlarla örnek bir yapılandırma dosyası aşağıdadır:</span><span class="sxs-lookup"><span data-stu-id="f6cd0-203">Following is an example configuration file with these settings:</span></span>  
  
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
  
 <span data-ttu-id="f6cd0-204">Self Servis barındırmak için bir konsol uygulaması için aşağıdaki satırları ekleyin ve uygulamayı başlatın.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-204">Add the following lines to a console application, to self-host the service, and start the app.</span></span>  
  
```  
ServiceHost factoryHost = new ServiceHost(typeof(SessionBoundFactory));  
factoryHost.Open();  
  
ServiceHost sessionBoundServiceHost = new ServiceHost(  
typeof(MySessionBoundObject));  
sessionBoundServiceHost.Open();  
```  
  
### <a name="step-4-configure-the-client-and-call-the-service"></a><span data-ttu-id="f6cd0-205">4. adım: istemciyi Yapılandırma ve hizmet çağırın</span><span class="sxs-lookup"><span data-stu-id="f6cd0-205">Step 4: Configure the client and call the service</span></span>  
 <span data-ttu-id="f6cd0-206">Projenin uygulama yapılandırma dosyasına (app.config) aşağıdaki girdileri yaparak WCF hizmetleri ile iletişim kurmak için istemci yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-206">Configure the client to communicate with the WCF services by making the following entries in the project’s application configuration file (app.config).</span></span>  
  
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
  
 <span data-ttu-id="f6cd0-207">Hizmetini çağırmak için aşağıdakileri yapmak için istemci kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f6cd0-207">To call the service, add the code to the client to do the following:</span></span>  
  
1.  <span data-ttu-id="f6cd0-208">Bir kanal oluşturmak `ISessionBoundFactory` hizmet.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-208">Create a channel to the `ISessionBoundFactory` service.</span></span>  
  
2.  <span data-ttu-id="f6cd0-209">Çağrılacak kanalı kullanmaya `ISessionBoundFactory` bir elde hizmet bir <xref:System.ServiceModel.EndpointAddress10> bbject.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-209">Use the channel to invoke the `ISessionBoundFactory` service an obtain an <xref:System.ServiceModel.EndpointAddress10> bbject.</span></span>  
  
3.  <span data-ttu-id="f6cd0-210">Kullanım <xref:System.ServiceModel.EndpointAddress10> bir süre sonuyla nesnesi elde etmek için bir kanal oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-210">Use the <xref:System.ServiceModel.EndpointAddress10> to create a channel to obtain a sessionful object.</span></span>  
  
4.  <span data-ttu-id="f6cd0-211">Çağrı `SetCurrentValue` ve `GetCurrentValue` aynı nesne örneğini kaldığı göstermek için yöntemleri arasında birden fazla çağrı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-211">Call the `SetCurrentValue` and `GetCurrentValue` methods to demonstrate it remains the same object instance is used across multiple calls.</span></span>  
  
```  
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
  
## <a name="see-also"></a><span data-ttu-id="f6cd0-212">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f6cd0-212">See Also</span></span>  
 [<span data-ttu-id="f6cd0-213">Temel WCF Programlama</span><span class="sxs-lookup"><span data-stu-id="f6cd0-213">Basic WCF Programming</span></span>](../../../docs/framework/wcf/basic-wcf-programming.md)  
 [<span data-ttu-id="f6cd0-214">Hizmetleri Tasarlama ve Uygulama</span><span class="sxs-lookup"><span data-stu-id="f6cd0-214">Designing and Implementing Services</span></span>](../../../docs/framework/wcf/designing-and-implementing-services.md)  
 [<span data-ttu-id="f6cd0-215">İstemci Derleme</span><span class="sxs-lookup"><span data-stu-id="f6cd0-215">Building Clients</span></span>](../../../docs/framework/wcf/building-clients.md)  
 [<span data-ttu-id="f6cd0-216">Çift Yönlü Hizmetler</span><span class="sxs-lookup"><span data-stu-id="f6cd0-216">Duplex Services</span></span>](../../../docs/framework/wcf/feature-details/duplex-services.md)
