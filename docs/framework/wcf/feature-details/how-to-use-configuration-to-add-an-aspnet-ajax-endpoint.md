---
title: "Nasıl yapılır: ASP.NET AJAX Uç Noktası Eklemek için Yapılandırma Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7cd0099e-dc3a-47e4-a38c-6e10f997f6ea
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4db4b105bc958a19dc803aa74dc9193e8a8a7edb
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-use-configuration-to-add-an-aspnet-ajax-endpoint"></a><span data-ttu-id="20cda-102">Nasıl yapılır: ASP.NET AJAX Uç Noktası Eklemek için Yapılandırma Kullanma</span><span class="sxs-lookup"><span data-stu-id="20cda-102">How to: Use Configuration to Add an ASP.NET AJAX Endpoint</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="20cda-103">bir ASP.NET AJAX etkinleştirilmiş uç nokta bir istemci Web sitesinde JavaScript'ten çağrılabilir kullanılabilir hale getirir bir hizmet oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="20cda-103"> allows you to create a service that makes an ASP.NET AJAX-enabled endpoint available that can be called from JavaScript on a client Web site.</span></span> <span data-ttu-id="20cda-104">Bu tür bir uç nokta oluşturmak için ya da bir yapılandırma dosyası tüm diğer olarak kullanabileceğiniz [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] uç noktaları veya tüm yapılandırma öğeleri gerektirmeyen bir yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="20cda-104">To create such an endpoint, you can either use a configuration file, as with all other [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] endpoints, or use a method that does not require any configuration elements.</span></span> <span data-ttu-id="20cda-105">Bu konuda yapılandırma yaklaşım gösterilir.</span><span class="sxs-lookup"><span data-stu-id="20cda-105">This topic demonstrates the configuration approach.</span></span>  
  
 <span data-ttu-id="20cda-106">Hizmet uç noktası, ASP.NET AJAX etkinleştirilmiş olmasını sağlayan yordamının parçası kullanmak için uç nokta yapılandırmayı içerir <xref:System.ServiceModel.WebHttpBinding> ve eklemek için [ \<enableWebScript >](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) uç noktası davranışı.</span><span class="sxs-lookup"><span data-stu-id="20cda-106">The part of the procedure that enables the service endpoint to become ASP.NET AJAX-enabled consists of configuring the endpoint to use the <xref:System.ServiceModel.WebHttpBinding> and to add the [\<enableWebScript>](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) endpoint behavior.</span></span> <span data-ttu-id="20cda-107">Uç nokta yapılandırdıktan sonra uygulama ve hizmet barındırmak için adımları tarafından kullanılan benzerdir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet.</span><span class="sxs-lookup"><span data-stu-id="20cda-107">After configuring the endpoint, the steps to implement and host the service are similar to those used by any [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="20cda-108">Çalışan bir örnek için bkz: [AJAX hizmeti kullanarak HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span><span class="sxs-lookup"><span data-stu-id="20cda-108">For a working example, see the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="20cda-109">Yapılandırma kullanmadan ASP.NET AJAX uç noktası yapılandırma hakkında [nasıl yapılır: ASP.NET AJAX uç nokta olmadan kullanarak Yapılandırması Ekle](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="20cda-109"> how to configure an ASP.NET AJAX endpoint without using configuration, see [How to: Add an ASP.NET AJAX Endpoint Without Using Configuration](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span></span>  
  
### <a name="to-create-a-basic-wcf-service"></a><span data-ttu-id="20cda-110">Temel bir WCF hizmeti oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="20cda-110">To create a basic WCF service</span></span>  
  
1.  <span data-ttu-id="20cda-111">Temel bir tanımlamak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet sözleşmesini bir arabirim ile işaretlenmiş <xref:System.ServiceModel.ServiceContractAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="20cda-111">Define a basic [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service contract with an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="20cda-112">Her işlemiyle işaretlemek <xref:System.ServiceModel.OperationContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="20cda-112">Mark each operation with the <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="20cda-113">Ayarladığınızdan emin olun <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="20cda-113">Be sure to set the <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> property.</span></span>  
  
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
  
2.  <span data-ttu-id="20cda-114">Uygulama `ICalculator` hizmet sözleşmesine bir `CalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="20cda-114">Implement the `ICalculator` service contract with a `CalculatorService`.</span></span>  
  
    ```  
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
  
    //Other operations omitted…  
    ```  
  
3.  <span data-ttu-id="20cda-115">Bir ad alanı için tanımlayın `ICalculator` ve `CalculatorService` bir ad alanı bloğunda kaydırma tarafından uygulamaları.</span><span class="sxs-lookup"><span data-stu-id="20cda-115">Define a namespace for the `ICalculator` and `CalculatorService` implementations by wrapping them in a namespace block.</span></span>  
  
    ```  
    Namespace Microsoft.Ajax.Samples  
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
### <a name="to-create-an-aspnet-ajax-endpoint-for-the-service"></a><span data-ttu-id="20cda-116">Hizmeti için bir ASP.NET AJAX uç noktası oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="20cda-116">To create an ASP.NET AJAX endpoint for the service</span></span>  
  
1.  <span data-ttu-id="20cda-117">Davranışı yapılandırmasını oluşturun ve belirtin [ \<enableWebScript >](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) hizmet uç noktalarına ASP.NET AJAX etkinleştirilmiş davranışı.</span><span class="sxs-lookup"><span data-stu-id="20cda-117">Create a behavior configuration and specify the [\<enableWebScript>](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) behavior for ASP.NET AJAX-enabled endpoints of the service.</span></span>  
  
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
  
2.  <span data-ttu-id="20cda-118">Kullanan hizmet için bir uç nokta oluşturma <xref:System.ServiceModel.WebHttpBinding> ve önceki adımda tanımlanan ASP.NET AJAX davranışı.</span><span class="sxs-lookup"><span data-stu-id="20cda-118">Create an endpoint for the service that uses the <xref:System.ServiceModel.WebHttpBinding> and the ASP.NET AJAX behavior defined in the previous step.</span></span>  
  
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
  
### <a name="to-host-the-service-in-iis"></a><span data-ttu-id="20cda-119">Ana bilgisayar hizmeti IIS</span><span class="sxs-lookup"><span data-stu-id="20cda-119">To host the service in IIS</span></span>  
  
1.  <span data-ttu-id="20cda-120">IIS hizmetinde barındırmak için uygulama .svc uzantısında hizmetiyle adlı yeni bir dosya oluşturun.</span><span class="sxs-lookup"><span data-stu-id="20cda-120">To host the service in IIS, create a new file named service with a .svc extension in the application.</span></span> <span data-ttu-id="20cda-121">Uygun ekleyerek bu dosyayı düzenlemek [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) hizmet için yönerge bilgileri.</span><span class="sxs-lookup"><span data-stu-id="20cda-121">Edit this file by adding the appropriate [@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive information for the service.</span></span> <span data-ttu-id="20cda-122">Örneğin, hizmet dosyanın içeriği `CalculatorService` örnek aşağıdaki bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="20cda-122">For example, the content in the service file for the `CalculatorService` sample contains the following information.</span></span>  
  
    ```  
    <%@ServiceHost   
    language=c#   
    Debug="true"   
    Service="Microsoft.Ajax.Samples.CalculatorService"  
    %>  
    ```  
  
2.  [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="20cda-123">IIS, barındırma bkz [nasıl yapılır: IIS'de WCF Hizmeti barındırma](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).</span><span class="sxs-lookup"><span data-stu-id="20cda-123"> hosting in IIS, see [How to: Host a WCF Service in IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).</span></span>  
  
### <a name="to-call-the-service"></a><span data-ttu-id="20cda-124">Hizmeti çağırmak için</span><span class="sxs-lookup"><span data-stu-id="20cda-124">To call the service</span></span>  
  
1.  <span data-ttu-id="20cda-125">Hizmet kullanıma sunulmuştur ve service.svc/ için istek göndererek çağrılabilir uç nokta .svc dosyasıyla ilişkili boş bir adresindeki yapılandırıldığından\<işlemi > - Örneğin, service.svc/Add için `Add` işlemi.</span><span class="sxs-lookup"><span data-stu-id="20cda-125">The endpoint is configured at an empty address relative to the .svc file, so the service is now available and can be invoked by sending requests to service.svc/\<operation> - for example, service.svc/Add for the `Add` operation.</span></span> <span data-ttu-id="20cda-126">ASP.NET AJAX komut dosyası Manager denetim betikleri koleksiyona uç nokta URL'sini girerek kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="20cda-126">You can use it by entering the endpoint URL into the Scripts collection of the ASP.NET AJAX Script Manager control.</span></span> <span data-ttu-id="20cda-127">Bir örnek için bkz: [AJAX hizmeti kullanarak HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span><span class="sxs-lookup"><span data-stu-id="20cda-127">For an example, see the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20cda-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="20cda-128">See Also</span></span>  
 [<span data-ttu-id="20cda-129">ASP.NET AJAX için WCF hizmetleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="20cda-129">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)  
 [<span data-ttu-id="20cda-130">Nasıl yapılır: AJAX etkinleştirilmiş ASP.NET Web hizmetlerini WCF'ye taşıma</span><span class="sxs-lookup"><span data-stu-id="20cda-130">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
