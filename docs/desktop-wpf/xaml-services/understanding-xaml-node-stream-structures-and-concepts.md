---
title: XAML Düğüm Akış Yapılarını ve Kavramlarını Anlama
ms.date: 03/30/2017
helpviewer_keywords:
- XAML node streams [XAML Services]
- nodes [XAML Services], XAML node stream
- XAML [XAML Services], XAML node streams
ms.assetid: 7c11abec-1075-474c-9d9b-778e5dab21c3
ms.openlocfilehash: b3de3dca029c5e676fc7cdebc7735cfdade0228a
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071621"
---
# <a name="xaml-node-stream-structures-and-concepts"></a>XAML düğüm akışı yapıları ve kavramları

.NET XAML Services'da uygulanan XAML okuyucuları ve XAML yazarları, XAML düğüm akışının tasarım konseptine dayanır. XAML düğümü akışı, XAML düğüm kümesinin kavramsallaştırılmasıdır. Bu kavramsallaştırmada, bir XAML işlemci sis ilişkileri yapısı nda teker teker yürür. Herhangi bir zamanda, açık bir XAML düğüm akışında yalnızca bir geçerli kayıt veya geçerli konum bulunur ve API'nin birçok yönü yalnızca bu konumdan kullanılabilen bilgileri raporlar. XAML düğümü akışındaki geçerli düğüm bir nesne, üye veya değer olarak tanımlanabilir. XAML'yi XAML düğümü akışı olarak ele alarak, XAML okuyucuları XAML yazarlarıyla iletişim kurabilir ve bir programın bir yükleme yolu veya XAML içeren bir kaydet yolu işlemi sırasında XAML düğüm akışının içeriğini görüntülemesini, etkileşimde bulunmasını veya değiştirmesini sağlayabilir. XAML okuyucu ve yazar API tasarımı ve XAML düğüm akışı kavramı önceki ilgili okuyucu ve yazar tasarımları ve kavramları, <xref:System.Xml.XmlReader> <xref:System.Xml.XmlWriter> XML Belge Nesne Modeli (DOM) ve ve sınıflar gibi benzer. Bu konu XAML düğüm akışı kavramlarını açıklar ve XAML düğüm düzeyinde XAML gösterimleri ile etkileşim yordamları nasıl yazabileceğinizi açıklar.

## <a name="loading-xaml-into-a-xaml-reader"></a>XAML Okuyucuya XAML Yükleme

Taban <xref:System.Xaml.XamlReader> sınıf, ilk XAML'yi XAML okuyucuya yüklemek için belirli bir teknik bildirmez. Bunun yerine, türemiş bir sınıf XAML için giriş kaynağının genel özellikleri ve kısıtlamaları da dahil olmak üzere yükleme tekniğini bildirir ve uygular. Örneğin, bir <xref:System.Xaml.XamlObjectReader> nesne grafiği, kök veya tabanı temsil eden tek bir nesnenin giriş kaynağından başlayarak okur. Daha <xref:System.Xaml.XamlObjectReader> sonra nesne grafiğinden bir XAML düğüm akışı üretir.

En belirgin .NET XAML <xref:System.Xaml.XamlReader> Hizmetleri tanımlı alt sınıfıdır. <xref:System.Xaml.XamlXmlReader> <xref:System.Xaml.XamlXmlReader>bir metin dosyasını doğrudan bir akış veya dosya yolu üzerinden yükleyerek veya dolaylı olarak <xref:System.IO.TextReader>ilgili bir okuyucu sınıfı aracılığıyla ilk XAML yükler. XAML <xref:System.Xaml.XamlReader> giriş kaynağının tamamını içeren olarak düşünülebilir. <xref:System.Xaml.XamlReader> Ancak, temel API okuyucu XAML tek bir düğüm ile etkileşim olacak şekilde tasarlanmıştır. İlk yüklendiğinizde, karşılaştığınız ilk tek düğüm XAML'nin kökü ve başlangıç nesnesidir.

### <a name="the-xaml-node-stream-concept"></a>XAML Düğüm Akışı Kavramı

Bir DOM, ağaç metaforu veya XML tabanlı teknolojilere erişime yönelik sorgu tabanlı bir yaklaşıma daha aşinaysanız, XAML düğüm akışını kavramsallaştırmanın yararlı bir yolu aşağıdaki gibidir. Yüklü XAML'nin bir DOM veya olası düğümün tamamen genişletildiği ve doğrusal olarak sunulduğu bir ağaç olduğunu düşünün. Düğümler arasında ilerledikçe, bir DOM ile ilgili olacak düzeylerin "içinde" veya "dışında" geçiş yapıyor olabilirsiniz, ancak xaml düğüm akışı açıkça izlemiyor, çünkü bu düzey kavramları bir düğüm akışıyla ilgili değildir. Düğüm akışı bir "geçerli" konuma sahiptir, ancak akışın diğer bölümlerini başvuru olarak kendiniz saklamadığınız sürece, düğüm akışının geçerli düğüm konumu dışındaki her yönü görüntülenmez.

