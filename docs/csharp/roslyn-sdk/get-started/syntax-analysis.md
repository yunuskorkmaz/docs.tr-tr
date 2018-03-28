---
title: Sözdizimi analiz (Roslyn API) ile çalışmaya başlama
description: Çapraz geçiş yapma, sorgulama ve sözdizimi ağaçları taramasını giriş.
author: billwagner
ms.author: wiwagn
ms.date: 02/05/2018
ms.topic: conceptual
ms.prod: .net
ms.technology: devlang-csharp
ms.custom: mvc
ms.openlocfilehash: 90d6542122dd8c579c63f5f003441ce63a7ca5e9
ms.sourcegitcommit: 935d5267c44f9bce801468ef95f44572f1417e8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/28/2018
---
# <a name="get-started-with-syntax-analysis"></a>Sözdizimi Analizi ile çalışmaya başlama

Bu öğreticide, ele alacağız **sözdizimi API**. Sözdizimi API bir C# veya Visual Basic programı açıklayan veri yapılarını erişim sağlar. Bu veri yapılarını bunlar tam olarak herhangi bir boyuttaki herhangi bir programı gösterebilir yeterli ayrıntı vardır. Bu yapıları derlemek ve düzgün çalışmasına tam programları tanımlayabilirsiniz. Bunları, düzenleyicide yazarken ayrıca tamamlanmamış programlar açıklayabilirsiniz.

Bu zengin ifade etkinleştirmek için söz dizimi API yapmak API'ları ve veri yapıları mutlaka karmaşıktır. Veri yapısı gibi tipik "Hello World" programın göründüğünü ile başlayalım:

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

Önceki programının metni arayın. Tanıdık öğeleri farkındayız. Tek bir kaynak dosyası, tüm metni temsil veya **derleme birim**. Bu kaynak dosyasının ilk üç satır **yönergeleri kullanarak**. Kalan kaynağı bulunan bir **ad alanı bildiriminin**. Bir alt ad alanı bildirimini içerir **sınıf bildiriminin**. Sınıf bildirimi içeriyor **yöntem bildirimi**.

Sözdizimi API derleme birimini temsil eden kök ile bir ağaç yapısı oluşturur. Ağaçtaki düğümler temsil kullanma yönergeleri, ad alanı bildirimi ve diğer tüm öğeleri programının. Ağaç yapısını aşağıya doğru en düşük düzey devam eder: "Hello World!" dize olan bir **dize değişmez değer belirteci** olan bir alt bir **bağımsız değişkeni**. Sözdizimi API programı yapısını erişim sağlar. Belirli bir kod yöntemler için sorgu kodu anlamak için tüm ağaç yol ve varolan ağacı değiştirerek yeni ağaçları oluşturun.

Bu kısa bir açıklama tür bilgileri sözdizimi API'si kullanılarak erişilebilir genel bir bakış sağlar. Sözdizimi API tanıdık kodu tanımlayan bir resmi API yapıları fazlasını C# ' dan bilmeniz doğrudur. Özelliklerinin kodu satır sonları, boşluk ve girintileme dahil olmak üzere nasıl biçimlendirilmiş hakkında bilgi içerir. Bu bilgileri kullanarak, yazılı kod ve İnsan programlayıcıların okuma veya Derleyici tam olarak gösterebilir. Bu yapı kullanarak iç anlamlı bir düzeyde kaynak kodu ile etkileşim sağlar. Artık metin dizelerini, ancak bir C# programı yapısını temsil eden veri değil.

Başlamak için yüklemek gerekecektir **.NET derleyici Platform SDK**:

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

## <a name="understanding-syntax-trees"></a>Sözdizimi ağacı anlama

C# kod yapısını herhangi analize sözdizimi API kullanın. **Sözdizimi API** ayrıştırıcıları, sözdizimi ağaçları ve analiz etme ve sözdizimi ağaçları oluşturmak için utilities kullanıma sunar. Nasıl belirli söz dizimi öğeleri için kod arama veya bir programın kodunu okuma değil.

