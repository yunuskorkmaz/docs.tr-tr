---
title: 'Nasıl yapılır: Filtreleri Kullanma'
ms.date: 03/30/2017
ms.assetid: f2c7255f-c376-460e-aa20-14071f1666e5
ms.openlocfilehash: f99c2af623dacac3ebe46422815a7f42e2a4df2c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184824"
---
# <a name="how-to-use-filters"></a>Nasıl yapılır: Filtreleri Kullanma
Bu konu, birden çok filtre kullanan bir yönlendirme yapılandırması oluşturmak için gereken temel adımları özetler. Bu örnekte, iletiler bir hesap makinesi hizmetinin iki uygulamasına yönlendirilir, düzenli Calc ve yuvarlamaCalc. Her iki uygulama da aynı işlemleri destekler; ancak bir hizmet, dönmeden önce tüm hesaplamaları en yakın tümsabudeğere yuvarlar. İstemci uygulaması, hizmetin yuvarlama sürümünü kullanıp kullanmayacağını belirtebilmeli; hizmet tercihi ifade edilmezse, ileti iki hizmet arasında yük dengelenir. Her iki hizmettarafından ortaya çıkarılan işlemler şunlardır:  
  
- Ekle  
  
- Çıkar  
  
- Çarp  
  
- Böl  
  
 İletide belirtilen eylem benzersiz olmadığından, her iki hizmet de aynı işlemleri uyguladığından, Eylem filtresini kullanamazsınız. Bunun yerine iletilerin uygun uç noktalara yönlendirilmesini sağlamak için ek çalışma yapmanız gerekir.  
  
### <a name="determine-unique-data"></a>Benzersiz Verileri Belirleme  
  
1. Her iki hizmet uygulaması da aynı işlemleri işlediğinden ve döndükleri veriler dışında temelde aynı olduğundan, istemci uygulamalarından gönderilen iletilerde bulunan temel veriler, Istek. Ancak istemci uygulaması iletiye benzersiz bir üstbilgi değeri eklerse, iletinin nasıl yönlendirilmesi gerektiğini belirlemek için bu değeri kullanabilirsiniz.  
  
     Bu örnekte, istemci uygulaması nın iletinin yuvarlama hesap makinesi tarafından işlenmesi gerekiyorsa, aşağıdaki kodu kullanarak özel bir üstbilgi ekler:  
  
    ```csharp  
    messageHeadersElement.Add(MessageHeader.CreateHeader("RoundingCalculator",
                                   "http://my.custom.namespace/", "rounding"));  
    ```  
  
     Artık bu üstbilginin iletilerini incelemek ve üstbilgi içeren iletileri roundCalc hizmetine yönlendirmek için XPath filtresini kullanabilirsiniz.  
  
2. Ayrıca Yönlendirme Hizmeti, gelen iletileri bitiş noktasına dayalı olarak belirli bir hesap makinesi uygulamasına benzersiz bir şekilde yönlendirmek için EndpointName, EndpointAddress veya PrefixEndpointAddress filtreleriyle kullanılabilecek iki sanal hizmet uç noktasını ortaya çıkarır hangi istemci başvuru isteği gönderir.  
  
### <a name="define-endpoints"></a>Uç Noktaları Tanımla  
  
1. Yönlendirme Hizmeti tarafından kullanılan uç noktaları tanımlarken, öncelikle müşterileriniz ve hizmetleriniz tarafından kullanılan kanalın şeklini belirlemeniz gerekir. Bu senaryoda, hem hedef hizmetler bir istek-yanıt deseni kullanır, bu nedenle <xref:System.ServiceModel.Routing.IRequestReplyRouter> kullanılır. Aşağıdaki örnekte Yönlendirme Hizmeti tarafından maruz kalan hizmet bitiş noktaları tanımlanır.  
  
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
  
     Bu yapılandırmaile Yönlendirme Hizmeti üç ayrı uç noktayı ortaya çıkarır. Çalışma zamanı seçimlerine bağlı olarak, istemci uygulaması bu adreslerden birine ileti gönderir. "Sanal" hizmet bitiş noktalarından birine ("yuvarlama/hesap makinesi" veya "normal/hesap makinesi") gelen iletiler ilgili hesap makinesi uygulamasına iletilir. İstemci uygulaması isteği belirli bir bitiş noktasına göndermezse, ileti genel bitiş noktasına yönlendirilir. Seçilen bitiş noktası ne olursa olsun, istemci uygulaması iletinin yuvarlama hesap makinesi uygulamasına iletilmesi gerektiğini belirtmek için özel üstbilgi eklemeyi de seçebilir.  
  
2. Aşağıdaki örnek, Yönlendirme Hizmeti'nin iletileri yolettiği istemci (hedef) uç noktalarını tanımlar.  
  
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
  
     Bu uç noktalar, iletinin belirli bir filtreyle eşleştiğinde gönderildiği hedef bitiş noktasını belirtmek için filtre tablosunda kullanılır.  
  
### <a name="define-filters"></a>Filtreleri Tanımla  
  
