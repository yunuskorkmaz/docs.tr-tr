---
title: Yönlendirme Tanıtımı
ms.date: 03/30/2017
ms.assetid: bf6ceb38-6622-433b-9ee7-f79bc93497a1
ms.openlocfilehash: 3ee7ea8271df47354a0897434bf8f203eaf09a51
ms.sourcegitcommit: e8dc507cfdaad504fc9d4c83d28d24569dcef91c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2018
ms.locfileid: "33496870"
---
# <a name="routing-introduction"></a>Yönlendirme Tanıtımı
Yönlendirme hizmeti, yönlendirme iletilerinin ileti içeriğine göre yeteneğine sahip bir genel takılabilir SOAP aracı sağlar. Yönlendirme hizmeti ile hizmet toplama, hizmet sürümü oluşturma, öncelikli Yönlendirme ve çok noktaya yayın yönlendirme gibi senaryolara olanak tanır ve yönlendirme karmaşık mantık oluşturabilirsiniz. Yönlendirme hizmeti, hata, işleme sağlar ve birincil hedef uç noktasına gönderilirken bir hata oluşması durumunda iletilerin gönderildiği listelerini yedekleme uç nokta ayarlamak de sağlar.  
  
 Bu konu için yönlendirme hizmeti için yeni yöneliktir ve temel yapılandırma ve yönlendirme hizmeti, barındırma kapsar.  
  
## <a name="configuration"></a>Yapılandırma  
 Yönlendirme hizmeti, istemci uygulamalarından iletileri almak ve bir veya daha fazla hedef uç noktaları için iletileri yönlendirmek bir veya daha fazla hizmet uç noktayı kullanıma sokan bir WCF hizmeti olarak uygulanır. Hizmeti sağlayan bir <xref:System.ServiceModel.Routing.RoutingBehavior>, hizmet tarafından sunulan hizmet uç noktalarına uygulanır. Bu davranış, hizmetin nasıl çalıştığı çeşitli yönlerini yapılandırmak için kullanılır. Bir yapılandırma dosyası kullanarak yapılandırma kolaylığı için parametreleri üzerinde belirtilen **RoutingBehavior**. Kod tabanlı senaryolarda bu parametreleri bir parçası olarak belirtilecek bir <xref:System.ServiceModel.Routing.RoutingConfiguration> ardından geçirilebilir nesnesi bir **RoutingBehavior**.  
  
 Başlatma sırasında bu davranışı ekler <xref:System.ServiceModel.Routing.SoapProcessingBehavior>, istemci uç noktalarına iletilerin SOAP işleme gerçekleştirmek için kullanılır. Farklı bir gerektiren uç noktalarına ileti aktarmaya yönlendirme hizmeti böylece **MessageVersion** daha uç nokta üzerinden ileti alındı. **RoutingBehavior** de bir hizmet uzantısı kaydeder <xref:System.ServiceModel.Routing.RoutingExtension>, çalışma zamanında yönlendirme hizmeti yapılandırmasını değiştirmek için bir erişilebilirlik noktası sağlar.  
  
 **RoutingConfiguration** sınıfı, yapılandırma ve yönlendirme hizmeti yapılandırmasını güncelleştirmek için tutarlı bir yol sağlar.  Yönlendirme hizmeti ayarlarını görür ve yapılandırmak için kullanılan parametreleri içeren **RoutingBehavior** hizmet yeniden başlatıldığında veya geçirilir **RoutingExtension** yönlendirme değiştirmek için Çalışma zamanında yapılandırması.  
  
 İçerik tabanlı yönlendirme iletilerinin gerçekleştirmek için kullanılan yönlendirme mantığı birden çok gruplandırma tarafından tanımlanan <xref:System.ServiceModel.Dispatcher.MessageFilter> nesneleri ile birlikte filtre tablolar (<xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> nesneleri). Gelen iletileri filtre tabloda ve her ileti filtreleri karşı değerlendirilir **MessageFilter** iletinin bir hedef uç noktasına iletilen eşleşir. İletileri yönlendirmek için kullanılan filtre tabloyu kullanarak belirtilen **RoutingBehavior** yapılandırma veya kod kullanarak **RoutingConfiguration** nesne.  
  
### <a name="defining-endpoints"></a>Uç noktaları tanımlama  
 Kullanacağınız yönlendirme mantığı tanımlayarak yapılandırmanızı başlaması gerektiğini görünebilir, ancak ilk adımınız yönlendirme iletileri olacaktır uç noktaları şeklini belirlemek için gerçekten olmalıdır. Yönlendirme hizmeti almak ve göndermek için kullanılan kanalları şeklini tanımlayan sözleşme kullanır ve bu nedenle Giriş kanalı şeklini çıkış kanalının eşleşmelidir.  İstek-yanıt kanal şekli kullanan uç noktaları için yönlendirdiğinden, örneğin, ardından uyumlu bir sözleşme gelen uç noktalar gibi kullanmalısınız <xref:System.ServiceModel.Routing.IRequestReplyRouter>.  
  
 Başka bir deyişle, hedef uç noktaları (örneğin, tek yönlü ve çift yönlü işlemleri karıştırma) birden çok kimlik doğrulaması desenleri ile sözleşmeler kullanırsanız, bu bildirimleri alabilen ve bunların tümüne iletileri yönlendirmek bir tek hizmet uç noktası oluşturulamıyor. Hangi uç noktaları uyumlu şekilleri sahip ve hedef Uç noktalara yönlendirilmesi için iletileri almak için kullanılacak bir veya daha fazla hizmet uç noktaları tanımlamak belirlemeniz gerekir.  
  
