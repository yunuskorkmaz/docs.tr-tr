---
title: "XAML Düğüm Akış Yapılarını ve Kavramlarını Anlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XAML node streams [XAML Services]
- nodes [XAML Services], XAML node stream
- XAML [XAML Services], XAML node streams
ms.assetid: 7c11abec-1075-474c-9d9b-778e5dab21c3
caps.latest.revision: "14"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: ae5cfd6cdb557aff4910f38ea0fb7f4b54afbbb0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="understanding-xaml-node-stream-structures-and-concepts"></a>XAML Düğüm Akış Yapılarını ve Kavramlarını Anlama
XAML düğümü akışı tasarım kavramı XAML okuyucuları ve .NET Framework XAML hizmetlerinde uygulandığı şekilde XAML yazıcılarının temel alır. XAML düğümü akışı XAML düğüm kümesinin kavramsallaştırılması ' dir. Bu kavramsallaştırılması, XAML işlemci XAML düğüm ilişkilerde yapısını aynı anda anlatılmaktadır. Herhangi bir zamanda yalnızca bir geçerli kaydı veya geçerli konumu bir açık XAML düğümü akışı var ve yalnızca bilgi kullanılabilir o konumdan API pek çok görünüşünün rapor. XAML düğümü akışı geçerli düğümünde bir nesne, bir üye ya da bir değer olacak şekilde açıklanabilir. XAML düğümü akışı XAML düşünerek XAML okuyucuları XAML yazıcılarının ile iletişim kurabilmesini ve görüntülemek, etkileşimde veya bir yükleme yolu veya kaydetme sırasında XAML düğüm akış içeriğini değiştirmek bir programı etkinleştirmek XAML içerir yolu işlemi. XAML okuyucu ve yazıcı API tasarım ve XAML düğüm akış kavram önceki ilgili okuyucu ve yazıcı tasarımları ve kavramları, benzer gibi [!INCLUDE[TLA#tla_xmldom](../../../includes/tlasharptla-xmldom-md.md)] ve <xref:System.Xml.XmlReader> ve <xref:System.Xml.XmlWriter> sınıfları. Bu konu, XAML düğüm akış kavramları açıklar ve XAML Beyanları XAML düğüm düzeyinde etkileşimde yordamları yazma biçimini açıklar.  
  
<a name="loading_into_a_xaml_reader"></a>   
## <a name="loading-xaml-into-a-xaml-reader"></a>XAML XAML okuyucuya yükleniyor  
 Temel <xref:System.Xaml.XamlReader> sınıfı bir XAML okuyucuya ilk XAML yüklenmesi için belirli bir teknik bildirme değil. Bunun yerine, türetilmiş bir sınıf bildirir ve genel özellikleri ve giriş kaynağına kısıtlamaları XAML için de dahil olmak üzere, bir yükleme teknik uygular. Örneğin, bir <xref:System.Xaml.XamlObjectReader> kök veya temel temsil eden tek bir nesnenin giriş kaynağından başlayarak bir nesne grafiğinin okur. <xref:System.Xaml.XamlObjectReader> Bir nesne grafiğinin XAML düğüm akıştan üretir.  
  
 En belirgin .NET Framework XAML hizmetlerinde – tanımlanan <xref:System.Xaml.XamlReader> sınıfıdır <xref:System.Xaml.XamlXmlReader>. <xref:System.Xaml.XamlXmlReader>ilk XAML gibi bir metin dosyasına bir akış veya dosya yolu aracılığıyla doğrudan veya dolaylı olarak ilgili okuyucusu sınıf aracılığıyla yükleme ya da yükler <xref:System.IO.TextReader>. <xref:System.Xaml.XamlReader> , Onu yüklendikten sonra XAML giriş kaynağı tamamen içeren olarak düşünülebilir. Ancak, <xref:System.Xaml.XamlReader> temel API, böylece okuyucu XAML tek bir düğüm ile etkileşim tasarlanmıştır. İlk yüklendiğinde, karşılaştığınız ilk tek düğümlü XAML ve onun başlangıç nesnesinden köküdür.  
  
