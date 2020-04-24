---
title: Özel SQLite sürümleri
ms.date: 12/13/2019
description: Yerel SQLite kitaplığı 'nın özel bir sürümünü nasıl kullanacağınızı öğrenin.
ms.openlocfilehash: dd27278c1dbe17b12e5067d04d19043bf259b1e8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746983"
---
# <a name="custom-sqlite-versions"></a><span data-ttu-id="a44c5-103">Özel SQLite sürümleri</span><span class="sxs-lookup"><span data-stu-id="a44c5-103">Custom SQLite versions</span></span>

<span data-ttu-id="a44c5-104">Microsoft. Data. SQLite, SQLitePCLRaw üzerine kurulmuştur.</span><span class="sxs-lookup"><span data-stu-id="a44c5-104">Microsoft.Data.Sqlite is built on top of SQLitePCLRaw.</span></span> <span data-ttu-id="a44c5-105">Bir paket kullanarak veya bir SQLitePCLRaw sağlayıcısı yapılandırarak yerel SQLite kitaplığının özel sürümlerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a44c5-105">You can use custom versions of the native SQLite library by using a bundle or by configuring a SQLitePCLRaw provider.</span></span>

## <a name="bundles"></a><span data-ttu-id="a44c5-106">Paketi</span><span class="sxs-lookup"><span data-stu-id="a44c5-106">Bundles</span></span>

<span data-ttu-id="a44c5-107">SQLitePCLRaw, farklı platformlarda doğru bağımlılıklara kolayca getirmeyi kolaylaştıran paket paketleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="a44c5-107">SQLitePCLRaw provides bundle packages that make it easy to bring in the right dependencies across different platforms.</span></span>

<span data-ttu-id="a44c5-108">Ana Microsoft. Data. SQLite paketi varsayılan olarak SQLitePCLRaw. bundle_e_sqlite3 ' ye getirir.</span><span class="sxs-lookup"><span data-stu-id="a44c5-108">The main Microsoft.Data.Sqlite package brings in SQLitePCLRaw.bundle_e_sqlite3 by default.</span></span>

<span data-ttu-id="a44c5-109">Farklı bir paket kullanmak için, kullanmak istediğiniz `Microsoft.Data.Sqlite.Core` paket paketiyle birlikte bunun yerine paketini de yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a44c5-109">To use a different bundle, install the `Microsoft.Data.Sqlite.Core` package instead along with the bundle package you want to use.</span></span> <span data-ttu-id="a44c5-110">Paketleri Microsoft. Data. SQLite tarafından otomatik olarak başlatılır.</span><span class="sxs-lookup"><span data-stu-id="a44c5-110">Bundles are automatically initialized by Microsoft.Data.Sqlite.</span></span>

| <span data-ttu-id="a44c5-111">Paket</span><span class="sxs-lookup"><span data-stu-id="a44c5-111">Bundle</span></span> | <span data-ttu-id="a44c5-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a44c5-112">Description</span></span> |
| --- | --- |
| <span data-ttu-id="a44c5-113">SQLitePCLRaw. bundle_e_sqlite3</span><span class="sxs-lookup"><span data-stu-id="a44c5-113">SQLitePCLRaw.bundle_e_sqlite3</span></span> | <span data-ttu-id="a44c5-114">Tüm platformlarda SQLite ' un tutarlı bir sürümünü sağlar.</span><span class="sxs-lookup"><span data-stu-id="a44c5-114">Provides a consistent version of SQLite on all platforms.</span></span> <span data-ttu-id="a44c5-115">FTS4, FTS5, JSON1 ve R \* ağaç uzantılarını içerir.</span><span class="sxs-lookup"><span data-stu-id="a44c5-115">Includes the FTS4, FTS5, JSON1, and R\*Tree extensions.</span></span> <span data-ttu-id="a44c5-116">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="a44c5-116">This is the default.</span></span> |
| <span data-ttu-id="a44c5-117">SQLitePCLRaw. bundle_green</span><span class="sxs-lookup"><span data-stu-id="a44c5-117">SQLitePCLRaw.bundle_green</span></span> | <span data-ttu-id="a44c5-118">System SQLite kitaplığını kullandığı iOS dışında bundle_e_sqlite3 ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="a44c5-118">Same as bundle_e_sqlite3, except on iOS where it uses the system SQLite library.</span></span> |
| <span data-ttu-id="a44c5-119">SQLitePCLRaw. bundle_zetetic</span><span class="sxs-lookup"><span data-stu-id="a44c5-119">SQLitePCLRaw.bundle_zetetic</span></span> | <span data-ttu-id="a44c5-120">Zetetik 'dan (dahil değil) resmi SQLCipher derlemelerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="a44c5-120">Uses the official SQLCipher builds from Zetetic (not included).</span></span> |
| <span data-ttu-id="a44c5-121">SQLitePCLRaw. bundle_winsqlite3</span><span class="sxs-lookup"><span data-stu-id="a44c5-121">SQLitePCLRaw.bundle_winsqlite3</span></span> | <span data-ttu-id="a44c5-122">Windows 10 ' da sistem SQLite kitaplığı olan winsqlite3. dll ' yi kullanır.</span><span class="sxs-lookup"><span data-stu-id="a44c5-122">Uses winsqlite3.dll, the system SQLite library on Windows 10.</span></span> |
| <span data-ttu-id="a44c5-123">SQLitePCLRaw. bundle_e_sqlcipher</span><span class="sxs-lookup"><span data-stu-id="a44c5-123">SQLitePCLRaw.bundle_e_sqlcipher</span></span> | <span data-ttu-id="a44c5-124">, Bir SQLCipher 'ın resmi olmayan, açık kaynaklı bir derlemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="a44c5-124">Provides an unofficial, open-source build of SQLCipher.</span></span> |

