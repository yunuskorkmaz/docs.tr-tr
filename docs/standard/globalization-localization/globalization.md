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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 84e44f0112a5d1b5fd38daf488d865f6e228f82b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54713947"
---
# <a name="globalization"></a>Genelleştirme
Genelleştirme, tasarlamaya ve geliştirmeye yönelik birden çok kültürde yerelleştirilmiş arabirimleri ve bölgesel verileri destekleyen dünya çapında kullanılmaya hazır uygulamasını içerir. Tasarım aşamasına başlamadan önce hangi kültürleri uygulamanızı destekleyeceğini belirlemeniz gerekir. Bir tek bir kültür veya bölgeyi varsayılan olarak bir uygulama hedeflese de, tasarlayın ve böylece diğer kültür ya da bölgelerdeki kullanıcılara kolayca genişletilebilir yazabilirsiniz.  
  
 Geliştiriciler olarak, tüm kullanıcı arabirimleri kültürlerimiz tarafından biçimlendirilmiş veriler hakkında varsayımlar sahibiz. Örneğin, bir İngilizce konuşan bir geliştirici için Amerika Birleşik Devletleri, tarih ve saat verileri biçiminde bir dize olarak seri hale getirme `MM/dd/yyyy hh:mm:ss` son derece makuldür. Ancak, bu dize bir sistem üzerinde farklı bir kültür seri durumdan çıkarılırken kaldırıldığında bir <xref:System.FormatException> özel durumu veya yanlış veriler üretilebilir. Genelleştirme, bu tür kültüre özgü varsayımları tanımlamamıza ve bunların uygulama tasarım veya kod etkilemez emin olmak için bize sağlar.  
  
 Aşağıdaki bölümlerde bazı dikkate almanız gereken ana sorunları ve, dizeleri, tarih ve saat değerleri ve genelleştirilmiş bir uygulamada sayısal değerleri işlerken uygulayabileceğiniz en iyi uygulamalar açıklanmaktadır.  
  
