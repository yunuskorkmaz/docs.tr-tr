---
title: 'Nasıl yapılır: Kod Kullanarak Bir Hizmet için Meta Verileri Yayımlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 51407e6d-4d87-42d5-be7c-9887b8652006
ms.openlocfilehash: bef5421d377bcae6e8c56b0117ebbe22a861de86
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33496630"
---
# <a name="how-to-publish-metadata-for-a-service-using-code"></a><span data-ttu-id="653d4-102">Nasıl yapılır: Kod Kullanarak Bir Hizmet için Meta Verileri Yayımlama</span><span class="sxs-lookup"><span data-stu-id="653d4-102">How to: Publish Metadata for a Service Using Code</span></span>
<span data-ttu-id="653d4-103">Bu, bir Windows Communication Foundation (WCF) hizmet için meta veri yayımlama ele iki nasıl yapılır konuları biridir.</span><span class="sxs-lookup"><span data-stu-id="653d4-103">This is one of two how-to topics that discuss publishing metadata for a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="653d4-104">Bir hizmeti bir yapılandırma dosyası kullanarak ve kod kullanarak meta verileri, nasıl yayınlamalıdır belirtmek için iki yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="653d4-104">There are two ways to specify how a service should publish metadata, using a configuration file and using code.</span></span> <span data-ttu-id="653d4-105">Bu konuda, bir kod kullanarak bir hizmet için meta verileri yayımlama gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="653d4-105">This topic shows how to publish metadata for a service using a code.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="653d4-106">Bu konu, güvenli olmayan bir şekilde meta verileri yayımlama gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="653d4-106">This topic shows how to publish metadata in an unsecure manner.</span></span> <span data-ttu-id="653d4-107">Herhangi bir istemci hizmetinden meta verileri alabilir.</span><span class="sxs-lookup"><span data-stu-id="653d4-107">Any client can retrieve the metadata from the service.</span></span> <span data-ttu-id="653d4-108">Meta veriler güvenli bir şekilde yayımlamak için hizmetinizin gerekiyorsa.</span><span class="sxs-lookup"><span data-stu-id="653d4-108">If you require your service to publish metadata in a secure manner.</span></span> <span data-ttu-id="653d4-109">bkz: [özel güvenli meta veri uç noktasının](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span><span class="sxs-lookup"><span data-stu-id="653d4-109">see [Custom Secure Metadata Endpoint](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span></span>  
  
 <span data-ttu-id="653d4-110">Yapılandırma dosyasındaki meta veri yayımlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir yapılandırma dosyası kullanarak bir hizmet için meta veri yayımlama](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="653d4-110">For more information about publishing metadata in a configuration file, see [How to: Publish Metadata for a Service Using a Configuration File](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span></span> <span data-ttu-id="653d4-111">Meta veri yayımlama sağlayan bir WS-aktarımı GET isteği ya da bir HTTP/GET isteği kullanarak kullanarak meta verileri almak istemcileri `?wsdl` sorgu dizesi.</span><span class="sxs-lookup"><span data-stu-id="653d4-111">Publishing metadata allows clients to retrieve the metadata using a WS-Transfer GET request or an HTTP/GET request using the `?wsdl` query string.</span></span> <span data-ttu-id="653d4-112">Kod, çalıştığından emin olmak için temel bir WCF Hizmeti oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="653d4-112">To be sure that the code is working you must create a basic WCF service.</span></span> <span data-ttu-id="653d4-113">Temel bir kendi kendini barındıran hizmet aşağıdaki kodu sağlanır.</span><span class="sxs-lookup"><span data-stu-id="653d4-113">A basic self-hosted service is provided in the following code.</span></span>  
  
 [!code-csharp[htPublishMetadataCode#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#0)]
 [!code-vb[htPublishMetadataCode#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#0)]  
  
### <a name="to-publish-metadata-in-code"></a><span data-ttu-id="653d4-114">Kodda metadata yayımlamak için</span><span class="sxs-lookup"><span data-stu-id="653d4-114">To publish metadata in code</span></span>  
  
1.  <span data-ttu-id="653d4-115">Bir konsol uygulaması ana yöntem içinde örneği bir <xref:System.ServiceModel.ServiceHost> hizmet türü ve taban adresi geçirerek nesnesi.</span><span class="sxs-lookup"><span data-stu-id="653d4-115">Within the main method of a console application, instantiate a <xref:System.ServiceModel.ServiceHost> object by passing in the service type and the base address.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#1)]
     [!code-vb[htPublishMetadataCode#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#1)]  
  
2.  <span data-ttu-id="653d4-116">Try bloğunun hemen altındaki 1. adım için kod oluşturur, bu hizmet çalışırken oluşan tüm özel durumları yakalar.</span><span class="sxs-lookup"><span data-stu-id="653d4-116">Create a try block immediately below the code for step 1, this catches any exceptions that get thrown while the service is running.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#2)]
     [!code-vb[htPublishMetadataCode#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#2)]  
  
     [!code-csharp[htPublishMetadataCode#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#3)]
     [!code-vb[htPublishMetadataCode#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#3)]  
  
3.  <span data-ttu-id="653d4-117">Hizmet ana bilgisayarı zaten bulunup bulunmadığını denetleyin bir <xref:System.ServiceModel.Description.ServiceMetadataBehavior>, aksi takdirde, yeni bir <xref:System.ServiceModel.Description.ServiceMetadataBehavior> örneği.</span><span class="sxs-lookup"><span data-stu-id="653d4-117">Check to see whether the service host already contains a <xref:System.ServiceModel.Description.ServiceMetadataBehavior>, if not, create a new <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#4)]
     [!code-vb[htPublishMetadataCode#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#4)]  
  
4.  <span data-ttu-id="653d4-118">Ayarlama <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> özelliği `true.`</span><span class="sxs-lookup"><span data-stu-id="653d4-118">Set the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> property to `true.`</span></span>  
  
     [!code-csharp[htPublishMetadataCode#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#5)]
     [!code-vb[htPublishMetadataCode#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#5)]  
  
5.  <span data-ttu-id="653d4-119"><xref:System.ServiceModel.Description.ServiceMetadataBehavior> İçeren bir <xref:System.ServiceModel.Description.MetadataExporter> özelliği.</span><span class="sxs-lookup"><span data-stu-id="653d4-119">The <xref:System.ServiceModel.Description.ServiceMetadataBehavior> contains a <xref:System.ServiceModel.Description.MetadataExporter> property.</span></span> <span data-ttu-id="653d4-120"><xref:System.ServiceModel.Description.MetadataExporter> İçeren bir <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="653d4-120">The <xref:System.ServiceModel.Description.MetadataExporter> contains a <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> property.</span></span> <span data-ttu-id="653d4-121">Değerini <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> özelliğine <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A>.</span><span class="sxs-lookup"><span data-stu-id="653d4-121">Set the value of the <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> property to <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A>.</span></span> <span data-ttu-id="653d4-122"><xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> Özelliği de ayarlanabilir <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A>.</span><span class="sxs-lookup"><span data-stu-id="653d4-122">The <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> property can also be set to <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A>.</span></span> <span data-ttu-id="653d4-123">Ayarlandığında <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> meta verileri dışarı aktarma ilkesi bilgileri meta verileri ile oluşturur, "WS-Policy 1.5 uyumlu.</span><span class="sxs-lookup"><span data-stu-id="653d4-123">When set to <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> the metadata exporter generates policy information with the metadata that" conforms to WS-Policy 1.5.</span></span> <span data-ttu-id="653d4-124">Ayarlandığında <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A> meta verileri dışarı aktarma WS-Policy 1.2 uyumlu ilke bilgilerini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="653d4-124">When set to <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A> the metadata exporter generates policy information that conforms to WS-Policy 1.2.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#6)]
     [!code-vb[htPublishMetadataCode#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#6)]  
  
6.  <span data-ttu-id="653d4-125">Ekleme <xref:System.ServiceModel.Description.ServiceMetadataBehavior> hizmet ana bilgisayarın davranışları koleksiyonuna örneği.</span><span class="sxs-lookup"><span data-stu-id="653d4-125">Add the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance to the service host's behaviors collection.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#7)]
     [!code-vb[htPublishMetadataCode#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#7)]  
  
7.  <span data-ttu-id="653d4-126">Meta veri exchange uç noktası hizmeti konak ekleyin.</span><span class="sxs-lookup"><span data-stu-id="653d4-126">Add the metadata exchange endpoint to the service host.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#8)]
     [!code-vb[htPublishMetadataCode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#8)]  
  
8.  <span data-ttu-id="653d4-127">Uygulama uç hizmeti konak ekleyin.</span><span class="sxs-lookup"><span data-stu-id="653d4-127">Add an application endpoint to the service host.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#9)]
     [!code-vb[htPublishMetadataCode#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#9)]  
  
    > [!NOTE]
    >  <span data-ttu-id="653d4-128">Hizmeti için uç nokta eklemezseniz çalışma zamanı varsayılan uç noktaları ekler.</span><span class="sxs-lookup"><span data-stu-id="653d4-128">If you do not add any endpoints to the service, the runtime adds default endpoints for you.</span></span> <span data-ttu-id="653d4-129">Bu örnekte, hizmetin sahip olduğu bir <xref:System.ServiceModel.Description.ServiceMetadataBehavior> kümesine `true`, hizmetin etkin meta veri yayımlama vardır.</span><span class="sxs-lookup"><span data-stu-id="653d4-129">In this example, because the service has a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> set to `true`, the service has publishing metadata enabled.</span></span> <span data-ttu-id="653d4-130">Varsayılan uç noktalar hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="653d4-130">For more information about default endpoints, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
9. <span data-ttu-id="653d4-131">Hizmet ana bilgisayarı'nı açın ve gelen çağrıları için bekleyin.</span><span class="sxs-lookup"><span data-stu-id="653d4-131">Open the service host and wait for incoming calls.</span></span> <span data-ttu-id="653d4-132">Kullanıcı ENTER tuşuna bastığında hizmet ana bilgisayarını kapatın.</span><span class="sxs-lookup"><span data-stu-id="653d4-132">When the user presses ENTER, close the service host.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#10)]
     [!code-vb[htPublishMetadataCode#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#10)]  
  
10. <span data-ttu-id="653d4-133">Derleme ve konsol uygulamasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="653d4-133">Build and run the console application.</span></span>  
  
11. <span data-ttu-id="653d4-134">Hizmetin taban adresine göz atmak için Internet Explorer kullanın (http://localhost:8001/MetadataSample Bu örnekte) ve meta veri yayımlama açık olduğunu doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="653d4-134">Use Internet Explorer to browse to the base address of the service (http://localhost:8001/MetadataSample in this sample) and verify that the metadata publishing is turned on.</span></span> <span data-ttu-id="653d4-135">En üstte ve hemen altında "Bir hizmet oluşturdunuz." bir Web görüntülenen "Basit hizmeti" diyen sayfasını görmeniz gerekir</span><span class="sxs-lookup"><span data-stu-id="653d4-135">You should see a Web page displayed that says "Simple Service" at the top and immediately below "You have created a service."</span></span> <span data-ttu-id="653d4-136">Değilse, sayfanın üst kısmındaki ortaya çıkan bir ileti görüntüler: "Bu hizmet için meta veri yayımlama şu anda devre dışı."</span><span class="sxs-lookup"><span data-stu-id="653d4-136">If not, a message at the top of the resulting page displays: "Metadata publishing for this service is currently disabled."</span></span>  
  
## <a name="example"></a><span data-ttu-id="653d4-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="653d4-137">Example</span></span>  
 <span data-ttu-id="653d4-138">Aşağıdaki kod örneğinde kod içinde hizmet için meta veriler yayımlar temel bir WCF Hizmeti uygulamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="653d4-138">The following code example shows the implementation of a basic WCF service that publishes metadata for the service in code.</span></span>  
  
 [!code-csharp[htPublishMetadataCode#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#11)]
 [!code-vb[htPublishMetadataCode#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="653d4-139">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="653d4-139">See Also</span></span>  
 [<span data-ttu-id="653d4-140">Nasıl yapılır: Yönetilen Bir Uygulamada Bir WCF Hizmeti Barındırma</span><span class="sxs-lookup"><span data-stu-id="653d4-140">How to: Host a WCF Service in a Managed Application</span></span>](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)  
 [<span data-ttu-id="653d4-141">Kendini Barındırma</span><span class="sxs-lookup"><span data-stu-id="653d4-141">Self-Host</span></span>](../../../../docs/framework/wcf/samples/self-host.md)  
 [<span data-ttu-id="653d4-142">Meta Veri Mimarisine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="653d4-142">Metadata Architecture Overview</span></span>](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)  
 [<span data-ttu-id="653d4-143">Meta Verileri Kullanma</span><span class="sxs-lookup"><span data-stu-id="653d4-143">Using Metadata</span></span>](../../../../docs/framework/wcf/feature-details/using-metadata.md)  
 [<span data-ttu-id="653d4-144">Nasıl yapılır: Yapılandırma Dosyası Kullanarak Bir Hizmet için Meta Verileri Yayımlama</span><span class="sxs-lookup"><span data-stu-id="653d4-144">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
