---
title: .NET derleme Platform SDK sözdizimi modelini kullanın
description: Bu genel bakışta anlamak ve sözdizimi düğümleri yönetmek için kullandığınız türleri bir anlayış sağlar.
author: billwagner
ms.author: wiwagn
ms.date: 10/15/2017
ms.topic: conceptual
ms.prod: .net
ms.devlang: devlang-csharp
ms.custom: mvc
ms.openlocfilehash: 09d07e6257ad7d32d75328a8c1850888b4d0b937
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2018
---
# <a name="work-with-syntax"></a>Sözdizimi ile çalışma

**Sözdizimi ağacı** olan API'leri derleyici tarafından kullanıma sunulan bir temel veri yapısı. Bu ağaçları kaynak kod sözcük ve söz dizimi yapısını temsil eder. Bunlar, iki önemli amaca hizmet eder:

1. -Bir IDE gibi araçlar izin vermek için eklentiler, kod çözümleme araçları ve yapan yeniden düzenlemeler - görmek ve bir kullanıcının proje kaynak kodunda söz dizimi yapısını işlemek için.
2. Araçları - yapan yeniden düzenlemeler ve oluşturmak için bir IDE - gibi etkinleştirmek için değiştirmek ve kaynak kodu kullanım doğrudan metin düzenlemeleri gerek kalmadan doğal bir şekilde yeniden düzenleyin. Oluşturma ve ağaçları düzenleme araçları kolayca oluşturabilir ve kaynak kodu yeniden düzenleyin.

## <a name="syntax-trees"></a>Sözdizimi ağacı

Sözdizimi ağacı yeniden düzenleme, IDE özellikleri ve kod oluşturma kod analizi, bağlama, derleme için kullanılan birincil yapısı var. Kaynak kodun hiçbir bölümü ilk tanımlanan ve pek çok iyi bilinen yapısal dil öğeleri birine kategorilere olmadan anladım. 

Sözdizimi ağacı üç anahtar özniteliklere sahiptir. Sözdizimi ağacı tam bir güvenilirlik tüm kaynak bilgileri tutun ilk özniteliğidir. Başka bir deyişle, sözdizimi ağacı her bilgiye boşluk, açıklamalar ve önişlemci yönergeleri de dahil olmak üzere kaynak metni, her dilbilgisi yapısı, her sözcük belirteci ve şey arasındaki, bulunan içerir. Örneğin, tam olarak yazılmış şekilde kaynağında belirtilen her değişmez değeri gösterilir. Program Atlanan ya da eksik belirteçleri sözdizimi ağacında temsil eden eksik veya hatalı oluşturulmuş olduğunda sözdizimi ağaçları Ayrıca kaynak kod hatalarını temsil eder.  

Bu, söz dizimi ağaçları ikinci öznitelik sağlar. Ayrıştırıcının elde edilen bir sözdizimi ağacı gelen ayrıştırıldığında tam metin üretebilir. Tüm sözdizimi düğümden bu düğümden başlayan alt ağaç metin gösterimini alır mümkündür. Bu, söz dizimi ağaçları oluşturmak ve kaynak metnini düzenlemek için bir yol olarak kullanılabileceği anlamına gelir. Yeni bir ağaç değişiklikleri dışında varolan ağacına yapmadan eşdeğer metni oluşturulan uygulanır ve bir sözdizimi ağacı düzenleyerek sahip bir ağaç oluşturarak, metin etkili bir şekilde düzenlediniz. 

Üçüncü sözdizimi ağaçları değişmez ve iş parçacığı açısından güvenli olduğunu özniteliğidir.  Bu bir ağaç alındıktan sonra bu kodu geçerli durumunu anlık görüntüsüdür, hiçbir zaman anlamına gelir. Bu, aynı sözdizimi ağacı ile aynı anda farklı iş parçacıklarındaki kilitleme veya çoğaltma etkileşim kurmak birden çok kullanıcı sağlar. Çünkü ağaçları sabittir ve değişikliğe doğrudan ağacına yapılabilmesi için Fabrika yöntemleri oluşturmak ve ağaç ek anlık görüntüleri oluşturarak sözdizimi ağaçlarını değiştirme yardımcı olur. Yeni bir sürüm hızlı ve çok az ek bellek ile yeniden oluşturulması için temel alınan düğümleri yeniden şekilde ağaçları verimlidir.