> [!NOTE]
>  Belirtin (örneğin, tek yönlü ve çift yönlü işlemlerin bir karışımı) birden çok desenleri sözleşmeleri ile çalışırken, geçici bir çözüm çift yönlü sözleşme yönlendirme hizmeti gibi kullanmaktır <xref:System.ServiceModel.Routing.IDuplexSessionRouter>. Ancak bu bağlama için tüm senaryoları mümkün olmayabilir çift yönlü iletişim özellikli olması gerektiği anlamına gelir. Bu mümkün olduğu senaryolarda yazışmaya birden fazla uç nokta hesaba katacak şekilde veya uygulamayı değiştirmek gerekli olabilir.  
  
 Sözleşmeleri yönlendirme hakkında daha fazla bilgi için bkz: [sözleşmeleri yönlendirme](../../../../docs/framework/wcf/feature-details/routing-contracts.md).  
  
 Hizmet uç noktası tanımlandıktan sonra kullanabileceğiniz **RoutingBehavior** belirli bir ilişkilendirilecek **RoutingConfiguration** uç nokta ile. Yönlendirme hizmeti bir yapılandırma dosyası kullanarak yapılandırırken **RoutingBehavior** Bu uç noktada alınan iletileri işlemek için kullanılan yönlendirme mantığı içeren filtre tablo belirtmek için kullanılır. Yönlendirme hizmeti programlı bir şekilde yapılandırıyorsanız kullanarak filtreleme tablosu belirtebilirsiniz **RoutingConfiguration**.  
  
 Aşağıdaki örnek, programlı ve bir yapılandırma dosyası kullanarak yönlendirme hizmeti tarafından kullanılan hizmet ve istemci uç noktalarını tanımlar.  
  
```xml  
    <services>  
      <!--ROUTING SERVICE -->  
      <service behaviorConfiguration="routingData"  
               name="System.ServiceModel.Routing.RoutingService">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost:8000/routingservice/router"/>  
          </baseAddresses>  
        </host>  
        <!-- Define the service endpoints that are receive messages -->  
        <endpoint address=""  
                  binding="wsHttpBinding"  
                  name="reqReplyEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />      
      </service>  
    </services>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="routingData">  
          <serviceMetadata httpGetEnabled="True"/>  
          <!-- Add the RoutingBehavior and specify the Routing Table to use -->  
          <routing filterTableName="routingTable1" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <client>  
    <!-- Define the client endpoint(s) to route messages to -->  
      <endpoint name="CalculatorService"  
                address="http://localhost:8000/servicemodelsamples/service"  
                binding="wsHttpBinding" contract="*" />  
    </client>  
```  
  
```csharp  
//set up some communication defaults  
string clientAddress = "http://localhost:8000/servicemodelsamples/service";  
string routerAddress = "http://localhost:8000/routingservice/router";  
Binding routerBinding = new WSHttpBinding();  
Binding clientBinding = new WSHttpBinding();  
//add the endpoint the router uses to receive messages  
serviceHost.AddServiceEndpoint(  
     typeof(IRequestReplyRouter),   
     routerBinding,   
     routerAddress);  
//create the client endpoint the router routes messages to  
ContractDescription contract = ContractDescription.GetContract(  
     typeof(IRequestReplyRouter));  
ServiceEndpoint client = new ServiceEndpoint(  
     contract,   
     clientBinding,   
     new EndpointAddress(clientAddress));  
//create a new routing configuration object  
RoutingConfiguration rc = new RoutingConfiguration();  
….  
rc.FilterTable.Add(new MatchAllMessageFilter(), endpointList);  
//attach the behavior to the service host  
serviceHost.Description.Behaviors.Add(  
     new RoutingBehavior(rc));  
```  
  
 Bu örnek bir adresi olan tek bir uç nokta kullanıma sunmak için yönlendirme hizmetini yapılandırır. "http://localhost:8000/routingservice/router", yönlendirilmesini iletileri almak için kullanılır. Hizmet uç noktası kullanır, iletileri istek-yanıt Uç noktalara yönlendirilir çünkü <xref:System.ServiceModel.Routing.IRequestReplyRouter> sözleşme. Bu yapılandırma bir tek istemcisi bitiş noktasının da tanımlar. "http://localhost:8000/servicemodelsample/service" iletileri için yönlendirilir. "RoutingTable1" adlı (gösterilmemiştir) filtre tablo iletileri yönlendirmek için kullanılan yönlendirme mantığı içerir ve hizmet uç noktası ile ilişkili olup'ı kullanarak **RoutingBehavior** (için bir yapılandırma dosyası) veya  **RoutingConfiguration** (için program yapılandırması).  
  
