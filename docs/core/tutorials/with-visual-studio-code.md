---
title: C# ve Visual Studio Code kullanmaya başlama
description: Visual Studio Code'u kullanarak C#'daki ilk .NET Core uygulamanızı nasıl oluşturup hata ayıklayarak hata ayıklamayı öğrenin.
author: kendrahavens
ms.date: 12/05/2018
ms.openlocfilehash: 49a1271f2bf74224e189e70bebf0d22c49408e5d
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111068"
---
# <a name="get-started-with-c-and-visual-studio-code"></a>C# ve Visual Studio Code kullanmaya başlama

.NET Core, Windows, Linux ve macOS'ta çalışan uygulamalar oluşturmak için size hızlı ve modüler bir platform sağlar. C# IntelliSense (akıllı kod tamamlama) ve hata ayıklama için tam destek ile güçlü bir düzenleme deneyimi elde etmek için C# uzantısı ile Visual Studio Code kullanın.

## <a name="prerequisites"></a>Ön koşullar

1. [Visual Studio Kodunu](https://code.visualstudio.com/)Yükleyin.
2. [.NET Çekirdek SDK'yı](https://dotnet.microsoft.com/download)yükleyin.
3. Visual Studio Code için [C# uzantısını](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) yükleyin. Visual Studio Code uzantılarının nasıl yüklenir hakkında daha fazla bilgi için [VS Code Extension Marketplace'e](https://code.visualstudio.com/docs/editor/extension-gallery)bakın.

## <a name="hello-world"></a>Hello World

.NET Core'da basit bir "Hello World" programı ile başlayalım:

1. Bir proje açın:

    - Visual Studio Code'u açın.
    - Sol menüdeki Explorer simgesine tıklayın ve ardından **Klasörü Aç'ı**tıklatın.
    - C# projenizin içinde olmasını istediğiniz klasörü açmak için ana menüden **Dosya** > **Aç Klasörünü** seçin ve **Klasörseç'e**tıklayın. Örneğin, *HelloWorld*adlı projemiz için bir klasör oluşturuyoruz.

      ![Visual Studio Code açık klasör](media/with-visual-studio-code/vs-code-open-folder.png)

2. Bir C# projesini başlatma:

    - Ana menüden **View** > **Integrated Terminal'i** seçerek Visual Studio Code'dan Entegre Terminal'i açın.
    - Terminal penceresinde, `dotnet new console`yazın.
    - Bu komut, zaten yazılmış basit bir "Hello World" programı ile klasörünüzde *bir Program.cs* dosyası oluşturur, *HelloWorld.csproj*adlı bir C# proje dosyası ile birlikte.

      ![Dotnet yeni komutu](media/with-visual-studio-code/dotnet-new-command.png)

3. Yapı varlıklarını çözümle:

    - **.NET Core 1.x** `dotnet restore`, türü için . Çalışan, `dotnet restore` projenizi oluşturmak için gereken .NET Core paketlerine erişmenizi sağlar.

      ![Dotnet geri yükleme komutu](media/with-visual-studio-code/dotnet-restore-command.png)

      [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

4. "Hello World" programını çalıştırın:

    - `dotnet run` yazın.

      ![Dotnet çalıştır komutu](media/with-visual-studio-code/dotnet-run-command.png)

Ayrıca [Windows,](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core) [macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core-on-MacOS)veya [Linux](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu)daha fazla kurulum yardım için kısa bir video öğretici izleyebilirsiniz.

## <a name="debug"></a>Hata ayıklama

1. Üzerine tıklayarak *Program.cs* açın. Visual Studio Code'da c# dosyasını ilk açtığınızda, [OmniSharp](https://www.omnisharp.net/) editöre yüklenir.

    ![Program.cs dosyasını açma](media/with-visual-studio-code/open-program-cs.png)

2. Visual Studio Code, uygulamanızı oluşturmak ve hata ayıklamak için eksik varlıkları eklemenizi ister. **Evet'i**seçin.

    ![Eksik varlıklar için komut istemi](media/with-visual-studio-code/missing-assets.png)

3. Hata Ayıklama görünümünü açmak için sol taraftaki menüdeki Hata Ayıklama simgesine tıklayın.

    ![Visual Studio Code'da Hata Ayıklama sekmesini açma](media/with-visual-studio-code/open-debug-tab.png)

4. Bölmenin üst kısmındayeşil oku bulun. Yanındaki açılır bırakmanın **.NET Core Launch (konsol)** seçildiğinden emin olun.

    ![Visual Studio Code'da .NET Core'un seçilmesi](media/with-visual-studio-code/select-net-core.png)

5. **Düzenleyici kenar boşluğuna**tıklayarak projenize bir kesme noktası ekleyin , editördeki satır numaralarının solundaki boşluk, satır 9'un yanında, veya metin imlecini düzenleyicideki 9 satıra taşıyın ve <kbd>F9</kbd>tuşuna basın .

    ![Kesme Noktası Ayarlama](media/with-visual-studio-code/set-breakpoint-vs-code.png)

6. Hata ayıklamaya başlamak için <kbd>F5</kbd> tuşuna basın veya yeşil oku seçin. Hata ayıklama, önceki adımda ayarladığınız kesme noktasına ulaştığında programınızın yürütülmesini durdurur.
    - Hata ayıklama sırasında, yerel değişkenlerinizi sol üst bölmede görüntüleyebilir veya hata ayıklama konsolunu kullanabilirsiniz.

7. Hata ayıklama devam etmek için üstteki mavi oku seçin veya durdurmak için üstteki kırmızı kareyi seçin.

    ![Visual Studio Code'da Çalıştır ve Hata Ayıklama](media/with-visual-studio-code/run-debug-vs-code.png)

> [!TIP]
> Visual Studio Code'da OmniSharp ile .NET Core hata ayıklama hakkında daha fazla bilgi ve sorun giderme ipuçları için [.NET Core hata ayıklayıcısını ayarlama yönergelerine](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md)bakın.

## <a name="add-a-class"></a>Sınıf ekleme

1. Yeni bir sınıf eklemek için VSCode Explorer'a sağ tıklayın ve **Yeni Dosya'yı**seçin. Bu, VSCode'da açtığınız klasöre yeni bir dosya ekler.
2. Dosyanızı *MyClass.cs.* Bir csharp dosyası `.cs` olarak tanınması için sonunda bir uzantısı ile kaydetmeniz gerekir.
3. Birinci sınıf oluşturmak için aşağıdaki kodu ekleyin. *Program.cs* dosyanızdan başvuruda bulunabilmek için doğru ad alanını eklediğinizden emin olun:

    ``` csharp
    using System;

    namespace HelloWorld
    {
        public class MyClass
        {
            public string ReturnMessage()
            {
                return "Happy coding!";
            }
        }
    }
    ```

4. Aşağıdaki kodu ekleyerek *Program.cs* ana yönteminizden yeni sınıfınızı arayın:

    ```csharp
    using System;

    namespace HelloWorld
    {
        class Program
        {
            static void Main(string[] args)
            {
                var c1 = new MyClass();
                Console.WriteLine($"Hello World! {c1.ReturnMessage()}");
            }
        }
    }
    ```

5. Değişikliklerinizi kaydedin ve programınızı yeniden çalıştırın. Yeni ileti eklenen dize ile görünmelidir.

    ```dotnetcli
    dotnet run
    ```

    Aşağıdaki çıkışı alırsınız:

    ```console
    Hello World! Happy coding!
    ```

## <a name="faq"></a>SSS

### <a name="im-missing-required-assets-to-build-and-debug-c-in-visual-studio-code-my-debugger-says-no-configuration"></a>Visual Studio Code'da C# inşa etmek ve hata ayıklamak için gerekli varlıkları kaçırıyorum. Hata ayıklamam "Yapılandırma Yok" diyor.

Visual Studio Code C# uzantısı, sizin için oluşturmak ve hata ayıklamak için varlıklar oluşturabilir. Visual Studio Code, bir C# projesini ilk açtığınızda bu varlıkları oluşturmanızı ister. O zaman varlık oluşturmadıysanız, komut paletini açarak **(komut paletini görüntüle >)** ve ">.NET: Oluşturma ve Hata Ayıklama için Varlıklar Oluştur" yazarak bu komutu çalıştırabilirsiniz. Bunu seçmek, *.vscode*, *launch.json*ve *tasks.json* yapılandırma dosyaları için ihtiyacınız olan dosyaları oluşturur.

## <a name="see-also"></a>Ayrıca bkz.

- [Görsel Stüdyo Kodu Ayarlama](https://code.visualstudio.com/docs/setup/setup-overview)
- [Visual Studio Code'da Hata Ayıklama](https://code.visualstudio.com/Docs/editor/debugging)
