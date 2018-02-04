---
title: "&lt;specifiedPickupDirectory&gt; öğesi (ağ ayarları)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#specifiedPickupDirectory
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/specifiedPickupDirectory
helpviewer_keywords:
- specifiedPickupDirectory element
- <specifiedPickupDirectory> element
ms.assetid: 0121f49d-bff2-4bc6-af06-f1628dcd61f1
caps.latest.revision: 
author: mcleblanc
ms.author: markl
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: e68ce8cac4048ee2df89d0241cc50242e20391a2
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/01/2018
---
# <a name="ltspecifiedpickupdirectorygt-element-network-settings"></a><span data-ttu-id="31374-102">&lt;specifiedPickupDirectory&gt; öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="31374-102">&lt;specifiedPickupDirectory&gt; Element (Network Settings)</span></span>
<span data-ttu-id="31374-103">Basit Posta Aktarım Protokolü (SMTP) sunucusunun yerel dizin yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="31374-103">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>  
  
 <span data-ttu-id="31374-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="31374-104">\<configuration></span></span>  
<span data-ttu-id="31374-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="31374-105">\<system.net></span></span>  
<span data-ttu-id="31374-106">\<mailSettings></span><span class="sxs-lookup"><span data-stu-id="31374-106">\<mailSettings></span></span>  
<span data-ttu-id="31374-107">\<smtp></span><span class="sxs-lookup"><span data-stu-id="31374-107">\<smtp></span></span>  
<span data-ttu-id="31374-108">\<specifiedPickupDirectory></span><span class="sxs-lookup"><span data-stu-id="31374-108">\<specifiedPickupDirectory></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31374-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="31374-109">Syntax</span></span>  
  
```xml  
<specifiedPickupDirectory  
  pickupDirectoryLocation="directory"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="31374-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="31374-110">Attributes and Elements</span></span>  
 <span data-ttu-id="31374-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="31374-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="31374-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="31374-112">Attributes</span></span>  
  
|<span data-ttu-id="31374-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="31374-113">Attribute</span></span>|<span data-ttu-id="31374-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="31374-114">Description</span></span>|  
|---------------|-----------------|  
|`pickupDirectoryLocation`|<span data-ttu-id="31374-115">Uygulamaları daha sonra SMTP sunucusu tarafından işlenmek için e-posta kaydetmek dizin.</span><span class="sxs-lookup"><span data-stu-id="31374-115">The directory where applications save email for later processing by the SMTP server.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="31374-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="31374-116">Child Elements</span></span>  
 <span data-ttu-id="31374-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="31374-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="31374-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="31374-118">Parent Elements</span></span>  
  
|<span data-ttu-id="31374-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="31374-119">Element</span></span>|<span data-ttu-id="31374-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="31374-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="31374-121">\<SMTP > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="31374-121">\<smtp> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|<span data-ttu-id="31374-122">Basit Posta Aktarım Protokolü (SMTP) posta gönderme seçenekleri yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="31374-122">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="31374-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="31374-123">Remarks</span></span>  
 <span data-ttu-id="31374-124">`specifiedPickupDirectory` Öznitelik uygulamaları posta iletileri SMTP sunucusu tarafından işlenmek üzere kaydetmek dizini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="31374-124">The `specifiedPickupDirectory` attribute sets the directory where applications save mail messages to be processed by the SMTP server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="31374-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="31374-125">Example</span></span>  
 <span data-ttu-id="31374-126">Aşağıdaki örnek c:\maildrop posta toplama dizini belirtir.</span><span class="sxs-lookup"><span data-stu-id="31374-126">The following example specifies c:\maildrop as the mail pickup directory.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="31374-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="31374-127">See Also</span></span>  
 <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.SmtpSpecifiedPickupDirectoryElement?displayProperty=nameWithType>  
 [<span data-ttu-id="31374-128">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="31374-128">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
