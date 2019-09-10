---
title: .NET Core ile çalışmaya başlama
description: Windows, Linux ve macOS 'ta .NET Core uygulamaları oluşturmayı öğrenmek için kaynakları bulun.
author: thraka
ms.author: adegeo
ms.date: 06/27/2018
ms.openlocfilehash: 5c45364cfe725d47cbb6108cd9d6ec9f981cef25
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70849127"
---
# <a name="get-started-with-net-core"></a>.NET Core ile çalışmaya başlama

Bu makalede, .NET Core ile çalışmaya başlama hakkında bilgi sağlanır. .NET Core, Windows, Linux ve macOS 'a yüklenebilir. En sevdiğiniz metin düzenleyicinizde kod oluşturabilir ve platformlar arası kitaplıklar ve uygulamalar oluşturabilirsiniz. 

.NET Core 'un ne olduğunu veya diğer .NET teknolojileriyle nasıl ilişkili olduğunu bilmiyorsanız, [.net](https://dotnet.microsoft.com/learn/dotnet/what-is-dotnet) genel bakış ile başlayın. .NET Core, .NET ' in açık kaynaklı ve platformlar arası bir uygulamasıdır.

## <a name="create-an-application"></a>Uygulama oluşturma

İlk olarak, [.NET Core SDK](https://dotnet.microsoft.com/download) bilgisayarınıza indirip yükleyin.

Ardından, **PowerShell**, **komut istemi**veya **Bash**gibi bir Terminal açın. Bir C# uygulama oluşturmak `dotnet` ve çalıştırmak için aşağıdaki komutları yazın.

```console
dotnet new console --output sample1
dotnet run --project sample1
```

Aşağıdaki çıktıyı görmeniz gerekir:

```console
Hello World!
```

Tebrikler! Basit bir .NET Core uygulaması oluşturdunuz. .NET Core uygulaması oluşturmak için [Visual Studio Code](tutorials/with-visual-studio-code.md), [Visual Studio](tutorials/with-visual-studio.md) (yalnızca Windows) veya [Mac için Visual Studio](tutorials/using-on-mac-vs.md) (yalnızca MacOS) de kullanabilirsiniz.

## <a name="tutorials"></a>Öğreticiler

Bu adım adım öğreticilerini izleyerek .NET Core uygulamaları geliştirmeye başlamanızı sağlayabilirsiniz.

# <a name="windowstabwindows"></a>[Windows](#tab/windows)

* [Visual Studio C# 2017 ' de .NET Core ile bir "Merhaba Dünya" uygulaması oluşturun.](./tutorials/with-visual-studio.md)

* [Visual Studio C# 2017 ' de .NET Core ile bir sınıf kitaplığı oluşturun.](./tutorials/library-with-visual-studio.md)

* [Visual Studio 2017 ' de .NET Core ile bir Visual Basic "Merhaba Dünya" uygulaması oluşturun.](./tutorials/vb-with-visual-studio.md)

* [Visual Studio 2017 ' de Visual Basic ve .NET Core ile bir sınıf kitaplığı oluşturun.](./tutorials/vb-library-with-visual-studio.md)  

* [Visual Studio Code ve .NET Core 'u yüklemek ve kullanmak için](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/)bir video izleyin.

* [Visual Studio 2017 ve .NET Core 'u yüklemek ve kullanmak için](https://channel9.msdn.com/Blogs/dotnet/Get-Started-NET-Core-Visual-Studio-2017/)bir video izleyin.

* [Komut satırını kullanarak .NET Core ile çalışmaya başlama.](tutorials/using-with-xplat-cli.md)

Desteklenen Windows sürümlerinin listesi için bkz. [Windows geliştirme Için Önkoşullar](windows-prerequisites.md) makalesi.

# <a name="linuxtablinux"></a>[Linux](#tab/linux)

Bu adım adım öğreticilerini izleyerek .NET Core uygulaması geliştirmeye başlamanızı sağlayabilirsiniz.

* [Komut satırını kullanarak .NET Core ile çalışmaya başlama.](tutorials/using-with-xplat-cli.md)

* [Ubuntu 'da ve .NET Core 'u kullanarak C# Visual Studio Code](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu)kullanmaya başlama hakkında bir video izleyin.

Desteklenen Linux destekleri ve sürümlerinin listesi için [Linux geliştirme Için Önkoşullar](linux-prerequisites.md) makalesine bakın.

# <a name="macostabmacos"></a>[macOS](#tab/macos)

Bu adım adım öğreticilerini izleyerek .NET Core uygulaması geliştirmeye başlamanızı sağlayabilirsiniz.

* [MacOS 'ta .NET Core 'u kullanarak C# Visual Studio Code](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac)kullanmaya başlama hakkında bir video izleyin.

* [Visual Studio Code kullanarak macOS 'ta .NET Core ile çalışmaya başlama.](tutorials/using-on-macos.md)

* [Komut satırını kullanarak .NET Core ile çalışmaya başlama.](tutorials/using-with-xplat-cli.md)

* [Mac için Visual Studio kullanarak macOS 'ta .NET Core ile çalışmaya başlama.](tutorials/using-on-mac-vs.md)

* [Mac için Visual Studio kullanarak macOS 'ta kapsamlı bir .NET Core çözümü oluşturun.](tutorials/using-on-mac-vs-full-solution.md)

Desteklenen OS X/macOS sürümlerinin bir listesi için [MacOS geliştirme Için Önkoşullar](macos-prerequisites.md) makalesine bakın.

---
