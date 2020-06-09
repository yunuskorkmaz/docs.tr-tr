---
title: 'Nasıl yapılır: ASP.NET AJAX Uç Noktası Eklemek için Yapılandırma Kullanma'
ms.date: 03/30/2017
ms.assetid: 7cd0099e-dc3a-47e4-a38c-6e10f997f6ea
ms.openlocfilehash: 0aa59ce04e09d700d853f213c6fc9d3a25cdb43b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601159"
---
# <a name="how-to-use-configuration-to-add-an-aspnet-ajax-endpoint"></a>Nasıl yapılır: ASP.NET AJAX Uç Noktası Eklemek için Yapılandırma Kullanma
Windows Communication Foundation (WCF), istemci Web sitesinde JavaScript 'ten çağrılabilen ASP.NET AJAX özellikli bir uç nokta sağlayan bir hizmet oluşturmanızı sağlar. Böyle bir uç nokta oluşturmak için, diğer tüm Windows Communication Foundation (WCF) uç noktalarında olduğu gibi bir yapılandırma dosyası ya da herhangi bir yapılandırma öğesi gerektirmeyen bir yöntemi kullanabilirsiniz. Bu konu, yapılandırma yaklaşımını gösterir.  
  
 Yordamın, hizmet uç noktasının ASP.NET AJAX etkin hale gelmesini sağlayan bölümü, uç nokta davranışını eklemek için ve kullanacak şekilde yapılandırmayı içerir <xref:System.ServiceModel.WebHttpBinding> [\<enableWebScript>](../../configure-apps/file-schema/wcf/enablewebscript.md) . Uç nokta yapılandırıldıktan sonra, hizmeti uygulama ve barındırma adımları herhangi bir WCF hizmeti tarafından kullanılanlarla benzerdir. Çalışan bir örnek için bkz. [http post kullanan AJAX Hizmeti](../samples/ajax-service-using-http-post.md).  
  
 Yapılandırma kullanmadan bir ASP.NET AJAX uç noktası yapılandırma hakkında daha fazla bilgi için bkz. [nasıl yapılır: yapılandırma kullanmadan ASP.NET AJAX uç noktası ekleme](how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).  
  
## <a name="to-create-a-basic-wcf-service"></a>Temel bir WCF hizmeti oluşturmak için  
  
1. Özniteliği ile işaretlenmiş bir arabirimle birlikte temel bir WCF hizmeti sözleşmesi tanımlayın <xref:System.ServiceModel.ServiceContractAttribute> . Her işlemi ile işaretleyin <xref:System.ServiceModel.OperationContractAttribute> . Özelliği ayarladığınızdan emin olun <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> .  
  
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
  
2. `ICalculator`Hizmet sözleşmesini bir ile uygulayın `CalculatorService` .  
  
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
  
3. Bir ad `ICalculator` `CalculatorService` alanı bloğunda sarmalayarak ve uygulamalar için bir ad alanı tanımlayın.  
  
    ```csharp
    namespace Microsoft.Ajax.Samples
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
## <a name="to-create-an-aspnet-ajax-endpoint-for-the-service"></a>Hizmet için bir ASP.NET AJAX uç noktası oluşturmak için  
  
1. Bir davranış yapılandırması oluşturun ve [\<enableWebScript>](../../configure-apps/file-schema/wcf/enablewebscript.md) hizmetin ASP.NET AJAX özellikli uç noktaları için davranışı belirtin.  
  
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
  
2. <xref:System.ServiceModel.WebHttpBinding>Önceki adımda tanımlanan ve ASP.NET AJAX davranışını kullanan hizmet için bir uç nokta oluşturun.  
  
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
  
1. Hizmeti IIS 'de barındırmak için, uygulamada. svc uzantılı yeni bir dosya adlı hizmet oluşturun. Hizmet için uygun [ \@ ServiceHost](../../configure-apps/file-schema/wcf-directive/servicehost.md) yönergesi bilgilerini ekleyerek bu dosyayı düzenleyin. Örneğin, örnek için hizmet dosyasındaki içerik `CalculatorService` aşağıdaki bilgileri içerir.  
  
    ```
    <%@ServiceHost
    language=c#
    Debug="true"
    Service="Microsoft.Ajax.Samples.CalculatorService"  
    %>  
    ```  
  
2. IIS 'de barındırma hakkında daha fazla bilgi için bkz. [nasıl yapılır: IIS 'de WCF hizmeti barındırma](how-to-host-a-wcf-service-in-iis.md).  
  
## <a name="to-call-the-service"></a>Hizmeti çağırmak için  
  
1. Uç nokta,. svc dosyasına göre boş bir adreste yapılandırılır, bu nedenle hizmet artık kullanılabilir ve hizmet. svc 'ye istek göndererek çağrılabilir. \<operation> Örneğin, işlem için Service. svc/Add. `Add` Bunu, ASP.NET AJAX betik Yöneticisi denetiminin betikler koleksiyonuna Endpoint URL 'SI girerek kullanabilirsiniz. Bir örnek için bkz. [http post kullanan AJAX Hizmeti](../samples/ajax-service-using-http-post.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ASP.NET AJAX için WCF Hizmetleri Oluşturma](creating-wcf-services-for-aspnet-ajax.md)
- [Nasıl yapılır: AJAX Etkinleştirilmiş ASP.NET Web Hizmetlerini WCF'ye Taşıma](how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
