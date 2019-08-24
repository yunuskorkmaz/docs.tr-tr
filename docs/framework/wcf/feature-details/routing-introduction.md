---
title: Yönlendirme Tanıtımı
ms.date: 03/30/2017
ms.assetid: bf6ceb38-6622-433b-9ee7-f79bc93497a1
ms.openlocfilehash: eaf09c0d724521c3c69fde0e90ecd7cd5aadb253
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988674"
---
# <a name="routing-introduction"></a>Yönlendirme Tanıtımı
Yönlendirme hizmeti ileti içeriğine göre iletileri yönlendirme yeteneğine sahip genel bir takılabilir SOAP aracı sağlar. Yönlendirme hizmeti ile hizmet toplama, hizmet sürümü oluşturma, öncelik yönlendirme ve çok noktaya yayın yönlendirme gibi senaryolar uygulamanıza olanak tanıyan karmaşık yönlendirme mantığı oluşturabilirsiniz. Yönlendirme hizmeti Ayrıca, birincil hedef uç noktasına gönderilirken bir hata oluşursa gönderilecek olan yedekleme uç noktaları listesini ayarlamanıza olanak tanıyan hata işleme sağlar.  
  
 Bu konu, yönlendirme hizmeti için yeni olanlar için tasarlanmıştır ve temel yapılandırmayı ve yönlendirme hizmetinin barındırılmasını içerir.  
  
## <a name="configuration"></a>Yapılandırma  
 Yönlendirme hizmeti, istemci uygulamalarından ileti alan ve iletileri bir veya daha fazla hedef uç noktaya yönlendiren bir veya daha fazla hizmet uç noktası sunan bir WCF hizmeti olarak uygulanır. Hizmet, hizmet tarafından <xref:System.ServiceModel.Routing.RoutingBehavior>sunulan hizmet uç noktalarına uygulanan bir sağlar. Bu davranış, hizmetin nasıl çalıştığı hakkında çeşitli yönleri yapılandırmak için kullanılır. Yapılandırma dosyası kullanılırken yapılandırma kolaylığı için, parametreler **RoutingBehavior**üzerinde belirtilir. Kod tabanlı senaryolarda, bu parametreler bir <xref:System.ServiceModel.Routing.RoutingConfiguration> nesnenin parçası olarak belirtilir ve daha sonra bir **RoutingBehavior**'a geçirilebilirler.  
  
 Bu davranış, başlatıldığında, istemci uç <xref:System.ServiceModel.Routing.SoapProcessingBehavior>noktalarına iletilerin SOAP işlemesini gerçekleştirmek için kullanılan öğesini ekler. Bu, yönlendirme hizmetinin ileti alındığı uç noktadan farklı bir **MessageVersion** gerektiren uç noktalara ileti aktarmasına olanak sağlar. **RoutingBehavior** Ayrıca, çalışma zamanında yönlendirme hizmeti yapılandırmasını değiştirmek <xref:System.ServiceModel.Routing.RoutingExtension>için bir erişilebilirlik noktası sağlayan bir hizmet uzantısı kaydeder.  
  
 **RoutingConfiguration** sınıfı, yönlendirme hizmeti yapılandırmasını yapılandırmak ve güncelleştirmek için tutarlı bir yol sağlar.  Yönlendirme hizmeti için ayarlar olarak davranan ve hizmet başlatıldığında **RoutingBehavior** 'ı yapılandırmak için kullanılan ve çalışma zamanında yönlendirme yapılandırmasını değiştirmek Için **RoutingExtension** 'a geçirilen parametreleri içerir.  
  
 İletilerin içerik tabanlı yönlendirilmesini gerçekleştirmek için kullanılan yönlendirme mantığı, birden çok <xref:System.ServiceModel.Dispatcher.MessageFilter> nesneyi filtre tablolarında (<xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> nesneler) birlikte gruplandırarak tanımlanır. Gelen iletiler, filtre tablosunda bulunan ileti filtrelerine ve bir hedef uç noktaya iletilen iletiyle eşleşen her **MessageFilter** için değerlendirilir. İletileri yönlendirmek için kullanılması gereken filtre tablosu, yapılandırma veya **RoutingConfiguration** nesnesi kullanılarak kod aracılığıyla yönlendirme **davranışı** kullanılarak belirtilir.  
  
