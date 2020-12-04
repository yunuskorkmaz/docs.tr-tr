---
title: Mac için Visual Studio kullanarak bir .NET sınıf kitaplığı oluşturma
description: Mac için Visual Studio kullanarak .NET sınıf kitaplığı oluşturmayı öğrenin.
ms.date: 11/30/2020
ms.openlocfilehash: 1b6b26de06d18d505fa6dde3ff9779a3dab3f1e6
ms.sourcegitcommit: 9d525bb8109216ca1dc9e39c149d4902f4b43da5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96599321"
---
# <a name="tutorial-create-a-net-class-library-using-visual-studio-for-mac"></a>Öğretici: Mac için Visual Studio kullanarak .NET sınıf kitaplığı oluşturma

Bu öğreticide, tek bir dize işleme yöntemi içeren bir sınıf kitaplığı oluşturacaksınız.

Bir *sınıf kitaplığı* , bir uygulama tarafından çağrılan türleri ve yöntemleri tanımlar. Kitaplık .NET Standard 2,0 hedefliyorsa, .NET Standard 2,0 ' yi destekleyen herhangi bir .NET uygulamasıyla (.NET Framework dahil) çağrılabilir. Kitaplık .NET 5 ' i hedefliyorsa, .NET 5 ' i hedefleyen herhangi bir uygulama tarafından çağrılabilir. Bu öğreticide, .NET 5 ' in nasıl hedeflenecek gösterilmektedir.

