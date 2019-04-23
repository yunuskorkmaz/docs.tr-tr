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
ms.openlocfilehash: 54fb68ab0bf8aa2665d70391350c626131ccb4bc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59180637"
---
# <a name="mailsettings-element-network-settings"></a><span data-ttu-id="3980c-102">\<mailSettings > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="3980c-102">\<mailSettings> Element (Network Settings)</span></span>
<span data-ttu-id="3980c-103">Posta gönderme seçeneklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="3980c-103">Configures mail sending options.</span></span>  

<span data-ttu-id="3980c-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="3980c-104">\<configuration></span></span>  
<span data-ttu-id="3980c-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="3980c-105">\<system.net></span></span>  
<span data-ttu-id="3980c-106">\<mailSettings ></span><span class="sxs-lookup"><span data-stu-id="3980c-106">\<mailSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3980c-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3980c-107">Syntax</span></span>  
  
```xml  
<mailSettings>
  <smtp>...</smtp>  
</mailSettings>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3980c-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3980c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="3980c-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3980c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3980c-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3980c-110">Attributes</span></span>  
 <span data-ttu-id="3980c-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="3980c-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3980c-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3980c-112">Child Elements</span></span>  
  
|<span data-ttu-id="3980c-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3980c-113">Attribute</span></span>|<span data-ttu-id="3980c-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3980c-114">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="3980c-115">\<SMTP > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="3980c-115">\<smtp> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|<span data-ttu-id="3980c-116">Basit Posta Aktarım Protokolü seçeneklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="3980c-116">Configures Simple Mail Transport Protocol options.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3980c-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3980c-117">Parent Elements</span></span>  
  
|<span data-ttu-id="3980c-118">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="3980c-118">**Element**</span></span>|<span data-ttu-id="3980c-119">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="3980c-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="3980c-120">\<system.Net > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="3980c-120">\<system.Net> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="3980c-121">.NET Framework ağa nasıl bağlandığını belirten ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="3980c-121">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="3980c-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="3980c-122">Example</span></span>  
 <span data-ttu-id="3980c-123">Aşağıdaki örnek, varsayılan ağ kimlik bilgilerini kullanarak e-posta göndermek için uygun SMTP parametrelerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3980c-123">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3980c-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3980c-124">See also</span></span>

- <xref:System.Net.Mail.SmtpClient>
- [<span data-ttu-id="3980c-125">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="3980c-125">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
