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
ms.openlocfilehash: aa902ffaf93c8e1f273ed476dc7d413bcfce914c
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73417583"
---
# <a name="walkthrough-creating-and-using-dynamic-objects-c-and-visual-basic"></a>İzlenecek yol: Dinamik Nesneler Oluşturma ve Kullanma (C# and Visual Basic)

Dinamik nesneler, derleme zamanında değil, çalışma zamanında Özellikler ve yöntemler gibi üyeleri kullanıma sunar. Bu, statik bir tür veya biçimle eşleşmeyen yapılarla çalışacak nesneler oluşturmanızı sağlar. Örneğin, geçerli HTML biçimlendirme öğelerinin ve özniteliklerin herhangi bir birleşimini içerebilen HTML Belge Nesne Modeli (DOM) başvurmak için dinamik bir nesne kullanabilirsiniz. Her HTML belgesi benzersiz olduğundan, belirli bir HTML belgesi üyeleri çalışma zamanında belirlenir. HTML öğesinin bir özniteliğine başvurmak için ortak bir yöntem, özniteliğin adını öğesinin `GetProperty` metoduna geçirmektir. HTML öğesi `<div id="Div1">``id` özniteliğine başvurmak için, önce `<div>` öğesine bir başvuru alın ve ardından `divElement.GetProperty("id")`kullanın. Dinamik bir nesne kullanıyorsanız, `divElement.id`olarak `id` özniteliğine başvurabilirsiniz.  
  
 Dinamik nesneler IronPython ve IronRuby gibi dinamik dillere de kolay erişim sağlar. Çalışma zamanında yorumlanan dinamik bir betiğe başvurmak için dinamik bir nesne kullanabilirsiniz.  
  
 Geç bağlamayı kullanarak dinamik bir nesneye başvurabilirsiniz. İçinde C#, bir geç bağlantılı nesnenin türünü `dynamic`olarak belirtirsiniz. Visual Basic, bir geç bağlantılı nesnenin türünü `Object`olarak belirtirsiniz. Daha fazla bilgi için bkz. [dinamik](../../language-reference/builtin-types/reference-types.md) ve [erken ve geç bağlama](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md).  
  
 <xref:System.Dynamic?displayProperty=nameWithType> ad alanındaki sınıfları kullanarak özel dinamik nesneler oluşturabilirsiniz. Örneğin, bir <xref:System.Dynamic.ExpandoObject> oluşturabilir ve çalışma zamanında o nesnenin üyelerini belirtebilirsiniz. Ayrıca, <xref:System.Dynamic.DynamicObject> sınıfını devralan kendi türünü de oluşturabilirsiniz. Sonra, çalışma zamanı dinamik işlevselliği sağlamak için <xref:System.Dynamic.DynamicObject> sınıfının üyelerini geçersiz kılabilirsiniz.  
  
 Bu kılavuzda, aşağıdaki görevleri yerine getirmeniz gerekir:  
  
- Bir metin dosyasının içeriğini dinamik olarak bir nesnenin özellikleri olarak sunan özel bir nesne oluşturun.  
  
- `IronPython` kitaplığı kullanan bir proje oluşturun.  
  
## <a name="prerequisites"></a>Prerequisites  