> [!NOTE]
> Geri bildiriminiz çok değerli. Mac için Visual Studio üzerinde geliştirme ekibine geri bildirimde bulunmak için kullanabileceğiniz iki yol vardır:
>
> - Mac için Visual Studio, **Help**  >  menüden **sorun bildir** veya hoş geldiniz ekranından **sorun** bildir ' i seçerek bir hata raporu dosyalamayı sağlayan bir pencere açar. Geri bildiriminizi [Geliştirici Topluluğu](https://aka.ms/feedback/report?space=41) portalında izleyebilirsiniz.
> - Öneride bulunmak için, **Help**  >  menüden **öneriler sağlama** veya hoş geldiniz ekranından [Mac için Visual Studio Geliştirici topluluğu Web sayfasına](https://aka.ms/feedback/suggest?space=41)götüren **bir öneri** sağlama ' yı seçin.

## <a name="prerequisites"></a>Önkoşullar

* [Mac için Visual Studio sürüm 8,8 veya üstünü yükler](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link). .NET Core ' u yüklemek için seçeneği belirleyin. Xamarin 'in yüklenmesi .NET geliştirme için isteğe bağlıdır. Daha fazla bilgi için aşağıdaki kaynaklara bakın:

  * [Öğretici: Mac için Visual Studio yüklemesi](/visualstudio/mac/installation).
  * [Desteklenen macOS sürümleri](../install/macos.md).
  * [Mac için Visual Studio tarafından desteklenen .NET sürümleri](/visualstudio/mac/net-core-support).

## <a name="create-a-solution-with-a-class-library-project"></a>Sınıf kitaplığı projesiyle çözüm oluşturma

Visual Studio çözümü bir veya daha fazla proje için kapsayıcı görevi görür. Çözümde bir çözüm ve bir sınıf kitaplığı projesi oluşturun. Aynı çözüme daha sonra ek ve ilgili projeler ekleyeceksiniz.

1. Mac için Visual Studio başlatın.

1. Başlangıç penceresinde **Yeni proje**' yi seçin.

1. **Yeni projeniz için bir şablon seçin** iletişim kutusunda **Web ve konsol**  >  **kitaplığı**  >  **sınıf kitaplığı**' nı seçin ve ardından **İleri**' yi seçin.

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-new-project.png" alt-text="Yeni proje iletişim kutusu":::

1. **Yeni sınıf kitaplığınızı yapılandırın** iletişim kutusunda, **.NET 5,0**' i seçin ve **İleri**' yi seçin.

1. "StringLibrary" projesini ve "ClassLibraryProjects" çözümünü adlandırın. **Çözüm dizini içinde bir proje dizini oluştur** ' un seçili kalsın. **Oluştur**’u seçin.

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-new-project-options.png" alt-text="Yeni proje iletişim kutusu seçeneklerini Mac için Visual Studio":::

1. Ana menüden **View**  >  **çözümü** görüntüle ' yi seçin ve paneli açık tutmak için Yerleştir simgesini seçin.

   :::image type="content" source="media/library-with-visual-studio-mac/solution-dock-icon.png" alt-text="Çözüm paneli için yerleştirme simgesi":::

1. **Çözüm** panelinde, `StringLibrary` *Class1.cs* şablonu tarafından sunulan sınıf dosyasını açığa çıkarmak için düğümünü genişletin. <kbd>CTRL</kbd>-dosyaya tıklayın, bağlam menüsünden **Yeniden Adlandır** ' ı seçin ve dosyayı *StringLibrary.cs* olarak yeniden adlandırın. Dosyasını açın ve içeriğini şu kodla değiştirin:

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibrary/Class1.cs":::

1. Dosyayı kaydetmek için <kbd>⌘</kbd><kbd>s</kbd> (<kbd>komut</kbd> + <kbd>S</kbd>) tuşuna basın.

1. **Hatalar** panelini açmak için IDE penceresinin altındaki kenar boşluğunda bulunan **hataları** seçin. **Derleme çıkışı** düğmesini seçin.

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-error-button.png" alt-text="Visual Studio Mac IDE 'nin hatalar düğmesini gösteren alt kenar boşluğu":::

1. Menüden **Build**  >  **Build All** öğesini seçin.

   Çözüm oluşturulur. Yapı çıktı paneli, yapılandırmanın başarılı olduğunu gösterir.

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-build-panel.png" alt-text="Derleme başarılı iletisi ile hatalar panelinin Visual Studio Mac derleme çıkış bölmesi":::

## <a name="add-a-console-app-to-the-solution"></a>Çözüme bir konsol uygulaması ekleme

Sınıf kitaplığını kullanan bir konsol uygulaması ekleyin. Uygulama kullanıcıdan bir dize girmesini ister ve dizenin büyük harfli bir karakterle başlayıp başlamamadığını rapor eder.

1. **Çözüm** panelinde, çözüme <kbd>CTRL</kbd>-tıklayın `ClassLibraryProjects` . **Web ve konsol** uygulaması şablonlarından şablonu seçerek yeni bir **konsol uygulaması** projesi ekleyin  >  **App** ve **İleri**' yi seçin.

1. **Hedef çerçeve** olarak **.NET 5,0** ' i seçin ve **İleri ' yi** seçin.

1. Proje **tanıtımı** adlandırın. Projeyi çözümde oluşturmak için **Oluştur** ' u seçin.

   :::image type="content" source="media/library-with-visual-studio-mac/add-showcase-project.png" alt-text="Gösterimi projesi Ekle":::

1. *Program.cs* dosyasını açın. Kodu şu kodla değiştirin:

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/ShowCase/Program.cs":::

   Program kullanıcıdan bir dize girmesini ister. Dizenin büyük harfle başlatılıp başlatılmayacağını gösterir. Kullanıcı bir dize girmeden <kbd>ENTER</kbd> tuşuna basarsa, uygulama sonlanır ve konsol penceresi kapanır.

   Kod, `row` konsol penceresine yazılan veri satırlarının sayısını korumak için değişkenini kullanır. 25 ' e eşit veya daha büyük olduğunda, kod konsol penceresini temizler ve kullanıcıya bir ileti görüntüler.

## <a name="add-a-project-reference"></a>Proje başvurusu Ekle

Başlangıçta, yeni konsol uygulaması projesi sınıf kitaplığına erişemez. Sınıf kitaplığındaki yöntemleri çağırmasına izin vermek için, sınıf kitaplığı projesine bir proje başvurusu oluşturun.

1. **Çözümler** panelinde **, yeni Gösterim** projesinin **Bağımlılıklar** düğümüne <kbd>CTRL tuşuna</kbd>tıklayın. Bağlam menüsünde **Başvuru Ekle**' yi seçin.

1. **Başvurular** Iletişim kutusunda **StringLibrary** ' yi seçin ve **Tamam**' ı seçin.

## <a name="run-the-app"></a>Uygulamayı çalıştırma

1. <kbd>CTRL tuşunu basılı</kbd>olarak **projeye tıklayın** ve bağlam menüsünden **projeyi Çalıştır** ' ı seçin.

1. Dizeleri girerek ve <kbd>ENTER</kbd>'a basarak programı deneyin ve çıkmak için <kbd>ENTER</kbd> tuşuna basın.

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-console-window.png" alt-text="Uygulamanızın çalıştığını gösteren Mac için Visual Studio konsol penceresi":::

## <a name="additional-resources"></a>Ek kaynaklar

* [.NET CLı ile Kitaplıklar geliştirme](libraries.md)
* [Mac için Visual Studio 2019 Sürüm Notları](/visualstudio/releasenotes/vs2019-mac-relnotes)
* [.NET Standard sürümleri ve destekledikleri platformlar](../../standard/net-standard.md).

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, bir çözüm ve kitaplık projesi oluşturdunuz ve kitaplığı kullanan bir konsol uygulaması projesi eklediniz. Sonraki öğreticide, çözüme bir birim testi projesi eklersiniz.

> [!div class="nextstepaction"]
> [Mac için Visual Studio kullanarak .NET sınıf kitaplığı test etme](testing-library-with-visual-studio-mac.md)
