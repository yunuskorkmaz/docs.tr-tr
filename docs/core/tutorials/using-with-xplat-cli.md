---
title: CLı kullanarak .NET Core ile çalışmaya başlama
description: .NET Core komut satırı arabirimi (CLı) kullanarak Windows, Linux veya macOS 'ta .NET Core ile çalışmaya başlama hakkında adım adım öğretici.
author: thraka
ms.author: adegeo
ms.date: 08/07/2019
ms.technology: dotnet-cli
ms.custom: seodec18
ms.openlocfilehash: b5ef70967c8404dc5ce5b816bb9a1c3b1d7e4230
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117356"
---
# <a name="get-started-with-net-core-on-windowslinuxmacos-using-the-command-line"></a>Komut satırını kullanarak Windows/Linux/macOS 'ta .NET Core ile çalışmaya başlama

Bu konu, .NET Core CLI araçları kullanılarak makinenizde platformlar arası uygulamalar geliştirmeye nasıl başlayacaksınız.

.NET Core CLI araç takımını tanımıyorsanız, [.NET Core SDK genel bakış](../tools/index.md)makalesini okuyun.

## <a name="prerequisites"></a>Önkoşullar

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

   [`dotnet new`](../tools/dotnet-new.md)konsol uygulaması oluşturmak için gereken bağımlılıklara sahip `Hello.csproj` bir güncel proje dosyası oluşturur.  Ayrıca `Program.cs`, uygulamanın giriş noktasını içeren temel bir dosya oluşturur.

   `Hello.csproj`:

   [!code[Hello.csproj](../../../samples/core/console-apps/HelloMsBuild/Hello.csproj)]

   Proje dosyası, bağımlılıkları geri yüklemek ve programı derlemek için gereken her şeyi belirtir.

   - `OutputType` Etiket, bir konsol uygulaması başka bir deyişle bir yürütülebilir dosya oluşturduğumuz olduğunu belirtir.
   - `TargetFramework` Etiket hangi .NET uygulamasının hedefleyebileceklerini belirtir. Gelişmiş bir senaryoda, birden çok hedef çerçeve belirtebilir ve tek bir işlemde bunların tümüne derleme yapabilirsiniz. Bu öğreticide yalnızca .NET Core 2,1 için derleme yapacağız.

   `Program.cs`:

   [!code-csharp[Program.cs](../../../samples/core/console-apps/HelloMsBuild/Program.cs)]

   Program tarafından `using System`başlar, bu, " `System` ad alanındaki her şeyi bu dosya için kapsama getir" anlamına gelir. Ad alanı `string`, veya sayısal türler gibi temel yapıları içerir. `System`

   Daha sonra adlı `Hello`bir ad alanı tanımlayacağız. Bunu istediğiniz herhangi bir şekilde değiştirebilirsiniz. Adlı `Program` bir sınıf, bağımsız değişkeni olarak bir dize dizisi alan `Main` bir yöntemle, bu ad alanı içinde tanımlanır. Bu dizi, derlenmiş program çağrıldığında geçirilen bağımsız değişkenlerin listesini içerir. Çünkü bu dizi kullanılmaz: tüm programlar "Merhaba Dünya!" yazmak konsoluna gidin. Daha sonra, bu bağımsız değişken tarafından kullanılacak kodda değişiklik yapacağız.

   [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

   `dotnet new`örtülü [`dotnet restore`](../tools/dotnet-restore.md) olarak çağırır. `dotnet restore`Bağımlılıklar ağacını geri yüklemek için [NuGet](https://www.nuget.org/) (.net Package Manager) çağrısı yapın. NuGet, *Hello. csproj* dosyasını analiz eder, dosyada tanımlanan bağımlılıkları indirir (veya makinenizde bir önbellekten Dallarınızla) ve örneği derlemek ve çalıştırmak için gerekli olan *obj/Project. varlıklar. JSON* dosyasını yazar.

   > [!IMPORTANT]
   > SDK 'nın .NET Core 1. x sürümünü kullanıyorsanız, öğesini çağırdıktan `dotnet restore` `dotnet new`sonra çağırmanız gerekir.

2. `dotnet run`

   [`dotnet run`](../tools/dotnet-run.md)Derleme [`dotnet build`](../tools/dotnet-build.md) hedeflerinin oluşturulduğundan emin olmak için çağrılar yapın ve ardından hedef uygulamayı çalıştırmak için `dotnet <assembly.dll>` çağırır.

    ```console
    $ dotnet run
    Hello World!
    ```

    Alternatif olarak, derleme konsolu uygulamalarını [`dotnet build`](../tools/dotnet-build.md) çalıştırmadan kodu derlemek için de çalıştırabilirsiniz. Bu, derlenmiş bir uygulamanın Windows üzerinde ile `dotnet bin\Debug\netcoreapp2.1\Hello.dll` çalıştırılabilecek bir dll dosyası olarak sonuçlanır (Windows dışı sistemler için kullanın `/` ). Ayrıca, konusunda daha sonra göreceğiniz gibi uygulamanın bağımsız değişkenlerini de belirtebilirsiniz.

    ```console
    $ dotnet bin\Debug\netcoreapp2.1\Hello.dll
    Hello World!
    ```

    Gelişmiş bir senaryo olarak, uygulamayı, .NET Core yüklü olması gerekmeyen bir makineye dağıtılabilecek ve çalıştırılabilen, kendi kendine ait platforma özgü dosyalar kümesi olarak oluşturmak mümkündür. Ayrıntılar için bkz. [.NET Core uygulama dağıtımı](../deploying/index.md) .

### <a name="augmenting-the-program"></a>Program artırılması

Programı bir bit olarak değiştirelim. Fibonaccı numaraları eğlencelidir. bu nedenle, uygulamayı çalıştıran kişiyi gremek için bağımsız değişkenini kullanmaya ek olarak ekleyelim.

1. *Program.cs* dosyanızın içeriğini aşağıdaki kodla değiştirin:

   [!code-csharp[Fibonacci](../../../samples/core/console-apps/fibonacci-msbuild/Program.cs)]

2. Değişiklikleri [`dotnet build`](../tools/dotnet-build.md) derlemek için yürütün.

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

İşte bu kadar!  `Program.cs` Dilediğiniz şekilde dilediğiniz gibi kullanabilirsiniz.

## <a name="working-with-multiple-files"></a>Birden çok dosya ile çalışma

Tek dosyalar basit bir tek başına programlar için uygundur, ancak daha karmaşık bir uygulama oluşturuyorsanız, muhtemelen projenizde birden fazla kaynak dosyasına sahip olursunuz.
Önceki Fibonaccı örneğini, bazı Fipriaccı değerlerini önbelleğe alarak ve bazı özyinelemeli özellikler ekleyerek oluşturalım.

1. Aşağıdaki kodla *FibonacciGenerator.cs* adlı *Hello* dizininin içine yeni bir dosya ekleyin:

   [!code-csharp[Fibonacci Generator](../../../samples/core/console-apps/FibonacciBetterMsBuild/FibonacciGenerator.cs)]

2. Program.cs dosyanızdaki `Main` yöntemi, yeni sınıfı başlatmak ve metodunu aşağıdaki örnekte olduğu gibi çağırmak için değiştirin:

   [!code-csharp[New Program.cs](../../../samples/core/console-apps/FibonacciBetterMsBuild/Program.cs)]

3. Değişiklikleri [`dotnet build`](../tools/dotnet-build.md) derlemek için yürütün.

4. Uygulamasını yürüterek [`dotnet run`](../tools/dotnet-run.md)çalıştırın. Program çıktısı aşağıda gösterilmektedir:

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

Uygulamanızı dağıtmaya hazırsanız, [`dotnet publish`](../tools/dotnet-publish.md) `/` _\\hata ayıklama\\netcoreapp 2.1\\Publish\\_  konumundaki _Yayımla_ klasörünü oluşturmak için komutunu kullanın (için kullanın Windows dışı sistemler). Daha önce DotNet çalışma zamanını yükledikleri sürece _Publish_ klasörünün içeriğini diğer platformlara dağıtabilirsiniz.

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
