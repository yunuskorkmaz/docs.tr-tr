---
title: '&lt;connectionManagement&gt; öğesi (ağ ayarları)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement
- http://schemas.microsoft.com/.NetConfiguration/v2.0#connectionManagement
helpviewer_keywords:
- <connectionManagement> element
- connectionManagement element
ms.assetid: bedccaab-12a2-4511-8f67-e961f249aec6
ms.openlocfilehash: ff2f895ca50f0d16ee9e16406f92b087b03e391e
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/26/2018
ms.locfileid: "50049119"
---
# <a name="ltconnectionmanagementgt-element-network-settings"></a><span data-ttu-id="2965e-102">&lt;connectionManagement&gt; öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="2965e-102">&lt;connectionManagement&gt; Element (Network Settings)</span></span>
<span data-ttu-id="2965e-103">Bir ağ konak bağlantı maksimum sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="2965e-103">Specifies the maximum number of connections to a network host.</span></span>  
  
 <span data-ttu-id="2965e-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="2965e-104">\<configuration></span></span>  
<span data-ttu-id="2965e-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="2965e-105">\<system.net></span></span>  
<span data-ttu-id="2965e-106">\<connectionManagement ></span><span class="sxs-lookup"><span data-stu-id="2965e-106">\<connectionManagement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2965e-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2965e-107">Syntax</span></span>  
  
```xml  
<connectionManagement>   
</connectionManagement>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2965e-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2965e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="2965e-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2965e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2965e-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2965e-110">Attributes</span></span>  
 <span data-ttu-id="2965e-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="2965e-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2965e-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2965e-112">Child Elements</span></span>  
  
|<span data-ttu-id="2965e-113">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="2965e-113">**Element**</span></span>|<span data-ttu-id="2965e-114">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="2965e-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="2965e-115">add</span><span class="sxs-lookup"><span data-stu-id="2965e-115">add</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="2965e-116">Bir IP adresi veya DNS adı bağlantı yönetimi listesine ekler.</span><span class="sxs-lookup"><span data-stu-id="2965e-116">Adds an IP address or DNS name to the connection management list.</span></span>|  
|[<span data-ttu-id="2965e-117">Temizle</span><span class="sxs-lookup"><span data-stu-id="2965e-117">clear</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="2965e-118">Bağlantı yönetim listesini temizler.</span><span class="sxs-lookup"><span data-stu-id="2965e-118">Clears the connection management list.</span></span>|  
|[<span data-ttu-id="2965e-119">remove</span><span class="sxs-lookup"><span data-stu-id="2965e-119">remove</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="2965e-120">Bir IP adresi veya DNS adı bağlantı yönetimi listesinden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="2965e-120">Removes an IP address or DNS name from the connection management list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2965e-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2965e-121">Parent Elements</span></span>  
  
|<span data-ttu-id="2965e-122">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="2965e-122">**Element**</span></span>|<span data-ttu-id="2965e-123">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="2965e-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="2965e-124">System.NET</span><span class="sxs-lookup"><span data-stu-id="2965e-124">system.net</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="2965e-125">.NET Framework ağa nasıl bağlandığını belirten ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="2965e-125">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2965e-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2965e-126">Remarks</span></span>  
 <span data-ttu-id="2965e-127">`connectionManagement` Öğesi, sunucu veya sunucu grubu için en fazla bağlantı sayısını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2965e-127">The `connectionManagement` element defines the maximum number of connections to a server or group of servers.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="2965e-128">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="2965e-128">Configuration Files</span></span>  
 <span data-ttu-id="2965e-129">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2965e-129">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2965e-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="2965e-130">Example</span></span>  
 <span data-ttu-id="2965e-131">Aşağıdaki örnek bir uygulama sunucusu dört bağlantılarını kullanmak için yapılandırır `www.contoso.com` ve diğer tüm sunucular iki bağlantı.</span><span class="sxs-lookup"><span data-stu-id="2965e-131">The following example configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2965e-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2965e-132">See Also</span></span>  
 <xref:System.Net.ServicePoint>  
 <xref:System.Net.ServicePointManager>  
 [<span data-ttu-id="2965e-133">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="2965e-133">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
