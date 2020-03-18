---
title: Varsayılan sondalama - .NET Core
description: .NET Core's System.Runtime.Loader.AssemblyLoadContext.Default sondalama mantığı bağımlılıkları bulmak için genel bakış.
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 500ee6ee863b1f311970a9e718936f57f7d4efd6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399093"
---
# <a name="default-probing"></a><span data-ttu-id="6882b-103">Varsayılan sondalama</span><span class="sxs-lookup"><span data-stu-id="6882b-103">Default probing</span></span>

<span data-ttu-id="6882b-104">Örnek, <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> bir derlemenin bağımlılıklarını bulmakla yükümlüdür.</span><span class="sxs-lookup"><span data-stu-id="6882b-104">The <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> instance is responsible for locating an assembly's dependencies.</span></span> <span data-ttu-id="6882b-105">Bu <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> makalede, örneğin sondalama mantığı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6882b-105">This article describes the <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> instance's probing logic.</span></span>

## <a name="host-configured-probing-properties"></a><span data-ttu-id="6882b-106">Barındırış yapılandırılmış sondalama özellikleri</span><span class="sxs-lookup"><span data-stu-id="6882b-106">Host configured probing properties</span></span>

<span data-ttu-id="6882b-107">Çalışma zamanı başlatıldığında, çalışma zamanı ana bilgisayarı <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> sonda yollarını yapılandıran adlandırılmış sonda özellikleri kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="6882b-107">When the runtime is started, the runtime host provides a set of named probing properties that configure <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> probe paths.</span></span>

<span data-ttu-id="6882b-108">Her sondalama özelliği isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="6882b-108">Each probing property is optional.</span></span> <span data-ttu-id="6882b-109">Varsa, her özellik, salt yolların sınırlı bir listesini içeren bir dize değeridir.</span><span class="sxs-lookup"><span data-stu-id="6882b-109">If present, each property is a string value that contains a delimited list of absolute paths.</span></span> <span data-ttu-id="6882b-110">Delimiter, Windows'da ';' ve diğer tüm platformlarda ':' olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="6882b-110">The delimiter is ';' on Windows and ':' on all other platforms.</span></span>

|<span data-ttu-id="6882b-111">Özellik Adı</span><span class="sxs-lookup"><span data-stu-id="6882b-111">Property Name</span></span>                 |<span data-ttu-id="6882b-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6882b-112">Description</span></span>  |
|------------------------------|---------|
|`TRUSTED_PLATFORM_ASSEMBLIES`   | <span data-ttu-id="6882b-113">Platform ve uygulama derleme dosya yollarının listesi.</span><span class="sxs-lookup"><span data-stu-id="6882b-113">List of platform and application assembly file paths.</span></span> |
|`PLATFORM_RESOURCE_ROOTS`       | <span data-ttu-id="6882b-114">Uydu kaynak derlemelerini aramak için dizin yolları listesi.</span><span class="sxs-lookup"><span data-stu-id="6882b-114">List of directory paths to search for satellite resource assemblies.</span></span> |
|`NATIVE_DLL_SEARCH_DIRECTORIES` | <span data-ttu-id="6882b-115">Yönetilmeyen (yerel) kitaplıkları aramak için dizin yolları listesi.</span><span class="sxs-lookup"><span data-stu-id="6882b-115">List of directory paths to search for unmanaged (native) libraries.</span></span>        |
|`APP_PATHS`                     | <span data-ttu-id="6882b-116">Yönetilen derlemeleri aramak için dizin yolları listesi.</span><span class="sxs-lookup"><span data-stu-id="6882b-116">List of directory paths to search for managed assemblies.</span></span> |
|`APP_NI_PATHS`                  | <span data-ttu-id="6882b-117">Yönetilen derlemelerin yerel görüntülerini aramak için dizin yolları listesi.</span><span class="sxs-lookup"><span data-stu-id="6882b-117">List of directory paths to search for native images of managed assemblies.</span></span> |

