---
title: <system.Net> Öğesi (Ağ Ayarları)
description: <system.Net> ağ ayarları öğesi, .NET Framework .NET Framework ağ seçeneklerine nasıl bağlanacağını belirten ayarları içerir.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.Net
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.Net
helpviewer_keywords:
- system.Net element
- <system.Net> element
ms.assetid: 52de4d6c-b24d-44aa-ba7d-6b5061f1357e
ms.openlocfilehash: 9f18c7a3586948c03391d609f437e216a91bc27f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504491"
---
# <a name="systemnet-element-network-settings"></a><span data-ttu-id="4bca3-103">\<system.Net> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="4bca3-103">\<system.Net> Element (Network Settings)</span></span>
<span data-ttu-id="4bca3-104">.NET Framework ağa nasıl bağlanacağını belirten ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="4bca3-104">Contains settings that specify how the .NET Framework connects to the network.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<system.net>**  
  
## <a name="syntax"></a><span data-ttu-id="4bca3-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4bca3-105">Syntax</span></span>  
  
```xml  
<system.net>
</system.net>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4bca3-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4bca3-106">Attributes and Elements</span></span>  
 <span data-ttu-id="4bca3-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4bca3-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4bca3-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4bca3-108">Attributes</span></span>  
 <span data-ttu-id="4bca3-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="4bca3-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4bca3-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4bca3-110">Child Elements</span></span>  
  
|<span data-ttu-id="4bca3-111">**Dosyalarında**</span><span class="sxs-lookup"><span data-stu-id="4bca3-111">**Element**</span></span>|<span data-ttu-id="4bca3-112">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="4bca3-112">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="4bca3-113">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="4bca3-113">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="4bca3-114">Internet isteklerinin kimliğini doğrulamak için kullanılan modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="4bca3-114">Specifies modules used to authenticate Internet requests.</span></span>|  
|[<span data-ttu-id="4bca3-115">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="4bca3-115">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="4bca3-116">Bir Internet ana bilgisayarına en fazla bağlantı sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4bca3-116">Specifies the maximum number of connections to an Internet host.</span></span>|  
|[<span data-ttu-id="4bca3-117">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="4bca3-117">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="4bca3-118">Köprü Metni Aktarım Protokolü (HTTP) proxy sunucusunu yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="4bca3-118">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
|[<span data-ttu-id="4bca3-119">mailSettings</span><span class="sxs-lookup"><span data-stu-id="4bca3-119">mailSettings</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="4bca3-120">Basit Posta Aktarım Protokolü (SMTP) posta gönderme seçeneklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="4bca3-120">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
|[<span data-ttu-id="4bca3-121">requestCaching</span><span class="sxs-lookup"><span data-stu-id="4bca3-121">requestCaching</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="4bca3-122">Ağ istekleri için önbelleğe alma mekanizmasını denetler.</span><span class="sxs-lookup"><span data-stu-id="4bca3-122">Controls the caching mechanism for network requests.</span></span>|  
|[<span data-ttu-id="4bca3-123">ayarlar</span><span class="sxs-lookup"><span data-stu-id="4bca3-123">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="4bca3-124">Ve ilişkili alt ad alanlarındaki sınıflar için temel ağ seçeneklerini yapılandırır <xref:System.Net> .</span><span class="sxs-lookup"><span data-stu-id="4bca3-124">Configures basic network options for classes in the <xref:System.Net> and related child namespaces.</span></span>|  
|[<span data-ttu-id="4bca3-125">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="4bca3-125">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="4bca3-126">Internet konaklarından bilgi istemek için kullanılacak modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="4bca3-126">Specifies modules to use to request information from Internet hosts.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4bca3-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4bca3-127">Parent Elements</span></span>  
  
|<span data-ttu-id="4bca3-128">**Dosyalarında**</span><span class="sxs-lookup"><span data-stu-id="4bca3-128">**Element**</span></span>|<span data-ttu-id="4bca3-129">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="4bca3-129">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="4bca3-130">yapılandırmada</span><span class="sxs-lookup"><span data-stu-id="4bca3-130">configuration</span></span>](../configuration-element.md)|<span data-ttu-id="4bca3-131">Tüm ad alanları için ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="4bca3-131">Contains settings for all namespaces.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4bca3-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4bca3-132">Remarks</span></span>  
 <span data-ttu-id="4bca3-133">[\<system.net>](system-net-element-network-settings.md)Öğesi <xref:System.Net> ve ilgili alt ad alanlarındaki sınıfların ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="4bca3-133">The [\<system.net>](system-net-element-network-settings.md) element contains settings for classes in the <xref:System.Net> and related child namespaces.</span></span> <span data-ttu-id="4bca3-134">Ayarlar, Internet konaklarından bilgi almak için kimlik doğrulama modüllerini, bağlantı yönetimini, posta ayarlarını, proxy sunucusunu ve Internet istek modüllerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="4bca3-134">The settings configure authentication modules, connection management, mail settings, the proxy server, and Internet request modules for receiving information from Internet hosts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4bca3-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="4bca3-135">Example</span></span>  
 <span data-ttu-id="4bca3-136">Aşağıdaki örnekte, sınıfları tarafından kullanılan tipik bir yapılandırma gösterilmektedir <xref:System.Net> .</span><span class="sxs-lookup"><span data-stu-id="4bca3-136">The following example shows a typical configuration used by <xref:System.Net> classes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4bca3-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4bca3-137">See also</span></span>

- [<span data-ttu-id="4bca3-138">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="4bca3-138">Network Settings Schema</span></span>](index.md)
