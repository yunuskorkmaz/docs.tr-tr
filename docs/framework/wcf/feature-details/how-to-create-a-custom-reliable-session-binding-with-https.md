---
title: 'Nasıl yapılır: HTTPS ile Özel Bir Güvenilir Oturum Bağlama Oluşturma'
ms.date: 03/30/2017
ms.assetid: fa772232-da1f-4c66-8c94-e36c0584b549
ms.openlocfilehash: 7f22eeaae39b4d9a83c77c7f3e9db1d7d3f04e8e
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70895193"
---
# <a name="how-to-create-a-custom-reliable-session-binding-with-https"></a><span data-ttu-id="9953e-102">Nasıl yapılır: HTTPS ile Özel Bir Güvenilir Oturum Bağlama Oluşturma</span><span class="sxs-lookup"><span data-stu-id="9953e-102">How to: Create a Custom Reliable Session Binding with HTTPS</span></span>

<span data-ttu-id="9953e-103">Bu konu, güvenilir oturumlarla Güvenli Yuva Katmanı (SSL) aktarım güvenliği kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9953e-103">This topic demonstrates the use of Secure Sockets Layer (SSL) transport security with reliable sessions.</span></span> <span data-ttu-id="9953e-104">HTTPS üzerinden güvenilir bir oturum kullanmak için güvenilir bir oturum ve HTTPS taşıması kullanan özel bir bağlama oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9953e-104">To use a reliable session over HTTPS, you must create a custom binding that uses a reliable session and the HTTPS transport.</span></span> <span data-ttu-id="9953e-105">Yapılandırma dosyasında kod kullanarak veya bildirimli olarak güvenilir oturumu imperatively etkinleştirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9953e-105">You enable the reliable session either imperatively by using code or declaratively in the configuration file.</span></span> <span data-ttu-id="9953e-106">Bu yordam, güvenilir oturumu ve [ **\<httpsTransport >** ](../../../../docs/framework/configure-apps/file-schema/wcf/httpstransport.md) öğesini etkinleştirmek için istemci ve hizmet yapılandırma dosyalarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="9953e-106">This procedure uses the client and service configuration files to enable the reliable session and the [**\<httpsTransport>**](../../../../docs/framework/configure-apps/file-schema/wcf/httpstransport.md) element.</span></span>

<span data-ttu-id="9953e-107">Bu yordamın `bindingConfiguration` `reliableSessionOverHttps`  **\<anahtar bölümü, uç nokta >** yapılandırma öğesinin adlı bir özel bağlama yapılandırmasına başvuran bir özniteliği içerecekse.</span><span class="sxs-lookup"><span data-stu-id="9953e-107">The key part of this procedure is that the **\<endpoint>** configuration element contain a `bindingConfiguration` attribute that references a custom binding configuration named `reliableSessionOverHttps`.</span></span> <span data-ttu-id="9953e-108">[ **\<Bağlama >** ](../../../../docs/framework/misc/binding.md) yapılandırma öğesi,  **\<reliableoturum >** ve **\<httpsTransport dahil, güvenilir bir oturumun ve https taşımanın kullanıldığını belirtmek için bu ada başvurur >** öğeleri.</span><span class="sxs-lookup"><span data-stu-id="9953e-108">The [**\<binding>**](../../../../docs/framework/misc/binding.md) configuration element references this name to specify that a reliable session and the HTTPS transport are used by including **\<reliableSession>** and **\<httpsTransport>** elements.</span></span>

<span data-ttu-id="9953e-109">Bu örneğin kaynak kopyası için bkz. [https üzerinden özel bağlama güvenilir oturumu](../../../../docs/framework/wcf/samples/custom-binding-reliable-session-over-https.md).</span><span class="sxs-lookup"><span data-stu-id="9953e-109">For the source copy of this example, see [Custom Binding Reliable Session over HTTPS](../../../../docs/framework/wcf/samples/custom-binding-reliable-session-over-https.md).</span></span>

### <a name="configure-the-service-with-a-custombinding-to-use-a-reliable-session-with-https"></a><span data-ttu-id="9953e-110">HTTPS ile güvenilir bir oturum kullanmak için hizmeti bir CustomBinding ile yapılandırma</span><span class="sxs-lookup"><span data-stu-id="9953e-110">Configure the service with a CustomBinding to use a reliable session with HTTPS</span></span>

