---
title: Dizeler-C# Programlama Kılavuzu
description: C# programlamasında dizeler hakkında bilgi edinin. Dizeleri bildirme ve başlatma, dize nesnelerinin imlebilirlik ve dize kaçış dizileri hakkında bilgi için bkz..
ms.date: 06/27/2019
helpviewer_keywords:
- C# language, strings
- strings [C#]
ms.assetid: 21580405-cb25-4541-89d5-037846a38b07
ms.openlocfilehash: 8e833bdeefcce2f12c839738b43778df8e54fa5b
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381612"
---
# <a name="strings-c-programming-guide"></a>Dizeler (C# Programlama Kılavuzu)
Dize, değeri Text olan türünde bir nesnedir <xref:System.String> . Dahili olarak, metin sıralı bir salt okunabilir nesne koleksiyonu olarak depolanır <xref:System.Char> . C# dizesinin sonunda null sonlandırma karakteri yoktur; Bu nedenle, bir C# dizesinde herhangi bir sayıda gömülü null karakter (' \ 0 ') bulunabilir. <xref:System.String.Length%2A>Bir dizenin özelliği, `Char` Unicode karakter sayısını değil, içerdiği nesne sayısını temsil eder. Bir dizedeki tek tek Unicode kod noktalarına erişmek için <xref:System.Globalization.StringInfo> nesnesini kullanın.  
  
## <a name="string-vs-systemstring"></a>String ve System. String karşılaştırması  
 C# ' de, `string` anahtar sözcüğü için bir diğer addır <xref:System.String> . Bu nedenle, `String` ve `string` eşdeğerdir ve tercih ettiğiniz adlandırma kuralını kullanabilirsiniz. `String`Sınıfı dizeleri güvenli bir şekilde oluşturmak, işlemek ve karşılaştırmak için birçok yöntem sağlar. Ayrıca, C# dili yaygın dize işlemlerini basitleştirmek için bazı işleçleri aşırı yükler. Anahtar sözcüğü hakkında daha fazla bilgi için bkz. [String](../../language-reference/builtin-types/reference-types.md). Türü ve yöntemleri hakkında daha fazla bilgi için bkz <xref:System.String> ..  
  
## <a name="declaring-and-initializing-strings"></a>Dizeleri bildirme ve başlatma  
 Aşağıdaki örnekte gösterildiği gibi çeşitli yollarla dizeler bildirebilir ve başlatabilirsiniz:  
  
 [!code-csharp[csProgGuideStrings#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#1)]  
  
 Dizenin bir karakter dizisiyle başlatılması dışında bir dize nesnesi oluşturmak için [New](../../language-reference/operators/new-operator.md) işlecini kullanmayacağınızı unutmayın.  
  
 <xref:System.String.Empty>Dizesi sıfır uzunluklu olan yeni bir nesne oluşturmak için sabit değere sahip bir dize başlatın <xref:System.String> . Sıfır uzunluklu bir dizenin dize sabit temsili "" dir. Dizeleri <xref:System.String.Empty> [null](../../language-reference/keywords/null.md)yerine değeri ile başlatarak, oluşma olasılığını azaltabilirsiniz <xref:System.NullReferenceException> . <xref:System.String.IsNullOrEmpty%28System.String%29>Bir dizenin değerini erişmeyi denemeden önce doğrulamak için statik yöntemi kullanın.  
  
## <a name="immutability-of-string-objects"></a>Dize nesnelerinin kullanılabilirliği  
 Dize nesneleri *sabittir*: oluşturulduktan sonra değiştirilemez. <xref:System.String>Bir dizeyi değiştirmek için görünen tüm yöntemler ve C# işleçleri aslında sonuçları yeni bir dize nesnesi olarak döndürür. Aşağıdaki örnekte, içeriği `s1` ve `s2` tek bir dize oluşturacak şekilde bitiştirildiği zaman, iki özgün dize değiştirilmemiş olur. `+=`İşleci, Birleşik içerikleri içeren yeni bir dize oluşturur. Bu yeni nesne değişkenine atanır `s1` ve kendisine atanmış olan özgün nesne, `s1` başka hiçbir değişken buna başvuru içermediğinden çöp toplama için serbest bırakılır.  
  
 [!code-csharp[csProgGuideStrings#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#2)]  
  
 Bir "değişiklik" dizesi aslında yeni bir dize oluşturma olduğundan, dizelere başvurular oluştururken dikkatli olmanız gerekir. Bir dizeye başvuru oluşturursanız ve sonra özgün dizeyi "değiştirirseniz", başvuru, dize değiştirildiğinde oluşturulan yeni nesne yerine özgün nesneyi işaret etmeye devam edecektir. Aşağıdaki kod bu davranışı göstermektedir:  
  
 [!code-csharp[csProgGuideStrings#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#25)]  
  
 Özgün dizedeki arama ve değiştirme işlemleri gibi değişikliklere dayalı yeni dizeler oluşturma hakkında daha fazla bilgi için bkz. [dize içeriğini değiştirme](../../how-to/modify-string-contents.md).  
  
## <a name="regular-and-verbatim-string-literals"></a>Normal ve tam dize sabit değerleri  
 Aşağıdaki örnekte gösterildiği gibi C# tarafından verilen kaçış karakterlerini katıştırmanız gerektiğinde normal dize değişmez değerlerini kullanın:  
  
 [!code-csharp[csProgGuideStrings#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#3)]  
  
 Dize metninde, örneğin dosya yollarında ters eğik çizgi karakterleri içerdiğinde, kolay ve daha iyi okunabilirlik için tam dizeler kullanın. Harfine dizeler dize metninin bir parçası olarak yeni satır karakterlerini koruduğundan, çok satırlı dizeleri başlatmak için kullanılabilirler. Tam bir dizenin içine tırnak işareti eklemek için çift tırnak işaretleri kullanın. Aşağıdaki örnek, tam dizeler için bazı yaygın kullanımları göstermektedir:  
  
 [!code-csharp[csProgGuideStrings#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#4)]  
  
## <a name="string-escape-sequences"></a>Dize kaçış dizileri  
  
|Kaçış sırası|Karakter adı|Unicode kodlama|  
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
|\u|Unicode kaçış sırası (UTF-16)|`\uHHHH`(Aralık: 0000-FFFF; örnek: `\u00E7` = "ç")|  
|\U|Unicode kaçış sırası (UTF-32)|`\U00HHHHHH`(Range: 000000 yazın-10FFFF; örnek: `\U0001F47D` = "& # x1F47D;")|  
|\x|Değişken uzunluğu dışında, "\u" şuna benzer Unicode kaçış sırası|`\xH[H][H][H]`(Aralık: 0-FFFF; örnek: `\x00E7` or `\x0E7` veya `\xE7` = "ç")|  
  
> [!WARNING]
> `\x`Kaçış sırasını kullanırken ve 4 onaltılık basamak belirtirken, kaçış sırasını hemen izleyen karakterler geçerli onaltılı basamaklar (yani 0-9, a-f ve a-f), kaçış sırasının bir parçası olarak yorumlanır. Örneğin, `\xA1` kod noktası U + 00A1 olan "&#161;" üretir. Bununla birlikte, sonraki karakter "A" veya "a" ise, kaçış sırası bunun yerine kabul edilir `\xA1A` ve kod noktası U + 0A1A olan "&#x0A1A;" üretir. Bu gibi durumlarda, tüm 4 onaltılık basamakları (ör. `\x00A1` ) belirtmek olası hatalı yorumlamayı engeller.  
  
> [!NOTE]
> Derleme zamanında, tam dizeler aynı kaçış dizileri ile normal dizelere dönüştürülür. Bu nedenle, hata ayıklayıcı izleme penceresinde tam bir dizeyi görürseniz, kaynak kodunuzdaki tam sürümü değil, derleyici tarafından eklenen kaçış karakterlerini görürsünüz. Örneğin, tam dize `@"C:\files.txt"` izleme penceresinde "C: \\\files.txt" olarak görüntülenir.  
  
## <a name="format-strings"></a>Biçim Dizeleri  
 Biçim dizesi, içeriği çalışma zamanında dinamik olarak belirlenen bir dizedir. Biçim dizeleri, bir dize içindeki küme ayraçları içine *enterpolasyonlu ifadeler* veya yer tutucuları katıştırarak oluşturulur. Küme ayracı () içindeki her şey, `{...}` çalışma zamanında biçimli bir dize olarak bir değere ve çıkışa çözümlenir. Biçim dizeleri oluşturmak için iki yöntem vardır: dize ilişkilendirme ve bileşik biçimlendirme.

### <a name="string-interpolation"></a>Dize Ilişkilendirme
C# 6,0 ve üzeri sürümlerde, [*enterpolasyonlu dizeler*](../../language-reference/tokens/interpolated.md) `$` özel karakter tarafından tanımlanır ve küme ayraçları içine enterpolasyonlu ifadeler ekler. Dize ilişkilendirmeden yeni bir genel bakış için bkz. [String enterpolasyon-C# etkileşimli öğreticisi](../../tutorials/exploration/interpolated-strings.yml) .

Kodlarınızın okunabilirliğini ve bakımlılığını artırmak için dize ilişkilendirmeyi kullanın. Dize ilişkilendirme yöntemiyle aynı sonuçlara erişir `String.Format` , ancak kullanım kolaylığı ve satır içi açıklık geliştirir.

[!code-csharp[csProgGuideFormatStrings](~/samples/snippets/csharp/programming-guide/strings/Strings_1.cs#StringInterpolation)]

### <a name="composite-formatting"></a>Bileşik Biçimlendirme
<xref:System.String.Format%2A?displayProperty=nameWithType>Bir biçim dizesi oluşturmak için yer tutucuları, küme ayraçları içinde kullanır. Bu örnek, yukarıda kullanılan dize ilişkilendirme yöntemine benzer bir çıkışa neden olur.
  
[!code-csharp[csProgGuideFormatStrings](~/samples/snippets/csharp/programming-guide/strings/Strings_1.cs#StringFormat)]

.NET türlerini biçimlendirme hakkında daha fazla bilgi için bkz. [.net 'Teki biçimlendirme türleri](../../../standard/base-types/formatting-types.md).
  
## <a name="substrings"></a>Dizelerin  
 Alt dize, bir dizede yer alan herhangi bir karakter dizisidir. <xref:System.String.Substring%2A>Özgün dizenin bir bölümünden yeni bir dize oluşturmak için yöntemini kullanın. Yöntemini kullanarak bir alt dizenin bir veya daha fazla örneğini arayabilirsiniz <xref:System.String.IndexOf%2A> . <xref:System.String.Replace%2A>Belirtilen bir alt dizenin tüm oluşumlarını yeni bir dizeyle değiştirmek için yöntemini kullanın. Yöntemi gibi <xref:System.String.Substring%2A> , <xref:System.String.Replace%2A> aslında yeni bir dize döndürür ve özgün dizeyi değiştirmez. Daha fazla bilgi için bkz. [dizeleri arama](../../how-to/search-strings.md) ve [dize içeriğini değiştirme](../../how-to/modify-string-contents.md).
  
 [!code-csharp[csProgGuideStrings#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#7)]  
  
## <a name="accessing-individual-characters"></a>Ayrı karakterlere erişme  
 Aşağıdaki örnekte olduğu gibi tek tek karakterlere salt okuma erişimi elde etmek için dizi gösterimini bir dizin değeriyle birlikte kullanabilirsiniz:  
  
 [!code-csharp[csProgGuideStrings#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#8)]  
  
 <xref:System.String>Yöntemler bir dizedeki bağımsız karakterleri değiştirmek için sahip olmanız gereken işlevselliği sağlamıyorsa, <xref:System.Text.StringBuilder> tek tek karakterleri "yerinde" değiştirmek için bir nesne kullanabilir ve ardından yöntemleri kullanarak sonuçları depolamak için yeni bir dize oluşturabilirsiniz <xref:System.Text.StringBuilder> . Aşağıdaki örnekte, özgün dizeyi belirli bir şekilde değiştirmeniz ve ardından daha sonra kullanmak üzere sonuçları depolamanız gerektiğini varsayalım:  
  
 [!code-csharp[csProgGuideStrings#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#27)]  
  
## <a name="null-strings-and-empty-strings"></a>Null dizeler ve boş dizeler  
 Boş dize, <xref:System.String?displayProperty=nameWithType> sıfır karakter içeren bir nesne örneğidir. Boş dizeler, genellikle boş bir metin alanını göstermek için çeşitli programlama senaryolarında kullanılır. Nesneleri boş dizeler üzerinde çağırabilirsiniz, çünkü bunlar geçerli <xref:System.String?displayProperty=nameWithType> nesneler. Boş dizeler aşağıdaki şekilde başlatılır:  
  
```csharp  
string s = String.Empty;  
```  
  
 Buna karşılık, bir null dize bir nesnenin örneğine başvurmaz <xref:System.String?displayProperty=nameWithType> ve null dize üzerinde bir yöntemi çağırma girişimi bir öğesine neden olur <xref:System.NullReferenceException> . Ancak, birleştirme ve karşılaştırma işlemlerinde aynı dizeleri diğer dizelerle birlikte kullanabilirsiniz. Aşağıdaki örneklerde, bir null dize başvurusunun oluşturulduğu ve bir özel durumun oluşturulmasına neden olmadığı bazı durumlar gösterilmektedir:  
  
 [!code-csharp[csProgGuideStrings#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#20)]  
  
## <a name="using-stringbuilder-for-fast-string-creation"></a>Hızlı dize oluşturma için StringBuilder kullanma  
 .NET 'teki dize işlemleri yüksek oranda iyileştirilmiştir ve çoğu durumda performansı önemli ölçüde etkilemez. Ancak, çok sayıda yüzlerce veya binlerce kez yürütülen sıkı döngüler gibi bazı senaryolarda, dize işlemleri performansı etkileyebilir. Bu <xref:System.Text.StringBuilder> sınıf, programınız çok sayıda dize işlemeleri gerçekleştirdiğinde daha iyi performans sunan bir dize arabelleği oluşturur. <xref:System.Text.StringBuilder>Dize Ayrıca, yerleşik dize veri türünün desteklemediği bir şeyler olan tek tek karakterleri yeniden atayabilmenizi de sağlar. Bu kod, örneğin, yeni bir dize oluşturmadan bir dizenin içeriğini değiştirir:  
  
 [!code-csharp[csProgGuideStrings#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#15)]  
  
 Bu örnekte bir nesne, bir <xref:System.Text.StringBuilder> sayısal türler kümesinden dize oluşturmak için kullanılır:  
  
 [!code-csharp[TestStringBuilder#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/TestStringBuilder.cs)]
  
## <a name="strings-extension-methods-and-linq"></a>Dizeler, uzantı yöntemleri ve LINQ  
 <xref:System.String>Türü uyguladığından <xref:System.Collections.Generic.IEnumerable%601> , dizelerde sınıfında tanımlanan genişletme yöntemlerini kullanabilirsiniz <xref:System.Linq.Enumerable> . Görsel dağınıklığı önlemek için, bu yöntemler tür için IntelliSense 'den dışlanır <xref:System.String> , ancak yine de kullanılabilir. Ayrıca, dizeler üzerinde LINQ sorgu ifadeleri de kullanabilirsiniz. Daha fazla bilgi için bkz. [LINQ ve dizeler](../concepts/linq/linq-and-strings.md).  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Konu|Description|  
|-----------|-----------------|  
|[Dize içeriklerini değiştirme](../../how-to/modify-string-contents.md)|Dizeleri dönüştürme ve dizelerin içeriğini değiştirme tekniklerini gösterir.|  
|[Dizeleri karşılaştırma](../../how-to/compare-strings.md)|Dizelerin sıralı ve kültüre özgü karşılaştırmalarının nasıl gerçekleştirileceğini gösterir.|  
|[Birden çok dizeyi birleştirme](../../how-to/concatenate-multiple-strings.md)|Birden çok dizeyi tek tek birleştirmek için çeşitli yollar gösterir.|
|[String. Split kullanarak dizeleri ayrıştırma](../../how-to/parse-strings-using-split.md)|Dizeleri ayrıştırmak için yönteminin nasıl kullanılacağını gösteren kod örnekleri içerir `String.Split` .|  
|[Dizeleri arama](../../how-to/search-strings.md)|Dizelerde belirli metin veya desenler için aramanın nasıl kullanılacağını açıklar.|  
|[Bir dizenin sayısal bir değeri temsil edip etmediğini belirleme](./how-to-determine-whether-a-string-represents-a-numeric-value.md)|Geçerli bir sayısal değer olup olmadığını görmek için bir dizeyi güvenli bir şekilde ayrıştırmayı gösterir.|  
|[Dize ilişkilendirme](../../language-reference/tokens/interpolated.md)|Dizeleri biçimlendirmek için uygun bir sözdizimi sağlayan dize ilişkilendirme özelliğini açıklar.|
|[Temel dize Işlemleri](../../../standard/base-types/basic-string-operations.md)|<xref:System.String?displayProperty=nameWithType> <xref:System.Text.StringBuilder?displayProperty=nameWithType> Temel dize işlemleri gerçekleştirmek için ve yöntemlerini kullanan konulara bağlantılar sağlar.|  
|[Dizeleri Ayrıştırma](../../../standard/base-types/parsing-strings.md)|.NET temel türlerinin dize temsillerini karşılık gelen türlerin örneklerine nasıl dönüştüreceğiniz açıklanmıştır.|  
|[.NET 'teki tarih ve saat dizelerini ayrıştırma](../../../standard/base-types/parsing-datetime.md)|"01/24/2008" gibi bir dizenin bir nesneye nasıl dönüştürüleceğini gösterir <xref:System.DateTime?displayProperty=nameWithType> .|  
|[Dizeleri Karşılaştırma](../../../standard/base-types/comparing.md)|Dizelerin nasıl karşılaştırılacağı ve C# ve Visual Basic örnekler sağladığı hakkında bilgiler içerir.|  
|[StringBuilder Sınıfını Kullanma](../../../standard/base-types/stringbuilder.md)|Sınıfını kullanarak dinamik dize nesnelerinin nasıl oluşturulduğunu ve değiştirileceğini açıklar <xref:System.Text.StringBuilder> .|  
|[LINQ ve Dizeler](../concepts/linq/linq-and-strings.md)|LINQ sorguları kullanılarak çeşitli dize işlemlerinin nasıl gerçekleştirileceği hakkında bilgi sağlar.|  
|[C# Programlama Kılavuzu](../index.md)|C# dilinde programlama yapılarını açıklayan konuların bağlantılarını sağlar.|  
