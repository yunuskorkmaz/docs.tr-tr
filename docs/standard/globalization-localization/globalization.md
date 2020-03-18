---
title: Genelleştirme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- globalization [.NET Framework], about globalization
- global applications, globalization
- international applications [.NET Framework], globalization
- world-ready applications, globalization
- application development [.NET Framework], globalization
- culture, globalization
ms.assetid: 4e919934-6b19-42f2-b770-275a4fae87c9
ms.openlocfilehash: fe03bbdd7d037a9f1fb4985b62b447c6ef9c6535
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79174790"
---
# <a name="globalization"></a>Genelleştirme

Küreselleşme, birden çok kültürdeki kullanıcılar için yerelleştirilmiş arabirimleri ve bölgesel verileri destekleyen, dünyaya hazır bir uygulama tasarlamayı ve geliştirmeyi içerir. Tasarım aşamasına başlamadan önce, uygulamanızın hangi kültürleri destekleyeceğini belirlemeniz gerekir. Bir uygulama varsayılan olarak tek bir kültürü veya bölgeyi hedefalse de, diğer kültürlerdeki veya bölgelerdeki kullanıcılara kolayca genişletilebilmek için tasarlayabilir ve yazabilirsiniz.

Geliştiriciler olarak, hepimizin kullanıcı arabirimleri ve kültürlerimizin oluşturduğu veriler hakkında varsayımları vardır. Örneğin, ABD'de İngilizce konuşan bir geliştirici için, tarih ve saat verilerini `MM/dd/yyyy hh:mm:ss` biçimde bir dize olarak serihale getirmek son derece makul görünüyor. Ancak, bu dizeyi farklı bir kültürdeki bir sistem <xref:System.FormatException> üzerinde deserializing bir özel durum atmak veya yanlış veri üretmek olasıdır. Küreselleşme, bu tür kültüre özgü varsayımları belirlememize ve uygulamamızın tasarımını veya kodunu etkilememesini sağlamamızı sağlar.

Bu makalede, göz önünde bulundurmanız gereken bazı önemli sorunlar ve küreselleştirilmiş bir uygulamada dizeleri, tarih ve saat değerlerini ve sayısal değerleri işlerken izleyebileceğiniz en iyi uygulamalar anlatılmaktadır.

## <a name="strings"></a>Dizeler

Her kültür veya bölge farklı karakter ve karakter kümeleri kullanabilir ve bunları farklı sıralayabilir, çünkü karakter ve dizeleri işleme, küreselleşme merkezi bir odak noktasıdır. Bu bölümde, genelleştirilmiş uygulamalarda dizeleri kullanmak için öneriler verilmektedir.

### <a name="use-unicode-internally"></a>Unicode'u dahili olarak kullanma

Varsayılan olarak, .NET Unicode dizeleri kullanır. Unicode dizesi, her biri <xref:System.Char> utf-16 kod birimini temsil eden sıfır, bir veya daha fazla nesneden oluşur. Dünya çapında kullanılmakta olan her karakterde hemen hemen her karakter için bir Unicode gösterimi vardır.

Windows işletim sistemi de dahil olmak üzere birçok uygulama ve işletim sistemi, karakter kümelerini temsil etmek için kod sayfalarını da kullanabilir. Kod sayfaları genellikle 0x00 ile 0x7F arasında standart ASCII değerlerini içerir ve diğer karakterleri 0x80 ile 0xFF arasında kalan değerlere eşler. 0x80 ile 0xFF arasında değerlerin yorumlanması belirli kod sayfasına bağlıdır. Bu nedenle, mümkünse küreselleştirilmiş bir uygulamada kod sayfaları kullanmaktan kaçınmalısınız.

Aşağıdaki örnek, bir sistemdeki varsayılan kod sayfası verilerin kaydedildiği kod sayfasından farklı olduğunda kod sayfası verilerini yorumlamanın tehlikelerini göstermektedir. (Bu senaryoyu simüle etmek için, örnek açıkça farklı kod sayfaları belirtir.) İlk olarak, örnek, Yunan alfabesinin büyük harf karakterlerinden oluşan bir dizi tanımlar. Kod sayfası 737 (MS-DOS Yunanca olarak da bilinir) kullanarak bir bayt diziiçine kodlar ve bir dosyaya bayt dizi kaydeder. Dosya alınır ve bayt dizisi kod sayfası 737 kullanılarak çözülürse, özgün karakterler geri yüklenir. Ancak, dosya alınır ve bayt dizisi kod sayfası 1252 (veya Latin alfabesindeki karakterleri temsil eden Windows-1252) kullanılarak deşifre edilirse, orijinal karakterler kaybolur.

