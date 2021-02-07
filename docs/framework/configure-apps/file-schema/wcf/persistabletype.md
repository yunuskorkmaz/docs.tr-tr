---
description: 'Hakkında daha fazla bilgi edinin: <persistableType>'
title: <persistableType>
ms.date: 03/30/2017
ms.assetid: e5425fe6-523a-4076-aab4-2c2515b1d830
ms.openlocfilehash: eadbb951d751dd88ce974edc8d5b343a1469b758
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683638"
---
# \<persistableType>

<span data-ttu-id="cd376-102">Tüm kalıcı türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="cd376-102">Specifies all the persistable types.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContracts>**](comcontracts.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContract>**](comcontract.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<persistableTypes>**](persistabletypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<persistableType>**  
  
## <a name="syntax"></a><span data-ttu-id="cd376-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="cd376-103">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="cd376-104">Tür</span><span class="sxs-lookup"><span data-stu-id="cd376-104">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cd376-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="cd376-105">Attributes and Elements</span></span>  

 <span data-ttu-id="cd376-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cd376-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cd376-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="cd376-107">Attributes</span></span>  
  
|<span data-ttu-id="cd376-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="cd376-108">Attribute</span></span>|<span data-ttu-id="cd376-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cd376-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cd376-110">kimlik</span><span class="sxs-lookup"><span data-stu-id="cd376-110">id</span></span>|<span data-ttu-id="cd376-111">Kalıcı bir tür için benzersiz bir tanımlayıcı belirten bir dize içeren gerekli bir öznitelik.</span><span class="sxs-lookup"><span data-stu-id="cd376-111">A required attribute that contains a string that specifies a unique identifier for a persistable type.</span></span>|  
|<span data-ttu-id="cd376-112">name</span><span class="sxs-lookup"><span data-stu-id="cd376-112">name</span></span>|<span data-ttu-id="cd376-113">Kalıcı tablo türünün adını belirten bir dize içeren isteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="cd376-113">An optional attribute that contains a string that specifies the name of the persistable type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cd376-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="cd376-114">Child Elements</span></span>  

 <span data-ttu-id="cd376-115">Yok</span><span class="sxs-lookup"><span data-stu-id="cd376-115">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cd376-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="cd376-116">Parent Elements</span></span>  
  
|<span data-ttu-id="cd376-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="cd376-117">Element</span></span>|<span data-ttu-id="cd376-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cd376-118">Description</span></span>|  
|-------------|-----------------|  
|[\<persistableTypes>](persistabletypes.md)|<span data-ttu-id="cd376-119">`persistableType`Öğelerin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="cd376-119">A collection of `persistableType` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cd376-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cd376-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComPersistableTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ComPersistableTypeElement>
- [\<comContracts>](comcontracts.md)
- [<span data-ttu-id="cd376-121">COM+ uygulamalarıyla tümleştirme</span><span class="sxs-lookup"><span data-stu-id="cd376-121">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="cd376-122">Nasıl yapılır: COM+ Hizmet Ayarlarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="cd376-122">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
