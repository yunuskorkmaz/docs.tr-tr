---
title: 'Nasıl yapılır: Yapılandırma Kullanmadan ASP.NET AJAX Uç Noktası Ekleme'
ms.date: 03/30/2017
ms.assetid: b05c1742-8d0a-4673-9d71-725b18a3008e
ms.openlocfilehash: cc3cca2ed703c4329b3da7c6fde286c341459fa8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33496132"
---
# <a name="how-to-add-an-aspnet-ajax-endpoint-without-using-configuration"></a><span data-ttu-id="27f5e-102">Nasıl yapılır: Yapılandırma Kullanmadan ASP.NET AJAX Uç Noktası Ekleme</span><span class="sxs-lookup"><span data-stu-id="27f5e-102">How to: Add an ASP.NET AJAX Endpoint Without Using Configuration</span></span>
<span data-ttu-id="27f5e-103">Windows Communication Foundation (WCF) JavaScript'ten bir istemci Web sitesinde çağrılabilen bir ASP.NET AJAX etkin bir uç nokta kullanıma sunan bir hizmet oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="27f5e-103">Windows Communication Foundation (WCF) allows you to create a service that exposes an ASP.NET AJAX-enabled endpoint that can be called from JavaScript on a client Web site.</span></span> <span data-ttu-id="27f5e-104">Bu tür bir uç nokta oluşturmak için tüm diğer WCF uç noktaları gibi bir yapılandırma dosyası kullanın veya tüm yapılandırma öğeleri gerektirmeyen bir yöntemi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="27f5e-104">To create such an endpoint, you can either use a configuration file, as with all other WCF endpoints, or use a method that does not require any configuration elements.</span></span> <span data-ttu-id="27f5e-105">Bu konuda, ikinci bir yaklaşım gösterilir.</span><span class="sxs-lookup"><span data-stu-id="27f5e-105">This topic demonstrates the second approach.</span></span>  
  
 <span data-ttu-id="27f5e-106">ASP.NET AJAX uç noktaları yapılandırma olmadan hizmetleri oluşturmak için hizmetler Internet Information Services (IIS) tarafından barındırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="27f5e-106">To create services with ASP.NET AJAX endpoints without configuration, the services must be hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="27f5e-107">Bu yaklaşımı kullanarak bir ASP.NET AJAX uç noktası etkinleştirmeyi belirtin <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> Fabrika parametresi olarak [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) .svc dosyasındaki yönergesi.</span><span class="sxs-lookup"><span data-stu-id="27f5e-107">To activate an ASP.NET AJAX endpoint using this approach, specify the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> as the Factory parameter in the [@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive in the .svc file.</span></span> <span data-ttu-id="27f5e-108">Bu özel fabrika ASP.NET AJAX uç noktası otomatik olarak yapılandırır ve böylece istemci Web sitesinde JavaScript'ten çağrılabilir bileşendir.</span><span class="sxs-lookup"><span data-stu-id="27f5e-108">This custom factory is the component that automatically configures an ASP.NET AJAX endpoint so that it can be called from JavaScript on a client Web site.</span></span>  
  
 <span data-ttu-id="27f5e-109">Çalışan bir örnek için bkz: [olmadan AJAX Hizmeti Yapılandırması](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="27f5e-109">For a working example, see the [AJAX Service Without Configuration](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).</span></span>  
  
 <span data-ttu-id="27f5e-110">Yapılandırma öğeleri kullanarak bir ASP.NET AJAX uç noktası yapılandırmak nasıl ana hattı için bkz: [nasıl yapılır: ASP.NET AJAX uç noktası eklemek için yapılandırma kullan](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md).</span><span class="sxs-lookup"><span data-stu-id="27f5e-110">For an outline of how to configure an ASP.NET AJAX endpoint using configuration elements, see [How to: Use Configuration to Add an ASP.NET AJAX Endpoint](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md).</span></span>  
  
### <a name="to-create-a-basic-wcf-service"></a><span data-ttu-id="27f5e-111">Temel bir WCF hizmeti oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="27f5e-111">To create a basic WCF service</span></span>  
  
1.  <span data-ttu-id="27f5e-112">İle işaretlenen bir arabirim ile temel bir WCF sözleşmesi tanımlayın. <xref:System.ServiceModel.ServiceContractAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="27f5e-112">Define a basic WCF service contract with an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="27f5e-113">Her işlemiyle işaretlemek <xref:System.ServiceModel.OperationContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="27f5e-113">Mark each operation with the <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="27f5e-114">Ayarladığınızdan emin olun <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="27f5e-114">Be sure to set the <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> property.</span></span>  
  
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
  
2.  <span data-ttu-id="27f5e-115">Uygulama `ICalculator` hizmet sözleşmesine bir `CalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="27f5e-115">Implement the `ICalculator` service contract with a `CalculatorService`.</span></span>  
  
    ```csharp  
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
  
    //Other operations omitted…  
    ```  
  
3.  <span data-ttu-id="27f5e-116">Bir ad alanı için tanımlayın `ICalculator` ve `CalculatorService` bir ad alanı bloğunda kaydırma tarafından uygulamaları.</span><span class="sxs-lookup"><span data-stu-id="27f5e-116">Define a namespace for the `ICalculator` and `CalculatorService` implementations by wrapping them in a namespace block.</span></span>  
  
    ```csharp  
    Namespace Microsoft.Ajax.Samples  
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
### <a name="to-host-the-service-in-internet-information-services-without-configuration"></a><span data-ttu-id="27f5e-117">Internet Information Services hizmeti yapılandırma olmadan barındırmak için</span><span class="sxs-lookup"><span data-stu-id="27f5e-117">To host the service in Internet Information Services without configuration</span></span>  
  
1.  <span data-ttu-id="27f5e-118">Hizmet uygulaması .svc uzantısıyla adlı yeni bir dosya oluşturun.</span><span class="sxs-lookup"><span data-stu-id="27f5e-118">Create a new file named service with a .svc extension in the application.</span></span> <span data-ttu-id="27f5e-119">Uygun ekleyerek bu dosyayı düzenlemek [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) hizmet için yönerge bilgileri.</span><span class="sxs-lookup"><span data-stu-id="27f5e-119">Edit this file by adding the appropriate [@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive information for the service.</span></span> <span data-ttu-id="27f5e-120">Belirtmek <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> kullanılacak olan [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) yönergesi ASP.NET AJAX uç noktası otomatik olarak yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="27f5e-120">Specify that the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is to be used in the [@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive to automatically configure an ASP.NET AJAX endpoint.</span></span>  
  
    ```  
    <%@ServiceHost   
        language=c#   
        Debug="true"   
        Service="Microsoft.Ajax.Samples.CalculatorService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
2.  <span data-ttu-id="27f5e-121">Yapı Hizmeti ve istemciden çağırın.</span><span class="sxs-lookup"><span data-stu-id="27f5e-121">Build the service and call it from the client.</span></span> <span data-ttu-id="27f5e-122">Internet Information Services (IIS) çağrıldığında hizmetini etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="27f5e-122">Internet Information Services (IIS) activates the service when called.</span></span> <span data-ttu-id="27f5e-123">IIS barındırma hakkında daha fazla bilgi için bkz: [nasıl yapılır: IIS'de WCF Hizmeti barındırma](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).</span><span class="sxs-lookup"><span data-stu-id="27f5e-123">For more information about hosting in IIS, see [How to: Host a WCF Service in IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).</span></span>  
  
### <a name="to-call-the-service"></a><span data-ttu-id="27f5e-124">Hizmeti çağırmak için</span><span class="sxs-lookup"><span data-stu-id="27f5e-124">To call the service</span></span>  
  
1.  <span data-ttu-id="27f5e-125">Hizmet kullanıma sunulmuştur ve service.svc/ için istek göndererek çağrılabilir uç nokta .svc dosyasıyla ilişkili boş bir adresindeki yapılandırıldığından\<işlemi > - Örneğin, service.svc/Add için `Add` işlemi.</span><span class="sxs-lookup"><span data-stu-id="27f5e-125">The endpoint is configured at an empty address relative to the .svc file, so the service is now available and can be invoked by sending requests to service.svc/\<operation> - for example, service.svc/Add for the `Add` operation.</span></span> <span data-ttu-id="27f5e-126">Hizmet URL'si ASP.NET AJAX komut dosyası Manager denetim betikleri koleksiyonuna girerek kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="27f5e-126">You can use it by entering the service URL into the Scripts collection of the ASP.NET AJAX Script Manager control.</span></span> <span data-ttu-id="27f5e-127">Bir örnek için bkz: [olmadan AJAX Hizmeti Yapılandırması](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="27f5e-127">For an example, see the [AJAX Service Without Configuration](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="27f5e-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="27f5e-128">Example</span></span>  
  
 <span data-ttu-id="27f5e-129">Temel URL göreli boş bir adresindeki otomatik olarak yapılandırılan uç noktası oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="27f5e-129">The automatically-configured endpoint is created at an empty address relative to the base URL.</span></span> <span data-ttu-id="27f5e-130">Bir yapılandırma dosyası da eklenir ve Bu yaklaşımda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="27f5e-130">A configuration file can also be added and used with this approach.</span></span> <span data-ttu-id="27f5e-131">Yapılandırma dosyası uç nokta tanımları içeriyorsa, bu uç noktaları otomatik olarak yapılandırılan uç noktası eklenir.</span><span class="sxs-lookup"><span data-stu-id="27f5e-131">If the configuration file contains endpoint definitions, these endpoints are added to the automatically-configured endpoint.</span></span>  
  
 <span data-ttu-id="27f5e-132">Örneğin, service.svc kullanır <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> ve hizmeti dizini kullanarak aynı hizmet için bir uç nokta tanımlayan bir Web.config dosyası içeren <xref:System.ServiceModel.BasicHttpBinding> "soap" göreli adresindeki.</span><span class="sxs-lookup"><span data-stu-id="27f5e-132">For example, service.svc uses the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> and the service directory contains a Web.config file that defines an endpoint for the same service using the <xref:System.ServiceModel.BasicHttpBinding> at the "soap" relative address.</span></span> <span data-ttu-id="27f5e-133">Bu durumda, iki uç nokta hizmet içerir: tek (, ASP.NET AJAX isteklerine yanıt verir) service.svc ve başka bir (hangi SOAP isteklerine yanıt verir) service.svc/soap.</span><span class="sxs-lookup"><span data-stu-id="27f5e-133">In this case, the service contains two endpoints: one at service.svc (which responds to ASP.NET AJAX requests) and another at service.svc/soap (which responds to SOAP requests).</span></span>  
  
 <span data-ttu-id="27f5e-134">Yapılandırma dosyası boş bir göreli adresinde bir uç nokta tanımlıyorsa ve <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> olduğu kullanıldığında, bir özel durum ve hizmeti başlatılamıyor.</span><span class="sxs-lookup"><span data-stu-id="27f5e-134">If the configuration file defines an endpoint at an empty relative address and the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is used, an exception is thrown and the service fails to start.</span></span>  
  
 <span data-ttu-id="27f5e-135">Otomatik olarak yapılandırılan uç noktası ayarlarını değiştirmek için yapılandırma kullanamaz.</span><span class="sxs-lookup"><span data-stu-id="27f5e-135">You cannot use configuration to modify settings on the automatically-configured endpoint.</span></span> <span data-ttu-id="27f5e-136">Herhangi bir ayarı (örneğin, bir okuyucu kota) olmalıdır, değiştirilebilir, yapılandırma serbest yaklaşım kaldırarak kullanmamalısınız <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> .svc dosyasındaki ve uç nokta için bir yapılandırma girişi oluşturma.</span><span class="sxs-lookup"><span data-stu-id="27f5e-136">If any setting (such as a reader quota) must be modified, you must not use the configuration-free approach by removing the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> from the .svc file and creating a configuration entry for the endpoint.</span></span>  
  
 <span data-ttu-id="27f5e-137">Bunu kullanıyorsa, hizmetiniz ASP.NET uyumluluk modu - Örneğin, gerektirip gerektirmediğini <xref:System.Web.HttpContext> sınıfı veya ASP.NET yetkilendirme mekanizmaları - bir yapılandırma dosyası bu modu etkinleştirmek için hala gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="27f5e-137">If your service requires ASP.NET Compatibility Mode - for example, if it uses the <xref:System.Web.HttpContext> class or ASP.NET authorization mechanisms - a configuration file is still required to turn on this mode.</span></span> <span data-ttu-id="27f5e-138">Gerekli yapılandırma öğesi [ \<serviceHostingEnvironment >](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) gibi eklenmelidir öğesi.</span><span class="sxs-lookup"><span data-stu-id="27f5e-138">The configuration element required is the [\<serviceHostingEnvironment>](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) element, which must be added as follows.</span></span>  
  
 `<system.serviceModel>`  
  
 `<serviceHostingEnvironment aspNetCompatibilityEnabled="true" /> </system.serviceModel>`  
  
 <span data-ttu-id="27f5e-139">Daha fazla bilgi için bkz: [WCF hizmetleri ve ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md) konu.</span><span class="sxs-lookup"><span data-stu-id="27f5e-139">For more information, see the [WCF Services and ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md) topic.</span></span>  
  
 <span data-ttu-id="27f5e-140"><xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> Sınıftır türetilen bir sınıftan <xref:System.ServiceModel.Activation.ServiceHostFactory>.</span><span class="sxs-lookup"><span data-stu-id="27f5e-140">The <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> class is a derived class of <xref:System.ServiceModel.Activation.ServiceHostFactory>.</span></span> <span data-ttu-id="27f5e-141">Hizmet ana bilgisayar üreteci mekanizması ayrıntılı bir açıklaması için bkz: [genişletme barındırma ServiceHostFactory kullanarak](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md) konu.</span><span class="sxs-lookup"><span data-stu-id="27f5e-141">For a detailed explanation of the service host factory mechanism, see the [Extending Hosting Using ServiceHostFactory](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md) topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27f5e-142">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="27f5e-142">See Also</span></span>  
 [<span data-ttu-id="27f5e-143">ASP.NET AJAX için WCF Hizmetleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="27f5e-143">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)  
 [<span data-ttu-id="27f5e-144">Nasıl yapılır: AJAX Etkinleştirilmiş ASP.NET Web Hizmetlerini WCF'ye Taşıma</span><span class="sxs-lookup"><span data-stu-id="27f5e-144">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