[!code-csharp[Conceptual.Globalization#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/codepages1.cs#1)]
[!code-vb[Conceptual.Globalization#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/codepages1.vb#1)]

Unicode kullanımı, aynı kod birimlerinin her zaman aynı karakterlerle eşlemesini ve aynı karakterlerin her zaman aynı bayt dizilerine eşlemesini sağlar.

### <a name="use-resource-files"></a>Kaynak dosyalarını kullanma

Tek bir kültürü veya bölgeyi hedefleyen bir uygulama geliştiriyor sanız bile, kullanıcı arabiriminde görüntülenen dizeleri ve diğer kaynakları depolamak için kaynak dosyalarını kullanmanız gerekir. Bunları asla doğrudan kodunuza eklememelisiniz. Kaynak dosyalarının kullanılmasının bir takım avantajları vardır:

- Tüm dizeleri tek bir yerde. Belirli bir dil veya kültür için değiştirmek için dizeleri tanımlamak için kaynak kodunuz boyunca arama yapmak zorunda değilsiniz.

- Dizeleri çoğaltmak için gerek yoktur. Kaynak dosyalarını kullanmayan geliştiriciler genellikle birden çok kaynak kodu dosyasında aynı dizeyi tanımlar. Bu yineleme, bir dize değiştirildiğinde bir veya daha fazla örneğin gözden kaçırılma olasılığını artırır.

- Görüntü veya ikili veri gibi dize dışı kaynakları ayrı bir bağımsız dosyada depolamak yerine kaynak dosyasına ekleyebilirsiniz, böylece kolayca alınabilirler.

Yerelleştirilmiş bir uygulama oluşturuyorsanız, kaynak dosyalarını kullanmanın belirli avantajları vardır. Kaynakları uydu derlemelerine dağıttığınızda, ortak dil çalışma zamanı, kullanıcının <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> özellik tarafından tanımlandığı şekilde geçerli Kullanıcı Arabirimi kültürüne dayalı kültüre uygun bir kaynağı otomatik olarak seçer. Uygun kültüre özgü bir kaynak sağladığınız ve bir <xref:System.Resources.ResourceManager> nesneyi doğru bir şekilde anında anettiğiniz veya güçlü bir şekilde yazılan bir kaynak sınıfı kullandığınız sürece, çalışma zamanı uygun kaynakları alma ayrıntılarını işler.

Kaynak dosyaları oluşturma hakkında daha fazla bilgi için kaynak [dosyaları oluşturma](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md)bilgisine bakın. Uydu derlemeleri oluşturma ve dağıtma hakkında bilgi [için](../../../docs/framework/resources/creating-satellite-assemblies-for-desktop-apps.md) [bkz.](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)

### <a name="search-and-compare-strings"></a>Dizeleri arama ve karşılaştırma

Mümkün olduğunda, dizeleri tek tek karakter dizisi olarak işlemek yerine tüm dizeleri olarak işlemelisiniz. Bu, özellikle birleştirilmiş karakterleri ayrıştırma ile ilişkili sorunları önlemek için substrings'i sıralarken veya ararken önemlidir.

> [!TIP]
> Bir dizedeki <xref:System.Globalization.StringInfo> tek tek karakterler yerine metin öğeleriyle çalışmak için sınıfı kullanabilirsiniz.

Dize aramalarında ve karşılaştırmalarda, sık karşılaşılan bir hata, dizeyi her biri bir <xref:System.Char> nesne tarafından temsil edilen bir karakter koleksiyonu olarak ele almaktır. Aslında, tek bir karakter bir, iki veya <xref:System.Char> daha fazla nesne tarafından oluşturulabilir. Bu tür karakterler en sık, alfabeleri Unicode Temel Latin karakter aralığının dışındaki karakterlerden oluşan kültürlerden gelen dizelerde bulunur (U+0021'den U+007E'ye kadar). Aşağıdaki örnek, LATIN BÜYÜK HARF A GRAVE karakteri (U+00C0) dizisini bulmaya çalışır. Ancak, bu karakter iki farklı şekilde temsil edilebilir: tek bir kod birimi (U+00C0) veya bileşik karakter olarak (iki kod birimi: U+0041 ve U+0300). Bu durumda, karakter dize örneğinde U+0041 ve U+0300 olmak üzere iki <xref:System.Char> nesne yle temsil edilir. Örnek kod, <xref:System.String.IndexOf%28System.Char%29?displayProperty=nameWithType> dize örneğindeki bu karakterin konumunu bulmak için çağırır ve <xref:System.String.IndexOf%28System.String%29?displayProperty=nameWithType> aşırı yükler, ancak bunlar farklı sonuçlar verir. İlk yöntem çağrısının <xref:System.Char> bir bağımsız değişkeni vardır; bir ordinal karşılaştırma yapar ve bu nedenle bir eşleşme bulamıyor. İkinci aramanın <xref:System.String> bir bağımsız değişkeni vardır; kültüre duyarlı bir karşılaştırma yapar ve bu nedenle bir eşleşme bulur.

[!code-csharp[Conceptual.Globalization#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/search1.cs#18)]
[!code-vb[Conceptual.Globalization#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/search1.vb#18)]

Bu örneğin bazı belirsizlikleri (farklı sonuçlar döndüren bir yöntemin benzer iki aşırı yüklemesine çağrı) <xref:System.StringComparison> parametre veya <xref:System.String.LastIndexOf%28System.String%2CSystem.StringComparison%29?displayProperty=nameWithType> yöntem <xref:System.String.IndexOf%28System.String%2CSystem.StringComparison%29?displayProperty=nameWithType> gibi bir parametre içeren bir aşırı yükleme çağırarak önleyebilirsiniz.

Ancak, aramalar her zaman kültüre duyarlı değildir. Aramanın amacı bir güvenlik kararı vermek veya bir kaynağa erişime izin vermek veya bu kaynağa izin vermemekse, karşılaştırma bir sonraki bölümde belirtildiği gibi ordinal olmalıdır.

### <a name="test-strings-for-equality"></a>Eşitlik için test dizeleri

Sıralama sırasına göre nasıl karşılaştıracaklarını belirlemek yerine iki dizeyi eşitlik <xref:System.String.Equals%2A?displayProperty=nameWithType> için sınamak istiyorsanız, dize karşılaştırma yöntemi yerine yöntemi kullanın <xref:System.String.Compare%2A?displayProperty=nameWithType> veya <xref:System.Globalization.CompareInfo.Compare%2A?displayProperty=nameWithType>.

Eşitlik için karşılaştırmalar genellikle koşullu bazı kaynaklara erişmek için gerçekleştirilir. Örneğin, parolayı doğrulamak veya bir dosyanın var olduğunu onaylamak için eşitlik için bir karşılaştırma gerçekleştirebilirsiniz. Bu tür dilsel olmayan karşılaştırmalar kültüre duyarlı olmaktan çok her zaman ordinal olmalıdır. <xref:System.String.Equals%28System.String%2CSystem.StringComparison%29?displayProperty=nameWithType> Genel olarak, örnek yöntemi ni veya <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> statik yöntemi <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> parolalar gibi dizeleri ve dosya <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> adları veya URI'ler gibi dizeleri için bir değer ile aramalısınız.

Eşitlik için karşılaştırmalar bazen <xref:System.String.Equals%2A?displayProperty=nameWithType> yönteme yapılan çağrılar yerine aramaları veya alt salgılar karşılaştırmalarını içerir. Bazı durumlarda, bu alt dize başka bir dize eşit olup olmadığını belirlemek için bir alt dize arama kullanabilirsiniz. Bu karşılaştırmanın amacı dilbilimsel değilse, arama kültüre duyarlı değil, aynı zamanda ordinal olmalıdır.

Aşağıdaki örnek, dilsel olmayan veriler üzerinde kültüre duyarlı bir aramanın tehlikesini göstermektedir. Yöntem, `AccessesFileSystem` "FILE" alt dizesiyle başlayan IU'lar için dosya sistemi erişimini yasaklamak üzere tasarlanmıştır. Bunu yapmak için, "FILE" dizesi ile URI başlangıcı bir kültür duyarlı, büyük/küçük harf duyarsız karşılaştırma gerçekleştirir. Dosya sistemine erişen bir URI "FILE:" veya "file:" ile başlayabileceğiniz için, örtük varsayım "i" (U+0069) her zaman "I" (U+0049) küçük harf eşdeğeri dir. Ancak Türkçe ve Azeriçe "i"nin büyük versiyonu "İ" (U+0130) 'dir. Bu tutarsızlık nedeniyle, kültüre duyarlı karşılaştırma, yasaklanması gerektiğinde dosya sistemi erişimine izin verir.

[!code-csharp[Conceptual.Globalization#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/equals1.cs#12)]
[!code-vb[Conceptual.Globalization#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/equals1.vb#12)]

Aşağıdaki örnekte görüldüğü gibi, büyük/küçük harf yoksayan bir ordinal karşılaştırma gerçekleştirerek bu sorunu önleyebilirsiniz.

[!code-csharp[Conceptual.Globalization#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/equals2.cs#13)]
[!code-vb[Conceptual.Globalization#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/equals2.vb#13)]

### <a name="order-and-sort-strings"></a>Dizeleri sırala ve sıralama

Genellikle, kullanıcı arabiriminde görüntülenecek sıralı dizeleri kültüre göre sıralanmalıdır. Çoğunlukla, bu tür dize karşılaştırmaları gibi dizeleri sıralayan bir yöntem çağırdığınızda <xref:System.Array.Sort%2A?displayProperty=nameWithType> <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType>.NET tarafından örtülü olarak işlenir. Varsayılan olarak, dizeleri geçerli kültürün sıralama kuralları kullanılarak sıralanır. Aşağıdaki örnek, bir dizi dize, İngilizce (ABD) kültürü ve İsveç (İsveç) kültürünün kuralları kullanılarak sıralandığında aradaki farkı göstermektedir.

[!code-csharp[Conceptual.Globalization#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/sort1.cs#14)]
[!code-vb[Conceptual.Globalization#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/sort1.vb#14)]

Kültüre duyarlı dize karşılaştırması, her kültürün <xref:System.Globalization.CompareInfo> <xref:System.Globalization.CultureInfo.CompareInfo%2A?displayProperty=nameWithType> özelliği tarafından döndürülen nesne tarafından tanımlanır. <xref:System.String.Compare%2A?displayProperty=nameWithType> Yöntemi aşırı kullanan kültüre duyarlı dize karşılaştırmaları da nesneyi <xref:System.Globalization.CompareInfo> kullanır.

.NET, dize verilerinde kültüre duyarlı sıralamalar gerçekleştirmek için tabloları kullanır. Sıralama ağırlıkları ve dize normalleştirme si verileri içeren bu tabloların içeriği, .NET'in belirli bir sürümü tarafından uygulanan Unicode standardının sürümü tarafından belirlenir. Aşağıdaki tabloda,.NET Framework'ün belirtilen sürümleri ve .NET Core tarafından uygulanan Unicode sürümleri listelenir. Desteklenen Unicode sürümlerinin bu listesinin yalnızca karakter karşılaştırması ve sıralama için geçerli olduğunu unutmayın; Unicode karakterlerinin kategoriye göre sınıflandırılması için geçerli değildir. Daha fazla bilgi için makaledeki "Dizeleri ve Unicode Standardı" bölümüne <xref:System.String> bakın.

|.NET Framework sürümü|İşletim sistemi|Unicode sürümü|
|----------------------------|----------------------|---------------------|
|.NET Framework 2.0|Tüm işletim sistemleri|Unicode 4.1|
|.NET Framework 3.0|Tüm işletim sistemleri|Unicode 4.1|
|.NET Framework 3.5|Tüm işletim sistemleri|Unicode 4.1|
|.NET Framework 4|Tüm işletim sistemleri|Unicode 5.0|
|.NET Framework 4.5 ve daha sonra Windows 7'de|Unicode 5.0|
|.NET Framework 4.5 ve daha sonra Windows 8 ve daha sonra işletim sistemlerinde|Unicode 6.3.0|
|.NET Core (tüm sürümler)|Altta yatan işletim sistemi tarafından desteklenen Unicode Standard sürümüne bağlıdır.|

.NET Framework 4.5 ile başlayıp .NET Core'un tüm sürümlerinde, dize karşılaştırması ve sıralama işletim sistemine bağlıdır. .NET Framework 4.5 ve daha sonra Windows 7'de çalışan unicode 5.0 uygulayan kendi tablolarından veri alır. .NET Framework 4.5 ve daha sonra Windows 8'de çalışır ve daha sonra Unicode 6.3 uygulayan işletim sistemi tablolarından veri alır. .NET Core'da, Unicode'un desteklenen sürümü temel işletim sistemine bağlıdır. Kültüre duyarlı sıralanmış verileri seri hale getirerek, serileştirilmiş verilerinizin ne zaman sıralanması gerektiğini belirlemek için <xref:System.Globalization.SortVersion> sınıfı kullanabilirsiniz, böylece .NET ve işletim sisteminin sıralama sırası ile tutarlı dır. Örneğin, sınıf konusuna <xref:System.Globalization.SortVersion> bakın.

Uygulamanız kültüre özgü geniş dize verisi türlerinde performans sergiliyorsa, dizeleri karşılaştırmak için <xref:System.Globalization.SortKey> sınıfla birlikte çalışabilirsiniz. Sıralama anahtarı, belirli bir dizenin alfabetik, büyük/küçük harf ve aksan ağırlıkları da dahil olmak üzere kültüre özgü sıralama ağırlıklarını yansıtır. Sıralama anahtarlarını kullanan karşılaştırmalar ikili olduğundan, nesneyi <xref:System.Globalization.CompareInfo> örtülü veya açık olarak kullanan karşılaştırmalardan daha hızlıdır. Dizeyi <xref:System.Globalization.CompareInfo.GetSortKey%2A?displayProperty=nameWithType> yönteme geçirerek belirli bir dize için kültüre özgü bir sıralama anahtarı oluşturursunuz.

Aşağıdaki örnek önceki örneğe benzer. Ancak, yöntemi dolaylı <xref:System.Array.Sort%28System.Array%29?displayProperty=nameWithType> olarak çağıran <xref:System.Globalization.CompareInfo.Compare%2A?displayProperty=nameWithType> yöntemi çağırmak yerine, anında <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> aldığı ve <xref:System.Array.Sort%60%601%28%60%600%5B%5D%2CSystem.Collections.Generic.IComparer%7B%60%600%7D%29?displayProperty=nameWithType> yönteme geçtiği sıralama anahtarlarını karşılaştıran bir uygulama tanımlar.

[!code-csharp[Conceptual.Globalization#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/sortkey1.cs#15)]
[!code-vb[Conceptual.Globalization#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/sortkey1.vb#15)]

### <a name="avoid-string-concatenation"></a>Dize concatenation kaçının

Mümkünse, zaman içinde konkalı tümceciklerden oluşturulmuş bileşik dizeleri kullanmaktan kaçının. Bileşik dizeleri yerelleştirmek zordur, çünkü genellikle uygulamanın özgün dilinde diğer yerelleştirilmiş diller için geçerli olmayan bir dilbilgisi sırası varsayarlar.

## <a name="handle-dates-and-times"></a>Tarihleri ve saatleri işleme

Tarih ve saat değerlerini nasıl işleyeceğiniz, kullanıcı arabiriminde görüntülenip görüntülenmediğine veya kalıcı olup olmadıklarına bağlıdır. Bu bölümde her iki kullanım da inceleneb.r.a.. Ayrıca, tarih ve saatlerle çalışırken saat dilimi farklılıklarını ve aritmetik işlemleri nasıl işleyeceğiniz de tartışılır.

### <a name="display-dates-and-times"></a>Tarihleri ve saatleri görüntüleme

Genellikle, tarih ve saatler kullanıcı arabiriminde görüntülendiğinde, kullanıcı kültürünün <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> özellik ve <xref:System.Globalization.DateTimeFormatInfo> `CultureInfo.CurrentCulture.DateTimeFormat` özellik tarafından döndürülen nesne tarafından tanımlanan biçimlendirme kurallarını kullanmanız gerekir. Geçerli kültürün biçimlendirme kuralları, bir tarihi şu yöntemlerden birini kullanarak biçimlendirdiğinizde otomatik olarak kullanılır:

- Parametresiz <xref:System.DateTime.ToString?displayProperty=nameWithType> yöntem

- Biçim <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> dizesini içeren yöntem

- Parametresiz <xref:System.DateTimeOffset.ToString?displayProperty=nameWithType> yöntem

- Bir <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType>biçim dizesi içeren ,

- Bileşik [biçimlendirme](../../../docs/standard/base-types/composite-formatting.md) özelliği, tarihlerle birlikte kullanıldığında

Aşağıdaki örnek, 11 Ekim 2012 için iki kez gün doğumu ve gün batımı verilerini görüntüler. Önce hırvat (Hırvatistan) ve daha sonra İngilizce (Büyük Britanya) mevcut kültürü ayarlar. Her durumda, tarihler ve saatler bu kültür için uygun biçimde görüntülenir.

[!code-csharp[Conceptual.Globalization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates1.cs#2)]
[!code-vb[Conceptual.Globalization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates1.vb#2)]

### <a name="persist-dates-and-times"></a>Tarihleri ve saatleri devam etti

Tarih ve saat verilerini kültüre göre değişiklik gösterebilecek bir biçimde asla devam etmemelisiniz. Bu, bozuk verilerle veya çalışma zamanı özel durumla sonuçlanan yaygın bir programlama hatasıdır. Aşağıdaki örnek, 9 Ocak 2013 ve 18 Ağustos 2013 olmak üzere iki tarihi, İngilizce (ABD) kültürünün biçimlendirme kurallarını kullanarak dizeleri olarak sıralar olarak sıralar. Veriler İngilizce (ABD) kültürünün kuralları kullanılarak alınıp ayrıştırıldığında, başarıyla geri yüklenir. Ancak, İngilizce (Birleşik Krallık) kültürünün kuralları kullanılarak alınıp ayrıştırıldığında, ilk tarih yanlış bir şekilde 1 Eylül olarak yorumlanır ve Gregoryen takvimionsekizinci ayı olmadığı için ikinci tarih ayrıştırılamaz.

[!code-csharp[Conceptual.Globalization#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates2.cs#3)]
[!code-vb[Conceptual.Globalization#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates2.vb#3)]

Bu sorunu üç şekilde önleyebilirsiniz:

- Tarih ve saati dize olarak değil, ikili biçimde serileştirin.

- Kullanıcının kültüründen bağımsız olarak aynı olan özel bir biçim dizesi kullanarak tarih ve saatin dize temsilini kaydedin ve ayrıştırın.

- Değişmez kültürün biçimlendirme kurallarını kullanarak dizeyi kaydedin.

Aşağıdaki örnek, son yaklaşımı göstermektedir. Statik <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> özellik tarafından döndürülen değişmez kültürün biçimlendirme kurallarını kullanır.

[!code-csharp[Conceptual.Globalization#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates3.cs#4)]
[!code-vb[Conceptual.Globalization#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates3.vb#4)]

### <a name="serialization-and-time-zone-awareness"></a>Serileştirme ve saat dilimi farkındalığı

Bir tarih ve saat değerinin, genel bir zamandan ("Mağazalar 2 Ocak 2013 saat 09:00'da açılır.") ile belirli bir zaman dilimi ("Doğum tarihi: 2 Ocak 2013:00:00") arasında değişen birden çok yorumu olabilir. Bir zaman değeri zaman içinde belirli bir anı temsil ettiğinde ve onu serileştirilmiş bir değerden geri yüklediğinizde, kullanıcının coğrafi konumu veya saat diliminden bağımsız olarak aynı anı temsil ettiğinden emin olmalısınız.

Aşağıdaki örnekte bu sorun gösterin. Tek bir yerel tarih ve saat değerini üç [standart biçimde](../../../docs/standard/base-types/standard-date-and-time-format-strings.md) (genel tarih için uzun süre "G", sıralanabilir tarih/saat için "s", gidiş-dönüş tarihi/saat için "o" olarak) ve ikili biçimde bir dize olarak kaydeder.

[!code-csharp[Conceptual.Globalization#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates4.cs#10)]
[!code-vb[Conceptual.Globalization#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates4.vb#10)]

Veriler seri hale geldiği sistemle aynı zaman diliminde ki bir sistemde geri yüklendiğinde, çıktının gösterdiği gibi, seri olarak çözülen tarih ve saat değerleri orijinal değeri doğru bir şekilde yansıtır:

```console
'3/30/2013 6:00:00 PM' --> 3/30/2013 6:00:00 PM Unspecified
'2013-03-30T18:00:00' --> 3/30/2013 6:00:00 PM Unspecified
'2013-03-30T18:00:00.0000000-07:00' --> 3/30/2013 6:00:00 PM Local

3/30/2013 6:00:00 PM Local
```

Ancak, farklı bir saat dilimindeki bir sistemdeki verileri geri yüklerseniz, yalnızca "o" (gidiş-dönüş) standart biçim dizesi ile biçimlendirilmiş tarih ve saat değeri saat dilimi bilgilerini korur ve bu nedenle aynı zamanı zaman içinde temsil eder. Romance Standart Saat dilimindeki bir sistemde tarih ve saat verilerinin geri yüklendiğinde çıktı aşağıda ve

```console
'3/30/2013 6:00:00 PM' --> 3/30/2013 6:00:00 PM Unspecified
'2013-03-30T18:00:00' --> 3/30/2013 6:00:00 PM Unspecified
'2013-03-30T18:00:00.0000000-07:00' --> 3/31/2013 3:00:00 AM Local

3/30/2013 6:00:00 PM Local
```

Verilerin seri selleştirildiği sistemin saat diliminden bağımsız olarak, tek bir zamanı temsil eden bir tarih ve saat değerini doğru bir şekilde yansıtmak için aşağıdakilerden birini yapabilirsiniz:

- "o" (gidiş-dönüş) standart biçim dizesini kullanarak değeri dize olarak kaydedin. O zaman hedef sistemde deserialize edin.

- UTC'ye dönüştürün ve "r" (RFC1123) standart biçim dizesini kullanarak bir dize olarak kaydedin. Daha sonra hedef sistemde deserialize ve yerel saate dönüştürmek.

- UTC'ye dönüştürün ve "u" (evrensel sıralanabilir) standart biçim dizesini kullanarak bir dize olarak kaydedin. Daha sonra hedef sistemde deserialize ve yerel saate dönüştürmek.

- UTC'ye dönüştürün ve ikili formatta kaydedin. Daha sonra hedef sistemde deserialize ve yerel saate dönüştürmek.

Aşağıdaki örnekte her tekniği gösterilmektedir.

[!code-csharp[Conceptual.Globalization#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates8.cs#11)]
[!code-vb[Conceptual.Globalization#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates8.vb#11)]

Veriler Pasifik Standart Saat dilimindeki bir sistemde serihale edildiğinde ve Romance Standart Saat dilimindeki bir sistemde seri dışılaştırıldığında, örnek aşağıdaki çıktıyı görüntüler:

```console
'2013-03-30T18:00:00.0000000-07:00' --> 3/31/2013 3:00:00 AM Local
'Sun, 31 Mar 2013 01:00:00 GMT' --> 3/31/2013 3:00:00 AM Local
'2013-03-31 01:00:00Z' --> 3/31/2013 3:00:00 AM Local

3/31/2013 3:00:00 AM Local
```

Daha fazla bilgi için [bkz.](../../../docs/standard/datetime/converting-between-time-zones.md)

### <a name="perform-date-and-time-arithmetic"></a>Tarih ve saat aritmetik yapma

Hem <xref:System.DateTime> türleri <xref:System.DateTimeOffset> hem de aritmetik işlemleri destekler. İki tarih değeri arasındaki farkı hesaplayabilir veya belirli zaman aralıklarını bir tarih değerine veya bir tarih değerinden ekleyebilir veya çıkarabilirsiniz. Ancak, tarih ve saat değerlerindeki aritmetik işlemler saat dilimlerini ve saat dilimi ayarlama kurallarını dikkate almaz. Bu nedenle, zaman daki anları temsil eden değerler üzerindeki tarih ve saat aritmetiği yanlış sonuçlar döndürebilir.

Örneğin, Pasifik Standart Saati'nden Pasifik Gün Işığı Saati'ne geçiş, 2013 yılı için 10 Mart olan Mart'ın ikinci Pazar günü gerçekleşir. Aşağıdaki örnekte görüldüğü gibi, 9 Mart 2013 tarihinden sonra 48 saat olan tarihi ve saati saat 10:30'da hesaplarsanız. Pasifik Standart Saat dilimindeki bir sistemde, sonuç, 11 Mart 2013 saat 10:30'da, aradaki zaman ayarlamasını dikkate almaz.

[!code-csharp[Conceptual.Globalization#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates5.cs#8)]
[!code-vb[Conceptual.Globalization#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates5.vb#8)]

Tarih ve saat değerlerinde aritmetik bir işlemin doğru sonuçlar ürettiğinden emin olmak için aşağıdaki adımları izleyin:

1. Kaynak saat dilimindeki saati UTC'ye dönüştürün.

2. Aritmetik işlemi gerçekleştirin.

3. Sonuç bir tarih ve saat değeriyse, kaynak saat dilimindeki saate UTC'den dönüştürün.

Aşağıdaki örnek, 9 Mart 2013 saat 10:30'a 48 saat doğru eklemek için bu üç adımı izlemesi dışında önceki örneğe benzer.

[!code-csharp[Conceptual.Globalization#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates6.cs#9)]
[!code-vb[Conceptual.Globalization#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates6.vb#9)]

Daha fazla bilgi için bkz: [Tarih ve Saatlerle Aritmetik İşlemleri Gerçekleştirme.](../../../docs/standard/datetime/performing-arithmetic-operations.md)

### <a name="use-culture-sensitive-names-for-date-elements"></a>Tarih öğeleri için kültüre duyarlı adlar kullanma

Uygulamanızın ayın veya haftanın gününün adını görüntülemesi gerekebilir. Bunu yapmak için, aşağıdaki gibi kod yaygındır.

[!code-csharp[Conceptual.Globalization#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/monthname1.cs#19)]
[!code-vb[Conceptual.Globalization#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/monthname1.vb#19)]

Ancak, bu kod her zaman İngilizce olarak haftanın gün lerinin adlarını döndürür. Ayın adını ayıklayan kod genellikle daha da esnek değildir. Sık sık belirli bir dilde ay adları ile on iki aylık bir takvim varsayar.

Özel [tarih ve saat biçimi dizeleri](../../../docs/standard/base-types/custom-date-and-time-format-strings.md) veya <xref:System.Globalization.DateTimeFormatInfo> nesnenin özelliklerini kullanarak, aşağıdaki örnekte gösterildiği gibi, kullanıcı kültüründe haftanın veya ay gün adlarını yansıtan dizeleri ayıklamak kolaydır. Mevcut kültürü Fransızca (Fransa) olarak değiştirir ve haftanın gününün adını ve 1 Temmuz 2013 için ayın adını görüntüler.

[!code-csharp[Conceptual.Globalization#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/monthname2.cs#20)]
[!code-vb[Conceptual.Globalization#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/monthname2.vb#20)]

## <a name="numeric-values"></a>Sayısal değerler

Sayıların işlenmesi, bunların kullanıcı arabiriminde görüntülenip görüntülenmediğine veya kalıcı olup olmadıklarına bağlıdır. Bu bölümde her iki kullanım da inceleneb.r.a..

> [!NOTE]
> Ayrıştırma ve biçimlendirme işlemlerinde ,NET yalnızca 0'dan 9'a kadar olan Temel Latince karakterleri (U+0030 ile U+0039) sayısal basamak olarak tanır.

### <a name="display-numeric-values"></a>Sayısal değerleri görüntüleme

Genellikle, sayılar kullanıcı arabiriminde görüntülendiğinde, kullanıcı kültürünün <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> özellik ve <xref:System.Globalization.NumberFormatInfo> `CultureInfo.CurrentCulture.NumberFormat` özellik tarafından döndürülen nesne tarafından tanımlanan biçimlendirme kurallarını kullanmanız gerekir. Geçerli kültürün biçimlendirme kuralları, bir tarihi aşağıdaki yöntemlerden herhangi birini kullanarak biçimlendirdiğinizde otomatik olarak kullanılır:

- Herhangi bir `ToString` sayısal tip parametresiz yöntem

- Bir `ToString(String)` argüman olarak bir biçim dizesi içeren herhangi bir sayısal tür, yöntemi

- Sayısal değerlerle kullanıldığında [bileşik biçimlendirme](../../../docs/standard/base-types/composite-formatting.md) özelliği

Aşağıdaki örnek, Fransa'nın Başkenti Paris'te ayda ortalama sıcaklığı görüntüler. Verileri görüntülemeden önce geçerli kültürü Fransızca (Fransa) olarak ayarlar ve ardından İngilizce 'ye (ABD) ayarlar. Her durumda, ay adları ve sıcaklıklar bu kültür için uygun biçimde görüntülenir. İki kültürün sıcaklık değerinde farklı ondalık ayırıcılar kullandığını unutmayın. Ayrıca, örneğin tam ay adını görüntülemek için "MMMM" özel tarih ve saat biçimi dizesini kullandığını ve <xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A?displayProperty=nameWithType> dizideki en uzun ay adının uzunluğunu belirleyerek sonuç dizesinde ay adı için uygun miktarda alan ayırdığını da unutmayın.

[!code-csharp[Conceptual.Globalization#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/numbers1.cs#5)]
[!code-vb[Conceptual.Globalization#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/numbers1.vb#5)]

### <a name="persist-numeric-values"></a>Sayısal değerleri persist

Sayısal verileri kültüre özgü bir biçimde asla devam etmemelisiniz. Bu, bozuk verilerle veya çalışma zamanı özel durumla sonuçlanan yaygın bir programlama hatasıdır. Aşağıdaki örnek, on rasgele kayan nokta numarası oluşturur ve daha sonra Bunları İngilizce (ABD) kültürünün biçimlendirme kurallarını kullanarak dizeleri olarak serileştirir. Veriler İngilizce (ABD) kültürünün kuralları kullanılarak alınıp ayrıştırıldığında, başarıyla geri yüklenir. Ancak, Fransız (Fransa) kültürünün kuralları kullanılarak alınıp ayrıştırıldığında, kültürler farklı ondalık ayırıcılar kullandığından sayıların hiçbiri ayrıştırılamaz.

[!code-csharp[Conceptual.Globalization#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/numbers2.cs#6)]
[!code-vb[Conceptual.Globalization#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/numbers2.vb#6)]

Bu sorunu önlemek için şu tekniklerden birini kullanabilirsiniz:

- Kullanıcının kültüründen bağımsız olarak aynı olan özel bir biçim dizesi kullanarak sayının dize temsilini kaydedin ve ayrıştırın.

- Özellik tarafından döndürülen değişmez kültürün biçimlendirme kurallarını kullanarak sayıyı bir dize olarak kaydedin. <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>

- Sayıyı dize biçimi yerine ikili olarak serileştirin.

Aşağıdaki örnek, son yaklaşımı göstermektedir. Bu değerler dizi <xref:System.Double> serileştirir ve daha sonra deserializes ve İngilizce (Amerika Birleşik Devletleri) ve Fransız (Fransa) kültürlerin biçimlendirme kuralları nı kullanarak bunları görüntüler.

[!code-csharp[Conceptual.Globalization#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/numbers3.cs#7)]
[!code-vb[Conceptual.Globalization#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/numbers3.vb#7)]

Para birimi değerlerini serihale getirmek özel bir durumdur. Çünkü bir para birimi değeri ifade edildiği para birimine bağlıdır; bağımsız bir sayısal değer olarak ele almak için çok az mantıklı. Ancak, para birimi değerini para birimi simgesi içeren biçimlendirilmiş bir dize olarak kaydederseniz, aşağıdaki örnekte görüldüğü gibi, varsayılan kültürü farklı bir para birimi simgesi kullanan bir sistemde deserialized olamaz.

[!code-csharp[Conceptual.Globalization#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/currency1.cs#16)]
[!code-vb[Conceptual.Globalization#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/currency1.vb#16)]

Bunun yerine, değerin ve para birimi sembolünün geçerli kültürden bağımsız olarak ayrışabilmesi için, kültürün adı gibi bazı kültürel bilgilerle birlikte sayısal değeri seri hale getirmelisiniz. Aşağıdaki örnek, iki üyeli `CurrencyValue` bir yapı yı <xref:System.Decimal> tanımlayarak bunu yapar: değerin ve değerin ait olduğu kültürün adı.

[!code-csharp[Conceptual.Globalization#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/currency2.cs#17)]
[!code-vb[Conceptual.Globalization#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/currency2.vb#17)]

## <a name="work-with-culture-specific-settings"></a>Kültüre özel ayarlarla çalışma

.NET'te <xref:System.Globalization.CultureInfo> sınıf belirli bir kültürü veya bölgeyi temsil eder. Bazı özellikleri, kültürün bazı yönleri hakkında belirli bilgiler sağlayan nesneleri döndürmektedir:

- Özellik, <xref:System.Globalization.CultureInfo.CompareInfo%2A?displayProperty=nameWithType> kültürün <xref:System.Globalization.CompareInfo> dizeleri nasıl karşılaştırır ve sipariş ler hakkında bilgi içeren bir nesne döndürür.

- Özellik, <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> tarih <xref:System.Globalization.DateTimeFormatInfo> ve saat verilerini biçimlendirmede kullanılan kültüre özgü bilgileri sağlayan bir nesne döndürür.

- Özellik, <xref:System.Globalization.CultureInfo.NumberFormat%2A?displayProperty=nameWithType> sayısal <xref:System.Globalization.NumberFormatInfo> verileri biçimlendirmede kullanılan kültüre özgü bilgiler sağlayan bir nesne döndürür.

- Özellik, <xref:System.Globalization.CultureInfo.TextInfo%2A?displayProperty=nameWithType> kültürün <xref:System.Globalization.TextInfo> yazma sistemi hakkında bilgi sağlayan bir nesne döndürür.

Genel olarak, belirli <xref:System.Globalization.CultureInfo> özellikleri ve ilgili nesnelerin değerleri hakkında herhangi bir varsayımda bulunmayın. Bunun yerine, kültüre özgü verileri şu nedenlerden dolayı değiştirilebilir olarak görüntülemeniz gerekir:

- Veriler düzeltildikçe, daha iyi veriler kullanılabilir hale geldikçe veya kültüre özel sözleşmeler değiştikçe, tek tek özellik değerleri zaman içinde değişebilir ve değişebilir.

- Tek tek özellik değerleri .NET veya işletim sistemi sürümlerine göre değişebilir.

- .NET değiştirme kültürleri destekler. Bu, mevcut standart kültürleri tamamlayan veya varolan standart kültürün tamamen yerini alan yeni bir özel kültürün tanımlanmasını mümkün kılar.

- Windows sistemlerinde, kullanıcı Denetim Masası'ndaki **Bölge ve Dil** uygulamasını kullanarak kültüre özel ayarları özelleştirebilir. Bir <xref:System.Globalization.CultureInfo> nesneyi anında yaptığınızda, <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> oluşturucuyu arayarak bu kullanıcı özelleştirmelerini yansıtıp yansıtmadığını belirleyebilirsiniz. Genellikle, son kullanıcı uygulamaları için kullanıcı tercihlerine saygı göstermelisiniz, böylece kullanıcıya bekledikleri biçimde veriler sunulur.

## <a name="see-also"></a>Ayrıca bkz.

- [Genelleştirme ve Yerelleştirme](../../../docs/standard/globalization-localization/index.md)
- [Dizeleri Kullanmak için En İyi Uygulamalar](../../../docs/standard/base-types/best-practices-strings.md)