-   [Dizeleri işleme](../../../docs/standard/globalization-localization/globalization.md#HandlingStrings)  
  
    -   [Dahili olarak Unicode kullanma](../../../docs/standard/globalization-localization/globalization.md#Strings_Unicode)  
  
    -   [Kaynak dosyaları kullan](../../../docs/standard/globalization-localization/globalization.md#Strings_Resources)  
  
    -   [Dizeleri arama ve karşılaştırma ](../../../docs/standard/globalization-localization/globalization.md#Strings_Searching)  
  
    -   [Eşitlik için sınama](../../../docs/standard/globalization-localization/globalization.md#Strings_Equality)  
  
    -   [Dizeleri sıralama ve düzenleme ](../../../docs/standard/globalization-localization/globalization.md#Strings_Ordering)  
  
    -   [Dize Bitiştirmeden kaçınma](../../../docs/standard/globalization-localization/globalization.md#Strings_Concat)  
  
-   [Tarih ve saatleri işleme](../../../docs/standard/globalization-localization/globalization.md#DatesAndTimes)  
  
    -   [Kalıcı tarihler ve saatler](../../../docs/standard/globalization-localization/globalization.md#DatesAndTimes_Persist)  
  
    -   [Tarihleri ve saatleri görüntüleme](../../../docs/standard/globalization-localization/globalization.md#DatesAndTimes_Display)  
  
    -   [Seri hale getirme ve saat dilimini tanıma](../../../docs/standard/globalization-localization/globalization.md#DatesAndTimes_TimeZones)  
  
    -   [Tarih ve saat aritmetiğini gerçekleştirme](../../../docs/standard/globalization-localization/globalization.md#DatesAndTimes_Arithmetic)  
  
-   [Sayısal değerleri işleme](../../../docs/standard/globalization-localization/globalization.md#Numbers)  
  
    -   [Sayısal değerleri görüntüleme](../../../docs/standard/globalization-localization/globalization.md#Numbers_Display)  
  
    -   [Kalıcı sayısal değerler](../../../docs/standard/globalization-localization/globalization.md#Numbers_Persist)  
  
-   [Kültüre özgü ayarlarla çalışma](../../../docs/standard/globalization-localization/globalization.md#Cultures)  
  
<a name="HandlingStrings"></a>   
## <a name="handling-strings"></a>Dizeleri İşleme  
 Her kültür veya bölgeyi farklı karakterler ve karakter kümeleri kullandığı ve bunları farklı sıraladığından karakterlerin ve dizelerin işlenmesi bir işlenmesi genelleştirmede odaklanılan, olmasıdır. Bu bölüm Global uygulamalarda dizelerin kullanmaya yönelik öneriler sağlar.  
  
<a name="Strings_Unicode"></a>   
### <a name="use-unicode-internally"></a>Dahili Olarak Unicode Kullanma  
 Varsayılan olarak, .NET Framework, Unicode dizelerini kullanır. Bir Unicode dizesi sıfır, bir veya daha fazla oluşur <xref:System.Char> her biri bir UTF-16 kod birimini temsil eden nesneleri. Dünyada kullanılan kümesindeki her karakteri neredeyse her karakter için bir Unicode gösterimi vardır.  
  
 Birçok uygulama ve işletim sistemleri, Windows işletim sistemi dahil olmak üzere kod sayfalarını karakter kümelerini göstermek için de kullanabilirsiniz. Kod sayfaları genellikle 0x00 ila 0x7F standart ASCII değerlerini içerir ve diğer karakterleri, 0x80 ila 0xFF kalan değerlere eşleyin. 0xFF üzerinden 0x80'den alınan değerlerin yorumu belirli kod sayfasına bağlıdır. Bu nedenle, kod sayfaları mümkünse genelleştirilmiş uygulamada kullanmaktan kaçınmanız gerekir.  
  
 Aşağıdaki örnek, bir sistemde varsayılan kod sayfası üzerinde verilerin kaydedildiği kod sayfasından farklı olduğunda, kod sayfası verilerini yorumlamanın tehlikelerini göstermektedir. (Bu senaryonun benzetimini yapmak için örnek açıkça farklı kod sayfalarını belirtir.) İlk olarak, örnek Yunan alfabesinin büyük harf karakterlerden oluşan bir dizi tanımlar. Bu kod sayfası 737 (MS-DOS Yunanca olarak da bilinir) kullanılarak Bayt dizisine kodlar ve bayt dizisini bir dosyaya kaydeder. Dosya alınırsa ve kod sayfası 737 kullanılarak bayt dizisinin kodu, özgün karakterler geri yüklenir. Ancak, dosya alınırsa ve kod sayfası 1252 (veya Latin alfabesindeki karakterleri temsil eden Windows-1252) kullanılarak bayt dizisinin kodu, özgün karakterler kaybolur.  
  
 [!code-csharp[Conceptual.Globalization#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/codepages1.cs#1)]
 [!code-vb[Conceptual.Globalization#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/codepages1.vb#1)]  
  
 Unicode kullanımı, aynı kod birimlerinin her zaman aynı karakterle eşlenmesini ve aynı karakterlerin her zaman aynı bayt dizileri ile eşlenmesini sağlar.  
  
<a name="Strings_Resources"></a>   
### <a name="use-resource-files"></a>Kaynak Dosyalarını Kullanma  
 Bir tek bir kültür veya bölgeyi hedefleyen bir uygulama geliştiriyor olsanız bile, dizeleri ve kullanıcı arabiriminde görüntülenen diğer kaynakları depolamak için kaynak dosyalarını kullanmanız gerekir. Ayrıca doğrudan kodunuza bunları asla eklemeniz gerekir. Kaynak dosyalarını kullanmanın birçok avantajı vardır:  
  
-   Tüm dizeler tek bir konumda olan. Belirli bir dil veya kültür için değişiklik yapılacak dizeleri bulmak için kaynak kodunuz genelinde arama yapmak zorunda kalmazsınız.  
  
-   Dizeleri çoğaltmaya gerek yoktur. Kaynak dosyaları genellikle kullanmayan geliştiriciler, birden çok kaynak kodu dosyasında aynı dize tanımlayın. Bu çoğaltma olasılığını artırır veya bir dize değiştirildiğinde daha fazla göz ardı edilmesi.  
  
-   Bunlar kolayca alınabilmesi bunları bir ayrı bağımsız dosyada depolamak yerine kaynak dosyasında, görüntü veya ikili veri gibi dize olmayan kaynaklar ekleyebilirsiniz.  
  
 Yerelleştirilmiş bir uygulama oluşturuyorsanız kaynak dosyaları kullanmanın belirli avantajları vardır. Kaynakları uydu derlemelerinde dağıttığınızda, ortak dil çalışma zamanı tarafından tanımlandığı gibi kullanıcının geçerli kullanıcı Arabirimi kültürüne göre kültüre uygun bir kaynağı otomatik olarak seçer. <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> özelliği. Uygun bir kültüre özgü kaynak sağladığınız ve doğru örnekleyin sürece bir <xref:System.Resources.ResourceManager> nesne veya türü kesin belirlenmiş kaynak sınıfı kullanın, çalışma zamanı uygun kaynakların alınmasına ilişkin ayrıntılar işler.  
  
 Kaynak dosyaları oluşturma hakkında daha fazla bilgi için bkz. [Creating Resource Files](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md). Oluşturma ve uydu derlemelerini dağıtma hakkında daha fazla bilgi için bkz: [uydu derlemeleri oluşturma](../../../docs/framework/resources/creating-satellite-assemblies-for-desktop-apps.md) ve [kaynakları paketleme ve dağıtma](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md).  
  
<a name="Strings_Searching"></a>   
### <a name="searching-and-comparing-strings"></a>Dizeleri Arama ve Karşılaştırma  
 Mümkün olduğunda, dizeler, bunları tek tek karakter dizisi olarak işlemek yerine bütün dizeler olarak işlemelidir. Bu sıralama veya arama sorunları önlemek için alt dizeler, birleşik karakterleri ayrıştırmayla ilişkili olduğunda özellikle önemlidir.  
  
> [!TIP]
>  Kullanabileceğiniz <xref:System.Globalization.StringInfo> bir dizedeki karakterlerin tek tek yerine metin öğeleriyle çalışmak için sınıf.  
  
 Dize aramalarında ve karşılaştırmalarında, sıkça dize karakter, her biri tarafından temsil edilen bir koleksiyon olarak değerlendirilecek olan bir <xref:System.Char> nesne. Tek bir karakter bir, iki veya daha fazla tarafından aslında oluşturulabilir <xref:System.Char> nesneleri. Bu tür karakterler en sık dizelerden karakterleri Unicode temel Latin karakter aralığı (U + 0021 ile U + 007E) dışında olan harfler oluşan kültürler bulunur. Aşağıdaki örnek, bir dizede ile LATIN CAPITAL LETTER A GRAVE karakterinin (U + 00 C 0) dizinini bulmaya çalışır. Ancak, bu karakter iki farklı şekilde temsil edilebilir: tek bir kod birimi (U + 00C 0) olarak veya bileşik bir karakter (iki kod birimi: U+ 0021 ve U + 007E). Bu durumda, karakter dize örneğinde iki tarafından temsil edilen <xref:System.Char> nesneleri, U + 0021 ve U + 007E. Örnek kod çağrıları <xref:System.String.IndexOf%28System.Char%29?displayProperty=nameWithType> ve <xref:System.String.IndexOf%28System.String%29?displayProperty=nameWithType> dize örneğinde, ancak bunlar bu karakterin konumunu bulmak için aşırı yüklemeler farklı sonuçlar döndürür. İlk yöntem çağrısında sahip bir <xref:System.Char> bağımsız değişkeni; sıralı bir karşılaştırma yapar ve bu nedenle bir eşleşme bulamaz. İkinci çağrıda sahip bir <xref:System.String> bağımsız değişkeni; bir kültüre duyarlı karşılaştırma yapar ve bu nedenle eşleşme bulur.  
  
 [!code-csharp[Conceptual.Globalization#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/search1.cs#18)]
 [!code-vb[Conceptual.Globalization#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/search1.vb#18)]  
  
 Bazı belirsizliklerden (çağrı farklı sonuçlar döndüren bir yöntemin iki benzer aşırı yüküne) Bu örnek içeren bir aşırı yükü çağırarak kaçının bir <xref:System.StringComparison> parametresi gibi <xref:System.String.IndexOf%28System.String%2CSystem.StringComparison%29?displayProperty=nameWithType> veya <xref:System.String.LastIndexOf%28System.String%2CSystem.StringComparison%29?displayProperty=nameWithType> yöntemi.  
  
 Ancak aramalar her zaman kültüre duyarlı değildir. Aramanın amacı, bir güvenlik kararı vermek veya izin vermek veya bazı kaynaklara erişim engellemek için ise, karşılaştırma sonraki bölümde açıklandığı gibi sıralı olmalıdır.  
  
<a name="Strings_Equality"></a>   
### <a name="testing-strings-for-equality"></a>Eşitlik için Sınama Ayarları  
 Sıralama düzeninde karşılaştırmasına belirleme yerine eşitlik kullanmak için iki dizeyi test etmek isterseniz <xref:System.String.Equals%2A?displayProperty=nameWithType> yöntemi gibi dize karşılaştırma yöntemi yerine <xref:System.String.Compare%2A?displayProperty=nameWithType> veya <xref:System.Globalization.CompareInfo.Compare%2A?displayProperty=nameWithType>.  
  
 Eşitlik karşılaştırmaları genellikle koşullu olarak bazı kaynaklara erişmek için gerçekleştirilir. Örneğin, bir parolayı doğrulamak veya bir dosyanın var olduğunu doğrulamak üzere eşitlik için bir karşılaştırma gerçekleştirebilirsiniz. Bu tür dilsel olmayan karşılaştırmalar her zaman yerine sıralı kültüre duyarlı olmalıdır. Genel olarak, örnek çağırmalıdır <xref:System.String.Equals%28System.String%2CSystem.StringComparison%29?displayProperty=nameWithType> yöntemi veya statik <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> değeriyle yöntemi <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> parolalar ve değerini gibi dizeler için <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> dosya adları ya da URI gibi dizeler için.  
  
 Eşitlik karşılaştırmaları bazen ilgili aramalar veya alt dize karşılaştırmaları yapılan çağrılar yerine <xref:System.String.Equals%2A?displayProperty=nameWithType> yöntemi. Bazı durumlarda, alt dizenin başka bir dizeye eşit olup olmadığını belirlemek için alt dize aramayı kullanabilirsiniz. Bu karşılaştırmanın amacı dile ait olmayan ise, arama da yerine sıralı kültüre duyarlı olmalıdır.  
  
 Aşağıdaki örnek, dilsel olmayan veriler üzerinde bir kültüre duyarlı aramada tehlikesi gösterir. `AccessesFileSystem` Yöntemi, "FILE" alt dizesi ile başlayan bir URI'leri için dosya sistemi erişimini engellemek için tasarlanmıştır. Bunu yapmak için "FILE" dizesiyle URI başlangıcını kültüre duyarlı ve büyük küçük harf duyarsız bir karşılaştırma gerçekleştirir. Dosya sistemine erişen bir URI ile başlayabilirsiniz çünkü "dosya:" veya "dosya:", "i" örtük varsayılır (U + 0069) her zaman "I" küçük harfli eşdeğeri olduğu (U + 0049). Ancak Türkçe ve Azerice, büyük harfli sürümünü içinde "i", "İ" olan (U + 0130). Yasaklanması gerektiğinde bu tutarsızlık nedeniyle, kültüre duyarlı bir karşılaştırma dosya sistemi erişimini sağlar.  
  
 [!code-csharp[Conceptual.Globalization#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/equals1.cs#12)]
 [!code-vb[Conceptual.Globalization#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/equals1.vb#12)]  
  
 Bu durumda, aşağıdaki örnekte gösterildiği gibi yoksayar sıralı karşılaştırma gerçekleştirerek bu sorunu önleyebilirsiniz.  
  
 [!code-csharp[Conceptual.Globalization#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/equals2.cs#13)]
 [!code-vb[Conceptual.Globalization#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/equals2.vb#13)]  
  
<a name="Strings_Ordering"></a>   
### <a name="ordering-and-sorting-strings"></a>Dizeleri Sıralama ve Düzenleme  
 Genellikle, kullanıcı arabiriminde görüntülenecek olan sıralı dizeler kültüre dayalı olarak sıralanmalıdır. Gibi dizeleri sıralayan bir yöntem çağırdığınızda çoğunlukla, bu tür dize karşılaştırmaları örtük olarak .NET Framework tarafından işlenen <xref:System.Array.Sort%2A?displayProperty=nameWithType> veya <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType>. Varsayılan olarak, dizeler, geçerli kültürün sıralama kuralları kullanılarak sıralanır. İngilizce (ABD) kültürü ve İsveç dili (İsveç) kültürü kurallarını kullanarak dize dizisi sıralandığında fark aşağıdaki örnekte gösterilmiştir.  
  
 [!code-csharp[Conceptual.Globalization#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/sort1.cs#14)]
 [!code-vb[Conceptual.Globalization#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/sort1.vb#14)]  
  
 Kültüre duyarlı dize karşılaştırma tarafından tanımlanan <xref:System.Globalization.CompareInfo> her kültürün tarafından döndürülen nesne <xref:System.Globalization.CultureInfo.CompareInfo%2A?displayProperty=nameWithType> özelliği. Kullanan kültüre duyarlı dize karşılaştırmaları <xref:System.String.Compare%2A?displayProperty=nameWithType> yöntemi aşırı ayrıca kullanım <xref:System.Globalization.CompareInfo> nesne.  
  
 .NET Framework, kültüre duyarlı sıralamaları dize veriler üzerinde gerçekleştirmek için tablolar kullanır. Dize normalleştirme ve sıralama ağırlıkları verilerini içeren, bu tabloların içeriği, .NET Framework'ün belirli bir sürümü tarafından uygulanan Unicode standart sürümü tarafından belirlenir. Belirtilen .NET Framework sürümleri tarafından uygulanan Unicode sürümleri aşağıdaki tabloda listelenmiştir. Bu liste desteklenen Unicode sürümleri karakter karşılaştırma ve sıralama yalnızca geçerli olduğunu unutmayın. kategoriye göre Unicode karakter sınıflandırması için uygulanmaz. Daha fazla bilgi için bkz: "Dizeleri ve Unicode standardı" bölümünde <xref:System.String> makalesi.  
  
|.NET Framework sürümü|İşletim sistemi|Unicode sürümü|  
|----------------------------|----------------------|---------------------|  
|.NET Framework 2.0|Tüm işletim sistemleri|Unicode 4.1|  
|.NET Framework 3.0|Tüm işletim sistemleri|Unicode 4.1|  
|.NET Framework 3.5|Tüm işletim sistemleri|Unicode 4.1|  
|.NET Framework 4|Tüm işletim sistemleri|Unicode 5.0|  
|.NET Framework 4.5|[!INCLUDE[win7](../../../includes/win7-md.md)]|Unicode 5.0|  
|.NET Framework 4.5|[!INCLUDE[win8](../../../includes/win8-md.md)]|Unicode 6.0|  
  
 İçinde [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], dize karşılaştırması ve sıralaması işletim sistemine bağlıdır. [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Üzerinde çalışan [!INCLUDE[win7](../../../includes/win7-md.md)] verileri Unicode 5.0 uygulayan kendi tablolarından alır. [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Üzerinde çalışan [!INCLUDE[win8](../../../includes/win8-md.md)] verileri Unicode 6.0 uygulayan işletim sistemi tablolarından alır. Kültüre duyarlı sıralanmış verileri sıralarsanız, kullanabileceğiniz <xref:System.Globalization.SortVersion> serileştirilmiş verilerinizi ne zaman .NET Framework ile işletim sisteminin sıralama düzeniyle tutarlı olması yeniden sırılanacığını saptamak için. Bir örnek için bkz <xref:System.Globalization.SortVersion> sınıf konusuna.  
  
 Uygulamanız dize verileri, kapsamlı kültüre özel sıralarını gerçekleştiriyorsa çalışabilirsiniz <xref:System.Globalization.SortKey> dizeleri karşılaştırmak için sınıf. Bir sıralama anahtarı alfabetik dahil, kültüre özgü sıralama ağırlıklarını, durum ve aksan ağırlıkları da belirli bir dizenin yansıtır. Sıralama anahtarlarını kullanan karşılaştırmalar ikili olduğundan, bunlar kullanan karşılaştırmalardan daha hızlı bir <xref:System.Globalization.CompareInfo> örtük veya açık olarak nesnesi. Dize olarak geçirerek belirli bir dize için kültüre özgü sıralama anahtarı oluşturma <xref:System.Globalization.CompareInfo.GetSortKey%2A?displayProperty=nameWithType> yöntemi.  
  
 Aşağıdaki örnek önceki örneğe benzerdir. Ancak, çağırmak yerine <xref:System.Array.Sort%28System.Array%29?displayProperty=nameWithType> örtük olarak çağırır ve yöntem <xref:System.Globalization.CompareInfo.Compare%2A?displayProperty=nameWithType> yöntemi tanımlar bir <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> başlatan ve geçirir Bu sıralama anahtarlarını karşılaştıran uygulama <xref:System.Array.Sort%60%601%28%60%600%5B%5D%2CSystem.Collections.Generic.IComparer%7B%60%600%7D%29?displayProperty=nameWithType> yöntemi.  
  
 [!code-csharp[Conceptual.Globalization#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/sortkey1.cs#15)]
 [!code-vb[Conceptual.Globalization#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/sortkey1.vb#15)]  
  
<a name="Strings_Concat"></a>   
### <a name="avoid-string-concatenation"></a>Dize Bitiştirmeden Kaçınma  
 Bu tamamen Mümkünse, yan tümcelerden çalışma zamanında oluşturulan bileşik dizeleri kullanmaktan kaçının. Bunlar genellikle sıralamasının diğer yerelleştirilmiş diller için geçerli olmayan uygulamanın orijinal dilinde olduğunu varsaydığından bileşik dizelerin yerelleştirmek zordur.  
  
<a name="DatesAndTimes"></a>   
## <a name="handling-dates-and-times"></a>Tarih ve Saatleri İşleme  
 Nasıl tarih işlemek ve saat değerleri olup bunların kullanıcı arabiriminde görüntülenen veya kalıcı üzerinde bağlıdır. Bu bölüm her iki kullanımı da inceler. Nasıl, saat dilimi farklarını ve aritmetik işlemleri tarih ve saatlerle çalışırken işleyebileceğini açıklar.  
  
<a name="DatesAndTimes_Display"></a>   
### <a name="displaying-dates-and-times"></a>Tarihleri ve Saatleri Görüntüleme  
 Genellikle, tarihler ve saatler kullanıcı arabiriminde görüntülendiğinde tarafından tanımlanan kullanıcı kültürünün biçimlendirme kurallarını kullanmanız gerekir <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> özelliği ve <xref:System.Globalization.DateTimeFormatInfo> tarafından döndürülen nesne `CultureInfo.CurrentCulture.DateTimeFormat` özelliği. Bu yöntemlerden birini kullanarak bir tarihi biçimlendirdiğinizde geçerli kültürün biçimlendirme kuralları otomatik olarak kullanılır:  
  
-   Parametresiz <xref:System.DateTime.ToString?displayProperty=nameWithType> yöntemi  
  
-   <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> Bir biçim dizesi içeren yöntemi  
  
-   Parametresiz <xref:System.DateTimeOffset.ToString?displayProperty=nameWithType> yöntemi  
  
-   <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType>, Bir biçim dizesi içerir  
  
-   [Bileşik biçimlendirme](../../../docs/standard/base-types/composite-formatting.md) tarihlerle kullanıldığında özelliği  
  
 Aşağıdaki örnek, iki kez 11 Ekim 2012 için Gün Doğumu ve gün batımı verilerini görüntüler. İlk geçerli kültürü Hırvatça (Hırvatistan) ve İngilizce (İngiltere) için ayarlar. Her durumda, tarihler ve saatler, o kültür için uygun biçimde görüntülenir.  
  
 [!code-csharp[Conceptual.Globalization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates1.cs#2)]
 [!code-vb[Conceptual.Globalization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates1.vb#2)]  
  
<a name="DatesAndTimes_Persist"></a>   
### <a name="persisting-dates-and-times"></a>Kalıcı Tarihler ve Saatler  
 Hiçbir zaman kültüre göre değişebilen bir biçimde tarih ve saat verilerini kalıcı olması. Bozuk veriler veya bir çalışma zamanı özel durumu sonuçları yaygın bir programlama hatası budur. Aşağıdaki örnek, dizeleri İngilizce (ABD) kültürünün biçimlendirme kurallarını kullanarak 9 Ocak 2013 ve 18 Ağustos 2013 iki tarih serileştirir. Veriler alınıp İngilizce (ABD) kültürünün kuralları geleneklerine göre ayrıştırıldığında, başarıyla geri yüklenir. Ancak, alındığında ve ayrıştırıldığında İngilizce (İngiltere) kültürü kurallarını kullanarak birinci tarih yanlışlıkla 1 Eylül olarak yorumlanır ve Gregoryen takvimini takviminde on sekizinci ay olmadığından ayrıştırmak saniye başarısız olur.  
  
 [!code-csharp[Conceptual.Globalization#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates2.cs#3)]
 [!code-vb[Conceptual.Globalization#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates2.vb#3)]  
  
 Üç yoldan herhangi birini bu sorunu önleyebilirsiniz:  
  
-   Tarih ve saat dizesi olarak yerine ikili biçimde serileştirin.  
  
-   Kaydet ve kullanıcının kültürü ne olursa olsun aynı olan özel biçim dizesi kullanarak tarih ve saat dize gösterimini ayrıştırın.  
  
-   Dize sabit kültürün biçimlendirme kurallarını kullanarak kaydedin.  
  
 Aşağıdaki örnek, son yaklaşımı gösterir. Statik tarafından döndürülen sabit kültürün biçimlendirme kurallarını kullanır <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> özelliği.  
  
 [!code-csharp[Conceptual.Globalization#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates3.cs#4)]
 [!code-vb[Conceptual.Globalization#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates3.vb#4)]  
  
<a name="DatesAndTimes_TimeZones"></a>   
### <a name="serialization-and-time-zone-awareness"></a>Seri Hale Getirme ve Saat Dilimini Tanıma  
 Bir tarih ve saat değerini, genel zaman arasında birden çok yorumlaması olabilir ("mağazalar 2 Ocak 2013'te 9: 00'da zaman içinde belirli bir ana Aç") ("Doğum Tarihi: 2 Ocak 2013 6:32: 00'da "). Bir zaman değeri zaman içinde belirli bir ana temsil eder ve onu diziselleştirilmiş bir değerden geri, kullanıcının coğrafi konum veya saat dilimine bakılmaksızın zaman içinde aynı anı temsil ettiğini emin olun.  
  
 Aşağıdaki örnek bu sorunu gösterir. Bir dize olarak üç tek yerel tarih ve saat değerini kaydeder [standart biçim](../../../docs/standard/base-types/standard-date-and-time-format-strings.md) (genel tarih uzun saat, "s" sıralanabilir tarih/saat, "G" ve "o" Ring tarih/saat) ikili biçimin yanı.  
  
 [!code-csharp[Conceptual.Globalization#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates4.cs#10)]
 [!code-vb[Conceptual.Globalization#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates4.vb#10)]  
  
 Doğru bir şekilde sıralanmış sistem aynı saat dilimindeki bir sistemde verileri geri yüklendiğinde, Serisi kaldırılan tarih ve saat değerleri çıktıda gösterildiği gibi orijinal değeri yansıtır:  
  
```  
'3/30/2013 6:00:00 PM' --> 3/30/2013 6:00:00 PM Unspecified  
'2013-03-30T18:00:00' --> 3/30/2013 6:00:00 PM Unspecified  
'2013-03-30T18:00:00.0000000-07:00' --> 3/30/2013 6:00:00 PM Local  
  
3/30/2013 6:00:00 PM Local  
```  
  
 Ancak, farklı bir saat dilimindeki bir sistemde verileri geri yüklerseniz, "o" (gidiş dönüş) standart biçimi dize ile biçimlendirilmiş yalnızca tarih ve saat değerinin saat dilimi bilgilerini korur ve bu nedenle aynı anlık sürede temsil eder. Romanya Standart saat dilimindeki bir sistemde tarih ve saat verileri geri yüklendiğinde çıktı şöyledir:  
  
```  
'3/30/2013 6:00:00 PM' --> 3/30/2013 6:00:00 PM Unspecified  
'2013-03-30T18:00:00' --> 3/30/2013 6:00:00 PM Unspecified  
'2013-03-30T18:00:00.0000000-07:00' --> 3/31/2013 3:00:00 AM Local  
  
3/30/2013 6:00:00 PM Local  
```  
  
 Veri seri durumda sistemin saat dilimine bakılmaksızın zaman içinde tek bir anı temsil eden bir tarih ve saat değerini doğru şekilde yansıtmak için aşağıdakilerden birini yapabilirsiniz:  
  
-   Değer, "o" (gidiş-dönüş) standart biçim dizesini kullanarak dize olarak kaydedin. Daha sonra hedef sistemde serileştirmeyi kaldırın.  
  
-   UTC'ye dönüştürün ve "r" (RFC1123) standart biçim dizesini kullanarak dize olarak kaydedin. Daha sonra hedef sistemde serileştirmesini ve yerel saate dönüştürün.  
  
-   UTC'ye dönüştürün ve "u" (Evrensel sıralanabilir) standart biçim dizesini kullanarak dize olarak kaydedin. Daha sonra hedef sistemde serileştirmesini ve yerel saate dönüştürün.  
  
-   UTC'ye dönüştürün ve ikili biçimde kaydedin. Daha sonra hedef sistemde serileştirmesini ve yerel saate dönüştürün.  
  
 Aşağıdaki örnek her yöntemi gösterir.  
  
 [!code-csharp[Conceptual.Globalization#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates8.cs#11)]
 [!code-vb[Conceptual.Globalization#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates8.vb#11)]  
  
 Veriler Pasifik Standart saat dilimindeki bir sistemde serileştirilmiş ve Romanya Standart saat dilimindeki bir sistemde serisi, örnek aşağıdaki çıkışı görüntüler:  
  
```  
'2013-03-30T18:00:00.0000000-07:00' --> 3/31/2013 3:00:00 AM Local  
'Sun, 31 Mar 2013 01:00:00 GMT' --> 3/31/2013 3:00:00 AM Local  
'2013-03-31 01:00:00Z' --> 3/31/2013 3:00:00 AM Local  
  
3/31/2013 3:00:00 AM Local  
```  
  
 Daha fazla bilgi için [dönüştürme saatleri arasında saat dilimlerini](../../../docs/standard/datetime/converting-between-time-zones.md).  
  
<a name="DatesAndTimes_Arithmetic"></a>   
### <a name="performing-date-and-time-arithmetic"></a>Tarih ve Saat Aritmetiğini Gerçekleştirme  
 Hem <xref:System.DateTime> ve <xref:System.DateTimeOffset> türleri aritmetik işlemleri destekler. İki tarih değeri arasındaki farkı hesaplayabilirsiniz veya ekleyebilir veya belirli zaman aralıklarını bir tarih değerinden çıkarır. Ancak, tarih ve saat değerleri üzerinde aritmetik işlem saat dilimlerini ve saat dilimi ayarlama kurallarını dikkate almaz. Bu nedenle, tarih ve saat aritmetiği zaman içindeki anları temsil değerleri tutarsız sonuçlar döndürebilir.  
  
 Örneğin, Pasifik Standart saatinden Pasifik Yaz saatine geçiş, Mart 2013 yılı için 10 Mart İkinci Pazar oluşur. Aşağıdaki örnek tarih ve zamanda gösterir, 48 saat sonra 9 Mart 2013 10: 30'da Pasifik Standart saat dilimindeki bir sistemde bir araya giren zaman ayarlamasını hesaba 11 Mart 2013, 10: 30'da, sonuç almaz.  
  
 [!code-csharp[Conceptual.Globalization#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates5.cs#8)]
 [!code-vb[Conceptual.Globalization#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates5.vb#8)]  
  
 Tarih ve saat değerleri üzerinde aritmetik işleminin doğru sonuçlar ürettiğinden emin olmak için bu adımları izleyin:  
  
1.  Kaynak saat dilimindeki saati UTC'ye dönüştürün.  
  
2.  Aritmetik işlemi gerçekleştirir.  
  
3.  Sonuç bir tarih ve saat değeriyse UTC'den kaynak saat diliminde saate dönüştürün.  
  
 48 saati 9 Mart 2013'e 10: 30'da doğru şekilde eklemek için bu üç adımı takip eden dışında aşağıdaki örnek önceki örneğe benzerdir  
  
 [!code-csharp[Conceptual.Globalization#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates6.cs#9)]
 [!code-vb[Conceptual.Globalization#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates6.vb#9)]  
  
 Daha fazla bilgi için [tarih ve saatlerle aritmetik işlemler gerçekleştirme](../../../docs/standard/datetime/performing-arithmetic-operations.md).  
  
### <a name="using-culture-sensitive-names-for-date-elements"></a>Veri Öğeleri için Kültüre Duyarlı Adlar Kullanma  
 Ayın adı veya haftanın günü görüntülemek, uygulamanız gerekebilir. Bunu yapmak için aşağıdaki gibi bir kod yaygındır.  
  
 [!code-csharp[Conceptual.Globalization#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/monthname1.cs#19)]
 [!code-vb[Conceptual.Globalization#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/monthname1.vb#19)]  
  
 Ancak, bu kod her zaman İngilizce olarak Haftanın günlerinin adlarını döndürür. Ayın adını ayıklayan kod genellikle daha az esnektir. Sıklıkla, belirli bir dilde ay adları ve bir on iki aylık takvimi varsayar.  
  
 Kullanarak [özel tarih ve saat biçim dizeleri](../../../docs/standard/base-types/custom-date-and-time-format-strings.md) veya özelliklerini <xref:System.Globalization.DateTimeFormatInfo> nesne, aşağıdaki örnekte gösterildiği gibi kullanıcının kültüründeki ayların veya Haftanın günlerinin adlarını yansıtan dizelerin çıkarılması kolaydır. Geçerli kültürü Fransızca (Fransa) değiştirir ve haftanın günü ve ay adını 1 Temmuz 2013 adını görüntüler.  
  
 [!code-csharp[Conceptual.Globalization#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/monthname2.cs#20)]
 [!code-vb[Conceptual.Globalization#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/monthname2.vb#20)]  
  
<a name="Numbers"></a>   
## <a name="handling-numeric-values"></a>Sayısal Değerleri İşleme  
 Sayıların işlenmesi, bunlar kullanıcı arabiriminde görüntülenen olup kalıcı üzerinde bağlıdır. Bu bölüm her iki kullanımı da inceler.  
  
> [!NOTE]
>  Ayrıştırma ve biçimlendirme işlemleri, .NET Framework yalnızca temel Latin karakterleri 0-9 tanır (U + 0030-U + 0039) sayısal basamak olarak.  
  
<a name="Numbers_Display"></a>   
### <a name="displaying-numeric-values"></a>Sayısal Değerleri Görüntüleme  
 Genellikle, kullanıcı arabiriminde sayılar görüntülendiğinde tarafından tanımlanan kullanıcı kültürünün biçimlendirme kurallarını kullanmanız gerekir <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> özelliği ve <xref:System.Globalization.NumberFormatInfo> tarafından döndürülen nesne `CultureInfo.CurrentCulture.NumberFormat` özelliği. Aşağıdaki yöntemlerden birini kullanarak bir tarihi biçimlendirdiğinizde geçerli kültürün biçimlendirme kuralları otomatik olarak kullanılır:  
  
-   Parametresiz `ToString` herhangi bir sayısal tür yöntemi  
  
-   `ToString(String)` Bağımsız değişken olarak bir biçim dizesi içeren her sayısal tür yöntemi  
  
-   [Bileşik biçimlendirme](../../../docs/standard/base-types/composite-formatting.md) sayısal değerlerle kullanıldığında özelliği  
  
 Aşağıdaki örnek, Paris, Fransa'daki aylık Ortalama sıcaklığı görüntüler. İlk veri görüntülemeden önce geçerli kültürü Fransızca (Fransa) ayarlar ve sonra İngilizce (ABD) ayarlar. Her durumda, ay adları ve sıcaklıklar, o kültür için uygun biçimde görüntülenir. İki kültürün sıcaklık değerinde farklı ondalık ayırıcılar kullandığını unutmayın. Ayrıca örnek "MMMM" özel tarih ve saat biçim dizesi tam ay adını görüntülemek için kullandığı ve bunu uygun boşluk miktarını sonuçtaki ay adı için enuzunayadınınuzunluğunubelirleyerekayırdığınıunutmayın<xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A?displayProperty=nameWithType></C0>dizisi.  
  
 [!code-csharp[Conceptual.Globalization#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/numbers1.cs#5)]
 [!code-vb[Conceptual.Globalization#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/numbers1.vb#5)]  
  
<a name="Numbers_Persist"></a>   
### <a name="persisting-numeric-values"></a>Kalıcı Sayısal Değerler  
 Hiçbir zaman kültüre özgü biçimde sayısal veri kalıcı olması. Bozuk veriler veya bir çalışma zamanı özel durumu sonuçları yaygın bir programlama hatası budur. Aşağıdaki örnek rastgele on kayan noktalı sayı oluşturur ve ardından bunları dize olarak İngilizce (ABD) kültürünün biçimlendirme kurallarını kullanarak serileştirir. Veriler alınıp İngilizce (ABD) kültürünün kuralları geleneklerine göre ayrıştırıldığında, başarıyla geri yüklenir. Alındığında ve Fransızca (Fransa) kültürü kurallarını geleneklerine göre ayrıştırıldığında, kültürler farklı ondalık ayırıcılar kullandığından ancak sayıların hiçbiri ayrıştırılamaz.  
  
 [!code-csharp[Conceptual.Globalization#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/numbers2.cs#6)]
 [!code-vb[Conceptual.Globalization#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/numbers2.vb#6)]  
  
 Bu sorunu önlemek için aşağıdaki tekniklerden birini kullanabilirsiniz:  
  
-   Kaydet ve kullanıcının kültürü ne olursa olsun aynı olan özel biçim dizesi kullanarak sayının dize gösterimini ayrıştırın.  
  
-   Tarafından döndürülen sabit kültürün biçimlendirme kurallarını kullanarak sayıyı bir dize olarak kaydedin <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> özelliği.  
  
-   Sayı dize biçimi yerine ikili biçimde serileştirin.  
  
 Aşağıdaki örnek, son yaklaşımı gösterir. Dizisini serileştirir <xref:System.Double> değerleri, seri durumdan çıkarır ve İngilizce (ABD) ve Fransızca (Fransa) kültürler biçimlendirme kurallarını kullanarak görüntüler.  
  
 [!code-csharp[Conceptual.Globalization#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/numbers3.cs#7)]
 [!code-vb[Conceptual.Globalization#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/numbers3.vb#7)]  
  
 Para birimi değerlerini serileştirmek özel bir durumdur. Para birimi değerini ifade edildiği para biriminde bağlı olduğundan; Bu, bağımsız bir sayısal değer olarak değerlendirilmesi çok mantıklı. Para birimi değeri, para birimi sembolü içeren bir biçimlendirilmiş dize olarak kaydederseniz, ancak bu varsayılan kültürü aşağıdaki örnekte gösterildiği gibi farklı bir para birimi sembolü kullanan sistemde bunun serisi kaldırılamaz.  
  
 [!code-csharp[Conceptual.Globalization#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/currency1.cs#16)]
 [!code-vb[Conceptual.Globalization#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/currency1.vb#16)]  
  
 Bunun yerine, böylece değer ve para birimi simgesi geçerli Kültürden bağımsız seri durumdan çıkarılabiliyorsa kültür adı gibi bazı kültürel bilgilerle birlikte sayısal değeri seri hale. Aşağıdaki örnek tanımlayarak yapan bir `CurrencyValue` yapısı iki üyeli: <xref:System.Decimal> değeri ve değerin ait olduğu kültürün adı.  
  
 [!code-csharp[Conceptual.Globalization#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/currency2.cs#17)]
 [!code-vb[Conceptual.Globalization#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/currency2.vb#17)]  
  
<a name="Cultures"></a>   
## <a name="working-with-culture-specific-settings"></a>Kültüre Özgü Ayarlarla Çalışma  
 .NET Framework'teki <xref:System.Globalization.CultureInfo> sınıfı belirli bir kültür veya bölgeyi temsil eder. Bazı özellikleri bir kültürün bazı yönleri hakkında belirli bilgi sağlayan nesneleri döndürür:  
  
-   <xref:System.Globalization.CultureInfo.CompareInfo%2A?displayProperty=nameWithType> Özelliği döndürür bir <xref:System.Globalization.CompareInfo> kültürü karşılaştırır ve sıralar dizeleri hakkında bilgi içeren nesne.  
  
-   <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> Özelliği döndürür bir <xref:System.Globalization.DateTimeFormatInfo> tarih ve saat verilerini biçimlendirmede kullanılan kültüre özgü bilgiler sağlayan nesne.  
  
-   <xref:System.Globalization.CultureInfo.NumberFormat%2A?displayProperty=nameWithType> Özelliği döndürür bir <xref:System.Globalization.NumberFormatInfo> sayısal verileri biçimlendirmede kullanılan kültüre özgü bilgiler sağlayan nesne.  
  
-   <xref:System.Globalization.CultureInfo.TextInfo%2A?displayProperty=nameWithType> Özelliği döndürür bir <xref:System.Globalization.TextInfo> kültürle ilgili bilgileri sağlayan nesne yazma sistemi.  
  
 Genel olarak, belirli değerleri hakkında varsayımlar yapmayın <xref:System.Globalization.CultureInfo> özellikleri ve ilgili nesneleri. Bunun yerine, kültüre özel verileri değiştirmeniz Bu nedenlerden dolayı görüntülemeniz gerekir:  
  
-   Tek tek özellik değerleri değiştirme ve düzeltme zaman içerisinde, veriler düzeltildiğinden, daha iyi veri kullanılabilir olduğunda veya kültüre özel kurallar değiştirme gibi tabidir.  
  
-   Tek tek özellik değerleri, .NET Framework veya işletim sistemi sürümleri sürümleri arasında değişebilir.  
  
-   .NET Framework, yeni kültürleri destekler. Bu, varolan standart kültürleri tamamlayan veya varolan bir standart kültürü tamamen değiştiren özel bir yeni kültür tanımlamayı mümkün kılar.  
  
-   Kullanıcı kullanarak kültüre özgü ayarları özelleştirebilir **bölge ve dil** Denetim Masası'ndaki uygulama. Ne zaman örneği bir <xref:System.Globalization.CultureInfo> nesnesini çağırarak, bu kullanıcı özelleştirmelerini yansıtır olup olmadığını belirleyebilir <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> Oluşturucusu. Kullanıcının beklediği biçimde verilerle sunulur, böylece tipik olarak, son kullanıcı uygulamaları için kullanıcı tercihleri dikkate.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Genelleştirme ve Yerelleştirme](../../../docs/standard/globalization-localization/index.md)
- [Dizeleri Kullanmak için En İyi Uygulamalar](../../../docs/standard/base-types/best-practices-strings.md)
