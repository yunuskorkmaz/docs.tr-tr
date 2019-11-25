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
ms.openlocfilehash: 4e8bf23ce39edadf80f019315c690b597b3d7361
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089227"
---
# <a name="mailsettings-element-network-settings"></a><span data-ttu-id="440db-102">\<mailSettings > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="440db-102">\<mailSettings> Element (Network Settings)</span></span>
<span data-ttu-id="440db-103">Posta gönderme seçeneklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="440db-103">Configures mail sending options.</span></span>  

<span data-ttu-id="440db-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="440db-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="440db-105">[**System. net >\<** ](system-net-element-network-settings.md) &nbsp;&nbsp;</span><span class="sxs-lookup"><span data-stu-id="440db-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="440db-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<mailSettings >**</span><span class="sxs-lookup"><span data-stu-id="440db-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<mailSettings>**</span></span>

## <a name="syntax"></a><span data-ttu-id="440db-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="440db-107">Syntax</span></span>  
  
```xml  
<mailSettings>
  <smtp>...</smtp>  
</mailSettings>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="440db-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="440db-108">Attributes and Elements</span></span>  
 <span data-ttu-id="440db-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="440db-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="440db-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="440db-110">Attributes</span></span>  
 <span data-ttu-id="440db-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="440db-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="440db-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="440db-112">Child Elements</span></span>  
  
|<span data-ttu-id="440db-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="440db-113">Attribute</span></span>|<span data-ttu-id="440db-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="440db-114">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="440db-115">\<SMTP > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="440db-115">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="440db-116">Basit Posta Aktarım Protokolü seçeneklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="440db-116">Configures Simple Mail Transport Protocol options.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="440db-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="440db-117">Parent Elements</span></span>  
  
|<span data-ttu-id="440db-118">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="440db-118">**Element**</span></span>|<span data-ttu-id="440db-119">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="440db-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="440db-120">\<sistem .net > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="440db-120">\<system.Net> Element (Network Settings)</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="440db-121">.NET Framework ağa nasıl bağlanacağını belirten ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="440db-121">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="440db-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="440db-122">Example</span></span>  
 <span data-ttu-id="440db-123">Aşağıdaki örnek, varsayılan ağ kimlik bilgilerini kullanarak e-posta göndermek için uygun SMTP parametrelerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="440db-123">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="440db-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="440db-124">See also</span></span>

- <xref:System.Net.Mail.SmtpClient>
- [<span data-ttu-id="440db-125">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="440db-125">Network Settings Schema</span></span>](index.md)
