---
title: 'İzlenecek yol: Dinamik Nesneler Oluşturma ve Kullanma (C# and Visual Basic)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dynamic objects [Visual Basic]
- dynamic objects
- dynamic objects [C#]
ms.assetid: 568f1645-1305-4906-8625-5d77af81e04f
caps.latest.revision: 22
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 16c08ff42ce77b3901f5909571c528394d139e03
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="walkthrough-creating-and-using-dynamic-objects-c-and-visual-basic"></a>İzlenecek yol: Dinamik Nesneler Oluşturma ve Kullanma (C# and Visual Basic)

Dinamik nesneler üyeleri özellikleri ve yöntemleri gibi çalışma zamanında yerine içinde derleme zamanında kullanıma sunar. Bu statik türü veya biçimi eşleşmiyor yapıları ile çalışmak için nesneleri oluşturmanıza olanak sağlar. Örneğin, bir dinamik Nesne geçerli HTML biçimlendirme öğeleri ve özniteliklerinin herhangi bir birleşimini içerebilir HTML belge nesne modeli (DOM) başvurmak için kullanabilirsiniz. Her HTML belgesi benzersiz olduğundan, üyeler belirli bir HTML belgesi için çalışma zamanında belirlenir. Bir HTML öğesi özniteliği başvurmak için ortak bir yöntemi için öznitelik adı geçirmektir `GetProperty` öğesinin yöntemi. Başvuru `id` HTML öğesinin özniteliği `<div id="Div1">`, başvuru edinip `<div>` öğesini ve ardından `divElement.GetProperty("id")`. Dinamik Nesne kullanırsanız, başvurabilir `id` olarak özniteliği `divElement.id`.  
  
 Dinamik nesneler de IronPython ve IronRuby gibi dinamik dilleri kolay erişim sağlar. Çalışma zamanında yorumlanır dinamik bir komut dosyasına başvurmak için dinamik bir nesne kullanabilirsiniz.  
  
 Geç bağlama kullanarak bir dinamik Nesne başvurusu. C# ' ta geç bağlama nesnesi olarak türünü belirtin `dynamic`. Visual Basic'te geç bağlama nesnesi olarak türünü belirtin `Object`. Daha fazla bilgi için bkz: [dinamik](../../../csharp/language-reference/keywords/dynamic.md) ve [erken ve geç bağlama](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md).  
  
 Sınıflarda kullanarak özel dinamik nesneler oluşturabilirsiniz <xref:System.Dynamic?displayProperty=nameWithType> ad alanı. Örneğin, oluşturabileceğiniz bir <xref:System.Dynamic.ExpandoObject> ve çalışma zamanında nesne üyeleri belirtin. Ayrıca devralır kendi türü oluşturabilirsiniz <xref:System.Dynamic.DynamicObject> sınıfı. Daha sonra üyelerini geçersiz <xref:System.Dynamic.DynamicObject> çalışma zamanı dinamik işlevselliği sağlamak için sınıf.  
  
 Bu kılavuzda aşağıdaki görevleri gerçekleştirmeniz gerekecektir:  
  
-   Dinamik olarak bir metin dosyasının içeriğini bir nesne özelliklerini gösteren özel bir nesne oluşturun.  
  
-   Kullanan bir proje oluşturun bir `IronPython` kitaplığı.  
  
## <a name="prerequisites"></a>Önkoşullar  
Gereksinim duyduğunuz [IronPython](http://ironpython.net/) bu yönlendirmeyi tamamlamak .NET için. Git kendi [indirme sayfasına](http://ironpython.net/download/) en son sürümü edinmek için.
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-a-custom-dynamic-object"></a>Özel bir dinamik Nesne oluşturma  
 Bu kılavuzda oluşturduğunuz ilk proje bir metin dosyasının içeriğini arar özel bir dinamik Nesne tanımlar. Aranacak metin dinamik özellik adına göre belirtilir. Örneğin, kod çağırma durumunda belirtir `dynamicFile.Sample`, dinamik sınıf tüm "Örnek" ile başlayan satırlar dosyasından içeren bir genel dize listesi döndürür. Arama büyük/küçük harf duyarlıdır. Dinamik sınıf iki isteğe bağlı bağımsız değişkenler de destekler. İlk bağımsız değişken dinamik sınıf satırının veya herhangi bir satırda son satırın başındaki eşleşmeleri için arayacağı belirten bir arama seçeneği enum değerdir. İkinci bağımsız değişkeni, dinamik sınıf öndeki ve arama yapmadan önce her satırdan sondaki boşlukları kırpma belirtir. Örneğin, kod çağırma durumunda belirtir `dynamicFile.Sample(StringSearchOption.Contains)`, dinamik sınıf arar "Örneği için" herhangi bir satır. Kodu çağırma belirtir `dynamicFile.Sample(StringSearchOption.StartsWith, false)`, dinamik sınıf her satırın başındaki "örnek" arar ve öndeki ve sondaki boşlukları kaldırmaz. Dinamik sınıf varsayılan davranışı, her satırın başındaki bir eşleşme aramak ve öndeki ve sondaki boşlukları kaldırmak için değildir.  
  
#### <a name="to-create-a-custom-dynamic-class"></a>Özel bir dinamik sınıf oluşturmak için  
  
1.  Visual Studio'yu başlatın.  
  
2.  Üzerinde **dosya** menüsündeki **yeni** ve ardından **proje**.  
  
3.  İçinde **yeni proje** iletişim kutusunda **proje türleri** bölmesinde olduğundan emin olun **Windows** seçilir. Seçin **konsol uygulaması** içinde **şablonları** bölmesi. İçinde **adı** kutusuna `DynamicSample`ve ardından **Tamam**. Yeni Proje oluşturulur.  
  
4.  DynamicSample projesine sağ tıklayın ve fareyle **Ekle**ve ardından **sınıfı**. İçinde **adı** kutusuna `ReadOnlyFile`ve ardından **Tamam**. Yeni bir dosya ReadOnlyFile sınıfı içeren eklenir.  
  
5.  ReadOnlyFile.cs veya ReadOnlyFile.vb dosyanın üst kısmında, içeri aktarmak için aşağıdaki kodu ekleyin <xref:System.IO?displayProperty=nameWithType> ve <xref:System.Dynamic?displayProperty=nameWithType> ad alanları.  
  
     [!code-csharp[VbDynamicWalkthrough#1](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_1.cs)]

     [!code-vb[VbDynamicWalkthrough#1](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_1.vb)]  
  
6.  Özel dinamik nesnesini enum arama ölçütlerini belirlemek için kullanır. Class deyimi önce aşağıdaki enum tanımını ekleyin.  
  
     [!code-csharp[VbDynamicWalkthrough#2](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_2.cs)]

     [!code-vb[VbDynamicWalkthrough#2](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_2.vb)]  
  
7.  Class deyimi devralmak için güncelleştirme `DynamicObject` aşağıdaki kod örneğinde gösterildiği gibi sınıfı.  
  
     [!code-csharp[VbDynamicWalkthrough#3](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_3.cs)]

     [!code-vb[VbDynamicWalkthrough#3](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_3.vb)]  
  
8.  Aşağıdaki kodu ekleyin `ReadOnlyFile` dosya yolu için özel bir alan ve için bir oluşturucu tanımlamak için sınıf `ReadOnlyFile` sınıfı.  
  
     [!code-csharp[VbDynamicWalkthrough#4](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_4.cs)]
     
     [!code-vb[VbDynamicWalkthrough#4](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_4.vb)]  
  
9. Aşağıdakileri ekleyin `GetPropertyValue` yönteme `ReadOnlyFile` sınıfı. `GetPropertyValue` Yöntemi alır, girdi olarak, arama ölçütünü ve dosya, arama ölçütlerini karşılayan bir metinden satırları döndürür. Tarafından sağlanan dinamik yöntemleri `ReadOnlyFile` sınıf çağrısı `GetPropertyValue` ilgili sonuçları almak için yöntem.  
  
     [!code-csharp[VbDynamicWalkthrough#5](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_5.cs)]
     
     [!code-vb[VbDynamicWalkthrough#5](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_5.vb)]  
  
10. Sonra `GetPropertyValue` yöntemi, geçersiz kılmak için aşağıdaki kodu ekleyin <xref:System.Dynamic.DynamicObject.TryGetMember%2A> yöntemi <xref:System.Dynamic.DynamicObject> sınıfı. <xref:System.Dynamic.DynamicObject.TryGetMember%2A> Dinamik sınıf üyesi istenen ve bağımsız değişkenler belirtilmişse yöntemi çağrılır. `binder` Bağımsız değişkeni başvurulan üye hakkında bilgiler içerir ve `result` bağımsız değişkeni için belirtilen üye döndürülen sonuç başvuruyor. <xref:System.Dynamic.DynamicObject.TryGetMember%2A> Yöntemi döndüren bir Boole değeri döndürür `true` istenen üye var; Aksi takdirde döndürür `false`.  
  
     [!code-csharp[VbDynamicWalkthrough#6](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_6.cs)]
     
     [!code-vb[VbDynamicWalkthrough#6](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_6.vb)]  
  
11. Sonra `TryGetMember` yöntemi, geçersiz kılmak için aşağıdaki kodu ekleyin <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> yöntemi <xref:System.Dynamic.DynamicObject> sınıfı. <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> Dinamik sınıf üyesi bağımsız değişkenlerle istendiğinde yöntemi çağrılır. `binder` Bağımsız değişkeni başvurulan üye hakkında bilgiler içerir ve `result` bağımsız değişkeni için belirtilen üye döndürülen sonuç başvuruyor. `args` Bağımsız değişkeni bir üyesine geçirilen bağımsız değişken dizisi içerir. <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> Yöntemi döndüren bir Boole değeri döndürür `true` istenen üye var; Aksi takdirde döndürür `false`.  
  
     Özel sürümünü `TryInvokeMember` yöntemi arasında bir değer olması için ilk bağımsız değişken bekler `StringSearchOption` bir önceki adımda tanımlanan enum. `TryInvokeMember` Yöntemi bir Boole değeri olması için ikinci bağımsız değişken bekler. Bir veya iki bağımsız değişken geçerli değerler varsa, bunlar geçirilecek `GetPropertyValue` sonuçları almak için yöntem.  
  
     [!code-csharp[VbDynamicWalkthrough#7](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_7.cs)]
     
     [!code-vb[VbDynamicWalkthrough#7](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_7.vb)]  
  
12. Dosyayı kaydedin ve kapatın.  
  
#### <a name="to-create-a-sample-text-file"></a>Örnek bir metin dosyası oluşturmak için  
  
1.  DynamicSample projesine sağ tıklayın ve fareyle **Ekle**ve ardından **yeni öğe**. İçinde **yüklü şablonlar** bölmesinde, **genel**ve ardından **metin dosyası** şablonu. İçinde TextFile1.txt varsayılan adı bırakın **adı** kutusuna ve ardından **Ekle**. Yeni bir metin dosyası projeye eklenir.  
  
2.  Aşağıdaki metni TextFile1.txt dosyasına kopyalayın.  
  
    ```  
    List of customers and suppliers  
  
    Supplier: Lucerne Publishing (http://www.lucernepublishing.com/)  
    Customer: Preston, Chris  
    Customer: Hines, Patrick  
    Customer: Cameron, Maria  
    Supplier: Graphic Design Institute (http://www.graphicdesigninstitute.com/)   
    Supplier: Fabrikam, Inc. (http://www.fabrikam.com/)   
    Customer: Seubert, Roxanne  
    Supplier: Proseware, Inc. (http://www.proseware.com/)   
    Customer: Adolphi, Stephan  
    Customer: Koch, Paul  
    ```  
  
3.  Dosyayı kaydedin ve kapatın.  
  
#### <a name="to-create-a-sample-application-that-uses-the-custom-dynamic-object"></a>Özel dinamik nesnesi kullanan örnek bir uygulama oluşturmak için  
  
1.  İçinde **Çözüm Gezgini**, Visual C# kullanıyorsanız, Visual Basic veya Program.cs dosyasını kullanıyorsanız, Module1.vb dosyasına çift tıklayın.  
  
2.  Aşağıdaki kod örneği oluşturmak için ana yordama ekleyin `ReadOnlyFile` TextFile1.txt dosyası için sınıf. Kod geç bağlama dinamik üyeler çağırın ve "Müşteri" dizesini içeren metin satırı almak için kullanır.  
  
     [!code-csharp[VbDynamicWalkthrough#8](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_8.cs)]
     
     [!code-vb[VbDynamicWalkthrough#8](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_8.vb)]  
  
3.  Dosyayı kaydedin ve oluşturmak ve uygulamayı çalıştırmak için CTRL + F5 tuşuna basın.  
  
## <a name="calling-a-dynamic-language-library"></a>Dinamik Dil kitaplığı çağırma  

Bu kılavuzda oluşturduğunuz sonraki proje IronPython dinamik dilinde yazılmış bir kitaplık erişir.
  
#### <a name="to-create-a-custom-dynamic-class"></a>Özel bir dinamik sınıf oluşturmak için  
  
1.  Visual Studio'da üzerinde **dosya** menüsündeki **yeni** ve ardından **proje**.  
  
2.  İçinde **yeni proje** iletişim kutusunda **proje türleri** bölmesinde olduğundan emin olun **Windows** seçilir. Seçin **konsol uygulaması** içinde **şablonları** bölmesi. İçinde **adı** kutusuna `DynamicIronPythonSample`ve ardından **Tamam**. Yeni Proje oluşturulur.  
  
3.  Visual Basic kullanıyorsanız, DynamicIronPythonSample projesine sağ tıklayın ve ardından **özellikleri**. Tıklatın **başvuruları** sekmesi. Tıklatın **Ekle** düğmesi. Visual C# içinde kullanıyorsanız **Çözüm Gezgini**, sağ **başvuruları** klasörünü ve ardından **Başvuru Ekle**.  
  
4.  Üzerinde **Gözat** sekmesinde, IronPython kitaplıklarına yüklü olduğu klasöre göz atın. C:\Program Files\IronPython 2.6 .NET 4.0 için örneğin. Seçin **IronPython.dll**, **IronPython.Modules.dll**, **Microsoft.Scripting.dll**, ve **Microsoft.Dynamic.dll** kitaplıkları . **Tamam**'ı tıklatın.  
  
5.  Visual Basic kullanıyorsanız, Module1.vb dosyasını düzenleyin. Visual C# kullanıyorsanız Program.cs dosyasını düzenleyin.  
  
6.  Dosyanın üst kısmında, içeri aktarmak için aşağıdaki kodu ekleyin `Microsoft.Scripting.Hosting` ve `IronPython.Hosting` IronPython kitaplıklarından ad alanları.  
  
     [!code-csharp[VbDynamicWalkthroughIronPython#1](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_9.cs)]
     
     [!code-vb[VbDynamicWalkthroughIronPython#1](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_9.vb)]  
  
7.  Main yöntemi yeni bir oluşturmak için aşağıdaki kodu ekleyin `Microsoft.Scripting.Hosting.ScriptRuntime` IronPython kitaplıklarına barındırmak için nesne. `ScriptRuntime` Nesnesi IronPython kitaplığı modülü random.py yükler.  
  
     [!code-csharp[VbDynamicWalkthroughIronPython#2](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_10.cs)]
     
     [!code-vb[VbDynamicWalkthroughIronPython#2](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_10.vb)]  
  
8.  Random.py modülü yüklenemedi koddan sonra dizisi oluşturmak için aşağıdaki kodu ekleyin. Dizi geçirilir `shuffle` rastgele dizideki sıralar random.py modülün yöntemi.  
  
     [!code-csharp[VbDynamicWalkthroughIronPython#3](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_11.cs)]
     
     [!code-vb[VbDynamicWalkthroughIronPython#3](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_11.vb)]  
  
9. Dosyayı kaydedin ve oluşturmak ve uygulamayı çalıştırmak için CTRL + F5 tuşuna basın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Dynamic?displayProperty=nameWithType>  
 <xref:System.Dynamic.DynamicObject?displayProperty=nameWithType>  
 [Tür dinamiği kullanma](../../../csharp/programming-guide/types/using-type-dynamic.md)  
 [Erken ve Geç Bağlama](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)  
 [dynamic](../../../csharp/language-reference/keywords/dynamic.md)  
 [Dinamik arabirimler (Microsoft TechNet indirilebilir PDF) uygulama](http://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/implementing-dynamic-interfaces.pdf)
