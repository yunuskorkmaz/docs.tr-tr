---
title: <mailSettings> Öğesi (Ağ Ayarları)
description: <mailSettings>Ağ ayarları öğesi .NET Framework posta gönderme seçeneklerini yapılandırır.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#mailSettings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings
helpviewer_keywords:
- mailSettings element
- <mailSettings> element
ms.assetid: 54f0f153-17e5-4f49-afdc-deadb940c9c1
ms.openlocfilehash: ce7b8564e4ee5ea73d42259612c077420d36645b
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504569"
---
# <a name="mailsettings-element-network-settings"></a><span data-ttu-id="4fbb7-103">\<mailSettings> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="4fbb7-103">\<mailSettings> Element (Network Settings)</span></span>
<span data-ttu-id="4fbb7-104">Posta gönderme seçeneklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="4fbb7-104">Configures mail sending options.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<mailSettings>**

## <a name="syntax"></a><span data-ttu-id="4fbb7-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4fbb7-105">Syntax</span></span>  
  
```xml  
<mailSettings>
  <smtp>...</smtp>  
</mailSettings>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4fbb7-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4fbb7-106">Attributes and Elements</span></span>  
 <span data-ttu-id="4fbb7-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4fbb7-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4fbb7-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4fbb7-108">Attributes</span></span>  
 <span data-ttu-id="4fbb7-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="4fbb7-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4fbb7-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4fbb7-110">Child Elements</span></span>  
  
|<span data-ttu-id="4fbb7-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4fbb7-111">Attribute</span></span>|<span data-ttu-id="4fbb7-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4fbb7-112">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="4fbb7-113">\<smtp>Öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="4fbb7-113">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="4fbb7-114">Basit Posta Aktarım Protokolü seçeneklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="4fbb7-114">Configures Simple Mail Transport Protocol options.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4fbb7-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4fbb7-115">Parent Elements</span></span>  
  
|<span data-ttu-id="4fbb7-116">**Dosyalarında**</span><span class="sxs-lookup"><span data-stu-id="4fbb7-116">**Element**</span></span>|<span data-ttu-id="4fbb7-117">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="4fbb7-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="4fbb7-118">\<system.Net>Öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="4fbb7-118">\<system.Net> Element (Network Settings)</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="4fbb7-119">.NET Framework ağa nasıl bağlanacağını belirten ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="4fbb7-119">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="4fbb7-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="4fbb7-120">Example</span></span>  
 <span data-ttu-id="4fbb7-121">Aşağıdaki örnek, varsayılan ağ kimlik bilgilerini kullanarak e-posta göndermek için uygun SMTP parametrelerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4fbb7-121">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4fbb7-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4fbb7-122">See also</span></span>

- <xref:System.Net.Mail.SmtpClient>
- [<span data-ttu-id="4fbb7-123">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="4fbb7-123">Network Settings Schema</span></span>](index.md)
