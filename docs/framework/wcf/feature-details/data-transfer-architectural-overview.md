---
title: Veri Aktarımı Mimarisi Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data transfer [WCF], architectural overview
ms.assetid: 343c2ca2-af53-4936-a28c-c186b3524ee9
ms.openlocfilehash: f34bf82ec44140827c5d8da59911afe10ab7a853
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84576479"
---
# <a name="data-transfer-architectural-overview"></a>Veri Aktarımı Mimarisi Genel Bakış
Windows Communication Foundation (WCF), bir mesajlaşma altyapısı olarak düşünülebilir. Daha fazla eylem için ileti alabilir, bunları işleyebilir ve Kullanıcı koduna gönderebilir veya Kullanıcı kodu tarafından verilen verilerden iletiler oluşturabilir ve bunları bir hedefe teslim edebilir. Gelişmiş geliştiricilere yönelik bu konu, iletileri ve kapsanan verileri işleme mimarisini açıklar. Verilerin nasıl gönderileceğini ve alınacağını gösteren daha basit, görev odaklı bir görünüm için bkz. [hizmet sözleşmeleri içinde veri aktarımı belirtme](specifying-data-transfer-in-service-contracts.md).  
  
> [!NOTE]
> Bu konu, WCF nesne modelini inceleyerek görünmeyen WCF uygulama ayrıntılarını açıklamaktadır. Belgelenmiş uygulama ayrıntıları ile ilgili olarak iki sözcük dikkatli olun. İlk olarak, açıklamalar basitleştirilmiştir; iyileştirmeler veya diğer nedenlerden dolayı gerçek uygulama daha karmaşık olabilir. İkinci olarak, belirli uygulama ayrıntılarına asla güvenmelisiniz, aksi halde, bu, sürümden sürüme veya bir bakım sürümünde bile fark etmeksizin değişebilir.  
  
