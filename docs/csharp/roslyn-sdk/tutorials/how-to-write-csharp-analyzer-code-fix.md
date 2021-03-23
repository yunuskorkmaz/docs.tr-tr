---
title: 'Öğretici: ilk çözümleyicinizi ve kod düzeltmesini yazma'
description: Bu öğretici, .NET derleyici SDK 'sını (Roslyn API 'Ler) kullanarak bir çözümleyici ve kod düzeltmesini oluşturmak için adım adım yönergeler sağlar.
ms.date: 03/02/2021
ms.custom: mvc
ms.openlocfilehash: ca586874d79e9de5f293e548b1cfd08c694d3479
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104876168"
---
# <a name="tutorial-write-your-first-analyzer-and-code-fix"></a>Öğretici: ilk çözümleyicinizi ve kod düzeltmesini yazma

.NET Compiler Platform SDK 'Sı, C# veya Visual Basic kodunu hedefleyen özel Tanılamalar (çözümleyiciler), kod düzeltmeleri, kod yeniden düzenleme ve tanılama Gizleyiciler oluşturmak için ihtiyacınız olan araçları sağlar. **Çözümleyici** , kuralınızın ihlallerini algılayan kod içerir. **Kod düzeltmenizi** ihlalin giderdiği kodu içerir. Uyguladığınız kurallar, kod yapısından, adlandırma kurallarına ve daha fazlasına yönelik kodlama stiline kadar herhangi bir şey olabilir. .NET Compiler Platform, geliştiricilerin kod yazmakta olduğu ve kodu düzeltmek için tüm Visual Studio Kullanıcı arabirimi özelliklerinin yanı sıra kodu çözmede, Visual Studio Hata Listesi, "ampul" önerilerini oluşturarak ve önerilen düzeltmelerin zengin önizlemesini göstererek, analiz çalıştırma çerçevesini sağlar.

Bu öğreticide, bir **çözümleyici** oluşturmayı ve Roslyn API 'lerini kullanarak bir **kod düzeltmesini** inceleyebilirsiniz. Çözümleyici, kaynak kodu analizini gerçekleştirmek ve kullanıcıya bir sorun bildirmek için bir yoldur. İsteğe bağlı olarak, kullanıcının kaynak kodunda yapılan bir değişikliği göstermek için bir kod onarımı çözümleyici ile ilişkilendirilebilir. Bu öğreticide, değiştirici kullanılarak bildirilebilecek ancak olmayan yerel değişken bildirimlerini bulan bir çözümleyici oluşturulur `const` . Eşlik eden kod düzeltilmesi, değiştiriciyi eklemek için bu bildirimleri değiştirir `const` .

## <a name="prerequisites"></a>Önkoşullar

