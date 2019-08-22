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
ms.openlocfilehash: 851a63b41dfb5d3b4058e1373148f48d47d9d6ae
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664076"
---
# <a name="module-element-network-settings"></a><span data-ttu-id="3d8d6-102">\<Module > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="3d8d6-102">\<module> Element (Network Settings)</span></span>
<span data-ttu-id="3d8d6-103">Uygulamaya yeni bir proxy modülü ekler.</span><span class="sxs-lookup"><span data-stu-id="3d8d6-103">Adds a new proxy module to the application.</span></span>  
  
 <span data-ttu-id="3d8d6-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="3d8d6-104">\<configuration></span></span>  
<span data-ttu-id="3d8d6-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="3d8d6-105">\<system.net></span></span>  
<span data-ttu-id="3d8d6-106">\<defaultProxy ></span><span class="sxs-lookup"><span data-stu-id="3d8d6-106">\<defaultProxy></span></span>  
<span data-ttu-id="3d8d6-107">\<Modül ></span><span class="sxs-lookup"><span data-stu-id="3d8d6-107">\<module></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d8d6-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3d8d6-108">Syntax</span></span>  
  
```xml  
<module   
  type="type_fullname, assembly_fullname"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3d8d6-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3d8d6-109">Attributes and Elements</span></span>  
 <span data-ttu-id="3d8d6-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3d8d6-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3d8d6-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3d8d6-111">Attributes</span></span>  
  
|<span data-ttu-id="3d8d6-112">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="3d8d6-112">**Attribute**</span></span>|<span data-ttu-id="3d8d6-113">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="3d8d6-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="3d8d6-114">Proxy 'yi uygulayan tam tür adı ( <xref:System.Type.FullName%2A> özelliği ile gösterilir) ve derleme adı ( <xref:System.Reflection.Assembly.FullName%2A> özelliği ile gösterilir).</span><span class="sxs-lookup"><span data-stu-id="3d8d6-114">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma, that implements the proxy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3d8d6-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3d8d6-115">Child Elements</span></span>  
 <span data-ttu-id="3d8d6-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="3d8d6-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3d8d6-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3d8d6-117">Parent Elements</span></span>  
  
|<span data-ttu-id="3d8d6-118">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="3d8d6-118">**Element**</span></span>|<span data-ttu-id="3d8d6-119">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="3d8d6-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="3d8d6-120">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="3d8d6-120">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="3d8d6-121">Köprü Metni Aktarım Protokolü (HTTP) proxy sunucusunu yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="3d8d6-121">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3d8d6-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3d8d6-122">Remarks</span></span>  
 <span data-ttu-id="3d8d6-123">Öğesi, <xref:System.Net.IWebProxy> arabirimini uygulayan proxy sınıflarını kaydeder. `module`</span><span class="sxs-lookup"><span data-stu-id="3d8d6-123">The `module` element registers proxy classes that implement the <xref:System.Net.IWebProxy> interface.</span></span> <span data-ttu-id="3d8d6-124">Proxy sınıfına kaydolduktan sonra, `module` desteklenen proxy aracılığıyla bilgi istemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3d8d6-124">After registering the proxy class, `module` can be used to request information through the supported proxy.</span></span>  
  
 <span data-ttu-id="3d8d6-125">`type` Özniteliğin değeri, modülün sınıf adı ve karşılık gelen dinamik bağlantı kitaplığının (dll) adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3d8d6-125">The value for the `type` attribute should be the class name of the module and the name of its corresponding Dynamic Link Library (DLL).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="3d8d6-126">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="3d8d6-126">Configuration Files</span></span>  
 <span data-ttu-id="3d8d6-127">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3d8d6-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3d8d6-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="3d8d6-128">Example</span></span>  
 <span data-ttu-id="3d8d6-129">Aşağıdaki örnek bir özel proxy sınıfı kaydeder.</span><span class="sxs-lookup"><span data-stu-id="3d8d6-129">The following example registers a custom proxy class.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3d8d6-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3d8d6-130">See also</span></span>

- <xref:System.Net.IWebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="3d8d6-131">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="3d8d6-131">Network Settings Schema</span></span>](index.md)
