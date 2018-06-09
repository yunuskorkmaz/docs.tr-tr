---
title: Sözdizimi dönüştürme (Roslyn API) ile çalışmaya başlama
description: Çapraz geçiş yapma, sorgulama ve sözdizimi ağaçları taramasını giriş.
ms.date: 06/01/2018
ms.custom: mvc
ms.openlocfilehash: 04053645b91e8f74e890340fb9bba66a4efdce0c
ms.sourcegitcommit: 2ad7d06f4f469b5d8a5280ac0e0289a81867fc8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2018
ms.locfileid: "35231635"
---
# <a name="get-started-with-syntax-transformation"></a>Sözdizimi dönüştürme ile çalışmaya başlama

Bu öğretici kavramlara oluşturur ve teknikleri incelediniz [sözdizimi Analizi ile çalışmaya başlama](syntax-analysis.md) ve [semantik analizi ile çalışmaya başlama](semantic-analysis.md) quickstarts. Henüz yapmadıysanız, bunu başlamadan önce bu hızlı başlangıçların tamamlamanız gerekir.

Bu hızlı başlangıç oluşturma ve sözdizimi ağaçları dönüştürme teknikleri keşfedin. İçinde önceki quickstarts öğrenilen teknikleri ile birlikte, ilk komut satırı yeniden düzenleme oluşturun!

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

## <a name="immutability-and-the-net-compiler-platform"></a>Girişi ve .NET derleyici platformu

**Girişi** .NET derleyici platformu, temel bir ilkesidir. Sabit veri yapılarını bunlar oluşturduktan sonra değiştirilemez. Sabit veri yapılarını güvenli bir şekilde paylaşılan ve aynı anda birden çok tüketiciler tarafından analiz. Bu tek bir tüketici başka tahmin edilemeyen şekillerde etkiler tehlike yoktur. Çözümleyicisi kilitleri ya da diğer eşzamanlılık ölçüleri gerekmez. Bu kural sözdizimi ağaçları, derlemeleri, simgeler, anlam modellerine ve karşılaştığınız her veri yapısı için geçerlidir. Varolan yapıları değiştirme yerine API'ler belirtilen farklar eski olanlara göre yeni nesneler oluşturur. Bu kavram dönüştürmeleri kullanma yeni ağaçları oluşturmak için sözdizimi ağacı için geçerlidir.

## <a name="create-and-transform-trees"></a>Oluşturma ve ağaçları dönüştürme

Sözdizimi dönüştürmeleri için iki stratejiler birini seçin. **Fabrika yöntemleri** değiştirmek için belirli düğümler veya yeni kod eklemek istediğiniz belirli konumlara aradığınız olduğunda en iyi şekilde kullanılır. **Yazıcılar** olan kodu, desenler için tüm proje tarama istediğinizde iyi değiştirmek ister.

### <a name="create-nodes-with-factory-methods"></a>Fabrika yöntemleriyle düğümleri oluşturma

İlk sözdizimi dönüştürme Fabrika yöntemleri gösterir. Değiştir oluşturacağız bir `using System.Collections;` deyimiyle bir `using System.Collections.Generic;` deyimi. Bu örnek nasıl oluşturacağınızı gösterir <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxNode?displayProperty=nameWithType> kullanarak nesneleri <xref:Microsoft.CodeAnalysis.CSharp.SyntaxFactory?displayProperty=nameWithType> Fabrika yöntemleri. Her tür için **düğümü**, **belirteci**, veya **trivia** bu türünün bir örneği oluşturan bir Üreteç yöntemi yoktur. Hiyerarşik olarak aşağıdan yukarıya çıktısından düğümler tarafından sözdizimi ağaçları oluşturun. Ardından, var olan dönüştürme program varolan düğümleri oluşturduğunuz yeni bir ağacı ile değiştirerek.

Visual Studio'yu açın ve yeni C# oluşturma **tek başına kod analizi aracı** projesi. Visual Studio'da, **dosya** > **yeni* > **proje** yeni proje iletişim kutusu görüntülemek için. Altında **Visual C#** > **genişletilebilirlik** seçin bir **tek başına kod analizi aracı**. Bu hızlı başlangıç iki örnek proje yok, bu nedenle çözüm adı **SyntaxTransformationQuickStart**ve proje adı **ConstructionCS**. **Tamam**'ı tıklatın.

Bu proje kullanıyor <xref:Microsoft.CodeAnalysis.CSharp.SyntaxFactory?displayProperty=nameWithType> sınıfı yöntemlerinin oluşturmak için bir <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax?displayProperty=nameWithType> temsil eden `System.Collections.Generic` ad alanı.