### <a name="the-xaml-node-stream-concept"></a>XAML düğümü akışı kavramı  
 Genellikle daha DOM, ağaç benzetimini veya XML tabanlı teknolojiler erişme doğrultusunda yaklaşım sorgu tabanlı biliyorsanız, XAML düğümü akışı canlandırmanın yararlı bir yolu aşağıdaki gibidir. Yüklenen XAML bir DOM veya burada olası her düğüm tüm genişletilmiş ve doğrusal olarak sunulan bir ağaç olduğunu düşünün. Düğümleri arasında ilerlemek gibi "" veya "" bir DOM ilgilendirebilecek düzeylerinden çapraz geçiş yapan, ancak bu level kavramları bir düğüm akış ilgili olmadığından XAML düğümü akışı izleme açıkça korumaz. Düğümü akışı için "geçerli" konumu olsa da, diğer bölümleri akışın başvuru olarak kendiniz depoladığınız sürece, her geçerli düğüm konumu dışında düğümü akışı görünümü dışında yönüdür.  
  
 XAML düğümü akışı kavram tüm düğüm akışı giderseniz, tüm XAML gösterimi işlenmiş garanti önemli avantajı vardır; bir sorgu, DOM işlem veya işleme bilgileri bazı doğrusal diğer yaklaşımı tam XAML temsili bir bölümü eksik olduğunu endişelenmeniz gerekmez. Bu nedenle, XAML düğüm akış gösterim işlem XAML işleme okuma ve yazma aşamaları arasında davranır kendi işlemi burada ekleyebilirsiniz XAML okuyucuları ve XAML yazıcıları bağlamak için hem bir sistem sağlamak için idealdir. Çoğu durumda, kasıtlı olarak en iyi duruma getirilmiş veya kaynak metin, ikili veya nesne grafiğinin sırasını nasıl görünebilir karşı XAML okuyucuları tarafından kaldırılmasında XAML düğümü akışı düğümler sıralama. Bu davranış, hiçbir zaman "" düğüm akışında dönmek için sahip oldukları bir konuma yapabildiği XAML yazıcılarının bulunan bir XAML işleme mimarisi zorlamak için tasarlanmıştır. İdeal olarak, tüm XAML yazma işlemlerini hareket için şema bağlamı artı düğümü akışı geçerli konumunu bağlı olmalıdır.  
  
<a name="a_basic_reading_node_loop"></a>   
## <a name="a-basic-reading-node-loop"></a>Bir temel okuma düğümü Döngü  
 Temel bir düğüm döngü XAML düğümü akışı incelemek için aşağıdaki kavramlarını oluşur okuma. Döngüler, bu konuda anlatıldığı gibi varsayın metin tabanlı, okunabilir bir XAML okuma düğümünün amacıyla dosya kullanarak <xref:System.Xaml.XamlXmlReader>. Bu bölümdeki bağlantılar belirli XAML düğüm döngü API tarafından uygulanan bakın <xref:System.Xaml.XamlXmlReader>.  
  
-   XAML düğümü akışı sonunda olmadığından emin olun (denetleyin <xref:System.Xaml.XamlXmlReader.IsEof%2A>, veya <xref:System.Xaml.XamlXmlReader.Read%2A> dönüş değeri). Akış sonunda varsa, geçerli bir düğüm yoktur ve çıkılması gerekiyor.  
  
-   Düğümün ne tür çağırarak XAML düğümü akışı şu anda gösterir. denetleyin <xref:System.Xaml.XamlXmlReader.NodeType%2A>.  
  
-   Doğrudan bağlı bir ilişkili XAML nesne yazıcısı varsa, genellikle çağırmanız <xref:System.Xaml.XamlWriter.WriteNode%2A> bu noktada.  
  
-   Temel <xref:System.Xaml.XamlNodeType> geçerli kayıt ya da geçerli düğümün çağrı olarak aşağıdakilerden birini düğümü içeriği hakkında bilgi edinmek için bildirilen:  
  
    -   İçin bir <xref:System.Xaml.XamlXmlReader.NodeType%2A> , <xref:System.Xaml.XamlNodeType.StartMember> veya <xref:System.Xaml.XamlNodeType.EndMember>, çağrı <xref:System.Xaml.XamlXmlReader.Member%2A> almak için <xref:System.Xaml.XamlMember> üyesi hakkında bilgi. Üye olabilir Not bir <xref:System.Xaml.XamlDirective>, ve bu nedenle yukarıdaki nesne geleneksel türü tanımlı üye mutlaka olmayabilir. Örneğin, `x:Name` uygulanan bir nesne XAML üye olarak görünüyor nerede <xref:System.Xaml.XamlMember.IsDirective%2A> geçerlidir ve <xref:System.Xaml.XamlMember.Name%2A> üyesi `Name`, bu yönergesi XAML dili XAML ad uzayı altında olduğunu belirten diğer özelliklerle.  
  
    -   İçin bir <xref:System.Xaml.XamlXmlReader.NodeType%2A> , <xref:System.Xaml.XamlNodeType.StartObject> veya <xref:System.Xaml.XamlNodeType.EndObject>, çağrı <xref:System.Xaml.XamlXmlReader.Type%2A> almak için <xref:System.Xaml.XamlType> bir nesne hakkında bilgiler.  
  
    -   İçin bir <xref:System.Xaml.XamlXmlReader.NodeType%2A> , <xref:System.Xaml.XamlNodeType.Value>, çağrı <xref:System.Xaml.XamlXmlReader.Value%2A>. Yalnızca bir değer basit ifade bir üye ya da (ancak, bu konunun ilerideki bölümde açıklandığı gibi türü dönüştürme davranışını bilmeniz) bir nesne için başlatma metin için ise bir düğüm bir değerdir.  
  
    -   İçin bir <xref:System.Xaml.XamlXmlReader.NodeType%2A> , <xref:System.Xaml.XamlNodeType.NamespaceDeclaration>, çağrı <xref:System.Xaml.XamlXmlReader.Namespace%2A> bir ad alanı düğümü için ad alanı bilgilerini elde etmek için.  
  
