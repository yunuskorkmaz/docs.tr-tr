---
title: "Nasıl yapılır: Filtreleri Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2c7255f-c376-460e-aa20-14071f1666e5
caps.latest.revision: "12"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 94d45537ca3edd5f31f1ed31898857f002312a0b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-filters"></a>Nasıl yapılır: Filtreleri Kullanma
Bu konu, birden çok filtre kullanan bir yönlendirme yapılandırması oluşturmak için gereken temel adımlarda özetler. Bu örnekte, iletiler için bir hesap makinesi hizmetinin, regularCalc ve roundingCalc iki uygulamaları yönlendirilir. Her iki uygulamaları aynı işlemleri destekler; Ancak bir hizmet döndürmeden önce hesaplamalarının yakın tamsayı değere yuvarlar. Bir istemci uygulaması hizmetinin yuvarlama sürümü kullanılıp kullanılmayacağını belirtmek kurabilmesi gerekir; Hizmet tercih ifade, ileti iki hizmetleri arasında dengeli yoktur. Her iki Hizmetleri tarafından sunulan işlemleri şunlardır:  
  
-   Ekle  
  
-   Çıkarma  
  
-   Çarp  
  
-   Bölme  
  
 Her iki hizmet işlemlerin aynısını uyguladığınız için iletide belirtilen eylemi benzersiz olmayacağından, eylem filtresi kullanamazsınız. Bunun yerine iletileri uygun Uç noktalara yönlendirildiğinden emin olmak için ek iş yapmanız gerekir.  
  
### <a name="determine-unique-data"></a>Benzersiz veri belirleme  
  
1.  Her iki hizmet uygulamaları aynı işlemleri işlemek ve dışında döndürmeleri veri temelde aynı olduğundan, istemci uygulamalarından gönderilen iletileri bulunan temel verileri nasıl yönlendirileceğini belirlemenize izin vermek için benzersiz değil İstek. Ancak daha sonra istemci uygulamasının iletiye benzersiz üstbilgi değeri eklerse, ileti nasıl yönlendirileceğini belirlemek için bu değeri kullanabilirsiniz.  
  
     İstemci uygulaması yuvarlama hesaplayıcı tarafından işlenmek üzere ileti gerekiyorsa bu örnek için onu bir özel üst bilgi aşağıdaki kodu kullanarak ekler:  
  
    ```csharp  
    messageHeadersElement.Add(MessageHeader.CreateHeader("RoundingCalculator",   
                                   "http://my.custom.namespace/", "rounding"));  
    ```  
  
     Şimdi bu başlığı iletilerde incelemek için XPath filtresi kullanın ve roundCalc hizmetine üstbilgisini içeren iletileri yönlendirmek.  
  
2.  Yönlendirme hizmeti EndpointName, EndpointAddress, kullanılabilir iki sanal hizmet uç noktalarına ek olarak kullanıma sunar veya benzersiz olarak uç noktada dayalı belirli hesaplayıcı uygulamasına gelen iletileri yönlendirmek için PrefixEndpointAddress filtreleri için istemci uygulaması isteği gönderir.  
  
### <a name="define-endpoints"></a>Uç noktaları tanımlayın  
  
1.  Yönlendirme hizmeti tarafından kullanılan uç noktalarını tanımlarken, istemciler ve hizmetler tarafından kullanılan kanal şeklini belirlemeniz gerekir. Bu senaryoda, her iki hedef hizmet istek-yanıt düzeni kullanın. Bu nedenle <xref:System.ServiceModel.Routing.IRequestReplyRouter> kullanılır. Aşağıdaki örnek yönlendirme hizmeti tarafından sunulan hizmet uç noktaları tanımlar.  
  
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
  
     Bu yapılandırma ile yönlendirme hizmeti üç ayrı uç noktalarını kullanıma sunar. Çalışma zamanı seçenekler bağlı olarak, istemci uygulaması iletileri bu adresleri biri olarak gönderir. ("Yuvarlama/hesaplayıcı" veya "normal/hesaplayıcı") "sanal" hizmet uç noktalarına birini gelen iletiler için karşılık gelen hesaplayıcı uygulama iletilir. İstemci uygulaması için özel bir uç nokta isteği göndermez, ileti genel uç noktasına değinilmiştir. Seçilen uç nokta bağımsız olarak, istemci uygulaması da ileti yuvarlama hesaplayıcı kullanımla iletilen olduğunu belirtmek için özel üstbilgisini seçebilirsiniz.  
  
2.  Aşağıdaki örnek, yönlendirme hizmeti, iletileri yönlendirir (hedef) istemci uç noktalarını tanımlar.  
  
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
  
     Bu uç noktalar filtre tablosunda belirli bir filtre eşleştiğinde iletisi gönderilir hedef uç noktası belirtmek için kullanılır.  
  
### <a name="define-filters"></a>Filtrelerin tanımlayın  
  
