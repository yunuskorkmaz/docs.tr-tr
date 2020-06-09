---
title: 'Nasıl yapılır: Filtreleri Kullanma'
ms.date: 03/30/2017
ms.assetid: f2c7255f-c376-460e-aa20-14071f1666e5
ms.openlocfilehash: 434171138e75a0f4c336cd80cc2beb574b10001e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598898"
---
# <a name="how-to-use-filters"></a>Nasıl yapılır: Filtreleri Kullanma
Bu konuda, birden çok filtre kullanan bir yönlendirme yapılandırması oluşturmak için gereken temel adımlar özetlenmektedir. Bu örnekte, iletiler, regularCalc ve roundingCalc hesap makinesi hizmetinin iki uygulamasına yönlendirilir. Her iki uygulama da aynı işlemleri destekler; Ancak, bir hizmet, döndürmeden önce tüm hesaplamaları en yakın tamsayı değerine yuvarlar. İstemci uygulaması, hizmetin yuvarlama sürümünün kullanılıp kullanılmayacağını belirtebilmelidir; hiçbir hizmet tercihi ifade Ediyse, ileti iki hizmet arasında yük dengelemesi yapılır. Her iki hizmet tarafından kullanıma sunulan işlemler şunlardır:  
  
- Ekle  
  
- Çıkar  
  
- Çarp  
  
- Böl  
  
 Her iki hizmet de aynı işlemleri uygulayacağından, iletide belirtilen eylem benzersiz olmayacak olduğundan, eylem filtresini kullanamazsınız. Bunun yerine, iletilerin uygun uç noktalara yönlendirildiğinden emin olmak için ek iş yapmanız gerekir.  
  
### <a name="determine-unique-data"></a>Benzersiz verileri belirleme  
  
1. Her iki hizmet uygulaması da aynı işlemleri yaptığından ve temelde geri aldıkları verilerden farklı olduklarından, istemci uygulamalarından gönderilen iletilerde bulunan temel veriler, isteğin nasıl yönlendirileceğini belirlemenizi sağlayacak kadar benzersiz değildir. Ancak, istemci uygulaması iletiye benzersiz bir üstbilgi değeri eklerse, iletinin nasıl yönlendirildiğini öğrenmek için bu değeri kullanabilirsiniz.  
  
     Bu örnekte, istemci uygulamanın, yuvarlama Hesaplayıcı tarafından işlenmek üzere bir ileti gerekiyorsa, aşağıdaki kodu kullanarak özel bir üst bilgi ekler:  
  
    ```csharp  
    messageHeadersElement.Add(MessageHeader.CreateHeader("RoundingCalculator",
                                   "http://my.custom.namespace/", "rounding"));  
    ```  
  
     Artık bu üstbilgiye yönelik iletileri incelemek ve üstbilgiyi içeren iletileri roundCalc hizmetine yönlendirmek için XPath filtresini kullanabilirsiniz.  
  
2. Ayrıca, yönlendirme hizmeti, gelen iletileri istemci uygulamanın gönderdiği uç noktaya göre belirli bir Hesaplayıcı uygulamasına benzersiz şekilde yönlendirmek için EndpointName, EndpointAddress veya PrefixEndpointAddress filtreleriyle birlikte kullanılabilecek iki sanal hizmet uç noktasını kullanıma sunar.  
  
### <a name="define-endpoints"></a>Uç noktaları tanımlama  
  
