---
title: 'Nasıl yapılır: ASP.NET AJAX Uç Noktası Eklemek için Yapılandırma Kullanma'
ms.date: 03/30/2017
ms.assetid: 7cd0099e-dc3a-47e4-a38c-6e10f997f6ea
ms.openlocfilehash: db5085d01dbed841109ac46fe4e8b2a0143352e3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62039123"
---
# <a name="how-to-use-configuration-to-add-an-aspnet-ajax-endpoint"></a>Nasıl yapılır: ASP.NET AJAX Uç Noktası Eklemek için Yapılandırma Kullanma
Windows Communication Foundation (WCF), bir ASP.NET AJAX etkinleştirilmiş uç nokta, istemci Web sitesinde JavaScript'ten çağrılabilir kullanılabilir bir hizmet oluşturmanıza olanak sağlar. Böyle bir uç nokta oluşturmak için bir yapılandırma dosyası ile tüm diğer Windows Communication Foundation (WCF) uç noktalar olarak kullanabilir veya yapılandırma öğeleri gerektirmeyen bir yöntem kullanın. Bu konuda, yapılandırma yaklaşım gösterilmektedir.  
  
 Hizmet uç noktası, ASP.NET AJAX etkinleştirilmiş olmasını sağlayan yordamının parçası kullanılacak uç nokta yapılandırmayı içerir <xref:System.ServiceModel.WebHttpBinding> eklenecek ve [ \<enableWebScript >](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) uç nokta davranışı. Uç noktası yapılandırıldıktan sonra uygulama ve hizmeti barındırmak için adımları herhangi bir WCF hizmeti tarafından kullanılan benzerdir. Çalışan bir örnek için bkz. [hizmet HTTP POST kullanan AJAX](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).  
  
 Yapılandırma kullanmadan ASP.NET AJAX uç nokta yapılandırma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Yapılandırma kullanmadan ASP.NET AJAX uç noktası ekleme](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).  
  
### <a name="to-create-a-basic-wcf-service"></a>Temel bir WCF hizmeti oluşturmak için  
  
1. İle işaretlenen arabirim ile temel bir WCF sözleşmesi tanımlayın. <xref:System.ServiceModel.ServiceContractAttribute> özniteliği. Her işlemi ile işaretle <xref:System.ServiceModel.OperationContractAttribute>. Ayarladığınızdan emin olun <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> özelliği.  
  
    ```  
    [ServiceContract(Namespace = "MyService")]  
    public interface ICalculator  
    {  
        [OperationContract]  
         // This operation returns the sum of d1 and d2.  
        double Add(double n1, double n2);  
  
        //Other operations omitted…  
  
    }  
    ```  
  
2. Uygulama `ICalculator` hizmet söyleşmesi bir `CalculatorService`.  
  
    ```  
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
  
    //Other operations omitted…  
    ```  
  
3. Tanımlamak için bir ad alanı `ICalculator` ve `CalculatorService` tarafından bir ad alanı bloğunda kaydırmalı uygulamaları.  
  
    ```  
    Namespace Microsoft.Ajax.Samples  
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
### <a name="to-create-an-aspnet-ajax-endpoint-for-the-service"></a>Hizmet için bir ASP.NET AJAX uç noktası oluşturmak için  
  
1. Davranışı yapılandırmasını oluşturun ve belirtin [ \<enableWebScript >](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) ASP.NET AJAX etkinleştirilmiş uç hizmet davranışı.  
  
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
  
2. Kullanan hizmet için bir uç nokta oluşturma <xref:System.ServiceModel.WebHttpBinding> ve önceki adımda tanımlanan ASP.NET AJAX davranışı.  
  
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
  
### <a name="to-host-the-service-in-iis"></a>IIS hizmeti barındırmak için  
  
1. IIS hizmeti barındırmak için uygulamada .svc uzantılı hizmeti adlı yeni bir dosya oluşturun. Uygun ekleyerek bu dosyayı Düzenle [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) hizmeti yönerge bilgi. Örneğin, hizmet dosyanın içeriği `CalculatorService` örnek, aşağıdaki bilgileri içerir.  
  
    ```  
    <%@ServiceHost   
    language=c#   
    Debug="true"   
    Service="Microsoft.Ajax.Samples.CalculatorService"  
    %>  
    ```  
  
2. IIS'de barındırma hakkında daha fazla bilgi için bkz. [nasıl yapılır: IIS'de WCF Hizmeti barındırma](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).  
  
### <a name="to-call-the-service"></a>Hizmeti çağırmak için  
  
1. Hizmeti kullanıma sunuldu ve service.svc/ için istek göndererek çağrılabilir uç nokta boş bir adresten .svc dosyanın göreli yapılandırılır\<işlemi > - Örneğin, için service.svc/Add `Add` işlemi. ASP.NET AJAX komut dosyası Manager denetim betikleri koleksiyona uç nokta URL'sini girerek kullanabilirsiniz. Bir örnek için bkz. [hizmet HTTP POST kullanan AJAX](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ASP.NET AJAX için WCF Hizmetleri Oluşturma](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)
- [Nasıl yapılır: AJAX etkinleştirilmiş ASP.NET Web hizmetlerini WCF'ye taşıma](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
