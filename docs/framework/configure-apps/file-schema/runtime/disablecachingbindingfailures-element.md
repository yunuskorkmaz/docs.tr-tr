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
ms.openlocfilehash: 4893adaf528f1a9ef8fc8eab8027406fd8520cc2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59159282"
---
# <a name="disablecachingbindingfailures-element"></a><span data-ttu-id="10fcd-102">\<disableCachingBindingFailures > öğesi</span><span class="sxs-lookup"><span data-stu-id="10fcd-102">\<disableCachingBindingFailures> Element</span></span>
<span data-ttu-id="10fcd-103">Derleme yoklama işlemi tarafından bulunamadığı için oluşan hataları bağlama önbelleğe alma devre dışı bırakılıp bırakılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="10fcd-103">Specifies whether to disable the caching of binding failures that occur because the assembly was not found by probing.</span></span>  
  
 <span data-ttu-id="10fcd-104">\<Yapılandırma > öğesi</span><span class="sxs-lookup"><span data-stu-id="10fcd-104">\<configuration> Element</span></span>  
<span data-ttu-id="10fcd-105">\<çalışma zamanı > öğesi</span><span class="sxs-lookup"><span data-stu-id="10fcd-105">\<runtime> Element</span></span>  
<span data-ttu-id="10fcd-106">\<disableCachingBindingFailures ></span><span class="sxs-lookup"><span data-stu-id="10fcd-106">\<disableCachingBindingFailures></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10fcd-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="10fcd-107">Syntax</span></span>  
  
