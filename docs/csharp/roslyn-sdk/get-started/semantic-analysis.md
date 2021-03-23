---
title: Anlamsal analiz ile çalışmaya başlama
description: Bu öğreticide, .NET derleyici SDK 'sını kullanarak anlam analizi ile çalışmaya genel bakış sunulmaktadır.
ms.date: 02/06/2018
ms.custom: mvc
ms.openlocfilehash: 3119363822328c0e5fc67c2a2a4a917a7d37cfd2
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104872567"
---
# <a name="get-started-with-semantic-analysis"></a>Anlamsal analiz ile çalışmaya başlama

Bu öğreticide, sözdizimi API 'SI hakkında bilgi sahibi olduğunuz varsayılır. [Sözdizimi analizi ile çalışmaya başlama](syntax-analysis.md) makalesi, yeterli giriş sağlar.

Bu öğreticide, **sembol** ve **bağlama API 'lerini** keşfedebilirsiniz. Bu API 'Ler, bir programın _anlam anlamı_ hakkında bilgi sağlar. Bunlar, programınızda herhangi bir sembol tarafından temsil edilen türler hakkında soru sormaya ve yanıt uygulamanıza olanak tanır.

**.Net Compiler Platform SDK 'sını** yüklemeniz gerekir:

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

## <a name="understanding-compilations-and-symbols"></a>Derlemeleri ve sembolleri anlama

.NET derleyici SDK ile daha fazla çalışırken, sözdizimi API 'SI ve anlam API 'SI arasındaki farklılıklarla ilgili bilgi sahibi olursunuz. **Sözdizimi API 'si** , bir programın _yapısına_ bakabilmeniz için izin verir. Ancak, genellikle bir programın semantiği veya _anlamı_ hakkında daha zengin bilgi istemeniz gerekir. Gevşek bir kod dosyası veya Visual Basic veya C# kodu kod parçacığı, yalıtım halinde analiz edilebilir olsa da, "Bu değişkenin türü nedir" gibi sorular sormak için anlamlı değildir. Bir tür adının anlamı derleme başvurularına, ad alanı içeri aktarmalara veya diğer kod dosyalarına bağlı olabilir. Bu sorular, özellikle sınıfı olan **SEMANTIK API** kullanılarak yanıtlanır <xref:Microsoft.CodeAnalysis.Compilation?displayProperty=nameWithType> .

Bir örneği, <xref:Microsoft.CodeAnalysis.Compilation> derleyici tarafından görülen tek bir projeye benzer ve bir Visual Basic veya C# programını derlemek için gereken her şeyi temsil eder. **Derleme** , Derlenecek kaynak dosyalar kümesi, derleme başvuruları ve derleyici seçenekleri içerir. Bu bağlamdaki tüm diğer bilgileri kullanarak kodun anlamı hakkında neden olabilirsiniz. <xref:Microsoft.CodeAnalysis.Compilation>, Türler, ad alanları, Üyeler ve ad ve diğer ifadelerin başvurduğu değişkenler gibi **sembolleri** bulmanıza olanak tanır. Adları ve ifadeleri **simgelerle** Ilişkilendirme işlemine **bağlama** denir.

Benzer şekilde <xref:Microsoft.CodeAnalysis.SyntaxTree?displayProperty=nameWithType> , <xref:Microsoft.CodeAnalysis.Compilation> dile özgü türevlerle soyut bir sınıftır. Bir derleme örneği oluştururken, <xref:Microsoft.CodeAnalysis.CSharp.CSharpCompilation?displayProperty=nameWithType> (veya) sınıfında bir fabrika yöntemi çağırmanız gerekir <xref:Microsoft.CodeAnalysis.VisualBasic.VisualBasicCompilation?displayProperty=nameWithType> .

## <a name="querying-symbols"></a>Sembolleri sorgulama

Bu öğreticide, "Merhaba Dünya" programına tekrar göz atalım. Bu kez, bu sembollerin hangi türleri temsil ettiğini anlamak için programdaki sembolleri sorgulayın. Bir ad alanındaki türleri sorgular ve bir tür üzerinde kullanılabilir olan yöntemleri bulmayı öğrenin.

