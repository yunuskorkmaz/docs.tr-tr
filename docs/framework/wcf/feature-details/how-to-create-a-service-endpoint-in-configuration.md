---
title: 'Nasıl yapılır: Yapılandırma İçinde Hizmet Uç Noktası Oluşturma'
ms.date: 06/16/2016
ms.assetid: f474e25d-2a27-4f31-84c5-395c442b8e70
ms.openlocfilehash: 56b29da0c147eb9e73a08e2875e33e384da729ed
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598924"
---
# <a name="how-to-create-a-service-endpoint-in-configuration"></a><span data-ttu-id="db8cc-102">Nasıl yapılır: Yapılandırma İçinde Hizmet Uç Noktası Oluşturma</span><span class="sxs-lookup"><span data-stu-id="db8cc-102">How to: Create a Service Endpoint in Configuration</span></span>
<span data-ttu-id="db8cc-103">Uç noktalar, istemcilere Windows Communication Foundation (WCF) hizmet tekliflerini erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="db8cc-103">Endpoints provide clients with access to the functionality a Windows Communication Foundation (WCF) service offers.</span></span> <span data-ttu-id="db8cc-104">Bir hizmet için bir veya daha fazla uç noktası, göreli ve mutlak uç nokta adreslerinin birleşimini kullanarak tanımlayabilir veya herhangi bir hizmet uç noktası tanımlamadıysanız, çalışma zamanı sizin için varsayılan olarak bir değer sağlar.</span><span class="sxs-lookup"><span data-stu-id="db8cc-104">You can define one or more endpoints for a service by using a combination of relative and absolute endpoint addresses, or if you do not define any service endpoints, the runtime provides some by default for you.</span></span> <span data-ttu-id="db8cc-105">Bu konu, hem göreli hem de mutlak adresler içeren bir yapılandırma dosyası kullanarak uç noktaların nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="db8cc-105">This topic shows how to add endpoints using a configuration file that contain both relative and absolute addresses.</span></span>  
  
## <a name="example"></a><span data-ttu-id="db8cc-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="db8cc-106">Example</span></span>  
 <span data-ttu-id="db8cc-107">Aşağıdaki hizmet yapılandırması, bir temel adresi ve beş uç noktasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="db8cc-107">The following service configuration specifies a base address and five endpoints.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="db8cc-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="db8cc-108">Example</span></span>  
 <span data-ttu-id="db8cc-109">Temel adres, `add` Aşağıdaki örnekte gösterildiği gibi hizmet/ana bilgisayar/baseAddresses altında öğesi kullanılarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="db8cc-109">The base address is specified using the `add` element, under service/host/baseAddresses, as shown in the following sample.</span></span>  
  
```xml  
<service
    name="Microsoft.ServiceModel.Samples.CalculatorService">  
  <host>  
    <baseAddresses>  
      <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
    </baseAddresses>  
  </host>  
```  
  
## <a name="example"></a><span data-ttu-id="db8cc-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="db8cc-110">Example</span></span>  
 <span data-ttu-id="db8cc-111">Aşağıdaki örnekte gösterilen ilk uç nokta tanımı göreli bir adresi belirtir. Bu, uç nokta adresinin temel adresin bir birleşimi ve Tekdüzen Kaynak tanımlayıcısı (URI) kompozisyonunun kurallarından sonraki göreli adres olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="db8cc-111">The first endpoint definition shown in the following sample specifies a relative address, which means the endpoint address is a combination of the base address and the relative address following the rules of Uniform Resource Identifier (URI) composition.</span></span> <span data-ttu-id="db8cc-112">Göreli adres boş ("") olduğundan, uç nokta adresi taban adresle aynı olur.</span><span class="sxs-lookup"><span data-stu-id="db8cc-112">The relative address is empty (""), so the endpoint address is the same as the base address.</span></span> <span data-ttu-id="db8cc-113">Gerçek uç nokta adresi `http://localhost:8000/servicemodelsamples/service` .</span><span class="sxs-lookup"><span data-stu-id="db8cc-113">The actual endpoint address is `http://localhost:8000/servicemodelsamples/service`.</span></span>  
  
