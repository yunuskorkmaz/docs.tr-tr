---
description: 'Daha fazla bilgi için: Ileti filtreleri'
title: İleti Filtreleri
ms.date: 03/30/2017
helpviewer_keywords:
- routing [WCF], message filters
ms.assetid: cb33ba49-8b1f-4099-8acb-240404a46d9a
ms.openlocfilehash: 1b52b2b50dc94e79ba6960e834f601af18200f52
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99727071"
---
# <a name="message-filters"></a>İleti Filtreleri

İçerik tabanlı yönlendirme uygulamak için, yönlendirme hizmeti, <xref:System.ServiceModel.Dispatcher.MessageFilter> iletinin adresi, uç nokta adı veya belirli bir XPath ekstresi gibi belirli bölümlerini denetleyen uygulamalar kullanır. Gereksinimlerinizi karşılayacak şekilde sağlanmayan ileti filtrelerinden hiçbiri [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] , temel sınıfın yeni bir uygulamasını oluşturarak özel bir filtre oluşturabilirsiniz <xref:System.ServiceModel.Dispatcher.MessageFilter> .  
  
 Yönlendirme hizmetini yapılandırırken, <xref:System.ServiceModel.Routing.Configuration.FilterElement> ileti içinde aranacak özel dize değerleri gibi, **MessageFilter** türünü ve filtrenin oluşturulması için gereken tüm destekleyici verileri tanımlayan filtre öğelerini (nesneleri) tanımlamanız gerekir. Filtre öğelerinin oluşturulması yalnızca ayrı ileti filtrelerini tanımlar; iletileri değerlendirmek ve yönlendirmek için filtreleri kullanmak üzere bir filtre tablosu () tanımlamanız gerekir <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryCollection> .  
  
 Filtre tablosundaki her giriş bir filtre öğesine başvurur ve ileti filtreyle eşleşiyorsa iletinin yönlendirileceği istemci uç noktasını belirtir. Filtre tablosu girdileri Ayrıca <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection> , birincil uç noktaya gönderilirken bir iletim hatası olması durumunda iletinin iletibileceği bitiş noktaları listesini tanımlayan bir yedekleme uç noktası () koleksiyonu belirtmenize de olanak tanır. Bu uç noktalar, bir başarılı olana kadar belirtilen sırada denenir.  
  
## <a name="message-filters"></a>İleti Filtreleri  

 Yönlendirme hizmeti tarafından kullanılan ileti filtreleri, bir iletinin gönderildiği uç noktanın adını, SOAP eylemini veya iletinin gönderildiği adres ya da adres önekini değerlendirmek gibi ortak ileti seçimi işlevlerini sağlar. Filtreler aynı zamanda bir koşula dahil edilebilir `AND` , böylece ileti her iki filtreyle de eşleşiyorsa iletiler yalnızca bir uç noktaya yönlendirilir. Kendi uygulamanızı oluşturarak özel filtreler de oluşturabilirsiniz <xref:System.ServiceModel.Dispatcher.MessageFilter> .  
  
 Aşağıdaki tabloda <xref:System.ServiceModel.Routing.Configuration.FilterType> , yönlendirme hizmeti tarafından kullanılan, belirli ileti filtresi uygulayan sınıf ve gerekli <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A> parametreler listelenmektedir.  
  
