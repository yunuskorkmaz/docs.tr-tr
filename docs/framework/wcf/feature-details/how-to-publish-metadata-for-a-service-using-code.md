---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: kod kullanarak bir hizmet için meta verileri yayımlama'
title: 'Nasıl yapılır: Kod Kullanarak Bir Hizmet için Meta Verileri Yayımlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 51407e6d-4d87-42d5-be7c-9887b8652006
ms.openlocfilehash: 94939c77b1c66643b0cc378516479e35c41aefbb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793694"
---
# <a name="how-to-publish-metadata-for-a-service-using-code"></a><span data-ttu-id="976be-103">Nasıl yapılır: Kod Kullanarak Bir Hizmet için Meta Verileri Yayımlama</span><span class="sxs-lookup"><span data-stu-id="976be-103">How to: Publish Metadata for a Service Using Code</span></span>

<span data-ttu-id="976be-104">Bu, bir Windows Communication Foundation (WCF) hizmeti için yayımlama meta verilerini tartışan iki nasıl yapılır konuktan biridir.</span><span class="sxs-lookup"><span data-stu-id="976be-104">This is one of two how-to topics that discuss publishing metadata for a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="976be-105">Bir hizmetin bir yapılandırma dosyası kullanarak ve kod kullanarak meta verileri nasıl yayımlayacağınızı belirten iki yol vardır.</span><span class="sxs-lookup"><span data-stu-id="976be-105">There are two ways to specify how a service should publish metadata, using a configuration file and using code.</span></span> <span data-ttu-id="976be-106">Bu konu, kod kullanarak bir hizmet için meta verilerin nasıl yayımlanacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="976be-106">This topic shows how to publish metadata for a service using a code.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="976be-107">Bu konuda, meta verilerin güvensiz bir şekilde nasıl yayımlanacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="976be-107">This topic shows how to publish metadata in an unsecure manner.</span></span> <span data-ttu-id="976be-108">Tüm istemciler, hizmetten meta verileri alabilir.</span><span class="sxs-lookup"><span data-stu-id="976be-108">Any client can retrieve the metadata from the service.</span></span> <span data-ttu-id="976be-109">Hizmetinizin meta verileri güvenli bir şekilde yayımlamasını istiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="976be-109">If you require your service to publish metadata in a secure manner.</span></span> <span data-ttu-id="976be-110">bkz. [özel güvenli meta veri uç noktası](../samples/custom-secure-metadata-endpoint.md).</span><span class="sxs-lookup"><span data-stu-id="976be-110">see [Custom Secure Metadata Endpoint](../samples/custom-secure-metadata-endpoint.md).</span></span>  
  
 <span data-ttu-id="976be-111">Bir yapılandırma dosyasında meta verileri yayımlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: yapılandırma dosyası kullanarak bir hizmet Için meta verileri yayımlama](how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="976be-111">For more information about publishing metadata in a configuration file, see [How to: Publish Metadata for a Service Using a Configuration File](how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span></span> <span data-ttu-id="976be-112">Meta veri yayımlama, istemcilerin bir WS-Transfer GET isteği veya sorgu dizesini kullanarak bir HTTP/GET isteği kullanarak meta verileri almasına izin verir `?wsdl` .</span><span class="sxs-lookup"><span data-stu-id="976be-112">Publishing metadata allows clients to retrieve the metadata using a WS-Transfer GET request or an HTTP/GET request using the `?wsdl` query string.</span></span> <span data-ttu-id="976be-113">Kodun çalıştığından emin olmak için temel bir WCF hizmeti oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="976be-113">To be sure that the code is working you must create a basic WCF service.</span></span> <span data-ttu-id="976be-114">Aşağıdaki kodda temel bir kendini barındıran hizmet sağlanır.</span><span class="sxs-lookup"><span data-stu-id="976be-114">A basic self-hosted service is provided in the following code.</span></span>  
  
 [!code-csharp[htPublishMetadataCode#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#0)]
 [!code-vb[htPublishMetadataCode#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#0)]  
  
### <a name="to-publish-metadata-in-code"></a><span data-ttu-id="976be-115">Meta verileri kodda yayınlamak için</span><span class="sxs-lookup"><span data-stu-id="976be-115">To publish metadata in code</span></span>  
  
1. <span data-ttu-id="976be-116">Konsol uygulamasının Main yönteminde, <xref:System.ServiceModel.ServiceHost> hizmet türünü ve temel adresi geçirerek bir nesnesi örneği oluşturun.</span><span class="sxs-lookup"><span data-stu-id="976be-116">Within the main method of a console application, instantiate a <xref:System.ServiceModel.ServiceHost> object by passing in the service type and the base address.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#1)]
     [!code-vb[htPublishMetadataCode#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#1)]  
  
2. <span data-ttu-id="976be-117">1. adım için kodun hemen altında bir try bloğu oluşturun, bu, hizmet çalışırken oluşturulan tüm özel durumları yakalar.</span><span class="sxs-lookup"><span data-stu-id="976be-117">Create a try block immediately below the code for step 1, this catches any exceptions that get thrown while the service is running.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#2)]
     [!code-vb[htPublishMetadataCode#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#2)]  
  
     [!code-csharp[htPublishMetadataCode#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#3)]
     [!code-vb[htPublishMetadataCode#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#3)]  
  
3. <span data-ttu-id="976be-118">Hizmet ana bilgisayarının zaten bir içerip içermediğini denetleyin, yoksa <xref:System.ServiceModel.Description.ServiceMetadataBehavior> Yeni bir <xref:System.ServiceModel.Description.ServiceMetadataBehavior> örnek oluşturun.</span><span class="sxs-lookup"><span data-stu-id="976be-118">Check to see whether the service host already contains a <xref:System.ServiceModel.Description.ServiceMetadataBehavior>, if not, create a new <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#4)]
     [!code-vb[htPublishMetadataCode#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#4)]  
  
4. <span data-ttu-id="976be-119"><xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A>Özelliğini olarak ayarlayın`true.`</span><span class="sxs-lookup"><span data-stu-id="976be-119">Set the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> property to `true.`</span></span>  
  
     [!code-csharp[htPublishMetadataCode#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#5)]
     [!code-vb[htPublishMetadataCode#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#5)]  
  
5. <span data-ttu-id="976be-120">, <xref:System.ServiceModel.Description.ServiceMetadataBehavior> Bir <xref:System.ServiceModel.Description.MetadataExporter> özelliği içerir.</span><span class="sxs-lookup"><span data-stu-id="976be-120">The <xref:System.ServiceModel.Description.ServiceMetadataBehavior> contains a <xref:System.ServiceModel.Description.MetadataExporter> property.</span></span> <span data-ttu-id="976be-121">, <xref:System.ServiceModel.Description.MetadataExporter> Bir <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> özelliği içerir.</span><span class="sxs-lookup"><span data-stu-id="976be-121">The <xref:System.ServiceModel.Description.MetadataExporter> contains a <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> property.</span></span> <span data-ttu-id="976be-122"><xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A>Özelliğinin değerini olarak ayarlayın <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> .</span><span class="sxs-lookup"><span data-stu-id="976be-122">Set the value of the <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> property to <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A>.</span></span> <span data-ttu-id="976be-123"><xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A>Özelliği de olarak ayarlanabilir <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A> .</span><span class="sxs-lookup"><span data-stu-id="976be-123">The <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> property can also be set to <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A>.</span></span> <span data-ttu-id="976be-124"><xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A>Meta veri dışarı aktarıcı olarak ayarlandığında, "WS-Policy 1,5 'e uyan meta verilerle ilke bilgilerini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="976be-124">When set to <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> the metadata exporter generates policy information with the metadata that" conforms to WS-Policy 1.5.</span></span> <span data-ttu-id="976be-125"><xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A>Meta veri aktarıcı olarak ayarlandığında, WS-Policy 1,2 'e uyan ilke bilgilerini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="976be-125">When set to <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A> the metadata exporter generates policy information that conforms to WS-Policy 1.2.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#6)]
     [!code-vb[htPublishMetadataCode#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#6)]  
  
6. <span data-ttu-id="976be-126"><xref:System.ServiceModel.Description.ServiceMetadataBehavior>Örneği hizmet ana bilgisayarının davranış koleksiyonuna ekleyin.</span><span class="sxs-lookup"><span data-stu-id="976be-126">Add the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance to the service host's behaviors collection.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#7)]
     [!code-vb[htPublishMetadataCode#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#7)]  
  
7. <span data-ttu-id="976be-127">Meta veri değişimi uç noktasını hizmet ana bilgisayarına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="976be-127">Add the metadata exchange endpoint to the service host.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#8)]
     [!code-vb[htPublishMetadataCode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#8)]  
  
8. <span data-ttu-id="976be-128">Hizmet ana bilgisayarına bir uygulama uç noktası ekleyin.</span><span class="sxs-lookup"><span data-stu-id="976be-128">Add an application endpoint to the service host.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#9)]
     [!code-vb[htPublishMetadataCode#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#9)]  
  
    > [!NOTE]
    > <span data-ttu-id="976be-129">Hizmete herhangi bir uç nokta eklemediğiniz takdirde, çalışma zamanı sizin için varsayılan uç noktaları ekler.</span><span class="sxs-lookup"><span data-stu-id="976be-129">If you do not add any endpoints to the service, the runtime adds default endpoints for you.</span></span> <span data-ttu-id="976be-130">Bu örnekte, hizmetin <xref:System.ServiceModel.Description.ServiceMetadataBehavior> olarak ayarlanmış olması nedeniyle `true` , hizmette yayımlama meta verileri etkindir.</span><span class="sxs-lookup"><span data-stu-id="976be-130">In this example, because the service has a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> set to `true`, the service has publishing metadata enabled.</span></span> <span data-ttu-id="976be-131">Varsayılan uç noktalar hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="976be-131">For more information about default endpoints, see [Simplified Configuration](../simplified-configuration.md) and [Simplified Configuration for WCF Services](../samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
9. <span data-ttu-id="976be-132">Hizmet konağını açın ve gelen çağrıları bekleyin.</span><span class="sxs-lookup"><span data-stu-id="976be-132">Open the service host and wait for incoming calls.</span></span> <span data-ttu-id="976be-133">Kullanıcı ENTER tuşuna bastığında hizmet konağını kapatın.</span><span class="sxs-lookup"><span data-stu-id="976be-133">When the user presses ENTER, close the service host.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#10)]
     [!code-vb[htPublishMetadataCode#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#10)]  
  
10. <span data-ttu-id="976be-134">Konsol uygulamasını derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="976be-134">Build and run the console application.</span></span>  
  
11. <span data-ttu-id="976be-135">Internet Explorer 'ı kullanarak hizmetin temel adresine gidin ( `http://localhost:8001/MetadataSample` Bu örnekte) ve meta veri yayımlamanın açık olduğunu doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="976be-135">Use Internet Explorer to browse to the base address of the service (`http://localhost:8001/MetadataSample` in this sample) and verify that the metadata publishing is turned on.</span></span> <span data-ttu-id="976be-136">En üstte "basit hizmet" ve hemen aşağıda "bir hizmet oluşturdunuz" ifadesinin görüntülendiğini belirten bir Web sayfası görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="976be-136">You should see a Web page displayed that says "Simple Service" at the top and immediately below "You have created a service."</span></span> <span data-ttu-id="976be-137">Aksi takdirde, sonuçta ortaya çıkan sayfanın en üstündeki bir ileti şunu görüntüler: "Bu hizmet için meta veri yayımlama Şu anda devre dışı."</span><span class="sxs-lookup"><span data-stu-id="976be-137">If not, a message at the top of the resulting page displays: "Metadata publishing for this service is currently disabled."</span></span>  
  
## <a name="example"></a><span data-ttu-id="976be-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="976be-138">Example</span></span>  

 <span data-ttu-id="976be-139">Aşağıdaki kod örneği, kodda hizmet için meta veriler yayımlayan temel bir WCF hizmeti uygulamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="976be-139">The following code example shows the implementation of a basic WCF service that publishes metadata for the service in code.</span></span>  
  
 [!code-csharp[htPublishMetadataCode#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#11)]
 [!code-vb[htPublishMetadataCode#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="976be-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="976be-140">See also</span></span>

- [<span data-ttu-id="976be-141">Nasıl yapılır: Yönetilen Bir Uygulamada Bir WCF Hizmeti Barındırma</span><span class="sxs-lookup"><span data-stu-id="976be-141">How to: Host a WCF Service in a Managed Application</span></span>](../how-to-host-a-wcf-service-in-a-managed-application.md)
- [<span data-ttu-id="976be-142">Kendini Barındırma</span><span class="sxs-lookup"><span data-stu-id="976be-142">Self-Host</span></span>](../samples/self-host.md)
- [<span data-ttu-id="976be-143">Meta Veri Mimarisi Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="976be-143">Metadata Architecture Overview</span></span>](metadata-architecture-overview.md)
- [<span data-ttu-id="976be-144">Meta Verileri Kullanma</span><span class="sxs-lookup"><span data-stu-id="976be-144">Using Metadata</span></span>](using-metadata.md)
- [<span data-ttu-id="976be-145">Nasıl yapılır: Yapılandırma Dosyası Kullanarak Bir Hizmet için Meta Verileri Yayımlama</span><span class="sxs-lookup"><span data-stu-id="976be-145">How to: Publish Metadata for a Service Using a Configuration File</span></span>](how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
