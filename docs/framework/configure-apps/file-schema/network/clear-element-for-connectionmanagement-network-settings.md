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
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088481"
---
# <a name="clear-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="e43a0-102">connectionManagement için \<Clear > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="e43a0-102">\<clear> Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="e43a0-103">Bağlantı yönetimi listesini temizler.</span><span class="sxs-lookup"><span data-stu-id="e43a0-103">Clears the connection management list.</span></span>  

<span data-ttu-id="e43a0-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="e43a0-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e43a0-105">[**System. net >\<** ](system-net-element-network-settings.md) &nbsp;&nbsp;</span><span class="sxs-lookup"><span data-stu-id="e43a0-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="e43a0-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<connectionManagement >** ](connectionmanagement-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="e43a0-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<connectionManagement>**](connectionmanagement-element-network-settings.md)</span></span>\
<span data-ttu-id="e43a0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<clear >**</span><span class="sxs-lookup"><span data-stu-id="e43a0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="e43a0-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e43a0-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e43a0-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e43a0-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e43a0-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e43a0-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e43a0-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e43a0-111">Attributes</span></span>  
 <span data-ttu-id="e43a0-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="e43a0-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e43a0-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e43a0-113">Child Elements</span></span>  
 <span data-ttu-id="e43a0-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="e43a0-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e43a0-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e43a0-115">Parent Elements</span></span>  
  
|<span data-ttu-id="e43a0-116">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="e43a0-116">**Element**</span></span>|<span data-ttu-id="e43a0-117">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="e43a0-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="e43a0-118">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="e43a0-118">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="e43a0-119">Bir ağ konağına en fazla bağlantı sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e43a0-119">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e43a0-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e43a0-120">Remarks</span></span>  
 <span data-ttu-id="e43a0-121">`clear` öğesi, bağlantı yönetimi listesinden tüm girdileri temizler.</span><span class="sxs-lookup"><span data-stu-id="e43a0-121">The `clear` element clears all entries from the connection management list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="e43a0-122">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="e43a0-122">Configuration Files</span></span>  
 <span data-ttu-id="e43a0-123">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e43a0-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e43a0-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="e43a0-124">Example</span></span>  
 <span data-ttu-id="e43a0-125">Aşağıdaki örnek, bağlantı yönetimi listesini temizler ve sunucu `www.contoso.com` ve diğer tüm ağ konakları için yeni bağlantı yönetimi girişleri ekler.</span><span class="sxs-lookup"><span data-stu-id="e43a0-125">The following example clears the connection management list and then adds new connection management entries for the server `www.contoso.com` and all other network hosts.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e43a0-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e43a0-126">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="e43a0-127">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="e43a0-127">Network Settings Schema</span></span>](index.md)
