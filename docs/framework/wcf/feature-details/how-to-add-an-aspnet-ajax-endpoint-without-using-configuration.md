---
title: 'Nasıl yapılır: Yapılandırma Kullanmadan ASP.NET AJAX Uç Noktası Ekleme'
ms.date: 03/30/2017
ms.assetid: b05c1742-8d0a-4673-9d71-725b18a3008e
ms.openlocfilehash: 9935e2a7738796fff9a037b09237a6acbf7bf988
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185131"
---
# <a name="how-to-add-an-aspnet-ajax-endpoint-without-using-configuration"></a><span data-ttu-id="1aa3f-102">Nasıl yapılır: Yapılandırma Kullanmadan ASP.NET AJAX Uç Noktası Ekleme</span><span class="sxs-lookup"><span data-stu-id="1aa3f-102">How to: Add an ASP.NET AJAX Endpoint Without Using Configuration</span></span>
<span data-ttu-id="1aa3f-103">Windows Communication Foundation (WCF), istemci Web sitesinde JavaScript'ten çağrılabilen AJAX özellikli ASP.NET bir bitiş noktasını ortaya çıkaran bir hizmet oluşturmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="1aa3f-103">Windows Communication Foundation (WCF) allows you to create a service that exposes an ASP.NET AJAX-enabled endpoint that can be called from JavaScript on a client Web site.</span></span> <span data-ttu-id="1aa3f-104">Böyle bir bitiş noktası oluşturmak için, diğer tüm WCF uç noktalarında olduğu gibi bir yapılandırma dosyası kullanabilir veya yapılandırma öğesi gerektirmeyen bir yöntem kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1aa3f-104">To create such an endpoint, you can either use a configuration file, as with all other WCF endpoints, or use a method that does not require any configuration elements.</span></span> <span data-ttu-id="1aa3f-105">Bu konu ikinci yaklaşımı gösterir.</span><span class="sxs-lookup"><span data-stu-id="1aa3f-105">This topic demonstrates the second approach.</span></span>  
  
 <span data-ttu-id="1aa3f-106">ASP.NET AJAX uç noktalarına sahip hizmetler oluşturmak için, hizmetlerin Internet Information Services (IIS) tarafından barındırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1aa3f-106">To create services with ASP.NET AJAX endpoints without configuration, the services must be hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="1aa3f-107">Bu yaklaşımı kullanarak ASP.NET bir AJAX uç <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> noktasını etkinleştirmek için,.svc dosyasındaki [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) yönergesinde Fabrika parametresi olarak belirtin.</span><span class="sxs-lookup"><span data-stu-id="1aa3f-107">To activate an ASP.NET AJAX endpoint using this approach, specify the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> as the Factory parameter in the [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive in the .svc file.</span></span> <span data-ttu-id="1aa3f-108">Bu özel fabrika, bir istemci Web sitesinde JavaScript'ten çağrılabilmesi için ASP.NET bir AJAX bitiş noktasını otomatik olarak yapılandıran bileşendir.</span><span class="sxs-lookup"><span data-stu-id="1aa3f-108">This custom factory is the component that automatically configures an ASP.NET AJAX endpoint so that it can be called from JavaScript on a client Web site.</span></span>  
  
 <span data-ttu-id="1aa3f-109">Çalışan bir örnek için, [Yapılandırma olmadan AJAX Hizmeti'ne](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="1aa3f-109">For a working example, see the [AJAX Service Without Configuration](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).</span></span>  
  
 <span data-ttu-id="1aa3f-110">Yapılandırma öğelerini kullanarak ASP.NET bir AJAX uç noktasının nasıl yapılandırılabildiğini özetlemek için bkz [ASP.NET.](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)</span><span class="sxs-lookup"><span data-stu-id="1aa3f-110">For an outline of how to configure an ASP.NET AJAX endpoint using configuration elements, see [How to: Use Configuration to Add an ASP.NET AJAX Endpoint](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md).</span></span>  
  
### <a name="to-create-a-basic-wcf-service"></a><span data-ttu-id="1aa3f-111">Temel bir WCF hizmeti oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="1aa3f-111">To create a basic WCF service</span></span>  
  
1. <span data-ttu-id="1aa3f-112">Öznitelik ile işaretlenmiş bir arabirim ile <xref:System.ServiceModel.ServiceContractAttribute> temel bir WCF hizmet sözleşmesi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="1aa3f-112">Define a basic WCF service contract with an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="1aa3f-113">Her işlemi <xref:System.ServiceModel.OperationContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="1aa3f-113">Mark each operation with the <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="1aa3f-114"><xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> Özelliği ayarladıklı.</span><span class="sxs-lookup"><span data-stu-id="1aa3f-114">Be sure to set the <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> property.</span></span>  
  
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
  
2. <span data-ttu-id="1aa3f-115">Bir `ICalculator` `CalculatorService`ile hizmet sözleşmesi uygulayın.</span><span class="sxs-lookup"><span data-stu-id="1aa3f-115">Implement the `ICalculator` service contract with a `CalculatorService`.</span></span>  
  
    ```csharp  
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
  
    //Other operations omitted…  
    ```  
  
3. <span data-ttu-id="1aa3f-116">Ad alanı bloğuna `ICalculator` `CalculatorService` sararak ve uygulamalar için bir ad alanı tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="1aa3f-116">Define a namespace for the `ICalculator` and `CalculatorService` implementations by wrapping them in a namespace block.</span></span>  
  
    ```csharp  
    Namespace Microsoft.Ajax.Samples  
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
### <a name="to-host-the-service-in-internet-information-services-without-configuration"></a><span data-ttu-id="1aa3f-117">Hizmeti yapılandırma olmadan Internet Bilgi Hizmetleri'nde barındırmak için</span><span class="sxs-lookup"><span data-stu-id="1aa3f-117">To host the service in Internet Information Services without configuration</span></span>  
  
1. <span data-ttu-id="1aa3f-118">Uygulamada .svc uzantısı bulunan hizmet adlı yeni bir dosya oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1aa3f-118">Create a new file named service with a .svc extension in the application.</span></span> <span data-ttu-id="1aa3f-119">Hizmet için uygun [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) yönergesi bilgilerini ekleyerek bu dosyayı düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="1aa3f-119">Edit this file by adding the appropriate [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive information for the service.</span></span> <span data-ttu-id="1aa3f-120"><xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> ASP.NET bir AJAX bitiş noktasını otomatik olarak yapılandırmak için [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) yönergesinde kullanılacağını belirtin.</span><span class="sxs-lookup"><span data-stu-id="1aa3f-120">Specify that the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is to be used in the [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive to automatically configure an ASP.NET AJAX endpoint.</span></span>  
  
    ```text
    <%@ServiceHost
        language=c#
        Debug="true"
        Service="Microsoft.Ajax.Samples.CalculatorService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
2. <span data-ttu-id="1aa3f-121">Hizmeti oluşturun ve istemciden arayın.</span><span class="sxs-lookup"><span data-stu-id="1aa3f-121">Build the service and call it from the client.</span></span> <span data-ttu-id="1aa3f-122">Internet Information Services (IIS) çağrıldığında hizmeti etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="1aa3f-122">Internet Information Services (IIS) activates the service when called.</span></span> <span data-ttu-id="1aa3f-123">IIS'de barındırma hakkında daha fazla bilgi için [bkz.](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)</span><span class="sxs-lookup"><span data-stu-id="1aa3f-123">For more information about hosting in IIS, see [How to: Host a WCF Service in IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).</span></span>  
  
### <a name="to-call-the-service"></a><span data-ttu-id="1aa3f-124">Hizmeti aramak için</span><span class="sxs-lookup"><span data-stu-id="1aa3f-124">To call the service</span></span>  
  
1. <span data-ttu-id="1aa3f-125">Bitiş noktası .svc dosyasına göre boş bir adreste yapılandırılır, bu nedenle hizmet artık kullanılabilir ve service.svc/\<operation> isteklerigönderilerek çağrılabilir - örneğin, service.svc/Add `Add` operasyon için.</span><span class="sxs-lookup"><span data-stu-id="1aa3f-125">The endpoint is configured at an empty address relative to the .svc file, so the service is now available and can be invoked by sending requests to service.svc/\<operation> - for example, service.svc/Add for the `Add` operation.</span></span> <span data-ttu-id="1aa3f-126">Hizmet URL'sini ASP.NET AJAX Script Manager denetiminin Scripts koleksiyonuna girerek kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1aa3f-126">You can use it by entering the service URL into the Scripts collection of the ASP.NET AJAX Script Manager control.</span></span> <span data-ttu-id="1aa3f-127">Örneğin, [Yapılandırma olmadan AJAX Hizmeti'ne](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="1aa3f-127">For an example, see the [AJAX Service Without Configuration](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1aa3f-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="1aa3f-128">Example</span></span>  
  
 <span data-ttu-id="1aa3f-129">Otomatik olarak yapılandırılan bitiş noktası, temel URL'ye göre boş bir adreste oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="1aa3f-129">The automatically-configured endpoint is created at an empty address relative to the base URL.</span></span> <span data-ttu-id="1aa3f-130">Yapılandırma dosyası da eklenebilir ve bu yaklaşımla kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1aa3f-130">A configuration file can also be added and used with this approach.</span></span> <span data-ttu-id="1aa3f-131">Yapılandırma dosyası uç nokta tanımları içeriyorsa, bu uç noktalar otomatik olarak yapılandırılan bitiş noktasına eklenir.</span><span class="sxs-lookup"><span data-stu-id="1aa3f-131">If the configuration file contains endpoint definitions, these endpoints are added to the automatically-configured endpoint.</span></span>  
  
 <span data-ttu-id="1aa3f-132">Örneğin, service.svc kullanır <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> ve hizmet dizini "sabun" göreli adresini kullanarak <xref:System.ServiceModel.BasicHttpBinding> aynı hizmet için bir bitiş noktası tanımlayan bir Web.config dosyası içerir.</span><span class="sxs-lookup"><span data-stu-id="1aa3f-132">For example, service.svc uses the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> and the service directory contains a Web.config file that defines an endpoint for the same service using the <xref:System.ServiceModel.BasicHttpBinding> at the "soap" relative address.</span></span> <span data-ttu-id="1aa3f-133">Bu durumda, hizmet iki uç nokta içerir: biri service.svc'de (ASP.NET AJAX isteklerine yanıt verir) ve diğeri service.svc/soap'da (SOAP isteklerine yanıt verir).</span><span class="sxs-lookup"><span data-stu-id="1aa3f-133">In this case, the service contains two endpoints: one at service.svc (which responds to ASP.NET AJAX requests) and another at service.svc/soap (which responds to SOAP requests).</span></span>  
  
 <span data-ttu-id="1aa3f-134">Yapılandırma dosyası boş bir göreli adreste bir <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> bitiş noktası tanımlar ve kullanılırsa, bir özel durum atılır ve hizmet başlatılmaz.</span><span class="sxs-lookup"><span data-stu-id="1aa3f-134">If the configuration file defines an endpoint at an empty relative address and the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is used, an exception is thrown and the service fails to start.</span></span>  
  
 <span data-ttu-id="1aa3f-135">Otomatik olarak yapılandırılan bitiş noktasındaki ayarları değiştirmek için yapılandırmayı kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="1aa3f-135">You cannot use configuration to modify settings on the automatically-configured endpoint.</span></span> <span data-ttu-id="1aa3f-136">Herhangi bir ayar (okuyucu kotası gibi) değiştirilmesi gerekiyorsa, .svc <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> dosyasından kaldırarak ve bitiş noktası için bir yapılandırma girişi oluşturarak yapılandırmasız yaklaşımı kullanmamalısınız.</span><span class="sxs-lookup"><span data-stu-id="1aa3f-136">If any setting (such as a reader quota) must be modified, you must not use the configuration-free approach by removing the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> from the .svc file and creating a configuration entry for the endpoint.</span></span>  
  
 <span data-ttu-id="1aa3f-137">Hizmetiniz ASP.NET Uyumluluk Modu gerektiriyorsa (örneğin, <xref:System.Web.HttpContext> sınıfı veya ASP.NET yetkilendirme mekanizmalarını kullanıyorsa - bu modu açmak için yine de bir yapılandırma dosyası gerekir.</span><span class="sxs-lookup"><span data-stu-id="1aa3f-137">If your service requires ASP.NET Compatibility Mode - for example, if it uses the <xref:System.Web.HttpContext> class or ASP.NET authorization mechanisms - a configuration file is still required to turn on this mode.</span></span> <span data-ttu-id="1aa3f-138">Gerekli yapılandırma öğesi aşağıdaki gibi eklenmesi gereken [ \<serviceHostingEnvironment>](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) öğesidir.</span><span class="sxs-lookup"><span data-stu-id="1aa3f-138">The configuration element required is the [\<serviceHostingEnvironment>](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) element, which must be added as follows.</span></span>  
  
 `<system.serviceModel>`  
  
 `<serviceHostingEnvironment aspNetCompatibilityEnabled="true" /> </system.serviceModel>`  
  
 <span data-ttu-id="1aa3f-139">Daha fazla bilgi için [WCF Hizmetleri ve ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md) konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="1aa3f-139">For more information, see the [WCF Services and ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md) topic.</span></span>  
  
 <span data-ttu-id="1aa3f-140">Sınıf <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> türetilmiş bir <xref:System.ServiceModel.Activation.ServiceHostFactory>sınıftır.</span><span class="sxs-lookup"><span data-stu-id="1aa3f-140">The <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> class is a derived class of <xref:System.ServiceModel.Activation.ServiceHostFactory>.</span></span> <span data-ttu-id="1aa3f-141">Hizmet ana bilgisayar fabrika mekanizmasıayrıntılı bir açıklama için, [ServiceHostFactory](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md) konu kullanarak Genişletme Hosting bakın.</span><span class="sxs-lookup"><span data-stu-id="1aa3f-141">For a detailed explanation of the service host factory mechanism, see the [Extending Hosting Using ServiceHostFactory](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md) topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1aa3f-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1aa3f-142">See also</span></span>

- [<span data-ttu-id="1aa3f-143">ASP.NET AJAX için WCF Hizmetleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="1aa3f-143">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)
- [<span data-ttu-id="1aa3f-144">Nasıl yapılır: AJAX Etkinleştirilmiş ASP.NET Web Hizmetlerini WCF'ye Taşıma</span><span class="sxs-lookup"><span data-stu-id="1aa3f-144">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
