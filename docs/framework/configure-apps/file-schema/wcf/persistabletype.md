---
title: <persistableType>
ms.date: 03/30/2017
ms.assetid: e5425fe6-523a-4076-aab4-2c2515b1d830
ms.openlocfilehash: 939a29e90ee21e94ccb78842d6f7224e9a6288d0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59083744"
---
# <a name="persistabletype"></a><span data-ttu-id="e6dae-101">\<Persistebletype ></span><span class="sxs-lookup"><span data-stu-id="e6dae-101">\<persistableType></span></span>
<span data-ttu-id="e6dae-102">Kalıcı türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e6dae-102">Specifies all the persistable types.</span></span>  
  
 <span data-ttu-id="e6dae-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e6dae-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="e6dae-104">\<comContracts ></span><span class="sxs-lookup"><span data-stu-id="e6dae-104">\<comContracts></span></span>  
<span data-ttu-id="e6dae-105">\<comContract ></span><span class="sxs-lookup"><span data-stu-id="e6dae-105">\<comContract></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6dae-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e6dae-106">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="e6dae-107">Tür</span><span class="sxs-lookup"><span data-stu-id="e6dae-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e6dae-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e6dae-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e6dae-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e6dae-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e6dae-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e6dae-110">Attributes</span></span>  
  
|<span data-ttu-id="e6dae-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e6dae-111">Attribute</span></span>|<span data-ttu-id="e6dae-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e6dae-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e6dae-113">kimlik</span><span class="sxs-lookup"><span data-stu-id="e6dae-113">id</span></span>|<span data-ttu-id="e6dae-114">Kalıcı bir türü için benzersiz bir tanımlayıcı belirten bir dize içeren gerekli bir öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e6dae-114">A required attribute that contains a string that specifies a unique identifier for a persistable type.</span></span>|  
|<span data-ttu-id="e6dae-115">name</span><span class="sxs-lookup"><span data-stu-id="e6dae-115">name</span></span>|<span data-ttu-id="e6dae-116">Kalıcı türünün adını belirten bir dize içeren isteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e6dae-116">An optional attribute that contains a string that specifies the name of the persistable type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e6dae-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e6dae-117">Child Elements</span></span>  
 <span data-ttu-id="e6dae-118">None</span><span class="sxs-lookup"><span data-stu-id="e6dae-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e6dae-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e6dae-119">Parent Elements</span></span>  
  
|<span data-ttu-id="e6dae-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="e6dae-120">Element</span></span>|<span data-ttu-id="e6dae-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e6dae-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e6dae-122">\<persistableTypes ></span><span class="sxs-lookup"><span data-stu-id="e6dae-122">\<persistableTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md)|<span data-ttu-id="e6dae-123">Bir koleksiyonu `persistableType` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="e6dae-123">A collection of `persistableType` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e6dae-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e6dae-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComPersistableTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ComPersistableTypeElement>
- [<span data-ttu-id="e6dae-125">\<comContracts ></span><span class="sxs-lookup"><span data-stu-id="e6dae-125">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)
- [<span data-ttu-id="e6dae-126">COM Uygulamaları ile Tümleştirme</span><span class="sxs-lookup"><span data-stu-id="e6dae-126">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="e6dae-127">Nasıl yapılır: COM+ Hizmet Ayarlarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e6dae-127">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