### <a name="defining-endpoints"></a>Uç noktaları tanımlama  
 Kullanacağınız yönlendirme mantığını tanımlayarak yapılandırmanızı başlatmanız gerektiği gibi görünse de, ilk adımınız ileti yönlendirdiğiniz uç noktaların şeklini belirlemektir, gerçekten yapmanız gerekir. Yönlendirme hizmeti, iletileri almak ve göndermek için kullanılan kanalların şeklini tanımlayan sözleşmeleri kullanır ve bu nedenle, giriş kanalının şekli çıkış kanalının ile aynı olmalıdır.  Örneğin, istek-yanıt kanalı şeklini kullanan uç noktalara yönlendirmeniz durumunda, gelen uç noktalarında, gibi <xref:System.ServiceModel.Routing.IRequestReplyRouter>uyumlu bir anlaşma kullanmanız gerekir.  
  
 Yani, hedef uç noktalarınız birden çok iletişim deseniyle (tek yönlü ve iki yönlü işlemleri karıştırma gibi) sözleşmeler kullanıyorsa, bunlara ileti alabilen ve bunlara yönlendirebileceği tek bir hizmet uç noktası oluşturamazsınız. Hangi uç noktaların uyumlu şekillere sahip olduğunu ve hedef uç noktalara yönlendirilmek üzere ileti almak için kullanılacak bir veya daha fazla hizmet uç noktası tanımlanacağını belirlemelisiniz.  
  
> [!NOTE]
> Birden çok iletişim deseni (tek yönlü ve iki yönlü işlemlerin karışımı gibi) belirten sözleşmelerle çalışırken, bir geçici çözüm, yönlendirme hizmetinde, gibi <xref:System.ServiceModel.Routing.IDuplexSessionRouter>bir çift yönlü sözleşme kullanmaktır. Ancak bu, bağlamanın çift yönlü iletişim özelliği olması gerektiği anlamına gelir. Bu, tüm senaryolarda mümkün olmayabilir. Bunun mümkün olmadığı senaryolarda, iletişimin birden çok uç noktaya düzenleme veya uygulamanın değiştirilmesi gerekebilir.  
  
 Yönlendirme sözleşmeleri hakkında daha fazla bilgi için bkz. [yönlendirme sözleşmeleri](routing-contracts.md).  
  
 Hizmet uç noktası tanımlandıktan sonra, belirli bir **RoutingConfiguration** 'ı uç noktayla Ilişkilendirmek Için **RoutingBehavior** 'ı kullanabilirsiniz. Yönlendirme hizmetini bir yapılandırma dosyası kullanarak yapılandırırken, bu uç noktada alınan iletileri işlemek için kullanılan yönlendirme mantığını içeren filtre tablosunu belirtmek için **RoutingBehavior** kullanılır. Yönlendirme hizmetini programlı olarak yapılandırıyorsanız, **RoutingConfiguration**kullanarak filtre tablosunu belirtebilirsiniz.  
  
 Aşağıdaki örnek, yönlendirme hizmeti tarafından hem programlı olarak hem de bir yapılandırma dosyası kullanılarak kullanılan hizmet ve istemci uç noktalarını tanımlar.  
  
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
  
 Bu örnek `http://localhost:8000/routingservice/router`, yönlendirme hizmetini yönlendirilen iletileri almak için kullanılan adresine sahip tek bir uç noktayı kullanıma sunmak üzere yapılandırır. İletiler istek-yanıt uç noktalarına yönlendirildiğinden, hizmet uç noktası <xref:System.ServiceModel.Routing.IRequestReplyRouter> sözleşmeyi kullanır. Bu yapılandırma ayrıca iletilerin yönlendirildiği tek bir istemci uç `http://localhost:8000/servicemodelsample/service` noktasını tanımlar. "RoutingTable1" adlı Filtre tablosu (gösterilmez), iletileri yönlendirmek için kullanılan yönlendirme mantığını içerir ve **RoutingBehavior** (bir yapılandırma dosyası için) veya **RoutingConfiguration** (için) kullanılarak hizmet uç noktasıyla ilişkilendirilir ( programlı yapılandırma).  
  
