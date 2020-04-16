---
title: 'Nasıl yapılır: Yapılandırma İçinde Hizmet Uç Noktası Oluşturma'
ms.date: 06/16/2016
ms.assetid: f474e25d-2a27-4f31-84c5-395c442b8e70
ms.openlocfilehash: 5935f798004de3ec049b9c9f0300675e1660f462
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81464125"
---
# <a name="how-to-create-a-service-endpoint-in-configuration"></a>Nasıl yapılır: Yapılandırma İçinde Hizmet Uç Noktası Oluşturma
Uç noktalar, istemcilere Windows Communication Foundation (WCF) hizmetinin sunduğu işlevsellik lere erişim sağlar. Bir hizmet için bir veya daha fazla uç nokta, göreli ve mutlak uç nokta adreslerinin bir birleşimini kullanarak veya herhangi bir hizmet bitiş noktası tanımlamazsanız, çalışma süresi varsayılan olarak sizin için bazı sağlar. Bu konu, hem göreceli hem de mutlak adresleri içeren bir yapılandırma dosyasını kullanarak uç noktaların nasıl ekleyeceğini gösterir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki hizmet yapılandırması bir temel adres ve beş uç nokta belirtir.  
  
```xml  
<configuration>  
  
  <appSettings>  
    <!-- use appSetting to configure base address provided by host -->  
    <add key="baseAddress" value="http://localhost:8000/servicemodelsamples/service" />  
  </appSettings>  
  
  <system.serviceModel>  
    <services>  
    <!-- This section is optional with the default configuration introduced in .NET Framework 4. -->  
      <service name="Microsoft.ServiceModel.Samples.CalculatorService">  
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
 Temel adres, aşağıdaki `add` örnekte gösterildiği gibi hizmet/ana bilgisayar/baseAddresss altında öğe kullanılarak belirtilir.  
  
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
 Aşağıdaki örnekte gösterilen ilk uç nokta tanımı göreceli bir adres belirtir, bu da bitiş noktası adresinin temel adres ve Tekdüzen Kaynak Tanımlayıcı (URI) kompozisyonunun kurallarını izleyen göreli adresin birleşimi olduğu anlamına gelir. Göreli adres boş (""), bu nedenle bitiş noktası adresi temel adresle aynıdır. Gerçek bitiş noktası `http://localhost:8000/servicemodelsamples/service`adresi .  
  
```xml  
<endpoint address=""
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a>Örnek  
 İkinci uç nokta tanımı, aşağıdaki örnek yapılandırmada gösterildiği gibi göreli bir adres de belirtir. Göreli adres, "test", temel adrese eklenir. Gerçek bitiş noktası `http://localhost:8000/servicemodelsamples/service/test`adresi .  
  
```xml  
<endpoint address="/test"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a>Örnek  
 Üçüncü uç nokta tanımı, aşağıdaki örnek yapılandırmada gösterildiği gibi mutlak bir adres belirtir. Temel adres adreste hiçbir rol oynamaz. Gerçek bitiş noktası `http://localhost:8001/hello/servicemodelsamples`adresi .  
  
```xml  
<endpoint address="http://localhost:8001/hello/servicemodelsamples"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a>Örnek  
 Dördüncü uç nokta adresi mutlak bir adres ve farklı bir aktarım belirtir—TCP. Temel adres adreste hiçbir rol oynamaz. Gerçek bitiş noktası adresi net.tcp://localhost:9000/servicemodelsamples/service olduğunu.  
  
```xml  
<endpoint address="net.tcp://localhost:9000/servicemodelsamples/service"  
    binding="netTcpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a>Örnek  
 Çalışma zamanı tarafından sağlanan varsayılan uç noktaları kullanmak için, kod veya yapılandırma dosyasında herhangi bir hizmet uç noktası belirtmeyin. Bu örnekte, hizmet açıldığında çalışma süresi varsayılan uç noktaları oluşturur. Varsayılan uç noktalar, bağlamalar ve davranışlar hakkında daha fazla bilgi için wcf hizmetleri için [Basitleştirilmiş Yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md) ve [Basitleştirilmiş Yapılandırma'ya](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)bakın.  
  
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