XAML düğüm akışı kavramı, tüm düğüm akışı üzerinden giderseniz, tüm XAML gösterimi işlenmiş emin olduğunu önemli bir avantaja sahiptir; bir sorgu, bir DOM işlemi veya bilgileri işlemeye yönelik diğer doğrusal olmayan bir yaklaşımın xaml gösteriminin bir bölümünü kaçırdığından endişelenmenize gerek yoktur. Bu nedenle, XAML düğüm akışı gösterimi hem XAML okuyucuları ve XAML yazarlarını bağlamak hem de bir XAML işleme işleminin okuma ve yazma aşamaları arasında hareket eden kendi işleminizi ekebileceğiniz bir sistem sağlamak için idealdir. Çoğu durumda, XAML düğüm akışındaki düğümlerin sıralanması, xaml okuyucuları tarafından, siparişin kaynak metin, ikili veya nesne grafiğinde nasıl görünebileceğine göre kasıtlı olarak optimize edilir veya yeniden sıralanır. Bu davranış, XAML yazarlarıdüğüm akışı "geri" gitmek zorunda bir konumda asla bir XAML işleme mimarisi zorlamak için tasarlanmıştır. İdeal olarak, tüm XAML yazma işlemleri şema bağlamına ve düğüm akışının geçerli konumuna göre hareket edebilmelidir.

## <a name="a-basic-reading-node-loop"></a>Temel Okuma Düğümü Döngüsü

XAML düğüm akışını incelemek için temel bir okuma düğümü döngüsü aşağıdaki kavramlardan oluşur. Düğüm döngüleri amacıyla bu konuda tartışılan, bir metin tabanlı, insan tarafından okunabilir XAML dosyasını <xref:System.Xaml.XamlXmlReader>kullanarak okuyorsanız varsayalım. Bu bölümdeki bağlantılar, '. tarafından uygulanan belirli XAML <xref:System.Xaml.XamlXmlReader>düğüm döngüsü API'sine bakın.

- XAML düğüm akışının sonunda olmadığınızı unutmayın <xref:System.Xaml.XamlXmlReader.IsEof%2A> <xref:System.Xaml.XamlXmlReader.Read%2A> (iade değerini denetleyin veya kullanın). Akışın sonundaysanız, akım düğümü yoktur ve çıkmalısınız.

- XAML düğümü akışının şu anda ne tür <xref:System.Xaml.XamlXmlReader.NodeType%2A>bir düğüm ortaya çıkardığını kontrol edin.

- Doğrudan bağlı ilişkili bir XAML nesne yazar varsa, <xref:System.Xaml.XamlWriter.WriteNode%2A> genellikle bu noktada arama.

- <xref:System.Xaml.XamlNodeType> Geçerli düğüm veya geçerli kayıt olarak bildirilen bağlı olarak, düğüm içeriği hakkında bilgi edinmek için aşağıdakilerden birini arayın:

  - <xref:System.Xaml.XamlXmlReader.NodeType%2A> Bir <xref:System.Xaml.XamlNodeType.StartMember> <xref:System.Xaml.XamlNodeType.EndMember>veya , <xref:System.Xaml.XamlXmlReader.Member%2A> bir <xref:System.Xaml.XamlMember> üye hakkında bilgi almak için arayın. Üye bir <xref:System.Xaml.XamlDirective>, ve bu nedenle mutlaka önceki nesnenin geleneksel bir tür tanımlı üyesi olmayabilir. `x:Name` Örneğin, bir nesneye uygulanan bir XAML <xref:System.Xaml.XamlMember.IsDirective%2A> üyesi olarak <xref:System.Xaml.XamlMember.Name%2A> görünür nerede `Name`doğrudur ve üyenin , bu yönerge XAML dili XAML ad alanı altında olduğunu gösteren diğer özellikleri ile.

  - <xref:System.Xaml.XamlXmlReader.NodeType%2A> Bir <xref:System.Xaml.XamlNodeType.StartObject> <xref:System.Xaml.XamlNodeType.EndObject>veya , <xref:System.Xaml.XamlXmlReader.Type%2A> bir <xref:System.Xaml.XamlType> nesne hakkında bilgi almak için arayın.

  - Bir <xref:System.Xaml.XamlXmlReader.NodeType%2A> of <xref:System.Xaml.XamlNodeType.Value>için <xref:System.Xaml.XamlXmlReader.Value%2A>, çağrı . Düğüm, yalnızca bir üye için bir değerin en basit ifadesi veya bir nesnenin başlatma metniyse bir değerdir (ancak, bu konunun gelecek bölümünde belgelenen tür dönüştürme davranışının farkında olmalısınız).

  - Bir <xref:System.Xaml.XamlXmlReader.NodeType%2A> <xref:System.Xaml.XamlNodeType.NamespaceDeclaration>, ad <xref:System.Xaml.XamlXmlReader.Namespace%2A> alanı düğümü için ad alanı bilgilerini almak için arayın.

