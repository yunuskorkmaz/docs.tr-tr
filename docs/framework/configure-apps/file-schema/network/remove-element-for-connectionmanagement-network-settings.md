---
title: '&lt;kaldırma&gt; connectionManagement (ağ ayarları) için'
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
author: mcleblanc
ms.author: markl
ms.openlocfilehash: d249cc412a1638e62b57b4976adc23fdf8f36e80
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47085553"
---
# <a name="ltremovegt-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="e395b-102">&lt;kaldırma&gt; connectionManagement (ağ ayarları) için</span><span class="sxs-lookup"><span data-stu-id="e395b-102">&lt;remove&gt; Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="e395b-103">Bir IP adresi veya DNS adı bağlantı yönetimi listesinden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="e395b-103">Removes an IP address or DNS name from the connection management list.</span></span>  
  
 <span data-ttu-id="e395b-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="e395b-104">\<configuration></span></span>  
<span data-ttu-id="e395b-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="e395b-105">\<system.net></span></span>  
<span data-ttu-id="e395b-106">\<connectionManagement ></span><span class="sxs-lookup"><span data-stu-id="e395b-106">\<connectionManagement></span></span>  
<span data-ttu-id="e395b-107">\<kaldırma ></span><span class="sxs-lookup"><span data-stu-id="e395b-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e395b-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e395b-108">Syntax</span></span>  
  
```xml  
<remove   
  address="server name or IP address"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e395b-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e395b-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e395b-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e395b-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e395b-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e395b-111">Attributes</span></span>  
  
|<span data-ttu-id="e395b-112">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="e395b-112">**Attribute**</span></span>|<span data-ttu-id="e395b-113">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="e395b-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`address`|<span data-ttu-id="e395b-114">Bir IP adresi veya DNS adı.</span><span class="sxs-lookup"><span data-stu-id="e395b-114">An IP address or DNS name.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e395b-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e395b-115">Child Elements</span></span>  
 <span data-ttu-id="e395b-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="e395b-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e395b-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e395b-117">Parent Elements</span></span>  
  
|<span data-ttu-id="e395b-118">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="e395b-118">**Element**</span></span>|<span data-ttu-id="e395b-119">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="e395b-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="e395b-120">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="e395b-120">connectionManagement</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|<span data-ttu-id="e395b-121">Bir ağ konak bağlantı maksimum sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e395b-121">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e395b-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e395b-122">Remarks</span></span>  
 <span data-ttu-id="e395b-123">`remove` Bağlantı yönetim listesi girişi için belirtilen server öğeyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="e395b-123">The `remove` element removes the connection management list entry for the specified server.</span></span>  
  
 <span data-ttu-id="e395b-124">Değerini `address` özniteliği geçerli bir IP adresi veya ana bilgisayar adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e395b-124">The value of the `address` attribute should be a valid IP address or host name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="e395b-125">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="e395b-125">Configuration Files</span></span>  
 <span data-ttu-id="e395b-126">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e395b-126">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e395b-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="e395b-127">Example</span></span>  
 <span data-ttu-id="e395b-128">Aşağıdaki örnekte, sunucu www.adventure-works.com için tüm bağlantı yönetimi Liste girişlerini kaldırır ve bir uygulamayı server www.contoso.com için dört bağlantıları ve diğer tüm sunucular iki bağlantıları kullanmak için yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="e395b-128">The following example removes any connection management list entries for the server www.adventure-works.com and then configures an application to use four connections to the server www.contoso.com and two connections to all other servers.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e395b-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e395b-129">See Also</span></span>  
 <xref:System.Net.ServicePoint>  
 <xref:System.Net.ServicePointManager>  
 [<span data-ttu-id="e395b-130">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="e395b-130">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
