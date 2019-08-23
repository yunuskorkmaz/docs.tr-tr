---
title: 'Nasıl yapılır: Hizmet Uç Noktalarına Meta Verileri İçe Aktarma'
ms.date: 03/30/2017
ms.assetid: b69dbe20-92a1-4911-89d8-ffbc3dad4663
ms.openlocfilehash: dce65c31134c211c134cbae2b9bd8296f74b1627
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930721"
---
# <a name="how-to-import-metadata-into-service-endpoints"></a><span data-ttu-id="d1910-102">Nasıl yapılır: Hizmet Uç Noktalarına Meta Verileri İçe Aktarma</span><span class="sxs-lookup"><span data-stu-id="d1910-102">How to: Import Metadata into Service Endpoints</span></span>
<span data-ttu-id="d1910-103">Bu konuda, bir hizmet uç noktası koleksiyonuna meta verilerin nasıl içeri aktarılacağı ve [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md)' de tanımlanan hizmetin nasıl kullanılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d1910-103">This topic explains how to import metadata into a collection of service endpoints and use the service defined in the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="d1910-104">Bu konuda, hizmetten meta verileri içeri aktaran ve sonra hizmette `Add` yöntemi çağıran bir istemci uygulamasının nasıl oluşturulacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d1910-104">This topic show how to create a client application that imports metadata from the service and then calls the `Add` method on the service.</span></span>  
  
### <a name="to-import-metadata-into-service-endpoints"></a><span data-ttu-id="d1910-105">Meta verileri hizmet uç noktalarına aktarmak için</span><span class="sxs-lookup"><span data-stu-id="d1910-105">To import metadata into service endpoints</span></span>  
  
1. <span data-ttu-id="d1910-106">Bir <xref:System.ServiceModel.EndpointAddress> nesne bildirin ve hizmetin meta veri değişimi (MEX) adresi için Tekdüzen Kaynak tanımlayıcısı (URI) ile başlatın.</span><span class="sxs-lookup"><span data-stu-id="d1910-106">Declare an <xref:System.ServiceModel.EndpointAddress> object and initialize it with the Uniform Resource Identifier (URI) for the metadata exchange (MEX) address of the service.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#0)]  
  
2. <span data-ttu-id="d1910-107">Bir <xref:System.ServiceModel.Description.MetadataExchangeClient>oluşturun, MEX adresini geçirerek ve çağırın <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A>.</span><span class="sxs-lookup"><span data-stu-id="d1910-107">Create a <xref:System.ServiceModel.Description.MetadataExchangeClient>, passing in the MEX address, and call <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A>.</span></span> <span data-ttu-id="d1910-108">Bu, hizmetten meta verileri alır.</span><span class="sxs-lookup"><span data-stu-id="d1910-108">This retrieves the metadata from the service.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#1)]  
  
3. <span data-ttu-id="d1910-109">Daha önce <xref:System.ServiceModel.Description.WsdlImporter>alınan meta verileri geçirerek bir oluşturun ve çağırın. <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A></span><span class="sxs-lookup"><span data-stu-id="d1910-109">Create a <xref:System.ServiceModel.Description.WsdlImporter>, passing in the metadata previously retrieved, and call <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>.</span></span> <span data-ttu-id="d1910-110">Bu bir <xref:System.ServiceModel.Description.ContractDescription> nesne koleksiyonu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d1910-110">This generates a collection of <xref:System.ServiceModel.Description.ContractDescription> objects.</span></span> <span data-ttu-id="d1910-111">Gereksinimlerinize bağlı olarak, <xref:System.ServiceModel.Description.WsdlImporter.ImportAllEndpoints%2A> veya <xref:System.ServiceModel.Description.WsdlImporter.ImportAllBindings%2A>öğesini de çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d1910-111">You could also call <xref:System.ServiceModel.Description.WsdlImporter.ImportAllEndpoints%2A> or <xref:System.ServiceModel.Description.WsdlImporter.ImportAllBindings%2A>, depending upon your needs.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#2)]  
  
    > [!NOTE]
    > <span data-ttu-id="d1910-112">Meta verileri içeri aktardıktan sonra, bir istemci kanalı oluşturamaz veya meta verileri dışarı aktarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d1910-112">After you have imported the metadata, you will not be able to create a client channel or export the metadata.</span></span> <span data-ttu-id="d1910-113">Bunun nedeni, bu noktada hiçbir tür bilgisinin mevcut olmaması değildir.</span><span class="sxs-lookup"><span data-stu-id="d1910-113">This is because no type information is available at this point.</span></span> <span data-ttu-id="d1910-114">Hizmet veya dışarı aktarma meta verileriyle etkileşim kurmak için tür bilgileri gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d1910-114">Type information is required to actually interact with the service or export metadata.</span></span> <span data-ttu-id="d1910-115">Tür bilgilerini oluşturmak için, 4 ve 5. adımlarda gösterilen kodu oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d1910-115">To generate the type information, you need to generate code, shown in steps 4 and 5.</span></span> <span data-ttu-id="d1910-116">Alternatif olarak, <xref:System.ServiceModel.Description.MetadataResolver> yardımcı sınıfını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d1910-116">Alternatively, you could use the <xref:System.ServiceModel.Description.MetadataResolver> helper class.</span></span> <span data-ttu-id="d1910-117">Daha fazla bilgi için [nasıl yapılır: Bağlama meta verilerini dinamik olarak](../../../../docs/framework/wcf/feature-details/how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically.md)almak Için MetadataResolver kullanın.</span><span class="sxs-lookup"><span data-stu-id="d1910-117">For more information, see [How to: Use MetadataResolver to Obtain Binding Metadata Dynamically](../../../../docs/framework/wcf/feature-details/how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically.md).</span></span>  
  
4. <span data-ttu-id="d1910-118">Her sözleşme için tür bilgisi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d1910-118">Generate type information for each contract.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#3)]  
  
5. <span data-ttu-id="d1910-119">Artık bu bilgileri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d1910-119">Now you can use this information.</span></span> <span data-ttu-id="d1910-120">Aşağıdaki örnek kaynak kodu C# oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d1910-120">The following sample generates C# source code.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#4)]  
  
## <a name="see-also"></a><span data-ttu-id="d1910-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d1910-121">See also</span></span>

- [<span data-ttu-id="d1910-122">Meta Veriler</span><span class="sxs-lookup"><span data-stu-id="d1910-122">Metadata</span></span>](../../../../docs/framework/wcf/feature-details/metadata.md)
- [<span data-ttu-id="d1910-123">Başlarken</span><span class="sxs-lookup"><span data-stu-id="d1910-123">Getting Started</span></span>](../../../../docs/framework/wcf/samples/getting-started-sample.md)
