---
title: <diagnostics>Etkinleştirme için
ms.date: 03/30/2017
ms.assetid: 1486e0eb-fe2a-46c3-b584-c924889477dd
ms.openlocfilehash: 543c41936921eda39017e07f1c97294b268a9141
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919215"
---
# <a name="diagnostics-for-activation"></a><span data-ttu-id="ca86f-102">\<Etkinleştirme için tanılama ></span><span class="sxs-lookup"><span data-stu-id="ca86f-102">\<diagnostics> for Activation</span></span>
<span data-ttu-id="ca86f-103">Windows Communication Foundation (WCF) dinleyicisinin tanılama işlevlerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="ca86f-103">Configures Windows Communication Foundation (WCF) listener's diagnostics functionalities.</span></span>  
  
 <span data-ttu-id="ca86f-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="ca86f-104">\<system.serviceModel.activation></span></span>  
<span data-ttu-id="ca86f-105">\<Tanılama ></span><span class="sxs-lookup"><span data-stu-id="ca86f-105">\<diagnostics></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca86f-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ca86f-106">Syntax</span></span>  
  
```xml  
<configuration>
  <system.serviceModel.activation>
    <diagnostics performanceCountersEnabled="Boolean" />
  </system.serviceModel.activation>
</configuration>
```  
  
## <a name="type"></a><span data-ttu-id="ca86f-107">Tür</span><span class="sxs-lookup"><span data-stu-id="ca86f-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ca86f-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ca86f-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ca86f-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ca86f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ca86f-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ca86f-110">Attributes</span></span>  
  
|<span data-ttu-id="ca86f-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ca86f-111">Attribute</span></span>|<span data-ttu-id="ca86f-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ca86f-112">Description</span></span>|  
|---------------|-----------------|  
|`performanceCountersEnabled`|<span data-ttu-id="ca86f-113">Tanılama amacıyla performans sayaçlarının etkin olup olmadığını gösteren bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="ca86f-113">A Boolean value that indicates whether performance counters are enabled for diagnostic purposes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ca86f-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ca86f-114">Child Elements</span></span>  
 <span data-ttu-id="ca86f-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="ca86f-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ca86f-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ca86f-116">Parent Elements</span></span>  
  
|<span data-ttu-id="ca86f-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="ca86f-117">Element</span></span>|<span data-ttu-id="ca86f-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ca86f-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ca86f-119">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="ca86f-119">\<system.serviceModel.activation></span></span>](system-servicemodel-activation.md)|<span data-ttu-id="ca86f-120">SMSvcHost. exe dinleyici işleminin yapılandırma ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="ca86f-120">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ca86f-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ca86f-121">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.DiagnosticSection>
