---
title: Sözdizimi analizine başlayın (Roslyn API'leri)
description: Sözdizimi ağaçlarını gezmeye, sorgulamaya ve yürümeye giriş.
ms.date: 02/05/2018
ms.custom: mvc
ms.openlocfilehash: 22d1303c9daa2ae35cf130b0c857cd7a5efdbe76
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240525"
---
# <a name="get-started-with-syntax-analysis"></a>Sözdizimi analizine başlayın

Bu eğitimde, **Sözdizimi API'sini**keşfedeceksiniz. Sözdizimi API' si, C# veya Visual Basic programını açıklayan veri yapılarına erişim sağlar. Bu veri yapıları, herhangi bir boyuttaki herhangi bir programı tam olarak temsil edebilecekleri kadar ayrıntıya sahiptir. Bu yapılar, derleyen ve doğru çalışan tam programları açıklayabilir. Ayrıca, siz yazarken eksik programları editörde tanımlayabilirler.

Bu zengin ifadeyi etkinleştirmek için, Sözdizimi API'sini oluşturan veri yapıları ve API'ler mutlaka karmaşıktır. Tipik "Hello World" programı için veri yapısının nasıl göründüğüyle başlayalım:

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

Önceki programın metnine bakın. Tanıdık öğeleri tanıyorsun. Metnin tamamı tek bir kaynak dosyayı veya **derleme birimini**temsil eder. Bu kaynak dosyanın ilk üç satırı **yönergeleri kullanıyor.** Kalan kaynak bir **ad alanı bildiriminde**bulunur. Ad alanı bildirimi bir alt **sınıf bildirimi**içerir. Sınıf bildirimi bir **yöntem bildirimi**içerir.

Sözdizimi API derleme birimini temsil eden kök içeren bir ağaç yapısı oluşturur. Ağaçtaki düğümler, kullanma yönergelerini, ad alanı bildirimini ve programın diğer tüm öğelerini temsil eder. Ağaç yapısı en düşük seviyelere kadar devam ediyor: dize "Merhaba Dünya!" bir **bağımsız değişkenin**soyundan gelen bir **dize gerçek belirtecidir.** Sözdizimi API'si programın yapısına erişim sağlar. Belirli kod uygulamaları için sorgu yapabilir, kodu anlamak için tüm ağacı gezdirebilir ve varolan ağacı değiştirerek yeni ağaçlar oluşturabilirsiniz.

Bu kısa açıklama, Sözdizimi API'sini kullanarak erişilebilen bilgi türüne genel bir bakış sağlar. Sözdizimi API'si, C#'dan bildiğiniz tanıdık kod yapılarını açıklayan resmi bir API'den başka bir şey değildir. Tam özellikler, satır sonları, beyaz boşluk ve girintiyi de içeren kodun nasıl biçimlendirilip biçimlendirilenhakkında bilgi içerir. Bu bilgileri kullanarak, kodu insan programcılar veya derleyici tarafından yazılmış ve okunmuş olarak tam olarak temsil edebilirsiniz. Bu yapıyı kullanmak, kaynak kodla son derece anlamlı bir düzeyde etkileşim kurmanızı sağlar. Artık metin dizeleri değil, C# programının yapısını temsil eden verilerdir.

Başlamak için **.NET Derleyici Platformu SDK'yı**yüklemeniz gerekir:

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

## <a name="understanding-syntax-trees"></a>Sözdizimi ağaçlarını anlama

C# kodunun yapısının herhangi bir analizi için Sözdizimi API'sini kullanırsınız. **Sözdizimi API** ayrışdırıcıları, sözdizimi ağaçlarını ve sözdizimi ağaçlarını çözümleme ve oluşturma yardımcı larını ortaya çıkarır. Belirli sözdizimi öğeleri için kodu arama veya bir programın kodunu okuma şeklidir.

Sözdizimi ağacı, C# ve Visual Basic derleyicileri tarafından C# ve Visual Basic programlarını anlamak için kullanılan bir veri yapısıdır. Sözdizimi ağaçları, bir proje inşa edildiğinde veya geliştirici F5'e ulaştığında çalışan aynı ayrıştırıcı tarafından üretilir. Sözdizimi ağaçları nın dili yle tam sadakati vardır; kod dosyasındaki her bilgi parçası ağaçta temsil edilir. Metne sözdizimi ağacı yazmak, ayrıştırılan tam özgün metni yeniden üretir. Sözdizimi ağaçları da **değişmez;** bir kez oluşturulan bir sözdizimi ağacı asla değiştirilemez. Ağaçların tüketicileri, verilerin hiçbir zaman değişmediğini bilerek, kilitler veya diğer eşzamanlılık önlemleri olmadan ağaçları birden fazla iplik üzerinde analiz edebilirler. Varolan bir ağacı değiştirmenin sonucu olan yeni ağaçlar oluşturmak için API'leri kullanabilirsiniz.

Sözdizimi ağaçlarının dört ana yapı taşları şunlardır:

* Sınıf, <xref:Microsoft.CodeAnalysis.SyntaxTree?displayProperty=nameWithType> bir örneği tüm ayrışdıran ağacı temsil eder. <xref:Microsoft.CodeAnalysis.SyntaxTree>dile özgü türevleri olan soyut bir sınıftır. C# veya Visual Basic'teki <xref:Microsoft.CodeAnalysis.VisualBasic.VisualBasicSyntaxTree?displayProperty=nameWithType>metni ayrıştırmak için (veya) sınıfının <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxTree?displayProperty=nameWithType> ayrıştırma yöntemlerini kullanırsınız.
* Bildirimler, deyimler, yan tümceler ve ifadeler gibi sözdizim yapılarını temsil eden <xref:Microsoft.CodeAnalysis.SyntaxNode?displayProperty=nameWithType> sınıf.
* Tek <xref:Microsoft.CodeAnalysis.SyntaxToken?displayProperty=nameWithType> bir anahtar kelimeyi, tanımlayıcıyı, işleçveya noktalama işaretlerini temsil eden yapı.
* Ve son <xref:Microsoft.CodeAnalysis.SyntaxTrivia?displayProperty=nameWithType> olarak, belirteçler, ön işleme yönergeleri ve yorumlar arasındaki beyaz boşluk gibi sözdizimsel olarak önemsiz bilgi bitlerini temsil eden yapı.

Trivia, belirteçleri ve düğümler hiyerarşik olarak Visual Basic veya C# kodunun bir parçasındaki her şeyi temsil eden bir ağaç oluşturmak üzere oluşturulur. Bu yapıyı **Sözdizimi Görselleştiricisi** penceresini kullanarak görebilirsiniz. Visual Studio'da**Diğer Windows** > **Sözdizimi Görselleştiricisini** **Görüntüle'yi** > seçin. Örneğin, **Sözdizimi Görselleştiricisi** kullanılarak incelenen önceki C# kaynak dosyası aşağıdaki şekilde görünür:

**SözdizimiNode**: Mavi | **SözdizimiToken**: Yeşil | **SözdizimiTrivia** ![: Kırmızı C# Kodu Dosyası](media/walkthrough-csharp-syntax-figure1.png)

Bu ağaç yapısında gezinerek, bir kod dosyasında herhangi bir ifade, ifade, belirteç veya beyaz boşluk biti bulabilirsiniz.

Sözdizimi API'lerini kullanarak bir kod dosyasında herhangi bir şey bulabilirsiniz, ancak çoğu senaryo kod küçük parçacıkları inceleyerek veya belirli ifadeler veya parçalar için arama içerir. İzleyen iki örnek, kodun yapısına göz atmak veya tek bir deyim aramak için tipik kullanımları gösterir.

## <a name="traversing-trees"></a>Ağaçların geçişi

Sözdizimi ağacındaki düğümleri iki şekilde inceleyebilirsiniz. Her düğümü incelemek için ağaçta geçiş yapabilir veya belirli öğeleri veya düğümleri sorgulayabilirsiniz.

### <a name="manual-traversal"></a>Manuel geçiş

Bu örneğin bitmiş kodunu [GitHub depomuzda](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/SyntaxQuickStart)görebilirsiniz.

> [!NOTE]
> Sözdizimi Ağacı türleri, programdaki farklı konumlarda geçerli olan farklı sözdizimi öğelerini açıklamak için kalıtım kullanır. Bu API'lerin kullanılması genellikle özellikleri veya koleksiyon üyelerini belirli türemiş türlere dökümü anlamına gelir. Aşağıdaki örneklerde, atama ve dökümler, açıkça yazılan değişkenler kullanılarak ayrı ifadelerdir. API'nin geri dönüş türlerini ve döndürülen nesnelerin çalışma zamanı türünü görmek için kodu okuyabilirsiniz. Uygulamada, örtülü olarak yazılan değişkenleri kullanmak ve incelenmekte olan nesnelerin türünü açıklamak için API adlarına güvenmek daha yaygındır.

Yeni bir C# **Tek Başına Kod Analizi Aracı** projesi oluşturun:

* Visual Studio'da, Yeni Proje iletişim kutusunu görüntülemek için **Dosya** > **Yeni** > **Projesi'ni** seçin.
* **Visual C#** > **Genişletilebilirlik** **altında, Tek Başına Kod Analiz Aracı'nı**seçin.
* Projenizi "**SözdizimiTreeManualTraversal**" adını ver ve Tamam'ı tıklatın.

Temel "Merhaba Dünya"yı analiz edeceksin. program daha önce gösterilmiştir.
Merhaba Dünya programı için metni sınıfınızda `Program` sabit olarak ekleyin:

[!code-csharp[Declare the program text](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#1 "Declare a constant string for the program text to analyze")]

Ardından, `programText` sabitteki kod metni için **sözdizimi ağacı** oluşturmak için aşağıdaki kodu ekleyin.  Yönteminize `Main` aşağıdaki satırı ekleyin:

[!code-csharp[Create the tree](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#2 "Create the syntax tree")]

Bu iki satır ağacı oluşturmak ve bu ağacın kök düğümünü almak. Artık ağaçtaki düğümleri inceleyebilirsiniz. Ağaçtaki kök `Main` düğümünün bazı özelliklerini görüntülemek için yönteminize bu satırları ekleyin:

[!code-csharp[Examine the root node](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#3 "Examine the root node")]

Kodunuzun bu ağaçtaki kök düğümü hakkında ne bulduğunu görmek için uygulamayı çalıştırın.

Genellikle, kod hakkında bilgi edinmek için ağaç çapraz istiyorum. Bu örnekte, API'leri keşfetmek için bildiğiniz kodu çözümlüyorsunuz. `root` Düğümün ilk üyesini incelemek için aşağıdaki kodu ekleyin:

[!code-csharp[Find the first member](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#4 "Find the first member")]

Bu üye <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NamespaceDeclarationSyntax?displayProperty=nameWithType>bir . Beyanname kapsamındaki her şeyi `namespace HelloWorld` temsil eder. Ad alanı içinde hangi düğümlerin beyan edildiğine `HelloWorld` inanca göre aşağıdaki kodu ekleyin:

[!code-csharp[Find the class declaration](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#5 "Find the class declaration")]

Öğrendiklerinizi görmek için programı çalıştırın.

Artık, sınıf bildirimini <xref:Microsoft.CodeAnalysis.CSharp.Syntax.ClassDeclarationSyntax?displayProperty=nameWithType>incelemek için bu tür yeni bir değişken bildirin. Bu sınıf yalnızca bir `Main` üye içerir: yöntem. `Main` Yöntemi bulmak için aşağıdaki kodu ekleyin ve <xref:Microsoft.CodeAnalysis.CSharp.Syntax.MethodDeclarationSyntax?displayProperty=nameWithType>bir .

[!code-csharp[Find the main declaration](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#6 "Find the main declaration")]

Yöntem bildirimi düğümü, yöntem le ilgili tüm sözdizimsiz bilgileri içerir. Yöntemin `Main` dönüş türünü, bağımsız değişkenlerin sayısını ve türlerini ve yöntemin gövde metnini görüntüleyelim. Aşağıdaki kodu ekleyin:

[!code-csharp[Examine the syntax of the main method](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#7 "Display information about the main method")]

Bu program hakkında keşfettiğiniz tüm bilgileri görmek için programı çalıştırın:

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

Ağaçlarda geçişe ek olarak, sözdizimi ağacında <xref:Microsoft.CodeAnalysis.SyntaxNode?displayProperty=nameWithType>tanımlanan sorgu yöntemlerini kullanarak da keşfedebilirsiniz. Bu yöntemler, XPath'e aşina olan herkes için hemen bilinmelidir. Bir ağaçtaki şeyleri hızlı bir şekilde bulmak için LINQ ile bu yöntemleri kullanabilirsiniz. Gibi <xref:Microsoft.CodeAnalysis.SyntaxNode> sorgu yöntemleri <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantNodes%2A>vardır <xref:Microsoft.CodeAnalysis.SyntaxNode.AncestorsAndSelf%2A> <xref:Microsoft.CodeAnalysis.SyntaxNode.ChildNodes%2A>ve .

Bu sorgu yöntemlerini, `Main` yönteme bağımsız değişkeni ağaçta gezinmeye alternatif olarak bulmak için kullanabilirsiniz. Yönteminizin `Main` altına aşağıdaki kodu ekleyin:

[!code-csharp[Query the tree for the arguments to Main](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#8 "Query the tree for the arguments to Main")]

İlk deyim, önceki örnekteki <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantNodes%2A> yle aynı parametreyi bulmak için bir LINQ ifadesi ve yöntem kullanır.

Programı çalıştırdığınızda LINQ ifadesinin ağaçta el ile gezinmeyle aynı parametreyi bulduğunu görebilirsiniz.

Örnek, `WriteLine` sözdizimi ağaçlarının geçişi yle ilgili bilgileri görüntülemek için deyimleri kullanır. Ayrıca hata ayıklama altında bitmiş programı çalıştırarak çok daha fazla bilgi edinebilirsiniz. Merhaba dünya programı için oluşturulan sözdizimi ağacının bir parçası olan özellikleri ve yöntemleri daha inceleyebilirsiniz.

## <a name="syntax-walkers"></a>Sözdizimi yürüteçleri

Genellikle sözdizimi ağacında belirli bir türün tüm düğümlerini (örneğin, bir dosyadaki her özellik bildirimini) bulmak istersiniz. <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker?displayProperty=nameWithType> Sınıfı genişleterek ve <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor.VisitPropertyDeclaration(Microsoft.CodeAnalysis.CSharp.Syntax.PropertyDeclarationSyntax)> yöntemi geçersiz kılarak, her özellik bildirimini bir sözdizimi ağacında yapısını önceden bilmeden işlersiniz. <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker>özyinelemeli bir <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor> düğüm ve her çocuğunu ziyaret eden özel bir türdür.

Bu örnek, <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> sözdizimi ağacını inceleyen bir uygulama uygular. Ad alanı `using` almayan `System` yönergeleri toplar.

Yeni bir C# **Tek Başına Kod Analizi Aracı** projesi oluşturun; adı "**SyntaxWalker**."

Bu örneğin bitmiş kodunu [GitHub depomuzda](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/SyntaxQuickStart)görebilirsiniz. GitHub'daki örnek, bu öğreticide açıklanan her iki projeyi de içerir.

Önceki örnekte olduğu gibi, çözümleyeceğiniz programın metnini tutmak için bir dize sabiti tanımlayabilirsiniz:

[!code-csharp[Define the code text to analyzer](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/Program.cs#1 "Define the program text to analyze")]

Bu kaynak `using` metin dört farklı konuma dağılmış yönergeleri içerir: dosya düzeyi, üst düzey ad alanında ve iç içe geçen iki ad alanında. Bu örnek, <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> sınıfı sorgu kodu için kullanmak için temel bir senaryoyu vurgular. Bildirimleri kullanarak bulmak için kök sözdizimi ağacında her düğümü ziyaret etmek hantal olacaktır. Bunun yerine, türetilmiş bir sınıf oluşturur sunuz ve yalnızca ağaçtaki geçerli düğüm bir yönerge olduğunda çağrılan yöntemi geçersiz kılarsınız. Ziyaretçiniz diğer düğüm türleri üzerinde herhangi bir çalışma yapmaz. Bu tek `using` yöntem, ifadelerin her birini inceler ve `System` ad alanında olmayan ad alanlarının bir koleksiyon oluşturur. Tüm <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> `using` ifadeleri inceleyen, sadece `using` ifadeleri inceleyen bir yapı oluşturursunuz.

Artık program metnini tanımladığınıza göre, bir `SyntaxTree` oluşturmanız ve bu ağacın kökünü almanız gerekir:

[!code-csharp[Create the Syntax tree and access the root](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/Program.cs#2 "Create the Syntax tree and access the root node.")]

Ardından, yeni bir sınıf oluşturun. Visual Studio'da **Project** > **Add New Item'i**seçin. Yeni **Öğe Ekle** iletişim kutusunda dosya adı olarak *UsingCollector.cs.*

`UsingCollector` Sınıfta `using` ziyaretçi işlevselliğini uygularsınız. `UsingCollector` Sınıfı' ndan <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker>türeterek başlayın.

[!code-csharp[Declare the base class for the using collector](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/UsingCollector.cs#3 "Declare the base class for the UsingCollector")]

Topladığınız ad alanı düğümlerini tutmak için depolama alanına ihtiyacınız vardır.  Sınıfta herkese açık salt okunur `UsingCollector` bir özelliği bildirin; bulduğunuz düğümleri depolamak için bu değişkeni <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax> kullanırsınız:

[!code-csharp[Declare storage for the using syntax nodes](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/UsingCollector.cs#4 "Declare storage for the using syntax nodes")]

Taban sınıf, <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> sözdizimi ağacındaki her düğümü ziyaret etme mantığını uygular. Türemiş sınıf, ilgilendiğiniz belirli düğümler için çağrılan yöntemleri geçersiz kılar. Bu durumda, herhangi bir `using` direktifle ilgileniyorsunuz. Bu, <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor.VisitUsingDirective(Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax)> yöntemi geçersiz kılmanız gerektiği anlamına gelir. Bu yöntemin tek bağımsız <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax?displayProperty=nameWithType> değişkeni bir nesnedir. Bu ziyaretçileri kullanmak için önemli bir avantajdır: zaten belirli düğüm türüne döküm argümanlar ile geçersiz kılınan yöntemleri arayın. Sınıfın, <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax?displayProperty=nameWithType> içe <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax.Name> aktarılan ad alanının adını depolayan bir özelliği vardır. Bu bir. <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax?displayProperty=nameWithType> Geçersiz kılmaya <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor.VisitUsingDirective(Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax)> aşağıdaki kodu ekleyin:

[!code-csharp[Examine using nodes for the System namespace](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/UsingCollector.cs#5 "Examine all using nodes for the System namespace.")]

Önceki örnekte olduğu gibi, bu yöntemin `WriteLine` anlaşılmasına yardımcı olmak için çeşitli ifadeler eklediniz. Ne zaman çağrıldığını ve her seferinde hangi bağımsız değişkenlerin aktarılabileceğini görebilirsiniz.

Son olarak, oluşturmak için iki kod `UsingCollector` satırı eklemeniz ve tüm deyimleri `using` toplayarak kök düğümünü ziyaret etmesini zorunda kalmanız gerekir. Ardından, toplayıcınızın bulduğu `foreach` tüm `using` ifadeleri görüntülemek için bir döngü ekleyin:

[!code-csharp[Create the UsingCollector and visit the root node.](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/Program.cs#6 "Create the UsingCollector and visit the root node.")]

Programı derle ve çalıştır. Aşağıdaki çıktıyı görmeniz gerekir:

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

Tebrikler! C# kaynak kodunda belirli c# deyimleri ve bildirimleri bulmak için **Sözdizimi API'sini** kullandınız.
