---
title: '&lt;persistableType&gt;'
ms.date: 03/30/2017
ms.assetid: e5425fe6-523a-4076-aab4-2c2515b1d830
ms.openlocfilehash: 23724957398ed1ade2c81a3932e9773d7cf4c642
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32747079"
---
# <a name="ltpersistabletypegt"></a><span data-ttu-id="15f17-102">&lt;persistableType&gt;</span><span class="sxs-lookup"><span data-stu-id="15f17-102">&lt;persistableType&gt;</span></span>
<span data-ttu-id="15f17-103">Tüm kalıcı türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="15f17-103">Specifies all the persistable types.</span></span>  
  
 <span data-ttu-id="15f17-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="15f17-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="15f17-105">\<comContracts ></span><span class="sxs-lookup"><span data-stu-id="15f17-105">\<comContracts></span></span>  
<span data-ttu-id="15f17-106">\<comContract ></span><span class="sxs-lookup"><span data-stu-id="15f17-106">\<comContract></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15f17-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="15f17-107">Syntax</span></span>  
  
```xml  
<comContracts>  
  <comContract>  
      <persistableTypes>  
         <persistableType id="string"  
            name="string">  
         </persistableType>  
      </persistableTypes>  
  </comContract>  
</comContracts>  
```  
  
## <a name="type"></a><span data-ttu-id="15f17-108">Tür</span><span class="sxs-lookup"><span data-stu-id="15f17-108">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="15f17-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="15f17-109">Attributes and Elements</span></span>  
 <span data-ttu-id="15f17-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="15f17-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="15f17-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="15f17-111">Attributes</span></span>  
  
|<span data-ttu-id="15f17-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="15f17-112">Attribute</span></span>|<span data-ttu-id="15f17-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="15f17-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="15f17-114">kimlik</span><span class="sxs-lookup"><span data-stu-id="15f17-114">id</span></span>|<span data-ttu-id="15f17-115">Kalıcı bir türü için benzersiz bir tanımlayıcı belirten bir dize içeriyor gerekli bir öznitelik.</span><span class="sxs-lookup"><span data-stu-id="15f17-115">A required attribute that contains a string that specifies a unique identifier for a persistable type.</span></span>|  
|<span data-ttu-id="15f17-116">name</span><span class="sxs-lookup"><span data-stu-id="15f17-116">name</span></span>|<span data-ttu-id="15f17-117">Kalıcı türünün adını belirten dize içeren bir isteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="15f17-117">An optional attribute that contains a string that specifies the name of the persistable type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="15f17-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="15f17-118">Child Elements</span></span>  
 <span data-ttu-id="15f17-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="15f17-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="15f17-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="15f17-120">Parent Elements</span></span>  
  
|<span data-ttu-id="15f17-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="15f17-121">Element</span></span>|<span data-ttu-id="15f17-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="15f17-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="15f17-123">\<persistableTypes ></span><span class="sxs-lookup"><span data-stu-id="15f17-123">\<persistableTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md)|<span data-ttu-id="15f17-124">Bir koleksiyonu `persistableType` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="15f17-124">A collection of `persistableType` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="15f17-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="15f17-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ComPersistableTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ComPersistableTypeElement>  
 [<span data-ttu-id="15f17-126">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="15f17-126">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)  
 [<span data-ttu-id="15f17-127">COM+ Uygulamaları ile Tümleştirme</span><span class="sxs-lookup"><span data-stu-id="15f17-127">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [<span data-ttu-id="15f17-128">Nasıl yapılır: COM+ Hizmet Ayarlarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="15f17-128">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
