---
title: Uzantıları
ms.date: 12/13/2019
description: SQLite uzantılarını yüklemeyi öğrenin.
ms.openlocfilehash: a85b1227be4274dd20156d2475d6d2d68e250f99
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901290"
---
# <a name="extensions"></a><span data-ttu-id="2a25c-103">Uzantıları</span><span class="sxs-lookup"><span data-stu-id="2a25c-103">Extensions</span></span>

<span data-ttu-id="2a25c-104">SQLite çalışma zamanında uzantıları yüklemeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="2a25c-104">SQLite supports loading extensions at run time.</span></span> <span data-ttu-id="2a25c-105">Uzantılar ek SQL işlevleri, harmanlamalar, sanal tablolar ve daha fazlası gibi şeyleri içerir.</span><span class="sxs-lookup"><span data-stu-id="2a25c-105">Extensions include things like additional SQL functions, collations, virtual tables, and more.</span></span>

<span data-ttu-id="2a25c-106">.NET Core, başvurulan NuGet paketleri gibi ek yerlerde yerel kitaplıkları bulmaya yönelik ek mantık içerir.</span><span class="sxs-lookup"><span data-stu-id="2a25c-106">.NET Core includes additional logic for locating native libraries in additional places like referenced NuGet packages.</span></span> <span data-ttu-id="2a25c-107">Ne yazık ki, SQLite bu mantığdan yararlanamaz; doğrudan kitaplık yüklemek için platform API 'sini çağırır.</span><span class="sxs-lookup"><span data-stu-id="2a25c-107">Unfortunately, SQLite can't leverage this logic; it calls the platform API directly to load libraries.</span></span> <span data-ttu-id="2a25c-108">Bu nedenle, SQLite uzantılarını yüklemeden önce yolu, LD_LIBRARY_PATH veya DYLD_LIBRARY_PATH ortam değişkenlerini değiştirmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="2a25c-108">Because of this, you may need to modify the PATH, LD_LIBRARY_PATH, or DYLD_LIBRARY_PATH environment variables before loading SQLite extensions.</span></span> <span data-ttu-id="2a25c-109">GitHub 'da, başvurulan bir NuGet paketinin içindeki geçerli çalışma zamanı için ikili dosyaların bulmayı gösteren [bir örnek](https://github.com/dotnet/samples/blob/master/snippets/standard/data/sqlite/ExtensionsSample/Program.cs) vardır.</span><span class="sxs-lookup"><span data-stu-id="2a25c-109">There's [a sample](https://github.com/dotnet/samples/blob/master/snippets/standard/data/sqlite/ExtensionsSample/Program.cs) on GitHub that demonstrates finding binaries for the current runtime inside a referenced NuGet package.</span></span>

<span data-ttu-id="2a25c-110">Bir uzantıyı yüklemek için <xref:Microsoft.Data.Sqlite.SqliteConnection.LoadExtension%2A> yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="2a25c-110">To load an extension, call the <xref:Microsoft.Data.Sqlite.SqliteConnection.LoadExtension%2A> method.</span></span> <span data-ttu-id="2a25c-111">Microsoft. Data. SQLite, bağlantı kapatılıp yeniden açıldığı halde uzantının yüklendiğinden emin olur.</span><span class="sxs-lookup"><span data-stu-id="2a25c-111">Microsoft.Data.Sqlite will ensure that the extension remains loaded even if the connection is closed and reopened.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/ExtensionsSample/Program.cs?name=snippet_LoadExtension)]

## <a name="see-also"></a><span data-ttu-id="2a25c-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2a25c-112">See also</span></span>

* [<span data-ttu-id="2a25c-113">Çalışma zamanı yüklenebilir uzantıları</span><span class="sxs-lookup"><span data-stu-id="2a25c-113">Run-Time Loadable Extensions</span></span>](https://www.sqlite.org/loadext.html)
