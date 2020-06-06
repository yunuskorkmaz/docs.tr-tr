---
title: <timeOuts>
ms.date: 03/30/2017
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
ms.openlocfilehash: b9c67ac03f0eb73a2a4cdd43ab48fe12871a1cc3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70854970"
---
# \<timeOuts>
<span data-ttu-id="5c7fa-101">Hizmet ana bilgisayarının açması veya kapatılması için izin verilen zaman aralığını belirten bir yapılandırma öğesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5c7fa-101">Represents a configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<host>**](host.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<timeOuts>**  
  
## <a name="syntax"></a><span data-ttu-id="5c7fa-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5c7fa-102">Syntax</span></span>  
  
```xml  
<timeOuts closeTimeout="TimeSpan"
          openTimeout="TimeSpan" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5c7fa-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5c7fa-103">Attributes and Elements</span></span>  
 <span data-ttu-id="5c7fa-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5c7fa-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5c7fa-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5c7fa-105">Attributes</span></span>  
  
|<span data-ttu-id="5c7fa-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5c7fa-106">Attribute</span></span>|<span data-ttu-id="5c7fa-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5c7fa-107">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="5c7fa-108"><xref:System.TimeSpan>Hizmet ana bilgisayarının kapanması için izin verilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="5c7fa-108">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to close.</span></span>|  
|`openTimeout`|<span data-ttu-id="5c7fa-109"><xref:System.TimeSpan>Hizmet ana bilgisayarının açması için izin verilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="5c7fa-109">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to open.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5c7fa-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5c7fa-110">Child Elements</span></span>  
 <span data-ttu-id="5c7fa-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="5c7fa-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5c7fa-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5c7fa-112">Parent Elements</span></span>  
  
|<span data-ttu-id="5c7fa-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="5c7fa-113">Element</span></span>|<span data-ttu-id="5c7fa-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5c7fa-114">Description</span></span>|  
|-------------|-----------------|  
|[\<host>](host.md)|<span data-ttu-id="5c7fa-115">Bir hizmet ana bilgisayarı için ayarları belirten bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="5c7fa-115">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5c7fa-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5c7fa-116">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="5c7fa-117">Hosting</span><span class="sxs-lookup"><span data-stu-id="5c7fa-117">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
