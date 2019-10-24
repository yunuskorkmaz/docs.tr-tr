---
title: .NET Compiler Platform SDK sözdizimi modelini kullanın
description: Bu genel bakışta, söz dizimi düğümlerini anlamak ve işlemek için kullandığınız türlerin anlaşılması sağlanır.
ms.date: 10/15/2017
ms.custom: mvc
ms.openlocfilehash: 940d2756ef7735ee96d38d0286f99fadf7b81dc6
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72774094"
---
# <a name="work-with-syntax"></a>Söz dizimi ile çalışma

**Sözdizimi ağacı** , derleyici API 'leri tarafından kullanıma sunulan temel bir veri yapısıdır. Bu ağaçlar, kaynak kodunun sözlü ve sözdizimsel yapısını temsil eder. Bunlar iki önemli amaca hizmet eder:

1. IDE, Eklentiler, kod analizi araçları ve yeniden düzenlemeler gibi araçlara izin vermek için, bir kullanıcının projesindeki kaynak kodun sözdizimsel yapısını görmek ve işlemek için.
2. Yeniden düzenlemeler ve IDE gibi araçları etkinleştirmek için-doğrudan metin düzenlemeleri kullanmadan kaynak kodu doğal bir şekilde oluşturmak, değiştirmek ve yeniden düzenlemek için. Ağaçlar oluşturup düzenleyerek, araçlar kaynak kodu kolayca oluşturup yeniden düzenleyebilir.

## <a name="syntax-trees"></a>Sözdizimi ağaçları

Sözdizimi ağaçları, derleme, kod analizi, bağlama, yeniden düzenleme, IDE özellikleri ve kod oluşturma için kullanılan birincil yapıdır. Birinci olarak bilinen yapısal dil öğelerinden birinde tanımlanmadan ve sınıflandırılmadan kaynak kodun hiçbir bölümü anlaşılmamıştır.

Sözdizimi ağaçları üç anahtar özniteliğe sahiptir. İlk öznitelik, söz dizimi ağaçlarının tüm kaynak bilgilerini tam Aslına göre tutamadır. Bu, söz dizimi ağacının kaynak metinde bulunan her bilgi parçasını, her dilbilgisi yapısını, her sözcük belirtecini ve diğer her şeyi (boşluk, açıklamalar ve Önişlemci yönergeleri dahil) içerdiği anlamına gelir. Örneğin, kaynakta bahsedilen her bir sabit değer tam olarak yazıldığı gibi gösterilir. Söz dizimi ağaçları Ayrıca, söz dizimi ağacındaki Atlanan veya eksik belirteçleri temsil ederek, program eksik veya hatalı biçimlendirilmiş olduğunda kaynak kodundaki hataları da temsil eder.

Bu, söz dizimi ağaçlarının ikinci özniteliğini sunar. Ayrıştırıcıdan alınan bir sözdizimi ağacı, ayrıştırıldığına tam metni üretebilir. Herhangi bir söz dizimi düğümünden, kök ağacın alt ağacının metin temsilini bu düğüme almak mümkündür. Bu, söz dizimi ağaçlarının kaynak metni oluşturmak ve düzenlemek için bir yol olarak kullanılabileceği anlamına gelir. Bir ağaç oluşturarak denk metin oluşturmuş ve bir sözdizimi ağacını düzenleyerek, varolan bir ağaçtaki değişikliklerden daha fazla değişiklik yapmaktan yararlanarak, metni etkin bir şekilde düzenlediğiniz bir ağaç oluşturabilirsiniz.

Söz dizimi ağaçlarının üçüncü özniteliği, sabit ve iş parçacığı açısından güvenlidir.  Bu, bir ağaç alındıktan sonra kodun geçerli durumunun anlık görüntüsüdür ve hiçbir değişiklik yapılmadığı anlamına gelir. Bu, birden çok kullanıcının kilitleme veya çoğaltma olmadan farklı iş parçacıklarında aynı söz dizimi ağacıyla etkileşime geçmesini sağlar. Ağaçlar sabittir ve hiçbir değişiklik doğrudan bir ağaca yapılamaz, ancak Fabrika yöntemleri ağacın ek anlık görüntülerini oluşturarak sözdizimi ağaçları oluşturma ve değiştirme konusunda yardımcı olur. Ağaçlar, temel düğümleri yeniden kullanma biçiminde etkilidir, bu nedenle yeni bir sürüm hızlı bir şekilde ve çok fazla bellekle yeniden oluşturulabilir.

