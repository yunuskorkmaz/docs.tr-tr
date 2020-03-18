---
title: Mac için Visual Studio'u kullanarak eksiksiz bir .NET Core çözümü oluşturun
description: Bu makale, yeniden kullanılabilir kitaplık ve birim testi içeren bir .NET Core çözümü oluşturmada size yol açabilirsiniz.
ms.date: 12/19/2019
ms.openlocfilehash: 8c9fcca404a3875b6bb7f9cf20551a017ff553c5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78239969"
---
# <a name="build-a-complete-net-core-solution-on-macos-using-visual-studio-for-mac"></a>Mac için Visual Studio'u kullanarak macOS'ta eksiksiz bir .NET Core çözümü oluşturun

Mac için Visual Studio, .NET Core uygulamalarını geliştirmek için tam özellikli entegre geliştirme ortamı (IDE) sağlar. Bu makale, yeniden kullanılabilir kitaplık ve birim testi içeren bir .NET Core çözümü oluşturmada size yol açabilirsiniz.

Bu öğretici, bir arama sözcüğü ve kullanıcıdan bir metin dizesini kabul eden bir uygulamanın nasıl oluşturulabileceğinizi, bir sınıf kitaplığındaki bir yöntemi kullanarak arama sözcüğünün dizede kaç kez göründüğünü sayar ve sonucu kullanıcıya döndürür. Çözüm, birim test kavramlarına giriş olarak sınıf kitaplığı için birim testini de içerir. Öğreticiye tam bir örnekle devam etmeyi tercih ederseniz, [örnek çözüme](https://github.com/dotnet/samples/blob/master/core/tutorials/using-on-mac-vs-full-solution/WordCounter)indirin. İndirme talimatları için [Örnekler ve Öğreticiler'e](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)bakın.

> [!NOTE]
> Geri bildiriminiz çok değerlidir. Mac için Visual Studio'daki geliştirme ekibine geri bildirim sağlamanın iki yolu vardır:
>
> - Mac için Visual Studio'da, menüden **Sorun Bildir'i** > veya hata raporu doldurmak için bir pencere açan Karşılama ekranından **Sorunu Bildir'i'ni** seçin.**Report a Problem** Geri bildiriminizi [Geliştirici Topluluğu](https://developercommunity.visualstudio.com/spaces/41/index.html) portalında izleyebilirsiniz.
> - Öneride bulunmak için menüden **Öneri Sağlama'ya Yardım Et'i** > **Provide a Suggestion** veya Sizi Mac Developer Community web sayfası için [Visual Studio'ya](https://developercommunity.visualstudio.com/content/idea/post.html?space=41)götüren Karşılama ekranından Bir **Öneri Sağlayın'ı** seçin.

## <a name="prerequisites"></a>Önkoşullar

- [.NET Core SDK 3.1 veya sonrası](https://dotnet.microsoft.com/download)
- [Mac için Visual Studio 2019](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)

Ön koşullar hakkında daha fazla bilgi için [.NET Çekirdek bağımlılıkları ve gereksinimlerine](../install/dependencies.md?pivots=os-macos)bakın. Mac için Visual Studio 2019'un tüm sistem gereksinimleri [için, Mac Ürün Aile Sistemi Gereksinimleri için Visual Studio 2019'a](/visualstudio/productinfo/vs2019-system-requirements-mac)bakın.

## <a name="building-a-library"></a>Kütüphane oluşturma

1. Başlangıç penceresinde Yeni **Proje'yi**seçin. **.NET Core** düğümü altındaki **Yeni Proje** iletişim kutusunda **.NET Standart Kitaplığı** şablonu'nu seçin. Bu komut, .NET Core'un yanı sıra [.NET Standard'ın](../../standard/net-standard.md)sürüm 2.1'ini destekleyen diğer .NET uygulamalarını hedefleyen bir .NET Standart kitaplığı oluşturur. .NET Core SDK'nın birden çok sürümü yüklüyse, kitaplığınız için .NET Standard'ın farklı sürümlerini seçebilirsiniz. ".NET Standart 2.1" ve **İleri'yi**seçin.

   > [!div class="mx-imgBorder"]
   > ![Mac Yeni proje iletişim kutusu için Visual Studio](./media/using-on-mac-vs-full-solution/visual-studio-mac-new-project.png)

1. Projeyi "TextUtils" ("Text Utilities" için kısa bir ad) ve "WordCounter" çözümlerini adlandırın. Sol **Çözüm dizininde bir proje dizini oluşturma** denetlenir. **Oluştur'u**seçin.

   > [!div class="mx-imgBorder"]
   > ![Mac Yeni proje iletişim seçenekleri için Visual Studio](./media/using-on-mac-vs-full-solution/visual-studio-mac-new-project-options.png)

1. **Çözüm** defterinde, şablon `TextUtils` tarafından sağlanan sınıf dosyasını ortaya çıkarmak için düğümü genişletin, *Class1.cs.* Ctrl-dosyayı tıklatın, bağlam menüsünden **Yeniden Adlandır'ı** seçin ve dosyayı *WordCount.cs.* Dosyayı açın ve içindekileri aşağıdaki kodla değiştirin:

   [!code-csharp[Main](../../../samples/snippets/core/tutorials/using-on-mac-vs-full-solution/csharp/TextUtils/WordCount.cs)]

1. Üç farklı yöntemden herhangi birini kullanarak dosyayı kaydedin: klavye kısayolu <kbd>&#8984;</kbd> + <kbd>s'</kbd>yi kullanın, menüden **Dosya** > **Kaydet'i** seçin veya dosyanın sekmesine ctrl-tıklayın ve bağlamsal menüden **Kaydet'i** seçin. Aşağıdaki resim IDE penceresini gösterir:

   > [!div class="mx-imgBorder"]
   > ![Sınıf kitaplığı dosyası ve yöntemi ile Mac IDE penceresi için Visual Studio](./media/using-on-mac-vs-full-solution/visual-studio-mac-editor.png)

1. **Hatalar** panelini açmak için IDE penceresinin altındaki kenar boşluğundaki **Hatalar'ı** seçin. Çıktı **Oluştur** düğmesini seçin.

   > [!div class="mx-imgBorder"]
   > ![Hatalar düğmesini gösteren Visual Studio Mac IDE'nin alt kenar boşluğu](./media/using-on-mac-vs-full-solution/visual-studio-mac-error-button.png)

1. Menüden **Yapı** > **Tümü'nü** oluştur'u seçin.

   Çözüm oluşturur. Yapı çıktı paneli, yapının başarılı olduğunu gösterir.

   > [!div class="mx-imgBorder"]
   > ![Visual Studio Mac Yapı çıkış bölmesi Hatalar paneli ile Başarılı İleti Oluştur](./media/using-on-mac-vs-full-solution/visual-studio-mac-build-panel.png)

## <a name="creating-a-test-project"></a>Test projesi oluşturma

Birim testleri geliştirme ve yayımlama sırasında otomatik yazılım testleri sağlar. Bu öğreticide kullandığınız test çerçevesi [xUnit (sürüm 2.4.0 veya sonraki)](https://xunit.github.io/)olup, xUnit test projesi aşağıdaki adımlarda çözüme eklendiğinde otomatik olarak yüklenir:

1. **Çözüm** kenar `WordCounter` çubuğunda, ctrl-çözüme tıklayın ve Yeni Proje **Ekle'yi** > **Add New Project**seçin.

1. Yeni **Proje** iletişim kutusunda,.NET **Core** düğümünden **Testler'i** seçin. **XUnit Test Project'i** ve ardından **Next'i**seçin.

   > [!div class="mx-imgBorder"]
   > ![Visual Studio Mac Yeni Proje iletişim kutusu oluşturma xUnit test projesi](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-project.png)

1. .NET Core SDK'nın birden çok sürümü varsa, bu projenin sürümünü seçmeniz gerekir. **.NET Core 3.1'i**seçin. Yeni projeye "TestLibrary" adını ve **Oluştur'u**seçin.

   > [!div class="mx-imgBorder"]
   > ![Proje adını sağlayan Visual Studio Mac Yeni Proje iletişim kutusu](./media/using-on-mac-vs-full-solution/visual-studio-mac-new-project-name.png)

1. Test kitaplığının `WordCount` sınıfla çalışması için `TextUtils` projeye bir başvuru ekleyin. **Çözüm** kenar çubuğunda, **TestLibrary**altında ctrl-click **Bağımlılıklar.** Bağlam menüsünden **Başvuruları Edit'i** seçin.

1. Başvuruları **Edit** iletişim kutusunda, **Projeler** sekmesindeki **TextUtils** projesini seçin. **Tamam'ı**seçin.

   > [!div class="mx-imgBorder"]
   > ![Visual Studio Mac Başvuruları Edit iletişim kutusu](./media/using-on-mac-vs-full-solution/visual-studio-mac-edit-references.png)

1. **TestLibrary** projesinde, *UnitTest1.cs* dosyayı *TextUtilsTests.cs*olarak yeniden adlandırın.

1. Dosyayı açın ve kodu aşağıdaki kodla değiştirin:

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

   Aşağıdaki resimde, birim test kodu yerinde olan IDE gösterilmektedir. Açıklamaya dikkat `Assert.NotEqual` edin.

   > [!div class="mx-imgBorder"]
   > ![IDE ana penceresinde Mac İlk birim testi için Visual Studio](./media/using-on-mac-vs-full-solution/visual-studio-mac-assert-test.png)

   Test mantığının doğru olduğunu doğrulamak için yeni bir testin başarısız olmasını sağlamak önemlidir. Yöntem adı "Jack" (büyük harf) ve "Jack" ve "jack" (büyük harf ve küçük harf) ile bir dize geçer. `GetWordCount` Yöntem düzgün çalışıyorsa, arama sözcüğünün iki örneğinin sayısını döndürür. Bu testi kasıtlı olarak başarısız etmek için, önce "Jack" arama sözcüğünün iki örneğinin `GetWordCount` yöntemle döndürülemediğini ileri sürerek testi uygularsınız. Testi kasıtlı olarak başarısız yapmak için bir sonraki adıma devam edin.

1. Ekranın sağ tarafındaki **Ünite Testleri** panelini açın. Menüden**Testleri** **Görüntüle'yi** > seçin.

   > [!div class="mx-imgBorder"]
   > ![Mac Birim Testleri paneli için Visual Studio](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-panel.png)

1. Paneli açık tutmak için **Dock** simgesini tıklatın. (Aşağıdaki resimde vurgulanmıştır.)

   > [!div class="mx-imgBorder"]
   > ![Mac Unit Tests panel dock simgesi için Visual Studio](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-dock-icon.png)

1. **Tümlerini Çalıştır** düğmesini tıklatın.

   Test başarısız olur, bu da doğru sonuçtur. Test yöntemi, "Jack"in iki `inputString`örneğinin `GetWordCount` yönteme sağlanan "Jack jack" dizesinden döndürülmediğini ileri sürmüştür. Sözcük kasası yöntemde çarpanlara tekli olarak eksitolduğundan, `GetWordCount` iki örnek döndürülür. 2'nin *2'ye eşit olmadığı* iddiası başarısız olur. Bu sonuç doğru sonuçtur ve testimizin mantığı iyidir.

   > [!div class="mx-imgBorder"]
   > ![Mac test hatası ekranı için Visual Studio](./media/using-on-mac-vs-full-solution/visual-studio-for-mac-unit-test-failure.png)

1. 'ye `IgnoreCasing` değiştirerek `Assert.NotEqual` `Assert.Equal`test yöntemini değiştirin Klavye kısayolu <kbd>Ctrl</kbd>+<kbd>s</kbd>, Menüden **Dosya** > **Kaydet** veya dosyanın sekmesine ctrl tıklayarak ve bağlam menüsünden Kaydet'i seçerek dosyayı **kaydedin.**

   "Jack"in `searchWord` "Jack jack" ile `inputString` iki örneği döndürmesini `GetWordCount`beklersiniz. **Ünite Testleri** panelindeki **Testleri Çalıştır** düğmesine veya ekranın altındaki Test **Sonuçları** panelindeki Testleri **Yeniden Çalıştır** düğmesine tıklayarak testi tekrar çalıştırın. Test geçer. "Jack jack" dizesinde iki "Jack" örneği vardır (kasayı yok sayma) ve test iddiası . `true`

   > [!div class="mx-imgBorder"]
   > ![Mac testleri için Visual Studio ekran geçmek](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-pass.png)

1. Tek tek dönüş `Fact` değerlerini a ile test etmek, birim testiile yapabileceklerinin yalnızca başlangıcıdır. Başka bir güçlü teknik kullanarak `Theory`aynı anda çeşitli değerleri test etmenizi sağlar. Sınıfınıza `TextUtils_GetWordCountShould` aşağıdaki yöntemi ekleyin. Bu yöntemi ekledikten sonra sınıfta iki yöntem var:

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

   Yöntemin `CountInstancesCorrectly` `GetWordCount` doğru sayıldığını denetler. Bir `InlineData` sayım, bir arama sözcüğü ve denetlemek için bir giriş dizesi sağlar. Test yöntemi, her veri satırı için bir kez çalışır. Verilerdeki sayıların doğru olduğunu ve değerlerin `Assert.NotEqual`yöntemtarafından döndürülen sayımlarla eşleşip eşleştirdiğini biliyor sanız bile, `GetWordCount` önce kullanarak bir hata iddia ettiğinizi bir kez daha unutmayın. Testi kasıtlı olarak başarısız etme adımını gerçekleştirmek ilk başta zaman kaybı gibi görünebilir, ancak önce başarısız olarak testin mantığını kontrol etmek, testlerinizin mantığı üzerinde önemli bir denetimdir. Başarısız olmasını beklediğiniz zaman geçen bir test yöntemiyle karşılaştığınızda, testin mantığında bir hata bulursunuz. Bir test yöntemi oluşturmak her zaman bu adımı atmak için çaba değer.

1. Dosyayı kaydedin ve testleri yeniden çalıştırın. Kasa testi geçer ancak üç sayım testi başarısız olursa. Bu sonuç tam olarak olmasını beklediğiniz şeydir.

   > [!div class="mx-imgBorder"]
   > ![Mac için Visual Studio beklenen test hatası](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-failure.png)

1. 'ye `CountInstancesCorrectly` değiştirerek `Assert.NotEqual` `Assert.Equal`test yöntemini değiştirin Dosyayı kaydedin. Testleri tekrar çalıştırın. Tüm testler geçer.

   > [!div class="mx-imgBorder"]
   > ![Mac için Visual Studio beklenen test geçer](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-pass.png)

## <a name="adding-a-console-app"></a>Konsol uygulaması ekleme

1. **Çözüm** kenar çubuğunda, `WordCounter` ctrl-çözüme tıklayın. **.NET Core** > **App** şablonlarından şablonu seçerek yeni bir **Konsol Uygulaması** projesi ekleyin. **Sonraki'ni**seçin. Proje **WordCounterApp**adı . Çözümde proje oluşturmak için **Oluştur'u** seçin.

1. **Çözümler** kenar çubuğunda, ctrl-yeni **WordCounterApp** projesinin **Bağımlılıklar** düğüm'üne tıklayın. Başvuruları **Edit** iletişim kutusunda **TextUtils'i** denetleyin ve **Tamam'ı**seçin.

1. *Program.cs* dosyasını açın. Kodu aşağıdaki kodla değiştirin:

   [!code-csharp[Main](../../../samples/snippets/core/tutorials/using-on-mac-vs-full-solution/csharp/WordCounterApp/Program.cs)]

1. `WordCounterApp` Ctrl-projeye tıklayın ve bağlam menüsünden **projeyi çalıştır'ı** seçin. Uygulamayı çalıştırdığınızda, konsol penceresindeki istemlerde arama sözcüğü ve giriş dizesi için değerler sağlayın. Uygulama, arama sözcüğünün dizede kaç kez göründüğünü gösterir.

   > [!div class="mx-imgBorder"]
   > ![Uygulamanızın çalıştığını gösteren Mac konsol penceresi için Visual Studio](./media/using-on-mac-vs-full-solution/visual-studio-mac-console-window.png)

1. Keşfetmek için son özelliği Mac için Visual Studio ile hata ayıklama olduğunu. Deyimüzerinde `Console.WriteLine` bir kesme noktası ayarlayın: Satır 23'ün sol kenar boşluğunda seçin ve kod satırının yanında kırmızı bir daire nin göründüğünü görürsünüz. Alternatif olarak, kod satırında herhangi bir yeri seçin ve menüden**Toggle Breakpoint'i** **çalıştır'ı** > seçin.

   > [!div class="mx-imgBorder"]
   > ![Mac kesme noktası seti için Visual Studio](./media/using-on-mac-vs-full-solution/visual-studio-mac-breakpoint.png)

1. `WordCounterApp` ctrl-projeyi tıklatın. Bağlam menüsünden **Hata Ayıklama Projesini Başlat'ı** seçin. Uygulama çalıştığında, "kedi" ve "Köpek kediyi kovaladı, ancak kedi kaçtı" arama sözcüğe girin. dize aramak için. İfadeye `Console.WriteLine` ulaşıldığında, deyim yürütülmeden önce program yürütme durdurulur. **Yereller** `searchWord`sekmesinde , `inputString`, `wordCount`ve `pluralChar` değerleri görebilirsiniz.

   > [!div class="mx-imgBorder"]
   > ![Mac hata ayıklama programı yürütme için Visual Studio durduruldu](./media/using-on-mac-vs-full-solution/visual-studio-mac-debugger.png)

1. **Hemen** bölmesinde "wordCount = 999;" yazın ve Enter tuşuna basın. Bu komut, hata ayıklama sırasında değişken `wordCount` değerlerini değiştirebileceğinizi gösteren değişkene 999'luk anlamsız bir değer atar.

   > [!div class="mx-imgBorder"]
   > ![Mac için Visual Studio hemen pencerede değerleri değiştiriyor](./media/using-on-mac-vs-full-solution/visual-studio-mac-immediate-window.png)

1. Araç çubuğunda *devam* ok'una tıklayın. Konsol penceresindeki çıkışa bak. Uygulamanın hata ayıklamasını yaparken ayarladığınız 999'un yanlış değerini bildirir.

   > [!div class="mx-imgBorder"]
   > ![Mac için Visual Studio araç çubuğunda devam düğmesine](./media/using-on-mac-vs-full-solution/visual-studio-mac-toolbar.png)

   > [!div class="mx-imgBorder"]
   > ![Mac konsol penceresi çıkışı için Visual Studio](./media/using-on-mac-vs-full-solution/visual-studio-mac-output.png)

Birim test projenizi kullanarak kodu hata ayıklamak için aynı işlemi kullanabilirsiniz. WordCount uygulama projesini başlatmak yerine, Ctrl-Test **Kitaplığı** projesini tıklatın ve bağlam menüsünden **Hata Ayıklama Projesini Başlat'ı** seçin. Mac için Visual Studio, test projenize hata ayıklama ile başlar. Yürütme, test projesine veya temel kitaplık koduna eklediğiniz herhangi bir kesme noktasında durur.

## <a name="see-also"></a>Ayrıca bkz.

- [Mac için Visual Studio 2019 Sürüm Notları](/visualstudio/releasenotes/vs2019-mac-relnotes)
