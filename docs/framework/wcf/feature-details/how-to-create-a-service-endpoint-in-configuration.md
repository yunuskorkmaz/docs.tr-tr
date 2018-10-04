---
title: 'Nasıl yapılır: Yapılandırma İçinde Hizmet Uç Noktası Oluşturma'
ms.date: 06/16/2016
ms.assetid: f474e25d-2a27-4f31-84c5-395c442b8e70
ms.openlocfilehash: 63a40576b805952197cec5af2f89a5dc4b5d3545
ms.sourcegitcommit: 700b9003ea6bdd83a53458bbc436c9b5778344f1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48266279"
---
# <a name="how-to-create-a-service-endpoint-in-configuration"></a>Nasıl yapılır: Yapılandırma İçinde Hizmet Uç Noktası Oluşturma
Uç noktaları, istemcilerin bir Windows Communication Foundation (WCF) hizmeti sunan işlevine erişim sağlar. Göreli ve mutlak uç nokta adresleri bir birleşimini kullanarak bir hizmet için bir veya daha fazla uç nokta tanımlayabilirsiniz veya herhangi bir hizmet uç noktaları tanımlamazsanız, çalışma zamanı bazı varsayılan olarak, sağlar. Bu konuda, göreli ve mutlak adreslerini içeren bir yapılandırma dosyası kullanarak uç noktalarını eklemek gösterilmektedir.  
  
## <a name="example"></a>Örnek  
 Temel adres ve beş uç noktaları aşağıdaki hizmet yapılandırmasını belirtir.  
  
```xml  
<configuration>  
  
  <appSettings>  
    <!-- use appSetting to configure base address provided by host -->  
    <add key="baseAddress" value="http://localhost:8000/servicemodelsamples/service" />  
  </appSettings>  
  
  <system.serviceModel>  
    <services>  
    <!-- This section is optional with the default configuration introduced  
         in .NET Framework 4. -->  
      <service  
          name="Microsoft.ServiceModel.Samples.CalculatorService">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
          </baseAddresses>  
        </host>  
        <endpoint address=""  
                  binding="wsHttpBinding"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <endpoint address="/test"  
                  binding="wsHttpBinding"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <endpoint address="http://localhost:8001/hello/servicemodelsamples"  
                  binding="wsHttpBinding"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <endpoint address="net.tcp://localhost:9000/servicemodelsamples/service"  
                  binding="netTcpBinding"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <!-- the mex endpoint is another relative address exposed at   
             http://localhost:8000/ServiceModelSamples/service/mex -->  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  
  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
  </system.serviceModel>  
  
</configuration>  
```  
  
## <a name="example"></a>Örnek  
 Taban adresi kullanarak belirtilen `add` öğede hizmet/konak/baseAddresses aşağıdaki örnekte gösterildiği gibi.  
  
```xml  
<service   
    name="Microsoft.ServiceModel.Samples.CalculatorService">  
  <host>  
    <baseAddresses>  
      <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
    </baseAddresses>  
  </host>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte gösterilen ilk uç nokta tanımı taban adresini ve hizmetin göreli adresini Tekdüzen Kaynak Tanımlayıcısı (URI) oluşturma kuralları aşağıdaki uç nokta adresi olduğu anlamına gelir göreli bir adresi belirtir. Hizmetin göreli adresini boştur (""), uç nokta adresini temel adresi ile aynıdır. Gerçek bir uç nokta adresi `http://localhost:8000/servicemodelsamples/service`.  
  
```xml  
<endpoint address=""   
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a>Örnek  
 İkinci uç nokta tanımı, ayrıca aşağıdaki örnek yapılandırmada gösterildiği gibi bir göreli adresini belirtir. Hizmetin göreli adresini "test" öğesine taban adresi olarak eklenir. Gerçek bir uç nokta adresi `http://localhost:8000/servicemodelsamples/service/test`.  
  
```xml  
<endpoint address="/test"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek yapılandırmada gösterildiği gibi üçüncü bir uç nokta tanımı mutlak bir adres belirtir. Temel adres, adres, hiçbir rol oynar. Gerçek bir uç nokta adresi `http://localhost:8001/hello/servicemodelsamples`.  
  
```xml  
<endpoint address="http://localhost:8001/hello/servicemodelsamples"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a>Örnek  
 Mutlak bir adres ve farklı bir aktarım dördüncü uç nokta adresini belirtir; TCP. Temel adres, adres, hiçbir rol oynar. Gerçek bir uç nokta adresi olduğunu NET.TCP://localhost: 9000/servicemodelsamples/hizmet.  
  
```xml  
<endpoint address="net.tcp://localhost:9000/servicemodelsamples/service"  
    binding="netTcpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a>Örnek  
 Çalışma zamanı tarafından sağlanan varsayılan uç noktalarını kullanacak şekilde herhangi bir hizmet uç noktaları kod veya yapılandırma dosyasını belirtmeyin. Bir hizmeti açtığınızda bu örnekte, çalışma zamanı varsayılan uç noktaları oluşturur. Varsayılan uç noktaları, bağlamalar ve davranışları hakkında daha fazla bilgi için bkz. [Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
```xml  
<configuration>  
  
  <appSettings>  
    <!-- use appSetting to configure base address provided by host -->  
    <add key="baseAddress" value="http://localhost:8000/servicemodelsamples/service" />  
  </appSettings>  
  
  <system.serviceModel>  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
  </system.serviceModel>  
  
</configuration>  
```