Sözdizimi ağacı, Terminal olmayan yapısal öğelerin üst diğer öğelerinden oluşan bir ağaç veri yapısıdır. Her bir sözdizimi ağacı düğümlerin, belirteçlerin ve trivia oluşur.

## <a name="syntax-nodes"></a>Sözdizimi düğümleri

Sözdizimi düğümleri, söz dizimi ağaçlarının birincil öğelerinden biridir. Bu düğümler, bildirimler, deyimler, yan tümceler ve ifadeler gibi sözdizimsel yapıları temsil eder. Her bir sözdizimi düğümleri kategorisi <xref:Microsoft.CodeAnalysis.SyntaxNode?displayProperty=nameWithType>türetilen ayrı bir sınıf tarafından temsil edilir. Düğüm sınıfları kümesi genişletilebilir değil.

Tüm sözdizimi düğümleri, söz dizimi ağacındaki Terminal olmayan düğümlerdir, bu da her zaman alt öğe olarak diğer düğümleri ve belirteçleri oldukları anlamına gelir. Başka bir düğümün alt öğesi olarak, her düğümün <xref:Microsoft.CodeAnalysis.SyntaxNode.Parent?displayProperty=nameWithType> özelliği aracılığıyla erişilebilen bir üst düğümü vardır. Düğümler ve ağaçlar sabit olduğundan, düğümün üst öğesi hiçbir şekilde değişmez. Ağacın kökü null bir üst öğeye sahip.

Her düğümün bir <xref:Microsoft.CodeAnalysis.SyntaxNode.ChildNodes?displayProperty=nameWithType> yöntemi vardır ve bu, kaynak metindeki konumlarına göre sıralı sırada alt düğümlerin bir listesini döndürür. Bu liste belirteç içermiyor. Her düğüm Ayrıca, bu düğüm tarafından kökü oluşturulan alt ağaçta var olan tüm düğümlerin, belirteçlerin veya bir listenin listesini temsil eden <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantNodes%2A>, <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantTokens%2A>veya <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantTrivia%2A> gibi alt öğeleri inceleme yöntemlerine sahiptir.

Ayrıca, her bir sözdizimi düğüm alt sınıfı, kesin belirlenmiş özellikler aracılığıyla aynı alt öğeleri gösterir. Örneğin, bir <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax> node sınıfı ikili işleçlere özgü üç ek özelliğe sahiptir: <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Left>, <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.OperatorToken>ve <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Right>. <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Left> ve <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Right> türü <xref:Microsoft.CodeAnalysis.CSharp.Syntax.ExpressionSyntax>ve <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.OperatorToken> türü <xref:Microsoft.CodeAnalysis.SyntaxToken>.

Bazı sözdizimi düğümlerinde isteğe bağlı alt öğeler vardır. Örneğin, bir <xref:Microsoft.CodeAnalysis.CSharp.Syntax.IfStatementSyntax> isteğe bağlı bir <xref:Microsoft.CodeAnalysis.CSharp.Syntax.ElseClauseSyntax>vardır. Alt öğe yoksa, özelliği null döndürür.

## <a name="syntax-tokens"></a>Sözdizimi belirteçleri

Sözdizimi belirteçleri, kodun en küçük sözdizimsel parçalarını temsil eden dil dilbilgisinde bulunan terminallerdir. Bunlar hiçbir şekilde diğer düğümlerin veya belirteçlerin hiçbir üst öğesi değildir. Sözdizimi belirteçleri anahtar sözcüklerden, tanımlayıcılardan, değişmez değerlerden ve noktalama işaretlerinden oluşur.

Verimlilik açısından, <xref:Microsoft.CodeAnalysis.SyntaxToken> türü bir CLR değer türüdür. Bu nedenle, sözdizimi düğümlerinden farklı olarak, temsil edilen belirtecin türüne bağlı olarak anlamı olan özelliklerin karışımına sahip tüm belirteç türleri için tek bir yapı vardır.

