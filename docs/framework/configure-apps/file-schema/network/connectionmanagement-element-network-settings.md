---
title: <connectionManagement> Öğesi (Ağ Ayarları)
description: <connectionManagement>Ağ ayarları öğesi .NET Framework bir ağ konağına en fazla bağlantı sayısını belirtir.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement
- http://schemas.microsoft.com/.NetConfiguration/v2.0#connectionManagement
helpviewer_keywords:
- <connectionManagement> element
- connectionManagement element
ms.assetid: bedccaab-12a2-4511-8f67-e961f249aec6
ms.openlocfilehash: 52b780c739a00cb53694b547ee1a33c1b5d98c86
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91167320"
---
# <a name="connectionmanagement-element-network-settings"></a><span data-ttu-id="21287-103">\<connectionManagement> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="21287-103">\<connectionManagement> Element (Network Settings)</span></span>

<span data-ttu-id="21287-104">Bir ağ konağına en fazla bağlantı sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="21287-104">Specifies the maximum number of connections to a network host.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<connectionManagement>**

## <a name="syntax"></a><span data-ttu-id="21287-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="21287-105">Syntax</span></span>  
  
```xml  
<connectionManagement>
</connectionManagement>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="21287-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="21287-106">Attributes and Elements</span></span>  

 <span data-ttu-id="21287-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="21287-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="21287-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="21287-108">Attributes</span></span>  

 <span data-ttu-id="21287-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="21287-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="21287-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="21287-110">Child Elements</span></span>  
  
|<span data-ttu-id="21287-111">**Dosyalarında**</span><span class="sxs-lookup"><span data-stu-id="21287-111">**Element**</span></span>|<span data-ttu-id="21287-112">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="21287-112">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="21287-113">add</span><span class="sxs-lookup"><span data-stu-id="21287-113">add</span></span>](add-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="21287-114">Bağlantı yönetimi listesine bir IP adresi veya DNS adı ekler.</span><span class="sxs-lookup"><span data-stu-id="21287-114">Adds an IP address or DNS name to the connection management list.</span></span>|  
|[<span data-ttu-id="21287-115">lediğiniz</span><span class="sxs-lookup"><span data-stu-id="21287-115">clear</span></span>](clear-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="21287-116">Bağlantı yönetimi listesini temizler.</span><span class="sxs-lookup"><span data-stu-id="21287-116">Clears the connection management list.</span></span>|  
|[<span data-ttu-id="21287-117">temizlenmesine</span><span class="sxs-lookup"><span data-stu-id="21287-117">remove</span></span>](remove-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="21287-118">Bağlantı yönetimi listesinden bir IP adresini veya DNS adını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="21287-118">Removes an IP address or DNS name from the connection management list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="21287-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="21287-119">Parent Elements</span></span>  
  
|<span data-ttu-id="21287-120">**Dosyalarında**</span><span class="sxs-lookup"><span data-stu-id="21287-120">**Element**</span></span>|<span data-ttu-id="21287-121">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="21287-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="21287-122">system.net</span><span class="sxs-lookup"><span data-stu-id="21287-122">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="21287-123">.NET Framework ağa nasıl bağlanacağını belirten ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="21287-123">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="21287-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="21287-124">Remarks</span></span>  

 <span data-ttu-id="21287-125">`connectionManagement`Öğesi bir sunucu veya sunucu grubu için en fazla bağlantı sayısını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="21287-125">The `connectionManagement` element defines the maximum number of connections to a server or group of servers.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="21287-126">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="21287-126">Configuration Files</span></span>  

 <span data-ttu-id="21287-127">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="21287-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="21287-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="21287-128">Example</span></span>  

 <span data-ttu-id="21287-129">Aşağıdaki örnek, bir uygulamayı sunucuya dört bağlantı `www.contoso.com` ve diğer tüm sunuculara iki bağlantı kullanacak şekilde yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="21287-129">The following example configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="21287-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="21287-130">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="21287-131">Ağ ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="21287-131">Network Settings Schema</span></span>](index.md)
