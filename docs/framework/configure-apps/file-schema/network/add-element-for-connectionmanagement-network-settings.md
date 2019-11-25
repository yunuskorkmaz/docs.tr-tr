---
title: connectionManagement için <add> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement/add
helpviewer_keywords:
- <add> element, connectionManagement
- <connectionManagement>, add element
- add element, connectionManagement
- connectionManagement, add element
ms.assetid: 856bf57d-1c63-46c7-a178-03d97b0a4149
ms.openlocfilehash: 19ebbfba477eeba253a7af0742953cc6a4d45a0e
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088526"
---
# <a name="add-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="37b2a-102">connectionManagement için > öğesi eklemek \<(ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="37b2a-102">\<add> Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="37b2a-103">Bağlantı yönetimi listesine bir IP adresi veya DNS adı ekler.</span><span class="sxs-lookup"><span data-stu-id="37b2a-103">Adds an IP address or DNS name to the connection management list.</span></span>  

<span data-ttu-id="37b2a-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="37b2a-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="37b2a-105">[**System. net >\<** ](system-net-element-network-settings.md) &nbsp;&nbsp;</span><span class="sxs-lookup"><span data-stu-id="37b2a-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="37b2a-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<connectionManagement >** ](connectionmanagement-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="37b2a-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<connectionManagement>**](connectionmanagement-element-network-settings.md)</span></span>\
<span data-ttu-id="37b2a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<add >**</span><span class="sxs-lookup"><span data-stu-id="37b2a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="37b2a-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="37b2a-108">Syntax</span></span>  
  
```xml  
<add   
  address="address expression"   
  maxconnection="integer"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="37b2a-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="37b2a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="37b2a-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="37b2a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="37b2a-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="37b2a-111">Attributes</span></span>  
  
|<span data-ttu-id="37b2a-112">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="37b2a-112">**Attribute**</span></span>|<span data-ttu-id="37b2a-113">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="37b2a-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`address`|<span data-ttu-id="37b2a-114">IP adresini veya DNS adını tanımlayan bir dize.</span><span class="sxs-lookup"><span data-stu-id="37b2a-114">A string describing an IP address or DNS name.</span></span>|  
|`maxconnection`|<span data-ttu-id="37b2a-115">Bir sunucuyla izin verilen en fazla bağlantı sayısı.</span><span class="sxs-lookup"><span data-stu-id="37b2a-115">The maximum number of connections allowed to a server.</span></span> <span data-ttu-id="37b2a-116">Sağlanmazsa, varsayılan değer 2 ' dir.</span><span class="sxs-lookup"><span data-stu-id="37b2a-116">If not supplied, the default is 2.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="37b2a-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="37b2a-117">Child Elements</span></span>  
 <span data-ttu-id="37b2a-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="37b2a-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="37b2a-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="37b2a-119">Parent Elements</span></span>  
  
|<span data-ttu-id="37b2a-120">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="37b2a-120">**Element**</span></span>|<span data-ttu-id="37b2a-121">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="37b2a-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="37b2a-122">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="37b2a-122">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="37b2a-123">Bir ağ konağına en fazla bağlantı sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="37b2a-123">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="37b2a-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="37b2a-124">Remarks</span></span>  
 <span data-ttu-id="37b2a-125">`address` özniteliğin değeri, tüm bağlantıları göstermek için bir yıldız işareti ya da `<schema>://<idn_hostname>[:<port>]`bir form dizesi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="37b2a-125">The value of the `address` attribute should be either an asterisk to indicate all connections, or a string of the form `<schema>://<idn_hostname>[:<port>]`.</span></span>  
  
 <span data-ttu-id="37b2a-126">Herhangi bir HTTP API 'sine geçirilen URI Unicode içeriyorsa, ad, bir punıcode dizesi (geçerli ıDN yapılandırmasına bağımlı davranış) döndürebilen <xref:System.Uri.DnsSafeHost%2A> kullanılarak dahili olarak dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="37b2a-126">If the URI passed to any HTTP APIs contains Unicode, the name will be converted internally using <xref:System.Uri.DnsSafeHost%2A> which might return a punicode string (behavior dependent on the current IDN configuration).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="37b2a-127">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="37b2a-127">Configuration Files</span></span>  
 <span data-ttu-id="37b2a-128">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="37b2a-128">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="37b2a-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="37b2a-129">Example</span></span>  
 <span data-ttu-id="37b2a-130">Aşağıdaki örnek, bir uygulamayı sunucu `www.contoso.com` dört bağlantı ve diğer tüm sunuculara iki bağlantı kullanacak şekilde yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="37b2a-130">The following example configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <add address="http://www.contoso.com" maxconnection="4" />  
      <add address="*" maxconnection="2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="37b2a-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="37b2a-131">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="37b2a-132">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="37b2a-132">Network Settings Schema</span></span>](index.md)