1. İstemci uygulamasının iletiye eklediği "Yuvarlama Hesaplayıcısı" özel üstbilgisini temel alan iletileri yönlendirmek için, bu üstbilginin varlığını denetlemek için XPath sorgusu kullanan bir filtre tanımlayın. Bu üstbilgi özel bir ad alanı kullanılarak tanımlandığı için, XPath sorgusunda kullanılan "özel" özel bir ad alanı öneki tanımlayan bir ad alanı girişi de ekleyin. Aşağıdaki örnekte gerekli yönlendirme bölümü, ad alanı tablosu ve XPath filtresi tanımlanır.  
  
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
  
     Bu **MessageFilter,** iletide "yuvarlama" değeri içeren bir Yuvarlama Hesaplayıcısı üstbilgisini arar. Bu üstbilgi istemci tarafından iletinin yuvarlamaCalc hizmetine yönlendirilmesi gerektiğini belirtmek için ayarlanır.  
  
    > [!NOTE]
    > s12 ad alanı öneki, ad alanı tablosunda varsayılan olarak `http://www.w3.org/2003/05/soap-envelope`tanımlanır ve ad alanını temsil eder.
  
2. Ayrıca, iki sanal uç noktada alınan iletileri arayan filtreleri de tanımlamanız gerekir. İlk sanal bitiş noktası "normal/hesap makinesi" bitiş noktasıdır. İstemci, iletinin normal Calc hizmetine yönlendirilmesi gerektiğini belirtmek için bu bitiş noktasına istekgönderebilir. Aşağıdaki yapılandırma, iletinin <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> filterData'da belirtilen adı içeren bir bitiş noktasından gelip gelmediğini belirlemek için bir filtre tanımlar.  
  
    ```xml  
    <!--define an endpoint name filter looking for messages that show up on the virtual regular calculator endpoint-->  
    <filter name="EndpointNameFilter" filterType="EndpointName" filterData="calculatorEndpoint"/>  
    ```  
  
     "CalculatorEndpoint" adlı hizmet bitiş noktası tarafından bir ileti alınırsa, `true`bu filtre .  
  
3. Ardından, yuvarlama Bitiş Noktası'nın adresine gönderilen iletileri arayan bir filtre tanımlayın. İstemci, iletinin yuvarlamaCalc hizmetine yönlendirilmesi gerektiğini belirtmek için bu bitiş noktasına istekgönderebilir. Aşağıdaki yapılandırma, iletinin "yuvarlama/hesap makinesi" bitiş noktasına gelip gelmediğini belirlemek <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> için bir filtre tanımlar.  
  
    ```xml  
    <!--define a filter looking for messages that show up with the address prefix.  The corresponds to the rounding calc virtual endpoint-->  
    <filter name="PrefixAddressFilter" filterType="PrefixEndpointAddress"  
            filterData="http://localhost/routingservice/router/rounding/"/>  
    ```  
  
     İleti ile `http://localhost/routingservice/router/rounding/` başlayan bir adreste alınırsa, bu filtre **doğru**olarak değerlendirilir. Bu yapılandırma tarafından kullanılan temel `http://localhost/routingservice/router` adres olduğundan ve yuvarlama Bitiş Noktası için belirtilen adres "yuvarlama/hesap makinesi" `http://localhost/routingservice/router/rounding/calculator`olduğundan, bu uç noktayla iletişim kurmak için kullanılan tam adres , bu filtreyle eşleşir.  
  
    > [!NOTE]
    > PrefixEndpointAddress filtresi, tek bir ana bilgisayar istemci uygulamasından ana bilgisayara atıfta bulunarak geçerli yollar olabilecek çeşitli ana bilgisayar adları kullanılarak başvurulabileceğinden, bir eşleşme gerçekleştirirken ana bilgisayar adını değerlendirmez. Örneğin, aşağıdakilerin tümü aynı ana bilgisayara başvurabilir:  
    >
    > - localhost  
    > - 127.0.0.1  
    > - `www.contoso.com`  
    > - ContosoWeb01  
  
4. Son filtre, özel üstbilgi olmadan genel bitiş noktasına gelen iletilerin yönlendirmesini desteklemelidir. Bu senaryo için, iletiler regularCalc ve yuvarlamaCalc hizmetleri arasında geçiş yapılmalıdır. Bu iletilerin "yuvarlak robin" yönlendirmesini desteklemek için, işlenen her ileti için bir filtre örneğinin eşleşmesine izin veren özel bir filtre kullanın.  Aşağıda, aralarında geçiş olması gerektiğini belirtmek için birlikte gruplanan RoundRobinMessageFilter'in iki örneği tanımlanır.  
  
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
  
     Çalışma süresi sırasında, bu filtre türü, aynı grup olarak yapılandırılan bu türdeki tüm tanımlanmış filtre örnekleri arasında tek bir koleksiyona dönüşür. Bu, bu özel filtre tarafından işlenen iletilerin `true` `RoundRobinFilter1` için `RoundRobinFilter2`dönen ve .  
  
### <a name="define-filter-tables"></a>Filtre Tablolarını Tanımla  
  
