---
title: Sözdizimi dönüşümü ile çalışmaya başlama (Roslyn API 'Leri)
description: Sözdizimi ağaçlarını geçme, sorgulama ve yürüyen bir giriş.
ms.date: 06/01/2018
ms.custom: mvc
ms.openlocfilehash: 232fe5fcba35f152dbc3f00b2f2c092b5df0dd35
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82794799"
---
# <a name="get-started-with-syntax-transformation"></a>Sözdizimi dönüşümü ile çalışmaya başlama

Bu öğretici, [sözdizimi analizi ile çalışmaya başlama](syntax-analysis.md) bölümünde keşfolan kavram ve tekniklerin yanı sıra [anlam Analizi](semantic-analysis.md) hızlı başlangıçlarını kullanmaya başlamanızı de oluşturur. Henüz yapmadıysanız, bu hızlı başlangıçlara başlamadan önce bunu tamamlamalısınız.

Bu hızlı başlangıçta, sözdizimi ağaçları oluşturma ve dönüştürme tekniklerini keşfedebilirsiniz. Önceki hızlı başlangıçlarda öğrendiğiniz tekniklerle birlikte ilk komut satırı yeniden düzenleme bilgilerinizi oluşturursunuz!

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

## <a name="immutability-and-the-net-compiler-platform"></a>İmlebilirlik ve .NET derleyici platformu

**İmlebilirlik kullanılabilirliği** , .NET derleyicisi platformunun temel bir temel ' dir. Sabit veri yapıları oluşturulduktan sonra değiştirilemez. Değişmez veri yapıları, aynı anda birden çok tüketici tarafından güvenli bir şekilde paylaşılabilir ve çözümlenebilir. Bir tüketicinin, bir tüketiciyi öngörülemeyen yollarla etkilediğine ilişkin tehlike yoktur. Çözümleyici 'nizin kilitleri veya diğer eşzamanlılık ölçüleri gerekmez. Bu kural, söz konusu sözdizimi ağaçları, derlemeler, semboller, anlam modelleri ve karşılaştığınız tüm diğer veri yapılarına yöneliktir. API 'Ler, var olan yapıları değiştirmek yerine, eski farklılıklara göre belirtilen farklılıkları temel alarak yeni nesneler oluşturur. Dönüşümleri kullanarak yeni ağaçlar oluşturmak için bu kavramı sözdizimi ağaçlarına uygularsınız.

## <a name="create-and-transform-trees"></a>Ağaçlar oluşturma ve dönüştürme

Söz dizimi dönüştürmeleri için iki stratejiden birini seçersiniz. **Fabrika yöntemleri** , değiştirilecek belirli düğümleri veya yeni kod eklemek istediğiniz belirli konumları ararken en iyi şekilde kullanılır. **Yeniden yazarlar** , değiştirmek istediğiniz kod desenleri için bir projenin tamamını taramak istediğinizde en iyi seçenektir.

### <a name="create-nodes-with-factory-methods"></a>Fabrika yöntemleriyle düğüm oluşturma

İlk sözdizimi dönüştürmesi, Fabrika yöntemlerini gösterir. Bir `using System.Collections;` ifadeyi bir `using System.Collections.Generic;` ifadesiyle değiştirecek. Bu örnek, <xref:Microsoft.CodeAnalysis.CSharp.SyntaxFactory?displayProperty=nameWithType> Fabrika yöntemlerini kullanarak <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxNode?displayProperty=nameWithType> nesneleri nasıl oluşturacağınızı gösterir. Her **düğüm**, **belirteç**veya **üç** tür için, bu türün bir örneğini oluşturan bir fabrika yöntemi vardır. Düğümleri aşağıdan yukarıya doğru oluşturarak sözdizimi ağaçları oluşturursunuz. Ardından, var olan programı, oluşturduğunuz yeni ağaç ile varolan düğümleri değiştirmektir.

Visual Studio 'yu başlatın ve yeni bir C# **tek başına kod analizi araç** projesi oluşturun. Visual Studio 'da yeni proje iletişim kutusunu göstermek için **Dosya** > **Yeni** > **Proje** ' yi seçin. **Visual C#** > **genişletilebilirliği** altında **tek başına bir kod Analizi Aracı**seçin. Bu hızlı başlangıçta iki örnek proje bulunur, bu nedenle çözümü **SyntaxTransformationQuickStart**olarak adlandırın ve projeyi **constructioncs**olarak adlandırın. **Tamam**'a tıklayın.

Bu proje, <xref:Microsoft.CodeAnalysis.CSharp.SyntaxFactory?displayProperty=nameWithType> <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax?displayProperty=nameWithType> `System.Collections.Generic` ad alanını temsil eden bir oluşturmak için sınıf yöntemlerini kullanır.

Aşağıdaki using yönergesini, `Program.cs` <xref:Microsoft.CodeAnalysis.CSharp.SyntaxFactory> sınıfının Fabrika yöntemlerini ve yöntemlerini <xref:System.Console> , daha sonra bunları nitelemeden kullanabilmek için ' ın en üstüne ekleyin:

[!code-csharp[import the SyntaxFactory class](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#StaticUsings "import the Syntax Factory class and the System.Console class")]

İfadeyi temsil eden ağacı oluşturmak için **ad sözdizimi düğümleri** oluşturacaksınız. `using System.Collections.Generic;` <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax>, C# dilinde görünen dört tür ad için temel sınıftır. C# dilinde görünebilen herhangi bir ad oluşturmak için bu dört tür adı birlikte oluşturursunuz:

* <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax?displayProperty=nameWithType>, ve `System` `Microsoft`gibi basit tek tanımlayıcı adlarını temsil eder.
* <xref:Microsoft.CodeAnalysis.CSharp.Syntax.GenericNameSyntax?displayProperty=nameWithType>, gibi genel bir tür veya yöntem adını temsil eder `List<int>`.
* <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax?displayProperty=nameWithType>, gibi formun `<left-name>.<right-identifier-or-generic-name>` tam adını temsil eder `System.IO`.
* <xref:Microsoft.CodeAnalysis.CSharp.Syntax.AliasQualifiedNameSyntax?displayProperty=nameWithType>Bu, bir derleme extern diğer adını kullanarak bir `LibraryV2::Foo`adı temsil eder.

Bir <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax> düğüm oluşturmak <xref:Microsoft.CodeAnalysis.CSharp.SyntaxFactory.IdentifierName(System.String)> için yöntemini kullanırsınız. Aşağıdaki kodu `Main` yöntemine ekleyin `Program.cs`:

[!code-csharp[create the system identifier](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#CreateIdentifierName "Create and display the system name identifier")]

Önceki kod bir <xref:Microsoft.CodeAnalysis.CSharp.Syntax.IdentifierNameSyntax> nesnesi oluşturur ve değişkenine `name`atar. Roslyn API 'Lerinin birçoğu, ilgili türlerle çalışmayı kolaylaştırmak için temel sınıflar döndürür. , Bir `name` <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax>değişkeni oluştururken yeniden kullanılabilir <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax>. Örneği oluştururken tür çıkarımı kullanmayın. Bu adımı bu projede otomatikleştirin.

Adı oluşturdunuz. Şimdi, bir <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax>oluşturarak ağaçta daha fazla düğüm oluşturmaya zaman atalım. Yeni ağaç, adının `name` solunda ve öğesinin sağ tarafıyla birlikte <xref:Microsoft.CodeAnalysis.CSharp.Syntax.IdentifierNameSyntax> `Collections` ad alanı için yeni bir kez kullanılır <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax>. Aşağıdaki kodu öğesine `program.cs`ekleyin:

[!code-csharp[create the collections identifier](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#CreateQualifiedIdentifierName "Build the System.Collections identifier")]

Kodu yeniden çalıştırın ve sonuçları görün. Kodu temsil eden bir düğüm ağacı yarayorsunuz. Ad alanı <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax> `System.Collections.Generic`için oluşturmak üzere bu düzene devam edersiniz. Aşağıdaki kodu öğesine `Program.cs`ekleyin:

[!code-csharp[create the full identifier](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#CreateFullNamespace "Build the System.Collections.Generic identifier")]

Eklenecek kodun ağacını oluşturduğunuzdan emin olmak için programı yeniden çalıştırın.

### <a name="create-a-modified-tree"></a>Değiştirilmiş ağaç oluşturma

Tek bir ifade içeren küçük bir sözdizimi ağacı oluşturdunuz. Yeni düğümler oluşturmak için API 'Ler, tek deyimler veya diğer küçük kod blokları oluşturmak için doğru seçimdir. Ancak, daha büyük kod blokları oluşturmak için, düğümleri değiştirecek veya düğümleri varolan bir ağaca ekleyecek yöntemleri kullanmanız gerekir. Söz dizimi ağaçlarının sabit olduğunu unutmayın. **Sözdizimi API 'si** , oluşturulduktan sonra var olan bir sözdizimi ağacını değiştirmek için herhangi bir mekanizma sağlamaz. Bunun yerine, var olan değişikliklere göre yeni ağaçlar üreten yöntemler sağlar. `With*`Yöntemler, <xref:Microsoft.CodeAnalysis.SyntaxNode> <xref:Microsoft.CodeAnalysis.SyntaxNodeExtensions> sınıfında belirtilen genişletme yöntemlerinden veya sınıfından türetilen somut sınıflarda tanımlanmıştır. Bu yöntemler, var olan bir düğümün alt özelliklerine değişiklikler uygulayarak yeni bir düğüm oluşturur. Ek olarak, <xref:Microsoft.CodeAnalysis.SyntaxNodeExtensions.ReplaceNode%2A> genişletme yöntemi bir alt ağaçtaki alt düğümü değiştirmek için de kullanılabilir. Bu yöntem aynı zamanda yeni oluşturulan alt öğeye işaret eden üst öğeyi güncelleştirir ve bu işlemi, ağacı _yeniden dönme_ olarak bilinen bir işlem olan ağacın tamamına yineler.

Bir sonraki adım, (küçük) bir programın tamamını temsil eden bir ağaç oluşturmak ve ardından onu değiştirmektir. `Program` Sınıfının başlangıcına aşağıdaki kodu ekleyin:

[!code-csharp[create a parse tree](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#DeclareSampleCode "Create a tree that represents a small program")]

> [!NOTE]
> Örnek kod, ad alanını `System.Collections` değil `System.Collections.Generic` ad alanını kullanır.

Sonra, metni ayrıştırmak ve bir ağaç oluşturmak için `Main` yönteminin altına aşağıdaki kodu ekleyin:

[!code-csharp[create a parse tree](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#CreateParseTree "Create a tree that represents a small program")]

Bu örnek, bir <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax.WithName(Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax)?displayProperty=NameWithType> <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax> düğümdeki adı önceki kodda oluşturulmuş bir ile değiştirmek için yöntemini kullanır.

Adı önceki kodda <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax> oluşturduğunuz adla güncelleştirmek <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax.WithName(Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax)> için yöntemini kullanarak yeni bir düğüm oluşturun. `System.Collections` Aşağıdaki kodu `Main` yönteminin altına ekleyin:

[!code-csharp[create a new subtree](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#BuildNewUsing "Create the subtree with the replaced namespace")]

Programı çalıştırın ve çıkışa dikkatle göz atın. `newusing` Kök ağaca yerleştirilmemiş. Özgün ağaç değiştirilmedi.

Yeni bir ağaç oluşturmak için <xref:Microsoft.CodeAnalysis.SyntaxNodeExtensions.ReplaceNode%2A> genişletme yöntemini kullanarak aşağıdaki kodu ekleyin. Yeni ağaç, varolan içeri aktarmanın güncelleştirilmiş `newUsing` düğümle değiştirilmesi sonucudur. Bu yeni ağacı mevcut `root` değişkene atarsınız:

[!code-csharp[create a new root tree](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#TransformTree "Create the transformed root tree with the replaced namespace")]

Programı yeniden çalıştırın. Bu kez, ağaç artık `System.Collections.Generic` ad alanını doğru bir şekilde içeri aktarır.

### <a name="transform-trees-using-syntaxrewriters"></a>Kullanarak ağaçları dönüştürme`SyntaxRewriters`

Ve `With*` <xref:Microsoft.CodeAnalysis.SyntaxNodeExtensions.ReplaceNode%2A> yöntemleri, bir sözdizimi ağacının tek tek dallarını dönüştürmek için kullanışlı bir yol sağlar. Sınıfı <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter?displayProperty=nameWithType> , bir sözdizimi ağacında birden çok dönüştürme gerçekleştirir. <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter?displayProperty=nameWithType> Sınıfı, öğesinin <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor%601?displayProperty=nameWithType>bir alt sınıfıdır. , <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter> Belirli bir türüne dönüşüm uygular <xref:Microsoft.CodeAnalysis.SyntaxNode>. Bir sözdizimi ağacında göründükleri yerde, <xref:Microsoft.CodeAnalysis.SyntaxNode> birden çok nesne türüne dönüşümler uygulayabilirsiniz. Bu hızlı başlangıçtaki ikinci proje, tür çıkarımı kullanılabilir her yerde yerel değişken bildirimlerinde açık türleri kaldıran bir komut satırı yeniden düzenlemesi oluşturur.

Yeni bir C# **tek başına kod analizi araç** projesi oluşturun. Visual Studio 'da `SyntaxTransformationQuickStart` çözüm düğümüne sağ tıklayın. **Yeni proje iletişim kutusunu**göstermek için**Yeni proje** **Ekle** > ' yi seçin. **Visual C#** > **genişletilebilirliği**altında **tek başına Kod Analizi Aracı**' nı seçin. Projenizi `TransformationCS` adlandırın ve Tamam ' a tıklayın.

İlk adım, dönüştürmelerinizi gerçekleştirmek için öğesinden <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter> türeten bir sınıf oluşturmaktır. Projeye yeni bir sınıf dosyası ekleyin. Visual Studio 'da **Proje** > **Sınıf Ekle...** öğesini seçin. **Yeni öğe Ekle** iletişim kutusunda dosya adı `TypeInferenceRewriter.cs` olarak yazın.

Aşağıdaki using yönergelerini `TypeInferenceRewriter.cs` dosyasına ekleyin:

[!code-csharp[add necessary usings](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#AddUsings "Add required usings")]

Sonra, `TypeInferenceRewriter` sınıfın <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter> sınıfı genişletmesine dikkat edin:

[!code-csharp[add base class](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#BaseClass "Add base class")]

Bir <xref:Microsoft.CodeAnalysis.SemanticModel> özel salt okuma alanı bildirmek için aşağıdaki kodu ekleyin ve oluşturucuda başlatın. Tür çıkarımını nerede kullanılabileceğini öğrenmek için bu alana daha sonra ihtiyacınız olacak:

[!code-csharp[initialize members](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#Construction "Declare and initialize member variables")]

<xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter.VisitLocalDeclarationStatement(Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax)> Yöntemi geçersiz kılın:

```csharp
public override SyntaxNode VisitLocalDeclarationStatement(LocalDeclarationStatementSyntax node)
{

}
```

> [!NOTE]
> Roslyn API 'lerinin birçoğu, döndürülen gerçek çalışma zamanı türlerinin temel sınıfları olan dönüş türlerini bildirir. Birçok senaryoda, bir tür düğüm tamamen veya hatta kaldırılmış başka bir düğüm türüyle değiştirilebilir. Bu örnekte, <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter.VisitLocalDeclarationStatement(Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax)> metodu türetilmiş türü yerine bir <xref:Microsoft.CodeAnalysis.SyntaxNode>döndürür <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax>. Bu yeniden yazıcı, mevcut bir <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> düğümü temel alarak yeni bir düğüm döndürüyor.

Bu hızlı başlangıçta yerel değişken bildirimleri ele alır. `foreach` Döngüleri, `for` döngüleri, LINQ ifadeleri ve lambda ifadeleri gibi diğer bildirimlere genişletebilirsiniz. Ayrıca, bu yeniden yazıcı yalnızca en basit formun bildirimlerini dönüştürür:

```csharp
Type variable = expression;
```

Kendi kendinize araştırmak isterseniz, bu tür bildirimler için tamamlanan örneği genişletmeyi göz önünde bulundurun:

```csharp
// Multiple variables in a single declaration.
Type variable1 = expression1,
     variable2 = expression2;
// No initializer.
Type variable;
```

Aşağıdaki kodu, bu bildirim biçimlerini yeniden yazmayı atlamak `VisitLocalDeclarationStatement` için yönteminin gövdesine ekleyin:

[!code-csharp[exclude other declarations](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#Exclusions "Exclude variables declarations not processed by this sample")]

Yöntemi, `node` parametreyi değiştirilmemiş olarak döndürerek yeniden yazma gerçekleşmeden emin olduğunu gösterir. Bu `if` ifadelerden hiçbiri true ise, düğüm başlatma ile olası bir bildirimi temsil eder. Bildirimde belirtilen tür adını ayıklamak ve bir tür simgesi almak için <xref:Microsoft.CodeAnalysis.SemanticModel> alanı kullanarak bağlamak için bu deyimleri ekleyin:

[!code-csharp[extract type name](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#ExtractTypeSymbol "Extract the type name specified by the declaration")]

Şimdi Başlatıcı ifadesini bağlamak için bu deyimi ekleyin:

[!code-csharp[bind initializer](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#BindInitializer "Bind the initializer expressions")]

Son olarak, başlatıcı ifadesinin `if` türü belirtilen türle eşleşiyorsa, varolan tür adını `var` anahtar sözcüğüyle değiştirmek için aşağıdaki deyimi ekleyin:

[!code-csharp[ReplaceNode](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#ReplaceNode "Replace the initializer node")]

Bildirim, başlatıcı ifadesini temel bir sınıfa veya arabirime atabileceğinden koşullu gereklidir. Bu istenirse, atamanın sol ve sağ tarafındaki türler eşleşmez. Bu durumlarda açık türün kaldırılması bir programın semantiğini değiştirir. `var`bağlamsal bir anahtar sözcük olduğundan `var` , bir anahtar sözcük yerine tanımlayıcı olarak belirtilir. Baştaki ve sondaki üç nokta (beyaz boşluk), dikey boşluk ve girintileme sağlamak için eski tür adından `var` anahtar sözcüğe aktarılır. Tür adı bildirim ifadesinin gerçekten `ReplaceNode` alt öğesi `With*` olduğundan, <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> bunu dönüştürmek yerine kullanılması daha basittir.

Tamamladınız `TypeInferenceRewriter`. Şimdi, örneği tamamlayacak `Program.cs` şekilde dosyanıza geri dönün. Bir test <xref:Microsoft.CodeAnalysis.Compilation> oluşturun ve <xref:Microsoft.CodeAnalysis.SemanticModel> buradan alın. Bunu denemek <xref:Microsoft.CodeAnalysis.SemanticModel> için kullanın `TypeInferenceRewriter`. Bu adımı son yapmanız gerekir. Bu arada, test derlenmesini temsil eden bir yer tutucu değişkeni bildirin:

[!code-csharp[DeclareCompilation](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/Program.cs#DeclareTestCompilation "Declare the test compilation")]

Bir süre durakladıktan sonra, hiçbir `CreateTestCompilation` yöntemin mevcut olmadığını bildiren bir hata ortaya çıktıktan sonra hata görürsünüz. Açık ampul ' i açmak için **CTRL + nokta** tuşlarına basın ve sonra **Yöntem oluşturma saplama** komutunu çağırmak için ENTER tuşuna basın. Bu komut, `CreateTestCompilation` `Program` sınıfında yöntemi için bir yöntem saplaması oluşturacaktır. Daha sonra bu yöntemi dolduracak şekilde geri döneceksiniz:

![C# kullanımdan bir yöntem oluştur](./media/syntax-transformation/generate-from-usage.png)

Testteki <xref:Microsoft.CodeAnalysis.SyntaxTree> <xref:Microsoft.CodeAnalysis.Compilation>her birinde yinelemek için aşağıdaki kodu yazın. Her biri için, bu ağaç `TypeInferenceRewriter` <xref:Microsoft.CodeAnalysis.SemanticModel> için ile yeni bir başlatın:

[!code-csharp[IterateTrees](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/Program.cs#IterateTrees "Iterate all the source trees in the test compilation")]

Oluşturduğunuz `foreach` deyimin içinde, her kaynak ağacında dönüştürmeyi gerçekleştirmek için aşağıdaki kodu ekleyin. Bu kod, herhangi bir düzenleme yapılıyorsa, yeni dönüştürülmüş ağacı koşullu olarak yazar. Yeniden yazıcı, tür çıkarımı kullanılarak Basitleştirilen bir veya daha fazla yerel değişken bildirimi ile karşılaştığında yalnızca bir ağacı değiştirmeli:

[!code-csharp[TransformTrees](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/Program.cs#TransformTrees "Transform and save any trees that are modified by the rewriter")]

`File.WriteAllText` Kodun altında dalgalı çizgiler görmeniz gerekir. Ampul ' i seçin ve gerekli `using System.IO;` ifadeyi ekleyin.

Neredeyse tamamladınız! Bir adım kaldı: test <xref:Microsoft.CodeAnalysis.Compilation>oluşturma. Bu hızlı başlangıçta tür çıkarımı kullanmadığınız için, tam bir test çalışması yapmış olabilir. Ne yazık ki, bir C# proje dosyasından derleme oluşturmak Bu izlenecek yolun kapsamının dışındadır. Ancak, yönergeleri dikkatle takip ediyorsanız, umuyoruz. `CreateTestCompilation` yönteminin içeriğini aşağıdaki kodla değiştirin. Tesadüfen bu hızlı başlangıçta açıklanan projeyle eşleşen bir test derlemesi oluşturur:

[!code-csharp[CreateTestCompilation](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/Program.cs#CreateTestCompilation "Create a test compilation using the code written for this quickstart.")]

Parmaklarınızın çapraz yanı sıra projeyi çalıştırın. Visual Studio 'da **hata** > **ayıklamayı Başlat hata**Ayıkla ' yı seçin. Visual Studio 'Nun projenizdeki dosyaların değiştiği sorulur. Değiştirilen dosyaları yeniden yüklemek için "**Tümüne Evet**" e tıklayın. Awesomeninizi gözlemlemek için bunları inceleyin. Kodun tüm açık ve gereksiz tür belirticileri olmadan ne kadar temizleyici göründüğünü göz önünde edin.

Tebrikler! **Derleyici API 'lerini** , belirli sözdizimsel desenler Için bir C# projesindeki tüm dosyaları arayan kendi yeniden düzenleme, bu desenlerle eşleşen kaynak kodun semantiğini analiz eden ve onu dönüştüren kendi yeniden düzenlemenizi yazmak için kullandınız. Artık resmi bir yeniden düzenleme yazarımız!
