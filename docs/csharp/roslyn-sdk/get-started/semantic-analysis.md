---
title: Anlam Analizi ile çalışmaya başlama
description: Bu öğretici, .NET derleyici SDK'sını kullanarak anlam Analizi ile çalışmaya genel bir bakış sağlar.
ms.date: 02/06/2018
ms.custom: mvc
ms.openlocfilehash: 188104c3430b4ca32578cd35d3e161a6eb0e0e1a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61676072"
---
# <a name="get-started-with-semantic-analysis"></a>Anlam Analizi ile çalışmaya başlama

Bu öğreticide söz dizimi API ile ilgili bilgi sahibi olduğunuz varsayılır. [Söz dizimi Analizi ile çalışmaya başlama](syntax-analysis.md) makale yeterli giriş sağlar.

Bu öğreticide, Keşif **sembol** ve **bağlama API'leri**. Bu API'ler hakkında bilgi sağlar. _anlam_ programının. Soru sormak ve programınızda herhangi bir simge ile temsil edilen türleri hakkında soruları yanıtlamak etkinleştirin.

Yüklemeniz gerekir **.NET derleyici Platformu SDK'sı**:

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

## <a name="understanding-compilations-and-symbols"></a>Derlemeleri anlama ve semboller

Daha fazla .NET derleyici SDK'sı ile çalışırken, söz dizimi API ve anlam API arasındaki farklılıklar hakkında bilgi sahibi olur. **Söz dizimi API** görmenize olanak tanır _yapısı_ programının. Ancak, genellikle daha zengin bilgi semantiği istersiniz veya _anlamı_ programının. Gevşek bir kod dosyası veya VB veya C# kod parçacığını yalıtım modunda sözdizimsel olarak çözümlenebilir olsa, "Bu değişken türünde bir boşlukta nedir" gibi sorular sorun anlamlı değildir. Bir tür adı anlamını derleme başvuruları, ad alanı içeri aktarmaları veya diğer kod dosyaları bağımlı olabilir. Kullanarak bu soruları yanıtlanır **anlam API**, özellikle <xref:Microsoft.CodeAnalysis.Compilation?displayProperty=nameWithType> sınıfı.

Örneği <xref:Microsoft.CodeAnalysis.Compilation> derleyici tarafından görülen şekilde tek bir projeye benzer ve Visual Basic veya C# programı derlemek için gereken her şeyi temsil eder. **Derleme** derlenecek kaynak dosyaları, bütünleştirilmiş kod başvuruları ve derleyici seçenekleri içerir. Bu bağlam içinde ve diğer bilgileri kullanarak kodun anlamı hakkında neden. A <xref:Microsoft.CodeAnalysis.Compilation> bulmanıza olanak tanır **sembolleri** -türleri, ad alanları, üyeleri ve adları ve diğer ifadeler başvuran değişkenler gibi varlıklar. Adlar ve ifadeler ile ilişkilendirme işlemi **sembolleri** çağrılır **bağlama**.

Gibi <xref:Microsoft.CodeAnalysis.SyntaxTree?displayProperty=nameWithType>, <xref:Microsoft.CodeAnalysis.Compilation> soyut bir sınıf dile bağlı türevleri ile ilgilidir. Derleme örneğini oluştururken, üzerinde bir fabrika yöntemini çağırmanız gerekir <xref:Microsoft.CodeAnalysis.CSharp.CSharpCompilation?displayProperty=nameWithType> (veya <xref:Microsoft.CodeAnalysis.VisualBasic.VisualBasicCompilation?displayProperty=nameWithType>) sınıfı.

## <a name="querying-symbols"></a>Semboller sorgulama

Bu öğreticide, "Hello World" programı tekrar bakın. Bu kez, programın ne bu sembolleri temsil türlerini anlamak için sembolleri sorgulayın. Bir ad alanı içindeki türleri için sorgulama ve türe göre uygun olan yöntemler bulmayı öğrenin.

Bu örnek için tamamlanan kodu gördüğünüz [GitHub depomuzda](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/SemanticQuickStart).

> [!NOTE]
> Sözdizimi ağacı türleri devralma programı farklı konumlarda geçerli olan farklı bir sözdizimi öğeleri tanımlamak için kullanın. Genellikle bu API'leri kullanarak, atama özellikleri veya belirli türetilen türler için koleksiyon üyelerini anlamına gelir. Aşağıdaki örneklerde, atama ve atamaları açıkça yazılmış değişkenler kullanarak ayrı deyim olan. API dönüş türleri ve döndürülen nesnelerin çalışma zamanı türü görmek için kodu okuyabilirsiniz. Uygulamada, türü örtük olarak belirlenmiş değişkenlerin ve incelenmekte olan nesnelerin türünü tanımlamak için API adlara dayalı daha yaygındır.