### <a name="routing-logic"></a>Yönlendirme mantığı  
 İletileri yönlendirmek için kullanılan yönlendirme mantığı tanımlamak için hangi gelen iletileri içinde bulunan verileri belirlemeniz gerekir bağlı benzersiz olarak eylem gerçekleştirilmesi. İleti içinde yer alan eylem değerini aynı SOAP eylemleri paylaşmak için yönlendirme tüm hedef uç noktaları değilse, iyi bir göstergesi gibi belirli hangi uç noktaya, ileti için yönlendirileceğini. İletileri belirli bir uç nokta için benzersiz bir şekilde yönlendirmek gerekir, ileti yönlendirilir hedef uç nokta benzersiz olarak tanımlayan veri üzerine filtre.  
  
 Yönlendirme hizmeti birkaç sağlayan **MessageFilter** adresi, eylem, uç nokta adı veya hatta bir XPath sorgusu gibi ileti içindeki belirli değerleri inceleyin uygulamaları. Bu uygulamaların hiçbiri gereksinimlerinizi karşılamıyorsa, özel bir oluşturabilirsiniz **MessageFilter** uygulaması. İleti filtreleri ve yönlendirme hizmeti tarafından kullanılan uygulamaları karşılaştırması hakkında daha fazla bilgi için bkz. [ileti filtreleri](../../../../docs/framework/wcf/feature-details/message-filters.md) ve [filtre seçme](../../../../docs/framework/wcf/feature-details/choosing-a-filter.md).  
  
 Birden çok ileti filtreleri birlikte her ilişkilendirmeniz filtre tablolarına düzenlenir **MessageFilter** hedef uç noktası ile. İsteğe bağlı olarak, filtre tablosunda yönlendirme hizmeti için bir iletim hatası durumunda ileti göndermeye çalışır yedekleme uç noktalarının bir listesini belirtmek için de kullanılabilir.  
  
 Varsayılan olarak tüm ileti filtreleri filtreleme tablosu içinde eşzamanlı olarak değerlendirilir; Ancak, belirtebileceğiniz bir <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement.Priority%2A> belirli bir sırada değerlendirilecek ileti filtreleri neden olur. En yüksek önceliğe sahip tüm girişleri ilk olarak değerlendirilir ve daha yüksek bir öncelik düzeyinde bir eşleşme bulunursa ileti filtreleri daha düşük önceliklerin değerlendirilmez. Filtre tabloları hakkında daha fazla bilgi için bkz. [ileti filtreleri](../../../../docs/framework/wcf/feature-details/message-filters.md).  
  
 Aşağıdaki örneklerde <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter>, hangi değerlendirilen `true` tüm iletiler için. Bu **MessageFilter** ilişkilendirir "routingTable1" filtre tablosuna ekleneceğinden **MessageFilter** "CalculatorService" adlı istemci uç noktası ile. **RoutingBehavior** ardından bu tablo Hizmeti uç noktası tarafından işlenen iletileri yönlendirmek için kullanılması gerektiğini belirtir.  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="routingData">  
      <serviceMetadata httpGetEnabled="True"/>  
      <!-- Add the RoutingBehavior and specify the Routing Table to use -->  
      <routing filterTableName="routingTable1" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
<!--ROUTING SECTION -->  
<routing>  
  <filters>  
    <filter name="MatchAllFilter1" filterType="MatchAll" />  
  </filters>  
  <filterTables>  
    <table name="routingTable1">  
      <filters>  
        <add filterName="MatchAllFilter1" endpointName="CalculatorService" />  
      </filters>  
    </table>  
  </filterTables>  
