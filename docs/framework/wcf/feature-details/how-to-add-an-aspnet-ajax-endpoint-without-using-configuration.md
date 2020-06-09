---
title: 'Nasıl yapılır: Yapılandırma Kullanmadan ASP.NET AJAX Uç Noktası Ekleme'
ms.date: 03/30/2017
ms.assetid: b05c1742-8d0a-4673-9d71-725b18a3008e
ms.openlocfilehash: 9aab53d6457aa7848fd4acea6317a30da352cc98
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84579637"
---
# <a name="how-to-add-an-aspnet-ajax-endpoint-without-using-configuration"></a><span data-ttu-id="99e9c-102">Nasıl yapılır: Yapılandırma Kullanmadan ASP.NET AJAX Uç Noktası Ekleme</span><span class="sxs-lookup"><span data-stu-id="99e9c-102">How to: Add an ASP.NET AJAX Endpoint Without Using Configuration</span></span>
<span data-ttu-id="99e9c-103">Windows Communication Foundation (WCF), istemci Web sitesinde JavaScript 'ten çağrılabilen ASP.NET AJAX özellikli bir uç nokta sunan bir hizmet oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="99e9c-103">Windows Communication Foundation (WCF) allows you to create a service that exposes an ASP.NET AJAX-enabled endpoint that can be called from JavaScript on a client Web site.</span></span> <span data-ttu-id="99e9c-104">Böyle bir uç nokta oluşturmak için, diğer tüm WCF uç noktalarında olduğu gibi bir yapılandırma dosyası ya da herhangi bir yapılandırma öğesi gerektirmeyen bir yöntemi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="99e9c-104">To create such an endpoint, you can either use a configuration file, as with all other WCF endpoints, or use a method that does not require any configuration elements.</span></span> <span data-ttu-id="99e9c-105">Bu konuda ikinci yaklaşım gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="99e9c-105">This topic demonstrates the second approach.</span></span>  
  
 <span data-ttu-id="99e9c-106">ASP.NET AJAX uç noktalarıyla yapılandırma olmadan hizmetler oluşturmak için, hizmetler Internet Information Services (IIS) tarafından barındırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="99e9c-106">To create services with ASP.NET AJAX endpoints without configuration, the services must be hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="99e9c-107">Bu yaklaşımı kullanarak bir ASP.NET AJAX uç noktasını etkinleştirmek için <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> . svc dosyasındaki [ \@ ServiceHost](../../configure-apps/file-schema/wcf-directive/servicehost.md) yönergesinde Factory parametresi olarak belirtin.</span><span class="sxs-lookup"><span data-stu-id="99e9c-107">To activate an ASP.NET AJAX endpoint using this approach, specify the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> as the Factory parameter in the [\@ServiceHost](../../configure-apps/file-schema/wcf-directive/servicehost.md) directive in the .svc file.</span></span> <span data-ttu-id="99e9c-108">Bu özel fabrika, bir istemci Web sitesindeki JavaScript 'ten çağrılabilmesi için bir ASP.NET AJAX uç noktası otomatik olarak yapılandıran bileşendir.</span><span class="sxs-lookup"><span data-stu-id="99e9c-108">This custom factory is the component that automatically configures an ASP.NET AJAX endpoint so that it can be called from JavaScript on a client Web site.</span></span>  
  
 <span data-ttu-id="99e9c-109">Çalışan bir örnek için, [yapılandırma olmadan Ajax hizmetine](../samples/ajax-service-without-configuration.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="99e9c-109">For a working example, see the [AJAX Service Without Configuration](../samples/ajax-service-without-configuration.md).</span></span>  
  
 <span data-ttu-id="99e9c-110">Yapılandırma öğelerini kullanarak bir ASP.NET AJAX uç noktasının nasıl yapılandırılacağı hakkında bilgi için bkz. [nasıl yapılır: yapılandırma kullanma bir ASP.NET AJAX uç noktası eklemek için](how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md).</span><span class="sxs-lookup"><span data-stu-id="99e9c-110">For an outline of how to configure an ASP.NET AJAX endpoint using configuration elements, see [How to: Use Configuration to Add an ASP.NET AJAX Endpoint](how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md).</span></span>  
  
### <a name="to-create-a-basic-wcf-service"></a><span data-ttu-id="99e9c-111">Temel bir WCF hizmeti oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="99e9c-111">To create a basic WCF service</span></span>  
  
1. <span data-ttu-id="99e9c-112">Özniteliği ile işaretlenmiş bir arabirimle birlikte temel bir WCF hizmeti sözleşmesi tanımlayın <xref:System.ServiceModel.ServiceContractAttribute> .</span><span class="sxs-lookup"><span data-stu-id="99e9c-112">Define a basic WCF service contract with an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="99e9c-113">Her işlemi ile işaretleyin <xref:System.ServiceModel.OperationContractAttribute> .</span><span class="sxs-lookup"><span data-stu-id="99e9c-113">Mark each operation with the <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="99e9c-114">Özelliği ayarladığınızdan emin olun <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> .</span><span class="sxs-lookup"><span data-stu-id="99e9c-114">Be sure to set the <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> property.</span></span>  
  
    ```csharp  
    [ServiceContract(Namespace = "MyService")]]  
    public interface ICalculator  
    {  
        [OperationContract]  
        // This operation returns the sum of d1 and d2.  
        double Add(double n1, double n2);  
  
        //Other operations omitted…  
  
    }  
    ```  
  
2. <span data-ttu-id="99e9c-115">`ICalculator`Hizmet sözleşmesini bir ile uygulayın `CalculatorService` .</span><span class="sxs-lookup"><span data-stu-id="99e9c-115">Implement the `ICalculator` service contract with a `CalculatorService`.</span></span>  
  
    ```csharp  
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
  
    //Other operations omitted…  
    ```  
  
3. <span data-ttu-id="99e9c-116">Bir ad `ICalculator` `CalculatorService` alanı bloğunda sarmalayarak ve uygulamalar için bir ad alanı tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="99e9c-116">Define a namespace for the `ICalculator` and `CalculatorService` implementations by wrapping them in a namespace block.</span></span>  
  
    ```csharp  
    Namespace Microsoft.Ajax.Samples  
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
### <a name="to-host-the-service-in-internet-information-services-without-configuration"></a><span data-ttu-id="99e9c-117">Hizmeti yapılandırma olmadan Internet Information Services içinde barındırmak için</span><span class="sxs-lookup"><span data-stu-id="99e9c-117">To host the service in Internet Information Services without configuration</span></span>  
  
1. <span data-ttu-id="99e9c-118">Uygulamada. svc uzantısıyla yeni bir dosya adlı hizmet oluşturun.</span><span class="sxs-lookup"><span data-stu-id="99e9c-118">Create a new file named service with a .svc extension in the application.</span></span> <span data-ttu-id="99e9c-119">Hizmet için uygun [ \@ ServiceHost](../../configure-apps/file-schema/wcf-directive/servicehost.md) yönergesi bilgilerini ekleyerek bu dosyayı düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="99e9c-119">Edit this file by adding the appropriate [\@ServiceHost](../../configure-apps/file-schema/wcf-directive/servicehost.md) directive information for the service.</span></span> <span data-ttu-id="99e9c-120"><xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>ASP.NET AJAX uç noktasını otomatik olarak yapılandırmak için [ \@ ServiceHost](../../configure-apps/file-schema/wcf-directive/servicehost.md) yönergesinde kullanılacağını belirtin.</span><span class="sxs-lookup"><span data-stu-id="99e9c-120">Specify that the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is to be used in the [\@ServiceHost](../../configure-apps/file-schema/wcf-directive/servicehost.md) directive to automatically configure an ASP.NET AJAX endpoint.</span></span>  
  
    ```text
    <%@ServiceHost
        language=c#
        Debug="true"
        Service="Microsoft.Ajax.Samples.CalculatorService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
2. <span data-ttu-id="99e9c-121">Hizmeti derleyin ve istemciden çağırın.</span><span class="sxs-lookup"><span data-stu-id="99e9c-121">Build the service and call it from the client.</span></span> <span data-ttu-id="99e9c-122">Internet Information Services (IIS), çağrıldığında hizmeti etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="99e9c-122">Internet Information Services (IIS) activates the service when called.</span></span> <span data-ttu-id="99e9c-123">IIS 'de barındırma hakkında daha fazla bilgi için bkz. [nasıl yapılır: IIS 'de WCF hizmeti barındırma](how-to-host-a-wcf-service-in-iis.md).</span><span class="sxs-lookup"><span data-stu-id="99e9c-123">For more information about hosting in IIS, see [How to: Host a WCF Service in IIS](how-to-host-a-wcf-service-in-iis.md).</span></span>  
  
