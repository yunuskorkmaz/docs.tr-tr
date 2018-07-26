---
title: Dizeler (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, strings
- strings [C#]
ms.assetid: 21580405-cb25-4541-89d5-037846a38b07
ms.openlocfilehash: 9b108a1613e01016c541d088612303c6aaa13629
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37961475"
---
# <a name="strings-c-programming-guide"></a>Dizeler (C# Programlama Kılavuzu)
Türünde bir nesne bir dizedir <xref:System.String> metin değeri olan. Metin sıralı salt okunur bir koleksiyonu dahili olarak depolanan <xref:System.Char> nesneleri. Bir C# dizenin sonuna kadar hiçbir null Sonlandırıcı karakter yoktur; Bu nedenle bir C# dize herhangi bir sayıda gömülü null karakterleri ('\0') içerebilir. <xref:System.String.Length%2A> Bir dize özelliğini sayısını temsil eden `Char` içerdiği, Unicode karakter sayısını nesneleri. Bir dizedeki tek Unicode kod noktaları erişmek için <xref:System.Globalization.StringInfo> nesne.  
  
## <a name="string-vs-systemstring"></a>VS dize. System.String  
 C# ' ta, `string` anahtar sözcüğü, bir diğer ad için <xref:System.String>. Bu nedenle, `String` ve `string` eşdeğerdir ve tercih ettiğiniz herhangi bir adlandırma kuralını kullanabilirsiniz. `String` Sınıfı, güvenli bir şekilde oluşturma, düzenleme ve dizeleri karşılaştırmak için birçok yöntem sağlar. Ayrıca, C# dili, yaygın dize işlemleri basitleştirmek için bazı işleçleri aşırı yüklemeleri. Anahtar sözcüğü hakkında daha fazla bilgi için bkz: [dize](../../../csharp/language-reference/keywords/string.md). Tür ve yöntemlerini hakkında daha fazla bilgi için bkz. <xref:System.String>.  
  
## <a name="declaring-and-initializing-strings"></a>Bildirme ve başlatma dizeleri  
 Bildirebilir ve aşağıdaki örnekte gösterildiği gibi çeşitli şekillerde dizeleri Başlat:  
  
 [!code-csharp[csProgGuideStrings#1](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_1.cs)]  
  
 Seçeneğini kullanmaz Not [yeni](../../../csharp/language-reference/keywords/new-operator.md) işleci, bir dizi karakter dizesiyle başlatma dışında bir dize nesnesi oluşturmak için.  
  
 Bir dizeyle başlatmak <xref:System.String.Empty> yeni bir sabit değer <xref:System.String> nesnesi, dize uzunluğu sıfır. Dize değişmez değer gösterimiyse sıfır uzunlukta bir dize, "". Başlatma dizeleri ile tarafından <xref:System.String.Empty> değeri yerine [null](../../../csharp/language-reference/keywords/null.md), olasılığını azaltmak bir <xref:System.NullReferenceException> gerçekleşiyor. Statik <xref:System.String.IsNullOrEmpty%28System.String%29> yeniden erişmeye çalışmadan önce bir dize değerini doğrulamak için yöntem.  
  
## <a name="immutability-of-string-objects"></a>Dize nesnesi değiştirilemezlik  
 Dize nesneler *değişmez*: oluşturulduktan sonra bunlarda değişiklik yapılamaz. Tüm <xref:System.String> yöntemleri ve bir dize değiştirmek için görüntülenen C# işleçleri gerçekten sonuçları döndürür içinde yeni bir dize nesnesi. Aşağıdaki örnekte, zaman içeriğini `s1` ve `s2` birleştirilmiş tek bir dize oluşturmak için iki özgün değiştirilmemiş dizelerdir. `+=` İşleci birleşik içeriği içeren yeni bir dize oluşturur. Yeni nesne değişkenine atanır `s1`ve atandı özgün nesneye `s1` başka bir değişken buna bir başvuru bulunduğundan, çöp toplama için yayımlanır.  
  
 [!code-csharp[csProgGuideStrings#2](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_2.cs)]  
  
 Bir dize "değişiklik" yeni bir dize oluşturma gerçekten olduğundan, dizeleri başvuruları oluşturduğunuzda dikkatli kullanmanız gerekir. Bir dize başvuru oluşturun ve ardından orijinal dizeyi "değiştirme", başvuru dize değiştirildiğinde oluşturan yeni bir nesne yerine özgün nesneye işaret edecek şekilde devam eder. Aşağıdaki kod bu davranış gösterir:  
  
 [!code-csharp[csProgGuideStrings#25](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_3.cs)]  
  
 Arama gibi değişiklikler temel alır ve özgün dize işlemleri yerine yeni dizeler oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: dize içeriklerini değiştirme](../../how-to/modify-string-contents.md).  
  
## <a name="regular-and-verbatim-string-literals"></a>Normal ve Verbatim dize değişmez değerleri  
 Normal dize değişmez değerleri kullanarak aşağıdaki örnekte gösterildiği gibi C# tarafından sağlanan bir kaçış karakterleri katıştırmanız gerekir:  
  
 [!code-csharp[csProgGuideStrings#3](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_4.cs)]  
  
 Dizesi metnini ters eğik çizgi karakterleri, örneğin dosya yolları içerdiğinde harfi harfine dizeler kolaylık ve daha iyi okunabilirlik için kullanın. Harfi harfine dizeler dize metnin bir parçası olarak yeni satır karakterleri korumak için çok satırlı dize başlatmak için kullanılabilir. Verbatim dizesi içinde bir tırnak işareti eklemek için çift tırnak işaretleri kullanın. Aşağıdaki örnek, bazı yaygın kullanımları harfi harfine dizeler için gösterir:  
  
 [!code-csharp[csProgGuideStrings#4](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_5.cs)]  
  
## <a name="string-escape-sequences"></a>Dize kaçış dizileri  
  
|Kaçış sırası|Karakter adı|Unicode kodlama|  
|---------------------|--------------------|----------------------|  
|\\'|tek tırnak|0x0027|  
|\\"|çift tırnak işareti|0x0022|  
|\\\\ |Ters eğik çizgi|0x005C|  
|\0|Null|0x0000|  
|\a|Uyarı|0x0007|  
|\b|Geri Al tuşu|0x0008|  
|\f|form besleme|0x000C|  
|\n|Yeni satır|0x000A|  
|\r|satır başı|0x000D|  
|\t|Yatay sekme|0x0009|  
|\U|Unicode çıkış dizisi vekil çiftleri için.|\Unnnnnnnn|  
|\u|Unicode çıkış dizisi|\u0041 = "A"|  
|\v|dikey sekme|0x000B|  
|\x|Unicode çıkış dizisi değişken uzunluğu dışında "\u" benzer.|\x0041 = "A"|  
  
> [!NOTE]
>  Derleme zamanında harfi harfine dizeler sıradan dizelerle aynı kaçış dizileri dönüştürülür. Bu nedenle, hata ayıklayıcı İzleme penceresinde verbatim dizesi görüntülerseniz, kaynak kodunuzdan verbatim sürümünü değil derleyici tarafından eklenmiş kaçış karakterleri görürsünüz. Örneğin, verbatim dizesi @"C:\files.txt" İzleme penceresinde görünür "C:\\\files.txt".  
  
## <a name="format-strings"></a>Biçim dizeleri  
 Bir biçim dizesi, içerikleri, çalışma zamanında dinamik olarak belirlenebilir bir dizedir. Statik kullanarak bir biçim dizesi oluşturmak <xref:System.String.Format%2A> yöntemi ve diğer değerleri çalışma zamanında değiştirilecek olan ayraç içindeki yer tutucuları ekleme. Aşağıdaki örnek, her bir döngü yinelemesi sonucunun çıktısını almak için bir biçim dizesi kullanır:  
  
 [!code-csharp[csProgGuideStrings#26](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_6.cs)]  
  
 Bir aşırı yüklemesini <xref:System.Console.WriteLine%2A> yöntemi bir biçim dizesi bir parametre olarak alır. Bu nedenle, yalnızca bir biçim dizesi olmadan açık bir yöntemin çağrı değişmez değer ekleyebilirsiniz. Ancak, kullanırsanız <xref:System.Diagnostics.Trace.WriteLine%2A> Visual Studio'da hata ayıklama çıkışını görüntülemek için yöntemi **çıkış** penceresinde sahip açıkça çağırmak <xref:System.String.Format%2A> yöntemi olduğundan <xref:System.Diagnostics.Trace.WriteLine%2A> yalnızca biçim dizesi bir dize kabul eder. Biçim dizeleri hakkında daha fazla bilgi için bkz. [biçimlendirme türleri](../../../standard/base-types/formatting-types.md).  
  
## <a name="substrings"></a>Alt dizeler  
 Bir alt dizenin bir dizede bulunan bir karakter dizisidir. Kullanım <xref:System.String.Substring%2A> özgün dizeye bir bölümünden yeni bir dize oluşturmak için yöntemi. Kullanarak bir alt dizenin bir veya daha çok tekrarı için arama yapabilirsiniz <xref:System.String.IndexOf%2A> yöntemi. Kullanım <xref:System.String.Replace%2A> yöntemi belirtilen bir alt dizenin tüm oluşumlarını yeni bir dize ile değiştirin. Gibi <xref:System.String.Substring%2A> yöntemi <xref:System.String.Replace%2A> gerçekten yeni bir dize döndürür ve özgün dizeye değiştirmez. Daha fazla bilgi için [nasıl yapılır: dizeleri arama](../../how-to/search-strings.md) ve [nasıl yapılır: dize içeriklerini değiştirme](../../how-to/modify-string-contents.md).  
  
 [!code-csharp[csProgGuideStrings#7](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_7.cs)]  
  
## <a name="accessing-individual-characters"></a>Karakterlerin tek tek erişme  
 Aşağıdaki örnekte olduğu gibi tek karakterleri salt okunur erişim kazanmak için bir dizin değeri ile dizi gösterimini kullanın:  
  
 [!code-csharp[csProgGuideStrings#9](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_8.cs)]  
  
 Varsa <xref:System.String> yöntemi bir dizedeki karakterlerin tek tek değiştirmek zorunda olan işlevleri sağlamaz kullanabileceğiniz bir <xref:System.Text.StringBuilder> tek karakter "yerinde" değiştirmek için nesne ve ardından kullanarak sonuçlarını depolamak için yeni bir dize oluşturma <xref:System.Text.StringBuilder> yöntemleri. Aşağıdaki örnekte, orijinal dizeyi belirli bir şekilde değiştirin ve sonra sonuçları gelecekte kullanım için depolamak varsayın:  
  
 [!code-csharp[csProgGuideStrings#8](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_9.cs)]  
  
## <a name="null-strings-and-empty-strings"></a>Null dizeler ve boş dizeler  
 Boş bir dize örneği olan bir <xref:System.String?displayProperty=nameWithType> sıfır karakter içeren nesne. Boş dizeler genellikle boş metin alanını temsil etmek için çeşitli programlama senaryolarında kullanılır. Geçerli olduğundan boş dizeleri yöntemleri çağırabilir <xref:System.String?displayProperty=nameWithType> nesneleri. Boş dizeler gibi başlatılır:  
  
```  
string s = String.Empty;  
```  
  
 Bunun aksine, boş bir dize örneğine başvurmayan bir <xref:System.String?displayProperty=nameWithType> nesnesi ve her türlü girişim neden boş bir dize üzerinde bir yöntemi çağırmak için bir <xref:System.NullReferenceException>. Ancak, diğer dizelerle null dizeler birleştirme ve karşılaştırma işlemleri kullanabilirsiniz. Aşağıdaki örnekler, boş bir dize için bir başvuru yapar ve bir özel durum oluşturulmasına neden olmaz, bazı durumlarda gösterir:  
  
 [!code-csharp[csProgGuideStrings#27](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_10.cs)]  
  
## <a name="using-stringbuilder-for-fast-string-creation"></a>StringBuilder kullanarak dize hızlı oluşturmak için  
 . NET'te dize işlemleri, son derece iyileştirilmiştir ve çoğu durumda performansı önemli ölçüde etkilemez. Ancak, yüzlerce veya binlerce kez yürütülen sıkı döngüler gibi bazı senaryolarda, dize işlemlerinin performansını etkileyebilir. <xref:System.Text.StringBuilder> Programınızı birçok dize işlemeleri uyguluyorsa, daha iyi performans sunan bir dize arabelleğine sınıfı oluşturur. <xref:System.Text.StringBuilder> Dize de tanır karakterlerin tek tek bir şey yeniden atamak için yerleşik dize veri türünü desteklemiyor. Bu kod, örneğin, bir dizenin içeriği yeni bir dize oluşturmadan değiştirir:  
  
 [!code-csharp[csProgGuideStrings#20](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_11.cs)]  
  
 Bu örnekte, bir <xref:System.Text.StringBuilder> nesnesi, bir dize, sayısal türlerin kümesinden oluşturmak için kullanılır:  
  
 [!code-csharp[csProgGuideStrings#15](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_12.cs)]  
  
## <a name="strings-extension-methods-and-linq"></a>Dizeleri, genişletme yöntemleri ve LINQ  
 Çünkü <xref:System.String> yazın uygular <xref:System.Collections.Generic.IEnumerable%601>, tanımlanan genişletme yöntemleri kullanabilirsiniz <xref:System.Linq.Enumerable> dizelerde sınıfı. Görsel dağınıklığını önlemek için bu yöntemleri için IntelliSense edilmeyen <xref:System.String> türü, ancak kullanılabilir ancak yine de. Ayrıca [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu ifadelerinde dizeler. Daha fazla bilgi için [LINQ ve dizeler](../../../csharp/programming-guide/concepts/linq/linq-and-strings.md).  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Konu|Açıklama|  
|-----------|-----------------|  
|[Nasıl yapılır: Dize İçeriklerini Değiştirme](../../how-to/modify-string-contents.md)|Dizeleri dönüştürme ve dize içeriklerini değiştirme teknikleri gösterir.|  
|[Nasıl yapılır: Dizeleri Karşılaştırma](../../how-to/compare-strings.md)|Dizeler belirli karşılaştırmalar kültüre ve sıralı gerçekleştirmek nasıl gösterir.|  
|[Nasıl yapılır: Birden Çok Dizeyi Birleştirme](../../how-to/concatenate-multiple-strings.md)|Bir alana birden çok dizeyi birleştirme için çeşitli yollar gösterir.|
|[Nasıl yapılır: String.Split kullanarak dizeleri ayrıştırma ](../../how-to/parse-strings-using-split.md)|Nasıl kullanılacağını örneklendiren kod örnekleri içeren `String.Split` dizelerini ayrıştırmak için yöntemi.|  
|[Nasıl yapılır: dizeleri arama](../../how-to/search-strings.md)|Dizelerde arama belirli bir metin veya düzenleri için kullanmayı açıklar.|  
|[Nasıl yapılır: Bir Dizenin Sayısal bir Değeri Temsil Edip Etmediğini Belirleme](../../../csharp/programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)|Güvenli bir şekilde geçerli bir sayısal değer olup olmadığını görmek için bir dizeyi ayrıştırma işlemi gösterilmektedir.|  
|[Dize ilişkilendirme](../../language-reference/tokens/interpolated.md)|Biçim dizelerine bir sözdizimindeki sağlayan dize ilişkilendirme özelliğini açıklar.|
|[Temel Dize İşlemleri](../../../../docs/standard/base-types/basic-string-operations.md)|Kullanan konulara bağlantılar sağlar <xref:System.String?displayProperty=nameWithType> ve <xref:System.Text.StringBuilder?displayProperty=nameWithType> temel dize işlemleri gerçekleştirmek için yöntemleri.|  
|[Dizeleri Ayrıştırma](../../../standard/base-types/parsing-strings.md)|Temel türler .NET dize temsillerini türleri ve karşılık gelen örneklerine dönüştürüleceğini açıklar.|  
|[Tarih ve saat dizelerini .NET ayrıştırma](../../../standard/base-types/parsing-datetime.md)|"01/24/2008" gibi bir dizenin nasıl dönüştürüleceğini gösterir bir <xref:System.DateTime?displayProperty=nameWithType> nesne.|  
|[Dizeleri Karşılaştırma](../../../../docs/standard/base-types/comparing.md)|Dizeleri karşılaştırma hakkında bilgiler içerir ve C# ve Visual Basic örnekleri sağlar.|  
|[StringBuilder Sınıfını Kullanma](../../../standard/base-types/stringbuilder.md)|Oluşturma ve kullanarak dinamik dize nesneleri değiştirme işlemini açıklamaktadır <xref:System.Text.StringBuilder> sınıfı.|  
|[LINQ ve Dizeler](../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)|LINQ sorgularını kullanarak çeşitli dize işlemlerini gerçekleştirme hakkında bilgi sağlar.|  
|[C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)|C# programlama yapıları açıklayan konulara bağlantılar sağlar.|  
