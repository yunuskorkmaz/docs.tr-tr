---
title: 'Nasıl yapılır: Filtreleri Kullanma'
ms.date: 03/30/2017
ms.assetid: f2c7255f-c376-460e-aa20-14071f1666e5
ms.openlocfilehash: aee0f2e4fbf3b4e0802803b76aa557f2dec668bb
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2018
ms.locfileid: "48245198"
---
# <a name="how-to-use-filters"></a>Nasıl yapılır: Filtreleri Kullanma
Bu konuda, birden çok filtre kullanan yönlendirme yapılandırması oluşturma için gerekli temel adımlar açıklanmaktadır. Bu örnekte, iki hesap makinesi hizmeti, regularCalc ve roundingCalc uygulamaları için iletileri yönlendirilir. Hem uygulamalar aynı işlemleri desteği: Ancak bir hizmet, döndürmeden önce tüm hesaplamalar en yakın tamsayı değerine yuvarlanır. Bir istemci uygulaması yuvarlama sürüm hizmetinin kullanılıp kullanılmayacağını belirtmek için bir değer olmalıdır; hiçbir hizmet tercihi ifade, ileti iki hizmet arasında yük dengeli yoktur. Her iki hizmet tarafından sunulan işlemleri şunlardır:  
  
-   Ekle  
  
-   Çıkarma  
  
-   Çarp  
  
-   Bölme  
  
 Her iki hizmet de aynı işlemleri uygulamak için eylem filtresi kullanamazsınız, çünkü message içinde belirtilen eylem benzersiz olmayacaktır. Bunun yerine iletileri uygun Uç noktalara yönlendirilir emin olmak için ek bir iş yapmanız gerekir.  
  
### <a name="determine-unique-data"></a>Benzersiz veri belirleme  
  
1.  Her iki hizmet uygulamalarını aynı işlemleri işlemek ve dışında döndürmeleri veri temel olarak aynı olduğundan, istemci uygulamalarından gönderilen iletileri bulunan temel verileri nasıl yönlendirileceğini belirlemek olanak tanımak için benzersiz değil İstek. Ancak daha sonra istemci uygulama bir benzersiz üstbilgi değerini ekler, ileti nasıl yönlendirileceğini belirlemek için bu değeri kullanabilirsiniz.  
  
     İstemci uygulaması yuvarlama hesaplayıcı tarafından işlenecek ileti gerekiyorsa bu örnek için bir özel üst bilgi aşağıdaki kodu kullanarak ekler:  
  
    ```csharp  
    messageHeadersElement.Add(MessageHeader.CreateHeader("RoundingCalculator",   
                                   "http://my.custom.namespace/", "rounding"));  
    ```  
  
     Artık bu üst bilgi iletilerini incelemek için XPath filtreyi kullanın ve roundCalc hizmetine üstbilgisini içeren iletiler yönlendirebilirsiniz.  
  
2.  Ayrıca yönlendirme hizmeti EndpointAddress, Uçnoktaadı ile kullanılabilecek iki sanal hizmet uç noktalarını kullanıma sunar veya PrefixEndpointAddress benzersiz uç noktasına göre belirli hesaplayıcı uygulamasına gelen iletileri yönlendirmek için filtreler için istemci uygulaması isteği gönderir.  
  
### <a name="define-endpoints"></a>Uç noktalarını tanımlayın  
  
