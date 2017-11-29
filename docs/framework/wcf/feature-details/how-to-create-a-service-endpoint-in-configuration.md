---
title: "Nasıl yapılır: Yapılandırma İçinde Hizmet Uç Noktası Oluşturma"
ms.custom: 
ms.date: 06/16/2016
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f474e25d-2a27-4f31-84c5-395c442b8e70
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: bf9b6eed2ce4270c9faecc27cb4626a155eb4a6c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-a-service-endpoint-in-configuration"></a><span data-ttu-id="27502-102">Nasıl yapılır: Yapılandırma İçinde Hizmet Uç Noktası Oluşturma</span><span class="sxs-lookup"><span data-stu-id="27502-102">How to: Create a Service Endpoint in Configuration</span></span>
<span data-ttu-id="27502-103">Uç noktaları sağlamak için işlevlere erişimi istemcilerle bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] hizmet sunar.</span><span class="sxs-lookup"><span data-stu-id="27502-103">Endpoints provide clients with access to the functionality a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service offers.</span></span> <span data-ttu-id="27502-104">Mutlak bitiş noktası adreslerini birleşimini kullanarak bir hizmet için bir veya daha fazla uç noktaları tanımlayabilirsiniz, veya tüm hizmet uç noktaları tanımlamıyorsa, çalışma zamanı bazı varsayılan olarak, sağlar.</span><span class="sxs-lookup"><span data-stu-id="27502-104">You can define one or more endpoints for a service by using a combination of relative and absolute endpoint addresses, or if you do not define any service endpoints, the runtime provides some by default for you.</span></span> <span data-ttu-id="27502-105">Bu konu, göreli ve mutlak adreslerini içeren bir yapılandırma dosyası kullanarak uç noktaları ekleme gösterir.</span><span class="sxs-lookup"><span data-stu-id="27502-105">This topic shows how to add endpoints using a configuration file that contain both relative and absolute addresses.</span></span>  
  
## <a name="example"></a><span data-ttu-id="27502-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="27502-106">Example</span></span>  
 <span data-ttu-id="27502-107">Aşağıdaki hizmet yapılandırmasını temel adres ve beş uç noktaları belirtir.</span><span class="sxs-lookup"><span data-stu-id="27502-107">The following service configuration specifies a base address and five endpoints.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="27502-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="27502-108">Example</span></span>  
 <span data-ttu-id="27502-109">Taban adresi kullanarak belirtilen `add` hizmeti/ana/baseAddresses aşağıdaki örnekte gösterildiği gibi altında öğesi.</span><span class="sxs-lookup"><span data-stu-id="27502-109">The base address is specified using the `add` element, under service/host/baseAddresses, as shown in the following sample.</span></span>  
  
```xml  
<service   
    name="Microsoft.ServiceModel.Samples.CalculatorService">  
  <host>  
    <baseAddresses>  
      <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
    </baseAddresses>  
  </host>  
```  
  
## <a name="example"></a><span data-ttu-id="27502-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="27502-110">Example</span></span>  
 <span data-ttu-id="27502-111">Aşağıdaki örnekte gösterilen ilk uç nokta tanımı taban adresini ve Tekdüzen Kaynak Tanımlayıcısı (URI) birleşim kurallar aşağıdaki ilgili adresi bileşimini uç nokta adresi gelir bir göreli adresi belirtir.</span><span class="sxs-lookup"><span data-stu-id="27502-111">The first endpoint definition shown in the following sample specifies a relative address, which means the endpoint address is a combination of the base address and the relative address following the rules of Uniform Resource Identifier (URI) composition.</span></span> <span data-ttu-id="27502-112">Göreli adresi boştur (""), uç nokta adresi taban adresi ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="27502-112">The relative address is empty (""), so the endpoint address is the same as the base address.</span></span> <span data-ttu-id="27502-113">Gerçek bitiş adresini 8000/servicemodelsamples/hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="27502-113">The actual endpoint address is http://localhost:8000/servicemodelsamples/service.</span></span>  
  
```xml  
<endpoint address=""   
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="27502-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="27502-114">Example</span></span>  
 <span data-ttu-id="27502-115">İkinci uç nokta tanımı, ayrıca aşağıdaki örnek yapılandırmada gösterildiği gibi bir göreli adresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="27502-115">The second endpoint definition also specifies a relative address, as shown in the following sample configuration.</span></span> <span data-ttu-id="27502-116">Göreli adresi "test", taban adresi eklenir.</span><span class="sxs-lookup"><span data-stu-id="27502-116">The relative address, "test", is appended to the base address.</span></span> <span data-ttu-id="27502-117">Gerçek bitiş noktası 8000/servicemodelsamples/service/test adresidir.</span><span class="sxs-lookup"><span data-stu-id="27502-117">The actual endpoint address is http://localhost:8000/servicemodelsamples/service/test.</span></span>  
  
```xml  
<endpoint address="/test"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="27502-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="27502-118">Example</span></span>  
 <span data-ttu-id="27502-119">Aşağıdaki örnek yapılandırmada gösterildiği gibi üçüncü uç nokta tanımı mutlak bir adres belirtir.</span><span class="sxs-lookup"><span data-stu-id="27502-119">The third endpoint definition specifies an absolute address, as shown in the following sample configuration.</span></span> <span data-ttu-id="27502-120">Temel adres adresi herhangi bir rol oynar.</span><span class="sxs-lookup"><span data-stu-id="27502-120">The base address plays no role in the address.</span></span> <span data-ttu-id="27502-121">Gerçek bitiş noktası hello/http://localhost:8001/servicemodelsamples adresidir.</span><span class="sxs-lookup"><span data-stu-id="27502-121">The actual endpoint address is http://localhost:8001/hello/servicemodelsamples.</span></span>  
  
```xml  
<endpoint address="http://localhost:8001/hello/servicemodelsamples"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="27502-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="27502-122">Example</span></span>  
 <span data-ttu-id="27502-123">Mutlak bir adres ve farklı bir aktarım dördüncü uç noktası adresi belirtir — TCP.</span><span class="sxs-lookup"><span data-stu-id="27502-123">The fourth endpoint address specifies an absolute address and a different transport—TCP.</span></span> <span data-ttu-id="27502-124">Temel adres adresi herhangi bir rol oynar.</span><span class="sxs-lookup"><span data-stu-id="27502-124">The base address plays no role in the address.</span></span> <span data-ttu-id="27502-125">Gerçek bitiş adresini net.tcp://localhost olan: servicemodelsamples/9000/hizmet.</span><span class="sxs-lookup"><span data-stu-id="27502-125">The actual endpoint address is net.tcp://localhost:9000/servicemodelsamples/service.</span></span>  
  
```xml  
<endpoint address="net.tcp://localhost:9000/servicemodelsamples/service"  
    binding="netTcpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="27502-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="27502-126">Example</span></span>  
 <span data-ttu-id="27502-127">Çalışma zamanı tarafından sağlanan varsayılan uç noktaları kullanmak için tüm hizmet uç noktaları kod veya yapılandırma dosyasını belirtmeyin.</span><span class="sxs-lookup"><span data-stu-id="27502-127">To use the default endpoints provided by the runtime, do not specify any service endpoints in either the code or the configuration file.</span></span> <span data-ttu-id="27502-128">Hizmet açıldığında, bu örnekte, varsayılan uç noktalar çalışma zamanı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="27502-128">In this example, the runtime creates the default endpoints when the service is opened.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="27502-129">Varsayılan uç noktalar, bağlamaları ve davranışları, bkz: [Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="27502-129"> default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
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
