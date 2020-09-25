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
ms.openlocfilehash: ad641f93e93f627dae1c7d0bda4620093c4567b2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91205054"
---
# <a name="module-element-network-settings"></a><span data-ttu-id="2dfce-102">\<module> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="2dfce-102">\<module> Element (Network Settings)</span></span>

<span data-ttu-id="2dfce-103">Uygulamaya yeni bir proxy modülü ekler.</span><span class="sxs-lookup"><span data-stu-id="2dfce-103">Adds a new proxy module to the application.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<module>**

## <a name="syntax"></a><span data-ttu-id="2dfce-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="2dfce-104">Syntax</span></span>  
  
```xml  
<module
  type="type_fullname, assembly_fullname"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2dfce-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2dfce-105">Attributes and Elements</span></span>  

 <span data-ttu-id="2dfce-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2dfce-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2dfce-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2dfce-107">Attributes</span></span>  
  
|<span data-ttu-id="2dfce-108">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="2dfce-108">**Attribute**</span></span>|<span data-ttu-id="2dfce-109">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="2dfce-109">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="2dfce-110">Proxy 'yi uygulayan tam tür adı (özelliği ile gösterilir <xref:System.Type.FullName%2A> ) ve derleme adı (özelliği ile gösterilir <xref:System.Reflection.Assembly.FullName%2A> ).</span><span class="sxs-lookup"><span data-stu-id="2dfce-110">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma, that implements the proxy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2dfce-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2dfce-111">Child Elements</span></span>  

 <span data-ttu-id="2dfce-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="2dfce-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2dfce-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2dfce-113">Parent Elements</span></span>  
  
|<span data-ttu-id="2dfce-114">**Dosyalarında**</span><span class="sxs-lookup"><span data-stu-id="2dfce-114">**Element**</span></span>|<span data-ttu-id="2dfce-115">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="2dfce-115">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="2dfce-116">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="2dfce-116">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="2dfce-117">Köprü Metni Aktarım Protokolü (HTTP) proxy sunucusunu yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="2dfce-117">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2dfce-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2dfce-118">Remarks</span></span>  

 <span data-ttu-id="2dfce-119">`module`Öğesi, arabirimini uygulayan proxy sınıflarını kaydeder <xref:System.Net.IWebProxy> .</span><span class="sxs-lookup"><span data-stu-id="2dfce-119">The `module` element registers proxy classes that implement the <xref:System.Net.IWebProxy> interface.</span></span> <span data-ttu-id="2dfce-120">Proxy sınıfına kaydolduktan sonra, `module` desteklenen proxy aracılığıyla bilgi istemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2dfce-120">After registering the proxy class, `module` can be used to request information through the supported proxy.</span></span>  
  
 <span data-ttu-id="2dfce-121">Özniteliğin değeri, `type` modülün sınıf adı ve karşılık gelen dinamik bağlantı kitaplığının (dll) adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2dfce-121">The value for the `type` attribute should be the class name of the module and the name of its corresponding Dynamic Link Library (DLL).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="2dfce-122">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="2dfce-122">Configuration Files</span></span>  

 <span data-ttu-id="2dfce-123">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2dfce-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2dfce-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="2dfce-124">Example</span></span>  

 <span data-ttu-id="2dfce-125">Aşağıdaki örnek bir özel proxy sınıfı kaydeder.</span><span class="sxs-lookup"><span data-stu-id="2dfce-125">The following example registers a custom proxy class.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2dfce-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2dfce-126">See also</span></span>

- <xref:System.Net.IWebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="2dfce-127">Ağ ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="2dfce-127">Network Settings Schema</span></span>](index.md)
