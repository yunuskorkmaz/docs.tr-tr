---
title: '&lt;protocolMapping&gt;'
ms.date: 03/30/2017
ms.assetid: 5076644b-1f33-4f26-9488-87de9fcda04c
ms.openlocfilehash: 199a5d820a80565ccdfa2cb11fe749d63bd65087
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54644266"
---
# <a name="ltprotocolmappinggt"></a><span data-ttu-id="68d3f-102">&lt;protocolMapping&gt;</span><span class="sxs-lookup"><span data-stu-id="68d3f-102">&lt;protocolMapping&gt;</span></span>
<span data-ttu-id="68d3f-103">Taşıma protokol şemaları (örn., http, net.tcp, net.pipe, vb.) ve WCF bağlamaları arasında varsayılan protokol eşleşmelerinin bir kümesini tanımlayan bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="68d3f-103">Represents a configuration section for defining a set of default protocol mapping between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and WCF bindings.</span></span> <span data-ttu-id="68d3f-104">Varsayılan uç noktalar çalışma zamanında oluştururken, Windows Communication Foundation (WCF) yapılandırılmış eşlemelerin arar ve hangi belirli bir için kullanılacak bağlama adresine göre karar verir.</span><span class="sxs-lookup"><span data-stu-id="68d3f-104">When creating default endpoints at runtime, Windows Communication Foundation (WCF) looks at the configured mappings and decides on which binding to use for a particular based address.</span></span>  
  
[<span data-ttu-id="68d3f-105">**\<system.serviceModel>**</span><span class="sxs-lookup"><span data-stu-id="68d3f-105">**\<system.serviceModel>**</span></span>](system-servicemodel.md)  
<span data-ttu-id="68d3f-106">&nbsp;&nbsp;**\<protocolMapping >**</span><span class="sxs-lookup"><span data-stu-id="68d3f-106">&nbsp;&nbsp;**\<protocolMapping>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68d3f-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="68d3f-107">Syntax</span></span>  
  
```xml  
<protocolMapping>
  <add binding="String"
       bindingConfiguration="String"
       scheme="http/net.msmq/net.pipe/net.tcp" />
</protocolMapping>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="68d3f-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="68d3f-108">Attributes and Elements</span></span>  
 <span data-ttu-id="68d3f-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="68d3f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="68d3f-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="68d3f-110">Attributes</span></span>  
 <span data-ttu-id="68d3f-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="68d3f-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="68d3f-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="68d3f-112">Child Elements</span></span>  
  
|<span data-ttu-id="68d3f-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="68d3f-113">Element</span></span>|<span data-ttu-id="68d3f-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="68d3f-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="68d3f-115">\<filtreleri ></span><span class="sxs-lookup"><span data-stu-id="68d3f-115">\<filters></span></span>](filters-of-routing.md)|<span data-ttu-id="68d3f-116">Taşıma protokol şeması (örneğin, http, net.tcp, net.pipe, vb.) ve WCF bağlaması arasında varsayılan protokol eşleşmelerinin içerir.</span><span class="sxs-lookup"><span data-stu-id="68d3f-116">Contains a default protocol mapping between a transport protocol scheme (e.g., http, net.tcp, net.pipe, etc.) and a WCF binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="68d3f-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="68d3f-117">Parent Elements</span></span>  
  
|<span data-ttu-id="68d3f-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="68d3f-118">Element</span></span>|<span data-ttu-id="68d3f-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="68d3f-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="68d3f-120">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="68d3f-120">\<system.serviceModel></span></span>](system-servicemodel.md)|<span data-ttu-id="68d3f-121">Tüm WCF yapılandırma öğelerinin kök öğe.</span><span class="sxs-lookup"><span data-stu-id="68d3f-121">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="68d3f-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="68d3f-122">Example</span></span>  
 <span data-ttu-id="68d3f-123">Aşağıdaki yapılandırma örnek machine.config dosyasında varsayılan protokol eşleşmelerinin gösterir.</span><span class="sxs-lookup"><span data-stu-id="68d3f-123">The following configuration example shows the default protocol mapping in the machine.config file.</span></span> <span data-ttu-id="68d3f-124">Machine.config dosyasının değiştirerek bu varsayılan eşleme makine düzeyinde geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68d3f-124">You can override this default mapping at the machine level by modifying the machine.config file.</span></span> <span data-ttu-id="68d3f-125">Veya yalnızca bir uygulama kapsamında geçersiz kılmak istiyorsanız, bu bölümde, uygulama yapılandırma dosyasında geçersiz kılmak ve eşlemeyi tek protokol şemaları için değiştirin.</span><span class="sxs-lookup"><span data-stu-id="68d3f-125">Or if you would only like to override it within the scope of an application, you can override this section within your application configuration file and change the mapping for individual protocol schemes.</span></span>  
  
```xml  
<protocolMapping>
  <add scheme="http"
       binding="basicHttpBinding" />
  <add scheme="net.tcp"
       binding="netTcpBinding" />
  <add scheme="net.pipe"
       binding="netNamedPipeBinding" />
  <add scheme="net.msmq"
       binding="netMsmqBinding" />
</protocolMapping>
```  
  
## <a name="see-also"></a><span data-ttu-id="68d3f-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="68d3f-126">See also</span></span>
- <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>
