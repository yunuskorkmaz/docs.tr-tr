---
title: İleti Filtreleri
ms.date: 03/30/2017
helpviewer_keywords:
- routing [WCF], message filters
ms.assetid: cb33ba49-8b1f-4099-8acb-240404a46d9a
ms.openlocfilehash: a953dea9224d75907c593d87f06a0b0888f0af2d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184668"
---
# <a name="message-filters"></a>İleti Filtreleri
İçerik tabanlı yönlendirmeyi uygulamak için Yönlendirme Hizmeti, <xref:System.ServiceModel.Dispatcher.MessageFilter> iletinin adres, bitiş noktası adı veya belirli bir XPath deyimi gibi belirli bölümlerini denetleyen uygulamaları kullanır. Sağlanan [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] ileti filtrelerinin hiçbiri gereksinimlerinizi karşılamazsa, taban <xref:System.ServiceModel.Dispatcher.MessageFilter> sınıfın yeni bir uygulamasını oluşturarak özel bir filtre oluşturabilirsiniz.  
  
 Yönlendirme Hizmetini yapılandırırken, **MessageFilter** türünü açıklayan<xref:System.ServiceModel.Routing.Configuration.FilterElement> filtre öğelerini (nesneler) ve ileti içinde aranacak belirli dize değerleri gibi filtreyi oluşturmak için gereken destekleyici verileri tanımlamanız gerekir. Filtre öğelerini oluşturmanın yalnızca tek tek ileti filtrelerini tanımladığını unutmayın; İletileri değerlendirmek ve yönlendirmek için filtreleri kullanmak için bir<xref:System.ServiceModel.Routing.Configuration.FilterTableEntryCollection>filtre tablosu da tanımlamanız gerekir ( ).  
  
 Filtre tablosundaki her giriş bir filtre öğesine başvurur ve ileti filtreyle eşleşiyorsa iletinin yönlendirilen istemci bitiş noktasını belirtir. Filtre tablosu girişleri, birincil bitiş noktasına gönderirken<xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection>iletinin iletinin iletileceği uç noktaların listesini tanımlayan yedek uç noktaları ( ) bir koleksiyonunu da belirtmenize olanak sağlar. Bu uç noktalar, başarılı olana kadar belirtilen sırada denenecektir.  
  
## <a name="message-filters"></a>İleti Filtreleri  
 Yönlendirme Hizmeti tarafından kullanılan ileti filtreleri, iletinin gönderildiği bitiş noktasının adını, SOAP eylemini veya iletinin gönderildiği adres veya adres önekini değerlendirmek gibi yaygın ileti seçimi işlevselliği sağlar. Filtreler bir `AND` koşulla da birleşebilir, böylece iletiler yalnızca ileti her iki filtreyle de eşleşirse bitiş noktasına yönlendirilir. Ayrıca kendi uygulama nızı oluşturarak özel <xref:System.ServiceModel.Dispatcher.MessageFilter>filtreler oluşturabilirsiniz.  
  
 Aşağıdaki tabloda <xref:System.ServiceModel.Routing.Configuration.FilterType> Yönlendirme Hizmeti tarafından kullanılan, belirli ileti filtresini uygulayan sınıf ve <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A> gerekli parametreler listelemektedir.  
  
