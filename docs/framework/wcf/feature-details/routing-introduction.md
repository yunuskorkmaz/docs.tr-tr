---
title: Yönlendirme Tanıtımı
ms.date: 03/30/2017
ms.assetid: bf6ceb38-6622-433b-9ee7-f79bc93497a1
ms.openlocfilehash: 3ee7ea8271df47354a0897434bf8f203eaf09a51
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="routing-introduction"></a>Yönlendirme Tanıtımı
Yönlendirme hizmeti, ileti içeriğine göre yönlendirme iletilerinin özelliğine sahip bir genel takılabilir SOAP aracı sağlar. Yönlendirme hizmeti ile hizmet toplama, hizmet sürümü oluşturma, öncelik Yönlendirme ve çok noktaya yayın yönlendirme gibi senaryolar uygulamak olanak tanıyan karmaşık bir yönlendirme mantık oluşturabilirsiniz. Yönlendirme hizmeti, işleme hatası, birincil hedef uç noktasına gönderilirken bir hata oluşursa, iletileri gönderildiği yedekleme uç noktaları listelerini ayarlamanıza olanak tanır de sağlar.  
  
 Bu konu için yönlendirme hizmeti yeni yöneliktir ve temel yapılandırma ve yönlendirme hizmeti barındırma kapsar.  
  
## <a name="configuration"></a>Yapılandırma  
 Yönlendirme hizmeti, istemci uygulamalarından iletileri almasına ve iletileri bir veya daha fazla hedef Uç noktalara yönlendirmek bir veya daha fazla hizmet uç noktaları kullanıma sunan bir WCF hizmeti olarak uygulanır. Hizmeti sağlayan bir <xref:System.ServiceModel.Routing.RoutingBehavior>, hizmet tarafından kullanıma sunulan hizmet uç noktalarına uygulanır. Bu davranış, hizmetin nasıl çalıştığı hakkında çeşitli yönlerini yapılandırmak için kullanılır. Üzerinde belirtilen bir yapılandırma dosyası kullanırken yapılandırma kolaylığı için parametreleri **RoutingBehavior**. Kod tabanlı senaryolarda, bu parametreler parçası olarak belirtilen bir <xref:System.ServiceModel.Routing.RoutingConfiguration> için geçirilebilir nesnesi bir **RoutingBehavior**.  
  
 Başlatma sırasında bu davranış ekler <xref:System.ServiceModel.Routing.SoapProcessingBehavior>, istemci uç noktaları için iletileri SOAP işlemeyi gerçekleştirmek için kullanılır. Farklı bir Gerektirdiğiniz iletileri iletmek yönlendirme hizmeti böylece **MessageVersion** üzerinden alınan ileti uç nokta değerinden. **RoutingBehavior** de bir hizmeti uzantı kayıtları <xref:System.ServiceModel.Routing.RoutingExtension>, çalışma zamanında yönlendirme hizmeti yapılandırmasını değiştirmek için erişilebilirlik noktası sağlar.  
  
 **RoutingConfiguration** sınıfı, yapılandırma ve yönlendirme hizmeti yapılandırmasını güncelleştirmek için tutarlı bir yol sağlar.  Yönlendirme hizmeti ayarlarını olarak davranmasına ve yapılandırmak için kullanılan parametreleri içeren **RoutingBehavior** hizmeti başladığında veya geçirilir **RoutingExtension** yönlendirme değiştirmek için Çalışma zamanında yapılandırma.  
  
 İçerik tabanlı yönlendirme iletilerinin gerçekleştirmek için kullanılan yönlendirme mantığı birden çok gruplandırma tarafından tanımlanan <xref:System.ServiceModel.Dispatcher.MessageFilter> nesneleri içine birlikte filtre tabloları (<xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> nesneleri). Gelen İleti Filtresi tablosu ve her ileti filtreleri karşı değerlendirilir **MessageFilter** hedef uç noktasına iletilen iletinin eşleşir. Kullanarak iletileri yönlendirmek için kullanılan filtre tablosunda belirtilen **RoutingBehavior** yapılandırmasında veya kullanarak kod aracılığıyla **RoutingConfiguration** nesnesi.  
  
