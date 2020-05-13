---
title: .NET Compiler Platform SDK sözdizimi modelini kullanın
description: Bu genel bakışta, söz dizimi düğümlerini anlamak ve işlemek için kullandığınız türlerin anlaşılması sağlanır.
ms.date: 10/15/2017
ms.custom: mvc
ms.openlocfilehash: fdb13095c2b91e54d58988a51a51b05652e57ea6
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83208401"
---
# <a name="work-with-syntax"></a>Söz dizimi ile çalışma

*Sözdizimi ağacı* , derleyici API 'leri tarafından kullanıma sunulan temel bir veri yapısıdır. Bu ağaçlar, kaynak kodunun sözlü ve sözdizimsel yapısını temsil eder. Bunlar iki önemli amaca hizmet eder:

- IDE, Eklentiler, kod analizi araçları ve yeniden düzenlemeler gibi araçlara izin vermek için, bir kullanıcının projesindeki kaynak kodun sözdizimsel yapısını görmek ve işlemek için.
- Yeniden düzenlemeler ve IDE gibi araçları etkinleştirmek için-doğrudan metin düzenlemeleri kullanmak zorunda kalmadan, kaynak kodu doğal bir şekilde oluşturmak, değiştirmek ve yeniden düzenlemek için. Ağaçlar oluşturup düzenleyerek, araçlar kaynak kodu kolayca oluşturup yeniden düzenleyebilir.

## <a name="syntax-trees"></a>Sözdizimi ağaçları

Sözdizimi ağaçları, derleme, kod analizi, bağlama, yeniden düzenleme, IDE özellikleri ve kod oluşturma için kullanılan birincil yapıdır. Birinci olarak bilinen yapısal dil öğelerinden birinde tanımlanmadan ve sınıflandırılmadan kaynak kodun hiçbir bölümü anlaşılmamıştır.

Sözdizimi ağaçları üç anahtar özniteliğe sahiptir. İlk öznitelik, söz dizimi ağaçlarının tüm kaynak bilgilerini tam Aslına göre tutamadır. Tam doğruluk, sözdizimi ağacının kaynak metinde bulunan her bilgi parçasını, her dilbilgisi yapısını, her sözcük belirtecini ve diğer her şeyi (boşluk, açıklama ve Önişlemci yönergeleri dahil) içerdiği anlamına gelir. Örneğin, kaynakta bahsedilen her bir sabit değer tam olarak yazıldığı gibi gösterilir. Sözdizimi ağaçları Ayrıca, Atlanan veya eksik belirteçleri temsil ederek, program eksik veya hatalı biçimlendirilmiş olarak kaynak kodundaki hataları yakalar.

Sözdizimi ağaçlarının ikinci özniteliği, ayrıştırıldıkları metnin tam olarak oluşturabilmesine neden olur. Herhangi bir söz dizimi düğümünden, bu düğümde kök alt ağacın metin temsilini almak mümkündür. Bu özellik, söz dizimi ağaçlarının kaynak metni oluşturmak ve düzenlemek için bir yol olarak kullanılabileceği anlamına gelir. Sahip olduğunuz bir ağaç oluşturarak, benzer bir metin oluşturup, bir sözdizimi ağacını düzenleyerek, yeni bir ağacı varolan bir ağaçtaki değişikliklerden sonra, metni etkin bir şekilde düzenlemiş olursunuz.

Söz dizimi ağaçlarının üçüncü özniteliği, sabit ve iş parçacığı açısından güvenlidir. Bir ağaç alındıktan sonra, kodun geçerli durumunun anlık görüntüsü olur ve hiçbir şekilde değişiklik olmaz. Bu, birden çok kullanıcının kilitleme veya çoğaltma olmadan farklı iş parçacıklarında aynı söz dizimi ağacıyla etkileşime geçmesini sağlar. Ağaçlar sabittir ve hiçbir değişiklik doğrudan bir ağaca yapılamaz, ancak Fabrika yöntemleri ağacın ek anlık görüntülerini oluşturarak sözdizimi ağaçları oluşturma ve değiştirme konusunda yardımcı olur. Ağaçlar, temel düğümleri yeniden kullanma biçiminde etkilidir, bu nedenle yeni bir sürüm hızlı bir şekilde ve çok fazla bellekle yeniden oluşturulabilir.

