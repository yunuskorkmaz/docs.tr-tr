---
title: Dizeleri - C# Programlama Kılavuzu
ms.date: 06/27/2019
helpviewer_keywords:
- C# language, strings
- strings [C#]
ms.assetid: 21580405-cb25-4541-89d5-037846a38b07
ms.openlocfilehash: dd76450c2a6a1726d630285f652d252c5f66183f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711915"
---
# <a name="strings-c-programming-guide"></a>Dizeler (C# Programlama Kılavuzu)
Dize, değeri metin <xref:System.String> olan bir tür nesnesidir. Dahili olarak, metin <xref:System.Char> nesnelerin sırayla salt okunur koleksiyonu olarak depolanır. C# dizesinin sonunda null-terminating karakter yoktur; bu nedenle bir C# dizesi herhangi bir sayıda katışılmış null karakter ('\0') içerebilir. Bir <xref:System.String.Length%2A> dize özelliği, Unicode karakter sayısını değil, içerdiği nesne sayısını `Char` temsil eder. Bir dizedeki tek tek Unicode kod <xref:System.Globalization.StringInfo> noktalarına erişmek için nesneyi kullanın.  
  
## <a name="string-vs-systemstring"></a>string vs System.String  
 C#'da `string` anahtar kelime <xref:System.String>. Bu `String` nedenle, ve `string` eşdeğerdir ve tercih hangi adlandırma kuralı kullanabilirsiniz. Sınıf, `String` dizeleri güvenli bir şekilde oluşturmak, işlemek ve karşılaştırmak için birçok yöntem sağlar. Buna ek olarak, C# dili ortak dize işlemlerini basitleştirmek için bazı işleçleri aşırı yükler. Anahtar kelime hakkında daha fazla bilgi için [string'e](../../language-reference/builtin-types/reference-types.md)bakın. Türü ve yöntemleri hakkında daha fazla <xref:System.String>bilgi için bkz.  
  
## <a name="declaring-and-initializing-strings"></a>Dizeleri Bildirme ve Başlatma  
 Dizeleri aşağıdaki örnekte gösterildiği gibi çeşitli şekillerde bildirebilir ve başolarak bildirebilirsiniz:  
  
 [!code-csharp[csProgGuideStrings#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#1)]  
  
 Dizeyi bir karakter dizisiyle başlatma dışında bir dize nesnesi oluşturmak için [yeni](../../language-reference/operators/new-operator.md) işleci kullanmadığınızı unutmayın.  
  
 Dize sıfır uzunlukta <xref:System.String.Empty> yeni bir <xref:System.String> nesne oluşturmak için sabit değeri olan bir dize başlatma. Sıfır uzunluktabir dize dize harfi harfi "" dir. Dizeleri null yerine <xref:System.String.Empty> değerle [null](../../language-reference/keywords/null.md)başlayarak, bir <xref:System.NullReferenceException> meydana olma olasılığını azaltabilirsiniz. Erişmeye <xref:System.String.IsNullOrEmpty%28System.String%29> çalışmadan önce bir dize değerini doğrulamak için statik yöntemi kullanın.  
  
## <a name="immutability-of-string-objects"></a>String Nesnelerinin Değişmezliği  
 String nesneleri *değişmez:* oluşturulduktan sonra değiştirilemezler. Bir dizeyi <xref:System.String> değiştirmek için görünen tüm yöntemler ve C# işleçleri aslında sonuçları yeni bir dize nesnesinde döndürür. Aşağıdaki örnekte, içeriği `s1` `s2` tek bir dize oluşturmak için bağlandığında, iki özgün dize değiştirilmemiştir. İşleç, `+=` birleştirilmiş içeriği içeren yeni bir dize oluşturur. Bu yeni nesne değişkene `s1`atanır ve atanan özgün `s1` nesne çöp toplama için serbest bırakılır, çünkü başka hiçbir değişken ona başvuruda bulunmaz.  
  
 [!code-csharp[csProgGuideStrings#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#2)]  
  
 Dize "değişiklik" aslında yeni bir dize oluşturma olduğundan, dizeleri başvurular oluştururken dikkatli kullanmanız gerekir. Bir dize için bir başvuru oluşturur ve özgün dizeyi "değiştirirseniz", başvuru dize değiştirildiğinde oluşturulan yeni nesne yerine özgün nesneyi işaret etmeye devam edecektir. Aşağıdaki kod bu davranışı göstermektedir:  
  
 [!code-csharp[csProgGuideStrings#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#25)]  
  
 Özgün dizedeki arama ve değiştirme işlemleri gibi değişikliklere dayanan yeni dizeleri nasıl oluşturabilirsiniz hakkında daha fazla bilgi için [dize içeriğini nasıl değiştirebilirsiniz'e](../../how-to/modify-string-contents.md)bakın.  
  
## <a name="regular-and-verbatim-string-literals"></a>Düzenli ve Verbatim String Literals  
 Aşağıdaki örnekte gösterildiği gibi, C# tarafından sağlanan kaçış karakterlerini gömmeniz gerektiğinde normal dize gerçeklerini kullanın:  
  
 [!code-csharp[csProgGuideStrings#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#3)]  
  
 Dize metni, örneğin dosya yollarında ters eğik çizgi karakterleri içeriyorsa kolaylık ve daha iyi okunabilirlik için tam olarak dizeleri kullanın. Verbatim dizeleri dize metninin bir parçası olarak yeni satır karakterleri korumak için, çok satırlı dizeleri baş harflerine almak için kullanılabilir. Bir tırnak işaretini harfi harfine dize katıştırmak için çift tırnak işaretlerini kullanın. Aşağıdaki örnek, harfi harfine dizeleri için bazı yaygın kullanımları gösterir:  
  
 [!code-csharp[csProgGuideStrings#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#4)]  
  
## <a name="string-escape-sequences"></a>String Kaçış Dizileri  
  
|Kaçış sırası|Karakter adı|Unicode kodlama|  
|---------------------|--------------------|----------------------|  
|\\'|Tek teklif|0x0027|  
|\\"|Çift teklif|0x0022|  
|\\\\ |Ters eğik çizgi|0x005C|  
|\0|Null|0x0000|  
|\a|Uyarı|0x0007|  
|\b|Geri Al tuşu|0x0008|  
|\f|Form akışı|0x000C|  
|\n|Yeni satır|0x000A|  
|\r|Satır başı|0x000D|  
|\t|Yatay sekme|0x0009|  
|\v|Dikey sekme|0x000B|  
|\u|Unicode kaçış sırası (UTF-16)|`\uHHHH`(aralık: 0000 - FFFF; örnek: `\u00E7` = "ç")|  
|\u|Unicode kaçış sırası (UTF-32)|`\U00HHHHHH`(aralık: 000000 - 10FFFF; örnek: `\U0001F47D` = "&#x1F47D;")|  
|\x|Değişken uzunluğu dışında "\u" benzeri unicode kaçış sırası|`\xH[H][H][H]`(aralık: 0 - FFFF; `\x0E7` `\xE7` örnek: `\x00E7` veya = "ç")|  
  
> [!WARNING]
> Kaçış sırasını `\x` kullanırken ve 4 hex'ten az rakam belirtirken, kaçış sırasını hemen izleyen karakterler geçerli hex basamakları ise (yani 0-9, A-F ve a-f) kaçış sırasının bir parçası olarak yorumlanır. Örneğin, `\xA1` U+00A1 kod noktası olan "&#161;" üretir. Ancak, bir sonraki karakter "A" veya "a" ise, kaçış sırası `\xA1A` bunun yerine olmak olarak yorumlanır ve kod noktası U+0A1A olan "&#x0A1A;" üretmek. Bu gibi durumlarda, 4 hex basamağının `\x00A1` tümlerinin (örn. ) belirtilmesi olası yanlış yorumlamayı önler.  
  
> [!NOTE]
> Derleme zamanında, tam anlamıyla dizeleri tüm aynı kaçış dizileri ile sıradan dizeleri dönüştürülür. Bu nedenle, hata ayıklama izleme penceresinde bir harfi harfini görürseniz, kaynak kodunuzdan tam olarak sürüm değil, derleyici tarafından eklenen kaçış karakterlerini görürsünüz. Örneğin, saat penceresinde "C: `@"C:\files.txt"` \\\files.txt" olarak görünür.  
  
## <a name="format-strings"></a>Biçim Dizeleri  
 Biçim dizesi, içeriği çalışma zamanında dinamik olarak belirlenen bir dizedir. Biçim dizeleri, *enterpolasyonlu ifadeleri* veya yer tutucuları bir dize içinde ayraçların içine katıştırarak oluşturulur. Ayraçların içindeki`{...}`her şey ( ) çalışma zamanında biçimlendirilmiş bir dize olarak bir değere ve çıktıya çözülür. Biçim dizeleri oluşturmak için iki yöntem vardır: dize enterpolasyonu ve bileşik biçimlendirme.

### <a name="string-interpolation"></a>String Enterpolasyonu
C# 6.0 ve daha sonra, [*enterpolasyonlu dizeleri*](../../language-reference/tokens/interpolated.md) `$` özel karakter tarafından tanımlanır ve parantez içinde enterpolasyonlu ifadeler içerir. Dize enterpolasyonunda yeniyseniz, hızlı bir genel bakış için [String enterpolasyonu - C# etkileşimli öğreticiye](../../tutorials/exploration/interpolated-strings.yml) bakın.

Kodunuzu okunabilirliğini ve korunabilirliğini artırmak için dize enterpolasyonunu kullanın. Dize enterpolasyonu `String.Format` yöntemle aynı sonuçları elde eder, ancak kullanım kolaylığını ve satır açıklığını artırır.

[!code-csharp[csProgGuideFormatStrings](~/samples/snippets/csharp/programming-guide/strings/Strings_1.cs#StringInterpolation)]

### <a name="composite-formatting"></a>Bileşik Biçimlendirme
Biçim <xref:System.String.Format%2A?displayProperty=nameWithType> dizesi oluşturmak için parantez içinde yer tutucuları kullanır. Bu örnek, yukarıda kullanılan dize enterpolasyon yöntemine benzer çıktı ile sonuçlanır.
  
[!code-csharp[csProgGuideFormatStrings](~/samples/snippets/csharp/programming-guide/strings/Strings_1.cs#StringFormat)]

Biçimlendirme .NET türleri hakkında daha fazla bilgi için [.NET'teki Biçimlendirme Türleri'ne](../../../standard/base-types/formatting-types.md)bakın.
  
## <a name="substrings"></a>Alt dizeleri  
 Alt dize, bir dize içinde bulunan herhangi bir karakter dizisidir. Özgün <xref:System.String.Substring%2A> dize parçasından yeni bir dize oluşturmak için yöntemi kullanın. <xref:System.String.IndexOf%2A> Yöntemi kullanarak bir alt dize bir veya daha fazla oluşumları arayabilirsiniz. Belirtilen <xref:System.String.Replace%2A> bir alt dizeğin tüm oluşumlarını yeni bir dizeyle değiştirmek için yöntemi kullanın. <xref:System.String.Substring%2A> Yöntem gibi, <xref:System.String.Replace%2A> aslında yeni bir dize döndürür ve özgün dize değiştirmez. Daha fazla bilgi için [dizeleri nasıl arayacağını](../../how-to/search-strings.md) ve [dize içeriğini nasıl değiştirin'](../../how-to/modify-string-contents.md)e bakın.
  
 [!code-csharp[csProgGuideStrings#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#9)]  
  
## <a name="accessing-individual-characters"></a>Tek tek Karakterlere Erişim  
 Aşağıdaki örnekte olduğu gibi, tek tek karakterlere salt okunur erişim elde etmek için dizin değeri olan dizi gösterimini kullanabilirsiniz:  
  
 [!code-csharp[csProgGuideStrings#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#8)]  
  
 <xref:System.String> Yöntemler bir dizedeki tek tek karakterleri değiştirmeniz gereken işlevselliği sağlamıyorsa, <xref:System.Text.StringBuilder> tek tek karakter "yerinde" değiştirmek için bir nesne kullanabilir ve ardından <xref:System.Text.StringBuilder> yöntemleri kullanarak sonuçları depolamak için yeni bir dize oluşturabilirsiniz. Aşağıdaki örnekte, özgün dizeyi belirli bir şekilde değiştirmeniz ve sonra sonuçları ileride kullanmak üzere depolamanız gerektiğini varsayalım:  
  
 [!code-csharp[csProgGuideStrings#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#27)]  
  
## <a name="null-strings-and-empty-strings"></a>Null Dizeleri ve Boş Dizeleri  
 Boş bir dize sıfır <xref:System.String?displayProperty=nameWithType> karakter içeren bir nesneörneğidir. Boş dizeleri boş bir metin alanını temsil etmek için çeşitli programlama senaryolarında sık sık kullanılır. Geçerli <xref:System.String?displayProperty=nameWithType> nesneler oldukları için boş dizelerdeki yöntemleri çağırabilirsiniz. Boş dizeleri aşağıdaki gibi başharfle karşılanır:  
  
```csharp  
string s = String.Empty;  
```  
  
 Buna karşılık, null dize bir <xref:System.String?displayProperty=nameWithType> nesnenin bir örnek anlamına gelmez ve null dize üzerinde bir yöntem çağırmak için herhangi bir girişim neden olur <xref:System.NullReferenceException>. Ancak, diğer dizeleri ile birlikte leştirme ve karşılaştırma işlemleri null dizeleri kullanabilirsiniz. Aşağıdaki örnekler, null dize için bir başvuru yok ve bir özel durum atılmasına neden olmaz bazı durumlarda göstermektedir:  
  
 [!code-csharp[csProgGuideStrings#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#20)]  
  
## <a name="using-stringbuilder-for-fast-string-creation"></a>Hızlı String Oluşturma için StringBuilder kullanma  
 .NET'teki string işlemleri son derece iyi leştirilmiştir ve çoğu durumda performansı önemli ölçüde etkilemez. Ancak, yüzlerce veya binlerce kez çalıştırıyorum sıkı döngüler gibi bazı senaryolarda, dize işlemleri performansı etkileyebilir. Programınız çok sayıda dize işlemesi gerçekleştirirse, <xref:System.Text.StringBuilder> sınıf daha iyi performans sunan bir dize arabelleği oluşturur. Dize, <xref:System.Text.StringBuilder> yerleşik dize veri türünün desteklemediği tek tek karakterleri yeniden atamanızı da sağlar. Bu kod, örneğin, yeni bir dize oluşturmadan bir dize içeriğini değiştirir:  
  
 [!code-csharp[csProgGuideStrings#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#15)]  
  
 Bu örnekte, <xref:System.Text.StringBuilder> bir nesne sayısal türleri kümesinden bir dize oluşturmak için kullanılır:  
  
 [!code-csharp[TestStringBuilder#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/TestStringBuilder.cs)]
  
## <a name="strings-extension-methods-and-linq"></a>Dizeleri, Uzatma Yöntemleri ve LINQ  
 Tür <xref:System.String> <xref:System.Collections.Generic.IEnumerable%601>uygulandığından, <xref:System.Linq.Enumerable> dizeleri üzerinde sınıfta tanımlanan uzantı yöntemlerik kullanabilirsiniz. Görsel yığılmayı önlemek için, bu yöntemler <xref:System.String> türü için IntelliSense hariç, ancak yine de kullanılabilir. Dizeleri linq sorgu ifadeleri de kullanabilirsiniz. Daha fazla bilgi için [LINQ ve Strings'e](../concepts/linq/linq-and-strings.md)bakın.  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Konu başlığı|Açıklama|  
|-----------|-----------------|  
|[Dize içeriklerini değiştirme](../../how-to/modify-string-contents.md)|Dizeleri dönüştürme ve dizelerin içeriğini değiştirme tekniklerini gösterir.|  
|[Dizeleri karşılaştırmak için nasıl](../../how-to/compare-strings.md)|Dizelerin ordinal ve kültüre özgü karşılaştırmalarının nasıl yapılacağını gösterir.|  
|[Birden çok dize nasıl işlenir?](../../how-to/concatenate-multiple-strings.md)|Birden çok dizeleri tek bir dizeleri birleştirmek için çeşitli yollar gösterir.|
|[String.Split kullanarak dizeleri ayrışdırmak için nasıl](../../how-to/parse-strings-using-split.md)|Dizeleri ayrışdırmak için `String.Split` yöntemin nasıl kullanılacağını gösteren kod örnekleri içerir.|  
|[Dizeleri arama](../../how-to/search-strings.md)|Dizelerdeki belirli metin veya desenleriçin aramanın nasıl kullanılacağını açıklar.|  
|[Bir dizenin sayısal bir değeri temsil edip etmediğini belirleme](./how-to-determine-whether-a-string-represents-a-numeric-value.md)|Geçerli bir sayısal değere sahip olup olmadığını görmek için bir dizeyi güvenli bir şekilde ayrıştırmayı gösterir.|  
|[Dize ilişkilendirme](../../language-reference/tokens/interpolated.md)|Dizeleri biçimlendirmek için kullanışlı bir sözdizimi sağlayan dize enterpolasyon özelliğini açıklar.|
|[Temel Dize İşlemleri](../../../standard/base-types/basic-string-operations.md)|Temel dize işlemlerini <xref:System.String?displayProperty=nameWithType> <xref:System.Text.StringBuilder?displayProperty=nameWithType> gerçekleştirmek için kullanılan konulara ve yöntemlere bağlantılar sağlar.|  
|[Dizeleri Ayrıştırma](../../../standard/base-types/parsing-strings.md)|.NET taban türlerinin dize gösterimlerinin karşılık gelen türlerin örneklerine nasıl dönüştürülür olduğunu açıklar.|  
|[Tarih ve Saat Dizelerini .NET'te ayrıştama](../../../standard/base-types/parsing-datetime.md)|"24/01/2008" gibi bir dize yi <xref:System.DateTime?displayProperty=nameWithType> bir nesneye nasıl dönüştüreceklerini gösterir.|  
|[Dizeleri Karşılaştırma](../../../standard/base-types/comparing.md)|Dizeleri karşılaştırmak hakkında bilgi içerir ve C# ve Visual Basic'te örnekler sağlar.|  
|[StringBuilder Sınıfını Kullanma](../../../standard/base-types/stringbuilder.md)|Sınıfı kullanarak dinamik dize nesnelerinin nasıl <xref:System.Text.StringBuilder> oluşturulup değiştirilebildiğini açıklar.|  
|[LINQ ve Dizeler](../concepts/linq/linq-and-strings.md)|LINQ sorgularını kullanarak çeşitli dize işlemlerinin nasıl gerçekleştirilebildiğini hakkında bilgi sağlar.|  
|[C# Programlama Kılavuzu](../index.md)|C#'da programlama yapılarını açıklayan konulara bağlantılar sağlar.|  
