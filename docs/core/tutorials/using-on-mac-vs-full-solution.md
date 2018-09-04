---
title: Mac için Visual Studio kullanarak macos'ta eksiksiz bir .NET Core çözümü derleme
description: Bu konuda, bir yeniden kullanılabilir bir kitaplık ve birim testi içeren bir .NET Core çözümü derleme açıklanmaktadır.
author: guardrex
ms.author: mairaw
ms.date: 06/12/2017
ms.openlocfilehash: 17d7cc5b085b4d47ebf1e5ed9a766be9d5d8b01f
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43457049"
---
# <a name="building-a-complete-net-core-solution-on-macos-using-visual-studio-for-mac"></a>Mac için Visual Studio kullanarak macos'ta eksiksiz bir .NET Core çözümü derleme

Mac için Visual Studio, .NET Core uygulamaları geliştirmek için bir tam özellikli tümleşik geliştirme ortamı (IDE) sağlar. Bu konuda, bir yeniden kullanılabilir bir kitaplık ve birim testi içeren bir .NET Core çözümü derleme açıklanmaktadır.

Bu öğreticide, bir arama sözcüğünü ve bir kullanıcının metin dizesini kabul eder, arama sözcüğünü sınıf kitaplığında bir yöntem kullanılarak dize görünür ve kullanıcıya sonucunu döndürür sayısını sayar bir uygulamanın nasıl oluşturulacağını gösterir. Çözüm ayrıca birim olarak birim testi kavramlarına giriş için sınıf kitaplığı testi içerir. Bu öğreticide eksiksiz bir örnek ile devam etmek isterseniz, indirme [örnek çözüm](https://github.com/dotnet/samples/blob/master/core/tutorials/using-on-mac-vs-full-solution/WordCounter). Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

> [!NOTE]
> Geri bildiriminiz çok değerli. Mac için Visual Studio geliştirme ekibine geri bildirim sağlayabilirsiniz iki yolu vardır:
> * Mac için Visual Studio'da **yardımcı** > **sorun bildir** menüsünden veya **sorun bildir** Karşılama ekranında, dosyalama için bir pencere açan bir hata raporu. Geri bildiriminizi [Geliştirici Topluluğu](https://developercommunity.visualstudio.com/spaces/41/index.html) portalında izleyebilirsiniz.
> * Bir öneride bulunmak için seçin **yardımcı** > **bir öneride** menüsünden veya **bir öneride** Karşılama ekranında, aldığı, için[ Visual Studio Mac UserVoice Web sayfası için](https://visualstudio.uservoice.com/forums/563332-visual-studio-for-mac).

## <a name="prerequisites"></a>Önkoşullar

- (.NET Core 1.1 çalıştırılıyorsa) OpenSSL: bkz [Mac üzerinde .NET Core önkoşulları](../macos-prerequisites.md) konu.
- [.NET core SDK 1.1 veya üzeri](https://www.microsoft.com/net/core#macos)
- [Mac için Visual Studio 2017](https://visualstudio.microsoft.com/vs/visual-studio-mac/)

Önkoşullar hakkında daha fazla bilgi için bkz. [Mac üzerinde .NET Core önkoşulları](../../core/macos-prerequisites.md). Tam Visual Studio 2017 için Mac için bkz: sistem gereksinimleri [Mac ürün ailesi sistem gereksinimleri için Visual Studio 2017](/visualstudio/productinfo/vs2017-system-requirements-mac).

## <a name="building-a-library"></a>Bir kitaplığı oluşturma

1. Hoş Geldiniz ekranında seçin **yeni proje**. İçinde **yeni proje** iletişim altında **çok platformlu** düğümünü **.NET Standard Kitaplığı** şablonu. Seçin **sonraki**.

   ![Yeni Proje iletişim kutusu](./media/using-on-mac-vs-full-solution/vsmacfull01.png)

1. "TextUtils" ("Metin yardımcı programlar" için bir kısa ad) Projeyi adlandırın ve ' % s'çözüm "WordCounter". Bırakın **dizini çözüm dizini içinde bir proje oluşturma** işaretli. Seçin **oluşturma**.

   ![Yeni Proje iletişim kutusu](./media/using-on-mac-vs-full-solution/vsmacfull02.png)

1. İçinde **çözüm** kenar genişletin `TextUtils` şablonu tarafından sağlanan sınıf dosyası açığa çıkarmak için düğüm *Class1.cs*. Dosyaya sağ tıklayın, **Yeniden Adlandır** bağlam menüsünden ve dosyayı yeniden adlandır *WordCount.cs*. Dosyayı açıp içeriğini aşağıdaki kodla değiştirin:

   [!code-csharp[Main](../../../samples/core/tutorials/using-on-mac-vs-full-solution/WordCounter/TextUtils/WordCount.cs)]

1. Üç farklı yöntemden birini kullanarak dosyayı kaydedin: klavye kısayolunu kullanın <kbd> &#8984; </kbd> + <kbd>s</kbd>seçin **dosya**  >  **Kaydet** menüsünden veya sağ tıklama dosyanın sekmesini ve seçim **Kaydet** bağlam menüsünde. Aşağıdaki görüntüde, IDE penceresi gösterilmektedir:

   ![IDE penceresi TextUtils gösteren sınıf kitaplığı, WordCount sınıf dosyası, statik sınıf WordCount ve GetWordCount yöntemi](./media/using-on-mac-vs-full-solution/vsmacfull03.png)

1. Seçin **hataları** IDE penceresi açmak için sayfanın alt kısmında kenar **hataları** paneli. Seçin **derleme çıkışı** düğmesi.

   ![Alt kenar boşluğu hataları düğmeyi gösteren IDE](./media/using-on-mac-vs-full-solution/vsmacfull03b.png)

1. Seçin **derleme** > **yapı tüm** menüsünde.

   Çözüm oluşturur. Derleme çıkışı paneline, yapının başarılı olduğunu gösterir.

   ![Çıkış Bölmesi'derleme başarılı iletisini gösteren hata panelinin derleme](./media/using-on-mac-vs-full-solution/vsmacfull04.png)

## <a name="creating-a-test-project"></a>Test projesi oluşturma

Birim testleri, geliştirme sırasında test etme ve yayımlama otomatikleştirilmiş yazılım sağlar. Bu öğreticide kullandığınız test çerçevesi [xUnit (2.2.0 sürümü veya üzeri)](https://xunit.github.io/), yüklendiği otomatik olarak aşağıdaki adımları çözümde xUnit test projesi eklendiğinde:

1. İçinde **çözüm** kenar sağ `WordCounter` çözüm ve select **Ekle** > **Yeni Proje Ekle**.

1. İçinde **yeni proje** iletişim kutusunda **testleri** gelen **.NET Core** düğümü. Seçin **xUnit Test projesi** ardından **sonraki**.

   ![Yeni Proje iletişim kutusu xUnit test projesi oluşturma](./media/using-on-mac-vs-full-solution/vsmacfull05.png)

1. Yeni projeyi "TestLibrary" olarak adlandırın ve seçin **Oluştur**.

   ![Proje adı sağlayarak yeni proje iletişim kutusu](./media/using-on-mac-vs-full-solution/vsmacfull06.png)

1. Çalışmak test kitaplığının sırayla `WordCount` sınıfı, bir başvuru ekleyin `TextUtils` proje. İçinde **çözüm** kenar sağ **bağımlılıkları** altında **TestLibrary**. Seçin **başvuruları Düzenle** bağlam menüsünden.

1. İçinde **başvuruları Düzenle** iletişim kutusunda **TextUtils** projesine **projeleri** sekmesi. Seçin **Tamam**.

   ![Başvurular iletişim Düzenle](./media/using-on-mac-vs-full-solution/vsmacfull07.png)

1. İçinde **TestLibrary** project, yeniden adlandırma *UnitTest1.cs* dosyasını *TextUtilsTests.cs*.

1. Dosyasını açın ve kodu aşağıdakiyle değiştirin:

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

   Aşağıdaki görüntüde, yerinde IDE ile birim testi kodu gösterir. Dikkat `Assert.NotEqual` deyimi.

   ![IDE ana pencerede GetWordCount denetlemek için ilk birim testi](./media/using-on-mac-vs-full-solution/vsmacfull08.png)

   Yeni bir test, test mantığının doğru olup olmadığını onaylamak bir kez başarısız hale getirmek önemlidir. Yöntem adı "Jack" (büyük harf) ve "Jack" ve "jack" olan bir dize (büyük ve küçük harf) geçirir. Varsa `GetWordCount` yöntemi düzgün çalıştığından, bir arama sözcüğünü iki örnek sayımı döndürür. Bu test amaç başarısız için ilk arama sözcüğünü "Jack" iki örneği tarafından döndürülen olmayan test sunduğundan uygulamanız `GetWordCount` yöntemi. Test amaç başarısız için sonraki adıma devam edin.

1. Açık **birim testleri** ekranın sağ tarafındaki paneli.

   ![Birim testleri paneli](./media/using-on-mac-vs-full-solution/vsmacfull_UnitTestPanel.png)

1. Tıklayın **Dock** simgesini panel açık tutun.

   ![Birim testleri paneli sabitlemek simgesi](./media/using-on-mac-vs-full-solution/vsmacfull_UnitTestPanelDockIcon.png)

1. Tıklayın **tümünü Çalıştır** düğmesi.

   Doğru sonuç, testi başarısız. Bu iki test yöntemi onaylar örneklerini `inputString`, olmayan "Jack" döndürülen ' % s'dizesinden "Jack jack sağlanan" `GetWordCount` yöntemi. Sözcük büyük/küçük harf out factored bu yana `GetWordCount` yöntemi, iki örneği döndürülür. Onaylama işlemi, 2 *eşit değildir* 2 başarısız olur. Bu doğru sonuç elde edilir ve bizim test mantığı iyidir.

   ![Test hatası](./media/using-on-mac-vs-full-solution/vsmacfull09.png)

1. Değiştirme `IgnoreCasing` test yöntemi değiştirerek `Assert.NotEqual` için `Assert.Equal`. Klavye kısayolunu kullanarak dosyayı kaydedin <kbd> &#8984; </kbd> + <kbd>s</kbd>, **dosya** > **Kaydet** menüsünden veya dosyanın sekmesinde sağ tıklayıp **Kaydet** bağlam menüsünden.

   Beklediğiniz `searchWord` "Jack" döndürür iki örneği ile `inputString` "Jack jack" geçirildi `GetWordCount`. Tıklayarak testi yeniden çalıştırın **çalıştırmak testlerini** düğmesine **birim testleri** paneli veya **yeniden çalıştırılan testleri** düğmesine **Test sonuçları** paneli ekranın alt kısmında. Test başarılı olur. "(Büyük/küçük harf yoksayar) Jack jack" dizesinde "Jack" iki örneği vardır ve test olaydır `true`.

   ![Test geçiş](./media/using-on-mac-vs-full-solution/vsmacfull10.png)

1. Tek tek dönüş değerleri ile test etme bir `Fact` birim testi ile neler yapabileceğinizi sadece başlangıç. Başka bir güçlü teknik değerlerden tek seferde kullanarak test etmenize olanak bir `Theory`. Aşağıdaki yöntemi ekleyin, `TextUtils_GetWordCountShould` sınıfı. Bu yöntem ekledikten sonra sınıfında iki yöntem vardır:

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

   `CountInstancesCorrectly` Denetleyen `GetWordCount` yöntemi doğru sayar. `InlineData` Sayısı, bir arama sözcüğünü ve denetlemek için bir Giriş dizesinin sağlar. Test yöntemi, her veri satırı için bir kez çalışır. Bir kez daha, bir hatanın ilk kullanarak sunduğundan olduğunu unutmayın. `Assert.NotEqual`, hatta veri sayılarını doğru olduğunu ve değerleri tarafından döndürülen sayıları eşleştiğini bildiğinizde `GetWordCount` yöntemi. İlk zaman kaybı gibi test amaç başarısız adımı gerçekleştiriliyor görünebilir, ancak mantıksal test başarısız olarak denetleme ilk testlerinizin mantığı üzerinde önemli bir denetleyin. Başarısız beklediğiniz geçirmeden bir test yöntemi arasında geldiğinizde, test mantığı bir hata buldunuz. Bu, bir test yöntemi her oluşturduğunuzda, bu adımı gerçekleştirmek için gereken çabayı olur.

1. Dosyayı kaydedin ve testleri yeniden çalıştırın. Büyük/küçük harf test geçer, ancak üç sayısı testler başarısız. Olmasını beklediğiniz tam olarak budur.

   ![Test hatası](./media/using-on-mac-vs-full-solution/vsmacfull11.png)

1. Değiştirme `CountInstancesCorrectly` test yöntemi değiştirerek `Assert.NotEqual` için `Assert.Equal`. Dosyayı kaydedin. Testleri yeniden çalıştırın. Tüm testler başarılı.

   ![Test geçiş](./media/using-on-mac-vs-full-solution/vsmacfull12.png)

## <a name="adding-a-console-app"></a>Bir konsol uygulaması ekleme

1. İçinde **çözüm** kenar sağ `WordCounter` çözüm. Yeni bir **konsol uygulaması** şablonu seçerek proje **.NET Core** > **uygulama** şablonları. Seçin **sonraki**. Projeyi adlandırın **WordCounterApp**. Seçin **Oluştur** çözümde proje oluşturmaktır.

1. İçinde **çözümleri** kenar sağ **bağımlılıkları** yeni düğüm **WordCounterApp** proje. İçinde **başvuruları Düzenle** iletişim kutusunda, onay **TextUtils** seçip **Tamam**.

1. Açık *Program.cs* dosya. Kodu aşağıdakiyle değiştirin:

   [!code-csharp[Main](../../../samples/core/tutorials/using-on-mac-vs-full-solution/WordCounter/WordCounterApp/Program.cs)]

1. IDE yerine bir konsol penceresi uygulamayı çalıştırmak için sağ `WordCounterApp` proje seçin **seçenekleri**açın **varsayılan** düğümünde **yapılandırmaları**. İçin kutuyu **harici konsol üzerinde Çalıştır**. Bırakın **konsol çıkışını duraklatmak** teslim seçeneği. Bu ayar için giriş türü, konsol penceresinde üretme uygulama neden `Console.ReadLine` deyimleri. IDE içinde çalıştırılacak uygulamanın değiştirmeden bırakırsanız, yalnızca çıktısını görebilirsiniz `Console.WriteLine` deyimleri. `Console.ReadLine` deyimleri, IDE'nin içinde çalışmıyor **uygulama çıktısı** paneli.

   ![Proje Seçenekleri penceresini](./media/using-on-mac-vs-full-solution/vsmacfull13.png)

1. Testleri Mac için Visual Studio'nun geçerli sürümü çalışamadığı çözümü çalıştırdığınızda, konsol uygulaması doğrudan çalıştırın. Sağ `WordCounterApp` seçin ve proje **öğesi çalıştırma** bağlam menüsünden. Uygulama ile Oynat düğmesini çalıştırmayı denerseniz, çalıştırmak test Çalıştırıcısı ve uygulamanın başarısız. Bu sorunla ilgili iş durumu hakkında daha fazla bilgi için bkz. [xunit/xamarinstudio.xunit (#60)](https://github.com/xunit/xamarinstudio.xunit/issues/60). Uygulamayı çalıştırdığınızda, konsol penceresinde istemleri giriş dizesini ve arama sözcüğünü için değerleri sağlayın. Uygulama arama sözcüğünü dizesinde görüntülenen sayısını gösterir.

   ![Konsol penceresinde sözcük Zeytin gösteren arama dizesinde 'Iro lake tarafından Zeytin oluştur ve Zeytin harika.' Uygulama yanıt veren, 'search word Zeytin 2 kez görünür.'](./media/using-on-mac-vs-full-solution/vsmacfull14.png)

1. Araştırılacak son özelliğini Mac için Visual Studio ile hata Bir kesme noktası ayarlamak `Console.WriteLine` deyimi: 23 satırının sol kenar boşluğunda seçin ve görünen kod satırının yanında kırmızı bir daire görürsünüz. Alternatif olarak, herhangi bir yeri seçin ve kod satırında seçin **çalıştırma** > **iki durumlu kesme noktası** menüsünde.

   ![Kesme noktası satır 23 Console.WriteLine deyimi ayarlanır](./media/using-on-mac-vs-full-solution/vsmacfull15.png)

1. Sağ `WordCounterApp` proje. Seçin **hata ayıklamayı Başlat öğesi** bağlam menüsünden. Uygulama çalıştırıldığında, arama sözcük "cat" ve "cat köpek aranır; cat kaçış" girin. arama dizesi için. Zaman `Console.WriteLine` deyimine ulaşıldığında, deyim yürütülmeden önce programın yürütülmesini durdurur. İçinde **Yereller** sekmesinde, gördüğünüz `searchWord`, `inputString`, `wordCount`, ve `pluralChar` değerleri.

   ![Program yürütme Console.WriteLine bildirimine hemen Console.WriteLine deyim yürütülmeden önce değerleri gösteren yerel penceresi ile durduruldu.](./media/using-on-mac-vs-full-solution/vsmacfull16.png)

1. İçinde **hemen** bölmesinde, türü "wordCount 999; =" ve Enter tuşuna basın. Bu 999 arasında anlamsız değeri atar `wordCount` değişkeni gösteren, hata ayıklama sırasında değişken değerlerini değiştirebilirsiniz.

   ![Bizim kesme noktasına ulaşılır. WordCount hemen penceresinde 999 arasında bir değere değiştirilir](./media/using-on-mac-vs-full-solution/vsmacfull17.png)

1. Araç çubuğunda *devam* oku. Konsol penceresinde çıktıyı inceleyin. Bu, uygulamanın hata ayıkladığınız zaman 999 yanlış değerini bildirir.

   ![Araç çubuğunda düğme devam](./media/using-on-mac-vs-full-solution/vsmacfull18.png)

   ![Arama sözcük sayısını uygulamanın çıkışında 999 arasında bir değere değiştirilir](./media/using-on-mac-vs-full-solution/vsmacfull19.png)

## <a name="see-also"></a>Ayrıca bkz.

* [Sürüm Notları Mac için Visual Studio 2017](/visualstudio/releasenotes/vs2017-mac-relnotes)
