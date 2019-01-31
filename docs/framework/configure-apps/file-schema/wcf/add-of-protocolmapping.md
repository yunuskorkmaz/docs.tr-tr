---
title: <add> , <protocolMapping>
ms.date: 03/30/2017
ms.assetid: 08e62249-1641-41d1-91b1-66d7b46244e4
ms.openlocfilehash: 18b50ec2d848bc6bb920fb8f630ac7703654b286
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55280741"
---
# <a name="add-of-protocolmapping"></a><span data-ttu-id="4ed5e-102">\<Ekle >, \<protocolMapping ></span><span class="sxs-lookup"><span data-stu-id="4ed5e-102">\<add> of \<protocolMapping></span></span>
<span data-ttu-id="4ed5e-103">Taşıma protokol şeması (örneğin, http, net.tcp, net.pipe, vb.) ve Windows Communication Foundation (WCF) bağlaması arasında varsayılan protokol eşleşmelerinin temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4ed5e-103">Represents a default protocol mapping between a transport protocol scheme (e.g., http, net.tcp, net.pipe, etc.) and a Windows Communication Foundation (WCF) binding.</span></span> <span data-ttu-id="4ed5e-104">Varsayılan uç noktalar çalışma zamanında oluştururken, WCF yapılandırılmış eşlemelerin arar ve hangi belirli bir için kullanılacak bağlama adresine göre karar verir.</span><span class="sxs-lookup"><span data-stu-id="4ed5e-104">When creating default endpoints at runtime, WCF looks at the configured mappings and decides on which binding to use for a particular based address.</span></span>  
  
 <span data-ttu-id="4ed5e-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="4ed5e-105">\<system.serviceModel></span></span>  
<span data-ttu-id="4ed5e-106">\<protocolMapping ></span><span class="sxs-lookup"><span data-stu-id="4ed5e-106">\<protocolMapping></span></span>  
<span data-ttu-id="4ed5e-107">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="4ed5e-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ed5e-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4ed5e-108">Syntax</span></span>  
  
```xml  
<protocolMapping>
  <add binding="String"
       bindingConfiguration="String"
       scheme="http/net.msmq/net.pipe/net.tcp" />
</protocolMapping>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4ed5e-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4ed5e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="4ed5e-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4ed5e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4ed5e-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4ed5e-111">Attributes</span></span>  
  
|<span data-ttu-id="4ed5e-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="4ed5e-112">Element</span></span>|<span data-ttu-id="4ed5e-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4ed5e-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4ed5e-114">bağlama</span><span class="sxs-lookup"><span data-stu-id="4ed5e-114">binding</span></span>|<span data-ttu-id="4ed5e-115">Varsayılan uç nokta oluşturma sırasında bir uç nokta için kullanılacak bağlama türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="4ed5e-115">A string that specifies the type of binding to be used for an endpoint during default endpoint creation.</span></span>|  
|<span data-ttu-id="4ed5e-116">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="4ed5e-116">bindingConfiguration</span></span>|<span data-ttu-id="4ed5e-117">Başvurulacak bağlama yapılandırma bölümünün adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="4ed5e-117">A string that specifies the name of the binding configuration section to be referenced.</span></span>|  
|<span data-ttu-id="4ed5e-118">düzen</span><span class="sxs-lookup"><span data-stu-id="4ed5e-118">scheme</span></span>|<span data-ttu-id="4ed5e-119">Varsayılan uç nokta için kullanılacak taşıma protokol şeması.</span><span class="sxs-lookup"><span data-stu-id="4ed5e-119">The transport protocol scheme to be used for the default endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4ed5e-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4ed5e-120">Child Elements</span></span>  
 <span data-ttu-id="4ed5e-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="4ed5e-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4ed5e-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4ed5e-122">Parent Elements</span></span>  
  
|<span data-ttu-id="4ed5e-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="4ed5e-123">Element</span></span>|<span data-ttu-id="4ed5e-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4ed5e-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4ed5e-125">\<protocolMapping ></span><span class="sxs-lookup"><span data-stu-id="4ed5e-125">\<protocolMapping></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/protocolmapping.md)|<span data-ttu-id="4ed5e-126">Taşıma protokol şemaları (örn., http, net.tcp, net.pipe, vb.) ve Windows Communication Foundation (WCF) bağlamaları arasında varsayılan protokol eşlemeleri tanımlayan bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4ed5e-126">Represents a configuration section for defining default protocol mappings between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and Windows Communication Foundation (WCF) bindings.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="4ed5e-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="4ed5e-127">Example</span></span>  
 <span data-ttu-id="4ed5e-128">Aşağıdaki yapılandırma örnek machine.config dosyasında varsayılan protokol eşleşmelerinin gösterir.</span><span class="sxs-lookup"><span data-stu-id="4ed5e-128">The following configuration example shows the default protocol mapping in the machine.config file.</span></span> <span data-ttu-id="4ed5e-129">Machine.config dosyasının değiştirerek bu varsayılan eşleme makine düzeyinde geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ed5e-129">You can override this default mapping at the machine level by modifying the machine.config file.</span></span> <span data-ttu-id="4ed5e-130">Veya yalnızca bir uygulama kapsamında geçersiz kılmak istiyorsanız, bu bölümde, uygulama yapılandırma dosyasında geçersiz kılmak ve eşlemeyi tek protokol şemaları için değiştirin.</span><span class="sxs-lookup"><span data-stu-id="4ed5e-130">Or if you would only like to override it within the scope of an application, you can override this section within your application configuration file and change the mapping for individual protocol schemes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4ed5e-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4ed5e-131">See also</span></span>
- <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>
