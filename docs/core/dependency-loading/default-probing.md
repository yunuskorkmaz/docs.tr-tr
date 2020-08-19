---
title: Varsayılan yoklama-.NET Core
description: Bağımlılıkları bulmak için .NET Core 'un System. Runtime. Loader. AssemblyLoadContext. Default araştırma mantığına genel bakış.
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 13ce4c7de5f6ce1b76b2e61db810c0f19717540f
ms.sourcegitcommit: cbb19e56d48cf88375d35d0c27554d4722761e0d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2020
ms.locfileid: "88608421"
---
# <a name="default-probing"></a><span data-ttu-id="0fb0d-103">Varsayılan yoklama</span><span class="sxs-lookup"><span data-stu-id="0fb0d-103">Default probing</span></span>

<span data-ttu-id="0fb0d-104"><xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType>Örnek, bir derlemenin bağımlılıklarını bulmaktan sorumludur.</span><span class="sxs-lookup"><span data-stu-id="0fb0d-104">The <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> instance is responsible for locating an assembly's dependencies.</span></span> <span data-ttu-id="0fb0d-105">Bu makalede <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> Örneğin araştırma mantığı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0fb0d-105">This article describes the <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> instance's probing logic.</span></span>

## <a name="host-configured-probing-properties"></a><span data-ttu-id="0fb0d-106">Konak yapılandırılmış yoklama özellikleri</span><span class="sxs-lookup"><span data-stu-id="0fb0d-106">Host configured probing properties</span></span>

<span data-ttu-id="0fb0d-107">Çalışma zamanı başlatıldığında, çalışma zamanı ana bilgisayarı araştırma yollarını yapılandıran adlandırılmış bir yoklama özellikleri kümesi sağlar <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="0fb0d-107">When the runtime is started, the runtime host provides a set of named probing properties that configure <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> probe paths.</span></span>

<span data-ttu-id="0fb0d-108">Her yoklama özelliği isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="0fb0d-108">Each probing property is optional.</span></span> <span data-ttu-id="0fb0d-109">Varsa, her özellik mutlak yolların ayrılmış bir listesini içeren bir dize değeridir.</span><span class="sxs-lookup"><span data-stu-id="0fb0d-109">If present, each property is a string value that contains a delimited list of absolute paths.</span></span> <span data-ttu-id="0fb0d-110">Sınırlayıcı, Windows üzerinde '; ' ve diğer tüm platformlarda ': '.</span><span class="sxs-lookup"><span data-stu-id="0fb0d-110">The delimiter is ';' on Windows and ':' on all other platforms.</span></span>

|<span data-ttu-id="0fb0d-111">Özellik Adı</span><span class="sxs-lookup"><span data-stu-id="0fb0d-111">Property Name</span></span>                 |<span data-ttu-id="0fb0d-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0fb0d-112">Description</span></span>  |
|------------------------------|---------|
|`TRUSTED_PLATFORM_ASSEMBLIES`   | <span data-ttu-id="0fb0d-113">Platform ve uygulama derleme dosyası yollarının listesi.</span><span class="sxs-lookup"><span data-stu-id="0fb0d-113">List of platform and application assembly file paths.</span></span> |
|`PLATFORM_RESOURCE_ROOTS`       | <span data-ttu-id="0fb0d-114">Uydu kaynak derlemelerinin aranacağı Dizin yollarının listesi.</span><span class="sxs-lookup"><span data-stu-id="0fb0d-114">List of directory paths to search for satellite resource assemblies.</span></span> |
|`NATIVE_DLL_SEARCH_DIRECTORIES` | <span data-ttu-id="0fb0d-115">Yönetilmeyen (yerel) kitaplıkları aramak için Dizin yollarının listesi.</span><span class="sxs-lookup"><span data-stu-id="0fb0d-115">List of directory paths to search for unmanaged (native) libraries.</span></span>        |
|`APP_PATHS`                     | <span data-ttu-id="0fb0d-116">Yönetilen derlemeleri aramak için Dizin yollarının listesi.</span><span class="sxs-lookup"><span data-stu-id="0fb0d-116">List of directory paths to search for managed assemblies.</span></span> |
|`APP_NI_PATHS`                  | <span data-ttu-id="0fb0d-117">Yönetilen derlemelerin yerel görüntülerini aramak için Dizin yollarının listesi.</span><span class="sxs-lookup"><span data-stu-id="0fb0d-117">List of directory paths to search for native images of managed assemblies.</span></span> |

### <a name="how-are-the-properties-populated"></a><span data-ttu-id="0fb0d-118">Özellikler nasıl doldurulur?</span><span class="sxs-lookup"><span data-stu-id="0fb0d-118">How are the properties populated?</span></span>

