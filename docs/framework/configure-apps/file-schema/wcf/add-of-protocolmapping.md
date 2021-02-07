---
description: 'Hakkında daha fazla bilgi <add> edinin: <protocolMapping>'
title: <add> / <protocolMapping>
ms.date: 03/30/2017
ms.assetid: 08e62249-1641-41d1-91b1-66d7b46244e4
ms.openlocfilehash: 530ef6b2893eb55a979aba2ef7ec21efffc3070a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99750253"
---
# <a name="add-of-protocolmapping"></a><span data-ttu-id="512b2-103">\<add> / \<protocolMapping></span><span class="sxs-lookup"><span data-stu-id="512b2-103">\<add> of \<protocolMapping></span></span>

<span data-ttu-id="512b2-104">Bir Aktarım Protokolü şeması (örn. http, net. TCP, net. pipe, vb.) ve bir Windows Communication Foundation (WCF) bağlaması arasındaki varsayılan protokol eşlemesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="512b2-104">Represents a default protocol mapping between a transport protocol scheme (e.g., http, net.tcp, net.pipe, etc.) and a Windows Communication Foundation (WCF) binding.</span></span> <span data-ttu-id="512b2-105">Çalışma zamanında varsayılan uç noktalar oluştururken, WCF yapılandırılan eşlemelere bakar ve belirli bir tabanlı adres için hangi bağlamanın kullanılacağına karar verir.</span><span class="sxs-lookup"><span data-stu-id="512b2-105">When creating default endpoints at runtime, WCF looks at the configured mappings and decides on which binding to use for a particular based address.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<protocolMapping>**](protocolmapping.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="512b2-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="512b2-106">Syntax</span></span>  
  
```xml  
<protocolMapping>
  <add binding="String"
       bindingConfiguration="String"
       scheme="http/net.msmq/net.pipe/net.tcp" />
</protocolMapping>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="512b2-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="512b2-107">Attributes and Elements</span></span>  

 <span data-ttu-id="512b2-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="512b2-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="512b2-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="512b2-109">Attributes</span></span>  
  
|<span data-ttu-id="512b2-110">Öğe</span><span class="sxs-lookup"><span data-stu-id="512b2-110">Element</span></span>|<span data-ttu-id="512b2-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="512b2-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="512b2-112">bağlama</span><span class="sxs-lookup"><span data-stu-id="512b2-112">binding</span></span>|<span data-ttu-id="512b2-113">Varsayılan uç nokta oluşturma sırasında bir uç nokta için kullanılacak bağlama türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="512b2-113">A string that specifies the type of binding to be used for an endpoint during default endpoint creation.</span></span>|  
|<span data-ttu-id="512b2-114">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="512b2-114">bindingConfiguration</span></span>|<span data-ttu-id="512b2-115">Başvurulacak bağlama yapılandırma bölümünün adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="512b2-115">A string that specifies the name of the binding configuration section to be referenced.</span></span>|  
|<span data-ttu-id="512b2-116">düzen</span><span class="sxs-lookup"><span data-stu-id="512b2-116">scheme</span></span>|<span data-ttu-id="512b2-117">Varsayılan uç nokta için kullanılacak Aktarım Protokolü şeması.</span><span class="sxs-lookup"><span data-stu-id="512b2-117">The transport protocol scheme to be used for the default endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="512b2-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="512b2-118">Child Elements</span></span>  

 <span data-ttu-id="512b2-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="512b2-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="512b2-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="512b2-120">Parent Elements</span></span>  
  
|<span data-ttu-id="512b2-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="512b2-121">Element</span></span>|<span data-ttu-id="512b2-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="512b2-122">Description</span></span>|  
|-------------|-----------------|  
|[\<protocolMapping>](protocolmapping.md)|<span data-ttu-id="512b2-123">Aktarım Protokolü şemaları (örn. http, net. TCP, net. pipe, vs.) ve Windows Communication Foundation (WCF) bağlamaları arasında varsayılan protokol eşlemelerini tanımlamaya yönelik bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="512b2-123">Represents a configuration section for defining default protocol mappings between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and Windows Communication Foundation (WCF) bindings.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="512b2-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="512b2-124">Example</span></span>  

 <span data-ttu-id="512b2-125">Aşağıdaki yapılandırma örneği machine.config dosyasında varsayılan protokol eşlemesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="512b2-125">The following configuration example shows the default protocol mapping in the machine.config file.</span></span> <span data-ttu-id="512b2-126">machine.config dosyasını değiştirerek makine düzeyinde bu varsayılan eşlemeyi geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="512b2-126">You can override this default mapping at the machine level by modifying the machine.config file.</span></span> <span data-ttu-id="512b2-127">Ya da uygulamayı yalnızca bir uygulamanın kapsamında geçersiz kılmak istiyorsanız, uygulama yapılandırma dosyanızda bu bölümü geçersiz kılabilir ve ayrı protokol şemaları için eşlemeyi değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="512b2-127">Or if you would only like to override it within the scope of an application, you can override this section within your application configuration file and change the mapping for individual protocol schemes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="512b2-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="512b2-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>
