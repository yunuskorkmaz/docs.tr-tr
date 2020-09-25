---
title: <PreferComInsteadOfManagedRemoting> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- <PreferComInsteadOfManagedRemoting> element
- PreferComInsteadOfManagedRemoting element
ms.assetid: a279a42a-c415-4e79-88cf-64244ebda613
ms.openlocfilehash: 2fb0d94f91d28f9d9d4f247411d273f786f7b63b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91195291"
---
# <a name="prefercominsteadofmanagedremoting-element"></a><span data-ttu-id="4cac3-102">\<PreferComInsteadOfManagedRemoting> Öğesi</span><span class="sxs-lookup"><span data-stu-id="4cac3-102">\<PreferComInsteadOfManagedRemoting> Element</span></span>

<span data-ttu-id="4cac3-103">Çalışma zamanının, uygulama etki alanı sınırları genelinde tüm çağrılar için uzaktan iletişim yerine COM birlikte çalışabilme kullanıp kullanmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4cac3-103">Specifies whether the runtime will use COM interop instead of remoting for all calls across application domain boundaries.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<PreferComInsteadOfManagedRemoting>**  
  
## <a name="syntax"></a><span data-ttu-id="4cac3-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="4cac3-104">Syntax</span></span>  
  
```xml  
<PreferComInsteadOfManagedRemoting enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4cac3-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4cac3-105">Attributes and Elements</span></span>  

 <span data-ttu-id="4cac3-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4cac3-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4cac3-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4cac3-107">Attributes</span></span>  
  
|<span data-ttu-id="4cac3-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4cac3-108">Attribute</span></span>|<span data-ttu-id="4cac3-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4cac3-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="4cac3-110">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="4cac3-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="4cac3-111">Çalışma zamanının, uygulama etki alanı sınırları arasında uzaktan iletişim yerine COM birlikte çalışabilirliğine sahip olup olmayacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4cac3-111">Indicates whether the runtime will use COM interop instead of remoting across application domain boundaries.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="4cac3-112">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4cac3-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="4cac3-113">Değer</span><span class="sxs-lookup"><span data-stu-id="4cac3-113">Value</span></span>|<span data-ttu-id="4cac3-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4cac3-114">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="4cac3-115">Çalışma zamanı, uygulama etki alanı sınırları genelinde uzaktan iletişim kullanacaktır.</span><span class="sxs-lookup"><span data-stu-id="4cac3-115">The runtime will use remoting across application domain boundaries.</span></span> <span data-ttu-id="4cac3-116">Bu varsayılan seçenektir.</span><span class="sxs-lookup"><span data-stu-id="4cac3-116">This is the default.</span></span>|  
|`true`|<span data-ttu-id="4cac3-117">Çalışma zamanı, uygulama etki alanı sınırları arasında COM birlikte çalışabilirliği kullanacaktır.</span><span class="sxs-lookup"><span data-stu-id="4cac3-117">The runtime will use COM interop across application domain boundaries.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4cac3-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4cac3-118">Child Elements</span></span>  

 <span data-ttu-id="4cac3-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="4cac3-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4cac3-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4cac3-120">Parent Elements</span></span>  
  
|<span data-ttu-id="4cac3-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="4cac3-121">Element</span></span>|<span data-ttu-id="4cac3-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4cac3-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="4cac3-123">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="4cac3-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="4cac3-124">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="4cac3-124">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4cac3-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4cac3-125">Remarks</span></span>  

 <span data-ttu-id="4cac3-126">`enabled`Özniteliğini öğesine ayarladığınızda `true` , çalışma zamanı aşağıdaki gibi davranır:</span><span class="sxs-lookup"><span data-stu-id="4cac3-126">When you set the `enabled` attribute to `true`, the runtime behaves as follows:</span></span>  
  
- <span data-ttu-id="4cac3-127">Bir [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) ARABIRIMI bir com arabirimi aracılığıyla etki alanına girdiğinde, çalışma zamanı [ımanagementpackbir](../../../unmanaged-api/hosting/imanagedobject-interface.md) arabirim Için [IUnknown:: QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) ' i çağırmaz.</span><span class="sxs-lookup"><span data-stu-id="4cac3-127">The runtime does not call [IUnknown::QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) for an [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) interface when an [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) interface enters the domain through a COM interface.</span></span> <span data-ttu-id="4cac3-128">Bunun yerine, nesne etrafında bir [çalışma zamanı çağrılabilir sarmalayıcı](../../../../standard/native-interop/runtime-callable-wrapper.md) (RCW) oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4cac3-128">Instead, it constructs a [Runtime Callable Wrapper](../../../../standard/native-interop/runtime-callable-wrapper.md) (RCW) around the object.</span></span>  
  
- <span data-ttu-id="4cac3-129">Çalışma zamanı, `QueryInterface` Bu etki alanında oluşturulan herhangi bir [com çağrılabilir sarmalayıcı](../../../../standard/native-interop/com-callable-wrapper.md) (CCW) Için bir [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) arabirimi çağrısı aldığında E_NOINTERFACE döndürür.</span><span class="sxs-lookup"><span data-stu-id="4cac3-129">The runtime returns E_NOINTERFACE when it receives a `QueryInterface` call for an [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) interface for any [COM Callable Wrapper](../../../../standard/native-interop/com-callable-wrapper.md) (CCW) that has been created in this domain.</span></span>  
  
 <span data-ttu-id="4cac3-130">Bu iki davranış, uygulama etki alanı sınırları genelinde yönetilen nesneler arasındaki tüm COM arabirimleri arasında tüm çağrıların, uzaktan iletişim yerine COM ve COM birlikte çalışabilirliği kullanmasını sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="4cac3-130">These two behaviors ensure that all calls over COM interfaces between managed objects across application domain boundaries use COM and COM interop instead of remoting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4cac3-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="4cac3-131">Example</span></span>  

 <span data-ttu-id="4cac3-132">Aşağıdaki örnek, çalışma zamanının yalıtım sınırları genelinde COM birlikte çalışabilirliği kullanması gerektiğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="4cac3-132">The following example shows how to specify that the runtime should use COM interop across isolation boundaries:</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <PreferComInsteadOfManagedRemoting enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4cac3-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4cac3-133">See also</span></span>

- [<span data-ttu-id="4cac3-134">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="4cac3-134">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="4cac3-135">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="4cac3-135">Configuration File Schema</span></span>](../index.md)
