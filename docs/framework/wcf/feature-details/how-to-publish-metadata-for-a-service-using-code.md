---
title: 'Nasıl yapılır: Kod Kullanarak Bir Hizmet için Meta Verileri Yayımlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 51407e6d-4d87-42d5-be7c-9887b8652006
ms.openlocfilehash: 870142724321629d6dbeccd4118b814283901776
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59297973"
---
# <a name="how-to-publish-metadata-for-a-service-using-code"></a><span data-ttu-id="1f955-102">Nasıl yapılır: Kod Kullanarak Bir Hizmet için Meta Verileri Yayımlama</span><span class="sxs-lookup"><span data-stu-id="1f955-102">How to: Publish Metadata for a Service Using Code</span></span>
<span data-ttu-id="1f955-103">Bu, bir Windows Communication Foundation (WCF) hizmet için meta verileri yayımlama tartışmak iki nasıl yapılır konuları biridir.</span><span class="sxs-lookup"><span data-stu-id="1f955-103">This is one of two how-to topics that discuss publishing metadata for a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="1f955-104">Hizmet yapılandırma dosyasını ve kod kullanarak meta verileri nasıl yayımlamalısınız belirtmenin iki yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="1f955-104">There are two ways to specify how a service should publish metadata, using a configuration file and using code.</span></span> <span data-ttu-id="1f955-105">Bu konuda, bir kod kullanarak bir hizmet için meta verileri yayımlama gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1f955-105">This topic shows how to publish metadata for a service using a code.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="1f955-106">Bu konu, güvenli bir şekilde meta verileri yayımlama gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1f955-106">This topic shows how to publish metadata in an unsecure manner.</span></span> <span data-ttu-id="1f955-107">Herhangi bir istemci hizmet meta verileri alabilir.</span><span class="sxs-lookup"><span data-stu-id="1f955-107">Any client can retrieve the metadata from the service.</span></span> <span data-ttu-id="1f955-108">Meta verileri güvenli bir şekilde yayımlamak için hizmetinize gerekiyorsa.</span><span class="sxs-lookup"><span data-stu-id="1f955-108">If you require your service to publish metadata in a secure manner.</span></span> <span data-ttu-id="1f955-109">bkz: [özel güvenli meta veri uç noktası](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span><span class="sxs-lookup"><span data-stu-id="1f955-109">see [Custom Secure Metadata Endpoint](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span></span>  
  
 <span data-ttu-id="1f955-110">Bir yapılandırma dosyasında meta verileri yayımlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: Bir yapılandırma dosyası kullanarak bir hizmet için meta verileri yayımlama](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="1f955-110">For more information about publishing metadata in a configuration file, see [How to: Publish Metadata for a Service Using a Configuration File](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span></span> <span data-ttu-id="1f955-111">Meta veri yayımlama sağlayan bir WS aktarım GET isteği ya da bir HTTP/GET isteği kullanılarak kullanarak meta verileri almak istemcileri `?wsdl` sorgu dizesi.</span><span class="sxs-lookup"><span data-stu-id="1f955-111">Publishing metadata allows clients to retrieve the metadata using a WS-Transfer GET request or an HTTP/GET request using the `?wsdl` query string.</span></span> <span data-ttu-id="1f955-112">Kod, çalıştığından emin olmak için temel bir WCF Hizmeti oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1f955-112">To be sure that the code is working you must create a basic WCF service.</span></span> <span data-ttu-id="1f955-113">Temel bir şirket içinde barındırılan hizmeti, aşağıdaki kodda sağlanır.</span><span class="sxs-lookup"><span data-stu-id="1f955-113">A basic self-hosted service is provided in the following code.</span></span>  
  
 [!code-csharp[htPublishMetadataCode#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#0)]
 [!code-vb[htPublishMetadataCode#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#0)]  
  
### <a name="to-publish-metadata-in-code"></a><span data-ttu-id="1f955-114">Kodda meta verileri yayımlama</span><span class="sxs-lookup"><span data-stu-id="1f955-114">To publish metadata in code</span></span>  
  
1. <span data-ttu-id="1f955-115">Konsol uygulamasının ana yöntemi içinde örneği bir <xref:System.ServiceModel.ServiceHost> nesnesini geçirerek hizmet türü ve temel adres.</span><span class="sxs-lookup"><span data-stu-id="1f955-115">Within the main method of a console application, instantiate a <xref:System.ServiceModel.ServiceHost> object by passing in the service type and the base address.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#1)]
     [!code-vb[htPublishMetadataCode#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#1)]  
  
2. <span data-ttu-id="1f955-116">1. adım için kodun hemen altına bir try bloğu oluşturur, bu hizmet çalışırken oluşan herhangi bir özel durumu yakalar.</span><span class="sxs-lookup"><span data-stu-id="1f955-116">Create a try block immediately below the code for step 1, this catches any exceptions that get thrown while the service is running.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#2)]
     [!code-vb[htPublishMetadataCode#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#2)]  
  
     [!code-csharp[htPublishMetadataCode#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#3)]
     [!code-vb[htPublishMetadataCode#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#3)]  
  
3. <span data-ttu-id="1f955-117">Hizmet ana bilgisayarı zaten içerip içermediğini görmek için onay bir <xref:System.ServiceModel.Description.ServiceMetadataBehavior>, aksi takdirde, yeni bir <xref:System.ServiceModel.Description.ServiceMetadataBehavior> örneği.</span><span class="sxs-lookup"><span data-stu-id="1f955-117">Check to see whether the service host already contains a <xref:System.ServiceModel.Description.ServiceMetadataBehavior>, if not, create a new <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#4)]
     [!code-vb[htPublishMetadataCode#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#4)]  
  
4. <span data-ttu-id="1f955-118">Ayarlama <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> özelliği `true.`</span><span class="sxs-lookup"><span data-stu-id="1f955-118">Set the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> property to `true.`</span></span>  
  
     [!code-csharp[htPublishMetadataCode#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#5)]
     [!code-vb[htPublishMetadataCode#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#5)]  
  
5. <span data-ttu-id="1f955-119"><xref:System.ServiceModel.Description.ServiceMetadataBehavior> İçeren bir <xref:System.ServiceModel.Description.MetadataExporter> özelliği.</span><span class="sxs-lookup"><span data-stu-id="1f955-119">The <xref:System.ServiceModel.Description.ServiceMetadataBehavior> contains a <xref:System.ServiceModel.Description.MetadataExporter> property.</span></span> <span data-ttu-id="1f955-120"><xref:System.ServiceModel.Description.MetadataExporter> İçeren bir <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="1f955-120">The <xref:System.ServiceModel.Description.MetadataExporter> contains a <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> property.</span></span> <span data-ttu-id="1f955-121">Değerini <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> özelliğini <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A>.</span><span class="sxs-lookup"><span data-stu-id="1f955-121">Set the value of the <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> property to <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A>.</span></span> <span data-ttu-id="1f955-122"><xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> Özelliği de ayarlanabilir <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A>.</span><span class="sxs-lookup"><span data-stu-id="1f955-122">The <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> property can also be set to <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A>.</span></span> <span data-ttu-id="1f955-123">Ayarlandığında <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> meta verileri dışarı Aktarıcı meta verilerle ilke bilgilerini oluşturur, "için WS-Policy 1.5 uyar.</span><span class="sxs-lookup"><span data-stu-id="1f955-123">When set to <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> the metadata exporter generates policy information with the metadata that" conforms to WS-Policy 1.5.</span></span> <span data-ttu-id="1f955-124">Ayarlandığında <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A> meta verileri dışarı Aktarıcı WS-Policy 1.2 uyan ilke bilgilerini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1f955-124">When set to <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A> the metadata exporter generates policy information that conforms to WS-Policy 1.2.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#6)]
     [!code-vb[htPublishMetadataCode#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#6)]  
  
6. <span data-ttu-id="1f955-125">Ekleme <xref:System.ServiceModel.Description.ServiceMetadataBehavior> örneğine hizmet ana bilgisayarın davranışları koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="1f955-125">Add the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance to the service host's behaviors collection.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#7)]
     [!code-vb[htPublishMetadataCode#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#7)]  
  
7. <span data-ttu-id="1f955-126">Meta veri değişimi uç noktası için hizmet ana bilgisayarı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1f955-126">Add the metadata exchange endpoint to the service host.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#8)]
     [!code-vb[htPublishMetadataCode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#8)]  
  
8. <span data-ttu-id="1f955-127">Bir uygulama uç noktası için hizmet ana bilgisayarı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1f955-127">Add an application endpoint to the service host.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#9)]
     [!code-vb[htPublishMetadataCode#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#9)]  
  
    > [!NOTE]
    >  <span data-ttu-id="1f955-128">Hizmet için uç nokta eklemezseniz, çalışma zamanı varsayılan uç noktalar ekler.</span><span class="sxs-lookup"><span data-stu-id="1f955-128">If you do not add any endpoints to the service, the runtime adds default endpoints for you.</span></span> <span data-ttu-id="1f955-129">Bu örnekte, hizmetin sahip olduğu bir <xref:System.ServiceModel.Description.ServiceMetadataBehavior> kümesine `true`, hizmetin etkin meta veri yayımlama vardır.</span><span class="sxs-lookup"><span data-stu-id="1f955-129">In this example, because the service has a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> set to `true`, the service has publishing metadata enabled.</span></span> <span data-ttu-id="1f955-130">Varsayılan uç noktaları hakkında daha fazla bilgi için bkz. [Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="1f955-130">For more information about default endpoints, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
9. <span data-ttu-id="1f955-131">Hizmet ana bilgisayarı'nı açın ve gelen çağrılar için bekleyin.</span><span class="sxs-lookup"><span data-stu-id="1f955-131">Open the service host and wait for incoming calls.</span></span> <span data-ttu-id="1f955-132">Kullanıcı ENTER tuşuna bastığında hizmet ana bilgisayarını kapatın.</span><span class="sxs-lookup"><span data-stu-id="1f955-132">When the user presses ENTER, close the service host.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#10)]
     [!code-vb[htPublishMetadataCode#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#10)]  
  
10. <span data-ttu-id="1f955-133">Konsol uygulamasını derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1f955-133">Build and run the console application.</span></span>  
  
11. <span data-ttu-id="1f955-134">Hizmetin taban adresine göz atmak için Internet Explorer'ı kullanın (http://localhost:8001/MetadataSample Bu örnekte) ve meta veri yayımlama açık olduğunu doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="1f955-134">Use Internet Explorer to browse to the base address of the service (http://localhost:8001/MetadataSample in this sample) and verify that the metadata publishing is turned on.</span></span> <span data-ttu-id="1f955-135">Üst ve hemen "Bir hizmet oluşturdunuz." altında "Basit hizmeti" ifadesini içeren Web görüntülenen sayfası görmeniz gerekir</span><span class="sxs-lookup"><span data-stu-id="1f955-135">You should see a Web page displayed that says "Simple Service" at the top and immediately below "You have created a service."</span></span> <span data-ttu-id="1f955-136">Aksi durumda, sonuçta elde edilen sayfanın üst kısmındaki bir ileti görüntüler: "Bu hizmet için meta veri yayımlama şu anda devre dışı bırakıldı."</span><span class="sxs-lookup"><span data-stu-id="1f955-136">If not, a message at the top of the resulting page displays: "Metadata publishing for this service is currently disabled."</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f955-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="1f955-137">Example</span></span>  
 <span data-ttu-id="1f955-138">Aşağıdaki kod örneği, kod içinde hizmet meta verilerini yayımlayan temel bir WCF Hizmeti uygulamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1f955-138">The following code example shows the implementation of a basic WCF service that publishes metadata for the service in code.</span></span>  
  
 [!code-csharp[htPublishMetadataCode#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#11)]
 [!code-vb[htPublishMetadataCode#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="1f955-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1f955-139">See also</span></span>

- [<span data-ttu-id="1f955-140">Nasıl yapılır: Yönetilen bir uygulamada bir WCF Hizmeti barındırma</span><span class="sxs-lookup"><span data-stu-id="1f955-140">How to: Host a WCF Service in a Managed Application</span></span>](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)
- [<span data-ttu-id="1f955-141">Kendini Barındırma</span><span class="sxs-lookup"><span data-stu-id="1f955-141">Self-Host</span></span>](../../../../docs/framework/wcf/samples/self-host.md)
- [<span data-ttu-id="1f955-142">Meta Veri Mimarisine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="1f955-142">Metadata Architecture Overview</span></span>](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)
- [<span data-ttu-id="1f955-143">Meta Verileri Kullanma</span><span class="sxs-lookup"><span data-stu-id="1f955-143">Using Metadata</span></span>](../../../../docs/framework/wcf/feature-details/using-metadata.md)
- [<span data-ttu-id="1f955-144">Nasıl yapılır: Bir yapılandırma dosyası kullanarak bir hizmet için meta verileri yayımlama</span><span class="sxs-lookup"><span data-stu-id="1f955-144">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
