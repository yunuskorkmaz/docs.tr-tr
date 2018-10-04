---
title: Uç Noktası Oluşturma Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- endpoints [WCF], overview
ms.assetid: f4dce0fb-6f54-47e6-8054-86d7f574b91c
ms.openlocfilehash: b72c3959b2a42c6a5abc8ef31975d5bdb9ce220e
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48781615"
---
# <a name="endpoint-creation-overview"></a><span data-ttu-id="072be-102">Uç Noktası Oluşturma Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="072be-102">Endpoint Creation Overview</span></span>
<span data-ttu-id="072be-103">Bir Windows Communication Foundation (WCF) hizmetiyle kurulan tüm iletişimlerde üzerinden gerçekleşir *uç noktaları* hizmeti.</span><span class="sxs-lookup"><span data-stu-id="072be-103">All communication with a Windows Communication Foundation (WCF) service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="072be-104">Uç noktaları, istemcilerin bir WCF hizmeti sunan işlevine erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="072be-104">Endpoints provide the clients access to the functionality that a WCF service offers.</span></span> <span data-ttu-id="072be-105">Bu bölümde, bir uç nokta yapısını açıklar ve bir uç nokta yapılandırması ve kodda nasıl tanımlanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="072be-105">This section describes the structure of an endpoint and outlines how to define an endpoint in configuration and in code.</span></span>  
  
## <a name="the-structure-of-an-endpoint"></a><span data-ttu-id="072be-106">Bir uç nokta yapısı</span><span class="sxs-lookup"><span data-stu-id="072be-106">The Structure of an Endpoint</span></span>  
 <span data-ttu-id="072be-107">Her uç nokta uç noktası, istemci uç noktasıyla nasıl iletişim kurabilir belirten bir bağlama ve uygun olan yöntemler tanımlayan bir sözleşme nerede bulacağını gösteren bir adres içeriyor.</span><span class="sxs-lookup"><span data-stu-id="072be-107">Each endpoint contains an address that indicates where to find the endpoint, a binding that specifies how a client can communicate with the endpoint, and a contract that identifies the methods available.</span></span>  
  
