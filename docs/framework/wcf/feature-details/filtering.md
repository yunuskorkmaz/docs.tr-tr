---
title: Filtreleme
ms.date: 03/30/2017
ms.assetid: 4002946c-e34a-4356-8cfb-e25912a4be63
ms.openlocfilehash: 5f599ac74aa63951f59c5e5c79d3fe37b2ab5100
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="filtering"></a>Filtreleme
Sistem filtreleme Windows Communication Foundation (WCF) iletileri eşleşmiyor ve işletimsel kararları için bildirim temelli filtreleri kullanabilirsiniz. Yapılacaklar içeren bir ileti iletinin parçası inceleyerek belirlemek için filtreleri kullanabilirsiniz. Sıraya alma işlemi, örneğin, bir ileti sıranın önünü taşınıp taşınmayacağını belirlemek için bilinen bir üstbilgi öncelik öğesinin denetlemek için XPath 1.0 sorgusu kullanabilirsiniz.  
  
 Filtreleme sistem verimli bir şekilde yapabilirsiniz sınıfları kümesinden oluşan bir filtre kümesi hangisinin belirlemek `true` belirli bir WCF ileti.  
  
 Filtreleme sistem WCF Mesajlaşma çekirdek bileşenidir; son derece hızlı çalışacak şekilde tasarlanmıştır. Her filtre uygulama belirli bir tür WCF iletileri karşı eşleştirme için optimize edilmiştir.  
  
 Filtreleme sistemi iş parçacığı içinde korumalı değil. Uygulama, kilitleme tüm söz dizimini işlemesi gerekir. Ancak, çok Okuyucu, tek bir yazıcı destekler.  
  
## <a name="where-filtering-fits"></a>Burada filtreleme uygun  
 Bir ileti alındı ve uygun uygulama bileşeni için ileti gönderilirken işleminin parçası sonra filtreleme gerçekleştirilir. Filtreleme sistem tasarımını Mesajlaşma, yönlendirme, güvenlik, olay işleme ve sistem yönetimi dahil olmak üzere çeşitli WCF alt gereksinimlerini ele alır.  
  
## <a name="filters"></a>FilTReleri  
 Filtre Altyapısı filtreleri ve filtre tabloları olmak üzere iki birincil bileşenleri içerir. Bir filtre kullanıcı tarafından belirtilen mantıksal koşullara göre bir ileti hakkında Boolean kararlarını verir. Filtreler uygulamasına <xref:System.ServiceModel.Dispatcher.MessageFilter> sınıfı.  
  
 <xref:System.ServiceModel.Dispatcher.MessageFilter.Match%2A> Yöntemleri bir ileti bir filtre karşılayan varsa belirlemek için kullanılır. Yöntemlerden birini iletinin üstbilgisi test eder, ancak ileti gövdesi incelemek olamaz. Başka bir yöntem geçen bir *ileti arabelleği* giriş parametresi olarak ve ileti gövdesini inceleyebilirsiniz.  
  
 Filtreler değil genellikle sınanır ayrı ayrı, ancak bir filtre tablo bir parçası olarak olduğu genel, sınıf <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601.CreateFilterTable%2A> yöntemi oluşturur.  
  
 Filtreler her çeşitli türlerde üzerindeki belirli bir türdeki Boolean koşulun eşleştirmelerinde specialize. Bir filtre oluşturun sonra bir filtre kullanır, ölçüt değiştirilemiyor; bir filtrenin ölçütlerini değiştirmek için yeni bir tane oluşturun ve mevcut filtreyi silin.  
  
### <a name="action-filters"></a>Eylem filtreleri  
 <xref:System.ServiceModel.Dispatcher.ActionMessageFilter> Eylem dizelerinin listesini içerir. Filtrenin listesindeki eylemlerden herhangi birini eşleşirse ileti veya ileti arabelleği eylem üstbilgisinde `Match` yöntemi döndürür `true`. Liste boşsa, filtre eşleşen tüm filtre ve ileti veya ileti arabellek eşleşen kabul edilir ve `Match` döndürür `true`. Filtrenin listesindeki eylemleri hiçbiri ileti veya ileti arabelleği eylem üstbilgisinde eşleşirse `Match` döndürür `false`. İletinin eylemi yok ve filtre listesi boş, ardından ise `Match` döndürür `false`.  
  