- XAML okuyucuyu XAML düğüm akışındaki bir sonraki düğüme ilerletmek için arayın <xref:System.Xaml.XamlXmlReader.Read%2A> ve adımları tekrarlayın.

.NET XAML Services XAML okuyucuları tarafından sağlanan XAML düğüm akışı her zaman tüm olası düğümlerin tam ve derin bir geçişsağlar. XAML düğüm döngüsü için tipik akış kontrol teknikleri içinde `while (reader.Read())`bir gövde <xref:System.Xaml.XamlXmlReader.NodeType%2A> tanımlama ve düğüm döngüsündeki her düğüm noktasında açma içerir.

Düğüm akışı dosyanın sonundaysa, geçerli düğüm null'dur.

Bir okuyucu ve yazar kullanan en basit döngü aşağıdaki örneğe benzer.

```csharp
XamlXmlReader xxr = new XamlXmlReader(new StringReader(xamlStringToLoad));
//where xamlStringToLoad is a string of well formed XAML
XamlObjectWriter xow = new XamlObjectWriter(xxr.SchemaContext);
while (xxr.Read()) {
  xow.WriteNode(xxr);
}
```

Bir yük yolu XAML düğüm döngü bu temel örnek şeffaf XAML okuyucu ve XAML yazar <xref:System.Xaml.XamlServices.Parse%2A?displayProperty=nameWithType>bağlanır, eğer kullanmış olsaydı farklı bir şey yapıyor. Ancak bu temel yapı daha sonra okuma veya yazma senaryonuza uygulanacak şekilde genişletilir. Bazı olası senaryolar aşağıdaki gibidir:

- Aç. <xref:System.Xaml.XamlXmlReader.NodeType%2A> Hangi düğüm türüokunduğuna bağlı olarak farklı eylemler gerçekleştirin.

- Her durumda <xref:System.Xaml.XamlWriter.WriteNode%2A> aramayın. Sadece <xref:System.Xaml.XamlWriter.WriteNode%2A> bazı <xref:System.Xaml.XamlXmlReader.NodeType%2A> durumlarda ararsın.

- Belirli bir düğüm türü için mantık içinde, bu düğümün özelliklerini analiz ve onlara hareket. Örneğin, yalnızca belirli bir XAML ad alanından gelen nesneleri yazabilir ve ardından xaml ad alanından olmayan nesneleri bırakabilir veya erteleyebilirdiniz. Veya XAML sisteminizin üye işlemenizin bir parçası olarak desteklemediği XAML yönergelerini bırakabilir veya başka bir şekilde yeniden işleyebilirsiniz.

- XAML <xref:System.Xaml.XamlObjectWriter> şema `Write*` bağlamı atlar tür eşleme gerçekleştirerek, yöntemleri geçersiz kılan bir özel tanımlayın.

- Varsayılan <xref:System.Xaml.XamlXmlReader> olmayan bir XAML şeması bağlamı kullanmak için, Böylece XAML davranışında özelleştirilmiş farklılıklar hem okuyucu hem de yazar tarafından kullanılır oluştur.

### <a name="accessing-xaml-beyond-the-node-loop-concept"></a>Düğüm Döngüsü Kavramının Ötesinde XAML'ye Erişim

XAML düğüm döngüsü dışında bir XAML gösterimi ile çalışmak için potansiyel olarak başka yollar vardır. Örneğin, dizine eklenmiş bir düğümü okuyabilen veya özellikle düğümlere doğrudan `x:Name`, tarafından `x:Uid`veya diğer tanımlayıcılar aracılığıyla erişen bir XAML okuyucusu olabilir. .NET XAML Hizmetleri tam bir uygulama sağlamaz, ancak hizmetler ve destek türleri aracılığıyla önerilen bir desen sağlar. Daha fazla bilgi için <xref:System.Xaml.IXamlIndexingReader> ve <xref:System.Xaml.XamlNodeList> bölümlerine bakın.

## <a name="working-with-the-current-node"></a>Geçerli Düğümle Çalışma

