---
title: Özel SQLite sürümleri
ms.date: 09/04/2020
description: Yerel SQLite kitaplığı 'nın özel bir sürümünü nasıl kullanacağınızı öğrenin.
ms.openlocfilehash: fbf4b4cd33e6e890ce0c0cfe0b7688487b94b4a3
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89516144"
---
# <a name="custom-sqlite-versions"></a><span data-ttu-id="661e1-103">Özel SQLite sürümleri</span><span class="sxs-lookup"><span data-stu-id="661e1-103">Custom SQLite versions</span></span>

<span data-ttu-id="661e1-104">`Microsoft.Data.Sqlite` , üzerine kurulmuştur `SQLitePCLRaw` .</span><span class="sxs-lookup"><span data-stu-id="661e1-104">`Microsoft.Data.Sqlite` is built on top of `SQLitePCLRaw`.</span></span> <span data-ttu-id="661e1-105">Bir paket kullanarak veya bir sağlayıcıyı yapılandırarak yerel SQLite kitaplığının özel sürümlerini kullanabilirsiniz `SQLitePCLRaw` .</span><span class="sxs-lookup"><span data-stu-id="661e1-105">You can use custom versions of the native SQLite library by using a bundle or by configuring a `SQLitePCLRaw` provider.</span></span>

## <a name="bundles"></a><span data-ttu-id="661e1-106">Paketi</span><span class="sxs-lookup"><span data-stu-id="661e1-106">Bundles</span></span>

<span data-ttu-id="661e1-107">`SQLitePCLRaw` , farklı platformlarda doğru bağımlılıklara kolayca gelmesini kolaylaştıran, kullanışlı tabanlı paket paketleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="661e1-107">`SQLitePCLRaw` provides convenience-based bundle packages, that make it easy to bring in the right dependencies across different platforms.</span></span> <span data-ttu-id="661e1-108">Ana `Microsoft.Data.Sqlite` paket varsayılan olarak ' i sunar `SQLitePCLRaw.bundle_e_sqlite3` .</span><span class="sxs-lookup"><span data-stu-id="661e1-108">The main `Microsoft.Data.Sqlite` package brings in `SQLitePCLRaw.bundle_e_sqlite3` by default.</span></span> <span data-ttu-id="661e1-109">Farklı bir paket kullanmak için, kullanmak istediğiniz paket `Microsoft.Data.Sqlite.Core` paketiyle birlikte bunun yerine paketini de yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="661e1-109">To use a different bundle, install the `Microsoft.Data.Sqlite.Core` package instead along with the bundle package you want to use.</span></span> <span data-ttu-id="661e1-110">Paketleri tarafından otomatik olarak başlatılır `Microsoft.Data.Sqlite` .</span><span class="sxs-lookup"><span data-stu-id="661e1-110">Bundles are automatically initialized by `Microsoft.Data.Sqlite`.</span></span>

