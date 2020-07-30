---
title: 'İzlenecek yol: Dinamik Nesneler Oluşturma ve Kullanma (C# and Visual Basic)'
description: Bu kılavuzda dinamik nesneler oluşturma ve kullanma hakkında bilgi edinin. Özel bir dinamik nesne ve ' IronPython ' kitaplığı kullanan bir proje oluşturun.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dynamic objects [Visual Basic]
- dynamic objects
- dynamic objects [C#]
ms.assetid: 568f1645-1305-4906-8625-5d77af81e04f
ms.openlocfilehash: 144651d3b14f6f6093ab07f1df7be10e6d05ae89
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381261"
---
# <a name="walkthrough-creating-and-using-dynamic-objects-c-and-visual-basic"></a>İzlenecek yol: Dinamik Nesneler Oluşturma ve Kullanma (C# and Visual Basic)

Dinamik nesneler, derleme zamanında değil, çalışma zamanında Özellikler ve yöntemler gibi üyeleri kullanıma sunar. Bu, statik bir tür veya biçimle eşleşmeyen yapılarla çalışacak nesneler oluşturmanızı sağlar. Örneğin, geçerli HTML biçimlendirme öğelerinin ve özniteliklerin herhangi bir birleşimini içerebilen HTML Belge Nesne Modeli (DOM) başvurmak için dinamik bir nesne kullanabilirsiniz. Her HTML belgesi benzersiz olduğundan, belirli bir HTML belgesi üyeleri çalışma zamanında belirlenir. Bir HTML öğesinin özniteliğine başvurmak için ortak bir yöntem özniteliğin adını `GetProperty` öğesi yöntemine geçirmektir. `id`HTML öğesinin özniteliğine başvurmak için `<div id="Div1">` , önce öğesine bir başvuru alın `<div>` ve ardından öğesini kullanın `divElement.GetProperty("id")` . Dinamik bir nesne kullanıyorsanız, `id` özniteliğe olarak başvurabilirsiniz `divElement.id` .  
  
 Dinamik nesneler IronPython ve IronRuby gibi dinamik dillere de kolay erişim sağlar. Çalışma zamanında yorumlanan dinamik bir betiğe başvurmak için dinamik bir nesne kullanabilirsiniz.  
  
 Geç bağlamayı kullanarak dinamik bir nesneye başvurabilirsiniz. C# ' de, bir geç bağlantılı nesnenin türünü olarak belirtirsiniz `dynamic` . Visual Basic, bir geç bağlantılı nesnenin türünü olarak belirtirsiniz `Object` . Daha fazla bilgi için bkz. [dinamik](../../language-reference/builtin-types/reference-types.md) ve [erken ve geç bağlama](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md).  
  
 Ad alanındaki sınıfları kullanarak özel dinamik nesneler oluşturabilirsiniz <xref:System.Dynamic?displayProperty=nameWithType> . Örneğin, bir oluşturup <xref:System.Dynamic.ExpandoObject> çalışma zamanında o nesnenin üyelerini belirtebilirsiniz. Ayrıca, sınıfını devralan kendi türünü de oluşturabilirsiniz <xref:System.Dynamic.DynamicObject> . Daha sonra <xref:System.Dynamic.DynamicObject> çalışma zamanı dinamik işlevselliği sağlamak için sınıfın üyelerini geçersiz kılabilirsiniz.  
  
 Bu kılavuzda, aşağıdaki görevleri yerine getirmeniz gerekir:  
  
- Bir metin dosyasının içeriğini dinamik olarak bir nesnenin özellikleri olarak sunan özel bir nesne oluşturun.  
  
- Kitaplığı kullanan bir proje oluşturun `IronPython` .  
  
## <a name="prerequisites"></a>Ön koşullar  

Bu izlenecek yolu tamamlamak için .NET için [IronPython](https://ironpython.net/) gerekir. En son sürümü edinmek için [indirme sayfasına](https://ironpython.net/download/) gidin.
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-a-custom-dynamic-object"></a>Özel dinamik nesne oluşturma

Bu izlenecek yolda oluşturduğunuz ilk proje, bir metin dosyasının içeriğini arayan özel bir dinamik nesne tanımlar. Aranacak metin, dinamik bir özelliğin adı ile belirtilir. Örneğin, kod çağırma belirtiyorsa `dynamicFile.Sample` dinamik sınıf, dosyadaki "Sample" ile başlayan tüm satırları içeren bir dize genel listesini döndürür. Arama büyük/küçük harfe duyarlıdır. Dinamik sınıf Ayrıca iki isteğe bağlı bağımsız değişkeni destekler. İlk bağımsız değişken, dinamik sınıfın satır başlangıcında, satırın sonunda veya satırdaki herhangi bir yerde eşleşmelerin aranması gerektiğini belirten bir arama seçeneği enum değeridir. İkinci bağımsız değişken, dinamik sınıfın, aramadan önce her satırdaki baştaki ve sondaki boşlukları kırpmalıdır. Örneğin, kod çağırma belirtiyorsa `dynamicFile.Sample(StringSearchOption.Contains)` dinamik sınıf, "Sample" öğesini bir satırda herhangi bir yerde arar. Çağıran kod belirtiyorsa `dynamicFile.Sample(StringSearchOption.StartsWith, false)` , dinamik sınıf her satırın başlangıcında "Sample" arar ve baştaki ve sondaki boşlukları kaldırmaz. Dinamik sınıfın varsayılan davranışı, her satırın başlangıcında bir eşleşme aramak ve baştaki ve sondaki boşlukları kaldırmak içindir.  
  
### <a name="to-create-a-custom-dynamic-class"></a>Özel bir dinamik sınıf oluşturmak için  
  
1. Visual Studio’yu çalıştırın.  
  
2. **Dosya** menüsünde, **Yeni** ' nin üzerine gelin ve ardından **Proje**' ye tıklayın.  
  
3. **Yeni proje** iletişim kutusunda, **Proje türleri** bölmesinde **Windows** ' un seçili olduğundan emin olun. **Şablonlar** bölmesinde **konsol uygulaması** ' nı seçin. **Ad** kutusuna yazın `DynamicSample` ve ardından **Tamam**' a tıklayın. Yeni proje oluşturulur.  
  
4. DynamicSample projesine sağ tıklayın ve **Ekle**' nin üzerine gelin ve ardından **sınıf**' a tıklayın. **Ad** kutusuna yazın `ReadOnlyFile` ve ardından **Tamam**' a tıklayın. ReadOnlyFile sınıfını içeren yeni bir dosya eklenir.  
  
5. ReadOnlyFile.cs veya ReadOnlyFile. vb dosyasının en üstünde, <xref:System.IO?displayProperty=nameWithType> ve ad alanlarını içeri aktarmak için aşağıdaki kodu ekleyin <xref:System.Dynamic?displayProperty=nameWithType> .  

    [!code-csharp[VbDynamicWalkthrough#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#1)]
    [!code-vb[VbDynamicWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#1)]  

6. Özel dinamik nesne, arama ölçütlerini bulmak için bir sabit listesi kullanır. Class ifadesinden önce aşağıdaki sabit listesi tanımını ekleyin.  
  
    [!code-csharp[VbDynamicWalkthrough#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#2)]
    [!code-vb[VbDynamicWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#2)]
  
7. Aşağıdaki kod örneğinde gösterildiği gibi sınıfını devralması için Class ifadesini güncelleştirin `DynamicObject` .  
  
    [!code-csharp[VbDynamicWalkthrough#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#3)]
    [!code-vb[VbDynamicWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#3)]

8. `ReadOnlyFile`Dosya yolu ve sınıf için bir Oluşturucu için özel bir alan tanımlamak üzere sınıfına aşağıdaki kodu ekleyin `ReadOnlyFile` .  
  
    [!code-csharp[VbDynamicWalkthrough#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#4)]
    [!code-vb[VbDynamicWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#4)]
  
9. `ReadOnlyFile` sınıfına aşağıdaki `GetPropertyValue` yöntemini ekleyin. `GetPropertyValue`Yöntemi giriş, arama ölçütü olarak alır ve bu arama ölçütleriyle eşleşen bir metin dosyasındaki satırları döndürür. Sınıfı tarafından sunulan dinamik yöntemler `ReadOnlyFile` , `GetPropertyValue` ilgili sonuçlarını almak için yöntemini çağırır.  
  
    [!code-csharp[VbDynamicWalkthrough#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#5)]
    [!code-vb[VbDynamicWalkthrough#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#5)]  
  
10. Yönteminden sonra `GetPropertyValue` , sınıfının yöntemini geçersiz kılmak için aşağıdaki kodu ekleyin <xref:System.Dynamic.DynamicObject.TryGetMember%2A> <xref:System.Dynamic.DynamicObject> . <xref:System.Dynamic.DynamicObject.TryGetMember%2A>Yöntemi, dinamik bir sınıfın bir üyesi istendiğinde ve hiçbir bağımsız değişken belirtilmediğinde çağrılır. `binder`Bağımsız değişkeni başvurulan üye hakkında bilgi içerir ve `result` bağımsız değişken belirtilen üye için döndürülen sonuca başvurur. <xref:System.Dynamic.DynamicObject.TryGetMember%2A>Yöntemi, istenen üye varsa döndüren bir Boolean değer döndürür `true` ; Aksi takdirde döndürür `false` .  
  
    [!code-csharp[VbDynamicWalkthrough#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#6)]
    [!code-vb[VbDynamicWalkthrough#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#6)]
  
11. Yönteminden sonra `TryGetMember` , sınıfının yöntemini geçersiz kılmak için aşağıdaki kodu ekleyin <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> <xref:System.Dynamic.DynamicObject> . <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A>Yöntemi, bağımsız değişkenlerle bir dinamik sınıfın bir üyesi istendiğinde çağrılır. `binder`Bağımsız değişkeni başvurulan üye hakkında bilgi içerir ve `result` bağımsız değişken belirtilen üye için döndürülen sonuca başvurur. `args`Bağımsız değişkeni, üyeye geçirilen bağımsız değişkenlerin bir dizisini içerir. <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A>Yöntemi, istenen üye varsa döndüren bir Boolean değer döndürür `true` ; Aksi takdirde döndürür `false` .  
  
    Yöntemin özel sürümü, `TryInvokeMember` ilk bağımsız değişkenin `StringSearchOption` önceki adımda tanımladığınız numaralandırıcıdan bir değer olmasını bekler. `TryInvokeMember`Yöntemi ikinci bağımsız değişkenin bir Boole değeri olmasını bekler. Bağımsız değişkenlerden biri veya her ikisi de geçerli değerlerdir, `GetPropertyValue` sonuçları almak için yönteme geçirilir.  
  
    [!code-csharp[VbDynamicWalkthrough#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#7)]
    [!code-vb[VbDynamicWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#7)]
  
12. Dosyayı kaydedin ve kapatın.  
  
#### <a name="to-create-a-sample-text-file"></a>Örnek metin dosyası oluşturmak için  
  
1. DynamicSample projesine sağ tıklayın ve **Ekle**' nin üzerine gelin ve ardından **Yeni öğe**' ye tıklayın. **Yüklü şablonlar** bölmesinde, **genel**' i seçin ve sonra **metin dosyası** şablonunu seçin. **Ad** kutusunda TextFile1.txt varsayılan adını bırakın ve ardından **Ekle**' ye tıklayın. Projeye yeni bir metin dosyası eklenir.  
  
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
  
#### <a name="to-create-a-sample-application-that-uses-the-custom-dynamic-object"></a>Özel dinamik nesneyi kullanan bir örnek uygulama oluşturmak için  
  
1. **Çözüm Gezgini**, Visual C# kullanıyorsanız Visual Basic veya program.cs dosyasını kullanıyorsanız Module1. vb dosyasını çift tıklayın.  
  
2. TextFile1.txt dosyasının sınıfının bir örneğini oluşturmak için aşağıdaki kodu ana yordama ekleyin `ReadOnlyFile` . Kod, dinamik üyeleri çağırmak ve "Customer" dizesini içeren metnin satırlarını almak için geç bağlamayı kullanır.  
  
     [!code-csharp[VbDynamicWalkthrough#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/program.cs#8)]
     [!code-vb[VbDynamicWalkthrough#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/module1.vb#8)]
  
3. Dosyayı kaydedin ve uygulamayı derlemek ve çalıştırmak için CTRL + F5 tuşlarına basın.  
  
## <a name="calling-a-dynamic-language-library"></a>Dinamik dil kitaplığı çağırma  

Bu kılavuzda oluşturduğunuz sonraki proje, IronPython dinamik dilinde yazılmış bir kitaplığa erişir.
  
### <a name="to-create-a-custom-dynamic-class"></a>Özel bir dinamik sınıf oluşturmak için
  
1. Visual Studio 'da, **Dosya** menüsünde, **Yeni** ' nin üzerine gelin ve ardından **Proje**' ye tıklayın.  
  
2. **Yeni proje** iletişim kutusunda, **Proje türleri** bölmesinde **Windows** ' un seçili olduğundan emin olun. **Şablonlar** bölmesinde **konsol uygulaması** ' nı seçin. **Ad** kutusuna yazın `DynamicIronPythonSample` ve ardından **Tamam**' a tıklayın. Yeni proje oluşturulur.  
  
3. Visual Basic kullanıyorsanız, DynamicIronPythonSample projesine sağ tıklayın ve ardından **Özellikler**' e tıklayın. **Başvurular** sekmesine tıklayın. **Ekle** düğmesine tıklayın. Visual C# kullanıyorsanız, **Çözüm Gezgini**, **Başvurular** klasörüne sağ tıklayın ve ardından **Başvuru Ekle**' ye tıklayın.  
  
4. **Araştır** sekmesinde, IronPython kitaplıklarının yüklendiği klasöre gidin. Örneğin, .NET 4,0 için C:\Program Files\ıronpython 2,6. **IronPython.dll**, **IronPython.Modules.dll**, **Microsoft.Scripting.dll**ve **Microsoft.Dynamic.dll** kitaplıklarını seçin. **Tamam** düğmesine tıklayın.  
  
5. Visual Basic kullanıyorsanız, Module1. vb dosyasını düzenleyin. Visual C# kullanıyorsanız, Program.cs dosyasını düzenleyin.  
  
6. Dosyasının en üstüne, `Microsoft.Scripting.Hosting` ve `IronPython.Hosting` ad alanlarını IronPython kitaplıklarından içeri aktarmak için aşağıdaki kodu ekleyin.  
  
    [!code-csharp[VbDynamicWalkthroughIronPython#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/cs/program.cs#1)]
    [!code-vb[VbDynamicWalkthroughIronPython#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/vb/module1.vb#1)]
  
7. Ana yöntemde, `Microsoft.Scripting.Hosting.ScriptRuntime` IronPython kitaplıklarını barındırmak üzere yeni bir nesne oluşturmak için aşağıdaki kodu ekleyin. `ScriptRuntime`Nesnesi IronPython kitaplığı modülünü Random.py yükler.  
  
     [!code-csharp[VbDynamicWalkthroughIronPython#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/cs/program.cs#2)]
     [!code-vb[VbDynamicWalkthroughIronPython#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/vb/module1.vb#2)]
  
8. Random.py modülünü yüklemeye yönelik koddan sonra, bir tamsayılar dizisi oluşturmak için aşağıdaki kodu ekleyin. Dizi, `shuffle` dizideki değerleri rastgele sıralayan Random.py modülünün yöntemine geçirilir.  
  
     [!code-csharp[VbDynamicWalkthroughIronPython#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/cs/program.cs#3)]
     [!code-vb[VbDynamicWalkthroughIronPython#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/vb/module1.vb#3)]
  
9. Dosyayı kaydedin ve uygulamayı derlemek ve çalıştırmak için CTRL + F5 tuşlarına basın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Dynamic?displayProperty=nameWithType>
- <xref:System.Dynamic.DynamicObject?displayProperty=nameWithType>
- [Tür dinamiği kullanma](./using-type-dynamic.md)
- [Erken ve geç bağlama](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
- [dinamik](../../language-reference/builtin-types/reference-types.md)
- [Dinamik arabirimleri uygulama (Microsoft TechNet 'ten indirilebilir PDF)](https://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/implementing-dynamic-interfaces.pdf)
