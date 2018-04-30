---
title: 'Nasıl yapılır: ASP.NET AJAX Uç Noktası Eklemek için Yapılandırma Kullanma'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7cd0099e-dc3a-47e4-a38c-6e10f997f6ea
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 28051dbed626dc0073a38e72f2cdc21ea108a32e
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-use-configuration-to-add-an-aspnet-ajax-endpoint"></a>Nasıl yapılır: ASP.NET AJAX Uç Noktası Eklemek için Yapılandırma Kullanma
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] bir ASP.NET AJAX etkinleştirilmiş uç nokta bir istemci Web sitesinde JavaScript'ten çağrılabilir kullanılabilir hale getirir bir hizmet oluşturmanıza olanak sağlar. Bu tür bir uç nokta oluşturmak için ya da bir yapılandırma dosyası tüm diğer olarak kullanabileceğiniz [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] uç noktaları veya tüm yapılandırma öğeleri gerektirmeyen bir yöntemi kullanın. Bu konuda yapılandırma yaklaşım gösterilir.  
  
 Hizmet uç noktası, ASP.NET AJAX etkinleştirilmiş olmasını sağlayan yordamının parçası kullanmak için uç nokta yapılandırmayı içerir <xref:System.ServiceModel.WebHttpBinding> ve eklemek için [ \<enableWebScript >](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) uç noktası davranışı. Uç nokta yapılandırdıktan sonra uygulama ve hizmet barındırmak için adımları tarafından kullanılan benzerdir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet. Çalışan bir örnek için bkz: [AJAX hizmeti kullanarak HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).  
  
 Yapılandırma kullanmadan ASP.NET AJAX uç noktası yapılandırma hakkında daha fazla bilgi için bkz: [nasıl yapılır: ASP.NET AJAX uç nokta olmadan kullanarak Yapılandırması Ekle](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).  
  
### <a name="to-create-a-basic-wcf-service"></a>Temel bir WCF hizmeti oluşturmak için  
  
1.  Temel bir tanımlamak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet sözleşmesini bir arabirim ile işaretlenmiş <xref:System.ServiceModel.ServiceContractAttribute> özniteliği. Her işlemiyle işaretlemek <xref:System.ServiceModel.OperationContractAttribute>. Ayarladığınızdan emin olun <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> özelliği.  
  
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
  
2.  Uygulama `ICalculator` hizmet sözleşmesine bir `CalculatorService`.  
  
    ```  
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
  
    //Other operations omitted…  
    ```  
  
3.  Bir ad alanı için tanımlayın `ICalculator` ve `CalculatorService` bir ad alanı bloğunda kaydırma tarafından uygulamaları.  
  
    ```  
    Namespace Microsoft.Ajax.Samples  
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
### <a name="to-create-an-aspnet-ajax-endpoint-for-the-service"></a>Hizmeti için bir ASP.NET AJAX uç noktası oluşturmak için  
  
1.  Davranışı yapılandırmasını oluşturun ve belirtin [ \<enableWebScript >](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) hizmet uç noktalarına ASP.NET AJAX etkinleştirilmiş davranışı.  
  
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
  
2.  Kullanan hizmet için bir uç nokta oluşturma <xref:System.ServiceModel.WebHttpBinding> ve önceki adımda tanımlanan ASP.NET AJAX davranışı.  
  
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
  
### <a name="to-host-the-service-in-iis"></a>Ana bilgisayar hizmeti IIS  
  
1.  IIS hizmetinde barındırmak için uygulama .svc uzantısında hizmetiyle adlı yeni bir dosya oluşturun. Uygun ekleyerek bu dosyayı düzenlemek [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) hizmet için yönerge bilgileri. Örneğin, hizmet dosyanın içeriği `CalculatorService` örnek aşağıdaki bilgileri içerir.  
  
    ```  
    <%@ServiceHost   
    language=c#   
    Debug="true"   
    Service="Microsoft.Ajax.Samples.CalculatorService"  
    %>  
    ```  
  
2.  IIS barındırma hakkında daha fazla bilgi için bkz: [nasıl yapılır: IIS'de WCF Hizmeti barındırma](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).  
  
### <a name="to-call-the-service"></a>Hizmeti çağırmak için  
  
1.  Hizmet kullanıma sunulmuştur ve service.svc/ için istek göndererek çağrılabilir uç nokta .svc dosyasıyla ilişkili boş bir adresindeki yapılandırıldığından\<işlemi > - Örneğin, service.svc/Add için `Add` işlemi. ASP.NET AJAX komut dosyası Manager denetim betikleri koleksiyona uç nokta URL'sini girerek kullanabilirsiniz. Bir örnek için bkz: [AJAX hizmeti kullanarak HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ASP.NET AJAX için WCF Hizmetleri Oluşturma](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)  
 [Nasıl yapılır: AJAX Etkinleştirilmiş ASP.NET Web Hizmetlerini WCF'ye Taşıma](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
