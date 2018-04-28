---
title: Mac için Visual Studio kullanarak macOS üzerinde tam bir .NET Core çözümü oluşturma
description: Bu konu, yeniden kullanılabilir kitaplık ve birim testleri içeren bir .NET Core çözümü oluşturma sürecinde açıklanmaktadır.
author: guardrex
ms.author: mairaw
ms.date: 06/12/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: 01b73fb3ec815440aaf6225f6e7c2894db3d24f2
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="building-a-complete-net-core-solution-on-macos-using-visual-studio-for-mac"></a>Mac için Visual Studio kullanarak macOS üzerinde tam bir .NET Core çözümü oluşturma

Mac için Visual Studio .NET Core uygulamaları geliştirmek için bir tam özellikli tümleşik geliştirme ortamı (IDE) sağlar. Bu konu, yeniden kullanılabilir kitaplık ve birim testleri içeren bir .NET Core çözümü oluşturma sürecinde açıklanmaktadır.

Bu öğretici, bir arama sözcüğü ve kullanıcıdan bir metin dizesi kabul eder, arama Word'ün bir sınıf kitaplığı'nda bir yöntem kullanarak dize görünür ve kullanıcıya sonucu döndürür sayısını sayar bir uygulama oluşturmak nasıl gösterir. Çözüm ayrıca birim teste dayalı geliştirme (TDD) kavramları giriş olarak için sınıf kitaplığı testi içerir. Bu öğreticiyi tam bir örnek üzerinden geçmek isterseniz, indirme [örnek çözümü](https://github.com/dotnet/samples/blob/master/core/tutorials/using-on-mac-vs-full-solution/WordCounter). Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

> [!NOTE]
> Geri bildiriminiz yüksek değerli. Mac için Visual Studio geliştirme ekibine geribildirim sağlayabilir iki yolu vardır:
> * Mac için Visual Studio'da seçin **yardımcı** > **bir sorun bildirmek** menüsünden veya **bir sorun bildirmek** Karşılama ekranında dosyalama için bir pencere açan bir hata raporu. Geri bildiriminizi [Geliştirici Topluluğu](https://developercommunity.visualstudio.com/spaces/41/index.html) portalında izleyebilirsiniz.
> * Bir öneride bulunmak için seçin **yardımcı** > **bir öneride bulunmak** menüsünden veya **bir öneride bulunmak** Karşılama ekranında aldığı, [ Visual Studio Web sayfası Mac UserVoice için](https://visualstudio.uservoice.com/forums/563332-visual-studio-for-mac).

## <a name="prerequisites"></a>Önkoşullar

- (.NET Core 1.1 çalıştırılıyorsa) OpenSSL: bkz [.NET Core Mac üzerinde önkoşulları](../macos-prerequisites.md) konu.
- [.NET core SDK 1.1 veya üstü](https://www.microsoft.com/net/core#macos)
- [Mac için Visual Studio 2017](https://www.visualstudio.com/vs/visual-studio-mac/)

Önkoşullar hakkında daha fazla bilgi için bkz: [.NET Core Mac üzerinde önkoşulları](../../core/macos-prerequisites.md). Tam sistem gereksinimlerini Visual Studio 2017 için Mac için bkz: [Mac ürün ailesi sistem gereksinimleri için Visual Studio 2017](/visualstudio/productinfo/vs2017-system-requirements-mac).

## <a name="building-a-library"></a>Bir kitaplığı oluşturma

1. Hoş Geldiniz ekranında seçin **yeni proje**. İçinde **yeni proje** altında iletişim **Multiplatform** düğümü, select **.NET standart Kitaplığı** şablonu. Seçin **sonraki**.

   ![Yeni Proje iletişim kutusu](./media/using-on-mac-vs-full-solution/vsmacfull01.png)

1. Proje adı "TextUtils" ("Metin yardımcı programlar" için kısa ad) ve "WordCounter" çözümü. Bırakın **çözüm dizini içinde proje dizin oluşturma** işaretli. Seçin **oluşturma**.

   ![Yeni Proje iletişim kutusu](./media/using-on-mac-vs-full-solution/vsmacfull02.png)

1. İçinde **çözüm** kenar genişletin `TextUtils` şablon tarafından sağlanan sınıf dosyası ortaya düğüme *Class1.cs*. Dosyaya sağ tıklayın, **yeniden adlandırma** ve bağlam menüsünden ve dosyayı yeniden adlandırın *WordCount.cs*. Dosyasını açın ve içeriğini aşağıdaki kodla değiştirin:

   [!code-csharp[Main](../../../samples/core/tutorials/using-on-mac-vs-full-solution/WordCounter/TextUtils/WordCount.cs)]

1. Üç farklı yöntemlerden birini kullanarak dosyayı kaydedin: klavye kısayolunu kullanın <kbd> &#8984; </kbd> + <kbd>s</kbd>seçin **dosya**  >  **Kaydetmek** menüsünden veya sağ tıklatın dosyanın sekmesi ve select **kaydetmek** bağlam menüsünde. Aşağıdaki resimde IDE penceresi gösterilir:

   ![IDE pencere TextUtils gösteren sınıf kitaplığı, WordCount sınıf dosyası, statik sınıf WordCount ve GetWordCount yöntemi](./media/using-on-mac-vs-full-solution/vsmacfull03.png)

1. Seçin **hataları** IDE penceresini ekranın alt kısmındaki kenar boşluğunda **hataları** paneli. Seçin **yapı çıktı** düğmesi.

   ![Alt kenar boşluğu hataları düğmesini gösteren IDE](./media/using-on-mac-vs-full-solution/vsmacfull03b.png)

1. Seçin **yapı** > **yapı tüm** menüsünde.

   Çözüm oluşturur. Derleme Çıktı paneli yapılandırmanın başarılı olduğunu gösterir.

   ![Çıkış Bölmesi'yapı başarılı iletisini gösteren hatalar panelinin derleme](./media/using-on-mac-vs-full-solution/vsmacfull04.png)

## <a name="creating-a-test-project"></a>Test projesi oluşturma

Birim testleri, geliştirme sırasında sınama ve yayımlama otomatik yazılım sağlar. Bu öğreticide kullandığınız test çerçevesi [xUnit (sürüm 2.2.0 veya sonraki)](https://xunit.github.io/), hangi otomatik olarak yüklenir aşağıdaki adımları çözümde xUnit test projesi eklenir:

1. İçinde **çözüm** kenar sağ `WordCounter` çözümü ve Seç **Ekle** > **Yeni Proje Ekle**.

1. İçinde **yeni proje** iletişim kutusunda **testleri** gelen **.NET Core** düğümü. Seçin **xUnit Test projesi** arkasından **sonraki**.

   ![Yeni Proje iletişim kutusu xUnit test projesi oluşturma](./media/using-on-mac-vs-full-solution/vsmacfull05.png)

1. Yeni Proje "TestLibrary" olarak adlandırın ve seçin **oluşturma**.

   ![Proje adı sağlayan yeni proje iletişim kutusu](./media/using-on-mac-vs-full-solution/vsmacfull06.png)

1. Çalışmak test kitaplığının sırayla `WordCount` sınıfı, bir başvuru ekleyin `TextUtils` projesi. İçinde **çözüm** kenar sağ **bağımlılıkları** altında **TestLibrary**. Seçin **Düzenle başvuruları** ve bağlam menüsünden.

1. İçinde **Düzenle başvuruları** iletişim kutusunda **TextUtils** üzerinde proje **projeleri** sekmesi. Seçin **Tamam**.

   ![Başvurular iletişim Düzenle](./media/using-on-mac-vs-full-solution/vsmacfull07.png)

1. İçinde **TestLibrary** projesi, yeniden adlandırma *UnitTest1.cs* dosya *TextUtilsTests.cs*.

1. Dosyasını açın ve kodu aşağıdakilerle değiştirin:

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

   Aşağıdaki resimde yerinde IDE birim test kodu ile gösterilmiştir. Dikkat `Assert.NotEqual` deyimi.

   ![IDE ana penceresinde GetWordCount denetlemek için ilk birim testi](./media/using-on-mac-vs-full-solution/vsmacfull08.png)

   TDD kullanarak, test mantığını doğru olduğunu doğrulamak bir kez başarısız yeni bir test olmak önemlidir. (Büyük ve küçük harf) adı "Prizine" (büyük harf) ve "Prizine" ve "prizine" dizesiyle yöntemi geçirir. Varsa `GetWordCount` yöntemi düzgün çalıştığından, arama word'ün iki örnek sayısını döndürür. Bu test başarısız amaç için önce arama Word'ün "Prizine" iki örneği tarafından döndürülen olmayan test sunduğundan uygulamanız `GetWordCount` yöntemi. Test amaç başarısız için sonraki adıma devam edin.

1. Açık **birim testleri** paneli ekranın sağ tarafında.

![Birim testleri paneli](./media/using-on-mac-vs-full-solution/vsmacfull_UnitTestPanel.png)

1. Tıklatın **yerleştirme** paneli açık tutmak için simge.

![Birim testleri panelini yerleştirme simgesi](./media/using-on-mac-vs-full-solution/vsmacfull_UnitTestPanelDockIcon.png)

1. Tıklatın **tümünü Çalıştır** düğmesi.
   
   Doğru sonuç olduğu test başarısız. Bu iki test yöntemini onaylar örneklerini `inputString`, "Prizine," değil "için sağlanan prizine prizine" dizesi sağlayıcıdan döndürülen `GetWordCount` yöntemi. Word büyük/küçük harf out oluşturmak bu yana `GetWordCount` yöntemi, iki örneği döndürülür. Onaylama işlemi, 2 *eşit değil* 2 başarısız olur. Bu doğru sonucu ve bizim test mantığı iyidir.

   ![Sınama hatası](./media/using-on-mac-vs-full-solution/vsmacfull09.png)

1. Değiştirme `IgnoreCasing` test yöntemi değiştirerek `Assert.NotEqual` için `Assert.Equal`. Klavye kısayolunu kullanarak dosyayı kaydedin <kbd> &#8984; </kbd> + <kbd>s</kbd>, **dosya** > **kaydetmek** menüsünde veya dosyanın sekmesinde sağ tıklayıp seçerek **kaydetmek** ve bağlam menüsünden.

   Beklediğiniz `searchWord` "Prizine" döndürür iki örnekleriyle `inputString` "Prizine prizine" geçirildi `GetWordCount`. Tıklayarak test yeniden çalıştırın **Testleri Çalıştır** düğmesini **birim testleri** Masası veya **yeniden çalıştır testleri** düğmesini **Test sonuçları** paneli ekranın alt kısmında. Test başarılı olur. "(Büyük/küçük harf yoksayar) prizine prizine" dizesindeki "Prizine" iki örneği vardır ve test onayı ifade eder `true`.

   ![Test geçişi](./media/using-on-mac-vs-full-solution/vsmacfull10.png)

1. Tek tek dönüş değerleri ile test etme bir `Fact` birim testi ile ne yapabileceğinizi sadece başlangıçtır. Başka bir güçlü teknik aynı anda kullanarak çeşitli değerleri test sayesinde bir `Theory`. Aşağıdaki yöntemi ekleyin, `TextUtils_GetWordCountShould` sınıfı. Bu yöntem ekledikten sonra sınıfında iki yöntem vardır:

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

   `CountInstancesCorrectly` Denetleyen `GetWordCount` yöntemi sayıları doğru. `InlineData` Bir sayısı, bir arama sözcüğü ve denetlemek için bir giriş dizesi sağlar. Test yöntemi, her veri satırı için bir kez çalışır. Bir kez daha, bir hata ilk kullanarak sunduğundan olduğunu unutmayın `Assert.NotEqual`, hatta veri sayıları doğru olduğunu ve tarafından döndürülen sayıları eşleşen değerleri bildiğinizde `GetWordCount` yöntemi. İlk zaman kaybı gibi test amaç başarısız adımı gerçekleştirmeden görünebilir, ancak ilk olup testlerinizi mantığını üzerinde önemli bir denetimi başarısız tarafından test mantığı olmadığı denetleniyor. Başarısız beklediğiniz geçirmeden bir test yöntemi geldiğinizde, bir hata test mantığında buldunuz. Bu bir test yöntemi her oluşturduğunuzda bu adımı için değer.
   
1. Dosyayı kaydedin ve testleri yeniden çalıştırın. Büyük/küçük harf test geçirir, ancak üç sayısı sınama başarısız. Bu, tam olarak gerçekleşecek şekilde beklediğiniz olur.

   ![Sınama hatası](./media/using-on-mac-vs-full-solution/vsmacfull11.png)

1. Değiştirme `CountInstancesCorrectly` test yöntemi değiştirerek `Assert.NotEqual` için `Assert.Equal`. Dosyayı kaydedin. Testleri yeniden çalıştırın. Tüm sınamaları geçmesi.

   ![Test geçişi](./media/using-on-mac-vs-full-solution/vsmacfull12.png)

## <a name="adding-a-console-app"></a>Bir konsol uygulaması ekleme

1. İçinde **çözüm** kenar sağ `WordCounter` çözümü. Yeni bir ekleme **konsol uygulaması** şablonu seçerek proje **.NET Core** > **uygulama** şablonları. Seçin **sonraki**. Proje adı **WordCounterApp**. Seçin **oluşturma** çözümde projesi oluşturmak için.

1. İçinde **çözümleri** kenar sağ **bağımlılıkları** yeni düğümü **WordCounterApp** proje. İçinde **Düzenle başvuruları** iletişim kutusunda, onay **TextUtils** seçip **Tamam**.

1. Açık *Program.cs* dosya. Kod aşağıdakiyle değiştirin:

   [!code-csharp[Main](../../../samples/core/tutorials/using-on-mac-vs-full-solution/WordCounter/WordCounterApp/Program.cs)]

1. IDE yerine bir konsol penceresinde uygulamayı çalıştırmak için sağ `WordCounterApp` proje, select **seçenekleri**ve açın **varsayılan** düğümü altında **yapılandırmaları**. Onay kutusunu için **dış konsolda çalıştırmak**. Bırakın **duraklatma konsol çıktısı** iade seçeneği. Bu ayar için giriş yazabilirsiniz böylece bir konsol penceresi oluşturma uygulama neden `Console.ReadLine` deyimleri. IDE içinde çalıştırmak için uygulamayı değiştirmeden bırakırsanız, yalnızca çıktısını görebilirsiniz `Console.WriteLine` deyimleri. `Console.ReadLine` deyimleri IDE'nin içinde çalışmıyor **uygulama çıktısı** paneli.

   ![Proje Seçenekleri penceresi](./media/using-on-mac-vs-full-solution/vsmacfull13.png)

1. Çözüm çalıştırdığınızda, Visual Studio Mac için geçerli sürümü testleri çalışamadığı konsol uygulaması doğrudan çalıştırın. Sağ `WordCounterApp` proje ve seçin **öğesi çalıştırmak** ve bağlam menüsünden. Uygulama ile YÜRÜT düğmesine çalıştırmayı denerseniz, çalıştırmak test Çalıştırıcısı ve uygulama başarısız. Bu sorunla ilgili iş durumu hakkında daha fazla bilgi için bkz: [xunit/xamarinstudio.xunit (#60)](https://github.com/xunit/xamarinstudio.xunit/issues/60). Uygulamayı çalıştırdığınızda, konsol penceresinde istemleri giriş dizesini ve arama word için değerler sağlayın. Uygulama arama sözcüğü dizesinde görünür sayısını gösterir.

   ![Konsol penceresi word Zeytin gösteren arama dizesinde 'Iro tarafından lake Zeytin tarih ve Zeytin harika.' Uygulama yanıt, 'arama word Zeytin 2 defa görünür.'](./media/using-on-mac-vs-full-solution/vsmacfull14.png)

1. Keşfetmek için son özelliğini Mac için hata Visual Studio ile ayıklama Bir kesme noktası ayarlayın `Console.WriteLine` deyimi: 23 satırının sol kenar boşluğunda seçin ve kod satırı yanındaki görünür kırmızı bir daire görürsünüz. Alternatif olarak, herhangi bir yere satırında seçin ve kodu seçin **çalıştırmak** > **kesme** menüsünde.

   ![Satır 23 Console.WriteLine deyimi kesme noktası ayarlama](./media/using-on-mac-vs-full-solution/vsmacfull15.png)

1. Sağ `WordCounterApp` projesi. Seçin **hata ayıklamayı Başlat öğesi** ve bağlam menüsünden. Uygulama çalıştırıldığında arama word "kat" ve "köpek kat aranır; kat kaçışlı" girin. Arama için dize. Zaman `Console.WriteLine` deyimi ulaşıldığında, program yürütme deyimi yürütülmeden önce durur. İçinde **Yereller** sekmesinde, gördüğünüz `searchWord`, `inputString`, `wordCount`, ve `pluralChar` değerleri.

   ![Program yürütme hemen Console.WriteLine deyimi yürütülmeden önce değerleri gösteren yerel penceresiyle Console.WriteLine ifadesine durduruldu.](./media/using-on-mac-vs-full-solution/vsmacfull16.png)

1. İçinde **hemen** bölmesi, türü "wordCount 999; =" ve Enter tuşuna basın. Bu 999 arasında anlamsız değeri atar `wordCount` değişkeni gösteren hata ayıklama sırasında değişken değerlerini değiştirebilirsiniz.

   ![Bizim kesme noktası isabet. WordCount hemen penceresinde 999 arasında bir değere değiştirilir](./media/using-on-mac-vs-full-solution/vsmacfull17.png)

1. Araç çubuğunda *devam* oku. Konsol penceresinde çıktı bakın. Uygulama hata ayıklaması ayarladığınız 999 yanlış değerini bildirir.

   ![Araç çubuğu düğmesi devam](./media/using-on-mac-vs-full-solution/vsmacfull18.png)

   ![Arama sözcük sayısını 999 uygulamanın çıktıda bir değere değiştirilir](./media/using-on-mac-vs-full-solution/vsmacfull19.png)

## <a name="see-also"></a>Ayrıca bkz.

[Visual Studio 2017 Mac sürüm notları](/visualstudio/releasenotes/vs2017-mac-relnotes)
