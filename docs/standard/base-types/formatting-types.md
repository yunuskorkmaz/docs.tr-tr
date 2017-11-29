---
title: ".NET biçimlendirme türleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data formatting [.NET Framework]
- dates [.NET Framework], formatting
- date formatting [.NET Framework]
- number formatting [.NET Framework]
- ToString method
- custom cultural settings [.NET Framework]
- numbers [.NET Framework], formatting
- formatting strings [.NET Framework]
- time [.NET Framework], formatting
- currency [.NET Framework], formatting
- types [.NET Framework], formatting
- format specifiers [.NET Framework]
- times [.NET Framework], formatting
- culture [.NET Framework], formatting
- formatting [.NET Framework], types supported
- base types [.NET Framework], formatting
- custom formatting [.NET Framework]
- strings [.NET Framework], formatting
ms.assetid: 0d1364da-5b30-4d42-8e6b-03378343343f
caps.latest.revision: "43"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 816337ead810be405339a0616798a06689b97315
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="formatting-types-in-net"></a>.NET biçimlendirme türleri
<a name="Introduction"></a>Biçimlendirme Sonuç dizesini kullanıcılara görüntülenen ya da özgün veri türü geri yüklemek için seri, dize gösterimi için genellikle bir sınıf, yapı veya sabit listesi değeri örneği dönüştürme işlemidir. Bu dönüştürme belirli zorluklar oluşturabilir:  
  
