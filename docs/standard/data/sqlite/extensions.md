---
title: Uzantıları
ms.date: 12/08/2020
description: SQLite uzantılarını yüklemeyi öğrenin.
ms.openlocfilehash: 45ef5d2e5e8ea1f25866d3239e06fc87d8a91d44
ms.sourcegitcommit: e3cf8227573e13b8e1f4e3dc007404881cdafe47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/11/2021
ms.locfileid: "103190053"
---
# <a name="extensions"></a>Uzantıları

SQLite çalışma zamanında uzantıları yüklemeyi destekler. Uzantılar ek SQL işlevleri, harmanlamalar, sanal tablolar ve daha fazlası gibi şeyleri içerir.

.NET Core, başvurulan NuGet paketleri gibi ek yerlerde yerel kitaplıkları bulmaya yönelik ek mantık içerir. Ne yazık ki, SQLite bu mantığdan yararlanamaz; doğrudan kitaplık yüklemek için platform API 'sini çağırır. Bu nedenle, SQLite uzantılarını yüklemeden önce yolu, LD_LIBRARY_PATH veya DYLD_LIBRARY_PATH ortam değişkenlerini değiştirmeniz gerekebilir. GitHub 'da, başvurulan bir NuGet paketinin içindeki geçerli çalışma zamanı için ikili dosyaların bulmayı gösteren [bir örnek](https://github.com/dotnet/docs/blob/main/samples/snippets/standard/data/sqlite/ExtensionsSample/Program.cs) vardır.

Bir uzantıyı yüklemek için <xref:Microsoft.Data.Sqlite.SqliteConnection.LoadExtension%2A> yöntemini çağırın. Microsoft. Data. SQLite, bağlantı kapatılıp yeniden açıldığı halde uzantının yüklendiğinden emin olur.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/ExtensionsSample/Program.cs?name=snippet_LoadExtension)]

> [!NOTE]
> Loadexgerme yöntemi 3,0 sürümüne eklenmiştir.

## <a name="see-also"></a>Ayrıca bkz.

* [Çalışma zamanı yüklenebilir uzantıları](https://www.sqlite.org/loadext.html)
