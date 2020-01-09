---
title: Anlamsal analiz ile çalışmaya başlama
description: Bu öğreticide, .NET derleyici SDK 'sını kullanarak anlam analizi ile çalışmaya genel bakış sunulmaktadır.
ms.date: 02/06/2018
ms.custom: mvc
ms.openlocfilehash: 7bf2f40ea0bc059d9c517780016ca5deb805ceb6
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346975"
---
# <a name="get-started-with-semantic-analysis"></a>Anlamsal analiz ile çalışmaya başlama

Bu öğreticide, sözdizimi API 'SI hakkında bilgi sahibi olduğunuz varsayılır. [Sözdizimi analizi ile çalışmaya başlama](syntax-analysis.md) makalesi, yeterli giriş sağlar.

Bu öğreticide, **sembol** ve **bağlama API 'lerini**keşfedebilirsiniz. Bu API 'Ler, bir programın _anlam anlamı_ hakkında bilgi sağlar. Bunlar, programınızda herhangi bir sembol tarafından temsil edilen türler hakkında soru sormaya ve yanıt uygulamanıza olanak tanır.

**.Net Compiler Platform SDK 'sını**yüklemeniz gerekir:

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

## <a name="understanding-compilations-and-symbols"></a>Derlemeleri ve sembolleri anlama

.NET derleyici SDK ile daha fazla çalışırken, sözdizimi API 'SI ve anlam API 'SI arasındaki farklılıklarla ilgili bilgi sahibi olursunuz. **Sözdizimi API 'si** , bir programın _yapısına_ bakabilmeniz için izin verir. Ancak, genellikle bir programın semantiği veya _anlamı_ hakkında daha zengin bilgi istemeniz gerekir. Gevşek bir kod dosyası veya Visual Basic ya da C# kodun kod parçacığı, yalıtımda çözümlenirken, "Bu değişkenin türü nedir" gibi sorular sormak için anlamlı değildir. Bir tür adının anlamı derleme başvurularına, ad alanı içeri aktarmalara veya diğer kod dosyalarına bağlı olabilir. Bu sorular, özellikle <xref:Microsoft.CodeAnalysis.Compilation?displayProperty=nameWithType> sınıfı **ANLAMSAL API**kullanılarak yanıtlanır.

Bir <xref:Microsoft.CodeAnalysis.Compilation> örneği, derleyici tarafından görülen tek bir projeye benzerdir ve bir Visual Basic ya da C# program derlemek için gereken her şeyi temsil eder. **Derleme** , Derlenecek kaynak dosyalar kümesi, derleme başvuruları ve derleyici seçenekleri içerir. Bu bağlamdaki tüm diğer bilgileri kullanarak kodun anlamı hakkında neden olabilirsiniz. <xref:Microsoft.CodeAnalysis.Compilation>; türler, ad alanları, Üyeler ve ad ve diğer ifadelerin başvurduğu değişkenler gibi **varlıkları bulmanıza olanak** tanır. Adları ve ifadeleri **simgelerle** Ilişkilendirme işlemine **bağlama**denir.

<xref:Microsoft.CodeAnalysis.SyntaxTree?displayProperty=nameWithType>gibi, <xref:Microsoft.CodeAnalysis.Compilation> dile özgü türetmek olan soyut bir sınıftır. Bir derleme örneği oluştururken <xref:Microsoft.CodeAnalysis.CSharp.CSharpCompilation?displayProperty=nameWithType> (veya <xref:Microsoft.CodeAnalysis.VisualBasic.VisualBasicCompilation?displayProperty=nameWithType>) sınıfında bir fabrika yöntemi çağırmanız gerekir.

## <a name="querying-symbols"></a>Sembolleri sorgulama

Bu öğreticide, "Merhaba Dünya" programına tekrar göz atalım. Bu kez, bu sembollerin hangi türleri temsil ettiğini anlamak için programdaki sembolleri sorgulayın. Bir ad alanındaki türleri sorgular ve bir tür üzerinde kullanılabilir olan yöntemleri bulmayı öğrenin.

Bu örnek için tamamlanmış kodu [GitHub depomuza](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/SemanticQuickStart)bakabilirsiniz.

> [!NOTE]
> Sözdizimi ağacı türleri, programdaki farklı konumlarda geçerli olan farklı sözdizimi öğelerini anlatmak için devralmayı kullanır. Bu API 'Lerin kullanılması genellikle özellikleri veya koleksiyon üyelerini belirli türetilmiş türlere atama anlamına gelir. Aşağıdaki örneklerde atama ve yayınlar, açıkça belirlenmiş değişkenler kullanılarak ayrı deyimlerdir. API 'nin dönüş türlerini ve döndürülen nesnelerin çalışma zamanı türünü görmek için kodu okuyabilirsiniz. Uygulamada, örtük olarak yazılan değişkenleri kullanmak daha yaygındır ve incelenen nesne türlerini belirtmek için API adlarını kullanır.

