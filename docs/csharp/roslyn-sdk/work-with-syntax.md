---
title: .NET derleyici Platformu SDK'sı söz dizimi modelini kullanın
description: Bu genel bakışta anlamak ve söz dizimi düğümleri işlemek için kullandığınız türleri bir anlayış sağlar.
ms.date: 10/15/2017
ms.custom: mvc
ms.openlocfilehash: a48d48168dffdb439c984f5b4209019514b3b970
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61706604"
---
# <a name="work-with-syntax"></a>Söz dizimi ile çalışma

**Söz dizimi ağacı** olan API'leri derleyici tarafından kullanıma sunulan bir temel veri yapısı. Bu ağaç, kaynak kodu sözcük ve söz dizimi yapısını temsil eder. Bunlar, iki önemli amaca hizmet eder:

1. Gibi bir IDE araçları - izin vermek için eklentileri, Kod Analizi araçları ve yeniden düzenlemeler - bakın ve bir kullanıcının proje kaynak kodunda sözdizimi yapısını işlemek için.
2. Araçları - yeniden düzenlemeler ve oluşturmak için bir IDE - gibi etkinleştirmek için değiştirme ve kaynak kodu, doğrudan metin düzenlemeleri kullanmak zorunda kalmadan doğal bir şekilde yeniden düzenleyin. Oluşturma ve ağaçları düzenleme araçları kolayca oluşturun ve kaynak kodu yeniden düzenleyin.

## <a name="syntax-trees"></a>Sözdizimi ağacı

Sözdizimi ağacı yeniden düzenleme, IDE özellikleri ve kod oluşturmayı bağlama, kod analizi, derleme için kullanılan birincil yapısı var. Kaynak kodun hiçbir kısmı ilk ve tanımlanmış birçok iyi bilinen yapısal dil öğelerini birine kategorilere olmadan anlaşılır. 

Sözdizimi ağacı üç anahtar özniteliklere sahiptir. Söz dizimi ağacı içinde tam uygunlukta tüm kaynak bilgileri tutmak ilk özniteliğidir. Başka bir deyişle, söz dizimi ağacı her bir parçası boşluk, açıklamalar ve ön işlemci yönergeleri dahil olmak üzere kaynak metni, her dilbilgisi yapısı, her sözcük temelli belirteç ve arasındaki, diğer her şey bulunan bilgiler içerir. Örneğin, tam olarak yazılmış şekilde kaynak bahsedilen her bir sabit değer gösterilir. Program sözdizimi ağacı belirteçleri Atlanan ya da eksik temsil eden tarafından eksik veya hatalı olduğunda söz dizimi ağacı ayrıca kaynak kodundaki hataları temsil eder.  

Bu ikinci öznitelik söz dizimi ağaçları sağlar. Ayrıştırıcının alınan bir sözdizimi ağacına gelen ayrıştırıldığında küpte tam metin üretebilir. Herhangi bir söz dizimi düğümünden metin temsili o düğümde kökü alt ağacı mümkündür. Başka bir deyişle, söz dizimi ağacı bir şekilde oluşturun ve kaynak metni düzenlemek için kullanılabilir. Yeni bir ağaç değişiklikleri dışında varolan ağacına yapma eşdeğer metin oluşturulan itiraz ve düzenleyerek bir sözdizimi ağacına sahip bir ağaç oluşturarak, metin etkili bir şekilde düzenlediniz. 

Üçüncü söz dizimi ağacı sabittir ve iş parçacığı açısından güvenli olmalarını özniteliğidir.  Bu bir ağaç alındıktan sonra bu kodun geçerli durumunun bir anlık görüntüdür, hiçbir zaman anlamına gelir. Bu, aynı söz dizimi ağacı ile aynı anda farklı iş parçacıklarında kilitlenmesi veya çoğaltma etkileşime geçmek birden fazla kullanıcı sağlar. Çünkü ağaçları sabittir ve bir ağaca doğrudan herhangi bir değişiklik yapılabilmesi için Fabrika yöntemleri oluşturun ve ek anlık görüntü ağacının oluşturarak söz dizimi ağaçlarını değiştirme yardımcı olur. Hızlı ve çok az ek bellek ile yeni bir sürüm oluşturulabilmesi için temel alınan düğümleri yeniden şekilde ağaçları verimlidir.

