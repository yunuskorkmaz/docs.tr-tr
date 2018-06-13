---
title: 'Nasıl yapılır: ASP.NET AJAX Uç Noktası Eklemek için Yapılandırma Kullanma'
ms.date: 03/30/2017
ms.assetid: 7cd0099e-dc3a-47e4-a38c-6e10f997f6ea
ms.openlocfilehash: f14b441ead7c701aa4f794370fc5f54ad3b4a4e6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33495008"
---
# <a name="how-to-use-configuration-to-add-an-aspnet-ajax-endpoint"></a><span data-ttu-id="fbee2-102">Nasıl yapılır: ASP.NET AJAX Uç Noktası Eklemek için Yapılandırma Kullanma</span><span class="sxs-lookup"><span data-stu-id="fbee2-102">How to: Use Configuration to Add an ASP.NET AJAX Endpoint</span></span>
<span data-ttu-id="fbee2-103">Windows Communication Foundation (WCF), ASP.NET AJAX etkinleştirilmiş uç istemci Web sitesinde JavaScript'ten çağrılabilir kullanılabilir hale getirir bir hizmet oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="fbee2-103">Windows Communication Foundation (WCF) allows you to create a service that makes an ASP.NET AJAX-enabled endpoint available that can be called from JavaScript on a client Web site.</span></span> <span data-ttu-id="fbee2-104">Bu tür bir uç nokta oluşturmak için tüm diğer Windows Communication Foundation (WCF) uç noktaları gibi bir yapılandırma dosyası kullanın veya tüm yapılandırma öğeleri gerektirmeyen bir yöntemi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fbee2-104">To create such an endpoint, you can either use a configuration file, as with all other Windows Communication Foundation (WCF) endpoints, or use a method that does not require any configuration elements.</span></span> <span data-ttu-id="fbee2-105">Bu konuda yapılandırma yaklaşım gösterilir.</span><span class="sxs-lookup"><span data-stu-id="fbee2-105">This topic demonstrates the configuration approach.</span></span>  
  
 <span data-ttu-id="fbee2-106">Hizmet uç noktası, ASP.NET AJAX etkinleştirilmiş olmasını sağlayan yordamının parçası kullanmak için uç nokta yapılandırmayı içerir <xref:System.ServiceModel.WebHttpBinding> ve eklemek için [ \<enableWebScript >](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) uç noktası davranışı.</span><span class="sxs-lookup"><span data-stu-id="fbee2-106">The part of the procedure that enables the service endpoint to become ASP.NET AJAX-enabled consists of configuring the endpoint to use the <xref:System.ServiceModel.WebHttpBinding> and to add the [\<enableWebScript>](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) endpoint behavior.</span></span> <span data-ttu-id="fbee2-107">Uç nokta yapılandırdıktan sonra uygulama ve hizmet barındırmak için adımları herhangi bir WCF hizmeti tarafından kullanılan benzerdir.</span><span class="sxs-lookup"><span data-stu-id="fbee2-107">After configuring the endpoint, the steps to implement and host the service are similar to those used by any WCF service.</span></span> <span data-ttu-id="fbee2-108">Çalışan bir örnek için bkz: [AJAX hizmeti kullanarak HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span><span class="sxs-lookup"><span data-stu-id="fbee2-108">For a working example, see the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span></span>  
  
 <span data-ttu-id="fbee2-109">Yapılandırma kullanmadan ASP.NET AJAX uç noktası yapılandırma hakkında daha fazla bilgi için bkz: [nasıl yapılır: ASP.NET AJAX uç nokta olmadan kullanarak Yapılandırması Ekle](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="fbee2-109">For more information about how to configure an ASP.NET AJAX endpoint without using configuration, see [How to: Add an ASP.NET AJAX Endpoint Without Using Configuration](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span></span>  
  
### <a name="to-create-a-basic-wcf-service"></a><span data-ttu-id="fbee2-110">Temel bir WCF hizmeti oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="fbee2-110">To create a basic WCF service</span></span>  
  
1.  <span data-ttu-id="fbee2-111">İle işaretlenen bir arabirim ile temel bir WCF sözleşmesi tanımlayın. <xref:System.ServiceModel.ServiceContractAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="fbee2-111">Define a basic WCF service contract with an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="fbee2-112">Her işlemiyle işaretlemek <xref:System.ServiceModel.OperationContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="fbee2-112">Mark each operation with the <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="fbee2-113">Ayarladığınızdan emin olun <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="fbee2-113">Be sure to set the <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> property.</span></span>  
  
    ```  
    [ServiceContract(Namespace = "MyService")]  
    public interface ICalculator  
    {  
        [OperationContract]  
         // This operation returns the sum of d1 and d2.  
        double Add(double n1, double n2);  
  
        //Other operations omitted…  
  
    }  
    ```  
  
2.  <span data-ttu-id="fbee2-114">Uygulama `ICalculator` hizmet sözleşmesine bir `CalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="fbee2-114">Implement the `ICalculator` service contract with a `CalculatorService`.</span></span>  
  
    ```  
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
  
    //Other operations omitted…  
    ```  
  
3.  <span data-ttu-id="fbee2-115">Bir ad alanı için tanımlayın `ICalculator` ve `CalculatorService` bir ad alanı bloğunda kaydırma tarafından uygulamaları.</span><span class="sxs-lookup"><span data-stu-id="fbee2-115">Define a namespace for the `ICalculator` and `CalculatorService` implementations by wrapping them in a namespace block.</span></span>  
  
    ```  
    Namespace Microsoft.Ajax.Samples  
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
### <a name="to-create-an-aspnet-ajax-endpoint-for-the-service"></a><span data-ttu-id="fbee2-116">Hizmeti için bir ASP.NET AJAX uç noktası oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="fbee2-116">To create an ASP.NET AJAX endpoint for the service</span></span>  
  
1.  <span data-ttu-id="fbee2-117">Davranışı yapılandırmasını oluşturun ve belirtin [ \<enableWebScript >](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) hizmet uç noktalarına ASP.NET AJAX etkinleştirilmiş davranışı.</span><span class="sxs-lookup"><span data-stu-id="fbee2-117">Create a behavior configuration and specify the [\<enableWebScript>](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) behavior for ASP.NET AJAX-enabled endpoints of the service.</span></span>  
  
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
  
2.  <span data-ttu-id="fbee2-118">Kullanan hizmet için bir uç nokta oluşturma <xref:System.ServiceModel.WebHttpBinding> ve önceki adımda tanımlanan ASP.NET AJAX davranışı.</span><span class="sxs-lookup"><span data-stu-id="fbee2-118">Create an endpoint for the service that uses the <xref:System.ServiceModel.WebHttpBinding> and the ASP.NET AJAX behavior defined in the previous step.</span></span>  
  
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
  
### <a name="to-host-the-service-in-iis"></a><span data-ttu-id="fbee2-119">Ana bilgisayar hizmeti IIS</span><span class="sxs-lookup"><span data-stu-id="fbee2-119">To host the service in IIS</span></span>  
  
1.  <span data-ttu-id="fbee2-120">IIS hizmetinde barındırmak için uygulama .svc uzantısında hizmetiyle adlı yeni bir dosya oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fbee2-120">To host the service in IIS, create a new file named service with a .svc extension in the application.</span></span> <span data-ttu-id="fbee2-121">Uygun ekleyerek bu dosyayı düzenlemek [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) hizmet için yönerge bilgileri.</span><span class="sxs-lookup"><span data-stu-id="fbee2-121">Edit this file by adding the appropriate [@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive information for the service.</span></span> <span data-ttu-id="fbee2-122">Örneğin, hizmet dosyanın içeriği `CalculatorService` örnek aşağıdaki bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="fbee2-122">For example, the content in the service file for the `CalculatorService` sample contains the following information.</span></span>  
  
    ```  
    <%@ServiceHost   
    language=c#   
    Debug="true"   
    Service="Microsoft.Ajax.Samples.CalculatorService"  
    %>  
    ```  
  
2.  <span data-ttu-id="fbee2-123">IIS barındırma hakkında daha fazla bilgi için bkz: [nasıl yapılır: IIS'de WCF Hizmeti barındırma](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).</span><span class="sxs-lookup"><span data-stu-id="fbee2-123">For more information about hosting in IIS, see [How to: Host a WCF Service in IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).</span></span>  
  
### <a name="to-call-the-service"></a><span data-ttu-id="fbee2-124">Hizmeti çağırmak için</span><span class="sxs-lookup"><span data-stu-id="fbee2-124">To call the service</span></span>  
  
1.  <span data-ttu-id="fbee2-125">Hizmet kullanıma sunulmuştur ve service.svc/ için istek göndererek çağrılabilir uç nokta .svc dosyasıyla ilişkili boş bir adresindeki yapılandırıldığından\<işlemi > - Örneğin, service.svc/Add için `Add` işlemi.</span><span class="sxs-lookup"><span data-stu-id="fbee2-125">The endpoint is configured at an empty address relative to the .svc file, so the service is now available and can be invoked by sending requests to service.svc/\<operation> - for example, service.svc/Add for the `Add` operation.</span></span> <span data-ttu-id="fbee2-126">ASP.NET AJAX komut dosyası Manager denetim betikleri koleksiyona uç nokta URL'sini girerek kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fbee2-126">You can use it by entering the endpoint URL into the Scripts collection of the ASP.NET AJAX Script Manager control.</span></span> <span data-ttu-id="fbee2-127">Bir örnek için bkz: [AJAX hizmeti kullanarak HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span><span class="sxs-lookup"><span data-stu-id="fbee2-127">For an example, see the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbee2-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fbee2-128">See Also</span></span>  
 [<span data-ttu-id="fbee2-129">ASP.NET AJAX için WCF Hizmetleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="fbee2-129">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)  
 [<span data-ttu-id="fbee2-130">Nasıl yapılır: AJAX Etkinleştirilmiş ASP.NET Web Hizmetlerini WCF'ye Taşıma</span><span class="sxs-lookup"><span data-stu-id="fbee2-130">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
