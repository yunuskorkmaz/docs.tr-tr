---
title: <diagnostics> Etkinleştirme için
ms.date: 03/30/2017
ms.assetid: 1486e0eb-fe2a-46c3-b584-c924889477dd
ms.openlocfilehash: ac235b9a3c125cd3fe63ccd899e2ff92d4d3f31b
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55278462"
---
# <a name="diagnostics-for-activation"></a><span data-ttu-id="2b44c-102">\<Tanılama > etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="2b44c-102">\<diagnostics> for Activation</span></span>
<span data-ttu-id="2b44c-103">Windows Communication Foundation (WCF) dinleyicinin Tanılama işlevleri yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="2b44c-103">Configures Windows Communication Foundation (WCF) listener's diagnostics functionalities.</span></span>  
  
 <span data-ttu-id="2b44c-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="2b44c-104">\<system.serviceModel.activation></span></span>  
<span data-ttu-id="2b44c-105">\<Tanılama ></span><span class="sxs-lookup"><span data-stu-id="2b44c-105">\<diagnostics></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b44c-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2b44c-106">Syntax</span></span>  
  
```xml  
<configuration>
  <system.serviceModel.activation>
    <diagnostics performanceCountersEnabled="Boolean" />
  </system.serviceModel.activation>
</configuration>
```  
  
## <a name="type"></a><span data-ttu-id="2b44c-107">Tür</span><span class="sxs-lookup"><span data-stu-id="2b44c-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2b44c-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2b44c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="2b44c-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2b44c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2b44c-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2b44c-110">Attributes</span></span>  
  
|<span data-ttu-id="2b44c-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="2b44c-111">Attribute</span></span>|<span data-ttu-id="2b44c-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2b44c-112">Description</span></span>|  
|---------------|-----------------|  
|`performanceCountersEnabled`|<span data-ttu-id="2b44c-113">Tanılama amacıyla performans sayaçlarının etkin olup olmadığını gösteren bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="2b44c-113">A Boolean value that indicates whether performance counters are enabled for diagnostic purposes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2b44c-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2b44c-114">Child Elements</span></span>  
 <span data-ttu-id="2b44c-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="2b44c-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2b44c-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2b44c-116">Parent Elements</span></span>  
  
|<span data-ttu-id="2b44c-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="2b44c-117">Element</span></span>|<span data-ttu-id="2b44c-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2b44c-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2b44c-119">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="2b44c-119">\<system.serviceModel.activation></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|<span data-ttu-id="2b44c-120">Dinleyici işlem SMSvcHost.exe için yapılandırma ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="2b44c-120">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2b44c-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2b44c-121">See also</span></span>
- <xref:System.ServiceModel.Activation.Configuration.DiagnosticSection>
