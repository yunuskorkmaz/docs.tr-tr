---
title: '&lt;ekleme&gt; connectionManagement (ağ ayarları) için'
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
author: mcleblanc
ms.author: markl
ms.openlocfilehash: cdc7e8501f7cf3f5cff4c29ca5b2d004ce7cd5c6
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47080331"
---
# <a name="ltaddgt-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="5cd37-102">&lt;ekleme&gt; connectionManagement (ağ ayarları) için</span><span class="sxs-lookup"><span data-stu-id="5cd37-102">&lt;add&gt; Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="5cd37-103">Bir IP adresi veya DNS adı bağlantı yönetimi listesine ekler.</span><span class="sxs-lookup"><span data-stu-id="5cd37-103">Adds an IP address or DNS name to the connection management list.</span></span>  
  
 <span data-ttu-id="5cd37-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="5cd37-104">\<configuration></span></span>  
<span data-ttu-id="5cd37-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="5cd37-105">\<system.net></span></span>  
<span data-ttu-id="5cd37-106">\<connectionManagement ></span><span class="sxs-lookup"><span data-stu-id="5cd37-106">\<connectionManagement></span></span>  
<span data-ttu-id="5cd37-107">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="5cd37-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5cd37-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5cd37-108">Syntax</span></span>  
  
```xml  
<add   
  address="address expression"   
  maxconnection="integer"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5cd37-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5cd37-109">Attributes and Elements</span></span>  
 <span data-ttu-id="5cd37-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5cd37-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5cd37-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5cd37-111">Attributes</span></span>  
  
|<span data-ttu-id="5cd37-112">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="5cd37-112">**Attribute**</span></span>|<span data-ttu-id="5cd37-113">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="5cd37-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`address`|<span data-ttu-id="5cd37-114">Bir IP adresi veya DNS adını tanımlayan bir dize.</span><span class="sxs-lookup"><span data-stu-id="5cd37-114">A string describing an IP address or DNS name.</span></span>|  
|`maxconnection`|<span data-ttu-id="5cd37-115">Bir sunucu için izin verilen bağlantı sayısı.</span><span class="sxs-lookup"><span data-stu-id="5cd37-115">The maximum number of connections allowed to a server.</span></span> <span data-ttu-id="5cd37-116">Sağlanmazsa, varsayılan 2'dir.</span><span class="sxs-lookup"><span data-stu-id="5cd37-116">If not supplied, the default is 2.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5cd37-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5cd37-117">Child Elements</span></span>  
 <span data-ttu-id="5cd37-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="5cd37-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5cd37-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5cd37-119">Parent Elements</span></span>  
  
|<span data-ttu-id="5cd37-120">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="5cd37-120">**Element**</span></span>|<span data-ttu-id="5cd37-121">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="5cd37-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="5cd37-122">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="5cd37-122">connectionManagement</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|<span data-ttu-id="5cd37-123">Bir ağ konak bağlantı maksimum sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5cd37-123">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5cd37-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5cd37-124">Remarks</span></span>  
 <span data-ttu-id="5cd37-125">Değerini `address` özniteliği olmalıdır tüm bağlantıları göstermek için bir yıldız işareti ya da formun dizesi `<schema>://<idn_hostname>[:<port>]`.</span><span class="sxs-lookup"><span data-stu-id="5cd37-125">The value of the `address` attribute should be either an asterisk to indicate all connections, or a string of the form `<schema>://<idn_hostname>[:<port>]`.</span></span>  
  
 <span data-ttu-id="5cd37-126">Herhangi bir HTTP API'sini geçirilen URI Unicode içeriyorsa, adı dahili olarak kullanılarak dönüştürülecek <xref:System.Uri.DnsSafeHost%2A> punicode dize (geçerli IDN yapılandırmaya bağımlı davranış) döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="5cd37-126">If the URI passed to any HTTP APIs contains Unicode, the name will be converted internally using <xref:System.Uri.DnsSafeHost%2A> which might return a punicode string (behavior dependent on the current IDN configuration).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="5cd37-127">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="5cd37-127">Configuration Files</span></span>  
 <span data-ttu-id="5cd37-128">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5cd37-128">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5cd37-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="5cd37-129">Example</span></span>  
 <span data-ttu-id="5cd37-130">Aşağıdaki örnek, bir uygulamayı server www.contoso.com için dört bağlantıları ve diğer tüm sunucular iki bağlantıları kullanmak için yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="5cd37-130">The following example configures an application to use four connections to the server www.contoso.com and two connections to all other servers.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5cd37-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5cd37-131">See Also</span></span>  
 <xref:System.Net.ServicePoint>  
 <xref:System.Net.ServicePointManager>  
 [<span data-ttu-id="5cd37-132">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="5cd37-132">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
