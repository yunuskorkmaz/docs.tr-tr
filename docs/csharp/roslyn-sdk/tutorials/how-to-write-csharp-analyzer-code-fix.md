---
title: 'Öğretici: ilk Çözümleyicisi ve kod düzeltmenizi yazın'
description: Bu öğretici bir çözümleyici oluşturmak için adım adım yönergeler sağlar ve kod düzeltmesi .NET derleyici SDK'sı (Roslyn API'leri) kullanarak.
ms.date: 08/01/2018
ms.custom: mvc
ms.openlocfilehash: 2959fe3008bfca972d3a164ed27d05c2a8b0e69a
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47171757"
---
# <a name="tutorial-write-your-first-analyzer-and-code-fix"></a>Öğretici: ilk Çözümleyicisi ve kod düzeltmenizi yazın

.NET derleyici Platformu SDK'sı, özel uyarıları, hedef C# veya Visual Basic kodunu oluşturmak için ihtiyacınız olan araçları sağlar. **Çözümleyicisi** , kural ihlalleri algılar kodunu içerir. **Kod düzeltme** ihlali düzelten kodu içerir. Uygulamanız kuralları kodlama stili için adlandırma kuralları ve daha fazla bilgi için kod yapısını her şey olabilir. .NET derleyici platformu, geliştiricilerin kod yazma ve tüm Visual Studio kullanıcı Arabirimi özellikleri kodu düzeltmek için analiz çalıştırmak için framework sunar: dalgalı çizgiler Visual Studio hata oluşturma "ampule" listesinde doldurma Düzenleyicisi'nde gösteriliyor öneriler ve önerilen düzeltmeleri zengin önizlemesi gösteriliyor.

Bu öğreticide, oluşturma hakkında bilgi edineceksiniz bir **Çözümleyicisi** ve yayarsa **kod düzeltme** Roslyn API'leri kullanma. Bir çözümleyici, kaynak kod analizini gerçekleştirin ve kullanıcıya bir sorun bildirmek için bir yoldur. İsteğe bağlı olarak, bir çözümleyici, kullanıcının kaynak kodu için bir değişiklik gösteren bir kod düzeltme de sağlayabilirsiniz. Bu öğreticide kullanılarak bildirilebilir yerel değişken bildirimlerini bulan bir çözümleyici oluşturur `const` değiştiricisi ancak değildir. Eşlik eden kod düzeltmesi eklemek için bu bildirimler değiştirir `const` değiştiricisi.

## <a name="prerequisites"></a>Önkoşullar

