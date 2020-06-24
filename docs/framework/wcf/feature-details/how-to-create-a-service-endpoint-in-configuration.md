---
title: 'Nasıl yapılır: Yapılandırma İçinde Hizmet Uç Noktası Oluşturma'
description: Hem göreli hem de mutlak adresler içeren bir yapılandırma dosyası kullanarak bir WCF hizmeti için uç noktaların nasıl ekleneceğini öğrenin.
ms.date: 06/16/2016
ms.assetid: f474e25d-2a27-4f31-84c5-395c442b8e70
ms.openlocfilehash: 184bcb5f7f3e83f12608757b55bbb4d57be58f7d
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247071"
---
# <a name="how-to-create-a-service-endpoint-in-configuration"></a><span data-ttu-id="b762e-103">Nasıl yapılır: Yapılandırma İçinde Hizmet Uç Noktası Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b762e-103">How to: Create a Service Endpoint in Configuration</span></span>
<span data-ttu-id="b762e-104">Uç noktalar, istemcilere Windows Communication Foundation (WCF) hizmet tekliflerini erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="b762e-104">Endpoints provide clients with access to the functionality a Windows Communication Foundation (WCF) service offers.</span></span> <span data-ttu-id="b762e-105">Bir hizmet için bir veya daha fazla uç noktası, göreli ve mutlak uç nokta adreslerinin birleşimini kullanarak tanımlayabilir veya herhangi bir hizmet uç noktası tanımlamadıysanız, çalışma zamanı sizin için varsayılan olarak bir değer sağlar.</span><span class="sxs-lookup"><span data-stu-id="b762e-105">You can define one or more endpoints for a service by using a combination of relative and absolute endpoint addresses, or if you do not define any service endpoints, the runtime provides some by default for you.</span></span> <span data-ttu-id="b762e-106">Bu konu, hem göreli hem de mutlak adresler içeren bir yapılandırma dosyası kullanarak uç noktaların nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b762e-106">This topic shows how to add endpoints using a configuration file that contain both relative and absolute addresses.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b762e-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="b762e-107">Example</span></span>  
 <span data-ttu-id="b762e-108">Aşağıdaki hizmet yapılandırması, bir temel adresi ve beş uç noktasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b762e-108">The following service configuration specifies a base address and five endpoints.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="b762e-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="b762e-109">Example</span></span>  
 <span data-ttu-id="b762e-110">Temel adres, `add` Aşağıdaki örnekte gösterildiği gibi hizmet/ana bilgisayar/baseAddresses altında öğesi kullanılarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="b762e-110">The base address is specified using the `add` element, under service/host/baseAddresses, as shown in the following sample.</span></span>  
  
```xml  
<service
    name="Microsoft.ServiceModel.Samples.CalculatorService">  
  <host>  
    <baseAddresses>  
      <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
    </baseAddresses>  
  </host>  
```  
  
## <a name="example"></a><span data-ttu-id="b762e-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="b762e-111">Example</span></span>  
 <span data-ttu-id="b762e-112">Aşağıdaki örnekte gösterilen ilk uç nokta tanımı göreli bir adresi belirtir. Bu, uç nokta adresinin temel adresin bir birleşimi ve Tekdüzen Kaynak tanımlayıcısı (URI) kompozisyonunun kurallarından sonraki göreli adres olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="b762e-112">The first endpoint definition shown in the following sample specifies a relative address, which means the endpoint address is a combination of the base address and the relative address following the rules of Uniform Resource Identifier (URI) composition.</span></span> <span data-ttu-id="b762e-113">Göreli adres boş ("") olduğundan, uç nokta adresi taban adresle aynı olur.</span><span class="sxs-lookup"><span data-stu-id="b762e-113">The relative address is empty (""), so the endpoint address is the same as the base address.</span></span> <span data-ttu-id="b762e-114">Gerçek uç nokta adresi `http://localhost:8000/servicemodelsamples/service` .</span><span class="sxs-lookup"><span data-stu-id="b762e-114">The actual endpoint address is `http://localhost:8000/servicemodelsamples/service`.</span></span>  
  
