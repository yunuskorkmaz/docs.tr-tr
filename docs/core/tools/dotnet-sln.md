---
title: dotnet sln komutu
description: dotnet-sln komutu, çözüm dosyasındaki projeleri eklemek, kaldırmak ve listelemek için kullanışlı bir seçenek sağlar.
ms.date: 02/14/2020
ms.openlocfilehash: 615e25e30a63b6ca36d9898cfcde565053830572
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389646"
---
# <a name="dotnet-sln"></a>dotnet sln

**Bu makale şu şekilde dir:** ✔️ .NET Core 2.x SDK ve sonraki sürümler

## <a name="name"></a>Adı

`dotnet sln`- Projeleri .NET Core çözüm dosyasında listeler veya değiştirir.

## <a name="synopsis"></a>Özet

```dotnetcli
dotnet sln [<SOLUTION_FILE>] [command] [-h|--help]
```

## <a name="description"></a>Açıklama

Komut, `dotnet sln` bir çözüm dosyasındaki projeleri listelemek ve değiştirmek için kullanışlı bir yol sağlar.

Komutu `dotnet sln` kullanmak için çözüm dosyasının zaten var olması gerekir. Bir tane oluşturmanız gerekiyorsa, aşağıdaki örnekte olduğu gibi [dotnet yeni](dotnet-new.md) komutunu kullanın:

```dotnetcli
dotnet new sln
```

## <a name="arguments"></a>Bağımsız Değişkenler

- **`SOLUTION_FILE`**

  Kullanılacak çözüm dosyası. Bu bağımsız değişken atlanırsa, komut geçerli dizini arar. Çözüm dosyası veya birden çok çözüm dosyası bulamazsa, komut başarısız olur.

## <a name="options"></a>Seçenekler

- **`-h|--help`**

  Komutun nasıl kullanılacağına ilişkin bir açıklama sızıntılır.

## <a name="commands"></a>Komutlar

### `list`

Çözüm dosyasındaki tüm projeleri listeler.

#### <a name="synopsis"></a>Özet

```dotnetcli
dotnet sln list [-h|--help]
```

#### <a name="arguments"></a>Bağımsız Değişkenler

- **`SOLUTION_FILE`**

  Kullanılacak çözüm dosyası. Bu bağımsız değişken atlanırsa, komut geçerli dizini arar. Çözüm dosyası veya birden çok çözüm dosyası bulamazsa, komut başarısız olur.

#### <a name="options"></a>Seçenekler

- **`-h|--help`**

  Komutun nasıl kullanılacağına ilişkin bir açıklama sızıntılır.
  
### `add`

Çözüm dosyasına bir veya daha fazla proje ekler.

#### <a name="synopsis"></a>Özet

```dotnetcli
dotnet sln [<SOLUTION_FILE>] add [--in-root] [-s|--solution-folder] <PROJECT_PATH> [<PROJECT_PATH>...]
dotnet sln add [-h|--help]
```

#### <a name="arguments"></a>Bağımsız Değişkenler

- **`SOLUTION_FILE`**

  Kullanılacak çözüm dosyası. Belirtilmemişse, komut geçerli dizini arar ve birden çok çözüm dosyası varsa başarısız olur.

- **`PROJECT_PATH`**

  Çözüme eklenecek proje veya projelere giden yol. Unix/Linux kabuk [globbing desen](https://en.wikipedia.org/wiki/Glob_(programming)) genişletmeleri `dotnet sln` komut u tarafından doğru bir şekilde işlenir.

#### <a name="options"></a>Seçenekler

- **`-h|--help`**

  Komutun nasıl kullanılacağına ilişkin bir açıklama sızıntılır.

- **`--in-root`**

  Projeleri çözüm klasörü oluşturmak yerine çözümün köküne yerleştirir. .NET Core 3.0 SDK'dan beri mevcuttur.

- **`-s|--solution-folder`**

  Projeleri eklemek için hedef çözüm klasörü yolu. .NET Core 3.0 SDK'dan beri mevcuttur.

### `remove`

Bir projeyi veya birden çok projeyi çözüm dosyasından kaldırır.

#### <a name="synopsis"></a>Özet

```dotnetcli
dotnet sln [<SOLUTION_FILE>] remove <PROJECT_PATH> [<PROJECT_PATH>...]
dotnet sln [<SOLUTION_FILE>] remove [-h|--help]
```

#### <a name="arguments"></a>Bağımsız Değişkenler

- **`SOLUTION_FILE`**

  Kullanılacak çözüm dosyası. Belirtilmemiş bırakılırsa, komut geçerli dizini arar ve birden çok çözüm dosyası varsa başarısız olur.

- **`PROJECT_PATH`**

  Çözüme eklenecek proje veya projelere giden yol. Unix/Linux kabuk [globbing desen](https://en.wikipedia.org/wiki/Glob_(programming)) genişletmeleri `dotnet sln` komut u tarafından doğru bir şekilde işlenir.

#### <a name="options"></a>Seçenekler

- **`-h|--help`**

  Komutun nasıl kullanılacağına ilişkin bir açıklama sızıntılır.

## <a name="examples"></a>Örnekler

- Projeleri bir çözümde listele:

  ```dotnetcli
  dotnet sln todo.sln list
  ```

- Çözüme C# projesi ekleyin:

  ```dotnetcli
  dotnet sln add todo-app/todo-app.csproj
  ```

- Bir C# projesini çözümden kaldırın:

  ```dotnetcli
  dotnet sln remove todo-app/todo-app.csproj
  ```

- Bir çözümün köküne birden çok C# projesi ekleyin:

  ```dotnetcli
  dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj --in-root
  ```

- Bir çözüme birden çok C# projesi ekleyin:

  ```dotnetcli
  dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj
  ```

- Birden çok C# projesinin çözümden kaldırılması:

  ```dotnetcli
  dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj
  ```

- Globbing deseni (yalnızca Unix/Linux) kullanarak bir çözüme birden fazla C# projesi ekleyin:

  ```dotnetcli
  dotnet sln todo.sln add **/*.csproj
  ```

- Globbing deseni (yalnızca Windows PowerShell) kullanarak çözüme birden çok C# projesi ekleyin:

  ```dotnetcli
  dotnet sln todo.sln add (ls **/*.csproj)
  ```

- Birden fazla C# projesinin bir çözümden globbing deseni (yalnızca Unix/Linux) kullanarak çıkarılması:

  ```dotnetcli
  dotnet sln todo.sln remove **/*.csproj
  ```

- Birden çok C# projesiglobbing deseni kullanarak çözümden (yalnızca Windows PowerShell):

  ```dotnetcli
  dotnet sln todo.sln remove (ls **/*.csproj)
  ```