XAML düğüm döngüsü kullanan çoğu senaryo yalnızca düğümleri okumaz. Çoğu senaryo geçerli düğümleri işler ve her düğümü bir er <xref:System.Xaml.XamlWriter>teker bir uygulamaya geçirir.

Tipik yük yolu senaryosunda, bir <xref:System.Xaml.XamlXmlReader> XAML düğüm akışı üretir; XAML düğümleri mantığınıza ve XAML şema bağlamınıza göre işlenir; ve düğümler bir <xref:System.Xaml.XamlObjectWriter>. Daha sonra ortaya çıkan nesne grafiğini uygulamanıza veya çerçevenize tümleştirirsiniz.

Tipik bir kaydet yolu <xref:System.Xaml.XamlObjectReader> senaryosunda, nesne grafiği ni okur, tek tek <xref:System.Xaml.XamlXmlWriter> XAML düğümleri işlenir ve XAML metin dosyası olarak serileştirilmiş sonucu çıktıları. Anahtar, hem yolların hem de senaryoların aynı anda tam olarak bir XAML düğümüyle çalışmayı içermesi ve XAML düğümlerinin XAML tipi sistemi ve the.NET XAML Hizmetleri API'leri tarafından tanımlanan standart bir şekilde tedavi edilebilmektedir.

### <a name="frames-and-scope"></a>Çerçeveler ve Kapsam

XAML düğüm döngüsü, Bir XAML düğüm akışında doğrusal bir şekilde yürür. Düğüm akışı nesnelere, diğer nesneleri içeren üyelere ve benzeri geçişler. Genellikle bir çerçeve ve yığın kavramı uygulayarak XAML düğüm akışı içinde kapsamı izlemek için yararlıdır. Bu, özellikle düğüm akışını içindeyken etkin olarak ayarlıyorsanız geçerlidir. Düğüm döngü mantığınız bir parçası olarak uyguladığınız çerçeve `StartObject` ve `GetObject`yığın `EndObject` desteği, yapı bir DOM perspektifinden düşünülürse XAML düğüm yapısına inerken sayılabilir (veya) ve kapsamlar.

## <a name="traversing-and-entering-object-nodes"></a>Nesne Düğümlerini Geçiş ve Girme

XAML okuyucusu tarafından açıldığında düğüm akışındaki ilk düğüm, kök nesnenin başlangıç nesnesi düğümüdür. Tanım olarak, bu nesne her zaman tek bir nesne düğümüdür ve eşleri yoktur. Herhangi bir gerçek dünya XAML örneğinde, kök nesne daha fazla nesne tutan bir veya daha fazla özellise sahip olarak tanımlanır ve bu özelliklerin üye düğümleri vardır. Üye düğümleri sonra bir veya daha fazla nesne düğümleri var, ya da yerine bir değer düğümü sona erdirebilir. Kök nesne genellikle XAML metin biçimlendirmesinde öznitelik olarak atanan ancak XAML düğüm akışı gösterimindeki bir `Namescope` düğüm türüyle eşleyen XAML adskoplarını tanımlar.

Aşağıdaki XAML örneğini göz önünde bulundurun (bu rasgele XAML'dir, .NET'teki varolan türler tarafından desteklenmez). Bu nesne modelinde, `FavorCollection` `List<T>` wpf bilinen renk adları olarak `Balloon.Color` renkleri tanımlar ve `Color` atnitelik sözdizimi için bir tür dönüştürücü `Color` destekler benzer bir nesne tarafından desteklenen, `Favor`ve `Balloon` `NoiseMaker` atayabiliyor, ve atayabiliyor `Favor`varsayalım.

|XAML biçimlendirmesi|Ortaya çıkan XAML düğüm akışı|
|-----------------|--------------------------------|
|`<Party`|`Namespace`için düğüm`Party`|
|`xmlns="PartyXamlNamespace">`|`StartObject`için düğüm`Party`|
|`<Party.Favors>`|`StartMember`için düğüm`Party.Favors`|
||`StartObject`örtük düğüm`FavorCollection`|
||`StartMember`örtük `FavorCollection` öğeler özelliği için düğüm.|
|`<Balloon`|`StartObject`için düğüm`Balloon`|
|`Color="Red"`|`StartMember`için düğüm`Color`<br /><br /> `Value`öznitelik değer dizesi için düğüm`"Red"`<br /><br /> `EndMember`Için`Color`|
|`HasHelium="True"`|`StartMember`için düğüm`HasHelium`<br /><br /> `Value`öznitelik değer dizesi için düğüm`"True"`<br /><br /> `EndMember`Için`HasHelium`|
|`>`|`EndObject`Için`Balloon`|
|`<NoiseMaker>Loudest</NoiseMaker>`|`StartObject`için düğüm`NoiseMaker`<br /><br /> `StartMember`için düğüm`_Initialization`<br /><br /> `Value`başlatma değeri dizesi için düğüm`"Loudest"`<br /><br /> `EndMember`için düğüm`_Initialization`<br /><br /> `EndObject`Için`NoiseMaker`|
||`EndMember`örtük `FavorCollection` öğeler özelliği için düğüm.|
||`EndObject`örtük düğüm`FavorCollection`|
|`</Party.Favors>`|`EndMember`Için`Favors`|
|`</Party>`|`EndObject`Için`Party`|

