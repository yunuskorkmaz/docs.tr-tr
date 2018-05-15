---
title: '&lt;ProtocolMapping&gt;'
ms.date: 03/30/2017
ms.assetid: 5076644b-1f33-4f26-9488-87de9fcda04c
ms.openlocfilehash: 4afdaaa62c1ac3241eb7382d0995bed51bde73e2
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltprotocolmappinggt"></a><span data-ttu-id="41268-102">&lt;ProtocolMapping&gt;</span><span class="sxs-lookup"><span data-stu-id="41268-102">&lt;protocolMapping&gt;</span></span>
<span data-ttu-id="41268-103">Aktarım Protokolü düzenleri (örn., http, net.tcp, net.pipe, vb.) ve WCF bağlamaları arasında varsayılan protokolü eşleme kümesini tanımlamak için yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="41268-103">Represents a configuration section for defining a set of default protocol mapping between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and WCF bindings.</span></span> <span data-ttu-id="41268-104">Varsayılan uç noktalar çalışma zamanında oluştururken, Windows Communication Foundation (WCF) yapılandırılmış eşlemelerin arar ve adresine göre hangi belirli bir için kullanılacak bağlama karar verir.</span><span class="sxs-lookup"><span data-stu-id="41268-104">When creating default endpoints at runtime, Windows Communication Foundation (WCF) looks at the configured mappings and decides on which binding to use for a particular based address.</span></span>  
  
 <span data-ttu-id="41268-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="41268-105">\<system.serviceModel></span></span>  
<span data-ttu-id="41268-106">\<protocolMapping ></span><span class="sxs-lookup"><span data-stu-id="41268-106">\<protocolMapping></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41268-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="41268-107">Syntax</span></span>  
  
```xml
   <protocolMapping>    <add binding="String"         bindingConfiguration="String"         scheme="http/net.msmq/net.pipe/net.tcp"/></protocolMapping>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="41268-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="41268-108">Attributes and Elements</span></span>  
 <span data-ttu-id="41268-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="41268-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="41268-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="41268-110">Attributes</span></span>  
 <span data-ttu-id="41268-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="41268-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="41268-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="41268-112">Child Elements</span></span>  
  
|<span data-ttu-id="41268-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="41268-113">Element</span></span>|<span data-ttu-id="41268-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="41268-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="41268-115">\<filtreleri ></span><span class="sxs-lookup"><span data-stu-id="41268-115">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="41268-116">Bir Aktarım Protokolü düzeni (örn., http, net.tcp, net.pipe, vb.) ve WCF bağlama varsayılan protokolü eşlemesini içerir.</span><span class="sxs-lookup"><span data-stu-id="41268-116">Contains a default protocol mapping between a transport protocol scheme (e.g., http, net.tcp, net.pipe, etc.) and a WCF binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="41268-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="41268-117">Parent Elements</span></span>  
  
|<span data-ttu-id="41268-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="41268-118">Element</span></span>|<span data-ttu-id="41268-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="41268-119">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="41268-120">Sistem.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="41268-120">system.ServiceModel</span></span>|<span data-ttu-id="41268-121">Tüm WCF yapılandırma öğelerinin kök öğesi.</span><span class="sxs-lookup"><span data-stu-id="41268-121">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="41268-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="41268-122">Example</span></span>  
 <span data-ttu-id="41268-123">Aşağıdaki yapılandırma örnek machine.config dosyasındaki varsayılan protokolü eşlemeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="41268-123">The following configuration example shows the default protocol mapping in the machine.config file.</span></span> <span data-ttu-id="41268-124">Machine.config dosyasının değiştirerek bu varsayılan eşleme makine düzeyinde geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="41268-124">You can override this default mapping at the machine level by modifying the machine.config file.</span></span> <span data-ttu-id="41268-125">Veya yalnızca bir uygulama kapsamında geçersiz kılmak isterseniz, bu bölümde, uygulama yapılandırma dosyasında geçersiz kılmak ve tek protokol düzenleri için eşleme değiştirin.</span><span class="sxs-lookup"><span data-stu-id="41268-125">Or if you would only like to override it within the scope of an application, you can override this section within your application configuration file and change the mapping for individual protocol schemes.</span></span>  
  
```xml  
<protocolMapping>  
        <add scheme="http" binding="basicHttpBinding"/>  
        <add scheme="net.tcp" binding="netTcpBinding"/>  
        <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
        <add scheme="net.msmq" binding="netMsmqBinding"/>  
</protocolMapping>  
```  
  
## <a name="see-also"></a><span data-ttu-id="41268-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="41268-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>    
