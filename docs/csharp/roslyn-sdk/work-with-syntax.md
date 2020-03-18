---
title: .NET Derleyici Platformu SDK sözdizimi modelini kullanın
description: Bu genel bakış, sözdizimi düğümlerini anlamak ve işlemek için kullandığınız türlerin anlaşılmasını sağlar.
ms.date: 10/15/2017
ms.custom: mvc
ms.openlocfilehash: fc1b1f5ae5ec985425c8d6aec49ef7f830ea9162
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75740479"
---
# <a name="work-with-syntax"></a>Söz dizimi ile çalışma

**Sözdizimi ağacı** derleyici API'leri tarafından maruz kalan temel bir veri yapısıdır. Bu ağaçlar kaynak kodun sözlü ve sözdizimsel yapısını temsil ediyor. İki önemli amac için kullanılırlar:

1. IDE, eklentiler, kod çözümleme araçları ve refactorings gibi araçların bir kullanıcının projesinde kaynak kodun sözdizimi yapısını görmesine ve işlemesine izin vermek için.
2. Doğrudan metin düzenlemeleri kullanmadan kaynak kodu doğal bir şekilde oluşturmak, değiştirmek ve yeniden düzenlemek için yeniden düzenleme ler gibi araçları etkinleştirmek için. Ağaçlar oluşturup manipüle ederek, araçlar kaynak kodu kolayca oluşturabilir ve yeniden düzenleyebilir.

## <a name="syntax-trees"></a>Sözdizimi ağaçları

Sözdizimi ağaçları derleme, kod analizi, bağlama, yeniden düzenleme, IDE özellikleri ve kod oluşturma için kullanılan birincil yapıdır. Kaynak kodun hiçbir bölümü, ilk olarak tanımlanmadan ve birçok tanınmış yapısal dil öğesinden biri olarak sınıflandırılmadan anlaşılmaz.

Sözdizimi ağaçlarının üç temel özelliği vardır. İlk öznitelik sözdizimi ağaçları tam sadakat tüm kaynak bilgileri tutmak olduğunu. Bu, sözdizimi ağacının kaynak metinde bulunan her bilgi parçasını, her dilbilgisi yapısını, her sözlü belirteci ve beyaz boşluk, yorumlar ve önişlemci yönergeleri de dahil olmak üzere aradaki her şeyi içerdiği anlamına gelir. Örneğin, kaynakta belirtilen her bir edebi tam olarak yazılmış olarak temsil edilir. Sözdizimi ağaçları, program tamamlanmamış veya sözdizimi ağacında atlanan veya eksik belirteçleri temsil ederek eksik olduğunda kaynak kodundaki hataları da temsil eder.

Bu sözdizimi ağaçlarının ikinci özniteliğini sağlar. Ayrıştırıcıdan elde edilen bir sözdizimi ağacı, ayrıştırılmış olduğu metni üretebilir. Herhangi bir sözdizimi düğümünden, bu düğümde köklü alt ağacın metin gösterimini almak mümkündür. Bu, sözdizimi ağaçlarının kaynak metni oluşturma ve bunları yeniden oluşturmanın bir yolu olarak kullanabileceği anlamına gelir. Eşdeğer metni oluşturduğunuz bir ağaç oluşturarak ve sözdizimi ağacıdüzenleyerek, varolan bir ağaçta yapılan değişikliklerden yeni bir ağaç oluşturarak metni etkili bir şekilde düzenlemiş olursunuz.

Sözdizimi ağaçlarının üçüncü özniteliği, değişmez ve iş parçacığı güvenli olmasıdır.  Bu, bir ağaç alındıktan sonra, kodun geçerli durumunun anlık görüntüsü olduğu ve hiçbir zaman değişmeyiş anlamına gelir. Bu, birden çok kullanıcının kilitleme veya yineleme olmadan farklı iş parçacıklarında aynı anda aynı sözdizimi ağacıyla etkileşimkurmasına olanak tanır. Ağaçlar değişmez olduğundan ve doğrudan bir ağaca değişiklik yapılamadığından, fabrika yöntemleri ağacın ek anlık görüntülerini oluşturarak sözdizimi ağaçlarının oluşturulmasına ve değiştirilmesine yardımcı olur. Ağaçlar altta yatan düğümleri yeniden kullanma şeklinde etkilidir, böylece yeni bir sürüm hızlı ve çok az ekstra bellekle yeniden oluşturulabilir.

