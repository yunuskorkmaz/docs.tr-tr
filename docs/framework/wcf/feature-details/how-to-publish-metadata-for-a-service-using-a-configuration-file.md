---
title: 'Nasıl yapılır: Yapılandırma Dosyası Kullanarak Bir Hizmet için Meta Verileri Yayımlama'
ms.date: 03/30/2017
ms.assetid: f061443f-92df-4824-b36a-609c4cd14a17
ms.openlocfilehash: 976e1e0bb2c6479f7599165a1c6fe83bae4e17c1
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596987"
---
# <a name="how-to-publish-metadata-for-a-service-using-a-configuration-file"></a><span data-ttu-id="dc811-102">Nasıl yapılır: Yapılandırma Dosyası Kullanarak Bir Hizmet için Meta Verileri Yayımlama</span><span class="sxs-lookup"><span data-stu-id="dc811-102">How to: Publish Metadata for a Service Using a Configuration File</span></span>
<span data-ttu-id="dc811-103">Bu, bir Windows Communication Foundation (WCF) hizmeti için meta verileri yayımlamayı gösteren iki nasıl yapılır konuktan biridir.</span><span class="sxs-lookup"><span data-stu-id="dc811-103">This is one of two how-to topics that demonstrate publishing metadata for a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="dc811-104">Bir hizmetin bir yapılandırma dosyası kullanarak ve kod kullanarak meta verileri nasıl yayımlayacağınızı belirten iki yol vardır.</span><span class="sxs-lookup"><span data-stu-id="dc811-104">There are two ways to specify how a service should publish metadata, using a configuration file and using code.</span></span> <span data-ttu-id="dc811-105">Bu konuda bir yapılandırma dosyası kullanarak bir hizmet için meta verilerin nasıl yayımlanacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="dc811-105">This topic shows how to publish metadata for a service using a configuration file.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="dc811-106">Bu konuda, meta verilerin güvensiz bir şekilde nasıl yayımlanacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="dc811-106">This topic shows how to publish metadata in an unsecure manner.</span></span> <span data-ttu-id="dc811-107">Tüm istemciler, hizmetten meta verileri alabilir.</span><span class="sxs-lookup"><span data-stu-id="dc811-107">Any client can retrieve the metadata from the service.</span></span> <span data-ttu-id="dc811-108">Hizmetinizin meta verileri güvenli bir şekilde yayımlamasını istiyorsanız bkz. [özel güvenli meta veri uç noktası](../samples/custom-secure-metadata-endpoint.md).</span><span class="sxs-lookup"><span data-stu-id="dc811-108">If you require your service to publish metadata in a secure manner, see [Custom Secure Metadata Endpoint](../samples/custom-secure-metadata-endpoint.md).</span></span>  
  
 <span data-ttu-id="dc811-109">Kodda meta verileri yayımlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: kod kullanarak bir hizmet Için meta verileri yayımlama](how-to-publish-metadata-for-a-service-using-code.md).</span><span class="sxs-lookup"><span data-stu-id="dc811-109">For more information about publishing metadata in code, see [How to: Publish Metadata for a Service Using Code](how-to-publish-metadata-for-a-service-using-code.md).</span></span> <span data-ttu-id="dc811-110">Meta veri yayımlama, istemcilerin bir WS-transfer GET isteği veya sorgu dizesini kullanarak bir HTTP/GET isteği kullanarak meta verileri almasına izin verir `?wsdl` .</span><span class="sxs-lookup"><span data-stu-id="dc811-110">Publishing metadata allows clients to retrieve the metadata using a WS-Transfer GET request or an HTTP/GET request using the `?wsdl` query string.</span></span> <span data-ttu-id="dc811-111">Kodun çalıştığından emin olmak için temel bir WCF hizmeti oluşturun.</span><span class="sxs-lookup"><span data-stu-id="dc811-111">To be sure that the code is working, create a basic WCF service.</span></span> <span data-ttu-id="dc811-112">Basitlik sağlamak için, aşağıdaki kodda temel bir şirket içinde barındırılan bir hizmet sağlanır.</span><span class="sxs-lookup"><span data-stu-id="dc811-112">For simplicity, a basic self-hosted service is provided in the following code.</span></span>  
  
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
  
 <span data-ttu-id="dc811-113">Bu hizmet, bir yapılandırma dosyası kullanılarak yapılandırılan, kendi kendine barındırılan bir hizmettir.</span><span class="sxs-lookup"><span data-stu-id="dc811-113">This service is a self-hosted service, which is configured using a configuration file.</span></span> <span data-ttu-id="dc811-114">Aşağıdaki yapılandırma dosyası bir başlangıç noktası olarak görev yapar.</span><span class="sxs-lookup"><span data-stu-id="dc811-114">The following configuration file serves as a starting point.</span></span>  
  
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
  
### <a name="to-publish-metadata-for-a-wcf-service-using-an-application-configuration-file"></a><span data-ttu-id="dc811-115">Bir WCF hizmeti için meta verileri bir uygulama yapılandırma dosyası kullanarak yayımlamak için</span><span class="sxs-lookup"><span data-stu-id="dc811-115">To publish metadata for a WCF service using an application configuration file</span></span>  
  
