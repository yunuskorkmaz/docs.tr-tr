---
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
ms.openlocfilehash: 39ce85c3c15a2d4bdfce801a35e9ca088bd5091b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154744"
---
# <a name="remove-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="0125a-102">\<bağlantı yönetimi için> Öğesi kaldırma (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="0125a-102">\<remove> Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="0125a-103">Bağlantı yönetim listesinden bir IP adresi veya DNS adını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="0125a-103">Removes an IP address or DNS name from the connection management list.</span></span>  

<span data-ttu-id="0125a-104">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0125a-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0125a-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="0125a-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="0125a-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bağlantıYönetim>**](connectionmanagement-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="0125a-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<connectionManagement>**](connectionmanagement-element-network-settings.md)</span></span>\
<span data-ttu-id="0125a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>kaldırmak**</span><span class="sxs-lookup"><span data-stu-id="0125a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="0125a-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0125a-108">Syntax</span></span>  
  
```xml  
<remove
  address="server name or IP address"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0125a-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0125a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="0125a-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0125a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0125a-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0125a-111">Attributes</span></span>  
  
|<span data-ttu-id="0125a-112">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="0125a-112">**Attribute**</span></span>|<span data-ttu-id="0125a-113">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="0125a-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`address`|<span data-ttu-id="0125a-114">BIR IP adresi veya DNS adı.</span><span class="sxs-lookup"><span data-stu-id="0125a-114">An IP address or DNS name.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0125a-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0125a-115">Child Elements</span></span>  
 <span data-ttu-id="0125a-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="0125a-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0125a-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0125a-117">Parent Elements</span></span>  
  
|<span data-ttu-id="0125a-118">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="0125a-118">**Element**</span></span>|<span data-ttu-id="0125a-119">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="0125a-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="0125a-120">bağlantıYönetim</span><span class="sxs-lookup"><span data-stu-id="0125a-120">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="0125a-121">Bir ağ ana bilgisayarına en fazla bağlantı sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0125a-121">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0125a-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0125a-122">Remarks</span></span>  
 <span data-ttu-id="0125a-123">Öğe, `remove` belirtilen sunucunun bağlantı yönetimi listesi girişini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="0125a-123">The `remove` element removes the connection management list entry for the specified server.</span></span>  
  
 <span data-ttu-id="0125a-124">Özniteliğin `address` değeri geçerli bir IP adresi veya ana bilgisayar adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0125a-124">The value of the `address` attribute should be a valid IP address or host name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="0125a-125">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="0125a-125">Configuration Files</span></span>  
 <span data-ttu-id="0125a-126">Bu öğe uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0125a-126">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0125a-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="0125a-127">Example</span></span>  
 <span data-ttu-id="0125a-128">Aşağıdaki örnek, sunucu `www.adventure-works.com` için tüm bağlantı yönetimi listesi girişlerini kaldırır ve ardından bir `www.contoso.com` uygulamayı sunucuya dört, diğer tüm sunuculara iki bağlantı kullanacak şekilde yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="0125a-128">The following example removes any connection management list entries for the server `www.adventure-works.com` and then configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0125a-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0125a-129">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="0125a-130">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="0125a-130">Network Settings Schema</span></span>](index.md)
