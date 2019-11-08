---
title: XAML Düğüm Akış Yapılarını ve Kavramlarını Anlama
ms.date: 03/30/2017
helpviewer_keywords:
- XAML node streams [XAML Services]
- nodes [XAML Services], XAML node stream
- XAML [XAML Services], XAML node streams
ms.assetid: 7c11abec-1075-474c-9d9b-778e5dab21c3
ms.openlocfilehash: 2c8093c3ef497bd836427f71098e62626f228e24
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73733384"
---
# <a name="understanding-xaml-node-stream-structures-and-concepts"></a>XAML Düğüm Akış Yapılarını ve Kavramlarını Anlama

.NET Framework XAML hizmetlerinde uygulanan xaml okuyucuları ve XAML yazarları, XAML düğüm akışının tasarım kavramını temel alır. XAML düğüm akışı, bir dizi XAML düğümü için bir dizi kavramsalization. Bu conceptuselte, bir XAML işlemcisi XAML içindeki düğüm ilişkilerinin yapısını birer birer gösterir. Herhangi bir zamanda, açık bir XAML düğüm akışında yalnızca bir adet geçerli kayıt veya geçerli konum bulunur ve API 'nin birçok yönü yalnızca ilgili konumdan kullanılabilen bilgileri rapor ediyor. Bir XAML düğüm akışındaki geçerli düğüm bir nesne, üye veya değer olarak açıklanabilir. Xaml okuyucular bir XAML düğüm akışı olarak davranarak XAML yazarları ile iletişim kurabilir ve bir programın bir yük yolu ya da XAML içeren bir yol kaydetme işlemi sırasında XAML düğüm akışının içeriğini görüntülemesini, bunlarla etkileşime geçmesini veya değiştirmesini sağlayabilir. XAML okuyucu ve yazıcı API 'SI tasarımı ve XAML düğüm akışı kavramı, XML Belge Nesne Modeli (DOM) ve <xref:System.Xml.XmlReader> ve <xref:System.Xml.XmlWriter> sınıfları gibi önceki ilgili okuyucu ve yazıcı tasarımlarına ve kavramlarına benzerdir. Bu konu XAML düğüm akışı kavramlarını ve xaml düğüm düzeyinde xaml temsilleri ile etkileşime geçen yordamları nasıl yazacağınız açıklanmaktadır.

<a name="loading_into_a_xaml_reader"></a>

## <a name="loading-xaml-into-a-xaml-reader"></a>Xaml 'yi XAML okuyucusuna yükleme

Temel <xref:System.Xaml.XamlReader> sınıfı, ilk XAML 'yi bir XAML okuyucusuna yüklemek için belirli bir teknik bildirmiyor. Bunun yerine, türetilmiş bir sınıf, XAML için giriş kaynağının genel özellikleri ve kısıtlamaları dahil olmak üzere yükleme tekniğini bildirir ve uygular. Örneğin, bir <xref:System.Xaml.XamlObjectReader>, kökü veya tabanı temsil eden tek bir nesnenin giriş kaynağından başlayarak bir nesne grafiğini okur. <xref:System.Xaml.XamlObjectReader> ardından nesne grafiğinden bir XAML düğüm akışı üretir.

En belirgin .NET Framework XAML Hizmetleri – tanımlanmış <xref:System.Xaml.XamlReader> alt sınıfı <xref:System.Xaml.XamlXmlReader>. <xref:System.Xaml.XamlXmlReader> ilk XAML 'yi, doğrudan bir akış veya dosya yoluyla bir metin dosyası yükleyerek ya da <xref:System.IO.TextReader>gibi ilgili bir okuyucu sınıfı aracılığıyla dolaylı olarak yükler. <xref:System.Xaml.XamlReader>, yüklendikten sonra XAML giriş kaynağının tamamını içeren olarak düşünülebilir. Ancak <xref:System.Xaml.XamlReader> temel API, okuyucunun tek bir XAML düğümüyle etkileşimde bulunmak için tasarlanmıştır. İlk yüklendiğinde, karşılaştığınız ilk tek düğüm XAML 'in ve başlangıç nesnesinin köküdür.

### <a name="the-xaml-node-stream-concept"></a>XAML düğüm akışı kavramı

XML tabanlı teknolojilerle ilgili bir DOM, ağaç metaphor veya sorgu tabanlı yaklaşım hakkında genel olarak daha fazla bilginiz varsa, XAML düğüm akışının kavramaya yönelik faydalı bir yolu aşağıdaki gibidir. Yüklenen XAML 'nin bir DOM veya her olası düğümün her şekilde genişletildiği bir ağaç olduğunu düşünün ve ardından ilk olarak sunulur. Düğümlerde ilerlettikçe, bir DOM ile ilgili olacak düzeylerin "içinde" veya "Out" şeklinde geçiş yapabilirsiniz, ancak bu düzey kavramlar bir düğüm akışıyla ilgili olmadığından XAML düğüm akışı açıkça izlenmez. Düğüm akışı "geçerli" bir konuma sahiptir, ancak akışın diğer bölümlerini başvuru olarak depolamadığınız sürece, düğüm akışının geçerli düğüm konumu dışındaki her yönü görünüm dışında olur.

