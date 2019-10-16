---
title: Uç Noktası Oluşturma Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- endpoints [WCF], overview
ms.assetid: f4dce0fb-6f54-47e6-8054-86d7f574b91c
ms.openlocfilehash: bf6bfb10123223bf689945ef93ff09219a68092c
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319922"
---
# <a name="endpoint-creation-overview"></a><span data-ttu-id="f23c1-102">Uç Noktası Oluşturma Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f23c1-102">Endpoint Creation Overview</span></span>

<span data-ttu-id="f23c1-103">Bir Windows Communication Foundation (WCF) hizmeti olan tüm iletişimler hizmetin *uç noktaları* aracılığıyla oluşur.</span><span class="sxs-lookup"><span data-stu-id="f23c1-103">All communication with a Windows Communication Foundation (WCF) service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="f23c1-104">Uç noktalar, istemcilerin bir WCF hizmetinin sunduğu işlevlere erişmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="f23c1-104">Endpoints provide the clients access to the functionality that a WCF service offers.</span></span> <span data-ttu-id="f23c1-105">Bu bölüm bir uç noktanın yapısını açıklar ve bir uç noktanın yapılandırma ve kodda nasıl tanımlanacağını özetler.</span><span class="sxs-lookup"><span data-stu-id="f23c1-105">This section describes the structure of an endpoint and outlines how to define an endpoint in configuration and in code.</span></span>

## <a name="the-structure-of-an-endpoint"></a><span data-ttu-id="f23c1-106">Bir uç noktanın yapısı</span><span class="sxs-lookup"><span data-stu-id="f23c1-106">The Structure of an Endpoint</span></span>

<span data-ttu-id="f23c1-107">Her uç nokta, uç noktanın nerede bulunacağını belirten bir adres içerir, bir istemcinin uç noktasıyla nasıl iletişim kurabildiğini belirten bir bağlama ve kullanılabilir yöntemleri tanımlayan bir anlaşma.</span><span class="sxs-lookup"><span data-stu-id="f23c1-107">Each endpoint contains an address that indicates where to find the endpoint, a binding that specifies how a client can communicate with the endpoint, and a contract that identifies the methods available.</span></span>

- <span data-ttu-id="f23c1-108">**Adres**.</span><span class="sxs-lookup"><span data-stu-id="f23c1-108">**Address**.</span></span> <span data-ttu-id="f23c1-109">Adres, uç noktayı benzersiz bir şekilde tanımlar ve hizmetin bulunduğu potansiyel tüketicilere bildirir.</span><span class="sxs-lookup"><span data-stu-id="f23c1-109">The address uniquely identifies the endpoint and tells potential consumers where the service is located.</span></span> <span data-ttu-id="f23c1-110">Bir kimlik, bazı Web Hizmetleri Açıklama Dili (WSDL) öğeleri ve isteğe bağlı üstbilgiler koleksiyonu içeren bir Tekdüzen Kaynak tanımlayıcısı (URI) ve adres özellikleri içeren <xref:System.ServiceModel.EndpointAddress> adresi tarafından WCF nesne modelinde temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="f23c1-110">It is represented in the WCF object model by the <xref:System.ServiceModel.EndpointAddress> address, which contains a Uniform Resource Identifier (URI) and address properties that include an identity, some Web Services Description Language (WSDL) elements, and a collection of optional headers.</span></span> <span data-ttu-id="f23c1-111">İsteğe bağlı üstbilgiler, uç noktayı tanımlamak veya bunlarla etkileşime geçmek için ek ayrıntılı adresleme bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="f23c1-111">The optional headers provide additional detailed addressing information to identify or interact with the endpoint.</span></span> <span data-ttu-id="f23c1-112">Daha fazla bilgi için bkz. [uç nokta adresi belirtme](specifying-an-endpoint-address.md).</span><span class="sxs-lookup"><span data-stu-id="f23c1-112">For more information, see [Specifying an Endpoint Address](specifying-an-endpoint-address.md).</span></span>

