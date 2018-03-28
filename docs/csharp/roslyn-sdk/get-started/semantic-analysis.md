---
title: Anlam Analizi ile çalışmaya başlama
description: Bu öğreticide, .NET derleme SDK'sını kullanarak anlamsal Analizi ile çalışma genel bir bakış sağlar.
author: billwagner
ms.author: wiwagn
ms.date: 02/06/2018
ms.topic: conceptual
ms.prod: .net
ms.devlang: devlang-csharp
ms.custom: mvc
ms.openlocfilehash: b9921bc3621d6abfc37b1bf1fc4f481620ccc407
ms.sourcegitcommit: 935d5267c44f9bce801468ef95f44572f1417e8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/28/2018
---
# <a name="get-started-with-semantic-analysis"></a>Anlam Analizi ile çalışmaya başlama

Bu öğretici sözdizimi API ile tanıdık varsayar. [Sözdizimi Analizi ile çalışmaya başlama](syntax-analysis.md) makale yeterli giriş sağlar.

Bu öğreticide, keşfedin **simgesi** ve **bağlama API'leri**. Bu API'ları hakkında bilgi sağlamak _anlamsal anlamı_ bir programın. İsteyin ve programınızdaki herhangi bir simge ile temsil edilen türleri hakkında sorularını olanak sağlar.

Yüklemeniz gerekir **.NET derleyici Platform SDK**:

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

## <a name="understanding-compilations-and-symbols"></a>Anlama derlemeleri ve simgeler

Daha fazla .NET derleyici SDK ile çalışırken, sözdizimi API ve anlam API arasındaki farklılıklar öğrenmeniz. **Sözdizimi API** bakmak sayesinde _yapısı_ bir programın. Ancak, genellikle daha zengin bilgi semantiğini hakkında istediğiniz veya _anlamı_ bir programın. Gevşek kod dosyası ya da VB veya C# kod parçacığını yalıtım modunda sözdizimsel olarak çözümlenebilir olsa da, "Bu değişken türünü bir boşlukta nedir" gibi sorular sormak için anlamlı değil. Tür adı anlamını derleme başvurularını, ad alanı içe aktarımlarını veya diğer kod dosyaları bağımlı olabilir. Kullanarak bu soruları yanıtlanır **anlamsal API**, özellikle <xref:Microsoft.CodeAnalysis.Compilation?displayProperty=nameWithType> sınıfı.

Örneği <xref:Microsoft.CodeAnalysis.Compilation> derleyici tarafından görülen tek bir projeye paraleldir ve Visual Basic veya C# programı derlemek için gereken her şeyi temsil eder. **Derleme** derlenecek kaynak dosyaları kümesi, derleme başvurularını ve derleyici seçenekleri içerir. Diğer tüm bilgiler bu bağlamda kullanarak kod anlamı hakkında neden. A <xref:Microsoft.CodeAnalysis.Compilation> bulabilirsiniz **simgeleri** -türleri, ad alanları, üyeleri ve adları ve diğer ifadeleri başvuran değişkenler gibi varlıklar. Adları ve ifadeler ile ilişkilendirme işlemi **simgeleri** çağrılır **bağlama**.

Gibi <xref:Microsoft.CodeAnalysis.SyntaxTree?displayProperty=nameWithType>, <xref:Microsoft.CodeAnalysis.Compilation> dile özgü türevleri ile bir Özet sınıf. Derleme örneği oluştururken, üzerinde bir Üreteç yöntemi çağırmanız gerekir <xref:Microsoft.CodeAnalysis.CSharp.CSharpCompilation?displayProperty=nameWithType> (veya <xref:Microsoft.CodeAnalysis.VisualBasic.VisualBasicCompilation?displayProperty=nameWithType>) sınıfı.

## <a name="querying-symbols"></a>Simgeler sorgulama

Bu öğreticide, "Hello World" programı yeniden bakın. Bu süre, programın ne bu simgeleri göstermek türlerini anlamak için sembolleri sorgu. Bir ad alanındaki türler için sorgular ve bir türünde kullanılabilen yöntemler bulmayı öğrenin.

