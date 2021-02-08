---
description: 'Hakkında daha fazla bilgi edinin: <timeOuts>'
title: <timeOuts>
ms.date: 03/30/2017
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
ms.openlocfilehash: 097569d1742f6486ddfb5fb3c3d98ba106424f45
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786596"
---
# \<timeOuts>

<span data-ttu-id="c2478-102">Hizmet ana bilgisayarının açması veya kapatılması için izin verilen zaman aralığını belirten bir yapılandırma öğesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c2478-102">Represents a configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<host>**](host.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<timeOuts>**  
  
## <a name="syntax"></a><span data-ttu-id="c2478-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="c2478-103">Syntax</span></span>  
  
```xml  
<timeOuts closeTimeout="TimeSpan"
          openTimeout="TimeSpan" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c2478-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c2478-104">Attributes and Elements</span></span>  

 <span data-ttu-id="c2478-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c2478-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c2478-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c2478-106">Attributes</span></span>  
  
|<span data-ttu-id="c2478-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c2478-107">Attribute</span></span>|<span data-ttu-id="c2478-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c2478-108">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="c2478-109"><xref:System.TimeSpan>Hizmet ana bilgisayarının kapanması için izin verilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="c2478-109">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to close.</span></span>|  
|`openTimeout`|<span data-ttu-id="c2478-110"><xref:System.TimeSpan>Hizmet ana bilgisayarının açması için izin verilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="c2478-110">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to open.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c2478-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c2478-111">Child Elements</span></span>  

 <span data-ttu-id="c2478-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="c2478-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c2478-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c2478-113">Parent Elements</span></span>  
  
|<span data-ttu-id="c2478-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="c2478-114">Element</span></span>|<span data-ttu-id="c2478-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c2478-115">Description</span></span>|  
|-------------|-----------------|  
|[\<host>](host.md)|<span data-ttu-id="c2478-116">Bir hizmet ana bilgisayarı için ayarları belirten bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="c2478-116">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c2478-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c2478-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="c2478-118">Hosting</span><span class="sxs-lookup"><span data-stu-id="c2478-118">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
