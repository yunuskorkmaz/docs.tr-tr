---
description: 'Daha fazla bilgi edinin: <disableCachingBindingFailures> öğesi'
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
ms.openlocfilehash: b1f36f6a8fc7c78a0dc90ecc78ad725b677fdf40
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787116"
---
# <a name="disablecachingbindingfailures-element"></a><span data-ttu-id="cb7dd-103">\<disableCachingBindingFailures> Öğesi</span><span class="sxs-lookup"><span data-stu-id="cb7dd-103">\<disableCachingBindingFailures> Element</span></span>

<span data-ttu-id="cb7dd-104">Derleme yoklama tarafından bulunamadığı için oluşan bağlama hatalarının önbelleğe alınmasının devre dışı bırakılıp başlatılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="cb7dd-104">Specifies whether to disable the caching of binding failures that occur because the assembly was not found by probing.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<disableCachingBindingFailures>**  
  
## <a name="syntax"></a><span data-ttu-id="cb7dd-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="cb7dd-105">Syntax</span></span>  
  
```xml  
<disableCachingBindingFailures enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cb7dd-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="cb7dd-106">Attributes and Elements</span></span>  

 <span data-ttu-id="cb7dd-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cb7dd-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cb7dd-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="cb7dd-108">Attributes</span></span>  
  
|<span data-ttu-id="cb7dd-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="cb7dd-109">Attribute</span></span>|<span data-ttu-id="cb7dd-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cb7dd-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cb7dd-111">enabled</span><span class="sxs-lookup"><span data-stu-id="cb7dd-111">enabled</span></span>|<span data-ttu-id="cb7dd-112">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="cb7dd-112">Required attribute.</span></span><br /><br /> <span data-ttu-id="cb7dd-113">Derleme yoklama tarafından bulunamadığı için oluşan bağlama hatalarının önbelleğe alınmasının devre dışı bırakılıp başlatılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="cb7dd-113">Specifies whether to disable the caching of binding failures that occur because the assembly was not found by probing.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="cb7dd-114">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="cb7dd-114">enabled Attribute</span></span>  
  
|<span data-ttu-id="cb7dd-115">Değer</span><span class="sxs-lookup"><span data-stu-id="cb7dd-115">Value</span></span>|<span data-ttu-id="cb7dd-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cb7dd-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cb7dd-117">0</span><span class="sxs-lookup"><span data-stu-id="cb7dd-117">0</span></span>|<span data-ttu-id="cb7dd-118">Derleme yoklama tarafından bulunamadığı için oluşan bağlama hatalarının önbelleğe alınmasını devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="cb7dd-118">Do not disable the caching of binding failures that occur because the assembly was not found by probing.</span></span> <span data-ttu-id="cb7dd-119">Bu, .NET Framework sürüm 2,0 ' den başlayarak varsayılan bağlama davranışıdır.</span><span class="sxs-lookup"><span data-stu-id="cb7dd-119">This is the default binding behavior starting with the .NET Framework version 2.0.</span></span>|  
|<span data-ttu-id="cb7dd-120">1</span><span class="sxs-lookup"><span data-stu-id="cb7dd-120">1</span></span>|<span data-ttu-id="cb7dd-121">Derleme yoklama tarafından bulunamadığı için oluşan bağlama hatalarının önbelleğe alınmasını devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="cb7dd-121">Disable the caching of binding failures that occur because the assembly was not found by probing.</span></span> <span data-ttu-id="cb7dd-122">Bu ayar 1,1 .NET Framework sürümünün bağlama davranışına geri döner.</span><span class="sxs-lookup"><span data-stu-id="cb7dd-122">This setting reverts to the binding behavior of the .NET Framework version 1.1.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cb7dd-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="cb7dd-123">Child Elements</span></span>  

 <span data-ttu-id="cb7dd-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="cb7dd-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cb7dd-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="cb7dd-125">Parent Elements</span></span>  
  
|<span data-ttu-id="cb7dd-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="cb7dd-126">Element</span></span>|<span data-ttu-id="cb7dd-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cb7dd-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="cb7dd-128">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="cb7dd-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="cb7dd-129">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="cb7dd-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cb7dd-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cb7dd-130">Remarks</span></span>  

 <span data-ttu-id="cb7dd-131">.NET Framework sürüm 2,0 ' den başlayarak, derlemelerin yüklenmesi için varsayılan davranış tüm bağlama ve yükleme hatalarının önbelleğe alınarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="cb7dd-131">Starting with the .NET Framework version 2.0, the default behavior for loading assemblies is to cache all binding and loading failures.</span></span> <span data-ttu-id="cb7dd-132">Diğer bir deyişle, bir derlemeyi yükleme girişimi başarısız olursa, derlemeyi bulmaya gerek kalmadan, aynı derlemeyi yükleme isteklerinin sonraki istekleri hemen başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="cb7dd-132">That is, if an attempt to load an assembly fails, subsequent requests to load the same assembly fail immediately, without any attempt to locate the assembly.</span></span> <span data-ttu-id="cb7dd-133">Bu öğe, derleme yoklama yolunda bulunamadığı için oluşan bağlama hatalarının varsayılan davranışını devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="cb7dd-133">This element disables that default behavior for binding failures that occur because the assembly could not be found in the probing path.</span></span> <span data-ttu-id="cb7dd-134">Bu arızalar oluşturur <xref:System.IO.FileNotFoundException> .</span><span class="sxs-lookup"><span data-stu-id="cb7dd-134">These failures throw <xref:System.IO.FileNotFoundException>.</span></span>  
  
 <span data-ttu-id="cb7dd-135">Bazı bağlama ve yükleme hatalarının bu öğeden etkilenmemesi ve her zaman önbelleğe alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="cb7dd-135">Some binding and loading failures are not affected by this element, and are always cached.</span></span> <span data-ttu-id="cb7dd-136">Bu arızalar, derlemenin bulunduğu ancak yüklenemediği için oluşur.</span><span class="sxs-lookup"><span data-stu-id="cb7dd-136">These failures occur because the assembly was found but could not be loaded.</span></span> <span data-ttu-id="cb7dd-137"><xref:System.BadImageFormatException>Ya da oluşturur <xref:System.IO.FileLoadException> .</span><span class="sxs-lookup"><span data-stu-id="cb7dd-137">They throw <xref:System.BadImageFormatException> or <xref:System.IO.FileLoadException>.</span></span> <span data-ttu-id="cb7dd-138">Aşağıdaki liste, bu hataların bazı örneklerini içerir.</span><span class="sxs-lookup"><span data-stu-id="cb7dd-138">The following list includes some examples of such failures.</span></span>  
  
- <span data-ttu-id="cb7dd-139">Bir dosyayı yüklemeye çalışırsanız, geçerli bir derleme değilse, bozuk dosya doğru derlemeyle değiştirilse bile derlemeyi yükleme girişimleri başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="cb7dd-139">If you attempt to load a file is not a valid assembly, subsequent attempts to load the assembly will fail even if the bad file is replaced with the correct assembly.</span></span>  
  
- <span data-ttu-id="cb7dd-140">Dosya sistemi tarafından kilitlenen bir derlemeyi yüklemeye çalışırsanız, derlemeyi yükleme girişimleri, derleme dosya sistemi tarafından serbest bırakıldıktan sonra bile başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="cb7dd-140">If you attempt to load an assembly that is locked by the file system, subsequent attempts to load the assembly will fail even after the assembly is released by the file system.</span></span>  
  
- <span data-ttu-id="cb7dd-141">Yüklemeye çalıştığınız derlemenin bir veya daha fazla sürümü yoklama yolunda ise, ancak istediğiniz özel sürüm bunlar arasında değilse, doğru sürüm yoklama yoluna taşınsa bile bu sürümü yüklemeye yönelik sonraki girişimler başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="cb7dd-141">If one or more versions of the assembly that you are attempting to load is in the probing path, but the specific version you are requesting is not among them, subsequent attempts to load that version will fail even if the correct version is moved into the probing path.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb7dd-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="cb7dd-142">Example</span></span>  

 <span data-ttu-id="cb7dd-143">Aşağıdaki örnek, derleme yoklama tarafından bulunamadığı için oluşan derleme bağlama hatalarının önbelleğe alınmasının nasıl devre dışı bırakılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="cb7dd-143">The following example shows how to disable the caching of assembly binding failures that occur because the assembly was not found by probing.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableCachingBindingFailures enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="cb7dd-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cb7dd-144">See also</span></span>

- [<span data-ttu-id="cb7dd-145">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="cb7dd-145">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="cb7dd-146">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="cb7dd-146">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="cb7dd-147">Çalışma Zamanının Derlemelerin Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="cb7dd-147">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
