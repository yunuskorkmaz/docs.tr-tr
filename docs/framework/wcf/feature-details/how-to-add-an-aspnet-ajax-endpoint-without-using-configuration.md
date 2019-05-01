---
title: 'Nasıl yapılır: Yapılandırma Kullanmadan ASP.NET AJAX Uç Noktası Ekleme'
ms.date: 03/30/2017
ms.assetid: b05c1742-8d0a-4673-9d71-725b18a3008e
ms.openlocfilehash: 078580b96ab911f65790e58338951532cd7ad704
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62047912"
---
# <a name="how-to-add-an-aspnet-ajax-endpoint-without-using-configuration"></a><span data-ttu-id="c6a16-102">Nasıl yapılır: Yapılandırma Kullanmadan ASP.NET AJAX Uç Noktası Ekleme</span><span class="sxs-lookup"><span data-stu-id="c6a16-102">How to: Add an ASP.NET AJAX Endpoint Without Using Configuration</span></span>
<span data-ttu-id="c6a16-103">Windows Communication Foundation (WCF), istemci Web sitesinde JavaScript'ten çağrılabilen bir ASP.NET AJAX etkinleştirilmiş bir uç nokta hizmetidir oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="c6a16-103">Windows Communication Foundation (WCF) allows you to create a service that exposes an ASP.NET AJAX-enabled endpoint that can be called from JavaScript on a client Web site.</span></span> <span data-ttu-id="c6a16-104">Böyle bir uç nokta oluşturmak için bir yapılandırma dosyası, tüm diğer WCF uç noktaları ile gibi kullanabilir veya yapılandırma öğeleri gerektirmeyen bir yöntem kullanın.</span><span class="sxs-lookup"><span data-stu-id="c6a16-104">To create such an endpoint, you can either use a configuration file, as with all other WCF endpoints, or use a method that does not require any configuration elements.</span></span> <span data-ttu-id="c6a16-105">Bu konuda, ikinci yaklaşım gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c6a16-105">This topic demonstrates the second approach.</span></span>  
  
 <span data-ttu-id="c6a16-106">ASP.NET AJAX uç noktaları yapılandırma olmadan hizmetleri oluşturmak için Internet Information Services (IIS) tarafından Hizmetleri barındırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c6a16-106">To create services with ASP.NET AJAX endpoints without configuration, the services must be hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="c6a16-107">Bu yaklaşımı kullanarak bir ASP.NET AJAX uç noktası etkinleştirmeyi belirtin <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> Fabrika parametresi olarak [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) .svc dosyasında yönergesi.</span><span class="sxs-lookup"><span data-stu-id="c6a16-107">To activate an ASP.NET AJAX endpoint using this approach, specify the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> as the Factory parameter in the [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive in the .svc file.</span></span> <span data-ttu-id="c6a16-108">Bu özel fabrika bir ASP.NET AJAX uç noktası otomatik olarak yapılandırır ve böylece istemci Web sitesinde JavaScript'ten çağrılabilir bileşendir.</span><span class="sxs-lookup"><span data-stu-id="c6a16-108">This custom factory is the component that automatically configures an ASP.NET AJAX endpoint so that it can be called from JavaScript on a client Web site.</span></span>  
  
 <span data-ttu-id="c6a16-109">Çalışan bir örnek için bkz. [olmadan AJAX Hizmeti Yapılandırması](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="c6a16-109">For a working example, see the [AJAX Service Without Configuration](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).</span></span>  
  
 <span data-ttu-id="c6a16-110">Özetini yapılandırma öğeleri kullanarak bir ASP.NET AJAX uç noktası nasıl yapılandıracağınızı öğrenmek için bkz: [nasıl yapılır: ASP.NET AJAX uç noktası eklemek için yapılandırma kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md).</span><span class="sxs-lookup"><span data-stu-id="c6a16-110">For an outline of how to configure an ASP.NET AJAX endpoint using configuration elements, see [How to: Use Configuration to Add an ASP.NET AJAX Endpoint](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md).</span></span>  
  
### <a name="to-create-a-basic-wcf-service"></a><span data-ttu-id="c6a16-111">Temel bir WCF hizmeti oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="c6a16-111">To create a basic WCF service</span></span>  
  
1. <span data-ttu-id="c6a16-112">İle işaretlenen arabirim ile temel bir WCF sözleşmesi tanımlayın. <xref:System.ServiceModel.ServiceContractAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="c6a16-112">Define a basic WCF service contract with an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="c6a16-113">Her işlemi ile işaretle <xref:System.ServiceModel.OperationContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="c6a16-113">Mark each operation with the <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="c6a16-114">Ayarladığınızdan emin olun <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="c6a16-114">Be sure to set the <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> property.</span></span>  
  
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
  
2. <span data-ttu-id="c6a16-115">Uygulama `ICalculator` hizmet söyleşmesi bir `CalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="c6a16-115">Implement the `ICalculator` service contract with a `CalculatorService`.</span></span>  
  
    ```csharp  
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
  
    //Other operations omitted…  
    ```  
  
3. <span data-ttu-id="c6a16-116">Tanımlamak için bir ad alanı `ICalculator` ve `CalculatorService` tarafından bir ad alanı bloğunda kaydırmalı uygulamaları.</span><span class="sxs-lookup"><span data-stu-id="c6a16-116">Define a namespace for the `ICalculator` and `CalculatorService` implementations by wrapping them in a namespace block.</span></span>  
  
    ```csharp  
    Namespace Microsoft.Ajax.Samples  
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
### <a name="to-host-the-service-in-internet-information-services-without-configuration"></a><span data-ttu-id="c6a16-117">Internet Information Services hizmetinde yapılandırma olmadan barındırmak için</span><span class="sxs-lookup"><span data-stu-id="c6a16-117">To host the service in Internet Information Services without configuration</span></span>  
  
1. <span data-ttu-id="c6a16-118">Uygulamada .svc uzantılı hizmeti adlı yeni bir dosya oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c6a16-118">Create a new file named service with a .svc extension in the application.</span></span> <span data-ttu-id="c6a16-119">Uygun ekleyerek bu dosyayı Düzenle [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) hizmeti yönerge bilgi.</span><span class="sxs-lookup"><span data-stu-id="c6a16-119">Edit this file by adding the appropriate [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive information for the service.</span></span> <span data-ttu-id="c6a16-120">Belirten <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> kullanılacak olan [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) yönergesi, bir ASP.NET AJAX uç noktası otomatik olarak yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="c6a16-120">Specify that the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is to be used in the [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive to automatically configure an ASP.NET AJAX endpoint.</span></span>  
  
    ```  
    <%@ServiceHost   
        language=c#   
        Debug="true"   
        Service="Microsoft.Ajax.Samples.CalculatorService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
2. <span data-ttu-id="c6a16-121">Derleme hizmeti ve istemciden çağırın.</span><span class="sxs-lookup"><span data-stu-id="c6a16-121">Build the service and call it from the client.</span></span> <span data-ttu-id="c6a16-122">Internet Information Services (IIS) çağrıldığında hizmetini etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="c6a16-122">Internet Information Services (IIS) activates the service when called.</span></span> <span data-ttu-id="c6a16-123">IIS'de barındırma hakkında daha fazla bilgi için bkz. [nasıl yapılır: IIS'de WCF Hizmeti barındırma](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).</span><span class="sxs-lookup"><span data-stu-id="c6a16-123">For more information about hosting in IIS, see [How to: Host a WCF Service in IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).</span></span>  
  
### <a name="to-call-the-service"></a><span data-ttu-id="c6a16-124">Hizmeti çağırmak için</span><span class="sxs-lookup"><span data-stu-id="c6a16-124">To call the service</span></span>  
  
1. <span data-ttu-id="c6a16-125">Hizmeti kullanıma sunuldu ve service.svc/ için istek göndererek çağrılabilir uç nokta boş bir adresten .svc dosyanın göreli yapılandırılır\<işlemi > - Örneğin, için service.svc/Add `Add` işlemi.</span><span class="sxs-lookup"><span data-stu-id="c6a16-125">The endpoint is configured at an empty address relative to the .svc file, so the service is now available and can be invoked by sending requests to service.svc/\<operation> - for example, service.svc/Add for the `Add` operation.</span></span> <span data-ttu-id="c6a16-126">ASP.NET AJAX komut dosyası Manager denetim betikleri koleksiyonuna hizmet URL'sini girerek kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c6a16-126">You can use it by entering the service URL into the Scripts collection of the ASP.NET AJAX Script Manager control.</span></span> <span data-ttu-id="c6a16-127">Bir örnek için bkz. [olmadan AJAX Hizmeti Yapılandırması](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="c6a16-127">For an example, see the [AJAX Service Without Configuration](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6a16-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="c6a16-128">Example</span></span>  
  
 <span data-ttu-id="c6a16-129">Göreli temel URL boş bir adresi otomatik olarak yapılandırılmış uç noktası oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c6a16-129">The automatically-configured endpoint is created at an empty address relative to the base URL.</span></span> <span data-ttu-id="c6a16-130">Bir yapılandırma dosyası da eklenir ve bu yaklaşımı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c6a16-130">A configuration file can also be added and used with this approach.</span></span> <span data-ttu-id="c6a16-131">Yapılandırma dosyası, uç nokta tanımları varsa, bu uç noktalar için otomatik olarak yapılandırılan uç noktası eklenir.</span><span class="sxs-lookup"><span data-stu-id="c6a16-131">If the configuration file contains endpoint definitions, these endpoints are added to the automatically-configured endpoint.</span></span>  
  
 <span data-ttu-id="c6a16-132">Örneğin, service.svc kullanır <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> ve hizmet dizini kullanarak aynı hizmet için bir uç nokta tanımlayan bir Web.config dosyası içeren <xref:System.ServiceModel.BasicHttpBinding> "soap" göreli adresinde.</span><span class="sxs-lookup"><span data-stu-id="c6a16-132">For example, service.svc uses the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> and the service directory contains a Web.config file that defines an endpoint for the same service using the <xref:System.ServiceModel.BasicHttpBinding> at the "soap" relative address.</span></span> <span data-ttu-id="c6a16-133">Bu durumda, iki uç nokta hizmet içerir: (Bu, ASP.NET AJAX isteklerine yanıt verip) service.svc ve (hangi SOAP isteklerine yanıt verip) service.svc/soap başka bir seferde.</span><span class="sxs-lookup"><span data-stu-id="c6a16-133">In this case, the service contains two endpoints: one at service.svc (which responds to ASP.NET AJAX requests) and another at service.svc/soap (which responds to SOAP requests).</span></span>  
  
 <span data-ttu-id="c6a16-134">Yapılandırma dosyası boş bir göreli adresinde bir uç nokta tanımlar varsa ve <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> olan kullanıldığında, bir özel durum ve hizmeti başlatılamıyor.</span><span class="sxs-lookup"><span data-stu-id="c6a16-134">If the configuration file defines an endpoint at an empty relative address and the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is used, an exception is thrown and the service fails to start.</span></span>  
  
 <span data-ttu-id="c6a16-135">Yapılandırma, otomatik olarak yapılandırılmış uç noktası ayarlarını değiştirmek için kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="c6a16-135">You cannot use configuration to modify settings on the automatically-configured endpoint.</span></span> <span data-ttu-id="c6a16-136">Herhangi bir ayar (örneğin, bir okuyucu kota) olmalıdır değiştirilmesi, yapılandırma gerektirmeyen bir yaklaşım kaldırarak kullanmamalıdır <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> .svc dosya ve uç nokta için bir yapılandırma girişi oluşturma.</span><span class="sxs-lookup"><span data-stu-id="c6a16-136">If any setting (such as a reader quota) must be modified, you must not use the configuration-free approach by removing the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> from the .svc file and creating a configuration entry for the endpoint.</span></span>  
  
 <span data-ttu-id="c6a16-137">Kullanılıyorsa hizmetinizi ASP.NET uyumluluk modunun - Örneğin, gerektirip gerektirmediğini <xref:System.Web.HttpContext> sınıf ya da ASP.NET yetkilendirme mekanizmalarını - bir yapılandırma dosyası yine de bu modu açmak gerekir.</span><span class="sxs-lookup"><span data-stu-id="c6a16-137">If your service requires ASP.NET Compatibility Mode - for example, if it uses the <xref:System.Web.HttpContext> class or ASP.NET authorization mechanisms - a configuration file is still required to turn on this mode.</span></span> <span data-ttu-id="c6a16-138">Gerekli yapılandırma öğesi [ \<serviceHostingEnvironment >](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) öğesi gibi eklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="c6a16-138">The configuration element required is the [\<serviceHostingEnvironment>](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) element, which must be added as follows.</span></span>  
  
 `<system.serviceModel>`  
  
 `<serviceHostingEnvironment aspNetCompatibilityEnabled="true" /> </system.serviceModel>`  
  
 <span data-ttu-id="c6a16-139">Daha fazla bilgi için [WCF hizmetleri ve ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md) konu.</span><span class="sxs-lookup"><span data-stu-id="c6a16-139">For more information, see the [WCF Services and ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md) topic.</span></span>  
  
 <span data-ttu-id="c6a16-140"><xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> , Türetilmiş bir sınıfı <xref:System.ServiceModel.Activation.ServiceHostFactory>.</span><span class="sxs-lookup"><span data-stu-id="c6a16-140">The <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> class is a derived class of <xref:System.ServiceModel.Activation.ServiceHostFactory>.</span></span> <span data-ttu-id="c6a16-141">Hizmet ana bilgisayar üreteci mekanizması ayrıntılı bir açıklaması için bkz. [genişletme barındırma ServiceHostFactory kullanarak](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md) konu.</span><span class="sxs-lookup"><span data-stu-id="c6a16-141">For a detailed explanation of the service host factory mechanism, see the [Extending Hosting Using ServiceHostFactory](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md) topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6a16-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c6a16-142">See also</span></span>

- [<span data-ttu-id="c6a16-143">ASP.NET AJAX için WCF Hizmetleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c6a16-143">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)
- [<span data-ttu-id="c6a16-144">Nasıl yapılır: AJAX etkinleştirilmiş ASP.NET Web hizmetlerini WCF'ye taşıma</span><span class="sxs-lookup"><span data-stu-id="c6a16-144">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
