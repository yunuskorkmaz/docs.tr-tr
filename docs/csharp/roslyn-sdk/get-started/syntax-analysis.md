---
title: Sözdizimi analizini kullanmaya başlama (Roslyn API 'Leri)
description: Sözdizimi ağaçlarını geçme, sorgulama ve yürüyen bir giriş.
ms.date: 02/05/2018
ms.custom: mvc
ms.openlocfilehash: 8b9dd909a83877755dc1ebafd58aae892e460b93
ms.sourcegitcommit: a8a205034eeffc7c3e1bdd6f506a75b0f7099ebf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2020
ms.locfileid: "91756162"
---
# <a name="get-started-with-syntax-analysis"></a>Sözdizimi analizini kullanmaya başlayın

Bu öğreticide, **SÖZDIZIMI API**'sini keşfedeceğiz. Sözdizimi API 'SI, C# veya Visual Basic programını tanımlayan veri yapılarına erişim sağlar. Bu veri yapıları, her boyuttaki programı tam olarak temsil ettikleri yeterli ayrıntıya sahiptir. Bu yapılar, derleme ve doğru şekilde çalışan tüm programları tanımlayabilir. Ayrıca, bunları düzenleyicide yazarken tamamlanmamış programları da tanımlayabilir.

Bu zengin ifadeyi etkinleştirmek için, söz dizimi API 'sini oluşturan veri yapıları ve API 'Ler karmaşık olması gerekir. Veri yapısının tipik "Merhaba Dünya" programı için nasıl göründüğünü başlayalım:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;

namespace HelloWorld
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

Önceki programın metnine bakın. Tanıdık öğeleri tanısınız. Tüm metin, tek bir kaynak dosyasını veya bir **derleme birimini**temsil eder. Bu kaynak dosyanın ilk üç satırı **yönergeleri kullanıyor**. Kalan kaynak, bir **ad alanı bildiriminde**bulunur. Ad alanı bildirimi bir alt **sınıf bildirimi**içerir. Sınıf bildirimi bir **Yöntem bildirimi**içerir.

Sözdizimi API 'SI, derleme birimini temsil eden köke sahip bir ağaç yapısı oluşturur. Ağaçtaki düğümler using yönergelerini, ad alanı bildirimini ve programın diğer tüm öğelerini temsil eder. Ağaç yapısı en düşük düzeylere devam eder: "Merhaba Dünya!" dizesi , bir **bağımsız değişkenin**alt değeri olan **dize sabit değer belirtecidir** . Sözdizimi API 'SI programın yapısına erişim sağlar. Belirli kod uygulamalarını sorgulayabilir, kodu anlamak için ağacın tamamına kılavuzluk edebilir ve var olan ağacı değiştirerek yeni ağaçlar oluşturabilirsiniz.

Bu kısa açıklama, sözdizimi API 'SI kullanılarak erişilebilen bilgi türüne genel bir bakış sağlar. Sözdizimi API 'SI, C# ' den bildiğiniz tanıdık kod yapılarını açıklayan bir biçimsel API 'den daha fazla şey yapmaz. Tüm yetenekler, kodun satır sonları, boşluk ve girintileme dahil nasıl biçimlendirildiği hakkında bilgiler içerir. Bu bilgileri kullanarak, kodu insan programcıları veya derleyicisi tarafından yazılmış ve okunan şekilde tam olarak temsil edebilirsiniz. Bu yapının kullanılması, kaynak kodla daha anlamlı bir düzeyde etkileşim kurmanıza olanak sağlar. Artık metin dizeleri değildir, ancak bir C# programının yapısını temsil eden veriler.

Başlamak için **.net Compiler Platform SDK 'sını**yüklemeniz gerekir:

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

## <a name="understanding-syntax-trees"></a>Sözdizimi ağaçlarını anlama

C# kodu yapısının herhangi bir analizi için sözdizimi API 'sini kullanırsınız. **Sözdizimi API 'si** , sözdizimi ağaçlarını çözümlemek ve oluşturmak için ayrıştırıcıları, sözdizimi ağaçlarını ve yardımcı programları sunar. Belirli sözdizimi öğeleri için kod arama veya bir programın kodunu okuma.

Sözdizimi ağacı, c# ve Visual Basic programlarını anlamak için C# ve Visual Basic derleyicileri tarafından kullanılan bir veri yapısıdır. Sözdizimi ağaçları, bir proje oluşturulduğunda veya bir geliştirici isabetlerinin F5 'e göre çalışan aynı ayrıştırıcı tarafından oluşturulur. Sözdizimi ağaçları, dille tam uygunluğa sahiptir; bir kod dosyasındaki bilgilerin her bir biti ağaçta temsil edilir. Bir sözdizimi ağacının metne yazılması, ayrıştırılmış özgün metnin tam olarak yeniden üretilmesinden kaynaklanabilir. Sözdizimi ağaçları da **sabittir**; bir sözdizimi ağacı oluşturulduktan sonra hiçbir şekilde değiştirilemez. Ağaçların tüketicileri, verileri hiçbir şekilde değiştirmeksizin, kilitleri veya diğer eşzamanlılık ölçüleri olmadan birden çok iş parçacığında ağaçları analiz edebilir. API 'Leri, varolan bir ağacı değiştirmenin sonucu olan yeni ağaçlar oluşturmak için kullanabilirsiniz.

Sözdizimi ağaçlarının dört birincil yapı taşları şunlardır:

* <xref:Microsoft.CodeAnalysis.SyntaxTree?displayProperty=nameWithType>Tüm ayrıştırma ağacını temsil eden bir örneği olan sınıfı. <xref:Microsoft.CodeAnalysis.SyntaxTree> dile özgü türetme sahip olan soyut bir sınıftır. <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxTree?displayProperty=nameWithType> <xref:Microsoft.CodeAnalysis.VisualBasic.VisualBasicSyntaxTree?displayProperty=nameWithType> C# (veya Visual Basic) içinde metin ayrıştırmak için (veya) sınıfının Parse yöntemlerini kullanırsınız.
* <xref:Microsoft.CodeAnalysis.SyntaxNode?displayProperty=nameWithType>Bildirim, deyimler, yan tümceler ve ifadeler gibi sözdizimsel yapıları temsil eden sınıf, örnekleri.
* <xref:Microsoft.CodeAnalysis.SyntaxToken?displayProperty=nameWithType>Tek bir anahtar sözcük, tanımlayıcı, işleç veya noktalama temsil eden yapı.
* Ve son <xref:Microsoft.CodeAnalysis.SyntaxTrivia?displayProperty=nameWithType> olarak, belirteçler, ön işleme yönergeleri ve açıklamalar arasındaki boşluk gibi sözdizimsel bilgi bitlerini temsil eden yapı.

Trivia, belirteçler ve düğümler, Visual Basic veya C# kodu parçasındaki her şeyi tamamen temsil eden bir ağaç oluşturmak için hiyerarşik olarak oluşturulur. **Syntax Visualizer** penceresini kullanarak bu yapıyı görebilirsiniz. Visual Studio 'da **View**  >  **diğer Windows**  >  **Syntax Visualizer**görüntüle ' yi seçin. Örneğin, **Syntax Visualizer** kullanılarak Incelenen önceki C# kaynak dosyası aşağıdaki şekilde görünür:

**SyntaxNode**: mavi | **SyntaxToken**: yeşil | **SyntaxTrivia**: Red ![ C# kod dosyası](media/walkthrough-csharp-syntax-figure1.png)

Bu ağaç yapısına giderek, bir kod dosyasında herhangi bir deyimi, ifadeyi, belirteci veya boşluk alanını bulabilirsiniz.

Söz dizimi API 'Lerini kullanarak bir kod dosyasında herhangi bir şeyi bulabilirsiniz, ancak çoğu senaryo küçük kod parçacıklarını incelemeyi veya belirli deyimler ya da parçaları aramayı içerir. Aşağıdaki iki örnek, kodun yapısına gözatabilmek veya tek deyimler aramak için tipik kullanımları gösterir.

## <a name="traversing-trees"></a>Ağaçlara geçme

Bir sözdizimi ağacındaki düğümleri iki şekilde inceleyebilirsiniz. Her bir düğümü incelemek için ağacı çapraz geçiş yapabilir veya belirli öğeleri veya düğümleri sorgulayabilirsiniz.

### <a name="manual-traversal"></a>El ile çapraz geçiş

Bu örnek için tamamlanmış kodu [GitHub depomuza](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/SyntaxQuickStart)bakabilirsiniz.

> [!NOTE]
> Sözdizimi ağacı türleri, programdaki farklı konumlarda geçerli olan farklı sözdizimi öğelerini anlatmak için devralmayı kullanır. Bu API 'Lerin kullanılması genellikle özellikleri veya koleksiyon üyelerini belirli türetilmiş türlere atama anlamına gelir. Aşağıdaki örneklerde atama ve yayınlar, açıkça belirlenmiş değişkenler kullanılarak ayrı deyimlerdir. API 'nin dönüş türlerini ve döndürülen nesnelerin çalışma zamanı türünü görmek için kodu okuyabilirsiniz. Uygulamada, örtük olarak yazılan değişkenleri kullanmak daha yaygındır ve incelenen nesne türlerini belirtmek için API adlarını kullanır.

Yeni bir C# **tek başına kod analizi araç** projesi oluşturun:

* Visual Studio 'da **File**  >  **New**  >  Yeni proje iletişim kutusunu göstermek için dosya yeni**Proje** ' yi seçin.
* **Visual C#**  >  **genişletilebilirliği**altında **tek başına Kod Analizi Aracı**' nı seçin.
* Projenizi "**SyntaxTreeManualTraversal**" olarak adlandırın ve Tamam ' a tıklayın.

Temel "Merhaba Dünya!" öğesini çözümleyeceğiz Program daha önce gösteriliyor.
Merhaba Dünya programın metnini sınıfınıza bir sabit olarak ekleyin `Program` :

[!code-csharp[Declare the program text](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#1 "Declare a constant string for the program text to analyze")]

Sonra, sabit içindeki kod metni için **sözdizimi ağacını** derlemek üzere aşağıdaki kodu ekleyin `programText` .  Aşağıdaki satırı `Main` yöntemine ekleyin:

[!code-csharp[Create the tree](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#2 "Create the syntax tree")]

Bu iki satır ağacı oluşturur ve bu ağacın kök düğümünü alır. Artık ağaçtaki düğümleri inceleyebilirsiniz. `Main`Ağaçtaki kök düğümün bazı özelliklerini göstermek için bu satırları yönteminizin içine ekleyin:

[!code-csharp[Examine the root node](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#3 "Examine the root node")]

Kodunuzun, bu ağaçtaki kök düğüm hakkında nasıl keşfedildiğini görmek için uygulamayı çalıştırın.

Genellikle, kod hakkında bilgi edinmek için ağacı gezirsiniz. Bu örnekte, API 'Leri araştırmak için bildiğiniz kodu çözümlüyorsunuz. Düğümün ilk üyesini incelemek için aşağıdaki kodu ekleyin `root` :

[!code-csharp[Find the first member](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#4 "Find the first member")]

Bu üye bir <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NamespaceDeclarationSyntax?displayProperty=nameWithType> . Bildirimin kapsamındaki her şeyi temsil eder `namespace HelloWorld` . Ad alanı içinde hangi düğümlerin bildirildiği hakkında incelemek için aşağıdaki kodu ekleyin `HelloWorld` :

[!code-csharp[Find the class declaration](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#5 "Find the class declaration")]

Öğrendiklerinizi görmek için programı çalıştırın.

Bildirimin bir olduğunu bildiğinize göre <xref:Microsoft.CodeAnalysis.CSharp.Syntax.ClassDeclarationSyntax?displayProperty=nameWithType> , sınıf bildirimini incelemek için o türde yeni bir değişken bildirin. Bu sınıf yalnızca bir üye içeriyor: `Main` yöntemi. `Main`Yöntemini bulmak ve ' a dönüştürmek için aşağıdaki kodu ekleyin <xref:Microsoft.CodeAnalysis.CSharp.Syntax.MethodDeclarationSyntax?displayProperty=nameWithType> .

[!code-csharp[Find the main declaration](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#6 "Find the main declaration")]

Yöntem bildirimi düğümü, yöntemiyle ilgili tüm sözdizimsel bilgileri içerir. Yöntemin dönüş türünü `Main` , bağımsız değişkenlerin sayısını ve türlerini ve yönteminin gövde metnini gösterelim. Şu kodu ekleyin:

[!code-csharp[Examine the syntax of the main method](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#7 "Display information about the main method")]

Bu program hakkında bulduğunuz tüm bilgileri görmek için programı çalıştırın:

```text
The tree is a CompilationUnit node.
The tree has 1 elements in it.
The tree has 4 using statements. They are:
        System
        System.Collections
        System.Linq
        System.Text
The first member is a NamespaceDeclaration.
There are 1 members declared in this namespace.
The first member is a ClassDeclaration.
There are 1 members declared in the Program class.
The first member is a MethodDeclaration.
The return type of the Main method is void.
The method has 1 parameters.
The type of the args parameter is string[].
The body text of the Main method follows:
        {
            Console.WriteLine("Hello, World!");
        }
```

### <a name="query-methods"></a>Sorgu yöntemleri

Geçiş ağaçlarına ek olarak, sözdizimi ağacını üzerinde tanımlanan sorgu yöntemlerini kullanarak da keşfedebilirsiniz <xref:Microsoft.CodeAnalysis.SyntaxNode?displayProperty=nameWithType> . Bu yöntemler XPath 'i bilen herkese hemen tanıdık gelmelidir. Bu yöntemleri, LINQ ile birlikte kullanarak bir ağaçtaki şeyleri hızlıca bulabilirsiniz. , <xref:Microsoft.CodeAnalysis.SyntaxNode> Ve gibi sorgu yöntemlerine sahiptir <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantNodes%2A> <xref:Microsoft.CodeAnalysis.SyntaxNode.AncestorsAndSelf%2A> <xref:Microsoft.CodeAnalysis.SyntaxNode.ChildNodes%2A> .

Bu sorgu yöntemlerini, `Main` ağaca gidilme alternatifi olarak yönteme bağımsız değişkeni bulmak için kullanabilirsiniz. Aşağıdaki kodu yönteminizin en altına ekleyin `Main` :

[!code-csharp[Query the tree for the arguments to Main](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#8 "Query the tree for the arguments to Main")]

İlk deyim bir LINQ ifadesi ve <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantNodes%2A> önceki örnekteki ile aynı parametreyi bulmak için yöntemini kullanır.

Programı çalıştırın ve LINQ ifadesinin ağaçta el ile gezinirken aynı parametreyi bulmuştur.

Örnek `WriteLine` deyimleri, geçen sözdizimi ağaçları hakkında bilgi göstermek için kullanır. Ayrıca, hata ayıklayıcı altında tamamlanmış programı çalıştırarak çok daha fazla bilgi edinebilirsiniz. Hello World programı için oluşturulan sözdizimi ağacının bir parçası olan özelliklerin ve yöntemlerin daha fazlasını inceleyebilirsiniz.

## <a name="syntax-walkers"></a>Sözdizimi walranlar

Genellikle, belirli bir türün tüm düğümlerini bir sözdizimi ağacında (örneğin, bir dosyadaki her özellik bildirimi) bulmak istiyorsunuz. <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker?displayProperty=nameWithType>Sınıfını genişleterek ve yöntemi geçersiz kılarak <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor.VisitPropertyDeclaration(Microsoft.CodeAnalysis.CSharp.Syntax.PropertyDeclarationSyntax)> , yapısını önceden bilmeden bir sözdizimi ağacında her özellik bildirimini işleyebilirsiniz. <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> , <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor> bir düğümü ve alt öğelerinden her birini yinelemeli olarak ziyaret eden belirli bir türüdür.

Bu örnek, bir <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> sözdizimi ağacını inceleyen bir uygular. `using`Bir ad alanını içeri aktarmayan bulduğu yönergeleri toplar `System` .

Yeni bir C# **tek başına kod analizi araç** projesi oluşturun; "**SyntaxWalker**" olarak adlandırın.

Bu örnek için tamamlanmış kodu [GitHub depomuza](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/SyntaxQuickStart)bakabilirsiniz. GitHub 'daki örnek, bu öğreticide açıklanan her iki projeyi içerir.

Önceki örnekte olduğu gibi, analiz edilecek programın metnini tutmak için bir dize sabiti tanımlayabilirsiniz:

[!code-csharp[Define the code text to analyzer](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/Program.cs#1 "Define the program text to analyze")]

Bu kaynak metin, `using` dört farklı konuma dağılmış olan yönergeleri içerir: dosya düzeyi, en üst düzey ad alanı ve iç içe yerleştirilmiş iki ad alanı. Bu örnek, <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> kodu sorgulamak için sınıfının kullanılmasına yönelik temel bir senaryoyu vurgular. Bildirimleri kullanarak bulmak için kök sözdizimi ağacındaki her düğümü ziyaret etmek daha fazla olabilir. Bunun yerine, türetilmiş bir sınıf oluşturur ve yalnızca ağaçtaki geçerli düğüm bir using yönergesi olduğunda çağrılan yöntemi geçersiz kılabilirsiniz. Ziyaretçinizin başka hiçbir düğüm türü üzerinde herhangi bir iş gerçekleştirmez. Bu tek yöntem deyimlerin her birini inceler `using` ve ad alanında olmayan ad alanlarını bir koleksiyon oluşturur `System` . <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker>Tüm deyimlerini ve yalnızca deyimlerini incelediği bir oluşturursunuz `using` `using` .

Program metnini tanımladığınıza göre, `SyntaxTree` Bu ağacın kökünü oluşturmanız ve bu ağacın kökünü almanız gerekir:

[!code-csharp[Create the Syntax tree and access the root](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/Program.cs#2 "Create the Syntax tree and access the root node.")]

Sonra yeni bir sınıf oluşturun. Visual Studio 'da **Proje**  >  **Ekle yeni öğe**' yi seçin. **Yeni öğe Ekle** iletişim kutusunda dosya adı olarak *UsingCollector.cs* yazın.

`using`Ziyaretçi işlevselliğini `UsingCollector` sınıfında uygulamalısınız. `UsingCollector`Sınıfın türemesini sağlayarak başlayın <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> .

[!code-csharp[Declare the base class for the using collector](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/UsingCollector.cs#3 "Declare the base class for the UsingCollector")]

Topladığınız ad alanı düğümlerini tutmak için depolama gerekir.  Sınıfında ortak bir salt okunurdur özelliği bildirin `UsingCollector` ; bulduğunuz düğümleri depolamak için bu değişkeni kullanırsınız <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax> :

[!code-csharp[Declare storage for the using syntax nodes](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/UsingCollector.cs#4 "Declare storage for the using syntax nodes")]

Temel sınıf, <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> söz dizimi ağacındaki her bir düğümü ziyaret etmek için mantığı uygular. Türetilmiş sınıf, ilgilendiğiniz belirli düğümler için çağrılan yöntemleri geçersiz kılar. Bu durumda, herhangi bir yönergeyle ilgileniyorsunuz `using` . Yani, yöntemini geçersiz kılmanız gerekir <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor.VisitUsingDirective(Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax)> . Bu yöntemin bir bağımsız değişkeni bir <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax?displayProperty=nameWithType> nesnedir. Bu, ziyaretçilerin kullanılması için önemli bir avantajdır: geçersiz kılınan yöntemleri, zaten belirli düğüm türüne saçmış bağımsız değişkenlerle çağırır. <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax?displayProperty=nameWithType>Sınıfı, <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax.Name> içeri aktarılmakta olan ad alanının adını depolayan bir özelliğe sahiptir. Bir <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax?displayProperty=nameWithType> . Geçersiz kılmada aşağıdaki kodu ekleyin <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor.VisitUsingDirective(Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax)> :

[!code-csharp[Examine using nodes for the System namespace](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/UsingCollector.cs#5 "Examine all using nodes for the System namespace.")]

Önceki örnekte olduğu gibi, `WriteLine` Bu yöntemin anlaşılmasına yardımcı olmak için çeşitli deyimler eklediniz. Ne zaman çağrdığını ve her seferinde hangi bağımsız değişkenlerin geçtiğini görebilirsiniz.

Son olarak, oluşturmak için iki satır kod eklemeniz `UsingCollector` ve tüm deyimlerini toplamak için kök düğümü ziyaret etmeniz gerekir `using` . Ardından, `foreach` toplayıcılarınızın bulduğu tüm deyimleri göstermek için bir döngü ekleyin `using` :

[!code-csharp[Create the UsingCollector and visit the root node.](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/Program.cs#6 "Create the UsingCollector and visit the root node.")]

Programı derleyin ve çalıştırın. Aşağıdaki çıkışı görmeniz gerekir:

```console
        VisitUsingDirective called with System.
        VisitUsingDirective called with System.Collections.Generic.
        VisitUsingDirective called with System.Linq.
        VisitUsingDirective called with System.Text.
        VisitUsingDirective called with Microsoft.CodeAnalysis.
                Success. Adding Microsoft.CodeAnalysis.
        VisitUsingDirective called with Microsoft.CodeAnalysis.CSharp.
                Success. Adding Microsoft.CodeAnalysis.CSharp.
        VisitUsingDirective called with Microsoft.
                Success. Adding Microsoft.
        VisitUsingDirective called with System.ComponentModel.
        VisitUsingDirective called with Microsoft.Win32.
                Success. Adding Microsoft.Win32.
        VisitUsingDirective called with System.Runtime.InteropServices.
        VisitUsingDirective called with System.CodeDom.
        VisitUsingDirective called with Microsoft.CSharp.
                Success. Adding Microsoft.CSharp.
Microsoft.CodeAnalysis
Microsoft.CodeAnalysis.CSharp
Microsoft
Microsoft.Win32
Microsoft.CSharp
Press any key to continue . . .
```

Tebrikler! C# kaynak kodunda belirli türdeki C# deyimlerini ve bildirimlerini bulmak için **SÖZDIZIMI API** 'sini kullandınız.