</routing>  
```  
  
```csharp  
//create a new routing configuration object  
RoutingConfiguration rc = new RoutingConfiguration();  
//create the endpoint list that contains the endpoints to route to  
//in this case we have only one  
List<ServiceEndpoint> endpointList = new List<ServiceEndpoint>();  
endpointList.Add(client);  
//add a MatchAll filter to the Router's filter table  
//map it to the endpoint list defined earlier  
//when a message matches this filter, it is sent to the endpoint contained in the list  
rc.FilterTable.Add(new MatchAllMessageFilter(), endpointList);  
```  
  
> [!NOTE]
>  Varsayılan olarak, yönlendirme hizmeti, yalnızca ileti üstbilgileri değerlendirir. İleti gövdesi erişmek için filtreleri izin vermek için ayarlamanız gerekir <xref:System.ServiceModel.Routing.RoutingConfiguration.RouteOnHeadersOnly%2A> için `false`.  
  
 **Çok noktaya yayın**  
  
 Birçok yönlendirme hizmeti yapılandırması için belirli tek bir uç nokta iletileri yönlendiren özel filtre mantığı kullanırken, belirli bir ileti birden çok hedef Uç noktalara yönlendirmek gerekebilir. Çok noktaya yayın için birden fazla hedefe bir ileti, aşağıdaki koşulların doğru olması gerekir:  
  
-   Kanal şekli istek-yanıt olmamalıdır (ancak tek yönlü veya çift yönlü olabilir) çünkü isteğine yanıt olarak istemci uygulaması tarafından yalnızca bir yanıt aldı.  
  
-   Birden çok filtre döndürmelidir `true` ileti değerlendirirken.  
  
 Bu koşullar karşılanıyorsa, ileti değerlendirmek için tüm filtre tüm uç noktalara yönlendirilir `true`. Aşağıdaki örnek, uç nokta adresini iletisi ise iki uç noktalara yönlendirilmek iletilerinde sonuçları bir yönlendirme yapılandırması tanımlar http://localhost:8000/routingservice/router/rounding.  
  
```xml  
<!--ROUTING SECTION -->  
<routing>  
  <filters>  
    <filter name="MatchAllFilter1" filterType="MatchAll" />  
    <filter name="RoundingFilter1" filterType="EndpointAddress"  
            filterData="http://localhost:8000/routingservice/router/rounding" />  
  </filters>  
  <filterTables>  
    <table name="routingTable1">  
      <filters>  
        <add filterName="MatchAllFilter1" endpointName="CalculatorService" />  
        <add filterName="RoundingFilter1" endpointName="RoundingCalcService" />  
      </filters>  
    </table>  
  </filterTables>  
</routing>  
```  
  
```csharp  
rc.FilterTable.Add(new MatchAllMessageFilter(), calculatorEndpointList);  
rc.FilterTable.Add(new EndpointAddressMessageFilter(new EndpointAddress(  
    "http://localhost:8000/routingservice/router/rounding")),  
    roundingCalcEndpointList);  
```  
  
### <a name="soap-processing"></a>SOAP işleme  
 Benzer olmayan protokolleri arasında iletileri yönlendirme desteklemek için **RoutingBehavior** varsayılan ekler <xref:System.ServiceModel.Routing.SoapProcessingBehavior> iletileri yönlendirilir tüm istemci uç noktası için. Bu davranışı otomatik olarak yeni bir oluşturur **MessageVersion** bir uyumlu oluşturma yanı sıra ileti uç noktaya yönlendirme önce **MessageVersion** için döndürmeden önce herhangi bir yanıt belge için istekte bulunan istemci uygulaması.  
  
 Yeni bir oluşturmak için izlenen adımların **MessageVersion** için giden ileti şu şekildedir:  
  
 **İstek işleme**  
  
-   Alma **MessageVersion** giden bağlama/kanal.  
  
-   Gövde Okuyucu için özgün iletisi görüntüleniyor.  
  
-   Aynı eylemi, gövde okuyucu ve yeni bir yeni bir ileti oluşturma **MessageVersion**.  
  
-   Varsa <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> ! = **Addressing.None**, Kime FaultTo, kopyalama ve yeni iletisi RelatesTo üst bilgi.  
  
-   Tüm ileti özelliklerini yeni iletinin kopyalayın.  
  
-   Yanıtı işlerken kullanılacak özgün istek iletisi Store.  
  
-   Yeni İstek iletisi döndürür.  
  
 **Yanıt işleme**  
  
-   Alma **MessageVersion** özgün istek iletisi.  
  
-   Gövde Okuyucu için alınan yanıt iletisi alın.  
  
-   Yeni bir yanıt iletisi gövdesi okuyucu aynı eylemi oluşturun ve **MessageVersion** özgün istek iletisi.  
  
-   Varsa <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> ! = **Addressing.None**, Kime FaultTo, kopyalama ve yeni iletisi RelatesTo üst bilgi.  
  
-   Yeni ileti için ileti özelliklerinde kopyalayın.  
  
-   Yeni bir yanıt iletisi döndürür.  
  
 Varsayılan olarak, **SoapProcessingBehavior** istemci uç noktaları tarafından otomatik olarak eklenir <xref:System.ServiceModel.Routing.RoutingBehavior> hizmet başladığında; ancak, SOAP işleme kullanarak tüm istemci uç noktaları için eklenen olup olmadığını kontrol edebilirsiniz <xref:System.ServiceModel.Routing.RoutingConfiguration.SoapProcessingEnabled%2A> özelliği. Ayrıca doğrudan belirli bir uç davranışı eklemek ve da etkinleştirebilir veya SOAP işleme daha ayrıntılı bir denetim gerekiyorsa uç nokta düzeyinde bu davranışı devre dışı.  
  
> [!NOTE]
>  SOAP işleme özgün istek iletisi ait olandan farklı bir MessageVersion gerektiren bir uç nokta için devre dışı bırakılırsa, iletiyi göndermeden önce gerekli olan herhangi bir SOAP değişiklik gerçekleştirmek için özel bir mekanizma sağlamanız gerekir Hedef uç nokta.  
  
 Aşağıdaki örneklerde, **soapProcessingEnabled** önlemek için kullanılan özellik **SoapProcessingBehavior** için tüm istemci uç noktalarını otomatik olarak eklenmesini.  
  
```xml  
<behaviors>  
  <!--default routing service behavior definition-->  
  <serviceBehaviors>  
    <behavior name="routingConfiguration">  
      <routing filterTableName="filterTable1" soapProcessingEnabled="false"/>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
