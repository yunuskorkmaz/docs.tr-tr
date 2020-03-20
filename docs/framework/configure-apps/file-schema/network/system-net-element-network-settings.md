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
ms.openlocfilehash: 88098f2afaad9728e38c4f9935b45f45826a0ca9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154562"
---
# <a name="systemnet-element-network-settings"></a><span data-ttu-id="b45f4-102">\<system.Net> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="b45f4-102">\<system.Net> Element (Network Settings)</span></span>
<span data-ttu-id="b45f4-103">.NET Framework'ün ağa nasıl bağladığını belirten ayarlar içerir.</span><span class="sxs-lookup"><span data-stu-id="b45f4-103">Contains settings that specify how the .NET Framework connects to the network.</span></span>  
  
[<span data-ttu-id="b45f4-104">**\<yapılandırma>**</span><span class="sxs-lookup"><span data-stu-id="b45f4-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="b45f4-105">&nbsp;&nbsp;**\<system.net>**</span><span class="sxs-lookup"><span data-stu-id="b45f4-105">&nbsp;&nbsp;**\<system.net>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b45f4-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b45f4-106">Syntax</span></span>  
  
```xml  
<system.net>
</system.net>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b45f4-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b45f4-107">Attributes and Elements</span></span>  
 <span data-ttu-id="b45f4-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b45f4-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b45f4-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b45f4-109">Attributes</span></span>  
 <span data-ttu-id="b45f4-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="b45f4-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b45f4-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b45f4-111">Child Elements</span></span>  
  
|<span data-ttu-id="b45f4-112">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="b45f4-112">**Element**</span></span>|<span data-ttu-id="b45f4-113">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="b45f4-113">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="b45f4-114">kimlik doğrulamaModülleri</span><span class="sxs-lookup"><span data-stu-id="b45f4-114">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="b45f4-115">Internet isteklerini doğrulamak için kullanılan modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="b45f4-115">Specifies modules used to authenticate Internet requests.</span></span>|  
|[<span data-ttu-id="b45f4-116">bağlantıYönetim</span><span class="sxs-lookup"><span data-stu-id="b45f4-116">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="b45f4-117">Bir Internet ana bilgisayara en fazla bağlantı sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b45f4-117">Specifies the maximum number of connections to an Internet host.</span></span>|  
|[<span data-ttu-id="b45f4-118">Defaultproxy</span><span class="sxs-lookup"><span data-stu-id="b45f4-118">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="b45f4-119">Hypertext Transfer Protocol (HTTP) proxy sunucusunu yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="b45f4-119">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
|[<span data-ttu-id="b45f4-120">mailAyarlar</span><span class="sxs-lookup"><span data-stu-id="b45f4-120">mailSettings</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="b45f4-121">Basit Posta Aktarım Protokolü (SMTP) posta gönderme seçeneklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="b45f4-121">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
|[<span data-ttu-id="b45f4-122">requestCaching</span><span class="sxs-lookup"><span data-stu-id="b45f4-122">requestCaching</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="b45f4-123">Ağ istekleri için önbelleğe alma mekanizmasını denetler.</span><span class="sxs-lookup"><span data-stu-id="b45f4-123">Controls the caching mechanism for network requests.</span></span>|  
|[<span data-ttu-id="b45f4-124">ayarlar</span><span class="sxs-lookup"><span data-stu-id="b45f4-124">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="b45f4-125"><xref:System.Net> Ve ilgili alt ad alanlarındaki sınıflar için temel ağ seçeneklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="b45f4-125">Configures basic network options for classes in the <xref:System.Net> and related child namespaces.</span></span>|  
|[<span data-ttu-id="b45f4-126">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="b45f4-126">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="b45f4-127">Internet ana bilgisayarlarından bilgi istemek için kullanılacak modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="b45f4-127">Specifies modules to use to request information from Internet hosts.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b45f4-128">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b45f4-128">Parent Elements</span></span>  
  
|<span data-ttu-id="b45f4-129">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="b45f4-129">**Element**</span></span>|<span data-ttu-id="b45f4-130">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="b45f4-130">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="b45f4-131">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b45f4-131">configuration</span></span>](../configuration-element.md)|<span data-ttu-id="b45f4-132">Tüm ad alanlarının ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="b45f4-132">Contains settings for all namespaces.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b45f4-133">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b45f4-133">Remarks</span></span>  
 <span data-ttu-id="b45f4-134">[ \<system.net>](system-net-element-network-settings.md) <xref:System.Net> öğesi, ve ilgili alt ad alanlarındaki sınıflar için ayarlar içerir.</span><span class="sxs-lookup"><span data-stu-id="b45f4-134">The [\<system.net>](system-net-element-network-settings.md) element contains settings for classes in the <xref:System.Net> and related child namespaces.</span></span> <span data-ttu-id="b45f4-135">Ayarlar, kimlik doğrulama modüllerini, bağlantı yönetimini, posta ayarlarını, proxy sunucusunu ve Internet istek modüllerini Internet ana bilgisayarlarından bilgi almak için yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="b45f4-135">The settings configure authentication modules, connection management, mail settings, the proxy server, and Internet request modules for receiving information from Internet hosts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b45f4-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="b45f4-136">Example</span></span>  
 <span data-ttu-id="b45f4-137">Aşağıdaki örnek, sınıflar tarafından <xref:System.Net> kullanılan tipik bir yapılandırmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="b45f4-137">The following example shows a typical configuration used by <xref:System.Net> classes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b45f4-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b45f4-138">See also</span></span>

- [<span data-ttu-id="b45f4-139">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="b45f4-139">Network Settings Schema</span></span>](index.md)