|Filtre türü|Description|Veri filtreleme anlamı|Örnek filtre|  
|------------------|-----------------|-------------------------|--------------------|  
|Eylem|, <xref:System.ServiceModel.Dispatcher.ActionMessageFilter> Belirli bir eylemi içeren iletileri eşleştirmek için sınıfını kullanır.|Üzerine filtreleyecek eylem.|\<filter name="action1" filterType="Action" filterData="http://namespace/contract/operation" />|  
|EndpointAddress|<xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter>, <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter.IncludeHostNameInComparison%2A>  ==  `true` Belirli bir adresi içeren iletileri eşleştirmek için ile sınıfını kullanır.|Filtrelemeye yönelik adres (-üst bilgisinde).|\<filter name="address1" filterType="EndpointAddress" filterData="http://host/vdir/s.svc/b"  />|  
|EndpointAddressPrefix|<xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter>, <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter.IncludeHostNameInComparison%2A>  ==  `true` Belirli bir adres ön ekini içeren iletileri eşleştirmek için ile sınıfını kullanır.|En uzun ön ek eşleştirme kullanılarak filtrelenecek adres.|\<filter name="prefix1" filterType="EndpointAddressPrefix" filterData="http://host/" />|  
|And|, <xref:System.ServiceModel.Dispatcher.StrictAndMessageFilter> Döndürmeden önce her iki koşulu da değerlendiren sınıfını kullanır.|filterData kullanılmaz; Bunun yerine, filter1 ve filter2 karşılık gelen ileti filtrelerinin (aynı zamanda tablo içinde) adlarına sahiptir **ve** bu, birlikte olmalıdır.|\<filter name="and1" filterType="And" filter1="address1" filter2="action1" />|  
|Özel|<xref:System.ServiceModel.Dispatcher.MessageFilter>Sınıfını genişleten ve dize alan bir oluşturucuya sahip olan Kullanıcı tanımlı bir tür.|CustomType özniteliği, oluşturulacak sınıfın tam tür adıdır; filterData, filtre oluşturulurken oluşturucuya geçirilecek dizedir.|\<filter name="custom1" filterType="Custom" customType="CustomAssembly.CustomMsgFilter, CustomAssembly" filterData="Custom Data" />|  
|Uçnoktaadı|, <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> Gelen hizmet uç noktasının adına göre iletileri eşleştirmek için sınıfını kullanır.|Hizmet uç noktasının adı, örneğin: "serviceEndpoint1".  Bu, yönlendirme hizmetinde açığa çıkarılan uç noktalardan biri olmalıdır.|\<filter name="stock1" filterType="Endpoint" filterData="SvcEndpoint" />|  
|MatchAll|Sınıfını kullanır <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> . Bu filtre tüm gelen iletilerle eşleşir.|filterData kullanılmıyor. Bu filtre, her zaman tüm iletilerle eşleşir.|\<filter name="matchAll1" filterType="MatchAll" />|  
|XPath|<xref:System.ServiceModel.Dispatcher.XPathMessageFilter>İleti içindeki belirli XPath sorgularını eşleştirmek için sınıfını kullanır.|İletileri eşleştirirken kullanılacak XPath sorgusu.|\<filter name="XPath1" filterType="XPath" filterData="//ns:element" />|  
  
 Aşağıdaki örnek, XPath, EndpointName ve PrefixEndpointAddress ileti filtrelerini kullanan filtre girdilerini tanımlar. Bu örnek ayrıca RoundRobinFilter1 ve RoundRobinFilter2 girdileri için özel bir filtre kullanmayı da gösterir.  
  
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
> Yalnızca bir filtre tanımlamanız, iletilerin filtreye göre değerlendirilmemesine neden olmaz. Filtrenin bir filtre tablosuna eklenmesi gerekir, bu, daha sonra yönlendirme hizmeti tarafından açığa çıkarılan hizmet uç noktasıyla ilişkilendirilir.  
  
### <a name="namespace-table"></a>Ad alanı tablosu  

 XPath filtresi kullanılırken, XPath sorgusunu içeren filtre verileri, ad alanlarının kullanımı nedeniyle son derece büyük olabilir. Bu sorunu gidermek için yönlendirme hizmeti, ad alanı kullanarak kendi ad alanı öneklerinizi tanımlama yeteneği sağlar.  
  
 Ad alanı tablosu, <xref:System.ServiceModel.Routing.Configuration.NamespaceElement> bir XPath 'te kullanılabilen ortak ad alanları için ad alanı öneklerini tanımlayan bir nesne koleksiyonudur. Ad alanı tablosunda yer alan varsayılan ad alanları ve ad alanı önekleri aşağıda verilmiştir.  
  
|Ön ek|Ad Alanı|  
|------------|---------------|  
|s11|`http://schemas.xmlsoap.org/soap/envelope`|  
|S12|`http://www.w3.org/2003/05/soap-envelope`|  
|wsaAugust2004|`http://schemas.xmlsoap.org/ws/2004/08/addressing`|  
|wsa10|`http://www.w3.org/2005/08/addressing`|  
|sm|`http://schemas.microsoft.com/serviceModel/2004/05/xpathfunctions`|  
|tempuri|`http://tempuri.org`|  
|hiz|`http://schemas.microsoft.com/2003/10/Serialization`|  
  
 XPath sorgularınızda belirli bir ad alanı kullanacağınızı bildiğiniz zaman, benzersiz bir ad alanı önekiyle birlikte ad alanı tablosuna ekleyebilir ve öneki tam ad alanı yerine herhangi bir XPath sorgusunda kullanabilirsiniz. Aşağıdaki örnek, ad alanı için "Custom" önekini tanımlar `"http://my.custom.namespace"` , daha sonra filterData içinde bulunan XPath sorgusunda kullanılır.  
  
