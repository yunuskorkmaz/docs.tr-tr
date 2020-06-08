---
title: Ağ Ayarları Şeması
description: .NET Framework Internet 'e nasıl bağlandığını ve URI 'Leri nasıl işlediğini belirten ağ ayarlarının şeması hakkında bilgi edinin.
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
ms.openlocfilehash: 6a22d7f1608db2e8909d0ead11e9110ec8a8a2c5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504582"
---
# <a name="network-settings-schema"></a><span data-ttu-id="ef0c3-103">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="ef0c3-103">Network Settings Schema</span></span>
<span data-ttu-id="ef0c3-104">Ağ ayarları .NET Framework Internet 'e nasıl bağlandığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ef0c3-104">Network settings specify how the .NET Framework connects to the Internet.</span></span>

<span data-ttu-id="ef0c3-105">\<system.net>Ayarlar .NET Framework ağa nasıl bağlanacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ef0c3-105">The \<system.net> settings specify how the .NET Framework connects to the network.</span></span> <span data-ttu-id="ef0c3-106">Aşağıdaki tabloda, [ \<system.Net> öğesi (ağ ayarları)](system-net-element-network-settings.md)altındaki her bir alt yapılandırma öğesinin işlevi açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ef0c3-106">The following table describes the function of each child configuration element under the [\<system.Net> Element (Network Settings)](system-net-element-network-settings.md).</span></span>  
  
|<span data-ttu-id="ef0c3-107">Öğe</span><span class="sxs-lookup"><span data-stu-id="ef0c3-107">Element</span></span>|<span data-ttu-id="ef0c3-108">Description</span><span class="sxs-lookup"><span data-stu-id="ef0c3-108">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ef0c3-109">\<authenticationModules>Öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="ef0c3-109">\<authenticationModules> Element (Network Settings)</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="ef0c3-110">Internet isteklerinin kimliğini doğrulamak için kullanılan modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="ef0c3-110">Specifies the modules used to authenticate Internet requests.</span></span>|  
|[<span data-ttu-id="ef0c3-111">\<connectionManagement>Öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="ef0c3-111">\<connectionManagement> Element (Network Settings)</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="ef0c3-112">Internet ana bilgisayarlarına en fazla bağlantı sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ef0c3-112">Specifies the maximum number of connections to Internet hosts.</span></span>|  
|[<span data-ttu-id="ef0c3-113">\<defaultProxy>Öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="ef0c3-113">\<defaultProxy> Element (Network Settings)</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="ef0c3-114">Internet 'e HTTP istekleri için kullanılan proxy sunucusunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="ef0c3-114">Specifies the proxy server used for HTTP requests to the Internet.</span></span>|  
|[<span data-ttu-id="ef0c3-115">\<mailSettings>Öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="ef0c3-115">\<mailSettings> Element (Network Settings)</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="ef0c3-116">Posta gönderme seçeneklerinin ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="ef0c3-116">Contains settings for mail sending options.</span></span>|  
|[<span data-ttu-id="ef0c3-117">\<requestCaching>Öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="ef0c3-117">\<requestCaching> Element (Network Settings)</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="ef0c3-118">Ağ istekleri için önbelleğe alma mekanizmasını denetler.</span><span class="sxs-lookup"><span data-stu-id="ef0c3-118">Controls the caching mechanism for network requests.</span></span>|  
|[<span data-ttu-id="ef0c3-119">\<webRequestModules>Öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="ef0c3-119">\<webRequestModules> Element (Network Settings)</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="ef0c3-120">Internet konaklarından bilgi istemek için kullanılan modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="ef0c3-120">Specifies the modules used to request information from Internet hosts.</span></span>|  
  
<span data-ttu-id="ef0c3-121">\<uri>Ayarlar, .NET Framework Tekdüzen Kaynak tanımlayıcıları (URI) kullanarak ifade edilen Web adreslerini nasıl işleyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ef0c3-121">The \<uri> settings specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span> <span data-ttu-id="ef0c3-122">Aşağıdaki tabloda, öğesi altındaki her bir alt yapılandırma öğesinin işlevi açıklanmaktadır [ \<uri> (URI ayarları)](uri-element-uri-settings.md).</span><span class="sxs-lookup"><span data-stu-id="ef0c3-122">The following table describes the function of each child configuration element under the [\<uri> Element (Uri Settings)](uri-element-uri-settings.md).</span></span>  
  
|<span data-ttu-id="ef0c3-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="ef0c3-123">Element</span></span>|<span data-ttu-id="ef0c3-124">Description</span><span class="sxs-lookup"><span data-stu-id="ef0c3-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ef0c3-125">\<idn>Öğesi (URI ayarları)</span><span class="sxs-lookup"><span data-stu-id="ef0c3-125">\<idn> Element (Uri Settings)</span></span>](idn-element-uri-settings.md)|<span data-ttu-id="ef0c3-126">Uluslararası etki alanı adı (ıDN) ayrıştırma 'nın etki alanı adlarına uygulandığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ef0c3-126">Specifies if Internationalized Domain Name (IDN) parsing is applied to domain names.</span></span>|  
|[<span data-ttu-id="ef0c3-127">\<iriParsing>Öğesi (URI ayarları)</span><span class="sxs-lookup"><span data-stu-id="ef0c3-127">\<iriParsing> Element (Uri Settings)</span></span>](iriparsing-element-uri-settings.md)|<span data-ttu-id="ef0c3-128">Uluslararası kaynak tanımlayıcı (IRI) ayrıştırma 'nin bir öğesine uygulanıp uygulanmadığını <xref:System.Uri> ve IRI ayrıştırma kurallarının uygulanıp uygulanamayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ef0c3-128">Specifies if International Resource Identifier (IRI) parsing is applied to a <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>|  
|[<span data-ttu-id="ef0c3-129">\<schemeSettings>Öğesi (URI ayarları)</span><span class="sxs-lookup"><span data-stu-id="ef0c3-129">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="ef0c3-130"><xref:System.Uri>Belirli düzenler için nasıl ayrıştırılacaksınız belirtir.</span><span class="sxs-lookup"><span data-stu-id="ef0c3-130">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ef0c3-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ef0c3-131">See also</span></span>

- [<span data-ttu-id="ef0c3-132">İnternet Uygulamalarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="ef0c3-132">Configuring Internet Applications</span></span>](../../../network-programming/configuring-internet-applications.md)
- [<span data-ttu-id="ef0c3-133">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="ef0c3-133">Configuration File Schema</span></span>](../index.md)
