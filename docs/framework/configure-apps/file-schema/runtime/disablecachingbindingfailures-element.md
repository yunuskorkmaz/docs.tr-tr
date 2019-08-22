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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ba74907e2f6fc2ca14e12a24113fa7654c9b967e
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663794"
---
# <a name="disablecachingbindingfailures-element"></a><span data-ttu-id="39553-102">\<Disablecachingbindinghatalarıyla > öğesi</span><span class="sxs-lookup"><span data-stu-id="39553-102">\<disableCachingBindingFailures> Element</span></span>
<span data-ttu-id="39553-103">Derleme yoklama tarafından bulunamadığı için oluşan bağlama hatalarının önbelleğe alınmasının devre dışı bırakılıp başlatılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="39553-103">Specifies whether to disable the caching of binding failures that occur because the assembly was not found by probing.</span></span>  
  
 <span data-ttu-id="39553-104">\<Yapılandırma > öğesi</span><span class="sxs-lookup"><span data-stu-id="39553-104">\<configuration> Element</span></span>  
<span data-ttu-id="39553-105">\<çalışma zamanı > öğesi</span><span class="sxs-lookup"><span data-stu-id="39553-105">\<runtime> Element</span></span>  
<span data-ttu-id="39553-106">\<Disablecachingbindinghatalarıyla ></span><span class="sxs-lookup"><span data-stu-id="39553-106">\<disableCachingBindingFailures></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39553-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="39553-107">Syntax</span></span>  
  
