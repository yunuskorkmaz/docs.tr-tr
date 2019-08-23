---
title: <persistableType>
ms.date: 03/30/2017
ms.assetid: e5425fe6-523a-4076-aab4-2c2515b1d830
ms.openlocfilehash: fcfd338e289b5151688724f0e84b6878707d32be
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933830"
---
# <a name="persistabletype"></a><span data-ttu-id="be02b-101">\<persistableType ></span><span class="sxs-lookup"><span data-stu-id="be02b-101">\<persistableType></span></span>
<span data-ttu-id="be02b-102">Tüm kalıcı türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="be02b-102">Specifies all the persistable types.</span></span>  
  
 <span data-ttu-id="be02b-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="be02b-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="be02b-104">\<comContracts ></span><span class="sxs-lookup"><span data-stu-id="be02b-104">\<comContracts></span></span>  
<span data-ttu-id="be02b-105">\<comContract ></span><span class="sxs-lookup"><span data-stu-id="be02b-105">\<comContract></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be02b-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="be02b-106">Syntax</span></span>  
  
```xml  
<comContracts>
  <comContract>
    <persistableTypes>
      <persistableType id="String"
                       name="String">
      </persistableType>
    </persistableTypes>
  </comContract>
</comContracts>
```  
  
## <a name="type"></a><span data-ttu-id="be02b-107">Tür</span><span class="sxs-lookup"><span data-stu-id="be02b-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="be02b-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="be02b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="be02b-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="be02b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="be02b-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="be02b-110">Attributes</span></span>  
  
|<span data-ttu-id="be02b-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="be02b-111">Attribute</span></span>|<span data-ttu-id="be02b-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="be02b-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="be02b-113">kimlik</span><span class="sxs-lookup"><span data-stu-id="be02b-113">id</span></span>|<span data-ttu-id="be02b-114">Kalıcı bir tür için benzersiz bir tanımlayıcı belirten bir dize içeren gerekli bir öznitelik.</span><span class="sxs-lookup"><span data-stu-id="be02b-114">A required attribute that contains a string that specifies a unique identifier for a persistable type.</span></span>|  
|<span data-ttu-id="be02b-115">name</span><span class="sxs-lookup"><span data-stu-id="be02b-115">name</span></span>|<span data-ttu-id="be02b-116">Kalıcı tablo türünün adını belirten bir dize içeren isteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="be02b-116">An optional attribute that contains a string that specifies the name of the persistable type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="be02b-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="be02b-117">Child Elements</span></span>  
 <span data-ttu-id="be02b-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="be02b-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="be02b-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="be02b-119">Parent Elements</span></span>  
  
|<span data-ttu-id="be02b-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="be02b-120">Element</span></span>|<span data-ttu-id="be02b-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="be02b-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="be02b-122">\<persistableTypes ></span><span class="sxs-lookup"><span data-stu-id="be02b-122">\<persistableTypes></span></span>](persistabletypes.md)|<span data-ttu-id="be02b-123">`persistableType` Öğelerin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="be02b-123">A collection of `persistableType` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="be02b-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="be02b-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComPersistableTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ComPersistableTypeElement>
- [<span data-ttu-id="be02b-125">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="be02b-125">\<comContracts></span></span>](comcontracts.md)
- [<span data-ttu-id="be02b-126">COM+ Uygulamaları ile Tümleştirme</span><span class="sxs-lookup"><span data-stu-id="be02b-126">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="be02b-127">Nasıl yapılır: COM+ hizmet ayarlarını yapılandırma</span><span class="sxs-lookup"><span data-stu-id="be02b-127">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
