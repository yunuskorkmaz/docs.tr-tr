---
title: Filtreleme
ms.date: 03/30/2017
ms.assetid: 4002946c-e34a-4356-8cfb-e25912a4be63
ms.openlocfilehash: efbedc16fe48d83cdc4223862bc691e9cbe15c10
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964289"
---
# <a name="filtering"></a>Filtreleme
Windows Communication Foundation (WCF) filtreleme sistemi, iletileri eşleştirmek ve işlem kararları almak için bildirim temelli filtreler kullanabilir. İleti parçasını inceleyerek, bir iletiyle ne yapılacağını belirlemek için filtreler kullanabilirsiniz. Örneğin, bir sıraya alma işlemi, bir iletiyi kuyruğun önüne taşıyıp taşımayacağını anlamak için bilinen bir üstbilginin öncelik öğesini denetlemek üzere bir XPath 1,0 sorgusu kullanabilir.  
  
 Filtreleme sistemi, belirli bir WCF iletisi için `true` bir filtre kümesinden hangisinin etkin bir şekilde belirleyebilen bir sınıf kümesinden oluşur.  
  
 Filtreleme sistemi, WCF mesajlaşma 'nın çekirdek bileşenidir; Son derece hızlı olacak şekilde tasarlanmıştır. Her filtre uygulama, WCF iletileriyle belirli bir tür eşleştirme için iyileştirilmiştir.  
  
 Filtreleme sistemi iş parçacığı güvenli değildir. Uygulamanın herhangi bir kilitleme semantiğini işlemesi gerekir. Ancak, çok okuyuculu tek bir yazıcıyı destekler.  
  
## <a name="where-filtering-fits"></a>Filtrelemenin sığması  
 Filtre, bir ileti alındıktan ve doğru uygulama bileşenine ileti gönderme işleminin bir parçası olduktan sonra yapılır. Filtreleme sisteminin tasarımı, mesajlaşma, yönlendirme, güvenlik, olay işleme ve sistem yönetimi de dahil olmak üzere birkaç WCF alt sisteminin gereksinimlerini ele alınmaktadır.  
  
## <a name="filters"></a>FilTReleri  
 Filtre altyapısının iki adet birincil bileşeni, filtre ve filtre tabloları vardır. Filtre, Kullanıcı tarafından belirtilen mantıksal koşullara göre bir iletiyle ilgili Boole kararları verir. Filtreler <xref:System.ServiceModel.Dispatcher.MessageFilter> sınıfını uygular.  
  
 <xref:System.ServiceModel.Dispatcher.MessageFilter.Match%2A> yöntemleri, bir iletinin bir filtreyi karşılayıp karşılamadığını belirlemede kullanılır. Yöntemlerden biri iletinin üstbilgisini sınar, ancak ileti gövdesini inceleyin. Diğer yöntem, giriş parametresi olarak bir *ileti arabelleği* alır ve ileti gövdesini inceleyebilir.  
  
 Filtreler genellikle ayrı ayrı sınanmamıştır, ancak <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601.CreateFilterTable%2A> yönteminin oluşturduğu genel bir sınıf olan filtre tablosunun bir parçası olarak.  
  
 Her biri belirli bir tür Boolean koşulunda eşleşen birçok filtre türü. Bir filtre oluşturduktan sonra, bir filtrenin kullandığı kriterleri değiştiremezsiniz; bir filtrenin ölçütlerini değiştirmek için yenisini oluşturun ve var olan filtreyi silin.  
  
### <a name="action-filters"></a>Eylem filtreleri  
 <xref:System.ServiceModel.Dispatcher.ActionMessageFilter> eylem dizelerinin bir listesini içerir. Filtre listesindeki eylemlerden herhangi biri ileti veya ileti arabelleğindeki eylem üstbilgisiyle eşleşiyorsa, `Match` yöntemi `true`döndürür. Liste boşsa, filtre eşleşme olarak kabul edilir-tüm filtre ve ileti veya ileti arabelleğinin eşleşmesi ve `Match` `true`döndürür. Filtre listesindeki eylemlerden hiçbiri ileti veya ileti arabelleğindeki eylem üstbilgisiyle eşleşiyorsa, `Match` `false`döndürür. İletide bir eylem yoksa ve filtrenin listesi boş değilse, `Match` `false`döndürür.  
  