Sözdizimi ağacı terminal olmayan yapısal öğelerini diğer öğeleri nerede üst ağaç veri yapısı, tam anlamıyla olduğu. Her bir söz dizimi ağacı, düğümler, belirteçleri ve trivia yapılır.  

## <a name="syntax-nodes"></a>Söz dizimi düğümleri

Söz dizimi düğümleri söz dizimi ağacı birincil öğelerinden biridir. Bu düğümler, bildirimleri, deyimler, yan tümceleri ve ifadeler gibi bir söz dizimi yapıları temsil eder. Söz dizimi düğümlerinin her kategori türetilen ayrı bir sınıf tarafından temsil edilen <xref:Microsoft.CodeAnalysis.SyntaxNode?displayProperty=nameWithType>. Düğüm sınıf kümesi Genişletilebilir değildir. 

Tüm söz dizimi terminal olmayan düğümleri her zaman diğer düğümleri ve alt öğeleri olarak belirteçleri olduğu anlamına gelir. söz dizimi ağacı içinde düğümlerdir. Başka bir düğümün alt, her düğüm üzerinden erişilebilen bir üst düğümün sahip <xref:Microsoft.CodeAnalysis.SyntaxNode.Parent?displayProperty=nameWithType> özelliği. Düğümler ve ağaçları sabit olduğundan, üst düğümünün hiçbir zaman değiştirir. Ağacının kökü null bir üst öğeye sahip.  

Her düğüme sahip bir <xref:Microsoft.CodeAnalysis.SyntaxNode.ChildNodes?displayProperty=nameWithType> yöntemi kaynak metin konumlarına göre sıralı alt düğümlerin listesini döndürür. Bu liste, belirteç içermiyor. Her düğüm alt sınamak için yöntemlerini de sahip <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantNodes%2A>, <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantTokens%2A>, veya <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantTrivia%2A> -tüm düğümleri, belirteçleri veya o düğümün kökü alt ağaçta mevcut Meraklısına Notlar listesini temsil eder.  

Ayrıca, her bir sözdizimi düğümü alt hepsi aynı alt kesin olarak belirlenmiş özellikler aracılığıyla kullanıma sunar. Örneğin, bir <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax> düğümü sınıfı için ikili işleçler belirli üç ek özelliklere sahiptir: <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Left>, <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.OperatorToken>, ve <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Right>. Türünü <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Left> ve <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Right> olduğu <xref:Microsoft.CodeAnalysis.CSharp.Syntax.ExpressionSyntax>ve türünü <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.OperatorToken> olduğu <xref:Microsoft.CodeAnalysis.SyntaxToken>.

İsteğe bağlı alt öğeleri bazı sözdizimi düğümünüz. Örneğin, bir <xref:Microsoft.CodeAnalysis.CSharp.Syntax.IfStatementSyntax> isteğe sahip <xref:Microsoft.CodeAnalysis.CSharp.Syntax.ElseClauseSyntax>. Alt mevcut değilse özellik null döndürür. 

## <a name="syntax-tokens"></a>Söz dizimi belirteçleri

Söz dizimi, kod söz dizimi küçük parçaları temsil eden dil dilbilgisi terminaller belirteçleridir. Hiçbir zaman diğer düğümleri veya belirteçleri üst öğelerinin değildirler. Söz dizimi belirteçleri, anahtar sözcükler, tanımlayıcılar, değişmez değerler ve noktalama işaretleri oluşur. 

Verimliliği amacıyla <xref:Microsoft.CodeAnalysis.SyntaxToken> türü, bir CLR değer türüdür. Bu nedenle, söz dizimi düğümleri, tüm tür belirteçleri karışımından oluşan temsil edilen bir belirteç türünü bağlı olarak anlam taşıyan özellikler için yalnızca bir yapı yoktur.

Örneğin, bir tamsayı değişmez değer belirteci sayısal bir değeri temsil eder. Ham kaynak metin yanı sıra belirteci yayılma değişmez değer belirtece bir <xref:Microsoft.CodeAnalysis.SyntaxToken.Value> tam belirten özellik çözülmüş tamsayı değeri. Bu özellik olarak yazılan <xref:System.Object> çünkü çok basit türlerden biri olabilir.

