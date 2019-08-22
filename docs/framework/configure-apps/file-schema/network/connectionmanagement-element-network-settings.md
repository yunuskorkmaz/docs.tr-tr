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
ms.openlocfilehash: faaba1b9de302ed916ad1a81c7e80b3fb5a67170
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664162"
---
# <a name="connectionmanagement-element-network-settings"></a><span data-ttu-id="2559f-102">\<connectionManagement > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="2559f-102">\<connectionManagement> Element (Network Settings)</span></span>
<span data-ttu-id="2559f-103">Bir ağ konağına en fazla bağlantı sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="2559f-103">Specifies the maximum number of connections to a network host.</span></span>  
  
 <span data-ttu-id="2559f-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="2559f-104">\<configuration></span></span>  
<span data-ttu-id="2559f-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="2559f-105">\<system.net></span></span>  
<span data-ttu-id="2559f-106">\<connectionManagement ></span><span class="sxs-lookup"><span data-stu-id="2559f-106">\<connectionManagement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2559f-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2559f-107">Syntax</span></span>  
  
```xml  
<connectionManagement>   
</connectionManagement>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2559f-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2559f-108">Attributes and Elements</span></span>  
 <span data-ttu-id="2559f-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2559f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2559f-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2559f-110">Attributes</span></span>  
 <span data-ttu-id="2559f-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="2559f-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2559f-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2559f-112">Child Elements</span></span>  
  
|<span data-ttu-id="2559f-113">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="2559f-113">**Element**</span></span>|<span data-ttu-id="2559f-114">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="2559f-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="2559f-115">add</span><span class="sxs-lookup"><span data-stu-id="2559f-115">add</span></span>](add-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="2559f-116">Bağlantı yönetimi listesine bir IP adresi veya DNS adı ekler.</span><span class="sxs-lookup"><span data-stu-id="2559f-116">Adds an IP address or DNS name to the connection management list.</span></span>|  
|[<span data-ttu-id="2559f-117">lediğiniz</span><span class="sxs-lookup"><span data-stu-id="2559f-117">clear</span></span>](clear-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="2559f-118">Bağlantı yönetimi listesini temizler.</span><span class="sxs-lookup"><span data-stu-id="2559f-118">Clears the connection management list.</span></span>|  
|[<span data-ttu-id="2559f-119">remove</span><span class="sxs-lookup"><span data-stu-id="2559f-119">remove</span></span>](remove-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="2559f-120">Bağlantı yönetimi listesinden bir IP adresini veya DNS adını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="2559f-120">Removes an IP address or DNS name from the connection management list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2559f-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2559f-121">Parent Elements</span></span>  
  
|<span data-ttu-id="2559f-122">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="2559f-122">**Element**</span></span>|<span data-ttu-id="2559f-123">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="2559f-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="2559f-124">system.net</span><span class="sxs-lookup"><span data-stu-id="2559f-124">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="2559f-125">.NET Framework ağa nasıl bağlanacağını belirten ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="2559f-125">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2559f-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2559f-126">Remarks</span></span>  
 <span data-ttu-id="2559f-127">`connectionManagement` Öğesi bir sunucu veya sunucu grubu için en fazla bağlantı sayısını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2559f-127">The `connectionManagement` element defines the maximum number of connections to a server or group of servers.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="2559f-128">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="2559f-128">Configuration Files</span></span>  
 <span data-ttu-id="2559f-129">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2559f-129">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2559f-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="2559f-130">Example</span></span>  
 <span data-ttu-id="2559f-131">Aşağıdaki örnek, bir uygulamayı sunucuya `www.contoso.com` dört bağlantı ve diğer tüm sunuculara iki bağlantı kullanacak şekilde yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="2559f-131">The following example configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2559f-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2559f-132">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="2559f-133">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="2559f-133">Network Settings Schema</span></span>](index.md)