### <a name="endpoint-address-filters"></a>Uç nokta adres filtreleri  
 <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter>, üst bilgi koleksiyonunda gösterildiği gibi, bir uç nokta adresini temel alarak iletileri ve ileti arabelleklerini filtreler. Bu tür bir filtre iletmek için aşağıdaki koşulların karşılanması gerekir:  
  
- Filtrenin adres Tekdüzen Kaynak tanımlayıcısı (URI), üstbilgideki ileti Ile aynı olmalıdır.  
  
- Filtrenin adresindeki her bir uç nokta parametresi (`address.Headers` Collection), üzerinde eşlenecek iletideki bir üst bilgi bulmalıdır. İleti veya ileti arabelleğindeki ek üstbilgiler, eşleşme `true`kalacak şekilde kabul edilebilir.  
  
### <a name="prefix-endpoint-address-filters"></a>Önek uç noktası adres filtreleri  
  
1. <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter>, eşleşme ileti URI 'sinin bir ön eki üzerinde olabilir, ancak <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter> filtresi gibi çalışır. Örneğin, adresi belirten bir filtre, `http://www.adatum.com/userA`adreslenen iletilerle eşleşir `http://www.adatum.com`.  
  
### <a name="xpath-message-filters"></a>XPath Ileti filtreleri  
 Bir <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>, bir XML belgesinin belirli öğeler, öznitelikler, metin veya diğer XML sözdizimi yapıları içerip içermediğini anlamak için bir XPath ifadesi kullanır. Filtre, XPath 'in katı bir alt kümesi için son derece etkili olacak şekilde iyileştirilmiştir. XML yol dili [W3C XML yol dili 1,0 belirtiminde](https://www.w3.org/TR/xpath/all/)açıklanmıştır.  
  
 Genellikle, bir uygulama bir SOAP iletisinin içeriğini sorgulamak için bir uç noktada <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> kullanır ve ardından bu sorgunun sonuçlarına göre uygun eylemi gerçekleştirir. Örneğin, bir sıraya alma işlemi, bir iletiyi kuyruğun önüne taşıyıp taşımayacağına karar vermek üzere bilinen üstbilginin öncelik öğesini incelemek için bir XPath sorgusu kullanabilir.  
  
## <a name="filter-tables"></a>Tabloları filtrele  
 Filtre tabloları anahtar-değer çiftlerini depolamak için kullanılır; burada bir filtre anahtar ve ilişkili veriler ise değerdir. Filtre verileri, filtre ile eşleşen bir ileti ve filtre verilerinin türü, filtre tablosu sınıfının genel parametresi ise, hangi eylemlerin yapılacağını belirtmek için kullanılabilir. Filtre verileri yönlendirme kurallarından, oturum güvenlik durumundan, bir kanaldaki dinleyicilerine ve bu şekilde olabilir. Veriler veri akışı denetiminin gerekli olduğu yerde kullanılabilir.  
  
 Filtre tabloları genel arabirimi <xref:System.ServiceModel.Dispatcher.IMessageFilterTable%601>uygular.  
  
 Filtre tablolarında, tablodaki tüm filtrelere karşı eşleşen ve eşleşen filtrelerin veya verilerin sıralanmamış bir koleksiyonunu döndüren çeşitli yöntemler vardır. Eşleşme yöntemlerinden bazıları birden çok eşleşmedir ve eşleşen tüm öğeleri döndürür. Diğerleri tek eşleşmedir, yalnızca bir öğe döndürüyor ve birden fazla filtre eşleşiyorsa <xref:System.ServiceModel.Dispatcher.MultipleFilterMatchesException> oluşturur.  
  
### <a name="message-filter-table"></a>İleti Filtresi tablosu  
 <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> en genel <xref:System.ServiceModel.Dispatcher.IMessageFilterTable%601>uygulamasıdır. Tablodaki tüm türlerin filtrelerini saklayabilirsiniz.  
  
 En yüksek önceliğin en yüksek sayıya göre kullanıldığı filtrelere sayısal öncelikler atayabilirsiniz. Birden çok filtre türü aynı önceliğe sahip olabilir. Belirli bir filtre türü, birden fazla öncelik düzeyinde görünebilir.  
  
 Eşleştirme en yüksek önceliğe göre yapılır ve belirli bir önceliğe sahip eşleşen filtreler bulunduğunda, daha düşük önceliklere sahip hiçbir filtre incelenir. Bu nedenle, tek bir filtre eşleştirme yöntemi kullanıyorsanız ve bir iletiyle birden çok filtre eşleşiyorsa, ancak eşleşen her filtrenin farklı bir önceliği varsa, hiçbir özel durum oluşturulmaz ve en yüksek önceliğe sahip filtre döndürülür. Benzer şekilde, birden çok filtreli eşleşme yöntemi yalnızca en yüksek önceliğe sahip eşleşen filtreleri döndürür.  
  
