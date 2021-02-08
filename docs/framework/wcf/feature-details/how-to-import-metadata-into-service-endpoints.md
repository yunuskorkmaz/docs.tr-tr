---
description: 'Daha fazla bilgi edinin: nasıl yapılır: meta verileri hizmet uç noktalarına aktarma'
title: 'Nasıl yapılır: Hizmet Uç Noktalarına Meta Verileri İçe Aktarma'
ms.date: 03/30/2017
ms.assetid: b69dbe20-92a1-4911-89d8-ffbc3dad4663
ms.openlocfilehash: d6e69b64c5f70a8e49ed6ee7c9ff319f5a639a30
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793746"
---
# <a name="how-to-import-metadata-into-service-endpoints"></a><span data-ttu-id="f4636-103">Nasıl yapılır: Hizmet Uç Noktalarına Meta Verileri İçe Aktarma</span><span class="sxs-lookup"><span data-stu-id="f4636-103">How to: Import Metadata into Service Endpoints</span></span>

<span data-ttu-id="f4636-104">Bu konuda, bir hizmet uç noktası koleksiyonuna meta verilerin nasıl içeri aktarılacağı ve [Başlarken](../samples/getting-started-sample.md)' de tanımlanan hizmetin nasıl kullanılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f4636-104">This topic explains how to import metadata into a collection of service endpoints and use the service defined in the [Getting Started](../samples/getting-started-sample.md).</span></span> <span data-ttu-id="f4636-105">Bu konuda, hizmetten meta verileri içeri aktaran ve sonra hizmette yöntemi çağıran bir istemci uygulamasının nasıl oluşturulacağı gösterilmektedir `Add` .</span><span class="sxs-lookup"><span data-stu-id="f4636-105">This topic show how to create a client application that imports metadata from the service and then calls the `Add` method on the service.</span></span>  
  
### <a name="to-import-metadata-into-service-endpoints"></a><span data-ttu-id="f4636-106">Meta verileri hizmet uç noktalarına aktarmak için</span><span class="sxs-lookup"><span data-stu-id="f4636-106">To import metadata into service endpoints</span></span>  
  
1. <span data-ttu-id="f4636-107">Bir <xref:System.ServiceModel.EndpointAddress> nesne bildirin ve hizmetin meta veri değişimi (MEX) adresi Için Tekdüzen Kaynak tanımlayıcısı (URI) ile başlatın.</span><span class="sxs-lookup"><span data-stu-id="f4636-107">Declare an <xref:System.ServiceModel.EndpointAddress> object and initialize it with the Uniform Resource Identifier (URI) for the metadata exchange (MEX) address of the service.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#0)]  
  
2. <span data-ttu-id="f4636-108">Bir oluşturun <xref:System.ServiceModel.Description.MetadataExchangeClient> , MEX adresini geçirerek ve çağırın <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> .</span><span class="sxs-lookup"><span data-stu-id="f4636-108">Create a <xref:System.ServiceModel.Description.MetadataExchangeClient>, passing in the MEX address, and call <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A>.</span></span> <span data-ttu-id="f4636-109">Bu, hizmetten meta verileri alır.</span><span class="sxs-lookup"><span data-stu-id="f4636-109">This retrieves the metadata from the service.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#1)]  
  
3. <span data-ttu-id="f4636-110"><xref:System.ServiceModel.Description.WsdlImporter>Daha önce alınan meta verileri geçirerek bir oluşturun ve çağırın <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A> .</span><span class="sxs-lookup"><span data-stu-id="f4636-110">Create a <xref:System.ServiceModel.Description.WsdlImporter>, passing in the metadata previously retrieved, and call <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>.</span></span> <span data-ttu-id="f4636-111">Bu bir nesne koleksiyonu oluşturur <xref:System.ServiceModel.Description.ContractDescription> .</span><span class="sxs-lookup"><span data-stu-id="f4636-111">This generates a collection of <xref:System.ServiceModel.Description.ContractDescription> objects.</span></span> <span data-ttu-id="f4636-112"><xref:System.ServiceModel.Description.WsdlImporter.ImportAllEndpoints%2A> <xref:System.ServiceModel.Description.WsdlImporter.ImportAllBindings%2A> Gereksinimlerinize bağlı olarak, veya öğesini de çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f4636-112">You could also call <xref:System.ServiceModel.Description.WsdlImporter.ImportAllEndpoints%2A> or <xref:System.ServiceModel.Description.WsdlImporter.ImportAllBindings%2A>, depending upon your needs.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#2)]  
  
    > [!NOTE]
    > <span data-ttu-id="f4636-113">Meta verileri içeri aktardıktan sonra, bir istemci kanalı oluşturamaz veya meta verileri dışarı aktarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f4636-113">After you have imported the metadata, you will not be able to create a client channel or export the metadata.</span></span> <span data-ttu-id="f4636-114">Bunun nedeni, bu noktada hiçbir tür bilgisinin mevcut olmaması değildir.</span><span class="sxs-lookup"><span data-stu-id="f4636-114">This is because no type information is available at this point.</span></span> <span data-ttu-id="f4636-115">Hizmet veya dışarı aktarma meta verileriyle etkileşim kurmak için tür bilgileri gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f4636-115">Type information is required to actually interact with the service or export metadata.</span></span> <span data-ttu-id="f4636-116">Tür bilgilerini oluşturmak için, 4 ve 5. adımlarda gösterilen kodu oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f4636-116">To generate the type information, you need to generate code, shown in steps 4 and 5.</span></span> <span data-ttu-id="f4636-117">Alternatif olarak, <xref:System.ServiceModel.Description.MetadataResolver> yardımcı sınıfını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f4636-117">Alternatively, you could use the <xref:System.ServiceModel.Description.MetadataResolver> helper class.</span></span> <span data-ttu-id="f4636-118">Daha fazla bilgi için bkz. [nasıl yapılır: MetadataResolver kullanarak bağlama meta verilerini dinamik olarak elde](how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically.md)edin.</span><span class="sxs-lookup"><span data-stu-id="f4636-118">For more information, see [How to: Use MetadataResolver to Obtain Binding Metadata Dynamically](how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically.md).</span></span>  
  
4. <span data-ttu-id="f4636-119">Her sözleşme için tür bilgisi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f4636-119">Generate type information for each contract.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#3)]  
  
5. <span data-ttu-id="f4636-120">Artık bu bilgileri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f4636-120">Now you can use this information.</span></span> <span data-ttu-id="f4636-121">Aşağıdaki örnek C# kaynak kodu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f4636-121">The following sample generates C# source code.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#4)]  
  
## <a name="see-also"></a><span data-ttu-id="f4636-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f4636-122">See also</span></span>

- [<span data-ttu-id="f4636-123">Meta veri</span><span class="sxs-lookup"><span data-stu-id="f4636-123">Metadata</span></span>](metadata.md)
- [<span data-ttu-id="f4636-124">Başlarken</span><span class="sxs-lookup"><span data-stu-id="f4636-124">Getting Started</span></span>](../samples/getting-started-sample.md)
