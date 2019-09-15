---
title: 'Nasıl yapılır: ASP.NET AJAX Uç Noktası Eklemek için Yapılandırma Kullanma'
ms.date: 03/30/2017
ms.assetid: 7cd0099e-dc3a-47e4-a38c-6e10f997f6ea
ms.openlocfilehash: 33f99161034db2aa142a422139406a1a68d42b2c
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972272"
---
# <a name="how-to-use-configuration-to-add-an-aspnet-ajax-endpoint"></a>Nasıl yapılır: ASP.NET AJAX Uç Noktası Eklemek için Yapılandırma Kullanma
Windows Communication Foundation (WCF), istemci Web sitesinde JavaScript 'ten çağrılabilen ASP.NET AJAX özellikli bir uç nokta sağlayan bir hizmet oluşturmanızı sağlar. Böyle bir uç nokta oluşturmak için, diğer tüm Windows Communication Foundation (WCF) uç noktalarında olduğu gibi bir yapılandırma dosyası ya da herhangi bir yapılandırma öğesi gerektirmeyen bir yöntemi kullanabilirsiniz. Bu konu, yapılandırma yaklaşımını gösterir.  
  
 Hizmet uç noktasının ASP.NET AJAX özellikli hale gelmesini sağlayan yordamın bir bölümü, <xref:System.ServiceModel.WebHttpBinding> ' i kullanmak için bitiş noktasını yapılandırmayı ve [ \<enablewebscript >](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) uç noktası davranışını eklemeyi içerir. Uç nokta yapılandırıldıktan sonra, hizmeti uygulama ve barındırma adımları herhangi bir WCF hizmeti tarafından kullanılanlarla benzerdir. Çalışan bir örnek için bkz. [http post kullanan AJAX Hizmeti](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).  
  
 Yapılandırma kullanmadan bir ASP.NET AJAX uç noktası yapılandırma hakkında daha fazla bilgi için bkz [. nasıl yapılır: Yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md)kullanmadan bir ASP.NET AJAX uç noktası ekleyin.  
  
## <a name="to-create-a-basic-wcf-service"></a>Temel bir WCF hizmeti oluşturmak için  
  
1. <xref:System.ServiceModel.ServiceContractAttribute> Özniteliği ile işaretlenmiş bir arabirimle birlikte temel bir WCF hizmeti sözleşmesi tanımlayın. Her işlemi ile <xref:System.ServiceModel.OperationContractAttribute>işaretleyin. <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> Özelliği ayarladığınızdan emin olun.  
  
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
    namespace Microsoft.Ajax.Samples  
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
## <a name="to-create-an-aspnet-ajax-endpoint-for-the-service"></a>Hizmet için bir ASP.NET AJAX uç noktası oluşturmak için  
  
1. Bir davranış yapılandırması oluşturun ve hizmetin ASP.NET AJAX özellikli uç noktaları için [ \<enablewebscript >](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) davranışını belirtin.  
  
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
  
1. Hizmeti IIS 'de barındırmak için, uygulamada. svc uzantılı yeni bir dosya adlı hizmet oluşturun. Hizmet için uygun [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) yönergesi bilgilerini ekleyerek bu dosyayı düzenleyin. Örneğin, `CalculatorService` örnek için hizmet dosyasındaki içerik aşağıdaki bilgileri içerir.  
  
    ```
    <%@ServiceHost   
    language=c#   
    Debug="true"   
    Service="Microsoft.Ajax.Samples.CalculatorService"  
    %>  
    ```  
  
2. IIS 'de barındırma hakkında daha fazla bilgi için bkz [. nasıl yapılır: IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)'de bir WCF hizmeti barındırın.  
  
## <a name="to-call-the-service"></a>Hizmeti çağırmak için  
  
1. Uç nokta,. svc dosyası ile ilgili boş bir adreste yapılandırılır, bu nedenle hizmet artık kullanılabilir ve hizmet. svc/\<işlem > istek göndererek çağrılabilir. Örneğin, `Add` işlem için Service. svc/Add. Bunu, ASP.NET AJAX betik Yöneticisi denetiminin betikler koleksiyonuna Endpoint URL 'SI girerek kullanabilirsiniz. Bir örnek için bkz. [http post kullanan AJAX Hizmeti](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ASP.NET AJAX için WCF Hizmetleri Oluşturma](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)
- [Nasıl yapılır: AJAX etkin ASP.NET Web hizmetlerini WCF 'ye geçirme](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
