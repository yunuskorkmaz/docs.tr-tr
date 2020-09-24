---
title: <services>
ms.date: 03/30/2017
ms.assetid: 80d76ba9-2058-48ad-9b91-5e4be7e5c113
ms.openlocfilehash: b8cb5075ba41bed5a22b152a231c7213b326a62f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153722"
---
# \<services>

<span data-ttu-id="4634e-101">Hizmetler, `services` yapılandırma dosyasının bölümünde tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="4634e-101">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="4634e-102">Her hizmetin kendi `service` yapılandırma bölümü vardır.</span><span class="sxs-lookup"><span data-stu-id="4634e-102">Each service has its own `service` configuration section.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<services>**  
  
## <a name="syntax"></a><span data-ttu-id="4634e-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="4634e-103">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service>
    </service>
  </services>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4634e-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4634e-104">Attributes and Elements</span></span>  

 <span data-ttu-id="4634e-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4634e-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4634e-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4634e-106">Attributes</span></span>  

 <span data-ttu-id="4634e-107">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="4634e-107">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4634e-108">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4634e-108">Child Elements</span></span>  
  
|<span data-ttu-id="4634e-109">Öğe</span><span class="sxs-lookup"><span data-stu-id="4634e-109">Element</span></span>|<span data-ttu-id="4634e-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4634e-110">Description</span></span>|  
|-------------|-----------------|  
|[\<service>](service.md)|<span data-ttu-id="4634e-111">Belirli bir hizmetin hizmet sözleşmesini, davranışını ve uç noktalarını tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="4634e-111">Define the service contract, behavior, and endpoints of the particular service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4634e-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4634e-112">Parent Elements</span></span>  
  
|<span data-ttu-id="4634e-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="4634e-113">Element</span></span>|<span data-ttu-id="4634e-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4634e-114">Description</span></span>|  
|-------------|-----------------|  
|[\<system.serviceModel>](system-servicemodel.md)|<span data-ttu-id="4634e-115">Tüm Windows Communication Foundation (WCF) yapılandırma öğelerinin kök öğesi.</span><span class="sxs-lookup"><span data-stu-id="4634e-115">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4634e-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4634e-116">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServicesSection>
