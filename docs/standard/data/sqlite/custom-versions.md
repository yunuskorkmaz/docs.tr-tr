---
title: Özel SQLite sürümleri
ms.date: 12/13/2019
description: Yerel SQLite kitaplığı 'nın özel bir sürümünü nasıl kullanacağınızı öğrenin.
ms.openlocfilehash: 8a2646138ea9dbecf412a2e8e0e347e2d71a5b0b
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447148"
---
# <a name="custom-sqlite-versions"></a>Özel SQLite sürümleri

Microsoft. Data. SQLite, SQLitePCLRaw üzerine kurulmuştur. Bir paket kullanarak veya bir SQLitePCLRaw sağlayıcısı yapılandırarak yerel SQLite kitaplığının özel sürümlerini kullanabilirsiniz.

## <a name="bundles"></a>Paketi

SQLitePCLRaw, farklı platformlarda doğru bağımlılıklara kolayca getirmeyi kolaylaştıran paket paketleri sağlar.

Ana Microsoft. Data. SQLite paketi varsayılan olarak SQLitePCLRaw. bundle_e_sqlite3 ' ye getirir.

Farklı bir paket kullanmak için, kullanmak istediğiniz paket paketiyle birlikte `Microsoft.Data.Sqlite.Core` paketini de yükleyebilirsiniz. Paketleri Microsoft. Data. SQLite tarafından otomatik olarak başlatılır.

| Paket | Açıklama |
| --- | --- |
| SQLitePCLRaw. bundle_e_sqlite3 | Tüm platformlarda SQLite ' un tutarlı bir sürümünü sağlar. FTS4, FTS5, JSON1 ve | R * ağaç uzantıları. Bu varsayılandır. |
| SQLitePCLRaw. bundle_green | System SQLite kitaplığını kullandığı iOS dışında bundle_e_sqlite3 ile aynıdır. |
| SQLitePCLRaw. bundle_zetetic | Zetetik 'dan (dahil değil) resmi SQLCipher derlemelerini kullanır. |
| SQLitePCLRaw. bundle_winsqlite3 | Windows 10 ' da sistem SQLite kitaplığı olan winsqlite3. dll ' yi kullanır. |
| SQLitePCLRaw. bundle_e_sqlcipher | , Bir SQLCipher 'ın resmi olmayan, açık kaynaklı bir derlemesini sağlar. |

Örneğin, bir SQLCipher 'ın resmi olmayan, açık kaynaklı derlemesini kullanmak için aşağıdaki komutları kullanın.

### <a name="net-core-clitabnetcore-cli"></a>[.NET Core CLI](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite.Core
dotnet add package SQLitePCLRaw.bundle_e_sqlcipher
```

### <a name="visual-studiotabvisual-studio"></a>[Visual Studio](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite.Core
Install-Package SQLitePCLRaw.bundle_e_sqlcipher
```

---

## <a name="sqlitepclraw-providers"></a>SQLitePCLRaw sağlayıcıları

`SQLitePCLRaw.provider.dynamic_cdecl` paketinden yararlanarak, kendi SQLite yapınızı kullanabilirsiniz. Bu durumda, yerel kitaplığı uygulamanızla dağıtmaktan sorumlu olursunuz. Bu şekilde, uygulamanıza yerel kitaplıklar dağıtmanın ayrıntıları, kullandığınız .NET platformu ve çalışma zamanına bağlı olarak önemli ölçüde farklılık gösterir.

İlk olarak, IGetFunctionPointer uygulamanız gerekir. Uygulama .NET Core üzerinde oldukça basit.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SystemLibrarySample/Program.cs?name=snippet_NativeLibraryAdapter)]

Sonra, SQLitePCLRaw sağlayıcısını yapılandırın. Uygulamanızda Microsoft. Data. SQLite kullanılmadan önce bunun yapıldığından emin olun. Ayrıca, sağlayıcınızı geçersiz kılabilecek bir SQLitePCLRaw demeti paketi kullanmaktan kaçının.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SystemLibrarySample/Program.cs?name=snippet_SetProvider)]
