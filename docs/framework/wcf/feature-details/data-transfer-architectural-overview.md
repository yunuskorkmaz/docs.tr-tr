---
title: Veri Aktarımı Mimarisi Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data transfer [WCF], architectural overview
ms.assetid: 343c2ca2-af53-4936-a28c-c186b3524ee9
ms.openlocfilehash: 401803229c54a2b38af08c0418b9efd4c64d9d60
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64627039"
---
# <a name="data-transfer-architectural-overview"></a>Veri Aktarımı Mimarisi Genel Bakış
Windows Communication Foundation (WCF), bir Mesajlaşma altyapısı düşünülebilir. Bu iletileri almak, bunları işlemek ve bunları başka bir eylem için kullanıcı kodu için gönderme veya kullanıcı kodu tarafından verilen veri iletileri oluşturmak ve bunları bir hedefe sunun. İleri düzey geliştiriciler için tasarlanmıştır, bu konu, iletileri ve içerdiği veri işleme mimarisini açıklar. Veri göndermek ve almak nasıl daha basit, görev odaklı görünümü için bkz: [hizmet sözleşmelerinde veri aktarımı belirtme](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).  
  
> [!NOTE]
>  Bu konu, WCF nesne modeli inceleyerek görünür olmayan WCF uygulama ayrıntılarını açıklar. İki uyarı belgelenmiş uygulama ayrıntılarını onaylamaz sırayla sözcüklerdir. İlk olarak, açıklamaları basitleştirilmiştir; kullanımınız, en iyi duruma getirme veya diğer nedenlerle nedeniyle daha karmaşık olabilir. Hiçbir zaman ikinci yararlanmalıdır bu sürümünden sürümüne veya hatta bir bakım sürüm değiştirilebilir çünkü belirli uygulama hakkında ayrıntılı bilgi bile dahil olmak üzere, belgelenmiştir.  
  
