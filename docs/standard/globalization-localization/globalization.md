---
description: 'Daha fazla bilgi edinin: Genelleştirme'
title: Genelleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- globalization [.NET], about globalization
- global applications, globalization
- international applications [.NET], globalization
- world-ready applications, globalization
- application development [.NET], globalization
- culture, globalization
ms.assetid: 4e919934-6b19-42f2-b770-275a4fae87c9
ms.openlocfilehash: 3a95660624f116ca5600d71ee633ba0f14a72588
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99675864"
---
# <a name="globalization"></a>Genelleştirme

Genelleştirme, birden fazla kültürde kullanıcılar için yerelleştirilmiş arabirimleri ve bölgesel verileri destekleyen bir dünya çapında hazırlanma uygulaması tasarlamayı ve geliştirmeyi içerir. Tasarım aşamasına başlamadan önce, uygulamanızın destekleyeceği kültürü belirlemelisiniz. Bir uygulama varsayılan olarak tek bir kültür veya bölgeyi hedefliyorsa, ancak diğer kültürlerde veya bölgelerde kullanıcılara kolayca genişletilebilen şekilde tasarlayabilirsiniz ve yazabilirsiniz.

Geliştiriciler olarak, küllerimiz tarafından oluşturulan kullanıcı arabirimleri ve verileri hakkında varsayımlar vardır. Örneğin, Birleşik Devletler Ingilizce konuşan bir geliştirici için tarih ve saat verilerinin, biçimdeki bir dize olarak serileştirilmesi mükemmel bir şekilde `MM/dd/yyyy hh:mm:ss` görünür. Ancak, farklı bir kültürden bir sistemde bu dizenin serisini kaldırma, büyük olasılıkla bir <xref:System.FormatException> özel durum oluşturabilir veya yanlış veri üretebilir. Genelleştirme, kültüre özgü bu varsayımları tanımlamamızı ve uygulamanın tasarımını veya kodunu etkilememesini sağlar.

Bu makalede, bir Genelleştirilmiş uygulamasındaki dizeleri, tarih ve saat değerlerini ve sayısal değerleri işlerken dikkate almanız gereken bazı önemli sorunlar ve en iyi uygulamalar ele alınmaktadır.

## <a name="strings"></a>Dizeler

Her kültür veya bölge farklı karakterler ve karakter kümeleri kullandığından ve bunları farklı şekilde sıralabildiğinden, karakter ve dizelerin işlenmesi Genelleştirme 'nin bir odasıdır. Bu bölüm, genelleştirilmiş uygulamalarında dizeleri kullanmaya yönelik öneriler sağlar.

### <a name="use-unicode-internally"></a>Dahili olarak Unicode kullanma

Varsayılan olarak, .NET Unicode dizelerini kullanır. Bir Unicode dize, <xref:System.Char> her biri BIR UTF-16 kod birimini temsil eden sıfır, bir veya daha fazla nesneden oluşur. Dünyanın tamamında kullanılan her karakter kümesinde neredeyse her karakter için bir Unicode temsili vardır.

Windows işletim sistemi dahil birçok uygulama ve işletim sistemi, karakter kümelerini temsil etmek için kod sayfalarını da kullanabilir. Kod sayfaları tipik olarak 0x00 ile 0x7F arasındaki standart ASCII değerlerini içerir ve diğer karakterleri 0x80 ile 0xFF arasında kalan değerlere eşler. 0x80 ile 0xFF arasındaki değerlerin yorumu, belirli kod sayfasına bağlıdır. Bu nedenle, mümkünse Genelleştirilmiş uygulamasında kod sayfaları kullanmaktan kaçının.

Aşağıdaki örnek, bir sistemdeki varsayılan kod sayfası, verilerin kaydedildiği kod sayfasından farklı olduğunda kod sayfası verilerini yorumlama tehlikeleri gösterilmektedir. (Bu senaryonun benzetimini yapmak için örnek açıkça farklı kod sayfaları belirtir.) İlk olarak, örnek Yunan alfabesinin büyük harfli karakterlerinden oluşan bir diziyi tanımlar. Kod sayfası 737 (MS-DOS Yunanca olarak da bilinir) kullanarak bir bayt dizisine kodlar ve bayt dizisini bir dosyaya kaydeder. Dosya alınırsa ve bayt dizisinin kodu kod sayfası 737 kullanılarak kodu çözülerek, özgün karakterler geri yüklenir. Ancak, dosya alınırsa ve bayt dizisinin kodu, kod sayfası 1252 (veya Latin alfabedeki karakterleri temsil eden Windows-1252) kullanılarak çözülerek, özgün karakterler kaybedilir.

