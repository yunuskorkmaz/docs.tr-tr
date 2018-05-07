---
title: Veri Aktarımı Mimarisi Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data transfer [WCF], architectural overview
ms.assetid: 343c2ca2-af53-4936-a28c-c186b3524ee9
ms.openlocfilehash: 69032a04067311f4df3696474dfc9ad4df465f51
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="data-transfer-architectural-overview"></a>Veri Aktarımı Mimarisi Genel Bakış
Windows Communication Foundation (WCF), bir Mesajlaşma altyapısı düşünülebilir. Bu iletileri almak, bunları işlemek ve bunları başka bir eylem için kullanıcı kodu gönderme veya kullanıcı kodu tarafından verilen verilerden iletileri oluşturmak ve bunları bir hedefe teslim et. Gelişmiş geliştiricileri için tasarlanmıştır, bu konu, iletileri ve içerilen verileri işleme mimarisini açıklar. Veri göndermek ve almak nasıl daha basit, görev yönelimli görünümü için bkz: [hizmet sözleşmelerinde veri aktarımı belirtme](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).  
  
> [!NOTE]
>  Bu konuda, WCF nesne modeli inceleyerek görünmez WCF uygulama ayrıntıları ele alınmıştır. İki uyarı belgelenen uygulama ayrıntılarını açısından sırayla sözcüklerdir. İlk olarak, açıklamaları basitleştirilmiştir; Gerçek uygulamayı en iyi duruma getirme veya diğer nedenlerle nedeniyle daha karmaşık olabilir. Hiçbir zaman ikinci olarak, yararlanmalıdır bu sürümünden sürümüne veya hizmet sürümdeki bile verilmeksizin çünkü belirli uygulama hakkında ayrıntılı bilgi bile olanlar da dahil belgelenmiştir.  
  
