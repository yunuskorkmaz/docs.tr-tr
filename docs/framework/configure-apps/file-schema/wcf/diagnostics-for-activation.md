---
title: <diagnostics> Etkinleştirme için
ms.date: 03/30/2017
ms.assetid: 1486e0eb-fe2a-46c3-b584-c924889477dd
ms.openlocfilehash: 30456963a7d74a93e39bb1fddc0910daae97f039
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59203814"
---
# <a name="diagnostics-for-activation"></a><span data-ttu-id="e70c8-102">\<Tanılama > etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="e70c8-102">\<diagnostics> for Activation</span></span>
<span data-ttu-id="e70c8-103">Windows Communication Foundation (WCF) dinleyicinin Tanılama işlevleri yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="e70c8-103">Configures Windows Communication Foundation (WCF) listener's diagnostics functionalities.</span></span>  
  
 <span data-ttu-id="e70c8-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="e70c8-104">\<system.serviceModel.activation></span></span>  
<span data-ttu-id="e70c8-105">\<Tanılama ></span><span class="sxs-lookup"><span data-stu-id="e70c8-105">\<diagnostics></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e70c8-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e70c8-106">Syntax</span></span>  
  
```xml  
<configuration>
  <system.serviceModel.activation>
    <diagnostics performanceCountersEnabled="Boolean" />
  </system.serviceModel.activation>
</configuration>
```  
  
## <a name="type"></a><span data-ttu-id="e70c8-107">Tür</span><span class="sxs-lookup"><span data-stu-id="e70c8-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e70c8-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e70c8-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e70c8-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e70c8-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e70c8-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e70c8-110">Attributes</span></span>  
  
|<span data-ttu-id="e70c8-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e70c8-111">Attribute</span></span>|<span data-ttu-id="e70c8-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e70c8-112">Description</span></span>|  
|---------------|-----------------|  
|`performanceCountersEnabled`|<span data-ttu-id="e70c8-113">Tanılama amacıyla performans sayaçlarının etkin olup olmadığını gösteren bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="e70c8-113">A Boolean value that indicates whether performance counters are enabled for diagnostic purposes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e70c8-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e70c8-114">Child Elements</span></span>  
 <span data-ttu-id="e70c8-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="e70c8-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e70c8-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e70c8-116">Parent Elements</span></span>  
  
|<span data-ttu-id="e70c8-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="e70c8-117">Element</span></span>|<span data-ttu-id="e70c8-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e70c8-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e70c8-119">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="e70c8-119">\<system.serviceModel.activation></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|<span data-ttu-id="e70c8-120">Dinleyici işlem SMSvcHost.exe için yapılandırma ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="e70c8-120">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e70c8-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e70c8-121">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.DiagnosticSection>
