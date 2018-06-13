---
title: Bileşik Biçimlendirme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parameter specifiers
- strings [.NET Framework], alignment
- format specifiers, composite formatting
- strings [.NET Framework], composite
- composite formatting
- objects [.NET Framework], formatting multiple objects
ms.assetid: 87b7d528-73f6-43c6-b71a-f23043039a49
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4922470633f3dec8e2e2f898bdf544f5aa4deded
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33579190"
---
# <a name="composite-formatting"></a>Bileşik Biçimlendirme
.NET bileşik biçimlendirme özelliği nesneleri ve bir bileşik biçim dizesi listesini girdi olarak alır. Bir bileşik biçimlendirme dizesi, sabit metinle karışık bir şekilde listedeki nesnelere karşılık gelen, biçim öğeleri adı verilen dizinli yer tutuculardan oluşur. Biçimlendirme işlemi sonuç olarak, orijinal sabit metin ve listedeki nesnelerin dize temsillerinin karışımından oluşan bir dize oluşturur.  
  
 Bileşik biçimlendirme özelliği aşağıdaki gibi yöntemler tarafından desteklenir:  
  
-   <xref:System.String.Format%2A?displayProperty=nameWithType>, biçimlendirilmiş Sonuç dizesini döndürür.  
  
-   <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>, biçimlendirilmiş sonuç dizeye ekler bir <xref:System.Text.StringBuilder> nesnesi.  
  
-   Bazı aşırı <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> konsola biçimlendirilmiş sonuç dize görüntüleme yöntemi.  
  
-   Bazı aşırı <xref:System.IO.TextWriter.WriteLine%2A?displayProperty=nameWithType> biçimlendirilmiş sonuç dize bir akış veya dosyaya yazmak yöntemi. Türetilmiş sınıflar <xref:System.IO.TextWriter>, gibi <xref:System.IO.StreamWriter> ve <xref:System.Web.UI.HtmlTextWriter>, aynı zamanda bu işlevselliği paylaşın.  
  
-   <xref:System.Diagnostics.Debug.WriteLine%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>, izleme dinleyicileri için biçimlendirilmiş bir ileti çıkarır.  
  
-   <xref:System.Diagnostics.Trace.TraceError%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.TraceInformation%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>, Ve <xref:System.Diagnostics.Trace.TraceWarning%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> yöntemleri, hangi çıktı biçimlendirilmiş izleme dinleyicileri iletileri.  
  
-   <xref:System.Diagnostics.TraceSource.TraceInformation%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> İzleme dinleyicileri bilgilendirici bir yöntem Yazar yöntemi.  
  
