---
title: 'Nasıl yapılır: Yönetilen Kodu DCOM’dan WCF’ye Geçirme'
description: Sunucular ve istemciler arasında dağıtılmış bileşen nesne modeli (DCOM) yönetilen kod çağrılarını Windows Communication Foundation (WCF) olarak geçirin.
ms.date: 03/30/2017
ms.assetid: 52961ffc-d1c7-4f83-832c-786444b951ba
ms.openlocfilehash: cc6ac1dd01e17bb184d1f1faca372134d6130d33
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619097"
---
# <a name="how-to-migrate-managed-code-dcom-to-wcf"></a><span data-ttu-id="4a414-103">Nasıl yapılır: Yönetilen Kodu DCOM’dan WCF’ye Geçirme</span><span class="sxs-lookup"><span data-stu-id="4a414-103">How to: Migrate Managed-Code DCOM to WCF</span></span>
<span data-ttu-id="4a414-104">Windows Communication Foundation (WCF) dağıtılmış bir ortamdaki sunucular ve istemciler arasındaki yönetilen kod çağrıları için dağıtılmış bileşen nesne modeli (DCOM) üzerinde önerilen ve güvenli seçenektir.</span><span class="sxs-lookup"><span data-stu-id="4a414-104">Windows Communication Foundation (WCF) is the recommended and secure choice over Distributed Component Object Model (DCOM) for managed code calls between servers and clients in a distributed environment.</span></span> <span data-ttu-id="4a414-105">Bu makalede, aşağıdaki senaryolar için DCOM 'dan WCF 'ye nasıl kod geçirebileceğiniz gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="4a414-105">This article shows how you to migrate code from DCOM to WCF for the following scenarios.</span></span>  
  
- <span data-ttu-id="4a414-106">Uzak hizmet, istemciye bir nesne değeri döndürür</span><span class="sxs-lookup"><span data-stu-id="4a414-106">The remote service returns an object by-value to the client</span></span>  
  
- <span data-ttu-id="4a414-107">İstemci, uzak hizmete bir nesne olarak değer gönderir</span><span class="sxs-lookup"><span data-stu-id="4a414-107">The client sends an object by-value to the remote service</span></span>  
  
- <span data-ttu-id="4a414-108">Uzak hizmet, istemciye başvuruya göre bir nesne döndürür</span><span class="sxs-lookup"><span data-stu-id="4a414-108">The remote service returns an object by-reference to the client</span></span>  
  
 <span data-ttu-id="4a414-109">Güvenlik nedenleriyle, istemciden hizmete bir nesne başvuruya göre gönderilmesi WCF 'de buna izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="4a414-109">For security reasons, sending an object by-reference from the client to the service is not allowed in WCF.</span></span> <span data-ttu-id="4a414-110">Bir çift yönlü hizmet kullanılarak, istemci ve sunucu arasında geri ve ileri bir konuşma gerektiren bir senaryo WCF 'de elde edilebilir.</span><span class="sxs-lookup"><span data-stu-id="4a414-110">A scenario that requires a conversation back and forth between client and server can be achieved in WCF using a duplex service.</span></span>  <span data-ttu-id="4a414-111">Çift yönlü hizmetler hakkında daha fazla bilgi için bkz. [çift yönlü hizmetler](../wcf/feature-details/duplex-services.md).</span><span class="sxs-lookup"><span data-stu-id="4a414-111">For more information about duplex services, see [Duplex Services](../wcf/feature-details/duplex-services.md).</span></span>  
  
 <span data-ttu-id="4a414-112">Bu hizmetler için WCF Hizmetleri ve istemcileri oluşturma hakkında daha fazla bilgi için bkz. [Temel WCF programlama](../wcf/basic-wcf-programming.md), [Hizmetleri tasarlama ve uygulama](../wcf/designing-and-implementing-services.md)ve [istemci oluşturma](../wcf/building-clients.md).</span><span class="sxs-lookup"><span data-stu-id="4a414-112">For more details about creating WCF services and clients for those services, see [Basic WCF Programming](../wcf/basic-wcf-programming.md), [Designing and Implementing Services](../wcf/designing-and-implementing-services.md), and [Building Clients](../wcf/building-clients.md).</span></span>  
  
## <a name="dcom-example-code"></a><span data-ttu-id="4a414-113">DCOM örnek kodu</span><span class="sxs-lookup"><span data-stu-id="4a414-113">DCOM example code</span></span>  
 <span data-ttu-id="4a414-114">Bu senaryolar için, WCF kullanılarak gösterilen DCOM arabirimleri aşağıdaki yapıya sahiptir:</span><span class="sxs-lookup"><span data-stu-id="4a414-114">For these scenarios, the DCOM interfaces that are illustrated using WCF have the following structure:</span></span>  
  
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
  
