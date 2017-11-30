---
title: "&lt;Modül&gt; öğesi (ağ ayarları)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#module
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/module
helpviewer_keywords:
- module element
- <module> element
ms.assetid: 10318725-9666-4d65-ab61-b94c64e59f13
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: a039f6ed985997c5557659abd299fe0fc7699a1b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltmodulegt-element-network-settings"></a><span data-ttu-id="384b4-102">&lt;Modül&gt; öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="384b4-102">&lt;module&gt; Element (Network Settings)</span></span>
<span data-ttu-id="384b4-103">Yeni bir proxy modülü uygulamaya ekler.</span><span class="sxs-lookup"><span data-stu-id="384b4-103">Adds a new proxy module to the application.</span></span>  
  
 <span data-ttu-id="384b4-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="384b4-104">\<configuration></span></span>  
<span data-ttu-id="384b4-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="384b4-105">\<system.net></span></span>  
<span data-ttu-id="384b4-106">\<defaultProxy ></span><span class="sxs-lookup"><span data-stu-id="384b4-106">\<defaultProxy></span></span>  
<span data-ttu-id="384b4-107">\<Modül ></span><span class="sxs-lookup"><span data-stu-id="384b4-107">\<module></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="384b4-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="384b4-108">Syntax</span></span>  
  
```xml  
<module   
  type="type_fullname, assembly_fullname"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="384b4-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="384b4-109">Attributes and Elements</span></span>  
 <span data-ttu-id="384b4-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="384b4-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="384b4-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="384b4-111">Attributes</span></span>  
  
|<span data-ttu-id="384b4-112">**Özniteliği**</span><span class="sxs-lookup"><span data-stu-id="384b4-112">**Attribute**</span></span>|<span data-ttu-id="384b4-113">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="384b4-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="384b4-114">Tam olarak nitelenmiş tür adını (belirttiği <xref:System.Type.FullName%2A> özelliği) ve derleme adının (belirttiği <xref:System.Reflection.Assembly.FullName%2A> özelliği), proxy uygulayan bir virgülle ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="384b4-114">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma, that implements the proxy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="384b4-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="384b4-115">Child Elements</span></span>  
 <span data-ttu-id="384b4-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="384b4-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="384b4-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="384b4-117">Parent Elements</span></span>  
  
|<span data-ttu-id="384b4-118">**Öğesi**</span><span class="sxs-lookup"><span data-stu-id="384b4-118">**Element**</span></span>|<span data-ttu-id="384b4-119">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="384b4-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="384b4-120">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="384b4-120">defaultProxy</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|<span data-ttu-id="384b4-121">Köprü Metni Aktarım Protokolü (HTTP) proxy sunucusu yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="384b4-121">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="384b4-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="384b4-122">Remarks</span></span>  
 <span data-ttu-id="384b4-123">`module` Öğesi kaydeder uygulayan proxy sınıflar <xref:System.Net.IWebProxy> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="384b4-123">The `module` element registers proxy classes that implement the <xref:System.Net.IWebProxy> interface.</span></span> <span data-ttu-id="384b4-124">Proxy sınıfı kaydettikten sonra `module` desteklenen proxy üzerinden bilgi istemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="384b4-124">After registering the proxy class, `module` can be used to request information through the supported proxy.</span></span>  
  
 <span data-ttu-id="384b4-125">Değeri `type` modülün sınıfı adı ve onun karşılık gelen dinamik bağlantı kitaplığı (DLL), ad özniteliği olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="384b4-125">The value for the `type` attribute should be the class name of the module and the name of its corresponding Dynamic Link Library (DLL).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="384b4-126">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="384b4-126">Configuration Files</span></span>  
 <span data-ttu-id="384b4-127">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="384b4-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="384b4-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="384b4-128">Example</span></span>  
 <span data-ttu-id="384b4-129">Aşağıdaki örnek, bir özel proxy sınıfı kaydeder.</span><span class="sxs-lookup"><span data-stu-id="384b4-129">The following example registers a custom proxy class.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="384b4-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="384b4-130">See Also</span></span>  
 <xref:System.Net.IWebProxy?displayProperty=nameWithType>  
 [<span data-ttu-id="384b4-131">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="384b4-131">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
