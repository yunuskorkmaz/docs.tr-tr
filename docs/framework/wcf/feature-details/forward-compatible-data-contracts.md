---
title: "İleri Uyumlu Veri Sözleşmeleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: data contracts [WCF], forward compatibility
ms.assetid: 413c9044-26f8-4ecb-968c-18495ea52cd9
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5ffd4a09de508a2353af356863f9e4f41fc253e8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="forward-compatible-data-contracts"></a><span data-ttu-id="4744b-102">İleri Uyumlu Veri Sözleşmeleri</span><span class="sxs-lookup"><span data-stu-id="4744b-102">Forward-Compatible Data Contracts</span></span>
<span data-ttu-id="4744b-103">Bir özellik olan [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] veri sözleşmesi sistemidir sözleşmeleri bölünemez yollarla zamanla gelişmesi.</span><span class="sxs-lookup"><span data-stu-id="4744b-103">A feature of the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] data contract system is that contracts can evolve over time in nonbreaking ways.</span></span> <span data-ttu-id="4744b-104">Diğer bir deyişle, bir istemci bir veri sözleşmesi daha eski bir sürümü ile aynı veri sözleşmesi daha yeni bir sürümü olan bir hizmeti ile iletişim kurabilir veya bir istemci bir veri sözleşmesi daha yeni bir sürümü ile aynı veri sözleşmesi daha eski bir sürümü ile iletişim kurabilir.</span><span class="sxs-lookup"><span data-stu-id="4744b-104">That is, a client with an older version of a data contract can communicate with a service with a newer version of the same data contract, or a client with a newer version of a data contract can communicate with an older version of the same data contract.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="4744b-105">[En iyi uygulamalar: veri sözleşmesi sürümü oluşturma](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md).</span><span class="sxs-lookup"><span data-stu-id="4744b-105"> [Best Practices: Data Contract Versioning](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md).</span></span>  
  
 <span data-ttu-id="4744b-106">Var olan bir veri sözleşmeyi yeni sürümlerini oluşturduğunuzda gerektiği ölçüde temeline göre sürüm oluşturma özelliklerinin çoğu uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4744b-106">You can apply most of the versioning features on an as-needed basis when new versions of an existing data contract are created.</span></span> <span data-ttu-id="4744b-107">Ancak, tek bir sürüm oluşturma özelliği *gidiş*, ilk sürüm türünden düzgün çalışması için yerleşik gerekir.</span><span class="sxs-lookup"><span data-stu-id="4744b-107">However, one versioning feature, *round-tripping*, must be built into the type from the first version in order to work properly.</span></span>  
  
## <a name="round-tripping"></a><span data-ttu-id="4744b-108">Gidiş</span><span class="sxs-lookup"><span data-stu-id="4744b-108">Round-Tripping</span></span>  
 <span data-ttu-id="4744b-109">Eski bir sürümüne ve tekrar yeni bir veri sözleşmesi sürümü yeni bir sürümden verileri geçirmeden gidiş oluşur.</span><span class="sxs-lookup"><span data-stu-id="4744b-109">Round-tripping occurs when data passes from a new version to an old version and back to the new version of a data contract.</span></span> <span data-ttu-id="4744b-110">Gidiş veri kaybı olmamasına güvence altına alır.</span><span class="sxs-lookup"><span data-stu-id="4744b-110">Round-tripping guarantees that no data is lost.</span></span> <span data-ttu-id="4744b-111">Gidiş etkinleştirme türü ileri uyumlu veri sözleşmesi sürümü oluşturma modeli tarafından desteklenen herhangi bir gelecekteki değişiklikle hale getirir.</span><span class="sxs-lookup"><span data-stu-id="4744b-111">Enabling round-tripping makes the type forward-compatible with any future changes supported by the data contract versioning model.</span></span>  
  
 <span data-ttu-id="4744b-112">Belirli bir tür için gidiş etkinleştirmek için türü uygulamalıdır <xref:System.Runtime.Serialization.IExtensibleDataObject> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="4744b-112">To enable round-tripping for a particular type, the type must implement the <xref:System.Runtime.Serialization.IExtensibleDataObject> interface.</span></span> <span data-ttu-id="4744b-113">Bir özellik arabirimi içerir <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> (döndürme <xref:System.Runtime.Serialization.ExtensionDataObject> türü).</span><span class="sxs-lookup"><span data-stu-id="4744b-113">The interface contains one property, <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> (returning the <xref:System.Runtime.Serialization.ExtensionDataObject> type).</span></span> <span data-ttu-id="4744b-114">Özelliği için geçerli sürümü bilinmiyor veri sözleşmesi gelecek sürümlerinden herhangi bir veri depolar.</span><span class="sxs-lookup"><span data-stu-id="4744b-114">The property stores any data from future versions of the data contract that is unknown to the current version.</span></span>  
  