### <a name="defining-endpoints"></a>Uç noktaları tanımlama  
 Kullanacağınız yönlendirme mantığı tanımlayarak yapılandırmanızı başlaması gerektiğini görünebilir, ancak ilk adımınız yönlendirme mesajlarına olacaktır uç noktaları şeklini belirlemek için gerçekten olmalıdır. Yönlendirme hizmeti almak ve iletileri göndermek için kullanılan kanalları şekil tanımlamak sözleşmeleri kullanır ve bu nedenle Giriş kanalı şekli çıktı kanalı eşleşmelidir.  İstek-yanıt kanal şekli kullanan uç noktaları yönlendirme, örneğin, sonra uyumlu bir sözleşme gelen uç noktalarda gibi kullanmalısınız <xref:System.ServiceModel.Routing.IRequestReplyRouter>.  
  
 Başka bir deyişle, hedef uç noktaları (örneğin, tek yönlü ve iki yönlü işlemleri karıştırma) birden çok iletişim desenlerle sözleşmeleri kullanırsanız, alabilen ve bunların tümüne iletileri yönlendirmek tek hizmet uç noktası oluşturulamıyor. Hangi uç noktaları uyumlu şekiller varsa ve hedef Uç noktalara yönlendirilmesi için iletileri almak için kullanılan bir veya daha fazla hizmet uç noktaları tanımlamak belirlemeniz gerekir.  
  
> [!NOTE]
>  Birden çok iletişim düzenleri (örneğin, tek yönlü ve iki yönlü işlemleri karışımını) belirtin sözleşmeleri ile çalışırken, geçici bir çözüm çift yönlü sözleşme yönlendirme hizmeti gibi kullanmaktır <xref:System.ServiceModel.Routing.IDuplexSessionRouter>. Ancak bu bağlama için tüm senaryoları mümkün olmayabilir çift yönlü iletişim yeteneğine sahip olması gerektiği anlamına gelir. Bu mümkün olduğu senaryolarda, birden çok uç nokta içine iletişime Finansman veya uygulamayı değiştirirken gerekli olabilir.  
  
 Sözleşmeleri yönlendirme hakkında daha fazla bilgi için bkz: [sözleşmeleri yönlendirme](../../../../docs/framework/wcf/feature-details/routing-contracts.md).  
  
 Hizmet uç noktası tanımlandıktan sonra kullanabileceğiniz **RoutingBehavior** belirli bir ilişkilendirilecek **RoutingConfiguration** uç noktası ile. Yönlendirme hizmeti bir yapılandırma dosyası kullanarak yapılandırırken **RoutingBehavior** Bu uç noktada alınan iletileri işlemek için kullanılan yönlendirme mantığını içerir Filtresi tablosu belirtmek için kullanılır. Yönlendirme hizmeti program aracılığıyla yapılandırıyorsanız kullanarak filtreleme tablosu belirtebilirsiniz **RoutingConfiguration**.  
  
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
  
 Bu örnek bir adresi olan tek bir uç noktası kullanıma sunmak için yönlendirme hizmeti yapılandırır "http://localhost:8000/routingservice/router", yönlendirilecek iletileri almak için kullanılır. Hizmet uç noktası kullanır, iletiler istek-yanıt Uç noktalara yönlendirilir çünkü <xref:System.ServiceModel.Routing.IRequestReplyRouter> sözleşme. Bu yapılandırma ayrıca bir tek istemci uç noktasını tanımlıyor "http://localhost:8000/servicemodelsample/service" iletileri için yönlendirilir. "RoutingTable1" adlı (gösterilmez) filtre tablo iletileri yönlendirmek için kullanılan yönlendirme mantığı içerir ve kullanarak hizmet uç noktası ile ilişkili **RoutingBehavior** (için bir yapılandırma dosyası) veya  **RoutingConfiguration** (için program yapılandırması).  
  