## <a name="the-service-returns-an-object-by-value"></a><span data-ttu-id="4a414-115">Hizmet bir nesne değere göre döndürüyor</span><span class="sxs-lookup"><span data-stu-id="4a414-115">The service returns an object by-value</span></span>  
 <span data-ttu-id="4a414-116">Bu senaryo için, bir hizmet çağrısı yaparsınız ve IT yöntemi sunucudan istemciye değer ile geçirilen bir nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="4a414-116">For this scenario, you make a call to a service and it method returns an object, which is passed by-value from the server to the client.</span></span> <span data-ttu-id="4a414-117">Bu senaryo aşağıdaki COM çağrısını temsil eder:</span><span class="sxs-lookup"><span data-stu-id="4a414-117">This scenario represents the following COM call:</span></span>  
  
```csharp  
public interface IRemoteService  
{  
    Customer GetObjectByValue();  
}  
```  
  
 <span data-ttu-id="4a414-118">Bu senaryoda istemci, uzak hizmetten bir nesnenin serisi kaldırılmış bir kopyasını alır.</span><span class="sxs-lookup"><span data-stu-id="4a414-118">In this scenario, the client receives a deserialized copy of an object from the remote service.</span></span> <span data-ttu-id="4a414-119">İstemci, hizmete geri çağrı yapmadan bu yerel kopyayla etkileşime geçebilir.</span><span class="sxs-lookup"><span data-stu-id="4a414-119">The client can interact with this local copy without calling back to the service.</span></span>  <span data-ttu-id="4a414-120">Diğer bir deyişle, istemci garanti edilir çünkü yerel kopyada Yöntemler çağrıldığında hizmetin hiçbir şekilde ilgili olmaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4a414-120">In other words, the client is guaranteed the service will not be involved in any way when methods on the local copy are called.</span></span> <span data-ttu-id="4a414-121">WCF her zaman değere göre hizmetten nesneleri döndürür, bu nedenle aşağıdaki adımlarda normal bir WCF hizmeti oluşturma açıklanır.</span><span class="sxs-lookup"><span data-stu-id="4a414-121">WCF always returns objects from the service by value, so the following steps describe creating a regular WCF service.</span></span>  
  
### <a name="step-1-define-the-wcf-service-interface"></a><span data-ttu-id="4a414-122">1. Adım: WCF hizmeti arabirimini tanımlama</span><span class="sxs-lookup"><span data-stu-id="4a414-122">Step 1: Define the WCF service interface</span></span>  
 <span data-ttu-id="4a414-123">WCF hizmeti için bir ortak arabirim tanımlayın ve [ <xref:System.ServiceModel.ServiceContractAttribute> ] özniteliğiyle işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="4a414-123">Define a public interface for the WCF service and mark it with the [<xref:System.ServiceModel.ServiceContractAttribute>] attribute.</span></span>  <span data-ttu-id="4a414-124">İstemcilere göstermek istediğiniz yöntemleri [ <xref:System.ServiceModel.OperationContractAttribute> ] özniteliğiyle işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="4a414-124">Mark the methods you want to expose to clients with the [<xref:System.ServiceModel.OperationContractAttribute>] attribute.</span></span> <span data-ttu-id="4a414-125">Aşağıdaki örnek, bir istemcinin çağırabilmesi için sunucu tarafı arabirimi ve arabirim yöntemlerini tanımlamak üzere bu özniteliklerin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4a414-125">The following example shows using these attributes to identify the server-side interface and interface methods a client can call.</span></span> <span data-ttu-id="4a414-126">Bu senaryo için kullanılan yöntem kalın olarak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="4a414-126">The method used for this scenario is shown in bold.</span></span>  
  
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
  
