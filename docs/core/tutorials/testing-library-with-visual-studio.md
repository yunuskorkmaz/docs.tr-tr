---
title: Visual Studio 2017'de .NET Core ile bir .NET standart sınıf kitaplığını test etme
description: .NET Core sınıf kitaplığı için birim testi projesi oluşturun. .NET Core sınıf kitaplığı ile birim testleri doğru şekilde çalıştığını doğrulayın.
author: BillWagner
ms.author: wiwagn
ms.date: 08/07/2017
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet, seodoc18
ms.openlocfilehash: 352599d60a42a034b3d6647b1fe8f1cbf2f4572d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61647931"
---
# <a name="test-a-net-standard-library-with-net-core-in-visual-studio-2017"></a>Visual Studio 2017'de .NET Core ile bir .NET Standard kitaplığını test etme

İçinde [bir .NET Standard kitaplığı ile derleme C# ve Visual Studio 2017'de .NET Core](library-with-visual-studio.md) veya [Visual Basic ve Visual Studio 2017'de .NET Core ile bir .NET Standard kitaplığı derleme](vb-library-with-visual-studio.md), basit bir sınıf oluşturuldu bir genişletme yöntemi için ekler Kitaplığı <xref:System.String> sınıfı. Şimdi beklendiği gibi çalıştığından emin olmak için birim testi oluşturmayı öğreneceksiniz. Önceki makalede oluşturduğunuz çözüm, birim testi projesi ekleyeceksiniz.

## <a name="creating-a-unit-test-project"></a>Birim testi projesi oluşturma

Birim test projesi oluşturmak için aşağıdakileri yapın:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. İçinde **Çözüm Gezgini**, bağlam menüsünü **ClassLibraryProjects** çözüm düğümüne ve select **Ekle** > **YeniProje**.

1. İçinde **Yeni Proje Ekle** iletişim kutusunda **Visual C#** düğümü. Ardından **.NET Core** düğümünü ve ardından **MSTest Test projesi (.NET Core)** proje şablonu. İçinde **adı** metin kutusunda, projenin adı "StringLibraryTest" girin. Seçin **Tamam** birim test projesi oluşturmak için.

   ![Yeni Proje iletişim kutusunda görüntülenen birim testi projesi ekleyin-C#](./media/testing-library-with-visual-studio/create-new-test-project.png)

   > [!NOTE]  
   > MSTest Test projesinde ek olarak, .NET Core için bir xUnit test projesi oluşturmak için Visual Studio kullanabilirsiniz.

1. Visual Studio projesi oluşturur ve açar *UnitTest1.cs* kod penceresinde dosya.

   ![Visual Studio kod penceresi biriminin proje sınıf ve metod test-C#](./media/testing-library-with-visual-studio/unit-test-editor-window.png)

   Birim test şablon tarafından oluşturulan kaynak kodu şunları yapar:

   * Bunu aktarır <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> ad alanı birim testi için kullanılan türler içerir.

   * Geçerli <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> özniteliğini `UnitTest1` sınıfı. Her bir test sınıfındaki test yönteminin etiketlenir \[TestMethod\] özniteliği birim testi çalıştırdığınızda otomatik olarak yürütülür.

   * Geçerli <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> tanımlamak için öznitelik `TestMethod1` birim testi çalıştırdığınızda otomatik yürütme için bir test yöntemi olarak.

1. İçinde **Çözüm Gezgini**, sağ **bağımlılıkları** düğümünün **StringLibraryTest** seçin ve proje **Başvuru Ekle** gelen bağlam menüsü.

   ![Bağlam menüsü StringLibraryTest bağımlılıklarının-C#](./media/testing-library-with-visual-studio/add-reference-context-menu.png)

1. İçinde **başvuru Yöneticisi** iletişim kutusunda Genişlet **projeleri** düğüm ve yanındaki kutuyu işaretleyin **StringLibrary**. Bir başvuru eklemeyi `StringLibrary` derleme sağlayan bulmak derleyicinin **StringLibrary** yöntemleri. **Tamam** düğmesini seçin. Bu, sınıf kitaplığı projesine bir başvuru ekler `StringLibrary`.

   ![Visual Studio eklenti proje başvuru iletişim kutusu](./media/testing-library-with-visual-studio/project-reference-manager.png)
# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb) 
1. İçinde **Çözüm Gezgini**, bağlam menüsünü **ClassLibraryProjects** çözüm düğümüne ve select **Ekle** > **YeniProje**.

1. İçinde **Yeni Proje Ekle** iletişim kutusunda **Visual Basic** düğümü. Ardından **.NET Core** düğümünü ve ardından **MSTest Test projesi (.NET Core)** proje şablonu. İçinde **adı** metin kutusunda, projenin adı "StringLibraryTest" girin. Seçin **Tamam** birim test projesi oluşturmak için.

   ![Yeni Proje iletişim kutusunda görüntülenen - birim testi projesi ile Visual Basic Ekle](./media/testing-library-with-visual-studio/vb-create-new-test-project.png)

   > [!NOTE]  
   > MSTest Test projesinde ek olarak, .NET Core için bir xUnit test projesi oluşturmak için Visual Studio kullanabilirsiniz.

1. Visual Studio projesi oluşturur ve açar *UnitTest1.vb* kod penceresinde dosya.

   ![Visual Studio kod penceresi için birim test proje sınıfı ve yöntemi - Visual Basic](./media/testing-library-with-visual-studio/vb-unit-test-editor-window.png)

   Birim test şablon tarafından oluşturulan kaynak kodu şunları yapar:

   * [Microsoft.VisualStudio.TestTools.UnitTesting] aktarır<xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=namewithType> ad alanı birim testi için kullanılan türler içerir.

   * Geçerli <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute>) özniteliğini `UnitTest1` sınıfı. Her bir test sınıfındaki test yönteminin etiketlenir <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> özniteliği birim testi çalıştırdığınızda otomatik olarak yürütülür.

   * Geçerli <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> tanımlamak için öznitelik `TestMethod1` birim testi çalıştırdığınızda otomatik yürütme için bir test yöntemi olarak.

1. İçinde **Çözüm Gezgini**, sağ **bağımlılıkları** düğümünün **StringLibraryTest** seçin ve proje **Başvuru Ekle** gelen bağlam menüsü.

   ![StringLibraryTest bağımlılıkları bağlam menüsü](./media/testing-library-with-visual-studio/add-reference-context-menu.png)

1. İçinde **başvuru Yöneticisi** iletişim kutusunda Genişlet **projeleri** düğüm ve yanındaki kutuyu işaretleyin **StringLibrary**. Bir başvuru eklemeyi `StringLibrary` derleme sağlayan bulmak derleyicinin **StringLibrary** yöntemleri. **Tamam** düğmesini seçin. Bu, sınıf kitaplığı projesine bir başvuru ekler `StringLibrary`.

   ![Visual Studio eklenti proje başvuru iletişim kutusu - Visual Basic](./media/testing-library-with-visual-studio/project-reference-manager.png)
---

## <a name="adding-and-running-unit-test-methods"></a>Ekleme ve birim test yöntemleri

Visual Studio birim testi çalıştırıldığında her yöntem ile işaretlenmiş yürütülmeden <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> bir birim test sınıfı özniteliği, sınıfa <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> özniteliği uygulanır. Bir test yöntemi, ilk hata ile karşılaşıldığında veya yöntemin içinde yer alan tüm testler başarılı olduğunda sona erer.

En yaygın arama üyelerinin testleri <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> sınıfı. Çoğu assert, biri beklenen test sonucu olan ve gerçek test sonucu, diğeri ise en az iki parametre yöntemleri içerir. Aşağıdaki tabloda, en sık aranan yöntemlerden bazıları gösterilmektedir.

Assert yöntemi | İşlev
--- | ---
`Assert.AreEqual` | İki değerler veya nesneler eşit olduğunu doğrular. Assert, değerler veya nesneler eşit değilse başarısız olur.
`Assert.AreSame` | İki nesne değişkenini aynı nesneye başvurması doğrular. Değişkenleri farklı nesnelere başvuru assert başarısız olur.
`Assert.IsFalse` | Bir koşul olduğunu doğrular `false`. Assert başarısız koşul ise `true`.
`Assert.IsNotNull` | Bir nesne olmadığını doğrular `null`. Assert başarısız nesne ise `null`.

Ayrıca uygulayabilirsiniz <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute> bir test metodu özniteliği. Bu, bir test yöntemi throw beklenen özel durumun türünü gösterir. Belirtilen özel durum değil, test başarısız olur.

Test `StringLibrary.StartsWithUpper` yöntemi, istediğiniz bir büyük harf karakteri ile başlayan dizeleri sayısını sağlar. Döndürmek için yöntemin beklediğiniz `true` bu gibi durumlarda, bu nedenle çağırabilirsiniz <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A> yöntemi. Benzer şekilde, bir büyük harf karakteri dışında bir öğe ile başlayan dizeleri sayısı sunmak istiyorsunuz. Döndürmek için yöntemin beklediğiniz `false` bu gibi durumlarda, bu nedenle çağırabilirsiniz <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A> yöntemi.

Kitaplık yönteminizi dizeleri işleme olduğundan, ayrıca başarıyla işlediğini emin olmak istediğiniz bir [boş dize (`String.Empty`)](xref:System.String.Empty), herhangi bir karakter ve ayarlanmış olan geçerli bir dize <xref:System.String.Length> 0 ' dır ve `null` dize başlatılmadı. Varsa `StartsWithUpper` üzerinde bir genişletme yöntemi adlandırılır bir <xref:System.String> örneği, bu geçirilemez bir `null` dize. Ancak, bir statik yöntem doğrudan çağrı da tek bir geçirmek <xref:System.String> bağımsız değişken.

Üç yöntem tanımlarsınız her çağırır, <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> sürekli bir dize dizideki her öğe için yöntemi. İlk başarısızlık bulduğu hemen sonra test yöntemi başarısız olduğundan, yöntem çağrısında kullanılan dize değerini gösteren bir dize geçmesine izin veren bir yöntem aşırı yüklemesini ararız.

Test yöntemlerini oluşturmak için:

# <a name="ctabcsharp"></a>[C#](#tab/csharp) 
1. İçinde *UnitTest1.cs* kod penceresi, kodu aşağıdaki kodla değiştirin:

   [!CODE-csharp[Test#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/testlib1.cs)]

   Test büyük Not karakter olarak `TestStartsWithUpper` Yunanca Büyük Harf alfa includes yöntemi (U + 0391) ve Kiril EM (U + 041 C) büyük harf ve küçük harflerle test `TestDoesNotStartWithUpper` yöntemi Yunanca Küçük Harf içerir Alfa (U + 03B1) ve Kiril Küçük Harf Ghe (U + 0433).

1. Menü çubuğunda, seçin **dosya** > **UnitTest1.cs Kaydet**. İçinde **dosyayı farklı Kaydet** iletişim kutusunda, yanındaki oku seçerek **Kaydet** düğmesini ve **kodlama ile Kaydet**.

   ![Visual Studio dosyayı farklı Kaydet iletişim kutusu-C#](./media/testing-library-with-visual-studio/save-file-as-dialog.png)
# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb) 
1. İçinde *UnitTest1.vb* kod penceresi, kodu aşağıdaki kodla değiştirin:

    [!CODE-vb[Test#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/testlib.vb)]

   Test büyük Not karakter olarak `TestStartsWithUpper` Yunanca Büyük Harf alfa includes yöntemi (U + 0391) ve Kiril EM (U + 041 C) büyük harf ve küçük harflerle test `TestDoesNotStartWithUpper` yöntemi Yunanca Küçük Harf içerir Alfa (U + 03B1) ve Kiril Küçük Harf Ghe (U + 0433).

1. Menü çubuğunda, seçin **dosya** > **UnitTest1.vb Kaydet**. İçinde **dosyayı farklı Kaydet** iletişim kutusunda, yanındaki oku seçerek **Kaydet** düğmesini ve **kodlama ile Kaydet**.

   ![Visual Studio dosyayı farklı Kaydet iletişim kutusu - Visual Basic](./media/testing-library-with-visual-studio/save-file-as-dialog.png)
---

1. İçinde **Kaydet onaylayın** iletişim kutusunda **Evet** düğmesini kullanarak dosyayı kaydedin.

1. İçinde **Gelişmiş kaydetme seçenekleri** iletişim kutusunda **Unicode (UTF-8 imzayla) - kod sayfası 65001** gelen **kodlama** aşağı açılan listesinden **Tamam** .

   ![Visual Studio Gelişmiş Kaydetme Seçenekleri iletişim kutusu](./media/testing-library-with-visual-studio/advanced-save-options.png)

   Kaynak kodunuzu UTF8 ile kodlanan dosya olarak kaydetmek başarısız olursa, Visual Studio, bir ASCII dosyası olarak kaydedebilirsiniz. Bu durum oluştuğunda, çalışma zamanı ASCII aralığı dışındaki UTF8 karakterleri doğru bir şekilde kod çözme değil ve test sonuçlarını doğru olmaz.

1. Menü çubuğunda, seçin **Test** > **çalıştırma** > **tüm testleri**. **Test Gezgini** penceresi açılır ve testlerin başarıyla çalıştığını gösterir. Üç testi de listelenen **başarılı testler** bölümünde ve **özeti** bölüm test çalışması sonucu bildirir.

   ![Test Gezgini penceresi ile testleri geçirme](./media/testing-library-with-visual-studio/test-explorer-window.png)

## <a name="handling-test-failures"></a>Test hatalarını işleme

Test çalıştırmanızın herhangi bir hata vardı, ancak test yöntemi başarısız biraz değiştirmek:

1. Değiştirme `words` içindeki dizi `TestDoesNotStartWithUpper` "Error" dizesi eklemek için yöntemi. Testleri çalıştırmak için bir çözüm derlenirken açık dosyalar Visual Studio otomatik olarak kaydeder. çünkü dosyayı kaydetmek gerek yoktur.

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

   ```vb
   Dim words() As String = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " }

   ```

1. Seçerek test çalıştırması **Test** > **çalıştırma** > **tüm testleri** menü çubuğundan. **Test Gezgini** iki testleri başarılı ve başarısız bir pencerede gösterilir.

   ![Başarısız testleri içeren test Gezgini penceresi](./media/testing-library-with-visual-studio/failed-test-window.png)

1. İçinde **başarısız testler** bölümünde, başarısız bir test seçin `TestDoesNotStartWith`. **Test Gezgini** penceresi assert tarafından üretilen iletisini görüntüler: "Assert.IsFalse başarısız oldu. 'Hata' için bekleniyor: false; Gerçek: True". Hatasından sonra "Error" dizisindeki tüm dizeleri sınanmamıştır.

   ![Test Gezgini penceresi olan False onaylama işlemi hatası gösteriliyor](./media/testing-library-with-visual-studio/failed-test-detail.png)

1. 1. adımda yaptığınız değişikliği geri almak ve "Error" dizesini kaldırın. Testi yeniden çalıştırın ve testlerin başarılı.

## <a name="testing-the-release-version-of-the-library"></a>Kitaplık sürümünü test etme

Siz testlerinizi karşı kitaplığı hata ayıklama sürümünü çalıştırıyorsunuz. Tüm testler geçer ve kitaplığınızı yeterince test ettikten sonra kitaplığın sürüm oluşturma ek bir zaman testleri çalıştırmanız gerekir. Derleyici iyileştirmeleri dahil olmak üzere bir dizi etkene, bazen hata ayıklama ve yayın Yapılar arasındaki farklı bir davranış oluşturabilir.

Yayın derlemesi test etmek için:

1. Visual Studio araç çubuğunda, değiştirmek derleme yapılandırmasından **hata ayıklama** için **yayın**.

   ![Visual Studio araç ile vurgulanmış yayın derlemesi](./media/testing-library-with-visual-studio/visual-studio-toolbar-release.png)

1. İçinde **Çözüm Gezgini**, sağ tıklayın **StringLibrary** seçin ve proje **derleme** bağlam menüsünden kitaplığı yeniden derleyin.

   ![Derleme komutuyla StringLibrary bağlam menüsü](./media/testing-library-with-visual-studio/build-library-context-menu.png)

1. Kullanarak birim testlerini çalıştırmak **Test** > **çalıştırma** > **tüm testleri** menü çubuğundan. Testler başarılı.

Kitaplığınızı test işlemini bitirdikten sonra sonraki adıma arayanlar için kullanılabilir olmasını sağlamaktır. Uygulamaları bir veya daha fazla paket veya bir NuGet paketi olarak dağıtabilirsiniz. Daha fazla bilgi için [.NET standart sınıf kitaplığı kullanma](./consuming-library-with-visual-studio.md).
