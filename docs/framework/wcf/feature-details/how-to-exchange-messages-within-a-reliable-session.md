---
title: "Nasıl yapılır: Güvenilir Bir Oturumda İleti Alma ve Gönderme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 87cd0e75-dd2c-44c1-8da0-7b494bbdeaea
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6207b526aa98fd01892b493ab5b6ad6a58abc3c0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-exchange-messages-within-a-reliable-session"></a><span data-ttu-id="f8130-102">Nasıl yapılır: Güvenilir Bir Oturumda İleti Alma ve Gönderme</span><span class="sxs-lookup"><span data-stu-id="f8130-102">How to: Exchange Messages Within a Reliable Session</span></span>

<span data-ttu-id="f8130-103">Bu konuda bu tür bir oturum desteği sistem tarafından sağlanan bağlamalar, ancak varsayılan kullanarak bir güvenilir oturum etkinleştirmek için gereken adımlar açıklanır.</span><span class="sxs-lookup"><span data-stu-id="f8130-103">This topic outlines the steps required to enable a reliable session using one of the system-provided bindings that support such a session, but not by default.</span></span> <span data-ttu-id="f8130-104">İmperatively kod kullanarak bir güvenilir oturum etkinleştirmek veya bildirimli olarak yapılandırma dosyanızda.</span><span class="sxs-lookup"><span data-stu-id="f8130-104">You enable a reliable session imperatively using code or declaratively in your configuration file.</span></span> <span data-ttu-id="f8130-105">Bu yordam, güvenli oturum etkinleştirmek ve iletiler içinde gönderildikleri sırayla geldiğinde ilkelerde izni belirtmek için istemci ve hizmet yapılandırma dosyalarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="f8130-105">This procedure uses the client and service configuration files to enable the reliable session and to stipulate that the messages arrive in the same order in which they were sent.</span></span>

