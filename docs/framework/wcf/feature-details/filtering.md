---
title: Filtreleme
ms.date: 03/30/2017
ms.assetid: 4002946c-e34a-4356-8cfb-e25912a4be63
ms.openlocfilehash: 74915a45ed5ca1d13790f64c7921d1f750fa04d3
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43789009"
---
# <a name="filtering"></a>Filtreleme
Sistem filtreleme Windows Communication Foundation (WCF), iletileri eşleşmesi ve işletimsel karar vermek için bildirim temelli filtreleri kullanabilirsiniz. Filtreleri içeren bir ileti iletinin bölümünü inceleyerek yapmanız gerekenler belirlemek için kullanabilirsiniz. Sıraya alma işlemi, örneğin, priority öğesi bir ileti kuyruğu öne taşınıp taşınmayacağını belirleme bilinen üstbilgisinin denetlemek için bir XPath 1.0 sorgu kullanabilirsiniz.  
  
 Filtreleme sistemini verimli bir şekilde gerçekleştirebileceğiniz sınıfları kümesinden oluşan bir filtre kümesi olan belirlemek `true` belirli bir WCF ileti.  
  
 Filtreleme sistemini WCF Mesajlaşma çekirdek bileşenidir; son derece hızlı olacak şekilde tasarlanmıştır. Her filtre uygulama, belirli bir tür WCF iletileri karşı eşleştirme için iyileştirilmiştir.  
  
 Filtreleme sistemini iş parçacığı güvenli değildir. Uygulamanın herhangi bir kilitleme semantiği işlemesi gerekir. Ancak, birden çok Okuyucu, tek bir yazıcı destekler.  
  
## <a name="where-filtering-fits"></a>Burada filtreleme uyar  
 Bir ileti alındığında ve uygun uygulama bileşeni için ileti gönderilirken işleminin bir parçası olan sonra filtre uygulanmaz. Filtreleme sistemin tasarımını Mesajlaşma, yönlendirme, güvenlik, olay işleme ve sistem yönetimi dahil olmak üzere çeşitli WCF alt gereksinimlerini ele alır.  
  
## <a name="filters"></a>FilTReleri  
 Filtre altyapısı, filtreler ve filtre tabloları olmak üzere iki birincil bileşenden oluşur. Bir filtre, kullanıcı tarafından belirtilen mantıksal koşullara göre bir ileti hakkında Boole kararlarını verir. Filtreler uygulamak <xref:System.ServiceModel.Dispatcher.MessageFilter> sınıfı.  
  
 <xref:System.ServiceModel.Dispatcher.MessageFilter.Match%2A> Yöntemleri, bir ileti bir filtre karşılayıp karşılamadığını belirlemek için kullanılır. Yöntemlerinden biri olan ileti üst bilgisi testleri, ancak ileti gövdesi İnceleme olamaz. Diğer yöntem alır bir *ileti arabelleği* giriş parametresi olarak ve ileti gövdesi inceleyebilirsiniz.  
  
 Filtreler değil genellikle test ayrı ayrı, ancak bir filtre tablo bir parçası olarak olduğu genel, sınıf <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601.CreateFilterTable%2A> yöntemi oluşturur.  
  
 Filtreleri her çeşitli türlerde belirli bir Boolean koşulu türünü eşleşen uzmanlaşmıştır. Bir filtre oluşturmak sonra bir filtre kullanır, ölçütleri değiştiremezsiniz; bir filtre ölçütlerini değiştirmek için yeni bir tane oluşturun ve mevcut filtresini Sil.  
  
### <a name="action-filters"></a>Eylem filtreleri  
 <xref:System.ServiceModel.Dispatcher.ActionMessageFilter> Eylem dizeleri listesini içerir. Filtrenin listesindeki eylemlerden herhangi birini eşleşiyorsa ileti veya mesaj arabelleğine eylem üstbilgisinde `Match` yöntemi döndürür `true`. Liste boşsa, filtre eşleşen tüm filtre ve iletisi ve ileti arabelleği eşleşen kabul edilir ve `Match` döndürür `true`. Filtrenin listesindeki eylemleri hiçbiri ileti veya mesaj arabelleğine eylem üstbilgisinde eşleşiyorsa `Match` döndürür `false`. İletide bir eylem ve filtre listesi boş ise `Match` döndürür `false`.  
  
