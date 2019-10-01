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
ms.openlocfilehash: 47aa357dac8b6bf71ce8c391004af16f8c98e347
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697600"
---
# <a name="specifiedpickupdirectory-element-network-settings"></a><span data-ttu-id="5ab96-102">\<Belirtilmedipickupdirectory > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="5ab96-102">\<specifiedPickupDirectory> Element (Network Settings)</span></span>
<span data-ttu-id="5ab96-103">, Bir Basit Posta Aktarım Protokolü (SMTP) sunucusu için yerel dizini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="5ab96-103">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>  
  
[<span data-ttu-id="5ab96-104"> **\<Yapılandırma >** </span><span class="sxs-lookup"><span data-stu-id="5ab96-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="5ab96-105">&nbsp; @ no__t-1[ **@no__t -4system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="5ab96-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="5ab96-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<mailSettings >** ](mailsettings-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="5ab96-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)</span></span>  
<span data-ttu-id="5ab96-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<smtp >** ](smtp-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="5ab96-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<smtp>**](smtp-element-network-settings.md)</span></span>  
<span data-ttu-id="5ab96-108">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7 **\<Belirtilmedipickupdirectory >**</span><span class="sxs-lookup"><span data-stu-id="5ab96-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<specifiedPickupDirectory>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ab96-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5ab96-109">Syntax</span></span>  
  
```xml  
<specifiedPickupDirectory  
  pickupDirectoryLocation="directory"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5ab96-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5ab96-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5ab96-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5ab96-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5ab96-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5ab96-112">Attributes</span></span>  
  
|<span data-ttu-id="5ab96-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5ab96-113">Attribute</span></span>|<span data-ttu-id="5ab96-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5ab96-114">Description</span></span>|  
|---------------|-----------------|  
|`pickupDirectoryLocation`|<span data-ttu-id="5ab96-115">Uygulamaların SMTP sunucusu tarafından daha sonra işlenmek üzere e-posta kaydetmesinin bulunduğu dizin.</span><span class="sxs-lookup"><span data-stu-id="5ab96-115">The directory where applications save email for later processing by the SMTP server.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5ab96-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5ab96-116">Child Elements</span></span>  
 <span data-ttu-id="5ab96-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="5ab96-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5ab96-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5ab96-118">Parent Elements</span></span>  
  
|<span data-ttu-id="5ab96-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="5ab96-119">Element</span></span>|<span data-ttu-id="5ab96-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5ab96-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5ab96-121">\<smtp > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="5ab96-121">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="5ab96-122">Basit Posta Aktarım Protokolü (SMTP) posta gönderme seçeneklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="5ab96-122">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5ab96-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5ab96-123">Remarks</span></span>  
 <span data-ttu-id="5ab96-124">@No__t-0 özniteliği, uygulamaların posta iletilerini SMTP sunucusu tarafından işlenmek üzere kaydetmediği dizini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="5ab96-124">The `specifiedPickupDirectory` attribute sets the directory where applications save mail messages to be processed by the SMTP server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ab96-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="5ab96-125">Example</span></span>  
 <span data-ttu-id="5ab96-126">Aşağıdaki örnekte posta toplama dizini olarak c:\maildrop belirtilir.</span><span class="sxs-lookup"><span data-stu-id="5ab96-126">The following example specifies c:\maildrop as the mail pickup directory.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5ab96-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5ab96-127">See also</span></span>

- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSpecifiedPickupDirectoryElement?displayProperty=nameWithType>
- [<span data-ttu-id="5ab96-128">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="5ab96-128">Network Settings Schema</span></span>](index.md)
