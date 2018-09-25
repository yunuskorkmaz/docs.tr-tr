---
title: .NET içinde karakter kodlaması
ms.date: 12/22/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- encoding, understanding
- encoding, choosing
- encoding, fallback strategy
ms.assetid: bf6d9823-4c2d-48af-b280-919c5af66ae9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cac7e0fca4a009b7f5b6f677abed70cf2519052d
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2018
ms.locfileid: "46711763"
---
# <a name="character-encoding-in-net"></a>.NET içinde karakter kodlaması
Karakterler, birçok farklı şekilde temsil edilebilen soyut varlıklardır. Bir karakter kodlaması, desteklenen bir karakter kümesindeki her karakteri, o karakteri temsil eden değerle eşleştiren bir sistemdir. Örneğin; Morse kodu, Roma alfabesindeki her karakteri telgraf hattı üzerinden iletilmeye uygun olan bir nokta ve çizgi deseniyle eşleştiren bir karakter kodlamasıdır. Bilgisayarlar için bir karakter kodlaması, desteklenen bir karakter kümesindeki her karakteri, o karakteri temsil eden sayısal bir değerle eşleştirir. Bir karakter kodlaması iki farklı bileşene sahiptir:  
  
-   Bir karakter dizisini sayısal değerler dizisine (baytlara) çeviren bir kodlayıcı.  
  
-   Bir bayt dizisini karakter dizisine çeviren bir kod çözücü.  
  
 Karakter kodlama, bir kodlayıcının ve kod çözücünün çalışma kurallarını açıklar. Örneğin <xref:System.Text.UTF8Encoding> sınıfı, tek bir Unicode karakterini temsil etmek için bir ile dört arasında bayt kullanan 8 bitlik Unicode Dönüştürme Biçimi (UTF-8) için kodlama ve kod çözme kurallarını açıklar. Kodlama ve kod çözme aynı zamanda doğrulamayı da içerebilir. Örneğin <xref:System.Text.UnicodeEncoding> sınıfı, geçerli yedek çiftleri olduklarından emin olmak için tüm yedekleri denetler. (Bir yedek çifti, ardından U+DC00 ile U+DFFF aralığında bir kod noktasına sahip olan bir karakter gelen U+D800 ile U+DBFF aralığında kod noktasına sahip olan bir karakterden oluşur.)  Bir geri dönüş stratejisi, bir kodlayıcının geçersiz karakterleri veya bir kod çözücünün geçersiz baytları nasıl işleyeceğini belirler.  
  
> [!WARNING]
>  .NET kodlama sınıfları, depolamak ve karakter verileri dönüştürmek için bir yol sağlar. İkili verileri dize biçiminde depolamak için kullanılmamaları gerekir. Kullanılan kodlamaya bağlı olarak, kodlama sınıflarıyla ikili veriyi dize biçimine dönüştürmek beklenmedik davranışa sebep olabilir ve doğru olmayan ya da bozuk veriler üretebilir. İkili verileri bir dize biçimine dönüştürmek için, <xref:System.Convert.ToBase64String%2A?displayProperty=nameWithType> yöntemini kullanın.  
  
 .NET, UTF-16 kodlaması kullanır (tarafından temsil edilen <xref:System.Text.UnicodeEncoding> sınıfı) karakterleri ve dizeleri temsil etmek için. Ortak dil çalışma zamanını hedef alan uygulamalar, ortak dil çalışma zamanı tarafından desteklenen Unicode karakter temsillerini başka kodlama düzenleriyle eşlemek için kodlayıcıları kullanır. Unicode olmayan kodlamalar daki karakterleri Unicode karakterleriyle eşlemek için kod çözücüler kullanırlar.  
  
 Bu konu aşağıdaki bölümlerden oluşur:  
  
