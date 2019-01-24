---
title: Bileşik Biçimlendirme
ms.date: 10/26/2018
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
ms.openlocfilehash: f68c1f2f888f340488c3cbec4c2384f6dce58077
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54517688"
---
# <a name="composite-formatting"></a>Bileşik Biçimlendirme

.NET bileşik biçimlendirme özelliği, nesneleri ve bir bileşik biçimlendirme dizesi listesini girdi olarak alır. Bir bileşik biçimlendirme dizesi, sabit metinle karışık bir şekilde listedeki nesnelere karşılık gelen, biçim öğeleri adı verilen dizinli yer tutuculardan oluşur. Biçimlendirme işlemi sonuç olarak, orijinal sabit metin ve listedeki nesnelerin dize temsillerinin karışımından oluşan bir dize oluşturur.  
  
> [!IMPORTANT]
> Kullanabileceğiniz bileşik biçim dizeleri kullanmak yerine, *ilişkilendirilmiş dizeler* kullandığınız dil ve dil sürümü bunları destekliyorsa. İlişkilendirilmiş dize içeren bir dizedir *ilişkilendirilmiş ifade*. Her ilişkilendirilmiş ifade ifadenin değerinin ile çözümlendi ve dize atandığında sonuç dizesinde dahil. Daha fazla bilgi için [dize ilişkilendirme (C# başvuru)](../../csharp/language-reference/tokens/interpolated.md) ve [Ara değerli dizeler (Visual Basic Başvurusu)](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md).

Bileşik biçimlendirme özelliği aşağıdaki gibi yöntemler tarafından desteklenir:  
  
- <xref:System.String.Format%2A?displayProperty=nameWithType>, biçimlendirilmiş Sonuç dizesini döndürür.  
  
- <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>, ekler için biçimlendirilmiş Sonuç dizesini bir <xref:System.Text.StringBuilder> nesne.   
- Bazı aşırı yüklemeleri <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> yöntemi konsola biçimlendirilmiş Sonuç dizesini görüntüler.  
  
- Bazı aşırı yüklemeleri <xref:System.IO.TextWriter.WriteLine%2A?displayProperty=nameWithType> biçimlendirilmiş Sonuç dizesini bir akış veya dosyaya yazmak yöntemi. Türetilmiş sınıflar <xref:System.IO.TextWriter>, gibi <xref:System.IO.StreamWriter> ve <xref:System.Web.UI.HtmlTextWriter>, ayrıca bu işlevleri paylaşırlar.  
  
- <xref:System.Diagnostics.Debug.WriteLine%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>, izleme dinleyicilerine biçimlendirilmiş bir ileti çıkarır.  
  
- <xref:System.Diagnostics.Trace.TraceError%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.TraceInformation%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>, Ve <xref:System.Diagnostics.Trace.TraceWarning%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> iletileri izleme dinleyicilerine biçimlendirilmiş yöntemleri.  
  
- <xref:System.Diagnostics.TraceSource.TraceInformation%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> İzleme dinleyicilerine bilgi yöntemi yazan yöntemi.  
  
## <a name="composite-format-string"></a>Bileşik Biçim Dizesi  
 Bileşik biçimlendirme özelliğini destekleyen metotlarda bir bileşik biçimlendirme dizesi ve nesne listesi bağımsız değişkenler olarak kullanılır. Bir bileşik biçimlendirme dizesi sıfır veya daha fazla sabit metin bölümüyle karışık olarak bir veya daha fazla biçim öğesinden oluşur. Sabit metin seçtiğiniz herhangi bir dizedir, ve her biçim öğesi listedeki bir nesneye veya kutulu yapıya karşılık gelir. Bileşik biçimlendirme özelliği, her biçim öğesinin yerine listede karşılık gelen nesnenin dize temsili yerleştirilmiş bir şekilde yeni bir sonuç dizesi döndürür.  
  
 Aşağıdakileri göz önünde bulundurun <xref:System.String.Format%2A> kod parçası.  
  
 [!code-csharp[Formatting.Composite#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#1)]
 [!code-vb[Formatting.Composite#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#1)]  
  
 Sabit metin "`Name =` "ve"`, hours =` ". Biçim öğesi olan "`{0}`", dizini olan nesneye karşılık gelen 0 `name`, ve "`{1:hh}`", dizini olan nesneye karşılık gelen 1 `DateTime.Now`.  
  
## <a name="format-item-syntax"></a>Biçim Öğesi Sözdizimi  
 Her biçim öğesi aşağıdaki biçimi alır ve aşağıdaki bileşenlerden oluşur:  
  
 `{` *index*[`,`*alignment*][`:`*formatString*]`}`  
  
 Eşleşen ayraçlar ("{" ve "}") gereklidir.  
  
### <a name="index-component"></a>Dizin Bileşeni  
 Zorunlu *dizin* ayrıca bir parametre tanımlayıcı da denen bileşenidir Nesne listesinde karşılık gelen bir öğeyi tanımlayan 0 ile başlayan bir sayıdır. Yani, parametre tanımlayıcısı 0 olan biçim öğesi listedeki ilk nesneyi biçimlendirir, parametre tanımlayıcısı 1 olan biçim öğesi listedeki ikinci nesneyi biçimlendirir ve bu şekilde devam eder. Aşağıdaki örnek 10'dan az asal sayıları temsil etmek için sıfır üç sanal makine aracılığıyla numaralı dört parametre belirticileri, içerir:  
  
 [!code-csharp[Formatting.Composite#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/index1.cs#7)]
 [!code-vb[Formatting.Composite#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/index1.vb#7)]  
  
 Birden çok biçim öğesi, aynı parametre tanımlayıcısını belirterek nesne listesindeki aynı öğeye başvurabilir. Örneğin, bir bileşik biçimlendirme dizesi belirterek aynı sayısal değeri onaltılık, bilimsel ve sayı biçiminde biçimlendirebilirsiniz: "0 x{0:X} {0:E} {0:N}" aşağıdaki örnekte gösterildiği gibi.  
  
 [!code-csharp[Formatting.Composite#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/index1.cs#10)]
 [!code-vb[Formatting.Composite#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/index1.vb#10)]  
  
 Her biçim öğesi listedeki herhangi bir nesneye başvurabilir. Örneğin, üç nesne varsa, ikinci, biçimlendirme ve üçüncü nesneyi bir bileşik biçimlendirme dizesi belirterek: "{1} {0} {2}". Bir biçimlendirme nesnesi tarafından başvurulmayan nesneler yok sayılır. A <xref:System.FormatException> çalışma zamanında bir parametre tanımlayıcısı nesne listesinin sınırları dışında bir öğe belirlerse oluşturulur.  
  
### <a name="alignment-component"></a>Hizalama Bileşeni  
 İsteğe bağlı *hizalama* bileşendir tercih edilen biçimlendirilmiş alan genişliğini belirten bir işaretli tamsayı. Varsa değerini *hizalama* biçimlendirilmiş dizenin uzunluğu'dan küçük *hizalama* yok sayılır ve alan genişliği olarak biçimlendirilen dizenin uzunluğu kullanılır. Alandaki biçimlendirilmiş veri hakkı varsa hizalanır *hizalama* pozitif ve sola hizalanmış *hizalama* negatiftir. Eğer iç boşluk gerekliyse, boşluk kullanılır. Virgül gereklidir *hizalama* belirtilir.  
  
 Aşağıdaki örnek, bir iki haftalık süre içinde çalıştıkları saat dizilerinin, bir çalışan adlarını içeren ve diğer içeren tanımlar. Bileşik biçimlendirme dizesi sol-20 karakter alan adlarında ve sağ-saatlerini 5 karakterli alanında hizalar. "N1" standart biçim dizesi kesirli bir basamak ile saatleri biçimlendirmek için de kullanıldığını unutmayın.  
  
 [!code-csharp[Formatting.Composite#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/alignment1.cs#8)]
 [!code-vb[Formatting.Composite#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/alignment1.vb#8)]  
  
### <a name="format-string-component"></a>Biçim Dizesi Bileşeni  
 İsteğe bağlı *formatString* bileşenidir, biçimlendirilen nesnenin türü için uygun olan bir biçim dizesi. Bir standart veya özel sayısal biçim dizesi karşılık gelen nesne bir sayısal değer ise bir standart veya özel tarih ve saat biçim dizesini karşılık gelen nesne belirtin bir <xref:System.DateTime> nesnesi veya bir [sabit listesi biçimlendirme dizesi](../../../docs/standard/base-types/enumeration-format-strings.md)karşılık gelen nesne bir sabit listesi değeri ise. Varsa *formatString* belirtilmezse, sayı, tarih ve saat veya numaralandırma türü için genel ("G") Biçim belirleyicisi kullanılır. İki nokta üst üste gereklidir *formatString* belirtilir.  
  
 Aşağıdaki tablo, .NET Framework içinde bulunan, önceden tanımlanmış bir biçimlendirme dizesi kümesini destekleyen türleri ve kategorileri listeler, ve desteklenen biçimlendirme dizelerini listeleyen konulara bağlantılar sağlar. Dize biçimlendirmenin, tüm varolan türler için yeni biçimlendirme dizeleri tanımlanabilmesini mümkün kılmanın yanı sıra uygulamada tanımlanmış bir tür tarafından desteklenen bir biçimlendirme dizesi kümesinin tanımlanabilmesine olanak veren genişletilebilir bir mekanizma olduğuna dikkat edin. Daha fazla bilgi için <xref:System.IFormattable> ve <xref:System.ICustomFormatter> arabirimi konuları.  
  
|Tür veya tür kategorisi|Bkz. |  
|---------------------------|---------|  
|Tarih ve saat türleri (<xref:System.DateTime>, <xref:System.DateTimeOffset>)|[Standart Tarih ve Saat Biçim Dizeleri](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)<br /><br /> [Özel Tarih ve Saat Biçim Dizeleri](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)|  
|Numaralandırma türleri (öğesinden türetilen tüm türler <xref:System.Enum?displayProperty=nameWithType>)|[Sabit Listesi Biçim Dizeleri](../../../docs/standard/base-types/enumeration-format-strings.md)|  
|Sayısal türler (<xref:System.Numerics.BigInteger>, <xref:System.Byte>, <xref:System.Decimal>, <xref:System.Double>, <xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.SByte>, <xref:System.Single>, <xref:System.UInt16>, <xref:System.UInt32>, <xref:System.UInt64>)|[Standart Sayısal Biçim Dizeleri](../../../docs/standard/base-types/standard-numeric-format-strings.md)<br /><br /> [Özel Sayısal Biçim Dizeleri](../../../docs/standard/base-types/custom-numeric-format-strings.md)|  
|<xref:System.Guid>|<xref:System.Guid.ToString%28System.String%29?displayProperty=nameWithType>|  
|<xref:System.TimeSpan>|[Standart TimeSpan Biçim Dizeleri](../../../docs/standard/base-types/standard-timespan-format-strings.md)<br /><br /> [Özel TimeSpan Biçim Dizeleri](../../../docs/standard/base-types/custom-timespan-format-strings.md)|  
  
### <a name="escaping-braces"></a>Çıkış Yapan Ayraçlar  
 Açma ve kapatma ayraçları bir biçim öğesinin başlangıcı ve bitişi olarak yorumlanır. Sonuç olarak, sabit bir açılış veya kapanış ayracını görüntülemek için bir kaçış dizisi kullanmanız gerekir. Bir açılış ayracı ("{") görüntülemek için sabit metinde iki açılış ayracı ("{{"), veya bir kapanış ayracı ("}") görüntülemek için sabit metinde iki kapanış ayracı ("}}") belirtin. Bir biçim öğesindeki ayraçlar, karşılaşıldıkları sırada sıralı olarak yorumlanır. İç içe ayraçları yorumlama desteklenmez.  
  
 Kaçırılan ayraçların yorumlanma şekli beklenmeyen sonuçlara neden olabilir. Örneğin, biçim öğesini göz önünde bulundurun "{{{0:D}}}", bir açılış ayracı görüntülemek için hedeflenen, sayısal bir değer olarak biçimlendirilmiş bir ondalık sayı ve bir kapanış ayracı. Ancak, biçim öğesi aslında şu şekilde yorumlanır:  
  
1.  İlk iki açılış ayracı ("{{") kaçırılır ve bir açılış ayracı olur.  
  
2.  Sonraki üç karakter ("{0:") bir biçim öğesinin başlangıcı olarak yorumlanır.  
  
3.  Sonraki karakter ("D") Ondalık standart sayısal biçim tanımlayıcısı olarak yorumlanır, ancak sonraki iki kaçırılan ayıraç ("}}") tek bir ayıraç olur. Sonuç dize ("D}") standart bir sayısal biçim tanımlayıcısı olmadığı için, sonuç dize özel bir biçimlendirme dizesi olarak yorumlanır ve bu nedenle "D}" sabit dizesini görüntüler.  
  
4.  Son ayıraç ("}") biçim öğesinin bitişi olarak yorumlanır.  
  
5.  Sonuç olarak "{D}" sabit dizesi görüntülenir. Biçimlendirilmek istenen sayısal değer görüntülenmez.  
  
 Kodunuzun kaçırılan ayraçları ve format öğelerini yanlış yorumlamasından kaçınmanın bir yolu, ayraçları ve biçim öğesini ayrı olarak biçimlendirmektir. Yani, ilk biçimlendirme işleminde bir sabit açılış ayracı görüntülemek, sonraki işlemde biçim öğesinin sonucunu görüntülemek ve son işlemde de bir sabit kapanış ayracı görüntülemektir. Aşağıdaki örnek bu yaklaşımı gösterir.  
  
 [!code-csharp[Formatting.Composite#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Escaping1.cs#2)]
 [!code-vb[Formatting.Composite#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Escaping1.vb#2)]  
  
### <a name="processing-order"></a>İşlem Sırası  
 Bileşik biçimlendirme yöntemi çağrısı içeriyorsa, bir <xref:System.IFormatProvider> bağımsız değişken değeri değil `null`, çalışma zamanı çağrıları kendi <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> istemek için yöntemi bir <xref:System.ICustomFormatter> uygulaması. Yöntem dönüş mümkün ise bir <xref:System.ICustomFormatter> uygulama, süresi boyunca bileşik biçimlendirme yöntemi çağrısı, önbelleğe alınır.
  
 Parametre listesinde bir biçim öğesine karşılık gelen her değer şu şekilde bir dizeye dönüştürülür:  
  
1.  Biçimlendirilecek değer ise `null`, boş bir dize <xref:System.String.Empty?displayProperty=nameWithType> döndürülür.  
  
2.  Varsa bir <xref:System.ICustomFormatter> kullanılamıyorsa çalışma zamanı çağrıları kendi <xref:System.ICustomFormatter.Format%2A> yöntemi. Öğenin yöntemi geçirir *formatString* biri varsa, değer veya `null` , değilse ile birlikte <xref:System.IFormatProvider> uygulaması. Çağrı <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> yöntemi döndürür `null`, yürütme devam eder, sonraki adıma; Aksi takdirde, sonucunu <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> çağrı döndürülür.
  
3.  Değer uyguluyorsa <xref:System.IFormattable> arabirimi, arabirimin <xref:System.IFormattable.ToString%28System.String%2CSystem.IFormatProvider%29> yöntemi çağrılır. Yönteme *formatString* değeri biçim öğesinde varsa veya `null` değilse. <xref:System.IFormatProvider> Bağımsız değişkeni aşağıdaki şekilde belirlenir:  
  
    -   Bir bileşik biçimlendirme yöntemi ile bir null olmayan bir sayı değeri <xref:System.IFormatProvider> bağımsız değişken çağrılırsa, çalışma zamanı bir <xref:System.Globalization.NumberFormatInfo> nesnesinin kendi <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> yöntemi. Bağımsız değişkenin değerini ise tane sağlanamazsa, `null`, veya bileşik biçimlendirme yöntemi yoksa bir <xref:System.IFormatProvider> parametresi <xref:System.Globalization.NumberFormatInfo> nesnesi geçerli iş parçacığı kültürü kullanılır.  
  
    -   Bir tarih ve saat değeri, bir bileşik biçimlendirme yöntemi ile null olmayan bir <xref:System.IFormatProvider> bağımsız değişken çağrılırsa, çalışma zamanı bir <xref:System.Globalization.DateTimeFormatInfo> nesnesinin kendi <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> yöntemi. Bağımsız değişkenin değerini ise tane sağlanamazsa, `null`, veya bileşik biçimlendirme yöntemi yoksa bir <xref:System.IFormatProvider> parametresi <xref:System.Globalization.DateTimeFormatInfo> nesnesi geçerli iş parçacığı kültürü kullanılır.  
  
    -   Diğer tür nesneler için bir bileşik biçimlendirme yöntemi ile aranan bir <xref:System.IFormatProvider> bağımsız değişken değeri doğrudan geçirilir <xref:System.IFormattable.ToString%2A?displayProperty=nameWithType> uygulaması. Aksi takdirde, `null` geçirilir <xref:System.IFormattable.ToString%2A?displayProperty=nameWithType> uygulaması.  
  
4.  Türün parametresiz `ToString` yöntemini geçersiz kılan <xref:System.Object.ToString?displayProperty=nameWithType> veya temel sınıfının davranışını devralan, çağrılır. Bu durumda, belirtilen biçim dizesi tarafından *formatString* bileşen biçim öğesinde varsa, göz ardı edilir.  
  
 Üstteki adımlar gerçekleştirildikten sonra hizalama uygulanır.  
  
## <a name="code-examples"></a>Kod Örnekleri  
 Aşağıdaki örnek, gösterir ve başka bir nesnenin kullanılarak oluşturulmuş bir bileşik biçimlendirme kullanılarak oluşturulan iki dizeyi `ToString` yöntemi. İki biçimlendirme türü de eşdeğer sonuçlar üretir.  
  
 [!code-csharp[Formatting.Composite#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#3)]
 [!code-vb[Formatting.Composite#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#3)]  
  
 Geçerli günün Mayıs ayında bir Perşembe olduğunu varsayarsak, yukarıdaki örnekte her iki dize değeri `Thursday May` ABD İngilizce kültürüne.  
  
 <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> aynı işlevselliği sunar <xref:System.String.Format%2A?displayProperty=nameWithType>. İki yöntem arasındaki tek fark <xref:System.String.Format%2A?displayProperty=nameWithType> sonucunu bir dize olarak döndürür ancak <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> yazma ile ilişkili çıkış akışına sonucu <xref:System.Console> nesne. Aşağıdaki örnekte <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> değerini biçimlendirmek için yöntemi `MyInt` bir para birimi değeri.  
  
 [!code-csharp[Formatting.Composite#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#4)]
 [!code-vb[Formatting.Composite#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#4)]  
  
 Aşağıdaki örnek birden çok nesneyi biçimlendirmeyi ve bir nesneyi iki farklı şekilde biçimlendirmeyi gösterir.  
  
 [!code-csharp[Formatting.Composite#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#5)]
 [!code-vb[Formatting.Composite#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#5)]  
  
 Aşağıdaki örnek biçimlendirmede hizalama kullanımını gösterir. Biçimlendirilen bağımsız değişkenler dikey çubuk karakterleri yerleştirilir (&#124;) sonuçta elde edilen hizalamayı vurgulamak için.  
  
 [!code-csharp[Formatting.Composite#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#6)]
 [!code-vb[Formatting.Composite#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#6)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Console.WriteLine%2A>
- <xref:System.String.Format%2A?displayProperty=nameWithType>
- [Dize ilişkilendirme (C#)](../../csharp/language-reference/tokens/interpolated.md)
- [Dize ilişkilendirme (Visual Basic)](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md)
- [Biçimlendirme Türleri](../../../docs/standard/base-types/formatting-types.md)
- [Standart Sayısal Biçim Dizeleri](../../../docs/standard/base-types/standard-numeric-format-strings.md)
- [Özel Sayısal Biçim Dizeleri](../../../docs/standard/base-types/custom-numeric-format-strings.md)
- [Standart Tarih ve Saat Biçim Dizeleri](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)
- [Özel Tarih ve Saat Biçim Dizeleri](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)
- [Standart TimeSpan Biçim Dizeleri](../../../docs/standard/base-types/standard-timespan-format-strings.md)
- [Özel TimeSpan Biçim Dizeleri](../../../docs/standard/base-types/custom-timespan-format-strings.md)
- [Sabit Listesi Biçim Dizeleri](../../../docs/standard/base-types/enumeration-format-strings.md)