Sözdizimi ağacı, C# ve Visual Basic programları anlamak için C# ve Visual Basic derleyicileri tarafından kullanılan bir veri yapısıdır. Sözdizimi ağacı proje yerleşik veya F5 Geliştirici isabetler çalışır aynı ayrıştırıcı tarafından oluşturulur. Sözdizimi ağacı dili tam uygunluğunu; yine de sahip istiyor musunuz? Her bir kod dosyasındaki bilgileri bitini ağacında temsil edilir. Sözdizimi ağacı için metin yazma ayrıştırıldığında tam özgün metin oluşmazsa. Sözdizimi ağacı da olduğu **değişmez**; bir söz dizimi oluşturulduktan sonra ağaç hiçbir zaman değiştirilebilir. Ağaçları tüketicileri, hiçbir zaman veri değişikliklerini bilerek kilitleri ya da diğer eşzamanlılık ölçüleri olmadan birden çok iş parçacığı ağaçları analiz edebilirsiniz. Varolan bir ağacında değiştirme sonucu olan yeni ağaçları oluşturmak için API'ler kullanabilirsiniz.

Sözdizimi ağacı dört birincil yapı taşlarını şunlardır:

* <xref:Microsoft.CodeAnalysis.SyntaxTree?displayProperty=nameWithType> Sınıfı, bir örneği temsil eden tüm ayrıştırma ağacı. <xref:Microsoft.CodeAnalysis.SyntaxTree> dile özgü türevleri sahip soyut bir sınıftır. Ayrıştırma yöntemlerini kullanın <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxTree?displayProperty=nameWithType> (veya <xref:Microsoft.CodeAnalysis.VisualBasic.VisualBasicSyntaxTree?displayProperty=nameWithType>) C# ve vb metnin ayrıştırılacak sınıfı
* <xref:Microsoft.CodeAnalysis.SyntaxNode?displayProperty=nameWithType> Hangi örneklerini bildirimleri, deyimleri, yan tümceleri ve ifadeler gibi söz dizimi yapıları temsil eden sınıf.
* <xref:Microsoft.CodeAnalysis.SyntaxToken?displayProperty=nameWithType> Yapısı, ayrı anahtar sözcüğü, tanımlayıcı, operatör ya da noktalama temsil eder.
* Ve son <xref:Microsoft.CodeAnalysis.SyntaxTrivia?displayProperty=nameWithType> belirteçleri, önişleme yönergeleri ve yorumları arasındaki boşluk gibi bilgileri sözdizimsel olarak Önemsiz bitleri temsil eden yapısı.

Trivia, belirteçleri ve düğümler hiyerarşik olarak tamamen her şeyi bir Visual Basic veya C# kod parçasını temsil eden bir ağaç oluşturmak için oluşur. Bu yapı kullanarak görebilirsiniz **sözdizimi Görselleştirici** penceresi. Visual Studio'da, **Görünüm** > **diğer pencereler** > **sözdizimi Görselleştirici**. Örneğin, önceki C# kaynak dosyası incelenmesi kullanarak **sözdizimi Görselleştirici** gibi aşağıdaki şekilde görünür:

