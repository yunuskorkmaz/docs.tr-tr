---
title: Varsayılan yoklama-.NET Core
description: Bağımlılıkları bulmak için .NET Core 'un System. Runtime. Loader. AssemblyLoadContext. Default araştırma mantığına genel bakış.
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 1e347c716c2d739a1bd03be056b57fdbda6c678f
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82859519"
---
# <a name="default-probing"></a><span data-ttu-id="bd912-103">Varsayılan yoklama</span><span class="sxs-lookup"><span data-stu-id="bd912-103">Default probing</span></span>

<span data-ttu-id="bd912-104"><xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> Örnek, bir derlemenin bağımlılıklarını bulmaktan sorumludur.</span><span class="sxs-lookup"><span data-stu-id="bd912-104">The <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> instance is responsible for locating an assembly's dependencies.</span></span> <span data-ttu-id="bd912-105">Bu makalede <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> örneğin araştırma mantığı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bd912-105">This article describes the <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> instance's probing logic.</span></span>

## <a name="host-configured-probing-properties"></a><span data-ttu-id="bd912-106">Konak yapılandırılmış yoklama özellikleri</span><span class="sxs-lookup"><span data-stu-id="bd912-106">Host configured probing properties</span></span>

<span data-ttu-id="bd912-107">Çalışma zamanı başlatıldığında, çalışma zamanı ana bilgisayarı araştırma yollarını yapılandıran <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> adlandırılmış bir yoklama özellikleri kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="bd912-107">When the runtime is started, the runtime host provides a set of named probing properties that configure <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> probe paths.</span></span>

<span data-ttu-id="bd912-108">Her yoklama özelliği isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="bd912-108">Each probing property is optional.</span></span> <span data-ttu-id="bd912-109">Varsa, her özellik mutlak yolların ayrılmış bir listesini içeren bir dize değeridir.</span><span class="sxs-lookup"><span data-stu-id="bd912-109">If present, each property is a string value that contains a delimited list of absolute paths.</span></span> <span data-ttu-id="bd912-110">Sınırlayıcı, Windows üzerinde '; ' ve diğer tüm platformlarda ': '.</span><span class="sxs-lookup"><span data-stu-id="bd912-110">The delimiter is ';' on Windows and ':' on all other platforms.</span></span>

|<span data-ttu-id="bd912-111">Özellik Adı</span><span class="sxs-lookup"><span data-stu-id="bd912-111">Property Name</span></span>                 |<span data-ttu-id="bd912-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bd912-112">Description</span></span>  |
|------------------------------|---------|
|`TRUSTED_PLATFORM_ASSEMBLIES`   | <span data-ttu-id="bd912-113">Platform ve uygulama derleme dosyası yollarının listesi.</span><span class="sxs-lookup"><span data-stu-id="bd912-113">List of platform and application assembly file paths.</span></span> |
|`PLATFORM_RESOURCE_ROOTS`       | <span data-ttu-id="bd912-114">Uydu kaynak derlemelerinin aranacağı Dizin yollarının listesi.</span><span class="sxs-lookup"><span data-stu-id="bd912-114">List of directory paths to search for satellite resource assemblies.</span></span> |
|`NATIVE_DLL_SEARCH_DIRECTORIES` | <span data-ttu-id="bd912-115">Yönetilmeyen (yerel) kitaplıkları aramak için Dizin yollarının listesi.</span><span class="sxs-lookup"><span data-stu-id="bd912-115">List of directory paths to search for unmanaged (native) libraries.</span></span>        |
|`APP_PATHS`                     | <span data-ttu-id="bd912-116">Yönetilen derlemeleri aramak için Dizin yollarının listesi.</span><span class="sxs-lookup"><span data-stu-id="bd912-116">List of directory paths to search for managed assemblies.</span></span> |
|`APP_NI_PATHS`                  | <span data-ttu-id="bd912-117">Yönetilen derlemelerin yerel görüntülerini aramak için Dizin yollarının listesi.</span><span class="sxs-lookup"><span data-stu-id="bd912-117">List of directory paths to search for native images of managed assemblies.</span></span> |

### <a name="how-are-the-properties-populated"></a><span data-ttu-id="bd912-118">Özellikler nasıl doldurulur?</span><span class="sxs-lookup"><span data-stu-id="bd912-118">How are the properties populated?</span></span>

