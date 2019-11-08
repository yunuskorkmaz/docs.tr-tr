---
title: CLı kullanarak .NET Core ile çalışmaya başlama
description: .NET Core komut satırı arabirimi (CLı) kullanarak Windows, Linux veya macOS 'ta .NET Core ile çalışmaya başlama hakkında adım adım öğretici.
author: thraka
ms.author: adegeo
ms.date: 08/07/2019
ms.technology: dotnet-cli
ms.custom: seodec18
ms.openlocfilehash: cf8c3ae070f4c77789dc55ba4d7888c7b15c8653
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736983"
---
# <a name="get-started-with-net-core-on-windowslinuxmacos-using-the-command-line"></a>Komut satırını kullanarak Windows/Linux/macOS 'ta .NET Core ile çalışmaya başlama

Bu konu, .NET Core CLI araçları kullanılarak makinenizde platformlar arası uygulamalar geliştirmeye nasıl başlayacaksınız.

.NET Core CLI araç takımını tanımıyorsanız, [.NET Core SDK genel bakış](../tools/index.md)makalesini okuyun.

## <a name="prerequisites"></a>Prerequisites

- [.NET Core SDK 2,1](https://dotnet.microsoft.com/download) veya sonraki sürümler.
- Seçtiğiniz bir metin düzenleyici veya kod Düzenleyicisi.

## <a name="hello-console-app"></a>Merhaba, konsol uygulaması!

Örnek kodu DotNet/Samples GitHub deposundan [görüntüleyebilir veya indirebilirsiniz](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild) . İndirme yönergeleri için bkz. [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

Bir komut istemi açın ve *Hello*adlı bir klasör oluşturun. Oluşturduğunuz klasöre gidin ve aşağıdakini yazın:

```dotnetcli
dotnet new console
dotnet run
```

Hızlı bir yol açalım:

1. `dotnet new console`

   [`dotnet new`](../tools/dotnet-new.md) , bir konsol uygulaması oluşturmak için gereken bağımlılıklara sahip bir güncel *Hello. csproj* proje dosyası oluşturur. Ayrıca, uygulamanın giriş noktasını içeren temel bir dosya olan bir *program.cs*oluşturur.

   *Merhaba. csproj*:

   [!code-xml[Hello.csproj](~/samples/core/console-apps/HelloMsBuild/Hello.csproj)]

   Proje dosyası, bağımlılıkları geri yüklemek ve programı derlemek için gereken her şeyi belirtir.

   - `OutputType` etiketi, bir konsol uygulaması diğer bir deyişle yürütülebilir bir dosya oluşturduğumuz olduğunu belirtir.
   - `TargetFramework` etiketi, hangi .NET uygulamasının hedefleyebileceklerini belirtir. Gelişmiş bir senaryoda, birden çok hedef çerçeve belirtebilir ve tek bir işlemde bunların tümüne derleme yapabilirsiniz. Bu öğreticide yalnızca .NET Core 2,1 için derleme yapacağız.

   *Program.cs*:

   [!code-csharp[Program.cs](~/samples/core/console-apps/HelloMsBuild/Program.cs)]

   Program `using System`başlar, bu, "`System` ad alanındaki her şeyi bu dosyanın kapsamına getir" anlamına gelir. `System` ad alanı `Console` sınıfını içerir.

   Daha sonra `Hello`adlı bir ad alanı tanımlayacağız. Bunu istediğiniz herhangi bir şekilde değiştirebilirsiniz. `Program` adlı bir sınıf, bu ad alanı içinde tanımlanır ve bağımsız değişkeni olarak bir dize dizisi alan `Main` bir yöntemdir. Bu dizi, derlenmiş program çağrıldığında geçirilen bağımsız değişkenlerin listesini içerir. Çünkü bu dizi kullanılmaz: tüm programlar "Merhaba Dünya!" yazmak konsoluna gidin. Daha sonra, bu bağımsız değişken tarafından kullanılacak kodda değişiklik yapacağız.

   [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

   `dotnet new` [`dotnet restore`](../tools/dotnet-restore.md) dolaylı olarak çağırır. Bağımlılıklar ağacını geri yüklemek için [NuGet](https://www.nuget.org/) 'e (.net Package Manager) çağrı `dotnet restore`. NuGet, *Hello. csproj* dosyasını analiz eder, dosyada tanımlanan bağımlılıkları indirir (veya makinenizde bir önbellekten Dallarınızla) ve örneği derlemek ve çalıştırmak için gerekli olan *obj/Project. varlıklar. JSON* dosyasını yazar.

   > [!IMPORTANT]
   > SDK 'nın .NET Core 1. x sürümünü kullanıyorsanız, `dotnet new`çağrıldıktan sonra `dotnet restore` kendiniz çağırmanız gerekir.

2. `dotnet run`

   [`dotnet run`](../tools/dotnet-run.md) , derleme hedeflerinin oluşturulduğundan emin olmak için [`dotnet build`](../tools/dotnet-build.md) çağırır ve sonra hedef uygulamayı çalıştırmak için `dotnet <assembly.dll>` çağırır.

    ```console
    $ dotnet run
    Hello World!
    ```

    Alternatif olarak, derleme konsolu uygulamalarını çalıştırmadan kodu derlemek için de [`dotnet build`](../tools/dotnet-build.md) çalıştırabilirsiniz. Bu, derlenmiş bir uygulamanın Windows üzerinde `dotnet bin\Debug\netcoreapp2.1\Hello.dll` çalıştırılabilen bir DLL dosyası olarak sonuçlanır (Windows dışı sistemler için `/` kullanın). Ayrıca, konusunda daha sonra göreceğiniz gibi uygulamanın bağımsız değişkenlerini de belirtebilirsiniz.

    ```console
    $ dotnet bin\Debug\netcoreapp2.1\Hello.dll
    Hello World!
    ```

    Gelişmiş bir senaryo olarak, uygulamayı, .NET Core yüklü olması gerekmeyen bir makineye dağıtılabilecek ve çalıştırılabilen, kendi kendine ait platforma özgü dosyalar kümesi olarak oluşturmak mümkündür. Ayrıntılar için bkz. [.NET Core uygulama dağıtımı](../deploying/index.md) .

### <a name="augmenting-the-program"></a>Program artırılması

Programı bir bit olarak değiştirelim. Fibonaccı numaraları eğlencelidir. bu nedenle, uygulamayı çalıştıran kişiyi gremek için bağımsız değişkenini kullanmaya ek olarak ekleyelim.

1. *Program.cs* dosyanızın içeriğini aşağıdaki kodla değiştirin:

   [!code-csharp[Fibonacci](../../../samples/core/console-apps/fibonacci-msbuild/Program.cs)]

2. Değişiklikleri derlemek için [`dotnet build`](../tools/dotnet-build.md) yürütün.

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

İşte bu kadar!  Dilediğiniz şekilde *program.cs* yapabilirsiniz.

## <a name="working-with-multiple-files"></a>Birden çok dosya ile çalışma

Tek dosyalar basit bir tek başına programlar için uygundur, ancak daha karmaşık bir uygulama oluşturuyorsanız, muhtemelen projenizde birden fazla kaynak dosyasına sahip olursunuz.
Önceki Fibonaccı örneğini, bazı Fipriaccı değerlerini önbelleğe alarak ve bazı özyinelemeli özellikler ekleyerek oluşturalım.

1. Aşağıdaki kodla *FibonacciGenerator.cs* adlı *Hello* dizininin içine yeni bir dosya ekleyin:

   [!code-csharp[Fibonacci Generator](~/samples/core/console-apps/FibonacciBetterMsBuild/FibonacciGenerator.cs)]

2. *Program.cs* dosyanızdaki `Main` yöntemini, yeni sınıfı başlatmak ve metodunu aşağıdaki örnekte olduğu gibi çağırmak için değiştirin:

   [!code-csharp[New Program.cs](~/samples/core/console-apps/FibonacciBetterMsBuild/Program.cs)]

3. Değişiklikleri derlemek için [`dotnet build`](../tools/dotnet-build.md) yürütün.

4. [`dotnet run`](../tools/dotnet-run.md)yürüterek uygulamanızı çalıştırın. Program çıktısı aşağıda gösterilmektedir:

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

## <a name="publish-your-app"></a>Uygulamanızı yayınlama

Uygulamanızı dağıtmaya hazırladıktan sonra, _\\hata ayıklama\\netcoreapp 2.1\\hata ayıkla_ (Windows dışı sistemler için\\kullanın) konumundaki _Yayımla_ klasörünü oluşturmak için [`dotnet publish`](../tools/dotnet-publish.md) komutunu kullanın. Daha önce DotNet çalışma zamanını yükledikleri sürece _Publish_ klasörünün içeriğini diğer platformlara dağıtabilirsiniz.

Yayımlanmış uygulamanızı [DotNet](../tools/dotnet.md) komutuyla çalıştırabilirsiniz:

```console
$ dotnet bin\Debug\netcoreapp2.1\publish\Hello.dll
Hello World!
```

## <a name="conclusion"></a>Sonuç

İşte bu kadar! Şimdi kendi programlarınızı oluşturmak için burada öğrenilen temel kavramları kullanmaya başlayabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Core CLI araçlarıyla projeleri düzenleme ve test etme](testing-with-cli.md)
- [CLı ile .NET Core uygulamaları yayımlayın](../deploying/deploy-with-cli.md)
- [Uygulama dağıtımı hakkında daha fazla bilgi edinin](../deploying/index.md)
