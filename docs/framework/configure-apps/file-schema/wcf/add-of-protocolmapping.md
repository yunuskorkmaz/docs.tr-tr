---
title: <add> / <protocolMapping>
ms.date: 03/30/2017
ms.assetid: 08e62249-1641-41d1-91b1-66d7b46244e4
ms.openlocfilehash: df69b5f8a79489b722c1074f118b9c6f6e8e363d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926666"
---
# <a name="add-of-protocolmapping"></a><span data-ttu-id="cc726-102">\<\<ProtocolMapping > > ekleyin</span><span class="sxs-lookup"><span data-stu-id="cc726-102">\<add> of \<protocolMapping></span></span>
<span data-ttu-id="cc726-103">Bir Aktarım Protokolü şeması (örn. http, net. TCP, net. pipe, vb.) ve bir Windows Communication Foundation (WCF) bağlaması arasındaki varsayılan protokol eşlemesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="cc726-103">Represents a default protocol mapping between a transport protocol scheme (e.g., http, net.tcp, net.pipe, etc.) and a Windows Communication Foundation (WCF) binding.</span></span> <span data-ttu-id="cc726-104">Çalışma zamanında varsayılan uç noktalar oluştururken, WCF yapılandırılan eşlemelere bakar ve belirli bir tabanlı adres için hangi bağlamanın kullanılacağına karar verir.</span><span class="sxs-lookup"><span data-stu-id="cc726-104">When creating default endpoints at runtime, WCF looks at the configured mappings and decides on which binding to use for a particular based address.</span></span>  
  
 <span data-ttu-id="cc726-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="cc726-105">\<system.serviceModel></span></span>  
<span data-ttu-id="cc726-106">\<protocolMapping ></span><span class="sxs-lookup"><span data-stu-id="cc726-106">\<protocolMapping></span></span>  
<span data-ttu-id="cc726-107">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="cc726-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc726-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cc726-108">Syntax</span></span>  
  
```xml  
<protocolMapping>
  <add binding="String"
       bindingConfiguration="String"
       scheme="http/net.msmq/net.pipe/net.tcp" />
</protocolMapping>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cc726-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="cc726-109">Attributes and Elements</span></span>  
 <span data-ttu-id="cc726-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cc726-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cc726-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="cc726-111">Attributes</span></span>  
  
|<span data-ttu-id="cc726-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="cc726-112">Element</span></span>|<span data-ttu-id="cc726-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cc726-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cc726-114">bağlama</span><span class="sxs-lookup"><span data-stu-id="cc726-114">binding</span></span>|<span data-ttu-id="cc726-115">Varsayılan uç nokta oluşturma sırasında bir uç nokta için kullanılacak bağlama türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="cc726-115">A string that specifies the type of binding to be used for an endpoint during default endpoint creation.</span></span>|  
|<span data-ttu-id="cc726-116">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="cc726-116">bindingConfiguration</span></span>|<span data-ttu-id="cc726-117">Başvurulacak bağlama yapılandırma bölümünün adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="cc726-117">A string that specifies the name of the binding configuration section to be referenced.</span></span>|  
|<span data-ttu-id="cc726-118">düzen</span><span class="sxs-lookup"><span data-stu-id="cc726-118">scheme</span></span>|<span data-ttu-id="cc726-119">Varsayılan uç nokta için kullanılacak Aktarım Protokolü şeması.</span><span class="sxs-lookup"><span data-stu-id="cc726-119">The transport protocol scheme to be used for the default endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cc726-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="cc726-120">Child Elements</span></span>  
 <span data-ttu-id="cc726-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="cc726-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cc726-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="cc726-122">Parent Elements</span></span>  
  
|<span data-ttu-id="cc726-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="cc726-123">Element</span></span>|<span data-ttu-id="cc726-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cc726-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cc726-125">\<protocolMapping ></span><span class="sxs-lookup"><span data-stu-id="cc726-125">\<protocolMapping></span></span>](protocolmapping.md)|<span data-ttu-id="cc726-126">Aktarım Protokolü şemaları (örn. http, net. TCP, net. pipe, vs.) ve Windows Communication Foundation (WCF) bağlamaları arasında varsayılan protokol eşlemelerini tanımlamaya yönelik bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="cc726-126">Represents a configuration section for defining default protocol mappings between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and Windows Communication Foundation (WCF) bindings.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="cc726-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="cc726-127">Example</span></span>  
 <span data-ttu-id="cc726-128">Aşağıdaki yapılandırma örneği, Machine. config dosyasında varsayılan protokol eşlemesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="cc726-128">The following configuration example shows the default protocol mapping in the machine.config file.</span></span> <span data-ttu-id="cc726-129">Machine. config dosyasını değiştirerek makine düzeyinde bu varsayılan eşlemeyi geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cc726-129">You can override this default mapping at the machine level by modifying the machine.config file.</span></span> <span data-ttu-id="cc726-130">Ya da uygulamayı yalnızca bir uygulamanın kapsamında geçersiz kılmak istiyorsanız, uygulama yapılandırma dosyanızda bu bölümü geçersiz kılabilir ve ayrı protokol şemaları için eşlemeyi değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cc726-130">Or if you would only like to override it within the scope of an application, you can override this section within your application configuration file and change the mapping for individual protocol schemes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cc726-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cc726-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>
