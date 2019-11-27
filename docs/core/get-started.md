---
title: .NET Core ile çalışmaya başlama
description: Windows, Linux ve macOS 'ta .NET Core uygulamaları oluşturmayı öğrenmek için kaynakları bulun.
author: thraka
ms.author: adegeo
ms.date: 09/19/2019
ms.openlocfilehash: 78066f2904f6a874b71165e4fe1769b6b778ae41
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428876"
---
# <a name="get-started-with-net-core"></a>.NET Core ile çalışmaya başlama

Bu makalede, .NET Core ile çalışmaya başlama hakkında bilgi sağlanır. .NET Core, Windows, Linux ve macOS 'a yüklenebilir. En sevdiğiniz metin düzenleyicinizde kod oluşturabilir ve platformlar arası kitaplıklar ve uygulamalar oluşturabilirsiniz. 

.NET Core 'un ne olduğunu veya diğer .NET teknolojileriyle nasıl ilişkili olduğunu bilmiyorsanız, [.net](https://dotnet.microsoft.com/learn/dotnet/what-is-dotnet) genel bakış ile başlayın. .NET Core, .NET ' in açık kaynaklı ve platformlar arası bir uygulamasıdır.

## <a name="create-an-application"></a>Uygulama oluşturma

İlk olarak, [.NET Core SDK](https://dotnet.microsoft.com/download) bilgisayarınıza indirip yükleyin.

Ardından, **PowerShell**, **komut istemi**veya **Bash**gibi bir Terminal açın. Bir C# uygulama oluşturmak ve çalıştırmak için aşağıdaki `dotnet` komutlarını yazın:

```dotnetcli
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

<!-- markdownlint-disable MD025 -->

# <a name="windowstabwindows"></a>[Windows](#tab/windows)

- [Visual Studio C# 2017 ' de .NET Core ile bir "Merhaba Dünya" uygulaması oluşturun.](./tutorials/with-visual-studio.md)
- [Visual Studio C# 2017 ' de .NET Core ile bir sınıf kitaplığı oluşturun.](./tutorials/library-with-visual-studio.md)
- [Visual Studio 2017 ' de .NET Core ile bir Visual Basic "Merhaba Dünya" uygulaması oluşturun.](./tutorials/vb-with-visual-studio.md)
- [Visual Studio 2017 ' de Visual Basic ve .NET Core ile bir sınıf kitaplığı oluşturun.](./tutorials/vb-library-with-visual-studio.md)  
- [Visual Studio Code ve .NET Core 'u yüklemek ve kullanmak için](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/)bir video izleyin.
- [Visual Studio 2017 ve .NET Core 'u yüklemek ve kullanmak için](https://channel9.msdn.com/Blogs/dotnet/Get-Started-NET-Core-Visual-Studio-2017/)bir video izleyin.
- [Komut satırını kullanarak .NET Core ile çalışmaya başlama.](tutorials/using-with-xplat-cli.md)

Desteklenen Windows sürümlerinin bir listesi için bkz. [.NET Core Dependencies ve Requirements](install/dependencies.md?tabs=netcore30&pivots=os-windows) makalesi.

# <a name="linuxtablinux"></a>['Un](#tab/linux)

Aşağıdaki adım adım öğreticilerden yararlanarak .NET Core uygulaması geliştirmeye başlamanızı sağlayabilirsiniz:

- [Komut satırını kullanarak .NET Core ile çalışmaya başlama.](tutorials/using-with-xplat-cli.md)
- [Ubuntu 'da ve .NET Core 'u kullanarak C# Visual Studio Code](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu)kullanmaya başlama hakkında bir video izleyin.

Desteklenen Linux desteklerinin ve sürümlerinin bir listesi için bkz. [.NET Core Dependencies ve gereksinimler](install/dependencies.md?tabs=netcore30&pivots=os-linux) makalesi.

# <a name="macostabmacos"></a>[macOS](#tab/macos)

Aşağıdaki adım adım öğreticilerden yararlanarak .NET Core uygulaması geliştirmeye başlamanızı sağlayabilirsiniz:

- [MacOS 'ta .NET Core 'u kullanarak C# Visual Studio Code](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac)kullanmaya başlama hakkında bir video izleyin.
- [Visual Studio Code kullanarak macOS 'ta .NET Core ile çalışmaya başlama.](tutorials/using-on-macos.md)
- [Komut satırını kullanarak .NET Core ile çalışmaya başlama.](tutorials/using-with-xplat-cli.md)
- [Mac için Visual Studio kullanarak macOS 'ta .NET Core ile çalışmaya başlama.](tutorials/using-on-mac-vs.md)
- [Mac için Visual Studio kullanarak macOS 'ta kapsamlı bir .NET Core çözümü oluşturun.](tutorials/using-on-mac-vs-full-solution.md)

Desteklenen OS X/macOS sürümlerinin bir listesi için bkz. [.NET Core Dependencies ve Requirements](install/dependencies.md?tabs=netcore30&pivots=os-macos) makalesi.

---
