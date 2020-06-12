---
title: Mac için Visual Studio kullanarak .NET Core ile .NET Standard sınıf kitaplığı test etme
description: .NET Core sınıf kitaplığı için bir birim test projesi oluşturun. .NET Core sınıf kitaplığının birim testleriyle düzgün çalıştığını doğrulayın.
ms.date: 06/08/2020
ms.openlocfilehash: a183049623df44cbb8c4abd47ce6e78d91adae12
ms.sourcegitcommit: 1cbd77da54405ea7dba343ac0334fb03237d25d2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/11/2020
ms.locfileid: "84713611"
---
# <a name="test-a-net-standard-class-library-with-net-core-using-visual-studio"></a>Visual Studio kullanarak .NET Core ile .NET Standard sınıf kitaplığı test etme

Bu öğreticide, bir çözüme test projesi ekleyerek birim testinin nasıl otomatikleştirilmesi gösterilmektedir.

## <a name="prerequisites"></a>Önkoşullar

- Bu öğretici, [Mac için Visual Studio içinde .NET Standard kitaplığı oluşturma](library-with-visual-studio-mac.md)bölümünde oluşturduğunuz çözümle birlikte kullanılır.

## <a name="create-a-unit-test-project"></a>Birim testi projesi oluşturma

Birim testleri geliştirme ve yayımlama sırasında otomatik yazılım testi sağlar. [MSTest](https://github.com/Microsoft/testfx-docs) , aralarından seçim yapabileceğiniz üç test çerçevelerinden biridir. Diğerleri [xUnit](https://xunit.net/) ve [NUnit](https://nunit.org/)' dir.

1. Mac için Visual Studio başlatın.

1. `ClassLibraryProjects` [Mac için Visual Studio içinde .NET Standard kitaplığı oluşturma](library-with-visual-studio-mac.md)bölümünde oluşturduğunuz çözümü açın.

1. **Çözüm** panelinde, çözüme <kbd>CTRL</kbd>-tıklayın `ClassLibraryProjects` ve **Add**  >  **Yeni proje**Ekle ' yi seçin.

1. **Yeni proje** iletişim kutusunda, **Web ve konsol** düğümünden **testler** ' i seçin. **MSTest projesini** ve ardından Ileri ' **yi**seçin.

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-unit-test-project.png" alt-text="Visual Studio Mac yeni proje iletişim kutusu test projesi oluşturma":::

1. **.NET Core 3,1**' u seçin. "StringLibraryTest" adlı yeni projeyi adlandırın ve **Oluştur**' u seçin.

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-new-project-name.png" alt-text="Proje adı sağlayan Visual Studio Mac yeni proje iletişim kutusu":::

   Visual Studio aşağıdaki kodla bir sınıf dosyası oluşturur:

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

   Birim testi şablonu tarafından oluşturulan kaynak kodu aşağıdakileri yapar:

   - <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType>Birim testi için kullanılan türleri içeren ad alanını içeri aktarır.
   - <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute>Özniteliği `UnitTest1` sınıfına uygular.
   - <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute>Özniteliğini öğesine uygular `TestMethod1` .

   [ [TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) ile etiketlenmiş bir test sınıfında [[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) etiketli her bir yöntem, birim testi çalıştırıldığında otomatik olarak yürütülür.

## <a name="add-a-project-reference"></a>Proje başvurusu Ekle

Test projesinin sınıfla çalışması için `StringLibrary` projeye bir başvuru ekleyin `StringLibrary` .

1. **Çözüm** panelinde, **stringlibrarytest**altındaki **Bağımlılıklar** ' a <kbd>CTRL tuşuna</kbd>tıklayın. Bağlam menüsünden **Başvuru Ekle** ' yi seçin.

1. **Başvurular** Iletişim kutusunda **StringLibrary** projesini seçin. **Tamam**’ı seçin.

      :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-edit-references.png" alt-text="Visual Studio Mac başvuruları Düzenle iletişim kutusu":::

## <a name="add-and-run-unit-test-methods"></a>Birim testi yöntemleri ekleme ve çalıştırma

Visual Studio bir birim testi çalıştırdığında, özniteliğiyle <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> işaretlenmiş bir sınıfta özniteliğiyle işaretlenmiş her metodu yürütür <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> . İlk hata bulunduğunda veya yöntemde bulunan tüm testler başarılı olduğunda bir test yöntemi sonlanır.

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

1. *UnitTest1.cs* dosyasını açın ve kodu şu kodla değiştirin:

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibraryTest/UnitTest1.cs":::

   Yöntemdeki büyük harfli karakterlerin testi, `TestStartsWithUpper` Yunanca Büyük Harf Alpha (u + 0391) ve Kiril Büyük harf em (u + 041C) içerir. Yöntemdeki küçük harfli karakterlerin testi `TestDoesNotStartWithUpper` Yunanca Küçük Harf Alpha (u + 03B1) ve Kiril Küçük harf GHE (u + 0433) içerir.

1. Menü çubuğunda **Dosya**  >  **farklı kaydet**' i seçin. İletişim kutusunda, **kodlamanın** **UNICODE (UTF-8)** olarak ayarlandığından emin olun.

   :::image type="content" source="media/testing-library-with-visual-studio-mac/save-file-as-dialog.png" alt-text="Visual Studio dosyayı farklı Kaydet iletişim kutusu":::

1. Var olan dosyayı değiştirmek isteyip istemediğiniz sorulduğunda **Değiştir**' i seçin.

   Kaynak kodunuzu UTF8 kodlu bir dosya olarak kaydedemeyebilirsiniz, Visual Studio bunu bir ASCII dosyası olarak kaydedebilir. Söz konusu olduğunda, çalışma zamanı, ASCII aralığının dışında UTF8 karakterlerinin kodunu doğru şekilde çözmez ve test sonuçları doğru olmayacaktır.

1. Ekranın sağ tarafındaki **birim testleri** panelini açın. Menüden **View**  >  **Testleri** görüntüle ' yi seçin.

1. Paneli açık tutmak için **Yerleştir** simgesine tıklayın.

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-unit-test-dock-icon.png" alt-text="Mac için Visual Studio birim testleri bölmesi yerleştirme simgesi":::

1. **Tümünü Çalıştır** düğmesine tıklayın.

   Tüm testler geçer.

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-unit-test-pass.png" alt-text="Beklenen test geçişleri Mac için Visual Studio":::

## <a name="handle-test-failures"></a>Test başarısızlıklarını işle

Test odaklı geliştirme (TDD) yapıyorsanız, önce testleri yazarsınız ve ilk kez çalıştırdığınızda başarısız olur. Sonra, uygulamayı başarılı hale getiren uygulamaya kod eklersiniz. Bu öğreticide, doğrulaması yaptığı uygulama kodunu yazdıktan sonra test başarısız olduğunu görmediyseniz testi oluşturdunuz. Başarısız olması beklendiğinde testin başarısız olduğunu doğrulamak için, test girişine geçersiz bir değer ekleyin.

1. `words`Yöntemdeki diziyi, `TestDoesNotStartWithUpper` "Error" dizesini içerecek şekilde değiştirin. Testleri çalıştırmak için bir çözüm oluşturulduğunda Visual Studio açık dosyaları otomatik olarak kaydettiği için dosyayı kaydetmeniz gerekmez.

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

1. Testleri yeniden çalıştırın.

   Bu kez, **Test Gezgini** penceresi iki testin başarılı olduğunu ve bir başarısız olduğunu gösterir.

   :::image type="content" source="media/testing-library-with-visual-studio-mac/failed-test-window.png" alt-text="Başarısız testlerle test Gezgini penceresi":::

1. <kbd>CTRL tuşuna</kbd>basıp başarısız teste tıklayın `TestDoesNotStartWithUpper` ve bağlam menüsünden **sonuçlar panelini göster** ' i seçin.

   **Sonuç** panelinde, "onay. IsFalse başarısız oldu" onay tarafından oluşturulan ileti görüntülenir. ' Error ' bekleniyor: false; gerçek: true ". Hata nedeniyle "hata" sonunda dizide hiçbir dize sınanmadı.

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-unit-test-failure.png" alt-text="IsFalse onaylama hatasını gösteren test Gezgini penceresi":::

1. Adım 1 ' de eklediğiniz "Error" dizesini kaldırın. Testi ve test geçişini yeniden çalıştırın.

## <a name="test-the-release-version-of-the-library"></a>Kitaplığın yayın sürümünü test etme

Artık, kitaplığın hata ayıklama derlemesini çalıştırırken testlerin başarılı olduğuna göre, bu testleri kitaplığın yayın derlemesi için ek bir zaman çalıştırın. Derleyici iyileştirmeleri dahil olmak üzere bir dizi etken bazen hata ayıklama ve yayın yapıları arasında farklı davranışlar üretebilir.

Yayın derlemesini test etmek için:

1. Visual Studio araç çubuğunda, derleme yapılandırmasını **Debug** iken **Release**olarak değiştirin.

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-toolbar-release.png" alt-text="Yayın derlemesi vurgulanmış Visual Studio araç çubuğu":::

1. **Çözüm** panelinde, **StringLibrary** projesine <kbd>CTRL</kbd>-tıklayın ve bağlam menüsünden **Oluştur** ' u seçerek kitaplığı yeniden derleyin.

   :::image type="content" source="media/testing-library-with-visual-studio-mac/build-library-context-menu.png" alt-text="Build komutuyla StringLibrary bağlam menüsü":::

1. Birim testlerini yeniden çalıştırın.

   Testler geçer.

## <a name="debug-tests"></a>Hata ayıklama testleri

Öğreticide gösterilen aynı süreci kullanabilirsiniz: birim test projenizi kullanarak kodun hatalarını ayıklamak için [Mac için Visual Studio kullanarak bir .NET Core konsol uygulamasında hata ayıklayın](debugging-with-visual-studio-mac.md) . Gösterimi uygulama projesini başlatmak yerine **Stringlibrarytests** projesine <kbd>CTRL tuşunu basılı</kbd>ve bağlam menüsünde **proje hata ayıklamayı Başlat** ' ı seçin. Visual Studio, hata ayıklayıcı ekli olarak test projesi başlatır. Yürütme, test projesine veya temeldeki kitaplık koduna eklediğiniz herhangi bir kesme noktasında durur.

## <a name="additional-resources"></a>Ek kaynaklar

* [.NET Core ve .NET Standard birim testi](../testing/index.md)

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, birim bir sınıf kitaplığı test edilmiştir. Bir paket olarak [NuGet](https://nuget.org) 'e yayımlayarak, kitaplığı başkaları için kullanılabilir hale getirebilirsiniz. Nasıl yapılacağını öğrenmek için bir NuGet öğreticisini izleyin:

> [!div class="nextstepaction"]
> [Paket (dotnet CLI) oluşturma ve yayımlama](/nuget/quickstart/create-and-publish-a-package-using-the-dotnet-cli)

Bir kitaplığı bir NuGet paketi olarak yayımlarsanız, diğerleri onu yükleyebilir ve kullanabilir. Nasıl yapılacağını öğrenmek için bir NuGet öğreticisini izleyin:

> [!div class="nextstepaction"]
> [Mac için Visual Studio bir paketi yükleyip kullanma](/nuget/quickstart/install-and-use-a-package-in-visual-studio-mac)

Bir kitaplığın paket olarak dağıtılması gerekmez. Onu kullanan bir konsol uygulamasıyla paketlenmiş olabilir. Bir konsol uygulamasını yayımlamayı öğrenmek için bu serideki önceki öğreticiye bakın:

> [!div class="nextstepaction"]
> [Mac için Visual Studio bir .NET Core konsol uygulaması yayımlama](publishing-with-visual-studio-mac.md)
