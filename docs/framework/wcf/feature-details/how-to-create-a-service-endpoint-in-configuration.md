---
title: 'Nasıl yapılır: Yapılandırma İçinde Hizmet Uç Noktası Oluşturma'
ms.date: 06/16/2016
ms.assetid: f474e25d-2a27-4f31-84c5-395c442b8e70
ms.openlocfilehash: 63a40576b805952197cec5af2f89a5dc4b5d3545
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61787653"
---
# <a name="how-to-create-a-service-endpoint-in-configuration"></a><span data-ttu-id="76eb9-102">Nasıl yapılır: Yapılandırma İçinde Hizmet Uç Noktası Oluşturma</span><span class="sxs-lookup"><span data-stu-id="76eb9-102">How to: Create a Service Endpoint in Configuration</span></span>
<span data-ttu-id="76eb9-103">Uç noktaları, istemcilerin bir Windows Communication Foundation (WCF) hizmeti sunan işlevine erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="76eb9-103">Endpoints provide clients with access to the functionality a Windows Communication Foundation (WCF) service offers.</span></span> <span data-ttu-id="76eb9-104">Göreli ve mutlak uç nokta adresleri bir birleşimini kullanarak bir hizmet için bir veya daha fazla uç nokta tanımlayabilirsiniz veya herhangi bir hizmet uç noktaları tanımlamazsanız, çalışma zamanı bazı varsayılan olarak, sağlar.</span><span class="sxs-lookup"><span data-stu-id="76eb9-104">You can define one or more endpoints for a service by using a combination of relative and absolute endpoint addresses, or if you do not define any service endpoints, the runtime provides some by default for you.</span></span> <span data-ttu-id="76eb9-105">Bu konuda, göreli ve mutlak adreslerini içeren bir yapılandırma dosyası kullanarak uç noktalarını eklemek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="76eb9-105">This topic shows how to add endpoints using a configuration file that contain both relative and absolute addresses.</span></span>  
  
## <a name="example"></a><span data-ttu-id="76eb9-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="76eb9-106">Example</span></span>  
 <span data-ttu-id="76eb9-107">Temel adres ve beş uç noktaları aşağıdaki hizmet yapılandırmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="76eb9-107">The following service configuration specifies a base address and five endpoints.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="76eb9-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="76eb9-108">Example</span></span>  
 <span data-ttu-id="76eb9-109">Taban adresi kullanarak belirtilen `add` öğede hizmet/konak/baseAddresses aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="76eb9-109">The base address is specified using the `add` element, under service/host/baseAddresses, as shown in the following sample.</span></span>  
  
```xml  
<service   
    name="Microsoft.ServiceModel.Samples.CalculatorService">  
  <host>  
    <baseAddresses>  
      <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
    </baseAddresses>  
  </host>  
```  
  
## <a name="example"></a><span data-ttu-id="76eb9-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="76eb9-110">Example</span></span>  
 <span data-ttu-id="76eb9-111">Aşağıdaki örnekte gösterilen ilk uç nokta tanımı taban adresini ve hizmetin göreli adresini Tekdüzen Kaynak Tanımlayıcısı (URI) oluşturma kuralları aşağıdaki uç nokta adresi olduğu anlamına gelir göreli bir adresi belirtir.</span><span class="sxs-lookup"><span data-stu-id="76eb9-111">The first endpoint definition shown in the following sample specifies a relative address, which means the endpoint address is a combination of the base address and the relative address following the rules of Uniform Resource Identifier (URI) composition.</span></span> <span data-ttu-id="76eb9-112">Hizmetin göreli adresini boştur (""), uç nokta adresini temel adresi ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="76eb9-112">The relative address is empty (""), so the endpoint address is the same as the base address.</span></span> <span data-ttu-id="76eb9-113">Gerçek bir uç nokta adresi `http://localhost:8000/servicemodelsamples/service`.</span><span class="sxs-lookup"><span data-stu-id="76eb9-113">The actual endpoint address is `http://localhost:8000/servicemodelsamples/service`.</span></span>  
  
