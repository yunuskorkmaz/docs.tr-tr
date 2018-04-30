---
title: 'Nasıl yapılır: Yapılandırma İçinde Hizmet Uç Noktası Oluşturma'
ms.custom: ''
ms.date: 06/16/2016
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f474e25d-2a27-4f31-84c5-395c442b8e70
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ecb7345dbbff04388edb39dae9e5c05f2c40fd75
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-create-a-service-endpoint-in-configuration"></a>Nasıl yapılır: Yapılandırma İçinde Hizmet Uç Noktası Oluşturma
Uç noktaları sağlamak için işlevlere erişimi istemcilerle bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] hizmet sunar. Mutlak bitiş noktası adreslerini birleşimini kullanarak bir hizmet için bir veya daha fazla uç noktaları tanımlayabilirsiniz, veya tüm hizmet uç noktaları tanımlamıyorsa, çalışma zamanı bazı varsayılan olarak, sağlar. Bu konu, göreli ve mutlak adreslerini içeren bir yapılandırma dosyası kullanarak uç noktaları ekleme gösterir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki hizmet yapılandırmasını temel adres ve beş uç noktaları belirtir.  
  
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
 Taban adresi kullanarak belirtilen `add` hizmeti/ana/baseAddresses aşağıdaki örnekte gösterildiği gibi altında öğesi.  
  
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
 Aşağıdaki örnekte gösterilen ilk uç nokta tanımı taban adresini ve Tekdüzen Kaynak Tanımlayıcısı (URI) birleşim kurallar aşağıdaki ilgili adresi bileşimini uç nokta adresi gelir bir göreli adresi belirtir. Göreli adresi boştur (""), uç nokta adresi taban adresi ile aynıdır. Gerçek bitiş adresi http://localhost:8000/servicemodelsamples/service.  
  
```xml  
<endpoint address=""   
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a>Örnek  
 İkinci uç nokta tanımı, ayrıca aşağıdaki örnek yapılandırmada gösterildiği gibi bir göreli adresini belirtir. Göreli adresi "test", taban adresi eklenir. Gerçek bitiş adresi http://localhost:8000/servicemodelsamples/service/test.  
  
```xml  
<endpoint address="/test"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek yapılandırmada gösterildiği gibi üçüncü uç nokta tanımı mutlak bir adres belirtir. Temel adres adresi herhangi bir rol oynar. Gerçek bitiş adresi http://localhost:8001/hello/servicemodelsamples.  
  
```xml  
<endpoint address="http://localhost:8001/hello/servicemodelsamples"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a>Örnek  
 Mutlak bir adres ve farklı bir aktarım dördüncü uç noktası adresi belirtir — TCP. Temel adres adresi herhangi bir rol oynar. Gerçek bitiş adresini net.tcp://localhost olan: servicemodelsamples/9000/hizmet.  
  
```xml  
<endpoint address="net.tcp://localhost:9000/servicemodelsamples/service"  
    binding="netTcpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a>Örnek  
 Çalışma zamanı tarafından sağlanan varsayılan uç noktaları kullanmak için tüm hizmet uç noktaları kod veya yapılandırma dosyasını belirtmeyin. Hizmet açıldığında, bu örnekte, varsayılan uç noktalar çalışma zamanı oluşturur. Varsayılan uç noktalar, bağlamaları ve davranışları hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
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
