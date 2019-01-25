---
title: Etkinleştirme için &lt;tanılama&gt;
ms.date: 03/30/2017
ms.assetid: 1486e0eb-fe2a-46c3-b584-c924889477dd
ms.openlocfilehash: 5d8fcce28182dcac945655a52d829945a432a9b3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54723920"
---
# <a name="ltdiagnosticsgt-for-activation"></a><span data-ttu-id="4596f-102">Etkinleştirme için &lt;tanılama&gt;</span><span class="sxs-lookup"><span data-stu-id="4596f-102">&lt;diagnostics&gt; for Activation</span></span>
<span data-ttu-id="4596f-103">Windows Communication Foundation (WCF) dinleyicinin Tanılama işlevleri yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="4596f-103">Configures Windows Communication Foundation (WCF) listener's diagnostics functionalities.</span></span>  
  
 <span data-ttu-id="4596f-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="4596f-104">\<system.serviceModel.activation></span></span>  
<span data-ttu-id="4596f-105">\<Tanılama ></span><span class="sxs-lookup"><span data-stu-id="4596f-105">\<diagnostics></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4596f-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4596f-106">Syntax</span></span>  
  
```xml  
<configuration>
  <system.serviceModel.activation>
    <diagnostics performanceCountersEnabled="Boolean" />
  </system.serviceModel.activation>
</configuration>
```  
  
## <a name="type"></a><span data-ttu-id="4596f-107">Tür</span><span class="sxs-lookup"><span data-stu-id="4596f-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4596f-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4596f-108">Attributes and Elements</span></span>  
 <span data-ttu-id="4596f-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4596f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4596f-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4596f-110">Attributes</span></span>  
  
|<span data-ttu-id="4596f-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4596f-111">Attribute</span></span>|<span data-ttu-id="4596f-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4596f-112">Description</span></span>|  
|---------------|-----------------|  
|`performanceCountersEnabled`|<span data-ttu-id="4596f-113">Tanılama amacıyla performans sayaçlarının etkin olup olmadığını gösteren bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="4596f-113">A Boolean value that indicates whether performance counters are enabled for diagnostic purposes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4596f-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4596f-114">Child Elements</span></span>  
 <span data-ttu-id="4596f-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="4596f-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4596f-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4596f-116">Parent Elements</span></span>  
  
|<span data-ttu-id="4596f-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="4596f-117">Element</span></span>|<span data-ttu-id="4596f-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4596f-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4596f-119">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="4596f-119">\<system.serviceModel.activation></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|<span data-ttu-id="4596f-120">Dinleyici işlem SMSvcHost.exe için yapılandırma ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="4596f-120">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4596f-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4596f-121">See also</span></span>
- <xref:System.ServiceModel.Activation.Configuration.DiagnosticSection>
