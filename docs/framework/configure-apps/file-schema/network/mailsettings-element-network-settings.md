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
manager: markl
ms.openlocfilehash: 5bc7cc649b18a5330d056bbddfe96db4ecca2ec8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltmailsettingsgt-element-network-settings"></a><span data-ttu-id="1ab8b-102">&lt;mailSettings&gt; öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="1ab8b-102">&lt;mailSettings&gt; Element (Network Settings)</span></span>
<span data-ttu-id="1ab8b-103">Posta gönderme seçenekleri yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="1ab8b-103">Configures mail sending options.</span></span>  

<span data-ttu-id="1ab8b-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="1ab8b-104">\<configuration></span></span>  
<span data-ttu-id="1ab8b-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="1ab8b-105">\<system.net></span></span>  
<span data-ttu-id="1ab8b-106">\<mailSettings ></span><span class="sxs-lookup"><span data-stu-id="1ab8b-106">\<mailSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ab8b-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1ab8b-107">Syntax</span></span>  
  
```xml  
<mailSettings>
  <smtp> … </smtp>  
</mailSettings>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1ab8b-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1ab8b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="1ab8b-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1ab8b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1ab8b-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1ab8b-110">Attributes</span></span>  
 <span data-ttu-id="1ab8b-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="1ab8b-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1ab8b-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1ab8b-112">Child Elements</span></span>  
  
|<span data-ttu-id="1ab8b-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="1ab8b-113">Attribute</span></span>|<span data-ttu-id="1ab8b-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1ab8b-114">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="1ab8b-115">\<SMTP > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="1ab8b-115">\<smtp> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|<span data-ttu-id="1ab8b-116">Basit Posta Aktarım Protokolü seçenekleri yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="1ab8b-116">Configures Simple Mail Transport Protocol options.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1ab8b-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1ab8b-117">Parent Elements</span></span>  
  
|<span data-ttu-id="1ab8b-118">**Öğesi**</span><span class="sxs-lookup"><span data-stu-id="1ab8b-118">**Element**</span></span>|<span data-ttu-id="1ab8b-119">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="1ab8b-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="1ab8b-120">\<system.Net > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="1ab8b-120">\<system.Net> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="1ab8b-121">.NET Framework ağa nasıl bağlanacağını belirtin ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="1ab8b-121">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1ab8b-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="1ab8b-122">Example</span></span>  
 <span data-ttu-id="1ab8b-123">Aşağıdaki örnek, varsayılan ağ kimlik bilgilerini kullanarak e-posta göndermek için uygun SMTP parametreleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="1ab8b-123">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="network">  
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
  
## <a name="see-also"></a><span data-ttu-id="1ab8b-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1ab8b-124">See Also</span></span>  
 <xref:System.Net.Mail.SmtpClient>  
 [<span data-ttu-id="1ab8b-125">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="1ab8b-125">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