<xref:Microsoft.CodeAnalysis.SyntaxToken.ValueText> Özelliği bildirir, aynı bilgileri <xref:Microsoft.CodeAnalysis.SyntaxToken.Value> özelliği; ancak bu özellik her zaman olarak yazılan <xref:System.String>. Bir tanımlayıcı C# kaynak metin, Unicode kaçış karakterlerini içerebilir, ancak çıkış dizisi söz dizimi tanımlayıcı adı bir parçası olarak kabul edilmez. Belirteç tarafından kapsanan ham metni kaçış sırası içerse bunu <xref:Microsoft.CodeAnalysis.SyntaxToken.ValueText> özelliği yok. Bunun yerine, kaçış tarafından tanımlanan Unicode karakterler içerir. Örneğin, kaynak metin olarak yazılan tanımlayıcının içeriyorsa `\u03C0`, ardından <xref:Microsoft.CodeAnalysis.SyntaxToken.ValueText> özelliği için bu belirteci döndürür `π`.

## <a name="syntax-trivia"></a>Söz dizimi Meraklısına Notlar

Söz dizimi Meraklısına notlar gibi boşluk, açıklamalar ve ön işlemci yönergelerini kodun normal anlamak için büyük ölçüde Önemsiz kaynak metin parçalarını temsil eder. Söz dizimi belirteçleri gibi Meraklısına Notlar değer türleridir. Tek <xref:Microsoft.CodeAnalysis.SyntaxTrivia?displayProperty=nameWithType> türü Meraklısına Notlar tüm türleri tanımlamak için kullanılır.

Meraklısına Notlar normal dil sözdiziminin bir parçası değildir ve herhangi iki belirteç arasında herhangi bir yeri görünebilir çünkü bunlar sözdizimi ağacında bir düğümün alt düğümü dahil edilmez. Henüz, bunlar yeniden düzenleme gibi ve kaynak metni ile tam uygunluğu korumak için bir özellik uygularken önemli olduğundan, bunlar söz dizimi ağacı bir parçası olarak mevcut.

Meraklısına Notlar bir belirtecin inceleyerek erişebileceğiniz <xref:Microsoft.CodeAnalysis.SyntaxToken.LeadingTrivia?displayProperty=nameWithType> veya <xref:Microsoft.CodeAnalysis.SyntaxToken.TrailingTrivia?displayProperty=nameWithType> koleksiyonları. Kaynak metni ayrıştırıldığında Meraklısına Notlar dönüştürülmelerini belirteçleri ile ilişkilidir. Genel olarak, bir belirteç tüm Meraklısına Notlar sonra aynı satıra kadar sonraki belirtece sahip. Bu satırdan herhangi trivia aşağıdaki belirteciyle ilişkilendirilmiş olması gerekir. Kaynak dosyadaki ilk belirteçten tüm ilk trivia alır ve trivia dosyasındaki son dizi olan aksi Sıfır Genişlik dosya sonu belirteci sabitlenmiş.

Söz dizimi düğümleri ve belirteçleri aksine, söz dizimi trivia üst öğeleri yok. Henüz her tek bir belirteçle ilişkilendirilir ve ağacın parçası olduğundan, belirteci kullanarak ilişkili olduğu erişebilir <xref:Microsoft.CodeAnalysis.SyntaxTrivia.Token?displayProperty=nameWithType> özelliği.

## <a name="spans"></a>Yayılma

Her düğüm, belirteç veya trivia kaynak metni ve içerdiği karakter sayısını içindeki konumuna bilir. Bir metin konumu sıfır tabanlı bir 32 bit tamsayı olarak temsil edilen `char` dizini. A <xref:Microsoft.CodeAnalysis.Text.TextSpan> nesne başlangıç konumu ve karakter sayısı, her ikisi de tamsayı olarak temsil edilir. Varsa <xref:Microsoft.CodeAnalysis.Text.TextSpan> bir sıfır uzunluğuna sahip iki karakter arasına bir konuma başvuruyor.

Her düğümü iki içeren <xref:Microsoft.CodeAnalysis.Text.TextSpan> özellikleri: <xref:Microsoft.CodeAnalysis.SyntaxNode.Span*> ve <xref:Microsoft.CodeAnalysis.SyntaxNode.FullSpan*>. 

