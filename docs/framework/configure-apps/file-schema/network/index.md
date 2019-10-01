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
ms.openlocfilehash: 5e3bd1b1734fc7fba50b72785531a8b001d6d741
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698158"
---
# <a name="network-settings-schema"></a><span data-ttu-id="441bc-102">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="441bc-102">Network Settings Schema</span></span>
<span data-ttu-id="441bc-103">Ağ ayarları .NET Framework Internet 'e nasıl bağlandığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="441bc-103">Network settings specify how the .NET Framework connects to the Internet.</span></span>

<span data-ttu-id="441bc-104">@No__t -0system. net > ayarları .NET Framework ağa nasıl bağlanacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="441bc-104">The \<system.net> settings specify how the .NET Framework connects to the network.</span></span> <span data-ttu-id="441bc-105">Aşağıdaki tabloda, [\<Sistem .net > öğesi (ağ ayarları)](system-net-element-network-settings.md)altındaki her bir alt yapılandırma öğesinin işlevi açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="441bc-105">The following table describes the function of each child configuration element under the [\<system.Net> Element (Network Settings)](system-net-element-network-settings.md).</span></span>  
  
|<span data-ttu-id="441bc-106">Öğe</span><span class="sxs-lookup"><span data-stu-id="441bc-106">Element</span></span>|<span data-ttu-id="441bc-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="441bc-107">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="441bc-108">\<authenticationModules > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="441bc-108">\<authenticationModules> Element (Network Settings)</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="441bc-109">Internet isteklerinin kimliğini doğrulamak için kullanılan modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="441bc-109">Specifies the modules used to authenticate Internet requests.</span></span>|  
|[<span data-ttu-id="441bc-110">\<connectionManagement > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="441bc-110">\<connectionManagement> Element (Network Settings)</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="441bc-111">Internet ana bilgisayarlarına en fazla bağlantı sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="441bc-111">Specifies the maximum number of connections to Internet hosts.</span></span>|  
|[<span data-ttu-id="441bc-112">\<defaultProxy > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="441bc-112">\<defaultProxy> Element (Network Settings)</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="441bc-113">Internet 'e HTTP istekleri için kullanılan proxy sunucusunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="441bc-113">Specifies the proxy server used for HTTP requests to the Internet.</span></span>|  
|[<span data-ttu-id="441bc-114">\<mailSettings > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="441bc-114">\<mailSettings> Element (Network Settings)</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="441bc-115">Posta gönderme seçeneklerinin ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="441bc-115">Contains settings for mail sending options.</span></span>|  
|[<span data-ttu-id="441bc-116">\<requestCaching > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="441bc-116">\<requestCaching> Element (Network Settings)</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="441bc-117">Ağ istekleri için önbelleğe alma mekanizmasını denetler.</span><span class="sxs-lookup"><span data-stu-id="441bc-117">Controls the caching mechanism for network requests.</span></span>|  
|[<span data-ttu-id="441bc-118">\<webRequestModules > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="441bc-118">\<webRequestModules> Element (Network Settings)</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="441bc-119">Internet konaklarından bilgi istemek için kullanılan modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="441bc-119">Specifies the modules used to request information from Internet hosts.</span></span>|  
  
<span data-ttu-id="441bc-120">@No__t-0uri > ayarları, .NET Framework Tekdüzen Kaynak tanımlayıcıları (URI) kullanarak ifade edilen Web adreslerini nasıl işleyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="441bc-120">The \<uri> settings specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span> <span data-ttu-id="441bc-121">Aşağıdaki tabloda, [\<urı > öğesi (URI ayarları)](uri-element-uri-settings.md)altındaki her bir alt yapılandırma öğesinin işlevi açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="441bc-121">The following table describes the function of each child configuration element under the [\<uri> Element (Uri Settings)](uri-element-uri-settings.md).</span></span>  
  
|<span data-ttu-id="441bc-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="441bc-122">Element</span></span>|<span data-ttu-id="441bc-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="441bc-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="441bc-124">\<ıdn > öğesi (URI ayarları)</span><span class="sxs-lookup"><span data-stu-id="441bc-124">\<idn> Element (Uri Settings)</span></span>](idn-element-uri-settings.md)|<span data-ttu-id="441bc-125">Uluslararası etki alanı adı (ıDN) ayrıştırma 'nın etki alanı adlarına uygulandığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="441bc-125">Specifies if Internationalized Domain Name (IDN) parsing is applied to domain names.</span></span>|  
|[<span data-ttu-id="441bc-126">\<ıriayrıştırma > öğesi (Uri Ayarları)</span><span class="sxs-lookup"><span data-stu-id="441bc-126">\<iriParsing> Element (Uri Settings)</span></span>](iriparsing-element-uri-settings.md)|<span data-ttu-id="441bc-127">Uluslararası kaynak tanımlayıcı (IRI) ayrıştırma <xref:System.Uri> ' a uygulanıp uygulanmadığını ve IRI ayrıştırma kurallarının uygulanıp uygulanamayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="441bc-127">Specifies if International Resource Identifier (IRI) parsing is applied to a <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>|  
|[<span data-ttu-id="441bc-128">\<Ramesettings > öğesi (Uri Ayarları)</span><span class="sxs-lookup"><span data-stu-id="441bc-128">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="441bc-129">Belirli düzenler için <xref:System.Uri> ' ın nasıl ayrıştıralınacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="441bc-129">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="441bc-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="441bc-130">See also</span></span>

- [<span data-ttu-id="441bc-131">İnternet Uygulamalarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="441bc-131">Configuring Internet Applications</span></span>](../../../network-programming/configuring-internet-applications.md)
- [<span data-ttu-id="441bc-132">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="441bc-132">Configuration File Schema</span></span>](../index.md)