### <a name="endpoint-address-filters"></a>Uç nokta adresi filtreleri  
 <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter> Filtreler iletileri ve bir uç nokta adresini temel alan ileti arabelleklerinin kendi üstbilgi koleksiyonunda belirtildiği şekilde. Bir ileti gibi bir filtre geçirmek aşağıdaki koşulların karşılanması gerekir:  
  
-   Filtrenin adresi Tekdüzen Kaynak Tanımlayıcısı (URI) iletinin üstbilgisi için birinde ile aynı olmalıdır.  
  
-   Her filtre adresini uç nokta parametresinde (`address.Headers` koleksiyonu) bir başlık iletisi üzerinde eşlemek için bulmanız gerekir. Fazladan üstbilgiler ileti veya ileti arabelleği kalmasına eşleştirme için kabul edilebilir `true`.  
  
### <a name="prefix-endpoint-address-filters"></a>Uç nokta adresi filtreleri önek  
  
1.  <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> İşlevleri olduğu gibi <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter> eşleşme URI ileti ön ekini temel olabilir ancak bu filtre. Örneğin, adres belirten bir filtre http://www.adatum.com eşleşen gönderilen iletileri http://www.adatum.com/userA.  
  
### <a name="xpath-message-filters"></a>XPath ileti filtreleri  
 Bir <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> bir XPath ifadesi bir XML belgesi içeriyor belirli öğeleri, öznitelikleri, metin veya diğer XML söz dizimi oluşturur olup olmadığını belirlemek için kullanır. Filtre XPath katı bir kısmı için son derece etkili olması için optimize edilmiştir. XML Path dili açıklanan [W3C XML yol dili 1.0 belirtimi](http://go.microsoft.com/fwlink/?LinkId=94779).  
  
 Genellikle, uygulama kullanan bir <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> bir SOAP iletisi ve gerçekleştirilen işlemlerin içeriğini sorgulamak için bir uç noktada uygun eylemi sorgu sonuçlarına dayalı. Sıraya alma işlemi, örneğin, ileti sıranın önünü taşıma karar vermek için bilinen bir üstbilgi öncelik öğesinin incelemek için bir XPath sorgusu kullanabilir.  
  
## <a name="filter-tables"></a>Filtre tabloları  
 Filtre tabloları, burada bir filtre anahtarı ve ilişkilendirilmiş bazı veri değeri anahtar-değer çiftlerini depolamak için kullanılır. Filtre veri bir ileti filtre ile eşleşen ve filtre veri türünü genel parametresi filtre tablo sınıfı için ise yapılacak işlemler belirtmek için kullanılabilir. Filtre veri yönlendirme kuralları, oturum güvenlik durumu, kanal dinleyicileri oluşur ve benzeri. Verileri veri akış denetimi gerekli olduğu kullanılabilir.  
  
 Filtre tabloları genel arabirim uygulama <xref:System.ServiceModel.Dispatcher.IMessageFilterTable%601>.  
  
 Filtre tabloların bir ileti tablosundaki tüm filtreleriyle eşleşen ve eşleşen filtre ya da veri sırasız bir koleksiyonu çeşitli yöntemler vardır. Eşleşme yöntemlerin bazıları birden çok eşleşme ve tüm eşleşen öğeleri döndürür. Başkalarının tek-match, yalnızca bir öğe, döndürme ve throw bir <xref:System.ServiceModel.Dispatcher.MultipleFilterMatchesException> birden fazla filtre eşleşmesi durumunda.  
  
### <a name="message-filter-table"></a>İleti Filtresi tablosu  
 <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> En genel uygulamasıdır <xref:System.ServiceModel.Dispatcher.IMessageFilterTable%601>. Tablodaki her türlü filtreleri depolayabilirsiniz.  
  
 En yüksek önceliğe göre en yüksek sayı burada belirtilir filtreleri, sayısal öncelikleri atayabilirsiniz. Birden çok tür filtre aynı önceliğe sahip olabilir. Belirli bir filtre türü içinde birden fazla öncelik düzeyi yer alabilir.  
  
 Eşleşen yapılır en yüksek öncelikli başlatma ve bir kez filtreleri ile eşleşen bulunduğunda olan belirli önceliği, daha düşük önceliklerin hiçbir filtrelerle incelenmesini. Bu nedenle, kullanıyorsanız eşleşen yöntemi, bir tek filtresi kullanarak birden fazla filtre ile eşleşen bir ileti ancak her bir eşleşen filtre farklı bir önceliği olan, hiçbir özel durum ve en yüksek önceliğe sahip filtre döndürülür. Benzer şekilde, birden çok filtre eşleştiğinden yöntemi döndürür yalnızca en yüksek öncelikli filtreleri ile eşleşen.  
  
### <a name="xpath-message-filter-table"></a>XPath İleti Filtresi tablosu  
 <xref:System.ServiceModel.Dispatcher.XPathMessageFilterTable%601> Tablo anahtarı böylece bildirim temelli XPath filtreleri için optimize edilmiş bir <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.  
  
 <xref:System.ServiceModel.Dispatcher.XPathMessageFilterTable%601> Sınıfı iyileştirir ileti senaryolarının çoğunu kapsar ve ayrıca tam XPath 1.0 dilbilgisi destekleyen XPath bir kısmı için eşleşen. Verimli paralel eşleme algoritmaları optimize etti.  
  
 Bu tablo vardır özelleştirilmiş `Match` üzerinden çalışan yöntemleri bir <xref:System.Xml.XPath.XPathNavigator> ve <xref:System.ServiceModel.Dispatcher.SeekableXPathNavigator>. A <xref:System.ServiceModel.Dispatcher.SeekableXPathNavigator> genişletir <xref:System.Xml.XPath.XPathNavigator> ekleyerek sınıfı bir <xref:System.ServiceModel.Dispatcher.SeekableXPathNavigator.CurrentPosition%2A> özelliği. Bu özellik kaydedilebilir ve pahalı bellek ayırma Gezgini kopyalama gerek kalmadan hızlı bir şekilde yüklenebilir için XML belgesi içindeki konumlarına izin verir, <xref:System.Xml.XPath.XPathNavigator> için böyle bir işlem gerektirir. WCF XPath altyapısı sık sorgular XML belgelerinde, yürütme esnasında imleç konumu kaydetmeniz gerekir böylece <xref:System.ServiceModel.Dispatcher.SeekableXPathNavigator> ileti işleme için önemli bir iyileştirme sağlar.  
  
## <a name="customer-scenarios"></a>Müşteri senaryoları  
 İletinin içerdiği verilere bağlı olarak farklı işleme modülleri bir ileti göndermek için istediğiniz zaman filtresini kullanabilir. İki tipik senaryolar, eylem koduna göre ve iletileri uç nokta adresine dayalı iletilerinin bir akış XML'deki çoğullama bir ileti yönlendirme.  
  
### <a name="routing"></a>Yönlendirme  
 İletinin SOAP üstbilgisinde bir veya daha fazla eylem kodları olan iletiler için bir uç nokta dinleyicisi dinler. Oluşturarak uygulayan bir <xref:System.ServiceModel.Dispatcher.ActionMessageFilter> kendi oluşturucusunu eylem kodları içeren bir dizi geçirerek. Bu filtre kaydolmak için kullandığı `ListenerFactory`, bu belirli uç noktasına, eylem filtresi biri eşleşen yalnızca iletileri almak için.  
  
### <a name="de-multiplexing"></a>XML'deki çoğullama  
 Ne zaman birden çok uç nokta fan aynı `ServiceListener` kablo iletileri çoğullamasını ve bir belirli uç nokta adresine ait olup olmadığını bilmek için tek yoludur kullanmak için <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter>kayıtlı uç noktaları tarafından doğru mesajlar s bir arama üstbilgilerinde depolanan bilgileri gerçekleştiriliyor. Bu filtreler, hem de karşılık gelen tüm gerekli üstbilgileri geçmesi iletileri vardır:  
  
-   URI'de `EndpointAddress`.  
  
-   Uç nokta parametrelerinde kalan `EndpointAddress` belirtilmiş <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Aktarma ve Seri Hale Getirme](../../../../docs/framework/wcf/feature-details/data-transfer-and-serialization.md)