```csharp  
//create the default RoutingConfiguration  
RoutingConfiguration rc = new RoutingConfiguration();  
rc.SoapProcessingEnabled = false;  
```  
  
### <a name="dynamic-configuration"></a>Dinamik yapılandırma  
 Ek istemci uç noktalarını eklemek veya iletileri yönlendirmek için kullanılan filtreler değiştirmeniz gerekir, şu anda aracılığıyla iletileri alma uç noktaları için hizmet kesilmesini önlemek için dinamik olarak çalışma zamanında yapılandırmasını güncelleştirmek için bir yol olmalıdır. Yönlendirme hizmeti. Her iki yöntem hiçbir ileti şu anda geçiş ve olası kaybı için kapalı kalma süresiyle için sunulmasını uygulamasını geri dönüşüme gerektiğinden bir yapılandırma dosyası veya ana bilgisayar uygulaması kodunu değiştirerek her zaman yeterli değildir hizmetin yeniden başlatılması bekliyor.  
  
 Yalnızca değiştirebileceğiniz **RoutingConfiguration** programlı olarak. Başlangıçta, bir yapılandırma dosyası kullanarak hizmet yapılandırabilirsiniz; ancak, yalnızca çalışma zamanında yapılandırmanın yeni bir oluşturarak değiştirebilirsiniz **RoutingConfigution** ve parametre olarak geçirerek <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> yöntemi tarafından kullanıma sunulan <xref:System.ServiceModel.Routing.RoutingExtension> hizmet uzantısı. Şu anda yoldaki tüm iletileri çağrısından sonra alınan iletilerin çalışırken önceki yapılandırmayı kullanarak yönlendirilmesini devam **ApplyConfiguration** yeni yapılandırmayı kullanın. Aşağıdaki örnek, yönlendirme hizmeti örneği oluşturma ve daha sonra yapılandırmayı değiştirme gösterir.  
  
```csharp  
RoutingConfiguration routingConfig = new RoutingConfiguration();  
routingConfig.RouteOnHeadersOnly = true;  
routingConfig.FilterTable.Add(new MatchAllMessageFilter(), endpointList);  
RoutingBehavior routing = new RoutingBehavior(routingConfig);  
routerHost.Description.Behaviors.Add(routing);  
routerHost.Open();  
// Construct a new RoutingConfiguration  
RoutingConfiguration rc2 = new RoutingConfiguration();  
ServiceEndpoint clientEndpoint = new ServiceEndpoint();  
ServiceEndpoint clientEndpoint2 = new ServiceEndpoint();  
// Add filters to the FilterTable in the new configuration  
rc2.FilterTable.add(new MatchAllMessageFilter(),  
       new List<ServiceEndpoint>() { clientEndpoint });  
rc2.FilterTable.add(new MatchAllMessageFilter(),  
       new List<ServiceEndpoint>() { clientEndpoint2 });  
rc2.RouteOnHeadersOnly = false;  
// Apply the new configuration to the Routing Service hosted in  
routerHost.routerHost.Extensions.Find<RoutingExtension>().ApplyConfiguration(rc2);  
```  
  
> [!NOTE]
>  Bu şekilde yönlendirme hizmetini güncelleştirirken yalnızca yeni bir yapılandırma geçişi mümkündür. Yalnızca seçilen öğelerin geçerli yapılandırmasını değiştirmek ya da yeni girişler geçerli yapılandırmasına eklemek mümkün değildir; oluşturur ve var olan bir yerini alan yeni bir yapılandırma geçişi.  
  
> [!NOTE]
>  Önceki yapılandırmayı kullanarak açılan tüm oturumları, önceki yapılandırmayı'ı kullanmaya devam edin. Yeni yapılandırma, yalnızca yeni oturumlar tarafından kullanılır.  
  
## <a name="error-handling"></a>Hata İşleme  
 Varsa <xref:System.ServiceModel.CommunicationException> hata gerçekleştiğinde işleme bir ileti göndermeye çalışırken hatayla karşılaştı. Bu özel durumlar genellikle gibi tanımlı istemci uç noktası ile iletişim kurmaya çalışılırken bir sorunla karşılaşıldı gösterir bir <xref:System.ServiceModel.EndpointNotFoundException>, <xref:System.ServiceModel.ServerTooBusyException>, veya <xref:System.ServiceModel.CommunicationObjectFaultedException>. Hata işleme kodu ayrıca catch ve ne zaman göndermeyi yeniden deneme girişimi bir <xref:System.TimeoutException> gerçekleşir, türünden türetilmediğinden başka bir genel özel durum olduğu **CommunicationException**.  
  
 Bir önceki özel durumlar oluştuğunda, yönlendirme hizmeti bir yedekleme uç noktalar listesine devreder. Tüm yedekleme uç noktaları bir iletişim hatası ile başarısız veya bir uç nokta bir özel durum döndürürse, hedef hizmetinde bir hata gösteriyor, yönlendirme hizmeti bir hata istemci uygulamasına döndürür.  
  