XAML düğüm akışında, aşağıdaki davranışa güvenebilirsiniz:

- Bir `Namespace` düğüm varsa, xaml ad alanını `StartObject` ' ile bildirenden hemen `xmlns`önce akışa eklenir. XAML ve örnek düğüm akışı ile önceki tabloya tekrar bakın. `StartObject` Düğümlerin `Namespace` metin biçimlendirmedeki bildirim konumlarına göre nasıl aktarılana dikkat edin. Bu, ad alanı düğümlerinin her zaman düğüm akışında uyguladıkları düğümden önce göründüğü davranışı temsil eder. Bu tasarımın amacı, ad alanı bilgilerinin nesne yazarları için hayati önem taşıdığını ve nesne yazarının tür eşleme gerçekleştirmeye veya nesneyi işlemeye çalışmadan önce bilinmesi gerektiğidir. XAML ad alanı bilgilerini akışta uygulama kapsamının önüne yerleştirmek, düğüm akışını her zaman sunulan sırada işlemeyi kolaylaştırır.

- Yukarıdaki dikkate nedeniyle, en gerçek `Namespace` dünya biçimlendirme durumlarda ilk okuduğunuz bir veya daha fazla düğümleri başından itibaren `StartObject` düğümleri değil, kök geçiş.

- Bir `StartObject` düğüm tarafından `StartMember`takip `Value`edilebilir , `EndObject`, veya hemen . Hemen başka bir `StartObject`takip asla .

- A, `StartMember` bir `StartObject`, `Value`veya hemen `EndMember`bir tarafından takip edilebilir. Bu, değerin `GetObject`yeni bir değeri anında anlayacak bir `StartObject` değer yerine ana nesnenin varolan değerinden gelmesi gereken üyeler tarafından izlenebilir. Ayrıca yaklaşan `StartObject`bir düğüm `Namespace` için geçerlidir bir düğüm tarafından takip edilebilir. Hemen başka bir `StartMember`takip asla .

- Düğüm `Value` değerin kendisini temsil eder; "EndValue" diye bir şey yoktur. Bu sadece bir `EndMember`tarafından takip edilebilir .

  - Yapı tarafından kullanılabilecek nesnenin XAML başlatma metni nesne-değer yapısıyla sonuçlanmaz. Bunun yerine, adlı `_Initialization` bir üye için özel bir üye düğüm oluşturulur. ve bu üye düğüm başlatma değeri dizesini içerir. Varsa, `_Initialization` her zaman ilk `StartMember`. `_Initialization`bazı XAML hizmetleri gösterimlerinde XAML dili XAML adskopu `_Initialization` ile nitelikli olabilir, bu destek türleri tanımlanmış bir özellik olmadığını açıklamak için.

  - Üye-Değer birleşimi, değerin öznitelik ayarını temsil eder. Sonunda bu değeri işleme dahil bir değer dönüştürücü olabilir ve değer düz bir dize. Ancak, bir XAML nesne yazar bu düğüm akışı işleyene kadar değerlendirilmemiştir. XAML nesne yazarı gerekli XAML şema bağlamına, tür sistem eşleneme ve değer dönüşümleri için gerekli diğer desteğe sahip.

- Bir `EndMember` düğüm sonraki bir `StartMember` üye için bir düğüm veya `EndObject` üye sahibi için bir düğüm tarafından izlenebilir.

- Bir `EndObject` düğüm bir `EndMember` düğüm tarafından takip edilebilir. Ayrıca, bir koleksiyonun `StartObject` öğelerinde nesnelerin eş olduğu durumlar için bir düğüm tarafından da izlenebilir. Ya da yaklaşan `Namespace` `StartObject`bir düğüm için geçerlidir bir düğüm tarafından takip edilebilir.

  - Tüm düğüm akışının kapatılması benzersiz durumda `EndObject` için, kök bir şey tarafından takip edilmez; okuyucu artık dosya sonu ve <xref:System.Xaml.XamlReader.Read%2A> döndürür. `false`

## <a name="value-converters-and-the-xaml-node-stream"></a>Değer Dönüştürücüler ve XAML Düğüm Akışı

