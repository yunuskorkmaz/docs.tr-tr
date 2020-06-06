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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154835"
---
# <a name="module-element-network-settings"></a><span data-ttu-id="eab0a-102">\<module> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="eab0a-102">\<module> Element (Network Settings)</span></span>
<span data-ttu-id="eab0a-103">Uygulamaya yeni bir proxy modülü ekler.</span><span class="sxs-lookup"><span data-stu-id="eab0a-103">Adds a new proxy module to the application.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<module>**

## <a name="syntax"></a><span data-ttu-id="eab0a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="eab0a-104">Syntax</span></span>  
  
```xml  
<module
  type="type_fullname, assembly_fullname"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eab0a-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="eab0a-105">Attributes and Elements</span></span>  
 <span data-ttu-id="eab0a-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="eab0a-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eab0a-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="eab0a-107">Attributes</span></span>  
  
|<span data-ttu-id="eab0a-108">**Öznitelik**</span><span class="sxs-lookup"><span data-stu-id="eab0a-108">**Attribute**</span></span>|<span data-ttu-id="eab0a-109">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="eab0a-109">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="eab0a-110">Proxy 'yi uygulayan tam tür adı (özelliği ile gösterilir <xref:System.Type.FullName%2A> ) ve derleme adı (özelliği ile gösterilir <xref:System.Reflection.Assembly.FullName%2A> ).</span><span class="sxs-lookup"><span data-stu-id="eab0a-110">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma, that implements the proxy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="eab0a-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="eab0a-111">Child Elements</span></span>  
 <span data-ttu-id="eab0a-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="eab0a-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="eab0a-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="eab0a-113">Parent Elements</span></span>  
  
|<span data-ttu-id="eab0a-114">**Dosyalarında**</span><span class="sxs-lookup"><span data-stu-id="eab0a-114">**Element**</span></span>|<span data-ttu-id="eab0a-115">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="eab0a-115">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="eab0a-116">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="eab0a-116">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="eab0a-117">Köprü Metni Aktarım Protokolü (HTTP) proxy sunucusunu yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="eab0a-117">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eab0a-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="eab0a-118">Remarks</span></span>  
 <span data-ttu-id="eab0a-119">`module`Öğesi, arabirimini uygulayan proxy sınıflarını kaydeder <xref:System.Net.IWebProxy> .</span><span class="sxs-lookup"><span data-stu-id="eab0a-119">The `module` element registers proxy classes that implement the <xref:System.Net.IWebProxy> interface.</span></span> <span data-ttu-id="eab0a-120">Proxy sınıfına kaydolduktan sonra, `module` desteklenen proxy aracılığıyla bilgi istemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="eab0a-120">After registering the proxy class, `module` can be used to request information through the supported proxy.</span></span>  
  
 <span data-ttu-id="eab0a-121">Özniteliğin değeri, `type` modülün sınıf adı ve karşılık gelen dinamik bağlantı kitaplığının (dll) adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="eab0a-121">The value for the `type` attribute should be the class name of the module and the name of its corresponding Dynamic Link Library (DLL).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="eab0a-122">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="eab0a-122">Configuration Files</span></span>  
 <span data-ttu-id="eab0a-123">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="eab0a-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="eab0a-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="eab0a-124">Example</span></span>  
 <span data-ttu-id="eab0a-125">Aşağıdaki örnek bir özel proxy sınıfı kaydeder.</span><span class="sxs-lookup"><span data-stu-id="eab0a-125">The following example registers a custom proxy class.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="eab0a-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eab0a-126">See also</span></span>

- <xref:System.Net.IWebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="eab0a-127">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="eab0a-127">Network Settings Schema</span></span>](index.md)
