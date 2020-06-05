---
title: Bileşik biçimlendirme
description: Bir nesne listesi ve Birleşik biçim dizesi olarak alan ve dizinli yer tutucuları olan sabit metin içeren .NET bileşik biçimlendirmesi hakkında bilgi edinin.
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
ms.openlocfilehash: 36197b382c449a2570e1d5530f307c4e66b0d983
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/05/2020
ms.locfileid: "84447270"
---
# <a name="composite-formatting"></a>Bileşik biçimlendirme

.NET Composite biçimlendirme özelliği, giriş olarak bir nesne listesi ve bileşik biçim dizesi alır. Bir bileşik biçimlendirme dizesi, sabit metinle karışık bir şekilde listedeki nesnelere karşılık gelen, biçim öğeleri adı verilen dizinli yer tutuculardan oluşur. Biçimlendirme işlemi sonuç olarak, orijinal sabit metin ve listedeki nesnelerin dize temsillerinin karışımından oluşan bir dize oluşturur.  
  
> [!IMPORTANT]
> Kullandığınız dil ve dil sürümü bunları destekliyorsa, bileşik biçim dizeleri kullanmak yerine, *enterpolasyonlu dizeler* kullanabilirsiniz. Enterpolasyonlu dize, *enterpolasyonlu ifadeler*içeren bir dizedir. Her bir enterpolasyonlu ifade, ifadenin değeri ile çözümlenir ve dize atandığında sonuç dizesine dahil edilir. Daha fazla bilgi için bkz. [dize ilişkilendirme (C# Başvurusu)](../../csharp/language-reference/tokens/interpolated.md) ve [enterpolasyonlu dizeler (Visual Basic Başvurusu)](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md).

Bileşik biçimlendirme özelliği aşağıdaki gibi yöntemler tarafından desteklenir:  
  
- <xref:System.String.Format%2A?displayProperty=nameWithType>, ancak biçimlendirilen bir sonuç dizesi döndürür.  
  
- <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>, bir nesnesine biçimlendirilen bir sonuç dizesi ekler <xref:System.Text.StringBuilder> .
- <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>Konsola biçimlendirilen bir sonuç dizesi görüntüleyen metodun bazı aşırı yüklemeleri.  
  
- <xref:System.IO.TextWriter.WriteLine%2A?displayProperty=nameWithType>Bir akışa veya dosyaya biçimlendirilen sonuç dizesini yazan, metodun bazı aşırı yüklemeleri. Ve gibi sınıfından türetilmiş sınıflar <xref:System.IO.TextWriter> <xref:System.IO.StreamWriter> <xref:System.Web.UI.HtmlTextWriter> da bu işlevi paylaşır.  
  
- <xref:System.Diagnostics.Debug.WriteLine%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>, dinleyicileri izlemek için biçimlendirilen bir ileti çıkışı verir.  
  
- <xref:System.Diagnostics.Trace.TraceError%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.TraceInformation%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> Ve ' i <xref:System.Diagnostics.Trace.TraceWarning%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> izlemek için biçimlendirilen iletileri çıktısını veren, ve yöntemleri.  
  
- <xref:System.Diagnostics.TraceSource.TraceInformation%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>Trace dinleyicilerine bir bilgilendirme yöntemi yazan yöntemi.  
  
## <a name="composite-format-string"></a>Bileşik Biçim Dizesi  
 Bileşik biçimlendirme özelliğini destekleyen metotlarda bir bileşik biçimlendirme dizesi ve nesne listesi bağımsız değişkenler olarak kullanılır. Bir bileşik biçimlendirme dizesi sıfır veya daha fazla sabit metin bölümüyle karışık olarak bir veya daha fazla biçim öğesinden oluşur. Sabit metin seçtiğiniz herhangi bir dizedir, ve her biçim öğesi listedeki bir nesneye veya kutulu yapıya karşılık gelir. Bileşik biçimlendirme özelliği, her biçim öğesinin yerine listede karşılık gelen nesnenin dize temsili yerleştirilmiş bir şekilde yeni bir sonuç dizesi döndürür.  
  
 Aşağıdaki kod parçasını göz önünde bulundurun <xref:System.String.Format%2A> .  
  
 [!code-csharp[Formatting.Composite#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#1)]
 [!code-vb[Formatting.Composite#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#1)]  
  
 Sabit metin " `Name =` " ve " `, hours =` ". Biçim öğeleri, `{0}` dizini 0 olan, nesnesine karşılık gelen "" `name` ve dizini 1 olan, nesnesine karşılık gelen "" olan "" dir `{1:hh}` `DateTime.Now` .  
  
## <a name="format-item-syntax"></a>Biçim Öğesi Sözdizimi  
 Her biçim öğesi aşağıdaki biçimi alır ve aşağıdaki bileşenlerden oluşur:  
  
 `{`*Dizin*[ `,` *Hizalama*] [ `:` *FormatString*]`}`  
  
 Eşleşen ayraçlar ("{" ve "}") gereklidir.  
  
### <a name="index-component"></a>Dizin Bileşeni  
 Parametre tanımlayıcısı olarak da bilinen zorunlu *Dizin* bileşeni, nesne listesinde karşılık gelen bir öğeyi tanımlayan 0 ' dan başlayan bir sayıdır. Yani, parametre tanımlayıcısı 0 olan biçim öğesi listedeki ilk nesneyi biçimlendirir, parametre tanımlayıcısı 1 olan biçim öğesi listedeki ikinci nesneyi biçimlendirir ve bu şekilde devam eder. Aşağıdaki örnek, 10 ' dan küçük olan asal sayıları temsil etmek için, sıfır ile numaralandırılmış dört parametre belirticilerini içerir:  
  
 [!code-csharp[Formatting.Composite#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/index1.cs#7)]
 [!code-vb[Formatting.Composite#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/index1.vb#7)]  
  
 Birden çok biçim öğesi, aynı parametre tanımlayıcısını belirterek nesne listesindeki aynı öğeye başvurabilir. Örneğin, aşağıdaki örnekte gösterildiği gibi bir bileşik biçim dizesi belirterek onaltılık, bilimsel ve sayı biçiminde aynı sayısal değeri biçimlendirebilirsiniz: "0x {0:X} {0:E} {0:N} ".  
  
 [!code-csharp[Formatting.Composite#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/index1.cs#10)]
 [!code-vb[Formatting.Composite#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/index1.vb#10)]  
  
 Her biçim öğesi listedeki herhangi bir nesneye başvurabilir. Örneğin, üç nesne varsa, şu şekilde bir bileşik biçim dizesi belirterek ikinci, birinci ve üçüncü nesneyi biçimlendirebilirsiniz: " {1} {0} {2} ". Bir biçimlendirme nesnesi tarafından başvurulmayan nesneler yok sayılır. Bir <xref:System.FormatException> parametre Belirleyicisi, nesne listesi sınırları dışında bir öğe tasarladığı zaman çalışma zamanında oluşturulur.  
  
### <a name="alignment-component"></a>Hizalama Bileşeni  
 İsteğe bağlı *Hizalama* bileşeni, tercih edilen biçimli alan genişliğini gösteren işaretli bir tamsayıdır. *Hizalama* değeri biçimlendirilen dizenin uzunluğundan küçükse, *Hizalama* yok sayılır ve biçimlendirilen dizenin uzunluğu alan genişliği olarak kullanılır. *Hizalama* pozitif ise ve *Hizalama* negatifse sola hizalı ise, alandaki biçimlendirilen veriler sağa hizalanır. Eğer iç boşluk gerekliyse, boşluk kullanılır. *Hizalama* belirtilmişse virgül gereklidir.  
  
 Aşağıdaki örnek, biri çalışanların adlarını ve diğeri iki haftalık bir dönemde çalıştıkları saatleri içeren iki diziyi tanımlar. Bileşik biçim dizesi, adları 20 karakterlik bir alana sola hizalar ve saatlerini 5 karakterli bir alanda sağa hizalar. "N1" standart biçim dizesinin aynı zamanda bir kesirli basamaklı saatleri biçimlendirmek için de kullanıldığını unutmayın.  
  
 [!code-csharp[Formatting.Composite#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/alignment1.cs#8)]
 [!code-vb[Formatting.Composite#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/alignment1.vb#8)]  
  
### <a name="format-string-component"></a>Biçim Dizesi Bileşeni  
 İsteğe bağlı *FormatString* bileşeni, biçimlendirilen nesne türüne uygun bir biçim dizesidir. Karşılık gelen nesne bir sayısal değer ise standart veya özel sayısal biçim dizesi, karşılık gelen nesne bir nesne ise standart veya özel tarih ve saat biçimi dizesi <xref:System.DateTime> ya da karşılık gelen nesne bir numaralandırma değeri ise bir [numaralandırma biçim dizesi](enumeration-format-strings.md) belirtin. *FormatString* belirtilmemişse, bir sayısal, tarih ve saat veya numaralandırma türü için genel ("G") Biçim belirleyicisi kullanılır. *FormatString* belirtilmişse, iki nokta üst üste gereklidir.  
  
 Aşağıdaki tablo, .NET Framework içinde bulunan, önceden tanımlanmış bir biçimlendirme dizesi kümesini destekleyen türleri ve kategorileri listeler, ve desteklenen biçimlendirme dizelerini listeleyen konulara bağlantılar sağlar. Dize biçimlendirmenin, tüm varolan türler için yeni biçimlendirme dizeleri tanımlanabilmesini mümkün kılmanın yanı sıra uygulamada tanımlanmış bir tür tarafından desteklenen bir biçimlendirme dizesi kümesinin tanımlanabilmesine olanak veren genişletilebilir bir mekanizma olduğuna dikkat edin. Daha fazla bilgi için bkz <xref:System.IFormattable> . ve <xref:System.ICustomFormatter> arabirimi konuları.  
  
|Tür veya tür kategorisi|Bkz.|  
|---------------------------|---------|  
|Tarih ve saat türleri ( <xref:System.DateTime> , <xref:System.DateTimeOffset> )|[Standart Tarih ve saat biçim dizeleri](standard-date-and-time-format-strings.md)<br /><br /> [Özel tarih ve saat biçim dizeleri](custom-date-and-time-format-strings.md)|  
|Sabit listesi türleri (türetilen tüm türler <xref:System.Enum?displayProperty=nameWithType> )|[Sabit listesi biçim dizeleri](enumeration-format-strings.md)|  
|Sayısal türler ( <xref:System.Numerics.BigInteger> , <xref:System.Byte> , <xref:System.Decimal> , <xref:System.Double> , <xref:System.Int16> , <xref:System.Int32> , <xref:System.Int64> , <xref:System.SByte> , <xref:System.Single> , <xref:System.UInt16> , <xref:System.UInt32> , <xref:System.UInt64> )|[Standart sayısal biçim dizeleri](standard-numeric-format-strings.md)<br /><br /> [Özel sayısal biçim dizeleri](custom-numeric-format-strings.md)|  
|<xref:System.Guid>|<xref:System.Guid.ToString%28System.String%29?displayProperty=nameWithType>|  
|<xref:System.TimeSpan>|[Standart TimeSpan Biçim dizeleri](standard-timespan-format-strings.md)<br /><br /> [Özel TimeSpan Biçim dizeleri](custom-timespan-format-strings.md)|  
  
### <a name="escaping-braces"></a>Çıkış Yapan Ayraçlar  
 Açma ve kapatma ayraçları bir biçim öğesinin başlangıcı ve bitişi olarak yorumlanır. Sonuç olarak, sabit bir açılış veya kapanış ayracını görüntülemek için bir kaçış dizisi kullanmanız gerekir. Bir açılış ayracı ("{") görüntülemek için sabit metinde iki açılış ayracı ("{{"), veya bir kapanış ayracı ("}") görüntülemek için sabit metinde iki kapanış ayracı ("}}") belirtin. Bir biçim öğesindeki ayraçlar, karşılaşıldıkları sırada sıralı olarak yorumlanır. İç içe ayraçları yorumlama desteklenmez.  
  
 Kaçırılan ayraçların yorumlanma şekli beklenmeyen sonuçlara neden olabilir. Örneğin, {0:D} bir açılış ayracı, ondalık sayı olarak biçimlendirilen sayısal bir değer ve bir kapanış ayracı görüntülemesi amaçlanan "{{}}" biçim öğesini göz önünde bulundurun. Ancak, biçim öğesi aslında şu şekilde yorumlanır:  
  
1. İlk iki açılış ayracı ("{{") kaçırılır ve bir açılış ayracı olur.  
  
2. Sonraki üç karakter ("{0:") bir biçim öğesinin başlangıcı olarak yorumlanır.  
  
3. Sonraki karakter ("D") Ondalık standart sayısal biçim tanımlayıcısı olarak yorumlanır, ancak sonraki iki kaçırılan ayıraç ("}}") tek bir ayıraç olur. Sonuç dize ("D}") standart bir sayısal biçim tanımlayıcısı olmadığı için, sonuç dize özel bir biçimlendirme dizesi olarak yorumlanır ve bu nedenle "D}" sabit dizesini görüntüler.  
  
4. Son ayıraç ("}") biçim öğesinin bitişi olarak yorumlanır.  
  
5. Sonuç olarak "{D}" sabit dizesi görüntülenir. Biçimlendirilmek istenen sayısal değer görüntülenmez.  
  
 Kodunuzun kaçırılan ayraçları ve format öğelerini yanlış yorumlamasından kaçınmanın bir yolu, ayraçları ve biçim öğesini ayrı olarak biçimlendirmektir. Yani, ilk biçimlendirme işleminde bir sabit açılış ayracı görüntülemek, sonraki işlemde biçim öğesinin sonucunu görüntülemek ve son işlemde de bir sabit kapanış ayracı görüntülemektir. Aşağıdaki örnek bu yaklaşımı gösterir.  
  
 [!code-csharp[Formatting.Composite#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Escaping1.cs#2)]
 [!code-vb[Formatting.Composite#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Escaping1.vb#2)]  
  
### <a name="processing-order"></a>İşlem Sırası  
 Bileşik biçimlendirme yöntemine yapılan çağrı, <xref:System.IFormatProvider> değeri olmayan bir bağımsız değişken içeriyorsa `null` , çalışma zamanı <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> bir uygulama istemek için yöntemini çağırır <xref:System.ICustomFormatter> . Yöntem bir uygulama döndürebiliyor ise <xref:System.ICustomFormatter> , bileşik biçimlendirme yöntemi çağrısının süresi boyunca önbelleğe alınır.
  
 Bir biçim öğesine karşılık gelen parametre listesindeki her bir değer, aşağıdaki gibi bir dizeye dönüştürülür:  
  
1. Biçimlendirilecek değer ise `null` , boş bir dize <xref:System.String.Empty?displayProperty=nameWithType> döndürülür.  
  
2. Bir <xref:System.ICustomFormatter> uygulama kullanılabiliyorsa, çalışma zamanı <xref:System.ICustomFormatter.Format%2A> yöntemini çağırır. Yöntemi, varsa veya *formatString* `null` uygulama ile birlikte, varsa, biçim öğesinin FormatString değerini geçirir <xref:System.IFormatProvider> . <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType>Yöntem çağrısı döndürürse `null` , yürütme sonraki adıma geçer; Aksi takdirde, <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> çağrının sonucu döndürülür.
  
3. Değer, arabirimini uyguluyorsa <xref:System.IFormattable> , arabirimin <xref:System.IFormattable.ToString%28System.String%2CSystem.IFormatProvider%29> yöntemi çağırılır. Yöntemi, biçim öğesinde varsa veya yoksa, *FormatString* değeri geçirilir `null` . <xref:System.IFormatProvider>Bağımsız değişkeni şöyle belirlenir:  
  
    - Sayısal bir değer için, null olmayan bir bağımsız değişkeni olan bir bileşik biçimlendirme yöntemi <xref:System.IFormatProvider> çağrılırsa, çalışma zamanı yönteminden bir nesne ister <xref:System.Globalization.NumberFormatInfo> <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> . Bir tane sağlayamazsa, bağımsız değişkenin değeri ise `null` veya bileşik biçimlendirme yönteminin bir parametresi yoksa, <xref:System.IFormatProvider> <xref:System.Globalization.NumberFormatInfo> geçerli iş parçacığı kültürü için nesnesi kullanılır.  
  
    - Bir tarih ve saat değeri için, null olmayan bir bağımsız değişkeni olan bir bileşik biçimlendirme yöntemi <xref:System.IFormatProvider> çağrılırsa, çalışma zamanı <xref:System.Globalization.DateTimeFormatInfo> kendi yönteminden bir nesne ister <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> . Bir tane sağlayamazsa, bağımsız değişkenin değeri ise `null` veya bileşik biçimlendirme yönteminin bir parametresi yoksa, <xref:System.IFormatProvider> <xref:System.Globalization.DateTimeFormatInfo> geçerli iş parçacığı kültürü için nesnesi kullanılır.  
  
    - Diğer türlerdeki nesneler için, bir bileşik biçimlendirme yöntemi bir <xref:System.IFormatProvider> bağımsız değişkenle çağrılırsa, değeri doğrudan <xref:System.IFormattable.ToString%2A?displayProperty=nameWithType> uygulamaya geçirilir. Aksi takdirde, `null` <xref:System.IFormattable.ToString%2A?displayProperty=nameWithType> uygulamaya geçirilir.  
  
4. Türün parametresiz `ToString` yöntemi, <xref:System.Object.ToString?displayProperty=nameWithType> temel sınıfının davranışını geçersiz kılan veya devralan, çağrılır. Bu durumda, biçim öğesinde *FormatString* bileşeni tarafından belirtilen biçim dizesi varsa, yok sayılır.  
  
 Üstteki adımlar gerçekleştirildikten sonra hizalama uygulanır.  
  
## <a name="code-examples"></a>Kod Örnekleri  
 Aşağıdaki örnekte, bileşik biçimlendirme kullanılarak oluşturulan bir dize ve bir nesnenin yöntemi kullanılarak oluşturulan bir dize gösterilmektedir `ToString` . İki biçimlendirme türü de eşdeğer sonuçlar üretir.  
  
 [!code-csharp[Formatting.Composite#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#3)]
 [!code-vb[Formatting.Composite#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#3)]  
  
 Geçerli günün Mayıs değerindeki bir Perşembe olduğu varsayılırsa, yukarıdaki örnekteki her iki dizenin de değeri `Thursday May` ABD İngilizcesi kültür ' dadır.  
  
 <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>ile aynı işlevselliği sunar <xref:System.String.Format%2A?displayProperty=nameWithType> . İki yöntem arasındaki tek fark, sonucu <xref:System.String.Format%2A?displayProperty=nameWithType> bir dize olarak döndürirken <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> sonucu nesneyle ilişkili çıkış akışına yazar <xref:System.Console> . Aşağıdaki örnek, <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> değerini `MyInt` bir para birimi değerine biçimlendirmek için yöntemini kullanır.  
  
 [!code-csharp[Formatting.Composite#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#4)]
 [!code-vb[Formatting.Composite#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#4)]  
  
 Aşağıdaki örnek birden çok nesneyi biçimlendirmeyi ve bir nesneyi iki farklı şekilde biçimlendirmeyi gösterir.  
  
 [!code-csharp[Formatting.Composite#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#5)]
 [!code-vb[Formatting.Composite#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#5)]  
  
 Aşağıdaki örnek biçimlendirmede hizalama kullanımını gösterir. Biçimlendirilen bağımsız değişkenler, ortaya çıkan hizalamayı vurgulamak için dikey çubuk karakterleri (&#124;) arasına yerleştirilir.  
  
 [!code-csharp[Formatting.Composite#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#6)]
 [!code-vb[Formatting.Composite#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#6)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Console.WriteLine%2A>
- <xref:System.String.Format%2A?displayProperty=nameWithType>
- [Dize ilişkilendirme (C#)](../../csharp/language-reference/tokens/interpolated.md)
- [Dize ilişkilendirme (Visual Basic)](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md)
- [Biçimlendirme Türleri](formatting-types.md)
- [Standart sayısal biçim dizeleri](standard-numeric-format-strings.md)
- [Özel sayısal biçim dizeleri](custom-numeric-format-strings.md)
- [Standart Tarih ve saat biçim dizeleri](standard-date-and-time-format-strings.md)
- [Özel tarih ve saat biçim dizeleri](custom-date-and-time-format-strings.md)
- [Standart TimeSpan Biçim dizeleri](standard-timespan-format-strings.md)
- [Özel TimeSpan Biçim dizeleri](custom-timespan-format-strings.md)
- [Sabit listesi biçim dizeleri](enumeration-format-strings.md)