Değer dönüştürücü, biçimlendirme uzantısı, tür dönüştürücü (değer serileştiricileri dahil) veya XAML türü sistemi aracılığıyla değer dönüştürücüolarak bildirilen başka bir özel sınıf için genel bir terimdir. XAML düğüm akışında, tür dönüştürücü kullanımı ve biçimlendirme uzantısı kullanımı çok farklı gösterimlere sahiptir.

### <a name="type-converters-in-the-xaml-node-stream"></a>XAML Düğüm Akışında Tür Dönüştürücüler

Sonunda bir tür dönüştürücü kullanımı yla sonuçlanan bir öznitelik kümesi, XAML düğümü akışında bir üyenin değeri olarak bildirilir. XAML düğüm akışı bir tür dönüştürücü örnek nesnesi üretmek ve değeri ona geçmek için denemez. Bir tür dönüştürücünün dönüştürme uygulamasını kullanmak, XAML şema bağlamını çağırmak ve yazı eşleme için kullanmak gerektirir. Değeri işlemek için hangi tür dönüştürücü sınıfının kullanılması gerektiğini belirlemek bile XAML şema bağlamını dolaylı olarak gerektirir. Varsayılan XAML şema bağlamını kullandığınızda, bu bilgiler XAML türü sisteminden kullanılabilir. Bir XAML yazıcısına bağlanmadan önce XAML düğüm akışı düzeyindetür dönüştürücü sınıf bilgilerine <xref:System.Xaml.XamlMember> ihtiyacınız varsa, bunu ayarlanan üyenin bilgisinden elde edebilirsiniz. Ancak aksi takdirde, tür eşleç girişi, örneğin xaml nesne yazarı tarafından nesne oluşturma işlemi gerektiren işlemlerin geri kalanı gerçekleştirile kadar düz bir değer olarak XAML düğüm akışında korunmalıdır.

Örneğin, bunun için aşağıdaki sınıf tanımı anahat ve XAML kullanımı düşünün:

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

Bu kullanım için XAML düğüm akışının metin gösterimi aşağıdaki gibi ifade edilebilir:

`StartObject`temsil <xref:System.Xaml.XamlType> ile`GameBoard`

`StartMember`temsil <xref:System.Xaml.XamlMember> ile`BoardSize`

`Value`düğüm, metin dizeli " "`8x8`

`EndMember`Eşleşen`BoardSize`

`EndObject`Eşleşen`GameBoard`

Bu düğüm akışında tür dönüştürücü örneği olmadığına dikkat edin. Ama <xref:System.Xaml.XamlMember.TypeConverter%2A?displayProperty=nameWithType> <xref:System.Xaml.XamlMember> for'u `BoardSize`arayarak tür dönüştürücü bilgilerini alabilirsiniz. Geçerli bir XAML şema bağlamınız varsa, 'den <xref:System.Xaml.Schema.XamlValueConverter%601.ConverterInstance%2A>bir örnek alarak dönüştürücü yöntemlerini de çağırabilirsiniz.

### <a name="markup-extensions-in-the-xaml-node-stream"></a>XAML Düğümü Akışında Biçimlendirme Uzantıları

Biçimlendirme uzantısı kullanımı XAML düğümü akışında, nesnenin biçimlendirme uzantısı örneğini temsil ettiği bir üye içindeki nesne düğümü olarak bildirilir. Böylece bir biçimlendirme uzantısı kullanımı, düğüm akışı gösteriminde bir tür dönüştürücü kullanımından daha açık bir şekilde sunulur ve daha fazla bilgi taşır. <xref:System.Xaml.XamlMember>bilgiler biçimlendirme uzantısı hakkında size bir şey söylemiş olabilirsiniz, çünkü kullanım durumsaldır ve olası her biçimlendirme durumunda değişir; tür dönüştürücüler ile olduğu gibi türü veya üyesi başına adanmış ve örtülü değildir.

Biçimlendirme uzantılarının nesne düğümleri olarak düğüm akışı gösterimi, biçimlendirme uzantısı kullanımı XAML metin biçimlendirmesinde öznitelik biçiminde yapılmış olsa bile (genellikle böyledir) durumdur. Açık nesne öğesi formu kullanılan Biçimlendirme uzantısı kullanımları aynı şekilde işlenir.

Biçimlendirme uzantısı nesne düğümü içinde, bu biçimlendirme uzantısı üyeleri olabilir. XAML düğüm akışı gösterimi, ister konumsal parametre kullanımı ister açık adlandırılmış parametrelere sahip bir kullanım olsun, bu biçimlendirme uzantısının kullanımını korur.

