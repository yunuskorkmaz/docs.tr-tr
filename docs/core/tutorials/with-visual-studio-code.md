---
title: C# ve Visual Studio Code - C# Kılavuzu ile çalışmaya başlama
description: Oluşturma ve C# Visual Studio Code kullanarak ilk .NET Core uygulamanızda hata ayıklama hakkında bilgi edinin.
author: kendrahavens
ms.author: mairaw
ms.date: 09/27/2017
ms.openlocfilehash: 8958c39ba16cadbfab95e35fa36e8e85ce0a4ab8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33213623"
---
# <a name="get-started-with-c-and-visual-studio-code"></a>C# ve Visual Studio Code ile çalışmaya başlama

.NET core size Windows, Linux ve macOS çalışan uygulamaları oluşturmak için hızlı ve modüler bir platform sağlar. Visual Studio Code C# uzantısı ile bir güçlü C# IntelliSense (Akıllı kod tamamlama) için tam destek deneyimi düzenleme ve hata ayıklama almak için kullanın.

## <a name="prerequisites"></a>Önkoşullar

1. Yükleme [Visual Studio Code](https://code.visualstudio.com/).
2. Yükleme [.NET Core SDK](https://www.microsoft.com/net/download/core).
3. Yükleme [C# uzantısı](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp) Visual Studio Code için. Visual Studio kodu uzantıları yükleme hakkında daha fazla bilgi için bkz: [VS Code uzantısı Market](https://code.visualstudio.com/docs/editor/extension-gallery).

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
