---
title: "&lt;connectionManagement&gt; öğesi (ağ ayarları)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement
- http://schemas.microsoft.com/.NetConfiguration/v2.0#connectionManagement
helpviewer_keywords:
- <connectionManagement> element
- connectionManagement element
ms.assetid: bedccaab-12a2-4511-8f67-e961f249aec6
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 700d06d22c76762c80ea877006a8ac3789052b14
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltconnectionmanagementgt-element-network-settings"></a><span data-ttu-id="8235f-102">&lt;connectionManagement&gt; öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="8235f-102">&lt;connectionManagement&gt; Element (Network Settings)</span></span>
<span data-ttu-id="8235f-103">Bir ağ ana bilgisayar için bağlantı sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="8235f-103">Specifies the maximum number of connections to a network host.</span></span>  
  
 <span data-ttu-id="8235f-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="8235f-104">\<configuration></span></span>  
<span data-ttu-id="8235f-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="8235f-105">\<system.net></span></span>  
<span data-ttu-id="8235f-106">\<connectionManagement ></span><span class="sxs-lookup"><span data-stu-id="8235f-106">\<connectionManagement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8235f-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8235f-107">Syntax</span></span>  
  
```xml  
<connectionManagement>   
</connectionManagement>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8235f-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8235f-108">Attributes and Elements</span></span>  
 <span data-ttu-id="8235f-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8235f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8235f-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8235f-110">Attributes</span></span>  
 <span data-ttu-id="8235f-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="8235f-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8235f-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8235f-112">Child Elements</span></span>  
  
|<span data-ttu-id="8235f-113">**Öğesi**</span><span class="sxs-lookup"><span data-stu-id="8235f-113">**Element**</span></span>|<span data-ttu-id="8235f-114">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="8235f-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="8235f-115">add</span><span class="sxs-lookup"><span data-stu-id="8235f-115">add</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="8235f-116">Bir IP adresi veya DNS adı bağlantısı Yönetim listesine ekler.</span><span class="sxs-lookup"><span data-stu-id="8235f-116">Adds an IP address or DNS name to the connection management list.</span></span>|  
|[<span data-ttu-id="8235f-117">Temizle</span><span class="sxs-lookup"><span data-stu-id="8235f-117">clear</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="8235f-118">Bağlantı Yönetimi listesini temizler.</span><span class="sxs-lookup"><span data-stu-id="8235f-118">Clears the connection management list.</span></span>|  
|[<span data-ttu-id="8235f-119">remove</span><span class="sxs-lookup"><span data-stu-id="8235f-119">remove</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="8235f-120">Bir IP adresi veya DNS adı bağlantı yönetimi listesinden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="8235f-120">Removes an IP address or DNS name from the connection management list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8235f-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8235f-121">Parent Elements</span></span>  
  
|<span data-ttu-id="8235f-122">**Öğesi**</span><span class="sxs-lookup"><span data-stu-id="8235f-122">**Element**</span></span>|<span data-ttu-id="8235f-123">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="8235f-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="8235f-124">System.NET</span><span class="sxs-lookup"><span data-stu-id="8235f-124">system.net</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="8235f-125">.NET Framework ağa nasıl bağlanacağını belirtin ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="8235f-125">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8235f-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8235f-126">Remarks</span></span>  
 <span data-ttu-id="8235f-127">`connectionManagement` Öğesi, sunucu veya sunucu grubu için en fazla bağlantı sayısını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8235f-127">The `connectionManagement` element defines the maximum number of connections to a server or group of servers.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="8235f-128">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="8235f-128">Configuration Files</span></span>  
 <span data-ttu-id="8235f-129">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8235f-129">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8235f-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="8235f-130">Example</span></span>  
 <span data-ttu-id="8235f-131">Aşağıdaki örnek bir uygulama sunucusu www.contoso.com için dört bağlantıları ve diğer tüm sunucular iki bağlantıları kullanmak için yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="8235f-131">The following example configures an application to use four connections to the server www.contoso.com and two connections to all other servers.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <add address = "http://www.contoso.com" maxconnection = "4" />  
      <add address = "*" maxconnection = "2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8235f-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8235f-132">See Also</span></span>  
 <xref:System.Net.ServicePoint>  
 <xref:System.Net.ServicePointManager>  
 [<span data-ttu-id="8235f-133">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="8235f-133">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