1. Yönlendirme hizmeti tarafından kullanılan uç noktaları tanımlarken, önce istemcileriniz ve hizmetleriniz tarafından kullanılan kanalın şeklini belirlemelisiniz. Bu senaryoda, her iki hedef hizmet de bir istek-yanıt deseninin kullanıldığı için <xref:System.ServiceModel.Routing.IRequestReplyRouter> kullanılır. Aşağıdaki örnek, yönlendirme hizmeti tarafından sunulan hizmet uç noktalarını tanımlar.  
  
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
  
     Bu yapılandırmayla, yönlendirme hizmeti üç ayrı uç noktayı kullanıma sunar. Çalışma zamanı seçeneklerine bağlı olarak, istemci uygulaması bu adreslerden birine iletiler gönderir. "Sanal" hizmet uç noktalarından birine ulaşan iletiler ("yuvarlama/Hesaplayıcı" veya "normal/Hesaplayıcı"), ilgili Hesaplayıcı uygulamasına iletilir. İstemci uygulaması isteği belirli bir uç noktaya göndermezse, ileti genel uç noktaya gönderilir. Seçtiğiniz uç nokta ne olursa olsun, istemci uygulaması iletinin yuvarlama Hesaplayıcı uygulamasına iletilmesi gerektiğini belirtmek için özel üst bilgiyi dahil etmek de tercih edebilir.  
  
2. Aşağıdaki örnek, yönlendirme hizmetinin iletileri yönlendirdiğini istemci (hedef) uç noktalarını tanımlar.  
  
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
  
     Bu uç noktalar, belirli bir filtreyle eşleştiğinde iletinin gönderildiği hedef uç noktayı göstermek için filtre tablosunda kullanılır.  
  
### <a name="define-filters"></a>Filtre tanımlama  
  
1. İstemci uygulamanın iletiye eklediği "Roundinghesaplayıcı" özel üstbilgisine göre iletileri yönlendirmek için, bu üst bilginin varlığını denetlemek üzere bir XPath sorgusu kullanan bir filtre tanımlayın. Bu üstbilgi özel bir ad alanı kullanılarak tanımlandığından, XPath sorgusunda kullanılan "Custom" özel ad alanı önekini tanımlayan bir ad alanı girişi de ekleyin. Aşağıdaki örnek, gerekli Yönlendirme bölümünü, ad alanı tablosunu ve XPath filtresini tanımlar.  
  
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
  
     Bu **MessageFilter** , "yuvarlama" değeri içeren Iletide bir Roundinghesaplayıcı başlığına bakar. Bu üstbilgi, istemci tarafından, iletinin roundingCalc hizmetine yönlendirildiğini belirtmek üzere ayarlanır.  
  
    > [!NOTE]
    > S12 ad alanı ön eki, ad alanı tablosunda varsayılan olarak tanımlanır ve ad alanını temsil eder `http://www.w3.org/2003/05/soap-envelope` .
  
2. Ayrıca, iki sanal uç noktasında alınan iletileri aramak için filtreler tanımlamanız gerekir. İlk sanal uç nokta, "normal/Hesaplayıcı" uç noktasıdır. İstemci, iletinin regularCalc hizmetine yönlendirildiğini göstermek için istekleri bu uç noktaya gönderebilir. Aşağıdaki yapılandırma, <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> Iletinin filterData içinde belirtilen ada sahip bir uç nokta üzerinden geldiğini öğrenmek için öğesini kullanan bir filtre tanımlar.  
  
    ```xml  
    <!--define an endpoint name filter looking for messages that show up on the virtual regular calculator endpoint-->  
    <filter name="EndpointNameFilter" filterType="EndpointName" filterData="calculatorEndpoint"/>  
    ```  
  
     "Hesaplatorendpoint" adlı hizmet uç noktası tarafından bir ileti alındığında, bu filtre olarak değerlendirilir `true` .  
  
