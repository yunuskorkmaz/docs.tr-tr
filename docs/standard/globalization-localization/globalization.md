---
title: "Genelleştirme"
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
- globalization [.NET Framework], about globalization
- global applications, globalization
- international applications [.NET Framework], globalization
- world-ready applications, globalization
- application development [.NET Framework], globalization
- culture, globalization
ms.assetid: 4e919934-6b19-42f2-b770-275a4fae87c9
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 357d18843af0af2869d0ec98def6c733e51f9a4c
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="globalization"></a>Genelleştirme
Genelleştirme tasarlama ve birden çok kültürü kullanıcılar için yerelleştirilmiş arabirimleri ve bölgesel veri destekleyen bir dünya çapında kullanılmaya hazır uygulaması geliştirme içerir. Tasarım aşaması başlamadan önce uygulamanızı destekleyecek hangi kültürler belirlemeniz gerekir. Bir uygulama bir tek kültür veya bölge varsayılan olarak hedefler rağmen tasarlayın ve böylece diğer kültürler veya bölgelerdeki kullanıcılar için kolayca genişletilebilir yazma.  
  
 Geliştiriciler, tüm kullanıcı arabirimleri ve bizim kültürler tarafından biçimlendirilmiş veriler hakkında varsayımlar sahibiz. Örneğin, bir İngilizce konuşan geliştiricisi Amerika Birleşik Devletleri'nde, tarih ve saat verileri biçiminde bir dize olarak seri hale getirme `MM/dd/yyyy hh:mm:ss` mükemmel makul gibi görünüyor. Ancak, farklı bir kültür sisteminde bu dizeyi seri durumdan throw olasıdır bir <xref:System.FormatException> özel durumu veya üretim yanlış bir veri. Genelleştirme gibi kültüre özgü varsayımlar tanımlamak ve bunlar bizim uygulamanın tasarım veya kod etkilemez emin olmak için bize sağlar.  
  
 Aşağıdaki bölümlerde bazı dikkate almanız gereken önemli sorunları ve dizeler, tarih ve saat değerleri ve bir globalized uygulamasında sayısal değerleri işlerken izleyebileceğiniz en iyi uygulamalar açıklanmaktadır.  
  