Bu örnek için tamamlanmış kodu [GitHub depomuza](https://github.com/dotnet/samples/tree/main/csharp/roslyn-sdk/SemanticQuickStart)bakabilirsiniz.

> [!NOTE]
> Sözdizimi ağacı türleri, programdaki farklı konumlarda geçerli olan farklı sözdizimi öğelerini anlatmak için devralmayı kullanır. Bu API 'Lerin kullanılması genellikle özellikleri veya koleksiyon üyelerini belirli türetilmiş türlere atama anlamına gelir. Aşağıdaki örneklerde atama ve yayınlar, açıkça belirlenmiş değişkenler kullanılarak ayrı deyimlerdir. API 'nin dönüş türlerini ve döndürülen nesnelerin çalışma zamanı türünü görmek için kodu okuyabilirsiniz. Uygulamada, örtük olarak yazılan değişkenleri kullanmak daha yaygındır ve incelenen nesne türlerini belirtmek için API adlarını kullanır.

Yeni bir C# **tek başına kod analizi araç** projesi oluşturun:

* Visual Studio 'da   >    >  Yeni proje iletişim kutusunu göstermek için dosya yeni **Proje** ' yi seçin.
* **Visual C#**  >  **genişletilebilirliği** altında **tek başına Kod Analizi Aracı**' nı seçin.
* Projenizi "**Semantıhızlı başlangıç**" olarak adlandırın ve Tamam ' a tıklayın.

Temel "Merhaba Dünya!" öğesini çözümleyeceğiz Program daha önce gösteriliyor.
Merhaba Dünya programın metnini sınıfınıza bir sabit olarak ekleyin `Program` :

[!code-csharp[Declare the program test](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#1 "Declare a constant string for the program text to analyze")]

Sonra, sabit içindeki kod metni için sözdizimi ağacını derlemek üzere aşağıdaki kodu ekleyin `programText` .  Aşağıdaki satırı `Main` yöntemine ekleyin:

[!code-csharp[Create the tree](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#2 "Create the syntax tree")]

Ardından, <xref:Microsoft.CodeAnalysis.CSharp.CSharpCompilation> zaten oluşturduğunuz ağaçtan bir oluşturun. "Merhaba Dünya" örneği ve türlerini temel alır <xref:System.String> <xref:System.Console> . Derlemenizin bu iki türü bildiren derlemeye başvurmanız gerekir. `Main`Uygun derlemeye başvuru dahil olmak üzere, sözdizimi ağacınızı oluşturmak için aşağıdaki satırı yöntemine ekleyin:

[!code-csharp[Create the compilation](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#3 "Create the compilation for the semantic model")]

<xref:Microsoft.CodeAnalysis.CSharp.CSharpCompilation.AddReferences%2A?displayProperty=nameWithType>Yöntemi, derlemeye başvurular ekler. <xref:Microsoft.CodeAnalysis.MetadataReference.CreateFromFile%2A?displayProperty=nameWithType>Yöntemi bir derlemeyi başvuru olarak yükler.

## <a name="querying-the-semantic-model"></a>Anlam modelini sorgulama

Bir kez oluşturduktan sonra, <xref:Microsoft.CodeAnalysis.Compilation> bunun için bir için bunu isteyebilirsiniz <xref:Microsoft.CodeAnalysis.SemanticModel> <xref:Microsoft.CodeAnalysis.SyntaxTree> <xref:Microsoft.CodeAnalysis.Compilation> . Anlamsal modeli, normalde IntelliSense 'ten alacağınız tüm bilgilerin kaynağı olarak düşünebilirsiniz. Bir <xref:Microsoft.CodeAnalysis.SemanticModel> "Bu konumda kapsam içinde olan adlar nedir?", "Bu metin bloğunda hangi değişkenler kullanılır?" ve "Bu ad/ifade ne ifade edilir?" gibi sorulara yanıt verebilir Anlam modeli oluşturmak için bu ifadeyi ekleyin:

[!code-csharp[Create the semantic model](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#4 "Create the semantic model")]

## <a name="binding-a-name"></a>Ad bağlama

, <xref:Microsoft.CodeAnalysis.Compilation> Öğesinden öğesini oluşturur  <xref:Microsoft.CodeAnalysis.SemanticModel> <xref:Microsoft.CodeAnalysis.SyntaxTree> . Modeli oluşturduktan sonra, ilk yönergeyi bulmak için sorgulama yapabilir `using` ve ad alanı için sembol bilgilerini alabilirsiniz `System` . `Main`Anlam modeli oluşturmak ve ilk using ifadesinin simgesini almak için bu iki satırı yönteminizin içine ekleyin:

[!code-csharp[Find the namespace symbol for the first using](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#5 "Find the namespace symbol for the first using")]

Yukarıdaki kodda ad `using` alanı için ilk yönergedeki adın nasıl bağlanacağı gösterilmektedir <xref:Microsoft.CodeAnalysis.SymbolInfo?displayProperty=nameWithType> `System` . Yukarıdaki kod ayrıca kodun yapısını bulmak için **sözdizimi modelini** kullanmanızı da gösterir; **anlam modelini** , anlamını anlamak için kullanabilirsiniz. **Sözdizimi modeli** using deyimindeki dizeyi bulur `System` . **Anlam modeli** , ad alanında tanımlanan türlerle ilgili tüm bilgileri içerir `System` .

<xref:Microsoft.CodeAnalysis.SymbolInfo>Nesnesinden <xref:Microsoft.CodeAnalysis.ISymbol?displayProperty=nameWithType> özelliğini kullanarak elde edebilirsiniz <xref:Microsoft.CodeAnalysis.SymbolInfo.Symbol?displayProperty=nameWithType> . Bu özellik, bu ifadenin başvurduğu simgeyi döndürür. Her şeye başvurmaz (sayısal değişmez değerler gibi), bu özellik olur `null` . Null olmadığında, <xref:Microsoft.CodeAnalysis.SymbolInfo.Symbol?displayProperty=nameWithType> <xref:Microsoft.CodeAnalysis.ISymbol.Kind?displayProperty=nameWithType> simgenin türünü gösterir. Bu örnekte, <xref:Microsoft.CodeAnalysis.ISymbol.Kind?displayProperty=nameWithType> özelliği bir <xref:Microsoft.CodeAnalysis.SymbolKind.Namespace?displayProperty=nameWithType> . Yöntemine aşağıdaki kodu ekleyin `Main` . Ad alanı için sembolü alır `System` ve ad alanında belirtilen tüm alt ad alanlarını görüntüler `System` :

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
> Çıktı, ad alanının alt ad alanı olan her ad alanını içermez `System` . Bu derlemede bulunan her ad alanını görüntüler, bu derleme yalnızca bildirildiği derlemeye başvurur `System.String` . Diğer derlemelerde belirtilen ad alanları bu derleme tarafından tanınmıyor

### <a name="binding-an-expression"></a>Bir ifadeyi bağlama

Yukarıdaki kod, bir ada bağlama yoluyla nasıl bir sembol bulunacağını gösterir. Bir C# programında, isimsiz olmayan bağlanabilen başka ifadeler de vardır. Bu özelliği göstermek için bağlamaya basit bir dize değişmez değerine erişelim.

"Merhaba Dünya" programı <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LiteralExpressionSyntax?displayProperty=nameWithType> , "Hello, World!" öğesini içerir konsola görüntülenecek dize.

"Hello, World!" öğesini bulursunuz Programda tek dize sabit değerini bularak dize. Ardından, söz dizimi düğümünü bulduktan sonra söz konusu düğümün tür bilgilerini anlamsal modelden alın. Aşağıdaki kodu yönteminizin içine ekleyin `Main` :

[!code-csharp[Find the namespace symbol for the only using](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#7 "Find the namespace symbol for the only using")]

<xref:Microsoft.CodeAnalysis.TypeInfo?displayProperty=nameWithType>Struct, <xref:Microsoft.CodeAnalysis.TypeInfo.Type?displayProperty=nameWithType> değişmez değer türü hakkında anlam bilgisine erişim sağlayan bir özelliği içerir. Bu örnekte, `string` türü budur. Bu özelliği yerel bir değişkene atayan bir bildirim ekleyin:

[!code-csharp[Find the semantic information about the string type](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#8 "Use the string literal to access the semantic information in the string type.")]

Bu öğreticiyi tamamlaması için, döndüren türünde belirtilen tüm ortak yöntemlerin bir dizisini oluşturan bir LINQ sorgusu oluşturalım `string` `string` . Bu sorgu karmaşıktır, bu yüzden satırı satıra göre oluşturalım ve sonra tek bir sorgu olarak yeniden yapılandırma. Bu sorgunun kaynağı, türde belirtilen tüm üyelerin sırasıdır `string` :

[!code-csharp[Access the sequence of members on the string type](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#9 "Access the sequence of members on the string type.")]

Bu kaynak sırası Özellikler ve alanlar da dahil olmak üzere tüm üyeleri içerir, bu nedenle <xref:System.Collections.Immutable.ImmutableArray%601.OfType%2A?displayProperty=nameWithType> nesne olan öğeleri bulmak için yöntemini kullanarak filtreleyin <xref:Microsoft.CodeAnalysis.IMethodSymbol?displayProperty=nameWithType> :

[!code-csharp[Filter the sequence to only methods](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#10 "Find the subset of the collection that is the methods.")]

Sonra, yalnızca ortak olan yöntemleri döndürmek için başka bir filtre ekleyin ve şunu döndürür `string` :

[!code-csharp[Filter on return type and accessibility](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#11 "Find only the public methods that return a string.")]

Yalnızca ad özelliğini ve yalnızca herhangi bir aşırı yüklemeyi kaldırarak farklı adları seçin:

[!code-csharp[find the distinct names.](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#12 "Use the string literal to access the semantic information in the string type.")]

Ayrıca, LINQ sorgu söz dizimini kullanarak tam sorgu oluşturabilir ve sonra tüm yöntem adlarını konsolda görüntüleyebilirsiniz:

[!code-csharp[build and display the results of this query.](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#13 "Build and display the results of the query.")]

Programı derleyin ve çalıştırın. Aşağıdaki çıkışı görmeniz gerekir:

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

Bu programın parçası olan semboller hakkındaki bilgileri bulmak ve göstermek için anlamsal API 'YI kullandınız.