Aşağıdakileri ekleyin using yönergesi üstüne `Program.cs` Fabrika yöntemlerini içeri aktarmak için dosya <xref:Microsoft.CodeAnalysis.CSharp.SyntaxFactory> sınıfı ve yöntemlerinin <xref:System.Console> böylece bunları daha sonra uygun olmadan kullanabilirsiniz:

[!code-csharp[import the SyntaxFactory class](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#StaticUsings "import the Syntax Factory class and the System.Console class")]

Oluşturacağınız **adı sözdizimi düğümleri** temsil eden ağaç oluşturmak için `using System.Collections.Generic;` deyimi. <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax> C# ' ta görünen adları dört tür için temel sınıftır. Bu dört tür adları birlikte C# dilinde görünebilir herhangi bir ad oluşturmak için Oluştur:

* <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax?displayProperty=nameWithType>, basit tek tanımlayıcı adları gibi temsil eden `System` ve `Microsoft`.
* <xref:Microsoft.CodeAnalysis.CSharp.Syntax.GenericNameSyntax?displayProperty=nameWithType>, temsil eden bir genel türü veya yöntemi adı gibi `List<int>`.
* <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax?displayProperty=nameWithType>, formun tam adını temsil eden `<left-name>.<right-identifier-or-generic-name>` gibi `System.IO`.
* <xref:Microsoft.CodeAnalysis.CSharp.Syntax.AliasQualifiedNameSyntax?displayProperty=nameWithType>, diğer adı bu tür bir derleme extern kullanarak adı temsil eden bir `LibraryV2::Foo`.

Kullandığınız <xref:Microsoft.CodeAnalysis.CSharp.SyntaxFactory.IdentifierName(System.String)> yöntemi oluşturmak için bir <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax> düğümü. Aşağıdaki kodu ekleyin, `Main` yönteminde `Program.cs`:

[!code-csharp[create the system identifier](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#CreateIdentifierName "Create and display the system name identifier")]

Önceki kod oluşturur bir <xref:Microsoft.CodeAnalysis.CSharp.Syntax.IdentifierNameSyntax> nesne ve değişkenine atar `name`. Birçok Roslyn API'leri iş ile ilgili türleri kolaylaştırmak için temel sınıflar döndür. Değişkeni `name`, bir <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax>, oluşturma gibi yeniden <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax>. Tür çıkarımı örneği oluşturmak gibi kullanmayın. Bu proje bu adımda otomatikleştirmek.

Adı oluşturduğunuzu düşünün. Şimdi, daha fazla düğüm ağacına oluşturarak oluşturmak için zaman olan bir <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax>. Yeni ağaç kullanan `name` adı ve yeni bir solundaki olarak <xref:Microsoft.CodeAnalysis.CSharp.Syntax.IdentifierNameSyntax> için `Collections` ad alanı sağ tarafındaki olarak <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax>. Aşağıdaki kodu ekleyin `program.cs`:

[!code-csharp[create the collections identifier](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#CreateQualifiedIdentifierName "Build the System.Collections identifier")]

Kodu yeniden çalıştırın ve sonuçlarını görebilirsiniz. Kodun temsil ettiği düğümler ağacı oluşturmakta olduğunuz. Derleme için bu deseni devam edeceğiz <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax> ad alanı için `System.Collections.Generic`. Aşağıdaki kodu ekleyin `Program.cs`:

[!code-csharp[create the full identifier](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#CreateFullNamespace "Build the System.Collections.Generic identifier")]

Yeniden, olduğunuz yapı eklemek için kodu için ağacı görmek için programını çalıştırın.

### <a name="create-a-modified-tree"></a>Değiştirilen ağacı oluşturma

Bir ifade içeren bir kısa sözdizimi ağacı temel aldık. Yeni bir düğüm oluşturmak için tek deyimleri veya diğer küçük kod blokları oluşturmak için doğru seçim apı'leridir. Ancak, daha büyük kod bloklarını oluşturmak için düğümleri değiştirin veya varolan bir ağacına düğümlerini eklemek yöntemleri kullanmanız gerekir. Sözdizimi ağacı değişmez olduğunu unutmayın. **Sözdizimi API** yapım sonra varolan bir sözdizimi ağacında değiştirmek için herhangi bir mekanizma sağlamaz. Bunun yerine, yeni ağaçları var olanları değişikliklere göre üretmek yöntemleri sağlar. `With*` yöntemleri öğesinden türetilen somut sınıflar tanımlanmış <xref:Microsoft.CodeAnalysis.SyntaxNode> veya bildirilen genişletme yöntemleri <xref:Microsoft.CodeAnalysis.SyntaxNodeExtensions> sınıfı. Bu yöntemler, var olan bir düğümün alt özelliklerine değişiklikleri uygulayarak yeni bir düğüm oluşturun. Ayrıca, <xref:Microsoft.CodeAnalysis.SyntaxNodeExtensions.ReplaceNode%2A> genişletme yöntemi, bir alt ağacı alt düğümünde değiştirmek için kullanılabilir. Bu yöntem aynı zamanda yeni oluşturulan alt işaret edecek şekilde üst güncelleştirir ve bu işlem tüm ağacı - olarak da bilinen bir işlem yinelenir _re spining_ ağacı.

(Küçük) programının tamamını temsil eden bir ağaç oluşturmak ve sonra değiştirmek için sonraki adım olacaktır. Aşağıdaki kodu başlangıcına ekleyin `Program` sınıfı:

[!code-csharp[create a parse tree](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#DeclareSampleCode "Create a tree that represents a small program")]

> [!NOTE]
> Kod örneği kullanan `System.Collections` ad alanı ve `System.Collections.Generic` ad alanı.

Ardından, altına aşağıdaki kodu ekleyin `Main` yöntemi metni ayrıştırma ve bir ağaç oluşturmak için:

[!code-csharp[create a parse tree](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#CreateParseTree "Create a tree that represents a small program")]

Bu örnekte <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax.WithName(Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax)?displayProperty=NameWithType> yöntemi adını değiştirmek için bir <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax> önceki kodda oluşturulan bir düğümle.

Yeni bir <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax> düğümünü kullanarak <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax.WithName(Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax)> güncelleştirmek için yöntemi `System.Collections` önceki kodda oluşturulan adıyla adı. ' In altına aşağıdaki kodu ekleyin `Main` yöntemi:

[!code-csharp[create a new subtree](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#BuildNewUsing "Create the subtree with the replaced namespace")]

Programını çalıştırın ve çıktıyı dikkatle inceleyin. `newusing` Kök ağacında yerleştirilen kurmadı. Özgün ağaç değişmediğinden.

Aşağıdaki kodu kullanarak eklemek <xref:Microsoft.CodeAnalysis.SyntaxNodeExtensions.ReplaceNode%2A> yeni bir ağacı oluşturmak için genişletme yöntemi. Yeni ağaç varolan alma güncelleştirilmiş ile değiştirerek sonucudur `newUsing` düğümü. Bu yeni ağaç varolan atamak `root` değişkeni:

[!code-csharp[create a new root tree](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#TransformTree "Create the transformed root tree with the replaced namespace")]

Programı yeniden çalıştırın. Ağaç artık doğru şekilde içe aktarır bu kez `System.Collections.Generic` ad alanı.

### <a name="transform-trees-using-syntaxrewriters"></a>Ağaçları kullanarak dönüştürme `SyntaxRewriters`

`With*` Ve <xref:Microsoft.CodeAnalysis.SyntaxNodeExtensions.ReplaceNode%2A> yöntemleri sağlayan bir sözdizimi ağacı tek tek dallarını dönüştürmek için uygun anlamına gelir. <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter?displayProperty=nameWithType> Sınıfı, bir sözdizimi ağacında birden çok dönüşümleri gerçekleştirir. <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter?displayProperty=nameWithType> Öğesinin bir alt sınıfıdır <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor%601?displayProperty=nameWithType>. <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter> Belirli bir türüne dönüştürme uygulanan <xref:Microsoft.CodeAnalysis.SyntaxNode>. Birden çok tür dönüştürmeleri uygulayabilirsiniz <xref:Microsoft.CodeAnalysis.SyntaxNode> sözdizimi ağacında göründükleri her yerde nesneleri. Bu hızlı başlangıç ikinci projesinde, bir komut satırı açık türleri tür çıkarımı herhangi bir yerde kullanılabilir yerel değişken bildirimlerinde kaldıran yeniden düzenleme oluşturur.

Yeni C# oluşturma **tek başına kod analizi aracı** projesi. Visual Studio'da sağ `SyntaxTransformationQuickStart` çözüm düğümü. Seçin **Ekle** > **yeni proje** görüntülemek için **yeni proje iletişim kutusu**. Altında **Visual C#** > **genişletilebilirlik**, seçin **tek başına kod analizi aracı**. Projenizin adı `TransformationCS` ve Tamam'ı tıklatın.

Öğesinden türeyen bir sınıf oluşturmak için ilk adımdır <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter> , dönüşümleri gerçekleştirir. Yeni bir sınıf dosyası projeye ekleyin. Visual Studio'da, **proje** > **sınıfı Ekle...** . İçinde **Yeni Öğe Ekle** iletişim türü `TypeInferenceRewriter.cs` dosya adı olarak.

Aşağıdaki yönergeleri kullanarak `TypeInferenceRewriter.cs` dosyası:

[!code-csharp[add necessary usings](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#AddUsings "Add required usings")]

Ardından, olun `TypeInferenceRewriter` sınıfını genişleten <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter> sınıfı:

[!code-csharp[add base class](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#BaseClass "Add base class")]

Tutmak için özel bir salt okunur alanı bildirmek için aşağıdaki kodu ekleyin bir <xref:Microsoft.CodeAnalysis.SemanticModel> ve oluşturucuda başlatma. Tür çıkarımı kullanıldığı daha sonra belirlemek için bu alanı gerekir:

[!code-csharp[initialize members](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#Construction "Declare and initialize member variables")]

Geçersiz kılma <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter.VisitLocalDeclarationStatement(Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax)> yöntemi:

```C#
public override SyntaxNode VisitLocalDeclarationStatement(LocalDeclarationStatementSyntax node)
{

}
```

> [!NOTE]
> Birçok Roslyn API'leri döndürülen gerçek çalışma zamanı türlerinin temel sınıfları dönüş türleri bildirin. n birçok senaryo, bir düğümü türü başka bir düğümü türü tarafından tamamen - değiştirilebilir veya bile kaldırılır. Bu örnekte, <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter.VisitLocalDeclarationStatement(Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax)> yöntemi döndürür bir <xref:Microsoft.CodeAnalysis.SyntaxNode>, türetilen tür yerine <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax>. Bu yeniden yazan yeni döndürür <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> düğümü var olan bir temel.

Bu hızlı başlangıç yerel değişken bildirimleri işler. Bu diğer bildirimleri gibi genişletebilirsiniz `foreach` döngüler, `for` döngüler, LINQ ifadeleri ve lambda ifadeleri. Ayrıca bu yeniden yazan yalnızca basit form bildirimleri dönüştüren:

```csharp
Type variable = expression;
```

Kendi kendinize araştırmak istiyorsanız, bu tür bir değişken bildirimleri için tamamlanan örnek genişletme düşünün:

```csharp
// Multiple variables in a single declaration.
Type variable1 = expression1,
     variable2 = expression2;
// No initializer.
Type variable;
```

Gövdesi için aşağıdaki kodu ekleyin `VisitLocalDeclarationStatement` bu formların bildirimlerinin yeniden yazma işlemi atlamayı yöntemi:

[!code-csharp[exclude other declarations](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#Exclusions "Exclude variables declarations not processed by this sample")]

Hiçbir yeniden yazma işlemi döndürerek gerçekleşir, yöntemi gösterir `node` değiştirilmemiş parametresi. Bu hiçbiri varsa `if` ifadesi true, başlatma olası bildirimiyle düğümünü temsil eder. Bildiriminde belirtilen tür adı ayıklamak için bu deyimleri ekleyin ve kullanarak bağlamak <xref:Microsoft.CodeAnalysis.SemanticModel> alan bir tür simgesi almak için:

[!code-csharp[extract type name](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#ExtractTypeSymbol "Extract the type name specified by the declaration")]

Şimdi, başlatıcı ifade bağlamak için bu bildirimi ekleyin:

[!code-csharp[bind initializer](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#BindInitializer "Bind the initializer expressions")]

Son olarak, aşağıdaki ekleyin `if` varolan tür adıyla değiştirdiğinizden deyimi `var` Başlatıcı ifade türü belirtilen tür eşleşirse anahtar sözcüğü:

[!code-csharp[ReplaceNode](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#BindInitializer "Replace the initializer node")]

Koşullu gerekir çünkü bildirimi bir temel sınıf veya arabirim Başlatıcı ifadeyi dönüştürmek. İstenirse, sol ve sağ taraftaki atama türleri eşleşmiyor. Bu durumlarda açık tür kaldırma programı semantiği değiştirirsiniz. `var` çünkü bir anahtar sözcük yerine bir tanımlayıcı olarak belirtilen `var` bağlamsal bir anahtardır. Eski tür adı baştaki ve sondaki trivia (boşluk) aktarıldığı `var` dikey boşluk ve girinti korumak için anahtar sözcüğü. Kullanmak daha basittir `ReplaceNode` yerine `With*` dönüştürmek için <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> tür adı gerçekte bildirimi deyiminin en alt olduğundan.

Seçtiğiniz tamamlandı `TypeInferenceRewriter`. Şimdi geri dönün, `Program.cs` örnek tamamlamak için dosya. Bir test oluşturmak <xref:Microsoft.CodeAnalysis.Compilation> ve elde <xref:Microsoft.CodeAnalysis.SemanticModel> almaktır. Kullanan <xref:Microsoft.CodeAnalysis.SemanticModel> denemek için `TypeInferenceRewriter`. Bu adım son gerçekleştirirsiniz. Bu sırada, test derleme temsil eden bir yer tutucu değişken bildirin:

[!code-csharp[DeclareCompilation](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/Program.cs#DeclareTestCompilation "Declare the test compilation")]

Biraz duraklatma sonra Raporlama görünür bir hata dalgalı görmelisiniz hiçbir `CreateTestCompilation` yöntem vardır. Basın **Ctrl + nokta** ampul açıp çağırmak için Enter tuşuna basın **Generate Method Stub** komutu. Bu komut için bir yöntem saplama oluşturacak `CreateTestCompilation` yönteminde `Program` sınıfı. Bu yöntemi, daha sonra doldurmak için geri alınması:

![Kullanımdan Oluştur C# yöntemi](./media/syntax-transformation/generate-from-usage.png)

Her yineleme için aşağıdaki kodu yazma <xref:Microsoft.CodeAnalysis.SyntaxTree> test <xref:Microsoft.CodeAnalysis.Compilation>. Her biri için yeni bir başlatma `TypeInferenceRewriter` ile <xref:Microsoft.CodeAnalysis.SemanticModel> o ağaç için:

[!code-csharp[IterateTrees](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/Program.cs#IterateTrees "Iterate all the source trees in the test compilation")]

İçinde `foreach` deyimi, oluşturduğunuz her kaynak ağaçta dönüştürme gerçekleştirmek için aşağıdaki kodu ekleyin. Tüm düzenlemeleri yapılmışsa bu kodu yeni dönüştürülmüş ağacı koşullu olarak yazar. Tür çıkarımı kullanarak basitleştirilmiş bir veya daha fazla yerel değişken bildirimleri karşılaşırsa, yeniden yazan yalnızca bir ağaç değiştirmeniz gerekir:

[!code-csharp[TransformTrees](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/Program.cs#TransformTrees "Transform and save any trees that are modified by the rewriter")]

Dalgalı çizgiler altında görmelisiniz `File.WriteAllText` kodu. Ampul seçin ve gerekli ekleyin `using System.IO;` deyimi.

Bitmek üzere! Bir kez sol adım vardır: bir test oluşturma <xref:Microsoft.CodeAnalysis.Compilation>. Tür çıkarımı hiç bu hızlı başlangıç sırasında kullanmakta henüz olduğundan, mükemmel bir test çalışması yapmış. Ne yazık ki, C# proje dosyasından bir derleme oluşturma, bu kılavuz kapsamında değildir. Ancak Neyse ki, yönergeleri dikkatle takip, soluk var. Değiştir `CreateTestCompilation` aşağıdaki kod ile yöntemi. Bu hızlı başlangıç içinde açıklanan proje tesadüfen eşleşen bir test derleme oluşturur:

[!code-csharp[CreateTestCompilation](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/Program.cs#CreateTestCompilation "Create a test compilation using the code written for this quickstart.")]

Parmakları arası ve projeyi çalıştırın. Visual Studio'da, **hata ayıklama** > **hata ayıklamayı Başlat**. Visual Studio tarafından projenizi dosyalarda değişen istenir. Tıklayın "**Tümüne Evet**" değiştirilen dosyalar yeniden yüklemek için. Bunları, awesomeness izlemek için inceleyin. Kod bu tüm açık ve yedek tür tanımlayıcıları görünür ne kadar temizleyici unutmayın.

Tebrikler! Kullandığınız **derleyici API'leri** kendi belirli söz dizimi desenler için C# projesinde tüm dosyaları arayan yeniden düzenleme yazmak için bu düzenlere eşleştiğinden ve bunu dönüştüren kaynak kodu semantiği analiz eder. Artık resmi olarak yazar yeniden düzenleme!