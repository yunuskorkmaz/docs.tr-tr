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
manager: markl
ms.openlocfilehash: 50ab7387fc5e2cac65cac1a6dba0e563225beec9
ms.sourcegitcommit: 59b51cd7c95c75be85bd6ef715e9ef8c85720bac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37874708"
---
# <a name="ltspecifiedpickupdirectorygt-element-network-settings"></a><span data-ttu-id="91e93-102">&lt;specifiedPickupDirectory&gt; öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="91e93-102">&lt;specifiedPickupDirectory&gt; Element (Network Settings)</span></span>
<span data-ttu-id="91e93-103">Bir Basit Posta Aktarım Protokolü (SMTP) sunucusu için yerel dizini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="91e93-103">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>  
  
 <span data-ttu-id="91e93-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="91e93-104">\<configuration></span></span>  
<span data-ttu-id="91e93-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="91e93-105">\<system.net></span></span>  
<span data-ttu-id="91e93-106">\<mailSettings ></span><span class="sxs-lookup"><span data-stu-id="91e93-106">\<mailSettings></span></span>  
<span data-ttu-id="91e93-107">\<SMTP ></span><span class="sxs-lookup"><span data-stu-id="91e93-107">\<smtp></span></span>  
<span data-ttu-id="91e93-108">\<specifiedPickupDirectory ></span><span class="sxs-lookup"><span data-stu-id="91e93-108">\<specifiedPickupDirectory></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91e93-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="91e93-109">Syntax</span></span>  
  
```xml  
<specifiedPickupDirectory  
  pickupDirectoryLocation="directory"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="91e93-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="91e93-110">Attributes and Elements</span></span>  
 <span data-ttu-id="91e93-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="91e93-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="91e93-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="91e93-112">Attributes</span></span>  
  
|<span data-ttu-id="91e93-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="91e93-113">Attribute</span></span>|<span data-ttu-id="91e93-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="91e93-114">Description</span></span>|  
|---------------|-----------------|  
|`pickupDirectoryLocation`|<span data-ttu-id="91e93-115">SMTP sunucusu tarafından daha sonra işlenmek için e-posta uygulamaları kaydetmek dizin.</span><span class="sxs-lookup"><span data-stu-id="91e93-115">The directory where applications save email for later processing by the SMTP server.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="91e93-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="91e93-116">Child Elements</span></span>  
 <span data-ttu-id="91e93-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="91e93-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="91e93-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="91e93-118">Parent Elements</span></span>  
  
|<span data-ttu-id="91e93-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="91e93-119">Element</span></span>|<span data-ttu-id="91e93-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="91e93-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="91e93-121">\<SMTP > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="91e93-121">\<smtp> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|<span data-ttu-id="91e93-122">Basit Posta Aktarım Protokolü (SMTP) posta gönderme seçeneklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="91e93-122">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="91e93-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="91e93-123">Remarks</span></span>  
 <span data-ttu-id="91e93-124">`specifiedPickupDirectory` Özniteliği uygulamaları e-posta iletileri SMTP sunucusu tarafından işlenecek kaydetmek dizin ayarlar.</span><span class="sxs-lookup"><span data-stu-id="91e93-124">The `specifiedPickupDirectory` attribute sets the directory where applications save mail messages to be processed by the SMTP server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="91e93-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="91e93-125">Example</span></span>  
 <span data-ttu-id="91e93-126">Aşağıdaki örnek, posta toplama dizini c:\maildrop belirtir.</span><span class="sxs-lookup"><span data-stu-id="91e93-126">The following example specifies c:\maildrop as the mail pickup directory.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="91e93-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="91e93-127">See Also</span></span>  
 <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.SmtpSpecifiedPickupDirectoryElement?displayProperty=nameWithType>  
 [<span data-ttu-id="91e93-128">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="91e93-128">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