-   [. NET'te kodlamaları](../../../docs/standard/base-types/character-encoding.md#Encodings)  
  
-   [Bir kodlama sınıfı seçme](../../../docs/standard/base-types/character-encoding.md#Selecting)  
  
-   [Using an Encoding Object](../../../docs/standard/base-types/character-encoding.md#Using)  
  
-   [Bir geri dönüş stratejisini seçme](../../../docs/standard/base-types/character-encoding.md#FallbackStrategy)  
  
-   [Özel bir geri dönüş stratejisi uygulamak](../../../docs/standard/base-types/character-encoding.md#Custom)  
  
<a name="Encodings"></a>   
## <a name="encodings-in-net"></a>. NET'te kodlamaları  
 Tüm karakter kodlama sınıfları, .NET devralmanız <xref:System.Text.Encoding?displayProperty=nameWithType> tüm karakter kodlamalarına ortak olan işlevselliği tanımlayan soyut bir sınıf olan sınıf. .NET içinde uygulanan kodlama nesnelerine tek tek erişmek için aşağıdakileri yapın:  
  
-   Statik özelliklerini kullanın <xref:System.Text.Encoding> nesneleri döndüren bir sınıfı temsil eden standart karakter kodlamalarını (ASCII, UTF-7, UTF-8, UTF-16 ve UTF-32) .NET içinde kullanılabilir. Örneğin, <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> özelliği bir <xref:System.Text.UnicodeEncoding> nesnesini döndürür. Her bir nesne, kodlayamadığı dizeleri ve kodunu çözemediği baytları işlemek için değiştirme geri dönüşünü kullanır. (Daha fazla bilgi için [değiştirme geri dönüşü](../../../docs/standard/base-types/character-encoding.md#Replacement) bölümüne.)  
  
-   Kodlamanın sınıf oluşturucusunu çağırın. ASCII, UTF-7, UTF-8, UTF-16 ve UTF-32 kodlamalarına ait nesneler bu şekilde örneklenebilir. Varsayılan olarak her nesne, kodlayamadığı dizeleri ve kodunu çözemediği baytları işlemek için değiştirme geri dönüşünü kullanır, ancak bunun yerine bir özel durumun oluşturulmasını da belirtebilirsiniz. (Daha fazla bilgi için [değiştirme geri dönüşü](../../../docs/standard/base-types/character-encoding.md#Replacement) ve [özel durum geri dönüşü](../../../docs/standard/base-types/character-encoding.md#Exception) bölümleri.)  
  
-   <xref:System.Text.Encoding.%23ctor%28System.Int32%29?displayProperty=nameWithType> oluşturucusunu çağırın ve kodlamayı temsil eden bir tamsayı geçirin. Kodlanamayan dizeleri ve kodu çözülemeyen baytları işlemek için, standart kodlama nesneleri değiştirme geri dönüşünü kullanır ve kod sayfası ile çift bayt karakter kümesi (DBCS) kodlama nesneleri, en uygun geri dönüşü kullanır. (Daha fazla bilgi için [en uygun geri dönüş](../../../docs/standard/base-types/character-encoding.md#BestFit) bölümüne.)  
  
-   Çağrı <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> herhangi standart, kod sayfası veya DBCS kodlamasını. NET'te kullanılabilir döndüren yöntemi. Aşırı yüklemeler, hem kodlayıcı hem de kod çözücü için bir geri dönüş nesnesi belirtmenizi sağlar.  
  
> [!NOTE]
>  Unicode Standardı, desteklenen tüm betiklerde her karaktere bir kod noktası (bir sayı) ve bir ad atar. Örneğin "A" karakteri, U+0041 kod noktası ile ve "LATIN BÜYÜK HARF A" adıyla temsil edilir. Unicode Dönüştürme Biçimi (UTF) kodlamaları, bu kod noktasını bir veya daha fazla bayt dizisi olarak kodlamanın yollarını tanımlar. Bir Unicode kodlama düzeni, herhangi bir karakter kümesindeki karakterlerin tek bir kodlama içinde temsil edilmesini sağladığından, dünya çapında kullanılmaya hazır uygulama geliştirmeyi basitleştirir. Uygulama geliştiricilerin artık belirli bir dil veya yazı sistemi için karakter oluşturmakta kullanılan kodlama düzenini takip etmesine gerek yoktur ve veriler bozulmadan sistemler arasında uluslararası olarak paylaşılabilir.  
>   
>  .NET Unicode standardı tarafından tanımlanan üç kodlamayı destekler: UTF-8, UTF-16 ve UTF-32. Daha fazla bilgi için bkz. konumundaki Unicode standardı [Unicode ana sayfa](https://www.unicode.org/).  
  
 Çağırarak .NET içinde kullanılabilir olan tüm Kodlamalar hakkında bilgi alabilirsiniz <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=nameWithType> yöntemi. .NET karakter kodlama sistemlerini aşağıdaki tabloda listelenen destekler.  
  
|Kodlama|örneği|Açıklama|Avantajlar/dezavantajlar|  
|--------------|-----------|-----------------|-------------------------------|  
|ASCII|<xref:System.Text.ASCIIEncoding>|Bir baytın alt yedi bitini kullanarak sınırlı bir karakter aralığını kodlar.|Bu kodlama yalnızca U+0000 ile U+007F arasındaki karakter değerlerini desteklediğinden, çoğu zaman uluslararası uygulamalar için yeterli değildir.|  
|UTF-7|<xref:System.Text.UTF7Encoding>|Karakterleri 7-bitlik ASCII karakter dizileri olarak temsil eder. ASCII olmayan Unicode karakterleri, ASCII karakterlerinin bir kaçış dizisi ile temsil edilir.|UTF-7, e-posta gibi protokoller ve haber grubu protokolleri destekler. Ancak, UTF-7 özellikle güvenli veya sağlam değildir. Bazı durumlarda bir biti değiştirmek, bütün bir UTF-7 dizesinin yorumunu tamamen değiştirebilir. Diğer durumlarda, farklı UTF-7 dizeleri aynı metni kodlayabilir. ASCII olmayan karakterleri içeren diziler için UTF-7, UTF-8'den daha fazla alan gerektirir ve kodlama/kod çözme daha yavaştır. Sonuç olarak, mümkünse UTF-7 yerine UTF-8 kullanmanız gerekir.|  
|UTF-8|<xref:System.Text.UTF8Encoding>|Her Unicode kod noktasını bir ile dört bayt arası bir dizi olarak temsil eder.|UTF-8, 8 bitlik veri boyutlarını destekler ve mevcut çoğu işletim sistemi ile çalışır. ASCII aralığındaki karakterler için, UTF-8 ASCII kodlaması ile aynıdır ve daha geniş bir karakter kümesi sağlar. Ancak, Çince-Japonca-Korece (CJK) betikleri için UTF-8, her karakter için üç bayt gerektirir ve UTF-16'dan daha büyük veri boyutlarına neden olabilir. Bazen HTML etiketleri gibi ASCII verilerinin miktarının, CJK aralığındaki artan boyutu haklı çıkarabilir, buna dikkat edin.|  
|UTF-16|<xref:System.Text.UnicodeEncoding>|Her Unicode kod noktasını bir veya iki 16 bitlik tamsayı dizisi olarak temsil eder. En yaygın Unicode karakterleri yalnızca bir UTF-16 kod noktası gerektirir, ancak Unicode ek karakterleri (U+10000 ve daha üstü) iki UTF-16 yedek kod noktası gerektirir. Küçük endian ve büyük endian bayt sıralarının her ikisi de desteklenir.|UTF-16 kodlaması ortak dil çalışma zamanı tarafından <xref:System.Char> ve <xref:System.String> değerlerini ve Windows işletim sistemi tarafından `WCHAR` değerlerini temsil etmek için kullanılır.|  
|UTF-32|<xref:System.Text.UTF32Encoding>|Her Unicode kod noktasını bir 32-bit tamsayı olarak temsil eder. Küçük endian ve büyük endian bayt sıralarının her ikisi de desteklenir.|UTF-32 kodlama, uygulamalar kodlama alanının çok önemli olduğu işletim sistemlerinde UTF-16 kodlama davranışının yedek kod noktası davranışından kaçınmak istediğinde kullanılır. Görüntü üzerinde işlenen tek simgeler hala birden fazla UTF-32 karakteriyle kodlanabilir.|  
|ANSI/ISO kodlamaları||Çeşitli kod sayfaları için destek sağlar. Windows işletim sistemlerinde, kod sayfaları belirli bir dili veya dil grubunu desteklemek için kullanılır. .NET tarafından desteklenen kod sayfalarını listeleyen bir tablo için bkz: <xref:System.Text.Encoding> sınıfı. <xref:System.Text.Encoding.GetEncoding%28System.Int32%29?displayProperty=nameWithType> yöntemini çağırarak belirli bir kod sayfası için bir kodlama nesnesi alabilirsiniz.|Bir kod sayfası 256 kod noktası içerir ve sıfır tabanlıdır. Çoğu kod sayfasında, 0 ile 127 arasındaki kod noktaları ASCII karakter kümesini temsil eder, ve 128 ile 255 arasındaki kod noktaları kod sayfaları arasında önemli ölçüde değişir. Örneğin kod sayfası 1252; İngilizce, Almanca ve Fransızca dahil olmak üzere Latin yazma sistemleri için karakterler sağlar. Kod sayfası 1252'deki son 128 kod noktası vurgu karakterlerini içerir. Kod sayfası 1253, Yunanca yazma sisteminde gerekli olan karakter kodlarını sağlar. Kod sayfası 1253'deki son 128 kod noktası Yunanca karakterleri içerir. Sonuç olarak, ANSI kod sayfalarını temel alan bir uygulama, başvurulan kod sayfasını gösteren bir tanımlayıcı eklemediği sürece aynı metin akışında Yunanca ve Almanca karakterleri depolayamaz.|  
|Çift bayt karakter kümesi (DBCS) kodlamaları||256 karakterden daha fazla karakter içeren Çince, Japonca ve Korece gibi dilleri destekler. DBCS içinde, bir kod noktası çifti (bir çift bayt), her bir karakteri temsil eder. <xref:System.Text.Encoding.IsSingleByte%2A?displayProperty=nameWithType> özelliği, DBCS kodlamaları için `false`'i döndürür. <xref:System.Text.Encoding.GetEncoding%28System.Int32%29?displayProperty=nameWithType> yöntemini çağırarak belirli bir DBCS için bir kodlama nesnesi alabilirsiniz.|DBCS içinde, bir kod noktası çifti (bir çift bayt), her bir karakteri temsil eder. Bir uygulama DBCS verilerini işlediğinde, bir DBCS karakterinin (öndeki bayt) ilk baytı, hemen ardından gelen sondaki bayt ile birlikte işlenir. Tek bir çift bayt kod noktası çifti kod sayfasına bağlı olarak farklı karakterleri temsil edebileceğinden, bu düzen yine de Japonca ve Çince gibi iki dilin aynı veri akışında bulunmasına izin vermez.|  
  
 Bu kodlamalar, hem Unicode karakterleriyle hem de eski uygulamalarda yaygın olarak kullanılan kodlamalarla birlikte çalışmanıza olanak sağlar. Ek olarak, <xref:System.Text.Encoding> sınıfından türetilen bir sınıf tanımlayarak ve üyelerini geçersiz kılarak özel bir kodlama oluşturabilirsiniz.  
  
### <a name="platform-notes-includenetcoreincludesnet-core-mdmd"></a>Platform notları: [!INCLUDE[net_core](../../../includes/net-core-md.md)]  
 Varsayılan olarak, [!INCLUDE[net_core](../../../includes/net-core-md.md)] 28591 kod sayfası dışındaki herhangi bir kod sayfası kodlamaları ve UTF-8 ve UTF-16 gibi Unicode kodlamaları kullanılabilir yapmaz. Ancak, standart Windows uygulamaları hedefleyen .NET uygulamanız için bulunan kod sayfası kodlamaları ekleyebilirsiniz. Tam bilgi için bkz. <xref:System.Text.CodePagesEncodingProvider> konu.  
  
<a name="Selecting"></a>   
## <a name="selecting-an-encoding-class"></a>Bir Kodlama Sınıfı Seçme  
 Eğer uygulamanız tarafından kullanılacak kodlamayı seçme olanağınız varsa, bir Unicode kodlamasını, tercihen <xref:System.Text.UTF8Encoding> veya <xref:System.Text.UnicodeEncoding>'i kullanmanız gerekir. (.NET de destekler üçüncü bir Unicode kodlaması, <xref:System.Text.UTF32Encoding>.)  
  
 Eğer bir ASCII kodlaması (<xref:System.Text.ASCIIEncoding>) kullanmayı planlıyorsanız, bunun yerine <xref:System.Text.UTF8Encoding>'i seçin. Bu iki kodlama ASCII karakter kümesi için aynıdır, ancak <xref:System.Text.UTF8Encoding> aşağıdaki avantajlara sahiptir:  
  
-   <xref:System.Text.ASCIIEncoding>, yalnızca U+0000 ve U+007F arasındaki Unicode karakterlerini desteklerken, bu bütün Unicode karakterlerini temsil edebilir.  
  
-   Hata algılama ve daha iyi güvenlik sağlar.  
  
-   Mümkün olduğunca hızlı olacak şekilde ayarlanmıştır ve diğer kodlamalardan daha hızlı olmalıdır. Tamamen ASCII olan içerik için bile, <xref:System.Text.UTF8Encoding> ile yapılan işlemler <xref:System.Text.ASCIIEncoding> ile yapılan işlemlerden daha hızlıdır.  
  
 <xref:System.Text.ASCIIEncoding> kodlamasını yalnızca eski uygulamalar için kullanmayı düşünmelisiniz. Ancak, eski uygulamalar için bile, <xref:System.Text.UTF8Encoding> aşağıdaki nedenlerden dolayı (varsayılan ayarların olduğunu düşünerek) daha iyi bir seçimdir:  
  
-   Eğer uygulamanız tamamen ASCII olmayan içeriğe sahipse ve bunu <xref:System.Text.ASCIIEncoding> ile kodlarsa ASCII olmayan her bir karakter, bir soru işareti (?) olarak kodlanır. Eğer sonra uygulama bu verinin kodunu çözerse, bilgi kaybolur.  
  
-   Eğer uygulamanız tamamen ASCII olmayan içeriğe sahipse ve bunu <xref:System.Text.UTF8Encoding> ile kodlarsa, ASCII olarak yorumlandığında sonuç anlamsız görünebilir. Ancak ardından uygulama, bu verinin kodunu çözmek için bir UTF-8 kod çözücü kullanırsa veriler, gidiş dönüşü başarıyla tamamlar.  
  
 Bir web uygulamasında, bir web isteğine karşılık olarak istemciye gönderilen karakterler istemcide kullanılan kodlamayı yansıtmalıdır. Çoğu durumda, metni kullanıcının beklediği kodlamayla görüntülemek için <xref:System.Web.HttpResponse.ContentEncoding%2A?displayProperty=nameWithType> özelliğini <xref:System.Web.HttpRequest.ContentEncoding%2A?displayProperty=nameWithType> özelliği tarafından döndürülen değere ayarlamanız gerekir.  
  
<a name="Using"></a>   
## <a name="using-an-encoding-object"></a>Using an Encoding Object  
 Bir kodlayıcı, bir karakter dizesini (genellikle Unicode karakterleri) sayısal (bayt) eşdeğerine dönüştürür. Örneğin, Unicode karakterlerini dönüştürmek için bir ASCII kodlayıcısı kullanabilirsiniz ve bu sayede bunların konsolda görüntülenmelerini sağlayabilirsiniz. Dönüşümü gerçekleştirmek için, <xref:System.Text.Encoding.GetBytes%2A?displayProperty=nameWithType> yöntemini çağırın. Eğer kodlanmış karakterlerin depolanması için kaç bayt gerektiğini kodlamayı gerçekleştirmeden önce belirlemek istiyorsanız, <xref:System.Text.Encoding.GetByteCount%2A> yöntemini çağırabilirsiniz.  
  
 Aşağıdaki örnek, dizeleri iki ayrı işlemde kodlamak için tek bir bayt dizisini kullanır. Bayt dizisinde, sonraki ASCII kodlamalı bayt kümesinin başlangıç konumunu belirten bir dizin tutar. Bayt dizisinin kodlanmış dizeyi tutabilecek kadar büyük olduğundan emin olmak için <xref:System.Text.ASCIIEncoding.GetByteCount%28System.String%29?displayProperty=nameWithType> yöntemini çağırır. Ardından dizedeki karakterleri kodlamak için <xref:System.Text.ASCIIEncoding.GetBytes%28System.String%2CSystem.Int32%2CSystem.Int32%2CSystem.Byte%5B%5D%2CSystem.Int32%29?displayProperty=nameWithType> yöntemini çağırır.  
  
 [!code-csharp[Conceptual.Encoding#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/getbytes1.cs#8)]
 [!code-vb[Conceptual.Encoding#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/getbytes1.vb#8)]  
  
 Bir kod çözücü, belirli bir karakter kodlamasını yansıtan bayt dizisini, bir karakter dizisi veya dize olarak karakter kümesine dönüştürür. Bir bayt dizisinin karakter dizisi olarak kodunu çözmek için <xref:System.Text.Encoding.GetChars%2A?displayProperty=nameWithType> yöntemini çağırın. Bir bayt dizisinin dize olarak kodunu çözmek için <xref:System.Text.Encoding.GetString%2A> yöntemini çağırın. Eğer kodu çözülmüş baytların depolanması için kaç karakter gerektiğini kodlamayı gerçekleştirmeden önce belirlemek istiyorsanız, <xref:System.Text.Encoding.GetCharCount%2A> yöntemini çağırabilirsiniz.  
  
 Aşağıdaki örnek üç dizeyi kodlar ve ardından tek bir karakter dizisi olarak kodunu çözer. Karakter dizisinde sonraki kodu çözülmüş karakter kümesinin başlangıç konumunu belirten bir dizin tutar. Karakter dizisinin kodu çözülmüş tüm karakterleri tutacak kadar büyük olduğundan emin olmak için <xref:System.Text.ASCIIEncoding.GetCharCount%2A> yöntemini çağırır. Ardından bayt dizisinin kodunu çözmek için <xref:System.Text.ASCIIEncoding.GetChars%28System.Byte%5B%5D%2CSystem.Int32%2CSystem.Int32%2CSystem.Char%5B%5D%2CSystem.Int32%29?displayProperty=nameWithType> yöntemini çağırır.  
  
 [!code-csharp[Conceptual.Encoding#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/getchars1.cs#9)]
 [!code-vb[Conceptual.Encoding#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/getchars1.vb#9)]  
  
 <xref:System.Text.Encoding> sınıfından türetilen bir sınıfın kodlama ve kod çözme yöntemleri, tam bir veri kümesi ile çalışacak şekilde tasarlanmıştır; yani, kodlanacak veya kodu çözülecek tüm veriler tek bir yöntem çağrısında sağlanır. Ancak, bazı durumlarda veriler bir akışta bulunabilir ve kodlanacak ya da kodu çözülecek veriler yalnızca ayrı okuma işlemleri ile kullanılabilir olabilir. Bu, kodlama veya kod çözme işleminin önceki çağrıda kaydedilen durumunu hatırlamasını gerektirir. <xref:System.Text.Encoder> ve <xref:System.Text.Decoder> sınıflarından türetilen sınıfların yöntemleri, birden çok yöntem çağrısına yayılan kodlama ve kod çözme işlemlerini işleyebilir.  
  
 Belirli bir kodlamaya ait bir <xref:System.Text.Encoder> nesnesi, o kodlamanın <xref:System.Text.Encoding.GetEncoder%2A?displayProperty=nameWithType> özelliğinden kullanılabilir. Belirli bir kodlamaya ait bir <xref:System.Text.Decoder> nesnesi, o kodlamanın <xref:System.Text.Encoding.GetDecoder%2A?displayProperty=nameWithType> özelliğinden kullanılabilir. Kod çözme işlemleri için, <xref:System.Text.Decoder> sınıfından türetilen sınıfların bir <xref:System.Text.Decoder.GetChars%2A?displayProperty=nameWithType> yöntemi içerdiğine, ancak <xref:System.Text.Encoding.GetString%2A?displayProperty=nameWithType> yöntemine karşılık gelen bir yöntemleri olmadığına dikkat edin.  
  
 Aşağıdaki örnek, bir Unicode bayt dizisinin kodunu çözmek için <xref:System.Text.Encoding.GetChars%2A?displayProperty=nameWithType> ve <xref:System.Text.Decoder.GetChars%2A?displayProperty=nameWithType> yöntemlerinin kullanılması arasındaki farkı gösterir. Bu örnek, bazı Unicode karakterleri içeren bir dizeyi dosya içine kodlar ve ardından iki kod çözme yöntemini kullanarak tek seferde on bayt olacak şekilde kodlarını çözer. Onuncu ve on birinci baytlarda bir yedek çifti olduğu için kodu, ayrı yöntem çağrılarında çözülür. Çıktının gösterdiği gibi <xref:System.Text.Encoding.GetChars%2A?displayProperty=nameWithType> yöntemi, baytların kodunu doğru şekilde çözemez ve bunun yerine onları U+FFFD (DEĞİŞTİRME KARAKTERİ) ile değiştirir. Diğer taraftan <xref:System.Text.Decoder.GetChars%2A?displayProperty=nameWithType> yöntemi, bayt dizisinin kodunu başarıyla çözerek özgün dizeye ulaşır.  
  
 [!code-csharp[Conceptual.Encoding#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/stream1.cs#10)]
 [!code-vb[Conceptual.Encoding#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/stream1.vb#10)]  
  
<a name="FallbackStrategy"></a>   
## <a name="choosing-a-fallback-strategy"></a>Choosing a Fallback Strategy  
 Bir yöntem, bir karakter için kodlamayı veya kod çözmeyi denediğinde ancak hiçbir eşleme bulunmadığında, başarısız olan eşlemenin nasıl işleneceğini belirleyen bir geri dönüş stratejisi uygulanmalıdır. Üç çeşit geri dönüş stratejisi bulunur:  
  
-   En uygun geri dönüş  
  
-   Değiştirme geri dönüşü  
  
-   Özel durum geri dönüşü  
  
> [!IMPORTANT]
>  Kodlama işlemlerindeki en yaygın sorunlar, bir Unicode karakteri belirli bir kod sayfası kodlamasıyla eşlenemediğinde ortaya çıkar. Kod çözme işlemlerindeki en yaygın sorunlar, geçersiz bayt dizileri geçerli Unicode karakterlerine çevrilemediğinde ortaya çıkar. Bu nedenlerden dolayı, belirli bir kodlama nesnesinin hangi geri dönüş stratejisini kullandığını bilmeniz gerekir. Mümkün olduğunda, bir kodlama nesnesinin kullandığı geri dönüş stratejisini nesnenin örneğini oluştururken belirtmeniz gerekir.  
  
<a name="BestFit"></a>   
### <a name="best-fit-fallback"></a>En Uygun Geri Dönüş  
 Bir karakter hedef kodlamada tam bir eşleşmeye sahip olmadığında, kodlayıcı bu karakteri benzer bir karakterle eşlemeyi deneyebilir. (En uygun geri dönüş genellikle bir kod çözme sorunu değil, bir kodlama sorunudur. Unicode ile başarıyla eşlenemeyen karakterleri içeren çok az kod sayfası vardır.) En uygun geri dönüş, <xref:System.Text.Encoding.GetEncoding%28System.Int32%29?displayProperty=nameWithType> ve <xref:System.Text.Encoding.GetEncoding%28System.String%29?displayProperty=nameWithType> aşırı yüklemeleri tarafından alınan kod sayfası ve çift bayt karakter kümesi kodlamaları için varsayılandır.  
  
> [!NOTE]
>  Teorik olarak sağlanan .NET Unicode kodlama sınıfları (<xref:System.Text.UTF8Encoding>, <xref:System.Text.UnicodeEncoding>, ve <xref:System.Text.UTF32Encoding>) en uygun geri dönüş sorunlarını gidermek için kullanılabilir her karakter kümesindeki her karakteri desteğini.  
  
 En uygun stratejiler, farklı kod sayfalarına göre değişir. Örneğin, bazı kod sayfalarında tam genişlikteki Latin karakterler, daha yaygın olan yarım genişlikteki Latin karakterlerle eşlenir. Diğer kod sayfaları için bu eşleme yapılmaz. Agresif bir en uygun stratejide bile, bazı kodlamalardaki bazı karakterler için mümkün olan hiçbir uygun karakter yoktur. Örneğin, bir Çince ideogramın kod sayfası 1252 için hiçbir mantıklı eşlemesi yoktur. Bu durumda, bir değiştirme dizesi kullanılır. Varsayılan olarak bu dize, yalnızca tek bir SORU İŞARETİ (U+003F) karakteridir.  
  
> [!NOTE]
>  En uygun stratejiler, ayrıntılı olarak belgelenmemiştir. Ancak, çeşitli kod sayfaları bölümünde verilmiştir [Unicode Consortium'ın](https://www.unicode.org/Public/MAPPINGS/VENDORS/MICSFT/WindowsBestFit/) Web sitesi. Lütfen inceleyin **readme.txt** klasördeki bir dosya eşleme dosyaları yorumlama açıklaması.
  
 Aşağıdaki örnek, kod sayfası 1252'yi (Batı Avrupa dilleri için Windows kod sayfası) kullanarak en uygun eşlemeyi ve bunun dezavantajlarını gösterir. Kod sayfası 1252 için bir kodlama nesnesi almak üzere <xref:System.Text.Encoding.GetEncoding%28System.Int32%29?displayProperty=nameWithType> yöntemi kullanılır. Varsayılan olarak, desteklemediği Unicode karakterleri için bir en uygun eşleme kullanır. Örnek; boşluklarla ayrılan, ASCII olmayan üç karakteri içeren bir dizeyi örnekler - DAİRELİ LATIN BÜYÜK HARF S (U+24C8), ÜST SİMGE BEŞ (U+2075) ve SONSUZLUK (U+221E). Örneğin çıktısının gösterdiği üzere, dize kodlandığında boşluk olmayan üç orijinal karakter, SORU İŞARETİ (U+003F), BEŞ BASAMAĞI (U+0035) ve SEKİZ BASAMAĞI (U+0038) ile değiştirilir. Özellikle SEKİZ BASAMAĞI, desteklenmeyen SONSUZLUK karakteri için kötü bir değiştirmedir ve SORU İŞARETİ, orijinal karakter için kullanılabilir bir eşleme bulunmadığını gösterir.  
  
 [!code-csharp[Conceptual.Encoding#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/bestfit1.cs#1)]
 [!code-vb[Conceptual.Encoding#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/bestfit1.vb#1)]  
  
 En uygun eşleme, Unicode verilerini kod sayfası verisine kodlayan bir <xref:System.Text.Encoding> nesnesi için varsayılan davranıştır ve bu davranışı kullanan eski uygulamalar vardır. Ancak, güvenlik gerekçesiyle çoğu yeni uygulamanın, en uygun davranışından kaçınması gerekir. Örneğin, uygulamalar bir etki alanı adını en uygun kodlama ile koymamalıdır.  
  
> [!NOTE]
>  Bir kodlama için aynı zamanda özel bir en uygun geri dönüş eşlemesi uygulayabilirsiniz. Daha fazla bilgi için [Custom Fallback Strategy uygulama](../../../docs/standard/base-types/character-encoding.md#Custom) bölümü.  
  
 Eğer en uygun geri dönüş bir kodlama nesnesi için varsayılansa, <xref:System.Text.Encoding> veya <xref:System.Text.Encoding.GetEncoding%28System.Int32%2CSystem.Text.EncoderFallback%2CSystem.Text.DecoderFallback%29?displayProperty=nameWithType> aşırı yüklemesini çağırarak bir <xref:System.Text.Encoding.GetEncoding%28System.String%2CSystem.Text.EncoderFallback%2CSystem.Text.DecoderFallback%29?displayProperty=nameWithType> nenesi aldığınızda başka bir geri dönüş stratejisi seçebilirsiniz. Aşağıdaki bölüm, kod sayfası 1252 ile eşleşemeyen her karakteri yıldız işareti (*) ile değiştiren bir örnek içerir.  
  
 [!code-csharp[Conceptual.Encoding#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/bestfit1a.cs#3)]
 [!code-vb[Conceptual.Encoding#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/bestfit1a.vb#3)]  
  
<a name="Replacement"></a>   
### <a name="replacement-fallback"></a>Değiştirme Geri Dönüşü  
 Bir karakterin hedef düzende tam eşleşmesi olmadığında ancak eşlenebileceği hiçbir uygun karakter bulunmadığında, uygulama bir değişim karakteri veya dizesi belirtebilir. Bu, kodunu çözemediği herhangi bir iki baytlık diziyi DEĞİŞİM_KARAKTERİ (U+FFFD) ile değiştiren Unicode kod çözücünün varsayılan davranışıdır. Bu ayrıca, kodlayamadığı veya kodunu çözemediği her karakteri bir soru işareti ile değiştiren <xref:System.Text.ASCIIEncoding> sınıfının da varsayılan davranışıdır. Aşağıdaki örnek, önceki örnekteki Unicode dizesi için karakter değiştirmeyi gösterir. Çıktının gösterdiği üzere bir ASCII bayt değeri olarak kodu çözülemeyen her karakter,bir soru işareti için ASCII kodu olan 0x3F ile değiştirilir.  
  
 [!code-csharp[Conceptual.Encoding#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/replacementascii.cs#2)]
 [!code-vb[Conceptual.Encoding#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/replacementascii.vb#2)]  
  
 .NET içeren <xref:System.Text.EncoderReplacementFallback> ve <xref:System.Text.DecoderReplacementFallback> bir karakter tam olarak bir kodlama veya kod çözme işleminde eşleşmezse, bir değiştirme dizesi yerine sınıfları. Varsayılan olarak bu değiştirme dizesi bir soru işaretidir, ancak farklı dize seçmek için bir sınıf oluşturucusu aşırı yüklemesini çağırabilirsiniz. Genellikle, değiştirme karakteri tek bir karakterdir, ancak bu, bir gereksinim değildir. Aşağıdaki örnek, değişim dizesi olarak yıldız işareti (*) kullanan bir <xref:System.Text.EncoderReplacementFallback> nesnesinin örneğini oluşturarak kod sayfası 1252'nin davranışını değiştirir.  
  
 [!code-csharp[Conceptual.Encoding#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/bestfit1a.cs#3)]
 [!code-vb[Conceptual.Encoding#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/bestfit1a.vb#3)]  
  
> [!NOTE]
>  Bir kodlama için ayrıca bir değiştirme sınıfı da uygulayabilirsiniz. Daha fazla bilgi için [Custom Fallback Strategy uygulama](../../../docs/standard/base-types/character-encoding.md#Custom) bölümü.  
  
 SORU İŞARETİ (U+003F) karakterine ek olarak, özellikle Unicode karakterlerine başarıyla çevrilemeyen bayt dizilerinin kodunu çözerken Unicode DEĞİŞTİRME KARAKTERİ (U+FFFD) de bir değiştirme dizesi olarak kullanılır. Ancak, istediğiniz değiştirme dizesini seçebilirsiniz ve bu dize birden çok karakteri içerebilir.  
  
<a name="Exception"></a>   
### <a name="exception-fallback"></a>Özel Durum Geri Dönüşü  
 Bir en uygun geri dönüş veya değiştirme dizesi sağlamak yerine bir kodlayıcı, bir karakter kümesini kodlayamadığında <xref:System.Text.EncoderFallbackException>'i oluşturabilir; ve bir kod çözücü, bir bayt dizisinin kodunu çözemediğinde bir <xref:System.Text.DecoderFallbackException>'i oluşturabilir. Kodlama ve kod çözme işlemlerinde bir özel durum oluşturmak için, <xref:System.Text.EncoderExceptionFallback> yöntemine sırasıyla bir <xref:System.Text.DecoderExceptionFallback> ve bir <xref:System.Text.Encoding.GetEncoding%28System.String%2CSystem.Text.EncoderFallback%2CSystem.Text.DecoderFallback%29?displayProperty=nameWithType> nesnesi sağlayın. Aşağıdaki örnek, <xref:System.Text.ASCIIEncoding> sınıfıyla özel durum geri dönüşünü gösterir.  
  
 [!code-csharp[Conceptual.Encoding#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/exceptionascii.cs#4)]
 [!code-vb[Conceptual.Encoding#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/exceptionascii.vb#4)]  
  
> [!NOTE]
>  Ayrıca bir kodlama işlemi için özel bir özel durum işleyicisi uygulayabilirsiniz. Daha fazla bilgi için [Custom Fallback Strategy uygulama](../../../docs/standard/base-types/character-encoding.md#Custom) bölümü.  
  
 <xref:System.Text.EncoderFallbackException> ve <xref:System.Text.DecoderFallbackException> nesneleri, özel durumu oluşturan durum hakkında aşağıdaki bilgileri sağlar:  
  
-   <xref:System.Text.EncoderFallbackException> nesnesi, kodlanamayan karakterin veya karakterlerin bilinmeyen bir temsilci çifti mi (bu durumda yöntem <xref:System.Text.EncoderFallbackException.IsUnknownSurrogate%2A>'i döndürür) yoksa bilinmeyen tek bir karakter mi (bu durumda yöntem `true`'i döndürür) olduğunu belirten bir `false` yöntemini içerir. Yedek çiftindeki karakterler <xref:System.Text.EncoderFallbackException.CharUnknownHigh%2A?displayProperty=nameWithType> ve <xref:System.Text.EncoderFallbackException.CharUnknownLow%2A?displayProperty=nameWithType> özelliklerinde mevcuttur. Bilinmeyen tek karakter, <xref:System.Text.EncoderFallbackException.CharUnknown%2A?displayProperty=nameWithType> özelliğinde mevcuttur. <xref:System.Text.EncoderFallbackException.Index%2A?displayProperty=nameWithType> özelliği, kodlanamayan ilk karakterin dizede bulunduğu konumu gösterir.  
  
-   <xref:System.Text.DecoderFallbackException> nesnesi, kodu çözülemeyen bir bayt dizisini döndüren bir <xref:System.Text.DecoderFallbackException.BytesUnknown%2A> özelliğini içerir. <xref:System.Text.DecoderFallbackException.Index%2A?displayProperty=nameWithType> özelliği, bilinmeyen baytların başlangıç konumunu gösterir.  
  
 <xref:System.Text.EncoderFallbackException> ve <xref:System.Text.DecoderFallbackException> nesneleri özel durum hakkında yeterli tanılama bilgisi sağlasa da, kodlama veya kod çözme arabelleğine erişim sağlamaz. Bu nedenle bu nesneler, geçersiz verinin kodlama veya kod çözme yönteminde değiştirilmesine veya düzeltilmesine izin vermez.  
  
<a name="Custom"></a>   
## <a name="implementing-a-custom-fallback-strategy"></a>Implementing a Custom Fallback Strategy  
 Kod sayfaları tarafından dahili olarak uygulanan en uygun eşlemenin yanı sıra .NET bir geri dönüş stratejisi uygulamak için aşağıdaki sınıfları içerir:  
  
-   Kodlama işlemlerinde karakterleri değiştirmek için <xref:System.Text.EncoderReplacementFallback> ve <xref:System.Text.EncoderReplacementFallbackBuffer> kullanın.  
  
-   Kod çözme işlemlerinde karakterleri değiştirmek için <xref:System.Text.DecoderReplacementFallback> ve <xref:System.Text.DecoderReplacementFallbackBuffer> kullanın.  
  
-   Bir karakter kodlanamadığında bir <xref:System.Text.EncoderExceptionFallback> oluşturmak için <xref:System.Text.EncoderExceptionFallbackBuffer> ve <xref:System.Text.EncoderFallbackException> kullanın.  
  
-   Bir karakterin kodu çözülemediğinde bir <xref:System.Text.DecoderExceptionFallback> oluşturmak için <xref:System.Text.DecoderExceptionFallbackBuffer> ve <xref:System.Text.DecoderFallbackException> kullanın.  
  
 Ek olarak, aşağıdaki adımları izleyerek en iyi geri dönüş, değiştirme geri dönüşü veya özel durum geri dönüşü kullanan özel bir çözüm uygulayabilirsiniz:  
  
1.  Kodlama işlemleri için <xref:System.Text.EncoderFallback> sınıfından, kod çözme işlemleri için <xref:System.Text.DecoderFallback> sınıfından bir sınıf türetin.  
  
2.  Kodlama işlemleri için <xref:System.Text.EncoderFallbackBuffer> sınıfından, kod çözme işlemleri için <xref:System.Text.DecoderFallbackBuffer> sınıfından bir sınıf türetin.  
  
3.  Özel durum geri dönüşü için, eğer önceden tanımlı <xref:System.Text.EncoderFallbackException> ve <xref:System.Text.DecoderFallbackException> sınıfları gereksinimlerinizi karşılamıyorsa, <xref:System.Exception> veya <xref:System.ArgumentException> gibi bir özel durum nesnesinden bir sınıf türetin.  
  
### <a name="deriving-from-encoderfallback-or-decoderfallback"></a>EncoderFallback veya DecoderFallback Öğesinden Türetme  
 Özel bir geri dönüş çözümü uygulamak için, kodlama işlemleri için <xref:System.Text.EncoderFallback> sınıfından ve kod çözme işlemleri için <xref:System.Text.DecoderFallback> sınıfından devralan bir sınıf oluşturmanız gerekir. Bu sınıfların örnekleri <xref:System.Text.Encoding.GetEncoding%28System.String%2CSystem.Text.EncoderFallback%2CSystem.Text.DecoderFallback%29?displayProperty=nameWithType> yöntemine geçirilir ve kodlama sınıfıyla geri dönüş uygulaması arasında bir aracı görevi görür.  
  
 Bir kodlayıcı veya kod çözücü için özel bir geri dönüş çözümü oluşturduğunuzda, aşağıdaki üyeleri uygulamanız gerekir:  
  
-   En uygun, değiştirme veya özel durum geri dönüşünün tek bir karakterini değiştirmek için döndürebileceği en fazla karakter sayısını döndüren <xref:System.Text.EncoderFallback.MaxCharCount%2A?displayProperty=nameWithType> veya <xref:System.Text.DecoderFallback.MaxCharCount%2A?displayProperty=nameWithType> özelliği. Özel bir özel durum geri dönüşü için, değeri sıfırdır.  
  
-   Özel <xref:System.Text.EncoderFallback.CreateFallbackBuffer%2A?displayProperty=nameWithType> veya <xref:System.Text.DecoderFallback.CreateFallbackBuffer%2A?displayProperty=nameWithType> uygulamanızı döndüren <xref:System.Text.EncoderFallbackBuffer> veya <xref:System.Text.DecoderFallbackBuffer> yöntemi. Bu yöntem, kodlayıcı tarafından başarıyla kodlayamadığı ilk karakterle karşılaştığında veya kod çözücü tarafından başarıyla kodunu çözemediği ilk bayt ile karşılaştığında çağırılır.  
  
### <a name="deriving-from-encoderfallbackbuffer-or-decoderfallbackbuffer"></a>EncoderFallbackBuffer veya DecoderFallbackBuffer Öğesinden Türetme  
 Özel bir geri dönüş çözümü uygulamak için aynı zamanda, kodlama işlemleri için <xref:System.Text.EncoderFallbackBuffer> sınıfından ve kod çözme işlemleri için <xref:System.Text.DecoderFallbackBuffer> sınıfından devralan bir sınıf oluşturmanız gerekir. Bu sınıfların örnekleri <xref:System.Text.EncoderFallback.CreateFallbackBuffer%2A> ve <xref:System.Text.EncoderFallback> sınıflarının <xref:System.Text.DecoderFallback> yöntemi tarafından döndürülür. <xref:System.Text.EncoderFallback.CreateFallbackBuffer%2A?displayProperty=nameWithType> yöntemi, kodlayıcı tarafından kodlayamadığı ilk karakterle karşılaştığında çağırılır ve <xref:System.Text.DecoderFallback.CreateFallbackBuffer%2A?displayProperty=nameWithType> yöntemi, kod çözücü tarafından başarıyla kodunu çözemediği bir veya daha fazla bayt ile karşılaştığında çağırılır. <xref:System.Text.EncoderFallbackBuffer> ve <xref:System.Text.DecoderFallbackBuffer> sınıfları geri dönüş uygulamasını sağlar. Her bir örnek, kodlanamayan karakteri veya kodu çözülemeyen bayt dizisini değiştirecek geri dönüş karakterlerini içeren bir arabelleği temsil eder.  
  
 Bir kodlayıcı veya kod çözücü için özel bir geri dönüş çözümü oluşturduğunuzda, aşağıdaki üyeleri uygulamanız gerekir:  
  
-   <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> veya <xref:System.Text.DecoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> yöntemi. <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType>, kodlayamadığı karakter hakkında geri dönüş arabelleğine bilgi vermek için kodlayıcı tarafından çağrılır. Kodlanacak karakter bir yedek çifti olabileceği için bu yöntem aşırı yüklüdür. Aşırı yüklemelerden birine kodlanacak karakter ve dizedeki dizini geçirilir. İkinci aşırı yüklemeye, dizedeki dizini ile birlikte yüksek ve düşük yedek geçirilir. <xref:System.Text.DecoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> yöntemi, geri dönüş arabelleğine kodu çözülemeyen baytlar hakkında bilgi vermek için kod çözücü tarafından çağrılır. Bu yönteme, ilk baytın dizini ile birlikte kodunu çözemediği bir bayt dizisi geçirilir. Geri dönüş metodu, eğer geri dönüş arabelleği karakterler için bir en uygun veya değiştirme karakteri veya karakterleri sağlayabiliyorsa `true`'i, aksi halde `false`'i döndürmelidir. Bir özel durum geri dönüşü için, geri dönüş yönteminin bir özel durum oluşturması gerekir.  
  
-   Geri dönüş arabelleğinden sonraki karakteri almak için kodlayıcı veya kod çözücü tarafından tekrar tekrar çağrılan <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> veya <xref:System.Text.DecoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> yöntemi. Tüm geri dönüş karakterleri döndürüldükten sonra yöntem U+0000'ı döndürmelidir.  
  
-   Geri dönüş arabelleğinde kalan karakter sayısını döndüren <xref:System.Text.EncoderFallbackBuffer.Remaining%2A?displayProperty=nameWithType> veya <xref:System.Text.DecoderFallbackBuffer.Remaining%2A?displayProperty=nameWithType> özelliği.  
  
-   Geri dönüş arabelleğindeki gereçli konumu önceki karaktere taşıyan <xref:System.Text.EncoderFallbackBuffer.MovePrevious%2A?displayProperty=nameWithType> veya <xref:System.Text.DecoderFallbackBuffer.MovePrevious%2A?displayProperty=nameWithType> yöntemi.  
  
-   Geri dönüş arabelleğini yeniden başlatan <xref:System.Text.EncoderFallbackBuffer.Reset%2A?displayProperty=nameWithType> veya <xref:System.Text.DecoderFallbackBuffer.Reset%2A?displayProperty=nameWithType> yöntemi.  
  
 Eğer geri dönüş uygulaması bir en uygun geri dönüş veya değiştirme geri dönüşü ise, <xref:System.Text.EncoderFallbackBuffer> ve <xref:System.Text.DecoderFallbackBuffer> sınıflarından türetilen sınıflar ayrıca iki özel örnek alanı içerir: arabellekteki tam karakter sayısı ve bellekte dönülecek sıradaki karakterin dizini.  
  
### <a name="an-encoderfallback-example"></a>Bir EncoderFallback Örneği  
 Önceki bir örnek, ASCII karakterlerine karşılık gelmeyen Unicode karakterlerini bir yıldız işareti (*) ile değiştirmek için değiştirme geri dönüşü kullandı. Aşağıdaki örnek, ASCII olmayan karakterler için daha iyi bir eşleme sağlamak üzere bunun yerine özel bir en uygun geri dönüş uygulaması kullanır.  
  
 Aşağıdaki kod, ASCII olmayan karakterlerin en uygun geri dönüş eşlemesini işlemek için `CustomMapper` sınıfından türetilen <xref:System.Text.EncoderFallback> adında bir sınıf tanımlar. `CreateFallbackBuffer` yöntemi, `CustomMapperFallbackBuffer` uygulamasını sağlayan bir <xref:System.Text.EncoderFallbackBuffer> nesnesini döndürür. `CustomMapper` sınıfı, desteklenmeyen Unicode karakterlerini (anahtar değeri) ve karşılık gelen 8 bitlik karakterleri (64 bitlik bir tamsayıda ardışık iki baytta depolanan karakterler) depolamak için bir <xref:System.Collections.Generic.Dictionary%602> nesnesi kullanır. Bu eşleşmeyi geri dönüş arabelleği için kullanılabilir yapmak amacıyla `CustomMapper` örneği, `CustomMapperFallbackBuffer` sınıf oluşturucusuna bir parametre olarak geçirilir. U+221E Unicode karakteri için en uzun eşleme "INF" dizesi olduğundan, `MaxCharCount` özelliği 3'ü döndürür.  
  
 [!code-csharp[Conceptual.Encoding#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/custom1.cs#5)]
 [!code-vb[Conceptual.Encoding#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/custom1.vb#5)]  
  
 Aşağıdaki kod, `CustomMapperFallbackBuffer` sınıfından türetilen <xref:System.Text.EncoderFallbackBuffer> sınıfını tanımlar. En uygun eşlemeleri içeren ve `CustomMapper` içinde tanımlanan sözlük, kendi sınıf oluşturucusunda mevcuttur. `Fallback` yöntemi, eğer ASCII kodlayıcısının kodlayamadığı Unicode karakterlerinden herhangi biri eşleme sözlüğünde tanımlıysa `true`'i, aksi halde `false`'i döndürür. Her geri dönüş için, özel `count` değişkeni döndürülecek kalan karakter sayısını belirtir, özel `index` değişkeni ise döndürülecek bir sonraki karakterin `charsToReturn` dize arabelleğindeki konumu gösterir.  
  
 [!code-csharp[Conceptual.Encoding#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/custom1.cs#6)]
 [!code-vb[Conceptual.Encoding#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/custom1.vb#6)]  
  
 Aşağıdaki kod, daha sonra `CustomMapper` nesnesinin örneğini oluşturur ve <xref:System.Text.Encoding.GetEncoding%28System.String%2CSystem.Text.EncoderFallback%2CSystem.Text.DecoderFallback%29?displayProperty=nameWithType> yöntemine bunun bir örneğini geçirir. Çıktı, en uygun geri dönüş uygulamasının özgün dizedeki ASCII olmayan üç karakteri başarıyla işlediğini gösterir.  
  
 [!code-csharp[Conceptual.Encoding#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.encoding/cs/custom1.cs#7)]
 [!code-vb[Conceptual.Encoding#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.encoding/vb/custom1.vb#7)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Text.Encoder>  
- <xref:System.Text.Decoder>  
- <xref:System.Text.DecoderFallback>  
- <xref:System.Text.Encoding>  
- <xref:System.Text.EncoderFallback>  
- [Genelleştirme ve Yerelleştirme](../../../docs/standard/globalization-localization/index.md)