### <a name="routing-logic"></a>Yönlendirme mantığı  
 İletileri yönlendirmek için kullanılan yönlendirme mantığını tanımlamak için, gelen iletilerde bulunan verilerin üzerinde benzersiz olarak işlem yapabileceğini belirlemelisiniz. Örneğin, tüm hedef uç noktaları aynı SOAP eylemlerini paylaşmak üzere yönlendirdiğiniz takdirde, ileti içinde yer alan eylemin değeri iletinin hangi belirli uç noktada yönlendirildiğini belirten iyi bir göstergedir. İletileri belirli bir uç noktaya benzersiz bir şekilde yönlendirmelisiniz, iletinin yönlendirildiği hedef uç noktayı benzersiz şekilde tanımlayan verileri filtrelemeniz gerekir.  
  
 Yönlendirme hizmeti, ileti içindeki adres, eylem, uç nokta adı ve hatta bir XPath sorgusu gibi belirli değerleri denetleyen çeşitli **MessageFilter** uygulamaları sağlar. Bu uygulamalardan hiçbiri gereksinimlerinizi karşılamıyorsa, özel bir **MessageFilter** uygulaması oluşturabilirsiniz. İleti filtreleri ve yönlendirme hizmeti tarafından kullanılan uygulamaların karşılaştırması hakkında daha fazla bilgi için bkz. [Ileti filtreleri](message-filters.md) ve [bir filtre seçme](choosing-a-filter.md).  
  
 Birden çok ileti filtresi, her **MessageFilter** öğesini bir hedef uç noktasıyla ilişkilendiren filtre tablolarında birlikte düzenlenir. İsteğe bağlı olarak, bir aktarım hatası durumunda yönlendirme hizmetinin iletiyi göndermek için deneyeceği yedek uç noktaların listesini belirtmek için filtre tablosu da kullanılabilir.  
  
 Varsayılan olarak, bir filtre tablosu içindeki tüm ileti filtreleri aynı anda değerlendirilir; Ancak, ileti filtrelerinin belirli bir <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement.Priority%2A> sırada değerlendirilmesini sağlayan bir de belirtebilirsiniz. En yüksek önceliğe sahip tüm girişler önce değerlendirilir ve daha yüksek bir öncelik düzeyinde eşleşme bulunursa düşük önceliklerdeki ileti filtreleri değerlendirilmez. Filtre tabloları hakkında daha fazla bilgi için bkz. [Ileti filtreleri](message-filters.md).  
  
 Aşağıdaki örneklerde, tüm iletiler <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> `true` için değerlendirilen ' kullanılır. Bu **MessageFilter** , "routingTable1" filtre tablosuna eklenir ve bu, **MessageFilter** öğesini "hesaplatorservice" adlı istemci uç noktasıyla ilişkilendirir. **RoutingBehavior** daha sonra bu tablonun hizmet uç noktası tarafından işlenen iletileri yönlendirmek için kullanılması gerektiğini belirtir.  
  
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
> Varsayılan olarak, yönlendirme hizmeti yalnızca iletinin üstbilgilerini değerlendirir. Filtrelerin ileti gövdesine erişmesine izin vermek için, olarak <xref:System.ServiceModel.Routing.RoutingConfiguration.RouteOnHeadersOnly%2A> `false`ayarlamanız gerekir.  
  
 **Noktalı**  
  
 Birçok yönlendirme hizmeti yapılandırması iletileri yalnızca belirli bir uç noktaya yönlendiren özel durum filtre mantığı kullanır, ancak belirli bir iletiyi birden çok hedef uç noktaya yönlendirmenize gerek vardır. Bir iletinin birden çok hedefe çok noktaya yayını olması için aşağıdaki koşulların doğru olması gerekir:  
  
