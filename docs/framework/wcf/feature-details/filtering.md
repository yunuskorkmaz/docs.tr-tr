---
title: Filtreleme
ms.date: 03/30/2017
ms.assetid: 4002946c-e34a-4356-8cfb-e25912a4be63
ms.openlocfilehash: d04141e4720320784bc92c332a3f0b96a7b1ac92
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595472"
---
# <a name="filtering"></a>Filtreleme
Windows Communication Foundation (WCF) filtreleme sistemi, iletileri eşleştirmek ve işlem kararları almak için bildirim temelli filtreler kullanabilir. İleti parçasını inceleyerek, bir iletiyle ne yapılacağını belirlemek için filtreler kullanabilirsiniz. Örneğin, bir sıraya alma işlemi, bir iletiyi kuyruğun önüne taşıyıp taşımayacağını anlamak için bilinen bir üstbilginin öncelik öğesini denetlemek üzere bir XPath 1,0 sorgusu kullanabilir.  
  
 Filtreleme sistemi, `true` belirli BIR WCF iletisi için bir filtre kümesinden hangisinin olacağını etkili bir şekilde belirleyebilen bir sınıf kümesinden oluşur.  
  
 Filtreleme sistemi, WCF mesajlaşma 'nın çekirdek bileşenidir; Son derece hızlı olacak şekilde tasarlanmıştır. Her filtre uygulama, WCF iletileriyle belirli bir tür eşleştirme için iyileştirilmiştir.  
  
 Filtreleme sistemi iş parçacığı güvenli değildir. Uygulamanın herhangi bir kilitleme semantiğini işlemesi gerekir. Ancak, çok okuyuculu tek bir yazıcıyı destekler.  
  
## <a name="where-filtering-fits"></a>Filtrelemenin sığması  
 Filtre, bir ileti alındıktan ve doğru uygulama bileşenine ileti gönderme işleminin bir parçası olduktan sonra yapılır. Filtreleme sisteminin tasarımı, mesajlaşma, yönlendirme, güvenlik, olay işleme ve sistem yönetimi de dahil olmak üzere birkaç WCF alt sisteminin gereksinimlerini ele alınmaktadır.  
  
## <a name="filters"></a>FilTReleri  
 Filtre altyapısının iki adet birincil bileşeni, filtre ve filtre tabloları vardır. Filtre, Kullanıcı tarafından belirtilen mantıksal koşullara göre bir iletiyle ilgili Boole kararları verir. Filtreler sınıfı uygular <xref:System.ServiceModel.Dispatcher.MessageFilter> .  
  
 <xref:System.ServiceModel.Dispatcher.MessageFilter.Match%2A>Yöntemler bir iletiyi bir filtre karşılayıp karşılamadığını belirlemekte kullanılır. Yöntemlerden biri iletinin üstbilgisini sınar, ancak ileti gövdesini inceleyin. Diğer yöntem, giriş parametresi olarak bir *ileti arabelleği* alır ve ileti gövdesini inceleyebilir.  
  
 Filtreler genellikle ayrı ayrı sınanmamıştır, ancak bir filtre tablosunun bir parçası olarak, yöntemin oluşturduğu genel bir sınıftır <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601.CreateFilterTable%2A> .  
  
 Her biri belirli bir tür Boolean koşulunda eşleşen birçok filtre türü. Bir filtre oluşturduktan sonra, bir filtrenin kullandığı kriterleri değiştiremezsiniz; bir filtrenin ölçütlerini değiştirmek için yenisini oluşturun ve var olan filtreyi silin.  
  
### <a name="action-filters"></a>Eylem filtreleri  
 , <xref:System.ServiceModel.Dispatcher.ActionMessageFilter> Eylem dizelerinin bir listesini içerir. Filtre listesindeki eylemlerden herhangi biri ileti veya ileti arabelleğindeki eylem üstbilgisiyle eşleşiyorsa, `Match` yöntemi döndürür `true` . Liste boşsa, filtre eşleşme-All filtresi olarak değerlendirilir ve herhangi bir ileti veya ileti arabelleği eşleşir ve `Match` döndürür `true` . Filtre listesindeki eylemlerden hiçbiri ileti veya ileti arabelleğindeki eylem üstbilgisiyle eşleşiyorsa, `Match` döndürür `false` . İletide bir eylem yoksa ve filtrenin listesi boş değilse, öğesini `Match` döndürür `false` .  
  
