---
title: 'Nasıl yapılır: ASP.NET AJAX Uç Noktası Eklemek için Yapılandırma Kullanma'
ms.date: 03/30/2017
ms.assetid: 7cd0099e-dc3a-47e4-a38c-6e10f997f6ea
ms.openlocfilehash: 3ccfb34614707c17885da3ed37f545bbab808869
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73978260"
---
# <a name="how-to-use-configuration-to-add-an-aspnet-ajax-endpoint"></a><span data-ttu-id="f1c2b-102">Nasıl yapılır: ASP.NET AJAX Uç Noktası Eklemek için Yapılandırma Kullanma</span><span class="sxs-lookup"><span data-stu-id="f1c2b-102">How to: Use Configuration to Add an ASP.NET AJAX Endpoint</span></span>
<span data-ttu-id="f1c2b-103">Windows Communication Foundation (WCF), istemci Web sitesinde JavaScript 'ten çağrılabilen ASP.NET AJAX özellikli bir uç nokta sağlayan bir hizmet oluşturmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="f1c2b-103">Windows Communication Foundation (WCF) allows you to create a service that makes an ASP.NET AJAX-enabled endpoint available that can be called from JavaScript on a client Web site.</span></span> <span data-ttu-id="f1c2b-104">Böyle bir uç nokta oluşturmak için, diğer tüm Windows Communication Foundation (WCF) uç noktalarında olduğu gibi bir yapılandırma dosyası ya da herhangi bir yapılandırma öğesi gerektirmeyen bir yöntemi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f1c2b-104">To create such an endpoint, you can either use a configuration file, as with all other Windows Communication Foundation (WCF) endpoints, or use a method that does not require any configuration elements.</span></span> <span data-ttu-id="f1c2b-105">Bu konu, yapılandırma yaklaşımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f1c2b-105">This topic demonstrates the configuration approach.</span></span>  
  
 <span data-ttu-id="f1c2b-106">Hizmet uç noktasının ASP.NET AJAX özellikli hale gelmesini sağlayan yordamın bir bölümü, <xref:System.ServiceModel.WebHttpBinding> kullanmak için uç noktayı yapılandırmayı ve [\<enableWebScript >](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) uç nokta davranışını eklemeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="f1c2b-106">The part of the procedure that enables the service endpoint to become ASP.NET AJAX-enabled consists of configuring the endpoint to use the <xref:System.ServiceModel.WebHttpBinding> and to add the [\<enableWebScript>](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) endpoint behavior.</span></span> <span data-ttu-id="f1c2b-107">Uç nokta yapılandırıldıktan sonra, hizmeti uygulama ve barındırma adımları herhangi bir WCF hizmeti tarafından kullanılanlarla benzerdir.</span><span class="sxs-lookup"><span data-stu-id="f1c2b-107">After configuring the endpoint, the steps to implement and host the service are similar to those used by any WCF service.</span></span> <span data-ttu-id="f1c2b-108">Çalışan bir örnek için bkz. [http post kullanan AJAX Hizmeti](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span><span class="sxs-lookup"><span data-stu-id="f1c2b-108">For a working example, see the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span></span>  
  
 <span data-ttu-id="f1c2b-109">Yapılandırma kullanmadan bir ASP.NET AJAX uç noktası yapılandırma hakkında daha fazla bilgi için bkz. [nasıl yapılır: yapılandırma kullanmadan ASP.NET AJAX uç noktası ekleme](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="f1c2b-109">For more information about how to configure an ASP.NET AJAX endpoint without using configuration, see [How to: Add an ASP.NET AJAX Endpoint Without Using Configuration](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span></span>  
  
## <a name="to-create-a-basic-wcf-service"></a><span data-ttu-id="f1c2b-110">Temel bir WCF hizmeti oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="f1c2b-110">To create a basic WCF service</span></span>  
  
1. <span data-ttu-id="f1c2b-111"><xref:System.ServiceModel.ServiceContractAttribute> özniteliğiyle işaretlenmiş bir arabirimle birlikte temel bir WCF hizmet sözleşmesi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="f1c2b-111">Define a basic WCF service contract with an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="f1c2b-112">Her işlemi <xref:System.ServiceModel.OperationContractAttribute>işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="f1c2b-112">Mark each operation with the <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="f1c2b-113"><xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> özelliğini ayarladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="f1c2b-113">Be sure to set the <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> property.</span></span>  
  
    ```csharp
    [ServiceContract(Namespace = "MyService")]  
    public interface ICalculator  
    {  
        [OperationContract]  
         // This operation returns the sum of d1 and d2.  
        double Add(double n1, double n2);  
  
        //Other operations omitted…  
  
    }  
    ```  
  
2. <span data-ttu-id="f1c2b-114">`ICalculator` hizmet sözleşmesini bir `CalculatorService`uygulayın.</span><span class="sxs-lookup"><span data-stu-id="f1c2b-114">Implement the `ICalculator` service contract with a `CalculatorService`.</span></span>  
  
    ```csharp
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }
        // Other operations omitted…
    }
    ```  
  
3. <span data-ttu-id="f1c2b-115">`ICalculator` ve `CalculatorService` uygulamalar için bir ad alanı bloğunda bir ad alanı tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="f1c2b-115">Define a namespace for the `ICalculator` and `CalculatorService` implementations by wrapping them in a namespace block.</span></span>  
  
    ```csharp
    namespace Microsoft.Ajax.Samples
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
## <a name="to-create-an-aspnet-ajax-endpoint-for-the-service"></a><span data-ttu-id="f1c2b-116">Hizmet için bir ASP.NET AJAX uç noktası oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="f1c2b-116">To create an ASP.NET AJAX endpoint for the service</span></span>  
  
1. <span data-ttu-id="f1c2b-117">Bir davranış yapılandırması oluşturun ve hizmetin ASP.NET AJAX özellikli uç noktaları için [\<enableWebScript >](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) davranışını belirtin.</span><span class="sxs-lookup"><span data-stu-id="f1c2b-117">Create a behavior configuration and specify the [\<enableWebScript>](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) behavior for ASP.NET AJAX-enabled endpoints of the service.</span></span>  
  
    ```xml  
    <system.serviceModel>  
        <behaviors>  
            <endpointBehaviors>  
                <behavior name="AspNetAjaxBehavior">  
                    <enableWebScript />  
                </behavior>  
            </endpointBehaviors>  
        </behaviors>  
    </system.serviceModel>  
    ```  
  
2. <span data-ttu-id="f1c2b-118">Önceki adımda tanımlanan <xref:System.ServiceModel.WebHttpBinding> ve ASP.NET AJAX davranışını kullanan hizmet için bir uç nokta oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f1c2b-118">Create an endpoint for the service that uses the <xref:System.ServiceModel.WebHttpBinding> and the ASP.NET AJAX behavior defined in the previous step.</span></span>  
  
    ```xml  
    <system.serviceModel>  
        <services>  
            <service name="Microsoft.Ajax.Samples.CalculatorService">  
                <endpoint address=""  
                    behaviorConfiguration="AspNetAjaxBehavior"   
                    binding="webHttpBinding"  
                    contract="Microsoft.Ajax.Samples.ICalculator" />  
            </service>  
        </services>  
    </system.serviceModel>   
    ```  
  
## <a name="to-host-the-service-in-iis"></a><span data-ttu-id="f1c2b-119">Hizmeti IIS 'de barındırmak için</span><span class="sxs-lookup"><span data-stu-id="f1c2b-119">To host the service in IIS</span></span>  
  
1. <span data-ttu-id="f1c2b-120">Hizmeti IIS 'de barındırmak için, uygulamada. svc uzantılı yeni bir dosya adlı hizmet oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f1c2b-120">To host the service in IIS, create a new file named service with a .svc extension in the application.</span></span> <span data-ttu-id="f1c2b-121">Hizmet için uygun [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) yönerge bilgilerini ekleyerek bu dosyayı düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="f1c2b-121">Edit this file by adding the appropriate [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive information for the service.</span></span> <span data-ttu-id="f1c2b-122">Örneğin, `CalculatorService` örneği için hizmet dosyasındaki içerik aşağıdaki bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="f1c2b-122">For example, the content in the service file for the `CalculatorService` sample contains the following information.</span></span>  
  
    ```
    <%@ServiceHost   
    language=c#   
    Debug="true"   
    Service="Microsoft.Ajax.Samples.CalculatorService"  
    %>  
    ```  
  
2. <span data-ttu-id="f1c2b-123">IIS 'de barındırma hakkında daha fazla bilgi için bkz. [nasıl yapılır: IIS 'de WCF hizmeti barındırma](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).</span><span class="sxs-lookup"><span data-stu-id="f1c2b-123">For more information about hosting in IIS, see [How to: Host a WCF Service in IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).</span></span>  
  
## <a name="to-call-the-service"></a><span data-ttu-id="f1c2b-124">Hizmeti çağırmak için</span><span class="sxs-lookup"><span data-stu-id="f1c2b-124">To call the service</span></span>  
  
1. <span data-ttu-id="f1c2b-125">Uç nokta,. svc dosyasına göre boş bir adreste yapılandırılır, bu nedenle hizmet artık kullanılabilir ve hizmet. svc/\<işlem > (örneğin, `Add` işlemi için Service. svc/Add) göndererek çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="f1c2b-125">The endpoint is configured at an empty address relative to the .svc file, so the service is now available and can be invoked by sending requests to service.svc/\<operation> - for example, service.svc/Add for the `Add` operation.</span></span> <span data-ttu-id="f1c2b-126">Bunu, ASP.NET AJAX betik Yöneticisi denetiminin betikler koleksiyonuna Endpoint URL 'SI girerek kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f1c2b-126">You can use it by entering the endpoint URL into the Scripts collection of the ASP.NET AJAX Script Manager control.</span></span> <span data-ttu-id="f1c2b-127">Bir örnek için bkz. [http post kullanan AJAX Hizmeti](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span><span class="sxs-lookup"><span data-stu-id="f1c2b-127">For an example, see the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1c2b-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f1c2b-128">See also</span></span>

- [<span data-ttu-id="f1c2b-129">ASP.NET AJAX için WCF Hizmetleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f1c2b-129">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)
- [<span data-ttu-id="f1c2b-130">Nasıl yapılır: AJAX Etkinleştirilmiş ASP.NET Web Hizmetlerini WCF'ye Taşıma</span><span class="sxs-lookup"><span data-stu-id="f1c2b-130">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
