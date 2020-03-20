---
title: 'Nasıl yapılır: Yapılandırma İçinde Hizmet Uç Noktası Oluşturma'
ms.date: 06/16/2016
ms.assetid: f474e25d-2a27-4f31-84c5-395c442b8e70
ms.openlocfilehash: 9687d9537d6f166a02b79261743050168f677261
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185007"
---
# <a name="how-to-create-a-service-endpoint-in-configuration"></a><span data-ttu-id="46abe-102">Nasıl yapılır: Yapılandırma İçinde Hizmet Uç Noktası Oluşturma</span><span class="sxs-lookup"><span data-stu-id="46abe-102">How to: Create a Service Endpoint in Configuration</span></span>
<span data-ttu-id="46abe-103">Uç noktalar, istemcilere Windows Communication Foundation (WCF) hizmetinin sunduğu işlevsellik lere erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="46abe-103">Endpoints provide clients with access to the functionality a Windows Communication Foundation (WCF) service offers.</span></span> <span data-ttu-id="46abe-104">Bir hizmet için bir veya daha fazla uç nokta, göreli ve mutlak uç nokta adreslerinin bir birleşimini kullanarak veya herhangi bir hizmet bitiş noktası tanımlamazsanız, çalışma süresi varsayılan olarak sizin için bazı sağlar.</span><span class="sxs-lookup"><span data-stu-id="46abe-104">You can define one or more endpoints for a service by using a combination of relative and absolute endpoint addresses, or if you do not define any service endpoints, the runtime provides some by default for you.</span></span> <span data-ttu-id="46abe-105">Bu konu, hem göreceli hem de mutlak adresleri içeren bir yapılandırma dosyasını kullanarak uç noktaların nasıl ekleyeceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="46abe-105">This topic shows how to add endpoints using a configuration file that contain both relative and absolute addresses.</span></span>  
  
## <a name="example"></a><span data-ttu-id="46abe-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="46abe-106">Example</span></span>  
 <span data-ttu-id="46abe-107">Aşağıdaki hizmet yapılandırması bir temel adres ve beş uç nokta belirtir.</span><span class="sxs-lookup"><span data-stu-id="46abe-107">The following service configuration specifies a base address and five endpoints.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="46abe-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="46abe-108">Example</span></span>  
 <span data-ttu-id="46abe-109">Temel adres, aşağıdaki `add` örnekte gösterildiği gibi hizmet/ana bilgisayar/baseAddresss altında öğe kullanılarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="46abe-109">The base address is specified using the `add` element, under service/host/baseAddresses, as shown in the following sample.</span></span>  
  
```xml  
<service
    name="Microsoft.ServiceModel.Samples.CalculatorService">  
  <host>  
    <baseAddresses>  
      <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
    </baseAddresses>  
  </host>  
```  
  
## <a name="example"></a><span data-ttu-id="46abe-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="46abe-110">Example</span></span>  
 <span data-ttu-id="46abe-111">Aşağıdaki örnekte gösterilen ilk uç nokta tanımı göreceli bir adres belirtir, bu da bitiş noktası adresinin temel adres ve Tekdüzen Kaynak Tanımlayıcı (URI) kompozisyonunun kurallarını izleyen göreli adresin birleşimi olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="46abe-111">The first endpoint definition shown in the following sample specifies a relative address, which means the endpoint address is a combination of the base address and the relative address following the rules of Uniform Resource Identifier (URI) composition.</span></span> <span data-ttu-id="46abe-112">Göreli adres boş (""), bu nedenle bitiş noktası adresi temel adresle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="46abe-112">The relative address is empty (""), so the endpoint address is the same as the base address.</span></span> <span data-ttu-id="46abe-113">Gerçek bitiş noktası `http://localhost:8000/servicemodelsamples/service`adresi .</span><span class="sxs-lookup"><span data-stu-id="46abe-113">The actual endpoint address is `http://localhost:8000/servicemodelsamples/service`.</span></span>  
  