-   <span data-ttu-id="072be-108">**Adres**.</span><span class="sxs-lookup"><span data-stu-id="072be-108">**Address**.</span></span> <span data-ttu-id="072be-109">Adres benzersiz şekilde uç noktayı tanımlar ve olası tüketiciler hizmet nerede olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="072be-109">The address uniquely identifies the endpoint and tells potential consumers where the service is located.</span></span> <span data-ttu-id="072be-110">WCF nesne modeli tarafından temsil edilir <xref:System.ServiceModel.EndpointAddress> Tekdüzen Kaynak Tanımlayıcısı (URI) ve bir kimlik, bazı Web Hizmetleri Açıklama Dili (WSDL) öğeleri ve isteğe bağlı bir koleksiyonunu içeren adres özelliklerini içeren adresi üstbilgileri.</span><span class="sxs-lookup"><span data-stu-id="072be-110">It is represented in the WCF object model by the <xref:System.ServiceModel.EndpointAddress> address, which contains a Uniform Resource Identifier (URI) and address properties that include an identity, some Web Services Description Language (WSDL) elements, and a collection of optional headers.</span></span> <span data-ttu-id="072be-111">İsteğe bağlı üst bilgileri tanımlamak veya uç nokta ile etkileşime geçmek için ek ayrıntılı adresleme bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="072be-111">The optional headers provide additional detailed addressing information to identify or interact with the endpoint.</span></span> <span data-ttu-id="072be-112">Daha fazla bilgi için [bir uç nokta adresi belirtme](../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span><span class="sxs-lookup"><span data-stu-id="072be-112">For more information, see [Specifying an Endpoint Address](../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span></span>  
  
-   <span data-ttu-id="072be-113">**Bağlama**.</span><span class="sxs-lookup"><span data-stu-id="072be-113">**Binding**.</span></span> <span data-ttu-id="072be-114">Bağlama uç noktasıyla iletişim nasıl belirtir.</span><span class="sxs-lookup"><span data-stu-id="072be-114">The binding specifies how to communicate with the endpoint.</span></span> <span data-ttu-id="072be-115">Bağlama nasıl uç nokta kullanmak için hangi Aktarım Protokolü dahil olmak üzere dünya ile (örneğin, TCP veya HTTP) hangi (örneğin, metin veya ikili) iletileri için kullanılacak kodlama iletişim kurar ve hangi güvenlik gereksinimleri (gereken belirtir. Örneğin, Güvenli Yuva Katmanı [SSL] veya SOAP ileti güvenliği).</span><span class="sxs-lookup"><span data-stu-id="072be-115">The binding specifies how the endpoint communicates with the world, including which transport protocol to use (for example, TCP or HTTP), which encoding to use for the messages (for example, text or binary), and which security requirements are necessary (for example, Secure Sockets Layer [SSL] or SOAP message security).</span></span> <span data-ttu-id="072be-116">Daha fazla bilgi için [hizmetlerini yapılandırın ve istemciler için bağlamaları kullanma](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md).</span><span class="sxs-lookup"><span data-stu-id="072be-116">For more information, see [Using Bindings to Configure Services and Clients](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md).</span></span>  
  
-   <span data-ttu-id="072be-117">**Hizmet sözleşmesini**.</span><span class="sxs-lookup"><span data-stu-id="072be-117">**Service contract**.</span></span> <span data-ttu-id="072be-118">Hizmet sözleşmesi istemciye uç noktasını kullanıma sunar işlevler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="072be-118">The service contract outlines what functionality the endpoint exposes to the client.</span></span> <span data-ttu-id="072be-119">Bir anlaşma, bir istemci çağırabilirsiniz işlemleri, ileti biçimi ve giriş parametreleri veya işlem ve işleme veya istemci bekleyebileceğiniz yanıt iletisi türü çağırmak için gereken veri türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="072be-119">A contract specifies the operations that a client can call, the form of the message and the type of input parameters or data required to call the operation, and the kind of processing or response message the client can expect.</span></span> <span data-ttu-id="072be-120">Sözleşmeler üç temel türde karşılık gelen temel ileti exchange desenlerini (MEPs): veri birimi (tek yönlü), istek/yanıt ve çift yönlü (çift yönlü).</span><span class="sxs-lookup"><span data-stu-id="072be-120">Three basic types of contracts correspond to basic message exchange patterns (MEPs): datagram (one-way), request/reply, and duplex (bidirectional).</span></span> <span data-ttu-id="072be-121">Hizmet sözleşmesi, erişilen, belirli veri türleri ve ileti formatları gerektiren veri ve ileti sözleşmeleri de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="072be-121">The service contract can also employ data and message contracts to require specific data types and message formats when being accessed.</span></span> <span data-ttu-id="072be-122">Bir hizmet sözleşmesini tanımlama hakkında daha fazla bilgi için bkz. [Hizmet sözleşmeleri tasarlama](../../../docs/framework/wcf/designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="072be-122">For more information about how to define a service contract, see [Designing Service Contracts](../../../docs/framework/wcf/designing-service-contracts.md).</span></span> <span data-ttu-id="072be-123">Bir istemci da çift yönlü MEP hizmette iletileri alacak şekilde geri çağırma anlaşması adlı bir hizmet tarafından tanımlanan sözleşme uygulamak için gerekli unutmayın.</span><span class="sxs-lookup"><span data-stu-id="072be-123">Note that a client may also be required to implement a service-defined contract, called a callback contract, to receive messages from the service in a duplex MEP.</span></span> <span data-ttu-id="072be-124">Daha fazla bilgi için [çift yönlü Hizmetler](../../../docs/framework/wcf/feature-details/duplex-services.md).</span><span class="sxs-lookup"><span data-stu-id="072be-124">For more information, see [Duplex Services](../../../docs/framework/wcf/feature-details/duplex-services.md).</span></span>  
  
 <span data-ttu-id="072be-125">Kesin kod kullanarak veya bildirimli olarak yapılandırma yoluyla bir hizmet için uç nokta belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="072be-125">The endpoint for a service can be specified either imperatively by using code or declaratively through configuration.</span></span> <span data-ttu-id="072be-126">Uç nokta belirtilmezse çalışma zamanı hizmeti tarafından uygulanan her bir hizmet sözleşmesi için her bir temel adres için bir varsayılan uç nokta ekleyerek varsayılan uç noktaları sağlar.</span><span class="sxs-lookup"><span data-stu-id="072be-126">If no endpoints are specified then the runtime provides default endpoints by adding one default endpoint for each base address for each service contract implemented by the service.</span></span> <span data-ttu-id="072be-127">Bağlamalarında ve adreslerinde dağıtılan bir hizmette hizmet geliştirilen kullandığı olanlardan genellikle farklı olduğundan uç noktaları kodda tanımlama genellikle pratik değildir.</span><span class="sxs-lookup"><span data-stu-id="072be-127">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="072be-128">Genel olarak, kod yerine yapılandırma kullanarak hizmet uç noktaları tanımlamak daha yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="072be-128">Generally, it is more practical to define service endpoints using configuration rather than code.</span></span> <span data-ttu-id="072be-129">Bağlama tutulması ve adresleme bilgilerini kodunun dışında yeniden derleyin ve uygulamayı yeniden dağıtmak zorunda kalmadan değiştirmek sağlar.</span><span class="sxs-lookup"><span data-stu-id="072be-129">Keeping the binding and addressing information out of the code allows them to change without having to recompile and redeploy the application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="072be-130">Kimliğe bürünme gerçekleştiren bir hizmet uç noktası eklerken ya da birini kullanmalısınız <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> yöntemleri veya <xref:System.ServiceModel.Description.ContractDescription.GetContract%28System.Type%2CSystem.Type%29> sözleşme düzgün bir şekilde yeni bir yükleme yöntemini <xref:System.ServiceModel.Description.ServiceDescription> nesne.</span><span class="sxs-lookup"><span data-stu-id="072be-130">When adding a service endpoint that performs impersonation, you must either use one of the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> methods or the <xref:System.ServiceModel.Description.ContractDescription.GetContract%28System.Type%2CSystem.Type%29> method to properly load the contract into a new <xref:System.ServiceModel.Description.ServiceDescription> object.</span></span>  
  
## <a name="defining-endpoints-in-code"></a><span data-ttu-id="072be-131">Uç noktaları kodda tanımlama</span><span class="sxs-lookup"><span data-stu-id="072be-131">Defining Endpoints in Code</span></span>  
 <span data-ttu-id="072be-132">Aşağıdaki örnek, aşağıdaki kodda bir uç nokta belirtmek verilmektedir:</span><span class="sxs-lookup"><span data-stu-id="072be-132">The following example illustrates how to specify an endpoint in code with the following:</span></span>  
  
-   <span data-ttu-id="072be-133">Sözleşme tanımlamasına bir `IEcho` birisinin adını ve yankı yanıtı ile kabul eden hizmet türü "Hello \<name >!".</span><span class="sxs-lookup"><span data-stu-id="072be-133">Define a contract for an `IEcho` type of service that accepts someone's name and echo with the response "Hello \<name>!".</span></span>  
  
-   <span data-ttu-id="072be-134">Uygulama bir `Echo` hizmet tarafından tanımlanan tür `IEcho` sözleşme.</span><span class="sxs-lookup"><span data-stu-id="072be-134">Implement an `Echo` service of the type defined by the `IEcho` contract.</span></span>  
  
-   <span data-ttu-id="072be-135">Bir uç nokta adresini belirtin `http://localhost:8000/Echo` hizmeti.</span><span class="sxs-lookup"><span data-stu-id="072be-135">Specify an endpoint address of `http://localhost:8000/Echo` for the service.</span></span>  
  
-   <span data-ttu-id="072be-136">Yapılandırma `Echo` kullanarak hizmet bir <xref:System.ServiceModel.WSHttpBinding> bağlama.</span><span class="sxs-lookup"><span data-stu-id="072be-136">Configure the `Echo` service using a <xref:System.ServiceModel.WSHttpBinding> binding.</span></span>  
  
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
>  <span data-ttu-id="072be-137">Hizmet ana bilgisayarı, bir taban adresi ile oluşturulur ve ardından temel adresini göreli adres geri kalanı bir uç noktasının bir parçası belirtilir.</span><span class="sxs-lookup"><span data-stu-id="072be-137">The service host is created with a base address and then the rest of the address, relative to the base address, is specified as part of an endpoint.</span></span> <span data-ttu-id="072be-138">Bu bölümleme adresini daha rahat bir ana bilgisayar Hizmetleri için tanımlanmış birden çok uç noktaları sağlar.</span><span class="sxs-lookup"><span data-stu-id="072be-138">This partitioning of the address allows multiple endpoints to be defined more conveniently for services at a host.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="072be-139">Özelliklerini <xref:System.ServiceModel.Description.ServiceDescription> hizmetinde uygulama için subsequent değiştirilmemelidir <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> metodunda <xref:System.ServiceModel.ServiceHostBase>.</span><span class="sxs-lookup"><span data-stu-id="072be-139">Properties of <xref:System.ServiceModel.Description.ServiceDescription> in the service application must not be modified subsequent to the <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> method on <xref:System.ServiceModel.ServiceHostBase>.</span></span> <span data-ttu-id="072be-140">Bazı üyeler gibi <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> özelliği ve `AddServiceEndpoint` yöntemlerde <xref:System.ServiceModel.ServiceHostBase> ve <xref:System.ServiceModel.ServiceHost>, bu noktanın ilerisine değiştirdiyseniz bir özel durum.</span><span class="sxs-lookup"><span data-stu-id="072be-140">Some members, such as the <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> property and the `AddServiceEndpoint` methods on <xref:System.ServiceModel.ServiceHostBase> and <xref:System.ServiceModel.ServiceHost>, throw an exception if modified past that point.</span></span> <span data-ttu-id="072be-141">Diğerleri, bunları değiştirmek için izin verir, ancak sonuç tanımsızdır.</span><span class="sxs-lookup"><span data-stu-id="072be-141">Others permit you to modify them, but the result is undefined.</span></span>  
>   
>  <span data-ttu-id="072be-142">Benzer şekilde, istemci üzerinde <xref:System.ServiceModel.Description.ServiceEndpoint> değerlerin değil değiştirilmelidir çağrısından sonra <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> üzerinde <xref:System.ServiceModel.ChannelFactory>.</span><span class="sxs-lookup"><span data-stu-id="072be-142">Similarly, on the client the <xref:System.ServiceModel.Description.ServiceEndpoint> values must not be modified after the call to <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> on the <xref:System.ServiceModel.ChannelFactory>.</span></span> <span data-ttu-id="072be-143"><xref:System.ServiceModel.ChannelFactory.Credentials%2A> Özelliği bu noktanın ilerisine değiştirdiyseniz bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="072be-143">The <xref:System.ServiceModel.ChannelFactory.Credentials%2A> property throws an exception if modified past that point.</span></span> <span data-ttu-id="072be-144">Diğer istemci açıklama değerler hatasız değiştirilebilir, ancak sonuç tanımsızdır.</span><span class="sxs-lookup"><span data-stu-id="072be-144">The other client description values can be modified without error, but the result is undefined.</span></span>  
>   
>  <span data-ttu-id="072be-145">Hizmet veya istemci için açıklama çağrılmadan önce değiştirmeniz önerilir olmadığını <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span><span class="sxs-lookup"><span data-stu-id="072be-145">Whether for the service or client, it is recommended that you modify the description prior to calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span></span>  
  
## <a name="defining-endpoints-in-configuration"></a><span data-ttu-id="072be-146">Uç noktalar yapılandırmada tanımlama</span><span class="sxs-lookup"><span data-stu-id="072be-146">Defining Endpoints in Configuration</span></span>  
 <span data-ttu-id="072be-147">Bir uygulama oluştururken, genellikle uygulama dağıtma Yöneticisi kararları erteleme istersiniz.</span><span class="sxs-lookup"><span data-stu-id="072be-147">When creating an application, you often want to defer decisions to the administrator who is deploying the application.</span></span> <span data-ttu-id="072be-148">Örneğin, yoktur genellikle önceden (URI) yönelik bir hizmet olduğunu bilmesinin imkanı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="072be-148">For example, there is often no way of knowing in advance what a service address (a URI) will be.</span></span> <span data-ttu-id="072be-149">Sabit bir adresi kodlama yerine, bir hizmet oluşturduktan sonra bunu yapmak bir yönetici izin vermek için tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="072be-149">Instead of hard-coding an address, it is preferable to allow an administrator to do so after creating a service.</span></span> <span data-ttu-id="072be-150">Bu esnekliğin yapılandırma aracılığıyla gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="072be-150">This flexibility is accomplished through configuration.</span></span> <span data-ttu-id="072be-151">Ayrıntılar için bkz [Hizmetleri'ni Yapılandırma](../../../docs/framework/wcf/configuring-services.md).</span><span class="sxs-lookup"><span data-stu-id="072be-151">For details, see [Configuring Services](../../../docs/framework/wcf/configuring-services.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="072be-152">Kullanım [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ile `/config:` *filename*`[,`*filename* `]` geçin yapılandırma dosyaları hızlı bir şekilde oluşturun.</span><span class="sxs-lookup"><span data-stu-id="072be-152">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) with the `/config:`*filename*`[,`*filename*`]` switch to quickly create configuration files.</span></span>  
  
## <a name="using-default-endpoints"></a><span data-ttu-id="072be-153">Varsayılan uç noktaları kullanma</span><span class="sxs-lookup"><span data-stu-id="072be-153">Using Default Endpoints</span></span>  
 <span data-ttu-id="072be-154">Uç nokta kod veya yapılandırma belirtilirse çalışma zamanı hizmeti tarafından uygulanan her bir hizmet sözleşmesi için her bir temel adres için bir varsayılan uç nokta ekleyerek varsayılan uç noktaları sağlar.</span><span class="sxs-lookup"><span data-stu-id="072be-154">If no endpoints are specified in code or in configuration then the runtime provides default endpoints by adding one default endpoint for each base address for each service contract implemented by the service.</span></span> <span data-ttu-id="072be-155">Kod veya yapılandırma taban adresi belirtilebilir ve varsayılan uç noktaları eklenip <xref:System.ServiceModel.ICommunicationObject.Open> üzerinde çağrılır <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="072be-155">The base address can be specified in code or in configuration, and the default endpoints are added when <xref:System.ServiceModel.ICommunicationObject.Open> is called on the <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="072be-156">Bu örnek, önceki bölümde aynı örneği olmakla birlikte varsayılan uç noktalarını, uç nokta belirlendiğinden eklenir.</span><span class="sxs-lookup"><span data-stu-id="072be-156">This example is the same example from the previous section, but since no endpoints are specified, the default endpoints are added.</span></span>  
  
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
  
 <span data-ttu-id="072be-157">Uç noktalar açıkça verdiyse, varsayılan uç noktaları hala çağırarak eklenebilir <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints%2A> üzerinde <xref:System.ServiceModel.ServiceHost> çağırmadan önce <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span><span class="sxs-lookup"><span data-stu-id="072be-157">If endpoints are explicitly provided, the default endpoints can still be added by calling <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints%2A> on the <xref:System.ServiceModel.ServiceHost> before calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span></span> <span data-ttu-id="072be-158">Varsayılan uç noktaları hakkında daha fazla bilgi için bkz. [Basitleştirilmiş yapılandırma](../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="072be-158">For more information about default endpoints, see [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="072be-159">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="072be-159">See Also</span></span>  
 [<span data-ttu-id="072be-160">Hizmet Anlaşmalarını Uygulama</span><span class="sxs-lookup"><span data-stu-id="072be-160">Implementing Service Contracts</span></span>](../../../docs/framework/wcf/implementing-service-contracts.md)