```xml  
<endpoint address=""
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="db8cc-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="db8cc-114">Example</span></span>  
 <span data-ttu-id="db8cc-115">İkinci uç nokta tanımı, aşağıdaki örnek yapılandırmada gösterildiği gibi göreli bir adresi de belirtir.</span><span class="sxs-lookup"><span data-stu-id="db8cc-115">The second endpoint definition also specifies a relative address, as shown in the following sample configuration.</span></span> <span data-ttu-id="db8cc-116">Göreli adres "test", temel adrese eklenir.</span><span class="sxs-lookup"><span data-stu-id="db8cc-116">The relative address, "test", is appended to the base address.</span></span> <span data-ttu-id="db8cc-117">Gerçek uç nokta adresi `http://localhost:8000/servicemodelsamples/service/test` .</span><span class="sxs-lookup"><span data-stu-id="db8cc-117">The actual endpoint address is `http://localhost:8000/servicemodelsamples/service/test`.</span></span>  
  
```xml  
<endpoint address="/test"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="db8cc-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="db8cc-118">Example</span></span>  
 <span data-ttu-id="db8cc-119">Üçüncü uç nokta tanımı, aşağıdaki örnek yapılandırmada gösterildiği gibi mutlak bir adresi belirtir.</span><span class="sxs-lookup"><span data-stu-id="db8cc-119">The third endpoint definition specifies an absolute address, as shown in the following sample configuration.</span></span> <span data-ttu-id="db8cc-120">Taban adresi adreste hiçbir rol oynamıyor.</span><span class="sxs-lookup"><span data-stu-id="db8cc-120">The base address plays no role in the address.</span></span> <span data-ttu-id="db8cc-121">Gerçek uç nokta adresi `http://localhost:8001/hello/servicemodelsamples` .</span><span class="sxs-lookup"><span data-stu-id="db8cc-121">The actual endpoint address is `http://localhost:8001/hello/servicemodelsamples`.</span></span>  
  
```xml  
<endpoint address="http://localhost:8001/hello/servicemodelsamples"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="db8cc-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="db8cc-122">Example</span></span>  
 <span data-ttu-id="db8cc-123">Dördüncü uç nokta adresi, bir mutlak adresi ve farklı bir aktarımı (TCP) belirtir.</span><span class="sxs-lookup"><span data-stu-id="db8cc-123">The fourth endpoint address specifies an absolute address and a different transport—TCP.</span></span> <span data-ttu-id="db8cc-124">Taban adresi adreste hiçbir rol oynamıyor.</span><span class="sxs-lookup"><span data-stu-id="db8cc-124">The base address plays no role in the address.</span></span> <span data-ttu-id="db8cc-125">Gerçek uç nokta adresi net. TCP:/localhost: 9000/servicemodelsamples/service ' dir.</span><span class="sxs-lookup"><span data-stu-id="db8cc-125">The actual endpoint address is net.tcp://localhost:9000/servicemodelsamples/service.</span></span>  
  
```xml  
<endpoint address="net.tcp://localhost:9000/servicemodelsamples/service"  
    binding="netTcpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="db8cc-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="db8cc-126">Example</span></span>  
 <span data-ttu-id="db8cc-127">Çalışma zamanı tarafından belirtilen varsayılan uç noktaları kullanmak için, kodda veya yapılandırma dosyasında herhangi bir hizmet uç noktası belirtmeyin.</span><span class="sxs-lookup"><span data-stu-id="db8cc-127">To use the default endpoints provided by the runtime, do not specify any service endpoints in either the code or the configuration file.</span></span> <span data-ttu-id="db8cc-128">Bu örnekte, çalışma zamanı, hizmet açıldığında varsayılan uç noktaları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="db8cc-128">In this example, the runtime creates the default endpoints when the service is opened.</span></span> <span data-ttu-id="db8cc-129">Varsayılan uç noktalar, bağlamalar ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="db8cc-129">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../simplified-configuration.md) and [Simplified Configuration for WCF Services](../samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
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