### <a name="endpoint-address-filters"></a>Uç nokta adres filtreleri  
 <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter>İletileri ve ileti arabelleğini, üst bilgi koleksiyonunda gösterildiği gibi bir uç nokta adresine göre filtreler. Bu tür bir filtre iletmek için aşağıdaki koşulların karşılanması gerekir:  
  
- Filtrenin adres Tekdüzen Kaynak tanımlayıcısı (URI), üstbilgideki ileti Ile aynı olmalıdır.  
  
- Filtrenin (koleksiyon) adresindeki her bir uç nokta parametresi `address.Headers` , üzerinde eşlenecek ileti içinde bir başlık bulmalıdır. İleti veya ileti arabelleğindeki ek üstbilgiler, eşleşmenin kalması için kabul edilebilir `true` .  
  
### <a name="prefix-endpoint-address-filters"></a>Önek uç noktası adres filtreleri  
  
1. <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter> Eşleşme, ileti URI 'sinin bir ön eki üzerinde olabilir, ancak filtreye benzer işlevler. Örneğin, adresi belirten bir filtre ile `http://www.adatum.com` adreslenen iletilerle eşleşir `http://www.adatum.com/userA` .  
  
### <a name="xpath-message-filters"></a>XPath Ileti filtreleri  
 Bir <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> XML belgesinin belirli öğeleri, öznitelikleri, metinleri veya DIĞER XML sözdizimsel yapılarını içerip içermediğini anlamak için bir XPath ifadesi kullanır. Filtre, XPath 'in katı bir alt kümesi için son derece etkili olacak şekilde iyileştirilmiştir. XML yol dili [W3C XML yol dili 1,0 belirtiminde](https://www.w3.org/TR/xpath/all/)açıklanmıştır.  
  
 Genellikle, bir uygulama bir <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> SOAP iletisinin içeriğini sorgulamak için bir uç noktada kullanır ve ardından bu sorgunun sonuçlarına göre uygun eylemi gerçekleştirir. Örneğin, bir sıraya alma işlemi, bir iletiyi kuyruğun önüne taşıyıp taşımayacağına karar vermek üzere bilinen üstbilginin öncelik öğesini incelemek için bir XPath sorgusu kullanabilir.  
  
## <a name="filter-tables"></a>Tabloları filtrele  
 Filtre tabloları anahtar-değer çiftlerini depolamak için kullanılır; burada bir filtre anahtar ve ilişkili veriler ise değerdir. Filtre verileri, filtre ile eşleşen bir ileti ve filtre verilerinin türü, filtre tablosu sınıfının genel parametresi ise, hangi eylemlerin yapılacağını belirtmek için kullanılabilir. Filtre verileri yönlendirme kurallarından, oturum güvenlik durumundan, bir kanaldaki dinleyicilerine ve bu şekilde olabilir. Veriler veri akışı denetiminin gerekli olduğu yerde kullanılabilir.  
  
 Filtre tabloları genel arabirimini uygular <xref:System.ServiceModel.Dispatcher.IMessageFilterTable%601> .  
  
 Filtre tablolarında, tablodaki tüm filtrelere karşı eşleşen ve eşleşen filtrelerin veya verilerin sıralanmamış bir koleksiyonunu döndüren çeşitli yöntemler vardır. Eşleşme yöntemlerinden bazıları birden çok eşleşmedir ve eşleşen tüm öğeleri döndürür. Diğerleri tek eşleşmedir, yalnızca bir öğe döndürüyor ve birden <xref:System.ServiceModel.Dispatcher.MultipleFilterMatchesException> çok filtre eşleşiyorsa bir oluşturur.  
  
### <a name="message-filter-table"></a>İleti Filtresi tablosu  
 , <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> En genel uygulamasıdır <xref:System.ServiceModel.Dispatcher.IMessageFilterTable%601> . Tablodaki tüm türlerin filtrelerini saklayabilirsiniz.  
  
 En yüksek önceliğin en yüksek sayıya göre kullanıldığı filtrelere sayısal öncelikler atayabilirsiniz. Birden çok filtre türü aynı önceliğe sahip olabilir. Belirli bir filtre türü, birden fazla öncelik düzeyinde görünebilir.  
  
 Eşleştirme en yüksek önceliğe göre yapılır ve belirli bir önceliğe sahip eşleşen filtreler bulunduğunda, daha düşük önceliklere sahip hiçbir filtre incelenir. Bu nedenle, tek bir filtre eşleştirme yöntemi kullanıyorsanız ve bir iletiyle birden çok filtre eşleşiyorsa, ancak eşleşen her filtrenin farklı bir önceliği varsa, hiçbir özel durum oluşturulmaz ve en yüksek önceliğe sahip filtre döndürülür. Benzer şekilde, birden çok filtreli eşleşme yöntemi yalnızca en yüksek önceliğe sahip eşleşen filtreleri döndürür.  
  
