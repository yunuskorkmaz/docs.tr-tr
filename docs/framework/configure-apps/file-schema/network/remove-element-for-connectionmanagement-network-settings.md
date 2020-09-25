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
ms.openlocfilehash: 46157482d7ceb42b352c68dc9b0eab4f7688bc5c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91176181"
---
# <a name="remove-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="da4ba-102">connectionManagement için \<remove> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="da4ba-102">\<remove> Element for connectionManagement (Network Settings)</span></span>

<span data-ttu-id="da4ba-103">Bağlantı yönetimi listesinden bir IP adresini veya DNS adını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="da4ba-103">Removes an IP address or DNS name from the connection management list.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<connectionManagement>**](connectionmanagement-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a><span data-ttu-id="da4ba-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="da4ba-104">Syntax</span></span>  
  
```xml  
<remove
  address="server name or IP address"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="da4ba-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="da4ba-105">Attributes and Elements</span></span>  

 <span data-ttu-id="da4ba-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="da4ba-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="da4ba-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="da4ba-107">Attributes</span></span>  
  
|<span data-ttu-id="da4ba-108">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="da4ba-108">**Attribute**</span></span>|<span data-ttu-id="da4ba-109">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="da4ba-109">**Description**</span></span>|  
|-------------------|---------------------|  
|`address`|<span data-ttu-id="da4ba-110">Bir IP adresi veya DNS adı.</span><span class="sxs-lookup"><span data-stu-id="da4ba-110">An IP address or DNS name.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="da4ba-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="da4ba-111">Child Elements</span></span>  

 <span data-ttu-id="da4ba-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="da4ba-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="da4ba-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="da4ba-113">Parent Elements</span></span>  
  
|<span data-ttu-id="da4ba-114">**Dosyalarında**</span><span class="sxs-lookup"><span data-stu-id="da4ba-114">**Element**</span></span>|<span data-ttu-id="da4ba-115">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="da4ba-115">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="da4ba-116">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="da4ba-116">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="da4ba-117">Bir ağ konağına en fazla bağlantı sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="da4ba-117">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="da4ba-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="da4ba-118">Remarks</span></span>  

 <span data-ttu-id="da4ba-119">`remove`Öğesi, belirtilen sunucu için bağlantı yönetimi listesi girişini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="da4ba-119">The `remove` element removes the connection management list entry for the specified server.</span></span>  
  
 <span data-ttu-id="da4ba-120">`address`Özniteliğin değeri geçerli BIR IP adresi veya ana bilgisayar adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="da4ba-120">The value of the `address` attribute should be a valid IP address or host name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="da4ba-121">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="da4ba-121">Configuration Files</span></span>  

 <span data-ttu-id="da4ba-122">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="da4ba-122">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="da4ba-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="da4ba-123">Example</span></span>  

 <span data-ttu-id="da4ba-124">Aşağıdaki örnek, sunucu için tüm bağlantı yönetim listesi girişlerini kaldırır `www.adventure-works.com` ve ardından bir uygulamayı sunucuya dört bağlantı `www.contoso.com` ve diğer tüm sunuculara iki bağlantı kullanacak şekilde yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="da4ba-124">The following example removes any connection management list entries for the server `www.adventure-works.com` and then configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="da4ba-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="da4ba-125">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="da4ba-126">Ağ ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="da4ba-126">Network Settings Schema</span></span>](index.md)