<span data-ttu-id="bd912-119">*MyApp>. Deps. json dosyasının var olup olmadığına bağlı olarak özelliklerin doldurulmasına yönelik iki ana senaryo vardır. \<*</span><span class="sxs-lookup"><span data-stu-id="bd912-119">There are two main scenarios for populating the properties depending on whether the *\<myapp>.deps.json* file exists.</span></span>

- <span data-ttu-id="bd912-120">. Deps. JSON dosyası mevcut olduğunda, araştırma özelliklerini doldurmak için ayrıştırılır. \* \*\*</span><span class="sxs-lookup"><span data-stu-id="bd912-120">When the *\*.deps.json* file is present, it's parsed to populate the probing properties.</span></span>
- <span data-ttu-id="bd912-121">. Deps. JSON dosyası mevcut olmadığında, uygulamanın dizininin tüm bağımlılıkları içermesi varsayılır. \* \*\*</span><span class="sxs-lookup"><span data-stu-id="bd912-121">When the *\*.deps.json* file isn't present, the application's directory is assumed to contain all the dependencies.</span></span> <span data-ttu-id="bd912-122">Dizin içeriği, araştırma özelliklerini doldurmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bd912-122">The directory's contents are used to populate the probing properties.</span></span>

<span data-ttu-id="bd912-123">Ayrıca, başvurulan tüm çerçeveler için \* \*. Deps. JSON\* dosyaları benzer şekilde ayrıştırılmaz.</span><span class="sxs-lookup"><span data-stu-id="bd912-123">Additionally, the *\*.deps.json* files for any referenced frameworks are similarly parsed.</span></span>

<span data-ttu-id="bd912-124">Son olarak, ortam `ADDITIONAL_DEPS` değişkeni ek bağımlılıklar eklemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bd912-124">Finally the environment variable `ADDITIONAL_DEPS` can be used to add additional dependencies.</span></span>

<span data-ttu-id="bd912-125">`APP_PATHS` Ve `APP_NI_PATHS` özellikleri varsayılan olarak doldurulmaz ve çoğu uygulama için atlanır.</span><span class="sxs-lookup"><span data-stu-id="bd912-125">The `APP_PATHS` and `APP_NI_PATHS` properties are not populated by default and are omitted for most applications.</span></span>

### <a name="how-do-i-see-the-probing-properties-from-managed-code"></a><span data-ttu-id="bd912-126">Nasıl yaparım? yönetilen koddan yoklama özelliklerini görmek mi istiyorsunuz?</span><span class="sxs-lookup"><span data-stu-id="bd912-126">How do I see the probing properties from managed code?</span></span>

<span data-ttu-id="bd912-127">Her özelliğe, yukarıdaki tablodaki Özellik adı <xref:System.AppContext.GetData(System.String)?displayProperty=nameWithType> ile işlev çağırarak ulaşılabilir.</span><span class="sxs-lookup"><span data-stu-id="bd912-127">Each property is available by calling the <xref:System.AppContext.GetData(System.String)?displayProperty=nameWithType> function with the property name from the table above.</span></span>

### <a name="how-do-i-debug-the-probing-properties-construction"></a><span data-ttu-id="bd912-128">Nasıl yaparım? araştırma özelliklerinin oluşturulması hata ayıklaması yapılsın mı?</span><span class="sxs-lookup"><span data-stu-id="bd912-128">How do I debug the probing properties' construction?</span></span>

<span data-ttu-id="bd912-129">.NET Core çalışma zamanı ana bilgisayarı, belirli ortam değişkenleri etkinleştirildiğinde yararlı izleme iletilerini çıktı olarak izler:</span><span class="sxs-lookup"><span data-stu-id="bd912-129">The .NET Core runtime host will output useful trace messages when certain environment variables are enabled:</span></span>

