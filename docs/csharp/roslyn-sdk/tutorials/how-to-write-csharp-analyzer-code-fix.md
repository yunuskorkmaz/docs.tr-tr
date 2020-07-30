---
title: 'Öğretici: ilk çözümleyicinizi ve kod düzeltmesini yazma'
description: Bu öğretici, .NET derleyici SDK 'sını (Roslyn API 'Ler) kullanarak bir çözümleyici ve kod düzeltmesini oluşturmak için adım adım yönergeler sağlar.
ms.date: 08/01/2018
ms.custom: mvc
ms.openlocfilehash: e79907f364939462b7d0d5814c4752be23bcfdf3
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381599"
---
# <a name="tutorial-write-your-first-analyzer-and-code-fix"></a>Öğretici: ilk çözümleyicinizi ve kod düzeltmesini yazma

.NET Compiler Platform SDK, C# veya Visual Basic kodunu hedefleyen özel uyarılar oluşturmak için ihtiyacınız olan araçları sağlar. **Çözümleyici** , kuralınızın ihlallerini algılayan kod içerir. **Kod düzeltmenizi** ihlalin giderdiği kodu içerir. Uyguladığınız kurallar, kod yapısından, adlandırma kurallarına ve daha fazlasına yönelik kodlama stiline kadar herhangi bir şey olabilir. .NET Compiler Platform, geliştiricilerin kod yazmakta olduğu ve kodu düzeltmek için tüm Visual Studio Kullanıcı arabirimi özelliklerinin yanı sıra kodu çözmede, Visual Studio Hata Listesi, "ampul" önerilerini oluşturarak ve önerilen düzeltmelerin zengin önizlemesini göstererek, analiz çalıştırma çerçevesini sağlar.

Bu öğreticide, bir **çözümleyici** oluşturmayı ve Roslyn API 'lerini kullanarak bir **kod düzeltmesini** inceleyebilirsiniz. Çözümleyici, kaynak kodu analizini gerçekleştirmek ve kullanıcıya bir sorun bildirmek için bir yoldur. İsteğe bağlı olarak, bir çözümleyici kullanıcının kaynak kodunda bir değişikliği temsil eden bir kod düzeltmesini de sağlayabilir. Bu öğreticide, değiştirici kullanılarak bildirilebilecek ancak olmayan yerel değişken bildirimlerini bulan bir çözümleyici oluşturulur `const` . Eşlik eden kod düzeltilmesi, değiştiriciyi eklemek için bu bildirimleri değiştirir `const` .

## <a name="prerequisites"></a>Ön koşullar

> [!NOTE]
> Visual Studio **Analyzer with Code düzeltmesini (.NET Standard)** şablonunda, içinde bilinen bir hata var ve visual Studio 2019 sürüm 16,7 ' de düzeltilmelidir. Aşağıdaki değişiklikler yapılmadığı takdirde şablondaki projeler derlenmeyecektir:
>
> 1. **Araç**  >  **seçenekleri**  >  **NuGet Paket Yöneticisi**  >  **paket kaynakları** ' nı seçin
>    - Yeni bir kaynak eklemek için artı düğmesini seçin:
>    - **Kaynağı** olarak ayarlayın `https://dotnet.myget.org/F/roslyn-analyzers/api/v3/index.json` ve **Güncelle** 'yi seçin
> 1. **Çözüm Gezgini**, **Makeconst. vsix** projesine sağ tıklayın ve **Proje dosyasını Düzenle** ' yi seçin.
>    - `<AssemblyName>`Soneki eklemek için düğümü güncelleştirin `.Visx` :
>      - `<AssemblyName>MakeConst.Vsix</AssemblyName>`
>    - `<ProjectReference>`Değeri değiştirmek için 41 satırındaki düğümü güncelleştirin `TargetFramework` :
>      - `<ProjectReference Update="@(ProjectReference)" AdditionalProperties="TargetFramework=netstandard2.0" />`
> 1. *MakeConstUnitTests.cs* dosyasını *makeconst. test* projesinde güncelleştirin:
>    - 9. satırı aşağıdaki gibi değiştirin:
>      - `using Verify = Microsoft.CodeAnalysis.CSharp.Testing.MSTest.CodeFixVerifier<`
>    - Aşağıdaki yönteme göre satırı 24 ' ü değiştirin:
>      - `await Verify.VerifyAnalyzerAsync(test);`
>    - 62 satırını aşağıdaki yönteme değiştirin:
>      - `await Verify.VerifyCodeFixAsync(test, expected, fixtest);`