<span data-ttu-id="0fb0d-119">\* \<myapp>.deps.js\* dosyanın var olup olmadığına bağlı olarak özelliklerin doldurulmasına yönelik iki ana senaryo vardır.</span><span class="sxs-lookup"><span data-stu-id="0fb0d-119">There are two main scenarios for populating the properties depending on whether the *\<myapp>.deps.json* file exists.</span></span>

- <span data-ttu-id="0fb0d-120">Dosyadaki \* \*.deps.js\* olduğunda, araştırma özelliklerini doldurmak için ayrıştırılır.</span><span class="sxs-lookup"><span data-stu-id="0fb0d-120">When the *\*.deps.json* file is present, it's parsed to populate the probing properties.</span></span>
- <span data-ttu-id="0fb0d-121">Dosyadaki \* \*.deps.js\* mevcut olmadığında, uygulamanın dizininin tüm bağımlılıkları içermesi varsayılır.</span><span class="sxs-lookup"><span data-stu-id="0fb0d-121">When the *\*.deps.json* file isn't present, the application's directory is assumed to contain all the dependencies.</span></span> <span data-ttu-id="0fb0d-122">Dizin içeriği, araştırma özelliklerini doldurmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0fb0d-122">The directory's contents are used to populate the probing properties.</span></span>

<span data-ttu-id="0fb0d-123">Ayrıca, başvurulan tüm çerçeveler için dosyalardaki \* \*.deps.js\* benzer şekilde ayrıştırılmaz.</span><span class="sxs-lookup"><span data-stu-id="0fb0d-123">Additionally, the *\*.deps.json* files for any referenced frameworks are similarly parsed.</span></span>

<span data-ttu-id="0fb0d-124">Son olarak, ortam değişkeni `ADDITIONAL_DEPS` ek bağımlılıklar eklemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0fb0d-124">Finally the environment variable `ADDITIONAL_DEPS` can be used to add additional dependencies.</span></span>  <span data-ttu-id="0fb0d-125">`dotnet.exe` Ayrıca, `--additional-deps` uygulamanın başlangıcında bu değeri ayarlamak için isteğe bağlı bir parametre içerir.</span><span class="sxs-lookup"><span data-stu-id="0fb0d-125">`dotnet.exe` also contains an `--additional-deps` optional parameter to set this value on application startup.</span></span>

<span data-ttu-id="0fb0d-126">`APP_PATHS`Ve `APP_NI_PATHS` özellikleri varsayılan olarak doldurulmaz ve çoğu uygulama için atlanır.</span><span class="sxs-lookup"><span data-stu-id="0fb0d-126">The `APP_PATHS` and `APP_NI_PATHS` properties are not populated by default and are omitted for most applications.</span></span>

<span data-ttu-id="0fb0d-127">Uygulama tarafından kullanılan dosyalardaki tüm \* \*.deps.js\* listesine aracılığıyla erişilebilir `System.AppContext.GetData("APP_CONTEXT_DEPS_FILES")` .</span><span class="sxs-lookup"><span data-stu-id="0fb0d-127">The list of all *\*.deps.json* files used by the application can be accessed via `System.AppContext.GetData("APP_CONTEXT_DEPS_FILES")`.</span></span>

### <a name="how-do-i-see-the-probing-properties-from-managed-code"></a><span data-ttu-id="0fb0d-128">Nasıl yaparım? yönetilen koddan yoklama özelliklerini görmek mi istiyorsunuz?</span><span class="sxs-lookup"><span data-stu-id="0fb0d-128">How do I see the probing properties from managed code?</span></span>

<span data-ttu-id="0fb0d-129">Her özelliğe, <xref:System.AppContext.GetData(System.String)?displayProperty=nameWithType> Yukarıdaki tablodaki Özellik adı ile işlev çağırarak ulaşılabilir.</span><span class="sxs-lookup"><span data-stu-id="0fb0d-129">Each property is available by calling the <xref:System.AppContext.GetData(System.String)?displayProperty=nameWithType> function with the property name from the table above.</span></span>

### <a name="how-do-i-debug-the-probing-properties-construction"></a><span data-ttu-id="0fb0d-130">Nasıl yaparım? araştırma özelliklerinin oluşturulması hata ayıklaması yapılsın mı?</span><span class="sxs-lookup"><span data-stu-id="0fb0d-130">How do I debug the probing properties' construction?</span></span>

<span data-ttu-id="0fb0d-131">.NET Core çalışma zamanı ana bilgisayarı, belirli ortam değişkenleri etkinleştirildiğinde yararlı izleme iletilerini çıktı olarak izler:</span><span class="sxs-lookup"><span data-stu-id="0fb0d-131">The .NET Core runtime host will output useful trace messages when certain environment variables are enabled:</span></span>

