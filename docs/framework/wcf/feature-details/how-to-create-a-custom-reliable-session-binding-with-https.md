---
title: 'Nasıl yapılır: HTTPS ile Özel Bir Güvenilir Oturum Bağlama Oluşturma'
ms.date: 03/30/2017
ms.assetid: fa772232-da1f-4c66-8c94-e36c0584b549
ms.openlocfilehash: f39325829cf4b548482a6a570a5aa1fd65e61a1d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62039539"
---
# <a name="how-to-create-a-custom-reliable-session-binding-with-https"></a><span data-ttu-id="866bd-102">Nasıl yapılır: HTTPS ile Özel Bir Güvenilir Oturum Bağlama Oluşturma</span><span class="sxs-lookup"><span data-stu-id="866bd-102">How to: Create a Custom Reliable Session Binding with HTTPS</span></span>

<span data-ttu-id="866bd-103">Bu konu, Güvenli Yuva Katmanı (SSL) aktarım güvenliği ile güvenilir oturumlar kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="866bd-103">This topic demonstrates the use of Secure Sockets Layer (SSL) transport security with reliable sessions.</span></span> <span data-ttu-id="866bd-104">Güvenilir oturum HTTPS üzerinden kullanmak için özel bağlama güvenilir oturum ve HTTPS aktarımı kullanan oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="866bd-104">To use a reliable session over HTTPS, you must create a custom binding that uses a reliable session and the HTTPS transport.</span></span> <span data-ttu-id="866bd-105">Güvenilir oturum kesin kod kullanarak veya bildirimli olarak yapılandırma dosyasında etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="866bd-105">You enable the reliable session either imperatively by using code or declaratively in the configuration file.</span></span> <span data-ttu-id="866bd-106">Güvenilir oturum etkinleştirmek için bu yordam istemci ve hizmet yapılandırma dosyalarını kullanır ve [  **\<httpsTransport >** ](../../../../docs/framework/configure-apps/file-schema/wcf/httpstransport.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="866bd-106">This procedure uses the client and service configuration files to enable the reliable session and the [**\<httpsTransport>**](../../../../docs/framework/configure-apps/file-schema/wcf/httpstransport.md) element.</span></span>

<span data-ttu-id="866bd-107">Bu yordam önemli bir parçası olan  **\<uç noktası >** yapılandırma öğesi içeren bir `bindingConfiguration` adlı bir özel bağlama yapılandırma başvuran öznitelik `reliableSessionOverHttps`.</span><span class="sxs-lookup"><span data-stu-id="866bd-107">The key part of this procedure is that the **\<endpoint>** configuration element contain a `bindingConfiguration` attribute that references a custom binding configuration named `reliableSessionOverHttps`.</span></span> <span data-ttu-id="866bd-108">[  **\<Bağlama >** ](../../../../docs/framework/misc/binding.md) yapılandırma öğesi ekleyerek bir güvenilir oturum ve HTTPS aktarımı kullanılan belirtmek için bu ada başvuran  **\< reliableSession >** ve  **\<httpsTransport >** öğeleri.</span><span class="sxs-lookup"><span data-stu-id="866bd-108">The [**\<binding>**](../../../../docs/framework/misc/binding.md) configuration element references this name to specify that a reliable session and the HTTPS transport are used by including **\<reliableSession>** and **\<httpsTransport>** elements.</span></span>

<span data-ttu-id="866bd-109">Bu örnekte kaynak kopyası için bkz: [özel bağlama güvenilir oturum HTTPS üzerinden](../../../../docs/framework/wcf/samples/custom-binding-reliable-session-over-https.md).</span><span class="sxs-lookup"><span data-stu-id="866bd-109">For the source copy of this example, see [Custom Binding Reliable Session over HTTPS](../../../../docs/framework/wcf/samples/custom-binding-reliable-session-over-https.md).</span></span>

### <a name="configure-the-service-with-a-custombinding-to-use-a-reliable-session-with-https"></a><span data-ttu-id="866bd-110">Güvenilir oturum ile HTTPS kullanmak için bir CustomBinding ile hizmetini yapılandırma</span><span class="sxs-lookup"><span data-stu-id="866bd-110">Configure the service with a CustomBinding to use a reliable session with HTTPS</span></span>

1. <span data-ttu-id="866bd-111">Hizmet türü için bir hizmet anlaşmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="866bd-111">Define a service contract for the type of service.</span></span>

   [!code-csharp[c_HowTo_CreateReliableSessionHTTPS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/service.cs#1121)]

1. <span data-ttu-id="866bd-112">Hizmet sözleşmesi bir hizmet sınıfında uygulayın.</span><span class="sxs-lookup"><span data-stu-id="866bd-112">Implement the service contract in a service class.</span></span> <span data-ttu-id="866bd-113">Adres veya bağlama bilgileri hizmeti uygulaması içinde belirtilmemiş unutmayın.</span><span class="sxs-lookup"><span data-stu-id="866bd-113">Note that the address or binding information isn't specified inside the implementation of the service.</span></span> <span data-ttu-id="866bd-114">Yapılandırma dosyasından adresi veya bağlama bilgileri almak üzere kod yazmak için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="866bd-114">You aren't required to write code to retrieve the address or binding information from the configuration file.</span></span>

   [!code-csharp[c_HowTo_CreateReliableSessionHTTPS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/service.cs#1122)]

1. <span data-ttu-id="866bd-115">Oluşturma bir *Web.config* yapılandırmak için bir uç nokta için bir dosya `CalculatorService` adlı özel bir bağlama ile `reliableSessionOverHttps` güvenilir bir oturum ve HTTPS aktarımı kullanır.</span><span class="sxs-lookup"><span data-stu-id="866bd-115">Create a *Web.config* file to configure an endpoint for the `CalculatorService` with a custom binding named `reliableSessionOverHttps` that uses a reliable session and the HTTPS transport.</span></span>

   [!code-xml[c_HowTo_CreateReliableSessionHTTPS#2111](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/common/web.config#2111)]

1. <span data-ttu-id="866bd-116">Oluşturma bir *Service.svc* satırını içeren dosya:</span><span class="sxs-lookup"><span data-stu-id="866bd-116">Create a *Service.svc* file that contains the line:</span></span>

   ```
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```

1. <span data-ttu-id="866bd-117">Bir yerde *Service.svc* Internet Information Services (IIS) sanal dizininizin dosyasında.</span><span class="sxs-lookup"><span data-stu-id="866bd-117">Place the *Service.svc* file in your Internet Information Services (IIS) virtual directory.</span></span>

### <a name="configure-the-client-with-a-custombinding-to-use-a-reliable-session-with-https"></a><span data-ttu-id="866bd-118">Güvenilir oturum ile HTTPS kullanmak için bir CustomBinding ile istemciyi Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="866bd-118">Configure the client with a CustomBinding to use a reliable session with HTTPS</span></span>

1. <span data-ttu-id="866bd-119">Kullanım [ServiceModel meta veri yardımcı Programracı (*Svcutil.exe*)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) hizmet meta verilerinden kodu oluşturmak için komut satırından.</span><span class="sxs-lookup"><span data-stu-id="866bd-119">Use the [ServiceModel Metadata Utility Tool (*Svcutil.exe*)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) from the command line to generate code from service metadata.</span></span>

   ```console
   Svcutil.exe <Metadata Exchange (MEX) address or HTTP GET address>
   ```

1. <span data-ttu-id="866bd-120">Oluşturulan istemci içeren `ICalculator` istemci uygulaması karşılaması gereken hizmet sözleşmesini tanımlayan arabirimi.</span><span class="sxs-lookup"><span data-stu-id="866bd-120">The client that's generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1221)]

1. <span data-ttu-id="866bd-121">Oluşturulan istemci uygulaması da uygulamasını içerir `ClientCalculator`.</span><span class="sxs-lookup"><span data-stu-id="866bd-121">The generated client application also contains the implementation of the `ClientCalculator`.</span></span> <span data-ttu-id="866bd-122">Adres ve bağlama bilgileri hizmeti uygulaması içinde belirtilmemiş unutmayın.</span><span class="sxs-lookup"><span data-stu-id="866bd-122">Note that the address and binding information isn't specified inside the implementation of the service.</span></span> <span data-ttu-id="866bd-123">Yapılandırma dosyasından adres ve bağlama bilgilerini almak üzere kod yazmak için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="866bd-123">You aren't required to write code to retrieve the address and binding information from the configuration file.</span></span>

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1222)]

1. <span data-ttu-id="866bd-124">Adlı özel bir bağlama yapılandırmak `reliableSessionOverHttps` HTTPS aktarımı ve güvenilir oturumlar kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="866bd-124">Configure a custom binding named `reliableSessionOverHttps` to use the HTTPS transport and reliable sessions.</span></span>

   [!code-xml[C_HowTo_CreateReliableSessionHTTPS#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/common/app.config#2211)]

1. <span data-ttu-id="866bd-125">Bir örneğini oluşturmak `ClientCalculator` uygulamada ve hizmet işlemleri çağırma.</span><span class="sxs-lookup"><span data-stu-id="866bd-125">Create an instance of the `ClientCalculator` in an application and then call the service operations.</span></span>

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1223)]

1. <span data-ttu-id="866bd-126">Derleyin ve istemci çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="866bd-126">Compile and run the client.</span></span>  

## <a name="net-framework-security"></a><span data-ttu-id="866bd-127">.NET Framework güvenliği</span><span class="sxs-lookup"><span data-stu-id="866bd-127">.NET Framework security</span></span>

<span data-ttu-id="866bd-128">Bu örnekte kullanılan sertifika ile oluşturulan bir test sertifikası olduğundan *Makecert.exe*, bir HTTPS adresi gibi erişmeye çalıştığınızda bir güvenlik uyarısı görünür `https://localhost/servicemodelsamples/service.svc`, tarayıcınız üzerinden.</span><span class="sxs-lookup"><span data-stu-id="866bd-128">Because the certificate used in this sample is a test certificate created with *Makecert.exe*, a security alert appears when you try to access an HTTPS address, such as `https://localhost/servicemodelsamples/service.svc`, from your browser.</span></span>

## <a name="see-also"></a><span data-ttu-id="866bd-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="866bd-129">See also</span></span>

- [<span data-ttu-id="866bd-130">Güvenilir Oturumlar</span><span class="sxs-lookup"><span data-stu-id="866bd-130">Reliable Sessions</span></span>](../../../../docs/framework/wcf/feature-details/reliable-sessions.md)
