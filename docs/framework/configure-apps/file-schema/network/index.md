---
title: Ağ Ayarları Şeması
ms.date: 03/30/2017
helpviewer_keywords:
- elements [.NET Framework], network configuration elements
- sending data, network configuration elements
- receiving data, network configuration elements
- configuration settings [.NET Framework], networks
- Internet, network configuration elements
- network configuration elements
- network settings
- connections [.NET Framework], network configuration elements
- network resources, network configuration elements
ms.assetid: f1de5a0f-76c5-4833-819f-5222b8146340
ms.openlocfilehash: 0f5d762a2b688bebcb7c027be6c639b6d64c069d
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664116"
---
# <a name="network-settings-schema"></a><span data-ttu-id="76e75-102">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="76e75-102">Network Settings Schema</span></span>
<span data-ttu-id="76e75-103">Ağ ayarları .NET Framework Internet 'e nasıl bağlandığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="76e75-103">Network settings specify how the .NET Framework connects to the Internet.</span></span> <span data-ttu-id="76e75-104">Aşağıdaki tabloda, [ \<sistem .net > öğesi (ağ ayarları)](system-net-element-network-settings.md)altındaki her bir alt yapılandırma öğesinin işlevi açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="76e75-104">The following table describes the function of each child configuration element under the [\<system.Net> Element (Network Settings)](system-net-element-network-settings.md).</span></span>  
  
|<span data-ttu-id="76e75-105">Öğe</span><span class="sxs-lookup"><span data-stu-id="76e75-105">Element</span></span>|<span data-ttu-id="76e75-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="76e75-106">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="76e75-107">\<authenticationModules > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="76e75-107">\<authenticationModules> Element (Network Settings)</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="76e75-108">Internet isteklerinin kimliğini doğrulamak için kullanılan modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="76e75-108">Specifies the modules used to authenticate Internet requests.</span></span>|  
|[<span data-ttu-id="76e75-109">\<connectionManagement > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="76e75-109">\<connectionManagement> Element (Network Settings)</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="76e75-110">Internet ana bilgisayarlarına en fazla bağlantı sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="76e75-110">Specifies the maximum number of connections to Internet hosts.</span></span>|  
|[<span data-ttu-id="76e75-111">\<defaultProxy > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="76e75-111">\<defaultProxy> Element (Network Settings)</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="76e75-112">Internet 'e HTTP istekleri için kullanılan proxy sunucusunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="76e75-112">Specifies the proxy server used for HTTP requests to the Internet.</span></span>|  
|[<span data-ttu-id="76e75-113">\<mailSettings > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="76e75-113">\<mailSettings> Element (Network Settings)</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="76e75-114">Posta gönderme seçeneklerinin ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="76e75-114">Contains settings for mail sending options.</span></span>|  
|[<span data-ttu-id="76e75-115">\<requestCaching > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="76e75-115">\<requestCaching> Element (Network Settings)</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="76e75-116">Ağ istekleri için önbelleğe alma mekanizmasını denetler.</span><span class="sxs-lookup"><span data-stu-id="76e75-116">Controls the caching mechanism for network requests.</span></span>|  
|[<span data-ttu-id="76e75-117">\<webRequestModules > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="76e75-117">\<webRequestModules> Element (Network Settings)</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="76e75-118">Internet konaklarından bilgi istemek için kullanılan modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="76e75-118">Specifies the modules used to request information from Internet hosts.</span></span>|  
  
 <span data-ttu-id="76e75-119">URI ayarları .NET Framework, Tekdüzen Kaynak tanımlayıcıları (URI) kullanarak ifade edilen Web adreslerini nasıl işleyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="76e75-119">Uri settings specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span> <span data-ttu-id="76e75-120">Aşağıdaki tabloda, [ \<Uri > öğesi (URI ayarları)](uri-element-uri-settings.md)altındaki her bir alt yapılandırma öğesinin işlevi açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="76e75-120">The following table describes the function of each child configuration element under the [\<Uri> Element (Uri Settings)](uri-element-uri-settings.md).</span></span>  
  
|<span data-ttu-id="76e75-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="76e75-121">Element</span></span>|<span data-ttu-id="76e75-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="76e75-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="76e75-123">\<IDN > öğesi (Uri Ayarları)</span><span class="sxs-lookup"><span data-stu-id="76e75-123">\<idn> Element (Uri Settings)</span></span>](idn-element-uri-settings.md)|<span data-ttu-id="76e75-124">Uluslararası etki alanı adı (ıDN) ayrıştırma 'nın etki alanı adlarına uygulandığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="76e75-124">Specifies if Internationalized Domain Name (IDN) parsing is applied to domain names.</span></span>|  
|[<span data-ttu-id="76e75-125">\<ıriayrıştırma > öğesi (URI ayarları)</span><span class="sxs-lookup"><span data-stu-id="76e75-125">\<iriParsing> Element (Uri Settings)</span></span>](iriparsing-element-uri-settings.md)|<span data-ttu-id="76e75-126">Uluslararası kaynak tanımlayıcı (IRI) ayrıştırma 'nin bir <xref:System.Uri> öğesine uygulanıp uygulanmadığını ve IRI ayrıştırma kurallarının uygulanıp uygulanamayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="76e75-126">Specifies if International Resource Identifier (IRI) parsing is applied to a <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>|  
|[<span data-ttu-id="76e75-127">\<> düzeni öğesi (URI ayarları)</span><span class="sxs-lookup"><span data-stu-id="76e75-127">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="76e75-128">Belirli düzenler için <xref:System.Uri> nasıl ayrıştırılacaksınız belirtir.</span><span class="sxs-lookup"><span data-stu-id="76e75-128">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="76e75-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="76e75-129">See also</span></span>

- [<span data-ttu-id="76e75-130">İnternet Uygulamalarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="76e75-130">Configuring Internet Applications</span></span>](../../../network-programming/configuring-internet-applications.md)
- [<span data-ttu-id="76e75-131">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="76e75-131">Configuration File Schema</span></span>](../index.md)