|Filtre Türü|Açıklama|Veri Anlamını Filtrele|Örnek Filtre|  
|------------------|-----------------|-------------------------|--------------------|  
|Eylem|Belirli <xref:System.ServiceModel.Dispatcher.ActionMessageFilter> bir eylem içeren iletileri eşleştirmek için sınıfı kullanır.|Üzerine filtre uygulanacak eylem.|\<filtre adı="action1" filterType="Action" filterData=" "http://namespace/contract/operation/>|  
|Endpointaddress|Belirli <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter> bir adres <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter.IncludeHostNameInComparison%2A>  ==  `true` içeren iletileri eşleştirmek için sınıfı kullanır.|Filtre uygulanacak adres (To üstbilgisinde).|\<filtre adı="address1" filterType="EndpointAddress" filterData=" "http://host/vdir/s.svc/b/>|  
|Uç NoktaAdresÖnek|Belirli <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> bir adres <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter.IncludeHostNameInComparison%2A>  ==  `true` öneki içeren iletileri eşleştirmek için sınıfı kullanır.|En uzun önek eşlemi kullanarak filtrelenebilmek için adres.|\<filtre adı="önek1" filterType="EndpointAddressPrefix" filterData=" "http://host//>|  
|And|Dönmeden <xref:System.ServiceModel.Dispatcher.StrictAndMessageFilter> önce her iki koşulu da değerlendiren sınıfı kullanır.|filterData kullanılmaz; bunun yerine filter1 ve filter2 ilgili ileti filtrelerinin adlarına (ayrıca tabloda) sahiptir ve bu da birlikte **ve**ed olmalıdır.|\<filtre adı="and1" filterType="Ve" filter1="address1" filter2="action1" />|  
|Özel|<xref:System.ServiceModel.Dispatcher.MessageFilter> Sınıfı genişleten ve bir dize alan bir oluşturucuya sahip kullanıcı tanımlı bir tür.|customType özniteliği oluşturmak için sınıfın tam nitelikli tür adıdır; filterData, filtreyi oluştururken oluşturucuya geçirilen dizedir.|\<filtre adı="custom1" filterType="Custom" customType="CustomAssembly.CustomMsgFilter, CustomAssembly" filterData="Özel Veriler" />|  
|EndpointName|İletileri, geldikleri hizmet bitiş noktasının adını temel alan olarak eşleştirmek için <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> sınıfı kullanır.|Hizmet bitiş noktasının adı, örneğin: "serviceEndpoint1".  Bu, Yönlendirme Hizmeti'nde açığa çıkan uç noktalardan biri olmalıdır.|\<filtre adı="stock1" filterType="Endpoint" filterData="SvcEndpoint" />|  
|MatchAll|<xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> Sınıfı kullanır. Bu filtre, gelen tüm iletilerle eşleşir.|filterData kullanılmaz. Bu filtre her zaman tüm iletilerle eşleşir.|\<filtre adı="matchAll1" filterType="MatchAll" />|  
|XPath|İleti <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> içindeki belirli XPath sorgularını eşleştirmek için sınıfı kullanır.|İletileri eşleştirirken kullanılacak XPath sorgusu.|\<filtre adı="XPath1" filterType="XPath" filterData="//ns:element" />|  
  
 Aşağıdaki örnekte, XPath, EndpointName ve PrefixEndpointAddress ileti filtrelerini kullanan filtre girişleri tanımlanıyor. Bu örnek, RoundRobinFilter1 ve RoundRobinFilter2 girişleri için özel bir filtre kullanılmasını da gösterir.  
  
```xml  
<filters>  
     <filter name="XPathFilter" filterType="XPath"
             filterData="/s12:Envelope/s12:Header/custom:RoundingCalculator = 1"/>  
     <filter name="EndpointNameFilter" filterType="EndpointName"
             filterData="calculatorEndpoint"/>  
     <filter name="PrefixAddressFilter" filterType="PrefixEndpointAddress"
             filterData="http://localhost/routingservice/router/rounding/"/>  
     <filter name="RoundRobinFilter1" filterType="Custom"
             customType="RoutingServiceFilters.RoundRobinMessageFilter,
             RoutingService" filterData="group1"/>  
     <filter name="RoundRobinFilter2" filterType="Custom"
             customType="RoutingServiceFilters.RoundRobinMessageFilter,
             RoutingService" filterData="group1"/>  
</filters>  
```  
  
> [!NOTE]
> Yalnızca bir filtre tanımlamak iletilerin filtreye karşı değerlendirilmesine neden olmaz. Filtre, daha sonra Yönlendirme Hizmeti tarafından açığa çıkarılan hizmet bitiş noktasıyla ilişkili olan bir filtre tablosuna eklenmelidir.  
  
