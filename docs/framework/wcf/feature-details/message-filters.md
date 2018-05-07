---
title: İleti Filtreleri
ms.date: 03/30/2017
helpviewer_keywords:
- routing [WCF], message filters
ms.assetid: cb33ba49-8b1f-4099-8acb-240404a46d9a
ms.openlocfilehash: e129924de53fb0dba61798cc492729c8af69ed94
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="message-filters"></a>İleti Filtreleri
İçerik tabanlı yönlendirme uygulamak için yönlendirme hizmeti kullanan <xref:System.ServiceModel.Dispatcher.MessageFilter> adresi, uç nokta adı veya belirli bir XPath ifadesi gibi bir ileti belirli bölümlerine incelemek uygulamaları. İleti filtreleri hiçbiri ile sağladıysanız [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] ihtiyaçlarınızı karşılamak, yeni bir uygulama taban oluşturarak özel filtre oluşturabilirsiniz <xref:System.ServiceModel.Dispatcher.MessageFilter> sınıfı.  
  
 Yönlendirme hizmeti yapılandırırken, filtre öğeleri tanımlamanız gerekir (<xref:System.ServiceModel.Routing.Configuration.FilterElement> nesneler) türünü açıklayan **MessageFilter** ve aramak için belirli dize değerlerini gibi filtre oluşturmak için gerekli destek verileri için ileti içinde. Filtre öğeleri oluşturma yalnızca tek tek ileti filtreleri tanımladığını unutmayın; değerlendirmek ve filtreleme tablosu da tanımlamalısınız iletileri yönlendirmek için filtreleri kullanmak için (<xref:System.ServiceModel.Routing.Configuration.FilterTableEntryCollection>).  
  
 Filtre tablosundaki her girişin bir filtre öğesine başvuruyor ve İleti Filtresi eşleşirse bir ileti için yönlendirilmiş istemci uç nokta belirtir. Filtre tablosu girdileri ayrıca yedekleme uç noktaları koleksiyonu belirtmenize olanak verir (<xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection>), ileti için bir iletim hatası durumunda birincil uç noktasına gönderirken aktarılmaz bitiş noktaları listesini tanımlar. Bu uç noktalar, biri başarılı olana kadar belirtilen sırayla denenir.  
  
## <a name="message-filters"></a>İleti Filtreleri  
 Yönlendirme hizmeti tarafından kullanılan ileti filtreleri gibi bir ileti, SOAP eylemi veya adres veya iletinin gönderildiği adres ön eki gönderildiği uç noktanın adı değerlendirme ortak ileti seçimi işlevlerini sağlar. Filtreler de birleştirilebileceği ile bir `AND` koşul böylece ileti iki filtreleri eşleşirse iletileri yalnızca bir bitiş noktasına yönlendirilir. Ayrıca, kendi uyarlamasını oluşturarak özel filtreler oluşturabilirsiniz <xref:System.ServiceModel.Dispatcher.MessageFilter>.  
  
 Aşağıdaki tabloda <xref:System.ServiceModel.Routing.Configuration.FilterType> yönlendirme hizmeti tarafından belirli bir ileti filtresi ve gerekli uygulayan sınıfa kullanılan <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A> parametreleri.  
  
