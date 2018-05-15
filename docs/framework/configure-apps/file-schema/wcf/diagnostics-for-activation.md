---
title: Etkinleştirme için &lt;tanılama&gt;
ms.date: 03/30/2017
ms.assetid: 1486e0eb-fe2a-46c3-b584-c924889477dd
ms.openlocfilehash: 4e5332eed87ded51cebcd614f45cbc8e80e570fb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltdiagnosticsgt-for-activation"></a><span data-ttu-id="ca821-102">Etkinleştirme için &lt;tanılama&gt;</span><span class="sxs-lookup"><span data-stu-id="ca821-102">&lt;diagnostics&gt; for Activation</span></span>
<span data-ttu-id="ca821-103">Windows Communication Foundation (WCF) dinleyici'nın Tanılama işlevleri yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="ca821-103">Configures Windows Communication Foundation (WCF) listener's diagnostics functionalities.</span></span>  
  
 <span data-ttu-id="ca821-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="ca821-104">\<system.serviceModel.activation></span></span>  
<span data-ttu-id="ca821-105">\<Tanılama ></span><span class="sxs-lookup"><span data-stu-id="ca821-105">\<diagnostics></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca821-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ca821-106">Syntax</span></span>  
  
```xml  
<configuration>  
   <system.serviceModel.activation>  
       <diagnostics performanceCountersEnabled="Boolean" />  
   </system.serviceModel.activation>  
</configuration>  
```  
  
## <a name="type"></a><span data-ttu-id="ca821-107">Tür</span><span class="sxs-lookup"><span data-stu-id="ca821-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ca821-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ca821-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ca821-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ca821-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ca821-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ca821-110">Attributes</span></span>  
  
|<span data-ttu-id="ca821-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ca821-111">Attribute</span></span>|<span data-ttu-id="ca821-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ca821-112">Description</span></span>|  
|---------------|-----------------|  
|`performanceCountersEnabled`|<span data-ttu-id="ca821-113">Performans sayaçları tanılama amacıyla etkin olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="ca821-113">A Boolean value that indicates whether performance counters are enabled for diagnostic purposes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ca821-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ca821-114">Child Elements</span></span>  
 <span data-ttu-id="ca821-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="ca821-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ca821-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ca821-116">Parent Elements</span></span>  
  
|<span data-ttu-id="ca821-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="ca821-117">Element</span></span>|<span data-ttu-id="ca821-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ca821-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ca821-119">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="ca821-119">\<system.serviceModel.activation></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|<span data-ttu-id="ca821-120">Dinleyici işlem SMSvcHost.exe için yapılandırma ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="ca821-120">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ca821-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ca821-121">See Also</span></span>  
 <xref:System.ServiceModel.Activation.Configuration.DiagnosticSection>