- İstek yanıtındaki istemci uygulaması tarafından yalnızca bir yanıt alınabileceğinden, kanal şeklinin istek Yanıtla (ancak tek yönlü veya çift yönlü olabilir) olması gerekir.  
  
- İleti değerlendirilirken birden çok `true` filtrenin dönmesi gerekir.  
  
 Bu koşullar karşılanıyorsa ileti, ' i değerlendiren `true`tüm filtrelerin tüm uç noktalarına yönlendirilir. Aşağıdaki örnek, iletideki bitiş noktası adresi olduğunda, `http://localhost:8000/routingservice/router/rounding`iletilerin her iki uç noktaya yönlendirilmesine neden olan bir yönlendirme yapılandırmasını tanımlar.  
  
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
  
### <a name="soap-processing"></a>SOAP Işleme  
 Farklı protokoller arasında ileti yönlendirmeyi desteklemek için, varsayılan olarak **RoutingBehavior** , <xref:System.ServiceModel.Routing.SoapProcessingBehavior> iletilerinin yönlendirildiği tüm istemci uç noktalara ekler. Bu davranış, iletiyi uç noktaya yönlendirmeden önce otomatik olarak yeni bir **MessageVersion** oluşturur, Ayrıca, istenen istemci uygulamasına döndürmeden önce herhangi bir yanıt belgesi için uyumlu bir **MessageVersion** oluşturma.  
  
 Giden ileti için yeni bir **MessageVersion** oluşturmak için uygulanan adımlar aşağıdaki gibidir:  
  
 **İstek işleme**  
  
- Giden bağlamanın/kanalın **MessageVersion** 'ı alın.  
  
- Özgün ileti için gövde okuyucuyu alın.  
  
- Aynı eylem, gövde okuyucu ve yeni bir **MessageVersion**ile yeni bir ileti oluşturun.  
  
- Eğer <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> ! = **Addressing. None**ise, to, from, FaultTo ve RelatesTo üst bilgilerini yeni iletiye kopyalayın.  
  
- Tüm ileti özelliklerini yeni iletiye kopyalayın.  
  
- Yanıtı işlerken kullanılacak özgün istek iletisini depolayın.  
  
- Yeni istek iletisini döndürün.  
  
 **Yanıt işleme**  
  
- Özgün istek iletisinin **MessageVersion** 'sini alın.  
  
- Alınan yanıt iletisi için gövde okuyucuyu alın.  
  
- Aynı eylem, gövde okuyucu ve özgün istek iletisinin **MessageVersion** ile yeni bir yanıt iletisi oluşturun.  
  
- Eğer <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> ! = **Addressing. None**ise, to, from, FaultTo ve RelatesTo üst bilgilerini yeni iletiye kopyalayın.  
  
- İleti özelliklerini yeni iletiye kopyalayın.  
  
- Yeni yanıt iletisini döndürün.  
  
 Varsayılan olarak, **SoapProcessingBehavior** , hizmet başladığında istemci uç noktalarına <xref:System.ServiceModel.Routing.RoutingBehavior> otomatik olarak eklenir; ancak, <xref:System.ServiceModel.Routing.RoutingConfiguration.SoapProcessingEnabled%2A> özelliğini kullanarak soap işlemenin tüm istemci uç noktalarına eklenip eklenmeyeceğini kontrol edebilirsiniz. . Ayrıca, daha ayrıntılı bir SOAP işleme denetimi gerekiyorsa, davranışı doğrudan belirli bir uç noktaya ekleyebilir ve uç nokta düzeyinde bu davranışı etkinleştirebilir veya devre dışı bırakabilirsiniz.  
  