## <a name="composite-format-string"></a>Bileşik Biçim Dizesi  
 Bileşik biçimlendirme özelliğini destekleyen metotlarda bir bileşik biçimlendirme dizesi ve nesne listesi bağımsız değişkenler olarak kullanılır. Bir bileşik biçimlendirme dizesi sıfır veya daha fazla sabit metin bölümüyle karışık olarak bir veya daha fazla biçim öğesinden oluşur. Sabit metin seçtiğiniz herhangi bir dizedir, ve her biçim öğesi listedeki bir nesneye veya kutulu yapıya karşılık gelir. Bileşik biçimlendirme özelliği, her biçim öğesinin yerine listede karşılık gelen nesnenin dize temsili yerleştirilmiş bir şekilde yeni bir sonuç dizesi döndürür.  
  
 Aşağıdakileri göz önünde bulundurun <xref:System.String.Format%2A> kod parçası.  
  
 [!code-csharp[Formatting.Composite#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#1)]
 [!code-vb[Formatting.Composite#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#1)]  
  
 Sabit metindir "`Name =` "ve"`, hours =` ". Biçim öğeleri "`{0}`", dizinini: nesnesine karşılık gelen 0 `name`, ve "`{1:hh}`", dizinini is nesnesine karşılık gelen 1 `DateTime.Now`.  
  
## <a name="format-item-syntax"></a>Biçim Öğesi Sözdizimi  
 Her biçim öğesi aşağıdaki biçimi alır ve aşağıdaki bileşenlerden oluşur:  
  
 `{` *Dizin*[`,`*hizalama*] [`:`*formatString*]`}`  
  
 Eşleşen ayraçlar ("{" ve "}") gereklidir.  
  
### <a name="index-component"></a>Dizin Bileşeni  
 Zorunlu *dizin* bileşeni, bir parametre tanımlayıcısı olarak da bilinir, nesnelerin karşılık gelen bir öğe listesi ile tanımlayan 0'dan başlayarak bir sayıdır. Yani, parametre tanımlayıcısı 0 olan biçim öğesi listedeki ilk nesneyi biçimlendirir, parametre tanımlayıcısı 1 olan biçim öğesi listedeki ikinci nesneyi biçimlendirir ve bu şekilde devam eder. Aşağıdaki örnek, ondan daha az asal sayılar göstermek için üç, aracılığıyla sıfır numaralı dört parametre belirticileri, içerir:  
  
 [!code-csharp[Formatting.Composite#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/index1.cs#7)]
 [!code-vb[Formatting.Composite#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/index1.vb#7)]  
  
 Birden çok biçim öğesi, aynı parametre tanımlayıcısını belirterek nesne listesindeki aynı öğeye başvurabilir. Bileşik biçimlendirme dizesi belirterek aynı sayısal değer onaltılık, bilimsel ve sayı biçiminde örneğin biçimlendirebilirsiniz: "0 x{0:X} {0:E} {0:N}", aşağıdaki örnekte gösterildiği gibi.  
  
 [!code-csharp[Formatting.Composite#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/index1.cs#10)]
 [!code-vb[Formatting.Composite#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/index1.vb#10)]  
  
 Her biçim öğesi listedeki herhangi bir nesneye başvurabilir. Örneğin, üç nesne varsa, biçimlendirmek ikinci, ilk ve üçüncü nesne şuna benzer bir bileşik biçim dizesi belirterek: "{1} {0} {2}". Bir biçimlendirme nesnesi tarafından başvurulmayan nesneler yok sayılır. A <xref:System.FormatException> parametre belirleyici nesnelerin listesini sınırları dışındaki bir öğe belirlerse çalışma zamanında atılır.  
  
### <a name="alignment-component"></a>Hizalama Bileşeni  
 İsteğe bağlı *hizalama* tercih edilen biçimlendirilmiş alan genişliğini belirten imzalı bir tamsayı bir bileşendir. Varsa değerini *hizalama* biçimlendirilmiş dize uzunluğu'dan küçük *hizalama* göz ardı edilir ve biçimlendirilmiş dize uzunluğu alan genişliği kullanılır. Biçimlendirilmiş verileri alanında sağ varsa hizalanır *hizalama* pozitif ve sola hizalı *hizalama* negatiftir. Eğer iç boşluk gerekliyse, boşluk kullanılır. Virgül gerekli ise *hizalama* belirtilir.  
  
 Aşağıdaki örnekte, iki hafta döneminde çalışılan saatleri dizilerinin, bir çalışanların adlarını içeren ve diğer içeren tanımlar. Bileşik biçim dizesi sol-20 karakter alan adları ve sağa-saatlerini 5 karakterlik alanında hizalar. Not "N1" standart biçim dizesi bir kesirli rakam ile saat biçimlendirmek için de kullanılır.  
  
 [!code-csharp[Formatting.Composite#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/alignment1.cs#8)]
 [!code-vb[Formatting.Composite#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/alignment1.vb#8)]  
  
### <a name="format-string-component"></a>Biçim Dizesi Bileşeni  
 İsteğe bağlı *formatString* bileşenidir biçimlendirilen nesne türü için uygun bir biçim dizesi. Standart veya özel sayısal biçim dizesi karşılık gelen nesne sayısal bir değer ise bir standart veya özel tarih ve saat biçim dizesi karşılık gelen nesne ise belirtin bir <xref:System.DateTime> nesnesi veya bir [numaralandırma biçim dizesi](../../../docs/standard/base-types/enumeration-format-strings.md)karşılık gelen nesne numaralandırma değeri ise. Varsa *formatString* belirtilmezse, genel ("G") biçimi belirleyici bir sayı, tarih ve saat veya numaralandırma türü için kullanılır. İki nokta üst üste gerekli ise *formatString* belirtilir.  
  
 Aşağıdaki tablo, .NET Framework içinde bulunan, önceden tanımlanmış bir biçimlendirme dizesi kümesini destekleyen türleri ve kategorileri listeler, ve desteklenen biçimlendirme dizelerini listeleyen konulara bağlantılar sağlar. Dize biçimlendirmenin, tüm varolan türler için yeni biçimlendirme dizeleri tanımlanabilmesini mümkün kılmanın yanı sıra uygulamada tanımlanmış bir tür tarafından desteklenen bir biçimlendirme dizesi kümesinin tanımlanabilmesine olanak veren genişletilebilir bir mekanizma olduğuna dikkat edin. Daha fazla bilgi için bkz: <xref:System.IFormattable> ve <xref:System.ICustomFormatter> arabirimi konuları.  
  
|Tür veya tür kategorisi|Bkz. |  
|---------------------------|---------|  
|Tarih ve saat türleri (<xref:System.DateTime>, <xref:System.DateTimeOffset>)|[Standart Tarih ve Saat Biçim Dizeleri](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)<br /><br /> [Özel Tarih ve Saat Biçim Dizeleri](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)|  
|Numaralandırma türleri (tüm türleri türetilmiş <xref:System.Enum?displayProperty=nameWithType>)|[Sabit Listesi Biçim Dizeleri](../../../docs/standard/base-types/enumeration-format-strings.md)|  
|Sayısal türler (<xref:System.Numerics.BigInteger>, <xref:System.Byte>, <xref:System.Decimal>, <xref:System.Double>, <xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.SByte>, <xref:System.Single>, <xref:System.UInt16>, <xref:System.UInt32>, <xref:System.UInt64>)|[Standart Sayısal Biçim Dizeleri](../../../docs/standard/base-types/standard-numeric-format-strings.md)<br /><br /> [Özel Sayısal Biçim Dizeleri](../../../docs/standard/base-types/custom-numeric-format-strings.md)|  
|<xref:System.Guid>|<xref:System.Guid.ToString%28System.String%29?displayProperty=nameWithType>|  
|<xref:System.TimeSpan>|[Standart TimeSpan Biçim Dizeleri](../../../docs/standard/base-types/standard-timespan-format-strings.md)<br /><br /> [Özel TimeSpan Biçim Dizeleri](../../../docs/standard/base-types/custom-timespan-format-strings.md)|  
  
### <a name="escaping-braces"></a>Çıkış Yapan Ayraçlar  
 Açma ve kapatma ayraçları bir biçim öğesinin başlangıcı ve bitişi olarak yorumlanır. Sonuç olarak, sabit bir açılış veya kapanış ayracını görüntülemek için bir kaçış dizisi kullanmanız gerekir. Bir açılış ayracı ("{") görüntülemek için sabit metinde iki açılış ayracı ("{{"), veya bir kapanış ayracı ("}") görüntülemek için sabit metinde iki kapanış ayracı ("}}") belirtin. Bir biçim öğesindeki ayraçlar, karşılaşıldıkları sırada sıralı olarak yorumlanır. İç içe ayraçları yorumlama desteklenmez.  
  
 Kaçırılan ayraçların yorumlanma şekli beklenmeyen sonuçlara neden olabilir. Örneğin, öğeyi Biçimlendir göz önünde bulundurun "{{{0:D}}}" açılan parantez görüntülemek için hedeflenen, sayısal bir değer olarak biçimlendirilmiş bir ondalık sayı ve bir kapanış ayracı. Ancak, biçim öğesi aslında şu şekilde yorumlanır:  
  
1.  İlk iki açılış ayracı ("{{") kaçırılır ve bir açılış ayracı olur.  
  
2.  Sonraki üç karakter ("{0:") bir biçim öğesinin başlangıcı olarak yorumlanır.  
  
3.  Sonraki karakter ("D") Ondalık standart sayısal biçim tanımlayıcısı olarak yorumlanır, ancak sonraki iki kaçırılan ayıraç ("}}") tek bir ayıraç olur. Sonuç dize ("D}") standart bir sayısal biçim tanımlayıcısı olmadığı için, sonuç dize özel bir biçimlendirme dizesi olarak yorumlanır ve bu nedenle "D}" sabit dizesini görüntüler.  
  
4.  Son ayıraç ("}") biçim öğesinin bitişi olarak yorumlanır.  
  
5.  Sonuç olarak "{D}" sabit dizesi görüntülenir. Biçimlendirilmek istenen sayısal değer görüntülenmez.  
  
 Kodunuzun kaçırılan ayraçları ve format öğelerini yanlış yorumlamasından kaçınmanın bir yolu, ayraçları ve biçim öğesini ayrı olarak biçimlendirmektir. Yani, ilk biçimlendirme işleminde bir sabit açılış ayracı görüntülemek, sonraki işlemde biçim öğesinin sonucunu görüntülemek ve son işlemde de bir sabit kapanış ayracı görüntülemektir. Aşağıdaki örnek bu yaklaşımı gösterir.  
  
 [!code-csharp[Formatting.Composite#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Escaping1.cs#2)]
 [!code-vb[Formatting.Composite#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Escaping1.vb#2)]  
  
### <a name="processing-order"></a>İşlem Sırası  
 Bileşik biçimlendirme yöntemi çağrısı içeriyorsa, bir <xref:System.IFormatProvider> bağımsız değişken değeri değil `null`, çalışma zamanı çağrıları kendi <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> istemek için yöntemi bir <xref:System.ICustomFormatter> uygulaması. Yöntemin dönüş mümkün ise bir <xref:System.ICustomFormatter> uygulaması, bileşik yöntemi biçimlendirme çağrı boyunca önbelleğe alınır.
  
 Her değer bir biçim öğesine karşılık gelen parametre listesinde aşağıdaki gibi bir dizeye dönüştürülür:  
  
1.  Biçimlendirilecek değer ise `null`, boş bir dize <xref:System.String.Empty?displayProperty=nameWithType> döndürülür.  
  
2.  Varsa bir <xref:System.ICustomFormatter> uygulamasıdır kullanılabilir, çalışma zamanı çağrıları kendi <xref:System.ICustomFormatter.Format%2A> yöntemi. Biçim öğesi'nin yöntemi geçirir *formatString* biri varsa, değer veya `null` , değilse ile birlikte <xref:System.IFormatProvider> uygulaması. Varsa çağrısı <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> yöntemi döndürür `null`, yürütme devam eder sonraki adıma; Aksi takdirde sonucu <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> çağrısı döndürülür.
  
3.  Değer uyguluyorsa <xref:System.IFormattable> arabirimi, arabirimin <xref:System.IFormattable.ToString%28System.String%2CSystem.IFormatProvider%29> yöntemi çağrılır. Yöntemine geçirilen *formatString* biçimi öğesinde varsa, değer veya `null` değilse. <xref:System.IFormatProvider> Bağımsız değişkeni şu şekilde belirlenir:  
  
    -   Null olmayan bir yöntemle biçimlendirme bileşik ise bir sayısal değer için <xref:System.IFormatProvider> bağımsız değişkeni çağrılır, çalışma zamanı isteklerini bir <xref:System.Globalization.NumberFormatInfo> nesnesinin kendi <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> yöntemi. Bağımsız değişkenin değeri ise, bir sağlamak kaydedemediği `null`, veya bileşik yöntemi biçimlendirme yoksa, bir <xref:System.IFormatProvider> parametresi <xref:System.Globalization.NumberFormatInfo> geçerli iş parçacığı kültürünü kullanılan nesne.  
  
    -   Bir tarih ve saat değeri null olmayan bir yöntemle biçimlendirme bileşik varsa <xref:System.IFormatProvider> bağımsız değişkeni çağrılır, çalışma zamanı isteklerini bir <xref:System.Globalization.DateTimeFormatInfo> nesnesinin kendi <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> yöntemi. Bağımsız değişkenin değeri ise, bir sağlamak kaydedemediği `null`, veya bileşik yöntemi biçimlendirme yoksa, bir <xref:System.IFormatProvider> parametresi <xref:System.Globalization.DateTimeFormatInfo> geçerli iş parçacığı kültürünü kullanılan nesne.  
  
    -   Diğer türleri nesneler için bileşik biçimlendirme varsa yöntemi çağrılır bir <xref:System.IFormatProvider> bağımsız değişken değerini doğrudan geçirilir <xref:System.IFormattable.ToString%2A?displayProperty=nameWithType> uygulaması. Aksi takdirde, `null` geçirilir <xref:System.IFormattable.ToString%2A?displayProperty=nameWithType> uygulaması.  
  
4.  Türü parametresiz `ToString` yöntemi, ya da bir geçersiz kılma <xref:System.Object.ToString?displayProperty=nameWithType> veya devralınabilir. taban sınıf davranışını devralır, olarak adlandırılır. Bu durumda, biçim dizesi tarafından belirtilen *formatString* biçimi öğesinde bileşen varsa, göz ardı edilir.  
  
 Üstteki adımlar gerçekleştirildikten sonra hizalama uygulanır.  
  
## <a name="code-examples"></a>Kod Örnekleri  
 Aşağıdaki örnek bileşik biçimlendirme ve başka bir nesnenin kullanılarak oluşturulan kullanılarak oluşturulan bir dizesini gösterir `ToString` yöntemi. İki biçimlendirme türü de eşdeğer sonuçlar üretir.  
  
 [!code-csharp[Formatting.Composite#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#3)]
 [!code-vb[Formatting.Composite#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#3)]  
  
 Geçerli gün Perşembe May içinde olduğu varsayılarak, önceki örnekte her iki dize değeri `Thursday May` ABD İngilizce kültür.  
  
 <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> ile aynı işlevselliği sunar <xref:System.String.Format%2A?displayProperty=nameWithType>. İki yöntem arasındaki tek fark <xref:System.String.Format%2A?displayProperty=nameWithType> sonuç bir dize olarak döndürür sırada <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> çıkış akışı sonucu ilişkili yazma <xref:System.Console> nesnesi. Aşağıdaki örnek kullanır <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> değerini biçimlendirmek için yöntemi `MyInt` para birimi değeri.  
  
 [!code-csharp[Formatting.Composite#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#4)]
 [!code-vb[Formatting.Composite#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#4)]  
  
 Aşağıdaki örnek birden çok nesneyi biçimlendirmeyi ve bir nesneyi iki farklı şekilde biçimlendirmeyi gösterir.  
  
 [!code-csharp[Formatting.Composite#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#5)]
 [!code-vb[Formatting.Composite#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#5)]  
  
 Aşağıdaki örnek biçimlendirmede hizalama kullanımını gösterir. Biçimlendirilmiş bağımsız değişkenleri dikey çubuk karakter arasında yerleştirilir (&#124;) sonuçta elde edilen hizalama vurgulayın.  
  
 [!code-csharp[Formatting.Composite#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#6)]
 [!code-vb[Formatting.Composite#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#6)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Console.WriteLine%2A>  
 <xref:System.String.Format%2A?displayProperty=nameWithType>  
 [Dize ilişkilendirme (C#)](../../csharp/language-reference/tokens/interpolated.md)  
 [Dize ilişkilendirme (Visual Basic)](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md)  
 [Biçimlendirme Türleri](../../../docs/standard/base-types/formatting-types.md)  
 [Standart Sayısal Biçim Dizeleri](../../../docs/standard/base-types/standard-numeric-format-strings.md)  
 [Özel Sayısal Biçim Dizeleri](../../../docs/standard/base-types/custom-numeric-format-strings.md)  
 [Standart Tarih ve Saat Biçim Dizeleri](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)  
 [Özel Tarih ve Saat Biçim Dizeleri](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)  
 [Standart TimeSpan Biçim Dizeleri](../../../docs/standard/base-types/standard-timespan-format-strings.md)  
 [Özel TimeSpan Biçim Dizeleri](../../../docs/standard/base-types/custom-timespan-format-strings.md)  
 [Sabit Listesi Biçim Dizeleri](../../../docs/standard/base-types/enumeration-format-strings.md)