Yeni C# oluşturma **tek başına kod analizi aracı** proje:

* Visual Studio'da **dosya** > **yeni** > **proje** yeni proje iletişim kutusu görüntülenecek.
* Altında **Visual C#** > **genişletilebilirlik**, seçin **tek başına kod analizi aracı**.
* Projenizi adlandırın "**SemanticQuickStart**" ve Tamam'a tıklayın.

Temel "Hello World!" analiz etmek için gideceğinizi daha önce gösterilen programı.
İçinde bir sabit olarak Hello World programı için metin ekleyin, `Program` sınıfı:

[!code-csharp[Declare the program test](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#1 "Declare a constant string for the program text to analyze")]

Ardından, kod metni için söz dizimi ağacı oluşturmak için aşağıdaki kodu ekleyin `programText` sabit.  Aşağıdaki satırı ekleyin, `Main` yöntemi:

[!code-csharp[Create the tree](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#2 "Create the syntax tree")]

Ardından, yapı bir <xref:Microsoft.CodeAnalysis.CSharp.CSharpCompilation> zaten oluşturduğunuz ağaç. "Hello World" örnek dayanan <xref:System.String> ve <xref:System.Console> türleri. Bu iki tür derlemenizdeki bildiren derlemesine başvuru gerekiyor. Aşağıdaki satırı ekleyin, `Main` yöntemi, söz dizimi ağacının uygun derlemesine başvuru dahil olmak üzere bir derleme oluşturmak için:

[!code-csharp[Create the compilation](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#3 "Create the compilation for the semantic model")]

<xref:Microsoft.CodeAnalysis.CSharp.CSharpCompilation.AddReferences%2A?displayProperty=nameWithType> Yöntemi derleme başvurularını ekler. <xref:Microsoft.CodeAnalysis.MetadataReference.CreateFromFile%2A?displayProperty=nameWithType> Yöntemi bir başvuru olarak bir derleme yükler.

## <a name="querying-the-semantic-model"></a>Anlam modeli sorgulama

Sonra bir <xref:Microsoft.CodeAnalysis.Compilation> bunları istemeniz bir <xref:Microsoft.CodeAnalysis.SemanticModel> herhangi <xref:Microsoft.CodeAnalysis.SyntaxTree> uygulamasında yer alan <xref:Microsoft.CodeAnalysis.Compilation>. Anlam modeli, normalde IntelliSense'de elde edebileceğiniz bilgi kaynağı olarak düşünebilirsiniz. A <xref:Microsoft.CodeAnalysis.SemanticModel> soruları "Adı bu konumda kapsamda nelerdir?", ister "hangi üyelerinin bu yöntemden erişilebilir?", "Bu metin bloğu içinde hangi değişkenleri kullanılır?" ve "Ne bu adı/ifadesi başvurmak?" Anlam modeli oluşturmak için bu deyimi ekleyin:

[!code-csharp[Create the semantic model](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#4 "Create the semantic model")]

## <a name="binding-a-name"></a>Bir ad bağlama

<xref:Microsoft.CodeAnalysis.Compilation> Oluşturur <xref:Microsoft.CodeAnalysis.SemanticModel> gelen <xref:Microsoft.CodeAnalysis.SyntaxTree>. Model oluşturduktan sonra ilk bulmak için sorgulayabilirsiniz `using` yönergesi için Sembol bilgilerini almanıza ve `System` ad alanı. Bu iki satırları ekleyin, `Main` anlam modeli oluşturma ve ilk simgesini almak için yöntem using deyimi:

[!code-csharp[Find the namespace symbol for the first using](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#5 "Find the namespace symbol for the first using")]

Yukarıdaki kod ilk adı bağlama gösterilmektedir `using` alınacak yönergesi bir <xref:Microsoft.CodeAnalysis.SymbolInfo?displayProperty=nameWithType> için `System` ad alanı. Yukarıdaki kod, ayrıca kullanmanızı gösterir **söz dizimi modeli** ; kod yapısını bulmak için kullandığınız **anlam modeli** anlamını anlamak için. **Söz dizimi modeli** bulur `System` kullanarak deyimi. **Anlam modeli** tanımlanan türleri hakkında tüm bilgiler `System` ad alanı.

Gelen <xref:Microsoft.CodeAnalysis.SymbolInfo> edinebilirsiniz nesne <xref:Microsoft.CodeAnalysis.ISymbol?displayProperty=nameWithType> kullanarak <xref:Microsoft.CodeAnalysis.SymbolInfo.Symbol?displayProperty=nameWithType> özelliği. Bu özellik, bu ifade için başvuruyor sembol döndürür. Bu özellik başvuran yoksa şeye (örneğin, sayısal değişmez değerler) ifadeler için olan `null`. Zaman <xref:Microsoft.CodeAnalysis.SymbolInfo.Symbol?displayProperty=nameWithType> null değil <xref:Microsoft.CodeAnalysis.ISymbol.Kind?displayProperty=nameWithType> simgenin türünü gösterir. Bu örnekte, <xref:Microsoft.CodeAnalysis.ISymbol.Kind?displayProperty=nameWithType> özelliği bir <xref:Microsoft.CodeAnalysis.SymbolKind.Namespace?displayProperty=nameWithType>. Aşağıdaki kodu ekleyin, `Main` yöntemi. Simgesini alır `System` tüm alt ad alanlarında bildirilen ad alanı ve görüntüler `System` ad alanı:

[!code-csharp[Display all the child namespaces](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#6 "Display all the child namespaces from this compilation")]

Programı çalıştırın ve aşağıdaki çıktıyı görmeniz gerekir:

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
> Çıktı bir alt ad alanı, her ad alanı içermeyen `System` ad alanı. Bu derlemede, yalnızca derlemenin başvuran mevcut olan her ad alanı görüntüler burada `System.String` bildirilir. Diğer derlemeler içinde bildirilen tüm ad alanları için bu derleme bilinmiyor

### <a name="binding-an-expression"></a>Bir ifade bağlama

Yukarıdaki kod, bir ad bağlayarak bir sembol Bul işlemi gösterilmektedir. Adı olmayan başka ifadelere bağlanabilir bir C# programı vardır. Bu özellik göstermek için şimdi basit dize sabit değeri için bağlama erişin.

"Hello World" programını içeren bir <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LiteralExpressionSyntax?displayProperty=nameWithType>, "Hello, World!" konsolda görüntülenen dize.

"Hello, World!" bulun tek bir dize programda değişmez değer bulma tarafından kullanılan dize. Daha sonra sözdizimi düğümü bulunan sonra anlam modeli Bu düğüm için tür bilgilerini alın. Aşağıdaki kodu ekleyin, `Main` yöntemi:

[!code-csharp[Find the namespace symbol for the only using](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#7 "Find the namespace symbol for the only using")]

<xref:Microsoft.CodeAnalysis.TypeInfo?displayProperty=nameWithType> Yapı içeren bir <xref:Microsoft.CodeAnalysis.TypeInfo.Type?displayProperty=nameWithType> değişmez değer türü hakkında anlam bilgilerine erişim sağlayan bir özellik. Bu örnekte, o `string` türü. Bu özellik yerel bir değişkene atar bir bildirimi ekleyin:

[!code-csharp[Find the semantic information about the string type](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#8 "Use the string literal to access the semantic information in the string type.")]

Bu öğreticiyi tamamlamak için tüm genel yöntemleri bildirilen üzerinde bir dizi oluşturur bir LINQ Sorgu oluşturalım `string` türü döndüren bir `string`. Bu sorgu karmaşık, bu nedenle şimdi bu yapı satır alır, tek bir sorgu yeniden yapılandırma. Bu sorgu için kaynak üzerinde bildirilen tüm üyelerle dizisidir `string` türü:

[!code-csharp[Access the sequence of members on the string type](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#9 "Access the sequence of members on the string type.")]

Bu kaynak dizisi özellikler ve alanları dahil olmak üzere tüm üyeleri içerir, böylece kullanarak filtre <xref:System.Collections.Immutable.ImmutableArray%601.OfType%2A?displayProperty=nameWithType> Bul öğeleri yönteme <xref:Microsoft.CodeAnalysis.IMethodSymbol?displayProperty=nameWithType> nesneler:

[!code-csharp[Filter the sequence to only methods](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#10 "Find the subset of the collection that is the methods.")]

Ardından, genel ve dönüş yöntemleri döndürülecek başka bir filtre Ekle bir `string`:

[!code-csharp[Filter on return type and accessibility](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#11 "Find only the public methods that return a string.")]

Name özelliği yalnızca ve yalnızca DISTINCT adları tüm aşırı yüklemeler kaldırarak seçin:

[!code-csharp[find the distinct names.](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#12 "Use the string literal to access the semantic information in the string type.")]

Ayrıca LINQ Sorgu söz dizimi kullanarak tam bir sorgu oluşturun ve sonra konsolda yöntem adları görüntüleyin:

[!code-csharp[build and display the results of this query.](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#13 "Build and display the results of the query.")]

Programı derleyin ve çalıştırın. Aşağıdaki çıktıyı görmeniz gerekir:

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

Bulmak ve bu programın bir parçası olan simgeler hakkında bilgi görüntülemek için anlamsal API kullandınız.
