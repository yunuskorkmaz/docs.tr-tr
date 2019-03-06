---
title: XAML Düğüm Akış Yapılarını ve Kavramlarını Anlama
ms.date: 03/30/2017
helpviewer_keywords:
- XAML node streams [XAML Services]
- nodes [XAML Services], XAML node stream
- XAML [XAML Services], XAML node streams
ms.assetid: 7c11abec-1075-474c-9d9b-778e5dab21c3
ms.openlocfilehash: 261c44ae06959ed387a4619bf2fdb99b37141c86
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57365730"
---
# <a name="understanding-xaml-node-stream-structures-and-concepts"></a>XAML Düğüm Akış Yapılarını ve Kavramlarını Anlama

XAML okuyucular ve .NET Framework XAML hizmetlerinde uygulandığı şekilde XAML yazarları XAML düğümü akışı tasarım kavramını temel alır. XAML düğümü akışı XAML düğüm kümesinin bir kavramsallaştırılması ' dir. Bu kavramsallaştırılması XAML işlemci XAML düğümü ilişkileri yapısını teker teker kılavuzluk eder. Herhangi bir zamanda yalnızca tek bir geçerli kayıt ya da geçerli konum bir açık XAML düğümü akışı var ve yalnızca bilgileri kullanılabilir o konumdan API birçok yönden rapor. XAML düğümü akışı geçerli düğüm, bir nesne, bir üyesi veya bir değer olacak şekilde açıklanabilir. XAML düğümü akışı XAML düşünerek XAML okuyucular XAML yazıcıları ile iletişim kurmak ve görüntülemek, etkileşim veya bir yükleme yolu veya kaydetme sırasında bir XAML düğüm akış içeriğini değiştirmek bir programı etkinleştirmek XAML içeren yolu işlemi. XAML okuyucu ve yazıcı API tasarımı ve XAML düğüm akış kavram benzerdir önceki ilgili okuyucu ve yazıcı tasarımları ve kavramlarını gibi [!INCLUDE[TLA#tla_xmldom](../../../includes/tlasharptla-xmldom-md.md)] ve <xref:System.Xml.XmlReader> ve <xref:System.Xml.XmlWriter> sınıfları. Bu konu, XAML düğüm akış kavramları açıklar ve XAML gösterimleri XAML düğüm düzeyinde etkileşim yordamlarını nasıl yazabileceğiniz açıklar.

<a name="loading_into_a_xaml_reader"></a>

## <a name="loading-xaml-into-a-xaml-reader"></a>XAML XAML okuyucuya yükleniyor

Temel <xref:System.Xaml.XamlReader> sınıfı bir XAML okuyucuya ilk XAML yüklemek için belirli bir teknik bildirmiyor. Bunun yerine, türetilmiş bir sınıf bildirir ve yükleme teknik genel özelliklerini ve giriş kaynağına kısıtlamaları için XAML dahil olmak üzere, uygular. Örneğin, bir <xref:System.Xaml.XamlObjectReader> kök veya temel temsil eden tek bir nesne ise giriş kaynağından başlayan bir nesne grafiğinin okur. <xref:System.Xaml.XamlObjectReader> Ardından XAML düğümü akıştan Nesne grafiği oluşturur.

En önemli .NET Framework XAML hizmetlerinde tanımlı <xref:System.Xaml.XamlReader> sınıfıdır <xref:System.Xaml.XamlXmlReader>. <xref:System.Xaml.XamlXmlReader> ilk XAML, bir metin dosyası bir akış veya dosya yolu üzerinden doğrudan veya dolaylı olarak ilgili okuyucusu sınıf aracılığıyla gibi yükleniyor ya da yükler <xref:System.IO.TextReader>. <xref:System.Xaml.XamlReader> Yüklendikten sonra tamamen XAML giriş kaynağının içerecek şekilde zorlayıcı olabilir. Ancak, <xref:System.Xaml.XamlReader> temel API okuyucu XAML tek bir düğüm ile etkileşimde olacak şekilde tasarlanmıştır. İlk yüklendiğinde, karşılaştığınız ilk düğümü XAML ve kendi başlangıç nesnesi köküdür.

### <a name="the-xaml-node-stream-concept"></a>XAML düğümü Stream kavramı

Genellikle daha tanıdık bir DOM, ağaç benzetimini veya XML tabanlı teknolojiler erişme doğrultusunda sorgu temelli yaklaşım ile, XAML düğümü akışı kavramsallaştırmanın kullanışlı bir yol aşağıdaki gibidir. Yüklenen XAML bir DOM ya da burada olası her düğüm tüm genişletilmiş ve doğrusal olarak sunulan bir ağaç olduğunu hayal edin. Düğümleri aracılığıyla geliştikçe, "içinde" veya "dışarı" için bir DOM ilgilendirebilecek düzeylerinde geçiş, ancak bu düzey kavramlarla ilgili bir düğüm akışa olmadığından XAML düğümü akışı izleme açıkça korumaz. Düğümü akışı "geçerli" konuma var, ancak kendiniz akış diğer bölümlerini başvuru olarak depoladığınız sürece düğümü akışı geçerli düğüm konumu dışında her yönüyle dışında görüntüle.

