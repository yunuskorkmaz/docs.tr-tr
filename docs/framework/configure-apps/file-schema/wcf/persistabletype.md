---
title: '&lt;Persistebletype&gt;'
ms.date: 03/30/2017
ms.assetid: e5425fe6-523a-4076-aab4-2c2515b1d830
ms.openlocfilehash: 92c59b3804e22c62340acccc1e12e594203c8e8b
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145425"
---
# <a name="ltpersistabletypegt"></a><span data-ttu-id="067c4-102">&lt;Persistebletype&gt;</span><span class="sxs-lookup"><span data-stu-id="067c4-102">&lt;persistableType&gt;</span></span>
<span data-ttu-id="067c4-103">Kalıcı türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="067c4-103">Specifies all the persistable types.</span></span>  
  
 <span data-ttu-id="067c4-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="067c4-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="067c4-105">\<comContracts ></span><span class="sxs-lookup"><span data-stu-id="067c4-105">\<comContracts></span></span>  
<span data-ttu-id="067c4-106">\<comContract ></span><span class="sxs-lookup"><span data-stu-id="067c4-106">\<comContract></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="067c4-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="067c4-107">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="067c4-108">Tür</span><span class="sxs-lookup"><span data-stu-id="067c4-108">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="067c4-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="067c4-109">Attributes and Elements</span></span>  
 <span data-ttu-id="067c4-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="067c4-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="067c4-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="067c4-111">Attributes</span></span>  
  
|<span data-ttu-id="067c4-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="067c4-112">Attribute</span></span>|<span data-ttu-id="067c4-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="067c4-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="067c4-114">kimlik</span><span class="sxs-lookup"><span data-stu-id="067c4-114">id</span></span>|<span data-ttu-id="067c4-115">Kalıcı bir türü için benzersiz bir tanımlayıcı belirten bir dize içeren gerekli bir öznitelik.</span><span class="sxs-lookup"><span data-stu-id="067c4-115">A required attribute that contains a string that specifies a unique identifier for a persistable type.</span></span>|  
|<span data-ttu-id="067c4-116">name</span><span class="sxs-lookup"><span data-stu-id="067c4-116">name</span></span>|<span data-ttu-id="067c4-117">Kalıcı türünün adını belirten bir dize içeren isteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="067c4-117">An optional attribute that contains a string that specifies the name of the persistable type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="067c4-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="067c4-118">Child Elements</span></span>  
 <span data-ttu-id="067c4-119">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="067c4-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="067c4-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="067c4-120">Parent Elements</span></span>  
  
|<span data-ttu-id="067c4-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="067c4-121">Element</span></span>|<span data-ttu-id="067c4-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="067c4-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="067c4-123">\<persistableTypes ></span><span class="sxs-lookup"><span data-stu-id="067c4-123">\<persistableTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md)|<span data-ttu-id="067c4-124">Bir koleksiyonu `persistableType` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="067c4-124">A collection of `persistableType` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="067c4-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="067c4-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ComPersistableTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ComPersistableTypeElement>  
 [<span data-ttu-id="067c4-126">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="067c4-126">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)  
 [<span data-ttu-id="067c4-127">COM+ Uygulamaları ile Tümleştirme</span><span class="sxs-lookup"><span data-stu-id="067c4-127">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [<span data-ttu-id="067c4-128">Nasıl yapılır: COM + hizmet ayarlarını yapılandırma</span><span class="sxs-lookup"><span data-stu-id="067c4-128">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
