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
ms.openlocfilehash: 3b5a92948a3e692a734f3ddee3c7238d5d27588f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79157058"
---
# <a name="walkthrough-creating-and-using-dynamic-objects-c-and-visual-basic"></a>İzlenecek yol: Dinamik Nesneler Oluşturma ve Kullanma (C# and Visual Basic)

Dinamik nesneler, derleme zamanında değil, çalışma zamanında özellikler ve yöntemler gibi üyeleri ortaya çıkarır. Bu, statik bir tür veya biçimle eşleşmeyan yapılarla çalışmak üzere nesneler oluşturmanıza olanak tanır. Örneğin, geçerli HTML biçimlendirme öğeleri ve özniteliklerinin herhangi bir birleşimini içerebilen HTML Belge Nesnesi Modeli'ne (DOM) başvurmak için dinamik bir nesne kullanabilirsiniz. Her HTML belgesi benzersiz olduğundan, belirli bir HTML belgesinin üyeleri çalışma zamanında belirlenir. Bir HTML öğesinin özniteliğine başvurmak için yaygın bir yöntem, özniteliğin adını öğenin `GetProperty` yöntemine geçirmektir. `id` HTML öğesinin `<div id="Div1">`özniteliğine başvurmak için önce `<div>` öğeye bir başvuru `divElement.GetProperty("id")`elde eve, sonra . Dinamik bir nesne kullanıyorsanız, `id` özniteliği . `divElement.id`  
  
 Dinamik nesneler ayrıca IronPython ve IronRuby gibi dinamik dillere kolay erişim sağlar. Çalışma zamanında yorumlanan dinamik bir komut dosyasına başvurmak için dinamik bir nesne kullanabilirsiniz.  
  
 Geç bağlama kullanarak dinamik bir nesneye başvurursunuz. C#'da, geç bağlanmış bir nesnenin `dynamic`türünü . olarak belirtirsiniz. Visual Basic'te, geç bağlanmış bir nesnenin `Object`türünü . olarak belirtirsiniz. Daha fazla bilgi için [dinamik](../../language-reference/builtin-types/reference-types.md) ve [Erken ve Geç Ciltleme'ye](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)bakın.  
  
 <xref:System.Dynamic?displayProperty=nameWithType> Ad alanındaki sınıfları kullanarak özel dinamik nesneler oluşturabilirsiniz. Örneğin, bir <xref:System.Dynamic.ExpandoObject> oluşturup çalışma zamanında o nesnenin üyelerini belirtebilirsiniz. <xref:System.Dynamic.DynamicObject> Sınıfı devralan kendi türünüzü de oluşturabilirsiniz. Daha sonra çalışma zamanı dinamik <xref:System.Dynamic.DynamicObject> işlevselliği sağlamak için sınıfın üyelerini geçersiz kılabilirsiniz.  
  
 Bu izlenecek yolda aşağıdaki görevleri gerçekleştireceksiniz:  
  
- Bir metin dosyasının içeriğini nesnenin özellikleri olarak dinamik olarak ortaya çıkaran özel bir nesne oluşturun.  
  
- Kitaplık kullanan bir `IronPython` proje oluşturun.  
  
## <a name="prerequisites"></a>Önkoşullar  