-   Çağrı <xref:System.Xaml.XamlXmlReader.Read%2A> XAML düğümü akışı bir sonraki düğüme XAML okuyucu ilerleyin ve yeniden adımları yineleyin.  
  
 .NET Framework XAML Hizmetleri XAML okuyucuları tarafından her zaman sağlanan XAML düğümü akışı tam, derin çapraz geçişi tüm olası düğümlerinin sağlar. XAML düğümü Döngü için tipik akış denetimi teknikler kullanılabilir gövdesi içinde tanımlama `while (reader.Read())`ve geçiş <xref:System.Xaml.XamlXmlReader.NodeType%2A> her düğümde düğümü döngüde gelin.  
  
 Düğümü akışı son dosya geçerli düğüm null ise.  
  
 Okuyucu ve yazıcı kullanan basit döngüsünü aşağıdaki örneğe benzer.  
  
```  
XamlXmlReader xxr = new XamlXmlReader(new StringReader(xamlStringToLoad));  
//where xamlStringToLoad is a string of well formed XAML  
XamlObjectWriter xow = new XamlObjectWriter(xxr.SchemaContext);  
while (xxr.Read()) {  
  xow.WriteNode(xxr);  
}  
```  
  
 Bu temel bir yükleme yolu XAML düğüm döngü örneği saydam XAML okuyucu ve XAML yazıcı bağlanır, eğer farklı bir şey yapmak kullandığınız <xref:System.Xaml.XamlServices.Parse%2A?displayProperty=nameWithType>. Ancak bu temel yapı okuma veya yazma senaryoyu uygulamak için genişletilir. Bazı olası senaryolar aşağıdaki gibidir:  
  
-   Anahtarı'nda <xref:System.Xaml.XamlXmlReader.NodeType%2A>. Hangi düğüme bağlı olarak okunan türü farklı eylemleri gerçekleştirin.  
  
-   Çağırmayın <xref:System.Xaml.XamlWriter.WriteNode%2A> tüm durumlarda. Yalnızca çağrısı <xref:System.Xaml.XamlWriter.WriteNode%2A> bazı <xref:System.Xaml.XamlXmlReader.NodeType%2A> durumları.  
  
-   İçinde belirli düğüm türü için mantığı, o düğümün ayrıntılarını çözümleyebilir ve bunlar üzerinde işlem. Örneğin, belirli bir XAML ad alanından gelir ve ardından bırakın ya da herhangi bir nesne değil, XAML ad alanından erteleneceği nesneleri yazabilirsiniz. Veya drop veya aksi halde XAML sisteminizi desteklemediği tüm XAML yönergeleri işleme üyelik bir parçası olarak yeniden işleyin.  
  
-   Özel tanımlama <xref:System.Xaml.XamlObjectWriter> , geçersiz kılmalar `Write*` yöntemleri, büyük olasılıkla XAML şema içeriği atlar türü eşleme gerçekleştirme.  
  
-   Oluşturmak <xref:System.Xaml.XamlXmlReader> özelleştirilmiş XAML davranış farklılıkları hem okuyucu ve yazıcı tarafından kullanılan varsayılan olmayan XAML şema içeriği kullanılacak.  
  
### <a name="accessing-xaml-beyond-the-node-loop-concept"></a>XAML düğümü Döngü kavram ötesinde erişme  
 XAML gösterimi dışında bir XAML düğüm döngü olarak çalışmak için büyük olasılıkla başka yolları vardır. Örneğin, var dizini oluşturulmuş bir düğüm okuyabilir veya özellikle erişen düğümleri doğrudan göre bir XAML okuyucu `x:Name`, göre `x:Uid`, veya diğer tanımlayıcıları aracılığıyla. .NET framework XAML hizmetlerinde tam uygulamasını sağlamaz, ancak Hizmetleri ve Destek türleri aracılığıyla önerilen bir desen sağlar. Daha fazla bilgi için bkz. <xref:System.Xaml.IXamlIndexingReader> ve <xref:System.Xaml.XamlNodeList>.  
  
