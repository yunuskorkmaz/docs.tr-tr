---
title: Dizeler (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, strings
- strings [C#]
ms.assetid: 21580405-cb25-4541-89d5-037846a38b07
ms.openlocfilehash: 9b108a1613e01016c541d088612303c6aaa13629
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33337200"
---
# <a name="strings-c-programming-guide"></a>Dizeler (C# Programlama Kılavuzu)
Türünde bir nesne bir dizedir <xref:System.String> değeri metindir. Metin sıralı salt okunur bir koleksiyonu dahili olarak depolanan <xref:System.Char> nesneleri. Bir C# dizesi sonunda hiçbir null sonlandırma karakter yoktur; Bu nedenle bir C# dize herhangi bir sayıda katıştırılmış boş karakterler ('\0') içerebilir. <xref:System.String.Length%2A> Bir dize özelliği sayısını temsil eden `Char` içerdiği, Unicode karakter sayısını değil nesneleri. Bir dizede tek tek Unicode kod noktaları erişmek için <xref:System.Globalization.StringInfo> nesnesi.  
  
## <a name="string-vs-systemstring"></a>dize karşılaştırması System.String  
 C# ' ta, `string` sözcüktür için diğer ad <xref:System.String>. Bu nedenle, `String` ve `string` eşdeğerdir ve tercih ettiğiniz hangi adlandırma kuralını kullanabilirsiniz. `String` Sınıfı güvenle oluşturma, düzenleme ve dizeleri karşılaştırma için birçok yöntem sağlar. Ayrıca, C# dili ortak dize işlemleri basitleştirmek için bazı işleçleri aşırı yüklemeler. Anahtar sözcük hakkında daha fazla bilgi için bkz: [dize](../../../csharp/language-reference/keywords/string.md). Türü ve onun yöntemleri hakkında daha fazla bilgi için bkz: <xref:System.String>.  
  
## <a name="declaring-and-initializing-strings"></a>Bildirme ve başlatma dizeleri  
 Bildirme ve aşağıdaki örnekte gösterildiği gibi çeşitli şekillerde dizeleri başlatılamadı:  
  
 [!code-csharp[csProgGuideStrings#1](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_1.cs)]  
  
 Kullanmaz Not [yeni](../../../csharp/language-reference/keywords/new-operator.md) bir dizi karakter dizesiyle başlatma zaman dışında bir dize nesnesi oluşturmak için işleç.  
  
 Bir dizeyle başlatma <xref:System.String.Empty> yeni bir sabit değer <xref:System.String> nesnesi, dize sıfır uzunluğunda. Dize değişmez değer sıfır uzunlukta bir dize gösterimidir "". Başlatma dizeleri ile tarafından <xref:System.String.Empty> değeri yerine [null](../../../csharp/language-reference/keywords/null.md), olasılığını azaltmak bir <xref:System.NullReferenceException> gerçekleşen. Statik kullanmak <xref:System.String.IsNullOrEmpty%28System.String%29> erişmeye çalışmadan önce bir dize değerini doğrulamak için yöntem.  
  
## <a name="immutability-of-string-objects"></a>Dize nesnelerini girişi  
 Dize nesneler *değişmez*: oluşturulduktan sonra bunlar değiştirilemez. Tüm <xref:System.String> yöntemleri ve bir dize değiştirmek için görünen C# işleçleri gerçekte sonuçları döndürür yeni bir dize nesnesi. Aşağıdaki örnekte, zaman içeriğini `s1` ve `s2` birleşir tek bir dize oluşturmak için iki özgün değiştirilmemiş dizelerdir. `+=` İşleci birleşik içeriği içeren yeni bir dize oluşturur. Bu yeni nesne değişkenine atanan `s1`ve atandığı özgün nesne `s1` başka bir değişken buna başvuruda bulunduğundan atık toplama için yayımlanır.  
  
 [!code-csharp[csProgGuideStrings#2](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_2.cs)]  
  
 Bir dize "değiştirme" yeni bir dize oluşturma gerçekte olduğundan dizelerine yapılan başvuruları oluştururken dikkat kullanmanız gerekir. Bir dize başvuru oluşturmak ve ardından özgün dizeye "Değiştir", başvuru dize değiştirildiğinde, oluşturulan yeni nesne yerine özgün nesne işaret edecek şekilde devam eder. Aşağıdaki kod bu davranış gösterir:  
  
 [!code-csharp[csProgGuideStrings#25](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_3.cs)]  
  
 Arama gibi değişiklikler temel alır ve değiştirme işlemlerini özgün dizeye yeni dizeler oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: dize içeriklerini değiştirme](../../how-to/modify-string-contents.md).  
  
## <a name="regular-and-verbatim-string-literals"></a>Normal ve Verbatim dize değişmez değerleri  
 Aşağıdaki örnekte gösterildiği gibi C# tarafından sağlanan kaçış karakterleri katıştır gerekir normal dize değişmez değerleri kullanın:  
  
 [!code-csharp[csProgGuideStrings#3](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_4.cs)]  
  
 Dize metin ters eğik çizgi karakterleri, örneğin dosya yolları içerdiğinde harfi harfine dizeler kolaylık sağlamak ve okunabilirliği için kullanın. Harfi harfine dizeler yeni satır karakterlerini dizesi metni bir parçası olarak korumak için çok satırlı dizeleri başlatmak için kullanılabilir. Tırnak işareti verbatim dizesi içinde katıştırmak için çift tırnak işaretleri kullanın. Aşağıdaki örnek, bazı yaygın kullanımları verbatim dizelerini gösterir:  
  
 [!code-csharp[csProgGuideStrings#4](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_5.cs)]  
  
## <a name="string-escape-sequences"></a>Dize kaçış dizileri  
  
|Kaçış sırası|Karakter adı|Unicode kodlama|  
|---------------------|--------------------|----------------------|  
|\\'|tek tırnak işareti|0x0027|  
|\\"|çift tırnak işareti|0x0022|  
|\\\\ |ters eğik çizgi|0x005C|  
|\0|Null|0x0000|  
|\a|Uyarı|0x0007|  
|\b|Geri Al tuşu|0x0008|  
|\f|sonraki sayfaya geçme|0x000C|  
|\n|Yeni satır|0x000A|  
|\r|satır başı|0x000D|  
|\t|Yatay sekme|0x0009|  
|\U|Yedek çiftleri için Unicode kaçış sırası.|\Unnnnnnnn|  
|\u|Unicode kaçış sırası|\u0041 = "A"|  
|\v|Dikey sekme|0x000B|  
|\x|Unicode kaçış sırası değişken uzunlukta dışında "\u" benzer.|\x0041 = "A"|  
  
> [!NOTE]
>  Derleme zamanında harfi harfine dizeler sıradan dizelerle hepsi aynı kaçış sıraları dönüştürülür. Bu nedenle, hata ayıklayıcı Gözcü penceresinde verbatim dize görünümdeyse, kaynak kodu değil verbatim sürümünden derleyici tarafından eklenen kaçış karakterleri görürsünüz. Örneğin, verbatim dize @"C:\files.txt" Gözcü penceresi görünür "C:\\\files.txt".  
  
## <a name="format-strings"></a>Biçim dizeleri  
 Bir biçim dizesi içerikleri çalışma zamanında dinamik olarak belirlenebilir bir dizedir. Statik kullanarak bir biçim dizesi oluşturmak <xref:System.String.Format%2A> yöntemi ve çalışma zamanında diğer değerlerle değiştirilecek ayraç içinde yer tutucuları katıştırma. Aşağıdaki örnek, her döngü tekrarında sonucunu çıktısını almak için bir biçim dizesi kullanır:  
  
 [!code-csharp[csProgGuideStrings#26](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_6.cs)]  
  
 Bir aşırı yüklemesini <xref:System.Console.WriteLine%2A> yöntemi bir biçim dizesi bir parametre olarak alır. Bu nedenle, yalnızca bir biçim dizesi yöntemi için açık bir çağrı olmadan değişmez değer eklenebilir. Ancak, kullanırsanız <xref:System.Diagnostics.Trace.WriteLine%2A> Visual Studio'da hata ayıklama Çıktısı görüntülenecek yöntemi **çıkış** penceresinde sahip açıkça çağırmak <xref:System.String.Format%2A> yöntemi nedeniyle <xref:System.Diagnostics.Trace.WriteLine%2A> yalnızca bir dize biçim dizesini kabul eder. Biçim dizeleri hakkında daha fazla bilgi için bkz: [biçimlendirme türleri](../../../standard/base-types/formatting-types.md).  
  
## <a name="substrings"></a>Alt dizeler  
 Bir alt dizesi içinde yer alan karakter dizisi dizesidir. Kullanım <xref:System.String.Substring%2A> özgün dizeye bölümünden yeni bir dize oluşturmak için yöntemi. Kullanarak bir alt dizesi bir veya daha fazla oluşumları için arama yapabilirsiniz <xref:System.String.IndexOf%2A> yöntemi. Kullanım <xref:System.String.Replace%2A> yöntemi belirtilen bir alt dizenin tüm oluşumlarını yeni bir dizesi ile değiştirin. Gibi <xref:System.String.Substring%2A> yöntemi, <xref:System.String.Replace%2A> gerçekten yeni bir dize döndürür ve özgün dizeye değiştirmez. Daha fazla bilgi için bkz: [nasıl yapılır: dizeleri arama](../../how-to/search-strings.md) ve [nasıl yapılır: dize içeriklerini değiştirme](../../how-to/modify-string-contents.md).  
  
 [!code-csharp[csProgGuideStrings#7](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_7.cs)]  
  
## <a name="accessing-individual-characters"></a>Tek tek karakterlere erişme  
 Aşağıdaki örnekte olduğu gibi tek tek karakterleri salt okunur erişim kazanmak için bir dizin değeri ile dizi gösterimini kullanın:  
  
 [!code-csharp[csProgGuideStrings#9](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_8.cs)]  
  
 Varsa <xref:System.String> yöntemleri bir dizedeki karakterleri tek tek değiştirmek zorunda işlevleri sağlamaz kullanabileceğiniz bir <xref:System.Text.StringBuilder> tek tek karakter "yerinde" değiştirmek için nesne ve sonuçları kullanarak depolamak için yeni bir dize oluşturma <xref:System.Text.StringBuilder> yöntemleri. Aşağıdaki örnekte, özgün dizeye belirli bir şekilde değiştirin ve sonra sonuçları gelecekte kullanım için depolamak varsayın:  
  
 [!code-csharp[csProgGuideStrings#8](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_9.cs)]  
  
## <a name="null-strings-and-empty-strings"></a>Null dizeler ve boş dizeler  
 Boş bir dize örneği olan bir <xref:System.String?displayProperty=nameWithType> sıfır karakterler içeren nesne. Boş dizeler, genellikle bir boş metin alanı temsil etmek için çeşitli programlama senaryolarda kullanılır. Geçerli olduklarından boş dizeleri yöntemleri çağırabilir <xref:System.String?displayProperty=nameWithType> nesneleri. Boş dizeler gibi başlatılır:  
  
```  
string s = String.Empty;  
```  
  
 Bunun aksine, boş bir dize örneğine başvurmayan bir <xref:System.String?displayProperty=nameWithType> nesne ve bir yöntem boş bir dizesine nedenler çağırma girişimi herhangi bir <xref:System.NullReferenceException>. Ancak, diğer dizelerle birleştirme ve karşılaştırma işlemleri null dizelerde kullanabilirsiniz. Aşağıdaki örneklerde, boş bir dize başvuru yapar ve bir özel durum oluşturulmasına neden olmaz ve bazı durumlarda gösterilmektedir:  
  
 [!code-csharp[csProgGuideStrings#27](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_10.cs)]  
  
## <a name="using-stringbuilder-for-fast-string-creation"></a>Hızlı dize oluşturma için StringBuilder kullanma  
 .NET dize işlemlerinde yüksek oranda iyileştirilmiş ve çoğu durumda performansı önemli ölçüde etkilemez. Ancak, yüzlerce veya binlerce kez yürütmeden sıkı döngüler gibi bazı senaryolarda, dize işlemleri performansını etkileyebilir. <xref:System.Text.StringBuilder> Sınıfı programınız birçok dize işlemeleri gerçekleştirirse, daha iyi performans sunan bir dize arabellek oluşturur. <xref:System.Text.StringBuilder> Dize ayrıca yerleşik dize veri türü desteklemiyor, tek tek karakter, bir şey atamak sağlar. Bu kod, bir dize içeriğini yeni bir dize oluşturmadan değişiklikler; örneğin:  
  
 [!code-csharp[csProgGuideStrings#20](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_11.cs)]  
  
 Bu örnekte, bir <xref:System.Text.StringBuilder> nesnesi sayısal türler kümesinden bir dizesi oluşturmak için kullanılır:  
  
 [!code-csharp[csProgGuideStrings#15](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_12.cs)]  
  
## <a name="strings-extension-methods-and-linq"></a>Dizeleri, genişletme yöntemleri ve LINQ  
 Çünkü <xref:System.String> yazın uygulayan <xref:System.Collections.Generic.IEnumerable%601>, tanımlanan genişletme yöntemleri kullanabilirsiniz <xref:System.Linq.Enumerable> dizelerde sınıfı. Görsel dağınıklığı önlemek için bu yöntemleri için IntelliSense gelen hariç tutulan <xref:System.String> türü, ancak kullanılabilir ancak yine de. Aynı zamanda [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu dizelerini ifadelerini. Daha fazla bilgi için bkz: [LINQ ve dizeler](../../../csharp/programming-guide/concepts/linq/linq-and-strings.md).  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Konu|Açıklama|  
|-----------|-----------------|  
|[Nasıl yapılır: Dize İçeriklerini Değiştirme](../../how-to/modify-string-contents.md)|Dizeleri dönüştürme ve dizeleri içeriğini değiştirmek için teknikleri göstermektedir.|  
|[Nasıl yapılır: Dizeleri Karşılaştırma](../../how-to/compare-strings.md)|Sıralı gerçekleştirme ve kültür belirli karşılaştırmaları dizisini gösterir.|  
|[Nasıl yapılır: Birden Çok Dizeyi Birleştirme](../../how-to/concatenate-multiple-strings.md)|Birden çok dizenin birine katılmak için çeşitli yollar gösterir.|
|[Nasıl yapılır: String.Split kullanarak dizeleri ayrıştırma ](../../how-to/parse-strings-using-split.md)|Nasıl kullanılacağını gösteren kod örnekleri içerir `String.Split` dizeleri ayrıştırma yöntemi.|  
|[Nasıl yapılır: dizeleri arama](../../how-to/search-strings.md)|Belirli bir metin veya desenler için arama dizelerini kullanımı açıklanmaktadır.|  
|[Nasıl yapılır: Bir Dizenin Sayısal bir Değeri Temsil Edip Etmediğini Belirleme](../../../csharp/programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)|Güvenli bir şekilde geçerli bir sayısal değer olup olmadığını görmek için bir dizesi ayrıştırılamıyor gösterilmiştir.|  
|[Dize ilişkilendirme](../../language-reference/tokens/interpolated.md)|Biçim dizeleri için kullanışlı bir sözdizimi sağlar ve dize ilişkilendirme özelliğini açıklar.|
|[Temel Dize İşlemleri](../../../../docs/standard/base-types/basic-string-operations.md)|Kullanın konulara bağlantılar sağlanır <xref:System.String?displayProperty=nameWithType> ve <xref:System.Text.StringBuilder?displayProperty=nameWithType> temel dize işlemleri gerçekleştirmek için yöntemleri.|  
|[Dizeleri Ayrıştırma](../../../standard/base-types/parsing-strings.md)|Karşılık gelen türlerine örneklerine dize Beyanları .NET temel türleri dönüştürme açıklar.|  
|[Tarih ve saat dizelerini .NET ayrıştırma](../../../standard/base-types/parsing-datetime.md)|İçin "24/01/2008" gibi bir dize dönüştürme gösteren bir <xref:System.DateTime?displayProperty=nameWithType> nesnesi.|  
|[Dizeleri Karşılaştırma](../../../../docs/standard/base-types/comparing.md)|Örnekler C# ve Visual Basic sağlar ve dizeleri karşılaştırmak hakkında bilgi içerir.|  
|[StringBuilder Sınıfını Kullanma](../../../standard/base-types/stringbuilder.md)|Oluşturup kullanarak dinamik dize nesneleri değiştirmek açıklar <xref:System.Text.StringBuilder> sınıfı.|  
|[LINQ ve Dizeler](../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)|LINQ sorgularını kullanarak çeşitli dize işlemlerini gerçekleştirme hakkında bilgi sağlar.|  
|[C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)|C# programlama yapıları açıklayan konulara bağlantılar sağlar.|  
