---
title: <PreferComInsteadOfManagedRemoting> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- <PreferComInsteadOfManagedRemoting> element
- PreferComInsteadOfManagedRemoting element
ms.assetid: a279a42a-c415-4e79-88cf-64244ebda613
ms.openlocfilehash: 1376df4efd56734f2b8da9bd76033afcce8a285b
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452259"
---
# <a name="prefercominsteadofmanagedremoting-element"></a><span data-ttu-id="27af5-102">\<Prefercomınsteadofmanagedremoting > öğesi</span><span class="sxs-lookup"><span data-stu-id="27af5-102">\<PreferComInsteadOfManagedRemoting> Element</span></span>
<span data-ttu-id="27af5-103">Çalışma zamanının, uygulama etki alanı sınırları genelinde tüm çağrılar için uzaktan iletişim yerine COM birlikte çalışabilme kullanıp kullanmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="27af5-103">Specifies whether the runtime will use COM interop instead of remoting for all calls across application domain boundaries.</span></span>  
  
<span data-ttu-id="27af5-104">[ **\<yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="27af5-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="27af5-105">&nbsp;&nbsp;[ **\<çalışma zamanı >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="27af5-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="27af5-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<PreferComInsteadOfManagedRemoting >**</span><span class="sxs-lookup"><span data-stu-id="27af5-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<PreferComInsteadOfManagedRemoting>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27af5-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="27af5-107">Syntax</span></span>  
  
```xml  
<PreferComInsteadOfManagedRemoting enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="27af5-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="27af5-108">Attributes and Elements</span></span>  
 <span data-ttu-id="27af5-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="27af5-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="27af5-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="27af5-110">Attributes</span></span>  
  
|<span data-ttu-id="27af5-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="27af5-111">Attribute</span></span>|<span data-ttu-id="27af5-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="27af5-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="27af5-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="27af5-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="27af5-114">Çalışma zamanının, uygulama etki alanı sınırları arasında uzaktan iletişim yerine COM birlikte çalışabilirliğine sahip olup olmayacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="27af5-114">Indicates whether the runtime will use COM interop instead of remoting across application domain boundaries.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="27af5-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="27af5-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="27af5-116">Değer</span><span class="sxs-lookup"><span data-stu-id="27af5-116">Value</span></span>|<span data-ttu-id="27af5-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="27af5-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="27af5-118">Çalışma zamanı, uygulama etki alanı sınırları genelinde uzaktan iletişim kullanacaktır.</span><span class="sxs-lookup"><span data-stu-id="27af5-118">The runtime will use remoting across application domain boundaries.</span></span> <span data-ttu-id="27af5-119">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="27af5-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="27af5-120">Çalışma zamanı, uygulama etki alanı sınırları arasında COM birlikte çalışabilirliği kullanacaktır.</span><span class="sxs-lookup"><span data-stu-id="27af5-120">The runtime will use COM interop across application domain boundaries.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="27af5-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="27af5-121">Child Elements</span></span>  
 <span data-ttu-id="27af5-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="27af5-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="27af5-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="27af5-123">Parent Elements</span></span>  
  
|<span data-ttu-id="27af5-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="27af5-124">Element</span></span>|<span data-ttu-id="27af5-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="27af5-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="27af5-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="27af5-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="27af5-127">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="27af5-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="27af5-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="27af5-128">Remarks</span></span>  
 <span data-ttu-id="27af5-129">`enabled` özniteliğini `true`olarak ayarladığınızda, çalışma zamanı aşağıdaki gibi davranır:</span><span class="sxs-lookup"><span data-stu-id="27af5-129">When you set the `enabled` attribute to `true`, the runtime behaves as follows:</span></span>  
  
- <span data-ttu-id="27af5-130">Bir [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) ARABIRIMI bir com arabirimi aracılığıyla etki alanına girdiğinde, çalışma zamanı [ımanagementpackbir](../../../unmanaged-api/hosting/imanagedobject-interface.md) arabirim Için [IUnknown:: QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) ' i çağırmaz.</span><span class="sxs-lookup"><span data-stu-id="27af5-130">The runtime does not call [IUnknown::QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) for an [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) interface when an [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) interface enters the domain through a COM interface.</span></span> <span data-ttu-id="27af5-131">Bunun yerine, nesne etrafında bir [çalışma zamanı çağrılabilir sarmalayıcı](../../../../standard/native-interop/runtime-callable-wrapper.md) (RCW) oluşturur.</span><span class="sxs-lookup"><span data-stu-id="27af5-131">Instead, it constructs a [Runtime Callable Wrapper](../../../../standard/native-interop/runtime-callable-wrapper.md) (RCW) around the object.</span></span>  
  
- <span data-ttu-id="27af5-132">Çalışma zamanı, bu etki alanında oluşturulan herhangi bir [com çağrılabilir sarmalayıcı](../../../../standard/native-interop/com-callable-wrapper.md) (CCW) Için bir [ımanagementpackınterface](../../../unmanaged-api/hosting/imanagedobject-interface.md) arabirimi için bir `QueryInterface` çağrısı aldığında E_NOINTERFACE döndürür.</span><span class="sxs-lookup"><span data-stu-id="27af5-132">The runtime returns E_NOINTERFACE when it receives a `QueryInterface` call for an [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) interface for any [COM Callable Wrapper](../../../../standard/native-interop/com-callable-wrapper.md) (CCW) that has been created in this domain.</span></span>  
  
 <span data-ttu-id="27af5-133">Bu iki davranış, uygulama etki alanı sınırları genelinde yönetilen nesneler arasındaki tüm COM arabirimleri arasında tüm çağrıların, uzaktan iletişim yerine COM ve COM birlikte çalışabilirliği kullanmasını sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="27af5-133">These two behaviors ensure that all calls over COM interfaces between managed objects across application domain boundaries use COM and COM interop instead of remoting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="27af5-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="27af5-134">Example</span></span>  
 <span data-ttu-id="27af5-135">Aşağıdaki örnek, çalışma zamanının yalıtım sınırları genelinde COM birlikte çalışabilirliği kullanması gerektiğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="27af5-135">The following example shows how to specify that the runtime should use COM interop across isolation boundaries:</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <PreferComInsteadOfManagedRemoting enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="27af5-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="27af5-136">See also</span></span>

- [<span data-ttu-id="27af5-137">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="27af5-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="27af5-138">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="27af5-138">Configuration File Schema</span></span>](../index.md)
