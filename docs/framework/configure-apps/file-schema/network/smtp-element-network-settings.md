---
title: "&lt;SMTP&gt; öğesi (ağ ayarları)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp
- http://schemas.microsoft.com/.NetConfiguration/v2.0#smtp
helpviewer_keywords:
- <smtp> element
- smtp element
ms.assetid: 220b0329-e384-4e0c-86b4-0945ad17efd9
caps.latest.revision: "13"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 17b4050c43354da7e7ba6c3ea13a0c7621faf0a0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltsmtpgt-element-network-settings"></a><span data-ttu-id="8dbda-102">&lt;SMTP&gt; öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="8dbda-102">&lt;smtp&gt; Element (Network Settings)</span></span>
<span data-ttu-id="8dbda-103">Teslim biçimi, teslim yöntemini yapılandırır ve e-postalar göndermek için adresinden.</span><span class="sxs-lookup"><span data-stu-id="8dbda-103">Configures the delivery format, delivery method, and from address for sending e-mails.</span></span>  
  
 <span data-ttu-id="8dbda-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="8dbda-104">\<configuration></span></span>  
<span data-ttu-id="8dbda-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="8dbda-105">\<system.net></span></span>  
<span data-ttu-id="8dbda-106">\<mailSettings ></span><span class="sxs-lookup"><span data-stu-id="8dbda-106">\<mailSettings></span></span>  
<span data-ttu-id="8dbda-107">\<SMTP ></span><span class="sxs-lookup"><span data-stu-id="8dbda-107">\<smtp></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8dbda-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8dbda-108">Syntax</span></span>  
  
```xml  
      <smtp  
        deliveryFormat="format"   
        deliveryMethod="method"   
        from="from address">
          <specifiedPickupDirectory> … </ specifiedPickupDirectory >  
          <network> … </network>  
      </smtp>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8dbda-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8dbda-109">Attributes and Elements</span></span>  
 <span data-ttu-id="8dbda-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8dbda-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8dbda-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8dbda-111">Attributes</span></span>  
  
|<span data-ttu-id="8dbda-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="8dbda-112">Attribute</span></span>|<span data-ttu-id="8dbda-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8dbda-113">Description</span></span>|  
|---------------|-----------------|  
|`deliveryFormat`|<span data-ttu-id="8dbda-114">Giden e-postalar için teslim biçimi belirtir.</span><span class="sxs-lookup"><span data-stu-id="8dbda-114">Specifies the delivery format for outgoing e-mails.</span></span> <span data-ttu-id="8dbda-115">SevenBit ve uluslararası bunun kabul edilebilir değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="8dbda-115">Acceptable values are SevenBit and International.</span></span>|  
|`deliveryMethod`|<span data-ttu-id="8dbda-116">E-postalar için teslim yöntemini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8dbda-116">Specifies the delivery method for e-mails.</span></span> <span data-ttu-id="8dbda-117">Ağ, pickupDirectoryFromIis ve specifiedPickupDirectory bunun kabul edilebilir değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="8dbda-117">Acceptable values are network, pickupDirectoryFromIis, and specifiedPickupDirectory.</span></span>|  
|`from`|<span data-ttu-id="8dbda-118">Belirtir giden e-postalar için adresinden.</span><span class="sxs-lookup"><span data-stu-id="8dbda-118">Specifies the from address for outgoing e-mails.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8dbda-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8dbda-119">Child Elements</span></span>  
  
|<span data-ttu-id="8dbda-120">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="8dbda-120">Attribute</span></span>|<span data-ttu-id="8dbda-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8dbda-121">Description</span></span>|  
|---------------|-----------------|  
|`specifiedPickupDirectory`|<span data-ttu-id="8dbda-122">Basit Posta Aktarım Protokolü (SMTP) sunucusunun yerel dizin yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="8dbda-122">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>|  
|`network`|<span data-ttu-id="8dbda-123">Harici bir SMTP sunucusu için ağ seçenekleri yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="8dbda-123">Configures the network options for an external SMTP server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8dbda-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8dbda-124">Parent Elements</span></span>  
  
|<span data-ttu-id="8dbda-125">**Öğesi**</span><span class="sxs-lookup"><span data-stu-id="8dbda-125">**Element**</span></span>|<span data-ttu-id="8dbda-126">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="8dbda-126">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="8dbda-127">\<mailSettings > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="8dbda-127">\<mailSettings> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/mailsettings-element-network-settings.md)|<span data-ttu-id="8dbda-128">Posta gönderme seçenekleri yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="8dbda-128">Configures mail sending options.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="8dbda-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="8dbda-129">Example</span></span>  
 <span data-ttu-id="8dbda-130">Aşağıdaki örnek, varsayılan ağ kimlik bilgilerini kullanarak e-posta göndermek için uygun SMTP parametreleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="8dbda-130">The following example specifies the appropriate SMTP parameters to send e-mail using the default network credentials.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="network" deliveryFormat="SevenBit"  from="ben@contoso.com">  
        <network  
          host="localhost"  
          port="25"  
          defaultCredentials="true"  
        />  
      </smtp>  
    </mailSettings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8dbda-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8dbda-131">See Also</span></span>  
 <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>  
 <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>  
 <xref:System.Net.Mail.SmtpDeliveryFormat>  
 <xref:System.Net.Mail.SmtpDeliveryMethod>  
 [<span data-ttu-id="8dbda-132">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="8dbda-132">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
