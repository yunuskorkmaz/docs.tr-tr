---
title: 'Nasıl yapılır: Güvenilir Bir Oturumda İleti Alma ve Gönderme'
ms.date: 03/30/2017
ms.assetid: 87cd0e75-dd2c-44c1-8da0-7b494bbdeaea
ms.openlocfilehash: 97371f8572d5d0db633ab8dd1ca82067d9d55c3f
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90550195"
---
# <a name="how-to-exchange-messages-within-a-reliable-session"></a><span data-ttu-id="f199d-102">Nasıl yapılır: Güvenilir Bir Oturumda İleti Alma ve Gönderme</span><span class="sxs-lookup"><span data-stu-id="f199d-102">How to: Exchange Messages Within a Reliable Session</span></span>

<span data-ttu-id="f199d-103">Bu konu, bu tür bir oturumu destekleyen ancak varsayılan olarak değil, sistem tarafından belirtilen bağlamalardan birini kullanarak güvenilir bir oturumu etkinleştirmek için gereken adımları açıklar.</span><span class="sxs-lookup"><span data-stu-id="f199d-103">This topic outlines the steps required to enable a reliable session using one of the system-provided bindings that support such a session, but not by default.</span></span> <span data-ttu-id="f199d-104">Yapılandırma dosyanızda kod kullanarak veya bildirimli olarak güvenilir bir oturum imperatively etkinleştirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f199d-104">You enable a reliable session imperatively using code or declaratively in your configuration file.</span></span> <span data-ttu-id="f199d-105">Bu yordam, güvenilir oturumu etkinleştirmek ve iletilerin gönderildikleri sırada gelmesi için istemci ve hizmet yapılandırma dosyalarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="f199d-105">This procedure uses the client and service configuration files to enable the reliable session and to stipulate that the messages arrive in the same order in which they were sent.</span></span>

<span data-ttu-id="f199d-106">Bu yordamın anahtar bölümü, uç nokta yapılandırma öğesinin `bindingConfiguration` adlı bir bağlama yapılandırmasına başvuran bir özniteliği içermesi olur `Binding1` .</span><span class="sxs-lookup"><span data-stu-id="f199d-106">The key part of this procedure is that the endpoint configuration element contain a `bindingConfiguration` attribute that references a binding configuration named `Binding1`.</span></span> <span data-ttu-id="f199d-107">[**\<binding>**](../../configure-apps/file-schema/wcf/bindings.md)Yapılandırma öğesi, `enabled` öğesinin özniteliğini olarak ayarlayarak güvenilir oturumları etkinleştirmek için bu ada başvurur [**\<reliableSession>**](/previous-versions/dotnet/netframework-4.0/ms731302(v=vs.100)) `true` .</span><span class="sxs-lookup"><span data-stu-id="f199d-107">The [**\<binding>**](../../configure-apps/file-schema/wcf/bindings.md) configuration element references this name to enable reliable sessions by setting the `enabled` attribute of the [**\<reliableSession>**](/previous-versions/dotnet/netframework-4.0/ms731302(v=vs.100)) element to `true`.</span></span> <span data-ttu-id="f199d-108">Özniteliğini olarak ayarlayarak güvenilir oturum için sıralı teslim bildirimlerini belirtirsiniz `ordered` `true` .</span><span class="sxs-lookup"><span data-stu-id="f199d-108">You specify the ordered delivery assurances for the reliable session by setting the `ordered` attribute to `true`.</span></span>

<span data-ttu-id="f199d-109">Bu örneğin kaynak kopyası için bkz. [WS güvenilir oturumu](../samples/ws-reliable-session.md).</span><span class="sxs-lookup"><span data-stu-id="f199d-109">For the source copy of this example, see [WS Reliable Session](../samples/ws-reliable-session.md).</span></span>

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="f199d-110">Güvenli bir oturum kullanmak için bir WSHttpBinding ile hizmeti yapılandırma</span><span class="sxs-lookup"><span data-stu-id="f199d-110">Configure the service with a WSHttpBinding to use a reliable session</span></span>

