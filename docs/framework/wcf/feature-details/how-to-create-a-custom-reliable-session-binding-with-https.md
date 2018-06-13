---
title: 'Nasıl yapılır: HTTPS ile Özel Bir Güvenilir Oturum Bağlama Oluşturma'
ms.date: 03/30/2017
ms.assetid: fa772232-da1f-4c66-8c94-e36c0584b549
ms.openlocfilehash: b3699593f783fff1227ec51194956e0cc8577dd8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33492768"
---
# <a name="how-to-create-a-custom-reliable-session-binding-with-https"></a><span data-ttu-id="5ef28-102">Nasıl yapılır: HTTPS ile Özel Bir Güvenilir Oturum Bağlama Oluşturma</span><span class="sxs-lookup"><span data-stu-id="5ef28-102">How to: Create a Custom Reliable Session Binding with HTTPS</span></span>

<span data-ttu-id="5ef28-103">Bu konu, Güvenli Yuva Katmanı (SSL) güvenilir oturumlar ile taşıma güvenliği kullanımını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="5ef28-103">This topic demonstrates the use of Secure Sockets Layer (SSL) transport security with reliable sessions.</span></span> <span data-ttu-id="5ef28-104">HTTPS üzerinden güvenli bir oturum kullanmak için güvenilir bir oturum ve HTTPS taşıması kullanan özel bağlama oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5ef28-104">To use a reliable session over HTTPS, you must create a custom binding that uses a reliable session and the HTTPS transport.</span></span> <span data-ttu-id="5ef28-105">Güvenilir oturum kodu kullanarak imperatively ya da bildirimli olarak yapılandırma dosyasında etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="5ef28-105">You enable the reliable session either imperatively by using code or declaratively in the configuration file.</span></span> <span data-ttu-id="5ef28-106">Güvenilir oturum etkinleştirmek için bu yordam istemci ve hizmet yapılandırma dosyalarını kullanır ve [  **\<httpsTransport >** ](../../../../docs/framework/configure-apps/file-schema/wcf/httpstransport.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="5ef28-106">This procedure uses the client and service configuration files to enable the reliable session and the [**\<httpsTransport>**](../../../../docs/framework/configure-apps/file-schema/wcf/httpstransport.md) element.</span></span>

<span data-ttu-id="5ef28-107">Bu yordam önemli bir parçası olan  **\<uç noktası >** yapılandırma öğesi içeren bir `bindingConfiguration` adlı bir özel bağlama yapılandırma başvuran özniteliği `reliableSessionOverHttps`.</span><span class="sxs-lookup"><span data-stu-id="5ef28-107">The key part of this procedure is that the **\<endpoint>** configuration element contain a `bindingConfiguration` attribute that references a custom binding configuration named `reliableSessionOverHttps`.</span></span> <span data-ttu-id="5ef28-108">[  **\<Bağlama >** ](../../../../docs/framework/misc/binding.md) yapılandırma öğesine başvuruyor ekleyerek bir güvenilir oturum ve HTTPS taşıma kullanılan belirtmek için bu ad  **\< reliableSession >** ve  **\<httpsTransport >** öğeleri.</span><span class="sxs-lookup"><span data-stu-id="5ef28-108">The [**\<binding>**](../../../../docs/framework/misc/binding.md) configuration element references this name to specify that a reliable session and the HTTPS transport are used by including **\<reliableSession>** and **\<httpsTransport>** elements.</span></span>

<span data-ttu-id="5ef28-109">Bu örnekte kaynak kopyası için bkz: [özel bağlama güvenilir oturum HTTPS üzerinden](../../../../docs/framework/wcf/samples/custom-binding-reliable-session-over-https.md).</span><span class="sxs-lookup"><span data-stu-id="5ef28-109">For the source copy of this example, see [Custom Binding Reliable Session over HTTPS](../../../../docs/framework/wcf/samples/custom-binding-reliable-session-over-https.md).</span></span>

### <a name="configure-the-service-with-a-custombinding-to-use-a-reliable-session-with-https"></a><span data-ttu-id="5ef28-110">Güvenilir bir oturum ile HTTPS kullanmak üzere bir CustomBinding ile hizmetini yapılandırma</span><span class="sxs-lookup"><span data-stu-id="5ef28-110">Configure the service with a CustomBinding to use a reliable session with HTTPS</span></span>

