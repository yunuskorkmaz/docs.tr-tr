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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154562"
---
# <a name="systemnet-element-network-settings"></a><span data-ttu-id="bda5e-102">\<system.Net> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="bda5e-102">\<system.Net> Element (Network Settings)</span></span>
<span data-ttu-id="bda5e-103">.NET Framework ağa nasıl bağlanacağını belirten ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="bda5e-103">Contains settings that specify how the .NET Framework connects to the network.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<system.net>**  
  
## <a name="syntax"></a><span data-ttu-id="bda5e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bda5e-104">Syntax</span></span>  
  
```xml  
<system.net>
</system.net>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bda5e-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="bda5e-105">Attributes and Elements</span></span>  
 <span data-ttu-id="bda5e-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bda5e-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bda5e-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bda5e-107">Attributes</span></span>  
 <span data-ttu-id="bda5e-108">Yok.</span><span class="sxs-lookup"><span data-stu-id="bda5e-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="bda5e-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="bda5e-109">Child Elements</span></span>  
  
|<span data-ttu-id="bda5e-110">**Dosyalarında**</span><span class="sxs-lookup"><span data-stu-id="bda5e-110">**Element**</span></span>|<span data-ttu-id="bda5e-111">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="bda5e-111">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="bda5e-112">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="bda5e-112">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="bda5e-113">Internet isteklerinin kimliğini doğrulamak için kullanılan modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="bda5e-113">Specifies modules used to authenticate Internet requests.</span></span>|  
|[<span data-ttu-id="bda5e-114">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="bda5e-114">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="bda5e-115">Bir Internet ana bilgisayarına en fazla bağlantı sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="bda5e-115">Specifies the maximum number of connections to an Internet host.</span></span>|  
|[<span data-ttu-id="bda5e-116">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="bda5e-116">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="bda5e-117">Köprü Metni Aktarım Protokolü (HTTP) proxy sunucusunu yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="bda5e-117">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
|[<span data-ttu-id="bda5e-118">mailSettings</span><span class="sxs-lookup"><span data-stu-id="bda5e-118">mailSettings</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="bda5e-119">Basit Posta Aktarım Protokolü (SMTP) posta gönderme seçeneklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="bda5e-119">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
|[<span data-ttu-id="bda5e-120">requestCaching</span><span class="sxs-lookup"><span data-stu-id="bda5e-120">requestCaching</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="bda5e-121">Ağ istekleri için önbelleğe alma mekanizmasını denetler.</span><span class="sxs-lookup"><span data-stu-id="bda5e-121">Controls the caching mechanism for network requests.</span></span>|  
|[<span data-ttu-id="bda5e-122">ayarlar</span><span class="sxs-lookup"><span data-stu-id="bda5e-122">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="bda5e-123">Ve ilişkili alt ad alanlarındaki sınıflar için temel ağ seçeneklerini yapılandırır <xref:System.Net> .</span><span class="sxs-lookup"><span data-stu-id="bda5e-123">Configures basic network options for classes in the <xref:System.Net> and related child namespaces.</span></span>|  
|[<span data-ttu-id="bda5e-124">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="bda5e-124">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="bda5e-125">Internet konaklarından bilgi istemek için kullanılacak modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="bda5e-125">Specifies modules to use to request information from Internet hosts.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bda5e-126">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="bda5e-126">Parent Elements</span></span>  
  
|<span data-ttu-id="bda5e-127">**Dosyalarında**</span><span class="sxs-lookup"><span data-stu-id="bda5e-127">**Element**</span></span>|<span data-ttu-id="bda5e-128">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="bda5e-128">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="bda5e-129">yapılandırmada</span><span class="sxs-lookup"><span data-stu-id="bda5e-129">configuration</span></span>](../configuration-element.md)|<span data-ttu-id="bda5e-130">Tüm ad alanları için ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="bda5e-130">Contains settings for all namespaces.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bda5e-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bda5e-131">Remarks</span></span>  
 <span data-ttu-id="bda5e-132">[\<system.net>](system-net-element-network-settings.md)Öğesi <xref:System.Net> ve ilgili alt ad alanlarındaki sınıfların ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="bda5e-132">The [\<system.net>](system-net-element-network-settings.md) element contains settings for classes in the <xref:System.Net> and related child namespaces.</span></span> <span data-ttu-id="bda5e-133">Ayarlar, Internet konaklarından bilgi almak için kimlik doğrulama modüllerini, bağlantı yönetimini, posta ayarlarını, proxy sunucusunu ve Internet istek modüllerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="bda5e-133">The settings configure authentication modules, connection management, mail settings, the proxy server, and Internet request modules for receiving information from Internet hosts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bda5e-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="bda5e-134">Example</span></span>  
 <span data-ttu-id="bda5e-135">Aşağıdaki örnekte, sınıfları tarafından kullanılan tipik bir yapılandırma gösterilmektedir <xref:System.Net> .</span><span class="sxs-lookup"><span data-stu-id="bda5e-135">The following example shows a typical configuration used by <xref:System.Net> classes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bda5e-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bda5e-136">See also</span></span>

- [<span data-ttu-id="bda5e-137">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="bda5e-137">Network Settings Schema</span></span>](index.md)
