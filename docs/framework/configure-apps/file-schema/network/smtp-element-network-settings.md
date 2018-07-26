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
ms.openlocfilehash: 9b6e01906c31316cfa8f148ed96944f309517f95
ms.sourcegitcommit: 59b51cd7c95c75be85bd6ef715e9ef8c85720bac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37874929"
---
# <a name="ltsmtpgt-element-network-settings"></a><span data-ttu-id="3d238-102">&lt;SMTP&gt; öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="3d238-102">&lt;smtp&gt; Element (Network Settings)</span></span>
<span data-ttu-id="3d238-103">Teslim biçimini, teslim yöntemini yapılandırır ve Kimden e-postaları gönderme için adresi.</span><span class="sxs-lookup"><span data-stu-id="3d238-103">Configures the delivery format, delivery method, and from address for sending emails.</span></span>  
  
 <span data-ttu-id="3d238-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="3d238-104">\<configuration></span></span>  
<span data-ttu-id="3d238-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="3d238-105">\<system.net></span></span>  
<span data-ttu-id="3d238-106">\<mailSettings ></span><span class="sxs-lookup"><span data-stu-id="3d238-106">\<mailSettings></span></span>  
<span data-ttu-id="3d238-107">\<SMTP ></span><span class="sxs-lookup"><span data-stu-id="3d238-107">\<smtp></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d238-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3d238-108">Syntax</span></span>  
  
```xml  
      <smtp  
        deliveryFormat="format"   
        deliveryMethod="method"   
        from="from address">
          <specifiedPickupDirectory> … </ specifiedPickupDirectory >  
          <network> … </network>  
      </smtp>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3d238-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3d238-109">Attributes and Elements</span></span>  
 <span data-ttu-id="3d238-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3d238-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3d238-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3d238-111">Attributes</span></span>  
  
|<span data-ttu-id="3d238-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3d238-112">Attribute</span></span>|<span data-ttu-id="3d238-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3d238-113">Description</span></span>|  
|---------------|-----------------|  
|`deliveryFormat`|<span data-ttu-id="3d238-114">Giden e-postalar için teslim etme biçimini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3d238-114">Specifies the delivery format for outgoing emails.</span></span> <span data-ttu-id="3d238-115">Kabul edilebilir değerler şunlardır: SevenBit ve uluslararası ' dir.</span><span class="sxs-lookup"><span data-stu-id="3d238-115">Acceptable values are SevenBit and International.</span></span>|  
|`deliveryMethod`|<span data-ttu-id="3d238-116">E-postalar için teslim etme yöntemini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3d238-116">Specifies the delivery method for emails.</span></span> <span data-ttu-id="3d238-117">Ağ, Pickupdirectoryfromıis ve SpecifiedPickupDirectory bunun kabul edilebilir değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="3d238-117">Acceptable values are Network, PickupDirectoryFromIis, and SpecifiedPickupDirectory.</span></span>|  
|`from`|<span data-ttu-id="3d238-118">Belirtir giden e-postalar için adresinden.</span><span class="sxs-lookup"><span data-stu-id="3d238-118">Specifies the from address for outgoing emails.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3d238-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3d238-119">Child Elements</span></span>  
  
|<span data-ttu-id="3d238-120">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3d238-120">Attribute</span></span>|<span data-ttu-id="3d238-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3d238-121">Description</span></span>|  
|---------------|-----------------|  
|`specifiedPickupDirectory`|<span data-ttu-id="3d238-122">Bir Basit Posta Aktarım Protokolü (SMTP) sunucusu için yerel dizini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="3d238-122">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>|  
|`network`|<span data-ttu-id="3d238-123">Dış SMTP sunucusu ağ seçeneklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="3d238-123">Configures the network options for an external SMTP server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3d238-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3d238-124">Parent Elements</span></span>  
  
|<span data-ttu-id="3d238-125">**Öğesi**</span><span class="sxs-lookup"><span data-stu-id="3d238-125">**Element**</span></span>|<span data-ttu-id="3d238-126">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="3d238-126">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="3d238-127">\<mailSettings > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="3d238-127">\<mailSettings> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/mailsettings-element-network-settings.md)|<span data-ttu-id="3d238-128">Posta gönderme seçeneklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="3d238-128">Configures mail sending options.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="3d238-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="3d238-129">Example</span></span>  
 <span data-ttu-id="3d238-130">Aşağıdaki örnek, varsayılan ağ kimlik bilgilerini kullanarak e-posta göndermek için uygun SMTP parametrelerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3d238-130">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="Network" deliveryFormat="SevenBit"  from="ben@contoso.com">  
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
  
## <a name="see-also"></a><span data-ttu-id="3d238-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3d238-131">See Also</span></span>  
 <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>  
 <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>  
 <xref:System.Net.Mail.SmtpDeliveryFormat>  
 <xref:System.Net.Mail.SmtpDeliveryMethod>  
 [<span data-ttu-id="3d238-132">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="3d238-132">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
