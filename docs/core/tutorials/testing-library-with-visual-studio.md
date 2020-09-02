---
title: Visual Studio kullanarak .NET Core ile .NET Standard sınıf kitaplığı test etme
description: .NET Core sınıf kitaplığı için bir birim test projesi oluşturun. .NET Core sınıf kitaplığının birim testleriyle düzgün çalıştığını doğrulayın.
ms.date: 06/08/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 049f0636b1c2c2df33461714aea5a11810ef00ad
ms.sourcegitcommit: ae2e8a61a93c5cf3f0035c59e6b064fa2f812d14
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89359200"
---
# <a name="tutorial-test-a-net-standard-class-library-with-net-core-using-visual-studio"></a>Öğretici: Visual Studio kullanarak .NET Core ile .NET Standard sınıf kitaplığı test etme

Bu öğreticide, bir çözüme test projesi ekleyerek birim testinin nasıl otomatikleştirilmesi gösterilmektedir.

## <a name="prerequisites"></a>Ön koşullar

- Bu öğretici, [Visual Studio kullanarak .NET Standard kitaplığı oluşturma](library-with-visual-studio.md)bölümünde oluşturduğunuz çözümle birlikte kullanılır.

## <a name="create-a-unit-test-project"></a>Birim testi projesi oluşturma

