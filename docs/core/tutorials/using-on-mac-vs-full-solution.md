---
title: Mac için Visual Studio kullanarak tüm .NET Core çözümü oluşturma
description: Bu makalede, yeniden kullanılabilir bir kitaplık ve birim testi içeren bir .NET Core çözümü oluşturma işlemi adım adım açıklanmaktadır.
author: mairaw
ms.date: 12/19/2019
ms.openlocfilehash: f4284cd4c3c8b358b87c31c0fd5c067b1e7fb8a2
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715358"
---
# <a name="build-a-complete-net-core-solution-on-macos-using-visual-studio-for-mac"></a>Mac için Visual Studio kullanarak macOS 'ta kapsamlı bir .NET Core çözümü oluşturun

Mac için Visual Studio .NET Core uygulamaları geliştirmek için tam özellikli bir tümleşik geliştirme ortamı (IDE) sağlar. Bu makalede, yeniden kullanılabilir bir kitaplık ve birim testi içeren bir .NET Core çözümü oluşturma işlemi adım adım açıklanmaktadır.

Bu öğreticide, bir arama sözcüğünü ve kullanıcıdan bir metin dizesini kabul eden bir uygulama oluşturma, bir sınıf kitaplığındaki yöntemi kullanarak arama sözcüğünün dize içinde görünme sayısını saymakta ve sonucu kullanıcıya döndürmekte olduğunuz gösterilmektedir. Çözüm, birim testi kavramlarına giriş olarak sınıf kitaplığı için birim testi de içerir. Öğreticide bir bütün örnekle devam etmek isterseniz, [örnek çözümü](https://github.com/dotnet/samples/blob/master/core/tutorials/using-on-mac-vs-full-solution/WordCounter)indirin. İndirme yönergeleri için bkz. [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

> [!NOTE]
> Geri bildiriminiz çok değerli. Mac için Visual Studio üzerinde geliştirme ekibine geri bildirimde bulunmak için kullanabileceğiniz iki yol vardır:
>
> - Mac için Visual Studio, menüden **sorun bildirmek** > **Yardım** ' ı veya bir hata raporu dosyalayarak bir pencere açan hoş geldiniz ekranından **sorun bildir** ' i seçin. Geri bildiriminizi [Geliştirici Topluluğu](https://developercommunity.visualstudio.com/spaces/41/index.html) portalında izleyebilirsiniz.
> - Bir öneride bulunmak için, **yardım** > menüden **bir öneri sağlayın** ya da size [Mac için Visual Studio Geliştirici topluluğu Web sayfasına](https://developercommunity.visualstudio.com/content/idea/post.html?space=41)götüren hoş geldiniz ekranından **bir öneri sağlayın** .

## <a name="prerequisites"></a>Prerequisites

- [.NET Core SDK 3,1 veya üzeri](https://dotnet.microsoft.com/download)
- [Mac için Visual Studio 2019](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)

Önkoşullar hakkında daha fazla bilgi için bkz. [.NET Core Dependencies ve gereksinimleri](../install/dependencies.md?pivots=os-macos). Mac için Visual Studio 2019 ' nin tüm sistem gereksinimleri için bkz. [Mac Için Visual studio 2019 ürün ailesi sistem gereksinimleri](/visualstudio/productinfo/vs2019-system-requirements-mac).

## <a name="building-a-library"></a>Kitaplık oluşturma

1. Başlangıç penceresinde **Yeni proje**' yi seçin. **.NET Core** düğümü altındaki **Yeni proje** iletişim kutusunda **.NET Standard kitaplığı** şablonunu seçin. Bu komut, .NET Core 'un yanı sıra [.NET Standard](../../standard/net-standard.md)sürüm 2,1 ' i destekleyen diğer .NET uygulamaları hedefleyen bir .NET Standard kitaplığı oluşturur. .NET Core SDK yüklü birden çok sürümü varsa, kitaplığınız için .NET Standard farklı sürümlerini seçebilirsiniz. ".NET Standard 2,1" öğesini seçin ve **İleri ' yi**seçin.

   > [!div class="mx-imgBorder"]
   > Yeni proje iletişim kutusunu Mac için Visual Studio ![](./media/using-on-mac-vs-full-solution/visual-studio-mac-new-project.png)

1. Projeyi "TextUtils" ("metin yardımcı programları" için kısa bir ad) ve "WordCounter" çözümünü adlandırın. **Çözüm dizini içinde bir proje dizini oluşturma** onay işaretli kalsın. Seçin **oluşturma**.

   > [!div class="mx-imgBorder"]
   > Yeni ![Mac için Visual Studio proje iletişim seçeneklerini](./media/using-on-mac-vs-full-solution/visual-studio-mac-new-project-options.png)

1. **Çözüm** panelinde, *Class1.cs*şablonu tarafından sunulan sınıf dosyasını açığa çıkarmak için `TextUtils` düğümünü genişletin. CTRL-dosyaya tıklayın, bağlam menüsünden **Yeniden Adlandır** ' ı seçin ve dosyayı *WORDCOUNT.cs*olarak yeniden adlandırın. Dosyasını açın ve içeriğini şu kodla değiştirin:

   [!code-csharp[Main](../../../samples/core/tutorials/using-on-mac-vs-full-solution/WordCounter/TextUtils/WordCount.cs)]

1. Üç farklı yöntemden birini kullanarak dosyayı kaydedin <kbd>&#8984;</kbd> :+<kbd>s</kbd>klavye kısayolunu kullanın, menüden **Dosya** > **Kaydet** ' i seçin veya dosya sekmesine CTRL tuşunu basılı tutarak bağlam menüsünden **Kaydet** ' i seçin. Aşağıdaki görüntüde IDE penceresi gösterilmektedir:

   > [!div class="mx-imgBorder"]
   > sınıf kitaplığı dosyası ve yöntemi ile Mac için Visual Studio IDE penceresi ![](./media/using-on-mac-vs-full-solution/visual-studio-mac-editor.png)

1. **Hatalar** panelini açmak için IDE penceresinin altındaki kenar boşluğunda bulunan **hataları** seçin. **Derleme çıkışı** düğmesini seçin.

   > [!div class="mx-imgBorder"]
   > Hatalar düğmesini gösteren Visual Studio Mac IDE 'nin alt kenar ![](./media/using-on-mac-vs-full-solution/visual-studio-mac-error-button.png)

1. Menüden **derleme** > **Oluştur** ' u seçin.

   Çözüm oluşturulur. Yapı çıktı paneli, yapılandırmanın başarılı olduğunu gösterir.

   > [!div class="mx-imgBorder"]
   > Hata bölmesinin Visual Studio Mac derleme çıkış bölmesi ![oluşturma başarılı iletisi](./media/using-on-mac-vs-full-solution/visual-studio-mac-build-panel.png)

## <a name="creating-a-test-project"></a>Test projesi oluşturma

Birim testleri geliştirme ve yayımlama sırasında otomatik yazılım testi sağlar. Bu öğreticide kullandığınız test çerçevesi, xUnit test projesi aşağıdaki adımlarda çözüme eklendiğinde otomatik olarak yüklenen [xUnit 'dir (sürüm 2.4.0 veya üzeri)](https://xunit.github.io/).

1. **Çözüm** kenar çubuğunda, `WordCounter` çözüme CTRL tuşunu basılı ve **Ekle** > **Yeni Proje Ekle**' yi seçin.

1. **Yeni proje** iletişim kutusunda, **.NET Core** düğümünden **testler** ' i seçin. Ardından **İleri**' ye tıklayarak **xUnit test projesini** seçin.

   > [!div class="mx-imgBorder"]
   > ![Visual Studio Mac yeni proje iletişim kutusu xUnit test projesi](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-project.png) oluşturuluyor

1. .NET Core SDK birden çok sürümüne sahipseniz, bu proje için sürümü seçmeniz gerekir. **.NET Core 3,1**' u seçin. "TestLibrary" adlı yeni projeyi adlandırın ve **Oluştur**' u seçin.

   > [!div class="mx-imgBorder"]
   > Visual Studio Mac ![proje adı](./media/using-on-mac-vs-full-solution/visual-studio-mac-new-project-name.png) sağlayan yeni proje iletişim kutusu

1. Test kitaplığının `WordCount` sınıfıyla çalışması için, `TextUtils` projesine bir başvuru ekleyin. **Çözüm** kenar çubuğunda, **Testlibrary**altında bulunan **Bağımlılıklar** ' a CTRL tuşuna tıklayın. Bağlam menüsünden **başvuruları Düzenle** ' yi seçin.

1. **Başvuruları Düzenle** iletişim kutusunda, **Projeler** sekmesinde **Textutils** projesini seçin. **Tamam**' ı seçin.

   > [!div class="mx-imgBorder"]
   > ![Visual Studio Mac başvuruları düzenleme iletişim kutusu](./media/using-on-mac-vs-full-solution/visual-studio-mac-edit-references.png)

1. **Testlibrary** projesinde, *UnitTest1.cs* dosyasını *TextUtilsTests.cs*olarak yeniden adlandırın.

1. Dosyasını açın ve kodu şu kodla değiştirin:

   ```csharp
   using Xunit;
   using TextUtils;
   using System.Diagnostics;

   namespace TestLibrary
   {
       public class TextUtils_GetWordCountShould
       {
           [Fact]
           public void IgnoreCasing()
           {
               var wordCount = WordCount.GetWordCount("Jack", "Jack jack");

               Assert.NotEqual(2, wordCount);
           }
       }
   }
   ```

   Aşağıdaki görüntüde birim test kodu yerine IDE gösterilmektedir. `Assert.NotEqual` bildirimine dikkat edin.

   > [!div class="mx-imgBorder"]
   > IDE ana penceresinde Ilk birim testi Mac için Visual Studio ![](./media/using-on-mac-vs-full-solution/visual-studio-mac-assert-test.png)

   Test mantığının doğru olduğundan emin olmak için yeni bir testin başarısız olması önemlidir. Yöntemi "jak" (büyük harf) ve "jak" ve "jak" (büyük ve küçük harf) ile bir dize ile geçer. `GetWordCount` yöntemi düzgün çalışıyorsa, Arama sözcüğünün iki örneğinin sayısını döndürür. Bu testi amaç doğrultusunda başarısız kılmak için, önce "jak" Arama sözcüğünün iki örneğinin `GetWordCount` yöntemi tarafından döndürülmeyeceğini belirten testi uygulamalısınız. Testi amaç üzerinde başarısız kılmak için sonraki adıma geçin.

1. Ekranın sağ tarafındaki **birim testleri** panelini açın. Menüden > **testlerini** **görüntüle** ' yi seçin.

   > [!div class="mx-imgBorder"]
   > ![Mac için Visual Studio birim testleri paneli](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-panel.png)

1. Paneli açık tutmak için **Yerleştir** simgesine tıklayın. (Aşağıdaki görüntüde vurgulanır.)

   > [!div class="mx-imgBorder"]
   > ![Mac için Visual Studio birim testleri bölmesi yerleştirme simgesi](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-dock-icon.png)

1. **Tümünü Çalıştır** düğmesine tıklayın.

   Test başarısız olur ve doğru sonuç olur. Test yöntemi, `GetWordCount` yöntemine sunulan "jak jakı" dizesinden `inputString`, "jak" öğesinin iki örneğinin döndürülmeyeceğini onaylar. Sözcük büyük harfleri `GetWordCount` yönteminde bir şekilde yayıldığından, iki örnek döndürülür. 2 ' nin 2 ' *ye eşit olmadığı* onay başarısız olur. Bu sonuç doğru sonuçadaydır ve testimizin mantığı iyidir.

   > [!div class="mx-imgBorder"]
   > ![Mac için Visual Studio test hatası görüntüleme](./media/using-on-mac-vs-full-solution/visual-studio-for-mac-unit-test-failure.png)

1. `IgnoreCasing` test yöntemini `Assert.Equal``Assert.NotEqual` değiştirerek değiştirin. <kbd>Ctrl</kbd>+<kbd>s</kbd>klavye kısayolunu kullanarak dosyayı kaydedin, menüden > Kaydet **'** i veya dosyanın sekmesine CTRL tuşunu basılı tutarak bağlam menüsünden **Kaydet** ' i seçin.

   `searchWord` "jak" `inputString` "jak jakı" `GetWordCount`geçirilmiş iki örnek döndürdüğünü düşünüyorsunuz. Ekranın alt kısmındaki **test sonuçları** panelinde, **birim testleri** panelinde **Testleri Çalıştır** düğmesine veya **Testleri** yeniden çalıştır düğmesine tıklayarak testi yeniden çalıştırın. Test başarılı olur. "Jak jakı" dizesinde iki "jak" örneği vardır (büyük/küçük harf yok sayılıyor) ve test onaylaması `true`.

   > [!div class="mx-imgBorder"]
   > ![Mac için Visual Studio Testleri görüntü geçişi](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-pass.png)

1. Tek tek dönüş değerlerini bir `Fact` test etmek yalnızca birim testinde yapabileceklerinizin başlangıcıdır. Başka bir güçlü teknik, `Theory`kullanarak birkaç değeri aynı anda test etmenizi sağlar. `TextUtils_GetWordCountShould` Sınıfınıza aşağıdaki yöntemi ekleyin. Bu yöntemi ekledikten sonra sınıfında iki yöntem vardır:

   ```csharp
   [Theory]
   [InlineData(0, "Ting", "Does not appear in the string.")]
   [InlineData(1, "Ting", "Ting appears once.")]
   [InlineData(2, "Ting", "Ting appears twice with Ting.")]
   public void CountInstancesCorrectly(int count,
                                       string searchWord,
                                       string inputString)
   {
       Assert.NotEqual(count, WordCount.GetWordCount(searchWord,
                                                  inputString));
   }
   ```

   `CountInstancesCorrectly`, `GetWordCount` yönteminin doğru şekilde sayımlarını denetler. `InlineData` bir sayı, bir arama sözcüğü ve denetlenecek bir giriş dizesi sağlar. Test yöntemi her veri satırı için bir kez çalışır. , Verilerdeki sayımların doğru olduğunu ve değerlerin `GetWordCount` yöntemi tarafından döndürülen sayılarla eşleştiğini bildiğiniz durumlarda bile, önce bir hatayı `Assert.NotEqual`kullanarak bir kez daha deneyin. Başarısız olma adımını gerçekleştirmek, ilk başta bir zaman kaybı gibi görünebilir, ancak testin mantığını başarısız olarak denetlemek öncelikle testlerin mantığına ilişkin önemli bir denetim olur. Başarısız olması beklendiğinde geçen bir test yöntemi boyunca aldığınızda testin mantığındaki bir hata buldunuz. Her test yöntemi oluşturduğunuzda bu adımı ele alma çabasına değecektir.

1. Dosyayı kaydedin ve testleri yeniden çalıştırın. Büyük/küçük harf testi geçer, ancak üç sayma testi başarısız olur. Bu sonuç, tam olarak ne olmasını beklediğiniz şeydir.

   > [!div class="mx-imgBorder"]
   > ![beklenen test hatası Mac için Visual Studio](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-failure.png)

1. `CountInstancesCorrectly` test yöntemini `Assert.Equal``Assert.NotEqual` değiştirerek değiştirin. Dosyayı kaydedin. Testleri yeniden çalıştırın. Tüm testler geçer.

   > [!div class="mx-imgBorder"]
   > ![beklenen test geçişleri Mac için Visual Studio](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-pass.png)

## <a name="adding-a-console-app"></a>Konsol uygulaması ekleme

1. **Çözüm** kenar çubuğunda `WordCounter` çözüme CTRL tuşunu basılı olarak tıklayın. **.NET Core** > **uygulama** şablonlarından şablonu seçerek yeni bir **konsol uygulama** projesi ekleyin. **İleri**’yi seçin. Projeyi **Wordcounterapp**olarak adlandırın. Projeyi çözümde oluşturmak için **Oluştur** ' u seçin.

1. **Çözümler** kenar çubuğunda, CTRL + yeni **wordcounterapp** projesinin **Bağımlılıklar** düğümüne tıklayın. **Başvuruları Düzenle** iletişim kutusunda, **textutils** ' i denetleyip **Tamam**' ı seçin.

1. *Program.cs* dosyasını açın. Kodu şu kodla değiştirin:

   [!code-csharp[Main](../../../samples/core/tutorials/using-on-mac-vs-full-solution/WordCounter/WordCounterApp/Program.cs)]

1. `WordCounterApp` projeye CTRL tuşunu basılı ve bağlam menüsünden **projeyi Çalıştır** ' ı seçin. Uygulamayı çalıştırdığınızda, konsol penceresindeki istemlerin sözcük ve giriş dizesi için değerler sağlayın. Uygulama, Arama sözcüğünün dizede kaç kez göründüğünü gösterir.

   > [!div class="mx-imgBorder"]
   > uygulamanızı çalıştıran](./media/using-on-mac-vs-full-solution/visual-studio-mac-console-window.png) ![Mac için Visual Studio konsol penceresi

1. Araştırılacak son özellik Mac için Visual Studio hata ayıklaması yapılır. `Console.WriteLine` bildiriminde bir kesme noktası ayarlayın: 23. satırın sol kenar boşluğunda seçim yapın ve kod satırının yanında kırmızı bir daire görünür. Alternatif olarak, kod satırında herhangi bir yeri seçin ve menüden **kesme noktası aç** > **Çalıştır** ' ı seçin.

   > [!div class="mx-imgBorder"]
   > ![Mac için Visual Studio kesme noktası ayarlandı](./media/using-on-mac-vs-full-solution/visual-studio-mac-breakpoint.png)

1. `WordCounterApp` projesine CTRL tuşuna tıklayın. Bağlam menüsünden **hata ayıklamayı Başlat** ' ı seçin. Uygulama çalıştığında, "Cat" sözcüğünü ve "kedi olan köpek, ancak Cat kaçışın." ifadesini girin. Aranacak dizenin. `Console.WriteLine` ifadeye ulaşıldığında, deyimin yürütülmesi için program yürütme durur. **Yereller** sekmesinde `searchWord`, `inputString`, `wordCount`ve `pluralChar` değerlerini görebilirsiniz.

   > [!div class="mx-imgBorder"]
   > ![Mac için Visual Studio hata ayıklayıcı program yürütme durdu](./media/using-on-mac-vs-full-solution/visual-studio-mac-debugger.png)

1. **Komut** bölmesinde, "WORDCOUNT = 999;" yazın ve ENTER tuşuna basın. Bu komut, hata ayıklama sırasında değişken değerlerini değiştirmenizi gösteren `wordCount` değişkenine 999 olmayan bir değer atar.

   > [!div class="mx-imgBorder"]
   > ![, komut penceresindeki değerleri değiştirme Mac için Visual Studio](./media/using-on-mac-vs-full-solution/visual-studio-mac-immediate-window.png)

1. Araç çubuğunda *devam* okuna tıklayın. Konsol penceresinde çıkışa bakın. Uygulamada hata ayıklarken ayarladığınız 999 yanlış değerini raporlar.

   > [!div class="mx-imgBorder"]
   > araç çubuğunda ![Mac için Visual Studio devam düğmesine](./media/using-on-mac-vs-full-solution/visual-studio-mac-toolbar.png)

   > [!div class="mx-imgBorder"]
   > ![Mac için Visual Studio konsol penceresi çıkışı](./media/using-on-mac-vs-full-solution/visual-studio-mac-output.png)

Birim testi projenizi kullanarak kodda hata ayıklamak için aynı işlemi kullanabilirsiniz. WordCount uygulama projesini başlatmak yerine, **test Kitaplığı** projesine CTRL tuşunu basılı ve bağlam menüsünde **proje hata ayıklamayı Başlat** ' ı seçin. Mac için Visual Studio, test projenizi ekli hata ayıklayıcı ile başlatır. Yürütme, test projesine eklediğiniz herhangi bir kesme noktasında veya temeldeki kitaplık kodunda durur.

## <a name="see-also"></a>Ayrıca bkz.

- [Mac için Visual Studio 2019 Sürüm Notları](/visualstudio/releasenotes/vs2019-mac-relnotes)
