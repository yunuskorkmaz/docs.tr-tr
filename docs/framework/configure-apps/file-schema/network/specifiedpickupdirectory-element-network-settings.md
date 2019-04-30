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
ms.openlocfilehash: a459fee557285935c383dcfaf512c8a8a9aea570
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674382"
---
# <a name="specifiedpickupdirectory-element-network-settings"></a><span data-ttu-id="1cc58-102">\<specifiedPickupDirectory > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="1cc58-102">\<specifiedPickupDirectory> Element (Network Settings)</span></span>
<span data-ttu-id="1cc58-103">Bir Basit Posta Aktarım Protokolü (SMTP) sunucusu için yerel dizini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="1cc58-103">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>  
  
 <span data-ttu-id="1cc58-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="1cc58-104">\<configuration></span></span>  
<span data-ttu-id="1cc58-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="1cc58-105">\<system.net></span></span>  
<span data-ttu-id="1cc58-106">\<mailSettings ></span><span class="sxs-lookup"><span data-stu-id="1cc58-106">\<mailSettings></span></span>  
<span data-ttu-id="1cc58-107">\<SMTP ></span><span class="sxs-lookup"><span data-stu-id="1cc58-107">\<smtp></span></span>  
<span data-ttu-id="1cc58-108">\<specifiedPickupDirectory ></span><span class="sxs-lookup"><span data-stu-id="1cc58-108">\<specifiedPickupDirectory></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1cc58-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1cc58-109">Syntax</span></span>  
  
```xml  
<specifiedPickupDirectory  
  pickupDirectoryLocation="directory"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1cc58-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1cc58-110">Attributes and Elements</span></span>  
 <span data-ttu-id="1cc58-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1cc58-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1cc58-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1cc58-112">Attributes</span></span>  
  
|<span data-ttu-id="1cc58-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="1cc58-113">Attribute</span></span>|<span data-ttu-id="1cc58-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1cc58-114">Description</span></span>|  
|---------------|-----------------|  
|`pickupDirectoryLocation`|<span data-ttu-id="1cc58-115">SMTP sunucusu tarafından daha sonra işlenmek için e-posta uygulamaları kaydetmek dizin.</span><span class="sxs-lookup"><span data-stu-id="1cc58-115">The directory where applications save email for later processing by the SMTP server.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1cc58-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1cc58-116">Child Elements</span></span>  
 <span data-ttu-id="1cc58-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="1cc58-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1cc58-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1cc58-118">Parent Elements</span></span>  
  
|<span data-ttu-id="1cc58-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="1cc58-119">Element</span></span>|<span data-ttu-id="1cc58-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1cc58-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1cc58-121">\<SMTP > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="1cc58-121">\<smtp> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|<span data-ttu-id="1cc58-122">Basit Posta Aktarım Protokolü (SMTP) posta gönderme seçeneklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="1cc58-122">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1cc58-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1cc58-123">Remarks</span></span>  
 <span data-ttu-id="1cc58-124">`specifiedPickupDirectory` Özniteliği uygulamaları e-posta iletileri SMTP sunucusu tarafından işlenecek kaydetmek dizin ayarlar.</span><span class="sxs-lookup"><span data-stu-id="1cc58-124">The `specifiedPickupDirectory` attribute sets the directory where applications save mail messages to be processed by the SMTP server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1cc58-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="1cc58-125">Example</span></span>  
 <span data-ttu-id="1cc58-126">Aşağıdaki örnek, posta toplama dizini c:\maildrop belirtir.</span><span class="sxs-lookup"><span data-stu-id="1cc58-126">The following example specifies c:\maildrop as the mail pickup directory.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1cc58-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1cc58-127">See also</span></span>

- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSpecifiedPickupDirectoryElement?displayProperty=nameWithType>
- [<span data-ttu-id="1cc58-128">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="1cc58-128">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
