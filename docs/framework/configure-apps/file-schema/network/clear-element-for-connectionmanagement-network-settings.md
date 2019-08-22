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
ms.openlocfilehash: 86a7a0ab402c8c40ec3b824402a1dba984412b68
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659441"
---
# <a name="clear-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="5bc28-102">\<connectionManagement için > öğesini temizle (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="5bc28-102">\<clear> Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="5bc28-103">Bağlantı yönetimi listesini temizler.</span><span class="sxs-lookup"><span data-stu-id="5bc28-103">Clears the connection management list.</span></span>  
  
 <span data-ttu-id="5bc28-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="5bc28-104">\<configuration></span></span>  
<span data-ttu-id="5bc28-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="5bc28-105">\<system.net></span></span>  
<span data-ttu-id="5bc28-106">\<connectionManagement ></span><span class="sxs-lookup"><span data-stu-id="5bc28-106">\<connectionManagement></span></span>  
<span data-ttu-id="5bc28-107">\<> Temizle</span><span class="sxs-lookup"><span data-stu-id="5bc28-107">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bc28-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5bc28-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5bc28-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5bc28-109">Attributes and Elements</span></span>  
 <span data-ttu-id="5bc28-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5bc28-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5bc28-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5bc28-111">Attributes</span></span>  
 <span data-ttu-id="5bc28-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="5bc28-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5bc28-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5bc28-113">Child Elements</span></span>  
 <span data-ttu-id="5bc28-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="5bc28-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5bc28-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5bc28-115">Parent Elements</span></span>  
  
|<span data-ttu-id="5bc28-116">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="5bc28-116">**Element**</span></span>|<span data-ttu-id="5bc28-117">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="5bc28-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="5bc28-118">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="5bc28-118">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="5bc28-119">Bir ağ konağına en fazla bağlantı sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5bc28-119">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5bc28-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5bc28-120">Remarks</span></span>  
 <span data-ttu-id="5bc28-121">`clear` Öğesi bağlantı yönetimi listesinden tüm girdileri temizler.</span><span class="sxs-lookup"><span data-stu-id="5bc28-121">The `clear` element clears all entries from the connection management list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="5bc28-122">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="5bc28-122">Configuration Files</span></span>  
 <span data-ttu-id="5bc28-123">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5bc28-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5bc28-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="5bc28-124">Example</span></span>  
 <span data-ttu-id="5bc28-125">Aşağıdaki örnek bağlantı yönetimi listesini temizler ve ardından sunucu `www.contoso.com` ve diğer tüm ağ konakları için yeni bağlantı yönetimi girişleri ekler.</span><span class="sxs-lookup"><span data-stu-id="5bc28-125">The following example clears the connection management list and then adds new connection management entries for the server `www.contoso.com` and all other network hosts.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5bc28-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5bc28-126">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="5bc28-127">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="5bc28-127">Network Settings Schema</span></span>](index.md)