### <a name="routing-logic"></a>Yönlendirme mantığı  
 İletileri yönlendirmek için kullanılan yönlendirme mantığını tanımlamak için ne gelen iletileri içinde bulunan verileri olabilir belirlemeniz gerekir benzersiz olarak sayısı. İyi bir gösterge aynı SOAP Eylemler, iletinin içinde yer alan eylem değerini paylaşmak için yönlendirme tüm hedef uç noktaları değilse, örneğin, belirli hangi uç noktasını ileti için yönlendirileceğini. Benzersiz olarak belirli bir uç noktasına iletileri yönlendirmek gerekir varsa, ileti yönlendirilir hedef uç nokta benzersiz olarak tanımlayan veri üzerine filtre.  
  
 Yönlendirme hizmeti birkaç sağlar **MessageFilter** adres, eylem, uç nokta adı veya hatta bir XPath sorgusu gibi bir iletinin içinde belirli değerleri inceleyin uygulamaları. Bu uygulamalar hiçbiri gereksinimlerinizi karşılıyorsa, özel bir oluşturabilirsiniz **MessageFilter** uygulaması. İleti filtreleri ve yönlendirme hizmeti tarafından kullanılan uygulamaları karşılaştırması hakkında daha fazla bilgi için bkz: [ileti filtreleri](../../../../docs/framework/wcf/feature-details/message-filters.md) ve [filtre seçme](../../../../docs/framework/wcf/feature-details/choosing-a-filter.md).  
  
 Birden çok ileti filtreleri birlikte her ilişkilendirmek filtre tablolara düzenlenir **MessageFilter** hedef uç noktası ile. İsteğe bağlı olarak, filtre tablosunda yönlendirme hizmeti için bir iletim hatası durumunda iletiyi göndermeyi deneyecek yedekleme bitiş noktaları listesini belirtmek için de kullanılabilir.  
  
 Varsayılan olarak tüm ileti filtreleri Filtresi tablosu içinde eşzamanlı olarak değerlendirilir; Ancak, belirleyebileceğiniz bir <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement.Priority%2A> belirli bir sırada değerlendirilecek ileti filtreleri neden olur. En yüksek önceliğe sahip tüm girişleri ilk olarak değerlendirilir ve daha yüksek bir öncelik düzeyde bir eşleşme bulunamazsa, ileti filtreleri alt öncelikler değerlendirilmez. Filtre tabloları hakkında daha fazla bilgi için bkz: [ileti filtreleri](../../../../docs/framework/wcf/feature-details/message-filters.md).  
  
 Aşağıdaki örneklerde <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter>, hesaplar için `true` tüm iletiler için. Bu **MessageFilter** ilişkilendiren "routingTable1" filtre tabloya eklenen **MessageFilter** "CalculatorService" adlı istemci uç noktası ile. **RoutingBehavior** Bu tablo Hizmeti uç noktası tarafından işlenen iletileri yönlendirmek için kullanılması gerektiğini belirtir.  
  
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
>  Varsayılan olarak, yönlendirme hizmeti, yalnızca ileti üstbilgilerini değerlendirir. İleti gövdesi erişmek için filtreleri izin vermek için ayarlamanız gerekir <xref:System.ServiceModel.Routing.RoutingConfiguration.RouteOnHeadersOnly%2A> için `false`.  
  
 **Çok noktaya yayın**  
  
 Birçok yönlendirme hizmeti yapılandırması yalnızca bir özel uç noktasına iletileri yönlendiren özel filtre mantığı kullanırken, belirli bir ileti birden çok hedef Uç noktalara yönlendirmek gerekebilir. Çok noktaya yayın ileti birden çok varış yeri için aşağıdaki koşulların doğru olması gerekir:  
  
-   Kanal şekli istek-yanıt olmamalıdır (ancak tek yönlü veya çift yönlü olabilir) çünkü isteğine yanıt olarak istemci uygulaması tarafından yalnızca bir yanıt aldı.  
  
-   Birden çok filtre döndürmelidir `true` ileti değerlendirirken.  
  
 Bu koşullar karşılanıyorsa, ileti tüm uç noktaları için değerlendirin tüm filtreleri yönlendirilir `true`. Aşağıdaki örnek, uç nokta adresi iletisi ise, her iki uç noktalara yönlendirilen iletilerinde sonuçları bir yönlendirme yapılandırması tanımlar http://localhost:8000/routingservice/router/rounding.  
  
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
 İletileri farklı protokoller arasında yönlendirme desteklemek için **RoutingBehavior** varsayılan ekler <xref:System.ServiceModel.Routing.SoapProcessingBehavior> iletileri yönlendirilir tüm istemci uç için. Bu davranış otomatik olarak yeni bir oluşturur **MessageVersion** uyumlu bir oluşturma yanı sıra uç noktasına ileti yönlendirme önce **MessageVersion** kendisine dönmeden önce herhangi bir yanıt belge için istekte bulunan istemci uygulaması.  
  
 Yeni bir oluşturmak için adımlar **MessageVersion** giden ileti için aşağıdaki gibidir:  
  
 **İstek işleme**  
  
-   Alma **MessageVersion** kanalının giden bağlama /.  
  
