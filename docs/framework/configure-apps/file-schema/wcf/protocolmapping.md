---
title: <protocolMapping>
ms.date: 03/30/2017
ms.assetid: 5076644b-1f33-4f26-9488-87de9fcda04c
ms.openlocfilehash: 0a79aa18c74ddb8ec47f02620d16d391b4a36b68
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91162302"
---
# \<protocolMapping>

<span data-ttu-id="6a336-101">Aktarım Protokolü şemaları (örn. http, net. TCP, net. pipe, vs.) ve WCF bağlamaları arasında bir dizi varsayılan protokol eşlemesini tanımlamaya yönelik bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6a336-101">Represents a configuration section for defining a set of default protocol mapping between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and WCF bindings.</span></span> <span data-ttu-id="6a336-102">Çalışma zamanında varsayılan uç noktalar oluştururken, Windows Communication Foundation (WCF) yapılandırılan eşlemelere bakar ve belirli bir tabanlı adres için hangi bağlamanın kullanılacağına karar verir.</span><span class="sxs-lookup"><span data-stu-id="6a336-102">When creating default endpoints at runtime, Windows Communication Foundation (WCF) looks at the configured mappings and decides on which binding to use for a particular based address.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<protocolMapping>**  
  
## <a name="syntax"></a><span data-ttu-id="6a336-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="6a336-103">Syntax</span></span>  
  
```xml  
<protocolMapping>
  <add binding="String"
       bindingConfiguration="String"
       scheme="http/net.msmq/net.pipe/net.tcp" />
</protocolMapping>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6a336-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6a336-104">Attributes and Elements</span></span>  

 <span data-ttu-id="6a336-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6a336-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6a336-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6a336-106">Attributes</span></span>  

 <span data-ttu-id="6a336-107">Yok.</span><span class="sxs-lookup"><span data-stu-id="6a336-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6a336-108">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6a336-108">Child Elements</span></span>  
  
|<span data-ttu-id="6a336-109">Öğe</span><span class="sxs-lookup"><span data-stu-id="6a336-109">Element</span></span>|<span data-ttu-id="6a336-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6a336-110">Description</span></span>|  
|-------------|-----------------|  
|[\<filters>](filters-of-routing.md)|<span data-ttu-id="6a336-111">Bir Aktarım Protokolü düzeni (örneğin, http, net. TCP, net. pipe, vb.) ve bir WCF bağlaması arasında bir varsayılan protokol eşlemesi içerir.</span><span class="sxs-lookup"><span data-stu-id="6a336-111">Contains a default protocol mapping between a transport protocol scheme (e.g., http, net.tcp, net.pipe, etc.) and a WCF binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6a336-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6a336-112">Parent Elements</span></span>  
  
|<span data-ttu-id="6a336-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="6a336-113">Element</span></span>|<span data-ttu-id="6a336-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6a336-114">Description</span></span>|  
|-------------|-----------------|  
|[\<system.serviceModel>](system-servicemodel.md)|<span data-ttu-id="6a336-115">Tüm WCF yapılandırma öğelerinin kök öğesi.</span><span class="sxs-lookup"><span data-stu-id="6a336-115">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="6a336-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="6a336-116">Example</span></span>  

 <span data-ttu-id="6a336-117">Aşağıdaki yapılandırma örneği machine.config dosyasında varsayılan protokol eşlemesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="6a336-117">The following configuration example shows the default protocol mapping in the machine.config file.</span></span> <span data-ttu-id="6a336-118">machine.config dosyasını değiştirerek makine düzeyinde bu varsayılan eşlemeyi geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6a336-118">You can override this default mapping at the machine level by modifying the machine.config file.</span></span> <span data-ttu-id="6a336-119">Ya da uygulamayı yalnızca bir uygulamanın kapsamında geçersiz kılmak istiyorsanız, uygulama yapılandırma dosyanızda bu bölümü geçersiz kılabilir ve ayrı protokol şemaları için eşlemeyi değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6a336-119">Or if you would only like to override it within the scope of an application, you can override this section within your application configuration file and change the mapping for individual protocol schemes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6a336-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6a336-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>
