---
title: <defaultProxy> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultProxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy
helpviewer_keywords:
- defaultProxy element
- <defaultProxy> element
ms.assetid: 9d663c4b-07b4-4f6f-9b12-efbd3630354f
ms.openlocfilehash: 0945629c1395917bc1cf825f2ba84d20afa99957
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698202"
---
# <a name="defaultproxy-element-network-settings"></a><span data-ttu-id="8d5d9-102">\<defaultProxy > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="8d5d9-102">\<defaultProxy> Element (Network Settings)</span></span>
<span data-ttu-id="8d5d9-103">Köprü Metni Aktarım Protokolü (HTTP) proxy sunucusunu yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="8d5d9-103">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>  
  
[<span data-ttu-id="8d5d9-104"> **\<Yapılandırma >** </span><span class="sxs-lookup"><span data-stu-id="8d5d9-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="8d5d9-105">[ **System. net >\<** &nbsp;&nbsp;](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="8d5d9-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="8d5d9-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<defaultProxy >**</span><span class="sxs-lookup"><span data-stu-id="8d5d9-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultProxy>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d5d9-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8d5d9-107">Syntax</span></span>  
  
```xml  
<defaultProxy  
  enabled="true|false"  
  useDefaultCredentials="true|false">  
    <bypasslist>...</bypasslist>  
    <proxy>...</proxy>  
    <module>...</module>  
</defaultProxy>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8d5d9-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8d5d9-108">Attributes and Elements</span></span>  
 <span data-ttu-id="8d5d9-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8d5d9-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8d5d9-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8d5d9-110">Attributes</span></span>  
  
|<span data-ttu-id="8d5d9-111">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="8d5d9-111">**Element**</span></span>|<span data-ttu-id="8d5d9-112">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="8d5d9-112">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="8d5d9-113">Bir Web proxy 'sinin kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="8d5d9-113">Specifies whether a web proxy is used.</span></span> <span data-ttu-id="8d5d9-114">Varsayılan değer `true` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="8d5d9-114">The default value is `true`.</span></span>|  
|`useDefaultCredentials`|<span data-ttu-id="8d5d9-115">Bu konak için varsayılan kimlik bilgilerinin Web proxy 'sine erişmek için kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="8d5d9-115">Specifies whether the default credentials for this host are used to access the web proxy.</span></span> <span data-ttu-id="8d5d9-116">Varsayılan değer `false` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="8d5d9-116">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8d5d9-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8d5d9-117">Child Elements</span></span>  
  
|<span data-ttu-id="8d5d9-118">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="8d5d9-118">**Element**</span></span>|<span data-ttu-id="8d5d9-119">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="8d5d9-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="8d5d9-120">BypassList</span><span class="sxs-lookup"><span data-stu-id="8d5d9-120">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="8d5d9-121">Proxy kullanmayan adresleri tanımlayan normal ifadeler kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="8d5d9-121">Provides a set of regular expressions that describe addresses that do not use the proxy.</span></span>|  
|[<span data-ttu-id="8d5d9-122">module</span><span class="sxs-lookup"><span data-stu-id="8d5d9-122">module</span></span>](module-element-network-settings.md)|<span data-ttu-id="8d5d9-123">Uygulamaya yeni bir proxy modülü ekler.</span><span class="sxs-lookup"><span data-stu-id="8d5d9-123">Adds a new proxy module to the application.</span></span>|  
|[<span data-ttu-id="8d5d9-124">Proxy</span><span class="sxs-lookup"><span data-stu-id="8d5d9-124">proxy</span></span>](proxy-element-network-settings.md)|<span data-ttu-id="8d5d9-125">Bir ara sunucu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8d5d9-125">Defines a proxy server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8d5d9-126">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8d5d9-126">Parent Elements</span></span>  
  
|<span data-ttu-id="8d5d9-127">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="8d5d9-127">**Element**</span></span>|<span data-ttu-id="8d5d9-128">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="8d5d9-128">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="8d5d9-129">system.net</span><span class="sxs-lookup"><span data-stu-id="8d5d9-129">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="8d5d9-130">.NET Framework ağa nasıl bağlanacağını belirten ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="8d5d9-130">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8d5d9-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8d5d9-131">Remarks</span></span>  
 <span data-ttu-id="8d5d9-132">DefaultProxy öğesi boşsa, Internet Explorer 'daki proxy ayarları kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="8d5d9-132">If the defaultProxy element is empty, the proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="8d5d9-133">Bu davranış .NET Framework 1,1 sürümünden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="8d5d9-133">This behavior is different from version 1.1 of the .NET Framework.</span></span>  
  
 <span data-ttu-id="8d5d9-134">[Modül](module-element-network-settings.md) öğesi ortak olmayan bir tür belirtiyorsa, tür <xref:System.Net.IWebProxy> sınıfından türetilmez, bu nesnenin parametresiz oluşturucusundan bir özel durum oluştu veya sistem tarafından belirtilen varsayılan proxy alınırken özel durum oluştu.</span><span class="sxs-lookup"><span data-stu-id="8d5d9-134">An exception is thrown if the [module](module-element-network-settings.md) element specifies a non-public type, the type is not deriving from the <xref:System.Net.IWebProxy> class, an exception from the parameterless constructor of this object occurred, or an exception occurred while retrieving the system-specified default proxy.</span></span> <span data-ttu-id="8d5d9-135">Özel durumun <xref:System.Exception.InnerException%2A> özelliği, hatanın kök nedeni hakkında daha fazla bilgiye sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8d5d9-135">The <xref:System.Exception.InnerException%2A> property on the exception should have more information about the root cause of the error.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="8d5d9-136">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="8d5d9-136">Configuration Files</span></span>  
 <span data-ttu-id="8d5d9-137">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8d5d9-137">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d5d9-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="8d5d9-138">Example</span></span>  
 <span data-ttu-id="8d5d9-139">Aşağıdaki örnek, Internet Explorer proxy 'sinden varsayılan değerleri kullanır, proxy adresini belirtir ve yerel erişim ve contoso.com için proxy 'yi atlar.</span><span class="sxs-lookup"><span data-stu-id="8d5d9-139">The following example uses the defaults from the Internet Explorer proxy, specifies the proxy address, and bypasses the proxy for local access and contoso.com.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8d5d9-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8d5d9-140">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="8d5d9-141">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="8d5d9-141">Network Settings Schema</span></span>](index.md)
