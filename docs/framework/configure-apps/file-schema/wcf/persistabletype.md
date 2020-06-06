---
title: <persistableType>
ms.date: 03/30/2017
ms.assetid: e5425fe6-523a-4076-aab4-2c2515b1d830
ms.openlocfilehash: 328caaefe0cc24da45b460cab0a672dc8a6ccce1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855075"
---
# \<persistableType>
<span data-ttu-id="43513-101">Tüm kalıcı türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="43513-101">Specifies all the persistable types.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContracts>**](comcontracts.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContract>**](comcontract.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<persistableTypes>**](persistabletypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<persistableType>**  
  
## <a name="syntax"></a><span data-ttu-id="43513-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="43513-102">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="43513-103">Tür</span><span class="sxs-lookup"><span data-stu-id="43513-103">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="43513-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="43513-104">Attributes and Elements</span></span>  
 <span data-ttu-id="43513-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="43513-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="43513-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="43513-106">Attributes</span></span>  
  
|<span data-ttu-id="43513-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="43513-107">Attribute</span></span>|<span data-ttu-id="43513-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="43513-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="43513-109">kimlik</span><span class="sxs-lookup"><span data-stu-id="43513-109">id</span></span>|<span data-ttu-id="43513-110">Kalıcı bir tür için benzersiz bir tanımlayıcı belirten bir dize içeren gerekli bir öznitelik.</span><span class="sxs-lookup"><span data-stu-id="43513-110">A required attribute that contains a string that specifies a unique identifier for a persistable type.</span></span>|  
|<span data-ttu-id="43513-111">name</span><span class="sxs-lookup"><span data-stu-id="43513-111">name</span></span>|<span data-ttu-id="43513-112">Kalıcı tablo türünün adını belirten bir dize içeren isteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="43513-112">An optional attribute that contains a string that specifies the name of the persistable type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="43513-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="43513-113">Child Elements</span></span>  
 <span data-ttu-id="43513-114">Yok</span><span class="sxs-lookup"><span data-stu-id="43513-114">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="43513-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="43513-115">Parent Elements</span></span>  
  
|<span data-ttu-id="43513-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="43513-116">Element</span></span>|<span data-ttu-id="43513-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="43513-117">Description</span></span>|  
|-------------|-----------------|  
|[\<persistableTypes>](persistabletypes.md)|<span data-ttu-id="43513-118">`persistableType`Öğelerin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="43513-118">A collection of `persistableType` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="43513-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="43513-119">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComPersistableTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ComPersistableTypeElement>
- [\<comContracts>](comcontracts.md)
- [<span data-ttu-id="43513-120">COM+ uygulamalarıyla tümleştirme</span><span class="sxs-lookup"><span data-stu-id="43513-120">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="43513-121">Nasıl yapılır: COM+ Hizmet Ayarlarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="43513-121">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