## <a name="basic-architecture"></a>Temel mimari  
 WCF ileti işleme özelliklerinin temel <xref:System.ServiceModel.Channels.Message> ayrıntılı olarak açıklanan sınıfı [ileti sınıfını kullanma](../../../../docs/framework/wcf/feature-details/using-the-message-class.md). Çalışma zamanı bileşenlerini WCF iki ana iki bölüme ayrılabilir: kanal yığını ve hizmet çerçevesi ile <xref:System.ServiceModel.Channels.Message> bağlantı noktası olan sınıf.  
  
 Kanal stack arasında geçerli bir oluşturmaktan sorumludur <xref:System.ServiceModel.Channels.Message> örneği ve gönderme veya alma ileti veri karşılık gelen bir eylem. Kanal yığın gönderme tarafında geçerli bir alan <xref:System.ServiceModel.Channels.Message> örneği ve bazı işlendikten sonra mantıksal olarak ileti göndermek için karşılık gelen bir eylem gerçekleştirir. Eylem Message Queuing, message queuing TCP veya HTTP paketleri ileti bir dosya paylaşımı ya da uygulama bağlı olarak diğer tüm eylemlerini kaydederek, bir veritabanı yazma gönderiyor olabilir. En yaygın eylem ağ protokolü üzerinden ileti gönderir. Tersine alma tarafında olur — bir eylem (aynı gelen TCP veya HTTP paketler ya da herhangi bir işlem olabilir) tespit edilir ve işlendikten sonra kanal yığın bu eylem geçerli bir dönüştürür <xref:System.ServiceModel.Channels.Message> örneği.  
  
 WCF kullanarak kullanabileceğiniz <xref:System.ServiceModel.Channels.Message> sınıfı ve kanal yığın doğrudan. Ancak bunun yapılması kadar zor ve zaman alıcı olabilir. Ayrıca, <xref:System.ServiceModel.Channels.Message> nesnesi, kesin türü belirtilmiş WCF istemcileri bu şekilde WCF kullanırsanız üretilemiyor bu nedenle hiçbir meta veri desteği sağlar.  
  
 Bu nedenle, WCF oluşturmak ve almak için kullanabileceğiniz bir kolayca kullanıma programlama modeli sağlayan bir hizmet çerçevesi içeren `Message` nesneleri. Hizmet çerçevesi Hizmetleri eşler [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] türleri kavramı Hizmet sözleşmeleri ve yalnızca kullanıcı işlemleri iletileri gönderir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] ile işaretlenmiş yöntemler <xref:System.ServiceModel.OperationContractAttribute> özniteliği ( dahafazlaayrıntıiçinbkz[Hizmet sözleşmeleri tasarlama](../../../../docs/framework/wcf/designing-service-contracts.md)). Bu yöntemlerin parametreleri ve dönüş değerleri. Hizmet çerçevesi hizmet tarafında, gelen dönüştürür <xref:System.ServiceModel.Channels.Message> örnek parametreler ve dönüştürür dönüş değerleri içine giden <xref:System.ServiceModel.Channels.Message> örnekleri. İstemci tarafında tersi yok. Örneğin, düşünün `FindAirfare` aşağıdaki işlemi.  
  
 [!code-csharp[c_DataArchitecture#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#1)]
 [!code-vb[c_DataArchitecture#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#1)]  
  
 Varsayalım `FindAirfare` istemci üzerinde çağrılır. Hizmet çerçevesi istemcide dönüştürür `FromCity` ve `ToCity` içine giden parametreleri <xref:System.ServiceModel.Channels.Message> örnek ve gönderilecek kanal yığın geçirir.  
  
 Hizmet tarafında, bir <xref:System.ServiceModel.Channels.Message> örneği kanal yığından ulaştığında, hizmet çerçevesi doldurmak için iletiden ilgili verileri ayıklar `FromCity` ve `ToCity` parametreleri ve Hizmet tarafı çağrıları `FindAirfare` yöntem. Yöntem döndürüldüğünde, hizmet çerçevesi döndürülen tamsayı değerini alır ve `IsDirectFlight` oluşturur ve çıkış parametresi bir <xref:System.ServiceModel.Channels.Message> bu bilgileri içeren bir nesne örneği. Daha sonra geçirir `Message` istemciye geri gönderilecek kanal yığınına örneği.  
  
 İstemci tarafında bir <xref:System.ServiceModel.Channels.Message> yanıt iletisini içeren örneğini kanal yığından ortaya çıkar. Hizmet çerçevesi dönüş değeri ayıklar ve `IsDirectFlight` değeri ve bu istemcinin çağırana döner.  
  
## <a name="message-class"></a>message sınıfı  
 <xref:System.ServiceModel.Channels.Message> Sınıfı, bir ileti soyut bir temsilini olacak şekilde tasarlanmıştır ancak tasarımı için SOAP iletisi kesin bağlıdır. A <xref:System.ServiceModel.Channels.Message> bilgi başlıca üç parça içerir: bir ileti gövdesi, ileti üstbilgileri ve ileti özellikleri.  
  
## <a name="message-body"></a>İleti gövdesi  
 İleti gövdesi, iletinin gerçek veri yükü temsil etmek üzere tasarlanmıştır. İleti gövdesi, her zaman bir XML bilgi kümesi temsil edilir. Bu, oluşturulan veya WCF'de alınan tüm iletileri XML biçiminde olması gerektiğini gelmez. Bu, ileti gövdesi yorumlama karar vermek için en fazla kanal yığın olur. Bunu XML olarak yayma, başka bir biçime dönüştürmeniz veya hatta tamamen atlayın. Elbette, ile bağlamaları WCF kaynakları çoğu, ileti gövdesi XML içeriği bir SOAP zarfının gövdesi bölümünde gösterilir.  
  
 Fark önemlidir `Message` sınıfı ile XML verileri gövdesini temsil eden bir arabellek mutlaka içermiyor. Mantıksal olarak `Message` bir XML bilgi kümesi içerir ancak bu bilgi, dinamik olarak oluşturulabilir ve bellekte hiçbir zaman fiziksel olarak mevcut olabilir.  
  
### <a name="putting-data-into-the-message-body"></a>İleti gövdesine verileri koyma  
 Bir ileti gövdesine verileri yerleştirmek için Tekdüzen bir mekanizma yoktur. <xref:System.ServiceModel.Channels.Message> Sınıfında bir soyut yönteminden <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%28System.Xml.XmlDictionaryWriter%29>, hangi alır bir <xref:System.Xml.XmlDictionaryWriter>. Her öğesinin <xref:System.ServiceModel.Channels.Message> sınıfı, bu yöntemi geçersiz kılma ve kendi içeriği yazmak için sorumludur. İleti gövdesi, mantıksal olarak XML bilgi kümesi içeren, `OnWriteBodyContent` üretir. Örneğin, aşağıdakileri dikkate alın `Message` öğesinin alt sınıfı.  
  
 [!code-csharp[c_DataArchitecture#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#2)]
 [!code-vb[c_DataArchitecture#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#2)]  
  
 Fiziksel bir `AirfareRequestMessage` örneği yalnızca iki dize ("fromCity" ve "toCity") içeriyor. Ancak, mantıksal olarak ileti aşağıdaki XML bilgi kümesi içerir:  
  
```xml  
<airfareRequest>  
    <from>Tokyo</from>  
    <to>London</to>  
</airfareRequest>  
```  
  
 Önceki bir işlemden gibi bir ileti anlaşması parametreleri oluşturmak için hizmet çerçevesi kullanabileceğinizden Elbette, iletileri bu şekilde oluşturacak normalde. Ayrıca, <xref:System.ServiceModel.Channels.Message> sınıfında statik `CreateMessage` iletileri içeriği genel türleri oluşturmak için kullanabileceğiniz yöntemler: boş bir ileti, XML ile seri hale getirilmiş bir nesneyi içeren bir ileti <xref:System.Runtime.Serialization.DataContractSerializer>, bir SOAP içeren bir ileti hata, XML tarafından temsil edilen içeren bir ileti bir <xref:System.Xml.XmlReader>ve benzeri.  
  
### <a name="getting-data-from-a-message-body"></a>Bir iletinin gövdesinden veri alma  
 İleti gövdesinde iki ana şekilde depolanan verileri de ayıklayabilirsiniz:  
  
- Çağırarak tüm ileti gövdesi tek seferde alabilirsiniz <xref:System.ServiceModel.Channels.Message.WriteBodyContents%28System.Xml.XmlDictionaryWriter%29> yöntemi ve bir XML yazıcısı geçirirsiniz. Eksiksiz bir ileti gövdesi için bu yazıcısı yazılır. Tek seferde tüm ileti gövdesi alma olarak da adlandırılır *bir iletiyi yazmanın*. Yazma, öncelikle kanal yığını tarafından yapılır, iletileri gönderirken — kanal yığınının bir parçası genellikle tüm ileti gövdesi erişin, kodlamak ve gönderin.  
  
- İleti gövdesinin dışında bilgi almak için başka bir yolu <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents> ve bir XML okuyucuyu almak. İleti gövdesi ardından okuyucuyu yöntemleri çağırarak gerektiği gibi sıralı olarak erişilebilir. İleti gövdesi parça--parça alma olarak da adlandırılır *bir ileti okuma*. İleti okuma öncelikle hizmet çerçevesi tarafından iletileri alınırken kullanılır. Örneğin, <xref:System.Runtime.Serialization.DataContractSerializer> olan kullanımda hizmet çerçevesi gövdesi bir XML okuyucuyu almak ve ardından ileti--öğe okuma ve karşılık gelen Nesne grafiği oluşturmak başlayacaktır seri durumundan çıkarma altyapısı geçirin.  
  
 İleti gövdesi yalnızca bir kez alınabilir. Bu, yalnızca iletme akışlarla çalışma mümkün kılar. Örneğin, yazabileceğiniz bir <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%28System.Xml.XmlDictionaryWriter%29> okur geçersiz kılma bir <xref:System.IO.FileStream> ve sonuçları bir XML bilgi kümesi döndürür. Hiçbir zaman "dosyanın başına geri sarmak" gerekir.  
  
 `WriteBodyContents` Ve `GetReaderAtBodyContents` yöntemleri işaretleyerek ileti gövdesi hiçbir zaman önce alınır ve sonra çağrı `OnWriteBodyContents` veya `OnGetReaderAtBodyContents`sırasıyla.  
  
## <a name="message-usage-in-wcf"></a>Wcf'de ileti kullanım  
 Çoğu ileti ya da sınıflandırılabilir *giden* (Bu kanal yığını tarafından gönderilmek üzere hizmet çerçevesi tarafından oluşturulan) veya *gelen* (kanaldan gelen yığın ve olan Hizmet çerçevesi tarafından yorumlanır). Ayrıca, kanal yığın arabelleğe alınan ya da akış modunda çalışır. Hizmet çerçevesi, bir akış veya nonstreamed programlama modeli de getirebilir. Bu Basitleştirilmiş, geliştirdikleri birlikte aşağıdaki tabloda listelenen çalışmaları neden olur.  
  
|İleti türü|İleti gövdesi verileri|Yazma (OnWriteBodyContents) uygulama|Okuma (OnGetReaderAtBodyContents) uygulama|  
|------------------|--------------------------|--------------------------------------------------|-------------------------------------------------------|  
|Giden nonstreamed programlama modelinden oluşturuldu|İleti yazmak için gerekli verileri (örneğin, bir nesne ve <xref:System.Runtime.Serialization.DataContractSerializer> , seri hale getirmek için gereken örnek) *|İletisi yazmak için özel mantığı depolanan verileri temel alarak (örneğin, çağrı `WriteObject` üzerinde `DataContractSerializer` , kullanımda seri hale getirici ise) *|Çağrı `OnWriteBodyContents`, sonuçları arabellek, XML okuyucusu arabellek döndürür|  
|Giden akış programlama modelinden oluşturuldu|`Stream` Yazılacak verilerle *|Saklı stream kullanarak verileri yazma <xref:System.Xml.IStreamProvider> mekanizması *|Çağrı `OnWriteBodyContents`, sonuçları arabellek, XML okuyucusu arabellek döndürür|  
|Kanal yığın akışı'ndan gelen|A `Stream` ile ağ üzerinden gelen verileri temsil eden bir nesne bir <xref:System.Xml.XmlReader> ele|İçeriği saklı yazma `XmlReader` kullanma `WriteNode`|Depolanan döndürür `XmlReader`|  
|Gelen nonstreaming kanal yığından|İle gövde verilerini içeren bir arabelleği bir `XmlReader` ele|İçeriği saklı Yazar `XmlReader` kullanma `WriteNode`|Saklı lang döndürür|  
  
 \* Bu öğeleri doğrudan uygulanmadı `Message` alt sınıflar, ancak alt sınıflarından birini <xref:System.ServiceModel.Channels.BodyWriter> sınıfı. Hakkında daha fazla bilgi için <xref:System.ServiceModel.Channels.BodyWriter>, bkz: [ileti sınıfını kullanma](../../../../docs/framework/wcf/feature-details/using-the-message-class.md).  
  
## <a name="message-headers"></a>İleti üstbilgileri  
 Bir ileti üst bilgiler içerebilir. Üst bilgi mantıksal olarak bir ad, bir ad alanı ve diğer birkaç özellik ile ilişkili olan bir XML bilgi oluşur. İleti üstbilgilerini kullanarak erişilen `Headers` özellikte <xref:System.ServiceModel.Channels.Message>. Her üst bilgisi tarafından temsil edilen bir <xref:System.ServiceModel.Channels.MessageHeader> sınıfı. Normalde, ileti üstbilgileri SOAP iletilerini ile çalışmak için yapılandırılmış bir kanal yığını kullanırken SOAP ileti üstbilgilerini eşlenir.  
  
 İleti üst bilgisini veren ve ondan bilgilerini ayıklama ileti gövdesi kullanmaya benzer. Akış desteklenmediğinden bu işlem biraz basitleştirilmiştir. Birden çok kez aynı üst bilginin içeriklerini erişim sağlamak mümkündür ve üst bilgileri her zaman arabelleğe alınan üstbilgileri zorlama rastgele sırayla erişilebilir. Üst bilgisinin üzerinde bir XML okuyucuyu almak kullanılabilen genel amaçlı bir mekanizma yoktur, ancak var olan bir `MessageHeader` temsil eden bir tür özelliği okunabilir bir üstbilgiyle WCF için iç alt sınıfı. Bu tür `MessageHeader` özel uygulama üst bilgilerini içeren bir ileti geldiğinde kanal yığını tarafından oluşturulur. Bu gibi bir seri durumundan çıkarma altyapısı kullanmak hizmet çerçevesi sağlar <xref:System.Runtime.Serialization.DataContractSerializer>, bu üst bilgilerini yorumlamak için.  
  
 Daha fazla bilgi için [ileti sınıfını kullanma](../../../../docs/framework/wcf/feature-details/using-the-message-class.md).  
  
## <a name="message-properties"></a>İleti özellikleri  
 Bir ileti özellikleri içerebilir. A *özelliği* herhangi [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dize adıyla ilişkili nesne. Özellikleri aracılığıyla erişilir `Properties` özellikte `Message`.  
  
 İleti gövdesi ve (Bu, normalde SOAP üstbilgileri ve SOAP gövdesi için sırasıyla eşleştiren) ileti üstbilgileri aksine, ileti özelliklerini normalde gönderilen veya alınan iletileri yanı sıra. Kanal yığınında çeşitli kanallar kanal yığını ve hizmet modeli arasında ve ileti hakkında veri iletmek için öncelikle bir iletişim mekanizması olarak ileti özellikleri yok.  
  
 Örneğin, WCF bir parçası olarak dahil edilen HTTP taşıma kanalının çeşitli HTTP durum kodları gibi üretebilen "404 (bulunamadı)" ve "500 (iç sunucu hatası)," yanıtları istemcilere gönderdiğinde. Bir yanıt iletisi göndermeden önce onu denetleyen olmadığını `Properties` , `Message` "türünde bir nesne içeren httpResponse" adlı bir özellik içeren <xref:System.ServiceModel.Channels.HttpResponseMessageProperty>. Böyle bir özellik bulursa, görüneceğini <xref:System.ServiceModel.Channels.HttpResponseMessageProperty.StatusCode%2A> özelliği ve bu durum kodu kullanın. Bunu bulunamadı varsa, "200 (Tamam)" varsayılan kod kullanılır.  
  
 Daha fazla bilgi için [ileti sınıfını kullanma](../../../../docs/framework/wcf/feature-details/using-the-message-class.md).  
  
### <a name="the-message-as-a-whole"></a>Bir bütün olarak ileti  
 Şu ana kadar çeşitli bölümlerini yalıtım iletisinde erişmek için yöntemleri ele almıştık. Ancak, <xref:System.ServiceModel.Channels.Message> sınıfı, iletinin tamamı bir bütün olarak çalışmak için yöntemler de sağlar. Örneğin, `WriteMessage` yöntemi tüm yapılacak bir XML yazıcısına yazar.  
  
 Bu mümkün olması, tüm arasında bir eşleme tanımlanmalıdır `Message` örneği ve bir XML bilgi kümesi. Aslında, böyle bir eşleme var: WCF SOAP standart, bu eşlemeyi tanımlamak için kullanır. Olduğunda bir `Message` örneği yazılır XML bilgi kümesi elde edilen bilgi iletisini içeren geçerli bir SOAP Zarfı. Bu nedenle, `WriteMessage` normalde aşağıdaki adımları gerçekleştirmelisiniz:  
  
1. SOAP Zarfı öğe etiketiyle yazın.  
  
2. Etiketiyle SOAP üstbilgi öğesi yazma, tüm üstbilgileri yazmak ve header öğesi kapatın.  
  
3. SOAP gövdesi öğe etiketiyle yazın.  
  
4. Çağrı `WriteBodyContents` veya gövdesi yazmak için eşdeğer yöntemi.  
  
5. Gövde ve zarf öğeleri kapatın.  
  
 Önceki adımlarda, SOAP standart yakından bağlıdır. Bu karmaşık, birden fazla SOAP sürümünü, örneğin, mevcut olduğunu olgu tarafından kullanılan SOAP sürümü bilmeden SOAP Zarfı öğesi doğru şekilde yazmak mümkün değildir. Ayrıca, bazı durumlarda, bu karmaşık SOAP özgü devre dışı kapatmak için istenebilir tamamen eşleme.  
  
 Bu amaçlar için bir `Version` özelliği sağlanan `Message`. SOAP sürümüne, yapılacak yazarken kullanmak için ayarlanabilir veya kümesine `None` SOAP özel eşleme önlemek için. Varsa `Version` özelliği `None`, ileti gövdesinde yalnızca, örneğin, toplamda gibi tüm ileti Yasası işe yöntemleri `WriteMessage` yalnızca çağrı yapıyordu `WriteBodyContents` yukarıda listelenen birden çok adımı gerçekleştirmek yerine. Bu beklenen, gelen iletiler `Version` otomatik olarak algılanır ve doğru şekilde ayarlayın.  
  
## <a name="the-channel-stack"></a>Kanal yığını  
  
### <a name="channels"></a>Kanallar  
 Önce belirtildiği gibi kanal yığın giden oluşturmaktan sorumludur <xref:System.ServiceModel.Channels.Message> örnekleri (örneğin, paketlerin ağ üzerinden gönderme) bazı eyleme veya gelen (ağ paketlerinin alma gibi) bazı eylemleri dönüştürme `Message` örnekleri.  
  
 Kanal yığını sıralanmış bir sırayla bir veya daha fazla kanal oluşur. Giden `Message` örneği, Yığındaki ilk kanala geçirilir (olarak da adlandırılan *üstteki kanal*), Geçiren, sonraki kanala yığını ve benzeri. Çağrılan son kanalda ileti sonlandırır *taşıma kanalının*. Gelen ileti aktarım kanalda kaynaklanan ve kanal kanal yığını geçirilir. En üstteki kanaldan ileti genellikle hizmet çerçevesi geçirilir. Bu uygulama iletileri için normal desenin olsa da, bazı kanalları biraz farklı çalışabilir, örneğin, bunlar bir ileti olmadan bir kanaldan yukarıdaki geçirilen kendi altyapısı iletileri gönderebilir.  
  
 Yığın geçerken kanalları çeşitli şekillerde ileti üzerinde çalışabilir. En yaygın işlemi giden iletisinin üst bilgi ekleme ve bir gelen iletideki üstbilgiler olunurken. Örneğin, bir kanal bir iletinin dijital imza işlem ve üst bilgi olarak ekleyin. Bir kanal, gelen iletileri ve kanal yığınına aşamalarından yapmasını geçerli bir imzaya sahip olmayan iletileri engelle Bu dijital imza üst bilgisi de inceleyebilirsiniz. Kanalları da genellikle ayarlayın ya da ileti özelliklerini inceleyin. İleti gövdesi genellikle olan izin verilen olsa da, değiştirilmemiş, örneğin, WCF güvenlik kanalı ileti gövdesi şifrelemenize olanak tanır.  
  
### <a name="transport-channels-and-message-encoders"></a>Taşıma kanalları ve ileti kodlayıcılar  
 Alttaki kanal yığınında gerçekten giden dönüştürme için sorumlu <xref:System.ServiceModel.Channels.Message>gibi bazı eylemlere diğer kanallar tarafından değiştirilmiş. Bazı eylemlere dönüştüren kanal budur alma tarafında bir `Message` diğer işlem kanal.  
  
 Daha önce bahsedildiği gibi eylemleri değişmesi: gönderme veya çeşitli protokoller üzerinden ağ paketlerini alma, okuma veya bir veritabanında iletisi yazarken veya sıraya alma veya sağlamak için bir Message Queuing sırası, ancak birkaç örnek iletiyi kuyruktan çıkarma işlemlerini. Tüm bu eylemlerin ortak bir şey vardır: WCF arasında dönüştürme gerektirdikleri`Message` örneği ve bir gerçek grubu, alınan, okuma, yazılan gönderilebilecek bayt kuyruğa alınan veya kuyruktan çıkarıldı. Dönüştürme işlemi bir `Message` bayt bir grup olarak adlandırılır *kodlama*ve ters oluşturma işleminin bir `Message` bayt gruptan adlı *kod çözme*.  
  
 Çoğu taşıma kanalları adı verilen bileşenleri kullanma *ileti kodlayıcılar* kodlama ve kodunu çözme iş gerçekleştirmek için. İleti Kodlayıcı sınıfıdır <xref:System.ServiceModel.Channels.MessageEncoder> sınıfı. `MessageEncoder` çeşitli içerir `ReadMessage` ve `WriteMessage` arasında dönüştürmek için yöntem aşırı yüklemeleri `Message` ve grupları bayt.  
  
 Gönderen tarafında bir arabelleğe alma taşıma kanalının geçirir `Message` için yukarıda bir kanaldan alınan nesne `WriteMessage`. Ardından (örneğin, bu bayt olarak geçerli TCP paketlerini paketleme ve bunları doğru hedefe gönderirken), eylemi gerçekleştirmek için kullandığı bir bayt dizisi geri alır. İlk olarak bir akış taşıma kanalı oluşturur bir `Stream` (örneğin, giden TCP bağlantısı üzerinden) ve her ikisi de geçirir `Stream` ve `Message` uygun göndermek gereken `WriteMessage` aşırı yükleme, hangi yapılacak Yazar .  
  
 Alıcı tarafında bir dizi ve çağrıları bir arabelleğe alma taşıma kanalının gelen bayt (örneğin, gelen TCP paketleri) ayıklar `ReadMessage` almak için bir `Message` nesnesini kanal yığını başka geçirebilirsiniz. Bir akış taşıma kanalı oluşturur bir `Stream` nesne (örneğin, gelen TCP bağlantısı üzerinden ağ akışı) ve olarak geçirir `ReadMessage` geri almak için bir `Message` nesne.  
  
 Taşıma kanalları ve ileti Kodlayıcı arasındaki ayrımı zorunlu değildir; ileti Kodlayıcı kullanmayan bir taşıma kanalı yazmak mümkündür. Ancak, bu ayırma avantajı oluşturma kolaylığı olmasıdır. Taşıma kanalının yalnızca temel kullandığı sürece <xref:System.ServiceModel.Channels.MessageEncoder>, herhangi bir WCF veya üçüncü taraf ileti Kodlayıcısı ile çalışabilirsiniz. Benzer şekilde, aynı Kodlayıcı normalde herhangi bir aktarım kanalda kullanılabilir.  
  
### <a name="message-encoder-operation"></a>İleti Kodlayıcı işlemi  
 İşleme sırasında bir kodlayıcı açıklamak için aşağıdaki dört durumları kullanışlıdır.  
  
|Çalışma|Yorum|  
|---------------|-------------|  
|Kodlama, arabelleğe alınmış|Arabelleğe alınan modda Kodlayıcı normalde değişken boyutlu bir arabellek oluşturur ve üzerine bir XML yazıcısı oluşturur. Çağırır <xref:System.ServiceModel.Channels.Message.WriteMessage%28System.Xml.XmlWriter%29> üstbilgileri ve ardından gövdesi kullanarak çıkış yazan kodlanmakta, iletide <xref:System.ServiceModel.Channels.Message.WriteBodyContents%28System.Xml.XmlDictionaryWriter%29>, hakkında önceki bölümde açıklandığı gibi `Message` bu konuda. (Bir bayt dizisi olarak temsil edilir) arabellek içeriği daha sonra kullanmak için taşıma kanalı olarak döndürülür.|  
|Kodlama, akış|Akış modunda işlemi yukarıda, daha basit ancak benzer. Arabellek için gerek yoktur. Bir XML yazıcısı normalde akış üzerinden oluşturulur ve <xref:System.ServiceModel.Channels.Message.WriteMessage%28System.Xml.XmlWriter%29> üzerinde çağrılır `Message` bu yazıcısına yazılmasına yarar için.|  
|Kod çözme, arabelleğe alınmış|Arabellekli modu, özel bir kod çözme yaparken `Message` arabelleğe alınan verileri içeren alt sınıf normal olarak oluşturulur. İletinin üstbilgiler okunduktan ve ileti gövdesinde konumlandırılmış bir XML okuyucusu oluşturulur. Bu ile döndürülen okuyucusudur <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents>.|  
|Kod çözme, akış|Akış modunda kod çözme özel bir ileti alt normalde oluşturulur. Akış yetecek kadar tüm üst bilgileri okuyarak ve ileti gövdesinde konumlandırmak için gelişmiştir. Bir XML okuyucusu, ardından akış üzerinden oluşturulur. Bu ile döndürülen okuyucusudur <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents>.|  
  
 Kodlayıcıları diğer işlevler de gerçekleştirebilir. Örneğin, XML okuyucular ve yazıcılar kodlayıcılarda havuza alabilir. Bir gerekli her zaman yeni XML okuyucusu veya yazıcısı oluşturmak pahalıdır. Bu nedenle, havuzu okuyucular ve yazıcılar yapılandırılabilir boyut havuzu kodlayıcılar normalde korur. Daha önce açıklanan Kodlayıcı işlemi açıklamasında her "XML okuyucusu/yazıcı oluştur" kullanılır, tümcecik normalde "bir havuzdan almak veya mevcut değilse oluşturun." anlamına gelir Kodlayıcı (ve `Message` alt sınıflar oluşturur çözülürken) artık gerekli sonra okuyucular ve yazıcılar havuzlarına döndürmek için mantığı içerir (örneğin, `Message` kapalı).  
  
 Ek özel türlerinizi oluşturmak mümkün olmakla WCF üç ileti Kodlayıcı sunar. Sağlanan metin ve ikili ileti aktarım en iyi duruma getirme mekanizması (MTOM) türleridir. Bu ayrıntılı olarak açıklanan [ileti Kodlayıcı seçme](../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md).  
  
### <a name="the-istreamprovider-interface"></a>IStreamProvider arabirimi  
 Bir XML yazıcısı için akış gövde içeren bir giden iletisi yazarken <xref:System.ServiceModel.Channels.Message> çağrıları aşağıdakine benzer bir dizi kullanan kendi <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%28System.Xml.XmlDictionaryWriter%29> uygulama:  
  
- Akış (örneğin, XML etiketi açma) önceki tüm gerekli bilgileri yazın.  
  
- Akış yazın.  
  
- Akış (örneğin, XML kapatma etiketi) aşağıdaki bilgileri yazın.  
  
 Bu, iyi XML metin kodlaması benzer Kodlamalar ile çalışır. Ancak, bazı XML bilgi kümesi bilgileri (için başlangıç ve bitiş XML öğesi etiketler gibi) öğeleri içinde yer alan verileri birlikte yerleştirmeyin. Örneğin, kodlama MTOM ileti birden çok parçaya bölünür. Bir bölümü diğer bölümleri gerçek öğe içeriği için başvurular içerebilir XML bilgi içerir. XML bilgi kümesi sonrası bilgi kümesi arabellek, dışarı yazın ve ardından içeriği akış şekilde yazmak için mantıklı şekilde akış içeriği, karşılaştırma normalde küçüktür. Zaman kapatma buna öğesi etiketi yazıldığı akış henüz yazılmadı.  
  
 Bu amaçla <xref:System.Xml.IStreamProvider> arabirimi kullanılır. Arabirime sahip bir <xref:System.Xml.IStreamProvider.GetStream> yazılacak akış döndüren yöntem. Çıkış bir akış ileti gövdesine yazılacak doğru şekilde <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%28System.Xml.XmlDictionaryWriter%29> aşağıdaki gibidir:  
  
1. Akış (örneğin, XML etiketi açma) önceki tüm gerekli bilgileri yazın.  
  
2. Çağrı `WriteValue` üzerinde aşırı <xref:System.Xml.XmlDictionaryWriter> almayan bir <xref:System.Xml.IStreamProvider>, ile bir `IStreamProvider` yazılacak akış döndüren uygulama.  
  
3. Akış (örneğin, XML kapatma etiketi) aşağıdaki bilgileri yazın.  
  
 Bu yaklaşımda, XML yazıcısı çağrısı yapıldığında bir seçim olan <xref:System.Xml.IStreamProvider.GetStream> ve akış verileri yazma. Örneğin, metin ve ikili XML yazarların hemen çağırın ve akış içeriği raflarının başlangıç ve bitiş etiketleri yazma. MTOM yazıcı çağırmak isteyebilirsiniz <xref:System.Xml.IStreamProvider.GetStream> daha sonra uygun bir ileti parçası yazmak hazır olduğunda.  
  
## <a name="representing-data-in-the-service-framework"></a>Hizmet çerçevesi verileri temsil eden  
 Bu konunun "Temel mimari" bölümünde belirtildiği gibi hizmet çerçevesi olan, başka şeylerin yanında gerçek ve ileti verileri için kullanımı kolay bir programlama modeli arasında dönüştürme sorumlu WCF'nin bir parçası olan `Message` örnekleri. Normalde, bir ileti exchange hizmet çerçevesi temsil edilir bir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] ile işaretlenmiş yöntem <xref:System.ServiceModel.OperationContractAttribute> özniteliği. Yöntemin bazı parametreler alabilir ve dönüş değeri döndürebilir veya out Parametreleri (veya her ikisi de). Hizmet tarafında, giriş parametrelerini gelen ileti ve dönüş değeri temsil eder ve out Parametreleri giden ileti temsil eder. İstemci tarafında durumun tersi de geçerlidir. Parametreler ve dönüş değeri kullanarak iletileri tanımlamak için programlama modeli, ayrıntılı olarak açıklanan [hizmet sözleşmelerinde veri aktarımı belirtme](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md). Ancak, bu bölümde kısa bir genel bakış sağlar.  
  
## <a name="programming-models"></a>Programlama modelleri  
 WCF hizmet çerçevesi iletileri açıklamak için beş farklı programlama modeli destekler:  
  
### <a name="1-the-empty-message"></a>1. Boş ileti  
 Bu basit bir durumdur. Boş bir gelen iletiyi tanımlamak için tüm giriş parametrelerini kullanmayın.  
  
 [!code-csharp[C_DataArchitecture#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#3)]
 [!code-vb[C_DataArchitecture#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#3)]  
  
 Boş bir giden ileti açıklamak için bir void dönüş değeri kullanın ve dış parametrelerin kullanmayın:  
  
 [!code-csharp[C_DataArchitecture#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#4)]
 [!code-vb[C_DataArchitecture#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#4)]  
  
 Bu bir tek yönlü işlem sözleşmesinden farklı olduğuna dikkat edin:  
  
 [!code-csharp[C_DataArchitecture#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#5)]
 [!code-vb[C_DataArchitecture#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#5)]  
  
 İçinde `SetDesiredTemperature` örnek, bir iki yönlü ileti değişim deseni açıklanmıştır. Bir ileti işlemi döndürülür, ancak boş. Bu işlemi bir hata döndürmek mümkündür. Açıklamak için giden ileti yok olduğundan "Ampul Ayarla" örnekte ileti değişim deseni, tek yönlüdür. Bu durumda hizmet istemciye herhangi bir durum iletişim kuramıyor.  
  
### <a name="2-using-the-message-class-directly"></a>2. Doğrudan ileti sınıfını kullanma  
 Kullanmak mümkün mü <xref:System.ServiceModel.Channels.Message> sınıfı (ya da alt sınıflarından birini) doğrudan bir işlem anlaşması. Bu durumda, yalnızca hizmet çerçevesi geçirir `Message` işlemden kanal yığınına ve ayrıntılı işlem ile bunun tersi de geçerlidir.  
  
 Kullanmak için iki ana kullanım durumlar `Message` doğrudan. Diğer programlama modelleri hiçbiri iletinizi açıklamak için yeterli esneklik sağlar, bu Gelişmiş senaryolar için kullanabilirsiniz. Örneğin, bir ileti ile dosya özelliklerini ileti üstbilgileri ve ileti gövdesi olma dosyanın içeriği olmakla açıklamak için dosyalar diskte kullanmak isteyebilirsiniz. Daha sonra aşağıdakine benzer bir şey oluşturabilirsiniz.  
  
 [!code-csharp[C_DataArchitecture#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#6)]
 [!code-vb[C_DataArchitecture#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#6)]  
  
 İkinci genel kullanım için `Message` içinde bir işlem anlaşması içeriği ne zaman bir hizmet ile ilgili belirli iletiyi ilgilenmez ve iletide üzerinde siyah bir kutu olarak görev yapar. Örneğin, diğer birden çok alıcıya iletilerini ileten bir hizmet olabilir. Sözleşme şu şekilde yazılabilir.  
  
 [!code-csharp[C_DataArchitecture#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#7)]
 [!code-vb[C_DataArchitecture#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#7)]  
  
 Eylem = "*" satır etkili bir şekilde ileti gönderilirken devre dışı bırakır ve tüm iletiler için gönderilen sağlar `IForwardingService` Sözleşme Oluştur aşamalarından geçerek `ForwardMessage` işlemi. (Normalde, dağıtıcı işe yaradığını işlemi belirlemek için ileti üst bilgisi "Action" inceleyebilir. Eylem = "\*" "eylem üstbilgisinin tüm olası değerler" anlamına gelir.) Eylem birleşimi = "\*" ve ileti kullanarak, tüm olası ileti alabilen olduğundan "Evrensel sözleşme" bilinir. Tüm olası iletileri gönderebilmesi için ileti dönüş değeri olarak kullanın ve ayarlayın `ReplyAction` için "\*". Bu hizmet çerçevesi kullanarak bu üst denetim sağlayarak kendi eylem üst bilgisi eklemesini engeller `Message` iade ettiğiniz nesne.  
  
### <a name="3-message-contracts"></a>3. İleti Sözleşmeleri  
 WCF denen bir ileti açıklamak için bildirim temelli bir programlama modeli sağlar *ileti sözleşmeleri*. Bu model, ayrıntılı olarak açıklanan [kullanarak ileti sözleşmeleri](../../../../docs/framework/wcf/feature-details/using-message-contracts.md). Tarafından tek bir iletinin tamamı temelde gösterilir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] gibi öznitelikleri kullanan türü <xref:System.ServiceModel.MessageBodyMemberAttribute> ve <xref:System.ServiceModel.MessageHeaderAttribute> açıklayan ileti anlaşması sınıfı hangi parçalarının ileti hangi kısmına eşlenmesi gerekir.  
  
 İleti sözleşmeleri çok fazla sonuç üzerinde denetim sağlayın `Message` örnekleri (açıkça değil kadar denetim olarak kullanarak rağmen `Message` doğrudan sınıfı). Örneğin, İleti gövdeleri genellikle birden çok bilgi parçalarını oluşur, her kendi XML öğesi tarafından temsil edilir. Bu öğeleri ya da doğrudan gövdesinde oluşabilir (*çıplak* modu) ya da *sarmalanmış* kapsamlı bir XML öğesi. Programlama modeli ileti anlaşması kullanarak sarmalanmış karşı çıplak kararı ve sarmalayıcı adı ve ad alanı adı denetlemenizi sağlar.  
  
 Bir ileti anlaşması aşağıdaki kod örneği, bu özellikleri gösterir.  
  
 [!code-csharp[C_DataArchitecture#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#9)]
 [!code-vb[C_DataArchitecture#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#9)]  
  
 İşaretli öğeleri serileştirilecek (ile <xref:System.ServiceModel.MessageBodyMemberAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute>, veya ilgili diğer öznitelikler) içinde bir ileti anlaşması katılmak için seri hale getirilebilir olması gerekir. Daha fazla bilgi için bu konunun ilerleyen bölümlerindeki "Serileştirme" bölümüne bakın.  
  
### <a name="4-parameters"></a>4. Parametreler  
 Genellikle, birden çok veri parçasını üzerinde işlevi gören bir işlemi tanımlamak için isteyen bir geliştirici ileti sözleşmeleri sağlayan ve kontrol derecesi gerek yoktur. Örneğin, yeni hizmetler oluştururken bir genellikle sarmalanmış karşı çıplak kararı ve sarmalayıcı öğe adı üzerinde karar vermek istemez. Bu kararların genellikle SOAP ve Web Hizmetleri konusundaki geniş bilgi birikiminden gerektirir.  
  
 WCF hizmet çerçevesi gönderme veya birden çok ilgili bilgilere, kullanıcı bu seçenekleri zorlamadan alma için en iyi ve en birlikte çalışabilen SOAP gösterimi otomatik olarak seçebilirsiniz. Bu parametre olarak bu bilgilerin açıklayarak gerçekleştirilir veya bir işlem anlaşması değerlerini döndürür. Örneğin, aşağıdaki işlem anlaşması göz önünde bulundurun.  
  
 [!code-csharp[C_DataArchitecture#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#11)]
 [!code-vb[C_DataArchitecture#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#11)]  
  
 Hizmet çerçevesi, tüm üç parça bilgi yerleştirmek otomatik olarak karar (`customerID`, `item`, ve `quantity`) ileti gövdesi ve kaydırma halinde bunları bir sarmalayıcı öğe adlı `SubmitOrderRequest`.  
  
 Gönderilen veya önerilen yaklaşım, basit bir işlem anlaşması parametrelerin listesi olduğu gibi daha karmaşık ileti anlaşması için taşıma için özel nedenleri mevcut sürece alınan bilgilere açıklayan veya `Message`-tabanlı programlama modeli.  
  
### <a name="5-stream"></a>5. Akış  
 Kullanarak `Stream` ya da işlem anlaşması veya bir tek ileti Gövde bölümünün bir ileti anlaşması içinde alt sınıflarından birini olarak kabul edilir yukarıda açıklanan gördüğünüzden ayrı bir programlama modeli. Kullanarak `Stream` bu şekilde sözleşmeniz kendi akış uyumlu yazma eksikliği akışlı bir biçimde, kullanılabilir olacağını garanti etmek için tek yoludur `Message` öğesinin alt sınıfı. Daha fazla bilgi için [büyük veriler ve akış](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).  
  
 Zaman `Stream` veya alt sınıflarından birini bu şekilde kullanıldığında, seri hale getirici çağrılamaz. Özel akış giden iletiler için `Message` alt oluşturulur ve akış üzerinde bölümünde açıklandığı gibi out yazılır <xref:System.Xml.IStreamProvider> arabirimi. Hizmet çerçevesi için gelen iletiler, oluşturur bir `Stream` alt üzerinden gelen ileti işlemi sağlar.  
  
## <a name="programming-model-restrictions"></a>Programlama modeli kısıtlamaları  
 Yukarıda açıklanan programlama modelleri rasgele birleştirilemez. Örneğin, bir işlem bir ileti anlaşması türü kabul ederse, ileti anlaşması, yalnızca giriş parametresinin olması gerekir. Ayrıca, dönüş boş bir ileti (dönüş türü void) veya başka bir ileti sonra Sözleşme işlemi gerekir. Programlama modeli kısıtlamalarının her belirli bir programlama modeli için konular açıklanmaktadır: [İleti sözleşmeleri kullanılıyor](../../../../docs/framework/wcf/feature-details/using-message-contracts.md), [ileti sınıfını kullanma](../../../../docs/framework/wcf/feature-details/using-the-message-class.md), ve [büyük veriler ve akış](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).  
  
## <a name="message-formatters"></a>İleti Biçimlendiriciler  
 Yukarıda açıklanan programlama modelleri takma adlı bileşenleri tarafından desteklenen *ileti biçimlendiriciler* halinde hizmet çerçevesi. İleti biçimlendiriciler olan uygulayan türler <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> veya <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> arabirimi veya her ikisini birden kullanımda ve hizmet WCF istemciler, sırasıyla.  
  
 İleti biçimlendiriciler normalde tarafından davranışları takılır. Örneğin, <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> içinde veri sözleşme ileti biçimlendirici yararlanmanıza imkan sağlar. Bu hizmet tarafında ayarlayarak yapılır <xref:System.ServiceModel.Dispatcher.DispatchOperation.Formatter%2A> içinde doğru biçimlendirici için <xref:System.ServiceModel.Description.IOperationBehavior.ApplyDispatchBehavior%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Dispatcher.DispatchOperation%29> yöntemi veya ayarlayarak istemci tarafında <xref:System.ServiceModel.Dispatcher.ClientOperation.Formatter%2A> içinde doğru biçimlendirici için <xref:System.ServiceModel.Description.IOperationBehavior.ApplyClientBehavior%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Dispatcher.ClientOperation%29> yöntemi.  
  
 Aşağıdaki tablolar, bir ileti biçimlendirici uygulayabilir yöntemleri listeler.  
  
|Arabirim|Yöntem|Eylem|  
|---------------|------------|------------|  
|<xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter>|<xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter.DeserializeRequest%28System.ServiceModel.Channels.Message%2CSystem.Object%5B%5D%29>|Gelen bir dönüştürür `Message` için işlem parametreleri|  
|<xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter>|<xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter.SerializeReply%28System.ServiceModel.Channels.MessageVersion%2CSystem.Object%5B%5D%2CSystem.Object%29>|Giden oluşturur `Message` işleminden dönüş değeri/out Parametreleri|  
|<xref:System.ServiceModel.Dispatcher.IClientMessageFormatter>|<xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.SerializeRequest%28System.ServiceModel.Channels.MessageVersion%2CSystem.Object%5B%5D%29>|Giden oluşturur `Message` işlemi parametrelerinden|  
|<xref:System.ServiceModel.Dispatcher.IClientMessageFormatter>|<xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.DeserializeReply%28System.ServiceModel.Channels.Message%2CSystem.Object%5B%5D%29>|Gelen bir dönüştürür `Message` dönüş değeri/out Parametreleri|  
  
## <a name="serialization"></a>Serileştirme  
 İleti içeriğini açıklamak için ileti sözleşmeleri veya parametrelerini kullandığınızda arasında dönüştürmek için serileştirme kullanmalısınız [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] türleri ve XML bilgi kümesi gösterimi. Serileştirme kullanılan diğer bölümlerinde WCF, örneğin, <xref:System.ServiceModel.Channels.Message> genel sahip <xref:System.ServiceModel.Channels.Message.GetBody%2A> bir nesnede seri durumdan iletinin tamamı gövdesini okumak için kullanabileceğiniz yöntem.  
  
 WCF serileştirme ve seri durumdan çıkarılırken parametreleri ve message bölümleri için "kullanıma hazır" iki seri hale getirme teknolojilerini destekler: <xref:System.Runtime.Serialization.DataContractSerializer> ve `XmlSerializer`. Ayrıca, özel seri hale getiricileri genişletme yazabilirsiniz. Ancak, WCF diğer bölümlerini (genel gibi `GetBody` yöntemi veya SOAP serileştirme hata) yalnızca kullanmak için kısıtlı olabilir <xref:System.Runtime.Serialization.XmlObjectSerializer> alt sınıfları (<xref:System.Runtime.Serialization.DataContractSerializer> ve <xref:System.Runtime.Serialization.NetDataContractSerializer>, ama <xref:System.Xml.Serialization.XmlSerializer>), ya da yalnızca kullanılacak kodlanmış olabilir <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
 `XmlSerializer` Serileştirme motoruna kullanılan [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web Hizmetleri. `DataContractSerializer` Yeni veri sözleşme programlama modelini anlayan yeni seri hale getirme altyapısı. `DataContractSerializer` Varsayılan seçenek ve kullanma seçimi `XmlSerializer` kullanarak bir işlem başına temel yapılabilir <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.DataContractFormatAttribute%2A> özniteliği.  
  
 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> ve <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> işlem davranışları için ileti biçimlendiriciler takma için sorumlu olan `DataContractSerializer` ve `XmlSerializer`sırasıyla. <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> Davranışı ile türetilen seri hale getirici gerçekten çalışabilir <xref:System.Runtime.Serialization.XmlObjectSerializer>de dahil olmak üzere <xref:System.Runtime.Serialization.NetDataContractSerializer> (tek başına serileştirme kullanarak ayrıntılı açıklanmıştır). Davranış birini çağırır `CreateSerializer` serileştiriciyi almak için sanal bir yöntem aşırı yüklemeleri. Farklı bir serileştirici takmak için yeni bir oluşturma <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> alt sınıf ve geçersiz kılma `CreateSerializer` aşırı yüklemeleri.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hizmet Anlaşmalarında Veri Aktarımını Belirtme](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)
