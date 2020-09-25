---
title: <smtp> Öğesi (Ağ Ayarları)
description: <smtp>Ağ ayarları öğesi, .NET Framework e-posta seçenekleri göndermek için teslim biçimini, teslim yöntemini ve Kimden adresini yapılandırır.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp
- http://schemas.microsoft.com/.NetConfiguration/v2.0#smtp
helpviewer_keywords:
- <smtp> element
- smtp element
ms.assetid: 220b0329-e384-4e0c-86b4-0945ad17efd9
ms.openlocfilehash: 58f496b4a07f7d5531df897dd54bb6176111f1c4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91178326"
---
# <a name="smtp-element-network-settings"></a><span data-ttu-id="42889-103">\<smtp> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="42889-103">\<smtp> Element (Network Settings)</span></span>

<span data-ttu-id="42889-104">Teslim biçimini, teslim yöntemini ve e-posta gönderme adresini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="42889-104">Configures the delivery format, delivery method, and from address for sending emails.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<smtp>**
  
## <a name="syntax"></a><span data-ttu-id="42889-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="42889-105">Syntax</span></span>  
  
```xml  
<smtp  
  deliveryFormat="format"  
  deliveryMethod="method"  
  from="from address">
    <specifiedPickupDirectory>...</specifiedPickupDirectory>  
    <network>...</network>  
</smtp>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="42889-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="42889-106">Attributes and Elements</span></span>  

 <span data-ttu-id="42889-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="42889-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="42889-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="42889-108">Attributes</span></span>  
  
|<span data-ttu-id="42889-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="42889-109">Attribute</span></span>|<span data-ttu-id="42889-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="42889-110">Description</span></span>|  
|---------------|-----------------|  
|`deliveryFormat`|<span data-ttu-id="42889-111">Giden e-postalar için teslim biçimini belirtir.</span><span class="sxs-lookup"><span data-stu-id="42889-111">Specifies the delivery format for outgoing emails.</span></span> <span data-ttu-id="42889-112">Kabul edilebilir değerler, yedi bit ve uluslararası.</span><span class="sxs-lookup"><span data-stu-id="42889-112">Acceptable values are SevenBit and International.</span></span>|  
|`deliveryMethod`|<span data-ttu-id="42889-113">E-postalar için teslim yöntemini belirtir.</span><span class="sxs-lookup"><span data-stu-id="42889-113">Specifies the delivery method for emails.</span></span> <span data-ttu-id="42889-114">Kabul edilebilir değerler Network, Pickupdirectoryfromısıs ve Belirtilmedipickupdirectory 'Dir.</span><span class="sxs-lookup"><span data-stu-id="42889-114">Acceptable values are Network, PickupDirectoryFromIis, and SpecifiedPickupDirectory.</span></span>|  
|`from`|<span data-ttu-id="42889-115">Giden e-postalar için kimden adresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="42889-115">Specifies the from address for outgoing emails.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="42889-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="42889-116">Child Elements</span></span>  
  
|<span data-ttu-id="42889-117">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="42889-117">Attribute</span></span>|<span data-ttu-id="42889-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="42889-118">Description</span></span>|  
|---------------|-----------------|  
|`specifiedPickupDirectory`|<span data-ttu-id="42889-119">, Bir Basit Posta Aktarım Protokolü (SMTP) sunucusu için yerel dizini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="42889-119">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>|  
|`network`|<span data-ttu-id="42889-120">Dış SMTP sunucusu için ağ seçeneklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="42889-120">Configures the network options for an external SMTP server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="42889-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="42889-121">Parent Elements</span></span>  
  
|<span data-ttu-id="42889-122">**Dosyalarında**</span><span class="sxs-lookup"><span data-stu-id="42889-122">**Element**</span></span>|<span data-ttu-id="42889-123">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="42889-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="42889-124">\<mailSettings> Öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="42889-124">\<mailSettings> Element (Network Settings)</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="42889-125">Posta gönderme seçeneklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="42889-125">Configures mail sending options.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="42889-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="42889-126">Example</span></span>  

 <span data-ttu-id="42889-127">Aşağıdaki örnek, varsayılan ağ kimlik bilgilerini kullanarak e-posta göndermek için uygun SMTP parametrelerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="42889-127">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="42889-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="42889-128">See also</span></span>

- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpDeliveryFormat>
- <xref:System.Net.Mail.SmtpDeliveryMethod>
- [<span data-ttu-id="42889-129">Ağ ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="42889-129">Network Settings Schema</span></span>](index.md)