### <a name="how-are-the-properties-populated"></a><span data-ttu-id="6882b-118">Mülkler nasıl doldurulur?</span><span class="sxs-lookup"><span data-stu-id="6882b-118">How are the properties populated?</span></span>

<span data-ttu-id="6882b-119">\* \<Myapp>.deps.json\* dosyasının var olup olmadığına bağlı olarak özellikleri doldurmak için iki ana senaryo vardır.</span><span class="sxs-lookup"><span data-stu-id="6882b-119">There are two main scenarios for populating the properties depending on whether the *\<myapp>.deps.json* file exists.</span></span>

- <span data-ttu-id="6882b-120">.deps.json dosyası bulunduğunda, sonlama özelliklerini doldurmak için ayrıştırılır. \* \*\*</span><span class="sxs-lookup"><span data-stu-id="6882b-120">When the *\*.deps.json* file is present, it's parsed to populate the probing properties.</span></span>
- <span data-ttu-id="6882b-121">.deps.json dosyası yoksa, uygulamanın dizininin tüm bağımlılıkları içerdiği varsayılır. \* \*\*</span><span class="sxs-lookup"><span data-stu-id="6882b-121">When the *\*.deps.json* file isn't present, the application's directory is assumed to contain all the dependencies.</span></span> <span data-ttu-id="6882b-122">Dizin içeriği sondalama özelliklerini doldurmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6882b-122">The directory's contents are used to populate the probing properties.</span></span>

<span data-ttu-id="6882b-123">Ayrıca, başvurulan çerçeveler için \* \*.deps.json\* dosyaları benzer şekilde ayrıştı.</span><span class="sxs-lookup"><span data-stu-id="6882b-123">Additionally, the *\*.deps.json* files for any referenced frameworks are similarly parsed.</span></span>

<span data-ttu-id="6882b-124">Son olarak `ADDITIONAL_DEPS` ortam değişkeni ek bağımlılıklar eklemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6882b-124">Finally the environment variable `ADDITIONAL_DEPS` can be used to add additional dependencies.</span></span>

### <a name="how-do-i-see-the-probing-properties-from-managed-code"></a><span data-ttu-id="6882b-125">Yönetilen koddaki sondalama özelliklerini nasıl görebiliyorum?</span><span class="sxs-lookup"><span data-stu-id="6882b-125">How do I see the probing properties from managed code?</span></span>

<span data-ttu-id="6882b-126">Her özellik yukarıdaki tablodan özellik adı ile <xref:System.AppContext.GetData(System.String)?displayProperty=nameWithType> işlevi çağırarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6882b-126">Each property is available by calling the <xref:System.AppContext.GetData(System.String)?displayProperty=nameWithType> function with the property name from the table above.</span></span>

### <a name="how-do-i-debug-the-probing-properties-construction"></a><span data-ttu-id="6882b-127">Sonlama özelliklerinin inşaatını nasıl ayıka ait olurum?</span><span class="sxs-lookup"><span data-stu-id="6882b-127">How do I debug the probing properties' construction?</span></span>

<span data-ttu-id="6882b-128">.NET Core çalışma zamanı ana bilgisayarı, belirli ortam değişkenleri etkinleştirildiğinde yararlı izleme iletileri çıkaracaktır:</span><span class="sxs-lookup"><span data-stu-id="6882b-128">The .NET Core runtime host will output useful trace messages when certain environment variables are enabled:</span></span>

|<span data-ttu-id="6882b-129">Çevre Değişkeni</span><span class="sxs-lookup"><span data-stu-id="6882b-129">Environment Variable</span></span>        |<span data-ttu-id="6882b-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6882b-130">Description</span></span>  |
|----------------------------|---------|
|`COREHOST_TRACE=1`          |<span data-ttu-id="6882b-131">İzlemeyi sağlar.</span><span class="sxs-lookup"><span data-stu-id="6882b-131">Enables tracing.</span></span>|
|`COREHOST_TRACEFILE=<path>` |<span data-ttu-id="6882b-132">Varsayılan `stderr`yerine bir dosya yoluna izler.</span><span class="sxs-lookup"><span data-stu-id="6882b-132">Traces to a file path instead of the default `stderr`.</span></span>|
|`COREHOST_TRACE_VERBOSITY`  |<span data-ttu-id="6882b-133">Ayrıntılılığı 1 (en düşük) ile 4 (en yüksek) arasında ayarlar.</span><span class="sxs-lookup"><span data-stu-id="6882b-133">Sets the verbosity from 1 (lowest) to 4 (highest).</span></span>|

