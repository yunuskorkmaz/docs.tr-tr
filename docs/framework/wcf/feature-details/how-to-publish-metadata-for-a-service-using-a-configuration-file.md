---
title: 'Nasıl yapılır: Yapılandırma Dosyası Kullanarak Bir Hizmet için Meta Verileri Yayımlama'
ms.date: 03/30/2017
ms.assetid: f061443f-92df-4824-b36a-609c4cd14a17
ms.openlocfilehash: 7ea0a2aa386f747b89f56f21d75a97e4409140a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184878"
---
# <a name="how-to-publish-metadata-for-a-service-using-a-configuration-file"></a><span data-ttu-id="0f5d7-102">Nasıl yapılır: Yapılandırma Dosyası Kullanarak Bir Hizmet için Meta Verileri Yayımlama</span><span class="sxs-lookup"><span data-stu-id="0f5d7-102">How to: Publish Metadata for a Service Using a Configuration File</span></span>
<span data-ttu-id="0f5d7-103">Bu, bir Windows Communication Foundation (WCF) hizmeti için meta veri yayımlama gösteren iki nasıl yapılır konularından biridir.</span><span class="sxs-lookup"><span data-stu-id="0f5d7-103">This is one of two how-to topics that demonstrate publishing metadata for a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="0f5d7-104">Bir yapılandırma dosyası kullanarak ve kodu kullanarak, bir hizmetin meta verileri nasıl yayımlayacağını belirtmenin iki yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="0f5d7-104">There are two ways to specify how a service should publish metadata, using a configuration file and using code.</span></span> <span data-ttu-id="0f5d7-105">Bu konu, yapılandırma dosyasını kullanarak bir hizmet için meta verilerin nasıl yayımlandırılabildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0f5d7-105">This topic shows how to publish metadata for a service using a configuration file.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="0f5d7-106">Bu konu, meta verilerin güvenli olmayan bir şekilde nasıl yayımlandırılabildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0f5d7-106">This topic shows how to publish metadata in an unsecure manner.</span></span> <span data-ttu-id="0f5d7-107">Herhangi bir istemci hizmetten meta verileri alabilir.</span><span class="sxs-lookup"><span data-stu-id="0f5d7-107">Any client can retrieve the metadata from the service.</span></span> <span data-ttu-id="0f5d7-108">Hizmetinizin meta verileri güvenli bir şekilde yayımlamasını istiyorsanız, [bkz.](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md)</span><span class="sxs-lookup"><span data-stu-id="0f5d7-108">If you require your service to publish metadata in a secure manner, see [Custom Secure Metadata Endpoint](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span></span>  
  
 <span data-ttu-id="0f5d7-109">Meta verileri kodda yayımlama hakkında daha fazla bilgi için [bkz: Kod Kullanan Bir Hizmet için Meta Veri Yayımlama.](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)</span><span class="sxs-lookup"><span data-stu-id="0f5d7-109">For more information about publishing metadata in code, see [How to: Publish Metadata for a Service Using Code](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md).</span></span> <span data-ttu-id="0f5d7-110">Meta verileri yayımlama, istemcilerin sorgu dizesini kullanarak `?wsdl` bir WS-Transfer GET isteği veya http/GET isteği kullanarak meta verileri almasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="0f5d7-110">Publishing metadata allows clients to retrieve the metadata using a WS-Transfer GET request or an HTTP/GET request using the `?wsdl` query string.</span></span> <span data-ttu-id="0f5d7-111">Kodun çalıştığından emin olmak için temel bir WCF hizmeti oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0f5d7-111">To be sure that the code is working, create a basic WCF service.</span></span> <span data-ttu-id="0f5d7-112">Basitlik için, aşağıdaki kodda temel bir kendi kendine barındırılan hizmet sağlanır.</span><span class="sxs-lookup"><span data-stu-id="0f5d7-112">For simplicity, a basic self-hosted service is provided in the following code.</span></span>  
  
```csharp  
using System;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.ServiceModel.Description;  
  
namespace Metadata.Samples  
{  
    [ServiceContract]  
    public interface ISimpleService  
    {  
        [OperationContract]  
        string SimpleMethod(string msg);  
    }  
  
    class SimpleService : ISimpleService  
    {  
        public string SimpleMethod(string msg)  
        {  
            Console.WriteLine("The caller passed in " + msg);  
            return "Hello " + msg;  
        }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            ServiceHost host = new ServiceHost(typeof(SimpleService),  
                new Uri("http://localhost:8001/MetadataSample"));
            try  
            {  
                // Open the service host to accept incoming calls  
                host.Open();  
  
                // The service can now be accessed.  
                Console.WriteLine("The service is ready.");  
                Console.WriteLine("Press <ENTER> to terminate service.");  
                Console.WriteLine();  
                Console.ReadLine();  
  
                // Close the ServiceHostBase to shutdown the service.  
                host.Close();  
            }  
            catch (CommunicationException commProblem)  
            {  
                Console.WriteLine("There was a communication problem. " + commProblem.Message);  
                Console.Read();  
            }  
        }  
    }  
}  
```  
  
 <span data-ttu-id="0f5d7-113">Bu hizmet, yapılandırma dosyası kullanılarak yapılandırılan, kendi kendine barındırılan bir hizmettir.</span><span class="sxs-lookup"><span data-stu-id="0f5d7-113">This service is a self-hosted service, which is configured using a configuration file.</span></span> <span data-ttu-id="0f5d7-114">Aşağıdaki yapılandırma dosyası bir başlangıç noktası olarak hizmet vermektedir.</span><span class="sxs-lookup"><span data-stu-id="0f5d7-114">The following configuration file serves as a starting point.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="Metadata.Example.SimpleService">  
        <endpoint address=""  
                  binding="basicHttpBinding"  
                  contract="Metadata.Example.ISimpleService" />  
      </service>  
    </services>  
    <behaviors>  
  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="to-publish-metadata-for-a-wcf-service-using-an-application-configuration-file"></a><span data-ttu-id="0f5d7-115">Bir uygulama yapılandırma dosyasını kullanarak bir WCF hizmeti için meta veri yayımlamak için</span><span class="sxs-lookup"><span data-stu-id="0f5d7-115">To publish metadata for a WCF service using an application configuration file</span></span>  
  
1. <span data-ttu-id="0f5d7-116">App.config dosyası içinde, kapanış `</services>` öğesisonra, `<behaviors>` bir öğe oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0f5d7-116">Within the App.config file, after the closing `</services>` element, create a `<behaviors>` element.</span></span>  

2. <span data-ttu-id="0f5d7-117">Öğe `<behaviors>` içinde, bir `<serviceBehaviors>` öğe ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0f5d7-117">Within the `<behaviors>` element, add a `<serviceBehaviors>` element.</span></span>  

3. <span data-ttu-id="0f5d7-118">Öğeye `<behavior>` bir öğe ekleyin ve `name` öğenin özniteliği için bir değer belirtin. `<behavior>` `<serviceBehaviors>`</span><span class="sxs-lookup"><span data-stu-id="0f5d7-118">Add a `<behavior>` element to the `<serviceBehaviors>` element and specify a value for the `name` attribute of the `<behavior>` element.</span></span>  

4. <span data-ttu-id="0f5d7-119">`<behavior>` Öğeye bir `<serviceMetadata>` öğe ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0f5d7-119">Add a `<serviceMetadata>` element to the `<behavior>` element.</span></span> <span data-ttu-id="0f5d7-120">Özniteliği ve `policyVersion` `true` Özniteliği İlke15'e ayarlayın. `httpGetEnabled`</span><span class="sxs-lookup"><span data-stu-id="0f5d7-120">Set the `httpGetEnabled` attribute to `true` and the `policyVersion` attribute to Policy15.</span></span> <span data-ttu-id="0f5d7-121">`httpGetEnabled`hizmetin bir HTTP GET isteği tarafından yapılan meta veri isteklerine yanıt vermesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="0f5d7-121">`httpGetEnabled` allows the service to respond to metadata requests made by an HTTP GET request.</span></span> <span data-ttu-id="0f5d7-122">`policyVersion`meta veri oluştururken hizmete WS-İlke 1.5'e uymasını söyler.</span><span class="sxs-lookup"><span data-stu-id="0f5d7-122">`policyVersion` tells the service to conform to WS-Policy 1.5 when generating metadata.</span></span>  

5. <span data-ttu-id="0f5d7-123">Öğeye `behaviorConfiguration` bir öznitelik ekleyin ve aşağıdaki `<behavior>` kod örneğinde gösterildiği gibi, adım 1'de eklenen öğenin özniteliğini belirtin. `name` `<service>`</span><span class="sxs-lookup"><span data-stu-id="0f5d7-123">Add a `behaviorConfiguration` attribute to the `<service>` element and specify the `name` attribute of the `<behavior>` element added in step 1, as shown in the following code example.</span></span>  
  
    ```xml  
    <services>  
      <service  
          name="Metadata.Example.SimpleService"  
          behaviorConfiguration="SimpleServiceBehavior">  
        ...  
      </service>  
    </services>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="SimpleServiceBehavior">  
          <serviceMetadata httpGetEnabled="True" policyVersion="Policy15" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
6. <span data-ttu-id="0f5d7-124">Aşağıdaki kod `<endpoint>` örneğinde gösterildiği `IMetadataExchange`gibi, sözleşme ayarlanmış bir veya daha fazla öğe ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0f5d7-124">Add one or more `<endpoint>` elements with the contract set to `IMetadataExchange`, as shown in the following code example.</span></span>  
  
    ```xml  
    <services>  
      <service  
          name="Metadata.Example.SimpleService"  
          behaviorConfiguration="SimpleServiceBehavior">  
  
        <endpoint address=""  
                  binding="wsHttpBinding"  
                  contract="Metadata.Example.ISimpleService" />  
  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  
    ```  
  
7. <span data-ttu-id="0f5d7-125">Önceki adımda eklenen meta veri uç noktaları `binding` için özniteliği aşağıdakilerden birine ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="0f5d7-125">For the metadata endpoints added in the previous step, set the `binding` attribute to one of the following:</span></span>  
  
    - <span data-ttu-id="0f5d7-126">`mexHttpBinding`HTTP yayını için.</span><span class="sxs-lookup"><span data-stu-id="0f5d7-126">`mexHttpBinding` for HTTP publication.</span></span>  
  
    - <span data-ttu-id="0f5d7-127">`mexHttpsBinding`HTTPS yayını için.</span><span class="sxs-lookup"><span data-stu-id="0f5d7-127">`mexHttpsBinding` for HTTPS publication.</span></span>  
  
    - <span data-ttu-id="0f5d7-128">`mexNamedPipeBinding`adlı boru yayını için.</span><span class="sxs-lookup"><span data-stu-id="0f5d7-128">`mexNamedPipeBinding` for named pipe publication.</span></span>  
  
    - <span data-ttu-id="0f5d7-129">`mexTcpBinding`TCP yayını için.</span><span class="sxs-lookup"><span data-stu-id="0f5d7-129">`mexTcpBinding` for TCP publication.</span></span>  
  
8. <span data-ttu-id="0f5d7-130">Önceki adımda eklenen meta veri uç noktaları için adresi aşağıdakilere eşit olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="0f5d7-130">For the metadata endpoints added in a previous step, set the address equal to:</span></span>  
  
    - <span data-ttu-id="0f5d7-131">Temel adres meta veri bağlama ile aynıysa, ana bilgisayar uygulamasının temel adresini yayın noktası olarak kullanmak için boş bir dize.</span><span class="sxs-lookup"><span data-stu-id="0f5d7-131">An empty string to use the host application's base address as the publication point if the base address is the same as the metadata binding.</span></span>  
  
    - <span data-ttu-id="0f5d7-132">Ana bilgisayar uygulamasının temel adresi varsa göreli bir adres.</span><span class="sxs-lookup"><span data-stu-id="0f5d7-132">A relative address if the host application has a base address.</span></span>  
  
    - <span data-ttu-id="0f5d7-133">Mutlak bir adres.</span><span class="sxs-lookup"><span data-stu-id="0f5d7-133">An absolute address.</span></span>  
  
9. <span data-ttu-id="0f5d7-134">Konsol uygulamasını derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0f5d7-134">Build and run the console application.</span></span>  
  
10. <span data-ttu-id="0f5d7-135">Hizmetin temel adresine (buhttp://localhost:8001/MetadataSample örnekte) göz atmak ve meta veri yayımlamanın açık olduğunu doğrulamak için Internet Explorer'ı kullanın.</span><span class="sxs-lookup"><span data-stu-id="0f5d7-135">Use Internet Explorer to browse to the base address of the service (http://localhost:8001/MetadataSample in this sample) and verify that the metadata publishing is turned on.</span></span> <span data-ttu-id="0f5d7-136">Değilse, ortaya çıkan sayfanın üst kısmındaki bir ileti görüntülenir: "Bu hizmet için meta veri yayımlama şu anda devre dışı bırakılır."</span><span class="sxs-lookup"><span data-stu-id="0f5d7-136">If not, a message at the top of the resulting page displays: "Metadata publishing for this service is currently disabled."</span></span>  
  
### <a name="to-use-default-endpoints"></a><span data-ttu-id="0f5d7-137">Varsayılan uç noktaları kullanmak için</span><span class="sxs-lookup"><span data-stu-id="0f5d7-137">To use default endpoints</span></span>  
  
1. <span data-ttu-id="0f5d7-138">Varsayılan uç noktaları kullanan bir hizmetteki meta verileri <xref:System.ServiceModel.Description.ServiceMetadataBehavior> yapılandırmak için yapılandırma dosyasındakileri önceki örnekte olduğu gibi belirtin, ancak herhangi bir uç nokta belirtmeyin.</span><span class="sxs-lookup"><span data-stu-id="0f5d7-138">To configure metadata on a service that uses default endpoints, specify the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> in the configuration file as in the previous example, but do not specify any endpoints.</span></span> <span data-ttu-id="0f5d7-139">Yapılandırma dosyası daha sonra bu gibi görünür.</span><span class="sxs-lookup"><span data-stu-id="0f5d7-139">The configuration file would then look like this.</span></span>  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <behaviors>  
          <serviceBehaviors>  
            <behavior name="SimpleServiceBehavior">  
              <serviceMetadata httpGetEnabled="True" policyVersion="Policy12" />  
            </behavior>  
          </serviceBehaviors>  
        </behaviors>  
  
      </system.serviceModel>  
    </configuration>  
    ```  
  
     <span data-ttu-id="0f5d7-140">Hizmet <xref:System.ServiceModel.Description.ServiceMetadataBehavior> `httpGetEnabled` kümesi ile bir `true`olduğundan, hizmet meta veri yayımlama etkin ve hiçbir uç noktaları açıkça eklenmiştir çünkü, çalışma süresi varsayılan uç noktaları ekler.</span><span class="sxs-lookup"><span data-stu-id="0f5d7-140">Because the service has a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> with the `httpGetEnabled` set to `true`, the service has publishing metadata enabled, and because no endpoints were explicitly added, the runtime adds the default endpoints.</span></span> <span data-ttu-id="0f5d7-141">Varsayılan uç noktalar, bağlamalar ve davranışlar hakkında daha fazla bilgi için wcf hizmetleri için [Basitleştirilmiş Yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md) ve [Basitleştirilmiş Yapılandırma'ya](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="0f5d7-141">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f5d7-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="0f5d7-142">Example</span></span>  
 <span data-ttu-id="0f5d7-143">Aşağıdaki kod örneği, temel bir WCF hizmetinin uygulanmasını ve hizmet için meta verileri yayımlayan yapılandırma dosyasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0f5d7-143">The following code example shows the implementation of a basic WCF service and the configuration file that publishes metadata for the service.</span></span>  
  
```csharp  
using System;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.ServiceModel.Description;  
  
namespace Metadata.Samples  
{  
    [ServiceContract]  
    public interface ISimpleService  
    {  
        [OperationContract]  
        string SimpleMethod(string msg);  
    }  
  
    class SimpleService : ISimpleService  
    {  
        public string SimpleMethod(string msg)  
        {  
            Console.WriteLine("The caller passed in " + msg);  
            return "Hello " + msg;  
        }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            ServiceHost host = new ServiceHost(typeof(SimpleService),  
                new Uri("http://localhost:8001/MetadataSample"));
            try  
            {  
                // Open the service host to accept incoming calls  
                host.Open();  
  
                // The service can now be accessed.  
                Console.WriteLine("The service is ready.");  
                Console.WriteLine("Press <ENTER> to terminate service.");  
                Console.WriteLine();  
                Console.ReadLine();  
  
                // Close the ServiceHostBase to shutdown the service.  
                host.Close();  
            }  
            catch (CommunicationException commProblem)  
            {  
                Console.WriteLine("There was a communication problem. " + commProblem.Message);  
                Console.Read();  
            }  
        }  
    }  
}  
```  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="SimpleServiceBehavior">  
          <serviceMetadata httpGetEnabled="True" policyVersion="Policy12" />  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0f5d7-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f5d7-144">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
- [<span data-ttu-id="0f5d7-145">Nasıl yapılır: Yönetilen Bir Uygulamada Bir WCF Hizmeti Barındırma</span><span class="sxs-lookup"><span data-stu-id="0f5d7-145">How to: Host a WCF Service in a Managed Application</span></span>](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)
- [<span data-ttu-id="0f5d7-146">Kendini Barındırma</span><span class="sxs-lookup"><span data-stu-id="0f5d7-146">Self-Host</span></span>](../../../../docs/framework/wcf/samples/self-host.md)
- [<span data-ttu-id="0f5d7-147">Meta Veri Mimarisi Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0f5d7-147">Metadata Architecture Overview</span></span>](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)
- [<span data-ttu-id="0f5d7-148">Meta Verileri Kullanma</span><span class="sxs-lookup"><span data-stu-id="0f5d7-148">Using Metadata</span></span>](../../../../docs/framework/wcf/feature-details/using-metadata.md)
- [<span data-ttu-id="0f5d7-149">Nasıl yapılır: Kod Kullanarak Bir Hizmet için Meta Verileri Yayımlama</span><span class="sxs-lookup"><span data-stu-id="0f5d7-149">How to: Publish Metadata for a Service Using Code</span></span>](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)
