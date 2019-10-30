---
title: Visual Studio 2017 ' de .NET Core ile .NET Standard sınıf kitaplığı test etme
description: .NET Core sınıf kitaplığınız için bir birim testi projesi oluşturun. .NET Core sınıf kitaplığınızın birim testlerle düzgün çalıştığını doğrulayın.
author: BillWagner
ms.author: wiwagn
ms.date: 08/07/2017
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet, seodoc18
ms.openlocfilehash: 242234d93bc1b8f9b88749f2e3bcfb37c2bde86d
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73037973"
---
# <a name="test-a-net-standard-library-with-net-core-in-visual-studio-2017"></a>Visual Studio 2017’de NET Core ile bir .NET Standard kitaplığını test etme

[Visual studio 2017 ' de ve C# .net Core Ile .NET Standard kitaplığı oluşturun](library-with-visual-studio.md) veya [visual Studio 2017 ' de Visual Basic ve .NET Core ile bir .NET Standard kitaplığı oluşturun](vb-library-with-visual-studio.md)@no__t_ bir genişletme yöntemi ekleyen basit bir sınıf kitaplığı oluşturdunuz 3_ sınıfı. Şimdi, beklendiği gibi çalıştığından emin olmak için bir birim testi oluşturacaksınız. Birim testi projenizi önceki makalede oluşturduğunuz çözüme ekleyeceksiniz.

## <a name="creating-a-unit-test-project"></a>Birim testi projesi oluşturma

Birim testi projesi oluşturmak için aşağıdakileri yapın:

<!-- markdownlint-disable MD025 -->

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. **Çözüm Gezgini**, **classlibraryprojects** çözüm düğümünün bağlam menüsünü açın ve > **Yeni proje** **Ekle** ' yi seçin.

