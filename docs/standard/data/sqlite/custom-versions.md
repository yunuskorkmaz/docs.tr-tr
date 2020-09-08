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
# <a name="custom-sqlite-versions"></a>Özel SQLite sürümleri

`Microsoft.Data.Sqlite` , üzerine kurulmuştur `SQLitePCLRaw` . Bir paket kullanarak veya bir sağlayıcıyı yapılandırarak yerel SQLite kitaplığının özel sürümlerini kullanabilirsiniz `SQLitePCLRaw` .

## <a name="bundles"></a>Paketi

`SQLitePCLRaw` , farklı platformlarda doğru bağımlılıklara kolayca gelmesini kolaylaştıran, kullanışlı tabanlı paket paketleri sağlar. Ana `Microsoft.Data.Sqlite` paket varsayılan olarak ' i sunar `SQLitePCLRaw.bundle_e_sqlite3` . Farklı bir paket kullanmak için, kullanmak istediğiniz paket `Microsoft.Data.Sqlite.Core` paketiyle birlikte bunun yerine paketini de yükleyebilirsiniz. Paketleri tarafından otomatik olarak başlatılır `Microsoft.Data.Sqlite` .

| Paket | Description |
|--|--|
| [SQLitePCLRaw. bundle_e_sqlite3](https://www.nuget.org/packages/SQLitePCLRaw.bundle_e_sqlite3) | Tüm platformlarda SQLite ' un tutarlı bir sürümünü sağlar. FTS4, FTS5, JSON1 ve R * ağaç uzantılarını içerir. Bu varsayılan seçenektir. |
| [SQLitePCLRaw. bundle_e_sqlcipher](https://www.nuget.org/packages/SQLitePCLRaw.bundle_e_sqlcipher) | Resmi olmayan, açık kaynaklı bir yapı sağlar `SQLCipher` . |
| [SQLitePCLRaw. bundle_green](https://www.nuget.org/packages/SQLitePCLRaw.bundle_green) | `bundle_e_sqlite3`İOS dışında, sistem SQLite kitaplığını kullandığında, ile aynıdır. |
| [SQLitePCLRaw. bundle_sqlite3](https://www.nuget.org/packages/SQLitePCLRaw.bundle_sqlite3) | , Sistem SQLite kitaplığını kullanır. |
| [SQLitePCLRaw. bundle_winsqlite3](https://www.nuget.org/packages/SQLitePCLRaw.bundle_winsqlite3) | `winsqlite3.dll`, Windows 10 ' da sistem SQLite Kitaplığı ' nı kullanır. |
| [SQLitePCLRaw. bundle_zetetic](https://www.nuget.org/packages/SQLitePCLRaw.bundle_zetetic) | `SQLCipher`Zetetik 'dan (dahil değil) resmi derlemeler kullanır. |

Örneğin, resmi olmayan, açık kaynaklı bir derlemesini kullanmak için `SQLCipher` aşağıdaki komutları kullanın.

### <a name="net-core-cli"></a>[.NET Core CLI](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite.Core
dotnet add package SQLitePCLRaw.bundle_e_sqlcipher
```

### <a name="visual-studio"></a>[Visual Studio](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite.Core
Install-Package SQLitePCLRaw.bundle_e_sqlcipher
```

---

## <a name="sqlitepclraw-available-providers"></a>SQLitePCLRaw kullanılabilir sağlayıcılar

Bir pakete bağlı olmadığında, çekirdek derleme ile kullanılabilir SQLite sağlayıcıları kullanabilirsiniz.

| Sağlayıcı | Description |
|--|--|
| [SQLitePCLRaw. Provider. Dynamic](https://www.nuget.org/packages/SQLitePCLRaw.provider.dynamic) | `dynamic`Sağlayıcı, öznitelikleri kullanmak yerine yerel kitaplığı yükler <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=nameWithType> . Bu sağlayıcıyı kullanma hakkında daha fazla bilgi için bkz. [dinamik sağlayıcıyı kullanma](#use-the-dynamic-provider). |
| [SQLitePCLRaw. Provider. e_sqlite3](https://www.nuget.org/packages/SQLitePCLRaw.provider.e_sqlite3) | `e_sqlite3`Varsayılan sağlayıcıdır. |
| [SQLitePCLRaw. Provider. e_sqlcipher](https://www.nuget.org/packages/SQLitePCLRaw.provider.e_sqlcipher) | `e_sqlcipher`Sağlayıcı, resmi olmayan ve desteklenmeyen bir sağlayıcıdır `SQLCipher` . |
| [SQLitePCLRaw. Provider. SQLite3](https://www.nuget.org/packages/SQLitePCLRaw.provider.sqlite3) | `sqlite3`Sağlayıcı `SQLite` IOS, MacOS ve Linux için sunulan bir sistemdir. |
| [SQLitePCLRaw. Provider. sqlcipher](https://www.nuget.org/packages/SQLitePCLRaw.provider.sqlcipher) | Sağlayıcı, ' `sqlcipher` den resmi `SQLCipher` derlemeler içindir `Zetetic` . |
| [SQLitePCLRaw. Provider. winsqlite3](https://www.nuget.org/packages/SQLitePCLRaw.provider.winsqlite3) | `winsqlite3`Sağlayıcı, Windows 10 ortamları içindir. |

Sağlayıcıyı kullanmak için `sqlite3` aşağıdaki komutları kullanın:

### <a name="net-core-cli"></a>[.NET Core CLI](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite.Core
dotnet add package SQLitePCLRaw.core
dotnet add package SQLitePCLRaw.provider.sqlite3
```

### <a name="visual-studio"></a>[Visual Studio](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite.Core
Install-Package SQLitePCLRaw.core
Install-Package SQLitePCLRaw.provider.sqlite3
```

---

Paketler yüklü olduğunda, sağlayıcıyı `sqlite3` örnekle ayarlarsınız.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SqliteProviderSample/Program.cs)]

## <a name="use-the-dynamic-provider"></a>Dinamik sağlayıcıyı kullan

Paketten yararlanarak kendi SQLite yapınızı kullanabilirsiniz `SQLitePCLRaw.provider.dynamic_cdecl` . Bu durumda, yerel kitaplığı uygulamanızla dağıtmaktan sorumlu olursunuz. Bu şekilde, uygulamanıza yerel kitaplıklar dağıtmanın ayrıntıları, kullandığınız .NET platformu ve çalışma zamanına bağlı olarak önemli ölçüde farklılık gösterir.

Öncelikle uygulamanız gerekir `IGetFunctionPointer` . .NET Core üzerinde uygulama aşağıdaki gibidir:

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SystemLibrarySample/Program.cs?name=snippet_NativeLibraryAdapter)]

Ardından, sağlayıcıyı yapılandırın `SQLitePCLRaw` . Uygulamanızda kullanılmadan önce bunun yapıldığından emin olun `Microsoft.Data.Sqlite` . Ayrıca, `SQLitePCLRaw` sağlayıcınızı geçersiz kılabilecek bir paket paketi kullanmaktan kaçının.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SystemLibrarySample/Program.cs?name=snippet_SetProvider)]
