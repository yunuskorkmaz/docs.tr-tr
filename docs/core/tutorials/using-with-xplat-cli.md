---
title: CLI kullanarak .NET Core ile çalışmaya başlama
description: Windows, Linux veya .NET Core komut satırı arabirimi (CLI) kullanarak macOS üzerinde .NET Core ile çalışmaya başlama gösteren adım adım bir öğretici.
author: cartermp
ms.date: 09/10/2018
ms.technology: dotnet-cli
ms.custom: seodec18
ms.openlocfilehash: c57326f038eee4069de9064cb2798d2004b0dbdd
ms.sourcegitcommit: 79066169e93d9d65203028b21983574ad9dcf6b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57212176"
---
# <a name="getting-started-with-net-core-on-windowslinuxmacos-using-the-command-line"></a>Windows/Linus/macos'ta komut satırını kullanarak .NET Core ile çalışmaya başlama

Bu konuda, makinenizde .NET Core CLI araçları ile platformlar arası uygulamalar geliştirmeye başlamak nasıl gösterir.

.NET Core CLI araç takımıyla bilmiyorsanız, okuma [.NET Core SDK'sı genel bakış](../tools/index.md).

## <a name="prerequisites"></a>Önkoşullar

- [.NET core SDK'sını 2.1](https://www.microsoft.com/net/download/core).
- Bir metin düzenleyicisi veya tercih ettiğiniz Kod Düzenleyicisi.

## <a name="hello-console-app"></a>Konsol uygulaması Merhaba!

Yapabilecekleriniz [görüntülemek veya örnek kodu indirdikten](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild) dotnet/samples GitHub deposundan. Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

Bir komut istemi açın ve adlı bir klasör oluşturun *Hello*. Oluşturduğunuz klasöre gidin ve aşağıdaki komutu yazın:

```console
dotnet new console
dotnet run
```

Hızlı bir kılavuz inceleyelim:

1. `dotnet new console`

   [`dotnet new`](../tools/dotnet-new.md) güncel bir oluşturur `Hello.csproj` bir konsol uygulaması oluşturmak gerekli bağımlılıkları olan proje dosyası.  Ayrıca oluşturur bir `Program.cs`, uygulamanın giriş noktasını içeren temel bir dosya.

   `Hello.csproj`:

   [!code[Hello.csproj](../../../samples/core/console-apps/HelloMsBuild/Hello.csproj)]

   Proje dosyası geri yükleme bağımlılıkları ve program oluşturmak için gerekli olan her şeyi belirtir.

   * `OutputType` Etiketini belirtir bir yürütülebilir dosya, başka bir deyişle bir konsol uygulaması oluşturuyorsunuz.
   * `TargetFramework` Hedefleyen hangi .NET uygulaması etiketini belirtir. Gelişmiş bir senaryoda, birden çok hedef çerçeve belirtin ve tüm yapı tek bir işlemde olanlar. Bu öğreticide, biz yalnızca .NET Core 2.1 için yapı için kullanacağız.

   `Program.cs`:

   [!code-csharp[Program.cs](../../../samples/core/console-apps/HelloMsBuild/Program.cs)]

   Tarafından program başlar `using System`, anlamına "her şey Getir `System` kapsama bu dosya için ad alanı". `System` Ad alanı içeren temel yapılarından gibi `string`, ya da sayısal türler.

   Ad alanı ardından tanımlarız `Hello`. Bu için istediğiniz değişikliği yapabilirsiniz. Adlı bir sınıf `Program` ile bu ad alanı içinde tanımlanan bir `Main` dizisini kendi bağımsız değişkeni olarak alan yöntemi. Bu dizi, derlenmiş programın çağrılırken geçirilen bağımsız değişken listesini içerir. Olduğu gibi bu dizinin kullanılmaz: "Hello World!" yazmak için tüm programı yaptığını olduğu konsola. Değişiklikleri olmanızı sağlayacak kodu daha sonra oluşturacağız bu değişkeni kullanın.

   [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

   `dotnet new` çağrıları [ `dotnet restore` ](../tools/dotnet-restore.md) örtük olarak. `dotnet restore` içine yapılan çağrılar [NuGet](https://www.nuget.org/) (bağımlılıkları ağacının geri yüklemek için Paket Yöneticisi .NET). NuGet çözümler *Hello.csproj* dosya, dosyasında tanımlanan bağımlılıkları indirir (veya bunları makinenizde önbellekten Dallarınızla) ve Yazar *obj/project.assets.json* için gerekli olan dosya derleme ve örneği çalıştırın.

   > [!IMPORTANT]
   > SDK'sının bir .NET Core 1.x sürümü kullanıyorsanız, çağırmanız gerekir `dotnet restore` arama sonra kendiniz `dotnet new`.

2. `dotnet run`

   [`dotnet run`](../tools/dotnet-run.md) çağrıları [ `dotnet build` ](../tools/dotnet-build.md) hedefleri oluşturulan derleme ve çağrıları emin olmak için `dotnet <assembly.dll>` hedef uygulamayı çalıştırın.

    ```console
    $ dotnet run
    Hello World!
    ```

    Alternatif olarak, aynı zamanda yürütebilirsiniz [ `dotnet build` ](../tools/dotnet-build.md) konsol uygulamaları derleme çalıştırmadan Kodu derlemek için. İle çalıştırılabilir bir DLL dosyası olarak derlenmiş bir uygulama sonuçlanır `dotnet bin\Debug\netcoreapp2.1\Hello.dll` Windows üzerinde (kullanın `/` Windows olmayan sistemler için). Bu konuda daha sonra göreceğiniz üzere uygulamaya bağımsız değişkenler de belirtebilirsiniz.

    ```console
    $ dotnet bin\Debug\netcoreapp2.1\Hello.dll
    Hello World!
    ```

    Gelişmiş bir senaryo dağıtılabilir ve .NET Core yüklü olmak zorunda olmayan bir makineye çalıştırma platforma özgü dosyaları kendi içinde bir dizi olarak uygulama oluşturmak mümkündür. Bkz: [.NET Core uygulaması dağıtımını](../deploying/index.md) Ayrıntılar için.

### <a name="augmenting-the-program"></a>Program deneyimlerinizi

Bir bit program değiştirelim. Eğlenceli Fibonacci sayılardır, kişi selam bağımsız değişkenin kullanım hakkına ek olarak uygulama çalıştıran şimdi ekleyin.

1. Öğesinin içeriğini değiştirin, *Program.cs* dosyasındaki kodu aşağıdaki kodla:

   [!code-csharp[Fibonacci](../../../samples/core/console-apps/fibonacci-msbuild/Program.cs)]

2. Yürütme [ `dotnet build` ](../tools/dotnet-build.md) değişiklikleri derlemek için.

3. Uygulamaya bir parametre geçirerek programı çalıştır:

   ```console
   $ dotnet run -- John
   Hello John!
   Fibonacci Numbers 1-15:
   1: 0
   2: 1
   3: 1
   4: 2
   5: 3
   6: 5
   7: 8
   8: 13
   9: 21
   10: 34
   11: 55
   12: 89
   13: 144
   14: 233
   15: 377
   ```

Ve İşte bu kadar!  Genişletmek `Program.cs` istediğiniz gibi.

## <a name="working-with-multiple-files"></a>Birden çok dosyaları ile çalışma

Tek dosyalar için basit bir kerelik programlar bir sakınca yoktur ancak daha karmaşık bir uygulama oluşturuyorsanız, büyük olasılıkla birden çok kaynak dosyaları projenize şimdi yükleneceği derleme önceki Fibonacci örnek alanlarını bazı Fibonacci değerleri önbelleğe alarak olduğunuz ve bazı özyinelemeli Ekle Özellikler.

1. İçinde yeni bir dosya ekleme *Hello* adlı dizin *FibonacciGenerator.cs* aşağıdaki kod ile:

   [!code-csharp[Fibonacci Generator](../../../samples/core/console-apps/FibonacciBetterMsBuild/FibonacciGenerator.cs)]

2. Değişiklik `Main` yönteminde, *Program.cs* dosya yeni bir sınıf örneği oluşturun ve aşağıdaki örnekte olduğu gibi yöntem çağırmak için:

   [!code-csharp[New Program.cs](../../../samples/core/console-apps/FibonacciBetterMsBuild/Program.cs)]

3. Yürütme [ `dotnet build` ](../tools/dotnet-build.md) değişiklikleri derlemek için.

4. Yürüterek uygulamanızı çalıştırma [ `dotnet run` ](../tools/dotnet-run.md). Program çıktısı aşağıda gösterilmiştir:

   ```console
   $ dotnet run
   0
   1
   1
   2
   3
   5
   8
   13
   21
   34
   55
   89
   144
   233
   377
   ```

Ve İşte bu kadar! Şimdi burada kendi programlar oluşturmak için temel kavramları öğrendiniz kullanmaya başlayabilirsiniz.

Komutlar ve uygulamanızı çalıştırmak için Bu öğreticide gösterilen adımlar yalnızca geliştirme zamanı sırasında kullanıldığını unutmayın. Uygulamanızı dağıtmak hazır olduğunuzda, farklı bir göz atın isteyeceksiniz [dağıtım stratejilerini](../deploying/index.md) .NET Core uygulamaları için ve [ `dotnet publish` ](../tools/dotnet-publish.md) komutu.

## <a name="see-also"></a>Ayrıca bkz.

- [Düzenleme ve .NET Core CLI araçları ile projeleri test etme](testing-with-cli.md)