|<span data-ttu-id="0fb0d-132">Ortam değişkeni</span><span class="sxs-lookup"><span data-stu-id="0fb0d-132">Environment Variable</span></span>        |<span data-ttu-id="0fb0d-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0fb0d-133">Description</span></span>  |
|----------------------------|---------|
|`COREHOST_TRACE=1`          |<span data-ttu-id="0fb0d-134">İzlemeyi etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="0fb0d-134">Enables tracing.</span></span>|
|`COREHOST_TRACEFILE=<path>` |<span data-ttu-id="0fb0d-135">Varsayılan yerine bir dosya yolu izler `stderr` .</span><span class="sxs-lookup"><span data-stu-id="0fb0d-135">Traces to a file path instead of the default `stderr`.</span></span>|
|`COREHOST_TRACE_VERBOSITY`  |<span data-ttu-id="0fb0d-136">Ayrıntı düzeyini 1 ' den (en düşük) 4 ' e (en yüksek) ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0fb0d-136">Sets the verbosity from 1 (lowest) to 4 (highest).</span></span>|

## <a name="managed-assembly-default-probing"></a><span data-ttu-id="0fb0d-137">Yönetilen derleme varsayılan yoklama</span><span class="sxs-lookup"><span data-stu-id="0fb0d-137">Managed assembly default probing</span></span>

<span data-ttu-id="0fb0d-138">Yönetilen bir derlemeyi bulma konusunda yoklama yaparken <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> Şu sırada görünür:</span><span class="sxs-lookup"><span data-stu-id="0fb0d-138">When probing to locate a managed assembly, the <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> looks in order at:</span></span>

- <span data-ttu-id="0fb0d-139">İle eşleşen dosyalar <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> `TRUSTED_PLATFORM_ASSEMBLIES` (dosya uzantıları kaldırıldıktan sonra).</span><span class="sxs-lookup"><span data-stu-id="0fb0d-139">Files matching the <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> in `TRUSTED_PLATFORM_ASSEMBLIES` (after removing file extensions).</span></span>
- <span data-ttu-id="0fb0d-140">Ortak dosya uzantıları ile içindeki yerel görüntü derleme dosyaları `APP_NI_PATHS` .</span><span class="sxs-lookup"><span data-stu-id="0fb0d-140">Native image assembly files in `APP_NI_PATHS` with common file extensions.</span></span>
- <span data-ttu-id="0fb0d-141">`APP_PATHS`Ortak dosya uzantılarıyla içindeki derleme dosyaları.</span><span class="sxs-lookup"><span data-stu-id="0fb0d-141">Assembly files in `APP_PATHS` with common file extensions.</span></span>

## <a name="satellite-resource-assembly-probing"></a><span data-ttu-id="0fb0d-142">Uydu (kaynak) derlemeyi yoklama</span><span class="sxs-lookup"><span data-stu-id="0fb0d-142">Satellite (resource) assembly probing</span></span>

<span data-ttu-id="0fb0d-143">Belirli bir kültürün uydu derlemesini bulmak için bir dosya yolları kümesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0fb0d-143">To find a satellite assembly for a specific culture, construct a set of file paths.</span></span>

<span data-ttu-id="0fb0d-144">İçindeki her yol için, `PLATFORM_RESOURCE_ROOTS` `APP_PATHS` <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> dizeyi, Dizin ayırıcısını, <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> dizeyi ve '. dll ' uzantısını ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0fb0d-144">For each path in `PLATFORM_RESOURCE_ROOTS` and then `APP_PATHS`, append the <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> string, a directory separator, the <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> string, and the extension '.dll'.</span></span>

<span data-ttu-id="0fb0d-145">Eşleşen herhangi bir dosya varsa, yüklemeyi ve döndürmeyi deneyin.</span><span class="sxs-lookup"><span data-stu-id="0fb0d-145">If any matching file exists, attempt to load and return it.</span></span>

## <a name="unmanaged-native-library-probing"></a><span data-ttu-id="0fb0d-146">Yönetilmeyen (yerel) kitaplık yoklama</span><span class="sxs-lookup"><span data-stu-id="0fb0d-146">Unmanaged (native) library probing</span></span>

<span data-ttu-id="0fb0d-147">Yönetilmeyen bir kitaplığı bulmaya yönelik yoklama yaparken, bu, `NATIVE_DLL_SEARCH_DIRECTORIES` eşleşen bir kitaplığı arıyor.</span><span class="sxs-lookup"><span data-stu-id="0fb0d-147">When probing to locate an unmanaged library, the `NATIVE_DLL_SEARCH_DIRECTORIES` are searched looking for a matching library.</span></span>
