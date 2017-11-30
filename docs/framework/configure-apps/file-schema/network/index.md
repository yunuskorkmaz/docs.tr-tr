---
title: "Ağ Ayarları Şeması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: ca4a0000d85c8fbac9a723beeda51f9c7886ed8c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="network-settings-schema"></a><span data-ttu-id="8a370-102">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="8a370-102">Network Settings Schema</span></span>
<span data-ttu-id="8a370-103">Ağ ayarları, .NET Framework Internet'e nasıl bağlanacağını belirtin.</span><span class="sxs-lookup"><span data-stu-id="8a370-103">Network settings specify how the .NET Framework connects to the Internet.</span></span> <span data-ttu-id="8a370-104">Aşağıdaki tabloda her bir alt yapılandırma öğesinin altında işlevi açıklanmaktadır [ \<system.Net > öğesi (ağ ayarları)](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md).</span><span class="sxs-lookup"><span data-stu-id="8a370-104">The following table describes the function of each child configuration element under the [\<system.Net> Element (Network Settings)](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md).</span></span>  
  
|<span data-ttu-id="8a370-105">Öğe</span><span class="sxs-lookup"><span data-stu-id="8a370-105">Element</span></span>|<span data-ttu-id="8a370-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8a370-106">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8a370-107">\<authenticationModules > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="8a370-107">\<authenticationModules> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|<span data-ttu-id="8a370-108">Internet istekleri kimliğini doğrulamak için kullanılan modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="8a370-108">Specifies the modules used to authenticate Internet requests.</span></span>|  
|[<span data-ttu-id="8a370-109">\<connectionManagement > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="8a370-109">\<connectionManagement> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|<span data-ttu-id="8a370-110">Internet konaklar bağlantıları en fazla sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="8a370-110">Specifies the maximum number of connections to Internet hosts.</span></span>|  
|[<span data-ttu-id="8a370-111">\<defaultProxy > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="8a370-111">\<defaultProxy> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|<span data-ttu-id="8a370-112">HTTP istekleri Internet için kullanılan proxy sunucusunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="8a370-112">Specifies the proxy server used for HTTP requests to the Internet.</span></span>|  
|[<span data-ttu-id="8a370-113">\<mailSettings > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="8a370-113">\<mailSettings> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/mailsettings-element-network-settings.md)|<span data-ttu-id="8a370-114">Posta seçenekleri gönderme ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="8a370-114">Contains settings for mail sending options.</span></span>|  
|[<span data-ttu-id="8a370-115">\<requestCaching > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="8a370-115">\<requestCaching> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|<span data-ttu-id="8a370-116">Internet ana bilgisayarlardan bilgi istemek için kullanılan modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="8a370-116">Specifies the modules used to request information from Internet hosts.</span></span>|  
|[<span data-ttu-id="8a370-117">\<requestCaching > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="8a370-117">\<requestCaching> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|<span data-ttu-id="8a370-118">Temel ağ seçeneklerini yapılandırır <xref:System.Net?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="8a370-118">Configures basic network options for the <xref:System.Net?displayProperty=nameWithType> namespace.</span></span>|  
|[<span data-ttu-id="8a370-119">\<webRequestModules > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="8a370-119">\<webRequestModules> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|<span data-ttu-id="8a370-120">Internet ana bilgisayarlardan bilgi istemek için kullanılan modülleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="8a370-120">Specifies the modules used to request information from Internet hosts.</span></span>|  
  
 <span data-ttu-id="8a370-121">.NET Framework Tekdüzen Kaynak Tanımlayıcıları (URI'ler) kullanılarak ifade web adresleri nasıl işlediğini URI ayarlarını belirtin.</span><span class="sxs-lookup"><span data-stu-id="8a370-121">Uri settings specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span> <span data-ttu-id="8a370-122">Aşağıdaki tabloda her bir alt yapılandırma öğesinin altında işlevi açıklanmaktadır [ \<URI > öğesi (URI ayarları)](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md).</span><span class="sxs-lookup"><span data-stu-id="8a370-122">The following table describes the function of each child configuration element under the [\<Uri> Element (Uri Settings)](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md).</span></span>  
  
|<span data-ttu-id="8a370-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="8a370-123">Element</span></span>|<span data-ttu-id="8a370-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8a370-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8a370-125">\<IDN > öğesi (URI ayarları)</span><span class="sxs-lookup"><span data-stu-id="8a370-125">\<idn> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/idn-element-uri-settings.md)|<span data-ttu-id="8a370-126">Etki alanı adlarının Uluslararası yapılan etki alanı adı (IDN) ayrıştırma uygulanmış olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="8a370-126">Specifies if Internationalized Domain Name (IDN) parsing is applied to domain names.</span></span>|  
|[<span data-ttu-id="8a370-127">\<iriParsing > öğesi (URI ayarları)</span><span class="sxs-lookup"><span data-stu-id="8a370-127">\<iriParsing> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/iriparsing-element-uri-settings.md)|<span data-ttu-id="8a370-128">Uluslararası kaynak tanımlayıcısı (IRI) ayrıştırma için uygulanmış olup olmadığını belirten bir <xref:System.Uri> ve kuralları ayrıştırma IRI uygulanıp.</span><span class="sxs-lookup"><span data-stu-id="8a370-128">Specifies if International Resource Identifier (IRI) parsing is applied to a <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>|  
|[<span data-ttu-id="8a370-129">\<schemeSettings > öğesi (URI ayarları)</span><span class="sxs-lookup"><span data-stu-id="8a370-129">\<schemeSettings> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|<span data-ttu-id="8a370-130">Belirtir nasıl bir <xref:System.Uri> için belirli düzenleri ayrıştırılır.</span><span class="sxs-lookup"><span data-stu-id="8a370-130">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8a370-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8a370-131">See Also</span></span>  
 [<span data-ttu-id="8a370-132">Internet uygulamaları yapılandırma</span><span class="sxs-lookup"><span data-stu-id="8a370-132">Configuring Internet Applications</span></span>](../../../../../docs/framework/network-programming/configuring-internet-applications.md)  
 [<span data-ttu-id="8a370-133">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="8a370-133">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