Sözdizimi ağacı, terminal olmayan yapısal öğelerin diğer öğelerin üst düzey eki olduğu bir ağaç veri yapısıdır. Her sözdizimi ağacı düğümlerden, belirteçlerden ve ıvır zıvırdan oluşur.

## <a name="syntax-nodes"></a>Sözdizimi düğümleri

Sözdizimi düğümleri sözdizimi ağaçlarının birincil öğelerinden biridir. Bu düğümler deyimler, deyimler, yan tümceler ve ifadeler gibi sözdizim yapıları temsil eder. Sözdizimi düğümlerinin her kategorisi, .'dan <xref:Microsoft.CodeAnalysis.SyntaxNode?displayProperty=nameWithType>türetilen ayrı bir sınıfla temsil edilir. Düğüm sınıfları kümesi genişletilebilir değildir.

Tüm sözdizimi düğümleri sözdizimi ağacındaki terminal olmayan düğümlerdir, bu da çocuk olarak her zaman başka düğümleri ve belirteçleri olduğu anlamına gelir. Başka bir düğümün alt öğesi olarak, her düğümün <xref:Microsoft.CodeAnalysis.SyntaxNode.Parent?displayProperty=nameWithType> özelliği nden erişilebilen bir üst düğüm vardır. Düğümler ve ağaçlar değişmez olduğundan, düğümün üst öğesi asla değişmez. Ağacın kökünde boş bir ebeveyn vardır.

Her düğüm, <xref:Microsoft.CodeAnalysis.SyntaxNode.ChildNodes?displayProperty=nameWithType> kaynak metindeki konumlarına göre alt düğümlerin listesini sıralı sırayla döndüren bir yönteme sahiptir. Bu liste belirteçleri içermez. Her düğüm, bu düğüm tarafından köksünün <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantTokens%2A>köklediği alt ağaçta bulunan tüm düğümlerin, belirteçlerin veya ıvır zıvırLarın listesini temsil eden Torunlar'ı <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantTrivia%2A> <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantNodes%2A>inceleme yöntemlerine de sahiptir.

Buna ek olarak, her sözdizimi düğümü alt sınıfı, güçlü bir şekilde yazılan özellikler aracılığıyla aynı alt tüm alt sınıfları ortaya çıkarır. Örneğin, bir <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax> düğüm sınıfının ikili işleçlere <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Left>özgü <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.OperatorToken>üç <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Right>ek özelliği vardır: , , ve . Türü <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Left> ve <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Right> türüdür <xref:Microsoft.CodeAnalysis.CSharp.Syntax.ExpressionSyntax>, ve <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.OperatorToken> türüdür <xref:Microsoft.CodeAnalysis.SyntaxToken>.

Bazı sözdizimi düğümlerinin isteğe bağlı çocukları vardır. Örneğin, isteğe <xref:Microsoft.CodeAnalysis.CSharp.Syntax.IfStatementSyntax> bağlı <xref:Microsoft.CodeAnalysis.CSharp.Syntax.ElseClauseSyntax>bir . Çocuk yoksa, özellik null döndürür.

## <a name="syntax-tokens"></a>Sözdizimi belirteçleri

Sözdizimi belirteçleri, kodun en küçük sözdizimi parçalarını temsil eden dil dilbilgisinin terminalleridir. Onlar asla diğer düğümlerin veya belirteçlerin ebeveynleri değildir. Sözdizimi belirteçleri anahtar kelimeler, tanımlayıcılar, literals ve noktalama oluşur.

Verimlilik amacıyla, <xref:Microsoft.CodeAnalysis.SyntaxToken> tür bir CLR değer türüdür. Bu nedenle, sözdizimi düğümlerinin aksine, temsil edilen belirteç türüne bağlı olarak anlamı olan özelliklerin bir karışımı ile belirteçleri her türlü için tek bir yapı vardır.

Örneğin, tamsayı gerçek belirteci sayısal bir değeri temsil eder. Belirteç yayılma lı ham kaynak metne ek olarak, <xref:Microsoft.CodeAnalysis.SyntaxToken.Value> gerçek belirteç tam olarak çözülmüş tamsayı değerini söyleyen bir özelliğe sahiptir. Bu özellik, birçok <xref:System.Object> ilkel türden biri olabileceği nden olarak yazılır.

