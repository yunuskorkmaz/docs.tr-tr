---
title: 'Öğretici: İlk çözümleyicinizi ve kod düzeltmenizi yazın'
description: Bu öğretici, .NET Derleyici SDK 'yu (Roslyn API'leri) kullanarak bir çözümleyici ve kod düzeltmesi oluşturmak için adım adım yönergeler sağlar.
ms.date: 08/01/2018
ms.custom: mvc
ms.openlocfilehash: f6fc21c010f9b5fcd5e709ef822639c020a7c93b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240556"
---
# <a name="tutorial-write-your-first-analyzer-and-code-fix"></a>Öğretici: İlk çözümleyicinizi ve kod düzeltmenizi yazın

.NET Derleyici Platformu SDK, C# veya Visual Basic kodunu hedefleyen özel uyarılar oluşturmak için ihtiyacınız olan araçları sağlar. **Çözümleyiciniz,** kural ihlallerinizi tanıyan kod lar içerir. **Kod düzeltmeniz** ihlali düzelten kodu içerir. Uyguladığınız kurallar, kod yapısından kodlama stiline, adlandırma kurallarına ve daha fazlasına kadar her şey olabilir. .NET Derleyici Platformu, geliştiriciler kod yazarken analiz leri çalıştırmak için bir çerçeve sağlar ve kodu sabitlemek için tüm Visual Studio UI özellikleri: editörde squiggles gösteren, Visual Studio Hata Listesi doldurma, "ampul" oluşturma öneriler ve önerilen düzeltmelerin zengin önizlemegösteren.

Bu eğitimde, Roslyn API'lerini kullanarak bir **çözümleyici** ve beraberindeki **kod düzeltmesinin** oluşturulmasını keşfedeceksiniz. Çözümleyici, kaynak kodu çözümlemesi gerçekleştirmenin ve bir sorunu kullanıcıya bildirmenin bir yoludur. İsteğe bağlı olarak, bir çözümleyici kullanıcının kaynak kodunda yapılan bir değişikliği temsil eden bir kod düzeltmesi de sağlayabilir. Bu öğretici, `const` değiştirici kullanılarak bildirilebilen ancak olmayan yerel değişken bildirimleri bulan bir çözümleyici oluşturur. Eşlik eden kod düzeltmesi, `const` değiştiricieklemek için bu bildirimleri değiştirir.

## <a name="prerequisites"></a>Önkoşullar

