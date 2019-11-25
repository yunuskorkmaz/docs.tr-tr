---
title: 'Nasıl yapılır: ASP.NET AJAX Uç Noktası Eklemek için Yapılandırma Kullanma'
ms.date: 03/30/2017
ms.assetid: 7cd0099e-dc3a-47e4-a38c-6e10f997f6ea
ms.openlocfilehash: 3ccfb34614707c17885da3ed37f545bbab808869
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73978260"
---
# <a name="how-to-use-configuration-to-add-an-aspnet-ajax-endpoint"></a>Nasıl yapılır: ASP.NET AJAX Uç Noktası Eklemek için Yapılandırma Kullanma
Windows Communication Foundation (WCF), istemci Web sitesinde JavaScript 'ten çağrılabilen ASP.NET AJAX özellikli bir uç nokta sağlayan bir hizmet oluşturmanızı sağlar. Böyle bir uç nokta oluşturmak için, diğer tüm Windows Communication Foundation (WCF) uç noktalarında olduğu gibi bir yapılandırma dosyası ya da herhangi bir yapılandırma öğesi gerektirmeyen bir yöntemi kullanabilirsiniz. Bu konu, yapılandırma yaklaşımını gösterir.  
  
 Hizmet uç noktasının ASP.NET AJAX özellikli hale gelmesini sağlayan yordamın bir bölümü, <xref:System.ServiceModel.WebHttpBinding> kullanmak için uç noktayı yapılandırmayı ve [\<enableWebScript >](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) uç nokta davranışını eklemeyi içerir. Uç nokta yapılandırıldıktan sonra, hizmeti uygulama ve barındırma adımları herhangi bir WCF hizmeti tarafından kullanılanlarla benzerdir. Çalışan bir örnek için bkz. [http post kullanan AJAX Hizmeti](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).  
  
 Yapılandırma kullanmadan bir ASP.NET AJAX uç noktası yapılandırma hakkında daha fazla bilgi için bkz. [nasıl yapılır: yapılandırma kullanmadan ASP.NET AJAX uç noktası ekleme](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).  
  
## <a name="to-create-a-basic-wcf-service"></a>Temel bir WCF hizmeti oluşturmak için  
  
1. <xref:System.ServiceModel.ServiceContractAttribute> özniteliğiyle işaretlenmiş bir arabirimle birlikte temel bir WCF hizmet sözleşmesi tanımlayın. Her işlemi <xref:System.ServiceModel.OperationContractAttribute>işaretleyin. <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> özelliğini ayarladığınızdan emin olun.  
  
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
  
2. `ICalculator` hizmet sözleşmesini bir `CalculatorService`uygulayın.  
  
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
  
3. `ICalculator` ve `CalculatorService` uygulamalar için bir ad alanı bloğunda bir ad alanı tanımlayın.  
  
    ```csharp
    namespace Microsoft.Ajax.Samples
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
## <a name="to-create-an-aspnet-ajax-endpoint-for-the-service"></a>Hizmet için bir ASP.NET AJAX uç noktası oluşturmak için  
  
1. Bir davranış yapılandırması oluşturun ve hizmetin ASP.NET AJAX özellikli uç noktaları için [\<enableWebScript >](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) davranışını belirtin.  
  
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
  
2. Önceki adımda tanımlanan <xref:System.ServiceModel.WebHttpBinding> ve ASP.NET AJAX davranışını kullanan hizmet için bir uç nokta oluşturun.  
  
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
  
## <a name="to-host-the-service-in-iis"></a>Hizmeti IIS 'de barındırmak için  
  
1. Hizmeti IIS 'de barındırmak için, uygulamada. svc uzantılı yeni bir dosya adlı hizmet oluşturun. Hizmet için uygun [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) yönerge bilgilerini ekleyerek bu dosyayı düzenleyin. Örneğin, `CalculatorService` örneği için hizmet dosyasındaki içerik aşağıdaki bilgileri içerir.  
  
    ```
    <%@ServiceHost   
    language=c#   
    Debug="true"   
    Service="Microsoft.Ajax.Samples.CalculatorService"  
    %>  
    ```  
  
2. IIS 'de barındırma hakkında daha fazla bilgi için bkz. [nasıl yapılır: IIS 'de WCF hizmeti barındırma](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).  
  
## <a name="to-call-the-service"></a>Hizmeti çağırmak için  
  
1. Uç nokta,. svc dosyasına göre boş bir adreste yapılandırılır, bu nedenle hizmet artık kullanılabilir ve hizmet. svc/\<işlem > (örneğin, `Add` işlemi için Service. svc/Add) göndererek çağrılabilir. Bunu, ASP.NET AJAX betik Yöneticisi denetiminin betikler koleksiyonuna Endpoint URL 'SI girerek kullanabilirsiniz. Bir örnek için bkz. [http post kullanan AJAX Hizmeti](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ASP.NET AJAX için WCF Hizmetleri Oluşturma](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)
- [Nasıl yapılır: AJAX Etkinleştirilmiş ASP.NET Web Hizmetlerini WCF'ye Taşıma](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
