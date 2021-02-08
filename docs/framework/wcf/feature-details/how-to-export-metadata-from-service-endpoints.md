---
description: 'Daha fazla bilgi: nasıl yapılır: hizmet uç noktalarından meta verileri dışarı aktarma'
title: 'Nasıl yapılır: Hizmet Uç Noktalarından Meta Verileri Dışa Aktarma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b6c4dfd0-f270-43ec-961a-e16eb6af2f2c
ms.openlocfilehash: f690d2dc0bd3ac0f89e527412a63ce0967daa8f6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802885"
---
# <a name="how-to-export-metadata-from-service-endpoints"></a><span data-ttu-id="2aec1-103">Nasıl yapılır: Hizmet Uç Noktalarından Meta Verileri Dışa Aktarma</span><span class="sxs-lookup"><span data-stu-id="2aec1-103">How to: Export Metadata from Service Endpoints</span></span>

<span data-ttu-id="2aec1-104">Bu konuda, hizmet uç noktalarından meta verilerin nasıl dışarı aktarılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2aec1-104">This topic explains how to export metadata from service endpoints.</span></span>  
  
### <a name="to-export-metadata-from-service-endpoints"></a><span data-ttu-id="2aec1-105">Meta verileri hizmet uç noktalarından dışarı aktarmak için</span><span class="sxs-lookup"><span data-stu-id="2aec1-105">To export metadata from service endpoints</span></span>  
  
1. <span data-ttu-id="2aec1-106">Yeni bir Visual Studio konsol uygulaması projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2aec1-106">Create a new Visual Studio Console App Project.</span></span> <span data-ttu-id="2aec1-107">Main () yönteminde oluşturulan Program.cs dosyasına aşağıdaki adımlarda gösterilen kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2aec1-107">Add the code shown in the following steps in the generated Program.cs file within the main() method.</span></span>  
  
2. <span data-ttu-id="2aec1-108">Oluşturun <xref:System.ServiceModel.Description.WsdlExporter> .</span><span class="sxs-lookup"><span data-stu-id="2aec1-108">Create a <xref:System.ServiceModel.Description.WsdlExporter>.</span></span>  
  
     [!code-csharp[S_UEWsdlExporter#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#1)]
     [!code-vb[S_UEWsdlExporter#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#1)]  
  
3. <span data-ttu-id="2aec1-109"><xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A>Özelliğini Numaralandırmadaki değerlerden birine ayarlayın <xref:System.ServiceModel.Description.PolicyVersion> .</span><span class="sxs-lookup"><span data-stu-id="2aec1-109">Set the <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> property to one of the values from the <xref:System.ServiceModel.Description.PolicyVersion> enumeration.</span></span> <span data-ttu-id="2aec1-110">Bu örnek, <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> 1,5 WS-Policy karşılık gelen değeri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="2aec1-110">This sample sets the value to <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> which corresponds to WS-Policy 1.5.</span></span>  
  
     [!code-csharp[S_UEWsdlExporter#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#2)]
     [!code-vb[S_UEWsdlExporter#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#2)]  
  
4. <span data-ttu-id="2aec1-111">Nesne dizisi oluşturun <xref:System.ServiceModel.Description.ServiceEndpoint> .</span><span class="sxs-lookup"><span data-stu-id="2aec1-111">Create an array of <xref:System.ServiceModel.Description.ServiceEndpoint> objects.</span></span>  
  
     [!code-csharp[S_UEWsdlExporter#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#3)]
     [!code-vb[S_UEWsdlExporter#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#3)]  
  
5. <span data-ttu-id="2aec1-112">Her hizmet uç noktası için meta verileri dışarı aktarın.</span><span class="sxs-lookup"><span data-stu-id="2aec1-112">Export metadata for each service endpoint.</span></span>  
  
     [!code-csharp[S_UEWsdlExporter#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#4)]
     [!code-vb[S_UEWsdlExporter#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#4)]  
  
6. <span data-ttu-id="2aec1-113">Dışarı aktarma işlemi sırasında bir hata olmadığından emin olun ve meta verileri alın.</span><span class="sxs-lookup"><span data-stu-id="2aec1-113">Check to make sure no errors occurred during the export process and retrieve the metadata.</span></span>  
  
     [!code-csharp[S_UEWsdlExporter#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#5)]
     [!code-vb[S_UEWsdlExporter#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#5)]  
  
7. <span data-ttu-id="2aec1-114">Artık, yöntemini çağırarak bir dosyaya yazmak gibi meta verileri kullanabilirsiniz <xref:System.ServiceModel.Description.MetadataSet.WriteTo%28System.Xml.XmlWriter%29> .</span><span class="sxs-lookup"><span data-stu-id="2aec1-114">You can now use the metadata, such as write it to a file by calling the <xref:System.ServiceModel.Description.MetadataSet.WriteTo%28System.Xml.XmlWriter%29> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2aec1-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="2aec1-115">Example</span></span>  

 <span data-ttu-id="2aec1-116">Bu örnek için tam kod listesi aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="2aec1-116">The following is the full code listing for this example.</span></span>  
  
 [!code-csharp[S_UEWsdlExporter#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#0)]
 [!code-vb[S_UEWsdlExporter#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2aec1-117">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="2aec1-117">Compiling the Code</span></span>  

 <span data-ttu-id="2aec1-118">Program.cs Reference System.ServiceModel.dll derlenirken.</span><span class="sxs-lookup"><span data-stu-id="2aec1-118">When compiling Program.cs reference System.ServiceModel.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2aec1-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2aec1-119">See also</span></span>

- [<span data-ttu-id="2aec1-120">Meta Veri Mimarisi Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="2aec1-120">Metadata Architecture Overview</span></span>](metadata-architecture-overview.md)
- [<span data-ttu-id="2aec1-121">Meta Verileri Kullanma</span><span class="sxs-lookup"><span data-stu-id="2aec1-121">Using Metadata</span></span>](using-metadata.md)
- [<span data-ttu-id="2aec1-122">Uç Noktalar: Adresler, Bağlamalar ve Sözleşmeler</span><span class="sxs-lookup"><span data-stu-id="2aec1-122">Endpoints: Addresses, Bindings, and Contracts</span></span>](endpoints-addresses-bindings-and-contracts.md)
