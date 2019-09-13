---
title: 'Nasıl yapılır: Yapılandırma Kullanmadan ASP.NET AJAX Uç Noktası Ekleme'
ms.date: 03/30/2017
ms.assetid: b05c1742-8d0a-4673-9d71-725b18a3008e
ms.openlocfilehash: 4a7ff48e529ab58c8744edea22d52ad12a4d7b96
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70895084"
---
# <a name="how-to-add-an-aspnet-ajax-endpoint-without-using-configuration"></a>Nasıl yapılır: Yapılandırma Kullanmadan ASP.NET AJAX Uç Noktası Ekleme
Windows Communication Foundation (WCF), istemci Web sitesinde JavaScript 'ten çağrılabilen ASP.NET AJAX özellikli bir uç nokta sunan bir hizmet oluşturmanıza olanak sağlar. Böyle bir uç nokta oluşturmak için, diğer tüm WCF uç noktalarında olduğu gibi bir yapılandırma dosyası ya da herhangi bir yapılandırma öğesi gerektirmeyen bir yöntemi kullanabilirsiniz. Bu konuda ikinci yaklaşım gösterilmektedir.  
  
 ASP.NET AJAX uç noktalarıyla yapılandırma olmadan hizmetler oluşturmak için, hizmetler Internet Information Services (IIS) tarafından barındırılmalıdır. Bu yaklaşımı kullanarak bir ASP.NET AJAX uç noktasını etkinleştirmek için. svc <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> dosyasındaki [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) yönergesinde Factory parametresi olarak belirtin. Bu özel fabrika, bir istemci Web sitesindeki JavaScript 'ten çağrılabilmesi için bir ASP.NET AJAX uç noktası otomatik olarak yapılandıran bileşendir.  
  
 Çalışan bir örnek için, [yapılandırma olmadan Ajax hizmetine](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md)bakın.  
  
 Yapılandırma öğelerini kullanarak bir ASP.NET AJAX uç noktası yapılandırma ana hattı için bkz [. nasıl yapılır: ASP.NET AJAX uç noktası](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)eklemek için yapılandırma kullanın.  
  
### <a name="to-create-a-basic-wcf-service"></a>Temel bir WCF hizmeti oluşturmak için  
  
1. <xref:System.ServiceModel.ServiceContractAttribute> Özniteliği ile işaretlenmiş bir arabirimle birlikte temel bir WCF hizmeti sözleşmesi tanımlayın. Her işlemi ile <xref:System.ServiceModel.OperationContractAttribute>işaretleyin. <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> Özelliği ayarladığınızdan emin olun.  
  
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
  
2. Hizmet sözleşmesini bir `CalculatorService`ile uygulayın. `ICalculator`  
  
    ```csharp  
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
  
    //Other operations omitted…  
    ```  
  
3. Bir ad alanı bloğunda `ICalculator` sarmalayarak `CalculatorService` ve uygulamalar için bir ad alanı tanımlayın.  
  
    ```csharp  
    Namespace Microsoft.Ajax.Samples  
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
### <a name="to-host-the-service-in-internet-information-services-without-configuration"></a>Hizmeti yapılandırma olmadan Internet Information Services içinde barındırmak için  
  
1. Uygulamada. svc uzantısıyla yeni bir dosya adlı hizmet oluşturun. Hizmet için uygun [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) yönergesi bilgilerini ekleyerek bu dosyayı düzenleyin. ASP.NET AJAX uç noktasını otomatik olarak yapılandırmak için [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) yönergesinde kullanılacağını belirtin. <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>  
  
    ```text
    <%@ServiceHost   
        language=c#   
        Debug="true"   
        Service="Microsoft.Ajax.Samples.CalculatorService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
2. Hizmeti derleyin ve istemciden çağırın. Internet Information Services (IIS), çağrıldığında hizmeti etkinleştirir. IIS 'de barındırma hakkında daha fazla bilgi için bkz [. nasıl yapılır: IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)'de bir WCF hizmeti barındırın.  
  
### <a name="to-call-the-service"></a>Hizmeti çağırmak için  
  
1. Uç nokta,. svc dosyası ile ilgili boş bir adreste yapılandırılır, bu nedenle hizmet artık kullanılabilir ve hizmet. svc/\<işlem > istek göndererek çağrılabilir. Örneğin, `Add` işlem için Service. svc/Add. Bunu, ASP.NET AJAX betik Yöneticisi denetiminin betikler koleksiyonuna hizmet URL 'sini girerek kullanabilirsiniz. Bir örnek için, [yapılandırma olmadan Ajax hizmetine](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md)bakın.  
  
## <a name="example"></a>Örnek  
  
 Otomatik olarak yapılandırılan uç nokta, temel URL 'ye göre boş bir adreste oluşturulur. Bu yaklaşım ile de bir yapılandırma dosyası eklenebilir ve kullanılabilir. Yapılandırma dosyası uç nokta tanımları içeriyorsa, bu uç noktalar otomatik olarak yapılandırılmış uç noktaya eklenir.  
  
 Örneğin, Service. svc ' nı kullanır <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> ve hizmet dizini, "SOAP" göreli adresinde öğesini <xref:System.ServiceModel.BasicHttpBinding> kullanarak aynı hizmet için bir uç nokta tanımlayan bir Web. config dosyası içerir. Bu durumda hizmet iki uç nokta içerir: bir adet Service. svc (ASP.NET AJAX isteklerine yanıt verir) ve başka bir Service. svc/SOAP (SOAP isteklerine yanıt verir).  
  
 Yapılandırma dosyası boş bir göreli adreste bir uç nokta tanımlıyorsa ve <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> kullanılırsa, bir özel durum oluşturulur ve hizmet başlatılamaz.  
  
 Otomatik olarak yapılandırılmış uç noktasındaki ayarları değiştirmek için yapılandırmayı kullanamazsınız. Herhangi bir ayarın (örn. bir okuyucu kotası) değiştirilmesi gerekiyorsa,. svc dosyasından ' yi kaldırarak <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> ve uç nokta için bir yapılandırma girişi oluşturarak yapılandırma-ücretsiz yaklaşımını kullanmanız gerekir.  
  
 Hizmetiniz ASP.NET uyumluluk moduna gerektiriyorsa (örneğin, <xref:System.Web.HttpContext> sınıfı veya ASP.NET yetkilendirme mekanizmalarını kullanıyorsa), bu modu açmak için bir yapılandırma dosyası gerekir. Gerekli yapılandırma öğesi, aşağıdaki şekilde eklenmesi gereken [ ServiceHostingEnvironment>öğesidir.\<](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)  
  
 `<system.serviceModel>`  
  
 `<serviceHostingEnvironment aspNetCompatibilityEnabled="true" /> </system.serviceModel>`  
  
 Daha fazla bilgi için bkz. [WCF Hizmetleri ve ASP.net](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md) konusu.  
  
 Sınıfı, türetilmiş bir <xref:System.ServiceModel.Activation.ServiceHostFactory>sınıftır. <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> Hizmet ana bilgisayarı fabrikası mekanizmasına ilişkin ayrıntılı bir açıklama için bkz. [ServiceHostFactory kullanarak barındırma genişletme](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md) konusu.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ASP.NET AJAX için WCF Hizmetleri Oluşturma](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)
- [Nasıl yapılır: AJAX etkin ASP.NET Web hizmetlerini WCF 'ye geçirme](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
