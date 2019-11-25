---
title: 'Nasıl yapılır: Güvenilir Bir Oturumda İleti Alma ve Gönderme'
ms.date: 03/30/2017
ms.assetid: 87cd0e75-dd2c-44c1-8da0-7b494bbdeaea
ms.openlocfilehash: 58a392fc6295e82f41e08c80a3343b4059afad7e
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141684"
---
# <a name="how-to-exchange-messages-within-a-reliable-session"></a><span data-ttu-id="eed5c-102">Nasıl yapılır: Güvenilir Bir Oturumda İleti Alma ve Gönderme</span><span class="sxs-lookup"><span data-stu-id="eed5c-102">How to: Exchange Messages Within a Reliable Session</span></span>

<span data-ttu-id="eed5c-103">Bu konu, bu tür bir oturumu destekleyen ancak varsayılan olarak değil, sistem tarafından belirtilen bağlamalardan birini kullanarak güvenilir bir oturumu etkinleştirmek için gereken adımları açıklar.</span><span class="sxs-lookup"><span data-stu-id="eed5c-103">This topic outlines the steps required to enable a reliable session using one of the system-provided bindings that support such a session, but not by default.</span></span> <span data-ttu-id="eed5c-104">Yapılandırma dosyanızda kod kullanarak veya bildirimli olarak güvenilir bir oturum imperatively etkinleştirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eed5c-104">You enable a reliable session imperatively using code or declaratively in your configuration file.</span></span> <span data-ttu-id="eed5c-105">Bu yordam, güvenilir oturumu etkinleştirmek ve iletilerin gönderildikleri sırada gelmesi için istemci ve hizmet yapılandırma dosyalarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="eed5c-105">This procedure uses the client and service configuration files to enable the reliable session and to stipulate that the messages arrive in the same order in which they were sent.</span></span>

<span data-ttu-id="eed5c-106">Bu yordamın anahtar bölümü, uç nokta yapılandırma öğesinin `Binding1`adlı bağlama yapılandırmasına başvuran bir `bindingConfiguration` özniteliği içermisimdir.</span><span class="sxs-lookup"><span data-stu-id="eed5c-106">The key part of this procedure is that the endpoint configuration element contain a `bindingConfiguration` attribute that references a binding configuration named `Binding1`.</span></span> <span data-ttu-id="eed5c-107">[ **\<binding >** ](../../configure-apps/file-schema/wcf/bindings.md) yapılandırma öğesi, [ **\<reliablesession >** ](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731302(v=vs.100)) öğesinin `enabled` özniteliğini `true`olarak ayarlayarak güvenilir oturumları etkinleştirmek için bu ada başvurur.</span><span class="sxs-lookup"><span data-stu-id="eed5c-107">The [**\<binding>**](../../configure-apps/file-schema/wcf/bindings.md) configuration element references this name to enable reliable sessions by setting the `enabled` attribute of the [**\<reliableSession>**](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731302(v=vs.100)) element to `true`.</span></span> <span data-ttu-id="eed5c-108">`ordered` özniteliğini `true`olarak ayarlayarak güvenilir oturum için sıralı teslim bildirimlerini belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eed5c-108">You specify the ordered delivery assurances for the reliable session by setting the `ordered` attribute to `true`.</span></span>

<span data-ttu-id="eed5c-109">Bu örneğin kaynak kopyası için bkz. [WS güvenilir oturumu](../../../../docs/framework/wcf/samples/ws-reliable-session.md).</span><span class="sxs-lookup"><span data-stu-id="eed5c-109">For the source copy of this example, see [WS Reliable Session](../../../../docs/framework/wcf/samples/ws-reliable-session.md).</span></span>

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="eed5c-110">Güvenli bir oturum kullanmak için bir WSHttpBinding ile hizmeti yapılandırma</span><span class="sxs-lookup"><span data-stu-id="eed5c-110">Configure the service with a WSHttpBinding to use a reliable session</span></span>