XAML düğüm akış kavramı tüm düğüm akışı giderseniz, tüm XAML gösterimi işlenen garanti önemli avantajı vardır; bir sorgu, bir DOM işlemi veya bazı diğer doğrusal yaklaşım işleme bilgiler için tam XAML gösterimi kısmı eksik olduğunu endişelenmeniz gerekmez. Bu nedenle, XAML düğümü akışı temsili bir XAML işleme işlemi okuma ve yazma aşamalar arasında davranan kendi işlemi burada ekleyebilirsiniz hem XAML okuyucular ve yazıcılar XAML bağlanma ve bir sistem sağlamak için idealdir. Çoğu durumda, kasıtlı olarak en iyi duruma getirilmiş veya sırasını kaynak metni, ikili veya nesne grafiğinin nasıl görünebilir ve XAML okuyucular tarafından yeniden düğümleri XAML düğüm akış sıralama. Bu davranışı ile XAML yazıcılarının, hiçbir zaman, "geri" düğümü stream'de dönmek için sahip olduğu bir konumda olduğundan bir XAML işleme mimarisi zorlamak için tasarlanmıştır. İdeal olarak, tüm XAML yazma işlemlerini yapmasını mümkün şema içeriği yanı sıra düğümü akışı geçerli konumunu de bağlı olmalıdır.

<a name="a_basic_reading_node_loop"></a>

## <a name="a-basic-reading-node-loop"></a>Bir temel okuma düğüm döngüsü

Temel bir okuma düğüm döngü XAML düğümü akışı incelemek için aşağıdaki kavramları oluşur. Döngüler, bu konuda açıklandığı gibi varsayar metin tabanlı, okunabilir XAML okuma düğüm amacıyla dosya kullanarak <xref:System.Xaml.XamlXmlReader>. Bu bölümdeki bağlantılar belirli XAML düğümü döngüsü tarafından uygulanan API bakın <xref:System.Xaml.XamlXmlReader>.

- XAML düğümü akışı sonunda olmadığından emin olun (denetleyin <xref:System.Xaml.XamlXmlReader.IsEof%2A>, veya <xref:System.Xaml.XamlXmlReader.Read%2A> dönüş değeri). Akışın sonunda ise hiçbir geçerli düğüm ve çıkılması gerekiyor.

- Ne tür bir düğüm çağırarak XAML düğüm akış şu anda sunar. kontrol <xref:System.Xaml.XamlXmlReader.NodeType%2A>.

- Doğrudan bağlı bir ilişkili XAML nesne yazıcısı varsa, genellikle arama <xref:System.Xaml.XamlWriter.WriteNode%2A> bu noktada.

- Temel <xref:System.Xaml.XamlNodeType> geçerli düğüm veya geçerli kayıt çağrısı olarak düğüm içeriği hakkında bilgi edinmek için aşağıdakilerden birini bildirilir:

    - İçin bir <xref:System.Xaml.XamlXmlReader.NodeType%2A> , <xref:System.Xaml.XamlNodeType.StartMember> veya <xref:System.Xaml.XamlNodeType.EndMember>, çağrı <xref:System.Xaml.XamlXmlReader.Member%2A> edinme <xref:System.Xaml.XamlMember> üyesi hakkında bilgi. Üye olabilecek bir not bir <xref:System.Xaml.XamlDirective>, ve bu nedenle yukarıdaki nesne türü tanımlı geleneksel üyesi mutlaka olmayabilir. Örneğin, `x:Name` uygulanan bir nesneyi bir XAML üyesi olarak görünür burada <xref:System.Xaml.XamlMember.IsDirective%2A> geçerlidir ve <xref:System.Xaml.XamlMember.Name%2A> üyesidir `Name`, bu yönerge, XAML dili XAML ad alanı altında olduğunu gösteren diğer özelliklere sahip.

    - İçin bir <xref:System.Xaml.XamlXmlReader.NodeType%2A> , <xref:System.Xaml.XamlNodeType.StartObject> veya <xref:System.Xaml.XamlNodeType.EndObject>, çağrı <xref:System.Xaml.XamlXmlReader.Type%2A> edinme <xref:System.Xaml.XamlType> bir nesneyle ilgili bilgileri.

    - İçin bir <xref:System.Xaml.XamlXmlReader.NodeType%2A> , <xref:System.Xaml.XamlNodeType.Value>, çağrı <xref:System.Xaml.XamlXmlReader.Value%2A>. Yalnızca basit ifadesi bir değerin bir üyesi veya başlatma metni (ancak, bu konunun ilerideki bölümde açıklandığı gibi tür dönüştürme davranışı bilmeniz) bir nesne için ise bir düğüm bir değerdir.

    - İçin bir <xref:System.Xaml.XamlXmlReader.NodeType%2A> , <xref:System.Xaml.XamlNodeType.NamespaceDeclaration>, çağrı <xref:System.Xaml.XamlXmlReader.Namespace%2A> bir ad alanı düğümü için ad alanı bilgileri elde etmek için.