XAML düğüm akışı kavramı, tüm düğüm akışının tamamına giderseniz, tüm XAML gösterimini işlemenize emin olduğunuz için önemli bir avantajdır. bir sorgunun, DOM işleminin veya işleme bilgileri ile ilgili başka bir doğrusal yaklaşımın, tüm XAML gösteriminin bir parçasını kaçırmadığından endişelenmeniz gerekmez. Bu nedenle, xaml düğüm akışı temsili hem XAML okuyucuları hem XAML yazıcılarını bağlamak için idealdir ve bir XAML işleme işleminin okuma ve yazma aşamaları arasında davranan kendi işleminizi ekleyebileceğiniz bir sistem sağlamak için idealdir. Çoğu durumda, XAML düğüm akışındaki düğümlerin sıralaması, XAML okuyucular tarafından kasıtlı olarak iyileştirilir veya yeniden sıralanabilir ve bu da sıranın kaynak metin, ikili veya nesne grafiğinde nasıl görünebileceğini de gösterebilir. Bu davranış, XAML yazıcılarının düğüm akışında "geri" gitmesi gereken bir konumda yer aldığı bir XAML işleme mimarisini zorlamak için tasarlanmıştır. İdeal olarak, tüm XAML yazma işlemleri şema bağlamına ve düğüm akışının geçerli konumuna göre işlem yapabilmelidir.

<a name="a_basic_reading_node_loop"></a>

## <a name="a-basic-reading-node-loop"></a>Temel bir okuma düğümü döngüsü

XAML düğüm akışını incelemek için temel bir okuma düğümü döngüsü aşağıdaki kavramlardan oluşur. Bu konuda anlatıldığı gibi düğüm döngülerinin amaçları doğrultusunda, <xref:System.Xaml.XamlXmlReader>kullanarak metin tabanlı, okunabilir XAML dosyasını okudığınızı varsayalım. Bu bölümdeki bağlantılar, <xref:System.Xaml.XamlXmlReader>tarafından uygulanan belirli XAML düğüm döngüsü API 'sine başvurur.

- XAML düğüm akışının sonunda olmadığından emin olun (<xref:System.Xaml.XamlXmlReader.IsEof%2A>denetleyin veya <xref:System.Xaml.XamlXmlReader.Read%2A> dönüş değerini kullanın). Akışın sonunda yer alıyorsa, geçerli bir düğüm yoktur ve çıkış yapmanız gerekir.

- <xref:System.Xaml.XamlXmlReader.NodeType%2A>çağırarak XAML düğüm akışının ne tür düğüm tarafından kullanıma sunulduğunu denetleyin.

- Doğrudan bağlanmış ilişkili bir XAML nesne yazıcınız varsa, genellikle bu noktada <xref:System.Xaml.XamlWriter.WriteNode%2A> çağırın.

- Geçerli düğüm veya geçerli kayıt olarak bildirilen <xref:System.Xaml.XamlNodeType> göre, düğüm içerikleri hakkında bilgi almak için aşağıdakilerden birini çağırın:

  - <xref:System.Xaml.XamlNodeType.StartMember> veya <xref:System.Xaml.XamlNodeType.EndMember><xref:System.Xaml.XamlXmlReader.NodeType%2A> için, bir üye hakkında <xref:System.Xaml.XamlMember> bilgileri almak üzere <xref:System.Xaml.XamlXmlReader.Member%2A> çağırın. Üyenin bir <xref:System.Xaml.XamlDirective>olabileceğini ve bu nedenle, önceki nesnenin geleneksel tür tanımlı bir üyesi olması gerekmediğini unutmayın. Örneğin, bir nesneye uygulanan `x:Name`, <xref:System.Xaml.XamlMember.IsDirective%2A> true olduğu ve üyenin <xref:System.Xaml.XamlMember.Name%2A>, bu yönergenin XAML Language XAML ad alanı altında olduğunu belirten diğer özelliklerle birlikte `Name`olduğu bir XAML üyesi olarak görünür.

  - <xref:System.Xaml.XamlNodeType.StartObject> veya <xref:System.Xaml.XamlNodeType.EndObject><xref:System.Xaml.XamlXmlReader.NodeType%2A> için, bir nesnesi hakkında <xref:System.Xaml.XamlType> bilgileri almak üzere <xref:System.Xaml.XamlXmlReader.Type%2A> çağırın.

  - <xref:System.Xaml.XamlNodeType.Value><xref:System.Xaml.XamlXmlReader.NodeType%2A> için <xref:System.Xaml.XamlXmlReader.Value%2A>çağırın. Düğüm yalnızca bir üye için bir değerin en basit ifadesi veya bir nesnenin başlatma metni ise bir değerdir (ancak, bu konunun yakında yaklaşan bölümünde belgelenen tür dönüştürme davranışının farkında olmanız gerekir).

  - <xref:System.Xaml.XamlNodeType.NamespaceDeclaration><xref:System.Xaml.XamlXmlReader.NodeType%2A> için, bir ad alanı düğümü için ad alanı bilgilerini almak üzere <xref:System.Xaml.XamlXmlReader.Namespace%2A> çağırın.