1. **Yeni Proje Ekle** iletişim kutusunda  **C# görsel** düğümünü seçin. Ardından, **.NET Core** düğümünü ve ardından **MSTest test projesi (.NET Core)** proje şablonunu seçin. **Ad** metin kutusuna projenin adı olarak "StringLibraryTest" yazın. Birim testi projesini oluşturmak için **Tamam ' ı** seçin.

   ![Birim testi projesi görüntülenirken yeni proje iletişim kutusu Ekle-C#](./media/testing-library-with-visual-studio/create-new-test-project.png)

   > [!NOTE]  
   > Bir MSTest test projesine ek olarak, .NET Core için bir xUnit test projesi oluşturmak üzere Visual Studio 'Yu da kullanabilirsiniz.

1. Visual Studio projeyi oluşturur ve kod penceresinde *UnitTest1.cs* dosyasını açar.

   ![Birim testi proje sınıfı ve yöntemi için Visual Studio Code penceresi-C#](./media/testing-library-with-visual-studio/unit-test-editor-window.png)

   Birim testi şablonu tarafından oluşturulan kaynak kodu aşağıdakileri yapar:

   - Birim testi için kullanılan türleri içeren <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> ad alanını içeri aktarır.

   - `UnitTest1` sınıfına <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> özniteliğini uygular. \[TestMethod\] özniteliğiyle etiketlenmiş bir test sınıfındaki her test yöntemi, birim testi çalıştırıldığında otomatik olarak yürütülür.

   - Birim testi çalıştırıldığında otomatik yürütmeye yönelik bir test yöntemi olarak `TestMethod1` tanımlamak için <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> özniteliğini uygular.

1. **Çözüm Gezgini**, **stringlibrarytest** projesinin **Bağımlılıklar** düğümüne sağ tıklayın ve bağlam menüsünden **Başvuru Ekle** ' yi seçin.

   ![StringLibraryTest bağımlılıklarının bağlam menüsü-C#](./media/testing-library-with-visual-studio/add-reference-context-menu.png)

1. **Başvuru Yöneticisi** iletişim kutusunda, **Projeler** düğümünü genişletin ve **StringLibrary**' ın yanındaki kutuyu işaretleyin. `StringLibrary` derlemesine bir başvuru eklemek derleyicinin **StringLibrary** yöntemlerini bulmasını sağlar. **Tamam** düğmesini seçin. Bu, `StringLibrary`sınıf kitaplığı projenize bir başvuru ekler.

   ![Visual Studio proje başvurusu ekleme iletişim kutusu](./media/testing-library-with-visual-studio/project-reference-manager.png)

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. **Çözüm Gezgini**, **classlibraryprojects** çözüm düğümünün bağlam menüsünü açın ve > **Yeni proje** **Ekle** ' yi seçin.

1. **Yeni Proje Ekle** iletişim kutusunda **Visual Basic** düğümünü seçin. Ardından, **.NET Core** düğümünü ve ardından **MSTest test projesi (.NET Core)** proje şablonunu seçin. **Ad** metin kutusuna projenin adı olarak "StringLibraryTest" yazın. Birim testi projesini oluşturmak için **Tamam ' ı** seçin.

   ![Birim testi projesi görüntülenirken yeni proje iletişim kutusu Ekle-Visual Basic](./media/testing-library-with-visual-studio/vb-create-new-test-project.png)

   > [!NOTE]  
   > Bir MSTest test projesine ek olarak, .NET Core için bir xUnit test projesi oluşturmak üzere Visual Studio 'Yu da kullanabilirsiniz.

1. Visual Studio projeyi oluşturur ve kod penceresinde *UnitTest1. vb* dosyasını açar.

   ![Birim testi proje sınıfı ve yöntemi için Visual Studio Code penceresi-Visual Basic](./media/testing-library-with-visual-studio/vb-unit-test-editor-window.png)

   Birim testi şablonu tarafından oluşturulan kaynak kodu aşağıdakileri yapar:

   - Birim testi için kullanılan türleri içeren <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> ad alanını içeri aktarır.

   - `UnitTest1` sınıfına <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> özniteliğini uygular. <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> özniteliğiyle etiketlenmiş bir test sınıfındaki her test yöntemi, birim testi çalıştırıldığında otomatik olarak yürütülür.

   - Birim testi çalıştırıldığında otomatik yürütmeye yönelik bir test yöntemi olarak `TestMethod1` tanımlamak için <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> özniteliğini uygular.

1. **Çözüm Gezgini**, **stringlibrarytest** projesinin **Bağımlılıklar** düğümüne sağ tıklayın ve bağlam menüsünden **Başvuru Ekle** ' yi seçin.

   ![StringLibraryTest bağımlılıklarının bağlam menüsü](./media/testing-library-with-visual-studio/add-reference-context-menu.png)

1. **Başvuru Yöneticisi** iletişim kutusunda, **Projeler** düğümünü genişletin ve **StringLibrary**' ın yanındaki kutuyu işaretleyin. `StringLibrary` derlemesine bir başvuru eklemek derleyicinin **StringLibrary** yöntemlerini bulmasını sağlar. **Tamam** düğmesini seçin. Bu, `StringLibrary`sınıf kitaplığı projenize bir başvuru ekler.

   ![Visual Studio proje başvurusu ekleme iletişim kutusu-Visual Basic](./media/testing-library-with-visual-studio/project-reference-manager.png)

---

## <a name="adding-and-running-unit-test-methods"></a>Birim testi yöntemleri ekleme ve çalıştırma

Visual Studio bir birim testi çalıştırdığında, bir birim testi sınıfında <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> özniteliğiyle işaretlenmiş her bir yöntemi yürütür, bu sınıf <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> özniteliği uygulandı. Bir test yöntemi, ilk hata ile karşılaşıldığında veya yöntemde bulunan tüm testler başarılı olduğunda sona erer.

En yaygın testler <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> sınıfının üyelerini çağırır. Birçok onaylama yöntemi, biri beklenen test sonucu ve diğeri de gerçek test sonucu olan en az iki parametre içerir. En sık çağrılan yöntemlerin bazıları aşağıdaki tabloda gösterilmiştir:

Onaylama yöntemleri | İşlev
--- | ---
`Assert.AreEqual` | İki değerin veya nesnenin eşit olduğunu doğrular. Değerler veya nesneler eşit değilse onaylama başarısız olur.
`Assert.AreSame` | İki nesne değişkeninin aynı nesneye başvurmasını doğrular. Değişkenler farklı nesnelere başvuru yaptığında onaylama başarısız olur.
`Assert.IsFalse` | Bir koşulun `false`olduğunu doğrular. Koşul `true`, onaylama başarısız olur.
`Assert.IsNotNull` | Bir nesnenin `null`olmadığını doğrular. Nesne `null`, onaylama başarısız olur.

<xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute> özniteliğini bir test yöntemine de uygulayabilirsiniz. Bir test yönteminin oluşturması beklenen özel durum türünü gösterir. Belirtilen özel durum atılmazsa, test başarısız olur.

`StringLibrary.StartsWithUpper` yöntemini test ederken, büyük harfli bir karakterle başlayan bir dizi dize sağlamak istersiniz. Yöntemi bu durumlarda `true` döndürecek şekilde beklediğinizi, <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A> yöntemini çağırabilirsiniz. Benzer şekilde, büyük harfli bir karakter ile başlayan bir dizi dize sağlamak istersiniz. Yöntemi bu durumlarda `false` döndürecek şekilde beklediğinizi, <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A> yöntemini çağırabilirsiniz.

Kitaplık yönteminiz dizeleri yaptığından, ayrıca [boş bir dizeyi (`String.Empty`) başarılı bir şekilde ()](xref:System.String.Empty), hiçbir karakteri olmayan ve <xref:System.String.Length> 0 olan ve başlatılmamış bir `null` dizesinin başarıyla çalıştığından emin olmak istersiniz. `StartsWithUpper` bir <xref:System.String> örneğinde uzantı yöntemi olarak çağrılırsa, `null` bir dize geçirilemez. Ancak, bunu doğrudan statik bir yöntem olarak çağırabilir ve tek bir <xref:System.String> bağımsız değişkeni geçirebilirsiniz.

Her biri bir dize dizisindeki her öğe için <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> yöntemini her bir kez çağıran üç yöntem tanımlayacaksınız. İlk başarısızlığından sonra test yöntemi başarısız olduğundan, yöntem çağrısında kullanılan dize değerini gösteren bir dize geçirmenize izin veren bir yöntem aşırı yüklemesi çağıracaksınız.

Test yöntemleri oluşturmak için:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. *UnitTest1.cs* Code penceresinde, kodu şu kodla değiştirin:

   [!code-csharp[Test#1](~/samples/snippets/csharp/getting_started/with_visual_studio_2017/testlib1.cs)]

   `TestStartsWithUpper` yönteminde büyük harfli karakter testinizin Yunanca Büyük Harf Alpha (U + 0391) ve Kiril Büyük harf EM (U + 041C) ve `TestDoesNotStartWithUpper` yönteminde küçük harfli karakterlerin testi, Yunanca Küçük Harf Alpha ' ı (U +) içerir. 03B1) ve Kiril Küçük harf GHE (U + 0433).

1. Menü çubuğunda **dosya > dosyayı** **farklı kaydet**' i seçin. **Dosyayı farklı kaydet** Iletişim kutusunda **Kaydet** düğmesinin yanındaki oku seçin ve **kodlamayla kaydet**' i seçin.

   ![Visual Studio dosyayı farklı Kaydet iletişim kutusu-C#](./media/testing-library-with-visual-studio/save-file-as-dialog.png)

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. *UnitTest1. vb* Code penceresinde, kodu aşağıdaki kodla değiştirin:

    [!code-vb[Test#1](~/samples/snippets/core/tutorials/vb-library-with-visual-studio/testlib.vb)]

   `TestStartsWithUpper` yönteminde büyük harfli karakter testinizin Yunanca Büyük Harf Alpha (U + 0391) ve Kiril Büyük harf EM (U + 041C) ve `TestDoesNotStartWithUpper` yönteminde küçük harfli karakterlerin testi, Yunanca Küçük Harf Alpha ' ı (U +) içerir. 03B1) ve Kiril Küçük harf GHE (U + 0433).

1. Menü çubuğunda **Dosya** ' yı seçin > **UnitTest1. vb dosyasını farklı kaydedin**. **Dosyayı farklı kaydet** Iletişim kutusunda **Kaydet** düğmesinin yanındaki oku seçin ve **kodlamayla kaydet**' i seçin.

   ![Visual Studio dosyayı farklı Kaydet iletişim kutusu Visual Basic](./media/testing-library-with-visual-studio/save-file-as-dialog.png)

---

1. **Farklı kaydet** iletişim kutusunda, dosyayı kaydetmek için **Evet** düğmesini seçin.

1. **Gelişmiş kaydetme seçenekleri** iletişim kutusunda, **kodlama** açılan LISTESINDEN **Unicode (imzayla UTF-8)-kod sayfası 65001** ' i seçin ve **Tamam**' ı seçin.

   ![Visual Studio Gelişmiş kaydetme seçenekleri iletişim kutusu](./media/testing-library-with-visual-studio/advanced-save-options.png)

   Kaynak kodunuzu UTF8 kodlu bir dosya olarak kaydedemeyebilirsiniz, Visual Studio bunu bir ASCII dosyası olarak kaydedebilir. Söz konusu olduğunda, çalışma zamanı, ASCII aralığının dışında UTF8 karakterlerinin kodunu doğru şekilde çözmez ve test sonuçları doğru olmayacaktır.

1. Menü çubuğunda **Test** > **Tüm testler** > **Çalıştır** ' ı seçin. **Test Gezgini** penceresi açılır ve testlerin başarıyla çalıştığını gösterir. **Geçen testler** bölümünde üç test listelenir ve **Özet** bölümü Test çalıştırmasının sonucunu raporlar.

   ![Testleri geçirerek test Gezgini penceresi](./media/testing-library-with-visual-studio/test-explorer-window.png)

## <a name="handling-test-failures"></a>Test başarısızlıklarını işleme

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

   ![Başarısız testlerle test Gezgini penceresi](./media/testing-library-with-visual-studio/failed-test-window.png)

1. **Başarısız testler** bölümünde başarısız test ' i seçin `TestDoesNotStartWith`. **Test Gezgini** penceresi onay tarafından oluşturulan iletiyi görüntüler: "onaylama. IsFalse başarısız oldu. ' Error ' bekleniyor: false; gerçek: true ". Hata nedeniyle "hata" sonunda dizideki tüm dizeler sınanmadı.

   ![False onaylama hatası olduğunu gösteren test Gezgini penceresi](./media/testing-library-with-visual-studio/failed-test-detail.png)

1. Adım 1 ' de yaptığınız değişikliği geri alın ve "hata" dizesini kaldırın. Testi yeniden çalıştırın ve testler geçer.

## <a name="testing-the-release-version-of-the-library"></a>Kitaplığın yayın sürümünü test etme

Testlerinizi kitaplığın hata ayıklama sürümüne karşı çalıştırıyorsunuz. Artık testleriniz başarılı olduğuna ve kitaplığınızı yeterince test edinceye kadar, bu testleri kitaplığın yayın derlemesi için ek bir zaman çalıştırmalısınız. Derleyici iyileştirmeleri dahil olmak üzere bir dizi etken bazen hata ayıklama ve yayın yapıları arasında farklı davranışlar üretebilir.

Yayın derlemesini test etmek için:

1. Visual Studio araç çubuğunda, derleme yapılandırmasını **Debug** iken **Release**olarak değiştirin.

   ![Yayın derlemesi vurgulanmış Visual Studio araç çubuğu](./media/testing-library-with-visual-studio/visual-studio-toolbar-release.png)

1. **Çözüm Gezgini**, **StringLibrary** projesine sağ tıklayın ve kitaplığı yeniden derlemek için bağlam menüsünden **Oluştur** ' u seçin.

   ![Build komutuyla StringLibrary bağlam menüsü](./media/testing-library-with-visual-studio/build-library-context-menu.png)

1. **Test** > menü çubuğundan **tüm testleri** > **Çalıştır** öğesini seçerek birim testlerini çalıştırın. Testler geçer.

Artık kitaplığınızı test etmeyi tamamladığınıza göre, bir sonraki adım çağıranlar tarafından kullanılabilir hale gelir. Bunu bir veya daha fazla uygulamayla paketleyebilir veya bir NuGet paketi olarak dağıtabilirsiniz. Daha fazla bilgi için bkz. [.NET Standard sınıf kitaplığı](./consuming-library-with-visual-studio.md)kullanma.
