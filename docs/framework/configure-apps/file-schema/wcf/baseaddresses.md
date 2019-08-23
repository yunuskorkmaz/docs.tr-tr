---
title: <baseAddresses>
ms.date: 03/30/2017
ms.assetid: 78918102-2898-46e0-9ea8-6b8afe65603e
ms.openlocfilehash: 059ea4e637ab906d1fde9807a73ac8341f81c574
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926417"
---
# <a name="baseaddresses"></a><span data-ttu-id="63422-101">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="63422-101">\<baseAddresses></span></span>
<span data-ttu-id="63422-102">Şirket içinde barındırılan bir `baseAddress` ortamdaki hizmet ana bilgisayarı için temel adres olan bir öğe koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="63422-102">Represents a collection of `baseAddress` elements, which are base addresses for a service host in a self-hosted environment.</span></span> <span data-ttu-id="63422-103">Bir temel adres varsa, uç noktalar temel adrese göre adreslerle yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="63422-103">If a base address is present, endpoints can be configured with addresses relative to the base address.</span></span>  
  
 <span data-ttu-id="63422-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="63422-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="63422-105">\<İstemci ></span><span class="sxs-lookup"><span data-stu-id="63422-105">\<client></span></span>  
<span data-ttu-id="63422-106">\<uç nokta ></span><span class="sxs-lookup"><span data-stu-id="63422-106">\<endpoint></span></span>  
<span data-ttu-id="63422-107">\<Ana bilgisayar ></span><span class="sxs-lookup"><span data-stu-id="63422-107">\<host></span></span>  
<span data-ttu-id="63422-108">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="63422-108">\<baseAddresses></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63422-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="63422-109">Syntax</span></span>  
  
```xml  
<baseAddresses>
  <add baseAddress="string" />
</baseAddresses>
```  
  
## <a name="type"></a><span data-ttu-id="63422-110">Tür</span><span class="sxs-lookup"><span data-stu-id="63422-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="63422-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="63422-111">Attributes and Elements</span></span>  
 <span data-ttu-id="63422-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="63422-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="63422-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="63422-113">Attributes</span></span>  
 <span data-ttu-id="63422-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="63422-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="63422-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="63422-115">Child Elements</span></span>  
  
|<span data-ttu-id="63422-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="63422-116">Element</span></span>|<span data-ttu-id="63422-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="63422-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="63422-118">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="63422-118">\<add></span></span>](add-of-baseaddresses.md)|<span data-ttu-id="63422-119">Hizmet ana bilgisayarı tarafından kullanılan taban adresleri belirten bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="63422-119">A configuration element that specifies the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="63422-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="63422-120">Parent Elements</span></span>  
  
|<span data-ttu-id="63422-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="63422-121">Element</span></span>|<span data-ttu-id="63422-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="63422-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="63422-123">\<Ana bilgisayar ></span><span class="sxs-lookup"><span data-stu-id="63422-123">\<host></span></span>](host.md)|<span data-ttu-id="63422-124">Bir hizmet ana bilgisayarı için ayarları belirten bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="63422-124">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="63422-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="63422-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [<span data-ttu-id="63422-126">Barındırma</span><span class="sxs-lookup"><span data-stu-id="63422-126">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
