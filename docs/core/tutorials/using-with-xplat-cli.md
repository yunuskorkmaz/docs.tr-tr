---
title: CLI kullanarak .NET Core'u kullanmaya başlama
description: Windows, Linux veya .NET Core komut satırı arabirimi (CLI) kullanarak macOS .NET Core kullanmaya başlamak nasıl gösteren adım adım öğretici.
author: cartermp
ms.author: mairaw
ms.date: 03/08/2017
ms.topic: get-started-article
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: 23aec1b951c4b65d62bd4da4b4c94043b1411cf3
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="getting-started-with-net-core-on-windowslinuxmacos-using-the-command-line"></a>Windows/Linux/macOS komut satırını kullanarak .NET Çekirdeğinde ile çalışmaya başlama

Bu konu .NET Core CLI araçlarını kullanarak makinenizdeki platformlar arası uygulamaları geliştirmeye başlamak nasıl yapacağınızı gösterir.

.NET Core CLI araç takımı değilseniz, okuma [.NET Core SDK Genel Bakış](../tools/index.md).

## <a name="prerequisites"></a>Önkoşullar

- [.NET core SDK 1.0](https://www.microsoft.com/net/download/core).
- Bir metin düzenleyicisi veya kod düzenleyiciyi.

## <a name="hello-console-app"></a>Merhaba, konsol uygulaması!

Yapabilecekleriniz [görüntülemek veya karşıdan örnek kod](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild) dotnet/samples Github'da depodan. Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

Bir komut istemi açın ve adlı bir klasör oluşturun *Hello*. Oluşturduğunuz klasöre gidin ve aşağıdaki komutu yazın:

```
$ dotnet new console
$ dotnet restore
$ dotnet run
```

Şimdi hızlı bir kılavuz yapın:

1. `$ dotnet new console`

   [`dotnet new`](../tools/dotnet-new.md) güncel bir oluşturur `Hello.csproj` bir konsol uygulaması oluşturmak için gereken bağımlılıkları olan proje dosyası.  Ayrıca oluşturur bir `Program.cs`, uygulama için giriş noktası içeren temel bir dosya.
   
   `Hello.csproj`:

   [!code[Hello.csproj](../../../samples/core/console-apps/HelloMsBuild/Hello.csproj)]   

   Proje dosyası bağımlılıkları geri yükleyin ve programı oluşturmak için gerekli olan her şeyi belirtir.

   * `OutputType` Etiketi bir yürütülebilir dosya, diğer bir deyişle bir konsol uygulaması oluşturduğunuz belirtir.
   * `TargetFramework` Etiketi hedefleme hangi .NET uygulaması belirtir. Gelişmiş bir senaryo da birden çok hedef çerçeveyi belirtin ve tüm yapı tek bir işlem de. Bu öğreticide, biz yalnızca .NET çekirdeği 1.0 için yapı takılıyor.

   `Program.cs`:

   [!code-csharp[Program.cs](../../../samples/core/console-apps/HelloMsBuild/Program.cs)]   

   Tarafından programı başlatan `using System`, anlamına gelen "her şeyi Getir `System` bu dosya için kapsam içine ad". `System` Ad alanı içeren temel yapıları gibi `string`, veya sayısal türler.

   Ardından adlı bir ad alanı tanımlarız `Hello`. Bu, istediğiniz bir şey değiştirebilirsiniz. Adlı bir sınıf `Program` ad alanında, ile tanımlanmış bir `Main` yönteminin dizisini kendi bağımsız değişken olarak alan. Bu dizi derlenmiş program çağrıldığında geçirilen bağımsız değişkenlerin listesini içerir. Olduğu gibi bu diziye kullanılmaz: program yapılması şey "Hello World!" yazmak için konsola. Daha sonra değişiklikler yapacak kodu vermiyoruz bu değişkeni kullanın.

   [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

2. `$ dotnet restore`

   [`dotnet restore`](../tools/dotnet-restore.md) içine çağırır [NuGet](https://www.nuget.org/) (bağımlılıkları ağacının geri yüklemek için Paket Yöneticisi .NET). NuGet çözümler *Hello.csproj* dosya, dosyasında belirtilen bağımlılıkları indirir (veya bunları makinenizde önbellekten alan) ve Yazar *obj/project.assets.json* dosya.  *Project.assets.json* derlemek ve çalıştırmak dosya gereklidir.
   
   *Project.assets.json* NuGet bağımlılıklar ve bir uygulamayı açıklayan diğer bilgi grafiği kalıcı ve eksiksiz bir kümesini bir dosyadır.  Bu dosyayı gibi diğer araçları tarafından okuma [ `dotnet build` ](../tools/dotnet-build.md) ve [ `dotnet run` ](../tools/dotnet-run.md), bunları işleme NuGet bağımlılıkları doğru kümesiyle kaynak kodu etkinleştirme ve bağlama çözümler.
   
3. `$ dotnet run`

   [`dotnet run`](../tools/dotnet-run.md) çağrıları [ `dotnet build` ](../tools/dotnet-build.md) hedefleri yerleşik yapı ve çağrıları emin olmak için `dotnet <assembly.dll>` hedef uygulamayı çalıştırın.
   
    ```
    $ dotnet run
    Hello World!
    ```

    Alternatif olarak, aynı zamanda yürütebilirsiniz [ `dotnet build` ](../tools/dotnet-build.md) konsol uygulamaları derleme çalıştırmadan Kodu derlemek için. Bu ile çalıştırılabilir bir DLL dosyası olarak derlenmiş bir uygulamada sonuçları `dotnet bin\Debug\netcoreapp1.0\Hello.dll` Windows (kullanmak `/` Windows olmayan sistemler için). Daha sonra konusunda anlatıldığı gibi uygulamaya bağımsız değişkenler de belirtebilir.

    ```
    $ dotnet bin\Debug\netcoreapp1.0\Hello.dll
    Hello World!
    ```

    Gelişmiş bir senaryo dağıtılan ve mutlaka .NET Core yüklü olmayan bir makineye çalıştırmak platforma özel dosyaları müstakil kümesi olarak uygulama oluşturmak mümkündür. Bkz: [.NET Core uygulama dağıtımı](../deploying/index.md) Ayrıntılar için.

### <a name="augmenting-the-program"></a>Program program.cs'ye

Bir bit program değiştirelim. Fun Fibonacci numaralarıdır, kişinin selam için bağımsız değişken kullanım yanı sıra uygulama çalışırken sağlandığından ekleyin.

1. Değiştir, *Program.cs* aşağıdaki kod ile dosya:

   [!code-csharp[Fibonacci](../../../samples/core/console-apps/fibonacci-msbuild/Program.cs)]   

2. Yürütme [ `dotnet build` ](../tools/dotnet-build.md) değişiklikleri derlemek için.

3. Uygulama için bir parametre geçirme programı çalıştır:

   ```
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

Ve bu kadar!  Büyütmek `Program.cs` istediğiniz gibi.

## <a name="working-with-multiple-files"></a>Birden çok dosyalarıyla çalışma

Tek dosyalar için basit bir kerelik programlar ince, ancak daha karmaşık bir uygulama oluşturuyorsanız, büyük olasılıkla birden fazla kaynak dosya projenizi şimdi yükleneceği yapı önceki Fibonacci örnek dışına bazı Fibonacci değerler önbelleğe alarak olduğunuz ve bazı özyinelemeli ekleyin Özellikler. 

1. İçinde yeni bir dosya ekleyin *Hello* adlı dizin *FibonacciGenerator.cs* aşağıdaki kod ile:

   [!code-csharp[Fibonacci Generator](../../../samples/core/console-apps/FibonacciBetterMsBuild/FibonacciGenerator.cs)]   

2. Değişiklik `Main` yönteminde, *Program.cs* dosyasını yeni sınıfının örneği ve aşağıdaki örnekteki gibi yöntemini çağırın:

   [!code-csharp[New Program.cs](../../../samples/core/console-apps/FibonacciBetterMsBuild/Program.cs)]

3. Yürütme [ `dotnet build` ](../tools/dotnet-build.md) değişiklikleri derlemek için.

4. Yürüterek uygulamanızı çalıştırma [ `dotnet run` ](../tools/dotnet-run.md). Aşağıdaki program çıkış şunları gösterir:

   ```
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

Ve bu kadar! Şimdi, temel kavramları kendi programlar oluşturmak için buraya öğrenilen kullanmaya başlayabilirsiniz.

Komutlar ve uygulamanızı çalıştırmak için Bu öğreticide gösterilen adımlar yalnızca geliştirme zamanı sırasında kullanılan unutmayın. Uygulamanızı dağıtmak hazır olduğunuzda, farklı bir göz atalım istersiniz [dağıtım stratejilerini](../deploying/index.md) .NET Core uygulamaları için ve [ `dotnet publish` ](../tools/dotnet-publish.md) komutu.

## <a name="see-also"></a>Ayrıca bkz.

[Düzenleme ve projeleri .NET Core CLI araçları ile test etme](testing-with-cli.md)