Örneğin, bir tamsayı sabit değeri bir sayısal değeri temsil eder. Belirtecin yayıldığı ham kaynak metnine ek olarak, sabit değer belirtecinin, kodu çözülmüş tam sayı değerini belirten bir <xref:Microsoft.CodeAnalysis.SyntaxToken.Value> özelliği vardır. Bu özellik birçok temel türden biri olabileceğinden <xref:System.Object> olarak yazılır.

<xref:Microsoft.CodeAnalysis.SyntaxToken.ValueText> özelliği, <xref:Microsoft.CodeAnalysis.SyntaxToken.Value> özelliğiyle aynı bilgileri size bildirir; Ancak bu özellik her zaman <xref:System.String>olarak yazılır. C# Kaynak metindeki bir tanımlayıcı Unicode kaçış karakterleri içerebilir, ancak kaçış dizisinin sözdizimi tanımlayıcı adının bir parçası olarak kabul edilmez. Bu nedenle, belirteç tarafından yayılan ham metin kaçış sırasını içerse de <xref:Microsoft.CodeAnalysis.SyntaxToken.ValueText> özelliği değildir. Bunun yerine, kaçış tarafından tanımlanan Unicode karakterleri içerir. Örneğin, kaynak metin `\u03C0`olarak yazılmış bir tanımlayıcı içeriyorsa, bu belirtecin <xref:Microsoft.CodeAnalysis.SyntaxToken.ValueText> özelliği `π`döndürür.

## <a name="syntax-trivia"></a>Sözdizimi bilgi

Sözdizimi bilgi kaynak metnin, beyaz boşluk, açıklama ve Önişlemci yönergeleri gibi kodu normal şekilde anlamak için büyük ölçüde önemli olan kısımlarını temsil eder. Sözdizimi belirteçleri gibi, bilgi değer türleridir. Tek <xref:Microsoft.CodeAnalysis.SyntaxTrivia?displayProperty=nameWithType> türü her türlü Tria 'nın açıklaması için kullanılır.

Bilgi normal dil sözdiziminin parçası olmadığından ve iki belirteç arasında bir yerde görünebildiğinden, bir düğümün alt öğesi olarak sözdizimi ağacına dahil edilmez. Henüz, yeniden düzenleme gibi bir özellik uygularken ve kaynak metinle tam uygunluğu sürdürmek için önemli olduklarından, söz dizimi ağacının bir parçası olarak mevcuttur.

Bir belirtecin <xref:Microsoft.CodeAnalysis.SyntaxToken.LeadingTrivia?displayProperty=nameWithType> veya <xref:Microsoft.CodeAnalysis.SyntaxToken.TrailingTrivia?displayProperty=nameWithType> koleksiyonlarını inceleyerek, bilgi 'a erişebilirsiniz. Kaynak metni ayrıştırıldığında, bilgi dizileri belirteçlerle ilişkilendirilir. Genel olarak, bir belirteç bir sonraki belirtece kadar aynı satıra kadar herhangi bir tribiya benzer. Bu satırdan sonraki her türlü bir değer aşağıdaki belirteçle ilişkilendirilir. Kaynak dosyadaki ilk simge, tüm başlangıç anlarını alır ve dosyadaki en son üç sıra, sıfır genişliğine sahip olan dosya sonu belirtecine göre belirlenir.

Söz dizimi düğümleri ve belirteçlerden farklı olarak söz dizimi bilgi üst öğeleri yoktur. Henüz, ağacın bir parçası olduklarından ve her biri tek bir belirteçle ilişkilendirildiği için, <xref:Microsoft.CodeAnalysis.SyntaxTrivia.Token?displayProperty=nameWithType> özelliğini kullanarak ilişkili olan belirtece erişebilirsiniz.

## <a name="spans"></a>Maları

Her düğüm, belirteç veya bilgi, kaynak metni içindeki konumunu ve içerdiği karakter sayısını bilir. Bir metin konumu, sıfır tabanlı `char` dizin olan 32 bitlik bir tamsayı olarak temsil edilir. <xref:Microsoft.CodeAnalysis.Text.TextSpan> nesnesi, her ikisi de tamsayılar olarak gösterilen başlangıç konumu ve karakter sayısıdır. <xref:Microsoft.CodeAnalysis.Text.TextSpan> sıfır uzunluğa sahipse, iki karakter arasındaki bir konuma başvurur.