-   [Dizeleri işleme](../../../docs/standard/globalization-localization/globalization.md#HandlingStrings)  
  
    -   [Unicode dahili olarak kullanın](../../../docs/standard/globalization-localization/globalization.md#Strings_Unicode)  
  
    -   [Kaynak dosyaları kullan](../../../docs/standard/globalization-localization/globalization.md#Strings_Resources)  
  
    -   [Arama ve dizeleri karşılaştırma](../../../docs/standard/globalization-localization/globalization.md#Strings_Searching)  
  
    -   [Dizeleri eşitlik için test etme](../../../docs/standard/globalization-localization/globalization.md#Strings_Equality)  
  
    -   [Sıralama ve dizeleri sıralama](../../../docs/standard/globalization-localization/globalization.md#Strings_Ordering)  
  
    -   [Dize birleştirme kaçının](../../../docs/standard/globalization-localization/globalization.md#Strings_Concat)  
  
-   [Tarihler ve saatler işleme](../../../docs/standard/globalization-localization/globalization.md#DatesAndTimes)  
  
    -   [Kalıcı tarihler ve saatler](../../../docs/standard/globalization-localization/globalization.md#DatesAndTimes_Persist)  
  
    -   [Tarihler ve saatler görüntüleme](../../../docs/standard/globalization-localization/globalization.md#DatesAndTimes_Display)  
  
    -   [Seri hale getirme ve saat dilimi tanıma](../../../docs/standard/globalization-localization/globalization.md#DatesAndTimes_TimeZones)  
  
    -   [Tarih ve saat Aritmetiğinde gerçekleştirme](../../../docs/standard/globalization-localization/globalization.md#DatesAndTimes_Arithmetic)  
  
-   [Sayısal değerler işleme](../../../docs/standard/globalization-localization/globalization.md#Numbers)  
  
    -   [Sayısal değerler görüntüleme](../../../docs/standard/globalization-localization/globalization.md#Numbers_Display)  
  
    -   [Kalıcı sayısal değerler](../../../docs/standard/globalization-localization/globalization.md#Numbers_Persist)  
  
-   [Kültüre özgü ayarları ile çalışma](../../../docs/standard/globalization-localization/globalization.md#Cultures)  
  
<a name="HandlingStrings"></a>   
## <a name="handling-strings"></a>Dizeleri İşleme  
 Her kültür veya bölge farklı karakterleri ve karakter kümesi kullanın ve farklı sıralama karakterler ve dizeleri işlenmesini Genelleştirme, merkezi bir odağını kaynaklanır. Bu bölümde globalized uygulamalarında dizeleri kullanmak için öneriler sağlar.  
  
<a name="Strings_Unicode"></a>   
### <a name="use-unicode-internally"></a>Dahili Olarak Unicode Kullanma  
 Varsayılan olarak, .NET Framework Unicode dizelerini kullanır. Bir UNICODE dizesi sıfır, bir veya daha fazla oluşur <xref:System.Char> nesneleri, her biri bir UTF-16 kod birimi temsil eder. Neredeyse her karakter kullanımı dünyanın her kümesindeki her karakteri, Unicode temsili yoktur.  
  
 Birçok uygulama ve işletim sistemleri, Windows işletim sistemi dahil olmak üzere kullanım kod sayfaları karakter kümelerini göstermek için de kullanabilirsiniz. Kod sayfaları genellikle 0x00 0x7F aracılığıyla standart ASCII değerleri içeren ve başka karakterler, 0x80 0xFF üzerinden gelen kalan değerler eşleyin. 0xFF aracılığıyla 0x80 değerlerinden yorumu belirli kod sayfasına bağlıdır. Bu nedenle, kod sayfaları globalized bir uygulamada mümkünse yapmaktan kaçınmalısınız.  
  
 Aşağıdaki örnek, bir sistem varsayılan kod sayfasına veri kaydedilmiş olan kod sayfasından farklı olduğunda, kod sayfası verileri yorumlama tehlikeleri gösterilmektedir. (Bu senaryoda benzetimini yapmak için örnek açıkça farklı kod sayfaları belirtir.) İlk olarak, Yunanca Harf, büyük harf karakterlerden oluşan bir dizi örnek tanımlar. Kod sayfası 737 (MS-DOS Yunanca olarak da bilinir) kullanarak bir bayt dizisine kodlar ve bayt dizisi bir dosyaya kaydeder. Dosya alınır ve kod sayfası 737 kullanarak kendi bayt dizisi kodlanmamış yüklerseniz, özgün karakterlerin geri yüklenir. Ancak, dosya alınır ve 1252 kod sayfası (veya Latin alfabesi karakterleri temsil eden Windows-1252) kullanarak kendi bayt dizisi kodlanmamış, özgün karakterlerin kaybolur.  
  
 [!code-csharp[Conceptual.Globalization#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/codepages1.cs#1)]
 [!code-vb[Conceptual.Globalization#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/codepages1.vb#1)]  
  
 Unicode kullanımını, aynı kod birimleri her zaman aynı karakterle eşleştirmek ve aynı karakterler her zaman aynı bayt dizileri eşleme sağlar.  
  
<a name="Strings_Resources"></a>   
### <a name="use-resource-files"></a>Kaynak Dosyalarını Kullanma  
 Bir tek kültür veya bölge hedefleyen bir uygulama geliştiriyorsanız bile dizeler ve kullanıcı arabiriminde görüntülenir diğer kaynakları depolamak için kaynak dosyaları kullanmalısınız. Bunları doğrudan kodunuzu hiçbir zaman eklemelisiniz. Kaynak dosyaları kullanarak, çok sayıda avantaj vardır:  
  
-   Tüm tek bir konumda dizelerdir. Belirli bir dil veya kültür için değiştirme dizeleri tanımlamak için kaynak kodunuz genelinde arama gerekmez.  
  
-   Dizeleri yeniden oluşturmaya gerek yoktur. Kaynak dosyaları sık kullanmadığınız geliştiriciler birden çok kaynak kodu dosyaları aynı dizesini tanımlayın. Bu çoğaltma olasılık bir artırır veya bir dize değiştirildiğinde daha fazla örnekleri atlamış.  
  
-   Kolayca alınabilir şekilde ayrı tek başına dosyasında depolamak yerine kaynak dosyasında görüntüleri ya da ikili veriler, dize olmayan kaynaklar içerebilir.  
  
 Yerelleştirilmiş uygulama oluşturuyorsanız, kaynak dosyaları kullanarak belirli avantajları vardır. Uydu derlemeleri kaynaklarında dağıttığınızda, ortak dil çalışma zamanı tarafından tanımlandığı gibi kullanıcının geçerli UI kültürü dayalı olarak kültür uygun bir kaynağa otomatik olarak seçer. <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> özelliği. Uygun bir kültüre özgü kaynakları sağlayın ve doğru örnekleyin sürece bir <xref:System.Resources.ResourceManager> nesne veya kesin olarak belirtilmiş kaynak sınıfı kullanın, çalışma zamanı uygun kaynakları alma ayrıntılarını işler.  
  
 Kaynak dosyaları oluşturma hakkında daha fazla bilgi için bkz: [oluşturma kaynak dosyaları](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md). Oluşturma ve uydu derlemeleri dağıtma hakkında daha fazla bilgi için bkz: [uydu derlemeleri oluşturma](../../../docs/framework/resources/creating-satellite-assemblies-for-desktop-apps.md) ve [paketleme ve dağıtma kaynakları](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md).  
  
<a name="Strings_Searching"></a>   
### <a name="searching-and-comparing-strings"></a>Dizeleri Arama ve Karşılaştırma  
 Mümkün olduğunda, tek tek karakter dizisi olarak işleme yerine tüm dizeleri olarak dizeleri işlemesi gerekir. Bu sıralama veya sorunları önlemek için alt dizeleri, arama ayrıştırma birleştirilen karakter ile ilişkili olduğunda özellikle önemlidir.  
  
> [!TIP]
>  Kullanabileceğiniz <xref:System.Globalization.StringInfo> karakterleri tek tek bir dizede yerine metin öğeleri ile çalışmak için sınıf.  
  
 Dize aramaları karşılaştırmaları, ortak bir hata dizesi karakterleri, her biri ile temsil edilir koleksiyonu olarak işlemek için olup bir <xref:System.Char> nesnesi. Aslında, tek bir karakter birini, iki veya daha fazla tarafından oluşturulmuş olması <xref:System.Char> nesneleri. Bu tür karakterler en sık karakterleri (U + 0021 ile U + 007E) Unicode temel Latin karakter aralığı dışında olan alfabesinde oluşur kültürler dizelerden bulunur. Aşağıdaki örnek, bir dize dizini ile LATIN büyük harf A işareti karakterinin (U + 00 C 0) bulmayı dener. Ancak, bu karakter iki farklı şekilde temsil edilebilir: tek kod birimi (U + 00C 0) veya bir bileşik karakter olarak (iki kod birimleri: U + 007E 0021 ve U +). Bu durumda, karakter dizesi örneğinde iki tarafından temsil edilen <xref:System.Char> nesneleri, U + 007E 0021 ve U +. Örnek kod çağrıları <xref:System.String.IndexOf%28System.Char%29?displayProperty=nameWithType> ve <xref:System.String.IndexOf%28System.String%29?displayProperty=nameWithType> string örneği, ancak bunlar bu karakterin bulmak için aşırı farklı sonuçlar döndürür. İlk yöntem çağrısı sahip bir <xref:System.Char> bağımsız değişkeni; bir sıralı karşılaştırma gerçekleştirir ve bu nedenle bir eşleşme bulamıyor. İkinci çağrı sahip bir <xref:System.String> bağımsız değişkeni; kültüre duyarlı karşılaştırma gerçekleştirir ve bu nedenle bir eşleşme bulur.  
  
 [!code-csharp[Conceptual.Globalization#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/search1.cs#18)]
 [!code-vb[Conceptual.Globalization#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/search1.vb#18)]  
  
 Bu örnek (iki benzer aşırı farklı sonuçlar döndüren bir yöntem çağrıları) belirsizliği bazıları içeren bir aşırı çağırarak kaçının bir <xref:System.StringComparison> parametresi gibi <xref:System.String.IndexOf%28System.String%2CSystem.StringComparison%29?displayProperty=nameWithType> veya <xref:System.String.LastIndexOf%28System.String%2CSystem.StringComparison%29?displayProperty=nameWithType> yöntemi.  
  
 Ancak, arama her zaman kültüre duyarlı değildir. Arama amacı güvenlik kararı veya izin vermek veya bazı kaynağa erişimi engellemek için ise, karşılaştırma sonraki bölümde açıklandığı gibi sıralı, olması gerekir.  
  
<a name="Strings_Equality"></a>   
### <a name="testing-strings-for-equality"></a>Eşitlik için Sınama Ayarları  
 Bunlar sıralama düzenini nasıl karşılaştırmak belirleme yerine eşitlik kullanmak için iki dizeyi test etmek isterseniz <xref:System.String.Equals%2A?displayProperty=nameWithType> yöntemi gibi bir dize karşılaştırma yöntemi yerine <xref:System.String.Compare%2A?displayProperty=nameWithType> veya <xref:System.Globalization.CompareInfo.Compare%2A?displayProperty=nameWithType>.  
  
 Eşitlik karşılaştırmaları genellikle bazı kaynak koşullu erişim için gerçekleştirilir. Örneğin, bir parola doğrulamak veya bir dosyanın var olduğunu onaylamak için eşitliği karşılaştırma gerçekleştirebilir. Bu tür dil olmayan karşılaştırmaları her zaman sıralı yerine kültüre duyarlı olması gerekir. Genel olarak, örnek çağırmalıdır <xref:System.String.Equals%28System.String%2CSystem.StringComparison%29?displayProperty=nameWithType> yöntemi veya statik <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> değerini yöntemi <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> dizeleri parolaları ve değeri gibi <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> dosya adlarını veya URI gibi dizeleri.  
  
 Eşitlik karşılaştırmaları bazen ilgili aramalar veya alt dize karşılaştırmaları yerine çağrıları <xref:System.String.Equals%2A?displayProperty=nameWithType> yöntemi. Bazı durumlarda, bu alt dizeyi başka bir dize eşit olup olmadığını belirlemek için bir alt dizenin arama kullanabilir. Bu karşılaştırma amacı dil olmayan ise, aynı zamanda sıralı yerine kültüre duyarlı arama olması gerekir.  
  
 Aşağıdaki örnek bir kültüre duyarlı arama dil olmayan veriler üzerinde tehlike gösterilmektedir. `AccessesFileSystem` Yöntemi alt dizeyi "Dosyası" ile başlayan URI için dosya sistemi erişimi engellemek üzere tasarlanmıştır. Bunu yapmak için URI'sı "Dosyası" dizesi ile başlayan kültüre duyarlı, büyük küçük harf duyarsız bir karşılaştırma gerçekleştirir. Dosya sistemi erişen bir URI ile ya da başlayabilirsiniz olduğundan "dosya:" veya "dosya:", örtük varsayımına olan "i" (U + 0069) her zaman küçük harfli "Yeni" eşdeğerdir (U + 0049). Ancak, Türkçe ve Azerice, büyük harfli sürümünü içinde "i" olan "İ" (U + 0130). Yasaklanmış, bu farklılık nedeniyle kültüre duyarlı karşılaştırma dosya sistemi erişimi sağlar.  
  
 [!code-csharp[Conceptual.Globalization#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/equals1.cs#12)]
 [!code-vb[Conceptual.Globalization#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/equals1.vb#12)]  
  
 Bu sorunu durumda, aşağıdaki örnekte gösterildiği gibi yoksayar bir sıralı karşılaştırma gerçekleştirerek önleyebilirsiniz.  
  
 [!code-csharp[Conceptual.Globalization#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/equals2.cs#13)]
 [!code-vb[Conceptual.Globalization#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/equals2.vb#13)]  
  
<a name="Strings_Ordering"></a>   
### <a name="ordering-and-sorting-strings"></a>Dizeleri Sıralama ve Düzenleme  
 Genellikle, kullanıcı arabiriminde görüntülenecek olan sıralı dizeleri kültür göre sıralanması gerektiğini. Dizeleri gibi sıralar bir yöntemini çağırdığınızda çoğunlukla, bu tür dize karşılaştırmaları örtük olarak .NET Framework tarafından işlenir <xref:System.Array.Sort%2A?displayProperty=nameWithType> veya <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType>. Varsayılan olarak, geçerli kültürü sıralama kuralları kullanarak dizeleri sıralanır. Aşağıdaki örnek, İngilizce (ABD) kültür ve İsveççe (İsviçre) kültür kurallarını kullanarak bir dizeler dizisi sıralandığında fark gösterilmektedir.  
  
 [!code-csharp[Conceptual.Globalization#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/sort1.cs#14)]
 [!code-vb[Conceptual.Globalization#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/sort1.vb#14)]  
  
 Kültüre duyarlı dize karşılaştırma tarafından tanımlanan <xref:System.Globalization.CompareInfo> her kültürün tarafından döndürülen nesne <xref:System.Globalization.CultureInfo.CompareInfo%2A?displayProperty=nameWithType> özelliği. Kullanın kültüre duyarlı dize karşılaştırmalarını <xref:System.String.Compare%2A?displayProperty=nameWithType> yöntemi aşırı yüklemeleri ayrıca kullanım <xref:System.Globalization.CompareInfo> nesnesi.  
  
 .NET Framework tablolar üzerinde dize verilerini kültüre duyarlı sıralar gerçekleştirmek için kullanır. Sıralama ağırlıkları verileri içeren ve normalleştirme dize, bu tabloların içeriği, belirli bir .NET Framework sürümü tarafından uygulanan Unicode standart sürümü tarafından belirlenir. Aşağıdaki tabloda belirtilen .NET Framework sürümleri tarafından uygulanan Unicode sürümleri listelenmiştir. Bu Desteklenen sürümlerin listesi için Unicode karakter karşılaştırma ve yalnızca sıralama için geçerli olduğunu unutmayın; kategoriye göre Unicode karakterler sınıflandırılması için uygulanmaz. Daha fazla bilgi için "Dizeler ve Unicode standart" bölümüne bakın <xref:System.String> makalesi.  
  
|.NET Framework sürümü|İşletim sistemi|Unicode sürümü|  
|----------------------------|----------------------|---------------------|  
|.NET Framework 2.0|Tüm işletim sistemleri|Unicode 4.1|  
|.NET Framework 3.0|Tüm işletim sistemleri|Unicode 4.1|  
|.NET Framework 3.5|Tüm işletim sistemleri|Unicode 4.1|  
|.NET Framework 4|Tüm işletim sistemleri|Unicode 5.0|  
|.NET Framework 4.5|[!INCLUDE[win7](../../../includes/win7-md.md)]|Unicode 5.0|  
|.NET Framework 4.5|[!INCLUDE[win8](../../../includes/win8-md.md)]|Unicode 6.0|  
  
 İçinde [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], dize karşılaştırma ve sıralama işletim sistemine bağlıdır. [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Üzerinde çalışan [!INCLUDE[win7](../../../includes/win7-md.md)] Unicode 5.0 uygulamak kendi tablolarından veri alır. [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Üzerinde çalışan [!INCLUDE[win8](../../../includes/win8-md.md)] Unicode 6.0 uygulayan işletim sistemi tablolarından veri alır. Kültüre duyarlı sıralanmış veri seri hale, kullanabileceğiniz <xref:System.Globalization.SortVersion> böylece işletim sisteminin sıralama düzenini ve .NET Framework ile tutarlı sıralanacak serileştirilmiş verilerinizi gerektiği zaman belirlemek için sınıf. Bir örnek için bkz: <xref:System.Globalization.SortVersion> sınıfı konu.  
  
 Uygulamanızı dize verilerini kapsamlı kültüre özgü tür gerçekleştirirse, çalışabilirsiniz <xref:System.Globalization.SortKey> dizeleri karşılaştırmak için sınıf. Sıralama anahtarı kültüre özgü sıralama ağırlıkları alfabetik dahil olmak üzere, durum ve belirli bir dizenin Aksan ağırlıkları yansıtır. Sıralama anahtarları kullanarak karşılaştırmaları ikili olduğundan, bunlar kullanan karşılaştırmaları hızlı bir <xref:System.Globalization.CompareInfo> örtük veya açık olarak nesne. Dizeye geçirerek belirli bir dizeyi kültüre özgü sıralama anahtarı oluşturma <xref:System.Globalization.CompareInfo.GetSortKey%2A?displayProperty=nameWithType> yöntemi.  
  
 Aşağıdaki örnek önceki örneğe benzer. Ancak, çağırmak yerine <xref:System.Array.Sort%28System.Array%29?displayProperty=nameWithType> örtük olarak çağırır yöntemi <xref:System.Globalization.CompareInfo.Compare%2A?displayProperty=nameWithType> yöntemi, tanımladığı bir <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> oluşturur ve geçirir sıralama anahtarları karşılaştırır uygulama <xref:System.Array.Sort%60%601%28%60%600%5B%5D%2CSystem.Collections.Generic.IComparer%7B%60%600%7D%29?displayProperty=nameWithType> yöntemi.  
  
 [!code-csharp[Conceptual.Globalization#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/sortkey1.cs#15)]
 [!code-vb[Conceptual.Globalization#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/sortkey1.vb#15)]  
  
<a name="Strings_Concat"></a>   
### <a name="avoid-string-concatenation"></a>Dize Bitiştirmeden Kaçınma  
 Mümkünse, birleştirilmiş tümcecikleri gelen çalışma zamanında oluşturulan bileşik dizeleri kullanmaktan kaçının. Bileşik dizeleri yerelleştirme zor olduğu bunlar genellikle diğer yerelleştirilmiş dillere uygulanmaz uygulamanın özgün dil dilbilgisi bir sırada varsayalım.  
  
<a name="DatesAndTimes"></a>   
## <a name="handling-dates-and-times"></a>Tarih ve Saatleri İşleme  
 Nasıl tarih işlemek ve saat değerleri olup bunlar kullanıcı arabiriminde görüntülenir veya kalıcı üzerinde bağlıdır. Bu bölümde her iki kullanımları inceler. Ayrıca, nasıl aritmetik işlemler ve saat dilimi farkları tarih ve saatlerle çalışırken işleyebilir anlatılmaktadır.  
  
<a name="DatesAndTimes_Display"></a>   
### <a name="displaying-dates-and-times"></a>Tarihleri ve Saatleri Görüntüleme  
 Genellikle, tarihler ve saatler kullanıcı arabiriminde görüntülendiğinde, tarafından tanımlanan kullanıcının kültür biçimlendirme kuralları kullanması gereken <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> özelliğini kullanarak ve <xref:System.Globalization.DateTimeFormatInfo> tarafından döndürülen nesne `CultureInfo.CurrentCulture.DateTimeFormat` özelliği. Bu yöntemlerden birini kullanarak bir tarih biçiminde geçerli kültür biçimlendirme kuralları otomatik olarak kullanılacaktır:  
  
-   Parametresiz <xref:System.DateTime.ToString?displayProperty=nameWithType> yöntemi  
  
-   <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> Bir biçim dizesi içeren yöntemi  
  
-   Parametresiz <xref:System.DateTimeOffset.ToString?displayProperty=nameWithType> yöntemi  
  
-   <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType>, Bir biçim dizesi içerir  
  
-   [Bileşik biçimlendirme](../../../docs/standard/base-types/composite-formatting.md) tarihlerle kullanıldığında özelliği  
  
 Aşağıdaki örnekte, iki kez Ekim 11, 2012 için sunrise ve gün batımı verilerini görüntüler. Önce geçerli kültürü Hırvatça (Hırvatistan) ve ardından İngilizce (Türkiye) ayarlar. Her durumda, bu kültür için uygun olan biçimde tarihler ve saatler görüntülenir.  
  
 [!code-csharp[Conceptual.Globalization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates1.cs#2)]
 [!code-vb[Conceptual.Globalization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates1.vb#2)]  
  
<a name="DatesAndTimes_Persist"></a>   
### <a name="persisting-dates-and-times"></a>Kalıcı Tarihler ve Saatler  
 Hiçbir zaman kültür göre değişebilir bir biçimde tarih ve saat verilerini kalıcı. Bozuk veri veya bir çalışma zamanı özel sonuçları ortak bir programlama hatası budur. Aşağıdaki örnekte iki tarih, 9 Ocak 2013 ile 18 Ağustos 2013 İngilizce (ABD) kültür biçimlendirme kuralları kullanarak dizeleri olarak serileştirir. Verileri alınır ve İngilizce (ABD) kültür kurallarını kullanarak ayrıştırılır, başarıyla geri yüklendi. Ancak, alınır ve İngilizce (Birleşik Krallık) kültür kurallarını kullanarak ayrıştırılır, ilk tarih yanlış 1 Eylül yorumlanır ve ikinci Gregoryen takvim 6 ay olmadığından ayrıştırmak başarısız olur.  
  
 [!code-csharp[Conceptual.Globalization#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates2.cs#3)]
 [!code-vb[Conceptual.Globalization#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates2.vb#3)]  
  
 Bu sorunu herhangi üç şekilde önleyebilirsiniz:  
  
-   Tarih ve saat ikili biçimi yerine bir dize olarak serileştirir.  
  
-   Kaydet ve kullanıcının kültür bakılmaksızın aynı olacak bir özel biçim dizesi kullanarak tarih ve saat dize gösterimini ayrıştırılamadı.  
  
-   Dize sabit kültür biçimlendirme kuralları kullanarak kaydedin.  
  
 Aşağıdaki örnek, son yaklaşım gösterilmektedir. Statik tarafından döndürülen sabit kültür biçimlendirme kuralları kullanan <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> özelliği.  
  
 [!code-csharp[Conceptual.Globalization#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates3.cs#4)]
 [!code-vb[Conceptual.Globalization#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates3.vb#4)]  
  
<a name="DatesAndTimes_TimeZones"></a>   
### <a name="serialization-and-time-zone-awareness"></a>Seri Hale Getirme ve Saat Dilimini Tanıma  
 Tarih ve saat değeri bir genel süreden arasında birden çok yorumlar olabilir ("depoları 2 Ocak 2013'te 9: 00'da zaman içinde belirli bir süre için Aç") ("Doğum Tarihi: 2 Ocak 2013 6:32: 00'da"). Zaman içinde belirli bir süre bir saat değeri temsil eder ve seri hale getirilmiş bir değeri geri yüklemek, kullanıcının coğrafi konum veya saat dilimi bağımsız olarak zaman içinde aynı anda temsil ettiğini emin olmalısınız.  
  
 Aşağıdaki örnekte bu sorun gösterilmektedir. Bir dize olarak üç tek bir yerel tarih ve saat değeri kaydeder [standart biçimlerini](../../../docs/standard/base-types/standard-date-and-time-format-strings.md) (genel tarih uzun zaman sıralanabilir tarih/saat, "s" için "G" ve "o" gidiş için tarih/saat) gibi ikili biçimde yanı.  
  
 [!code-csharp[Conceptual.Globalization#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates4.cs#10)]
 [!code-vb[Conceptual.Globalization#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates4.vb#10)]  
  
 Doğru bir şekilde verileri bir sistemde sıralandığı managementpack sistem aynı saat diliminde geri yüklendiğinde seri durumdan çıkarılmış tarih ve saat değerleri özgün değeri çıktı gösterildiği gibi yansıtmak:  
  
```  
'3/30/2013 6:00:00 PM' --> 3/30/2013 6:00:00 PM Unspecified  
'2013-03-30T18:00:00' --> 3/30/2013 6:00:00 PM Unspecified  
'2013-03-30T18:00:00.0000000-07:00' --> 3/30/2013 6:00:00 PM Local  
  
3/30/2013 6:00:00 PM Local  
```  
  
 Ancak, farklı bir zaman diliminde bir sistemde veri geri yüklerseniz, "o" (gidiş) standart biçim dizesi ile biçimlendirilmiş yalnızca tarih ve saat değeri saat dilimi bilgilerini korur ve bu nedenle aynı anlık zamanında temsil eder. Tarih ve saat verilerini Romantizm standart saat dilimi sisteminde geri yüklendiğinde çıktısı şöyledir:  
  
```  
'3/30/2013 6:00:00 PM' --> 3/30/2013 6:00:00 PM Unspecified  
'2013-03-30T18:00:00' --> 3/30/2013 6:00:00 PM Unspecified  
'2013-03-30T18:00:00.0000000-07:00' --> 3/31/2013 3:00:00 AM Local  
  
3/30/2013 6:00:00 PM Local  
```  
  
 Doğru bir şekilde tek biraz verileri seri durumdan olan sistem saat dilimini bakılmaksızın süreyi temsil eden bir tarih ve saat değeri yansıtmak için aşağıdakilerden birini yapabilirsiniz:  
  
-   Değer, "o" (gidiş dönüş) standart biçim dizesi kullanarak bir dize olarak kaydedin. Ardından, hedef sistemde seri durumdan çıkarır.  
  
-   UTC'ye dönüştürmek ve "r" (RFC1123) standart biçim dizesi kullanarak bir dize olarak kaydedin. Hedef sistemde seri durumdan sonra yerel saate dönüştürme.  
  
-   UTC'ye dönüştürmek ve "u" (Evrensel sıralanabilir) standart biçim dizesi kullanarak bir dize olarak kaydedin. Hedef sistemde seri durumdan sonra yerel saate dönüştürme.  
  
-   UTC'ye dönüştürmek ve ikili dosya biçiminde kaydedin. Hedef sistemde seri durumdan sonra yerel saate dönüştürme.  
  
 Aşağıdaki örnek, her bir teknik gösterilmektedir.  
  
 [!code-csharp[Conceptual.Globalization#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates8.cs#11)]
 [!code-vb[Conceptual.Globalization#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates8.vb#11)]  
  
 Veri Pasifik Standart saat dilimi sisteminde serileştirilmiş ve Romantizm standart saat dilimi sisteminde seri, örnek aşağıdaki çıkış görüntüler:  
  
```  
'2013-03-30T18:00:00.0000000-07:00' --> 3/31/2013 3:00:00 AM Local  
'Sun, 31 Mar 2013 01:00:00 GMT' --> 3/31/2013 3:00:00 AM Local  
'2013-03-31 01:00:00Z' --> 3/31/2013 3:00:00 AM Local  
  
3/31/2013 3:00:00 AM Local  
```  
  
 Daha fazla bilgi için bkz: [dönüştürme saatleri arasında saat dilimleri](../../../docs/standard/datetime/converting-between-time-zones.md).  
  
<a name="DatesAndTimes_Arithmetic"></a>   
### <a name="performing-date-and-time-arithmetic"></a>Tarih ve Saat Aritmetiğini Gerçekleştirme  
 Hem <xref:System.DateTime> ve <xref:System.DateTimeOffset> türlerini destekleyen aritmetik işlemler. İki tarih değerler arasındaki farkın hesaplayabilirsiniz ya da ekleyebilir veya belirli zaman aralıkları için veya bir tarih değeri çıkarır. Ancak, tarih ve saat değerleri aritmetik işlemler saat dilimleri ve saat dilimi ayarlama kuralları dikkate değil. Bu nedenle, tarih ve saat aritmetiği dakika zaman içinde temsil eden değerleri tutarsız sonuçlar döndürebilir.  
  
 Örneğin, 10 Mart 2013 yıl olduğundan Mart İkinci Pazar Pasifik Yaz Saati Pasifik Standart Saati geçiş oluşur. Aşağıdaki örnek olarak, saat ve hesaplaması, olduğunu gösterir 48 saat 9 Mart 2013'ün sonra 10: 30'da Pasifik Standart saat diliminde bir sistemde sonucu, 11 Mart 2013'ün en 10: 30'da, müdahalede bulunan saat ayarı dikkate almaz.  
  
 [!code-csharp[Conceptual.Globalization#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates5.cs#8)]
 [!code-vb[Conceptual.Globalization#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates5.vb#8)]  
  
 Tarih ve saat değerleri bir aritmetik işlemi doğru sonuçlar yapılmadığından emin olmak için şu adımları izleyin:  
  
1.  Kaynak saat diliminde süresi için UTC dönüştürün.  
  
2.  Aritmetik işlemi gerçekleştirin.  
  
3.  Sonuç bir tarih ve saat değeri ise, UTC saat kaynak saat diliminde dönüştürülemiyor.  
  
 Doğru 48 saat 10: 30'da 9 Mart 2013'e eklemek için bu üç adımı aşağıdaki aşağıdaki örnek önceki örneğe benzerdir  
  
 [!code-csharp[Conceptual.Globalization#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates6.cs#9)]
 [!code-vb[Conceptual.Globalization#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates6.vb#9)]  
  
 Daha fazla bilgi için bkz: [tarih ve saatlerle aritmetik işlemler gerçekleştirme](../../../docs/standard/datetime/performing-arithmetic-operations.md).  
  
### <a name="using-culture-sensitive-names-for-date-elements"></a>Veri Öğeleri için Kültüre Duyarlı Adlar Kullanma  
 Uygulamanızı ayın adını veya haftanın günü görüntülemeniz gerekebilir. Bunu yapmak için aşağıdaki gibi ortak koddur.  
  
 [!code-csharp[Conceptual.Globalization#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/monthname1.cs#19)]
 [!code-vb[Conceptual.Globalization#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/monthname1.vb#19)]  
  
 Ancak, bu kodu her zaman İngilizce haftanın günlerini adlarını döndürür. Ayın adını ayıklar kodu daha esnek olmayan görülür. Sıklıkla, on iki ay Takvim belirli bir dilde ay adlarıyla varsayar.  
  
 Kullanarak [özel tarih ve saat biçim dizeleri](../../../docs/standard/base-types/custom-date-and-time-format-strings.md) veya özelliklerini <xref:System.Globalization.DateTimeFormatInfo> nesnesi, aşağıdaki örnekte gösterildiği gibi haftanın ya da kullanıcının kültürü aydaki gün adlarını yansıtmak dizeleri ayıklamak kolay olduğu. Geçerli kültür Fransızca (Fransa) değiştirir ve haftanın günü ve ayın adını 1 Temmuz 2013'ün adını görüntüler.  
  
 [!code-csharp[Conceptual.Globalization#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/monthname2.cs#20)]
 [!code-vb[Conceptual.Globalization#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/monthname2.vb#20)]  
  
<a name="Numbers"></a>   
## <a name="handling-numeric-values"></a>Sayısal Değerleri İşleme  
 Sayıların işleme olup bunlar kullanıcı arabiriminde görüntülenir veya kalıcı üzerinde bağlıdır. Bu bölümde her iki kullanımları inceler.  
  
> [!NOTE]
>  .NET Framework ayrıştırma ve işlemleri biçimlendirme, yalnızca temel Latin karakterler 0-9 arası tanıdığı (U + 0039 aracılığıyla, U + 0030) Sayısal basamaklar olarak.  
  
<a name="Numbers_Display"></a>   
### <a name="displaying-numeric-values"></a>Sayısal Değerleri Görüntüleme  
 Genellikle, sayılar kullanıcı arabiriminde görüntülendiğinde tarafından tanımlanan kullanıcının kültür biçimlendirme kuralları kullanması gereken <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> özelliğini kullanarak ve <xref:System.Globalization.NumberFormatInfo> tarafından döndürülen nesne `CultureInfo.CurrentCulture.NumberFormat` özelliği. Aşağıdaki yöntemlerden birini kullanarak bir tarih biçiminde geçerli kültür biçimlendirme kuralları otomatik olarak kullanılacaktır:  
  
-   Parametresiz `ToString` herhangi bir sayısal türde yöntemi  
  
-   `ToString(String)` Bir biçim dizesi bağımsız değişken olarak içeren tüm sayısal türü yöntemi  
  
-   [Bileşik biçimlendirme](../../../docs/standard/base-types/composite-formatting.md) sayısal değerleri ile kullanıldığında özelliği  
  
 Aşağıdaki örnek, Paris, Fransa aylık Ortalama sıcaklık görüntüler. İlk veri görüntülemeden önce geçerli kültürü Fransızca (Fransa) ayarlar ve İngilizce (ABD) ayarlar. Her durumda, bu kültür için uygun olan biçimde etme ve ay adları görüntülenir. İki kültürler sıcaklık değeri farklı ondalık ayırıcı kullandığını unutmayın. Ayrıca, örneğin "Aaaa" özel tarih ve saat biçim dizesi tam ay adını görüntülemek için kullandığı ve uygun miktarını sonuç dizesinde ay adı için en uzun ayadıuzunluğubelirleyerekayırdığındaneminunutmayın<xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A?displayProperty=nameWithType></C0>dizi.  
  
 [!code-csharp[Conceptual.Globalization#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/numbers1.cs#5)]
 [!code-vb[Conceptual.Globalization#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/numbers1.vb#5)]  
  
<a name="Numbers_Persist"></a>   
### <a name="persisting-numeric-values"></a>Kalıcı Sayısal Değerler  
 Kültüre özgü biçimde sayısal veri hiçbir zaman kalıcı olması. Bozuk veri veya bir çalışma zamanı özel sonuçları ortak bir programlama hatası budur. Aşağıdaki örnek, on rastgele kayan nokta sayıları oluşturur ve ardından bunları dize olarak İngilizce (ABD) kültür biçimlendirme kuralları kullanarak serileştirir. Verileri alınır ve İngilizce (ABD) kültür kurallarını kullanarak ayrıştırılır, başarıyla geri yüklendi. Alınan ve Fransızca (Fransa) kültür kurallarını kullanarak Ayrıştırılan kültürler farklı ondalık ayırıcı kullandığından ancak sayıları hiçbiri ayrıştırılabilir.  
  
 [!code-csharp[Conceptual.Globalization#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/numbers2.cs#6)]
 [!code-vb[Conceptual.Globalization#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/numbers2.vb#6)]  
  
 Bu sorunu önlemek için bu teknikler birini kullanabilirsiniz:  
  
-   Kaydet ve kullanıcının kültür bakılmaksızın aynı olacak bir özel biçim dizesi kullanarak numarası dize gösterimini ayrıştırılamadı.  
  
-   Sabit kültür biçimlendirme kuralları tarafından döndürülen kullanarak bir dize olarak numarası Kaydet <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> özelliği.  
  
-   Dize biçimi yerine ikili sayısında serileştirir.  
  
 Aşağıdaki örnek, son yaklaşım gösterilmektedir. Dizi serileştiren <xref:System.Double> değerleri, seri durumdan çıkarır ve İngilizce (ABD) ve Fransızca (Fransa) kültür biçimlendirme kuralları kullanarak görüntüler.  
  
 [!code-csharp[Conceptual.Globalization#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/numbers3.cs#7)]
 [!code-vb[Conceptual.Globalization#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/numbers3.vb#7)]  
  
 Para birimi değerleri seri hale getirme özel bir durumdur. Para birimi değeri para birimi ifade edilir biriminde bağımlı olduğundan; bağımsız bir sayısal değer işlemek için az mantıklıdır. Para birimi değeri, para birimi simgesini içeren biçimlendirilmiş bir dize kaydederseniz, ancak bu, varsayılan kültürü farklı para birimi simgesini, aşağıdaki örnekte gösterildiği gibi kullanan bir sistemde serisi kaldırılamıyor.  
  
 [!code-csharp[Conceptual.Globalization#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/currency1.cs#16)]
 [!code-vb[Conceptual.Globalization#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/currency1.vb#16)]  
  
 Bunun yerine, böylece değer ve para birimi simgesini bağımsız olarak geçerli kültür çıkarılabiliyorsa kültür adı gibi bazı kültürel bilgilerle birlikte sayısal değer seri hale. Aşağıdaki örnek tanımlayarak yapan bir `CurrencyValue` iki üye yapısıyla: <xref:System.Decimal> değer ve değeri ait olduğu kültür adı.  
  
 [!code-csharp[Conceptual.Globalization#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/currency2.cs#17)]
 [!code-vb[Conceptual.Globalization#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/currency2.vb#17)]  
  
<a name="Cultures"></a>   
## <a name="working-with-culture-specific-settings"></a>Kültüre Özgü Ayarlarla Çalışma  
 .NET Framework'teki <xref:System.Globalization.CultureInfo> belirli kültür veya bölge sınıfı temsil eder. Özelliklerinden bazıları bir kültür bazı yönlerinin hakkındaki belirli bilgileri sağlayan nesneleri döndürün:  
  
-   <xref:System.Globalization.CultureInfo.CompareInfo%2A?displayProperty=nameWithType> Özelliği döndürür bir <xref:System.Globalization.CompareInfo> kültürü karşılaştırır ve siparişleri dizeleri hakkında bilgi içeren nesne.  
  
-   <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> Özelliği döndürür bir <xref:System.Globalization.DateTimeFormatInfo> tarih ve saat verilerini biçimlendirmede kullanılan kültüre özgü bilgileri sağlayan nesne.  
  
-   <xref:System.Globalization.CultureInfo.NumberFormat%2A?displayProperty=nameWithType> Özelliği döndürür bir <xref:System.Globalization.NumberFormatInfo> sayısal veri biçimlendirmede kullanılan kültüre özgü bilgileri sağlayan nesne.  
  
-   <xref:System.Globalization.CultureInfo.TextInfo%2A?displayProperty=nameWithType> Özelliği döndürür bir <xref:System.Globalization.TextInfo> kültürü hakkında bilgi sağlayan nesne sistem yazma.  
  
 Genel olarak, tüm özelliklerinin değerlerini özel yapmayın <xref:System.Globalization.CultureInfo> özellikler ve ilgili nesneleri. Bunun yerine, kültüre özgü veri değiştirilebilir olduğu gibi Bu nedenlerden dolayı görüntülemeniz gerekir:  
  
-   Tek tek özellik değerlerini değiştirme ve düzeltme zaman içerisinde, veri düzeltilene, daha iyi veriler kullanılabilir duruma gelir veya kültüre özgü kuralları değiştirme gibi tabidir.  
  
-   Tek tek özellik değerleri, .NET Framework veya işletim sistemi sürümleri sürümleri arasında farklılık gösterebilir.  
  
-   .NET Framework değiştirme kültürler destekler. Var olan standart kültürler tamamlayan ya da var olan bir standart kültür tamamen değiştirir yeni bir özel kültür tanımlamanızı mümkün kılar.  
  
-   Kullanıcı kültüre özgü ayarları kullanarak özelleştirebileceğiniz **bölge ve dil** Denetim Masası'ndaki uygulama. Ne zaman örneği bir <xref:System.Globalization.CultureInfo> nesne çağırarak, bu kullanıcı özelleştirmeleri yansıtır olup olmadığını belirleyebilir <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> Oluşturucusu. Böylece kullanıcı çözemiyorsa beklediği biçiminde verilerle sunulan genellikle son kullanıcı uygulamaları için kullanıcı tercihlerini dikkate.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Genelleştirme ve Yerelleştirme](../../../docs/standard/globalization-localization/index.md)  
 [Dizeleri Kullanmak için En İyi Uygulamalar](../../../docs/standard/base-types/best-practices-strings.md)