- Xaml okuyucuyu XAML düğüm akışındaki sonraki düğüme ilerletmek için <xref:System.Xaml.XamlXmlReader.Read%2A> çağırın ve adımları tekrar tekrarlayın.

.NET Framework XAML Hizmetleri XAML okuyucuları tarafından sağlanan XAML düğüm akışı her zaman tüm olası düğümlerin tam ve derin bir çapraz geçişini sağlar. XAML düğüm döngüsü için tipik akış denetimi teknikleri, `while (reader.Read())`içinde bir gövde tanımlamayı ve düğüm döngüsündeki her bir düğüm noktasında <xref:System.Xaml.XamlXmlReader.NodeType%2A> değiştirmeyi içerir.

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

Bir load path XAML düğümü döngüsünün bu temel örneği, XAML okuyucuyu ve XAML yazıcısını saydam şekilde bağlar ve <xref:System.Xaml.XamlServices.Parse%2A?displayProperty=nameWithType>kullanmışsınız gibi başka hiçbir şey yapmaz. Ancak bu temel yapı daha sonra okuma veya yazma senaryonuz için geçerlidir. Olası bazı senaryolar aşağıdaki gibidir:

- <xref:System.Xaml.XamlXmlReader.NodeType%2A>üzerinde geçiş yapın. Hangi düğüm türünün okunmakta olduğuna bağlı olarak farklı eylemler gerçekleştirin.

- Her durumda <xref:System.Xaml.XamlWriter.WriteNode%2A> çağırmayın. Yalnızca bazı <xref:System.Xaml.XamlXmlReader.NodeType%2A> durumlarda <xref:System.Xaml.XamlWriter.WriteNode%2A> çağırın.

- Belirli bir düğüm türünün mantığı içinde, bu düğümün özelliklerini çözümleyin ve üzerinde işlem yapın. Örneğin, yalnızca belirli bir XAML ad alanından gelen nesneleri yazabilir ve ardından bu XAML ad alanından olmayan nesneleri bırakabilir veya erteleyebilirsiniz. Ya da XAML sisteminizin üye işlemenin bir parçası olarak desteklemediği XAML yönergelerini bırakabilir veya başka bir şekilde yeniden işleyebilirsiniz.

- Muhtemelen XAML şeması bağlamını atlayan tür eşlemesi gerçekleştirerek, `Write*` yöntemleri geçersiz kılan özel bir <xref:System.Xaml.XamlObjectWriter> tanımlayın.

- Yalnızca, XAML davranışında özelleştirilmiş farkların hem okuyucu hem de yazıcı tarafından kullanıldığı şekilde, varsayılan olarak kullanılan XAML şema bağlamını kullanmak için <xref:System.Xaml.XamlXmlReader> oluşturun.

### <a name="accessing-xaml-beyond-the-node-loop-concept"></a>Düğüm döngüsü kavramının ötesinde XAML 'e erişme

XAML düğüm döngüsü dışında bir XAML temsili ile çalışmanın diğer olası yolları vardır. Örneğin, dizini oluşturulmuş bir düğümü okuyabilen bir XAML okuyucusu veya belirli erişim düğümlerine doğrudan `x:Name`, `x:Uid`veya diğer tanımlayıcılar aracılığıyla erişebilirsiniz. .NET Framework XAML Hizmetleri tam uygulama sağlamaz, ancak hizmetler ve destek türleri aracılığıyla önerilen bir model sağlar. Daha fazla bilgi için bkz. <xref:System.Xaml.IXamlIndexingReader> ve <xref:System.Xaml.XamlNodeList>.

<a name="working_with_the_current_node"></a>

## <a name="working-with-the-current-node"></a>Geçerli düğümle çalışma

XAML düğümü döngüsü kullanan çoğu senaryo yalnızca düğümleri okummaz. Çoğu senaryo geçerli düğümleri işler ve her bir düğümü tek seferde bir <xref:System.Xaml.XamlWriter>uygulamasına iletir.