-   Gövde Okuyucu için özgün iletisini alırsınız.  
  
-   Aynı eylemi, gövde okuyucu ve yeni bir ile yeni bir ileti oluşturma **MessageVersion**.  
  
-   Varsa <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> ! = **Addressing.None**, Kime FaultTo, Kopyala ve yeni iletisi RelatesTo üstbilgi.  
  
-   Tüm ileti özellikleri yeni bir iletiye kopyalayın.  
  
-   Yanıtı işlerken kullanılacak özgün istek iletisi depolar.  
  
-   Yeni İstek iletisi döndürür.  
  
 **Yanıt işleme**  
  
-   Alma **MessageVersion** özgün istek iletisi.  
  
-   Gövde Okuyucu için alınan yanıt iletisini alır.  
  
-   Gövde okuyucu aynı eylemi yeni bir yanıt iletisi oluşturmak ve **MessageVersion** özgün istek iletisi.  
  
-   Varsa <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> ! = **Addressing.None**, Kime FaultTo, Kopyala ve yeni iletisi RelatesTo üstbilgi.  
  
-   İleti özellikleri yeni bir iletiye kopyalayın.  
  
-   Yeni yanıt iletisi döndürür.  
  
 Varsayılan olarak, **SoapProcessingBehavior** istemci uç noktaları tarafından otomatik olarak eklenir <xref:System.ServiceModel.Routing.RoutingBehavior> hizmeti başladığında; ancak, kullanarak SOAP işleme için tüm istemci uç noktaları eklenip eklenmediğini kontrol edebilirsiniz <xref:System.ServiceModel.Routing.RoutingConfiguration.SoapProcessingEnabled%2A> özelliği. Ayrıca davranışı doğrudan belirli bir bitiş noktasına eklemek ve da etkinleştirebilir veya SOAP işleme konusunda daha ayrıntılı bir denetim gerekli olduğunda bu davranış uç nokta düzeyinde devre dışı bırakın.  
  
> [!NOTE]
>  SOAP işleme özgün istek iletisi daha farklı MessageVersion gerektiren bir uç nokta için devre dışı bırakılırsa, iletiyi göndermeden önce gerekli herhangi bir SOAP değişiklik gerçekleştirmek için özel bir mekanizma sağlamanız gerekir Hedef uç noktası.  
  
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
 Ek istemci uç noktalarını eklemek veya iletileri yönlendirmek için kullanılan filtreleri değiştirmek için ihtiyacınız olduğunda hizmet şu anda üzerinden ileti alma Uç noktalara kesilmesini önlemek için dinamik olarak çalışma zamanında yapılandırmasını güncelleştirmek için bir yol olması gerekir Yönlendirme hizmeti. Her iki yöntem hiçbir ileti şu anda transit ve olası olası kaybı için kapalı kalma süresi sırasında için sunulmasını uygulamasını geri dönüşüme gerektirdiğinden bir yapılandırma dosyası veya konak uygulama kodunu değiştirme her zaman yeterli değil hizmetin yeniden başlatılması bekliyor.  
  
 Yalnızca değiştirebileceğiniz **RoutingConfiguration** programlı olarak. Hizmet yapılandırma dosyası kullanarak başlangıçta yapılandırabilirsiniz ancak, yalnızca çalışma zamanında yapılandırma yeni bir oluşturarak değiştirebilirsiniz **RoutingConfigution** ve parametre olarak geçirme <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> yöntemi tarafından sunulan <xref:System.ServiceModel.Routing.RoutingExtension> hizmet uzantısı. Çağrısından sonra alınan iletilerin çalışırken önceki yapılandırmayı kullanarak yönlendirilecek şu anda yoldaki tüm iletileri devam **ApplyConfiguration** yeni yapılandırmasını kullanın. Aşağıdaki örnek, yönlendirme hizmeti örneği oluşturmayı ve daha sonra yapılandırmasını değiştirme gösterir.  
  
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
>  Bu şekilde yönlendirme hizmeti güncelleştirirken yalnızca yeni bir yapılandırma geçişi mümkündür. Geçerli yapılandırma yalnızca seçilen öğeleri değiştirmek veya geçerli yapılandırması için yeni girdileri eklemek mümkün değildir; oluşturmanız ve varolan yerini yeni bir yapılandırma geçişi gerekir.  
  