## <a name="basic-architecture"></a>Temel mimari  
 WCF ileti işleme yeteneklerinin çekirdeği, <xref:System.ServiceModel.Channels.Message> [Ileti sınıfını kullanma](using-the-message-class.md)konusunda ayrıntılı olarak açıklanan sınıftır. WCF çalışma zamanı bileşenleri iki ana parçaya ayrılabilir: kanal yığını ve hizmet çerçevesi, <xref:System.ServiceModel.Channels.Message> sınıf bağlantı noktası olur.  
  
 Kanal yığını, <xref:System.ServiceModel.Channels.Message> ileti verilerinin gönderilmesi veya alınmasına karşılık gelen geçerli bir örnek ve bazı eylemler arasında dönüştürme yapmaktan sorumludur. Gönderme tarafında, kanal yığını geçerli bir <xref:System.ServiceModel.Channels.Message> örnek alır ve bazı işlemler yapıldıktan sonra, iletiyi göndermek için mantıksal olarak karşılık gelen bazı işlemleri gerçekleştirir. Bu eylem TCP veya HTTP paketleri gönderiyor, Message Queuing ileti sıraya alıyor, bir veritabanına ileti yazıyor, dosyayı bir dosya paylaşımında ya da uygulamaya bağlı olarak başka bir eylem olarak kaydediyor olabilir. En yaygın eylem, iletiyi bir ağ protokolü üzerinden gönderiyor. Alma tarafında, tersi durum — bir işlem algılanır (TCP veya HTTP paketleri ya da başka bir eylem olabilir) ve işlemeden sonra kanal yığını bu eylemi geçerli bir <xref:System.ServiceModel.Channels.Message> örneğe dönüştürür.  
  
 WCF <xref:System.ServiceModel.Channels.Message> 'yi, sınıfını ve kanal yığınını doğrudan kullanarak kullanabilirsiniz. Ancak bunu yapmak zor ve zaman alır. Ayrıca, <xref:System.ServiceModel.Channels.Message> nesne meta veri desteği sağlamaz, bu nedenle WCF 'yi bu şekilde kullanıyorsanız, türü kesin BELIRLENMIŞ WCF istemcileri oluşturamazsınız.  
  
 Bu nedenle WCF, nesneleri oluşturmak ve almak için kullanabileceğiniz, kullanımı kolay bir programlama modeli sağlayan bir hizmet çerçevesi içerir `Message` . Service Framework, Hizmetleri hizmet sözleşmeleri kavramı aracılığıyla .NET Framework türlerine eşler ve yalnızca özniteliğiyle işaretlenmiş .NET Framework Yöntemler olan Kullanıcı işlemlerine ileti gönderir <xref:System.ServiceModel.OperationContractAttribute> (daha fazla bilgi için bkz. [hizmet sözleşmelerini tasarlama](../designing-service-contracts.md)). Bu yöntemlerin parametreleri ve dönüş değerleri olabilir. Hizmet tarafında, hizmet çerçevesi gelen <xref:System.ServiceModel.Channels.Message> örnekleri parametrelere dönüştürür ve dönüş değerlerini giden <xref:System.ServiceModel.Channels.Message> örneklere dönüştürür. İstemci tarafında, tersi olur. Örneğin, aşağıdaki işlemi göz önünde bulundurun `FindAirfare` .  
  
 [!code-csharp[c_DataArchitecture#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#1)]
 [!code-vb[c_DataArchitecture#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#1)]  
  
 `FindAirfare`İstemci üzerinde bir değer çağırılır. İstemci üzerindeki hizmet çerçevesi, `FromCity` ve `ToCity` parametrelerini giden <xref:System.ServiceModel.Channels.Message> örneğe dönüştürür ve gönderilecek kanal yığınına geçirir.  
  
 Hizmet tarafında, bir <xref:System.ServiceModel.Channels.Message> örnek kanal yığınından ulaştığında, hizmet çerçevesi, ve parametrelerini doldurmak için iletiden ilgili verileri ayıklar `FromCity` `ToCity` ve ardından hizmet tarafı `FindAirfare` yöntemini çağırır. Yöntem döndüğünde, Service Framework döndürülen tamsayı değerini ve `IsDirectFlight` Çıkış parametresini alır ve <xref:System.ServiceModel.Channels.Message> Bu bilgileri içeren bir nesne örneği oluşturur. Daha sonra `Message` örneği istemciye geri gönderilmek üzere kanal yığınına geçirir.  
  
 İstemci tarafında, <xref:System.ServiceModel.Channels.Message> yanıt iletisini içeren bir örnek kanal yığınından ortaya çıktı. Service Framework, dönüş değerini ve `IsDirectFlight` değerini ayıklar ve bunları istemci çağıranına döndürür.  
  
## <a name="message-class"></a>Message Sınıfı  
 <xref:System.ServiceModel.Channels.Message>Sınıfın bir iletinin soyut temsili olması amaçlanmıştır, ancak TASARıMı SOAP iletisine kesin bir şekilde bağlıdır. <xref:System.ServiceModel.Channels.Message>, Üç ana bilgi parçasını içerir: ileti gövdesi, ileti üstbilgileri ve ileti özellikleri.  
  
## <a name="message-body"></a>İleti gövdesi  
 İleti gövdesi iletinin gerçek veri yükünü temsil etmek üzere tasarlanmıştır. İleti gövdesi her zaman bir XML bilgi kümesi olarak temsil edilir. Bu, WCF 'de oluşturulan veya alınan tüm iletilerin XML biçiminde olması anlamına gelmez. İleti gövdesinin nasıl yorumlanacağına karar vermek için kanal yığınına kadar olur. Bu, XML olarak yayabilir, başka bir biçime dönüştürebilir, hatta tamamen atlayabilirsiniz. Kuşkusuz, her bağlamanın WCF sağladığı ileti gövdesi, bir SOAP zarfının gövde bölümünde XML içeriği olarak temsil edilir.  
  
 `Message`Sınıfın, gövdesi temsil eden XML verileri içeren bir arabellek içermesi gerekmediğini fark etmek önemlidir. Mantıksal olarak, `Message` BIR XML bilgi kümesi içerir, ancak bu bilgi kümesi dinamik olarak oluşturulabilir ve bellekte hiç fiziksel olarak bulunmayabilir.  
  
### <a name="putting-data-into-the-message-body"></a>Verilerin Ileti gövdesine yerleştirilmesi  
 Bir ileti gövdesine veri yerleştirmek için Tekdüzen mekanizması yoktur. <xref:System.ServiceModel.Channels.Message>Sınıfının bir soyut yöntemi vardır, <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%28System.Xml.XmlDictionaryWriter%29> Bu bir <xref:System.Xml.XmlDictionaryWriter> . Sınıfın her alt sınıfı <xref:System.ServiceModel.Channels.Message> , bu yöntemi geçersiz kılmaktan ve kendi içeriğini yazmadan sorumludur. İleti gövdesi mantıksal olarak, üreten XML bilgi kümesini içerir `OnWriteBodyContent` . Örneğin, aşağıdaki alt sınıfı göz önünde bulundurun `Message` .  
  
 [!code-csharp[c_DataArchitecture#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#2)]
 [!code-vb[c_DataArchitecture#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#2)]  
  
 Fiziksel olarak, bir `AirfareRequestMessage` örnek yalnızca iki dize ("fromCity" ve "toCity") içerir. Ancak, mantıksal olarak ileti aşağıdaki XML bilgi kümesini içerir:  
  
```xml  
<airfareRequest>  
    <from>Tokyo</from>  
    <to>London</to>  
</airfareRequest>  
```  
  
 Kuşkusuz, işlem sözleşmesi parametrelerinden önceki bir ileti oluşturmak üzere Service Framework 'ü kullanabilmeniz için normalde bu şekilde ileti oluşturmayız. Ayrıca, <xref:System.ServiceModel.Channels.Message> sınıfının `CreateMessage` ortak içerik türleri ile ileti oluşturmak için kullanabileceğiniz statik yöntemleri vardır: boş bir ileti, ile XML 'e serileştirilmiş bir nesne içeren bir ILETI, soap hatası içeren bir ileti, <xref:System.Runtime.Serialization.DataContractSerializer> bir Ile temsil edilen XML içeren bir ileti <xref:System.Xml.XmlReader> ve bu şekilde devam eder.  
  
### <a name="getting-data-from-a-message-body"></a>Ileti gövdesinden veri alma  
 İleti gövdesinde depolanan verileri iki ana şekilde ayıklayabilirsiniz:  
  
- <xref:System.ServiceModel.Channels.Message.WriteBodyContents%28System.Xml.XmlDictionaryWriter%29>Yöntemini çağırarak ve BIR XML yazıcısına geçirerek, tüm ileti gövdesini tek seferde alabilirsiniz. Tüm ileti gövdesi bu yazıcıya yazılır. Tüm ileti gövdesinin tek seferde alınması de *ileti yazma*olarak adlandırılır. Yazma işlemi öncelikli olarak ileti gönderilirken kanal yığını tarafından yapılır — kanal yığınının bir bölümü genellikle tüm ileti gövdesine erişebilir, kodlanacak ve gönderilir.  
  
- İleti gövdesinden bilgi almanın bir başka yolu da <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents> BIR XML okuyucusu çağırmak ve almak. İleti gövdesine, okuyucudaki Yöntemler çağrılırken gerektiği şekilde sırayla erişilebilir. İleti gövdesinin *bir ileti okuma*da denir. İletiyi okumak, öncelikle ileti alırken Service Framework tarafından kullanılır. Örneğin,, kullanılırken, <xref:System.Runtime.Serialization.DataContractSerializer> hizmet çerçevesi gövde üzerinde BIR XML okuyucusu alır ve bunu seri kaldırma altyapısına iletir. böylece, öğe tarafından ileti öğesini okumaya başlar ve ilgili nesne grafiğini oluşturulur.  
  
 İleti gövdesi yalnızca bir kez alınabilir. Bu, yalnızca ileri akışlarla çalışmayı mümkün kılar. Örneğin, <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%28System.Xml.XmlDictionaryWriter%29> öğesinden okuyan <xref:System.IO.FileStream> ve sonuçları bir xml bilgi kümesi olarak döndüren bir geçersiz kılma yazabilirsiniz. Dosyanın başlangıcına "geri sarma" gerek kalmaz.  
  
 `WriteBodyContents`Ve `GetReaderAtBodyContents` yöntemleri, ileti gövdesinin daha önce hiç alınamamıştır ve sonra `OnWriteBodyContents` sırasıyla veya olarak çağrı yapılır `OnGetReaderAtBodyContents` .  
  
## <a name="message-usage-in-wcf"></a>WCF 'de ileti kullanımı  
 Çoğu ileti, *giden* (kanal yığını tarafından gönderilmek üzere Service Framework tarafından oluşturulan) veya *gelen* (kanal yığınından gelen ve hizmet çerçevesi tarafından yorumlanan) olarak sınıflandırılabilir. Ayrıca, kanal yığını, ara belleğe alınmış ya da akış modunda çalışabilir. Hizmet çerçevesi Ayrıca akışlı veya akış olmayan bir programlama modeli sunabilir. Bu, uygulamanın Basitleştirilmiş ayrıntılarıyla birlikte aşağıdaki tabloda listelenen servis taleplerine yol açar.  
  
|Mesaj türü|İletideki gövde verileri|Yazma (OnWriteBodyContents) uygulama|Okuma (OnGetReaderAtBodyContents) uygulama|  
|------------------|--------------------------|--------------------------------------------------|-------------------------------------------------------|  
|Giden, akış olmayan programlama modelinden oluşturulan|İletiyi yazmak için gereken veriler (örneğin, bir nesne ve <xref:System.Runtime.Serialization.DataContractSerializer> seri hale getirmek için gereken örnek) *|Depolanan verileri temel alarak iletiyi yazmak için özel mantık (örneğin, `WriteObject` `DataContractSerializer` kullanılmakta olan seri hale getirici ise üzerinde çağırın) *|Arama `OnWriteBodyContents` yapın, sonuçları arabelleğe alarak arabellek üzerinde BIR XML okuyucusu döndürün|  
|Giden, akışlı programlama modelinden oluşturulan|`Stream`Yazılacak verilerle birlikte *|Yöntemi kullanarak depolanan akıştan veri yazma <xref:System.Xml.IStreamProvider> *|Arama `OnWriteBodyContents` yapın, sonuçları arabelleğe alarak arabellek üzerinde BIR XML okuyucusu döndürün|  
|Akış kanalı yığınından gelen|`Stream`Üzerinde bir ağ üzerinden gelen verileri temsil eden bir nesne <xref:System.Xml.XmlReader>|İçeriği `XmlReader` depolanan bilgisayardan yaz`WriteNode`|Depolanan`XmlReader`|  
|Akış olmayan kanal yığınından gelen|Üzerine gelen gövde verilerini içeren bir arabellek `XmlReader`|İçeriği `XmlReader` depolanan bilgisayardan yazar`WriteNode`|Depolanan dili döndürür|  
  
 \*Bu öğeler doğrudan alt `Message` sınıflarda, ancak sınıfının alt sınıflarında uygulanmaz <xref:System.ServiceModel.Channels.BodyWriter> . Hakkında daha fazla bilgi için <xref:System.ServiceModel.Channels.BodyWriter> bkz. [Ileti sınıfını kullanma](using-the-message-class.md).  
  
## <a name="message-headers"></a>İleti üstbilgileri  
 İleti, üst bilgiler içerebilir. Üst bilgi, bir ad, ad alanı ve diğer diğer özelliklerle ilişkili bir XML bilgi kümesinden mantıksal olarak oluşur. İleti üst bilgilerine `Headers` üzerindeki özelliği kullanılarak erişilir <xref:System.ServiceModel.Channels.Message> . Her üst bilgi bir sınıf tarafından temsil edilir <xref:System.ServiceModel.Channels.MessageHeader> . Normalde, SOAP iletileriyle çalışmak üzere yapılandırılmış bir kanal yığını kullanılırken, ileti üst bilgileri SOAP ileti üst bilgilerine eşlenir.  
  
 Bilgileri bir ileti başlığına koymak ve bundan bilgi ayıklamak ileti gövdesini kullanmaya benzer. Akış desteklenmediğinden işlem biraz basitleştirilmiştir. Aynı üstbilginin içeriğine birden çok kez erişmek mümkündür ve üstbilgilere rastgele sırayla erişilebilir ve üst bilgilerin her zaman arabelleğe alınbilmesini sağlayabilirsiniz. Bir üst bilgi üzerinde bir XML okuyucusu almak için kullanılabilen genel amaçlı bir mekanizma yoktur, ancak bu `MessageHeader` tür bir özelliği olan okunabilir bir üst bilgiyi temsil eden WCF 'nin dahili bir alt sınıfı vardır. Bu tür, `MessageHeader` özel uygulama üstbilgileri ile bir ileti geldiğinde kanal yığını tarafından oluşturulur. Bu, hizmet çerçevesinin <xref:System.Runtime.Serialization.DataContractSerializer> Bu üst bilgileri yorumlamak için gibi bir seri kaldırma altyapısı kullanmasına olanak sağlar.  
  
 Daha fazla bilgi için bkz. [Ileti sınıfını kullanma](using-the-message-class.md).  
  
## <a name="message-properties"></a>İleti özellikleri  
 Bir ileti, özellikler içerebilir. Bir *özellik* , bir dize adıyla ilişkili .NET Framework nesnedir. Özellikleri üzerinde özelliği aracılığıyla erişilir `Properties` `Message` .  
  
 İleti gövdesinin ve ileti başlıklarından farklı olarak (sırasıyla SOAP gövdesine ve SOAP üst bilgilerine eşlenir), ileti özellikleri normalde iletilerle birlikte gönderilmez veya alınmaz. İleti özellikleri, birincil olarak kanal yığınındaki çeşitli kanallar arasında ve kanal yığını ile hizmet modeli arasında ileti hakkında verileri geçirmek için bir iletişim mekanizması olarak mevcuttur.  
  
 Örneğin, WCF 'nin bir parçası olarak dahil edilen HTTP taşıma kanalı, istemcilere yanıt gönderdiğinde "404 (bulunamadı)" ve "500 (Iç sunucu hatası)" gibi çeşitli HTTP durum kodları üretebilme yeteneğine sahiptir. Bir yanıt iletisi göndermeden önce, `Properties` öğesinin `Message` ' de türünde bir nesne Içeren "HttpResponse" adlı bir özellik içerip içermediğini kontrol eder <xref:System.ServiceModel.Channels.HttpResponseMessageProperty> . Böyle bir özellik bulunursa, <xref:System.ServiceModel.Channels.HttpResponseMessageProperty.StatusCode%2A> özelliğine bakar ve bu durum kodunu kullanacaktır. Bulunmazsa, varsayılan "200 (Tamam)" kodu kullanılır.  
  
 Daha fazla bilgi için bkz. [Ileti sınıfını kullanma](using-the-message-class.md).  
  
### <a name="the-message-as-a-whole"></a>Ileti bir bütün olarak  
 Şimdiye kadar, iletinin çeşitli bölümlerine yalıtımıyla erişim için yöntemler açıklanmıştır. Ancak, <xref:System.ServiceModel.Channels.Message> sınıfı tüm iletiyle birlikte çalışmak için yöntemler de sağlar. Örneğin, `WriteMessage` yöntemi tüm iletiyi BIR XML yazıcısına yazar.  
  
 Bunun mümkün olması için, tüm `Message` örnek ve BIR XML bilgi kümesi arasında bir eşlemenin tanımlanması gerekir. Böyle bir eşleme, aslında vardır: WCF bu eşlemeyi tanımlamak için SOAP standardını kullanır. Bir `Message` Örnek BIR XML bilgi kümesi olarak yazıldığında, sonuçta elde edilen bilgi kümesi iletiyi içeren geçerli BIR SOAP Envelope. Bu nedenle, `WriteMessage` normalde aşağıdaki adımları gerçekleştirir:  
  
1. SOAP Envelope öğesi açma etiketi yazın.  
  
2. SOAP üst bilgisi öğesi açma etiketi yazın, tüm üst bilgileri yazın ve üst bilgi öğesini kapatın.  
  
3. SOAP body öğesi açılış etiketini yazın.  
  
4. `WriteBodyContents`Gövdeyi yazmak için çağrı veya eşdeğer bir yöntem.  
  
5. Body ve Envelope öğelerini kapatın.  
  
 Yukarıdaki adımlar SOAP standardına yakından bağlıdır. Bu, SOAP 'ın birden çok sürümünün mevcut olması nedeniyle karmaşıktır. Örneğin, kullanımdaki SOAP sürümünü bilmeden SOAP Envelope öğesini doğru bir şekilde yazmak olanaksızdır. Ayrıca, bazı durumlarda, bu karmaşık SOAP 'a özgü eşlemeyi tamamen kapatmak istenebilir.  
  
 Bu amaçlar için üzerinde bir `Version` Özellik sağlanır `Message` . İleti yazılırken kullanılacak SOAP sürümüne ayarlanabilir veya `None` SOAP 'a özgü tüm eşlemeleri engellemek için olarak ayarlanabilir. `Version`Özelliği olarak ayarlandıysa `None` , tüm iletiyle çalışan yöntemler ileti yalnızca gövdesinden oluyordu gibi davranır, örneğin, `WriteMessage` `WriteBodyContents` yukarıda listelenen birden çok adımı gerçekleştirmek yerine yalnızca çağırır. Gelen iletilerde, `Version` otomatik olarak algılanır ve doğru şekilde ayarlanacaktır.  
  
## <a name="the-channel-stack"></a>Kanal yığını  
  
### <a name="channels"></a>Kanallar  
 Daha önce belirtildiği gibi, kanal yığını, giden <xref:System.ServiceModel.Channels.Message> örnekleri bazı eylemlere (örneğin, ağ üzerinden paket gönderme) veya bazı eylemleri (örneğin, ağ paketleri alma) gelen örneklere dönüştürmekten sorumludur `Message` .  
  
 Kanal yığını, sırayla sıralanan bir veya daha fazla kanaldan oluşur. Giden bir `Message` örnek, yığındaki ilk kanala geçirilir ( *en üstteki kanal*olarak da adlandırılır), bunu yığındaki bir sonraki kanala geçirir ve bu şekilde devam eder. İleti, *aktarım kanalı*olarak adlandırılan son kanalda sonlanır. Gelen iletiler, aktarım kanalında kaynaklanar ve yığından kanala kadar kanal üzerinden geçirilir. En üstteki kanaldan ileti genellikle hizmet çerçevesine geçirilir. Bu, uygulama iletileri için normal bir modelken, bazı kanallar biraz farklı çalışabilir, örneğin, yukarıdaki kanaldan bir ileti iletilmeksizin kendi altyapı iletilerini gönderebilirler.  
  
 Kanallar, yığın aracılığıyla geçerken ileti üzerinde çeşitli yollarla işlem gösterebilir. En yaygın işlem, giden bir iletiye üst bilgi ekliyor ve gelen bir iletideki üst bilgileri okuyor. Örneğin, bir kanal bir iletinin dijital imzasını gösterebilir ve üst bilgi olarak ekleyebilir. Kanal Ayrıca, gelen iletilerde bu dijital imza üst bilgisini inceleyebilir ve kanal yığınının yolunu yaparak geçerli imzaya sahip olmayan iletileri engelleyebilir. Ayrıca kanallar, ileti özelliklerini de ayarlayabilir veya inceler. İleti gövdesi genellikle değiştirilmez, ancak buna izin verilir; Örneğin, WCF güvenlik kanalı ileti gövdesini şifreleyebilir.  
  
### <a name="transport-channels-and-message-encoders"></a>Taşıma kanalları ve Ileti kodlayıcıları  
 Yığındaki en altta bulunan kanal, <xref:System.ServiceModel.Channels.Message> başka kanallar tarafından değiştirilmiş şekilde giden bir işlemi bazı eylemlere dönüştürmekten sorumludur. Alma tarafında bu, bazı eylemleri `Message` diğer kanallar sürecine dönüştüren kanaldır.  
  
 Daha önce belirtildiği gibi, eylemler değiştirilebilir: çeşitli protokoller üzerinden ağ paketleri gönderme veya alma, iletiyi bir veritabanında okuma veya yazma ya da birkaç örnek sağlamak için bir Message Queuing sırasındaki iletiyi sıraya alma veya sıradan kaldırma. Tüm bu eylemlerin yaygın olarak bir şeyi vardır: WCF `Message` örneği ve gönderilebilecek, alınabilen, okunan, yazılan, sıraya alınmış veya kuyruğa alınan bir bayt grubu arasında bir dönüşüm gerektirir. Bir bayt grubuna dönüştürme işlemine `Message` *kodlama*denir ve bir bayt grubundan oluşturmak için ters işlem `Message` *kod çözme*olarak adlandırılır.  
  
 Çoğu aktarım kanalı kodlama ve kod çözme işini gerçekleştirmek için *ileti kodlayıcıları* adlı bileşenleri kullanır. İleti Kodlayıcısı, sınıfının bir alt sınıfıdır <xref:System.ServiceModel.Channels.MessageEncoder> . `MessageEncoder``ReadMessage` `WriteMessage` , ve bayt gruplarını dönüştürmek için çeşitli ve yöntem aşırı yüklemeleri içerir `Message` .  
  
 Gönderme tarafında, bir arabelleğe alma aktarım kanalı, `Message` onun üzerindeki bir kanaldan aldığı nesneyi geçirir `WriteMessage` . Bu, daha sonra eylemini gerçekleştirmek için kullandığı bir bayt dizisini geri alır (Bu baytları geçerli TCP paketleri olarak paketleme ve doğru hedefe göndermek gibi). Bir akış aktarım kanalı, ilk olarak bir `Stream` (örneğin, gıden TCP bağlantısı üzerinden) oluşturur ve sonra hem hem de `Stream` ' nin, `Message` iletiyi yazan uygun aşırı yüklemeye gönderilmesi gerekir `WriteMessage` .  
  
 Alma tarafında, bir arabelleğe alma aktarım kanalı gelen baytları (örneğin, gelen TCP paketlerinden) bir diziye ayıklar ve `ReadMessage` `Message` Kanal yığınını daha fazla geçirebildiğini bir nesne almak için çağırır. Akış taşıma kanalı bir `Stream` nesne (örneğin, gelen TCP bağlantısı üzerinden bir ağ akışı) oluşturur ve `ReadMessage` bir nesneyi geri almak için ' a geçirir `Message` .  
  
 Aktarım kanalları ve ileti Kodlayıcısı arasındaki ayrım zorunlu değildir; ileti Kodlayıcısı kullanmayan bir taşıma kanalı yazmak mümkündür. Ancak, bu ayırmanın avantajı, bileşim kolaylığıdır. Bir taşıma kanalı yalnızca temeli kullandığı sürece <xref:System.ServiceModel.Channels.MessageEncoder> , herhangi BIR WCF veya üçüncü taraf ileti Kodlayıcısı ile çalışabilir. Benzer şekilde, aynı kodlayıcı normalde herhangi bir aktarım kanalında kullanılabilir.  
  
### <a name="message-encoder-operation"></a>İleti Kodlayıcısı Işlemi  
 Bir kodlayıcının tipik işlemini anlatmak için, aşağıdaki dört durumu göz önünde bulundurmanız yararlı olur.  
  
|Çalışma|Yorum|  
|---------------|-------------|  
|Kodlama, arabelleğe alınmış|Tamponlanmış modda, kodlayıcı normalde değişken boyutlu bir arabellek oluşturur ve bundan sonra bunun üzerinde bir XML yazıcı oluşturur. Daha sonra, <xref:System.ServiceModel.Channels.Message.WriteMessage%28System.Xml.XmlWriter%29> <xref:System.ServiceModel.Channels.Message.WriteBodyContents%28System.Xml.XmlDictionaryWriter%29> Bu konunun önceki bölümünde açıklandığı gibi, üst bilgileri ve ardından gövde bilgilerini yazan, kodlanan iletiyi çağırır `Message` . Arabellek içeriği (bayt dizisi olarak gösterilir), daha sonra aktarım kanalının kullanması için döndürülür.|  
|Kodlama, akış|Akış modunda, işlem yukarıya benzerdir, ancak daha basittir. Arabellek gereksinimi yoktur. Normalde akış üzerinden bir XML yazıcı oluşturulur ve <xref:System.ServiceModel.Channels.Message.WriteMessage%28System.Xml.XmlWriter%29> `Message` Bu yazıcıya yazmak için üzerinde çağrılır.|  
|Kod çözme, arabelleğe alınmış|Arabelleğe alınan modda kod çözülürken, `Message` arabelleğe alınan verileri içeren özel bir alt sınıf normalde oluşturulur. İletinin üstbilgileri okunurdur ve ileti gövdesinde konumlandırılmış bir XML okuyucusu oluşturulur. Bu, ile döndürülecek olan okuyucudur <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents> .|  
|Kod çözme, akışlı|Akan modda kod çözmede, normalde özel bir Ileti alt sınıfı oluşturulur. Akış, tüm üst bilgileri okumak ve ileti gövdesinde konumlandırmak için yeterince gelişmiş bir hale gelir. Daha sonra Stream üzerinden bir XML okuyucusu oluşturulur. Bu, ile döndürülecek olan okuyucudur <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents> .|  
  
 Kodlayıcılar, diğer işlevleri de gerçekleştirebilir. Örneğin, kodlayıcılar XML okuyucularını ve yazarları havuza alabilir. Her gerektiğinde yeni bir XML okuyucu veya yazıcı oluşturmak pahalıdır. Bu nedenle, kodlayıcılar normalde bir okuyucu havuzunu ve yapılandırılabilir boyuttaki bir yazıcı havuzunu korur. Daha önce açıklanan kodlayıcı, "bir XML okuyucu/yazıcı oluştur" ifadesi kullanıldığında, normalde "havuzdan bir tane al veya yoksa bir tane oluştur" anlamına gelir. Kodlayıcı (ve `Message` kod çözme sırasında oluşturduğu alt sınıflar), artık gerekli olmadığında (örneğin, kapatıldığında), bu havuzlara okuyucuları ve yazarları döndürme mantığını içerir `Message` .  
  
 WCF, ek özel türler oluşturmak mümkün olsa da üç ileti kodlayıcıları sağlar. Sağlanan türler metin, Ikili ve Ileti Iletimi Iyileştirme mekanizmasıdır (MTOM). Bunlar, [Ileti Kodlayıcısı seçme](choosing-a-message-encoder.md)konusunda ayrıntılı olarak açıklanmıştır.  
  
### <a name="the-istreamprovider-interface"></a>IStreamProvider arabirimi  
 Bir XML yazıcısına akışlı gövde içeren giden bir ileti yazarken, <xref:System.ServiceModel.Channels.Message> uygulamasında şuna benzer bir çağrı dizisi kullanır <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%28System.Xml.XmlDictionaryWriter%29> :  
  
- Akıştan önce gerekli tüm bilgileri yazın (örneğin, açılış XML etiketi).  
  
- Akışı yazın.  
  
- Akışı izleyen tüm bilgileri yazın (örneğin, kapanış XML etiketi).  
  
 Bu, metinsel XML kodlamasıyla benzer kodlamalar ile iyi sonuç verir. Ancak bazı kodlamalar, XML bilgi kümesi bilgilerini (örneğin, XML öğelerini başlatma ve sonlandırma etiketleri) öğeler içinde içerilen verilerle birlikte yerleştirmez. Örneğin, MTOM kodlamasıyla ileti birden çok parçaya bölünür. Bir parça, gerçek öğe içerikleri için diğer bölümlere başvurular içerebilen XML bilgi kümesini içerir. XML bilgi kümesi normal olarak akışla karşılaştırıldığında küçük, bu nedenle bilgi kümesini arabelleğe alma, yazma ve sonra içeriği akışlı bir şekilde yazma açısından anlamlı hale gelir. Bu, kapanış öğesi etiketinin yazıldığı zamana göre akışın henüz yazılmamış olması anlamına gelir.  
  
 Bu amaçla, <xref:System.Xml.IStreamProvider> arabirim kullanılır. Arabirimin <xref:System.Xml.IStreamProvider.GetStream> yazılacak akışı döndüren bir yöntemi vardır. Akış ileti gövdesini yazmanın doğru yolu <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%28System.Xml.XmlDictionaryWriter%29> aşağıdaki gibidir:  
  
1. Akıştan önce gerekli tüm bilgileri yazın (örneğin, açılış XML etiketi).  
  
2. `WriteValue`Üzerine <xref:System.Xml.XmlDictionaryWriter> <xref:System.Xml.IStreamProvider> yazılacak akışı döndüren bir uygulamayla birlikte olan aşırı yüklemeyi çağırın `IStreamProvider` .  
  
3. Akışı izleyen tüm bilgileri yazın (örneğin, kapanış XML etiketi).  
  
 Bu yaklaşımda XML yazıcı, akış verilerinin ne zaman çağrılacağını ve yazılacağı bir seçenek içerir <xref:System.Xml.IStreamProvider.GetStream> . Örneğin, metin ve ikili XML yazarları hemen çağırır ve başlangıç ve bitiş etiketleri arasında akış içeriğini içine yazar. MTOM yazıcısı, <xref:System.Xml.IStreamProvider.GetStream> iletinin ilgili bölümünü yazmaya uygun olduğunda daha sonra çağrı yapmaya karar verebilir.  
  
## <a name="representing-data-in-the-service-framework"></a>Hizmet çerçevesindeki verileri temsil etme  
 Bu konunun "temel mimari" bölümünde belirtildiği gibi, hizmet çerçevesi, diğer şeyler arasında, ileti verileri ve gerçek örnekler için Kullanıcı dostu bir programlama modeli arasında dönüştürme yapmaktan sorumludur `Message` . Normalde, bir ileti alışverişi, Service Framework 'te özniteliğiyle işaretlenmiş .NET Framework yöntemi olarak temsil edilir <xref:System.ServiceModel.OperationContractAttribute> . Yöntemi bazı parametreleri alabilir ve dönüş değeri veya out parametreleri (veya her ikisi) döndürebilir. Hizmet tarafında, giriş parametreleri gelen iletiyi temsil eder ve dönüş değeri ve çıkış parametreleri giden iletiyi temsil eder. İstemci tarafında ters, doğru olur. Parametreleri ve dönüş değerini kullanarak iletileri tanımlamaya yönelik programlama modeli, [hizmet sözleşmelerinde veri aktarımı belirtme](specifying-data-transfer-in-service-contracts.md)konusunda ayrıntılı olarak açıklanmıştır. Ancak, bu bölümde kısa bir genel bakış sağlanır.  
  
## <a name="programming-models"></a>Programlama modelleri  
 WCF hizmet çerçevesi, iletileri açıklamak için beş farklı programlama modelini destekler:  
  
### <a name="1-the-empty-message"></a>1. boş Ileti  
 Bu en basit durumdur. Boş bir gelen iletiyi anlatmak için herhangi bir giriş parametresi kullanmayın.  
  
 [!code-csharp[C_DataArchitecture#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#3)]
 [!code-vb[C_DataArchitecture#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#3)]  
  
 Boş bir giden iletiyi anlatmak için, void dönüş değeri kullanın ve herhangi bir out parametresi kullanmayın:  
  
 [!code-csharp[C_DataArchitecture#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#4)]
 [!code-vb[C_DataArchitecture#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#4)]  
  
 Bunun tek yönlü bir işlem sözleşmesinden farklı olduğunu unutmayın:  
  
 [!code-csharp[C_DataArchitecture#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#5)]
 [!code-vb[C_DataArchitecture#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#5)]  
  
 `SetDesiredTemperature`Örnekte, iki yönlü bir ileti değişimi deseninin açıklaması vardır. İşlemden bir ileti döndürülür, ancak boştur. İşlemden bir hata döndürmek mümkündür. "Ampul ayarla" örneğinde ileti değişim şekli tek yönlü olduğundan, görüntülenecek giden bir ileti yoktur. Hizmet bu durumda istemciye herhangi bir durum geri iletişim kuramıyor.  
  
### <a name="2-using-the-message-class-directly"></a>2. Ileti sınıfını doğrudan kullanma  
 <xref:System.ServiceModel.Channels.Message>Doğrudan bir işlem sözleşmesindeki sınıfı (veya alt sınıflarından birini) kullanmak mümkündür. Bu durumda, Service Framework, `Message` işlemi daha fazla işleme olmadan işlemden yalnızca kanal yığınına geçirir.  
  
 Doğrudan kullanımı için iki ana kullanım durumu vardır `Message` . Diğer programlama modellerinin hiçbiri size iletinizi anlatmak için yeterli esneklik sunmadığı durumlarda bu gelişmiş senaryolar için kullanabilirsiniz. Örneğin, dosyanın özellikleri ileti üst bilgileri ve dosyanın içeriği ileti gövdesinde olacak şekilde bir iletiyi anlatmak için diskteki dosyaları kullanmak isteyebilirsiniz. Ardından aşağıdakine benzer bir şey oluşturabilirsiniz.  
  
 [!code-csharp[C_DataArchitecture#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#6)]
 [!code-vb[C_DataArchitecture#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#6)]  
  
 `Message`Bir işlem sözleşmesindeki ikinci yaygın kullanımı, bir hizmetin belirli ileti içeriğiyle ilgilenmez ve bir siyah kutuda olduğu gibi ileti üzerinde işlem yapar. Örneğin, iletileri birden çok alıcıya ileten bir hizmetiniz olabilir. Sözleşme aşağıdaki gibi yazılabilir.  
  
 [!code-csharp[C_DataArchitecture#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#7)]
 [!code-vb[C_DataArchitecture#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#7)]  
  
 Action = "*" satırı, ileti gönderme işlemini etkin bir şekilde devre dışı bırakır ve sözleşmeye gönderilen tüm iletilerin `IForwardingService` işlem için kendi yolunu yapmasını sağlar `ForwardMessage` . (Normalde, dağıtıcı iletinin "eylem" üst bilgisini inceleyerek hangi işlemin hedeflendiğinden belirlenir. Action = " \* ", "eylem üstbilgisinin tüm olası değerleri" anlamına gelir.) # "" Eyleminin birleşimi \* ve iletinin bir parametre olarak kullanılması "evrensel sözleşme" olarak bilinir, çünkü tüm olası iletileri alabiliyor. Olası tüm iletileri gönderebilmek için, dönüş değeri olarak Ileti kullanın ve `ReplyAction` "" olarak ayarlayın \* . Bu, Service Framework 'ün kendi eylem üst bilgisini eklemesini engelleyecek ve bu üstbilgiyi, geri yüklediğiniz nesneyi kullanarak denetlemenizi sağlar `Message` .  
  
### <a name="3-message-contracts"></a>3. ileti sözleşmeleri  
 WCF, *İleti sözleşmeleri*olarak adlandırılan iletileri açıklamak için bildirim temelli bir programlama modeli sağlar. Bu model, [Ileti sözleşmelerini kullanma](using-message-contracts.md)konusunda ayrıntılı olarak açıklanmıştır. Esas olarak, tüm ileti, ileti <xref:System.ServiceModel.MessageBodyMemberAttribute> <xref:System.ServiceModel.MessageHeaderAttribute> sözleşmesi sınıfının hangi bölümlerinin ileti parçasını eşlemek için ve gibi öznitelikleri kullanan tek bir .NET Framework türü ile temsil edilir.  
  
 İleti sözleşmeleri, sonuçta elde edilen örnekler üzerinde çok fazla denetim sağlar `Message` (ancak doğrudan sınıfı kullanmakla çok fazla denetim olmasa da `Message` ). Örneğin, ileti gövdeleri genellikle kendi XML öğesiyle temsil edilen birden çok bilgi parçalarından oluşur. Bu öğeler doğrudan gövdede (*çıplak* mod) gerçekleşebilir ya da çevreleyen bir XML öğesinde *kaydırılmış* olabilir. İleti sözleşmesi programlama modelinin kullanılması, tam olarak sarmalanmış kararı yapmanızı ve sarmalayıcı adının ve ad alanının adını denetlemenizi sağlar.  
  
 Bir ileti sözleşmesinin aşağıdaki kod örneği bu özellikleri gösterir.  
  
 [!code-csharp[C_DataArchitecture#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#9)]
 [!code-vb[C_DataArchitecture#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#9)]  
  
 Serileştirilmesi için işaretlenmiş öğelerin ( <xref:System.ServiceModel.MessageBodyMemberAttribute> , <xref:System.ServiceModel.MessageHeaderAttribute> veya diğer ilgili özniteliklerle) bir ileti sözleşmesine katılması için seri hale getirilebilir olması gerekir. Daha fazla bilgi için bu konunun ilerleyen bölümlerindeki "serileştirme" bölümüne bakın.  
  
### <a name="4-parameters"></a>4. parametreler  
 Genellikle, birden çok veri parçasına davranan bir işlemi anlatmak isteyen bir geliştirici, ileti sözleşmelerinin sağladığı denetim derecesini gerektirmez. Örneğin, yeni hizmetler oluştururken, bir tane genellikle, tek başına sarmalanmış kararı yapmak ve sarmalayıcı öğe adına karar vermek istemez. Bu kararların genellikle Web Hizmetleri ve SOAP hakkında ayrıntılı bilgi sahibi olması gerekir.  
  
 WCF hizmet çerçevesi, bu seçeneklere Kullanıcı üzerinde zorlanmadan, birden fazla ilgili bilgi alma veya alma için en iyi ve en fazla birlikte çalışabilen SOAP gösterimini otomatik olarak seçebilir. Bu, yalnızca bu bilgi parçalarını parametre olarak açıklayarak veya bir işlem sözleşmesinin dönüş değeri tarafından gerçekleştirilir. Örneğin, aşağıdaki işlem sözleşmesini göz önünde bulundurun.  
  
 [!code-csharp[C_DataArchitecture#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#11)]
 [!code-vb[C_DataArchitecture#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#11)]  
  
 Service Framework, her üç bilgi parçasını ( `customerID` , `item` , ve `quantity` ) ileti gövdesine yerleştirmeye ve bunları adlı bir sarmalayıcı öğesinde sarmalamaya otomatik olarak karar verir `SubmitOrderRequest` .  
  
 Daha karmaşık ileti sözleşmesine veya tabanlı programlama modellerine geçiş yapmak için özel nedenler olmadığı sürece, işlem sözleşmesi parametrelerinin basit bir listesi olarak gönderilecek veya alınacak bilgilerin açıklaması önerilen yaklaşımdır `Message` .  
  
### <a name="5-stream"></a>5. akış  
 Bir `Stream` işlem sözleşmesindeki alt sınıflarından veya bir ileti sözleşmesinin tek bir ileti gövdesinde bir parçası olarak, yukarıda açıklananlardan farklı bir programlama modeli olarak düşünülebilir. `Stream`Bu şekilde kullanılması, sözleşmenizi, akış uyumlu alt sınıfınıza yazmanın kısa bir süre içinde kullanılabilir olacağını güvence altına almanın tek yoludur `Message` . Daha fazla bilgi için bkz. [büyük veri ve akış](large-data-and-streaming.md).  
  
 `Stream`Bu şekilde bir veya alt sınıflarından biri kullanıldığında seri hale getirici çağrılmaz. Giden iletiler için özel bir akış `Message` alt sınıfı oluşturulur ve bu akış, arabirimdeki bölümünde açıklandığı gibi yazılır <xref:System.Xml.IStreamProvider> . Gelen iletilerde, Service Framework `Stream` gelen ileti üzerinde bir alt sınıf oluşturur ve bunu işleme sağlar.  
  
## <a name="programming-model-restrictions"></a>Programlama modeli kısıtlamaları  
 Yukarıda açıklanan programlama modelleri rastgele birleştirilemez. Örneğin, bir işlem bir ileti sözleşme türünü kabul ediyorsa, ileti sözleşmesinin yalnızca giriş parametresi olması gerekir. Ayrıca, işlemin daha sonra boş bir ileti (void dönüş türü) ya da başka bir ileti sözleşmesi döndürmesi gerekir. Bu programlama modeli kısıtlamaları, her belirli programlama modeli için konularda açıklanmaktadır: ileti [sözleşmelerini](using-message-contracts.md)kullanma, [Ileti sınıfı](using-the-message-class.md)ve [büyük veri ve akış](large-data-and-streaming.md).  
  
## <a name="message-formatters"></a>İleti formatları  
 Yukarıda açıklanan programlama modelleri, hizmet çerçevesine *ileti biçimleri* olarak adlandırılan bileşenleri takarak desteklenir. İleti formatlayıcıları, <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> veya <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> arabirimini veya her ikisini de, istemcilerde ve hizmet WCF istemcilerinde kullanılmak üzere, sırasıyla uygulayan türlerdir.  
  
 İleti formatları normalde davranışlara göre prize takılır. Örneğin, <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> veri sözleşmesi ileti biçimlendirici içindeki takar. Bu, <xref:System.ServiceModel.Dispatcher.DispatchOperation.Formatter%2A> yöntemde doğru biçimlendirici olarak ayarlanarak <xref:System.ServiceModel.Description.IOperationBehavior.ApplyDispatchBehavior%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Dispatcher.DispatchOperation%29> veya <xref:System.ServiceModel.Dispatcher.ClientOperation.Formatter%2A> metotta doğru biçimlendirici olarak ayarlanarak hizmet tarafında yapılır <xref:System.ServiceModel.Description.IOperationBehavior.ApplyClientBehavior%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Dispatcher.ClientOperation%29> .  
  
 Aşağıdaki tablolarda, bir ileti biçimlendirici tarafından uygulayabileceğiniz yöntemler listelenmiştir.  
  
|Arabirim|Yöntem|Eylem|  
|---------------|------------|------------|  
|<xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter>|<xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter.DeserializeRequest%28System.ServiceModel.Channels.Message%2CSystem.Object%5B%5D%29>|Gelen `Message` işlem parametrelerine dönüştürür|  
|<xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter>|<xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter.SerializeReply%28System.ServiceModel.Channels.MessageVersion%2CSystem.Object%5B%5D%2CSystem.Object%29>|Bir giden `Message` işlem dönüş değeri/Out parametrelerini oluşturur|  
|<xref:System.ServiceModel.Dispatcher.IClientMessageFormatter>|<xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.SerializeRequest%28System.ServiceModel.Channels.MessageVersion%2CSystem.Object%5B%5D%29>|İşlem parametrelerinden giden bir giden oluşturur `Message`|  
|<xref:System.ServiceModel.Dispatcher.IClientMessageFormatter>|<xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.DeserializeReply%28System.ServiceModel.Channels.Message%2CSystem.Object%5B%5D%29>|Gelen bir `Message` dönüş değeri/Out parametrelerine dönüştürür|  
  
## <a name="serialization"></a>Serileştirme  
 İleti içeriklerini betimleyen ileti sözleşmelerini veya parametrelerini her kullandığınızda .NET Framework türleri ve XML bilgi kümesi temsili arasında dönüştürme yapmak için serileştirme kullanmanız gerekir. Serileştirme, WCF 'deki diğer yerlerde kullanılır, örneğin, <xref:System.ServiceModel.Channels.Message> <xref:System.ServiceModel.Channels.Message.GetBody%2A> seri durumdan çıkarılan iletinin tamamının gövdesini okumak Için kullanabileceğiniz genel bir yöntemi vardır.  
  
 WCF, parametreleri ve ileti parçalarını seri hale getirmek ve seri durumdan çıkarmak için "kutudan çıkar" iki serileştirme teknolojisini destekler: <xref:System.Runtime.Serialization.DataContractSerializer> ve `XmlSerializer` . Ayrıca, özel serileştiriciler yazabilirsiniz. Ancak, WCF 'nin diğer bölümleri (genel `GetBody` Yöntem veya SOAP hata serileştirme gibi) yalnızca alt sınıfları kullanacak şekilde kısıtlanabilir <xref:System.Runtime.Serialization.XmlObjectSerializer> ( <xref:System.Runtime.Serialization.DataContractSerializer> ve <xref:System.Runtime.Serialization.NetDataContractSerializer> , ancak değil <xref:System.Xml.Serialization.XmlSerializer> ) ya da yalnızca ' i kullanmak için sabit kodlanmış olabilir <xref:System.Runtime.Serialization.DataContractSerializer> .  
  
 , `XmlSerializer` ASP.NET Web hizmetlerinde kullanılan serileştirme altyapısıdır. , `DataContractSerializer` Yeni veri sözleşmesi programlama modelini anlayan yeni serileştirme altyapısıdır. `DataContractSerializer`varsayılan seçenektir ve öğesini kullanma seçeneği `XmlSerializer` özniteliği kullanılarak işlem başına temelinde yapılabilir <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.DataContractFormatAttribute%2A> .  
  
 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>ve, <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> sırasıyla ve için ileti formatlarını takmaktan sorumlu işlem davranışlardır `DataContractSerializer` `XmlSerializer` . <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>Bu davranış <xref:System.Runtime.Serialization.XmlObjectSerializer> , <xref:System.Runtime.Serialization.NetDataContractSerializer> (tek başına serileştirme kullanma konusunda ayrıntılı olarak açıklanmıştır) dahil olmak üzere, ' den türetilen tüm serileştiricilerle çalışır. Bu davranış, `CreateSerializer` serileştiriciyi almak için sanal yöntem aşırı yüklerinden birini çağırır. Farklı bir seri hale getirici eklemek için yeni bir <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> alt sınıf oluşturun ve her iki aşırı yüklemeyi geçersiz kılın `CreateSerializer` .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hizmet Anlaşmalarında Veri Aktarımını Belirtme](specifying-data-transfer-in-service-contracts.md)
