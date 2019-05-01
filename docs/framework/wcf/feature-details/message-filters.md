---
title: İleti Filtreleri
ms.date: 03/30/2017
helpviewer_keywords:
- routing [WCF], message filters
ms.assetid: cb33ba49-8b1f-4099-8acb-240404a46d9a
ms.openlocfilehash: fc4656a76894eb3a844bc9f2187847fd9eff0ffe
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61786005"
---
# <a name="message-filters"></a>İleti Filtreleri
İçerik tabanlı yönlendirme uygulamak için yönlendirme hizmeti kullanan <xref:System.ServiceModel.Dispatcher.MessageFilter> adresi, uç nokta adı ya da belirli bir XPath ifadesi gibi bir ileti belirli bölümlerini inceleyin uygulamaları. İleti filtreleri hiçbiri ile sağlanmışsa [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] ihtiyaçlarınızı karşılamak, temel yeni bir uygulama oluşturarak özel filtre oluşturabilir <xref:System.ServiceModel.Dispatcher.MessageFilter> sınıfı.  
  
 Yönlendirme hizmeti yapılandırırken, filtre öğelerini tanımlamanız gerekir (<xref:System.ServiceModel.Routing.Configuration.FilterElement> nesneleri) türünü açıklayan **MessageFilter** ve aramak için belirli bir dize değerleri gibi bir filtre oluşturmak için gerekli destek verileri için ileti içinde. Filtre öğesi oluşturarak yalnızca tek bir ileti filtreleri tanımladığını unutmayın; değerlendirmek ve filtreleme tablosu da tanımlamalısınız iletileri yönlendirmek için filtrelerini kullanma (<xref:System.ServiceModel.Routing.Configuration.FilterTableEntryCollection>).  
  
 Filtre tablosundaki her girişin bir filtre öğesi atıfta bulunan ve İleti Filtresi eşleşmesi durumunda bir ileti için yönlendirilir istemci uç noktasını belirtir. Filtre tablo girişleri de Yedekleme uç noktaları koleksiyonu belirlemenize olanak tanır (<xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection>), bir ileti için bir iletim hatası durumunda birincil uç noktasına gönderilirken aktarılmaz uç noktaları listesi tanımlar. Bu uç noktaları, başarılı olana kadar belirtilen sırayla denenir.  
  
## <a name="message-filters"></a>İleti Filtreleri  
 Yönlendirme hizmeti tarafından kullanılan ileti filtreleri SOAP eylemi veya adres veya iletinin gönderildiği adres ön eki için bir ileti gönderildi uç nokta adı değerlendirme gibi ortak ileti seçimi işlevselliği sağlar. Filtreler de birleştirilebileceği ile bir `AND` koşul böylece ileti iki filtrelerle eşleşen iletileri yalnızca bir uç noktasına iletilir. Ayrıca, kendi uygulaması oluşturarak özel filtreler oluşturabilirsiniz <xref:System.ServiceModel.Dispatcher.MessageFilter>.  
  
 Aşağıdaki tabloda <xref:System.ServiceModel.Routing.Configuration.FilterType> yönlendirme hizmeti ile özel ileti filtresi ve gerekli uygulayan sınıf kullanılan <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A> parametreleri.  
  