> [!NOTE]
>  Önceki yapılandırmayı kullanarak açılan oturumlar önceki yapılandırmayı kullanarak devam edin. Yeni yapılandırma, yalnızca yeni oturumlar tarafından kullanılır.  
  
## <a name="error-handling"></a>Hata İşleme  
 Varsa <xref:System.ServiceModel.CommunicationException> hata meydana işleme bir ileti göndermeye çalışırken hatayla karşılaştı. Bu özel durumlar gibi tanımlanmış istemci uç noktası ile iletişim kurmaya çalışırken bir sorunla karşılaşıldı genellikle belirtmek bir <xref:System.ServiceModel.EndpointNotFoundException>, <xref:System.ServiceModel.ServerTooBusyException>, veya <xref:System.ServiceModel.CommunicationObjectFaultedException>. Hata işleme kodu da yakalamak ve ne zaman göndermeyi yeniden deneme girişimi bir <xref:System.TimeoutException> oluşur, türetilmedi başka bir ortak özel durumu olan **CommunicationException**.  
  
 Önceki özel durumlardan birini ortaya çıktığında, yönlendirme hizmeti üzerinden bir yedekleme uç noktaları listesine başarısız olur. Tüm yedekleme uç noktaları bir iletişim hatası ile başarısız ya da bir uç nokta bir özel durum döndürürse hedef hizmetinde bir hata gösterir, yönlendirme hizmeti istemci uygulamasına bir hata döndürür.  
  
> [!NOTE]
>  Hata işleme işlevselliği yakalar ve bir ileti göndermeye çalışırken ve kanal kapatılmaya çalışılırken oluşan özel durumları işler. Hata işleme kodu algılamak veya ile iletişim uygulama uç noktaları tarafından oluşturulan özel durumları işlemek üzere tasarlanmamıştır; bir <xref:System.ServiceModel.FaultException> tarafından oluşturulan bir hizmet yönlendirme hizmeti görünür bir **FaultMessage** ve istemciye akıtılan.  
>   
>  Yönlendirme hizmeti bir ileti geçiş yapmaya çalıştığında bir hata oluşursa, alabilirsiniz bir <xref:System.ServiceModel.FaultException> istemci tarafında yerine bir <xref:System.ServiceModel.EndpointNotFoundException> normalde yönlendirme hizmeti olmaması durumunda alırsınız. Yönlendirme hizmeti, böylece özel durumlar maske ve iç içe geçmiş özel durumları inceleyin sürece tam saydamlığı sağlamak için değil olabilir.  
  
### <a name="tracing-exceptions"></a>Özel durum izleme  
 Bir listedeki bir uç nokta ileti başarısız gönderirken, yönlendirme hizmeti ortaya çıkan özel durum verileri izler ve özel durum ayrıntıları adlı bir ileti özelliği ekler **özel durumları**. Bu özel durum verileri korur ve ileti denetçisi aracılığıyla kullanıcı programlı erişim sağlar.  Özel durum verileri, her ileti bir ileti göndermeye çalışırken karşılaşılan özel durum ayrıntıları uç nokta adı eşlendiği sözlükte depolanır.  
  
### <a name="backup-endpoints"></a>Yedekleme uç noktaları  
 Filtre tablo içindeki her filtre giriş isteğe bağlı olarak bir iletim hatası durumunda birincil uç noktasına gönderirken kullanılan yedekleme bitiş noktaları listesini belirtebilirsiniz. Bu tür bir hata oluşursa, yönlendirme hizmeti yedekleme endpoint listedeki ilk giriş iletiyi iletme dener. Bu gönderme girişimi de iletim hatasının karşılaşırsa, yedek listeyi sonraki uç denenir. Yönlendirme hizmeti iletiyi başarıyla alınırsa, tüm uç noktaları iletim hata döndürür veya bir olmayan iletim hatasının bir uç noktası tarafından döndürülen kadar listesindeki her bir uç nokta için ileti gönderilirken devam eder.  
  
 Aşağıdaki örnekler bir yedekleme listesi kullanmak için yönlendirme hizmeti yapılandırın.  
  
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
 Aşağıdaki tabloda, yedekleme endpoint listeleri, hata işleme için belirli desenleri ayrıntılarını açıklayan Notlar birlikte kullanımı ile uyumlu desenleri açıklar.  
  
