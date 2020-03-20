---
title: <module> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#module
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/module
helpviewer_keywords:
- module element
- <module> element
ms.assetid: 10318725-9666-4d65-ab61-b94c64e59f13
ms.openlocfilehash: ed28ae4a52085cbfa781b4baf2ee1eafbeff6eb4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154835"
---
# <a name="module-element-network-settings"></a><span data-ttu-id="ea4bc-102">\<modül> Elemanı (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="ea4bc-102">\<module> Element (Network Settings)</span></span>
<span data-ttu-id="ea4bc-103">Uygulamaya yeni bir proxy modülü ekler.</span><span class="sxs-lookup"><span data-stu-id="ea4bc-103">Adds a new proxy module to the application.</span></span>  

<span data-ttu-id="ea4bc-104">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ea4bc-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ea4bc-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="ea4bc-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="ea4bc-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="ea4bc-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)</span></span>\
<span data-ttu-id="ea4bc-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<modül>**</span><span class="sxs-lookup"><span data-stu-id="ea4bc-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<module>**</span></span>

## <a name="syntax"></a><span data-ttu-id="ea4bc-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ea4bc-108">Syntax</span></span>  
  
```xml  
<module
  type="type_fullname, assembly_fullname"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ea4bc-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ea4bc-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ea4bc-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ea4bc-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ea4bc-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ea4bc-111">Attributes</span></span>  
  
|<span data-ttu-id="ea4bc-112">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="ea4bc-112">**Attribute**</span></span>|<span data-ttu-id="ea4bc-113">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="ea4bc-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="ea4bc-114">Tam nitelikli tür adı <xref:System.Type.FullName%2A> (özellik tarafından gösterilir) ve derleme <xref:System.Reflection.Assembly.FullName%2A> adı (özellik tarafından gösterilir), bir virgül ile ayrılmış, proxy uygular.</span><span class="sxs-lookup"><span data-stu-id="ea4bc-114">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma, that implements the proxy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ea4bc-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ea4bc-115">Child Elements</span></span>  
 <span data-ttu-id="ea4bc-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="ea4bc-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ea4bc-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ea4bc-117">Parent Elements</span></span>  
  
|<span data-ttu-id="ea4bc-118">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="ea4bc-118">**Element**</span></span>|<span data-ttu-id="ea4bc-119">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="ea4bc-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="ea4bc-120">Defaultproxy</span><span class="sxs-lookup"><span data-stu-id="ea4bc-120">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="ea4bc-121">Hypertext Transfer Protocol (HTTP) proxy sunucusunu yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="ea4bc-121">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ea4bc-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ea4bc-122">Remarks</span></span>  
 <span data-ttu-id="ea4bc-123">Öğe, `module` arabirimi uygulayan proxy <xref:System.Net.IWebProxy> sınıflarını kaydeder.</span><span class="sxs-lookup"><span data-stu-id="ea4bc-123">The `module` element registers proxy classes that implement the <xref:System.Net.IWebProxy> interface.</span></span> <span data-ttu-id="ea4bc-124">Proxy sınıfını kaydettikten `module` sonra, desteklenen proxy aracılığıyla bilgi istemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ea4bc-124">After registering the proxy class, `module` can be used to request information through the supported proxy.</span></span>  
  
 <span data-ttu-id="ea4bc-125">Öznitelik değeri `type` modülün sınıf adı ve ilgili Dinamik Bağlantı Kitaplığı (DLL) adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ea4bc-125">The value for the `type` attribute should be the class name of the module and the name of its corresponding Dynamic Link Library (DLL).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="ea4bc-126">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="ea4bc-126">Configuration Files</span></span>  
 <span data-ttu-id="ea4bc-127">Bu öğe uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ea4bc-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea4bc-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="ea4bc-128">Example</span></span>  
 <span data-ttu-id="ea4bc-129">Aşağıdaki örneközel bir proxy sınıf kaydeder.</span><span class="sxs-lookup"><span data-stu-id="ea4bc-129">The following example registers a custom proxy class.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ea4bc-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ea4bc-130">See also</span></span>

- <xref:System.Net.IWebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="ea4bc-131">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="ea4bc-131">Network Settings Schema</span></span>](index.md)