Özellik, <xref:Microsoft.CodeAnalysis.SyntaxToken.ValueText> <xref:Microsoft.CodeAnalysis.SyntaxToken.Value> özellik ile aynı bilgileri söyler; ancak bu özellik her <xref:System.String>zaman . C# kaynak metindeki bir tanımlayıcı Unicode kaçış karakterlerini içerebilir, ancak kaçış dizisinin sözdizimi tanımlayıcı adının bir parçası olarak kabul edilmez. Yani belirteç tarafından yayılan ham metin kaçış sırasını <xref:Microsoft.CodeAnalysis.SyntaxToken.ValueText> içerse de, özellik içermez. Bunun yerine, kaçış tarafından tanımlanan Unicode karakterleri içerir. Örneğin, kaynak metin , `\u03C0`olarak yazılmış bir tanımlayıcı içeriyorsa, bu belirteç için <xref:Microsoft.CodeAnalysis.SyntaxToken.ValueText> özellik döndürecek. `π`

## <a name="syntax-trivia"></a>Sözdizimi ıvır zıvırı

Sözdizimi trivia, kaynak metnin beyaz alan, açıklamalar ve önişlemci yönergeleri gibi kodun normal anlaşılması için büyük ölçüde önemsiz olan bölümlerini temsil eder. Sözdizimi belirteçleri gibi, ıvır zıvır da değer türleridir. Tek <xref:Microsoft.CodeAnalysis.SyntaxTrivia?displayProperty=nameWithType> tip ıvır zıvır her türlü tanımlamak için kullanılır.

Trivia normal dil sözdiziminin bir parçası olmadığından ve herhangi iki belirteç arasında herhangi bir yerde görünebildiği için, düğüm bir alt ad olarak sözdizimi ağacına dahil edilmez. Ancak, yeniden düzenleme gibi bir özelliği uygularken ve kaynak metinle tam sadakati korurken önemli olduklarından, sözdizimi ağacının bir parçası olarak bulunurlar.

Bir jetonun <xref:Microsoft.CodeAnalysis.SyntaxToken.LeadingTrivia?displayProperty=nameWithType> veya <xref:Microsoft.CodeAnalysis.SyntaxToken.TrailingTrivia?displayProperty=nameWithType> koleksiyonları inceleyerek ıvır zıvıra erişebilirsiniz. Kaynak metin ayrıştırıldığında, önemsiz diziler belirteçlerle ilişkilendirilir. Genel olarak, bir belirteç sonraki belirteç kadar aynı satırda sonra herhangi bir ıvır zıvır sahibi. Bu satırdan sonra herhangi bir ıvır zıvır aşağıdaki belirteç ile ilişkilidir. Kaynak dosyadaki ilk belirteç tüm ilk ıvır zıvırı alır ve dosyadaki son ıvır zıvır dizisi dosya sonu belirteciüzerine yapıştırılır, aksi takdirde sıfır genişliğe sahiptir.

Sözdizimi düğümleri ve belirteçleri aksine, sözdizimi trivia anne yok. Ancak, ağacın bir parçası oldukları ve her biri tek bir belirteçle ilişkili olduğundan, <xref:Microsoft.CodeAnalysis.SyntaxTrivia.Token?displayProperty=nameWithType> özelliği kullanmakla ilişkili olan belirtecine erişebilirsiniz.

## <a name="spans"></a>Yayılan

Her düğüm, belirteç veya trivia kaynak metin içindeki konumunu ve oluştuğu karakter sayısını bilir. Metin konumu, sıfır tabanlı `char` bir dizin olan 32 bittamsedi olarak gösterilir. Nesne, <xref:Microsoft.CodeAnalysis.Text.TextSpan> her ikisi de tamsayılar olarak temsil edilen başlangıç konumu ve karakter sayısıdır. Uzunluğu <xref:Microsoft.CodeAnalysis.Text.TextSpan> sıfırsa, iki karakter arasındaki konumu ifade eder.