|Desen|Oturum|İşlem|Bağlamı alma|Desteklenen yedekleme listesi|Notlar|  
|-------------|-------------|-----------------|---------------------|---------------------------|-----------|  
|Tek Yönlü||||Evet|Yedek bir uç noktada iletiyi yeniden dener. Bu ileti yaşanıyorsa çok noktaya yayın, yalnızca ileti başarısız kanalda yedekleme hedefine taşındı.|  
|Tek Yönlü||![Onay işareti](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "onay işareti")||Hayır|Bir özel durum ve işlem geri alındı.|  
|Tek Yönlü|||![Onay işareti](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "onay işareti")|Evet|Yedek bir uç noktada iletiyi yeniden dener. İleti sonra başarıyla alındı, tam tüm bağlamları alırsınız. İleti tarafından herhangi bir uç nokta başarıyla alınmazsa alma bağlamı tamamlamayın.<br /><br /> Bu ileti yükleniyor zaman çok noktaya yayın alma bağlamı ileti en az bir uç noktası tarafından (birincil veya yedek) başarıyla alınırsa yalnızca tamamlandı. Uç noktalarını çok noktaya yayın yolların hiçbiri başarılı bir şekilde iletisi alırsanız, alma bağlamı tamamlamayın.|  
|Tek Yönlü||![Onay işareti](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "onay işareti")|![Onay işareti](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "onay işareti")|Evet|Önceki işlem abort, yeni bir işlem oluşturun ve tüm iletileri yeniden gönderin. Bir hata ile karşılaştı iletileri bir yedekleme hedefine iletilir.<br /><br /> Bir işlem oluşturulduktan sonra tüm iletimler başarısız, alma bağlamları tamamlayın ve hareketi.|  
|Tek Yönlü|![Onay işareti](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "onay işareti")|||Evet|Yedek bir uç noktada iletiyi yeniden dener. Çok noktaya yayın senaryoda yalnızca iletileri bir hatayla karşılaştı bir oturumda veya oturumunda başarısız oturumunu kapatmak için yedekleme hedefi gönderilir.|  
|Tek Yönlü|![Onay işareti](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "onay işareti")|![Onay işareti](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "onay işareti")||Hayır|Bir özel durum ve işlem geri alındı.|  
|Tek Yönlü|![Onay işareti](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "onay işareti")||![Onay işareti](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "onay işareti")|Evet|Yedek bir uç noktada iletiyi yeniden dener. Tüm hata tamamlandı iletisi sonra oturumu başka iletilerin gösterir ve yönlendirme hizmeti başarıyla tüm giden oturum kanal kapatır, alması bağlamları tamamlanır ve gelen oturum kanalı kapatıldı.|  
|Tek Yönlü|![Onay işareti](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "onay işareti")|![Onay işareti](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "onay işareti")|![Onay işareti](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "onay işareti")|Evet|Geçerli işlem iptal etmek ve yeni bir tane oluşturun. Tüm önceki iletileri oturumu yeniden gönderin. Bir işlem, tüm iletileri başarıyla gönderildi oluşturulduktan sonra daha fazla ileti, tüm giden oturum kanalları kapalı olduğundan, alma oturumu gösterir bağlamları tüm işlemle tamamlanır, gelen oturum kanalı Kapalı, ve işlem taahhüt eder.<br /><br /> Çok noktaya yayın aynı hedefe önce herhangi bir hata vardı iletileri gönderilir ve bir hata ile karşılaştı iletileri oturumları zaman olan yedekleme hedefi için gönderilir.|  
|Çift yönlü||||Evet|Bir yedekleme hedefine Gönder.  Bir kanal bir yanıt iletisi döndüren sonra özgün istemci yanıtı döndürür.|  
|Çift yönlü|![Onay işareti](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "onay işareti")|||Evet|Tüm iletileri kanalda bir yedekleme hedefine Gönder.  Bir kanal bir yanıt iletisi döndüren sonra özgün istemci yanıtı döndürür.|  
|Çift yönlü||![Onay işareti](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "onay işareti")||Hayır|Bir özel durum ve işlem geri alındı.|  
|Çift yönlü|![Onay işareti](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "onay işareti")|![Onay işareti](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "onay işareti")||Hayır|Bir özel durum ve işlem geri alındı.|  
|Çift Yönlü||||Hayır|Çift yönlü iletişimi olmayan oturumu şu anda desteklenmiyor.|  
|Çift Yönlü|![Onay işareti](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "onay işareti")|||Evet|Bir yedekleme hedefine Gönder.|  
  