[!code-csharp[Conceptual.Globalization#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/codepages1.cs#1)]
[!code-vb[Conceptual.Globalization#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/codepages1.vb#1)]

Unicode kullanımı, aynı kod birimlerinin aynı karakterlerle eşleşmesini ve aynı karakterlerin her zaman aynı byte dizilerine eşlenmesini sağlar.

### <a name="use-resource-files"></a>Kaynak dosyalarını kullanma

Tek bir kültür veya bölgeyi hedefleyen bir uygulama geliştirseniz bile, Kullanıcı arabiriminde görüntülenen dizeleri ve diğer kaynakları depolamak için kaynak dosyalarını kullanmanız gerekir. Bunları hiçbir şekilde doğrudan kodunuza eklememelisiniz. Kaynak dosyalarının kullanılması birçok avantaj sağlar:

- Tüm dizeler tek bir konumda bulunur. Belirli bir dil veya kültür için değiştirilecek dizeleri belirlemek için kaynak kodunuzun tamamında arama yapmanız gerekmez.

- Dizelerin yinelenmesine gerek yoktur. Kaynak dosyalarını kullanmayan geliştiriciler genellikle birden çok kaynak kodu dosyasında aynı dizeyi tanımlar. Bu çoğaltma bir veya daha fazla örnek, bir dize değiştirildiğinde bir veya daha fazla örneğe göz atılma olasılığını artırır.

- Resimler veya ikili veriler gibi dize olmayan kaynakları, kaynak dosyasında ayrı bir tek başına dosyada depolamak yerine, kolayca alınabilmesi için ekleyebilirsiniz.

Yerelleştirilmiş bir uygulama oluşturuyorsanız kaynak dosyalarının kullanılması belirli avantajlar sağlar. Uydu derlemelerindeki kaynakları dağıtırken, ortak dil çalışma zamanı, özelliğin tanımladığı şekilde kullanıcının geçerli kullanıcı arabirimi kültürüne dayalı olarak kültüre uygun bir kaynak seçer <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> . Uygun kültüre özgü bir kaynak sağladığınızda ve bir nesneyi doğru şekilde örneklediğinizde ya da <xref:System.Resources.ResourceManager> kesin belirlenmiş bir kaynak sınıfı kullandığınızda çalışma zamanı uygun kaynakları alma ayrıntılarını işler.

Kaynak dosyaları oluşturma hakkında daha fazla bilgi için bkz. [kaynak dosyaları oluşturma](../../framework/resources/creating-resource-files-for-desktop-apps.md). Uydu derlemeleri oluşturma ve dağıtma hakkında daha fazla bilgi için bkz. [uydu derlemeleri oluşturma](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md) ve [kaynakları paketleme ve dağıtma](../../framework/resources/packaging-and-deploying-resources-in-desktop-apps.md).

### <a name="search-and-compare-strings"></a>Dizeleri arama ve karşılaştırma

Mümkün olduğunda, dizeleri tek bir dizi karakter olarak işlemek yerine dizeleri tümüyle işlemeniz gerekir. Bu, Birleşik karakterlerin ayrıştırılmasından ilişkili sorunları engellemek için, alt dizeleri sıralayıp veya aradığınızda özellikle önemlidir.

> [!TIP]
> <xref:System.Globalization.StringInfo>Sınıfını bir dizedeki tek karakterler yerine metin öğeleriyle çalışmak için kullanabilirsiniz.

Dize aramalarındaki ve karşılaştırmalarda, yaygın bir hata, dizeyi bir nesne tarafından temsil edilen bir karakter koleksiyonu olarak değerlendirmek olur <xref:System.Char> . Aslında, tek bir karakter bir, iki veya daha fazla nesne ile oluşturulabilir <xref:System.Char> . Bu tür karakterler, alfabeller Unicode temel Latin karakter aralığı (U + 0021-U + 007E) dışındaki karakterlerden oluşan kültürlerin dizeleri içinde en sık bulunur. Aşağıdaki örnek, bir dizesinde aksan karakteri (U + 00C0) olan LATIN büyük harf A 'nın dizinini bulmaya çalışır. Ancak, bu karakter iki farklı şekilde temsil edilebilir: tek bir kod birimi (U + 00C0) veya bileşik bir karakter (iki kod birimi: U + 0041 ve U + 0300) olarak. Bu durumda, karakter dize örneğinde iki <xref:System.Char> nesne, u + 0041 ve u + 0300 olarak temsil edilir. Örnek kod, <xref:System.String.IndexOf%28System.Char%29?displayProperty=nameWithType> <xref:System.String.IndexOf%28System.String%29?displayProperty=nameWithType> Bu karakterin konumunu dize örneğinde bulmak için ve aşırı yüklerini çağırır, ancak bu farklı sonuçlar döndürür. İlk yöntem çağrısının bir <xref:System.Char> bağımsız değişkeni vardır; sıralı bir karşılaştırma gerçekleştirir ve bu nedenle bir eşleşme bulamaz. İkinci çağrının bir <xref:System.String> bağımsız değişkeni vardır; kültüre duyarlı bir karşılaştırma gerçekleştirir ve bu nedenle bir eşleşme bulur.

[!code-csharp[Conceptual.Globalization#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/search1.cs#18)]
[!code-vb[Conceptual.Globalization#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/search1.vb#18)]

Ya da yöntemi gibi bir parametre içeren aşırı yüklemeyi çağırarak, bu örneğin belirsizlerinden bazılarını (farklı sonuçlar döndüren bir yöntemin iki benzer aşırı yüküne çağrılar) engelleyebilirsiniz <xref:System.StringComparison> <xref:System.String.IndexOf%28System.String%2CSystem.StringComparison%29?displayProperty=nameWithType> <xref:System.String.LastIndexOf%28System.String%2CSystem.StringComparison%29?displayProperty=nameWithType> .

Ancak, aramalar her zaman kültüre duyarlı değildir. Aramanın amacı bir güvenlik kararı vermek veya bazı kaynaklara erişim izni vermek ya da erişimi engellemek ise, sonraki bölümde anlatıldığı gibi karşılaştırma sıralı olmalıdır.

### <a name="test-strings-for-equality"></a>Eşitlik için test dizeleri

Sıralama düzeninde nasıl karşılaştırılacağını belirleyebilmek yerine, eşitlik için iki dizeyi test etmek istiyorsanız, <xref:System.String.Equals%2A?displayProperty=nameWithType> veya gibi bir dize karşılaştırma yöntemi yerine yöntemini kullanın <xref:System.String.Compare%2A?displayProperty=nameWithType> <xref:System.Globalization.CompareInfo.Compare%2A?displayProperty=nameWithType> .

Eşitlik karşılaştırmaları genellikle bazı kaynaklara koşullu erişim için gerçekleştirilir. Örneğin, bir parolayı doğrulamak veya bir dosyanın var olduğunu doğrulamak için eşitlik için bir karşılaştırma gerçekleştirebilirsiniz. Bu tür dil olmayan karşılaştırmalar her zaman kültüre duyarlı yerine sıralı olmalıdır. Genel olarak, örnek <xref:System.String.Equals%28System.String%2CSystem.StringComparison%29?displayProperty=nameWithType> yöntemini veya statik <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> yöntemi <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> parolalar gibi dizeler için ve <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> dosya adları veya URI 'ler gibi dizeler için bir değer ile çağırmanız gerekir.

Eşitlik karşılaştırmaları bazen yönteme çağrılar yerine aramalardan veya alt dize karşılaştırmalarını içerir <xref:System.String.Equals%2A?displayProperty=nameWithType> . Bazı durumlarda, alt dizenin başka bir dizeye eşit olup olmadığını anlamak için bir alt dize araması kullanabilirsiniz. Bu karşılaştırmanın amacı dil olmayan bir değer ise, arama kültüre duyarlı değil de sıralı olmalıdır.

Aşağıdaki örnek, dile duyarlı olmayan verilerde kültüre duyarlı aramanın tehlikini gösterir. `AccessesFileSystem`Yöntemi, "dosya" alt dizesi ile başlayan URI 'ler için dosya sistemi erişimini yasaklamak üzere tasarlanmıştır. Bunu yapmak için, URI 'nin başlangıcını "dosya" dizesiyle kültüre duyarlı, büyük/küçük harfe duyarsız bir karşılaştırma gerçekleştirir. Dosya sistemine erişen bir URI "dosya:" ya da "dosya:" ile başlayabilir, örtük varsayım "i" (U + 0069) her zaman "I" (U + 0049) ' in küçük harfli eşdeğeri. Ancak Türkçe ve Azerbaycan 'da, "i" büyük harfli sürümü "i" dir (U + 0130). Bu tutarsızlık nedeniyle, kültüre duyarlı karşılaştırma, izin verilmeyen durumlarda dosya sistemi erişimine izin verir.

[!code-csharp[Conceptual.Globalization#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/equals1.cs#12)]
[!code-vb[Conceptual.Globalization#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/equals1.vb#12)]

Aşağıdaki örnekte gösterildiği gibi, büyük/küçük harf durumunu yok sayan bir sıralı karşılaştırma gerçekleştirerek bu sorundan kaçınabilirsiniz.

[!code-csharp[Conceptual.Globalization#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/equals2.cs#13)]
[!code-vb[Conceptual.Globalization#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/equals2.vb#13)]

### <a name="order-and-sort-strings"></a>Dizeleri sıralama ve sıralama

Genellikle, Kullanıcı arabiriminde görüntülenecek olan sıralı dizeler kültür temelinde sıralanmalıdır. Çoğu bölüm için, veya gibi dizeleri sıralayan bir yöntemi çağırdığınızda, bu tür dize karşılaştırmaları .NET tarafından örtük olarak işlenir <xref:System.Array.Sort%2A?displayProperty=nameWithType> <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> . Varsayılan olarak, dizeler geçerli kültürün sıralama kuralları kullanılarak sıralanır. Aşağıdaki örnek, bir dizi dizenin Ingilizce (Birleşik Devletler) kültürün ve Isveççe (Isveç) kültürünün kuralları kullanılarak sıralandığında farklılık gösterir.

[!code-csharp[Conceptual.Globalization#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/sort1.cs#14)]
[!code-vb[Conceptual.Globalization#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/sort1.vb#14)]

Kültüre duyarlı dize karşılaştırması, <xref:System.Globalization.CompareInfo> her bir kültürün özelliği tarafından döndürülen nesnesi tarafından tanımlanır <xref:System.Globalization.CultureInfo.CompareInfo%2A?displayProperty=nameWithType> . Yöntem aşırı yüklerini kullanan kültüre duyarlı dize karşılaştırmaları <xref:System.String.Compare%2A?displayProperty=nameWithType> de <xref:System.Globalization.CompareInfo> nesnesini kullanır.

.NET, dize verilerinde kültüre duyarlı sıralamalar gerçekleştirmek için tabloları kullanır. Sıralama ağırlıkları ve dize normalleştirmesi üzerinde veri içeren bu tabloların içeriği, belirli bir .NET sürümü tarafından uygulanan Unicode standardı sürümüne göre belirlenir. Aşağıdaki tabloda, belirtilen .NET sürümleri tarafından uygulanan Unicode sürümleri listelenmiştir. Desteklenen Unicode sürümlerinin bu listesi yalnızca karakter karşılaştırma ve sıralama için geçerlidir; Kategoriye göre Unicode karakterlerin sınıflandırmasına uygulanmaz. Daha fazla bilgi için, makalesindeki "dizeler ve Unicode standart" bölümüne bakın <xref:System.String> .

|.NET Framework sürümü|İşletim sistemi|Unicode sürümü|
|----------------------------|----------------------|---------------------|
|.NET Framework 2.0|Tüm işletim sistemleri|Unicode 4,1|
|.NET Framework 3.0|Tüm işletim sistemleri|Unicode 4,1|
|.NET Framework 3.5|Tüm işletim sistemleri|Unicode 4,1|
|.NET Framework 4|Tüm işletim sistemleri|Unicode 5,0|
|Windows 7 ' de .NET Framework 4,5 ve üzeri|Unicode 5,0|
|Windows 8 ve sonraki işletim sistemlerinde .NET Framework 4,5 ve üzeri|Unicode 6.3.0|
|.NET Core ve .NET 5 +|, Temel alınan işletim sistemi tarafından desteklenen Unicode standart sürümüne bağlıdır.|

.NET Framework 4,5 ve tüm .NET Core ve .NET 5 + sürümlerinde, dize karşılaştırma ve sıralama işletim sistemine bağlıdır. Windows 7 ' de çalışan .NET Framework 4,5 ve üzeri, Unicode 5,0 uygulayan kendi tablolarından veri alır. Windows 8 ve üzeri sürümlerde çalışan .NET Framework 4,5 ve üzeri, Unicode 6,3 uygulayan işletim sistemi tablolarından veri alır. .NET Core ve .NET 5 + ' da desteklenen Unicode sürümü temeldeki işletim sistemine bağlıdır. Kültüre duyarlı sıralanmış verileri seri hale <xref:System.Globalization.SortVersion> getirilebiliyorsanız, .net ve işletim sisteminin sıralama düzeni ile tutarlı olması için seri hale getirilmiş verilerinizin ne zaman sıralanması gerektiğini öğrenmek için sınıfını kullanabilirsiniz. Bir örnek için, bkz <xref:System.Globalization.SortVersion> . sınıf konusu.

Uygulamanız, kültüre özgü kapsamlı dize verisi sıralamayı gerçekleştiriyorsa, <xref:System.Globalization.SortKey> dizeleri karşılaştırmak için sınıfıyla çalışabilirsiniz. Sıralama anahtarı, belirli bir dizenin alfabetik, büyük/küçük harf ve aksan kalınlıkları dahil olmak üzere kültüre özgü sıralama ağırlıklarını yansıtır. Sıralama anahtarlarını kullanan karşılaştırmalar ikili olduğundan, örtük veya açık bir şekilde nesne kullanan karşılaştırmalardan daha hızlıdır <xref:System.Globalization.CompareInfo> . Dizeyi yöntemine geçirerek belirli bir dize için kültüre özgü bir sıralama anahtarı oluşturursunuz <xref:System.Globalization.CompareInfo.GetSortKey%2A?displayProperty=nameWithType> .

Aşağıdaki örnek, önceki örneğe benzerdir. Ancak yöntemini <xref:System.Array.Sort%28System.Array%29?displayProperty=nameWithType> dolaylı olarak çağıran yöntemini çağırmak yerine, tarafından <xref:System.Globalization.CompareInfo.Compare%2A?displayProperty=nameWithType> <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> örnekleyen ve yöntemine geçen sıralama anahtarlarını karşılaştıran bir uygulama tanımlar <xref:System.Array.Sort%60%601%28%60%600%5B%5D%2CSystem.Collections.Generic.IComparer%7B%60%600%7D%29?displayProperty=nameWithType> .

[!code-csharp[Conceptual.Globalization#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/sortkey1.cs#15)]
[!code-vb[Conceptual.Globalization#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/sortkey1.vb#15)]

### <a name="avoid-string-concatenation"></a>Dize birleştirmesini önleyin

Tüm mümkünse, birleştirilmiş ifadelerden çalışma zamanında oluşturulan bileşik dizeleri kullanmaktan kaçının. Genellikle uygulamanın özgün dilinde diğer yerelleştirilmiş dillere uygulanmayan bir dilbilgisi sırası varsaydığından, bileşik dizelerin yerelleştirilmesi zordur.

## <a name="handle-dates-and-times"></a>Tarihleri ve saatleri işle

Tarih ve saat değerlerini nasıl işleyişinizde, bunların Kullanıcı arabiriminde görüntülenip görüntülenmediğini veya kalıcı olduğunu gösterir. Bu bölüm her iki kullanımı inceler. Ayrıca, tarih ve saatlerle çalışırken saat dilimi farklarını ve aritmetik işlemleri nasıl işleyebileceğinizi de açıklar.

### <a name="display-dates-and-times"></a>Tarihleri ve saatleri görüntüleme

Genellikle, tarihler ve saatler Kullanıcı arabiriminde görüntülendiğinde, <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> özelliği tarafından ve <xref:System.Globalization.DateTimeFormatInfo> özelliği tarafından döndürülen nesne tarafından tanımlanan Kullanıcı kültürünün biçimlendirme kurallarını kullanmanız gerekir `CultureInfo.CurrentCulture.DateTimeFormat` . Aşağıdaki yöntemlerden birini kullanarak bir tarihi biçimlendirdiğinizde geçerli kültürün biçimlendirme kuralları otomatik olarak kullanılır:

- Parametresiz <xref:System.DateTime.ToString?displayProperty=nameWithType> yöntemi

- <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType>Bir biçim dizesi içeren yöntemi

- Parametresiz <xref:System.DateTimeOffset.ToString?displayProperty=nameWithType> yöntemi

- <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType>Bir biçim dizesi içeren,

- Tarih ile birlikte kullanıldığında [Bileşik biçimlendirme](../base-types/composite-formatting.md) özelliği

Aşağıdaki örnek, 11 Ekim 2012 ' de güneş ve gün doğumu verilerini iki kez görüntüler. Önce geçerli kültürü Hırvatça (Hırvatistan) ve ardından Ingilizce (Büyük Britanya) olarak ayarlar. Her durumda, tarihler ve saatler o kültür için uygun biçimde görüntülenir.

[!code-csharp[Conceptual.Globalization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates1.cs#2)]
[!code-vb[Conceptual.Globalization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates1.vb#2)]

### <a name="persist-dates-and-times"></a>Tarihleri ve saatleri kalıcı yap

Tarih ve saat verilerini, kültüre göre değişebilen bir biçimde asla kalıcı hale getirebilmelisiniz. Bu, bozuk veriler veya çalışma zamanı özel durumu ile sonuçlanan yaygın bir programlama hatasıdır. Aşağıdaki örnek, Ingilizce (Birleşik Devletler) kültürün biçimlendirme kurallarını kullanarak 9 Ocak 2013 ve 18 Ağustos 2013 tarihleri arasında iki tarihi seri hale getirir. Veriler, Ingilizce (Birleşik Devletler) kültürün kuralları kullanılarak alınıp ayrıştırıldığında başarıyla geri yüklenir. Bununla birlikte, Ingilizce (Birleşik Krallık) kültürün kuralları kullanılarak alınıp ayrıştırıldığında, ilk tarih yanlışlıkla 1 Eylül olarak yorumlanır ve Gregoryen takviminde sekizinci mali bir ay olmadığından ikincisi ayrıştırılamaz.

[!code-csharp[Conceptual.Globalization#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates2.cs#3)]
[!code-vb[Conceptual.Globalization#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates2.vb#3)]

Bu sorundan üç şekilde kaçınabilirsiniz:

- Tarih ve saati dize yerine ikili biçimde seri hale getirme.

- Kullanıcının kültürüne bakılmaksızın aynı olan bir özel biçim dizesi kullanarak tarih ve saatin dize gösterimini kaydedin ve ayrıştırın.

- Dizeyi, sabit kültürün biçimlendirme kurallarını kullanarak kaydedin.

Aşağıdaki örnekte, son yaklaşım gösterilmektedir. Statik özelliği tarafından döndürülen sabit kültürün biçimlendirme kurallarını kullanır <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> .

[!code-csharp[Conceptual.Globalization#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates3.cs#4)]
[!code-vb[Conceptual.Globalization#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates3.vb#4)]

### <a name="serialization-and-time-zone-awareness"></a>Serileştirme ve saat dilimi tanıma

Bir tarih ve saat değeri, genel bir saatten ("" Ocak 2013, saat 9:00 ' de açık olan depolar) zaman içinde belirli bir zamanda ("Doğum tarihi: 2 Ocak 2013 6:32:00") kadar çeşitli yorumlamalar içerebilir. Bir zaman değeri zaman içinde belirli bir anda temsil ettiğinde ve onu serileştirilmiş bir değerden geri yüklediğinizde, kullanıcının coğrafi konumundan veya saat diliminden bağımsız olarak aynı anda bir kez temsil ettiğinden emin olmanız gerekir.

Aşağıdaki örnekte bu sorun gösterilmektedir. Tek bir yerel tarih ve saat değerini üç [Standart formatta](../base-types/standard-date-and-time-format-strings.md) ("G", genel tarih Için "G", sıralanabilir tarih/saat için "s" ve "o" gidiş dönüş tarihi/saati için, ikili biçimde) bir dize olarak kaydeder.

[!code-csharp[Conceptual.Globalization#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates4.cs#10)]
[!code-vb[Conceptual.Globalization#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates4.vb#10)]

Veriler, serileştirildiği sistemle aynı saat dilimindeki bir sistemde geri yüklendiğinde, seri durumdan çıkarılan tarih ve saat değerleri, çıktının gösterdiği gibi özgün değeri doğru şekilde yansıtır:

```console
'3/30/2013 6:00:00 PM' --> 3/30/2013 6:00:00 PM Unspecified
'2013-03-30T18:00:00' --> 3/30/2013 6:00:00 PM Unspecified
'2013-03-30T18:00:00.0000000-07:00' --> 3/30/2013 6:00:00 PM Local

3/30/2013 6:00:00 PM Local
```

Bununla birlikte, verileri farklı bir saat diliminde bulunan bir sisteme geri yüklerseniz, yalnızca "o" (gidiş-dönüş) standart biçim dizesiyle biçimlendirilen tarih ve saat değeri saat dilimi bilgilerini korur ve bu nedenle aynı anda aynı anlık değeri temsil eder. Bu çıktı, romantik standart saat dilimindeki bir sistemde tarih ve saat verileri geri yüklendiğinde çıktı:

```console
'3/30/2013 6:00:00 PM' --> 3/30/2013 6:00:00 PM Unspecified
'2013-03-30T18:00:00' --> 3/30/2013 6:00:00 PM Unspecified
'2013-03-30T18:00:00.0000000-07:00' --> 3/31/2013 3:00:00 AM Local

3/30/2013 6:00:00 PM Local
```

Verilerin Serisi kaldırılan sistemin saat diliminden bağımsız olarak tek bir süreyi temsil eden bir tarih ve saat değerini doğru bir şekilde yansıtmak için aşağıdakilerden birini yapabilirsiniz:

- "O" (gidiş-dönüş) standart biçim dizesini kullanarak değeri bir dize olarak kaydedin. Sonra hedef sistemde serisini kaldırma.

- Bunu UTC 'ye dönüştürün ve "r" (RFC1123) standart biçim dizesini kullanarak dize olarak kaydedin. Sonra hedef sistemde serisini kaldırıp yerel saate dönüştürün.

- UTC 'ye dönüştürün ve "u" (Evrensel sıralanabilir) standart biçim dizesini kullanarak dize olarak kaydedin. Sonra hedef sistemde serisini kaldırıp yerel saate dönüştürün.

- UTC 'ye dönüştürün ve ikili biçimde kaydedin. Sonra hedef sistemde serisini kaldırıp yerel saate dönüştürün.

Aşağıdaki örnekte her bir yöntem gösterilmektedir.

[!code-csharp[Conceptual.Globalization#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates8.cs#11)]
[!code-vb[Conceptual.Globalization#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates8.vb#11)]

Veriler Pasifik standart saat dilimindeki bir sistemde serileştirildiğinde ve Latin standart saat dilimindeki bir sistemde serisi kaldırıldığında, örnek aşağıdaki çıktıyı görüntüler:

```console
'2013-03-30T18:00:00.0000000-07:00' --> 3/31/2013 3:00:00 AM Local
'Sun, 31 Mar 2013 01:00:00 GMT' --> 3/31/2013 3:00:00 AM Local
'2013-03-31 01:00:00Z' --> 3/31/2013 3:00:00 AM Local

3/31/2013 3:00:00 AM Local
```

Daha fazla bilgi için bkz. [saat dilimleri arasında süreleri dönüştürme](../datetime/converting-between-time-zones.md).

### <a name="perform-date-and-time-arithmetic"></a>Tarih ve saat aritmetiği yapma

Hem <xref:System.DateTime> hem de <xref:System.DateTimeOffset> türleri aritmetik işlemleri destekler. İki tarih değeri arasındaki farkı hesaplayabilir veya bir tarih değerine belirli zaman aralıklarını ekleyebilir veya buradan çıkarabilirsiniz. Ancak tarih ve saat değerlerinde aritmetik işlemler, saat dilimlerini ve saat dilimi ayarlama kurallarını hesaba götüremez. Bu nedenle, zaman içinde süresi temsil eden değerler üzerinde tarih ve saat aritmetiği hatalı sonuçlar döndürebilir.

Örneğin, Pasifik standart saati ile Pasifik yaz saati arasındaki geçiş, Mart ayının ikinci Pazar günü (2013 yılı için 10 Mart 'ta) oluşur. Aşağıdaki örnekte gösterildiği gibi, 9 Mart 48 ' den sonra saat olan tarih ve saati hesaplarsanız, 10:30:2013 Pasifik standart saat dilimindeki bir sistemde, 11 Mart 2013 ' den 10:30 itibaren, saat ayarlamasının hesaba göre yapılmadığından elde edilmesine neden olacak.

[!code-csharp[Conceptual.Globalization#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates5.cs#8)]
[!code-vb[Conceptual.Globalization#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates5.vb#8)]

Tarih ve saat değerlerinde bir aritmetik işlemin doğru sonuçlar ürettiğinden emin olmak için şu adımları izleyin:

1. Kaynak saat dilimindeki saati UTC 'ye dönüştürür.

2. Aritmetik işlemi gerçekleştirin.

3. Sonuç bir tarih ve saat değeri ise UTC 'den kaynak saat dilimindeki zamana dönüştürün.

Aşağıdaki örnek, önceki örneğe benzerdir, ancak bu üç adımı, 9 Mart 10:30 2013 ' ye doğru bir şekilde 48 saat eklemek için

[!code-csharp[Conceptual.Globalization#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates6.cs#9)]
[!code-vb[Conceptual.Globalization#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates6.vb#9)]

Daha fazla bilgi için bkz. [Tarih ve saatlerle aritmetik Işlemler gerçekleştirme](../datetime/performing-arithmetic-operations.md).

### <a name="use-culture-sensitive-names-for-date-elements"></a>Tarih öğeleri için kültüre duyarlı adlar kullanma

Uygulamanızın ayın adını veya haftanın gününü görüntülemesi gerekebilir. Bunu yapmak için, aşağıdaki gibi bir kod yaygındır.

[!code-csharp[Conceptual.Globalization#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/monthname1.cs#19)]
[!code-vb[Conceptual.Globalization#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/monthname1.vb#19)]

Ancak, bu kod her zaman Ingilizce 'deki haftanın günlerinin adlarını döndürür. Ayın adını çıkaran kod genellikle daha fazla bilgi olarak bilinir. Bu, genellikle belirli bir dildeki ayların adlarıyla birlikte on iki aylık bir takvimi kabul eder.

[Özel tarih ve saat biçimi dizelerini](../base-types/custom-date-and-time-format-strings.md) veya nesnenin özelliklerini kullanarak <xref:System.Globalization.DateTimeFormatInfo> , aşağıdaki örnekte gösterildiği gibi, kullanıcının kültürüne ait haftanın günleri veya ay adlarını yansıtan dizeleri ayıklamak kolaydır. Geçerli kültürü Fransızca (Fransa) olarak değiştirir ve Haftanın gününün adını ve 1 Temmuz 2013 için ayın adını görüntüler.

[!code-csharp[Conceptual.Globalization#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/monthname2.cs#20)]
[!code-vb[Conceptual.Globalization#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/monthname2.vb#20)]

## <a name="numeric-values"></a>Sayısal değerler

Sayıların işlenmesi, bunların Kullanıcı arabiriminde mi yoksa kalıcı mı olduğuna bağlıdır. Bu bölüm her iki kullanımı inceler.

> [!NOTE]
> Ayrıştırma ve biçimlendirme işlemlerinde, .NET, sayısal basamaklar olarak yalnızca 0 ile 9 arasında (U + 0030 ile U + 0039) temel Latin karakterlerini tanır.

### <a name="display-numeric-values"></a>Sayısal değerleri görüntüle

Genellikle, Kullanıcı arabiriminde numaralar görüntülenirken, <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> özelliği tarafından ve <xref:System.Globalization.NumberFormatInfo> özelliği tarafından döndürülen nesne tarafından tanımlanan Kullanıcı kültürünün biçimlendirme kurallarını kullanmanız gerekir `CultureInfo.CurrentCulture.NumberFormat` . Aşağıdaki yöntemlerden birini kullanarak bir tarihi biçimlendirdiğinizde geçerli kültürün biçimlendirme kuralları otomatik olarak kullanılır:

- Parametresiz `ToString` herhangi bir sayısal tür yöntemi

- `ToString(String)`Bağımsız değişken olarak bir biçim dizesi içeren herhangi bir sayısal tür yöntemi

- [Bileşik biçimlendirme](../base-types/composite-formatting.md) özelliği, sayısal değerlerle kullanıldığında

Aşağıdaki örnek, Paris, Fransa 'daki aylık ortalama sıcaklık sayısını görüntüler. Önce, verileri görüntülemeden önce geçerli kültürü Fransızca (Fransa) olarak ayarlar ve ardından Ingilizce (Birleşik Devletler) olarak ayarlar. Her durumda, ay adları ve sıcaklıklar o kültür için uygun olan biçimde görüntülenir. İki kültürlerin sıcaklık değerinde farklı Ondalık ayırıcılar kullandığına unutmayın. Ayrıca, tam ay adını göstermek için "aaaa" özel tarih ve saat biçim dizesini ve dizideki en uzun ay adının uzunluğunu belirleyerek sonuç dizesindeki ay adı için uygun alan miktarını ayırdığını unutmayın <xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A?displayProperty=nameWithType> .

[!code-csharp[Conceptual.Globalization#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/numbers1.cs#5)]
[!code-vb[Conceptual.Globalization#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/numbers1.vb#5)]

### <a name="persist-numeric-values"></a>Sayısal değerleri kalıcı yap

Sayısal verileri asla kültüre özgü bir biçimde kalıcı yapmanız gerekir. Bu, bozuk veriler veya çalışma zamanı özel durumu ile sonuçlanan yaygın bir programlama hatasıdır. Aşağıdaki örnek on rastgele kayan noktalı sayılar oluşturur ve Ingilizce (Birleşik Devletler) kültürün biçimlendirme kurallarını kullanarak bunları dizeler olarak serileştirir. Veriler, Ingilizce (Birleşik Devletler) kültürün kuralları kullanılarak alınıp ayrıştırıldığında başarıyla geri yüklenir. Ancak, Fransızca (Fransa) kültürünün kuralları kullanılarak alınıp ayrıştırıldığında, kültürler farklı Ondalık ayırıcılar kullandığından sayıların hiçbiri ayrıştırılamaz.

[!code-csharp[Conceptual.Globalization#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/numbers2.cs#6)]
[!code-vb[Conceptual.Globalization#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/numbers2.vb#6)]

Bu sorundan kaçınmak için şu tekniklerden birini kullanabilirsiniz:

- Kullanıcının kültürüne bakılmaksızın aynı olan bir özel biçim dizesi kullanarak sayının dize gösterimini kaydedin ve ayrıştırın.

- Özelliği tarafından döndürülen sabit kültürün biçimlendirme kurallarını kullanarak numarayı bir dize olarak kaydedin <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> .

- Sayıyı dize biçimi yerine binary olarak seri hale getirme.

Aşağıdaki örnekte, son yaklaşım gösterilmektedir. Değer dizisini serileştirir <xref:System.Double> ve sonra İngilizce (Birleşik Devletler) ve Fransızca (Fransa) kültürlerin biçimlendirme kurallarını kullanarak bunları yeniden serileştirir ve görüntüler.

[!code-csharp[Conceptual.Globalization#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/numbers3.cs#7)]
[!code-vb[Conceptual.Globalization#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/numbers3.vb#7)]

Para birimi değerlerinin serileştirilmesi özel bir durumdur. Bir para birimi değeri, ifade edildiği para birimine bağlı olduğundan, Bunu bağımsız bir sayısal değer olarak değerlendirmek biraz anlamlı olur. Bununla birlikte, bir para birimi değerini bir para birimi simgesi içeren biçimli bir dize olarak kaydederseniz, aşağıdaki örnekte gösterildiği gibi varsayılan kültür farklı bir para birimi sembolü kullanan bir sistemde seri durumdan çıkarılamaz.

[!code-csharp[Conceptual.Globalization#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/currency1.cs#16)]
[!code-vb[Conceptual.Globalization#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/currency1.vb#16)]

Bunun yerine, sayısal değeri kültür adı gibi bazı kültürel bilgileriyle ve değer ve para birimi simgesi geçerli kültürden bağımsız olarak seri durumdan çıkarılacak şekilde seri hale getirebilirsiniz. Aşağıdaki örnek, `CurrencyValue` iki üyeli bir yapı tanımlayarak bunu yapar: değer <xref:System.Decimal> ve değerin ait olduğu kültürün adı.

[!code-csharp[Conceptual.Globalization#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/currency2.cs#17)]
[!code-vb[Conceptual.Globalization#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/currency2.vb#17)]

## <a name="work-with-culture-specific-settings"></a>Kültüre özgü ayarlarla çalışma

.NET sürümünde, <xref:System.Globalization.CultureInfo> sınıfı belirli bir kültürü veya bölgeyi temsil eder. Bazı özellikleri, kültürün bazı yönlerinin belirli bilgilerini sağlayan nesneleri döndürür:

- <xref:System.Globalization.CultureInfo.CompareInfo%2A?displayProperty=nameWithType>Özelliği <xref:System.Globalization.CompareInfo> , kültürün dizeleri nasıl karşılaştırdığı ve sıraladığı hakkında bilgi içeren bir nesnesi döndürür.

- <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType>Özelliği, <xref:System.Globalization.DateTimeFormatInfo> Tarih ve saat verilerinde biçimlendirme için kullanılan kültüre özgü bilgiler sağlayan bir nesne döndürür.

- <xref:System.Globalization.CultureInfo.NumberFormat%2A?displayProperty=nameWithType>Özelliği, <xref:System.Globalization.NumberFormatInfo> sayısal verileri biçimlendirmede kullanılan kültüre özgü bilgiler sağlayan bir nesne döndürür.

- <xref:System.Globalization.CultureInfo.TextInfo%2A?displayProperty=nameWithType>Özelliği <xref:System.Globalization.TextInfo> , kültürün yazma sistemi hakkında bilgi sağlayan bir nesne döndürür.

Genel olarak, belirli <xref:System.Globalization.CultureInfo> Özellikler ve bunlarla ilgili nesneler hakkında herhangi bir varsayım yapmayın. Bunun yerine, kültüre özgü verileri değiştirmek için aşağıdaki nedenlerden dolayı görüntülemeniz gerekir:

- Bireysel özellik değerleri zaman içinde değişiklik ve düzeltmeye tabidir, veriler düzeltildiğinden daha iyi veriler kullanılabilir hale gelir veya kültüre özgü kurallar değişir.

- Bireysel özellik değerleri .NET veya işletim sistemi sürümlerinin sürümleri arasında farklılık gösterebilir.

- .NET, değiştirme kültürlerini destekler. Bu, varolan standart kültürleri tamamlayan veya mevcut bir standart kültürün tamamen yerini alan yeni bir özel kültür tanımlamanızı mümkün kılar.

- Windows sistemlerinde Kullanıcı, Denetim Masası 'ndaki **bölge ve dil** uygulamasını kullanarak kültüre özgü ayarları özelleştirebilir. Bir nesne örneğini oluşturduğunuzda <xref:System.Globalization.CultureInfo> , oluşturucuyu çağırarak bu kullanıcı özelleştirmelerini yansıtmasının gerekip gerekmediğini belirleyebilirsiniz <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29> . Genellikle, son kullanıcı uygulamaları için Kullanıcı tercihlerinin, kullanıcının bekledikleri bir biçimde veri sunulmasını sağlayacak şekilde dikkate almanız gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [Genelleştirme ve yerelleştirme](index.md)
- [Dizeleri kullanmak için en iyi uygulamalar](../base-types/best-practices-strings.md)