## <a name="basic-architecture"></a>Temel mimari  
 WCF ileti işleme özellikleri çekirdeği <xref:System.ServiceModel.Channels.Message> içinde ayrıntılı olarak açıklanmıştır sınıfı [ileti sınıfını kullanma](../../../../docs/framework/wcf/feature-details/using-the-message-class.md). Çalışma zamanı bileşenleri WCF iki ana iki bölüme ayrılabilir: kanal yığını ve hizmet çerçevesi ile <xref:System.ServiceModel.Channels.Message> bağlantı noktası olan sınıf.  
  
 Kanal yığını arasında geçerli bir dönüştürme için sorumlu olduğu <xref:System.ServiceModel.Channels.Message> örneği ve gönderme veya ileti verilerini alma karşılık gelen bir eylem. Gönderen tarafında kanal yığını geçerli bir alan <xref:System.ServiceModel.Channels.Message> örneği ve bazı işlendikten sonra mantıksal olarak bu iletiyi göndermek için karşılık gelen bazı eylemleri gerçekleştirir. Eylem Message Queuing, message queuing, TCP veya HTTP paketleri ileti bir dosya paylaşımı veya herhangi bir eylemde, uygulamaya bağlı olarak kaydetmeyi, bir veritabanı yazma gönderiyor olabilir. En yaygın eylem, bir ağ protokolü üzerinden iletisi gönderiyor. Alma tarafında karşıtı olur — bir eylem (olabilen gelen TCP veya HTTP paketlerin veya başka bir eylem) algılanır ve işlendikten sonra kanal yığını bu eylem geçerli bir dönüştürür <xref:System.ServiceModel.Channels.Message> örneği.  
  
 WCF kullanarak kullanabileceğiniz <xref:System.ServiceModel.Channels.Message> sınıfı ve kanalı yığın doğrudan. Ancak, bunu yapmak böylece zor ve zaman alıcı olabilir. Ayrıca, <xref:System.ServiceModel.Channels.Message> nesnesi, bu şekilde WCF kullanırsanız, kesin türü belirtilmiş WCF istemcileri üretilemiyor böylece hiçbir meta veri desteği sağlar.  
  
 Bu nedenle, WCF oluşturmak ve almak için kullanabileceğiniz bir kullanımı kolay programlama modeli sağlayan bir hizmet framework içerir `Message` nesneleri. Hizmet çerçevesi Hizmetleri eşlemeleri [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] türleri Hizmet sözleşmeleri kavramı ve yalnızca kullanıcı işlemlerini iletileri gönderir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] yöntemleri ile işaretlenen <xref:System.ServiceModel.OperationContractAttribute> özniteliği ( dahafazlaayrıntıiçinbkz[Hizmet sözleşmeleri tasarlama](../../../../docs/framework/wcf/designing-service-contracts.md)). Bu yöntemleri parametrelere sahip ve dönüş değerleri. Hizmet çerçevesi hizmet tarafında gelen dönüştürür <xref:System.ServiceModel.Channels.Message> parametreleri ve dönüştürür örneği dönüş değerleri giden içine <xref:System.ServiceModel.Channels.Message> örnekleri. İstemci tarafında karşıtı yapar. Örneğin, göz önünde bulundurun `FindAirfare` aşağıdaki işlemi.  
  
 [!code-csharp[c_DataArchitecture#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#1)]
 [!code-vb[c_DataArchitecture#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#1)]  
  
 Varsayalım `FindAirfare` istemcide olarak adlandırılır. Hizmet çerçevesi istemcide dönüştürür `FromCity` ve `ToCity` giden içine parametreleri <xref:System.ServiceModel.Channels.Message> örneği ve gönderilmesi için kanal yığın geçirir.  
  
 Hizmet tarafında olduğunda bir <xref:System.ServiceModel.Channels.Message> örneği kanal yığınından ulaştığında, hizmet çerçevesi doldurmak için iletiden ilgili verileri ayıklar `FromCity` ve `ToCity` parametreler ve Hizmet tarafı çağrıları `FindAirfare` yöntem. Yöntem döndüğünde, hizmet çerçevesi döndürülen tamsayı değerini alır ve `IsDirectFlight` çıkış parametresi ve oluşturan bir <xref:System.ServiceModel.Channels.Message> bu bilgileri içeren bir nesne örneği. Daha sonra geçirir `Message` istemciye geri gönderilecek kanal yığınına örneği.  
  
 İstemci tarafında bir <xref:System.ServiceModel.Channels.Message> yanıt iletisini içeren örneği kanal yığınından ortaya çıkar. Hizmet çerçevesi dönüş değeri ayıklar ve `IsDirectFlight` değeri ve bu istemcinin çağırana döndürür.  
  
## <a name="message-class"></a>İleti sınıfı  
 <xref:System.ServiceModel.Channels.Message> Sınıfı, bir Özet ileti gösterimi olması için tasarlanmıştır ancak tasarımını kesinlikle SOAP iletisi bağlıdır. A <xref:System.ServiceModel.Channels.Message> başlıca üç parça bilgi içerir: ileti gövdesi, ileti üstbilgilerini ve ileti özellikleri.  
  
## <a name="message-body"></a>İleti gövdesi  
 İleti gövdesi, iletinin gerçek veri yükü temsil etmek üzere tasarlanmıştır. İleti gövdesi her zaman bir XML bilgi temsil edilir. Bu, oluşturulan veya WCF'de alınan tüm iletileri XML biçiminde olmalıdır gelmez. İleti gövdesi yorumlama karar vermek için kanal yığını kadar olur. XML olarak yayma, başka bir biçime dönüştürmek veya edebilir bile tamamen atlayın. Elbette, bağlamaları WCF kaynakları çoğuyla, ileti gövdesi SOAP zarfının gövdesi bölümdeki XML içerik olarak gösterilir.  
  
 Fark önemlidir `Message` sınıfı ile XML verileri gövdesi temsil eden bir arabellek mutlaka içermiyor. Mantıksal olarak `Message` bir XML bilgi içerir, ancak bu bilgi dinamik olarak oluşturulan ve hiçbir zaman fiziksel bellekte mevcut olabilir.  
  
### <a name="putting-data-into-the-message-body"></a>İleti gövdesi veri koyma  
 İleti gövdesi verileri yerleştirmek için Tekdüzen bir mekanizma yoktur. <xref:System.ServiceModel.Channels.Message> Sınıfına sahip soyut bir yöntem <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%28System.Xml.XmlDictionaryWriter%29>, hangi alır bir <xref:System.Xml.XmlDictionaryWriter>. Öğesinin her bir alt <xref:System.ServiceModel.Channels.Message> sınıfı için bu yöntemi geçersiz kılma ve kendi içeriğini yazma sorumlu. İleti gövdesi mantıksal olarak XML bilgi içerir, `OnWriteBodyContent` üretir. Örneğin, aşağıdakileri göz önünde bulundurun `Message` bir alt kümesi.  
  
 [!code-csharp[c_DataArchitecture#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#2)]
 [!code-vb[c_DataArchitecture#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#2)]  
  
 Fiziksel bir `AirfareRequestMessage` örneği yalnızca iki dize ("fromCity" ve "toCity") içeriyor. Ancak, mantıksal olarak ileti aşağıdaki XML bilgi içerir:  
  
```xml  
<airfareRequest>  
    <from>Tokyo</from>  
    <to>London</to>  
</airfareRequest>  
```  
  
 Önceki bir işlem gibi bir ileti sözleşmesi parametrelerini oluşturmak üzere hizmet çerçevesi kullanabileceğinizden doğal olarak, size iletileri bu şekilde, oluşturursunuz normalde. Ayrıca, <xref:System.ServiceModel.Channels.Message> sınıfına sahip statik `CreateMessage` içerik ortak türlerini iletileri oluşturmak için kullanabileceğiniz yöntemleri: boş bir iletiyi, XML ile seri hale getirilmiş bir nesne içeren bir ileti <xref:System.Runtime.Serialization.DataContractSerializer>, bir SOAP içeren bir ileti hata, tarafından temsil edilen XML içeren bir ileti bir <xref:System.Xml.XmlReader>ve benzeri.  
  
### <a name="getting-data-from-a-message-body"></a>Bir ileti gövdesinden veri alma  
 İleti gövdesinde iki ana yoldan depolanan verileri ayıklamak:  
  
-   Çağırarak tüm ileti gövdesi aynı anda alabilirsiniz <xref:System.ServiceModel.Channels.Message.WriteBodyContents%28System.Xml.XmlDictionaryWriter%29> yöntemi ve bir XML yazıcı geçirme. Tam ileti gövdesi bu yazıcısı yazılır. Tüm ileti gövdesi bir kerede alma olarak da adlandırılır *ileti yazmayı*. Yazma, öncelikle kanal yığını tarafından yapılır, ileti gönderirken — kanal yığını kısmı genellikle tüm ileti gövdesi erişmek, kodlamak ve gönderin.  
  
-   İleti gövdesi dışında bilgi almak için başka bir yolu çağırmaktır <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents> ve bir XML okuyucuyu almak. İleti gövdesi sonra okuyucusunda yöntemlerini çağırarak gerektiği gibi sıralı olarak erişilebilir. İleti gövdesi parça tarafından-parçası alma olarak da adlandırılır *bir ileti okunurken*. İleti okuma öncelikle hizmet çerçevesi tarafından iletileri alınırken kullanılır. Örneğin, <xref:System.Runtime.Serialization.DataContractSerializer> olan kullanımda, hizmet çerçevesi gövdesi bir XML okuyucuyu almak ve ileti--öğe okuma ve karşılık gelen Nesne grafiği oluşturmak sonra başlayacaktır seri durumdan çıkarma altyapısı geçirin.  
  
 İleti gövdesi yalnızca bir kez alınabilir. Yalnızca iletme akışları ile çalışmak mümkün kılar. Örneğin, yazma bir <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%28System.Xml.XmlDictionaryWriter%29> okur geçersiz kılma bir <xref:System.IO.FileStream> ve sonuçları bir XML bilgi döndürür. Hiçbir zaman "dosyasının başında sarılacak" gerekir.  
  
 `WriteBodyContents` Ve `GetReaderAtBodyContents` yöntemleri işaretlemeniz yeterli ileti gövdesi hiçbir zaman önce alınır ve ardından çağıran `OnWriteBodyContents` veya `OnGetReaderAtBodyContents`sırasıyla.  
  
## <a name="message-usage-in-wcf"></a>Wcf'de ileti kullanımı  
 Çoğu iletileri ya da sınıflandırılabilir *giden* (olanlar kanal yığını tarafından gönderilmek üzere hizmet çerçevesi tarafından oluşturulan) veya *gelen* (kanaldan gelen yığın ve olan Hizmet çerçevesi tarafından yorumlanan). Ayrıca, kanal yığını arabelleğe alınan veya akış modunda çalışır. Hizmet çerçevesi aynı zamanda bir akış veya nonstreamed programlama modeli getirebilir. Bu, Basitleştirilmiş ayrıntılarını uygulamalarının yanı sıra aşağıdaki tabloda listelenen durumlarda neden olmaktadır.  
  
|İleti türü|İleti gövde verileri|Yazma (OnWriteBodyContents) uygulama|Okuma (OnGetReaderAtBodyContents) uygulama|  
|------------------|--------------------------|--------------------------------------------------|-------------------------------------------------------|  
|Giden nonstreamed programlama modelinden oluşturulan|İleti yazmak için gereken verileri (örneğin, bir nesne ve <xref:System.Runtime.Serialization.DataContractSerializer> , seri hale getirmek için gereken örnek) *|Yapılacak yazmak için Özel mantık dayalı depolanan veriler üzerinde (örneğin, arama `WriteObject` üzerinde `DataContractSerializer` , kullanımdaki seri hale getirici ise) *|Çağrı `OnWriteBodyContents`, sonuçları arabellek, arabellek bir XML okuyucu Döndür|  
|Giden akış programlama modelinden oluşturulan|`Stream` Yazılacak verilerle *|Saklı akış kullanımından verileri yazma <xref:System.Xml.IStreamProvider> mekanizması *|Çağrı `OnWriteBodyContents`, sonuçları arabellek, arabellek bir XML okuyucu Döndür|  
|Kanal yığını akış öğesinden gelen|A `Stream` ile ağ üzerinden gelen verileri temsil eden nesne bir <xref:System.Xml.XmlReader> ele|İçeriği saklı yazma `XmlReader` kullanma `WriteNode`|Saklı döndürür `XmlReader`|  
|Gelen nonstreaming kanal yığından|Gövde verilerle içeren bir arabellek bir `XmlReader` ele|İçeriği saklı Yazar `XmlReader` kullanma `WriteNode`|Saklı lang döndürür|  
  
 \* Bu öğeler doğrudan uygulanmadı `Message` alt sınıfların, ancak alt sınıflarının <xref:System.ServiceModel.Channels.BodyWriter> sınıfı. Hakkında daha fazla bilgi için <xref:System.ServiceModel.Channels.BodyWriter>, bkz: [ileti sınıfını kullanma](../../../../docs/framework/wcf/feature-details/using-the-message-class.md).  
  
## <a name="message-headers"></a>İleti üstbilgileri  
 Bir ileti üstbilgilerini içerebilir. Üstbilgi mantıksal olarak bir ad, bir ad alanı ve birkaç diğer özellikleri ile ilişkili bir XML bilgi oluşur. İleti üstbilgilerini kullanılarak erişilir `Headers` özelliği <xref:System.ServiceModel.Channels.Message>. Her üstbilgisi tarafından temsil edilen bir <xref:System.ServiceModel.Channels.MessageHeader> sınıfı. Normalde, ileti üstbilgilerini SOAP iletilerine ile çalışmak için yapılandırılmış bir kanal yığını kullanırken SOAP ileti üstbilgilerini eşlenir.  
  
 İleti üstbilgisi içine bilgi koyma ve bilgileri buradan ayıklanıyor ileti gövdesi kullanmaya benzer. Akış desteklenmediğinden işlemi biraz basitleştirilmiştir. Birden çok kez aynı başlığını içeriğine erişmek mümkündür ve her zaman arabelleğe alınıp üstbilgiler zorlama rastgele sırayla üstbilgileri erişilebilir. Üstbilgi bir XML okuyucuyu almak için kullanılabilecek hiçbir genel amaçlı mekanizması yoktur, ancak var. bir `MessageHeader` böyle bir özellik ile okunabilir bir başlığı temsil eder WCF iç alt sınıf. Bu tür `MessageHeader` özel uygulama üstbilgiler içeren bir ileti geldiğinde kanal yığını tarafından oluşturulur. Bu seri durumdan çıkarma altyapısı gibi kullanmak hizmet çerçevesi sağlar <xref:System.Runtime.Serialization.DataContractSerializer>, bu üstbilgileri yorumlayamadı.  
  
 Daha fazla bilgi için bkz: [ileti sınıfını kullanma](../../../../docs/framework/wcf/feature-details/using-the-message-class.md).  
  
## <a name="message-properties"></a>İleti özellikleri  
 Bir ileti özellikleri içerebilir. A *özelliği* herhangi [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] bir dize adı ile ilişkili nesne. Özellikler yoluyla erişilir `Properties` özelliği `Message`.  
  
 İleti gövdesi ve (Bu, normal olarak SOAP gövdesi ve SOAP üstbilgileri, sırasıyla eşleştiren) ileti üstbilgilerini aksine, ileti özelliklerini normalde gönderilen veya alınan iletiler birlikte. Kanal yığınında çeşitli kanallar arasındaki ve kanal yığını ve hizmet modeli arasında ileti hakkında veri iletmek için öncelikle bir iletişim mekanizması olarak ileti özellikleri yok.  
  
 Örneğin, WCF bir parçası olarak dahil edilen HTTP taşıma kanalı çeşitli HTTP durum kodları gibi üretebilen "404 (bulunamadı)" ve "500 (Dahili Sunucu hatası)," yanıtları istemcilere gönderdiğinde. Bir yanıt iletisi göndermeden önce onu bakar olup olmadığını `Properties` , `Message` "türünde bir nesne içeren httpResponse" adlı bir özellik içeren <xref:System.ServiceModel.Channels.HttpResponseMessageProperty>. Böyle bir özellik bulunursa, bunu ele alacağız <xref:System.ServiceModel.Channels.HttpResponseMessageProperty.StatusCode%2A> özelliği ve bu durum kodu kullanın. Bunu bulunamadı varsa, varsayılan değer "200 (Tamam)" kod kullanılır.  
  
 Daha fazla bilgi için bkz: [ileti sınıfını kullanma](../../../../docs/framework/wcf/feature-details/using-the-message-class.md).  
  
### <a name="the-message-as-a-whole"></a>İletinin bir bütün olarak  
 Şu ana kadar biz yalıtım iletisinde çeşitli kısımlarını erişmek için yöntemler ele. Ancak, <xref:System.ServiceModel.Channels.Message> sınıfı ayrıca bir bütün olarak tüm ileti çalışmak için yöntemler sağlar. Örneğin, `WriteMessage` yöntemi tüm yapılacak bir XML yazıcısına yazar.  
  
 Bu mümkün olması, tüm arasında bir eşleme tanımlanmalıdır `Message` örneği ve bir XML bilgi. Aslında, bu tür bir eşleme var: WCF SOAP standart bu eşlemeyi tanımlamak için kullanır. Zaman bir `Message` örneği yazılır bir XML bilgi elde edilen bilgi iletisi içeren geçerli bir SOAP Zarfı. Bu nedenle, `WriteMessage` normal olarak aşağıdaki adımları gerçekleştirmelisiniz:  
  
1.  Etiket açma SOAP Zarfı öğesi yazma.  
  
2.  Etiket açma SOAP üstbilgi öğesi yazma, tüm üstbilgileri yazmak ve üstbilgi öğesi kapatın.  
  
3.  Etiket açma SOAP gövdesi öğesi yazma.  
  
4.  Çağrı `WriteBodyContents` veya gövde yazmak için eşdeğer bir yöntem.  
  
5.  Gövde ve zarf öğeleri kapatın.  
  
 Yukarıdaki adımları yakından SOAP standart bağlıdır. Bu karmaşık SOAP birden fazla sürümünü, örneğin, mevcut olduğunu olgu tarafından kullanılan SOAP sürümünü bilmeden SOAP Zarfı öğe doğru yazmak mümkün değildir. Ayrıca, bazı durumlarda, bu karmaşık SOAP özgü devre dışı bırakma istenebilir tamamen eşleme.  
  
 Bu amaçlar için bir `Version` özelliği sağlanan `Message`. Yapılacak yazarken kullanmak için bir SOAP sürümüne, ayarlanabilir veya kümesine `None` tüm SOAP özgü eşlemeleri önlemek için. Varsa `Version` özelliği ayarlanmış `None`, yalnızca, kendi gövdesi Örneğin, iletisi oluşmuştur gibi tüm ileti act ile çalışma yöntemlerini `WriteMessage` yalnızca çağırırdı `WriteBodyContents` yukarıda listelenen birden çok adımı gerçekleştirmek yerine. Bu beklenen, gelen iletiler `Version` otomatik olarak algılanır ve doğru olarak ayarlanmış.  
  
## <a name="the-channel-stack"></a>Kanal yığını  
  
### <a name="channels"></a>Kanallar  
 Önce belirtildiği gibi kanal yığını giden dönüştürmek için sorumlu olduğu <xref:System.ServiceModel.Channels.Message> örnekleri (paketlerin ağ üzerinden gönderilmesi) gibi bazı eyleme veya gelen (ağ paketlerinin alma gibi) bazı eylemleri dönüştürme `Message` örnekleri.  
  
 Bir dizisinde sıralanmış bir veya daha fazla kanalları, kanal yığını oluşur. Giden `Message` örneği ilk kanal yığınında geçirilir (olarak da bilinir *en üstteki kanal*), hangi geçirir, sonraki kanala yığını ve benzeri. İleti adlandırılır son kanalda sonlandırır *taşıma kanalı*. Gelen iletileri aktarım kanalda kaynaklanan ve kanal kanal yığını geçirilir. En üstteki kanaldan ileti hizmeti Framework'e genellikle geçirilir. Bu uygulama iletileri için normal deseni olmakla birlikte, bazı kanallar biraz farklı çalışabilir, örneğin, bunlar bir ileti olmadan bir kanaldan yukarıdaki geçirilen kendi altyapı iletileri gönderebilir.  
  
 Yığınından geçerken kanalları çeşitli şekillerde ileti üzerinde çalışabilir. En yaygın işlemi üstbilgi Giden iletiye eklemek ve gelen ileti üstbilgilerinde okuma. Örneğin, bir kanal bir iletinin dijital imzasını işlem ve başlık olarak ekleyin. Bir kanal Ayrıca bu dijital imza başlığındaki gelen iletileri ve bunların şekilde kanal yığını yapmasını geçerli bir imzası yok blok iletileri inceleyin. Kanallar ayrıca sıklıkla ayarlayın veya ileti özelliklerini inceleyin. İleti gövdesi genellikle olan izin verilen olsa da, değiştirilemez, örneğin, WCF güvenlik kanalı ileti gövdesi şifreleyebilirsiniz.  
  
### <a name="transport-channels-and-message-encoders"></a>Taşıma kanalları ve ileti kodlayıcılar  
 Alttaki kanal yığınında gerçekte giden dönüştürme için sorumlu olduğu <xref:System.ServiceModel.Channels.Message>, bazı eyleme diğer kanalları tarafından değiştirilmiş olarak. Bazı eyleme dönüştürür kanal budur alma tarafında bir `Message` diğer işlem kanallar.  
  
 Daha önce belirtildiği gibi eylemleri farklılık: gönderme veya çeşitli protokoller üzerinden ağ paketleri alma, okuma veya bir veritabanında işaretlemekdeki queuing veya sağlamak için bir Message Queuing sırasının, ancak birkaç örnek iletiyi kuyruktan alma. Tüm bu eylemler tek şey ortaktır: WCF arasında dönüştürme gereksinim duydukları`Message` örneği ve gerçek bir grup, alınan, okuma, yazılan gönderilebilir bayt sıraya veya kuyruktan çıkarıldı. Dönüştürme işlemi bir `Message` bayt grubuna adlı *kodlama*ve geriye doğru oluşturma işleminin bir `Message` bayt grubundan adlı *kod çözme*.  
  
 Adlı bileşenleri çoğu taşıma kanalları kullanmak *ileti kodlayıcılar* kodlama ve kod çözme iş gerçekleştirmek için. İleti Kodlayıcı sınıfıdır <xref:System.ServiceModel.Channels.MessageEncoder> sınıfı. `MessageEncoder` çeşitli içeren `ReadMessage` ve `WriteMessage` arasında dönüştürme yapma yöntemi aşırı `Message` ve grupları bayt.  
  
 Arabelleğe alma taşıma kanalı Gönderen tarafında geçirir `Message` için yukarıda bir kanaldan alınan nesne `WriteMessage`. Ayrıca sonra (örneğin, bu bayt olarak geçerli TCP paketlerini paketleme ve doğru hedef göndererek), eylemi gerçekleştirmek için kullandığı bir bayt dizisi geri alır. İlk olarak bir akış taşıma kanalı oluşturur bir `Stream` (örneğin, giden TCP bağlantısı üzerinden) ve her ikisi de geçirir `Stream` ve `Message` uygun göndermek gereken `WriteMessage` aşırı yükleme, hangi yapılacak Yazar .  
  
 Alıcı tarafında bir dizi ve çağrıları halinde arabelleğe alma taşıma kanalı gelen bayt sayısı (örneğin, paketlerini gelen TCP) ayıklar `ReadMessage` almak için bir `Message` kanal yığını başka geçirebilirsiniz nesne. Bir akış taşıma kanalı oluşturur bir `Stream` nesne (örneğin, gelen TCP bağlantısı üzerinden ağ akışı) ve için geçen `ReadMessage` geri almak için bir `Message` nesnesi.  
  
 Taşıma kanalları ve ileti Kodlayıcı arasında ayrım zorunlu değildir; ileti Kodlayıcı kullanmaz taşıma kanalı yazmak mümkündür. Ancak, bu ayrım avantajlarından birleşim Kolaylığı ' dir. Yalnızca temel bir aktarım kanal kullandığı sürece <xref:System.ServiceModel.Channels.MessageEncoder>, herhangi bir WCF veya üçüncü taraf ileti Kodlayıcı ile çalışabilirsiniz. Benzer şekilde, aynı Kodlayıcı herhangi taşıma kanalı normal olarak kullanılabilir.  
  
### <a name="message-encoder-operation"></a>İleti Kodlayıcı işlemi  
 İşleme sırasında bir kodlayıcı açıklamak için aşağıdaki dört gerektirmelidir kullanışlıdır.  
  
|Çalışma|Yorum|  
|---------------|-------------|  
|Kodlama, arabelleğe alındı.|Arabelleğe alınan modunda Kodlayıcı normalde bir değişken boyutlu arabellek ve ardından bir XML yazıcı üzerine oluşturur. Daha sonra çağırır <xref:System.ServiceModel.Channels.Message.WriteMessage%28System.Xml.XmlWriter%29> kodlanan, iletideki üstbilgileri ve ardından gövde kullanarak Yazar <xref:System.ServiceModel.Channels.Message.WriteBodyContents%28System.Xml.XmlDictionaryWriter%29>, hakkında önceki bölümde açıklandığı gibi `Message` bu konuda. (Bir bayt dizisi gösterilir) arabellek içeriğini sonra kullanmak taşıma kanalı döndürülür.|  
|Kodlama, akışı|Akış modunda işlemi yukarıda, daha basit ancak benzer. Arabellek için gerek yoktur. Bir XML yazıcı akış üzerinden normal olarak oluşturulur ve <xref:System.ServiceModel.Channels.Message.WriteMessage%28System.Xml.XmlWriter%29> üzerinde adlı `Message` bu yazan yazma.|  
|Kod çözme, arabelleğe alındı.|Arabellekli modu, özel bir kod çözme zaman `Message` arabelleğe alınan verileri içeren bir alt normal olarak oluşturulur. İleti üstbilgilerini okuyun ve ileti gövdesinde konumlandırılmış bir XML okuyucusu oluşturulur. Bu ile döndürülen okuyucusudur <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents>.|  
|Kod çözme, akışı|Akış modunda kod çözme özel bir ileti alt normal olarak oluşturulur. Akış yetecek kadar tüm üstbilgiler okunduktan ve ileti gövdesinde konumlandırmak için gelişmiştir. Bir XML okuyucusu sonra akış üzerinden oluşturulur. Bu ile döndürülen okuyucusudur <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents>.|  
  
 Kodlayıcılar diğer işlevlerini de gerçekleştirebilirsiniz. Örneğin, kodlayıcılar XML okuyucuları ve yazıcıları havuza alabilir. Bir gerektiği her zaman yeni XML okuyucusu veya yazıcısı oluşturmak maliyetlidir. Bu nedenle, kodlayıcılar normalde bir havuzu okuyucuların ve yapılandırılabilir boyutunun yazıcılarının havuzu bakımını yapar. Daha önce açıklanan Kodlayıcı işlemi açıklamasında her "bir XML okuyucusu/yazıcı oluşturma" kullanılan, deyim Bu normalde "bir havuzdan almak veya mevcut değilse oluşturun." anlamına gelir Kodlayıcı (ve `Message` oluşturduğu çözülürken alt sınıfların) artık gerekli olmayan sonra okuyucuları ve yazıcıları havuzlarına geri dönmek için mantık içerir (örneğin, `Message` kapalı).  
  
 Ek özel türler oluşturmak mümkün olmakla WCF üç ileti kodlayıcılar sağlar. Sağlanan metin ve ikili ileti iletim en iyi duruma getirme mekanizmasını (MTOM) türleridir. Bunlar içinde ayrıntılı olarak açıklanmıştır [ileti Kodlayıcı seçme](../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md).  
  
### <a name="the-istreamprovider-interface"></a>IStreamProvider arabirimi  
 Bir XML yazıcı akışlı bir gövde içeren giden iletisi yazılırken <xref:System.ServiceModel.Channels.Message> çağrıları aşağıdakine benzer bir dizi kullanan kendi <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%28System.Xml.XmlDictionaryWriter%29> uygulama:  
  
-   Akış (örneğin, XML etiketi açılış) önceki tüm gerekli bilgileri yazın.  
  
-   Akış yazma.  
  
-   Akış (örneğin, XML etiketi kapanış) aşağıdaki herhangi bir bilgi yazın.  
  
 Bu da XML metin kodlaması benzer Kodlamalar ile çalışır. Ancak, bazı Kodlamalar XML bilgi bilgi (başlangıç ve bitiş XML öğeleri için örneğin, etiketleri için) içinde öğelerin bulunan verileri birlikte yerleştirmeyin. Örneğin, kodlama MTOM ileti birden çok bölüme ayrılır. Bir bölümü diğer bölümleri gerçek öğesi içeriği için başvurular içerebilir XML bilgi içerir. XML bilgi bilgi arabellek, onu yazma ve ardından içeriği akışlı bir biçimde yazmak için bir anlam şekilde akış içeriği, karşılaştırıldığında genellikle küçüktür. Bu zaman kapatma anlamına öğe etiketi yazıldığı akış henüz yazılmadı.  
  
 Bu amaçla <xref:System.Xml.IStreamProvider> arabirimi kullanılır. Arabirime sahip bir <xref:System.Xml.IStreamProvider.GetStream> yazılacak akış döndürür yöntemi. Akış ileti gövdesinde çıkışı yazmak için doğru bir şekilde <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%28System.Xml.XmlDictionaryWriter%29> aşağıdaki gibidir:  
  
1.  Akış (örneğin, XML etiketi açılış) önceki tüm gerekli bilgileri yazın.  
  
2.  Çağrı `WriteValue` üzerinde aşırı <xref:System.Xml.XmlDictionaryWriter> alan bir <xref:System.Xml.IStreamProvider>, ile bir `IStreamProvider` yazılacak akış döndürür uygulama.  
  
3.  Akış (örneğin, XML etiketi kapanış) aşağıdaki herhangi bir bilgi yazın.  
  
 Bu yaklaşımda, XML yazıcıyı çağrısı yapıldığında seçimine sahip <xref:System.Xml.IStreamProvider.GetStream> ve akış verileri yazma. Örneğin, metin ve ikili XML yazıcılarının hemen çağırın ve başlangıç ve bitiş etiketleri ortası akış içeriğini yazma. MTOM yazıcısı çağırmak karar verebilir <xref:System.Xml.IStreamProvider.GetStream> daha sonra iletinin uygun parçası yazmak hazır olduğunda.  
  
## <a name="representing-data-in-the-service-framework"></a>Hizmet çerçevesi verileri temsil eden  
 Bu konunun "Temel mimari" bölümünde belirtildiği gibi hizmet çerçevesi olan, başka şeylerin ileti veriler için kullanıcı dostu bir programlama modeli arasında dönüştürme sorumlu ve gerçek WCF parçası olan `Message` örnekleri. Normalde, bir ileti alışverişi hizmet Framework'teki temsil edilen bir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] yöntemi ile işaretlenen <xref:System.ServiceModel.OperationContractAttribute> özniteliği. Yöntem bazı parametreler alabilir ve dönüş değeri döndürebilir ya da parametreleri (veya her ikisi de). Hizmet tarafında giriş parametreleri gelen ileti ve dönüş değerini temsil eder ve out Parametreleri giden iletiyi temsil eder. İstemci tarafında ters geçerlidir. Parametreler ve dönüş değerini kullanarak iletileri açıklamak için programlama modelini içinde ayrıntılı olarak açıklanmıştır [hizmet sözleşmelerinde veri aktarımı belirtme](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md). Ancak, bu bölümde kısa bir genel bakış sağlar.  
  
## <a name="programming-models"></a>Programlama modelleri  
 WCF hizmet çerçevesi iletileri açıklamak için beş farklı programlama modelleri destekler:  
  
### <a name="1-the-empty-message"></a>1. Boş ileti  
 Bu basit bir durumdur. Boş bir gelen iletiyi tanımlamak için giriş parametreleri kullanmayın.  
  
 [!code-csharp[C_DataArchitecture#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#3)]
 [!code-vb[C_DataArchitecture#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#3)]  
  
 Boş bir giden iletiyi tanımlamak için void dönüş değeri kullanın ve out Parametreleri kullanmayın:  
  
 [!code-csharp[C_DataArchitecture#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#4)]
 [!code-vb[C_DataArchitecture#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#4)]  
  
 Bu bir tek yönlü işlem sözleşmeden farklı olduğuna dikkat edin:  
  
 [!code-csharp[C_DataArchitecture#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#5)]
 [!code-vb[C_DataArchitecture#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#5)]  
  
 İçinde `SetDesiredTemperature` örnek, bir çift yönlü ileti değişim deseni açıklanmıştır. İşlemi bir ileti döndürdü ancak boş. Bir arıza işlemi geri dönmek mümkündür. Bu yüzden açıklamak için giden ileti yok "Ampul Ayarla" örnekte ileti değişim deseni, tek yönlüdür. Hizmeti herhangi bir durumla istemciye bu durumda iletişim kuramıyor.  
  
### <a name="2-using-the-message-class-directly"></a>2. İleti sınıfını doğrudan kullanma  
 Kullanmak da mümkündür <xref:System.ServiceModel.Channels.Message> sınıfı (veya alt sınıfları) doğrudan birinde bir işlemi sözleşme. Bu durumda, hizmet çerçevesi yalnızca geçirir `Message` kanal yığını ve tersi yönde başka bir işleme ile işlem.  
  
 Kullanmak için iki ana kullanım örnekleri vardır `Message` doğrudan. Bir programlama modelleri hiçbiri iletinizi açıklamak için yeterli esnekliği sağlar, bu Gelişmiş senaryoları için kullanabilirsiniz. Örneğin, dosyaları diskte ileti üstbilgilerini ve dosyanın içeriğini ileti gövdesi olmadan olmadan dosyanın özelliklere sahip bir ileti tanımlamak için kullanmak isteyebilirsiniz. Daha sonra aşağıdaki benzeri oluşturabilirsiniz.  
  
 [!code-csharp[C_DataArchitecture#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#6)]
 [!code-vb[C_DataArchitecture#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#6)]  
  
 İkinci genel kullanım için `Message` bir işlemi sözleşmede içeriği ne zaman bir hizmet hakkında belirli ileti ilgilenmez ve ileti üzerinde siyah bir kutu gibi üzerinde çalışır. Örneğin, diğer birden çok alıcıya iletilerini ileten bir hizmet olabilir. Sözleşme şu şekilde yazılabilir.  
  
 [!code-csharp[C_DataArchitecture#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#7)]
 [!code-vb[C_DataArchitecture#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#7)]  
  
 Eylem = "*" satırı etkili bir şekilde ileti gönderilirken devre dışı bırakır ve tüm iletileri için gönderilen sağlar `IForwardingService` Sözleşme Oluştur kendi şekilde `ForwardMessage` işlemi. (Normalde, dağıtıcı için hazırlanmıştır hangi işlemi belirlemek için ileti "Eylem" başlığı inceleyin. Eylem = "\*" "eylem üstbilgisinin tüm olası değerler" anlamına gelir.) Eylem birleşimi = "\*" ve tüm olası iletileri almak mümkün olduğu için bir parametre "Evrensel sözleşme" bilinen bir iletiyi kullanarak. Tüm olası iletileri gönderebilmesi için ileti dönüş değeri olarak kullanın ve ayarlayın `ReplyAction` için "\*". Kullanarak bu başlığı denetlemenizi etkinleştirme kendi eylem üstbilgisi ekleyerek bu hizmet çerçevesi engelleyecek `Message` dönmek nesne.  
  
### <a name="3-message-contracts"></a>3. İleti Sözleşmeleri  
 WCF adlı iletileri açıklamak için bildirim temelli bir programlama modeli sağlar *ileti sözleşmeleri*. Bu model içinde ayrıntılı olarak açıklanmıştır [kullanarak ileti sözleşmeleri](../../../../docs/framework/wcf/feature-details/using-message-contracts.md). Esas olarak, tüm ileti tek bir tarafından temsil edilen [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] gibi özniteliklere kullanan türü <xref:System.ServiceModel.MessageBodyMemberAttribute> ve <xref:System.ServiceModel.MessageHeaderAttribute> ileti sözleşme sınıfı hangi kısımlarının ileti hangi kısmına eşlemelisiniz açıklamak için.  
  
 İleti sözleşmeleri sağlayan çok sayıda sonuç üzerinde denetim `Message` örnekleri (kullanarak olarak açıkça değil kadar denetim rağmen `Message` doğrudan sınıfı). Örneğin, İleti gövdeleri genellikle birden çok bilgi parçalarını oluşur, her biri kendi XML öğesi tarafından temsil edilen. Bu öğeleri ya da doğrudan gövdesinde oluşabilir (*tam* mod) veya olabilir *Sarmalanan* kapsamlı bir XML öğesi içinde. Programlama modeli ileti sözleşmesi kullanarak Sarmalanan karşılaştırması tam kararı ve kapsayıcı adı ve ad alanı adını denetlemenizi sağlar.  
  
 İleti sözleşmesi aşağıdaki kod örneği, bu özellikleri gösterir.  
  
 [!code-csharp[C_DataArchitecture#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#9)]
 [!code-vb[C_DataArchitecture#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#9)]  
  
 İşaretli öğeleri serileştirilmesi için (ile <xref:System.ServiceModel.MessageBodyMemberAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute>, veya ilgili diğer öznitelikleri) bir ileti sözleşmesi katılmayı Serileştirilebilir olmalıdır. Daha fazla bilgi için bu konunun devamındaki "Serileştirme" bölümüne bakın.  
  
### <a name="4-parameters"></a>4. Parametreler  
 Genellikle, verileri birden çok parçalarını görevi gören bir işlemi tanımlamak için isteyen bir geliştirici denetime sahip ileti sözleşmeleri sağlayan gerekli değildir. Örneğin, yeni hizmetler oluştururken, bir genellikle Sarmalanan karşılaştırması tam kararı ve sarmalayıcı öğesi adına karar vermek istemez. Bu kararları genellikle Web Hizmetleri ve SOAP derinlemesine bilgi gerektirir.  
  
 WCF hizmet çerçevesi otomatik olarak gönderme veya kullanıcının bu seçenekler zorlamadan bilgi, birden fazla ilgili parçalarını alma için en iyi ve en çalışabilir SOAP gösterimi seçebilirsiniz. Bu parametre olarak bu bilgilerin açıklayarak gerçekleştirilir veya bir işlem sözleşmesi değerini döndürür. Örneğin, aşağıdaki işlemi sözleşme göz önünde bulundurun.  
  
 [!code-csharp[C_DataArchitecture#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#11)]
 [!code-vb[C_DataArchitecture#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#11)]  
  
 Hizmet çerçevesi otomatik olarak tüm üç parça bilgi koyacağına karar vermesine (`customerID`, `item`, ve `quantity`) kaydırma ve ileti gövdesi içinde bir kapsayıcı öğe bunlardaki adlı `SubmitOrderRequest`.  
  
 Gönderilen veya önerilen yaklaşım basit işlemi sözleşme parametrelerin listesini olduğu gibi daha karmaşık ileti sözleşmesi taşımak için özel nedenleri mevcut sürece alınan bilgilere açıklayan veya `Message`-programlama modelleri tabanlı.  
  
### <a name="5-stream"></a>5. Akış  
 Kullanarak `Stream` veya bir işlem sözleşmesi veya bir ileti sözleşmesi bulunan bir tek ileti gövdesi parçası olarak kendi alt sınıflarından birini sayılabileceğini yukarıda açıklanan gördüğünüzden ayrı bir programlama modeli. Kullanarak `Stream` bu şekilde, sözleşme kendi akış uyumlu yazma eksikliği akışlı bir şekilde kullanılabilir olacağını garanti etmek için tek yoludur `Message` bir alt kümesi. Daha fazla bilgi için bkz: [büyük veriler ve akış](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).  
  
 Zaman `Stream` veya onun alt sınıflarından birini bu şekilde kullanıldığında, seri hale getirici çağrılamaz. Özel akış giden iletiler için `Message` bir alt kümesi oluşturulur ve akış bölümünde açıklandığı gibi out yazılır <xref:System.Xml.IStreamProvider> arabirimi. Hizmet çerçevesi gelen iletiler için oluşturur bir `Stream` üzerinden gelen ileti bir alt işlemi sunar.  
  
## <a name="programming-model-restrictions"></a>Programlama modeli kısıtlamaları  
 Yukarıda açıklanan programlama modelleri rasgele birleştirilemez. Örneğin, bir işlem sözleşme türden bir ileti kabul ederse, ileti sözleşmesi, yalnızca giriş parametresi olmalıdır. Ayrıca, dönüş boş bir ileti (dönüş türü void) veya başka bir ileti sonra Sözleşme işlemi gerekir. Programlama modeli kısıtlamalarının her belirli bir programlama modeli konular açıklanmaktadır: [kullanarak ileti sözleşmeleri](../../../../docs/framework/wcf/feature-details/using-message-contracts.md), [ileti sınıfını kullanma](../../../../docs/framework/wcf/feature-details/using-the-message-class.md), ve [büyük veriler ve akış ](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).  
  
## <a name="message-formatters"></a>İleti Biçimlendiricileri  
 Yukarıda açıklanan programlama modelleri adlı bileşenlerinde takarak desteklenen *ileti biçimlendiricileri* hizmet çerçevesi içine. İleti biçimlendiricileri uygulayan türleridir <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> veya <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> arabirimi veya her ikisi için kullanımda ve hizmet WCF istemcilerinin, sırasıyla.  
  
 İleti biçimlendiricileri normalde davranışları tarafından takılır. Örneğin, <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> veri sözleşmesi ileti biçimlendiricisi takılan. Bu hizmet tarafında ayarlayarak yapılır <xref:System.ServiceModel.Dispatcher.DispatchOperation.Formatter%2A> doğru biçimlendirici için <xref:System.ServiceModel.Description.IOperationBehavior.ApplyDispatchBehavior%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Dispatcher.DispatchOperation%29> yöntemini veya ayarlayarak istemci tarafında <xref:System.ServiceModel.Dispatcher.ClientOperation.Formatter%2A> doğru biçimlendirici için <xref:System.ServiceModel.Description.IOperationBehavior.ApplyClientBehavior%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Dispatcher.ClientOperation%29> yöntemi.  
  
 Aşağıdaki tablolarda ileti biçimlendiricisi uygulayabilir yöntemlerini listeler.  
  
|Arabirim|Yöntem|Eylem|  
|---------------|------------|------------|  
|<xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter>|<xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter.DeserializeRequest%28System.ServiceModel.Channels.Message%2CSystem.Object%5B%5D%29>|Bir gelen dönüştürür `Message` işlemi parametreleri|  
|<xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter>|<xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter.SerializeReply%28System.ServiceModel.Channels.MessageVersion%2CSystem.Object%5B%5D%2CSystem.Object%29>|Giden oluşturur `Message` işleminden dönüş değeri/out Parametreleri|  
|<xref:System.ServiceModel.Dispatcher.IClientMessageFormatter>|<xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.SerializeRequest%28System.ServiceModel.Channels.MessageVersion%2CSystem.Object%5B%5D%29>|Giden oluşturur `Message` işlemi parametrelerinden|  
|<xref:System.ServiceModel.Dispatcher.IClientMessageFormatter>|<xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.DeserializeReply%28System.ServiceModel.Channels.Message%2CSystem.Object%5B%5D%29>|Bir gelen dönüştürür `Message` dönüş değeri/out Parametreleri|  
  
## <a name="serialization"></a>Serileştirme  
 İleti içeriği açıklamak için ileti sözleşmeleri veya parametrelerini kullandığınızda arasında dönüştürme için seri hale getirme kullanmalısınız [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] türleri ve XML bilgi gösterimi. Seri hale getirme kullanılır farklı konumlarda WCF, örneğin, <xref:System.ServiceModel.Channels.Message> genel sahip <xref:System.ServiceModel.Channels.Message.GetBody%2A> bir nesneye tüm seri durumdan ileti gövdesini okumak için kullanabileceğiniz yöntemi.  
  
 WCF seri hale getirme ve seri durumdan parametreleri ve ileti bölümleri için "dışında kutu" iki serileştirme teknolojilerini destekler: <xref:System.Runtime.Serialization.DataContractSerializer> ve `XmlSerializer`. Ayrıca, özel serileştiricileri yazabilirsiniz. Ancak, diğer bölümleri WCF (genel gibi `GetBody` yöntemi veya SOAP arıza seri hale getirme) yalnızca kullanmak üzere kısıtlanabilir <xref:System.Runtime.Serialization.XmlObjectSerializer> alt sınıfların (<xref:System.Runtime.Serialization.DataContractSerializer> ve <xref:System.Runtime.Serialization.NetDataContractSerializer>, ama <xref:System.Xml.Serialization.XmlSerializer>), veya yalnızca kullanmak üzere kodlanmış bile olabilir <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
 `XmlSerializer` Serileştirme motoruna kullanılan [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web Hizmetleri. `DataContractSerializer` Yeni veri sözleşmesi programlama modeli anlar yeni serileştirme altyapısıdır. `DataContractSerializer` Varsayılan seçenek ve kullanma seçimi `XmlSerializer` kullanarak bir işlem başına temel yapılan <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.DataContractFormatAttribute%2A> özniteliği.  
  
 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> ve <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> işlemi davranışları ileti biçimlendiricilerini takma için sorumlu olan `DataContractSerializer` ve `XmlSerializer`sırasıyla. <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> Davranışı türetilen seri hale getirici ile gerçekte çalışabilir <xref:System.Runtime.Serialization.XmlObjectSerializer>dahil <xref:System.Runtime.Serialization.NetDataContractSerializer> (kullanarak tek başına serileştirmede ayrıntılı açıklanmıştır). Davranışı birine çağrılarını `CreateSerializer` sanal yöntemi aşırı seri hale getirici elde edilir. İçinde farklı bir seri hale getirici takmak için yeni bir oluşturma <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> alt sınıf ve geçersiz kılma `CreateSerializer` aşırı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hizmet Anlaşmalarında Veri Aktarımını Belirtme](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)