Yeni C# bir **tek başına kod analizi araç** projesi oluşturun:

* Visual Studio 'da yeni proje iletişim kutusunu göstermek için **dosya** > **Yeni** > **projesi** öğesini seçin.
* **Görsel C#**  > **genişletilebilirliği**altında **tek başına Kod Analizi Aracı**' nı seçin.
* Projenizi "**Semantıhızlı başlangıç**" olarak adlandırın ve Tamam ' a tıklayın.

Temel "Merhaba Dünya!" öğesini çözümleyeceğiz Program daha önce gösteriliyor.
Merhaba Dünya programın metnini `Program` sınıfınıza bir sabit olarak ekleyin:

[!code-csharp[Declare the program test](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#1 "Declare a constant string for the program text to analyze")]

Daha sonra, `programText` sabitinde kod metni için sözdizimi ağacını derlemek üzere aşağıdaki kodu ekleyin.  Aşağıdaki satırı `Main` yöntemine ekleyin:

[!code-csharp[Create the tree](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#2 "Create the syntax tree")]

Ardından, zaten oluşturduğunuz ağaçtan bir <xref:Microsoft.CodeAnalysis.CSharp.CSharpCompilation> oluşturun. "Merhaba Dünya" örneği, <xref:System.String> ve <xref:System.Console> türlerini kullanır. Derlemenizin bu iki türü bildiren derlemeye başvurmanız gerekir. Uygun derlemeye başvuru dahil olmak üzere, sözdizimi ağacınızı oluşturmak için aşağıdaki satırı `Main` yöntemine ekleyin:

[!code-csharp[Create the compilation](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#3 "Create the compilation for the semantic model")]

<xref:Microsoft.CodeAnalysis.CSharp.CSharpCompilation.AddReferences%2A?displayProperty=nameWithType> yöntemi, derlemeye başvurular ekler. <xref:Microsoft.CodeAnalysis.MetadataReference.CreateFromFile%2A?displayProperty=nameWithType> yöntemi bir derlemeyi başvuru olarak yükler.

## <a name="querying-the-semantic-model"></a>Anlam modelini sorgulama

<xref:Microsoft.CodeAnalysis.Compilation> aldıktan sonra, bu <xref:Microsoft.CodeAnalysis.Compilation>bulunan <xref:Microsoft.CodeAnalysis.SyntaxTree> için <xref:Microsoft.CodeAnalysis.SemanticModel> isteyebilirsiniz. Anlamsal modeli, normalde IntelliSense 'ten alacağınız tüm bilgilerin kaynağı olarak düşünebilirsiniz. Bir <xref:Microsoft.CodeAnalysis.SemanticModel>, "Bu konumdaki kapsam içinde hangi adlar bulunur?", "Bu metin bloğunda hangi değişkenler kullanılır?" ve "Bu ad/ifade neye başvuruyor?" gibi sorulara yanıt verebilir. Anlam modeli oluşturmak için bu ifadeyi ekleyin:

[!code-csharp[Create the semantic model](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#4 "Create the semantic model")]

## <a name="binding-a-name"></a>Ad bağlama

<xref:Microsoft.CodeAnalysis.Compilation>, <xref:Microsoft.CodeAnalysis.SyntaxTree><xref:Microsoft.CodeAnalysis.SemanticModel> oluşturur. Modeli oluşturduktan sonra, ilk `using` yönergesini bulmak için onu sorgulayabilir ve `System` ad alanı için sembol bilgilerini alabilirsiniz. Anlam modeli oluşturmak ve ilk using ifadesinin simgesini almak için bu iki satırı `Main` yöntemine ekleyin:

[!code-csharp[Find the namespace symbol for the first using](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#5 "Find the namespace symbol for the first using")]

Yukarıdaki kod, `System` ad alanı için bir <xref:Microsoft.CodeAnalysis.SymbolInfo?displayProperty=nameWithType> almak üzere ilk `using` yönergesinin adının nasıl bağlanacağını gösterir. Yukarıdaki kod ayrıca kodun yapısını bulmak için **sözdizimi modelini** kullanmanızı da gösterir; **anlam modelini** , anlamını anlamak için kullanabilirsiniz. **Sözdizimi modeli** using deyimindeki dize `System` bulur. **Anlam modeli** `System` ad alanında tanımlanan türlerle ilgili tüm bilgilere sahiptir.

<xref:Microsoft.CodeAnalysis.SymbolInfo> nesnesinden <xref:Microsoft.CodeAnalysis.SymbolInfo.Symbol?displayProperty=nameWithType> özelliğini kullanarak <xref:Microsoft.CodeAnalysis.ISymbol?displayProperty=nameWithType> elde edebilirsiniz. Bu özellik, bu ifadenin başvurduğu simgeyi döndürür. Hiçbir şeye başvurmaz (sayısal değişmez değerler gibi), bu özellik `null`. <xref:Microsoft.CodeAnalysis.SymbolInfo.Symbol?displayProperty=nameWithType> null olmadığında <xref:Microsoft.CodeAnalysis.ISymbol.Kind?displayProperty=nameWithType> simgenin türünü gösterir. Bu örnekte, <xref:Microsoft.CodeAnalysis.ISymbol.Kind?displayProperty=nameWithType> özelliği bir <xref:Microsoft.CodeAnalysis.SymbolKind.Namespace?displayProperty=nameWithType>. Aşağıdaki kodu `Main` yöntemine ekleyin. `System` ad alanının sembolünü alır ve `System` ad alanında belirtilen tüm alt ad alanlarını görüntüler:

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
> Çıktı, `System` ad alanının alt ad alanı olan her ad alanını içermez. Yalnızca `System.String` bildirildiği derlemeye başvuran bu derlemede bulunan her ad alanını görüntüler. Diğer derlemelerde belirtilen ad alanları bu derleme tarafından tanınmıyor

### <a name="binding-an-expression"></a>Bir ifadeyi bağlama

Yukarıdaki kod, bir ada bağlama yoluyla nasıl bir sembol bulunacağını gösterir. Bir C# programda adı olmayan bağlanabilen başka ifadeler de vardır. Bu özelliği göstermek için bağlamaya basit bir dize değişmez değerine erişelim.

"Merhaba Dünya" programı, "Hello, World!" <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LiteralExpressionSyntax?displayProperty=nameWithType>içerir konsola görüntülenecek dize.

"Hello, World!" öğesini bulursunuz Programda tek dize sabit değerini bularak dize. Ardından, söz dizimi düğümünü bulduktan sonra söz konusu düğümün tür bilgilerini anlamsal modelden alın. `Main` yöntemine aşağıdaki kodu ekleyin:

[!code-csharp[Find the namespace symbol for the only using](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#7 "Find the namespace symbol for the only using")]

<xref:Microsoft.CodeAnalysis.TypeInfo?displayProperty=nameWithType> yapısı, değişmez değer türü hakkında anlam bilgisine erişim sağlayan bir <xref:Microsoft.CodeAnalysis.TypeInfo.Type?displayProperty=nameWithType> özelliği içerir. Bu örnekte, `string` türüdür. Bu özelliği yerel bir değişkene atayan bir bildirim ekleyin:

[!code-csharp[Find the semantic information about the string type](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#8 "Use the string literal to access the semantic information in the string type.")]

Bu öğreticiyi tamamlaması için, bir `string`döndüren `string` türünde belirtilen tüm ortak yöntemlerin dizisini oluşturan bir LINQ sorgusu oluşturalım. Bu sorgu karmaşıktır, bu yüzden satırı satıra göre oluşturalım ve sonra tek bir sorgu olarak yeniden yapılandırma. Bu sorgunun kaynağı, `string` türünde belirtilen tüm üyelerin sırasıdır:

[!code-csharp[Access the sequence of members on the string type](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#9 "Access the sequence of members on the string type.")]

Bu kaynak dizisi Özellikler ve alanlar da dahil olmak üzere tüm üyeleri içerir, bu nedenle <xref:Microsoft.CodeAnalysis.IMethodSymbol?displayProperty=nameWithType> nesneleri olan öğeleri bulmak için <xref:System.Collections.Immutable.ImmutableArray%601.OfType%2A?displayProperty=nameWithType> yöntemini kullanarak filtreleyin:

[!code-csharp[Filter the sequence to only methods](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#10 "Find the subset of the collection that is the methods.")]

Sonra, yalnızca ortak olan yöntemleri döndürmek ve bir `string`döndürmek için başka bir filtre ekleyin:

[!code-csharp[Filter on return type and accessibility](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#11 "Find only the public methods that return a string.")]

Yalnızca ad özelliğini ve yalnızca herhangi bir aşırı yüklemeyi kaldırarak farklı adları seçin:

[!code-csharp[find the distinct names.](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#12 "Use the string literal to access the semantic information in the string type.")]

Ayrıca, LINQ sorgu söz dizimini kullanarak tam sorgu oluşturabilir ve sonra tüm yöntem adlarını konsolda görüntüleyebilirsiniz:

[!code-csharp[build and display the results of this query.](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#13 "Build and display the results of the query.")]

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
