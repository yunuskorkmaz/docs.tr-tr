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
ms.openlocfilehash: e23b9e1fdf8a348d0d38575db8112b37c8dd9b69
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50048768"
---
# <a name="ltmailsettingsgt-element-network-settings"></a><span data-ttu-id="91033-102">&lt;mailSettings&gt; öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="91033-102">&lt;mailSettings&gt; Element (Network Settings)</span></span>
<span data-ttu-id="91033-103">Posta gönderme seçeneklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="91033-103">Configures mail sending options.</span></span>  

<span data-ttu-id="91033-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="91033-104">\<configuration></span></span>  
<span data-ttu-id="91033-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="91033-105">\<system.net></span></span>  
<span data-ttu-id="91033-106">\<mailSettings ></span><span class="sxs-lookup"><span data-stu-id="91033-106">\<mailSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91033-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="91033-107">Syntax</span></span>  
  
```xml  
<mailSettings>
  <smtp> … </smtp>  
</mailSettings>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="91033-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="91033-108">Attributes and Elements</span></span>  
 <span data-ttu-id="91033-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="91033-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="91033-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="91033-110">Attributes</span></span>  
 <span data-ttu-id="91033-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="91033-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="91033-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="91033-112">Child Elements</span></span>  
  
|<span data-ttu-id="91033-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="91033-113">Attribute</span></span>|<span data-ttu-id="91033-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="91033-114">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="91033-115">\<SMTP > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="91033-115">\<smtp> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|<span data-ttu-id="91033-116">Basit Posta Aktarım Protokolü seçeneklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="91033-116">Configures Simple Mail Transport Protocol options.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="91033-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="91033-117">Parent Elements</span></span>  
  
|<span data-ttu-id="91033-118">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="91033-118">**Element**</span></span>|<span data-ttu-id="91033-119">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="91033-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="91033-120">\<system.Net > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="91033-120">\<system.Net> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="91033-121">.NET Framework ağa nasıl bağlandığını belirten ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="91033-121">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="91033-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="91033-122">Example</span></span>  
 <span data-ttu-id="91033-123">Aşağıdaki örnek, varsayılan ağ kimlik bilgilerini kullanarak e-posta göndermek için uygun SMTP parametrelerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="91033-123">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="91033-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="91033-124">See Also</span></span>  
 <xref:System.Net.Mail.SmtpClient>  
 [<span data-ttu-id="91033-125">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="91033-125">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