> [!TIP]
>  Microsoft ayrıca Microsoft XAML Araç Seti bilinen bir bant dışı yayın üretir. Yayın öncesi aşamalar halinde hala bu bant dışı sürümüdür. Ancak, yayın öncesi bileşenleriyle çalışmaya istekli olup olmadığını XAML araçları ve XAML statik çözümleme için Microsoft XAML Araç Seti ilginç bazı kaynaklar sağlar. FxCop çözümleme ve XAML şema içeriği için Silverlight için destek, Microsoft XAML Araç Seti XAML DOM API içerir. Daha fazla bilgi için bkz: [Microsoft XAML Araç Seti](http://code.msdn.microsoft.com/XAML).  
  
<a name="working_with_the_current_node"></a>   
## <a name="working-with-the-current-node"></a>Geçerli düğüm ile çalışma  
 XAML düğümü Döngü kullanan çoğu senaryoları düğümleri salt okunur değil. Çoğu senaryoda geçerli düğümleri işlemek ve her düğüm uygulaması için aynı anda geçirmek <xref:System.Xaml.XamlWriter>.  
  
 Normal yük yolu senaryosunda bir <xref:System.Xaml.XamlXmlReader> bir XAML düğüm akış oluşturur; XAML düğümleri mantığı ve XAML şema içeriği; göre işlenir ve düğümlerin geçirilen bir <xref:System.Xaml.XamlObjectWriter>. Kullanıcılarınızın bir uygulama veya framework sonra sonuçta elde edilen nesne grafiğinin tümleştirin.  
  
 Tipik bir kaydetme yolu senaryo, bir <xref:System.Xaml.XamlObjectReader> nesne grafiğinin okur, tek tek XAML düğümleri işlenir ve <xref:System.Xaml.XamlXmlWriter> XAML metin dosyası olarak seri hale getirilmiş sonuç çıkarır. Yolları ve senaryoları ile tam olarak bir XAML düğümü birer birer ve XAML düğümleri XAML tür sistemi ve.NET Framework XAML Hizmetleri API tarafından tanımlanan standartlaştırılmış bir şekilde işleme için kullanılabilir çalışma içeren anahtardır.  
  
### <a name="frames-and-scope"></a>Çerçeve ve kapsamı  
 XAML düğümü Döngü doğrusal bir şekilde bir XAML düğüm akış anlatılmaktadır. Düğümü akışı ve diğer nesneleri içeren benzeri üyeleri halinde nesnelere erişir. Genellikle, XAML düğümü akışı kapsamında bir çerçeve ve yığını kavramı uygulayarak izlemek yararlıdır. İçinde çalışırken düğüm akış ayarlama etkin, bu özellikle doğrudur. Çerçeve ve yığın düğümü Döngü mantığının parçası sayısı gibi uygulamak Destek `StartObject` (veya `GetObject`) ve `EndObject` kapsamları yapısı DOM açısından düşünülen, bir XAML düğüm yapısında düzen gibi.  
  
<a name="traversing_and_entering_object_nodes"></a>   
## <a name="traversing-and-entering-object-nodes"></a>Çapraz geçiş yapma ve nesne düğümleri girme  
 XAML okuyucu tarafından açıldığında bir düğüm akış ilk düğüm kök nesnesinin Başlangıç nesnesi düğümdür. Tanımı tarafından bu nesne her zaman tek nesne düğümü ve hiç eş sahiptir. Herhangi bir gerçek XAML örnekte kök nesnesi daha çok nesne tutan bir veya daha fazla özellikleri sağlamak için tanımlanır ve bu özellikleri üye düğümünüz. Üye düğümler bir veya daha fazla nesne düğümünüz veya de bir değer düğümünde sonlandırmaya. Kök nesnede genellikle XAML metin biçimlendirme öznitelikleri olarak sözdizimsel olarak atanmış, ancak eşlemek XAML ad kapsamları tanımlayan bir `Namescope` XAML düğüm akış gösteriminde düğüm türü.  
  
 (Bu, .NET Framework'teki mevcut türleri tarafından yedeklenen değil, rastgele XAML) aşağıdaki XAML örneği göz önünde bulundurun. Bu nesne modelinde varsayımında `FavorCollection` olan `List<T>` , `Favor`, `Balloon` ve `NoiseMaker` için atanabilir olan `Favor`, `Balloon.Color` özelliği tarafından desteklenen bir `Color` nesne nasıl WPF tanımlar için benzer renkleri bilinen renk adları olarak ve `Color` öznitelik sözdizimi için tür dönüştürücüsünü destekler.  
  
|XAML biçimlendirme|Sonuçta elde edilen XAML düğümü akışı|  
|-----------------|--------------------------------|  
|`<Party`|`Namespace`düğümü için`Party`|  
|`xmlns="PartyXamlNamespace">`|`StartObject`düğümü için`Party`|  
|`<Party.Favors>`|`StartMember`düğümü için`Party.Favors`|  
||`StartObject`düğümü için örtük`FavorCollection`|  
||`StartMember`düğümü için örtük `FavorCollection` öğelerini özelliği.|  
|`<Balloon`|`StartObject`düğümü için`Balloon`|  
|`Color="Red"`|`StartMember`düğümü için`Color`<br /><br /> `Value`öznitelik değeri dizesi için düğüm`"Red"`<br /><br /> `EndMember`için`Color`|  
|`HasHelium="True"`|`StartMember`düğümü için`HasHelium`<br /><br /> `Value`öznitelik değeri dizesi için düğüm`"True"`<br /><br /> `EndMember`için`HasHelium`|  
|`>`|`EndObject`için`Balloon`|  
|`<NoiseMaker>Loudest</NoiseMaker>`|`StartObject`düğümü için`NoiseMaker`<br /><br /> `StartMember`düğümü için`_Initialization`<br /><br /> `Value`düğümü için başlatma değer dizesi`"Loudest"`<br /><br /> `EndMember`düğümü için`_Initialization`<br /><br /> `EndObject`için`NoiseMaker`|  
||`EndMember`düğümü için örtük `FavorCollection` öğelerini özelliği.|  
||`EndObject`düğümü için örtük`FavorCollection`|  
|`</Party.Favors>`|`EndMember`için`Favors`|  
|`</Party>`|`EndObject`için`Party`|  
  
 XAML düğümü akışı aşağıdaki davranışı kullanabilirsiniz:  
  
-   Varsa bir `Namespace` düğüm yoksa, bu akışa hemen önce eklenir `StartObject` ile XAML ad uzayı bildirimi `xmlns`. Önceki tabloya olan XAML ve örnek düğüm akış yeniden bakın. Bildirim nasıl `StartObject` ve `Namespace` düğümleri bildirimi konumlarına metin biçimlendirmede karşı harfine gözükmüyor. Bu temsilcisidir ad alanı düğümleri her zaman göründüğü öncesinde düğümü davranış için düğüm akışında geçerlidir. Bu tasarım amacı, ad alanı bilgisi nesne yazıcılara önemlidir ve nesne türü eşleştirme veya aksi gerçekleştirmek için nesne yazan girişimleri işlemeden önce bilinmesi gerekir. XAML ad alanı bilgisi akış, uygulama kapsamında öncesinde yerleştirme her zaman kendi sunulan sırayla düğümü akışı işlemek daha basit yapar.  
  
-   Yukarıdaki nedeniyle, onu bir veya daha fazla husustur `Namespace` ilk çoğu gerçek biçimlendirme durumda düğümler başlangıçta, geçiş değil, okuduğunuz düğümleri `StartObject` kök.  
  
-   A `StartObject` düğümü arkasından `StartMember`, `Value`, veya bir hemen `EndObject`. Hiçbir zaman hemen bir başkası tarafından sonrasında `StartObject`.  
  
-   A `StartMember` tarafından izlenen bir `StartObject`, `Value`, veya bir hemen `EndMember`. Tarafından izlenebilir `GetObject`, burada değeri bekleniyor var olan bir üst nesne değerinden gelen üyeleri için yerine bir `StartObject` yeni bir değer örneği. Tarafından da izlenebilir bir `Namespace` yaklaşan bir geçerli düğüm `StartObject`. Hiçbir zaman hemen bir başkası tarafından sonrasında `StartMember`.  
  
-   A `Value` düğümü değerini temsil eder; hiçbir "EndValue" yoktur. Yalnızca izlenebilir bir `EndMember`.  
  
    -   XAML başlatma metin nesnesinin yapım tarafından kullanılan bir nesne değeri yapısında oluşmaz. Bunun yerine, adlı bir üye için ayrılmış üye düğüm `_Initialization` oluşturulur. ve o üyesi düğümü başlatma değer dizesi içerir. Varsa, `_Initialization` her zaman ilk olduğu `StartMember`. `_Initialization`Bazı XAML Hizmetleri Beyanları dil XAML isim alanı XAML ile içinde açıklamak için nitelenmemiş olması `_Initialization` türleri yedekleme içinde tanımlanmış bir özellik değil.  
  
    -   Bir üye değeri birleşimini değerinin bir özniteliğini temsil eder. Sonunda olabilir değer Dönüştürücüsü bu değer işleme katılan ve düz bir dize değeridir. Ancak, bu düğüm akış XAML nesne yazıcısı işleyene kadar değerlendirilmez. XAML nesne yazıcısı gerekli XAML şema içeriği, türü sistem eşlemesi ve değer dönüştürmeleri için gereken diğer destek sahiptir.  
  
-   Bir `EndMember` düğümü arkasından bir `StartMember` düğümü tarafından veya bir sonraki üyesi için bir `EndObject` üye sahibi için düğüm.  
  
-   Bir `EndObject` düğümü arkasından bir `EndMember` düğümü. Tarafından da izlenebilir bir `StartObject` nesneleri bir koleksiyonun öğelerini eşlerden olduğu durumlarda düğümü. Veya tarafından izlenebilir bir `Namespace` yaklaşan bir geçerli düğüm `StartObject`.  
  
    -   Tüm düğüm akış kapatma benzersiz çalışması için `EndObject` , kök tarafından herhangi bir şey gelmez; okuyucu şimdi son dosya, ve <xref:System.Xaml.XamlReader.Read%2A> döndürür `false`.  
  
<a name="value_converters_and_the_xaml_node_stream"></a>   
## <a name="value-converters-and-the-xaml-node-stream"></a>Değer dönüştürücüler ve XAML düğümü akışı  
 Değer dönüştürücüsü, biçimlendirme uzantısı, bir tür dönüştürücüsünü (değer serileştiricileri dahil) veya değer dönüştürücüsü XAML tür sistemi aracılığıyla olarak bildirilen başka bir adanmış sınıf için genel bir terimdir. XAML düğümü akışı bir tür dönüştürücü kullanımı ve biçimlendirme uzantısı kullanımı çok farklı sunumu vardır.  
  
### <a name="type-converters-in-the-xaml-node-stream"></a>XAML düğüm akış tür dönüştürücüleri  
 Öznitelik, sonuçta bir türü dönüştürücü kullanımı sonuçlarında bildirilir olduğunu XAML düğüm akış üye değeri olarak ayarlayın. XAML düğümü akışı bir tür dönüştürücü örneği nesnesi üretmek ve değeri iletmektir denemez. Tür dönüştürücüsünü 's dönüştürme uygulamasını kullanarak çağırma XAML şema içeriği ve tür eşlemesi için kullanılarak gerektirir. Hangi tür dönüştürücü sınıfı değeri işlemek için kullanılması gereken bile belirleme XAML şema içeriği dolaylı olarak gerektirir. Varsayılan XAML şema içeriği kullandığınızda, bu bilgiler XAML türü sistemden kullanılamaz. XAML yazıcı bağlantısı önce XAML düğüm akış düzeyinde türü dönüştürücü sınıfı bilgi gerekiyorsa, buradan edinebilirsiniz <xref:System.Xaml.XamlMember> ayarlanan üye bilgileri. Ancak Aksi halde, XAML şema içeriği ve tür eşlemesi sistemi gerektiren işlemler geri kalanı gerçekleştirilen kadar türü dönüştürücü giriş XAML düğüm akış düz bir değer olarak korunması, örneğin bir XAML tarafından nesne oluşturma nesne yazıcı.  
  
 Örneğin, aşağıdaki sınıf tanımı anahat ve XAML kullanımı için göz önünde bulundurun:  
  
```  
public class BoardSizeConverter : TypeConverter {  
  //converts from string to an int[2] by splitting on an "x" char  
}  
public class GameBoard {  
  [TypeConverter(typeof(BoardSizeConverter))]  
  public int[] BoardSize; //2x2 array, initialization not shown  
}  
```  
  
```xaml  
<GameBoard BoardSize="8x8"/>  
```  
  
 XAML düğümü akışı bu kullanım için metin gösterimi aşağıdaki gibi ifade:  
  
 `StartObject`ile <xref:System.Xaml.XamlType> temsil eden`GameBoard`  
  
 `StartMember`ile <xref:System.Xaml.XamlMember> temsil eden`BoardSize`  
  
 `Value`bir metin dizesiyle düğümü "`8x8`"  
  
 `EndMember`eşleşir`BoardSize`  
  
 `EndObject`eşleşir`GameBoard`  
  
 Bu düğüm akış türü dönüştürücü örneği yok olduğuna dikkat edin. Ancak çağırarak tür dönüştürücü bilgi edinebilirsiniz <xref:System.Xaml.XamlMember.TypeConverter%2A?displayProperty=nameWithType> üzerinde <xref:System.Xaml.XamlMember> için `BoardSize`. Geçerli bir XAML şema içeriği varsa, ayrıca dönüştürücü yöntemleri bir örnekten elde ederek çağırabilirsiniz <xref:System.Xaml.Schema.XamlValueConverter%601.ConverterInstance%2A>.  
  
### <a name="markup-extensions-in-the-xaml-node-stream"></a>XAML düğümü akışı biçimlendirme uzantıları  
 Biçimlendirme uzantısı kullanımı XAML düğüm akış nesneyi biçimlendirme uzantısı örneğin temsil ettiği üyesi içinde nesne düğümü olarak bildirilir. Bu nedenle bir türü dönüştürücü kullanımı olan ve daha fazla bilgi taşıyan çok biçimlendirme uzantısı kullanımı daha açıkça düğüm akış gösterim sunulur. <xref:System.Xaml.XamlMember>Kullanım situational olduğundan ve her olası biçimlendirme durumda değişir bilgileri, herhangi bir şey biçimlendirme uzantısı hakkında istiyordu değil; tür dönüştürücüleri ile olduğu gibi ayrılmış ve tür veya üye başına kapalı değil.  
  
 Biçimlendirme uzantısı kullanımı (genellikle söz konusu olduğu) XAML metin biçimlendirme özniteliği formunda yapıldığı olsa bile biçimlendirme uzantıları düğüm akış gösterimi nesne düğümleri olarak bir durumdur. Bir açık nesne öğesi form kullanılan biçimlendirme uzantısı kullanımları aynı şekilde işlenir.  
  
 Biçimlendirme uzantısı nesne düğümü içinde bu biçimlendirme uzantısı'nın üyeleri olabilir. XAML düğümü akışı gösterimi bu biçimlendirme uzantısı'nın kullanımını yoksa konumsal parametre kullanımı veya açık adlandırılmış parametreleri ile kullanımını mı korur.  
  
 Konumsal parametresi kullanım için XAML düğümü akışı XAML dili tarafından tanımlanan bir özellik içeren `_PositionalParameters` kullanım kaydeder. Bu özellik genel olan <xref:System.Collections.Generic.List%601> ile <xref:System.Object> kısıtlaması. Kısıtlama nesnesi ve dize değil çünkü alanlara konumsal parametre kullanımı içindeki iç içe geçmiş biçimlendirme uzantısı kullanımları içerebilir. Konumsal parametreler kullanımdan erişmek için listenin yinelemek ve tek tek liste değerleri için bir dizin oluşturucuyu kullanın.  
  
 Adlandırılmış parametre kullanımı için her adlandırılmış parametre adının düğüm akış üye düğümü olarak temsil edilir. İç içe geçmiş biçimlendirme uzantısı kullanımı olabileceğinden üye değerleri dizeler, değildir.  
  
 `ProvideValue`biçimlendirmeden uzantısı henüz çağrılır. Ancak, bir XAML okuyucu ve XAML yazıcı bağlanıyorsanız çağrılır böylece `WriteEndObject` düğümü akışta incelediğinizde biçimlendirme uzantısı düğümde çağrılır. Bu nedenle, genellikle aynı XAML şema içeriği yükleme yolunda Nesne grafiği oluşturmak için kullanılacak şekilde kullanılabilir gerekir. Aksi takdirde `ProvideValue` beklenen services kullanılabilir olmadığından herhangi biçimlendirmeden istisnalar burada uzantı atabilirsiniz.  
  
<a name="xaml_and_xml_languagedefined_members_in_the_xaml_node_stream"></a>   
## <a name="xaml-and-xml-language-defined-members-in-the-xaml-node-stream"></a>XAML ve XML dili tarafından tanımlanan üyelerinde XAML düğümü akışı  
 Belirli üyeleri bir XAML düğüm akış yorumlar ve XAML okuyucu kuralları nedeniyle yerine açık bir sunulan <xref:System.Xaml.XamlMember> arama veya oluşturma. Genellikle, bu XAML yönergeleri üyeleridir. Bazı durumlarda, XAML düğümü akışı yönergesi tanıtır XAML okuma, işlemidir. Diğer bir deyişle, özgün XAML metin girişi olmayan özel member yönergesi belirttiniz, ancak bu bilgiler kaybolur önce bir yapısal XAML kuralı ve rapor bilgilerini XAML düğüm akış karşılamak için yönergesi XAML okuyucu ekler.  
  
 Aşağıdaki liste notları tüm durumlarda bir XAML okuyucu bir yönerge XAML üyesi düğümü tanıtmak için beklenirken ve o üye düğüm .NET Framework XAML Hizmetleri uygulamalarında nasıl tanımlanır.  
  
-   **Nesne düğümü için başlatma metin:** bu üye düğüm adı `_Initialization`bir XAML yönerge temsil eder ve XAML dili XAML ad alanında tanımlı. Buradan için statik bir varlık alma <xref:System.Xaml.XamlLanguage.Initialization%2A>.  
  
-   **Biçimlendirme uzantısı için konumsal Parametreler:** bu üye düğüm adı `_PositionalParameters`, ve XAML dili XAML ad uzayı tanımlanır. Her biri üzerinde bölerek önceden ayrılmış konumsal bir parametre olan genel nesnelerin bir listesini, her zaman içeren `,` XAML girişinde verdiği sınırlayıcı karakter. Konumsal parametreler yönergesi için statik bir varlık alma <xref:System.Xaml.XamlLanguage.PositionalParameters%2A>.  
  
-   **Bilinmeyen içerik:** bu üye düğüm adı `_UnknownContent`. NET olarak söylemek olan bir <xref:System.Xaml.XamlDirective>, ve XAML dili XAML ad uzayı tanımlanır. Bu yönerge, burada XAML kaynak içeriği XAML nesne öğesi içeriyor ancak hiçbir içerik özelliği şu anda kullanılabilir XAML şema içeriği altında belirlenebilir durumlarda sentinel kullanılır. Bu durumda adlı üyeleri için denetleyerek bir XAML düğüm akış tespit edebilirsiniz `_UnknownContent`. Başka bir eylemi bir yükleme yolu XAML düğüm akış varsayılan alınmışsa <xref:System.Xaml.XamlObjectWriter> denenen oluşturur `WriteEndObject` karşılaştığında, `_UnknownContent` üye herhangi bir nesne üzerinde. Varsayılan <xref:System.Xaml.XamlXmlWriter> değil throw ve üye örtük olarak değerlendirir. Statik bir varlık için alabilirsiniz `_UnknownContent` gelen <xref:System.Xaml.XamlLanguage.UnknownContent%2A>.  
  
-   **Bir koleksiyon özelliği:**XAML için genellikle kullanılan bir koleksiyon sınıfı destekleyen CLR türünü ayrılmış bir koleksiyon öğelerini tutan özelliği adlı olsa da, bu özellik türü yedekleme önce XAML tür sistemi bilinmemektedir çözünürlüğü. Bunun yerine, XAML düğümü akışı tanıtır bir `Items` yer tutucu XAML türü koleksiyonunun bir üyesi olarak. Bu yönerge, .NET Framework XAML hizmetlerinde uygulamasında adı düğümü akışı üye olduğu `_Items`. Bu yönerge için bir sabit elde edilebilir <xref:System.Xaml.XamlLanguage.Items%2A>.  
  
     XAML düğümü akışı parseable olmaması için kapatma öğeleri öğeleri özelliğiyle içerebilir yedekleme türü çözümlemesi ve XAML şema içeriği dayalı unutmayın. Örneğin,  
  
-   **XML tanımlı üyeleri:** XML tanımlı `xml:base`, `xml:lang` ve `xml:space` üyeleri adlı XAML yönergeleri bildirilen `base`, `lang`, ve `space` .NET Framework XAML hizmetlerinde uygulamaları. Bu ad alanı XML ad alanı olan `http://www.w3.org/XML/1998/namespace`. Bunların her biri için sabitleri elde edilebilir gelen <xref:System.Xaml.XamlLanguage>.  
  
## <a name="node-order"></a>Düğüm sırası  
 Bazı durumlarda, <xref:System.Xaml.XamlXmlReader> düğümleri biçimlendirmede görüntülerse veya XML olarak işlenen sırayı karşı XAML düğümü akışı XAML düğüm sırasını değiştirir. Bu düğümler sipariş için gerçekleştirilir gibi bir <xref:System.Xaml.XamlObjectWriter> düğümü akışı yalnızca ileriye doğru bir şekilde işleyebilir.  .NET Framework XAML hizmetlerinde, bu görev performansı iyileştirme düğümü akışı XAML nesne yazan Tüketiciler için XAML yazıcısına bırakmak yerine düğümleri XAML okuyucu yeniden sıralar.  
  
 Belirli yönergeleri, özellikle daha fazla bilgi için bir nesne bir nesne öğesinden oluşturulmasını sağlamak üzere tasarlanmıştır. Bu yönergeleri: `Initialization`, `PositionalParameters`, `TypeArguments`, `FactoryMethod`, `Arguments`. .NET Framework XAML Hizmetleri XAML okuyucuları nesnenin aşağıdaki düğümü akışı ilk üyeleri olarak bu yönergeleri yerleştirmek girişimi `StartObject`, sonraki bölümde açıklanan nedeniyle.  
  
### <a name="xamlobjectwriter-behavior-and-node-order"></a>XamlObjectWriter davranış ve düğüm sırası  
 `StartObject`için bir <xref:System.Xaml.XamlObjectWriter> mutlaka hemen nesne örneğini oluşturmak için sinyal XAML nesne yazıcısı için değil. XAML ek giriş sahip bir nesne başlatmak ve ilk nesne ve ancak bundan sonra ayarı özellikleri oluşturmak için varsayılan bir oluşturucu tamamen çağırma üzerinde kalmamanız olanaklı kılan birkaç dil özellikleri içerir. Bu özellikler şunlardır: <xref:System.Windows.Markup.XamlDeferLoadAttribute>; başlatma metin; [x: TypeArguments](../../../docs/framework/xaml-services/x-typearguments-directive.md); konumsal biçimlendirme uzantısı parametrelerinin; Fabrika yöntemleri ve ilişkili [x: Arguments](../../../docs/framework/xaml-services/x-arguments-directive.md) düğümleri (XAML 2009). Bu durumların her birinde gecikme gerçek nesne oluşturması ve düğüm akış kaldırılmasında çünkü XAML nesne yazıcısı özellikle bir yapım olmayan başlangıç üyesi karşılaşıldığında gerçekte örneği oluşturma bir davranışı üzerinde güvenebilirsiniz Bu nesne türü için yönergesi.  
  
### <a name="getobject"></a>GetObject  
 `GetObject`Yeni bir nesne oluşturmak yerine bir XAML nesne yazıcısı yerine nesnenin içeren özelliğinin değeri nereden bir XAML düğümü temsil eder. Tipik bir durumda olduğu bir `GetObject` düğümü karşılaştı içeren özellik yedekleme türü nesne modelinde salt okunur kasıtlı olarak XAML düğümü akışı bir koleksiyon nesnesi veya bir sözlük nesnesi için olur. Bu senaryoda, koleksiyon veya sözlük genellikle oluşturulur ve (genellikle boş) başlatıldı sahip olan bir türde başlatma mantığı tarafından.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Xaml.XamlObjectReader>  
 [XAML Hizmetleri](../../../docs/framework/xaml-services/index.md)  
 [XAML ad uzayları](../../../docs/framework/xaml-services/xaml-namespaces-for-net-framework-xaml-services.md)
