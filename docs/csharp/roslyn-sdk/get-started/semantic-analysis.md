---
title: Anlamsal analize başlayın
description: Bu öğretici, .NET Derleyici SDK'yı kullanarak anlamsal analizlerle çalışmaya genel bir bakış sağlar.
ms.date: 02/06/2018
ms.custom: mvc
ms.openlocfilehash: a6dcaeeb86acb5c0e1602f01dc5952ffd9d5e3f5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240518"
---
# <a name="get-started-with-semantic-analysis"></a>Anlamsal analize başlayın

Bu öğretici, Sözdizimi API'sini bildiğinizi varsayar. [Sözdizimi çözümleme](syntax-analysis.md) makalesi ile başlamak yeterli giriş sağlar.

Bu öğreticide, **Sembol** ve **Bağlama API'lerini**keşfe Bu API'ler bir programın _anlamsal anlamı_ hakkında bilgi sağlar. Bunlar, programınızdaki herhangi bir sembolle temsil edilen türler hakkında soru sormanızı ve yanıtlamanızı sağlar.

**.NET Derleyici Platformu SDK'yı**yüklemeniz gerekir:

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

## <a name="understanding-compilations-and-symbols"></a>Derlemeleri ve Sembolleri Anlama

.NET Derleyici SDK ile daha fazla çalışırken, Sözdizimi API'si ile Anlamsal API arasındaki ayrımlara aşina olursunuz. **Sözdizimi** API'si, bir programın _yapısına_ bakmanızı sağlar. Ancak, genellikle semantik veya bir programın _anlamı_ hakkında daha zengin bilgi istiyorum. Visual Basic veya C# kodunun gevşek bir kod dosyası veya parçacığı tek tekkenolarak çözümlenebilirken, boşlukta "bu değişkenin türü nedir" gibi sorular sormak anlamlı değildir. Bir tür adının anlamı derleme başvurularına, ad alanı aktarımına veya diğer kod dosyalarına bağlı olabilir. Bu sorular **Anlamsal API**kullanılarak yanıtlanır <xref:Microsoft.CodeAnalysis.Compilation?displayProperty=nameWithType> , özellikle sınıf.

Bir örneği <xref:Microsoft.CodeAnalysis.Compilation> derleyici tarafından görüldüğü gibi tek bir projeye benzer ve Visual Basic veya C# programını derlemek için gereken her şeyi temsil eder. **Derleme** derlenecek kaynak dosyaları kümesini, derleme başvurularını ve derleyici seçeneklerini içerir. Bu bağlamdaki diğer tüm bilgileri kullanarak kodun anlamı hakkında neden olabilirsiniz. <xref:Microsoft.CodeAnalysis.Compilation> A, türtürleri, ad alanları, üyeler ve adların ve diğer ifadelerin atıfta bulunduğu değişkenler gibi varlıklar gibi **Sembolleri** bulmanızı sağlar. İsimleri ve ifadeleri **Sembollerle** ilişkilendirme **işlemine Bağlama**denir.

Gibi <xref:Microsoft.CodeAnalysis.SyntaxTree?displayProperty=nameWithType> <xref:Microsoft.CodeAnalysis.Compilation> , dil özel türevleri ile soyut bir sınıftır. Derleme bir örnek oluştururken, <xref:Microsoft.CodeAnalysis.CSharp.CSharpCompilation?displayProperty=nameWithType> (veya) <xref:Microsoft.CodeAnalysis.VisualBasic.VisualBasicCompilation?displayProperty=nameWithType>sınıfında bir fabrika yöntemi çağırmak gerekir.

## <a name="querying-symbols"></a>Sembolleri sorgulama

Bu eğitimde, "Hello World" programına tekrar bakabilirsiniz. Bu kez, bu sembollerin hangi türlerde temsil olduğunu anlamak için programdaki sembolleri sorgularsınız. Ad alanındaki türleri sorgular sınız ve bir türde kullanılabilir yöntemleri bulmayı öğrenirsiniz.

Bu örneğin bitmiş kodunu [GitHub depomuzda](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/SemanticQuickStart)görebilirsiniz.

> [!NOTE]
> Sözdizimi Ağacı türleri, programdaki farklı konumlarda geçerli olan farklı sözdizimi öğelerini açıklamak için kalıtım kullanır. Bu API'lerin kullanılması genellikle özellikleri veya koleksiyon üyelerini belirli türemiş türlere dökümü anlamına gelir. Aşağıdaki örneklerde, atama ve dökümler, açıkça yazılan değişkenler kullanılarak ayrı ifadelerdir. API'nin geri dönüş türlerini ve döndürülen nesnelerin çalışma zamanı türünü görmek için kodu okuyabilirsiniz. Uygulamada, örtülü olarak yazılan değişkenleri kullanmak ve incelenmekte olan nesnelerin türünü açıklamak için API adlarına güvenmek daha yaygındır.