Sözdizimi ağacı gerçek anlamda bir ağaç veri, burada terminal olmayan yapısal öğeler diğer öğeleri üst yapısıdır. Her söz dizimi ağaç düğümleri, belirteçleri ve trivia oluşur.  

## <a name="syntax-nodes"></a>Sözdizimi düğümler

Sözdizimi düğümleri sözdizimi ağaçları birincil öğelerini biridir. Bu düğümler bildirimleri, deyimleri, yan tümceleri ve ifadeler gibi söz dizimi yapıları temsil eder. Sözdizimi düğümlerinin her kategori türetilmiş ayrı bir sınıf tarafından temsil edilen <xref:Microsoft.CodeAnalysis.SyntaxNode?displayProperty=nameWithType>. Düğüm sınıfları kümesi Genişletilebilir değil. 

Tüm sözdizimi düğümleri her zaman diğer düğümler ve alt öğeleri olarak belirteçleri sahip oldukları anlamına gelir sözdizimi ağacındaki terminal olmayan düğümler var. Başka bir düğüm alt olarak, her düğümün üzerinden erişilen bir üst düğümün sahip <xref:Microsoft.CodeAnalysis.SyntaxNode.Parent?displayProperty=nameWithType> özelliği. Bir düğümün üst düğümleri ve ağaçları değişmez olduğundan, hiçbir zaman değiştirir. Ağaç kökü null üst öğe içermiyor.  

Her düğümün sahip bir <xref:Microsoft.CodeAnalysis.SyntaxNode.ChildNodes?displayProperty=nameWithType> kaynak metni konumlarını temel sıralı bir düzende alt düğümleri listesini döndürür yöntemi. Bu liste belirteçleri içermiyor. Her düğümün alt gibi incelemek için yöntemler de sahip <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantNodes%2A>, <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantTokens%2A>, veya <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantTrivia%2A> -tüm düğümler, belirteçleri veya bu düğüm tarafından kökü alt ağaç var trivia listesini temsil eder.  

Ayrıca, her bir sözdizimi düğüm alt hepsi aynı alt kesin türü belirtilmiş özellikleri aracılığıyla kullanıma sunar. Örneğin, bir <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax> düğümü sınıfına sahip üç ek özellikler için ikili işleçler belirli: <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Left>, <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.OperatorToken>, ve <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Right>. Türü <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Left> ve <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Right> olan <xref:Microsoft.CodeAnalysis.CSharp.Syntax.ExpressionSyntax>ve türünü <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.OperatorToken> olan <xref:Microsoft.CodeAnalysis.SyntaxToken>.

İsteğe bağlı alt bazı sözdizimi düğümünüz. Örneğin, bir <xref:Microsoft.CodeAnalysis.CSharp.Syntax.IfStatementSyntax> isteğe sahip <xref:Microsoft.CodeAnalysis.CSharp.Syntax.ElseClauseSyntax>. Alt mevcut değilse, özelliği null döndürür. 

## <a name="syntax-tokens"></a>Sözdizimi belirteçleri

Sözdizimi, kodunun en küçük söz dizimi parçaları temsil eden dil dilbilgisi Terminal belirteçleridir. Hiçbir zaman diğer düğümleri veya belirteçleri üst oldukları. Anahtar sözcükler, tanımlayıcılar, değişmez değerleri ve noktalama sözdizimi belirteçleri oluşur. 

Verimlilik amacıyla <xref:Microsoft.CodeAnalysis.SyntaxToken> türü olan bir CLR değer türü. Bu nedenle, sözdizimi düğümleri farklı olarak, her türlü belirteçleri bağlı olarak temsil edilen belirteç türü anlamları özellikleri karışımını içeren için yalnızca bir yapısı yoktur.

