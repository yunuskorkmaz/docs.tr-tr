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
ms.openlocfilehash: 12666ca5ad8f223f2fba4a63a7cc7525601367a2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73091567"
---
# <a name="composite-formatting"></a>Bileşik Biçimlendirme

.NET Composite biçimlendirme özelliği, giriş olarak bir nesne listesi ve bileşik biçim dizesi alır. Bir bileşik biçimlendirme dizesi, sabit metinle karışık bir şekilde listedeki nesnelere karşılık gelen, biçim öğeleri adı verilen dizinli yer tutuculardan oluşur. Biçimlendirme işlemi sonuç olarak, orijinal sabit metin ve listedeki nesnelerin dize temsillerinin karışımından oluşan bir dize oluşturur.  
  
> [!IMPORTANT]
> Kullandığınız dil ve dil sürümü bunları destekliyorsa, bileşik biçim dizeleri kullanmak yerine, *enterpolasyonlu dizeler* kullanabilirsiniz. Enterpolasyonlu dize, *enterpolasyonlu ifadeler*içeren bir dizedir. Her bir enterpolasyonlu ifade, ifadenin değeri ile çözümlenir ve dize atandığında sonuç dizesine dahil edilir. Daha fazla bilgi için bkz. [dize ilişkilendirmeC# (başvuru)](../../csharp/language-reference/tokens/interpolated.md) ve [enterpolasyonlu dizeler (Visual Basic Başvurusu)](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md).

Bileşik biçimlendirme özelliği aşağıdaki gibi yöntemler tarafından desteklenir:  
  
- biçimlendirilen bir sonuç dizesi döndüren <xref:System.String.Format%2A?displayProperty=nameWithType>.  
  
- <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>, bir <xref:System.Text.StringBuilder> nesnesine biçimlendirilen bir sonuç dizesi ekler.   
- Konsola biçimlendirilen bir sonuç dizesi görüntüleyen <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> yönteminin bazı aşırı yüklemeleri.  
  
- <xref:System.IO.TextWriter.WriteLine%2A?displayProperty=nameWithType> yönteminin bazı aşırı yüklemeleri, biçimlendirilen sonuç dizesini bir akışa veya dosyaya yazar. <xref:System.IO.StreamWriter> ve <xref:System.Web.UI.HtmlTextWriter>gibi <xref:System.IO.TextWriter>türetilen sınıflar da bu işlevi paylaşır.  
  
- <xref:System.Diagnostics.Debug.WriteLine%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>, dinleyicileri izlemek için biçimlendirilen bir ileti verir.  
  
- <xref:System.Diagnostics.Trace.TraceError%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.TraceInformation%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>ve <xref:System.Diagnostics.Trace.TraceWarning%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> yöntemleri, bu, izleme dinleyicilerine yönelik biçimlendirilen iletileri çıktı.  
  
- İzleme dinleyicilerine bir bilgilendirme yöntemi yazan <xref:System.Diagnostics.TraceSource.TraceInformation%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> yöntemi.  
  
## <a name="composite-format-string"></a>Bileşik Biçim Dizesi  
 Bileşik biçimlendirme özelliğini destekleyen metotlarda bir bileşik biçimlendirme dizesi ve nesne listesi bağımsız değişkenler olarak kullanılır. Bir bileşik biçimlendirme dizesi sıfır veya daha fazla sabit metin bölümüyle karışık olarak bir veya daha fazla biçim öğesinden oluşur. Sabit metin seçtiğiniz herhangi bir dizedir, ve her biçim öğesi listedeki bir nesneye veya kutulu yapıya karşılık gelir. Bileşik biçimlendirme özelliği, her biçim öğesinin yerine listede karşılık gelen nesnenin dize temsili yerleştirilmiş bir şekilde yeni bir sonuç dizesi döndürür.  
  
 Aşağıdaki <xref:System.String.Format%2A> kod parçasını göz önünde bulundurun.  
  
 [!code-csharp[Formatting.Composite#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#1)]
 [!code-vb[Formatting.Composite#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#1)]  
  
 Sabit metin, "`Name =`" ve "`, hours =`". Biçim öğeleri, dizini 0 olan ve nesne `DateTime.Now`karşılık gelen dizin 1 olan ve "`{1:hh}`" olan "`{0}`" `name`.  
  
## <a name="format-item-syntax"></a>Biçim Öğesi Sözdizimi  
 Her biçim öğesi aşağıdaki biçimi alır ve aşağıdaki bileşenlerden oluşur:  
  
 *dizin*`{` [`,`*hizalaması*] [`:`*FormatString*]`}`  
  
 Eşleşen ayraçlar ("{" ve "}") gereklidir.  
  
### <a name="index-component"></a>Dizin Bileşeni  
 Parametre tanımlayıcısı olarak da bilinen zorunlu *Dizin* bileşeni, nesne listesinde karşılık gelen bir öğeyi tanımlayan 0 ' dan başlayan bir sayıdır. Yani, parametre tanımlayıcısı 0 olan biçim öğesi listedeki ilk nesneyi biçimlendirir, parametre tanımlayıcısı 1 olan biçim öğesi listedeki ikinci nesneyi biçimlendirir ve bu şekilde devam eder. Aşağıdaki örnek, 10 ' dan küçük olan asal sayıları temsil etmek için, sıfır ile numaralandırılmış dört parametre belirticilerini içerir:  
  
 [!code-csharp[Formatting.Composite#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/index1.cs#7)]
 [!code-vb[Formatting.Composite#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/index1.vb#7)]  
  
 Birden çok biçim öğesi, aynı parametre tanımlayıcısını belirterek nesne listesindeki aynı öğeye başvurabilir. Örneğin, aşağıdaki örnekte gösterildiği gibi, "0x{0:X} {0:E} {0:N}" gibi bir bileşik biçim dizesi belirterek, onaltılık, bilimsel ve sayı biçimindeki aynı sayısal değeri biçimlendirebilirsiniz.  
  
 [!code-csharp[Formatting.Composite#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/index1.cs#10)]
 [!code-vb[Formatting.Composite#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/index1.vb#10)]  
  
 Her biçim öğesi listedeki herhangi bir nesneye başvurabilir. Örneğin, üç nesne varsa, şu şekilde bir bileşik biçim dizesi belirterek ikinci, birinci ve üçüncü nesneyi biçimlendirebilirsiniz: "{1} {0} {2}". Bir biçimlendirme nesnesi tarafından başvurulmayan nesneler yok sayılır. Bir parametre belirleyicisi nesne listesi sınırları dışında bir öğe atılırsa, çalışma zamanında bir <xref:System.FormatException> oluşturulur.  
  
### <a name="alignment-component"></a>Hizalama Bileşeni  
 İsteğe bağlı *Hizalama* bileşeni, tercih edilen biçimli alan genişliğini gösteren işaretli bir tamsayıdır. *Hizalama* değeri biçimlendirilen dizenin uzunluğundan küçükse, *Hizalama* yok sayılır ve biçimlendirilen dizenin uzunluğu alan genişliği olarak kullanılır. *Hizalama* pozitif ise ve *Hizalama* negatifse sola hizalı ise, alandaki biçimlendirilen veriler sağa hizalanır. Eğer iç boşluk gerekliyse, boşluk kullanılır. *Hizalama* belirtilmişse virgül gereklidir.  
  
 Aşağıdaki örnek, biri çalışanların adlarını ve diğeri iki haftalık bir dönemde çalıştıkları saatleri içeren iki diziyi tanımlar. Bileşik biçim dizesi, adları 20 karakterlik bir alana sola hizalar ve saatlerini 5 karakterli bir alanda sağa hizalar. "N1" standart biçim dizesinin aynı zamanda bir kesirli basamaklı saatleri biçimlendirmek için de kullanıldığını unutmayın.  
  
 [!code-csharp[Formatting.Composite#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/alignment1.cs#8)]
 [!code-vb[Formatting.Composite#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/alignment1.vb#8)]  
  
### <a name="format-string-component"></a>Biçim Dizesi Bileşeni  
 İsteğe bağlı *FormatString* bileşeni, biçimlendirilen nesne türüne uygun bir biçim dizesidir. Karşılık gelen nesne bir sayısal değer ise standart veya özel bir sayısal biçim dizesi, karşılık gelen nesne bir <xref:System.DateTime> nesne ise standart veya özel tarih ve saat [biçimi dizesi ya](../../../docs/standard/base-types/enumeration-format-strings.md) da karşılık gelen nesne bir sabit listesi değeridir. *FormatString* belirtilmemişse, bir sayısal, tarih ve saat veya numaralandırma türü için genel ("G") Biçim belirleyicisi kullanılır. *FormatString* belirtilmişse, iki nokta üst üste gereklidir.  
  
 Aşağıdaki tablo, .NET Framework içinde bulunan, önceden tanımlanmış bir biçimlendirme dizesi kümesini destekleyen türleri ve kategorileri listeler, ve desteklenen biçimlendirme dizelerini listeleyen konulara bağlantılar sağlar. Dize biçimlendirmenin, tüm varolan türler için yeni biçimlendirme dizeleri tanımlanabilmesini mümkün kılmanın yanı sıra uygulamada tanımlanmış bir tür tarafından desteklenen bir biçimlendirme dizesi kümesinin tanımlanabilmesine olanak veren genişletilebilir bir mekanizma olduğuna dikkat edin. Daha fazla bilgi için <xref:System.IFormattable> ve <xref:System.ICustomFormatter> arabirimi konularına bakın.  
  
|Tür veya tür kategorisi|Bkz.|  
|---------------------------|---------|  
|Tarih ve saat türleri (<xref:System.DateTime>, <xref:System.DateTimeOffset>)|[Standart Tarih ve Saat Biçim Dizeleri](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)<br /><br /> [Özel Tarih ve Saat Biçim Dizeleri](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)|  
|Sabit listesi türleri (<xref:System.Enum?displayProperty=nameWithType>türetilen tüm türler)|[Sabit Listesi Biçim Dizeleri](../../../docs/standard/base-types/enumeration-format-strings.md)|  
|Sayısal türler (<xref:System.Numerics.BigInteger>, <xref:System.Byte>, <xref:System.Decimal>, <xref:System.Double>, <xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.SByte>, <xref:System.Single>, <xref:System.UInt16>, <xref:System.UInt32>, <xref:System.UInt64>)|[Standart Sayısal Biçim Dizeleri](../../../docs/standard/base-types/standard-numeric-format-strings.md)<br /><br /> [Özel Sayısal Biçim Dizeleri](../../../docs/standard/base-types/custom-numeric-format-strings.md)|  
|<xref:System.Guid>|<xref:System.Guid.ToString%28System.String%29?displayProperty=nameWithType>|  
|<xref:System.TimeSpan>|[Standart TimeSpan Biçim Dizeleri](../../../docs/standard/base-types/standard-timespan-format-strings.md)<br /><br /> [Özel TimeSpan Biçim Dizeleri](../../../docs/standard/base-types/custom-timespan-format-strings.md)|  
  
### <a name="escaping-braces"></a>Çıkış Yapan Ayraçlar  
 Açma ve kapatma ayraçları bir biçim öğesinin başlangıcı ve bitişi olarak yorumlanır. Sonuç olarak, sabit bir açılış veya kapanış ayracını görüntülemek için bir kaçış dizisi kullanmanız gerekir. Bir açılış ayracı ("{") görüntülemek için sabit metinde iki açılış ayracı ("{{"), veya bir kapanış ayracı ("}") görüntülemek için sabit metinde iki kapanış ayracı ("}}") belirtin. Bir biçim öğesindeki ayraçlar, karşılaşıldıkları sırada sıralı olarak yorumlanır. İç içe ayraçları yorumlama desteklenmez.  
  
 Kaçırılan ayraçların yorumlanma şekli beklenmeyen sonuçlara neden olabilir. Örneğin, bir açılış ayracı, ondalık sayı olarak biçimlendirilen sayısal bir değer ve bir kapanış ayracı görüntülemesi amaçlanan "{{{0:D}}}" biçim öğesini düşünün. Ancak, biçim öğesi aslında şu şekilde yorumlanır:  
  
1. İlk iki açılış ayracı ("{{") kaçırılır ve bir açılış ayracı olur.  
  
2. Sonraki üç karakter ("{0:") bir biçim öğesinin başlangıcı olarak yorumlanır.  
  
3. Sonraki karakter ("D") Ondalık standart sayısal biçim tanımlayıcısı olarak yorumlanır, ancak sonraki iki kaçırılan ayıraç ("}}") tek bir ayıraç olur. Sonuç dize ("D}") standart bir sayısal biçim tanımlayıcısı olmadığı için, sonuç dize özel bir biçimlendirme dizesi olarak yorumlanır ve bu nedenle "D}" sabit dizesini görüntüler.  
  
4. Son ayıraç ("}") biçim öğesinin bitişi olarak yorumlanır.  
  
5. Sonuç olarak "{D}" sabit dizesi görüntülenir. Biçimlendirilmek istenen sayısal değer görüntülenmez.  
  
 Kodunuzun kaçırılan ayraçları ve format öğelerini yanlış yorumlamasından kaçınmanın bir yolu, ayraçları ve biçim öğesini ayrı olarak biçimlendirmektir. Yani, ilk biçimlendirme işleminde bir sabit açılış ayracı görüntülemek, sonraki işlemde biçim öğesinin sonucunu görüntülemek ve son işlemde de bir sabit kapanış ayracı görüntülemektir. Aşağıdaki örnek bu yaklaşımı gösterir.  
  
 [!code-csharp[Formatting.Composite#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Escaping1.cs#2)]
 [!code-vb[Formatting.Composite#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Escaping1.vb#2)]  
  
### <a name="processing-order"></a>İşlem Sırası  
 Bileşik biçimlendirme yöntemine yapılan çağrı, değeri `null`olmayan bir <xref:System.IFormatProvider> bağımsız değişkeni içeriyorsa, çalışma zamanı <xref:System.ICustomFormatter> bir uygulama istemek için <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> yöntemini çağırır. Yöntem <xref:System.ICustomFormatter> bir uygulama döndürebiliyor ise, bileşik biçimlendirme yöntemi çağrısının süresi boyunca önbelleğe alınır.
  
 Bir biçim öğesine karşılık gelen parametre listesindeki her bir değer, aşağıdaki gibi bir dizeye dönüştürülür:  
  
1. Biçimlendirilecek değer `null`, boş bir dize <xref:System.String.Empty?displayProperty=nameWithType> döndürülür.  
  
2. <xref:System.ICustomFormatter> bir uygulama kullanılabiliyorsa, çalışma zamanı <xref:System.ICustomFormatter.Format%2A> yöntemini çağırır. Yöntemi, varsa biçim öğesinin *FormatString* değerini, varsa, <xref:System.IFormatProvider> uygulamasıyla birlikte `null` geçirir. <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> yöntemine yapılan çağrı `null`döndürürse, yürütme sonraki adıma geçer; Aksi takdirde, <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> çağrısının sonucu döndürülür.
  
3. Değer <xref:System.IFormattable> arabirimini uyguluyorsa, arabirimin <xref:System.IFormattable.ToString%28System.String%2CSystem.IFormatProvider%29> yöntemi çağırılır. Yöntemi, biçim öğesinde varsa veya yoksa `null`, *FormatString* değeri geçirilir. <xref:System.IFormatProvider> bağımsız değişkeni aşağıdaki gibi belirlenir:  
  
    - Sayısal bir değer için, null olmayan <xref:System.IFormatProvider> bağımsız değişkenine sahip bir bileşik biçimlendirme yöntemi çağrılırsa, çalışma zamanı <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> yönteminden bir <xref:System.Globalization.NumberFormatInfo> nesnesi ister. Bir tane sağlayamazsa, bağımsız değişkenin değeri `null`, ya da bileşik biçimlendirme yönteminin bir <xref:System.IFormatProvider> parametresi yoksa, geçerli iş parçacığı kültürü için <xref:System.Globalization.NumberFormatInfo> nesnesi kullanılır.  
  
    - Bir tarih ve saat değeri için, null olmayan <xref:System.IFormatProvider> bağımsız değişkenine sahip bir bileşik biçimlendirme yöntemi çağrılırsa, çalışma zamanı <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> yönteminden bir <xref:System.Globalization.DateTimeFormatInfo> nesnesi ister. Bir tane sağlayamazsa, bağımsız değişkenin değeri `null`, ya da bileşik biçimlendirme yönteminin bir <xref:System.IFormatProvider> parametresi yoksa, geçerli iş parçacığı kültürü için <xref:System.Globalization.DateTimeFormatInfo> nesnesi kullanılır.  
  
    - Diğer türlerin nesneleri için, bir <xref:System.IFormatProvider> bağımsız değişkeniyle bir bileşik biçimlendirme yöntemi çağrılırsa, değeri doğrudan <xref:System.IFormattable.ToString%2A?displayProperty=nameWithType> uygulamasına geçirilir. Aksi takdirde, `null` <xref:System.IFormattable.ToString%2A?displayProperty=nameWithType> uygulamasına geçirilir.  
  
4. Türün parametresiz `ToString` yöntemi, <xref:System.Object.ToString?displayProperty=nameWithType> ya da kendi temel sınıfının davranışını devralır, çağrılır. Bu durumda, biçim öğesinde *FormatString* bileşeni tarafından belirtilen biçim dizesi varsa, yok sayılır.  
  
 Üstteki adımlar gerçekleştirildikten sonra hizalama uygulanır.  
  
## <a name="code-examples"></a>Kod Örnekleri  
 Aşağıdaki örnekte, bileşik biçimlendirme kullanılarak oluşturulan bir dize ve bir nesnenin `ToString` yöntemi kullanılarak oluşturulan bir dize gösterilmektedir. İki biçimlendirme türü de eşdeğer sonuçlar üretir.  
  
 [!code-csharp[Formatting.Composite#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#3)]
 [!code-vb[Formatting.Composite#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#3)]  
  
 Geçerli günün Mayıs değerindeki bir Perşembe olduğunu varsayarsak, yukarıdaki örnekteki her iki dizenin da değeri ABD Ingilizcesi kültür ' de `Thursday May`.  
  
 <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, <xref:System.String.Format%2A?displayProperty=nameWithType>aynı işlevselliği kullanıma sunar. İki yöntem arasındaki tek fark, <xref:System.String.Format%2A?displayProperty=nameWithType> sonucunu bir dize olarak döndürdüğünden, <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> sonucu <xref:System.Console> nesnesiyle ilişkili çıkış akışına yazar. Aşağıdaki örnek, `MyInt` değerini bir para birimi değerine biçimlendirmek için <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> yöntemini kullanır.  
  
 [!code-csharp[Formatting.Composite#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#4)]
 [!code-vb[Formatting.Composite#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#4)]  
  
 Aşağıdaki örnek birden çok nesneyi biçimlendirmeyi ve bir nesneyi iki farklı şekilde biçimlendirmeyi gösterir.  
  
 [!code-csharp[Formatting.Composite#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#5)]
 [!code-vb[Formatting.Composite#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#5)]  
  
 Aşağıdaki örnek biçimlendirmede hizalama kullanımını gösterir. Biçimlendirilen bağımsız değişkenler, ortaya çıkan hizalamayı vurgulamak için dikey çubuk karakterleri&#124;() arasına yerleştirilir.  
  
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