Bu izlenecek yolu tamamlamak için .NET için [IronPython](https://ironpython.net/) gerekir. En son sürümü edinmek için [indirme sayfasına](https://ironpython.net/download/) gidin.
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-a-custom-dynamic-object"></a>Özel dinamik nesne oluşturma

Bu izlenecek yolda oluşturduğunuz ilk proje, bir metin dosyasının içeriğini arayan özel bir dinamik nesne tanımlar. Aranacak metin, dinamik bir özelliğin adı ile belirtilir. Örneğin, kod çağırma `dynamicFile.Sample`belirtiyorsa, dinamik sınıf, dosyadaki "Sample" ile başlayan tüm satırları içeren bir dize genel listesini döndürür. Arama büyük/küçük harfe duyarlıdır. Dinamik sınıf Ayrıca iki isteğe bağlı bağımsız değişkeni destekler. İlk bağımsız değişken, dinamik sınıfın satır başlangıcında, satırın sonunda veya satırdaki herhangi bir yerde eşleşmelerin aranması gerektiğini belirten bir arama seçeneği enum değeridir. İkinci bağımsız değişken, dinamik sınıfın, aramadan önce her satırdaki baştaki ve sondaki boşlukları kırpmalıdır. Örneğin, kod çağırma `dynamicFile.Sample(StringSearchOption.Contains)`belirtiyorsa dinamik sınıf, "Sample" öğesini bir satırda herhangi bir yerde arar. Kod çağırma `dynamicFile.Sample(StringSearchOption.StartsWith, false)`belirtiyorsa, dinamik sınıf her satırın başlangıcında "Sample" arar ve baştaki ve sondaki boşlukları kaldırmaz. Dinamik sınıfın varsayılan davranışı, her satırın başlangıcında bir eşleşme aramak ve baştaki ve sondaki boşlukları kaldırmak içindir.  
  
### <a name="to-create-a-custom-dynamic-class"></a>Özel bir dinamik sınıf oluşturmak için  
  
1. Visual Studio 'Yu başlatın.  
  
2. **Dosya** menüsünde, **Yeni** ' nin üzerine gelin ve ardından **Proje**' ye tıklayın.  
  
3. **Yeni proje** iletişim kutusunda, **Proje türleri** bölmesinde **Windows** ' un seçili olduğundan emin olun. **Şablonlar** bölmesinde **konsol uygulaması** ' nı seçin. **Ad** kutusuna `DynamicSample`yazın ve ardından **Tamam**' a tıklayın. Yeni proje oluşturulur.  
  
4. DynamicSample projesine sağ tıklayın ve **Ekle**' nin üzerine gelin ve ardından **sınıf**' a tıklayın. **Ad** kutusuna `ReadOnlyFile`yazın ve ardından **Tamam**' a tıklayın. ReadOnlyFile sınıfını içeren yeni bir dosya eklenir.  
  
5. ReadOnlyFile.cs veya ReadOnlyFile. vb dosyasının en üstünde, <xref:System.IO?displayProperty=nameWithType> ve <xref:System.Dynamic?displayProperty=nameWithType> ad alanlarını içeri aktarmak için aşağıdaki kodu ekleyin.  

    [!code-csharp[VbDynamicWalkthrough#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#1)]
    [!code-vb[VbDynamicWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#1)]  

6. Özel dinamik nesne, arama ölçütlerini bulmak için bir sabit listesi kullanır. Class ifadesinden önce aşağıdaki sabit listesi tanımını ekleyin.  
  
    [!code-csharp[VbDynamicWalkthrough#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#2)]
    [!code-vb[VbDynamicWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#2)]
  
7. Aşağıdaki kod örneğinde gösterildiği gibi, sınıf ifadesini `DynamicObject` sınıfını devralacak şekilde güncelleştirin.  
  
    [!code-csharp[VbDynamicWalkthrough#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#3)]
    [!code-vb[VbDynamicWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#3)]

8. Dosya yolu için bir özel alan ve `ReadOnlyFile` sınıfı için bir Oluşturucu tanımlamak üzere `ReadOnlyFile` sınıfına aşağıdaki kodu ekleyin.  
  
    [!code-csharp[VbDynamicWalkthrough#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#4)]
    [!code-vb[VbDynamicWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#4)]
  
9. Aşağıdaki `GetPropertyValue` yöntemini `ReadOnlyFile` sınıfına ekleyin. `GetPropertyValue` yöntemi giriş, arama ölçütü olarak alır ve bu arama ölçütleriyle eşleşen bir metin dosyasındaki satırları döndürür. `ReadOnlyFile` sınıfı tarafından sunulan dinamik yöntemler, ilgili sonuçlarını almak için `GetPropertyValue` yöntemini çağırır.  
  
    [!code-csharp[VbDynamicWalkthrough#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#5)]
    [!code-vb[VbDynamicWalkthrough#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#5)]  
  
10. `GetPropertyValue` yönteminden sonra, <xref:System.Dynamic.DynamicObject> sınıfının <xref:System.Dynamic.DynamicObject.TryGetMember%2A> metodunu geçersiz kılmak için aşağıdaki kodu ekleyin. <xref:System.Dynamic.DynamicObject.TryGetMember%2A> yöntemi, dinamik bir sınıfın bir üyesi istendiğinde ve hiçbir bağımsız değişken belirtilmediğinde çağrılır. `binder` bağımsız değişkeni, başvurulan üye hakkında bilgi içerir ve `result` bağımsız değişkeni belirtilen üye için döndürülen sonuca başvurur. <xref:System.Dynamic.DynamicObject.TryGetMember%2A> yöntemi, istenen üye varsa `true` döndüren bir Boolean değer döndürür; Aksi takdirde `false`döndürür.  
  
    [!code-csharp[VbDynamicWalkthrough#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#6)]
    [!code-vb[VbDynamicWalkthrough#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#6)]
  
11. `TryGetMember` yönteminden sonra, <xref:System.Dynamic.DynamicObject> sınıfının <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> metodunu geçersiz kılmak için aşağıdaki kodu ekleyin. Bağımsız değişkenlerle bir dinamik sınıfın üyesi istendiğinde <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> yöntemi çağrılır. `binder` bağımsız değişkeni, başvurulan üye hakkında bilgi içerir ve `result` bağımsız değişkeni belirtilen üye için döndürülen sonuca başvurur. `args` bağımsız değişkeni, üyeye geçirilen bağımsız değişkenlerin bir dizisini içerir. <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> yöntemi, istenen üye varsa `true` döndüren bir Boolean değer döndürür; Aksi takdirde `false`döndürür.  
  
    `TryInvokeMember` yönteminin özel sürümü, ilk bağımsız değişkenin önceki adımda tanımladığınız `StringSearchOption` numaralandırmasından bir değer olmasını bekler. `TryInvokeMember` yöntemi ikinci bağımsız değişkenin bir Boole değeri olmasını bekler. Bağımsız değişkenlerden biri veya her ikisi de geçerli değerlerdir, sonuçları almak için `GetPropertyValue` yöntemine geçirilir.  
  
    [!code-csharp[VbDynamicWalkthrough#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#7)]
    [!code-vb[VbDynamicWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#7)]
  
12. Dosyayı kaydedin ve kapatın.  
  
#### <a name="to-create-a-sample-text-file"></a>Örnek metin dosyası oluşturmak için  
  
1. DynamicSample projesine sağ tıklayın ve **Ekle**' nin üzerine gelin ve ardından **Yeni öğe**' ye tıklayın. **Yüklü şablonlar** bölmesinde, **genel**' i seçin ve sonra **metin dosyası** şablonunu seçin. **Ad** kutusunda TextFile1. txt varsayılan adını bırakın ve **Ekle**' ye tıklayın. Projeye yeni bir metin dosyası eklenir.  
  
2. Aşağıdaki metni TextFile1. txt dosyasına kopyalayın.  
  
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
  
1. **Çözüm Gezgini**, Visual C#kullanıyorsanız Visual Basic veya program.cs dosyasını kullanıyorsanız Module1. vb dosyasını çift tıklayın.  
  
2. TextFile1. txt dosyasının `ReadOnlyFile` sınıfının bir örneğini oluşturmak için aşağıdaki kodu ana yordama ekleyin. Kod, dinamik üyeleri çağırmak ve "Customer" dizesini içeren metnin satırlarını almak için geç bağlamayı kullanır.  
  
     [!code-csharp[VbDynamicWalkthrough#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/program.cs#8)]
     [!code-vb[VbDynamicWalkthrough#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/module1.vb#8)]
  
3. Dosyayı kaydedin ve uygulamayı derlemek ve çalıştırmak için CTRL + F5 tuşlarına basın.  
  
## <a name="calling-a-dynamic-language-library"></a>Dinamik dil kitaplığı çağırma  

Bu kılavuzda oluşturduğunuz sonraki proje, IronPython dinamik dilinde yazılmış bir kitaplığa erişir.
  
### <a name="to-create-a-custom-dynamic-class"></a>Özel bir dinamik sınıf oluşturmak için
  
1. Visual Studio 'da, **Dosya** menüsünde, **Yeni** ' nin üzerine gelin ve ardından **Proje**' ye tıklayın.  
  
2. **Yeni proje** iletişim kutusunda, **Proje türleri** bölmesinde **Windows** ' un seçili olduğundan emin olun. **Şablonlar** bölmesinde **konsol uygulaması** ' nı seçin. **Ad** kutusuna `DynamicIronPythonSample`yazın ve ardından **Tamam**' a tıklayın. Yeni proje oluşturulur.  
  
3. Visual Basic kullanıyorsanız, DynamicIronPythonSample projesine sağ tıklayın ve ardından **Özellikler**' e tıklayın. **Başvurular** sekmesine tıklayın. **Ekle** düğmesine tıklayın. Görsel C#kullanıyorsanız, **Çözüm Gezgini**' de **Başvurular** klasörüne sağ tıklayın ve ardından **Başvuru Ekle**' ye tıklayın.  
  
4. **Araştır** sekmesinde, IronPython kitaplıklarının yüklendiği klasöre gidin. Örneğin, .NET 4,0 için C:\Program Files\ıronpython 2,6. **IronPython. dll**, **IronPython. Modules. dll**, **Microsoft. Scripting. dll**ve **Microsoft. Dynamic. dll** kitaplıklarını seçin. **Tamam**'a tıklayın.  
  
5. Visual Basic kullanıyorsanız, Module1. vb dosyasını düzenleyin. Görsel C#kullanıyorsanız, program.cs dosyasını düzenleyin.  
  
6. Dosyanın en üstüne, `Microsoft.Scripting.Hosting` ve `IronPython.Hosting` ad alanlarını IronPython kitaplıklarından içeri aktarmak için aşağıdaki kodu ekleyin.  
  
    [!code-csharp[VbDynamicWalkthroughIronPython#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/cs/program.cs#1)]
    [!code-vb[VbDynamicWalkthroughIronPython#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/vb/module1.vb#1)]
  
7. Ana yöntemde, IronPython kitaplıklarını barındırmak üzere yeni bir `Microsoft.Scripting.Hosting.ScriptRuntime` nesnesi oluşturmak için aşağıdaki kodu ekleyin. `ScriptRuntime` nesnesi IronPython kitaplığı modülünü random.py yükler.  
  
     [!code-csharp[VbDynamicWalkthroughIronPython#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/cs/program.cs#2)]
     [!code-vb[VbDynamicWalkthroughIronPython#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/vb/module1.vb#2)]
  
8. Random.py modülünü yüklemeye yönelik koddan sonra, bir tamsayılar dizisi oluşturmak için aşağıdaki kodu ekleyin. Dizi, dizideki değerleri rastgele sıralayan random.py modülünün `shuffle` yöntemine geçirilir.  
  
     [!code-csharp[VbDynamicWalkthroughIronPython#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/cs/program.cs#3)]
     [!code-vb[VbDynamicWalkthroughIronPython#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/vb/module1.vb#3)]
  
9. Dosyayı kaydedin ve uygulamayı derlemek ve çalıştırmak için CTRL + F5 tuşlarına basın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Dynamic?displayProperty=nameWithType>
- <xref:System.Dynamic.DynamicObject?displayProperty=nameWithType>
- [Tür dinamiği kullanma](./using-type-dynamic.md)
- [Erken ve Geç Bağlama](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
- [dynamic](../../language-reference/builtin-types/reference-types.md)
- [Dinamik arabirimleri uygulama (Microsoft TechNet 'ten indirilebilir PDF)](https://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/implementing-dynamic-interfaces.pdf)
