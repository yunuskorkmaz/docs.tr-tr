---
title: Veri Sözleşmesi Eşitliği
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], equivalence
ms.assetid: f06f3c7e-c235-4ec1-b200-68142edf1ed1
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9d4463a04ac2113778d9ea0d315beeef7d564764
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="data-contract-equivalence"></a><span data-ttu-id="efebb-102">Veri Sözleşmesi Eşitliği</span><span class="sxs-lookup"><span data-stu-id="efebb-102">Data Contract Equivalence</span></span>
<span data-ttu-id="efebb-103">Bir hizmeti veya başarılı bir şekilde bir istemciye veri göndermek için bir hizmeti belirli bir türde veri başarıyla göndermek bir istemci için gönderilen türü mutlaka alan tarafta mevcut gerekmez.</span><span class="sxs-lookup"><span data-stu-id="efebb-103">For a client to successfully send data of a certain type to a service, or a service to successfully send data to a client, the sent type does not necessarily have to exist on the receiving end.</span></span> <span data-ttu-id="efebb-104">Veri sözleşmeleri her iki türdeki eşdeğer tek gereksinimdir.</span><span class="sxs-lookup"><span data-stu-id="efebb-104">The only requirement is that the data contracts of both types be equivalent.</span></span> <span data-ttu-id="efebb-105">(Bazı durumlarda, katı eşdeğer anlatıldığı gibi gerekli değil [veri sözleşmesi sürümü oluşturma](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md).)</span><span class="sxs-lookup"><span data-stu-id="efebb-105">(Sometimes, strict equivalence is not required, as discussed in [Data Contract Versioning](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md).)</span></span>  
  
 <span data-ttu-id="efebb-106">Veri sözleşmeleri eşdeğer olarak aynı ad alanına ve ada sahip oldukları gerekir.</span><span class="sxs-lookup"><span data-stu-id="efebb-106">For data contracts to be equivalent, they must have the same namespace and name.</span></span> <span data-ttu-id="efebb-107">Ayrıca, her veri üyesi bir tarafında diğer tarafta bir eşdeğer veri üyesi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="efebb-107">Additionally, each data member on one side must have an equivalent data member on the other side.</span></span>  
  
 <span data-ttu-id="efebb-108">Veri üyeleri eşdeğer olarak aynı ada sahip oldukları gerekir.</span><span class="sxs-lookup"><span data-stu-id="efebb-108">For data members to be equivalent, they must have the same name.</span></span> <span data-ttu-id="efebb-109">Ayrıca, aynı veri türünü temsil etmelidir; diğer bir deyişle, kendi veri sözleşmeleri eşdeğer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="efebb-109">Additionally, they must represent the same type of data; that is, their data contracts must be equivalent.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="efebb-110">Verileri veri üye adları, yanı sıra adları ve ad alanları sözleşme Not büyük küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="efebb-110">Note that data contract names and namespaces, as well as data member names, are case-sensitive.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="efebb-111"> veri sözleşmesi adları ve ad alanları yanı sıra, bkz: veri üye adı [veri sözleşmesi adları](../../../../docs/framework/wcf/feature-details/data-contract-names.md).</span><span class="sxs-lookup"><span data-stu-id="efebb-111"> data contract names and namespaces, as well as data member names, see [Data Contract Names](../../../../docs/framework/wcf/feature-details/data-contract-names.md).</span></span>  
  
 <span data-ttu-id="efebb-112">İki tür mevcutsa aynı tarafında (gönderen veya alıcı) ve kendi veri sözleşmeleri eşdeğer değildir (örneğin, farklı veri üyelerinin sahip oldukları), siz bunları aynı ad ve ad vermemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="efebb-112">If two types exist on the same side (sender or receiver) and their data contracts are not equivalent (for example, they have different data members), you should not give them the same name and namespace.</span></span> <span data-ttu-id="efebb-113">Bunun yapılması, özel durum oluşturulmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="efebb-113">Doing so may cause exceptions to be thrown.</span></span>  
  
 <span data-ttu-id="efebb-114">Veri sözleşmeleri aşağıdaki türleri için eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="efebb-114">The data contracts for the following types are equivalent:</span></span>  
  
 [!code-csharp[C_DataContractNames#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#5)]
 [!code-vb[C_DataContractNames#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#5)]  
  
## <a name="data-member-order-and-data-contract-equivalence"></a><span data-ttu-id="efebb-115">Veri üye sırası ve veri sözleşmesi eşdeğer</span><span class="sxs-lookup"><span data-stu-id="efebb-115">Data Member Order and Data Contract equivalence</span></span>  
 <span data-ttu-id="efebb-116">Kullanarak <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> özelliği <xref:System.Runtime.Serialization.DataMemberAttribute> sınıfı, veri sözleşmesi eşitliği etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="efebb-116">Using the <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> property of the <xref:System.Runtime.Serialization.DataMemberAttribute> class may affect data contract equivalence.</span></span> <span data-ttu-id="efebb-117">Veri sözleşmeleri eşdeğer olarak aynı sırada görünür üyeleri olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="efebb-117">The data contracts must have members that appear in the same order to be equivalent.</span></span> <span data-ttu-id="efebb-118">Varsayılan olarak alfabetik sırasıdır.</span><span class="sxs-lookup"><span data-stu-id="efebb-118">The default order is alphabetical.</span></span> <span data-ttu-id="efebb-119">Daha fazla bilgi için bkz: [veri üye sırası](../../../../docs/framework/wcf/feature-details/data-member-order.md).</span><span class="sxs-lookup"><span data-stu-id="efebb-119">For more information, see [Data Member Order](../../../../docs/framework/wcf/feature-details/data-member-order.md).</span></span>  
  
 <span data-ttu-id="efebb-120">Örneğin, aşağıdaki kodu eşdeğeri veri sözleşmelerinde sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="efebb-120">For example, the following code results in equivalent data contracts.</span></span>  
  
 [!code-csharp[C_DataContractNames#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#6)]
 [!code-vb[C_DataContractNames#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#6)]  
  
 <span data-ttu-id="efebb-121">Ancak, aşağıdakiler bir eşdeğer veri sözleşmesi oluşmaz.</span><span class="sxs-lookup"><span data-stu-id="efebb-121">However, the following does not result in an equivalent data contract.</span></span>  
  
 [!code-csharp[C_DataContractNames#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#7)]
 [!code-vb[C_DataContractNames#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#7)]  
  
## <a name="inheritance-interfaces-and-data-contract-equivalence"></a><span data-ttu-id="efebb-122">Devralma, arabirimler ve veri sözleşmesi eşitliği</span><span class="sxs-lookup"><span data-stu-id="efebb-122">Inheritance, Interfaces, and Data Contract Equivalence</span></span>  
 <span data-ttu-id="efebb-123">Tüm temel türü veri üyelerini içeren tek bir veri sözleşmesi ise gibi eşdeğer belirlerken, başka bir veri sözleşmesi devralan bir veri sözleşmesi kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="efebb-123">When determining equivalence, a data contract that inherits from another data contract is treated as if it is just one data contract that includes all of the data members from the base type.</span></span> <span data-ttu-id="efebb-124">Veri üyeleri sırasını eşleşmelidir göz önünde bulundurun ve türetilen tür üyeleri sırada temel tür üyeleri koyun.</span><span class="sxs-lookup"><span data-stu-id="efebb-124">Keep in mind that the order of the data members must match and that base type members precede derived type members in the order.</span></span> <span data-ttu-id="efebb-125">Aşağıdaki kod örneğinde olduğu gibi iki veri üyeleri aynı sıra değeri, ayrıca, bu veri üyeleri için sıralama alfabetik varsa.</span><span class="sxs-lookup"><span data-stu-id="efebb-125">Furthermore, if, as in the following code example, two data members have the same order value, the ordering for those data members is alphabetical.</span></span> <span data-ttu-id="efebb-126">Daha fazla bilgi için bkz: [veri üye sırası](../../../../docs/framework/wcf/feature-details/data-member-order.md).</span><span class="sxs-lookup"><span data-stu-id="efebb-126">For more information, see [Data Member Order](../../../../docs/framework/wcf/feature-details/data-member-order.md).</span></span>  
  
 <span data-ttu-id="efebb-127">Aşağıdaki örnekte, veri türü için sözleşme `Employee` türü için veri sözleşmesi eşdeğerdir `Worker`.</span><span class="sxs-lookup"><span data-stu-id="efebb-127">In the following example, the data contract for type `Employee` is equivalent to the data contract for the type `Worker`.</span></span>  
  
 [!code-csharp[C_DataContractNames#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#8)]
 [!code-vb[C_DataContractNames#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#8)]  
  
 <span data-ttu-id="efebb-128">Türetilmiş bir sınıf bir veri sözleşmesi alıcı uç nokta bekler, parametreler ve dönüş değerleri bir istemci ve hizmet arasında geçirirken, bir veri sözleşmesi temel sınıfından gönderilemiyor.</span><span class="sxs-lookup"><span data-stu-id="efebb-128">When passing parameters and return values between a client and a service, a data contract from a base class cannot be sent when the receiving endpoint expects a data contract from a derived class.</span></span> <span data-ttu-id="efebb-129">Nesne odaklı programlama tenets uygun olarak budur.</span><span class="sxs-lookup"><span data-stu-id="efebb-129">This is in accordance with object-oriented programming tenets.</span></span> <span data-ttu-id="efebb-130">Önceki örnekte, bir nesne türü `Person` ne zaman gönderilemez bir `Employee` beklenir.</span><span class="sxs-lookup"><span data-stu-id="efebb-130">In the previous example, an object of type `Person` cannot be sent when an `Employee` is expected.</span></span>  
  
 <span data-ttu-id="efebb-131">Beklenen, ancak alıcı endpoint "türetilmiş bir tür kullanarak biliyorsa" tek bir veri sözleşmesi temel sınıfından türetilmiş bir sınıf bir veri sözleşmesi gönderilebilir <xref:System.Runtime.Serialization.KnownTypeAttribute>.</span><span class="sxs-lookup"><span data-stu-id="efebb-131">A data contract from a derived class can be sent when a data contract from a base class is expected, but only if the receiving endpoint "knows" of the derived type using the <xref:System.Runtime.Serialization.KnownTypeAttribute>.</span></span> <span data-ttu-id="efebb-132">Daha fazla bilgi için bkz: [veri sözleşmesi bilinen türleri](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="efebb-132">For more information, see [Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span> <span data-ttu-id="efebb-133">Önceki örnekte, bir nesne türü `Employee` ne zaman gönderilebilecek bir `Person` bekleniyor ancak alıcı kodu içeriyorsa yalnızca <xref:System.Runtime.Serialization.KnownTypeAttribute> bilinen türleri listesinde dahil etmek için.</span><span class="sxs-lookup"><span data-stu-id="efebb-133">In the previous example, an object of type `Employee` can be sent when a `Person` is expected, but only if the receiver code employs the <xref:System.Runtime.Serialization.KnownTypeAttribute> to include it in the list of known types.</span></span>  
  
 <span data-ttu-id="efebb-134">Parametreler ve dönüş değerleri beklenen tür bir arabirim ise uygulamalar arasında geçirirken, beklenen tür olan türü eşdeğer <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="efebb-134">When passing parameters and return values between applications, if the expected type is an interface, it is equivalent to the expected type being of type <xref:System.Object>.</span></span> <span data-ttu-id="efebb-135">Türeyen sonuçta her tür için <xref:System.Object>, her veri sözleşmesi için veri sözleşmesi sonuçta türeyen <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="efebb-135">Because every type ultimately derives from <xref:System.Object>, every data contract ultimately derives from the data contract for <xref:System.Object>.</span></span> <span data-ttu-id="efebb-136">Bu nedenle, bir arabirim beklendiğinde herhangi bir veri sözleşmesi türü geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="efebb-136">Thus, any data contract type can be passed when an interface is expected.</span></span> <span data-ttu-id="efebb-137">Başarıyla arabirimleri ile çalışmak için ek adımlar gereklidir; Daha fazla bilgi için bkz: [veri sözleşmesi bilinen türleri](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="efebb-137">Additional steps are required to successfully work with interfaces; for more information, see [Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efebb-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="efebb-138">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 [<span data-ttu-id="efebb-139">Veri Üye Sırası</span><span class="sxs-lookup"><span data-stu-id="efebb-139">Data Member Order</span></span>](../../../../docs/framework/wcf/feature-details/data-member-order.md)  
 [<span data-ttu-id="efebb-140">Veri Anlaşması Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="efebb-140">Data Contract Known Types</span></span>](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [<span data-ttu-id="efebb-141">Veri Anlaşması Adları</span><span class="sxs-lookup"><span data-stu-id="efebb-141">Data Contract Names</span></span>](../../../../docs/framework/wcf/feature-details/data-contract-names.md)
