---
title: 'Nasıl yapılır: ASP.NET AJAX Uç Noktası Eklemek için Yapılandırma Kullanma'
ms.date: 03/30/2017
ms.assetid: 7cd0099e-dc3a-47e4-a38c-6e10f997f6ea
ms.openlocfilehash: 33f99161034db2aa142a422139406a1a68d42b2c
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972272"
---
# <a name="how-to-use-configuration-to-add-an-aspnet-ajax-endpoint"></a><span data-ttu-id="67f4d-102">Nasıl yapılır: ASP.NET AJAX Uç Noktası Eklemek için Yapılandırma Kullanma</span><span class="sxs-lookup"><span data-stu-id="67f4d-102">How to: Use Configuration to Add an ASP.NET AJAX Endpoint</span></span>
<span data-ttu-id="67f4d-103">Windows Communication Foundation (WCF), istemci Web sitesinde JavaScript 'ten çağrılabilen ASP.NET AJAX özellikli bir uç nokta sağlayan bir hizmet oluşturmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="67f4d-103">Windows Communication Foundation (WCF) allows you to create a service that makes an ASP.NET AJAX-enabled endpoint available that can be called from JavaScript on a client Web site.</span></span> <span data-ttu-id="67f4d-104">Böyle bir uç nokta oluşturmak için, diğer tüm Windows Communication Foundation (WCF) uç noktalarında olduğu gibi bir yapılandırma dosyası ya da herhangi bir yapılandırma öğesi gerektirmeyen bir yöntemi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="67f4d-104">To create such an endpoint, you can either use a configuration file, as with all other Windows Communication Foundation (WCF) endpoints, or use a method that does not require any configuration elements.</span></span> <span data-ttu-id="67f4d-105">Bu konu, yapılandırma yaklaşımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="67f4d-105">This topic demonstrates the configuration approach.</span></span>  
  
 <span data-ttu-id="67f4d-106">Hizmet uç noktasının ASP.NET AJAX özellikli hale gelmesini sağlayan yordamın bir bölümü, <xref:System.ServiceModel.WebHttpBinding> ' i kullanmak için bitiş noktasını yapılandırmayı ve [ \<enablewebscript >](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) uç noktası davranışını eklemeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="67f4d-106">The part of the procedure that enables the service endpoint to become ASP.NET AJAX-enabled consists of configuring the endpoint to use the <xref:System.ServiceModel.WebHttpBinding> and to add the [\<enableWebScript>](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) endpoint behavior.</span></span> <span data-ttu-id="67f4d-107">Uç nokta yapılandırıldıktan sonra, hizmeti uygulama ve barındırma adımları herhangi bir WCF hizmeti tarafından kullanılanlarla benzerdir.</span><span class="sxs-lookup"><span data-stu-id="67f4d-107">After configuring the endpoint, the steps to implement and host the service are similar to those used by any WCF service.</span></span> <span data-ttu-id="67f4d-108">Çalışan bir örnek için bkz. [http post kullanan AJAX Hizmeti](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span><span class="sxs-lookup"><span data-stu-id="67f4d-108">For a working example, see the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span></span>  
  
 <span data-ttu-id="67f4d-109">Yapılandırma kullanmadan bir ASP.NET AJAX uç noktası yapılandırma hakkında daha fazla bilgi için bkz [. nasıl yapılır: Yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md)kullanmadan bir ASP.NET AJAX uç noktası ekleyin.</span><span class="sxs-lookup"><span data-stu-id="67f4d-109">For more information about how to configure an ASP.NET AJAX endpoint without using configuration, see [How to: Add an ASP.NET AJAX Endpoint Without Using Configuration](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span></span>  
  
## <a name="to-create-a-basic-wcf-service"></a><span data-ttu-id="67f4d-110">Temel bir WCF hizmeti oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="67f4d-110">To create a basic WCF service</span></span>  
  
1. <span data-ttu-id="67f4d-111"><xref:System.ServiceModel.ServiceContractAttribute> Özniteliği ile işaretlenmiş bir arabirimle birlikte temel bir WCF hizmeti sözleşmesi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="67f4d-111">Define a basic WCF service contract with an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="67f4d-112">Her işlemi ile <xref:System.ServiceModel.OperationContractAttribute>işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="67f4d-112">Mark each operation with the <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="67f4d-113"><xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> Özelliği ayarladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="67f4d-113">Be sure to set the <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> property.</span></span>  
  
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
  
2. <span data-ttu-id="67f4d-114">Hizmet sözleşmesini bir `CalculatorService`ile uygulayın. `ICalculator`</span><span class="sxs-lookup"><span data-stu-id="67f4d-114">Implement the `ICalculator` service contract with a `CalculatorService`.</span></span>  
  
    ```csharp
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
  
    //Other operations omitted…  
    ```  
  
3. <span data-ttu-id="67f4d-115">Bir ad alanı bloğunda `ICalculator` sarmalayarak `CalculatorService` ve uygulamalar için bir ad alanı tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="67f4d-115">Define a namespace for the `ICalculator` and `CalculatorService` implementations by wrapping them in a namespace block.</span></span>  
  
    ```csharp
    namespace Microsoft.Ajax.Samples  
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
## <a name="to-create-an-aspnet-ajax-endpoint-for-the-service"></a><span data-ttu-id="67f4d-116">Hizmet için bir ASP.NET AJAX uç noktası oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="67f4d-116">To create an ASP.NET AJAX endpoint for the service</span></span>  
  
1. <span data-ttu-id="67f4d-117">Bir davranış yapılandırması oluşturun ve hizmetin ASP.NET AJAX özellikli uç noktaları için [ \<enablewebscript >](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) davranışını belirtin.</span><span class="sxs-lookup"><span data-stu-id="67f4d-117">Create a behavior configuration and specify the [\<enableWebScript>](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) behavior for ASP.NET AJAX-enabled endpoints of the service.</span></span>  
  
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
  
2. <span data-ttu-id="67f4d-118">Önceki adımda tanımlanan <xref:System.ServiceModel.WebHttpBinding> ve ASP.NET AJAX davranışını kullanan hizmet için bir uç nokta oluşturun.</span><span class="sxs-lookup"><span data-stu-id="67f4d-118">Create an endpoint for the service that uses the <xref:System.ServiceModel.WebHttpBinding> and the ASP.NET AJAX behavior defined in the previous step.</span></span>  
  
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
  
## <a name="to-host-the-service-in-iis"></a><span data-ttu-id="67f4d-119">Hizmeti IIS 'de barındırmak için</span><span class="sxs-lookup"><span data-stu-id="67f4d-119">To host the service in IIS</span></span>  
  
1. <span data-ttu-id="67f4d-120">Hizmeti IIS 'de barındırmak için, uygulamada. svc uzantılı yeni bir dosya adlı hizmet oluşturun.</span><span class="sxs-lookup"><span data-stu-id="67f4d-120">To host the service in IIS, create a new file named service with a .svc extension in the application.</span></span> <span data-ttu-id="67f4d-121">Hizmet için uygun [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) yönergesi bilgilerini ekleyerek bu dosyayı düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="67f4d-121">Edit this file by adding the appropriate [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive information for the service.</span></span> <span data-ttu-id="67f4d-122">Örneğin, `CalculatorService` örnek için hizmet dosyasındaki içerik aşağıdaki bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="67f4d-122">For example, the content in the service file for the `CalculatorService` sample contains the following information.</span></span>  
  
    ```
    <%@ServiceHost   
    language=c#   
    Debug="true"   
    Service="Microsoft.Ajax.Samples.CalculatorService"  
    %>  
    ```  
  
2. <span data-ttu-id="67f4d-123">IIS 'de barındırma hakkında daha fazla bilgi için bkz [. nasıl yapılır: IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)'de bir WCF hizmeti barındırın.</span><span class="sxs-lookup"><span data-stu-id="67f4d-123">For more information about hosting in IIS, see [How to: Host a WCF Service in IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).</span></span>  
  
## <a name="to-call-the-service"></a><span data-ttu-id="67f4d-124">Hizmeti çağırmak için</span><span class="sxs-lookup"><span data-stu-id="67f4d-124">To call the service</span></span>  
  
1. <span data-ttu-id="67f4d-125">Uç nokta,. svc dosyası ile ilgili boş bir adreste yapılandırılır, bu nedenle hizmet artık kullanılabilir ve hizmet. svc/\<işlem > istek göndererek çağrılabilir. Örneğin, `Add` işlem için Service. svc/Add.</span><span class="sxs-lookup"><span data-stu-id="67f4d-125">The endpoint is configured at an empty address relative to the .svc file, so the service is now available and can be invoked by sending requests to service.svc/\<operation> - for example, service.svc/Add for the `Add` operation.</span></span> <span data-ttu-id="67f4d-126">Bunu, ASP.NET AJAX betik Yöneticisi denetiminin betikler koleksiyonuna Endpoint URL 'SI girerek kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="67f4d-126">You can use it by entering the endpoint URL into the Scripts collection of the ASP.NET AJAX Script Manager control.</span></span> <span data-ttu-id="67f4d-127">Bir örnek için bkz. [http post kullanan AJAX Hizmeti](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span><span class="sxs-lookup"><span data-stu-id="67f4d-127">For an example, see the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67f4d-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="67f4d-128">See also</span></span>

- [<span data-ttu-id="67f4d-129">ASP.NET AJAX için WCF Hizmetleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="67f4d-129">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)
- [<span data-ttu-id="67f4d-130">Nasıl yapılır: AJAX etkin ASP.NET Web hizmetlerini WCF 'ye geçirme</span><span class="sxs-lookup"><span data-stu-id="67f4d-130">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