|Filtre türü|Açıklama|Filtre verileri anlama|Örnek filtresi|  
|------------------|-----------------|-------------------------|--------------------|  
|Eylem|Kullanan <xref:System.ServiceModel.Dispatcher.ActionMessageFilter> belirli bir eylemi içeren iletileri eşleşmesi için sınıf.|Temel filtre uygulamak için eylem.|\<Filtre adı "action1" filterType = "Action" filterData = = "http://namespace/contract/operation" / >|  
|EndpointAddress|Kullanan <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter> sınıfı ile <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter.IncludeHostNameInComparison%2A>  ==  `true` içeren belirli bir adresi iletileri eşleştirilecek.|Filtreleme (Kime üstbilgisinde) adresi.|\<Filtre adı "Adresi1" filterType = "EndpointAddress" filterData = = "http://host/vdir/s.svc/b" / >|  
|EndpointAddressPrefix|Kullanan <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> sınıfı ile <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter.IncludeHostNameInComparison%2A>  ==  `true` belirli adres ön eki içeren iletileri eşleştirilecek.|Eşleşen en uzun ön ek kullanımı üzerine filtre adresi.|\<filter name="prefix1" filterType="EndpointAddressPrefix" filterData="http://host/" />|  
|And|Kullanan <xref:System.ServiceModel.Dispatcher.StrictAndMessageFilter> döndürmeden önce her iki koşul her zaman değerlendirilir sınıfı.|filterData kullanılmaz; Bunun yerine Filtre1 ve Filtresi2 olması gereken karşılık gelen ileti filtreleri (Ayrıca tabloda) adlarını sahip **ve**ed birlikte.|\<filter name="and1" filterType="And" filter1="address1" filter2="action1" />|  
|Özel|Genişleten ve kullanıcı tanımlı bir tür <xref:System.ServiceModel.Dispatcher.MessageFilter> sınıfı ve bir dize alan bir oluşturucusu vardır.|CustomType öznitelik sınıfı oluşturmak için tam olarak nitelenmiş tür adıdır; Filtre veri filtresi oluştururken oluşturucuya geçirilecek dizedir.|\<Filtre adı "custom1" filterType = "Özel" customType="CustomAssembly.CustomMsgFilter, CustomAssembly =" filterData = "Özel veri" / >|  
|EndpointName|Kullanan <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> gelen üzerinde hizmet uç noktası adını temel iletileri eşleşmesi için sınıf.|Hizmet uç noktası adı örneğin: "serviceEndpoint1".  Bu, yönlendirme hizmeti üzerinde kullanıma sunulan uç noktalardan biri olmalıdır.|\<filter name="stock1" filterType="Endpoint" filterData="SvcEndpoint" />|  
|MatchAll|Kullanan <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> sınıfı. Bu filtre ile eşleşen tüm gelen iletileri.|filterData kullanılmaz. Bu filtre, her zaman tüm iletiler aynı olacaktır.|\<Filtre adı "matchAll1" filterType = = "MatchAll" / >|  
|XPath|Kullanan <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> ileti içinde belirli bir XPath sorguları eşleştirilecek sınıfı.|İletileri eşleştirme yapılırken kullanılacak XPath sorgusu.|\<filter name="XPath1" filterType="XPath" filterData="//ns:element" />|  
  
 Aşağıdaki örnek, XPath Uçnoktaadı ve PrefixEndpointAddress ileti filtreleri kullanan filtre girişler tanımlar. Bu örnek ayrıca RoundRobinFilter1 ve RoundRobinFilter2 girişleri için özel bir filtre kullanarak gösterir.  
  
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
>  Yalnızca bir filtreyi tanımlayan filtre karşı değerlendirilecek iletileri neden olmaz. Filtre ise bir filtre tabloya eklenmelidir yönlendirme hizmeti tarafından kullanıma sunulan hizmet uç noktası ile ilişkili.  
  
### <a name="namespace-table"></a>Namespace tablo  
 Bir XPath filtresi kullanırken, XPath sorgusu içeren filtre veri alanlarının kullanımı nedeniyle son derece büyük hale gelebilir. Bu sorunu gidermeyi yönlendirme hizmeti ad alanı tablosunu kullanarak kendi ad alanı öneklerini tanımlama yeteneği sağlar.  
  
 Ad alanı tablo oluşan bir koleksiyondur <xref:System.ServiceModel.Routing.Configuration.NamespaceElement> XPath içinde kullanılabilen ortak ad alanları için ad alanı öneklerini tanımlayan nesne. Ad alanı tabloda bulunan varsayılan ad alanları ve ad alanı öneklerini aşağıda verilmiştir.  
  
|Ön eki|Ad Alanı|  
|------------|---------------|  
|s11|`http://schemas.xmlsoap.org/soap/envelope`|  
|s12|`http://www.w3.org/2003/05/soap-envelope`|  
|wsaAugust2004|`http://schemas.xmlsoap.org/ws/2004/08/addressing`|  
|wsa10|`http://www.w3.org/2005/08/addressing`|  
|SM|`http://schemas.microsoft.com/serviceModel/2004/05/xpathfunctions`|  
|tempuri|`http://tempuri.org`|  
|Hiz|`http://schemas.microsoft.com/2003/10/Serialization`|  
  
 XPath sorgularınızdaki belirli bir ad alanı kullanarak bildiğinizde, bir benzersiz ad alanı öneki ile birlikte ad alanı tablo ekleyin ve herhangi bir XPath sorgusu yerine tam ad alanı önekini kullanın. Aşağıdaki örnek, ad alanı için "özel" öneki tanımlar `"http://my.custom.namespace"`, ardından kullanılan filterData içinde yer alan XPath sorgusu.  
  
```xml  
<namespaceTable>  
     <add prefix="custom" namespace="http://my.custom.namespace/"/>  
</namespaceTable>  
<filters>  
     <filter name="XPathFilter" filterType="XPath" filterData="/s12:Envelope/s12:Header/custom:RoundingCalculator = 1"/>  
</filters>  
```  
  