|Filtre türü|Açıklama|Filtre veri anlama|Örnek filtresi|  
|------------------|-----------------|-------------------------|--------------------|  
|Eylem|Kullanan <xref:System.ServiceModel.Dispatcher.ActionMessageFilter> belirli bir eylemi içeren iletileri eşleşecek şekilde sınıfı.|Üzerine filtre eylemi.|\<Filtre adı "action1" filterType = "Eylem" filterData = = "http://namespace/contract/operation" / >|  
|EndpointAddress|Kullanan <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter> sınıfı ile <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter.IncludeHostNameInComparison%2A>  ==  `true` belirli bir adresi içeren iletileri eşleşecek şekilde.|Bağlı (Kime üstbilgisinde) filtre adresi.|\<Filtre adı "Adresi1" filterType = "EndpointAddress" filterData = = "http://host/vdir/s.svc/b" / >|  
|EndpointAddressPrefix|Kullanan <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> sınıfı ile <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter.IncludeHostNameInComparison%2A>  ==  `true` belirli adres ön eki içeren iletileri eşleşecek şekilde.|En uzun önek eşleştirme kullanılarak üzerine filtre adresi.|\<filter name="prefix1" filterType="EndpointAddressPrefix" filterData="http://host/" />|  
|Ve|Kullanan <xref:System.ServiceModel.Dispatcher.StrictAndMessageFilter> koşulların her ikisi de döndürmeden önce her zaman değerlendirir sınıfı.|Filtre veri kullanılmaz; Bunun yerine filter1 ve Filtre2 olması gereken karşılık gelen ileti filtreleri (aynı zamanda tabloda) adlarını sahip **ve**ed birlikte.|\<filter name="and1" filterType="And" filter1="address1" filter2="action1" />|  
|Özel|Genişletir kullanıcı tanımlı bir tür <xref:System.ServiceModel.Dispatcher.MessageFilter> sınıfı ve bir dize alan bir oluşturucuya sahip.|Sınıf oluşturmak için tam olarak nitelenmiş tür adını customType özniteliktir; filterData filtre oluştururken oluşturucuya geçmesine dizesidir.|\<Filtre adı "custom1" filterType = "Özel" customType="CustomAssembly.CustomMsgFilter, CustomAssembly =" filterData = "Özel veri" / >|  
|EndpointName|Kullanan <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> bunlar gelen hizmet uç noktası adını temel iletileri eşleşecek şekilde sınıfı.|Hizmet uç noktası adı örneğin: "serviceEndpoint1".  Bu yönlendirme hizmette sunulan uç noktalardan biri olmalıdır.|\<filter name="stock1" filterType="Endpoint" filterData="SvcEndpoint" />|  
|MatchAll|Kullanan <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> sınıfı. Bu filtre ile eşleşen tüm gelen iletileri.|filterData kullanılmaz. Bu filtre, her zaman tüm iletileri ile eşleşir.|\<Filtre adı "matchAll1" filterType = = "MatchAll" / >|  
|XPath|Kullanan <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> belirli XPath sorguları iletideki eşleşecek şekilde sınıfı.|İletileri eşleştirme yapılırken kullanılacak XPath sorgusu.|\<filter name="XPath1" filterType="XPath" filterData="//ns:element" />|  
  
 Aşağıdaki örnek, XPath, EndpointName ve PrefixEndpointAddress ileti filtreleri kullanan filtre girişler tanımlar. Bu örnek ayrıca RoundRobinFilter1 ve RoundRobinFilter2 girişleri için özel bir filtre kullanarak gösterir.  
  
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
>  Yalnızca bir filtre tanımlama karşı filtreyi değerlendirilecek iletileri neden olmaz. Filtre ise bir filtre tabloya eklenmelidir yönlendirme hizmeti tarafından sunulan hizmet uç noktası ile ilişkili.  
  
### <a name="namespace-table"></a>Namespace tablosu  
 Bir XPath filtresi kullanırken, XPath sorgusu içeren filtre veri ad alanları kullanımı nedeniyle son derece büyük hale gelebilir. Bu sorunu gidermek için yönlendirme hizmeti ad alanı tablosunu kullanarak kendi ad alanı öneklerini tanımlama yeteneği sağlar.  
  
 Ad alanı tablo koleksiyonudur <xref:System.ServiceModel.Routing.Configuration.NamespaceElement> bir XPath kullanılabilir ortak ad alanları için ad alanı öneklerini tanımlar nesneleri. Ad alanı tabloda bulunan varsayılan ad alanları ve ad alanı önekleri verilmiştir.  
  
|önek|Ad Alanı|  
|------------|---------------|  
|s11|http://schemas.xmlsoap.org/soap/envelope|  
|s12|http://www.w3.org/2003/05/soap-envelope|  
|wsaAugust2004|http://schemas.xmlsoap.org/ws/2004/08/addressing|  
|wsa10|http://www.w3.org/2005/08/addressing|  
|SM|http://schemas.microsoft.com/serviceModel/2004/05/xpathfunctions|  
|tempuri|http://tempuri.org|  
|Ser|http://schemas.microsoft.com/2003/10/Serialization|  
  
 XPath sorgularınızda belirli bir ad kullanarak bildiğiniz durumlarda bir benzersiz ad alanı öneki ile birlikte ad alanı tabloya ekleyin ve herhangi bir XPath sorgusu yerine tam ad alanı önekini kullanın. Aşağıdaki örnek, ad alanı için "özel" öneki tanımlar "http://my.custom.namespace", ardından kullanılan filterData içinde yer alan XPath sorgusunda.  
  
```xml  
<namespaceTable>  
     <add prefix="custom" namespace="http://my.custom.namespace/"/>  
</namespaceTable>  
<filters>  
     <filter name="XPathFilter" filterType="XPath" filterData="/s12:Envelope/s12:Header/custom:RoundingCalculator = 1"/>  
</filters>  
```  
  