> [!NOTE]
>  Hata işleme işlevleri yakalar ve ileti göndermek çalışırken ve kanal kapatılmaya çalışılırken oluşan özel durumları işler. Hata işleme kodu algılamak veya uygulama uç noktaları ile iletişim tarafından oluşturulan özel durumları işlemek üzere tasarlanmamıştır; bir <xref:System.ServiceModel.FaultException> tarafından oluşturulan bir hizmet yönlendirme hizmeti görünür bir **FaultMessage** ve istemciye geri akışı yapılan işlemler.  
>   
>  Yönlendirme hizmeti bir ileti geçiş çalıştığında bir hata oluşursa, alabilirsiniz bir <xref:System.ServiceModel.FaultException> istemci tarafında yerine <xref:System.ServiceModel.EndpointNotFoundException> normal olarak yönlendirme hizmeti olmaması durumunda elde edersiniz. Yönlendirme hizmeti, böylece özel durumlarını maskeler ve iç içe geçmiş özel durumları incelemeniz sürece tam şeffaflık sağlamak.  
  
### <a name="tracing-exceptions"></a>Özel durum izleme  
 Yönlendirme hizmeti başarısız olursa listedeki bir uç nokta ileti gönderirken, sonuçta elde edilen özel durum verileri izler ve özel durum ayrıntıları adlı bir ileti özelliği ekler **özel durumları**. Bu, özel durum verilerini korur ve bir ileti Inspector'ı aracılığıyla bir kullanıcının programlı erişim sağlar.  Özel durum verileri, her ileti bir ileti göndermeye çalışırken karşılaşılan özel durum ayrıntıları için uç nokta adına eşleyen bir sözlükte depolanır.  
  
### <a name="backup-endpoints"></a>Yedekleme uç noktaları  
 Her filtre giriş filtre tablo içindeki isteğe bağlı olarak bir iletim hatası durumunda birincil uç noktasına gönderilirken kullanılan yedekleme uç noktaları listesini belirtebilirsiniz. Böyle bir hata oluşursa, yönlendirme hizmeti, yedekleme uç nokta listesinde ilk girişe ileti gönderirken dener. Bu gönderme girişimi de bir iletim hatası karşılaşırsa, sonraki uç nokta yedekleme listesinde denenir. Yönlendirme hizmeti, iletiyi başarıyla alınırsa, tüm uç noktaları bir iletim hatası döndürür veya bir olmayan iletim hatasının bir uç noktası tarafından döndürülen kadar listesindeki her bir uç nokta için ileti gönderilirken devam eder.  
  
 Aşağıdaki örnekler, yedekleme listesini kullanmak için yönlendirme hizmetini yapılandırın.  
  
```xml  
<routing>  
  <filters>  
    <!-- Create a MatchAll filter that catches all messages -->  
    <filter name="MatchAllFilter1" filterType="MatchAll" />  
  </filters>  
  <filterTables>  
    <!-- Set up the Routing Service's Message Filter Table -->  
    <filterTable name="filterTable1">  
        <!-- Add an entry that maps the MatchAllMessageFilter to the dead destination -->  
        <!-- If that endpoint is down, tell the Routing Service to try the endpoints -->  
        <!-- Listed in the backupEndpointList -->  
        <add filterName="MatchAllFilter1" endpointName="deadDestination" backupList="backupEndpointList"/>  
    </filterTable>  
  </filterTables>  
  <!-- Create the backup endpoint list -->  
  <backupLists>  
    <!-- Add an endpoint list that contains the backup destinations -->  
    <backupList name="backupEndpointList">  
      <add endpointName="realDestination" />  
      <add endpointName="backupDestination" />  
    </backupList>  
  </backupLists>  
</routing>  
```  
  
```csharp  
//create the endpoint list that contains the service endpoints we want to route to  
List<ServiceEndpoint> backupList = new List<ServiceEndpoint>();  
//add the endpoints in the order that the Routing Service should contact them  
//first add the endpoint that we know is down  
//clearly, normally you wouldn't know that this endpoint was down by default  
backupList.Add(fakeDestination);  
//then add the real Destination endpoint  
//the Routing Service attempts to send to this endpoint only if it   
//encounters a TimeOutException or CommunicationException when sending  
//to the previous endpoint in the list.  
backupList.Add(realDestination);  
//add the backupDestination endpoint  
//the Routing Service attempts to send to this endpoint only if it  
//encounters a TimeOutException or CommunicationsException when sending  
//to the previous endpoints in the list  
backupList.Add(backupDestination);  
//create the default RoutingConfiguration option              
RoutingConfiguration rc = new RoutingConfiguration();  
//add a MatchAll filter to the Routing Configuration's filter table  
//map it to the list of endpoints defined above  
//when a message matches this filter, it is sent to the endpoints in the list in order  
//if an endpoint is down or does not respond (which the first endpoint won't  
//since the client does not exist), the Routing Service automatically moves the message  
//to the next endpoint in the list and try again.  
rc.FilterTable.Add(new MatchAllMessageFilter(), backupList);  
```  
  
