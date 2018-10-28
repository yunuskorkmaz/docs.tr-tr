---
title: 'Nasıl yapılır: Güvenilir Bir Oturumda İleti Alma ve Gönderme'
ms.date: 03/30/2017
ms.assetid: 87cd0e75-dd2c-44c1-8da0-7b494bbdeaea
ms.openlocfilehash: 53e5661bf140540cd0fc7a9fcb739b67488b8491
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50195742"
---
# <a name="how-to-exchange-messages-within-a-reliable-session"></a><span data-ttu-id="fbda1-102">Nasıl yapılır: Güvenilir Bir Oturumda İleti Alma ve Gönderme</span><span class="sxs-lookup"><span data-stu-id="fbda1-102">How to: Exchange Messages Within a Reliable Session</span></span>

<span data-ttu-id="fbda1-103">Bu konuda, bu tür bir oturumu destekleyen sistem tarafından sağlanan bağlamalar, ancak değil, varsayılan olarak kullanarak bir güvenilir oturum etkinleştirmek için gereken adımlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fbda1-103">This topic outlines the steps required to enable a reliable session using one of the system-provided bindings that support such a session, but not by default.</span></span> <span data-ttu-id="fbda1-104">Kesin kod kullanarak bir güvenilir oturum etkinleştirmek ya da yapılandırma dosyanızdaki bildirimli olarak.</span><span class="sxs-lookup"><span data-stu-id="fbda1-104">You enable a reliable session imperatively using code or declaratively in your configuration file.</span></span> <span data-ttu-id="fbda1-105">Bu yordam, güvenilir oturum etkinleştirmek ve iletileri, gönderildiği aynı sırada ulşamasını işleyebileceği için hizmet ve istemci yapılandırma dosyalarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="fbda1-105">This procedure uses the client and service configuration files to enable the reliable session and to stipulate that the messages arrive in the same order in which they were sent.</span></span>

