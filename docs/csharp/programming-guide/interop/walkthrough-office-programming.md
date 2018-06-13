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
ms.openlocfilehash: cef2a907a8d7e6158239b88d5c8551c2c734faa0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33338643"
---
# <a name="walkthrough-office-programming-c-and-visual-basic"></a>İzlenecek yol: Office Programlama (C# ve Visual Basic)
Visual Studio, Microsoft Office programlama artıran C# ve Visual Basic özellikleri sunar. Yararlı C# özelliklerini adlandırılmış ve isteğe bağlı bağımsız değişkenler içerir ve dönüş türü değerleri `dynamic`. COM programlamada, atlayabilirsiniz `ref` Dizinli Özellikler anahtar sözcüğü ve kazanç erişim. Visual Basic'de özellikler lambda ifadeleri ve koleksiyon başlatıcıları deyimlerinde otomatik uygulanan özellikler içerir.

Her iki dilde kullanıcının bilgisayarına birincil birlikte çalışma derlemeleri (PIA) dağıtmadan COM bileşenleri ile etkileşim derlemeleri dağıtımını sağlar türü bilgilerinin katıştırma etkinleştirin. Daha fazla bilgi için bkz: [izlenecek yol: yönetilen derlemelerden türler katıştırma](https://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21).  
  
Bu yönergeler, bu özellikler Office programlama bağlamındaki gösterir, ancak bu özelliklerin de genel programlama yararlıdır. Bu kılavuzda, bir Excel çalışma kitabı oluşturmak için Excel eklenti uygulama kullanın. Ardından, çalışma kitabı bağlantısını içeren bir Word belgesi oluşturun. Son olarak, etkinleştirme ve devre dışı PIA bağımlılık konusuna bakın.  
  
## <a name="prerequisites"></a>Önkoşullar  

Bu kılavuzu tamamlamak için Microsoft Office Excel ve Microsoft Office Word'ün bilgisayarınızda yüklü olması gerekir.  
  
 Daha eski bir işletim sistemi kullanıyorsanız, [!INCLUDE[windowsver](~/includes/windowsver-md.md)], olduğundan emin olun [!INCLUDE[dnprdnlong](~/includes/dnprdnlong-md.md)] yüklenir.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-set-up-an-excel-add-in-application"></a>Excel eklentisi uygulamayı kurmak için  
  
1.  Visual Studio'yu başlatın.  
  
2.  Üzerinde **dosya** menüsündeki **yeni**ve ardından **proje**.  
  
3.  İçinde **yüklü şablonlar** bölmesini genişletin **Visual Basic** veya **Visual C#**, genişletin **Office**ve sürüm yılın'ı tıklatın Office Ürün.  
  
4.  İçinde **şablonları** bölmesinde tıklatın **Excel \<sürüm > eklenti**.  
  
5.  Ara en üstünde **şablonları** emin olmak için bölmesinde **.NET Framework 4**, veya sonraki bir sürümünü görünür **hedef Framework** kutusu.  
  
6.  Projenizde için bir ad yazın **adı** vermek istiyorsanız, kutusunda.  
  
7.  **Tamam**'ı tıklatın.  
  
8.  Yeni Proje görünür **Çözüm Gezgini**.  
  
### <a name="to-add-references"></a>Başvuruları ekleme  
  
1.  İçinde **Çözüm Gezgini**, projenizin adına sağ tıklayın ve ardından **Başvuru Ekle**. **Başvuru Ekle** iletişim kutusu görüntülenir.  
  
2.  Üzerinde **derlemeleri** sekmesine **Microsoft.Office.Interop.Excel**, sürüm `<version>.0.0.0` (Office Ürün sürüm numaralarını anahtar için bkz: [Microsoft Versions](https://en.wikipedia.org/wiki/Microsoft_Office#Versions)), **bileşen adı** listesinde ve anahtar ve seçin ve CTRL tuşunu basılı tutun **Microsoft.Office.Interop.Word**, `version <version>.0.0.0`. Derlemeleri görmüyorsanız yüklenmesini ve görüntülenen gerekebilir (bkz [nasıl yapılır: yükleme Office birincil birlikte çalışma derlemeleri](/visualstudio/vsto/how-to-install-office-primary-interop-assemblies)).  
  
3.  **Tamam**'ı tıklatın.  
  
### <a name="to-add-necessary-imports-statements-or-using-directives"></a>Gerekli içeri aktarmaları deyimleri eklemek veya yönergeleri kullanma  
  
1.  İçinde **Çözüm Gezgini**, sağ **ThisAddIn.vb** veya **ThisAddIn.cs** dosya ve ardından **görünümü kodu**.  
  
2.  Aşağıdakileri ekleyin `Imports` deyimler (Visual Basic) veya `using` yönergeleri (C#) zaten yoksa, kod dosyasının en üstüne.  
  
     [!code-csharp[csOfficeWalkthrough#1](../../../csharp/programming-guide/interop/codesnippet/CSharp/walkthrough-office-programming_1.cs)]

     [!code-vb[csOfficeWalkthrough#1](../../../csharp/programming-guide/interop/codesnippet/VisualBasic/walkthrough-office-programming_1.vb)]
  
### <a name="to-create-a-list-of-bank-accounts"></a>Banka hesapları listesini oluşturmak için  
  
1.  İçinde **Çözüm Gezgini**, projenizin adına sağ tıklayın, **Ekle**ve ardından **sınıfı**. C# kullanıyorsanız, Visual Basic veya Account.cs kullanıyorsanız Account.vb sınıfı adı. **Ekle**'yi tıklatın.  
  
2.  Tanımını değiştirin `Account` aşağıdaki kodla sınıfı. Sınıf tanımları kullanın *otomatik uygulanan Özellikler*. Daha fazla bilgi için bkz: [Auto-Implemented özellikleri](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md).  
  
     [!code-csharp[csOfficeWalkthrough#2](../../../csharp/programming-guide/interop/codesnippet/CSharp/walkthrough-office-programming_2.cs)]

     [!code-vb[csOfficeWalkthrough#2](../../../csharp/programming-guide/interop/codesnippet/VisualBasic/walkthrough-office-programming_2.vb)]  
  
3.  Oluşturmak için bir `bankAccounts` iki hesap içeren liste için aşağıdaki kodu ekleyin `ThisAddIn_Startup` yönteminde *ThisAddIn.vb* veya *ThisAddIn.cs*. Liste bildirimleri kullanmak *koleksiyon başlatıcıları*. Daha fazla bilgi için bkz: [koleksiyon başlatıcıları](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).  
  
     [!code-csharp[csOfficeWalkthrough#3](../../../csharp/programming-guide/interop/codesnippet/CSharp/walkthrough-office-programming_3.cs)]

     [!code-vb[csOfficeWalkthrough#3](../../../csharp/programming-guide/interop/codesnippet/VisualBasic/walkthrough-office-programming_3.vb)]  
  
### <a name="to-export-data-to-excel"></a>Verileri Excel'e aktarmak için  
  
1.  Aynı dosyada aşağıdaki yöntemi ekleyin `ThisAddIn` sınıfı. Yöntemi, bir Excel çalışma kitabı ayarlar ve için verileri dışa aktarır.  
  
     [!code-csharp[csOfficeWalkthrough#4](../../../csharp/programming-guide/interop/codesnippet/CSharp/walkthrough-office-programming_4.cs)]

     [!code-vb[csOfficeWalkthrough#4](../../../csharp/programming-guide/interop/codesnippet/VisualBasic/walkthrough-office-programming_4.vb)]  
  
     İki yeni C# özelliklerini Bu yöntemde kullanılır. Bu özelliklerin her ikisi de, Visual Basic'te zaten mevcut.  
  
    -   Yöntem [Ekle](https://msdn.microsoft.com/library/microsoft.office.interop.excel.workbooks.add.aspx) sahip bir *isteğe bağlı bir parametre* belirli bir şablon belirtmek için. İsteğe bağlı parametreler, yeni [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)], parametrenin varsayılan değerini kullanmak istiyorsanız, bu parametre için bağımsız değişken atlayın olanak sağlar. Önceki örnekte, bağımsız değişken gönderdiğinden `Add` yeni bir çalışma kitabı oluşturur ve varsayılan şablonu kullanır. Önceki sürümlerinde, C# eşdeğer deyimi bir yer tutucu bağımsız değişken gerektiriyor: `excelApp.Workbooks.Add(Type.Missing)`.  
  
         Daha fazla bilgi için bkz: [adlandırılmış ve isteğe bağlı bağımsız değişkenler](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md).  
  
    -   `Range` Ve `Offset` özelliklerini [aralığı](https://msdn.microsoft.com/library/microsoft.office.interop.excel.range.aspx) nesne kullanım *özellikleri dizine* özelliği. Bu özellik aşağıdaki tipik C# sözdizimi kullanarak COM türlerinden bu özellikleri kullanmasına olanak sağlar. Dizinli Özellikler de etkinleştirmeniz kullanmanızı `Value` özelliği `Range` kullanma gereksinimini ortadan nesne `Value2` özelliği. `Value` Özelliği dizine ancak dizini isteğe bağlıdır. İsteğe bağlı bağımsız değişkenler ve dizinli özellikler aşağıdaki örnekte birlikte çalışır.  
  
         [!code-csharp[csOfficeWalkthrough#5](../../../csharp/programming-guide/interop/codesnippet/CSharp/walkthrough-office-programming_5.cs)]  
  
         Dil önceki sürümlerinde aşağıdaki özel sözdizimi gereklidir.  
  
         [!code-csharp[csOfficeWalkthrough#6](../../../csharp/programming-guide/interop/codesnippet/CSharp/walkthrough-office-programming_6.cs)]  
  
         Dizinli Özellikler kendi oluşturulamıyor. Özelliği, yalnızca mevcut Dizinli Özellikler kullanımını destekler.  
  
         Daha fazla bilgi için bkz: [nasıl yapılır: kullanım dizine özelliklerinde COM birlikte çalışma programlama](../../../csharp/programming-guide/interop/how-to-use-indexed-properties-in-com-interop-rogramming.md).  
  
2.  Sonuna aşağıdaki kodu ekleyin `DisplayInExcel` içeriğin sığması için sütun genişliklerini ayarlamak için.  
  
     [!code-csharp[csOfficeWalkthrough#7](../../../csharp/programming-guide/interop/codesnippet/CSharp/walkthrough-office-programming_7.cs)]

     [!code-vb[csOfficeWalkthrough#7](../../../csharp/programming-guide/interop/codesnippet/VisualBasic/walkthrough-office-programming_7.vb)]  
  
     C# başka bir özelliği bu eklemeleri göstermek: değerlendirmesini `Object` döndürülen COM konakları Office gibi türüne sahipse gibi [dinamik](../../../csharp/language-reference/keywords/dynamic.md). Bu otomatik olarak gerçekleşir, **birlikte çalışma türlerini katıştır** , varsayılan değer olarak ayarlı `True`, ya da eşdeğer, ne zaman derlemesi tarafından başvurulan [/link](../../../csharp/language-reference/compiler-options/link-compiler-option.md) derleyici seçeneği. Tür `dynamic` geç bağlama zaten Visual Basic'te kullanılabilir sağlar ve Visual C# 2008 ve önceki sürümlerinde dilin gerekli açık atamadan kaçınan.  
  
     Örneğin, `excelApp.Columns[1]` döndüren bir `Object`, ve `AutoFit` bir Excel [aralığı](https://msdn.microsoft.com/library/microsoft.office.interop.excel.range.aspx) yöntemi. Olmadan `dynamic`, tarafından döndürülen nesne cast `excelApp.Columns[1]` örneği olarak `Range` önce yöntemi çağırmadan `AutoFit`.  
  
     [!code-csharp[csOfficeWalkthrough#8](../../../csharp/programming-guide/interop/codesnippet/CSharp/walkthrough-office-programming_8.cs)]  
  
     Birlikte çalışma türlerini katıştırma hakkında daha fazla bilgi için yordam "PIA başvuru bulmak için" ve "PIA bağımlılık geri yüklemek için" bölümüne bakın. Hakkında daha fazla bilgi için `dynamic`, bkz: [dinamik](../../../csharp/language-reference/keywords/dynamic.md) veya [türünü kullanarak dinamik](../../../csharp/programming-guide/types/using-type-dynamic.md).  
  
### <a name="to-invoke-displayinexcel"></a>DisplayInExcel çağırmak için  
  
1.  Sonuna aşağıdaki kodu ekleyin `ThisAddIn_StartUp` yöntemi. Çağrı `DisplayInExcel` iki bağımsız değişken içeriyor. İlk bağımsız değişken işlenecek hesapların listesini adıdır. İkinci bağımsız değişkeni nasıl işlenmesi için verileri olduğunu tanımlayan çok satırlı lambda ifadesi değil. `ID` Ve `balance` her hesap için değerler bitişik hücreleri görüntülenir ve Bakiye küçükse sıfır satır kırmızı olarak görüntülenir. Daha fazla bilgi için bkz: [Lambda ifadeleri](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
     [!code-csharp[csOfficeWalkthrough#9](../../../csharp/programming-guide/interop/codesnippet/CSharp/walkthrough-office-programming_9.cs)]

     [!code-vb[csOfficeWalkthrough#9](../../../csharp/programming-guide/interop/codesnippet/VisualBasic/walkthrough-office-programming_9.vb)]  
  
2.  Programı çalıştırmak için F5 tuşuna basın. Excel çalışma hesaplarından veri içeren görüntülenir.  
  
### <a name="to-add-a-word-document"></a>Word belgesine eklemek için  
  
1.  Sonuna aşağıdaki kodu ekleyin `ThisAddIn_StartUp` Excel çalışma kitabı bağlantısını içeren bir Word belgesi oluşturmak için yöntemi.  
  
     [!code-csharp[csOfficeWalkthrough#10](../../../csharp/programming-guide/interop/codesnippet/CSharp/walkthrough-office-programming_10.cs)]

     [!code-vb[csOfficeWalkthrough#10](../../../csharp/programming-guide/interop/codesnippet/VisualBasic/walkthrough-office-programming_10.vb)]  
  
     Bu kod, C# ' deki yeni özelliklerin bazıları göstermektedir: atlayın olanağı `ref` anahtar sözcüğü COM programlama, adlandırılmış bağımsız değişkenler ve isteğe bağlı bağımsız değişkenler. Visual Basic'te bu özellikleri zaten var. [Denetlemeye](https://msdn.microsoft.com/library/microsoft.office.interop.word.selection.pastespecial.aspx) yöntemi isteğe bağlı başvuru parametre olarak tanımlanan her biri yedi parametrelere sahip. Adlandırılmış ve isteğe bağlı bağımsız değişkenler ada göre erişme ve bağımsız değişkenler yalnızca bu parametreleri göndermek için istediğiniz parametreleri tanımlamanızı sağlar. Bu örnekte, çalışma kitabını panoya bağlantı oluşturulması gerektiğini belirtmek için bağımsız değişkenler gönderilen (parametre `Link`) ve simge olarak Word belgesinde görüntülenecek bağlantı olduğunu (parametre `DisplayAsIcon`). Visual C# ayrıca sağlar, atlamak `ref` bu bağımsız değişkenler için anahtar sözcük.
  
### <a name="to-run-the-application"></a>Uygulamayı çalıştırmak için  
  
1.  Uygulamayı çalıştırmak için F5 tuşuna basın. Excel başlatır ve iki hesap bilgileri içeren bir tablo görüntüler `bankAccounts`. Excel tablosuna bir bağlantı içeren bir Word belgesi görünür sonra.  
  
### <a name="to-clean-up-the-completed-project"></a>Tamamlanmış projeyi temizlemek için  
  
1.  Visual Studio'da sırasıyla **temiz çözüm** üzerinde **yapı** menüsü. Aksi takdirde, eklenti Excel bilgisayarınızda açın her zaman çalışır.  
  
### <a name="to-find-the-pia-reference"></a>PIA başvurusu bulunamıyor  
  
1.  Uygulamayı yeniden çalıştırın, ancak'a tıklamayın **temiz çözüm**.  
  
2.  Seçin **Başlat**. Bulun **Microsoft Visual Studio \<sürüm >** ve bir geliştirici komut istemi açın.  
  
3.  Tür `ildasm` Visual Studio komut istemi penceresinde ve ENTER tuşuna BASIN. IL DASM penceresi görüntülenir.  
  
4.  Üzerinde **dosya** menüsünü seçin IL DASM penceresinde **dosya** > **açık**. Çift **Visual Studio \<sürüm >**, çift tıklayın ve ardından **projeleri**. Projeniz için klasörü açın ve bin/Debug klasöründe arayın *projenizin adına*.dll. Çift *projenizin adına*.dll. Yeni bir pencere diğer modüller ve derlemeler başvuruları ek olarak, projenizin özniteliklerini görüntüler. Bu ad alanları Not `Microsoft.Office.Interop.Excel` ve `Microsoft.Office.Interop.Word` bütünleştirilmiş kodunda dahil edilir. Visual Studio'da varsayılan olarak, derleyici, derlemeye başvurulan bir PIA gereksinim türleri alır.  
  
     Daha fazla bilgi için bkz: [nasıl yapılır: derleme içeriği görüntüle](../../../framework/app-domains/how-to-view-assembly-contents.md).  
  
5.  Çift **bildirim** simgesi. Proje tarafından başvurulan öğeleri içeren bir derleme listesi içeren bir pencere görüntülenir. `Microsoft.Office.Interop.Excel` ve `Microsoft.Office.Interop.Word` listesinde dahil edilmez. Projenizi derlemenizi aktarılan türleri, bir PIA başvuruları olmadığından gereklidir. Bu dağıtım kolaylaştırır. PIA kullanıcının bilgisayarda mevcut olması gerekmez ve uygulamanın bir PIA belirli bir sürümünü dağıtımı gerektirmediğinden koşuluyla gerekli API'leri tüm sürümlerinde mevcut uygulamaları birden çok Office sürümü ile çalışmak için tasarlanabilir .  
  
     PIA dağıtımını artık gerekli olmadığından, Office, önceki sürümleri de dahil olmak üzere birden çok sürümü ile çalışır, Gelişmiş senaryolarda bir uygulama oluşturabilirsiniz. Ancak, yalnızca kodunuzu çalıştığınız Office sürümünde kullanılamaz API'leri kullanmıyorsa bu çalışır. Her zaman belirli bir API'yi Office'in önceki sürümleriyle birlikte çalışmaya neden önerilmez kullanılabilir önceki bir sürümünü ve için olup açık değildir.  
  
    > [!NOTE]
    > Office Office 2003 önce PIA yayımlamadı. Bu nedenle, Office 2002 veya önceki sürümleri için birlikte çalışma derlemeyi oluşturmak için tek COM başvurusu içeri aktararak yoludur.  
  
6.  Bildirim penceresini ve derleme penceresini kapatın.  
  
### <a name="to-restore-the-pia-dependency"></a>PIA bağımlılık geri yüklemek için  
  
1.  İçinde **Çözüm Gezgini**, tıklatın **tüm dosyaları göster** düğmesi. Genişletme **başvuruları** klasörü ve select **Microsoft.Office.Interop.Excel**. Tuşuna basın, görüntülemek için F4 **özellikleri** penceresi.  
  
2.  İçinde **Propertie**s penceresinde, değişiklik **birlikte çalışma türlerini katıştır** özelliğinden **True** için **False**.  
  
3.  1 ve 2 için bu yordamdaki adımları yineleyin `Microsoft.Office.Interop.Word`.  
  
4.  C# ' ta iki çağrıları çıkışı açıklama `Autofit` sonunda `DisplayInExcel` yöntemi.  
  
5.  Proje hala düzgün şekilde çalıştığını doğrulamak için F5 tuşuna basın.  
  
6.  Derleme penceresini açmak için önceki yordamın 1-3 adımları yineleyin. Dikkat `Microsoft.Office.Interop.Word` ve `Microsoft.Office.Interop.Excel` artık katıştırılmış derlemeleri listede yer almaktadır.  
  
7.  Çift **bildirim** simgesi ve listesini kaydırın başvurulan derlemeler. Her ikisi de `Microsoft.Office.Interop.Word` ve `Microsoft.Office.Interop.Excel` listede yer almaktadır. Uygulama Excel ve Word PIA başvurduğundan ve **birlikte çalışma türlerini katıştır** özelliği ayarlanmış **yanlış**, her iki derlemeleri son kullanıcının bilgisayarda mevcut olması gerekir.  
  
8.  Visual Studio'da sırasıyla **temiz çözüm** üzerinde **yapı** tamamlanmış projeyi temizlemek için menüsü.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Otomatik uygulanan özellikler (Visual Basic)](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md)  
 [Otomatik uygulanan özellikler (C#)](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)  
 [Öğe Başlatıcıları](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)  
 [Nesne ve Koleksiyon Başlatıcıları](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
 [İsteğe Bağlı Parametreler](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)  
 [Bağımsız Değişkenleri Konuma ve Ada Göre Geçirme](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md)  
 [Adlandırılmış ve İsteğe Bağlı Bağımsız Değişkenler](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)  
 [Erken ve Geç Bağlama](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)  
 [dynamic](../../../csharp/language-reference/keywords/dynamic.md)  
 [Tür dinamiği kullanma](../../../csharp/programming-guide/types/using-type-dynamic.md)  
 [Lambda ifadeleri (Visual Basic)](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [Lambda ifadeleri (C#)](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
 [Nasıl yapılır: COM Birlikte Çalışma Programlamada Dizin Oluşturulmuş Özellikleri Kullanma](../../../csharp/programming-guide/interop/how-to-use-indexed-properties-in-com-interop-rogramming.md)  
 [İzlenecek yol: Microsoft Office Bütünleştirilmiş Kodlarından Tür Bilgilerini Katıştırma](https://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3(v=vs.100))  
 [İzlenecek yol: Yönetilen Bütünleştirilmiş Kodlardan Türler Katıştırma](https://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21)  
 [İnceleme: Excel için İlk VSTO Eklentinizi Oluşturma](https://msdn.microsoft.com/library/a855e2be-3ecf-4112-a7f5-ec0f7fad3b5f)  
 [COM Birlikte Çalışma](../../../visual-basic/programming-guide/com-interop/index.md)  
 [Birlikte çalışabilirlik](../../../csharp/programming-guide/interop/index.md)