Bu örnek için tamamlanmış kod görebilirsiniz [GitHub depomuzda](https://github.com/dotnet/docs/tree/master/samples/csharp/roslyn-sdk/SemanticQuickStart).

> [!NOTE]
> Sözdizimi ağacı türleri devralma programı farklı konumlarda geçerli farklı söz dizimi öğeleri tanımlamak için kullanın. Genellikle bu API'leri kullanarak atama özellikleri veya belirli türetilmiş türler için koleksiyon üyeleri anlamına gelir. Aşağıdaki örneklerde, atama ve atamalar açıkça yazılan değişkenler kullanılarak ayrı deyim ' dir. Dönüş türleri API ve çalışma zamanı türü, döndürülen nesnelerin görmek için kodu okuyabilir. Uygulamada, incelenmesi nesnelerin türünü tanımlamak için API adları kullanır ve örtük olarak yazılan değişkenler kullanmak için daha yaygın bir durumdur.

Yeni C# oluşturma **tek başına kod analizi aracı** proje:

* Visual Studio'da, **dosya** > **yeni** > **proje** yeni proje iletişim kutusu görüntülemek için.
* Altında **Visual C#** > **genişletilebilirlik**, seçin **tek başına kod analizi aracı**.
* Projenizin adı "**SemanticQuickStart**" ve Tamam'ı tıklatın.

Temel "Hello World!" analiz etmeyi deneyeceğimiz daha önce gösterilen programı.
Bir sabit olarak Hello World program için metni ekleyin, `Program` sınıfı:

[!code-csharp[Declare the program test](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#1 "Declare a constant string for the program text to analyze")]

Ardından, kod metinde sözdizimi ağacı oluşturmak için aşağıdaki kodu ekleyin `programText` sabit.  Aşağıdaki satırı ekleyin, `Main` yöntemi:

[!code-csharp[Create the tree](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#2 "Create the syntax tree")]

Ardından, yapı bir <xref:Microsoft.CodeAnalysis.CSharp.CSharpCompilation> ağacından zaten oluşturulmuş. "Hello World" örnek dayanan <xref:System.String> ve <xref:System.Console> türleri. Bu iki derlemeniz türlerinde bildirir derleme başvurmanız gerekir. Aşağıdaki satırı ekleyin, `Main` yöntemi uygun derlemesine başvuru dahil olmak üzere, sözdizimi ağacı derlenmesini oluşturmak için:

[!code-csharp[Create the compilation](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#3 "Create the compilation for the semantic model")]

<xref:Microsoft.CodeAnalysis.CSharp.CSharpCompilation.AddReferences%2A?displayProperty=nameWithType> Yöntemi derleme başvurularını ekler. <xref:Microsoft.CodeAnalysis.MetadataReference.CreateFromFile%2A?displayProperty=nameWithType> Yöntemi bir başvuru olarak bir derleme yükler. 

## <a name="querying-the-semantic-model"></a>Anlam modeli sorgulama

Bulduktan sonra bir <xref:Microsoft.CodeAnalysis.Compilation> için sorabileceğiniz bir <xref:Microsoft.CodeAnalysis.SemanticModel> herhangi <xref:Microsoft.CodeAnalysis.SyntaxTree> uygulamasında bulunan <xref:Microsoft.CodeAnalysis.Compilation>. Anlam modeli, normalde IntelliSense elde edebileceğiniz tüm bilgi kaynağı olarak düşünebilirsiniz. A <xref:Microsoft.CodeAnalysis.SemanticModel> gibi soruları yanıtlamanıza "Adları bu konumda kapsamdaki nelerdir?", "hangi üyelerinin bu yönteminden erişilebilir?", "hangi değişkenler bu metin bloğunda kullanılır?" ve "Ne bu ad/ifade başvurmak?" Anlam modeli oluşturmak için bu deyim ekleyin:

[!code-csharp[Create the semantic model](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#4 "Create the semantic model")]

## <a name="binding-a-name"></a>Bir ad bağlama

<xref:Microsoft.CodeAnalysis.Compilation> Oluşturur <xref:Microsoft.CodeAnalysis.SemanticModel> gelen <xref:Microsoft.CodeAnalysis.SyntaxTree>. Model oluşturduktan sonra ilk bulmak için sorgulayabilirsiniz `using` yönerge ve sembol bilgilerini almak `System` ad alanı. Bu iki satır ekleyin, `Main` anlam modeli oluşturmak ve ilk simgesini almak için yöntemi deyimi kullanarak:

[!code-csharp[Find the namespace symbol for the first using](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#5 "Find the namespace symbol for the first using")]

Önceki kod ilk adı bağlanacağı gösterilmektedir `using` yönergesi almak için bir <xref:Microsoft.CodeAnalysis.SymbolInfo?displayProperty=nameWithType> için `System` ad alanı. Önceki kod Ayrıca, kullandığınız gösterilmektedir **sözdizimi modeli** ; kod yapısını bulmak için kullandığınız **anlam modeli** anlamlarını anlamak için. **Sözdizimi modeli** dizeyi bulur `System` kullanarak deyimi. **Anlam modeli** tanımlanan türleri hakkında tüm bilgiler `System` ad alanı.

Gelen <xref:Microsoft.CodeAnalysis.SymbolInfo> edinebilirsiniz nesne <xref:Microsoft.CodeAnalysis.ISymbol?displayProperty=nameWithType> kullanarak <xref:Microsoft.CodeAnalysis.SymbolInfo.Symbol?displayProperty=nameWithType> özelliği. Bu özellik bu ifade başvurduğu simgesini döndürür. Herhangi bir şeye (örneğin, sayısal değişmez değerleri) Bu özellik başvuran yok ifadeleri olduğu `null`. Zaman <xref:Microsoft.CodeAnalysis.SymbolInfo.Symbol?displayProperty=nameWithType> null değil <xref:Microsoft.CodeAnalysis.ISymbol.Kind?displayProperty=nameWithType> simgenin türünü gösterir. Bu örnekte, <xref:Microsoft.CodeAnalysis.ISymbol.Kind?displayProperty=nameWithType> özelliği bir <xref:Microsoft.CodeAnalysis.SymbolKind.Namespace?displayProperty=nameWithType>. Aşağıdaki kodu ekleyin, `Main` yöntemi. Simge için alır `System` ad alanı ve görüntüler tüm alt ad alanlarını içinde bildirilen `System` ad alanı:

[!code-csharp[Display all the child namespaces](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#6 "Display all the child namespaces from this compilation")]

Programını çalıştırın ve aşağıdaki çıktı görmeniz gerekir:

```
System.Collections
System.Configuration
System.Deployment
System.Diagnostics
System.Globalization
System.IO
System.Numerics
System.Reflection
System.Resources
System.Runtime
System.Security
System.StubHelpers
System.Text
System.Threading
Press any key to continue . . .
```

> [!NOTE]
> Çıkış alt ad alanı, her ad alanı içermeyen `System` ad alanı. Yalnızca bütünleştirilmiş koduna başvuruyor bu derlemede varsa her ad alanı görüntüler nerede `System.String` bildirilmedi. Bu derleme diğer derlemelerde bildirilen ad bilinmiyor

### <a name="binding-an-expression"></a>Bir ifade bağlama

Önceki kod, bir ad bağlayarak bir sembol bulmak gösterilmiştir. Adları olmayan diğer ifadeler bağlanabilen bir C# programında vardır. Bu özellik göstermek için şimdi basit bir dize sabit değeri bağlamayı erişin.

"Hello World" programı içeren bir <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LiteralExpressionSyntax?displayProperty=nameWithType>, "Hello, World!" konsolda görüntülenen dize.

"Hello, World!" Bul tek bir dize programa değişmez değer bulma tarafından dizesi. Ardından, sözdizimi düğümü bulunan sonra tür bilgi bu düğüm için anlam modeli alın. Aşağıdaki kodu ekleyin, `Main` yöntemi:

[!code-csharp[Find the namespace symbol for the only using](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#7 "Find the namespace symbol for the only using")]

<xref:Microsoft.CodeAnalysis.TypeInfo?displayProperty=nameWithType> Yapı içeren bir <xref:Microsoft.CodeAnalysis.TypeInfo.Type?displayProperty=nameWithType> özelliği sabit türü anlamsal bilgilerine erişim sağlar. Bu örnekte, o `string` türü. Bu özellik yerel bir değişkene atar bir bildirimi ekleyin:

[!code-csharp[Find the semantic information about the string type](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#8 "Use the string literal to access the semantic information in the string type.")]

Bu öğreticiyi tamamlamak için şimdi tüm genel yöntemler bildirilen bir dizi oluşturan bir LINQ sorgusu yapı `string` , dönüş türü bir `string`. Bu sorgu karmaşık sağlandığından, yapı satır alır, tek bir sorgu yeniden yapılandırma. Bu sorgu için kaynak üzerinde bildirilen tüm üyeleri dizisidir `string` türü:

[!code-csharp[Access the sequence of members on the string type](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#9 "Access the sequence of members on the string type.")]

Bu kaynak sırası karakterlerine özellikleri ve alanları da dahil olmak üzere tüm üyeleri bu nedenle kullanarak filtre <xref:System.Collections.Immutable.ImmutableArray%601.OfType%2A?displayProperty=nameWithType> yöntemi Bul öğesine <xref:Microsoft.CodeAnalysis.IMethodSymbol?diplayProperty=nameWithType> nesneler:

[!code-csharp[Filter the sequence to only methods](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#10 "Find the subset of the collection that is the methods.")]

Ardından, yalnızca genel ve dönüş yöntemlerini döndürmek için başka bir filtre Ekle bir `string`:

[!code-csharp[Filter on return type and accessibility](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#11 "Find only the public methods that return a string.")]

Yalnızca ad özelliği ve yalnızca DISTINCT adlarını herhangi aşırı kaldırarak seçin:

[!code-csharp[find the distinct names.](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#12 "Use the string literal to access the semantic information in the string type.")]

Ayrıca LINQ sorgu sözdizimini kullanarak tam sorgusu oluşturun ve sonra konsolda tüm yöntemi adlarını görüntülemek:

[!code-csharp[build and display the results of this query.](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#12 "Build and display the results of the query.")]

Derleme ve programı çalıştırın. Şu çıktı görmeniz gerekir:

```
Join
Substring
Trim
TrimStart
TrimEnd
Normalize
PadLeft
PadRight
ToLower
ToLowerInvariant
ToUpper
ToUpperInvariant
ToString
Insert
Replace
Remove
Format
Copy
Concat
Intern
IsInterned
Press any key to continue . . .
```
Anlam API bulmak ve bu programın parçası olan simgeler hakkında bilgi görüntülemek için kullandığınız.