### <a name="xpath-message-filter-table"></a>XPath Iletisi filtre tablosu  
 <xref:System.ServiceModel.Dispatcher.XPathMessageFilterTable%601> bildirim temelli XPath filtreleri için iyileştirilmiştir, bu nedenle tablo anahtarı bir <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.  
  
 <xref:System.ServiceModel.Dispatcher.XPathMessageFilterTable%601> sınıfı, birçok mesajlaşma senaryosunu içeren bir XPath alt kümesi için eşleştirmeyi iyileştirir ve ayrıca tam XPath 1,0 dilbilgisini destekler. Etkili paralel eşleştirme için iyileştirilmiş algoritmalara sahiptir.  
  
 Bu tabloda, bir <xref:System.Xml.XPath.XPathNavigator> ve <xref:System.ServiceModel.Dispatcher.SeekableXPathNavigator>üzerinde çalışan çeşitli özelleştirilmiş `Match` yöntemleri vardır. Bir <xref:System.ServiceModel.Dispatcher.SeekableXPathNavigator> <xref:System.Xml.XPath.XPathNavigator> sınıfını bir <xref:System.ServiceModel.Dispatcher.SeekableXPathNavigator.CurrentPosition%2A> özelliği ekleyerek genişletir. Bu özellik, XML belgesi içindeki konumların, bu tür bir işlem için ihtiyaç duyduğu pahalı bir bellek ayırma <xref:System.Xml.XPath.XPathNavigator> olan gezgin 'i kopyalamaya gerek olmadan hızla kaydedilmesine ve yüklenmesine izin verir. WCF XPath altyapısı, XML belgelerinde sorgu yürütme sırasında imlecin konumunu sıklıkla kaydetmeniz gerekir, bu nedenle <xref:System.ServiceModel.Dispatcher.SeekableXPathNavigator> ileti işleme için önemli bir iyileştirme sağlar.  
  
## <a name="customer-scenarios"></a>Müşteri senaryoları  
 İleti içinde bulunan verilere bağlı olarak farklı işleme modüllerine ileti göndermek istediğiniz zaman filtrelemeyi kullanabilirsiniz. İki tipik senaryo, işlem koduna göre bir iletiyi yönlendirerek iletilerin bir uç nokta adresini temel alan bir ileti akışını de aynı şekilde alır.  
  
### <a name="routing"></a>Yönlendirme  
 Bir uç noktanın dinleyicisi, iletinin SOAP üstbilgisindeki bir veya daha fazla eylem koduna sahip iletileri dinler. Bu işlemi, eylem kodlarını içeren bir diziyi oluşturucusuna geçirerek bir <xref:System.ServiceModel.Dispatcher.ActionMessageFilter> oluşturarak uygulayabilirsiniz. Bu filtre, `ListenerFactory`kaydetmek için bu filtreyi kullanır, bu nedenle yalnızca eylemi bu belirli bir uç noktaya sahip olan filtreden biriyle eşleşen mesajlar.  
  
### <a name="de-multiplexing"></a>Çoğullama  
 Birden fazla uç nokta, aynı `ServiceListener` olduğunda, her zaman çift yönlü mesajlardan bağımsız olarak ileti kullanmanın ve belirli bir uç nokta adresine ait olup olmadığını bilmenin tek yolu, üst bilgilerde depolanan bilgilerde bir arama gerçekleştirerek kayıtlı uç noktalara giden iletileri seçme <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter>s ' nin kullanılması anlamına gelir. Bu filtrelerde, yalnızca geçen iletiler, her ikisine karşılık gelen gerekli tüm üstbilgilere sahiptir:  
  
- `EndpointAddress`URI 'SI.  
  
- <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter>belirtilen `EndpointAddress` uç nokta parametrelerinin geri kalanı.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Aktarma ve Seri Hale Getirme](../../../../docs/framework/wcf/feature-details/data-transfer-and-serialization.md)