1.  İstemci uygulaması iletiye ekler "RoundingCalculator" özel üstbilgi göre iletileri yönlendirmek için bu üst varlığını denetlemek için bir XPath sorgusu kullanan bir filtre tanımlar. Özel bir ad alanını kullanarak bu başlığı tanımlı olduğundan, ayrıca "kullanılan özel" bir özel ad alanı önekini XPath sorgusu tanımlayan bir ad alanı girişi ekleyin. Aşağıdaki örnek gerekli yönlendirme bölüm, ad alanı tablo ve XPath filtresi tanımlar.  
  
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
  
     Bu **MessageFilter** "yuvarlama" değeri içeren iletisini RoundingCalculator üstbilgisinde arar. Bu üst ileti roundingCalc hizmete yönlendirileceğini belirtmek için istemci tarafından ayarlanır.  
  
    > [!NOTE]
    >  S12 ad alanı öneki varsayılan ad alanı tablo olarak tanımlanır ve "http://www.w3.org/2003/05/soap-envelope" ad alanı temsil eder.  
  
2.  Ayrıca iki sanal uç noktalarda alınan iletilerin Ara filtreleri tanımlamanız gerekir. İlk sanal uç nokta "normal/hesaplayıcı" uç noktadır. İstemci, ileti regularCalc hizmete yönlendirileceğini belirtmek için bu uç noktaya istekleri gönderebilirsiniz. Aşağıdaki yapılandırmayı kullanan bir filtre tanımlar <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> ileti filterData içinde belirtilen ada sahip bir uç noktası aracılığıyla ulaştığında, belirlemek için.  
  
    ```xml  
    <!--define an endpoint name filter looking for messages that show up on the virtual regular calculator endpoint-->  
    <filter name="EndpointNameFilter" filterType="EndpointName" filterData="calculatorEndpoint"/>  
    ```  
  
     Bir ileti "calculatorEndpoint" adlı hizmet uç noktası tarafından alınmazsa, bu filtresinin `true`.  
  
3.  Ardından, roundingEndpoint adresine gönderilen iletileri arar bir filtre tanımlar. İstemci, ileti roundingCalc hizmete yönlendirileceğini belirtmek için bu uç noktaya istekleri gönderebilirsiniz. Aşağıdaki yapılandırmayı kullanan bir filtre tanımlar <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> ileti "yuvarlama/hesaplayıcı" uç noktada ulaştığında, belirlemek için.  
  
    ```xml  
    <!--define a filter looking for messages that show up with the address prefix.  The corresponds to the rounding calc virtual endpoint-->  
    <filter name="PrefixAddressFilter" filterType="PrefixEndpointAddress"  
            filterData="http://localhost/routingservice/router/rounding/"/>  
    ```  
  
     "Http://localhost/routingservice/router/rounding/" ile başlayan adreste bir ileti alındığında sonra bu filtresinin **doğru**. Bu yapılandırma tarafından kullanılan temel adres "http://localhost/routingservice/router" ve roundingEndpoint için belirtilen adresi "yuvarlama/hesaplayıcı" olduğundan bu bitiş noktası ile iletişim kurmak için kullanılan tam "http://localhost/ adresidir routingservice/yönlendirici/yuvarlama/Bu filtre ile eşleşen hesaplayıcı".  
  
    > [!NOTE]
    >  PrefixEndpointAddress filtre ana bilgisayar adı, tek bir ana bilgisayar için tüm olabilir ana bilgisayar adlarını çeşitli kullanarak başvurulabilir olduğundan bir eşleşme gerçekleştirme konağa istemci uygulamasından başvuran geçerli yolu kullanırken değerlendirmez. Örneğin, aşağıdakilerin tümü aynı ana bilgisayarına başvurabilir:  
    >   
    >  -   localhost  
    > -   127.0.0.1  
    > -   www.contoso.com  
    > -   ContosoWeb01  
  
4.  Son filtre özel üst bilgi içermeyen genel uç noktada gelen iletileri yönlendirme desteklemesi gerekir. Bu senaryo için iletileri regularCalc ve roundingCalc hizmetleri arasında alternatif. "Hepsini bir kez deneme" Bu iletilerin yönlendirme desteklemek için işlenen her ileti için eşleştirecek bir filtre örneğini sağlayan özel bir filtre kullanın.  Bunlar diğer arasında alternatif olduğunu göstermek için hangi birlikte gruplandırılmış bir RoundRobinMessageFilter, iki örneğini tanımlar.  
  
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
  
     Çalışma zamanı sırasında bu filtre türü bu türdeki bir koleksiyona aynı grubu olarak yapılandırıldığı tüm tanımlı filtre örnekleri arasında geçiş yapar. Bu, bu özel filtre döndürme arasında alternatif tarafından işlenen iletilerin neden olur `true` RoundRobinFilter1 ve RoundRobinFilter2.  
  
### <a name="define-filter-tables"></a>Filtre tabloları tanımlayın  
  
