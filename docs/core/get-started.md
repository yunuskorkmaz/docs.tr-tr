---
title: .NET Core ile başlayın
description: Windows, Linux ve macOS'ta .NET Core uygulamalarının nasıl oluşturüldüğünü öğrenmek için kaynakları bulun.
author: thraka
ms.author: adegeo
ms.date: 12/03/2019
ms.custom: vs-dotnet
ms.openlocfilehash: 0968d9db1dbfbdc8c586328ee8e02315f17950b9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714390"
---
# <a name="get-started-with-net-core"></a>.NET Core ile başlayın

Bu makalede, .NET Core ile başlamak hakkında bilgi sağlar. .NET Core Windows, Linux ve macOS'a yüklenebilir. En sevdiğiniz metin düzenleyicisini kodlayabilir ve platformlar arası kitaplıklar ve uygulamalar oluşturabilirsiniz.

.NET Core'un ne olduğundan veya diğer .NET teknolojileriyle nasıl ilişkili olduğundan emin değilseniz, [.NET'e](https://dotnet.microsoft.com/learn/dotnet/what-is-dotnet) genel bakış nedir ile başlayın. Basitçe söylemek gerekirse, .NET Core .NET'in açık kaynak kodlu, çapraz platform uygulamasıdır.

## <a name="create-an-application"></a>Uygulama oluşturma

Öncelikle [.NET Core SDK'yı](https://dotnet.microsoft.com/download) bilgisayarınıza indirin ve kurun.

Ardından, **PowerShell,** **Komut İstemi**veya **bash**gibi bir terminal açın. C# `dotnet` uygulaması oluşturmak ve çalıştırmak için aşağıdaki komutları yazın:

```dotnetcli
dotnet new console --output sample1
dotnet run --project sample1
```

Aşağıdaki çıktıyı görmeniz gerekir:

```console
Hello World!
```

Tebrikler! Basit bir .NET Core uygulaması oluşturdunuz. Bir .NET Core uygulaması oluşturmak için [Visual Studio Code,](./tutorials/with-visual-studio-code.md) [Visual Studio](./tutorials/with-visual-studio.md) (yalnızca Windows) veya Mac için [Visual Studio](./tutorials/using-on-mac-vs.md) (yalnızca macOS) da kullanabilirsiniz.

## <a name="tutorials"></a>Öğreticiler

Bu adım adım öğreticileri izleyerek .NET Core uygulamalarını geliştirmeye başlayın:

<!-- markdownlint-disable MD025 -->

# <a name="windows"></a>[Windows](#tab/windows)

- [Visual Studio 2019'da ilk .NET Core konsol uygulamanızı oluşturun](./tutorials/with-visual-studio.md)
- [Visual Studio'da .NET Standard ile sınıf kitaplığı oluşturma](./tutorials/library-with-visual-studio.md)
- [.NET Core CLI'yi kullanarak .NET Core ile başlayın](./tutorials/cli-create-console-app.md)

|   |   |
|---|---|
| ![video için film kamera simgesi](./media/video-icon.png "Nasıl yapılacağını görmek için") | Visual [Studio Code ve .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/) videosunu Kanal 9'da nasıl yükleyip kullanacağını izleyin. |
| ![video için film kamera simgesi](./media/video-icon.png "Nasıl yapılacağını görmek için") | YouTube'da [.NET Core 101](https://www.youtube.com/playlist?list=PLdo4fOcmZ0oWoazjhXQzBKMrFuArxpW80) videolarını izleyin. |

Desteklenen Windows sürümlerinin listesi için [.NET Core bağımlılıkları ve gereksinimleri](install/dependencies.md?pivots=os-windows) makalesine bakın.

# <a name="linux"></a>[Linux](#tab/linux)

Bu adım adım öğreticileri izleyerek .NET Core uygulamalarını geliştirmeye başlayın:

- [Komut satırını kullanarak .NET Core ile başlayın](./tutorials/cli-create-console-app.md)

|   |   |
|---|---|
| ![video için film kamera simgesi](./media/video-icon.png "Nasıl yapılacağını görmek için") | [Ubuntu'da C# ve .NET Core kullanarak Visual Studio Code ile başlarken](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu)bir video izleyin. |

Desteklenen Linux dağıtımları ve sürümlerinin listesi için [.NET Core bağımlılıkları](install/dependencies.md?pivots=os-linux) ve gereksinimleri makalesine bakın.

# <a name="macos"></a>[Macos](#tab/macos)

Bu adım adım öğreticileri izleyerek .NET Core uygulamalarını geliştirmeye başlayın:

- [Visual Studio Code kullanarak macOS üzerinde .NET Core kullanmaya başlama](./tutorials/using-on-macos.md)
- [Komut satırını kullanarak .NET Core ile başlayın](./tutorials/cli-create-console-app.md)
- [Mac için Visual Studio kullanarak macOS üzerinde .NET Core kullanmaya başlama](./tutorials/using-on-mac-vs.md)
- [Mac için Visual Studio'u kullanarak macOS'ta eksiksiz bir .NET Core çözümü oluşturun](./tutorials/using-on-mac-vs-full-solution.md)

|   |   |
|---|---|
| ![video için film kamera simgesi](media/video-icon.png "Nasıl yapılacağını görmek için") | [MacOS'ta C# ve .NET Core kullanarak Visual Studio Code ile başlarken](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac)bir video izleyin. |

Desteklenen OS X / macOS sürümlerinin listesi için [.NET Core bağımlılıkları ve gereksinimleri](install/dependencies.md?pivots=os-macos) makalesine bakın.

---
