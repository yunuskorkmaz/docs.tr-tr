---
title: Anlamsal analiz ile çalışmaya başlama
description: Bu öğreticide, .NET derleyici SDK 'sını kullanarak anlam analizi ile çalışmaya genel bakış sunulmaktadır.
ms.date: 02/06/2018
ms.custom: mvc
ms.openlocfilehash: 80a814054ab95a5b6585289e8580a725b18ca44e
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252944"
---
# <a name="get-started-with-semantic-analysis"></a>Anlamsal analiz ile çalışmaya başlama

Bu öğreticide, sözdizimi API 'SI hakkında bilgi sahibi olduğunuz varsayılır. [Sözdizimi analizi ile çalışmaya başlama](syntax-analysis.md) makalesi, yeterli giriş sağlar.

Bu öğreticide, **sembol** ve **bağlama API 'lerini**keşfedebilirsiniz. Bu API 'Ler, bir programın _anlam anlamı_ hakkında bilgi sağlar. Bunlar, programınızda herhangi bir sembol tarafından temsil edilen türler hakkında soru sormaya ve yanıt uygulamanıza olanak tanır.

**.Net Compiler Platform SDK 'sını**yüklemeniz gerekir:

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

## <a name="understanding-compilations-and-symbols"></a>Derlemeleri ve sembolleri anlama

.NET derleyici SDK ile daha fazla çalışırken, sözdizimi API 'SI ve anlam API 'SI arasındaki farklılıklarla ilgili bilgi sahibi olursunuz. **Sözdizimi API 'si** , bir programın _yapısına_ bakabilmeniz için izin verir. Ancak, genellikle bir programın semantiği veya _anlamı_ hakkında daha zengin bilgi istemeniz gerekir. Bir seyrek kod dosyası ya da VB veya C# kod parçacığı, yalıtım halinde analiz edilebilir olsa da, "Bu değişkenin türü nedir" gibi sorular sormak için anlamlı değildir. Bir tür adının anlamı derleme başvurularına, ad alanı içeri aktarmalara veya diğer kod dosyalarına bağlı olabilir. Bu sorular, özellikle <xref:Microsoft.CodeAnalysis.Compilation?displayProperty=nameWithType> sınıfı olan **semantik API**kullanılarak yanıtlanır.

Bir örneği <xref:Microsoft.CodeAnalysis.Compilation> , derleyici tarafından görülen tek bir projeye benzerdir ve bir Visual Basic veya C# program derlemek için gereken her şeyi temsil eder. **Derleme** , Derlenecek kaynak dosyalar kümesi, derleme başvuruları ve derleyici seçenekleri içerir. Bu bağlamdaki tüm diğer bilgileri kullanarak kodun anlamı hakkında neden olabilirsiniz. , Türler, ad alanları, Üyeler ve ad ve diğer ifadelerin başvurduğu değişkenler gibi **sembolleri** bulmanıza olanaktanır.<xref:Microsoft.CodeAnalysis.Compilation> Adları ve ifadeleri **simgelerle** Ilişkilendirme işlemine **bağlama**denir.

Benzer <xref:Microsoft.CodeAnalysis.SyntaxTree?displayProperty=nameWithType>şekilde <xref:Microsoft.CodeAnalysis.Compilation> , dile özgü türevlerle soyut bir sınıftır. Bir derleme örneği oluştururken, <xref:Microsoft.CodeAnalysis.CSharp.CSharpCompilation?displayProperty=nameWithType> (veya <xref:Microsoft.CodeAnalysis.VisualBasic.VisualBasicCompilation?displayProperty=nameWithType>) sınıfında bir fabrika yöntemi çağırmanız gerekir.

## <a name="querying-symbols"></a>Sembolleri sorgulama

Bu öğreticide, "Merhaba Dünya" programına tekrar göz atalım. Bu kez, bu sembollerin hangi türleri temsil ettiğini anlamak için programdaki sembolleri sorgulayın. Bir ad alanındaki türleri sorgular ve bir tür üzerinde kullanılabilir olan yöntemleri bulmayı öğrenin.

Bu örnek için tamamlanmış kodu [GitHub depomuza](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/SemanticQuickStart)bakabilirsiniz.

> [!NOTE]
> Sözdizimi ağacı türleri, programdaki farklı konumlarda geçerli olan farklı sözdizimi öğelerini anlatmak için devralmayı kullanır. Bu API 'Lerin kullanılması genellikle özellikleri veya koleksiyon üyelerini belirli türetilmiş türlere atama anlamına gelir. Aşağıdaki örneklerde atama ve yayınlar, açıkça belirlenmiş değişkenler kullanılarak ayrı deyimlerdir. API 'nin dönüş türlerini ve döndürülen nesnelerin çalışma zamanı türünü görmek için kodu okuyabilirsiniz. Uygulamada, örtük olarak yazılan değişkenleri kullanmak daha yaygındır ve incelenen nesne türlerini belirtmek için API adlarını kullanır.