1.  Yönlendirme hizmeti tarafından kullanılan uç noktalarını tanımlarken, istemcileri ve Hizmetleri tarafından kullanılan kanal şeklini ilk belirlemeniz gerekir. Bu senaryoda, her iki hedef hizmetler bir istek-yanıt deseni kullanır. böylece <xref:System.ServiceModel.Routing.IRequestReplyRouter> kullanılır. Aşağıdaki örnek, yönlendirme hizmeti tarafından kullanıma sunulan hizmet uç noktalarını tanımlar.  
  
    ```xml  
    <services>  
          <service behaviorConfiguration="routingConfiguration"  
                   name="System.ServiceModel.Routing.RoutingService">  
            <host>  
              <baseAddresses>  
                <add baseAddress="http://localhost/routingservice/router" />  
              </baseAddresses>  
            </host>  
            <!--Set up the inbound endpoints for the Routing Service-->  
            <!--first create the general router endpoint-->  
            <endpoint address="general"  
                      binding="wsHttpBinding"  
                      name="routerEndpoint"  
                      contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
            <!--create a virtual endpoint for the regular calculator service-->  
            <endpoint address="regular/calculator"  
                      binding="wsHttpBinding"  
                      name="calculatorEndpoint"  
                      contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
            <!--now create a virtual endpoint for the rounding calculator-->  
            <endpoint address="rounding/calculator"  
                      binding="wsHttpBinding"  
                      name="roundingEndpoint"  
                      contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
  
          </service>  
    </services>  
    ```  
  
     Bu yapılandırma ile yönlendirme hizmeti, üç ayrı uç noktalarını kullanıma sunar. Çalışma zamanı seçimlere bağlı olarak, istemci uygulama iletileri bu adreslerden birini gönderir. ("Yuvarlama/hesaplayıcı" veya "normal/hesaplayıcı") "sanal" hizmet uç noktalardan biri gelen iletiler için karşılık gelen hesaplayıcısı uygulaması iletilir. İstemci uygulama, belirli bir uç noktaya istek göndermediği durumlarda ileti genel uç noktaya değinilmiştir. Seçilen uç nokta bağımsız olarak, istemci uygulaması, yuvarlama hesaplayıcı uygulamasına iletinin iletileceği belirtmek için özel üst bilgi eklemeyi de seçebilirler.  
  
2.  Aşağıdaki örnek, yönlendirme hizmeti, iletileri yönlendirir. (hedef) istemci uç noktalarını tanımlar.  
  
    ```xml  
    <client>  
          <endpoint name="regularCalcEndpoint"  
                    address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                    binding="netTcpBinding"  
                    contract="*" />  
  
          <endpoint name="roundingCalcEndpoint"  
                    address="net.tcp://localhost:8080/servicemodelsamples/service/"  
                    binding="netTcpBinding"  
                    contract="*" />  
    </client>  
    ```  
  
     Bu uç noktaları, filtre tablosunda, mesajın gönderilip gönderilmediği özgü süzgeçler eşleştiğinde hedef uç nokta belirtmek için kullanılır.  
  
### <a name="define-filters"></a>Filtreleri tanımlar  
  
1.  İstemci uygulaması ekler "RoundingCalculator" özel üst bilgi temel iletileri yönlendirmek için bu üst bilgisi varlığını denetlemek için bir XPath sorgusu kullanan bir filtre tanımlar. Ayrıca özel bir ad alanı kullanarak bu başlığı tanımlı olduğundan, XPath sorgusundaki "kullanılan özel" bir özel ad alanı öneki tanımlayan bir ad alanı girişi ekleyin. Aşağıdaki örnek, gerekli yönlendirme bölümünde, ad alanı tablosu ve XPath filtresi tanımlar.  
  
    ```xml  
    <routing>  
          <!-- use the namespace table element to define a prefix for our custom namespace-->  
          <namespaceTable>  
            <add prefix="custom" namespace="http://my.custom.namespace/"/>  
          </namespaceTable>  
          <filters>  
            <!--define the different message filters-->  
            <!--define an xpath message filter to look for the custom header coming from the client-->  
            <filter name="XPathFilter" filterType="XPath"   
                    filterData="/s12:Envelope/s12:Header/custom:RoundingCalculator = 'rounding'"/>  
          </filters>  
    </routing>  
    ```  
  
     Bu **MessageFilter** RoundingCalculator başlığı "yuvarlama" bir değer içeren iletiyi arar. Bu üst bilgi iletisi roundingCalc hizmete yönlendirileceğini göstermek için istemci tarafından ayarlanır.  
  
    > [!NOTE]
    > S12 ad alanı öneki varsayılan ad alanı tablo olarak tanımlanır ve ad alanını temsil eden `http://www.w3.org/2003/05/soap-envelope`.
  
2.  Ayrıca iki sanal uç noktalarda alınan iletilerin arayın filtreleri tanımlamanız gerekir. İlk sanal uç "normal/hesaplayıcı" uç noktasıdır. İstemci istekleri ileti regularCalc hizmete yönlendirileceğini belirtmek için bu endpoint gönderebilirsiniz. Aşağıdaki yapılandırmayı kullanan bir filtre tanımlar <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> ileti filterData içinde belirtilen adla bir uç nokta gelen varsa belirlemek için.  
  
    ```xml  
    <!--define an endpoint name filter looking for messages that show up on the virtual regular calculator endpoint-->  
    <filter name="EndpointNameFilter" filterType="EndpointName" filterData="calculatorEndpoint"/>  
    ```  
  
     "CalculatorEndpoint" adlı hizmet uç noktası tarafından bir ileti alınmazsa, bu filtresinin `true`.  
  
