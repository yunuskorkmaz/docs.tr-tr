---
title: C# ve Visual Studio Code kullanmaya başlama
description: Visual Studio Code C# kullanarak Ilk .NET Core uygulamanızı nasıl oluşturacağınızı ve hata ayıklacağınızı öğrenin.
author: kendrahavens
ms.date: 12/05/2018
ms.openlocfilehash: ef7134e26c1ded3926faa51748c1b6d4a461008f
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156614"
---
# <a name="get-started-with-c-and-visual-studio-code"></a>C# ve Visual Studio Code kullanmaya başlama

.NET Core, Windows, Linux ve macOS 'ta çalışan uygulamalar oluşturmaya yönelik hızlı ve modüler bir platform sağlar. IntelliSense (akıllı kod C# tamamlama) ve hata ayıklama için C# tam desteğe sahip güçlü bir düzen deneyimi almak üzere uzantıya sahip Visual Studio Code kullanın.

## <a name="prerequisites"></a>Önkoşullar

1. [Visual Studio Code](https://code.visualstudio.com/)'i yükler.
2. [.NET Core SDK](https://dotnet.microsoft.com/download)'i yükler.
3. Visual Studio Code [ C# uzantısını](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp) yükler. Visual Studio Code uzantıları nasıl yükleyeceğiniz hakkında daha fazla bilgi için bkz. [vs Code uzantısı marketi](https://code.visualstudio.com/docs/editor/extension-gallery).

## <a name="hello-world"></a>Hello World

.NET Core üzerinde basit bir "Merhaba Dünya" programı kullanmaya başlayalım:

1. Bir proje açın:

    - Visual Studio Code'u açın.
    - Sol menüdeki gezgin simgesine ve ardından **klasörü aç**' a tıklayın.
    - Ana menüdeki **dosya** > **klasörü aç** ' ı seçerek C# projenizin Içinde olmasını istediğiniz klasörü açın ve **Klasör Seç**' e tıklayın. Bizim örneğimizde *HelloWorld*adlı projemiz için bir klasör oluşturuluyoruz.

      ![Visual Studio Code klasörü aç](media/with-visual-studio-code/vs-code-open-folder.png)

2. C# Projeyi Başlat:

    - Ana menüden > **Tümleşik Terminal** 'yi **göster** ' i seçerek Visual Studio Code tümleşik terminalden açın.
    - Terminal penceresinde `dotnet new console`yazın.
    - Bu komut, klasörünüzde zaten yazılmış olan basit bir "Merhaba Dünya" programı ile birlikte *HelloWorld. csproj*adlı bir C# proje dosyası içeren bir *program.cs* dosyası oluşturur.

      ![DotNet yeni komutu](media/with-visual-studio-code/dotnet-new-command.png)

3. Derleme varlıklarını çözümleyin:

    - **.NET Core 1. x**için `dotnet restore`yazın. `dotnet restore` çalıştırmak, projenizi derlemek için gereken gerekli .NET Core paketlerine erişmenizi sağlar.

      ![dotnet restore komutu](media/with-visual-studio-code/dotnet-restore-command.png)

      [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

4. "Merhaba Dünya" programını çalıştırın:

    - `dotnet run` yazın.

      ![DotNet Run komutu](media/with-visual-studio-code/dotnet-run-command.png)

Ayrıca, [Windows](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core), [MacOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core-on-MacOS)veya [Linux](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu)hakkında daha fazla kurulum yardımı için kısa bir video öğreticisini izleyebilirsiniz.

## <a name="debug"></a>Hata ayıklama

1. Üzerine tıklayarak *program.cs* açın. Visual Studio Code bir C# dosyayı ilk açışınızda, [Omnisharp](https://www.omnisharp.net/) , düzenleyicide yüklenir.

    ![Program.cs dosyasını açın](media/with-visual-studio-code/open-program-cs.png)

2. Visual Studio Code, uygulamanızda derlemek ve hata ayıklamak için eksik varlıkları eklemenizi ister. **Evet**’i seçin.

    ![Eksik varlıklar için istem](media/with-visual-studio-code/missing-assets.png)

3. Hata ayıklama görünümünü açmak için sol taraftaki menüdeki hata ayıklama simgesine tıklayın.

    ![Visual Studio Code hata ayıkla sekmesini açın](media/with-visual-studio-code/open-debug-tab.png)

4. Bölmenin en üstündeki yeşil oku bulun. ' In yanındaki açılan kutuda **.NET Core başlatma (konsol)** seçili olduğundan emin olun.

    ![Visual Studio Code .NET Core seçme](media/with-visual-studio-code/select-net-core.png)

5. Düzenleyicide satır numaralarının solundaki boşluk olan **Düzenleyici kenar boşluğuna**, 9. satırın yanında bir kesme noktası ekleyin veya metin imlecini düzenleyicide 9. satıra taşıyın ve <kbd>F9</kbd>tuşuna basın.

    ![Kesme noktası ayarlama](media/with-visual-studio-code/set-breakpoint-vs-code.png)

6. Hata ayıklamayı başlatmak için <kbd>F5</kbd> 'e basın veya yeşil oku seçin. Hata ayıklayıcı, önceki adımda ayarladığınız kesme noktasına ulaştığında programınızın yürütülmesini durduruyor.
    - Hata ayıklarken, sol üst bölmedeki yerel değişkenlerinizi görüntüleyebilir veya hata ayıklama konsolunu kullanabilirsiniz.

7. Hata ayıklamaya devam etmek için üstteki mavi oku seçin ya da durdurmak için üstteki kırmızı kareyi seçin.

    ![Visual Studio Code Çalıştır ve hata ayıkla](media/with-visual-studio-code/run-debug-vs-code.png)

> [!TIP]
> .NET Core hata ayıklama hakkında daha fazla bilgi ve Visual Studio Code ile ilgili sorun giderme ipuçları için, [.NET Core hata ayıklayıcısını ayarlama yönergelerine](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md)bakın.

## <a name="add-a-class"></a>Sınıf ekleme

1. Yeni bir sınıf eklemek için VSCode Gezgini ' ne sağ tıklayıp **yeni dosya**' yı seçin. Bu, VSCode 'da açtığınız klasöre yeni bir dosya ekler.
2. Dosyanızı *MyClass.cs*olarak adlandırın. Bir CSharp dosyası olarak tanınabilmesi için, bu dosyayı sonda bir `.cs` uzantısıyla kaydetmelisiniz.
3. İlk sınıfınızı oluşturmak için aşağıdaki kodu ekleyin. *Program.cs* dosyanıza başvurabilmeniz için doğru ad alanını eklediğinizden emin olun:

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

4. Aşağıdaki kodu ekleyerek yeni sınıfınızı *program.cs* içindeki Main yönteminden çağırın:

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

5. Değişikliklerinizi kaydedin ve programınızı yeniden çalıştırın. Yeni ileti, eklenen dizeyle birlikte görünmelidir.

    ```dotnetcli
    dotnet run
    ```

    Aşağıdaki çıkışı alırsınız:

    ```console
    Hello World! Happy coding!
    ```

## <a name="faq"></a>SSS

### <a name="im-missing-required-assets-to-build-and-debug-c-in-visual-studio-code-my-debugger-says-no-configuration"></a>Visual Studio Code derlemek ve hata ayıklamak C# için gerekli varlıkların yok. Hata ayıklayıcı "yapılandırma yok" diyor.

Visual Studio Code C# uzantısı sizin için derlemek ve hata ayıklamak üzere varlık oluşturabilir. Visual Studio Code, bir C# projeyi ilk açtığınızda bu varlıkları oluşturmanız istenir. Daha sonra varlık oluşturmadıysanız, bu komutu yine de komut paletini açıp **>** (derleme ve hata ayıklama Için varlık oluştur) "> .net: varlıkları oluşturma ve hata ayıklama" yazarak çalıştırabilirsiniz. Bunu seçtiğinizde, ihtiyacınız olan *. vscode*, *Launch. JSON*ve *Tasks. JSON* yapılandırma dosyaları oluşturulur.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio Code ayarlama](https://code.visualstudio.com/docs/setup/setup-overview)
- [Visual Studio Code 'de hata ayıklama](https://code.visualstudio.com/Docs/editor/debugging)
