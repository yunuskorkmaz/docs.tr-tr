---
title: 'Nasıl yapılır: Yapılandırma İçinde Hizmet Uç Noktası Oluşturma'
ms.date: 06/16/2016
ms.assetid: f474e25d-2a27-4f31-84c5-395c442b8e70
ms.openlocfilehash: f1a2696e2aeb8d0c704d008b064a8f8c8b0745d5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33490233"
---
# <a name="how-to-create-a-service-endpoint-in-configuration"></a><span data-ttu-id="660bf-102">Nasıl yapılır: Yapılandırma İçinde Hizmet Uç Noktası Oluşturma</span><span class="sxs-lookup"><span data-stu-id="660bf-102">How to: Create a Service Endpoint in Configuration</span></span>
<span data-ttu-id="660bf-103">Uç noktaları için bir Windows Communication Foundation (WCF) hizmeti sunan işlevlere erişimi istemcilerle sağlar.</span><span class="sxs-lookup"><span data-stu-id="660bf-103">Endpoints provide clients with access to the functionality a Windows Communication Foundation (WCF) service offers.</span></span> <span data-ttu-id="660bf-104">Mutlak bitiş noktası adreslerini birleşimini kullanarak bir hizmet için bir veya daha fazla uç noktaları tanımlayabilirsiniz, veya tüm hizmet uç noktaları tanımlamıyorsa, çalışma zamanı bazı varsayılan olarak, sağlar.</span><span class="sxs-lookup"><span data-stu-id="660bf-104">You can define one or more endpoints for a service by using a combination of relative and absolute endpoint addresses, or if you do not define any service endpoints, the runtime provides some by default for you.</span></span> <span data-ttu-id="660bf-105">Bu konu, göreli ve mutlak adreslerini içeren bir yapılandırma dosyası kullanarak uç noktaları ekleme gösterir.</span><span class="sxs-lookup"><span data-stu-id="660bf-105">This topic shows how to add endpoints using a configuration file that contain both relative and absolute addresses.</span></span>  
  
## <a name="example"></a><span data-ttu-id="660bf-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="660bf-106">Example</span></span>  
 <span data-ttu-id="660bf-107">Aşağıdaki hizmet yapılandırmasını temel adres ve beş uç noktaları belirtir.</span><span class="sxs-lookup"><span data-stu-id="660bf-107">The following service configuration specifies a base address and five endpoints.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="660bf-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="660bf-108">Example</span></span>  
 <span data-ttu-id="660bf-109">Taban adresi kullanarak belirtilen `add` hizmeti/ana/baseAddresses aşağıdaki örnekte gösterildiği gibi altında öğesi.</span><span class="sxs-lookup"><span data-stu-id="660bf-109">The base address is specified using the `add` element, under service/host/baseAddresses, as shown in the following sample.</span></span>  
  
```xml  
<service   
    name="Microsoft.ServiceModel.Samples.CalculatorService">  
  <host>  
    <baseAddresses>  
      <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
    </baseAddresses>  
  </host>  
```  
  
## <a name="example"></a><span data-ttu-id="660bf-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="660bf-110">Example</span></span>  
 <span data-ttu-id="660bf-111">Aşağıdaki örnekte gösterilen ilk uç nokta tanımı taban adresini ve Tekdüzen Kaynak Tanımlayıcısı (URI) birleşim kurallar aşağıdaki ilgili adresi bileşimini uç nokta adresi gelir bir göreli adresi belirtir.</span><span class="sxs-lookup"><span data-stu-id="660bf-111">The first endpoint definition shown in the following sample specifies a relative address, which means the endpoint address is a combination of the base address and the relative address following the rules of Uniform Resource Identifier (URI) composition.</span></span> <span data-ttu-id="660bf-112">Göreli adresi boştur (""), uç nokta adresi taban adresi ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="660bf-112">The relative address is empty (""), so the endpoint address is the same as the base address.</span></span> <span data-ttu-id="660bf-113">Gerçek bitiş adresi http://localhost:8000/servicemodelsamples/service.</span><span class="sxs-lookup"><span data-stu-id="660bf-113">The actual endpoint address is http://localhost:8000/servicemodelsamples/service.</span></span>  
  
