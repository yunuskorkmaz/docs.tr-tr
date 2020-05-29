---
title: Sözdizimi dönüşümü ile çalışmaya başlama (Roslyn API 'Leri)
description: Sözdizimi ağaçlarını geçme, sorgulama ve yürüyen bir giriş.
ms.date: 06/01/2018
ms.custom: mvc
ms.openlocfilehash: 5879dfd6ed0a5f6465829eec496d10cfcfd07362
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202118"
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

İlk sözdizimi dönüştürmesi, Fabrika yöntemlerini gösterir. Bir `using System.Collections;` ifadeyi bir `using System.Collections.Generic;` ifadesiyle değiştirecek. Bu örnek <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxNode?displayProperty=nameWithType> , Fabrika yöntemlerini kullanarak nesneleri nasıl oluşturacağınızı gösterir <xref:Microsoft.CodeAnalysis.CSharp.SyntaxFactory?displayProperty=nameWithType> . Her **düğüm**, **belirteç**veya **üç** tür için, bu türün bir örneğini oluşturan bir fabrika yöntemi vardır. Düğümleri aşağıdan yukarıya doğru oluşturarak sözdizimi ağaçları oluşturursunuz. Ardından, var olan programı, oluşturduğunuz yeni ağaç ile varolan düğümleri değiştirmektir.

Visual Studio 'yu başlatın ve yeni bir C# **tek başına kod analizi araç** projesi oluşturun. Visual Studio 'da **File**  >  **New**  >  Yeni proje iletişim kutusunu göstermek için dosya yeni**Proje** ' yi seçin. **Visual C#**  >  **genişletilebilirliği** altında **tek başına bir kod Analizi Aracı**seçin. Bu hızlı başlangıçta iki örnek proje bulunur, bu nedenle çözümü **SyntaxTransformationQuickStart**olarak adlandırın ve projeyi **constructioncs**olarak adlandırın. **Tamam**'a tıklayın.

Bu proje, <xref:Microsoft.CodeAnalysis.CSharp.SyntaxFactory?displayProperty=nameWithType> <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax?displayProperty=nameWithType> ad alanını temsil eden bir oluşturmak için sınıf yöntemlerini kullanır `System.Collections.Generic` .

Aşağıdaki using yönergesini öğesinin en üstüne ekleyin `Program.cs` .

[!code-csharp[import the SyntaxFactory class](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#StaticUsings "import the Syntax Factory class and the System.Console class")]

İfadeyi temsil eden ağacı oluşturmak için **ad sözdizimi düğümleri** oluşturacaksınız `using System.Collections.Generic;` . <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax>, C# dilinde görünen dört tür ad için temel sınıftır. C# dilinde görünebilen herhangi bir ad oluşturmak için bu dört tür adı birlikte oluşturursunuz:

* <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax?displayProperty=nameWithType>, ve gibi basit tek tanımlayıcı adlarını temsil `System` eder `Microsoft` .
* <xref:Microsoft.CodeAnalysis.CSharp.Syntax.GenericNameSyntax?displayProperty=nameWithType>, gibi genel bir tür veya yöntem adını temsil eder `List<int>` .
* <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax?displayProperty=nameWithType>, gibi formun tam adını temsil eder `<left-name>.<right-identifier-or-generic-name>` `System.IO` .
* <xref:Microsoft.CodeAnalysis.CSharp.Syntax.AliasQualifiedNameSyntax?displayProperty=nameWithType>Bu, bir derleme extern diğer adını kullanarak bir adı temsil eder `LibraryV2::Foo` .

<xref:Microsoft.CodeAnalysis.CSharp.SyntaxFactory.IdentifierName(System.String)>Bir düğüm oluşturmak için yöntemini kullanırsınız <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax> . Aşağıdaki kodu `Main` yöntemine ekleyin `Program.cs` :

[!code-csharp[create the system identifier](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#CreateIdentifierName "Create and display the system name identifier")]

Önceki kod bir nesnesi oluşturur <xref:Microsoft.CodeAnalysis.CSharp.Syntax.IdentifierNameSyntax> ve değişkenine atar `name` . Roslyn API 'Lerinin birçoğu, ilgili türlerle çalışmayı kolaylaştırmak için temel sınıflar döndürür. , Bir değişkeni oluştururken yeniden kullanılabilir `name` <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax> <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax> . Örneği oluştururken tür çıkarımı kullanmayın. Bu adımı bu projede otomatikleştirin.

Adı oluşturdunuz. Şimdi, bir oluşturarak ağaçta daha fazla düğüm oluşturmaya zaman atalım <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax> . Yeni ağaç, `name` adının solunda ve <xref:Microsoft.CodeAnalysis.CSharp.Syntax.IdentifierNameSyntax> `Collections` öğesinin sağ tarafıyla birlikte ad alanı için yeni bir kez kullanılır <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax> . Aşağıdaki kodu öğesine ekleyin `program.cs` :

[!code-csharp[create the collections identifier](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#CreateQualifiedIdentifierName "Build the System.Collections identifier")]

Kodu yeniden çalıştırın ve sonuçları görün. Kodu temsil eden bir düğüm ağacı yarayorsunuz. Ad alanı için oluşturmak üzere bu düzene devam edersiniz <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax> `System.Collections.Generic` . Aşağıdaki kodu öğesine ekleyin `Program.cs` :

[!code-csharp[create the full identifier](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#CreateFullNamespace "Build the System.Collections.Generic identifier")]

Eklenecek kodun ağacını oluşturduğunuzdan emin olmak için programı yeniden çalıştırın.

### <a name="create-a-modified-tree"></a>Değiştirilmiş ağaç oluşturma

Tek bir ifade içeren küçük bir sözdizimi ağacı oluşturdunuz. Yeni düğümler oluşturmak için API 'Ler, tek deyimler veya diğer küçük kod blokları oluşturmak için doğru seçimdir. Ancak, daha büyük kod blokları oluşturmak için, düğümleri değiştirecek veya düğümleri varolan bir ağaca ekleyecek yöntemleri kullanmanız gerekir. Söz dizimi ağaçlarının sabit olduğunu unutmayın. **Sözdizimi API 'si** , oluşturulduktan sonra var olan bir sözdizimi ağacını değiştirmek için herhangi bir mekanizma sağlamaz. Bunun yerine, var olan değişikliklere göre yeni ağaçlar üreten yöntemler sağlar. `With*`Yöntemler <xref:Microsoft.CodeAnalysis.SyntaxNode> , sınıfında belirtilen genişletme yöntemlerinden veya sınıfından türetilen somut sınıflarda tanımlanmıştır <xref:Microsoft.CodeAnalysis.SyntaxNodeExtensions> . Bu yöntemler, var olan bir düğümün alt özelliklerine değişiklikler uygulayarak yeni bir düğüm oluşturur. Ek olarak, <xref:Microsoft.CodeAnalysis.SyntaxNodeExtensions.ReplaceNode%2A> genişletme yöntemi bir alt ağaçtaki alt düğümü değiştirmek için de kullanılabilir. Bu yöntem aynı zamanda yeni oluşturulan alt öğeye işaret eden üst öğeyi güncelleştirir ve bu işlemi, ağacı _yeniden dönme_ olarak bilinen bir işlem olan ağacın tamamına yineler.

Bir sonraki adım, (küçük) bir programın tamamını temsil eden bir ağaç oluşturmak ve ardından onu değiştirmektir. Sınıfının başlangıcına aşağıdaki kodu ekleyin `Program` :

[!code-csharp[create a parse tree](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#DeclareSampleCode "Create a tree that represents a small program")]

> [!NOTE]
> Örnek kod, ad alanını `System.Collections` değil ad alanını kullanır `System.Collections.Generic` .

Sonra, `Main` metni ayrıştırmak ve bir ağaç oluşturmak için yönteminin altına aşağıdaki kodu ekleyin:

[!code-csharp[create a parse tree](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#CreateParseTree "Create a tree that represents a small program")]

Bu örnek, <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax.WithName(Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax)?displayProperty=NameWithType> bir <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax> düğümdeki adı önceki kodda oluşturulmuş bir ile değiştirmek için yöntemini kullanır.

<xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax> <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax.WithName(Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax)> `System.Collections` Adı önceki kodda oluşturduğunuz adla güncelleştirmek için yöntemini kullanarak yeni bir düğüm oluşturun. Aşağıdaki kodu yönteminin altına ekleyin `Main` :

[!code-csharp[create a new subtree](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#BuildNewUsing "Create the subtree with the replaced namespace")]

Programı çalıştırın ve çıkışa dikkatle göz atın. `newusing`Kök ağaca yerleştirilmemiş. Özgün ağaç değiştirilmedi.

<xref:Microsoft.CodeAnalysis.SyntaxNodeExtensions.ReplaceNode%2A>Yeni bir ağaç oluşturmak için genişletme yöntemini kullanarak aşağıdaki kodu ekleyin. Yeni ağaç, varolan içeri aktarmanın güncelleştirilmiş düğümle değiştirilmesi sonucudur `newUsing` . Bu yeni ağacı mevcut `root` değişkene atarsınız:

[!code-csharp[create a new root tree](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#TransformTree "Create the transformed root tree with the replaced namespace")]

Programı yeniden çalıştırın. Bu kez, ağaç artık ad alanını doğru bir şekilde içeri aktarır `System.Collections.Generic` .

### <a name="transform-trees-using-syntaxrewriters"></a>Kullanarak ağaçları dönüştürme`SyntaxRewriters`

`With*`Ve <xref:Microsoft.CodeAnalysis.SyntaxNodeExtensions.ReplaceNode%2A> yöntemleri, bir sözdizimi ağacının tek tek dallarını dönüştürmek için kullanışlı bir yol sağlar. <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter?displayProperty=nameWithType>Sınıfı, bir sözdizimi ağacında birden çok dönüştürme gerçekleştirir. <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter?displayProperty=nameWithType>Sınıfı, öğesinin bir alt sınıfıdır <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor%601?displayProperty=nameWithType> . , <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter> Belirli bir türüne dönüşüm uygular <xref:Microsoft.CodeAnalysis.SyntaxNode> . <xref:Microsoft.CodeAnalysis.SyntaxNode>Bir sözdizimi ağacında göründükleri yerde, birden çok nesne türüne dönüşümler uygulayabilirsiniz. Bu hızlı başlangıçtaki ikinci proje, tür çıkarımı kullanılabilir her yerde yerel değişken bildirimlerinde açık türleri kaldıran bir komut satırı yeniden düzenlemesi oluşturur.

Yeni bir C# **tek başına kod analizi araç** projesi oluşturun. Visual Studio 'da `SyntaxTransformationQuickStart` çözüm düğümüne sağ tıklayın. **Add**  >  Yeni proje **iletişim kutusunu**göstermek için**Yeni proje** Ekle ' yi seçin. **Visual C#**  >  **genişletilebilirliği**altında **tek başına Kod Analizi Aracı**' nı seçin. Projenizi adlandırın `TransformationCS` ve Tamam ' a tıklayın.

İlk adım, <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter> dönüştürmelerinizi gerçekleştirmek için öğesinden türeten bir sınıf oluşturmaktır. Projeye yeni bir sınıf dosyası ekleyin. Visual Studio 'da **Proje**  >  **Sınıf Ekle...** öğesini seçin. **Yeni öğe Ekle** iletişim kutusunda `TypeInferenceRewriter.cs` dosya adı olarak yazın.

Aşağıdaki using yönergelerini `TypeInferenceRewriter.cs` dosyasına ekleyin:

[!code-csharp[add necessary usings](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#AddUsings "Add required usings")]

Sonra, `TypeInferenceRewriter` sınıfın sınıfı genişletmesine dikkat edin <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter> :

[!code-csharp[add base class](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#BaseClass "Add base class")]

Bir özel salt okuma alanı bildirmek için aşağıdaki kodu ekleyin <xref:Microsoft.CodeAnalysis.SemanticModel> ve oluşturucuda başlatın. Tür çıkarımını nerede kullanılabileceğini öğrenmek için bu alana daha sonra ihtiyacınız olacak:

[!code-csharp[initialize members](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#Construction "Declare and initialize member variables")]

Yöntemi geçersiz kılın <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter.VisitLocalDeclarationStatement(Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax)> :

```csharp
public override SyntaxNode VisitLocalDeclarationStatement(LocalDeclarationStatementSyntax node)
{

}
```

> [!NOTE]
> Roslyn API 'lerinin birçoğu, döndürülen gerçek çalışma zamanı türlerinin temel sınıfları olan dönüş türlerini bildirir. Birçok senaryoda, bir tür düğüm tamamen veya hatta kaldırılmış başka bir düğüm türüyle değiştirilebilir. Bu örnekte, <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter.VisitLocalDeclarationStatement(Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax)> metodu <xref:Microsoft.CodeAnalysis.SyntaxNode> türetilmiş türü yerine bir döndürür <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> . Bu yeniden yazıcı <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> , mevcut bir düğümü temel alarak yeni bir düğüm döndürüyor.

Bu hızlı başlangıçta yerel değişken bildirimleri ele alır. `foreach`Döngüleri, `for` DÖNGÜLERI, LINQ ifadeleri ve lambda ifadeleri gibi diğer bildirimlere genişletebilirsiniz. Ayrıca, bu yeniden yazıcı yalnızca en basit formun bildirimlerini dönüştürür:

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

Aşağıdaki kodu, `VisitLocalDeclarationStatement` Bu bildirim biçimlerini yeniden yazmayı atlamak için yönteminin gövdesine ekleyin:

[!code-csharp[exclude other declarations](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#Exclusions "Exclude variables declarations not processed by this sample")]

Yöntemi, parametreyi değiştirilmemiş olarak döndürerek yeniden yazma gerçekleşmeden emin olduğunu gösterir `node` . Bu `if` ifadelerden hiçbiri true ise, düğüm başlatma ile olası bir bildirimi temsil eder. Bildirimde belirtilen tür adını ayıklamak ve <xref:Microsoft.CodeAnalysis.SemanticModel> bir tür simgesi almak için alanı kullanarak bağlamak için bu deyimleri ekleyin:

[!code-csharp[extract type name](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#ExtractTypeSymbol "Extract the type name specified by the declaration")]

Şimdi Başlatıcı ifadesini bağlamak için bu deyimi ekleyin:

[!code-csharp[bind initializer](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#BindInitializer "Bind the initializer expressions")]

Son olarak, `if` `var` Başlatıcı ifadesinin türü belirtilen türle eşleşiyorsa, varolan tür adını anahtar sözcüğüyle değiştirmek için aşağıdaki deyimi ekleyin:

[!code-csharp[ReplaceNode](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#ReplaceNode "Replace the initializer node")]

Bildirim, başlatıcı ifadesini temel bir sınıfa veya arabirime atabileceğinden koşullu gereklidir. Bu istenirse, atamanın sol ve sağ tarafındaki türler eşleşmez. Bu durumlarda açık türün kaldırılması bir programın semantiğini değiştirir. `var`bağlamsal bir anahtar sözcük olduğundan, bir anahtar sözcük yerine tanımlayıcı olarak belirtilir `var` . Baştaki ve sondaki üç nokta (beyaz boşluk), `var` dikey boşluk ve girintileme sağlamak için eski tür adından anahtar sözcüğe aktarılır. `ReplaceNode` `With*` <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> Tür adı bildirim ifadesinin gerçekten alt öğesi olduğundan, bunu dönüştürmek yerine kullanılması daha basittir.

Tamamladınız `TypeInferenceRewriter` . Şimdi `Program.cs` , örneği tamamlayacak şekilde dosyanıza geri dönün. Bir test oluşturun <xref:Microsoft.CodeAnalysis.Compilation> ve buradan alın <xref:Microsoft.CodeAnalysis.SemanticModel> . Bunu <xref:Microsoft.CodeAnalysis.SemanticModel> denemek için kullanın `TypeInferenceRewriter` . Bu adımı son yapmanız gerekir. Bu arada, test derlenmesini temsil eden bir yer tutucu değişkeni bildirin:

[!code-csharp[DeclareCompilation](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/Program.cs#DeclareTestCompilation "Declare the test compilation")]

Bir süre durakladıktan sonra, hiçbir yöntemin mevcut olmadığını bildiren bir hata ortaya çıktıktan sonra hata görürsünüz `CreateTestCompilation` . Açık ampul ' i açmak için **CTRL + nokta** tuşlarına basın ve sonra **Yöntem oluşturma saplama** komutunu çağırmak için ENTER tuşuna basın. Bu komut, sınıfında yöntemi için bir yöntem saplaması oluşturacaktır `CreateTestCompilation` `Program` . Daha sonra bu yöntemi dolduracak şekilde geri döneceksiniz:

![C# kullanımdan bir yöntem oluştur](./media/syntax-transformation/generate-from-usage.png)

Testteki her birinde yinelemek için aşağıdaki kodu yazın <xref:Microsoft.CodeAnalysis.SyntaxTree> <xref:Microsoft.CodeAnalysis.Compilation> . Her biri için, `TypeInferenceRewriter` Bu ağaç için ile yeni bir başlatın <xref:Microsoft.CodeAnalysis.SemanticModel> :

[!code-csharp[IterateTrees](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/Program.cs#IterateTrees "Iterate all the source trees in the test compilation")]

`foreach`Oluşturduğunuz deyimin içinde, her kaynak ağacında dönüştürmeyi gerçekleştirmek için aşağıdaki kodu ekleyin. Bu kod, herhangi bir düzenleme yapılıyorsa, yeni dönüştürülmüş ağacı koşullu olarak yazar. Yeniden yazıcı, tür çıkarımı kullanılarak Basitleştirilen bir veya daha fazla yerel değişken bildirimi ile karşılaştığında yalnızca bir ağacı değiştirmeli:

[!code-csharp[TransformTrees](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/Program.cs#TransformTrees "Transform and save any trees that are modified by the rewriter")]

Kodun altında dalgalı çizgiler görmeniz gerekir `File.WriteAllText` . Ampul ' i seçin ve gerekli `using System.IO;` ifadeyi ekleyin.

Neredeyse tamamladınız! Bir adım kaldı: test oluşturma <xref:Microsoft.CodeAnalysis.Compilation> . Bu hızlı başlangıçta tür çıkarımı kullanmadığınız için, tam bir test çalışması yapmış olabilir. Ne yazık ki, bir C# proje dosyasından derleme oluşturmak Bu izlenecek yolun kapsamının dışındadır. Ancak, yönergeleri dikkatle takip ediyorsanız, umuyoruz. `CreateTestCompilation` yönteminin içeriğini aşağıdaki kodla değiştirin. Tesadüfen bu hızlı başlangıçta açıklanan projeyle eşleşen bir test derlemesi oluşturur:

[!code-csharp[CreateTestCompilation](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/Program.cs#CreateTestCompilation "Create a test compilation using the code written for this quickstart.")]

Parmaklarınızın çapraz yanı sıra projeyi çalıştırın. Visual Studio 'da **hata**  >  **ayıklamayı Başlat hata**Ayıkla ' yı seçin. Visual Studio 'Nun projenizdeki dosyaların değiştiği sorulur. Değiştirilen dosyaları yeniden yüklemek için "**Tümüne Evet**" e tıklayın. Awesomeninizi gözlemlemek için bunları inceleyin. Kodun tüm açık ve gereksiz tür belirticileri olmadan ne kadar temizleyici göründüğünü göz önünde edin.

Tebrikler! **Derleyici API 'lerini** , belirli sözdizimsel desenler Için bir C# projesindeki tüm dosyaları arayan kendi yeniden düzenleme, bu desenlerle eşleşen kaynak kodun semantiğini analiz eden ve onu dönüştüren kendi yeniden düzenlemenizi yazmak için kullandınız. Artık resmi bir yeniden düzenleme yazarımız!
