---
title: Uzantıları
ms.date: 12/13/2019
description: SQLite uzantılarını nasıl yükleyeriz öğrenin.
ms.openlocfilehash: 51c705349c25240fe42e0edda8004a3e3b013ca3
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242965"
---
# <a name="extensions"></a>Uzantıları

SQLite, çalışma zamanında yükleme uzantılarını destekler. Uzantılar ek SQL işlevleri, harmanlamalar, sanal tablolar ve daha fazlası gibi şeyleri içerir.

.NET Core, başvurulan NuGet paketleri gibi ek yerlerde yerel kitaplıkları bulmak için ek mantık içerir. Ne yazık ki, SQLite bu mantık kaldıraç olamaz; platform API'sini doğrudan yükleme kitaplıklarına çağırır. Bu nedenle, SQLite uzantılarını yüklemeden önce PATH, LD_LIBRARY_PATH veya DYLD_LIBRARY_PATH ortam değişkenlerini değiştirmeniz gerekebilir. GitHub'da başvurulan Bir NuGet paketinin içinde geçerli çalışma süresi için ikili leri bulmayı gösteren bir [örnek](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/ExtensionsSample/Program.cs) vardır.

Uzantı yüklemek için <xref:Microsoft.Data.Sqlite.SqliteConnection.LoadExtension%2A> yöntemi arayın. Microsoft.Data.Sqlite, bağlantı kapatılsa ve yeniden açılsa bile uzantıntın yüklü kalmasını sağlar.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/ExtensionsSample/Program.cs?name=snippet_LoadExtension)]

## <a name="see-also"></a>Ayrıca bkz.

* [Run-Time Yüklenebilir Uzantılar](https://www.sqlite.org/loadext.html)