| <span data-ttu-id="661e1-111">Paket</span><span class="sxs-lookup"><span data-stu-id="661e1-111">Bundle</span></span> | <span data-ttu-id="661e1-112">Description</span><span class="sxs-lookup"><span data-stu-id="661e1-112">Description</span></span> |
|--|--|
| [<span data-ttu-id="661e1-113">SQLitePCLRaw. bundle_e_sqlite3</span><span class="sxs-lookup"><span data-stu-id="661e1-113">SQLitePCLRaw.bundle_e_sqlite3</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.bundle_e_sqlite3) | <span data-ttu-id="661e1-114">Tüm platformlarda SQLite ' un tutarlı bir sürümünü sağlar.</span><span class="sxs-lookup"><span data-stu-id="661e1-114">Provides a consistent version of SQLite on all platforms.</span></span> <span data-ttu-id="661e1-115">FTS4, FTS5, JSON1 ve R \* ağaç uzantılarını içerir.</span><span class="sxs-lookup"><span data-stu-id="661e1-115">Includes the FTS4, FTS5, JSON1, and R\*Tree extensions.</span></span> <span data-ttu-id="661e1-116">Bu varsayılan seçenektir.</span><span class="sxs-lookup"><span data-stu-id="661e1-116">This is the default.</span></span> |
| [<span data-ttu-id="661e1-117">SQLitePCLRaw. bundle_e_sqlcipher</span><span class="sxs-lookup"><span data-stu-id="661e1-117">SQLitePCLRaw.bundle_e_sqlcipher</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.bundle_e_sqlcipher) | <span data-ttu-id="661e1-118">Resmi olmayan, açık kaynaklı bir yapı sağlar `SQLCipher` .</span><span class="sxs-lookup"><span data-stu-id="661e1-118">Provides an unofficial, open-source build of `SQLCipher`.</span></span> |
| [<span data-ttu-id="661e1-119">SQLitePCLRaw. bundle_green</span><span class="sxs-lookup"><span data-stu-id="661e1-119">SQLitePCLRaw.bundle_green</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.bundle_green) | <span data-ttu-id="661e1-120">`bundle_e_sqlite3`İOS dışında, sistem SQLite kitaplığını kullandığında, ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="661e1-120">Same as `bundle_e_sqlite3`, except on iOS where it uses the system SQLite library.</span></span> |
| [<span data-ttu-id="661e1-121">SQLitePCLRaw. bundle_sqlite3</span><span class="sxs-lookup"><span data-stu-id="661e1-121">SQLitePCLRaw.bundle_sqlite3</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.bundle_sqlite3) | <span data-ttu-id="661e1-122">, Sistem SQLite kitaplığını kullanır.</span><span class="sxs-lookup"><span data-stu-id="661e1-122">Uses the system SQLite library.</span></span> |
| [<span data-ttu-id="661e1-123">SQLitePCLRaw. bundle_winsqlite3</span><span class="sxs-lookup"><span data-stu-id="661e1-123">SQLitePCLRaw.bundle_winsqlite3</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.bundle_winsqlite3) | <span data-ttu-id="661e1-124">`winsqlite3.dll`, Windows 10 ' da sistem SQLite Kitaplığı ' nı kullanır.</span><span class="sxs-lookup"><span data-stu-id="661e1-124">Uses `winsqlite3.dll`, the system SQLite library on Windows 10.</span></span> |
| [<span data-ttu-id="661e1-125">SQLitePCLRaw. bundle_zetetic</span><span class="sxs-lookup"><span data-stu-id="661e1-125">SQLitePCLRaw.bundle_zetetic</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.bundle_zetetic) | <span data-ttu-id="661e1-126">`SQLCipher`Zetetik 'dan (dahil değil) resmi derlemeler kullanır.</span><span class="sxs-lookup"><span data-stu-id="661e1-126">Uses the official `SQLCipher` builds from Zetetic (not included).</span></span> |

<span data-ttu-id="661e1-127">Örneğin, resmi olmayan, açık kaynaklı bir derlemesini kullanmak için `SQLCipher` aşağıdaki komutları kullanın.</span><span class="sxs-lookup"><span data-stu-id="661e1-127">For example, to use the unofficial, open-source build of `SQLCipher` use the following commands.</span></span>

### <a name="net-core-cli"></a>[<span data-ttu-id="661e1-128">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="661e1-128">.NET Core CLI</span></span>](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite.Core
dotnet add package SQLitePCLRaw.bundle_e_sqlcipher
```

### <a name="visual-studio"></a>[<span data-ttu-id="661e1-129">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="661e1-129">Visual Studio</span></span>](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite.Core
Install-Package SQLitePCLRaw.bundle_e_sqlcipher
```

---

## <a name="sqlitepclraw-available-providers"></a><span data-ttu-id="661e1-130">SQLitePCLRaw kullanılabilir sağlayıcılar</span><span class="sxs-lookup"><span data-stu-id="661e1-130">SQLitePCLRaw available providers</span></span>

