---
title: 'Nasıl yapılır: Hizmet Uç Noktalarından Meta Verileri Dışa Aktarma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b6c4dfd0-f270-43ec-961a-e16eb6af2f2c
ms.openlocfilehash: c253358b68cf18a23bab4d12d4ad760874103bff
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96246413"
---
# <a name="how-to-export-metadata-from-service-endpoints"></a><span data-ttu-id="aa53a-102">Nasıl yapılır: Hizmet Uç Noktalarından Meta Verileri Dışa Aktarma</span><span class="sxs-lookup"><span data-stu-id="aa53a-102">How to: Export Metadata from Service Endpoints</span></span>

<span data-ttu-id="aa53a-103">Bu konuda, hizmet uç noktalarından meta verilerin nasıl dışarı aktarılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="aa53a-103">This topic explains how to export metadata from service endpoints.</span></span>  
  
### <a name="to-export-metadata-from-service-endpoints"></a><span data-ttu-id="aa53a-104">Meta verileri hizmet uç noktalarından dışarı aktarmak için</span><span class="sxs-lookup"><span data-stu-id="aa53a-104">To export metadata from service endpoints</span></span>  
  
1. <span data-ttu-id="aa53a-105">Yeni bir Visual Studio konsol uygulaması projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="aa53a-105">Create a new Visual Studio Console App Project.</span></span> <span data-ttu-id="aa53a-106">Main () yönteminde oluşturulan Program.cs dosyasına aşağıdaki adımlarda gösterilen kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="aa53a-106">Add the code shown in the following steps in the generated Program.cs file within the main() method.</span></span>  
  
2. <span data-ttu-id="aa53a-107">Oluşturun <xref:System.ServiceModel.Description.WsdlExporter> .</span><span class="sxs-lookup"><span data-stu-id="aa53a-107">Create a <xref:System.ServiceModel.Description.WsdlExporter>.</span></span>  
  
     [!code-csharp[S_UEWsdlExporter#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#1)]
     [!code-vb[S_UEWsdlExporter#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#1)]  
  
3. <span data-ttu-id="aa53a-108"><xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A>Özelliğini Numaralandırmadaki değerlerden birine ayarlayın <xref:System.ServiceModel.Description.PolicyVersion> .</span><span class="sxs-lookup"><span data-stu-id="aa53a-108">Set the <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> property to one of the values from the <xref:System.ServiceModel.Description.PolicyVersion> enumeration.</span></span> <span data-ttu-id="aa53a-109">Bu örnek, <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> 1,5 WS-Policy karşılık gelen değeri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="aa53a-109">This sample sets the value to <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> which corresponds to WS-Policy 1.5.</span></span>  
  
     [!code-csharp[S_UEWsdlExporter#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#2)]
     [!code-vb[S_UEWsdlExporter#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#2)]  
  
4. <span data-ttu-id="aa53a-110">Nesne dizisi oluşturun <xref:System.ServiceModel.Description.ServiceEndpoint> .</span><span class="sxs-lookup"><span data-stu-id="aa53a-110">Create an array of <xref:System.ServiceModel.Description.ServiceEndpoint> objects.</span></span>  
  
     [!code-csharp[S_UEWsdlExporter#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#3)]
     [!code-vb[S_UEWsdlExporter#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#3)]  
  
5. <span data-ttu-id="aa53a-111">Her hizmet uç noktası için meta verileri dışarı aktarın.</span><span class="sxs-lookup"><span data-stu-id="aa53a-111">Export metadata for each service endpoint.</span></span>  
  
     [!code-csharp[S_UEWsdlExporter#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#4)]
     [!code-vb[S_UEWsdlExporter#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#4)]  
  
6. <span data-ttu-id="aa53a-112">Dışarı aktarma işlemi sırasında bir hata olmadığından emin olun ve meta verileri alın.</span><span class="sxs-lookup"><span data-stu-id="aa53a-112">Check to make sure no errors occurred during the export process and retrieve the metadata.</span></span>  
  
     [!code-csharp[S_UEWsdlExporter#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#5)]
     [!code-vb[S_UEWsdlExporter#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#5)]  
  
7. <span data-ttu-id="aa53a-113">Artık, yöntemini çağırarak bir dosyaya yazmak gibi meta verileri kullanabilirsiniz <xref:System.ServiceModel.Description.MetadataSet.WriteTo%28System.Xml.XmlWriter%29> .</span><span class="sxs-lookup"><span data-stu-id="aa53a-113">You can now use the metadata, such as write it to a file by calling the <xref:System.ServiceModel.Description.MetadataSet.WriteTo%28System.Xml.XmlWriter%29> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa53a-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="aa53a-114">Example</span></span>  

 <span data-ttu-id="aa53a-115">Bu örnek için tam kod listesi aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="aa53a-115">The following is the full code listing for this example.</span></span>  
  
 [!code-csharp[S_UEWsdlExporter#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#0)]
 [!code-vb[S_UEWsdlExporter#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="aa53a-116">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="aa53a-116">Compiling the Code</span></span>  

 <span data-ttu-id="aa53a-117">Program.cs Reference System.ServiceModel.dll derlenirken.</span><span class="sxs-lookup"><span data-stu-id="aa53a-117">When compiling Program.cs reference System.ServiceModel.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa53a-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aa53a-118">See also</span></span>

- [<span data-ttu-id="aa53a-119">Meta Veri Mimarisi Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="aa53a-119">Metadata Architecture Overview</span></span>](metadata-architecture-overview.md)
- [<span data-ttu-id="aa53a-120">Meta Verileri Kullanma</span><span class="sxs-lookup"><span data-stu-id="aa53a-120">Using Metadata</span></span>](using-metadata.md)
- [<span data-ttu-id="aa53a-121">Uç Noktalar: Adresler, Bağlamalar ve Sözleşmeler</span><span class="sxs-lookup"><span data-stu-id="aa53a-121">Endpoints: Addresses, Bindings, and Contracts</span></span>](endpoints-addresses-bindings-and-contracts.md)