3.  Ardından, roundingEndpoint adresine gönderilen iletileri bakan bir filtre tanımlar. İstemci istekleri ileti roundingCalc hizmete yönlendirileceğini belirtmek için bu endpoint gönderebilirsiniz. Aşağıdaki yapılandırmayı kullanan bir filtre tanımlar <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> iletinin "yuvarlama/hesaplayıcı" uç noktada geldiği varsa belirlemek için.  
  
    ```xml  
    <!--define a filter looking for messages that show up with the address prefix.  The corresponds to the rounding calc virtual endpoint-->  
    <filter name="PrefixAddressFilter" filterType="PrefixEndpointAddress"  
            filterData="http://localhost/routingservice/router/rounding/"/>  
    ```  
  
     İle başlayan bir adresteki bir ileti alındığında, `http://localhost/routingservice/router/rounding/` bu filtresinin sonra **true**. Bu yapılandırma tarafından kullanılan temel adresi olduğundan `http://localhost/routingservice/router` ve roundingEndpoint "yuvarlama/hesap makinesi" için belirtilen adres, bu uç nokta ile iletişim kurmak için kullanılan tam adresidir `http://localhost/routingservice/router/rounding/calculator`, bu filtre ile eşleşir.  
  
    > [!NOTE]
    >  PrefixEndpointAddress filtresi ana bilgisayar adı, istemci uygulamasından konağa başvuran geçerli yolu olmalıdır çünkü tek bir ana bilgisayar için tüm olabilir ve ana bilgisayar adları çeşitli kullanılarak başvurulabilen bir eşleşme gerçekleştirme değerlendirmez. Örneğin, aşağıdakilerin tümü aynı konağa başvurabilir:  
    >   
    > -   localhost  
    > -   127.0.0.1  
    > -   `www.contoso.com`  
    > -   ContosoWeb01  
  
4.  Son filtre özel üst bilgi içermeyen genel uç noktasında gelen iletileri yönlendirme desteklemesi gerekir. Bu senaryo için regularCalc ve roundingCalc hizmetleri arasında iletileri alternatif. "Hepsini bir kez deneme" Bu iletilerin yönlendirme desteklemek için bir filtre örneğini işlenen her ileti için eşleşen izin veren özel bir filtre kullanın.  Bunlar diğer arasında alternatif olduğunu belirtmek için birlikte gruplanmış bir RoundRobinMessageFilter, iki örneğini tanımlar.  
  
    ```xml  
    <!-- Set up the custom message filters.  In this example,   
         we'll use the example round robin message filter,   
         which alternates between the references-->  
    <filter name="RoundRobinFilter1" filterType="Custom"  
                    customType="CustomFilterAssembly.RoundRobinMessageFilter, CustomFilterAssembly"  
                    filterData="group1"/>  
    <filter name="RoundRobinFilter2" filterType="Custom"  
                    customType="CustomFilterAssembly.RoundRobinMessageFilter, CustomFilterAssembly"  
                    filterData="group1"/>  
    ```  
  
     Çalışma zamanı sırasında bu filtre türü, bu tür tek bir koleksiyonda aynı grup olarak yapılandırılmış tüm tanımlı filtre örnekleri arasında geçiş yapıyor. Bu alternatif döndüren arasında bu özel filtre tarafından işlenen iletilerin neden `true` için `RoundRobinFilter1` ve `RoundRobinFilter2`.  
  
### <a name="define-filter-tables"></a>Filtre tabloları tanımlama  
  
