---
title: '&lt;Modül&gt; öğesi (ağ ayarları)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#module
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/module
helpviewer_keywords:
- module element
- <module> element
ms.assetid: 10318725-9666-4d65-ab61-b94c64e59f13
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 4d51010d6236103d252507802e14d01230d90219
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47075206"
---
# <a name="ltmodulegt-element-network-settings"></a><span data-ttu-id="5ad65-102">&lt;Modül&gt; öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="5ad65-102">&lt;module&gt; Element (Network Settings)</span></span>
<span data-ttu-id="5ad65-103">Yeni proxy modülü uygulamayı ekler.</span><span class="sxs-lookup"><span data-stu-id="5ad65-103">Adds a new proxy module to the application.</span></span>  
  
 <span data-ttu-id="5ad65-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="5ad65-104">\<configuration></span></span>  
<span data-ttu-id="5ad65-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="5ad65-105">\<system.net></span></span>  
<span data-ttu-id="5ad65-106">\<defaultProxy ></span><span class="sxs-lookup"><span data-stu-id="5ad65-106">\<defaultProxy></span></span>  
<span data-ttu-id="5ad65-107">\<Modül ></span><span class="sxs-lookup"><span data-stu-id="5ad65-107">\<module></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ad65-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5ad65-108">Syntax</span></span>  
  
```xml  
<module   
  type="type_fullname, assembly_fullname"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5ad65-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5ad65-109">Attributes and Elements</span></span>  
 <span data-ttu-id="5ad65-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5ad65-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5ad65-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5ad65-111">Attributes</span></span>  
  
|<span data-ttu-id="5ad65-112">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="5ad65-112">**Attribute**</span></span>|<span data-ttu-id="5ad65-113">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="5ad65-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="5ad65-114">Tam nitelikli tür adı (belirttiği <xref:System.Type.FullName%2A> özelliği) ve derleme adı (belirttiği <xref:System.Reflection.Assembly.FullName%2A> özelliği) proxy uygulayan bir virgülle ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="5ad65-114">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma, that implements the proxy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5ad65-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5ad65-115">Child Elements</span></span>  
 <span data-ttu-id="5ad65-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="5ad65-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5ad65-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5ad65-117">Parent Elements</span></span>  
  
|<span data-ttu-id="5ad65-118">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="5ad65-118">**Element**</span></span>|<span data-ttu-id="5ad65-119">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="5ad65-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="5ad65-120">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="5ad65-120">defaultProxy</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|<span data-ttu-id="5ad65-121">Köprü Metni Aktarım Protokolü (HTTP) proxy sunucusunu yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="5ad65-121">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5ad65-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5ad65-122">Remarks</span></span>  
 <span data-ttu-id="5ad65-123">`module` Öğesi kaydeder uygulayan proxy sınıflar <xref:System.Net.IWebProxy> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="5ad65-123">The `module` element registers proxy classes that implement the <xref:System.Net.IWebProxy> interface.</span></span> <span data-ttu-id="5ad65-124">Proxy sınıfı kaydettikten sonra `module` desteklenen proxy üzerinden bilgi istemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5ad65-124">After registering the proxy class, `module` can be used to request information through the supported proxy.</span></span>  
  
 <span data-ttu-id="5ad65-125">Değeri `type` modülünün sınıfı adı ve ' % s'adı, karşılık gelen dinamik bağlantı kitaplığı (DLL), öznitelik olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5ad65-125">The value for the `type` attribute should be the class name of the module and the name of its corresponding Dynamic Link Library (DLL).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="5ad65-126">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="5ad65-126">Configuration Files</span></span>  
 <span data-ttu-id="5ad65-127">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5ad65-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ad65-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="5ad65-128">Example</span></span>  
 <span data-ttu-id="5ad65-129">Aşağıdaki örnek bir özel proxy sınıfı kaydeder.</span><span class="sxs-lookup"><span data-stu-id="5ad65-129">The following example registers a custom proxy class.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <module  
        type="Test.CustomWebProxy, TestProxy, Version=2.0.3600.0, Culture=neutral, PublicKeyToken=b23a5c561934e385"  
      />  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5ad65-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5ad65-130">See Also</span></span>  
 <xref:System.Net.IWebProxy?displayProperty=nameWithType>  
 [<span data-ttu-id="5ad65-131">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="5ad65-131">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