```xml  
<endpoint address=""
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="46abe-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="46abe-114">Example</span></span>  
 <span data-ttu-id="46abe-115">İkinci uç nokta tanımı, aşağıdaki örnek yapılandırmada gösterildiği gibi göreli bir adres de belirtir.</span><span class="sxs-lookup"><span data-stu-id="46abe-115">The second endpoint definition also specifies a relative address, as shown in the following sample configuration.</span></span> <span data-ttu-id="46abe-116">Göreli adres, "test", temel adrese eklenir.</span><span class="sxs-lookup"><span data-stu-id="46abe-116">The relative address, "test", is appended to the base address.</span></span> <span data-ttu-id="46abe-117">Gerçek bitiş noktası `http://localhost:8000/servicemodelsamples/service/test`adresi .</span><span class="sxs-lookup"><span data-stu-id="46abe-117">The actual endpoint address is `http://localhost:8000/servicemodelsamples/service/test`.</span></span>  
  
```xml  
<endpoint address="/test"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="46abe-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="46abe-118">Example</span></span>  
 <span data-ttu-id="46abe-119">Üçüncü uç nokta tanımı, aşağıdaki örnek yapılandırmada gösterildiği gibi mutlak bir adres belirtir.</span><span class="sxs-lookup"><span data-stu-id="46abe-119">The third endpoint definition specifies an absolute address, as shown in the following sample configuration.</span></span> <span data-ttu-id="46abe-120">Temel adres adreste hiçbir rol oynamaz.</span><span class="sxs-lookup"><span data-stu-id="46abe-120">The base address plays no role in the address.</span></span> <span data-ttu-id="46abe-121">Gerçek bitiş noktası `http://localhost:8001/hello/servicemodelsamples`adresi .</span><span class="sxs-lookup"><span data-stu-id="46abe-121">The actual endpoint address is `http://localhost:8001/hello/servicemodelsamples`.</span></span>  
  
```xml  
<endpoint address="http://localhost:8001/hello/servicemodelsamples"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="46abe-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="46abe-122">Example</span></span>  
 <span data-ttu-id="46abe-123">Dördüncü uç nokta adresi mutlak bir adres ve farklı bir aktarım belirtir—TCP.</span><span class="sxs-lookup"><span data-stu-id="46abe-123">The fourth endpoint address specifies an absolute address and a different transport—TCP.</span></span> <span data-ttu-id="46abe-124">Temel adres adreste hiçbir rol oynamaz.</span><span class="sxs-lookup"><span data-stu-id="46abe-124">The base address plays no role in the address.</span></span> <span data-ttu-id="46abe-125">Gerçek bitiş noktası adresi net.tcp://localhost:9000/servicemodelsamples/service olduğunu.</span><span class="sxs-lookup"><span data-stu-id="46abe-125">The actual endpoint address is net.tcp://localhost:9000/servicemodelsamples/service.</span></span>  
  
```xml  
<endpoint address="net.tcp://localhost:9000/servicemodelsamples/service"  
    binding="netTcpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="46abe-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="46abe-126">Example</span></span>  
 <span data-ttu-id="46abe-127">Çalışma zamanı tarafından sağlanan varsayılan uç noktaları kullanmak için, kod veya yapılandırma dosyasında herhangi bir hizmet uç noktası belirtmeyin.</span><span class="sxs-lookup"><span data-stu-id="46abe-127">To use the default endpoints provided by the runtime, do not specify any service endpoints in either the code or the configuration file.</span></span> <span data-ttu-id="46abe-128">Bu örnekte, hizmet açıldığında çalışma süresi varsayılan uç noktaları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="46abe-128">In this example, the runtime creates the default endpoints when the service is opened.</span></span> <span data-ttu-id="46abe-129">Varsayılan uç noktalar, bağlamalar ve davranışlar hakkında daha fazla bilgi için wcf hizmetleri için [Basitleştirilmiş Yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md) ve [Basitleştirilmiş Yapılandırma'ya](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="46abe-129">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
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
