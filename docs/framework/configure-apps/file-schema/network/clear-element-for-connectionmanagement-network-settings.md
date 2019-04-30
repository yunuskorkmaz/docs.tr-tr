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
ms.openlocfilehash: 733c70b0575de7e2635afaab58ad48591f035fc0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705252"
---
# <a name="clear-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="bef0d-102">\<Temizle > connectionManagement (ağ ayarları) için</span><span class="sxs-lookup"><span data-stu-id="bef0d-102">\<clear> Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="bef0d-103">Bağlantı yönetim listesini temizler.</span><span class="sxs-lookup"><span data-stu-id="bef0d-103">Clears the connection management list.</span></span>  
  
 <span data-ttu-id="bef0d-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="bef0d-104">\<configuration></span></span>  
<span data-ttu-id="bef0d-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="bef0d-105">\<system.net></span></span>  
<span data-ttu-id="bef0d-106">\<connectionManagement ></span><span class="sxs-lookup"><span data-stu-id="bef0d-106">\<connectionManagement></span></span>  
<span data-ttu-id="bef0d-107">\<Temizleme ></span><span class="sxs-lookup"><span data-stu-id="bef0d-107">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bef0d-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bef0d-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bef0d-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="bef0d-109">Attributes and Elements</span></span>  
 <span data-ttu-id="bef0d-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bef0d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bef0d-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bef0d-111">Attributes</span></span>  
 <span data-ttu-id="bef0d-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="bef0d-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="bef0d-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="bef0d-113">Child Elements</span></span>  
 <span data-ttu-id="bef0d-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="bef0d-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bef0d-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="bef0d-115">Parent Elements</span></span>  
  
|<span data-ttu-id="bef0d-116">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="bef0d-116">**Element**</span></span>|<span data-ttu-id="bef0d-117">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="bef0d-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="bef0d-118">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="bef0d-118">connectionManagement</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|<span data-ttu-id="bef0d-119">Bir ağ konak bağlantı maksimum sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="bef0d-119">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bef0d-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bef0d-120">Remarks</span></span>  
 <span data-ttu-id="bef0d-121">`clear` Öğesi bağlantı yönetimi listesindeki tüm girişleri siler.</span><span class="sxs-lookup"><span data-stu-id="bef0d-121">The `clear` element clears all entries from the connection management list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="bef0d-122">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="bef0d-122">Configuration Files</span></span>  
 <span data-ttu-id="bef0d-123">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bef0d-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bef0d-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="bef0d-124">Example</span></span>  
 <span data-ttu-id="bef0d-125">Aşağıdaki örnekte, bağlantı yönetimi listesini temizler ve ardından sunucu için yeni bağlantı yönetimi girişleri ekler `www.contoso.com` ve diğer tüm ağ konaklar.</span><span class="sxs-lookup"><span data-stu-id="bef0d-125">The following example clears the connection management list and then adds new connection management entries for the server `www.contoso.com` and all other network hosts.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bef0d-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bef0d-126">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="bef0d-127">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="bef0d-127">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