Her düğümün <xref:Microsoft.CodeAnalysis.Text.TextSpan> iki <xref:Microsoft.CodeAnalysis.SyntaxNode.Span%2A> özelliği <xref:Microsoft.CodeAnalysis.SyntaxNode.FullSpan%2A>vardır: ve.

Özellik, <xref:Microsoft.CodeAnalysis.SyntaxNode.Span%2A> düğümün alt ağacındaki ilk belirteç başlangıcından son belirteci sonuna kadar olan metin aralığıdır. Bu açıklık, herhangi bir öncü veya izbırakan ıvır zıvır içermez.

Özellik <xref:Microsoft.CodeAnalysis.SyntaxNode.FullSpan%2A> düğüm normal açıklığı, artı herhangi bir satır veya iz civarı açıklığı içeren metin açıklığıdır.

Örnek:

``` csharp
      if (x > 3)
      {
||        // this is bad
          |throw new Exception("Not right.");|  // better exception?||
      }
```

Bloğun içindeki deyim düğümü, tek dikey çubuklarla (|) gösterilen bir açıklığa sahiptir. Karakterleri `throw new Exception("Not right.");`içerir. Tam açıklık çift dikey çubuklarla (||) gösterilir. Bu açıklık ve önde gelen ve izleyen ıvır zıvır ile ilişkili karakterler olarak aynı karakterleri içerir.

## <a name="kinds"></a>Her türlü

Her düğüm, belirteç veya trivia temsil <xref:System.Int32?displayProperty=nameWithType>edilen tam sözdizimi öğesini tanımlayan türü, bir <xref:Microsoft.CodeAnalysis.SyntaxNode.RawKind?displayProperty=nameWithType> özelliği vardır. Bu değer, dile özgü numaralandırmaya kullanılabilir. Her dil, C# veya Visual `SyntaxKind` Basic, dilbilgisindeki<xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind?displayProperty=nameWithType> <xref:Microsoft.CodeAnalysis.VisualBasic.SyntaxKind?displayProperty=nameWithType>tüm olası düğümleri, belirteçleri ve önemsiz öğeleri listeleyen tek bir numaralandırmaya (ve sırasıyla) sahiptir. Bu dönüştürme, uzantı yöntemlerine <xref:Microsoft.CodeAnalysis.CSharp.CSharpExtensions.Kind%2A?displayProperty=nameWithType> <xref:Microsoft.CodeAnalysis.VisualBasic.VisualBasicExtensions.Kind%2A?displayProperty=nameWithType> erişerek otomatik olarak yapılabilir.

Özellik, <xref:Microsoft.CodeAnalysis.SyntaxToken.RawKind> aynı düğüm sınıfını paylaşan sözdizimi düğümü türlerinin kolayca yok edilmesine olanak tanır. Belirteçler ve ıvır zıvır için bu özellik, bir öğe türünü diğerinden ayırmanın tek yoludur.

Örneğin, <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax> tek bir <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Left>sınıf <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.OperatorToken>vardır <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Right> , ve çocuk olarak. <xref:Microsoft.CodeAnalysis.CSharp.CSharpExtensions.Kind%2A> Özellik, sözdizimi düğümü <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.AddExpression> <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.SubtractExpression>nün <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.MultiplyExpression> bir , veya tür olup olmadığını ayırt eder.

## <a name="errors"></a>Hatalar

Kaynak metin sözdizimi hataları içerse bile, kaynak için çift yönlü eşzamanlı olan tam bir sözdizimi ağacı açığa çıkarır. Parser, dilin tanımlı sözdizimine uymayan kodla karşılaştığında, sözdizimi ağacı oluşturmak için iki teknikten birini kullanır.

İlk olarak, parser belirli bir tür belirteç bekliyor ancak bulamazsa, belirteç beklenen konumda sözdizimi ağacına eksik bir belirteç ekleyebilirsiniz. Eksik bir belirteç beklenen gerçek belirteci temsil eder, ancak <xref:Microsoft.CodeAnalysis.SyntaxNode.IsMissing?displayProperty=nameWithType> boş `true`bir açıklığı vardır ve özelliği döndürür.

İkinci olarak, ayrıştırmaya devam edebileceği bir belirteç ler bulana kadar parser belirteçleri atlayabilir. Bu durumda, atlanan belirteçleri tür <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.SkippedTokensTrivia>ile bir trivia düğüm olarak eklenir.
