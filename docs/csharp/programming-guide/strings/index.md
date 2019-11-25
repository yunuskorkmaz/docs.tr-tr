---
title: Dizeler- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 06/27/2019
helpviewer_keywords:
- C# language, strings
- strings [C#]
ms.assetid: 21580405-cb25-4541-89d5-037846a38b07
ms.openlocfilehash: c6e29781f566fac0fd1219ac842a4838d631afb6
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73969711"
---
# <a name="strings-c-programming-guide"></a>Dizeler (C# Programlama Kılavuzu)
Dize, değeri Text olan <xref:System.String> türünde bir nesnedir. Dahili olarak, metin, <xref:System.Char> nesnelerinin sıralı salt okunurdur koleksiyonu olarak depolanır. C# Dizenin sonunda null sonlandırma karakteri yoktur; Bu nedenle C# , bir dize herhangi bir sayıda katıştırılmış null karakteri (' \ 0 ') içerebilir. Bir dizenin <xref:System.String.Length%2A> özelliği, Unicode karakterlerin sayısını değil, içerdiği `Char` nesne sayısını temsil eder. Bir dizedeki tek tek Unicode kod noktalarına erişmek için <xref:System.Globalization.StringInfo> nesnesini kullanın.  
  
## <a name="string-vs-systemstring"></a>String ve System. String karşılaştırması  
 ' C#De, `string` anahtar sözcüğü <xref:System.String>bir diğer addır. Bu nedenle, `String` ve `string` eşdeğerdir ve tercih ettiğiniz adlandırma kuralını kullanabilirsiniz. `String` sınıfı dizeleri güvenli bir şekilde oluşturmak, işlemek ve karşılaştırmak için birçok yöntem sağlar. Ayrıca, C# dil, yaygın dize işlemlerini basitleştirmek için bazı işleçleri aşırı yükler. Anahtar sözcüğü hakkında daha fazla bilgi için bkz. [String](../../language-reference/builtin-types/reference-types.md). Türü ve yöntemleri hakkında daha fazla bilgi için bkz. <xref:System.String>.  
  
## <a name="declaring-and-initializing-strings"></a>Dizeleri bildirme ve başlatma  
 Aşağıdaki örnekte gösterildiği gibi çeşitli yollarla dizeler bildirebilir ve başlatabilirsiniz:  
  
 [!code-csharp[csProgGuideStrings#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#1)]  
  
 Dizenin bir karakter dizisiyle başlatılması dışında bir dize nesnesi oluşturmak için [New](../../language-reference/operators/new-operator.md) işlecini kullanmayacağınızı unutmayın.  
  
 Dizesi sıfır uzunluklu olan yeni bir <xref:System.String> nesnesi oluşturmak için <xref:System.String.Empty> sabit değeri ile bir dize başlatın. Sıfır uzunluklu bir dizenin dize sabit temsili "" dir. Dizeleri [null](../../language-reference/keywords/null.md)yerine <xref:System.String.Empty> değeriyle başlatarak, bir <xref:System.NullReferenceException> oluşma olasılığını azaltabilirsiniz. Bir dizenin değerini erişmeyi denemeden önce doğrulamak için statik <xref:System.String.IsNullOrEmpty%28System.String%29> yöntemini kullanın.  
  
## <a name="immutability-of-string-objects"></a>Dize nesnelerinin kullanılabilirliği  
 Dize nesneleri *sabittir*: oluşturulduktan sonra değiştirilemez. Bir dizeyi değiştirmek için görünen tüm C# <xref:System.String> yöntemleri ve işleçleri, sonuçları yeni bir dize nesnesi olarak döndürür. Aşağıdaki örnekte, `s1` ve `s2` içerikleri tek bir dize oluşturacak şekilde bitiştirildiği zaman, iki özgün dize değiştirilmemiş olur. `+=` işleci, Birleşik içerikleri içeren yeni bir dize oluşturur. Bu yeni nesne `s1`değişkenine atanır ve başka bir değişken kendisine başvuru içermediğinden, `s1` atanmış olan özgün nesne çöp toplama için serbest bırakılır.  
  
 [!code-csharp[csProgGuideStrings#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#2)]  
  
 Bir "değişiklik" dizesi aslında yeni bir dize oluşturma olduğundan, dizelere başvurular oluştururken dikkatli olmanız gerekir. Bir dizeye başvuru oluşturursanız ve sonra özgün dizeyi "değiştirirseniz", başvuru, dize değiştirildiğinde oluşturulan yeni nesne yerine özgün nesneyi işaret etmeye devam edecektir. Aşağıdaki kod bu davranışı göstermektedir:  
  
 [!code-csharp[csProgGuideStrings#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#25)]  
  
 Özgün dizedeki arama ve değiştirme işlemleri gibi değişikliklere dayalı yeni dizeler oluşturma hakkında daha fazla bilgi için bkz. [dize içeriğini değiştirme](../../how-to/modify-string-contents.md).  
  
## <a name="regular-and-verbatim-string-literals"></a>Normal ve tam dize sabit değerleri  
 Aşağıdaki örnekte gösterildiği gibi, tarafından C#verilen kaçış karakterlerini katıştırmanız gerektiğinde normal dize değişmez değerlerini kullanın:  
  
 [!code-csharp[csProgGuideStrings#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#3)]  
  
 Dize metninde, örneğin dosya yollarında ters eğik çizgi karakterleri içerdiğinde, kolay ve daha iyi okunabilirlik için tam dizeler kullanın. Harfine dizeler dize metninin bir parçası olarak yeni satır karakterlerini koruduğundan, çok satırlı dizeleri başlatmak için kullanılabilirler. Tam bir dizenin içine tırnak işareti eklemek için çift tırnak işaretleri kullanın. Aşağıdaki örnek, tam dizeler için bazı yaygın kullanımları göstermektedir:  
  
 [!code-csharp[csProgGuideStrings#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#4)]  
  
## <a name="string-escape-sequences"></a>Dize kaçış dizileri  
  
|Kaçış sırası|Karakter adı|Unicode kodlaması|  
|---------------------|--------------------|----------------------|  
|\\'|Tek tırnak|0x0027|  
|\\"|Çift tırnak|0x0022|  
|\\\\ |Sola|0x005C|  
|izin|Null|0x0000|  
|\|Uyarı|0x0007|  
|\b|Geri Al tuşu|0x0008|  
|\f|Form akışı|0x000C|  
|\n|Yeni satır|0x000A|  
|\r|Satır başı|0x000D|  
|\t|Yatay sekme|0x0009|  
|\v|Dikey sekme|0x000B|  
|\u|Unicode kaçış sırası (UTF-16)|`\uHHHH` (Aralık: 0000-FFFF; örnek: `\u00E7` = "ç")|  
|\U|Unicode kaçış sırası (UTF-32)|`\U00HHHHHH` (Range: 000000 yazın-10FFFF; örnek: `\U0001F47D` = "&#x1F47D;")|  
|\x|Değişken uzunluğu dışında, "\u" şuna benzer Unicode kaçış sırası|`\xH[H][H][H]` (Aralık: 0-FFFF; örnek: `\x00E7` veya `\x0E7` ya da `\xE7` = "ç")|  
  
> [!WARNING]
> `\x` kaçış sırasını kullanırken ve 4 onaltılık basamak belirtirken, kaçış sırasını hemen izleyen karakterler geçerli onaltılık basamaklar (yani 0-9, A-F ve a-f), kaçış sırasının bir parçası olarak yorumlanır. Örneğin, `\xA1`, U +&#161;00A1 kod noktası olan "" üretir. Ancak, sonraki karakter "A" veya "a" ise, kaçış sırası `\xA1A` olarak yorumlanır ve "" kod noktası U + 0A1A olan&#x0A1A;"" üretir. Bu gibi durumlarda, tüm 4 onaltılık basamakları (örn. `\x00A1`) belirtmek olası hatalı yorumlamayı engeller.  
  
> [!NOTE]
> Derleme zamanında, tam dizeler aynı kaçış dizileri ile normal dizelere dönüştürülür. Bu nedenle, hata ayıklayıcı izleme penceresinde tam bir dizeyi görürseniz, kaynak kodunuzdaki tam sürümü değil, derleyici tarafından eklenen kaçış karakterlerini görürsünüz. Örneğin, tam dize `@"C:\files.txt"` izleme penceresinde "C:\\\files.txt" olarak görüntülenir.  
  
## <a name="format-strings"></a>Biçim dizeleri  
 Biçim dizesi, içeriği çalışma zamanında dinamik olarak belirlenen bir dizedir. Biçim dizeleri, bir dize içindeki küme ayraçları içine *enterpolasyonlu ifadeler* veya yer tutucuları katıştırarak oluşturulur. Küme ayraçları (`{...}`) içindeki her şey, çalışma zamanında biçimli bir dize olarak bir değer ve çıkışa çözümlenir. Biçim dizeleri oluşturmak için iki yöntem vardır: dize ilişkilendirme ve bileşik biçimlendirme.

### <a name="string-interpolation"></a>Dize Ilişkilendirme
C# 6,0 ve üzeri sürümlerde bulunan, [*enterpolasyonlu dizeler*](../../language-reference/tokens/interpolated.md) `$` özel karakter tarafından tanımlanır ve araya alınmış ifadeleri küme ayraçları içine dahil eder. Dize ilişkilendirme konusunda yeni bir adım için bkz. hızlı bir genel bakış için [dize ilişkilendirme- C# Etkileşimli öğretici](../../tutorials/exploration/interpolated-strings.yml) .

Kodlarınızın okunabilirliğini ve bakımlılığını artırmak için dize ilişkilendirmeyi kullanın. Dize ilişkilendirme `String.Format` yöntemiyle aynı sonuçlara erişir, ancak kullanım kolaylığı ve satır içi açıklık geliştirir.

[!code-csharp[csProgGuideFormatStrings](~/samples/snippets/csharp/programming-guide/strings/Strings_1.cs#StringInterpolation)]

### <a name="composite-formatting"></a>Bileşik Biçimlendirme
<xref:System.String.Format%2A?displayProperty=nameWithType>, biçim dizesi oluşturmak için yer tutucuları parantez içinde kullanır. Bu örnek, yukarıda kullanılan dize ilişkilendirme yöntemine benzer bir çıkışa neden olur.
  
[!code-csharp[csProgGuideFormatStrings](~/samples/snippets/csharp/programming-guide/strings/Strings_1.cs#StringFormat)]

.NET türlerini biçimlendirme hakkında daha fazla bilgi için bkz. [.net 'Teki biçimlendirme türleri](../../../standard/base-types/formatting-types.md).
  
## <a name="substrings"></a>Dizelerin  
 Alt dize, bir dizede yer alan herhangi bir karakter dizisidir. Özgün dizenin bir bölümünden yeni bir dize oluşturmak için <xref:System.String.Substring%2A> yöntemini kullanın. <xref:System.String.IndexOf%2A> yöntemini kullanarak bir alt dizenin bir veya daha fazla örneğini arayabilirsiniz. Belirtilen bir alt dizenin tüm oluşumlarını yeni bir dizeyle değiştirmek için <xref:System.String.Replace%2A> yöntemini kullanın. <xref:System.String.Substring%2A> yöntemi gibi, <xref:System.String.Replace%2A> aslında yeni bir dize döndürür ve özgün dizeyi değiştirmez. Daha fazla bilgi için bkz. [dizeleri arama](../../how-to/search-strings.md) ve [dize içeriğini değiştirme](../../how-to/modify-string-contents.md).
  
 [!code-csharp[csProgGuideStrings#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#9)]  
  
## <a name="accessing-individual-characters"></a>Ayrı karakterlere erişme  
 Aşağıdaki örnekte olduğu gibi tek tek karakterlere salt okuma erişimi elde etmek için dizi gösterimini bir dizin değeriyle birlikte kullanabilirsiniz:  
  
 [!code-csharp[csProgGuideStrings#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#8)]  
  
 <xref:System.String> Yöntemler bir dizedeki bağımsız karakterleri değiştirmek için sahip olmanız gereken işlevselliği sağlamıyorsa, "yerinde" karakterlerini tek tek değiştirmek için bir <xref:System.Text.StringBuilder> nesnesi kullanabilir ve sonra sonuçları depolamak için yeni bir dize oluşturabilirsiniz <xref:System.Text.StringBuilder> Yöntem. Aşağıdaki örnekte, özgün dizeyi belirli bir şekilde değiştirmeniz ve ardından daha sonra kullanmak üzere sonuçları depolamanız gerektiğini varsayalım:  
  
 [!code-csharp[csProgGuideStrings#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#27)]  
  
## <a name="null-strings-and-empty-strings"></a>Null dizeler ve boş dizeler  
 Boş dize, sıfır karakter içeren bir <xref:System.String?displayProperty=nameWithType> nesnesinin örneğidir. Boş dizeler, genellikle boş bir metin alanını göstermek için çeşitli programlama senaryolarında kullanılır. Nesneleri <xref:System.String?displayProperty=nameWithType> geçerli dizeler için çağırabilirsiniz. Boş dizeler aşağıdaki şekilde başlatılır:  
  
```csharp  
string s = String.Empty;  
```  
  
 Buna karşılık, bir null dize bir <xref:System.String?displayProperty=nameWithType> nesnesinin örneğine başvurmaz ve null dize üzerinde bir yöntemi çağırma girişimi bir <xref:System.NullReferenceException>neden olur. Ancak, birleştirme ve karşılaştırma işlemlerinde aynı dizeleri diğer dizelerle birlikte kullanabilirsiniz. Aşağıdaki örneklerde, bir null dize başvurusunun oluşturulduğu ve bir özel durumun oluşturulmasına neden olmadığı bazı durumlar gösterilmektedir:  
  
 [!code-csharp[csProgGuideStrings#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#20)]  
  
## <a name="using-stringbuilder-for-fast-string-creation"></a>Hızlı dize oluşturma için StringBuilder kullanma  
 .NET 'teki dize işlemleri yüksek oranda iyileştirilmiştir ve çoğu durumda performansı önemli ölçüde etkilemez. Ancak, çok sayıda yüzlerce veya binlerce kez yürütülen sıkı döngüler gibi bazı senaryolarda, dize işlemleri performansı etkileyebilir. <xref:System.Text.StringBuilder> sınıfı, programınız çok sayıda dize işlemeleri gerçekleştiriyorsa daha iyi performans sağlayan bir dize arabelleği oluşturur. <xref:System.Text.StringBuilder> dize, yerleşik dize veri türünün desteklemediği bir şeyi tek tek yeniden atayabilmenizi de sağlar. Bu kod, örneğin, yeni bir dize oluşturmadan bir dizenin içeriğini değiştirir:  
  
 [!code-csharp[csProgGuideStrings#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#15)]  
  
 Bu örnekte, bir <xref:System.Text.StringBuilder> nesnesi bir sayısal türler kümesinden dize oluşturmak için kullanılır:  
  
 [!code-csharp[TestStringBuilder#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/TestStringBuilder.cs)]
  
## <a name="strings-extension-methods-and-linq"></a>Dizeler, uzantı yöntemleri ve LINQ  
 <xref:System.String> türü <xref:System.Collections.Generic.IEnumerable%601>uyguladığından, dizeler üzerinde <xref:System.Linq.Enumerable> sınıfında tanımlanan genişletme yöntemlerini kullanabilirsiniz. Görsel dağınıklığı önlemek için, bu yöntemler <xref:System.String> türü için IntelliSense 'den dışlanır, ancak yine de kullanılabilir. Ayrıca, dizeler üzerinde [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu ifadeleri de kullanabilirsiniz. Daha fazla bilgi için bkz. [LINQ ve dizeler](../concepts/linq/linq-and-strings.md).  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Konu|Açıklama|  
|-----------|-----------------|  
|[Dize içeriklerini değiştirme](../../how-to/modify-string-contents.md)|Dizeleri dönüştürme ve dizelerin içeriğini değiştirme tekniklerini gösterir.|  
|[Dizeleri karşılaştırma](../../how-to/compare-strings.md)|Dizelerin sıralı ve kültüre özgü karşılaştırmalarının nasıl gerçekleştirileceğini gösterir.|  
|[Birden çok dizeyi birleştirme](../../how-to/concatenate-multiple-strings.md)|Birden çok dizeyi tek tek birleştirmek için çeşitli yollar gösterir.|
|[String. Split kullanarak dizeleri ayrıştırma](../../how-to/parse-strings-using-split.md)|Dizeleri ayrıştırmak için `String.Split` yönteminin nasıl kullanılacağını gösteren kod örnekleri içerir.|  
|[Dizeleri arama](../../how-to/search-strings.md)|Dizelerde belirli metin veya desenler için aramanın nasıl kullanılacağını açıklar.|  
|[Bir dizenin sayısal bir değeri temsil edip etmediğini belirleme](./how-to-determine-whether-a-string-represents-a-numeric-value.md)|Geçerli bir sayısal değer olup olmadığını görmek için bir dizeyi güvenli bir şekilde ayrıştırmayı gösterir.|  
|[Dize ilişkilendirme](../../language-reference/tokens/interpolated.md)|Dizeleri biçimlendirmek için uygun bir sözdizimi sağlayan dize ilişkilendirme özelliğini açıklar.|
|[Temel Dize İşlemleri](../../../standard/base-types/basic-string-operations.md)|Temel dize işlemleri gerçekleştirmek için <xref:System.String?displayProperty=nameWithType> ve <xref:System.Text.StringBuilder?displayProperty=nameWithType> yöntemlerini kullanan konulara bağlantılar sağlar.|  
|[Dizeleri Ayrıştırma](../../../standard/base-types/parsing-strings.md)|.NET temel türlerinin dize temsillerini karşılık gelen türlerin örneklerine nasıl dönüştüreceğiniz açıklanmıştır.|  
|[.NET 'teki tarih ve saat dizelerini ayrıştırma](../../../standard/base-types/parsing-datetime.md)|"01/24/2008" gibi bir dizenin <xref:System.DateTime?displayProperty=nameWithType> nesnesine nasıl dönüştürüleceğini gösterir.|  
|[Dizeleri Karşılaştırma](../../../standard/base-types/comparing.md)|Dizelerin nasıl karşılaştırılacağı hakkında bilgiler içerir ve C# ve Visual Basic örnekler sağlar.|  
|[StringBuilder Sınıfını Kullanma](../../../standard/base-types/stringbuilder.md)|<xref:System.Text.StringBuilder> sınıfını kullanarak dinamik dize nesnelerinin nasıl oluşturulduğunu ve değiştirileceğini açıklar.|  
|[LINQ ve Dizeler](../concepts/linq/linq-and-strings.md)|LINQ sorguları kullanılarak çeşitli dize işlemlerinin nasıl gerçekleştirileceği hakkında bilgi sağlar.|  
|[C# Programlama Kılavuzu](../index.md)|İçinde C#programlama yapılarını açıklayan konuların bağlantılarını sağlar.|  
