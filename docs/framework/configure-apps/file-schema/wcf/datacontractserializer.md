---
title: dataContractSerializer
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a47513a4-a96c-4350-8586-daacb05dee71
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 66c8686ae4397b9d4bf18fbf7a79aa2408db101d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="datacontractserializer"></a><span data-ttu-id="40098-102">dataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="40098-102">dataContractSerializer</span></span>
<span data-ttu-id="40098-103">Yapılandırma verilerini içeren <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="40098-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="40098-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="40098-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="40098-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="40098-105">\<behaviors></span></span>  
<span data-ttu-id="40098-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="40098-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="40098-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="40098-107">\<behavior></span></span>  
<span data-ttu-id="40098-108">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="40098-108">\<dataContractSerializer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40098-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="40098-109">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"  
      maxItemsInObjectGraph="Integer" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="40098-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="40098-110">Attributes and Elements</span></span>  
 <span data-ttu-id="40098-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="40098-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="40098-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="40098-112">Attributes</span></span>  
  
|<span data-ttu-id="40098-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="40098-113">Element</span></span>|<span data-ttu-id="40098-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="40098-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="40098-115">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="40098-115">ignoreExtensionDataObject</span></span>|<span data-ttu-id="40098-116">Yüklenmekte olan zaman bitiş noktası tarafından sağlanan verileri yoksayacak şekilde belirten bir Boole değeri serileştirilecek veya serisi.</span><span class="sxs-lookup"><span data-stu-id="40098-116">A Boolean value that specifies whether to ignore data supplied by the endpoint, when it is being serialized or deserialized.</span></span>|  
|<span data-ttu-id="40098-117">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="40098-117">maxItemsInObjectGraph</span></span>|<span data-ttu-id="40098-118">Tamsayı serileştirmek veya seri durumdan öğe sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="40098-118">An integer that specifies the maximum number of items to serialize or deserialize.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="40098-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="40098-119">Child Elements</span></span>  
 <span data-ttu-id="40098-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="40098-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="40098-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="40098-121">Parent Elements</span></span>  
  
|<span data-ttu-id="40098-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="40098-122">Element</span></span>|<span data-ttu-id="40098-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="40098-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="40098-124">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="40098-124">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="40098-125">Bir uç nokta davranışını belirtir.</span><span class="sxs-lookup"><span data-stu-id="40098-125">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="40098-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="40098-126">Remarks</span></span>  
 <span data-ttu-id="40098-127">Bkz: <xref:System.Runtime.Serialization.DataContractSerializer> bilinen türleri hakkında daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="40098-127">See the <xref:System.Runtime.Serialization.DataContractSerializer> documentation for more information about known types.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="40098-128">`<dataContractSerializer>` Davranışı öğesi (varsa) önce her zaman görünmelidir `<enableWebScript>` davranışı öğesi yapılandırma dosyasında.</span><span class="sxs-lookup"><span data-stu-id="40098-128">The `<dataContractSerializer>` behavior element (if present) should always appear before the `<enableWebScript>` behavior element in the configuration file.</span></span> <span data-ttu-id="40098-129">Aksi takdirde, bunun sonucunda oluşan davranışı tanımlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="40098-129">Otherwise, the resulting behavior is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40098-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="40098-130">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>  
 <xref:System.ServiceModel.Configuration.DataContractSerializerElement>  
 [<span data-ttu-id="40098-131">Veri Anlaşması Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="40098-131">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [<span data-ttu-id="40098-132">Veri Aktarma ve Seri Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="40098-132">Data Transfer and Serialization</span></span>](../../../../../docs/framework/wcf/feature-details/data-transfer-and-serialization.md)
