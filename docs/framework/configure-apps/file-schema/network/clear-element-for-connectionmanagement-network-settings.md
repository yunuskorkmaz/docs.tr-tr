---
title: connectionManagement için <clear> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- <clear> element, connectionManagement
- connectionManagement, clear element
- clear element, connectionManagement
- <connectionManagement>, clear element
ms.assetid: fb259282-84c4-4dc4-a226-78d904a6edc3
ms.openlocfilehash: a76df48a9de084e1121a5e96b22edf7aa3acba23
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74088481"
---
# <a name="clear-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="55166-102">connectionManagement için \<clear> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="55166-102">\<clear> Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="55166-103">Bağlantı yönetimi listesini temizler.</span><span class="sxs-lookup"><span data-stu-id="55166-103">Clears the connection management list.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<connectionManagement>**](connectionmanagement-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="55166-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="55166-104">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="55166-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="55166-105">Attributes and Elements</span></span>  
 <span data-ttu-id="55166-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="55166-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="55166-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="55166-107">Attributes</span></span>  
 <span data-ttu-id="55166-108">Yok.</span><span class="sxs-lookup"><span data-stu-id="55166-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="55166-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="55166-109">Child Elements</span></span>  
 <span data-ttu-id="55166-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="55166-110">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="55166-111">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="55166-111">Parent Elements</span></span>  
  
|<span data-ttu-id="55166-112">**Dosyalarında**</span><span class="sxs-lookup"><span data-stu-id="55166-112">**Element**</span></span>|<span data-ttu-id="55166-113">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="55166-113">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="55166-114">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="55166-114">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="55166-115">Bir ağ konağına en fazla bağlantı sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="55166-115">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="55166-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="55166-116">Remarks</span></span>  
 <span data-ttu-id="55166-117">`clear`Öğesi bağlantı yönetimi listesinden tüm girdileri temizler.</span><span class="sxs-lookup"><span data-stu-id="55166-117">The `clear` element clears all entries from the connection management list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="55166-118">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="55166-118">Configuration Files</span></span>  
 <span data-ttu-id="55166-119">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="55166-119">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="55166-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="55166-120">Example</span></span>  
 <span data-ttu-id="55166-121">Aşağıdaki örnek bağlantı yönetimi listesini temizler ve ardından sunucu `www.contoso.com` ve diğer tüm ağ konakları için yeni bağlantı yönetimi girişleri ekler.</span><span class="sxs-lookup"><span data-stu-id="55166-121">The following example clears the connection management list and then adds new connection management entries for the server `www.contoso.com` and all other network hosts.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <clear/>  
      <add address = "http://www.contoso.com" maxconnection = "4" />  
      <add address = "*" maxconnection = "2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="55166-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="55166-122">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="55166-123">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="55166-123">Network Settings Schema</span></span>](index.md)
