---
title: <defaultProxy> Öğesi (Ağ Ayarları)
description: <defaultProxy>Ağ ayarları öğesi .NET Framework Köprü Metni Aktarım Protokolü (http) proxy sunucusunu yapılandırır.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultProxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy
helpviewer_keywords:
- defaultProxy element
- <defaultProxy> element
ms.assetid: 9d663c4b-07b4-4f6f-9b12-efbd3630354f
ms.openlocfilehash: 915fdc96dbd4d417f9c9e6aa3ff96de3026491ef
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504608"
---
# <a name="defaultproxy-element-network-settings"></a><span data-ttu-id="c3769-103">\<defaultProxy> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="c3769-103">\<defaultProxy> Element (Network Settings)</span></span>
<span data-ttu-id="c3769-104">Köprü Metni Aktarım Protokolü (HTTP) proxy sunucusunu yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="c3769-104">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultProxy>**  
  
## <a name="syntax"></a><span data-ttu-id="c3769-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c3769-105">Syntax</span></span>  
  
```xml  
<defaultProxy  
  enabled="true|false"  
  useDefaultCredentials="true|false">  
    <bypasslist>...</bypasslist>  
    <proxy>...</proxy>  
    <module>...</module>  
</defaultProxy>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c3769-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c3769-106">Attributes and Elements</span></span>  
 <span data-ttu-id="c3769-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c3769-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c3769-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c3769-108">Attributes</span></span>  
  
|<span data-ttu-id="c3769-109">**Dosyalarında**</span><span class="sxs-lookup"><span data-stu-id="c3769-109">**Element**</span></span>|<span data-ttu-id="c3769-110">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="c3769-110">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="c3769-111">Bir Web proxy 'sinin kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c3769-111">Specifies whether a web proxy is used.</span></span> <span data-ttu-id="c3769-112">Varsayılan değer: `true`.</span><span class="sxs-lookup"><span data-stu-id="c3769-112">The default value is `true`.</span></span>|  
|`useDefaultCredentials`|<span data-ttu-id="c3769-113">Bu konak için varsayılan kimlik bilgilerinin Web proxy 'sine erişmek için kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c3769-113">Specifies whether the default credentials for this host are used to access the web proxy.</span></span> <span data-ttu-id="c3769-114">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="c3769-114">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c3769-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c3769-115">Child Elements</span></span>  
  
|<span data-ttu-id="c3769-116">**Dosyalarında**</span><span class="sxs-lookup"><span data-stu-id="c3769-116">**Element**</span></span>|<span data-ttu-id="c3769-117">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="c3769-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="c3769-118">BypassList</span><span class="sxs-lookup"><span data-stu-id="c3769-118">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="c3769-119">Proxy kullanmayan adresleri tanımlayan normal ifadeler kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="c3769-119">Provides a set of regular expressions that describe addresses that do not use the proxy.</span></span>|  
|[<span data-ttu-id="c3769-120">birimi</span><span class="sxs-lookup"><span data-stu-id="c3769-120">module</span></span>](module-element-network-settings.md)|<span data-ttu-id="c3769-121">Uygulamaya yeni bir proxy modülü ekler.</span><span class="sxs-lookup"><span data-stu-id="c3769-121">Adds a new proxy module to the application.</span></span>|  
|[<span data-ttu-id="c3769-122">proxy</span><span class="sxs-lookup"><span data-stu-id="c3769-122">proxy</span></span>](proxy-element-network-settings.md)|<span data-ttu-id="c3769-123">Bir ara sunucu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c3769-123">Defines a proxy server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c3769-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c3769-124">Parent Elements</span></span>  
  
|<span data-ttu-id="c3769-125">**Dosyalarında**</span><span class="sxs-lookup"><span data-stu-id="c3769-125">**Element**</span></span>|<span data-ttu-id="c3769-126">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="c3769-126">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="c3769-127">system.net</span><span class="sxs-lookup"><span data-stu-id="c3769-127">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="c3769-128">.NET Framework ağa nasıl bağlanacağını belirten ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="c3769-128">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c3769-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c3769-129">Remarks</span></span>  
 <span data-ttu-id="c3769-130">DefaultProxy öğesi boşsa, Internet Explorer 'daki proxy ayarları kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="c3769-130">If the defaultProxy element is empty, the proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="c3769-131">Bu davranış .NET Framework 1,1 sürümünden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="c3769-131">This behavior is different from version 1.1 of the .NET Framework.</span></span>  
  
 <span data-ttu-id="c3769-132">[Modül](module-element-network-settings.md) öğesi ortak olmayan bir tür belirtiyorsa, tür sınıftan türetilmiyor <xref:System.Net.IWebProxy> , bu nesnenin parametresiz oluşturucusundan bir özel durum oluştu veya sistem tarafından belirtilen varsayılan proxy alınırken özel durum oluştu.</span><span class="sxs-lookup"><span data-stu-id="c3769-132">An exception is thrown if the [module](module-element-network-settings.md) element specifies a non-public type, the type is not deriving from the <xref:System.Net.IWebProxy> class, an exception from the parameterless constructor of this object occurred, or an exception occurred while retrieving the system-specified default proxy.</span></span> <span data-ttu-id="c3769-133"><xref:System.Exception.InnerException%2A>Özel durum üzerindeki özelliği, hatanın kök nedeni hakkında daha fazla bilgi içermelidir.</span><span class="sxs-lookup"><span data-stu-id="c3769-133">The <xref:System.Exception.InnerException%2A> property on the exception should have more information about the root cause of the error.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="c3769-134">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="c3769-134">Configuration Files</span></span>  
 <span data-ttu-id="c3769-135">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c3769-135">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c3769-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="c3769-136">Example</span></span>  
 <span data-ttu-id="c3769-137">Aşağıdaki örnek, Internet Explorer proxy 'sinden varsayılan değerleri kullanır, proxy adresini belirtir ve yerel erişim ve contoso.com için proxy 'yi atlar.</span><span class="sxs-lookup"><span data-stu-id="c3769-137">The following example uses the defaults from the Internet Explorer proxy, specifies the proxy address, and bypasses the proxy for local access and contoso.com.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c3769-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c3769-138">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="c3769-139">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="c3769-139">Network Settings Schema</span></span>](index.md)