-   Değerleri dahili olarak depolanma şeklini, kullanıcılar bunları görüntülemek istediğiniz şekilde yansıtmayabilir. Örneğin, bir telefon numarası kullanıcı dostu olmayan biçiminde 8009999999, depolanabilir. Bunun yerine 800-999-9999 görüntülenmelidir. Bkz: [özel biçim dizeleri](#customStrings) bu şekilde bir sayıyı biçimlendirir bir örnek bölüm.  
  
-   Bazı durumlarda bir nesnenin dize gösterimi dönüştürme sezgisel değildir. Örneğin, bir sıcaklık veya bir kişinin nesneyi dize gösterimini nasıl görünmelidir açık değil. Çeşitli şekillerde sıcaklık nesnesinde biçimleri bir örnek için bkz: [standart biçim dizeleri](#standardStrings) bölümü.  
  
-   Kültüre duyarlı biçimlendirme değerleri genellikle gerektirir. Örneğin, parasal değerleri yansıtacak şekilde numaraları kullanan bir uygulama içinde geçerli kültürün para birimi simgesini, Grup ayırıcı sayısal dizeleri içermelidir (, çoğu kültürler içinde olduğu binlik ayırıcı) ve ondalık simgesi. Bir örnek için bkz: [kültüre duyarlı biçimlendirme biçim sağlayıcıları ve Iformatprovider arabirimi ile](#FormatProviders) bölümü.  
  
-   Aynı değeri farklı şekillerde görüntülemek bir uygulama olabilir. Örneğin, bir uygulama adı bir dize gösterimini görüntüleyerek veya temel alınan değeri görüntüleyerek bir numaralandırma üyesine gösterebilir. Üye biçimleri bir örnek <xref:System.DayOfWeek> farklı şekillerde numaralandırması bkz [standart biçim dizeleri](#standardStrings) bölümü.  
  
> [!NOTE]
>  Biçimlendirme bir türü değeri bir dize gösterimine dönüştürür. Ayrıştırma biçimlendirme tersidir. Ayrıştırma işlemi kendi dize gösteriminden bir veri türünün bir örneğini oluşturur. Diğer veri türlerine dizeleri dönüştürme hakkında daha fazla bilgi için bkz: [dizeleri ayrıştırma](../../../docs/standard/base-types/parsing-strings.md).  
  
 .NET geliştiricileri bu gereksinimlere sağlayan zengin biçimlendirme desteği sağlar.  
  
 Bu genel bakışta aşağıdaki bölümleri içerir:  
  
-   [.NET biçimlendirme](#NetFormatting)  
  
-   [Biçimlendirme ToString yöntemini kullanarak varsayılan](#DefaultToString)  
  
-   [ToString yöntemini geçersiz kılma](#OverrideToString)  
  
-   [ToString yöntemi ve biçim dizeleri](#FormatStrings)  
  
    -   [Standart biçim dizeleri](#standardStrings)  
  
    -   [Özel biçim dizeleri](#customStrings)  
  
    -   [Biçim dizeleri ve .NET sınıf kitaplığı türleri](#stringRef)  
  
-   [Biçim sağlayıcıları ve Iformatprovider arabirimi ile kültüre duyarlı biçimlendirme](#FormatProviders)  
  
    -   [Kültüre duyarlı sayısal değerleri biçimlendirme](#numericCulture)  
  
    -   [Tarih ve saat değerleri kültüre duyarlı biçimlendirme](#dateCulture)  
  
-   [IFormattable arabirimi](#IFormattable)  
  
-   [Bileşik biçimlendirme](#CompositeFormatting)  
  
-   [Özel ICustomFormatter ile biçimlendirme](#Custom)  
  
-   [İlgili Konular](#RelatedTopics)  
  
-   [Başvuru](#Reference)  
  
<a name="NetFormatting"></a>   
## <a name="formatting-in-net"></a>.NET biçimlendirme  
 Varsayılan uygulamasıdır biçimlendirme için temel mekanizmasını <xref:System.Object.ToString%2A?displayProperty=nameWithType> içinde ele alınmıştır yöntemi [ToString yöntemini kullanarak biçimlendirmeyi varsayılan](#DefaultToString) bu konunun ilerleyen bölümlerinde. Ancak, .NET değiştirmek ve Destek biçimlendirme varsayılan genişletmek için çeşitli yollar sağlar. Bunlar aşağıdakileri içerir:  
  
-   Geçersiz kılma <xref:System.Object.ToString%2A?displayProperty=nameWithType> yöntemi nesnenin değeri özel bir dize gösterimini tanımlayın. Daha fazla bilgi için bkz: [ToString yöntemini geçersiz kılma](#OverrideToString) bu konunun ilerleyen bölümlerinde.  
  
-   Bir nesnenin değeri çoklu biçimlerde dize gösterimini etkinleştirmek biçim belirticileri tanımlama. Örneğin, aşağıdaki deyiminde "X" biçimi belirleyici bir onaltılık değer dize gösterimini bir tamsayı dönüştürür.  
  
     [!code-csharp[Conceptual.Formatting.Overview#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/specifier1.cs#3)]
     [!code-vb[Conceptual.Formatting.Overview#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/specifier1.vb#3)]  
  
     Biçim belirticiler hakkında daha fazla bilgi için bkz: [ToString yöntemini ve biçim dizeleri](#FormatStrings) bölümü.  
  
-   Belirli bir kültür biçimlendirme kuralları yararlanmak için biçim sağlayıcıları kullanma. Örneğin, aşağıdaki deyim, en-US kültür biçimlendirme kuralları kullanarak para birimi değeri görüntüler.  
  
     [!code-csharp[Conceptual.Formatting.Overview#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/specifier1.cs#10)]
     [!code-vb[Conceptual.Formatting.Overview#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/specifier1.vb#10)]  
  
     Biçim sağlayıcıları ile biçimlendirme hakkında daha fazla bilgi için bkz: [biçim sağlayıcıları ve Iformatprovider arabirimi](#FormatProviders) bölümü.  
  
-   Uygulama <xref:System.IFormattable> ile iki dize dönüştürme desteklemek için arabirimi <xref:System.Convert> sınıfı ve bileşik biçimlendirme. Daha fazla bilgi için bkz: [IFormattable arabirimi](#IFormattable) bölümü.  
  
-   Bileşik biçimlendirme içinde daha büyük bir dize değeri dize gösterimini katıştırmak için kullanma. Daha fazla bilgi için bkz: [bileşik biçimlendirme](#CompositeFormatting) bölümü.  
  
-   Uygulama <xref:System.ICustomFormatter> ve <xref:System.IFormatProvider> eksiksiz bir özel biçimlendirme çözümü sağlamak için. Daha fazla bilgi için bkz: [özel biçimlendirme ICustomFormatter ile](#Custom) bölümü.  
  
 Bu yöntemler bir nesne, dize gösterimi dönüştürmek için aşağıdaki bölümleri inceleyin.  
  
 [Başa dön](#Introduction)  
  
<a name="DefaultToString"></a>   
## <a name="default-formatting-using-the-tostring-method"></a>ToString Yöntemini Kullanarak Varsayılan Biçimlendirme  
 Türetilen her türün <xref:System.Object?displayProperty=nameWithType> otomatik olarak bir parametresiz devralır `ToString` türünün adını varsayılan olarak döndüren yöntemi. Aşağıdaki örnekte, varsayılan gösterilmektedir `ToString` yöntemi. Adlı bir sınıf tanımlar `Automobile` uygulaması sahip. Sınıf örneği ne zaman ve kendi `ToString` yöntemi çağrıldığında, türü adını görüntüler. Unutmayın `ToString` yöntemi örnekte açıkça çağrılmaz. <xref:System.Console.WriteLine%28System.Object%29?displayProperty=nameWithType> Yöntemi örtük olarak çağırır `ToString` nesnesinin yöntemi için bağımsız değişken olarak geçirilen.  
  
 [!code-csharp[Conceptual.Formatting.Overview#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/default1.cs#1)]
 [!code-vb[Conceptual.Formatting.Overview#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/default1.vb#1)]  
  
> [!WARNING]
>  Sürümünden itibaren [!INCLUDE[win81](../../../includes/win81-md.md)], [!INCLUDE[wrt](../../../includes/wrt-md.md)] içeren bir [IStringable](http://msdn.microsoft.com/library/windows/apps/windows.foundation.istringable.aspx) tek bir yöntem arabirimiyle [IStringable.ToString](http://msdn.microsoft.com/library/windows/apps/windows.foundation.istringable.tostring.aspx), varsayılan biçimlendirme desteği sağlar. Ancak, yönetilen türler uygulamayan öneririz `IStringable` arabirimi. Daha fazla bilgi için " [!INCLUDE[wrt](../../../includes/wrt-md.md)] ve `IStringable` arabirimi" bölümünde <xref:System.Object.ToString%2A?displayProperty=nameWithType> başvuru sayfası.  
  
 Arabirimler dışında tüm türleri türetilmiş çünkü <xref:System.Object>, bu işlev, özel sınıflar veya yapıları otomatik olarak sağlanır. Ancak, varsayılan olarak sunulan işlevleri `ToString` yöntemi, sınırlıdır: türü tanımlasa da, türünün bir örneği hakkında hiçbir bilgi sağlamak başarısız. Bu nesne hakkında bilgi sağlayan bir nesne bir dize gösterimini sağlamak için geçersiz kılmanız gerekir `ToString` yöntemi.  
  
> [!NOTE]
>  Yapıları devral <xref:System.ValueType>, sırayla türetilen <xref:System.Object>. Ancak <xref:System.ValueType> geçersiz kılmaları <xref:System.Object.ToString%2A?displayProperty=nameWithType>, kendi uygulama aynıdır.  
  
 [Başa dön](#Introduction)  
  
<a name="OverrideToString"></a>   
## <a name="overriding-the-tostring-method"></a>ToString Yöntemini Geçersiz Kılma  
 Bir türün adını görüntüleme genellikle sınırlı kullanımı olan ve bir örnek diğerinden ayırt etmek için türlerinizi tüketicilerinin izin vermez. Ancak, kılabilirsiniz `ToString` yöntemi nesnenin değeri daha kullanışlı bir gösterimini sağlar. Aşağıdaki örnek tanımlayan bir `Temperature` nesne ve geçersiz kılmalar kendi `ToString` derece derece sıcaklık görüntülenecek yöntemi.  
  
 [!code-csharp[Conceptual.Formatting.Overview#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/overrides1.cs#2)]
 [!code-vb[Conceptual.Formatting.Overview#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/overrides1.vb#2)]  
  
 .NET içinde `ToString` yöntem her İlkel değer türü geçersiz nesnenin değeri adı yerine görüntülenecek. Aşağıdaki tabloda her ilkel tür için geçersiz kılma gösterir. Geçersiz kılınan yöntemlerinin çoğu başka bir aşırı yüklemesini çağırın Not `ToString` yöntemi ve genel biçim türü için tanımlar, "G" biçim belirticisi geçirin ve bir <xref:System.IFormatProvider> geçerli kültürü temsil eden nesne.  
  
|Tür|ToString geçersiz kılma|  
|----------|-----------------------|  
|<xref:System.Boolean>|Ya da döndürür <xref:System.Boolean.TrueString?displayProperty=nameWithType> veya <xref:System.Boolean.FalseString?displayProperty=nameWithType>.|  
|<xref:System.Byte>|Çağrıları `Byte.ToString("G", NumberFormatInfo.CurrentInfo)` biçimlendirmek için <xref:System.Byte> geçerli kültür için değer.|  
|<xref:System.Char>|Karakter dizesi olarak döndürür.|  
|<xref:System.DateTime>|Çağrıları `DateTime.ToString("G", DatetimeFormatInfo.CurrentInfo)` geçerli kültür için tarih ve saat değeri biçimlendirmek için.|  
|<xref:System.Decimal>|Çağrıları `Decimal.ToString("G", NumberFormatInfo.CurrentInfo)` biçimlendirmek için <xref:System.Decimal> geçerli kültür için değer.|  
|<xref:System.Double>|Çağrıları `Double.ToString("G", NumberFormatInfo.CurrentInfo)` biçimlendirmek için <xref:System.Double> geçerli kültür için değer.|  
|<xref:System.Int16>|Çağrıları `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` biçimlendirmek için <xref:System.Int16> geçerli kültür için değer.|  
|<xref:System.Int32>|Çağrıları `Int32.ToString("G", NumberFormatInfo.CurrentInfo)` biçimlendirmek için <xref:System.Int32> geçerli kültür için değer.|  
|<xref:System.Int64>|Çağrıları `Int64.ToString("G", NumberFormatInfo.CurrentInfo)` biçimlendirmek için <xref:System.Int64> geçerli kültür için değer.|  
|<xref:System.SByte>|Çağrıları `SByte.ToString("G", NumberFormatInfo.CurrentInfo)` biçimlendirmek için <xref:System.SByte> geçerli kültür için değer.|  
|<xref:System.Single>|Çağrıları `Single.ToString("G", NumberFormatInfo.CurrentInfo)` biçimlendirmek için <xref:System.Single> geçerli kültür için değer.|  
|<xref:System.UInt16>|Çağrıları `UInt16.ToString("G", NumberFormatInfo.CurrentInfo)` biçimlendirmek için <xref:System.UInt16> geçerli kültür için değer.|  
|<xref:System.UInt32>|Çağrıları `UInt32.ToString("G", NumberFormatInfo.CurrentInfo)` biçimlendirmek için <xref:System.UInt32> geçerli kültür için değer.|  
|<xref:System.UInt64>|Çağrıları `UInt64.ToString("G", NumberFormatInfo.CurrentInfo)` biçimlendirmek için <xref:System.UInt64> geçerli kültür için değer.|  
  
 [Başa dön](#Introduction)  
  
<a name="FormatStrings"></a>   
## <a name="the-tostring-method-and-format-strings"></a>ToString Yöntemi ve Biçim Dizeleri  
 Varsayılan olarak bağlı olan `ToString` yöntemi veya geçersiz kılma `ToString` nesneyi tek bir dize gösterimi olduğunda uygundur. Ancak, bir nesnenin değerini genellikle birden çok Beyanları sahiptir. Örneğin, bir sıcaklık Fahrenhayt derece, derece derece veya kelvins ifade edilebilir. Benzer şekilde, tamsayı değeri 10 10 ' da dahil olmak üzere çeşitli yollarla temsil edilebilir 10.0, 1.0e01 veya $10,00.  
  
 Birden çok dize Beyanları sağlamak tek bir değer sağlamak için biçim dizeleri .NET kullanır. Bir biçim dizesi birini içeren bir dize tek karakter veya tanımlayan karakter grubu olan daha önceden tanımlanmış biçim belirticileri, mi nasıl `ToString` yöntemi çıktısını biçimlendirme. Biçim dizesi parametresi olarak nesnenin geçirilir `ToString` yöntemi ve o nesnenin değeri dize gösterimini nasıl göründüğünü belirler.  
  
 Tüm sayısal türler, tarih ve saat türlerde ve sıralama türlerinde .NET içindeki Biçim belirticileri önceden tanımlanmış bir kümesini destekler. Biçim dizeleri, uygulama tanımlı veri türleri birden çok dize gösterimlerini tanımlamak için de kullanabilirsiniz.  
  
<a name="standardStrings"></a>   
### <a name="standard-format-strings"></a>Standart Biçim Dizeleri  
 Standart biçim dizesi, uygulanacağı, kaç basamak görüntülenme şeklini etkiler bir isteğe bağlı duyarlık Belirleyicisi birlikte nesnenin dize gösterimini tanımlar alfabetik bir karakter olan bir tek biçim belirticisi içerir Sonuç dizesini. Duyarlık Belirleyicisi atlanmış veya desteklenmiyorsa, standart biçim belirleyici bir standart biçim dizesine eşdeğerdir.  
  
 .NET tüm sayısal türler, tüm tarih ve saat türleri ve tüm sabit listesi türleri için standart biçim belirticileri kümesini tanımlar. Örneğin, bu kategorilerin her birinde bu türde bir değer genel dize gösterimini tanımlayan bir "G" standart biçim belirticisi destekler.  
  
 Standart biçim dizeleri Numaralandırma türleri için bir değer dize gösterimini doğrudan denetler. Biçim dizeleri geçirilen bir numaralandırma değerinin için `ToString` yöntemini belirleme değeri dize adıyla ("G" ve "tanımlayıcıları biçimlendirmek F"), temel alınan tam sayı değeri ("D" biçim belirticisi) veya onaltılık değeri ("X görüntülenip görüntülenmeyeceğini "biçim belirticisi). Aşağıdaki örnek biçimlendirmek için standart biçim dizeleri kullanımını göstermektedir bir <xref:System.DayOfWeek> numaralandırma değeri.  
  
 [!code-csharp[Conceptual.Formatting.Overview#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/standard1.cs#4)]
 [!code-vb[Conceptual.Formatting.Overview#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/standard1.vb#4)]  
  
 Numaralandırma biçimi dizeleri hakkında daha fazla bilgi için bkz: [numaralandırma biçimi dizeleri](../../../docs/standard/base-types/enumeration-format-strings.md).  
  
 Standart biçim dizeleri sayısal türler için genellikle kesin görünümünü bir veya daha fazla özellik değerlerini tarafından denetlenen bir sonuç dizesini tanımlayın. Örneğin, "C" biçimi belirleyici bir sayı bir para birimi değeri olarak biçimlendirir. Çağırdığınızda `ToString` tek parametre olarak "C" biçim belirticisi, geçerli kültürün aşağıdaki özellik değerleri yöntemiyle <xref:System.Globalization.NumberFormatInfo> nesne sayısal değer dize gösterimini tanımlamak için kullanılır:  
  
-   <xref:System.Globalization.NumberFormatInfo.CurrencySymbol%2A> Geçerli kültürün para birimi simgesini belirtir özelliği.  
  
-   <xref:System.Globalization.NumberFormatInfo.CurrencyNegativePattern%2A> Veya <xref:System.Globalization.NumberFormatInfo.CurrencyPositivePattern%2A> aşağıdaki belirleyen bir tamsayı döndürür özelliği:  
  
    -   Para birimi simgesini yerleştirme.  
  
    -   Olup negatif değerler önüne eksi işareti, sonunda eksi işareti veya parantez tarafından belirtilir.  
  
    -   Bir alanı sayısal değer ve para birimi simgesini arasında görüntülenip.  
  
-   <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits%2A> Kesir basamakları sayısı sonuç dizesinde tanımlar özelliği.  
  
-   <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator%2A> Ondalık ayırıcı simge sonuç dizesinde tanımlar özelliği.  
  
-   <xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator%2A> Grup ayırıcı simge tanımlar özelliği.  
  
-   <xref:System.Globalization.NumberFormatInfo.CurrencyGroupSizes%2A> Ondalık solundaki her grubundaki basamak sayısını tanımlar özelliği.  
  
-   <xref:System.Globalization.NumberFormatInfo.NegativeSign%2A> Negatif değerleri belirtmek için parantez kullanılmazsa sonuç dizesinde kullanılan eksi işareti belirler özelliği.  
  
 Ayrıca, sayısal biçim dizeleri duyarlık Belirleyicisi içerebilir. Bu belirleyici anlamını hangi kullanılır, ancak genellikle toplam basamak sayısı veya sonuç dizesinde görünmelidir kesir basamakları sayısı gösterir biçim dizesi bağlıdır. Örneğin, aşağıdaki örnekte "X 4" standart sayısal dize ve duyarlık Belirleyicisi dört onaltılık basamak sahip bir string değeri oluşturmak için kullanır.  
  
 [!code-csharp[Conceptual.Formatting.Overview#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/precisionspecifier1.cs#6)]
 [!code-vb[Conceptual.Formatting.Overview#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/precisionspecifier1.vb#6)]  
  
 Standart sayısal biçimlendirme dizeleri hakkında daha fazla bilgi için bkz: [standart sayısal biçim dizeleri](../../../docs/standard/base-types/standard-numeric-format-strings.md).  
  
 Tarih ve saat değerleri için standart biçim dizeleri olan belirli bir tarafından depolanan özel biçim dizeleri için diğer adlar <xref:System.Globalization.DateTimeFormatInfo> özelliği. Örneğin, arama `ToString` yöntemi ile "D" biçimi belirleyici bir tarih ve saat değerinin tarih ve saati geçerli kültürün içinde depolanan özel biçim dizesini kullanarak görüntüler <xref:System.Globalization.DateTimeFormatInfo.LongDatePattern%2A?displayProperty=nameWithType> özelliği. (Özel biçim dizeleri hakkında daha fazla bilgi için bkz: [sonraki bölümde](#customStrings).) Aşağıdaki örnek, bu ilişki gösterilmektedir.  
  
 [!code-csharp[Conceptual.Formatting.Overview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/alias1.cs#5)]
 [!code-vb[Conceptual.Formatting.Overview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/alias1.vb#5)]  
  
 Standart tarih ve saat biçim dizeleri hakkında daha fazla bilgi için bkz: [standart tarih ve saat biçim dizeleri](../../../docs/standard/base-types/standard-date-and-time-format-strings.md).  
  
 Standart biçim dizeleri nesnenin tarafından üretilen uygulama tanımlı bir nesnenin dize gösterimini tanımlamak için de kullanabilirsiniz `ToString(String)` yöntemi. Büyük küçük harfe duyarlı veya büyük küçük harf duyarlı olup olmadıklarını belirlemek ve nesnenizin destekler belirli standart biçim belirticileri tanımlayabilirsiniz. Uygulamanıza `ToString(String)` yöntemi aşağıdaki Destek:  
  
-   Nesnenin her zamanki veya ortak bir biçimi temsil eder "G" biçimi tanımlayıcısı. Nesnenin parametresiz yüklemesini `ToString` yöntemini çağırın kendi `ToString(String)` aşırı yükleme ve "G" standart biçim dizesi geçirin.  
  
-   Bir null başvuru eşit olan bir biçim belirticisi desteği (`Nothing` Visual Basic'te). Bir null başvuru eşit olan bir biçim belirticisi "G" biçim belirteci eşdeğer olarak düşünülmelidir.  
  
 Örneğin, bir `Temperature` sınıfı, dahili olarak sıcaklık derece derece depolayın ve değerini temsil etmek için biçim belirticileri kullanın `Temperature` derece derece, fahrenhayt derece ve kelvins nesne. Aşağıdaki örnek, bir gösterim sağlar.  
  
 [!code-csharp[Conceptual.Formatting.Overview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/appstandard1.cs#7)]
 [!code-vb[Conceptual.Formatting.Overview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/appstandard1.vb#7)]  
  
 [Başa dön](#Introduction)  
  
<a name="customStrings"></a>   
### <a name="custom-format-strings"></a>Özel Biçim Dizeleri  
 Standart biçim dizeleri ek olarak, .NET özel biçim dizeleri hem sayısal değerler için tarih ve saat değerlerini tanımlar. Özel bir biçim dizesi değeri dize gösterimini tanımlayan bir veya daha fazla özel biçim belirticileri oluşur. Örneğin, özel tarih ve saat biçimi dizesi "yyyy/aa/gg hh:mm:ss.ffff t zzz" biçiminde kendi dize gösterimi dönüştürür "11/2008/15 07:45:00.0000 P -08:00" en-US kültür için. Benzer şekilde, özel biçim dizesi "0000" tamsayı değeri "0012" 12 dönüştürür. Özel biçim dizeleri tam bir listesi için bkz: [özel tarih ve saat biçim dizeleri](../../../docs/standard/base-types/custom-date-and-time-format-strings.md) ve [özel sayısal biçim dizeleri](../../../docs/standard/base-types/custom-numeric-format-strings.md).  
  
 Bir biçim dizesi bir tek özel biçim belirticisi oluşuyorsa, biçim belirteci standart biçim belirteci ile Karışıklığı önlemek için yüzde (%) simgesi gelmelidir. Aşağıdaki örnek, belirli bir tarih ayın tek basamaklı veya iki basamaklı sayısını görüntülemek için "M" özel biçim belirticisi kullanır.  
  
 [!code-csharp[Conceptual.Formatting.Overview#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/singlecustom1.cs#8)]
 [!code-vb[Conceptual.Formatting.Overview#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/singlecustom1.vb#8)]  
  
 Tarih ve saat değerleri için birçok standart biçim dizeleri özellikleri tarafından tanımlanan özel biçim dizeleri diğer adlarıdır <xref:System.Globalization.DateTimeFormatInfo> nesnesi. Özel biçim dizeleri de sayısal değer veya tarih ve saat değerleri için uygulama tanımlı biçimlendirme sağlayarak önemli esneklik sunar. Tek özel bir biçim dizesi birden çok özel biçim belirticileri birleştirerek, kendi özel sonuç dizeleri hem sayısal değerler için tarih ve saat değerleri tanımlayabilirsiniz. Aşağıdaki örnek, ay adını, günlük ve yıl sonra parantez içinde haftanın gününü gösteren özel bir biçim dizesi tanımlar.  
  
 [!code-csharp[Conceptual.Formatting.Overview#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/custom1.cs#9)]
 [!code-vb[Conceptual.Formatting.Overview#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/custom1.vb#9)]  
  
 Aşağıdaki örnek görüntüleyen özel bir biçim dizesi tanımlayan bir <xref:System.Int64> değeri, alan kodunu birlikte standart, yedi basamaklı ABD telefon numarası olarak.  
  
 [!code-csharp[Conceptual.Formatting.Overview#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/telnumber1.cs#21)]
 [!code-vb[Conceptual.Formatting.Overview#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/telnumber1.vb#21)]  
  
 Standart biçim dizeleri genellikle uygulama tanımlı türleri için biçimlendirme gereksinimlerini çoğunu işleyebilir karşın, aynı zamanda türlerinizi biçimlendirmek için özel biçim belirticileri tanımlayabilir.  
  
 [Başa dön](#Introduction)  
  
<a name="stringRef"></a>   
### <a name="format-strings-and-net-class-library-types"></a>Biçim dizeleri ve .NET sınıf kitaplığı türleri  
 Tüm sayısal türler (diğer bir deyişle, <xref:System.Byte>, <xref:System.Decimal>, <xref:System.Double>, <xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.SByte>, <xref:System.Single>, <xref:System.UInt16>, <xref:System.UInt32>, <xref:System.UInt64>ve <xref:System.Numerics.BigInteger>türleri)  
  
 , hem de <xref:System.DateTime>, <xref:System.DateTimeOffset>, <xref:System.TimeSpan>, <xref:System.Guid>, ve tüm sabit listesi türleri, destek ile biçim dizeleri biçimlendirme. Her türü tarafından desteklenen özel biçim dizeleri hakkında daha fazla bilgi için aşağıdaki konulara bakın  
  
|Başlık|Tanım|  
|-----------|----------------|  
|[Standart sayısal biçim dizeleri](../../../docs/standard/base-types/standard-numeric-format-strings.md)|Sayısal değerleri yaygın olarak kullanılan dize temsilini oluşturmak standart biçim dizeleri açıklar.|  
|[Özel sayısal biçim dizeleri](../../../docs/standard/base-types/custom-numeric-format-strings.md)|Sayısal değerler için uygulamaya özgü biçimi oluşturmanıza özel biçim dizeleri açıklar.|  
|[Standart tarih ve saat biçim dizeleri](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)|Yaygın olarak kullanılan dize temsilini oluşturmak standart biçim dizeleri açıklar <xref:System.DateTime> değerleri.|  
|[Özel tarih ve saat biçim dizeleri](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)|Uygulamaya özgü biçimleri için oluşturduğunuz özel biçim dizeleri açıklar <xref:System.DateTime> değerleri.|  
|[Standart TimeSpan biçim dizeleri](../../../docs/standard/base-types/standard-timespan-format-strings.md)|Zaman aralıkları yaygın olarak kullanılan dize temsilini oluşturmak standart biçim dizeleri açıklar.|  
|[Özel TimeSpan biçim dizeleri](../../../docs/standard/base-types/custom-timespan-format-strings.md)|Zaman aralıkları için uygulamaya özgü biçimleri oluşturma özel biçim dizeleri açıklar.|  
|[Numaralandırma biçimi dizeleri](../../../docs/standard/base-types/enumeration-format-strings.md)|Numaralandırma değerlerinin dize temsilini oluşturmak için kullanılan standart biçim dizeleri açıklar.|  
|<xref:System.Guid.ToString%28System.String%29?displayProperty=nameWithType>|Standart biçim dizeleri için açıklar <xref:System.Guid> değerleri.|  
  
<a name="FormatProviders"></a>   
## <a name="culture-sensitive-formatting-with-format-providers-and-the-iformatprovider-interface"></a>Biçim Sağlayıcıları ve IFormatProvider Arabirimi ile Kültüre Duyarlı Biçimlendirme  
 Biçim belirticiler nesnelerin biçimlendirme özelleştirmenize olanak tanır ancak genellikle anlamlı dize gösterimi nesnelerin oluşturan ek biçimlendirme bilgi gerektirir. Örneğin, "C" standart biçim dizesi veya özel bir biçim dizesi gibi kullanarak bir sayı bir para birimi değeri olarak biçimlendirme "$ #, #. 00" gerektirir, en azından doğru para birimi simgesini, Grup ayırıcısı ve olmasını ondalık ayırıcı hakkında bilgi biçimlendirilmiş dizesini dahil etmek kullanılabilir. .NET içinde bu ek biçimlendirme bilgiler kullanılabilir hale <xref:System.IFormatProvider> bir veya daha fazla aşırı parametre olarak sağlanan arabirimi `ToString` sayısal türler ve tarih ve saat türlerinin yöntemi. <xref:System.IFormatProvider>uygulamaları .NET kültüre özgü biçimlendirme desteklemek için kullanılır. Aşağıdaki örnek, bir nesnenin dize gösterimini üç biçimlendirildiğinde nasıl değiştiğini gösterir <xref:System.IFormatProvider> farklı kültürler temsil eden nesne.  
  
 [!code-csharp[Conceptual.Formatting.Overview#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/iformatprovider1.cs#11)]
 [!code-vb[Conceptual.Formatting.Overview#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/iformatprovider1.vb#11)]  
  
 <xref:System.IFormatProvider> Arabirimi içeren bir yöntem <xref:System.IFormatProvider.GetFormat%28System.Type%29>, biçimlendirme bilgileri sağlayan nesne türünü belirten tek bir parametre vardır. Yöntemi bu türde bir nesne sağlarsanız, döndürür. Aksi takdirde null bir başvuru döndürür (`Nothing` Visual Basic'te).  
  
 <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType>bir geri çağırma yöntemidir. Çağırdığınızda bir `ToString` içeren yöntemi aşırı yüklemesini bir <xref:System.IFormatProvider> parametresi çağırır <xref:System.IFormatProvider.GetFormat%2A> yöntemi, <xref:System.IFormatProvider> nesnesi. <xref:System.IFormatProvider.GetFormat%2A> Yöntemi tarafından belirtilen gerekli biçimlendirme bilgileri sağlayan bir nesne döndürmek için sorumlu kendi `formatType` parametresi, `ToString` yöntemi.  
  
 Biçimlendirme veya dize dönüştürme yöntemleri sayısı dahil türünde bir parametre <xref:System.IFormatProvider>, ancak birçok durumda yöntemi çağrıldığında parametresinin değeri yoksayılır. Aşağıdaki tabloda, parametre ve türünü kullanan biçimlendirme yöntemlerin bazıları listeler <xref:System.Type> için geçirirler nesne <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> yöntemi.  
  
|Yöntem|Tür `formatType` parametresi|  
|------------|------------------------------------|  
|`ToString`sayısal türler yöntemi|<xref:System.Globalization.NumberFormatInfo?displayProperty=nameWithType>|  
|`ToString`Tarih ve saat türlerinin yöntemi|<xref:System.Globalization.DateTimeFormatInfo?displayProperty=nameWithType>|  
|<xref:System.String.Format%2A?displayProperty=nameWithType>|<xref:System.ICustomFormatter?displayProperty=nameWithType>|  
|<xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>|<xref:System.ICustomFormatter?displayProperty=nameWithType>|  
  
> [!NOTE]
>  `ToString` Tarih ve saat türleri ve sayısal türler yöntemlerini aşırı ve yalnızca aşırı bazıları bir <xref:System.IFormatProvider> parametresi. Bir yöntem türünde bir parametre yoksa <xref:System.IFormatProvider>, tarafından döndürülen nesne <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> özelliği yerine geçti. Örneğin, varsayılan bir çağrı <xref:System.Int32.ToString?displayProperty=nameWithType> yöntemi sonuçta sonuçlanıyor aşağıdaki gibi bir yöntem çağrısı: `Int32.ToString("G", System.Globalization.CultureInfo.CurrentCulture)`.  
  
 .NET uygulayan üç sınıflar sağlar <xref:System.IFormatProvider>:  
  
-   <xref:System.Globalization.DateTimeFormatInfo>, belirli bir kültür için tarih ve saat değerleri için biçimlendirme bilgileri sağlayan bir sınıf. Kendi <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> uygulaması kendi örneğini döndürür.  
  
-   <xref:System.Globalization.NumberFormatInfo>, belirli bir kültür için sayısal biçimlendirme bilgileri sağlayan bir sınıf. Kendi <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> uygulaması kendi örneğini döndürür.  
  
-   <xref:System.Globalization.CultureInfo>. Kendi <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> uygulama ya da dönebilirsiniz bir <xref:System.Globalization.NumberFormatInfo> sayısal biçimlendirme bilgi sağlamak için nesne veya <xref:System.Globalization.DateTimeFormatInfo> tarih ve saat değerleri biçimlendirme bilgilerini sağlamak için nesne.  
  
 Ayrıca bu sınıfların herhangi birini değiştirmek için kendi biçim sağlayıcısı uygulayabilirsiniz. Ancak, uygulamanızı 's <xref:System.IFormatProvider.GetFormat%2A> yöntemi biçimlendirme bilgi sağlamak amacıyla varsa önceki tabloda listelenen türünde bir nesne döndürmelidir `ToString` yöntemi.  
  
 [Başa dön](#Introduction)  
  
<a name="numericCulture"></a>   
### <a name="culture-sensitive-formatting-of-numeric-values"></a>Sayısal Değerleri Kültüre Duyarlı Olarak Biçimlendirme  
 Varsayılan olarak, biçimlendirme sayısal değerleri kültüre duyarlı. Biçimlendirme yöntemini çağırdığınızda bir kültür belirtmezseniz, geçerli iş parçacığı kültürünü biçimlendirme kuralları kullanılır. Bu, geçerli iş parçacığı kültürünü dört kez değiştirir ve çağırır aşağıdaki örnekte gösterilmiştir <xref:System.Decimal.ToString%28System.String%29?displayProperty=nameWithType> yöntemi. Her durumda, sonuç dizesini geçerli kültür biçimlendirme kuralları yansıtır. Bunun nedeni, `ToString` ve `ToString(String)` yöntemleri kaydırma her sayısal tür çağrılar `ToString(String, IFormatProvider)` yöntemi.  
  
 [!code-csharp[Conceptual.Formatting.Overview#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific3.cs#19)]
 [!code-vb[Conceptual.Formatting.Overview#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific3.vb#19)]  
  
 Çağırarak bir sayısal değer belirli bir kültür için biçimlendirebilirsiniz bir `ToString` sahip aşırı bir `provider` parametresi ve aşağıdakilerden birini geçirme:  
  
-   A <xref:System.Globalization.CultureInfo> , biçimlendirme kuralları kullanılacak kültür temsil eden nesne. Kendi <xref:System.Globalization.CultureInfo.GetFormat%2A?displayProperty=nameWithType> yöntemi değerini döndürür <xref:System.Globalization.CultureInfo.NumberFormat%2A?displayProperty=nameWithType> olan özelliği, <xref:System.Globalization.NumberFormatInfo> sayısal değerler için kültüre özgü biçimlendirme bilgileri sağlayan nesne.  
  
-   A <xref:System.Globalization.NumberFormatInfo> kullanılacak kültüre özgü biçimlendirme kuralları tanımlayan nesne. Kendi <xref:System.Globalization.NumberFormatInfo.GetFormat%2A> yöntemi kendi örneğini döndürür.  
  
 Aşağıdaki örnek kullanır <xref:System.Globalization.NumberFormatInfo> İngilizce (ABD) ve İngilizce (Türkiye) kültürler ve Fransızca ve Rusça nötr kültürler kayan noktalı sayı biçimlendirmek için temsil eden nesneler.  
  
 [!code-csharp[Conceptual.Formatting.Overview#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific4.cs#20)]
 [!code-vb[Conceptual.Formatting.Overview#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific4.vb#20)]  
  
<a name="dateCulture"></a>   
### <a name="culture-sensitive-formatting-of-date-and-time-values"></a>Tarih ve Saat Değerlerini Kültüre Duyarlı Olarak Biçimlendirme  
 Varsayılan olarak, tarih ve saat değerlerini biçimlendirme kültüre duyarlı. Biçimlendirme yöntemini çağırdığınızda bir kültür belirtmezseniz, geçerli iş parçacığı kültürünü biçimlendirme kuralları kullanılır. Bu, geçerli iş parçacığı kültürünü dört kez değiştirir ve çağırır aşağıdaki örnekte gösterilmiştir <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> yöntemi. Her durumda, sonuç dizesini geçerli kültür biçimlendirme kuralları yansıtır. Bunun nedeni, <xref:System.DateTime.ToString?displayProperty=nameWithType>, <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType>, <xref:System.DateTimeOffset.ToString?displayProperty=nameWithType>, ve <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> yöntemleri sarmalamak çağrıları <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> ve <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> yöntemleri.  
  
 [!code-csharp[Conceptual.Formatting.Overview#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific1.cs#17)]
 [!code-vb[Conceptual.Formatting.Overview#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific1.vb#17)]  
  
 Çağırarak bir tarih ve saat değeri belirli bir kültür için biçimlendirebilirsiniz bir <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> veya <xref:System.DateTimeOffset.ToString%2A?displayProperty=nameWithType> sahip aşırı bir `provider` parametresi ve aşağıdakilerden birini geçirme:  
  
-   A <xref:System.Globalization.CultureInfo> , biçimlendirme kuralları kullanılacak kültür temsil eden nesne. Kendi <xref:System.Globalization.CultureInfo.GetFormat%2A?displayProperty=nameWithType> yöntemi değerini döndürür <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> olan özelliği, <xref:System.Globalization.DateTimeFormatInfo> tarih ve saat değerleri için kültüre özgü biçimlendirme bilgileri sağlayan nesne.  
  
-   A <xref:System.Globalization.DateTimeFormatInfo> kullanılacak kültüre özgü biçimlendirme kuralları tanımlayan nesne. Kendi <xref:System.Globalization.DateTimeFormatInfo.GetFormat%2A> yöntemi kendi örneğini döndürür.  
  
 Aşağıdaki örnek kullanır <xref:System.Globalization.DateTimeFormatInfo> İngilizce (ABD) ve İngilizce (Türkiye) kültürler ve Fransızca ve Rusça nötr kültürler bir tarih biçimine temsil eden nesneler.  
  
 [!code-csharp[Conceptual.Formatting.Overview#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific2.cs#18)]
 [!code-vb[Conceptual.Formatting.Overview#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific2.vb#18)]  
  
<a name="IFormattable"></a>   
## <a name="the-iformattable-interface"></a>IFormattable Arabirimi  
 Genellikle, bu aşırı yüklemesi'ni türleri `ToString` bir biçim dizesi yöntemiyle ve bir <xref:System.IFormatProvider> parametresi de uygulamak <xref:System.IFormattable> arabirimi. Bu arabirim tek bir üyeye sahip <xref:System.IFormattable.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>, parametre olarak bir biçim dizesi ve bir biçim sağlayıcısı dahildir.  
  
 Uygulama <xref:System.IFormattable> uygulama tanımlı sınıfınız iki avantajlar sunar için arabirim:  
  
-   Dize dönüştürme için destek <xref:System.Convert> sınıfı. Çağrılar <xref:System.Convert.ToString%28System.Object%29?displayProperty=nameWithType> ve <xref:System.Convert.ToString%28System.Object%2CSystem.IFormatProvider%29?displayProperty=nameWithType> yöntem çağrısı, <xref:System.IFormattable> uygulama otomatik olarak.  
  
-   Bileşik biçimlendirme desteği. Bir biçim öğesini içeriyorsa, özel türünüz biçimlendirmek için kullanılan biçim dizesi, ortak dil çalışma zamanı otomatik olarak çağırır, <xref:System.IFormattable> uygulama ve biçim dizesi geçirir. Bileşik yöntemleriyle gibi biçimlendirme hakkında daha fazla bilgi için <xref:System.String.Format%2A?displayProperty=nameWithType> veya <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, bkz: [bileşik biçimlendirme](#CompositeFormatting) bölümü.  
  
 Aşağıdaki örnek tanımlayan bir `Temperature` uygulayan sınıf <xref:System.IFormattable> arabirimi. "C" veya "G" Sıcaklık derece içinde görüntülemek için biçim belirticileri, fahrenhayt sıcaklık görüntülemek için "F" biçim belirticisi ve "K" biçim belirticisi Kelvin sıcaklık görüntülenecek destekler.  
  
 [!code-csharp[Conceptual.Formatting.Overview#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/iformattable.cs#12)]
 [!code-vb[Conceptual.Formatting.Overview#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/iformattable.vb#12)]  
  
 Aşağıdaki örnek başlatır bir `Temperature` nesnesi. Daha sonra çağırır <xref:System.Convert.ToString%2A> yöntemi ve farklı almak için birkaç bileşik biçim dizeleri dize gösterimlerini kullanan bir `Temperature` nesnesi. Bu yöntem çağrılarının her sırayla çağırır <xref:System.IFormattable> uyarlamasını `Temperature` sınıfı.  
  
 [!code-csharp[Conceptual.Formatting.Overview#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/iformattable.cs#13)]
 [!code-vb[Conceptual.Formatting.Overview#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/iformattable.vb#13)]  
  
 [Başa dön](#Introduction)  
  
<a name="CompositeFormatting"></a>   
## <a name="composite-formatting"></a>Bileşik Biçimlendirme  
 Bazı yöntemler gibi <xref:System.String.Format%2A?displayProperty=nameWithType> ve <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>, bileşik biçimlendirme destekler. Bileşik biçimlendirme dizesi sıfır, bir veya daha çok nesne dize gösterimini içeren tek bir dize döndürür şablon türüdür. Her nesne bileşik biçim dizesi içinde bir dizini oluşturulmuş biçimi öğe tarafından temsil edilir. Biçim öğenin dizini yöntemin parametre listesinde temsil eden nesne konumunu karşılık gelir. Sıfır tabanlı dizin. Örneğin, aşağıdaki çağrı <xref:System.String.Format%2A?displayProperty=nameWithType> yöntemi, ilk biçimi öğesi `{0:D}`, tarafından dize gösterimini değiştirilir `thatDate`; ikinci biçimi öğesi `{1}`, dizegösteriminitarafındandeğiştirilir`item1`; ve üçüncü biçimi öğesi `{2:C2}`, tarafından dize gösterimini değiştirilir `item1.Value`.  
  
 [!code-csharp[Conceptual.Formatting.Overview#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/composite1.cs#14)]
 [!code-vb[Conceptual.Formatting.Overview#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/composite1.vb#14)]  
  
 Bir biçim öğesi kendi ilgili nesnenin dize gösterimini ile değiştirerek yanı sıra biçim öğeleri de aşağıdaki denetlemenize olanak tanıyan:  
  
-   Özel yolu içinde nesne uyguluyorsa, bir nesne bir dize olarak temsil edilen <xref:System.IFormattable> arabirim ve biçim dizeleri destekler. Biçim öğesi'nin diziniyle izleyerek bunu bir `:` (üste) göre geçerli biçim dizesi. Önceki örnekte bu "d" (kısa tarih düzeni) biçim dizesi içeren bir date değeri biçimlendirme tarafından mı (örn., `{0:d}`) ve "C2" ile bir sayısal değer biçimlendirme tarafından biçim dizesi (örn., `{2:C2}` numarasını iki para birimi değeri olarak göstermek için kesirli ondalık basamak.  
  
-   Nesnenin dize gösterimini ve bu alandaki dize gösterimi hizalamasını içeren alanın genişliği. Biçim öğesi'nin diziniyle izleyerek bunu bir `,` (virgül) ve ardından alan genişliği. Dize alan genişliği pozitif bir değer ise ve onu soldan alan genişliği negatif bir değer ise hizalanır sağa hizalı alanıdır. Aşağıdaki örnek sol-20 karakter alanındaki tarih değerleri, ve onu sağ-ondalık değerleri 11 karakterlik bir alanda bir kesirli rakam ile hizalar.  
  
     [!code-csharp[Conceptual.Formatting.Overview#22](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/composite2.cs#22)]
     [!code-vb[Conceptual.Formatting.Overview#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/composite2.vb#22)]  
  
     Hizalama dize bileşeni ve biçim dizesi bileşen varsa, önceki ikinci önündeki, Not (örneğin, `{0,-20:g}`.  
  
 Bileşik biçimlendirme hakkında daha fazla bilgi için bkz: [bileşik biçimlendirme](../../../docs/standard/base-types/composite-formatting.md).  
  
 [Başa dön](#Introduction)  
  
<a name="Custom"></a>   
## <a name="custom-formatting-with-icustomformatter"></a>ICustomFormatter ile Özel Biçimlendirme  
 İki bileşik biçimlendirme yöntemi <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> ve <xref:System.Text.StringBuilder.AppendFormat%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>, özel biçimlendirme destekleyen bir biçim sağlayıcısı parametresini ekleyin. Biçimlendirme yöntemlerine bunlardan çağrıldığında geçirmeden bir <xref:System.Type> temsil eden nesnesi bir <xref:System.ICustomFormatter> arabirimi biçimi sağlayıcısının <xref:System.IFormatProvider.GetFormat%2A> yöntemi. <xref:System.IFormatProvider.GetFormat%2A> Yöntemi döndürmek için sorumlu sonra <xref:System.ICustomFormatter> özel biçimlendirme sağlayan uygulama.  
  
 <xref:System.ICustomFormatter> Arabirimi sahip tek bir yöntem <xref:System.ICustomFormatter.Format%28System.String%2CSystem.Object%2CSystem.IFormatProvider%29>, yani her bir bileşik biçim dizesi biçimi öğe için bir kez yöntemi biçimlendirme bileşik tarafından otomatik olarak çağrılır. <xref:System.ICustomFormatter.Format%28System.String%2CSystem.Object%2CSystem.IFormatProvider%29> Yöntemi sahip üç parametre: temsil eden bir biçim dizesi `formatString` bağımsız değişkeni bir biçim öğesinde biçimlendirmek için bir nesne ve bir <xref:System.IFormatProvider> biçimlendirme sağlayan nesne Hizmetleri. Genellikle, uygulayan sınıf <xref:System.ICustomFormatter> de uygulayan <xref:System.IFormatProvider>bu son parametre özel biçimlendirme başvuru sınıfının kendisini gelir. Yöntemi nesnenin biçimlendirilmesi için özel biçimlendirilmiş dize gösterimini döndürür. Yöntemin Nesne biçimlendirilemez, bir null başvuru döndürmelidir (`Nothing` Visual Basic'te).  
  
 Aşağıdaki örnek sağlayan bir <xref:System.ICustomFormatter> adlı uygulama `ByteByByteFormatter` bir boşluk bırakarak iki basamaklı onaltılık değerler dizisi olarak tamsayı değerlerini görüntüleyen.  
  
 [!code-csharp[Conceptual.Formatting.Overview#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/icustomformatter1.cs#15)]
 [!code-vb[Conceptual.Formatting.Overview#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/icustomformatter1.vb#15)]  
  
 Aşağıdaki örnek kullanır `ByteByByteFormatter` tamsayı değerlerini biçimlendirmek için sınıf. Unutmayın <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> yöntemi saniye içinde birden çok kez çağrılır <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> yöntem çağrısı ve varsayılan <xref:System.Globalization.NumberFormatInfo> çünkü sağlayıcı üçüncü yöntem çağrısı kullanılır.`ByteByByteFormatter.Format` yöntem "N0" biçim dizesi tanımıyor ve null bir başvuru döndürür (`Nothing` Visual Basic'te).  
  
 [!code-csharp[Conceptual.Formatting.Overview#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/icustomformatter1.cs#16)]
 [!code-vb[Conceptual.Formatting.Overview#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/icustomformatter1.vb#16)]  
  
 [Başa dön](#Introduction)  
  
<a name="RelatedTopics"></a>   
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Tanım|  
|-----------|----------------|  
|[Standart sayısal biçim dizeleri](../../../docs/standard/base-types/standard-numeric-format-strings.md)|Sayısal değerleri yaygın olarak kullanılan dize temsilini oluşturmak standart biçim dizeleri açıklar.|  
|[Özel sayısal biçim dizeleri](../../../docs/standard/base-types/custom-numeric-format-strings.md)|Sayısal değerler için uygulamaya özgü biçimi oluşturmanıza özel biçim dizeleri açıklar.|  
|[Standart tarih ve saat biçim dizeleri](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)|Yaygın olarak kullanılan dize temsilini oluşturmak standart biçim dizeleri açıklar <xref:System.DateTime> değerleri.|  
|[Özel tarih ve saat biçim dizeleri](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)|Uygulamaya özgü biçimleri için oluşturduğunuz özel biçim dizeleri açıklar <xref:System.DateTime> değerleri.|  
|[Standart TimeSpan biçim dizeleri](../../../docs/standard/base-types/standard-timespan-format-strings.md)|Zaman aralıkları yaygın olarak kullanılan dize temsilini oluşturmak standart biçim dizeleri açıklar.|  
|[Özel TimeSpan biçim dizeleri](../../../docs/standard/base-types/custom-timespan-format-strings.md)|Zaman aralıkları için uygulamaya özgü biçimleri oluşturma özel biçim dizeleri açıklar.|  
|[Numaralandırma biçimi dizeleri](../../../docs/standard/base-types/enumeration-format-strings.md)|Numaralandırma değerlerinin dize temsilini oluşturmak için kullanılan standart biçim dizeleri açıklar.|  
|[Bileşik biçimlendirme](../../../docs/standard/base-types/composite-formatting.md)|Bir veya daha fazla biçimlendirilmiş değer bir dize katıştırmak açıklar. Dize daha sonra konsolda görüntülenmez veya bir akışa yazılan.|  
|[Biçimlendirme işlemlerini gerçekleştirme](../../../docs/standard/base-types/performing-formatting-operations.md)|Belirli biçimlendirme işlemlerini gerçekleştirmek için adım adım yönergeler sağlar konuları listeler.|  
|[Dizeleri ayrıştırma](../../../docs/standard/base-types/parsing-strings.md)|Nesneleri bu nesnelerin dizesi ifadeleri tarafından tanımlanan değerlerle başlatmak açıklar. Ayrıştırma, biçimlendirme ters bir işlemdir.|  
  
 [Başa dön](#Introduction)  
  
<a name="Reference"></a>   
## <a name="reference"></a>Başvuru  
 <xref:System.IFormattable?displayProperty=nameWithType>  
  
 <xref:System.IFormatProvider?displayProperty=nameWithType>  
  
 <xref:System.ICustomFormatter?displayProperty=nameWithType>
