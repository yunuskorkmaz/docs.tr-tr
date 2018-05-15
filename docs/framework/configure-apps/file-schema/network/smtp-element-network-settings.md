---
title: '&lt;SMTP&gt; öğesi (ağ ayarları)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp
- http://schemas.microsoft.com/.NetConfiguration/v2.0#smtp
helpviewer_keywords:
- <smtp> element
- smtp element
ms.assetid: 220b0329-e384-4e0c-86b4-0945ad17efd9
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 56912e09d24fc83e93a91cc42b1d96dcc68210f2
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltsmtpgt-element-network-settings"></a><span data-ttu-id="5122a-102">&lt;SMTP&gt; öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="5122a-102">&lt;smtp&gt; Element (Network Settings)</span></span>
<span data-ttu-id="5122a-103">Teslim biçimi, teslim yöntemini yapılandırır ve e-postaları göndermek için adresinden.</span><span class="sxs-lookup"><span data-stu-id="5122a-103">Configures the delivery format, delivery method, and from address for sending emails.</span></span>  
  
 <span data-ttu-id="5122a-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="5122a-104">\<configuration></span></span>  
<span data-ttu-id="5122a-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="5122a-105">\<system.net></span></span>  
<span data-ttu-id="5122a-106">\<mailSettings ></span><span class="sxs-lookup"><span data-stu-id="5122a-106">\<mailSettings></span></span>  
<span data-ttu-id="5122a-107">\<SMTP ></span><span class="sxs-lookup"><span data-stu-id="5122a-107">\<smtp></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5122a-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5122a-108">Syntax</span></span>  
  
```xml  
      <smtp  
        deliveryFormat="format"   
        deliveryMethod="method"   
        from="from address">
          <specifiedPickupDirectory> … </ specifiedPickupDirectory >  
          <network> … </network>  
      </smtp>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5122a-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5122a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="5122a-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5122a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5122a-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5122a-111">Attributes</span></span>  
  
|<span data-ttu-id="5122a-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5122a-112">Attribute</span></span>|<span data-ttu-id="5122a-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5122a-113">Description</span></span>|  
|---------------|-----------------|  
|`deliveryFormat`|<span data-ttu-id="5122a-114">Giden e-postalar için teslim biçimi belirtir.</span><span class="sxs-lookup"><span data-stu-id="5122a-114">Specifies the delivery format for outgoing emails.</span></span> <span data-ttu-id="5122a-115">SevenBit ve uluslararası bunun kabul edilebilir değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="5122a-115">Acceptable values are SevenBit and International.</span></span>|  
|`deliveryMethod`|<span data-ttu-id="5122a-116">E-postalar için teslim yöntemini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5122a-116">Specifies the delivery method for emails.</span></span> <span data-ttu-id="5122a-117">Ağ, pickupDirectoryFromIis ve specifiedPickupDirectory bunun kabul edilebilir değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="5122a-117">Acceptable values are network, pickupDirectoryFromIis, and specifiedPickupDirectory.</span></span>|  
|`from`|<span data-ttu-id="5122a-118">Belirtir giden e-posta adresinden.</span><span class="sxs-lookup"><span data-stu-id="5122a-118">Specifies the from address for outgoing emails.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5122a-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5122a-119">Child Elements</span></span>  
  
|<span data-ttu-id="5122a-120">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5122a-120">Attribute</span></span>|<span data-ttu-id="5122a-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5122a-121">Description</span></span>|  
|---------------|-----------------|  
|`specifiedPickupDirectory`|<span data-ttu-id="5122a-122">Basit Posta Aktarım Protokolü (SMTP) sunucusunun yerel dizin yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="5122a-122">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>|  
|`network`|<span data-ttu-id="5122a-123">Harici bir SMTP sunucusu için ağ seçenekleri yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="5122a-123">Configures the network options for an external SMTP server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5122a-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5122a-124">Parent Elements</span></span>  
  
|<span data-ttu-id="5122a-125">**Öğesi**</span><span class="sxs-lookup"><span data-stu-id="5122a-125">**Element**</span></span>|<span data-ttu-id="5122a-126">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="5122a-126">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="5122a-127">\<mailSettings > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="5122a-127">\<mailSettings> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/mailsettings-element-network-settings.md)|<span data-ttu-id="5122a-128">Posta gönderme seçenekleri yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="5122a-128">Configures mail sending options.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="5122a-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="5122a-129">Example</span></span>  
 <span data-ttu-id="5122a-130">Aşağıdaki örnek, varsayılan ağ kimlik bilgilerini kullanarak e-posta göndermek için uygun SMTP parametreleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="5122a-130">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5122a-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5122a-131">See Also</span></span>  
 <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>  
 <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>  
 <xref:System.Net.Mail.SmtpDeliveryFormat>  
 <xref:System.Net.Mail.SmtpDeliveryMethod>  
 [<span data-ttu-id="5122a-132">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="5122a-132">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
