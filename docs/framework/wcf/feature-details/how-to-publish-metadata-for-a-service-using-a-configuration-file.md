---
title: 'Nasıl yapılır: Yapılandırma Dosyası Kullanarak Bir Hizmet için Meta Verileri Yayımlama'
ms.date: 03/30/2017
ms.assetid: f061443f-92df-4824-b36a-609c4cd14a17
ms.openlocfilehash: 367ebeee5c12d809a758f1bee73dfaadda85788d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61761461"
---
# <a name="how-to-publish-metadata-for-a-service-using-a-configuration-file"></a><span data-ttu-id="e15f3-102">Nasıl yapılır: Yapılandırma Dosyası Kullanarak Bir Hizmet için Meta Verileri Yayımlama</span><span class="sxs-lookup"><span data-stu-id="e15f3-102">How to: Publish Metadata for a Service Using a Configuration File</span></span>
<span data-ttu-id="e15f3-103">Bu, bir Windows Communication Foundation (WCF) hizmet için meta verileri yayımlama gösteren iki nasıl yapılır konuları biridir.</span><span class="sxs-lookup"><span data-stu-id="e15f3-103">This is one of two how-to topics that demonstrate publishing metadata for a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="e15f3-104">Hizmet yapılandırma dosyasını ve kod kullanarak meta verileri nasıl yayımlamalısınız belirtmenin iki yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="e15f3-104">There are two ways to specify how a service should publish metadata, using a configuration file and using code.</span></span> <span data-ttu-id="e15f3-105">Bu konuda, bir yapılandırma dosyası kullanarak bir hizmet için meta verileri yayımlama gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e15f3-105">This topic shows how to publish metadata for a service using a configuration file.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="e15f3-106">Bu konu, güvenli bir şekilde meta verileri yayımlama gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e15f3-106">This topic shows how to publish metadata in an unsecure manner.</span></span> <span data-ttu-id="e15f3-107">Herhangi bir istemci hizmet meta verileri alabilir.</span><span class="sxs-lookup"><span data-stu-id="e15f3-107">Any client can retrieve the metadata from the service.</span></span> <span data-ttu-id="e15f3-108">Meta verileri güvenli bir şekilde yayımlamak için hizmetinize ihtiyaç duyuyorsanız bkz [özel güvenli meta veri uç noktası](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span><span class="sxs-lookup"><span data-stu-id="e15f3-108">If you require your service to publish metadata in a secure manner, see [Custom Secure Metadata Endpoint](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span></span>  
  
 <span data-ttu-id="e15f3-109">Kod meta verileri yayımlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: Kod kullanarak bir hizmet için meta verileri yayımlama](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md).</span><span class="sxs-lookup"><span data-stu-id="e15f3-109">For more information about publishing metadata in code, see [How to: Publish Metadata for a Service Using Code](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md).</span></span> <span data-ttu-id="e15f3-110">Meta veri yayımlama sağlayan bir WS aktarım GET isteği ya da bir HTTP/GET isteği kullanılarak kullanarak meta verileri almak istemcileri `?wsdl` sorgu dizesi.</span><span class="sxs-lookup"><span data-stu-id="e15f3-110">Publishing metadata allows clients to retrieve the metadata using a WS-Transfer GET request or an HTTP/GET request using the `?wsdl` query string.</span></span> <span data-ttu-id="e15f3-111">Kod çalıştığından emin olmak için temel bir WCF hizmeti oluşturma.</span><span class="sxs-lookup"><span data-stu-id="e15f3-111">To be sure that the code is working, create a basic WCF service.</span></span> <span data-ttu-id="e15f3-112">Kolaylık olması için aşağıdaki kodda temel şirket içinde barındırılan bir hizmet sağlanır.</span><span class="sxs-lookup"><span data-stu-id="e15f3-112">For simplicity, a basic self-hosted service is provided in the following code.</span></span>  
  
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
  
 <span data-ttu-id="e15f3-113">Bu hizmet bir yapılandırma dosyası kullanılarak yapılandırılan şirket içinde barındırılan bir hizmettir.</span><span class="sxs-lookup"><span data-stu-id="e15f3-113">This service is a self-hosted service, which is configured using a configuration file.</span></span> <span data-ttu-id="e15f3-114">Aşağıdaki yapılandırma dosyası, başlangıç noktası olarak görev yapar.</span><span class="sxs-lookup"><span data-stu-id="e15f3-114">The following configuration file serves as a starting point.</span></span>  
  
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
  
### <a name="to-publish-metadata-for-a-wcf-service-using-an-application-configuration-file"></a><span data-ttu-id="e15f3-115">Uygulama yapılandırma dosyası kullanarak bir WCF hizmeti için meta verileri yayımlama</span><span class="sxs-lookup"><span data-stu-id="e15f3-115">To publish metadata for a WCF service using an application configuration file</span></span>  
  
1. <span data-ttu-id="e15f3-116">App.config dosyasında Kapanıştan sonra `</services>` öğesi oluşturmak bir `<behaviors>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="e15f3-116">Within the App.config file, after the closing `</services>` element, create a `<behaviors>` element.</span></span>  

2. <span data-ttu-id="e15f3-117">İçinde `<behaviors>` öğe, Ekle bir `<serviceBehaviors>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="e15f3-117">Within the `<behaviors>` element, add a `<serviceBehaviors>` element.</span></span>  

3. <span data-ttu-id="e15f3-118">Ekleme bir `<behavior>` öğesine `<serviceBehaviors>` öğesi için bir değer belirtin `name` özniteliği `<behavior>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="e15f3-118">Add a `<behavior>` element to the `<serviceBehaviors>` element and specify a value for the `name` attribute of the `<behavior>` element.</span></span>  

4. <span data-ttu-id="e15f3-119">Ekleme bir `<serviceMetadata>` öğesine `<behavior>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="e15f3-119">Add a `<serviceMetadata>` element to the `<behavior>` element.</span></span> <span data-ttu-id="e15f3-120">Ayarlama `httpGetEnabled` özniteliğini `true` ve `policyVersion` Policy15 için özniteliği.</span><span class="sxs-lookup"><span data-stu-id="e15f3-120">Set the `httpGetEnabled` attribute to `true` and the `policyVersion` attribute to Policy15.</span></span> <span data-ttu-id="e15f3-121">`httpGetEnabled` bir HTTP GET isteği tarafından yapılan meta veri isteklerine hizmet verir.</span><span class="sxs-lookup"><span data-stu-id="e15f3-121">`httpGetEnabled` allows the service to respond to metadata requests made by an HTTP GET request.</span></span> <span data-ttu-id="e15f3-122">`policyVersion` Hizmet meta verilerini oluştururken için WS-Policy 1.5 uyacak şekilde söyler.</span><span class="sxs-lookup"><span data-stu-id="e15f3-122">`policyVersion` tells the service to conform to WS-Policy 1.5 when generating metadata.</span></span>  

5. <span data-ttu-id="e15f3-123">Ekleme bir `behaviorConfiguration` özniteliğini `<service>` öğe belirtin `name` özniteliği `<behavior>` adım 1'de aşağıdaki kod örneğinde gösterildiği gibi eklenen öğe.</span><span class="sxs-lookup"><span data-stu-id="e15f3-123">Add a `behaviorConfiguration` attribute to the `<service>` element and specify the `name` attribute of the `<behavior>` element added in step 1, as shown in the following code example.</span></span>  
  
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
  
6. <span data-ttu-id="e15f3-124">Bir veya daha fazla Ekle `<endpoint>` sözleşmesi öğeleri kümesine `IMetadataExchange`aşağıdaki kod örneğinde gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="e15f3-124">Add one or more `<endpoint>` elements with the contract set to `IMetadataExchange`, as shown in the following code example.</span></span>  
  
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
  
7. <span data-ttu-id="e15f3-125">Önceki adımda eklediğiniz meta veri uç noktaları için `binding` öznitelik aşağıdakilerden biri:</span><span class="sxs-lookup"><span data-stu-id="e15f3-125">For the metadata endpoints added in the previous step, set the `binding` attribute to one of the following:</span></span>  
  
    - <span data-ttu-id="e15f3-126">`mexHttpBinding` için HTTP yayımlama.</span><span class="sxs-lookup"><span data-stu-id="e15f3-126">`mexHttpBinding` for HTTP publication.</span></span>  
  
    - <span data-ttu-id="e15f3-127">`mexHttpsBinding` HTTPS için yayımlama.</span><span class="sxs-lookup"><span data-stu-id="e15f3-127">`mexHttpsBinding` for HTTPS publication.</span></span>  
  
    - <span data-ttu-id="e15f3-128">`mexNamedPipeBinding` adlandırılmış kanal yayını.</span><span class="sxs-lookup"><span data-stu-id="e15f3-128">`mexNamedPipeBinding` for named pipe publication.</span></span>  
  
    - <span data-ttu-id="e15f3-129">`mexTcpBinding` için TCP yayımlama.</span><span class="sxs-lookup"><span data-stu-id="e15f3-129">`mexTcpBinding` for TCP publication.</span></span>  
  
8. <span data-ttu-id="e15f3-130">Bir önceki adımda eklediğiniz meta veri uç noktaları, adresi eşit olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="e15f3-130">For the metadata endpoints added in a previous step, set the address equal to:</span></span>  
  
    - <span data-ttu-id="e15f3-131">Taban adresi meta veri bağlama ile aynı olduğunda konak uygulamanın temel adres yayın noktası olarak kullanmak için boş bir dize.</span><span class="sxs-lookup"><span data-stu-id="e15f3-131">An empty string to use the host application's base address as the publication point if the base address is the same as the metadata binding.</span></span>  
  
    - <span data-ttu-id="e15f3-132">Konak uygulamanın temel adres varsa göreli bir adres.</span><span class="sxs-lookup"><span data-stu-id="e15f3-132">A relative address if the host application has a base address.</span></span>  
  
    - <span data-ttu-id="e15f3-133">Mutlak bir adres.</span><span class="sxs-lookup"><span data-stu-id="e15f3-133">An absolute address.</span></span>  
  
9. <span data-ttu-id="e15f3-134">Konsol uygulamasını derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e15f3-134">Build and run the console application.</span></span>  
  
10. <span data-ttu-id="e15f3-135">Hizmetin taban adresine göz atmak için Internet Explorer'ı kullanın (http://localhost:8001/MetadataSample Bu örnekte) ve meta veri yayımlama açık olduğunu doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="e15f3-135">Use Internet Explorer to browse to the base address of the service (http://localhost:8001/MetadataSample in this sample) and verify that the metadata publishing is turned on.</span></span> <span data-ttu-id="e15f3-136">Aksi durumda, sonuçta elde edilen sayfanın üst kısmındaki bir ileti görüntüler: "Bu hizmet için meta veri yayımlama şu anda devre dışı bırakıldı."</span><span class="sxs-lookup"><span data-stu-id="e15f3-136">If not, a message at the top of the resulting page displays: "Metadata publishing for this service is currently disabled."</span></span>  
  
### <a name="to-use-default-endpoints"></a><span data-ttu-id="e15f3-137">Varsayılan uç noktalarını kullanacak şekilde</span><span class="sxs-lookup"><span data-stu-id="e15f3-137">To use default endpoints</span></span>  
  
1. <span data-ttu-id="e15f3-138">Varsayılan uç noktalarını kullanan bir hizmet üzerinde meta verileri yapılandırmak için belirtmeniz <xref:System.ServiceModel.Description.ServiceMetadataBehavior> yapılandırma dosyasını önceki örnekte olduğu gibi ancak tüm uç noktalar belirtmeyin.</span><span class="sxs-lookup"><span data-stu-id="e15f3-138">To configure metadata on a service that uses default endpoints, specify the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> in the configuration file as in the previous example, but do not specify any endpoints.</span></span> <span data-ttu-id="e15f3-139">Yapılandırma dosyası, ardından şöyle görünebilir.</span><span class="sxs-lookup"><span data-stu-id="e15f3-139">The configuration file would then look like this.</span></span>  
  
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
  
     <span data-ttu-id="e15f3-140">Hizmetin sahip olduğu bir <xref:System.ServiceModel.Description.ServiceMetadataBehavior> ile `httpGetEnabled` kümesine `true`etkin meta veri yayımlama hizmeti sahiptir ve uç nokta açıkça eklenmiş olduğundan, çalışma zamanı varsayılan uç noktalar ekler.</span><span class="sxs-lookup"><span data-stu-id="e15f3-140">Because the service has a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> with the `httpGetEnabled` set to `true`, the service has publishing metadata enabled, and because no endpoints were explicitly added, the runtime adds the default endpoints.</span></span> <span data-ttu-id="e15f3-141">Varsayılan uç noktaları, bağlamalar ve davranışları hakkında daha fazla bilgi için bkz. [Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="e15f3-141">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e15f3-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="e15f3-142">Example</span></span>  
 <span data-ttu-id="e15f3-143">Aşağıdaki kod örneği, hizmet için meta verilerini yayımlayan yapılandırma dosyası ile temel bir WCF hizmeti ve uygulamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e15f3-143">The following code example shows the implementation of a basic WCF service and the configuration file that publishes metadata for the service.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e15f3-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e15f3-144">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
- [<span data-ttu-id="e15f3-145">Nasıl yapılır: Yönetilen bir uygulamada bir WCF Hizmeti barındırma</span><span class="sxs-lookup"><span data-stu-id="e15f3-145">How to: Host a WCF Service in a Managed Application</span></span>](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)
- [<span data-ttu-id="e15f3-146">Kendini Barındırma</span><span class="sxs-lookup"><span data-stu-id="e15f3-146">Self-Host</span></span>](../../../../docs/framework/wcf/samples/self-host.md)
- [<span data-ttu-id="e15f3-147">Meta Veri Mimarisine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e15f3-147">Metadata Architecture Overview</span></span>](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)
- [<span data-ttu-id="e15f3-148">Meta Verileri Kullanma</span><span class="sxs-lookup"><span data-stu-id="e15f3-148">Using Metadata</span></span>](../../../../docs/framework/wcf/feature-details/using-metadata.md)
- [<span data-ttu-id="e15f3-149">Nasıl yapılır: Kod kullanarak bir hizmet için meta verileri yayımlama</span><span class="sxs-lookup"><span data-stu-id="e15f3-149">How to: Publish Metadata for a Service Using Code</span></span>](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)
