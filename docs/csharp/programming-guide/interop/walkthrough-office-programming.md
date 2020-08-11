---
title: 'İzlenecek yol: Office Programlama (C# ve Visual Basic)'
description: C# ve Microsoft Office programlamayı geliştiren Visual Basic Visual Studio tekliflerinin özellikleri hakkında bilgi edinin.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Office, programming in Visual Basic and C#
- Office programming [C#]
- Office programming [Visual Basic]
ms.assetid: 519cff31-f80b-4f0e-a56b-26358d0f8c51
ms.openlocfilehash: 76f0e2eccb5d1a59d9aaa3eed11b25dd2dd9cac3
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/11/2020
ms.locfileid: "88063009"
---
# <a name="walkthrough-office-programming-c-and-visual-basic"></a>İzlenecek yol: Office Programlama (C# ve Visual Basic)

Visual Studio, C# ve Microsoft Office programlamayı geliştiren Visual Basic özellikler sunar. Yardımcı C# özellikleri adlandırılmış ve isteğe bağlı bağımsız değişkenleri ve türünün dönüş değerlerini içerir `dynamic` . COM programlamasında, `ref` anahtar sözcüğünü atlayabilir ve dizinli özelliklere erişim elde edebilirsiniz. Visual Basic Özellikler otomatik olarak uygulanan özellikler, Lambda ifadelerinde deyimler ve koleksiyon başlatıcıları içerir.

Her iki dil de, birincil birlikte çalışma derlemelerini (PIA 'lar) kullanıcının bilgisayarına dağıtmaksızın COM bileşenleriyle etkileşen derlemelerin dağıtımına izin veren tür bilgilerinin gömülmesini sağlar. Daha fazla bilgi için bkz. [Izlenecek yol: yönetilen derlemelerden tür ekleme](../../../standard/assembly/embed-types-visual-studio.md).

Bu izlenecek yol, Office programlama bağlamında bu özellikleri gösterir, ancak bu özelliklerin birçoğu genel programlamada de yararlıdır. İzlenecek yolda, Excel çalışma kitabı oluşturmak için bir Excel eklenti uygulaması kullanırsınız. Sonra, çalışma kitabının bağlantısını içeren bir Word belgesi oluşturursunuz. Son olarak, PIA bağımlılığını etkinleştirmeyi ve devre dışı bırakmayı görürsünüz.

## <a name="prerequisites"></a>Önkoşullar

Bu yönergeyi tamamlamak için bilgisayarınızda Microsoft Office Excel ve Microsoft Office Word yüklü olmalıdır.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

### <a name="to-set-up-an-excel-add-in-application"></a>Excel eklenti uygulaması ayarlamak için

1. Visual Studio’yu çalıştırın.

2. **Dosya** menüsünde, **Yeni**' nin üzerine gelin ve ardından **Proje**' ye tıklayın.

3. **Yüklü şablonlar** bölmesinde **Visual Basic** veya **Visual C#**' yi genişletin, **Office**' i genişletin ve ardından Office ürününün sürüm yılına tıklayın.

4. **Şablonlar** bölmesinde, **Excel \<version> eklentisi**' ne tıklayın.

5. **.NET Framework 4**veya sonraki bir sürümün **hedef Framework** kutusunda göründüğünden emin olmak için **Şablonlar** bölmesinin en üstüne bakın.

6. İsterseniz, **ad** kutusuna projeniz için bir ad yazın.

7. **Tamam**’a tıklayın.

8. Yeni proje **Çözüm Gezgini**görüntülenir.

### <a name="to-add-references"></a>Başvuru eklemek için

1. **Çözüm Gezgini**, projenizin adına sağ tıklayın ve ardından **Başvuru Ekle**' ye tıklayın. **Başvuru Ekle** iletişim kutusu görüntülenir.

2. **Derlemeler** sekmesinde, **Microsoft. Office. Interop. Excel**, sürüm `<version>.0.0.0` (Office ürün sürüm numaraları için bir anahtar için), **bileşen adı** listesinde, [Microsoft](https://en.wikipedia.org/wiki/Microsoft_Office#Versions) **. Office. Interop. Word**, öğesini seçin ve sonra da CTRL tuşunu basılı tutun `version <version>.0.0.0` . Derlemeleri görmüyorsanız bunların yüklendiğinden ve görüntülendiklerinden emin olmanız gerekebilir (bkz. [nasıl yapılır: Office birincil birlikte çalışma derlemelerini yükleme](/visualstudio/vsto/how-to-install-office-primary-interop-assemblies)).

3. **Tamam**’a tıklayın.

### <a name="to-add-necessary-imports-statements-or-using-directives"></a>Gerekli Içeri aktarmalar deyimlerini eklemek veya yönergeleri kullanmak için

1. **Çözüm Gezgini**, **ThisAddIn. vb** veya **ThisAddIn.cs** dosyasına sağ tıklayın ve ardından **kodu görüntüle**' ye tıklayın.

2. `Imports` `using` Zaten mevcut değilse, kod dosyasının en üstüne aşağıdaki deyimleri (Visual Basic) veya yönergeleri (C#) ekleyin.

     [!code-csharp[csOfficeWalkthrough#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#1)]

     [!code-vb[csOfficeWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/thisaddin.vb#1)]

### <a name="to-create-a-list-of-bank-accounts"></a>Banka hesaplarının bir listesini oluşturmak için

1. **Çözüm Gezgini**, projenizin adına sağ tıklayın, **Ekle**' ye ve ardından **sınıf**' a tıklayın. C# kullanıyorsanız, Visual Basic veya Account.cs kullanıyorsanız, Account. vb sınıfını adlandırın. **Ekle**'ye tıklayın.

2. `Account`Sınıfının tanımını aşağıdaki kodla değiştirin. Sınıf tanımları *Otomatik uygulanan özellikleri*kullanır. Daha fazla bilgi için bkz. [Otomatik uygulanan özellikler](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md).

     [!code-csharp[csOfficeWalkthrough#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/account.cs#2)]

     [!code-vb[csOfficeWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/account.vb#2)]

3. `bankAccounts`İki hesap içeren bir liste oluşturmak için, `ThisAddIn_Startup` *ThisAddIn. vb* veya *ThisAddIn.cs*içindeki yöntemine aşağıdaki kodu ekleyin. Liste bildirimleri *koleksiyon başlatıcıları*kullanır. Daha fazla bilgi için bkz. [koleksiyon başlatıcıları](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).

     [!code-csharp[csOfficeWalkthrough#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#3)]

     [!code-vb[csOfficeWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/thisaddin.vb#3)]

### <a name="to-export-data-to-excel"></a>Excel 'e veri aktarmak için

1. Aynı dosyada, sınıfına aşağıdaki yöntemi ekleyin `ThisAddIn` . Yöntemi bir Excel çalışma kitabı ayarlar ve verileri buna dışa aktarır.

     [!code-csharp[csOfficeWalkthrough#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#4)]

     [!code-vb[csOfficeWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/thisaddin.vb#4)]

     Bu yöntemde iki yeni C# özelliği kullanılır. Bu özelliklerin her ikisi de Visual Basic zaten var.

    - [Add](<xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A>) yöntemi belirli bir şablonu belirtmek için *isteğe bağlı bir parametreye* sahiptir. C# 4 ' te yeni olan isteğe bağlı parametreler, parametrenin varsayılan değerini kullanmak istiyorsanız bu parametreye ilişkin bağımsız değişkeni atlamanızı sağlar. Önceki örnekte hiçbir bağımsız değişken gönderilmediğinden, `Add` varsayılan şablonu kullanır ve yeni bir çalışma kitabı oluşturur. C# ' nin önceki sürümlerindeki denk ifade, bir yer tutucu bağımsız değişkeni gerektirir: `excelApp.Workbooks.Add(Type.Missing)` .

         Daha fazla bilgi için bkz. [adlandırılmış ve Isteğe bağlı bağımsız değişkenler](../classes-and-structs/named-and-optional-arguments.md).

    - `Range` `Offset` [Range](<xref:Microsoft.Office.Interop.Excel.Range>) nesnesinin ve özellikleri *dizinli Özellikler* özelliğini kullanır. Bu özellik, aşağıdaki normal C# sözdizimini kullanarak bu özellikleri COM türlerinden kullanmanıza olanak sağlar. Dizinli Özellikler Ayrıca, `Value` `Range` özelliğini kullanma gereksinimini ortadan kaldırarak nesnenin özelliğini kullanmanıza olanak sağlar `Value2` . `Value`Özelliğin dizini oluşturulmuş, ancak dizin isteğe bağlıdır. İsteğe bağlı bağımsız değişkenler ve dizinli özellikler, aşağıdaki örnekte birlikte çalışır.

         [!code-csharp[csOfficeWalkthrough#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#5)]

         Dilin önceki sürümlerinde aşağıdaki özel sözdizimi gereklidir.

         [!code-csharp[csOfficeWalkthrough#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#6)]

         Kendinizinkini dizinli Özellikler oluşturamazsınız. Özelliği yalnızca var olan dizinli özelliklerin kullanımını destekler.

         Daha fazla bilgi için bkz. [com birlikte çalışma programlamada dizinli özellikleri kullanma](./how-to-use-indexed-properties-in-com-interop-rogramming.md).

2. `DisplayInExcel`Sütunun genişliğini içeriğe sığacak şekilde ayarlamak için aşağıdaki kodu sonuna ekleyin.

     [!code-csharp[csOfficeWalkthrough#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#7)]

     [!code-vb[csOfficeWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/thisaddin.vb#7)]

     Bu eklemeler, C# ' deki başka bir özelliği gösterir: `Object` Office gıbı com konaklarından döndürülen değerleri [dinamik](../../language-reference/builtin-types/reference-types.md)tür olarak kabul ediyor. Bu otomatik olarak, **ekleme birlikte çalışma türleri** varsayılan değerine ayarlandığında, `True` veya derlemeye [-Link](../../language-reference/compiler-options/link-compiler-option.md) derleyici seçeneği tarafından başvuruluyorsa, equivalently. Tür, `dynamic` geç bağlamaya izin verir, Visual Basic ' de zaten kullanılabilir ve C# 3,0 ve önceki dil sürümlerinde gerekli olan açık dönüştürmeyi önler.

     Örneğin, `excelApp.Columns[1]` bir `Object` , ve bir `AutoFit` Excel [Range](<xref:Microsoft.Office.Interop.Excel.Range>) yöntemi döndürür. Olmadan `dynamic` , `excelApp.Columns[1]` yöntemi çağrılmadan önce bir örneği olarak döndürülen nesneyi atamalısınız `Range` `AutoFit` .

     [!code-csharp[csOfficeWalkthrough#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#8)]

     Birlikte çalışma türlerini katıştırma hakkında daha fazla bilgi için, bu konunun devamındaki "PIA başvurusunu bulmak Için" ve "PIA bağımlılığını geri yüklemek için" yordamlarına bakın. Hakkında daha fazla bilgi için `dynamic` bkz [dynamic](../../language-reference/builtin-types/reference-types.md) . dinamik veya [tür dinamik kullanımı](../types/using-type-dynamic.md).

### <a name="to-invoke-displayinexcel"></a>DisplayInExcel 'i çağırmak için

1. Yönteminin sonuna aşağıdaki kodu ekleyin `ThisAddIn_StartUp` . Çağrısı `DisplayInExcel` iki bağımsız değişken içerir. İlk bağımsız değişken işlenecek hesapların listesinin adıdır. İkinci bağımsız değişken, verilerin nasıl işleneceğini tanımlayan çok satırlı bir lambda ifadesidir. `ID`Her bir `balance` hesabın ve değerleri bitişik hücrelerde görüntülenir ve bakiye sıfırdan küçükse satır kırmızı renkte görüntülenir. Daha fazla bilgi için bkz. [lambda ifadeleri](../../language-reference/operators/lambda-expressions.md).

     [!code-csharp[csOfficeWalkthrough#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#9)]

     [!code-vb[csOfficeWalkthrough#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/thisaddin.vb#9)]

2. Programı çalıştırmak için F5 'e basın. Hesaplardan verileri içeren bir Excel çalışma sayfası görüntülenir.

### <a name="to-add-a-word-document"></a>Word belgesi eklemek için

1. `ThisAddIn_StartUp`Excel çalışma kitabının bağlantısını içeren bir Word belgesi oluşturmak için yönteminin sonuna aşağıdaki kodu ekleyin.

     [!code-csharp[csOfficeWalkthrough#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#10)]

     [!code-vb[csOfficeWalkthrough#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/thisaddin.vb#10)]

     Bu kod, C# ' deki yeni özelliklerden birkaçını gösterir: `ref` com programlamasında anahtar sözcüğü atlama özelliği, adlandırılmış bağımsız değişkenler ve isteğe bağlı bağımsız değişkenler. Bu özellikler Visual Basic zaten var. [PasteSpecial](<xref:Microsoft.Office.Interop.Word.Selection.PasteSpecial%2A>) yönteminde yedi parametre bulunur ve bunların tümü isteğe bağlı başvuru parametresi olarak tanımlanır. Adlandırılmış ve isteğe bağlı bağımsız değişkenler, ad ile erişmek istediğiniz parametreleri tanımlamanızı ve yalnızca bu parametrelere bağımsız değişkenler göndermenizi sağlar. Bu örnekte, panodaki çalışma kitabına bir bağlantının oluşturulması (parametre `Link` ) ve bağlantının Word belgesinde bir simge (parametre) olarak görüntülenmesi gerektiğini göstermek için bağımsız değişkenler gönderilir `DisplayAsIcon` . Visual C# Ayrıca `ref` Bu bağımsız değişkenlerin anahtar sözcüğünü atlamanızı sağlar.

### <a name="to-run-the-application"></a>Uygulamayı çalıştırmak için

1. Uygulamayı çalıştırmak için F5'e basın. Excel başlatılır ve içindeki iki hesaptan bilgileri içeren bir tablo görüntüler `bankAccounts` . Daha sonra Excel tablosuna bir bağlantı içeren bir Word belgesi görüntülenir.

### <a name="to-clean-up-the-completed-project"></a>Tamamlanmış projeyi temizlemek için

1. Visual Studio 'da **Yapı** menüsünde **Çözümü Temizle** ' ye tıklayın. Aksi takdirde, eklenti, bilgisayarınızda Excel 'i her açışınızda çalışacaktır.

### <a name="to-find-the-pia-reference"></a>PIA başvurusunu bulmak için

1. Uygulamayı yeniden çalıştırın, ancak **Çözümü Temizle**' yi tıklamayın.

2. **Başlat**' ı seçin. **Microsoft Visual Studio \<version> ** bulun ve bir geliştirici komut istemi açın.

3. `ildasm`Visual Studio için geliştirici komut istemi yazın ve ardından ENTER tuşuna basın. Il DADSM penceresi görüntülenir.

4. Il dadsm penceresindeki **Dosya** menüsünde **Dosya**  >  **Aç**' ı seçin. **Visual Studio \<version> **' ya çift tıklayın ve ardından **Projeler**' e çift tıklayın. Projeniz için klasörü açın ve *Proje adı*. dll 'niz için bin/Debug klasörüne bakın. *Proje adı*. dll ' ye çift tıklayın. Yeni bir pencere, diğer modüller ve derlemelere başvurulara ek olarak projenizin özniteliklerini görüntüler. Ad alanlarının `Microsoft.Office.Interop.Excel` ve `Microsoft.Office.Interop.Word` derlemeye dahil edildiğini unutmayın. Visual Studio 'da varsayılan olarak, derleyici başvurulan bir PIA 'ten sizin için gerekli olan türleri derlemenizin içine aktarır.

     Daha fazla bilgi için bkz. [nasıl yapılır: derleme Içeriğini görüntüleme](../../../standard/assembly/view-contents.md).

5. **Bildirim** simgesine çift tıklayın. Proje tarafından başvurulan öğeleri içeren derlemelerin listesini içeren bir pencere görüntülenir. `Microsoft.Office.Interop.Excel`ve `Microsoft.Office.Interop.Word` listeye dahil değildir. Projenizin gerektirdiği türler derlemenizin içine aktarıldığından, bir PIA başvuruları gerekli değildir. Bu, dağıtımı kolaylaştırır. PIA 'Lerin kullanıcının bilgisayarında mevcut olması gerekmez ve bir uygulama bir PIA 'ın belirli bir sürümünün dağıtımını gerektirmediğinden, uygulamalar, gerekli API 'Lerin tüm sürümlerde bulunması şartıyla birden fazla Office sürümüyle çalışacak şekilde tasarlanabilir.

     PIA dağıtımı artık gerekli olmadığından, önceki sürümler dahil olmak üzere birden fazla Office sürümüyle birlikte çalışarak Gelişmiş senaryolarda bir uygulama oluşturabilirsiniz. Ancak, bu yalnızca kodunuz, çalıştığınız Office sürümünde kullanılamayan API 'Leri kullanmıyorsa çalışır. Belirli bir API 'nin önceki bir sürümde kullanılabilir olup olmadığını her zaman temizlemez ve bu nedenle Office 'in önceki sürümleriyle çalışma için önerilmez.

    > [!NOTE]
    > Office, Office 2003 öncesi PIA 'Ları yayımlamadı. Bu nedenle, Office 2002 veya önceki sürümleri için birlikte çalışma derlemesi oluşturmanın tek yolu COM başvurusunu içeri aktarmadır.

6. Bildirim penceresini ve derleme penceresini kapatın.

### <a name="to-restore-the-pia-dependency"></a>PIA bağımlılığını geri yüklemek için

1. **Çözüm Gezgini**, **tüm dosyaları göster** düğmesine tıklayın. **Başvurular** klasörünü genişletin ve **Microsoft. Office. Interop. Excel**' i seçin. **Özellikler** penceresini göstermek için F4 tuşuna basın.

2. **Özellikler** penceresinde, **birlikte çalışma türlerini katıştır** özelliğini **true** değerinden **false**değerine değiştirin.

3. İçin bu yordamda 1 ve 2. adımları tekrarlayın `Microsoft.Office.Interop.Word` .

4. C# ' ta, yönteminin sonundaki iki çağrısı için açıklama ekleyin `Autofit` `DisplayInExcel` .

5. Projenin hala doğru şekilde çalıştığını doğrulamak için F5 tuşuna basın.

6. Önceki yordamdan derleme penceresini açmak için 1-3 arasındaki adımları yineleyin. Bunun, `Microsoft.Office.Interop.Word` `Microsoft.Office.Interop.Excel` gömülü derlemeler listesinde artık olmadığına dikkat edin.

7. **Bildirim** simgesine çift tıklayın ve başvurulan derlemeler listesinde gezinin. Her ikisi de `Microsoft.Office.Interop.Word` `Microsoft.Office.Interop.Excel` listede bulunur. Uygulama Excel ve Word PIAlerine başvurduğundan ve **birlikte çalışma türlerini katıştır** özelliği **false**olarak ayarlandığından, her iki derlemenin de son kullanıcının bilgisayarında bulunması gerekir.

8. Visual Studio 'da, tamamlanmış projeyi temizlemek için **derleme** menüsündeki **Çözümü Temizle** ' ye tıklayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Otomatik Uygulanan Özellikler (Visual Basic)](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md)
- [Otomatik uygulanan Özellikler (C#)](../classes-and-structs/auto-implemented-properties.md)
- [Koleksiyon Başlatıcıları](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [Nesne ve Koleksiyon Başlatıcıları](../classes-and-structs/object-and-collection-initializers.md)
- [İsteğe Bağlı Parametreler](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)
- [Bağımsız Değişkenleri Konuma ve Ada Göre Geçirme](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md)
- [Adlandırılmış ve İsteğe Bağlı Bağımsız Değişkenler](../classes-and-structs/named-and-optional-arguments.md)
- [Erken ve geç bağlama](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
- [dynamic](../../language-reference/builtin-types/reference-types.md)
- [Tür dinamiği kullanma](../types/using-type-dynamic.md)
- [Lambda İfadeleri (Visual Basic)](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [Lambda Ifadeleri (C#)](../../language-reference/operators/lambda-expressions.md)
- [COM birlikte çalışma programlamada dizin oluşturulmuş özellikleri kullanma](./how-to-use-indexed-properties-in-com-interop-rogramming.md)
- [İzlenecek yol: Visual Studio’da Microsoft Office Bütünleştirilmiş Kodlarından Tür Bilgilerini Katıştırma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ee317478(v%3dvs.120))
- [İzlenecek yol: Yönetilen Bütünleştirilmiş Kodlardan Türler Katıştırma](../../../standard/assembly/embed-types-visual-studio.md)
- [İnceleme: Excel için İlk VSTO Eklentinizi Oluşturma](/visualstudio/vsto/walkthrough-creating-your-first-vsto-add-in-for-excel)
- [COM birlikte çalışma](../../../visual-basic/programming-guide/com-interop/index.md)
- [Birlikte çalışabilirlik](./index.md)