```xml  
<namespaceTable>  
     <add prefix="custom" namespace="http://my.custom.namespace/"/>  
</namespaceTable>  
<filters>  
     <filter name="XPathFilter" filterType="XPath" filterData="/s12:Envelope/s12:Header/custom:RoundingCalculator = 1"/>  
</filters>  
```  
  
## <a name="filter-tables"></a>Tabloları filtrele  

 Her filtre öğesi bir iletiye uygulanabilen bir mantıksal karşılaştırma tanımladığından, filtre tablosu filtre öğesi ile hedef istemci uç noktası arasındaki ilişkilendirmeyi sağlar. Filtre tablosu <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement> , bir filtre, birincil hedef uç noktası ve alternatif yedekleme bitiş noktaları listesi arasındaki ilişkiyi tanımlayan nesnelerin adlandırılmış bir koleksiyonudur. Filtre tablosu girdileri, her bir filtre koşulu için isteğe bağlı bir öncelik belirtmenize de olanak tanır. Aşağıdaki örnek iki filtre tanımlar ve ardından her bir filtreyi bir hedef uç noktasıyla ilişkilendiren bir filtre tablosu tanımlar.  
  
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
  
### <a name="filter-evaluation-priority"></a>Değerlendirme önceliğini filtrele  

 Varsayılan olarak, filtre tablosundaki tüm girişler eşzamanlı olarak değerlendirilir ve değerlendirilen ileti, eşleşen her filtre girdisiyle ilişkili uç noktalara yönlendirilir. Birden çok filtre değerlendirmesi yaptıysanız `true` ve ileti tek yönlü veya çift yönlü ise, ileti tüm eşleşen filtreler için uç noktalara çok noktaya yayın yapılır. İstemciye yalnızca bir yanıt döndürülemediğinden, istek-yanıt iletileri çok noktaya geçirilemez.  
  
 Her filtrenin öncelik düzeyleri belirtilerek daha karmaşık yönlendirme mantığı uygulanabilir; Yönlendirme hizmeti, ilk olarak tüm filtreleri en yüksek öncelik düzeyinde değerlendirir. Bir ileti bu düzeyin bir filtresiyle eşleşiyorsa, daha düşük önceliğe sahip hiçbir filtre işlenmez. Örneğin, gelen tek yönlü bir ileti, öncelikle 2 önceliğine sahip tüm filtrelere karşı değerlendirilir. İleti, bu öncelik düzeyindeki herhangi bir filtreyle eşleşmez, bu nedenle ileti önceliği 1 olan filtrelere göre karşılaştırılır. İki öncelik 1 filtresi iletiyle eşleşir ve tek yönlü bir ileti olduğundan, her iki hedef uç noktasına yönlendirilir.  Öncelik 1 filtreleri arasında bir eşleşme bulunduğundan, öncelik 0 filtresi değerlendirilmez.  
  
> [!NOTE]
> Hiçbir öncelik belirtilmemişse, varsayılan 0 önceliği kullanılır.  
  
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
  
 Yukarıdaki örnekte, bir ileti XPathFilter ile eşleşirse, bu, roundingCalcEndpoint 'e yönlendirilir ve diğer tüm filtreler daha düşük bir önceliğe sahip olduğundan tablodaki başka bir filtre değerlendirilmez. Ancak, ileti XPathFilter ile eşleşmezse, daha sonra bir sonraki düşük önceliğin, EndpointNameFilter ve PrefixAddressFilter tüm filtrelerine göre değerlendirilir.  
  
> [!NOTE]
> Mümkün olduğunda öncelikli bir öncelik belirtmek yerine özel filtreler kullanın, çünkü öncelik değerlendirmesi performans düşüşüne neden olabilir.  
  
### <a name="backup-lists"></a>Yedekleme listeleri  

 Filtre tablosundaki her bir filtre, isteğe bağlı olarak bir uç nokta () koleksiyonu olan bir yedekleme listesi belirtebilir <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection> . Bu koleksiyon, iletinin <xref:System.ServiceModel.CommunicationException> ' de belirtilen birincil uç noktaya gönderilirken bir olayında iletilebilecek uç noktaların sıralı bir listesini içerir <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement.EndpointName%2A> . Aşağıdaki örnek, iki uç nokta içeren "backupServiceEndpoints" adlı bir yedekleme listesini tanımlar.  
  
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
  
 Yukarıdaki örnekte, birincil uç noktaya gönder "hedef" başarısız olursa, yönlendirme hizmeti listelenen her bir uç noktaya, önce backupServiceQueue öğesine gönderilir ve ardından backupServiceQueue öğesine Gönder başarısız olursa alternateServiceQueue öğesine gönderilir. Tüm yedekleme uç noktaları başarısız olursa, bir hata döndürülür.