|<span data-ttu-id="bd912-130">Ortam değişkeni</span><span class="sxs-lookup"><span data-stu-id="bd912-130">Environment Variable</span></span>        |<span data-ttu-id="bd912-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bd912-131">Description</span></span>  |
|----------------------------|---------|
|`COREHOST_TRACE=1`          |<span data-ttu-id="bd912-132">İzlemeyi etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="bd912-132">Enables tracing.</span></span>|
|`COREHOST_TRACEFILE=<path>` |<span data-ttu-id="bd912-133">Varsayılan `stderr`yerine bir dosya yolu izler.</span><span class="sxs-lookup"><span data-stu-id="bd912-133">Traces to a file path instead of the default `stderr`.</span></span>|
|`COREHOST_TRACE_VERBOSITY`  |<span data-ttu-id="bd912-134">Ayrıntı düzeyini 1 ' den (en düşük) 4 ' e (en yüksek) ayarlar.</span><span class="sxs-lookup"><span data-stu-id="bd912-134">Sets the verbosity from 1 (lowest) to 4 (highest).</span></span>|

## <a name="managed-assembly-default-probing"></a><span data-ttu-id="bd912-135">Yönetilen derleme varsayılan yoklama</span><span class="sxs-lookup"><span data-stu-id="bd912-135">Managed assembly default probing</span></span>

<span data-ttu-id="bd912-136">Yönetilen bir derlemeyi bulma konusunda yoklama yaparken şu sırada <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> görünür:</span><span class="sxs-lookup"><span data-stu-id="bd912-136">When probing to locate a managed assembly, the <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> looks in order at:</span></span>

- <span data-ttu-id="bd912-137">İle eşleşen <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> dosyalar `TRUSTED_PLATFORM_ASSEMBLIES` (dosya uzantıları kaldırıldıktan sonra).</span><span class="sxs-lookup"><span data-stu-id="bd912-137">Files matching the <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> in `TRUSTED_PLATFORM_ASSEMBLIES` (after removing file extensions).</span></span>
- <span data-ttu-id="bd912-138">Ortak dosya uzantıları ile içindeki `APP_NI_PATHS` yerel görüntü derleme dosyaları.</span><span class="sxs-lookup"><span data-stu-id="bd912-138">Native image assembly files in `APP_NI_PATHS` with common file extensions.</span></span>
- <span data-ttu-id="bd912-139">Ortak dosya uzantılarıyla `APP_PATHS` içindeki derleme dosyaları.</span><span class="sxs-lookup"><span data-stu-id="bd912-139">Assembly files in `APP_PATHS` with common file extensions.</span></span>

## <a name="satellite-resource-assembly-probing"></a><span data-ttu-id="bd912-140">Uydu (kaynak) derlemeyi yoklama</span><span class="sxs-lookup"><span data-stu-id="bd912-140">Satellite (resource) assembly probing</span></span>

<span data-ttu-id="bd912-141">Belirli bir kültürün uydu derlemesini bulmak için bir dosya yolları kümesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="bd912-141">To find a satellite assembly for a specific culture, construct a set of file paths.</span></span>

<span data-ttu-id="bd912-142">İçindeki `PLATFORM_RESOURCE_ROOTS` `APP_PATHS`her yol için, <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> dizeyi, Dizin ayırıcısını, <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> dizeyi ve '. dll ' uzantısını ekleyin.</span><span class="sxs-lookup"><span data-stu-id="bd912-142">For each path in `PLATFORM_RESOURCE_ROOTS` and then `APP_PATHS`, append the <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> string, a directory separator, the <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> string, and the extension '.dll'.</span></span>

<span data-ttu-id="bd912-143">Eşleşen herhangi bir dosya varsa, yüklemeyi ve döndürmeyi deneyin.</span><span class="sxs-lookup"><span data-stu-id="bd912-143">If any matching file exists, attempt to load and return it.</span></span>

## <a name="unmanaged-native-library-probing"></a><span data-ttu-id="bd912-144">Yönetilmeyen (yerel) kitaplık yoklama</span><span class="sxs-lookup"><span data-stu-id="bd912-144">Unmanaged (native) library probing</span></span>

<span data-ttu-id="bd912-145">Yönetilmeyen bir kitaplığı bulmaya yönelik yoklama yaparken, bu `NATIVE_DLL_SEARCH_DIRECTORIES` , eşleşen bir kitaplığı arıyor.</span><span class="sxs-lookup"><span data-stu-id="bd912-145">When probing to locate an unmanaged library, the `NATIVE_DLL_SEARCH_DIRECTORIES` are searched looking for a matching library.</span></span>
