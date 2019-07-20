---
title: XAML Düğüm Akış Yapılarını ve Kavramlarını Anlama
ms.date: 03/30/2017
helpviewer_keywords:
- XAML node streams [XAML Services]
- nodes [XAML Services], XAML node stream
- XAML [XAML Services], XAML node streams
ms.assetid: 7c11abec-1075-474c-9d9b-778e5dab21c3
ms.openlocfilehash: c873961982cd1642d8b354e5d77b06105c0b7a1e
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2019
ms.locfileid: "68364315"
---
# <a name="understanding-xaml-node-stream-structures-and-concepts"></a>XAML Düğüm Akış Yapılarını ve Kavramlarını Anlama

.NET Framework XAML hizmetlerinde uygulanan xaml okuyucuları ve XAML yazarları, XAML düğüm akışının tasarım kavramını temel alır. XAML düğüm akışı, bir dizi XAML düğümü için bir dizi kavramsalization. Bu conceptuselte, bir XAML işlemcisi XAML içindeki düğüm ilişkilerinin yapısını birer birer gösterir. Herhangi bir zamanda, açık bir XAML düğüm akışında yalnızca bir adet geçerli kayıt veya geçerli konum bulunur ve API 'nin birçok yönü yalnızca ilgili konumdan kullanılabilen bilgileri rapor ediyor. Bir XAML düğüm akışındaki geçerli düğüm bir nesne, üye veya değer olarak açıklanabilir. Xaml okuyucular bir XAML düğüm akışı olarak davranarak XAML yazarları ile iletişim kurabilir ve bir programın bir yük yolu ya da XAML içeren bir yol kaydetme işlemi sırasında XAML düğüm akışının içeriğini görüntülemesini, bunlarla etkileşime geçmesini veya değiştirmesini sağlayabilir. Xaml okuyucu ve yazıcı API 'si tasarımı ve xaml düğüm akışı kavramı, [!INCLUDE[TLA#tla_xmldom](../../../includes/tlasharptla-xmldom-md.md)] <xref:System.Xml.XmlReader> ve <xref:System.Xml.XmlWriter> ve sınıfları gibi önceki ilgili okuyucu ve yazıcı tasarımlarına ve kavramlarına benzerdir. Bu konu XAML düğüm akışı kavramlarını ve xaml düğüm düzeyinde xaml temsilleri ile etkileşime geçen yordamları nasıl yazacağınız açıklanmaktadır.

<a name="loading_into_a_xaml_reader"></a>

## <a name="loading-xaml-into-a-xaml-reader"></a>Xaml 'yi XAML okuyucusuna yükleme

Temel <xref:System.Xaml.XamlReader> sınıf, ilk xaml 'yi bir xaml okuyucusuna yüklemek için belirli bir teknik bildirmiyor. Bunun yerine, türetilmiş bir sınıf, XAML için giriş kaynağının genel özellikleri ve kısıtlamaları dahil olmak üzere yükleme tekniğini bildirir ve uygular. Örneğin, bir nesnesi <xref:System.Xaml.XamlObjectReader> , kökü veya tabanı temsil eden tek bir nesnenin giriş kaynağından başlayarak bir nesne grafiğini okur. <xref:System.Xaml.XamlObjectReader> Ardından nesne grafiğinden bir xaml düğüm akışı üretir.

En belirgin .NET Framework xaml Hizmetleri – tanımlı <xref:System.Xaml.XamlReader> <xref:System.Xaml.XamlXmlReader>alt sınıf. <xref:System.Xaml.XamlXmlReader>bir metin dosyasını doğrudan bir akış veya dosya yoluyla yükleyerek ya da gibi ilgili bir okuyucu sınıfı aracılığıyla dolaylı olarak <xref:System.IO.TextReader>ilk xaml 'yi yükler. <xref:System.Xaml.XamlReader> Yüklendikten sonra XAML giriş kaynağının tamamen bulunduğu düşünülebilir. Ancak, <xref:System.Xaml.XamlReader> temel API, okuyucunun tek bir xaml düğümüyle etkileşimde bulunmak için tasarlanmıştır. İlk yüklendiğinde, karşılaştığınız ilk tek düğüm XAML 'in ve başlangıç nesnesinin köküdür.

### <a name="the-xaml-node-stream-concept"></a>XAML düğüm akışı kavramı

XML tabanlı teknolojilerle ilgili bir DOM, ağaç metaphor veya sorgu tabanlı yaklaşım hakkında genel olarak daha fazla bilginiz varsa, XAML düğüm akışının kavramaya yönelik faydalı bir yolu aşağıdaki gibidir. Yüklenen XAML 'nin bir DOM veya her olası düğümün her şekilde genişletildiği bir ağaç olduğunu düşünün ve ardından ilk olarak sunulur. Düğümlerde ilerlettikçe, bir DOM ile ilgili olacak düzeylerin "içinde" veya "Out" şeklinde geçiş yapabilirsiniz, ancak bu düzey kavramlar bir düğüm akışıyla ilgili olmadığından XAML düğüm akışı açıkça izlenmez. Düğüm akışı "geçerli" bir konuma sahiptir, ancak akışın diğer bölümlerini başvuru olarak depolamadığınız sürece, düğüm akışının geçerli düğüm konumu dışındaki her yönü görünüm dışında olur.

XAML düğüm akışı kavramı, tüm düğüm akışının tamamına giderseniz, tüm XAML gösterimini işlemenize emin olduğunuz için önemli bir avantajdır. bir sorgunun, DOM işleminin veya işleme bilgileri ile ilgili başka bir doğrusal yaklaşımın, tüm XAML gösteriminin bir parçasını kaçırmadığından endişelenmeniz gerekmez. Bu nedenle, xaml düğüm akışı temsili hem XAML okuyucuları hem XAML yazıcılarını bağlamak için idealdir ve bir XAML işleme işleminin okuma ve yazma aşamaları arasında davranan kendi işleminizi ekleyebileceğiniz bir sistem sağlamak için idealdir. Çoğu durumda, XAML düğüm akışındaki düğümlerin sıralaması, XAML okuyucular tarafından kasıtlı olarak iyileştirilir veya yeniden sıralanabilir ve bu da sıranın kaynak metin, ikili veya nesne grafiğinde nasıl görünebileceğini de gösterebilir. Bu davranış, XAML yazıcılarının düğüm akışında "geri" gitmesi gereken bir konumda yer aldığı bir XAML işleme mimarisini zorlamak için tasarlanmıştır. İdeal olarak, tüm XAML yazma işlemleri şema bağlamına ve düğüm akışının geçerli konumuna göre işlem yapabilmelidir.

<a name="a_basic_reading_node_loop"></a>

## <a name="a-basic-reading-node-loop"></a>Temel bir okuma düğümü döngüsü

XAML düğüm akışını incelemek için temel bir okuma düğümü döngüsü aşağıdaki kavramlardan oluşur. Bu konuda anlatıldığı gibi düğüm döngülerinin amaçları doğrultusunda, kullanarak <xref:System.Xaml.XamlXmlReader>metin tabanlı, okunabilir xaml dosyalarını okudığınızı varsayalım. Bu bölümdeki bağlantılar tarafından <xref:System.Xaml.XamlXmlReader>uygulanan belirli xaml düğüm döngüsü API 'sine başvurur.

- XAML düğüm akışının sonunda olmadığından emin olun (Check <xref:System.Xaml.XamlXmlReader.IsEof%2A>veya <xref:System.Xaml.XamlXmlReader.Read%2A> Return Value kullanın). Akışın sonunda yer alıyorsa, geçerli bir düğüm yoktur ve çıkış yapmanız gerekir.

- ' İ çağırarak <xref:System.Xaml.XamlXmlReader.NodeType%2A>xaml düğüm akışının ne tür bir düğümde olduğunu denetleyin.

- Doğrudan bağlanmış ilişkili bir xaml nesne yazıcınız varsa, genellikle bu noktada çağrı <xref:System.Xaml.XamlWriter.WriteNode%2A> yapılır.

- Geçerli düğüm veya <xref:System.Xaml.XamlNodeType> geçerli kayıt olarak bildirilen temel alınarak, düğüm içerikleri hakkında bilgi almak için aşağıdakilerden birini çağırın:

  - <xref:System.Xaml.XamlXmlReader.NodeType%2A> <xref:System.Xaml.XamlXmlReader.Member%2A> Veya ' de, bir üye hakkında bilgi <xref:System.Xaml.XamlMember> almak için çağrısı yapın. <xref:System.Xaml.XamlNodeType.EndMember> <xref:System.Xaml.XamlNodeType.StartMember> Üyenin bir <xref:System.Xaml.XamlDirective>olabileceğini ve bu nedenle önceki nesnenin geleneksel tür tanımlı bir üyesi olması gerekebileceğini unutmayın. Örneğin, `x:Name` bir nesneye uygulanan bir xaml <xref:System.Xaml.XamlMember.IsDirective%2A> üyesi olarak ve üyenin `Name`, <xref:System.Xaml.XamlMember.Name%2A> bu yönergenin xaml Language xaml ad alanı altında olduğunu belirten diğer özelliklerle birlikte görüntülenir.

  - <xref:System.Xaml.XamlNodeType.StartObject> Veya <xref:System.Xaml.XamlXmlReader.NodeType%2A> <xref:System.Xaml.XamlXmlReader.Type%2A> <xref:System.Xaml.XamlType> ' de,birnesnesihakkındabilgialmakiçinçağrısıyapın.<xref:System.Xaml.XamlNodeType.EndObject>

  - İçin bir <xref:System.Xaml.XamlXmlReader.NodeType%2A> <xref:System.Xaml.XamlNodeType.Value> çağrısı<xref:System.Xaml.XamlXmlReader.Value%2A>yapın. Düğüm yalnızca bir üye için bir değerin en basit ifadesi veya bir nesnenin başlatma metni ise bir değerdir (ancak, bu konunun yakında yaklaşan bölümünde belgelenen tür dönüştürme davranışının farkında olmanız gerekir).

  - İçin, bir ad alanı düğümü için ad alanı bilgilerini almak üzere çağırın <xref:System.Xaml.XamlXmlReader.Namespace%2A>. <xref:System.Xaml.XamlXmlReader.NodeType%2A> <xref:System.Xaml.XamlNodeType.NamespaceDeclaration>

- Xaml <xref:System.Xaml.XamlXmlReader.Read%2A> okuyucuyu xaml düğüm akışındaki bir sonraki düğüme ilerletmek için çağrı yapın ve adımları tekrar tekrarlayın.

.NET Framework XAML Hizmetleri XAML okuyucuları tarafından sağlanan XAML düğüm akışı her zaman tüm olası düğümlerin tam ve derin bir çapraz geçişini sağlar. XAML düğüm döngüsü için tipik akış denetimi teknikleri, içinde `while (reader.Read())`bir gövde tanımlamayı ve düğüm döngüsünde her düğüm noktasında <xref:System.Xaml.XamlXmlReader.NodeType%2A> değiştirmeyi içerir.

Düğüm akışı dosyanın sonunda ise, geçerli düğüm null olur.

Bir okuyucu ve yazıcı kullanan en basit döngü aşağıdaki örneğe benzer.

```csharp
XamlXmlReader xxr = new XamlXmlReader(new StringReader(xamlStringToLoad));
//where xamlStringToLoad is a string of well formed XAML
XamlObjectWriter xow = new XamlObjectWriter(xxr.SchemaContext);
while (xxr.Read()) {
  xow.WriteNode(xxr);
}
```

Bir load path XAML düğümü döngüsünün bu temel örneği, XAML okuyucuyu ve XAML yazıcısını saydam bir şekilde bağlayarak, kullandıysanız <xref:System.Xaml.XamlServices.Parse%2A?displayProperty=nameWithType>kullanmaktan farklı hiçbir şey yapmaz. Ancak bu temel yapı daha sonra okuma veya yazma senaryonuz için geçerlidir. Olası bazı senaryolar aşağıdaki gibidir:

- Üzerinde <xref:System.Xaml.XamlXmlReader.NodeType%2A>geçiş yapın. Hangi düğüm türünün okunmakta olduğuna bağlı olarak farklı eylemler gerçekleştirin.

- Her durumda çağırmayın <xref:System.Xaml.XamlWriter.WriteNode%2A> . Yalnızca bazı <xref:System.Xaml.XamlWriter.WriteNode%2A> <xref:System.Xaml.XamlXmlReader.NodeType%2A> durumlarda çağrı yapın.

- Belirli bir düğüm türünün mantığı içinde, bu düğümün özelliklerini çözümleyin ve üzerinde işlem yapın. Örneğin, yalnızca belirli bir XAML ad alanından gelen nesneleri yazabilir ve ardından bu XAML ad alanından olmayan nesneleri bırakabilir veya erteleyebilirsiniz. Ya da XAML sisteminizin üye işlemenin bir parçası olarak desteklemediği XAML yönergelerini bırakabilir veya başka bir şekilde yeniden işleyebilirsiniz.

- Muhtemelen xaml şema <xref:System.Xaml.XamlObjectWriter> bağlamını atlayan `Write*` tür eşlemesi gerçekleştiren yöntemleri geçersiz kılan özel bir tanımlar.

- <xref:System.Xaml.XamlXmlReader> Öğesini varsayılan olmayan xaml şema bağlamını kullanacak şekilde oluşturun, böylece xaml davranışında özelleştirilmiş farklılıklar hem okuyucu hem de yazıcı tarafından kullanılır.

### <a name="accessing-xaml-beyond-the-node-loop-concept"></a>Düğüm döngüsü kavramının ötesinde XAML 'e erişme

XAML düğüm döngüsü dışında bir XAML temsili ile çalışmanın diğer olası yolları vardır. Örneğin, dizine alınmış bir düğümü okuyabilen bir XAML okuyucusu veya özel erişim düğümlerine, ya `x:Name` `x:Uid`da diğer tanımlayıcılara göre doğrudan erişebilir. .NET Framework XAML Hizmetleri tam uygulama sağlamaz, ancak hizmetler ve destek türleri aracılığıyla önerilen bir model sağlar. Daha fazla bilgi için bkz. <xref:System.Xaml.IXamlIndexingReader> ve <xref:System.Xaml.XamlNodeList>.

> [!TIP]
> Microsoft, Microsoft XAML araç seti olarak bilinen bir bant dışı yayın da üretir. Bu bant dışı sürüm, hala yayın öncesi aşamalarda bulunur. Ancak, yayın öncesi bileşenleriyle çalışmak istiyorsanız, Microsoft XAML araç seti XAML araçları ve XAML 'nin statik analizi için bazı ilginç kaynaklar sağlar. Microsoft XAML araç seti bir XAML DOM API 'SI, FxCop analizi desteği ve Silverlight için XAML şeması bağlamı içerir. Daha fazla bilgi için bkz. [MICROSOFT xaml araç seti](https://code.msdn.microsoft.com/XAML).

<a name="working_with_the_current_node"></a>

## <a name="working-with-the-current-node"></a>Geçerli düğümle çalışma

XAML düğümü döngüsü kullanan çoğu senaryo yalnızca düğümleri okummaz. Çoğu senaryo geçerli düğümleri işler ve her bir düğümü her seferinde bir uygulamasına <xref:System.Xaml.XamlWriter>iletir.

Tipik yükleme yolu senaryosunda, bir <xref:System.Xaml.XamlXmlReader> xaml düğüm akışı üretir; xaml düğümleri Logic ve xaml şema bağlamına göre işlenir ve düğümler bir <xref:System.Xaml.XamlObjectWriter>öğesine geçirilir. Daha sonra elde edilen nesne grafiğini uygulamanız veya çatısı ile tümleştirin.

Tipik bir <xref:System.Xaml.XamlObjectReader> kayıt yolu senaryosunda, nesne grafiğini okur, tek xaml düğümleri işlenir <xref:System.Xaml.XamlXmlWriter> ve serileştirilmiş sonuç bir xaml metin dosyası olarak çıktı verir. Anahtar, hem yolların hem de senaryoların tek seferde tam olarak bir XAML düğümü ile çalışmasını içerir ve XAML düğümleri XAML türü sistem ve the.NET Framework XAML Hizmetleri API 'Leri tarafından tanımlanan standartlaştırılmış bir şekilde kullanıma sunulmuştur.

### <a name="frames-and-scope"></a>Çerçeveler ve kapsam

XAML düğüm döngüsü, XAML düğüm akışını doğrusal bir şekilde gösterir. Düğüm akışı nesnelere, diğer nesneleri içeren üyelere ve bu şekilde devam eder. Bir çerçeve ve yığın kavramı uygulayarak XAML düğüm akışı içindeki kapsamı izlemek genellikle yararlıdır. Bu, özellikle düğüm akışını etkin olarak ayarlıyorsanız geçerlidir. Düğüm döngüsü mantığınızın bir parçası olarak uyguladığınız çerçeve ve yığın desteği, yapı bir DOM perspektifinden `StartObject` düşünülse `GetObject`de bir xaml düğüm yapısına son bakış halinde (veya) ve `EndObject` kapsamları saymanız olabilir.

<a name="traversing_and_entering_object_nodes"></a>

## <a name="traversing-and-entering-object-nodes"></a>Nesne düğümlerini geçme ve girme

Bir XAML okuyucusu tarafından açıldığında düğüm akışındaki ilk düğüm, kök nesnenin başlangıç nesnesi düğümüdür. Tanım olarak, bu nesne her zaman tek bir nesne düğümüdür ve bir eşi yoktur. Herhangi bir gerçek dünyada XAML örneğinde, kök nesnesi daha fazla nesne tutan bir veya daha fazla özelliğe sahip olacak şekilde tanımlanır ve bu özelliklerde üye düğümleri vardır. Daha sonra üye düğümleri bir veya daha fazla nesne düğümüne sahiptir veya bunun yerine bir değer düğümünde da sonlandırılabilir. Kök nesnesi genellikle xaml metin biçimlendirmesinde öznitelik olarak atanan, ancak xaml düğüm akışı temsilindeki bir `Namescope` düğüm türüyle eşlenen xaml namescopes 'yi tanımlar.

Aşağıdaki XAML örneğini göz önünde bulundurun (.NET Framework, bu rastgele XAML 'dir, bu, var olan türler tarafından yedeklenmez). Bu nesne modelinde `FavorCollection` `List<T>` , ve `Favor` `Balloon.Color` `Color` ' nin atanmakta olduğu varsayıyoruz ,özelliğiWPF'innasıltanımladığınabenzerbirnesnetarafındandesteklenir.`Favor` `Balloon` `NoiseMaker` bilinen renk adları olarak renkler, `Color` öznitelik sözdizimi için bir tür dönüştürücüyü destekler.

|XAML işaretleme|Sonuçta elde edilen XAML düğüm akışı|
|-----------------|--------------------------------|
|`<Party`|`Namespace`için düğüm`Party`|
|`xmlns="PartyXamlNamespace">`|`StartObject`için düğüm`Party`|
|`<Party.Favors>`|`StartMember`için düğüm`Party.Favors`|
||`StartObject`örtük için düğüm`FavorCollection`|
||`StartMember`örtük `FavorCollection` öğeler özelliği için düğüm.|
|`<Balloon`|`StartObject`için düğüm`Balloon`|
|`Color="Red"`|`StartMember`için düğüm`Color`<br /><br /> `Value`öznitelik değeri dizesinin düğümü`"Red"`<br /><br /> `EndMember` için `Color`|
|`HasHelium="True"`|`StartMember`için düğüm`HasHelium`<br /><br /> `Value`öznitelik değeri dizesinin düğümü`"True"`<br /><br /> `EndMember` için `HasHelium`|
|`>`|`EndObject` için `Balloon`|
|`<NoiseMaker>Loudest</NoiseMaker>`|`StartObject`için düğüm`NoiseMaker`<br /><br /> `StartMember`için düğüm`_Initialization`<br /><br /> `Value`başlatma değeri dizesinin düğümü`"Loudest"`<br /><br /> `EndMember`için düğüm`_Initialization`<br /><br /> `EndObject` için `NoiseMaker`|
||`EndMember`örtük `FavorCollection` öğeler özelliği için düğüm.|
||`EndObject`örtük için düğüm`FavorCollection`|
|`</Party.Favors>`|`EndMember` için `Favors`|
|`</Party>`|`EndObject` için `Party`|

XAML düğüm akışında aşağıdaki davranışa güvenebilirsiniz:

- Bir `Namespace` düğüm varsa, xaml ad alanını ile `xmlns`bildirdikten hemen `StartObject` önce akışa eklenir. XAML ve örnek düğüm akışının bulunduğu önceki tabloya bakın. `StartObject` Ve`Namespace` düğümlerinin, metin biçimlendirmesinde bildirim konumlarına göre nasıl konumlandırdığı gibi göründüğünü unutmayın. Bu, ad alanı düğümlerinin düğüm akışında için uygulanan düğümden önce her zaman göründüğü davranış temsilcisidir. Bu tasarımın amacı, ad alanı bilgilerinin nesne yazarları için hayati öneme sahip olması ve nesne yazıcısının tür eşlemesi gerçekleştirmeyi denemesi ya da nesneyi işlemesini denemeden önce bilinmesi gerekir. XAML ad alanı bilgilerini akıştaki uygulama kapsamının önüne koymak, her zaman düğüm akışının sunulma sırasında işlemesini daha kolay hale getirir.

- Yukarıdaki durumlar nedeniyle, köke `Namespace` `StartObject` göre değil, başlangıçtan itibaren düğümlerden geçiş yaparken çoğu gerçek dünya biçimlendirme durumunda ilk olarak okunan bir veya daha fazla düğümdür.

- `StartObject` Düğüm `StartMember`, veyahemen`EndObject`arkasından gelebilir. `Value` Hiç bir şekilde başka bir `StartObject`bu değil.

- Bir `StartMember` `StartObject`, ,veya`EndMember`hemen arkasından gelebilir. `Value` Değerin, yeni bir değer `GetObject`örneklenebilecek bir öğesi yerine üst nesnenin var olan bir `StartObject` değerinden gelmesi beklenen Üyeler için tarafından izlenebilir. Ayrıca, yaklaşan `Namespace` `StartObject`bir düğüm tarafından izlenebilir. Hiç bir şekilde başka bir `StartMember`bu değil.

- `Value` Düğüm, değerin kendisini temsil eder; "EndValue" yoktur. Bu, yalnızca bir `EndMember`ile izlenebilir.

  - Nesnenin XAML başlatma metni, oluşturma tarafından kullanılabilecek şekilde, nesne değeri yapısına neden olmaz. Bunun yerine, adlı `_Initialization` üye için adanmış bir üye düğümü oluşturulur. ve bu üye düğümü başlatma değeri dizesini içerir. Varsa, `_Initialization` her zaman ilk `StartMember`. `_Initialization`, bir xaml dili xaml namescope ile bazı xaml Hizmetleri temsillerine uygun olabilir ve bu `_Initialization` da, yedekleme türlerinde tanımlı bir özellik değildir.

  - Üye-değer birleşimi değerin bir öznitelik ayarını temsil eder. Sonuç olarak bu değeri işlemeye dahil bir değer Dönüştürücüsü olabilir ve değer düz bir dizedir. Ancak, bir XAML nesne yazıcısı bu düğüm akışını işleene kadar değerlendirilmez. XAML nesne yazarı, gerekli XAML şeması bağlamı, tür sistemi eşlemesi ve değer dönüştürmeleri için gereken diğer desteğe sahiptir.

- Düğüm, sonraki bir `StartMember` `EndObject` üye için düğüm veya üye sahibi için bir düğüm tarafından izlenebilir. `EndMember`

- Düğüm, bir `EndMember` düğüm tarafından izlenebilir. `EndObject` Ayrıca, nesnelerin bir koleksiyonun öğelerinde eşleri `StartObject` olduğu durumlar için bir düğüm tarafından izlenebilir. Ya da gelecekteki `Namespace` `StartObject`bir düğüm tarafından izlenebilir.

  - Tüm düğüm akışını kapatmakla ilgili benzersiz bir durum olması için, `EndObject` köke ait hiçbir şey uygulanmaz; okuyucu şimdi dosya sonu ve <xref:System.Xaml.XamlReader.Read%2A> döndürür `false`.

<a name="value_converters_and_the_xaml_node_stream"></a>

## <a name="value-converters-and-the-xaml-node-stream"></a>Değer dönüştürücüler ve XAML düğüm akışı

Değer Dönüştürücüsü, bir işaretleme uzantısı için genel bir terimdir, bir tür Dönüştürücüsü (değer serileştiriciler dahil) veya XAML tür sistemi aracılığıyla bir değer Dönüştürücüsü olarak bildirilen başka bir ayrılmış sınıf. XAML düğüm akışında, tür dönüştürücüsü kullanımı ve biçimlendirme uzantısı kullanımı çok farklı temsiller de vardır.

### <a name="type-converters-in-the-xaml-node-stream"></a>XAML düğüm akışında tür dönüştürücüler

Sonunda bir tür dönüştürücüsü kullanımıyla sonuçlanan bir öznitelik kümesi, XAML düğüm akışında bir üyenin değeri olarak raporlanır. XAML düğüm akışı, bir tür dönüştürücü örnek nesnesi üretmeyi ve değeri geçirmeye çalışmaz. Tür dönüştürücünün dönüştürme uygulamasının kullanılması için XAML şema bağlamını çağırma ve tür eşleme için kullanılması gerekir. Değeri işlemek için hangi tür dönüştürücü sınıfının kullanılması gerektiğini belirlemek bile, XAML şeması bağlamını dolaylı olarak gerektirir. Varsayılan XAML şema bağlamını kullandığınızda, bu bilgiler XAML tür sisteminde kullanılabilir. XAML yazıcı ile bağlantı öncesinde xaml düğüm akışı düzeyinde tür dönüştürücüsü sınıf bilgilerine ihtiyacınız varsa, bu dosyayı <xref:System.Xaml.XamlMember> ayarlanan üyenin bilgileriyle elde edebilirsiniz. Ancak Aksi takdirde, tür dönüştürme sistemi ve XAML şeması bağlamı gerektiren işlemlerin geri kalanı, örneğin bir XAML nesne yazıcısı tarafından oluşturulması gibi bir değer olarak XAML düğüm akışında, tür dönüştürücüsü girişi korunmalıdır.

Örneğin, aşağıdaki sınıf tanımı ana hattını ve XAML kullanımını göz önünde bulundurun:

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

Bu kullanım için XAML düğüm akışının metin gösterimi aşağıdakiler olarak ifade edilebilir:

`StartObject`<xref:System.Xaml.XamlType> temsil eden`GameBoard`

`StartMember`<xref:System.Xaml.XamlMember> temsil eden`BoardSize`

`Value`düğüm, "`8x8`" metin dizesiyle

`EndMember`Eşleştir`BoardSize`

`EndObject`Eşleştir`GameBoard`

Bu düğüm akışında tür dönüştürücüsü örneği olmadığına dikkat edin. Ancak, <xref:System.Xaml.XamlMember.TypeConverter%2A?displayProperty=nameWithType> <xref:System.Xaml.XamlMember> için 'deçağıraraktürdönüştürücüsübilgilerinialabilirsiniz.`BoardSize` Geçerli bir XAML şeması bağlamına sahipseniz, öğesinden <xref:System.Xaml.Schema.XamlValueConverter%601.ConverterInstance%2A>bir örnek elde ederek dönüştürücü yöntemlerini de çağırabilirsiniz.

### <a name="markup-extensions-in-the-xaml-node-stream"></a>XAML düğüm akışındaki biçimlendirme uzantıları

Biçimlendirme uzantısı kullanımı, XAML düğüm akışında, nesnenin bir biçimlendirme uzantısı örneğini temsil ettiği bir üye içindeki nesne düğümü olarak raporlanır. Bu nedenle, bir biçimlendirme uzantısı kullanımı, düğüm akışı gösteriminde tür dönüştürücüsü kullanımının daha açık bir şekilde sunulur ve daha fazla bilgi taşır. <xref:System.Xaml.XamlMember>Kullanım durumsal olduğundan ve olası her biçimlendirme durumunda değişiklik yaptığından, bilgi biçimlendirme uzantısıyla ilgili hiçbir şey söylemedi; tür dönüştürücülerinde olduğu gibi tür veya üye başına adanmış ve örtük değildir.

Biçimlendirme uzantılarının nesne düğümleri olarak düğüm akışı temsili, XAML metin biçimlendirmesinde (genellikle büyük/küçük harf) biçimlendirme uzantısı kullanımı öznitelik biçiminde yapılmış olsa bile durumdur. Açık nesne öğesi formu kullanan biçimlendirme uzantısı kullanımları aynı şekilde işlenir.

Biçimlendirme uzantısı nesne düğümü içinde, bu biçimlendirme uzantısının üyeleri olabilir. XAML düğüm akışı temsili, bu biçimlendirme uzantısının kullanımını, Konumsal parametre kullanımı veya açık adlandırılmış parametrelerle kullanım gibi korur.

Konumsal parametre kullanımı için xaml düğüm akışı, kullanımı kaydeden bir xaml dil tanımlı özelliği `_PositionalParameters` içerir. Bu özellik kısıtlamasıyla <xref:System.Object> geneldir <xref:System.Collections.Generic.List%601> . Çalıp a Konumsal parametre kullanımı, içinde iç içe biçimlendirme uzantısı kullanımları içerebildiğinden kısıtlama Object ve String değildir. Kullanımdan konumsal parametrelere erişmek için, listede yineleyebilir ve tek liste değerleri için Dizin oluşturuculardan yararlanabilirsiniz.

Adlandırılmış bir parametre kullanımı için, her adlandırılmış parametre, düğüm akışındaki bu adın üye düğümü olarak temsil edilir. İç içe geçmiş biçimlendirme uzantısı kullanımı olabileceğinden üye değerleri dize değildir.

`ProvideValue`biçimlendirme uzantısından henüz çağrılmamıştır. Ancak, bir xaml okuyucuyu ve xaml yazıcısını, düğüm akışında inceleyebileceğiniz biçimlendirme uzantısı düğümünde `WriteEndObject` çağrılacak şekilde bağladığınızda çağrılır. Bu nedenle, genellikle yükleme yolundaki nesne grafiğini biçimlendirmek için kullanılan aynı XAML şeması bağlamına ihtiyacınız vardır. Aksi takdirde `ProvideValue` , herhangi bir biçimlendirme uzantısı beklenen hizmetleri kullanılabilir olmadığından burada özel durumlar oluşturabilir.

<a name="xaml_and_xml_languagedefined_members_in_the_xaml_node_stream"></a>

## <a name="xaml-and-xml-language-defined-members-in-the-xaml-node-stream"></a>Xaml düğüm akışındaki XAML ve XML dil tanımlı Üyeler

Belirli Üyeler, açıkça <xref:System.Xaml.XamlMember> bir arama veya yapım yerine bir xaml okuyucusunun yorumlamalar ve kuralları nedeniyle xaml düğüm akışına tanıtılmıştır. Genellikle, bu Üyeler XAML yönergelerinden kaynaklanır. Bazı durumlarda, XAML düğüm akışına yönergesini tanıtan XAML okuma işlemidir. Diğer bir deyişle, özgün giriş XAML metni üye yönergesini açıkça belirtmedi, ancak XAML okuyucu, bir yapısal XAML kuralını ve bu bilgiler kaybedilmeden önce XAML düğüm akışındaki rapor bilgilerini karşılamak için yönergesini ekler.

Aşağıdaki liste, bir XAML okuyucusunun bir yönerge XAML üye düğümü tanıtması beklenen ve bu üye düğümünün .NET Framework XAML Hizmetleri uygulamalarında nasıl belirlenebileceği tüm durumları not.

- **Nesne düğümü için başlatma metni:** Bu üye düğümün `_Initialization`adı, XAML yönergesini temsil eder ve xaml Language xaml ad alanında tanımlanır. Bunun için bir statik varlık edinebilirsiniz <xref:System.Xaml.XamlLanguage.Initialization%2A>.

- **Biçimlendirme uzantısı için Konumsal Parametreler:** Bu üye düğümün `_PositionalParameters`adı, XAML Language xaml ad alanında tanımlanmıştır. Her birinin genel bir nesne listesini içerir, her biri, giriş xaml 'de sağlanan `,` sınırlayıcı karakter üzerinde bölünerek önceden ayrılmış konumsal bir parametre olur. Konumundan <xref:System.Xaml.XamlLanguage.PositionalParameters%2A>konumsal Parameters yönergesi için statik bir varlık edinebilirsiniz.

- **Bilinmeyen içerik:** Bu üye düğümün `_UnknownContent`adı. Kesinlikle konuşuyor <xref:System.Xaml.XamlDirective>ve xaml Language xaml ad alanında tanımlanmış. Bu yönerge, bir XAML nesne öğesinin kaynak XAML 'de içerik içerdiği ancak şu anda kullanılabilir olan XAML şema bağlamı altında hiçbir içerik özelliği belirlenebileceği durumlar için Sentinel olarak kullanılır. Adlı `_UnknownContent`üyeleri denetleyerek bu durumu bir xaml düğüm akışında tespit edebilirsiniz. Bir yükleme yolu xaml düğüm akışında başka bir işlem alınıyorsa, varsayılan <xref:System.Xaml.XamlObjectWriter> olarak herhangi bir nesne üzerinde `_UnknownContent` üyeyle `WriteEndObject` karşılaştığında denendiğinde denenir. Varsayılan değer <xref:System.Xaml.XamlXmlWriter> throw yapmaz ve üyeyi örtülü olarak değerlendirir. `_UnknownContent` Kaynağından<xref:System.Xaml.XamlLanguage.UnknownContent%2A>için bir statik varlık edinebilirsiniz.

- **Bir koleksiyonun Collection özelliği:** XAML için kullanılan bir koleksiyon sınıfının yedekleme CLR türünün genellikle koleksiyon öğelerini tutan ayrılmış bir adlandırılmış özelliği olsa da, bu özellik tür çözümlemesini yedeklemeden önce bir XAML tür sistemi olarak bilinir. Bunun yerine xaml düğüm akışı, koleksiyon XAML `Items` türünün bir üyesi olarak bir yer tutucu tanıtır. .NET Framework XAML Hizmetleri uygulamasında, düğüm akışındaki `_Items`bu yönergenin/üyenin adı. Bu yönerge için bir sabit, öğesinden <xref:System.Xaml.XamlLanguage.Items%2A>elde edilebilir.

    XAML düğüm akışı, yedekleme türü çözümleme ve XAML şema bağlamı temelinde ayrıştırılamayan bir öğe özelliği içerebilir. Örneğin,

- **XML tanımlı Üyeler:** XML `xml:base`tanımlı `base` `lang` `space` ve üyeleri, .NET Framework xaml Hizmetleri uygulamalarında, ve adlı xaml yönergeleri olarak raporlanır. `xml:space` `xml:lang` Bu ad alanı, XML ad alanıdır `http://www.w3.org/XML/1998/namespace`. Bunların her biri için sabitler, öğesinden <xref:System.Xaml.XamlLanguage>elde edilebilir.

## <a name="node-order"></a>Düğüm sırası

Bazı durumlarda, <xref:System.Xaml.XamlXmlReader> xaml düğüm akışındaki xaml düğümlerinin sırasını, İşaretlemede görüntüleniyorsa veya XML olarak işlendiğinde, düğümlerin görüntülenmesine göre değiştirir. Bu, düğüm akışını yalnızca ileri bir şekilde <xref:System.Xaml.XamlObjectWriter> işleyebilmesi için düğümleri sıralamak amacıyla yapılır.  .NET Framework XAML hizmetlerinde XAML okuyucusu, düğüm akışının XAML nesne yazıcısı tüketicileri için performans iyileştirmesi olarak bu görevi XAML yazıcısına bırakmak yerine düğümleri yeniden sıralar.

Belirli yönergeler özellikle bir nesne öğesinden bir nesne oluşturulmasına yönelik daha fazla bilgi sağlamak için tasarlanmıştır. Bu yönergeler şunlardır: `Initialization`, `PositionalParameters`, `TypeArguments` `FactoryMethod`,, `Arguments`. .NET Framework xaml Hizmetleri xaml okuyucuları, sonraki bölümde açıklanan nedenlerden dolayı bu yönergeleri bir nesne `StartObject`için düğüm akışındaki ilk üye olarak yerleştirmeyi dener.

### <a name="xamlobjectwriter-behavior-and-node-order"></a>XamlObjectWriter davranışı ve düğüm sırası

`StartObject`, nesne <xref:System.Xaml.XamlObjectWriter> örneğini hemen oluşturmak için bir, xaml nesne yazarının bir sinyali olması gerekmez. XAML, ek girişi olan bir nesneyi başlatmayı mümkün kılan ve tamamen ilk nesneyi oluşturmak için parametresiz bir Oluşturucu çağırma ve yalnızca özellikleri ayarlama gibi birçok dil özelliği içerir. Bu özellikler şunları içerir <xref:System.Windows.Markup.XamlDeferLoadAttribute>:; başlatma metni; [X:TypeArguments](x-typearguments-directive.md); biçimlendirme uzantısının konumsal parametreleri; Factory yöntemleri ve ilişkili [X:Arguments](x-arguments-directive.md) DÜĞÜMLERI (XAML 2009). Bu durumların her biri gerçek nesne oluşumunu geciktirecek ve düğüm akışı yeniden sınıflandırıldığı için XAML nesne yazıcısı, özellikle bir oluşturma olmayan bir başlangıç üyesine rastlana her seferinde örneği oluşturan bir davranışa güvenebilirler Bu nesne türü için yönerge.

### <a name="getobject"></a>GetObject

`GetObject`Yeni bir nesne oluşturmak yerine bir xaml düğümünü temsil eder, bunun yerine nesnenin içeren özelliğin değerini alır. Bir xaml düğüm akışında bir `GetObject` düğümün karşılaştığı tipik bir durum, bir koleksiyon nesnesi veya sözlük nesnesi için, kapsayan özellik, yedekleme türünün nesne modelinde kasıtlı olarak salt okunurdur. Bu senaryoda, koleksiyon veya sözlük genellikle sahip olan bir türün başlatma mantığı tarafından oluşturulur ve başlatılır (genellikle boştur).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xaml.XamlObjectReader>
- [XAML Hizmetleri](index.md)
- [XAML Ad Alanları](xaml-namespaces-for-net-framework-xaml-services.md)