Sözdizimi ağacı, Terminal olmayan yapısal öğelerin üst diğer öğelerinden oluşan bir ağaç veri yapısıdır. Her bir sözdizimi ağacı düğümlerin, belirteçlerin ve trivia oluşur.

## <a name="syntax-nodes"></a>Sözdizimi düğümleri

Sözdizimi düğümleri, söz dizimi ağaçlarının birincil öğelerinden biridir. Bu düğümler, bildirimler, deyimler, yan tümceler ve ifadeler gibi sözdizimsel yapıları temsil eder. Her bir sözdizimi düğümleri kategorisi, öğesinden türetilmiş ayrı bir sınıf tarafından temsil edilir <xref:Microsoft.CodeAnalysis.SyntaxNode?displayProperty=nameWithType> . Düğüm sınıfları kümesi genişletilebilir değil.

Tüm sözdizimi düğümleri, söz dizimi ağacındaki Terminal olmayan düğümlerdir, bu da her zaman alt öğe olarak diğer düğümleri ve belirteçleri oldukları anlamına gelir. Başka bir düğümün alt öğesi olarak, her düğümün özelliği aracılığıyla erişilebilen bir üst düğümü vardır <xref:Microsoft.CodeAnalysis.SyntaxNode.Parent?displayProperty=nameWithType> . Düğümler ve ağaçlar sabit olduğundan, düğümün üst öğesi hiçbir şekilde değişmez. Ağacın kökü null bir üst öğeye sahip.

Her düğüm bir <xref:Microsoft.CodeAnalysis.SyntaxNode.ChildNodes?displayProperty=nameWithType> yöntemine sahiptir ve bu, kaynak metindeki konumlarına göre alt düğümlerin bir listesini sıralı sırada döndürür. Bu liste belirteç içermiyor. Her düğüm,,, veya gibi alt öğeleri inceleme yöntemlerine sahiptir; Örneğin, <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantNodes%2A> <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantTokens%2A> <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantTrivia%2A> Bu düğüm tarafından kök alt ağaçta bulunan tüm düğümlerin, belirteçlerin veya üç yanındaki bir listeyi temsil eder.

Ayrıca, her bir sözdizimi düğüm alt sınıfı, kesin belirlenmiş özellikler aracılığıyla aynı alt öğeleri gösterir. Örneğin, bir <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax> düğüm sınıfı ikili işleçlere özgü üç ek özelliğe sahiptir: <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Left> , <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.OperatorToken> , ve <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Right> . , Ve türü <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Left> <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Right> ve türüdür <xref:Microsoft.CodeAnalysis.CSharp.Syntax.ExpressionSyntax> <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.OperatorToken> <xref:Microsoft.CodeAnalysis.SyntaxToken> .

Bazı sözdizimi düğümlerinde isteğe bağlı alt öğeler vardır. Örneğin, bir, <xref:Microsoft.CodeAnalysis.CSharp.Syntax.IfStatementSyntax> isteğe bağlıdır <xref:Microsoft.CodeAnalysis.CSharp.Syntax.ElseClauseSyntax> . Alt öğe yoksa, özelliği null döndürür.

## <a name="syntax-tokens"></a>Sözdizimi belirteçleri

Sözdizimi belirteçleri, kodun en küçük sözdizimsel parçalarını temsil eden dil dilbilgisinde bulunan terminallerdir. Bunlar hiçbir şekilde diğer düğümlerin veya belirteçlerin hiçbir üst öğesi değildir. Sözdizimi belirteçleri anahtar sözcüklerden, tanımlayıcılardan, değişmez değerlerden ve noktalama işaretlerinden oluşur.

Verimlilik açısından, <xref:Microsoft.CodeAnalysis.SyntaxToken> tür BIR clr değer türüdür. Bu nedenle, sözdizimi düğümlerinden farklı olarak, temsil edilen belirtecin türüne bağlı olarak anlamı olan özelliklerin karışımına sahip tüm belirteç türleri için tek bir yapı vardır.

Örneğin, bir tamsayı sabit değeri bir sayısal değeri temsil eder. Belirtecin yayıldığı ham kaynak metnine ek olarak, değişmez değer belirtecinin, <xref:Microsoft.CodeAnalysis.SyntaxToken.Value> kodu çözülen tam sayı değerini size bildiren bir özelliği vardır. Bu özellik, <xref:System.Object> birçok temel türden biri olabileceği için olarak yazılır.

