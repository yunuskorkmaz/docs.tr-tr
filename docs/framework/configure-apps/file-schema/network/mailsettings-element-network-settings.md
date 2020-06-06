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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74089227"
---
# <a name="mailsettings-element-network-settings"></a><span data-ttu-id="e5dbc-102">\<mailSettings> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="e5dbc-102">\<mailSettings> Element (Network Settings)</span></span>
<span data-ttu-id="e5dbc-103">Posta gönderme seçeneklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="e5dbc-103">Configures mail sending options.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<mailSettings>**

## <a name="syntax"></a><span data-ttu-id="e5dbc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e5dbc-104">Syntax</span></span>  
  
```xml  
<mailSettings>
  <smtp>...</smtp>  
</mailSettings>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e5dbc-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e5dbc-105">Attributes and Elements</span></span>  
 <span data-ttu-id="e5dbc-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e5dbc-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e5dbc-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e5dbc-107">Attributes</span></span>  
 <span data-ttu-id="e5dbc-108">Yok.</span><span class="sxs-lookup"><span data-stu-id="e5dbc-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e5dbc-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e5dbc-109">Child Elements</span></span>  
  
|<span data-ttu-id="e5dbc-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e5dbc-110">Attribute</span></span>|<span data-ttu-id="e5dbc-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e5dbc-111">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="e5dbc-112">\<smtp>Öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="e5dbc-112">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="e5dbc-113">Basit Posta Aktarım Protokolü seçeneklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="e5dbc-113">Configures Simple Mail Transport Protocol options.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e5dbc-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e5dbc-114">Parent Elements</span></span>  
  
|<span data-ttu-id="e5dbc-115">**Dosyalarında**</span><span class="sxs-lookup"><span data-stu-id="e5dbc-115">**Element**</span></span>|<span data-ttu-id="e5dbc-116">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="e5dbc-116">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="e5dbc-117">\<system.Net>Öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="e5dbc-117">\<system.Net> Element (Network Settings)</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="e5dbc-118">.NET Framework ağa nasıl bağlanacağını belirten ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="e5dbc-118">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e5dbc-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="e5dbc-119">Example</span></span>  
 <span data-ttu-id="e5dbc-120">Aşağıdaki örnek, varsayılan ağ kimlik bilgilerini kullanarak e-posta göndermek için uygun SMTP parametrelerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e5dbc-120">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e5dbc-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e5dbc-121">See also</span></span>

- <xref:System.Net.Mail.SmtpClient>
- [<span data-ttu-id="e5dbc-122">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="e5dbc-122">Network Settings Schema</span></span>](index.md)
