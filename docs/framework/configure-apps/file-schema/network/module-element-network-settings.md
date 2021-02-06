---
description: 'Daha fazla bilgi edinin: <module> öğesi (ağ ayarları)'
title: <module> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#module
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/module
helpviewer_keywords:
- module element
- <module> element
ms.assetid: 10318725-9666-4d65-ab61-b94c64e59f13
ms.openlocfilehash: d498b79ae6046367bc81add5ea387e178ab6c29d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652841"
---
# <a name="module-element-network-settings"></a><span data-ttu-id="0ba8d-103">\<module> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="0ba8d-103">\<module> Element (Network Settings)</span></span>

<span data-ttu-id="0ba8d-104">Uygulamaya yeni bir proxy modülü ekler.</span><span class="sxs-lookup"><span data-stu-id="0ba8d-104">Adds a new proxy module to the application.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<module>**

## <a name="syntax"></a><span data-ttu-id="0ba8d-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="0ba8d-105">Syntax</span></span>  
  
```xml  
<module
  type="type_fullname, assembly_fullname"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0ba8d-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0ba8d-106">Attributes and Elements</span></span>  

 <span data-ttu-id="0ba8d-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0ba8d-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0ba8d-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0ba8d-108">Attributes</span></span>  
  
|<span data-ttu-id="0ba8d-109">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="0ba8d-109">**Attribute**</span></span>|<span data-ttu-id="0ba8d-110">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="0ba8d-110">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="0ba8d-111">Proxy 'yi uygulayan tam tür adı (özelliği ile gösterilir <xref:System.Type.FullName%2A> ) ve derleme adı (özelliği ile gösterilir <xref:System.Reflection.Assembly.FullName%2A> ).</span><span class="sxs-lookup"><span data-stu-id="0ba8d-111">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma, that implements the proxy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0ba8d-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0ba8d-112">Child Elements</span></span>  

 <span data-ttu-id="0ba8d-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="0ba8d-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0ba8d-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0ba8d-114">Parent Elements</span></span>  
  
|<span data-ttu-id="0ba8d-115">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="0ba8d-115">**Element**</span></span>|<span data-ttu-id="0ba8d-116">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="0ba8d-116">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="0ba8d-117">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="0ba8d-117">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="0ba8d-118">Köprü Metni Aktarım Protokolü (HTTP) proxy sunucusunu yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="0ba8d-118">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0ba8d-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0ba8d-119">Remarks</span></span>  

 <span data-ttu-id="0ba8d-120">`module`Öğesi, arabirimini uygulayan proxy sınıflarını kaydeder <xref:System.Net.IWebProxy> .</span><span class="sxs-lookup"><span data-stu-id="0ba8d-120">The `module` element registers proxy classes that implement the <xref:System.Net.IWebProxy> interface.</span></span> <span data-ttu-id="0ba8d-121">Proxy sınıfına kaydolduktan sonra, `module` desteklenen proxy aracılığıyla bilgi istemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0ba8d-121">After registering the proxy class, `module` can be used to request information through the supported proxy.</span></span>  
  
 <span data-ttu-id="0ba8d-122">Özniteliğin değeri, `type` modülün sınıf adı ve karşılık gelen dinamik bağlantı kitaplığının (dll) adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0ba8d-122">The value for the `type` attribute should be the class name of the module and the name of its corresponding Dynamic Link Library (DLL).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="0ba8d-123">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="0ba8d-123">Configuration Files</span></span>  

 <span data-ttu-id="0ba8d-124">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0ba8d-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ba8d-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="0ba8d-125">Example</span></span>  

 <span data-ttu-id="0ba8d-126">Aşağıdaki örnek bir özel proxy sınıfı kaydeder.</span><span class="sxs-lookup"><span data-stu-id="0ba8d-126">The following example registers a custom proxy class.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0ba8d-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0ba8d-127">See also</span></span>

- <xref:System.Net.IWebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="0ba8d-128">Ağ ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="0ba8d-128">Network Settings Schema</span></span>](index.md)
