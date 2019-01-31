---
title: < System.Net > öğesi (ağ ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.Net
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.Net
helpviewer_keywords:
- system.Net element
- <system.Net> element
ms.assetid: 52de4d6c-b24d-44aa-ba7d-6b5061f1357e
ms.openlocfilehash: f9fbf48325c7cb5216d16041543bc53c00584ea3
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55257895"
---
# <a name="systemnet-element-network-settings"></a><span data-ttu-id="e7a50-102">\<system.Net > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="e7a50-102">\<system.Net> Element (Network Settings)</span></span>
<span data-ttu-id="e7a50-103">.NET Framework ağa nasıl bağlandığını belirten ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="e7a50-103">Contains settings that specify how the .NET Framework connects to the network.</span></span>  
  
 <span data-ttu-id="e7a50-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="e7a50-104">\<configuration></span></span>  
<span data-ttu-id="e7a50-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="e7a50-105">\<system.net></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7a50-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e7a50-106">Syntax</span></span>  
  
```xml  
<system.net>   
</system.net>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e7a50-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e7a50-107">Attributes and Elements</span></span>  
 <span data-ttu-id="e7a50-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e7a50-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e7a50-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e7a50-109">Attributes</span></span>  
 <span data-ttu-id="e7a50-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="e7a50-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e7a50-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e7a50-111">Child Elements</span></span>  
  
|<span data-ttu-id="e7a50-112">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="e7a50-112">**Element**</span></span>|<span data-ttu-id="e7a50-113">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="e7a50-113">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="e7a50-114">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="e7a50-114">authenticationModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|<span data-ttu-id="e7a50-115">Internet isteklerini kimliğini doğrulamak için kullanılan modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="e7a50-115">Specifies modules used to authenticate Internet requests.</span></span>|  
|[<span data-ttu-id="e7a50-116">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="e7a50-116">connectionManagement</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|<span data-ttu-id="e7a50-117">Bağlantılar Internet barındırmak için en yüksek sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e7a50-117">Specifies the maximum number of connections to an Internet host.</span></span>|  
|[<span data-ttu-id="e7a50-118">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="e7a50-118">defaultProxy</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|<span data-ttu-id="e7a50-119">Köprü Metni Aktarım Protokolü (HTTP) proxy sunucusunu yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="e7a50-119">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
|[<span data-ttu-id="e7a50-120">mailSettings</span><span class="sxs-lookup"><span data-stu-id="e7a50-120">mailSettings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/mailsettings-element-network-settings.md)|<span data-ttu-id="e7a50-121">Basit Posta Aktarım Protokolü (SMTP) posta gönderme seçeneklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="e7a50-121">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
|[<span data-ttu-id="e7a50-122">requestCaching</span><span class="sxs-lookup"><span data-stu-id="e7a50-122">requestCaching</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|<span data-ttu-id="e7a50-123">Ağ istekleri için önbelleğe alma mekanizması denetler.</span><span class="sxs-lookup"><span data-stu-id="e7a50-123">Controls the caching mechanism for network requests.</span></span>|  
|[<span data-ttu-id="e7a50-124">Ayarlar</span><span class="sxs-lookup"><span data-stu-id="e7a50-124">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="e7a50-125">Sınıflar için temel ağ seçeneklerini yapılandırır <xref:System.Net> ve ilgili alt ad alanları.</span><span class="sxs-lookup"><span data-stu-id="e7a50-125">Configures basic network options for classes in the <xref:System.Net> and related child namespaces.</span></span>|  
|[<span data-ttu-id="e7a50-126">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="e7a50-126">webRequestModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|<span data-ttu-id="e7a50-127">Internet konaklarından bilgi istemek için modüller belirtir.</span><span class="sxs-lookup"><span data-stu-id="e7a50-127">Specifies modules to use to request information from Internet hosts.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e7a50-128">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e7a50-128">Parent Elements</span></span>  
  
|<span data-ttu-id="e7a50-129">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="e7a50-129">**Element**</span></span>|<span data-ttu-id="e7a50-130">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="e7a50-130">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="e7a50-131">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e7a50-131">configuration</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="e7a50-132">Tüm ad alanları için ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="e7a50-132">Contains settings for all namespaces.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e7a50-133">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e7a50-133">Remarks</span></span>  
 <span data-ttu-id="e7a50-134">[ \<System.net >](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md) öğe içeren sınıflar için ayarları <xref:System.Net> ve ilgili alt ad alanları.</span><span class="sxs-lookup"><span data-stu-id="e7a50-134">The [\<system.net>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md) element contains settings for classes in the <xref:System.Net> and related child namespaces.</span></span> <span data-ttu-id="e7a50-135">Kimlik doğrulama modülleri, bağlantı yönetimi, posta ayarları, Ara sunucu ve Internet isteği modüller bilgi Internet konakları için ayarları yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="e7a50-135">The settings configure authentication modules, connection management, mail settings, the proxy server, and Internet request modules for receiving information from Internet hosts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7a50-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="e7a50-136">Example</span></span>  
 <span data-ttu-id="e7a50-137">Aşağıdaki örnek tarafından kullanılan tipik yapılandırma gösterilmektedir <xref:System.Net> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="e7a50-137">The following example shows a typical configuration used by <xref:System.Net> classes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e7a50-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e7a50-138">See also</span></span>
- [<span data-ttu-id="e7a50-139">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="e7a50-139">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