### <a name="xpath-message-filter-table"></a>XPath Iletisi filtre tablosu  
 , <xref:System.ServiceModel.Dispatcher.XPathMessageFilterTable%601> Bildirim temelli XPath filtreleri için en iyi duruma getirilmiştir, bu nedenle tablo anahtarı bir olur <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> .  
  
 <xref:System.ServiceModel.Dispatcher.XPathMessageFilterTable%601>Sınıfı, birçok mesajlaşma senaryosunu içeren bir XPath alt kümesi için eşleştirmeyi iyileştirir ve ayrıca tam xpath 1,0 dilbilgisini destekler. Etkili paralel eşleştirme için iyileştirilmiş algoritmalara sahiptir.  
  
 Bu tabloda, ve arasında `Match` çalışan çeşitli özelleştirilmiş yöntemler bulunur <xref:System.Xml.XPath.XPathNavigator> <xref:System.ServiceModel.Dispatcher.SeekableXPathNavigator> . Bir <xref:System.ServiceModel.Dispatcher.SeekableXPathNavigator> <xref:System.Xml.XPath.XPathNavigator> özellik ekleyerek sınıfı genişletir <xref:System.ServiceModel.Dispatcher.SeekableXPathNavigator.CurrentPosition%2A> . Bu özellik, XML belgesi içindeki konumların, bu <xref:System.Xml.XPath.XPathNavigator> tür bir işlem için gereken pahalı bir bellek ayırma olan gezgin 'i kopyalamaya gerek olmadan hızlı bir şekilde kaydedilmesine ve yüklenmesine izin verir. WCF XPath altyapısının, XML belgelerinde sorgu yürütmek için genellikle imlecin konumunu kayıt ettirmelidir, bu nedenle <xref:System.ServiceModel.Dispatcher.SeekableXPathNavigator> ileti işleme için önemli bir iyileştirme sağlar.  
  
## <a name="customer-scenarios"></a>Müşteri senaryoları  
 İleti içinde bulunan verilere bağlı olarak farklı işleme modüllerine ileti göndermek istediğiniz zaman filtrelemeyi kullanabilirsiniz. İki tipik senaryo, işlem koduna göre bir iletiyi yönlendirerek iletilerin bir uç nokta adresini temel alan bir ileti akışını de aynı şekilde alır.  
  
### <a name="routing"></a>Yönlendirme  
 Bir uç noktanın dinleyicisi, iletinin SOAP üstbilgisindeki bir veya daha fazla eylem koduna sahip iletileri dinler. Bu <xref:System.ServiceModel.Dispatcher.ActionMessageFilter> işlemi, kendi oluşturucuya eylem kodlarını içeren bir diziyi geçirerek oluşturursunuz. Bu filtre, ile kaydolmak için bu filtreyi kullanır `ListenerFactory` , bu nedenle yalnızca eylemi bu belirli bir uç noktaya sahip olan filtreden biriyle eşleşen mesajlar.  
  
### <a name="de-multiplexing"></a>Çoğullama  
 Birden çok uç nokta, aynı noktadan itibaren bir `ServiceListener` arada olduğunda, tek bir uç nokta adresine dahil etmenin yanı sıra belirli bir uç nokta adresine ait olup olmadığını bilmenin tek yolu, <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter> üst bilgilerde depolanan bilgilere bir arama gerçekleştirerek kayıtlı uç noktalara giden iletileri seçme işlemini kullanmaktır. Bu filtrelerde, yalnızca geçen iletiler, her ikisine karşılık gelen gerekli tüm üstbilgilere sahiptir:  
  
- İçindeki URI `EndpointAddress` .  
  
- ' De belirtilen as içindeki Endpoint parametrelerinin geri kalanı `EndpointAddress` <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Aktarma ve Seri Hale Getirme](data-transfer-and-serialization.md)