```xml  
<disableCachingBindingFailures enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="10fcd-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="10fcd-108">Attributes and Elements</span></span>  
 <span data-ttu-id="10fcd-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="10fcd-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="10fcd-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="10fcd-110">Attributes</span></span>  
  
|<span data-ttu-id="10fcd-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="10fcd-111">Attribute</span></span>|<span data-ttu-id="10fcd-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="10fcd-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="10fcd-113">Etkin</span><span class="sxs-lookup"><span data-stu-id="10fcd-113">enabled</span></span>|<span data-ttu-id="10fcd-114">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="10fcd-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="10fcd-115">Derleme yoklama işlemi tarafından bulunamadığı için oluşan hataları bağlama önbelleğe alma devre dışı bırakılıp bırakılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="10fcd-115">Specifies whether to disable the caching of binding failures that occur because the assembly was not found by probing.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="10fcd-116">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="10fcd-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="10fcd-117">Değer</span><span class="sxs-lookup"><span data-stu-id="10fcd-117">Value</span></span>|<span data-ttu-id="10fcd-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="10fcd-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="10fcd-119">0</span><span class="sxs-lookup"><span data-stu-id="10fcd-119">0</span></span>|<span data-ttu-id="10fcd-120">Derleme yoklama işlemi tarafından bulunamadığı için oluşan hataları bağlama önbelleğe alma devre dışı bırakmayın.</span><span class="sxs-lookup"><span data-stu-id="10fcd-120">Do not disable the caching of binding failures that occur because the assembly was not found by probing.</span></span> <span data-ttu-id="10fcd-121">.NET Framework sürüm 2.0 ile başlayarak varsayılan bağlama davranışı budur.</span><span class="sxs-lookup"><span data-stu-id="10fcd-121">This is the default binding behavior starting with the .NET Framework version 2.0.</span></span>|  
|<span data-ttu-id="10fcd-122">1.</span><span class="sxs-lookup"><span data-stu-id="10fcd-122">1</span></span>|<span data-ttu-id="10fcd-123">Derleme yoklama işlemi tarafından bulunamadığı için oluşan hataları bağlama önbelleğe alma devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="10fcd-123">Disable the caching of binding failures that occur because the assembly was not found by probing.</span></span> <span data-ttu-id="10fcd-124">Bu ayar, .NET Framework sürüm 1.1 bağlama davranışını geri döner.</span><span class="sxs-lookup"><span data-stu-id="10fcd-124">This setting reverts to the binding behavior of the .NET Framework version 1.1.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="10fcd-125">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="10fcd-125">Child Elements</span></span>  
 <span data-ttu-id="10fcd-126">Yok.</span><span class="sxs-lookup"><span data-stu-id="10fcd-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="10fcd-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="10fcd-127">Parent Elements</span></span>  
  
|<span data-ttu-id="10fcd-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="10fcd-128">Element</span></span>|<span data-ttu-id="10fcd-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="10fcd-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="10fcd-130">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="10fcd-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="10fcd-131">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="10fcd-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="10fcd-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="10fcd-132">Remarks</span></span>  
 <span data-ttu-id="10fcd-133">.NET Framework sürüm 2.0 ile başlayarak, tüm bağlama ve yükleme hatalarını önbelleğe almak için derlemeleri yüklemek için varsayılan davranış şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="10fcd-133">Starting with the .NET Framework version 2.0, the default behavior for loading assemblies is to cache all binding and loading failures.</span></span> <span data-ttu-id="10fcd-134">Diğer bir deyişle, bir derlemeyi yüklemek için bir deneme başarısız olursa, aynı derlemenin yüklemek için sonraki istekleri hemen derlemeyi bulmak için her türlü girişim başarısız.</span><span class="sxs-lookup"><span data-stu-id="10fcd-134">That is, if an attempt to load an assembly fails, subsequent requests to load the same assembly fail immediately, without any attempt to locate the assembly.</span></span> <span data-ttu-id="10fcd-135">Bu öğe Derleme yoklama yolu bulunamadı nedeniyle oluşabilecek hataları bağlama için bu varsayılan davranışı devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="10fcd-135">This element disables that default behavior for binding failures that occur because the assembly could not be found in the probing path.</span></span> <span data-ttu-id="10fcd-136">Bu hatalar throw <xref:System.IO.FileNotFoundException>.</span><span class="sxs-lookup"><span data-stu-id="10fcd-136">These failures throw <xref:System.IO.FileNotFoundException>.</span></span>  
  
 <span data-ttu-id="10fcd-137">Bazı bağlama ve yükleme hatalarını bu öğe tarafından etkilenmez ve her zaman önbelleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="10fcd-137">Some binding and loading failures are not affected by this element, and are always cached.</span></span> <span data-ttu-id="10fcd-138">Derleme bulundu, ancak yüklenemedi çünkü bu hatalar oluşur.</span><span class="sxs-lookup"><span data-stu-id="10fcd-138">These failures occur because the assembly was found but could not be loaded.</span></span> <span data-ttu-id="10fcd-139">Oluştururlar <xref:System.BadImageFormatException> veya <xref:System.IO.FileLoadException>.</span><span class="sxs-lookup"><span data-stu-id="10fcd-139">They throw <xref:System.BadImageFormatException> or <xref:System.IO.FileLoadException>.</span></span> <span data-ttu-id="10fcd-140">Aşağıdaki listede, bu tür hataları bazı örnekleri içerir.</span><span class="sxs-lookup"><span data-stu-id="10fcd-140">The following list includes some examples of such failures.</span></span>  
  
-   <span data-ttu-id="10fcd-141">Yüklemeye çalışırsanız, bir dosya geçerli bir derleme değil, hatalı dosya doğru derleme ile değiştirilir bile derlemesini yüklemek için sonraki denemeler başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="10fcd-141">If you attempt to load a file is not a valid assembly, subsequent attempts to load the assembly will fail even if the bad file is replaced with the correct assembly.</span></span>  
  
-   <span data-ttu-id="10fcd-142">Dosya sistemi tarafından kilitlenmiş bir derlemeyi yüklemeye çalışırsanız, derleme bile dosya sistemi tarafından serbest bırakıldıktan sonra derlemeyi yüklemek için sonraki denemeler başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="10fcd-142">If you attempt to load an assembly that is locked by the file system, subsequent attempts to load the assembly will fail even after the assembly is released by the file system.</span></span>  
  
-   <span data-ttu-id="10fcd-143">Araştırma yolu doğru sürümü taşınsa dahi yüklemeye çalıştığınız derlemenin bir veya daha fazla sürümleri olan algılama yolu, ancak istediğiniz belirli bir sürüm bunlar arasında değil, bu sürümü yüklemek için sonraki denemeler başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="10fcd-143">If one or more versions of the assembly that you are attempting to load is in the probing path, but the specific version you are requesting is not among them, subsequent attempts to load that version will fail even if the correct version is moved into the probing path.</span></span>  
  
## <a name="example"></a><span data-ttu-id="10fcd-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="10fcd-144">Example</span></span>  
 <span data-ttu-id="10fcd-145">Aşağıdaki örnek, derleme yoklama işlemi tarafından bulunamadığı için oluşan bir derleme bağlama hataları önbelleğe almayı devre dışı bırakmak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="10fcd-145">The following example shows how to disable the caching of assembly binding failures that occur because the assembly was not found by probing.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableCachingBindingFailures enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="10fcd-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="10fcd-146">See also</span></span>

- [<span data-ttu-id="10fcd-147">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="10fcd-147">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="10fcd-148">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="10fcd-148">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="10fcd-149">Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="10fcd-149">How the Runtime Locates Assemblies</span></span>](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