Örneğin, bir tamsayı değişmez değer belirteci sayısal bir değeri temsil eder. Ek olarak ham kaynak metni belirteci yayılma değişmez değer belirteci sahip bir <xref:Microsoft.CodeAnalysis.SyntaxToken.Value> tam söyler özelliği Integer değeri kodunu çözdü. Bu özellik olarak yazılan <xref:System.Object> çünkü pek çok basit türlerden biri olabilir.

<xref:Microsoft.CodeAnalysis.SyntaxToken.ValueText> Özelliği bildirir, aynı bilgileri <xref:Microsoft.CodeAnalysis.SyntaxToken.Value> özellik; ancak bu özellik her zaman olarak yazılan <xref:System.String>. C# kaynak metni tanımlayıcıda Unicode kaçış karakterleri içerebilir, ancak kaçış sırası sözdizimi tanımlayıcı adı bir parçası olarak kabul edilmez. Belirtecin tarafından kapsanan ham metni kaçış sırası içeren ancak bunu <xref:Microsoft.CodeAnalysis.SyntaxToken.ValueText> özelliğini desteklemez. Bunun yerine, kaçış tarafından tanımlanan Unicode karakterler içerir. Örneğin, kaynak metin olarak yazılmış bir tanımlayıcı içeriyorsa `\u03C0`, sonra <xref:Microsoft.CodeAnalysis.SyntaxToken.ValueText> özelliği bu belirtece döndürecektir `π`.

## <a name="syntax-trivia"></a>Sözdizimi trivia

Sözdizimi trivia kodu, boşluk, açıklamalar ve önişlemci yönergeleri gibi normal anlamak için büyük ölçüde anlamsız kaynak metni bölümlerini temsil eder. Sözdizimi belirteçleri gibi trivia değer türleridir. Tek <xref:Microsoft.CodeAnalysis.SyntaxTrivia?displayProperty=nameWithType> türü trivia her türlü açıklamak için kullanılır.

Trivia normal dili sözdizimi parçası olmayan ve her iki belirteç arasında herhangi bir yerde görünebilir çünkü bunlar sözdizimi ağacında bir düğümün bir alt öğesi olarak dahil edilmez. Yeniden düzenleme gibi ve kaynak metinle tam uygunluğunu korumak için bir özellik uygularken önemli olduklarından, henüz sözdizimi ağacının bir parçası kalırlar.

Bir belirtecin inceleyerek trivia erişebilirsiniz <xref:Microsoft.CodeAnalysis.SyntaxToken.LeadingTrivia?displayProperty=nameWithType> veya <xref:Microsoft.CodeAnalysis.SyntaxToken.TrailingTrivia?displayProperty=nameWithType> koleksiyonları. Kaynak metni ayrıştırıldığında trivia dizilerini belirteçleri ile ilişkilendirilir. Genel olarak, bir belirteç herhangi trivia sonra aynı satıra kadar sonraki belirtece sahip olur. Tüm trivia o satırdan aşağıdaki belirteç ile ilişkilidir. Tüm ilk trivia kaynak dosyasında ilk belirteci alır ve son trivia dosyasında yapılan dizisini Sıfır Genişlik sahip değilse, dosya sonu belirteç sabitlenmiş.

Sözdizimi düğümleri ve belirteçleri aksine, sözdizimi trivia üst öğeleri yok. Henüz ağacının bir parçası olan ve her bir tek belirteçle ilişkili olduğu için kullanarak ilişkili olduğu belirteci erişebilir <xref:Microsoft.CodeAnalysis.SyntaxTrivia.Token?displayProperty=nameWithType> özelliği.

## <a name="spans"></a>Yayılma

Her düğüm, belirteç veya trivia kaynak metni ve oluşur karakter sayısı içindeki konumuna bilir. Bir metin konumu bir sıfır tabanlı olduğundan ve 32 bit tamsayı olarak temsil edilir `char` dizini. A <xref:Microsoft.CodeAnalysis.Text.TextSpan> nesnesidir başlangıç konumu ve karakter sayısını, her ikisi de tamsayı olarak temsil. Varsa <xref:Microsoft.CodeAnalysis.Text.TextSpan> bir sıfır uzunlukta olan iki karakter arasında bir konuma başvuruyor.