### <a name="supported-error-patterns"></a>Desteklenen hata desenleri  
 Aşağıdaki tabloda, yedekleme uç nokta listeleri, hata işleme için belirli desenleri ayrıntılarını açıklayan Notlar birlikte kullanımı ile uyumlu olan desenleri açıklar.  
  
|Desen|Oturum|İşlem|Bağlamı alma|Desteklenen yedekleme listesi|Notlar|  
|-------------|-------------|-----------------|---------------------|---------------------------|-----------|  
|Tek Yönlü||||Evet|Bir yedekleme uç noktasında iletiyi yeniden dener. Bu ileti olup olmadığını çok noktaya yayın, yalnızca başarısız bir kanalda ileti, yedekleme hedefine taşınır.|  
|Tek Yönlü||![Onay işareti](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "onay işareti")||Hayır|Bir özel durum ve işlem geri alındı.|  
|Tek Yönlü|||![Onay işareti](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "onay işareti")|Evet|Bir yedekleme uç noktasında iletiyi yeniden dener. İleti sonra başarıyla alındı, tam tüm bağlamı alır. İleti tarafından herhangi bir uç noktası başarıyla alınmazsa alma bağlamı tamamlamayın.<br /><br /> Bu ileti yükleniyor, çok noktaya yayın alma bağlamı ileti en az bir uç noktası tarafından (birincil veya yedek) başarıyla alınırsa yalnızca tamamlandı. Uç noktaları çok noktaya yayın yollardan birinde hiçbiri başarılı bir şekilde iletisi alırsanız, alma bağlamı tamamlamayın.|  
|Tek Yönlü||![Onay işareti](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "onay işareti")|![Onay işareti](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "onay işareti")|Evet|Önceki işlem durdurma, yeni bir işlem oluşturun ve tüm iletileri yeniden gönderin. Bir hatayla karşılaştı iletileri yedekleme hedefine aktarılır.<br /><br /> Bir işlem oluşturulduktan sonra tüm iletimler başarısız, alma bağlamı tamamlayın ve hareketi.|  
|Tek Yönlü|![Onay işareti](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "onay işareti")|||Evet|Bir yedekleme uç noktasında iletiyi yeniden dener. Bir çok noktaya yayın senaryosunda, yedekleme hedefi için yalnızca iletileri bir oturumda bir hatayla karşılaştı veya başarısız oturumunu kapatmak bir oturumda gönderilir.|  
|Tek Yönlü|![Onay işareti](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "onay işareti")|![Onay işareti](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "onay işareti")||Hayır|Bir özel durum ve işlem geri alındı.|  
|Tek Yönlü|![Onay işareti](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "onay işareti")||![Onay işareti](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "onay işareti")|Evet|Bir yedekleme uç noktasında iletiyi yeniden dener. Tüm hata tamamlandı iletisi sonra oturumu başka iletilerin gösterir ve yönlendirme hizmeti başarıyla tüm giden oturumu kanallarınızı kapatır, tüm alma bağlamları tamamlanır ve gelen oturum kanalı kapatıldı.|  
|Tek Yönlü|![Onay işareti](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "onay işareti")|![Onay işareti](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "onay işareti")|![Onay işareti](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "onay işareti")|Evet|Geçerli işlem iptal edip yeni bir tane oluşturun. Tüm önceki iletileri oturumunda yeniden gönderin. Bir işlem, tüm ileti başarıyla gönderildi oluşturulduktan sonra daha fazla ileti, tüm giden oturum kanalları kapalı olduğundan, alma oturumu gösterir bağlamları tüm olan işlem tamamlanır, gelen oturum kanalı Kapalı, ve işlem taahhüt eder.<br /><br /> Çok noktaya yayın aynı hedefe önce herhangi bir hata vardı iletileri gönderilir ve hatayla iletileri oturumları ne zaman gönderildiğini yedekleme hedefi için gönderilir.|  
|İki yönlü||||Evet|Yedekleme hedefine gönderin.  Bir kanal bir yanıt iletisi döndürür. sonra özgün istemci yanıtı döndürür.|  
|İki yönlü|![Onay işareti](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "onay işareti")|||Evet|Tüm iletileri kanalda yedekleme hedefine gönderin.  Bir kanal bir yanıt iletisi döndürür. sonra özgün istemci yanıtı döndürür.|  
|İki yönlü||![Onay işareti](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "onay işareti")||Hayır|Bir özel durum ve işlem geri alındı.|  
|İki yönlü|![Onay işareti](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "onay işareti")|![Onay işareti](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "onay işareti")||Hayır|Bir özel durum ve işlem geri alındı.|  
|Çift Yönlü||||Hayır|Çift yönlü iletişim olmayan oturumu şu anda desteklenmiyor.|  
|Çift Yönlü|![Onay işareti](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "onay işareti")|||Evet|Yedekleme hedefine gönderin.|  
  