## <a name="managed-assembly-default-probing"></a><span data-ttu-id="6882b-134">Yönetilen derleme varsayılan sondalama</span><span class="sxs-lookup"><span data-stu-id="6882b-134">Managed assembly default probing</span></span>

<span data-ttu-id="6882b-135">Yönetilen bir derlemeyi bulmak için <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> sondalama yaparken, aşağıdakileri sırayla bakar:</span><span class="sxs-lookup"><span data-stu-id="6882b-135">When probing to locate a managed assembly, the <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> looks in order at:</span></span>

- <span data-ttu-id="6882b-136"><xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> In `TRUSTED_PLATFORM_ASSEMBLIES` ile eşleşen dosyalar (dosya uzantılarını kaldırdıktan sonra).</span><span class="sxs-lookup"><span data-stu-id="6882b-136">Files matching the <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> in `TRUSTED_PLATFORM_ASSEMBLIES` (after removing file extensions).</span></span>
- <span data-ttu-id="6882b-137">Ortak dosya uzantıları `APP_NI_PATHS` ile yerel görüntü derleme dosyaları.</span><span class="sxs-lookup"><span data-stu-id="6882b-137">Native image assembly files in `APP_NI_PATHS` with common file extensions.</span></span>
- <span data-ttu-id="6882b-138">Ortak dosya `APP_PATHS` uzantıları ile derleme dosyaları.</span><span class="sxs-lookup"><span data-stu-id="6882b-138">Assembly files in `APP_PATHS` with common file extensions.</span></span>

## <a name="satellite-resource-assembly-probing"></a><span data-ttu-id="6882b-139">Uydu (kaynak) montaj sondalama</span><span class="sxs-lookup"><span data-stu-id="6882b-139">Satellite (resource) assembly probing</span></span>

<span data-ttu-id="6882b-140">Belirli bir kültür için uydu derlemesi bulmak için bir dosya yolu kümesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="6882b-140">To find a satellite assembly for a specific culture, construct a set of file paths.</span></span>

<span data-ttu-id="6882b-141">Her yol `PLATFORM_RESOURCE_ROOTS` için `APP_PATHS`ve sonra <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> , dize, bir dizin ayırıcı, <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> dize ve uzantısı '.dll' ekler.</span><span class="sxs-lookup"><span data-stu-id="6882b-141">For each path in `PLATFORM_RESOURCE_ROOTS` and then `APP_PATHS`, append the <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> string, a directory separator, the <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> string, and the extension '.dll'.</span></span>

<span data-ttu-id="6882b-142">Eşleşen bir dosya varsa, yüklemeyi ve döndürmeyi dene.</span><span class="sxs-lookup"><span data-stu-id="6882b-142">If any matching file exists, attempt to load and return it.</span></span>

## <a name="unmanaged-native-library-probing"></a><span data-ttu-id="6882b-143">Yönetilmeyen (yerel) kitaplık sondalama</span><span class="sxs-lookup"><span data-stu-id="6882b-143">Unmanaged (native) library probing</span></span>

<span data-ttu-id="6882b-144">Yönetilmeyen bir kitaplığı bulmak için `NATIVE_DLL_SEARCH_DIRECTORIES` araştırma yaparken, eşleşen bir kitaplık aranır.</span><span class="sxs-lookup"><span data-stu-id="6882b-144">When probing to locate an unmanaged library, the `NATIVE_DLL_SEARCH_DIRECTORIES` are searched looking for a matching library.</span></span>
