---
title: <disableCachingBindingFailures> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#disableCachingBindingFailures
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/disableCachingBindingFailures
helpviewer_keywords:
- assemblies [.NET Framework],caching binding failures
- caching assembly binding failures
- <disableCachingBindingFailures> element
- disableCachingBindingFailures element
ms.assetid: bf598873-83b7-48de-8955-00b0504fbad0
ms.openlocfilehash: c9e608bfd54b641564a9095076455e10dd8653fb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91176129"
---
# <a name="disablecachingbindingfailures-element"></a><span data-ttu-id="4b45c-102">\<disableCachingBindingFailures> Öğesi</span><span class="sxs-lookup"><span data-stu-id="4b45c-102">\<disableCachingBindingFailures> Element</span></span>

<span data-ttu-id="4b45c-103">Derleme yoklama tarafından bulunamadığı için oluşan bağlama hatalarının önbelleğe alınmasının devre dışı bırakılıp başlatılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4b45c-103">Specifies whether to disable the caching of binding failures that occur because the assembly was not found by probing.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<disableCachingBindingFailures>**  
  
## <a name="syntax"></a><span data-ttu-id="4b45c-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="4b45c-104">Syntax</span></span>  
  
```xml  
<disableCachingBindingFailures enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4b45c-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4b45c-105">Attributes and Elements</span></span>  

 <span data-ttu-id="4b45c-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4b45c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4b45c-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4b45c-107">Attributes</span></span>  
  
|<span data-ttu-id="4b45c-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4b45c-108">Attribute</span></span>|<span data-ttu-id="4b45c-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4b45c-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4b45c-110">enabled</span><span class="sxs-lookup"><span data-stu-id="4b45c-110">enabled</span></span>|<span data-ttu-id="4b45c-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="4b45c-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="4b45c-112">Derleme yoklama tarafından bulunamadığı için oluşan bağlama hatalarının önbelleğe alınmasının devre dışı bırakılıp başlatılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4b45c-112">Specifies whether to disable the caching of binding failures that occur because the assembly was not found by probing.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="4b45c-113">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4b45c-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="4b45c-114">Değer</span><span class="sxs-lookup"><span data-stu-id="4b45c-114">Value</span></span>|<span data-ttu-id="4b45c-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4b45c-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4b45c-116">0</span><span class="sxs-lookup"><span data-stu-id="4b45c-116">0</span></span>|<span data-ttu-id="4b45c-117">Derleme yoklama tarafından bulunamadığı için oluşan bağlama hatalarının önbelleğe alınmasını devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="4b45c-117">Do not disable the caching of binding failures that occur because the assembly was not found by probing.</span></span> <span data-ttu-id="4b45c-118">Bu, .NET Framework sürüm 2,0 ' den başlayarak varsayılan bağlama davranışıdır.</span><span class="sxs-lookup"><span data-stu-id="4b45c-118">This is the default binding behavior starting with the .NET Framework version 2.0.</span></span>|  
|<span data-ttu-id="4b45c-119">1</span><span class="sxs-lookup"><span data-stu-id="4b45c-119">1</span></span>|<span data-ttu-id="4b45c-120">Derleme yoklama tarafından bulunamadığı için oluşan bağlama hatalarının önbelleğe alınmasını devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="4b45c-120">Disable the caching of binding failures that occur because the assembly was not found by probing.</span></span> <span data-ttu-id="4b45c-121">Bu ayar 1,1 .NET Framework sürümünün bağlama davranışına geri döner.</span><span class="sxs-lookup"><span data-stu-id="4b45c-121">This setting reverts to the binding behavior of the .NET Framework version 1.1.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4b45c-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4b45c-122">Child Elements</span></span>  

 <span data-ttu-id="4b45c-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="4b45c-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4b45c-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4b45c-124">Parent Elements</span></span>  
  
|<span data-ttu-id="4b45c-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="4b45c-125">Element</span></span>|<span data-ttu-id="4b45c-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4b45c-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="4b45c-127">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="4b45c-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="4b45c-128">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="4b45c-128">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4b45c-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4b45c-129">Remarks</span></span>  

 <span data-ttu-id="4b45c-130">.NET Framework sürüm 2,0 ' den başlayarak, derlemelerin yüklenmesi için varsayılan davranış tüm bağlama ve yükleme hatalarının önbelleğe alınarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="4b45c-130">Starting with the .NET Framework version 2.0, the default behavior for loading assemblies is to cache all binding and loading failures.</span></span> <span data-ttu-id="4b45c-131">Diğer bir deyişle, bir derlemeyi yükleme girişimi başarısız olursa, derlemeyi bulmaya gerek kalmadan, aynı derlemeyi yükleme isteklerinin sonraki istekleri hemen başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="4b45c-131">That is, if an attempt to load an assembly fails, subsequent requests to load the same assembly fail immediately, without any attempt to locate the assembly.</span></span> <span data-ttu-id="4b45c-132">Bu öğe, derleme yoklama yolunda bulunamadığı için oluşan bağlama hatalarının varsayılan davranışını devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="4b45c-132">This element disables that default behavior for binding failures that occur because the assembly could not be found in the probing path.</span></span> <span data-ttu-id="4b45c-133">Bu arızalar oluşturur <xref:System.IO.FileNotFoundException> .</span><span class="sxs-lookup"><span data-stu-id="4b45c-133">These failures throw <xref:System.IO.FileNotFoundException>.</span></span>  
  
 <span data-ttu-id="4b45c-134">Bazı bağlama ve yükleme hatalarının bu öğeden etkilenmemesi ve her zaman önbelleğe alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4b45c-134">Some binding and loading failures are not affected by this element, and are always cached.</span></span> <span data-ttu-id="4b45c-135">Bu arızalar, derlemenin bulunduğu ancak yüklenemediği için oluşur.</span><span class="sxs-lookup"><span data-stu-id="4b45c-135">These failures occur because the assembly was found but could not be loaded.</span></span> <span data-ttu-id="4b45c-136"><xref:System.BadImageFormatException>Ya da oluşturur <xref:System.IO.FileLoadException> .</span><span class="sxs-lookup"><span data-stu-id="4b45c-136">They throw <xref:System.BadImageFormatException> or <xref:System.IO.FileLoadException>.</span></span> <span data-ttu-id="4b45c-137">Aşağıdaki liste, bu hataların bazı örneklerini içerir.</span><span class="sxs-lookup"><span data-stu-id="4b45c-137">The following list includes some examples of such failures.</span></span>  
  
- <span data-ttu-id="4b45c-138">Bir dosyayı yüklemeye çalışırsanız, geçerli bir derleme değilse, bozuk dosya doğru derlemeyle değiştirilse bile derlemeyi yükleme girişimleri başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="4b45c-138">If you attempt to load a file is not a valid assembly, subsequent attempts to load the assembly will fail even if the bad file is replaced with the correct assembly.</span></span>  
  
- <span data-ttu-id="4b45c-139">Dosya sistemi tarafından kilitlenen bir derlemeyi yüklemeye çalışırsanız, derlemeyi yükleme girişimleri, derleme dosya sistemi tarafından serbest bırakıldıktan sonra bile başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="4b45c-139">If you attempt to load an assembly that is locked by the file system, subsequent attempts to load the assembly will fail even after the assembly is released by the file system.</span></span>  
  
- <span data-ttu-id="4b45c-140">Yüklemeye çalıştığınız derlemenin bir veya daha fazla sürümü yoklama yolunda ise, ancak istediğiniz özel sürüm bunlar arasında değilse, doğru sürüm yoklama yoluna taşınsa bile bu sürümü yüklemeye yönelik sonraki girişimler başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="4b45c-140">If one or more versions of the assembly that you are attempting to load is in the probing path, but the specific version you are requesting is not among them, subsequent attempts to load that version will fail even if the correct version is moved into the probing path.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b45c-141">Örnek</span><span class="sxs-lookup"><span data-stu-id="4b45c-141">Example</span></span>  

 <span data-ttu-id="4b45c-142">Aşağıdaki örnek, derleme yoklama tarafından bulunamadığı için oluşan derleme bağlama hatalarının önbelleğe alınmasının nasıl devre dışı bırakılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4b45c-142">The following example shows how to disable the caching of assembly binding failures that occur because the assembly was not found by probing.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableCachingBindingFailures enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4b45c-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4b45c-143">See also</span></span>

- [<span data-ttu-id="4b45c-144">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="4b45c-144">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="4b45c-145">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="4b45c-145">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="4b45c-146">Çalışma Zamanının Derlemelerin Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="4b45c-146">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
