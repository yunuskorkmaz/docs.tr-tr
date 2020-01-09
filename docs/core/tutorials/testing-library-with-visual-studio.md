---
title: Visual Studio 'da .NET Core ile .NET Standard sınıf kitaplığı test etme
description: .NET Core sınıf kitaplığınız için bir birim testi projesi oluşturun. .NET Core sınıf kitaplığınızın birim testlerle düzgün çalıştığını doğrulayın.
ms.date: 12/24/2019
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet, seodoc18
ms.openlocfilehash: 3a4f25b0d250469102fdac6ee960e42b2d969aed
ms.sourcegitcommit: f8c36054eab877de4d40a705aacafa2552ce70e9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/31/2019
ms.locfileid: "75559584"
---
# <a name="test-a-net-standard-library-with-net-core-in-visual-studio"></a>Visual Studio 'da .NET Core ile .NET Standard kitaplığı test etme

[Visual Studio 'da .NET Standard kitaplığı oluşturma](library-with-visual-studio.md)bölümünde, <xref:System.String> sınıfına bir genişletme yöntemi ekleyen basit bir sınıf kitaplığı oluşturdunuz. Şimdi, beklendiği gibi çalıştığından emin olmak için bir birim testi oluşturacaksınız. Birim testi projenizi önceki makalede oluşturduğunuz çözüme ekleyeceksiniz.

## <a name="create-a-unit-test-project"></a>Birim testi projesi oluşturma

Birim testi projesi oluşturmak için aşağıdakileri yapın:

1. [Visual Studio 'da bir .NET Standard kitaplığı oluşturun](library-with-visual-studio.md) makalesindeki oluşturduğunuz `ClassLibraryProjects` çözümünü açın.

1. Çözüme "StringLibraryTest" adlı yeni bir birim test projesi ekleyin.

   1. **Çözüm Gezgini** çözüme sağ tıklayın ve > **Yeni proje** **Ekle** ' yi seçin.

   1. **Yeni Proje Ekle** sayfasında, arama kutusuna **MSTest** yazın. Dil **C#** listesinden seçin veya **Visual Basic** ve ardından platform listesinden **tüm platformlar** ' ı seçin. **MSTest test projesi (.NET Core)** şablonunu seçin ve ardından **İleri**' yi seçin.

   1. **Yeni projenizi yapılandırın** sayfasında, **Proje adı** kutusuna **stringlibrarytest** girin. Ardından **Oluştur**’u seçin.

   > [!NOTE]
   > Bir MSTest 'e ek olarak, Visual Studio 'da .NET Core için xUnit ve nUnit test projeleri de oluşturabilirsiniz.

1. Visual Studio projeyi oluşturur ve kod penceresinde sınıf dosyasını aşağıdaki kodla açar:

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

   - Birim testi için kullanılan türleri içeren <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> ad alanını içeri aktarır.

   - `UnitTest1` sınıfına [TestClass](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) özniteliğini uygular. [TestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) özniteliğiyle etiketlenmiş bir test sınıfındaki her test yöntemi, birim testi çalıştırıldığında otomatik olarak yürütülür.

   - Birim testi çalıştırıldığında otomatik yürütmeye yönelik bir test yöntemi olarak C# Visual Basic içinde `TestMethod1` veya `TestSub` tanımlamak Için [TestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) özniteliğini uygular.

1. **Çözüm Gezgini**, **stringlibrarytest** projesinin **Bağımlılıklar** düğümüne sağ tıklayın ve bağlam menüsünden **Başvuru Ekle** ' yi seçin.

   > [!div class="mx-imgBorder"]
   > StringLibraryTest bağımlılıklarının bağlam menüsünü ![](./media/testing-library-with-visual-studio/add-reference-context-menu.png)

1. **Başvuru Yöneticisi** iletişim kutusunda, **Projeler** düğümünü genişletin ve **StringLibrary**' ın yanındaki kutuyu işaretleyin. `StringLibrary` derlemesine bir başvuru eklemek derleyicinin **StringLibrary** yöntemlerini bulmasını sağlar. **Tamam** düğmesini seçin. `StringLibrary`sınıf kitaplığı projenize bir başvuru eklenir.

   ![Visual Studio 'da başvuru Yöneticisi iletişim kutusu](./media/testing-library-with-visual-studio/project-reference-manager.png)

## <a name="add-and-run-unit-test-methods"></a>Birim testi yöntemleri ekleme ve çalıştırma

Visual Studio bir birim testi çalıştırdığında, bir birim testi sınıfında <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> özniteliğiyle işaretlenmiş her bir yöntemi yürütür, bu sınıf, <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> özniteliği uygulandı. İlk hata bulunduğunda veya yöntemde bulunan tüm testler başarılı olduğunda bir test yöntemi sonlanır.

En yaygın testler <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> sınıfının üyelerini çağırır. Birçok onaylama yöntemi, biri beklenen test sonucu ve diğeri de gerçek test sonucu olan en az iki parametre içerir. `Assert` sınıfının en sık çağrılan yöntemlerin bazıları aşağıdaki tabloda gösterilmiştir:

| Onaylama yöntemleri     | İşlev |
| ------------------ | -------- |
| `Assert.AreEqual`  | İki değerin veya nesnenin eşit olduğunu doğrular. Değerler veya nesneler eşitse onaylama başarısız olur. |
| `Assert.AreSame`   | İki nesne değişkeninin aynı nesneye başvurmasını doğrular. Değişkenler farklı nesnelere başvuru yaptığında onaylama başarısız olur. |
| `Assert.IsFalse`   | Bir koşulun `false`olduğunu doğrular. Koşul `true`, onaylama başarısız olur. |
| `Assert.IsNotNull` | Bir nesnenin `null`olmadığını doğrular. Nesne `null`, onaylama başarısız olur. |

Ayrıca, oluşturması beklenen özel durum türünü belirtmek için bir test yönteminde <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A> yöntemini de kullanabilirsiniz. Belirtilen özel durum atılmazsa, test başarısız olur.

`StringLibrary.StartsWithUpper` yöntemini test ederken, büyük harfli bir karakterle başlayan bir dizi dize sağlamak istersiniz. Yöntemi bu durumlarda `true` döndürecek şekilde beklediğinizi, <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A> yöntemini çağırabilirsiniz. Benzer şekilde, büyük harfli bir karakter ile başlayan bir dizi dize sağlamak istersiniz. Yöntemi bu durumlarda `false` döndürecek şekilde beklediğinizi, <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A> yöntemini çağırabilirsiniz.

Kitaplık yönteminiz dizeleri yaptığından, ayrıca [boş bir dizeyi (`String.Empty`) başarılı bir şekilde ()](xref:System.String.Empty), hiçbir karakteri olmayan geçerli bir dizeyi ve <xref:System.String.Length> 0 olan `null` bir dizeyi başarıyla işlemesini sağlamak isteyeceksiniz. `StartsWithUpper` bir <xref:System.String> örneğinde uzantı yöntemi olarak çağrılırsa, `null` bir dize geçirilebilir. Ancak, bunu doğrudan statik bir yöntem olarak çağırabilir ve tek bir <xref:System.String> bağımsız değişkeni geçirebilirsiniz.

Her biri bir dize dizisindeki her öğe için sürekli olarak <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> yöntemi çağıran üç yöntem tanımlayacaksınız. İlk hatayı bulduğunda test yöntemi başarısız olduğundan, yöntem çağrısında kullanılan dize değerini gösteren bir dize geçirmenize izin veren bir yöntem aşırı yüklemesi çağıracaksınız.

Test yöntemleri oluşturmak için:

1. *UnitTest1.cs* veya *UnitTest1. vb* kodu penceresinde, kodu aşağıdaki kodla değiştirin:

   [!code-csharp[Test#1](~/samples/snippets/csharp/getting_started/with_visual_studio_2017/testlib1.cs)]
   [!code-vb[Test#1](~/samples/snippets/core/tutorials/vb-library-with-visual-studio/testlib.vb)]

   `TestStartsWithUpper` yönteminde büyük harfli karakterlerin testi, Yunanca Büyük Harf Alpha (U + 0391) ve Kiril Büyük harf EM (U + 041C) içerir. `TestDoesNotStartWithUpper` yönteminde küçük harfli karakterlerin testi, Yunanca Küçük Harf Alpha (U + 03B1) ve Kiril Küçük harf GHE (U + 0433) içerir.

1. Menü çubuğunda **Dosya** ' yı seçin > **UnitTest1.cs as** veya **Dosya** kaydet > **UnitTest1. vb dosyasını kaydedin**. **Dosyayı farklı kaydet** Iletişim kutusunda **Kaydet** düğmesinin yanındaki oku seçin ve **kodlamayla kaydet**' i seçin.

   > [!div class="mx-imgBorder"]
   > Visual Studio dosyayı farklı Kaydet iletişim kutusunu ![](./media/testing-library-with-visual-studio/save-file-as-dialog.png)

1. **Farklı kaydet** iletişim kutusunda, dosyayı kaydetmek için **Evet** düğmesini seçin.

1. **Gelişmiş kaydetme seçenekleri** iletişim kutusunda, **kodlama** açılan LISTESINDEN **Unicode (imzayla UTF-8)-kod sayfası 65001** ' i seçin ve **Tamam**' ı seçin.

   > [!div class="mx-imgBorder"]
   > Visual Studio Gelişmiş kaydetme seçenekleri iletişim ![](./media/testing-library-with-visual-studio/advanced-save-options.png)

   Kaynak kodunuzu UTF8 kodlu bir dosya olarak kaydedemeyebilirsiniz, Visual Studio bunu bir ASCII dosyası olarak kaydedebilir. Söz konusu olduğunda, çalışma zamanı, ASCII aralığının dışında UTF8 karakterlerinin kodunu doğru şekilde çözmez ve test sonuçları doğru olmayacaktır.

1. Menü çubuğunda **Test** > **Tüm testler** > **Çalıştır** ' ı seçin. **Test Gezgini** penceresi açılır ve testlerin başarıyla çalıştığını gösterir. **Geçen testler** bölümünde üç test listelenir ve **Özet** bölümü Test çalıştırmasının sonucunu raporlar.

   > [!div class="mx-imgBorder"]
   > testleri geçirerek test Gezgini penceresini ![](./media/testing-library-with-visual-studio/test-explorer-window.png)

## <a name="handle-test-failures"></a>Test başarısızlıklarını işle

Test çalıştırmasında hata yoktu, ancak test yöntemlerinden birinin başarısız olması için biraz değiştirin:

1. `TestDoesNotStartWithUpper` yönteminde `words` diziyi, "Error" dizesini içerecek şekilde değiştirin. Testleri çalıştırmak için bir çözüm oluşturulduğunda Visual Studio açık dosyaları otomatik olarak kaydettiği için dosyayı kaydetmeniz gerekmez.

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

   ```vb
   Dim words() As String = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " }

   ```

1. **Test > menü** çubuğundan **tüm testleri** > **Çalıştır** öğesini seçerek testi çalıştırın. **Test Gezgini** penceresi, iki testin başarılı olduğunu ve bir başarısız olduğunu gösterir.

   > [!div class="mx-imgBorder"]
   > Test Gezgini penceresini başarısız testlerle ![](./media/testing-library-with-visual-studio/failed-test-window.png)

1. Başarısız testi seçin, `TestDoesNotStartWith`. **Test Gezgini** penceresi onay tarafından oluşturulan iletiyi görüntüler: "onaylama. IsFalse başarısız oldu. ' Error ' bekleniyor: false; gerçek: true ". Hata nedeniyle "hata" sonunda dizideki tüm dizeler sınanmadı.

   > [!div class="mx-imgBorder"]
   > IsFalse onaylama başarısızlığını gösteren test Gezgini penceresi ![](./media/testing-library-with-visual-studio/failed-test-detail.png)

1. Adım 1 ' de yaptığınız değişikliği geri alın ve "hata" dizesini kaldırın. Testi yeniden çalıştırın ve testler geçer.

## <a name="test-the-release-version-of-the-library"></a>Kitaplığın yayın sürümünü test etme

Testlerinizi kitaplığın hata ayıklama sürümüne karşı çalıştırıyorsunuz. Artık testleriniz başarılı olduğuna ve kitaplığınızı yeterince test edinceye kadar, bu testleri kitaplığın yayın derlemesi için ek bir zaman çalıştırmalısınız. Derleyici iyileştirmeleri dahil olmak üzere bir dizi etken bazen hata ayıklama ve yayın yapıları arasında farklı davranışlar üretebilir.

Yayın derlemesini test etmek için:

1. Visual Studio araç çubuğunda, derleme yapılandırmasını **Debug** iken **Release**olarak değiştirin.

   > [!div class="mx-imgBorder"]
   > Yayın derlemesi vurgulanan Visual Studio araç çubuğunu ![](./media/testing-library-with-visual-studio/visual-studio-toolbar-release.png)

1. **Çözüm Gezgini**, **StringLibrary** projesine sağ tıklayın ve kitaplığı yeniden derlemek için bağlam menüsünden **Oluştur** ' u seçin.

   > [!div class="mx-imgBorder"]
   > Build komutuyla ![StringLibrary bağlam menüsü](./media/testing-library-with-visual-studio/build-library-context-menu.png)

1. **Test** > menü çubuğundan **tüm testleri** > **Çalıştır** öğesini seçerek birim testlerini çalıştırın. Testler geçer.

Artık kitaplığınızı test etmeyi tamamladığınıza göre, bir sonraki adım çağıranlar tarafından kullanılabilir hale gelir. Bunu bir veya daha fazla uygulamayla paketleyebilir veya bir NuGet paketi olarak dağıtabilirsiniz. Daha fazla bilgi için bkz. [.NET Standard sınıf kitaplığı](consuming-library-with-visual-studio.md)kullanma.

## <a name="see-also"></a>Ayrıca bkz.

- [Birim testi temelleri-Visual Studio](/visualstudio/test/unit-test-basics)
