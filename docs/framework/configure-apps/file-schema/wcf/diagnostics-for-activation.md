---
title: <diagnostics> Etkinleştirme için
ms.date: 03/30/2017
ms.assetid: 1486e0eb-fe2a-46c3-b584-c924889477dd
ms.openlocfilehash: c16f32357d40b9b69d52c525ce8a395a3de8fdb1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91192327"
---
# <a name="diagnostics-for-activation"></a><span data-ttu-id="585ac-102">\<diagnostics> Etkinleştirme için</span><span class="sxs-lookup"><span data-stu-id="585ac-102">\<diagnostics> for Activation</span></span>

<span data-ttu-id="585ac-103">Windows Communication Foundation (WCF) dinleyicisinin tanılama işlevlerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="585ac-103">Configures Windows Communication Foundation (WCF) listener's diagnostics functionalities.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<diagnostics>**  
  
## <a name="syntax"></a><span data-ttu-id="585ac-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="585ac-104">Syntax</span></span>  
  
```xml  
<configuration>
  <system.serviceModel.activation>
    <diagnostics performanceCountersEnabled="Boolean" />
  </system.serviceModel.activation>
</configuration>
```  
  
## <a name="type"></a><span data-ttu-id="585ac-105">Tür</span><span class="sxs-lookup"><span data-stu-id="585ac-105">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="585ac-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="585ac-106">Attributes and Elements</span></span>  

 <span data-ttu-id="585ac-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="585ac-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="585ac-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="585ac-108">Attributes</span></span>  
  
|<span data-ttu-id="585ac-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="585ac-109">Attribute</span></span>|<span data-ttu-id="585ac-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="585ac-110">Description</span></span>|  
|---------------|-----------------|  
|`performanceCountersEnabled`|<span data-ttu-id="585ac-111">Tanılama amacıyla performans sayaçlarının etkin olup olmadığını gösteren bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="585ac-111">A Boolean value that indicates whether performance counters are enabled for diagnostic purposes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="585ac-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="585ac-112">Child Elements</span></span>  

 <span data-ttu-id="585ac-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="585ac-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="585ac-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="585ac-114">Parent Elements</span></span>  
  
|<span data-ttu-id="585ac-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="585ac-115">Element</span></span>|<span data-ttu-id="585ac-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="585ac-116">Description</span></span>|  
|-------------|-----------------|  
|[\<system.serviceModel.activation>](system-servicemodel-activation.md)|<span data-ttu-id="585ac-117">SMSvcHost.exe dinleyici işlemi için yapılandırma ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="585ac-117">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="585ac-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="585ac-118">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.DiagnosticSection>
