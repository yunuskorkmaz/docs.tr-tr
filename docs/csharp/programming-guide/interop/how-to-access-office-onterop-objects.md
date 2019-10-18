---
title: 'Nasıl yapılır: görsel C# özellikler kullanarak Office birlikte çalışma nesnelerine erişme- C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- optional parameters [C#], Office programming
- named and optional arguments [C#], Office programming
- dynamic [C#], Office programming
- optional arguments [C#], Office programming
- named arguments [C#], Office programming
- Office programming [C#]
ms.assetid: 041b25c2-3512-4e0f-a4ea-ceb2999e4d5e
ms.openlocfilehash: f0b763ad6b65c74b8c406fe006ef4036e70a99d4
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523558"
---
# <a name="how-to-access-office-interop-objects-by-using-visual-c-features-c-programming-guide"></a>Nasıl yapılır: Visual C# Özelliklerini Kullanarak Office Birlikte Çalışma Nesnelerine Erişim (C# Programlama Kılavuzu)

Görselde C# Office API nesnelerine erişimi basitleştiren özellikler vardır. Yeni özellikler adlandırılmış ve isteğe bağlı bağımsız değişkenler, `dynamic` adlı yeni bir tür ve COM yöntemlerindeki başvuru parametrelerine bağımsız değişkenleri değer parametreleri gibi geçirme özelliği içerir.

Bu konu başlığında, Microsoft Office bir Excel çalışma sayfası oluşturan ve görüntüleyen kod yazmak için yeni özellikleri kullanacaksınız. Daha sonra, Excel çalışma sayfasına bağlı bir simge içeren bir Office Word belgesi eklemek için kod yazacaksınız.

Bu yönergeyi tamamlamak için, bilgisayarınızda yüklü Microsoft Office Excel 2007 ve Microsoft Office Word 2007 veya sonraki sürümlerin olması gerekir.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-a-new-console-application"></a>Yeni bir konsol uygulaması oluşturmak için

1. Visual Studio 'Yu başlatın.

2. **Dosya** menüsünde, **Yeni**' nin üzerine gelin ve ardından **Proje**' ye tıklayın. **Yeni proje** iletişim kutusu görüntülenir.

3. **Yüklü şablonlar** bölmesinde, **görsel C#** ' i genişletin ve ardından **Windows**' a tıklayın.

4. **.NET Framework 4** ' ün (veya sonraki bir sürüm) hedef çerçeve olarak seçildiğinden emin olmak Için **Yeni proje** iletişim kutusunun üst kısmına bakın.

5. **Şablonlar** bölmesinde **konsol uygulaması**' na tıklayın.

6. **Ad** alanına projeniz için bir ad yazın.

7. **Tamam**'a tıklayın.

     Yeni proje **Çözüm Gezgini**görüntülenir.

## <a name="to-add-references"></a>Başvuru eklemek için

1. **Çözüm Gezgini**, projenizin adına sağ tıklayın ve ardından **Başvuru Ekle**' ye tıklayın. **Başvuru Ekle** iletişim kutusu görüntülenir.

2. **Derlemeler** sayfasında, **bileşen adı** listesinde **Microsoft. Office. Interop. Word** ' ü seçin ve ardından CTRL tuşunu basılı tutarak **Microsoft. Office. Interop. Excel**' i seçin.  Derlemeleri görmüyorsanız bunların yüklendiğinden ve görüntülendiğinden emin olmanız gerekebilir. Bkz. [nasıl yapılır: Office birincil birlikte çalışma derlemelerini yüklemek](/visualstudio/vsto/how-to-install-office-primary-interop-assemblies).

3. **Tamam**'a tıklayın.

## <a name="to-add-necessary-using-directives"></a>Gerekli yönergeleri kullanarak ekleme

1. **Çözüm Gezgini**, *program.cs* dosyasına sağ tıklayın ve ardından **kodu görüntüle**' ye tıklayın.

2. Kod dosyasının en üstüne aşağıdaki `using` yönergelerini ekleyin:

     [!code-csharp[csProgGuideOfficeHowTo#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#1)]

## <a name="to-create-a-list-of-bank-accounts"></a>Banka hesaplarının bir listesini oluşturmak için

1. Aşağıdaki sınıf tanımını `Program` sınıfının altındaki **program.cs**içine yapıştırın.

     [!code-csharp[csProgGuideOfficeHowTo#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#2)]

2. İki hesap içeren bir `bankAccounts` listesi oluşturmak için `Main` yöntemine aşağıdaki kodu ekleyin.

     [!code-csharp[csProgGuideOfficeHowTo#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#3)]

## <a name="to-declare-a-method-that-exports-account-information-to-excel"></a>Excel 'e hesap bilgilerini veren bir yöntem bildirmek için

1. Bir Excel çalışma sayfası ayarlamak için aşağıdaki yöntemi `Program` sınıfına ekleyin.

     @No__t_0 yöntemi, belirli bir şablonu belirtmek için isteğe bağlı bir parametreye sahiptir. 4 ' te C# yeni olan isteğe bağlı parametreler, parametrenin varsayılan değerini kullanmak istiyorsanız bu parametreye ilişkin bağımsız değişkeni atlamanızı sağlar. Aşağıdaki kodda bir bağımsız değişken gönderilmediğinden, `Add` varsayılan şablonu kullanır ve yeni bir çalışma kitabı oluşturur. Önceki sürümlerindeki denk ifade, bir yer C# tutucu bağımsız değişkeni gerektirir: `ExcelApp.Workbooks.Add(Type.Missing)`.

     [!code-csharp[csProgGuideOfficeHowTo#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#4)]

2. @No__t_0 sonuna aşağıdaki kodu ekleyin. Kod, çalışma sayfasının ilk satırının ilk iki sütununa değer ekler.

     [!code-csharp[csProgGuideOfficeHowTo#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#5)]

3. @No__t_0 sonuna aşağıdaki kodu ekleyin. @No__t_0 döngüsü, hesap listesindeki bilgileri, çalışma sayfasının Art arda gelen satırlarının ilk iki sütununa koyar.

     [!code-csharp[csProgGuideOfficeHowTo#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#7)]

4. Sütun genişliklerini içeriğe uyacak şekilde ayarlamak için `DisplayInExcel` sonuna aşağıdaki kodu ekleyin.

     [!code-csharp[csProgGuideOfficeHowTo#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#13)]

     Önceki sürümleri bu C# işlemler için açık atama gerektirir çünkü `ExcelApp.Columns[1]` bir `Object` döndürdüğünden `AutoFit` bir Excel <xref:Microsoft.Office.Interop.Excel.Range> yöntemidir. Aşağıdaki satırlarda atama gösterilmektedir.

     [!code-csharp[csProgGuideOfficeHowTo#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#14)]

     C#4 ve sonraki sürümlerde, derleme [-Link](../../language-reference/compiler-options/link-compiler-option.md) derleyici seçeneği tarafından başvuruluyorsa veya equivalently, Excel **birlikte çalışma türleri** özelliği true olarak ayarlandıysa, döndürülen `Object` otomatik olarak `dynamic` dönüştürür. True, bu özellik için varsayılan değerdir.

## <a name="to-run-the-project"></a>Projeyi çalıştırmak için

1. @No__t_0 sonuna aşağıdaki satırı ekleyin.

     [!code-csharp[csProgGuideOfficeHowTo#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#8)]

2. CTRL + F5 tuşlarına basın.

     İki hesaptan gelen verileri içeren bir Excel çalışma sayfası görüntülenir.

## <a name="to-add-a-word-document"></a>Word belgesi eklemek için

1. C# 4 ve sonraki sürümlerin, Office programlama 'yi geliştiren ek yollarını göstermek için aşağıdaki kod bir Word uygulaması açar ve Excel çalışma sayfasına bağlanan bir simge oluşturur.

     Bu adımda daha sonra belirtilen `CreateIconInWordDoc` yöntemi `Program` sınıfına yapıştırın. `CreateIconInWordDoc`, <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> ve <xref:Microsoft.Office.Interop.Word.Selection.PasteSpecial%2A> metot çağrılarının karmaşıklığını azaltmak için adlandırılmış ve isteğe bağlı bağımsız değişkenleri kullanır. Bu çağrılar, başvuru parametrelerine sahip COM yöntemlerine yapılan C# çağrıları kolaylaştıran 4 ' te tanıtılan iki yeni özelliği dahil ediyor. İlk olarak, başvuru parametrelerine bağımsız değişkenleri değer parametreleriniz gibi gönderebilirsiniz. Diğer bir deyişle, her başvuru parametresi için bir değişken oluşturmadan doğrudan değerleri gönderebilirsiniz. Derleyici bağımsız değişken değerlerini tutacak geçici değişkenler oluşturur ve çağrıdan geri döndüğünüzde değişkenleri atar. İkinci olarak, bağımsız değişken listesindeki `ref` anahtar sözcüğünü atlayabilirsiniz.

     @No__t_0 yönteminin tümü isteğe bağlı dört başvuru parametresi vardır. C# 4,0 ve sonraki sürümlerde, varsayılan değerlerini kullanmak istiyorsanız parametrelerin herhangi biri veya tümü için bağımsız değişkenleri atlayabilirsiniz. C# 3,0 ve önceki sürümlerde, her bir parametre için bir bağımsız değişken sağlanmalı ve parametreler başvuru parametreleri olduğundan bağımsız değişken bir değişken olmalıdır.

     @No__t_0 yöntemi panonun içeriğini ekler. Yönteminde, hepsi isteğe bağlı yedi başvuru parametresi vardır. Aşağıdaki kod, bunların ikisi için bağımsız değişkenler belirtir: `Link`, pano içeriklerinin kaynağına bir bağlantı oluşturmak ve bağlantıyı bir simge olarak göstermek için `DisplayAsIcon`. C# 4,0 ve sonraki sürümlerde, bu ikisi için adlandırılmış bağımsız değişkenleri kullanabilir ve diğerlerini atlayabilirsiniz. Bunlar başvuru parametreleri olsa da, `ref` anahtar sözcüğünü kullanmanız veya bağımsız değişken olarak gönderilmek üzere değişkenler oluşturmanız gerekmez. Değerleri doğrudan gönderebilirsiniz. C# 3,0 ve önceki sürümlerde, her başvuru parametresi için bir değişken bağımsız değişkeni sağlamanız gerekir.

     [!code-csharp[csProgGuideOfficeHowTo#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#9)]

     Dilin C# 3,0 ve önceki sürümlerinde, aşağıdaki daha karmaşık kod gereklidir.

     [!code-csharp[csProgGuideOfficeHowTo#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#10)]

2. @No__t_0 sonuna aşağıdaki ifadeyi ekleyin.

     [!code-csharp[csProgGuideOfficeHowTo#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#11)]

3. @No__t_0 sonuna aşağıdaki ifadeyi ekleyin. @No__t_0 yöntemi, çalışma sayfasını panoya ekler.

     [!code-csharp[csProgGuideOfficeHowTo#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#12)]

4. CTRL + F5 tuşlarına basın.

     Bir simge içeren bir Word belgesi görüntülenir. Çalışma sayfasını ön plana getirmek için simgeye çift tıklayın.

## <a name="to-set-the-embed-interop-types-property"></a>Birlikte çalışma türlerini katıştır özelliğini ayarlamak için

1. Çalışma zamanında birincil birlikte çalışma derlemesi (PIA) gerektirmeyen bir COM türünü çağırdığınızda ek geliştirmeler yapılabilir. PIA 'ların bağımlılığını kaldırmak sürüm bağımsızlık ve daha kolay dağıtıma neden olur. PIA olmadan programlamanın avantajları hakkında daha fazla bilgi için bkz. [Izlenecek yol: yönetilen derlemelerden tür ekleme](../../../standard/assembly/embed-types-visual-studio.md).

     Ayrıca, gerekli ve COM yöntemleri tarafından döndürülen türler `Object` yerine `dynamic` türü kullanılarak gösterilebildiğinden programlama kolaylaşır. Tür `dynamic` olan değişkenler çalışma zamanına kadar değerlendirilmez, bu da açık atama gereksinimini ortadan kaldırır. Daha fazla bilgi için bkz. [dinamik tür kullanımı](../types/using-type-dynamic.md).

     4 C# ' te, PIA kullanımı yerine tür bilgilerini katıştırma varsayılan davranıştır. Bu varsayılan nedenle, açık atama gerekli olmadığından önceki örneklerden bazıları basitleştirilmiştir. Örneğin, `DisplayInExcel` `worksheet` bildirimi `Excel._Worksheet workSheet = (Excel.Worksheet)excelApp.ActiveSheet` yerine `Excel._Worksheet workSheet = excelApp.ActiveSheet` olarak yazılmıştır. Aynı yöntemde `AutoFit` yapılan çağrılar, `ExcelApp.Columns[1]` bir `Object` döndürdüğünden ve `AutoFit` bir Excel yöntemi olduğundan, varsayılan olmadan açık atama gerektirir. Aşağıdaki kod, atama gösterir.

     [!code-csharp[csProgGuideOfficeHowTo#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#14)]

2. Tür bilgilerini gömmek yerine varsayılan değer değiştirmek ve PIA 'leri kullanmak için, **Çözüm Gezgini** ' deki **Başvurular** düğümünü genişletin ve ardından **Microsoft. Office. Interop. Excel** veya **Microsoft. Office. Interop. Word**öğesini seçin.

3. **Özellikler** penceresini göremiyorsanız **F4**tuşuna basın.

4. Özellik listesine **birlikte çalışma türlerini katıştır** ' ı bulun ve değerini **false**olarak değiştirin. Equivalently, bir komut isteminde [-Link](../../language-reference/compiler-options/link-compiler-option.md) yerine [-Reference](../../language-reference/compiler-options/reference-compiler-option.md) derleyici seçeneğini kullanarak derleyebilirsiniz.

## <a name="to-add-additional-formatting-to-the-table"></a>Tabloya ek biçimlendirme eklemek için

1. Aşağıdaki ifadesiyle `DisplayInExcel` `AutoFit` iki çağrısı değiştirin.

     [!code-csharp[csProgGuideOfficeHowTo#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#15)]

     @No__t_0 yöntemi, hepsi isteğe bağlı yedi değer parametresine sahiptir. Adlandırılmış ve isteğe bağlı bağımsız değişkenler hiçbiri, bazıları veya tümü için bağımsız değişkenler sağlamanıza olanak tanır. Önceki ifadede, `Format` parametrelerden yalnızca biri için bir bağımsız değişken sağlanır. @No__t_0 parametre listesindeki ilk parametre olduğundan, parametre adını belirtmeniz gerekmez. Ancak, aşağıdaki kodda gösterildiği gibi, deyimin parametre adının dahil edilip edilmediğini anlamak daha kolay olabilir.

     [!code-csharp[csProgGuideOfficeHowTo#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#16)]

2. Sonucu görmek için CTRL + F5 tuşlarına basın. Diğer biçimler <xref:Microsoft.Office.Interop.Excel.XlRangeAutoFormat> numaralandırmasında listelenmiştir.

3. Adım 1 ' deki ifadesini, C# 3,0 ve önceki sürümlerde gerekli olan bağımsız değişkenleri gösteren aşağıdaki kodla karşılaştırın.

     [!code-csharp[csProgGuideOfficeHowTo#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#17)]

## <a name="example"></a>Örnek

Aşağıdaki kod, tüm örneği göstermektedir.

[!code-csharp[csProgGuideOfficeHowTo#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/walkthrough.cs#18)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Type.Missing?displayProperty=nameWithType>
- [dynamic](../../language-reference/keywords/dynamic.md)
- [Tür dinamiği kullanma](../types/using-type-dynamic.md)
- [Adlandırılmış ve İsteğe Bağlı Bağımsız Değişkenler](../classes-and-structs/named-and-optional-arguments.md)
- [Nasıl yapılır: Office Programlamada Adlandırılmış ve İsteğe Bağlı Bağımsız Değişkenleri Kullanma](../classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)
