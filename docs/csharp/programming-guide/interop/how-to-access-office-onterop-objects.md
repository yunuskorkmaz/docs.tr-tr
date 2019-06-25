---
title: 'Nasıl yapılır: Visual kullanarak Office birlikte çalışma nesnelerine erişim C# özellikleri - C# Programlama Kılavuzu'
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
ms.openlocfilehash: 9163bfa98d85a3268e154321d1aa6e55783a50f9
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2019
ms.locfileid: "67347636"
---
# <a name="how-to-access-office-interop-objects-by-using-visual-c-features-c-programming-guide"></a>Nasıl yapılır: Visual kullanarak Office birlikte çalışma nesnelerine erişim C# özellikleri (C# Programlama Kılavuzu)
Visual C# Office API'si nesnelere erişimi kolaylaştıran bir özelliğe sahiptir. Adlandırılmış ve isteğe bağlı bağımsız değişkenler, yeni özellikler olarak adlandırılan yeni türü `dynamic`ve değer parametreleri değilmiş gibi COM yöntemleri parametrelere başvuru bağımsız değişkenleri geçirmek olanağı.  
  
 Bu konuda yeni özellikler oluşturur ve bir Microsoft Office Excel çalışma sayfası görüntüleyen kod yazmak için kullanın. Ardından Excel çalışma sayfasına bağlantılı bir simge içeren bir Office Word belgesi eklemek için kod yazacaksınız.  
  
 Bu izlenecek yolu tamamlamak için Microsoft Office Excel 2007 ve Microsoft Office Word 2007 veya sonraki sürümlerinde, bilgisayarınızda yüklü olması gerekir.  
  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-create-a-new-console-application"></a>Yeni bir konsol uygulaması oluşturmak için  
  
1. Visual Studio’yu çalıştırın.  
  
2. Üzerinde **dosya** menüsünde **yeni**ve ardından **proje**. **Yeni Proje** iletişim kutusu görünür.  
  
3. İçinde **yüklü şablonlar** bölmesini genişletin **Visual C#** ve ardından **Windows**.  
  
4. Konum üst kısmında **yeni proje** emin olmak için iletişim kutusu **.NET Framework 4** (veya üzeri bir sürüm) hedef çerçeve olarak seçildiğinden.  
  
5. İçinde **şablonları** bölmesinde tıklayın **konsol uygulaması**.  
  
6. Projeniz için bir ad yazın **adı** alan.  
  
7. **Tamam**'ı tıklatın.  
  
     Yeni Proje görünür **Çözüm Gezgini**.  
  
## <a name="to-add-references"></a>Başvuruları eklemek için  
  
1. İçinde **Çözüm Gezgini**, projenizin adına sağ tıklayın ve ardından **Başvuru Ekle**. **Başvuru Ekle** iletişim kutusu görüntülenir.  
  
2. Üzerinde **derlemeleri** sayfasında **Microsoft.Office.Interop.Word** içinde **bileşen adı** listelemek ve anahtar ve seçin ve CTRL tuşunu basılı tutun  **Microsoft.Office.Interop.Excel**.  Derlemeleri görmüyorsanız, yüklü ve görüntülenen olun gerekebilir (bkz [nasıl yapılır: Office birincil birlikte çalışma derlemelerini yükleme](/visualstudio/vsto/how-to-install-office-primary-interop-assemblies))  
  
3. **Tamam**'ı tıklatın.  
  
## <a name="to-add-necessary-using-directives"></a>Eklemek için gerekli yönergeleri kullanma  
  
1. İçinde **Çözüm Gezgini**, sağ **Program.cs** dosya ve ardından **kodu görüntüle**.  
  