<xref:Microsoft.CodeAnalysis.SyntaxToken.ValueText>Özelliği, özelliği ile aynı bilgileri söyler <xref:Microsoft.CodeAnalysis.SyntaxToken.Value> ; ancak bu özellik her zaman olarak yazılır <xref:System.String> . C# kaynak metnindeki bir tanımlayıcı Unicode kaçış karakterlerini içerebilir, ancak kaçış dizisinin sözdizimi tanımlayıcı adının bir parçası olarak kabul edilmez. Bu nedenle, belirteç tarafından yayılan ham metin kaçış sırasını içerse de, <xref:Microsoft.CodeAnalysis.SyntaxToken.ValueText> özelliği değildir. Bunun yerine, kaçış tarafından tanımlanan Unicode karakterleri içerir. Örneğin, kaynak metin olarak yazılmış bir tanımlayıcı içeriyorsa `\u03C0` , <xref:Microsoft.CodeAnalysis.SyntaxToken.ValueText> Bu belirtecin özelliği döndürülür `π` .

## <a name="syntax-trivia"></a>Sözdizimi bilgi

Sözdizimi bilgi kaynak metnin, beyaz boşluk, açıklama ve Önişlemci yönergeleri gibi kodu normal şekilde anlamak için büyük ölçüde önemli olan kısımlarını temsil eder. Sözdizimi belirteçleri gibi, bilgi değer türleridir. Tek <xref:Microsoft.CodeAnalysis.SyntaxTrivia?displayProperty=nameWithType> tür her türlü Tria 'nın açıklaması için kullanılır.

Bilgi normal dil sözdiziminin parçası olmadığından ve iki belirteç arasında bir yerde görünebildiğinden, bir düğümün alt öğesi olarak sözdizimi ağacına dahil edilmez. Henüz, yeniden düzenleme gibi bir özellik uygularken ve kaynak metinle tam uygunluğu sürdürmek için önemli olduklarından, söz dizimi ağacının bir parçası olarak mevcuttur.

Bir belirtecin veya koleksiyonların bir listesini inceleyerek, bilgi 'a erişebilirsiniz <xref:Microsoft.CodeAnalysis.SyntaxToken.LeadingTrivia?displayProperty=nameWithType> <xref:Microsoft.CodeAnalysis.SyntaxToken.TrailingTrivia?displayProperty=nameWithType> . Kaynak metni ayrıştırıldığında, bilgi dizileri belirteçlerle ilişkilendirilir. Genel olarak, bir belirteç bir sonraki belirtece kadar aynı satıra kadar herhangi bir tribiya benzer. Bu satırdan sonraki her türlü bir değer aşağıdaki belirteçle ilişkilendirilir. Kaynak dosyadaki ilk simge, tüm başlangıç anlarını alır ve dosyadaki en son üç sıra, sıfır genişliğine sahip olan dosya sonu belirtecine göre belirlenir.

Söz dizimi düğümleri ve belirteçlerden farklı olarak söz dizimi bilgi üst öğeleri yoktur. Henüz, ağacın bir parçası olduklarından ve her biri tek bir belirteçle ilişkilendirildiğinden, özelliği kullanılarak ilişkili olan belirtece erişebilirsiniz <xref:Microsoft.CodeAnalysis.SyntaxTrivia.Token?displayProperty=nameWithType> .

## <a name="spans"></a>Maları

Her düğüm, belirteç veya bilgi, kaynak metni içindeki konumunu ve içerdiği karakter sayısını bilir. Bir metin konumu, sıfır tabanlı bir dizin olan 32 bitlik bir tamsayı olarak temsil edilir `char` . Bir <xref:Microsoft.CodeAnalysis.Text.TextSpan> nesne, her ikisi de tamsayılar olarak gösterilen başlangıç konumu ve karakter sayısıdır. <xref:Microsoft.CodeAnalysis.Text.TextSpan>Sıfır uzunluğa sahipse, iki karakter arasındaki bir konuma başvurur.

