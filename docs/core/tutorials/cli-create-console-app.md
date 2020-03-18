---
title: CLI kullanarak .NET Core kullanmaya başlama
description: .NET Core CLI'yi kullanarak Windows, Linux veya macOS'ta .NET Core ile nasıl başlaşmak gerektiğini gösteren adım adım bir öğretici.
author: thraka
ms.author: adegeo
ms.date: 12/05/2019
ms.technology: dotnet-cli
ms.custom: updateeachrelease
ms.openlocfilehash: fe69521a6ac88055e3e8c8502a7e19a72667dbef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240863"
---
# <a name="get-started-with-net-core-using-the-net-core-cli"></a>.NET Core CLI'yi kullanarak .NET Core ile başlayın

Bu makalede, .NET Core CLI'yi kullanarak Windows, Linux ve macOS'ta çalışan .NET Core uygulamalarını geliştirmeye nasıl başlayacağınızı gösterecektir.

.NET Core CLI'ye aşina [değilseniz,.NET Core CLI genel](../tools/index.md)bakış'ına bakın.

## <a name="prerequisites"></a>Önkoşullar

- [.NET Core SDK 3.1](https://dotnet.microsoft.com/download) veya sonraki sürümler.
- Tercih ettiğiniz bir metin veya kod düzenleyicisi.

## <a name="hello-console-app"></a>Merhaba, Konsol Uygulaması!

Örnek kodu dotnet/samples GitHub deposundan [görüntüleyebilir veya indirebilirsiniz.](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild) İndirme talimatları için [Örnekler ve Öğreticiler'e](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)bakın.

Komut istemini açın ve *Merhaba*adlı bir klasör oluşturun. Oluşturduğunuz klasöre gidin ve aşağıdakileri yazın.

```dotnetcli
dotnet new console
dotnet run
```

Hızlı bir gözden geçirme yapalım:

01. `dotnet new console`

    [dotnet yeni](../tools/dotnet-new.md) bir konsol uygulaması oluşturmak için gerekli bağımlılıkları ile güncel bir *Hello.csproj* proje dosyası oluşturur. Ayrıca, uygulama için giriş noktasını içeren temel bir dosya olan *Program.cs*oluşturur.

    *Merhaba.csproj*:

    [!code-xml[Hello.csproj](~/samples/snippets/core/tutorials/cli-create-console-app/HelloMsBuild/csharp/Hello.csproj)]

    Proje dosyası, bağımlılıkları geri yüklemek ve programı oluşturmak için gereken her şeyi belirtir.

    - Öğe, `<OutputType>` bir yürütülebilir, başka bir deyişle bir konsol uygulaması oluşturuyoruz belirtir.
    - Öğe, `<TargetFramework>` hedeflediğimiz .NET uygulamasını belirtir. Gelişmiş bir senaryoda, birden çok hedef çerçevesi belirtebilir ve tek bir işlemdeki herkese oluşturun. Bu eğitimde, sadece .NET Core 3.1 için oluşturmaya devam edeceğiz.

    *Program.cs*:

    [!code-csharp[Program.cs](~/samples/snippets/core/tutorials/cli-create-console-app/HelloMsBuild/csharp/Program.cs)]

    Program `using System`, `System` "bu dosya için kapsamına ad alanında her şeyi getirmek" anlamına gelir başlar. Ad `System` alanı `Console` sınıfı içerir.

    Daha sonra bir ad `Hello`alanı olarak tanımlanır. Bunu istediğin şeyle değiştirebilirsin. Adlı `Program` bir sınıf, adlı `Main` `args`dizeleri bir dizi alan bir yöntem ile, bu ad alanı içinde tanımlanır. Bu dizi, program çalıştırıldığında geçirilen bağımsız değişkenlerin listesini içerir. Olduğu gibi, bu dizi kullanılmaz ve program sadece metin "Merhaba Dünya yazıyor!" metnini görüntülemelidir. Daha sonra, bu bağımsız değişkenden yararlanacak kodda değişiklikler yapacağız.

    `dotnet new`[dotnet geri yükleme](../tools/dotnet-restore.md) çağırır örtülü olarak. `dotnet restore`bağımlılıklar ağacını geri yüklemek için [NuGet'e](https://www.nuget.org/) (.NET paket yöneticisi) çağrır. NuGet *Hello.csproj* dosyasını analiz eder, dosyada tanımlanan bağımlılıkları karşıdan yükler (veya makinenizdeki bir önbellekten yakalar) ve örneği derlemek ve çalıştırmak için gerekli olan *obj/project.assets.json* dosyasını yazar.

02. `dotnet run`

    [dotnet,](../tools/dotnet-run.md) yapı hedeflerinin inşa edildiğinden emin olmak için [dotnet yapılı](../tools/dotnet-build.md) çağrıları çalıştırır ve ardından hedef uygulamayı çalıştırmak için çağrılar da yapar. `dotnet <assembly.dll>`

    ```dotnetcli
    dotnet run
    ```

    Aşağıdaki çıktıyı alırsınız.

    ```console
    Hello World!
    ```

    Alternatif olarak, yapı `dotnet build` konsolu uygulamalarını çalıştırmadan kodu derlemek için de çalıştırabilirsiniz. Bu, projenin adını temel alan bir DLL dosyası olarak derlenmiş bir uygulamayla sonuçlanır. Bu durumda, oluşturulan dosya *Hello.dll*olarak adlandırılır. Bu uygulama `dotnet bin\Debug\netcoreapp3.1\Hello.dll` Windows'da çalıştırılabilir `/` (Windows olmayan sistemler için kullanın).

    ```dotnetcli
    dotnet bin\Debug\netcoreapp3.1\Hello.dll
    ```

    Aşağıdaki çıktıyı alırsınız.

    ```console
    Hello World!
    ```

    Uygulama derlendiğinde, işletim sistemine özgü bir çalıştırılabilir `Hello.dll` Windows'da, bu `Hello.exe`olurdu; Linux veya macOS, bu `hello`olurdu . Yukarıdaki örnekte, dosya ile `Hello.exe` adlandırılır `Hello`veya . Bu çalıştırılabilir doğrudan çalıştırabilirsiniz.

    ```console
    .\bin\Debug\netcoreapp3.1\Hello.exe

    Hello World!
    ```

## <a name="modify-the-program"></a>Programı değiştirme

Programı biraz değiştirelim. Fibonacci numaraları eğlenceli, bu yüzden bunu ekleyelim ve ayrıca uygulamayı çalıştıran kişiyi karşılamak için argümanı kullanalım.

01. *Program.cs* dosyanızın içeriğini aşağıdaki kodla değiştirin:

    [!code-csharp[Fibonacci](~/samples/snippets/core/tutorials/cli-create-console-app/fibonacci-msbuild/csharp/Program.cs)]

02. Değişiklikleri derlemek için [dotnet yapısını](../tools/dotnet-build.md) çalıştırın.

03. Uygulamaya bir parametre geçen programı çalıştırın. Bir uygulamayı `dotnet` çalıştırmak için komutu `--` kullandığınızda, sonuna ekleyin. Sağdaki her `--` şey uygulamaya parametre olarak geçirilecektir. Aşağıdaki örnekte, değer `John` uygulamaya aktarılır.

    ```dotnetcli
    dotnet run -- John
    ```

    Aşağıdaki çıktıyı alırsınız.

    ```console
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

Hepsi bu! *İstediğiniz Program.cs* değiştirebilirsiniz.

## <a name="working-with-multiple-files"></a>Birden çok dosyayla çalışma

Tek dosyalar basit tek seferlik programlar için iyidir, ancak daha karmaşık bir uygulama oluşturuyorsanız, büyük olasılıkla projenizde birden çok kod dosyanız olacaktır. Bazı Fibonacci değerlerini önbelleğe alarak önceki Fibonacci örneğini oluşturalım ve bazı özyinelemeli özellikler ekleyelim.

01. Aşağıdaki kodla *FibonacciGenerator.cs* adlı *Merhaba* dizininin içine yeni bir dosya ekleyin:

    [!code-csharp[Fibonacci Generator](~/samples/snippets/core/tutorials/cli-create-console-app/FibonacciBetterMsBuild/csharp/FibonacciGenerator.cs)]

02. Yeni `Main` sınıfı anında açmak ve yöntemiaşağıdaki örnekte olduğu gibi çağırmak için *Program.cs* dosyanızdaki yöntemi değiştirin:

    [!code-csharp[New Program.cs](~/samples/snippets/core/tutorials/cli-create-console-app/FibonacciBetterMsBuild/csharp/Program.cs)]

03. Değişiklikleri derlemek için [dotnet yapısını](../tools/dotnet-build.md) çalıştırın.

04. [dotnet çalıştırarak](../tools/dotnet-run.md)uygulamanızı çalıştırın.

    ```dotnetcli
    dotnet run
    ```

    Aşağıdaki çıktıyı alırsınız.

    ```console
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

## <a name="publish-your-app"></a>Uygulamanızı yayımlama

Uygulamanızı dağıtmaya hazır olduğunuzda, _bin\\debug\\netcoreapp3.1\\publish\\ _ 'de _yayımlama_ klasörünü oluşturmak için [dotnet yayımlama](../tools/dotnet-publish.md) komutunu kullanın (Windows dışı sistemler için kullanın). `/` Dotnet çalışma süresini yükledikleri sürece _yayımlama_ klasörünün içeriğini diğer platformlara dağıtabilirsiniz.

```dotnetcli
dotnet publish
```

Aşağıdakine benzer çıktı alırsınız.

```console
Microsoft (R) Build Engine version 16.4.0+e901037fe for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 20 ms for C:\Code\Temp\Hello\Hello.csproj.
  Hello -> C:\Code\Temp\Hello\bin\Debug\netcoreapp3.1\Hello.dll
  Hello -> C:\Code\Temp\Hello\bin\Debug\netcoreapp3.1\publish\
```

Yukarıdaki çıktı geçerli klasörünüze ve işletim sisteminize bağlı olarak farklılık gösterebilir, ancak çıktı benzer olmalıdır.

Yayınlanan uygulamanızı [dotnet](../tools/dotnet.md) komutu ile çalıştırabilirsiniz:

```dotnetcli
dotnet bin\Debug\netcoreapp3.1\publish\Hello.dll
```

Aşağıdaki çıktıyı alırsınız.

```console
Hello World!
```

Bu makalenin başında belirtildiği gibi, bir işletim sistemi özel çalıştırılabilir `Hello.dll`ile birlikte oluşturuldu . Windows'da, bu `Hello.exe`olurdu; Linux veya macOS, bu `hello`olurdu . Yukarıdaki örnekte, dosya ile `Hello.exe` adlandırılır `Hello`veya . Bu yayımlanabilir çalıştırılabilir çalıştırAbilirsiniz.

```console
.\bin\Debug\netcoreapp3.1\publish\Hello.exe

Hello World!
```

## <a name="conclusion"></a>Sonuç

Hepsi bu! Şimdi, kendi programlarınızı oluşturmak için burada öğrenilen temel kavramları kullanmaya başlayabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Core CLI ile projelerin düzenlenmesi ve test edilmesi](testing-with-cli.md)
- [.NET Core CLI ile .NET Core uygulamalarını yayımla](../deploying/deploy-with-cli.md)
- [.NET Core uygulama dağıtımı](../deploying/index.md)
