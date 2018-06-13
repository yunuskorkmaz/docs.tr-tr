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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: a91775ff9f46eba772a959cfac3115c9720ac5ab
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32742724"
---
# <a name="ltdefaultproxygt-element-network-settings"></a><span data-ttu-id="5b30f-102">&lt;defaultProxy&gt; öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="5b30f-102">&lt;defaultProxy&gt; Element (Network Settings)</span></span>
<span data-ttu-id="5b30f-103">Köprü Metni Aktarım Protokolü (HTTP) proxy sunucusu yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="5b30f-103">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>  
  
 <span data-ttu-id="5b30f-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="5b30f-104">\<configuration></span></span>  
<span data-ttu-id="5b30f-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="5b30f-105">\<system.net></span></span>  
<span data-ttu-id="5b30f-106">\<defaultProxy ></span><span class="sxs-lookup"><span data-stu-id="5b30f-106">\<defaultProxy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b30f-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5b30f-107">Syntax</span></span>  
  
```xml  
      <defaultProxy  
        enabled="true|false"  
        useDefaultCredentials="true|false">  
           <bypasslist> … </bypasslist>  
           <proxy> … </proxy>  
           <module> … </module>  
      </defaultProxy>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5b30f-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5b30f-108">Attributes and Elements</span></span>  
 <span data-ttu-id="5b30f-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5b30f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5b30f-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5b30f-110">Attributes</span></span>  
  
|<span data-ttu-id="5b30f-111">**Öğesi**</span><span class="sxs-lookup"><span data-stu-id="5b30f-111">**Element**</span></span>|<span data-ttu-id="5b30f-112">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="5b30f-112">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="5b30f-113">Bir web proxy kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5b30f-113">Specifies whether a web proxy is used.</span></span> <span data-ttu-id="5b30f-114">Varsayılan değer `true` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="5b30f-114">The default value is `true`.</span></span>|  
|`useDefaultCredentials`|<span data-ttu-id="5b30f-115">Bu ana bilgisayarın varsayılan kimlik bilgilerini web proxy sunucusuna erişmek için kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5b30f-115">Specifies whether the default credentials for this host are used to access the web proxy.</span></span> <span data-ttu-id="5b30f-116">Varsayılan değer `false` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="5b30f-116">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5b30f-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5b30f-117">Child Elements</span></span>  
  
|<span data-ttu-id="5b30f-118">**Öğesi**</span><span class="sxs-lookup"><span data-stu-id="5b30f-118">**Element**</span></span>|<span data-ttu-id="5b30f-119">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="5b30f-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="5b30f-120">olarak ayarlanıyor</span><span class="sxs-lookup"><span data-stu-id="5b30f-120">bypasslist</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|<span data-ttu-id="5b30f-121">Proxy kullanmayın adresleri açıklamak normal bir ifade kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="5b30f-121">Provides a set of regular expressions that describe addresses that do not use the proxy.</span></span>|  
|[<span data-ttu-id="5b30f-122">Modülü</span><span class="sxs-lookup"><span data-stu-id="5b30f-122">module</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/module-element-network-settings.md)|<span data-ttu-id="5b30f-123">Yeni bir proxy modülü uygulamaya ekler.</span><span class="sxs-lookup"><span data-stu-id="5b30f-123">Adds a new proxy module to the application.</span></span>|  
|[<span data-ttu-id="5b30f-124">Proxy</span><span class="sxs-lookup"><span data-stu-id="5b30f-124">proxy</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/proxy-element-network-settings.md)|<span data-ttu-id="5b30f-125">Bir proxy sunucu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5b30f-125">Defines a proxy server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5b30f-126">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5b30f-126">Parent Elements</span></span>  
  
|<span data-ttu-id="5b30f-127">**Öğesi**</span><span class="sxs-lookup"><span data-stu-id="5b30f-127">**Element**</span></span>|<span data-ttu-id="5b30f-128">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="5b30f-128">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="5b30f-129">System.NET</span><span class="sxs-lookup"><span data-stu-id="5b30f-129">system.net</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="5b30f-130">.NET Framework ağa nasıl bağlanacağını belirtin ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="5b30f-130">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5b30f-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5b30f-131">Remarks</span></span>  
 <span data-ttu-id="5b30f-132">DefaultProxy öğesi boş ise, Internet Explorer proxy ayarları kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5b30f-132">If the defaultProxy element is empty, the proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="5b30f-133">Bu davranış, .NET Framework 1.1 sürümünden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="5b30f-133">This behavior is different from version 1.1 of the .NET Framework.</span></span>  
  
 <span data-ttu-id="5b30f-134">Bir özel durum [Modülü](../../../../../docs/framework/configure-apps/file-schema/network/module-element-network-settings.md) öğesi genel türü belirttiğinden, türü öğesinden türetilen değil <xref:System.Net.IWebProxy> sınıfı, bu nesnenin varsayılan oluşturucusundan özel durum oluştu ya da bir özel durum oluştu sırada Sistem tarafından belirlenen varsayılan proxy alınıyor.</span><span class="sxs-lookup"><span data-stu-id="5b30f-134">An exception is thrown if the [module](../../../../../docs/framework/configure-apps/file-schema/network/module-element-network-settings.md) element specifies a non-public type, the type is not deriving from the <xref:System.Net.IWebProxy> class, an exception from the default constructor of this object occurred, or an exception occurred while retrieving the system-specified default proxy.</span></span> <span data-ttu-id="5b30f-135"><xref:System.Exception.InnerException%2A> Özel durum özelliği hatasının kök nedeni hakkında daha fazla bilgi sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5b30f-135">The <xref:System.Exception.InnerException%2A> property on the exception should have more information about the root cause of the error.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="5b30f-136">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="5b30f-136">Configuration Files</span></span>  
 <span data-ttu-id="5b30f-137">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5b30f-137">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5b30f-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="5b30f-138">Example</span></span>  
 <span data-ttu-id="5b30f-139">Aşağıdaki örnek, varsayılan Internet Explorer proxy adlardan kullanır, proxy adresi belirtir ve yerel erişim ve contoso.com için proxy atlar.</span><span class="sxs-lookup"><span data-stu-id="5b30f-139">The following example uses the defaults from the Internet Explorer proxy, specifies the proxy address, and bypasses the proxy for local access and contoso.com.</span></span>  
  
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
        <add address="[a-z]+\.contoso\.com" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5b30f-140">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5b30f-140">See Also</span></span>  
 <xref:System.Net.WebProxy?displayProperty=nameWithType>  
 [<span data-ttu-id="5b30f-141">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="5b30f-141">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