- <span data-ttu-id="f23c1-113">**Bağlama**.</span><span class="sxs-lookup"><span data-stu-id="f23c1-113">**Binding**.</span></span> <span data-ttu-id="f23c1-114">Bağlama, uç noktayla nasıl iletişim kuracağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f23c1-114">The binding specifies how to communicate with the endpoint.</span></span> <span data-ttu-id="f23c1-115">Bağlama, (örneğin, metin veya ikili) ve hangi güvenlik gereksinimlerinin gerekli olduğu ile (örneğin, metin veya ikili) hangi Aktarım protokolünün kullanılacağını (örneğin, TCP veya HTTP) dahil olmak üzere, uç noktanın dünya ile nasıl iletişim kuracağını belirtir ( örnek, Güvenli Yuva Katmanı [SSL] veya SOAP iletisi güvenliği).</span><span class="sxs-lookup"><span data-stu-id="f23c1-115">The binding specifies how the endpoint communicates with the world, including which transport protocol to use (for example, TCP or HTTP), which encoding to use for the messages (for example, text or binary), and which security requirements are necessary (for example, Secure Sockets Layer [SSL] or SOAP message security).</span></span> <span data-ttu-id="f23c1-116">Daha fazla bilgi için bkz. [Hizmetleri ve Istemcileri yapılandırmak Için bağlamaları kullanma](using-bindings-to-configure-services-and-clients.md).</span><span class="sxs-lookup"><span data-stu-id="f23c1-116">For more information, see [Using Bindings to Configure Services and Clients](using-bindings-to-configure-services-and-clients.md).</span></span>

