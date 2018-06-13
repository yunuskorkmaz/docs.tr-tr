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
ms.openlocfilehash: 3a982bdbe4953691d4e8e7663f14059ff4771934
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32743982"
---
# <a name="ltspecifiedpickupdirectorygt-element-network-settings"></a><span data-ttu-id="8a208-102">&lt;specifiedPickupDirectory&gt; öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="8a208-102">&lt;specifiedPickupDirectory&gt; Element (Network Settings)</span></span>
<span data-ttu-id="8a208-103">Basit Posta Aktarım Protokolü (SMTP) sunucusunun yerel dizin yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="8a208-103">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>  
  
 <span data-ttu-id="8a208-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="8a208-104">\<configuration></span></span>  
<span data-ttu-id="8a208-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="8a208-105">\<system.net></span></span>  
<span data-ttu-id="8a208-106">\<mailSettings ></span><span class="sxs-lookup"><span data-stu-id="8a208-106">\<mailSettings></span></span>  
<span data-ttu-id="8a208-107">\<SMTP ></span><span class="sxs-lookup"><span data-stu-id="8a208-107">\<smtp></span></span>  
<span data-ttu-id="8a208-108">\<specifiedPickupDirectory ></span><span class="sxs-lookup"><span data-stu-id="8a208-108">\<specifiedPickupDirectory></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a208-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8a208-109">Syntax</span></span>  
  
```xml  
<specifiedPickupDirectory  
  pickupDirectoryLocation="directory"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8a208-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8a208-110">Attributes and Elements</span></span>  
 <span data-ttu-id="8a208-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8a208-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8a208-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8a208-112">Attributes</span></span>  
  
|<span data-ttu-id="8a208-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="8a208-113">Attribute</span></span>|<span data-ttu-id="8a208-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8a208-114">Description</span></span>|  
|---------------|-----------------|  
|`pickupDirectoryLocation`|<span data-ttu-id="8a208-115">Uygulamaları daha sonra SMTP sunucusu tarafından işlenmek için e-posta kaydetmek dizin.</span><span class="sxs-lookup"><span data-stu-id="8a208-115">The directory where applications save email for later processing by the SMTP server.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8a208-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8a208-116">Child Elements</span></span>  
 <span data-ttu-id="8a208-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="8a208-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8a208-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8a208-118">Parent Elements</span></span>  
  
|<span data-ttu-id="8a208-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="8a208-119">Element</span></span>|<span data-ttu-id="8a208-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8a208-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8a208-121">\<SMTP > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="8a208-121">\<smtp> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|<span data-ttu-id="8a208-122">Basit Posta Aktarım Protokolü (SMTP) posta gönderme seçenekleri yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="8a208-122">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8a208-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8a208-123">Remarks</span></span>  
 <span data-ttu-id="8a208-124">`specifiedPickupDirectory` Öznitelik uygulamaları posta iletileri SMTP sunucusu tarafından işlenmek üzere kaydetmek dizini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="8a208-124">The `specifiedPickupDirectory` attribute sets the directory where applications save mail messages to be processed by the SMTP server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8a208-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="8a208-125">Example</span></span>  
 <span data-ttu-id="8a208-126">Aşağıdaki örnek c:\maildrop posta toplama dizini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8a208-126">The following example specifies c:\maildrop as the mail pickup directory.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="specifiedPickupDirectory">  
        <specifiedPickupDirectory  
          pickupDirectoryLocation="c:\maildrop"  
        />  
      </smtp>  
    </mailSettings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8a208-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8a208-127">See Also</span></span>  
 <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.SmtpSpecifiedPickupDirectoryElement?displayProperty=nameWithType>  
 [<span data-ttu-id="8a208-128">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="8a208-128">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