2. Aşağıdaki `using` kod dosyasının en üstüne yönergeleri.  
  
     [!code-csharp[csProgGuideOfficeHowTo#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#1)]  
  
## <a name="to-create-a-list-of-bank-accounts"></a>Banka hesabı listesini oluşturmak için  
  
1. Aşağıdaki sınıf tanımının içine yapıştırın **Program.cs**altında `Program` sınıfı.  
  
     [!code-csharp[csProgGuideOfficeHowTo#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#2)]  
  
2. Aşağıdaki kodu ekleyin `Main` yöntemi oluşturmak için bir `bankAccounts` iki hesap içeren liste.  
  
     [!code-csharp[csProgGuideOfficeHowTo#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#3)]  
  
## <a name="to-declare-a-method-that-exports-account-information-to-excel"></a>Hesap bilgileri Excel'e dışarı aktaran bir yöntemi bildirmek için  
  
1. Aşağıdaki yöntemi ekleyin `Program` bir Excel çalışma ayarlamak için sınıf.  
  
     Yöntemi <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A> belirli bir şablon belirtmek için isteğe bağlı parametresi vardır. İsteğe bağlı parametreler, yeni C# 4, parametrenin varsayılan değeri kullanmak istiyorsanız, bu parametreye yönelik bağımsız değişkeni atlamak etkinleştirin. Aşağıdaki kodda, hiçbir bağımsız değişken gönderildiği `Add` varsayılan şablonu kullanır ve yeni bir çalışma kitabı oluşturur. C# ' ın önceki sürümlerinde eşdeğer deyimi bir yer tutucu bağımsız değişken gerektiriyor: `ExcelApp.Workbooks.Add(Type.Missing)`.  
  
     [!code-csharp[csProgGuideOfficeHowTo#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#4)]  
  
2. Sonuna aşağıdaki kodu ekleyin `DisplayInExcel`. Kodu çalışma sayfasının ilk satırın ilk iki sütuna değerler ekler.  
  
     [!code-csharp[csProgGuideOfficeHowTo#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#5)]  
  
3. Sonuna aşağıdaki kodu ekleyin `DisplayInExcel`. `foreach` Döngü, listesinde art arda gelen satır çalışma sayfasının ilk iki sütuna bilgi hesaplarının koyar.  
  
     [!code-csharp[csProgGuideOfficeHowTo#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#7)]  
  
4. Sonuna aşağıdaki kodu ekleyin `DisplayInExcel` İçeriği sığdırmak için sütun genişliklerini ayarlamak için.  
  
     [!code-csharp[csProgGuideOfficeHowTo#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#13)]  
  
     C# ' ın önceki sürümlerinde çünkü bu açık atama için bu işlemler gerektiren `ExcelApp.Columns[1]` döndürür bir `Object`, ve `AutoFit` bir Excel <xref:Microsoft.Office.Interop.Excel.Range> yöntemi. Aşağıdaki satırları atama gösterir.  
  
     [!code-csharp[csProgGuideOfficeHowTo#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#14)]  
  
     C#4 ve üzeri sürümler dönüştürür döndürülen `Object` için `dynamic` derleme tarafından otomatik olarak başvurulan [/link](../../../csharp/language-reference/compiler-options/link-compiler-option.md) derleyici seçeneği veya eşdeğer, varsa Excel **birlikteçalışmatürlerinikatıştır** özelliği ayarlanmışsa true. Bu özellik için varsayılan değer doğrudur.  
  
## <a name="to-run-the-project"></a>Projeyi çalıştırmak için  
  
1. Aşağıdaki satırı sona Ekle `Main`.  
  
     [!code-csharp[csProgGuideOfficeHowTo#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#8)]  
  
2. CTRL + F5 tuşlarına basın.  
  
     İki hesap verileri içeren bir Excel çalışma sayfası görüntülenir.  
  
## <a name="to-add-a-word-document"></a>Bir Word belgesi eklemek için  
  
1. Ek şekillerde göstermek için C# 4 ve üzeri sürümler Office programlama geliştirir, aşağıdaki kod bir Word uygulama açılır ve bağlanan Excel çalışma sayfasına bir simge oluşturur.  
  
     Yapıştırma yöntemi `CreateIconInWordDoc`, daha sonra bu adımda, sağlanan içine `Program` sınıfı. `CreateIconInWordDoc` adlandırılmış ve isteğe bağlı bağımsız değişkenler için yöntem çağrılarının karmaşıklığını azaltmak için kullandığı <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> ve <xref:Microsoft.Office.Interop.Word.Selection.PasteSpecial%2A>. Eklenen diğer iki yeni özellikleri bu çağrılar dahil edilip derecelendirilir C# sahip bir COM yöntemlere yapılan çağrılar basitleştiren 4 başvuru parametreleri. İlk olarak, değer parametreleri değilmiş gibi bağımsız değişken başvuru parametreleri gönderebilirsiniz. Diğer bir deyişle, her başvuru parametresi için bir değişken oluşturmadan değerleri doğrudan gönderebilirsiniz. Derleyici, bağımsız değişken değerlerini tutmak için geçici değişken oluşturur ve çağrısından döndüğünüzde değişkenleri atar. İkinci olarak, atlayabilirsiniz `ref` anahtar sözcüğü bağımsız değişken listesinde.  
  
     `Add` Yöntemi her biri, isteğe bağlı, dört başvuru parametresi vardır. İçinde C# 4.0 ve üzeri sürümleri çıkarabilirsiniz tüm parametreler için bağımsız değişkenler, varsayılan değerleri kullanmak istiyorsanız. İçinde C# 3.0 ve daha önceki sürümleri, her parametre için bir bağımsız değişkeni sağlanmalı ve parametreleri başvuru parametreleri olduğundan, bağımsız değişken bir değişken olmalıdır.  
  
     `PasteSpecial` Yöntemi Pano içeriğini ekler. Yöntemi, tümü isteğe bağlı olan yedi başvuru parametresi vardır. Aşağıdaki kod iki tanesi bağımsız değişkenleri belirtir: `Link`, Pano içeriğini kaynağını bir bağlantı oluşturmak için ve `DisplayAsIcon`, bağlantı, simge olarak görüntüler. İçinde C# 4.0 ve üzeri sürümler için bu iki adlandırılmış bağımsız değişkenler kullanın ve diğerlerini atlayın. Bu başvuru parametreleri olsa da, kullanın gerekmez `ref` anahtar sözcüğü veya değişkenlerinin bağımsız değişken olarak gönderin. Değerleri doğrudan gönderebilirsiniz. İçinde C# 3.0 ve daha önceki sürümleri, her başvuru parametresi için bir değişken bağımsız değişkeni belirtmeniz gerekir.  
  
     [!code-csharp[csProgGuideOfficeHowTo#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#9)]  
  
     İçinde C# dili, aşağıdaki 3.0 ve eski sürümlerine daha karmaşık kod gereklidir.  
  
     [!code-csharp[csProgGuideOfficeHowTo#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#10)]  
  
2. Sonunda aşağıdaki ifadeyi ekleyin `Main`.  
  
     [!code-csharp[csProgGuideOfficeHowTo#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#11)]  
  
3. Sonunda aşağıdaki ifadeyi ekleyin `DisplayInExcel`. `Copy` Yöntemi çalışma panoya ekler.  
  
     [!code-csharp[csProgGuideOfficeHowTo#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#12)]  
  
4. CTRL + F5 tuşlarına basın.  
  
     Bir simge içeren bir Word belgesi görüntülenir. Çalışma sayfasında öne getirmek için simgesine çift tıklayın.  
  
## <a name="to-set-the-embed-interop-types-property"></a>Birlikte çalışma türlerini katıştır özelliğini ayarlamak için  
  
1. Ek geliştirmeler, çalışma zamanında birincil birlikte çalışma derlemesi (PIA) gerektirmeyen bir COM tür çağırdığınızda mümkündür. PIA'ların sonuçları bağımlılığı sürüm bağımsızlığı ve daha kolay dağıtım kaldırılıyor. PIA'ların programlamadan avantajları hakkında daha fazla bilgi için bkz. [izlenecek yol: Yönetilen derlemeler türler katıştırma](../../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md).  
  
     Ayrıca, gerekli ve COM yöntemleri tarafından döndürülen türleri türü kullanarak temsil edilebildiğinden programlama daha kolay `dynamic` yerine `Object`. Türü değişkenler `dynamic` açık atama ihtiyacını ortadan kaldırır çalışma zamanı kadar değerlendirilmez. Daha fazla bilgi için [türünü kullanarak dinamik](../../../csharp/programming-guide/types/using-type-dynamic.md).  
  
     İçinde C# türü ekleme 4, PIA'ların yerine bilgilerdir varsayılan davranışı. Açık atama gerekli olmadığı için bu varsayılan nedeniyle birkaç önceki örneklerin basitleştirilmiştir. Örneğin, bildirimi `worksheet` içinde `DisplayInExcel` olarak yazılan `Excel._Worksheet workSheet = excelApp.ActiveSheet` yerine `Excel._Worksheet workSheet = (Excel.Worksheet)excelApp.ActiveSheet`. Çağrıları `AutoFit` çünkü aynı yöntemi de açık atama olmadan varsayılan gerektirecek `ExcelApp.Columns[1]` döndürür bir `Object`, ve `AutoFit` bir Excel yöntemidir. Aşağıdaki kod, atama gösterir.  
  
     [!code-csharp[csProgGuideOfficeHowTo#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#14)]  
  
2. Varsayılan değiştirme ve tür bilgilerini katıştırma yerine PIA'ların kullanmak için genişletme **başvuruları** düğümünde **Çözüm Gezgini** seçip **Microsoft.Office.Interop.Excel** veya **Microsoft.Office.Interop.Word**.  
  
3. Göremiyorsanız **özellikleri** penceresinde, tuşuna **F4**.  
  
4. Bulma **birlikte çalışma türlerini katıştır** özellikler listesinde değerine değiştirip **False**. Eşdeğer, kullanarak derleyebilirsiniz [/reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md) derleyici seçeneği yerine [/link](../../../csharp/language-reference/compiler-options/link-compiler-option.md) bir komut isteminde.  
  
## <a name="to-add-additional-formatting-to-the-table"></a>Ek tablosuna biçimlendirmeyi eklemek için  
  
1. İki çağrıları değiştirin `AutoFit` içinde `DisplayInExcel` aşağıdaki deyimi.  
  
     [!code-csharp[csProgGuideOfficeHowTo#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#15)]  
  
     <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> Yöntemi her biri, isteğe bağlı, yedi değer parametresi vardır. Adlandırılmış ve isteğe bağlı bağımsız değişkenler, none, bazı veya tüm kullanımları için bağımsız değişkenleri sağlayın sağlar. Önceki tabloda parametreleri yalnızca biri için bir bağımsız değişken sağlanan `Format`. Çünkü `Format` ilk parametre parametre listesinde parametre adı sağlamanız gerekmez. Ancak, deyim parametre adı, aşağıdaki kodda gösterildiği gibi dahil olup olmadığını anlamak daha kolay olabilir.  
  
     [!code-csharp[csProgGuideOfficeHowTo#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#16)]  
  
2. Sonuçları görmek için CTRL + F5 tuşlarına basın. Diğer biçimlere listelenen <xref:Microsoft.Office.Interop.Excel.XlRangeAutoFormat> sabit listesi.  
  
3. 1\. adım gerekli bağımsız değişkenler gösteren aşağıdaki kod ile deyiminde karşılaştırma C# 3.0 ve daha önceki sürümleri.  
  
     [!code-csharp[csProgGuideOfficeHowTo#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#17)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, tam bir örnek gösterir.  
  
 [!code-csharp[csProgGuideOfficeHowTo#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/walkthrough.cs#18)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Type.Missing?displayProperty=nameWithType>
- [dynamic](../../../csharp/language-reference/keywords/dynamic.md)
- [Tür dinamiği kullanma](../../../csharp/programming-guide/types/using-type-dynamic.md)
- [Adlandırılmış ve İsteğe Bağlı Bağımsız Değişkenler](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)
- [Nasıl yapılır: Office Programlamada adlandırılmış ve isteğe bağlı bağımsız değişkenleri kullanma](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)
