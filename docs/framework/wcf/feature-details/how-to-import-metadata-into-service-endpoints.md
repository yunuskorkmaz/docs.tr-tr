---
title: 'Nasıl yapılır: Hizmet Uç Noktalarına Meta Verileri İçe Aktarma'
ms.date: 03/30/2017
ms.assetid: b69dbe20-92a1-4911-89d8-ffbc3dad4663
ms.openlocfilehash: afee3f2236db99b14c0e840d987e4862a260568e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62047834"
---
# <a name="how-to-import-metadata-into-service-endpoints"></a><span data-ttu-id="5340c-102">Nasıl yapılır: Hizmet Uç Noktalarına Meta Verileri İçe Aktarma</span><span class="sxs-lookup"><span data-stu-id="5340c-102">How to: Import Metadata into Service Endpoints</span></span>
<span data-ttu-id="5340c-103">Bu konu başlığında, tanımlanan hizmet meta verileri, hizmet uç noktaları bir koleksiyona içe aktarma ve açıklanmaktadır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="5340c-103">This topic explains how to import metadata into a collection of service endpoints and use the service defined in the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="5340c-104">Bu konuda hizmet ve çağrıları meta veri aktaran bir istemci uygulamanın nasıl oluşturulacağını gösterir `Add` hizmette yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5340c-104">This topic show how to create a client application that imports metadata from the service and then calls the `Add` method on the service.</span></span>  
  
### <a name="to-import-metadata-into-service-endpoints"></a><span data-ttu-id="5340c-105">Hizmet uç noktalarına meta verileri içeri aktarmak için</span><span class="sxs-lookup"><span data-stu-id="5340c-105">To import metadata into service endpoints</span></span>  
  
1. <span data-ttu-id="5340c-106">Bildirme bir <xref:System.ServiceModel.EndpointAddress> nesne ve ile Tekdüzen Kaynak Tanımlayıcısı (URI) hizmeti meta veri değişimi (MEX) adresi için başlatılamıyor.</span><span class="sxs-lookup"><span data-stu-id="5340c-106">Declare an <xref:System.ServiceModel.EndpointAddress> object and initialize it with the Uniform Resource Identifier (URI) for the metadata exchange (MEX) address of the service.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#0)]  
  
2. <span data-ttu-id="5340c-107">Oluşturma bir <xref:System.ServiceModel.Description.MetadataExchangeClient>, geçen MEX adresa ve çağrı <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A>.</span><span class="sxs-lookup"><span data-stu-id="5340c-107">Create a <xref:System.ServiceModel.Description.MetadataExchangeClient>, passing in the MEX address, and call <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A>.</span></span> <span data-ttu-id="5340c-108">Bu hizmet meta verileri alır.</span><span class="sxs-lookup"><span data-stu-id="5340c-108">This retrieves the metadata from the service.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#1)]  
  
3. <span data-ttu-id="5340c-109">Oluşturma bir <xref:System.ServiceModel.Description.WsdlImporter>, daha önce listelene meta verileri ve çağrı geçen <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>.</span><span class="sxs-lookup"><span data-stu-id="5340c-109">Create a <xref:System.ServiceModel.Description.WsdlImporter>, passing in the metadata previously retrieved, and call <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>.</span></span> <span data-ttu-id="5340c-110">Bu işlem bir koleksiyonunu oluşturur. <xref:System.ServiceModel.Description.ContractDescription> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="5340c-110">This generates a collection of <xref:System.ServiceModel.Description.ContractDescription> objects.</span></span> <span data-ttu-id="5340c-111">Ayrıca çağırabilir <xref:System.ServiceModel.Description.WsdlImporter.ImportAllEndpoints%2A> veya <xref:System.ServiceModel.Description.WsdlImporter.ImportAllBindings%2A>, ihtiyaçlarınıza bağlı.</span><span class="sxs-lookup"><span data-stu-id="5340c-111">You could also call <xref:System.ServiceModel.Description.WsdlImporter.ImportAllEndpoints%2A> or <xref:System.ServiceModel.Description.WsdlImporter.ImportAllBindings%2A>, depending upon your needs.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#2)]  
  
    > [!NOTE]
    >  <span data-ttu-id="5340c-112">Meta verileri içeri aktardıktan sonra istemci bir kanal oluşturmak veya meta veri dışarı aktarmak mümkün olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="5340c-112">After you have imported the metadata, you will not be able to create a client channel or export the metadata.</span></span> <span data-ttu-id="5340c-113">Bu noktada kullanılabilir türü bilgi olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="5340c-113">This is because no type information is available at this point.</span></span> <span data-ttu-id="5340c-114">Tür bilgilerini gerçekten hizmetiyle etkileşim kurmak veya meta veri dışarı aktarmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="5340c-114">Type information is required to actually interact with the service or export metadata.</span></span> <span data-ttu-id="5340c-115">Tür bilgisi üretmek için 4 ve 5. adımda gösterilen kodu oluşturmak gerekir.</span><span class="sxs-lookup"><span data-stu-id="5340c-115">To generate the type information, you need to generate code, shown in steps 4 and 5.</span></span> <span data-ttu-id="5340c-116">Alternatif olarak, kullanabileceğinizi <xref:System.ServiceModel.Description.MetadataResolver> yardımcı sınıfı.</span><span class="sxs-lookup"><span data-stu-id="5340c-116">Alternatively, you could use the <xref:System.ServiceModel.Description.MetadataResolver> helper class.</span></span> <span data-ttu-id="5340c-117">Daha fazla bilgi için [nasıl yapılır: Dinamik olarak meta verilerini almak için MetadataResolver kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically.md).</span><span class="sxs-lookup"><span data-stu-id="5340c-117">For more information, see [How to: Use MetadataResolver to Obtain Binding Metadata Dynamically](../../../../docs/framework/wcf/feature-details/how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically.md).</span></span>  
  
4. <span data-ttu-id="5340c-118">Her sözleşme için tür bilgisi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5340c-118">Generate type information for each contract.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#3)]  
  
5. <span data-ttu-id="5340c-119">Artık bu bilgileri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5340c-119">Now you can use this information.</span></span> <span data-ttu-id="5340c-120">Aşağıdaki örnek oluşturur C# kaynak kodu.</span><span class="sxs-lookup"><span data-stu-id="5340c-120">The following sample generates C# source code.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#4)]  
  
## <a name="see-also"></a><span data-ttu-id="5340c-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5340c-121">See also</span></span>

- [<span data-ttu-id="5340c-122">Meta Veriler</span><span class="sxs-lookup"><span data-stu-id="5340c-122">Metadata</span></span>](../../../../docs/framework/wcf/feature-details/metadata.md)
- [<span data-ttu-id="5340c-123">Başlarken</span><span class="sxs-lookup"><span data-stu-id="5340c-123">Getting Started</span></span>](../../../../docs/framework/wcf/samples/getting-started-sample.md)