3. Ardından, roundingEndpoint adresine gönderilen iletileri gösteren bir filtre tanımlayın. İstemci bu uç noktaya istek göndererek, iletinin roundingCalc hizmetine yönlendirildiğini gösterir. Aşağıdaki yapılandırma, <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> iletinin "yuvarlama/Hesaplayıcı" uç noktasında geldiğini öğrenmek için öğesini kullanan bir filtre tanımlar.  
  
    ```xml  
    <!--define a filter looking for messages that show up with the address prefix.  The corresponds to the rounding calc virtual endpoint-->  
    <filter name="PrefixAddressFilter" filterType="PrefixEndpointAddress"  
            filterData="http://localhost/routingservice/router/rounding/"/>  
    ```  
  
     İle başlayan bir adreste bir ileti alındığında, `http://localhost/routingservice/router/rounding/` Bu filtre **true**olarak değerlendirilir. Bu yapılandırma tarafından kullanılan temel adres `http://localhost/routingservice/router` ve roundingEndpoint için belirtilen adres "yuvarlama/Hesaplayıcı" olduğundan, bu uç nokta ile iletişim kurmak için kullanılan tam adres `http://localhost/routingservice/router/rounding/calculator` Bu filtreyle eşleşir.  
  
    > [!NOTE]
    > Tek bir konağa, bir eşleşme gerçekleştirirken konak adı değerlendirilmez, çünkü tek bir ana bilgisayar, ana bilgisayara istemci uygulamasından başvurmanın geçerli yolları olabilecek çeşitli konak adları kullanılarak başvuruda bulunulabilir. Örneğin, aşağıdakilerin tümü aynı konağa başvurabilir:  
    >
    > - localhost  
    > - 127.0.0.1  
    > - `www.contoso.com`  
    > - ContosoWeb01  
  
4. Son filtre, genel uç noktaya gelen iletilerin özel üstbilgi olmadan yönlendirilmesini desteklemelidir. Bu senaryo için, iletilerin regularCalc ve roundingCalc hizmetleri arasında alternatif olması gerekir. Bu iletilerin "hepsini bir kez deneme" öğesini desteklemek için, işlenen her ileti için bir filtre örneğinin eşleşmesini sağlayan bir özel filtre kullanın.  Aşağıda, bir RoundRobinMessageFilter öğesinin aralarında farklı olmaları gerektiğini göstermek için birlikte gruplanmış iki örneği tanımlanmaktadır.  
  
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
  
     Çalışma zamanı sırasında, bu filtre türü, aynı grup olarak yapılandırılmış bu türün tanımlanmış tüm filtre örnekleri arasında tek bir koleksiyonda alternatifleri vardır. Bu `true` , ve için döndürme arasında alternatif olarak bu özel filtre tarafından işlenen mesajların oluşmasına neden olur `RoundRobinFilter1` `RoundRobinFilter2` .  
  
### <a name="define-filter-tables"></a>Filtre tabloları tanımlama  
  