### <a name="endpoint-address-filters"></a>Uç nokta adresi filtreleri  
 <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter> Filtreler iletileri ve bir uç nokta adresini temel alan ileti arabelleklerinin üstbilgi koleksiyonu içinde temsil edilen. Bir ileti gibi bir filtre geçirmek aşağıdaki koşullar karşılanmalıdır:  
  
-   Filtrenin adresi Tekdüzen Kaynak Tanımlayıcısı (URI) bir ileti üst bilgisi ile aynı olmalıdır.  
  
-   Her uç nokta parametresi filtre adresini (`address.Headers` koleksiyonu) bir başlık iletisi üzerinde eşlemek için bulmanız gerekir. Fazladan üst bilgiler ileti veya mesaj arabelleğine eşleşme kalması kabul edilebilir `true`.  
  
### <a name="prefix-endpoint-address-filters"></a>Uç nokta adresi filtreleri öneki  
  
1.  <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> İşlevleri olduğu gibi <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter> filtre dışında eşleşmenin bir ön ek iletisinin URI olabilir. Örneğin, adresi belirten bir filtre http://www.adatum.com eşleşen gönderilen iletileri http://www.adatum.com/userA.  
  
### <a name="xpath-message-filters"></a>XPath ileti filtreleri  
 Bir <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> bir XPath ifadesi içeren bir XML belgesi belirli öğeler, öznitelikler, metin veya diğer XML söz dizimi yapıları olup olmadığını belirlemek için kullanır. Filtre bir katı XPath alt kümesi için son derece etkili olması için optimize edilmiştir. XML Path Language açıklanan [W3C XML yolu dil 1.0 belirtimi](https://go.microsoft.com/fwlink/?LinkId=94779).  
  
 Genellikle, bir uygulamanın kullandığı bir <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> SOAP iletisi ve gerçekleştirilen işlemlerin içeriğini sorgulamak için bir uç noktada uygun eylemi sorgu sonuçlarına dayalı. Sıraya alma işlemi, örneğin, sıranın önüne bir ileti geçmeye karar vermek için bir bilinen üstbilgisinin priority öğesi incelemek için bir XPath sorgusu kullanabilir.  
  
## <a name="filter-tables"></a>Filtre tabloları  
 Filtre tabloları, burada bir filtre anahtarı, ilişkilendirilmiş bazı veri değeri ise anahtar-değer çiftlerini depolamak için kullanılır. Filtre verisi belirten bir ileti eşleşen filtre ve filtre veri türünü genel parametresi filtre tablo sınıfı için yapılacak işlemler için kullanılabilir. Filtre verisi, yönlendirme kuralları, oturumun güvenlik durumunu, kanal dinleyicileri oluşur ve benzeri. Veriler, veri akış denetimi gerekli olduğu kullanılabilir.  
  
 Filtre tabloları yönelik genel arabirimi uygulayan <xref:System.ServiceModel.Dispatcher.IMessageFilterTable%601>.  
  
 Filtre tabloların bir ileti tabloda tüm filtreleriyle eşleşen ve sırasız koleksiyonunun eşleşen filtreleri ya da veri dönüş çeşitli yöntemler vardır. Eşleşme yöntemlerden bazıları birden çok eşleşme ve tüm eşleşen öğeleri döndürür. Başkaları tek-match, yalnızca bir öğe döndüren ve throw bir <xref:System.ServiceModel.Dispatcher.MultipleFilterMatchesException> birden fazla filtre eşleşmesi durumunda.  
  
### <a name="message-filter-table"></a>İleti filtreleme tablosu  
 <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> En genel uygulamasıdır <xref:System.ServiceModel.Dispatcher.IMessageFilterTable%601>. Tablodaki tüm türleri filtreler depolayabilirsiniz.  
  
 En yüksek önceliği en yüksek sayısı burada miktarlara filtreleri, sayısal öncelikleri atayabilirsiniz. Birden çok filtre türleri, aynı önceliğe sahip olabilir. Filtre, belirli bir tür içindeki birden fazla öncelik düzeyi görünebilir.  
  
 Eşleşen yapılır en yüksek öncelik ile başlayan ve bir kez filtrelerle eşleşen bulunan söz konusu önceliğe, daha düşük önceliklere sahip filtre incelenir. Bu nedenle, kullanıyorsanız tek filtresini kullanarak eşleşen yöntemi, eşleşen birden fazla filtre bir ileti ancak eşleşen her filtre farklı bir önceliği olan, hiçbir özel durum ve en yüksek öncelikli filtre döndürülür. Benzer şekilde, birden çok filtre uyuşan yöntemi yalnızca en yüksek öncelikli filtrelerle eşleşen.  
  
### <a name="xpath-message-filter-table"></a>XPath İleti Filtresi tablosu  
 <xref:System.ServiceModel.Dispatcher.XPathMessageFilterTable%601> Bildirim temelli XPath filtrelerinde için iyileştirilmiş tablo anahtarı, bu nedenle bir <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.  
  
 <xref:System.ServiceModel.Dispatcher.XPathMessageFilterTable%601> Sınıfı, ileti senaryolarının çoğunu kapsar ve ayrıca tam XPath 1.0 dilbilgisi destekleyen XPath bir alt kümesi için eşleşen iyileştirir. Verimli paralel eşleşen algoritmalar için iyileştirilmiş.  
  
 Bu tablo vardır özelleştirilmiş `Match` üzerinden çalışan yöntemleri bir <xref:System.Xml.XPath.XPathNavigator> ve <xref:System.ServiceModel.Dispatcher.SeekableXPathNavigator>. A <xref:System.ServiceModel.Dispatcher.SeekableXPathNavigator> genişletir <xref:System.Xml.XPath.XPathNavigator> ekleyerek sınıfı bir <xref:System.ServiceModel.Dispatcher.SeekableXPathNavigator.CurrentPosition%2A> özelliği. Bu özellik kaydedilebilir ve Gezgin, pahalı bellek ayırması kopyalamak zorunda kalmadan kolayca yüklenebilir için XML belgesi içindeki konumları sağlayan, <xref:System.Xml.XPath.XPathNavigator> bu tür bir işlem gerektirir. WCF XPath altyapısı sorguları XML belgelerinde, yürütme sırasında imleç konumu sık kaydetmeniz gerekir böylece <xref:System.ServiceModel.Dispatcher.SeekableXPathNavigator> ileti işleme için önemli bir iyileştirme sağlar.  
  
## <a name="customer-scenarios"></a>Müşteri senaryoları  
 Farklı işleme modülleri ileti içinde yer alan verilere bağlı olarak bir ileti göndermek için istediğiniz zaman filtresini kullanabilirsiniz. İki tipik senaryo, eylem koduna göre ve temel alınan iletileri uç noktası adresi iletileri akışını XML'deki çoğullama bir ileti yönlendirme.  
  
### <a name="routing"></a>Yönlendirme  
 İletinin SOAP üst bilgisinde bir veya daha fazla eylem kodları olan iletiler için bir uç noktası dinleyicisi dinler. Oluşturarak uygulayan bir <xref:System.ServiceModel.Dispatcher.ActionMessageFilter> oluşturucusuna eylem kodları içeren bir dizi geçirerek. Bu filtre kaydolmak için kullandığı `ListenerFactory`, bu nedenle, belirli bir uç nokta için olan eylem eşleşen filtre biri yalnızca iletileri alın.  
  
### <a name="de-multiplexing"></a>XML'deki çoğullama  
 Ne zaman birden fazla uç nokta fan aynı `ServiceListener` kablo, iletileri çoğullamasını ve bir belirli uç nokta adresine ait olup olmadığını bilmek tek yolu kullanmaktır <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter>s, kayıtlı uç noktaları tarafından doğru iletileri seçin üst bilgilerinde depolanan bilgileri bir arama gerçekleştirme. Bu filtrelere geçen iletileri hem de karşılık gelen tüm gerekli üstbilgileri vardır:  
  
-   URI'de `EndpointAddress`.  
  
-   Rest uç noktası parametrelerini `EndpointAddress` belirtilmiş <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Aktarma ve Seri Hale Getirme](../../../../docs/framework/wcf/feature-details/data-transfer-and-serialization.md)
