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
ms.openlocfilehash: a42b10574a1f44d310f86fe3fa99490f2f1981c6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltmailsettingsgt-element-network-settings"></a><span data-ttu-id="efd7a-102">&lt;mailSettings&gt; öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="efd7a-102">&lt;mailSettings&gt; Element (Network Settings)</span></span>
<span data-ttu-id="efd7a-103">Posta gönderme seçenekleri yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="efd7a-103">Configures mail sending options.</span></span>  

<span data-ttu-id="efd7a-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="efd7a-104">\<configuration></span></span>  
<span data-ttu-id="efd7a-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="efd7a-105">\<system.net></span></span>  
<span data-ttu-id="efd7a-106">\<mailSettings ></span><span class="sxs-lookup"><span data-stu-id="efd7a-106">\<mailSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efd7a-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="efd7a-107">Syntax</span></span>  
  
```xml  
<mailSettings>
  <smtp> … </smtp>  
</mailSettings>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="efd7a-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="efd7a-108">Attributes and Elements</span></span>  
 <span data-ttu-id="efd7a-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="efd7a-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="efd7a-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="efd7a-110">Attributes</span></span>  
 <span data-ttu-id="efd7a-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="efd7a-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="efd7a-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="efd7a-112">Child Elements</span></span>  
  
|<span data-ttu-id="efd7a-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="efd7a-113">Attribute</span></span>|<span data-ttu-id="efd7a-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="efd7a-114">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="efd7a-115">\<SMTP > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="efd7a-115">\<smtp> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|<span data-ttu-id="efd7a-116">Basit Posta Aktarım Protokolü seçenekleri yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="efd7a-116">Configures Simple Mail Transport Protocol options.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="efd7a-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="efd7a-117">Parent Elements</span></span>  
  
|<span data-ttu-id="efd7a-118">**Öğesi**</span><span class="sxs-lookup"><span data-stu-id="efd7a-118">**Element**</span></span>|<span data-ttu-id="efd7a-119">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="efd7a-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="efd7a-120">\<system.Net > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="efd7a-120">\<system.Net> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="efd7a-121">.NET Framework ağa nasıl bağlanacağını belirtin ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="efd7a-121">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="efd7a-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="efd7a-122">Example</span></span>  
 <span data-ttu-id="efd7a-123">Aşağıdaki örnek, varsayılan ağ kimlik bilgilerini kullanarak e-posta göndermek için uygun SMTP parametreleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="efd7a-123">The following example specifies the appropriate SMTP parameters to send e-mail using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="efd7a-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="efd7a-124">See Also</span></span>  
 <xref:System.Net.Mail.SmtpClient>  
 [<span data-ttu-id="efd7a-125">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="efd7a-125">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