- <span data-ttu-id="f23c1-117">**Hizmet sözleşmesi**.</span><span class="sxs-lookup"><span data-stu-id="f23c1-117">**Service contract**.</span></span> <span data-ttu-id="f23c1-118">Hizmet sözleşmesi, uç noktanın istemciye sunduğu işlevselliği özetler.</span><span class="sxs-lookup"><span data-stu-id="f23c1-118">The service contract outlines what functionality the endpoint exposes to the client.</span></span> <span data-ttu-id="f23c1-119">Bir anlaşma, bir istemcinin çağırabilecekleri işlemleri, ileti formunu ve giriş parametrelerinin türünü ya da işlemi çağırmak için gereken verileri, istemcinin beklediği işlem veya yanıt iletisi türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="f23c1-119">A contract specifies the operations that a client can call, the form of the message and the type of input parameters or data required to call the operation, and the kind of processing or response message the client can expect.</span></span> <span data-ttu-id="f23c1-120">Üç temel sözleşme türü, temel ileti değişimi desenlerine (MEPs) karşılık gelir: veri birimi (tek yönlü), istek/yanıt ve çift yönlü (çift yönlü).</span><span class="sxs-lookup"><span data-stu-id="f23c1-120">Three basic types of contracts correspond to basic message exchange patterns (MEPs): datagram (one-way), request/reply, and duplex (bidirectional).</span></span> <span data-ttu-id="f23c1-121">Hizmet sözleşmesi, erişim sırasında belirli veri türleri ve ileti biçimleri istemek için veri ve ileti sözleşmeleri de kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="f23c1-121">The service contract can also employ data and message contracts to require specific data types and message formats when being accessed.</span></span> <span data-ttu-id="f23c1-122">Hizmet sözleşmesinin nasıl tanımlanacağı hakkında daha fazla bilgi için bkz. [hizmet sözleşmeleri tasarlama](designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="f23c1-122">For more information about how to define a service contract, see [Designing Service Contracts](designing-service-contracts.md).</span></span> <span data-ttu-id="f23c1-123">Bir istemcinin, bir çift yönlü MEP 'de hizmetten ileti almak için, geri arama sözleşmesi olarak adlandırılan hizmet tanımlı bir sözleşmeyi uygulamak için de gerekli olabileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="f23c1-123">Note that a client may also be required to implement a service-defined contract, called a callback contract, to receive messages from the service in a duplex MEP.</span></span> <span data-ttu-id="f23c1-124">Daha fazla bilgi için bkz. [çift yönlü hizmetler](./feature-details/duplex-services.md).</span><span class="sxs-lookup"><span data-stu-id="f23c1-124">For more information, see [Duplex Services](./feature-details/duplex-services.md).</span></span>

<span data-ttu-id="f23c1-125">Bir hizmetin uç noktası, kod kullanılarak veya bildirimli olarak yapılandırma yoluyla imperatively belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="f23c1-125">The endpoint for a service can be specified either imperatively by using code or declaratively through configuration.</span></span> <span data-ttu-id="f23c1-126">Hiçbir uç nokta belirtilmemişse, çalışma zamanı, hizmet tarafından uygulanan her bir hizmet sözleşmesinin her bir temel adresi için bir varsayılan uç nokta ekleyerek varsayılan uç noktaları sağlar.</span><span class="sxs-lookup"><span data-stu-id="f23c1-126">If no endpoints are specified then the runtime provides default endpoints by adding one default endpoint for each base address for each service contract implemented by the service.</span></span> <span data-ttu-id="f23c1-127">Dağıtılmış bir hizmetin bağlamaları ve adresleri genellikle hizmet geliştirildiğinde kullanılanlardan farklı olduğundan, koddaki uç noktaların tanımlanması genellikle pratik değildir.</span><span class="sxs-lookup"><span data-stu-id="f23c1-127">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="f23c1-128">Genellikle, kod yerine yapılandırma kullanarak hizmet uç noktaları tanımlamak daha pratik bir yapılandırmadır.</span><span class="sxs-lookup"><span data-stu-id="f23c1-128">Generally, it is more practical to define service endpoints using configuration rather than code.</span></span> <span data-ttu-id="f23c1-129">Bağlama ve adresleme bilgilerinin koddan tutulması, uygulamayı yeniden derlemek ve yeniden dağıtmak zorunda kalmadan değiştirilmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="f23c1-129">Keeping the binding and addressing information out of the code allows them to change without having to recompile and redeploy the application.</span></span>

> [!NOTE]
> <span data-ttu-id="f23c1-130">Kimliğe bürünme gerçekleştiren bir hizmet uç noktası eklerken, sözleşmeyi yeni bir <xref:System.ServiceModel.Description.ServiceDescription> nesnesine doğru bir şekilde yüklemek için <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> yöntemlerinden birini ya da <xref:System.ServiceModel.Description.ContractDescription.GetContract%28System.Type%2CSystem.Type%29> yöntemini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f23c1-130">When adding a service endpoint that performs impersonation, you must either use one of the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> methods or the <xref:System.ServiceModel.Description.ContractDescription.GetContract%28System.Type%2CSystem.Type%29> method to properly load the contract into a new <xref:System.ServiceModel.Description.ServiceDescription> object.</span></span>

## <a name="defining-endpoints-in-code"></a><span data-ttu-id="f23c1-131">Koddaki uç noktaları tanımlama</span><span class="sxs-lookup"><span data-stu-id="f23c1-131">Defining Endpoints in Code</span></span>

<span data-ttu-id="f23c1-132">Aşağıdaki örnek, kodda aşağıdaki gibi bir uç noktanın nasıl belirtildiğini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="f23c1-132">The following example illustrates how to specify an endpoint in code with the following:</span></span>

- <span data-ttu-id="f23c1-133">"Hello \<name >!" yanıtıyla birlikte birisinin adını ve yankısını kabul eden `IEcho` hizmet türü için bir sözleşme tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="f23c1-133">Define a contract for an `IEcho` type of service that accepts someone's name and echo with the response "Hello \<name>!".</span></span>

- <span data-ttu-id="f23c1-134">@No__t-1 sözleşmesi tarafından tanımlanan türde `Echo` hizmeti uygulayın.</span><span class="sxs-lookup"><span data-stu-id="f23c1-134">Implement an `Echo` service of the type defined by the `IEcho` contract.</span></span>

- <span data-ttu-id="f23c1-135">Hizmet için `http://localhost:8000/Echo` ' nın bir uç nokta adresini belirtin.</span><span class="sxs-lookup"><span data-stu-id="f23c1-135">Specify an endpoint address of `http://localhost:8000/Echo` for the service.</span></span>

- <span data-ttu-id="f23c1-136">@No__t-0 hizmetini <xref:System.ServiceModel.WSHttpBinding> bağlamayı kullanarak yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="f23c1-136">Configure the `Echo` service using a <xref:System.ServiceModel.WSHttpBinding> binding.</span></span>

```csharp
namespace Echo
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
> <span data-ttu-id="f23c1-137">Hizmet ana bilgisayarı bir temel adresle oluşturulur ve ardından temel adrese göre adresin geri kalanı bir uç noktanın parçası olarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="f23c1-137">The service host is created with a base address and then the rest of the address, relative to the base address, is specified as part of an endpoint.</span></span> <span data-ttu-id="f23c1-138">Adresin bu bölümlenmesi, birden çok uç noktanın bir konaktaki hizmetler için daha kolay tanımlanmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="f23c1-138">This partitioning of the address allows multiple endpoints to be defined more conveniently for services at a host.</span></span>

> [!NOTE]
> <span data-ttu-id="f23c1-139">Hizmet uygulamasındaki <xref:System.ServiceModel.Description.ServiceDescription> ' ın özellikleri, daha sonra <xref:System.ServiceModel.ServiceHostBase> ' deki <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> yöntemine değiştirilmemelidir.</span><span class="sxs-lookup"><span data-stu-id="f23c1-139">Properties of <xref:System.ServiceModel.Description.ServiceDescription> in the service application must not be modified subsequent to the <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> method on <xref:System.ServiceModel.ServiceHostBase>.</span></span> <span data-ttu-id="f23c1-140">@No__t-0 özelliği ve <xref:System.ServiceModel.ServiceHostBase> ve <xref:System.ServiceModel.ServiceHost> üzerindeki `AddServiceEndpoint` yöntemleri gibi bazı üyeler o noktadan sonra değiştirilirse bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f23c1-140">Some members, such as the <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> property and the `AddServiceEndpoint` methods on <xref:System.ServiceModel.ServiceHostBase> and <xref:System.ServiceModel.ServiceHost>, throw an exception if modified past that point.</span></span> <span data-ttu-id="f23c1-141">Diğerleri bunları değiştirmenize izin verir, ancak sonuç tanımsızdır.</span><span class="sxs-lookup"><span data-stu-id="f23c1-141">Others permit you to modify them, but the result is undefined.</span></span>
>
> <span data-ttu-id="f23c1-142">Benzer şekilde, istemcide <xref:System.ServiceModel.Description.ServiceEndpoint> değerleri <xref:System.ServiceModel.ChannelFactory> ' de <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> ' e çağrıdan sonra değiştirilmemelidir.</span><span class="sxs-lookup"><span data-stu-id="f23c1-142">Similarly, on the client the <xref:System.ServiceModel.Description.ServiceEndpoint> values must not be modified after the call to <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> on the <xref:System.ServiceModel.ChannelFactory>.</span></span> <span data-ttu-id="f23c1-143">@No__t-0 özelliği o noktadan sonra değiştirilirse bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f23c1-143">The <xref:System.ServiceModel.ChannelFactory.Credentials%2A> property throws an exception if modified past that point.</span></span> <span data-ttu-id="f23c1-144">Diğer istemci açıklama değerleri hata olmadan değiştirilebilir, ancak sonuç tanımsızdır.</span><span class="sxs-lookup"><span data-stu-id="f23c1-144">The other client description values can be modified without error, but the result is undefined.</span></span>
>
> <span data-ttu-id="f23c1-145">Hizmet veya istemci için, <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> çağrılmadan önce açıklamayı değiştirmeniz önerilir.</span><span class="sxs-lookup"><span data-stu-id="f23c1-145">Whether for the service or client, it is recommended that you modify the description prior to calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span></span>

## <a name="defining-endpoints-in-configuration"></a><span data-ttu-id="f23c1-146">Yapılandırmada uç noktaları tanımlama</span><span class="sxs-lookup"><span data-stu-id="f23c1-146">Defining Endpoints in Configuration</span></span>

<span data-ttu-id="f23c1-147">Bir uygulama oluştururken, kararları genellikle uygulamayı dağıtan yöneticiye erteleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f23c1-147">When creating an application, you often want to defer decisions to the administrator who is deploying the application.</span></span> <span data-ttu-id="f23c1-148">Örneğin, genellikle bir hizmet adresinin (URI) ne olduğunu bilmenin bir yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="f23c1-148">For example, there is often no way of knowing in advance what a service address (a URI) will be.</span></span> <span data-ttu-id="f23c1-149">Bir adresi sabit kodlamak yerine, bir hizmet oluşturduktan sonra yöneticinin bunu yapmasına izin vermek tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="f23c1-149">Instead of hard-coding an address, it is preferable to allow an administrator to do so after creating a service.</span></span> <span data-ttu-id="f23c1-150">Bu esneklik yapılandırma aracılığıyla gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="f23c1-150">This flexibility is accomplished through configuration.</span></span> <span data-ttu-id="f23c1-151">Ayrıntılar için bkz. [Hizmetleri yapılandırma](configuring-services.md).</span><span class="sxs-lookup"><span data-stu-id="f23c1-151">For details, see [Configuring Services](configuring-services.md).</span></span>

> [!NOTE]
> <span data-ttu-id="f23c1-152">Yapılandırma dosyalarını hızlıca oluşturmak için `/config:`*dosya adı*`[,`*Dosya*adı `]` anahtarıyla [ServiceModel meta veri yardımcı programı aracını (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="f23c1-152">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) with the `/config:`*filename*`[,`*filename*`]` switch to quickly create configuration files.</span></span>

## <a name="using-default-endpoints"></a><span data-ttu-id="f23c1-153">Varsayılan uç noktaları kullanma</span><span class="sxs-lookup"><span data-stu-id="f23c1-153">Using Default Endpoints</span></span>

<span data-ttu-id="f23c1-154">Kodda veya yapılandırmada hiçbir uç nokta belirtilmemişse, çalışma zamanı, hizmet tarafından uygulanan her bir hizmet sözleşmesinin her bir temel adresi için bir varsayılan uç nokta ekleyerek varsayılan uç noktaları sağlar.</span><span class="sxs-lookup"><span data-stu-id="f23c1-154">If no endpoints are specified in code or in configuration then the runtime provides default endpoints by adding one default endpoint for each base address for each service contract implemented by the service.</span></span> <span data-ttu-id="f23c1-155">Temel adres kodda veya yapılandırmada belirtilebilir ve varsayılan uç noktalar <xref:System.ServiceModel.ICommunicationObject.Open> <xref:System.ServiceModel.ServiceHost> ' de çağrıldığında eklenir.</span><span class="sxs-lookup"><span data-stu-id="f23c1-155">The base address can be specified in code or in configuration, and the default endpoints are added when <xref:System.ServiceModel.ICommunicationObject.Open> is called on the <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="f23c1-156">Bu örnek, önceki bölümden aynı örnektir, ancak hiçbir uç nokta belirtilmediğinden varsayılan uç noktalar eklenir.</span><span class="sxs-lookup"><span data-stu-id="f23c1-156">This example is the same example from the previous section, but since no endpoints are specified, the default endpoints are added.</span></span>

```csharp
namespace Echo
{
   // Define the contract for the IEcho service
   [ServiceContract]
   public interface IEcho
   {
       [OperationContract]
       String Hello(string name)
   }

   // Create an Echo service that implements IEcho contract
   public class Echo : IEcho
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

 <span data-ttu-id="f23c1-157">Uç noktalar açıkça sağlanmışsa, <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> çağrılmadan önce <xref:System.ServiceModel.ServiceHost> ' de <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints%2A> çağırarak varsayılan uç noktalar eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="f23c1-157">If endpoints are explicitly provided, the default endpoints can still be added by calling <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints%2A> on the <xref:System.ServiceModel.ServiceHost> before calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span></span> <span data-ttu-id="f23c1-158">Varsayılan uç noktalar hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](./samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="f23c1-158">For more information about default endpoints, see [Simplified Configuration](simplified-configuration.md) and [Simplified Configuration for WCF Services](./samples/simplified-configuration-for-wcf-services.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f23c1-159">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f23c1-159">See also</span></span>

- [<span data-ttu-id="f23c1-160">Hizmet Anlaşmalarını Uygulama</span><span class="sxs-lookup"><span data-stu-id="f23c1-160">Implementing Service Contracts</span></span>](implementing-service-contracts.md)