- Çağrı <xref:System.Xaml.XamlXmlReader.Read%2A> XAML okuyucu XAML düğüm akış sonraki düğümü geçin ve yeniden adımları tekrarlayın.

.NET Framework XAML Hizmetleri XAML okuyucular tarafından her zaman sağlanan XAML düğümü akışı, tüm olası düğümlerinin tam ve kapsamlı bir geçişi sağlar. XAML düğümü Döngü için tipik bir akış denetimi teknikler kullanılabilir gövdesi içinde tanımlama `while (reader.Read())`ve geçme konusunda <xref:System.Xaml.XamlXmlReader.NodeType%2A> her düğümde düğüm döngüde gelin.

Düğümü akışı dosya sonunda ise, geçerli düğüm null olur.

Okuyucu ve yazıcı kullanan basit döngüsünü aşağıdaki örneğe benzer.

```csharp
XamlXmlReader xxr = new XamlXmlReader(new StringReader(xamlStringToLoad));
//where xamlStringToLoad is a string of well formed XAML
XamlObjectWriter xow = new XamlObjectWriter(xxr.SchemaContext);
while (xxr.Read()) {
  xow.WriteNode(xxr);
}
```

Bu temel örnek, bir yükleme yolu XAML düğüm döngünün XAML okuyucu ve yazıcı XAML şeffaf bir şekilde bağlanır, eğer farklı bir şey yapmak, kullanmışsınız <xref:System.Xaml.XamlServices.Parse%2A?displayProperty=nameWithType>. Ancak, bu temel yapı okuma veya yazma senaryoyu uygulamak için genişletilir. Bazı olası senaryolar aşağıdaki gibidir:

- Anahtarı'nda <xref:System.Xaml.XamlXmlReader.NodeType%2A>. Bağlı olarak hangi düğümün türü okunan farklı eylemleri gerçekleştirin.

- Çağırmayın <xref:System.Xaml.XamlWriter.WriteNode%2A> tüm durumlarda. Yalnızca çağrı <xref:System.Xaml.XamlWriter.WriteNode%2A> bazı <xref:System.Xaml.XamlXmlReader.NodeType%2A> durumları.

- Mantık belirli düğüm türü için içinde o düğümün ayrıntılarını analiz edin ve bunlar üzerinde harekete. Örneğin, belirli bir XAML ad alanından gelen ve ardından bırakın ya da herhangi bir nesne değil, XAML ad alanından erteleme nesneleri yazabilirsiniz. Veya bırakın veya aksi halde XAML sisteminizi desteklemediği bir XAML yönergeleri işleme üyelik bir parçası olarak yeniden işleme.

- Özel tanımlama <xref:System.Xaml.XamlObjectWriter> , geçersiz kılmalar `Write*` yöntemleri, büyük olasılıkla XAML şema içeriği atlar tür eşlemesi gerçekleştirme.

- Oluşturmak <xref:System.Xaml.XamlXmlReader> özelleştirilmiş XAML davranış farklılıkları hem okuyucu ve yazıcı tarafından kullanılan varsayılan XAML şema içeriği kullanılacak.

### <a name="accessing-xaml-beyond-the-node-loop-concept"></a>XAML düğümü Döngü kavramı ötesinde erişme

XAML düğümü döngü olarak dışındaki bir XAML gösterimi ile çalışmak için büyük olasılıkla farklı yöntemleri vardır. Örneğin, var dizinli bir düğüm okuyabilir veya özellikle erişen düğümleri ile doğrudan bir XAML okuyucu `x:Name`tarafından `x:Uid`, ya da diğer tanımlayıcılarla aracılığıyla. .NET framework XAML hizmetlerinde tam bir uygulamayı sağlamaz, ancak önerilen bir modeli Hizmetleri ve Destek türleri aracılığıyla sağlar. Daha fazla bilgi için bkz. <xref:System.Xaml.IXamlIndexingReader> ve <xref:System.Xaml.XamlNodeList>.

> [!TIP]
> Microsoft ayrıca Microsoft XAML Araç Seti bilinen bir bant dışı yayın oluşturur. Yayın öncesi aşamalı olarak yine de bu bant dışı sürümdür. Ancak, yayın öncesi bileşenleri ile çalışmak istekliyse Microsoft XAML Araç Seti bazı ilginç kaynaklar XAML araçları ve XAML statik analizini sağlar. Bir XAML DOM API'yi Microsoft XAML Araç Seti içeren, FxCop analizi ve XAML şema içeriği için Silverlight için destek. Daha fazla bilgi için [Microsoft XAML Araç Seti](https://code.msdn.microsoft.com/XAML).

