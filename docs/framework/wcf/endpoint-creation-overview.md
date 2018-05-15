---
title: Uç Noktası Oluşturma Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- endpoints [WCF], overview
ms.assetid: f4dce0fb-6f54-47e6-8054-86d7f574b91c
ms.openlocfilehash: 46ca6294d68537e86a319b55d8c11e3ae0084738
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
---
# <a name="endpoint-creation-overview"></a><span data-ttu-id="37893-102">Uç Noktası Oluşturma Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="37893-102">Endpoint Creation Overview</span></span>
<span data-ttu-id="37893-103">Tüm Windows Communication Foundation (WCF) hizmetiyle aracılığıyla iletişimin *uç noktaları* hizmetinin.</span><span class="sxs-lookup"><span data-stu-id="37893-103">All communication with a Windows Communication Foundation (WCF) service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="37893-104">Uç noktaları istemciler için bir WCF hizmeti sunan işlevlere erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="37893-104">Endpoints provide the clients access to the functionality that a WCF service offers.</span></span> <span data-ttu-id="37893-105">Bu bölümde bir uç nokta yapısını tanımlar ve bir uç nokta yapılandırması ve kodda nasıl tanımlanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="37893-105">This section describes the structure of an endpoint and outlines how to define an endpoint in configuration and in code.</span></span>  
  
## <a name="the-structure-of-an-endpoint"></a><span data-ttu-id="37893-106">Bir uç nokta yapısı</span><span class="sxs-lookup"><span data-stu-id="37893-106">The Structure of an Endpoint</span></span>  
 <span data-ttu-id="37893-107">Her uç nokta uç noktası, bir istemci uç noktasıyla nasıl iletişim kurabilir belirten bir bağlama ve kullanılabilir yöntemleri tanımlayan bir sözleşme nerede bulacağını gösterir bir adres içeriyor.</span><span class="sxs-lookup"><span data-stu-id="37893-107">Each endpoint contains an address that indicates where to find the endpoint, a binding that specifies how a client can communicate with the endpoint, and a contract that identifies the methods available.</span></span>  
  
