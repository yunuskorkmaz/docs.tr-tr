---
title: '&lt;protocolMapping&gt; &lt;ekleme&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 08e62249-1641-41d1-91b1-66d7b46244e4
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 255cd8518bd9c6c6c199c75aa32ca086c801d23f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltaddgt-of-ltprotocolmappinggt"></a><span data-ttu-id="c978e-102">&lt;protocolMapping&gt; &lt;ekleme&gt;</span><span class="sxs-lookup"><span data-stu-id="c978e-102">&lt;add&gt; of &lt;protocolMapping&gt;</span></span>
<span data-ttu-id="c978e-103">Bir Aktarım Protokolü düzeni (örn., http, net.tcp, net.pipe, vb.) arasındaki bir varsayılan protokolü eşlemeyi temsil eder ve bir [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] bağlama.</span><span class="sxs-lookup"><span data-stu-id="c978e-103">Represents a default protocol mapping between a transport protocol scheme (e.g., http, net.tcp, net.pipe, etc.) and a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] binding.</span></span> <span data-ttu-id="c978e-104">Varsayılan uç noktalar çalışma zamanında oluştururken [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] yapılandırılmış eşlemelerin arar ve adresine göre hangi belirli bir için kullanılacak bağlama karar verir.</span><span class="sxs-lookup"><span data-stu-id="c978e-104">When creating default endpoints at runtime, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] looks at the configured mappings and decides on which binding to use for a particular based address.</span></span>  
  
 <span data-ttu-id="c978e-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="c978e-105">\<system.serviceModel></span></span>  
<span data-ttu-id="c978e-106">\<protocolMapping ></span><span class="sxs-lookup"><span data-stu-id="c978e-106">\<protocolMapping></span></span>  
<span data-ttu-id="c978e-107">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="c978e-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c978e-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c978e-108">Syntax</span></span>  
  
```xml
   <protocolMapping>    <add binding="String"         bindingConfiguration="String"         scheme="http/net.msmq/net.pipe/net.tcp"/></protocolMapping>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c978e-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c978e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="c978e-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c978e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c978e-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c978e-111">Attributes</span></span>  
  
|<span data-ttu-id="c978e-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="c978e-112">Element</span></span>|<span data-ttu-id="c978e-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c978e-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c978e-114">bağlama</span><span class="sxs-lookup"><span data-stu-id="c978e-114">binding</span></span>|<span data-ttu-id="c978e-115">Varsayılan uç nokta oluşturma sırasında bir uç noktası için kullanılacak bağlama türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="c978e-115">A string that specifies the type of binding to be used for an endpoint during default endpoint creation.</span></span>|  
|<span data-ttu-id="c978e-116">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="c978e-116">bindingConfiguration</span></span>|<span data-ttu-id="c978e-117">Başvurulacak bağlama yapılandırma bölümünün adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="c978e-117">A string that specifies the name of the binding configuration section to be referenced.</span></span>|  
|<span data-ttu-id="c978e-118">düzen</span><span class="sxs-lookup"><span data-stu-id="c978e-118">scheme</span></span>|<span data-ttu-id="c978e-119">Varsayılan uç noktası için kullanılacak Aktarım Protokolü düzeni.</span><span class="sxs-lookup"><span data-stu-id="c978e-119">The transport protocol scheme to be used for the default endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c978e-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c978e-120">Child Elements</span></span>  
 <span data-ttu-id="c978e-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="c978e-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c978e-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c978e-122">Parent Elements</span></span>  
  
|<span data-ttu-id="c978e-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="c978e-123">Element</span></span>|<span data-ttu-id="c978e-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c978e-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c978e-125">\<protocolMapping ></span><span class="sxs-lookup"><span data-stu-id="c978e-125">\<protocolMapping></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/protocolmapping.md)|<span data-ttu-id="c978e-126">Aktarım Protokolü düzenleri (örn., http, net.tcp, net.pipe, vb.) arasındaki varsayılan protokolü eşlemeleri tanımlamak için yapılandırma bölümünü temsil eder ve [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] bağlar.</span><span class="sxs-lookup"><span data-stu-id="c978e-126">Represents a configuration section for defining default protocol mappings between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] bindings.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c978e-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="c978e-127">Example</span></span>  
 <span data-ttu-id="c978e-128">Aşağıdaki yapılandırma örnek machine.config dosyasındaki varsayılan protokolü eşlemeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="c978e-128">The following configuration example shows the default protocol mapping in the machine.config file.</span></span> <span data-ttu-id="c978e-129">Machine.config dosyasının değiştirerek bu varsayılan eşleme makine düzeyinde geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c978e-129">You can override this default mapping at the machine level by modifying the machine.config file.</span></span> <span data-ttu-id="c978e-130">Veya yalnızca bir uygulama kapsamında geçersiz kılmak isterseniz, bu bölümde, uygulama yapılandırma dosyasında geçersiz kılmak ve tek protokol düzenleri için eşleme değiştirin.</span><span class="sxs-lookup"><span data-stu-id="c978e-130">Or if you would only like to override it within the scope of an application, you can override this section within your application configuration file and change the mapping for individual protocol schemes.</span></span>  
  
```xml  
<protocolMapping>  
        <add scheme="http" binding="basicHttpBinding"/>  
        <add scheme="net.tcp" binding="netTcpBinding"/>  
        <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
        <add scheme="net.msmq" binding="netMsmqBinding"/>  
</protocolMapping>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c978e-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c978e-131">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>      
 <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>    
