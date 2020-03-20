---
title: <connectionManagement> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement
- http://schemas.microsoft.com/.NetConfiguration/v2.0#connectionManagement
helpviewer_keywords:
- <connectionManagement> element
- connectionManagement element
ms.assetid: bedccaab-12a2-4511-8f67-e961f249aec6
ms.openlocfilehash: 9f1e382bbbaad2cb95e2c33bbbdfb4c505378c9e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154900"
---
# <a name="connectionmanagement-element-network-settings"></a><span data-ttu-id="a3a09-102">\<bağlantıYönetim> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="a3a09-102">\<connectionManagement> Element (Network Settings)</span></span>
<span data-ttu-id="a3a09-103">Bir ağ ana bilgisayarına en fazla bağlantı sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a3a09-103">Specifies the maximum number of connections to a network host.</span></span>  

<span data-ttu-id="a3a09-104">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a3a09-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a3a09-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="a3a09-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="a3a09-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<bağlantıYönetim>**</span><span class="sxs-lookup"><span data-stu-id="a3a09-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<connectionManagement>**</span></span>

## <a name="syntax"></a><span data-ttu-id="a3a09-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a3a09-107">Syntax</span></span>  
  
```xml  
<connectionManagement>
</connectionManagement>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a3a09-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a3a09-108">Attributes and Elements</span></span>  
 <span data-ttu-id="a3a09-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a3a09-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a3a09-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a3a09-110">Attributes</span></span>  
 <span data-ttu-id="a3a09-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="a3a09-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a3a09-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a3a09-112">Child Elements</span></span>  
  
|<span data-ttu-id="a3a09-113">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="a3a09-113">**Element**</span></span>|<span data-ttu-id="a3a09-114">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="a3a09-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="a3a09-115">Ekle</span><span class="sxs-lookup"><span data-stu-id="a3a09-115">add</span></span>](add-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="a3a09-116">Bağlantı yönetim listesine bir IP adresi veya DNS adı ekler.</span><span class="sxs-lookup"><span data-stu-id="a3a09-116">Adds an IP address or DNS name to the connection management list.</span></span>|  
|[<span data-ttu-id="a3a09-117">Temizleyin</span><span class="sxs-lookup"><span data-stu-id="a3a09-117">clear</span></span>](clear-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="a3a09-118">Bağlantı yönetimi listesini temizler.</span><span class="sxs-lookup"><span data-stu-id="a3a09-118">Clears the connection management list.</span></span>|  
|[<span data-ttu-id="a3a09-119">Kaldırmak</span><span class="sxs-lookup"><span data-stu-id="a3a09-119">remove</span></span>](remove-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="a3a09-120">Bağlantı yönetim listesinden bir IP adresi veya DNS adını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="a3a09-120">Removes an IP address or DNS name from the connection management list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a3a09-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a3a09-121">Parent Elements</span></span>  
  
|<span data-ttu-id="a3a09-122">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="a3a09-122">**Element**</span></span>|<span data-ttu-id="a3a09-123">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="a3a09-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="a3a09-124">system.net</span><span class="sxs-lookup"><span data-stu-id="a3a09-124">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="a3a09-125">.NET Framework'ün ağa nasıl bağladığını belirten ayarlar içerir.</span><span class="sxs-lookup"><span data-stu-id="a3a09-125">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a3a09-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a3a09-126">Remarks</span></span>  
 <span data-ttu-id="a3a09-127">Öğe, `connectionManagement` bir sunucuya veya sunucu grubuna en fazla bağlantı sayısını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a3a09-127">The `connectionManagement` element defines the maximum number of connections to a server or group of servers.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="a3a09-128">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="a3a09-128">Configuration Files</span></span>  
 <span data-ttu-id="a3a09-129">Bu öğe uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a3a09-129">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a3a09-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="a3a09-130">Example</span></span>  
 <span data-ttu-id="a3a09-131">Aşağıdaki örnek, bir uygulamayı sunucuya `www.contoso.com` dört, diğer tüm sunuculara iki bağlantı kullanacak şekilde yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="a3a09-131">The following example configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a3a09-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a3a09-132">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="a3a09-133">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="a3a09-133">Network Settings Schema</span></span>](index.md)
