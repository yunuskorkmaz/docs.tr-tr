---
description: 'Hakkında daha fazla bilgi edinin: <protocolMapping>'
title: <protocolMapping>
ms.date: 03/30/2017
ms.assetid: 5076644b-1f33-4f26-9488-87de9fcda04c
ms.openlocfilehash: defdf3129122212dac9481dc5d8d48a0dfa94d72
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786921"
---
# \<protocolMapping>

<span data-ttu-id="06358-102">Aktarım Protokolü şemaları (örn. http, net. TCP, net. pipe, vs.) ve WCF bağlamaları arasında bir dizi varsayılan protokol eşlemesini tanımlamaya yönelik bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="06358-102">Represents a configuration section for defining a set of default protocol mapping between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and WCF bindings.</span></span> <span data-ttu-id="06358-103">Çalışma zamanında varsayılan uç noktalar oluştururken, Windows Communication Foundation (WCF) yapılandırılan eşlemelere bakar ve belirli bir tabanlı adres için hangi bağlamanın kullanılacağına karar verir.</span><span class="sxs-lookup"><span data-stu-id="06358-103">When creating default endpoints at runtime, Windows Communication Foundation (WCF) looks at the configured mappings and decides on which binding to use for a particular based address.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<protocolMapping>**  
  
## <a name="syntax"></a><span data-ttu-id="06358-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="06358-104">Syntax</span></span>  
  
```xml  
<protocolMapping>
  <add binding="String"
       bindingConfiguration="String"
       scheme="http/net.msmq/net.pipe/net.tcp" />
</protocolMapping>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="06358-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="06358-105">Attributes and Elements</span></span>  

 <span data-ttu-id="06358-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="06358-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="06358-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="06358-107">Attributes</span></span>  

 <span data-ttu-id="06358-108">Yok.</span><span class="sxs-lookup"><span data-stu-id="06358-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="06358-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="06358-109">Child Elements</span></span>  
  
|<span data-ttu-id="06358-110">Öğe</span><span class="sxs-lookup"><span data-stu-id="06358-110">Element</span></span>|<span data-ttu-id="06358-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="06358-111">Description</span></span>|  
|-------------|-----------------|  
|[\<filters>](filters-of-routing.md)|<span data-ttu-id="06358-112">Bir Aktarım Protokolü düzeni (örneğin, http, net. TCP, net. pipe, vb.) ve bir WCF bağlaması arasında bir varsayılan protokol eşlemesi içerir.</span><span class="sxs-lookup"><span data-stu-id="06358-112">Contains a default protocol mapping between a transport protocol scheme (e.g., http, net.tcp, net.pipe, etc.) and a WCF binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="06358-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="06358-113">Parent Elements</span></span>  
  
|<span data-ttu-id="06358-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="06358-114">Element</span></span>|<span data-ttu-id="06358-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="06358-115">Description</span></span>|  
|-------------|-----------------|  
|[\<system.serviceModel>](system-servicemodel.md)|<span data-ttu-id="06358-116">Tüm WCF yapılandırma öğelerinin kök öğesi.</span><span class="sxs-lookup"><span data-stu-id="06358-116">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="06358-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="06358-117">Example</span></span>  

 <span data-ttu-id="06358-118">Aşağıdaki yapılandırma örneği machine.config dosyasında varsayılan protokol eşlemesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="06358-118">The following configuration example shows the default protocol mapping in the machine.config file.</span></span> <span data-ttu-id="06358-119">machine.config dosyasını değiştirerek makine düzeyinde bu varsayılan eşlemeyi geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="06358-119">You can override this default mapping at the machine level by modifying the machine.config file.</span></span> <span data-ttu-id="06358-120">Ya da uygulamayı yalnızca bir uygulamanın kapsamında geçersiz kılmak istiyorsanız, uygulama yapılandırma dosyanızda bu bölümü geçersiz kılabilir ve ayrı protokol şemaları için eşlemeyi değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="06358-120">Or if you would only like to override it within the scope of an application, you can override this section within your application configuration file and change the mapping for individual protocol schemes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="06358-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="06358-121">See also</span></span>

- <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>