```xml  
<endpoint address=""   
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="660bf-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="660bf-114">Example</span></span>  
 <span data-ttu-id="660bf-115">İkinci uç nokta tanımı, ayrıca aşağıdaki örnek yapılandırmada gösterildiği gibi bir göreli adresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="660bf-115">The second endpoint definition also specifies a relative address, as shown in the following sample configuration.</span></span> <span data-ttu-id="660bf-116">Göreli adresi "test", taban adresi eklenir.</span><span class="sxs-lookup"><span data-stu-id="660bf-116">The relative address, "test", is appended to the base address.</span></span> <span data-ttu-id="660bf-117">Gerçek bitiş adresi http://localhost:8000/servicemodelsamples/service/test.</span><span class="sxs-lookup"><span data-stu-id="660bf-117">The actual endpoint address is http://localhost:8000/servicemodelsamples/service/test.</span></span>  
  
```xml  
<endpoint address="/test"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="660bf-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="660bf-118">Example</span></span>  
 <span data-ttu-id="660bf-119">Aşağıdaki örnek yapılandırmada gösterildiği gibi üçüncü uç nokta tanımı mutlak bir adres belirtir.</span><span class="sxs-lookup"><span data-stu-id="660bf-119">The third endpoint definition specifies an absolute address, as shown in the following sample configuration.</span></span> <span data-ttu-id="660bf-120">Temel adres adresi herhangi bir rol oynar.</span><span class="sxs-lookup"><span data-stu-id="660bf-120">The base address plays no role in the address.</span></span> <span data-ttu-id="660bf-121">Gerçek bitiş adresi http://localhost:8001/hello/servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="660bf-121">The actual endpoint address is http://localhost:8001/hello/servicemodelsamples.</span></span>  
  
```xml  
<endpoint address="http://localhost:8001/hello/servicemodelsamples"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="660bf-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="660bf-122">Example</span></span>  
 <span data-ttu-id="660bf-123">Mutlak bir adres ve farklı bir aktarım dördüncü uç noktası adresi belirtir — TCP.</span><span class="sxs-lookup"><span data-stu-id="660bf-123">The fourth endpoint address specifies an absolute address and a different transport—TCP.</span></span> <span data-ttu-id="660bf-124">Temel adres adresi herhangi bir rol oynar.</span><span class="sxs-lookup"><span data-stu-id="660bf-124">The base address plays no role in the address.</span></span> <span data-ttu-id="660bf-125">Gerçek bitiş adresini net.tcp://localhost olan: servicemodelsamples/9000/hizmet.</span><span class="sxs-lookup"><span data-stu-id="660bf-125">The actual endpoint address is net.tcp://localhost:9000/servicemodelsamples/service.</span></span>  
  
```xml  
<endpoint address="net.tcp://localhost:9000/servicemodelsamples/service"  
    binding="netTcpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="660bf-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="660bf-126">Example</span></span>  
 <span data-ttu-id="660bf-127">Çalışma zamanı tarafından sağlanan varsayılan uç noktaları kullanmak için tüm hizmet uç noktaları kod veya yapılandırma dosyasını belirtmeyin.</span><span class="sxs-lookup"><span data-stu-id="660bf-127">To use the default endpoints provided by the runtime, do not specify any service endpoints in either the code or the configuration file.</span></span> <span data-ttu-id="660bf-128">Hizmet açıldığında, bu örnekte, varsayılan uç noktalar çalışma zamanı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="660bf-128">In this example, the runtime creates the default endpoints when the service is opened.</span></span> <span data-ttu-id="660bf-129">Varsayılan uç noktalar, bağlamaları ve davranışları hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="660bf-129">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
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
