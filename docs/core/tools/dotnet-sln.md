---
title: DotNet sln komutu
description: DotNet-sln komutu bir çözüm dosyasındaki projeleri eklemek, kaldırmak ve listelemek için kullanışlı bir seçenek sağlar.
ms.date: 10/29/2019
ms.openlocfilehash: e344deaae0867202a79a3c38df48a2be8d4d7d13
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733076"
---
# <a name="dotnet-sln"></a>dotnet sln

**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 1. x SDK ve sonraki sürümleri

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Ad

`dotnet sln`-bir .NET Core çözüm dosyasını değiştirir.

## <a name="synopsis"></a>Özeti

```dotnetcli
dotnet sln [<SOLUTION_FILE>] [command] [-h|--help]
```

## <a name="description"></a>Açıklama

`dotnet sln` komutu bir çözüm dosyasındaki projeleri eklemek, kaldırmak ve listelemek için kullanışlı bir yol sağlar.

`dotnet sln` komutunu kullanmak için, çözüm dosyası zaten var olmalıdır. Bir tane oluşturmanız gerekiyorsa, aşağıdaki örnekte olduğu gibi [DotNet New](dotnet-new.md) komutunu kullanın:

```dotnetcli
dotnet new sln
```

## <a name="arguments"></a>Arguments

- **`SOLUTION_FILE`**

  Kullanılacak çözüm dosyası. Belirtilmemişse, komut geçerli dizinde bir arama yapar. Dizinde birden çok çözüm dosyası varsa, birinin belirtilmesi gerekir.

## <a name="options"></a>Seçenekler

- **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

## <a name="commands"></a>Komutlar

### `add`

Çözüm dosyasına bir proje veya birden çok proje ekler.

#### <a name="synopsis"></a>Özeti

```dotnetcli
dotnet sln [<SOLUTION_FILE>] add [--in-root] [-s|--solution-folder] <PROJECT_PATH>
dotnet sln add [-h|--help]
```

#### <a name="arguments"></a>Arguments

- **`SOLUTION_FILE`**

  Kullanılacak çözüm dosyası. Belirtilmemişse, komut geçerli dizinde bir arama yapar. Dizinde birden çok çözüm dosyası varsa, birinin belirtilmesi gerekir.

- **`PROJECT_PATH`**

  Çözüme eklenecek projenin yolu. Boşluktan daha sonra bir tane ekleyerek birden fazla proje ekleyin. UNIX/Linux kabuğu [Glob model](https://en.wikipedia.org/wiki/Glob_(programming)) genişletmeleri `dotnet sln` komutu tarafından doğru şekilde işlenir.

#### <a name="options"></a>Seçenekler

- **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

- **`--in-root`**

  Bir çözüm klasörü oluşturmak yerine, projeleri çözümün köküne koyar. .NET Core 3,0 SDK 'dan beri kullanılabilir.

- **`-s|--solution-folder`**

  Projelerin ekleneceği hedef çözüm klasörünün yolu. .NET Core 3,0 SDK 'dan beri kullanılabilir.

### `remove`

Çözüm dosyasından bir projeyi veya birden çok projeyi kaldırır.

#### <a name="synopsis"></a>Özeti

```dotnetcli
dotnet sln [<SOLUTION_FILE>] remove <PROJECT_PATH>
dotnet sln [<SOLUTION_FILE>] remove [-h|--help]
```

#### <a name="arguments"></a>Arguments

- **`SOLUTION_FILE`**

  Kullanılacak çözüm dosyası. Belirtilmemişse, komut geçerli dizinde bir arama yapar. Dizinde birden çok çözüm dosyası varsa, birinin belirtilmesi gerekir.

- **`PROJECT_PATH`**

  Çözümden kaldırılacak projenin yolu. Boşluktan daha sonra bir tane ekleyerek birden çok projeyi kaldırın. UNIX/Linux kabuğu [Glob model](https://en.wikipedia.org/wiki/Glob_(programming)) genişletmeleri `dotnet sln` komutu tarafından doğru şekilde işlenir.

#### <a name="options"></a>Seçenekler

- **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

### `list`

Bir çözüm dosyasındaki tüm projeleri listeler.

#### <a name="synopsis"></a>Özeti

```dotnetcli
dotnet sln list [-h|--help]
```

#### <a name="arguments"></a>Arguments

- **`SOLUTION_FILE`**

  Kullanılacak çözüm dosyası. Belirtilmemişse, komut geçerli dizinde bir arama yapar. Dizinde birden çok çözüm dosyası varsa, birinin belirtilmesi gerekir.

#### <a name="options"></a>Seçenekler

- **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

## <a name="examples"></a>Örnekler

- Bir çözüme C# proje ekleme:

  ```dotnetcli
  dotnet sln todo.sln add todo-app/todo-app.csproj
  ```

- Bir C# projeyi çözümden kaldırma:

  ```dotnetcli
  dotnet sln todo.sln remove todo-app/todo-app.csproj
  ```

- Bir çözüme C# birden çok proje ekleyin:

  ```dotnetcli
  dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj
  ```

- Bir çözümden C# birden çok proje kaldırma:

  ```dotnetcli
  dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj
  ```

- Bir glob C# kalıbı kullanarak bir çözüme birden çok proje ekleme (yalnızca Unix/Linux):

  ```dotnetcli
  dotnet sln todo.sln add **/*.csproj
  ```

- Bir glob C# kalıbı kullanarak birden çok projeyi çözümden kaldırma (yalnızca Unix/Linux):

  ```dotnetcli
  dotnet sln todo.sln remove **/*.csproj
  ```
