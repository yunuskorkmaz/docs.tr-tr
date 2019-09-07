---
title: <diagnostics>Etkinleştirme için
ms.date: 03/30/2017
ms.assetid: 1486e0eb-fe2a-46c3-b584-c924889477dd
ms.openlocfilehash: 33b2cd4c5ae1b4076892a61aa7e2b927efa1ddc1
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400405"
---
# <a name="diagnostics-for-activation"></a><span data-ttu-id="cf736-102">\<Etkinleştirme için tanılama ></span><span class="sxs-lookup"><span data-stu-id="cf736-102">\<diagnostics> for Activation</span></span>
<span data-ttu-id="cf736-103">Windows Communication Foundation (WCF) dinleyicisinin tanılama işlevlerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="cf736-103">Configures Windows Communication Foundation (WCF) listener's diagnostics functionalities.</span></span>  
  
<span data-ttu-id="cf736-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="cf736-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="cf736-105">&nbsp;&nbsp;[ **\<System. serviceModel. Activation >** ](system-servicemodel-activation.md)</span><span class="sxs-lookup"><span data-stu-id="cf736-105">&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)</span></span>\
<span data-ttu-id="cf736-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<Tanılama >**</span><span class="sxs-lookup"><span data-stu-id="cf736-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<diagnostics>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf736-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cf736-107">Syntax</span></span>  
  
```xml  
<configuration>
  <system.serviceModel.activation>
    <diagnostics performanceCountersEnabled="Boolean" />
  </system.serviceModel.activation>
</configuration>
```  
  
## <a name="type"></a><span data-ttu-id="cf736-108">Tür</span><span class="sxs-lookup"><span data-stu-id="cf736-108">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cf736-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="cf736-109">Attributes and Elements</span></span>  
 <span data-ttu-id="cf736-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cf736-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cf736-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="cf736-111">Attributes</span></span>  
  
|<span data-ttu-id="cf736-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="cf736-112">Attribute</span></span>|<span data-ttu-id="cf736-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cf736-113">Description</span></span>|  
|---------------|-----------------|  
|`performanceCountersEnabled`|<span data-ttu-id="cf736-114">Tanılama amacıyla performans sayaçlarının etkin olup olmadığını gösteren bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="cf736-114">A Boolean value that indicates whether performance counters are enabled for diagnostic purposes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cf736-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="cf736-115">Child Elements</span></span>  
 <span data-ttu-id="cf736-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="cf736-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cf736-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="cf736-117">Parent Elements</span></span>  
  
|<span data-ttu-id="cf736-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="cf736-118">Element</span></span>|<span data-ttu-id="cf736-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cf736-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cf736-120">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="cf736-120">\<system.serviceModel.activation></span></span>](system-servicemodel-activation.md)|<span data-ttu-id="cf736-121">SMSvcHost. exe dinleyici işleminin yapılandırma ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="cf736-121">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cf736-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cf736-122">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.DiagnosticSection>
