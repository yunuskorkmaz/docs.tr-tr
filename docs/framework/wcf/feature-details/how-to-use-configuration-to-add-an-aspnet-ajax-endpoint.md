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
# <a name="how-to-use-configuration-to-add-an-aspnet-ajax-endpoint"></a>Nasıl yapılır: ASP.NET AJAX Uç Noktası Eklemek için Yapılandırma Kullanma
Windows Communication Foundation (WCF), bir istemci Web sitesinde JavaScript'ten çağrılabilen ASP.NET AJAX özellikli bitiş noktası nı kullanıma sunabilecek bir hizmet oluşturmanıza olanak tanır. Böyle bir bitiş noktası oluşturmak için, diğer tüm Windows Communication Foundation (WCF) uç noktalarında olduğu gibi bir yapılandırma dosyası kullanabilir veya yapılandırma öğesi gerektirmeyen bir yöntem kullanabilirsiniz. Bu konu yapılandırma yaklaşımını gösterir.  
  
 Yordamın hizmet bitiş noktasının AJAX'ASP.NET olmasını sağlayan bölümü, bitiş noktasını kullanmak <xref:System.ServiceModel.WebHttpBinding> ve [ \<etkinleştirilen WebScript>](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) bitiş noktası davranışını eklemek için yapılandırmaktan oluşur. Bitiş noktasını yapılandırdıktan sonra, hizmeti uygulamak ve barındırma adımları herhangi bir WCF hizmeti tarafından kullanılanadımlara benzer. Çalışan bir örnek için, [HTTP POST'u kullanarak AJAX Hizmeti'ne](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)bakın.  
  
 Yapılandırmayı kullanmadan ASP.NET bir AJAX bitiş noktasının nasıl yapılandırılabildiğini hakkında daha fazla bilgi için bkz [ASP.NET.](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md)  
  
## <a name="to-create-a-basic-wcf-service"></a>Temel bir WCF hizmeti oluşturmak için  
  
1. Öznitelik ile işaretlenmiş bir arabirim ile <xref:System.ServiceModel.ServiceContractAttribute> temel bir WCF hizmet sözleşmesi tanımlayın. Her işlemi <xref:System.ServiceModel.OperationContractAttribute>. <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> Özelliği ayarladıklı.  
  
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
  
2. Bir `ICalculator` `CalculatorService`ile hizmet sözleşmesi uygulayın.  
  
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
  
3. Ad alanı bloğuna `ICalculator` `CalculatorService` sararak ve uygulamalar için bir ad alanı tanımlayın.  
  
    ```csharp
    namespace Microsoft.Ajax.Samples
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
## <a name="to-create-an-aspnet-ajax-endpoint-for-the-service"></a>Hizmet için ASP.NET bir AJAX bitiş noktası oluşturmak için  
  
1. Bir davranış yapılandırması [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) oluşturun ve hizmetin AJAX özellikli ASP.NET uç noktaları için etkinleştirmeWebScript>davranışını belirtin.  
  
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
  
2. Önceki adımda tanımlanan ve ASP.NET <xref:System.ServiceModel.WebHttpBinding> AJAX davranışını kullanan hizmet için bir bitiş noktası oluşturun.  
  
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
  
## <a name="to-host-the-service-in-iis"></a>Hizmeti IIS'de barındırmak için  
  
1. Hizmeti IIS'de barındırmak için, uygulamada .svc uzantısı bulunan hizmet adlı yeni bir dosya oluşturun. Hizmet için uygun [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) yönergesi bilgilerini ekleyerek bu dosyayı düzenleyin. Örneğin, `CalculatorService` örnek için hizmet dosyasındaki içerik aşağıdaki bilgileri içerir.  
  
    ```
    <%@ServiceHost
    language=c#
    Debug="true"
    Service="Microsoft.Ajax.Samples.CalculatorService"  
    %>  
    ```  
  
2. IIS'de barındırma hakkında daha fazla bilgi için [bkz.](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)  
  
## <a name="to-call-the-service"></a>Hizmeti aramak için  
  
1. Bitiş noktası .svc dosyasına göre boş bir adreste yapılandırılır, bu nedenle hizmet artık kullanılabilir ve service.svc/\<operation> isteklerigönderilerek çağrılabilir - örneğin, service.svc/Add `Add` operasyon için. ASP.NET AJAX Script Manager denetiminin Komut Dosyaları koleksiyonuna bitiş noktası URL'sini girerek kullanabilirsiniz. Örneğin, [HTTP POST'u kullanarak AJAX Hizmeti'ne](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ASP.NET AJAX için WCF Hizmetleri Oluşturma](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)
- [Nasıl yapılır: AJAX Etkinleştirilmiş ASP.NET Web Hizmetlerini WCF'ye Taşıma](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
