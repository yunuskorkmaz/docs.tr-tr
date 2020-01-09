---
title: Uzantıları
ms.date: 12/13/2019
description: SQLite uzantılarını yüklemeyi öğrenin.
ms.openlocfilehash: ab00ccf31b8a22407fc177c18149fe4825a19091
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447260"
---
# <a name="extensions"></a><span data-ttu-id="69a02-103">Uzantıları</span><span class="sxs-lookup"><span data-stu-id="69a02-103">Extensions</span></span>

<span data-ttu-id="69a02-104">SQLite çalışma zamanında uzantıları yüklemeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="69a02-104">SQLite supports loading extensions at run time.</span></span> <span data-ttu-id="69a02-105">Uzantılar ek SQL işlevleri, harmanlamalar, sanal tablolar ve daha fazlası gibi şeyleri içerir.</span><span class="sxs-lookup"><span data-stu-id="69a02-105">Extensions include things like additional SQL functions, collations, virtual tables, and more.</span></span>

<span data-ttu-id="69a02-106">.NET Core, başvurulan NuGet paketleri gibi ek yerlerde yerel kitaplıkları bulmaya yönelik ek mantık içerir.</span><span class="sxs-lookup"><span data-stu-id="69a02-106">.NET Core includes additional logic for locating native libraries in additional places like referenced NuGet packages.</span></span> <span data-ttu-id="69a02-107">Ne yazık ki, SQLite bu mantığdan yararlanamaz; doğrudan kitaplık yüklemek için platform API 'sini çağırır.</span><span class="sxs-lookup"><span data-stu-id="69a02-107">Unfortunately, SQLite can't leverage this logic; it calls the platform API directly to load libraries.</span></span> <span data-ttu-id="69a02-108">Bu nedenle, uygulamanızın SQLite uzantılarını yüklemeden önce yolu, LD_LIBRARY_PATH veya DYLD_LIBRARY_PATH ortam değişkenlerini değiştirmesi gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="69a02-108">Because of this, your app may need to modify the PATH, LD_LIBRARY_PATH, or DYLD_LIBRARY_PATH environment variables before loading SQLite extensions.</span></span> <span data-ttu-id="69a02-109">GitHub 'da, başvurulan bir NuGet paketinin içindeki geçerli çalışma zamanı için ikili dosyaların bulmayı gösteren [bir örnek](https://github.com/dotnet/samples/blob/master/samples/snippets/standard/data/sqlite/ExtensionsSample/Program.cs) vardır.</span><span class="sxs-lookup"><span data-stu-id="69a02-109">There's [a sample](https://github.com/dotnet/samples/blob/master/samples/snippets/standard/data/sqlite/ExtensionsSample/Program.cs) on GitHub that demonstrates finding binaries for the current runtime inside a referenced NuGet package.</span></span>

<span data-ttu-id="69a02-110">Bir uzantıyı yüklemek için <xref:Microsoft.Data.Sqlite.SqliteConnection.LoadExtension%2A> yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="69a02-110">To load an extension, call the <xref:Microsoft.Data.Sqlite.SqliteConnection.LoadExtension%2A> method.</span></span> <span data-ttu-id="69a02-111">Microsoft. Data. SQLite, bağlantı kapatılıp yeniden açıldığı halde uzantının yüklendiğinden emin olur.</span><span class="sxs-lookup"><span data-stu-id="69a02-111">Microsoft.Data.Sqlite will ensure that the extension remains loaded even if the connection is closed and reopened.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/ExtensionsSample/Program.cs?name=snippet_LoadExtension)]

## <a name="see-also"></a><span data-ttu-id="69a02-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="69a02-112">See also</span></span>

* [<span data-ttu-id="69a02-113">Çalışma zamanı yüklenebilir uzantıları</span><span class="sxs-lookup"><span data-stu-id="69a02-113">Run-Time Loadable Extensions</span></span>](https://www.sqlite.org/loadext.html)