### <a name="namespace-table"></a>Ad Alanı Tablosu  
 XPath filtresi kullanırken, Ad alanlarının kullanımı nedeniyle XPath sorgusunu içeren filtre verileri son derece büyük olabilir. Bu sorunu gidermek için Yönlendirme Hizmeti, ad alanı tablosunu kullanarak kendi ad alanı öneklerinizi tanımlama olanağı sağlar.  
  
 Ad alanı tablosu, XPath'te kullanılabilecek ortak ad alanları için ad alanı önekleri tanımlayan <xref:System.ServiceModel.Routing.Configuration.NamespaceElement> nesneler topluluğudur. Aşağıda, ad alanı tablosunda bulunan varsayılan ad alanları ve ad alanı önekleri ve ad alanı önekleri vereme leri vereme leri ve bunlar yer alır.  
  
|Ön ek|Ad Alanı|  
|------------|---------------|  
|s11|`http://schemas.xmlsoap.org/soap/envelope`|  
|s12|`http://www.w3.org/2003/05/soap-envelope`|  
|wsaAugust2004|`http://schemas.xmlsoap.org/ws/2004/08/addressing`|  
|wsa10|`http://www.w3.org/2005/08/addressing`|  
|sm|`http://schemas.microsoft.com/serviceModel/2004/05/xpathfunctions`|  
|tempuri|`http://tempuri.org`|  
|ser|`http://schemas.microsoft.com/2003/10/Serialization`|  
  
 XPath sorgularınızda belirli bir ad alanı kullanacağınızı bildiğinizde, özgün bir ad alanı önekiyle birlikte ad alanı tablosuna ekleyebilir ve önekini tam ad alanı yerine herhangi bir XPath sorgusunda kullanabilirsiniz. Aşağıdaki örnek, daha sonra filterData'da bulunan `"http://my.custom.namespace"`XPath sorgusunda kullanılan ad alanı için "özel" bir öneki tanımlar.  
  
```xml  
<namespaceTable>  
     <add prefix="custom" namespace="http://my.custom.namespace/"/>  
</namespaceTable>  
<filters>  
     <filter name="XPathFilter" filterType="XPath" filterData="/s12:Envelope/s12:Header/custom:RoundingCalculator = 1"/>  
</filters>  
```  
  
## <a name="filter-tables"></a>Filtre Tabloları  
 Her filtre öğesi iletiye uygulanabilecek mantıksal bir karşılaştırma tanımlasa da, filtre tablosu filtre öğesi ile hedef istemci bitiş noktası arasındaki ilişkilendirme sağlar. Filtre tablosu, bir filtre, birincil hedef bitiş noktası ve alternatif yedekleme uç noktaları nın listesi arasındaki ilişkilendirme tanımlayan adlandırılmış nesneler topluluğudur. <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement> Filtre tablosu girişleri, her filtre koşulu için isteğe bağlı bir öncelik belirtmenize de olanak sağlar. Aşağıdaki örnekte iki filtre tanımlanır ve sonra her filtreyi bir hedef bitiş noktasıyla ilişkilendiren bir filtre tablosu tanımlar.  
  
```xml  
<routing>  
     <filters>  
       <filter name="AddAction" filterType="Action" filterData="Add" />  
       <filter name="SubtractAction" filterType="Action" filterData="Subtract" />  
     </filters>  
     <filterTables>  
       <table name="routingTable1">  
         <filters>  
           <add filterName="AddAction" endpointName="Addition" />  
           <add filterName="SubtractAction" endpointName="Subtraction" />  
         </filters>  
       </table>  
     </filterTables>
</routing>  
```  
  