### <a name="to-call-the-service"></a><span data-ttu-id="99e9c-124">Hizmeti çağırmak için</span><span class="sxs-lookup"><span data-stu-id="99e9c-124">To call the service</span></span>  
  
1. <span data-ttu-id="99e9c-125">Uç nokta,. svc dosyasına göre boş bir adreste yapılandırılır, bu nedenle hizmet artık kullanılabilir ve hizmet. svc 'ye istek göndererek çağrılabilir. \<operation> Örneğin, işlem için Service. svc/Add. `Add`</span><span class="sxs-lookup"><span data-stu-id="99e9c-125">The endpoint is configured at an empty address relative to the .svc file, so the service is now available and can be invoked by sending requests to service.svc/\<operation> - for example, service.svc/Add for the `Add` operation.</span></span> <span data-ttu-id="99e9c-126">Bunu, ASP.NET AJAX betik Yöneticisi denetiminin betikler koleksiyonuna hizmet URL 'sini girerek kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="99e9c-126">You can use it by entering the service URL into the Scripts collection of the ASP.NET AJAX Script Manager control.</span></span> <span data-ttu-id="99e9c-127">Bir örnek için, [yapılandırma olmadan Ajax hizmetine](../samples/ajax-service-without-configuration.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="99e9c-127">For an example, see the [AJAX Service Without Configuration](../samples/ajax-service-without-configuration.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="99e9c-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="99e9c-128">Example</span></span>  
  
 <span data-ttu-id="99e9c-129">Otomatik olarak yapılandırılan uç nokta, temel URL 'ye göre boş bir adreste oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="99e9c-129">The automatically-configured endpoint is created at an empty address relative to the base URL.</span></span> <span data-ttu-id="99e9c-130">Bu yaklaşım ile de bir yapılandırma dosyası eklenebilir ve kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="99e9c-130">A configuration file can also be added and used with this approach.</span></span> <span data-ttu-id="99e9c-131">Yapılandırma dosyası uç nokta tanımları içeriyorsa, bu uç noktalar otomatik olarak yapılandırılmış uç noktaya eklenir.</span><span class="sxs-lookup"><span data-stu-id="99e9c-131">If the configuration file contains endpoint definitions, these endpoints are added to the automatically-configured endpoint.</span></span>  
  
 <span data-ttu-id="99e9c-132">Örneğin, Service. svc ' nı kullanır <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> ve hizmet dizini, <xref:System.ServiceModel.BasicHttpBinding> "SOAP" göreli adresinde öğesini kullanarak aynı hizmet için bir uç nokta tanımlayan bir Web. config dosyası içerir.</span><span class="sxs-lookup"><span data-stu-id="99e9c-132">For example, service.svc uses the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> and the service directory contains a Web.config file that defines an endpoint for the same service using the <xref:System.ServiceModel.BasicHttpBinding> at the "soap" relative address.</span></span> <span data-ttu-id="99e9c-133">Bu durumda hizmet iki uç nokta içerir: bir adet Service. svc (ASP.NET AJAX isteklerine yanıt verir) ve başka bir Service. svc/SOAP (SOAP isteklerine yanıt verir).</span><span class="sxs-lookup"><span data-stu-id="99e9c-133">In this case, the service contains two endpoints: one at service.svc (which responds to ASP.NET AJAX requests) and another at service.svc/soap (which responds to SOAP requests).</span></span>  
  
 <span data-ttu-id="99e9c-134">Yapılandırma dosyası boş bir göreli adreste bir uç nokta tanımlıyorsa ve <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> kullanılırsa, bir özel durum oluşturulur ve hizmet başlatılamaz.</span><span class="sxs-lookup"><span data-stu-id="99e9c-134">If the configuration file defines an endpoint at an empty relative address and the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is used, an exception is thrown and the service fails to start.</span></span>  
  
 <span data-ttu-id="99e9c-135">Otomatik olarak yapılandırılmış uç noktasındaki ayarları değiştirmek için yapılandırmayı kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="99e9c-135">You cannot use configuration to modify settings on the automatically-configured endpoint.</span></span> <span data-ttu-id="99e9c-136">Herhangi bir ayarın (örn. bir okuyucu kotası) değiştirilmesi gerekiyorsa, <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> . svc dosyasından ' yi kaldırarak ve uç nokta için bir yapılandırma girişi oluşturarak yapılandırma-ücretsiz yaklaşımını kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="99e9c-136">If any setting (such as a reader quota) must be modified, you must not use the configuration-free approach by removing the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> from the .svc file and creating a configuration entry for the endpoint.</span></span>  
  
 <span data-ttu-id="99e9c-137">Hizmetiniz ASP.NET uyumluluk moduna gerektiriyorsa (örneğin, <xref:System.Web.HttpContext> sınıfı veya ASP.NET yetkilendirme mekanizmalarını kullanıyorsa), bu modu açmak için bir yapılandırma dosyası gerekir.</span><span class="sxs-lookup"><span data-stu-id="99e9c-137">If your service requires ASP.NET Compatibility Mode - for example, if it uses the <xref:System.Web.HttpContext> class or ASP.NET authorization mechanisms - a configuration file is still required to turn on this mode.</span></span> <span data-ttu-id="99e9c-138">Gerekli yapılandırma öğesi, [\<serviceHostingEnvironment>](../../configure-apps/file-schema/wcf/servicehostingenvironment.md) aşağıdaki şekilde eklenmesi gereken öğesidir.</span><span class="sxs-lookup"><span data-stu-id="99e9c-138">The configuration element required is the [\<serviceHostingEnvironment>](../../configure-apps/file-schema/wcf/servicehostingenvironment.md) element, which must be added as follows.</span></span>  
  
 `<system.serviceModel>`  
  
 `<serviceHostingEnvironment aspNetCompatibilityEnabled="true" /> </system.serviceModel>`  
  
 <span data-ttu-id="99e9c-139">Daha fazla bilgi için bkz. [WCF Hizmetleri ve ASP.net](wcf-services-and-aspnet.md) konusu.</span><span class="sxs-lookup"><span data-stu-id="99e9c-139">For more information, see the [WCF Services and ASP.NET](wcf-services-and-aspnet.md) topic.</span></span>  
  
 <span data-ttu-id="99e9c-140"><xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>Sınıfı, türetilmiş bir sınıftır <xref:System.ServiceModel.Activation.ServiceHostFactory> .</span><span class="sxs-lookup"><span data-stu-id="99e9c-140">The <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> class is a derived class of <xref:System.ServiceModel.Activation.ServiceHostFactory>.</span></span> <span data-ttu-id="99e9c-141">Hizmet ana bilgisayarı fabrikası mekanizmasına ilişkin ayrıntılı bir açıklama için bkz. [ServiceHostFactory kullanarak barındırma genişletme](../extending/extending-hosting-using-servicehostfactory.md) konusu.</span><span class="sxs-lookup"><span data-stu-id="99e9c-141">For a detailed explanation of the service host factory mechanism, see the [Extending Hosting Using ServiceHostFactory](../extending/extending-hosting-using-servicehostfactory.md) topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99e9c-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="99e9c-142">See also</span></span>

- [<span data-ttu-id="99e9c-143">ASP.NET AJAX için WCF Hizmetleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="99e9c-143">Creating WCF Services for ASP.NET AJAX</span></span>](creating-wcf-services-for-aspnet-ajax.md)
- [<span data-ttu-id="99e9c-144">Nasıl yapılır: AJAX Etkinleştirilmiş ASP.NET Web Hizmetlerini WCF'ye Taşıma</span><span class="sxs-lookup"><span data-stu-id="99e9c-144">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
