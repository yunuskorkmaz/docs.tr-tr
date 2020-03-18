---
title: .NET Standart sınıf kitaplığını Visual Studio'da .NET Core ile test edin
description: .NET Core sınıf kitaplığınız için bir birim test projesi oluşturun. .NET Core sınıf kitaplığınızın birim testleriyle doğru çalıştığını doğrulayın.
ms.date: 12/24/2019
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet, seodoc18
ms.openlocfilehash: 307261088f5c7c69c0e69fbd6b99940c04842eec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156627"
---
# <a name="test-a-net-standard-library-with-net-core-in-visual-studio"></a>.NET Standart kitaplığını .NET Core ile Visual Studio'da test edin

[Visual Studio'da bir .NET Standart kitaplık oluşturun'da,](library-with-visual-studio.md) <xref:System.String> sınıfa uzantı yöntemi ekleyen basit bir sınıf kitaplığı oluşturdunuz. Şimdi, beklendiği gibi çalıştığından emin olmak için bir birim testi oluşturacaksınız. Birim test projenizi önceki makalede oluşturduğunuz çözüme eklersiniz.

## <a name="create-a-unit-test-project"></a>Birim testi projesi oluşturma

Birim test projesini oluşturmak için aşağıdakileri yapın:

1. Visual `ClassLibraryProjects` Studio makalesinde [Bir .NET Standart kitaplığı oluştur'da](library-with-visual-studio.md) oluşturduğunuz çözümü açın.

1. Çözüme "StringLibraryTest" adlı yeni bir birim test projesi ekleyin.

   1. **Solution Explorer'da** çözüme sağ tıklayın ve**Yeni proje** **Ekle'yi** > seçin.

   1. Yeni **bir proje ekle** sayfasında, arama kutusuna **mstest** girin. Dil listesinden **C#** veya **Visual Basic'i** seçin ve ardından Platform listesindeki **tüm platformları** seçin. **MsTest Test Project (.NET Core)** şablonunu seçin ve ardından **İleri'yi**seçin.

   1. Yeni **proje sayfanızı Yapılandır'da,** Project **ad** kutusuna **StringLibraryTest'i** girin. Ardından **Oluştur**’u seçin.

   > [!NOTE]
   > MSTest'e ek olarak Visual Studio'da .NET Core için xUnit ve nUnit test projeleri de oluşturabilirsiniz.

1. Visual Studio projeyi oluşturur ve kod penceresindeki sınıf dosyasını aşağıdaki kodla açar:

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

   Birim test şablonu tarafından oluşturulan kaynak kodu aşağıdakileri yapar:

   - Birim sınama <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> için kullanılan türleri içeren ad alanını içeri iter.

   - [TestClass](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) özniteliğini `UnitTest1` sınıfa uygular. [Test Yöntemi](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) özniteliği ile etiketlenmiş bir test sınıfındaki her test yöntemi, birim testi çalıştırıldığında otomatik olarak çalıştırılır.

   - Birim testi çalıştırıldığında otomatik yürütme `TestMethod1` için bir `TestSub` test yöntemi olarak C# veya Visual Basic'te tanımlamak için [TestYöntemi](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) özniteliğiuygular.

1. **Çözüm Gezgini'nde** **StringLibraryTest** projesinin **Bağımlılıklar** düğümüne sağ tıklayın ve bağlam menüsünden **Başvuru Ekle'yi** seçin.

   > [!div class="mx-imgBorder"]
   > ![StringLibraryTest bağımlılıkları bağlam menüsü](./media/testing-library-with-visual-studio/add-reference-context-menu.png)

1. Başvuru **Yöneticisi** iletişim kutusunda, **Projeler** düğüm'üne genişletin ve **StringLibrary'nin**yanındaki kutuyu işaretleyin. `StringLibrary` Derlemeye bir başvuru eklemek, derleyicinin **StringLibrary** yöntemlerini bulmasını sağlar. **Tamam** düğmesini seçin. Sınıf kitaplığı projenize bir `StringLibrary`başvuru eklenir.

   ![Visual Studio'da referans yöneticisi iletişim kutusu](./media/testing-library-with-visual-studio/project-reference-manager.png)

## <a name="add-and-run-unit-test-methods"></a>Birim test yöntemleri ekleme ve çalıştırma

Visual Studio bir birim testi çalıştırdığında, özniteliğin <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> uygulandığı sınıf <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> olan birim test sınıfında öznitelik ile işaretlenmiş her yöntemi yürütür. İlk hata bulunduğunda veya yöntemde bulunan tüm testler başarılı olduğunda bir test yöntemi sona erer.

En yaygın testler <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> sınıfın üyelerini çağırır. Birçok ileri alma yöntemi, biri beklenen test sonucu, diğeri gerçek test sonucu olmak üzere en az iki parametre içerir. `Assert` Sınıfın en sık çağrılan yöntemlerinden bazıları aşağıdaki tabloda gösterilmiştir:

| Öne koyma yöntemleri     | İşlev |
| ------------------ | -------- |
| `Assert.AreEqual`  | İki değerin veya nesnenin eşit olduğunu doğrular. Değerler veya nesneler eşit değilse, ileri deyiş başarısız olur. |
| `Assert.AreSame`   | İki nesne değişkeninin aynı nesneye atıfta bulunduğunu doğrular. Değişkenler farklı nesnelere başvuruyorsa, assert başarısız olur. |
| `Assert.IsFalse`   | Bir koşulun `false`. Koşul `true`. |
| `Assert.IsNotNull` | Nesnenin olmadığını `null`doğrular. Nesne `null`. |

Atması beklenen özel <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A> durum türünü belirtmek için yöntemi bir test yönteminde de kullanabilirsiniz. Belirtilen özel durum atılmıyorsa test başarısız olur.

`StringLibrary.StartsWithUpper` Yöntemi sınamak için, büyük harf karakteriyle başlayan bir dizi dize sağlamak istiyorsunuz. Bu gibi durumlarda `true` yöntemin dönmesini beklersiniz, <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A> böylece yöntemi arayabilirsiniz. Benzer şekilde, büyük harf karakteri dışında bir şeyle başlayan dizeleri bir dizi sağlamak istiyorum. Bu gibi durumlarda `false` yöntemin dönmesini beklersiniz, <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A> böylece yöntemi arayabilirsiniz.

Kitaplık yönteminiz dizeleri işlediğiiçin, boş bir [dizeyi ( )`String.Empty`,](xref:System.String.Empty)karakteri olmayan ve <xref:System.String.Length> 0 olan geçerli bir `null` dize ve baş harfe çevrilmiş bir dize yi başarıyla işlediğinden de emin olmak istersiniz. `StartsWithUpper` Bir <xref:System.String> örnekte uzantı yöntemi olarak adlandırılırsa, bir `null` dize geçirilemeyecek. Ancak, doğrudan statik bir yöntem olarak çağırabilir <xref:System.String> ve tek bir bağımsız değişken geçirebilirsiniz.

Dize dizisindeki her öğe için <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> tekrar tekrar bir yöntem çağıran üç yöntem tanımlarsınız. Test yöntemi ilk hatayı bulur bulmaz başarısız olduğundan, yöntem çağrısında kullanılan dize değerini gösteren bir dize yi geçmenizi sağlayan bir yöntem aşırı yüklemesi çağırırsınız.

Test yöntemlerini oluşturmak için:

1. *UnitTest1.cs* veya *UnitTest1.vb* kod penceresinde, kodu aşağıdaki kodla değiştirin:

   [!code-csharp[Test#1](~/samples/snippets/csharp/getting_started/with_visual_studio_2017/testlib1.cs)]
   [!code-vb[Test#1](~/samples/snippets/core/tutorials/vb-library-with-visual-studio/testlib.vb)]

   `TestStartsWithUpper` Yöntemdeki büyük harflerin testi, Yunan büyük harfi alfa (U+0391) ve Kiril büyük harfi EM 'yi (U+041C) içerir. `TestDoesNotStartWithUpper` Yöntemde küçük harflerin testi Yunanca küçük alfa harfi (U+03B1) ve Kiril küçük harf Ghe (U+0433) içerir.

1. Menü çubuğunda **Dosya** > **Kaydet UnitTest1.cs** veya **Dosya** > Yı**Kaydet BirimiTest1.vb As'ı**seçin. **Dosyayı Kaydet** iletişim kutusunda, **Kaydet** düğmesinin yanındaki oku seçin ve **Kodlama ile Kaydet'i**seçin.

   > [!div class="mx-imgBorder"]
   > ![Visual Studio Dosyayı İletişim Olarak Kaydet](./media/testing-library-with-visual-studio/save-file-as-dialog.png)

1. **Kaydet'i Doğrula** iletişim kutusunda, dosyayı kaydetmek için **Evet** düğmesini seçin.

1. Gelişmiş **Kaydet Seçenekleri** iletişim kutusunda, **Unicode'u (imzalı UTF-8) seçin -** **Kodlama** açılır listesinden Codepage 65001'i seçin ve **Tamam'ı**seçin.

   > [!div class="mx-imgBorder"]
   > ![Visual Studio Gelişmiş Kaydet Seçenekleri iletişim kutusu](./media/testing-library-with-visual-studio/advanced-save-options.png)

   Kaynak kodunuzu UTF8 kodlanmış bir dosya olarak kaydetmezseniz, Visual Studio dosyayı ASCII dosyası olarak kaydedebilir. Bu durumda, çalışma süresi ASCII aralığının dışındaki UTF8 karakterlerinin kodunu tam olarak çözmez ve test sonuçları doğru olmaz.

1. Menü çubuğunda,**Tüm Testleri** **Test** > **Edin'i** > seçin. **Test Gezgini** penceresi açılır ve testlerin başarılı bir şekilde çalıştırıldığını gösterir. Üç test **Geçti Testleri** bölümünde listelenir ve **Özet** bölümü test çalışmasının sonucunu bildirir.

   > [!div class="mx-imgBorder"]
   > ![Geçen testler ile Explorer'ı test edin penceresi](./media/testing-library-with-visual-studio/test-explorer-window.png)

## <a name="handle-test-failures"></a>Test hatalarını işleme

Test çalışmanızda hiçbir hata yoktu, ancak test yöntemlerinden birinin başarısız olması için biraz değiştirin:

1. "Hata" dizesini `words` `TestDoesNotStartWithUpper` içerecek şekilde yöntemdeki diziyi değiştirin. Visual Studio testleri çalıştırmak için bir çözüm oluşturulunca açık dosyaları otomatik olarak kaydettiğinden dosyayı kaydetmeniz gerekmez.

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

   ```vb
   Dim words() As String = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " }

   ```

1. Menü çubuğundan**Tüm Testleri** **Test** > **Edin'i** > seçerek testi çalıştırın. **Test Gezgini** penceresi, iki testin başarılı olduğunu ve birinin başarısız olduğunu gösterir.

   > [!div class="mx-imgBorder"]
   > ![Başarısız testler ile Explorer penceresi test](./media/testing-library-with-visual-studio/failed-test-window.png)

1. Başarısız testi `TestDoesNotStartWith`seçin. **Test Gezgini** penceresi assert tarafından üretilen iletiyi görüntüler: "Assert.IsFalse başarısız oldu. 'Hata' için beklenen: yanlış; gerçek: True". Hata nedeniyle, "Hata" sonra dizideki tüm dizeleri sınanmadı.

   > [!div class="mx-imgBorder"]
   > ![IsFalse savması hatasını gösteren Sınayış penceresi](./media/testing-library-with-visual-studio/failed-test-detail.png)

1. Adım 1'de yaptığınız değişikliği geri alave ve "Hata" dizesini kaldırın. Testi yeniden çalıştırın ve testler geçsin.

## <a name="test-the-release-version-of-the-library"></a>Kitaplığın Sürüm sürümünü sına

Testlerinizi kitaplığın Hata Ayıklama sürümüne karşı çalıştırDınız. Artık tüm testlerinizin tümü geçtiğine ve kitaplığınızı yeterince test ettiğinize göre, testleri kitaplığın Sürüm yapısına karşı ek bir süre çalıştırmanız gerekir. Derleyici optimizasyonları da dahil olmak üzere bir dizi etken bazen Hata Ayıklama ve Sürüm oluşturmaları arasında farklı davranışlar oluşturabilir.

Sürüm oluşturmatest etmek için:

1. Visual Studio araç çubuğunda, yapı yapılandırmasını **Hata Ayıklama'dan** **Sürüm'e**değiştirin.

   > [!div class="mx-imgBorder"]
   > ![Sürüm yapısı vurgulanmış Visual Studio araç çubuğu](./media/testing-library-with-visual-studio/visual-studio-toolbar-release.png)

1. **Çözüm Gezgini'nde** **StringLibrary** projesini sağ tıklatın ve kitaplığı yeniden derlemek için bağlam menüsünden **Oluştur'u** seçin.

   > [!div class="mx-imgBorder"]
   > ![Yapı komutu ile StringLibrary bağlam menüsü](./media/testing-library-with-visual-studio/build-library-context-menu.png)

1. Menü çubuğundan**Tüm Testleri** **Test** > **Çalıştır'ı** > seçerek birim testlerini çalıştırın. Testler geçiyor.

Kitaplığınızı test etmeyi tamamladığınızda, bir sonraki adım, kitaplığı arayanların kullanımına açmaktır. Bir veya daha fazla uygulamayla paketleyebilir veya NuGet paketi olarak dağıtabilirsiniz. Daha fazla bilgi için [bkz.](consuming-library-with-visual-studio.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Ünite test temelleri - Visual Studio](/visualstudio/test/unit-test-basics)