Tipik yükleme yolu senaryosunda, bir <xref:System.Xaml.XamlXmlReader> XAML düğüm akışı oluşturur; XAML düğümleri Logic ve XAML şema bağlamına göre işlenir; ve düğümleri bir <xref:System.Xaml.XamlObjectWriter>geçirilir. Daha sonra elde edilen nesne grafiğini uygulamanız veya çatısı ile tümleştirin.

Tipik bir kayıt yolu senaryosunda, bir <xref:System.Xaml.XamlObjectReader> nesne grafiğini okur, tek XAML düğümleri işlenir ve bir <xref:System.Xaml.XamlXmlWriter> serileştirilmiş sonucu bir XAML metin dosyası olarak verir. Anahtar, hem yolların hem de senaryoların tek seferde tam olarak bir XAML düğümü ile çalışmasını içerir ve XAML düğümleri XAML türü sistem ve the.NET Framework XAML Hizmetleri API 'Leri tarafından tanımlanan standartlaştırılmış bir şekilde kullanıma sunulmuştur.

### <a name="frames-and-scope"></a>Çerçeveler ve kapsam

XAML düğüm döngüsü, XAML düğüm akışını doğrusal bir şekilde gösterir. Düğüm akışı nesnelere, diğer nesneleri içeren üyelere ve bu şekilde devam eder. Bir çerçeve ve yığın kavramı uygulayarak XAML düğüm akışı içindeki kapsamı izlemek genellikle yararlıdır. Bu, özellikle düğüm akışını etkin olarak ayarlıyorsanız geçerlidir. Düğüm döngüsü mantığınızın bir parçası olarak uyguladığınız çerçeve ve yığın desteği, yapı bir DOM perspektifinden düşünülse de bir XAML düğüm yapısına son bakış halinde `StartObject` (veya `GetObject`) ve `EndObject` kapsamlarını saymanız olabilir.

<a name="traversing_and_entering_object_nodes"></a>

## <a name="traversing-and-entering-object-nodes"></a>Nesne düğümlerini geçme ve girme

Bir XAML okuyucusu tarafından açıldığında düğüm akışındaki ilk düğüm, kök nesnenin başlangıç nesnesi düğümüdür. Tanım olarak, bu nesne her zaman tek bir nesne düğümüdür ve bir eşi yoktur. Herhangi bir gerçek dünyada XAML örneğinde, kök nesnesi daha fazla nesne tutan bir veya daha fazla özelliğe sahip olacak şekilde tanımlanır ve bu özelliklerde üye düğümleri vardır. Daha sonra üye düğümleri bir veya daha fazla nesne düğümüne sahiptir veya bunun yerine bir değer düğümünde da sonlandırılabilir. Kök nesnesi genellikle xaml metin biçimlendirmesinde öznitelik olarak atanan, ancak XAML düğüm akışı gösteriminde bir `Namescope` node türüyle eşlenen XAML namescopes 'yi tanımlar.

