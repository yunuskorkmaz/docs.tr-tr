---
title: <mailSettings> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#mailSettings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings
helpviewer_keywords:
- mailSettings element
- <mailSettings> element
ms.assetid: 54f0f153-17e5-4f49-afdc-deadb940c9c1
ms.openlocfilehash: 0e71284e914dac2d28448f3d8bd4bdc7a9f6b325
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55277621"
---
# <a name="mailsettings-element-network-settings"></a><span data-ttu-id="615d0-102">\<mailSettings > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="615d0-102">\<mailSettings> Element (Network Settings)</span></span>
<span data-ttu-id="615d0-103">Posta gönderme seçeneklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="615d0-103">Configures mail sending options.</span></span>  

<span data-ttu-id="615d0-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="615d0-104">\<configuration></span></span>  
<span data-ttu-id="615d0-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="615d0-105">\<system.net></span></span>  
<span data-ttu-id="615d0-106">\<mailSettings ></span><span class="sxs-lookup"><span data-stu-id="615d0-106">\<mailSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="615d0-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="615d0-107">Syntax</span></span>  
  
```xml  
<mailSettings>
  <smtp>...</smtp>  
</mailSettings>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="615d0-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="615d0-108">Attributes and Elements</span></span>  
 <span data-ttu-id="615d0-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="615d0-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="615d0-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="615d0-110">Attributes</span></span>  
 <span data-ttu-id="615d0-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="615d0-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="615d0-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="615d0-112">Child Elements</span></span>  
  
|<span data-ttu-id="615d0-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="615d0-113">Attribute</span></span>|<span data-ttu-id="615d0-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="615d0-114">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="615d0-115">\<SMTP > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="615d0-115">\<smtp> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|<span data-ttu-id="615d0-116">Basit Posta Aktarım Protokolü seçeneklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="615d0-116">Configures Simple Mail Transport Protocol options.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="615d0-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="615d0-117">Parent Elements</span></span>  
  
|<span data-ttu-id="615d0-118">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="615d0-118">**Element**</span></span>|<span data-ttu-id="615d0-119">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="615d0-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="615d0-120">\<system.Net > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="615d0-120">\<system.Net> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="615d0-121">.NET Framework ağa nasıl bağlandığını belirten ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="615d0-121">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="615d0-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="615d0-122">Example</span></span>  
 <span data-ttu-id="615d0-123">Aşağıdaki örnek, varsayılan ağ kimlik bilgilerini kullanarak e-posta göndermek için uygun SMTP parametrelerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="615d0-123">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="615d0-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="615d0-124">See also</span></span>
- <xref:System.Net.Mail.SmtpClient>
- [<span data-ttu-id="615d0-125">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="615d0-125">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
