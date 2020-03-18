---
title: 'İzlenecek yol: Office Programlama (C# ve Visual Basic)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Office, programming in Visual Basic and C#
- Office programming [C#]
- Office programming [Visual Basic]
ms.assetid: 519cff31-f80b-4f0e-a56b-26358d0f8c51
ms.openlocfilehash: 6c27442cb5c0c4172f503c945849e47560c2b33d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635359"
---
# <a name="walkthrough-office-programming-c-and-visual-basic"></a>İzlenecek yol: Office Programlama (C# ve Visual Basic)

Visual Studio, C# ve Visual Basic'te Microsoft Office programlamasını geliştiren özellikler sunar. Yararlı C# özellikleri, adlandırılmış ve isteğe bağlı bağımsız değişkenler ve tür `dynamic`deki iade değerlerini içerir. COM programlamada, anahtar kelimeyi `ref` atlayabilir ve dizine ekili özelliklere erişebilirsiniz. Visual Basic'teki özellikler otomatik olarak uygulanan özellikleri, lambda ifadelerindeki deyimleri ve toplama başlatmacılarını içerir.

Her iki dil de, birincil interop derlemelerini (PIA) kullanıcının bilgisayarına dağıtmadan COM bileşenleriyle etkileşimde bulunan derlemelerin dağıtılmasına olanak tanıyan tür bilgilerinin gömülmesine olanak tanır. Daha fazla bilgi için [Walkthrough: Yönetilen Derlemelerden Türleri Katıştırma'ya](../../../standard/assembly/embed-types-visual-studio.md)bakın.

Bu izbis, Office programlama bağlamında bu özellikleri gösterir, ancak bu özelliklerin çoğu genel programlamada da yararlıdır. Bu çalışmada, Excel çalışma kitabı oluşturmak için bir Excel Eklentisi uygulaması kullanırsınız. Ardından, çalışma kitabına bağlantı içeren bir Word belgesi oluşturursunuz. Son olarak, PIA bağımlılığını nasıl etkinleştirebileceğinizi ve devre dışı kabileceğinizi görün.

## <a name="prerequisites"></a>Önkoşullar

Bu izbiyi tamamlamak için bilgisayarınızda Microsoft Office Excel ve Microsoft Office Word yüklü olmalıdır.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

### <a name="to-set-up-an-excel-add-in-application"></a>Excel Eklenti sayarı kurmak için

1. Visual Studio’yu çalıştırın.

2. **Dosya** menüsünde **Yeni'yi**işaret edin ve ardından **Project'i**tıklatın.

3. Yüklü **Şablonlar** bölmesinde Visual **Basic** veya **Visual C#** seçeneğini genişletin, **Office'i**genişletin ve ardından Office ürününün sürüm yılını tıklatın.

4. **Şablonlar** bölmesinde, **Eklenti \<> Excel sürümünü**tıklatın.

5. **.NET Framework 4**veya daha sonraki bir sürümün **Hedef Çerçeve** kutusunda göründüğünden emin olmak için **Şablonlar** bölmesinin üst bölümüne bakın.

6. İsterseniz **Ad** kutusuna projeniz için bir ad yazın.

7. **Tamam**'a tıklayın.

8. Yeni proje Çözüm **Gezgini'nde**görünür.

### <a name="to-add-references"></a>Referans eklemek için

1. **Çözüm Gezgini'nde,** projenizin adını sağ tıklatın ve ardından **Başvuru Ekle'yi**tıklatın. **Başvuru Ekle** iletişim kutusu görüntülenir.

2. **Derlemeler** sekmesinde, **Microsoft.Office.Interop.Excel**, `<version>.0.0.0` sürümünü (Office ürün sürüm numaralarının anahtarı için, [Microsoft Sürümleri'ne](https://en.wikipedia.org/wiki/Microsoft_Office#Versions)bakın), **Bileşen Adı** listesinde seçin ve ardından CTRL anahtarını basılı tutun ve **Microsoft.Office.Interop.Word**'ü `version <version>.0.0.0`seçin. Derlemeleri görmüyorsanız, bunların yüklendiğinden ve görüntülendiğinden emin olmanız gerekebilir [(bkz.](/visualstudio/vsto/how-to-install-office-primary-interop-assemblies)

3. **Tamam**'a tıklayın.

### <a name="to-add-necessary-imports-statements-or-using-directives"></a>Gerekli İthalat bildirimlerini eklemek veya yönergeleri kullanmak için

1. **Çözüm Gezgini'nde** **ThisAddIn.vb** veya **ThisAddIn.cs** dosyasını sağ tıklatın ve ardından **Kodu Görüntüle'yi**tıklatın.

2. Zaten yoksa, kod dosyasının en üstüne aşağıdaki `Imports` ifadeleri (Visual Basic) veya `using` yönergeleri (C#) ekleyin.

     [!code-csharp[csOfficeWalkthrough#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#1)]

     [!code-vb[csOfficeWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/thisaddin.vb#1)]

### <a name="to-create-a-list-of-bank-accounts"></a>Banka hesaplarının listesini oluşturmak için

1. **Çözüm Gezgini'nde,** projenizin adını sağ tıklatın, **Ekle'yi**tıklatın ve ardından **Sınıf'ı**tıklatın. Visual Basic kullanıyorsanız Account.vb sınıfını veya C#'ı kullanıyorsanız Account.cs adlandırın. **Ekle**’ye tıklayın.

2. Sınıfın tanımını `Account` aşağıdaki kodla değiştirin. Sınıf tanımları *otomatik uygulanan özellikleri*kullanır. Daha fazla bilgi için otomatik [olarak uygulanan özellikler'e](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md)bakın.

     [!code-csharp[csOfficeWalkthrough#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/account.cs#2)]

     [!code-vb[csOfficeWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/account.vb#2)]

3. İki hesap `bankAccounts` içeren bir liste oluşturmak için `ThisAddIn_Startup` *ThisAddIn.vb* veya *ThisAddIn.cs'daki*yönteme aşağıdaki kodu ekleyin. Liste bildirimleri *toplama başlatılmasını*kullanır. Daha fazla bilgi için [Bkz. Collection Initializers](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).

     [!code-csharp[csOfficeWalkthrough#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#3)]

     [!code-vb[csOfficeWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/thisaddin.vb#3)]

### <a name="to-export-data-to-excel"></a>Verileri Excel'e aktarmak için

1. Aynı dosyada, `ThisAddIn` sınıfa aşağıdaki yöntemi ekleyin. Yöntem, bir Excel çalışma kitabı ayarlar ve verileri ona aktarın.

     [!code-csharp[csOfficeWalkthrough#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#4)]

     [!code-vb[csOfficeWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/thisaddin.vb#4)]

     Bu yöntemde iki yeni C# özelliği kullanılmıştır. Bu özelliklerin her ikisi de Visual Basic'te zaten mevcuttur.

    - Yöntem [Ekle](<xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A>) belirli bir şablon belirtmek için *isteğe bağlı* bir parametre vardır. C# 4'te yeni olan isteğe bağlı parametreler, parametrenin varsayılan değerini kullanmak istiyorsanız, bu parametrenin bağımsız değişkenini atlayabilmenizi sağlar. Önceki örnekte bağımsız değişken gönderilmediği için varsayılan `Add` şablonu kullanır ve yeni bir çalışma kitabı oluşturur. C# önceki sürümlerinde eşdeğer ifade bir yer `excelApp.Workbooks.Add(Type.Missing)`tutucu argüman gerektirir: .

         Daha fazla bilgi için [Bkz. Adlandırılmış ve İsteğe Bağlı Bağımsız Değişkenler.](../classes-and-structs/named-and-optional-arguments.md)

    - Aralık `Range` `Offset` nesnesinin [Range](<xref:Microsoft.Office.Interop.Excel.Range>) ve özellikleri *dizine eklenmiş özellikler* özelliğini kullanır. Bu özellik, aşağıdaki tipik C# sözdizimini kullanarak COM türlerinden bu özellikleri tüketmenizi sağlar. Dizinlenmiş özellikler, nesnenin `Value` özelliğini `Range` kullanmanızı da sağlayarak özelliği `Value2` kullanma gereksinimini ortadan kaldırır. Özellik `Value` dizine eklenmiştir, ancak dizin isteğe bağlıdır. İsteğe bağlı bağımsız değişkenler ve dizine eklenmiş özellikler aşağıdaki örnekte birlikte çalışır.

         [!code-csharp[csOfficeWalkthrough#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#5)]

         Dilin önceki sürümlerinde aşağıdaki özel sözdizimi gereklidir.

         [!code-csharp[csOfficeWalkthrough#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#6)]

         Kendi dizinlenmiş özellikleri oluşturamazsınız. Özellik yalnızca varolan dizinlenmiş özelliklerin tüketimini destekler.

         Daha fazla bilgi için, [COM interop programlamada dizinlenmiş özelliklerin nasıl kullanılacağına](./how-to-use-indexed-properties-in-com-interop-rogramming.md)bakın.

2. İçeriğe uyacak şekilde `DisplayInExcel` sütun gençlerini ayarlamak için sonuna şeni ekleyin.

     [!code-csharp[csOfficeWalkthrough#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#7)]

     [!code-vb[csOfficeWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/thisaddin.vb#7)]

     Bu eklemeler C#'da başka `Object` bir özelliği gösterir: Office gibi COM ana bilgisayarlarından döndürülen değerleri tür [dinamiği](../../language-reference/builtin-types/reference-types.md)varmış gibi ele alma. Embed **Interop Türleri** varsayılan değerine `True`ayarlandığında veya montaj [-bağlantı](../../language-reference/compiler-options/link-compiler-option.md) derleyicisi seçeneği yle başvurulduğunda bu otomatik olarak gerçekleşir. Type, `dynamic` Visual Basic'te zaten mevcut olan geç bağlamayı sağlar ve C# 3.0 ve dilin önceki sürümlerinde gerekli olan açık dökümden kaçınır.

     Örneğin, `excelApp.Columns[1]` bir `Object`, `AutoFit` döndürür ve bir Excel [Aralığı](<xref:Microsoft.Office.Interop.Excel.Range>) yöntemidir. Olmadan, `dynamic`arama `excelApp.Columns[1]` yöntemiönce `Range` `AutoFit`bir örnek olarak döndürülen nesne döküm gerekir.

     [!code-csharp[csOfficeWalkthrough#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#8)]

     Interop türlerini katıştırma hakkında daha fazla bilgi için, bu konunun ilerleyen saatlerinde "PIA başvurusunu bulmak için" ve "PIA bağımlılığını geri yüklemek için" yordamlarına bakın. Hakkında `dynamic`daha fazla bilgi için [dinamik](../../language-reference/builtin-types/reference-types.md) veya [Type dinamik kullanma'ya](../types/using-type-dynamic.md)bakın.

### <a name="to-invoke-displayinexcel"></a>DisplayInExcel'i çağırmak için

1. `ThisAddIn_StartUp` Yöntemin sonuna aşağıdaki kodu ekleyin. Çağrı iki `DisplayInExcel` bağımsız değişken içerir. İlk bağımsız değişken, işlenecek hesaplar listesinin adıdır. İkinci bağımsız değişken, verilerin nasıl işlenecek olduğunu tanımlayan çok satırlı bir lambda ifadesidir. Her `ID` `balance` hesabın değerleri bitişik hücrelerde görüntülenir ve bakiye sıfırdan küçükse satır kırmızı renkte görüntülenir. Daha fazla bilgi için [Lambda İfadeleri'ne](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)bakın.

     [!code-csharp[csOfficeWalkthrough#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#9)]

     [!code-vb[csOfficeWalkthrough#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/thisaddin.vb#9)]

2. Programı çalıştırmak için F5 tuşuna basın. Hesaplardaki verileri içeren bir Excel çalışma sayfası görüntülenir.

### <a name="to-add-a-word-document"></a>Word belgesi eklemek için

1. `ThisAddIn_StartUp` Excel çalışma kitabına bağlantı içeren bir Word belgesi oluşturmak için yöntemin sonuna aşağıdaki kodu ekleyin.

     [!code-csharp[csOfficeWalkthrough#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#10)]

     [!code-vb[csOfficeWalkthrough#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/thisaddin.vb#10)]

     Bu kod, C#'daki yeni özelliklerden birkaçını gösterir: `ref` COM programlamadaki anahtar kelimeyi, adlandırılmış bağımsız değişkenleri ve isteğe bağlı bağımsız değişkenleri atlayabilme yeteneği. Bu özellikler Visual Basic'te zaten var. [PasteSpecial](<xref:Microsoft.Office.Interop.Word.Selection.PasteSpecial%2A>) yöntemi, hepsi isteğe bağlı başvuru parametreleri olarak tanımlanan yedi parametreye sahiptir. Adlandırılmış ve isteğe bağlı bağımsız değişkenler, erişmek istediğiniz parametreleri ada göre belirlemenize ve bağımsız değişkenleri yalnızca bu parametrelere göndermenize olanak tanır. Bu örnekte, Pano'daki çalışma kitabına bağlantı nın oluşturulması (parametre) `Link`ve bağlantının Word belgesinde simge (parametre) `DisplayAsIcon`olarak görüntüleneceğini belirtmek için bağımsız değişkenler gönderilir. Visual C# ayrıca bu bağımsız değişkenlerin anahtar sözcüklerini `ref` atlayabilmenizi sağlar.

### <a name="to-run-the-application"></a>Uygulamayı çalıştırmak için

1. Uygulamayı çalıştırmak için F5'e basın. Excel, `bankAccounts`'deki iki hesaptan gelen bilgileri içeren bir tablo yu başlatır ve görüntüler. Ardından, Excel tablosuna bağlantı içeren bir Word belgesi görüntülenir.

### <a name="to-clean-up-the-completed-project"></a>Tamamlanan projeyi temizlemek için

1. Visual Studio'da **Yapı** menüsünde **Çözüm Temizle'yi** tıklatın. Aksi takdirde, eklenti bilgisayarınızda Excel'i her açtığınızda çalışır.

### <a name="to-find-the-pia-reference"></a>PIA referansını bulmak için

1. Uygulamayı yeniden çalıştırın, ancak **Çözüm Temizle'yi**tıklatmayın.

2. **Başlat'ı**seçin. **Microsoft Visual \<Studio sürümünü>** bulun ve bir geliştirici komut istemi açın.

3. Visual `ildasm` Studio için Geliştirici Komut İstemi'ni yazın ve ENTER tuşuna basın. IL DASM penceresi görüntülenir.

4. IL DASM penceresindeki **Dosya** menüsünde **Dosya** > **Aç'ı**seçin. **Visual Studio \<sürümünü>** çift tıklatın ve ardından **Projeler'e**çift tıklayın. Projenizin klasörünü açın ve *proje adınız*.dll için hata ayıklama klasörüne bakın. *Proje adınızı*.dll'ye çift tıklayın. Yeni bir pencere, diğer modüllere ve derlemelere yapılan başvurulara ek olarak projenizin özniteliklerini görüntüler. Ad boşluklarının `Microsoft.Office.Interop.Excel` `Microsoft.Office.Interop.Word` ve derlemeye dahil edildiğini unutmayın. Visual Studio'da varsayılan olarak derleyici, başvurulan bir PIA'dan gereksinim duyduğunuz türleri derlemenize alır.

     Daha fazla bilgi için [bkz: Derleme İçeriklerini Görüntüleyin.](../../../standard/assembly/view-contents.md)

5. **MANIFEST** simgesine çift tıklayın. Proje tarafından başvurulan öğeleri içeren derlemeler listesini içeren bir pencere görüntülenir. `Microsoft.Office.Interop.Excel`ve `Microsoft.Office.Interop.Word` listeye dahil edilmez. Proje gereksinimleriniz derlemenize aktarıldığı türleri olduğundan, PIA'ya başvuru yapılması gerekmez. Bu, dağıtımı kolaylaştırır. PiAs kullanıcının bilgisayarında mevcut olması gerekmez ve bir uygulama PIA belirli bir sürümünün dağıtım gerektirmez çünkü, uygulamalar Office'in birden çok sürümü ile çalışmak üzere tasarlanmış olabilir, gerekli API'ler tüm sürümlerinde var olması koşuluyla .

     PI'lerin dağıtımı artık gerekli olmadığından, önceki sürümler de dahil olmak üzere Office'in birden çok sürümüyle çalışan gelişmiş senaryolarda bir uygulama oluşturabilirsiniz. Ancak, bu yalnızca kodunuz birlikte çalıştığınız Office sürümünde bulunmayan API'leri kullanmıyorsa çalışır. Belirli bir API'nin önceki bir sürümde kullanılabilir olup olmadığı her zaman açık değildir ve bu nedenle Office'in önceki sürümleriyle çalışmak önerilmez.

    > [!NOTE]
    > Office, Office 2003'ten önce PI'leri yayımlamadı. Bu nedenle, Office 2002 veya önceki sürümler için bir interop derleme oluşturmak için tek yolu COM başvuru alma gereğidir.

6. Bildirim penceresini ve derleme penceresini kapatın.

### <a name="to-restore-the-pia-dependency"></a>PIA bağımlılığını geri yüklemek için

1. **Çözüm Gezgini'nde** **Tüm Dosyaları Göster** düğmesini tıklatın. **Başvurular** klasörünü genişletin ve **Microsoft.Office.Interop.Excel'i**seçin. **Özellikler** penceresini görüntülemek için F4 tuşuna basın.

2. **Özellikler** penceresinde, **Embed Interop Türleri** özelliğini **True'dan** **False'a**değiştirin.

3. Bu yordamdaki 1 ve `Microsoft.Office.Interop.Word`2 adımlarını tekrarlayın.

4. C#'da, yöntemin sonundaki `Autofit` iki aramayı `DisplayInExcel` yorumla.

5. Projenin hala doğru çalıştığını doğrulamak için F5 tuşuna basın.

6. Derleme penceresini açmak için önceki yordamdan 1-3 adımlarını yineleyin. `Microsoft.Office.Interop.Word` Artık gömülü `Microsoft.Office.Interop.Excel` derlemeler listesinde olmadığına dikkat edin.

7. **MANIFEST** simgesine çift tıklayın ve başvurulan derlemeler listesinde ilerleyin. Her `Microsoft.Office.Interop.Word` `Microsoft.Office.Interop.Excel` ikisi de ve listede bulunmaktadır. Uygulama Excel ve Word PI'lerine başvurulduğundan ve **Embed Interop Türleri** özelliği **False**olarak ayarlandığından, her iki derlemenin de son kullanıcının bilgisayarında bulunması gerekir.

8. Visual Studio'da, tamamlanan projeyi temizlemek için **Yapı** menüsünde **Çözüm** Temizle'yi tıklatın.

## <a name="see-also"></a>Ayrıca bkz.

- [Otomatik Uygulanan Özellikler (Visual Basic)](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md)
- [Otomatik Uygulanan Özellikler (C#)](../classes-and-structs/auto-implemented-properties.md)
- [Öğe Başlatıcıları](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [Nesne ve Koleksiyon Başlatıcıları](../classes-and-structs/object-and-collection-initializers.md)
- [İsteğe Bağlı Parametreler](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)
- [Bağımsız Değişkenleri Konuma ve Ada Göre Geçirme](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md)
- [Adlandırılmış ve İsteğe Bağlı Bağımsız Değişkenler](../classes-and-structs/named-and-optional-arguments.md)
- [Erken ve Geç Ciltleme](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
- [Dinamik](../../language-reference/builtin-types/reference-types.md)
- [Tür dinamiği kullanma](../types/using-type-dynamic.md)
- [Lambda İfadeleri (Visual Basic)](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [Lambda İfadeleri (C#)](../statements-expressions-operators/lambda-expressions.md)
- [COM birlikte çalışma programlamada dizin oluşturulmuş özellikleri kullanma](./how-to-use-indexed-properties-in-com-interop-rogramming.md)
- [İzlenecek yol: Visual Studio’da Microsoft Office Bütünleştirilmiş Kodlarından Tür Bilgilerini Katıştırma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ee317478(v%3dvs.120))
- [İzlenecek yol: Yönetilen Bütünleştirilmiş Kodlardan Türler Katıştırma](../../../standard/assembly/embed-types-visual-studio.md)
- [İnceleme: Excel için İlk VSTO Eklentinizi Oluşturma](/visualstudio/vsto/walkthrough-creating-your-first-vsto-add-in-for-excel)
- [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md)
- [Birlikte çalışabilirlik](./index.md)