Bu izbiyi tamamlamak için .NET için [IronPython'a](https://ironpython.net/) ihtiyacınız vardır. En son sürümü almak için [İndirme sayfalarına](https://ironpython.net/download/) gidin.
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-a-custom-dynamic-object"></a>Özel Dinamik Nesne Oluşturma

Bu izbinde oluşturduğunuz ilk proje, metin dosyasının içeriğini arayan özel dinamik bir nesne tanımlar. Aranacak metin dinamik bir özelliğin adıyla belirtilir. Örneğin, arama kodu belirtenirse, `dynamicFile.Sample`dinamik sınıf "Örnek" ile başlayan dosyadaki tüm satırları içeren dizeleri genel bir liste döndürür. Arama büyük/küçük harf duyarsız. Dinamik sınıf da iki isteğe bağlı bağımsız değişkeni destekler. İlk bağımsız değişken, dinamik sınıfın satırın başında, satırın sonunda veya satırın herhangi bir yerinde eşleşmeleri araması gerektiğini belirten bir arama seçeneği enum değeridir. İkinci bağımsız değişken, dinamik sınıfın arama yapmadan önce her satırdan satır başında ve sondalama boşluklarını kırpması gerektiğini belirtir. Örneğin, arama kodu belirteniyorsa, `dynamicFile.Sample(StringSearchOption.Contains)`dinamik sınıf bir satırdaki herhangi bir yerde "Örnek" arar. Arama kodu belirtse, `dynamicFile.Sample(StringSearchOption.StartsWith, false)`dinamik sınıf her satırın başında "Örnek" arar ve satır aralığı ve sondaki boşlukları kaldırmaz. Dinamik sınıfın varsayılan davranışı, her satırın başında bir eşleşme aramak ve satır aralığı ve sondaki boşlukları kaldırmaktır.  
  
### <a name="to-create-a-custom-dynamic-class"></a>Özel dinamik bir sınıf oluşturmak için  
  
1. Visual Studio’yu çalıştırın.  
  
2. **Dosya** menüsünde **Yeni'yi** işaret edin ve ardından **Project'i**tıklatın.  
  
3. Yeni **Proje** iletişim kutusunda, **Proje Türleri** bölmesinde **Windows'un** seçildiğinden emin olun. **Şablonlar** bölmesinde **Konsol Uygulaması'nı** seçin. **Ad** kutusuna, `DynamicSample`''yı yazın ve sonra **Tamam'ı**tıklatın. Yeni proje oluşturuldu.  
  
4. DynamicSample projesini sağ tıklatın ve **Ekle'ye**işaret edin ve **ardından Sınıf'ı**tıklatın. **Ad** kutusuna, `ReadOnlyFile`''yı yazın ve sonra **Tamam'ı**tıklatın. ReadOnlyFile sınıfını içeren yeni bir dosya eklenir.  
  
5. ReadOnlyFile.cs veya ReadOnlyFile.vb dosyasının üst kısmında, ve <xref:System.IO?displayProperty=nameWithType> <xref:System.Dynamic?displayProperty=nameWithType> ad alanlarını almak için aşağıdaki kodu ekleyin.  

    [!code-csharp[VbDynamicWalkthrough#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#1)]
    [!code-vb[VbDynamicWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#1)]  

6. Özel dinamik nesne, arama ölçütlerini belirlemek için bir enum kullanır. Sınıf deyiminden önce aşağıdaki enum tanımını ekleyin.  
  
    [!code-csharp[VbDynamicWalkthrough#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#2)]
    [!code-vb[VbDynamicWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#2)]
  
7. Aşağıdaki kod örneğinde `DynamicObject` gösterildiği gibi sınıf deyimini sınıfı devralmak üzere güncelleştirin.  
  
    [!code-csharp[VbDynamicWalkthrough#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#3)]
    [!code-vb[VbDynamicWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#3)]

8. Dosya yolu için `ReadOnlyFile` özel bir alan ve `ReadOnlyFile` sınıf için bir oluşturucu tanımlamak için sınıfa aşağıdaki kodu ekleyin.  
  
    [!code-csharp[VbDynamicWalkthrough#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#4)]
    [!code-vb[VbDynamicWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#4)]
  
9. `ReadOnlyFile` sınıfına aşağıdaki `GetPropertyValue` yöntemini ekleyin. Yöntem, `GetPropertyValue` giriş olarak arama ölçütlerini alır ve arama ölçütlerini eşleşen bir metin dosyasındaki satırları döndürür. `ReadOnlyFile` Sınıf tarafından sağlanan dinamik yöntemler, kendi sonuçlarını almak için `GetPropertyValue` yöntemi çağırır.  
  
    [!code-csharp[VbDynamicWalkthrough#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#5)]
    [!code-vb[VbDynamicWalkthrough#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#5)]  
  
10. Yöntemden `GetPropertyValue` sonra, <xref:System.Dynamic.DynamicObject.TryGetMember%2A> <xref:System.Dynamic.DynamicObject> sınıfın yöntemini geçersiz kılmak için aşağıdaki kodu ekleyin. Dinamik <xref:System.Dynamic.DynamicObject.TryGetMember%2A> bir sınıfın bir üyesi istendiğinde ve bağımsız değişken belirtilmediğinde yöntem çağrılır. Bağımsız `binder` değişken, başvurulan üye hakkında `result` bilgi içerir ve bağımsız değişken, belirtilen üye için döndürülen sonuca başvurur. Yöntem, <xref:System.Dynamic.DynamicObject.TryGetMember%2A> istenen üye varsa `true` döndüren bir Boolean değeri döndürür; aksi takdirde `false`döner .  
  
    [!code-csharp[VbDynamicWalkthrough#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#6)]
    [!code-vb[VbDynamicWalkthrough#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#6)]
  
11. Yöntemden `TryGetMember` sonra, <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> <xref:System.Dynamic.DynamicObject> sınıfın yöntemini geçersiz kılmak için aşağıdaki kodu ekleyin. Dinamik <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> bir sınıfın bir üyesi bağımsız değişkenlerle istendiğinde yöntem çağrılır. Bağımsız `binder` değişken, başvurulan üye hakkında `result` bilgi içerir ve bağımsız değişken, belirtilen üye için döndürülen sonuca başvurur. Bağımsız `args` değişken, üyeye geçirilen bağımsız değişkenler dizisi içerir. Yöntem, <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> istenen üye varsa `true` döndüren bir Boolean değeri döndürür; aksi takdirde `false`döner .  
  
    `TryInvokeMember` Yöntemin özel sürümü, ilk bağımsız değişkenin önceki `StringSearchOption` adımda tanımladığınız enumdan bir değer olmasını bekler. Yöntem, `TryInvokeMember` ikinci bağımsız değişkenin Boolean değeri olmasını bekler. Bir veya her iki bağımsız değişken geçerli `GetPropertyValue` değerlerse, sonuçları almak için yönteme geçirilir.  
  
    [!code-csharp[VbDynamicWalkthrough#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#7)]
    [!code-vb[VbDynamicWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#7)]
  
12. Dosyayı kaydedin ve kapatın.  
  
#### <a name="to-create-a-sample-text-file"></a>Örnek metin dosyası oluşturmak için  
  
1. DynamicSample projesini sağ tıklatın ve **Ekle'ye**işaret edin ve ardından **Yeni Öğe'yi**tıklatın. Yüklü **Şablonlar** bölmesinde **Genel**'i ve ardından **Metin Dosyası** şablonu'nu seçin. TextFile1.txt varsayılan adını **Ad** kutusuna bırakın ve sonra **Ekle'yi**tıklatın. Projeye yeni bir metin dosyası eklenir.  
  
2. Aşağıdaki metni TextFile1.txt dosyasına kopyalayın.  
  
    ```text  
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
  
3. Dosyayı kaydedin ve kapatın.  
  
#### <a name="to-create-a-sample-application-that-uses-the-custom-dynamic-object"></a>Özel dinamik nesneyi kullanan örnek bir uygulama oluşturmak için  
  
1. **Çözüm Gezgini'nde**Visual Basic kullanıyorsanız Module1.vb dosyasına çift tıklayın veya Visual C# kullanıyorsanız Program.cs dosyasını tıklatın.  
  
2. TextFile1.txt dosyası için `ReadOnlyFile` sınıfın bir örneğini oluşturmak için Ana yordamına aşağıdaki kodu ekleyin. Kod, dinamik üyeleri çağırmak ve "Müşteri" dizesini içeren metin satırlarını almak için geç bağlama kullanır.  
  
     [!code-csharp[VbDynamicWalkthrough#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/program.cs#8)]
     [!code-vb[VbDynamicWalkthrough#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/module1.vb#8)]
  
3. Uygulamayı oluşturmak ve çalıştırmak için dosyayı kaydedin ve CTRL+F5 tuşuna basın.  
  
## <a name="calling-a-dynamic-language-library"></a>Dinamik Dil Kitaplığı Arama  

Bu geçiş te oluşturduğunuz bir sonraki proje, dinamik dilde yazılmış bir kitaplık olan IronPython'a erişir.
  
### <a name="to-create-a-custom-dynamic-class"></a>Özel dinamik bir sınıf oluşturmak için
  
1. Visual Studio'da, **Dosya** menüsünde **Yeni'yi** işaret edin ve **Project'i**tıklatın.  
  
2. Yeni **Proje** iletişim kutusunda, **Proje Türleri** bölmesinde **Windows'un** seçildiğinden emin olun. **Şablonlar** bölmesinde **Konsol Uygulaması'nı** seçin. **Ad** kutusuna, `DynamicIronPythonSample`''yı yazın ve sonra **Tamam'ı**tıklatın. Yeni proje oluşturuldu.  
  
3. Visual Basic kullanıyorsanız, DynamicIronPythonSample projesini sağ tıklatın ve ardından **Özellikler'i**tıklatın. **Başvurular** sekmesini tıklatın. **Ekle** düğmesini tıklatın. Visual C# kullanıyorsanız, **Çözüm Gezgini'nde,** **Başvurular** klasörüne sağ tıklayın ve ardından **Başvuru Ekle'yi**tıklatın.  
  
4. **Gözat** sekmesinde, IronPython kitaplıklarının yüklü olduğu klasöre göz atın. Örneğin, C:\Program Files\IronPython 2.6 için .NET 4.0. **IronPython.dll,** **IronPython.Modules.dll,** **Microsoft.Scripting.dll**ve **Microsoft.Dynamic.dll** kitaplıklarını seçin. **Tamam**'a tıklayın.  
  
5. Visual Basic kullanıyorsanız, Module1.vb dosyasını değiştirin. Visual C# kullanıyorsanız, Program.cs dosyasını edin.  
  
6. Dosyanın üst kısmında, IronPython kitaplıklarından `Microsoft.Scripting.Hosting` `IronPython.Hosting` ve ad alanlarını almak için aşağıdaki kodu ekleyin.  
  
    [!code-csharp[VbDynamicWalkthroughIronPython#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/cs/program.cs#1)]
    [!code-vb[VbDynamicWalkthroughIronPython#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/vb/module1.vb#1)]
  
7. Ana yöntemde, IronPython kitaplıklarını `Microsoft.Scripting.Hosting.ScriptRuntime` barındıracak yeni bir nesne oluşturmak için aşağıdaki kodu ekleyin. Nesne `ScriptRuntime` IronPython kitaplık modülrandom.py yükler.  
  
     [!code-csharp[VbDynamicWalkthroughIronPython#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/cs/program.cs#2)]
     [!code-vb[VbDynamicWalkthroughIronPython#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/vb/module1.vb#2)]
  
8. random.py modülü yüklemek için kod sonra, tamsayılar bir dizi oluşturmak için aşağıdaki kodu ekleyin. Dizi, dizideki `shuffle` değerleri rasgele sıralayan random.py modülü yöntemine aktarılır.  
  
     [!code-csharp[VbDynamicWalkthroughIronPython#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/cs/program.cs#3)]
     [!code-vb[VbDynamicWalkthroughIronPython#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/vb/module1.vb#3)]
  
9. Uygulamayı oluşturmak ve çalıştırmak için dosyayı kaydedin ve CTRL+F5 tuşuna basın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Dynamic?displayProperty=nameWithType>
- <xref:System.Dynamic.DynamicObject?displayProperty=nameWithType>
- [Tür dinamiği kullanma](./using-type-dynamic.md)
- [Erken ve Geç Ciltleme](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
- [Dinamik](../../language-reference/builtin-types/reference-types.md)
- [Dinamik Arabirimlerin Uygulanması (Microsoft TechNet'ten indirilebilir PDF)](https://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/implementing-dynamic-interfaces.pdf)