<span data-ttu-id="fbda1-106">Uç nokta yapılandırma öğesi içeren bu yordamı önemli bir parçası olan bir `bindingConfiguration` adlı bir bağlama yapılandırmasını başvuran öznitelik `Binding1`.</span><span class="sxs-lookup"><span data-stu-id="fbda1-106">The key part of this procedure is that the endpoint configuration element contain a `bindingConfiguration` attribute that references a binding configuration named `Binding1`.</span></span> <span data-ttu-id="fbda1-107">[  **\<Bağlama >** ](../../../../docs/framework/misc/binding.md) yapılandırma öğesi güvenilir oturumlar etkinleştirmek için bu ada başvuran `enabled` özniteliği [  **\<reliableSession >** ](https://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) öğesine `true`.</span><span class="sxs-lookup"><span data-stu-id="fbda1-107">The [**\<binding>**](../../../../docs/framework/misc/binding.md) configuration element references this name to enable reliable sessions by setting the `enabled` attribute of the [**\<reliableSession>**](https://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) element to `true`.</span></span> <span data-ttu-id="fbda1-108">Ayarlayarak güvenilir oturum için belirttiğiniz sıralı teslim Güvenceleri `ordered` özniteliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="fbda1-108">You specify the ordered delivery assurances for the reliable session by setting the `ordered` attribute to `true`.</span></span>

<span data-ttu-id="fbda1-109">Bu örnekte kaynak kopyası için bkz: [WS güvenilir oturum](../../../../docs/framework/wcf/samples/ws-reliable-session.md).</span><span class="sxs-lookup"><span data-stu-id="fbda1-109">For the source copy of this example, see [WS Reliable Session](../../../../docs/framework/wcf/samples/ws-reliable-session.md).</span></span>

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="fbda1-110">Güvenilir oturum kullanılacak WSHttpBinding hizmetini yapılandırma</span><span class="sxs-lookup"><span data-stu-id="fbda1-110">Configure the service with a WSHttpBinding to use a reliable session</span></span>

1. <span data-ttu-id="fbda1-111">Hizmet türü için bir hizmet anlaşmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fbda1-111">Define a service contract for the type of service.</span></span>

   [!code-csharp[c_HowTo_UseReliableSession#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1121)]

1. <span data-ttu-id="fbda1-112">Hizmet sözleşmesi bir hizmet sınıfında uygulayın.</span><span class="sxs-lookup"><span data-stu-id="fbda1-112">Implement the service contract in a service class.</span></span> <span data-ttu-id="fbda1-113">Adres veya bağlama bilgileri hizmeti uygulaması içinde belirtilmemiş unutmayın.</span><span class="sxs-lookup"><span data-stu-id="fbda1-113">Note that the address or binding information isn't specified inside the implementation of the service.</span></span> <span data-ttu-id="fbda1-114">Yapılandırma dosyasından adresi veya bağlama bilgileri almak üzere kod yazmak için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="fbda1-114">You aren't required to write code to retrieve the address or binding information from the configuration file.</span></span>

   [!code-csharp[c_HowTo_UseReliableSession#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1122)]

1. <span data-ttu-id="fbda1-115">Oluşturma bir *Web.config* yapılandırmak için bir uç nokta için bir dosya `CalculatorService` kullanan <xref:System.ServiceModel.WSHttpBinding> etkin ve sıralı teslim gerekli iletilerin güvenilir oturum ile.</span><span class="sxs-lookup"><span data-stu-id="fbda1-115">Create a *Web.config* file to configure an endpoint for the `CalculatorService` that uses the <xref:System.ServiceModel.WSHttpBinding> with reliable session enabled and ordered delivery of messages required.</span></span>

   [!code-xml[c_HowTo_UseReliableSession#2111](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/web.config#2111)]

1. <span data-ttu-id="fbda1-116">Oluşturma bir *Service.svc* satırını içeren dosya:</span><span class="sxs-lookup"><span data-stu-id="fbda1-116">Create a *Service.svc* file that contains the line:</span></span>

   ```
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```

1.  <span data-ttu-id="fbda1-117">Bir yerde *Service.svc* Internet Information Services (IIS) sanal dizininizin dosyasında.</span><span class="sxs-lookup"><span data-stu-id="fbda1-117">Place the *Service.svc* file in your Internet Information Services (IIS) virtual directory.</span></span>

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="fbda1-118">Güvenilir oturum kullanılacak WSHttpBinding istemciyi Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="fbda1-118">Configure the client with a WSHttpBinding to use a reliable session</span></span>

1. <span data-ttu-id="fbda1-119">Kullanım [ServiceModel meta veri yardımcı Programracı (*Svcutil.exe*)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) hizmet meta verilerinden kodu oluşturmak için komut satırından:</span><span class="sxs-lookup"><span data-stu-id="fbda1-119">Use the [ServiceModel Metadata Utility Tool (*Svcutil.exe*)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) from the command line to generate code from service metadata:</span></span>

   ```console
   Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
   ```

1. <span data-ttu-id="fbda1-120">Oluşturulan istemci içeren `ICalculator` istemci uygulaması karşılaması gereken hizmet sözleşmesini tanımlayan arabirimi.</span><span class="sxs-lookup"><span data-stu-id="fbda1-120">The generated client contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>

   [!code-csharp[C_HowTo_UseReliableSession#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1221)]

1. <span data-ttu-id="fbda1-121">Oluşturulan istemci uygulaması da uygulamasını içerir `ClientCalculator`.</span><span class="sxs-lookup"><span data-stu-id="fbda1-121">The generated client application also contains the implementation of the `ClientCalculator`.</span></span> <span data-ttu-id="fbda1-122">Adres ve bağlama bilgilerini herhangi bir uygulama hizmetinin içinde belirtilmemiş unutmayın.</span><span class="sxs-lookup"><span data-stu-id="fbda1-122">Note that the address and binding information isn't specified anywhere inside the implementation of the service.</span></span> <span data-ttu-id="fbda1-123">Yapılandırma dosyasından adresi veya bağlama bilgileri almak üzere kod yazmak için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="fbda1-123">You aren't required to write code to retrieve the address or binding information from the configuration file.</span></span>

   [!code-csharp[C_HowTo_UseReliableSession#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1222)]

1. <span data-ttu-id="fbda1-124">*Svcutil.exe* ayrıca kullanan istemci yapılandırmasını oluşturur <xref:System.ServiceModel.WSHttpBinding> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="fbda1-124">*Svcutil.exe* also generates the configuration for the client that uses the <xref:System.ServiceModel.WSHttpBinding> class.</span></span> <span data-ttu-id="fbda1-125">Yapılandırma dosyası adı *App.config* Visual Studio kullanarak.</span><span class="sxs-lookup"><span data-stu-id="fbda1-125">Name the configuration file *App.config* when using Visual Studio.</span></span>

   [!code-xml[C_HowTo_UseReliableSession#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/app.config#2211)]

1. <span data-ttu-id="fbda1-126">Bir örneğini oluşturmak `ClientCalculator` uygulamada ve hizmet işlemleri çağırın.</span><span class="sxs-lookup"><span data-stu-id="fbda1-126">Create an instance of the `ClientCalculator` in an application and call the service operations.</span></span>

   [!code-csharp[C_HowTo_UseReliableSession#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1223)]

1. <span data-ttu-id="fbda1-127">Derleyin ve istemci çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="fbda1-127">Compile and run the client.</span></span>

## <a name="example"></a><span data-ttu-id="fbda1-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="fbda1-128">Example</span></span>

<span data-ttu-id="fbda1-129">Birçok sistem tarafından sağlanan bağlamalar güvenilir oturumlar varsayılan olarak destekler.</span><span class="sxs-lookup"><span data-stu-id="fbda1-129">Several of the system-provided bindings support reliable sessions by default.</span></span> <span data-ttu-id="fbda1-130">Bu güncelleştirmeler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="fbda1-130">These include:</span></span>

- <xref:System.ServiceModel.WSDualHttpBinding>

- <xref:System.ServiceModel.NetNamedPipeBinding>

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>

<span data-ttu-id="fbda1-131">Güvenilir oturumlar destekleyen özel bağlama oluşturma örneği için bkz: [nasıl yapılır: HTTPS ile özel bir güvenilir oturum bağlama oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md).</span><span class="sxs-lookup"><span data-stu-id="fbda1-131">For an example of how to create a custom binding that supports reliable sessions, see [How to: Create a Custom Reliable Session Binding with HTTPS](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fbda1-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fbda1-132">See also</span></span>

[<span data-ttu-id="fbda1-133">Güvenilir Oturumlar</span><span class="sxs-lookup"><span data-stu-id="fbda1-133">Reliable Sessions</span></span>](../../../../docs/framework/wcf/feature-details/reliable-sessions.md)
