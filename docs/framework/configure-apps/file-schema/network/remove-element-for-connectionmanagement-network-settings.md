---
description: 'Daha fazla bilgi edinin: <remove> connectionManagement için öğesi (ağ ayarları)'
title: connectionManagement için <remove> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- connectionManagement, remove element
- <remove> element, connectionManagement
- <connectionManagement>, remove element
- remove element, connectionManagement
ms.assetid: 94b81775-5a22-4975-8c47-8620c40c3f35
ms.openlocfilehash: 98916846fb5de93ee93a7e25530e983cbd3719ff
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99740255"
---
# <a name="remove-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="6c6ba-103">connectionManagement için \<remove> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="6c6ba-103">\<remove> Element for connectionManagement (Network Settings)</span></span>

<span data-ttu-id="6c6ba-104">Bağlantı yönetimi listesinden bir IP adresini veya DNS adını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="6c6ba-104">Removes an IP address or DNS name from the connection management list.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<connectionManagement>**](connectionmanagement-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a><span data-ttu-id="6c6ba-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="6c6ba-105">Syntax</span></span>  
  
```xml  
<remove
  address="server name or IP address"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6c6ba-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6c6ba-106">Attributes and Elements</span></span>  

 <span data-ttu-id="6c6ba-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6c6ba-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6c6ba-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6c6ba-108">Attributes</span></span>  
  
|<span data-ttu-id="6c6ba-109">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="6c6ba-109">**Attribute**</span></span>|<span data-ttu-id="6c6ba-110">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="6c6ba-110">**Description**</span></span>|  
|-------------------|---------------------|  
|`address`|<span data-ttu-id="6c6ba-111">Bir IP adresi veya DNS adı.</span><span class="sxs-lookup"><span data-stu-id="6c6ba-111">An IP address or DNS name.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6c6ba-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6c6ba-112">Child Elements</span></span>  

 <span data-ttu-id="6c6ba-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="6c6ba-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6c6ba-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6c6ba-114">Parent Elements</span></span>  
  
|<span data-ttu-id="6c6ba-115">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="6c6ba-115">**Element**</span></span>|<span data-ttu-id="6c6ba-116">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="6c6ba-116">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="6c6ba-117">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="6c6ba-117">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="6c6ba-118">Bir ağ konağına en fazla bağlantı sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6c6ba-118">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c6ba-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6c6ba-119">Remarks</span></span>  

 <span data-ttu-id="6c6ba-120">`remove`Öğesi, belirtilen sunucu için bağlantı yönetimi listesi girişini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="6c6ba-120">The `remove` element removes the connection management list entry for the specified server.</span></span>  
  
 <span data-ttu-id="6c6ba-121">`address`Özniteliğin değeri geçerli BIR IP adresi veya ana bilgisayar adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6c6ba-121">The value of the `address` attribute should be a valid IP address or host name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="6c6ba-122">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="6c6ba-122">Configuration Files</span></span>  

 <span data-ttu-id="6c6ba-123">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6c6ba-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6c6ba-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="6c6ba-124">Example</span></span>  

 <span data-ttu-id="6c6ba-125">Aşağıdaki örnek, sunucu için tüm bağlantı yönetim listesi girişlerini kaldırır `www.adventure-works.com` ve ardından bir uygulamayı sunucuya dört bağlantı `www.contoso.com` ve diğer tüm sunuculara iki bağlantı kullanacak şekilde yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="6c6ba-125">The following example removes any connection management list entries for the server `www.adventure-works.com` and then configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6c6ba-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6c6ba-126">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="6c6ba-127">Ağ ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="6c6ba-127">Network Settings Schema</span></span>](index.md)