### <a name="step-2-define-the-data-contract"></a><span data-ttu-id="4a414-127">2. Adım: veri sözleşmesini tanımlama</span><span class="sxs-lookup"><span data-stu-id="4a414-127">Step 2: Define the data contract</span></span>  
 <span data-ttu-id="4a414-128">Daha sonra hizmet için bir veri sözleşmesi oluşturmanız gerekir, bu, hizmetin ve istemcilerinin arasında verilerin nasıl değiş tokuş olacağını anlatmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4a414-128">Next you should create a data contract for the service, which will describe how the data will be exchanged between the service and its clients.</span></span>  <span data-ttu-id="4a414-129">Veri sözleşmesinde açıklanan sınıflar [ <xref:System.Runtime.Serialization.DataContractAttribute> ] özniteliğiyle işaretlenmelidir.</span><span class="sxs-lookup"><span data-stu-id="4a414-129">Classes described in the data contract should be marked with the [<xref:System.Runtime.Serialization.DataContractAttribute>] attribute.</span></span> <span data-ttu-id="4a414-130">Hem istemci hem de sunucu için görünür olmasını istediğiniz bireysel özellikler veya alanlar [ <xref:System.Runtime.Serialization.DataMemberAttribute> ] özniteliğiyle işaretlenmelidir.</span><span class="sxs-lookup"><span data-stu-id="4a414-130">The individual properties or fields you want visible to both client and server should be marked with the [<xref:System.Runtime.Serialization.DataMemberAttribute>] attribute.</span></span> <span data-ttu-id="4a414-131">Veri sözleşmesindeki bir sınıftan türetilmiş türlerin izin verilmesini istiyorsanız, bunları [ <xref:System.Runtime.Serialization.KnownTypeAttribute> ] özniteliğiyle belirlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="4a414-131">If you want types derived from a class in the data contract to be allowed, you must identify them with the [<xref:System.Runtime.Serialization.KnownTypeAttribute>] attribute.</span></span> <span data-ttu-id="4a414-132">WCF yalnızca hizmet arabirimindeki türleri ve bilinen türler olarak tanımlanan türleri seri hale getir veya seri durumdan çıkaracaktır.</span><span class="sxs-lookup"><span data-stu-id="4a414-132">WCF will only serialize or deserialize types in the service interface and types identified as known types.</span></span> <span data-ttu-id="4a414-133">Bilinen bir tür olmayan bir türü kullanmaya çalışırsanız, bir özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="4a414-133">If you attempt to use a type that is not a known type, an exception will occur.</span></span>  
  
 <span data-ttu-id="4a414-134">Veri sözleşmeleri hakkında daha fazla bilgi için bkz. [veri sözleşmeleri](../wcf/samples/data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="4a414-134">For more information about data contracts, see [Data Contracts](../wcf/samples/data-contracts.md).</span></span>  
  
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
  
### <a name="step-3-implement-the-wcf-service"></a><span data-ttu-id="4a414-135">3. Adım: WCF hizmetini uygulama</span><span class="sxs-lookup"><span data-stu-id="4a414-135">Step 3: Implement the WCF service</span></span>  
 <span data-ttu-id="4a414-136">Ardından, önceki adımda tanımladığınız arabirimi uygulayan WCF hizmeti sınıfını uygulamalısınız.</span><span class="sxs-lookup"><span data-stu-id="4a414-136">Next, you should implement the WCF service class that implements the interface you defined in the previous step.</span></span>  
  
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
  
### <a name="step-4-configure-the-service-and-the-client"></a><span data-ttu-id="4a414-137">4. Adım: hizmeti ve istemciyi yapılandırma</span><span class="sxs-lookup"><span data-stu-id="4a414-137">Step 4: Configure the service and the client</span></span>  
 <span data-ttu-id="4a414-138">Bir WCF hizmetini çalıştırmak için belirli bir WCF bağlamasını kullanarak bu hizmet arabirimini belirli bir URL 'de kullanıma sunan bir uç nokta bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="4a414-138">To run a WCF service, you need to declare an endpoint that exposes that service interface at a specific URL using a specific WCF binding.</span></span> <span data-ttu-id="4a414-139">Bir bağlama, iletişim kuracak istemciler ve sunucu için Aktarım, kodlama ve protokol ayrıntılarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4a414-139">A binding specifies the transport, encoding and protocol details for the clients and server to communicate.</span></span> <span data-ttu-id="4a414-140">Genellikle, hizmet projesinin yapılandırma dosyasına (web.config) bağlama eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="4a414-140">You typically add bindings to the service project’s configuration file (web.config).</span></span> <span data-ttu-id="4a414-141">Aşağıda örnek hizmet için bir bağlama girişi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="4a414-141">The following shows a binding entry for the example service:</span></span>  
  
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
  
 <span data-ttu-id="4a414-142">Ardından, istemciyi, hizmet tarafından belirtilen bağlama bilgileriyle eşleşecek şekilde yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4a414-142">Next, you need to configure the client to match the binding information specified by the service.</span></span> <span data-ttu-id="4a414-143">Bunu yapmak için, istemcinin uygulama yapılandırma (app.config) dosyasına aşağıdakini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4a414-143">To do so, add the following to the client’s application configuration (app.config) file.</span></span>  
  
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
  
### <a name="step-5-run-the-service"></a><span data-ttu-id="4a414-144">5. Adım: hizmeti çalıştırma</span><span class="sxs-lookup"><span data-stu-id="4a414-144">Step 5: Run the service</span></span>  
 <span data-ttu-id="4a414-145">Son olarak, hizmet uygulamasına aşağıdaki satırları ekleyerek ve uygulamayı başlatarak bir konsol uygulamasında kendi kendine barındırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4a414-145">Finally, you can self-host it in a console application by adding the following lines to the service app, and starting the app.</span></span> <span data-ttu-id="4a414-146">Bir WCF hizmet uygulamasını [barındırma hizmetleri, barındırma hizmetleri](../wcf/hosting-services.md)hakkında daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="4a414-146">For more information about other ways to host a WCF service application, [Hosting Services](../wcf/hosting-services.md).</span></span>  
  
```csharp  
ServiceHost customerServiceHost = new ServiceHost(typeof(CustomerService));  
customerServiceHost.Open();  
```  
  
### <a name="step-6-call-the-service-from-the-client"></a><span data-ttu-id="4a414-147">6. Adım: istemciden hizmeti çağırma</span><span class="sxs-lookup"><span data-stu-id="4a414-147">Step 6: Call the service from the client</span></span>  
 <span data-ttu-id="4a414-148">Hizmeti istemciden çağırmak için, hizmet için bir kanal fabrikası oluşturmanız ve bir kanal istemeniz gerekir. Bu, doğrudan istemciden doğrudan bir yöntemi çağırmasını sağlar `GetCustomer` .</span><span class="sxs-lookup"><span data-stu-id="4a414-148">To call the service from the client, you need to create a channel factory for the service, and request a channel, which will enable you to directly call the `GetCustomer` method directly from the client.</span></span> <span data-ttu-id="4a414-149">Kanal, hizmetin arabirimini uygular ve temel alınan istek/yanıt mantığını sizin için işler.</span><span class="sxs-lookup"><span data-stu-id="4a414-149">The channel implements the service’s interface and handles the underlying request/reply logic for you.</span></span>  <span data-ttu-id="4a414-150">Bu yöntem çağrısından gelen dönüş değeri, hizmet yanıtının Serisi kaldırılan kopyasıdır.</span><span class="sxs-lookup"><span data-stu-id="4a414-150">The return value from that method call is the deserialized copy of the service response.</span></span>  
  
```csharp  
ChannelFactory<ICustomerManager> factory =
     new ChannelFactory<ICustomerManager>("customermanager");  
ICustomerManager service = factory.CreateChannel();  
Customer customer = service.GetCustomer("Mary", "Smith");  
```  
  
## <a name="the-client-sends-a-by-value-object-to-the-server"></a><span data-ttu-id="4a414-151">İstemci sunucuya bir değere göre nesnesi gönderiyor</span><span class="sxs-lookup"><span data-stu-id="4a414-151">The client sends a by-value object to the server</span></span>  
 <span data-ttu-id="4a414-152">Bu senaryoda, istemci sunucuya bir nesne gönderir ve değeri göre.</span><span class="sxs-lookup"><span data-stu-id="4a414-152">In this scenario, the client sends an object to the server, by-value.</span></span> <span data-ttu-id="4a414-153">Bu, sunucunun, serisi kaldırılan nesnenin bir kopyasını alacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="4a414-153">This means that the server will receive a deserialized copy of the object.</span></span>  <span data-ttu-id="4a414-154">Sunucu söz konusu kopyada yöntemleri çağırabilir ve istemci koduna geri çağırma olmadığı garantisini alabilir.</span><span class="sxs-lookup"><span data-stu-id="4a414-154">The server can call methods on that copy and be guaranteed there is no callback into client code.</span></span> <span data-ttu-id="4a414-155">Daha önce belirtildiği gibi, verilerin normal WCF değişimlerinin değeri şunlardır.</span><span class="sxs-lookup"><span data-stu-id="4a414-155">As mentioned previously, normal WCF exchanges of data are by-value.</span></span>  <span data-ttu-id="4a414-156">Bu, bu nesnelerden birine çağırma yöntemlerinin yalnızca yerel olarak yürütüldüğünden emin olur; istemcide kod çağırmaz.</span><span class="sxs-lookup"><span data-stu-id="4a414-156">This guarantees that calling methods on one of these objects executes locally only – it will not invoke code on the client.</span></span>  
  
 <span data-ttu-id="4a414-157">Bu senaryo aşağıdaki COM yöntemi çağrısını temsil eder:</span><span class="sxs-lookup"><span data-stu-id="4a414-157">This scenario represents the following COM method call:</span></span>  
  
```csharp  
public interface IRemoteService  
{  
    void SendObjectByValue(Customer customer);  
}  
```  
  
 <span data-ttu-id="4a414-158">Bu senaryo, ilk örnekte gösterildiği gibi aynı hizmet arabirimini ve veri sözleşmesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="4a414-158">This scenario uses the same service interface and data contract as shown in the first example.</span></span> <span data-ttu-id="4a414-159">Ayrıca, istemci ve hizmet aynı şekilde yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="4a414-159">In addition, the client and service will be configured in the same way.</span></span> <span data-ttu-id="4a414-160">Bu örnekte, nesneyi göndermek ve aynı şekilde çalıştırmak için bir kanal oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="4a414-160">In this example, a channel is created to send the object and run the same way.</span></span> <span data-ttu-id="4a414-161">Ancak, bu örnekte, bir nesneyi değere göre geçirerek hizmeti çağıran bir istemci oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="4a414-161">However, for this example, you will create a client that calls the service, passing an object by-value.</span></span> <span data-ttu-id="4a414-162">İstemcinin hizmet sözleşmesinde çağırabilecek hizmet yöntemi kalın olarak gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="4a414-162">The service method the client will call in the service contract is shown in bold:</span></span>  
  
```csharp  
[ServiceContract]  
public interface ICustomerManager  
{  
    [OperationContract]     void StoreCustomer(Customer customer);  
  
    [OperationContract]  
    Customer GetCustomer(string firstName, string lastName);  
}  
```  
  
### <a name="add-code-to-the-client-that-sends-a-by-value-object"></a><span data-ttu-id="4a414-163">İstemciye değer nesnesi gönderen istemciye kod ekleme</span><span class="sxs-lookup"><span data-stu-id="4a414-163">Add code to the client that sends a by-value object</span></span>  
 <span data-ttu-id="4a414-164">Aşağıdaki kod, istemcinin yeni bir değerli müşteri nesnesi nasıl oluşturduğunu gösterir, hizmetle iletişim kurmak için bir kanal oluşturur `ICustomerManager` ve müşteri nesnesini bu sunucuya gönderir.</span><span class="sxs-lookup"><span data-stu-id="4a414-164">The following code shows how the client creates a new by-value customer object, creates a channel to communicate with the `ICustomerManager` service, and sends the customer object to it.</span></span>  
  
 <span data-ttu-id="4a414-165">Müşteri nesnesi serileştirilir ve hizmete gönderilir; burada hizmet tarafından bu nesnenin yeni bir kopyasına kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="4a414-165">The customer object will be serialized, and sent to the service, where it is deserialized by the service into a new copy of that object.</span></span>  <span data-ttu-id="4a414-166">Bu nesne üzerindeki hizmet çağrılarının her türlü yöntemi yalnızca sunucuda yerel olarak yürütülür.</span><span class="sxs-lookup"><span data-stu-id="4a414-166">Any methods the service calls on this object will execute only locally on the server.</span></span> <span data-ttu-id="4a414-167">Bu kodun türetilmiş bir türün () gönderilmesini gösterdiğine dikkat edin `PremiumCustomer` .</span><span class="sxs-lookup"><span data-stu-id="4a414-167">It’s important to note that this code illustrates sending a derived type (`PremiumCustomer`).</span></span>  <span data-ttu-id="4a414-168">Hizmet sözleşmesi bir nesne bekler `Customer` , ancak hizmet veri sözleşmesi <xref:System.Runtime.Serialization.KnownTypeAttribute> de izin verildiğini belirtmek için [] özniteliğini kullanır `PremiumCustomer` .</span><span class="sxs-lookup"><span data-stu-id="4a414-168">The service contract expects a `Customer` object, but the service data contract uses the [<xref:System.Runtime.Serialization.KnownTypeAttribute>] attribute to indicate that `PremiumCustomer` is also allowed.</span></span>  <span data-ttu-id="4a414-169">WCF, bu hizmet arabirimi aracılığıyla başka herhangi bir türü seri hale getirmeye veya seri durumdan çıkarmasına çalışır.</span><span class="sxs-lookup"><span data-stu-id="4a414-169">WCF will fail attempts to serialize or deserialize any other type via this service interface.</span></span>  
  
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
  
## <a name="the-service-returns-an-object-by-reference"></a><span data-ttu-id="4a414-170">Hizmet, başvuruya göre bir nesne döndürüyor</span><span class="sxs-lookup"><span data-stu-id="4a414-170">The service returns an object by reference</span></span>  
 <span data-ttu-id="4a414-171">Bu senaryo için, istemci uygulaması uzak hizmete bir çağrı yapar ve yöntemi hizmetten istemciye başvuru ile geçirilen bir nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="4a414-171">For this scenario, the client app makes a call to the remote service and the method returns an object, which is passed by reference from the service to the client.</span></span>  
  
 <span data-ttu-id="4a414-172">Daha önce belirtildiği gibi, WCF Hizmetleri nesneyi her zaman değere göre döndürür.</span><span class="sxs-lookup"><span data-stu-id="4a414-172">As mentioned previously, WCF services always return object by value.</span></span>  <span data-ttu-id="4a414-173">Ancak, sınıfını kullanarak benzer bir sonuç elde edebilirsiniz <xref:System.ServiceModel.EndpointAddress10> .</span><span class="sxs-lookup"><span data-stu-id="4a414-173">However, you can achieve a similar result by using the <xref:System.ServiceModel.EndpointAddress10> class.</span></span>  <span data-ttu-id="4a414-174">, <xref:System.ServiceModel.EndpointAddress10> İstemci tarafından sunucuda bir sessionby başvuruya göre nesne elde etmek için kullanılabilecek bir seri hale getirilebilir değer nesnesi.</span><span class="sxs-lookup"><span data-stu-id="4a414-174">The <xref:System.ServiceModel.EndpointAddress10> is a serializable by-value object that can be used by the client to obtain a sessionful by-reference object on the server.</span></span>  
  
 <span data-ttu-id="4a414-175">Bu senaryoda gösterilen WCF 'deki başvuruya göre nesnesinin davranışı, DCOM 'dan farklıdır.</span><span class="sxs-lookup"><span data-stu-id="4a414-175">The behavior of the by-reference object in WCF shown in this scenario is different than DCOM.</span></span>  <span data-ttu-id="4a414-176">DCOM 'da, sunucu istemciye doğrudan başvuruya göre bir nesne döndürebilir ve istemci, sunucuda yürütülen bu nesnenin yöntemlerini çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="4a414-176">In DCOM, the server can return a by-reference object to the client directly, and the client can call that object’s methods, which execute on the server.</span></span>  <span data-ttu-id="4a414-177">Ancak, WCF 'de döndürülen nesne her zaman değeri ile belirlenir.</span><span class="sxs-lookup"><span data-stu-id="4a414-177">In WCF, however, the object returned is always by-value.</span></span>  <span data-ttu-id="4a414-178">İstemci, tarafından temsil edilen <xref:System.ServiceModel.EndpointAddress10> ve kendi sessionby başvuru nesnesini oluşturmak için onu kullanarak bu nesne tarafından temsil etmelidir.</span><span class="sxs-lookup"><span data-stu-id="4a414-178">The client must take that by-value object, represented by <xref:System.ServiceModel.EndpointAddress10> and use it to create its own sessionful by-reference object.</span></span>  <span data-ttu-id="4a414-179">İstemci yöntemi, sunucuda yürütülen oturumsuz nesneye çağrı yapılır. Diğer bir deyişle, WCF 'deki bu başvuruya göre bu nesne, sessionmek üzere yapılandırılmış normal bir WCF hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="4a414-179">The client method calls on the sessionful object execute on the server.In other words, this by-reference object in WCF is a normal WCF service that is configured to be sessionful.</span></span>  
  
 <span data-ttu-id="4a414-180">WCF 'de oturum, iki uç nokta arasında gönderilen birden fazla iletiyi eş bir şekilde ilişkilendirme yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="4a414-180">In WCF, a session is a way of correlating multiple messages sent between two endpoints.</span></span>  <span data-ttu-id="4a414-181">Bu, bir istemci bu hizmete bir bağlantı edinirse, istemci ile sunucu arasında bir oturum kurulacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="4a414-181">This means that once a client obtains a connection to this service, a session will be established between the client and the server.</span></span>  <span data-ttu-id="4a414-182">İstemci, bu tek oturumdaki tüm etkileşimleri için sunucu tarafı nesnesinin tek bir benzersiz örneğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="4a414-182">The client will use a single unique instance of the server-side object for all its interactions within this single session.</span></span> <span data-ttu-id="4a414-183">Oturumsuz WCF sözleşmeleri, bağlantıya dayalı ağ isteği/yanıt desenlerine benzer.</span><span class="sxs-lookup"><span data-stu-id="4a414-183">Sessionful WCF contracts are similar to connection-oriented network request/response patterns.</span></span>  
  
 <span data-ttu-id="4a414-184">Bu senaryo, aşağıdaki DCOM yöntemiyle temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="4a414-184">This scenario is represented by the following DCOM method.</span></span>  
  
```csharp  
public interface IRemoteService  
{  
    IRemoteObject GetObjectByReference();  
}  
```  
  
### <a name="step-1-define-the-sessionful-wcf-service-interface-and-implementation"></a><span data-ttu-id="4a414-185">1. Adım: oturumsuz WCF hizmeti arabirimini ve uygulamasını tanımlama</span><span class="sxs-lookup"><span data-stu-id="4a414-185">Step 1: Define the Sessionful WCF service interface and implementation</span></span>  
 <span data-ttu-id="4a414-186">İlk olarak, sessionobject nesnesini içeren bir WCF hizmeti arabirimi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="4a414-186">First, define a WCF service interface that contains the sessionful object.</span></span>  
  
 <span data-ttu-id="4a414-187">Bu kodda, sessionobject nesnesi `ServiceContract` onu normal BIR WCF hizmeti arabirimi olarak tanımlayan özniteliğiyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="4a414-187">In this code, the sessionful object is marked with the `ServiceContract` attribute, which identifies it as a regular WCF service interface.</span></span>  <span data-ttu-id="4a414-188">Buna ek olarak, <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> özelliği, bir sessionservice olacağını belirtecek şekilde ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="4a414-188">In addition, the <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> property is set to indicate it will be a sessionful service.</span></span>  
  
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
  
 <span data-ttu-id="4a414-189">Aşağıdaki kod, hizmet uygulamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4a414-189">The following code shows the service implementation.</span></span>  
  
 <span data-ttu-id="4a414-190">Hizmet, [ServiceBehavior] özniteliğiyle işaretlenir ve InstanceContextMode özelliği, her oturum için bu türün benzersiz bir örneğinin oluşturulması gerektiğini belirtmek için InstanceContextMode. PerSessions olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="4a414-190">The service is marked with the [ServiceBehavior] attribute, and its InstanceContextMode property set to InstanceContextMode.PerSessions to indicate that a unique instance of this type should be created for each session.</span></span>  
  
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
  
### <a name="step-2-define-the-wcf-factory-service-for-the-sessionful-object"></a><span data-ttu-id="4a414-191">2. Adım: oturumsuz nesne için WCF fabrikası hizmetini tanımlama</span><span class="sxs-lookup"><span data-stu-id="4a414-191">Step 2: Define the WCF factory service for the sessionful object</span></span>  
 <span data-ttu-id="4a414-192">Oturumsuz nesneyi oluşturan hizmetin tanımlanması ve uygulanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4a414-192">The service that creates the sessionful object must be defined and implemented.</span></span> <span data-ttu-id="4a414-193">Aşağıdaki kod bunun nasıl yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4a414-193">The following code shows how to do this.</span></span> <span data-ttu-id="4a414-194">Bu kod, bir nesne döndüren başka bir WCF hizmeti oluşturur <xref:System.ServiceModel.EndpointAddress10> .</span><span class="sxs-lookup"><span data-stu-id="4a414-194">This code creates another WCF service that returns an <xref:System.ServiceModel.EndpointAddress10> object.</span></span>  <span data-ttu-id="4a414-195">Bu, oturum tam nesnesini oluşturmak için kullanabileceği bir uç noktanın seri hale getirilebilir bir biçimidir.</span><span class="sxs-lookup"><span data-stu-id="4a414-195">This is a serializable form of an endpoint the can use to create the session-full object.</span></span>  
  
```csharp  
[ServiceContract]  
    public interface ISessionBoundFactory  
    {  
        [OperationContract]  
        EndpointAddress10 GetInstanceAddress();  
    }  
```  
  
 <span data-ttu-id="4a414-196">Bu hizmetin uygulanması aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="4a414-196">The following is the implementation of this service.</span></span> <span data-ttu-id="4a414-197">Bu uygulama, oturumsuz nesneler oluşturmak için tek bir kanal fabrikası sağlar.</span><span class="sxs-lookup"><span data-stu-id="4a414-197">This implementation maintains a singleton channel factory to create sessionful objects.</span></span>  <span data-ttu-id="4a414-198">`GetInstanceAddress`Çağrıldığında, bir kanal oluşturur ve <xref:System.ServiceModel.EndpointAddress10> bu kanalla ilişkili uzak adrese işaret eden bir nesne oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4a414-198">When `GetInstanceAddress` is called, it creates a channel and creates an <xref:System.ServiceModel.EndpointAddress10> object that points to the remote address associated with this channel.</span></span>   <span data-ttu-id="4a414-199"><xref:System.ServiceModel.EndpointAddress10>istemciye değere göre döndürülebilecek bir veri türüdür.</span><span class="sxs-lookup"><span data-stu-id="4a414-199"><xref:System.ServiceModel.EndpointAddress10> is a data type that can be returned to the client by-value.</span></span>
  
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
  
### <a name="step-3-configure-and-start-the-wcf-services"></a><span data-ttu-id="4a414-200">3. Adım: WCF hizmetlerini yapılandırma ve başlatma</span><span class="sxs-lookup"><span data-stu-id="4a414-200">Step 3: Configure and start the WCF services</span></span>  
 <span data-ttu-id="4a414-201">Bu hizmetleri barındırmak için, sunucunun yapılandırma dosyasına (web.config) aşağıdaki eklemeleri yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4a414-201">To host these services, you will need to make the following additions to the server’s configuration file (web.config).</span></span>  
  
1. <span data-ttu-id="4a414-202">`<client>`Oturumsuz nesnenin bitiş noktasını açıklayan bir bölüm ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4a414-202">Add a `<client>` section that describes the endpoint for the sessionful object.</span></span>  <span data-ttu-id="4a414-203">Bu senaryoda, sunucu istemci olarak da çalışır ve bunu etkinleştirmek üzere yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4a414-203">In this scenario, the server also acts as a client and must be configured to enable this.</span></span>  
  
2. <span data-ttu-id="4a414-204">`<services>`Bölümünde, fabrika ve oturumsuz nesne için hizmet uç noktalarını bildirin.</span><span class="sxs-lookup"><span data-stu-id="4a414-204">In the `<services>` section, declare service endpoints for the factory and sessionful object.</span></span>  <span data-ttu-id="4a414-205">Bu, istemcinin hizmet uç noktaları ile iletişim kurmasını sağlar, alın <xref:System.ServiceModel.EndpointAddress10> ve Oturumsuz kanalı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4a414-205">This enables the client to communicate with the service endpoints, acquire the <xref:System.ServiceModel.EndpointAddress10> and create the sessionful channel.</span></span>  
  
 <span data-ttu-id="4a414-206">Aşağıdaki ayarlara sahip örnek bir yapılandırma dosyası aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="4a414-206">The following is an example configuration file with these settings:</span></span>  
  
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
  
 <span data-ttu-id="4a414-207">Bir konsol uygulamasına, hizmeti kendinden barındırmak ve uygulamayı başlatmak için aşağıdaki satırları ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4a414-207">Add the following lines to a console application, to self-host the service, and start the app.</span></span>  
  
```csharp  
ServiceHost factoryHost = new ServiceHost(typeof(SessionBoundFactory));  
factoryHost.Open();  
  
ServiceHost sessionBoundServiceHost = new ServiceHost(  
typeof(MySessionBoundObject));  
sessionBoundServiceHost.Open();  
```  
  
### <a name="step-4-configure-the-client-and-call-the-service"></a><span data-ttu-id="4a414-208">4. Adım: istemciyi yapılandırma ve hizmeti çağırma</span><span class="sxs-lookup"><span data-stu-id="4a414-208">Step 4: Configure the client and call the service</span></span>  
 <span data-ttu-id="4a414-209">İstemcisini, projenin uygulama yapılandırma dosyasında (app.config) aşağıdaki girişleri yaparak WCF hizmetleriyle iletişim kuracak şekilde yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="4a414-209">Configure the client to communicate with the WCF services by making the following entries in the project’s application configuration file (app.config).</span></span>  
  
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
  
 <span data-ttu-id="4a414-210">Hizmeti çağırmak için, aşağıdakileri yapmak üzere istemciye kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="4a414-210">To call the service, add the code to the client to do the following:</span></span>  
  
1. <span data-ttu-id="4a414-211">Hizmete bir kanal oluşturun `ISessionBoundFactory` .</span><span class="sxs-lookup"><span data-stu-id="4a414-211">Create a channel to the `ISessionBoundFactory` service.</span></span>  
  
2. <span data-ttu-id="4a414-212">Bir nesne elde eden hizmeti çağırmak için kanalı kullanın `ISessionBoundFactory` <xref:System.ServiceModel.EndpointAddress10> .</span><span class="sxs-lookup"><span data-stu-id="4a414-212">Use the channel to invoke the `ISessionBoundFactory` service an obtain an <xref:System.ServiceModel.EndpointAddress10> object.</span></span>  
  
3. <span data-ttu-id="4a414-213"><xref:System.ServiceModel.EndpointAddress10>Oturumsuz bir nesne almak için bir kanal oluşturmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="4a414-213">Use the <xref:System.ServiceModel.EndpointAddress10> to create a channel to obtain a sessionful object.</span></span>  
  
4. <span data-ttu-id="4a414-214">`SetCurrentValue`Ve yöntemlerini çağırarak, `GetCurrentValue` birden çok çağrıda aynı nesne örneğinin kullanıldığını göstermek için ve yöntemlerini çağırın.</span><span class="sxs-lookup"><span data-stu-id="4a414-214">Call the `SetCurrentValue` and `GetCurrentValue` methods to demonstrate it remains the same object instance is used across multiple calls.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4a414-215">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4a414-215">See also</span></span>

- [<span data-ttu-id="4a414-216">Temel WCF Programlama</span><span class="sxs-lookup"><span data-stu-id="4a414-216">Basic WCF Programming</span></span>](../wcf/basic-wcf-programming.md)
- [<span data-ttu-id="4a414-217">Hizmetleri Tasarlama ve Uygulama</span><span class="sxs-lookup"><span data-stu-id="4a414-217">Designing and Implementing Services</span></span>](../wcf/designing-and-implementing-services.md)
- [<span data-ttu-id="4a414-218">İstemci Derleme</span><span class="sxs-lookup"><span data-stu-id="4a414-218">Building Clients</span></span>](../wcf/building-clients.md)
- [<span data-ttu-id="4a414-219">Çift Yönlü Hizmetler</span><span class="sxs-lookup"><span data-stu-id="4a414-219">Duplex Services</span></span>](../wcf/feature-details/duplex-services.md)