> [!NOTE]
> SOAP işleme, özgün istek iletisinden farklı bir MessageVersion gerektiren bir uç nokta için devre dışı bırakılmışsa, iletiyi ileti gönderilmeden önce gereken SOAP değişikliklerinin gerçekleştirilmesi için özel bir mekanizma sağlamanız gerekir. hedef uç nokta.  
  
 Aşağıdaki örneklerde SoapProcessingEnabled özelliği, **SoapProcessingBehavior** 'ın tüm istemci uç noktalarına otomatik olarak eklenmesini engellemek için kullanılır.  
  
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
 Ek istemci uç noktaları eklediğinizde veya iletileri yönlendirmek için kullanılan filtreleri değiştirmeniz gerekiyorsa, hizmetin Şu anda iletileri aldığı uç noktalara engel olmak için yapılandırmayı çalışma zamanında dinamik olarak güncelleştirmeniz için bir yola sahip olmanız gerekir. Yönlendirme hizmeti. Bir yapılandırma dosyasını veya ana bilgisayar uygulamasının kodunu değiştirmek her zaman yeterli değildir çünkü her iki yöntem de uygulamanın geri dönüşümünü gerektirir, bu da şu anda aktarımda olan iletilerin olası kaybına ve kapalı kalma süresine yol açabilir. hizmetin yeniden başlatılması bekleniyor.  
  
 **RoutingConfiguration** 'ı yalnızca programlı olarak değiştirebilirsiniz. Hizmeti ilk olarak bir yapılandırma dosyası kullanarak yapılandırabilmeniz mümkün olsa da, yalnızca yeni bir **RoutingConfiguration** oluşturarak ve onu bir parametre <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A>olarak <xref:System.ServiceModel.Routing.RoutingExtension>hizmet uzantısı. Şu anda yoldaki tüm iletiler önceki yapılandırma kullanılarak yönlendirilmeye devam ederken, **ApplyConfiguration** çağrısından sonra alınan iletiler yeni yapılandırmayı kullanır. Aşağıdaki örnek, yönlendirme hizmeti 'nin bir örneğini oluşturmayı ve sonra yapılandırmayı değiştirmeyi gösterir.  
  
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
> Yönlendirme hizmeti bu şekilde güncelleştirilirken yalnızca yeni bir yapılandırma geçirmek mümkündür. Geçerli yapılandırmanın yalnızca seçim öğelerini değiştirmek veya geçerli yapılandırmaya yeni girişler eklemek mümkün değildir; var olan bir yapılandırmayı oluşturup yeni bir yapılandırma geçirmeniz gerekir.  
  
> [!NOTE]
> Önceki yapılandırma kullanılarak açılan oturumlar önceki yapılandırmayı kullanmaya devam eder. Yeni yapılandırma yalnızca yeni oturumlar tarafından kullanılır.  
  
## <a name="error-handling"></a>Hata İşleme  
 İleti gönderilmeye <xref:System.ServiceModel.CommunicationException> çalışılırken herhangi bir hatayla karşılaşırsanız, hata işleme gerçekleşir. Bu özel durumlar genellikle <xref:System.ServiceModel.EndpointNotFoundException>, <xref:System.ServiceModel.ServerTooBusyException>veya <xref:System.ServiceModel.CommunicationObjectFaultedException>gibi tanımlı istemci uç noktasıyla iletişim kurmaya çalışırken bir sorunla karşılaşıldığını gösterir. Hata işleme-kod ayrıca, bir <xref:System.TimeoutException> durum oluştuğunda, **CommunicationException**'dan türetilmeyen başka bir ortak özel durum olduğunda göndermeyi yeniden denemeye çalışır.  
  
 Yukarıdaki özel durumlardan biri gerçekleştiğinde, yönlendirme hizmeti yedekleme uç noktaları listesine yük devreder. Tüm yedekleme uç noktaları bir iletişim hatasıyla başarısız olursa veya bir uç nokta hedef hizmette bir hata olduğunu gösteren bir özel durum döndürürse, yönlendirme hizmeti istemci uygulamasına bir hata döndürür.  
  
