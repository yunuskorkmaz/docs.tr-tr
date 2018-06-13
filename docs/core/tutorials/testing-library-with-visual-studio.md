---
title: Visual Studio 2017 içinde bir sınıf kitaplığı .NET Core ile test etme
description: Visual Studio 2017 kullanarak C# içinde yazılmış bir sınıf kitaplığı test öğrenin
author: BillWagner
ms.author: wiwagn
ms.date: 08/07/2017
dev_langs:
- csharp
- vb
ms.openlocfilehash: 1733f3fc66d79dafb9bc6f983773f043be6c1006
ms.sourcegitcommit: b7763f3435635850a76d4cbcf09bdce6c019208a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/25/2018
ms.locfileid: "34483479"
---
# <a name="testing-a-class-library-with-net-core-in-visual-studio-2017"></a>Visual Studio 2017 içinde bir sınıf kitaplığı .NET Core ile test etme

İçinde [oluşturma C# ve Visual Studio 2017 .NET çekirdek sınıf kitaplığına](library-with-visual-studio.md) veya [oluşturma Visual Basic ve Visual Studio 2017 .NET çekirdek sınıf kitaplığına](vb-library-with-visual-studio.md), ekler basit sınıf kitaplığı oluşturulan bir genişletme yöntemi <xref:System.String> sınıfı. Şimdi, beklendiği gibi çalıştığını emin olmak için birim testi oluşturacaksınız. Birim testi projesi önceki konusunda oluşturulan çözüm eklenecektir.

## <a name="creating-a-unit-test-project"></a>Birim testi projesi oluşturma

Birim testi projesi oluşturmak için aşağıdakileri yapın:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. İçinde **Çözüm Gezgini**, bağlam menüsünü açın **ClassLibraryProjects** çözüm düğümüne ve select **Ekle** > **yeni proje**.

1. İçinde **Yeni Proje Ekle** iletişim kutusunda **Visual C#** düğümü. Ardından **.NET Core** düğümünü ve ardından **mstest'i Test projesi (.NET Core)** proje şablonu. İçinde **adı** metin kutusunda, "StringLibraryTest" projesinin adı girin. Seçin **Tamam** birim testi projesi oluşturmak için.

   ![Yeni Proje iletişim kutusu ekleme](./media/testing-library-with-visual-studio/testproject.png)

   > [!NOTE]  
   > Mstest'i Test projesinde ek olarak, .NET Core xUnit test projesi oluşturmak için Visual Studio kullanabilirsiniz.

1. Visual Studio projesi oluşturur ve açılır *UnitTest1.cs* kod penceresinde dosya.

   ![Visual Studio kod penceresi varsayılan birimi gösteren test projesi UnitTest1 sınıfı ve TestMethod1 yöntemi](./media/testing-library-with-visual-studio/unittestwindow.png)

   Birim testi şablonu tarafından oluşturulan kaynak kodu şunları yapar:

   * Bunu aktarır [Microsoft.VisualStudio.TestTools.UnitTesting](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.aspx) ad alanı birim testi için kullanılan türler içerir.

   * Geçerli [ \[TestClass\] ](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testclassattribute.aspx) özniteliğini `UnitTest1` sınıfı. Bir test sınıftaki her test yöntemi etiketli ile \[TestMethod\] özniteliği birim testi çalıştırdığınızda otomatik olarak yürütüldüğünde.

   * Geçerli [ \[TestMethod\] ](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testmethodattribute.aspx) tanımlamak için öznitelik `TestMethod1` birim testi çalıştırdığınızda otomatik yürütme için bir test yöntemi olarak.

1. İçinde **Çözüm Gezgini**, sağ **bağımlılıkları** düğümünün **StringLibraryTest** proje ve seçin **Başvuru Ekle** gelen bağlam menüsü.

   ![Bağlam menüsü StringLibraryTest bağımlılıkları](./media/testing-library-with-visual-studio/addreference.png)

1. İçinde **başvuru Yöneticisi** iletişim kutusunda, genişletin **projeleri** düğümü ve yanındaki kutuyu işaretleyin **StringLibrary**. Bir başvuru ekleyerek `StringLibrary` derleme sağlayan bulmak derleyici **StringLibrary** yöntemleri. Seçin **Tamam** düğmesi. Bu sınıf kitaplığı projenizin bir başvuru ekler `StringLibrary`.

   ![Başvuru Yöneticisi](./media/testing-library-with-visual-studio/referencemanager.png)
# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic) 
1. İçinde **Çözüm Gezgini**, bağlam menüsünü açın **ClassLibraryProjects** çözüm düğümüne ve select **Ekle** > **yeni proje**.

1. İçinde **Yeni Proje Ekle** iletişim kutusunda **Visual Basic** düğümü. Ardından **.NET Core** düğümünü ve ardından **mstest'i Test projesi (.NET Core)** proje şablonu. İçinde **adı** metin kutusunda, "StringLibraryTest" projesinin adı girin. Seçin **Tamam** birim testi projesi oluşturmak için.

   ![Yeni Proje iletişim kutusu ekleme](./media/testing-library-with-visual-studio/vb-testproject.png)

   > [!NOTE]  
   > Mstest'i Test projesinde ek olarak, .NET Core xUnit test projesi oluşturmak için Visual Studio kullanabilirsiniz.

1. Visual Studio projesi oluşturur ve açılır *UnitTest1.vb* kod penceresinde dosya.

   ![Visual Studio kod penceresi varsayılan birimi gösteren test projesi UnitTest1 sınıfı ve TestMethod1 yöntemi](./media/testing-library-with-visual-studio/vb-unittestwindow.png)

   Birim testi şablonu tarafından oluşturulan kaynak kodu şunları yapar:

   * Bunu aktarır [Microsoft.VisualStudio.TestTools.UnitTesting](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.aspx) ad alanı birim testi için kullanılan türler içerir.

   * Geçerli [ \[TestClass\] ](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testclassattribute.aspx) özniteliğini `UnitTest1` sınıfı. Bir test sınıftaki her test yöntemi etiketli ile \[TestMethod\] özniteliği birim testi çalıştırdığınızda otomatik olarak yürütüldüğünde.

   * Geçerli [ \[TestMethod\] ](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testmethodattribute.aspx) tanımlamak için öznitelik `TestMethod1` birim testi çalıştırdığınızda otomatik yürütme için bir test yöntemi olarak.

1. İçinde **Çözüm Gezgini**, sağ **bağımlılıkları** düğümünün **StringLibraryTest** proje ve seçin **Başvuru Ekle** gelen bağlam menüsü.

   ![Bağlam menüsü StringLibraryTest bağımlılıkları](./media/testing-library-with-visual-studio/addreference.png)

1. İçinde **başvuru Yöneticisi** iletişim kutusunda, genişletin **projeleri** düğümü ve yanındaki kutuyu işaretleyin **StringLibrary**. Bir başvuru ekleyerek `StringLibrary` derleme sağlayan bulmak derleyici **StringLibrary** yöntemleri. Seçin **Tamam** düğmesi. Bu sınıf kitaplığı projenizin bir başvuru ekler `StringLibrary`.

   ![Başvuru Yöneticisi](./media/testing-library-with-visual-studio/referencemanager.png)
---

## <a name="adding-and-running-unit-test-methods"></a>Ekleme ve birim çalıştıran test yöntemleri

Visual Studio birim testi çalıştığında, ile işaretli her yöntem yürütür [ \[TestMethod\] ](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testmethodattribute.aspx) birim testi sınıfı özniteliğinde, sınıfına [ \[TestClass\] ](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testclassattribute.aspx) özniteliği uygulanır. Test yöntemi ilk hatasıyla karşılaştı veya ne zaman yönteminde bulunan tüm testlerde başarılı olduğunu sonlandırır.

En sık karşılaşılan çağrısı üyeleri testleri [Assert](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.assert.aspx) sınıfı. Birçok yöntemlerden biri beklenen test sonucu olan ve diğeri de gerçek test sonucu, en az iki parametre dahil assert. Aşağıdaki tabloda, en sık aranan yöntemlerden bazıları gösterilmektedir.

Assert yöntemleri | İşlev
--- | ---
`Assert.AreEqual` | İki değeri veya nesneleri eşit olduğunu doğrular. Değerleri veya nesneleri eşit değilse assert başarısız olur.
`Assert.AreSame` | İki nesne değişkenlerini de aynı nesneye başvuran doğrular. Farklı nesnelere değişkenleri başvurduğundan assert başarısız olur.
`Assert.IsFalse` | Bir koşul olduğunu doğrular `false`. Koşul ise assert başarısız `true`.
`Assert.IsNotNull` | Bir nesnenin olmadığını doğrular `null`. Nesne ise assert başarısız `null`.

Ayrıca uygulayabilirsiniz [ \[ExpectedException\] ](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.expectedexceptionattribute.aspx) özniteliği için bir test yöntemi. Test yöntemi throw beklenen özel durumun türünü gösterir. Belirtilen özel olmayan durum sınama başarısız olur.

Sınama sırasında `StringLibrary.StartsWithUpper` yöntemi, istediğiniz bir büyük harf karakter ile başlayan dizeleri çok sayıda sağlar. Döndürülecek yöntemi beklediğiniz `true` bu durumlarda, bu nedenle çağırabilirsiniz [Assert.IsTrue (Boolean, dize)](https://msdn.microsoft.com/library/ms243754.aspx) yöntemi. Benzer şekilde, bir büyük harf karakter dışında bir şey ile başlayan dizeleri sayısı sağlamak istediğinizde. Döndürülecek yöntemi beklediğiniz `false` bu durumlarda, bu nedenle çağırabilirsiniz [Assert.IsFalse (Boolean, dize)](https://msdn.microsoft.com/library/ms243805.aspx) yöntemi.

Dizeleri kitaplığı yönteminizi işleme olduğundan, ayrıca başarıyla işler emin olmak istediğiniz bir [boş dize (`String.Empty`)](xref:System.String.Empty), hiçbir karakter ve özelliği sahip geçerli bir dize <xref:System.String.Length> 0 ' dır ve `null` dize başlatılmadı. Varsa `StartsWithUpper` üzerinde bir genişletme yöntemi adlandırılır bir <xref:System.String> örneği, bu olamaz bayraklarıdır bir `null` dize. Ancak, ayrıca bir statik yöntem olarak doğrudan çağırmak ve tek bir geçirmek <xref:System.String> bağımsız değişkeni.

Üç yöntem tanımlama olasılığınız yüksektir her çağıran kendi [Assert](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.assert.aspx) sürekli olarak bir dize dizisi her öğe için yöntem. İlk hata karşılaştığında hemen test yöntemi başarısız olduğu için yöntem çağrısında kullanılan dize değeri belirten bir dize geçmesine izin veren bir yöntemi aşırı yüklemesini çağırın.

Test yöntemleri oluşturmak için:

# <a name="ctabcsharp"></a>[C#](#tab/csharp) 
1. İçinde *UnitTest1.cs* kod penceresi, kodu aşağıdaki kodla değiştirin:

   [!CODE-csharp[Test#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/testlib1.cs)]

   Testinizi, büyük harf Not karakterleri `TestStartsWithUpper` Yunanca Büyük Harf alpha includes yöntemi (U + 0391) ve Kiril Büyük Harf EM (U + 041 C) ve küçük harf karakter test `TestDoesNotStartWithUpper` Yunanca Küçük Harf includes yöntemi Alfa (U + 03B1) ve Kiril Küçük Harf Ghe (U + 0433).

1. Menü çubuğunda seçin **dosya** > **UnitTest1.cs Kaydet**. İçinde **dosyasını Farklı Kaydet** iletişim kutusunda, yanındaki oku seçin **kaydetmek** düğmesine tıklayın ve ardından **kodlama ile Kaydet**.

   ![İletişim dosyayı farklı kaydet](./media/testing-library-with-visual-studio/savefileas.png)
# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic) 
1. İçinde *UnitTest1.vb* kod penceresi, kodu aşağıdaki kodla değiştirin:

    [!CODE-vb[Test#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/testlib.vb)]

   Testinizi, büyük harf Not karakterleri `TestStartsWithUpper` Yunanca Büyük Harf alpha includes yöntemi (U + 0391) ve Kiril Büyük Harf EM (U + 041 C) ve küçük harf karakter test `TestDoesNotStartWithUpper` Yunanca Küçük Harf includes yöntemi Alfa (U + 03B1) ve Kiril Küçük Harf Ghe (U + 0433).

1. Menü çubuğunda seçin **dosya** > **UnitTest1.vb Kaydet**. İçinde **dosyasını Farklı Kaydet** iletişim kutusunda, yanındaki oku seçin **kaydetmek** düğmesine tıklayın ve ardından **kodlama ile Kaydet**.

   ![İletişim dosyayı farklı kaydet](./media/testing-library-with-visual-studio/savefileas.png)
---

1. İçinde **Kaydet onaylayın** iletişim kutusunda **Evet** düğmesi dosyayı kaydedin.

1. İçinde **Gelişmiş kaydetme seçenekleri** iletişim kutusunda **Unicode (UTF-8 imzayla) - Codepage 65001** gelen **kodlama** aşağı açılan liste ve select **Tamam** .

   ![Gelişmiş Kaydetme Seçenekleri iletişim kutusu](./media/testing-library-with-visual-studio/advancedsaveoptions.png)

   Visual Studio kaynak kodunuzu UTF8 olarak kodlanmış bir dosya olarak kaydetmek başarısız olursa, ASCII dosyası olarak kaydetmek. Bu durum oluştuğunda çalışma zamanı ASCII aralığın dışında UTF8 karakterleri doğru bir şekilde kod çözme değil ve test sonuçlarını doğru olmayacaktır.

1. Menü çubuğunda seçin **Test** > **çalıştırmak** > **tüm testleri**. **Test Gezgini** penceresi açılır ve testleri başarıyla çalıştı gösterir. Üç sınama listelenen **testleri geçti** bölümünde ve **Özet** bölüm raporları çalıştırma test sonucu.

   ![Test Gezgini penceresi](./media/testing-library-with-visual-studio/firsttest.png)

## <a name="handling-test-failures"></a>İşleme test başarısızlıklarının

Test çalışması hiçbir hataları vardı, ancak test yöntemlerden biri başarısız şekilde biraz değiştirin:

1. Değiştirme `words` içinde dizi `TestDoesNotStartWithUpper` yöntemi "Error" dizesini içerir. Visual Studio testleri çalıştırmak için bir çözüm yapılandırıldığında, otomatik olarak açık dosyaları kaydeder olduğundan dosya kaydetmeniz gerekmez.

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```
   ```vb
   Dim words() As String = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " }

   ```
1. Seçerek testi **Test** > **çalıştırmak** > **tüm testleri** menü çubuğundan. **Test Gezgini** penceresi gösteren iki testleri başarılı oldu ve biri başarısız oldu.

   ![Test Gezgini penceresi](./media/testing-library-with-visual-studio/failedtest.png)

1. İçinde **başarısız testler** bölümünde, hatalı test seçin `TestDoesNotStartWith`. **Test Gezgini** penceresi assert tarafından üretilen iletisini görüntüler: "Assert.IsFalse başarısız oldu. 'Hata' için beklenen: false; Gerçek: True ". Hatasından sonra "Error" dizisindeki tüm dizeleri sınanmamıştır.

   ![Test Gezgini penceresi olan False onaylama hatası gösterme](./media/testing-library-with-visual-studio/failedtestdetail.png)

1. Eklediğiniz kodu kaldırın (`"Error", `) ve test yeniden çalıştırın. Testleri geçer.

## <a name="testing-the-release-version-of-the-library"></a>Kitaplık sürümünü test etme

Testlerinizi kitaplığının hata ayıklama sürümü karşı çalışır durumda. Testlerinizi tüm başarılı ve kitaplığınızın yeterince test ettikten göre ek bir zaman testleri kitaplığı yayın derlemesi karşı çalıştırmanız gerekir. Derleyici iyileştirmesi dahil çeşitli Etkenler bir dizi bazen hata ayıklama ve yayın derlemeleri arasında farklı bir davranış üretebilir.

Yayın derlemesi test etmek için:

1. Visual Studio araç çubuğunda, yapı yapılandırmasından değiştirme **hata ayıklama** için **sürüm**.

   ![Visual Studio araç çubuğu](./media/testing-library-with-visual-studio/toolbar.png)

1. İçinde **Çözüm Gezgini**, sağ **StringLibrary** proje ve seçin **yapı** bağlam menüsünden kitaplığı yeniden derleyin.

   ![StringLibrary bağlam menüsü](./media/testing-library-with-visual-studio/buildlibrary.png)

1. Seçerek birim testleri çalıştırma **Test** > **çalıştırmak** > **tüm testleri** menü çubuğundan. Testleri geçirin.

Kitaplığınızı sınama bitirdikten sonra sonraki adıma arayanlara olmasını sağlamaktır. Bir veya daha fazla uygulamalarla paket veya bir NuGet paketi olarak dağıtabilirsiniz. Daha fazla bilgi için bkz: [.NET standart sınıf kitaplığı kullanma](./consuming-library-with-visual-studio.md).
