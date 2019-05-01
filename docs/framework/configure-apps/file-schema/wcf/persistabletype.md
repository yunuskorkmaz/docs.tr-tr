---
title: <persistableType>
ms.date: 03/30/2017
ms.assetid: e5425fe6-523a-4076-aab4-2c2515b1d830
ms.openlocfilehash: 939a29e90ee21e94ccb78842d6f7224e9a6288d0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61783324"
---
# <a name="persistabletype"></a><span data-ttu-id="52bf9-101">\<Persistebletype ></span><span class="sxs-lookup"><span data-stu-id="52bf9-101">\<persistableType></span></span>
<span data-ttu-id="52bf9-102">Kalıcı türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="52bf9-102">Specifies all the persistable types.</span></span>  
  
 <span data-ttu-id="52bf9-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="52bf9-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="52bf9-104">\<comContracts ></span><span class="sxs-lookup"><span data-stu-id="52bf9-104">\<comContracts></span></span>  
<span data-ttu-id="52bf9-105">\<comContract ></span><span class="sxs-lookup"><span data-stu-id="52bf9-105">\<comContract></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52bf9-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="52bf9-106">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="52bf9-107">Tür</span><span class="sxs-lookup"><span data-stu-id="52bf9-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="52bf9-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="52bf9-108">Attributes and Elements</span></span>  
 <span data-ttu-id="52bf9-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="52bf9-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="52bf9-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="52bf9-110">Attributes</span></span>  
  
|<span data-ttu-id="52bf9-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="52bf9-111">Attribute</span></span>|<span data-ttu-id="52bf9-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="52bf9-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="52bf9-113">kimlik</span><span class="sxs-lookup"><span data-stu-id="52bf9-113">id</span></span>|<span data-ttu-id="52bf9-114">Kalıcı bir türü için benzersiz bir tanımlayıcı belirten bir dize içeren gerekli bir öznitelik.</span><span class="sxs-lookup"><span data-stu-id="52bf9-114">A required attribute that contains a string that specifies a unique identifier for a persistable type.</span></span>|  
|<span data-ttu-id="52bf9-115">name</span><span class="sxs-lookup"><span data-stu-id="52bf9-115">name</span></span>|<span data-ttu-id="52bf9-116">Kalıcı türünün adını belirten bir dize içeren isteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="52bf9-116">An optional attribute that contains a string that specifies the name of the persistable type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="52bf9-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="52bf9-117">Child Elements</span></span>  
 <span data-ttu-id="52bf9-118">None</span><span class="sxs-lookup"><span data-stu-id="52bf9-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="52bf9-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="52bf9-119">Parent Elements</span></span>  
  
|<span data-ttu-id="52bf9-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="52bf9-120">Element</span></span>|<span data-ttu-id="52bf9-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="52bf9-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="52bf9-122">\<persistableTypes ></span><span class="sxs-lookup"><span data-stu-id="52bf9-122">\<persistableTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md)|<span data-ttu-id="52bf9-123">Bir koleksiyonu `persistableType` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="52bf9-123">A collection of `persistableType` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="52bf9-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="52bf9-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComPersistableTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ComPersistableTypeElement>
- [<span data-ttu-id="52bf9-125">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="52bf9-125">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)
- [<span data-ttu-id="52bf9-126">COM+ Uygulamaları ile Tümleştirme</span><span class="sxs-lookup"><span data-stu-id="52bf9-126">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="52bf9-127">Nasıl yapılır: COM + hizmet ayarlarını yapılandırma</span><span class="sxs-lookup"><span data-stu-id="52bf9-127">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
