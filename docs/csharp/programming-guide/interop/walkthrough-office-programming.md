---
title: 'İzlenecek yol: Office programlama (C# ve Visual Basic)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Office, programming in Visual Basic and C#
- Office programming [C#]
- Office programming [Visual Basic]
ms.assetid: 519cff31-f80b-4f0e-a56b-26358d0f8c51
ms.openlocfilehash: 76d48b588db17a712ac698b604828520e38776a9
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2019
ms.locfileid: "54223162"
---
# <a name="walkthrough-office-programming-c-and-visual-basic"></a>İzlenecek yol: Office programlama (C# ve Visual Basic)
Visual Studio, C# ve Visual Basic, Microsoft Office programlama artıran özellikleri sunar. Yararlı C# özellikleri adlandırılmış ve isteğe bağlı bağımsız değişkenler içerir ve dönüş türü değerlerinin `dynamic`. COM programlama, atlayabilirsiniz `ref` Dizinli Özellikler anahtar sözcüğü ve kazanç erişim. Visual Basic'de özellikler, lambda ifadeleri ve koleksiyon başlatıcıları deyimlerinde otomatik uygulanan özellikler içerir.

Birincil birlikte çalışma derlemeleri (PIA) kullanıcının bilgisayarına dağıtmadan COM bileşenleri ile etkileşim derlemelerin dağıtımı verir tür bilgilerin ekleme her iki dil etkinleştirin. Daha fazla bilgi için [izlenecek yol: Yönetilen derlemeler türler katıştırma](../../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md).  
  
Bu izlenecek yol bu özellikleri Office programlama bağlamında gösterir, ancak bu özelliklerin birçoğu ayrıca genel programlama yararlı olur. Bu izlenecek yolda, bir Excel çalışma kitabı oluşturmak için Excel eklentisi uygulama kullanın. Ardından, çalışma kitabının bağlantısını içeren bir Word belgesi oluşturun. Son olarak, etkinleştirme ve devre dışı PIA bağımlılık bakın.  
  
## <a name="prerequisites"></a>Önkoşullar  

Bu izlenecek yolu tamamlamak için Microsoft Office Excel ve Microsoft Office Word'ün yüklü olması gerekir.  
  
 Daha eski bir işletim sistemi kullanıyorsanız [!INCLUDE[windowsver](~/includes/windowsver-md.md)], emin [!INCLUDE[dnprdnlong](~/includes/dnprdnlong-md.md)] yüklenir.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-set-up-an-excel-add-in-application"></a>Excel eklentisi uygulama ayarlamak için  
  
1.  Visual Studio’yu çalıştırın.  
  
2.  Üzerinde **dosya** menüsünde **yeni**ve ardından **proje**.  
  
3.  İçinde **yüklü şablonlar** bölmesini genişletin **Visual Basic** veya **Visual C#**, genişletin **Office**ve sürüm yılını'ye tıklayın Office Ürün.  
  
4.  İçinde **şablonları** bölmesinde tıklayın **Excel \<sürüm > eklenti**.  
  
5.  Konum üst kısmında **şablonları** emin olmak için bölmesinde **.NET Framework 4**, veya sonraki bir sürümünü görünür **hedef Framework'ü** kutusu.  
  
6.  Projeniz için bir ad yazın **adı** kutusunda istiyorsanız.  
  
7.  **Tamam**'ı tıklatın.  
  
8.  Yeni Proje görünür **Çözüm Gezgini**.  
  
### <a name="to-add-references"></a>Başvuruları eklemek için  
  
1.  İçinde **Çözüm Gezgini**, projenizin adına sağ tıklayın ve ardından **Başvuru Ekle**. **Başvuru Ekle** iletişim kutusu görüntülenir.  
  
2.  Üzerinde **derlemeleri** sekmesinde **Microsoft.Office.Interop.Excel**, sürüm `<version>.0.0.0` (Office Ürün sürüm numaraları için bir anahtar için [Microsoft Versions](https://en.wikipedia.org/wiki/Microsoft_Office#Versions)), **bileşen adı** listelemek ve anahtar ve seçin ve CTRL tuşunu basılı tutun **Microsoft.Office.Interop.Word**, `version <version>.0.0.0`. Derlemeleri görmüyorsanız, yüklü ve görüntülenen olun gerekebilir (bkz [nasıl yapılır: Office birincil birlikte çalışma derlemelerini yükleme](/visualstudio/vsto/how-to-install-office-primary-interop-assemblies)).  
  
3.  **Tamam**'ı tıklatın.  
  
### <a name="to-add-necessary-imports-statements-or-using-directives"></a>Gerekli içeri aktarmaları deyimleri eklemeye veya using yönergeleri  
  
1.  İçinde **Çözüm Gezgini**, sağ **ThisAddIn.vb** veya **ThisAddIn.cs** dosya ve ardından **Kodu Görüntüle**.  
  
2.  Aşağıdaki `Imports` deyimleri (Visual Basic) veya `using` zaten yoksa, kod dosyasının en üstüne yönergeleri (C#).  
  
     [!code-csharp[csOfficeWalkthrough#1](../../../csharp/programming-guide/interop/codesnippet/CSharp/walkthrough-office-programming_1.cs)]

     [!code-vb[csOfficeWalkthrough#1](../../../csharp/programming-guide/interop/codesnippet/VisualBasic/walkthrough-office-programming_1.vb)]
  
### <a name="to-create-a-list-of-bank-accounts"></a>Banka hesabı listesini oluşturmak için  
  
1.  İçinde **Çözüm Gezgini**, projenizin adına sağ tıklayın, **Ekle**ve ardından **sınıfı**. C# kullanıyorsanız Visual Basic veya Account.cs kullanıyorsanız Account.vb sınıfı adı. **Ekle**'yi tıklatın.  
  
2.  Tanımını değiştirin `Account` aşağıdaki kodla sınıfı. Sınıf tanımları kullanın *otomatik uygulanan Özellikler*. Daha fazla bilgi için [Implemented Properties](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md).  
  
     [!code-csharp[csOfficeWalkthrough#2](../../../csharp/programming-guide/interop/codesnippet/CSharp/walkthrough-office-programming_2.cs)]

     [!code-vb[csOfficeWalkthrough#2](../../../csharp/programming-guide/interop/codesnippet/VisualBasic/walkthrough-office-programming_2.vb)]  
  
3.  Oluşturmak için bir `bankAccounts` iki hesap içeren liste için aşağıdaki kodu ekleyin `ThisAddIn_Startup` yönteminde *ThisAddIn.vb* veya *ThisAddIn.cs*. Liste bildirimlerini *koleksiyon başlatıcıları*. Daha fazla bilgi için [koleksiyon başlatıcıları](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).  
  
     [!code-csharp[csOfficeWalkthrough#3](../../../csharp/programming-guide/interop/codesnippet/CSharp/walkthrough-office-programming_3.cs)]

     [!code-vb[csOfficeWalkthrough#3](../../../csharp/programming-guide/interop/codesnippet/VisualBasic/walkthrough-office-programming_3.vb)]  
  
### <a name="to-export-data-to-excel"></a>Verileri Excel'e aktarmak için  
  
1.  Aynı dosyada, aşağıdaki yöntemi ekleyin `ThisAddIn` sınıfı. Yöntemi, bir Excel çalışma kitabı oluşturun ayarlar ve için verileri dışarı aktarır.  
  
     [!code-csharp[csOfficeWalkthrough#4](../../../csharp/programming-guide/interop/codesnippet/CSharp/walkthrough-office-programming_4.cs)]

     [!code-vb[csOfficeWalkthrough#4](../../../csharp/programming-guide/interop/codesnippet/VisualBasic/walkthrough-office-programming_4.vb)]  
  
     Bu yöntemi, iki yeni C# özellikleri kullanılır. Bu özelliklerin her ikisi de Visual Basic'te zaten mevcut.  
  
    -   Yöntemi [Ekle](<xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A>) sahip bir *isteğe bağlı parametre* belirli bir şablon belirtmek için. İsteğe bağlı parametreler, yeni [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)], parametrenin varsayılan değeri kullanmak istiyorsanız, bu parametreye yönelik bağımsız değişkeni atlamak sağlar. Önceki örnekte hiçbir bağımsız değişken gönderildiği `Add` varsayılan şablonu kullanır ve yeni bir çalışma kitabı oluşturur. C# ' ın önceki sürümlerinde eşdeğer deyimi bir yer tutucu bağımsız değişken gerektiriyor: `excelApp.Workbooks.Add(Type.Missing)`.  
  
         Daha fazla bilgi için [adlandırılmış ve isteğe bağlı bağımsız değişkenler](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md).  
  
    -   `Range` Ve `Offset` özelliklerini [aralığı](<xref:Microsoft.Office.Interop.Excel.Range>) nesne kullanım *özellikleri dizine* özelliği. Bu özellik, aşağıdaki tipik C# sözdizimi ile bu özellikler COM türünden kullanmasını sağlar. Dizinli Özellikler de etkinleştirmeniz kullanmanızı `Value` özelliği `Range` kullanma gereksinimini ortadan kaldırır, nesne `Value2` özelliği. `Value` Özelliği tarihine, ancak dizin isteğe bağlıdır. İsteğe bağlı bağımsız değişkenler ve dizinli özellikler aşağıdaki örnekte birlikte çalışır.  
  
         [!code-csharp[csOfficeWalkthrough#5](../../../csharp/programming-guide/interop/codesnippet/CSharp/walkthrough-office-programming_5.cs)]  
  
         Dilin önceki sürümlerinde aşağıdaki özel sözdizimini gereklidir.  
  
         [!code-csharp[csOfficeWalkthrough#6](../../../csharp/programming-guide/interop/codesnippet/CSharp/walkthrough-office-programming_6.cs)]  
  
         Dizinli Özellikler kendi oluşturulamıyor. Özelliği, yalnızca mevcut Dizinlenmiş özelliklerin tüketimini destekler.  
  
         Daha fazla bilgi için [nasıl yapılır: Özellikleri COM birlikte çalışma programlamada dizin oluşturulmuş kullanma](../../../csharp/programming-guide/interop/how-to-use-indexed-properties-in-com-interop-rogramming.md).  
  
2.  Sonuna aşağıdaki kodu ekleyin `DisplayInExcel` İçeriği sığdırmak için sütun genişliklerini ayarlamak için.  
  
     [!code-csharp[csOfficeWalkthrough#7](../../../csharp/programming-guide/interop/codesnippet/CSharp/walkthrough-office-programming_7.cs)]

     [!code-vb[csOfficeWalkthrough#7](../../../csharp/programming-guide/interop/codesnippet/VisualBasic/walkthrough-office-programming_7.vb)]  
  
     C# başka bir özellik bu eklemeleri gösterir: değerlendirmesini `Object` döndürülen Office gibi COM konaklarından türü yokmuş gibi [dinamik](../../../csharp/language-reference/keywords/dynamic.md). Bu otomatik olarak gerçekleşir, **birlikte çalışma türlerini katıştır** varsayılan değerine ayarlanır `True`, ya da eşdeğer, ne zaman derlemesi tarafından başvurulan [/link](../../../csharp/language-reference/compiler-options/link-compiler-option.md) derleyici seçeneği. Tür `dynamic` geç bağlama, zaten Visual Basic'te kullanılabilir izin verir ve Visual C# 2008 ve dilin önceki sürümlerinde gerekli açık atama önler.  
  
     Örneğin, `excelApp.Columns[1]` döndürür bir `Object`, ve `AutoFit` bir Excel [aralığı](<xref:Microsoft.Office.Interop.Excel.Range>) yöntemi. Olmadan `dynamic`, tarafından döndürülen nesne dönüştürmelisiniz `excelApp.Columns[1]` örneği olarak `Range` çağırmadan önce yöntemi `AutoFit`.  
  
     [!code-csharp[csOfficeWalkthrough#8](../../../csharp/programming-guide/interop/codesnippet/CSharp/walkthrough-office-programming_8.cs)]  
  
     Birlikte çalışma türlerini katıştırma hakkında daha fazla bilgi için yordam "PIA başvurusu bulmak için" ve "PIA bağımlılık geri yüklemek için" bölümüne bakın. Hakkında daha fazla bilgi için `dynamic`, bkz: [dinamik](../../../csharp/language-reference/keywords/dynamic.md) veya [türünü kullanarak dinamik](../../../csharp/programming-guide/types/using-type-dynamic.md).  
  
### <a name="to-invoke-displayinexcel"></a>DisplayInExcel çağırmak için  
  
1.  Sonuna aşağıdaki kodu ekleyin `ThisAddIn_StartUp` yöntemi. Çağrı `DisplayInExcel` iki bağımsız değişken içeriyor. İlk bağımsız değişken işlenecek hesaplarının listesi adıdır. İkinci bağımsız değişkeni nasıl işlenecek verileri olduğunu tanımlayan bir çok satırlı lambda ifadesidir. `ID` Ve `balance` her hesap için değerleri, bitişik hücrelerde görüntülenir ve Bakiye küçükse sıfır satır kırmızı renkte görüntülenir. Daha fazla bilgi için [Lambda ifadeleri](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
     [!code-csharp[csOfficeWalkthrough#9](../../../csharp/programming-guide/interop/codesnippet/CSharp/walkthrough-office-programming_9.cs)]

     [!code-vb[csOfficeWalkthrough#9](../../../csharp/programming-guide/interop/codesnippet/VisualBasic/walkthrough-office-programming_9.vb)]  
  
2.  Programı çalıştırmak için F5 tuşuna basın. Hesaplarından veri içeren bir Excel çalışma sayfası görünür.  
  
### <a name="to-add-a-word-document"></a>Bir Word belgesi eklemek için  
  
1.  Sonuna aşağıdaki kodu ekleyin `ThisAddIn_StartUp` Excel çalışma kitabının bağlantısını içeren bir Word belgesi oluşturmak için yöntemi.  
  
     [!code-csharp[csOfficeWalkthrough#10](../../../csharp/programming-guide/interop/codesnippet/CSharp/walkthrough-office-programming_10.cs)]

     [!code-vb[csOfficeWalkthrough#10](../../../csharp/programming-guide/interop/codesnippet/VisualBasic/walkthrough-office-programming_10.vb)]  
  
     Bu kod, C# ' deki yeni özelliklerin bazılarını gösterir: atlamak için özelliği `ref` anahtar sözcüğü COM programlama, adlandırılmış bağımsız değişkenler ve isteğe bağlı bağımsız değişkenler. Bu özellikler, Visual Basic'te zaten mevcut. [Denetlemeye](<xref:Microsoft.Office.Interop.Word.Selection.PasteSpecial%2A>) yöntemi yedi parametresi, isteğe bağlı başvuru parametreleri tanımlanan tüm vardır. Adlandırılmış ve isteğe bağlı bağımsız değişkenler adıyla erişmek ve bu parametreleri yalnızca bağımsız değişken göndermemeniz için istediğiniz parametreleri belirtmek etkinleştirin. Bu örnekte, bağımsız değişkenleri Panosu'ndaki çalışma kitabı bağlantısını oluşturulması gerektiğini belirtmek için gönderilen (parametre `Link`) ve bağlantı Word belgesinde bir simge olarak görüntülenecek olan (parametre `DisplayAsIcon`). Visual C# ayrıca sayesinde atlamak `ref` bu bağımsız değişkenler için anahtar sözcüğü.
  
### <a name="to-run-the-application"></a>Uygulamayı çalıştırmak için  
  
1.  Uygulamayı çalıştırmak için F5'e basın. Excel başlar ve iki hesap bilgileri içeren bir tablo görüntüler `bankAccounts`. Daha sonra Excel tablosuna bir bağlantı içeren bir Word belgesi görüntülenir.  
  
### <a name="to-clean-up-the-completed-project"></a>Tamamlanmış projeyi temizlemek için  
  
1.  Visual Studio'da **çözümü Temizle** üzerinde **derleme** menüsü. Aksi halde, eklentinin her saat Excel bilgisayarınızda açın çalışacaktır.  
  
### <a name="to-find-the-pia-reference"></a>PIA başvurusu bulunamıyor  
  
1.  Uygulamayı yeniden çalıştırın, ancak tıklamayın **çözümü Temizle**.  
  
2.  Seçin **Başlat**. Bulun **Microsoft Visual Studio \<sürüm >** ve bir geliştirici komut istemi açın.  
  
3.  Tür `ildasm` içinde için geliştirici komut istemi penceresi Visual Studio ve ENTER tuşuna basın. IL DASM penceresi görüntülenir.  
  
4.  Üzerinde **dosya** IL DASM penceresinde, seçim menüsünde **dosya** > **açık**. Çift **Visual Studio \<sürüm >** ve çift tıklatarak **projeleri**. Projeniz için klasörü açın ve bin/Debug klasöründe arayın *projenizin adına*.dll. Çift *projenizin adına*.dll. Yeni bir pencere diğer modül ve derlemelerdeki başvuruları ek olarak, projenizin öznitelikleri görüntüler. Bu ad alanları Not `Microsoft.Office.Interop.Excel` ve `Microsoft.Office.Interop.Word` derlemeye dahil edilir. Visual Studio'da varsayılan olarak, derleyici, derlemeye başvurulan bir PIA ihtiyacınız türlerini alır.  
  
     Daha fazla bilgi için [nasıl yapılır: Bütünleştirilmiş kod içeriklerini görüntüleme](../../../framework/app-domains/how-to-view-assembly-contents.md).  
  
5.  Çift **bildirim** simgesi. Proje tarafından başvurulan öğeleri içeren bir derleme listesi içeren bir pencere görüntülenir. `Microsoft.Office.Interop.Excel` ve `Microsoft.Office.Interop.Word` listede yer almaz. PIA başvuruları projenize derlemenizi alınan türleri olmadığı için gereklidir. Bu dağıtımı kolaylaştırır. PIA'ların kullanıcının bilgisayarında mevcut olması gerekmez ve uygulamanın bir PIA'yı belirli bir sürümünü dağıtımı gerektirmediğinden şartıyla tüm sürümlerinde gerekli API'leri mevcut uygulamaları birden çok sürümü Office ile çalışmak için tasarlanabilir .  
  
     PIA'ların dağıtımı artık gerekli olmadığından, Office, önceki sürümleri dahil olmak üzere birden çok sürümü ile çalışır, Gelişmiş senaryolarda bir uygulama oluşturabilirsiniz. Ancak, yalnızca kodunuzu çalıştığınız Office sürümü bulunmayan tüm API'leri kullanmıyorsa bu çalışır. Her zaman belirli bir API'yi Office önceki sürümleriyle birlikte çalışmaya neden önerilmez bir önceki sürümünde ve kullanılabilir olup açık değildir.  
  
    > [!NOTE]
    > Office PIA'ların Office 2003 önce yayımlamadı. Bu nedenle, Office 2002 veya önceki sürümleri için birlikte çalışma derlemesi oluşturmak için tek bir COM başvurusu içeri aktararak yoludur.  
  
6.  Bildirim penceresini ve derleme penceresini kapatın.  
  
### <a name="to-restore-the-pia-dependency"></a>PIA bağımlılık geri yüklemek için  
  
1.  İçinde **Çözüm Gezgini**, tıklayın **tüm dosyaları göster** düğmesi. Genişletin **başvuruları** klasörü ve select **Microsoft.Office.Interop.Excel**. Görüntülenecek F4 tuşuna **özellikleri** penceresi.  
  
2.  İçinde **özellikleri** penceresinde değişiklik **birlikte çalışma türlerini katıştır** özelliğinden **True** için **False**.  
  
3.  1. ve 2 için bu yordamdaki adımları yineleyin `Microsoft.Office.Interop.Word`.  
  
4.  C# dilinde iki çağrıları açıklama `Autofit` sonunda `DisplayInExcel` yöntemi.  
  
5.  Projeyi yine de düzgün şekilde çalıştığını doğrulamak için F5 tuşuna basın.  
  
6.  Derleme penceresini açmak için önceki yordamdan 1-3 adımları yineleyin. Dikkat `Microsoft.Office.Interop.Word` ve `Microsoft.Office.Interop.Excel` gömülü bütünleştirilmiş kodlar listesinde artık düzeninizin.  
  
7.  Çift **bildirim** simgesi ve listesini kaydırın başvurulan derlemeler. Her ikisi de `Microsoft.Office.Interop.Word` ve `Microsoft.Office.Interop.Excel` listede yer almaktadır. Uygulama Excel ve Word PIA'ların başvurduğundan ve **birlikte çalışma türlerini katıştır** özelliği **False**, iki derleme, son kullanıcının bilgisayarda var olmalıdır.  
  
8.  Visual Studio'da **çözümü Temizle** üzerinde **derleme** tamamlanmış projeyi temizlemek için menü.  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [Otomatik uygulanan özellikler (Visual Basic)](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md)  
- [Otomatik uygulanan özellikler (C#)](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)  
- [Öğe Başlatıcıları](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)  
- [Nesne ve Koleksiyon Başlatıcıları](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
- [İsteğe Bağlı Parametreler](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)  
- [Bağımsız Değişkenleri Konuma ve Ada Göre Geçirme](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md)  
- [Adlandırılmış ve İsteğe Bağlı Bağımsız Değişkenler](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)  
- [Erken ve Geç Bağlama](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)  
- [dynamic](../../../csharp/language-reference/keywords/dynamic.md)  
- [Tür dinamiği kullanma](../../../csharp/programming-guide/types/using-type-dynamic.md)  
- [Lambda ifadeleri (Visual Basic)](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
- [Lambda ifadeleri (C#)](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
- [Nasıl yapılır: COM birlikte çalışma programlamada dizin oluşturulmuş özellikleri kullanma](../../../csharp/programming-guide/interop/how-to-use-indexed-properties-in-com-interop-rogramming.md)  
- [İzlenecek yol: Microsoft Office derlemelerinden tür bilgilerini katıştırma](../../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-type-information-from-microsoft-office-assemblies.md)  
- [İzlenecek yol: Yönetilen derlemelerden türler katıştırma](../../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)  
- [İzlenecek yol: Excel için ilk VSTO eklentinizi oluşturma](/visualstudio/vsto/walkthrough-creating-your-first-vsto-add-in-for-excel)  
- [COM Birlikte Çalışma](../../../visual-basic/programming-guide/com-interop/index.md)  
- [Birlikte çalışabilirlik](../../../csharp/programming-guide/interop/index.md)