<span data-ttu-id="f8130-106">Uç nokta yapılandırma öğesi içeren bu yordamı anahtar parçası olan bir `bindingConfiguration` adlı bir bağlama yapılandırması başvuran özniteliği `Binding1`.</span><span class="sxs-lookup"><span data-stu-id="f8130-106">The key part of this procedure is that the endpoint configuration element contain a `bindingConfiguration` attribute that references a binding configuration named `Binding1`.</span></span> <span data-ttu-id="f8130-107">[  **\<Bağlama >** ](../../../../docs/framework/misc/binding.md) yapılandırma öğesine başvuruyor ayarlayarak güvenilir oturumlar etkinleştirmek için bu ad `enabled` özniteliği [  **\<reliableSession >** ](http://msdn.microsoft.com/en-us/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) öğesine `true`.</span><span class="sxs-lookup"><span data-stu-id="f8130-107">The [**\<binding>**](../../../../docs/framework/misc/binding.md) configuration element references this name to enable reliable sessions by setting the `enabled` attribute of the [**\<reliableSession>**](http://msdn.microsoft.com/en-us/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) element to `true`.</span></span> <span data-ttu-id="f8130-108">Ayarlayarak güvenilir oturum için belirttiğiniz sıralı teslim Güvenceleri `ordered` özniteliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="f8130-108">You specify the ordered delivery assurances for the reliable session by setting the `ordered` attribute to `true`.</span></span>

<span data-ttu-id="f8130-109">Bu örnekte kaynak kopyası için bkz: [WS güvenilir oturum](../../../../docs/framework/wcf/samples/ws-reliable-session.md).</span><span class="sxs-lookup"><span data-stu-id="f8130-109">For the source copy of this example, see [WS Reliable Session](../../../../docs/framework/wcf/samples/ws-reliable-session.md).</span></span>

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="f8130-110">Güvenilir oturum kullanmak için bir WSHttpBinding hizmetini yapılandırma</span><span class="sxs-lookup"><span data-stu-id="f8130-110">Configure the service with a WSHttpBinding to use a reliable session</span></span>

1. <span data-ttu-id="f8130-111">Hizmet türü için bir hizmet sözleşmesini tanımlama.</span><span class="sxs-lookup"><span data-stu-id="f8130-111">Define a service contract for the type of service.</span></span>

   [!code-csharp[c_HowTo_UseReliableSession#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1121)]

1. <span data-ttu-id="f8130-112">Bir hizmet sınıfında Hizmet sözleşmesini uygulama.</span><span class="sxs-lookup"><span data-stu-id="f8130-112">Implement the service contract in a service class.</span></span> <span data-ttu-id="f8130-113">Adres veya bağlama bilgisi hizmet uygulaması içinde belirlenmezse unutmayın.</span><span class="sxs-lookup"><span data-stu-id="f8130-113">Note that the address or binding information isn't specified inside the implementation of the service.</span></span> <span data-ttu-id="f8130-114">Yapılandırma dosyasından adresi veya bağlama bilgileri bilgileri almak üzere kod yazmak için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="f8130-114">You aren't required to write code to retrieve the address or binding information information from the configuration file.</span></span>

   [!code-csharp[c_HowTo_UseReliableSession#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1122)]

1. <span data-ttu-id="f8130-115">Oluşturma bir *Web.config* için bir uç nokta yapılandırmak için bir dosya `CalculatorService` kullanan <xref:System.ServiceModel.WSHttpBinding> etkin ve sıralı gerekli iletileri teslimini güvenilir oturum ile.</span><span class="sxs-lookup"><span data-stu-id="f8130-115">Create a *Web.config* file to configure an endpoint for the `CalculatorService` that uses the <xref:System.ServiceModel.WSHttpBinding> with reliable session enabled and ordered delivery of messages required.</span></span>

   [!code-xml[c_HowTo_UseReliableSession#2111](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/web.config#2111)]

1. <span data-ttu-id="f8130-116">Oluşturma bir *Service.svc* bir çizgi içeren dosya:</span><span class="sxs-lookup"><span data-stu-id="f8130-116">Create a *Service.svc* file that contains the line:</span></span>

   ```
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```

1.  <span data-ttu-id="f8130-117">Yer *Service.svc* , Internet Information Services (IIS) sanal dizinde dosya.</span><span class="sxs-lookup"><span data-stu-id="f8130-117">Place the *Service.svc* file in your Internet Information Services (IIS) virtual directory.</span></span>

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="f8130-118">Güvenilir oturum kullanmak için bir WSHttpBinding istemciyi Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="f8130-118">Configure the client with a WSHttpBinding to use a reliable session</span></span>

1. <span data-ttu-id="f8130-119">Kullanım [ServiceModel meta veri yardımcı Programracı (*Svcutil.exe*)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) hizmet meta verilerinden kodu oluşturmak için komut satırından:</span><span class="sxs-lookup"><span data-stu-id="f8130-119">Use the [ServiceModel Metadata Utility Tool (*Svcutil.exe*)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) from the command line to generate code from service metadata:</span></span>

   ```console
   Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
   ```

1. <span data-ttu-id="f8130-120">Oluşturulan istemci içeren `ICalculator` istemci uygulaması getirmelidir hizmet sözleşmesini tanımlayan arabirimi.</span><span class="sxs-lookup"><span data-stu-id="f8130-120">The generated client contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>

   [!code-csharp[C_HowTo_UseReliableSession#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1221)]

1. <span data-ttu-id="f8130-121">Oluşturulan istemci uygulaması da uyarlamasını içeren `ClientCalculator`.</span><span class="sxs-lookup"><span data-stu-id="f8130-121">The generated client application also contains the implementation of the `ClientCalculator`.</span></span> <span data-ttu-id="f8130-122">Adres ve bağlama bilgilerini hizmet uygulaması içinde herhangi bir yere belirlenmezse unutmayın.</span><span class="sxs-lookup"><span data-stu-id="f8130-122">Note that the address and binding information isn't specified anywhere inside the implementation of the service.</span></span> <span data-ttu-id="f8130-123">Yapılandırma dosyasından adresi veya bağlama bilgileri bilgileri almak üzere kod yazmak için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="f8130-123">You aren't required to write code to retrieve the address or binding information information from the configuration file.</span></span>

   [!code-csharp[C_HowTo_UseReliableSession#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1222)]

1. <span data-ttu-id="f8130-124">*Svcutil.exe* ayrıca kullanan istemci yapılandırması oluşturur <xref:System.ServiceModel.WSHttpBinding> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f8130-124">*Svcutil.exe* also generates the configuration for the client that uses the <xref:System.ServiceModel.WSHttpBinding> class.</span></span> <span data-ttu-id="f8130-125">Yapılandırma dosyası adı *App.config* kullanırken [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f8130-125">Name the configuration file *App.config* when using [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].</span></span>

   [!code-xml[C_HowTo_UseReliableSession#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/app.config#2211)]

1. <span data-ttu-id="f8130-126">Bir örneğini oluşturmak `ClientCalculator` bir uygulamada ve hizmet işlemlerini çağırma.</span><span class="sxs-lookup"><span data-stu-id="f8130-126">Create an instance of the `ClientCalculator` in an application and call the service operations.</span></span>

   [!code-csharp[C_HowTo_UseReliableSession#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1223)]

1. <span data-ttu-id="f8130-127">Derleme ve istemci çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="f8130-127">Compile and run the client.</span></span>

## <a name="example"></a><span data-ttu-id="f8130-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="f8130-128">Example</span></span>

<span data-ttu-id="f8130-129">Sistem tarafından sağlanan bağlamalar çeşitli güvenilir oturumlar varsayılan olarak destekler.</span><span class="sxs-lookup"><span data-stu-id="f8130-129">Several of the system-provided bindings support reliable sessions by default.</span></span> <span data-ttu-id="f8130-130">Bu güncelleştirmeler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="f8130-130">These include:</span></span>

- <xref:System.ServiceModel.WSDualHttpBinding>

- <xref:System.ServiceModel.NetNamedPipeBinding>

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>

<span data-ttu-id="f8130-131">Güvenilir oturumlar destekleyen özel bağlama oluşturma örneği için bkz: [nasıl yapılır: HTTPS ile özel bir güvenilir oturum bağlama oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md).</span><span class="sxs-lookup"><span data-stu-id="f8130-131">For an example of how to create a custom binding that supports reliable sessions, see [How to: Create a Custom Reliable Session Binding with HTTPS](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f8130-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f8130-132">See also</span></span>

[<span data-ttu-id="f8130-133">Güvenilir oturumlar</span><span class="sxs-lookup"><span data-stu-id="f8130-133">Reliable Sessions</span></span>](../../../../docs/framework/wcf/feature-details/reliable-sessions.md)
