---
title: C# ve Visual Studio Code kullanmaya başlama
description: Oluşturma ve C# Visual Studio Code kullanarak ilk .NET Core uygulamanızı hata ayıklama hakkında bilgi edinin.
author: kendrahavens
ms.date: 12/05/2018
ms.custom: seodec18
ms.openlocfilehash: ea8b93128e4acd435ad95fc42257df6ab22812fa
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54620558"
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

      ![Visual Studio Code klasörü aç](media/with-visual-studio-code/vs-code-open-folder.png)

2. Bir C# projesi başlatın:
    * Seçerek Visual Studio Code'dan tümleşik Terminalini açın **görünümü** > **tümleşik Terminalini** ana menüden.
    * Terminal penceresinde şunu yazın `dotnet new console`.
    * Bu komut, oluşturur bir `Program.cs` önceden yazılmış, adlı bir C# proje dosyası ile birlikte basit "Merhaba Dünya" programıyla klasörünüzdeki dosya `HelloWorld.csproj`.

      ![Dotnet yeni komutu](media/with-visual-studio-code/dotnet-new-command.png)

3. Derleme varlıkları çözümlemeye:

    * İçin **.NET Core 1.x**, türü `dotnet restore`. Çalışan `dotnet restore` projenizi yapılandırmak için gereken gerekli .NET Core paketleri erişim sağlar.

      ![Dotnet restore komutu](media/with-visual-studio-code/dotnet-restore-command.png)

      [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

4. "Hello World" programı çalıştır:

    * Türü `dotnet run`

      ![Dotnet komutu çalıştırın](media/with-visual-studio-code/dotnet-run-command.png)

Üzerinde ek kurulum Yardım almak için kısa bir video öğreticisini izleyebilirsiniz [Windows](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core), [macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core-on-MacOS), veya [Linux](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).

## <a name="debug"></a>Hata ayıklama

1. Açık *Program.cs* üzerine tıklayarak. Visual Studio Code'da bir C# dosyası açın ilk kez [OmniSharp](https://www.omnisharp.net/) düzenleyicide yükler.

    ![Program.cs dosyasını açın](media/with-visual-studio-code/open-program-cs.png)

2. Visual Studio Code, oluşturmak ve uygulamanızda hata ayıklama için eksik varlıkları eklemek isteyecektir. Seçin **Evet**.

    ![Eksik varlıklar sor](media/with-visual-studio-code/missing-assets.png)

3. Hata ayıklama görünümünü açmak için sol taraftaki menüde hata ayıklama simgesine tıklayın.

    ![Visual Studio Codee içinde hata ayıklama sekmesini açın](media/with-visual-studio-code/open-debug-tab.png)

4. Yeşil ok Bölmenin üst kısmındaki bulun. Yanındaki açılan sahip olduğundan emin olun `.NET Core Launch (console)` seçili.

    ![.NET Core Visual Studio Code'da seçme](media/with-visual-studio-code/select-net-core.png)

5. Tıklayarak bir kesme noktası projenize ekleyin **Düzenleyici kenar**, sol tarafında 9. satıra yanındaki düzenleyicide satır numaralarını alanı veya metin imleç 9. satırına Düzenleyicisi ve tuşuna üzerine <kbd>F9</kbd>.

    ![Bir kesme noktası ayarlama](media/with-visual-studio-code/set-breakpoint-vs-code.png)

6. Hata ayıklamayı başlatmak için seçin <kbd>F5</kbd> veya yeşil oka. Önceki adımda ayarladığınız kesme noktasına ulaştığında hata ayıklayıcı, programınızın yürütülmesini durdurur.
    * Hata ayıklarken, üst sol bölmede, yerel değişkenleri görüntüleyebilir veya hata ayıklama konsolunu kullanın.

7. Hata ayıklamaya devam etmek için üstteki mavi oku seçin veya durdurmak için kırmızı kareyi üst seçin.

    ![Çalıştırın ve Visual Studio Code'da Hata Ayıkla](media/with-visual-studio-code/run-debug-vs-code.png)

> [!TIP]
> Daha fazla bilgi ve sorun giderme ipuçları, .NET Core ile OmniSharp Visual Studio code'da hata ayıklama için bkz: [.NET Core Hata Ayıklayıcısı ' ayarlamaya yönelik yönergeler](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).

## <a name="add-a-class"></a>Bir sınıf ekleyin

1. Yeni bir sınıf sağ tıklatın VSCode Gezgini'nde ekleyin ve seçmek için **yeni dosya**. Bu, VSCode içinde açtığınız klasöre yeni bir dosya ekler.
2. Dosyanızın adı `Class1.cs`. İle kaydetmelisiniz bir `.cs` uzantısı için bir csharp dosyası olarak tanınması için sonunda.
3. İlk sınıfınıza oluşturmak için aşağıdaki kodu ekleyin. Buradan başvurabilmeniz için doğru ad alanını eklediğinizden emin olun, `Program.cs` dosya.
``` csharp
using System;

namespace HelloWorld
{
    public class Class1
    {
        public string ReturnMessage()
        {
            return "Happy coding!";
        }
    }
}
```

4. Yeni sınıfınıza ana yönteminiz çağırmanıza `Program.cs` aşağıdaki kodu ekleyerek.

```csharp
using System;

namespace HelloWorld
{
    class Program
    {
        static void Main(string[] args)
        {
            Class1 c1 = new Class1();
            Console.WriteLine($"Hello World! {c1.ReturnMessage()}");
        }
    }
}
```

5. Yaptığınız değişiklikleri kaydedin ve programınızı tekrar çalıştırın. Eklenen dize ile yeni iletinin görüntülenmesi gerekir.
```console
> dotnet run
Hello World! Happy coding!
```

## <a name="faq"></a>SSS

### <a name="im-missing-required-assets-to-build-and-debug-c-in-visual-studio-code-my-debugger-says-no-configuration"></a>Ben oluşturmak ve C# Visual Studio code'da hata ayıklama için gerekli varlıkları eksik. My hata ayıklayıcı "Yapılandırması yok." diyor.

Visual Studio kodu C# uzantısı oluşturun ve sizin için hata ayıklama için varlıklar oluşturabilir. Visual Studio Code bir C# projesi ilk kez açtığınızda, bu varlıkları oluşturmak isteyip istemediğinizi sorar. Varlık oluşturma olmadı sonra komut paletini açıp bu komutu yine de çalıştırabilirsiniz, (**Görüntüle > komut paleti**) yazarak "> .NET: Varlık oluşturma ve hata ayıklama için oluşturma". Bu seçeneğin seçilmesi gereken .vscode launch.json ve tasks.json yapılandırma dosyalarını oluşturur.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio Code ayarlama](https://code.visualstudio.com/docs/setup/setup-overview)
- [Visual Studio Code'da hata ayıklama](https://code.visualstudio.com/Docs/editor/debugging)