> [!NOTE]
> Hata işleme işlevselliği, bir ileti gönderilirken ve bir kanalı kapatmaya çalışırken oluşan özel durumları yakalar ve işler. Hata işleme kodu, iletişim kurduğu uygulama uç noktaları tarafından oluşturulan özel durumları algılamaya veya işlemeye yönelik değildir; bir <xref:System.ServiceModel.FaultException> hizmet tarafından oluşturulan bir durum, yönlendirme hizmetinde bir **FaultMessage** olarak görünür ve istemciye geri gönderilir.  
>   
>  Yönlendirme hizmeti bir iletiyi geçirmeye çalıştığında bir hata oluşursa, normalde yönlendirme hizmeti yokluğunda olmak yerine <xref:System.ServiceModel.FaultException> <xref:System.ServiceModel.EndpointNotFoundException> istemci tarafında bir alabilirsiniz. Bu nedenle, iç içe özel durumları incelemeden bir yönlendirme hizmeti özel durumları maskeleyebilir ve tam saydamlık sağlamaz.  
  
### <a name="tracing-exceptions"></a>Özel durumları izleme  
 Bir listedeki uç noktaya ileti gönderilirken, yönlendirme hizmeti elde edilen özel durum verilerini izler ve özel durum ayrıntılarını özel **durumlar**adlı bir ileti özelliği olarak ekler. Bu, özel durum verilerini korur ve bir kullanıcı tarafından ileti denetçisi aracılığıyla programlı erişim sağlar.  Özel durum verileri, bir ileti gönderilmeye çalışırken karşılaşılan özel durum ayrıntılarıyla eşleşen bir sözlükte ileti başına depolanır.  
  
### <a name="backup-endpoints"></a>Yedekleme uç noktaları  
 Filtre tablosu içindeki her bir filtre girişi, isteğe bağlı olarak, birincil uç noktaya gönderilirken bir iletim hatası durumunda kullanılan yedekleme uç noktaları listesini belirtebilir. Böyle bir hata oluşursa, yönlendirme hizmeti iletiyi yedekleme uç noktası listesindeki ilk girişe aktarmaya çalışır. Bu gönderme girişimi de bir iletim hatasıyla karşılaşırsa, yedekleme listesindeki bir sonraki uç nokta denenir. Yönlendirme hizmeti, ileti başarılı bir şekilde alınana kadar iletiyi listedeki her bir uç noktaya göndermeye devam eder, tüm uç noktalar bir iletim hatası döndürmez veya bir uç nokta tarafından iletim dışı bir hata döndürülür.  
  
 Aşağıdaki örnekler, yönlendirme hizmetini bir yedekleme listesi kullanacak şekilde yapılandırır.  
  
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
 Aşağıdaki tabloda, yedekleme uç noktası listelerinin kullanımıyla uyumlu desenler ve belirli desenler için hata işlemenin ayrıntılarını açıklayan notlar açıklanmaktadır.  
  
