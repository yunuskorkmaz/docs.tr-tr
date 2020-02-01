---
title: CLı kullanarak .NET Core ile çalışmaya başlama
description: .NET Core CLI kullanarak Windows, Linux veya macOS 'ta .NET Core ile çalışmaya başlama hakkında adım adım öğretici.
author: thraka
ms.author: adegeo
ms.date: 12/05/2019
ms.technology: dotnet-cli
ms.custom: updateeachrelease
ms.openlocfilehash: 6e1c7881aa415ea54307d80214001a2f0fe5b4a6
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920474"
---
# <a name="get-started-with-net-core-using-the-net-core-cli"></a>.NET Core CLI kullanarak .NET Core ile çalışmaya başlama

Bu makalede, .NET Core CLI kullanarak Windows, Linux ve macOS üzerinde çalışan .NET Core uygulamaları geliştirmeye nasıl başlayacaksınız.

.NET Core CLI hakkında bilgi sahibi değilseniz, [.NET Core CLI genel bakış ' a](../tools/index.md)bakın.

## <a name="prerequisites"></a>Prerequisites

- [.NET Core SDK 3,1](https://dotnet.microsoft.com/download) veya sonraki sürümler.
- Seçtiğiniz bir metin düzenleyici veya kod Düzenleyicisi.

## <a name="hello-console-app"></a>Merhaba, konsol uygulaması!

Örnek kodu DotNet/Samples GitHub deposundan [görüntüleyebilir veya indirebilirsiniz](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild) . İndirme yönergeleri için bkz. [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

Bir komut istemi açın ve *Hello*adlı bir klasör oluşturun. Oluşturduğunuz klasöre gidin ve aşağıdakini yazın:

```dotnetcli
dotnet new console
dotnet run
```

Hızlı bir yol açalım:

01. `dotnet new console`

    [DotNet New](../tools/dotnet-new.md) , bir konsol uygulaması oluşturmak için gereken bağımlılıklara sahip bir güncel *Hello. csproj* proje dosyası oluşturur. Ayrıca, uygulamanın giriş noktasını içeren temel bir dosya olan bir *program.cs*oluşturur.
    
    *Merhaba. csproj*:
    
    [!code-xml[Hello.csproj](~/samples/core/console-apps/HelloMsBuild/Hello.csproj)]
    
    Proje dosyası, bağımlılıkları geri yüklemek ve programı derlemek için gereken her şeyi belirtir.
    
    - `<OutputType>` öğesi, bir konsol uygulaması diğer bir deyişle yürütülebilir bir dosya oluşturduğumuz olduğunu belirtir.
    - `<TargetFramework>` öğesi hangi .NET uygulamasını hedefliyoruz belirtir. Gelişmiş bir senaryoda, birden çok hedef çerçeve belirtebilir ve tek bir işlemde bunların tümüne derleme yapabilirsiniz. Bu öğreticide yalnızca .NET Core 3,1 için derleme yapacağız.
    
    *Program.cs*:
    
    [!code-csharp[Program.cs](~/samples/core/console-apps/HelloMsBuild/Program.cs)]
    
    Program `using System`başlar, bu, "`System` ad alanındaki her şeyi bu dosyanın kapsamına getir" anlamına gelir. `System` ad alanı `Console` sınıfını içerir.
    
    Daha sonra `Hello`adlı bir ad alanı tanımlayacağız. Bunu istediğiniz herhangi bir şekilde değiştirebilirsiniz. `Program` adlı bir sınıf, `args`adlı dizelerin dizisini alan `Main` yöntemi ile bu ad alanı içinde tanımlanır. Bu dizi, program çalıştırıldığında geçirilen bağımsız değişkenlerin listesini içerir. Çünkü bu dizi kullanılmaz ve program yalnızca "Merhaba Dünya!" metnini yazar konsoluna gidin. Daha sonra, bu bağımsız değişken tarafından kullanılacak kodda değişiklik yapacağız.
    
    `dotnet new` [DotNet restore](../tools/dotnet-restore.md) dolaylı olarak çağırır. Bağımlılıklar ağacını geri yüklemek için [NuGet](https://www.nuget.org/) 'e (.net Package Manager) çağrı `dotnet restore`. NuGet, *Hello. csproj* dosyasını analiz eder, dosyada tanımlanan bağımlılıkları indirir (veya makinenizde bir önbellekten Dallarınızla) ve örneği derlemek ve çalıştırmak için gerekli olan *obj/Project. varlıklar. JSON* dosyasını yazar.

02. `dotnet run`

    [DotNet Run](../tools/dotnet-run.md) , derleme hedeflerinin oluşturulduğundan emin olmak için [DotNet derlemesini](../tools/dotnet-build.md) çağırır ve sonra hedef uygulamayı çalıştırmak için `dotnet <assembly.dll>` çağırır.
    
    ```console
    dotnet run

    Hello World!
    ```
    
    Alternatif olarak, derleme konsolu uygulamalarını çalıştırmadan kodu derlemek için `dotnet build` de çalıştırabilirsiniz. Bu, bir DLL dosyası olarak proje adına bağlı olarak derlenmiş bir uygulama ile sonuçlanır. Bu durumda, oluşturulan dosya *Hello. dll*olarak adlandırılır. Bu uygulama, Windows üzerinde `dotnet bin\Debug\netcoreapp3.1\Hello.dll` çalıştırılabilir (Windows dışı sistemler için `/` kullanın).
    
    ```console
    dotnet bin\Debug\netcoreapp3.1\Hello.dll

    Hello World!
    ```
    
    Uygulama derlendiğinde, `Hello.dll`birlikte işletim sistemine özgü bir yürütülebilir dosya oluşturulur. Windows 'da bu `Hello.exe`olur; Linux veya macOS üzerinde bu `hello`. Yukarıdaki örnekte, dosya `Hello.exe` veya `Hello`ile adlandırılır. Bu yürütülebilir dosyayı doğrudan çalıştırabilirsiniz.

    ```console
    .\bin\Debug\netcoreapp3.1\Hello.exe

    Hello World!
    ```

## <a name="modify-the-program"></a>Programı değiştirme

Programı bir bit olarak değiştirelim. Fibonaccı numaraları eğlencelidir. bu nedenle, uygulamayı çalıştıran kişiyi almak için bağımsız değişkenini de kullanarak ekleyelim.

01. *Program.cs* dosyanızın içeriğini aşağıdaki kodla değiştirin:

    [!code-csharp[Fibonacci](~/samples/core/console-apps/fibonacci-msbuild/Program.cs)]

02. Değişiklikleri derlemek için [DotNet derlemesini](../tools/dotnet-build.md) çalıştırın.

03. Uygulamaya bir parametre geçirerek programı çalıştırın. Bir uygulamayı çalıştırmak için `dotnet` komutunu kullandığınızda sonuna `--` ekleyin. `--` sağına herhangi bir şey, uygulamaya parametre olarak geçirilir. Aşağıdaki örnekte `John` değeri uygulamaya geçirilir.

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

İşte bu kadar! Dilediğiniz gibi *program.cs* değiştirebilirsiniz.

## <a name="working-with-multiple-files"></a>Birden çok dosya ile çalışma

Tek dosyalar basit bir tek başına programlar için uygundur, ancak daha karmaşık bir uygulama oluşturuyorsanız, muhtemelen projenizde birden çok kod dosyasına sahip olursunuz. Önceki Fibonaccı örneğini, bazı Fipriaccı değerlerini önbelleğe alarak ve bazı özyinelemeli özellikler ekleyerek oluşturalım.

01. Aşağıdaki kodla *FibonacciGenerator.cs* adlı *Hello* dizininin içine yeni bir dosya ekleyin:

    [!code-csharp[Fibonacci Generator](~/samples/core/console-apps/FibonacciBetterMsBuild/FibonacciGenerator.cs)]

02. *Program.cs* dosyanızdaki `Main` yöntemini, yeni sınıfı başlatmak ve metodunu aşağıdaki örnekte olduğu gibi çağırmak için değiştirin:

    [!code-csharp[New Program.cs](~/samples/core/console-apps/FibonacciBetterMsBuild/Program.cs)]

03. Değişiklikleri derlemek için [DotNet derlemesini](../tools/dotnet-build.md) çalıştırın.

04. [DotNet çalıştırmasını](../tools/dotnet-run.md)yürüterek uygulamanızı çalıştırın. Program çıktısı aşağıda gösterilmektedir:

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

Uygulamanızı dağıtmaya hazırladıktan sonra, _\\,\\netcoreapp 3.1\\hata ayıkla_ (Windows dışı sistemler için\\kullanın) konumundaki _Yayımla_ klasörünü oluşturmak için [DotNet Publish](../tools/dotnet-publish.md) komutunu kullanın. Daha önce DotNet çalışma zamanını yükledikleri sürece _Publish_ klasörünün içeriğini diğer platformlara dağıtabilirsiniz.

```console
dotnet publish
Microsoft (R) Build Engine version 16.4.0+e901037fe for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 20 ms for C:\Code\Temp\Hello\Hello.csproj.
  Hello -> C:\Code\Temp\Hello\bin\Debug\netcoreapp3.1\Hello.dll
  Hello -> C:\Code\Temp\Hello\bin\Debug\netcoreapp3.1\publish\
```

Yukarıdaki çıkış, geçerli klasörünüze ve işletim sisteminize göre farklılık gösterebilir, ancak çıktının benzer olması gerekir.

Yayımlanmış uygulamanızı [DotNet](../tools/dotnet.md) komutuyla çalıştırabilirsiniz:

```console
dotnet bin\Debug\netcoreapp3.1\publish\Hello.dll

Hello World!
```

Bu makalenin başlangıcında belirtildiği gibi, `Hello.dll`birlikte işletim sistemine özgü bir yürütülebilir dosya oluşturulmuştur. Windows 'da bu `Hello.exe`olur; Linux veya macOS üzerinde bu `hello`. Yukarıdaki örnekte, dosya `Hello.exe` veya `Hello`ile adlandırılır. Bu yayınlanan yürütülebilir dosyayı doğrudan çalıştırabilirsiniz.

```console
.\bin\Debug\netcoreapp3.1\publish\Hello.exe

Hello World!
```

## <a name="conclusion"></a>Sonuç

İşte bu kadar! Şimdi kendi programlarınızı oluşturmak için burada öğrenilen temel kavramları kullanmaya başlayabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Core CLI projeleri düzenleme ve test etme](testing-with-cli.md)
- [.NET Core CLI .NET Core uygulamaları yayımlayın](../deploying/deploy-with-cli.md)
- [.NET core uygulama dağıtımı](../deploying/index.md)