Konumsal parametre kullanımı için XAML düğümü akışı, kullanımı kaydeden XAML dili tanımlı bir özellik `_PositionalParameters` içerir. Bu özellik, <xref:System.Collections.Generic.List%601> kısıtlaması olan <xref:System.Object> genel bir özelliktir. Kısıtlama, bir konumsal parametre kullanımı iç içe geçmiş biçimlendirme uzantısı kullanımları içerebilir, çünkü kısıtlama ve dize değildir. Kullanımdan konumparametrelerine erişmek için, liste boyunca yineleyebilir ve tek tek liste değerleri için dizinleyicileri kullanabilirsiniz.

Adlandırılmış parametre kullanımı için, adlandırılmış her parametre düğüm akışında bu adın bir üye düğümü olarak temsil edilir. İç içe biçimlendirilmiş biçimlendirme uzantısı kullanımı olabileceğinden, üye değerler mutlaka dizeleri değildir.

`ProvideValue`biçimlendirme uzantısından henüz çağrılmadı. Ancak, düğüm akışında incelediğinizde biçimlendirme uzantısı düğümünde çağrılan `WriteEndObject` bir XAML okuyucusu ve XAML yazarı bağlanırsa çağrılır. Bu nedenle, genellikle yük yolunda nesne grafiği oluşturmak için kullanılacak aynı XAML şema bağlamı gerekir. Aksi `ProvideValue` takdirde, herhangi bir biçimlendirme uzantısı burada özel durumlar atabilir, çünkü beklenen hizmetler kullanılabilir değildir.

## <a name="xaml-and-xml-language-defined-members-in-the-xaml-node-stream"></a>XAML Düğümü Akışında XAML ve XML Dil Tanımlı Üyeler

Bazı üyeler, açık <xref:System.Xaml.XamlMember> bir arama veya inşaat yerine, bir XAML okuyucunun yorumları ve kuralları nedeniyle XAML düğüm akışına tanıtılır. Genellikle, bu üyeler XAML yönergeleridir. Bazı durumlarda, XAML düğüm akışına yönergeyi tanıtan XAML okuma eylemidir. Başka bir deyişle, özgün giriş XAML metni üye yönergesini açıkça belirtmedi, ancak XAML okuyucusu, yapısal bir XAML kuralını karşılamak ve bu bilgiler kaybolmadan önce XAML düğüm akışındaki bilgileri bildirmek için yönergeyi ekler.

Aşağıdaki liste, XAML okuyucusunun bir yönerge XAML üye düğümü getirmesinin beklendiği tüm durumları ve üye düğümün .NET XAML Hizmetleri uygulamalarında nasıl tanımlandığını not eder.

- **Nesne düğümü için başlatma metni:** Bu üye düğümün `_Initialization`adı, bir XAML yönergesini temsil eder ve XAML dilinde xaml ad alanında tanımlanır. Bunun için statik bir varlık <xref:System.Xaml.XamlLanguage.Initialization%2A>alabilirsiniz.

- **Biçimlendirme uzantısı için konumsal parametreler:** Bu üye düğümün adı `_PositionalParameters`, ve XAML dil XAML ad alanında tanımlanır. Her zaman, xaml girişinde verilen `,` delimiter karakterine bölünerek önceden ayrılmış konumsal bir parametre olan genel bir nesne listesi içerir. Konumsal parametreler yönergesi için statik <xref:System.Xaml.XamlLanguage.PositionalParameters%2A>bir varlık elde edebilirsiniz.

- **Bilinmeyen içerik:** Bu üye düğümün `_UnknownContent`adı. Açıkçası, bir <xref:System.Xaml.XamlDirective>, ve XAML dil XAML isim alanında tanımlanır. Bu yönerge, xaml nesne öğesinin kaynak XAML'de içerik içerdiği, ancak şu anda kullanılabilir XAML şeması bağlamında hiçbir içerik özelliğinin belirlenemeden bulunduğu durumlar için sentinel olarak kullanılır. Bu servis talebinin bir XAML düğüm akışında, `_UnknownContent`adı geçen üyeleri denetleyerek algılayabilirsiniz. Bir yük yolu XAML düğüm akışında başka bir <xref:System.Xaml.XamlObjectWriter> eylem yapılmazsa, varsayılan `WriteEndObject` `_UnknownContent` değer, herhangi bir nesnede üyeyle karşılaştığında denenmeye başlar. Varsayılan <xref:System.Xaml.XamlXmlWriter> atmaz ve üyeyi örtülü olarak ele alır. Statik bir varlık `_UnknownContent` için <xref:System.Xaml.XamlLanguage.UnknownContent%2A>.