|Desen|Oturum|İşlem|Alma bağlamı|Yedekleme listesi destekleniyor|Notlar|  
|-------------|-------------|-----------------|---------------------|---------------------------|-----------|  
|Tek Yönlü||||Evet|İletiyi bir yedekleme uç noktasında yeniden göndermeye çalışır. Bu ileti çok noktaya yayın ise, yalnızca başarısız olan kanaldaki ileti yedekleme hedefine taşınır.|  
|Tek Yönlü||✓||Hayır|Bir özel durum oluşturulur ve işlem geri alınır.|  
|Tek Yönlü|||✓|Evet|İletiyi bir yedekleme uç noktasında yeniden göndermeye çalışır. İleti başarıyla alındıktan sonra tüm alma bağlamlarını doldurun. İleti herhangi bir uç nokta tarafından başarıyla alınmıyorsa, alma bağlamını tamamlamayın.<br /><br /> Bu ileti çok noktaya yayın olduğunda, alma bağlamı yalnızca ileti en az bir uç nokta (birincil veya yedek) tarafından başarıyla alınmışsa tamamlanır. Çok noktaya yayın yollarındaki uç noktaların hiçbiri iletiyi başarıyla aldıysanız, alma bağlamını tamamlamayın.|  
|Tek Yönlü||✓|✓|Evet|Önceki işlemi iptal edin, yeni bir işlem oluşturun ve tüm iletileri yeniden gönderin. Bir hatayla karşılaşan iletiler bir yedekleme hedefine iletilir.<br /><br /> Tüm iletimlerin başarılı olduğu bir işlem oluşturulduktan sonra alma bağlamlarını tamamlayıp işlemi yürütün.|  
|Tek Yönlü|✓|||Evet|İletiyi bir yedekleme uç noktasında yeniden göndermeye çalışır. Çok noktaya yayın senaryosunda yalnızca bir oturumdaki veya oturum kapatma başarısız olan bir oturumdaki iletiler yedekleme hedeflerine yeniden gönderilir.|  
|Tek Yönlü|✓|✓||Hayır|Bir özel durum oluşturulur ve işlem geri alınır.|  
|Tek Yönlü|✓||✓|Evet|İletiyi bir yedekleme uç noktasında yeniden göndermeye çalışır. Tüm iletiler hatasız tamamlandı, oturum daha fazla ileti olmadığını ve yönlendirme hizmeti tüm giden oturum kanallarını başarıyla kapatmışsa, tüm alma bağlamlarının tamamlandığı ve gelen oturum kanalının kapalı olması gerekir.|  
|Tek Yönlü|✓|✓|✓|Evet|Geçerli işlemi iptal edin ve yeni bir tane oluşturun. Oturumdaki tüm önceki iletileri yeniden gönderin. Tüm iletilerin başarıyla gönderildiği ve oturum daha fazla ileti olmadığını gösterdiği bir işlem oluşturulduktan sonra, tüm giden oturum kanalları kapatılır, alma bağlamlarının tümü işlemle tamamlanır, gelen oturum kanalı kapalı ve işlem kaydedildi.<br /><br /> Oturumlar çok noktaya yayın yaparken, hatasız bir hata olmayan mesajlar daha önce olduğu gibi aynı hedefe gönderilir ve bir hatayla karşılaşan iletiler yedekleme hedeflerine gönderilir.|  
|İki yönlü||||Evet|Bir yedekleme hedefine gönderin.  Bir kanal yanıt iletisi döndürdüğünde, yanıtı özgün istemciye döndürün.|  
|İki yönlü|✓|||Evet|Kanaldaki tüm iletileri bir yedekleme hedefine gönderin.  Bir kanal yanıt iletisi döndürdüğünde, yanıtı özgün istemciye döndürün.|  
|İki yönlü||✓||Hayır|Bir özel durum oluşturulur ve işlem geri alınır.|  
|İki yönlü|✓|✓||Hayır|Bir özel durum oluşturulur ve işlem geri alınır.|  
|Çift Yönlü||||Hayır|Oturum olmayan çift yönlü iletişim şu anda desteklenmiyor.|  
|Çift Yönlü|✓|||Evet|Bir yedekleme hedefine gönderin.|  
  
## <a name="hosting"></a>Barındırma  
 Yönlendirme hizmeti bir WCF hizmeti olarak uygulandığından, bir uygulama içinde kendi kendine barındırılan veya IIS ya da WAS tarafından barındırılan olmalıdır. Bu barındırma ortamlarında sunulan otomatik başlatma ve yaşam döngüsü yönetim özelliklerinden yararlanmak için yönlendirme hizmetinin IIS, WAS veya bir Windows hizmet uygulamasında barındırılması önerilir.  
  
 Aşağıdaki örnek, bir uygulamada yönlendirme hizmetinin barındırılmasını gösterir.  
  