Her düğüm iki <xref:Microsoft.CodeAnalysis.Text.TextSpan> özelliğe sahiptir: <xref:Microsoft.CodeAnalysis.SyntaxNode.Span*> ve <xref:Microsoft.CodeAnalysis.SyntaxNode.FullSpan*>.

<xref:Microsoft.CodeAnalysis.SyntaxNode.Span*> özelliği, düğümün alt ağacındaki ilk belirtecin başından son belirtecin sonuna kadar olan metindir. Bu yayılma, başında veya sonunda bir boşluk içermez.

<xref:Microsoft.CodeAnalysis.SyntaxNode.FullSpan*> özelliği, düğümün normal yayılımını ve önünde ya da sondaki üç nokta yayılmasını içeren metin yaydır.

Örneğin:

``` csharp
      if (x > 3)
      {
||        // this is bad
          |throw new Exception("Not right.");|  // better exception?||
      }
```

Bloğun içindeki deyimin düğümü, tek dikey çubuklar (|) ile belirtilen bir yayılım içeriyor. `throw new Exception("Not right.");`karakterleri içerir. Tam yayılma, çift dikey çubuklar (| |) ile belirtilir. Yayılma ile aynı karakterleri ve baştaki ve sondaki trivia ile ilişkili karakterleri içerir.

## <a name="kinds"></a>Farklı

Her düğüm, belirteç veya bilgi, temsil edilen tam sözdizimi öğesini tanımlayan <xref:System.Int32?displayProperty=nameWithType>türünde bir <xref:Microsoft.CodeAnalysis.SyntaxNode.RawKind?displayProperty=nameWithType> özelliğine sahiptir. Bu değer dile özgü bir numaralandırmaya atanabilir; Her dil C# veya vb, tüm olası düğümleri, belirteçleri ve dilbilgisinde bilgi öğelerini listeleyen tek bir`SyntaxKind`numaralandırması (sırasıyla<xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind?displayProperty=nameWithType>ve<xref:Microsoft.CodeAnalysis.VisualBasic.SyntaxKind?displayProperty=nameWithType>) vardır. Bu dönüştürme <xref:Microsoft.CodeAnalysis.CSharp.CSharpExtensions.Kind*?displayProperty=nameWithType> veya <xref:Microsoft.CodeAnalysis.VisualBasic.VisualBasicExtensions.Kind*?displayProperty=nameWithType> uzantısı yöntemlerine erişerek otomatik olarak yapılabilir.

<xref:Microsoft.CodeAnalysis.SyntaxToken.RawKind> özelliği, aynı düğüm sınıfını paylaşan sözdizimi düğümü türlerinin kolay bir şekilde kesinleştirilmesine olanak sağlar. Belirteçler ve trivia için, bu özellik bir öğe türünü diğerinden ayırt etmenin tek yoludur.

Örneğin, tek bir <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax> sınıfı alt öğe olarak <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Left>, <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.OperatorToken>ve <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Right> sahiptir. <xref:Microsoft.CodeAnalysis.CSharp.CSharpExtensions.Kind*> özelliği, bunun <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.AddExpression>, <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.SubtractExpression>veya <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.MultiplyExpression> tür bir sözdizimi düğümü olduğunu ayırt eder.

## <a name="errors"></a>Hatalar

Kaynak metin sözdizimi hataları içerdiğinde bile, kaynağa gidiş olarak dönüşümlü bir tam sözdizimi ağacı gösterilir. Ayrıştırıcı dilin tanımlı söz dizimi ile uyumlu olmayan kodla karşılaştığında, sözdizimi ağacı oluşturmak için iki teknikten birini kullanır.

Birincisi, ayrıştırıcı belirli bir belirteç türünü beklediğinde ancak bulamazsa, belirtecin beklenildiği konumdaki sözdizimi ağacına eksik bir belirteç eklenebilir. Eksik bir belirteç beklenen gerçek belirteci temsil eder, ancak boş bir yayılma alanına sahiptir ve <xref:Microsoft.CodeAnalysis.SyntaxNode.IsMissing?displayProperty=nameWithType> özelliği `true`döndürüyor.

İkincisi, ayrıştırıcının ayrıştırmaya devam edebilecekleri bir konum bulana kadar belirteçleri atlayabilirler. Bu durumda, atlanan belirteçler, türü <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.SkippedTokensTrivia>olan bir düğüm ile birlikte eklenir.