1. Filtreleri belirli istemci uç noktalarıyla ilişkilendirmek için, bunları bir filtre tablosu içine yerleştirmeniz gerekir. Bu örnek senaryo, filtrelerin işlenme sırasını belirtmenize izin veren isteğe bağlı bir ayar olan filtre öncelik ayarlarını da kullanır. Filtre önceliği belirtilmemişse, tüm filtreler eşzamanlı olarak değerlendirilir.  
  
    > [!NOTE]
    > Filtre önceliği belirtildiğinde, filtrelerin işlenme sırasını denetlemenizi sağlar, bu da yönlendirme hizmetinin performansını olumsuz etkileyebilir. Mümkün olduğunda, filtre önceliklerinin kullanılması gerekli olmadığından filtre mantığını oluşturun.  
  
     Aşağıda, filtre tablosu tanımlanmaktadır ve daha önce tanımlanan "XPathFilter" öğesini bir önceliği 2 olan tabloya ekler. Bu giriş Ayrıca, `XPathFilter` iletisi ile eşleşirse iletinin öğesine yönlendirildiğini belirtir `roundingCalcEndpoint` .  
  
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
          </filterTables>  
    </routing>  
    ```  
  
     Filtre önceliği belirtirken, en yüksek öncelikli filtreler önce değerlendirilir. Belirli bir öncelik düzeyinde bir veya daha fazla filtre eşleşiyorsa, daha düşük öncelikli düzeylerde hiçbir filtre değerlendirilmeyecektir. Bu senaryoda, 2 belirtilen en yüksek önceliktir ve bu düzeyde tek filtre girişi budur.  
  
2. Filtre girdileri, uç nokta adını veya adres önekini inceleyerek belirli bir uç noktada bir iletinin alınıp alınmadığını denetlemek üzere tanımlanmıştır. Aşağıdaki girişler, bu filtre girdilerinin her ikisini de filtre tablosuna ekler ve bunları iletinin yönlendirileceği hedef uç noktalarla ilişkilendirir. Bu filtreler, yalnızca önceki XPath filtresi iletiyle eşleşmezse çalışması gerektiğini belirtmek için 1 önceliğine ayarlanır.  
  
    ```xml  
    <!--if the header wasn't there, send the message based on which virtual endpoint it arrived at-->  
    <!--we determine this through the endpoint name, or through the address prefix-->  
    <add filterName="EndpointNameFilter" endpointName="regularCalcEndpoint" priority="1"/>  
    <add filterName="PrefixAddressFilter" endpointName="roundingCalcEndpoint" priority="1"/>  
    ```  
  
     Bu filtrelerin filtre önceliği 1 olduğundan, yalnızca öncelik düzeyi 2 ' deki filtre iletiyle eşleşmezse değerlendirilir. Ayrıca, her iki filtrenin de aynı öncelik düzeyine sahip olduğu için aynı anda değerlendirilirler. Her iki filtre de birbirini dışlamadığından, bir iletiyle eşleşmesi yalnızca bir veya diğeri olabilir.  
  
3. Bir ileti önceki filtrelerden hiçbiriyle eşleşmezse, ileti genel hizmet uç noktası aracılığıyla alındı ve bu, nereye yönlendirildiğini belirten hiçbir üstbilgi bilgisi içermiyordu. Bu iletiler özel filtre tarafından işlenerek, yük, iki Hesaplayıcı hizmeti arasında dengelenebilir. Aşağıdaki örnek, filtre girişlerinin filtre tablosuna nasıl ekleneceğini gösterir; Her filtre iki hedef uç noktasından biriyle ilişkilendirilir.  
  
    ```xml  
    <!--if none of the other filters have matched,   
        this message showed up on the default router endpoint,   
        with no custom header-->  
    <!--round robin these requests between the two services-->  
    <add filterName="RoundRobinFilter1" endpointName="regularCalcEndpoint" priority="0"/>  
    <add filterName="RoundRobinFilter2" endpointName="roundingCalcEndpoint" priority="0"/>  
    ```  
  
     Bu girdiler 0 değerini belirttiğinden, yalnızca daha yüksek öncelikli bir filtrenin iletiyle eşleşmesi durumunda değerlendirilir. Ayrıca, her ikisi de aynı önceliğe sahip olduğundan, aynı anda değerlendirilir.  
  
     Daha önce bahsedildiği gibi, bu filtre tanımları tarafından kullanılan özel filtre yalnızca bir veya diğer her ileti için bir veya diğerini değerlendirir `true` . Bu filtre kullanılarak yalnızca iki filtre tanımlandığından, aynı belirtilen grup ayarıyla, bu, yönlendirme hizmetinin regularCalcEndpoint ve RoundingCalcEndpoint öğesine gönderme arasında değişiklik göstermesi durumunda olur.  
  
4. İletileri filtrelere karşı değerlendirmek için, önce filtre tablosunun ileti almak için kullanılacak hizmet uç noktaları ile ilişkilendirilmesi gerekir.  Aşağıdaki örnek yönlendirme davranışını kullanarak yönlendirme tablosunun hizmet uç noktalarıyla nasıl ilişkilendirileceğini göstermektedir:  
  
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
 Yapılandırma dosyasının tüm listesi aşağıda verilmiştir.  
  
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

- [Yönlendirme Hizmetleri](../samples/routing-services.md)