1. Filtreleri belirli istemci uç noktalarıyla ilişkilendirmek için, filtreleri bir filtre tablosuna yerleştirmeniz gerekir. Bu örnek senaryo, filtrelerin işlenme sırasını belirtmenize olanak tanıyan isteğe bağlı bir ayar olan filtre önceliği ayarlarını da kullanır. Filtre önceliği belirtilmemişse, tüm filtreler aynı anda değerlendirilir.  
  
    > [!NOTE]
    > Filtre önceliği belirtmek, filtrelerin işlendiği sırayı denetlemenize olanak sağlarken, Yönlendirme Hizmeti'nin performansını olumsuz etkileyebilir. Mümkün olduğunda, filtre önceliklerinin kullanılmasının gerekli olmaması için filtre mantığı oluşturun.  
  
     Aşağıdaki filtre tablosunu tanımlar ve daha önce tanımlanan "XPathFilter"i 2 önceliği olan tabloya ekler. Bu giriş ayrıca, iletiyle `XPathFilter` eşleşirse, iletinin `roundingCalcEndpoint`.  
  
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
  
     Filtre önceliği belirtilirken, önce en yüksek öncelik filtreleri değerlendirilir. Belirli bir öncelik düzeyinde bir veya daha fazla filtre eşleşirse, daha düşük öncelik düzeylerindeki filtreler değerlendirilmez. Bu senaryo için, 2 belirtilen en yüksek önceliktir ve bu düzeydeki tek filtre girişidir.  
  
2. Filtre girişleri, bitiş noktası adını veya adres önekini inceleyerek belirli bir uç noktadan ileti alınıp alınıp alınıp alınıp alınıp alınıp alınmayolmadığını denetlemek için tanımlanmıştır. Aşağıdaki girişler, bu filtre girişlerinin her ikisini de filtre tablosuna ekler ve iletinin yönlendirileceği hedef uç noktalarıyla ilişkilendirir. Bu filtreler, yalnızca önceki XPath filtresi iletiyle eşleşmediyse çalışması gerektiğini belirtmek için 1 önceliğe ayarlanır.  
  
    ```xml  
    <!--if the header wasn't there, send the message based on which virtual endpoint it arrived at-->  
    <!--we determine this through the endpoint name, or through the address prefix-->  
    <add filterName="EndpointNameFilter" endpointName="regularCalcEndpoint" priority="1"/>  
    <add filterName="PrefixAddressFilter" endpointName="roundingCalcEndpoint" priority="1"/>  
    ```  
  
     Bu filtrelerin filtre önceliği 1 olduğundan, yalnızca öncelik düzeyi 2'deki filtre iletiyle eşleşmiyorsa değerlendirilir. Ayrıca, her iki filtre de aynı öncelik düzeyine sahip olduğundan aynı anda değerlendirilir. Her iki filtre de birbirini dışladığından, yalnızca birinin veya diğerinin bir iletiyi eşleştirmesi mümkündür.  
  
3. İleti önceki filtrelerden herhangi biri ile eşleşmiyorsa, ileti genel hizmet bitiş noktası üzerinden alındı ve iletinin nereye yönlendirilmeyeceğini gösteren üstbilgi bilgisi içermedi. Bu iletiler, iki hesap makinesi hizmeti arasında yük dengeleri özel filtre tarafından işlenecek. Aşağıdaki örnek, filtre girişlerinin filtre tablosuna nasıl ekleyeceğini gösterir; her filtre iki hedef uç noktadan biriyle ilişkilidir.  
  
    ```xml  
    <!--if none of the other filters have matched,   
        this message showed up on the default router endpoint,   
        with no custom header-->  
    <!--round robin these requests between the two services-->  
    <add filterName="RoundRobinFilter1" endpointName="regularCalcEndpoint" priority="0"/>  
    <add filterName="RoundRobinFilter2" endpointName="roundingCalcEndpoint" priority="0"/>  
    ```  
  
     Bu girişler 0 önceliği belirttiğinden, yalnızca daha yüksek bir önceliğe ait bir filtre iletiyle eşleşmediğinde değerlendirilir. Ayrıca, her ikisi de aynı önceliğe ait olduğundan, aynı anda değerlendirilir.  
  
     Daha önce de belirtildiği gibi, bu filtre tanımları tarafından kullanılan özel `true` filtre, alınan her ileti için yalnızca bir veya diğerini değerlendirir. Bu filtre kullanılarak, aynı belirtilen grup ayarına sahip yalnızca iki filtre tanımlandığı için, bunun etkisi, Yönlendirme Hizmetinin düzenli CalcEndpoint'e gönderme ile YuvarlamaCalcEndpoint arasında dönüşümlü olmasıdır.  
  
4. İletileri filtrelere karşı değerlendirmek için, filtre tablosunun öncelikle ileti almak için kullanılacak hizmet bitiş noktalarıyla ilişkilendirilmesi gerekir.  Aşağıdaki örnek, yönlendirme davranışını kullanarak yönlendirme tablosunun hizmet bitiş noktalarıyla nasıl ilişkilendirilen  
  
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
 Aşağıda yapılandırma dosyasının tam listesi veremivettir.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönlendirme Hizmetleri](../../../../docs/framework/wcf/samples/routing-services.md)