## <a name="hosting"></a>Barındırma  
 Yönlendirme hizmeti bir WCF hizmeti olarak uygulanması için ya da bir uygulama içinde kendi kendini barındıran veya gerekir barındırılan IIS ya da WAS tarafından. Yönlendirme hizmeti, IIS, WAS veya bir Windows hizmet uygulaması otomatik olarak başlamasını yararlanabilir ve yaşam döngüsü yönetimi özellikleri bu barındırma ortamlarında kullanılabilir barındırılması önerilir.  
  
 Aşağıdaki örnek, yönlendirme hizmeti bir uygulamada barındırma gösterir.  
  
```csharp  
using (ServiceHost serviceHost =  
                new ServiceHost(typeof(RoutingService)))  
```  
  
 Yönlendirme hizmeti IIS ya da WAS içinde barındırmak için bir hizmet dosyası (.svc) oluşturmanız veya yapılandırma temelli etkinleştirme hizmetinin kullanmak gerekir. Bir hizmeti dosyasını kullanırken belirtmelisiniz <xref:System.ServiceModel.Routing.RoutingService> hizmet parametresini kullanarak. Aşağıdaki örnek, yönlendirme hizmeti IIS ya da WAS ile barındırmak için kullanılan bir örnek hizmet dosyası içerir.  
  
```  
<%@ ServiceHost Language="C#" Debug="true" Service="System.ServiceModel.Routing.RoutingService,   
     System.ServiceModel.Routing, version=4.0.0.0, Culture=neutral,   
     PublicKeyToken=31bf3856ad364e35" %>  
```  
  
## <a name="routing-service-and-impersonation"></a>Yönlendirme hizmeti ile kimliğe bürünme  
 WCF yönlendirme hizmeti ile kimliğe bürünme hem ileti gönderme ve alma için kullanılabilir. Tüm kimliğe bürünme normal Windows kısıtlamalar uygulanır. Kimliğe bürünme kendi hizmet yazarken kullanmak için hizmet veya hesap izinlerini ayarlamak gerekli, kimliğe bürünme yönlendirme hizmeti ile kullanmak için bu aynı adımları gerçekleştirmeniz gerekir. Daha fazla bilgi için bkz: [temsilcilik ve kimliğe bürünme](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
 Yönlendirme hizmeti ile kimliğe bürünme, ASP.NET kimliğe bürünme ASP.NET uyumluluğu modundayken kullanımını ya da kimliğe bürünme izin verecek şekilde yapılandırılmış Windows kimlik bilgilerinin kullanımını gerektirir. ASP.NET uyumluluğu modu hakkında daha fazla bilgi için bkz: [WCF hizmetleri ve ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).  
  
> [!WARNING]
>  Yönlendirme WCF Hizmeti temel kimlik doğrulaması ile kimliğe bürünme desteklemez.  
  
 ASP.NET kimliğe bürünme yönlendirme hizmeti ile kullanmak için barındırma ortamı Service ASP.NET uyumluluğu modunu etkinleştirin. Yönlendirme hizmeti zaten ASP.NET uyumluluk modu ve kimliğe bürünme özelliğini otomatik olarak etkinleştirilecek izin verme olarak işaretlendi. Kimliğe bürünme ASP.NET tümleştirme yönlendirme hizmeti ile yalnızca desteklenen kullanılmasıdır.  
  
 Windows kimlik bilgisi kimliğe bürünme yönlendirme hizmeti ile kullanmak için kimlik bilgileri ve hizmet yapılandırmanız gerekir. İstemci kimlik bilgileri nesnesini (<xref:System.ServiceModel.Security.WindowsClientCredential>, gelen accessable <xref:System.ServiceModel.ChannelFactory>) tanımlayan bir <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> özelliği kimliğe bürünme izin verecek şekilde ayarlamanız gerekir. Son olarak, hizmette yapılandırmanız gereken <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> ayarlamak için davranış `ImpersonateCallerForAllOperations` için `true`. Yönlendirme hizmeti ile kimliğe bürünme etkin iletilerini yönlendirmede istemcileri oluşturma karar vermek için bu bayrağı kullanır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İleti Filtreleri](../../../../docs/framework/wcf/feature-details/message-filters.md)  
 [Anlaşmaları Yönlendirme](../../../../docs/framework/wcf/feature-details/routing-contracts.md)  
 [Filtre Seçme](../../../../docs/framework/wcf/feature-details/choosing-a-filter.md)
