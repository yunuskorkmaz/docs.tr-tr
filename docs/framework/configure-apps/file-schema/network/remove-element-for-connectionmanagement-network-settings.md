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
ms.openlocfilehash: cbafd29be6855cbb95d17388791ba152230295cc
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697837"
---
# <a name="remove-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="86426-102">connectionManagement için \<remove > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="86426-102">\<remove> Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="86426-103">Bağlantı yönetimi listesinden bir IP adresini veya DNS adını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="86426-103">Removes an IP address or DNS name from the connection management list.</span></span>  
  
[<span data-ttu-id="86426-104"> **\<Yapılandırma >** </span><span class="sxs-lookup"><span data-stu-id="86426-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="86426-105">&nbsp; @ no__t-1[ **@no__t -4system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="86426-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="86426-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<connectionManagement >** ](connectionmanagement-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="86426-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<connectionManagement>**](connectionmanagement-element-network-settings.md)</span></span>  
<span data-ttu-id="86426-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<remove >**</span><span class="sxs-lookup"><span data-stu-id="86426-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86426-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="86426-108">Syntax</span></span>  
  
```xml  
<remove   
  address="server name or IP address"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="86426-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="86426-109">Attributes and Elements</span></span>  
 <span data-ttu-id="86426-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="86426-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="86426-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="86426-111">Attributes</span></span>  
  
|<span data-ttu-id="86426-112">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="86426-112">**Attribute**</span></span>|<span data-ttu-id="86426-113">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="86426-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`address`|<span data-ttu-id="86426-114">Bir IP adresi veya DNS adı.</span><span class="sxs-lookup"><span data-stu-id="86426-114">An IP address or DNS name.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="86426-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="86426-115">Child Elements</span></span>  
 <span data-ttu-id="86426-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="86426-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="86426-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="86426-117">Parent Elements</span></span>  
  
|<span data-ttu-id="86426-118">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="86426-118">**Element**</span></span>|<span data-ttu-id="86426-119">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="86426-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="86426-120">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="86426-120">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="86426-121">Bir ağ konağına en fazla bağlantı sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="86426-121">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="86426-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="86426-122">Remarks</span></span>  
 <span data-ttu-id="86426-123">@No__t-0 öğesi, belirtilen sunucu için bağlantı yönetimi listesi girişini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="86426-123">The `remove` element removes the connection management list entry for the specified server.</span></span>  
  
 <span data-ttu-id="86426-124">@No__t-0 özniteliğinin değeri geçerli bir IP adresi veya ana bilgisayar adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="86426-124">The value of the `address` attribute should be a valid IP address or host name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="86426-125">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="86426-125">Configuration Files</span></span>  
 <span data-ttu-id="86426-126">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="86426-126">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="86426-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="86426-127">Example</span></span>  
 <span data-ttu-id="86426-128">Aşağıdaki örnek, `www.adventure-works.com` sunucu için tüm bağlantı yönetim listesi girişlerini kaldırır ve ardından bir uygulamayı sunucu `www.contoso.com` ve diğer tüm sunucular için dört bağlantı kullanacak şekilde yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="86426-128">The following example removes any connection management list entries for the server `www.adventure-works.com` and then configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="86426-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="86426-129">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="86426-130">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="86426-130">Network Settings Schema</span></span>](index.md)
