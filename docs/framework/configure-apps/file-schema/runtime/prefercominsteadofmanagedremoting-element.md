---
title: <PreferComInsteadOfManagedRemoting> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- <PreferComInsteadOfManagedRemoting> element
- PreferComInsteadOfManagedRemoting element
ms.assetid: a279a42a-c415-4e79-88cf-64244ebda613
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f143429c1f579ae98a03fd69a8cf3dcdd26ad2c2
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55260374"
---
# <a name="prefercominsteadofmanagedremoting-element"></a><span data-ttu-id="39546-102">\<Prefercomınsteadofmanagedremoting > öğesi</span><span class="sxs-lookup"><span data-stu-id="39546-102">\<PreferComInsteadOfManagedRemoting> Element</span></span>
<span data-ttu-id="39546-103">Çalışma zamanı COM birlikte çalışma remoting yerine tüm çağrıları için uygulama etki alanı sınırlarında kullanıp kullanmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="39546-103">Specifies whether the runtime will use COM interop instead of remoting for all calls across application domain boundaries.</span></span>  
  
 <span data-ttu-id="39546-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="39546-104">\<configuration></span></span>  
<span data-ttu-id="39546-105">\<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="39546-105">\<runtime></span></span>  
<span data-ttu-id="39546-106">\<Prefercomınsteadofmanagedremoting ></span><span class="sxs-lookup"><span data-stu-id="39546-106">\<PreferComInsteadOfManagedRemoting></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39546-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="39546-107">Syntax</span></span>  
  
```xml  
<PreferComInsteadOfManagedRemoting enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="39546-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="39546-108">Attributes and Elements</span></span>  
 <span data-ttu-id="39546-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="39546-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="39546-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="39546-110">Attributes</span></span>  
  
|<span data-ttu-id="39546-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="39546-111">Attribute</span></span>|<span data-ttu-id="39546-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="39546-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="39546-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="39546-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="39546-114">Çalışma zamanı COM birlikte çalışma remoting yerine uygulama etki alanı sınırlarında kullanıp kullanmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="39546-114">Indicates whether the runtime will use COM interop instead of remoting across application domain boundaries.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="39546-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="39546-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="39546-116">Değer</span><span class="sxs-lookup"><span data-stu-id="39546-116">Value</span></span>|<span data-ttu-id="39546-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="39546-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="39546-118">Çalışma zamanı, uygulama etki alanı sınırları uzaktan iletişim kullanır.</span><span class="sxs-lookup"><span data-stu-id="39546-118">The runtime will use remoting across application domain boundaries.</span></span> <span data-ttu-id="39546-119">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="39546-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="39546-120">Çalışma zamanı, uygulama etki alanı sınırlarında COM birlikte çalışma kullanır.</span><span class="sxs-lookup"><span data-stu-id="39546-120">The runtime will use COM interop across application domain boundaries.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="39546-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="39546-121">Child Elements</span></span>  
 <span data-ttu-id="39546-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="39546-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="39546-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="39546-123">Parent Elements</span></span>  
  
|<span data-ttu-id="39546-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="39546-124">Element</span></span>|<span data-ttu-id="39546-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="39546-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="39546-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="39546-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="39546-127">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="39546-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="39546-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="39546-128">Remarks</span></span>  
 <span data-ttu-id="39546-129">Ayarladığınızda `enabled` özniteliğini `true`, çalışma zamanı gibi davranır:</span><span class="sxs-lookup"><span data-stu-id="39546-129">When you set the `enabled` attribute to `true`, the runtime behaves as follows:</span></span>  
  
-   <span data-ttu-id="39546-130">Çalışma zamanı arama [IUnknown::QueryInterface](https://go.microsoft.com/fwlink/?LinkID=144867) için bir [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md) arabirimini şu durumlarda bir [IUnknown](https://go.microsoft.com/fwlink/?LinkId=148003) arabirim bir COM arabirimi üzerinden etki alanına girer.</span><span class="sxs-lookup"><span data-stu-id="39546-130">The runtime does not call [IUnknown::QueryInterface](https://go.microsoft.com/fwlink/?LinkID=144867) for an [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md) interface when an [IUnknown](https://go.microsoft.com/fwlink/?LinkId=148003) interface enters the domain through a COM interface.</span></span> <span data-ttu-id="39546-131">Bunun yerine, oluşturur bir [çalışma zamanı çağrılabilir sarmalayıcı](../../../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) nesne çevresinde.</span><span class="sxs-lookup"><span data-stu-id="39546-131">Instead, it constructs a [Runtime Callable Wrapper](../../../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) around the object.</span></span>  
  
-   <span data-ttu-id="39546-132">Aldığında, çalışma zamanı e_noınterface döndürür bir `QueryInterface` çağrısı bir [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md) herhangi bir arabirimdeki [COM çağrılabilir sarmalayıcısı](../../../../../docs/framework/interop/com-callable-wrapper.md) (CCW) bu etki alanında oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="39546-132">The runtime returns E_NOINTERFACE when it receives a `QueryInterface` call for an [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md) interface for any [COM Callable Wrapper](../../../../../docs/framework/interop/com-callable-wrapper.md) (CCW) that has been created in this domain.</span></span>  
  
 <span data-ttu-id="39546-133">Bu iki davranışları uygulama etki alanı sınırları kullanımı COM üzerinden yönetilen nesneleri ve COM birlikte çalışma remoting yerine arasındaki tüm çağrıları üzerinden COM arabirimleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="39546-133">These two behaviors ensure that all calls over COM interfaces between managed objects across application domain boundaries use COM and COM interop instead of remoting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="39546-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="39546-134">Example</span></span>  
 <span data-ttu-id="39546-135">Aşağıdaki örnek çalışma zamanı COM kullanması gerektiğini belirtmek yalıtım sınırları arasında birlikte çalışma gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="39546-135">The following example shows how to specify that the runtime should use COM interop across isolation boundaries:</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <PreferComInsteadOfManagedRemoting enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="39546-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="39546-136">See also</span></span>
- [<span data-ttu-id="39546-137">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="39546-137">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="39546-138">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="39546-138">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
