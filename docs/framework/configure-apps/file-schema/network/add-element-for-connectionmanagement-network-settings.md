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
ms.openlocfilehash: 32b84412edf2d7c9943391909659dc91d8060cc1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54625763"
---
# <a name="ltaddgt-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="d4170-102">&lt;ekleme&gt; connectionManagement (ağ ayarları) için</span><span class="sxs-lookup"><span data-stu-id="d4170-102">&lt;add&gt; Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="d4170-103">Bir IP adresi veya DNS adı bağlantı yönetimi listesine ekler.</span><span class="sxs-lookup"><span data-stu-id="d4170-103">Adds an IP address or DNS name to the connection management list.</span></span>  
  
 <span data-ttu-id="d4170-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="d4170-104">\<configuration></span></span>  
<span data-ttu-id="d4170-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="d4170-105">\<system.net></span></span>  
<span data-ttu-id="d4170-106">\<connectionManagement ></span><span class="sxs-lookup"><span data-stu-id="d4170-106">\<connectionManagement></span></span>  
<span data-ttu-id="d4170-107">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="d4170-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4170-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d4170-108">Syntax</span></span>  
  
```xml  
<add   
  address="address expression"   
  maxconnection="integer"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d4170-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d4170-109">Attributes and Elements</span></span>  
 <span data-ttu-id="d4170-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d4170-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d4170-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d4170-111">Attributes</span></span>  
  
|<span data-ttu-id="d4170-112">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="d4170-112">**Attribute**</span></span>|<span data-ttu-id="d4170-113">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="d4170-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`address`|<span data-ttu-id="d4170-114">Bir IP adresi veya DNS adını tanımlayan bir dize.</span><span class="sxs-lookup"><span data-stu-id="d4170-114">A string describing an IP address or DNS name.</span></span>|  
|`maxconnection`|<span data-ttu-id="d4170-115">Bir sunucu için izin verilen bağlantı sayısı.</span><span class="sxs-lookup"><span data-stu-id="d4170-115">The maximum number of connections allowed to a server.</span></span> <span data-ttu-id="d4170-116">Sağlanmazsa, varsayılan 2'dir.</span><span class="sxs-lookup"><span data-stu-id="d4170-116">If not supplied, the default is 2.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d4170-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d4170-117">Child Elements</span></span>  
 <span data-ttu-id="d4170-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="d4170-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d4170-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d4170-119">Parent Elements</span></span>  
  
|<span data-ttu-id="d4170-120">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="d4170-120">**Element**</span></span>|<span data-ttu-id="d4170-121">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="d4170-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="d4170-122">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="d4170-122">connectionManagement</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|<span data-ttu-id="d4170-123">Bir ağ konak bağlantı maksimum sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d4170-123">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d4170-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d4170-124">Remarks</span></span>  
 <span data-ttu-id="d4170-125">Değerini `address` özniteliği olmalıdır tüm bağlantıları göstermek için bir yıldız işareti ya da formun dizesi `<schema>://<idn_hostname>[:<port>]`.</span><span class="sxs-lookup"><span data-stu-id="d4170-125">The value of the `address` attribute should be either an asterisk to indicate all connections, or a string of the form `<schema>://<idn_hostname>[:<port>]`.</span></span>  
  
 <span data-ttu-id="d4170-126">Herhangi bir HTTP API'sini geçirilen URI Unicode içeriyorsa, adı dahili olarak kullanılarak dönüştürülecek <xref:System.Uri.DnsSafeHost%2A> punicode dize (geçerli IDN yapılandırmaya bağımlı davranış) döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="d4170-126">If the URI passed to any HTTP APIs contains Unicode, the name will be converted internally using <xref:System.Uri.DnsSafeHost%2A> which might return a punicode string (behavior dependent on the current IDN configuration).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="d4170-127">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="d4170-127">Configuration Files</span></span>  
 <span data-ttu-id="d4170-128">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d4170-128">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d4170-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="d4170-129">Example</span></span>  
 <span data-ttu-id="d4170-130">Aşağıdaki örnek bir uygulama sunucusu dört bağlantılarını kullanmak için yapılandırır `www.contoso.com` ve diğer tüm sunucular iki bağlantı.</span><span class="sxs-lookup"><span data-stu-id="d4170-130">The following example configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d4170-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d4170-131">See also</span></span>
- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="d4170-132">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="d4170-132">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
