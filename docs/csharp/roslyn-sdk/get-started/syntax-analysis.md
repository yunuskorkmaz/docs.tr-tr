---
title: Söz dizimi analizi (Roslyn API'leri) ile çalışmaya başlama
description: Geçiş, sorgulama ve söz dizimi ağacı walking giriş.
ms.date: 02/05/2018
ms.custom: mvc
ms.openlocfilehash: e377fe10e094e958627c3503fc39b7e2d02b3d7a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61706627"
---
# <a name="get-started-with-syntax-analysis"></a>Söz dizimi Analizi ile çalışmaya başlama

Bu öğreticide, hakkında bilgi edineceksiniz **söz dizimi API**. API söz dizimi bir C# veya Visual Basic programını açıklayan veri yapılarını erişim sağlar. Bu veri yapıları, tam olarak her boyutta herhangi bir programı gösterebilir yeterli ayrıntı sahip. Bu yapılar, derleyin ve doğru bir şekilde çalışması eksiksiz programlar tanımlayabilirsiniz. Düzenleyicide, yazarken tamamlanmamış Programlar'ne de tanımlayabilirsiniz.

Bu zengin ifade etkinleştirmek için söz dizimi API'nizi API ve veri yapıları karmaşık olması gerekmez. Veri yapısı tipik bir "Merhaba Dünya" program için nasıl göründüğüne ile başlayalım:

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

Önceki program metin bakın. Size tanıdık öğeleri kabul eder. Tek bir kaynak dosyası, tüm metni temsil eder veya **derleme biriminde**. Bu kaynak dosyanın ilk üç satırlar **yönergeleri kullanarak**. Kalan kaynağı bulunan bir **ad alanı bildirimi**. Alt ad alanı bildirimi içeren **sınıf bildiriminin**. Bir sınıf bildirimi içeren **yöntem bildiriminde**.

Söz dizimi API derleme biriminde temsil eden kök ile bir ağaç yapısı oluşturur. Ağaçtaki düğümler temsil kullanma yönergeleri, ad alanı bildirimi ve programın diğer tüm öğeleri. En düşük düzey aşağı ağaç yapısını devam: "Hello World!" dizesi olan bir **dize değişmez değer belirteci** diğer bir deyişle bir alt bir **bağımsız değişken**. Söz dizimi API programı yapısını erişim sağlar. Belirli bir kod yöntemleri için sorgulayabilirsiniz kodu anlamak için tüm ağaçta yürüyebilir ve mevcut ağaca değiştirerek yeni bir ağaç oluşturun.

Bu kısa bir açıklama söz dizimi API kullanılarak erişilebilen bilgi türünü genel bir bakış sağlar. Söz dizimi API'si tanıdık kodu tanımlayan bir biçimsel API, yapıları daha C# ' tan bilmeniz doğrudur. Tüm özelliklerini kod satır sonları, boşluk ve girintileme dahil olmak üzere nasıl biçimlendirildiğini hakkında bilgi içerir. Bu bilgileri kullanarak, yazılan kod ve İnsan programlayıcıların kullandığı okuma veya derleyicinin tam olarak gösterebilir. Bu yapı kullanarak derin anlamlı düzeyinde kaynak kodu ile etkileşimde bulunmanızı sağlar. Artık metin dizelerini, ancak bir C# programı yapısını temsil eden veri değil.

Başlamak için yüklemeniz gerekecektir **.NET derleyici Platformu SDK'sı**:

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

## <a name="understanding-syntax-trees"></a>Sözdizimi ağacı anlama

Söz dizimi API herhangi bir C# kodunun yapısını çözümlemesi için kullanırsınız. **Söz dizimi API** Çözümleyicileri, söz dizimi ağacı ve analiz etme ve söz dizimi ağacı oluşturmak için yardımcı programlar kullanıma sunar. Bu, belirli bir söz dizimi öğeleri için kod arama veya bir program kodunu okuma nasıl olur.

Sözdizimi ağacı, C# ve Visual Basic programlar anlamak için C# ve Visual Basic derleyiciler tarafından kullanılan bir veri yapısıdır. Söz dizimi ağacı bir proje veya F5'e bir geliştirici İsabetleri çalıştırır aynı ayrıştırıcı tarafından oluşturulur. Sözdizimi ağacı tam uygunluklu dilini sahip; bir kod dosyası bilgilerinin her bit ağacında temsil edilir. Sözdizimi ağacı için metin yazma ayrıştırıldığında küpte tam orijinal metni yeniden oluşturur. Söz dizimi ağacı ayrıca, **değişmez**; oluşturulan bir söz dizimi ağacı hiçbir zaman değiştirilebilir. Ağaçları tüketicilerinin ağaçları kilit veya diğer eşzamanlılık ölçüler olmadan birden çok iş parçacığı üzerinde hiçbir zaman veri değişikliği bilerek çözümleyebilirsiniz. API'leri, var olan bir ağaç değiştirme sonucu olan yeni ağacı oluşturmak için kullanabilirsiniz.

Sözdizimi ağacı dört birincil yapı taşları şunlardır:

* <xref:Microsoft.CodeAnalysis.SyntaxTree?displayProperty=nameWithType> Sınıfının bir örneğini temsil eden bir tüm ayrıştırma ağacı. <xref:Microsoft.CodeAnalysis.SyntaxTree> dile özgü türevleri sahip bir soyut sınıftır. Ayrıştırma yöntemlerinin kullandığınız <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxTree?displayProperty=nameWithType> (veya <xref:Microsoft.CodeAnalysis.VisualBasic.VisualBasicSyntaxTree?displayProperty=nameWithType>) C# veya vb metni ayrıştırılamıyor sınıfı
* <xref:Microsoft.CodeAnalysis.SyntaxNode?displayProperty=nameWithType> Örnekleri, bildirimleri, deyimler, yan tümceleri ve ifadeler gibi bir söz dizimi yapıları temsil eden sınıf.
* <xref:Microsoft.CodeAnalysis.SyntaxToken?displayProperty=nameWithType> Yapısı, tek tek anahtar sözcük, tanımlayıcı, işleci veya noktalama temsil eder.
* Ve son olarak <xref:Microsoft.CodeAnalysis.SyntaxTrivia?displayProperty=nameWithType> belirteçleri, ön işleme yönergeleri ve yorumları arasındaki boşluk gibi bilgileri sözdizimsel olarak anlamsız bitlerini gösteren yapısı.

Meraklısına Notlar belirteç ve düğümleri tamamen her şeyi Visual Basic veya C# kod parçasını temsil eden bir ağaç oluşturmak için hiyerarşik olarak oluşur. Bu yapı kullanarak görebilirsiniz **Syntax Visualizer** penceresi. Visual Studio'da **görünümü** > **diğer Windows** > **Syntax Visualizer**. Örneğin, önceki C# kaynak dosyası incelenirken kullanarak **Syntax Visualizer** gibi aşağıdaki şekilde görünüyor:

**SyntaxNode**: Mavi | **SyntaxToken**: Yeşil | **SyntaxTrivia**: Kırmızı ![ C# kod dosyası](media/walkthrough-csharp-syntax-figure1.png)

Bu ağaç yapısı giderek deyim, ifade, belirteci veya boşluk biti bir kod dosyasında bulabilirsiniz.

Herhangi bir şey söz dizimi API'lerini kullanarak bir kod dosyasında bulabilirsiniz, ancak çoğu senaryoda küçük kod parçacıkları inceleme veya arama belirli deyimleri veya parçaları içerir. Tipik show izleyen iki örnek kodu veya arama için tek deyimler yapısını göz atmak için kullanır.

## <a name="traversing-trees"></a>Geçiş ağaçları

İki yolla bir sözdizimi ağacında düğümlerin inceleyebilirsiniz. Her düğüm incelemek için ağacı gezme veya belirli öğeleri veya düğümleri için sorgulayabilirsiniz.

### <a name="manual-traversal"></a>El ile geçişi

Bu örnek için tamamlanan kodu gördüğünüz [GitHub depomuzda](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/SyntaxQuickStart).

> [!NOTE]
> Sözdizimi ağacı türleri devralma programı farklı konumlarda geçerli olan farklı bir sözdizimi öğeleri tanımlamak için kullanın. Genellikle bu API'leri kullanarak, atama özellikleri veya belirli türetilen türler için koleksiyon üyelerini anlamına gelir. Aşağıdaki örneklerde, atama ve atamaları açıkça yazılmış değişkenler kullanarak ayrı deyim olan. API dönüş türleri ve döndürülen nesnelerin çalışma zamanı türü görmek için kodu okuyabilirsiniz. Uygulamada, türü örtük olarak belirlenmiş değişkenlerin ve incelenmekte olan nesnelerin türünü tanımlamak için API adlara dayalı daha yaygındır.

Yeni C# oluşturma **tek başına kod analizi aracı** proje:

* Visual Studio'da **dosya** > **yeni** > **proje** yeni proje iletişim kutusu görüntülenecek.
* Altında **Visual C#** > **genişletilebilirlik**, seçin **tek başına kod analizi aracı**.
* Projenizi adlandırın "**SyntaxTreeManualTraversal**" ve Tamam'a tıklayın.

Temel "Hello World!" analiz etmek için gideceğinizi daha önce gösterilen programı.
İçinde bir sabit olarak Hello World programı için metin ekleyin, `Program` sınıfı:

[!code-csharp[Declare the program text](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#1 "Declare a constant string for the program text to analyze")]

Ardından, oluşturmak için aşağıdaki kodu ekleyin **söz dizimi ağacı** kod metinde `programText` sabit.  Aşağıdaki satırı ekleyin, `Main` yöntemi:

[!code-csharp[Create the tree](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#2 "Create the syntax tree")]

Bu iki satırı ağacı oluşturmak ve o ağaç kök düğümü alınamıyor. Şimdi Ağaçtaki düğümler inceleyebilirsiniz. Bu satırları ekleyin, `Main` yöntemi ağaç kök düğümü özelliklerinin bazılarını görüntülemek için:

[!code-csharp[Examine the root node](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#3 "Examine the root node")]

Kodunuz hakkında bu ağaç kök düğümü bulunduğundan görmek için uygulamayı çalıştırın.

Genellikle, kod hakkında bilgi edinmek için ağacı gezme. Bu örnekte, API'leri keşfedin bildiğiniz kodu çözümlediğiniz. İlk üye incelemek için aşağıdaki kodu ekleyin `root` düğüm:

[!code-csharp[Find the first member](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#4 "Find the first member")]

Bu üye bir <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NamespaceDeclarationSyntax?displayProperty=nameWithType>. Her şeyi kapsamı temsil eden `namespace HelloWorld` bildirimi. Hangi düğümleri içinde bildirilen incelemek için aşağıdaki kodu ekleyin `HelloWorld` ad alanı:

[!code-csharp[Find the class declaration](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#5 "Find the class declaration")]

Öğrendiklerinizi görmek için programı çalıştırın.

Bildirimi öğrendiğinize göre olan bir <xref:Microsoft.CodeAnalysis.CSharp.Syntax.ClassDeclarationSyntax?displayProperty=nameWithType>, sınıf bildiriminin incelemek için bu türdeki yeni bir değişken bildirir. Bu sınıf yalnızca bir üye içeriyor: `Main` yöntemi. Bulmak için aşağıdaki kodu ekleyin `Main` yöntemi ve bunu bir <xref:Microsoft.CodeAnalysis.CSharp.Syntax.MethodDeclarationSyntax?displayProperty=nameWithType>.

[!code-csharp[Find the main declaration](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#6 "Find the main declaration")]

Yöntemi bildirim düğümü yöntemi söz dizimi tüm bilgileri içerir. Şimdi dönüş türünü görüntüle `Main` yöntemi, sayı ve bağımsız değişken türlerinin yanı sıra, yöntemin gövde metni. Aşağıdaki kodu ekleyin:

[!code-csharp[Examine the syntax of the main method](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#7 "Display information about the main method")]

Bu program hakkındaki tüm bilgileri keşfettiğinize göre görmek için bir programı çalıştır:

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

Ağaçlarında geçiş yapma ek olarak, söz dizimi ağacı tanımlanan sorgu yöntemlerini kullanarak da keşfedebilirsiniz <xref:Microsoft.CodeAnalysis.SyntaxNode?displayProperty=nameWithType>. Bu yöntemleri herkes XPath ile tanıdık hemen biliyor olmanız gerekir. Hızlı bir şekilde bir ağaç şeyi bulmak için bu yöntemleri LINQ ile kullanabilirsiniz. <xref:Microsoft.CodeAnalysis.SyntaxNode> Sorgu yöntemleri gibi sahip <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantNodes%2A>, <xref:Microsoft.CodeAnalysis.SyntaxNode.AncestorsAndSelf%2A> ve <xref:Microsoft.CodeAnalysis.SyntaxNode.ChildNodes%2A>.

Bu sorgu yöntemleri bağımsız değişkeni bulmak için kullanabileceğiniz `Main` ağacında doğru alternatif olarak yöntemi. ' In altına aşağıdaki kodu ekleyin, `Main` yöntemi:

[!code-csharp[Query the tree for the arguments to Main](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#8 "Query the tree for the arguments to Main")]

İlk deyim bir LINQ ifadesini kullanır ve <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantNodes%2A> önceki örnektekiyle aynı parametre bulmak için yöntemi.

Programı çalıştırın ve LINQ ifade ağacında el ile doğru olarak aynı parametre bulundu görebilirsiniz.

Örnek kullanır `WriteLine` deyimleri, geçiş söz dizimi ağacı hakkında bilgi görüntülemek için. Ayrıca, hata ayıklayıcısı altında tamamlanmış program çalıştırarak çok daha fazlasını öğrenebilirsiniz. Daha fazla özellik ve hello world programı için oluşturulan söz dizimi ağacı parçası olan yöntem inceleyebilirsiniz.

## <a name="syntax-walkers"></a>Söz dizimi yürüyüşçüleri

Genellikle, örneğin, her özellik bildiriminde bir dosyada bir sözdizimi ağacındaki belirli bir türdeki tüm düğümleri bulmak istediğiniz. Genişleterek <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker?displayProperty=nameWithType> sınıf ve geçersiz kılma <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor.VisitPropertyDeclaration(Microsoft.CodeAnalysis.CSharp.Syntax.PropertyDeclarationSyntax)> yöntemi, işlem her bir özellik bildirimi bir sözdizimi ağacında yapısını önceden bilmeden. <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> belirli bir tür olan <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor> , yinelemeli bir düğüm ve her alt ziyaret eder.

Bu örnekte uygulayan bir <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> , söz dizimi ağacı inceler. Topladığı `using` bulduğu yönergeleri, içeri aktarma olmayan bir `System` ad alanı.

Yeni C# oluşturma **tek başına kod analizi aracı** adlandırın; projesi "**SyntaxWalker**."

Bu örnek için tamamlanan kodu gördüğünüz [GitHub depomuzda](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/SyntaxQuickStart). Github'daki örnek bu eğiticide açıklananlarla her iki proje içerir.

Önceki örnekte olduğu gibi metin analiz etmek için gideceğinizi programının tutmak için bir dize sabitine tanımlayabilirsiniz:

[!code-csharp[Define the code text to analyzer](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/Program.cs#1 "Define the program text to analyze")]

Bu kaynak metni içeren `using` yönergeleri dört farklı konumlar arasında dağılmış: dosya düzeyinde, üst düzey ad alanı ve iki iç içe geçmiş ad alanı. Bu örneği kullanmak için bir çekirdek senaryosu vurgulanıyor <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> sorgu kod sınıfı. Her düğüm bildirimi kullanarak bulmak için kök sözdizimi ağacındaki ziyaret etmek için hantal olabilir. Bunun yerine, türetilen bir sınıf oluşturun ve yalnızca geçerli düğüm ağaçta kullanarak bir olduğunda çağrılan yöntemin yönergesi. Ziyaretçi herhangi bir düğüm türleri üzerinde herhangi bir iş yapmaz. Bu tek bir yöntem her biri inceler `using` deyimleri olmayan ad uzayları koleksiyonu oluşturur `System` ad alanı. Oluşturduğunuz bir <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> tüm inceler `using` deyimleri, ancak yalnızca `using` deyimleri.

Program metni tanımladığınıza göre oluşturmak gereken bir `SyntaxTree` ve o ağaç kökünde alın:

[!code-csharp[Create the Syntax tree and access the root](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/Program.cs#2 "Create the Syntax tree and access the root node.")]

Ardından, yeni bir sınıf oluşturun. Visual Studio'da **proje** > **Yeni Öğe Ekle**. İçinde **Yeni Öğe Ekle** iletişim kutusuna *UsingCollector.cs* dosya adı olarak.

Uygulamanız `using` ziyaretçi işlevindeki `UsingCollector` sınıfı. Başlangıç yaparak `UsingCollector` sınıfı türetilen <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker>.

[!code-csharp[Declare the base class for the using collector](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/UsingCollector.cs#3 "Declare the base class for the UsingCollector")]

Toplayacağınızı ad alanı düğümleri tutmak için depolama gerekir.  Genel bir salt okunur özelliği bildirme `UsingCollector` sınıfı; depolamak için bu değişkeni kullanın <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax> bulduğunuz düğümleri:

[!code-csharp[Declare storage for the using syntax nodes](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/UsingCollector.cs#4 "Declare storage for the using syntax nodes")]

Temel sınıfı, <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> sözdizimi ağacı içindeki her bir düğümün ziyaret etmek için mantığını uygular. Türetilmiş sınıf, ilgilendiğiniz belirli düğümler için çağrılan yöntemler geçersiz kılar. Bu durumda, tüm ilginizi çeken `using` yönergesi. Geçersiz kılması gerekir yani <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor.VisitUsingDirective(Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax)> yöntemi. Bu yöntemin bir bağımsız değişken bir <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax?displayProperty=nameWithType> nesne. Ziyaretçi kullanmanın önemli bir avantajı olmasıdır: Bunlar bağımsız değişken zaten belirli düğüm türüne geçersiz kılınan yöntemleri çağırın. <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax?displayProperty=nameWithType> Sınıfında bir <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax.Name> içeri aktarılan ad alanı adını depolar özelliği. Bu bir <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax?displayProperty=nameWithType>. Aşağıdaki kodu ekleyin <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor.VisitUsingDirective(Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax)> geçersiz kıl:

[!code-csharp[Examine using nodes for the System namespace](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/UsingCollector.cs#5 "Examine all using nodes for the System namespace.")]

Önceki örnekte, çeşitli eklediğiniz şekilde `WriteLine` deyimleri, bu yöntem bir anlayış, yardımcı olacak. Ne zaman çağrılır ve her zaman için hangi bağımsız değişkenler geçirilir görebilirsiniz.

Son olarak, iki oluşturmak için kod satırı eklemeniz gerekir `UsingCollector` ve tüm toplama kök düğümünü ziyaret `using` deyimleri. Ardından ekleyin bir `foreach` tümü döngü `using` deyimleri toplayıcınız bulundu:

[!code-csharp[Create the UsingCollector and visit the root node.](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/Program.cs#6 "Create the UsingCollector and visit the root node.")]

Derleme ve programı çalıştırın. Aşağıdaki çıktıyı görmeniz gerekir:

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

Tebrikler! Kullandığınız **söz dizimi API** C# belirli tür bulmak için ifadeleri ve bildirimleri C# kaynak kodu.