Her düğümün iki <xref:Microsoft.CodeAnalysis.Text.TextSpan> özelliği vardır: <xref:Microsoft.CodeAnalysis.SyntaxNode.Span%2A> ve <xref:Microsoft.CodeAnalysis.SyntaxNode.FullSpan%2A> .

<xref:Microsoft.CodeAnalysis.SyntaxNode.Span%2A>Özelliği, düğümün alt ağacındaki ilk belirtecin başından son belirtecin sonuna kadar olan metindir. Bu yayılma, başında veya sonunda bir boşluk içermez.

<xref:Microsoft.CodeAnalysis.SyntaxNode.FullSpan%2A>Özelliği, düğümün normal yayılımını içeren metin yaydır ve önünde ya da sondaki üç nokta için bir değer.

Örneğin:

``` csharp
      if (x > 3)
      {
||        // this is bad
          |throw new Exception("Not right.");|  // better exception?||
      }
```

Bloğun içindeki deyimin düğümü, tek dikey çubuklar (|) ile belirtilen bir yayılım içeriyor. Karakterleri içerir `throw new Exception("Not right.");` . Tam yayılma, çift dikey çubuklar (| |) ile belirtilir. Yayılma ile aynı karakterleri ve baştaki ve sondaki trivia ile ilişkili karakterleri içerir.

## <a name="kinds"></a>Farklı

Her düğüm, belirteç veya bilgi <xref:Microsoft.CodeAnalysis.SyntaxNode.RawKind?displayProperty=nameWithType> <xref:System.Int32?displayProperty=nameWithType> , temsil edilen tam sözdizimi öğesini tanımlayan türünde bir özelliğine sahiptir. Bu değer dile özgü bir numaralandırmaya atanabilir. Her dil, C# veya Visual Basic, `SyntaxKind` <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind?displayProperty=nameWithType> <xref:Microsoft.CodeAnalysis.VisualBasic.SyntaxKind?displayProperty=nameWithType> tüm olası düğümleri, belirteçleri ve dilbilgisinde bilgi öğelerini listeleyen tek bir sabit listesi (ve sırasıyla) vardır. Bu dönüştürme, <xref:Microsoft.CodeAnalysis.CSharp.CSharpExtensions.Kind%2A?displayProperty=nameWithType> veya genişletme yöntemlerine erişerek otomatik olarak yapılabilir <xref:Microsoft.CodeAnalysis.VisualBasic.VisualBasicExtensions.Kind%2A?displayProperty=nameWithType> .

<xref:Microsoft.CodeAnalysis.SyntaxToken.RawKind>Özelliği, aynı node sınıfını paylaşan sözdizimi düğümü türlerinin kolay bir şekilde kesinleştirilmesine olanak sağlar. Belirteçler ve trivia için, bu özellik bir öğe türünü diğerinden ayırt etmenin tek yoludur.

Örneğin, tek bir <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax> sınıf <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Left> , <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.OperatorToken> , ve <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Right> alt öğeleri içerir. <xref:Microsoft.CodeAnalysis.CSharp.CSharpExtensions.Kind%2A>Özelliği <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.AddExpression> ,, <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.SubtractExpression> veya tür bir sözdizimi düğümü olup olmadığını ayırt eder <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.MultiplyExpression> .

## <a name="errors"></a>Hatalar

Kaynak metin sözdizimi hataları içerdiğinde bile, kaynağa gidiş olarak dönüşümlü bir tam sözdizimi ağacı gösterilir. Ayrıştırıcı dilin tanımlı söz dizimi ile uyumlu olmayan kodla karşılaştığında, sözdizimi ağacı oluşturmak için iki teknikten birini kullanır:

- Ayrıştırıcı belirli bir belirteç türünü bekliyor ancak bulamazsa, belirtecin beklenildiği konumdaki sözdizimi ağacına eksik bir belirteç eklenebilir. Eksik belirteç beklenen gerçek belirteci temsil eder, ancak boş bir yayılım ve <xref:Microsoft.CodeAnalysis.SyntaxNode.IsMissing?displayProperty=nameWithType> özelliği döndürür `true` .

- Ayrıştırıcı ayrıştırmaya devam edebilecekleri bir konum bulana kadar belirteçleri atlayabilir. Bu durumda, atlanan belirteçler, türü ile bir bilgi düğüm olarak eklenir <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.SkippedTokensTrivia> .
