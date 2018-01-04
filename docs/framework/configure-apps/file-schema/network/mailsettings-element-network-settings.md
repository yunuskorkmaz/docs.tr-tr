---
title: "&lt;mailSettings&gt; öğesi (ağ ayarları)"
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#mailSettings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings
helpviewer_keywords:
- mailSettings element
- <mailSettings> element
ms.assetid: 54f0f153-17e5-4f49-afdc-deadb940c9c1
caps.latest.revision: "20"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 5ae9ecdfa9cccb7c70c153153b921151aad50e7c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltmailsettingsgt-element-network-settings"></a><span data-ttu-id="b7210-102">&lt;mailSettings&gt; öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="b7210-102">&lt;mailSettings&gt; Element (Network Settings)</span></span>
<span data-ttu-id="b7210-103">Posta gönderme seçenekleri yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="b7210-103">Configures mail sending options.</span></span>  

<span data-ttu-id="b7210-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="b7210-104">\<configuration></span></span>  
<span data-ttu-id="b7210-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="b7210-105">\<system.net></span></span>  
<span data-ttu-id="b7210-106">\<mailSettings ></span><span class="sxs-lookup"><span data-stu-id="b7210-106">\<mailSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7210-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b7210-107">Syntax</span></span>  
  
```xml  
<mailSettings>
  <smtp> … </smtp>  
</mailSettings>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b7210-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b7210-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b7210-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b7210-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b7210-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b7210-110">Attributes</span></span>  
 <span data-ttu-id="b7210-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="b7210-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b7210-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b7210-112">Child Elements</span></span>  
  
|<span data-ttu-id="b7210-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b7210-113">Attribute</span></span>|<span data-ttu-id="b7210-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b7210-114">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="b7210-115">\<SMTP > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="b7210-115">\<smtp> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|<span data-ttu-id="b7210-116">Basit Posta Aktarım Protokolü seçenekleri yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="b7210-116">Configures Simple Mail Transport Protocol options.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b7210-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b7210-117">Parent Elements</span></span>  
  
|<span data-ttu-id="b7210-118">**Öğesi**</span><span class="sxs-lookup"><span data-stu-id="b7210-118">**Element**</span></span>|<span data-ttu-id="b7210-119">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="b7210-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="b7210-120">\<system.Net > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="b7210-120">\<system.Net> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="b7210-121">.NET Framework ağa nasıl bağlanacağını belirtin ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="b7210-121">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b7210-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="b7210-122">Example</span></span>  
 <span data-ttu-id="b7210-123">Aşağıdaki örnek, varsayılan ağ kimlik bilgilerini kullanarak e-posta göndermek için uygun SMTP parametreleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="b7210-123">The following example specifies the appropriate SMTP parameters to send e-mail using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b7210-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b7210-124">See Also</span></span>  
 <xref:System.Net.Mail.SmtpClient>  
 [<span data-ttu-id="b7210-125">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="b7210-125">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
