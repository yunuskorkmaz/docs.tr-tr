---
title: <persistableType>
ms.date: 03/30/2017
ms.assetid: e5425fe6-523a-4076-aab4-2c2515b1d830
ms.openlocfilehash: 3ea99d360ceb1e3fe6e97cbf9c8827dd7c853f63
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55256530"
---
# <a name="persistabletype"></a><span data-ttu-id="56d6f-101">\<Persistebletype ></span><span class="sxs-lookup"><span data-stu-id="56d6f-101">\<persistableType></span></span>
<span data-ttu-id="56d6f-102">Kalıcı türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="56d6f-102">Specifies all the persistable types.</span></span>  
  
 <span data-ttu-id="56d6f-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="56d6f-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="56d6f-104">\<comContracts ></span><span class="sxs-lookup"><span data-stu-id="56d6f-104">\<comContracts></span></span>  
<span data-ttu-id="56d6f-105">\<comContract ></span><span class="sxs-lookup"><span data-stu-id="56d6f-105">\<comContract></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56d6f-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="56d6f-106">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="56d6f-107">Tür</span><span class="sxs-lookup"><span data-stu-id="56d6f-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="56d6f-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="56d6f-108">Attributes and Elements</span></span>  
 <span data-ttu-id="56d6f-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="56d6f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="56d6f-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="56d6f-110">Attributes</span></span>  
  
|<span data-ttu-id="56d6f-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="56d6f-111">Attribute</span></span>|<span data-ttu-id="56d6f-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="56d6f-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="56d6f-113">kimlik</span><span class="sxs-lookup"><span data-stu-id="56d6f-113">id</span></span>|<span data-ttu-id="56d6f-114">Kalıcı bir türü için benzersiz bir tanımlayıcı belirten bir dize içeren gerekli bir öznitelik.</span><span class="sxs-lookup"><span data-stu-id="56d6f-114">A required attribute that contains a string that specifies a unique identifier for a persistable type.</span></span>|  
|<span data-ttu-id="56d6f-115">name</span><span class="sxs-lookup"><span data-stu-id="56d6f-115">name</span></span>|<span data-ttu-id="56d6f-116">Kalıcı türünün adını belirten bir dize içeren isteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="56d6f-116">An optional attribute that contains a string that specifies the name of the persistable type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="56d6f-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="56d6f-117">Child Elements</span></span>  
 <span data-ttu-id="56d6f-118">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="56d6f-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="56d6f-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="56d6f-119">Parent Elements</span></span>  
  
|<span data-ttu-id="56d6f-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="56d6f-120">Element</span></span>|<span data-ttu-id="56d6f-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="56d6f-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="56d6f-122">\<persistableTypes ></span><span class="sxs-lookup"><span data-stu-id="56d6f-122">\<persistableTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md)|<span data-ttu-id="56d6f-123">Bir koleksiyonu `persistableType` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="56d6f-123">A collection of `persistableType` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="56d6f-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="56d6f-124">See also</span></span>
- <xref:System.ServiceModel.Configuration.ComPersistableTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ComPersistableTypeElement>
- [<span data-ttu-id="56d6f-125">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="56d6f-125">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)
- [<span data-ttu-id="56d6f-126">COM+ Uygulamaları ile Tümleştirme</span><span class="sxs-lookup"><span data-stu-id="56d6f-126">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="56d6f-127">Nasıl yapılır: COM + hizmet ayarlarını yapılandırma</span><span class="sxs-lookup"><span data-stu-id="56d6f-127">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