- **Koleksiyonun toplama özelliği:** XAML için kullanılan bir koleksiyon sınıfının destek CLR türü genellikle toplama öğelerini tutan özel bir adlandırılmış özelliğe sahip olsa da, bu özellik tür çözümlemesi desteklemeden önce bir XAML türü sistemi tarafından bilinmemektedir. Bunun yerine, XAML düğüm akışı, bir `Items` yer tutucuyu xaml koleksiyonunun bir üyesi olarak tanıtır. .NET XAML Hizmetleri uygulamasında, bu yönergenin adı veya `_Items`düğüm akışındaki üye . Bu yönerge için bir <xref:System.Xaml.XamlLanguage.Items%2A>sabit elde edilebilir.

    Bir XAML düğüm akışı, destek türü çözünürlüğü ve XAML şema bağlamına bağlı olarak ayrıştırılamaz öğeleri olan bir Öğeler özelliği içerebilir. Örneğin,

- **XML tanımlı üyeler:** XML tanımlı `xml:base` `xml:lang` ve `xml:space` üyeler XAML yönergeleri olarak `base` `lang`, `space` ve .NET XAML Hizmetleri uygulamaları olarak bildirilir. Bunların ad alanı XML ad `http://www.w3.org/XML/1998/namespace`alanıdır. Bunların her biri için sabitler <xref:System.Xaml.XamlLanguage>elde edilebilir.

## <a name="node-order"></a>Düğüm Sırası

Bazı durumlarda, <xref:System.Xaml.XamlXmlReader> XAML düğümü akışındaki XAML düğümlerinin sırasını değiştirir, biçimlendirmede görüntülenince veya XML olarak işlenmişse düğümlerin görünme sırasına karşılık. Bu, düğüm akışını yalnızca ileriye doğru <xref:System.Xaml.XamlObjectWriter> işleyebilir şekilde sıralamak için yapılır.  .NET XAML Services'da, XAML okuyucusu düğüm akışının XAML nesne yazarı tüketicileri için bir performans optimizasyonu olarak bu görevi XAML yazarına bırakmak yerine düğümleri yeniden sıralar.

Belirli yönergeler özellikle bir nesne öğesinden bir nesnenin oluşturulması için daha fazla bilgi sağlamak için tasarlanmıştır. Bu direktifler `Initialization`şunlardır: `FactoryMethod` `Arguments`, `PositionalParameters`, `TypeArguments`, , . .NET XAML Services XAML okuyucuları, bir nesnenin `StartObject`bir sonraki bölümünde açıklanan nedenlerle bu yönergeleri düğüm akışında ilk üye olarak yerleştirmeye çalışır.

### <a name="xamlobjectwriter-behavior-and-node-order"></a>XamlObjectWriter Davranış ve Düğüm Sırası

`StartObject`a <xref:System.Xaml.XamlObjectWriter> için mutlaka xaml nesne yazar için hemen nesne örneği oluşturmak için bir sinyal değildir. XAML, bir nesneyi ek girdiyle başlatmayı ve ilk nesneyi oluşturmak için parametresiz bir oluşturucuya ve ancak daha sonra özellikleri ayarlamaya tamamen güvenmemelerini mümkün kınlayan çeşitli dil özellikleri içerir. Bu özellikler <xref:System.Windows.Markup.XamlDeferLoadAttribute>şunlardır: ; başlatma metni; [x:TypeArguments](xtypearguments-directive.md); biçimlendirme uzantısının konumsal parametreleri; fabrika yöntemleri ve ilişkili [x:Bağımsız değişken](xarguments-directive.md) düğümleri (XAML 2009). Bu durumların her biri gerçek nesne yapısını geciktirir ve düğüm akışı yeniden sıralandığından, XAML nesne swriter, özellikle bu nesne türü için bir yapı yönergesi olmayan bir başlangıç üyesi karşılaşıldığında örneği gerçekten oluşturma davranışına güvenebilir.

### <a name="getobject"></a>GetObject

`GetObject`yeni bir nesne oluşturmak yerine, bir XAML nesne yazarı yerine nesnenin içeren özelliğinin değerini almalıdır bir XAML düğümü temsil eder. XAML düğümü `GetObject` akışında bir düğümle karşılaşılan tipik bir durum, içeren özelliğin destek türünün nesne modelinde kasıtlı olarak yalnızca okunduğu bir koleksiyon nesnesi veya sözlük nesnesi içindir. Bu senaryoda, koleksiyon veya sözlük genellikle oluşturulur ve sahip bir tür başlatma mantığı tarafından (genellikle boş) başharfe çevrilir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xaml.XamlObjectReader>
- [XAML Hizmetleri](index.md)
- [XAML Ad Uzayları](namespaces.md)