**SyntaxNode**: mavi | **SyntaxToken**: yeşil | **SyntaxTrivia**: kırmızı ![C# kod dosyası](media/walkthrough-csharp-syntax-figure1.png)

Bu ağaç yapısı giderek deyimi, ifade, belirteç veya boşluk bit kod dosyasında bulabilirsiniz.

Herhangi bir şey sözdizimi API'lerini kullanarak bir kod dosyasında bulabilirsiniz, ancak çoğu senaryoda küçük kod parçacıkları inceleyerek ya da belirli ifadeleri veya parçaları için arama içerir. Tipik gösterisini izleyin iki örnek kodu ya da tek deyimleri arayın yapısını göz atmak için kullanır.

## <a name="traversing-trees"></a>Ağaçlarında geçiş yapma

İki yolla bir sözdizimi ağacında düğümlerin inceleyebilirsiniz. Her düğüm incelemek için ağacı gezme veya belirli öğeleri veya düğümler için sorgulayabilirsiniz.

### <a name="manual-traversal"></a>El ile geçişi

Bu örnek için tamamlanmış kod görebilirsiniz [GitHub depomuzda](https://github.com/dotnet/docs/tree/master/samples/csharp/roslyn-sdk/SyntaxQuickStart).

> [!NOTE]
> Sözdizimi ağacı türleri devralma programı farklı konumlarda geçerli farklı söz dizimi öğeleri tanımlamak için kullanın. Genellikle bu API'leri kullanarak atama özellikleri veya belirli türetilmiş türler için koleksiyon üyeleri anlamına gelir. Aşağıdaki örneklerde, atama ve atamalar açıkça yazılan değişkenler kullanılarak ayrı deyim ' dir. Dönüş türleri API ve çalışma zamanı türü, döndürülen nesnelerin görmek için kodu okuyabilir. Uygulamada, incelenmesi nesnelerin türünü tanımlamak için API adları kullanır ve örtük olarak yazılan değişkenler kullanmak için daha yaygın bir durumdur.

Yeni C# oluşturma **tek başına kod analizi aracı** proje:

* Visual Studio'da, **dosya** > **yeni** > **proje** yeni proje iletişim kutusu görüntülemek için.
* Altında **Visual C#** > **genişletilebilirlik**, seçin **tek başına kod analizi aracı**.
* Projenizin adı "**SyntaxTreeManualTraversal**" ve Tamam'ı tıklatın.

Temel "Hello World!" analiz etmeyi deneyeceğimiz daha önce gösterilen programı.
Bir sabit olarak Hello World program için metni ekleyin, `Program` sınıfı:

[!code-csharp[Declare the program text](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#1 "Declare a constant string for the program text to analyze")]

Ardından, oluşturmak için aşağıdaki kodu ekleyin **sözdizimi ağacı** kodunu metin `programText` sabit.  Aşağıdaki satırı ekleyin, `Main` yöntemi:

[!code-csharp[Create the tree](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#2 "Create the syntax tree")]

Bu iki satırlar ağaç oluşturup ağacı kök düğümü alabilirsiniz. Ağaç düğümünde şimdi inceleyebilirsiniz. Şu satırları ekleyin, `Main` yöntemi ağacında kök düğümünün özelliklerini görüntülemek için:

[!code-csharp[Examine the root node](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#3 "Examine the root node")]

Kodunuzu bu ağacındaki kök düğümü hakkında buldu görmek için uygulamayı çalıştırın.

Genellikle, kodu hakkında bilgi edinmek için ağacı gezme. Bu örnekte, API keşfetmek için bilmeniz kodunu analiz etme. İlk üyesi incelemek için aşağıdaki kodu ekleyin `root` düğümü:

[!code-csharp[Find the first member](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#4 "Find the first member")]

Bu üye olduğu bir <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NamespaceDeclarationSyntax?displayProperty=nameWithType>. Kapsamındaki her şeyi temsil eden `namespace HelloWorld` bildirimi. Hangi düğümleri içinde bildirilen incelemek için aşağıdaki kodu ekleyin `HelloWorld` ad alanı:

[!code-csharp[Find the class declaration](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#5 "Find the class declaration")]

Ne öğrendiğinize görmek için programı çalıştırın.

Bildirim bildiğinize göre olan bir <xref:Microsoft.CodeAnalysis.CSharp.Syntax.ClassDeclarationSyntax?displayProperty=nameWithType>, sınıf bildiriminin incelemek için bu türdeki yeni bir değişken bildirin. Bu sınıf, yalnızca bir üye içerdiğinden: `Main` yöntemi. Bulmak için aşağıdaki kodu ekleyin `Main` yöntemi ve hangisine bir <xref:Microsoft.CodeAnalysis.CSharp.Syntax.MethodDeclarationSyntax?displayProperty=nameWithType>.

[!code-csharp[Find the main declaration](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#6 "Find the main declaration")]

Yöntem bildirimi düğüm tüm söz dizimi yöntemi hakkında bilgi içerir. Dönüş türünü şimdi görüntülemek `Main` yöntemi, sayı ve bağımsız değişken türleri ve yönteminin gövdesi metin. Aşağıdaki kodu ekleyin:

[!code-csharp[Examine the syntax of the main method](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#7 "Display information about the main method")]

Bu programla ilgili tüm bilgileri, keşfettiniz görmek için programı çalıştırın:

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

Ağaçları çapraz geçiş yapan yanı sıra üzerinde tanımlanan sorgu yöntemleri kullanarak sözdizimi ağacı de keşfedebilirsiniz <xref:Microsoft.CodeAnalysis.SyntaxNode?displayProperty=nameWithType>. Bu yöntemleri ile XPath tanıdık bir kişiye hemen bilgi sahibi olmanız gerekir. Hızlı bir şekilde bir ağaç öğeleri bulmak için bu yöntemleri LINQ ile kullanabilirsiniz. <xref:Microsoft.CodeAnalysis.SyntaxNode> Sorgu yöntemleri gibi sahip <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantNodes%2A>, <xref:Microsoft.CodeAnalysis.SyntaxNode.AncestorsAndSelf%2A> ve <xref:Microsoft.CodeAnalysis.SyntaxNode.ChildNodes%2A>.

Bağımsız değişkeni bulmak için bu sorguyu yöntemleri kullanabilir `Main` ağaç gezinme alternatif olarak yöntemi. ' In altına aşağıdaki kodu ekleyin, `Main` yöntemi:

[!code-csharp[Query the tree for the arguments to Main](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#8 "Query the tree for the arguments to Main")]

İlk ifade LINQ ifadesi kullanır ve <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantNodes%2A> yöntemi önceki örnektekiyle aynı parametre bulun.

Programını çalıştırın ve LINQ ifadesi el ile ağaç gezinme olarak aynı parametre bulunan görebilirsiniz.

Örnek kullanır `WriteLine` geçiş gibi söz dizimi ağaçları hakkındaki bilgileri görüntülemek için deyimleri. Ayrıca, hata ayıklayıcı altında tamamlanmış programını çalıştırarak çok daha öğrenebilirsiniz. Hello world program için oluşturulan sözdizimi ağacının bir parçası olan yöntemleri ve özellikleri birkaçını inceleyebilirsiniz.

## <a name="syntax-walkers"></a>Sözdizimi walkers

Genellikle, örneğin, her özellik bildirimi bir dosyada bir sözdizimi ağacında belirli bir türdeki tüm düğümleri bulmak istediğiniz. Genişletme tarafından <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker?displayProperty=nameWithType> sınıfı ve geçersiz kılma <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor.VisitPropertyDeclaration(Microsoft.CodeAnalysis.CSharp.Syntax.PropertyDeclarationSyntax)> yöntemi, işlem her özellik bildirimi sözdizimi ağacında yapısını önceden bilmeden. <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> belirli bir tür olduğundan <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor> , yinelemeli bir düğüme ve her alt ziyaret eder.

Bu örnek uygulayan bir <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> sözdizimi ağacı inceler. Topladığı `using` alma olmayan bulduğu yönergeleri bir `System` ad alanı.

Yeni C# oluşturma **tek başına kod analizi aracı** proje; adlandırın "**SyntaxWalker**."

Bu örnek için tamamlanmış kod görebilirsiniz [GitHub depomuzda](https://github.com/dotnet/docs/tree/master/samples/csharp/roslyn-sdk/SyntaxQuickStart). Örnek github'daki Bu öğreticide açıklanan her iki proje içerir.

Önceki örnekte olduğu gibi analiz etmeyi deneyeceğimiz program metnin tutmak için bir dize sabitine tanımlayabilirsiniz:

[!code-csharp[Define the code text to analyzer](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/Program.cs#1 "Define the program text to analyze")]

Bu kaynak metni içeren `using` yönergeleri dağılmış dört farklı konumlar arasında: dosya düzeyinde, en üst düzey ad ve iki iç içe geçmiş ad alanı. Bu örneği kullanmak için bir çekirdek senaryo vurgular <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> sorgu koduna sınıfı. Her düğüm bildirimlerini kullanarak bulmak için kök sözdizimi ağacındaki ziyaret etmek için sıkıcı olabilir. Bunun yerine, türetilmiş bir sınıf oluşturun ve yalnızca geçerli düğüm ağacında kullanarak bir olduğunda çağrılan yöntemi yok sayın yönergesi. Başka bir düğüm türleri üzerinde herhangi bir iş, ziyaretçi yapmaz. Bu tek bir yöntem her biri inceler `using` deyimleri ve olmayan ad alanlarını koleksiyonu derlemeler `System` ad alanı. Oluşturacağınız bir <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> tüm inceler `using` ancak deyimleri `using` deyimleri.

Program metin tanımladığınız, oluşturmak gereken bir `SyntaxTree` ve o Ağaç kökü alın:

[!code-csharp[Create the Syntax tree and access the root](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/Program.cs#2 "Create the Syntax tree and access the root node.")]

Ardından, yeni bir sınıf oluşturun. Visual Studio'da, **proje** > **Yeni Öğe Ekle**. İçinde **Yeni Öğe Ekle** iletişim türü *UsingCollector.cs* dosya adı olarak.

Uygulamanız `using` ziyaretçi işlevindeki `UsingCollector` sınıfı. Başlangıç yaparak `UsingCollector` sınıf türetin <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker>.

[!code-csharp[Declare the base class for the using collector](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/UsingCollector.cs#3 "Declare the base class for the UsingCollector")]

Toplama ad alanı düğümlerini tutmak için depolama gerekir.  Genel bir salt okunur özelliği bildirme `UsingCollector` sınıfı; depolamak için bu değişkeni kullanın <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax> bulduğunuz düğümleri:

[!code-csharp[Declare storage for the using syntax nodes](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/UsingCollector.cs#4 "Declare storage for the using syntax nodes")]

Taban sınıfı <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> sözdizimi ağacı içindeki her bir düğümün ziyaret etmek için mantığı uygular. Türetilmiş sınıf ilgilendiğiniz belirli düğümler için adlı yöntemlerini geçersiz kılar. Bu durumda, birinde ilgilendiğiniz `using` yönergesi. Geçersiz kılması gerekir anlamına <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor.VisitUsingDirective(Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax)> yöntemi. Bu yönteme bir bağımsız değişken bir <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax?displayProperty=nameWithType> nesnesi. Ziyaretçilerin kullanmanın önemli bir avantajı olan: Bunlar zaten belirli düğüm türe bağımsız değişkenlerle geçersiz kılınan yöntemlerini çağırın. <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax?displayProperty=nameWithType> Sınıfına sahip bir <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax.Name> içeri aktarılan ad depolar özelliği. Bu bir <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax?displayProperty=nameWithType>. Aşağıdaki kodu ekleyin <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor.VisitUsingDirective(Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax)> geçersiz kıl:

[!code-csharp[Examine using nodes for the System namespace](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/UsingCollector.cs#5 "Examine all using nodes for the System namespace.")]

Önceki örnekle çeşitli eklediğiniz gibi `WriteLine` bu yöntem bir anlayış de yardımcı olmak için deyimleri. Ne zaman denir ve hangi bağımsız değişkenler için her zaman geçirilir görebilirsiniz.

Son olarak, iki oluşturmak için kod satırı eklemeniz gerekir `UsingCollector` ve tüm toplama kök düğümünü ziyaret `using` deyimleri. Ardından, ekleyin bir `foreach` tümünü görüntülemek için döngü `using` deyimleri toplayıcınız bulundu:

[!code-csharp[Create the UsingCollector and visit the root node.](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/Program.cs#6 "Create the UsingCollector and visit the root node.")]

Derleme ve programı çalıştırın. Şu çıktı görmeniz gerekir:

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

Tebrikler! Kullandığınız **sözdizimi API** belirli türdeki C# bulmaya deyimleri ve bildirimleri C# kaynak kodu.
