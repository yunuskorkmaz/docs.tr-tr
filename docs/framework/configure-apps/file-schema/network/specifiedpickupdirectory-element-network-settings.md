---
title: '&lt;specifiedPickupDirectory&gt; öğesi (ağ ayarları)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#specifiedPickupDirectory
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/specifiedPickupDirectory
helpviewer_keywords:
- specifiedPickupDirectory element
- <specifiedPickupDirectory> element
ms.assetid: 0121f49d-bff2-4bc6-af06-f1628dcd61f1
author: mcleblanc
ms.author: markl
ms.openlocfilehash: b62dc1a9118f7d4f1f693ade36626deaecd23999
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47459743"
---
# <a name="ltspecifiedpickupdirectorygt-element-network-settings"></a><span data-ttu-id="3c4e0-102">&lt;specifiedPickupDirectory&gt; öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="3c4e0-102">&lt;specifiedPickupDirectory&gt; Element (Network Settings)</span></span>
<span data-ttu-id="3c4e0-103">Bir Basit Posta Aktarım Protokolü (SMTP) sunucusu için yerel dizini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="3c4e0-103">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>  
  
 <span data-ttu-id="3c4e0-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="3c4e0-104">\<configuration></span></span>  
<span data-ttu-id="3c4e0-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="3c4e0-105">\<system.net></span></span>  
<span data-ttu-id="3c4e0-106">\<mailSettings ></span><span class="sxs-lookup"><span data-stu-id="3c4e0-106">\<mailSettings></span></span>  
<span data-ttu-id="3c4e0-107">\<SMTP ></span><span class="sxs-lookup"><span data-stu-id="3c4e0-107">\<smtp></span></span>  
<span data-ttu-id="3c4e0-108">\<specifiedPickupDirectory ></span><span class="sxs-lookup"><span data-stu-id="3c4e0-108">\<specifiedPickupDirectory></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c4e0-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3c4e0-109">Syntax</span></span>  
  
```xml  
<specifiedPickupDirectory  
  pickupDirectoryLocation="directory"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3c4e0-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3c4e0-110">Attributes and Elements</span></span>  
 <span data-ttu-id="3c4e0-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3c4e0-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3c4e0-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3c4e0-112">Attributes</span></span>  
  
|<span data-ttu-id="3c4e0-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3c4e0-113">Attribute</span></span>|<span data-ttu-id="3c4e0-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3c4e0-114">Description</span></span>|  
|---------------|-----------------|  
|`pickupDirectoryLocation`|<span data-ttu-id="3c4e0-115">SMTP sunucusu tarafından daha sonra işlenmek için e-posta uygulamaları kaydetmek dizin.</span><span class="sxs-lookup"><span data-stu-id="3c4e0-115">The directory where applications save email for later processing by the SMTP server.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3c4e0-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3c4e0-116">Child Elements</span></span>  
 <span data-ttu-id="3c4e0-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="3c4e0-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3c4e0-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3c4e0-118">Parent Elements</span></span>  
  
|<span data-ttu-id="3c4e0-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="3c4e0-119">Element</span></span>|<span data-ttu-id="3c4e0-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3c4e0-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3c4e0-121">\<SMTP > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="3c4e0-121">\<smtp> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|<span data-ttu-id="3c4e0-122">Basit Posta Aktarım Protokolü (SMTP) posta gönderme seçeneklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="3c4e0-122">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3c4e0-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3c4e0-123">Remarks</span></span>  
 <span data-ttu-id="3c4e0-124">`specifiedPickupDirectory` Özniteliği uygulamaları e-posta iletileri SMTP sunucusu tarafından işlenecek kaydetmek dizin ayarlar.</span><span class="sxs-lookup"><span data-stu-id="3c4e0-124">The `specifiedPickupDirectory` attribute sets the directory where applications save mail messages to be processed by the SMTP server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3c4e0-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="3c4e0-125">Example</span></span>  
 <span data-ttu-id="3c4e0-126">Aşağıdaki örnek, posta toplama dizini c:\maildrop belirtir.</span><span class="sxs-lookup"><span data-stu-id="3c4e0-126">The following example specifies c:\maildrop as the mail pickup directory.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3c4e0-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3c4e0-127">See Also</span></span>  
 <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.SmtpSpecifiedPickupDirectoryElement?displayProperty=nameWithType>  
 [<span data-ttu-id="3c4e0-128">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="3c4e0-128">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
