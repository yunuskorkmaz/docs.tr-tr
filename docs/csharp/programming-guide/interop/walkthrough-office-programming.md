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
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635359"
---
# <a name="walkthrough-office-programming-c-and-visual-basic"></a>İzlenecek yol: Office Programlama (C# ve Visual Basic)

Visual Studio, C# ve Visual Basic Microsoft Office programlamayı geliştiren özellikler sunar. Yardımcı C# özellikler, adlandırılmış ve isteğe bağlı bağımsız değişkenleri ve `dynamic`türünde dönüş değerlerini içerir. COM programlamada `ref` anahtar sözcüğünü atlayabilir ve dizinli özelliklere erişim elde edebilirsiniz. Visual Basic Özellikler otomatik olarak uygulanan özellikler, Lambda ifadelerinde deyimler ve koleksiyon başlatıcıları içerir.

Her iki dil de, birincil birlikte çalışma derlemelerini (PIA 'lar) kullanıcının bilgisayarına dağıtmaksızın COM bileşenleriyle etkileşen derlemelerin dağıtımına izin veren tür bilgilerinin gömülmesini sağlar. Daha fazla bilgi için bkz. [Izlenecek yol: yönetilen derlemelerden tür ekleme](../../../standard/assembly/embed-types-visual-studio.md).

Bu izlenecek yol, Office programlama bağlamında bu özellikleri gösterir, ancak bu özelliklerin birçoğu genel programlamada de yararlıdır. İzlenecek yolda, Excel çalışma kitabı oluşturmak için bir Excel eklenti uygulaması kullanırsınız. Sonra, çalışma kitabının bağlantısını içeren bir Word belgesi oluşturursunuz. Son olarak, PIA bağımlılığını etkinleştirmeyi ve devre dışı bırakmayı görürsünüz.

## <a name="prerequisites"></a>Prerequisites

Bu yönergeyi tamamlamak için bilgisayarınızda Microsoft Office Excel ve Microsoft Office Word yüklü olmalıdır.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

### <a name="to-set-up-an-excel-add-in-application"></a>Excel eklenti uygulaması ayarlamak için

1. Visual Studio’yu çalıştırın.

2. **Dosya** menüsünde, **Yeni**' nin üzerine gelin ve ardından **Proje**' ye tıklayın.

3. **Yüklü şablonlar** bölmesinde, **Visual Basic** veya **Visual C#** ' i genişletin, **Office**' i genişletin ve ardından Office ürününün sürüm yılına tıklayın.

4. **Şablonlar** bölmesinde, **Excel \<sürüm > eklentisi**' ne tıklayın.

5. **.NET Framework 4**veya sonraki bir sürümün **hedef Framework** kutusunda göründüğünden emin olmak için **Şablonlar** bölmesinin en üstüne bakın.

6. İsterseniz, **ad** kutusuna projeniz için bir ad yazın.

7. **Tamam**'ı tıklatın.

8. Yeni proje **Çözüm Gezgini**görüntülenir.

### <a name="to-add-references"></a>Başvuru eklemek için

1. **Çözüm Gezgini**, projenizin adına sağ tıklayın ve ardından **Başvuru Ekle**' ye tıklayın. **Başvuru Ekle** iletişim kutusu görüntülenir.

2. **Derlemeler** sekmesinde **Microsoft. Office. Interop. Excel**, sürüm `<version>.0.0.0` (Office ürün sürüm numaralarına bir anahtar Için, bkz. [Microsoft sürümleri](https://en.wikipedia.org/wiki/Microsoft_Office#Versions)), **bileşen adı** listesinde, ve ardından CTRL tuşunu basılı tutarak **Microsoft. Office. Interop. Word**, `version <version>.0.0.0`seçeneğini belirleyin. Derlemeleri görmüyorsanız bunların yüklendiğinden ve görüntülendiklerinden emin olmanız gerekebilir (bkz. [nasıl yapılır: Office birincil birlikte çalışma derlemelerini yükleme](/visualstudio/vsto/how-to-install-office-primary-interop-assemblies)).

3. **Tamam**'ı tıklatın.

### <a name="to-add-necessary-imports-statements-or-using-directives"></a>Gerekli Içeri aktarmalar deyimlerini eklemek veya yönergeleri kullanmak için

1. **Çözüm Gezgini**, **ThisAddIn. vb** veya **ThisAddIn.cs** dosyasına sağ tıklayın ve ardından **kodu görüntüle**' ye tıklayın.

2. Zaten mevcut değilse, aşağıdaki `Imports` deyimlerini (Visual Basic) veya `using`C#yönergeleri () kod dosyasının en üstüne ekleyin.

     [!code-csharp[csOfficeWalkthrough#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#1)]

     [!code-vb[csOfficeWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/thisaddin.vb#1)]

### <a name="to-create-a-list-of-bank-accounts"></a>Banka hesaplarının bir listesini oluşturmak için

1. **Çözüm Gezgini**, projenizin adına sağ tıklayın, **Ekle**' ye ve ardından **sınıf**' a tıklayın. Kullanıyorsanız, Visual Basic veya Account.cs kullanıyorsanız,. vb sınıfını adlandırın C#. **Ekle**'yi tıklatın.

2. `Account` sınıfının tanımını aşağıdaki kodla değiştirin. Sınıf tanımları *Otomatik uygulanan özellikleri*kullanır. Daha fazla bilgi için bkz. [Otomatik uygulanan özellikler](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md).

     [!code-csharp[csOfficeWalkthrough#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/account.cs#2)]

     [!code-vb[csOfficeWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/account.vb#2)]

3. İki hesap içeren bir `bankAccounts` listesi oluşturmak için, *ThisAddIn. vb* veya *ThisAddIn.cs*içindeki `ThisAddIn_Startup` yöntemine aşağıdaki kodu ekleyin. Liste bildirimleri *koleksiyon başlatıcıları*kullanır. Daha fazla bilgi için bkz. [koleksiyon başlatıcıları](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).

     [!code-csharp[csOfficeWalkthrough#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#3)]

     [!code-vb[csOfficeWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/thisaddin.vb#3)]

### <a name="to-export-data-to-excel"></a>Excel 'e veri aktarmak için

1. Aynı dosyada, `ThisAddIn` sınıfına aşağıdaki yöntemi ekleyin. Yöntemi bir Excel çalışma kitabı ayarlar ve verileri buna dışa aktarır.

     [!code-csharp[csOfficeWalkthrough#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#4)]

     [!code-vb[csOfficeWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/thisaddin.vb#4)]

     Bu yöntemde C# iki yeni özellik kullanılır. Bu özelliklerin her ikisi de Visual Basic zaten var.

    - [Add](<xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A>) yöntemi belirli bir şablonu belirtmek için *isteğe bağlı bir parametreye* sahiptir. 4 ' te C# yeni olan isteğe bağlı parametreler, parametrenin varsayılan değerini kullanmak istiyorsanız bu parametreye ilişkin bağımsız değişkeni atlamanızı sağlar. Önceki örnekte hiçbir bağımsız değişken gönderilmediğinden, `Add` varsayılan şablonu kullanır ve yeni bir çalışma kitabı oluşturur. Önceki sürümlerindeki denk ifade, bir yer C# tutucu bağımsız değişkeni gerektirir: `excelApp.Workbooks.Add(Type.Missing)`.

         Daha fazla bilgi için bkz. [adlandırılmış ve Isteğe bağlı bağımsız değişkenler](../classes-and-structs/named-and-optional-arguments.md).

    - [Range](<xref:Microsoft.Office.Interop.Excel.Range>) nesnesinin `Range` ve `Offset` özellikleri *dizinli Özellikler* özelliğini kullanır. Bu özellik, aşağıdaki tipik C# sözdizimini kullanarak bu özellikleri com türlerinden kullanmanıza olanak sağlar. Dizinli Özellikler Ayrıca, `Value2` özelliğini kullanma gereksinimini ortadan kaldıran `Range` nesnesinin `Value` özelliğini kullanmanıza olanak sağlar. `Value` özelliği dizine alınmış, ancak dizin isteğe bağlıdır. İsteğe bağlı bağımsız değişkenler ve dizinli özellikler, aşağıdaki örnekte birlikte çalışır.

         [!code-csharp[csOfficeWalkthrough#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#5)]

         Dilin önceki sürümlerinde aşağıdaki özel sözdizimi gereklidir.

         [!code-csharp[csOfficeWalkthrough#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#6)]

         Kendinizinkini dizinli Özellikler oluşturamazsınız. Özelliği yalnızca var olan dizinli özelliklerin kullanımını destekler.

         Daha fazla bilgi için bkz. [com birlikte çalışma programlamada dizinli özellikleri kullanma](./how-to-use-indexed-properties-in-com-interop-rogramming.md).

2. Sütun genişliklerini içeriğe uyacak şekilde ayarlamak için `DisplayInExcel` sonuna aşağıdaki kodu ekleyin.

     [!code-csharp[csOfficeWalkthrough#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#7)]

     [!code-vb[csOfficeWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/thisaddin.vb#7)]

     Bu eklemeler, ' deki başka C#bir özelliği gösterir. Bu, OFFICE gibi com konaklarından döndürülen `Object` değerlerini [dinamik](../../language-reference/builtin-types/reference-types.md)tür olarak kabul ediyor. Bu, derleme [-bağlantı](../../language-reference/compiler-options/link-compiler-option.md) derleyici seçeneği tarafından başvuruluyorsa, **birlikte çalışma türleri ekle** , `True`veya equivalently gibi varsayılan değere ayarlandığında bu otomatik olarak gerçekleşir. Tür `dynamic`, geç bağlamaya izin verir, Visual Basic zaten kullanılabilir ve C# 3,0 ve önceki dil sürümlerinde gerekli olan açık dönüştürmeyi önler.

     Örneğin, `excelApp.Columns[1]` bir `Object`döndürür ve `AutoFit` bir Excel [Range](<xref:Microsoft.Office.Interop.Excel.Range>) yöntemidir. `dynamic`olmadan, yöntem `AutoFit`çağrılmadan önce `excelApp.Columns[1]` tarafından `Range` örneği olarak döndürülen nesneyi atamalısınız.

     [!code-csharp[csOfficeWalkthrough#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#8)]

     Birlikte çalışma türlerini katıştırma hakkında daha fazla bilgi için, bu konunun devamındaki "PIA başvurusunu bulmak Için" ve "PIA bağımlılığını geri yüklemek için" yordamlarına bakın. `dynamic`hakkında daha fazla bilgi için bkz. [dinamik veya](../../language-reference/builtin-types/reference-types.md) [tür dinamik kullanma](../types/using-type-dynamic.md).

### <a name="to-invoke-displayinexcel"></a>DisplayInExcel 'i çağırmak için

1. `ThisAddIn_StartUp` yönteminin sonuna aşağıdaki kodu ekleyin. `DisplayInExcel` çağrısı iki bağımsız değişken içerir. İlk bağımsız değişken işlenecek hesapların listesinin adıdır. İkinci bağımsız değişken, verilerin nasıl işleneceğini tanımlayan çok satırlı bir lambda ifadesidir. Her bir hesabın `ID` ve `balance` değerleri bitişik hücrelerde görüntülenir ve bakiye sıfırdan küçükse satır kırmızı renkte görüntülenir. Daha fazla bilgi için bkz. [lambda ifadeleri](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).

     [!code-csharp[csOfficeWalkthrough#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#9)]

     [!code-vb[csOfficeWalkthrough#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/thisaddin.vb#9)]

2. Programı çalıştırmak için F5 'e basın. Hesaplardan verileri içeren bir Excel çalışma sayfası görüntülenir.

### <a name="to-add-a-word-document"></a>Word belgesi eklemek için

1. Excel çalışma kitabına bir bağlantı içeren bir Word belgesi oluşturmak için, `ThisAddIn_StartUp` yönteminin sonuna aşağıdaki kodu ekleyin.

     [!code-csharp[csOfficeWalkthrough#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#10)]

     [!code-vb[csOfficeWalkthrough#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/thisaddin.vb#10)]

     Bu kod, içindeki C#yeni özelliklerden birkaçını gösterır: com programlama, adlandırılmış bağımsız değişkenler ve isteğe bağlı bağımsız değişkenlerle `ref` anahtar sözcüğünü atlama özelliği. Bu özellikler Visual Basic zaten var. [PasteSpecial](<xref:Microsoft.Office.Interop.Word.Selection.PasteSpecial%2A>) yönteminde yedi parametre bulunur ve bunların tümü isteğe bağlı başvuru parametresi olarak tanımlanır. Adlandırılmış ve isteğe bağlı bağımsız değişkenler, ad ile erişmek istediğiniz parametreleri tanımlamanızı ve yalnızca bu parametrelere bağımsız değişkenler göndermenizi sağlar. Bu örnekte, panodaki çalışma kitabına bir bağlantının oluşturulması gerektiğini göstermek için bağımsız değişkenler gönderilir (Parameter `Link`) ve bağlantının Word belgesinde bir simge olarak görüntülenmek (parametre `DisplayAsIcon`). Görsel C# Ayrıca bu bağımsız değişkenlerin `ref` anahtar sözcüğünü atlamanızı sağlar.

### <a name="to-run-the-application"></a>Uygulamayı çalıştırmak için

1. Uygulamayı çalıştırmak için F5'e basın. Excel başlatılır ve `bankAccounts`iki hesaptan bilgileri içeren bir tablo görüntüler. Daha sonra Excel tablosuna bir bağlantı içeren bir Word belgesi görüntülenir.

### <a name="to-clean-up-the-completed-project"></a>Tamamlanmış projeyi temizlemek için

1. Visual Studio 'da **Yapı** menüsünde **Çözümü Temizle** ' ye tıklayın. Aksi takdirde, eklenti, bilgisayarınızda Excel 'i her açışınızda çalışacaktır.

### <a name="to-find-the-pia-reference"></a>PIA başvurusunu bulmak için

1. Uygulamayı yeniden çalıştırın, ancak **Çözümü Temizle**' yi tıklamayın.

2. **Başlat**' ı seçin. **Microsoft Visual Studio \<sürüm >** bulun ve bir geliştirici komut istemi açın.

3. Visual Studio için Geliştirici Komut İstemi penceresine `ildasm` yazın ve ardından ENTER tuşuna basın. Il DADSM penceresi görüntülenir.

4. Il DAVSM penceresindeki **Dosya** menüsünde **Dosya** > **Aç**' ı seçin. **Visual Studio \<sürüm >** çift tıklayın ve ardından **Projeler**' e çift tıklayın. Projeniz için klasörü açın ve *Proje adı*. dll 'niz için bin/Debug klasörüne bakın. *Proje adı*. dll ' ye çift tıklayın. Yeni bir pencere, diğer modüller ve derlemelere başvurulara ek olarak projenizin özniteliklerini görüntüler. Ad alanlarının `Microsoft.Office.Interop.Excel` ve `Microsoft.Office.Interop.Word` derlemeye dahil edildiğini unutmayın. Visual Studio 'da varsayılan olarak, derleyici başvurulan bir PIA 'ten sizin için gerekli olan türleri derlemenizin içine aktarır.

     Daha fazla bilgi için bkz. [nasıl yapılır: derleme Içeriğini görüntüleme](../../../standard/assembly/view-contents.md).

5. **Bildirim** simgesine çift tıklayın. Proje tarafından başvurulan öğeleri içeren derlemelerin listesini içeren bir pencere görüntülenir. `Microsoft.Office.Interop.Excel` ve `Microsoft.Office.Interop.Word` listeye dahil edilmez. Projenizin gerektirdiği türler derlemenizin içine aktarıldığından, bir PIA başvuruları gerekli değildir. Bu, dağıtımı kolaylaştırır. PIA 'Lerin kullanıcının bilgisayarında mevcut olması gerekmez ve bir uygulama bir PIA 'ın belirli bir sürümünün dağıtımını gerektirmediğinden, uygulamalar, gerekli API 'Lerin tüm sürümlerde bulunması şartıyla, Office 'in birden çok sürümü ile çalışacak şekilde tasarlanabilir. .

     PIA dağıtımı artık gerekli olmadığından, önceki sürümler dahil olmak üzere birden fazla Office sürümüyle birlikte çalışarak Gelişmiş senaryolarda bir uygulama oluşturabilirsiniz. Ancak, bu yalnızca kodunuz, çalıştığınız Office sürümünde kullanılamayan API 'Leri kullanmıyorsa çalışır. Belirli bir API 'nin önceki bir sürümde kullanılabilir olup olmadığını her zaman temizlemez ve bu nedenle Office 'in önceki sürümleriyle çalışma için önerilmez.

    > [!NOTE]
    > Office, Office 2003 öncesi PIA 'Ları yayımlamadı. Bu nedenle, Office 2002 veya önceki sürümleri için birlikte çalışma derlemesi oluşturmanın tek yolu COM başvurusunu içeri aktarmadır.

6. Bildirim penceresini ve derleme penceresini kapatın.

### <a name="to-restore-the-pia-dependency"></a>PIA bağımlılığını geri yüklemek için

1. **Çözüm Gezgini**, **tüm dosyaları göster** düğmesine tıklayın. **Başvurular** klasörünü genişletin ve **Microsoft. Office. Interop. Excel**' i seçin. **Özellikler** penceresini göstermek için F4 tuşuna basın.

2. **Özellikler** penceresinde, **birlikte çalışma türlerini katıştır** özelliğini **true** değerinden **false**değerine değiştirin.

3. `Microsoft.Office.Interop.Word`için bu yordamda 1 ve 2. adımları tekrarlayın.

4. İçinde C#, `DisplayInExcel` yönteminin sonundaki `Autofit` için iki çağrısı olduğunu açıklama.

5. Projenin hala doğru şekilde çalıştığını doğrulamak için F5 tuşuna basın.

6. Önceki yordamdan derleme penceresini açmak için 1-3 arasındaki adımları yineleyin. `Microsoft.Office.Interop.Word` ve `Microsoft.Office.Interop.Excel` artık gömülü derlemeler listesinde olmadığına dikkat edin.

7. **Bildirim** simgesine çift tıklayın ve başvurulan derlemeler listesinde gezinin. `Microsoft.Office.Interop.Word` ve `Microsoft.Office.Interop.Excel` her ikisi de listede bulunur. Uygulama Excel ve Word PIAlerine başvurduğundan ve **birlikte çalışma türlerini katıştır** özelliği **false**olarak ayarlandığından, her iki derlemenin de son kullanıcının bilgisayarında bulunması gerekir.

8. Visual Studio 'da, tamamlanmış projeyi temizlemek için **derleme** menüsündeki **Çözümü Temizle** ' ye tıklayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Otomatik uygulanan Özellikler (Visual Basic)](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md)
- [Otomatik uygulanan Özellikler (C#)](../classes-and-structs/auto-implemented-properties.md)
- [Öğe Başlatıcıları](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [Nesne ve Koleksiyon Başlatıcıları](../classes-and-structs/object-and-collection-initializers.md)
- [İsteğe Bağlı Parametreler](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)
- [Bağımsız Değişkenleri Konuma ve Ada Göre Geçirme](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md)
- [Adlandırılmış ve İsteğe Bağlı Bağımsız Değişkenler](../classes-and-structs/named-and-optional-arguments.md)
- [Erken ve Geç Bağlama](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
- [dynamic](../../language-reference/builtin-types/reference-types.md)
- [Tür dinamiği kullanma](../types/using-type-dynamic.md)
- [Lambda Ifadeleri (Visual Basic)](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [Lambda Ifadeleri (C#)](../statements-expressions-operators/lambda-expressions.md)
- [COM birlikte çalışma programlamada dizinli özellikleri kullanma](./how-to-use-indexed-properties-in-com-interop-rogramming.md)
- [İzlenecek yol: Visual Studio’da Microsoft Office Bütünleştirilmiş Kodlarından Tür Bilgilerini Katıştırma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ee317478(v%3dvs.120))
- [İzlenecek yol: Yönetilen Bütünleştirilmiş Kodlardan Türler Katıştırma](../../../standard/assembly/embed-types-visual-studio.md)
- [İnceleme: Excel için İlk VSTO Eklentinizi Oluşturma](/visualstudio/vsto/walkthrough-creating-your-first-vsto-add-in-for-excel)
- [COM Birlikte Çalışma](../../../visual-basic/programming-guide/com-interop/index.md)
- [Birlikte çalışabilirlik](./index.md)
