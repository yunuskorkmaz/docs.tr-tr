---
title: 'Nasıl yapılır: Hizmet Uç Noktalarından Meta Verileri Dışa Aktarma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b6c4dfd0-f270-43ec-961a-e16eb6af2f2c
ms.openlocfilehash: bd6543e1e22b7a2cb0b870fe2fdb34011f0d2a4f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59162795"
---
# <a name="how-to-export-metadata-from-service-endpoints"></a><span data-ttu-id="f31c5-102">Nasıl yapılır: Hizmet Uç Noktalarından Meta Verileri Dışa Aktarma</span><span class="sxs-lookup"><span data-stu-id="f31c5-102">How to: Export Metadata from Service Endpoints</span></span>
<span data-ttu-id="f31c5-103">Bu konu, hizmet uç noktalarından meta verileri dışarı aktarma açıklar.</span><span class="sxs-lookup"><span data-stu-id="f31c5-103">This topic explains how to export metadata from service endpoints.</span></span>  
  
### <a name="to-export-metadata-from-service-endpoints"></a><span data-ttu-id="f31c5-104">Hizmet uç noktalarından meta verileri dışarı aktarmak için</span><span class="sxs-lookup"><span data-stu-id="f31c5-104">To export metadata from service endpoints</span></span>  
  
1.  <span data-ttu-id="f31c5-105">Yeni Visual Studio konsol uygulama projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f31c5-105">Create a new Visual Studio Console App Project.</span></span> <span data-ttu-id="f31c5-106">Aşağıdaki adımlarda oluşturulan Program.cs dosyasındaki ana() yöntemi içinde gösterilen kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f31c5-106">Add the code shown in the following steps in the generated Program.cs file within the main() method.</span></span>  
  
2.  <span data-ttu-id="f31c5-107">Oluşturma bir <xref:System.ServiceModel.Description.WsdlExporter>.</span><span class="sxs-lookup"><span data-stu-id="f31c5-107">Create a <xref:System.ServiceModel.Description.WsdlExporter>.</span></span>  
  
     [!code-csharp[S_UEWsdlExporter#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#1)]
     [!code-vb[S_UEWsdlExporter#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#1)]  
  
3.  <span data-ttu-id="f31c5-108">Ayarlama <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> özellik değerlerinden birine <xref:System.ServiceModel.Description.PolicyVersion> sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="f31c5-108">Set the <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> property to one of the values from the <xref:System.ServiceModel.Description.PolicyVersion> enumeration.</span></span> <span data-ttu-id="f31c5-109">Bu örnek değeri ayarlar <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> WS-Policy 1.5 sürümüne karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="f31c5-109">This sample sets the value to <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> which corresponds to WS-Policy 1.5.</span></span>  
  
     [!code-csharp[S_UEWsdlExporter#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#2)]
     [!code-vb[S_UEWsdlExporter#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#2)]  
  
4.  <span data-ttu-id="f31c5-110">Bir dizi oluşturma <xref:System.ServiceModel.Description.ServiceEndpoint> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="f31c5-110">Create an array of <xref:System.ServiceModel.Description.ServiceEndpoint> objects.</span></span>  
  
     [!code-csharp[S_UEWsdlExporter#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#3)]
     [!code-vb[S_UEWsdlExporter#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#3)]  
  
5.  <span data-ttu-id="f31c5-111">Her hizmet uç noktası için meta verileri dışarı aktarın.</span><span class="sxs-lookup"><span data-stu-id="f31c5-111">Export metadata for each service endpoint.</span></span>  
  
     [!code-csharp[S_UEWsdlExporter#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#4)]
     [!code-vb[S_UEWsdlExporter#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#4)]  
  
6.  <span data-ttu-id="f31c5-112">Dışarı aktarma işlemi sırasında bir hata oluşmamıştır emin olun ve meta verilerini almak için bu seçeneği işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="f31c5-112">Check to make sure no errors occurred during the export process and retrieve the metadata.</span></span>  
  
     [!code-csharp[S_UEWsdlExporter#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#5)]
     [!code-vb[S_UEWsdlExporter#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#5)]  
  
7.  <span data-ttu-id="f31c5-113">Artık meta çağırarak bir dosyaya yazmak gibi kullanabileceğiniz <xref:System.ServiceModel.Description.MetadataSet.WriteTo%28System.Xml.XmlWriter%29> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f31c5-113">You can now use the metadata, such as write it to a file by calling the <xref:System.ServiceModel.Description.MetadataSet.WriteTo%28System.Xml.XmlWriter%29> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f31c5-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="f31c5-114">Example</span></span>  
 <span data-ttu-id="f31c5-115">Bu örnek için listeleme tam kod aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f31c5-115">The following is the full code listing for this example.</span></span>  
  
 [!code-csharp[S_UEWsdlExporter#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#0)]
 [!code-vb[S_UEWsdlExporter#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f31c5-116">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="f31c5-116">Compiling the Code</span></span>  
 <span data-ttu-id="f31c5-117">Program.cs başvuru System.ServiceModel.dll derlenirken.</span><span class="sxs-lookup"><span data-stu-id="f31c5-117">When compiling Program.cs reference System.ServiceModel.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f31c5-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f31c5-118">See also</span></span>

- [<span data-ttu-id="f31c5-119">Meta Veri Mimarisi Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f31c5-119">Metadata Architecture Overview</span></span>](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)
- [<span data-ttu-id="f31c5-120">Meta Verileri Kullanma</span><span class="sxs-lookup"><span data-stu-id="f31c5-120">Using Metadata</span></span>](../../../../docs/framework/wcf/feature-details/using-metadata.md)
- [<span data-ttu-id="f31c5-121">Uç Noktalar: Adresler, Bağlamalar ve Sözleşmeler</span><span class="sxs-lookup"><span data-stu-id="f31c5-121">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
