---
title: Sözdizimi analizini kullanmaya başlama (Roslyn API 'Leri)
description: Sözdizimi ağaçlarını geçme, sorgulama ve yürüyen bir giriş.
ms.date: 02/05/2018
ms.custom: mvc
ms.openlocfilehash: d4163e8aadf577a5a5cbed225b26a0ec8390277e
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347009"
---
# <a name="get-started-with-syntax-analysis"></a>Sözdizimi analizini kullanmaya başlayın

Bu öğreticide, **SÖZDIZIMI API**'sini keşfedeceğiz. Sözdizimi API 'SI C# veya Visual Basic programı tanımlayan veri yapılarına erişim sağlar. Bu veri yapıları, her boyuttaki programı tam olarak temsil ettikleri yeterli ayrıntıya sahiptir. Bu yapılar, derleme ve doğru şekilde çalışan tüm programları tanımlayabilir. Ayrıca, bunları düzenleyicide yazarken tamamlanmamış programları da tanımlayabilir.

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

Bu kısa açıklama, sözdizimi API 'SI kullanılarak erişilebilen bilgi türüne genel bir bakış sağlar. Sözdizimi API 'SI, bildiğiniz tanıdık kod yapılarını açıklayan bir biçimsel API 'den daha fazla şey yapmaz C#. Tüm yetenekler, kodun satır sonları, boşluk ve girintileme dahil nasıl biçimlendirildiği hakkında bilgiler içerir. Bu bilgileri kullanarak, kodu insan programcıları veya derleyicisi tarafından yazılmış ve okunan şekilde tam olarak temsil edebilirsiniz. Bu yapının kullanılması, kaynak kodla daha anlamlı bir düzeyde etkileşim kurmanıza olanak sağlar. Artık metin dizeleri değildir, ancak bir C# programın yapısını temsil eden veriler.

Başlamak için **.net Compiler Platform SDK 'sını**yüklemeniz gerekir:

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

## <a name="understanding-syntax-trees"></a>Sözdizimi ağaçlarını anlama

C# Kod yapısının herhangi bir analizi IÇIN sözdizimi API 'sini kullanırsınız. **Sözdizimi API 'si** , sözdizimi ağaçlarını çözümlemek ve oluşturmak için ayrıştırıcıları, sözdizimi ağaçlarını ve yardımcı programları sunar. Belirli sözdizimi öğeleri için kod arama veya bir programın kodunu okuma.

Sözdizimi ağacı, C# programları ve Visual Basic anlamak C# için ve Visual Basic derleyicileri tarafından kullanılan bir veri yapısıdır. Sözdizimi ağaçları, bir proje oluşturulduğunda veya bir geliştirici isabetlerinin F5 'e göre çalışan aynı ayrıştırıcı tarafından oluşturulur. Sözdizimi ağaçları, dille tam uygunluğa sahiptir; bir kod dosyasındaki bilgilerin her bir biti ağaçta temsil edilir. Bir sözdizimi ağacının metne yazılması, ayrıştırılmış özgün metnin tam olarak yeniden üretilmesinden kaynaklanabilir. Sözdizimi ağaçları da **sabittir**; bir sözdizimi ağacı oluşturulduktan sonra hiçbir şekilde değiştirilemez. Ağaçların tüketicileri, verileri hiçbir şekilde değiştirmeksizin, kilitleri veya diğer eşzamanlılık ölçüleri olmadan birden çok iş parçacığında ağaçları analiz edebilir. API 'Leri, varolan bir ağacı değiştirmenin sonucu olan yeni ağaçlar oluşturmak için kullanabilirsiniz.

Sözdizimi ağaçlarının dört birincil yapı taşları şunlardır:

* Tüm ayrıştırma ağacını temsil eden bir örneği olan <xref:Microsoft.CodeAnalysis.SyntaxTree?displayProperty=nameWithType> sınıfı. <xref:Microsoft.CodeAnalysis.SyntaxTree> dile özgü türetme sahip soyut bir sınıftır. C# Veya Visual Basic metin ayrıştırmak için <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxTree?displayProperty=nameWithType> (veya <xref:Microsoft.CodeAnalysis.VisualBasic.VisualBasicSyntaxTree?displayProperty=nameWithType>) sınıfının ayrıştırma yöntemlerini kullanırsınız.
* <xref:Microsoft.CodeAnalysis.SyntaxNode?displayProperty=nameWithType> sınıfı, bildirimler, deyimler, yan tümceler ve ifadeler gibi sözdizimsel yapıları temsil eden örnekler.
* Tek bir anahtar sözcük, tanımlayıcı, işleç veya noktalama temsil eden <xref:Microsoft.CodeAnalysis.SyntaxToken?displayProperty=nameWithType> yapısı.
* Son olarak, belirteçler, ön işleme yönergeleri ve açıklamalar arasındaki boşluk gibi sözdizimsel bilgi bitlerini temsil eden <xref:Microsoft.CodeAnalysis.SyntaxTrivia?displayProperty=nameWithType> yapısı.

Trivia, belirteçler ve düğümler, Visual Basic veya C# kodun bir parçasındaki her şeyi tamamen temsil eden bir ağaç oluşturmak için hiyerarşik olarak oluşturulur. **Syntax Visualizer** penceresini kullanarak bu yapıyı görebilirsiniz. Visual Studio 'da **diğer Windows** > **Syntax Visualizer** > **görüntüle** ' yi seçin. Örneğin, Syntax Visualizer kullanılarak incelenen C# yukarıdaki kaynak dosya aşağıdaki şekilde görünür:

**SyntaxNode**: mavi | **SyntaxToken**: yeşil | **SyntaxTrivia**: Red ![C# kod dosyası](media/walkthrough-csharp-syntax-figure1.png)

Bu ağaç yapısına giderek, bir kod dosyasında herhangi bir deyimi, ifadeyi, belirteci veya boşluk alanını bulabilirsiniz.

Söz dizimi API 'Lerini kullanarak bir kod dosyasında herhangi bir şeyi bulabilirsiniz, ancak çoğu senaryo küçük kod parçacıklarını incelemeyi veya belirli deyimler ya da parçaları aramayı içerir. Aşağıdaki iki örnek, kodun yapısına gözatabilmek veya tek deyimler aramak için tipik kullanımları gösterir.

## <a name="traversing-trees"></a>Ağaçlara geçme

Bir sözdizimi ağacındaki düğümleri iki şekilde inceleyebilirsiniz. Her bir düğümü incelemek için ağacı çapraz geçiş yapabilir veya belirli öğeleri veya düğümleri sorgulayabilirsiniz.

### <a name="manual-traversal"></a>El ile çapraz geçiş

Bu örnek için tamamlanmış kodu [GitHub depomuza](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/SyntaxQuickStart)bakabilirsiniz.

> [!NOTE]
> Sözdizimi ağacı türleri, programdaki farklı konumlarda geçerli olan farklı sözdizimi öğelerini anlatmak için devralmayı kullanır. Bu API 'Lerin kullanılması genellikle özellikleri veya koleksiyon üyelerini belirli türetilmiş türlere atama anlamına gelir. Aşağıdaki örneklerde atama ve yayınlar, açıkça belirlenmiş değişkenler kullanılarak ayrı deyimlerdir. API 'nin dönüş türlerini ve döndürülen nesnelerin çalışma zamanı türünü görmek için kodu okuyabilirsiniz. Uygulamada, örtük olarak yazılan değişkenleri kullanmak daha yaygındır ve incelenen nesne türlerini belirtmek için API adlarını kullanır.

Yeni C# bir **tek başına kod analizi araç** projesi oluşturun:

* Visual Studio 'da yeni proje iletişim kutusunu göstermek için **dosya** > **Yeni** > **projesi** öğesini seçin.
* **Görsel C#**  > **genişletilebilirliği**altında **tek başına Kod Analizi Aracı**' nı seçin.
* Projenizi "**SyntaxTreeManualTraversal**" olarak adlandırın ve Tamam ' a tıklayın.

Temel "Merhaba Dünya!" öğesini çözümleyeceğiz Program daha önce gösteriliyor.
Merhaba Dünya programın metnini `Program` sınıfınıza bir sabit olarak ekleyin:

[!code-csharp[Declare the program text](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#1 "Declare a constant string for the program text to analyze")]

Daha sonra, `programText` sabitinde kod metni için **sözdizimi ağacını** derlemek üzere aşağıdaki kodu ekleyin.  Aşağıdaki satırı `Main` yöntemine ekleyin:

[!code-csharp[Create the tree](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#2 "Create the syntax tree")]

Bu iki satır ağacı oluşturur ve bu ağacın kök düğümünü alır. Artık ağaçtaki düğümleri inceleyebilirsiniz. Ağaçtaki kök düğümün bazı özelliklerini göstermek için bu satırları `Main` yöntemine ekleyin:

[!code-csharp[Examine the root node](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#3 "Examine the root node")]

Kodunuzun, bu ağaçtaki kök düğüm hakkında nasıl keşfedildiğini görmek için uygulamayı çalıştırın.

Genellikle, kod hakkında bilgi edinmek için ağacı gezirsiniz. Bu örnekte, API 'Leri araştırmak için bildiğiniz kodu çözümlüyorsunuz. `root` düğümünün ilk üyesini incelemek için aşağıdaki kodu ekleyin:

[!code-csharp[Find the first member](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#4 "Find the first member")]

Bu üye bir <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NamespaceDeclarationSyntax?displayProperty=nameWithType>. `namespace HelloWorld` bildiriminin kapsamındaki her şeyi temsil eder. `HelloWorld` ad alanı içinde hangi düğümlerin bildirildiği hakkında incelemek için aşağıdaki kodu ekleyin:

[!code-csharp[Find the class declaration](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#5 "Find the class declaration")]

Öğrendiklerinizi görmek için programı çalıştırın.

Artık bildirimin bir <xref:Microsoft.CodeAnalysis.CSharp.Syntax.ClassDeclarationSyntax?displayProperty=nameWithType>olduğunu öğrendiğinizden, sınıf bildirimini incelemek için o türde yeni bir değişken bildirin. Bu sınıf yalnızca bir üye içeriyor: `Main` yöntemi. `Main` yöntemini bulmak ve bir <xref:Microsoft.CodeAnalysis.CSharp.Syntax.MethodDeclarationSyntax?displayProperty=nameWithType>dönüştürmek için aşağıdaki kodu ekleyin.

[!code-csharp[Find the main declaration](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#6 "Find the main declaration")]

Yöntem bildirimi düğümü, yöntemiyle ilgili tüm sözdizimsel bilgileri içerir. `Main` yönteminin dönüş türünü, bağımsız değişkenlerin sayısını ve türlerini ve yönteminin gövde metnini gösterelim. Aşağıdaki kodu ekleyin:

[!code-csharp[Examine the syntax of the main method](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#7 "Display information about the main method")]

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

Geçiş ağaçlarına ek olarak, <xref:Microsoft.CodeAnalysis.SyntaxNode?displayProperty=nameWithType>tanımlanan sorgu yöntemlerini kullanarak sözdizimi ağacını da keşfedebilirsiniz. Bu yöntemler XPath 'i bilen herkese hemen tanıdık gelmelidir. Bu yöntemleri, LINQ ile birlikte kullanarak bir ağaçtaki şeyleri hızlıca bulabilirsiniz. <xref:Microsoft.CodeAnalysis.SyntaxNode>, <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantNodes%2A>, <xref:Microsoft.CodeAnalysis.SyntaxNode.AncestorsAndSelf%2A> ve <xref:Microsoft.CodeAnalysis.SyntaxNode.ChildNodes%2A>gibi sorgu yöntemlerine sahiptir.

Bu sorgu yöntemlerini, ağaca gidilme alternatifi olarak `Main` yönteminin bağımsız değişkenini bulmak için kullanabilirsiniz. `Main` yönteminizin en altına aşağıdaki kodu ekleyin:

[!code-csharp[Query the tree for the arguments to Main](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#8 "Query the tree for the arguments to Main")]

İlk deyim bir LINQ ifadesi ve <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantNodes%2A> yöntemi kullanarak önceki örnekteki aynı parametreyi bulur.

Programı çalıştırın ve LINQ ifadesinin ağaçta el ile gezinirken aynı parametreyi bulmuştur.

Örnek, geçilen sözdizimi ağaçları hakkında bilgileri göstermek için `WriteLine` deyimlerini kullanır. Ayrıca, hata ayıklayıcı altında tamamlanmış programı çalıştırarak çok daha fazla bilgi edinebilirsiniz. Hello World programı için oluşturulan sözdizimi ağacının bir parçası olan özelliklerin ve yöntemlerin daha fazlasını inceleyebilirsiniz.

## <a name="syntax-walkers"></a>Sözdizimi walranlar

Genellikle, belirli bir türün tüm düğümlerini bir sözdizimi ağacında (örneğin, bir dosyadaki her özellik bildirimi) bulmak istiyorsunuz. <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker?displayProperty=nameWithType> sınıfını genişleterek ve <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor.VisitPropertyDeclaration(Microsoft.CodeAnalysis.CSharp.Syntax.PropertyDeclarationSyntax)> yöntemi geçersiz kılarak, yapısını önceden bilmeden bir sözdizimi ağacında her özellik bildirimini işleyebilirsiniz. <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker>, bir düğümü ve alt öğelerinden her birini yinelemeli olarak ziyaret eden belirli bir <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor> türüdür.

Bu örnek, bir sözdizimi ağacını inceleyen bir <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> uygular. Bir `System` ad alanını içeri aktarmayan bulduğu `using` yönergeleri toplar.

Yeni C# bir **tek başına kod analizi araç** projesi oluşturun; "**SyntaxWalker**" olarak adlandırın.

Bu örnek için tamamlanmış kodu [GitHub depomuza](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/SyntaxQuickStart)bakabilirsiniz. GitHub 'daki örnek, bu öğreticide açıklanan her iki projeyi içerir.

Önceki örnekte olduğu gibi, analiz edilecek programın metnini tutmak için bir dize sabiti tanımlayabilirsiniz:

[!code-csharp[Define the code text to analyzer](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/Program.cs#1 "Define the program text to analyze")]

Bu kaynak metin, dört farklı konuma dağılmış `using` yönergeler içerir: dosya düzeyi, en üst düzey ad alanı ve iç içe yerleştirilmiş iki ad alanı. Bu örnek, kodu sorgulamak için <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> sınıfını kullanmak üzere temel bir senaryo vurgulamaktadır. Bildirimleri kullanarak bulmak için kök sözdizimi ağacındaki her düğümü ziyaret etmek daha fazla olabilir. Bunun yerine, türetilmiş bir sınıf oluşturur ve yalnızca ağaçtaki geçerli düğüm bir using yönergesi olduğunda çağrılan yöntemi geçersiz kılabilirsiniz. Ziyaretçinizin başka hiçbir düğüm türü üzerinde herhangi bir iş gerçekleştirmez. Bu tek yöntem `using` deyimlerinin her birini inceler ve `System` ad alanında olmayan bir ad alanı koleksiyonu oluşturur. Tüm `using` deyimlerini incelediği bir <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> oluşturursunuz, ancak yalnızca `using` deyimleri.

Program metnini tanımladığınıza göre, bir `SyntaxTree` oluşturmanız ve söz konusu ağacın kökünü almanız gerekir:

[!code-csharp[Create the Syntax tree and access the root](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/Program.cs#2 "Create the Syntax tree and access the root node.")]

Sonra yeni bir sınıf oluşturun. Visual Studio 'da **proje** > **Yeni öğe Ekle**' yi seçin. **Yeni öğe Ekle** iletişim kutusunda dosya adı olarak *UsingCollector.cs* yazın.

`using` ziyaretçi işlevini `UsingCollector` sınıfında uygulamalısınız. `UsingCollector` sınıfı <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker>türeten başlayın.

[!code-csharp[Declare the base class for the using collector](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/UsingCollector.cs#3 "Declare the base class for the UsingCollector")]

Topladığınız ad alanı düğümlerini tutmak için depolama gerekir.  `UsingCollector` sınıfında ortak bir salt okunurdur özelliği bildirin; Bu değişkeni, bulduğunuz <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax> düğümlerini depolamak için kullanırsınız:

[!code-csharp[Declare storage for the using syntax nodes](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/UsingCollector.cs#4 "Declare storage for the using syntax nodes")]

<xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> temel sınıf, sözdizimi ağacındaki her bir düğümü ziyaret etmek için mantığı uygular. Türetilmiş sınıf, ilgilendiğiniz belirli düğümler için çağrılan yöntemleri geçersiz kılar. Bu durumda, herhangi bir `using` yönergesi ile ilgileniyorsunuz. Yani <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor.VisitUsingDirective(Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax)> yöntemi geçersiz kılmalısınız. Bu yöntemin bir bağımsız değişkeni bir <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax?displayProperty=nameWithType> nesnesidir. Bu, ziyaretçilerin kullanılması için önemli bir avantajdır: geçersiz kılınan yöntemleri, zaten belirli düğüm türüne saçmış bağımsız değişkenlerle çağırır. <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax?displayProperty=nameWithType> sınıfı, içeri aktarılmakta olan ad alanının adını depolayan bir <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax.Name> özelliğine sahiptir. Bu bir <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax?displayProperty=nameWithType>. <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor.VisitUsingDirective(Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax)> geçersiz kılmak için aşağıdaki kodu ekleyin:

[!code-csharp[Examine using nodes for the System namespace](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/UsingCollector.cs#5 "Examine all using nodes for the System namespace.")]

Önceki örnekte olduğu gibi, bu yöntemin anlaşılmasına yardımcı olmak için çeşitli `WriteLine` deyimlerini ekledik. Ne zaman çağrdığını ve her seferinde hangi bağımsız değişkenlerin geçtiğini görebilirsiniz.

Son olarak, `UsingCollector` oluşturmak için iki satır kod eklemeniz ve tüm `using` deyimlerini toplamak için kök düğümü ziyaret etmeniz gerekir. Ardından, toplayıcılarınızın bulduğu tüm `using` deyimlerini göstermek için bir `foreach` döngüsü ekleyin:

[!code-csharp[Create the UsingCollector and visit the root node.](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/Program.cs#6 "Create the UsingCollector and visit the root node.")]

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

Tebrikler! Kaynak kodundaki belirli C# deyim ve bildirimlerin yerini bulmak IÇIN **sözdizimi API** 'sini kullandınız. C#