1.  Filtreler belirli istemci uç ile ilişkilendirmek için filtre tablo içinde yerleştirmeniz gerekir. Bu örnek senaryo, filtreleri işlenme sırasını göstermek izin veren, isteğe bağlı bir ayardır filtre öncelik ayarları, ayrıca kullanır. Hiçbir filtre öncelik belirtilmişse, tüm filtreleri eşzamanlı olarak değerlendirilir.  
  
    > [!NOTE]
    >  Belirtildiğinde bir filtre öncelik sayesinde, hangi filtrelerin sırasını denetlemek için işlenen yönlendirme hizmeti performansını olumsuz etkileyebilir. Filtre önceliklerin kullanımı gerekli olmamasını sağlamak mümkün olduğunda, filtre mantığı oluşturun.  
  
     Aşağıdaki filtre tablosunda tanımlar ve "tablosuna 2 önceliği daha önce tanımlanan XPathFilterElement" ekler. Bu giriş, ayrıca "XPathFilterElement" iletisi eşleşirse, ileti "roundingCalcEndpoint" yönlendirilir belirtir  
  
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
  
     Bir filtre öncelik belirtirken, en yüksek öncelik filtreleri önce değerlendirilir. Bir veya daha fazla filtre belirli öncelik düzeyindeki eşleşirse hiçbir filtre öncelik düzeylerinde değerlendirilir. Bu senaryo için 2, belirtilen en yüksek önceliktir ve bu düzeyde yalnızca filtre giriş budur.  
  
2.  Filtre girişleri, uç nokta adı veya adresi öneki inceleyerek bir ileti belirli bir noktadaki alınırsa, görmek için tanımlanmıştır. Aşağıdaki girdileri bu filtre girişleri her ikisi de filtre tabloya ekleyin ve bunları ileti için yönlendirilmiş hedef uç noktaları ile ilişkilendirin. Bu filtreler, önceki XPath filtresi ileti eşleşmedi varsa bunlar yalnızca çalışması gerektiğini belirtmek için bir öncelik 1 ayarlanır.  
  
    ```xml  
    <!--if the header wasn't there, send the message based on which virtual endpoint it arrived at-->  
    <!--we determine this through the endpoint name, or through the address prefix-->  
    <add filterName="EndpointNameFilter" endpointName="regularCalcEndpoint" priority="1"/>  
    <add filterName="PrefixAddressFilter" endpointName="roundingCalcEndpoint" priority="1"/>  
    ```  
  
     Bu filtreler, filtre önceliği 1 olduğundan, bunlar öncelik düzeyini 2'deki filtreyi ileti eşleşmiyorsa yalnızca değerlendirilir. Her iki filtreleri aynı öncelik düzeyine sahip olduğundan Ayrıca, bunlar aynı anda değerlendirilir. Her iki filtreleri birbirini dışlayan olduğundan, tek veya başka bir ileti eşleşecek şekilde mümkündür.  
  
3.  Bir ileti önceki filtrelerden biriyle eşleşmiyorsa, ileti genel hizmet uç noktası aracılığıyla alındı ve yönlendirmek yeri gösteren hiçbir üst bilgileri içeriyor. Bu iletiler, bunları iki hesaplayıcı hizmetleri arasında hangi yükünü dengeleyen özel filtre tarafından işleneceğini üzeresiniz. Aşağıdaki örnek Filtresi tablosu için filtre girişleri ekleneceği gösterilmektedir; Her filtre iki hedef uç noktalardan biri ile ilişkilidir.  
  
    ```xml  
    <!--if none of the other filters have matched,   
        this message showed up on the default router endpoint,   
        with no custom header-->  
    <!--round robin these requests between the two services-->  
    <add filterName="RoundRobinFilter1" endpointName="regularCalcEndpoint" priority="0"/>  
    <add filterName="RoundRobinFilter2" endpointName="roundingCalcEndpoint" priority="0"/>  
    ```  
  
     Bu girişler 0 önceliğini belirttiğinden, bunlar daha yüksek bir öncelik hiçbir filtre ileti eşleşiyorsa yalnızca değerlendirilir. Ayrıca, bunların her ikisi de aynı önceliği olduğundan, eşzamanlı olarak değerlendirilir.  
  
     Daha önce belirtildiği gibi bu filtre tanımları tarafından kullanılan özel filtre yalnızca bir ya da diğer olarak değerlendirir `true` alınan her ileti için. Bu filtre ile aynı belirtilen grup ayarı kullanarak yalnızca iki filtre tanımlı olduğundan, yönlendirme hizmeti regularCalcEndpoint ve RoundingCalcEndpoint gönderme arasında diğerleri etkisidir.  
  
4.  Filtrelerle iletileri değerlendirmek için filtre tablonun ilk iletileri almak için kullanılan hizmet uç noktaları ile ilişkilendirilmiş olması gerekir.  Aşağıdaki örnek, yönlendirme davranışını kullanarak yönlendirme tablosunu hizmet uç noktaları ile ilişkilendirmek gösterilmiştir:  
  
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
 Yapılandırma dosyası tam bir listesi verilmiştir.  
  
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