<a name="working_with_the_current_node"></a>

## <a name="working-with-the-current-node"></a>Geçerli düğüm ile çalışma

XAML düğümü Döngü kullanan Çoğu senaryoda, yalnızca düğümlerin okunmaz. Çoğu senaryoda geçerli düğümleri işlemek ve her düğüm uygulaması için teker teker geçirmek <xref:System.Xaml.XamlWriter>.

Tipik bir yükleme yolu senaryosunda bir <xref:System.Xaml.XamlXmlReader> bir XAML düğüm akış üretir; XAML düğümleri, mantıksal ve XAML şema içeriği; göre işlenir ve düğümleri geçirilen bir <xref:System.Xaml.XamlObjectWriter>. Uygulamanızı veya framework sonra elde edilen Nesne grafiği tümleştirin.

Tipik bir kaydetme yolu senaryosu, bir <xref:System.Xaml.XamlObjectReader> Nesne grafiğini okur, tek tek XAML düğümleri işlenir ve bir <xref:System.Xaml.XamlXmlWriter> XAML metin dosyası olarak seri hale getirilmiş sonuç verir. Yolları hem senaryoları ile tam olarak bir XAML düğümü aynı anda ve XAML düğümleri XAML tür sistemi ve.NET Framework XAML Hizmetleri API tarafından tanımlanan standartlaştırılmış bir şekilde işlenmesi için kullanılabilir çalışma içeren anahtardır.

### <a name="frames-and-scope"></a>Çerçeve ve kapsamı

XAML düğümü Döngü doğrusal bir şekilde XAML düğümü akışı gösterilir. Düğümü akışı nesneleri, diğer nesneleri kapsamak ve benzeri üye olarak erişir. Genellikle, XAML düğümü akışı kapsamında bir çerçeve ve yığın kavramı uygulayarak izlemek yararlıdır. İçinde çalışırken düğümü akışı ayarlama etkin, bu özellikle doğrudur. Çerçeve ve yığın düğümü Döngü mantığınızın bir parçası sayısı gibi uygulama destek `StartObject` (veya `GetObject`) ve `EndObject` kapsamları yapısı bir DOM açısından zorlayıcı, XAML düğümü yapısına düzen gibi.

<a name="traversing_and_entering_object_nodes"></a>

## <a name="traversing-and-entering-object-nodes"></a>Geçiş yapma ve nesne düğümleri girme

XAML okuyucu tarafından açıldığında bir düğümü akışı ilk düğümü kök nesnesinin Başlangıç nesnesi düğümüdür. Tanımına göre bu nesne bir tek bir nesne düğümü her zaman olduğu ve hiç eşlere sahiptir. Herhangi bir gerçek XAML örnek kök nesne, daha fazla nesne içeren bir veya daha fazla özelliklerine sahip olmayı tanımlanır ve üye düğümleri bu özelliklere sahip. Üye düğümlerinin düğümleri için bir veya daha fazla nesne veya bir değer düğüm bunun yerine aynı zamanda sonlandırabilir. Kök nesnenin, genellikle XAML metin biçimlendirme öznitelikleri olarak sözdizimsel olarak atanmış, ancak eşlemek, XAML ad kapsamları tanımlar bir `Namescope` XAML düğüm akış gösteriminde düğüm türü.

