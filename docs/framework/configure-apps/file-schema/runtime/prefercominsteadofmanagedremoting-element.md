---
description: 'Daha fazla bilgi edinin: <PreferComInsteadOfManagedRemoting> öğesi'
title: <PreferComInsteadOfManagedRemoting> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- <PreferComInsteadOfManagedRemoting> element
- PreferComInsteadOfManagedRemoting element
ms.assetid: a279a42a-c415-4e79-88cf-64244ebda613
ms.openlocfilehash: b621af9b584d1ea2623ffe5a44f74b5b7bd520e7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782279"
---
# <a name="prefercominsteadofmanagedremoting-element"></a><span data-ttu-id="88018-103">\<PreferComInsteadOfManagedRemoting> Öğesi</span><span class="sxs-lookup"><span data-stu-id="88018-103">\<PreferComInsteadOfManagedRemoting> Element</span></span>

<span data-ttu-id="88018-104">Çalışma zamanının, uygulama etki alanı sınırları genelinde tüm çağrılar için uzaktan iletişim yerine COM birlikte çalışabilme kullanıp kullanmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="88018-104">Specifies whether the runtime will use COM interop instead of remoting for all calls across application domain boundaries.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<PreferComInsteadOfManagedRemoting>**  
  
## <a name="syntax"></a><span data-ttu-id="88018-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="88018-105">Syntax</span></span>  
  
```xml  
<PreferComInsteadOfManagedRemoting enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="88018-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="88018-106">Attributes and Elements</span></span>  

 <span data-ttu-id="88018-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="88018-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="88018-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="88018-108">Attributes</span></span>  
  
|<span data-ttu-id="88018-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="88018-109">Attribute</span></span>|<span data-ttu-id="88018-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="88018-110">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="88018-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="88018-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="88018-112">Çalışma zamanının, uygulama etki alanı sınırları arasında uzaktan iletişim yerine COM birlikte çalışabilirliğine sahip olup olmayacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="88018-112">Indicates whether the runtime will use COM interop instead of remoting across application domain boundaries.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="88018-113">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="88018-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="88018-114">Değer</span><span class="sxs-lookup"><span data-stu-id="88018-114">Value</span></span>|<span data-ttu-id="88018-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="88018-115">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="88018-116">Çalışma zamanı, uygulama etki alanı sınırları genelinde uzaktan iletişim kullanacaktır.</span><span class="sxs-lookup"><span data-stu-id="88018-116">The runtime will use remoting across application domain boundaries.</span></span> <span data-ttu-id="88018-117">Bu varsayılan seçenektir.</span><span class="sxs-lookup"><span data-stu-id="88018-117">This is the default.</span></span>|  
|`true`|<span data-ttu-id="88018-118">Çalışma zamanı, uygulama etki alanı sınırları arasında COM birlikte çalışabilirliği kullanacaktır.</span><span class="sxs-lookup"><span data-stu-id="88018-118">The runtime will use COM interop across application domain boundaries.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="88018-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="88018-119">Child Elements</span></span>  

 <span data-ttu-id="88018-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="88018-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="88018-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="88018-121">Parent Elements</span></span>  
  
|<span data-ttu-id="88018-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="88018-122">Element</span></span>|<span data-ttu-id="88018-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="88018-123">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="88018-124">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="88018-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="88018-125">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="88018-125">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="88018-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="88018-126">Remarks</span></span>  

 <span data-ttu-id="88018-127">`enabled`Özniteliğini öğesine ayarladığınızda `true` , çalışma zamanı aşağıdaki gibi davranır:</span><span class="sxs-lookup"><span data-stu-id="88018-127">When you set the `enabled` attribute to `true`, the runtime behaves as follows:</span></span>  
  
- <span data-ttu-id="88018-128">Bir [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) ARABIRIMI bir com arabirimi aracılığıyla etki alanına girdiğinde, çalışma zamanı [ımanagementpackbir](../../../unmanaged-api/hosting/imanagedobject-interface.md) arabirim Için [IUnknown:: QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) ' i çağırmaz.</span><span class="sxs-lookup"><span data-stu-id="88018-128">The runtime does not call [IUnknown::QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) for an [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) interface when an [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) interface enters the domain through a COM interface.</span></span> <span data-ttu-id="88018-129">Bunun yerine, nesne etrafında bir [çalışma zamanı çağrılabilir sarmalayıcı](../../../../standard/native-interop/runtime-callable-wrapper.md) (RCW) oluşturur.</span><span class="sxs-lookup"><span data-stu-id="88018-129">Instead, it constructs a [Runtime Callable Wrapper](../../../../standard/native-interop/runtime-callable-wrapper.md) (RCW) around the object.</span></span>  
  
- <span data-ttu-id="88018-130">Çalışma zamanı, `QueryInterface` Bu etki alanında oluşturulan herhangi bir [com çağrılabilir sarmalayıcı](../../../../standard/native-interop/com-callable-wrapper.md) (CCW) Için bir [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) arabirimi çağrısı aldığında E_NOINTERFACE döndürür.</span><span class="sxs-lookup"><span data-stu-id="88018-130">The runtime returns E_NOINTERFACE when it receives a `QueryInterface` call for an [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) interface for any [COM Callable Wrapper](../../../../standard/native-interop/com-callable-wrapper.md) (CCW) that has been created in this domain.</span></span>  
  
 <span data-ttu-id="88018-131">Bu iki davranış, uygulama etki alanı sınırları genelinde yönetilen nesneler arasındaki tüm COM arabirimleri arasında tüm çağrıların, uzaktan iletişim yerine COM ve COM birlikte çalışabilirliği kullanmasını sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="88018-131">These two behaviors ensure that all calls over COM interfaces between managed objects across application domain boundaries use COM and COM interop instead of remoting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="88018-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="88018-132">Example</span></span>  

 <span data-ttu-id="88018-133">Aşağıdaki örnek, çalışma zamanının yalıtım sınırları genelinde COM birlikte çalışabilirliği kullanması gerektiğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="88018-133">The following example shows how to specify that the runtime should use COM interop across isolation boundaries:</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <PreferComInsteadOfManagedRemoting enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="88018-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="88018-134">See also</span></span>

- [<span data-ttu-id="88018-135">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="88018-135">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="88018-136">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="88018-136">Configuration File Schema</span></span>](../index.md)