### <a name="example"></a><span data-ttu-id="4744b-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="4744b-115">Example</span></span>  
 <span data-ttu-id="4744b-116">Aşağıdaki veri sözleşmesi gelecekteki değişikliklerle İleri uyumlu değil.</span><span class="sxs-lookup"><span data-stu-id="4744b-116">The following data contract is not forward-compatible with future changes.</span></span>  
  
 [!code-csharp[C_DataContract#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#7)]
 [!code-vb[C_DataContract#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#7)]  
  
 <span data-ttu-id="4744b-117">Türü (örneğin, "phoneNumber" adlı yeni bir veri üye ekleme) gelecekteki değişiklikler ile uyumlu hale getirmek için uygulama <xref:System.Runtime.Serialization.IExtensibleDataObject> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="4744b-117">To make the type compatible with future changes (such as adding a new data member named "phoneNumber"), implement the <xref:System.Runtime.Serialization.IExtensibleDataObject> interface.</span></span>  
  
 [!code-csharp[C_DataContract#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#8)]
 [!code-vb[C_DataContract#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#8)]  
  
 <span data-ttu-id="4744b-118">Zaman [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] altyapı özgün veri sözleşmenin parçası olmayan veriler karşılaştığında, veriler özellikte depolanan ve korunur.</span><span class="sxs-lookup"><span data-stu-id="4744b-118">When the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infrastructure encounters data that is not part of the original data contract, the data is stored in the property and preserved.</span></span> <span data-ttu-id="4744b-119">Geçici depolama dışında herhangi bir şekilde işlenmez.</span><span class="sxs-lookup"><span data-stu-id="4744b-119">It is not processed in any other way except for temporary storage.</span></span> <span data-ttu-id="4744b-120">Nesne geri onu başlatıldığı için döndürülürse, özgün (bilinmiyor) verileri de döndürülür.</span><span class="sxs-lookup"><span data-stu-id="4744b-120">If the object is returned back to where it originated, the original (unknown) data is also returned.</span></span> <span data-ttu-id="4744b-121">Bu nedenle, veri kaybı olmadan kaynak uç noktası gelen ve giden gidiş dönüş yaptı.</span><span class="sxs-lookup"><span data-stu-id="4744b-121">Therefore, the data has made a round trip to and from the originating endpoint without loss.</span></span> <span data-ttu-id="4744b-122">Ancak, kaynak uç noktası işlenecek verileri gerekirse, bu Beklenti unmet, olduğunu unutmayın ve uç nokta gerekir şekilde algılamak ve değişiklik uyum sağlamak.</span><span class="sxs-lookup"><span data-stu-id="4744b-122">Note, however, that if the originating endpoint required the data to be processed, that expectation is unmet, and the endpoint must somehow detect and accommodate the change.</span></span>  
  
 <span data-ttu-id="4744b-123"><xref:System.Runtime.Serialization.ExtensionDataObject> Türü, genel yöntemleri ya da özellikleri içerir.</span><span class="sxs-lookup"><span data-stu-id="4744b-123">The <xref:System.Runtime.Serialization.ExtensionDataObject> type contains no public methods or properties.</span></span> <span data-ttu-id="4744b-124">Bu nedenle, içinde depolanan verilere doğrudan erişmek mümkün değildir <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="4744b-124">Thus, it is impossible to get direct access to the data stored inside the <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> property.</span></span>  
  
 <span data-ttu-id="4744b-125">Gidiş özelliğini ayarlayarak ya da kapalı `ignoreExtensionDataObject` için `true` içinde <xref:System.Runtime.Serialization.DataContractSerializer> Oluşturucusu veya ayarlayarak <xref:System.ServiceModel.ServiceBehaviorAttribute.IgnoreExtensionDataObject%2A> özelliğine `true` üzerinde <xref:System.ServiceModel.ServiceBehaviorAttribute>.</span><span class="sxs-lookup"><span data-stu-id="4744b-125">The round-tripping feature may be turned off, either by setting `ignoreExtensionDataObject` to `true` in the <xref:System.Runtime.Serialization.DataContractSerializer> constructor or by setting the <xref:System.ServiceModel.ServiceBehaviorAttribute.IgnoreExtensionDataObject%2A> property to `true` on the <xref:System.ServiceModel.ServiceBehaviorAttribute>.</span></span> <span data-ttu-id="4744b-126">Bu özellik devre dışı olduğunda seri durumdan çıkarıcının değil doldurmak <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> özelliği ve seri hale getirici değil yayma özelliğinin içeriği.</span><span class="sxs-lookup"><span data-stu-id="4744b-126">When this feature is off, the deserializer will not populate the <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> property, and the serializer will not emit the contents of the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4744b-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4744b-127">See Also</span></span>  
 <xref:System.Runtime.Serialization.IExtensibleDataObject>  
 <xref:System.Runtime.Serialization.ExtensionDataObject>  
 [<span data-ttu-id="4744b-128">Veri Anlaşması Sürümü Oluşturma</span><span class="sxs-lookup"><span data-stu-id="4744b-128">Data Contract Versioning</span></span>](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md)  
 [<span data-ttu-id="4744b-129">En İyi Uygulamalar: Veri Sözleşmesi Sürümü Oluşturma</span><span class="sxs-lookup"><span data-stu-id="4744b-129">Best Practices: Data Contract Versioning</span></span>](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md)