(Bu, .NET Framework'teki varolan türleri tarafından yedeklenmez rastgele XAML) aşağıdaki XAML örneği göz önünde bulundurun. Bu nesne modelinde varsayımında `FavorCollection` olduğu `List<T>` , `Favor`, `Balloon` ve `NoiseMaker` öğesine atanamaz olduğundan `Favor`, `Balloon.Color` özelliği destekli bir `Color` WPF nasıl tanımladığını benzer nesnesi bilinen rengi adları olarak renkleri ve `Color` öznitelik sözdizimi için bir tür dönüştürücüsü destekler.

|XAML biçimlendirme|Sonuçta elde edilen XAML düğümü akışı|
|-----------------|--------------------------------|
|`<Party`|`Namespace` düğüm için `Party`|
|`xmlns="PartyXamlNamespace">`|`StartObject` düğüm için `Party`|
|`<Party.Favors>`|`StartMember` düğüm için `Party.Favors`|
||`StartObject` düğüm için örtük `FavorCollection`|
||`StartMember` düğüm için örtük `FavorCollection` öğelerini özelliği.|
|`<Balloon`|`StartObject` düğüm için `Balloon`|
|`Color="Red"`|`StartMember` düğüm için `Color`<br /><br /> `Value` öznitelik değeri dize düğümü `"Red"`<br /><br /> `EndMember` için `Color`|
|`HasHelium="True"`|`StartMember` düğüm için `HasHelium`<br /><br /> `Value` öznitelik değeri dize düğümü `"True"`<br /><br /> `EndMember` için `HasHelium`|
|`>`|`EndObject` için `Balloon`|
|`<NoiseMaker>Loudest</NoiseMaker>`|`StartObject` düğüm için `NoiseMaker`<br /><br /> `StartMember` düğüm için `_Initialization`<br /><br /> `Value` başlatma değeri dize düğümü `"Loudest"`<br /><br /> `EndMember` düğüm için `_Initialization`<br /><br /> `EndObject` için `NoiseMaker`|
||`EndMember` düğüm için örtük `FavorCollection` öğelerini özelliği.|
||`EndObject` düğüm için örtük `FavorCollection`|
|`</Party.Favors>`|`EndMember` için `Favors`|
|`</Party>`|`EndObject` için `Party`|

XAML düğüm akış üzerinde aşağıdaki davranış güvenebilirsiniz:

- Varsa bir `Namespace` düğüm yoksa, bu akışa hemen önce eklenir `StartObject` XAML ad alanı ile bildirilen `xmlns`. Önceki tabloya ile XAML ve örnek düğümü akışı yeniden bakın. Bildirim nasıl `StartObject` ve `Namespace` düğümleri görünen metni işaretleme bildirimi konumlarını karşı yorumlanabileceğinden için. Bu temsilci, ad alanı düğümleri her zaman göründüğü önüne düğüm davranış düğüm akışında geçerlidir. Bu tasarım amacı, ad alanı bilgisi nesnesi yazıcılar için önemlidir ve nesne türü eşleştirme veya aksi halde gerçekleştirmek için nesne yazıcı denemeleri işlemeden önce bilinmesi gerekir ' dir. Uygulama kapsamı stream'de önüne XAML ad alanı bilgi verme, her zaman kendi sunulan sırayla düğüm akışa işlemek daha basit kılar.

- Yukarıdaki nedeniyle, onu bir veya daha fazla husustur `Namespace` , ilk genellikle gerçek biçimlendirme düğümleri başından geçiş değil okuma düğümleri `StartObject` kök.

- A `StartObject` düğüm arkasından `StartMember`, `Value`, ya da hemen `EndObject`. Hiçbir zaman hemen bir başkası tarafından sonrasında `StartObject`.

- A `StartMember` tarafından izlenen bir `StartObject`, `Value`, ya da hemen `EndMember`. Tarafından izlenebilir `GetObject`, nerede olduğunu değeri beklenen üst nesne var olan bir değerden gelmesini üyeleri için yerine `StartObject` yeni bir değer örneği. Tarafından da izlenebilir bir `Namespace` yaklaşan bir geçerli düğüm `StartObject`. Hiçbir zaman hemen bir başkası tarafından sonrasında `StartMember`.

- A `Value` düğümü değeri temsil eder; yok "EndValue" yoktur. Yalnızca izlenebilir bir `EndMember`.

    - XAML başlatma metin nesnesinin oluşturma tarafından kullanılan bir nesne değeri yapısında sonuçlanmaz. Bunun yerine bir üye için bir özel üye düğüm adlı `_Initialization` oluşturulur. ve bu üye düğümünü başlatma değer dizesi içerir. Varsa, `_Initialization` her zaman ilk olan `StartMember`. `_Initialization` XAML dil XAML namescope ile bazı XAML Hizmetleri gösterimleri, açıklamak için nitelenebilir `_Initialization` yedekleme türleri içinde tanımlanan bir özellik değil.

    - Üyenin değeri değerinin bir özniteliğini temsil eder. Sonunda olabilir bir değer dönüştürücü bu değer işleme dahil olan ve düz bir dize değeridir. Ancak, bu düğümü akışı XAML nesne yazıcısı işler kadar değerlendirilmez. XAML nesne yazıcısı gerekli XAML şema içeriği ve tür sistemi eşlemesi değer dönüştürmeleri için gerekli olan diğer destek sahiptir.

- Bir `EndMember` düğüm arkasından bir `StartMember` düğümü tarafından veya sonraki üyesi için bir `EndObject` düğümü üyesi sahibi.

- Bir `EndObject` düğüm arkasından bir `EndMember` düğümü. Tarafından da izlenebilir bir `StartObject` düğüm nesneleri, bir koleksiyonun öğeleri meslektaşlarınız olduğu durumlar için. Ya da tarafından izlenebilir bir `Namespace` yaklaşan bir geçerli düğüm `StartObject`.

    - Tüm düğüm akış kapatılırken benzersiz kullanım durumu için `EndObject` , kök herhangi bir şey tarafından izlenmiyor; okuyucu artık bitiş dosya, ve <xref:System.Xaml.XamlReader.Read%2A> döndürür `false`.

<a name="value_converters_and_the_xaml_node_stream"></a>

## <a name="value-converters-and-the-xaml-node-stream"></a>Değer dönüştürücüler ve XAML düğümü Stream

Bir değer dönüştürücü (değeri seri hale getiricileri genişletme dahil) bir tür dönüştürücüsü veya XAML tür sistemi üzerinden bir değer dönüştürücü olarak bildirilen özel başka bir sınıf, bir işaretleme uzantısı için genel bir terimdir. XAML düğümü akışı bir tür dönüştürücüsü kullanımı ve biçimlendirme uzantısı kullanımı çok farklı temsilleri olabilir.

### <a name="type-converters-in-the-xaml-node-stream"></a>XAML düğümü Stream içinde tür dönüştürücüleri

Bir öznitelik, sonunda bir tür dönüştürücüsü kullanımı sonuçları raporlanır, XAML düğüm akış içinde bir üye değeri olarak ayarlayın. XAML düğümü akışı bir tür dönüştürücüsü örneği nesnesi üretir ve değeri geçirin denemez. Bir tür dönüştürücüsü 's dönüştürme uygulamasını kullanarak çağırma XAML şema içeriği ve tür eşlemesi için kullanarak gerektirir. Hangi tür dönüştürücü sınıfı değeri işlemek için kullanılması gereken bile belirleme XAML şema içeriği dolaylı olarak gerektirir. Varsayılan XAML şema içeriği kullandığınızda, bu bilgileri XAML tür sisteminden kullanılabilir. XAML yazıcı bağlantı önce XAML düğüm akış düzeyinde türü dönüştürücü sınıf bilgileri gerekiyorsa, buradan edinebilirsiniz <xref:System.Xaml.XamlMember> ayarlanan üye bilgileri. Ancak Aksi takdirde, XAML şema içeriği ve tür eşlemesi sistemi gerektiren işlemler geri kalanında gerçekleştirilinceye kadar türü dönüştürücü giriş XAML düğüm akış içinde düz bir değer olarak korunması, örneğin bir XAML ile nesne oluşturma nesne yazıcı.

Örneğin, aşağıdaki sınıf tanımı anahat ve XAML kullanım için göz önünde bulundurun:

```csharp
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

Bu kullanım için XAML düğümü akışı metin temsili aşağıdaki ifade edilebilir:

`StartObject` ile <xref:System.Xaml.XamlType> temsil eden `GameBoard`

`StartMember` ile <xref:System.Xaml.XamlMember> temsil eden `BoardSize`

`Value` düğümle metin dizesi "`8x8`"

`EndMember` Eşleşme `BoardSize`

`EndObject` Eşleşme `GameBoard`

Bu düğüm stream'de hiçbir tür dönüştürücü örnek olduğuna dikkat edin. Ancak çağırarak türü dönüştürücü bilgi edinebilirsiniz <xref:System.Xaml.XamlMember.TypeConverter%2A?displayProperty=nameWithType> üzerinde <xref:System.Xaml.XamlMember> için `BoardSize`. Geçerli bir XAML şema içeriği varsa, ayrıca dönüştürücü yöntemleri bir örneği elde ederek çağırabilirsiniz <xref:System.Xaml.Schema.XamlValueConverter%601.ConverterInstance%2A>.

### <a name="markup-extensions-in-the-xaml-node-stream"></a>XAML düğümü Stream biçimlendirme uzantıları

Biçimlendirme uzantısı kullanımı XAML düğüm akış nesnenin bir işaretleme uzantısı örneğinin temsil ettiği, bir üye içerisindeki bir nesne düğümü olarak bildirilir. Bu nedenle bir tür dönüştürücüsü kullanımı, daha fazla bilgi taşıyan değerinden ve biçimlendirme uzantısı kullanımı daha açık düğüm stream gösteriminde sunulur. <xref:System.Xaml.XamlMember> Kullanım durumsal ve her olası biçimlendirme durumda değişir olduğundan bilgileri, her şeyi işaretleme uzantısı hakkında bir uyarıyla değil; tür dönüştürücüleri olduğu gibi adanmış ve örtük tür veya üye başına değil.

Biçimlendirme uzantısı kullanımı (genellikle söz konusu olduğu) XAML metni işaretleme öznitelik formunda yapılan bile biçimlendirme uzantıları düğümü akışı temsili nesne düğümleri olarak durumdur. Aynı şekilde kullanılan bir açık nesne öğesi biçiminde biçimlendirme uzantısı kullanımı kabul edilir.

Bir işaretleme uzantısı nesne düğümü içinde bu işaretleme uzantısı üyeleri olabilir. XAML düğümü akışı temsili, biçimlendirme uzantısı kullanımı, konumsal parametre kullanımı ya da açıkça adlandırılmış parametrelerle bir kullanım oluşmasından korur.

Konumsal parametresi kullanım için XAML düğümü akışı XAML dili tarafından tanımlanan bir özellik içeren `_PositionalParameters` kullanım kayıtları. Bu özellik, genel <xref:System.Collections.Generic.List%601> ile <xref:System.Object> kısıtlaması. Kısıtlama nesnesi ve dize değil çünkü kısıtlanmamışsa konumsal parametre kullanımı içindeki iç içe geçmiş biçimlendirme uzantısı kullanımı içerebilir. Konumsal parametreler kullanımdan erişmek için listede yinelemek ve dizin oluşturucular için tek tek liste değerleri kullanın.

Adlandırılmış parametre kullanımı için her adlandırılmış parametre düğüm stream'de bu ada sahip bir üye düğümü olarak temsil edilir. İç içe geçmiş biçimlendirme uzantısı kullanımı olabileceğinden üye değerlerinin, dizeler desteklenmez.

`ProvideValue` biçimlendirmeden uzantısı henüz çağrılmaz. Ancak, XAML okuyucu ve yazıcı XAML bağlanmanız durumunda çağrılan böylece `WriteEndObject` düğüm stream'de incelediğinizde işaretleme uzantısı düğüm üzerinde çağrılır. Bu nedenle, genellikle aynı XAML şema içeriği yükleme yolunda Nesne grafiği oluşturmak için kullanılan kullanılabilir gerekir. Aksi takdirde, `ProvideValue` beklenen Hizmetleri kullanılabilir olmadığından hiçbir biçimlendirmeden özel durumlar, burada uzantı oluşturabilecek.

<a name="xaml_and_xml_languagedefined_members_in_the_xaml_node_stream"></a>

## <a name="xaml-and-xml-language-defined-members-in-the-xaml-node-stream"></a>XAML ve XML dili tarafından tanımlanan üyeleri XAML düğümü Stream

Belirli üyeleri bir XAML düğümü akışı yorumlar ve bir XAML okuyucu kuralları nedeniyle yerine açık bir sunulan <xref:System.Xaml.XamlMember> arama veya oluşturma. Genellikle, bu üyeler XAML yönergeleridir. Bazı durumlarda, XAML düğümü akışı yönergesi tanıtan XAML okuma işlemidir. Diğer bir deyişle, özgün XAML metni member yönergesi açıkça belirtilmedi, ancak XAML okuyucu bu bilgileri kaybolur önce bir yapısal XAML kuralı ve rapor bilgilerinde XAML düğümü akışı karşılamak için yönergesi ekler girin.

Aşağıdaki liste notları tüm durumlarda bir yönerge XAML üye düğümünü tanıtmak için bir XAML okuyucu burada beklenir ve bu üye düğümünü .NET Framework XAML hizmetlerinde uygulamalarında nasıl tanımlanır.

- **Bir nesne düğümü başlatma metni:** Bu üye düğümün adı `_Initialization`temsil ettiği bir XAML yönerge ve XAML dil XAML ad alanında tanımlanır. Buradan için statik bir varlığı alabilirsiniz <xref:System.Xaml.XamlLanguage.Initialization%2A>.

- **İşaretleme uzantısı için konumsal Parametreler:** Bu üye düğümün adı `_PositionalParameters`, XAML dili XAML ad alanında tanımlanır. Her zaman her biri üzerinde ayırarak, önceden ayrılmış konumsal bir parametresi olan bir genel liste nesnelerin içerdiği `,` XAML girişinde sağlanan olarak sınırlayıcı karakter. Konumsal parametreler yönergesinden kaynaklandığından için statik bir varlığı alabilirsiniz <xref:System.Xaml.XamlLanguage.PositionalParameters%2A>.

- **Bilinmeyen içeriği:** Bu üye düğümün adı `_UnknownContent`. NET olarak söylemek gerekirse, olan bir <xref:System.Xaml.XamlDirective>, XAML dili XAML ad alanında tanımlanır. Bu yönerge, burada kaynak XAML İçerik XAML nesne öğesi içeriyor, ancak hiçbir içerik özelliği şu anda kullanılabilir XAML şema içeriği altında belirlenebilir durumlarda bir sentinel kullanılır. XAML düğümü akışı bu durumda adlı üye için kontrol ederek algılayabilir `_UnknownContent`. Bir yükleme yolu XAML düğüm akış varsayılan başka hiçbir işlem yapılmazsa <xref:System.Xaml.XamlObjectWriter> denenen oluşturur `WriteEndObject` karşılaştığında `_UnknownContent` herhangi bir nesne üzerinde üyesi. Varsayılan <xref:System.Xaml.XamlXmlWriter> oluşturmaz ve üyeyi örtük olarak değerlendirir. Statik bir varlık için alabilirsiniz `_UnknownContent` gelen <xref:System.Xaml.XamlLanguage.UnknownContent%2A>.

- **Koleksiyon özelliği bir koleksiyonun:** destekleyen CLR türünü XAML için genellikle kullanılan bir koleksiyon sınıfının özel koleksiyon öğelerini tutan adlı olsa da, bu özellik türü yedekleme önce bir XAML tür sistemi bilinen bir durum Çözüm. Bunun yerine, XAML düğümü akışı tanıtır bir `Items` yer tutucu XAML türü koleksiyonunun bir üyesi olarak. Bu yönerge, .NET Framework XAML hizmetlerinde uygulamasında adı / düğüm stream'de üyesidir `_Items`. Bu yönerge için bir sabit örneğinden alınabilen <xref:System.Xaml.XamlLanguage.Items%2A>.

    XAML düğümü akışı ayrıştırılabilir olmaması kapatma öğeleri içeren bir Items özelliğini içerebilir yedekleme tür çözümlemesi ve XAML şema içeriği göre unutmayın. Örneğin,

- **XML tarafından tanımlanan Üyeler:** XML tanımlı `xml:base`, `xml:lang` ve `xml:space` üyeleri adlı XAML yönergeleri olarak bildirilen `base`, `lang`, ve `space` .NET Framework XAML hizmetlerinde uygulamalarında. Bu ad alanı XML ad alanı `http://www.w3.org/XML/1998/namespace`. Bunların her biri için sabitler elde edilebilir gelen <xref:System.Xaml.XamlLanguage>.

## <a name="node-order"></a>Düğüm sırası

Bazı durumlarda, <xref:System.Xaml.XamlXmlReader> XAML düğümlerinin düğümleri işaretlemede görüntülerse veya XML olarak işlenen görüntülenme sırasını karşı XAML düğüm akış sırasını değiştirir. Bu düğümler sipariş için gerçekleştirilir gibi bir <xref:System.Xaml.XamlObjectWriter> düğümü akışı yalnızca ileriye doğru bir şekilde işleyebilir.  .NET Framework XAML hizmetlerinde XAML okuyucu düğümleri bu görevi, performans iyileştirme düğümü akışı XAML nesne yazıcı Tüketiciler için XAML yazıcı için bırakmak yerine yeniden sıralar.

Belirli yönergeleri, özellikle daha fazla bilgi için bir nesneden bir nesne öğesi oluşturulmasını sağlamak için tasarlanmıştır. Bu yönergeler şunlardır: `Initialization`, `PositionalParameters`, `TypeArguments`, `FactoryMethod`, `Arguments`. Bu yönergeler, bir nesnenin aşağıdaki düğüm stream'de ilk üye olarak yerleştirmek .NET Framework XAML Hizmetleri XAML okuyucular denemesi `StartObject`, sonraki bölümde açıklanan nedenlerle.

### <a name="xamlobjectwriter-behavior-and-node-order"></a>XamlObjectWriter davranışı ve düğüm sırası

`StartObject` için bir <xref:System.Xaml.XamlObjectWriter> mutlaka hemen nesne örneği oluşturmak için bir sinyal için XAML nesne yazıcısı değil. XAML ek Giriş bir nesne başlatmak ve ilk nesnesi ve ardından yalnızca ayarı özellikleri oluşturmak için varsayılan bir oluşturucu tamamen çağırmaya dayanması değil olanaklı kılan birçok dil özellikleri içerir. Bu özellikler şunları içerir: <xref:System.Windows.Markup.XamlDeferLoadAttribute>; başlatma metin; [x: TypeArguments](../../../docs/framework/xaml-services/x-typearguments-directive.md); konumsal bir işaretleme uzantısı parametre; Fabrika yöntemleri ve ilişkili [x: Arguments](../../../docs/framework/xaml-services/x-arguments-directive.md) düğümleri (XAML 2009). Her durumda gerçek nesnenin yapımı gecikme ve XAML nesne yazıcısı düğümü akışı yeniden olduğundan, özellikle bir yapım olmayan bir başlangıç üyesi karşılaşıldığında, aslında örneği oluşturma davranışı güvenebilirsiniz nesne türüne yönergesi.

### <a name="getobject"></a>GetObject

`GetObject` Yeni bir nesne oluşturmak yerine bir XAML nesne yazıcısı bunun yerine nesnenin içeren özelliğinin değeri nereden bir XAML düğümünü temsil eder. Tipik bir servis talebi burada bir `GetObject` düğüm karşılaşıldığında içeren özellik yedekleme türün nesne modelinde salt okunur kasıtlı olarak bir XAML düğüm akış koleksiyon nesnesi veya bir sözlük nesnesi olur. Bu senaryoda, koleksiyona veya sözlüğe genellikle oluşturulur ve başlatıldı (genellikle boş) sahip olan bir türü başlatma mantığı tarafından.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xaml.XamlObjectReader>
- [XAML Hizmetleri](../../../docs/framework/xaml-services/index.md)
- [XAML Ad Alanları](../../../docs/framework/xaml-services/xaml-namespaces-for-net-framework-xaml-services.md)
