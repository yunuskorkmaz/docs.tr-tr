---
title: '&lt;defaultProxy&gt; öğesi (ağ ayarları)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultProxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy
helpviewer_keywords:
- defaultProxy element
- <defaultProxy> element
ms.assetid: 9d663c4b-07b4-4f6f-9b12-efbd3630354f
ms.openlocfilehash: 48c5f5a50563cdbea5fa806e7c7524e413ba3712
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54596182"
---
# <a name="ltdefaultproxygt-element-network-settings"></a><span data-ttu-id="6b404-102">&lt;defaultProxy&gt; öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="6b404-102">&lt;defaultProxy&gt; Element (Network Settings)</span></span>
<span data-ttu-id="6b404-103">Köprü Metni Aktarım Protokolü (HTTP) proxy sunucusunu yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="6b404-103">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>  
  
 <span data-ttu-id="6b404-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="6b404-104">\<configuration></span></span>  
<span data-ttu-id="6b404-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="6b404-105">\<system.net></span></span>  
<span data-ttu-id="6b404-106">\<defaultProxy ></span><span class="sxs-lookup"><span data-stu-id="6b404-106">\<defaultProxy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b404-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6b404-107">Syntax</span></span>  
  
```xml  
<defaultProxy  
  enabled="true|false"  
  useDefaultCredentials="true|false">  
    <bypasslist>...</bypasslist>  
    <proxy>...</proxy>  
    <module>...</module>  
</defaultProxy>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6b404-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6b404-108">Attributes and Elements</span></span>  
 <span data-ttu-id="6b404-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6b404-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6b404-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6b404-110">Attributes</span></span>  
  
|<span data-ttu-id="6b404-111">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="6b404-111">**Element**</span></span>|<span data-ttu-id="6b404-112">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="6b404-112">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="6b404-113">Bir web proxy kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6b404-113">Specifies whether a web proxy is used.</span></span> <span data-ttu-id="6b404-114">Varsayılan değer `true` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="6b404-114">The default value is `true`.</span></span>|  
|`useDefaultCredentials`|<span data-ttu-id="6b404-115">Bu ana bilgisayarın varsayılan kimlik bilgileri web proxy sunucusuna erişmek için kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6b404-115">Specifies whether the default credentials for this host are used to access the web proxy.</span></span> <span data-ttu-id="6b404-116">Varsayılan değer `false` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="6b404-116">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6b404-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6b404-117">Child Elements</span></span>  
  
|<span data-ttu-id="6b404-118">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="6b404-118">**Element**</span></span>|<span data-ttu-id="6b404-119">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="6b404-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="6b404-120">bypasslist</span><span class="sxs-lookup"><span data-stu-id="6b404-120">bypasslist</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|<span data-ttu-id="6b404-121">Proxy kullanmayın adresleri açıklayan normal bir ifade kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="6b404-121">Provides a set of regular expressions that describe addresses that do not use the proxy.</span></span>|  
|[<span data-ttu-id="6b404-122">module</span><span class="sxs-lookup"><span data-stu-id="6b404-122">module</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/module-element-network-settings.md)|<span data-ttu-id="6b404-123">Yeni proxy modülü uygulamayı ekler.</span><span class="sxs-lookup"><span data-stu-id="6b404-123">Adds a new proxy module to the application.</span></span>|  
|[<span data-ttu-id="6b404-124">Proxy</span><span class="sxs-lookup"><span data-stu-id="6b404-124">proxy</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/proxy-element-network-settings.md)|<span data-ttu-id="6b404-125">Bir proxy sunucusu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6b404-125">Defines a proxy server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6b404-126">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6b404-126">Parent Elements</span></span>  
  
|<span data-ttu-id="6b404-127">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="6b404-127">**Element**</span></span>|<span data-ttu-id="6b404-128">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="6b404-128">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="6b404-129">System.NET</span><span class="sxs-lookup"><span data-stu-id="6b404-129">system.net</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="6b404-130">.NET Framework ağa nasıl bağlandığını belirten ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="6b404-130">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6b404-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6b404-131">Remarks</span></span>  
 <span data-ttu-id="6b404-132">DefaultProxy öğesi boş ise, Internet Explorer proxy ayarları kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="6b404-132">If the defaultProxy element is empty, the proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="6b404-133">Bu davranış, .NET Framework'ün 1.1 sürümünden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="6b404-133">This behavior is different from version 1.1 of the .NET Framework.</span></span>  
  
 <span data-ttu-id="6b404-134">Bir özel durum [Modülü](../../../../../docs/framework/configure-apps/file-schema/network/module-element-network-settings.md) öğeyi belirten bir ortak olmayan tür, türün öğesinden türetme değil <xref:System.Net.IWebProxy> sınıfı, bu nesnenin varsayılan oluşturucu adresinden bir özel durum oluştu veya bir özel durum oluştu sırada Sistem tarafından belirlenen varsayılan ara sunucu alınıyor.</span><span class="sxs-lookup"><span data-stu-id="6b404-134">An exception is thrown if the [module](../../../../../docs/framework/configure-apps/file-schema/network/module-element-network-settings.md) element specifies a non-public type, the type is not deriving from the <xref:System.Net.IWebProxy> class, an exception from the default constructor of this object occurred, or an exception occurred while retrieving the system-specified default proxy.</span></span> <span data-ttu-id="6b404-135"><xref:System.Exception.InnerException%2A> Özel durum özelliği, hatanın kök nedeni hakkında daha fazla bilgi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6b404-135">The <xref:System.Exception.InnerException%2A> property on the exception should have more information about the root cause of the error.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="6b404-136">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="6b404-136">Configuration Files</span></span>  
 <span data-ttu-id="6b404-137">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6b404-137">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6b404-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="6b404-138">Example</span></span>  
 <span data-ttu-id="6b404-139">Aşağıdaki örnek, Internet Explorer proxy varsayılanlarından kullanır, proxy adresi belirtir ve yerel erişim ve contoso.com için proxy atlar.</span><span class="sxs-lookup"><span data-stu-id="6b404-139">The following example uses the defaults from the Internet Explorer proxy, specifies the proxy address, and bypasses the proxy for local access and contoso.com.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="true"  
        proxyaddress="http://192.168.1.10:3128"  
        bypassonlocal="true"  
      />  
      <bypasslist>  
        <add address="[a-z]+\.contoso\.com$" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6b404-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6b404-140">See also</span></span>
- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="6b404-141">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="6b404-141">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
