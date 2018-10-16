---
title: 'İzlenecek yol: Dinamik Nesneler Oluşturma ve Kullanma (C# and Visual Basic)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dynamic objects [Visual Basic]
- dynamic objects
- dynamic objects [C#]
ms.assetid: 568f1645-1305-4906-8625-5d77af81e04f
ms.openlocfilehash: 8134a7c7c1f2c4e6432dd19889faf796a9284553
ms.sourcegitcommit: fd8d4587cc26e53f0e27e230d6e27d828ef4306b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2018
ms.locfileid: "49347974"
---
# <a name="walkthrough-creating-and-using-dynamic-objects-c-and-visual-basic"></a>İzlenecek yol: Dinamik Nesneler Oluşturma ve Kullanma (C# and Visual Basic)

Dinamik nesneler özellikler ve yöntemler gibi üyeleri çalışma zamanında yerine, derleme zamanında ortaya çıkarır. Bu, bir statik türü veya biçimi eşleşmeyen yapılar ile çalışmak için nesneleri oluşturmanızı sağlar. Örneğin, bir dinamik Nesne geçerli HTML biçimlendirmeyi öğeler ve öznitelikler herhangi bir birleşimini içerebilir HTML belge nesne modeli (DOM) başvurmak için kullanabilirsiniz. Her HTML belgesi benzersiz olduğundan, belirli bir HTML belge üyelerini çalışma zamanında belirlenir. Bir HTML öğesi özniteliklerini başvurmak için kullanılan genel bir yöntem için öznitelik adı geçirmektir `GetProperty` öğenin yöntemi. Başvuru `id` HTML öğesi özniteliklerini `<div id="Div1">`, başvuru edinip `<div>` öğesini ve ardından `divElement.GetProperty("id")`. Dinamik Nesne kullanırsanız, başvurabileceğiniz `id` olarak özniteliği `divElement.id`.  
  
 Dinamik nesneler, IronPython ve Ironruby gibi dinamik dilleri uygun erişim de sağlar. Çalışma zamanında yorumlanır dinamik bir komut dosyasına başvuruda bulunmak için dinamik bir nesne kullanabilirsiniz.  
  
 Geç bağlama kullanarak dinamik bir nesne başvuru. C# ' ta bir geç bağlama nesnesi olarak türünü belirtin `dynamic`. Visual Basic'te bir geç bağlama nesnesi olarak türünü belirtin `Object`. Daha fazla bilgi için [dinamik](../../../csharp/language-reference/keywords/dynamic.md) ve [erken ve geç bağlama](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md).  
  
 Özel dinamik nesneler sınıflarını kullanarak oluşturabileceğiniz <xref:System.Dynamic?displayProperty=nameWithType> ad alanı. Örneğin, oluşturabileceğiniz bir <xref:System.Dynamic.ExpandoObject> ve çalışma zamanında, nesnenin üyeleri belirtin. Devralınan kendi türünüzü oluşturabilirsiniz <xref:System.Dynamic.DynamicObject> sınıfı. Daha sonra üyelerini geçersiz <xref:System.Dynamic.DynamicObject> çalışma zamanı dinamik işlevselliği sağlamak için sınıf.  
  
 Bu izlenecek yolda aşağıdaki görevleri gerçekleştireceksiniz:  
  
-   Dinamik olarak bir metin dosyasının içeriğini bir nesnenin özellikleri olarak sunan özel bir nesne oluşturun.  
  
-   Kullanan bir proje oluşturma bir `IronPython` kitaplığı.  
  
## <a name="prerequisites"></a>Önkoşullar  
Gereksinim duyduğunuz [IronPython](http://ironpython.net/) Bu izlenecek yolu tamamlamak .NET için. Git, [indirme sayfası](http://ironpython.net/download/) en güncel sürümü edinmek için.
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-a-custom-dynamic-object"></a>Özel bir dinamik Nesne oluşturma

Bu anlatımda oluşturduğunuz ilk proje, bir metin dosyasının içeriğini arar özel, dinamik bir nesneyi tanımlar. Dinamik özellik adına göre aramak için metin belirtilir. Örneğin, kod arama, belirtir `dynamicFile.Sample`, dinamik bir sınıf tüm "Örnek" ile başlayan satırlar dosyasından içeren bir genel dize listesi döndürür. Arama büyük/küçük harfe duyarsızdır. Dinamik sınıfı ayrıca iki isteğe bağlı bağımsız değişkenler de destekler. İlk bağımsız değişken dinamik sınıfı satırın sonunda veya herhangi bir satırında satırın başlangıcında eşleşmeleri için arayacağı belirten bir arama seçeneği numaralandırma değeridir. İkinci bağımsız değişkeni, dinamik sınıfı, baştaki ve sondaki boşlukları her satırında aramadan önce trim belirtir. Örneğin, kod arama, belirtir `dynamicFile.Sample(StringSearchOption.Contains)`, dinamik sınıfı arar "Örneği için" herhangi bir yerde bir satır. Kodu çağırma belirtir `dynamicFile.Sample(StringSearchOption.StartsWith, false)`, dinamik bir sınıf her satırın başındaki "örnek" arar ve öndeki ve sondaki boşlukları kaldırmaz. Dinamik sınıfı, varsayılan davranışı, her satırın başında bir eşleşme aramak ve öndeki ve sondaki boşlukları kaldırmak için olur.  
  
### <a name="to-create-a-custom-dynamic-class"></a>Dinamik özel bir sınıf oluşturmak için  
  
1.  Visual Studio'yu başlatın.  
  
2.  Üzerinde **dosya** menüsünde **yeni** ve ardından **proje**.  
  
3.  İçinde **yeni proje** iletişim kutusundaki **proje türleri** bölmesinde emin olun **Windows** seçilir. Seçin **konsol uygulaması** içinde **şablonları** bölmesi. İçinde **adı** kutusuna `DynamicSample`ve ardından **Tamam**. Yeni Proje oluşturulur.  
  
4.  DynamicSample projeye sağ tıklayın ve fareyle **Ekle**ve ardından **sınıfı**. İçinde **adı** kutusuna `ReadOnlyFile`ve ardından **Tamam**. Yeni bir dosya ReadOnlyFile sınıfı içeren eklenir.  
  
5.  İçeri aktarmak için aşağıdaki kodu ReadOnlyFile.cs veya ReadOnlyFile.vb dosyasının en üstüne ekleyin <xref:System.IO?displayProperty=nameWithType> ve <xref:System.Dynamic?displayProperty=nameWithType> ad alanları.  

    [!code-csharp[VbDynamicWalkthrough#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#1)]
    [!code-vb[VbDynamicWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#1)]  

6.  Özel dinamik Nesne enum arama kriterlerini belirlemek için kullanır. Class deyimi önce aşağıdaki liste tanımını ekleyin.  
  
    [!code-csharp[VbDynamicWalkthrough#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#2)]
    [!code-vb[VbDynamicWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#2)]
  
7.  Güncelleştirme devralmak için sınıf bildirimi `DynamicObject` , aşağıdaki kod örneğinde gösterildiği gibi sınıf.  
  
    [!code-csharp[VbDynamicWalkthrough#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#3)]
    [!code-vb[VbDynamicWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#3)]

8.  Aşağıdaki kodu ekleyin `ReadOnlyFile` dosya yolu için özel bir alan ve için bir kurucu tanımlamak için sınıf `ReadOnlyFile` sınıfı.  
  
    [!code-csharp[VbDynamicWalkthrough#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#4)]
    [!code-vb[VbDynamicWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#4)]
  
9. Aşağıdaki `GetPropertyValue` yönteme `ReadOnlyFile` sınıfı. `GetPropertyValue` Yöntemi alır, giriş olarak, arama ölçütleri ve dosya arama ölçütlerini karşılayan bir metinden satırları döndürür. Tarafından sağlanan dinamik yöntemleri `ReadOnlyFile` sınıf çağrı `GetPropertyValue` ilgili sonuçları almak için yöntemi.  
  
    [!code-csharp[VbDynamicWalkthrough#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#5)]
    [!code-vb[VbDynamicWalkthrough#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#5)]  
  
10. Sonra `GetPropertyValue` yöntemi geçersiz kılmak için aşağıdaki kodu ekleyin <xref:System.Dynamic.DynamicObject.TryGetMember%2A> yöntemi <xref:System.Dynamic.DynamicObject> sınıfı. <xref:System.Dynamic.DynamicObject.TryGetMember%2A> Dinamik bir sınıf üyesi istenen ve bağımsız değişken olmadan belirtilmişse yöntemi çağrılır. `binder` Bağımsız değişkeni başvurulan üyeyle ilgili bilgiler içerir ve `result` bağımsız değişkeni için belirtilen üyenin döndürülen sonuç başvuruyor. <xref:System.Dynamic.DynamicObject.TryGetMember%2A> Yöntemi döndüren bir Boole değeri döndürür `true` istenen üye var; Aksi halde döndürür `false`.  
  
    [!code-csharp[VbDynamicWalkthrough#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#6)]
    [!code-vb[VbDynamicWalkthrough#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#6)]
  
11. Sonra `TryGetMember` yöntemi geçersiz kılmak için aşağıdaki kodu ekleyin <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> yöntemi <xref:System.Dynamic.DynamicObject> sınıfı. <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> Dinamik bir sınıf üyesi bağımsız değişkenlerle istendiğinde yöntemi çağrılır. `binder` Bağımsız değişkeni başvurulan üyeyle ilgili bilgiler içerir ve `result` bağımsız değişkeni için belirtilen üyenin döndürülen sonuç başvuruyor. `args` Bağımsız değişkeni bir üyesine geçirilen bağımsız değişkenlerin dizisi içerir. <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> Yöntemi döndüren bir Boole değeri döndürür `true` istenen üye var; Aksi halde döndürür `false`.  
  
    Özel sürümü `TryInvokeMember` yöntemi bir değer olarak ilk bağımsız değişken bekliyor `StringSearchOption` bir önceki adımda tanımlanan sabit listesi. `TryInvokeMember` Yöntemi ikinci bağımsız değişkeni Boolean bir değer olmasını bekliyor. Bir veya iki bağımsız değişken geçerli değerler için geçirilen `GetPropertyValue` sonuçlarını almak için yöntemi.  
  
    [!code-csharp[VbDynamicWalkthrough#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#7)]
    [!code-vb[VbDynamicWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#7)]
  
12. Dosyayı kaydedin ve kapatın.  
  
#### <a name="to-create-a-sample-text-file"></a>Örnek metin dosyası oluşturmak için  
  
1.  DynamicSample projeye sağ tıklayın ve fareyle **Ekle**ve ardından **yeni öğe**. İçinde **yüklü şablonlar** bölmesinde **genel**ve ardından **metin dosyası** şablonu. İçinde TextFile1.txt varsayılan adı bırakın **adı** kutusuna ve ardından **Ekle**. Yeni bir metin dosyası projeye eklenir.  
  
2.  Aşağıdaki metni TextFile1.txt dosyasına kopyalayın.  
  
    ```  
    List of customers and suppliers  
  
    Supplier: Lucerne Publishing (https://www.lucernepublishing.com/)  
    Customer: Preston, Chris  
    Customer: Hines, Patrick  
    Customer: Cameron, Maria  
    Supplier: Graphic Design Institute (https://www.graphicdesigninstitute.com/)   
    Supplier: Fabrikam, Inc. (https://www.fabrikam.com/)   
    Customer: Seubert, Roxanne  
    Supplier: Proseware, Inc. (http://www.proseware.com/)   
    Customer: Adolphi, Stephan  
    Customer: Koch, Paul  
    ```  
  
3.  Dosyayı kaydedin ve kapatın.  
  
#### <a name="to-create-a-sample-application-that-uses-the-custom-dynamic-object"></a>Özel dinamik Nesne kullanan örnek bir uygulama oluşturmak için  
  
1.  İçinde **Çözüm Gezgini**, Visual C# kullanıyorsanız Program.cs dosyasını ya da Visual Basic kullanıyorsanız Module1.vb dosyasını çift tıklatın.  
  
2.  Main yordamı için bir örneğini oluşturmak için aşağıdaki kodu ekleyin `ReadOnlyFile` TextFile1.txt dosya için sınıf. Kod geç bağlama dinamik üyeleri çağırır ve "Müşteri" dizesini içeren metin satırı almak için kullanır.  
  
     [!code-csharp[VbDynamicWalkthrough#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/program.cs#8)]
     [!code-vb[VbDynamicWalkthrough#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/module1.vb#8)]
  
3.  Dosyayı kaydedin ve oluşturmak ve uygulamayı çalıştırmak için CTRL + F5 tuşlarına basın.  
  
## <a name="calling-a-dynamic-language-library"></a>Dinamik Dil kitaplığı çağırma  

Bu anlatımda oluşturduğunuz projenin sonraki IronPython dinamik dilinde yazılmış bir kitaplık erişir.
  
### <a name="to-create-a-custom-dynamic-class"></a>Dinamik özel bir sınıf oluşturmak için
  
1.  Visual Studio'da üzerinde **dosya** menüsünde **yeni** ve ardından **proje**.  
  
2.  İçinde **yeni proje** iletişim kutusundaki **proje türleri** bölmesinde emin olun **Windows** seçilir. Seçin **konsol uygulaması** içinde **şablonları** bölmesi. İçinde **adı** kutusuna `DynamicIronPythonSample`ve ardından **Tamam**. Yeni Proje oluşturulur.  
  
3.  Visual Basic kullanıyorsanız, DynamicIronPythonSample projeye sağ tıklayın ve ardından **özellikleri**. Tıklayın **başvuruları** sekmesi. Tıklayın **Ekle** düğmesi. Visual C# içinde kullanıyorsanız **Çözüm Gezgini**, sağ **başvuruları** klasörünü ve ardından **Başvuru Ekle**.  
  
4.  Üzerinde **Gözat** sekmesinde, IronPython kitaplıkları yüklü olduğu klasöre göz atın. C:\Program Files\IronPython 2.6 .NET 4.0 gibi. Seçin **IronPython.dll**, **IronPython.Modules.dll**, **Microsoft.Scripting.dll**, ve **Microsoft.Dynamic.dll** kitaplıkları . **Tamam**'ı tıklatın.  
  
5.  Visual Basic kullanıyorsanız, Module1.vb dosyasını düzenleyin. Visual C# kullanıyorsanız Program.cs dosyasını düzenleyin.  
  
6.  İçeri aktarmak için aşağıdaki kod dosyasının en üstüne ekleyin `Microsoft.Scripting.Hosting` ve `IronPython.Hosting` IronPython kitaplıklarından ad alanları.  
  
    [!code-csharp[VbDynamicWalkthroughIronPython#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/cs/program.cs#1)]
    [!code-vb[VbDynamicWalkthroughIronPython#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/vb/module1.vb#1)]
  
7.  Ana yöntemde yeni oluşturmak için aşağıdaki kodu ekleyin `Microsoft.Scripting.Hosting.ScriptRuntime` IronPython kitaplıkları barındırmak için nesne. `ScriptRuntime` Nesne IronPython kitaplık modülü random.py yükler.  
  
     [!code-csharp[VbDynamicWalkthroughIronPython#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/cs/program.cs#2)]
     [!code-vb[VbDynamicWalkthroughIronPython#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/vb/module1.vb#2)]
  
8.  Random.py modülünü yüklemek için koddan sonra tamsayı dizisi oluşturmak için aşağıdaki kodu ekleyin. Dizi geçirilir `shuffle` yöntemi dizideki değerleri rastgele sıralar random.py modülü.  
  
     [!code-csharp[VbDynamicWalkthroughIronPython#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/cs/program.cs#3)]
     [!code-vb[VbDynamicWalkthroughIronPython#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/vb/module1.vb#3)]
  
9. Dosyayı kaydedin ve oluşturmak ve uygulamayı çalıştırmak için CTRL + F5 tuşlarına basın.  
  
## <a name="see-also"></a>Ayrıca Bkz.

- <xref:System.Dynamic?displayProperty=nameWithType>  
- <xref:System.Dynamic.DynamicObject?displayProperty=nameWithType>  
- [Tür dinamiği kullanma](../../../csharp/programming-guide/types/using-type-dynamic.md)  
- [Erken ve Geç Bağlama](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)  
- [dynamic](../../../csharp/language-reference/keywords/dynamic.md)  
- [Dinamik arabirimleri (Microsoft TechNet indirilebilir PDF) uygulama](https://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/implementing-dynamic-interfaces.pdf)
