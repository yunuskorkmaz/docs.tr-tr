---
title: Office interop nesnelerine nasıl erişilir - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- optional parameters [C#], Office programming
- named and optional arguments [C#], Office programming
- dynamic [C#], Office programming
- optional arguments [C#], Office programming
- named arguments [C#], Office programming
- Office programming [C#]
ms.assetid: 041b25c2-3512-4e0f-a4ea-ceb2999e4d5e
ms.openlocfilehash: b5d2da011ec6318c8b07f1eb4d383a4d56488239
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75700841"
---
# <a name="how-to-access-office-interop-objects-c-programming-guide"></a>Office interop nesnelerine nasıl erişilir (C# Programlama Kılavuzu)

C#, Office API nesnelerine erişimi kolaylaştıran özelliklere sahiptir. Yeni özellikler arasında adlandırılmış ve isteğe `dynamic`bağlı bağımsız değişkenler, adı verilen yeni bir tür ve değer parametreleri yatmaktadır gibi COM yöntemlerinde başvuru parametrelerine bağımsız değişkenler geçirebilme yeteneği yer almaktadır.

Bu konuda, microsoft office excel çalışma sayfası oluşturan ve görüntüleyen kod yazmak için yeni özellikleri kullanırsınız. Daha sonra, Excel çalışma sayfasına bağlı bir simge içeren bir Office Word belgesi eklemek için kod yazarsınız.

Bu izbiyi tamamlamak için, Microsoft Office Excel 2007 ve Microsoft Office Word 2007 veya daha sonraki sürümlerinin bilgisayarınızda yüklü olması gerekir.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-a-new-console-application"></a>Yeni bir konsol uygulaması oluşturmak için

1. Visual Studio’yu çalıştırın.

2. **Dosya** menüsünde **Yeni'yi**işaret edin ve ardından **Project'i**tıklatın. **Yeni Proje** iletişim kutusu görünür.

3. Yüklü **Şablonlar** bölmesinde Visual **C#** seçeneğini genişletin ve ardından **Windows'u**tıklatın.

4. **.NET Framework 4'ün** (veya sonraki sürümün) hedef çerçeve olarak seçildiğinden emin olmak için **Yeni Proje** iletişim kutusunun en üstüne bakın.

5. **Şablonlar** bölmesinde Konsol **Uygulaması'nı**tıklatın.

6. **Ad** alanına projeniz için bir ad yazın.

7. **Tamam**'a tıklayın.

     Yeni proje Çözüm **Gezgini'nde**görünür.

## <a name="to-add-references"></a>Referans eklemek için

1. **Çözüm Gezgini'nde,** projenizin adını sağ tıklatın ve ardından **Başvuru Ekle'yi**tıklatın. **Başvuru Ekle** iletişim kutusu görüntülenir.

2. **Derlemeler** sayfasında, **Bileşen Adı** listesinde **Microsoft.Office.Interop.Word'u** seçin ve ardından CTRL tuşunu basılı tutun ve **Microsoft.Office.Interop.Excel'i**seçin.  Derlemeleri görmüyorsanız, bunların yüklendiğinden ve görüntülendiğinden emin olmanız gerekebilir. [Bkz. Nasıl: Office Birincil Interop Derlemelerini Yükleyin.](/visualstudio/vsto/how-to-install-office-primary-interop-assemblies)

3. **Tamam**'a tıklayın.

## <a name="to-add-necessary-using-directives"></a>Yönergeleri kullanarak gerekli eklemek için

1. **Çözüm Gezgini'nde,** *Program.cs* dosyasını sağ tıklatın ve ardından **Kodu Görüntüle'yi**tıklatın.

2. Kod dosyasının üst bölümüne aşağıdaki `using` yönergeleri ekleyin:

     [!code-csharp[csProgGuideOfficeHowTo#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#1)]

## <a name="to-create-a-list-of-bank-accounts"></a>Banka hesaplarının listesini oluşturmak için

1. Aşağıdaki sınıf tanımını **Program.cs**yapıştırın. `Program`

     [!code-csharp[csProgGuideOfficeHowTo#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#2)]

2. İki hesap içeren `Main` bir `bankAccounts` liste oluşturmak için yönteme aşağıdaki kodu ekleyin.

     [!code-csharp[csProgGuideOfficeHowTo#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#3)]

## <a name="to-declare-a-method-that-exports-account-information-to-excel"></a>Hesap bilgilerini Excel'e dışa aktarma yöntemini bildirmek için

1. Excel çalışma sayfası `Program` ayarlamak için sınıfa aşağıdaki yöntemi ekleyin.

     Yöntem, <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A> belirli bir şablonu belirtmek için isteğe bağlı bir parametreye sahiptir. C# 4'te yeni olan isteğe bağlı parametreler, parametrenin varsayılan değerini kullanmak istiyorsanız, bu parametrenin bağımsız değişkenini atlayabilmenizi sağlar. Aşağıdaki kodda bağımsız değişken gönderilmediği için varsayılan `Add` şablonu kullanır ve yeni bir çalışma kitabı oluşturur. C# önceki sürümlerinde eşdeğer ifade bir yer `ExcelApp.Workbooks.Add(Type.Missing)`tutucu argüman gerektirir: .

     [!code-csharp[csProgGuideOfficeHowTo#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#4)]

2. 'nin sonuna aşağıdaki kodu `DisplayInExcel`ekleyin. Kod, çalışma sayfasının ilk satırının ilk iki sütununa değerler ekler.

     [!code-csharp[csProgGuideOfficeHowTo#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#5)]

3. 'nin sonuna aşağıdaki kodu `DisplayInExcel`ekleyin. Döngü, `foreach` hesap listesindeki bilgileri çalışma sayfasının ardışık satırlarının ilk iki sütununa koyar.

     [!code-csharp[csProgGuideOfficeHowTo#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#7)]

4. İçeriğe uyacak şekilde `DisplayInExcel` sütun gençlerini ayarlamak için sonuna şeni ekleyin.

     [!code-csharp[csProgGuideOfficeHowTo#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#13)]

     C# önceki `ExcelApp.Columns[1]` sürümleri, bir `Object`,, döndürür `AutoFit` ve <xref:Microsoft.Office.Interop.Excel.Range> bir Excel yöntemi olduğundan bu işlemler için açık döküm gerektirir. Aşağıdaki satırlarda döküm göstermektedir.

     [!code-csharp[csProgGuideOfficeHowTo#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#14)]

     C# 4 ve sonraki sürümler, `Object` `dynamic` derleme [-link](../../language-reference/compiler-options/link-compiler-option.md) derleyicisi seçeneği tarafından başvurulsa veya excel **Gömme Interop Türleri** özelliği doğru ayarlanmışsa, döndürülen leri otomatik olarak dönüştürür. True, bu özellik için varsayılan değerdir.

## <a name="to-run-the-project"></a>Projeyi çalıştırmak için

1. 'nin sonuna aşağıdaki satırı `Main`ekleyin.

     [!code-csharp[csProgGuideOfficeHowTo#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#8)]

2. CTRL+F5 tuşuna basın.

     İki hesaptaki verileri içeren bir Excel çalışma sayfası görüntülenir.

## <a name="to-add-a-word-document"></a>Word belgesi eklemek için

1. C# 4 ve sonraki sürümlerin Office programlamasını geliştirdiği ek yolları göstermek için, aşağıdaki kod bir Word uygulaması açar ve Excel çalışma sayfasına bağlanan bir simge oluşturur.

     Yapıştır metodu, `CreateIconInWordDoc`daha sonra bu `Program` adımda sınıfa verilir. `CreateIconInWordDoc`çağıran yöntemin karmaşıklığını azaltmak için <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> adlandırılmış ve <xref:Microsoft.Office.Interop.Word.Selection.PasteSpecial%2A>isteğe bağlı bağımsız değişkenler kullanır ve. Bu çağrılar, c# 4'te tanıtılan ve başvuru parametreleri olan COM yöntemlerine yapılan çağrıları basitleştiren iki yeni özellik içerir. İlk olarak, bağımsız değişkenleri referans parametrelerine değer parametreleri gibi gönderebilirsiniz. Diğer bir diğer olarak, her başvuru parametresi için bir değişken oluşturmadan değerleri doğrudan gönderebilirsiniz. Derleyici bağımsız değişken değerlerini tutmak için geçici değişkenler oluşturur ve çağrıdan döndüğünüzde değişkenleri atar. İkinci olarak, bağımsız değişken `ref` listesindeki anahtar kelimeyi atlayabilirsiniz.

     Yöntem, `Add` hepsi isteğe bağlı olan dört başvuru parametresi vardır. C# 4.0 ve sonraki sürümlerde, varsayılan değerlerini kullanmak istiyorsanız parametrelerin herhangi birini veya tümünün bağımsız değişkenlerini atlayabilirsiniz. C# 3.0 ve önceki sürümlerde, her parametre için bir bağımsız değişken sağlanmalıdır ve parametreler referans parametreleri olduğundan bağımsız değişken bir değişken olmalıdır.

     Yöntem, `PasteSpecial` Pano içeriğini ekler. Yöntem, hepsi isteğe bağlı yedi başvuru parametrevardır. Aşağıdaki kod, iki tanesi için bağımsız `Link`değişkenler belirtir: , Pano içeriğinin kaynağına bir bağlantı oluşturmak ve `DisplayAsIcon`, bağlantıyı bir simge olarak görüntülemek için. C# 4.0 ve sonraki sürümlerde, bu ikisi için adlandırılmış bağımsız değişkenleri kullanabilir ve diğerlerini atlayabilirsiniz. Bunlar başvuru parametreleri olsa da, anahtar `ref` kelimeyi kullanmanız veya bağımsız değişken olarak göndermek için değişkenler oluşturmanız gerekmez. Değerleri doğrudan gönderebilirsiniz. C# 3.0 ve önceki sürümlerde, her başvuru parametresi için değişken bir bağımsız değişken sağlamanız gerekir.

     [!code-csharp[csProgGuideOfficeHowTo#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#9)]

     C# 3.0 ve dilin önceki sürümlerinde aşağıdaki daha karmaşık kod gereklidir.

     [!code-csharp[csProgGuideOfficeHowTo#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#10)]

2. 'nin sonuna aşağıdaki ifadeyi `Main`ekleyin.

     [!code-csharp[csProgGuideOfficeHowTo#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#11)]

3. 'nin sonuna aşağıdaki ifadeyi `DisplayInExcel`ekleyin. Yöntem, `Copy` çalışma sayfasını Panoya ekler.

     [!code-csharp[csProgGuideOfficeHowTo#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#12)]

4. CTRL+F5 tuşuna basın.

     Bir simge içeren bir Word belgesi görüntülenir. Çalışma sayfasını ön plana çıkarmak için simgeyi çift tıklatın.

## <a name="to-set-the-embed-interop-types-property"></a>Embed Interop Types özelliğini ayarlamak için

1. Çalışma zamanında birincil interop derlemesi (PIA) gerektirmeyen bir COM türünü çağırdığınızda ek geliştirmeler mümkündür. PIAs bağımlılığını kaldırmak sürüm bağımsızlığı ve daha kolay dağıtım sağlar. PI'siz programlamanın avantajları hakkında daha fazla bilgi için [Bkz. Walkthrough: Yönetilen Derlemelerden Türleri Gömme.](../../../standard/assembly/embed-types-visual-studio.md)

     Buna ek olarak, com yöntemleri ile gerekli ve döndürülen türleri yerine türü `dynamic` kullanılarak temsil `Object`edilebilir, çünkü programlama daha kolaydır. Türü `dynamic` olan değişkenler çalışma süresine kadar değerlendirilmez, bu da açık döküm ihtiyacını ortadan kaldırır. Daha fazla bilgi için [bkz.](../types/using-type-dynamic.md)

     C# 4'te, PI'ler kullanmak yerine tür bilgilerini katıştırma varsayılan davranıştır. Bu varsayılan nedenle, açık döküm gerekli olmadığından önceki örneklerden bazıları basitleştirilmiştir. Örneğin, `worksheet` in `DisplayInExcel` bildirimi `Excel._Worksheet workSheet = excelApp.ActiveSheet` yerine `Excel._Worksheet workSheet = (Excel.Worksheet)excelApp.ActiveSheet`yazılır. `AutoFit` Aynı yöntemde yapılan aramalar da varsayılan olmadan açık `ExcelApp.Columns[1]` döküm `Object`gerektirir, `AutoFit` çünkü bir , bir Excel yöntemi döndürür. Aşağıdaki kod döküm gösterir.

     [!code-csharp[csProgGuideOfficeHowTo#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#14)]

2. Varsayılanı değiştirmek ve tür bilgilerini katıştırmak yerine PI'leri kullanmak için **Solution Explorer'daki** **Başvuru** düğümünü genişletin ve ardından **Microsoft.Office.Interop.Excel** veya **Microsoft.Office.Interop.Word'ü**seçin.

3. **Özellikler** penceresini göremiyorsanız **F4**tuşuna basın.

4. Özellikler listesinde **Embed Interop Türlerini** bulun ve değerini **False**olarak değiştirin. Buna benzer şekilde, komut isteminde [-link](../../language-reference/compiler-options/link-compiler-option.md) yerine [-referans](../../language-reference/compiler-options/reference-compiler-option.md) derleyici seçeneğini kullanarak derleyebilirsiniz.

## <a name="to-add-additional-formatting-to-the-table"></a>Tabloya ek biçimlendirme eklemek için

1. İki aramayı `AutoFit` aşağıdaki `DisplayInExcel` ifadeyle değiştirin.

     [!code-csharp[csProgGuideOfficeHowTo#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#15)]

     Yöntem, <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> hepsi isteğe bağlı yedi değer parametresi vardır. Adlandırılmış ve isteğe bağlı bağımsız değişkenler, bunların hiçbiri, bazıları veya tümü için bağımsız değişkensağlamanızı sağlar. Önceki deyimde, bir bağımsız değişken parametrelerden yalnızca `Format`biri için verilir. Parametre listesindeki ilk parametre `Format` olduğundan, parametre adını sağlamanız gerekmez. Ancak, aşağıdaki kodda gösterildiği gibi, parametre adı dahil edilip edilmediğini anlamak daha kolay olabilir.

     [!code-csharp[csProgGuideOfficeHowTo#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#16)]

2. Sonucu görmek için CTRL+F5 tuşuna basın. Diğer biçimler numaralandırmada <xref:Microsoft.Office.Interop.Excel.XlRangeAutoFormat> listelenir.

3. 1. adımdaki ifadeyi, C# 3.0 ve önceki sürümlerde gerekli olan bağımsız değişkenleri gösteren aşağıdaki kodla karşılaştırın.

     [!code-csharp[csProgGuideOfficeHowTo#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#17)]

## <a name="example"></a>Örnek

Aşağıdaki kod tam örneği gösterir.

[!code-csharp[csProgGuideOfficeHowTo#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/walkthrough.cs#18)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Type.Missing?displayProperty=nameWithType>
- [Dinamik](../../language-reference/builtin-types/reference-types.md)
- [Tür dinamiği kullanma](../types/using-type-dynamic.md)
- [Adlandırılmış ve İsteğe Bağlı Bağımsız Değişkenler](../classes-and-structs/named-and-optional-arguments.md)
- [Office programlamada adlandırılmış ve isteğe bağlı bağımsız değişkenleri kullanma](../classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)
