---
title: Sözdizimi dönüşümüne başlayın (Roslyn API'leri)
description: Sözdizimi ağaçlarını gezmeye, sorgulamaya ve yürümeye giriş.
ms.date: 06/01/2018
ms.custom: mvc
ms.openlocfilehash: 5045dca839daba1070b34720e72cc9c4f7b94828
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240616"
---
# <a name="get-started-with-syntax-transformation"></a>Sözdizimi dönüştürmeye başlayın

Bu öğretici, [sözdizimi analiziile başlarken](syntax-analysis.md) incelenen kavramlar ve teknikler üzerine inşa edin ve [anlamsal analiz hızlı başlangıçlara başlayın.](semantic-analysis.md) Henüz yapmadıysanız, bu işe başlamadan önce bu hızlı başlangıcı tamamlamanız gerekir.

Bu hızlı başlangıçta, sözdizimi ağaçları oluşturma ve dönüştürme tekniklerini keşfesunuz. Önceki hızlı başlangıçlarda öğrendiğiniz tekniklerle birlikte, ilk komut satırı yeniden düzenlemenizi oluşturursunuz!

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

## <a name="immutability-and-the-net-compiler-platform"></a>Değişmezlik ve .NET derleyici platformu

**Değişmezlik** .NET derleyici platformunun temel ilkelerinden biridir. Değişmez veri yapıları oluşturulduktan sonra değiştirilemez. Değişmez veri yapıları aynı anda birden fazla tüketici tarafından güvenli bir şekilde paylaşılabilir ve analiz edilebilir. Bir tüketicinin diğerini öngörülemeyen şekillerde etkilemetehlikesi yoktur. Çözümleyicinizin kilitlenmeye veya diğer eşzamanlılık önlemlerine ihtiyacı yoktur. Bu kural sözdizimi ağaçları, derlemeler, semboller, anlamsal modeller ve karşılaştığınız diğer tüm veri yapıları için geçerlidir. API'ler varolan yapıları değiştirmek yerine, eskileri için belirtilen farkları temel alan yeni nesneler oluşturur. Dönüşümleri kullanarak yeni ağaçlar oluşturmak için sözdizimi ağaçlarına bu kavramı uygularsınız.

## <a name="create-and-transform-trees"></a>Ağaçlar oluşturma ve dönüştürme

Sözdizimi dönüşümleri için iki stratejiden birini seçersiniz. **Fabrika yöntemleri** en iyi, değiştirilecek belirli düğümleri veya yeni kod eklemek istediğiniz belirli konumları ararken kullanılır. **Yeniden yazanlar,** değiştirmek istediğiniz kod desenleri için tüm projeyi taramaya istediğinizde en iyi sidir.

### <a name="create-nodes-with-factory-methods"></a>Fabrika yöntemleriyle düğüm oluşturma

İlk sözdizimi dönüşümü fabrika yöntemlerini gösterir. İfadeyi `using System.Collections;` bir `using System.Collections.Generic;` ifadeyle değiştireceksin. Bu örnek, fabrika <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxNode?displayProperty=nameWithType> yöntemlerini kullanarak <xref:Microsoft.CodeAnalysis.CSharp.SyntaxFactory?displayProperty=nameWithType> nesneleri nasıl oluşturduğunuzu gösterir. **Düğüm**her tür için, **belirteç,** veya **trivia** bu tür bir örnek oluşturur bir fabrika yöntemi var. Alttan yukarıya doğru hiyerarşik düğümler oluşturarak sözdizimi ağaçları oluşturursunuz. Ardından, varolan düğümleri oluşturduğunuz yeni ağaçla değiştirirken varolan programı dönüştürürsünüz.

Visual Studio'yı başlatın ve yeni bir C# **Stand-Alone Kod Analizi Aracı** projesi oluşturun. Visual Studio'da, Yeni Proje iletişim kutusunu görüntülemek için **Dosya** > **Yeni** > **Projesi'ni** seçin. **Visual C#** > **Extensibility** altında tek **başına kod analiz aracı**seçin. Bu quickstart iki örnek projeler vardır, bu yüzden çözüm **SyntaxTransformationQuickStart**adı ve proje **ConstructionCS**adı . **Tamam**'a tıklayın.

Bu proje, <xref:Microsoft.CodeAnalysis.CSharp.SyntaxFactory?displayProperty=nameWithType> ad alanını <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax?displayProperty=nameWithType> temsil eden `System.Collections.Generic` bir yapı oluşturmak için sınıf yöntemlerini kullanır.

Sınıfın fabrika yöntemlerini ve yöntemlerini `Program.cs` <xref:System.Console> daha sonra nitelemeden kullanabilmeniz için dosyanın en üstüne aşağıdaki yönergeyi ekleyin: <xref:Microsoft.CodeAnalysis.CSharp.SyntaxFactory>

[!code-csharp[import the SyntaxFactory class](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#StaticUsings "import the Syntax Factory class and the System.Console class")]

Deyimi temsil eden ağacı oluşturmak için **ad sözdizimi düğümleri** oluşturursunuz. `using System.Collections.Generic;` <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax>C#'da görünen dört tür ad için taban sınıftır. C# dilinde görünebilecek herhangi bir ad oluşturmak için bu dört tür adı bir araya getirirsiniz:

* <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax?displayProperty=nameWithType>, gibi `System` basit tek tanımlayıcı adları temsil `Microsoft`eder ve .
* <xref:Microsoft.CodeAnalysis.CSharp.Syntax.GenericNameSyntax?displayProperty=nameWithType>, genel bir tür veya yöntem `List<int>`adı gibi temsil eder.
* <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax?displayProperty=nameWithType>, gibi formun `<left-name>.<right-identifier-or-generic-name>` nitelikli bir `System.IO`adını temsil eder.
* <xref:Microsoft.CodeAnalysis.CSharp.Syntax.AliasQualifiedNameSyntax?displayProperty=nameWithType>, bir derleme extern diğer adı kullanarak `LibraryV2::Foo`bir adı temsil eder.

Düğüm oluşturmak <xref:Microsoft.CodeAnalysis.CSharp.SyntaxFactory.IdentifierName(System.String)> <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax> için yöntemi kullanırsınız. Yönteminize `Main` aşağıdaki kodu `Program.cs`ekleyin:

[!code-csharp[create the system identifier](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#CreateIdentifierName "Create and display the system name identifier")]

Önceki kod bir <xref:Microsoft.CodeAnalysis.CSharp.Syntax.IdentifierNameSyntax> nesne oluşturur ve değişkene `name`atar. Roslyn API'lerinin çoğu, ilgili türlerle çalışmayı kolaylaştırmak için temel sınıfları döndürer. Değişken `name`, <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax>an , oluşturmak gibi yeniden <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax>kullanılabilir. Örneği oluştururken tür çıkarımını kullanmayın. Bu projede bu adımı otomatikleştireceksin.

Adı sen yarattın. Şimdi, bir <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax>inşa ederek ağaca daha fazla düğüm inşa etmek zamanı. Yeni ağaç `name` adın sol olarak kullanır ve <xref:Microsoft.CodeAnalysis.CSharp.Syntax.IdentifierNameSyntax> `Collections` ad alanı için yeni bir <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax>sağ tarafı olarak. Aşağıdaki kodu `program.cs`ekleyin:

[!code-csharp[create the collections identifier](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#CreateQualifiedIdentifierName "Build the System.Collections identifier")]

Kodu yeniden çalıştırın ve sonuçları görün. Kodu temsil eden bir düğüm ağacı inşa ediyorsun. Ad alanı <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax> `System.Collections.Generic`oluşturmak için bu deseni devam eeeceksiniz. Aşağıdaki kodu `Program.cs`ekleyin:

[!code-csharp[create the full identifier](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#CreateFullNamespace "Build the System.Collections.Generic identifier")]

Ekleyecek kod için ağaç oluşturduğunuzu görmek için programı yeniden çalıştırın.

### <a name="create-a-modified-tree"></a>Değiştirilmiş bir ağaç oluşturma

Bir deyim içeren küçük bir sözdizimi ağacı inşa ettik. Yeni düğümler oluşturmak için API'ler tek bir deyim veya diğer küçük kod blokları oluşturmak için doğru seçimdir. Ancak, daha büyük kod blokları oluşturmak için düğümleri değiştiren veya düğümleri varolan bir ağaca ekleyen yöntemler kullanmalısınız. Sözdizimi ağaçlarının değişmez olduğunu unutmayın. **Sözdizimi API' si,** inşaattan sonra varolan bir sözdizimi ağacını değiştirmek için herhangi bir mekanizma sağlamaz. Bunun yerine, varolandeğişikliklere dayalı yeni ağaçlar üreten yöntemler sağlar. `With*`yöntemler, sınıfta beyan edilen uzantı yöntemlerinden <xref:Microsoft.CodeAnalysis.SyntaxNode> türeyen veya uzatma yöntemlerinden kaynaklanan somut sınıflarda tanımlanır. <xref:Microsoft.CodeAnalysis.SyntaxNodeExtensions> Bu yöntemler, varolan bir düğümün alt özelliklerine değişiklikler uygulayarak yeni bir düğüm oluşturur. Ayrıca, <xref:Microsoft.CodeAnalysis.SyntaxNodeExtensions.ReplaceNode%2A> uzantı yöntemi bir alt ağaçta bir soyundan gelen düğüm değiştirmek için kullanılabilir. Bu yöntem ayrıca, yeni oluşturulan alt öğeyi işaret etmek için üst öğeyi güncelleştirir ve bu işlemi tüm ağaca kadar yineler - ağacı _yeniden döndürme_ olarak bilinen bir işlem.

Bir sonraki adım, tüm (küçük) bir programı temsil eden bir ağaç oluşturmak ve sonra onu değiştirmektir. `Program` Sınıfın başına aşağıdaki kodu ekleyin:

[!code-csharp[create a parse tree](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#DeclareSampleCode "Create a tree that represents a small program")]

> [!NOTE]
> Örnek kod ad `System.Collections` alanını değil, `System.Collections.Generic` ad alanını kullanır.

Ardından, metni ayrıştırmak ve `Main` bir ağaç oluşturmak için yöntemin altına aşağıdaki kodu ekleyin:

[!code-csharp[create a parse tree](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#CreateParseTree "Create a tree that represents a small program")]

Bu örnek, <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax.WithName(Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax)?displayProperty=NameWithType> bir <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax> düğümdeki adı önceki kodda oluşturulmuş olanla değiştirmek için yöntemi kullanır.

Adı önceki <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax> kodda <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax.WithName(Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax)> oluşturduğunuz adla güncelleştirmek için yöntemi kullanarak yeni bir düğüm oluşturun. `System.Collections` `Main` Yöntemin altına aşağıdaki kodu ekleyin:

[!code-csharp[create a new subtree](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#BuildNewUsing "Create the subtree with the replaced namespace")]

Programı çalıştırın ve çıktıya dikkatlice bakın. Kök `newusing` ağacına yerleştirilmemiş. Orijinal ağaç değiştirilmemiş.

Yeni bir ağaç <xref:Microsoft.CodeAnalysis.SyntaxNodeExtensions.ReplaceNode%2A> oluşturmak için uzantı yöntemini kullanarak aşağıdaki kodu ekleyin. Yeni ağaç, varolan alma işleminin güncelleştirilmiş `newUsing` düğümle değiştirilmesinin sonucudur. Bu yeni ağacı varolan `root` değişkene atarsınız:

[!code-csharp[create a new root tree](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#TransformTree "Create the transformed root tree with the replaced namespace")]

Programı yeniden çalıştırın. Bu kez ağaç şimdi doğru `System.Collections.Generic` ad alanı içeriak.

### <a name="transform-trees-using-syntaxrewriters"></a>Kullanarak ağaçları dönüştürün`SyntaxRewriters`

Ve `With*` <xref:Microsoft.CodeAnalysis.SyntaxNodeExtensions.ReplaceNode%2A> yöntemler, sözdizimi ağacının tek tek dallarını dönüştürmek için kullanışlı araçlar sağlar. Sınıf <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter?displayProperty=nameWithType> sözdizimi ağacında birden çok dönüşüm gerçekleştirir. Sınıf <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter?displayProperty=nameWithType> bir alt <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor%601?displayProperty=nameWithType>sınıftır. Belirli <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter> bir <xref:Microsoft.CodeAnalysis.SyntaxNode>türe dönüştürme uygular. Dönüşümleri sözdizimi ağacında <xref:Microsoft.CodeAnalysis.SyntaxNode> göründükleri her yerde birden çok nesne türüne uygulayabilirsiniz. Bu hızlı başlatmadaki ikinci proje, yerel değişken bildirimlerinde açık türleri kaldıran ve tür çıkarımının kullanılabilebileceği bir komut satırı yeniden oluşturma oluşturur.

Yeni bir C# **Tek Başına Kod Analizi Aracı** projesi oluşturun. Visual Studio'da çözüm `SyntaxTransformationQuickStart` düğümüne sağ tıklayın. **Yeni Proje iletişim kutusunu**görüntülemek için Yeni**Proje** **Ekle'yi** > seçin. **Visual C#** > **Genişletilebilirlik** **altında, Tek Başına Kod Analiz Aracı'nı**seçin. Projenizi `TransformationCS` adlandırın ve Tamam'ı tıklatın.

İlk adım, dönüşümlerinizi gerçekleştirmek için türetilen <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter> bir sınıf oluşturmaktır. Projeye yeni bir sınıf dosyası ekleyin. Visual Studio'da **Project** > **Add Class'ı seçin...** **Dosya** adı `TypeInferenceRewriter.cs` olarak Yeni Öğe ekle iletişim türünde.

`TypeInferenceRewriter.cs` Dosyaya yönergeleri kullanarak aşağıdakileri ekleyin:

[!code-csharp[add necessary usings](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#AddUsings "Add required usings")]

Ardından, `TypeInferenceRewriter` sınıfın sınıfı <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter> genişletmesini yapın:

[!code-csharp[add base class](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#BaseClass "Add base class")]

Bir <xref:Microsoft.CodeAnalysis.SemanticModel> alanı tutmak ve oluşturucuda başlatmayı sağlamak için özel bir salt okunur alanını bildirmek için aşağıdaki kodu ekleyin. Tür çıkarımının nerede kullanılabileceğini belirlemek için daha sonra bu alana ihtiyacınız olacaktır:

[!code-csharp[initialize members](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#Construction "Declare and initialize member variables")]

<xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter.VisitLocalDeclarationStatement(Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax)> Yöntemi geçersiz kılın:

```csharp
public override SyntaxNode VisitLocalDeclarationStatement(LocalDeclarationStatementSyntax node)
{

}
```

> [!NOTE]
> Roslyn API'lerinin çoğu, döndürülen gerçek çalışma zamanı türlerinin temel sınıfları olan dönüş türlerini bildirir. Birçok senaryoda, bir tür düğüm tamamen başka bir tür düğüm le değiştirilebilir - hatta kaldırılabilir. Bu örnekte, <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter.VisitLocalDeclarationStatement(Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax)> yöntem <xref:Microsoft.CodeAnalysis.SyntaxNode>türetilmiş tür . <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> Bu yeniden yazar, <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> varolana dayalı yeni bir düğüm döndürür.

Bu hızlı başlatma yerel değişken bildirimlerini işler. Döngüler, döngüler, `for` LINQ `foreach` ifadeleri ve lambda ifadeleri gibi diğer bildirimlere genişletebilirsiniz. Ayrıca bu rewriter sadece basit formun beyannameleri dönüştürecek:

```csharp
Type variable = expression;
```

Kendi başına keşfetmek istiyorsanız, bu tür değişken bildirimleri için bitmiş örneği genişletmeyi düşünün:

```csharp
// Multiple variables in a single declaration.
Type variable1 = expression1,
     variable2 = expression2;
// No initializer.
Type variable;
```

Bu bildirim formlarını yeniden `VisitLocalDeclarationStatement` yazmayı atlamak için yöntemin gövdesine aşağıdaki kodu ekleyin:

[!code-csharp[exclude other declarations](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#Exclusions "Exclude variables declarations not processed by this sample")]

Yöntem, parametredeğiştirilmeden `node` döndürülerek hiçbir yeniden yazma gerçekleşir gösterir. Bu `if` ifadelerden hiçbiri doğru değilse, düğüm başharfle olası bir bildirimi temsil eder. Bildirimde belirtilen tür adını ayıklamak için bu deyimleri <xref:Microsoft.CodeAnalysis.SemanticModel> ekleyin ve bir tür sembolü elde etmek için alanı kullanarak bağlamak:

[!code-csharp[extract type name](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#ExtractTypeSymbol "Extract the type name specified by the declaration")]

Şimdi, baş harf ifadesini bağlamak için bu ifadeyi ekleyin:

[!code-csharp[bind initializer](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#BindInitializer "Bind the initializer expressions")]

Son olarak, `if` baş harf ifadesinin türü `var` belirtilen türle eşleşiyorsa, varolan tür adını anahtar kelimeyle değiştirmek için aşağıdaki ifadeyi ekleyin:

[!code-csharp[ReplaceNode](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#ReplaceNode "Replace the initializer node")]

Bildirge, başharf ifadesini bir taban sınıfa veya arabirime atabileceğinden koşullu olarak gereklidir. Bu istenirse, atamanın sol ve sağ tarafındaki türler eşleşmez. Bu gibi durumlarda açık türü kaldırmak bir programın anlambilimini değiştirir. `var`bağlamsal bir anahtar kelime `var` olduğundan, anahtar kelime yerine tanımlayıcı olarak belirtilir. Önde gelen ve sondaki ıvır zıvır (beyaz boşluk) `var` dikey beyaz boşluk ve girintiyi korumak için eski tür adından anahtar kelimeye aktarılır. Tür adı aslında bildirim `ReplaceNode` deyiminin torunu <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> olduğu için dönüştürmek yerine `With*` kullanmak daha kolaydır.

`TypeInferenceRewriter`Bitirdin. Şimdi örneği `Program.cs` bitirmek için dosyanıza dönün. Bir test <xref:Microsoft.CodeAnalysis.Compilation> oluşturun <xref:Microsoft.CodeAnalysis.SemanticModel> ve ondan elde edin. Bunu <xref:Microsoft.CodeAnalysis.SemanticModel> denemek için `TypeInferenceRewriter`kullan. Bu adımı en son sen atacaksın. Bu arada, test derlemenizi temsil eden bir yer tutucu değişkeni bildirin:

[!code-csharp[DeclareCompilation](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/Program.cs#DeclareTestCompilation "Declare the test compilation")]

Bir anı durakldıktan sonra, hiçbir `CreateTestCompilation` yöntemin bulunmadığını bildiren bir hata squiggle görünmelisiniz. Ampulü açmak için **Ctrl+Period** tuşuna basın ve ardından **Yöntem Saplama** oluştur komutunu çağırmak için Enter tuşuna basın. Bu `CreateTestCompilation` `Program` komut, sınıftaki yöntem için bir yöntem saplama oluşturur. Bu yöntemi daha sonra doldurmak için geri geleceksiniz:

![C# Kullanımdan yöntem oluşturma](./media/syntax-transformation/generate-from-usage.png)

Testteki <xref:Microsoft.CodeAnalysis.SyntaxTree> <xref:Microsoft.CodeAnalysis.Compilation>her birinin üzerinde yinelemek için aşağıdaki kodu yazın. Her biri `TypeInferenceRewriter` <xref:Microsoft.CodeAnalysis.SemanticModel> için, bu ağaç için yeni bir baş harf:

[!code-csharp[IterateTrees](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/Program.cs#IterateTrees "Iterate all the source trees in the test compilation")]

Oluşturduğunuz `foreach` deyimin içinde, her kaynak ağaçta dönüşümü gerçekleştirmek için aşağıdaki kodu ekleyin. Bu kod, herhangi bir düzenleme yapıldıysa, yeni dönüştürülmüş ağacı koşullu olarak yazar. Yeniden yazarınız yalnızca tür çıkarımı kullanılarak basitleştirilebilen bir veya daha fazla yerel değişken bildirimiyle karşılaştığında bir ağacı değiştirmelidir:

[!code-csharp[TransformTrees](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/Program.cs#TransformTrees "Transform and save any trees that are modified by the rewriter")]

`File.WriteAllText` Kodun altında kıvrımlar görmelisin. Ampulü seçin ve gerekli `using System.IO;` ifadeyi ekleyin.

Neredeyse bitirdin! Bir adım kaldı: bir test <xref:Microsoft.CodeAnalysis.Compilation>oluşturma . Bu hızlı başlangıç sırasında hiç tür çıkarım kullanmadığınız için, mükemmel bir test çalışması yapılmış olurdu. Ne yazık ki, c# proje dosyasından derleme oluşturmak bu gözden geçirmenin kapsamı dışındadır. Ama neyse ki, talimatları dikkatle takip ediyorsanız, umut var. `CreateTestCompilation` yönteminin içeriğini aşağıdaki kodla değiştirin. Bu hızlı başlatmada açıklanan projeyle tesadüfen eşleşen bir test derlemesi oluşturur:

[!code-csharp[CreateTestCompilation](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/Program.cs#CreateTestCompilation "Create a test compilation using the code written for this quickstart.")]

Parmaklarını çapraz ve projeyi çalıştır. Visual Studio'da **Hata** > **Ayıklama Başlat'ı**seçin. Visual Studio tarafından projenizdeki dosyaların değiştiği sorulmalıdır. Değiştirilen dosyaları yeniden yüklemek için "**Tümüne Evet**" seçeneğini tıklayın. Muhteşemliğinizi gözlemlemek için onları inceleyin. Tüm bu açık ve gereksiz tür belirteci olmadan kodun ne kadar temiz göründüğünü unutmayın.

Tebrikler! **Derleyici API'lerini,** belirli sözdizimdiziliş desenler için bir C# projesindeki tüm dosyaları arayan, bu desenlerle eşleşen kaynak kodun anlambilimini analiz eden ve dönüştüren kendi yeniden düzenlemenizi yazmak için kullandınız. Artık resmen yeniden düzenleme yazarısın!
