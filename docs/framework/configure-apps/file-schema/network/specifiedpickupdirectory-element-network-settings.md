---
title: <specifiedPickupDirectory> Öğesi (Ağ Ayarları)
description: <specifiedPickupDirectory>Ağ ayarları öğesi .NET Framework BIR SMTP sunucusu seçenekleri için yerel dizini yapılandırır.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#specifiedPickupDirectory
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/specifiedPickupDirectory
helpviewer_keywords:
- specifiedPickupDirectory element
- <specifiedPickupDirectory> element
ms.assetid: 0121f49d-bff2-4bc6-af06-f1628dcd61f1
ms.openlocfilehash: f0c4c1845e9542d0f3b836ff03f16bdf2979ebd8
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504504"
---
# <a name="specifiedpickupdirectory-element-network-settings"></a><span data-ttu-id="094e5-103">\<specifiedPickupDirectory> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="094e5-103">\<specifiedPickupDirectory> Element (Network Settings)</span></span>
<span data-ttu-id="094e5-104">, Bir Basit Posta Aktarım Protokolü (SMTP) sunucusu için yerel dizini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="094e5-104">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<smtp>**](smtp-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<specifiedPickupDirectory>**  
  
## <a name="syntax"></a><span data-ttu-id="094e5-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="094e5-105">Syntax</span></span>  
  
```xml  
<specifiedPickupDirectory  
  pickupDirectoryLocation="directory"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="094e5-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="094e5-106">Attributes and Elements</span></span>  
 <span data-ttu-id="094e5-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="094e5-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="094e5-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="094e5-108">Attributes</span></span>  
  
|<span data-ttu-id="094e5-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="094e5-109">Attribute</span></span>|<span data-ttu-id="094e5-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="094e5-110">Description</span></span>|  
|---------------|-----------------|  
|`pickupDirectoryLocation`|<span data-ttu-id="094e5-111">Uygulamaların SMTP sunucusu tarafından daha sonra işlenmek üzere e-posta kaydetmesinin bulunduğu dizin.</span><span class="sxs-lookup"><span data-stu-id="094e5-111">The directory where applications save email for later processing by the SMTP server.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="094e5-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="094e5-112">Child Elements</span></span>  
 <span data-ttu-id="094e5-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="094e5-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="094e5-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="094e5-114">Parent Elements</span></span>  
  
|<span data-ttu-id="094e5-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="094e5-115">Element</span></span>|<span data-ttu-id="094e5-116">Description</span><span class="sxs-lookup"><span data-stu-id="094e5-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="094e5-117">\<smtp>Öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="094e5-117">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="094e5-118">Basit Posta Aktarım Protokolü (SMTP) posta gönderme seçeneklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="094e5-118">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="094e5-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="094e5-119">Remarks</span></span>  
 <span data-ttu-id="094e5-120">`specifiedPickupDirectory`Özniteliği, uygulamaların posta ILETILERINI SMTP sunucusu tarafından işlenmek üzere kaydetmediği dizini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="094e5-120">The `specifiedPickupDirectory` attribute sets the directory where applications save mail messages to be processed by the SMTP server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="094e5-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="094e5-121">Example</span></span>  
 <span data-ttu-id="094e5-122">Aşağıdaki örnekte posta toplama dizini olarak c:\maildrop belirtilir.</span><span class="sxs-lookup"><span data-stu-id="094e5-122">The following example specifies c:\maildrop as the mail pickup directory.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="094e5-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="094e5-123">See also</span></span>

- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSpecifiedPickupDirectoryElement?displayProperty=nameWithType>
- [<span data-ttu-id="094e5-124">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="094e5-124">Network Settings Schema</span></span>](index.md)
