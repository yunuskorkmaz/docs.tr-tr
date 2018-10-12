---
title: .NET Core ile çalışmaya başlama
description: Windows, Linux ve Macos'ta .NET Core uygulamaları oluşturma hakkında bilgi edinmek için kaynakları bulun.
author: thraka
ms.author: adegeo
ms.date: 06/27/2018
ms.openlocfilehash: 3fff7884082c46477d37b08560a2c71e7ee345e5
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49121260"
---
# <a name="get-started-with-net-core"></a>.NET Core ile çalışmaya başlama

Bu makalede .NET Core kullanmaya başlama hakkında bilgi sağlar. Windows, Linux ve Macos'ta .NET core yüklenebilir. Sık kullandığınız metin düzenleyicinizde kod ve platformlar arası kitaplıklar ve uygulamalar oluşturur. 

.NET Core nedir ve .NET teknolojilerden nasıl ilişkili olduğu emin değilseniz başlayın [.NET nedir](https://www.microsoft.com/net/learn/dotnet/what-is-dotnet) genel bakış. Kısacası, .NET Core açık kaynaklı, platformlar arası .NET uygulamasıdır.

## <a name="create-an-application"></a>Uygulama oluşturma

İlk olarak, indirme ve yükleme [.NET Core SDK'sı](https://www.microsoft.com/net/download/) bilgisayarınızda.

Ardından, aşağıdaki gibi bir terminal açın **PowerShell**, **komut istemi**, veya **bash**. Aşağıdaki komutu yazın `dotnet` oluşturma ve C# uygulama çalıştırma için komutları.

```console
dotnet new console --output sample1
dotnet run --project sample1
```

Aşağıdaki çıktıyı görmeniz gerekir:

```console
Hello World!
```

Tebrikler! Basit bir .NET Core uygulaması oluşturdunuz. Ayrıca [Visual Studio Code](tutorials/with-visual-studio-code.md), [Visual Studio 2017](tutorials/with-visual-studio.md) (yalnızca Windows) veya [Mac için Visual Studio](tutorials/using-on-mac-vs.md) (.NET Core uygulaması oluşturmak için macOS yalnızca).

## <a name="tutorials"></a>Öğreticiler

Bu adım adım öğreticileri izleyerek .NET Core uygulamaları geliştirmeye başlayabilirsiniz.

# <a name="windowstabwindows"></a>[Windows](#tab/windows)

* [Visual Studio 2017'de .NET Core ile C# "Hello World" uygulaması oluşturun.](./tutorials/with-visual-studio.md)

* [Bir Visual Studio 2017'de .NET Core ile C# sınıf kitaplığı oluşturun.](./tutorials/library-with-visual-studio.md)

* [Visual Studio 2017'de .NET Core ile bir Visual Basic "Hello World" uygulaması oluşturun.](./tutorials/vb-with-visual-studio.md)

* [Visual Basic ve Visual Studio 2017'de .NET Core ile bir sınıf kitaplığı oluşturun.](./tutorials/vb-library-with-visual-studio.md)  

* Üzerinde bir video izleyin [yüklemek ve Visual Studio Code ve .NET Core kullanmak nasıl](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/).

* Üzerinde bir video izleyin [yüklemek ve Visual Studio 2017 ve .NET Core kullanmak nasıl](https://channel9.msdn.com/Blogs/dotnet/Get-Started-NET-Core-Visual-Studio-2017/).

* [Komut satırını kullanarak .NET Core ile çalışmaya başlama.](tutorials/using-with-xplat-cli.md)

Bkz: [Önkoşullar için Windows geliştirme](windows-prerequisites.md) desteklenen Windows sürümlerinin bir listesi için makale.

# <a name="linuxtablinux"></a>[Linux](#tab/linux)

Bu adım adım öğreticileri izleyerek .NET Core uygulaması geliştirmeye başlayabilirsiniz.

* [Komut satırını kullanarak .NET Core ile çalışmaya başlama.](tutorials/using-with-xplat-cli.md)

* Üzerinde bir video izleyin [Ubuntu üzerinde C# ve .NET Core kullanarak Visual Studio Code kullanmaya başlama](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).

Bkz: [Linux geliştirme için Önkoşullar](linux-prerequisites.md) makale listesi için desteklenen Linux dağıtımları ve sürümleri.

# <a name="macostabmacos"></a>[macOS](#tab/macos)

Bu adım adım öğreticileri izleyerek .NET Core uygulaması geliştirmeye başlayabilirsiniz.

* Üzerinde bir video izleyin [macOS üzerinde C# ve .NET Core kullanarak Visual Studio Code kullanmaya başlama](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac).

* [Visual Studio Code kullanarak macOS üzerinde .NET Core ile çalışmaya başlama.](tutorials/using-on-macos.md)

* [Komut satırını kullanarak .NET Core ile çalışmaya başlama.](tutorials/using-with-xplat-cli.md)

* [Mac için Visual Studio kullanarak macos'ta .NET Core ile çalışmaya başlama](tutorials/using-on-mac-vs.md)

* [Mac için Visual Studio kullanarak macos'ta eksiksiz bir .NET Core çözümü derleme](tutorials/using-on-mac-vs-full-solution.md)

Bkz: [macOS geliştirme önkoşulları](macos-prerequisites.md) makale listesi için desteklenen işletim sistemi x / macOS sürümleri.

***