- [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/#visual-studio-2017-and-other-products)
- [Visual Studio 2019](https://www.visualstudio.com/downloads)

**.Net Compiler Platform SDK 'sını** Visual Studio yükleyicisi aracılığıyla yüklemeniz gerekir:

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

Çözümleyicinizi oluşturmak ve doğrulamak için birkaç adım vardır:

1. Çözümü oluşturun.
1. Çözümleyici adını ve açıklamasını kaydedin.
1. Rapor çözümleyici uyarıları ve önerileri.
1. Önerileri kabul etmek için kod düzeltmesini uygulayın.
1. Birim testler aracılığıyla Analizi geliştirme.

## <a name="explore-the-analyzer-template"></a>Çözümleyici şablonunu keşfet

Çözümleyici, kullanıcıya yerel sabitlere dönüştürülebileceği herhangi bir yerel değişken bildirimi bildirir. Örneğin, aşağıdaki kodu göz önünde bulundurun:

```csharp
int x = 0;
Console.WriteLine(x);
```

Yukarıdaki kodda `x` sabit bir değer atanır ve hiçbir şekilde değiştirilmez. Değiştirici kullanılarak bildirilebilecek `const` :

```csharp
const int x = 0;
Console.WriteLine(x);
```

Bir değişkenin sabit bir şekilde yapılıp yapılmayacağını belirleme, değişken için sözdizimi analizi, başlatıcı ifadesinin sabit Analizi ve değişkenin hiçbir şekilde yazılmaması için veri akışı analizi gerektirir. .NET Compiler Platform, bu çözümlemenin daha kolay hale getirebilmesini sağlayan API 'Ler sağlar. İlk adım, **kod düzeltilme projesi ile** yeni bir C# Çözümleyicisi oluşturmaktır.

- Visual Studio 'da yeni proje iletişim kutusunu göstermek için **dosya > yeni > proje..** . öğesini seçin.
- **Visual C# > genişletilebilirlik**altında, **kod düzeltmesine sahip çözümleyici 'yi (.NET Standard)** seçin.
- Projenizi "**Makeconst**" olarak adlandırın ve Tamam ' a tıklayın.

Code düzeltmesini içeren çözümleyici, üç proje oluşturur: biri çözümleyici ve kod düzeltmesini içerir, ikincisi bir birim testi projisidir ve üçüncüsü VSıX projisidir. Varsayılan başlangıç projesi VSıX projem ' dir. VSıX projesini başlatmak için <kbd>F5</kbd> tuşuna basın. Bu, yeni çözümleyicinizi yükleyen ikinci bir Visual Studio örneğini başlatır.

> [!TIP]
> Çözümleyicinizi çalıştırdığınızda, Visual Studio 'nun ikinci bir kopyasını başlatabilirsiniz. Bu ikinci kopya ayarları depolamak için farklı bir kayıt defteri kovanı kullanır. Bu, Visual Studio 'nun iki kopyasında görsel ayarları ayırt etmenize olanak sağlar. Visual Studio 'nun deneysel çalıştırması için farklı bir tema seçebilirsiniz. Ayrıca, Visual Studio 'nun deneysel çalıştırmasını kullanarak ayarlarınızı dolaşıyor veya Visual Studio hesabınızda oturum açmayın. Bu, ayarları farklı tutar.

Az önce başlattığınız ikinci Visual Studio örneğinde, yeni bir C# konsol uygulaması projesi oluşturun (.NET Core veya .NET Framework Project, kaynak düzeyinde çalışır.) Simgenin üzerine dalgalı alt çizgiyle gelin ve bir çözümleyici tarafından sunulan uyarı metni görüntülenir.

Şablon, aşağıdaki şekilde gösterildiği gibi tür adında küçük harfler içeren her tür bildiriminde uyarı raporlayan bir çözümleyici oluşturur:

![Çözümleyici raporlama uyarısı](media/how-to-write-csharp-analyzer-code-fix/report-warning.png)

Şablon Ayrıca, küçük harf karakter içeren herhangi bir tür adını tüm büyük harflere değiştiren bir kod düzeltmesini de sağlar. Önerilen değişiklikleri görmek için uyarıyla birlikte görüntülenecek ampule tıklayabilirsiniz. Önerilen değişiklikler kabul edildiğinde, tür adı ve çözümdeki bu türe yapılan tüm başvurular güncelleştirilir. İlk çözümleyici 'yi eylemde gördüğünüze göre, ikinci Visual Studio örneğini kapatın ve çözümleyici projenize geri dönün.

Visual Studio 'nun ikinci bir kopyasını başlatmanız ve çözümleyicinizdeki her değişikliği test etmek için yeni kod oluşturmanız gerekmez. Şablon sizin için bir birim testi projesi de oluşturur. Bu proje iki test içerir. `TestMethod1`Bir tanılamayı tetiklemeden kodu çözümleyen testin tipik biçimini gösterir. `TestMethod2`Bir tanılamayı tetikleyen testin biçimini gösterir ve ardından önerilen bir kod düzeltmesini uygular. Çözümleyicinizi ve kod düzeltmesini oluştururken, çalışmanızı doğrulamak üzere farklı kod yapıları için testler yazacaksınız. Çözümleyiciler için birim testleri, Visual Studio ile etkileşimli olarak test edilmesine kıyasla çok daha hızlıdır.

> [!TIP]
> Çözümleyici birim testleri, hangi kod yapılarının çözümleyicinizi tetikleyemediğini bildiğiniz ve bu harika bir araçtır. Visual Studio 'nun başka bir kopyasına çözümleyicinizi yüklemek, henüz düşünmemiş olan yapıları keşfetmeye ve bulmaya yönelik harika bir araçtır.

## <a name="create-analyzer-registrations"></a>Çözümleyici kayıtları oluşturma

Şablon, `DiagnosticAnalyzer` **MakeConstAnalyzer.cs** dosyasında başlangıç sınıfını oluşturur. Bu ilk çözümleyici, her çözümleyici 'nin iki önemli özelliğini gösterir.

- Her Tanılama Çözümleyicisi `[DiagnosticAnalyzer]` , üzerinde çalıştığı dili açıklayan bir öznitelik sağlamalıdır.
- Her Tanılama Çözümleyicisi <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer> sınıfından türetilmelidir.

Şablon, herhangi bir çözümleyici 'nin parçası olan temel özellikleri de gösterir:

1. Kaydetme eylemleri. Eylemler, çözümleyicinizi ihlalleri için kodu incelemek üzere tetiklemesi gereken kod değişikliklerini temsil eder. Visual Studio, kayıtlı bir eylemle eşleşen kod düzenlemeleri algıladığında, çözümleyici 'nin kayıtlı yöntemini çağırır.
1. Tanılama oluşturun. Çözümleyicisi bir ihlal algıladığında, bu, ihlalin kullanıcısına bildirimde bulunan Visual Studio 'Nun kullandığı bir tanılama nesnesi oluşturur.

Eylemini geçersiz kılmanızda kaydedebilirsiniz <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer.Initialize(Microsoft.CodeAnalysis.Diagnostics.AnalysisContext)?displayProperty=nameWithType> . Bu öğreticide, yerel bildirimleri arayan **sözdizimi düğümlerini** ziyaret edeceğiz ve hangilerinin sabit değerlere sahip olduğunu görürsünüz. Bir bildirim sabitlenebilir, çözümleyici bir tanılama oluşturup rapor eder.

İlk adım, kayıt sabitlerini ve yöntemini güncelleştirmek ve `Initialize` Bu sabitler "const yap" çözümleyicisini göstermek için kullanılır. Dize sabitlerinin çoğu dize kaynak dosyasında tanımlanmıştır. Daha kolay yerelleştirme için bu uygulamayı izlemeniz gerekir. **Makeconst** çözümleyici projesi için **Resources. resx** dosyasını açın. Bu, kaynak düzenleyicisini görüntüler. Dize kaynaklarını aşağıdaki gibi güncelleştirin:

- `AnalyzerTitle`"Değişken sabit hale getirilebilir" olarak değiştirin.
- `AnalyzerMessageFormat`"Sabit yapılabilir" olarak değiştirin.
- `AnalyzerDescription`"Sabit yap" olarak değiştirin.

Ayrıca, **erişim değiştirici** açılan öğesini olarak değiştirin `public` . Bu, birim testlerinde bu sabitleri kullanmayı kolaylaştırır. İşiniz bittiğinde, kaynak Düzenleyicisi aşağıdaki şekilde görünür:

![Dize kaynaklarını Güncelleştir](media/how-to-write-csharp-analyzer-code-fix/update-string-resources.png)

Geri kalan değişiklikler çözümleyici dosyasıdır. Visual Studio 'da **MakeConstAnalyzer.cs** açın. Semboller üzerinde çalışan bir eylemden, söz dizimi üzerinde davranan bir eylemi değiştirin. `MakeConstAnalyzerAnalyzer.Initialize`Yönteminde, simgeleri üzerinde eylemi kaydeden satırı bulun:

```csharp
context.RegisterSymbolAction(AnalyzeSymbol, SymbolKind.NamedType);
```

Aşağıdaki satırla değiştirin:

[!code-csharp[Register the node action](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstAnalyzer.cs#RegisterNodeAction "Register a node action")]

Bu değişiklikten sonra `AnalyzeSymbol` yöntemini silebilirsiniz. Bu çözümleyici <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.LocalDeclarationStatement?displayProperty=nameWithType> , deyimleri inceler <xref:Microsoft.CodeAnalysis.SymbolKind.NamedType?displayProperty=nameWithType> . `AnalyzeNode`Altında Red dalgalı çizgiler olduğuna dikkat edin. Az önce eklediğiniz kod `AnalyzeNode` bildirilmemiş bir yönteme başvurur. Aşağıdaki kodu kullanarak bu yöntemi bildirin:

```csharp
private void AnalyzeNode(SyntaxNodeAnalysisContext context)
{
}
```

`Category`Aşağıdaki kodda gösterildiği gibi, **MakeConstAnalyzer.cs** içinde "kullanım" olarak değiştirin:

```csharp
private const string Category = "Usage";
```

## <a name="find-local-declarations-that-could-be-const"></a>Const olabilecek yerel bildirimleri bul

Yöntemin ilk sürümünü yazmak zaman `AnalyzeNode` . Bu, `const` Aşağıdaki kod gibi olabilecek, ancak olmayan tek bir yerel bildirime bakmalıdır:

```csharp
int x = 0;
Console.WriteLine(x);
```

İlk adım, yerel bildirimleri bulledir. Aşağıdaki kodu `AnalyzeNode` **MakeConstAnalyzer.cs**içine ekleyin:

```csharp
var localDeclaration = (LocalDeclarationStatementSyntax)context.Node;
```

Bu atama, çözümleyici yerel bildirimlerinizde değişiklikler ve yalnızca yerel bildirimler için kaydedildiği için her zaman başarılı olur. Başka hiçbir düğüm türü, yönteminiz için bir çağrı tetiklemiyor `AnalyzeNode` . Sonra, herhangi bir değiştiricinin bildirimini kontrol edin `const` . Bunları bulursanız anında geri dönün. Aşağıdaki kod, `const` Yerel bildirimde herhangi bir değiştirici arar:

```csharp
// make sure the declaration isn't already const:
if (localDeclaration.Modifiers.Any(SyntaxKind.ConstKeyword))
{
    return;
}
```

Son olarak, değişkenin olup olmadığını kontrol etmeniz gerekir `const` . Bu, başlatıldıktan sonra hiçbir şekilde atanmadığından emin olmak anlamına gelir.

Kullanarak bazı semantik analizler gerçekleştirirsiniz <xref:Microsoft.CodeAnalysis.Diagnostics.SyntaxNodeAnalysisContext> . `context`Yerel değişken bildiriminin yapılıp yapılmayacağını anlamak için bağımsız değişkenini kullanırsınız `const` . <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType>Tek bir kaynak dosyasındaki tüm anlam bilgilerini temsil eder. [Anlam modellerini](../work-with-semantics.md)içeren makalede daha fazla bilgi edinebilirsiniz. <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType>' Yi, yerel bildirim deyimindeki veri akışı analizini gerçekleştirmek için kullanacaksınız. Ardından, bu veri akışı analizinin sonuçlarını kullanarak yerel değişkenin başka bir yerde yeni bir değerle yazılmadığından emin olun. <xref:Microsoft.CodeAnalysis.ModelExtensions.GetDeclaredSymbol%2A>Değişkenini almak için genişletme yöntemini çağırın <xref:Microsoft.CodeAnalysis.ILocalSymbol> ve <xref:Microsoft.CodeAnalysis.DataFlowAnalysis.WrittenOutside%2A?displayProperty=nameWithType> veri akışı analizinin koleksiyonuna dahil olmadığını kontrol edin. Yönteminin sonuna aşağıdaki kodu ekleyin `AnalyzeNode` :

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

Yeni eklenen kod, değişkenin değiştirilmediğinden emin olur ve bu nedenle yapılabilir `const` . Tanılamayı yükseltme zamanı. Aşağıdaki kodu içine son satır olarak ekleyin `AnalyzeNode` :

```csharp
context.ReportDiagnostic(Diagnostic.Create(Rule, context.Node.GetLocation()));
```

<kbd>F5</kbd> 'e basarak çözümleyicinizi çalıştırmak için ilerleme durumunu kontrol edebilirsiniz. Daha önce oluşturduğunuz konsol uygulamasını yükleyebilir ve sonra şu test kodunu ekleyebilirsiniz:

```csharp
int x = 0;
Console.WriteLine(x);
```

Ampul görünmelidir ve çözümleyici 'niz bir tanılama raporlemelidir. Ancak ampul, şablon tarafından oluşturulan kod düzeltmesini hala kullanır ve bunun büyük bir durum oluşturabileceklerini söyler. Sonraki bölümde, kod düzeltmesinin nasıl yazılacağı açıklanmaktadır.

## <a name="write-the-code-fix"></a>Kod düzeltmesini yazın

Bir çözümleyici, bir veya daha fazla kod düzeltmesi sağlayabilir. Kod onarımı, bildirilen sorunu ele alan bir düzenleme tanımlar. Oluşturduğunuz çözümleyici için, const anahtar sözcüğünü ekleyen bir kod düzeltmesini sağlayabilirsiniz:

```csharp
const int x = 0;
Console.WriteLine(x);
```

Kullanıcı onu düzenleyicide ampul kullanıcı arabiriminden seçer ve Visual Studio kodu değiştirir.

Şablon tarafından eklenen **MakeConstCodeFixProvider.cs** dosyasını açın.  Bu kod onarımı, tanılama çözümleyici 'niz tarafından üretilen tanılama KIMLIĞI 'ne zaten kablolu, ancak doğru kod dönüşümünü uygulamıyor. Öncelikle bazı şablon kodunu kaldırmalısınız. Başlık dizesini "sabit yap" olarak değiştirin:

[!code-csharp[Update the CodeFix title](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#CodeFixTitle "Update the CodeFix title")]

Sonra, yöntemini silin `MakeUppercaseAsync` . Artık geçerli değildir.

Tüm kod onarma sağlayıcıları öğesinden türetilir <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider> . Bunlar, <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider.RegisterCodeFixesAsync(Microsoft.CodeAnalysis.CodeFixes.CodeFixContext)?displayProperty=nameWithType> kullanılabilir kod düzeltmelerini raporlamak için tüm geçersiz kılınır. ' De `RegisterCodeFixesAsync` , <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> tanı ile eşleştirmek için Aradığınız üst düğüm türünü bir olarak değiştirin:

[!code-csharp[Find local declaration node](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#FindDeclarationNode  "Find the local declaration node that raised the diagnostic")]

Sonra, bir kod düzeltmesini kaydetmek için son satırı değiştirin. Bu değişiklik, değiştiricinin mevcut bir bildirime eklenmesinin sonucu olan yeni bir belge oluşturur `const` :

[!code-csharp[Register the new code fix](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#RegisterCodeFix  "Register the new code fix")]

Simgenin üzerine yeni eklediğiniz kodda kırmızı dalgalı çizgiler fark edeceksiniz `MakeConstAsync` . `MakeConstAsync`Aşağıdaki kodu beğenmek için bir bildirim ekleyin:

```csharp
private async Task<Document> MakeConstAsync(Document document,
   LocalDeclarationStatementSyntax localDeclaration,
   CancellationToken cancellationToken)
{
}
```

Yeni `MakeConstAsync` yönteminiz, <xref:Microsoft.CodeAnalysis.Document> kullanıcının kaynak dosyasını temsil eden yeni bir bildirim içeren yeni bir öğesine dönüştürür <xref:Microsoft.CodeAnalysis.Document> `const` .

`const`Bildirim ifadesinin önüne eklemek için yeni bir anahtar sözcük belirteci oluşturursunuz. Önce bildirim bildiriminin ilk belirtecinden önde gelen her türlü boşluğu kaldırmak ve belirtece eklemek konusunda dikkatli olun `const` . `MakeConstAsync` yöntemine aşağıdaki kodu ekleyin:

[!code-csharp[Create a new const keyword token](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#CreateConstToken  "Create the new const keyword token")]

Ardından, `const` aşağıdaki kodu kullanarak belirteci bildirime ekleyin:

```csharp
// Insert the const token into the modifiers list, creating a new modifiers list.
var newModifiers = trimmedLocal.Modifiers.Insert(0, constToken);
// Produce the new local declaration.
var newLocal = trimmedLocal
    .WithModifiers(newModifiers)
    .WithDeclaration(localDeclaration.Declaration);
```

Ardından, yeni bildirimi C# biçimlendirme kurallarıyla eşleşecek şekilde biçimlendirin. Değişikliklerinizi varolan kodla eşleşecek şekilde biçimlendirmek daha iyi bir deneyim oluşturur. Mevcut koddan hemen sonra aşağıdaki ifadeyi ekleyin:

[!code-csharp[Format the new declaration](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#FormatLocal  "Format the new declaration")]

Bu kod için yeni bir ad alanı gereklidir. Aşağıdaki `using` yönergeyi dosyanın en üstüne ekleyin:

```csharp
using Microsoft.CodeAnalysis.Formatting;
```

Son adım, düzenlemenizi yapmak için kullanılır. Bu işlemin üç adımı vardır:

1. Mevcut belgeye yönelik bir tanıtıcı alın.
1. Mevcut bildirimi yeni bildirimle değiştirerek yeni bir belge oluşturun.
1. Yeni belgeyi döndür.

Yönteminin sonuna aşağıdaki kodu ekleyin `MakeConstAsync` :

[!code-csharp[replace the declaration](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#ReplaceDocument  "Generate a new document by replacing the declaration")]

Kod düzeltmeizin denemeye hazırlanıyor.  Visual Studio 'nun ikinci bir örneğinde çözümleyici projesini çalıştırmak için <kbd>F5</kbd> tuşuna basın. İkinci Visual Studio örneğinde, yeni bir C# konsol uygulaması projesi oluşturun ve Main yöntemine sabit değerlerle başlatılan birkaç yerel değişken bildirimi ekleyin. Bunların uyarı olarak raporlandıklarından aşağıda gösterildiği gibi göreceksiniz.

![Const uyarıları yapabilir](media/how-to-write-csharp-analyzer-code-fix/make-const-warning.png)

Çok sayıda ilerleme yaptınız. Bildirimlerin altında dalgalı çizgiler vardır `const` . Ancak yine de devam eden bir iş var. Bu `const` `i` , sonrasında `j` ve son olarak bulunan bildirimlere eklerseniz bu işe yarar `k` . Ancak, `const` değiştiricisini ile başlayarak farklı bir sırada eklerseniz `k` , çözümleyici 'niz hata oluşturuyor: `k` `const` `i` ve ikisi birden olmadığı için bildirilemez `j` `const` . Değişkenlerin bildirilebilecek ve başlatılabileceği farklı yolları işlediğinizden emin olmak için daha fazla analiz yapmanız gerekir.

## <a name="build-data-driven-tests"></a>Veri odaklı testler oluşturun

Çözümleyici ve kod düzeltmesizin const hale getirilebilir tek bir bildirimin basit bir durumunda çalışır. Bu uygulamanın hata yaptığı çok sayıda olası bildirim deyimi vardır. Şablon tarafından yazılan birim testi kitaplığıyla çalışarak bu durumları ele alacağız. Visual Studio 'nun ikinci bir kopyasını art arda açmadan çok daha hızlıdır.

Birim testi projesinde **MakeConstUnitTests.cs** dosyasını açın. Şablon, bir çözümleyici ve kod düzelme birimi testi için iki ortak deseni izleyen iki test oluşturmuştur. `TestMethod1`çözümleyicinin ne zaman bir tanılama bildirmemesini sağlayan bir testin modelini gösterir. `TestMethod2`Bir tanılamayı raporlamak ve kod düzeltmesini çalıştırmak için bir model gösterir.

Çözümleyicinizi neredeyse her test için kod, bu iki desenden birini izler. İlk adımda, bu testlerin veri odaklı testler olarak yeniden kullanılabilir. Daha sonra, farklı test girişlerini temsil etmek için yeni dize sabitleri ekleyerek yeni testlerin oluşturulması kolay olur.

Verimlilik için ilk adım, veri odaklı testlerde iki testi yeniden düzenleme. Ardından, her yeni test için yalnızca birkaç dize sabiti tanımlamanız gerekir. Yeniden düzenleme yaparken her iki yöntemi de daha iyi adlarla yeniden adlandırın. `TestMethod1`Herhangi bir tanılama işlemi yapılmasını sağlayan bu testle değiştirin:

```csharp
[DataTestMethod]
[DataRow("")]
public void WhenTestCodeIsValidNoDiagnosticIsTriggered(string testCode)
{
    VerifyCSharpDiagnostic(testCode);
}
```

Tanılamanın bir uyarı tetiklemesine neden olmaması gereken herhangi bir kod parçasını tanımlayarak, bu test için yeni bir veri satırı oluşturabilirsiniz. `VerifyCSharpDiagnostic`Kaynak kod parçası için hiçbir Tanılama tetikleniyorsa, bu geçiş yükü geçer.

Sonra, `TestMethod2` bir Tanılamanın ortaya çıkarılmasını ve kaynak kod parçası için bir kod düzeltmesinin uygulanmasını sağlayan bu testle değiştirin:

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

Yukarıdaki kod ayrıca, beklenen tanılama sonucunu oluşturan kodda birkaç değişiklik yaptı. Çözümleyici 'de kayıtlı olan genel sabitleri kullanır `MakeConst` . Ayrıca, giriş ve sabit kaynak için iki dize sabiti kullanır. Sınıfına aşağıdaki dize sabitlerini ekleyin `UnitTest` :

[!code-csharp[string constants for fix test](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#FirstFixTest "string constants for fix test")]

Geçirdiklerinden emin olmak için bu iki testi çalıştırın. Visual Studio 'da **, test** **Test Explorer**  >  **Windows**  >  **Test Gezgini**' ni seçerek test Gezginini açın. Ardından **Tümünü Çalıştır** bağlantısını seçin.

## <a name="create-tests-for-valid-declarations"></a>Geçerli bildirimler için testler oluşturma

Genel bir kural olarak, çözümleyicilerin olabildiğince çabuk çıkması gerekir ve en az iş yapılır. Visual Studio, Kullanıcı kodu düzenlediği için kayıtlı çözümleyiciler çağırır. Yanıt verme bir anahtar gereksinimidir. Tanılamasını yükseltmemelidir kod için birkaç test çalışması vardır. Çözümleyicisi zaten bu testlerin birini, bir değişkenin başlatıldıktan sonra atandığı durumu işler. Bu durumu göstermek için testlerinize aşağıdaki dize sabitini ekleyin:

[!code-csharp[variable assigned](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#VariableAssigned "a variable that is assigned after being initialized won't raise the diagnostic")]

Ardından, aşağıdaki kod parçacığında gösterildiği gibi bu test için bir veri satırı ekleyin:

```csharp
[DataTestMethod]
[DataRow(""),
 DataRow(VariableAssigned)]
public void WhenTestCodeIsValidNoDiagnosticIsTriggered(string testCode)
```

Bu test da geçer. Daha sonra, henüz işlememiş olan koşullar için sabitler ekleyin:

- Zaten const olduklarından, zaten sabit olan bildirimler `const` :

   [!code-csharp[already const declaration](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#AlreadyConst "a declaration that is already const should not raise the diagnostic")]

- Başlatıcısı olmayan bildirimler, kullanılacak bir değer yoktur:

   [!code-csharp[declarations that have no initializer](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#NoInitializer "a declaration that has no initializer should not raise the diagnostic")]

- Başlatıcıya bir sabit olmadığı ve derleme zamanı sabitleri olmadıkları için bildirim:

   [!code-csharp[declarations where the initializer isn't const](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#InitializerNotConstant "a declaration where the initializer is not a compile-time constant should not raise the diagnostic")]

C# birden çok bildirime tek bir bildirimde Izin verdiğinden daha karmaşık olabilir. Aşağıdaki test çalışması dize sabitini göz önünde bulundurun:

[!code-csharp[multiple initializers](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#MultipleInitializers "A declaration can be made constant only if all variables in that statement can be made constant")]

Değişken `i` sabit hale getirilebilir, ancak değişken `j` olamaz. Bu nedenle, bu ifade bir const bildirimi yapılamaz. `DataRow`Tüm bu testler için bildirimleri ekleyin:

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

Testlerinizi yeniden çalıştırın ve bu yeni test çalışmalarını başarısız görürsünüz.

## <a name="update-your-analyzer-to-ignore-correct-declarations"></a>Çözümleyicinizi doğru bildirimleri yoksayacak şekilde güncelleştirme

`AnalyzeNode`Bu koşullara uyan kodu filtrelemek için çözümleyicinizdeki bazı geliştirmeler yapmanız gerekir. Bunlar ilgili tüm koşullardır, böylece benzer değişiklikler bu koşulların tümünü düzeltir. Aşağıdaki değişiklikleri yapın `AnalyzeNode` :

- Anlam analiziniz tek bir değişken bildirimi inceledi. Bu kodun, `foreach` aynı bildirimde belirtilen tüm değişkenleri inceleyen bir döngüde olması gerekir.
- Her beyan edilen değişkenin bir başlatıcıya sahip olması gerekir.
- Her bir derlenen değişkenin başlatıcısı bir derleme zamanı sabiti olmalıdır.

`AnalyzeNode`Yöntemdeki özgün anlam analizini değiştirin:

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

Aşağıdaki kod parçacığı ile:

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

İlk `foreach` döngü, söz dizimi analizini kullanarak her bir değişken bildirimini inceler. İlk denetim, değişkenin bir başlatıcıya sahip olduğunu garanti eder. İkinci denetim, başlatıcının bir sabit olduğunu garanti eder. İkinci döngünün özgün anlam analizi vardır. Performans üzerinde daha fazla etkisi olduğundan anlam denetimleri ayrı bir döngüde bulunur. Testlerinizi yeniden çalıştırın ve hepsini bir kez görmeniz gerekir.

## <a name="add-the-final-polish"></a>Son Lehçe 'ı ekleyin

Neredeyse bitti. Çözümleyicinizi işlemek için birkaç koşul daha vardır. Visual Studio, Kullanıcı kod yazarken Çözümleyicileri çağırır. Bu durum genellikle çözümleyicinizi derlenmeyen kod için çağrılacaktır. Tanılama Çözümleyicisi yöntemi, `AnalyzeNode` sabit değerin değişken türüne dönüştürülebilir olup olmadığını kontrol etmez. Bu nedenle, geçerli uygulama int ı = "abc" ' gibi yanlış bir bildirimi yerel bir sabit 'e dönüştürmelidir. Bu koşul için bir kaynak dize sabiti ekleyin:

[!code-csharp[Mismatched types don't raise diagnostics](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#DeclarationIsInvalid "When the variable type and the constant type don't match, there's no diagnostic")]

Ayrıca, başvuru türleri düzgün işlenmez. Bir başvuru türü için izin verilen tek sabit değeri, `null` Bu durum dışında, <xref:System.String?displayProperty=nameWithType> dize değişmezine izin verir. Diğer bir deyişle, geçerlidir `const string s = "abc"` ancak `const object s = "abc"` değildir. Bu kod parçacığı bu durumu doğrular:

[!code-csharp[Reference types don't raise diagnostics](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#DeclarationIsntString "When the variable type is a reference type other than string, there's no diagnostic")]

Tam olarak, bir dize için sabit bildirim oluşturabilmeniz için başka bir test eklemeniz gerekir. Aşağıdaki kod parçacığı, hem tanılamayı başlatan kodu hem de düzeltilme uygulandıktan sonra kodu tanımlar:

[!code-csharp[string reference types raise diagnostics](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#ConstantIsString "When the variable type is string, it can be constant")]

Son olarak, bir değişken `var` anahtar sözcükle bildirilirse, kod düzeltilmesi yanlış şeyi yapar ve `const var` C# dili tarafından desteklenmeyen bir bildirim oluşturur. Bu hatayı onarmak için, kod düzeltmesinin `var` anahtar sözcüğünün çıkarılan türün adıyla yerine gelmelidir:

[!code-csharp[var references need to use the inferred types](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#VarDeclarations "Declarations made using var must have the type replaced with the inferred type")]

Bu değişiklikler her iki test için de veri satırı bildirimlerini güncelleştirir. Aşağıdaki kod, tüm veri satırı öznitelikleriyle bu testleri gösterir:

[!code-csharp[The finished tests](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#FinishedTests "The finished tests for the make const analyzer")]

Neyse ki, yukarıdaki hataların tümü, az önce öğrendiğiniz tekniklerin kullanılmasıyla çözülebilir.

İlk hatayı onarmak için önce **DiagnosticAnalyzer.cs** açın ve her bir yerel bildirimin başlatıcılarının her birinin, sabit değerlerle atanmasını sağlamak için her birinin kontrol edildiği foreach döngüsünü bulun. İlk foreach döngüsünden hemen _önce_ , `context.SemanticModel.GetTypeInfo()` Yerel bildirimin belirtilen türü hakkında ayrıntılı bilgi almak için çağırın:

```csharp
var variableTypeName = localDeclaration.Declaration.Type;
var variableType = context.SemanticModel.GetTypeInfo(variableTypeName).ConvertedType;
```

Sonra, `foreach` döngünüz içinde, değişken türüne dönüştürülebilir olduğundan emin olmak için her başlatıcıyı kontrol edin. Başlatıcının bir sabit olduğundan emin olduktan sonra aşağıdaki denetimi ekleyin:

```csharp
// Ensure that the initializer value can be converted to the type of the
// local declaration without a user-defined conversion.
var conversion = context.SemanticModel.ClassifyConversion(initializer.Value, variableType);
if (!conversion.Exists || conversion.IsUserDefined)
{
    return;
}
```

Sonraki değişiklik, son bir üzerinde derleme oluşturur. İlk foreach döngüsünün kapanış küme ayracından önce, sabit bir dize veya null olduğunda yerel bildirimin türünü denetlemek için aşağıdaki kodu ekleyin.

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

Anahtar sözcüğünü doğru tür adıyla değiştirmek için kod düzeltme sağlayıcınızda bir bit daha daha kod yazmalısınız `var` . **CodeFixProvider.cs**'e geri dönün. Ekleyeceğiniz kod aşağıdaki adımları yapar:

- Bildirimin bir bildirim olup olmadığını `var` ve şu şekilde olduğunu kontrol edin:
- Çıkarsanan tür için yeni bir tür oluşturun.
- Tür bildiriminin bir diğer ad olmadığından emin olun. Varsa, bildirim için geçerlidir `const var` .
- `var`Bunun, bu programda bir tür adı olmadığından emin olun. (Varsa, `const var` geçerlidir).
- Tam tür adını basitleştirme

Bu çok fazla kod gibi seslerden oluşur. Bu değildir. Bildiren ve Başlatan satırı `newLocal` aşağıdaki kodla değiştirin. Başlatma işleminden hemen sonra geçer `newModifiers` :

[!code-csharp[Replace Var designations](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#ReplaceVar "Replace a var designation with the explicit type")]

`using`Türünü kullanmak için bir yönerge eklemeniz gerekir <xref:Microsoft.CodeAnalysis.Simplification.Simplifier> :

```csharp
using Microsoft.CodeAnalysis.Simplification;
```

Testlerinizi çalıştırın ve hepsi başarılı olmalıdır. Tamamlanmış çözümleyicinizi çalıştırarak kendiniz kutlama yapın. <kbd>Ctrl</kbd> + Visual Studio 'nun ikinci bir örneğinde, Roslyn önizleme uzantısı yüklenmiş olarak çözümleyici projesini çalıştırmak için CTRL<kbd>F5</kbd> tuşuna basın.

- İkinci Visual Studio örneğinde, yeni bir C# konsol uygulaması projesi oluşturun ve `int x = "abc";` Main yöntemine ekleyin. İlk hata düzelttiğinde, bu yerel değişken bildirimi için hiçbir uyarı bildirilmemelidir (ancak beklenen bir derleyici hatası var).
- Sonra `object s = "abc";` Main yöntemine ekleyin. İkinci hata düzelttiğinden uyarı bildirilmemelidir.
- Son olarak, anahtar sözcüğünü kullanan başka bir yerel değişken ekleyin `var` . Bir uyarının bildirilmekte olduğunu ve sol tarafta bir öneri göründüğünü görürsünüz.
- Düzenleyici giriş işaretini dalgalı alt çizginin üzerine taşıyın ve <kbd>CTRL</kbd>tuşuna basın + <kbd>.</kbd> önerilen kod düzeltmesini göstermek için. Kod düzeltmesini seçtikten sonra `var` anahtar sözcüğünün artık doğru şekilde işlendiğini unutmayın.

Son olarak, aşağıdaki kodu ekleyin:

```csharp
int i = 2;
int j = 32;
int k = i + j;
```

Bu değişikliklerden sonra, yalnızca ilk iki değişkene kırmızı dalgalı çizgiler alırsınız. Hem hem de `const` ' ye ekleyin `i` `j` , artık bu şekilde bir uyarı alabilirsiniz `k` `const` .

Tebrikler! Bir sorunu tespit etmek ve düzeltmek için hızlı bir düzeltme sağlamak üzere anında çalıştırılan kod analizini gerçekleştiren ilk .NET Compiler Platform uzantınızı oluşturdunuz. Bu şekilde, .NET Compiler Platform SDK 'nın (Roslyn API 'Ler) parçası olan kod API 'lerinin birçoğunu öğrendiniz. Çalışmalarımızı örnek GitHub deponuzdaki [tamamlanmış örnekle](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/Tutorials/MakeConst) karşı denetleyebilirsiniz.

## <a name="other-resources"></a>Diğer kaynaklar

- [Sözdizimi analizini kullanmaya başlayın](../get-started/syntax-analysis.md)
- [Anlamsal analiz ile çalışmaya başlama](../get-started/semantic-analysis.md)