## <a name="filter-tables"></a>Filtre tabloları  
 İletiye uygulanacak bir mantıksal karşılaştırma her filtre öğe tanımlar, ancak filtre tabloda filtre öğesi ve hedef istemci uç noktası arasındaki ilişki gösterilmektedir. Bir filtre tablosu adlandırılmış bir koleksiyonudur <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement> yedekleme alternatif uç noktaları listesini bir filtre ve birincil hedef uç nokta arasındaki ilişkiyi tanımlayan nesne. Filtre tablo girişleri her filtre koşulu için isteğe bağlı bir öncelik belirtmenizi sağlar. Aşağıdaki örnek, iki filtre tanımlar ve sonra her bir filtrenin bir hedef uç nokta ile ilişkilendiren bir filtre tablo tanımlar.  
  
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
  
### <a name="filter-evaluation-priority"></a>Filtre değerlendirme önceliği  
 Varsayılan olarak, filtre tablodaki tüm girişleri eşzamanlı olarak değerlendirilir ve değerlendirilen ileti eşleşen her filtre girişle ilişkili uç noktalarına yönlendirilir. Birden çok filtre sonucunu verirse `true`ve tek yönlü veya çift yönlü iletiyi, ileti eşleşen tüm filtreleri için uç noktaya yayın. İstek-yanıt iletileri, yalnızca bir yanıtı istemciye döndürülen için çok noktaya yayın olamaz.  
  
 Daha karmaşık yönlendirme mantığı, her bir filtrenin öncelik düzeyleri belirterek uygulanabilir; Yönlendirme hizmeti, en yüksek öncelik düzeyinde tüm filtreleri ilk önce değerlendirir. Bir ileti bu düzeyi filtresi eşleşirse, daha düşük bir öncelik filtre işlenir. Örneğin, tek yönlü gelen ileti önceliği 2 olan tüm filtreleri karşı ilk olarak değerlendirilir. Bu nedenle sonraki ileti önceliği 1 ile filtrelere göre karşılaştırılır ileti bu öncelik düzeyinde herhangi bir filtre eşleşmiyor. İletinin iki öncelik 1 filtrelerle eşleşen ve tek yönlü bir ileti olduğu için her iki hedef Uç noktalara yönlendirilir.  Öncelik 1 filtreler arasında bir eşleşme bulunamadığından, öncelik 0 filtre değerlendirilir.  
  
> [!NOTE]
>  Eğer öncelik belirtilmezse, varsayılan öncelik 0 kullanılır.  
  
 Aşağıdaki örnekte, 2, 1 ve 0 başvurulan filtreleri için öncelikleri tablodaki belirten bir filtre tablo tanımlar.  
  
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
  
 Yukarıdaki örnekte, bir ileti XPathFilterElement eşleşirse, için roundingCalcEndpoint yönlendirilir ve diğer tüm filtreleri daha düşük bir öncelik olduğundan tabloda daha fazla filtre değerlendirilir. İleti XPathFilterElement eşleşmiyorsa ancak bunu daha sonra tüm filtreleri sonraki daha düşük öncelikli karşı EndpointNameFilter ve PrefixAddressFilter değerlendirilir.  
  
> [!NOTE]
>  Mümkün olduğunda, bir öncelik öncelik değerlendirme içinde performans düşüşü sağladığından belirtmek yerine özel filtreler kullanın.  
  
### <a name="backup-lists"></a>Yedekleme listeler  
 Filtre tablodaki her bir filtrenin isteğe bağlı olarak adlandırılmış uç noktaları koleksiyonudur yedek bir liste belirtin (<xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection>). Bu koleksiyon, sıralı bir ileti için durumunda aktarılmaz uç noktaları listesi içeren bir <xref:System.ServiceModel.CommunicationException> belirtilen birincil uç noktasına gönderilirken <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement.EndpointName%2A>. Aşağıdaki örnek, "iki uç nokta içeren backupServiceEndpoints" adlı bir yedekleme listesi tanımlar.  
  
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
  
 Birincil uç nokta "Hedef" gönderme başarısız olursa, önceki örnekte, yönlendirme hizmeti listelendikleri sırayla her bir uç noktaya gönderme, ilk backupServiceQueue için gönderme ve alternateServiceQueue için sonradan göndermeyi deneyecek backupServiceQueue gönderme başarısız olur. Tüm yedekleme uç noktalar başarısız olursa, bir hata döndürülür.