-   <span data-ttu-id="37893-108">**Adres**.</span><span class="sxs-lookup"><span data-stu-id="37893-108">**Address**.</span></span> <span data-ttu-id="37893-109">Adresi benzersiz olarak uç nokta tanımlar ve olası tüketicileri hizmet nerede olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="37893-109">The address uniquely identifies the endpoint and tells potential consumers where the service is located.</span></span> <span data-ttu-id="37893-110">WCF nesne modeli tarafından temsil edilen <xref:System.ServiceModel.EndpointAddress> Tekdüzen Kaynak Tanımlayıcısı (URI) ve bir kimlik, bazı Web Hizmetleri Açıklama Dili (WSDL) öğeleri ve isteğe bağlı bir koleksiyonunu içeren adres özelliklerini içeren adresi üstbilgileri.</span><span class="sxs-lookup"><span data-stu-id="37893-110">It is represented in the WCF object model by the <xref:System.ServiceModel.EndpointAddress> address, which contains a Uniform Resource Identifier (URI) and address properties that include an identity, some Web Services Description Language (WSDL) elements, and a collection of optional headers.</span></span> <span data-ttu-id="37893-111">İsteğe bağlı üstbilgi tanımlamak veya uç noktasıyla etkileşim için ek ayrıntılı adresleme bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="37893-111">The optional headers provide additional detailed addressing information to identify or interact with the endpoint.</span></span> <span data-ttu-id="37893-112">Daha fazla bilgi için bkz: [bir uç noktası adresi belirtme](../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span><span class="sxs-lookup"><span data-stu-id="37893-112">For more information, see [Specifying an Endpoint Address](../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span></span>  
  
-   <span data-ttu-id="37893-113">**Bağlama**.</span><span class="sxs-lookup"><span data-stu-id="37893-113">**Binding**.</span></span> <span data-ttu-id="37893-114">Bağlama bitiş noktası ile iletişim kurmak nasıl belirtir.</span><span class="sxs-lookup"><span data-stu-id="37893-114">The binding specifies how to communicate with the endpoint.</span></span> <span data-ttu-id="37893-115">Bağlama nasıl uç nokta kullanmak için hangi Aktarım Protokolü dahil olmak üzere dünya ile (örneğin, TCP veya HTTP) hangi (örneğin, metin veya ikili) iletileri için kullanılacak kodlama iletişim kurar ve hangi güvenlik gereksinimlerini (için gerekli olduğunu belirler Örneğin, Güvenli Yuva Katmanı [SSL] veya SOAP iletisi güvenlik).</span><span class="sxs-lookup"><span data-stu-id="37893-115">The binding specifies how the endpoint communicates with the world, including which transport protocol to use (for example, TCP or HTTP), which encoding to use for the messages (for example, text or binary), and which security requirements are necessary (for example, Secure Sockets Layer [SSL] or SOAP message security).</span></span> <span data-ttu-id="37893-116">Daha fazla bilgi için bkz: [kullanarak bağlamaları yapılandırma hizmetler ve istemcileri için](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md).</span><span class="sxs-lookup"><span data-stu-id="37893-116">For more information, see [Using Bindings to Configure Services and Clients](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md).</span></span>  
  
-   <span data-ttu-id="37893-117">**Hizmet sözleşmesi**.</span><span class="sxs-lookup"><span data-stu-id="37893-117">**Service contract**.</span></span> <span data-ttu-id="37893-118">Hizmet sözleşmesi istemciye uç noktasını kullanıma sunar hangi işlevsellikler özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="37893-118">The service contract outlines what functionality the endpoint exposes to the client.</span></span> <span data-ttu-id="37893-119">Bir sözleşme istemci çağırabilirsiniz işlemleri, ileti biçimi ve giriş parametreleri veya işlem ve işleme veya istemci bekleyebilirsiniz yanıt iletisi türünü aramak için gerekli veri türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="37893-119">A contract specifies the operations that a client can call, the form of the message and the type of input parameters or data required to call the operation, and the kind of processing or response message the client can expect.</span></span> <span data-ttu-id="37893-120">Sözleşmeleri üç temel türde karşılık gelen temel ileti exchange desenlerini (MEPs): (tek yönlü), veri birimi istek/yanıt ve çift yönlü (çift yönlü).</span><span class="sxs-lookup"><span data-stu-id="37893-120">Three basic types of contracts correspond to basic message exchange patterns (MEPs): datagram (one-way), request/reply, and duplex (bidirectional).</span></span> <span data-ttu-id="37893-121">Hizmet sözleşmesi belirli veri türlerini ve ileti formatları erişilen zaman gerektirecek şekilde veri ve ileti sözleşmeleri da tercih edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="37893-121">The service contract can also employ data and message contracts to require specific data types and message formats when being accessed.</span></span> <span data-ttu-id="37893-122">Bir hizmet sözleşmesini tanımlama hakkında daha fazla bilgi için bkz: [Hizmet sözleşmeleri tasarlama](../../../docs/framework/wcf/designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="37893-122">For more information about how to define a service contract, see [Designing Service Contracts](../../../docs/framework/wcf/designing-service-contracts.md).</span></span> <span data-ttu-id="37893-123">Bir istemci da çift yönlü MEP hizmetinde iletileri almak için bir geri çağırma sözleşme adlı bir hizmet tarafından tanımlanan sözleşme uygulamak için gerekli unutmayın.</span><span class="sxs-lookup"><span data-stu-id="37893-123">Note that a client may also be required to implement a service-defined contract, called a callback contract, to receive messages from the service in a duplex MEP.</span></span> <span data-ttu-id="37893-124">Daha fazla bilgi için bkz: [çift yönlü Hizmetler](../../../docs/framework/wcf/feature-details/duplex-services.md).</span><span class="sxs-lookup"><span data-stu-id="37893-124">For more information, see [Duplex Services](../../../docs/framework/wcf/feature-details/duplex-services.md).</span></span>  
  
 <span data-ttu-id="37893-125">Bir hizmeti için uç noktaya kodu kullanarak imperatively ya da bildirimli olarak yapılandırma yoluyla belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="37893-125">The endpoint for a service can be specified either imperatively by using code or declaratively through configuration.</span></span> <span data-ttu-id="37893-126">Uç nokta yok belirtilmezse, çalışma zamanı hizmeti tarafından uygulanan her hizmet sözleşmesi için her bir taban adresi için bir varsayılan uç nokta ekleyerek varsayılan uç noktaları sağlar.</span><span class="sxs-lookup"><span data-stu-id="37893-126">If no endpoints are specified then the runtime provides default endpoints by adding one default endpoint for each base address for each service contract implemented by the service.</span></span> <span data-ttu-id="37893-127">Bağlamalar ve dağıtılmış bir hizmet için adresleri hizmet geliştirildiği sırada kullanılan olanlardan genellikle farklı olduğu için uç noktalar kodda tanımlama genellikle pratik değildir.</span><span class="sxs-lookup"><span data-stu-id="37893-127">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="37893-128">Genellikle, kod yerine Yapılandırması kullanılarak hizmet uç noktaları tanımlamak daha pratik olur.</span><span class="sxs-lookup"><span data-stu-id="37893-128">Generally, it is more practical to define service endpoints using configuration rather than code.</span></span> <span data-ttu-id="37893-129">Bağlama tutulması ve kod dışında bilgisine derlenir ve uygulamayı yeniden dağıtmak zorunda kalmadan değiştirmek için bunları sağlar.</span><span class="sxs-lookup"><span data-stu-id="37893-129">Keeping the binding and addressing information out of the code allows them to change without having to recompile and redeploy the application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="37893-130">Kimliğe bürünme gerçekleştiren bir hizmet uç noktası eklerken ya da birini kullanmanız gerekir <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> yöntemleri veya <xref:System.ServiceModel.Description.ContractDescription.GetContract%28System.Type%2CSystem.Type%29> düzgün sözleşmeyi yeni bir yükleme yöntemini <xref:System.ServiceModel.Description.ServiceDescription> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="37893-130">When adding a service endpoint that performs impersonation, you must either use one of the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> methods or the <xref:System.ServiceModel.Description.ContractDescription.GetContract%28System.Type%2CSystem.Type%29> method to properly load the contract into a new <xref:System.ServiceModel.Description.ServiceDescription> object.</span></span>  
  
## <a name="defining-endpoints-in-code"></a><span data-ttu-id="37893-131">Uç noktaları kodda tanımlama</span><span class="sxs-lookup"><span data-stu-id="37893-131">Defining Endpoints in Code</span></span>  
 <span data-ttu-id="37893-132">Aşağıdaki örnek, bir uç nokta aşağıdaki kodla belirtmek üzere verilmektedir:</span><span class="sxs-lookup"><span data-stu-id="37893-132">The following example illustrates how to specify an endpoint in code with the following:</span></span>  
  
-   <span data-ttu-id="37893-133">Tanımlamak için bir sözleşmede bir `IEcho` birisinin adını ve yankı yanıtı ile kabul hizmet türü "Merhaba \<adı >!".</span><span class="sxs-lookup"><span data-stu-id="37893-133">Define a contract for an `IEcho` type of service that accepts someone's name and echo with the response "Hello \<name>!".</span></span>  
  
-   <span data-ttu-id="37893-134">Uygulama bir `Echo` tarafından tanımlanan türdeki hizmet `IEcho` sözleşme.</span><span class="sxs-lookup"><span data-stu-id="37893-134">Implement an `Echo` service of the type defined by the `IEcho` contract.</span></span>  
  
-   <span data-ttu-id="37893-135">Bir uç nokta adresini belirtin http://localhost:8000/Echo hizmeti.</span><span class="sxs-lookup"><span data-stu-id="37893-135">Specify an endpoint address of http://localhost:8000/Echo for the service.</span></span>  
  
-   <span data-ttu-id="37893-136">Yapılandırma `Echo` kullanarak hizmet bir <xref:System.ServiceModel.WSHttpBinding> bağlama.</span><span class="sxs-lookup"><span data-stu-id="37893-136">Configure the `Echo` service using a <xref:System.ServiceModel.WSHttpBinding> binding.</span></span>  
  
```csharp  
Namespace Echo  
{  
   // Define the contract for the IEcho service   
   [ServiceContract]  
   public interface IEcho  
   {  
       [OperationContract]  
       String Hello(string name)  
   }  
  
   // Create an Echo service that implements IEcho contract  
   class Echo : IEcho  
   {  
      public string Hello(string name)  
      {  
         return "Hello" + name + "!";  
      }  
      public static void Main ()  
      {  
          //Specify the base address for Echo service.  
          Uri echoUri = new Uri("http://localhost:8000/");  
  
          //Create a ServiceHost for the Echo service.  
          ServiceHost serviceHost = new ServiceHost(typeof(Echo),echoUri);  
  
          // Use a predefined WSHttpBinding to configure the service.  
          WSHttpBinding binding = new WSHttpBinding();  
  
          // Add the endpoint for this service to the service host.  
          serviceHost.AddServiceEndpoint(  
             typeof(IEcho),   
             binding,   
             echoUri  
           );  
  
          // Open the service host to run it.  
          serviceHost.Open();  
     }  
  }  
}  
```  
  
```vb  
' Define the contract for the IEcho service  
    <ServiceContract()> _  
    Public Interface IEcho  
        <OperationContract()> _  
        Function Hello(ByVal name As String) As String  
    End Interface  
  
' Create an Echo service that implements IEcho contract  
    Public Class Echo   
        Implements IEcho  
        Public Function Hello(ByVal name As String) As String _  
 Implements ICalculator.Hello  
            Dim result As String = "Hello" + name + "!"  
            Return result  
        End Function  
  
' Specify the base address for Echo service.  
Dim echoUri As Uri = New Uri("http://localhost:8000/")  
  
' Create a ServiceHost for the Echo service.  
Dim svcHost As ServiceHost = New ServiceHost(GetType(HelloWorld), echoUri)  
  
' Use a predefined WSHttpBinding to configure the service.  
Dim binding As New WSHttpBinding()  
  
' Add the endpoint for this service to the service host.  
serviceHost.AddServiceEndpoint(GetType(IEcho), binding, echoUri)  
  
' Open the service host to run it.  
serviceHost.Open()  
```  
  
> [!NOTE]
>  <span data-ttu-id="37893-137">Hizmet ana bilgisayarı ile temel bir adres oluşturulur ve temel adres göre adresi geri kalanı bir uç nokta bir parçası olarak sonra belirtilir.</span><span class="sxs-lookup"><span data-stu-id="37893-137">The service host is created with a base address and then the rest of the address, relative to the base address, is specified as part of an endpoint.</span></span> <span data-ttu-id="37893-138">Bu adresini bölümleme daha rahat bir ana adresinde Hizmetleri tanımlanması birden çok uç nokta sağlar.</span><span class="sxs-lookup"><span data-stu-id="37893-138">This partitioning of the address allows multiple endpoints to be defined more conveniently for services at a host.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="37893-139">Özelliklerini <xref:System.ServiceModel.Description.ServiceDescription> hizmetinde uygulama subsequent için değiştirilmemelidir <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> yöntemi <xref:System.ServiceModel.ServiceHostBase>.</span><span class="sxs-lookup"><span data-stu-id="37893-139">Properties of <xref:System.ServiceModel.Description.ServiceDescription> in the service application must not be modified subsequent to the <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> method on <xref:System.ServiceModel.ServiceHostBase>.</span></span> <span data-ttu-id="37893-140">Bazı üyeler gibi <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> özelliği ve `AddServiceEndpoint` yöntemlere <xref:System.ServiceModel.ServiceHostBase> ve <xref:System.ServiceModel.ServiceHost>, o noktayı değiştirilirse bir özel durum.</span><span class="sxs-lookup"><span data-stu-id="37893-140">Some members, such as the <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> property and the `AddServiceEndpoint` methods on <xref:System.ServiceModel.ServiceHostBase> and <xref:System.ServiceModel.ServiceHost>, throw an exception if modified past that point.</span></span> <span data-ttu-id="37893-141">Başkalarının, bunları değiştirmek için izin verme, ancak sonuç tanımlanmadı.</span><span class="sxs-lookup"><span data-stu-id="37893-141">Others permit you to modify them, but the result is undefined.</span></span>  
>   
>  <span data-ttu-id="37893-142">Benzer şekilde, istemci üzerinde <xref:System.ServiceModel.Description.ServiceEndpoint> değerleri değil değiştirilmelidir çağrısından sonra <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> üzerinde <xref:System.ServiceModel.ChannelFactory>.</span><span class="sxs-lookup"><span data-stu-id="37893-142">Similarly, on the client the <xref:System.ServiceModel.Description.ServiceEndpoint> values must not be modified after the call to <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> on the <xref:System.ServiceModel.ChannelFactory>.</span></span> <span data-ttu-id="37893-143"><xref:System.ServiceModel.ChannelFactory.Credentials%2A> Özelliği bu noktayı değiştirilirse bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="37893-143">The <xref:System.ServiceModel.ChannelFactory.Credentials%2A> property throws an exception if modified past that point.</span></span> <span data-ttu-id="37893-144">Bir istemci açıklama değerleri hatasız değiştirilebilir, ancak sonuç tanımlanmadı.</span><span class="sxs-lookup"><span data-stu-id="37893-144">The other client description values can be modified without error, but the result is undefined.</span></span>  
>   
>  <span data-ttu-id="37893-145">Hizmet veya istemci için açıklama çağrılmadan önce değiştirmeniz önerilir olup olmadığını <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span><span class="sxs-lookup"><span data-stu-id="37893-145">Whether for the service or client, it is recommended that you modify the description prior to calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span></span>  
  
## <a name="defining-endpoints-in-configuration"></a><span data-ttu-id="37893-146">Uç nokta yapılandırmasında tanımlama</span><span class="sxs-lookup"><span data-stu-id="37893-146">Defining Endpoints in Configuration</span></span>  
 <span data-ttu-id="37893-147">Bir uygulama oluştururken, genellikle uygulama dağıtma Yöneticisi kararları erteleneceği istersiniz.</span><span class="sxs-lookup"><span data-stu-id="37893-147">When creating an application, you often want to defer decisions to the administrator who is deploying the application.</span></span> <span data-ttu-id="37893-148">Örneğin, olduğundan genellikle önceden (URI) adresi bir hizmet bilerek hiçbir şekilde olacaktır.</span><span class="sxs-lookup"><span data-stu-id="37893-148">For example, there is often no way of knowing in advance what a service address (a URI) will be.</span></span> <span data-ttu-id="37893-149">Sabit bir adresi kodlama yerine, bir hizmet oluşturduktan sonra bunu yapmak için yönetici izin vermek için tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="37893-149">Instead of hard-coding an address, it is preferable to allow an administrator to do so after creating a service.</span></span> <span data-ttu-id="37893-150">Bu esneklik yapılandırma aracılığıyla gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="37893-150">This flexibility is accomplished through configuration.</span></span> <span data-ttu-id="37893-151">Ayrıntılar için bkz [Hizmetleri'ni Yapılandırma](../../../docs/framework/wcf/configuring-services.md).</span><span class="sxs-lookup"><span data-stu-id="37893-151">For details, see [Configuring Services](../../../docs/framework/wcf/configuring-services.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="37893-152">Kullanım [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ile `/config:` *filename*`[,`*filename* `]` geç yapılandırma dosyaları hızla oluşturun.</span><span class="sxs-lookup"><span data-stu-id="37893-152">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) with the `/config:`*filename*`[,`*filename*`]` switch to quickly create configuration files.</span></span>  
  
## <a name="using-default-endpoints"></a><span data-ttu-id="37893-153">Varsayılan uç noktaları kullanma</span><span class="sxs-lookup"><span data-stu-id="37893-153">Using Default Endpoints</span></span>  
 <span data-ttu-id="37893-154">Uç nokta yok kod veya yapılandırma belirtilmezse, çalışma zamanı hizmeti tarafından uygulanan her hizmet sözleşmesi için her bir taban adresi için bir varsayılan uç nokta ekleyerek varsayılan uç noktaları sağlar.</span><span class="sxs-lookup"><span data-stu-id="37893-154">If no endpoints are specified in code or in configuration then the runtime provides default endpoints by adding one default endpoint for each base address for each service contract implemented by the service.</span></span> <span data-ttu-id="37893-155">Kod veya yapılandırma taban adresi belirtilebilir ve varsayılan uç noktaları eklenip <xref:System.ServiceModel.ICommunicationObject.Open> üzerinde adlı <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="37893-155">The base address can be specified in code or in configuration, and the default endpoints are added when <xref:System.ServiceModel.ICommunicationObject.Open> is called on the <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="37893-156">Bu örnek, önceki bölümde aynı örnekten olmakla birlikte uç nokta yok belirtilen olduğundan, varsayılan uç noktalar eklenir.</span><span class="sxs-lookup"><span data-stu-id="37893-156">This example is the same example from the previous section, but since no endpoints are specified, the default endpoints are added.</span></span>  
  
```csharp  
Namespace Echo  
{  
   // Define the contract for the IEcho service   
   [ServiceContract]  
   Interface IEcho  
   {  
       [OperationContract]  
       String Hello(string name)  
   }  
  
   // Create an Echo service that implements IEcho contract  
   Class Echo : IEcho  
   {  
      Public string Hello(string name)  
      {  
         return "Hello" + name + "!";  
      }  
      static void Main ()  
      {  
          //Specify the base address for Echo service.  
          Uri echoUri = new Uri("http://localhost:8000/");  
  
          //Create a ServiceHost for the Echo service.  
          ServiceHost serviceHost = new ServiceHost(typeof(Echo),echoUri);  
  
          // Open the service host to run it. Default endpoints  
          // are added when the service is opened.  
          serviceHost.Open();  
     }  
  }  
}  
```  
  
```vb  
' Define the contract for the IEcho service  
    <ServiceContract()> _  
    Public Interface IEcho  
        <OperationContract()> _  
        Function Hello(ByVal name As String) As String  
    End Interface  
  
' Create an Echo service that implements IEcho contract  
    Public Class Echo   
        Implements IEcho  
        Public Function Hello(ByVal name As String) As String _  
 Implements ICalculator.Hello  
            Dim result As String = "Hello" + name + "!"  
            Return result  
        End Function  
  
' Specify the base address for Echo service.  
Dim echoUri As Uri = New Uri("http://localhost:8000/")  
  
' Open the service host to run it. Default endpoints  
' are added when the service is opened.  
serviceHost.Open()  
```  
  
 <span data-ttu-id="37893-157">Uç noktalar açıkça verdiyse, varsayılan uç noktalar hala çağırarak eklenebilir <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints%2A> üzerinde <xref:System.ServiceModel.ServiceHost> çağırmadan önce <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span><span class="sxs-lookup"><span data-stu-id="37893-157">If endpoints are explicitly provided, the default endpoints can still be added by calling <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints%2A> on the <xref:System.ServiceModel.ServiceHost> before calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span></span> <span data-ttu-id="37893-158">Varsayılan uç noktalar hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="37893-158">For more information about default endpoints, see [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37893-159">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="37893-159">See Also</span></span>  
 [<span data-ttu-id="37893-160">Hizmet Anlaşmalarını Uygulama</span><span class="sxs-lookup"><span data-stu-id="37893-160">Implementing Service Contracts</span></span>](../../../docs/framework/wcf/implementing-service-contracts.md)
