---
title: <add> , <protocolMapping>
ms.date: 03/30/2017
ms.assetid: 08e62249-1641-41d1-91b1-66d7b46244e4
ms.openlocfilehash: 85d09c920de2ca1ab4971551ff98ea58c4492f44
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59109271"
---
# <a name="add-of-protocolmapping"></a><span data-ttu-id="1d676-102">\<Ekle >, \<protocolMapping ></span><span class="sxs-lookup"><span data-stu-id="1d676-102">\<add> of \<protocolMapping></span></span>
<span data-ttu-id="1d676-103">Taşıma protokol şeması (örneğin, http, net.tcp, net.pipe, vb.) ve Windows Communication Foundation (WCF) bağlaması arasında varsayılan protokol eşleşmelerinin temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1d676-103">Represents a default protocol mapping between a transport protocol scheme (e.g., http, net.tcp, net.pipe, etc.) and a Windows Communication Foundation (WCF) binding.</span></span> <span data-ttu-id="1d676-104">Varsayılan uç noktalar çalışma zamanında oluştururken, WCF yapılandırılmış eşlemelerin arar ve hangi belirli bir için kullanılacak bağlama adresine göre karar verir.</span><span class="sxs-lookup"><span data-stu-id="1d676-104">When creating default endpoints at runtime, WCF looks at the configured mappings and decides on which binding to use for a particular based address.</span></span>  
  
 <span data-ttu-id="1d676-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="1d676-105">\<system.serviceModel></span></span>  
<span data-ttu-id="1d676-106">\<protocolMapping ></span><span class="sxs-lookup"><span data-stu-id="1d676-106">\<protocolMapping></span></span>  
<span data-ttu-id="1d676-107">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="1d676-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d676-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1d676-108">Syntax</span></span>  
  
```xml  
<protocolMapping>
  <add binding="String"
       bindingConfiguration="String"
       scheme="http/net.msmq/net.pipe/net.tcp" />
</protocolMapping>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1d676-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1d676-109">Attributes and Elements</span></span>  
 <span data-ttu-id="1d676-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1d676-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1d676-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1d676-111">Attributes</span></span>  
  
|<span data-ttu-id="1d676-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="1d676-112">Element</span></span>|<span data-ttu-id="1d676-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1d676-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1d676-114">bağlama</span><span class="sxs-lookup"><span data-stu-id="1d676-114">binding</span></span>|<span data-ttu-id="1d676-115">Varsayılan uç nokta oluşturma sırasında bir uç nokta için kullanılacak bağlama türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="1d676-115">A string that specifies the type of binding to be used for an endpoint during default endpoint creation.</span></span>|  
|<span data-ttu-id="1d676-116">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="1d676-116">bindingConfiguration</span></span>|<span data-ttu-id="1d676-117">Başvurulacak bağlama yapılandırma bölümünün adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="1d676-117">A string that specifies the name of the binding configuration section to be referenced.</span></span>|  
|<span data-ttu-id="1d676-118">düzen</span><span class="sxs-lookup"><span data-stu-id="1d676-118">scheme</span></span>|<span data-ttu-id="1d676-119">Varsayılan uç nokta için kullanılacak taşıma protokol şeması.</span><span class="sxs-lookup"><span data-stu-id="1d676-119">The transport protocol scheme to be used for the default endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1d676-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1d676-120">Child Elements</span></span>  
 <span data-ttu-id="1d676-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="1d676-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1d676-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1d676-122">Parent Elements</span></span>  
  
|<span data-ttu-id="1d676-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="1d676-123">Element</span></span>|<span data-ttu-id="1d676-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1d676-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1d676-125">\<protocolMapping ></span><span class="sxs-lookup"><span data-stu-id="1d676-125">\<protocolMapping></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/protocolmapping.md)|<span data-ttu-id="1d676-126">Taşıma protokol şemaları (örn., http, net.tcp, net.pipe, vb.) ve Windows Communication Foundation (WCF) bağlamaları arasında varsayılan protokol eşlemeleri tanımlayan bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1d676-126">Represents a configuration section for defining default protocol mappings between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and Windows Communication Foundation (WCF) bindings.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1d676-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="1d676-127">Example</span></span>  
 <span data-ttu-id="1d676-128">Aşağıdaki yapılandırma örnek machine.config dosyasında varsayılan protokol eşleşmelerinin gösterir.</span><span class="sxs-lookup"><span data-stu-id="1d676-128">The following configuration example shows the default protocol mapping in the machine.config file.</span></span> <span data-ttu-id="1d676-129">Machine.config dosyasının değiştirerek bu varsayılan eşleme makine düzeyinde geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1d676-129">You can override this default mapping at the machine level by modifying the machine.config file.</span></span> <span data-ttu-id="1d676-130">Veya yalnızca bir uygulama kapsamında geçersiz kılmak istiyorsanız, bu bölümde, uygulama yapılandırma dosyasında geçersiz kılmak ve eşlemeyi tek protokol şemaları için değiştirin.</span><span class="sxs-lookup"><span data-stu-id="1d676-130">Or if you would only like to override it within the scope of an application, you can override this section within your application configuration file and change the mapping for individual protocol schemes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1d676-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1d676-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>
