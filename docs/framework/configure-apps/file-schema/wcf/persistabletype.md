---
title: <persistableType>
ms.date: 03/30/2017
ms.assetid: e5425fe6-523a-4076-aab4-2c2515b1d830
ms.openlocfilehash: 328caaefe0cc24da45b460cab0a672dc8a6ccce1
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855075"
---
# <a name="persistabletype"></a><span data-ttu-id="4109a-101">\<persistableType ></span><span class="sxs-lookup"><span data-stu-id="4109a-101">\<persistableType></span></span>
<span data-ttu-id="4109a-102">Tüm kalıcı türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4109a-102">Specifies all the persistable types.</span></span>  
  
<span data-ttu-id="4109a-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="4109a-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="4109a-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="4109a-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="4109a-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comContracts >** ](comcontracts.md)</span><span class="sxs-lookup"><span data-stu-id="4109a-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContracts>**](comcontracts.md)</span></span>\
<span data-ttu-id="4109a-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comContract >** ](comcontract.md)</span><span class="sxs-lookup"><span data-stu-id="4109a-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContract>**](comcontract.md)</span></span>\
<span data-ttu-id="4109a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<persistableTypes >** ](persistabletypes.md)</span><span class="sxs-lookup"><span data-stu-id="4109a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<persistableTypes>**](persistabletypes.md)</span></span>\
<span data-ttu-id="4109a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<persistableType >**</span><span class="sxs-lookup"><span data-stu-id="4109a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<persistableType>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4109a-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4109a-109">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="4109a-110">Tür</span><span class="sxs-lookup"><span data-stu-id="4109a-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4109a-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4109a-111">Attributes and Elements</span></span>  
 <span data-ttu-id="4109a-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4109a-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4109a-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4109a-113">Attributes</span></span>  
  
|<span data-ttu-id="4109a-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4109a-114">Attribute</span></span>|<span data-ttu-id="4109a-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4109a-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4109a-116">kimlik</span><span class="sxs-lookup"><span data-stu-id="4109a-116">id</span></span>|<span data-ttu-id="4109a-117">Kalıcı bir tür için benzersiz bir tanımlayıcı belirten bir dize içeren gerekli bir öznitelik.</span><span class="sxs-lookup"><span data-stu-id="4109a-117">A required attribute that contains a string that specifies a unique identifier for a persistable type.</span></span>|  
|<span data-ttu-id="4109a-118">name</span><span class="sxs-lookup"><span data-stu-id="4109a-118">name</span></span>|<span data-ttu-id="4109a-119">Kalıcı tablo türünün adını belirten bir dize içeren isteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="4109a-119">An optional attribute that contains a string that specifies the name of the persistable type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4109a-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4109a-120">Child Elements</span></span>  
 <span data-ttu-id="4109a-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="4109a-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4109a-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4109a-122">Parent Elements</span></span>  
  
|<span data-ttu-id="4109a-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="4109a-123">Element</span></span>|<span data-ttu-id="4109a-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4109a-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4109a-125">\<persistableTypes ></span><span class="sxs-lookup"><span data-stu-id="4109a-125">\<persistableTypes></span></span>](persistabletypes.md)|<span data-ttu-id="4109a-126">`persistableType` Öğelerin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="4109a-126">A collection of `persistableType` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4109a-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4109a-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComPersistableTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ComPersistableTypeElement>
- [<span data-ttu-id="4109a-128">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="4109a-128">\<comContracts></span></span>](comcontracts.md)
- [<span data-ttu-id="4109a-129">COM+ Uygulamaları ile Tümleştirme</span><span class="sxs-lookup"><span data-stu-id="4109a-129">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="4109a-130">Nasıl yapılır: COM+ hizmet ayarlarını yapılandırma</span><span class="sxs-lookup"><span data-stu-id="4109a-130">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
