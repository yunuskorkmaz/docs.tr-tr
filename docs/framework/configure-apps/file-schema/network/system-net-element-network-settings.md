---
title: "&lt;system.Net&gt; öğesi (ağ ayarları)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.Net
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.Net
helpviewer_keywords:
- system.Net element
- <system.Net> element
ms.assetid: 52de4d6c-b24d-44aa-ba7d-6b5061f1357e
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: d2eb903b8a84410aa08504c12e78a016d2368923
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltsystemnetgt-element-network-settings"></a><span data-ttu-id="e39d6-102">&lt;system.Net&gt; öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="e39d6-102">&lt;system.Net&gt; Element (Network Settings)</span></span>
<span data-ttu-id="e39d6-103">.NET Framework ağa nasıl bağlanacağını belirtin ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="e39d6-103">Contains settings that specify how the .NET Framework connects to the network.</span></span>  
  
 <span data-ttu-id="e39d6-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="e39d6-104">\<configuration></span></span>  
<span data-ttu-id="e39d6-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="e39d6-105">\<system.net></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e39d6-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e39d6-106">Syntax</span></span>  
  
```xml  
<system.net>   
</system.net>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e39d6-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e39d6-107">Attributes and Elements</span></span>  
 <span data-ttu-id="e39d6-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e39d6-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e39d6-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e39d6-109">Attributes</span></span>  
 <span data-ttu-id="e39d6-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="e39d6-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e39d6-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e39d6-111">Child Elements</span></span>  
  
|<span data-ttu-id="e39d6-112">**Öğesi**</span><span class="sxs-lookup"><span data-stu-id="e39d6-112">**Element**</span></span>|<span data-ttu-id="e39d6-113">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="e39d6-113">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="e39d6-114">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="e39d6-114">authenticationModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|<span data-ttu-id="e39d6-115">Internet istekleri kimliğini doğrulamak için kullanılan modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="e39d6-115">Specifies modules used to authenticate Internet requests.</span></span>|  
|[<span data-ttu-id="e39d6-116">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="e39d6-116">connectionManagement</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|<span data-ttu-id="e39d6-117">Internet ana bilgisayara bağlantılar en fazla sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e39d6-117">Specifies the maximum number of connections to an Internet host.</span></span>|  
|[<span data-ttu-id="e39d6-118">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="e39d6-118">defaultProxy</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|<span data-ttu-id="e39d6-119">Köprü Metni Aktarım Protokolü (HTTP) proxy sunucusu yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="e39d6-119">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
|[<span data-ttu-id="e39d6-120">mailSettings</span><span class="sxs-lookup"><span data-stu-id="e39d6-120">mailSettings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/mailsettings-element-network-settings.md)|<span data-ttu-id="e39d6-121">Basit Posta Aktarım Protokolü (SMTP) posta gönderme seçenekleri yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="e39d6-121">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
|[<span data-ttu-id="e39d6-122">requestCaching</span><span class="sxs-lookup"><span data-stu-id="e39d6-122">requestCaching</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|<span data-ttu-id="e39d6-123">Ağ isteği önbelleğe alma mekanizması denetler.</span><span class="sxs-lookup"><span data-stu-id="e39d6-123">Controls the caching mechanism for network requests.</span></span>|  
|[<span data-ttu-id="e39d6-124">Ayarlar</span><span class="sxs-lookup"><span data-stu-id="e39d6-124">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="e39d6-125">Sınıflar için temel ağ seçenekleri yapılandırır <xref:System.Net> ve ilgili alt ad alanları.</span><span class="sxs-lookup"><span data-stu-id="e39d6-125">Configures basic network options for classes in the <xref:System.Net> and related child namespaces.</span></span>|  
|[<span data-ttu-id="e39d6-126">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="e39d6-126">webRequestModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|<span data-ttu-id="e39d6-127">Internet ana bilgisayarlardan bilgi istemek için kullanılacak modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="e39d6-127">Specifies modules to use to request information from Internet hosts.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e39d6-128">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e39d6-128">Parent Elements</span></span>  
  
|<span data-ttu-id="e39d6-129">**Öğesi**</span><span class="sxs-lookup"><span data-stu-id="e39d6-129">**Element**</span></span>|<span data-ttu-id="e39d6-130">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="e39d6-130">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="e39d6-131">yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e39d6-131">configuration</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="e39d6-132">Tüm ad alanlarını ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="e39d6-132">Contains settings for all namespaces.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e39d6-133">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e39d6-133">Remarks</span></span>  
 <span data-ttu-id="e39d6-134">[ \<System.net >](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md) öğesi sınıfları için ayarları içeren <xref:System.Net> ve ilgili alt ad alanları.</span><span class="sxs-lookup"><span data-stu-id="e39d6-134">The [\<system.net>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md) element contains settings for classes in the <xref:System.Net> and related child namespaces.</span></span> <span data-ttu-id="e39d6-135">Kimlik doğrulama modülleri, bağlantı yönetimi, posta ayarları, proxy sunucusu ve Internet isteği modülleri Internet ana bilgisayarlardan bilgi almasına için ayarları yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="e39d6-135">The settings configure authentication modules, connection management, mail settings, the proxy server, and Internet request modules for receiving information from Internet hosts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e39d6-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="e39d6-136">Example</span></span>  
 <span data-ttu-id="e39d6-137">Aşağıdaki örnek tarafından kullanılan tipik bir yapılandırmayı gösterir <xref:System.Net> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="e39d6-137">The following example shows a typical configuration used by <xref:System.Net> classes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e39d6-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e39d6-138">See Also</span></span>  
 [<span data-ttu-id="e39d6-139">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="e39d6-139">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