- [Visual Studio 2019](https://www.visualstudio.com/downloads) sürüm 16,8 veya üzeri

**.Net Compiler Platform SDK 'sını** Visual Studio yükleyicisi aracılığıyla yüklemeniz gerekir:

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

Çözümleyicinizi oluşturmak ve doğrulamak için birkaç adım vardır:

1. Çözümü oluşturun.
1. Çözümleyici adını ve açıklamasını kaydedin.
1. Rapor çözümleyici uyarıları ve önerileri.
1. Önerileri kabul etmek için kod düzeltmesini uygulayın.
1. Birim testler aracılığıyla Analizi geliştirme.

## <a name="create-the-solution"></a>Çözümü oluşturma

- Visual Studio 'da yeni proje iletişim kutusunu göstermek için **dosya > yeni > proje..** . öğesini seçin.
- **Visual C# > genişletilebilirlik** altında, **kod düzeltmesine sahip çözümleyici 'yi (.NET Standard)** seçin.
- Projenizi "**Makeconst**" olarak adlandırın ve Tamam ' a tıklayın.

## <a name="explore-the-analyzer-template"></a>Çözümleyici şablonunu keşfet

Kod düzelme şablonuyla çözümleyici, beş proje oluşturur:

- Çözümleyicisi içeren **Makeconst**.
- Kod düzeltmesini içeren **Makeconst. Codedüzeltmeleriyle**.
- Çözümleyici ve kod düzeltilmesi için NuGet paketini üretmek için kullanılan **Makeconst. Package**.
- Bir birim testi projesi olan **Makeconst. test**.
- Yeni çözümleyicinizi yükleyen ikinci bir Visual Studio örneğini başlatan varsayılan başlangıç projesi olan **Makeconst. vsix**. VSıX projesini başlatmak için <kbd>F5</kbd> tuşuna basın.

> [!TIP]
> Çözümleyicinizi çalıştırdığınızda, Visual Studio 'nun ikinci bir kopyasını başlatabilirsiniz. Bu ikinci kopya ayarları depolamak için farklı bir kayıt defteri kovanı kullanır. Bu, Visual Studio 'nun iki kopyasında görsel ayarları ayırt etmenize olanak sağlar. Visual Studio 'nun deneysel çalıştırması için farklı bir tema seçebilirsiniz. Ayrıca, Visual Studio 'nun deneysel çalıştırmasını kullanarak ayarlarınızı dolaşıyor veya Visual Studio hesabınızda oturum açmayın. Bu, ayarları farklı tutar.

Az önce başlattığınız ikinci Visual Studio örneğinde yeni bir C# konsol uygulaması projesi oluşturun (herhangi bir hedef çerçeve, kaynak düzeyinde çalışır.) Simgenin üzerine dalgalı alt çizgiyle gelin ve bir çözümleyici tarafından sunulan uyarı metni görüntülenir.

Şablon, aşağıdaki şekilde gösterildiği gibi tür adında küçük harfler içeren her tür bildiriminde uyarı raporlayan bir çözümleyici oluşturur:

![Çözümleyici raporlama uyarısı](media/how-to-write-csharp-analyzer-code-fix/report-warning.png)

Şablon Ayrıca, küçük harf karakter içeren herhangi bir tür adını tüm büyük harflere değiştiren bir kod düzeltmesini de sağlar. Önerilen değişiklikleri görmek için uyarıyla birlikte görüntülenecek ampule tıklayabilirsiniz. Önerilen değişiklikler kabul edildiğinde, tür adı ve çözümdeki bu türe yapılan tüm başvurular güncelleştirilir. İlk çözümleyici 'yi eylemde gördüğünüze göre, ikinci Visual Studio örneğini kapatın ve çözümleyici projenize geri dönün.

Visual Studio 'nun ikinci bir kopyasını başlatmanız ve çözümleyicinizdeki her değişikliği test etmek için yeni kod oluşturmanız gerekmez. Şablon sizin için bir birim testi projesi de oluşturur. Bu proje iki test içerir. `TestMethod1` Bir tanılamayı tetiklemeden kodu çözümleyen testin tipik biçimini gösterir. `TestMethod2` Bir tanılamayı tetikleyen testin biçimini gösterir ve ardından önerilen bir kod düzeltmesini uygular. Çözümleyicinizi ve kod düzeltmesini oluştururken, çalışmanızı doğrulamak üzere farklı kod yapıları için testler yazacaksınız. Çözümleyiciler için birim testleri, Visual Studio ile etkileşimli olarak test edilmesine kıyasla çok daha hızlıdır.

> [!TIP]
> Çözümleyici birim testleri, hangi kod yapılarının çözümleyicinizi tetikleyemediğini bildiğiniz ve bu harika bir araçtır. Visual Studio 'nun başka bir kopyasına çözümleyicinizi yüklemek, henüz düşünmemiş olan yapıları keşfetmeye ve bulmaya yönelik harika bir araçtır.

Bu öğreticide, kullanıcıya, yerel sabitlere dönüştürülebilen herhangi bir yerel değişken bildirimini raporlayan bir çözümleyici yazarsınız. Örneğin, aşağıdaki kodu göz önünde bulundurun:

```csharp
int x = 0;
Console.WriteLine(x);
```

Yukarıdaki kodda `x` sabit bir değer atanır ve hiçbir şekilde değiştirilmez. Değiştirici kullanılarak bildirilebilecek `const` :

```csharp
const int x = 0;
Console.WriteLine(x);
```

Bir değişkenin sabit bir şekilde yapılıp yapılmayacağını belirleme, değişken için sözdizimi analizi, başlatıcı ifadesinin sabit Analizi ve değişkenin hiçbir şekilde yazılmaması için veri akışı analizi gerektirir. .NET Compiler Platform, bu çözümlemenin daha kolay hale getirebilmesini sağlayan API 'Ler sağlar.

## <a name="create-analyzer-registrations"></a>Çözümleyici kayıtları oluşturma

Şablon, `DiagnosticAnalyzer` *MakeConstAnalyzer. cs* dosyasında başlangıç sınıfını oluşturur. Bu ilk çözümleyici, her çözümleyici 'nin iki önemli özelliğini gösterir.

- Her Tanılama Çözümleyicisi `[DiagnosticAnalyzer]` , üzerinde çalıştığı dili açıklayan bir öznitelik sağlamalıdır.
- Her Tanılama Çözümleyicisi sınıfından (doğrudan veya dolaylı olarak) türemelidir <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer> .

Şablon, herhangi bir çözümleyici 'nin parçası olan temel özellikleri de gösterir:

1. Kaydetme eylemleri. Eylemler, çözümleyicinizi ihlalleri için kodu incelemek üzere tetiklemesi gereken kod değişikliklerini temsil eder. Visual Studio, kayıtlı bir eylemle eşleşen kod düzenlemeleri algıladığında, çözümleyici 'nin kayıtlı yöntemini çağırır.
1. Tanılama oluşturun. Çözümleyicisi bir ihlal algıladığında, bu, ihlalin kullanıcısına bildirimde bulunan Visual Studio 'Nun kullandığı bir tanılama nesnesi oluşturur.

Eylemini geçersiz kılmanızda kaydedebilirsiniz <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer.Initialize(Microsoft.CodeAnalysis.Diagnostics.AnalysisContext)?displayProperty=nameWithType> . Bu öğreticide, yerel bildirimleri arayan **sözdizimi düğümlerini** ziyaret edeceğiz ve hangilerinin sabit değerlere sahip olduğunu görürsünüz. Bir bildirim sabitlenebilir, çözümleyici bir tanılama oluşturup rapor eder.

İlk adım, kayıt sabitlerini ve yöntemini güncelleştirmek ve `Initialize` Bu sabitler "const yap" çözümleyicisini göstermek için kullanılır. Dize sabitlerinin çoğu dize kaynak dosyasında tanımlanmıştır. Daha kolay yerelleştirme için bu uygulamayı izlemeniz gerekir. **Makeconst** çözümleyici projesi için *Resources. resx* dosyasını açın. Bu, kaynak düzenleyicisini görüntüler. Dize kaynaklarını aşağıdaki gibi güncelleştirin:

- `AnalyzerDescription`"" Olarak değiştirin :::no-loc text="Variables that are not modified should be made constants."::: .
- `AnalyzerMessageFormat`"" Olarak değiştirin :::no-loc text="Variable '{0}' can be made constant"::: .
- `AnalyzerTitle`"Olarak değiştirin :::no-loc text="Variable can be made constant"::: .

İşiniz bittiğinde, kaynak Düzenleyicisi aşağıdaki şekilde görünür:

![Dize kaynaklarını Güncelleştir](media/how-to-write-csharp-analyzer-code-fix/update-string-resources.png)

Geri kalan değişiklikler çözümleyici dosyasıdır. Visual Studio 'da *MakeConstAnalyzer. cs* ' i açın. Semboller üzerinde çalışan bir eylemden, söz dizimi üzerinde davranan bir eylemi değiştirin. `MakeConstAnalyzerAnalyzer.Initialize`Yönteminde, simgeleri üzerinde eylemi kaydeden satırı bulun:

```csharp
context.RegisterSymbolAction(AnalyzeSymbol, SymbolKind.NamedType);
```

Aşağıdaki satırla değiştirin:

[!code-csharp[Register the node action](snippets/how-to-write-csharp-analyzer-code-fix/MakeConst/MakeConst/MakeConstAnalyzer.cs#RegisterNodeAction "Register a node action")]

Bu değişiklikten sonra `AnalyzeSymbol` yöntemini silebilirsiniz. Bu çözümleyici <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.LocalDeclarationStatement?displayProperty=nameWithType> , deyimleri inceler <xref:Microsoft.CodeAnalysis.SymbolKind.NamedType?displayProperty=nameWithType> . `AnalyzeNode`Altında Red dalgalı çizgiler olduğuna dikkat edin. Az önce eklediğiniz kod `AnalyzeNode` bildirilmemiş bir yönteme başvurur. Aşağıdaki kodu kullanarak bu yöntemi bildirin:

```csharp
private void AnalyzeNode(SyntaxNodeAnalysisContext context)
{
}
```

`Category` :::no-loc text="Usage"::: Aşağıdaki kodda gösterildiği gibi, *MakeConstAnalyzer. cs* içinde "" olarak değiştirin:

[!code-csharp[Category constant](snippets/how-to-write-csharp-analyzer-code-fix/MakeConst/MakeConst/MakeConstAnalyzer.cs#Category  "Change category to Usage")]

## <a name="find-local-declarations-that-could-be-const"></a>Const olabilecek yerel bildirimleri bul

Yöntemin ilk sürümünü yazmak zaman `AnalyzeNode` . Bu, `const` Aşağıdaki kod gibi olabilecek, ancak olmayan tek bir yerel bildirime bakmalıdır:

```csharp
int x = 0;
Console.WriteLine(x);
```

İlk adım, yerel bildirimleri bulledir. Aşağıdaki kodu `AnalyzeNode` *MakeConstAnalyzer. cs* içine ekleyin:

[!code-csharp[localDeclaration variable](snippets/how-to-write-csharp-analyzer-code-fix/MakeConst/MakeConst/MakeConstAnalyzer.cs#LocalDeclaration  "Add localDeclaration variable")]

Bu atama, çözümleyici yerel bildirimlerinizde değişiklikler ve yalnızca yerel bildirimler için kaydedildiği için her zaman başarılı olur. Başka hiçbir düğüm türü, yönteminiz için bir çağrı tetiklemiyor `AnalyzeNode` . Sonra, herhangi bir değiştiricinin bildirimini kontrol edin `const` . Bunları bulursanız anında geri dönün. Aşağıdaki kod, `const` Yerel bildirimde herhangi bir değiştirici arar:

[!code-csharp[bail-out on const keyword](snippets/how-to-write-csharp-analyzer-code-fix/MakeConst/MakeConst/MakeConstAnalyzer.cs#BailOutOnConst  "bail-out on const keyword")]

Son olarak, değişkenin olup olmadığını kontrol etmeniz gerekir `const` . Bu, başlatıldıktan sonra hiçbir şekilde atanmadığından emin olmak anlamına gelir.

Kullanarak bazı semantik analizler gerçekleştirirsiniz <xref:Microsoft.CodeAnalysis.Diagnostics.SyntaxNodeAnalysisContext> . `context`Yerel değişken bildiriminin yapılıp yapılmayacağını anlamak için bağımsız değişkenini kullanırsınız `const` . <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType>Tek bir kaynak dosyasındaki tüm anlam bilgilerini temsil eder. [Anlam modellerini](../work-with-semantics.md)içeren makalede daha fazla bilgi edinebilirsiniz. <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType>' Yi, yerel bildirim deyimindeki veri akışı analizini gerçekleştirmek için kullanacaksınız. Ardından, bu veri akışı analizinin sonuçlarını kullanarak yerel değişkenin başka bir yerde yeni bir değerle yazılmadığından emin olun. <xref:Microsoft.CodeAnalysis.ModelExtensions.GetDeclaredSymbol%2A>Değişkenini almak için genişletme yöntemini çağırın <xref:Microsoft.CodeAnalysis.ILocalSymbol> ve <xref:Microsoft.CodeAnalysis.DataFlowAnalysis.WrittenOutside%2A?displayProperty=nameWithType> veri akışı analizinin koleksiyonuna dahil olmadığını kontrol edin. Yönteminin sonuna aşağıdaki kodu ekleyin `AnalyzeNode` :

```csharp
// Perform data flow analysis on the local declaration.
DataFlowAnalysis dataFlowAnalysis = context.SemanticModel.AnalyzeDataFlow(localDeclaration);

// Retrieve the local symbol for each variable in the local declaration
// and ensure that it is not written outside of the data flow analysis region.
VariableDeclaratorSyntax variable = localDeclaration.Declaration.Variables.Single();
ISymbol variableSymbol = context.SemanticModel.GetDeclaredSymbol(variable, context.CancellationToken);
if (dataFlowAnalysis.WrittenOutside.Contains(variableSymbol))
{
    return;
}
```

Yeni eklenen kod, değişkenin değiştirilmediğinden emin olur ve bu nedenle yapılabilir `const` . Tanılamayı yükseltme zamanı. Aşağıdaki kodu içine son satır olarak ekleyin `AnalyzeNode` :

[!code-csharp[Call ReportDiagnostic](snippets/how-to-write-csharp-analyzer-code-fix/MakeConst/MakeConst/MakeConstAnalyzer.cs#ReportDiagnostic  "Call ReportDiagnostic")]

<kbd>F5</kbd> 'e basarak çözümleyicinizi çalıştırmak için ilerleme durumunu kontrol edebilirsiniz. Daha önce oluşturduğunuz konsol uygulamasını yükleyebilir ve sonra şu test kodunu ekleyebilirsiniz:

```csharp
int x = 0;
Console.WriteLine(x);
```

Ampul görünmelidir ve çözümleyici 'niz bir tanılama raporlemelidir. Ancak ampul, şablon tarafından oluşturulan kod düzeltmesini hala kullanır ve bunun büyük bir durum oluşturabileceklerini söyler. Sonraki bölümde, kod düzeltmesinin nasıl yazılacağı açıklanmaktadır.

## <a name="write-the-code-fix"></a>Kod düzeltmesini yazın

Bir çözümleyici, bir veya daha fazla kod düzeltmesi sağlayabilir. Kod onarımı, bildirilen sorunu ele alan bir düzenleme tanımlar. Oluşturduğunuz çözümleyici için, const anahtar sözcüğünü ekleyen bir kod düzeltmesini sağlayabilirsiniz:

```diff
- int x = 0;
+ const int x = 0;
Console.WriteLine(x);
```

Kullanıcı onu düzenleyicide ampul kullanıcı arabiriminden seçer ve Visual Studio kodu değiştirir.

*Codefixresources. resx* dosyasını açın ve `CodeFixTitle` "" olarak değiştirin :::no-loc text="Make constant"::: .

Şablon tarafından eklenen *MakeConstCodeFixProvider. cs* dosyasını açın. Bu kod onarımı, tanılama çözümleyici 'niz tarafından üretilen tanılama KIMLIĞI 'ne zaten kablolu, ancak doğru kod dönüşümünü uygulamıyor.

Sonra, yöntemini silin `MakeUppercaseAsync` . Artık geçerli değildir.

Tüm kod onarma sağlayıcıları öğesinden türetilir <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider> . Bunlar, <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider.RegisterCodeFixesAsync(Microsoft.CodeAnalysis.CodeFixes.CodeFixContext)?displayProperty=nameWithType> kullanılabilir kod düzeltmelerini raporlamak için tüm geçersiz kılınır. ' De `RegisterCodeFixesAsync` , <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> tanı ile eşleştirmek için Aradığınız üst düğüm türünü bir olarak değiştirin:

[!code-csharp[Find local declaration node](snippets/how-to-write-csharp-analyzer-code-fix/MakeConst/MakeConst.CodeFixes/MakeConstCodeFixProvider.cs#FindDeclarationNode  "Find the local declaration node that raised the diagnostic")]

Sonra, bir kod düzeltmesini kaydetmek için son satırı değiştirin. Bu değişiklik, değiştiricinin mevcut bir bildirime eklenmesinin sonucu olan yeni bir belge oluşturur `const` :

[!code-csharp[Register the new code fix](snippets/how-to-write-csharp-analyzer-code-fix/MakeConst/MakeConst.CodeFixes/MakeConstCodeFixProvider.cs#RegisterCodeFix  "Register the new code fix")]

Simgenin üzerine yeni eklediğiniz kodda kırmızı dalgalı çizgiler fark edeceksiniz `MakeConstAsync` . `MakeConstAsync`Aşağıdaki kodu beğenmek için bir bildirim ekleyin:

```csharp
private static async Task<Document> MakeConstAsync(Document document,
    LocalDeclarationStatementSyntax localDeclaration,
    CancellationToken cancellationToken)
{
}
```

Yeni `MakeConstAsync` yönteminiz, <xref:Microsoft.CodeAnalysis.Document> kullanıcının kaynak dosyasını temsil eden yeni bir bildirim içeren yeni bir öğesine dönüştürür <xref:Microsoft.CodeAnalysis.Document> `const` .

`const`Bildirim ifadesinin önüne eklemek için yeni bir anahtar sözcük belirteci oluşturursunuz. Önce bildirim bildiriminin ilk belirtecinden önde gelen her türlü boşluğu kaldırmak ve belirtece eklemek konusunda dikkatli olun `const` . `MakeConstAsync` yöntemine aşağıdaki kodu ekleyin:

[!code-csharp[Create a new const keyword token](snippets/how-to-write-csharp-analyzer-code-fix/MakeConst/MakeConst.CodeFixes/MakeConstCodeFixProvider.cs#CreateConstToken  "Create the new const keyword token")]

Ardından, `const` aşağıdaki kodu kullanarak belirteci bildirime ekleyin:

```csharp
// Insert the const token into the modifiers list, creating a new modifiers list.
SyntaxTokenList newModifiers = trimmedLocal.Modifiers.Insert(0, constToken);
// Produce the new local declaration.
LocalDeclarationStatementSyntax newLocal = trimmedLocal
    .WithModifiers(newModifiers)
    .WithDeclaration(localDeclaration.Declaration);
```

Ardından, yeni bildirimi C# biçimlendirme kurallarıyla eşleşecek şekilde biçimlendirin. Değişikliklerinizi varolan kodla eşleşecek şekilde biçimlendirmek daha iyi bir deneyim oluşturur. Mevcut koddan hemen sonra aşağıdaki ifadeyi ekleyin:

[!code-csharp[Format the new declaration](snippets/how-to-write-csharp-analyzer-code-fix/MakeConst/MakeConst.CodeFixes/MakeConstCodeFixProvider.cs#FormatLocal  "Format the new declaration")]

Bu kod için yeni bir ad alanı gereklidir. Aşağıdaki `using` yönergeyi dosyanın en üstüne ekleyin:

```csharp
using Microsoft.CodeAnalysis.Formatting;
```

Son adım, düzenlemenizi yapmak için kullanılır. Bu işlemin üç adımı vardır:

1. Mevcut belgeye yönelik bir tanıtıcı alın.
1. Mevcut bildirimi yeni bildirimle değiştirerek yeni bir belge oluşturun.
1. Yeni belgeyi döndür.

Yönteminin sonuna aşağıdaki kodu ekleyin `MakeConstAsync` :

[!code-csharp[replace the declaration](snippets/how-to-write-csharp-analyzer-code-fix/MakeConst/MakeConst.CodeFixes/MakeConstCodeFixProvider.cs#ReplaceDocument  "Generate a new document by replacing the declaration")]

Kod düzeltmeizin denemeye hazırlanıyor.  Visual Studio 'nun ikinci bir örneğinde çözümleyici projesini çalıştırmak için <kbd>F5</kbd> tuşuna basın. İkinci Visual Studio örneğinde, yeni bir C# konsol uygulaması projesi oluşturun ve Main yöntemine sabit değerlerle başlatılan birkaç yerel değişken bildirimi ekleyin. Bunların uyarı olarak raporlandıklarından aşağıda gösterildiği gibi göreceksiniz.

![Const uyarıları yapabilir](media/how-to-write-csharp-analyzer-code-fix/make-const-warning.png)

Çok sayıda ilerleme yaptınız. Bildirimlerin altında dalgalı çizgiler vardır `const` . Ancak yine de devam eden bir iş var. Bu `const` `i` , sonrasında `j` ve son olarak bulunan bildirimlere eklerseniz bu işe yarar `k` . Ancak, `const` değiştiricisini ile başlayarak farklı bir sırada eklerseniz `k` , çözümleyici 'niz hata oluşturuyor: `k` `const` `i` ve ikisi birden olmadığı için bildirilemez `j` `const` . Değişkenlerin bildirilebilecek ve başlatılabileceği farklı yolları işlediğinizden emin olmak için daha fazla analiz yapmanız gerekir.

## <a name="build-unit-tests"></a>Derleme birimi testleri

Çözümleyici ve kod düzeltmesizin const hale getirilebilir tek bir bildirimin basit bir durumunda çalışır. Bu uygulamanın hata yaptığı çok sayıda olası bildirim deyimi vardır. Şablon tarafından yazılan birim testi kitaplığıyla çalışarak bu durumları ele alacağız. Visual Studio 'nun ikinci bir kopyasını art arda açmadan çok daha hızlıdır.

Birim testi projesinde *MakeConstUnitTests. cs* dosyasını açın. Şablon, bir çözümleyici ve kod düzelme birimi testi için iki ortak deseni izleyen iki test oluşturmuştur. `TestMethod1` çözümleyicinin ne zaman bir tanılama bildirmemesini sağlayan bir testin modelini gösterir. `TestMethod2` Bir tanılamayı raporlamak ve kod düzeltmesini çalıştırmak için bir model gösterir.

Şablon, birim testi için [Microsoft. CodeAnalysis. Testing](https://github.com/dotnet/roslyn-sdk/blob/main/src/Microsoft.CodeAnalysis.Testing/README.md) paketlerini kullanır.

> [!TIP]
> Sınama kitaplığı, aşağıdakiler de dahil olmak üzere özel bir biçimlendirme söz dizimini destekler:
>
> - `[|text|]`: için bir tanılayıcı rapor olduğunu gösterir `text` . Bu form, varsayılan olarak yalnızca tarafından sağlanmış olan Çözümleyicileri test etmek için kullanılabilir `DiagnosticDescriptor` `DiagnosticAnalyzer.SupportedDiagnostics` .
> - `{|ExpectedDiagnosticId:text|}`: ile bir Tanılamanın rapor olduğunu gösterir <xref:Microsoft.CodeAnalysis.Diagnostic.Id> `ExpectedDiagnosticId` `text` .

Aşağıdaki test yöntemini `MakeConstUnitTest` sınıfına ekleyin:

[!code-csharp[test method for fix test](snippets/how-to-write-csharp-analyzer-code-fix/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#FirstFixTest "test method for fix test")]

Geçirdiklerinden emin olmak için bu iki testi çalıştırın. Visual Studio 'da **, test**   >  **Windows**  >  **Test Gezgini**' ni seçerek test Gezginini açın. Ardından **Tümünü Çalıştır**' ı seçin.

## <a name="create-tests-for-valid-declarations"></a>Geçerli bildirimler için testler oluşturma

Genel bir kural olarak, çözümleyicilerin olabildiğince çabuk çıkması gerekir ve en az iş yapılır. Visual Studio, Kullanıcı kodu düzenlediği için kayıtlı çözümleyiciler çağırır. Yanıt verme bir anahtar gereksinimidir. Tanılamasını yükseltmemelidir kod için birkaç test çalışması vardır. Çözümleyicisi zaten bu testlerin birini, bir değişkenin başlatıldıktan sonra atandığı durumu işler. Bu durumu göstermek için aşağıdaki test yöntemini ekleyin:

[!code-csharp[variable assigned](snippets/how-to-write-csharp-analyzer-code-fix/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#VariableAssigned "a variable that is assigned after being initialized won't raise the diagnostic")]

Bu test da geçer. Daha sonra, henüz işlenmeyen koşullar için test yöntemleri ekleyin:

- Zaten const olduklarından, zaten sabit olan bildirimler `const` :

   [!code-csharp[already const declaration](snippets/how-to-write-csharp-analyzer-code-fix/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#AlreadyConst "a declaration that is already const should not raise the diagnostic")]

- Başlatıcısı olmayan bildirimler, kullanılacak bir değer yoktur:

   [!code-csharp[declarations that have no initializer](snippets/how-to-write-csharp-analyzer-code-fix/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#NoInitializer "a declaration that has no initializer should not raise the diagnostic")]

- Başlatıcıya bir sabit olmadığı ve derleme zamanı sabitleri olmadıkları için bildirim:

   [!code-csharp[declarations where the initializer isn't const](snippets/how-to-write-csharp-analyzer-code-fix/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#InitializerNotConstant "a declaration where the initializer is not a compile-time constant should not raise the diagnostic")]

C# birden çok bildirime tek bir bildirimde Izin verdiğinden daha karmaşık olabilir. Aşağıdaki test çalışması dize sabitini göz önünde bulundurun:

[!code-csharp[multiple initializers](snippets/how-to-write-csharp-analyzer-code-fix/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#MultipleInitializers "A declaration can be made constant only if all variables in that statement can be made constant")]

Değişken `i` sabit hale getirilebilir, ancak değişken `j` olamaz. Bu nedenle, bu ifade bir const bildirimi yapılamaz.

Testlerinizi yeniden çalıştırın ve bu yeni test çalışmalarını başarısız görürsünüz.

## <a name="update-your-analyzer-to-ignore-correct-declarations"></a>Çözümleyicinizi doğru bildirimleri yoksayacak şekilde güncelleştirme

`AnalyzeNode`Bu koşullara uyan kodu filtrelemek için çözümleyicinizdeki bazı geliştirmeler yapmanız gerekir. Bunlar ilgili tüm koşullardır, böylece benzer değişiklikler bu koşulların tümünü düzeltir. Aşağıdaki değişiklikleri yapın `AnalyzeNode` :

- Anlam analiziniz tek bir değişken bildirimi inceledi. Bu kodun, `foreach` aynı bildirimde belirtilen tüm değişkenleri inceleyen bir döngüde olması gerekir.
- Her beyan edilen değişkenin bir başlatıcıya sahip olması gerekir.
- Her bir derlenen değişkenin başlatıcısı bir derleme zamanı sabiti olmalıdır.

`AnalyzeNode`Yöntemdeki özgün anlam analizini değiştirin:

```csharp
// Perform data flow analysis on the local declaration.
DataFlowAnalysis dataFlowAnalysis = context.SemanticModel.AnalyzeDataFlow(localDeclaration);

// Retrieve the local symbol for each variable in the local declaration
// and ensure that it is not written outside of the data flow analysis region.
VariableDeclaratorSyntax variable = localDeclaration.Declaration.Variables.Single();
ISymbol variableSymbol = context.SemanticModel.GetDeclaredSymbol(variable, context.CancellationToken);
if (dataFlowAnalysis.WrittenOutside.Contains(variableSymbol))
{
    return;
}
```

Aşağıdaki kod parçacığı ile:

```csharp
// Ensure that all variables in the local declaration have initializers that
// are assigned with constant values.
foreach (VariableDeclaratorSyntax variable in localDeclaration.Declaration.Variables)
{
    EqualsValueClauseSyntax initializer = variable.Initializer;
    if (initializer == null)
    {
        return;
    }

    Optional<object> constantValue = context.SemanticModel.GetConstantValue(initializer.Value, context.CancellationToken);
    if (!constantValue.HasValue)
    {
        return;
    }
}

// Perform data flow analysis on the local declaration.
DataFlowAnalysis dataFlowAnalysis = context.SemanticModel.AnalyzeDataFlow(localDeclaration);

foreach (VariableDeclaratorSyntax variable in localDeclaration.Declaration.Variables)
{
    // Retrieve the local symbol for each variable in the local declaration
    // and ensure that it is not written outside of the data flow analysis region.
    ISymbol variableSymbol = context.SemanticModel.GetDeclaredSymbol(variable, context.CancellationToken);
    if (dataFlowAnalysis.WrittenOutside.Contains(variableSymbol))
    {
        return;
    }
}
```

İlk `foreach` döngü, söz dizimi analizini kullanarak her bir değişken bildirimini inceler. İlk denetim, değişkenin bir başlatıcıya sahip olduğunu garanti eder. İkinci denetim, başlatıcının bir sabit olduğunu garanti eder. İkinci döngünün özgün anlam analizi vardır. Performans üzerinde daha fazla etkisi olduğundan anlam denetimleri ayrı bir döngüde bulunur. Testlerinizi yeniden çalıştırın ve hepsini bir kez görmeniz gerekir.

## <a name="add-the-final-polish"></a>Son Lehçe 'ı ekleyin

Neredeyse bitti. Çözümleyicinizi işlemek için birkaç koşul daha vardır. Visual Studio, Kullanıcı kod yazarken Çözümleyicileri çağırır. Bu durum genellikle çözümleyicinizi derlenmeyen kod için çağrılacaktır. Tanılama Çözümleyicisi yöntemi, `AnalyzeNode` sabit değerin değişken türüne dönüştürülebilir olup olmadığını kontrol etmez. Bu nedenle, geçerli uygulama int ı = "abc" ' gibi yanlış bir bildirimi yerel bir sabit 'e dönüştürmelidir. Bu durum için bir test yöntemi ekleyin:

[!code-csharp[Mismatched types don't raise diagnostics](snippets/how-to-write-csharp-analyzer-code-fix/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#DeclarationIsInvalid "When the variable type and the constant type don't match, there's no diagnostic")]

Ayrıca, başvuru türleri düzgün işlenmez. Bir başvuru türü için izin verilen tek sabit değeri, `null` Bu durum dışında, <xref:System.String?displayProperty=nameWithType> dize değişmezine izin verir. Diğer bir deyişle, geçerlidir `const string s = "abc"` ancak `const object s = "abc"` değildir. Bu kod parçacığı bu durumu doğrular:

[!code-csharp[Reference types don't raise diagnostics](snippets/how-to-write-csharp-analyzer-code-fix/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#DeclarationIsntString "When the variable type is a reference type other than string, there's no diagnostic")]

Tam olarak, bir dize için sabit bildirim oluşturabilmeniz için başka bir test eklemeniz gerekir. Aşağıdaki kod parçacığı, hem tanılamayı başlatan kodu hem de düzeltilme uygulandıktan sonra kodu tanımlar:

[!code-csharp[string reference types raise diagnostics](snippets/how-to-write-csharp-analyzer-code-fix/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#ConstantIsString "When the variable type is string, it can be constant")]

Son olarak, bir değişken `var` anahtar sözcükle bildirilirse, kod düzeltilmesi yanlış şeyi yapar ve `const var` C# dili tarafından desteklenmeyen bir bildirim oluşturur. Bu hatayı onarmak için, kod düzeltmesinin `var` anahtar sözcüğünün çıkarılan türün adıyla yerine gelmelidir:

[!code-csharp[var references need to use the inferred types](snippets/how-to-write-csharp-analyzer-code-fix/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#VarDeclarations "Declarations made using var must have the type replaced with the inferred type")]

Neyse ki, yukarıdaki hataların tümü, az önce öğrendiğiniz tekniklerin kullanılmasıyla çözülebilir.

İlk hatayı onarmak için öncelikle *Diagnosticanalyzer. cs* ' yi açın ve her bir yerel bildirimin başlatıcılarının her birinin, sabit değerlerle atanmasını sağlamak için her birinin kontrol edildiği foreach döngüsünü bulun. İlk foreach döngüsünden hemen _önce_ , `context.SemanticModel.GetTypeInfo()` Yerel bildirimin belirtilen türü hakkında ayrıntılı bilgi almak için çağırın:

[!code-csharp[Retrieve type information](snippets/how-to-write-csharp-analyzer-code-fix/MakeConst/MakeConst/MakeConstAnalyzer.cs#VariableConvertedType "Retrieve type information")]

Sonra, `foreach` döngünüz içinde, değişken türüne dönüştürülebilir olduğundan emin olmak için her başlatıcıyı kontrol edin. Başlatıcının bir sabit olduğundan emin olduktan sonra aşağıdaki denetimi ekleyin:

[!code-csharp[Ensure non-user-defined conversion](snippets/how-to-write-csharp-analyzer-code-fix/MakeConst/MakeConst/MakeConstAnalyzer.cs#BailOutOnUserDefinedConversion "Bail-out on user-defined conversion")]

Sonraki değişiklik, son bir üzerinde derleme oluşturur. İlk foreach döngüsünün kapanış küme ayracından önce, sabit bir dize veya null olduğunda yerel bildirimin türünü denetlemek için aşağıdaki kodu ekleyin.

[!code-csharp[Handle special cases](snippets/how-to-write-csharp-analyzer-code-fix/MakeConst/MakeConst/MakeConstAnalyzer.cs#HandleSpecialCases "Handle special cases")]

Anahtar sözcüğünü doğru tür adıyla değiştirmek için kod düzeltme sağlayıcınızda bir bit daha daha kod yazmalısınız `var` . *MakeConstCodeFixProvider. cs*' ye geri dönün. Ekleyeceğiniz kod aşağıdaki adımları yapar:

- Bildirimin bir bildirim olup olmadığını `var` ve şu şekilde olduğunu kontrol edin:
- Çıkarsanan tür için yeni bir tür oluşturun.
- Tür bildiriminin bir diğer ad olmadığından emin olun. Varsa, bildirim için geçerlidir `const var` .
- `var`Bunun, bu programda bir tür adı olmadığından emin olun. (Varsa, `const var` geçerlidir).
- Tam tür adını basitleştirme

Bu çok fazla kod gibi seslerden oluşur. Bu değildir. Bildiren ve Başlatan satırı `newLocal` aşağıdaki kodla değiştirin. Başlatma işleminden hemen sonra geçer `newModifiers` :

[!code-csharp[Replace Var designations](snippets/how-to-write-csharp-analyzer-code-fix/MakeConst/MakeConst.CodeFixes/MakeConstCodeFixProvider.cs#ReplaceVar "Replace a var designation with the explicit type")]

`using`Türünü kullanmak için bir yönerge eklemeniz gerekir <xref:Microsoft.CodeAnalysis.Simplification.Simplifier> :

```csharp
using Microsoft.CodeAnalysis.Simplification;
```

Testlerinizi çalıştırın ve hepsi başarılı olmalıdır. Tamamlanmış çözümleyicinizi çalıştırarak kendiniz kutlama yapın. <kbd></kbd> + Visual Studio 'nun ikinci bir örneğinde, Roslyn önizleme uzantısı yüklenmiş olarak çözümleyici projesini çalıştırmak için CTRL<kbd>F5</kbd> tuşuna basın.

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

Tebrikler! Bir sorunu tespit etmek ve düzeltmek için hızlı bir düzeltme sağlamak üzere anında çalıştırılan kod analizini gerçekleştiren ilk .NET Compiler Platform uzantınızı oluşturdunuz. Bu şekilde, .NET Compiler Platform SDK 'nın (Roslyn API 'Ler) parçası olan kod API 'lerinin birçoğunu öğrendiniz. Çalışmalarımızı örnek GitHub deponuzdaki [tamamlanmış örnekle](https://github.com/dotnet/samples/tree/main/csharp/roslyn-sdk/Tutorials/MakeConst) karşı denetleyebilirsiniz.

## <a name="other-resources"></a>Diğer kaynaklar

- [Sözdizimi analizini kullanmaya başlayın](../get-started/syntax-analysis.md)
- [Anlamsal analiz ile çalışmaya başlama](../get-started/semantic-analysis.md)
