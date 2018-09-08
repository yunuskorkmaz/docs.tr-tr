---
title: C# ve Visual Studio Code - C# Kılavuzu ile çalışmaya başlama
description: Oluşturma ve C# Visual Studio Code kullanarak ilk .NET Core uygulamanızı hata ayıklama hakkında bilgi edinin.
author: kendrahavens
ms.author: mairaw
ms.date: 09/27/2017
ms.openlocfilehash: 321edcebdea141b7290fa57b47c8d9fc91d3521c
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44185960"
---
# <a name="get-started-with-c-and-visual-studio-code"></a>C# ve Visual Studio Code kullanmaya başlama

.NET core Windows, Linux ve macOS üzerinde çalışan uygulamalar oluşturmak için hızlı ve modüler bir platform sunar. Visual Studio Code C# uzantısı ile bir güçlü düzenleme deneyimi ile C# IntelliSense (Akıllı kod tamamlama) için tam destek ve hata ayıklama almak için kullanın.

## <a name="prerequisites"></a>Önkoşullar

1. Yükleme [Visual Studio Code'u](https://code.visualstudio.com/).
2. Yükleme [.NET Core SDK'sı](https://www.microsoft.com/net/download/core).
3. Yükleme [C# uzantısı](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp) Visual Studio Code için. Visual Studio Code uzantılarını yükleme hakkında daha fazla bilgi için bkz. [VS Code uzantı Marketi](https://code.visualstudio.com/docs/editor/extension-gallery).

## <a name="hello-world"></a>Merhaba Dünya

.NET Core üzerinde basit bir "Merhaba Dünya" programıyla Haydi başlayalım:

1. Bir proje açın:

    * Visual Studio Code'u açın.
    * Soldaki menünün Gezgini simgesine tıklayın ve ardından **Klasör Aç**.
    * Seçin **dosya** > **klasörünü Aç** olması ve C# projenize istediğiniz klasörü açmak için ana menüden **Klasör Seç**. Bizim örneğimizde, Projemizin için adlı bir klasör oluşturmakta olduğumuz *HelloWorld*.

      ![VSCodeOpenFolder](media/with-visual-studio-code/vscodeopenfolder.png)

2. Bir C# projesi başlatın:
    * Seçerek Visual Studio Code'dan tümleşik Terminalini açın **görünümü** > **tümleşik Terminalini** ana menüden.
    * Terminal penceresinde şunu yazın `dotnet new console`.
    * Bu komut, oluşturur bir `Program.cs` önceden yazılmış, adlı bir C# proje dosyası ile birlikte basit "Merhaba Dünya" programıyla klasörünüzdeki dosya `HelloWorld.csproj`.

      ![Dotnet yeni komutu](media/with-visual-studio-code/dotnetnew.png)

3. Derleme varlıkları çözümlemeye:

    * İçin **.NET Core 1.x**, türü `dotnet restore`. Çalışan `dotnet restore` projenizi yapılandırmak için gereken gerekli .NET Core paketleri erişim sağlar.

      ![Dotnet restore komutu](media/with-visual-studio-code/dotnetrestore.png)

      [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

4. "Hello World" programı çalıştır:

    * Tür `dotnet run`.

      ![Dotnet komutu çalıştırın](media/with-visual-studio-code/dotnetrun.png)

Üzerinde ek kurulum Yardım almak için kısa bir video öğreticisini izleyebilirsiniz [Windows](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core), [macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core-on-MacOS), veya [Linux](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).

## <a name="debug"></a>Hata ayıklama

1. Açık *Program.cs* üzerine tıklayarak. Visual Studio Code'da bir C# dosyası açın ilk kez [OmniSharp](http://www.omnisharp.net/) düzenleyicide yükler.

    ![Program.cs dosyasını açın](media/with-visual-studio-code/opencs.png)

2. Visual Studio Code, oluşturmak ve uygulamanızda hata ayıklama için eksik varlıkları eklemek isteyecektir. Seçin **Evet**.

    ![Eksik varlıklar sor](media/with-visual-studio-code/missing-assets.png)

3. Hata ayıklama görünümünü açmak için sol taraftaki menüde hata ayıklama simgesine tıklayın.

    ![Hata ayıklama sekmesini açın.](media/with-visual-studio-code/opendebug.png)

4. Yeşil ok Bölmenin üst kısmındaki bulun. Yanındaki açılan sahip olduğundan emin olun `.NET Core Launch (console)` seçili.

    ![.NET Core seçme](media/with-visual-studio-code/selectcore.png)

5. Tıklayarak bir kesme noktası projenize ekleyin **Düzenleyici kenar**, sol tarafında 9. satıra yanındaki düzenleyicide satır numaralarını alanı veya metin imleç 9. satırına Düzenleyicisi ve tuşuna üzerine <kbd>F9</kbd>.

    ![Bir kesme noktası ayarlama](media/with-visual-studio-code/setbreakpoint.png)

6. Hata ayıklamayı başlatmak için seçin <kbd>F5</kbd> veya yeşil oka. Önceki adımda ayarladığınız kesme noktasına ulaştığında hata ayıklayıcı, programınızın yürütülmesini durdurur.
    * Hata ayıklarken, üst sol bölmede, yerel değişkenleri görüntüleyebilir veya hata ayıklama konsolunu kullanın.

    ![Çalıştırma ve hata ayıklama](media/with-visual-studio-code/rundebug.png)

7. Yeşil ok hata ayıklamaya devam etmek için üstteki seçin veya durdurmak için kırmızı kareyi üst seçin.

> [!TIP]
> Daha fazla bilgi ve sorun giderme ipuçları, .NET Core ile OmniSharp Visual Studio code'da hata ayıklama için bkz: [.NET Core Hata Ayıklayıcısı ' ayarlamaya yönelik yönergeler](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).

## <a name="faq"></a>SSS

### <a name="im-missing-required-assets-to-build-and-debug-c-in-visual-studio-code-my-debugger-says-no-configuration"></a>Ben oluşturmak ve C# Visual Studio code'da hata ayıklama için gerekli varlıkları eksik. My hata ayıklayıcı "Yapılandırması yok." diyor.

Visual Studio kodu C# uzantısı oluşturun ve sizin için hata ayıklama için varlıklar oluşturabilir. Visual Studio Code bir C# projesi ilk kez açtığınızda, bu varlıkları oluşturmak isteyip istemediğinizi sorar. Varlık oluşturma olmadı sonra komut paletini açıp bu komutu yine de çalıştırabilirsiniz, (**Görüntüle > komut paleti**) yazarak "> .NET: derleme ve hata ayıklama için varlık oluşturma". Bu seçeneğin seçilmesi gereken .vscode launch.json ve tasks.json yapılandırma dosyalarını oluşturur.

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio Code ayarlama](https://code.visualstudio.com/docs/setup/setup-overview)
* [Visual Studio Code'da hata ayıklama](https://code.visualstudio.com/Docs/editor/debugging)
