---
title: 'Nasıl yapılır: ASP.NET AJAX Uç Noktası Eklemek için Yapılandırma Kullanma'
ms.date: 03/30/2017
ms.assetid: 7cd0099e-dc3a-47e4-a38c-6e10f997f6ea
ms.openlocfilehash: 5314bb000371ee2d3eef2576e1edfa455aa65b90
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184829"
---
# <a name="how-to-use-configuration-to-add-an-aspnet-ajax-endpoint"></a><span data-ttu-id="3327a-102">Nasıl yapılır: ASP.NET AJAX Uç Noktası Eklemek için Yapılandırma Kullanma</span><span class="sxs-lookup"><span data-stu-id="3327a-102">How to: Use Configuration to Add an ASP.NET AJAX Endpoint</span></span>
<span data-ttu-id="3327a-103">Windows Communication Foundation (WCF), bir istemci Web sitesinde JavaScript'ten çağrılabilen ASP.NET AJAX özellikli bitiş noktası nı kullanıma sunabilecek bir hizmet oluşturmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="3327a-103">Windows Communication Foundation (WCF) allows you to create a service that makes an ASP.NET AJAX-enabled endpoint available that can be called from JavaScript on a client Web site.</span></span> <span data-ttu-id="3327a-104">Böyle bir bitiş noktası oluşturmak için, diğer tüm Windows Communication Foundation (WCF) uç noktalarında olduğu gibi bir yapılandırma dosyası kullanabilir veya yapılandırma öğesi gerektirmeyen bir yöntem kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3327a-104">To create such an endpoint, you can either use a configuration file, as with all other Windows Communication Foundation (WCF) endpoints, or use a method that does not require any configuration elements.</span></span> <span data-ttu-id="3327a-105">Bu konu yapılandırma yaklaşımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3327a-105">This topic demonstrates the configuration approach.</span></span>  
  
 <span data-ttu-id="3327a-106">Yordamın hizmet bitiş noktasının AJAX'ASP.NET olmasını sağlayan bölümü, bitiş noktasını kullanmak <xref:System.ServiceModel.WebHttpBinding> ve [ \<etkinleştirilen WebScript>](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) bitiş noktası davranışını eklemek için yapılandırmaktan oluşur.</span><span class="sxs-lookup"><span data-stu-id="3327a-106">The part of the procedure that enables the service endpoint to become ASP.NET AJAX-enabled consists of configuring the endpoint to use the <xref:System.ServiceModel.WebHttpBinding> and to add the [\<enableWebScript>](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) endpoint behavior.</span></span> <span data-ttu-id="3327a-107">Bitiş noktasını yapılandırdıktan sonra, hizmeti uygulamak ve barındırma adımları herhangi bir WCF hizmeti tarafından kullanılanadımlara benzer.</span><span class="sxs-lookup"><span data-stu-id="3327a-107">After configuring the endpoint, the steps to implement and host the service are similar to those used by any WCF service.</span></span> <span data-ttu-id="3327a-108">Çalışan bir örnek için, [HTTP POST'u kullanarak AJAX Hizmeti'ne](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="3327a-108">For a working example, see the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span></span>  
  
 <span data-ttu-id="3327a-109">Yapılandırmayı kullanmadan ASP.NET bir AJAX bitiş noktasının nasıl yapılandırılabildiğini hakkında daha fazla bilgi için bkz [ASP.NET.](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="3327a-109">For more information about how to configure an ASP.NET AJAX endpoint without using configuration, see [How to: Add an ASP.NET AJAX Endpoint Without Using Configuration](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span></span>  
  
## <a name="to-create-a-basic-wcf-service"></a><span data-ttu-id="3327a-110">Temel bir WCF hizmeti oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="3327a-110">To create a basic WCF service</span></span>  
  
1. <span data-ttu-id="3327a-111">Öznitelik ile işaretlenmiş bir arabirim ile <xref:System.ServiceModel.ServiceContractAttribute> temel bir WCF hizmet sözleşmesi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="3327a-111">Define a basic WCF service contract with an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="3327a-112">Her işlemi <xref:System.ServiceModel.OperationContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="3327a-112">Mark each operation with the <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="3327a-113"><xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> Özelliği ayarladıklı.</span><span class="sxs-lookup"><span data-stu-id="3327a-113">Be sure to set the <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> property.</span></span>  
  
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
  
2. <span data-ttu-id="3327a-114">Bir `ICalculator` `CalculatorService`ile hizmet sözleşmesi uygulayın.</span><span class="sxs-lookup"><span data-stu-id="3327a-114">Implement the `ICalculator` service contract with a `CalculatorService`.</span></span>  
  
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
  
3. <span data-ttu-id="3327a-115">Ad alanı bloğuna `ICalculator` `CalculatorService` sararak ve uygulamalar için bir ad alanı tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="3327a-115">Define a namespace for the `ICalculator` and `CalculatorService` implementations by wrapping them in a namespace block.</span></span>  
  
    ```csharp
    namespace Microsoft.Ajax.Samples
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
## <a name="to-create-an-aspnet-ajax-endpoint-for-the-service"></a><span data-ttu-id="3327a-116">Hizmet için ASP.NET bir AJAX bitiş noktası oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="3327a-116">To create an ASP.NET AJAX endpoint for the service</span></span>  
  
1. <span data-ttu-id="3327a-117">Bir davranış yapılandırması [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) oluşturun ve hizmetin AJAX özellikli ASP.NET uç noktaları için etkinleştirmeWebScript>davranışını belirtin.</span><span class="sxs-lookup"><span data-stu-id="3327a-117">Create a behavior configuration and specify the [\<enableWebScript>](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) behavior for ASP.NET AJAX-enabled endpoints of the service.</span></span>  
  
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
  
2. <span data-ttu-id="3327a-118">Önceki adımda tanımlanan ve ASP.NET <xref:System.ServiceModel.WebHttpBinding> AJAX davranışını kullanan hizmet için bir bitiş noktası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3327a-118">Create an endpoint for the service that uses the <xref:System.ServiceModel.WebHttpBinding> and the ASP.NET AJAX behavior defined in the previous step.</span></span>  
  
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
  
## <a name="to-host-the-service-in-iis"></a><span data-ttu-id="3327a-119">Hizmeti IIS'de barındırmak için</span><span class="sxs-lookup"><span data-stu-id="3327a-119">To host the service in IIS</span></span>  
  
1. <span data-ttu-id="3327a-120">Hizmeti IIS'de barındırmak için, uygulamada .svc uzantısı bulunan hizmet adlı yeni bir dosya oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3327a-120">To host the service in IIS, create a new file named service with a .svc extension in the application.</span></span> <span data-ttu-id="3327a-121">Hizmet için uygun [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) yönergesi bilgilerini ekleyerek bu dosyayı düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="3327a-121">Edit this file by adding the appropriate [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive information for the service.</span></span> <span data-ttu-id="3327a-122">Örneğin, `CalculatorService` örnek için hizmet dosyasındaki içerik aşağıdaki bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="3327a-122">For example, the content in the service file for the `CalculatorService` sample contains the following information.</span></span>  
  
    ```
    <%@ServiceHost
    language=c#
    Debug="true"
    Service="Microsoft.Ajax.Samples.CalculatorService"  
    %>  
    ```  
  
2. <span data-ttu-id="3327a-123">IIS'de barındırma hakkında daha fazla bilgi için [bkz.](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)</span><span class="sxs-lookup"><span data-stu-id="3327a-123">For more information about hosting in IIS, see [How to: Host a WCF Service in IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).</span></span>  
  
## <a name="to-call-the-service"></a><span data-ttu-id="3327a-124">Hizmeti aramak için</span><span class="sxs-lookup"><span data-stu-id="3327a-124">To call the service</span></span>  
  
1. <span data-ttu-id="3327a-125">Bitiş noktası .svc dosyasına göre boş bir adreste yapılandırılır, bu nedenle hizmet artık kullanılabilir ve service.svc/\<operation> isteklerigönderilerek çağrılabilir - örneğin, service.svc/Add `Add` operasyon için.</span><span class="sxs-lookup"><span data-stu-id="3327a-125">The endpoint is configured at an empty address relative to the .svc file, so the service is now available and can be invoked by sending requests to service.svc/\<operation> - for example, service.svc/Add for the `Add` operation.</span></span> <span data-ttu-id="3327a-126">ASP.NET AJAX Script Manager denetiminin Komut Dosyaları koleksiyonuna bitiş noktası URL'sini girerek kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3327a-126">You can use it by entering the endpoint URL into the Scripts collection of the ASP.NET AJAX Script Manager control.</span></span> <span data-ttu-id="3327a-127">Örneğin, [HTTP POST'u kullanarak AJAX Hizmeti'ne](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="3327a-127">For an example, see the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3327a-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3327a-128">See also</span></span>

- [<span data-ttu-id="3327a-129">ASP.NET AJAX için WCF Hizmetleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="3327a-129">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)
- [<span data-ttu-id="3327a-130">Nasıl yapılır: AJAX Etkinleştirilmiş ASP.NET Web Hizmetlerini WCF'ye Taşıma</span><span class="sxs-lookup"><span data-stu-id="3327a-130">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