Yeni bir C# **Tek Başına Kod Analizi Aracı** projesi oluşturun:

* Visual Studio'da, Yeni Proje iletişim kutusunu görüntülemek için **Dosya** > **Yeni** > **Projesi'ni** seçin.
* **Visual C#** > **Genişletilebilirlik** **altında, Tek Başına Kod Analiz Aracı'nı**seçin.
* Projenizi "**SemanticQuickStart**" adını ve Tamam'ı tıklatın.

Temel "Merhaba Dünya"yı analiz edeceksin. program daha önce gösterilmiştir.
Merhaba Dünya programı için metni sınıfınızda `Program` sabit olarak ekleyin:

[!code-csharp[Declare the program test](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#1 "Declare a constant string for the program text to analyze")]

Ardından, `programText` sabitteki kod metni için sözdizimi ağacı oluşturmak için aşağıdaki kodu ekleyin.  Yönteminize `Main` aşağıdaki satırı ekleyin:

[!code-csharp[Create the tree](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#2 "Create the syntax tree")]

Ardından, zaten <xref:Microsoft.CodeAnalysis.CSharp.CSharpCompilation> oluşturduğunuz ağaçtan bir tane oluşturun. "Hello World" örneği, türlerine <xref:System.Console> ve türlerine <xref:System.String> dayanır. Derlemenizde bu iki türü bildiren derlemeye başvurmanız gerekir. Sözdizimi ağacınızın `Main` bir derlemesini oluşturmak için yönteminize, uygun derlemeye başvuru da dahil olmak üzere aşağıdaki satırı ekleyin:

[!code-csharp[Create the compilation](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#3 "Create the compilation for the semantic model")]

Yöntem <xref:Microsoft.CodeAnalysis.CSharp.CSharpCompilation.AddReferences%2A?displayProperty=nameWithType> derlemeye başvurular ekler. Yöntem, <xref:Microsoft.CodeAnalysis.MetadataReference.CreateFromFile%2A?displayProperty=nameWithType> bir derlemeyi başvuru olarak yükler.

## <a name="querying-the-semantic-model"></a>Anlamsal modeli sorgulama

Bir kez <xref:Microsoft.CodeAnalysis.Compilation> herhangi bir <xref:Microsoft.CodeAnalysis.SemanticModel> <xref:Microsoft.CodeAnalysis.SyntaxTree> içinde bulunan <xref:Microsoft.CodeAnalysis.Compilation>için bir sorabilirsiniz. Semantik modeli normalde intellisense'den alacağınız tüm bilgilerin kaynağı olarak düşünebilirsiniz. A, <xref:Microsoft.CodeAnalysis.SemanticModel> "Bu konumda kapsamda hangi adlar var?", "Bu yöntemden hangi üyelere erişilebilir?", "Bu metin bloğunda hangi değişkenler kullanılır?" ve "Bu ad/ifade ne anlama geliyor?" gibi soruları yanıtlayabilir. Anlamsal modeli oluşturmak için bu deyimi ekleyin:

[!code-csharp[Create the semantic model](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#4 "Create the semantic model")]

## <a name="binding-a-name"></a>Bir adı bağlama

<xref:Microsoft.CodeAnalysis.SemanticModel> Gelen <xref:Microsoft.CodeAnalysis.Compilation> oluşturur <xref:Microsoft.CodeAnalysis.SyntaxTree>. Modeli oluşturduktan sonra, ilk `using` yönergeleri bulmak için sorgulayabilir ve `System` ad alanı için sembol bilgilerini alabilirsiniz. Anlamsal modeli oluşturmak `Main` ve ilk kullanılan ifadenin simgesini almak için yönteminize bu iki satırı ekleyin:

[!code-csharp[Find the namespace symbol for the first using](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#5 "Find the namespace symbol for the first using")]

Önceki kod, `using` <xref:Microsoft.CodeAnalysis.SymbolInfo?displayProperty=nameWithType> `System` ad alanı için a almak için ilk yönergede adın nasıl bağlanılsüreceğini gösterir. Önceki kod, kodun yapısını bulmak için **sözdizimi modelini** kullandığınızı da gösterir; anlamını anlamak için **anlamsal modeli** kullanırsınız. **Sözdizimi modeli,** `System` string'i kullanarak ifadede bulur. `System` **Anlamsal model,** ad alanında tanımlanan türler hakkında tüm bilgilere sahiptir.

Nesneden <xref:Microsoft.CodeAnalysis.SymbolInfo> <xref:Microsoft.CodeAnalysis.ISymbol?displayProperty=nameWithType> <xref:Microsoft.CodeAnalysis.SymbolInfo.Symbol?displayProperty=nameWithType> özelliği kullanarak elde edebilirsiniz. Bu özellik, bu ifadenin ifade bahsettiği sembolü döndürür. Hiçbir şeye atıfta bulunmadan ifadeler için (sayısal literals gibi) `null`bu özellik . Null <xref:Microsoft.CodeAnalysis.SymbolInfo.Symbol?displayProperty=nameWithType> olmadığında, sembolün <xref:Microsoft.CodeAnalysis.ISymbol.Kind?displayProperty=nameWithType> türünü gösterir. Bu örnekte, <xref:Microsoft.CodeAnalysis.ISymbol.Kind?displayProperty=nameWithType> özellik <xref:Microsoft.CodeAnalysis.SymbolKind.Namespace?displayProperty=nameWithType>bir . Yönteminize `Main` aşağıdaki kodu ekleyin. Ad alanı nın simgesini `System` alır ve `System` ad alanında bildirilen tüm alt ad alanlarını görüntüler:

[!code-csharp[Display all the child namespaces](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#6 "Display all the child namespaces from this compilation")]

Programı çalıştırın ve aşağıdaki çıktıyı görmeniz gerekir:

```output
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
> Çıktı, ad alanının `System` alt ad alanı olan her ad alanını içermez. Yalnızca bildirilen derlemeye `System.String` başvuran bu derlemede bulunan her ad alanını görüntüler. Diğer derlemelerde bildirilen ad alanları bu derlemede bilinmemektedir

### <a name="binding-an-expression"></a>İfade bağlama

Önceki kod, bir ada bağlanarak bir sembolün nasıl bulunup bulunulacağıdır. C# programında ad olmayan başka ifadeler de vardır. Bu özelliği göstermek için, basit bir dize edebi bağlama erişelim.

"Hello World" programı <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LiteralExpressionSyntax?displayProperty=nameWithType>"Merhaba, Dünya!" konsola görüntülenen dize.

"Merhaba, Dünya!" programdaki tek dize harfini bularak dize. Ardından, sözdizimi düğümlerini tespit ettikten sonra, bu düğümün yazı bilgilerini anlamsal modelden alın. Yönteminize `Main` aşağıdaki kodu ekleyin:

[!code-csharp[Find the namespace symbol for the only using](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#7 "Find the namespace symbol for the only using")]

Yapı, <xref:Microsoft.CodeAnalysis.TypeInfo?displayProperty=nameWithType> edebi yapının türü hakkında anlamsal bilgilere erişim sağlayan bir <xref:Microsoft.CodeAnalysis.TypeInfo.Type?displayProperty=nameWithType> özellik içerir. Bu örnekte, `string` bu tür. Bu özelliği yerel bir değişkene atayan bir bildirim ekleyin:

[!code-csharp[Find the semantic information about the string type](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#8 "Use the string literal to access the semantic information in the string type.")]

Bu öğreticiyi bitirmek için, `string` bir `string`. Bu sorgu karmaşıklaşır, bu nedenle satır satır oluşturalım, sonra tek bir sorgu olarak yeniden oluşturalım. Bu sorgunun kaynağı, `string` türde bildirilen tüm üyelerin sırasıdır:

[!code-csharp[Access the sequence of members on the string type](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#9 "Access the sequence of members on the string type.")]

Bu kaynak sırası özellikleri ve alanları da dahil olmak <xref:System.Collections.Immutable.ImmutableArray%601.OfType%2A?displayProperty=nameWithType> üzere tüm üyeleri <xref:Microsoft.CodeAnalysis.IMethodSymbol?displayProperty=nameWithType> içerir, bu nedenle nesne öğeleri bulmak için yöntemi kullanarak filtre:

[!code-csharp[Filter the sequence to only methods](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#10 "Find the subset of the collection that is the methods.")]

Ardından, yalnızca herkese açık olan yöntemleri döndürmek için `string`başka bir filtre ekleyin ve bir:

[!code-csharp[Filter on return type and accessibility](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#11 "Find only the public methods that return a string.")]

Yalnızca ad özelliğini ve yalnızca farklı adları aşırı yüklemeleri kaldırarak seçin:

[!code-csharp[find the distinct names.](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#12 "Use the string literal to access the semantic information in the string type.")]

Ayrıca, LINQ sorgu sözdizimini kullanarak tam sorguyu oluşturabilir ve konsoldaki tüm yöntem adlarını görüntüleyebilirsiniz:

[!code-csharp[build and display the results of this query.](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#13 "Build and display the results of the query.")]

Programı derleyin ve çalıştırın. Aşağıdaki çıktıyı görmeniz gerekir:

```output
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

Bu programın bir parçası olan semboller hakkında bilgi bulmak ve görüntülemek için Anlamsal API'yi kullandınız.
