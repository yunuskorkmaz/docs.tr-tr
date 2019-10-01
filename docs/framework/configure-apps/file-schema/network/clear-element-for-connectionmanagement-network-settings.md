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
ms.openlocfilehash: 17b380b12977423669fd413132d69a3082daca41
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698365"
---
# <a name="clear-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="46bfc-102">connectionManagement için \<clear > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="46bfc-102">\<clear> Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="46bfc-103">Bağlantı yönetimi listesini temizler.</span><span class="sxs-lookup"><span data-stu-id="46bfc-103">Clears the connection management list.</span></span>  
  
[<span data-ttu-id="46bfc-104"> **\<Yapılandırma >** </span><span class="sxs-lookup"><span data-stu-id="46bfc-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="46bfc-105">&nbsp; @ no__t-1[ **@no__t -4system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="46bfc-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="46bfc-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<connectionManagement >** ](connectionmanagement-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="46bfc-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<connectionManagement>**](connectionmanagement-element-network-settings.md)</span></span>  
<span data-ttu-id="46bfc-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<clear >**</span><span class="sxs-lookup"><span data-stu-id="46bfc-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46bfc-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="46bfc-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="46bfc-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="46bfc-109">Attributes and Elements</span></span>  
 <span data-ttu-id="46bfc-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="46bfc-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="46bfc-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="46bfc-111">Attributes</span></span>  
 <span data-ttu-id="46bfc-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="46bfc-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="46bfc-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="46bfc-113">Child Elements</span></span>  
 <span data-ttu-id="46bfc-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="46bfc-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="46bfc-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="46bfc-115">Parent Elements</span></span>  
  
|<span data-ttu-id="46bfc-116">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="46bfc-116">**Element**</span></span>|<span data-ttu-id="46bfc-117">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="46bfc-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="46bfc-118">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="46bfc-118">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="46bfc-119">Bir ağ konağına en fazla bağlantı sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="46bfc-119">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="46bfc-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="46bfc-120">Remarks</span></span>  
 <span data-ttu-id="46bfc-121">@No__t-0 öğesi bağlantı yönetimi listesinden tüm girdileri temizler.</span><span class="sxs-lookup"><span data-stu-id="46bfc-121">The `clear` element clears all entries from the connection management list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="46bfc-122">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="46bfc-122">Configuration Files</span></span>  
 <span data-ttu-id="46bfc-123">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="46bfc-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="46bfc-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="46bfc-124">Example</span></span>  
 <span data-ttu-id="46bfc-125">Aşağıdaki örnek, bağlantı yönetimi listesini temizler ve sunucu için yeni bağlantı yönetim girdilerini ekler `www.contoso.com` ve diğer tüm ağ Konakları.</span><span class="sxs-lookup"><span data-stu-id="46bfc-125">The following example clears the connection management list and then adds new connection management entries for the server `www.contoso.com` and all other network hosts.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="46bfc-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="46bfc-126">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="46bfc-127">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="46bfc-127">Network Settings Schema</span></span>](index.md)
