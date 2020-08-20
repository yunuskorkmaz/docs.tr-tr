---
title: .NET Core ile çalışmaya başlama
description: Windows, Linux ve macOS 'ta .NET Core uygulamaları oluşturmayı öğrenmek için kaynakları bulun.
author: adegeo
ms.author: adegeo
ms.date: 12/03/2019
ms.custom: vs-dotnet
ms.openlocfilehash: 56eebc0fc5bad6f57d93358cbbef389d6355d66b
ms.sourcegitcommit: c4a15c6c4ecbb8a46ad4e67d9b3ab9b8b031d849
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/20/2020
ms.locfileid: "88656696"
---
# <a name="get-started-with-net-core"></a>.NET Core ile çalışmaya başlama

Bu makalede, .NET Core ile çalışmaya başlama hakkında bilgi sağlanır. .NET Core, Windows, Linux ve macOS 'a yüklenebilir. En sevdiğiniz metin düzenleyicinizde kod oluşturabilir ve platformlar arası kitaplıklar ve uygulamalar oluşturabilirsiniz.

.NET Core 'un ne olduğu veya diğer .NET teknolojileriyle nasıl ilişkili olduğu konusunda emin değilseniz, [.net](https://dotnet.microsoft.com/learn/dotnet/what-is-dotnet) genel bakış ile başlayın. .NET Core, .NET ' in açık kaynaklı ve platformlar arası bir uygulamasıdır.

## <a name="create-an-application"></a>Uygulama oluşturma

İlk olarak, [.NET Core SDK](https://dotnet.microsoft.com/download) bilgisayarınıza indirip yükleyin.

Ardından, **PowerShell**, **komut istemi**veya **Bash**gibi bir Terminal açın. `dotnet`Bir C# uygulaması oluşturmak ve çalıştırmak için aşağıdaki komutları girin:

```dotnetcli
dotnet new console --output sample1
dotnet run --project sample1
```

Aşağıdaki çıkışı görmeniz gerekir:

```console
Hello World!
```

Tebrikler! Basit bir .NET Core uygulaması oluşturdunuz. .NET Core uygulaması oluşturmak için [Visual Studio Code](./tutorials/with-visual-studio-code.md), [Visual Studio](./tutorials/with-visual-studio.md) (yalnızca Windows) veya [Mac için Visual Studio](tutorials/with-visual-studio-mac.md) (yalnızca MacOS) de kullanabilirsiniz.

## <a name="tutorials"></a>Öğreticiler

Aşağıdaki adım adım öğreticilerden yararlanarak .NET Core uygulamaları geliştirmeye başlayın:

<!-- markdownlint-disable MD025 -->

# <a name="windows"></a>[Windows](#tab/windows)

- [Visual Studio 2019 ' de ilk .NET Core konsol uygulamanızı oluşturma](./tutorials/with-visual-studio.md)
- [Visual Studio 'da .NET Standard bir sınıf kitaplığı oluşturma](./tutorials/library-with-visual-studio.md)
- [Öğretici: Visual Studio Code kullanarak bir .NET Core konsol uygulaması oluşturma](tutorials/with-visual-studio-code.md)

|   |   |
|---|---|
| ![video için film kamerası simgesi](./media/video-icon.png "Nasıl yapılacağını görmek için") | [Visual Studio Code ve .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/) videosunu Kanal 9 ' da nasıl yükleyip kullanacağınızı izleyin. |
| ![video için film kamerası simgesi](./media/video-icon.png "Nasıl yapılacağını görmek için") | YouTube 'daki [.NET Core 101](https://www.youtube.com/playlist?list=PLdo4fOcmZ0oWoazjhXQzBKMrFuArxpW80) videolarını izleyin. |

Desteklenen Windows sürümlerinin bir listesi için bkz. [.NET Core Dependencies ve Requirements](install/dependencies.md?pivots=os-windows) makalesi.

# <a name="linux"></a>[Linux](#tab/linux)

Aşağıdaki adım adım öğreticilerden yararlanarak .NET Core uygulamaları geliştirmeye başlayın:

- [Öğretici: Visual Studio Code kullanarak bir .NET Core konsol uygulaması oluşturma](tutorials/with-visual-studio-code.md)

|   |   |
|---|---|
| ![video için film kamerası simgesi](./media/video-icon.png "Nasıl yapılacağını görmek için") | [Ubuntu 'Da C# ve .NET Core kullanarak Visual Studio Code kullanmaya başlama](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu)hakkında bir video izleyin. |

Desteklenen Linux desteklerinin ve sürümlerinin bir listesi için bkz. [.NET Core Dependencies ve gereksinimler](install/dependencies.md?pivots=os-linux) makalesi.

# <a name="macos"></a>[macOS](#tab/macos)

Aşağıdaki adım adım öğreticilerden yararlanarak .NET Core uygulamaları geliştirmeye başlayın:

- [Öğretici: Visual Studio Code kullanarak bir .NET Core konsol uygulaması oluşturma](tutorials/with-visual-studio-code.md)
- [Öğretici: Mac için Visual Studio kullanarak bir .NET Core konsol uygulaması oluşturma](tutorials/with-visual-studio-mac.md)
- [Mac için Visual Studio kullanarak macOS 'ta .NET Standard kitaplığı oluşturma](tutorials/library-with-visual-studio-mac.md)

|   |   |
|---|---|
| ![video için film kamerası simgesi](media/video-icon.png "Nasıl yapılacağını görmek için") | [MacOS 'Ta C# ve .NET Core kullanarak Visual Studio Code](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac)kullanmaya başlama hakkında bir video izleyin. |

Desteklenen OS X/macOS sürümlerinin bir listesi için bkz. [.NET Core Dependencies ve Requirements](install/dependencies.md?pivots=os-macos) makalesi.

---