<span data-ttu-id="a44c5-125">Örneğin, bir SQLCipher 'ın resmi olmayan, açık kaynaklı derlemesini kullanmak için aşağıdaki komutları kullanın.</span><span class="sxs-lookup"><span data-stu-id="a44c5-125">For example, to use the unofficial, open-source build of SQLCipher use the following commands.</span></span>

### <a name="net-core-cli"></a>[<span data-ttu-id="a44c5-126">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="a44c5-126">.NET Core CLI</span></span>](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite.Core
dotnet add package SQLitePCLRaw.bundle_e_sqlcipher
```

### <a name="visual-studio"></a>[<span data-ttu-id="a44c5-127">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a44c5-127">Visual Studio</span></span>](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite.Core
Install-Package SQLitePCLRaw.bundle_e_sqlcipher
```

---

## <a name="sqlitepclraw-providers"></a><span data-ttu-id="a44c5-128">SQLitePCLRaw sağlayıcıları</span><span class="sxs-lookup"><span data-stu-id="a44c5-128">SQLitePCLRaw providers</span></span>

<span data-ttu-id="a44c5-129">`SQLitePCLRaw.provider.dynamic_cdecl` Paketten yararlanarak kendi SQLite yapınızı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a44c5-129">You can use your own build of SQLite by leveraging the `SQLitePCLRaw.provider.dynamic_cdecl` package.</span></span> <span data-ttu-id="a44c5-130">Bu durumda, yerel kitaplığı uygulamanızla dağıtmaktan sorumlu olursunuz.</span><span class="sxs-lookup"><span data-stu-id="a44c5-130">In this case, you're responsible for deploying the native library with your app.</span></span> <span data-ttu-id="a44c5-131">Bu şekilde, uygulamanıza yerel kitaplıklar dağıtmanın ayrıntıları, kullandığınız .NET platformu ve çalışma zamanına bağlı olarak önemli ölçüde farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="a44c5-131">Note, the details of deploying native libraries with your app vary considerably depending on which .NET platform and runtime you're using.</span></span>

<span data-ttu-id="a44c5-132">İlk olarak, IGetFunctionPointer uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a44c5-132">First, you'll need to implement IGetFunctionPointer.</span></span> <span data-ttu-id="a44c5-133">Uygulama .NET Core üzerinde oldukça basit.</span><span class="sxs-lookup"><span data-stu-id="a44c5-133">The implementation is fairly trivial on .NET Core.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SystemLibrarySample/Program.cs?name=snippet_NativeLibraryAdapter)]

<span data-ttu-id="a44c5-134">Sonra, SQLitePCLRaw sağlayıcısını yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="a44c5-134">Next, configure the SQLitePCLRaw provider.</span></span> <span data-ttu-id="a44c5-135">Uygulamanızda Microsoft. Data. SQLite kullanılmadan önce bunun yapıldığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="a44c5-135">Ensure this is done before Microsoft.Data.Sqlite is used in your app.</span></span> <span data-ttu-id="a44c5-136">Ayrıca, sağlayıcınızı geçersiz kılabilecek bir SQLitePCLRaw demeti paketi kullanmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="a44c5-136">Also, avoid using a SQLitePCLRaw bundle package which might override your provider.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SystemLibrarySample/Program.cs?name=snippet_SetProvider)]
