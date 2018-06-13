---
title: dataContractSerializer
ms.date: 03/30/2017
ms.assetid: a47513a4-a96c-4350-8586-daacb05dee71
ms.openlocfilehash: 0528ae823db500da3c3a1efc6934951c4e41cea7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32748024"
---
# <a name="datacontractserializer"></a><span data-ttu-id="2b0a4-102">dataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="2b0a4-102">dataContractSerializer</span></span>
<span data-ttu-id="2b0a4-103">Yapılandırma verilerini içeren <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="2b0a4-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="2b0a4-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="2b0a4-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="2b0a4-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="2b0a4-105">\<behaviors></span></span>  
<span data-ttu-id="2b0a4-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="2b0a4-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="2b0a4-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="2b0a4-107">\<behavior></span></span>  
<span data-ttu-id="2b0a4-108">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="2b0a4-108">\<dataContractSerializer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b0a4-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2b0a4-109">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"  
      maxItemsInObjectGraph="Integer" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2b0a4-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2b0a4-110">Attributes and Elements</span></span>  
 <span data-ttu-id="2b0a4-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2b0a4-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2b0a4-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2b0a4-112">Attributes</span></span>  
  
|<span data-ttu-id="2b0a4-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="2b0a4-113">Element</span></span>|<span data-ttu-id="2b0a4-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2b0a4-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2b0a4-115">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="2b0a4-115">ignoreExtensionDataObject</span></span>|<span data-ttu-id="2b0a4-116">Yüklenmekte olan zaman bitiş noktası tarafından sağlanan verileri yoksayacak şekilde belirten bir Boole değeri serileştirilecek veya serisi.</span><span class="sxs-lookup"><span data-stu-id="2b0a4-116">A Boolean value that specifies whether to ignore data supplied by the endpoint, when it is being serialized or deserialized.</span></span>|  
|<span data-ttu-id="2b0a4-117">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="2b0a4-117">maxItemsInObjectGraph</span></span>|<span data-ttu-id="2b0a4-118">Tamsayı serileştirmek veya seri durumdan öğe sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="2b0a4-118">An integer that specifies the maximum number of items to serialize or deserialize.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2b0a4-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2b0a4-119">Child Elements</span></span>  
 <span data-ttu-id="2b0a4-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="2b0a4-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2b0a4-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2b0a4-121">Parent Elements</span></span>  
  
|<span data-ttu-id="2b0a4-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="2b0a4-122">Element</span></span>|<span data-ttu-id="2b0a4-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2b0a4-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2b0a4-124">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="2b0a4-124">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="2b0a4-125">Bir uç nokta davranışını belirtir.</span><span class="sxs-lookup"><span data-stu-id="2b0a4-125">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2b0a4-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2b0a4-126">Remarks</span></span>  
 <span data-ttu-id="2b0a4-127">Bkz: <xref:System.Runtime.Serialization.DataContractSerializer> bilinen türleri hakkında daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="2b0a4-127">See the <xref:System.Runtime.Serialization.DataContractSerializer> documentation for more information about known types.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="2b0a4-128">`<dataContractSerializer>` Davranışı öğesi (varsa) önce her zaman görünmelidir `<enableWebScript>` davranışı öğesi yapılandırma dosyasında.</span><span class="sxs-lookup"><span data-stu-id="2b0a4-128">The `<dataContractSerializer>` behavior element (if present) should always appear before the `<enableWebScript>` behavior element in the configuration file.</span></span> <span data-ttu-id="2b0a4-129">Aksi takdirde, bunun sonucunda oluşan davranışı tanımlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="2b0a4-129">Otherwise, the resulting behavior is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b0a4-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2b0a4-130">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>  
 <xref:System.ServiceModel.Configuration.DataContractSerializerElement>  
 [<span data-ttu-id="2b0a4-131">Veri Anlaşması Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="2b0a4-131">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [<span data-ttu-id="2b0a4-132">Veri Aktarma ve Seri Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="2b0a4-132">Data Transfer and Serialization</span></span>](../../../../../docs/framework/wcf/feature-details/data-transfer-and-serialization.md)
