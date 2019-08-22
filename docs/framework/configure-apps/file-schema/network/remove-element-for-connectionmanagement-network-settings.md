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
ms.openlocfilehash: 8ab7a43fbb3e8df5bb0c99b5947f2fafb362399a
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664038"
---
# <a name="remove-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="d2086-102">\<connectionManagement için > öğesini kaldır (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="d2086-102">\<remove> Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="d2086-103">Bağlantı yönetimi listesinden bir IP adresini veya DNS adını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="d2086-103">Removes an IP address or DNS name from the connection management list.</span></span>  
  
 <span data-ttu-id="d2086-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="d2086-104">\<configuration></span></span>  
<span data-ttu-id="d2086-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="d2086-105">\<system.net></span></span>  
<span data-ttu-id="d2086-106">\<connectionManagement ></span><span class="sxs-lookup"><span data-stu-id="d2086-106">\<connectionManagement></span></span>  
<span data-ttu-id="d2086-107">\<> Kaldır</span><span class="sxs-lookup"><span data-stu-id="d2086-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2086-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d2086-108">Syntax</span></span>  
  
```xml  
<remove   
  address="server name or IP address"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d2086-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d2086-109">Attributes and Elements</span></span>  
 <span data-ttu-id="d2086-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d2086-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d2086-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d2086-111">Attributes</span></span>  
  
|<span data-ttu-id="d2086-112">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="d2086-112">**Attribute**</span></span>|<span data-ttu-id="d2086-113">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="d2086-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`address`|<span data-ttu-id="d2086-114">Bir IP adresi veya DNS adı.</span><span class="sxs-lookup"><span data-stu-id="d2086-114">An IP address or DNS name.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d2086-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d2086-115">Child Elements</span></span>  
 <span data-ttu-id="d2086-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="d2086-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d2086-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d2086-117">Parent Elements</span></span>  
  
|<span data-ttu-id="d2086-118">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="d2086-118">**Element**</span></span>|<span data-ttu-id="d2086-119">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="d2086-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="d2086-120">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="d2086-120">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="d2086-121">Bir ağ konağına en fazla bağlantı sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d2086-121">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d2086-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d2086-122">Remarks</span></span>  
 <span data-ttu-id="d2086-123">`remove` Öğesi, belirtilen sunucu için bağlantı yönetimi listesi girişini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="d2086-123">The `remove` element removes the connection management list entry for the specified server.</span></span>  
  
 <span data-ttu-id="d2086-124">`address` Özniteliğin değeri geçerli bir IP adresi veya ana bilgisayar adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d2086-124">The value of the `address` attribute should be a valid IP address or host name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="d2086-125">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="d2086-125">Configuration Files</span></span>  
 <span data-ttu-id="d2086-126">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d2086-126">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2086-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="d2086-127">Example</span></span>  
 <span data-ttu-id="d2086-128">Aşağıdaki örnek, sunucu `www.adventure-works.com` için tüm bağlantı yönetim listesi girişlerini kaldırır ve ardından bir uygulamayı sunucuya `www.contoso.com` dört bağlantı ve diğer tüm sunuculara iki bağlantı kullanacak şekilde yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="d2086-128">The following example removes any connection management list entries for the server `www.adventure-works.com` and then configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d2086-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d2086-129">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="d2086-130">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="d2086-130">Network Settings Schema</span></span>](index.md)
