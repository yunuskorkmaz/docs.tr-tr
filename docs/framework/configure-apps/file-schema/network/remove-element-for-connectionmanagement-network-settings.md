---
title: "&lt;kaldırma&gt; öğesi connectionManagement (ağ ayarları) için"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- connectionManagement, remove element
- <remove> element, connectionManagement
- <connectionManagement>, remove element
- remove element, connectionManagement
ms.assetid: 94b81775-5a22-4975-8c47-8620c40c3f35
caps.latest.revision: "12"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 947150ce0ff9a5ec5fa87fef8c2e24f3ebf6b4cb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltremovegt-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="bbf30-102">&lt;kaldırma&gt; öğesi connectionManagement (ağ ayarları) için</span><span class="sxs-lookup"><span data-stu-id="bbf30-102">&lt;remove&gt; Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="bbf30-103">Bir IP adresi veya DNS adı bağlantı yönetimi listesinden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="bbf30-103">Removes an IP address or DNS name from the connection management list.</span></span>  
  
 <span data-ttu-id="bbf30-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="bbf30-104">\<configuration></span></span>  
<span data-ttu-id="bbf30-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="bbf30-105">\<system.net></span></span>  
<span data-ttu-id="bbf30-106">\<connectionManagement ></span><span class="sxs-lookup"><span data-stu-id="bbf30-106">\<connectionManagement></span></span>  
<span data-ttu-id="bbf30-107">\<kaldırma ></span><span class="sxs-lookup"><span data-stu-id="bbf30-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbf30-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bbf30-108">Syntax</span></span>  
  
```xml  
<remove   
  address="server name or IP address"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bbf30-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="bbf30-109">Attributes and Elements</span></span>  
 <span data-ttu-id="bbf30-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bbf30-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bbf30-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bbf30-111">Attributes</span></span>  
  
|<span data-ttu-id="bbf30-112">**Özniteliği**</span><span class="sxs-lookup"><span data-stu-id="bbf30-112">**Attribute**</span></span>|<span data-ttu-id="bbf30-113">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="bbf30-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`address`|<span data-ttu-id="bbf30-114">Bir IP adresi veya DNS adı.</span><span class="sxs-lookup"><span data-stu-id="bbf30-114">An IP address or DNS name.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bbf30-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="bbf30-115">Child Elements</span></span>  
 <span data-ttu-id="bbf30-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="bbf30-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bbf30-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="bbf30-117">Parent Elements</span></span>  
  
|<span data-ttu-id="bbf30-118">**Öğesi**</span><span class="sxs-lookup"><span data-stu-id="bbf30-118">**Element**</span></span>|<span data-ttu-id="bbf30-119">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="bbf30-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="bbf30-120">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="bbf30-120">connectionManagement</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|<span data-ttu-id="bbf30-121">Bir ağ ana bilgisayar için bağlantı sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="bbf30-121">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bbf30-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bbf30-122">Remarks</span></span>  
 <span data-ttu-id="bbf30-123">`remove` Öğesi belirtilen sunucu bağlantısı yönetim liste girdisini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="bbf30-123">The `remove` element removes the connection management list entry for the specified server.</span></span>  
  
 <span data-ttu-id="bbf30-124">Değeri `address` özniteliği geçerli bir IP adresi veya ana bilgisayar adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bbf30-124">The value of the `address` attribute should be a valid IP address or host name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="bbf30-125">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="bbf30-125">Configuration Files</span></span>  
 <span data-ttu-id="bbf30-126">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bbf30-126">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bbf30-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="bbf30-127">Example</span></span>  
 <span data-ttu-id="bbf30-128">Aşağıdaki örnekte tüm bağlantı yönetimi Liste girişlerini sunucu www.adventure-works.com için kaldırır ve sunucu www.contoso.com için dört bağlantıları ve diğer tüm sunucular iki bağlantıları kullanmak için bir uygulamayı yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="bbf30-128">The following example removes any connection management list entries for the server www.adventure-works.com and then configures an application to use four connections to the server www.contoso.com and two connections to all other servers.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <remove address="http://www.adventure-works.com" />  
      <add address="http://www.contoso.com" maxconnection="4" />  
      <add address="*" maxconnection="2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bbf30-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bbf30-129">See Also</span></span>  
 <xref:System.Net.ServicePoint>  
 <xref:System.Net.ServicePointManager>  
 [<span data-ttu-id="bbf30-130">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="bbf30-130">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
