---
title: "C# ve Visual Studio Code - C# Kılavuzu ile çalışmaya başlama"
description: "Oluşturma ve C# Visual Studio Code kullanarak ilk .NET Core uygulamanızda hata ayıklama hakkında bilgi edinin."
keywords: "C#, Get başlatıldığından, edinme, yükleme, Visual Studio Code, platformlar arası"
author: kendrahavens
ms.author: mairaw
ms.date: 09/27/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 76c23597-4cf9-467e-8a47-0c3703ce37e7
ms.workload: dotnetcore
ms.openlocfilehash: 95052da1688ec1026f11ff679dda6aad50a340fa
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="get-started-with-c-and-visual-studio-code"></a>C# ve Visual Studio Code ile çalışmaya başlama

.NET core size Windows, Linux ve macOS çalışan uygulamaları oluşturmak için hızlı ve modüler bir platform sağlar. Visual Studio Code C# uzantısı ile bir güçlü C# IntelliSense (Akıllı kod tamamlama) için tam destek deneyimi düzenleme ve hata ayıklama almak için kullanın.

## <a name="prerequisites"></a>Önkoşullar

1. Yükleme [Visual Studio Code](https://code.visualstudio.com/).
2. Yükleme [.NET Core SDK](https://www.microsoft.com/net/download/core).
3. Yükleme [C# uzantısı](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp) Visual Studio kod marketten.

## <a name="hello-world"></a>Merhaba Dünya

.NET Core üzerinde basit bir "Hello World" programla başlayalım:

1. Bir proje açın:

    * Visual Studio Code'da açın.
    * Sol menüde Explorer simgesine tıklayın ve ardından **Klasör Aç**.
    * Seçin **dosya** > **klasörünü Aç** olması ve'ı tıklatın, C# projesinde istediğiniz klasörü açmak için ana menüden **Klasör Seç**. Bizim örneğimizde, bir klasör adında Projemizin için oluşturuyoruz *HelloWorld*.

      ![VSCodeOpenFolder](media/with-visual-studio-code/vscodeopenfolder.png)

2. Bir C# projesi başlatın:
    * Visual Studio koddan seçerek tümleşik Terminali açın **Görünüm** > **tümleşik Terminal** ana menüden.
    * Terminal penceresinde yazın `dotnet new console`.
    * Bu komut oluşturur bir `Program.cs` , adlandırılmış bir C# proje dosyası ile birlikte yazılmış bir basit "Hello World" programla klasörünüzdeki dosya `HelloWorld.csproj`.

      ![Dotnet yeni komutu](media/with-visual-studio-code/dotnetnew.png)

3. Yapı varlıklar çözün:

    * İçin **.NET Core 1.x**, türü `dotnet restore`. Çalışan `dotnet restore` projenizi oluşturmak için gereken gerekli .NET Core paketlerini erişim sağlar.

      ![Dotnet restore komutu](media/with-visual-studio-code/dotnetrestore.png)

      [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

4. "Hello World" programı çalıştır:

    * Türü `dotnet run`. 

      ![Dotnet komutunu çalıştırın](media/with-visual-studio-code/dotnetrun.png)

Üzerinde kısa videosu ek kurulum Yardım almak için izleyebileceğiniz [Windows](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core), [macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core-on-MacOS), veya [Linux](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).

## <a name="debug"></a>Hata ayıklama

1. Açık *Program.cs* üzerinde tıklatarak. Visual Studio Code C# dosyasını açın ilk kez [OmniSharp](http://www.omnisharp.net/) Düzenleyicisi'nde yükler.

    ![Program.cs dosyasını açın](media/with-visual-studio-code/opencs.png)

2. Visual Studio Code oluşturun ve uygulamanızın hatalarını ayıklama eksik varlıklar eklemenizi ister. Seçin **Evet**. 

    ![Eksik varlıklar sor](media/with-visual-studio-code/missing-assets.png)

3. Hata ayıklama görünümünü açmak için sol tarafındaki menüde hata ayıklama simgeyi tıklatın.

    ![Hata ayıklama sekmesini açın](media/with-visual-studio-code/opendebug.png)

4. Yeşil ok bölmesinin üst bulun. Aşağı açılan yanında sahip olduğundan emin olun `.NET Core Launch (console)` seçili.

    ![.NET Core seçme](media/with-visual-studio-code/selectcore.png)

5. Kesme noktası tıklayarak projenize ekleme **Düzenleyicisi kenar boşluğu**, sol tarafındaki satırını 9 yanındaki düzenleyicide satır numaralarını alanı olduğu.

    ![Kesme noktası ayarlama](media/with-visual-studio-code/setbreakpoint.png)

6. Hata ayıklama başlatmak için <kbd>F5</kbd> veya yeşil ok. Önceki adımda ayarladığınız kesme noktasına ulaştığında hata ayıklayıcı programınızın çalışmayı durdurur.
    * Hata ayıklama sırasında üst sol bölmede, yerel değişkenleri görüntüleyemez veya hata ayıklama konsolunu kullanın.

    ![Çalıştırın ve hata ayıklama](media/with-visual-studio-code/rundebug.png)

7. Hata ayıklama devam etmek için üst yeşil ok veya durdurmak için kırmızı kare üst seçin.

> [!TIP] 
> Daha fazla bilgi ve .NET Core OmniSharp Visual Studio Code ile hata ayıklama ipuçları sorun giderme için bkz: [.NET çekirdek hata ayıklayıcısı yönergeleri](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).

## <a name="see-also"></a>Ayrıca bkz.
[Visual Studio Code ayarlama](https://code.visualstudio.com/docs/setup/setup-overview)   
[Visual Studio kodda hata ayıklama](https://code.visualstudio.com/Docs/editor/debugging)