Yeni C# bir **tek başına kod analizi araç** projesi oluşturun:

* Visual Studio 'da yeni proje iletişim kutusunu göstermek için **Dosya** > **Yeni** > **Proje** ' yi seçin.
* **Görsel C#** genişletilebilirlik altında tek başına Kod Analizi Aracı ' nı seçin.  > 
* Projenizi "**Semantıhızlı başlangıç**" olarak adlandırın ve Tamam ' a tıklayın.

Temel "Merhaba Dünya!" öğesini çözümleyeceğiz Program daha önce gösteriliyor.
Merhaba Dünya programın metnini sınıfınıza `Program` bir sabit olarak ekleyin:

[!code-csharp[Declare the program test](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#1 "Declare a constant string for the program text to analyze")]

Sonra, `programText` sabit içindeki kod metni için sözdizimi ağacını derlemek üzere aşağıdaki kodu ekleyin.  Aşağıdaki satırı `Main` yöntemine ekleyin:

[!code-csharp[Create the tree](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#2 "Create the syntax tree")]

Ardından, zaten oluşturduğunuz <xref:Microsoft.CodeAnalysis.CSharp.CSharpCompilation> ağaçtan bir oluşturun. "Merhaba Dünya" örneği <xref:System.String> ve <xref:System.Console> türlerini temel alır. Derlemenizin bu iki türü bildiren derlemeye başvurmanız gerekir. Uygun derlemeye başvuru dahil olmak üzere `Main` , sözdizimi ağacınızı oluşturmak için aşağıdaki satırı yöntemine ekleyin:

[!code-csharp[Create the compilation](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#3 "Create the compilation for the semantic model")]

<xref:Microsoft.CodeAnalysis.CSharp.CSharpCompilation.AddReferences%2A?displayProperty=nameWithType> Yöntemi, derlemeye başvurular ekler. <xref:Microsoft.CodeAnalysis.MetadataReference.CreateFromFile%2A?displayProperty=nameWithType> Yöntemi bir derlemeyi başvuru olarak yükler.

## <a name="querying-the-semantic-model"></a>Anlam modelini sorgulama

Bir <xref:Microsoft.CodeAnalysis.Compilation> kez oluşturduktan sonra, bunun için bir <xref:Microsoft.CodeAnalysis.SemanticModel> <xref:Microsoft.CodeAnalysis.SyntaxTree> <xref:Microsoft.CodeAnalysis.Compilation>için bunu isteyebilirsiniz. Anlamsal modeli, normalde IntelliSense 'ten alacağınız tüm bilgilerin kaynağı olarak düşünebilirsiniz. Bir <xref:Microsoft.CodeAnalysis.SemanticModel> "Bu konumda kapsam içinde olan adlar nedir?", "Bu metin bloğunda hangi değişkenler kullanılır?" ve "Bu ad/ifade ne ifade edilir?" gibi sorulara yanıt verebilir Anlam modeli oluşturmak için bu ifadeyi ekleyin:

[!code-csharp[Create the semantic model](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#4 "Create the semantic model")]

## <a name="binding-a-name"></a>Ad bağlama

<xref:Microsoft.CodeAnalysis.SemanticModel> , Öğesinden <xref:Microsoft.CodeAnalysis.Compilation> öğesini oluşturur .<xref:Microsoft.CodeAnalysis.SyntaxTree> Modeli oluşturduktan sonra, ilk `using` yönergeyi bulmak için sorgulama yapabilir ve `System` ad alanı için sembol bilgilerini alabilirsiniz. Anlam modeli oluşturmak ve ilk using `Main` ifadesinin simgesini almak için bu iki satırı yönteminizin içine ekleyin:

[!code-csharp[Find the namespace symbol for the first using](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#5 "Find the namespace symbol for the first using")]

Yukarıdaki kodda ad `using` `System` alanı <xref:Microsoft.CodeAnalysis.SymbolInfo?displayProperty=nameWithType> için ilk yönergedeki adın nasıl bağlanacağı gösterilmektedir. Yukarıdaki kod ayrıca kodun yapısını bulmak için **sözdizimi modelini** kullanmanızı da gösterir; **anlam modelini** , anlamını anlamak için kullanabilirsiniz. **Sözdizimi modeli** using deyimindeki dizeyi `System` bulur. **Anlam modeli** , `System` ad alanında tanımlanan türlerle ilgili tüm bilgileri içerir.

Nesnesinden özelliğini <xref:Microsoft.CodeAnalysis.ISymbol?displayProperty=nameWithType> kullanarak elde edebilirsiniz. <xref:Microsoft.CodeAnalysis.SymbolInfo> <xref:Microsoft.CodeAnalysis.SymbolInfo.Symbol?displayProperty=nameWithType> Bu özellik, bu ifadenin başvurduğu simgeyi döndürür. Her şeye başvurmaz (sayısal değişmez değerler gibi), bu özellik olur `null`. Nullolmadığında,simgenintürünügösterir.<xref:Microsoft.CodeAnalysis.SymbolInfo.Symbol?displayProperty=nameWithType> <xref:Microsoft.CodeAnalysis.ISymbol.Kind?displayProperty=nameWithType> Bu örnekte, <xref:Microsoft.CodeAnalysis.ISymbol.Kind?displayProperty=nameWithType> özelliği bir <xref:Microsoft.CodeAnalysis.SymbolKind.Namespace?displayProperty=nameWithType>. `Main` Yöntemine aşağıdaki kodu ekleyin. `System` Ad alanı için sembolü alır ve `System` ad alanında belirtilen tüm alt ad alanlarını görüntüler:

[!code-csharp[Display all the child namespaces](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#6 "Display all the child namespaces from this compilation")]

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
> Çıktı, `System` ad alanının alt ad alanı olan her ad alanını içermez. Bu derlemede bulunan her ad alanını görüntüler, bu derleme yalnızca bildirildiği derlemeye `System.String` başvurur. Diğer derlemelerde belirtilen ad alanları bu derleme tarafından tanınmıyor

### <a name="binding-an-expression"></a>Bir ifadeyi bağlama

Yukarıdaki kod, bir ada bağlama yoluyla nasıl bir sembol bulunacağını gösterir. Bir C# programda adı olmayan bağlanabilen başka ifadeler de vardır. Bu özelliği göstermek için bağlamaya basit bir dize değişmez değerine erişelim.

"Merhaba Dünya" programı <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LiteralExpressionSyntax?displayProperty=nameWithType>, "Hello, World!" öğesini içerir konsola görüntülenecek dize.

"Hello, World!" öğesini bulursunuz Programda tek dize sabit değerini bularak dize. Ardından, söz dizimi düğümünü bulduktan sonra söz konusu düğümün tür bilgilerini anlamsal modelden alın. Aşağıdaki kodu `Main` yönteminizin içine ekleyin:

[!code-csharp[Find the namespace symbol for the only using](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#7 "Find the namespace symbol for the only using")]

Struct, değişmez değer <xref:Microsoft.CodeAnalysis.TypeInfo.Type?displayProperty=nameWithType> türü hakkında anlam bilgisine erişim sağlayan bir özelliği içerir. <xref:Microsoft.CodeAnalysis.TypeInfo?displayProperty=nameWithType> Bu örnekte, `string` türü budur. Bu özelliği yerel bir değişkene atayan bir bildirim ekleyin:

[!code-csharp[Find the semantic information about the string type](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#8 "Use the string literal to access the semantic information in the string type.")]

Bu öğreticiyi tamamlaması için, `string` `string`döndüren türünde belirtilen tüm ortak yöntemlerin bir dizisini oluşturan bir LINQ sorgusu oluşturalım. Bu sorgu karmaşıktır, bu yüzden satırı satıra göre oluşturalım ve sonra tek bir sorgu olarak yeniden yapılandırma. Bu sorgunun kaynağı, `string` türde belirtilen tüm üyelerin sırasıdır:

[!code-csharp[Access the sequence of members on the string type](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#9 "Access the sequence of members on the string type.")]

Bu kaynak sırası Özellikler ve alanlar da dahil olmak üzere tüm üyeleri içerir, bu nedenle <xref:System.Collections.Immutable.ImmutableArray%601.OfType%2A?displayProperty=nameWithType> <xref:Microsoft.CodeAnalysis.IMethodSymbol?displayProperty=nameWithType> nesne olan öğeleri bulmak için yöntemini kullanarak filtreleyin:

[!code-csharp[Filter the sequence to only methods](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#10 "Find the subset of the collection that is the methods.")]

Sonra, yalnızca ortak olan yöntemleri döndürmek için başka bir filtre ekleyin ve şunu döndürür `string`:

[!code-csharp[Filter on return type and accessibility](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#11 "Find only the public methods that return a string.")]

Yalnızca ad özelliğini ve yalnızca herhangi bir aşırı yüklemeyi kaldırarak farklı adları seçin:

[!code-csharp[find the distinct names.](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#12 "Use the string literal to access the semantic information in the string type.")]

Ayrıca, LINQ sorgu söz dizimini kullanarak tam sorgu oluşturabilir ve sonra tüm yöntem adlarını konsolda görüntüleyebilirsiniz:

[!code-csharp[build and display the results of this query.](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#13 "Build and display the results of the query.")]

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

Bu programın parçası olan semboller hakkındaki bilgileri bulmak ve göstermek için anlamsal API 'YI kullandınız.