Her düğümü iki sahip <xref:Microsoft.CodeAnalysis.Text.TextSpan> özellikleri: <xref:Microsoft.CodeAnalysis.SyntaxNode.Span*> ve <xref:Microsoft.CodeAnalysis.SyntaxNode.FullSpan*>. 

<xref:Microsoft.CodeAnalysis.SyntaxNode.Span*> Düğümün alt ağaç ilk belirteç başından metin aralık son belirteç sonuna bir özelliktir. Bu aralık, başında veya sonunda trivia içermez.

<xref:Microsoft.CodeAnalysis.SyntaxNode.FullSpan*> Düğümün normal aralık yanı sıra, başında veya sonunda trivia aralık içeren metin aralık bir özelliktir.

Örneğin: 

``` csharp
      if (x > 3)
      {
||        // this is bad
          |throw new Exception("Not right.");|  // better exception?||
      }
```

Bloktaki deyimi düğüm tek dikey çubuk (|) tarafından gösterilen bir aralık sahiptir. Karakterler içeren `throw new Exception("Not right.");`. Tam aralık çift dikey çubuk (|) tarafından belirtilir. Aynı aralık olarak ve baştaki ve sondaki trivia ile ilişkili karakterler içerir.

## <a name="kinds"></a>Tür

Her düğüm, belirteç veya trivia sahip bir <xref:Microsoft.CodeAnalysis.SyntaxNode.RawKind?displayProperty=nameWithType> türünde özellik <xref:System.Int32?displayProperty=nameWithType>, gösterilen söz dizimi öğesi tanımlar. Bu değer için dile özgü numaralandırması çevirebilirsiniz; tek bir C# veya VB, her dil sahip `SyntaxKind` numaralandırması (<xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind?displayProperty=nameWithType> ve <xref:Microsoft.CodeAnalysis.VisualBasic.SyntaxKind?displayProperty=nameWithType>sırasıyla) tüm olası düğümleri, belirteçleri ve trivia öğeleri dilbilgisi listeler. Bu dönüştürme erişerek otomatik olarak yapılabilir <xref:Microsoft.CodeAnalysis.CSharp.CSharpExtensions.Kind*?displayProperty=nameWithType> veya <xref:Microsoft.CodeAnalysis.VisualBasic.VisualBasicExtensions.Kind*?displayProperty=nameWithType> genişletme yöntemleri.

<xref:Microsoft.CodeAnalysis.SyntaxToken.RawKind> Özelliği için aynı düğüm sınıfı paylaşmak sözdizimi düğüm türü kolay Kesinleştirme izin verir. Belirteçleri ve trivia için bu özellik bir öğe türü diğerinden ayırt etmek için tek yoludur. 

Örneğin, bir tek <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax> sınıfına sahip <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Left>, <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.OperatorToken>, ve <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Right> alt öğeleri olarak. <xref:Microsoft.CodeAnalysis.CSharp.CSharpExtensions.Kind*> Özelliği ayırt olduğunu bir <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.AddExpression>, <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.SubtractExpression>, veya <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.MultiplyExpression> sözdizimi düğümün tür.

## <a name="errors"></a>Hatalar

Kaynak metni bile sözdizimi hataları içeriyorsa, kaynak ayrıştırılabilmelerini tam sözdizimi ağacı açıktır. Ayrıştırıcının dili tanımlanmış sözdizimine uymuyor kod karşılaştığında, iki teknikleri birini sözdizimi ağacı oluşturmak için kullanır.

Ayrıştırıcı belirteci belirli bir tür bekliyor, ancak onu bulamazsa, ilk olarak, bu eksik belirteci belirteç bekleniyordu konumu sözdizimi ağacında yerleştirme. Eksik bir belirteç bekleniyordu gerçek belirteci temsil eder, ancak boş bir aralığın var ve kendi <xref:Microsoft.CodeAnalysis.SyntaxNode.IsMissing?displayProperty=nameWithType> özelliği döndürür `true`.

İkinci olarak, bir tane ayrıştırma burada devam edebilirsiniz bulana kadar ayrıştırıcı belirteçleri atlayabilirsiniz. Bu durumda, atlanan belirteçleri türü trivia düğümle olarak bağlı olan <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.SkippedTokensTrivia>.
