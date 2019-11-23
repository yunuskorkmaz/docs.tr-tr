---
title: <system.Net> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.Net
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.Net
helpviewer_keywords:
- system.Net element
- <system.Net> element
ms.assetid: 52de4d6c-b24d-44aa-ba7d-6b5061f1357e
ms.openlocfilehash: 810e942394c75c192e4423afe4c674ef3a2b9900
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697501"
---
# <a name="systemnet-element-network-settings"></a><span data-ttu-id="39ab7-102">\<sistem .net > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="39ab7-102">\<system.Net> Element (Network Settings)</span></span>
<span data-ttu-id="39ab7-103">.NET Framework ağa nasıl bağlanacağını belirten ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="39ab7-103">Contains settings that specify how the .NET Framework connects to the network.</span></span>  
  
[<span data-ttu-id="39ab7-104"> **\<Yapılandırma >** </span><span class="sxs-lookup"><span data-stu-id="39ab7-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="39ab7-105">**System. net >\<** &nbsp;&nbsp;</span><span class="sxs-lookup"><span data-stu-id="39ab7-105">&nbsp;&nbsp;**\<system.net>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39ab7-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="39ab7-106">Syntax</span></span>  
  
```xml  
<system.net>   
</system.net>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="39ab7-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="39ab7-107">Attributes and Elements</span></span>  
 <span data-ttu-id="39ab7-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="39ab7-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="39ab7-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="39ab7-109">Attributes</span></span>  
 <span data-ttu-id="39ab7-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="39ab7-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="39ab7-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="39ab7-111">Child Elements</span></span>  
  
|<span data-ttu-id="39ab7-112">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="39ab7-112">**Element**</span></span>|<span data-ttu-id="39ab7-113">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="39ab7-113">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="39ab7-114">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="39ab7-114">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="39ab7-115">Internet isteklerinin kimliğini doğrulamak için kullanılan modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="39ab7-115">Specifies modules used to authenticate Internet requests.</span></span>|  
|[<span data-ttu-id="39ab7-116">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="39ab7-116">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="39ab7-117">Bir Internet ana bilgisayarına en fazla bağlantı sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="39ab7-117">Specifies the maximum number of connections to an Internet host.</span></span>|  
|[<span data-ttu-id="39ab7-118">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="39ab7-118">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="39ab7-119">Köprü Metni Aktarım Protokolü (HTTP) proxy sunucusunu yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="39ab7-119">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
|[<span data-ttu-id="39ab7-120">mailSettings</span><span class="sxs-lookup"><span data-stu-id="39ab7-120">mailSettings</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="39ab7-121">Basit Posta Aktarım Protokolü (SMTP) posta gönderme seçeneklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="39ab7-121">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
|[<span data-ttu-id="39ab7-122">requestCaching</span><span class="sxs-lookup"><span data-stu-id="39ab7-122">requestCaching</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="39ab7-123">Ağ istekleri için önbelleğe alma mekanizmasını denetler.</span><span class="sxs-lookup"><span data-stu-id="39ab7-123">Controls the caching mechanism for network requests.</span></span>|  
|[<span data-ttu-id="39ab7-124">Ayarlar</span><span class="sxs-lookup"><span data-stu-id="39ab7-124">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="39ab7-125"><xref:System.Net> ve ilgili alt ad alanlarında sınıflar için temel ağ seçeneklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="39ab7-125">Configures basic network options for classes in the <xref:System.Net> and related child namespaces.</span></span>|  
|[<span data-ttu-id="39ab7-126">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="39ab7-126">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="39ab7-127">Internet konaklarından bilgi istemek için kullanılacak modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="39ab7-127">Specifies modules to use to request information from Internet hosts.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="39ab7-128">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="39ab7-128">Parent Elements</span></span>  
  
|<span data-ttu-id="39ab7-129">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="39ab7-129">**Element**</span></span>|<span data-ttu-id="39ab7-130">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="39ab7-130">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="39ab7-131">yapılandırmada</span><span class="sxs-lookup"><span data-stu-id="39ab7-131">configuration</span></span>](../configuration-element.md)|<span data-ttu-id="39ab7-132">Tüm ad alanları için ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="39ab7-132">Contains settings for all namespaces.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="39ab7-133">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="39ab7-133">Remarks</span></span>  
 <span data-ttu-id="39ab7-134">[\<System. net >](system-net-element-network-settings.md) öğesi, <xref:System.Net> ve ilgili alt ad alanlarındaki sınıfların ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="39ab7-134">The [\<system.net>](system-net-element-network-settings.md) element contains settings for classes in the <xref:System.Net> and related child namespaces.</span></span> <span data-ttu-id="39ab7-135">Ayarlar, Internet konaklarından bilgi almak için kimlik doğrulama modüllerini, bağlantı yönetimini, posta ayarlarını, proxy sunucusunu ve Internet istek modüllerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="39ab7-135">The settings configure authentication modules, connection management, mail settings, the proxy server, and Internet request modules for receiving information from Internet hosts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="39ab7-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="39ab7-136">Example</span></span>  
 <span data-ttu-id="39ab7-137">Aşağıdaki örnekte <xref:System.Net> sınıfları tarafından kullanılan tipik bir yapılandırma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="39ab7-137">The following example shows a typical configuration used by <xref:System.Net> classes.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <add type="System.Net.DigestClient" />  
      <add type="System.Net.NegotiateClient" />  
      <add type="System.Net.KerberosClient" />  
      <add type="System.Net.NtlmClient" />  
      <add type="System.Net.BasicClient" />  
    </authenticationModules>  
    <connectionManagement>  
      <add address="*" maxconnection="2" />  
    </connectionManagement>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="true"  
        bypassonlocal="true"  
      />  
    </defaultProxy>  
    <webRequestModules>  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator"  
      />  
      <add prefix="https"  
           type="System.Net.HttpRequestCreator"  
      />  
      <add prefix="file"  
           type="System.Net.FileWebRequestCreator"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="39ab7-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="39ab7-138">See also</span></span>

- [<span data-ttu-id="39ab7-139">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="39ab7-139">Network Settings Schema</span></span>](index.md)
