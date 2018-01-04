---
title: '&lt;protocolMapping&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5076644b-1f33-4f26-9488-87de9fcda04c
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b2d932e8a7fbe9c1457b5cea5106b69317227a21
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltprotocolmappinggt"></a><span data-ttu-id="b82b9-102">&lt;protocolMapping&gt;</span><span class="sxs-lookup"><span data-stu-id="b82b9-102">&lt;protocolMapping&gt;</span></span>
<span data-ttu-id="b82b9-103">Aktarım Protokolü düzenleri (örn., http, net.tcp, net.pipe, vb.) ve WCF bağlamaları arasında varsayılan protokolü eşleme kümesini tanımlamak için yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b82b9-103">Represents a configuration section for defining a set of default protocol mapping between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and WCF bindings.</span></span> <span data-ttu-id="b82b9-104">Varsayılan uç noktalar çalışma zamanında oluştururken [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] yapılandırılmış eşlemelerin arar ve adresine göre hangi belirli bir için kullanılacak bağlama karar verir.</span><span class="sxs-lookup"><span data-stu-id="b82b9-104">When creating default endpoints at runtime, [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] looks at the configured mappings and decides on which binding to use for a particular based address.</span></span>  
  
 <span data-ttu-id="b82b9-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="b82b9-105">\<system.serviceModel></span></span>  
<span data-ttu-id="b82b9-106">\<protocolMapping ></span><span class="sxs-lookup"><span data-stu-id="b82b9-106">\<protocolMapping></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b82b9-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b82b9-107">Syntax</span></span>  
  
```xml
   <protocolMapping>    <add binding="String"         bindingConfiguration="String"         scheme="http/net.msmq/net.pipe/net.tcp"/></protocolMapping>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b82b9-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b82b9-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b82b9-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b82b9-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b82b9-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b82b9-110">Attributes</span></span>  
 <span data-ttu-id="b82b9-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="b82b9-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b82b9-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b82b9-112">Child Elements</span></span>  
  
|<span data-ttu-id="b82b9-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="b82b9-113">Element</span></span>|<span data-ttu-id="b82b9-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b82b9-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b82b9-115">\<filtreleri ></span><span class="sxs-lookup"><span data-stu-id="b82b9-115">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="b82b9-116">Bir Aktarım Protokolü düzeni (örn., http, net.tcp, net.pipe, vb.) ve WCF bağlama varsayılan protokolü eşlemesini içerir.</span><span class="sxs-lookup"><span data-stu-id="b82b9-116">Contains a default protocol mapping between a transport protocol scheme (e.g., http, net.tcp, net.pipe, etc.) and a WCF binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b82b9-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b82b9-117">Parent Elements</span></span>  
  
|<span data-ttu-id="b82b9-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="b82b9-118">Element</span></span>|<span data-ttu-id="b82b9-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b82b9-119">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b82b9-120">Sistem.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="b82b9-120">system.ServiceModel</span></span>|<span data-ttu-id="b82b9-121">Tüm WCF yapılandırma öğelerinin kök öğesi.</span><span class="sxs-lookup"><span data-stu-id="b82b9-121">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b82b9-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="b82b9-122">Example</span></span>  
 <span data-ttu-id="b82b9-123">Aşağıdaki yapılandırma örnek machine.config dosyasındaki varsayılan protokolü eşlemeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="b82b9-123">The following configuration example shows the default protocol mapping in the machine.config file.</span></span> <span data-ttu-id="b82b9-124">Machine.config dosyasının değiştirerek bu varsayılan eşleme makine düzeyinde geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b82b9-124">You can override this default mapping at the machine level by modifying the machine.config file.</span></span> <span data-ttu-id="b82b9-125">Veya yalnızca bir uygulama kapsamında geçersiz kılmak isterseniz, bu bölümde, uygulama yapılandırma dosyasında geçersiz kılmak ve tek protokol düzenleri için eşleme değiştirin.</span><span class="sxs-lookup"><span data-stu-id="b82b9-125">Or if you would only like to override it within the scope of an application, you can override this section within your application configuration file and change the mapping for individual protocol schemes.</span></span>  
  
```xml  
<protocolMapping>  
        <add scheme="http" binding="basicHttpBinding"/>  
        <add scheme="net.tcp" binding="netTcpBinding"/>  
        <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
        <add scheme="net.msmq" binding="netMsmqBinding"/>  
</protocolMapping>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b82b9-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b82b9-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>    
