---
title: 'Nasıl yapılır: ASP.NET AJAX Uç Noktası Eklemek için Yapılandırma Kullanma'
ms.date: 03/30/2017
ms.assetid: 7cd0099e-dc3a-47e4-a38c-6e10f997f6ea
ms.openlocfilehash: db5085d01dbed841109ac46fe4e8b2a0143352e3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59337623"
---
# <a name="how-to-use-configuration-to-add-an-aspnet-ajax-endpoint"></a><span data-ttu-id="10854-102">Nasıl yapılır: ASP.NET AJAX Uç Noktası Eklemek için Yapılandırma Kullanma</span><span class="sxs-lookup"><span data-stu-id="10854-102">How to: Use Configuration to Add an ASP.NET AJAX Endpoint</span></span>
<span data-ttu-id="10854-103">Windows Communication Foundation (WCF), bir ASP.NET AJAX etkinleştirilmiş uç nokta, istemci Web sitesinde JavaScript'ten çağrılabilir kullanılabilir bir hizmet oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="10854-103">Windows Communication Foundation (WCF) allows you to create a service that makes an ASP.NET AJAX-enabled endpoint available that can be called from JavaScript on a client Web site.</span></span> <span data-ttu-id="10854-104">Böyle bir uç nokta oluşturmak için bir yapılandırma dosyası ile tüm diğer Windows Communication Foundation (WCF) uç noktalar olarak kullanabilir veya yapılandırma öğeleri gerektirmeyen bir yöntem kullanın.</span><span class="sxs-lookup"><span data-stu-id="10854-104">To create such an endpoint, you can either use a configuration file, as with all other Windows Communication Foundation (WCF) endpoints, or use a method that does not require any configuration elements.</span></span> <span data-ttu-id="10854-105">Bu konuda, yapılandırma yaklaşım gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="10854-105">This topic demonstrates the configuration approach.</span></span>  
  
 <span data-ttu-id="10854-106">Hizmet uç noktası, ASP.NET AJAX etkinleştirilmiş olmasını sağlayan yordamının parçası kullanılacak uç nokta yapılandırmayı içerir <xref:System.ServiceModel.WebHttpBinding> eklenecek ve [ \<enableWebScript >](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) uç nokta davranışı.</span><span class="sxs-lookup"><span data-stu-id="10854-106">The part of the procedure that enables the service endpoint to become ASP.NET AJAX-enabled consists of configuring the endpoint to use the <xref:System.ServiceModel.WebHttpBinding> and to add the [\<enableWebScript>](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) endpoint behavior.</span></span> <span data-ttu-id="10854-107">Uç noktası yapılandırıldıktan sonra uygulama ve hizmeti barındırmak için adımları herhangi bir WCF hizmeti tarafından kullanılan benzerdir.</span><span class="sxs-lookup"><span data-stu-id="10854-107">After configuring the endpoint, the steps to implement and host the service are similar to those used by any WCF service.</span></span> <span data-ttu-id="10854-108">Çalışan bir örnek için bkz. [hizmet HTTP POST kullanan AJAX](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span><span class="sxs-lookup"><span data-stu-id="10854-108">For a working example, see the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span></span>  
  
 <span data-ttu-id="10854-109">Yapılandırma kullanmadan ASP.NET AJAX uç nokta yapılandırma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Yapılandırma kullanmadan ASP.NET AJAX uç noktası ekleme](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="10854-109">For more information about how to configure an ASP.NET AJAX endpoint without using configuration, see [How to: Add an ASP.NET AJAX Endpoint Without Using Configuration](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span></span>  
  
### <a name="to-create-a-basic-wcf-service"></a><span data-ttu-id="10854-110">Temel bir WCF hizmeti oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="10854-110">To create a basic WCF service</span></span>  
  
1. <span data-ttu-id="10854-111">İle işaretlenen arabirim ile temel bir WCF sözleşmesi tanımlayın. <xref:System.ServiceModel.ServiceContractAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="10854-111">Define a basic WCF service contract with an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="10854-112">Her işlemi ile işaretle <xref:System.ServiceModel.OperationContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="10854-112">Mark each operation with the <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="10854-113">Ayarladığınızdan emin olun <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="10854-113">Be sure to set the <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> property.</span></span>  
  
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
  
2. <span data-ttu-id="10854-114">Uygulama `ICalculator` hizmet söyleşmesi bir `CalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="10854-114">Implement the `ICalculator` service contract with a `CalculatorService`.</span></span>  
  
    ```  
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
  
    //Other operations omitted…  
    ```  
  
3. <span data-ttu-id="10854-115">Tanımlamak için bir ad alanı `ICalculator` ve `CalculatorService` tarafından bir ad alanı bloğunda kaydırmalı uygulamaları.</span><span class="sxs-lookup"><span data-stu-id="10854-115">Define a namespace for the `ICalculator` and `CalculatorService` implementations by wrapping them in a namespace block.</span></span>  
  
    ```  
    Namespace Microsoft.Ajax.Samples  
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
### <a name="to-create-an-aspnet-ajax-endpoint-for-the-service"></a><span data-ttu-id="10854-116">Hizmet için bir ASP.NET AJAX uç noktası oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="10854-116">To create an ASP.NET AJAX endpoint for the service</span></span>  
  
1. <span data-ttu-id="10854-117">Davranışı yapılandırmasını oluşturun ve belirtin [ \<enableWebScript >](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) ASP.NET AJAX etkinleştirilmiş uç hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="10854-117">Create a behavior configuration and specify the [\<enableWebScript>](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) behavior for ASP.NET AJAX-enabled endpoints of the service.</span></span>  
  
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
  
2. <span data-ttu-id="10854-118">Kullanan hizmet için bir uç nokta oluşturma <xref:System.ServiceModel.WebHttpBinding> ve önceki adımda tanımlanan ASP.NET AJAX davranışı.</span><span class="sxs-lookup"><span data-stu-id="10854-118">Create an endpoint for the service that uses the <xref:System.ServiceModel.WebHttpBinding> and the ASP.NET AJAX behavior defined in the previous step.</span></span>  
  
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
  
### <a name="to-host-the-service-in-iis"></a><span data-ttu-id="10854-119">IIS hizmeti barındırmak için</span><span class="sxs-lookup"><span data-stu-id="10854-119">To host the service in IIS</span></span>  
  
1. <span data-ttu-id="10854-120">IIS hizmeti barındırmak için uygulamada .svc uzantılı hizmeti adlı yeni bir dosya oluşturun.</span><span class="sxs-lookup"><span data-stu-id="10854-120">To host the service in IIS, create a new file named service with a .svc extension in the application.</span></span> <span data-ttu-id="10854-121">Uygun ekleyerek bu dosyayı Düzenle [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) hizmeti yönerge bilgi.</span><span class="sxs-lookup"><span data-stu-id="10854-121">Edit this file by adding the appropriate [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive information for the service.</span></span> <span data-ttu-id="10854-122">Örneğin, hizmet dosyanın içeriği `CalculatorService` örnek, aşağıdaki bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="10854-122">For example, the content in the service file for the `CalculatorService` sample contains the following information.</span></span>  
  
    ```  
    <%@ServiceHost   
    language=c#   
    Debug="true"   
    Service="Microsoft.Ajax.Samples.CalculatorService"  
    %>  
    ```  
  
2. <span data-ttu-id="10854-123">IIS'de barındırma hakkında daha fazla bilgi için bkz. [nasıl yapılır: IIS'de WCF Hizmeti barındırma](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).</span><span class="sxs-lookup"><span data-stu-id="10854-123">For more information about hosting in IIS, see [How to: Host a WCF Service in IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).</span></span>  
  
### <a name="to-call-the-service"></a><span data-ttu-id="10854-124">Hizmeti çağırmak için</span><span class="sxs-lookup"><span data-stu-id="10854-124">To call the service</span></span>  
  
1. <span data-ttu-id="10854-125">Hizmeti kullanıma sunuldu ve service.svc/ için istek göndererek çağrılabilir uç nokta boş bir adresten .svc dosyanın göreli yapılandırılır\<işlemi > - Örneğin, için service.svc/Add `Add` işlemi.</span><span class="sxs-lookup"><span data-stu-id="10854-125">The endpoint is configured at an empty address relative to the .svc file, so the service is now available and can be invoked by sending requests to service.svc/\<operation> - for example, service.svc/Add for the `Add` operation.</span></span> <span data-ttu-id="10854-126">ASP.NET AJAX komut dosyası Manager denetim betikleri koleksiyona uç nokta URL'sini girerek kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="10854-126">You can use it by entering the endpoint URL into the Scripts collection of the ASP.NET AJAX Script Manager control.</span></span> <span data-ttu-id="10854-127">Bir örnek için bkz. [hizmet HTTP POST kullanan AJAX](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span><span class="sxs-lookup"><span data-stu-id="10854-127">For an example, see the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10854-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="10854-128">See also</span></span>

- [<span data-ttu-id="10854-129">ASP.NET AJAX için WCF Hizmetleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="10854-129">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)
- [<span data-ttu-id="10854-130">Nasıl yapılır: AJAX etkinleştirilmiş ASP.NET Web hizmetlerini WCF'ye taşıma</span><span class="sxs-lookup"><span data-stu-id="10854-130">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