1. <span data-ttu-id="eed5c-111">Hizmet türü için bir hizmet sözleşmesi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="eed5c-111">Define a service contract for the type of service.</span></span>

   [!code-csharp[c_HowTo_UseReliableSession#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1121)]

1. <span data-ttu-id="eed5c-112">Hizmet sözleşmesini bir hizmet sınıfına uygulayın.</span><span class="sxs-lookup"><span data-stu-id="eed5c-112">Implement the service contract in a service class.</span></span> <span data-ttu-id="eed5c-113">Adresin veya bağlama bilgilerinin hizmet uygulamasının içinde belirtilmediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="eed5c-113">Note that the address or binding information isn't specified inside the implementation of the service.</span></span> <span data-ttu-id="eed5c-114">Yapılandırma dosyasından adresi veya bağlama bilgilerini almak için kod yazmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="eed5c-114">You aren't required to write code to retrieve the address or binding information from the configuration file.</span></span>

   [!code-csharp[c_HowTo_UseReliableSession#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1122)]

1. <span data-ttu-id="eed5c-115">Güvenilir oturum etkinken <xref:System.ServiceModel.WSHttpBinding> kullanan `CalculatorService` için bir uç nokta yapılandırmak üzere bir *Web. config* dosyası oluşturun ve gerekli iletilerin sıralı teslimini yapın.</span><span class="sxs-lookup"><span data-stu-id="eed5c-115">Create a *Web.config* file to configure an endpoint for the `CalculatorService` that uses the <xref:System.ServiceModel.WSHttpBinding> with reliable session enabled and ordered delivery of messages required.</span></span>

   [!code-xml[c_HowTo_UseReliableSession#2111](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/web.config#2111)]

1. <span data-ttu-id="eed5c-116">Satırı içeren bir *Service. svc* dosyası oluşturun:</span><span class="sxs-lookup"><span data-stu-id="eed5c-116">Create a *Service.svc* file that contains the line:</span></span>

   ```
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```

1. <span data-ttu-id="eed5c-117">*Service. svc* dosyasını Internet INFORMATION SERVICES (IIS) sanal dizinine yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="eed5c-117">Place the *Service.svc* file in your Internet Information Services (IIS) virtual directory.</span></span>

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="eed5c-118">Güvenli bir oturum kullanmak için istemciyi bir WSHttpBinding ile yapılandırma</span><span class="sxs-lookup"><span data-stu-id="eed5c-118">Configure the client with a WSHttpBinding to use a reliable session</span></span>

1. <span data-ttu-id="eed5c-119">Hizmet meta verilerinden kod oluşturmak için, komut satırından [ServiceModel meta veri yardımcı programı aracını (*Svcutil. exe*)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) kullanın:</span><span class="sxs-lookup"><span data-stu-id="eed5c-119">Use the [ServiceModel Metadata Utility Tool (*Svcutil.exe*)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) from the command line to generate code from service metadata:</span></span>

   ```console
   Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
   ```

1. <span data-ttu-id="eed5c-120">Oluşturulan istemci, istemci uygulamasının karşılaması gereken hizmet sözleşmesini tanımlayan `ICalculator` arabirimini içerir.</span><span class="sxs-lookup"><span data-stu-id="eed5c-120">The generated client contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>

   [!code-csharp[C_HowTo_UseReliableSession#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1221)]

1. <span data-ttu-id="eed5c-121">Oluşturulan istemci uygulaması, `ClientCalculator`uygulamasını da içerir.</span><span class="sxs-lookup"><span data-stu-id="eed5c-121">The generated client application also contains the implementation of the `ClientCalculator`.</span></span> <span data-ttu-id="eed5c-122">Adres ve bağlama bilgilerinin, hizmet uygulamasının içinde herhangi bir yerde belirtilmediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="eed5c-122">Note that the address and binding information isn't specified anywhere inside the implementation of the service.</span></span> <span data-ttu-id="eed5c-123">Yapılandırma dosyasından adresi veya bağlama bilgilerini almak için kod yazmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="eed5c-123">You aren't required to write code to retrieve the address or binding information from the configuration file.</span></span>

   [!code-csharp[C_HowTo_UseReliableSession#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1222)]

1. <span data-ttu-id="eed5c-124">*Svcutil. exe* , <xref:System.ServiceModel.WSHttpBinding> sınıfını kullanan istemcinin yapılandırmasını da oluşturur.</span><span class="sxs-lookup"><span data-stu-id="eed5c-124">*Svcutil.exe* also generates the configuration for the client that uses the <xref:System.ServiceModel.WSHttpBinding> class.</span></span> <span data-ttu-id="eed5c-125">Visual Studio kullanırken yapılandırma dosyasını *app. config* olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="eed5c-125">Name the configuration file *App.config* when using Visual Studio.</span></span>

   [!code-xml[C_HowTo_UseReliableSession#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/app.config#2211)]

1. <span data-ttu-id="eed5c-126">Bir uygulamada `ClientCalculator` örneği oluşturun ve hizmet işlemlerini çağırın.</span><span class="sxs-lookup"><span data-stu-id="eed5c-126">Create an instance of the `ClientCalculator` in an application and call the service operations.</span></span>

   [!code-csharp[C_HowTo_UseReliableSession#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1223)]

1. <span data-ttu-id="eed5c-127">İstemcisini derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="eed5c-127">Compile and run the client.</span></span>

## <a name="example"></a><span data-ttu-id="eed5c-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="eed5c-128">Example</span></span>

<span data-ttu-id="eed5c-129">Sistem tarafından sunulan bağlamalardan bazıları varsayılan olarak güvenilir oturumları destekler.</span><span class="sxs-lookup"><span data-stu-id="eed5c-129">Several of the system-provided bindings support reliable sessions by default.</span></span> <span data-ttu-id="eed5c-130">Bu güncelleştirmeler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="eed5c-130">These include:</span></span>

- <xref:System.ServiceModel.WSDualHttpBinding>

- <xref:System.ServiceModel.NetNamedPipeBinding>

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>

<span data-ttu-id="eed5c-131">Güvenilir oturumları destekleyen özel bir bağlamanın nasıl oluşturulacağı hakkında bir örnek için bkz. [nasıl yapılır: https Ile özel bir güvenilir oturum bağlama oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md).</span><span class="sxs-lookup"><span data-stu-id="eed5c-131">For an example of how to create a custom binding that supports reliable sessions, see [How to: Create a Custom Reliable Session Binding with HTTPS](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="eed5c-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eed5c-132">See also</span></span>

- [<span data-ttu-id="eed5c-133">Güvenilir Oturumlar</span><span class="sxs-lookup"><span data-stu-id="eed5c-133">Reliable Sessions</span></span>](../../../../docs/framework/wcf/feature-details/reliable-sessions.md)