<span data-ttu-id="661e1-131">Bir pakete bağlı olmadığında, çekirdek derleme ile kullanılabilir SQLite sağlayıcıları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="661e1-131">When not relying on a bundle, you can use the available providers of SQLite with the core assembly.</span></span>

| <span data-ttu-id="661e1-132">Sağlayıcı</span><span class="sxs-lookup"><span data-stu-id="661e1-132">Provider</span></span> | <span data-ttu-id="661e1-133">Description</span><span class="sxs-lookup"><span data-stu-id="661e1-133">Description</span></span> |
|--|--|
| [<span data-ttu-id="661e1-134">SQLitePCLRaw. Provider. Dynamic</span><span class="sxs-lookup"><span data-stu-id="661e1-134">SQLitePCLRaw.provider.dynamic</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.provider.dynamic) | <span data-ttu-id="661e1-135">`dynamic`Sağlayıcı, öznitelikleri kullanmak yerine yerel kitaplığı yükler <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="661e1-135">The `dynamic` provider loads the native library instead of using <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=nameWithType> attributes.</span></span> <span data-ttu-id="661e1-136">Bu sağlayıcıyı kullanma hakkında daha fazla bilgi için bkz. [dinamik sağlayıcıyı kullanma](#use-the-dynamic-provider).</span><span class="sxs-lookup"><span data-stu-id="661e1-136">For more information on using this provider, see [use the dynamic provider](#use-the-dynamic-provider).</span></span> |
| [<span data-ttu-id="661e1-137">SQLitePCLRaw. Provider. e_sqlite3</span><span class="sxs-lookup"><span data-stu-id="661e1-137">SQLitePCLRaw.provider.e_sqlite3</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.provider.e_sqlite3) | <span data-ttu-id="661e1-138">`e_sqlite3`Varsayılan sağlayıcıdır.</span><span class="sxs-lookup"><span data-stu-id="661e1-138">The `e_sqlite3` is the default provider.</span></span> |
| [<span data-ttu-id="661e1-139">SQLitePCLRaw. Provider. e_sqlcipher</span><span class="sxs-lookup"><span data-stu-id="661e1-139">SQLitePCLRaw.provider.e_sqlcipher</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.provider.e_sqlcipher) | <span data-ttu-id="661e1-140">`e_sqlcipher`Sağlayıcı, resmi olmayan ve desteklenmeyen bir sağlayıcıdır `SQLCipher` .</span><span class="sxs-lookup"><span data-stu-id="661e1-140">The `e_sqlcipher` provider is the unofficial and unsupported `SQLCipher`.</span></span> |
| [<span data-ttu-id="661e1-141">SQLitePCLRaw. Provider. SQLite3</span><span class="sxs-lookup"><span data-stu-id="661e1-141">SQLitePCLRaw.provider.sqlite3</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.provider.sqlite3) | <span data-ttu-id="661e1-142">`sqlite3`Sağlayıcı `SQLite` IOS, MacOS ve Linux için sunulan bir sistemdir.</span><span class="sxs-lookup"><span data-stu-id="661e1-142">The `sqlite3` provider is a system-provided `SQLite` for iOS, macOS, and Linux.</span></span> |
| [<span data-ttu-id="661e1-143">SQLitePCLRaw. Provider. sqlcipher</span><span class="sxs-lookup"><span data-stu-id="661e1-143">SQLitePCLRaw.provider.sqlcipher</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.provider.sqlcipher) | <span data-ttu-id="661e1-144">Sağlayıcı, ' `sqlcipher` den resmi `SQLCipher` derlemeler içindir `Zetetic` .</span><span class="sxs-lookup"><span data-stu-id="661e1-144">The `sqlcipher` provider is for official `SQLCipher` builds from `Zetetic`.</span></span> |
| [<span data-ttu-id="661e1-145">SQLitePCLRaw. Provider. winsqlite3</span><span class="sxs-lookup"><span data-stu-id="661e1-145">SQLitePCLRaw.provider.winsqlite3</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.provider.winsqlite3) | <span data-ttu-id="661e1-146">`winsqlite3`Sağlayıcı, Windows 10 ortamları içindir.</span><span class="sxs-lookup"><span data-stu-id="661e1-146">The `winsqlite3` provider is for Windows 10 environments.</span></span> |

<span data-ttu-id="661e1-147">Sağlayıcıyı kullanmak için `sqlite3` aşağıdaki komutları kullanın:</span><span class="sxs-lookup"><span data-stu-id="661e1-147">To use the `sqlite3` provider use the following commands:</span></span>

### <a name="net-core-cli"></a>[<span data-ttu-id="661e1-148">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="661e1-148">.NET Core CLI</span></span>](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite.Core
dotnet add package SQLitePCLRaw.core
dotnet add package SQLitePCLRaw.provider.sqlite3
```

### <a name="visual-studio"></a>[<span data-ttu-id="661e1-149">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="661e1-149">Visual Studio</span></span>](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite.Core
Install-Package SQLitePCLRaw.core
Install-Package SQLitePCLRaw.provider.sqlite3
```

---

<span data-ttu-id="661e1-150">Paketler yüklü olduğunda, sağlayıcıyı `sqlite3` örnekle ayarlarsınız.</span><span class="sxs-lookup"><span data-stu-id="661e1-150">With the packages installed, you then set the provider to the `sqlite3` instance.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SqliteProviderSample/Program.cs)]