1. <span data-ttu-id="5ef28-111">Hizmet türü için bir hizmet sözleşmesini tanımlama.</span><span class="sxs-lookup"><span data-stu-id="5ef28-111">Define a service contract for the type of service.</span></span>

   [!code-csharp[c_HowTo_CreateReliableSessionHTTPS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/service.cs#1121)]

1. <span data-ttu-id="5ef28-112">Bir hizmet sınıfında Hizmet sözleşmesini uygulama.</span><span class="sxs-lookup"><span data-stu-id="5ef28-112">Implement the service contract in a service class.</span></span> <span data-ttu-id="5ef28-113">Adres veya bağlama bilgisi hizmet uygulaması içinde belirlenmezse unutmayın.</span><span class="sxs-lookup"><span data-stu-id="5ef28-113">Note that the address or binding information isn't specified inside the implementation of the service.</span></span> <span data-ttu-id="5ef28-114">Yapılandırma dosyasından adresi veya bağlama bilgilerini almak üzere kod yazmak için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="5ef28-114">You aren't required to write code to retrieve the address or binding information from the configuration file.</span></span>

   [!code-csharp[c_HowTo_CreateReliableSessionHTTPS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/service.cs#1122)]

1. <span data-ttu-id="5ef28-115">Oluşturma bir *Web.config* için bir uç nokta yapılandırmak için bir dosya `CalculatorService` adlı özel bir bağlama ile `reliableSessionOverHttps` güvenilir bir oturum ve HTTPS aktarımı kullanır.</span><span class="sxs-lookup"><span data-stu-id="5ef28-115">Create a *Web.config* file to configure an endpoint for the `CalculatorService` with a custom binding named `reliableSessionOverHttps` that uses a reliable session and the HTTPS transport.</span></span>

   [!code-xml[c_HowTo_CreateReliableSessionHTTPS#2111](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/common/web.config#2111)]

1. <span data-ttu-id="5ef28-116">Oluşturma bir *Service.svc* bir çizgi içeren dosya:</span><span class="sxs-lookup"><span data-stu-id="5ef28-116">Create a *Service.svc* file that contains the line:</span></span>

   ```
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```

1. <span data-ttu-id="5ef28-117">Yer *Service.svc* , Internet Information Services (IIS) sanal dizinde dosya.</span><span class="sxs-lookup"><span data-stu-id="5ef28-117">Place the *Service.svc* file in your Internet Information Services (IIS) virtual directory.</span></span>

### <a name="configure-the-client-with-a-custombinding-to-use-a-reliable-session-with-https"></a><span data-ttu-id="5ef28-118">İstemci bir CustomBinding güvenilir bir oturum ile HTTPS kullanmak üzere yapılandırın</span><span class="sxs-lookup"><span data-stu-id="5ef28-118">Configure the client with a CustomBinding to use a reliable session with HTTPS</span></span>

1. <span data-ttu-id="5ef28-119">Kullanım [ServiceModel meta veri yardımcı Programracı (*Svcutil.exe*)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) hizmet meta verilerinden kodu oluşturmak için komut satırından.</span><span class="sxs-lookup"><span data-stu-id="5ef28-119">Use the [ServiceModel Metadata Utility Tool (*Svcutil.exe*)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) from the command line to generate code from service metadata.</span></span>

   ```console
   Svcutil.exe <Metadata Exchange (MEX) address or HTTP GET address>
   ```

1. <span data-ttu-id="5ef28-120">Oluşturulan istemci içeren `ICalculator` istemci uygulaması getirmelidir hizmet sözleşmesini tanımlayan arabirimi.</span><span class="sxs-lookup"><span data-stu-id="5ef28-120">The client that's generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1221)]

1. <span data-ttu-id="5ef28-121">Oluşturulan istemci uygulaması da uyarlamasını içeren `ClientCalculator`.</span><span class="sxs-lookup"><span data-stu-id="5ef28-121">The generated client application also contains the implementation of the `ClientCalculator`.</span></span> <span data-ttu-id="5ef28-122">Adres ve bağlama bilgilerini hizmet uygulaması içinde belirlenmezse unutmayın.</span><span class="sxs-lookup"><span data-stu-id="5ef28-122">Note that the address and binding information isn't specified inside the implementation of the service.</span></span> <span data-ttu-id="5ef28-123">Yapılandırma dosyasından adres ve bağlama bilgilerini almak üzere kod yazmak için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="5ef28-123">You aren't required to write code to retrieve the address and binding information from the configuration file.</span></span>

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1222)]

1. <span data-ttu-id="5ef28-124">Adlı özel bağlama yapılandırma `reliableSessionOverHttps` HTTPS taşıma ve güvenilir oturumlar kullanmak için.</span><span class="sxs-lookup"><span data-stu-id="5ef28-124">Configure a custom binding named `reliableSessionOverHttps` to use the HTTPS transport and reliable sessions.</span></span>

   [!code-xml[C_HowTo_CreateReliableSessionHTTPS#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/common/app.config#2211)]

1. <span data-ttu-id="5ef28-125">Bir örneğini oluşturmak `ClientCalculator` bir uygulamada ve hizmet işlemleri çağırın.</span><span class="sxs-lookup"><span data-stu-id="5ef28-125">Create an instance of the `ClientCalculator` in an application and then call the service operations.</span></span>

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1223)]

1. <span data-ttu-id="5ef28-126">Derleme ve istemci çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="5ef28-126">Compile and run the client.</span></span>  

## <a name="net-framework-security"></a><span data-ttu-id="5ef28-127">.NET Framework güvenliği</span><span class="sxs-lookup"><span data-stu-id="5ef28-127">.NET Framework security</span></span>

<span data-ttu-id="5ef28-128">Bu örnekte kullanılan sertifika ile oluşturulan bir test sertifikası olduğundan *Makecert.exe*, bir HTTPS adresi gibi erişmeye çalıştığınızda bir güvenlik uyarısı görünür `https://localhost/servicemodelsamples/service.svc`, tarayıcınızdan.</span><span class="sxs-lookup"><span data-stu-id="5ef28-128">Because the certificate used in this sample is a test certificate created with *Makecert.exe*, a security alert appears when you try to access an HTTPS address, such as `https://localhost/servicemodelsamples/service.svc`, from your browser.</span></span>

## <a name="see-also"></a><span data-ttu-id="5ef28-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5ef28-129">See also</span></span>

[<span data-ttu-id="5ef28-130">Güvenilir Oturumlar</span><span class="sxs-lookup"><span data-stu-id="5ef28-130">Reliable Sessions</span></span>](../../../../docs/framework/wcf/feature-details/reliable-sessions.md)
