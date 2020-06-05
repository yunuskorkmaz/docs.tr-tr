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
ms.sourcegitcommit: 0a798a7e9680e2d0a5a81a3eaa203870ea782883
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/03/2020
ms.locfileid: "79154614"
---
# <a name="specifiedpickupdirectory-element-network-settings"></a><span data-ttu-id="5c702-102">\<specifiedPickupDirectory> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="5c702-102">\<specifiedPickupDirectory> Element (Network Settings)</span></span>
<span data-ttu-id="5c702-103">, Bir Basit Posta Aktarım Protokolü (SMTP) sunucusu için yerel dizini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="5c702-103">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<smtp>**](smtp-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<specifiedPickupDirectory>**  
  
## <a name="syntax"></a><span data-ttu-id="5c702-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5c702-104">Syntax</span></span>  
  
```xml  
<specifiedPickupDirectory  
  pickupDirectoryLocation="directory"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5c702-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5c702-105">Attributes and Elements</span></span>  
 <span data-ttu-id="5c702-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5c702-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5c702-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5c702-107">Attributes</span></span>  
  
|<span data-ttu-id="5c702-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5c702-108">Attribute</span></span>|<span data-ttu-id="5c702-109">Description</span><span class="sxs-lookup"><span data-stu-id="5c702-109">Description</span></span>|  
|---------------|-----------------|  
|`pickupDirectoryLocation`|<span data-ttu-id="5c702-110">Uygulamaların SMTP sunucusu tarafından daha sonra işlenmek üzere e-posta kaydetmesinin bulunduğu dizin.</span><span class="sxs-lookup"><span data-stu-id="5c702-110">The directory where applications save email for later processing by the SMTP server.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5c702-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5c702-111">Child Elements</span></span>  
 <span data-ttu-id="5c702-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="5c702-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5c702-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5c702-113">Parent Elements</span></span>  
  
|<span data-ttu-id="5c702-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="5c702-114">Element</span></span>|<span data-ttu-id="5c702-115">Description</span><span class="sxs-lookup"><span data-stu-id="5c702-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5c702-116">\<smtp>Öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="5c702-116">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="5c702-117">Basit Posta Aktarım Protokolü (SMTP) posta gönderme seçeneklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="5c702-117">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5c702-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5c702-118">Remarks</span></span>  
 <span data-ttu-id="5c702-119">`specifiedPickupDirectory`Özniteliği, uygulamaların posta ILETILERINI SMTP sunucusu tarafından işlenmek üzere kaydetmediği dizini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="5c702-119">The `specifiedPickupDirectory` attribute sets the directory where applications save mail messages to be processed by the SMTP server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5c702-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="5c702-120">Example</span></span>  
 <span data-ttu-id="5c702-121">Aşağıdaki örnekte posta toplama dizini olarak c:\maildrop belirtilir.</span><span class="sxs-lookup"><span data-stu-id="5c702-121">The following example specifies c:\maildrop as the mail pickup directory.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5c702-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5c702-122">See also</span></span>

- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSpecifiedPickupDirectoryElement?displayProperty=nameWithType>
- [<span data-ttu-id="5c702-123">Ağ ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="5c702-123">Network Settings Schema</span></span>](index.md)