```csharp  
using (ServiceHost serviceHost =  
                new ServiceHost(typeof(RoutingService)))  
```  
  
 Yönlendirme hizmetini IIS veya WAS içinde barındırmak için bir hizmet dosyası (. svc) oluşturmanız ya da hizmetin yapılandırma tabanlı etkinleştirmesini kullanmanız gerekir. Bir hizmet dosyası kullanırken, hizmet parametresini <xref:System.ServiceModel.Routing.RoutingService> kullanarak belirtmeniz gerekir. Aşağıdaki örnek, yönlendirme hizmetini IIS veya WAS ile barındırmak için kullanılabilecek örnek bir hizmet dosyası içerir.  
  
```  
<%@ ServiceHost Language="C#" Debug="true" Service="System.ServiceModel.Routing.RoutingService,   
     System.ServiceModel.Routing, version=4.0.0.0, Culture=neutral,   
     PublicKeyToken=31bf3856ad364e35" %>  
```  
  
## <a name="routing-service-and-impersonation"></a>Yönlendirme hizmeti ve kimliğe bürünme  
 WCF yönlendirme hizmeti, hem gönderme hem de alma iletileri için kimliğe bürünme ile kullanılabilir. Kimliğe bürünme için tüm olağan Windows kısıtlamaları geçerlidir. Kendi hizmetinizi yazarken kimliğe bürünme özelliğini kullanmak üzere hizmet veya hesap izinleri ayarlamanız gerekiyorsa, yönlendirme hizmeti ile kimliğe bürünme özelliğini kullanmak için bu adımları uygulamanız gerekir. Daha fazla bilgi için bkz. [temsil ve kimliğe bürünme](delegation-and-impersonation-with-wcf.md).  
  
 Yönlendirme hizmeti ile kimliğe bürünme, ASP.NET uyumluluk modundayken ASP.NET Kimliğe bürünme özelliğinin kullanımını veya kimliğe bürünmeye izin verecek şekilde yapılandırılmış Windows kimlik bilgilerinin kullanılmasını gerektirir. ASP.NET uyumluluk modu hakkında daha fazla bilgi için bkz. [WCF Hizmetleri ve ASP.net](wcf-services-and-aspnet.md).  
  
> [!WARNING]
> WCF yönlendirme hizmeti temel kimlik doğrulamasıyla kimliğe bürünme özelliğini desteklemiyor.  
  
 Yönlendirme hizmeti ile ASP.NET Kimliğe bürünme özelliğini kullanmak için hizmet barındırma ortamında ASP.NET uyumluluk modunu etkinleştirin. Yönlendirme hizmeti zaten ASP.NET uyumluluk moduna izin vermek üzere işaretlendi ve kimliğe bürünme otomatik olarak etkinleştirilir. Kimliğe bürünme, ASP.NET tümleştirmesi 'nin yönlendirme hizmeti ile desteklenen tek kullanımı.  
  
 Windows kimlik bilgisi kimliğe bürünme özelliğini yönlendirme hizmeti ile birlikte kullanmak için hem kimlik bilgilerini hem de hizmeti yapılandırmanız gerekir. İstemci kimlik bilgileri nesnesi (<xref:System.ServiceModel.Security.WindowsClientCredential>, <xref:System.ServiceModel.ChannelFactory>öğesinden çözümlenemeyen), kimliğe bürünmeye <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> izin vermek için ayarlanması gereken bir özelliği tanımlar. Son olarak, hizmette olarak <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> `true`ayarlanacak `ImpersonateCallerForAllOperations` davranışı yapılandırmanız gerekir. Yönlendirme hizmeti, kimliğe bürünme özelliği etkinken iletileri iletmek için istemciler oluşturulup oluşturulmayacağını belirlemek için bu bayrağı kullanır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İleti Filtreleri](message-filters.md)
- [Anlaşmaları Yönlendirme](routing-contracts.md)
- [Filtre Seçme](choosing-a-filter.md)
