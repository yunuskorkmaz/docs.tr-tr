---
title: C# ve Visual Studio Code kullanmaya başlama
description: Visual Studio Code kullanarak C# ' de ilk .NET Core uygulamanızı nasıl oluşturacağınızı ve hata ayıklacağınızı öğrenin.
author: kendrahavens
ms.date: 04/23/2020
ms.openlocfilehash: 3dd7c4602fbb27e29bad977f8d3df34b6061bc23
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82506924"
---
# <a name="get-started-with-c-and-visual-studio-code"></a>C# ve Visual Studio Code kullanmaya başlama

.NET Core, Windows, Linux ve macOS 'ta çalışan uygulamalar oluşturmaya yönelik hızlı ve modüler bir platform sağlar. C# IntelliSense ile Visual Studio Code kullanın (akıllı kod tamamlama) ve hata ayıklama için tam destek sayesinde güçlü bir düzen deneyimi alın.

## <a name="prerequisites"></a>Ön koşullar

1. [Visual Studio Code](https://code.visualstudio.com/)'i yükler.
2. [.NET Core SDK](https://dotnet.microsoft.com/download)'i yükler.
3. Visual Studio Code için [C# uzantısını](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) yükler. Visual Studio Code uzantıları nasıl yükleyeceğiniz hakkında daha fazla bilgi için bkz. [vs Code uzantısı marketi](https://code.visualstudio.com/docs/editor/extension-gallery).

## <a name="hello-world"></a>Hello World

.NET Core üzerinde basit bir "Merhaba Dünya" programı ile çalışmaya başlayın:

1. Bir proje açın:

    - Visual Studio Code'u açın.
    - Ana menüden **Dosya** > **Aç klasörünü** seçin.
    - *HelloWorld*adlı bir klasör oluşturun ve **Klasör Seç**' e tıklayın. Klasör adı, varsayılan olarak proje adı ve ad alanı adı olur. Daha sonra, proje ad alanının olduğunu `HelloWorld`varsayan öğreticide kod ekleyeceksiniz.

1. C# projesi Başlat:

    - Ana menüden **Görünüm** > **terminali** ' i seçerek Visual Studio Code terminalden açın.
    - Terminal penceresinde, girin `dotnet new console`.

      Bu komut, klasörünüzde zaten yazılmış olan basit bir "Merhaba Dünya" programı ile birlikte *HelloWorld. csproj*adlı bir C# proje dosyası içeren bir *program.cs* dosyası oluşturur.

      ![DotNet yeni komutu](media/with-visual-studio-code/dotnet-new-command.png)

1. "Merhaba Dünya" programını çalıştırın:

    - Terminal penceresinde, girin `dotnet run`.

      ![DotNet Run komutu](media/with-visual-studio-code/dotnet-run-command.png)

## <a name="debug"></a>Hata ayıklama

1. Üzerine tıklayarak *program.cs* açın. Visual Studio Code bir C# dosyasını ilk açışınızda, [Omnisharp](https://www.omnisharp.net/) düzenleyicide yüklenir.

    ![Program.cs dosyasını açın](media/with-visual-studio-code/open-program-cs.png)

1. Visual Studio Code, uygulamanızda derleme ve hata ayıklama için eksik varlıkları eklemenizi ister. **Evet**' i seçin.

    ![Eksik varlıklar için istem](media/with-visual-studio-code/missing-assets.png)

1. Hata ayıklama görünümünü açmak için sol taraftaki menüdeki hata ayıklama simgesine tıklayın.

    ![Visual Studio Code hata ayıkla sekmesini açın](media/with-visual-studio-code/open-debug-tab.png)

1. Bölmenin en üstündeki yeşil oku bulun. ' In yanındaki açılan kutuda **.NET Core başlatma (konsol)** seçili olduğundan emin olun.

    ![Visual Studio Code .NET Core seçme](media/with-visual-studio-code/select-net-core.png)

1. Düzenleyicide satır numaralarının solundaki boşluk olan **Düzenleyici kenar boşluğuna**, 9. satırın yanında bir kesme noktası ekleyin veya metin imlecini düzenleyicide 9. satıra taşıyın ve <kbd>F9</kbd>tuşuna basın.

    ![Kesme noktası ayarlama](media/with-visual-studio-code/set-breakpoint-vs-code.png)

1. Hata ayıklamayı başlatmak için <kbd>F5</kbd> 'e basın veya yeşil oku seçin. Hata ayıklayıcı, önceki adımda ayarladığınız kesme noktasına ulaştığında programınızın yürütülmesini durduruyor.
    - Hata ayıklarken, sol üst bölmedeki yerel değişkenlerinizi görüntüleyebilir veya hata ayıklama konsolunu kullanabilirsiniz.

1. Hata ayıklamaya devam etmek için üstteki mavi oku seçin ya da durdurmak için üstteki kırmızı kareyi seçin.

    ![Visual Studio Code Çalıştır ve hata ayıkla](media/with-visual-studio-code/run-debug-vs-code.png)

> [!TIP]
> .NET Core hata ayıklama hakkında daha fazla bilgi ve Visual Studio Code ile ilgili sorun giderme ipuçları için, [.NET Core hata ayıklayıcısını ayarlama yönergelerine](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md)bakın.

## <a name="add-a-class"></a>Sınıf ekleme

1. Yeni bir sınıf eklemek için, *program.cs* aşağıdaki vscode Explorer ' a sağ tıklayıp **yeni dosya**' yı seçin. Bu, VSCode 'da açtığınız klasöre yeni bir dosya ekler.
1. Dosyanızı *MyClass.cs*olarak adlandırın. Bir CSharp dosyası olarak tanınabilmesi `.cs` için onu sonda bir uzantıyla kaydetmelisiniz.
1. İlk sınıfınızı oluşturmak için aşağıdaki kodu ekleyin.

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

1. Program.cs içindeki kodu aşağıdaki kodla değiştirerek `Main` , yönteinizden yeni sınıfınızı çağırın *Program.cs* :

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

1. Yaptığınız değişiklikleri kaydedin.

1. Programı yeniden çalıştırın.

    ```dotnetcli
    dotnet run
    ```

    Yeni ileti eklenmiş dize ile görüntülenir.

    ```console
    Hello World! Happy coding!
    ```

## <a name="faq"></a>SSS

### <a name="im-missing-required-assets-to-build-and-debug-c-in-visual-studio-code-my-debugger-says-no-configuration"></a>Visual Studio Code C# derlemek ve hatalarını ayıklamak için gerekli varlıkların yok. Hata ayıklayıcı "yapılandırma yok" diyor.

Visual Studio Code C# uzantısı sizin için derlemek ve hata ayıklamak için varlıklar oluşturabilir. Visual Studio Code, ilk olarak bir C# projesi açtığınızda bu varlıkları oluşturmanızı ister. Daha sonra varlık oluşturmadıysanız, bu komutu yine de komut paletini açıp **>**(derleme ve hata ayıklama Için varlık oluştur) "> .net: varlıkları oluşturma ve hata ayıklama" yazarak çalıştırabilirsiniz. Bunu seçtiğinizde, ihtiyacınız olan *. vscode*, *Launch. JSON*ve *Tasks. JSON* yapılandırma dosyaları oluşturulur.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio Code ayarlama](https://code.visualstudio.com/docs/setup/setup-overview)
- [Visual Studio Code 'de hata ayıklama](https://code.visualstudio.com/Docs/editor/debugging)
