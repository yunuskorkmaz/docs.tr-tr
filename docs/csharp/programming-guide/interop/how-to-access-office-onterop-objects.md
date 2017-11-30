---
title: "Nasıl yapılır: Visual C# Özelliklerini Kullanarak Office Birlikte Çalışma Nesnelerine Erişim (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- optional parameters [C#], Office programming
- named and optional arguments [C#], Office programming
- dynamic [C#], Office programming
- optional arguments [C#], Office programming
- named arguments [C#], Office programming
- Office programming [C#]
ms.assetid: 041b25c2-3512-4e0f-a4ea-ceb2999e4d5e
caps.latest.revision: "33"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 25e83195d5f0d8a49e402a5a32e61940960b052a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-office-interop-objects-by-using-visual-c-features-c-programming-guide"></a>Nasıl yapılır: Visual C# Özelliklerini Kullanarak Office Birlikte Çalışma Nesnelerine Erişim (C# Programlama Kılavuzu)
Visual C# Office API nesnelerine erişimi basitleştiren özellikleri vardır. Adlandırılmış ve isteğe bağlı bağımsız değişkenler, yeni özellikleri yeni bir tür olarak adlandırılan `dynamic`ve değer parametreleri değilmiş gibi COM yöntemleri başvuru parametrelere bağımsız değişkenleri geçirme özelliği.  
  
 Bu konuda yeni özellikler oluşturur ve Microsoft Office Excel çalışma görüntüleyen kod yazmak için kullanın. Ardından Excel çalışma sayfasına bağlantılı bir simge içeren bir Office belgesine eklemek için kod yazacaksınız.  
  
 Bu kılavuzu tamamlamak için Microsoft Office Excel 2007 ve Microsoft Office Word 2007 veya sonraki sürümler, bilgisayarınızda yüklü olması gerekir.  
  
 Daha eski bir işletim sistemi kullanıyorsanız, [!INCLUDE[windowsver](~/includes/windowsver-md.md)], olduğundan emin olun [!INCLUDE[dnprdnlong](~/includes/dnprdnlong-md.md)] yüklenir.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-new-console-application"></a>Yeni bir konsol uygulaması oluşturmak için  
  
1.  Visual Studio'yu başlatın.  
  
2.  Üzerinde **dosya** menüsündeki **yeni**ve ardından **proje**. **Yeni proje** iletişim kutusu görüntülenir.  
  
3.  İçinde **yüklü şablonlar** bölmesini genişletin **Visual C#**ve ardından **Windows**.  
  
4.  Ara en üstünde **yeni proje** emin olmak için iletişim kutusu **.NET Framework 4** (veya sonraki bir sürümü) bir hedef çerçeve olarak seçildiğinden.  
  
5.  İçinde **şablonları** bölmesinde tıklatın **konsol uygulaması**.  
  
6.  Projenizde için bir ad yazın **adı** alan.  
  
7.  **Tamam**'ı tıklatın.  
  
     Yeni Proje görünür **Çözüm Gezgini**.  
  
### <a name="to-add-references"></a>Başvuruları ekleme  
  
1.  İçinde **Çözüm Gezgini**, projenizin adına sağ tıklayın ve ardından **Başvuru Ekle**. **Başvuru Ekle** iletişim kutusu görüntülenir.  
  
2.  Üzerinde **derlemeleri** sayfasında, **Microsoft.Office.Interop.Word** içinde **bileşen adı** listesinde ve anahtar ve seçin ve CTRL tuşunu basılı tutun  **Microsoft.Office.Interop.Excel**.  Derlemeleri görmüyorsanız yüklenmesini ve görüntülenen gerekebilir (bkz [nasıl yapılır: yükleme Office birincil birlikte çalışma derlemeleri](/visualstudio/vsto/how-to-install-office-primary-interop-assemblies))  
  
3.  **Tamam**'ı tıklatın.  
  
### <a name="to-add-necessary-using-directives"></a>Eklemek için gerekli yönergeleri kullanma  
  
1.  İçinde **Çözüm Gezgini**, sağ **Program.cs** dosya ve ardından **görünümü kodu**.  
  
2.  Aşağıdakileri ekleyin `using` yönergelerini kod dosyasının en üstüne.  
  
     [!code-csharp[csProgGuideOfficeHowTo#1](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_1.cs)]  
  
### <a name="to-create-a-list-of-bank-accounts"></a>Banka hesapları listesini oluşturmak için  
  
1.  Aşağıdaki sınıf tanımının içine yapıştırma **Program.cs**altında `Program` sınıfı.  
  
     [!code-csharp[csProgGuideOfficeHowTo#2](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_2.cs)]  
  
2.  Aşağıdaki kodu ekleyin `Main` yöntemi oluşturmak için bir `bankAccounts` iki hesap içeren liste.  
  
     [!code-csharp[csProgGuideOfficeHowTo#3](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_3.cs)]  
  
### <a name="to-declare-a-method-that-exports-account-information-to-excel"></a>Hesap bilgileri Excel'e verir bir yöntem bildirmek için  
  
1.  Aşağıdaki yöntemi ekleyin `Program` bir Excel çalışma ayarlamak için sınıf.  
  
     Yöntem [Ekle](http://go.microsoft.com/fwlink/?LinkId=210910) belirli bir şablon belirtmek için isteğe bağlı bir parametre içeriyor. İsteğe bağlı parametreler, yeni [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)], parametrenin varsayılan değerini kullanmak istiyorsanız, bu parametre için bağımsız değişken atlayın olanak sağlar. Bağımsız değişken aşağıdaki kodda gönderdiğinden `Add` yeni bir çalışma kitabı oluşturur ve varsayılan şablonu kullanır. Önceki sürümlerinde, C# eşdeğer deyimi bir yer tutucu bağımsız değişken gerektiriyor: `ExcelApp.Workbooks.Add(Type.Missing)`.  
  
     [!code-csharp[csProgGuideOfficeHowTo#4](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_4.cs)]  
  
2.  Sonuna aşağıdaki kodu ekleyin `DisplayInExcel`. Kodu çalışma ilk satırının ilk iki sütuna değerler ekler.  
  
     [!code-csharp[csProgGuideOfficeHowTo#5](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_5.cs)]  
  
3.  Sonuna aşağıdaki kodu ekleyin `DisplayInExcel`. `foreach` Döngü listeden çalışma sayfasının art arda satır ilk iki sütuna bilgi hesaplarının koyar.  
  
     [!code-csharp[csProgGuideOfficeHowTo#7](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_6.cs)]  
  
4.  Sonuna aşağıdaki kodu ekleyin `DisplayInExcel` içeriğin sığması için sütun genişliklerini ayarlamak için.  
  
     [!code-csharp[csProgGuideOfficeHowTo#13](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_7.cs)]  
  
     Önceki sürümleri, C# çünkü bu açık atama bu işlemler için gerekli `ExcelApp.Columns[1]` döndüren bir `Object`, ve `AutoFit` bir Excel [aralığı](http://go.microsoft.com/fwlink/?LinkId=210911) yöntemi. Aşağıdaki satırları atama gösterir.  
  
     [!code-csharp[csProgGuideOfficeHowTo#14](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_8.cs)]  
  
     [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)]ve sonraki sürümlerinde, döndürülen dönüştürür `Object` için `dynamic` otomatik olarak derlemesi tarafından başvurulduğunda [/link](../../../csharp/language-reference/compiler-options/link-compiler-option.md) derleyici seçeneği veya eşdeğer, varsa Excel **birlikte çalışma türlerini katıştır** özelliği ayarlanmış true. Bu özellik için varsayılan değer doğrudur.  
  
### <a name="to-run-the-project"></a>Projeyi çalıştırmak için  
  
1.  Sonunda aşağıdaki satırı ekleyin `Main`.  
  
     [!code-csharp[csProgGuideOfficeHowTo#8](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_9.cs)]  
  
2.  CTRL + F5 tuşuna basın.  
  
     Bir Excel çalışma sayfası iki hesap verilerini içeren görüntülenir.  
  
### <a name="to-add-a-word-document"></a>Word belgesine eklemek için  
  
1.  Ek yolla göstermeye [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)]ve sonraki sürümlerinde, Office geliştirir programlama, aşağıdaki kod bir Word uygulamasını açar ve Excel çalışma bağlanan bir simge oluşturur.  
  
     Yapıştırma yöntemi `CreateIconInWordDoc`, daha sonra bu adımda, sağlanan içine `Program` sınıfı. `CreateIconInWordDoc`Yöntem çağrıları için karmaşıklığını azaltmak için adlandırılmış ve isteğe bağlı bağımsız değişkenler kullanan [Ekle](http://go.microsoft.com/fwlink/?LinkId=210937) ve [denetlemeye](http://go.microsoft.com/fwlink/?LinkId=147099). Sürümünde sunulan diğer iki yeni özellik bu çağrıları dahil [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)] başvuru parametrelere sahip COM yöntemleri çağrıları basitleştirin. İlk olarak, değer parametreleri değilmiş gibi başvuru parametreleri bağımsız değişkenler gönderebilirsiniz. Diğer bir deyişle, her bir başvuru parametre için bir değişken oluşturmak zorunda kalmadan değerleri doğrudan gönderebilirsiniz. Derleyici bağımsız değişken değerleri tutmak için geçici değişkenleri oluşturur ve çağrısından döndüğünüzde değişkenleri atar. İkinci olarak, atlayabilirsiniz `ref` anahtar sözcüğü bağımsız değişken listesinde.  
  
     `Add` Yöntemi tümü isteğe bağlı dört başvuru parametre vardır. İçinde [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)], veya sonraki sürümlerinde, çıkarın bağımsız değişkenleri herhangi parametrelerden biri veya tümü için varsayılan değerleri kullanmak istiyorsanız. İçinde [!INCLUDE[csharp_orcas_long](~/includes/csharp-orcas-long-md.md)] ve önceki sürümleri, her parametre için bir bağımsız değişken sağlanmalıdır ve parametreleri başvuru parametreleri olduğundan bağımsız değişkeni bir değişken olmalıdır.  
  
     `PasteSpecial` Yöntemi Pano içeriğini ekler. Yöntemi, isteğe bağlı tümü yedi başvuru parametre yok. Aşağıdaki kod iki tanesi için değişkenlerini belirtir: `Link`Pano içeriği kaynağına bir bağlantı oluşturmak için ve `DisplayAsIcon`bağlantıyı simge olarak görüntülemek için. İçinde [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)], adlandırılmış bağımsız değişkenler için bu iki kullanın ve diğerleri atlayın. Bu başvuru parametreleri olsa da, kullanmak gerekmez `ref` anahtar sözcüğü veya bağımsız değişken olarak göndermek için değişkenleri oluşturmak üzere. Değerleri doğrudan gönderebilirsiniz. İçinde [!INCLUDE[csharp_orcas_long](~/includes/csharp-orcas-long-md.md)] ve önceki sürümleri, her bir başvuru parametre için bir değişken bağımsız değişken gönderme gerekir.  
  
     [!code-csharp[csProgGuideOfficeHowTo#9](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_10.cs)]  
  
     İçinde [!INCLUDE[csharp_orcas_long](~/includes/csharp-orcas-long-md.md)] veya önceki sürümleri, aşağıdaki şekilde dilinin daha karmaşık kod gereklidir.  
  
     [!code-csharp[csProgGuideOfficeHowTo#10](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_11.cs)]  
  
2.  Aşağıdaki deyim sonuna Ekle `Main`.  
  
     [!code-csharp[csProgGuideOfficeHowTo#11](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_12.cs)]  
  
3.  Aşağıdaki deyim sonuna Ekle `DisplayInExcel`. `Copy` Yöntemi panoya çalışma ekler.  
  
     [!code-csharp[csProgGuideOfficeHowTo#12](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_13.cs)]  
  
4.  CTRL + F5 tuşuna basın.  
  
     Bir Word belgesi içeren bir simge görüntülenir. Çalışma sayfası ön plana çıkarmak için simgesini çift tıklatın.  
  
### <a name="to-set-the-embed-interop-types-property"></a>Birlikte çalışma türlerini katıştır özelliğini ayarlamak için  
  
1.  Çalışma zamanında birincil birlikte çalışma derlemesi (PIA) gerektirmeyen bir COM türü çağırdığınızda ek geliştirmeler mümkündür. PIA sonuçları bağımlılığını sürüm bağımsızlığı ve daha kolay dağıtım kaldırılıyor. PIA olmadan programlama avantajları hakkında daha fazla bilgi için bkz: [izlenecek yol: yönetilen derlemelerden türler katıştırma](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21).  
  
     Gerekli ve COM yöntemleri tarafından döndürülen türleri türünü kullanarak temsil edilebilir ek olarak, programlama kolaydır, çünkü `dynamic` yerine `Object`. Türüne sahip değişkenler `dynamic` açık atama gereksinimini ortadan kaldırır çalışma zamanı kadar değerlendirilmez. Daha fazla bilgi için bkz: [türünü kullanarak dinamik](../../../csharp/programming-guide/types/using-type-dynamic.md).  
  
     İçinde [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)], PIA kullanmak yerine tür bilgilerini katıştırma olan varsayılan davranışı. Açık atama gerekli olmadığı için bu varsayılan nedeniyle birkaç önceki örneklerin basitleştirilmiştir. Örneğin, bildirimi `worksheet` içinde `DisplayInExcel` olarak yazılmış `Excel._Worksheet workSheet = excelApp.ActiveSheet` yerine `Excel._Worksheet workSheet = (Excel.Worksheet)excelApp.ActiveSheet`. Çağrıları `AutoFit` çünkü aynı yöntemi de varsayılan olmadan açık atama gerektirecek `ExcelApp.Columns[1]` döndürür bir `Object`, ve `AutoFit` bir Excel yöntemidir. Aşağıdaki kod atama gösterir.  
  
     [!code-csharp[csProgGuideOfficeHowTo#14](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_8.cs)]  
  
2.  Varsayılan değeri değiştirmek ve tür bilgilerini katıştırma yerine PIA kullanmak için Genişlet **başvuruları** düğümünde **Çözüm Gezgini** ve ardından **Microsoft.Office.Interop.Excel** veya **Microsoft.Office.Interop.Word**.  
  
3.  Göremiyorsanız **özellikleri** penceresinde, basın **F4**.  
  
4.  Bul **birlikte çalışma türlerini katıştır** özellikler listesinde değerine değiştirip **False**. Eşdeğer, kullanarak derleyebilir [/reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md) yerine derleyici seçeneği [/link](../../../csharp/language-reference/compiler-options/link-compiler-option.md) bir komut isteminde.  
  
### <a name="to-add-additional-formatting-to-the-table"></a>Ek tabloya biçimlendirme eklemek için  
  
1.  İki çağrıları Değiştir `AutoFit` içinde `DisplayInExcel` aşağıdaki ifadesiyle.  
  
     [!code-csharp[csProgGuideOfficeHowTo#15](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_14.cs)]  
  
     [Biçim](http://go.microsoft.com/fwlink/?LinkId=210948) yöntemi tümü isteğe bağlı yedi değer parametreleri sahiptir. Adlandırılmış ve isteğe bağlı bağımsız değişkenler none, bazıları veya tümü için bağımsız değişkenler sağlamak etkinleştirin. Önceki deyiminde parametrelerden yalnızca birini kullanmak için bir bağımsız değişken sağlanan `Format`. Çünkü `Format` ilk parametre parametre listesinde parametre adı sağlamanız gerekmez. Ancak, deyim parametre adı, aşağıdaki kodda gösterildiği gibi dahil olup olmadığını anlamak daha kolay olabilir.  
  
     [!code-csharp[csProgGuideOfficeHowTo#16](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_15.cs)]  
  
2.  Sonuç görmek için CTRL + F5 tuşuna basın. Diğer biçimlere listelenen [XlRangeAutoFormat](http://go.microsoft.com/fwlink/?LinkId=210967) numaralandırması.  
  
3.  1. adım gerekli bağımsız değişkenlerle gösterilir aşağıdaki kod ile deyiminde karşılaştırmak [!INCLUDE[csharp_orcas_long](~/includes/csharp-orcas-long-md.md)] veya önceki sürümleri.  
  
     [!code-csharp[csProgGuideOfficeHowTo#17](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_16.cs)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, tam bir örnek gösterilir.  
  
 [!code-csharp[csProgGuideOfficeHowTo#18](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_17.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Type.Missing?displayProperty=nameWithType>  
 [dinamik](../../../csharp/language-reference/keywords/dynamic.md)  
 [Tür dinamiği kullanma](../../../csharp/programming-guide/types/using-type-dynamic.md)  
 [Adlandırılmış ve isteğe bağlı bağımsız değişkenler](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)  
 [Nasıl yapılır: Office Programlamada adlandırılmış ve isteğe bağlı bağımsız değişkenleri kullanma](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)