- [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/#visual-studio-2017-and-other-products)
- [Visual Studio 2019](https://www.visualstudio.com/downloads)

**.NET Derleyici Platformu SDK'yı** Visual Studio Installer üzerinden yüklemeniz gerekir:

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

Çözümleyicinizi oluşturmak ve doğrulamak için birkaç adım vardır:

1. Çözümü oluşturun.
1. Çözümleyici adını ve açıklamasını kaydedin.
1. Çözümleyici uyarılarını ve önerilerini bildirin.
1. Önerileri kabul etmek için kod düzeltmesini uygulayın.
1. Birim testleri ile analizi geliştirin.

## <a name="explore-the-analyzer-template"></a>Çözümleyici şablonu keşfedin

Çözümleyiciniz, yerel sabitlere dönüştürülebilecek yerel değişken bildirimlerini kullanıcıya bildirir. Örneğin, aşağıdaki kodu göz önünde bulundurun:

```csharp
int x = 0;
Console.WriteLine(x);
```

Yukarıdaki kodda, `x` sabit bir değer atanır ve hiçbir zaman değiştirilmez. `const` Değiştirici kullanılarak bildirilebilir:

```csharp
const int x = 0;
Console.WriteLine(x);
```

Bir değişkenin sabit yapılıp yapılamayacağını belirlemek için yapılan analiz, sözdizimsal analiz, değişkenin asla yazılmamasını sağlamak için başharf ifadesinin sürekli analizi ve veri akışı analizi gerektirir. .NET Derleyici Platformu, bu çözümlemesi kolaylaştıran API'ler sağlar. İlk adım kod düzeltme projesi ile yeni bir C # **Analyzer** oluşturmaktır.

- Visual Studio'da, Yeni Proje iletişim kutusunu görüntülemek için **Dosya > Yeni > Projesi...** seçeneğini belirleyin.
- **Visual C# > Genişletilebilirlik** **altında, kod düzeltmeli Çözümleyici'yi (.NET Standart)** seçin.
- Projenize "**MakeConst**" adını ve Tamam'ı tıklatın.

Kod düzeltme şablonuna sahip çözümleyici üç proje oluşturur: biri çözümleyici ve kod düzeltmesi içerir, ikincisi birim test projesidir ve üçüncüsü VSIX projesidir. Varsayılan başlangıç projesi VSIX projesidir. VSIX projesini başlatmak için **F5** tuşuna basın. Bu, yeni çözümleyicinizi yüklemiş olan Visual Studio'nun ikinci bir örneğini başlatır.

> [!TIP]
> Çözümleyicinizi çalıştırdığınızda Visual Studio'nun ikinci bir kopyasını başlayırsınız. Bu ikinci kopya, ayarları depolamak için farklı bir kayıt defteri kovanı kullanır. Bu, Visual Studio'nun iki kopyasındaki görsel ayarları ayırt etmenizi sağlar. Visual Studio'nun deneysel çalışması için farklı bir tema seçebilirsiniz. Buna ek olarak, Visual Studio'nun deneysel çalışmasını kullanarak ayarlarınızda gezinmeyin veya Visual Studio hesabınıza giriş yapmayın. Bu ayarları farklı tutar.

Yeni başladığınız ikinci Visual Studio örneğinde, yeni bir C# Console Application projesi oluşturun (.NET Core veya .NET Framework projesi çalışacaktır - çözümleyiciler kaynak düzeyinde çalışır.) Dalgalı bir alt çizgi ile belirteci üzerinde gezinmek ve bir çözümleyici tarafından sağlanan uyarı metni görüntülenir.

Şablon, tür adının aşağıdaki şekilde gösterildiği gibi küçük harfler içerdiği her tür bildiriminde bir uyarı bildiren bir çözümleyici oluşturur:

![Çözümleyici raporlama uyarısı](media/how-to-write-csharp-analyzer-code-fix/report-warning.png)

Şablon ayrıca, küçük harf karakterleri içeren herhangi bir tür adını tüm büyük harflerle değiştiren bir kod düzeltmesi de sağlar. Önerilen değişiklikleri görmek için uyarıyla birlikte görüntülenen ampule tıklayabilirsiniz. Önerilen değişiklikleri kabul etmek, tür adını ve çözümdeki bu türe yapılan tüm başvuruları güncelleştirir. Şimdi ilk çözümleyiciyi iş başında gördüğünüze göre, ikinci Visual Studio örneğini kapatın ve çözümleyici projenize geri dönün.

Visual Studio'nun ikinci bir kopyasını başlatmak ve çözümleyicinizdeki her değişikliği test etmek için yeni kodlar oluşturmanız gerekmez. Şablon ayrıca sizin için bir birim test projesi oluşturur. Bu proje iki test içeriyor. `TestMethod1`tanılamayı tetiklemeden kodu çözümleyen bir testin tipik biçimini gösterir. `TestMethod2`tanılamayı tetikleyen bir testin biçimini gösterir ve ardından önerilen kod düzeltmesini uygular. Çözümleyicinizi ve kod düzeltmenizi oluştururken, çalışmanızı doğrulamak için farklı kod yapıları için testler yazarsınız. Analizörler için birim testleri Visual Studio ile etkileşimli olarak test etmekten çok daha hızlıdır.

> [!TIP]
> Çözümleyici birim testleri, çözümleyicinizi hangi kod oluşturmanın tetiklemesi gerektiğini ve tetiklememesi gerektiğini bildiğinizde harika bir araçtır. Visual Studio başka bir kopyasını analizör yükleme keşfetmek ve henüz düşünmemiş olabilirsiniz yapıları bulmak için harika bir araçtır.

## <a name="create-analyzer-registrations"></a>Çözümleyici kayıtları oluşturma

Şablon, `DiagnosticAnalyzer` **MakeConstAnalyzer.cs** dosyasında ilk sınıfı oluşturur. Bu ilk çözümleyici her çözümleyicinin iki önemli özelliğini gösterir.

- Her tanı çözümleyicisi, çalıştığı dili açıklayan bir `[DiagnosticAnalyzer]` öznitelik sağlamalıdır.
- Her tanı analizörü sınıftan <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer> türemelidir.

Şablon ayrıca herhangi bir çözümleyicinin parçası olan temel özellikleri de gösterir:

1. Eylemleri kaydedin. Eylemler, ihlaller için kodu incelemek için çözümleyicinizi tetikleyecek kod değişikliklerini temsil eder. Visual Studio kayıtlı bir eylemle eşleşen kod edinimi algıladığında, çözümleyicinizin kayıtlı yöntemini çağırır.
1. Tanılama oluşturun. Çözümleyiciniz bir ihlali algıladığında, Visual Studio'nun kullanıcıyı ihlali bildirmek için kullandığı bir tanılama nesnesi oluşturur.

Eylemleri metodu geçersiz <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer.Initialize(Microsoft.CodeAnalysis.Diagnostics.AnalysisContext)?displayProperty=nameWithType> kılmanızda kaydedersiniz. Bu öğreticide, yerel bildirimleri arayan **sözdizimi düğümlerini** ziyaret eder ve bunlardan hangisinin sabit değerlere sahip olduğunu görürsünüz. Bir bildirim sabit olabilirse, çözümleyiciniz bir tanı oluşturur ve raporlar.

İlk adım, bu sabitlerin "Const Yap" çözümleyicinizi göstermesi için kayıt sabitlerini ve `Initialize` yöntemini güncelleştirmektir. Dize sabitlerinin çoğu dize kaynak dosyasında tanımlanır. Daha kolay yerelleştirme için bu uygulamayı izlemeniz gerekir. **MakeConst** çözümleyici projesi için **Resources.resx** dosyasını açın. Bu, kaynak düzenleyicisini görüntüler. Dize kaynaklarını aşağıdaki gibi güncelleştirin:

- "Değişken sabit yapılabilir" olarak değiştirin. `AnalyzerTitle`
- "Sabit yapılabilir" olarak değiştirin. `AnalyzerMessageFormat`
- "Constant yap" olarak değiştirin. `AnalyzerDescription`

Ayrıca, **Access Değiştirici** açılır'ı `public`' olarak değiştirin. Bu, birim testlerinde bu sabitlerin kullanılmasını kolaylaştırır. Bitirdikten sonra, kaynak düzenleyicisi aşağıdaki şekilde görünmelidir:

![Dize kaynaklarını güncelleştirme](media/how-to-write-csharp-analyzer-code-fix/update-string-resources.png)

Kalan değişiklikler çözümleyici dosyasında dır. Visual Studio'da **MakeConstAnalyzer.cs** aç. Kayıtlı eylemi, semboller üzerinde hareket eden bir eylemden sözdiziminde hareket eden eyleme değiştirin. `MakeConstAnalyzerAnalyzer.Initialize` Yöntemde, eylemi semboller üzerinde kaydeden satırı bulun:

```csharp
context.RegisterSymbolAction(AnalyzeSymbol, SymbolKind.NamedType);
```

Aşağıdaki satırla değiştirin:

[!code-csharp[Register the node action](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstAnalyzer.cs#RegisterNodeAction "Register a node action")]

Bu değişiklikten `AnalyzeSymbol` sonra yöntemi silebilirsiniz. Bu çözümleyici <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.LocalDeclarationStatement?displayProperty=nameWithType>ifadeleri <xref:Microsoft.CodeAnalysis.SymbolKind.NamedType?displayProperty=nameWithType> değil, inceler. Altında `AnalyzeNode` kırmızı dalgalar olduğuna dikkat edin. Az önce eklediğiniz `AnalyzeNode` kod, bildirilmemiş bir yönteme başvurur. Bu yöntemi aşağıdaki kodu kullanarak bildirin:

```csharp
private void AnalyzeNode(SyntaxNodeAnalysisContext context)
{
}
```

Aşağıdaki `Category` kodda gösterildiği **gibi MakeConstAnalyzer.cs** "Kullanım" olarak değiştirin:

```csharp
private const string Category = "Usage";
```

## <a name="find-local-declarations-that-could-be-const"></a>Const olabilecek yerel bildirimleri bulma

`AnalyzeNode` Yöntemin ilk sürümünü yazma nın zamanı. Aşağıdaki kod gibi olabilir `const` ama olmayabilir tek bir yerel bildirim için bakmak gerekir:

```csharp
int x = 0;
Console.WriteLine(x);
```

İlk adım yerel bildirimleri bulmaktır. MakeConstAnalyzer.cs aşağıdaki kodu `AnalyzeNode` **MakeConstAnalyzer.cs**ekleyin:

```csharp
var localDeclaration = (LocalDeclarationStatementSyntax)context.Node;
```

Çözümleyiciniz yerel bildirimlerdeki değişiklikler ve yalnızca yerel bildirimler için kaydolduğundan, bu döküm her zaman başarılı dır. Başka hiçbir düğüm türü yönteminize `AnalyzeNode` çağrı yı tetiklemez. Ardından, değiştiriciler `const` için bildirimi denetleyin. Onları bulursanız, hemen geri dönün. Aşağıdaki kod, yerel `const` bildirimdeki herhangi bir değiştiriciyi arar:

```csharp
// make sure the declaration isn't already const:
if (localDeclaration.Modifiers.Any(SyntaxKind.ConstKeyword))
{
    return;
}
```

Son olarak, değişkenin `const`. Bu, baş harfe atandıktan sonra asla atanmamalarını sağlamak anlamına gelir.

Bazı anlamsal analizler <xref:Microsoft.CodeAnalysis.Diagnostics.SyntaxNodeAnalysisContext>yapacaksınız. Bağımsız değişkeni, `context` yerel değişken bildiriminin yapılıp yapılamayacağını `const`belirlemek için kullanırsınız. A, <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> tek bir kaynak dosyadaki tüm anlamsal bilgilerin temsil eder. [Semantik modelleri](../work-with-semantics.md)kapsayan makalede daha fazla bilgi edinebilirsiniz. Yerel bildirim deyiminde veri akışı çözümlemesi gerçekleştirmek <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> için kullanırsınız. Ardından, yerel değişkenin başka bir yerde yeni bir değerle yazılmadığından emin olmak için bu veri akışı çözümlemesi sonuçlarını kullanırsınız. Değişkeniçin <xref:Microsoft.CodeAnalysis.ModelExtensions.GetDeclaredSymbol%2A> almak <xref:Microsoft.CodeAnalysis.ILocalSymbol> için uzantı yöntemini arayın ve veri akışı <xref:Microsoft.CodeAnalysis.DataFlowAnalysis.WrittenOutside%2A?displayProperty=nameWithType> çözümlemesi koleksiyonunda bulunup bulunmadığını kontrol edin. `AnalyzeNode` Yöntemin sonuna aşağıdaki kodu ekleyin:

```csharp
// Perform data flow analysis on the local declaration.
var dataFlowAnalysis = context.SemanticModel.AnalyzeDataFlow(localDeclaration);

// Retrieve the local symbol for each variable in the local declaration
// and ensure that it is not written outside of the data flow analysis region.
var variable = localDeclaration.Declaration.Variables.Single();
var variableSymbol = context.SemanticModel.GetDeclaredSymbol(variable);
if (dataFlowAnalysis.WrittenOutside.Contains(variableSymbol))
{
    return;
}
```

Eklenen kod, değişkenin değiştirilmemesini sağlar ve bu `const`nedenle yapılabilir. Teşhisi yükseltme nin zamanı. Son satır olarak aşağıdaki kodu `AnalyzeNode`ekleyin:

```csharp
context.ReportDiagnostic(Diagnostic.Create(Rule, context.Node.GetLocation()));
```

Çözümleyicinizi çalıştırmak için **F5** tuşuna basarak ilerlemenizi kontrol edebilirsiniz. Daha önce oluşturduğunuz konsol uygulamasını yükleyebilir ve ardından aşağıdaki test kodunu ekleyebilirsiniz:

```csharp
int x = 0;
Console.WriteLine(x);
```

Ampul görünmelidir ve çözümleyiciniz bir tanı bildirmelidir. Ancak, ampul hala şablon oluşturulan kod düzeltme kullanır ve büyük harf yapılabilir söyler. Sonraki bölümde kod düzeltmesi nasıl yazılalıyorum.

## <a name="write-the-code-fix"></a>Kod düzeltmesini yazma

Bir çözümleyici bir veya daha fazla kod düzeltmeleri sağlayabilir. Kod düzeltmesi, bildirilen sorunu gideren bir düzenleme tanımlar. Oluşturduğunuz çözümleyici için, const anahtar sözcüğü ekleyen bir kod düzeltmesi sağlayabilirsiniz:

```csharp
const int x = 0;
Console.WriteLine(x);
```

Kullanıcı editör ve Visual Studio ampul UI kodu değiştirir onu seçer.

Şablon tarafından eklenen **MakeConstCodeFixProvider.cs** dosyasını açın.  Bu kod düzeltmesi zaten tanılama çözümleyiciniz tarafından üretilen Tanılama Kimliği'ne bağlanmış durumda, ancak henüz doğru kod dönüştürmesini uygulamamaktadır. Önce şablon kodunun bir kısmını kaldırmanız gerekir. Başlık dizesini "Sabit yap" olarak değiştirin:

[!code-csharp[Update the CodeFix title](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#CodeFixTitle "Update the CodeFix title")]

Ardından, `MakeUppercaseAsync` yöntemi silin. Artık geçerli değil.

Tüm kod düzeltme <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider>sağlayıcıları. Bunların tümü <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider.RegisterCodeFixesAsync(Microsoft.CodeAnalysis.CodeFixes.CodeFixContext)?displayProperty=nameWithType> kullanılabilir kod düzeltmelerini bildirmek için geçersiz kılınır. In `RegisterCodeFixesAsync`, tanılama eşleşecek şekilde <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> aradığınız ata düğümü türünü değiştirin:

[!code-csharp[Find local declaration node](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#FindDeclarationNode  "Find the local declaration node that raised the diagnostic")]

Ardından, kod düzeltmesini kaydetmek için son satırı değiştirin. Düzeltmeniz, `const` değiştiriciyi varolan bir bildirime eklemeden kaynaklanan yeni bir belge oluşturur:

[!code-csharp[Register the new code fix](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#RegisterCodeFix  "Register the new code fix")]

Az önce sembole `MakeConstAsync`eklediğiniz kodda kırmızı dalgalı lıklar fark edeceksiniz. Aşağıdaki kod `MakeConstAsync` gibi bir bildirim ekleyin:

```csharp
private async Task<Document> MakeConstAsync(Document document,
   LocalDeclarationStatementSyntax localDeclaration,
   CancellationToken cancellationToken)
{
}
```

Yeni `MakeConstAsync` yöntemin, <xref:Microsoft.CodeAnalysis.Document> kullanıcının kaynak dosyasını temsil eden <xref:Microsoft.CodeAnalysis.Document> dosyayı `const` şimdi bir bildirim içeren yeni bir dosyaya dönüştürür.

Bildirim deyiminin `const` önüne eklemek için yeni bir anahtar kelime belirteci oluşturursunuz. Önce bildirim deyiminin ilk belirteci herhangi bir satır ı kaldırmak `const` ve belirteç eklemek için dikkatli olun. `MakeConstAsync` yöntemine aşağıdaki kodu ekleyin:

[!code-csharp[Create a new const keyword token](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#CreateConstToken  "Create the new const keyword token")]

Ardından, aşağıdaki `const` kodu kullanarak bildirime belirteci ekleyin:

```csharp
// Insert the const token into the modifiers list, creating a new modifiers list.
var newModifiers = trimmedLocal.Modifiers.Insert(0, constToken);
// Produce the new local declaration.
var newLocal = trimmedLocal
    .WithModifiers(newModifiers)
    .WithDeclaration(localDeclaration.Declaration);
```

Ardından, c# biçimlendirme kurallarıyla eşleşecek şekilde yeni bildiriyi biçimlendirin. Değişikliklerinizi varolan kodla eşleşecek şekilde biçimlendirmek daha iyi bir deneyim oluşturur. Varolan koddan hemen sonra aşağıdaki ifadeyi ekleyin:

[!code-csharp[Format the new declaration](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#FormatLocal  "Format the new declaration")]

Bu kod için yeni bir ad alanı gereklidir. Dosyanın `using` üst bölümüne aşağıdaki ifadeyi ekleyin:

```csharp
using Microsoft.CodeAnalysis.Formatting;
```

Son adım, sizin de bir şey yapmaktır. Bu işlemin üç adımı vardır:

1. Varolan belgeye bir tanıtıcı alın.
1. Varolan bildirgeyi yeni bildirimle değiştirerek yeni bir belge oluşturun.
1. Yeni belgeyi döndürün.

`MakeConstAsync` Yöntemin sonuna aşağıdaki kodu ekleyin:

[!code-csharp[replace the declaration](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#ReplaceDocument  "Generate a new document by replacing the declaration")]

Kod düzeltmeniz denemeye hazır.  Çözümleyici projesini Visual Studio'nun ikinci bir örneğinde çalıştırmak için F5 tuşuna basın. İkinci Visual Studio örneğinde, yeni bir C# Console Application projesi oluşturun ve Main yöntemine sabit değerlerle birlikte birkaç yerel değişken bildirimi ekleyin. Bunların aşağıdaki gibi uyarılar olarak bildirildiğini görürsünüz.

![Const uyarılar yapabilir](media/how-to-write-csharp-analyzer-code-fix/make-const-warning.png)

Çok ilerleme kaydettin. Yapılabilecek `const`beyanların altında squiggles var. Ama hala yapılacak işler var. Bu, sonra `const` `j` ve son olarak `k`ile `i`başlayan bildirimleri eklerseniz iyi çalışır. `const` Ancak, değiştiriciyi farklı bir sırada eklerseniz, `k`ile başlayarak , `k` çözümleyiciniz hatalar `const`oluşturur: bildirileme edilemez , sürece `i` ve `j` her ikisi de zaten `const`. Değişkenlerin bildirilip başharfe böldüğü farklı şekillerde ele aldığınızdan emin olmak için daha fazla analiz yapmalısın.

## <a name="build-data-driven-tests"></a>Veri odaklı testler oluşturma

Çözümleyiciniz ve kod düzeltme çalışmanız, const yapilebilen tek bir bildirimin basit bir durumu üzerinde çalışır. Bu uygulamanın hata yaptığı çok sayıda olası bildirim bildirimi vardır. Şablon tarafından yazılmış birim test kitaplığıyla çalışarak bu durumları giderin. Visual Studio'nun ikinci bir kopyasını tekrar tekrar açmaktan çok daha hızlı.

Birim test projesinde **MakeConstUnitTests.cs** dosyasını açın. Şablon, çözümleyici ve kod düzeltme birimi testi için iki ortak desen izleyen iki test oluşturdu. `TestMethod1`çözümleyicinin tanılamayı bildirmemesini sağlayan bir testin deseni gösterir. `TestMethod2`tanılama yı raporlama ve kod düzeltmesini çalıştırma deseni gösterir.

Çözümleyiciniz için hemen hemen her testin kodu bu iki modelden birini izler. İlk adım için, bu testleri veri odaklı testler olarak yeniden çalışabilirsiniz. Daha sonra, farklı test girişlerini temsil edecek yeni dize sabitleri ekleyerek yeni testler oluşturmak kolay olacaktır.

Verimlilik için ilk adım, iki testi veri odaklı testlere yeniden dahil etmektir. Daha sonra, her yeni test için yalnızca bir çift dize sabiti tanımlamanız gerekir. Yeniden düzenleme yaparken, her iki yöntemi de daha iyi adlara yeniden adlandırın. Tanılamanın yapılmadığını garanti eden bu testle değiştirin: `TestMethod1`

```csharp
[DataTestMethod]
[DataRow("")]
public void WhenTestCodeIsValidNoDiagnosticIsTriggered(string testCode)
{
    VerifyCSharpDiagnostic(testCode);
}
```

Tanılamanızın bir uyarıyı tetiklemesi için neden olmaması gereken herhangi bir kod parçası tanımlayarak bu test için yeni bir veri satırı oluşturabilirsiniz. Kaynak kodu `VerifyCSharpDiagnostic` parçası için tetiklenen tanılama olmadığında bu aşırı geçiş yükü.

Ardından, `TestMethod2` tanılamanın yükseltilmesini ve kaynak kod parçası için bir kod düzeltmesinin uygulanmasını sağlayan bu testle değiştirin:

```csharp
[DataTestMethod]
[DataRow(LocalIntCouldBeConstant, LocalIntCouldBeConstantFixed, 10, 13)]
public void WhenDiagnosticIsRaisedFixUpdatesCode(
    string test,
    string fixTest,
    int line,
    int column)
{
    var expected = new DiagnosticResult
    {
        Id = MakeConstAnalyzer.DiagnosticId,
        Message = new LocalizableResourceString(nameof(MakeConst.Resources.AnalyzerMessageFormat), MakeConst.Resources.ResourceManager, typeof(MakeConst.Resources)).ToString(),
        Severity = DiagnosticSeverity.Warning,
        Locations =
            new[] {
                    new DiagnosticResultLocation("Test0.cs", line, column)
                }
    };

    VerifyCSharpDiagnostic(test, expected);

    VerifyCSharpFix(test, fixTest);
}
```

Önceki kod da beklenen tanılama sonucu oluşturur kod için birkaç değişiklik yaptı. `MakeConst` Çözümleyicide kayıtlı genel sabitleri kullanır. Buna ek olarak, giriş ve sabit kaynak için iki dize sabitleri kullanır. `UnitTest` Sınıfa aşağıdaki dize sabitlerini ekleyin:

[!code-csharp[string constants for fix test](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#FirstFixTest "string constants for fix test")]

Geçtiklerinden emin olmak için bu iki testi çalıştırın. **Test** > Visual Studio'da,**Test Windows** > **Test Gezgini'ni**seçerek Test **Gezgini'ni** açın.  **Tümlerini Çalıştır** bağlantısına basın.

## <a name="create-tests-for-valid-declarations"></a>Geçerli bildirimler için testler oluşturma

Genel bir kural olarak, çözümleyiciler en az iş yaparak, mümkün olduğunca çabuk çıkmak gerekir. Visual Studio, kullanıcı kodu edinirken kayıtlı çözümleyicileri çağırır. Yanıt verme önemli bir gereksinimdir. Tanılamanızı yükseltmemesi gereken kod için birkaç test çalışması vardır. Çözümleyiciniz zaten bu testlerden birini işler, bir değişkenin baş harfe döndürüldüğü durumlarda. Bu durumda temsil etmek için testlerinize aşağıdaki dize sabitini ekleyin:

[!code-csharp[variable assigned](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#VariableAssigned "a variable that is assigned after being initialized won't raise the diagnostic")]

Ardından, aşağıdaki snippet'te gösterildiği gibi bu test için bir veri satırı ekleyin:

```csharp
[DataTestMethod]
[DataRow(""),
 DataRow(VariableAssigned)]
public void WhenTestCodeIsValidNoDiagnosticIsTriggered(string testCode)
```

Bu test de geçer. Ardından, henüz işlemediğiniz koşullar için sabitler ekleyin:

- Zaten const `const`oldukları için zaten olan bildirimler:

   [!code-csharp[already const declaration](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#AlreadyConst "a declaration that is already const should not raise the diagnostic")]

- Kullanılacak bir değer olmadığından, baş harfe aday olmayan bildirimler:

   [!code-csharp[declarations that have no initializer](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#NoInitializer "a declaration that has no initializer should not raise the diagnostic")]

- Başharfin sabit olmadığı bildirimler, çünkü zaman sabitlerini derleyemezler:

   [!code-csharp[declarations where the initializer isn't const](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#InitializerNotConstant "a declaration where the initializer is not a compile-time constant should not raise the diagnostic")]

C# tek bir bildirim olarak birden çok bildirime izin verdiğinden daha da karmaşık olabilir. Aşağıdaki test çalışması dize sabitini düşünün:

[!code-csharp[multiple initializers](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#MultipleInitializers "A declaration can be made constant only if all variables in that statement can be made constant")]

Değişken `i` sabit yapılabilir, ancak değişken `j` yapılamaz. Bu nedenle, bu bildirim const bir bildirim deılamaz. Tüm `DataRow` bu testler için bildirimleri ekleyin:

```csharp
[DataTestMethod]
[DataRow(""),
    DataRow(VariableAssigned),
    DataRow(AlreadyConst),
    DataRow(NoInitializer),
    DataRow(InitializerNotConstant),
    DataRow(MultipleInitializers)]
public void WhenTestCodeIsValidNoDiagnosticIsTriggered(string testCode)
```

Testlerinizi yeniden çalıştırın ve bu yeni test çalışmalarının başarısız olduğunu görürsünüz.

## <a name="update-your-analyzer-to-ignore-correct-declarations"></a>Doğru bildirimleri yoksaymak için çözümleyicinizi güncelleştirin

Bu koşullarla eşleşen kodu filtrelemek `AnalyzeNode` için çözümleyicinizin yönteminde bazı geliştirmeler yapmanız gerekir. Bunların hepsi ilgili koşullardır, bu nedenle benzer değişiklikler tüm bu koşulları düzeltecektir. Aşağıdaki değişiklikleri `AnalyzeNode`yapın:

- Anlamsal analiziniz tek bir değişken bildirimini inceledi. Bu kodun, aynı `foreach` ifadede bildirilen tüm değişkenleri inceleyen bir döngüde olması gerekir.
- Bildirilen her değişkenin bir baş harfe sahip olması gerekir.
- Bildirilen her değişkenin başharfi derleme zamanı sabiti olmalıdır.

Yönteminizde, orijinal anlamsal analizi değiştirin: `AnalyzeNode`

```csharp
// Perform data flow analysis on the local declaration.
var dataFlowAnalysis = context.SemanticModel.AnalyzeDataFlow(localDeclaration);

// Retrieve the local symbol for each variable in the local declaration
// and ensure that it is not written outside of the data flow analysis region.
var variable = localDeclaration.Declaration.Variables.Single();
var variableSymbol = context.SemanticModel.GetDeclaredSymbol(variable);
if (dataFlowAnalysis.WrittenOutside.Contains(variableSymbol))
{
    return;
}
```

aşağıdaki kod parçacığı ile:

```csharp
// Ensure that all variables in the local declaration have initializers that
// are assigned with constant values.
foreach (var variable in localDeclaration.Declaration.Variables)
{
    var initializer = variable.Initializer;
    if (initializer == null)
    {
        return;
    }

    var constantValue = context.SemanticModel.GetConstantValue(initializer.Value);
    if (!constantValue.HasValue)
    {
        return;
    }
}

// Perform data flow analysis on the local declaration.
var dataFlowAnalysis = context.SemanticModel.AnalyzeDataFlow(localDeclaration);

foreach (var variable in localDeclaration.Declaration.Variables)
{
    // Retrieve the local symbol for each variable in the local declaration
    // and ensure that it is not written outside of the data flow analysis region.
    var variableSymbol = context.SemanticModel.GetDeclaredSymbol(variable);
    if (dataFlowAnalysis.WrittenOutside.Contains(variableSymbol))
    {
        return;
    }
}
```

İlk `foreach` döngü, her değişken bildirimini sözdizimanalizi ni kullanarak inceler. İlk çek, değişkenin bir baş harfe sahip olduğunu garanti eder. İkinci çek, baş harfin sabit olduğunu garanti eder. İkinci döngü orijinal semantik analize sahiptir. Anlamsal denetimler, performans üzerinde daha büyük bir etkiye sahip olduğundan ayrı bir döngüdedir. Testlerinizi tekrar çalıştırın ve hepsinin geçtiğini göreceksiniz.

## <a name="add-the-final-polish"></a>Son cila ekle

Neredeyse bitti. Çözümleyicinizin işlemesi için birkaç koşul daha vardır. Kullanıcı kod yazarken Visual Studio çözümleyicileri çağırır. Çözümleyiciniz genellikle derlemeyen kod için çağrılacak tır. Tanı çözümleyicinin `AnalyzeNode` yöntemi, sabit değerin değişken türüne dönüştürülüp dönüştürülemeyeceğini kontrol etmez. Yani, geçerli uygulama mutlu int i = "abc" gibi yanlış bir bildirimi yerel bir sabit dönüştürür. Bu durum için bir kaynak dize sabiti ekleyin:

[!code-csharp[Mismatched types don't raise diagnostics](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#DeclarationIsInvalid "When the variable type and the constant type don't match, there's no diagnostic")]

Ayrıca, başvuru türleri düzgün şekilde işlenmez. Bir başvuru türü için izin `null`verilen tek sabit <xref:System.String?displayProperty=nameWithType>değer, dize literals sağlayan bu durumda dışında. Başka bir `const string s = "abc"` deyişle, yasal, ama `const object s = "abc"` değildir. Bu kod snippet bu koşulu doğrular:

[!code-csharp[Reference types don't raise diagnostics](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#DeclarationIsntString "When the variable type is a reference type other than string, there's no diagnostic")]

Ayrıntılı olması için, bir dize için sabit bir bildirim oluşturabileceğinizden emin olmak için başka bir sınayı eklemeniz gerekir. Aşağıdaki parçacık hem tanılamayı yükselten kodu hem de düzeltme uygulandıktan sonra kodu tanımlar:

[!code-csharp[string reference types raise diagnostics](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#ConstantIsString "When the variable type is string, it can be constant")]

Son olarak, bir değişken `var` anahtar kelimeyle birlikte bildirilirse, kod `const var` düzeltmesi yanlış bir şey yapar ve C# dili tarafından desteklenmeyen bir bildirim oluşturur. Bu hatayı düzeltmek için kod düzeltmesinin anahtar kelimeyi `var` çıkarılan türün adı ile değiştirmesi gerekir:

[!code-csharp[var references need to use the inferred types](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#VarDeclarations "Declarations made using var must have the type replaced with the inferred type")]

Bu değişiklikler, her iki test için veri satırı bildirimlerini güncelleştirin. Aşağıdaki kod tüm veri satırı öznitelikleri ile bu testleri gösterir:

[!code-csharp[The finished tests](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#FinishedTests "The finished tests for the make const analyzer")]

Neyse ki, yukarıdaki hataların hepsi sadece öğrendim aynı teknikleri kullanarak ele alınabilir.

İlk hatayı düzeltmek için, ilk **DiagnosticAnalyzer.cs** açın ve her bir yerel bildirimin başharflerinin işaretlendiği foreach döngüyü bulun ve sabit değerlerle atandıklarından emin olun. Her biri için ilk döngüden hemen _önce,_ yerel bildirimin bildirilen türü hakkında ayrıntılı bilgi almak için arayın: `context.SemanticModel.GetTypeInfo()`

```csharp
var variableTypeName = localDeclaration.Declaration.Type;
var variableType = context.SemanticModel.GetTypeInfo(variableTypeName).ConvertedType;
```

Daha sonra, `foreach` döngünüzün içinde, değişken türüne dönüştürülebilen olduğundan emin olmak için her bir baş harfe işaret edin. Baş harfin sabit olduğundan emin olduktan sonra aşağıdaki çeki ekleyin:

```csharp
// Ensure that the initializer value can be converted to the type of the
// local declaration without a user-defined conversion.
var conversion = context.SemanticModel.ClassifyConversion(initializer.Value, variableType);
if (!conversion.Exists || conversion.IsUserDefined)
{
    return;
}
```

Bir sonraki değişiklik sonuncusu üzerine inşa edin. İlk foreach döngükapanış kıvırcık ayraç önce, sabit bir dize veya null olduğunda yerel bildirimin türünü kontrol etmek için aşağıdaki kodu ekleyin.

```csharp
// Special cases:
//  * If the constant value is a string, the type of the local declaration
//    must be System.String.
//  * If the constant value is null, the type of the local declaration must
//    be a reference type.
if (constantValue.Value is string)
{
    if (variableType.SpecialType != SpecialType.System_String)
    {
        return;
    }
}
else if (variableType.IsReferenceType && constantValue.Value != null)
{
    return;
}
```

Var' anahtar sözcüğünün doğru tür adı ile değiştirilmesi için kod düzeltme sağlayıcınıza biraz daha kod yazmanız gerekir. **CodeFixProvider.cs**dön. Ekleyeceğiniz kod aşağıdaki adımları yapar:

- Bildirimin bir `var` bildirim olup olmadığını ve aşağıdakileri yapıp olmadığını denetleyin:
- Çıkarılan tür için yeni bir tür oluşturun.
- Tür bildiriminin takma ad olmadığından emin olun. Eğer öyleyse, beyan `const var`etmek yasal.
- Bu `var` programda bir tür adı olmadığından emin olun. (Eğer öyleyse, `const var` yasal).
- Tam tür adını basitleştirin

Kulağa çok fazla kod gibi geliyor. Değil. Bildiren ve başharfe gelen `newLocal` satırı aşağıdaki kodla değiştirin. Bu hemen başlatılmasından `newModifiers`sonra gider:

[!code-csharp[Replace Var designations](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#ReplaceVar "Replace a var designation with the explicit type")]

Türü kullanmak için bir `using` deyim eklemeniz <xref:Microsoft.CodeAnalysis.Simplification.Simplifier> gerekir:

```csharp
using Microsoft.CodeAnalysis.Simplification;
```

Testlerinizi çalıştırın ve hepsi geçsin. Bitmiş analizörünüzü çalıştırarak kendinizi tebrik edin. Analizör projesini, Roslyn Preview uzantısı yüklü Visual Studio'nun ikinci bir örneğinde çalıştırmak için Ctrl+F5 tuşuna basın.

- İkinci Visual Studio örneğinde, yeni bir C# `int x = "abc";` Console Application projesi oluşturun ve Ana yönteme ekleyin. İlk hata düzeltmesi sayesinde, bu yerel değişken bildirimi için hiçbir uyarı bildirilmelidir (beklendiği gibi bir derleyici hatası olsa da).
- Ardından, `object s = "abc";` Ana yönteme ekleyin. İkinci hata düzeltmesi nedeniyle hiçbir uyarı bildirilmemelidir.
- Son olarak, anahtar kelimeyi `var` kullanan başka bir yerel değişken ekleyin. Bir uyarının rapor olduğunu ve sola doğru bir öneri nin görüntülediğini görürsünüz.
- Düzenleyiciyi kıvrımlı altı çizili üzerine taşıyın ve Ctrl+ tuşuna basın. önerilen kod düzeltmesini görüntülemek için. Kod düzeltmenizi seçtikten sonra, var' anahtar kelimesinin artık doğru şekilde işleneceğini unutmayın.

Son olarak, aşağıdaki kodu ekleyin:

```csharp
int i = 2;
int j = 32;
int k = i + j;
```

Bu değişikliklerden sonra, yalnızca ilk iki değişkende kırmızı dalgalı squiggles olsun. Her `const` ikisine `i` de ekleyin ve `j`, `k` şimdi olabilir, `const`çünkü yeni bir uyarı almak .

Tebrikler! Bir sorunu algılamak için anında kod çözümlemesi gerçekleştiren ve düzeltmek için hızlı bir düzeltme sağlayan ilk .NET Derleyici Platformu uzantınızı oluşturdunuz. Yol boyunca, .NET Derleyici Platformu SDK'nın (Roslyn API'leri) bir parçası olan kod API'lerinin çoğunu öğrendiniz. GitHub depomuzda [tamamlanan örnekle](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/Tutorials/MakeConst) karşı çalışmanızı kontrol edebilirsiniz.

## <a name="other-resources"></a>Diğer kaynaklar

- [Sözdizimi analizine başlayın](../get-started/syntax-analysis.md)
- [Anlamsal analize başlayın](../get-started/semantic-analysis.md)