1.  Filtreler belirli istemci uç noktaları ile ilişkilendirmek için bir filtre tablosunun yerleştirmeniz gerekir. Bu örnek senaryo, filtreleri işlenme sırasını belirtmenize olanak sağlayan, isteğe bağlı bir ayardır filtre öncelik ayarlarını da kullanır. Hiçbir filtre öncelik belirtilmezse, tüm filtreleri eşzamanlı olarak değerlendirilir.  
  
    > [!NOTE]
    >  Belirtirken bir filtre önceliğine izin verir, hangi filtrelerin sırasını denetlemek için işlenen, Yönlendirme Hizmeti performansını olumsuz etkileyebilir. Filtre önceliklerin kullanımı gerekli değildir. böylece mümkün olduğunda, filtre mantığını oluşturun.  
  
     Aşağıdaki filtre tabloyu tanımlayan ve "tablosuna bir öncelik 2 ile daha önce tanımlanan XPathFilterElement" ekler. Bu giriş, ayrıca olmadığını belirtir `XPathFilter` eşleşen iletisi için ileti yönlendirilir `roundingCalcEndpoint`.  
  
    ```xml  
    <routing>  
    ...      <filters>  
    ...      </filters>  
          <filterTables>  
            <table name="filterTable1">  
              <entries>  
                <!--add the filters to the message filter table-->  
                <!--first look for the custom header, and if we find it,  
                    send the message to the rounding calc endpoint-->  
                <add filterName="XPathFilter" endpointName="roundingCalcEndpoint" priority="2"/>  
              </entries>  
            </table>  
          <filterTables>  
    </routing>  
    ```  
  
     Bir filtre öncelik belirtirken, en yüksek öncelikli filtreleri önce değerlendirilir. Belirli bir öncelik düzeyinde bir veya daha fazla filtrelerle eşleşen, en düşük öncelik düzeyleri filtre değerlendirilir. Bu senaryo için belirtilen en yüksek öncelik 2. ve bu düzeyde yalnızca filtre giriş budur.  
  
2.  Filtre girişleri, uç nokta adı veya adres ön eki inceleyerek bir ileti belirli bir noktadaki alındığında, kontrol etmek için tanımlanmadı. Aşağıdaki girdileri hem de bu filtre girişleri filtre tabloya ekleyin ve bunları için ileti yönlendirilecek hedef uç noktaları ile ilişkilendirin. Bu filtreler, önceki XPath filtresi ileti eşleşmedi varsa bunlar yalnızca çalışması gerektiğini belirtmek için bir öncelik 1 için ayarlanır.  
  
    ```xml  
    <!--if the header wasn't there, send the message based on which virtual endpoint it arrived at-->  
    <!--we determine this through the endpoint name, or through the address prefix-->  
    <add filterName="EndpointNameFilter" endpointName="regularCalcEndpoint" priority="1"/>  
    <add filterName="PrefixAddressFilter" endpointName="roundingCalcEndpoint" priority="1"/>  
    ```  
  
     Bu filtreler, filtre önceliği 1 olduğundan, bunlar öncelik düzeyi 2 sırasında filtre ileti eşleşmiyorsa yalnızca değerlendirilir. Her iki filtreleri aynı öncelik düzeyine sahip olduğundan da, bunlar aynı anda değerlendirilir. Her iki filtreleri birbirini dışlayan olduğundan, tek veya başka bir ileti eşleştirilecek mümkündür.  
  
3.  Bir ileti herhangi bir önceki süzgeçlere eşleşmiyorsa ileti genel hizmet uç noktası aracılığıyla alındı ve yönlendirmek yeri belirten hiçbir üst bilgiler. Bu iletiler, bunları iki hesaplayıcı hizmetleri arasında yük dengeleyen özel filtre tarafından işlenmesi üzeresiniz. Aşağıdaki örnek, filtre girişleri filtre tabloya eklenecek gösterilmektedir; Her bir filtrenin iki hedef uç noktalardan biri ile ilişkilidir.  
  
    ```xml  
    <!--if none of the other filters have matched,   
        this message showed up on the default router endpoint,   
        with no custom header-->  
    <!--round robin these requests between the two services-->  
    <add filterName="RoundRobinFilter1" endpointName="regularCalcEndpoint" priority="0"/>  
    <add filterName="RoundRobinFilter2" endpointName="roundingCalcEndpoint" priority="0"/>  
    ```  
  
     Bu girişler bir öncelik 0 belirttiğinden, bunlar daha yüksek bir öncelik filtre ileti eşleşiyorsa yalnızca değerlendirilir. Ayrıca, bunlar her ikisi de aynı önceliği olduğundan, eşzamanlı olarak değerlendirilir.  
  
     Daha önce belirtildiği gibi bu filtre tanımları tarafından kullanılan özel filtre yalnızca bir ya da diğer olarak değerlendirir `true` alınan her ileti için. Bu filtre ile aynı belirtilen grup ayarını kullanarak yalnızca iki filtre tanımlı olduğundan, yönlendirme hizmeti regularCalcEndpoint ve RoundingCalcEndpoint gönderme arasında diğerleri etkisidir.  
  
