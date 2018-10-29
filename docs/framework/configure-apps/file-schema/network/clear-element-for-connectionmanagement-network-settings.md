---
title: '&lt;Temizle&gt; connectionManagement (ağ ayarları) için'
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
ms.openlocfilehash: dba05128220b34bed34da4309a4994cbc4e1bd40
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50205106"
---
# <a name="ltcleargt-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="cb5a2-102">&lt;Temizle&gt; connectionManagement (ağ ayarları) için</span><span class="sxs-lookup"><span data-stu-id="cb5a2-102">&lt;clear&gt; Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="cb5a2-103">Bağlantı yönetim listesini temizler.</span><span class="sxs-lookup"><span data-stu-id="cb5a2-103">Clears the connection management list.</span></span>  
  
 <span data-ttu-id="cb5a2-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="cb5a2-104">\<configuration></span></span>  
<span data-ttu-id="cb5a2-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="cb5a2-105">\<system.net></span></span>  
<span data-ttu-id="cb5a2-106">\<connectionManagement ></span><span class="sxs-lookup"><span data-stu-id="cb5a2-106">\<connectionManagement></span></span>  
<span data-ttu-id="cb5a2-107">\<Temizleme ></span><span class="sxs-lookup"><span data-stu-id="cb5a2-107">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb5a2-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cb5a2-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cb5a2-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="cb5a2-109">Attributes and Elements</span></span>  
 <span data-ttu-id="cb5a2-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cb5a2-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cb5a2-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="cb5a2-111">Attributes</span></span>  
 <span data-ttu-id="cb5a2-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="cb5a2-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="cb5a2-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="cb5a2-113">Child Elements</span></span>  
 <span data-ttu-id="cb5a2-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="cb5a2-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cb5a2-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="cb5a2-115">Parent Elements</span></span>  
  
|<span data-ttu-id="cb5a2-116">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="cb5a2-116">**Element**</span></span>|<span data-ttu-id="cb5a2-117">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="cb5a2-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="cb5a2-118">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="cb5a2-118">connectionManagement</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|<span data-ttu-id="cb5a2-119">Bir ağ konak bağlantı maksimum sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="cb5a2-119">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cb5a2-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cb5a2-120">Remarks</span></span>  
 <span data-ttu-id="cb5a2-121">`clear` Öğesi bağlantı yönetimi listesindeki tüm girişleri siler.</span><span class="sxs-lookup"><span data-stu-id="cb5a2-121">The `clear` element clears all entries from the connection management list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="cb5a2-122">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="cb5a2-122">Configuration Files</span></span>  
 <span data-ttu-id="cb5a2-123">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cb5a2-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb5a2-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="cb5a2-124">Example</span></span>  
 <span data-ttu-id="cb5a2-125">Aşağıdaki örnekte, bağlantı yönetimi listesini temizler ve ardından sunucu için yeni bağlantı yönetimi girişleri ekler `www.contoso.com` ve diğer tüm ağ konaklar.</span><span class="sxs-lookup"><span data-stu-id="cb5a2-125">The following example clears the connection management list and then adds new connection management entries for the server `www.contoso.com` and all other network hosts.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cb5a2-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cb5a2-126">See Also</span></span>  
- <xref:System.Net.ServicePoint>  
- <xref:System.Net.ServicePointManager>  
- [<span data-ttu-id="cb5a2-127">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="cb5a2-127">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
