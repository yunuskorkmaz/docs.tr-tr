---
title: Söz dizimi dönüştürme (Roslyn API'leri) ile çalışmaya başlama
description: Geçiş, sorgulama ve söz dizimi ağacı walking giriş.
ms.date: 06/01/2018
ms.custom: mvc
ms.openlocfilehash: c372b1ba1e08a7d3b57ceea0d4449d03e55a39cf
ms.sourcegitcommit: 67de6cb5dd66a19f2180ba7e4d7aecc697f8a963
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44342884"
---
# <a name="get-started-with-syntax-transformation"></a>Söz dizimi dönüştürme ile çalışmaya başlama

Bu öğreticide kavrama oluşturur ve teknikleri incelediniz içinde [söz dizimi Analizi ile çalışmaya başlama](syntax-analysis.md) ve [anlam Analizi ile çalışmaya başlama](semantic-analysis.md) hızlı başlangıçları. Henüz yapmadıysanız, bunu başlamadan önce bu hızlı başlangıçların tamamlamanız gerekir.

Bu hızlı başlangıçta, oluşturma ve söz dizimi ağacı dönüştürmeye yönelik teknikleri keşfedin. Önceki hızlı başlangıçlar, öğrendiğiniz teknikleri ile birlikte, ilk komut satırı yeniden düzenleme oluşturun!

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

## <a name="immutability-and-the-net-compiler-platform"></a>Değiştirilemezliği ve .NET derleyici platformu

**Değiştirilemezlik** olan .NET derleyici platformu temel de aynen geçerli. Sabit veri yapıları, oluşturuldukları sonra değiştirilemez. Sabit veri yapılarını güvenli bir şekilde paylaşılan ve aynı anda birden fazla tüketici tarafından analiz edilir. Tek bir tüketici başka bir öngörülemeyen şekillerde etkiler tehlike yoktur. Çözümleyici kilit veya diğer eşzamanlılık ölçüleri gerek yoktur. Bu kural, söz dizimi ağacı, derlemeleri, simgeler, anlam modelleri ve karşılaştığınız her veri yapısı için geçerlidir. Mevcut yapıları değiştirmek yerine yeni nesneleri eskilerle belirtilen farklılıklar göre API'ler oluşturun. Bu kavramı dönüştürmeleri kullanma yeni ağacı oluşturmak için sözdizimi ağacı için geçerlidir.

## <a name="create-and-transform-trees"></a>Oluşturma ve ağaçları dönüştürün

Söz dizimi dönüştürmeleri için iki stratejileri birini seçin. **Fabrika yöntemleri** değiştirmek için belirli düğümler ya da yeni kod eklemek istediğiniz belirli konumları için arama yapıyorsanız, en iyi şekilde kullanılır. **Yazıcılar** olan bir projenin tamamı, kod desenleri için tarama istediğinizde iyi istediğiniz değiştirin.

### <a name="create-nodes-with-factory-methods"></a>Düğümleri Fabrika yöntemleri ile oluşturma

İlk söz dizimi dönüşümü Fabrika yöntemleri gösterir. Değiştirilecek gideceğinizi bir `using System.Collections;` deyimiyle bir `using System.Collections.Generic;` deyimi. Bu örnek nasıl oluşturabileceğinizi gösterir <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxNode?displayProperty=nameWithType> kullanarak nesneleri <xref:Microsoft.CodeAnalysis.CSharp.SyntaxFactory?displayProperty=nameWithType> Fabrika yöntemleri. Her tür için **düğüm**, **belirteci**, veya **Meraklısına Notlar** o türün bir örneği oluşturan bir Üreteç yöntemi yoktur. Hiyerarşik olarak aşağıdan yukarıya çıktısından düğümler tarafından söz dizimi ağacı oluşturmak. Ardından, var olan dönüştürme programı var olan düğümleri oluşturduğunuz yeni ağaçta değiştirdiğiniz.

Visual Studio'yu başlatın ve yeni C# oluşturma **tek başına kod analizi aracı** proje. Visual Studio'da **dosya** > **yeni* > **proje** yeni proje iletişim kutusu görüntülenecek. Altında **Visual C#** > **genişletilebilirlik** seçin bir **tek başına kod analizi aracı**. Bu hızlı başlangıçta iki örnek projeler varsa, bu nedenle çözümünü arlandırın **SyntaxTransformationQuickStart**, projeyi adlandırın **ConstructionCS**. **Tamam**'ı tıklatın.

Bu proje kullanan <xref:Microsoft.CodeAnalysis.CSharp.SyntaxFactory?displayProperty=nameWithType> sınıfı oluşturmak için yöntemleri bir <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax?displayProperty=nameWithType> temsil eden `System.Collections.Generic` ad alanı.

Aşağıdakileri ekleyin üstüne yönergesi kullanarak `Program.cs` Fabrika yöntemleri içeri aktarmak için dosya <xref:Microsoft.CodeAnalysis.CSharp.SyntaxFactory> sınıfı ve yöntemlerinin <xref:System.Console> böylece bunları daha sonra bunları nitelemeden kullanabilirsiniz:

[!code-csharp[import the SyntaxFactory class](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#StaticUsings "import the Syntax Factory class and the System.Console class")]

Oluşturacağınız **ad sözdizimi düğümleri** temsil eden ağacı oluşturmak için `using System.Collections.Generic;` deyimi. <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax> dört tür C# içinde görünen adları için temel sınıftır. Bu dört tür adları birlikte C# dilinde görünebilir herhangi bir ad oluşturmak için Araçlar:

* <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax?displayProperty=nameWithType>, basit bir tek tanımlayıcı adları gibi temsil eden `System` ve `Microsoft`.
* <xref:Microsoft.CodeAnalysis.CSharp.Syntax.GenericNameSyntax?displayProperty=nameWithType>, aşağıdaki gibi genel bir tür veya yöntem ad temsil `List<int>`.
* <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax?displayProperty=nameWithType>, formun tam adını temsil eden `<left-name>.<right-identifier-or-generic-name>` gibi `System.IO`.
* <xref:Microsoft.CodeAnalysis.CSharp.Syntax.AliasQualifiedNameSyntax?displayProperty=nameWithType>, derleme extern diğer adı gibi kullanarak adı temsil eden bir `LibraryV2::Foo`.

Kullandığınız <xref:Microsoft.CodeAnalysis.CSharp.SyntaxFactory.IdentifierName(System.String)> yöntemi oluşturmak için bir <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax> düğümü. Aşağıdaki kodu ekleyin, `Main` yönteminde `Program.cs`:

[!code-csharp[create the system identifier](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#CreateIdentifierName "Create and display the system name identifier")]

Yukarıdaki kod oluşturur bir <xref:Microsoft.CodeAnalysis.CSharp.Syntax.IdentifierNameSyntax> nesnesi ve bir değişkene atar `name`. Roslyn API'leri birçoğu, iş ile ilgili türleri daha kolay hale getirmek için temel sınıfları döndürür. Değişken `name`e <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax>, derleme sırasında yeniden kullanılabilir <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax>. Örneği oluşturmak gibi tür çıkarımı kullanmayın. Bu proje o adımda otomatikleştirin.

Adı oluşturdunuz. Daha fazla düğüm oluşturarak ağacına oluşturmak için zamanı artık, bir <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax>. Yeni ağaç kullanan `name` adını ve yeni bir sol olarak <xref:Microsoft.CodeAnalysis.CSharp.Syntax.IdentifierNameSyntax> için `Collections` sağ tarafı olarak ad alanı <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax>. Aşağıdaki kodu ekleyin `program.cs`:

[!code-csharp[create the collections identifier](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#CreateQualifiedIdentifierName "Build the System.Collections identifier")]

Kodu yeniden çalıştırmak ve sonuçlarını görebilirsiniz. Kod temsil eden bir ağaç düğümleri oluşturuyorsunuz. Bu düzen oluşturmak için devam edeceğiz <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax> ad alanı için `System.Collections.Generic`. Aşağıdaki kodu ekleyin `Program.cs`:

[!code-csharp[create the full identifier](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#CreateFullNamespace "Build the System.Collections.Generic identifier")]

Yeniden olduğunuz, ağacında eklenecek kodu görmek için programı çalıştırın.

### <a name="create-a-modified-tree"></a>Değiştirilmiş bir ağaç oluşturun

Bir ifade içeren bir küçük söz dizimi ağacı oluşturdunuz. Yeni düğümler oluşturma API'ları, tek deyimler veya diğer küçük kod blokları oluşturmak için doğru seçimdir. Ancak, daha büyük kod bloklarını oluşturmak için düğümleri değiştirin veya varolan bir ağacına düğümlerini eklemek yöntemlerini kullanmanız gerekir. Sözdizimi ağacı sabit olduğunu unutmayın. **Söz dizimi API** var olan bir söz dizimi ağacı oluşturma sonra değiştirmek için herhangi bir mekanizma sağlamaz. Bunun yerine, mevcut olanlara değişikliklere göre yeni ağaçları oluşturan yöntemleri sağlar. `With*` öğesinden türetilen somut sınıflar, yöntemlerin tanımlandığı <xref:Microsoft.CodeAnalysis.SyntaxNode> veya genişletme yöntemleri bildirilen <xref:Microsoft.CodeAnalysis.SyntaxNodeExtensions> sınıfı. Bu yöntemler, mevcut bir düğümün alt özellikleri için değişiklikleri uygulayarak yeni bir düğüm oluşturur. Ayrıca, <xref:Microsoft.CodeAnalysis.SyntaxNodeExtensions.ReplaceNode%2A> genişletme yöntemi, bir alt düğüm ağaçtaki değiştirmek için kullanılabilir. Bu yöntem ayrıca üst yeni oluşturulan alt öğeye işaret edecek şekilde güncelleştirir ve tüm ağacı - olarak da bilinen bir işlem bu işlemi yineler _re spining_ ağaç.

Sonraki adım, bir programın tamamındaki (küçük) temsil eden bir ağaç oluşturmak ve değiştirmek sağlamaktır. Aşağıdaki kodu ekleyin başlangıcına `Program` sınıfı:

[!code-csharp[create a parse tree](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#DeclareSampleCode "Create a tree that represents a small program")]

> [!NOTE]
> Örnek kod `System.Collections` ad alanı değil `System.Collections.Generic` ad alanı.

Ardından, altına aşağıdaki kodu ekleyin `Main` yöntemi metni ayrıştırılamadı ve bir ağaç oluşturun:

[!code-csharp[create a parse tree](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#CreateParseTree "Create a tree that represents a small program")]

Bu örnekte <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax.WithName(Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax)?displayProperty=NameWithType> adını değiştirmek için yöntemi bir <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax> önceki kodda oluşturulan tek düğüm.

Yeni bir <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax> düğümü kullanan <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax.WithName(Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax)> güncelleştirilecek yöntemi `System.Collections` önceki kodda oluşturduğunuz adıyla adı. ' In altına aşağıdaki kodu ekleyin `Main` yöntemi:

[!code-csharp[create a new subtree](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#BuildNewUsing "Create the subtree with the replaced namespace")]

Programı çalıştırın ve çıktıyı dikkatle inceleyin. `newusing` Kök ağacında yerleştirilen edilmemiş. Özgün ağaç değişmedi.

Aşağıdaki kodu kullanarak ekleme <xref:Microsoft.CodeAnalysis.SyntaxNodeExtensions.ReplaceNode%2A> yeni bir ağaç oluşturmak için genişletme yöntemi. Yeni ağaç mevcut içeri aktarma güncelleştirilmiş ile değiştirerek sonucudur `newUsing` düğümü. Bu yeni ağaç varolan atadığınız `root` değişkeni:

[!code-csharp[create a new root tree](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#TransformTree "Create the transformed root tree with the replaced namespace")]

Programı yeniden çalıştırın. Bu süre ağaç artık doğru şekilde içeri aktarır `System.Collections.Generic` ad alanı.

### <a name="transform-trees-using-syntaxrewriters"></a>Ağaçları kullanarak dönüştürme `SyntaxRewriters`

`With*` Ve <xref:Microsoft.CodeAnalysis.SyntaxNodeExtensions.ReplaceNode%2A> yöntemleri sağlayan bireysel dalları söz dizimi ağacı dönüştürmek için kullanışlı anlamına gelir. <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter?displayProperty=nameWithType> Sınıfı bir sözdizimi ağacında birden çok dönüşümleri gerçekleştirir. <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter?displayProperty=nameWithType> Sınıftır öğesinin <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor%601?displayProperty=nameWithType>. <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter> Belirli bir türüne dönüştürme uygulanan <xref:Microsoft.CodeAnalysis.SyntaxNode>. Dönüştürmeleri çoklu türleri için geçerli <xref:Microsoft.CodeAnalysis.SyntaxNode> söz dizimi ağacı içinde göründükleri yere nesneleri. İkinci projenin Bu hızlı başlangıçta, bir komut satırı tür çıkarımı, her yerde kullanılabilir yerel değişken bildirimlerinde türleri açık kaldıran yeniden düzenleme oluşturur.

Yeni C# oluşturma **tek başına kod analizi aracı** proje. Visual Studio'da sağ `SyntaxTransformationQuickStart` çözüm düğümü. Seçin **Ekle** > **yeni proje** görüntülenecek **yeni proje iletişim kutusu**. Altında **Visual C#** > **genişletilebilirlik**, seçin **tek başına kod analizi aracı**. Projenizi adlandırın `TransformationCS` ve Tamam'a tıklayın.

Türetilen bir sınıf oluşturmak için ilk adımıdır <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter> Bağlantılarınızdaki gerçekleştirilecek. Projeye yeni bir sınıf dosyası ekleyin. Visual Studio'da **proje** > **sınıfı Ekle...** . İçinde **Yeni Öğe Ekle** iletişim kutusuna `TypeInferenceRewriter.cs` dosya adı olarak.

Aşağıdaki using yönergelerini `TypeInferenceRewriter.cs` dosyası:

[!code-csharp[add necessary usings](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#AddUsings "Add required usings")]

Ardından, olun `TypeInferenceRewriter` sınıfını genişleten <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter> sınıfı:

[!code-csharp[add base class](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#BaseClass "Add base class")]

Tutmak için özel bir salt okunur alanı bildirmek için aşağıdaki kodu ekleyin bir <xref:Microsoft.CodeAnalysis.SemanticModel> ve oluşturucuda başlatır. Daha sonra tür çıkarımı kullanıldığı belirlemek için bu alana ihtiyacınız olacak:

[!code-csharp[initialize members](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#Construction "Declare and initialize member variables")]

Geçersiz kılma <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter.VisitLocalDeclarationStatement(Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax)> yöntemi:

```C#
public override SyntaxNode VisitLocalDeclarationStatement(LocalDeclarationStatementSyntax node)
{

}
```

> [!NOTE]
> Roslyn API'leri birçoğu, döndürülen gerçek çalışma zamanı türlerinin temel sınıflardır dönüş türlerini bildirir. n birçok senaryo, bir tür düğümünün başka tür bir düğüm tarafından tamamen - değiştirilebilir veya bile kaldırıldı. Bu örnekte, <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter.VisitLocalDeclarationStatement(Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax)> yöntemi döndürür bir <xref:Microsoft.CodeAnalysis.SyntaxNode>, türetilmiş bir tür yerine <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax>. Bu dosyaları yeni bir döndürür <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> düğüm üzerinde var olan bir alan.

Bu hızlı başlangıçta, yerel değişken bildirimlerini işler. Bunu diğer bildirimlerine gibi genişletilebiliyordu `foreach` döngüleri `for` döngüleri LINQ ifadeleri ve lambda ifadeleri. Ayrıca bu dosyaları en basit şekliyle bildirimleri yalnızca dönüştürür:

```csharp
Type variable = expression;
```

Kendi kendinize araştırmak istiyorsanız, bu tür bir değişken bildirimleri için tamamlanan örnek genişletme göz önünde bulundurun:

```csharp
// Multiple variables in a single declaration.
Type variable1 = expression1,
     variable2 = expression2;
// No initializer.
Type variable;
```

Gövdesi için aşağıdaki kodu ekleyin `VisitLocalDeclarationStatement` biçimlerinden birini bildirimleri yeniden yazma atlamak için yöntemi:

[!code-csharp[exclude other declarations](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#Exclusions "Exclude variables declarations not processed by this sample")]

Hiçbir yeniden yazma döndürerek gerçekleşir, yöntemi gösterir `node` değiştirilmemiş parametresi. Bunların hiçbiri, `if` ifadelerdir true, başlatma olası bir bildirimle düğümünü temsil eder. Belirtiminde belirtilen tür adı ayıklamak için aşağıdaki deyimleri ekleyin ve onu kullanarak bağlama <xref:Microsoft.CodeAnalysis.SemanticModel> alan bir tür simgesi almak için:

[!code-csharp[extract type name](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#ExtractTypeSymbol "Extract the type name specified by the declaration")]

Şimdi, başlatıcı ifadesinin bağlamak için bu bildirimi ekleyin:

[!code-csharp[bind initializer](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#BindInitializer "Bind the initializer expressions")]

Son olarak, aşağıdaki ekleyin `if` mevcut tür adıyla değiştirilecek deyimi `var` Başlatıcı ifadesinin türü belirtilen tür eşleşiyorsa anahtar sözcüğü:

[!code-csharp[ReplaceNode](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#BindInitializer "Replace the initializer node")]

Koşul bildirimi Başlatıcı ifadesinin bir temel sınıf veya arabirim için tür dönüştürme için gereklidir. İstenirse, sol ve sağ taraftaki atama türleri eşleşmiyor. Bu gibi durumlarda açık tür kaldırma programı semantiği değiştirirsiniz. `var` bir anahtar sözcüğü yerine bir tanımlayıcı olarak çünkü belirtilen `var` bağlamsal bir anahtar sözcüktür. Baştaki ve sondaki trivia (boşluk) eski tür adına aktarılırken `var` dikey boşluk ve girinti korumak için anahtar sözcüğü. Kullanmak daha kolaydır `ReplaceNode` yerine `With*` dönüştürmek için <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> gerçekten bildirim deyiminin en alt tür adı olduğu için.

Seçtiğiniz tamamlandı `TypeInferenceRewriter`. Şimdi geri dönüp, `Program.cs` örneği tamamlamak için dosya. Test oluşturma <xref:Microsoft.CodeAnalysis.Compilation> ve elde <xref:Microsoft.CodeAnalysis.SemanticModel> almaktır. Kullanan <xref:Microsoft.CodeAnalysis.SemanticModel> denemek için `TypeInferenceRewriter`. Bu adım son yaparsınız. Bu sırada test derlemeniz temsil eden bir yer tutucu değişken bildirin:

[!code-csharp[DeclareCompilation](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/Program.cs#DeclareTestCompilation "Declare the test compilation")]

Biraz duraklattıktan sonra Raporlama görünür bir hata dalgalı görmelisiniz hiçbir `CreateTestCompilation` yöntem vardır. Basın **Ctrl + nokta** ampul açın ve ardından çağırmak için Enter tuşuna basın **metot taslağı oluşturmak** komutu. Bu komut için bir yöntem saptama oluşturacaktır `CreateTestCompilation` yönteminde `Program` sınıfı. Bu yöntemi, daha sonra doldurmak için geri dönen:

![Kullanımdan Oluştur C# yöntemi](./media/syntax-transformation/generate-from-usage.png)

Her yineleme yapmak için aşağıdaki kodu yazın <xref:Microsoft.CodeAnalysis.SyntaxTree> test <xref:Microsoft.CodeAnalysis.Compilation>. Her biri için yeni bir başlatma `TypeInferenceRewriter` ile <xref:Microsoft.CodeAnalysis.SemanticModel> ağacı için:

[!code-csharp[IterateTrees](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/Program.cs#IterateTrees "Iterate all the source trees in the test compilation")]

İçinde `foreach` deyim, oluşturduğunuz her kaynak ağacının üzerinde dönüştürmeyi gerçekleştirmek için aşağıdaki kodu ekleyin. Düzenlemeler yaptıysanız bu kod, yeni dönüştürülmüş ağacı koşullu olarak yazar. Tür çıkarımı kullanarak basitleştirilmiş bir veya daha fazla yerel değişken bildirimleri karşılaşırsa, dosyaları yalnızca bir ağaç değiştirmeniz gerekir:

[!code-csharp[TransformTrees](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/Program.cs#TransformTrees "Transform and save any trees that are modified by the rewriter")]

Altında dalgalı çizgiler görürsünüz `File.WriteAllText` kod. Ampul seçin ve gerekli Ekle `using System.IO;` deyimi.

Neredeyse hazırsınız! Bir kez sol adım vardır: test oluşturma <xref:Microsoft.CodeAnalysis.Compilation>. Tür çıkarımı hiç bu hızlı başlangıç sırasında kullandığınız henüz olduğundan, mükemmel bir test çalışması alacağımızdı. Ne yazık ki, C# proje dosyasından bir derleme oluşturma, bu kılavuzun kapsamı dışındadır değil. Neyse ki, yönergeleri dikkatle takip ediyorsanız, yoktur ancak soluk. Öğesinin içeriğini değiştirin `CreateTestCompilation` yöntemini aşağıdaki kod ile. Bu hızlı başlangıçta açıklanan proje tesadüfen eşleşen bir test derleme oluşturur:

[!code-csharp[CreateTestCompilation](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/Program.cs#CreateTestCompilation "Create a test compilation using the code written for this quickstart.")]

Parmaklarınızın arası ve projeyi çalıştırın. Visual Studio'da **hata ayıklama** > **hata ayıklamayı Başlat**. Visual Studio tarafından projenizdeki dosyaları değişen sorulması gerekir. Tıklayın "**Tümüne Evet**" değiştirilmiş dosyalar yeniden yüklemek için. Bunları, awesomeness gözlemlemek için inceleyin. Kod tüm bu açık ve gereksiz tür tanımlayıcıları görünür ne kadar temizleyici unutmayın.

Tebrikler! Kullandığınız **derleyici API'leri** kendi söz dizimsel düzenlerini, C# projesinde tüm dosyaları arayan yeniden düzenleme yazmak için bu desenleri eşleşir ve bunu dönüştüren kaynak kodu semantiği analiz eder. Artık resmi olarak yazar yeniden düzenleme!