```xml  
<endpoint address=""   
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="76eb9-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="76eb9-114">Example</span></span>  
 <span data-ttu-id="76eb9-115">İkinci uç nokta tanımı, ayrıca aşağıdaki örnek yapılandırmada gösterildiği gibi bir göreli adresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="76eb9-115">The second endpoint definition also specifies a relative address, as shown in the following sample configuration.</span></span> <span data-ttu-id="76eb9-116">Hizmetin göreli adresini "test" öğesine taban adresi olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="76eb9-116">The relative address, "test", is appended to the base address.</span></span> <span data-ttu-id="76eb9-117">Gerçek bir uç nokta adresi `http://localhost:8000/servicemodelsamples/service/test`.</span><span class="sxs-lookup"><span data-stu-id="76eb9-117">The actual endpoint address is `http://localhost:8000/servicemodelsamples/service/test`.</span></span>  
  
```xml  
<endpoint address="/test"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="76eb9-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="76eb9-118">Example</span></span>  
 <span data-ttu-id="76eb9-119">Aşağıdaki örnek yapılandırmada gösterildiği gibi üçüncü bir uç nokta tanımı mutlak bir adres belirtir.</span><span class="sxs-lookup"><span data-stu-id="76eb9-119">The third endpoint definition specifies an absolute address, as shown in the following sample configuration.</span></span> <span data-ttu-id="76eb9-120">Temel adres, adres, hiçbir rol oynar.</span><span class="sxs-lookup"><span data-stu-id="76eb9-120">The base address plays no role in the address.</span></span> <span data-ttu-id="76eb9-121">Gerçek bir uç nokta adresi `http://localhost:8001/hello/servicemodelsamples`.</span><span class="sxs-lookup"><span data-stu-id="76eb9-121">The actual endpoint address is `http://localhost:8001/hello/servicemodelsamples`.</span></span>  
  
```xml  
<endpoint address="http://localhost:8001/hello/servicemodelsamples"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="76eb9-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="76eb9-122">Example</span></span>  
 <span data-ttu-id="76eb9-123">Mutlak bir adres ve farklı bir aktarım dördüncü uç nokta adresini belirtir; TCP.</span><span class="sxs-lookup"><span data-stu-id="76eb9-123">The fourth endpoint address specifies an absolute address and a different transport—TCP.</span></span> <span data-ttu-id="76eb9-124">Temel adres, adres, hiçbir rol oynar.</span><span class="sxs-lookup"><span data-stu-id="76eb9-124">The base address plays no role in the address.</span></span> <span data-ttu-id="76eb9-125">Gerçek bir uç nokta adresi olduğunu NET.TCP://localhost: 9000/servicemodelsamples/hizmet.</span><span class="sxs-lookup"><span data-stu-id="76eb9-125">The actual endpoint address is net.tcp://localhost:9000/servicemodelsamples/service.</span></span>  
  
```xml  
<endpoint address="net.tcp://localhost:9000/servicemodelsamples/service"  
    binding="netTcpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="76eb9-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="76eb9-126">Example</span></span>  
 <span data-ttu-id="76eb9-127">Çalışma zamanı tarafından sağlanan varsayılan uç noktalarını kullanacak şekilde herhangi bir hizmet uç noktaları kod veya yapılandırma dosyasını belirtmeyin.</span><span class="sxs-lookup"><span data-stu-id="76eb9-127">To use the default endpoints provided by the runtime, do not specify any service endpoints in either the code or the configuration file.</span></span> <span data-ttu-id="76eb9-128">Bir hizmeti açtığınızda bu örnekte, çalışma zamanı varsayılan uç noktaları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="76eb9-128">In this example, the runtime creates the default endpoints when the service is opened.</span></span> <span data-ttu-id="76eb9-129">Varsayılan uç noktaları, bağlamalar ve davranışları hakkında daha fazla bilgi için bkz. [Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="76eb9-129">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
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
