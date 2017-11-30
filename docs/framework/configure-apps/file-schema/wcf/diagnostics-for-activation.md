---
title: "Etkinleştirme için &lt;tanılama&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1486e0eb-fe2a-46c3-b584-c924889477dd
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 29f2e56dd18da9dc3ce3206f5c3c80f4a47a7ff0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="ltdiagnosticsgt-for-activation"></a><span data-ttu-id="c4bbc-102">Etkinleştirme için &lt;tanılama&gt;</span><span class="sxs-lookup"><span data-stu-id="c4bbc-102">&lt;diagnostics&gt; for Activation</span></span>
<span data-ttu-id="c4bbc-103">Yapılandırır [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] dinleyicisi'nın Tanılama işlevleri.</span><span class="sxs-lookup"><span data-stu-id="c4bbc-103">Configures [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] listener's diagnostics functionalities.</span></span>  
  
 <span data-ttu-id="c4bbc-104">\<system.serviceModel.activation ></span><span class="sxs-lookup"><span data-stu-id="c4bbc-104">\<system.serviceModel.activation></span></span>  
<span data-ttu-id="c4bbc-105">\<Tanılama ></span><span class="sxs-lookup"><span data-stu-id="c4bbc-105">\<diagnostics></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4bbc-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c4bbc-106">Syntax</span></span>  
  
```xml  
<configuration>  
   <system.serviceModel.activation>  
       <diagnostics performanceCountersEnabled="Boolean" />  
   </system.serviceModel.activation>  
</configuration>  
```  
  
## <a name="type"></a><span data-ttu-id="c4bbc-107">Tür</span><span class="sxs-lookup"><span data-stu-id="c4bbc-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c4bbc-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c4bbc-108">Attributes and Elements</span></span>  
 <span data-ttu-id="c4bbc-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c4bbc-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c4bbc-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c4bbc-110">Attributes</span></span>  
  
|<span data-ttu-id="c4bbc-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c4bbc-111">Attribute</span></span>|<span data-ttu-id="c4bbc-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c4bbc-112">Description</span></span>|  
|---------------|-----------------|  
|`performanceCountersEnabled`|<span data-ttu-id="c4bbc-113">Performans sayaçları tanılama amacıyla etkin olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="c4bbc-113">A Boolean value that indicates whether performance counters are enabled for diagnostic purposes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c4bbc-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c4bbc-114">Child Elements</span></span>  
 <span data-ttu-id="c4bbc-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="c4bbc-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c4bbc-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c4bbc-116">Parent Elements</span></span>  
  
|<span data-ttu-id="c4bbc-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="c4bbc-117">Element</span></span>|<span data-ttu-id="c4bbc-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c4bbc-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c4bbc-119">\<system.serviceModel.activation ></span><span class="sxs-lookup"><span data-stu-id="c4bbc-119">\<system.serviceModel.activation></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|<span data-ttu-id="c4bbc-120">Dinleyici işlem SMSvcHost.exe için yapılandırma ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="c4bbc-120">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c4bbc-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c4bbc-121">See Also</span></span>  
 <xref:System.ServiceModel.Activation.Configuration.DiagnosticSection>
