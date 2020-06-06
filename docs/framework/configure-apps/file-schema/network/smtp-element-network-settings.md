---
title: <smtp> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp
- http://schemas.microsoft.com/.NetConfiguration/v2.0#smtp
helpviewer_keywords:
- <smtp> element
- smtp element
ms.assetid: 220b0329-e384-4e0c-86b4-0945ad17efd9
ms.openlocfilehash: 625c3cb82a8659c742b540724e5cf31be65a705e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74089097"
---
# <a name="smtp-element-network-settings"></a><span data-ttu-id="53ed5-102">\<smtp> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="53ed5-102">\<smtp> Element (Network Settings)</span></span>
<span data-ttu-id="53ed5-103">Teslim biçimini, teslim yöntemini ve e-posta gönderme adresini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="53ed5-103">Configures the delivery format, delivery method, and from address for sending emails.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<smtp>**
  
## <a name="syntax"></a><span data-ttu-id="53ed5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="53ed5-104">Syntax</span></span>  
  
```xml  
<smtp  
  deliveryFormat="format"  
  deliveryMethod="method"  
  from="from address">
    <specifiedPickupDirectory>...</specifiedPickupDirectory>  
    <network>...</network>  
</smtp>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="53ed5-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="53ed5-105">Attributes and Elements</span></span>  
 <span data-ttu-id="53ed5-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="53ed5-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="53ed5-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="53ed5-107">Attributes</span></span>  
  
|<span data-ttu-id="53ed5-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="53ed5-108">Attribute</span></span>|<span data-ttu-id="53ed5-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="53ed5-109">Description</span></span>|  
|---------------|-----------------|  
|`deliveryFormat`|<span data-ttu-id="53ed5-110">Giden e-postalar için teslim biçimini belirtir.</span><span class="sxs-lookup"><span data-stu-id="53ed5-110">Specifies the delivery format for outgoing emails.</span></span> <span data-ttu-id="53ed5-111">Kabul edilebilir değerler, yedi bit ve uluslararası.</span><span class="sxs-lookup"><span data-stu-id="53ed5-111">Acceptable values are SevenBit and International.</span></span>|  
|`deliveryMethod`|<span data-ttu-id="53ed5-112">E-postalar için teslim yöntemini belirtir.</span><span class="sxs-lookup"><span data-stu-id="53ed5-112">Specifies the delivery method for emails.</span></span> <span data-ttu-id="53ed5-113">Kabul edilebilir değerler Network, Pickupdirectoryfromısıs ve Belirtilmedipickupdirectory 'Dir.</span><span class="sxs-lookup"><span data-stu-id="53ed5-113">Acceptable values are Network, PickupDirectoryFromIis, and SpecifiedPickupDirectory.</span></span>|  
|`from`|<span data-ttu-id="53ed5-114">Giden e-postalar için kimden adresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="53ed5-114">Specifies the from address for outgoing emails.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="53ed5-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="53ed5-115">Child Elements</span></span>  
  
|<span data-ttu-id="53ed5-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="53ed5-116">Attribute</span></span>|<span data-ttu-id="53ed5-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="53ed5-117">Description</span></span>|  
|---------------|-----------------|  
|`specifiedPickupDirectory`|<span data-ttu-id="53ed5-118">, Bir Basit Posta Aktarım Protokolü (SMTP) sunucusu için yerel dizini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="53ed5-118">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>|  
|`network`|<span data-ttu-id="53ed5-119">Dış SMTP sunucusu için ağ seçeneklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="53ed5-119">Configures the network options for an external SMTP server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="53ed5-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="53ed5-120">Parent Elements</span></span>  
  
|<span data-ttu-id="53ed5-121">**Dosyalarında**</span><span class="sxs-lookup"><span data-stu-id="53ed5-121">**Element**</span></span>|<span data-ttu-id="53ed5-122">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="53ed5-122">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="53ed5-123">\<mailSettings>Öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="53ed5-123">\<mailSettings> Element (Network Settings)</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="53ed5-124">Posta gönderme seçeneklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="53ed5-124">Configures mail sending options.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="53ed5-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="53ed5-125">Example</span></span>  
 <span data-ttu-id="53ed5-126">Aşağıdaki örnek, varsayılan ağ kimlik bilgilerini kullanarak e-posta göndermek için uygun SMTP parametrelerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="53ed5-126">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="53ed5-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="53ed5-127">See also</span></span>

- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpDeliveryFormat>
- <xref:System.Net.Mail.SmtpDeliveryMethod>
- [<span data-ttu-id="53ed5-128">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="53ed5-128">Network Settings Schema</span></span>](index.md)