### <a name="filter-evaluation-priority"></a>Filtre Değerlendirme Önceliği  
 Varsayılan olarak, filtre tablosundaki tüm girişler aynı anda değerlendirilir ve değerlendirilen ileti her eşleşen filtre girişiyle ilişkili uç nokta(lar)a yönlendirilir. Birden çok filtre `true`yi değerlendiriyorsa ve ileti tek yönlü veya çift yönlüise, ileti tüm eşleşen filtreler için uç noktalarına çok noktaya yayınlanır. İstemciye yalnızca bir yanıt döndürülebileceğinden, istek-yanıt iletileri çok noktaya yayın olamaz.  
  
 Her filtre için öncelik düzeyleri belirtilerek daha karmaşık yönlendirme mantığı uygulanabilir; Yönlendirme Hizmeti, tüm filtreleri önce en yüksek öncelik düzeyinde değerlendirir. İleti bu düzeybir filtreyle eşleşiyorsa, daha düşük önceliğe ait filtreler işlenmez. Örneğin, gelen tek yönlü ileti ilk olarak 2 önceliğe sahip tüm filtrelere göre değerlendirilir. İleti bu öncelik düzeyindeki herhangi bir filtreyle eşleşmiyor, bu nedenle sonraki ileti 1 önceliğe sahip filtrelerle karşılaştırılır. İki öncelikli 1 filtresi iletiyle eşleşir ve tek yönlü bir ileti olduğundan her iki hedef uç noktaya da yönlendirilir.  Öncelik 1 filtreleri arasında bir eşleşme bulunduğundan, öncelik 0 filtresi değerlendirilmemiştir.  
  
> [!NOTE]
> Öncelik belirtilmemişse, 0 varsayılan önceliği kullanılır.  
  
 Aşağıdaki örnek, tabloda başvurulan filtreler için 2, 1 ve 0 önceliklerini belirten bir filtre tablosu tanımlar.  
  
```xml  
<filterTables>  
     <filterTable name="filterTable1">  
          <add filterName="XPathFilter" endpointName="roundingCalcEndpoint"
               priority="2"/>  
          <add filterName="EndpointNameFilter" endpointName="regularCalcEndpoint"
               priority="1"/>  
          <add filterName="PrefixAddressFilter" endpointName="roundingCalcEndpoint"
               priority="1"/>  
          <add filterName="MatchAllMessageFilter" endpointName="defaultCalcEndpoint"
               priority="0"/>  
     </filterTable>  
</filterTables>  
```  
  
 Önceki örnekte, bir ileti XPathFilter ile eşleşirse, ileti yuvarlamaCalcEndpoint'e yönlendirilir ve diğer tüm filtreler daha düşük önceliğe göre olduğundan tablodaki başka filtreler değerlendirilmez. Ancak, ileti XPathFilter ile eşleşmiyorsa, sonraki alt önceliğe ait tüm filtrelere göre değerlendirilir, EndpointNameFilter ve ÖnekAddressFilter.  
  
> [!NOTE]
> Mümkün olduğunda, öncelik değerlendirmesi performans düşüşüne neden olabileceğinden öncelik belirtmek yerine özel filtreler kullanın.  
  
### <a name="backup-lists"></a>Yedekleme Listeleri  
 Filtre tablosundaki her filtre isteğe bağlı olarak, bitiş noktalarının adlandırılmış bir koleksiyonu olan bir yedekleme listesi (<xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection>. Bu koleksiyon, <xref:System.ServiceModel.CommunicationException> <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement.EndpointName%2A>'de belirtilen birincil bitiş noktasına gönderildiğinde iletinin iletilecek uç noktaların sıralı bir listesini içerir. Aşağıdaki örnekte, iki uç nokta içeren "backupServiceEndpoints" adlı bir yedekleme listesi tanımlanır.  
  
```xml  
<filterTables>  
     <filterTable name="filterTable1">  
          <add filterName="MatchAllFilter1" endpointName="Destination" backupList="backupEndpointList"/>  
     </filterTable>  
</filterTables>  
<backupLists>  
     <backupList name="backupEndpointList">  
          <add endpointName="backupServiceQueue" />  
          <add endpointName="alternateServiceQueue" />  
     </backupList>  
</backupLists>  
```  
  
 Önceki örnekte, birincil bitiş noktası "Hedef" bir gönderme başarısız olursa, Yönlendirme Hizmeti listelenir sırayla her bitiş noktasına göndermeyi deneyecek, ilk backupServiceQueue gönderme ve daha sonra alternatifServiceQueue gönderme eğer backupServiceQueue'ye gönderme başarısız olur. Tüm yedekleme uç noktaları başarısız olursa, bir hata döndürülür.
