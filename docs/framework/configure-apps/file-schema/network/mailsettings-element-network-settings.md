---
title: '&lt;mailSettings&gt; öğesi (ağ ayarları)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#mailSettings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings
helpviewer_keywords:
- mailSettings element
- <mailSettings> element
ms.assetid: 54f0f153-17e5-4f49-afdc-deadb940c9c1
author: mcleblanc
ms.author: markl
ms.openlocfilehash: f3a706edaeba551139368568a7467e0cdab3524c
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47208601"
---
# <a name="ltmailsettingsgt-element-network-settings"></a><span data-ttu-id="eefcb-102">&lt;mailSettings&gt; öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="eefcb-102">&lt;mailSettings&gt; Element (Network Settings)</span></span>
<span data-ttu-id="eefcb-103">Posta gönderme seçeneklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="eefcb-103">Configures mail sending options.</span></span>  

<span data-ttu-id="eefcb-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="eefcb-104">\<configuration></span></span>  
<span data-ttu-id="eefcb-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="eefcb-105">\<system.net></span></span>  
<span data-ttu-id="eefcb-106">\<mailSettings ></span><span class="sxs-lookup"><span data-stu-id="eefcb-106">\<mailSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eefcb-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="eefcb-107">Syntax</span></span>  
  
```xml  
<mailSettings>
  <smtp> … </smtp>  
</mailSettings>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eefcb-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="eefcb-108">Attributes and Elements</span></span>  
 <span data-ttu-id="eefcb-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="eefcb-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eefcb-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="eefcb-110">Attributes</span></span>  
 <span data-ttu-id="eefcb-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="eefcb-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="eefcb-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="eefcb-112">Child Elements</span></span>  
  
|<span data-ttu-id="eefcb-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="eefcb-113">Attribute</span></span>|<span data-ttu-id="eefcb-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eefcb-114">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="eefcb-115">\<SMTP > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="eefcb-115">\<smtp> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|<span data-ttu-id="eefcb-116">Basit Posta Aktarım Protokolü seçeneklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="eefcb-116">Configures Simple Mail Transport Protocol options.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="eefcb-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="eefcb-117">Parent Elements</span></span>  
  
|<span data-ttu-id="eefcb-118">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="eefcb-118">**Element**</span></span>|<span data-ttu-id="eefcb-119">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="eefcb-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="eefcb-120">\<system.Net > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="eefcb-120">\<system.Net> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="eefcb-121">.NET Framework ağa nasıl bağlandığını belirten ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="eefcb-121">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="eefcb-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="eefcb-122">Example</span></span>  
 <span data-ttu-id="eefcb-123">Aşağıdaki örnek, varsayılan ağ kimlik bilgilerini kullanarak e-posta göndermek için uygun SMTP parametrelerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="eefcb-123">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="Network">  
        <network  
          host="localhost"  
          port="25"  
          defaultCredentials="true"  
        />  
      </smtp>  
    </mailSettings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="eefcb-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="eefcb-124">See Also</span></span>  
 <xref:System.Net.Mail.SmtpClient>  
 [<span data-ttu-id="eefcb-125">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="eefcb-125">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
