---
title: "&lt;Clear&gt; öğesi connectionManagement (ağ ayarları) için"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- <clear> element, connectionManagement
- connectionManagement, clear element
- clear element, connectionManagement
- <connectionManagement>, clear element
ms.assetid: fb259282-84c4-4dc4-a226-78d904a6edc3
caps.latest.revision: "13"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 0fe32b20b9b0a0217ecef36f65ae1ee4084e92ad
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltcleargt-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="8ee36-102">&lt;Clear&gt; öğesi connectionManagement (ağ ayarları) için</span><span class="sxs-lookup"><span data-stu-id="8ee36-102">&lt;clear&gt; Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="8ee36-103">Bağlantı Yönetimi listesini temizler.</span><span class="sxs-lookup"><span data-stu-id="8ee36-103">Clears the connection management list.</span></span>  
  
 <span data-ttu-id="8ee36-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="8ee36-104">\<configuration></span></span>  
<span data-ttu-id="8ee36-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="8ee36-105">\<system.net></span></span>  
<span data-ttu-id="8ee36-106">\<connectionManagement ></span><span class="sxs-lookup"><span data-stu-id="8ee36-106">\<connectionManagement></span></span>  
<span data-ttu-id="8ee36-107">\<Clear ></span><span class="sxs-lookup"><span data-stu-id="8ee36-107">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ee36-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8ee36-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8ee36-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8ee36-109">Attributes and Elements</span></span>  
 <span data-ttu-id="8ee36-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8ee36-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8ee36-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8ee36-111">Attributes</span></span>  
 <span data-ttu-id="8ee36-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="8ee36-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8ee36-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8ee36-113">Child Elements</span></span>  
 <span data-ttu-id="8ee36-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="8ee36-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8ee36-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8ee36-115">Parent Elements</span></span>  
  
|<span data-ttu-id="8ee36-116">**Öğesi**</span><span class="sxs-lookup"><span data-stu-id="8ee36-116">**Element**</span></span>|<span data-ttu-id="8ee36-117">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="8ee36-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="8ee36-118">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="8ee36-118">connectionManagement</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|<span data-ttu-id="8ee36-119">Bir ağ ana bilgisayar için bağlantı sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="8ee36-119">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8ee36-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8ee36-120">Remarks</span></span>  
 <span data-ttu-id="8ee36-121">`clear` Öğesi bağlantı yönetimi listesindeki tüm girişleri siler.</span><span class="sxs-lookup"><span data-stu-id="8ee36-121">The `clear` element clears all entries from the connection management list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="8ee36-122">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="8ee36-122">Configuration Files</span></span>  
 <span data-ttu-id="8ee36-123">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8ee36-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ee36-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="8ee36-124">Example</span></span>  
 <span data-ttu-id="8ee36-125">Aşağıdaki örnek bağlantı yönetim listesini temizler ve ardından sunucu www.contoso.com ve diğer tüm ağ konaklar için yeni bağlantı yönetimi girişleri ekler.</span><span class="sxs-lookup"><span data-stu-id="8ee36-125">The following example clears the connection management list and then adds new connection management entries for the server www.contoso.com and all other network hosts.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8ee36-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8ee36-126">See Also</span></span>  
 <xref:System.Net.ServicePoint>  
 <xref:System.Net.ServicePointManager>  
 [<span data-ttu-id="8ee36-127">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="8ee36-127">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
