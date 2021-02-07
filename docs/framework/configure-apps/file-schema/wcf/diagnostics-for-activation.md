---
description: 'Daha fazla bilgi edinin: <diagnostics> etkinleştirme için'
title: <diagnostics> Etkinleştirme için
ms.date: 03/30/2017
ms.assetid: 1486e0eb-fe2a-46c3-b584-c924889477dd
ms.openlocfilehash: aa1529a478ac367ea89c8926571c6c6f2f57cf74
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698368"
---
# <a name="diagnostics-for-activation"></a><span data-ttu-id="00884-103">\<diagnostics> Etkinleştirme için</span><span class="sxs-lookup"><span data-stu-id="00884-103">\<diagnostics> for Activation</span></span>

<span data-ttu-id="00884-104">Windows Communication Foundation (WCF) dinleyicisinin tanılama işlevlerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="00884-104">Configures Windows Communication Foundation (WCF) listener's diagnostics functionalities.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<diagnostics>**  
  
## <a name="syntax"></a><span data-ttu-id="00884-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="00884-105">Syntax</span></span>  
  
```xml  
<configuration>
  <system.serviceModel.activation>
    <diagnostics performanceCountersEnabled="Boolean" />
  </system.serviceModel.activation>
</configuration>
```  
  
## <a name="type"></a><span data-ttu-id="00884-106">Tür</span><span class="sxs-lookup"><span data-stu-id="00884-106">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="00884-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="00884-107">Attributes and Elements</span></span>  

 <span data-ttu-id="00884-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="00884-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="00884-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="00884-109">Attributes</span></span>  
  
|<span data-ttu-id="00884-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="00884-110">Attribute</span></span>|<span data-ttu-id="00884-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="00884-111">Description</span></span>|  
|---------------|-----------------|  
|`performanceCountersEnabled`|<span data-ttu-id="00884-112">Tanılama amacıyla performans sayaçlarının etkin olup olmadığını gösteren bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="00884-112">A Boolean value that indicates whether performance counters are enabled for diagnostic purposes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="00884-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="00884-113">Child Elements</span></span>  

 <span data-ttu-id="00884-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="00884-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="00884-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="00884-115">Parent Elements</span></span>  
  
|<span data-ttu-id="00884-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="00884-116">Element</span></span>|<span data-ttu-id="00884-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="00884-117">Description</span></span>|  
|-------------|-----------------|  
|[\<system.serviceModel.activation>](system-servicemodel-activation.md)|<span data-ttu-id="00884-118">SMSvcHost.exe dinleyici işlemi için yapılandırma ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="00884-118">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="00884-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="00884-119">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.DiagnosticSection>