1. <span data-ttu-id="dc811-116">App. config dosyası içinde, kapanış `</services>` öğesinden sonra bir `<behaviors>` öğesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="dc811-116">Within the App.config file, after the closing `</services>` element, create a `<behaviors>` element.</span></span>  

2. <span data-ttu-id="dc811-117">Öğesi içinde `<behaviors>` , bir öğesi ekleyin `<serviceBehaviors>` .</span><span class="sxs-lookup"><span data-stu-id="dc811-117">Within the `<behaviors>` element, add a `<serviceBehaviors>` element.</span></span>  

3. <span data-ttu-id="dc811-118">Öğesine bir `<behavior>` öğesi ekleyin `<serviceBehaviors>` ve öğesi özniteliği için bir değer belirtin `name` `<behavior>` .</span><span class="sxs-lookup"><span data-stu-id="dc811-118">Add a `<behavior>` element to the `<serviceBehaviors>` element and specify a value for the `name` attribute of the `<behavior>` element.</span></span>  

4. <span data-ttu-id="dc811-119">Öğeye bir `<serviceMetadata>` öğe ekleyin `<behavior>` .</span><span class="sxs-lookup"><span data-stu-id="dc811-119">Add a `<serviceMetadata>` element to the `<behavior>` element.</span></span> <span data-ttu-id="dc811-120">`httpGetEnabled`Özniteliğini `true` ve `policyVersion` özniteliğini Policy15 olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="dc811-120">Set the `httpGetEnabled` attribute to `true` and the `policyVersion` attribute to Policy15.</span></span> <span data-ttu-id="dc811-121">`httpGetEnabled`hizmetin bir HTTP GET isteği tarafından yapılan meta veri isteklerine yanıt vermesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="dc811-121">`httpGetEnabled` allows the service to respond to metadata requests made by an HTTP GET request.</span></span> <span data-ttu-id="dc811-122">`policyVersion`meta verileri oluştururken Service 'in WS-Policy 1,5 ile uyumlu olduğunu söyler.</span><span class="sxs-lookup"><span data-stu-id="dc811-122">`policyVersion` tells the service to conform to WS-Policy 1.5 when generating metadata.</span></span>  

5. <span data-ttu-id="dc811-123">Öğesine bir `behaviorConfiguration` öznitelik ekleyin `<service>` ve `name` `<behavior>` Aşağıdaki kod örneğinde gösterildiği gibi, 1. adımda eklenen öğenin özniteliğini belirtin.</span><span class="sxs-lookup"><span data-stu-id="dc811-123">Add a `behaviorConfiguration` attribute to the `<service>` element and specify the `name` attribute of the `<behavior>` element added in step 1, as shown in the following code example.</span></span>  
  
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
  
6. <span data-ttu-id="dc811-124">`<endpoint>` `IMetadataExchange` Aşağıdaki kod örneğinde gösterildiği gibi, sözleşmeye ayarlanmış bir veya daha fazla öğe ekleyin.</span><span class="sxs-lookup"><span data-stu-id="dc811-124">Add one or more `<endpoint>` elements with the contract set to `IMetadataExchange`, as shown in the following code example.</span></span>  
  
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
  
7. <span data-ttu-id="dc811-125">Önceki adımda eklenen meta veri uç noktaları için, `binding` özniteliğini aşağıdakilerden birine ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="dc811-125">For the metadata endpoints added in the previous step, set the `binding` attribute to one of the following:</span></span>  
  
    - <span data-ttu-id="dc811-126">`mexHttpBinding`HTTP yayını için.</span><span class="sxs-lookup"><span data-stu-id="dc811-126">`mexHttpBinding` for HTTP publication.</span></span>  
  
    - <span data-ttu-id="dc811-127">`mexHttpsBinding`HTTPS yayını için.</span><span class="sxs-lookup"><span data-stu-id="dc811-127">`mexHttpsBinding` for HTTPS publication.</span></span>  
  
    - <span data-ttu-id="dc811-128">`mexNamedPipeBinding`Adlandırılmış Kanal yayını için.</span><span class="sxs-lookup"><span data-stu-id="dc811-128">`mexNamedPipeBinding` for named pipe publication.</span></span>  
  
    - <span data-ttu-id="dc811-129">`mexTcpBinding`TCP yayını için.</span><span class="sxs-lookup"><span data-stu-id="dc811-129">`mexTcpBinding` for TCP publication.</span></span>  
  
