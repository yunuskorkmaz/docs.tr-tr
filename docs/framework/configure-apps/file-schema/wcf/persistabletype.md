---
title: <persistableType>
ms.date: 03/30/2017
ms.assetid: e5425fe6-523a-4076-aab4-2c2515b1d830
ms.openlocfilehash: 6425b21fe50865beb7bb2876ea478b415fbe3944
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91181524"
---
# \<persistableType>

<span data-ttu-id="5af32-101">Tüm kalıcı türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5af32-101">Specifies all the persistable types.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContracts>**](comcontracts.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContract>**](comcontract.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<persistableTypes>**](persistabletypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<persistableType>**  
  
## <a name="syntax"></a><span data-ttu-id="5af32-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="5af32-102">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="5af32-103">Tür</span><span class="sxs-lookup"><span data-stu-id="5af32-103">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5af32-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5af32-104">Attributes and Elements</span></span>  

 <span data-ttu-id="5af32-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5af32-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5af32-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5af32-106">Attributes</span></span>  
  
|<span data-ttu-id="5af32-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5af32-107">Attribute</span></span>|<span data-ttu-id="5af32-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5af32-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5af32-109">kimlik</span><span class="sxs-lookup"><span data-stu-id="5af32-109">id</span></span>|<span data-ttu-id="5af32-110">Kalıcı bir tür için benzersiz bir tanımlayıcı belirten bir dize içeren gerekli bir öznitelik.</span><span class="sxs-lookup"><span data-stu-id="5af32-110">A required attribute that contains a string that specifies a unique identifier for a persistable type.</span></span>|  
|<span data-ttu-id="5af32-111">name</span><span class="sxs-lookup"><span data-stu-id="5af32-111">name</span></span>|<span data-ttu-id="5af32-112">Kalıcı tablo türünün adını belirten bir dize içeren isteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="5af32-112">An optional attribute that contains a string that specifies the name of the persistable type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5af32-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5af32-113">Child Elements</span></span>  

 <span data-ttu-id="5af32-114">Yok</span><span class="sxs-lookup"><span data-stu-id="5af32-114">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5af32-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5af32-115">Parent Elements</span></span>  
  
|<span data-ttu-id="5af32-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="5af32-116">Element</span></span>|<span data-ttu-id="5af32-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5af32-117">Description</span></span>|  
|-------------|-----------------|  
|[\<persistableTypes>](persistabletypes.md)|<span data-ttu-id="5af32-118">`persistableType`Öğelerin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="5af32-118">A collection of `persistableType` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5af32-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5af32-119">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComPersistableTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ComPersistableTypeElement>
- [\<comContracts>](comcontracts.md)
- [<span data-ttu-id="5af32-120">COM+ uygulamalarıyla tümleştirme</span><span class="sxs-lookup"><span data-stu-id="5af32-120">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="5af32-121">Nasıl yapılır: COM+ Hizmet Ayarlarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="5af32-121">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