1. <span data-ttu-id="9953e-111">Hizmet türü için bir hizmet sözleşmesi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="9953e-111">Define a service contract for the type of service.</span></span>

   [!code-csharp[c_HowTo_CreateReliableSessionHTTPS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/service.cs#1121)]

1. <span data-ttu-id="9953e-112">Hizmet sözleşmesini bir hizmet sınıfına uygulayın.</span><span class="sxs-lookup"><span data-stu-id="9953e-112">Implement the service contract in a service class.</span></span> <span data-ttu-id="9953e-113">Adresin veya bağlama bilgilerinin hizmet uygulamasının içinde belirtilmediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="9953e-113">Note that the address or binding information isn't specified inside the implementation of the service.</span></span> <span data-ttu-id="9953e-114">Yapılandırma dosyasından adresi veya bağlama bilgilerini almak için kod yazmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="9953e-114">You aren't required to write code to retrieve the address or binding information from the configuration file.</span></span>

   [!code-csharp[c_HowTo_CreateReliableSessionHTTPS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/service.cs#1122)]

1. <span data-ttu-id="9953e-115">Güvenli bir oturum ve HTTPS taşıması kullanan adlı `reliableSessionOverHttps` özel bir bağlama `CalculatorService` ile için bir uç nokta yapılandırmak üzere bir *Web. config* dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9953e-115">Create a *Web.config* file to configure an endpoint for the `CalculatorService` with a custom binding named `reliableSessionOverHttps` that uses a reliable session and the HTTPS transport.</span></span>

   [!code-xml[c_HowTo_CreateReliableSessionHTTPS#2111](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/common/web.config#2111)]

1. <span data-ttu-id="9953e-116">Satırı içeren bir *Service. svc* dosyası oluşturun:</span><span class="sxs-lookup"><span data-stu-id="9953e-116">Create a *Service.svc* file that contains the line:</span></span>

   `<%@ServiceHost language=c# Service="CalculatorService" %>`

1. <span data-ttu-id="9953e-117">*Service. svc* dosyasını Internet INFORMATION SERVICES (IIS) sanal dizinine yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="9953e-117">Place the *Service.svc* file in your Internet Information Services (IIS) virtual directory.</span></span>

### <a name="configure-the-client-with-a-custombinding-to-use-a-reliable-session-with-https"></a><span data-ttu-id="9953e-118">HTTPS ile güvenilir bir oturum kullanmak için istemciyi bir CustomBinding ile yapılandırma</span><span class="sxs-lookup"><span data-stu-id="9953e-118">Configure the client with a CustomBinding to use a reliable session with HTTPS</span></span>

1. <span data-ttu-id="9953e-119">Hizmet meta verilerinden kod oluşturmak için, komut satırından [ServiceModel meta veri yardımcı programı aracını (*Svcutil. exe*)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="9953e-119">Use the [ServiceModel Metadata Utility Tool (*Svcutil.exe*)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) from the command line to generate code from service metadata.</span></span>

   ```console
   Svcutil.exe <Metadata Exchange (MEX) address or HTTP GET address>
   ```

1. <span data-ttu-id="9953e-120">Oluşturulan istemci, istemci uygulamasının karşılaması gereken `ICalculator` hizmet sözleşmesini tanımlayan arabirimi içerir.</span><span class="sxs-lookup"><span data-stu-id="9953e-120">The client that's generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1221)]

1. <span data-ttu-id="9953e-121">Oluşturulan istemci uygulaması, `ClientCalculator`uygulamasının uygulamasını da içerir.</span><span class="sxs-lookup"><span data-stu-id="9953e-121">The generated client application also contains the implementation of the `ClientCalculator`.</span></span> <span data-ttu-id="9953e-122">Adres ve bağlama bilgilerinin hizmet uygulamasının içinde belirtilmediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="9953e-122">Note that the address and binding information isn't specified inside the implementation of the service.</span></span> <span data-ttu-id="9953e-123">Yapılandırma dosyasından adres ve bağlama bilgilerini almak için kod yazmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="9953e-123">You aren't required to write code to retrieve the address and binding information from the configuration file.</span></span>

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1222)]

1. <span data-ttu-id="9953e-124">HTTPS aktarımını ve güvenilir oturumları `reliableSessionOverHttps` kullanmak için adlı özel bir bağlama yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="9953e-124">Configure a custom binding named `reliableSessionOverHttps` to use the HTTPS transport and reliable sessions.</span></span>

   [!code-xml[C_HowTo_CreateReliableSessionHTTPS#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/common/app.config#2211)]

1. <span data-ttu-id="9953e-125">Uygulamasının bir örneğini `ClientCalculator` oluşturun ve ardından hizmet işlemlerini çağırın.</span><span class="sxs-lookup"><span data-stu-id="9953e-125">Create an instance of the `ClientCalculator` in an application and then call the service operations.</span></span>

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1223)]

1. <span data-ttu-id="9953e-126">İstemcisini derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9953e-126">Compile and run the client.</span></span>  

## <a name="net-framework-security"></a><span data-ttu-id="9953e-127">.NET Framework güvenliği</span><span class="sxs-lookup"><span data-stu-id="9953e-127">.NET Framework security</span></span>

<span data-ttu-id="9953e-128">Bu örnekte kullanılan sertifika, *MakeCert. exe*ile oluşturulmuş bir test sertifikasıdır çünkü, tarayıcınızla, gibi bir https adresine `https://localhost/servicemodelsamples/service.svc`erişmeye çalıştığınızda bir güvenlik uyarısı görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="9953e-128">Because the certificate used in this sample is a test certificate created with *Makecert.exe*, a security alert appears when you try to access an HTTPS address, such as `https://localhost/servicemodelsamples/service.svc`, from your browser.</span></span>

## <a name="see-also"></a><span data-ttu-id="9953e-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9953e-129">See also</span></span>

- [<span data-ttu-id="9953e-130">Güvenilir Oturumlar</span><span class="sxs-lookup"><span data-stu-id="9953e-130">Reliable Sessions</span></span>](../../../../docs/framework/wcf/feature-details/reliable-sessions.md)
