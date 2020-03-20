---
title: <specifiedPickupDirectory> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#specifiedPickupDirectory
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/specifiedPickupDirectory
helpviewer_keywords:
- specifiedPickupDirectory element
- <specifiedPickupDirectory> element
ms.assetid: 0121f49d-bff2-4bc6-af06-f1628dcd61f1
ms.openlocfilehash: 4b0cbaf9a7bfe2a9b1610811f4201253d219a6b2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154614"
---
# <a name="specifiedpickupdirectory-element-network-settings"></a><span data-ttu-id="2c65b-102">\<belirtilenPickupDirectory> Elemanı (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="2c65b-102">\<specifiedPickupDirectory> Element (Network Settings)</span></span>
<span data-ttu-id="2c65b-103">Basit Posta Aktarım Protokolü (SMTP) sunucusunun yerel dizinini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="2c65b-103">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>  
  
<span data-ttu-id="2c65b-104">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="2c65b-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2c65b-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="2c65b-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="2c65b-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailAyarlar>**](mailsettings-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="2c65b-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)</span></span>\
<span data-ttu-id="2c65b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<smtp>**](smtp-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="2c65b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<smtp>**](smtp-element-network-settings.md)</span></span>\
<span data-ttu-id="2c65b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<belirtilenPickupDirectory>**</span><span class="sxs-lookup"><span data-stu-id="2c65b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<specifiedPickupDirectory>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c65b-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2c65b-109">Syntax</span></span>  
  
```xml  
<specifiedPickupDirectory  
  pickupDirectoryLocation="directory"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2c65b-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2c65b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="2c65b-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2c65b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2c65b-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2c65b-112">Attributes</span></span>  
  
|<span data-ttu-id="2c65b-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="2c65b-113">Attribute</span></span>|<span data-ttu-id="2c65b-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2c65b-114">Description</span></span>|  
|---------------|-----------------|  
|`pickupDirectoryLocation`|<span data-ttu-id="2c65b-115">Uygulamaların e-postaları SMTP sunucusu tarafından daha sonra işlenmesi için kaydettiği dizin.</span><span class="sxs-lookup"><span data-stu-id="2c65b-115">The directory where applications save email for later processing by the SMTP server.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2c65b-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2c65b-116">Child Elements</span></span>  
 <span data-ttu-id="2c65b-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="2c65b-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2c65b-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2c65b-118">Parent Elements</span></span>  
  
|<span data-ttu-id="2c65b-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="2c65b-119">Element</span></span>|<span data-ttu-id="2c65b-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2c65b-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2c65b-121">\<smtp> Elemanı (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="2c65b-121">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="2c65b-122">Basit Posta Aktarım Protokolü (SMTP) posta gönderme seçeneklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="2c65b-122">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2c65b-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2c65b-123">Remarks</span></span>  
 <span data-ttu-id="2c65b-124">Öznitelik, `specifiedPickupDirectory` uygulamaların SMTP sunucusu tarafından işlenecek posta iletilerini kaydettiği dizini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="2c65b-124">The `specifiedPickupDirectory` attribute sets the directory where applications save mail messages to be processed by the SMTP server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2c65b-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="2c65b-125">Example</span></span>  
 <span data-ttu-id="2c65b-126">Aşağıdaki örnek, c:\maildrop'u posta alma dizinini belirtir.</span><span class="sxs-lookup"><span data-stu-id="2c65b-126">The following example specifies c:\maildrop as the mail pickup directory.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="SpecifiedPickupDirectory">  
        <specifiedPickupDirectory  
          pickupDirectoryLocation="c:\maildrop"  
        />  
      </smtp>  
    </mailSettings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2c65b-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2c65b-127">See also</span></span>

- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSpecifiedPickupDirectoryElement?displayProperty=nameWithType>
- [<span data-ttu-id="2c65b-128">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="2c65b-128">Network Settings Schema</span></span>](index.md)