```xml  
<endpoint address=""
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="b762e-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="b762e-115">Example</span></span>  
 <span data-ttu-id="b762e-116">İkinci uç nokta tanımı, aşağıdaki örnek yapılandırmada gösterildiği gibi göreli bir adresi de belirtir.</span><span class="sxs-lookup"><span data-stu-id="b762e-116">The second endpoint definition also specifies a relative address, as shown in the following sample configuration.</span></span> <span data-ttu-id="b762e-117">Göreli adres "test", temel adrese eklenir.</span><span class="sxs-lookup"><span data-stu-id="b762e-117">The relative address, "test", is appended to the base address.</span></span> <span data-ttu-id="b762e-118">Gerçek uç nokta adresi `http://localhost:8000/servicemodelsamples/service/test` .</span><span class="sxs-lookup"><span data-stu-id="b762e-118">The actual endpoint address is `http://localhost:8000/servicemodelsamples/service/test`.</span></span>  
  
```xml  
<endpoint address="/test"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="b762e-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="b762e-119">Example</span></span>  
 <span data-ttu-id="b762e-120">Üçüncü uç nokta tanımı, aşağıdaki örnek yapılandırmada gösterildiği gibi mutlak bir adresi belirtir.</span><span class="sxs-lookup"><span data-stu-id="b762e-120">The third endpoint definition specifies an absolute address, as shown in the following sample configuration.</span></span> <span data-ttu-id="b762e-121">Taban adresi adreste hiçbir rol oynamıyor.</span><span class="sxs-lookup"><span data-stu-id="b762e-121">The base address plays no role in the address.</span></span> <span data-ttu-id="b762e-122">Gerçek uç nokta adresi `http://localhost:8001/hello/servicemodelsamples` .</span><span class="sxs-lookup"><span data-stu-id="b762e-122">The actual endpoint address is `http://localhost:8001/hello/servicemodelsamples`.</span></span>  
  
```xml  
<endpoint address="http://localhost:8001/hello/servicemodelsamples"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="b762e-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="b762e-123">Example</span></span>  
 <span data-ttu-id="b762e-124">Dördüncü uç nokta adresi, bir mutlak adresi ve farklı bir aktarımı (TCP) belirtir.</span><span class="sxs-lookup"><span data-stu-id="b762e-124">The fourth endpoint address specifies an absolute address and a different transport—TCP.</span></span> <span data-ttu-id="b762e-125">Taban adresi adreste hiçbir rol oynamıyor.</span><span class="sxs-lookup"><span data-stu-id="b762e-125">The base address plays no role in the address.</span></span> <span data-ttu-id="b762e-126">Gerçek uç nokta adresi net. TCP:/localhost: 9000/servicemodelsamples/service ' dir.</span><span class="sxs-lookup"><span data-stu-id="b762e-126">The actual endpoint address is net.tcp://localhost:9000/servicemodelsamples/service.</span></span>  
  
```xml  
<endpoint address="net.tcp://localhost:9000/servicemodelsamples/service"  
    binding="netTcpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="b762e-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="b762e-127">Example</span></span>  
 <span data-ttu-id="b762e-128">Çalışma zamanı tarafından belirtilen varsayılan uç noktaları kullanmak için, kodda veya yapılandırma dosyasında herhangi bir hizmet uç noktası belirtmeyin.</span><span class="sxs-lookup"><span data-stu-id="b762e-128">To use the default endpoints provided by the runtime, do not specify any service endpoints in either the code or the configuration file.</span></span> <span data-ttu-id="b762e-129">Bu örnekte, çalışma zamanı, hizmet açıldığında varsayılan uç noktaları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b762e-129">In this example, the runtime creates the default endpoints when the service is opened.</span></span> <span data-ttu-id="b762e-130">Varsayılan uç noktalar, bağlamalar ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="b762e-130">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../simplified-configuration.md) and [Simplified Configuration for WCF Services](../samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
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
