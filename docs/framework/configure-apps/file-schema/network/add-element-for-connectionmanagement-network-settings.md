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
ms.openlocfilehash: 608c591b910252dd60950bf2aa7565d6df04d5fc
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664223"
---
# <a name="add-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="7503b-102">\<connectionManagement için > öğesi ekleme (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="7503b-102">\<add> Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="7503b-103">Bağlantı yönetimi listesine bir IP adresi veya DNS adı ekler.</span><span class="sxs-lookup"><span data-stu-id="7503b-103">Adds an IP address or DNS name to the connection management list.</span></span>  
  
 <span data-ttu-id="7503b-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="7503b-104">\<configuration></span></span>  
<span data-ttu-id="7503b-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="7503b-105">\<system.net></span></span>  
<span data-ttu-id="7503b-106">\<connectionManagement ></span><span class="sxs-lookup"><span data-stu-id="7503b-106">\<connectionManagement></span></span>  
<span data-ttu-id="7503b-107">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="7503b-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7503b-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7503b-108">Syntax</span></span>  
  
```xml  
<add   
  address="address expression"   
  maxconnection="integer"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7503b-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7503b-109">Attributes and Elements</span></span>  
 <span data-ttu-id="7503b-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7503b-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7503b-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7503b-111">Attributes</span></span>  
  
|<span data-ttu-id="7503b-112">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="7503b-112">**Attribute**</span></span>|<span data-ttu-id="7503b-113">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="7503b-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`address`|<span data-ttu-id="7503b-114">IP adresini veya DNS adını tanımlayan bir dize.</span><span class="sxs-lookup"><span data-stu-id="7503b-114">A string describing an IP address or DNS name.</span></span>|  
|`maxconnection`|<span data-ttu-id="7503b-115">Bir sunucuyla izin verilen en fazla bağlantı sayısı.</span><span class="sxs-lookup"><span data-stu-id="7503b-115">The maximum number of connections allowed to a server.</span></span> <span data-ttu-id="7503b-116">Sağlanmazsa, varsayılan değer 2 ' dir.</span><span class="sxs-lookup"><span data-stu-id="7503b-116">If not supplied, the default is 2.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7503b-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7503b-117">Child Elements</span></span>  
 <span data-ttu-id="7503b-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="7503b-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7503b-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7503b-119">Parent Elements</span></span>  
  
|<span data-ttu-id="7503b-120">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="7503b-120">**Element**</span></span>|<span data-ttu-id="7503b-121">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="7503b-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="7503b-122">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="7503b-122">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="7503b-123">Bir ağ konağına en fazla bağlantı sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="7503b-123">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7503b-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7503b-124">Remarks</span></span>  
 <span data-ttu-id="7503b-125">`address` Özniteliğin değeri tüm bağlantıları göstermek için bir yıldız işareti ya da formun `<schema>://<idn_hostname>[:<port>]`bir dizesi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7503b-125">The value of the `address` attribute should be either an asterisk to indicate all connections, or a string of the form `<schema>://<idn_hostname>[:<port>]`.</span></span>  
  
 <span data-ttu-id="7503b-126">Herhangi bir HTTP API 'sine geçirilen URI Unicode içeriyorsa, <xref:System.Uri.DnsSafeHost%2A> bu ad dahili olarak dönüştürülür ve bu, punicode dize (geçerli IDN yapılandırmasına bağımlı davranışlar) döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="7503b-126">If the URI passed to any HTTP APIs contains Unicode, the name will be converted internally using <xref:System.Uri.DnsSafeHost%2A> which might return a punicode string (behavior dependent on the current IDN configuration).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="7503b-127">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="7503b-127">Configuration Files</span></span>  
 <span data-ttu-id="7503b-128">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7503b-128">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7503b-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="7503b-129">Example</span></span>  
 <span data-ttu-id="7503b-130">Aşağıdaki örnek, bir uygulamayı sunucuya `www.contoso.com` dört bağlantı ve diğer tüm sunuculara iki bağlantı kullanacak şekilde yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="7503b-130">The following example configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7503b-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7503b-131">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="7503b-132">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="7503b-132">Network Settings Schema</span></span>](index.md)