```xml  
<disableCachingBindingFailures enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="39553-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="39553-108">Attributes and Elements</span></span>  
 <span data-ttu-id="39553-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="39553-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="39553-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="39553-110">Attributes</span></span>  
  
|<span data-ttu-id="39553-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="39553-111">Attribute</span></span>|<span data-ttu-id="39553-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="39553-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="39553-113">etkinletir</span><span class="sxs-lookup"><span data-stu-id="39553-113">enabled</span></span>|<span data-ttu-id="39553-114">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="39553-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="39553-115">Derleme yoklama tarafından bulunamadığı için oluşan bağlama hatalarının önbelleğe alınmasının devre dışı bırakılıp başlatılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="39553-115">Specifies whether to disable the caching of binding failures that occur because the assembly was not found by probing.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="39553-116">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="39553-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="39553-117">Değer</span><span class="sxs-lookup"><span data-stu-id="39553-117">Value</span></span>|<span data-ttu-id="39553-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="39553-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="39553-119">0</span><span class="sxs-lookup"><span data-stu-id="39553-119">0</span></span>|<span data-ttu-id="39553-120">Derleme yoklama tarafından bulunamadığı için oluşan bağlama hatalarının önbelleğe alınmasını devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="39553-120">Do not disable the caching of binding failures that occur because the assembly was not found by probing.</span></span> <span data-ttu-id="39553-121">Bu, .NET Framework sürüm 2,0 ' den başlayarak varsayılan bağlama davranışıdır.</span><span class="sxs-lookup"><span data-stu-id="39553-121">This is the default binding behavior starting with the .NET Framework version 2.0.</span></span>|  
|<span data-ttu-id="39553-122">1\.</span><span class="sxs-lookup"><span data-stu-id="39553-122">1</span></span>|<span data-ttu-id="39553-123">Derleme yoklama tarafından bulunamadığı için oluşan bağlama hatalarının önbelleğe alınmasını devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="39553-123">Disable the caching of binding failures that occur because the assembly was not found by probing.</span></span> <span data-ttu-id="39553-124">Bu ayar 1,1 .NET Framework sürümünün bağlama davranışına geri döner.</span><span class="sxs-lookup"><span data-stu-id="39553-124">This setting reverts to the binding behavior of the .NET Framework version 1.1.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="39553-125">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="39553-125">Child Elements</span></span>  
 <span data-ttu-id="39553-126">Yok.</span><span class="sxs-lookup"><span data-stu-id="39553-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="39553-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="39553-127">Parent Elements</span></span>  
  
|<span data-ttu-id="39553-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="39553-128">Element</span></span>|<span data-ttu-id="39553-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="39553-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="39553-130">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="39553-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="39553-131">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="39553-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="39553-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="39553-132">Remarks</span></span>  
 <span data-ttu-id="39553-133">.NET Framework sürüm 2,0 ' den başlayarak, derlemelerin yüklenmesi için varsayılan davranış tüm bağlama ve yükleme hatalarının önbelleğe alınarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="39553-133">Starting with the .NET Framework version 2.0, the default behavior for loading assemblies is to cache all binding and loading failures.</span></span> <span data-ttu-id="39553-134">Diğer bir deyişle, bir derlemeyi yükleme girişimi başarısız olursa, derlemeyi bulmaya gerek kalmadan, aynı derlemeyi yükleme isteklerinin sonraki istekleri hemen başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="39553-134">That is, if an attempt to load an assembly fails, subsequent requests to load the same assembly fail immediately, without any attempt to locate the assembly.</span></span> <span data-ttu-id="39553-135">Bu öğe, derleme yoklama yolunda bulunamadığı için oluşan bağlama hatalarının varsayılan davranışını devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="39553-135">This element disables that default behavior for binding failures that occur because the assembly could not be found in the probing path.</span></span> <span data-ttu-id="39553-136">Bu arızalar <xref:System.IO.FileNotFoundException>oluşturur.</span><span class="sxs-lookup"><span data-stu-id="39553-136">These failures throw <xref:System.IO.FileNotFoundException>.</span></span>  
  
 <span data-ttu-id="39553-137">Bazı bağlama ve yükleme hatalarının bu öğeden etkilenmemesi ve her zaman önbelleğe alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="39553-137">Some binding and loading failures are not affected by this element, and are always cached.</span></span> <span data-ttu-id="39553-138">Bu arızalar, derlemenin bulunduğu ancak yüklenemediği için oluşur.</span><span class="sxs-lookup"><span data-stu-id="39553-138">These failures occur because the assembly was found but could not be loaded.</span></span> <span data-ttu-id="39553-139">Ya da <xref:System.BadImageFormatException> <xref:System.IO.FileLoadException>oluşturur.</span><span class="sxs-lookup"><span data-stu-id="39553-139">They throw <xref:System.BadImageFormatException> or <xref:System.IO.FileLoadException>.</span></span> <span data-ttu-id="39553-140">Aşağıdaki liste, bu hataların bazı örneklerini içerir.</span><span class="sxs-lookup"><span data-stu-id="39553-140">The following list includes some examples of such failures.</span></span>  
  
- <span data-ttu-id="39553-141">Bir dosyayı yüklemeye çalışırsanız, geçerli bir derleme değilse, bozuk dosya doğru derlemeyle değiştirilse bile derlemeyi yükleme girişimleri başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="39553-141">If you attempt to load a file is not a valid assembly, subsequent attempts to load the assembly will fail even if the bad file is replaced with the correct assembly.</span></span>  
  
- <span data-ttu-id="39553-142">Dosya sistemi tarafından kilitlenen bir derlemeyi yüklemeye çalışırsanız, derlemeyi yükleme girişimleri, derleme dosya sistemi tarafından serbest bırakıldıktan sonra bile başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="39553-142">If you attempt to load an assembly that is locked by the file system, subsequent attempts to load the assembly will fail even after the assembly is released by the file system.</span></span>  
  
- <span data-ttu-id="39553-143">Yüklemeye çalıştığınız derlemenin bir veya daha fazla sürümü yoklama yolunda ise, ancak istediğiniz özel sürüm bunlar arasında değilse, doğru sürüm yoklama yoluna taşınsa bile bu sürümü yüklemeye yönelik sonraki girişimler başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="39553-143">If one or more versions of the assembly that you are attempting to load is in the probing path, but the specific version you are requesting is not among them, subsequent attempts to load that version will fail even if the correct version is moved into the probing path.</span></span>  
  
## <a name="example"></a><span data-ttu-id="39553-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="39553-144">Example</span></span>  
 <span data-ttu-id="39553-145">Aşağıdaki örnek, derleme yoklama tarafından bulunamadığı için oluşan derleme bağlama hatalarının önbelleğe alınmasının nasıl devre dışı bırakılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="39553-145">The following example shows how to disable the caching of assembly binding failures that occur because the assembly was not found by probing.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableCachingBindingFailures enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="39553-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="39553-146">See also</span></span>

- [<span data-ttu-id="39553-147">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="39553-147">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="39553-148">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="39553-148">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="39553-149">Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="39553-149">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
