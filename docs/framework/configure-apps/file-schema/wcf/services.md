---
title: <services>
ms.date: 03/30/2017
ms.assetid: 80d76ba9-2058-48ad-9b91-5e4be7e5c113
ms.openlocfilehash: 1f9cb6c95fa14a5b8a55cc561699e2a07e1dc80c
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399591"
---
# <a name="services"></a><span data-ttu-id="d0b45-101">\<Hizmetler ></span><span class="sxs-lookup"><span data-stu-id="d0b45-101">\<services></span></span>
<span data-ttu-id="d0b45-102">Hizmetler, yapılandırma dosyasının `services` bölümünde tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="d0b45-102">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="d0b45-103">Her hizmetin kendi `service` yapılandırma bölümü vardır.</span><span class="sxs-lookup"><span data-stu-id="d0b45-103">Each service has its own `service` configuration section.</span></span>  
  
<span data-ttu-id="d0b45-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d0b45-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d0b45-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="d0b45-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="d0b45-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<Hizmetler >**</span><span class="sxs-lookup"><span data-stu-id="d0b45-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<services>**</span></span>  
## <a name="syntax"></a><span data-ttu-id="d0b45-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d0b45-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service>
    </service>
  </services>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d0b45-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d0b45-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d0b45-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d0b45-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d0b45-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d0b45-110">Attributes</span></span>  
 <span data-ttu-id="d0b45-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="d0b45-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d0b45-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d0b45-112">Child Elements</span></span>  
  
|<span data-ttu-id="d0b45-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="d0b45-113">Element</span></span>|<span data-ttu-id="d0b45-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d0b45-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d0b45-115">\<hizmet ></span><span class="sxs-lookup"><span data-stu-id="d0b45-115">\<service></span></span>](service.md)|<span data-ttu-id="d0b45-116">Belirli bir hizmetin hizmet sözleşmesini, davranışını ve uç noktalarını tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="d0b45-116">Define the service contract, behavior, and endpoints of the particular service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d0b45-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d0b45-117">Parent Elements</span></span>  
  
|<span data-ttu-id="d0b45-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="d0b45-118">Element</span></span>|<span data-ttu-id="d0b45-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d0b45-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d0b45-120">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="d0b45-120">\<system.serviceModel></span></span>](system-servicemodel.md)|<span data-ttu-id="d0b45-121">Tüm Windows Communication Foundation (WCF) yapılandırma öğelerinin kök öğesi.</span><span class="sxs-lookup"><span data-stu-id="d0b45-121">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d0b45-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d0b45-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServicesSection>