<xref:Microsoft.CodeAnalysis.SyntaxNode.Span*> Düğümün alt ağacı ilk belirteci başlangıcı metin aralığı son belirteç sonuna bir özelliktir. Bu aralık, başında veya sonunda tüm Meraklısına Notlar içermez.

<xref:Microsoft.CodeAnalysis.SyntaxNode.FullSpan*> Düğümün normal yayılma yanı sıra, herhangi bir başında veya sonunda trivia aralık içeren metin aralığı bir özelliktir.

Örneğin: 

``` csharp
      if (x > 3)
      {
||        // this is bad
          |throw new Exception("Not right.");|  // better exception?||
      }
```

Deyimi düğümü bloktaki tek dikey çubuk (|) tarafından belirtilen bir yayılma vardır. Karakterleri içeren `throw new Exception("Not right.");`. Tam aralık çift dikey çubuk (|) tarafından belirtilir. Bu, aynı aralık olarak, baştaki ve sondaki Meraklısına Notlar ile ilişkili karakter içerir.

## <a name="kinds"></a>Tür

Her düğüm, belirteç veya Meraklısına Notlar bir <xref:Microsoft.CodeAnalysis.SyntaxNode.RawKind?displayProperty=nameWithType> türünün özelliği <xref:System.Int32?displayProperty=nameWithType>, temsil edilen söz dizimi öğe tanımlar. Bu değer bir dile özgü sabit listesine dönüştürülebilen; Her bir dilin C# veya VB, tek bir `SyntaxKind` numaralandırması (<xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind?displayProperty=nameWithType> ve <xref:Microsoft.CodeAnalysis.VisualBasic.SyntaxKind?displayProperty=nameWithType>sırasıyla), tüm olası düğümlerinin, belirteçleri ve Meraklısına Notlar öğeleri dilbilgisi içinde listelenir. Bu dönüştürme erişerek otomatik olarak yapılabilir <xref:Microsoft.CodeAnalysis.CSharp.CSharpExtensions.Kind*?displayProperty=nameWithType> veya <xref:Microsoft.CodeAnalysis.VisualBasic.VisualBasicExtensions.Kind*?displayProperty=nameWithType> genişletme yöntemleri.

<xref:Microsoft.CodeAnalysis.SyntaxToken.RawKind> Özelliği için aynı düğümü sınıfı paylaşan sözdizimi düğümü türleri kolay Kesinleştirme sağlar. Belirteçler ve Meraklısına notlar için bu özellik öğesi bir tür diğerinden ayırt etmek için tek yoludur. 

Örneğin, bir tek <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax> sınıfında <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Left>, <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.OperatorToken>, ve <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Right> alt öğeleri olarak. <xref:Microsoft.CodeAnalysis.CSharp.CSharpExtensions.Kind*> Özelliği olduğunu ayıran bir <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.AddExpression>, <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.SubtractExpression>, veya <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.MultiplyExpression> söz dizimi düğümünün türü.

## <a name="errors"></a>Hatalar

Kaynak metni söz dizimi hataları içerdiğinde, bile, hepsini kaynağına ayrıştırılabilmelerini sağlamak üzere bir tam söz dizimi ağacı kullanıma sunulur. Ayrıştırıcının dili tanımlanan sözdizimine uygun değil kod karşılaştığında, iki tekniklerden birini söz dizimi ağacı oluşturmak için kullanır.

İlk olarak, ayrıştırıcının belirli bir belirteç türünü bekliyor, ancak bunu bulamaz, belirteç bekleniyordu konumda söz dizimi ağacı içinde eksik bir belirteç ekleyebilirsiniz. Eksik bir belirteç bekleniyordu gerçek belirteci temsil eder, ancak boş bir yayılma vardır ve kendi <xref:Microsoft.CodeAnalysis.SyntaxNode.IsMissing?displayProperty=nameWithType> özelliği döndürür `true`.

İkinci olarak, bunu bir ayrıştırma burada devam edebilirsiniz bulana kadar ayrıştırıcının belirteçleri atlayabilirsiniz. Bu durumda, atlanan belirteçleri trivia düğüm türü ile olarak eklenen <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.SkippedTokensTrivia>.
