---
title: <diagnostics>Etkinleştirme için
ms.date: 03/30/2017
ms.assetid: 1486e0eb-fe2a-46c3-b584-c924889477dd
ms.openlocfilehash: 33b2cd4c5ae1b4076892a61aa7e2b927efa1ddc1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400405"
---
# <a name="diagnostics-for-activation"></a><span data-ttu-id="3014f-102">\<diagnostics>Etkinleştirme için</span><span class="sxs-lookup"><span data-stu-id="3014f-102">\<diagnostics> for Activation</span></span>
<span data-ttu-id="3014f-103">Windows Communication Foundation (WCF) dinleyicisinin tanılama işlevlerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="3014f-103">Configures Windows Communication Foundation (WCF) listener's diagnostics functionalities.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<diagnostics>**  
  
## <a name="syntax"></a><span data-ttu-id="3014f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3014f-104">Syntax</span></span>  
  
```xml  
<configuration>
  <system.serviceModel.activation>
    <diagnostics performanceCountersEnabled="Boolean" />
  </system.serviceModel.activation>
</configuration>
```  
  
## <a name="type"></a><span data-ttu-id="3014f-105">Tür</span><span class="sxs-lookup"><span data-stu-id="3014f-105">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3014f-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3014f-106">Attributes and Elements</span></span>  
 <span data-ttu-id="3014f-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3014f-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3014f-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3014f-108">Attributes</span></span>  
  
|<span data-ttu-id="3014f-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3014f-109">Attribute</span></span>|<span data-ttu-id="3014f-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3014f-110">Description</span></span>|  
|---------------|-----------------|  
|`performanceCountersEnabled`|<span data-ttu-id="3014f-111">Tanılama amacıyla performans sayaçlarının etkin olup olmadığını gösteren bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="3014f-111">A Boolean value that indicates whether performance counters are enabled for diagnostic purposes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3014f-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3014f-112">Child Elements</span></span>  
 <span data-ttu-id="3014f-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="3014f-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3014f-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3014f-114">Parent Elements</span></span>  
  
|<span data-ttu-id="3014f-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="3014f-115">Element</span></span>|<span data-ttu-id="3014f-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3014f-116">Description</span></span>|  
|-------------|-----------------|  
|[\<system.serviceModel.activation>](system-servicemodel-activation.md)|<span data-ttu-id="3014f-117">SMSvcHost. exe dinleyici işleminin yapılandırma ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="3014f-117">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3014f-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3014f-118">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.DiagnosticSection>
