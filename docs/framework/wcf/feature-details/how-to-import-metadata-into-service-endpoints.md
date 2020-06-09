---
title: 'Nasıl yapılır: Hizmet Uç Noktalarına Meta Verileri İçe Aktarma'
ms.date: 03/30/2017
ms.assetid: b69dbe20-92a1-4911-89d8-ffbc3dad4663
ms.openlocfilehash: 1de316b8e91739d5e3e24ff960e2cdfb33cc7fab
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597065"
---
# <a name="how-to-import-metadata-into-service-endpoints"></a><span data-ttu-id="ce399-102">Nasıl yapılır: Hizmet Uç Noktalarına Meta Verileri İçe Aktarma</span><span class="sxs-lookup"><span data-stu-id="ce399-102">How to: Import Metadata into Service Endpoints</span></span>
<span data-ttu-id="ce399-103">Bu konuda, bir hizmet uç noktası koleksiyonuna meta verilerin nasıl içeri aktarılacağı ve [Başlarken](../samples/getting-started-sample.md)' de tanımlanan hizmetin nasıl kullanılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ce399-103">This topic explains how to import metadata into a collection of service endpoints and use the service defined in the [Getting Started](../samples/getting-started-sample.md).</span></span> <span data-ttu-id="ce399-104">Bu konuda, hizmetten meta verileri içeri aktaran ve sonra hizmette yöntemi çağıran bir istemci uygulamasının nasıl oluşturulacağı gösterilmektedir `Add` .</span><span class="sxs-lookup"><span data-stu-id="ce399-104">This topic show how to create a client application that imports metadata from the service and then calls the `Add` method on the service.</span></span>  
  
### <a name="to-import-metadata-into-service-endpoints"></a><span data-ttu-id="ce399-105">Meta verileri hizmet uç noktalarına aktarmak için</span><span class="sxs-lookup"><span data-stu-id="ce399-105">To import metadata into service endpoints</span></span>  
  
1. <span data-ttu-id="ce399-106">Bir <xref:System.ServiceModel.EndpointAddress> nesne bildirin ve hizmetin meta veri değişimi (MEX) adresi Için Tekdüzen Kaynak tanımlayıcısı (URI) ile başlatın.</span><span class="sxs-lookup"><span data-stu-id="ce399-106">Declare an <xref:System.ServiceModel.EndpointAddress> object and initialize it with the Uniform Resource Identifier (URI) for the metadata exchange (MEX) address of the service.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#0)]  
  
2. <span data-ttu-id="ce399-107">Bir oluşturun <xref:System.ServiceModel.Description.MetadataExchangeClient> , MEX adresini geçirerek ve çağırın <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> .</span><span class="sxs-lookup"><span data-stu-id="ce399-107">Create a <xref:System.ServiceModel.Description.MetadataExchangeClient>, passing in the MEX address, and call <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A>.</span></span> <span data-ttu-id="ce399-108">Bu, hizmetten meta verileri alır.</span><span class="sxs-lookup"><span data-stu-id="ce399-108">This retrieves the metadata from the service.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#1)]  
  
3. <span data-ttu-id="ce399-109"><xref:System.ServiceModel.Description.WsdlImporter>Daha önce alınan meta verileri geçirerek bir oluşturun ve çağırın <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A> .</span><span class="sxs-lookup"><span data-stu-id="ce399-109">Create a <xref:System.ServiceModel.Description.WsdlImporter>, passing in the metadata previously retrieved, and call <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>.</span></span> <span data-ttu-id="ce399-110">Bu bir nesne koleksiyonu oluşturur <xref:System.ServiceModel.Description.ContractDescription> .</span><span class="sxs-lookup"><span data-stu-id="ce399-110">This generates a collection of <xref:System.ServiceModel.Description.ContractDescription> objects.</span></span> <span data-ttu-id="ce399-111"><xref:System.ServiceModel.Description.WsdlImporter.ImportAllEndpoints%2A> <xref:System.ServiceModel.Description.WsdlImporter.ImportAllBindings%2A> Gereksinimlerinize bağlı olarak, veya öğesini de çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ce399-111">You could also call <xref:System.ServiceModel.Description.WsdlImporter.ImportAllEndpoints%2A> or <xref:System.ServiceModel.Description.WsdlImporter.ImportAllBindings%2A>, depending upon your needs.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#2)]  
  
    > [!NOTE]
    > <span data-ttu-id="ce399-112">Meta verileri içeri aktardıktan sonra, bir istemci kanalı oluşturamaz veya meta verileri dışarı aktarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ce399-112">After you have imported the metadata, you will not be able to create a client channel or export the metadata.</span></span> <span data-ttu-id="ce399-113">Bunun nedeni, bu noktada hiçbir tür bilgisinin mevcut olmaması değildir.</span><span class="sxs-lookup"><span data-stu-id="ce399-113">This is because no type information is available at this point.</span></span> <span data-ttu-id="ce399-114">Hizmet veya dışarı aktarma meta verileriyle etkileşim kurmak için tür bilgileri gereklidir.</span><span class="sxs-lookup"><span data-stu-id="ce399-114">Type information is required to actually interact with the service or export metadata.</span></span> <span data-ttu-id="ce399-115">Tür bilgilerini oluşturmak için, 4 ve 5. adımlarda gösterilen kodu oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ce399-115">To generate the type information, you need to generate code, shown in steps 4 and 5.</span></span> <span data-ttu-id="ce399-116">Alternatif olarak, <xref:System.ServiceModel.Description.MetadataResolver> yardımcı sınıfını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ce399-116">Alternatively, you could use the <xref:System.ServiceModel.Description.MetadataResolver> helper class.</span></span> <span data-ttu-id="ce399-117">Daha fazla bilgi için bkz. [nasıl yapılır: MetadataResolver kullanarak bağlama meta verilerini dinamik olarak elde](how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically.md)edin.</span><span class="sxs-lookup"><span data-stu-id="ce399-117">For more information, see [How to: Use MetadataResolver to Obtain Binding Metadata Dynamically](how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically.md).</span></span>  
  
4. <span data-ttu-id="ce399-118">Her sözleşme için tür bilgisi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ce399-118">Generate type information for each contract.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#3)]  
  
5. <span data-ttu-id="ce399-119">Artık bu bilgileri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ce399-119">Now you can use this information.</span></span> <span data-ttu-id="ce399-120">Aşağıdaki örnek C# kaynak kodu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ce399-120">The following sample generates C# source code.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#4)]  
  
## <a name="see-also"></a><span data-ttu-id="ce399-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ce399-121">See also</span></span>

- [<span data-ttu-id="ce399-122">Meta Veriler</span><span class="sxs-lookup"><span data-stu-id="ce399-122">Metadata</span></span>](metadata.md)
- [<span data-ttu-id="ce399-123">Başlarken</span><span class="sxs-lookup"><span data-stu-id="ce399-123">Getting Started</span></span>](../samples/getting-started-sample.md)