## <a name="filter-tables"></a>Filtre tabloları  
 Her filtre öğesi için bir ileti uygulanabilir mantıksal bir karşılaştırma açıklarken Filtresi tablosu filtre öğesi ve hedef istemci uç arasındaki ilişkiyi sağlar. Bir filtre tablosu adlandırılmış bir koleksiyonudur <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement> bir filtre, bir birincil hedef uç noktası ve alternatif yedekleme bitiş noktaları listesini arasındaki ilişkiyi tanımlayan nesneleri. Filtre tablosu girdileri de her bir filtre koşulu için isteğe bağlı bir öncelik belirtmenizi sağlar. Aşağıdaki örnekte, iki filtre tanımlar ve her bir filtre hedef uç nokta ile ilişkilendiren bir filtre tablo tanımlar.  
  
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
  
### <a name="filter-evaluation-priority"></a>Filtre değerlendirmesi önceliği  
 Varsayılan olarak, filtre tablosundaki tüm girişleri eşzamanlı olarak değerlendirilir ve değerlendirilen iletinin her eşleşen filtre girişle ilişkili uç yönlendirilir. İçin birden çok filtre değerlendirin varsa `true`ve ileti tek yönlü veya çift yönlü, ileti eşleşen tüm filtreleri için uç noktalar için çok noktaya yayın. Yalnızca bir yanıt istemciye döndürülebilecek olduğundan istek-yanıt iletileri çok noktaya yayın olamaz.  
  
 Daha karmaşık yönlendirme mantığı, her bir filtrenin öncelik düzeyleri belirterek uygulanabilir; Yönlendirme hizmeti en yüksek öncelik düzeyindeki tüm filtreleri ilk önce değerlendirir. Bir ileti bu düzey filtresi eşleşirse, daha düşük bir öncelik hiçbir filtre işlenir. Örneğin, gelen tek yönlü ileti 2'in önceliği olan tüm filtreleri karşı ilk olarak değerlendirilir. İleti bu öncelik düzeyindeki herhangi bir filtre nedenle sonraki iletiyi filtreleriyle önceliği 1 ile karşılaştırılır eşleşmiyor. İleti iki öncelik 1 filtrelerle eşleşen ve tek yönlü bir ileti olduğu için her iki hedef Uç noktalara yönlendirilir.  Öncelik 1 filtreler arasında bir eşleşme bulunamadığından hiçbir filtre öncelik 0 değerlendirilir.  
  
> [!NOTE]
>  Öncelik belirtilmezse, varsayılan öncelik 0 kullanılır.  
  
 Aşağıdaki örnek, 2, 1 ve 0 başvurulan filtreler önceliklerini tablodaki belirtir bir filtre tablo tanımlar.  
  
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
  
 Önceki örnekte, bir ileti XPathFilterElement eşleşirse, roundingCalcEndpoint yönlendirilir ve diğer tüm filtreleri daha düşük bir öncelikte olduğundan tablodaki başka hiçbir filtre değerlendirilir. İleti XPathFilterElement eşleşmiyorsa ancak, bunu daha sonra tüm filtreleri sonraki daha düşük öncelikli karşı EndpointNameFilter ve PrefixAddressFilter değerlendirilir.  
  
> [!NOTE]
>  Mümkün olduğunda, öncelik değerlendirme performans düşüşüne neden olabileceğinden bir öncelik belirtmek yerine özel filtreleri kullanın.  
  
### <a name="backup-lists"></a>Yedekleme listeler  
 Filtre tablodaki her bir filtre isteğe bağlı olarak adlandırılmış uç noktaları koleksiyonudur yedek liste belirtebilirsiniz (<xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection>). Bu koleksiyon ileti için durumunda aktarılmaz uç noktaları sıralı bir listesini içeren bir <xref:System.ServiceModel.CommunicationException> belirtilen birincil uç gönderirken <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement.EndpointName%2A>. Aşağıdaki örnek, "iki uç nokta içeren backupServiceEndpoints" adlı bir yedekleme listesini tanımlar.  
  
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
  
 Birincil uç "Hedef" gönderme başarısız olursa, önceki örnekte, yönlendirme hizmeti listelenmiştir dizisindeki her bitiş gönderme, ilk backupServiceQueue için gönderme ve alternateServiceQueue için daha sonra göndermeyi deneyecek backupServiceQueue gönderme başarısız olur. Tüm yedekleme uç noktaları başarısız olursa bir hata döndürülür.
