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
ms.openlocfilehash: ac9405fdc6123a5a1352de06f94fefb6d7d4014b
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659115"
---
# <a name="smtp-element-network-settings"></a><span data-ttu-id="f1e23-102">\<SMTP > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="f1e23-102">\<smtp> Element (Network Settings)</span></span>
<span data-ttu-id="f1e23-103">Teslim biçimini, teslim yöntemini ve e-posta gönderme adresini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="f1e23-103">Configures the delivery format, delivery method, and from address for sending emails.</span></span>  
  
 <span data-ttu-id="f1e23-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="f1e23-104">\<configuration></span></span>  
<span data-ttu-id="f1e23-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="f1e23-105">\<system.net></span></span>  
<span data-ttu-id="f1e23-106">\<mailSettings ></span><span class="sxs-lookup"><span data-stu-id="f1e23-106">\<mailSettings></span></span>  
<span data-ttu-id="f1e23-107">\<SMTP ></span><span class="sxs-lookup"><span data-stu-id="f1e23-107">\<smtp></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1e23-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f1e23-108">Syntax</span></span>  
  
```xml  
<smtp  
  deliveryFormat="format"  
  deliveryMethod="method"  
  from="from address">
    <specifiedPickupDirectory>...</specifiedPickupDirectory>  
    <network>...</network>  
</smtp>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f1e23-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f1e23-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f1e23-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f1e23-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f1e23-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f1e23-111">Attributes</span></span>  
  
|<span data-ttu-id="f1e23-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f1e23-112">Attribute</span></span>|<span data-ttu-id="f1e23-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f1e23-113">Description</span></span>|  
|---------------|-----------------|  
|`deliveryFormat`|<span data-ttu-id="f1e23-114">Giden e-postalar için teslim biçimini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f1e23-114">Specifies the delivery format for outgoing emails.</span></span> <span data-ttu-id="f1e23-115">Kabul edilebilir değerler, yedi bit ve uluslararası.</span><span class="sxs-lookup"><span data-stu-id="f1e23-115">Acceptable values are SevenBit and International.</span></span>|  
|`deliveryMethod`|<span data-ttu-id="f1e23-116">E-postalar için teslim yöntemini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f1e23-116">Specifies the delivery method for emails.</span></span> <span data-ttu-id="f1e23-117">Kabul edilebilir değerler Network, Pickupdirectoryfromısıs ve Belirtilmedipickupdirectory 'Dir.</span><span class="sxs-lookup"><span data-stu-id="f1e23-117">Acceptable values are Network, PickupDirectoryFromIis, and SpecifiedPickupDirectory.</span></span>|  
|`from`|<span data-ttu-id="f1e23-118">Giden e-postalar için kimden adresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f1e23-118">Specifies the from address for outgoing emails.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f1e23-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f1e23-119">Child Elements</span></span>  
  
|<span data-ttu-id="f1e23-120">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f1e23-120">Attribute</span></span>|<span data-ttu-id="f1e23-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f1e23-121">Description</span></span>|  
|---------------|-----------------|  
|`specifiedPickupDirectory`|<span data-ttu-id="f1e23-122">, Bir Basit Posta Aktarım Protokolü (SMTP) sunucusu için yerel dizini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="f1e23-122">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>|  
|`network`|<span data-ttu-id="f1e23-123">Dış SMTP sunucusu için ağ seçeneklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="f1e23-123">Configures the network options for an external SMTP server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f1e23-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f1e23-124">Parent Elements</span></span>  
  
|<span data-ttu-id="f1e23-125">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="f1e23-125">**Element**</span></span>|<span data-ttu-id="f1e23-126">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="f1e23-126">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="f1e23-127">\<mailSettings > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="f1e23-127">\<mailSettings> Element (Network Settings)</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="f1e23-128">Posta gönderme seçeneklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="f1e23-128">Configures mail sending options.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f1e23-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="f1e23-129">Example</span></span>  
 <span data-ttu-id="f1e23-130">Aşağıdaki örnek, varsayılan ağ kimlik bilgilerini kullanarak e-posta göndermek için uygun SMTP parametrelerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f1e23-130">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f1e23-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f1e23-131">See also</span></span>

- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpDeliveryFormat>
- <xref:System.Net.Mail.SmtpDeliveryMethod>
- [<span data-ttu-id="f1e23-132">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="f1e23-132">Network Settings Schema</span></span>](index.md)