8. <span data-ttu-id="dc811-130">Önceki bir adımda eklenen meta veri uç noktaları için, adresi şuna eşit olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="dc811-130">For the metadata endpoints added in a previous step, set the address equal to:</span></span>  
  
    - <span data-ttu-id="dc811-131">Temel adres meta veri bağlamasıyla aynıysa, yayın noktası olarak ana bilgisayar uygulamasının temel adresini kullanmak için boş bir dize.</span><span class="sxs-lookup"><span data-stu-id="dc811-131">An empty string to use the host application's base address as the publication point if the base address is the same as the metadata binding.</span></span>  
  
    - <span data-ttu-id="dc811-132">Ana bilgisayar uygulamasının bir temel adresi varsa göreli bir adres.</span><span class="sxs-lookup"><span data-stu-id="dc811-132">A relative address if the host application has a base address.</span></span>  
  
    - <span data-ttu-id="dc811-133">Mutlak bir adres.</span><span class="sxs-lookup"><span data-stu-id="dc811-133">An absolute address.</span></span>  
  
9. <span data-ttu-id="dc811-134">Konsol uygulamasını derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="dc811-134">Build and run the console application.</span></span>  
  
10. <span data-ttu-id="dc811-135">Internet Explorer 'ı kullanarak hizmetin temel adresine gidin ( `http://localhost:8001/MetadataSample` Bu örnekte) ve meta veri yayımlamanın açık olduğunu doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="dc811-135">Use Internet Explorer to browse to the base address of the service (`http://localhost:8001/MetadataSample` in this sample) and verify that the metadata publishing is turned on.</span></span> <span data-ttu-id="dc811-136">Aksi takdirde, sonuçta ortaya çıkan sayfanın en üstündeki bir ileti şunu görüntüler: "Bu hizmet için meta veri yayımlama Şu anda devre dışı."</span><span class="sxs-lookup"><span data-stu-id="dc811-136">If not, a message at the top of the resulting page displays: "Metadata publishing for this service is currently disabled."</span></span>  
  
### <a name="to-use-default-endpoints"></a><span data-ttu-id="dc811-137">Varsayılan uç noktaları kullanmak için</span><span class="sxs-lookup"><span data-stu-id="dc811-137">To use default endpoints</span></span>  
  
1. <span data-ttu-id="dc811-138">Varsayılan uç noktaları kullanan bir hizmette meta verileri yapılandırmak için, <xref:System.ServiceModel.Description.ServiceMetadataBehavior> yapılandırma dosyasında önceki örnekte olduğu gibi ' i belirtin, ancak herhangi bir uç nokta belirtmeyin.</span><span class="sxs-lookup"><span data-stu-id="dc811-138">To configure metadata on a service that uses default endpoints, specify the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> in the configuration file as in the previous example, but do not specify any endpoints.</span></span> <span data-ttu-id="dc811-139">Yapılandırma dosyası bu şekilde görünür.</span><span class="sxs-lookup"><span data-stu-id="dc811-139">The configuration file would then look like this.</span></span>  
  
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
  
     <span data-ttu-id="dc811-140">Hizmeti, <xref:System.ServiceModel.Description.ServiceMetadataBehavior> `httpGetEnabled` olarak ayarlanmış bir öğesine sahip olduğundan `true` , hizmette yayımlama meta verileri etkindir ve hiçbir uç nokta açık olarak eklenmediğinden, çalışma zamanı varsayılan uç noktaları ekler.</span><span class="sxs-lookup"><span data-stu-id="dc811-140">Because the service has a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> with the `httpGetEnabled` set to `true`, the service has publishing metadata enabled, and because no endpoints were explicitly added, the runtime adds the default endpoints.</span></span> <span data-ttu-id="dc811-141">Varsayılan uç noktalar, bağlamalar ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="dc811-141">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../simplified-configuration.md) and [Simplified Configuration for WCF Services](../samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="dc811-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="dc811-142">Example</span></span>  
 <span data-ttu-id="dc811-143">Aşağıdaki kod örneği, temel bir WCF hizmetinin ve hizmet için meta verileri yayımlayan yapılandırma dosyasının uygulamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="dc811-143">The following code example shows the implementation of a basic WCF service and the configuration file that publishes metadata for the service.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dc811-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dc811-144">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
- [<span data-ttu-id="dc811-145">Nasıl yapılır: Yönetilen Bir Uygulamada Bir WCF Hizmeti Barındırma</span><span class="sxs-lookup"><span data-stu-id="dc811-145">How to: Host a WCF Service in a Managed Application</span></span>](../how-to-host-a-wcf-service-in-a-managed-application.md)
- [<span data-ttu-id="dc811-146">Kendini Barındırma</span><span class="sxs-lookup"><span data-stu-id="dc811-146">Self-Host</span></span>](../samples/self-host.md)
- [<span data-ttu-id="dc811-147">Meta Veri Mimarisi Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="dc811-147">Metadata Architecture Overview</span></span>](metadata-architecture-overview.md)
- [<span data-ttu-id="dc811-148">Meta Verileri Kullanma</span><span class="sxs-lookup"><span data-stu-id="dc811-148">Using Metadata</span></span>](using-metadata.md)
- [<span data-ttu-id="dc811-149">Nasıl yapılır: Kod Kullanarak Bir Hizmet için Meta Verileri Yayımlama</span><span class="sxs-lookup"><span data-stu-id="dc811-149">How to: Publish Metadata for a Service Using Code</span></span>](how-to-publish-metadata-for-a-service-using-code.md)
