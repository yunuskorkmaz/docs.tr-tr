---
title: <protocolMapping>
ms.date: 03/30/2017
ms.assetid: 5076644b-1f33-4f26-9488-87de9fcda04c
ms.openlocfilehash: e26044340bda84fe38b7e286edf833affa94b86c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59118222"
---
# <a name="protocolmapping"></a><span data-ttu-id="5523c-101">\<protocolMapping ></span><span class="sxs-lookup"><span data-stu-id="5523c-101">\<protocolMapping></span></span>
<span data-ttu-id="5523c-102">Taşıma protokol şemaları (örn., http, net.tcp, net.pipe, vb.) ve WCF bağlamaları arasında varsayılan protokol eşleşmelerinin bir kümesini tanımlayan bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5523c-102">Represents a configuration section for defining a set of default protocol mapping between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and WCF bindings.</span></span> <span data-ttu-id="5523c-103">Varsayılan uç noktalar çalışma zamanında oluştururken, Windows Communication Foundation (WCF) yapılandırılmış eşlemelerin arar ve hangi belirli bir için kullanılacak bağlama adresine göre karar verir.</span><span class="sxs-lookup"><span data-stu-id="5523c-103">When creating default endpoints at runtime, Windows Communication Foundation (WCF) looks at the configured mappings and decides on which binding to use for a particular based address.</span></span>  
  
[**<span data-ttu-id="5523c-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="5523c-104">\<system.serviceModel></span></span>**](system-servicemodel.md)  
<span data-ttu-id="5523c-105">&nbsp;&nbsp;**\<protocolMapping >**</span><span class="sxs-lookup"><span data-stu-id="5523c-105">&nbsp;&nbsp;**\<protocolMapping>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5523c-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5523c-106">Syntax</span></span>  
  
```xml  
<protocolMapping>
  <add binding="String"
       bindingConfiguration="String"
       scheme="http/net.msmq/net.pipe/net.tcp" />
</protocolMapping>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5523c-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5523c-107">Attributes and Elements</span></span>  
 <span data-ttu-id="5523c-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5523c-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5523c-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5523c-109">Attributes</span></span>  
 <span data-ttu-id="5523c-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="5523c-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5523c-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5523c-111">Child Elements</span></span>  
  
|<span data-ttu-id="5523c-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="5523c-112">Element</span></span>|<span data-ttu-id="5523c-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5523c-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5523c-114">\<filtreleri ></span><span class="sxs-lookup"><span data-stu-id="5523c-114">\<filters></span></span>](filters-of-routing.md)|<span data-ttu-id="5523c-115">Taşıma protokol şeması (örneğin, http, net.tcp, net.pipe, vb.) ve WCF bağlaması arasında varsayılan protokol eşleşmelerinin içerir.</span><span class="sxs-lookup"><span data-stu-id="5523c-115">Contains a default protocol mapping between a transport protocol scheme (e.g., http, net.tcp, net.pipe, etc.) and a WCF binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5523c-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5523c-116">Parent Elements</span></span>  
  
|<span data-ttu-id="5523c-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="5523c-117">Element</span></span>|<span data-ttu-id="5523c-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5523c-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5523c-119">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="5523c-119">\<system.serviceModel></span></span>](system-servicemodel.md)|<span data-ttu-id="5523c-120">Tüm WCF yapılandırma öğelerinin kök öğe.</span><span class="sxs-lookup"><span data-stu-id="5523c-120">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="5523c-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="5523c-121">Example</span></span>  
 <span data-ttu-id="5523c-122">Aşağıdaki yapılandırma örnek machine.config dosyasında varsayılan protokol eşleşmelerinin gösterir.</span><span class="sxs-lookup"><span data-stu-id="5523c-122">The following configuration example shows the default protocol mapping in the machine.config file.</span></span> <span data-ttu-id="5523c-123">Machine.config dosyasının değiştirerek bu varsayılan eşleme makine düzeyinde geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5523c-123">You can override this default mapping at the machine level by modifying the machine.config file.</span></span> <span data-ttu-id="5523c-124">Veya yalnızca bir uygulama kapsamında geçersiz kılmak istiyorsanız, bu bölümde, uygulama yapılandırma dosyasında geçersiz kılmak ve eşlemeyi tek protokol şemaları için değiştirin.</span><span class="sxs-lookup"><span data-stu-id="5523c-124">Or if you would only like to override it within the scope of an application, you can override this section within your application configuration file and change the mapping for individual protocol schemes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5523c-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5523c-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>