## <a name="use-the-dynamic-provider"></a><span data-ttu-id="661e1-151">Dinamik sağlayıcıyı kullan</span><span class="sxs-lookup"><span data-stu-id="661e1-151">Use the dynamic provider</span></span>

<span data-ttu-id="661e1-152">Paketten yararlanarak kendi SQLite yapınızı kullanabilirsiniz `SQLitePCLRaw.provider.dynamic_cdecl` .</span><span class="sxs-lookup"><span data-stu-id="661e1-152">You can use your own build of SQLite by leveraging the `SQLitePCLRaw.provider.dynamic_cdecl` package.</span></span> <span data-ttu-id="661e1-153">Bu durumda, yerel kitaplığı uygulamanızla dağıtmaktan sorumlu olursunuz.</span><span class="sxs-lookup"><span data-stu-id="661e1-153">In this case, you're responsible for deploying the native library with your app.</span></span> <span data-ttu-id="661e1-154">Bu şekilde, uygulamanıza yerel kitaplıklar dağıtmanın ayrıntıları, kullandığınız .NET platformu ve çalışma zamanına bağlı olarak önemli ölçüde farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="661e1-154">Note, the details of deploying native libraries with your app vary considerably depending on which .NET platform and runtime you're using.</span></span>

<span data-ttu-id="661e1-155">Öncelikle uygulamanız gerekir `IGetFunctionPointer` .</span><span class="sxs-lookup"><span data-stu-id="661e1-155">First, you'll need to implement `IGetFunctionPointer`.</span></span> <span data-ttu-id="661e1-156">.NET Core üzerinde uygulama aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="661e1-156">The implementation on .NET Core is as follows:</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SystemLibrarySample/Program.cs?name=snippet_NativeLibraryAdapter)]

<span data-ttu-id="661e1-157">Ardından, sağlayıcıyı yapılandırın `SQLitePCLRaw` .</span><span class="sxs-lookup"><span data-stu-id="661e1-157">Next, configure the `SQLitePCLRaw` provider.</span></span> <span data-ttu-id="661e1-158">Uygulamanızda kullanılmadan önce bunun yapıldığından emin olun `Microsoft.Data.Sqlite` .</span><span class="sxs-lookup"><span data-stu-id="661e1-158">Ensure this is done before `Microsoft.Data.Sqlite` is used in your app.</span></span> <span data-ttu-id="661e1-159">Ayrıca, `SQLitePCLRaw` sağlayıcınızı geçersiz kılabilecek bir paket paketi kullanmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="661e1-159">Also, avoid using a `SQLitePCLRaw` bundle package which might override your provider.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SystemLibrarySample/Program.cs?name=snippet_SetProvider)]
