---
title: Bileşik biçimlendirme
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
ms.openlocfilehash: b1ec8cfc0f8c6e660d716c51bf3c3387b73a278f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79400346"
---
# <a name="composite-formatting"></a>Bileşik biçimlendirme

.NET bileşik biçimlendirme özelliği, nesnelerin bir listesini ve giriş olarak bileşik biçim dizesini alır. Bir bileşik biçimlendirme dizesi, sabit metinle karışık bir şekilde listedeki nesnelere karşılık gelen, biçim öğeleri adı verilen dizinli yer tutuculardan oluşur. Biçimlendirme işlemi sonuç olarak, orijinal sabit metin ve listedeki nesnelerin dize temsillerinin karışımından oluşan bir dize oluşturur.  
  
> [!IMPORTANT]
> Bileşik biçim dizeleri kullanmak yerine, kullandığınız dil ve dil sürümü bunları destekliyorsa *enterpolasyonlu dizeleri* kullanabilirsiniz. Enterpolasyonlu dize, *enterpolasyonlu ifadeleri*içeren bir dizedir. Her enterpolasyonlu ifade ifadenin değeri ile çözülür ve dize atandığında sonuç dizesinde yer. Daha fazla bilgi için String [enterpolasyonu (C# Reference)](../../csharp/language-reference/tokens/interpolated.md) ve [Enterpolasyonlu dizeleri (Visual Basic Reference)](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md)bakın.

Bileşik biçimlendirme özelliği aşağıdaki gibi yöntemler tarafından desteklenir:  
  
- <xref:System.String.Format%2A?displayProperty=nameWithType>, biçimlendirilmiş bir sonuç dizesi döndürür.  
  
- <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>, biçimlendirilmiş bir sonuç dizesini bir <xref:System.Text.StringBuilder> nesneye ekler.
- Konsola <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> biçimlendirilmiş bir sonuç dizesi görüntüleyen yöntemin bazı aşırı yükleri.  
  
- Biçimlendirilmiş sonuç <xref:System.IO.TextWriter.WriteLine%2A?displayProperty=nameWithType> dizesini bir akışa veya dosyaya yazan yöntemin bazı aşırı yükleri. Türetilen sınıflar <xref:System.IO.TextWriter>, <xref:System.IO.StreamWriter> gibi <xref:System.Web.UI.HtmlTextWriter>ve , ayrıca bu işlevselliği paylaşır.  
  
- <xref:System.Diagnostics.Debug.WriteLine%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>, dinleyicileri izlemek için biçimlendirilmiş bir ileti çıktırıyor.  
  
- İzleme <xref:System.Diagnostics.Trace.TraceError%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> <xref:System.Diagnostics.Trace.TraceInformation%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>dinleyicilerine <xref:System.Diagnostics.Trace.TraceWarning%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> iletileri biçimlendiren , ve yöntemler.  
  
- Dinleyicileri izlemek için bilgilendirici bir yöntem yazan <xref:System.Diagnostics.TraceSource.TraceInformation%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> yöntem.  
  
## <a name="composite-format-string"></a>Bileşik Biçim Dizesi  
 Bileşik biçimlendirme özelliğini destekleyen metotlarda bir bileşik biçimlendirme dizesi ve nesne listesi bağımsız değişkenler olarak kullanılır. Bir bileşik biçimlendirme dizesi sıfır veya daha fazla sabit metin bölümüyle karışık olarak bir veya daha fazla biçim öğesinden oluşur. Sabit metin seçtiğiniz herhangi bir dizedir, ve her biçim öğesi listedeki bir nesneye veya kutulu yapıya karşılık gelir. Bileşik biçimlendirme özelliği, her biçim öğesinin yerine listede karşılık gelen nesnenin dize temsili yerleştirilmiş bir şekilde yeni bir sonuç dizesi döndürür.  
  
 Aşağıdaki <xref:System.String.Format%2A> kod parçasını göz önünde bulundurun.  
  
 [!code-csharp[Formatting.Composite#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#1)]
 [!code-vb[Formatting.Composite#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#1)]  
  
 Sabit metin "`Name =` ve`, hours =` " dir. " Biçim öğeleri "`{0}`", dizini 0 olan, `name`nesneye`{1:hh}`karşılık gelen " ve " ", `DateTime.Now`dizin1 olan nesneye karşılık gelen .  
  
## <a name="format-item-syntax"></a>Biçim Öğesi Sözdizimi  
 Her biçim öğesi aşağıdaki biçimi alır ve aşağıdaki bileşenlerden oluşur:  
  
 `{`*dizin*`,`[`:`*hizalama*][*formatString*]`}`  
  
 Eşleşen ayraçlar ("{" ve "}") gereklidir.  
  
### <a name="index-component"></a>Dizin Bileşeni  
 Parametre belirtimi olarak da adlandırılan zorunlu *dizin* bileşeni, nesneler listesinde karşılık gelen bir maddeyi tanımlayan 0'dan başlayarak bir sayıdır. Yani, parametre tanımlayıcısı 0 olan biçim öğesi listedeki ilk nesneyi biçimlendirir, parametre tanımlayıcısı 1 olan biçim öğesi listedeki ikinci nesneyi biçimlendirir ve bu şekilde devam eder. Aşağıdaki örnekte, ondan küçük asal sayıları temsil etmek için sıfırdan üçe kadar numaralanmış dört parametre belirteçleri içerir:  
  
 [!code-csharp[Formatting.Composite#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/index1.cs#7)]
 [!code-vb[Formatting.Composite#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/index1.vb#7)]  
  
 Birden çok biçim öğesi, aynı parametre tanımlayıcısını belirterek nesne listesindeki aynı öğeye başvurabilir. Örneğin, aşağıdaki örnekte görüldüğü gibi : "0x{0:X} {0:E} {0:N}" gibi bir bileşik biçim dizesi belirterek hexadecimal, bilimsel ve sayı biçiminde aynı sayısal değeri biçimlendirebilirsiniz.  
  
 [!code-csharp[Formatting.Composite#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/index1.cs#10)]
 [!code-vb[Formatting.Composite#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/index1.vb#10)]  
  
 Her biçim öğesi listedeki herhangi bir nesneye başvurabilir. Örneğin, üç nesne varsa, aşağıdaki gibi bir bileşik biçim dizesi belirterek ikinci, birinci{1} {0} {2}ve üçüncü nesneyi biçimlendirebilirsiniz: " ". Bir biçimlendirme nesnesi tarafından başvurulmayan nesneler yok sayılır. Parametre belirteci, nesneler listesinin sınırları dışında bir öğe belirtirse, çalışma zamanında a <xref:System.FormatException> atılır.  
  
### <a name="alignment-component"></a>Hizalama Bileşeni  
 İsteğe bağlı *hizalama* bileşeni, tercih edilen biçimlendirilmiş alan genişliğini gösteren imzalı bir tamsayıdır. *Hizalama* değeri biçimlendirilmiş dize uzunluğundan daha azsa, *hizalama* yoksayılmaz ve biçimlendirilmiş dize uzunluğu alan genişliği olarak kullanılır. *Hizalama* pozitifse alandaki biçimlendirilmiş veriler sağ hizalanır ve *hizalama* negatifse sol hizalanır. Eğer iç boşluk gerekliyse, boşluk kullanılır. *Hizalama* belirtilmişse virgül gereklidir.  
  
 Aşağıdaki örnek, biri çalışanların adlarını, diğeri ise iki haftalık bir süre boyunca çalıştıkları saatleri içeren iki dizi tanımlar. Bileşik biçim dizesi, 20 karakterlik bir alandaki adları sola hizalar ve saatlerini 5 karakterlik bir alanda sağa hizalar. "N1" standart biçim dizesi de bir kesirli basamak ile saat biçimlendirmek için kullanılır unutmayın.  
  
 [!code-csharp[Formatting.Composite#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/alignment1.cs#8)]
 [!code-vb[Formatting.Composite#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/alignment1.vb#8)]  
  
### <a name="format-string-component"></a>Biçim Dizesi Bileşeni  
 İsteğe bağlı *biçimString* bileşeni biçimlendirilmekte olan nesne türüne uygun bir biçim dizesidir. Karşılık gelen nesne sayısal bir değerse standart veya özel sayısal biçim dizesi, ilgili nesne <xref:System.DateTime> bir nesneyse standart veya özel tarih ve saat biçimi dizesi veya karşılık gelen nesne numaralandırma değeriyse [numaralandırma biçimi dizesi](../../../docs/standard/base-types/enumeration-format-strings.md) belirtin. *FormatString* belirtilmemişse, sayısal, tarih ve saat veya numaralandırma türü için genel ("G") biçim belirtici kullanılır. *formatString belirtilirse* iki nokta üst üste gereklidir.  
  
 Aşağıdaki tablo, .NET Framework içinde bulunan, önceden tanımlanmış bir biçimlendirme dizesi kümesini destekleyen türleri ve kategorileri listeler, ve desteklenen biçimlendirme dizelerini listeleyen konulara bağlantılar sağlar. Dize biçimlendirmenin, tüm varolan türler için yeni biçimlendirme dizeleri tanımlanabilmesini mümkün kılmanın yanı sıra uygulamada tanımlanmış bir tür tarafından desteklenen bir biçimlendirme dizesi kümesinin tanımlanabilmesine olanak veren genişletilebilir bir mekanizma olduğuna dikkat edin. Daha fazla bilgi <xref:System.IFormattable> için, bkz. <xref:System.ICustomFormatter>  
  
|Tür veya tür kategorisi|Bkz.|  
|---------------------------|---------|  
|Tarih ve saat<xref:System.DateTime> <xref:System.DateTimeOffset>türleri ( , )|[Standart Tarih ve Saat Biçim Dizeleri](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)<br /><br /> [Özel Tarih ve Saat Biçim Dizeleri](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)|  
|Numaralandırma türleri (tüm türler) <xref:System.Enum?displayProperty=nameWithType>|[Numaralandırma Biçimi Dizeleri](../../../docs/standard/base-types/enumeration-format-strings.md)|  
|Sayısal tipler<xref:System.Numerics.BigInteger>( <xref:System.Byte> <xref:System.Decimal>, <xref:System.Double> <xref:System.Int16>, <xref:System.Int32> <xref:System.Int64>, <xref:System.SByte> <xref:System.Single>, <xref:System.UInt16> <xref:System.UInt32>, <xref:System.UInt64>, , , , , ,|[Standart Sayısal Biçim Dizeleri](../../../docs/standard/base-types/standard-numeric-format-strings.md)<br /><br /> [Özel Sayısal Biçim Dizeleri](../../../docs/standard/base-types/custom-numeric-format-strings.md)|  
|<xref:System.Guid>|<xref:System.Guid.ToString%28System.String%29?displayProperty=nameWithType>|  
|<xref:System.TimeSpan>|[Standart TimeSpan Biçim Dizeleri](../../../docs/standard/base-types/standard-timespan-format-strings.md)<br /><br /> [Özel TimeSpan Biçim Dizeleri](../../../docs/standard/base-types/custom-timespan-format-strings.md)|  
  
### <a name="escaping-braces"></a>Çıkış Yapan Ayraçlar  
 Açma ve kapatma ayraçları bir biçim öğesinin başlangıcı ve bitişi olarak yorumlanır. Sonuç olarak, sabit bir açılış veya kapanış ayracını görüntülemek için bir kaçış dizisi kullanmanız gerekir. Bir açılış ayracı ("{") görüntülemek için sabit metinde iki açılış ayracı ("{{"), veya bir kapanış ayracı ("}") görüntülemek için sabit metinde iki kapanış ayracı ("}}") belirtin. Bir biçim öğesindeki ayraçlar, karşılaşıldıkları sırada sıralı olarak yorumlanır. İç içe ayraçları yorumlama desteklenmez.  
  
 Kaçırılan ayraçların yorumlanma şekli beklenmeyen sonuçlara neden olabilir. Örneğin, bir açılış ayracı,{0:D}ondalık sayı olarak biçimlendirilmiş sayısal bir değer ve kapanış ayracı görüntülemek için tasarlanmış biçim öğesi "{{ }}" düşünün. Ancak, biçim öğesi aslında şu şekilde yorumlanır:  
  
1. İlk iki açılış ayracı ("{{") kaçırılır ve bir açılış ayracı olur.  
  
2. Sonraki üç karakter ("{0:") bir biçim öğesinin başlangıcı olarak yorumlanır.  
  
3. Sonraki karakter ("D") Ondalık standart sayısal biçim tanımlayıcısı olarak yorumlanır, ancak sonraki iki kaçırılan ayıraç ("}}") tek bir ayıraç olur. Sonuç dize ("D}") standart bir sayısal biçim tanımlayıcısı olmadığı için, sonuç dize özel bir biçimlendirme dizesi olarak yorumlanır ve bu nedenle "D}" sabit dizesini görüntüler.  
  
4. Son ayıraç ("}") biçim öğesinin bitişi olarak yorumlanır.  
  
5. Sonuç olarak "{D}" sabit dizesi görüntülenir. Biçimlendirilmek istenen sayısal değer görüntülenmez.  
  
 Kodunuzun kaçırılan ayraçları ve format öğelerini yanlış yorumlamasından kaçınmanın bir yolu, ayraçları ve biçim öğesini ayrı olarak biçimlendirmektir. Yani, ilk biçimlendirme işleminde bir sabit açılış ayracı görüntülemek, sonraki işlemde biçim öğesinin sonucunu görüntülemek ve son işlemde de bir sabit kapanış ayracı görüntülemektir. Aşağıdaki örnek bu yaklaşımı gösterir.  
  
 [!code-csharp[Formatting.Composite#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Escaping1.cs#2)]
 [!code-vb[Formatting.Composite#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Escaping1.vb#2)]  
  
### <a name="processing-order"></a>İşlem Sırası  
 <xref:System.IFormatProvider> Bileşik biçimlendirme yöntemine yapılan çağrı, değeri olmayan `null`bir bağımsız değişken <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> içeriyorsa, çalışma zamanı <xref:System.ICustomFormatter> bir uygulama istemek için yöntemini çağırır. Yöntem bir <xref:System.ICustomFormatter> uygulamayı döndürebiliyorsa, bileşik biçimlendirme yönteminin çağrı süresi boyunca önbelleğe alınmış olur.
  
 Bir biçim öğesine karşılık gelen parametre listesindeki her değer aşağıdaki gibi bir dize dönüştürülür:  
  
1. Biçimlendirilecek değer ise, `null`boş <xref:System.String.Empty?displayProperty=nameWithType> bir dize döndürülür.  
  
2. Bir <xref:System.ICustomFormatter> uygulama varsa, çalışma zamanı <xref:System.ICustomFormatter.Format%2A> yöntemini çağırır. Bir tane varsa veya `null` <xref:System.IFormatProvider> yoksa, uygulama ile birlikte biçim öğesinin biçim *öğesinin biçimString* değerini yönteme geçirir. <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> Yönteme çağrı dönerse, `null`yürütme bir sonraki adıma devam eder; aksi takdirde, <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> arama sonucu döndürülür.
  
3. Değer <xref:System.IFormattable> arabirimi uygularsa, arabirimin <xref:System.IFormattable.ToString%28System.String%2CSystem.IFormatProvider%29> yöntemi çağrılır. Yöntem, biçim öğesinde varsa veya `null` yoksa *biçimString* değerine geçirilir. Bağımsız <xref:System.IFormatProvider> değişken aşağıdaki gibi belirlenir:  
  
    - Sayısal bir değer için, null <xref:System.IFormatProvider> olmayan bağımsız değişkeni olan bileşik biçimlendirme yöntemi <xref:System.Globalization.NumberFormatInfo> çağrılırsa, çalışma zamanı bir nesneyi <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> yönteminden ister. Bir tane sağlayamıyorsa, bağımsız değişkenin `null`değeri ise veya bileşik biçimlendirme yönteminde <xref:System.IFormatProvider> parametre yoksa, <xref:System.Globalization.NumberFormatInfo> geçerli iş parçacığı kültürü nesnesi kullanılır.  
  
    - Tarih ve saat değeri için, null <xref:System.IFormatProvider> olmayan bağımsız değişkeniçeren bileşik biçimlendirme yöntemi <xref:System.Globalization.DateTimeFormatInfo> çağrılırsa, çalışma zamanı bir nesneyi <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> yönteminden ister. Bir tane sağlayamıyorsa, bağımsız değişkenin `null`değeri ise veya bileşik biçimlendirme yönteminde <xref:System.IFormatProvider> parametre yoksa, <xref:System.Globalization.DateTimeFormatInfo> geçerli iş parçacığı kültürü nesnesi kullanılır.  
  
    - Diğer türlerdeki nesneler için, bileşik biçimlendirme yöntemi <xref:System.IFormatProvider> bir bağımsız değişkenle çağrılırsa, değeri doğrudan <xref:System.IFormattable.ToString%2A?displayProperty=nameWithType> uygulamaya aktarılır. Aksi `null` takdirde, <xref:System.IFormattable.ToString%2A?displayProperty=nameWithType> uygulamaya geçirilir.  
  
4. Türün taban sınıfının `ToString` davranışını geçersiz <xref:System.Object.ToString?displayProperty=nameWithType> kılan veya devralan parametresiz yöntemi çağrılır. Bu durumda, biçim öğesindeki *biçimString* bileşeni tarafından belirtilen biçim dizesi, varsa yoksayılır.  
  
 Üstteki adımlar gerçekleştirildikten sonra hizalama uygulanır.  
  
## <a name="code-examples"></a>Kod Örnekleri  
 Aşağıdaki örnekte, bileşik biçimlendirme kullanılarak oluşturulan bir dize `ToString` ve nesnenin yöntemi kullanılarak oluşturulan başka bir dize gösterilmektedir. İki biçimlendirme türü de eşdeğer sonuçlar üretir.  
  
 [!code-csharp[Formatting.Composite#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#3)]
 [!code-vb[Formatting.Composite#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#3)]  
  
 Geçerli günün Mayıs ayında bir Perşembe olduğunu varsayarsak, önceki örnekteki `Thursday May` her iki dizenin değeri ABD İngilizce kültüründedir.  
  
 <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>ile aynı işlevselliği <xref:System.String.Format%2A?displayProperty=nameWithType>ortaya çıkarır. İki yöntem arasındaki tek fark, sonucu <xref:System.String.Format%2A?displayProperty=nameWithType> <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> <xref:System.Console> nesneyle ilişkili çıkış akışına yazarken sonucu bir dize olarak döndürür. Aşağıdaki örnekte, <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> para birimi `MyInt` değerine değer biçimlendirmek için yöntem kullanır.  
  
 [!code-csharp[Formatting.Composite#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#4)]
 [!code-vb[Formatting.Composite#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#4)]  
  
 Aşağıdaki örnek birden çok nesneyi biçimlendirmeyi ve bir nesneyi iki farklı şekilde biçimlendirmeyi gösterir.  
  
 [!code-csharp[Formatting.Composite#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#5)]
 [!code-vb[Formatting.Composite#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#5)]  
  
 Aşağıdaki örnek biçimlendirmede hizalama kullanımını gösterir. Biçimlendirilmiş bağımsız değişkenler, elde edilen hizalamayı vurgulamak için dikey çubuk karakterler (&#124;) arasına yerleştirilir.  
  
 [!code-csharp[Formatting.Composite#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#6)]
 [!code-vb[Formatting.Composite#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#6)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Console.WriteLine%2A>
- <xref:System.String.Format%2A?displayProperty=nameWithType>
- [Dize enterpolasyonu (C#)](../../csharp/language-reference/tokens/interpolated.md)
- [Dize enterpolasyonu (Visual Basic)](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md)
- [Biçimlendirme Türleri](../../../docs/standard/base-types/formatting-types.md)
- [Standart Sayısal Biçim Dizeleri](../../../docs/standard/base-types/standard-numeric-format-strings.md)
- [Özel Sayısal Biçim Dizeleri](../../../docs/standard/base-types/custom-numeric-format-strings.md)
- [Standart Tarih ve Saat Biçim Dizeleri](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)
- [Özel Tarih ve Saat Biçim Dizeleri](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)
- [Standart TimeSpan Biçim Dizeleri](../../../docs/standard/base-types/standard-timespan-format-strings.md)
- [Özel TimeSpan Biçim Dizeleri](../../../docs/standard/base-types/custom-timespan-format-strings.md)
- [Numaralandırma Biçimi Dizeleri](../../../docs/standard/base-types/enumeration-format-strings.md)