4.  Filtrelerle iletileri değerlendirmek için filtre tablonun ilk ileti almak için kullanılacak olan hizmet uç noktaları ile ilişkilendirilmiş olması gerekir.  Aşağıdaki örnek, yönlendirme davranışını kullanarak hizmet uç noktaları ile yönlendirme tablosunu ilişkilendirme gösterir:  
  
    ```xml  
    <behaviors>  
      <!--default routing service behavior definition-->  
      <serviceBehaviors>  
        <behavior name="routingConfiguration">  
          <routing filterTableName="filterTable1" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
## <a name="example"></a>Örnek  
 Yapılandırma dosyasının tam bir listesi verilmiştir.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<!-- Copyright (c) Microsoft Corporation. All rights reserved -->  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service behaviorConfiguration="routingConfiguration"  
               name="System.ServiceModel.Routing.RoutingService">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost/routingservice/router" />  
          </baseAddresses>  
        </host>  
        <!--Set up the inbound endpoints for the Routing Service-->  
        <!--first create the general router endpoint-->  
        <endpoint address="general"  
                  binding="wsHttpBinding"  
                  name="routerEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
        <!--create a virtual endpoint for the regular calculator service-->  
        <endpoint address="regular/calculator"  
                  binding="wsHttpBinding"  
                  name="calculatorEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
        <!--now create a virtual endpoint for the rounding calculator-->  
        <endpoint address="rounding/calculator"  
                  binding="wsHttpBinding"  
                  name="roundingEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
  
      </service>  
    </services>  
    <behaviors>  
      <!--default routing service behavior definition-->  
      <serviceBehaviors>  
        <behavior name="routingConfiguration">  
          <routing filterTableName="filterTable1" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
    <client>  
<!--set up the destination endpoints-->  
      <endpoint name="regularCalcEndpoint"  
                address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
  
      <endpoint name="roundingCalcEndpoint"  
                address="net.tcp://localhost:8080/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
    </client>  
    <routing>  
      <!-- use the namespace table element to define a prefix for our custom namespace-->  
      <namespaceTable>  
        <add prefix="custom" namespace="http://my.custom.namespace/"/>  
      </namespaceTable>  
      <filters>  
        <!--define the different message filters-->  
        <!--define an xpath message filter to look for the custom header coming from the client-->  
        <filter name="XPathFilter" filterType="XPath" filterData="/s12:Envelope/s12:Header/custom:RoundingCalculator = 'rounding'"/>  
  
        <!--define an endpoint name filter looking for messages that show up on the virtual regular calculator endpoint-->  
        <filter name="EndpointNameFilter" filterType="EndpointName" filterData="calculatorEndpoint"/>  
  
        <!--define a filter looking for messages that show up with the address prefix.  The corresponds to the rounding calc virtual endpoint-->  
        <filter name="PrefixAddressFilter" filterType="PrefixEndpointAddress" filterData="http://localhost/routingservice/router/rounding/"/>  
  
        <!--Set up the custom message filters.  In this example, we'll use the example round robin message filter, which alternates between the references-->  
        <filter name="RoundRobinFilter1" filterType="Custom" customType="CustomFilterAssembly.RoundRobinMessageFilter, CustomFilterAssembly" filterData="group1"/>  
        <filter name="RoundRobinFilter2" filterType="Custom" customType="CustomFilterAssembly.RoundRobinMessageFilter, CustomFilterAssembly" filterData="group1"/>  
      </filters>  
      <filterTables>  
        <table name="filterTable1">  
          <entries>  
            <!--add the filters to the message filter table-->  
            <!--first look for the custom header, and if we find it, send the message to the rounding calc endpoint-->  
            <add filterName="XPathFilter" endpointName="roundingCalcEndpoint" priority="2"/>  
  
            <!--if the header wasn't there, send the message based on which virtual endpoint it arrived at-->  
            <!--we determine this through the endpoint name, or through the address prefix-->  
            <add filterName="EndpointNameFilter" endpointName="regularCalcEndpoint" priority="1"/>  
            <add filterName="PrefixAddressFilter" endpointName="roundingCalcEndpoint" priority="1"/>  
  
            <!--if none of the other filters have matched, this message showed up on the default router endpoint, with no custom header-->  
            <!--round robin these requests between the two services-->  
            <add filterName="RoundRobinFilter1" endpointName="regularCalcEndpoint" priority="0"/>  
            <add filterName="RoundRobinFilter2" endpointName="roundingCalcEndpoint" priority="0"/>  
          </entries>  
        </table>  
      </filterTables>  
    </routing>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yönlendirme Hizmetleri](../../../../docs/framework/wcf/samples/routing-services.md)