1. <span data-ttu-id="f199d-111">Hizmet türü için bir hizmet sözleşmesi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="f199d-111">Define a service contract for the type of service.</span></span>

   [!code-csharp[c_HowTo_UseReliableSession#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1121)]

1. <span data-ttu-id="f199d-112">Hizmet sözleşmesini bir hizmet sınıfına uygulayın.</span><span class="sxs-lookup"><span data-stu-id="f199d-112">Implement the service contract in a service class.</span></span> <span data-ttu-id="f199d-113">Adresin veya bağlama bilgilerinin hizmet uygulamasının içinde belirtilmediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="f199d-113">Note that the address or binding information isn't specified inside the implementation of the service.</span></span> <span data-ttu-id="f199d-114">Yapılandırma dosyasından adresi veya bağlama bilgilerini almak için kod yazmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="f199d-114">You aren't required to write code to retrieve the address or binding information from the configuration file.</span></span>

   [!code-csharp[c_HowTo_UseReliableSession#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1122)]

1. <span data-ttu-id="f199d-115">*Web.config* `CalculatorService` <xref:System.ServiceModel.WSHttpBinding> Güvenilir oturum etkin ve gereken iletilerin sıralı teslimini kullanan, için bir uç nokta yapılandırmak üzere birWeb.configdosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f199d-115">Create a *Web.config* file to configure an endpoint for the `CalculatorService` that uses the <xref:System.ServiceModel.WSHttpBinding> with reliable session enabled and ordered delivery of messages required.</span></span>

   [!code-xml[c_HowTo_UseReliableSession#2111](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/web.config#2111)]

1. <span data-ttu-id="f199d-116">Satırı içeren bir *Service. svc* dosyası oluşturun:</span><span class="sxs-lookup"><span data-stu-id="f199d-116">Create a *Service.svc* file that contains the line:</span></span>

   ```aspx-csharp
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```

1. <span data-ttu-id="f199d-117">*Service. svc* dosyasını Internet INFORMATION SERVICES (IIS) sanal dizinine yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="f199d-117">Place the *Service.svc* file in your Internet Information Services (IIS) virtual directory.</span></span>

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="f199d-118">Güvenli bir oturum kullanmak için istemciyi bir WSHttpBinding ile yapılandırma</span><span class="sxs-lookup"><span data-stu-id="f199d-118">Configure the client with a WSHttpBinding to use a reliable session</span></span>

1. <span data-ttu-id="f199d-119">Hizmet meta verilerinden kod oluşturmak için, komut satırından [ServiceModel meta veri yardımcı programı aracını (*Svcutil.exe*)](../servicemodel-metadata-utility-tool-svcutil-exe.md) kullanın:</span><span class="sxs-lookup"><span data-stu-id="f199d-119">Use the [ServiceModel Metadata Utility Tool (*Svcutil.exe*)](../servicemodel-metadata-utility-tool-svcutil-exe.md) from the command line to generate code from service metadata:</span></span>

   ```console
   Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
   ```

1. <span data-ttu-id="f199d-120">Oluşturulan istemci, `ICalculator` istemci uygulamasının karşılaması gereken hizmet sözleşmesini tanımlayan arabirimi içerir.</span><span class="sxs-lookup"><span data-stu-id="f199d-120">The generated client contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>

   [!code-csharp[C_HowTo_UseReliableSession#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1221)]

1. <span data-ttu-id="f199d-121">Oluşturulan istemci uygulaması, uygulamasının uygulamasını da içerir `ClientCalculator` .</span><span class="sxs-lookup"><span data-stu-id="f199d-121">The generated client application also contains the implementation of the `ClientCalculator`.</span></span> <span data-ttu-id="f199d-122">Adres ve bağlama bilgilerinin, hizmet uygulamasının içinde herhangi bir yerde belirtilmediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="f199d-122">Note that the address and binding information isn't specified anywhere inside the implementation of the service.</span></span> <span data-ttu-id="f199d-123">Yapılandırma dosyasından adresi veya bağlama bilgilerini almak için kod yazmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="f199d-123">You aren't required to write code to retrieve the address or binding information from the configuration file.</span></span>

   [!code-csharp[C_HowTo_UseReliableSession#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1222)]

1. <span data-ttu-id="f199d-124">*Svcutil.exe* Ayrıca, sınıfını kullanan istemcinin yapılandırmasını da oluşturur <xref:System.ServiceModel.WSHttpBinding> .</span><span class="sxs-lookup"><span data-stu-id="f199d-124">*Svcutil.exe* also generates the configuration for the client that uses the <xref:System.ServiceModel.WSHttpBinding> class.</span></span> <span data-ttu-id="f199d-125">Visual Studio kullanırken yapılandırma dosyası *App.config* adlandırın.</span><span class="sxs-lookup"><span data-stu-id="f199d-125">Name the configuration file *App.config* when using Visual Studio.</span></span>

   [!code-xml[C_HowTo_UseReliableSession#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/app.config#2211)]

1. <span data-ttu-id="f199d-126">Uygulamasının bir örneğini oluşturun `ClientCalculator` ve hizmet işlemlerini çağırın.</span><span class="sxs-lookup"><span data-stu-id="f199d-126">Create an instance of the `ClientCalculator` in an application and call the service operations.</span></span>

   [!code-csharp[C_HowTo_UseReliableSession#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1223)]

1. <span data-ttu-id="f199d-127">İstemcisini derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="f199d-127">Compile and run the client.</span></span>

## <a name="example"></a><span data-ttu-id="f199d-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="f199d-128">Example</span></span>

<span data-ttu-id="f199d-129">Sistem tarafından sunulan bağlamalardan bazıları varsayılan olarak güvenilir oturumları destekler.</span><span class="sxs-lookup"><span data-stu-id="f199d-129">Several of the system-provided bindings support reliable sessions by default.</span></span> <span data-ttu-id="f199d-130">Bu güncelleştirmeler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="f199d-130">These include:</span></span>

- <xref:System.ServiceModel.WSDualHttpBinding>

- <xref:System.ServiceModel.NetNamedPipeBinding>

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>

<span data-ttu-id="f199d-131">Güvenilir oturumları destekleyen özel bir bağlamanın nasıl oluşturulacağı hakkında bir örnek için bkz. [nasıl yapılır: https Ile özel bir güvenilir oturum bağlama oluşturma](how-to-create-a-custom-reliable-session-binding-with-https.md).</span><span class="sxs-lookup"><span data-stu-id="f199d-131">For an example of how to create a custom binding that supports reliable sessions, see [How to: Create a Custom Reliable Session Binding with HTTPS](how-to-create-a-custom-reliable-session-binding-with-https.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f199d-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f199d-132">See also</span></span>

- [<span data-ttu-id="f199d-133">Güvenilir oturumlar</span><span class="sxs-lookup"><span data-stu-id="f199d-133">Reliable Sessions</span></span>](reliable-sessions.md)
