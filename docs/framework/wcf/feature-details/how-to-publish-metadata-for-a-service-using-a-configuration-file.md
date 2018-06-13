---
title: 'Nasıl yapılır: Yapılandırma Dosyası Kullanarak Bir Hizmet için Meta Verileri Yayımlama'
ms.date: 03/30/2017
ms.assetid: f061443f-92df-4824-b36a-609c4cd14a17
ms.openlocfilehash: 94013c69bec0ea37c9260567437aeada3ebe2ae4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33495700"
---
# <a name="how-to-publish-metadata-for-a-service-using-a-configuration-file"></a><span data-ttu-id="73306-102">Nasıl yapılır: Yapılandırma Dosyası Kullanarak Bir Hizmet için Meta Verileri Yayımlama</span><span class="sxs-lookup"><span data-stu-id="73306-102">How to: Publish Metadata for a Service Using a Configuration File</span></span>
<span data-ttu-id="73306-103">Bu, bir Windows Communication Foundation (WCF) hizmet için meta veri yayımlama gösteren iki nasıl yapılır konuları biridir.</span><span class="sxs-lookup"><span data-stu-id="73306-103">This is one of two how-to topics that demonstrate publishing metadata for a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="73306-104">Bir hizmeti bir yapılandırma dosyası kullanarak ve kod kullanarak meta verileri, nasıl yayınlamalıdır belirtmek için iki yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="73306-104">There are two ways to specify how a service should publish metadata, using a configuration file and using code.</span></span> <span data-ttu-id="73306-105">Bu konuda, bir yapılandırma dosyası kullanarak bir hizmet için meta verileri yayımlama gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="73306-105">This topic shows how to publish metadata for a service using a configuration file.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="73306-106">Bu konu, güvenli olmayan bir şekilde meta verileri yayımlama gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="73306-106">This topic shows how to publish metadata in an unsecure manner.</span></span> <span data-ttu-id="73306-107">Herhangi bir istemci hizmetinden meta verileri alabilir.</span><span class="sxs-lookup"><span data-stu-id="73306-107">Any client can retrieve the metadata from the service.</span></span> <span data-ttu-id="73306-108">Hizmetinizin meta verileri güvenli bir şekilde yayımlamak için gerekli olup olmadığını görmek [özel güvenli meta veri uç noktasının](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span><span class="sxs-lookup"><span data-stu-id="73306-108">If you require your service to publish metadata in a secure manner, see [Custom Secure Metadata Endpoint](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span></span>  
  
 <span data-ttu-id="73306-109">Kodda meta veri yayımlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: meta verilerini kullanarak bir hizmet kodu yayımlama](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md).</span><span class="sxs-lookup"><span data-stu-id="73306-109">For more information about publishing metadata in code, see [How to: Publish Metadata for a Service Using Code](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md).</span></span> <span data-ttu-id="73306-110">Meta veri yayımlama sağlayan bir WS-aktarımı GET isteği ya da bir HTTP/GET isteği kullanarak kullanarak meta verileri almak istemcileri `?wsdl` sorgu dizesi.</span><span class="sxs-lookup"><span data-stu-id="73306-110">Publishing metadata allows clients to retrieve the metadata using a WS-Transfer GET request or an HTTP/GET request using the `?wsdl` query string.</span></span> <span data-ttu-id="73306-111">Kod çalıştığından emin olmak için temel bir WCF Hizmeti oluşturun.</span><span class="sxs-lookup"><span data-stu-id="73306-111">To be sure that the code is working, create a basic WCF service.</span></span> <span data-ttu-id="73306-112">Kolaylık olması için temel bir kendi kendini barındıran hizmet aşağıdaki kodu sağlanır.</span><span class="sxs-lookup"><span data-stu-id="73306-112">For simplicity, a basic self-hosted service is provided in the following code.</span></span>  
  
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
  
 <span data-ttu-id="73306-113">Bu hizmet bir yapılandırma dosyası kullanarak yapılandırılan kendi kendini barındıran bir hizmettir.</span><span class="sxs-lookup"><span data-stu-id="73306-113">This service is a self-hosted service, which is configured using a configuration file.</span></span> <span data-ttu-id="73306-114">Aşağıdaki yapılandırma dosyası bir başlangıç noktası olarak görev yapar.</span><span class="sxs-lookup"><span data-stu-id="73306-114">The following configuration file serves as a starting point.</span></span>  
  
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
  
### <a name="to-publish-metadata-for-a-wcf-service-using-an-application-configuration-file"></a><span data-ttu-id="73306-115">Uygulama yapılandırma dosyası kullanarak bir WCF Hizmeti meta verilerini yayımlamak için</span><span class="sxs-lookup"><span data-stu-id="73306-115">To publish metadata for a WCF service using an application configuration file</span></span>  
  
1.  <span data-ttu-id="73306-116">Kapatma sonrasında App.config dosyası içinde `</services>` öğesini oluşturmak bir `<behaviors>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="73306-116">Within the App.config file, after the closing `</services>` element, create a `<behaviors>` element.</span></span>  
  
  
  
2.  <span data-ttu-id="73306-117">İçinde `<behaviors>` öğesi ekleme bir `<serviceBehaviors>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="73306-117">Within the `<behaviors>` element, add a `<serviceBehaviors>` element.</span></span>  
  
  
  
3.  <span data-ttu-id="73306-118">Ekleme bir `<behavior>` öğesine `<serviceBehaviors>` öğesi için bir değer belirtin `name` özniteliği `<behavior>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="73306-118">Add a `<behavior>` element to the `<serviceBehaviors>` element and specify a value for the `name` attribute of the `<behavior>` element.</span></span>  
  
  
  
4.  <span data-ttu-id="73306-119">Ekleme bir `<serviceMetadata>` öğesine `<behavior>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="73306-119">Add a `<serviceMetadata>` element to the `<behavior>` element.</span></span> <span data-ttu-id="73306-120">Ayarlama `httpGetEnabled` özniteliğini `true` ve `policyVersion` özniteliği için Policy15.</span><span class="sxs-lookup"><span data-stu-id="73306-120">Set the `httpGetEnabled` attribute to `true` and the `policyVersion` attribute to Policy15.</span></span> <span data-ttu-id="73306-121">`httpGetEnabled` bir HTTP GET isteği tarafından yapılan meta veri isteklerine hizmet sağlar.</span><span class="sxs-lookup"><span data-stu-id="73306-121">`httpGetEnabled` allows the service to respond to metadata requests made by an HTTP GET request.</span></span> <span data-ttu-id="73306-122">`policyVersion` WS-Policy 1.5 meta verilerini oluştururken uygun hizmete bildirir.</span><span class="sxs-lookup"><span data-stu-id="73306-122">`policyVersion` tells the service to conform to WS-Policy 1.5 when generating metadata.</span></span>  
  
  
  
5.  <span data-ttu-id="73306-123">Ekleme bir `behaviorConfiguration` özniteliğini `<service>` öğesi ve belirtin `name` özniteliği `<behavior>` adım 1 ' de eklenen aşağıdaki kod örneğinde gösterildiği gibi öğesi.</span><span class="sxs-lookup"><span data-stu-id="73306-123">Add a `behaviorConfiguration` attribute to the `<service>` element and specify the `name` attribute of the `<behavior>` element added in step 1, as shown in the following code example.</span></span>  
  
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
  
6.  <span data-ttu-id="73306-124">Bir veya daha fazla Ekle `<endpoint>` sözleşme ile öğeleri kümesine `IMetadataExchange`aşağıdaki kod örneğinde gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="73306-124">Add one or more `<endpoint>` elements with the contract set to `IMetadataExchange`, as shown in the following code example.</span></span>  
  
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
  
7.  <span data-ttu-id="73306-125">Önceki adımda eklediğiniz meta veri uç noktaları için ayarlamak `binding` özniteliği şunlardan biri:</span><span class="sxs-lookup"><span data-stu-id="73306-125">For the metadata endpoints added in the previous step, set the `binding` attribute to one of the following:</span></span>  
  
    -   <span data-ttu-id="73306-126">`mexHttpBinding` için HTTP yayımlama.</span><span class="sxs-lookup"><span data-stu-id="73306-126">`mexHttpBinding` for HTTP publication.</span></span>  
  
    -   <span data-ttu-id="73306-127">`mexHttpsBinding` için HTTPS yayımlama.</span><span class="sxs-lookup"><span data-stu-id="73306-127">`mexHttpsBinding` for HTTPS publication.</span></span>  
  
    -   <span data-ttu-id="73306-128">`mexNamedPipeBinding` adlandırılmış kanal yayını için.</span><span class="sxs-lookup"><span data-stu-id="73306-128">`mexNamedPipeBinding` for named pipe publication.</span></span>  
  
    -   <span data-ttu-id="73306-129">`mexTcpBinding` için TCP yayımlama.</span><span class="sxs-lookup"><span data-stu-id="73306-129">`mexTcpBinding` for TCP publication.</span></span>  
  
8.  <span data-ttu-id="73306-130">Bir önceki adımda eklediğiniz meta veri uç noktaları için adres eşit olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="73306-130">For the metadata endpoints added in a previous step, set the address equal to:</span></span>  
  
    -   <span data-ttu-id="73306-131">Temel adres meta veri bağlama ile aynı olduğunda ana uygulamanın taban adresi yayın noktası olarak kullanmak için boş bir dize.</span><span class="sxs-lookup"><span data-stu-id="73306-131">An empty string to use the host application's base address as the publication point if the base address is the same as the metadata binding.</span></span>  
  
    -   <span data-ttu-id="73306-132">Ana bilgisayar uygulamasını taban adresi varsa, göreli bir adres.</span><span class="sxs-lookup"><span data-stu-id="73306-132">A relative address if the host application has a base address.</span></span>  
  
    -   <span data-ttu-id="73306-133">Mutlak bir adres.</span><span class="sxs-lookup"><span data-stu-id="73306-133">An absolute address.</span></span>  
  
9. <span data-ttu-id="73306-134">Derleme ve konsol uygulamasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="73306-134">Build and run the console application.</span></span>  
  
10. <span data-ttu-id="73306-135">Hizmetin taban adresine göz atmak için Internet Explorer kullanın (http://localhost:8001/MetadataSample Bu örnekte) ve meta veri yayımlama açık olduğunu doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="73306-135">Use Internet Explorer to browse to the base address of the service (http://localhost:8001/MetadataSample in this sample) and verify that the metadata publishing is turned on.</span></span> <span data-ttu-id="73306-136">Değilse, sayfanın üst kısmındaki ortaya çıkan bir ileti görüntüler: "Bu hizmet için meta veri yayımlama şu anda devre dışı."</span><span class="sxs-lookup"><span data-stu-id="73306-136">If not, a message at the top of the resulting page displays: "Metadata publishing for this service is currently disabled."</span></span>  
  
### <a name="to-use-default-endpoints"></a><span data-ttu-id="73306-137">Varsayılan uç noktalar kullanmak için</span><span class="sxs-lookup"><span data-stu-id="73306-137">To use default endpoints</span></span>  
  
1.  <span data-ttu-id="73306-138">Meta veri varsayılan uç noktaları kullanan bir hizmeti yapılandırmak için belirtmeniz <xref:System.ServiceModel.Description.ServiceMetadataBehavior> yapılandırmasında dosya önceki örnekte olduğu gibi ancak uç nokta belirtmeyin.</span><span class="sxs-lookup"><span data-stu-id="73306-138">To configure metadata on a service that uses default endpoints, specify the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> in the configuration file as in the previous example, but do not specify any endpoints.</span></span> <span data-ttu-id="73306-139">Yapılandırma dosyası ardından şuna benzer.</span><span class="sxs-lookup"><span data-stu-id="73306-139">The configuration file would then look like this.</span></span>  
  
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
  
     <span data-ttu-id="73306-140">Hizmetin sahip olduğu bir <xref:System.ServiceModel.Description.ServiceMetadataBehavior> ile `httpGetEnabled` kümesine `true`hizmeti etkin meta veri yayımlama sahiptir ve uç nokta yok açıkça eklenmiş olduğundan çalışma zamanı varsayılan uç noktaları ekler.</span><span class="sxs-lookup"><span data-stu-id="73306-140">Because the service has a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> with the `httpGetEnabled` set to `true`, the service has publishing metadata enabled, and because no endpoints were explicitly added, the runtime adds the default endpoints.</span></span> <span data-ttu-id="73306-141">Varsayılan uç noktalar, bağlamaları ve davranışları hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="73306-141">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="73306-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="73306-142">Example</span></span>  
 <span data-ttu-id="73306-143">Aşağıdaki kod örneği temel bir WCF hizmeti ve hizmet için meta verilerini yayımlayan yapılandırma dosyası gösterir.</span><span class="sxs-lookup"><span data-stu-id="73306-143">The following code example shows the implementation of a basic WCF service and the configuration file that publishes metadata for the service.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="73306-144">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="73306-144">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>  
 [<span data-ttu-id="73306-145">Nasıl yapılır: Yönetilen Bir Uygulamada Bir WCF Hizmeti Barındırma</span><span class="sxs-lookup"><span data-stu-id="73306-145">How to: Host a WCF Service in a Managed Application</span></span>](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)  
 [<span data-ttu-id="73306-146">Kendini Barındırma</span><span class="sxs-lookup"><span data-stu-id="73306-146">Self-Host</span></span>](../../../../docs/framework/wcf/samples/self-host.md)  
 [<span data-ttu-id="73306-147">Meta Veri Mimarisine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="73306-147">Metadata Architecture Overview</span></span>](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)  
 [<span data-ttu-id="73306-148">Meta Verileri Kullanma</span><span class="sxs-lookup"><span data-stu-id="73306-148">Using Metadata</span></span>](../../../../docs/framework/wcf/feature-details/using-metadata.md)  
 [<span data-ttu-id="73306-149">Nasıl yapılır: Kod Kullanarak Bir Hizmet için Meta Verileri Yayımlama</span><span class="sxs-lookup"><span data-stu-id="73306-149">How to: Publish Metadata for a Service Using Code</span></span>](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)