* [Visual Studio 2017](https://www.visualstudio.com/downloads)

Yüklemeniz gerekir **.NET derleyici Platformu SDK'sı**:

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

Birkaç adım vardır, çözümleyici doğrulamak ve oluşturmak için:

1. Çözümü oluşturun.
1. Çözümleyici bir ad ve açıklama kaydedin.
1. Rapor Çözümleyicisi uyarıları ve öneriler.
1. Önerileri kabul etmek için kod düzeltmeyi uygulayın.
1. Analiz birim testleri ile geliştirin.

## <a name="explore-the-analyzer-template"></a>Çözümleyici şablonu keşfedin

Çözümleyici yerel sabitleri dönüştürülebilir yerel değişken bildirimlerini kullanıcıya bildirir. Örneğin, aşağıdaki kodu düşünün:

```csharp
int x = 0;
Console.WriteLine(x);
```

Yukarıdaki kodda `x` sabit bir değer atanır ve hiçbir zaman değiştirilmez. Kullanılarak bildirilebilir `const` değiştiricisi:

```csharp
const int x = 0;
Console.WriteLine(x);
```

Bir değişken sabit yapılan olup olmadığını belirlemek için analiz gerektiren söz dizimi analizi, sabit Başlatıcı ifadesinin analizini ve değişkeni için hiçbir zaman yazıldığından emin olmak için veri akışı analizini yapar. .NET derleyici platformu bu analiz gerçekleştirmeyi kolaylaştıran API'ler sağlar. Yeni C# oluşturmak için ilk adımıdır **Çözümleyicisi kod düzeltme** proje.

* Visual Studio'da **Dosya > Yeni > Proje...**  yeni proje iletişim kutusu görüntülenecek.
* Altında **Visual C# > genişletilebilirlik**, seçin **kod düzeltme (.NET Standard) Çözümleyicisi**.
* Projenizi adlandırın "**MakeConst**" ve Tamam'a tıklayın.

Üç projenin kod düzeltme şablonuyla Çözümleyicisi oluşturur: Çözümleyicisi ve kod düzeltmesi içerir, ikinci bir birim test projesi ve üçüncü VSIX projesi. Varsayılan başlangıç projesi VSIX projesinde olduğundan. Tuşuna **F5** VSIX projesi başlatılamadı. Bu, yeni Çözümleyicisi yükledi Visual Studio'nun ikinci bir örneğini başlatır.

> [!TIP]
> Çözümleyicisi'ni çalıştırdığınızda, Visual Studio'nun ikinci bir kopya başlatın. Bu ikinci kopyanın farklı bir kayıt defteri kovanı ayarlarını depolamak için kullanır. Visual Studio iki kopyasını visual ayarlarında ayırt etmenize olanak sağlar. Visual Studio'nun Deneysel çalıştırma için farklı bir tema seçebilirsiniz. Ayrıca, ayarları veya oturum açma Visual Studio Deneysel kullanarak hesabı çalıştırma Visual Studio için Dolaşımda yok. Ayarları farklı saklar.

Başlattığınız ikinci Visual Studio örneğinde yeni bir C# konsol uygulaması projesi (.NET Core veya .NET Framework projesi olacaktır işler--kaynak düzeyinde Çözümleyicileri işler.) oluşturma Dalgalı çizgi belirteciyle üzerine gelin ve bir çözümleyici tarafından sağlanan uyarı metni görüntülenir.

Şablon, aşağıdaki resimde gösterildiği gibi her tür bildiriminde tür adı küçük harf, burada içeren bir uyarı bildirir bir çözümleyici oluşturur:

![Uyarı raporlama Çözümleyicisi](media/how-to-write-csharp-analyzer-code-fix/report-warning.png)

Şablon, tüm büyük küçük harf karakter içeren herhangi bir tür adı değiştiren bir kod düzeltme de sağlar. Önerilen değişiklikleri görmek için uyarı ile görüntülenen ampul tıklayabilirsiniz. Önerilen değişikliklerin güncelleştirmeler tür adı ve bu tür iş Çözümdeki tüm başvurular kabul etme. Uygulamada ilk Çözümleyicisi gördüğünüze göre ikinci Visual Studio örneğini kapatın ve Çözümleyicisi projenize döndürür.

Visual Studio ikinci bir kopyası başlayıp her değişiklik Çözümleyicisi'nde test etmek için yeni kod gerekmez. Şablon birim testi projesi ayrıca sizin için oluşturur. Bu proje, iki testleri içerir. `TestMethod1` Tipik bir tanılama tetiklemeden kod analiz eden bir testi biçimini gösterir. `TestMethod2` bir tanılama tetikler ve ardından bir önerilen kod düzeltme uygular bir test biçimini gösterir. Çözümleyicisi ve kod düzeltmesi oluştururken farklı kod yapıları iş doğrulamak için testler yazacaksınız. Çözümleyici için birim testleri, Visual Studio ile etkileşimli olarak sınama daha çok daha hızlı.

> [!TIP]
> Hangi kod yapıları gerekir ve sizin Çözümleyicisi tetikleyin olmamalıdır bildiğinizde Çözümleyicisi birim testleri harika bir araçlardır. Visual Studio'nun başka bir kopya, Çözümleyicisinde yüklenirken Keşfetmenin yanı sıra, hakkında henüz düşündüğünüz değil yapıları için harika bir araçtır.

## <a name="create-analyzer-registrations"></a>Çözümleyici kayıtları oluşturma

İlk şablon oluşturur `DiagnosticAnalyzer` içinde sınıf **MakeConstAnalyzer.cs** dosya. Bu ilk Çözümleyicisi her analyzer'ın iki önemli özellikleri gösterir.

* Her bir Tanılama Çözümleyicisi sağlamalısınız bir `[DiagnosticAnalyzer]` yerler üzerinde çalışır dil açıklayan öznitelik.
* Her bir Tanılama Çözümleyicisi öğesinden türetilmelidir <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer> sınıfı.

Şablon ayrıca tüm Çözümleyicisi parçası olan temel özelliklerini gösterir:

1. Eylemler kaydedin. Eylemleri ihlalleri kod inceleme, çözümleyici tetiklemesi gereken kod değişikliği temsil eder. Visual Studio kayıtlı eylem eşleşen kod düzenleme algıladığında, kayıtlı Çözümleyicisi'nin yöntemi çağırır.
1. Tanılama oluşturun. Çözümleyici ihlalinin algıladığında, kullanıcıya ihlalin bildirmek için Visual Studio kullanan bir tanılama nesnesi oluşturur.

İçinde geçersiz kılma eylemleri Kaydet <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer.Initialize(Microsoft.CodeAnalysis.Diagnostics.AnalysisContext)?displayProperty=nameWithType> yöntemi. Bu öğreticide, ziyaret ettiğiniz **söz dizimi düğümleri** yerel bildirimler için arama ve sabit değerleri bu olan bakın. Bir bildirimi sabit ise, çözümleyici oluşturun ve bir tanılama raporu.

Kayıt sabitleri güncelleştirmek için ilk adımıdır ve `Initialize` "Const olun" Çözümleyicisi'ni bu sabiti belirtmek için yöntemi. Çoğu dize sabitleri dize kaynak dosyasında tanımlanır. Bu yöntem daha kolay bir şekilde yerelleştirilmesi izlemelidir. Açık **Resources.resx** dosya **MakeConst** Çözümleyicisi proje. Bu kaynak düzenleyicisini görüntüler. Dize kaynakları şu şekilde güncelleştirin:

* Değişiklik `AnalyzerTitle` "Değişkeni sabit yapılabilmesi için" için.
* Değişiklik `AnalyzerMessageFormat` "sabit yapılabilmesi için" için.
* Değişiklik `AnalyzerDescription` "Sabit yapmak için".

Ayrıca, değişiklik **erişim değiştiricisi** açılan `public`. Bu, birim testleri bu sabiti kullanmak kolaylaştırır. İşiniz bittiğinde, kaynak düzenleyicisini şekil gösterir izleyin gibi görünmelidir:

![Dize kaynaklarını güncelleştir](media/how-to-write-csharp-analyzer-code-fix/update-string-resources.png)

Kalan Çözümleyicisi dosyasında değişikliklerdir. Açık **MakeConstAnalyzer.cs** Visual Studio'da. Kayıtlı eylem söz dizimini temel görevi gören bir simge gerçekleştirildiği birinden değiştirin. İçinde `MakeConstAnalyzerAnalyzer.Initialize` yöntemi, eylem simgeleri kaydeder satırı bulun:

```csharp
context.RegisterSymbolAction(AnalyzeSymbol, SymbolKind.NamedType);
```

Bunu, aşağıdaki satırla değiştirin:

[!code-csharp[Register the node action](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstAnalyzer.cs#RegisterNodeAction "Register a node action")]

Bu değişiklikten sonra silmeniz `AnalyzeSymbol` yöntemi. Bu çözümleyici inceler <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.LocalDeclarationStatement?displayProperty=nameWithType>değil <xref:Microsoft.CodeAnalysis.SymbolKind.NamedType?displayProperty=nameWithType> deyimleri. Dikkat `AnalyzeNode` kırmızı dalgalı çizgiler altındaki sahiptir. Yeni kod başvurularını eklenen bir `AnalyzeNode` bildirilmeyen yöntemi. Bu yöntem aşağıdaki kodu kullanarak bildirin:

```csharp
private void AnalyzeNode(SyntaxNodeAnalysisContext context)
{
}
```

Değişiklik `Category` "Kullanımı" **MakeConstAnalyzer.cs** aşağıdaki kodda gösterildiği gibi:

```csharp
private const string Category = "Usage";
```

## <a name="find-local-declarations-that-could-be-const"></a>Const yerel bildirimleri Bul

Ürününün ilk sürümünü yazmak için zamanı `AnalyzeNode` yöntemi. Olabilecek tek bir yerel bildirim için görünmelidir `const` ancak şu kod gibi:

```csharp
int x = 0;
Console.WriteLine(x);
```

İlk adım, yerel bildirimleri bulmaktır. Aşağıdaki kodu ekleyin `AnalyzeNode` içinde **MakeConstAnalyzer.cs**:

```csharp
var localDeclaration = (LocalDeclarationStatementSyntax)context.Node;
```

Bu tür dönüştürme, çözümleyici değişiklikler yerel bildirimleri ve yalnızca yerel bildirimler için kayıtlı olduğundan her zaman başarılı olur. Başka bir düğüm türü için bir çağrı tetikler, `AnalyzeNode` yöntemi. Ardından, herhangi bir bildirim denetleyin `const` değiştiriciler. Bulursanız, hemen döndürülür. Aşağıdaki kod için görünür `const` yerel bildiriminde değiştiriciler:

```csharp
// make sure the declaration isn't already const:
if (localDeclaration.Modifiers.Any(SyntaxKind.ConstKeyword))
{
    return;
}
```

Son olarak, değişkeni olabilir denetlemek ihtiyacınız `const`. Başlatıldıktan sonra emin olunmasını hiçbir zaman atandığı anlamına gelir.

Anlam analizi kullanarak, yerine getireceğiniz <xref:Microsoft.CodeAnalysis.Diagnostics.SyntaxNodeAnalysisContext>. Kullandığınız `context` yerel değişken bildiriminde yapılan olup olmadığını belirlemek için bağımsız değişken `const`. A <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> tek bir kaynak dosyası tüm anlamsal bilgilerin temsil eder. Kapsayan makalesinde daha fazla bilgi [anlam modelleri'ne](../work-with-semantics.md). Kullanacağınız <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> yerel bir bildirim deyiminin veri akış analizi gerçekleştirebilirsiniz. Ardından, bu veri akışını analiz sonuçlarını yerel değişkeni başka bir yerde yeni değerle yazılan olmadığından emin olmak için kullanın. Çağrı <xref:Microsoft.CodeAnalysis.ModelExtensions.GetDeclaredSymbol%2A> almak için genişletme yöntemi <xref:Microsoft.CodeAnalysis.ILocalSymbol> değişkeni ve bulunan olmayan onay <xref:Microsoft.CodeAnalysis.DataFlowAnalysis.WrittenOutside%2A?displayProperty=nameWithType> akış analizi veri koleksiyonu. Sonuna aşağıdaki kodu ekleyin `AnalyzeNode` yöntemi:

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

Yeni eklenen kod değişkeni değiştirilmez ve bu nedenle yapılabilir sağlar `const`. Bu tanılama yükseltme zamanı geldi. Son satırı olarak aşağıdaki kodu ekleyin `AnalyzeNode`:

```csharp
context.ReportDiagnostic(Diagnostic.Create(Rule, context.Node.GetLocation()));
```

İlerleme durumunuzu tuşlarına basarak denetleyebilirsiniz **F5** , Çözümleyicisi'ni çalıştırmak için. Daha önce oluşturduğunuz konsol uygulaması yükleyin ve ardından aşağıdaki test kodu ekleyin:

```csharp
int x = 0;
Console.WriteLine(x);
```

Ampul görünür olmalıdır ve bir tanılama, çözümleyici bildirmelisiniz. Ancak, ampul hala Şablonu oluşturulan kod düzeltme kullanır ve büyük harf yapılmış söyler. Sonraki bölümde, kod yazmaya açıklanmaktadır.

## <a name="write-the-code-fix"></a>Kod yazmaya

Bir çözümleyici, bir veya daha fazla kod düzeltmeleri sağlayabilir. Bir kod düzeltme bildirilen sorunu ele alan bir düzenleme tanımlar. Oluşturduğunuz için Çözümleyicisi, const anahtar sözcüğü ekleyen bir kod düzeltme sağlayabilirsiniz:

```csharp
const int x = 0;
Console.WriteLine(x);
```

Kullanıcı buradan ampul UI düzenleyicide ve Visual Studio kod değişikliklerini seçer.

Açık **MakeConstCodeFixProvider.cs** şablon tarafından eklenen dosya.  Bu kod düzeltmesi zaten tanı, tanılama, çözümleyici tarafından üretilen kimliği en fazla kablolu, ancak henüz doğru kod dönüşüm uygulamaz. İlk şablon kodunu bazıları kaldırmanız gerekir. Başlık dizesini "Yapma sabitine" değiştirin:

[!code-csharp[Update the CodeFix title](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#CodeFixTitle "Update the CodeFix title")]

Ardından, silmek `MakeUppercaseAsync` yöntemi. Artık geçerlidir.

Tüm kod düzeltmeleri türetilmesi <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider>. Bunların tümü geçersiz kılma <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider.RegisterCodeFixesAsync(Microsoft.CodeAnalysis.CodeFixes.CodeFixContext)?displayProperty=nameWithType> kullanılabilir kod düzeltmeleri bildirmek için. İçinde `RegisterCodeFixesAsync`, değiştirmek için aradığınız üst düğüm türü bir <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> tanılama eşleştirmek için:

[!code-csharp[Find local declaration node](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#FindDeclarationNode  "Find the local declaration node that raised the diagnostic")]

Ardından, bir kod düzeltme kaydetmek için son satırını değiştirin. Düzeltmenizi eklemesini sonuçları yeni bir belge oluşturacak `const` değiştiricisi var olan bir bildirim için:  

[!code-csharp[Register the new code fix](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#RegisterCodeFix  "Register the new code fix")]

Sembol sunucusunda yeni eklenen kod kırmızı dalgalı çizgiler görürsünüz `MakeConstAsync`. Eklemek için bir bildirim `MakeConstAsync` aşağıdaki kod gibi:

```csharp
private async Task<Document> MakeConstAsync(Document document,
   LocalDeclarationStatementSyntax localDeclaration,
   CancellationToken cancellationToken)
{
}
```

Yeni `MakeConstAsync` transform metodu <xref:Microsoft.CodeAnalysis.Document> yeni bir kullanıcının kaynak dosyasını temsil eden <xref:Microsoft.CodeAnalysis.Document> artık içeren bir `const` bildirimi.

Yeni oluşturduğunuz `const` bildirim deyiminin önündeki eklemek için anahtar belirteci. İlk önde gelen tüm Meraklısına Notlar bildirim deyiminin ilk belirtecinden kaldırıp ekleyebilir dikkatli olun `const` belirteci. Aşağıdaki kodu ekleyin `MakeConstAsync` yöntemi:

[!code-csharp[Create a new const keyword token](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#CreateConstToken  "Create the new const keyword token")]

Ardından, ekleme `const` aşağıdaki kodu kullanarak bildirimine belirteci:

```csharp
// Insert the const token into the modifiers list, creating a new modifiers list.
var newModifiers = trimmedLocal.Modifiers.Insert(0, constToken);
// Produce the new local declaration.
var newLocal = trimmedLocal
    .WithModifiers(newModifiers)
    .WithDeclaration(localDeclaration.Declaration);
```

Ardından, yeni bir bildirim C# biçimlendirme kurallarını eşleşecek şekilde biçimlendirin. Varolan kodu eşleştirmek için değişikliklerinizi biçimlendirme daha iyi bir deneyim oluşturur. Mevcut koddan hemen sonra aşağıdaki deyimi ekleyin:

[!code-csharp[Format the new declaration](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#FormatLocal  "Format the new declaration")]

Bu kod için yeni bir ad alanı gereklidir. Aşağıdaki `using` deyimini dosyanın en üstüne:

```csharp
using Microsoft.CodeAnalysis.Formatting;
```

Son adım, düzenlemeniz olmasını sağlamaktır. Bu işlem için üç adım vardır:

1. Var olan bir belgeyi tanıtıcısını alın.
1. Var olan bildirim yeni bildirimiyle değiştirerek yeni bir belge oluşturun.
1. Yeni belge döndürür.

Sonuna aşağıdaki kodu ekleyin `MakeConstAsync` yöntemi:

[!code-csharp[replace the declaration](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#ReplaceDocument  "Generate a new document by replacing the declaration")]

Kod düzeltmenizi denemek hazırdır.  Visual Studio ikinci bir örneğini Çözümleyicisi projeyi çalıştırmak için F5 tuşuna basın. İkinci Visual Studio örneğinde yeni bir C# konsol uygulaması projesi oluşturun ve Main yöntemi için sabit değerlerle başlatılan birkaç yerel değişken bildirimlerini ekleyin. Bunlar aşağıda gösterildiği gibi uyarı olarak raporlanır görürsünüz.

![Const uyarıları yapabilirsiniz](media/how-to-write-csharp-analyzer-code-fix/make-const-warning.png)

Devam eden birçok yaptık. Yapılabilecek bildirimleri altında dalgalı çizgiler vardır `const`. Ancak yine de yapmak için iş yok. Eklerseniz bu düzgün çalışır. `const` başlayarak bildirimlere `i`, ardından `j` ve son olarak `k`. Ancak eklerseniz `const` değiştiricisi ile başlayarak, farklı bir sıra i `k`, hataları, çözümleyici oluşturur: `k` bildirilemez `const`sürece `i` ve `j` her ikisi de zaten olan `const`. Değişkenleri bildirilir ve başlatılır farklı şekilde ele emin olmak için daha fazla analiz yapmak var.

## <a name="build-data-driven-tests"></a>Veri odaklı testler oluşturun

Çözümleyicisi ve kod basit bir const yapılabilmesi için tek bir bildirimde kasasındaki iş düzeltin. Bu uygulama hatalarını burada yapar, çok sayıda olası bildirim deyimleri vardır. Bu gibi durumlarda, şablon tarafından yazılmış birim testi kitaplığı birlikte çalışarak karşılayabilirsiniz. Visual Studio ikinci bir kopyası tekrar tekrar açarak değerinden daha hızlıdır.

Açık **MakeConstUnitTests.cs** birim test projesi dosyasında. Şablon bir Çözümleyicisi ve kod düzeltmesi birim testi için iki ortak desenler izleyen iki testten oluşturulan. `TestMethod1` Bu karakteri, bir Tanılama Çözümleyicisi sağlayan bir test desenini bildirmez gösterir. `TestMethod2` bir tanılama raporlama ve kod düzeltmesi çalıştıran desenini gösterir.

Aşağıdaki kod, Çözümleyicisi için neredeyse her test için bu iki Düzen biri. Birinci adım için veri odaklı testler bu testleri yeniden. Ardından, farklı test girişleri göstermek için yeni dize sabitleri ekleyerek yeni testler oluşturun kolay olacaktır.

Verimlilik için veri odaklı testler iki testleri yeniden düzenleme ilk adımdır. Ardından, her yeni test için birkaç dize sabitleri tanımlamak yeterlidir. Yeniden düzenleme sırasında her iki yöntem de daha iyi yeniden adlandırın. Değiştirin `TestMethod1` hiçbir tanılama sağlar. Bu test ile oluşturulur:

```csharp
[DataTestMethod]
[DataRow("")]
public void WhenTestCodeIsValidNoDiagnosticIsTriggered(string testCode)
{
    VerifyCSharpDiagnostic(testCode);
}
```

Bu test için yeni bir veri satırı bir uyarı tetiklemek, tanılama oluşmamalıdır herhangi bir kod parçası tanımlayarak oluşturabilirsiniz. Bu aşırı yüklemesini `VerifyCSharpDiagnostic` için kaynak kod parçasını harekete hiçbir tanılama olduğunda geçirir.  

Ardından, değiştirin `TestMethod2` bir tanılama oluşturulur sağlar. Bu test ve kaynak kod parçasını için uygulanan bir kod düzeltmesi:

```csharp
[DataTestMethod]
[DataRow(LocalIntCouldBeConstant, LocalIntCouldBeConstantFixed, 10, 13)]
public void WhenDiagosticIsRaisedFixUpdatesCode(
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

Yukarıdaki kod, beklenen Tanılama sonucu oluşturan koda da birkaç değişiklikler yaptınız. Kayıtlı genel sabitleri kullanan `MakeConst` Çözümleyicisi. Ayrıca, iki dize sabitleri için girdi ve sabit kaynak kullanır. Aşağıdaki dize sabitleri ekleyin `UnitTest` sınıfı:

[!code-csharp[string constants for fix test](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#FirstFixTest "string constants for fix test")]

Bunlar geçirmek emin olmak için bu iki testleri çalıştırın. Visual Studio'da açın **Test Gezgini** seçerek **Test** > **Windows** > **Test Gezgini**.  Baskı **tümünü Çalıştır** bağlantı.

## <a name="create-tests-for-valid-declarations"></a>Geçerli bildirimleri için testler oluşturma

Genel kural olarak, en az iş yapmak mümkün olan en kısa sürede Çözümleyicileri çıkılması gerekiyor. Visual Studio çağrıları kullanıcı düzenlemeleri kod Çözümleyicileri kayıtlı. Yanıt verme hızını önemli bir gereksinimdir. Çeşitli test çalışmaları, tanılama tetiklemelidir olmayan kod için vardır. Çözümleyici zaten bu testler, burada bir değişken başlatıldıktan sonra atanır çalışması birini işler. Bu durumda temsil etmek için testlerinizi aşağıdaki dize sabiti ekleyin:

[!code-csharp[variable assigned](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#VariableAssigned "a variable that is assigned after being initialized won't raise the diagnostic")]

Ardından, aşağıdaki kod parçacığında gösterildiği gibi bu test için veri satırı ekleyin:

```csharp
[DataTestMethod]
[DataRow(""),
 DataRow(VariableAssigned)]
public void WhenTestCodeIsValidNoDiagnosticIsTriggered(string testCode)
```

Bu test de geçer. Ardından, henüz işlenen henüz koşulları için sabitleri ekleyin:

* Zaten olan bildirimleri `const`zaten const çünkü:

   [!code-csharp[already const declaration](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#AlreadyConst "a declaration that is already const should not raise the diagnostic")]

* Kullanılacak herhangi bir değer olduğundan herhangi bir başlatıcıya sahip bildirimleri:

   [!code-csharp[declarations that have no initializer](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#NoInitializer "a declaration that has no initializer should not raise the diagnostic")]

* Derleme zamanı sabit olamayacağı Başlatıcı bir sabit olduğu bildirimleri:

   [!code-csharp[declarations where the initializer isn't const](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#InitializerNotConstant "a declaration where the initializer is not a compile-time constant should not raise the diagnostic")]

C# birden çok bildirimleri bir deyim olarak izin verdiğinden daha da karmaşık olabilir. Aşağıdaki test çalışması dize sabiti göz önünde bulundurun:

[!code-csharp[multiple initializers](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#MultipleInitializers "A declaration can be made constant only if all variables in that statement can be made constant")]

Değişken `i` sabiti, ancak değişkeni yapılabilir `j` olamaz. Bu nedenle, bu deyimi const bildirimi yapılamaz. Ekleme `DataRow` bildirimleri bu testler için:

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

Testlerinizi yeniden çalıştırın ve bu yeni test çalışmaları başarısız görürsünüz.

## <a name="update-your-analyzer-to-ignore-correct-declarations"></a>Doğru bildirimleri yoksaymayı, çözümleyici güncelleştir

Bazı geliştirmeler, çözümleyicisinin ihtiyacınız `AnalyzeNode` bu koşullara uyan kodu filtrelemek için yöntemi. Bu koşullar benzer değişiklikleri çözecektir için tüm ilgili koşulları değildirler. Aşağıdaki değişiklikleri yapın `AnalyzeNode`:

* Anlam analizi, tek bir değişken bildirimine incelenir. Bu kod içinde olması gereken bir `foreach` tüm değişkenleri araştıran döngü, aynı deyiminde bildirilen.
* Her bir başlatıcıya sahip gerekiyor değişken bildirildi.
* Her bildirilen değişkenin başlatıcısı, bir derleme zamanı sabiti olmalıdır.

İçinde `AnalyzeNode` yöntemi, özgün anlam analizi değiştirin:

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

Aşağıdaki kod parçacığıyla değiştirin:

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

İlk `foreach` döngü söz dizimsel analizini kullanarak her bir değişken bildirimini inceler. İlk denetimi değişkeni bir başlatıcıya sahip olacağını garanti eder. İkinci onay Başlatıcı bir sabit olmasını sağlar. İkinci döngü özgün anlam analizi sahiptir. Anlam denetimleri ayrı bir döngüde olduklarından performans üzerinde büyük bir etkisi vardır. Testlerinizi yeniden çalıştırın ve geçirmek tüm bunların görmeniz gerekir.

## <a name="add-the-final-polish"></a>Son Lehçe Ekle

Neredeyse bitti. İşlemek, Çözümleyicisi için birkaç başka koşullar vardır. Kullanıcı kod yazarken, visual Studio Çözümleyicileri çağırır. Bu, çözümleyici olacak durum genellikle derleme olmayan kod için çağrılır. Tanılama Çözümleyicisi'nin `AnalyzeNode` yöntemi için değişken türüne dönüştürülebilir sabit değer olup olmadığını denetlemez. Bu nedenle, geçerli uygulama Int gibi yanlış bir bildirimi sonsuza dek dönüştürecek miyim "abc" =' için bir yerel sabit. Bu koşul için bir kaynak dize sabitine ekleyin:

[!code-csharp[Mismatched types don't raise diagnostics](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#DeclarationIsInvalid "When the variable type and the constant type don't match, there's no diagnostic")]

Ayrıca, başvuru türleri düzgün işlenmez. Bir başvuru türü için izin verilen maksimum yalnızca sabit değer `null`, bu durumda dışındaki <xref:System.String?displayPropert=nameWIthType>, dize değişmez değerleri sağlar. Diğer bir deyişle, `const string s = "abc"` geçerli, ancak `const object s = "abc"` değil. Bu kod parçacığı bu koşulu doğrular:

[!code-csharp[Reference types don't raise diagnostics](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#DeclarationIsntString "When the variable type is a reference type other than string, there's no diagnostic")]

Eksiksiz olması için bir dize için sabit bir bildirimde oluşturabilirsiniz emin olmak için başka bir test eklemeniz gerekir. Aşağıdaki kod parçacığı, hem tanılama başlatır kodu ve kod düzeltme uygulandıktan sonra tanımlar:

[!code-csharp[string reference types raise diagnostics](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#ConstantIsString "When the variable type is string, it can be constant")]

Son olarak, bir değişken ile bildirilirse `var` anahtar sözcüğü, kod düzeltmesi yanlış şeyi yapar ve oluşturur bir `const var` bildirimi, C# dil tarafından desteklenmiyor. Bu hatayı düzeltmek için kod düzeltme değiştirmelisiniz `var` anahtar sözcüğü ile çıkarsanan tür adı:

[!code-csharp[var references need to use the inferred types](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#VarDeclarations "Declarations made using var must have the type replaced with the inferred type")]

Bu değişiklikler iki test için veri satırı bildirimler güncelleştirin. Aşağıdaki kod bu testleri ile tüm veri satır öznitelikleri gösterir:

[!code-csharp[The finished tests](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#FinishedTests "The finished tests for the make const analyzer")]

Neyse ki, yukarıdaki hataları tüm yeni öğrendiğiniz teknikleri kullanarak çözülebilir.

İlk hatayı düzeltmek için önce açın **DiagnosticAnalyzer.cs** ve burada her biri yerel bildirimin başlatıcıları sabit değerler atadığınız denetlenir foreach döngüsü bulun. Hemen _önce_ çağrı, ilk foreach döngüsü `context.SemanicModel.GetTypeInfo()` yerel bildirim türü hakkında ayrıntılı bilgi almak için:

```csharp
var variableTypeName = localDeclaration.Declaration.Type;
var variableType = context.SemanticModel.GetTypeInfo(variableTypeName).ConvertedType;
```

Ardından, içinde `foreach` döngü, her Başlatıcı, değişken türüne dönüştürülebilir olduğundan emin olmak için kontrol edin. Başlatıcı bir sabit olduğundan emin olduktan sonra aşağıdaki onay ekleyin:

```csharp
// Ensure that the initializer value can be converted to the type of the
// local declaration without a user-defined conversion.
var conversion = context.SemanticModel.ClassifyConversion(initializer.Value, variableType);
if (!conversion.Exists || conversion.IsUserDefined)
{
    return;
}
```

Sonraki değişiklik bir oluşturur. Kapanış küme ayracı, ilk foreach döngüsü önce sabiti, dize veya null olduğunda yerel bildirim türünü denetlemek için aşağıdaki kodu ekleyin.

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

Var değiştirmek için kod düzeltme sağlayıcısı biraz daha fazla kod yazmanız gereken ' anahtar sözcüğü doğru tür adı. Geri dönüp **CodeFixProvider.cs**. Ekleyeceğiniz kod, aşağıdaki adımları gerçekleştirir:

* Bildirimi olup olmadığını bir `var` bildirimi ve bu ise:
* Yeni bir tür için çıkarsanan tür oluşturun.
* Tür bildirimi bir diğer ad olmadığından emin olun. Bu nedenle, bildirmek için yasal ise `const var`.
* Emin olun `var` bu programda bir tür adı değil. (Bu durumda, `const var` geçerlidir).
* Tam tür adı basitleştirin

Bir sürü kod gibi görünüyor. Bu değil. Başlatır ve bildirir satırı değiştirin `newLocal` aşağıdaki kod ile. Başlatmadan sonra hemen gider `newModifiers`:

[!code-csharp[Replace Var designations](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#ReplaceVar "Replace a var designation with the explicit type")]

Bir eklemeniz gerekecektir `using` kullanılacak ifadesinin <xref:Microsoft.CodeAnalysis.Simplification.Simplifier> türü:

```csharp
using Microsoft.CodeAnalysis.Simplification;
```

Testlerinizi çalıştırmak ve tüm geçmelidir. Kendinize, tamamlanmış Çözümleyicisi'ni çalıştırarak kutlayın. Çözümleyici proje yüklenen Roslyn önizlemesi uzantısıyla Visual Studio ikinci bir örneğini çalıştırmak için CTRL + F5 tuşlarına basın.

* İkinci Visual Studio örneğinde yeni bir C# konsol uygulaması projesi oluşturma ve ekleme `int x = "abc";` Main yöntemi için. (Rağmen bir derleyici hatası beklendiği gibi), hiçbir uyarı ilk hata düzeltmesi sayesinde bu yerel değişken bildirimi olarak bildirilmelidir.
* Ardından, ekleme `object s = "abc";` Main yöntemi için. İkinci hata düzeltmesi nedeniyle hiçbir uyarı bildirilmelidir.
* Son olarak, kullanan başka bir yerel değişken Ekle `var` anahtar sözcüğü. Bir uyarı bildirilir ve sol altında bir öneri görünür görürsünüz.
* Düzenleyici giriş işaretinin dalgalı alt çizginin taşıyın ve CTRL tuşuna basın. Önerilen kod düzeltme görüntülenecek. Kod düzeltmenizi seçtikten sonra dikkat var' anahtar sözcüğü artık işlenir doğru.

Son olarak, aşağıdaki kodu ekleyin:

```csharp
int i = 2;
int j = 32;
int k = i + j;
```

Bu değişikliklerden sonra kırmızı dalgalı çizgiler yalnızca ilk iki değişkenlerde alın. Ekleme `const` hem `i` ve `j`, yeni bir uyarı alın `k` artık olabileceğinden `const`.

Tebrikler! Sorunu algılamak için üzerinde anında kod analizini yapar ve bunu düzeltmek için bir hızlı düzeltme sağlayan ilk .NET derleyici platformu uzantısı oluşturdunuz. Süreç boyunca birçok .NET derleyici Platformu SDK'sı (Roslyn API'leri) parçası olan API'leri kod öğrendiniz. Çalışmanızı karşı denetleyebilirsiniz [tamamlanan örnek](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/Tutorials/MakeConst) örnekleri GitHub depomuzda bulunan. Veya karşıdan yükleyebileceğiniz [projeyi ZIP dosyası](https://github.com/dotnet/samples/blob/master/csharp/roslyn-sdk/Tutorials/MakeConst.zip)

## <a name="other-resources"></a>Diğer kaynaklar

- [Söz dizimi Analizi ile çalışmaya başlama](../get-started/syntax-analysis.md)
- [Anlam Analizi ile çalışmaya başlama](../get-started/semantic-analysis.md)
