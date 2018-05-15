---
title: '&lt;protocolMapping&gt; &lt;ekleme&gt;'
ms.date: 03/30/2017
ms.assetid: 08e62249-1641-41d1-91b1-66d7b46244e4
ms.openlocfilehash: b9559a6921bdededf760f54f58abadb46612b174
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltaddgt-of-ltprotocolmappinggt"></a><span data-ttu-id="36ab8-102">&lt;protocolMapping&gt; &lt;ekleme&gt;</span><span class="sxs-lookup"><span data-stu-id="36ab8-102">&lt;add&gt; of &lt;protocolMapping&gt;</span></span>
<span data-ttu-id="36ab8-103">Bir Aktarım Protokolü düzeni (örn., http, net.tcp, net.pipe, vb.) ve bir Windows Communication Foundation (WCF) bağlama arasındaki varsayılan protokolü eşlemeyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="36ab8-103">Represents a default protocol mapping between a transport protocol scheme (e.g., http, net.tcp, net.pipe, etc.) and a Windows Communication Foundation (WCF) binding.</span></span> <span data-ttu-id="36ab8-104">Varsayılan uç noktalar çalışma zamanında oluştururken [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] yapılandırılmış eşlemelerin arar ve adresine göre hangi belirli bir için kullanılacak bağlama karar verir.</span><span class="sxs-lookup"><span data-stu-id="36ab8-104">When creating default endpoints at runtime, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] looks at the configured mappings and decides on which binding to use for a particular based address.</span></span>  
  
 <span data-ttu-id="36ab8-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="36ab8-105">\<system.serviceModel></span></span>  
<span data-ttu-id="36ab8-106">\<protocolMapping ></span><span class="sxs-lookup"><span data-stu-id="36ab8-106">\<protocolMapping></span></span>  
<span data-ttu-id="36ab8-107">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="36ab8-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36ab8-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="36ab8-108">Syntax</span></span>  
  
```xml
   <protocolMapping>    <add binding="String"         bindingConfiguration="String"         scheme="http/net.msmq/net.pipe/net.tcp"/></protocolMapping>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="36ab8-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="36ab8-109">Attributes and Elements</span></span>  
 <span data-ttu-id="36ab8-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="36ab8-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="36ab8-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="36ab8-111">Attributes</span></span>  
  
|<span data-ttu-id="36ab8-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="36ab8-112">Element</span></span>|<span data-ttu-id="36ab8-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="36ab8-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="36ab8-114">bağlama</span><span class="sxs-lookup"><span data-stu-id="36ab8-114">binding</span></span>|<span data-ttu-id="36ab8-115">Varsayılan uç nokta oluşturma sırasında bir uç noktası için kullanılacak bağlama türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="36ab8-115">A string that specifies the type of binding to be used for an endpoint during default endpoint creation.</span></span>|  
|<span data-ttu-id="36ab8-116">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="36ab8-116">bindingConfiguration</span></span>|<span data-ttu-id="36ab8-117">Başvurulacak bağlama yapılandırma bölümünün adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="36ab8-117">A string that specifies the name of the binding configuration section to be referenced.</span></span>|  
|<span data-ttu-id="36ab8-118">düzen</span><span class="sxs-lookup"><span data-stu-id="36ab8-118">scheme</span></span>|<span data-ttu-id="36ab8-119">Varsayılan uç noktası için kullanılacak Aktarım Protokolü düzeni.</span><span class="sxs-lookup"><span data-stu-id="36ab8-119">The transport protocol scheme to be used for the default endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="36ab8-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="36ab8-120">Child Elements</span></span>  
 <span data-ttu-id="36ab8-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="36ab8-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="36ab8-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="36ab8-122">Parent Elements</span></span>  
  
|<span data-ttu-id="36ab8-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="36ab8-123">Element</span></span>|<span data-ttu-id="36ab8-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="36ab8-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="36ab8-125">\<protocolMapping ></span><span class="sxs-lookup"><span data-stu-id="36ab8-125">\<protocolMapping></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/protocolmapping.md)|<span data-ttu-id="36ab8-126">Aktarım Protokolü düzenleri (örn., http, net.tcp, net.pipe, vb.) ve Windows Communication Foundation (WCF) bağlamaları arasındaki varsayılan protokolü eşlemeleri tanımlamak için yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="36ab8-126">Represents a configuration section for defining default protocol mappings between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and Windows Communication Foundation (WCF) bindings.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="36ab8-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="36ab8-127">Example</span></span>  
 <span data-ttu-id="36ab8-128">Aşağıdaki yapılandırma örnek machine.config dosyasındaki varsayılan protokolü eşlemeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="36ab8-128">The following configuration example shows the default protocol mapping in the machine.config file.</span></span> <span data-ttu-id="36ab8-129">Machine.config dosyasının değiştirerek bu varsayılan eşleme makine düzeyinde geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="36ab8-129">You can override this default mapping at the machine level by modifying the machine.config file.</span></span> <span data-ttu-id="36ab8-130">Veya yalnızca bir uygulama kapsamında geçersiz kılmak isterseniz, bu bölümde, uygulama yapılandırma dosyasında geçersiz kılmak ve tek protokol düzenleri için eşleme değiştirin.</span><span class="sxs-lookup"><span data-stu-id="36ab8-130">Or if you would only like to override it within the scope of an application, you can override this section within your application configuration file and change the mapping for individual protocol schemes.</span></span>  
  
```xml  
<protocolMapping>  
        <add scheme="http" binding="basicHttpBinding"/>  
        <add scheme="net.tcp" binding="netTcpBinding"/>  
        <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
        <add scheme="net.msmq" binding="netMsmqBinding"/>  
</protocolMapping>  
```  
  
## <a name="see-also"></a><span data-ttu-id="36ab8-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="36ab8-131">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>      
 <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>    
