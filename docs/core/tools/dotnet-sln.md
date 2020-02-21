---
title: DotNet sln komutu
description: DotNet-sln komutu bir çözüm dosyasındaki projeleri eklemek, kaldırmak ve listelemek için kullanışlı bir seçenek sağlar.
ms.date: 02/14/2020
ms.openlocfilehash: b2455c04a46b2a10b8142d8ddc2d8129f2154b27
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543488"
---
# <a name="dotnet-sln"></a>dotnet sln

**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 2. x SDK ve sonraki sürümleri

## <a name="name"></a>Adı

`dotnet sln`-bir .NET Core çözüm dosyasındaki projeleri listeler veya değiştirir.

## <a name="synopsis"></a>Özeti

```dotnetcli
dotnet sln [<SOLUTION_FILE>] [command] [-h|--help]
```

## <a name="description"></a>Açıklama

`dotnet sln` komutu bir çözüm dosyasındaki projeleri listelemek ve değiştirmek için kullanışlı bir yol sağlar.

`dotnet sln` komutunu kullanmak için, çözüm dosyası zaten var olmalıdır. Bir tane oluşturmanız gerekiyorsa, aşağıdaki örnekte olduğu gibi [DotNet New](dotnet-new.md) komutunu kullanın:

```dotnetcli
dotnet new sln
```

## <a name="arguments"></a>Bağımsız Değişkenler

- **`SOLUTION_FILE`**

  Kullanılacak çözüm dosyası. Bu bağımsız değişken atlanırsa, komut geçerli dizinde bir arar. Çözüm dosyası veya birden çok çözüm dosyası bulursa, komut başarısız olur.

## <a name="options"></a>Seçenekler

- **`-h|--help`**

  Komutunun nasıl kullanılacağına ilişkin bir açıklama yazdırır.

## <a name="commands"></a>Komutlar

### `list`

Bir çözüm dosyasındaki tüm projeleri listeler.

#### <a name="synopsis"></a>Özeti

```dotnetcli
dotnet sln list [-h|--help]
```

#### <a name="arguments"></a>Bağımsız Değişkenler

- **`SOLUTION_FILE`**

  Kullanılacak çözüm dosyası. Bu bağımsız değişken atlanırsa, komut geçerli dizinde bir arar. Çözüm dosyası veya birden çok çözüm dosyası bulursa, komut başarısız olur.

#### <a name="options"></a>Seçenekler

- **`-h|--help`**

  Komutunun nasıl kullanılacağına ilişkin bir açıklama yazdırır.
  
### `add`

Çözüm dosyasına bir veya daha fazla proje ekler.

#### <a name="synopsis"></a>Özeti

```dotnetcli
dotnet sln [<SOLUTION_FILE>] add [--in-root] [-s|--solution-folder] <PROJECT_PATH> [<PROJECT_PATH>...]
dotnet sln add [-h|--help]
```

#### <a name="arguments"></a>Bağımsız Değişkenler

- **`SOLUTION_FILE`**

  Kullanılacak çözüm dosyası. Belirtilmemişse, komut geçerli dizinde bir arar ve birden çok çözüm dosyası varsa başarısız olur.

- **`PROJECT_PATH`**

  Çözüme eklenecek projenin veya projelerin yolu. UNIX/Linux kabuğu [Glob model](https://en.wikipedia.org/wiki/Glob_(programming)) genişletmeleri `dotnet sln` komutu tarafından doğru şekilde işlenir.

#### <a name="options"></a>Seçenekler

- **`-h|--help`**

  Komutunun nasıl kullanılacağına ilişkin bir açıklama yazdırır.

- **`--in-root`**

  Bir çözüm klasörü oluşturmak yerine, projeleri çözümün köküne koyar. .NET Core 3,0 SDK 'dan beri kullanılabilir.

- **`-s|--solution-folder`**

  Projelerin ekleneceği hedef çözüm klasörünün yolu. .NET Core 3,0 SDK 'dan beri kullanılabilir.

### `remove`

Çözüm dosyasından bir projeyi veya birden çok projeyi kaldırır.

#### <a name="synopsis"></a>Özeti

```dotnetcli
dotnet sln [<SOLUTION_FILE>] remove <PROJECT_PATH> [<PROJECT_PATH>...]
dotnet sln [<SOLUTION_FILE>] remove [-h|--help]
```

#### <a name="arguments"></a>Bağımsız Değişkenler

- **`SOLUTION_FILE`**

  Kullanılacak çözüm dosyası. Belirtilmemişse, komut geçerli dizinde bir arar ve birden çok çözüm dosyası varsa başarısız olur.

- **`PROJECT_PATH`**

  Çözüme eklenecek projenin veya projelerin yolu. UNIX/Linux kabuğu [Glob model](https://en.wikipedia.org/wiki/Glob_(programming)) genişletmeleri `dotnet sln` komutu tarafından doğru şekilde işlenir.

#### <a name="options"></a>Seçenekler

- **`-h|--help`**

  Komutunun nasıl kullanılacağına ilişkin bir açıklama yazdırır.

## <a name="examples"></a>Örnekler

- Bir çözümdeki projeleri listeleyin:

  ```dotnetcli
  dotnet sln todo.sln list
  ```

- Bir çözüme C# proje ekleme:

  ```dotnetcli
  dotnet sln add todo-app/todo-app.csproj
  ```

- Bir C# projeyi çözümden kaldırma:

  ```dotnetcli
  dotnet sln remove todo-app/todo-app.csproj
  ```

- Bir çözümün C# köküne birden çok proje ekleyin:

  ```dotnetcli
  dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj --in-root
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
