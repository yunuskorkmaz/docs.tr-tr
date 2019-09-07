---
title: <protocolMapping>
ms.date: 03/30/2017
ms.assetid: 5076644b-1f33-4f26-9488-87de9fcda04c
ms.openlocfilehash: be4224ef1a8b17653df8123aaf89e105a496355a
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400017"
---
# <a name="protocolmapping"></a><span data-ttu-id="3a09c-101">\<protocolMapping ></span><span class="sxs-lookup"><span data-stu-id="3a09c-101">\<protocolMapping></span></span>
<span data-ttu-id="3a09c-102">Aktarım Protokolü şemaları (örn. http, net. TCP, net. pipe, vs.) ve WCF bağlamaları arasında bir dizi varsayılan protokol eşlemesini tanımlamaya yönelik bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3a09c-102">Represents a configuration section for defining a set of default protocol mapping between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and WCF bindings.</span></span> <span data-ttu-id="3a09c-103">Çalışma zamanında varsayılan uç noktalar oluştururken, Windows Communication Foundation (WCF) yapılandırılan eşlemelere bakar ve belirli bir tabanlı adres için hangi bağlamanın kullanılacağına karar verir.</span><span class="sxs-lookup"><span data-stu-id="3a09c-103">When creating default endpoints at runtime, Windows Communication Foundation (WCF) looks at the configured mappings and decides on which binding to use for a particular based address.</span></span>  
  
<span data-ttu-id="3a09c-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="3a09c-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="3a09c-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="3a09c-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="3a09c-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<protocolMapping >**</span><span class="sxs-lookup"><span data-stu-id="3a09c-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<protocolMapping>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a09c-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3a09c-107">Syntax</span></span>  
  
```xml  
<protocolMapping>
  <add binding="String"
       bindingConfiguration="String"
       scheme="http/net.msmq/net.pipe/net.tcp" />
</protocolMapping>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3a09c-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3a09c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="3a09c-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3a09c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3a09c-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3a09c-110">Attributes</span></span>  
 <span data-ttu-id="3a09c-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="3a09c-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3a09c-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3a09c-112">Child Elements</span></span>  
  
|<span data-ttu-id="3a09c-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="3a09c-113">Element</span></span>|<span data-ttu-id="3a09c-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3a09c-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3a09c-115">\<Filtreler ></span><span class="sxs-lookup"><span data-stu-id="3a09c-115">\<filters></span></span>](filters-of-routing.md)|<span data-ttu-id="3a09c-116">Bir Aktarım Protokolü düzeni (örneğin, http, net. TCP, net. pipe, vb.) ve bir WCF bağlaması arasında bir varsayılan protokol eşlemesi içerir.</span><span class="sxs-lookup"><span data-stu-id="3a09c-116">Contains a default protocol mapping between a transport protocol scheme (e.g., http, net.tcp, net.pipe, etc.) and a WCF binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3a09c-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3a09c-117">Parent Elements</span></span>  
  
|<span data-ttu-id="3a09c-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="3a09c-118">Element</span></span>|<span data-ttu-id="3a09c-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3a09c-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3a09c-120">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="3a09c-120">\<system.serviceModel></span></span>](system-servicemodel.md)|<span data-ttu-id="3a09c-121">Tüm WCF yapılandırma öğelerinin kök öğesi.</span><span class="sxs-lookup"><span data-stu-id="3a09c-121">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="3a09c-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="3a09c-122">Example</span></span>  
 <span data-ttu-id="3a09c-123">Aşağıdaki yapılandırma örneği, Machine. config dosyasında varsayılan protokol eşlemesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="3a09c-123">The following configuration example shows the default protocol mapping in the machine.config file.</span></span> <span data-ttu-id="3a09c-124">Machine. config dosyasını değiştirerek makine düzeyinde bu varsayılan eşlemeyi geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3a09c-124">You can override this default mapping at the machine level by modifying the machine.config file.</span></span> <span data-ttu-id="3a09c-125">Ya da uygulamayı yalnızca bir uygulamanın kapsamında geçersiz kılmak istiyorsanız, uygulama yapılandırma dosyanızda bu bölümü geçersiz kılabilir ve ayrı protokol şemaları için eşlemeyi değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3a09c-125">Or if you would only like to override it within the scope of an application, you can override this section within your application configuration file and change the mapping for individual protocol schemes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3a09c-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3a09c-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>
