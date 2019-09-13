---
title: Mac için Visual Studio kullanarak macOS’ta eksiksiz bir .NET Core çözümü derleme
description: Bu konuda, yeniden kullanılabilir bir kitaplık ve birim testi içeren bir .NET Core çözümü oluşturma işlemi adım adım açıklanmaktadır.
author: mairaw
ms.date: 06/12/2017
ms.custom: seodec18
ms.openlocfilehash: 46d118cc4dc54e34db0f964aa3f8d76f0ad67249
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70925991"
---
# <a name="building-a-complete-net-core-solution-on-macos-using-visual-studio-for-mac"></a>Mac için Visual Studio kullanarak macOS’ta eksiksiz bir .NET Core çözümü derleme

Mac için Visual Studio .NET Core uygulamaları geliştirmek için tam özellikli bir tümleşik geliştirme ortamı (IDE) sağlar. Bu konuda, yeniden kullanılabilir bir kitaplık ve birim testi içeren bir .NET Core çözümü oluşturma işlemi adım adım açıklanmaktadır.

Bu öğreticide, bir arama sözcüğünü ve kullanıcıdan bir metin dizesini kabul eden bir uygulama oluşturma, bir sınıf kitaplığındaki yöntemi kullanarak arama sözcüğünün dize içinde görünme sayısını saymakta ve sonucu kullanıcıya döndürmekte olduğunuz gösterilmektedir. Çözüm, birim testi kavramlarına giriş olarak sınıf kitaplığı için birim testi de içerir. Öğreticide bir bütün örnekle devam etmek isterseniz, [örnek çözümü](https://github.com/dotnet/samples/blob/master/core/tutorials/using-on-mac-vs-full-solution/WordCounter)indirin. İndirme yönergeleri için bkz. [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

> [!NOTE]
> Geri bildiriminiz çok değerli. Mac için Visual Studio üzerinde geliştirme ekibine geri bildirimde bulunmak için kullanabileceğiniz iki yol vardır:
>
> - Mac için Visual Studio, menüden**sorun bildir** veya hoş geldiniz ekranından **sorun** **bildir ' i seçerek** > bir hata raporu dosyalamayı sağlayan bir pencere açar. Geri bildiriminizi [Geliştirici Topluluğu](https://developercommunity.visualstudio.com/spaces/41/index.html) portalında izleyebilirsiniz.
> - Öneride bulunmak için, menüden**öneriler sağlama** veya hoş geldiniz ekranından [Mac için Visual Studio Geliştirici topluluğu Web sayfasına](https://developercommunity.visualstudio.com/content/idea/post.html?space=41)götüren **bir öneri** **sağlama ' yı seçin.**  > 

## <a name="prerequisites"></a>Önkoşullar

- OpenSSL (.NET Core 1,1 çalıştırıyorsanız): [Mac üzerinde .NET Core Için önkoşulları](../macos-prerequisites.md) konusuna bakın.
- [.NET Core SDK 1,1 veya üzeri](https://dotnet.microsoft.com/download)
- [Mac için Visual Studio 2017](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)

Önkoşullar hakkında daha fazla bilgi için bkz. [Mac üzerinde .NET Core önkoşulları](../macos-prerequisites.md). Mac için Visual Studio 2017 ' nin tüm sistem gereksinimleri için bkz. [Mac Için Visual studio 2017 ürün ailesi sistem gereksinimleri](/visualstudio/productinfo/vs2017-system-requirements-mac).

## <a name="building-a-library"></a>Kitaplık oluşturma

1. Hoş Geldiniz ekranında **Yeni proje**' yi seçin. **.NET Core** düğümü altındaki **Yeni proje** iletişim kutusunda **.NET Standard kitaplığı** şablonunu seçin. Bu, .NET Core 'un yanı sıra [.NET Standard](../../standard/net-standard.md)sürüm 2,0 ' i destekleyen diğer .NET uygulamaları hedefleyen bir .NET Standard kitaplığı oluşturur. **İleri**’yi seçin.

   ![Yeni proje iletişim kutusunu Mac için Visual Studio](./media/using-on-mac-vs-full-solution/visual-studio-mac-new-project.png)

1. Projeyi "TextUtils" ("metin yardımcı programları" için kısa bir ad) ve "WordCounter" çözümünü adlandırın. **Çözüm dizini içinde bir proje dizini oluşturma** onay işaretli kalsın. **Oluştur**’u seçin.

   ![Yeni proje iletişim kutusu seçeneklerini Mac için Visual Studio](./media/using-on-mac-vs-full-solution/visual-studio-mac-new-project-options.png)

1. **Çözüm** kenar çubuğunda, *Class1.cs*şablonu tarafından `TextUtils` sunulan sınıf dosyasını açığa çıkarmak için düğümünü genişletin. Dosyaya sağ tıklayın, bağlam menüsünden **Yeniden Adlandır** ' ı seçin ve dosyayı *WORDCOUNT.cs*olarak yeniden adlandırın. Dosyasını açın ve içeriğini şu kodla değiştirin:

   [!code-csharp[Main](../../../samples/core/tutorials/using-on-mac-vs-full-solution/WordCounter/TextUtils/WordCount.cs)]

1. <kbd>&#8984;</kbd> + <kbd>Şu</kbd>üç farklı yöntemden birini kullanarak dosyayı kaydedin: klavye kısayolunu kullanın, menüden **Dosya** > **Kaydet** ' i seçin veya dosyanın sekmesine sağ tıklayıp bağlamsal bilgisayardan **Kaydet** ' i seçin Menü. Aşağıdaki görüntüde IDE penceresi gösterilmektedir:

   ![Sınıf kitaplığı dosyası ve yöntemiyle IDE penceresi Mac için Visual Studio](./media/using-on-mac-vs-full-solution/visual-studio-mac-editor.png)

1. **Hatalar** panelini açmak için IDE penceresinin altındaki kenar boşluğunda bulunan **hataları** seçin. **Derleme çıkışı** düğmesini seçin.

   ![Visual Studio Mac IDE 'nin hatalar düğmesini gösteren alt kenar boşluğu](./media/using-on-mac-vs-full-solution/visual-studio-mac-error-button.png)

1. Menüden Build**Build All** **öğesini seçin.**  > 

   Çözüm oluşturulur. Yapı çıktı paneli, yapılandırmanın başarılı olduğunu gösterir.

   ![Derleme başarılı iletisi ile hatalar panelinin Visual Studio Mac derleme çıkış bölmesi](./media/using-on-mac-vs-full-solution/visual-studio-mac-build-panel.png)

## <a name="creating-a-test-project"></a>Test projesi oluşturma

Birim testleri geliştirme ve yayımlama sırasında otomatik yazılım testi sağlar. Bu öğreticide kullandığınız test çerçevesi, xUnit test projesi aşağıdaki adımlarda çözüme eklendiğinde otomatik olarak yüklenen [xUnit 'dir (sürüm 2.2.0 veya üzeri)](https://xunit.github.io/).

1. **Çözüm** kenar `WordCounter` çubuğunda çözüme sağ tıklayın ve Ekle**Yeni proje** **Ekle** > ' yi seçin.

1. **Yeni proje** iletişim kutusunda, **.NET Core** düğümünden **testler** ' i seçin. Ardından **İleri**' ye tıklayarak **xUnit test projesini** seçin.

   ![Visual Studio Mac yeni proje iletişim kutusu xUnit test projesi oluşturma](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-project.png)

1. "TestLibrary" adlı yeni projeyi adlandırın ve **Oluştur**' u seçin.

   ![Proje adı sağlayan Visual Studio Mac yeni proje iletişim kutusu](./media/using-on-mac-vs-full-solution/visual-studio-mac-new-project-name.png)

1. Test kitaplığının `WordCount` sınıfla çalışması için `TextUtils` projeye bir başvuru ekleyin. **Çözüm** kenar çubuğunda, **Testlibrary**altında **Bağımlılıklar** ' a sağ tıklayın. Bağlam menüsünden **başvuruları Düzenle** ' yi seçin.

1. **Başvuruları Düzenle** iletişim kutusunda, **Projeler** sekmesinde **textutils** projesini seçin. **Tamam**’ı seçin.

   ![Visual Studio Mac başvuruları Düzenle iletişim kutusu](./media/using-on-mac-vs-full-solution/visual-studio-mac-edit-references.png)

1. **Testlibrary** projesinde, *UnitTest1.cs* dosyasını *TextUtilsTests.cs*olarak yeniden adlandırın.

1. Dosyasını açın ve kodu aşağıdaki kodla değiştirin:

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

   Aşağıdaki görüntüde birim test kodu yerine IDE gösterilmektedir. `Assert.NotEqual` İfadeye dikkat edin.

   ![IDE ana penceresinde Ilk birim testini Mac için Visual Studio](./media/using-on-mac-vs-full-solution/visual-studio-mac-assert-test.png)

   Test mantığının doğru olduğundan emin olmak için yeni bir testin başarısız olması önemlidir. Yöntemi "jak" (büyük harf) ve "jak" ve "jak" (büyük ve küçük harf) ile bir dize ile geçer. `GetWordCount` Yöntem düzgün çalışıyorsa, Arama sözcüğünün iki örneğinin sayısını döndürür. Bu testi amacına uygun hale getirmek için ilk olarak, "jak" Arama sözcüğünün iki örneğinin `GetWordCount` yöntem tarafından döndürülmeyeceğini belirten testi uygulıyorsunuz. Testi amaç üzerinde başarısız kılmak için sonraki adıma geçin.

1. Ekranın sağ tarafındaki **birim testleri** panelini açın.

   ![Mac için Visual Studio birim testleri paneli](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-panel.png)

1. Paneli açık tutmak için **Yerleştir** simgesine tıklayın.

   ![Mac için Visual Studio birim testleri bölmesi yerleştirme simgesi](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-dock-icon.png)

1. **Tümünü Çalıştır** düğmesine tıklayın.

   Test başarısız olur ve doğru sonuç olur. Test yöntemi, "jak" öğesinin `inputString`iki örneğinin `GetWordCount` metoduna verilen "jak jakı" dizesinden döndürülmeyeceğini onaylar. Sözcük büyük harfleri `GetWordCount` yöntemde ayrı olduğundan, iki örnek döndürülür. 2 ' nin 2 ' *ye eşit olmadığı* onay başarısız olur. Bu doğru sonucudur ve testimizin mantığı iyidir.

   ![Test hatası görüntüleme Mac için Visual Studio](./media/using-on-mac-vs-full-solution/visual-studio-for-mac-unit-test-failure.png)

1. `Assert.NotEqual` Öğesini olarak `IgnoreCasing` değiştirerek`Assert.Equal`test yöntemini değiştirin. Klavye kısayolunu <kbd>&#8984;</kbd> +kullanarak dosyayı kaydedin, menüden **Dosya** > **Kaydet** <kbd>' i</kbd>veya dosyanın sekmesine sağ tıklayıp bağlam menüsünden **Kaydet** ' i seçin.

   `searchWord` "Jak" ın " `GetWordCount`jak jakı" ile birlikte `inputString` iki örnek döndürdüğünü düşünüyorsunuz. Ekranın alt kısmındaki **test sonuçları** panelinde, **birim testleri** panelinde **Testleri Çalıştır** düğmesine veya **Testleri** yeniden çalıştır düğmesine tıklayarak testi yeniden çalıştırın. Test başarılı olur. "Jak jakı" dizesinde iki "jak" örneği bulunur (büyük `true`/küçük harf yok sayılıyor) ve test onayı.

   ![Test geçiş görüntüsünü Mac için Visual Studio](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-pass.png)

1. Tek tek dönüş değerlerini bir `Fact` ile test etmek yalnızca birim testinde yapabileceklerinizin başlangıcıdır. Başka bir güçlü teknik, bir `Theory`kez kullanarak birkaç değeri test etmenizi sağlar. Sınıfınıza `TextUtils_GetWordCountShould` aşağıdaki yöntemi ekleyin. Bu yöntemi ekledikten sonra sınıfında iki yöntem vardır:

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

   , `CountInstancesCorrectly` `GetWordCount` Yöntemin doğru şekilde sayımlarını denetler. Bir sayı, bir arama sözcüğü ve denetlenecek bir giriş dizesi sağlar.`InlineData` Test yöntemi her veri satırı için bir kez çalışır. Veri içindeki sayımların doğru olduğunu ve değerlerin, `Assert.NotEqual` `GetWordCount` yöntemin döndürdüğü sayılarla eşleştiğini bildiğiniz durumlarda bile, önce bir hatayı bir kez daha deneyin. Başarısız olma adımını gerçekleştirmek, ilk başta bir zaman kaybı gibi görünebilir, ancak testin mantığını başarısız olarak denetlemek öncelikle testlerin mantığına ilişkin önemli bir denetim olur. Başarısız olması beklendiğinde geçen bir test yöntemi boyunca aldığınızda testin mantığındaki bir hata buldunuz. Her test yöntemi oluşturduğunuzda bu adımı ele alma çabasına değecektir.

1. Dosyayı kaydedin ve testleri yeniden çalıştırın. Büyük/küçük harf testi geçer, ancak üç sayma testi başarısız olur. Bu, tam olarak gerçekleşmesini beklediğiniz şeydir.

   ![Beklenen test hatası Mac için Visual Studio](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-failure.png)

1. `Assert.NotEqual` Öğesini olarak `CountInstancesCorrectly` değiştirerek`Assert.Equal`test yöntemini değiştirin. Dosyayı kaydedin. Testleri yeniden çalıştırın. Tüm testler geçer.

   ![Beklenen test geçişi Mac için Visual Studio](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-pass.png)

## <a name="adding-a-console-app"></a>Konsol uygulaması ekleme

1. **Çözüm** kenar çubuğunda `WordCounter` çözüme sağ tıklayın. **.NET Core** > **uygulama** şablonlarından şablonu seçerek yeni bir **konsol uygulama** projesi ekleyin. **İleri**’yi seçin. Projeyi **Wordcounterapp**olarak adlandırın. Projeyi çözümde oluşturmak için **Oluştur** ' u seçin.

1. **Çözümler** kenar çubuğunda, yeni **wordcounterapp** projesinin **Bağımlılıklar** düğümüne sağ tıklayın. **Başvuruları Düzenle** iletişim kutusunda, **textutils** ' i denetleyip **Tamam**' ı seçin.

1. *Program.cs* dosyasını açın. Kodu aşağıdaki kodla değiştirin:

   [!code-csharp[Main](../../../samples/core/tutorials/using-on-mac-vs-full-solution/WordCounter/WordCounterApp/Program.cs)]

1. Uygulamayı IDE yerine bir konsol penceresinde çalıştırmak `WordCounterApp` için projeye sağ tıklayın, **Seçenekler**' i seçin ve **varsayılan** düğümü **yapılandırma**bölümünde açın. **Dış konsolda Çalıştır**kutusunu işaretleyin. **Duraklatma konsolu çıkış** seçeneğini işaretli bırakın. Bu ayar, `Console.ReadLine` deyimler için giriş yazabileceğiniz şekilde uygulamanın bir konsol penceresinde oluşturulmasına neden olur. Uygulamayı IDE 'de çalıştırmak için bırakırsanız, yalnızca `Console.WriteLine` deyimlerin çıkışını görebilirsiniz. `Console.ReadLine`deyimler IDE 'nin **uygulama çıktısı** panelinde çalışmaz.

   ![Mac için Visual Studio projesi seçenekleri penceresi](./media/using-on-mac-vs-full-solution/visual-studio-mac-project-options.png)

1. Çözüm çalıştırıldığında Mac için Visual Studio geçerli sürümü testleri çalıştıramadığından, konsol uygulamasını doğrudan çalıştırırsınız. `WordCounterApp` Projeye sağ tıklayın ve bağlam menüsünden **öğeyi Çalıştır** ' ı seçin. Uygulamayı Play düğmesiyle çalıştırmayı denerseniz, Test Çalıştırıcısı ve uygulaması çalıştırılamaz. Bu sorunla ilgili işin durumu hakkında daha fazla bilgi için bkz. [xUnit/xamarinstudio. xUnit (#60)](https://github.com/xunit/xamarinstudio.xunit/issues/60). Uygulamayı çalıştırdığınızda, konsol penceresindeki istemlerin sözcük ve giriş dizesi için değerler sağlayın. Uygulama, Arama sözcüğünün dizede kaç kez göründüğünü gösterir.

   ![Uygulamanızın çalıştığını gösteren Mac için Visual Studio konsol penceresi](./media/using-on-mac-vs-full-solution/visual-studio-mac-console-window.png)

1. Araştırılacak son özellik Mac için Visual Studio hata ayıklaması yapılır. `Console.WriteLine` İfadede bir kesme noktası ayarlayın: 23. satırın sol kenar boşluğunda seçim yapın ve kod satırının yanında kırmızı bir daire görünür. Alternatif olarak, kod satırında herhangi bir yeri seçin ve menüden**geçiş kesme noktasını** **Çalıştır** > ' ı seçin.

   ![Mac için Visual Studio kesme noktası kümesi](./media/using-on-mac-vs-full-solution/visual-studio-mac-breakpoint.png)

1. `WordCounterApp` Projeye sağ tıklayın. Bağlam menüsünden **hata ayıklamayı Başlat öğesini** seçin. Uygulama çalıştığında, "Cat" sözcüğünü ve "kedi olan köpek, ancak Cat kaçışın." ifadesini girin. Aranacak dizenin. `Console.WriteLine` İfadeye ulaşıldığında, deyimin yürütülmesi için program yürütme durur. **Yereller** sekmesinde `searchWord`,,, ve `inputString` `pluralChar` değerlerini görebilirsiniz `wordCount`.

   ![Mac için Visual Studio hata ayıklayıcı program yürütmesi durdu](./media/using-on-mac-vs-full-solution/visual-studio-mac-debugger.png)

1. **Komut** bölmesinde, "WORDCOUNT = 999;" yazın ve ENTER tuşuna basın. Bu, `wordCount` hata ayıklama sırasında değişken değerlerini değiştirmenizi gösteren, değişkenine 999 olmayan bir değer atar.

   ![Mac için Visual Studio komut penceresindeki değerleri değiştirme](./media/using-on-mac-vs-full-solution/visual-studio-mac-immediate-window.png)

1. Araç çubuğunda *devam* okuna tıklayın. Konsol penceresinde çıkışa bakın. Uygulamada hata ayıklarken ayarladığınız 999 yanlış değerini raporlar.

   ![Araç çubuğundaki devam Mac için Visual Studio düğmesi](./media/using-on-mac-vs-full-solution/visual-studio-mac-toolbar.png)

   ![Mac için Visual Studio konsol penceresi çıkışı](./media/using-on-mac-vs-full-solution/visual-studio-mac-output.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Mac için Visual Studio 2017 sürüm notları](/visualstudio/releasenotes/vs2017-mac-relnotes)
