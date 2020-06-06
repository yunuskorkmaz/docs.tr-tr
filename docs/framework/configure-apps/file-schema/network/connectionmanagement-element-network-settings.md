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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154900"
---
# <a name="connectionmanagement-element-network-settings"></a><span data-ttu-id="f7c66-102">\<connectionManagement> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="f7c66-102">\<connectionManagement> Element (Network Settings)</span></span>
<span data-ttu-id="f7c66-103">Bir ağ konağına en fazla bağlantı sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f7c66-103">Specifies the maximum number of connections to a network host.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<connectionManagement>**

## <a name="syntax"></a><span data-ttu-id="f7c66-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f7c66-104">Syntax</span></span>  
  
```xml  
<connectionManagement>
</connectionManagement>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f7c66-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f7c66-105">Attributes and Elements</span></span>  
 <span data-ttu-id="f7c66-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f7c66-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f7c66-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f7c66-107">Attributes</span></span>  
 <span data-ttu-id="f7c66-108">Yok.</span><span class="sxs-lookup"><span data-stu-id="f7c66-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f7c66-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f7c66-109">Child Elements</span></span>  
  
|<span data-ttu-id="f7c66-110">**Dosyalarında**</span><span class="sxs-lookup"><span data-stu-id="f7c66-110">**Element**</span></span>|<span data-ttu-id="f7c66-111">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="f7c66-111">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="f7c66-112">add</span><span class="sxs-lookup"><span data-stu-id="f7c66-112">add</span></span>](add-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="f7c66-113">Bağlantı yönetimi listesine bir IP adresi veya DNS adı ekler.</span><span class="sxs-lookup"><span data-stu-id="f7c66-113">Adds an IP address or DNS name to the connection management list.</span></span>|  
|[<span data-ttu-id="f7c66-114">lediğiniz</span><span class="sxs-lookup"><span data-stu-id="f7c66-114">clear</span></span>](clear-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="f7c66-115">Bağlantı yönetimi listesini temizler.</span><span class="sxs-lookup"><span data-stu-id="f7c66-115">Clears the connection management list.</span></span>|  
|[<span data-ttu-id="f7c66-116">temizlenmesine</span><span class="sxs-lookup"><span data-stu-id="f7c66-116">remove</span></span>](remove-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="f7c66-117">Bağlantı yönetimi listesinden bir IP adresini veya DNS adını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="f7c66-117">Removes an IP address or DNS name from the connection management list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f7c66-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f7c66-118">Parent Elements</span></span>  
  
|<span data-ttu-id="f7c66-119">**Dosyalarında**</span><span class="sxs-lookup"><span data-stu-id="f7c66-119">**Element**</span></span>|<span data-ttu-id="f7c66-120">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="f7c66-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="f7c66-121">system.net</span><span class="sxs-lookup"><span data-stu-id="f7c66-121">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="f7c66-122">.NET Framework ağa nasıl bağlanacağını belirten ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="f7c66-122">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f7c66-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f7c66-123">Remarks</span></span>  
 <span data-ttu-id="f7c66-124">`connectionManagement`Öğesi bir sunucu veya sunucu grubu için en fazla bağlantı sayısını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f7c66-124">The `connectionManagement` element defines the maximum number of connections to a server or group of servers.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="f7c66-125">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="f7c66-125">Configuration Files</span></span>  
 <span data-ttu-id="f7c66-126">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f7c66-126">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f7c66-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="f7c66-127">Example</span></span>  
 <span data-ttu-id="f7c66-128">Aşağıdaki örnek, bir uygulamayı sunucuya dört bağlantı `www.contoso.com` ve diğer tüm sunuculara iki bağlantı kullanacak şekilde yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="f7c66-128">The following example configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f7c66-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f7c66-129">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="f7c66-130">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="f7c66-130">Network Settings Schema</span></span>](index.md)
