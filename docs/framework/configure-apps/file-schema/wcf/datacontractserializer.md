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
ms.openlocfilehash: a64f5ae4573efbd8c0f7d622e6b94b7786585bb1
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="datacontractserializer"></a><span data-ttu-id="84e26-102">dataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="84e26-102">dataContractSerializer</span></span>
<span data-ttu-id="84e26-103">Yapılandırma verilerini içeren <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="84e26-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="84e26-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="84e26-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="84e26-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="84e26-105">\<behaviors></span></span>  
<span data-ttu-id="84e26-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="84e26-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="84e26-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="84e26-107">\<behavior></span></span>  
<span data-ttu-id="84e26-108">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="84e26-108">\<dataContractSerializer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84e26-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="84e26-109">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"  
      maxItemsInObjectGraph="Integer" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="84e26-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="84e26-110">Attributes and Elements</span></span>  
 <span data-ttu-id="84e26-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="84e26-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="84e26-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="84e26-112">Attributes</span></span>  
  
|<span data-ttu-id="84e26-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="84e26-113">Element</span></span>|<span data-ttu-id="84e26-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="84e26-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="84e26-115">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="84e26-115">ignoreExtensionDataObject</span></span>|<span data-ttu-id="84e26-116">Yüklenmekte olan zaman bitiş noktası tarafından sağlanan verileri yoksayacak şekilde belirten bir Boole değeri serileştirilecek veya serisi.</span><span class="sxs-lookup"><span data-stu-id="84e26-116">A Boolean value that specifies whether to ignore data supplied by the endpoint, when it is being serialized or deserialized.</span></span>|  
|<span data-ttu-id="84e26-117">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="84e26-117">maxItemsInObjectGraph</span></span>|<span data-ttu-id="84e26-118">Tamsayı serileştirmek veya seri durumdan öğe sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="84e26-118">An integer that specifies the maximum number of items to serialize or deserialize.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="84e26-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="84e26-119">Child Elements</span></span>  
 <span data-ttu-id="84e26-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="84e26-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="84e26-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="84e26-121">Parent Elements</span></span>  
  
|<span data-ttu-id="84e26-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="84e26-122">Element</span></span>|<span data-ttu-id="84e26-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="84e26-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="84e26-124">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="84e26-124">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="84e26-125">Bir uç nokta davranışını belirtir.</span><span class="sxs-lookup"><span data-stu-id="84e26-125">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="84e26-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="84e26-126">Remarks</span></span>  
 <span data-ttu-id="84e26-127">Bkz: <xref:System.Runtime.Serialization.DataContractSerializer> bilinen türleri hakkında daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="84e26-127">See the <xref:System.Runtime.Serialization.DataContractSerializer> documentation for more information about known types.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="84e26-128">`<dataContractSerializer>` Davranışı öğesi (varsa) önce her zaman görünmelidir `<enableWebScript>` davranışı öğesi yapılandırma dosyasında.</span><span class="sxs-lookup"><span data-stu-id="84e26-128">The `<dataContractSerializer>` behavior element (if present) should always appear before the `<enableWebScript>` behavior element in the configuration file.</span></span> <span data-ttu-id="84e26-129">Aksi takdirde, bunun sonucunda oluşan davranışı tanımlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="84e26-129">Otherwise, the resulting behavior is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84e26-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="84e26-130">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>  
 <xref:System.ServiceModel.Configuration.DataContractSerializerElement>  
 [<span data-ttu-id="84e26-131">Veri sözleşmesi bilinen türler</span><span class="sxs-lookup"><span data-stu-id="84e26-131">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [<span data-ttu-id="84e26-132">Veri aktarma ve seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="84e26-132">Data Transfer and Serialization</span></span>](../../../../../docs/framework/wcf/feature-details/data-transfer-and-serialization.md)
