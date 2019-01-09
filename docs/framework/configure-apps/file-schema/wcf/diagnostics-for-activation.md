---
title: Etkinleştirme için &lt;tanılama&gt;
ms.date: 03/30/2017
ms.assetid: 1486e0eb-fe2a-46c3-b584-c924889477dd
ms.openlocfilehash: 28f051a7ab06dbc1b40f804c56071818eb37e88b
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54144983"
---
# <a name="ltdiagnosticsgt-for-activation"></a><span data-ttu-id="3a87a-102">Etkinleştirme için &lt;tanılama&gt;</span><span class="sxs-lookup"><span data-stu-id="3a87a-102">&lt;diagnostics&gt; for Activation</span></span>
<span data-ttu-id="3a87a-103">Windows Communication Foundation (WCF) dinleyicinin Tanılama işlevleri yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="3a87a-103">Configures Windows Communication Foundation (WCF) listener's diagnostics functionalities.</span></span>  
  
 <span data-ttu-id="3a87a-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="3a87a-104">\<system.serviceModel.activation></span></span>  
<span data-ttu-id="3a87a-105">\<Tanılama ></span><span class="sxs-lookup"><span data-stu-id="3a87a-105">\<diagnostics></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a87a-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3a87a-106">Syntax</span></span>  
  
```xml  
<configuration>
  <system.serviceModel.activation>
    <diagnostics performanceCountersEnabled="Boolean" />
  </system.serviceModel.activation>
</configuration>
```  
  
## <a name="type"></a><span data-ttu-id="3a87a-107">Tür</span><span class="sxs-lookup"><span data-stu-id="3a87a-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3a87a-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3a87a-108">Attributes and Elements</span></span>  
 <span data-ttu-id="3a87a-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3a87a-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3a87a-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3a87a-110">Attributes</span></span>  
  
|<span data-ttu-id="3a87a-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3a87a-111">Attribute</span></span>|<span data-ttu-id="3a87a-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3a87a-112">Description</span></span>|  
|---------------|-----------------|  
|`performanceCountersEnabled`|<span data-ttu-id="3a87a-113">Tanılama amacıyla performans sayaçlarının etkin olup olmadığını gösteren bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="3a87a-113">A Boolean value that indicates whether performance counters are enabled for diagnostic purposes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3a87a-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3a87a-114">Child Elements</span></span>  
 <span data-ttu-id="3a87a-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="3a87a-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3a87a-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3a87a-116">Parent Elements</span></span>  
  
|<span data-ttu-id="3a87a-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="3a87a-117">Element</span></span>|<span data-ttu-id="3a87a-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3a87a-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3a87a-119">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="3a87a-119">\<system.serviceModel.activation></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|<span data-ttu-id="3a87a-120">Dinleyici işlem SMSvcHost.exe için yapılandırma ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="3a87a-120">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3a87a-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3a87a-121">See Also</span></span>  
 <xref:System.ServiceModel.Activation.Configuration.DiagnosticSection>