Aşağıdaki XAML örneğini göz önünde bulundurun (.NET Framework, bu rastgele XAML 'dir, bu, var olan türler tarafından yedeklenmez). Bu nesne modelinde, `FavorCollection` `Favor``List<T>` `Balloon` ve `NoiseMaker` `Favor`atanabilir olduğunu varsayın, `Balloon.Color` özelliği WPF 'in bilinen renk adları olarak renkleri nasıl tanımladığına benzer bir `Color` nesne tarafından desteklenir ve `Color` öznitelik sözdizimi için tür dönüştürücüsünü destekler.

|XAML işaretleme|Sonuçta elde edilen XAML düğüm akışı|
|-----------------|--------------------------------|
|`<Party`|`Party` için `Namespace` düğümü|
|`xmlns="PartyXamlNamespace">`|`Party` için `StartObject` düğümü|
|`<Party.Favors>`|`Party.Favors` için `StartMember` düğümü|
||örtük `FavorCollection` için `StartObject` düğümü|
||örtük `FavorCollection` Items özelliği için `StartMember` düğümü.|
|`<Balloon`|`Balloon` için `StartObject` düğümü|
|`Color="Red"`|`Color` için `StartMember` düğümü<br /><br /> öznitelik değeri dizesinin `Value` düğümü `"Red"`<br /><br /> `Color` için `EndMember`|
|`HasHelium="True"`|`HasHelium` için `StartMember` düğümü<br /><br /> öznitelik değeri dizesinin `Value` düğümü `"True"`<br /><br /> `HasHelium` için `EndMember`|
|`>`|`Balloon` için `EndObject`|
|`<NoiseMaker>Loudest</NoiseMaker>`|`NoiseMaker` için `StartObject` düğümü<br /><br /> `_Initialization` için `StartMember` düğümü<br /><br /> başlatma değeri dizesi için düğüm `Value` `"Loudest"`<br /><br /> `_Initialization` için `EndMember` düğümü<br /><br /> `NoiseMaker` için `EndObject`|
||örtük `FavorCollection` Items özelliği için `EndMember` düğümü.|
||örtük `FavorCollection` için `EndObject` düğümü|
|`</Party.Favors>`|`Favors` için `EndMember`|
|`</Party>`|`Party` için `EndObject`|

XAML düğüm akışında aşağıdaki davranışa güvenebilirsiniz:

- Bir `Namespace` düğümü varsa, bu, `xmlns`ile XAML ad alanını bildirdikleri `StartObject` hemen öncesine akışa eklenir. XAML ve örnek düğüm akışının bulunduğu önceki tabloya bakın. `StartObject` ve `Namespace` düğümlerinin, metin biçimlendirmesinde bildirim konumlarına karşı nasıl konumlandırdığı gibi göründüğünü fark edin. Bu, ad alanı düğümlerinin düğüm akışında için uygulanan düğümden önce her zaman göründüğü davranış temsilcisidir. Bu tasarımın amacı, ad alanı bilgilerinin nesne yazarları için hayati öneme sahip olması ve nesne yazıcısının tür eşlemesi gerçekleştirmeyi denemesi ya da nesneyi işlemesini denemeden önce bilinmesi gerekir. XAML ad alanı bilgilerini akıştaki uygulama kapsamının önüne koymak, her zaman düğüm akışının sunulma sırasında işlemesini daha kolay hale getirir.

- Yukarıdaki durumlar nedeniyle, kökün `StartObject` değil, başlangıçtan itibaren düğümlerden geçiş yaparken en çok gerçek dünya biçimlendirme durumlarında ilk olarak okuduğunuzdan bir veya daha fazla `Namespace` düğümdür.

- `StartObject` bir düğümün ardından `StartMember`, `Value`veya hemen bir `EndObject`gelebilir. Artık başka bir `StartObject`tarafından hemen izlenmez.

- Bir `StartMember` `StartObject`, `Value`veya anında `EndMember`gelebilir. Değerin, yeni bir değer örneklenebilecek bir `StartObject` yerine üst nesnenin mevcut bir değerinden gelmesi beklenen Üyeler için `GetObject`tarafından izlenebilir. Ayrıca, yaklaşan bir `StartObject`için geçerli olan bir `Namespace` düğümü de gelebilir. Artık başka bir `StartMember`tarafından hemen izlenmez.

- `Value` düğüm değerin kendisini temsil eder; "EndValue" yok. Bunun ardından yalnızca bir `EndMember`olabilir.

  - Nesnenin XAML başlatma metni, oluşturma tarafından kullanılabilecek şekilde, nesne değeri yapısına neden olmaz. Bunun yerine, `_Initialization` adlı üye için ayrılmış bir üye düğümü oluşturulur. ve bu üye düğümü başlatma değeri dizesini içerir. Varsa, `_Initialization` her zaman ilk `StartMember`. `_Initialization`, XAML dili XAML namescope ile bazı XAML Hizmetleri temsillerine uygun olabilir, bu da `_Initialization`, yedekleme türlerinde tanımlı bir özellik değildir.

  - Üye-değer birleşimi değerin bir öznitelik ayarını temsil eder. Sonuç olarak bu değeri işlemeye dahil bir değer Dönüştürücüsü olabilir ve değer düz bir dizedir. Ancak, bir XAML nesne yazıcısı bu düğüm akışını işleene kadar değerlendirilmez. XAML nesne yazarı, gerekli XAML şeması bağlamı, tür sistemi eşlemesi ve değer dönüştürmeleri için gereken diğer desteğe sahiptir.

- Bir `EndMember` düğümü, sonraki bir üye için bir `StartMember` düğümü veya üye sahibi için bir `EndObject` düğümü tarafından izlenebilir.

- Bir `EndObject` düğümü, `EndMember` bir düğüm tarafından izlenebilir. Ayrıca, nesnelerin bir koleksiyonun öğelerinde eşler olduğu durumlarda bir `StartObject` düğümü de görüntülenebilir. Veya yaklaşan bir `StartObject`için geçerli olan bir `Namespace` düğümü gelebilir.

  - Tüm düğüm akışını kapatmakla ilgili benzersiz durumda, kök `EndObject` hiçbir şey tarafından izlenmez; okuyucu artık dosya sonu ' dir ve <xref:System.Xaml.XamlReader.Read%2A> `false`döndürür.

<a name="value_converters_and_the_xaml_node_stream"></a>

## <a name="value-converters-and-the-xaml-node-stream"></a>Değer dönüştürücüler ve XAML düğüm akışı

Değer Dönüştürücüsü, bir işaretleme uzantısı için genel bir terimdir, bir tür Dönüştürücüsü (değer serileştiriciler dahil) veya XAML tür sistemi aracılığıyla bir değer Dönüştürücüsü olarak bildirilen başka bir ayrılmış sınıf. XAML düğüm akışında, tür dönüştürücüsü kullanımı ve biçimlendirme uzantısı kullanımı çok farklı temsiller de vardır.

### <a name="type-converters-in-the-xaml-node-stream"></a>XAML düğüm akışında tür dönüştürücüler

Sonunda bir tür dönüştürücüsü kullanımıyla sonuçlanan bir öznitelik kümesi, XAML düğüm akışında bir üyenin değeri olarak raporlanır. XAML düğüm akışı, bir tür dönüştürücü örnek nesnesi üretmeyi ve değeri geçirmeye çalışmaz. Tür dönüştürücünün dönüştürme uygulamasının kullanılması için XAML şema bağlamını çağırma ve tür eşleme için kullanılması gerekir. Değeri işlemek için hangi tür dönüştürücü sınıfının kullanılması gerektiğini belirlemek bile, XAML şeması bağlamını dolaylı olarak gerektirir. Varsayılan XAML şema bağlamını kullandığınızda, bu bilgiler XAML tür sisteminde kullanılabilir. XAML yazıcı bağlantısı yapmadan önce XAML düğüm akışı düzeyinde tür dönüştürücü sınıfı bilgisine ihtiyacınız varsa, bunu ayarlanan üyenin <xref:System.Xaml.XamlMember> bilgilerden elde edebilirsiniz. Ancak Aksi takdirde, tür dönüştürme sistemi ve XAML şeması bağlamı gerektiren işlemlerin geri kalanı, örneğin bir XAML nesne yazıcısı tarafından oluşturulması gibi bir değer olarak XAML düğüm akışında, tür dönüştürücüsü girişi korunmalıdır.

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

`GameBoard` temsil eden <xref:System.Xaml.XamlType> `StartObject`

`BoardSize` temsil eden <xref:System.Xaml.XamlMember> `StartMember`

"`8x8`" metin dizesiyle `Value` düğümü

`EndMember` eşleşiyor `BoardSize`

`EndObject` eşleşiyor `GameBoard`

Bu düğüm akışında tür dönüştürücüsü örneği olmadığına dikkat edin. Ancak `BoardSize`için <xref:System.Xaml.XamlMember> <xref:System.Xaml.XamlMember.TypeConverter%2A?displayProperty=nameWithType> çağırarak tür dönüştürücüsü bilgilerini alabilirsiniz. Geçerli bir XAML şeması bağlamına sahipseniz, <xref:System.Xaml.Schema.XamlValueConverter%601.ConverterInstance%2A>bir örnek alarak dönüştürücü yöntemlerini de çağırabilirsiniz.

### <a name="markup-extensions-in-the-xaml-node-stream"></a>XAML düğüm akışındaki biçimlendirme uzantıları

Biçimlendirme uzantısı kullanımı, XAML düğüm akışında, nesnenin bir biçimlendirme uzantısı örneğini temsil ettiği bir üye içindeki nesne düğümü olarak raporlanır. Bu nedenle, bir biçimlendirme uzantısı kullanımı, düğüm akışı gösteriminde tür dönüştürücüsü kullanımının daha açık bir şekilde sunulur ve daha fazla bilgi taşır. <xref:System.Xaml.XamlMember> bilgiler, kullanım durumsal olduğu ve olası her biçimlendirme durumunda değişiklik gösterdiği için biçimlendirme uzantısıyla ilgili hiçbir şey söylemedi; tür dönüştürücülerinde olduğu gibi tür veya üye başına adanmış ve örtük değildir.

Biçimlendirme uzantılarının nesne düğümleri olarak düğüm akışı temsili, XAML metin biçimlendirmesinde (genellikle büyük/küçük harf) biçimlendirme uzantısı kullanımı öznitelik biçiminde yapılmış olsa bile durumdur. Açık nesne öğesi formu kullanan biçimlendirme uzantısı kullanımları aynı şekilde işlenir.

Biçimlendirme uzantısı nesne düğümü içinde, bu biçimlendirme uzantısının üyeleri olabilir. XAML düğüm akışı temsili, bu biçimlendirme uzantısının kullanımını, Konumsal parametre kullanımı veya açık adlandırılmış parametrelerle kullanım gibi korur.

Konumsal parametre kullanımı için XAML düğüm akışı, kullanımı kaydeden XAML dil tanımlı bir özellik `_PositionalParameters` içerir. Bu özellik <xref:System.Object> kısıtlaması olan genel bir <xref:System.Collections.Generic.List%601>. Çalıp a Konumsal parametre kullanımı, içinde iç içe biçimlendirme uzantısı kullanımları içerebildiğinden kısıtlama Object ve String değildir. Kullanımdan konumsal parametrelere erişmek için, listede yineleyebilir ve tek liste değerleri için Dizin oluşturuculardan yararlanabilirsiniz.

Adlandırılmış bir parametre kullanımı için, her adlandırılmış parametre, düğüm akışındaki bu adın üye düğümü olarak temsil edilir. İç içe geçmiş biçimlendirme uzantısı kullanımı olabileceğinden üye değerleri dize değildir.

biçimlendirme uzantısından `ProvideValue` henüz çağrılmamıştır. Ancak, bir XAML okuyucuyu ve XAML yazıcısını bağladığınızda çağrılır. böylece, düğüm akışında inceleyebileceğiniz biçimlendirme uzantısı düğümünde `WriteEndObject` çağrılır. Bu nedenle, genellikle yükleme yolundaki nesne grafiğini biçimlendirmek için kullanılan aynı XAML şeması bağlamına ihtiyacınız vardır. Aksi takdirde, herhangi bir biçimlendirme uzantısının `ProvideValue`, beklenen hizmetleri kullanılabilir olmadığı için burada özel durumlar oluşturabilir.

<a name="xaml_and_xml_languagedefined_members_in_the_xaml_node_stream"></a>

## <a name="xaml-and-xml-language-defined-members-in-the-xaml-node-stream"></a>Xaml düğüm akışındaki XAML ve XML dil tanımlı Üyeler

Belirli Üyeler, açık bir <xref:System.Xaml.XamlMember> arama veya oluşturma yerine bir XAML okuyucusunun yorumlamalar ve kuralları nedeniyle XAML düğüm akışına tanıtılmıştır. Genellikle, bu Üyeler XAML yönergelerinden kaynaklanır. Bazı durumlarda, XAML düğüm akışına yönergesini tanıtan XAML okuma işlemidir. Diğer bir deyişle, özgün giriş XAML metni üye yönergesini açıkça belirtmedi, ancak XAML okuyucu, bir yapısal XAML kuralını ve bu bilgiler kaybedilmeden önce XAML düğüm akışındaki rapor bilgilerini karşılamak için yönergesini ekler.

Aşağıdaki liste, bir XAML okuyucusunun bir yönerge XAML üye düğümü tanıtması beklenen ve bu üye düğümünün .NET Framework XAML Hizmetleri uygulamalarında nasıl belirlenebileceği tüm durumları not.

- **Nesne düğümü Için başlatma metni:** Bu üye düğümün adı `_Initialization`, bir XAML yönergesini temsil eder ve XAML Language XAML ad alanında tanımlanır. <xref:System.Xaml.XamlLanguage.Initialization%2A>için bir statik varlık alabilirsiniz.

- **Biçimlendirme Uzantısı Için Konumsal Parametreler:** Bu üye düğümün adı `_PositionalParameters`ve XAML Language XAML ad alanında tanımlanmıştır. Her biri her biri, giriş XAML 'de sağlanan `,` sınırlayıcı karakter üzerinde bölünerek önceden ayrılmış konumsal bir parametre olan bir konum parametresi olan genel bir nesne listesi içerir. <xref:System.Xaml.XamlLanguage.PositionalParameters%2A>konumsal Parameters yönergesine yönelik statik bir varlık alabilirsiniz.

- **Bilinmeyen içerik:** Bu üye düğümün adı `_UnknownContent`. Kesinlikle konuşuyor, bir <xref:System.Xaml.XamlDirective>ve XAML Language XAML ad alanında tanımlanmıştır. Bu yönerge, bir XAML nesne öğesinin kaynak XAML 'de içerik içerdiği ancak şu anda kullanılabilir olan XAML şema bağlamı altında hiçbir içerik özelliği belirlenebileceği durumlar için Sentinel olarak kullanılır. `_UnknownContent`adlı üyeleri denetleyerek bu durumu bir XAML düğüm akışında tespit edebilirsiniz. Bir yükleme yolu XAML düğüm akışında başka bir işlem alınıyorsa, varsayılan <xref:System.Xaml.XamlObjectWriter> herhangi bir nesne üzerinde `_UnknownContent` üyesiyle karşılaştığında `WriteEndObject` yapılmaya çalışıldı. Varsayılan <xref:System.Xaml.XamlXmlWriter> oluşturmaz ve üyeyi örtük olarak kabul etmez. <xref:System.Xaml.XamlLanguage.UnknownContent%2A>`_UnknownContent` için statik bir varlık alabilirsiniz.

- **Bir koleksiyonun Collection özelliği:** XAML için kullanılan bir koleksiyon sınıfının yedekleme CLR türünün genellikle koleksiyon öğelerini tutan ayrılmış bir adlandırılmış özelliği olsa da, bu özellik tür çözümlemesini yedeklemeden önce bir XAML tür sistemi olarak bilinir. Bunun yerine, XAML düğüm akışı, koleksiyon XAML türünün bir üyesi olarak bir `Items` yer tutucusu tanıtır. .NET Framework XAML Hizmetleri uygulamasında, düğüm akışındaki bu yönergenin/üyenin adı `_Items`. Bu yönerge için bir sabit <xref:System.Xaml.XamlLanguage.Items%2A>adresinden elde edilebilir.

    XAML düğüm akışı, yedekleme türü çözümleme ve XAML şema bağlamı temelinde ayrıştırılamayan bir öğe özelliği içerebilir. Örneğin,

- **XML tanımlı Üyeler:** XML tanımlı `xml:base`, `xml:lang` ve `xml:space` üyeleri, `lang`XAML Hizmetleri uygulamalarında `base`, `space` ve .NET Framework adlı XAML yönergeleri olarak raporlanır. Bu ad alanı, `http://www.w3.org/XML/1998/namespace`XML ad alanıdır. Bunların her biri için sabitler <xref:System.Xaml.XamlLanguage>elde edilebilir.

## <a name="node-order"></a>Düğüm sırası

Bazı durumlarda <xref:System.Xaml.XamlXmlReader> XAML düğüm akışındaki XAML düğümlerinin sırasını, İşaretlemede görüntüleniyorsa veya XML olarak işlenirse, düğümlerin görünmesini ve bu şekilde değişdikleri sıraya göre değiştirir. Bu, düğümleri bir <xref:System.Xaml.XamlObjectWriter> düğüm akışını yalnızca ileri bir şekilde işleyebileceği şekilde sıralamak için yapılır.  .NET Framework XAML hizmetlerinde XAML okuyucusu, düğüm akışının XAML nesne yazıcısı tüketicileri için performans iyileştirmesi olarak bu görevi XAML yazıcısına bırakmak yerine düğümleri yeniden sıralar.

Belirli yönergeler özellikle bir nesne öğesinden bir nesne oluşturulmasına yönelik daha fazla bilgi sağlamak için tasarlanmıştır. Bu yönergeler şunlardır: `Initialization`, `PositionalParameters`, `TypeArguments`, `FactoryMethod`, `Arguments`. .NET Framework XAML Hizmetleri XAML okuyucuları, sonraki bölümde açıklanan nedenlerden dolayı, bu yönergeleri nesnenin `StartObject`takip eden düğüm akışına ilk üye olarak yerleştirmeyi dener.

### <a name="xamlobjectwriter-behavior-and-node-order"></a>XamlObjectWriter davranışı ve düğüm sırası

bir <xref:System.Xaml.XamlObjectWriter> `StartObject`, nesne örneğini hemen oluşturmak için XAML nesne yazıcısında bir sinyal değildir. XAML, ek girişi olan bir nesneyi başlatmayı mümkün kılan ve tamamen ilk nesneyi oluşturmak için parametresiz bir Oluşturucu çağırma ve yalnızca özellikleri ayarlama gibi birçok dil özelliği içerir. Bu özellikler şunları içerir: <xref:System.Windows.Markup.XamlDeferLoadAttribute>; başlatma metni; [X:TypeArguments](x-typearguments-directive.md); biçimlendirme uzantısının konumsal parametreleri; Factory yöntemleri ve ilişkili [X:Arguments](x-arguments-directive.md) DÜĞÜMLERI (XAML 2009). Bu durumların her biri gerçek nesne oluşumunu geciktirecek ve düğüm akışı yeniden sınıflandırıldığı için XAML nesne yazıcısı, özellikle bir oluşturma olmayan bir başlangıç üyesine rastlana her seferinde örneği oluşturan bir davranışa güvenebilirler Bu nesne türü için yönerge.

### <a name="getobject"></a>GetObject

`GetObject`, yeni bir nesne oluşturmak yerine bir xaml düğümünü temsil eder, bunun yerine nesnenin içeren özelliğin değerini alır. Bir XAML düğüm akışında bir `GetObject` düğümünün karşılaştığı tipik bir durum, bir koleksiyon nesnesi veya sözlük nesnesi içindir; Bu özellik, kendisini yedekleme türünün nesne modelinde kasıtlı olarak salt okunurdur. Bu senaryoda, koleksiyon veya sözlük genellikle sahip olan bir türün başlatma mantığı tarafından oluşturulur ve başlatılır (genellikle boştur).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xaml.XamlObjectReader>
- [XAML Hizmetleri](index.md)
- [XAML Ad Alanları](xaml-namespaces-for-net-framework-xaml-services.md)
