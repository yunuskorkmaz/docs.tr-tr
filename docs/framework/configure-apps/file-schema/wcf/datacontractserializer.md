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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4044e81b7c33c7a755678e79586dd4f37cf54ed5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="datacontractserializer"></a><span data-ttu-id="2b215-102">dataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="2b215-102">dataContractSerializer</span></span>
<span data-ttu-id="2b215-103">Yapılandırma verilerini içeren <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="2b215-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="2b215-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="2b215-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="2b215-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="2b215-105">\<behaviors></span></span>  
<span data-ttu-id="2b215-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="2b215-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="2b215-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="2b215-107">\<behavior></span></span>  
<span data-ttu-id="2b215-108">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="2b215-108">\<dataContractSerializer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b215-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2b215-109">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"  
      maxItemsInObjectGraph="Integer" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2b215-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2b215-110">Attributes and Elements</span></span>  
 <span data-ttu-id="2b215-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2b215-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2b215-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2b215-112">Attributes</span></span>  
  
|<span data-ttu-id="2b215-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="2b215-113">Element</span></span>|<span data-ttu-id="2b215-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2b215-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2b215-115">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="2b215-115">ignoreExtensionDataObject</span></span>|<span data-ttu-id="2b215-116">Yüklenmekte olan zaman bitiş noktası tarafından sağlanan verileri yoksayacak şekilde belirten bir Boole değeri serileştirilecek veya serisi.</span><span class="sxs-lookup"><span data-stu-id="2b215-116">A Boolean value that specifies whether to ignore data supplied by the endpoint, when it is being serialized or deserialized.</span></span>|  
|<span data-ttu-id="2b215-117">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="2b215-117">maxItemsInObjectGraph</span></span>|<span data-ttu-id="2b215-118">Tamsayı serileştirmek veya seri durumdan öğe sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="2b215-118">An integer that specifies the maximum number of items to serialize or deserialize.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2b215-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2b215-119">Child Elements</span></span>  
 <span data-ttu-id="2b215-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="2b215-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2b215-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2b215-121">Parent Elements</span></span>  
  
|<span data-ttu-id="2b215-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="2b215-122">Element</span></span>|<span data-ttu-id="2b215-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2b215-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2b215-124">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="2b215-124">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="2b215-125">Bir uç nokta davranışını belirtir.</span><span class="sxs-lookup"><span data-stu-id="2b215-125">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2b215-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2b215-126">Remarks</span></span>  
 <span data-ttu-id="2b215-127">Bkz: <xref:System.Runtime.Serialization.DataContractSerializer> bilinen türleri hakkında daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="2b215-127">See the <xref:System.Runtime.Serialization.DataContractSerializer> documentation for more information about known types.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="2b215-128">`<dataContractSerializer>` Davranışı öğesi (varsa) önce her zaman görünmelidir `<enableWebScript>` davranışı öğesi yapılandırma dosyasında.</span><span class="sxs-lookup"><span data-stu-id="2b215-128">The `<dataContractSerializer>` behavior element (if present) should always appear before the `<enableWebScript>` behavior element in the configuration file.</span></span> <span data-ttu-id="2b215-129">Aksi takdirde, bunun sonucunda oluşan davranışı tanımlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="2b215-129">Otherwise, the resulting behavior is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b215-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2b215-130">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>  
 <xref:System.ServiceModel.Configuration.DataContractSerializerElement>  
 [<span data-ttu-id="2b215-131">Veri sözleşmesi bilinen türler</span><span class="sxs-lookup"><span data-stu-id="2b215-131">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [<span data-ttu-id="2b215-132">Veri aktarma ve seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="2b215-132">Data Transfer and Serialization</span></span>](../../../../../docs/framework/wcf/feature-details/data-transfer-and-serialization.md)