## <a name="hosting"></a>Barındırma  
 Yönlendirme hizmeti bir WCF hizmeti olarak uygulandığından, bir uygulamadaki şirket içinde barındırılan veya barındırılan IIS ya da WAS tarafından. Yönlendirme hizmeti, IIS, WAS veya bir Windows hizmeti uygulaması otomatik olarak başlamasını avantajlarından yararlanın ve yaşam döngüsü yönetim özellikleri bu barındırma ortamları kullanılabilir barındırılan önerilir.  
  
 Aşağıdaki örnek, bir uygulamada yönlendirme hizmeti barındırma gösterir.  
  
```csharp  
using (ServiceHost serviceHost =  
                new ServiceHost(typeof(RoutingService)))  
```  
  
 Yönlendirme hizmeti IIS ya da WAS içinde barındırmak için bir hizmet dosyası (.svc) oluşturun veya hizmetin yapılandırma temelli etkinleştirme kullanın gerekir. Hizmet dosyasını kullanırken belirtmelisiniz <xref:System.ServiceModel.Routing.RoutingService> hizmet parametresini kullanarak. Aşağıdaki örnek, IIS veya WAS ile yönlendirme hizmeti barındırmak için kullanılan bir örnek hizmet dosyası içerir.  
  
```  
<%@ ServiceHost Language="C#" Debug="true" Service="System.ServiceModel.Routing.RoutingService,   
     System.ServiceModel.Routing, version=4.0.0.0, Culture=neutral,   
     PublicKeyToken=31bf3856ad364e35" %>  
```  
  
## <a name="routing-service-and-impersonation"></a>Yönlendirme hizmeti ile kimliğe bürünme  
 WCF yönlendirme hizmeti ile kimliğe bürünme hem ileti gönderme ve alma için kullanılabilir. Tüm kimliğe bürünme normal Windows kısıtlamaları uygulanır. Kimliğe bürünme kendi hizmet yazarken kullanmak için hizmet veya hesap izinlerini ayarlamak gerekli olursa, kimliğe bürünme yönlendirme hizmeti ile kullanmak için bu aynı adımları uygulamanız gerekir. Daha fazla bilgi için [temsilcilik ve kimliğe bürünme](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
 Yönlendirme hizmeti ile kimliğe bürünme, ASP.NET kimliğe bürünme modunda ASP.NET uyumluluk kullanımı ya da kimliğe bürünme izin verecek şekilde yapılandırılmış bir Windows kimlik bilgilerinin kullanımını gerektirir. ASP.NET uyumluluğu modu hakkında daha fazla bilgi için bkz. [WCF hizmetleri ve ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).  
  
> [!WARNING]
>  WCF yönlendirme hizmeti, temel kimlik doğrulaması ile kimliğe bürünme desteklemez.  
  
 ASP.NET kimliğe bürünme yönlendirme hizmeti ile kullanmak için hizmet barındırma ortamını ASP.NET uyumluluk modu etkinleştirin. Yönlendirme hizmeti, zaten ASP.NET uyumluluk modunun ve kimliğe bürünme otomatik olarak etkinleştirilecek izin verecek şekilde işaretlendi. Kimliğe bürünme ASP.NET tümleştirme yönlendirme hizmeti ile yalnızca desteklenen kullanılmasıdır.  
  
 Windows kimlik bilgisi kimliğe bürünme yönlendirme hizmeti ile kullanmak için kimlik bilgilerini hem service'ı yapılandırmanız gerekir. İstemci kimlik bilgileri nesnesi (<xref:System.ServiceModel.Security.WindowsClientCredential>, gelen erişilebilir operasyonlar <xref:System.ServiceModel.ChannelFactory>) tanımlayan bir <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> kimliğe bürünme izin vermek için ayarlanmalıdır özelliği. Son olarak, hizmette yapılandırmanız gereken <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> ayarlamak için davranış `ImpersonateCallerForAllOperations` için `true`. Yönlendirme hizmeti ile kişileştirme etkinleştirildi iletilerini yönlendirmede istemcileri oluşturma karar vermek için bu bayrağı kullanır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İleti Filtreleri](../../../../docs/framework/wcf/feature-details/message-filters.md)  
 [Anlaşmaları Yönlendirme](../../../../docs/framework/wcf/feature-details/routing-contracts.md)  
 [Filtre Seçme](../../../../docs/framework/wcf/feature-details/choosing-a-filter.md)
