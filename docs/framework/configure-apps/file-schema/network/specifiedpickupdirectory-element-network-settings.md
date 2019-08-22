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
ms.openlocfilehash: b2e31dee4f5aff2bf6cedf5c4e9ca235695b0a53
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659092"
---
# <a name="specifiedpickupdirectory-element-network-settings"></a><span data-ttu-id="971a1-102">\<Belirtilmedipickupdirectory > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="971a1-102">\<specifiedPickupDirectory> Element (Network Settings)</span></span>
<span data-ttu-id="971a1-103">, Bir Basit Posta Aktarım Protokolü (SMTP) sunucusu için yerel dizini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="971a1-103">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>  
  
 <span data-ttu-id="971a1-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="971a1-104">\<configuration></span></span>  
<span data-ttu-id="971a1-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="971a1-105">\<system.net></span></span>  
<span data-ttu-id="971a1-106">\<mailSettings ></span><span class="sxs-lookup"><span data-stu-id="971a1-106">\<mailSettings></span></span>  
<span data-ttu-id="971a1-107">\<SMTP ></span><span class="sxs-lookup"><span data-stu-id="971a1-107">\<smtp></span></span>  
<span data-ttu-id="971a1-108">\<Belirtilmedipickupdirectory ></span><span class="sxs-lookup"><span data-stu-id="971a1-108">\<specifiedPickupDirectory></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="971a1-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="971a1-109">Syntax</span></span>  
  
```xml  
<specifiedPickupDirectory  
  pickupDirectoryLocation="directory"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="971a1-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="971a1-110">Attributes and Elements</span></span>  
 <span data-ttu-id="971a1-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="971a1-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="971a1-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="971a1-112">Attributes</span></span>  
  
|<span data-ttu-id="971a1-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="971a1-113">Attribute</span></span>|<span data-ttu-id="971a1-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="971a1-114">Description</span></span>|  
|---------------|-----------------|  
|`pickupDirectoryLocation`|<span data-ttu-id="971a1-115">Uygulamaların SMTP sunucusu tarafından daha sonra işlenmek üzere e-posta kaydetmesinin bulunduğu dizin.</span><span class="sxs-lookup"><span data-stu-id="971a1-115">The directory where applications save email for later processing by the SMTP server.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="971a1-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="971a1-116">Child Elements</span></span>  
 <span data-ttu-id="971a1-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="971a1-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="971a1-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="971a1-118">Parent Elements</span></span>  
  
|<span data-ttu-id="971a1-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="971a1-119">Element</span></span>|<span data-ttu-id="971a1-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="971a1-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="971a1-121">\<SMTP > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="971a1-121">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="971a1-122">Basit Posta Aktarım Protokolü (SMTP) posta gönderme seçeneklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="971a1-122">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="971a1-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="971a1-123">Remarks</span></span>  
 <span data-ttu-id="971a1-124">`specifiedPickupDirectory` Özniteliği, uygulamaların posta iletilerini SMTP sunucusu tarafından işlenmek üzere kaydetmediği dizini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="971a1-124">The `specifiedPickupDirectory` attribute sets the directory where applications save mail messages to be processed by the SMTP server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="971a1-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="971a1-125">Example</span></span>  
 <span data-ttu-id="971a1-126">Aşağıdaki örnekte posta toplama dizini olarak c:\maildrop belirtilir.</span><span class="sxs-lookup"><span data-stu-id="971a1-126">The following example specifies c:\maildrop as the mail pickup directory.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="971a1-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="971a1-127">See also</span></span>

- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSpecifiedPickupDirectoryElement?displayProperty=nameWithType>
- [<span data-ttu-id="971a1-128">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="971a1-128">Network Settings Schema</span></span>](index.md)