Birim testleri geliştirme ve yayımlama sırasında otomatik yazılım testi sağlar. [MSTest](https://github.com/Microsoft/testfx-docs) , aralarından seçim yapabileceğiniz üç test çerçevelerinden biridir. Diğerleri [xUnit](https://xunit.net/) ve [NUnit](https://nunit.org/)' dir.

1. Visual Studio’yu çalıştırın.

1. `ClassLibraryProjects` [Visual Studio 'yu kullanarak .NET Standard kitaplığı oluşturma](library-with-visual-studio.md)bölümünde oluşturduğunuz çözümü açın.

1. Çözüme "StringLibraryTest" adlı yeni bir birim test projesi ekleyin.

   1. **Çözüm Gezgini** çözüme sağ tıklayın ve **Add**  >  **Yeni proje**Ekle ' yi seçin.

   1. **Yeni Proje Ekle** sayfasında, arama kutusuna **MSTest** yazın. Dil listesinden **C#** veya **Visual Basic** seçin ve ardından platform listesinden **tüm platformlar** ' ı seçin.

   1. **MSTest test projesi (.NET Core)** şablonunu seçin ve ardından **İleri**' yi seçin.

   1. **Yeni projenizi yapılandırın** sayfasında, **Proje adı** kutusuna **stringlibrarytest** girin. Ardından **Oluştur**’u seçin.

1. Visual Studio projeyi oluşturur ve kod penceresinde aşağıdaki kodla sınıf dosyasını açar. Kullanmak istediğiniz dil gösterilmiyorsa sayfanın en üstündeki dil seçicisini değiştirin.

   ```csharp
   using Microsoft.VisualStudio.TestTools.UnitTesting;

   namespace StringLibraryTest
   {
       [TestClass]
       public class UnitTest1
       {
           [TestMethod]
           public void TestMethod1()
           {
           }
       }
   }
   ```

   ```vb
   Imports Microsoft.VisualStudio.TestTools.UnitTesting

   Namespace StringLibraryTest
       <TestClass>
       Public Class UnitTest1
           <TestMethod>
           Sub TestSub()

           End Sub
       End Class
   End Namespace
   ```

   Birim testi şablonu tarafından oluşturulan kaynak kodu aşağıdakileri yapar:

   - <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType>Birim testi için kullanılan türleri içeren ad alanını içeri aktarır.
   - <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute>Özniteliği `UnitTest1` sınıfına uygular.
   - <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> `TestMethod1` C# veya Visual Basic içinde tanımlamak için özniteliğini uygular `TestSub` .

   [ [TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) ile etiketlenmiş bir test sınıfında [[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) etiketli her bir yöntem, birim testi çalıştırıldığında otomatik olarak yürütülür.

## <a name="add-a-project-reference"></a>Proje başvurusu Ekle

Test projesinin sınıfla çalışması için `StringLibrary` , **Stringlibrarytest** projesinde projeye bir başvuru ekleyin `StringLibrary` .

1. **Çözüm Gezgini**, **stringlibrarytest** projesinin **Bağımlılıklar** düğümüne sağ tıklayın ve bağlam menüsünden **proje başvurusu Ekle** ' yi seçin.

1. **Başvuru Yöneticisi** iletişim kutusunda, **Projeler** düğümünü genişletin ve **StringLibrary**' ın yanındaki kutuyu seçin. Derlemeye başvuru eklemek `StringLibrary` derleyicinin **Stringlibrarytest** projesini derlerken **StringLibrary** yöntemlerini bulmasını sağlar.

1. **Tamam**’ı seçin.

## <a name="add-and-run-unit-test-methods"></a>Birim testi yöntemleri ekleme ve çalıştırma

Visual Studio bir birim testi çalıştırdığında, özniteliğiyle <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> işaretlenmiş bir sınıfta özniteliğiyle işaretlenmiş her metodu yürütür  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> . İlk hata bulunduğunda veya yöntemde bulunan tüm testler başarılı olduğunda bir test yöntemi sonlanır.

En yaygın testler, sınıfının üyelerini çağırır <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> . Birçok onaylama yöntemi, biri beklenen test sonucu ve diğeri de gerçek test sonucu olan en az iki parametre içerir. `Assert`Sınıfın en sık çağrılan yöntemlerin bazıları aşağıdaki tabloda gösterilmiştir:

| Onaylama yöntemleri     | İşlev |
| ------------------ | -------- |
| `Assert.AreEqual`  | İki değerin veya nesnenin eşit olduğunu doğrular. Değerler veya nesneler eşitse onaylama başarısız olur. |
| `Assert.AreSame`   | İki nesne değişkeninin aynı nesneye başvurmasını doğrular. Değişkenler farklı nesnelere başvuru yaptığında onaylama başarısız olur. |
| `Assert.IsFalse`   | Bir koşulun olduğunu doğrular `false` . Koşul ise onaylama başarısız olur `true` . |
| `Assert.IsNotNull` | Bir nesnenin olmadığını doğrular `null` . Nesne ise onaylama başarısız olur `null` . |

<xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType>Yöntemi bir test yönteminde, oluşturması beklenen özel durum türünü belirtmek için de kullanabilirsiniz. Belirtilen özel durum atılmazsa, test başarısız olur.

Yöntemi test ederken `StringLibrary.StartsWithUpper` , büyük harf karakteriyle başlayan bir dizi dize sağlamak istersiniz. Yöntemi bu durumlarda Return olarak beklediğinizi ve `true` <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType> yöntemi çağırabilirsiniz. Benzer şekilde, büyük harfli bir karakter ile başlayan bir dizi dize sağlamak istersiniz. Yöntemi bu durumlarda Return olarak beklediğinizi ve `false` <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType> yöntemi çağırabilirsiniz.

Kitaplık yönteminiz dizeleri yaptığından, ayrıca [boş bir dizeyi ( `String.Empty` )](xref:System.String.Empty)başarılı bir şekilde (), karakteri olmayan ve 0 olan geçerli bir dize <xref:System.String.Length> ve başlatılmamış bir dize de işlemesini sağlamak istersiniz `null` . `StartsWithUpper`Doğrudan statik bir yöntem olarak çağırabilir ve tek bir <xref:System.String> bağımsız değişken geçirebilirsiniz. Ya da `StartsWithUpper` öğesine atanan bir değişkende bir genişletme yöntemi olarak çağırabilirsiniz `string` `null` .

Her biri <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> bir dize dizisindeki her öğe için bir yöntem çağıran üç yöntem tanımlayacaksınız. Test hatası durumunda görüntülenecek bir hata iletisi belirtmenize imkan tanıyan bir yöntem aşırı yüklemesi çağıracaksınız. İleti, hataya neden olan dizeyi tanımlar.

Test yöntemleri oluşturmak için:

1. *UnitTest1.cs* veya *UnitTest1. vb* kodu penceresinde, kodu aşağıdaki kodla değiştirin:

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibraryTest/UnitTest1.cs":::
   :::code language="vb" source="./snippets/library-with-visual-studio/vb/StringLibraryTest/UnitTest1.vb":::

   Yöntemdeki büyük harfli karakterlerin testi, `TestStartsWithUpper` Yunanca Büyük Harf Alpha (u + 0391) ve Kiril Büyük harf em (u + 041C) içerir. Yöntemdeki küçük harfli karakterlerin testi `TestDoesNotStartWithUpper` Yunanca Küçük Harf Alpha (u + 03B1) ve Kiril Küçük harf GHE (u + 0433) içerir.

1. Menü çubuğunda **Dosya**  >  **Kaydet UnitTest1.cs as** veya **Dosya**  >  **Kaydet UnitTest1. vb**' yi seçin. **Dosyayı farklı kaydet** Iletişim kutusunda **Kaydet** düğmesinin yanındaki oku seçin ve **kodlamayla kaydet**' i seçin.

   > [!div class="mx-imgBorder"]
   > ![Visual Studio dosyayı farklı Kaydet iletişim kutusu](./media/testing-library-with-visual-studio/save-file-as-dialog.png)

1. **Farklı kaydet** iletişim kutusunda, dosyayı kaydetmek için **Evet** düğmesini seçin.

1. **Gelişmiş kaydetme seçenekleri** iletişim kutusunda, **kodlama** açılan LISTESINDEN **Unicode (imzayla UTF-8)-kod sayfası 65001** ' i seçin ve **Tamam**' ı seçin.

   > [!div class="mx-imgBorder"]
   > ![Visual Studio Gelişmiş kaydetme seçenekleri iletişim kutusu](./media/testing-library-with-visual-studio/advanced-save-options.png)

   Kaynak kodunuzu UTF8 kodlu bir dosya olarak kaydedemeyebilirsiniz, Visual Studio bunu bir ASCII dosyası olarak kaydedebilir. Söz konusu olduğunda, çalışma zamanı, ASCII aralığının dışında UTF8 karakterlerinin kodunu doğru şekilde çözmez ve test sonuçları doğru olmayacaktır.

1. Menü çubuğunda, **Test**  >  **Çalıştır tüm testler**' i seçin. **Test Gezgini** penceresi açılmazsa **Test**  >  **Test Gezgini**' ni seçerek açın. **Geçen testler** bölümünde üç test listelenir ve **Özet** bölümü Test çalıştırmasının sonucunu raporlar.

   > [!div class="mx-imgBorder"]
   > ![Testleri geçirerek test Gezgini penceresi](./media/testing-library-with-visual-studio/test-explorer-window.png)

## <a name="handle-test-failures"></a>Test başarısızlıklarını işle

Test odaklı geliştirme (TDD) yapıyorsanız, önce testleri yazarsınız ve ilk kez çalıştırdığınızda başarısız olur. Sonra, uygulamayı başarılı hale getiren uygulamaya kod eklersiniz. Bu öğreticide, doğrulaması yaptığı uygulama kodunu yazdıktan sonra test başarısız olduğunu görmediyseniz testi oluşturdunuz. Başarısız olması beklendiğinde testin başarısız olduğunu doğrulamak için, test girişine geçersiz bir değer ekleyin.

1. `words`Yöntemdeki diziyi, `TestDoesNotStartWithUpper` "Error" dizesini içerecek şekilde değiştirin. Testleri çalıştırmak için bir çözüm oluşturulduğunda Visual Studio açık dosyaları otomatik olarak kaydettiği için dosyayı kaydetmeniz gerekmez.

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

   ```vb
   Dim words() As String = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " }

   ```

1. Test Çalıştır **Test**  >  **tüm testleri** menü çubuğundan Çalıştır öğesini seçerek testi çalıştırın. **Test Gezgini** penceresi, iki testin başarılı olduğunu ve bir başarısız olduğunu gösterir.

   > [!div class="mx-imgBorder"]
   > ![Başarısız testlerle test Gezgini penceresi](./media/testing-library-with-visual-studio/failed-test-window.png)

1. Başarısız testi seçin `TestDoesNotStartWith` .

   **Test Gezgini** penceresi onay tarafından oluşturulan iletiyi görüntüler: "onaylama. IsFalse başarısız oldu. ' Error ' bekleniyor: false; gerçek: true ". Hata nedeniyle "hata" sonunda dizide hiçbir dize sınanmadı.

   > [!div class="mx-imgBorder"]
   > ![IsFalse onaylama hatasını gösteren test Gezgini penceresi](./media/testing-library-with-visual-studio/failed-test-detail.png)

1. Adım 1 ' de eklediğiniz "Error" dizesini kaldırın. Testi ve test geçişini yeniden çalıştırın.

## <a name="test-the-release-version-of-the-library"></a>Kitaplığın yayın sürümünü test etme

Artık, kitaplığın hata ayıklama derlemesini çalıştırırken testlerin başarılı olduğuna göre, bu testleri kitaplığın yayın derlemesi için ek bir zaman çalıştırın. Derleyici iyileştirmeleri dahil olmak üzere bir dizi etken bazen hata ayıklama ve yayın yapıları arasında farklı davranışlar üretebilir.

Yayın derlemesini test etmek için:

1. Visual Studio araç çubuğunda, derleme yapılandırmasını **Debug** iken **Release**olarak değiştirin.

   > [!div class="mx-imgBorder"]
   > ![Yayın derlemesi vurgulanmış Visual Studio araç çubuğu](./media/testing-library-with-visual-studio/visual-studio-toolbar-release.png)

1. **Çözüm Gezgini**, **StringLibrary** projesine sağ tıklayın ve kitaplığı yeniden derlemek için bağlam menüsünden **Oluştur** ' u seçin.

   > [!div class="mx-imgBorder"]
   > ![Build komutuyla StringLibrary bağlam menüsü](./media/testing-library-with-visual-studio/build-library-context-menu.png)

1. **Test Run**  >  Menü çubuğundan**tüm testleri** Çalıştır test ' i seçerek birim testlerini çalıştırın. Testler geçer.

## <a name="additional-resources"></a>Ek kaynaklar

* [Birim testi temelleri-Visual Studio](/visualstudio/test/unit-test-basics)
* [.NET Core ve .NET Standard birim testi](../testing/index.md)

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, birim bir sınıf kitaplığı test edilmiştir. Bir paket olarak [NuGet](https://nuget.org) 'e yayımlayarak, kitaplığı başkaları için kullanılabilir hale getirebilirsiniz. Nasıl yapılacağını öğrenmek için bir NuGet öğreticisini izleyin:

> [!div class="nextstepaction"]
> [Visual Studio kullanarak bir NuGet paketi oluşturma ve yayımlama](/nuget/quickstart/create-and-publish-a-package-using-visual-studio?tabs=netcore-cli)

Bir kitaplığı bir NuGet paketi olarak yayımlarsanız, diğerleri onu yükleyebilir ve kullanabilir. Nasıl yapılacağını öğrenmek için bir NuGet öğreticisini izleyin:

> [!div class="nextstepaction"]
> [Visual Studio 'da paket yükleyip kullanma](/nuget/quickstart/install-and-use-a-package-in-visual-studio)

Bir kitaplığın paket olarak dağıtılması gerekmez. Onu kullanan bir konsol uygulamasıyla paketlenmiş olabilir. Bir konsol uygulamasını yayımlamayı öğrenmek için bu serideki önceki öğreticiye bakın:

> [!div class="nextstepaction"]
> [Visual Studio kullanarak bir .NET Core konsol uygulaması yayımlama](publishing-with-visual-studio.md)
