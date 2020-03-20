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
# <a name="how-to-add-an-aspnet-ajax-endpoint-without-using-configuration"></a>Nasıl yapılır: Yapılandırma Kullanmadan ASP.NET AJAX Uç Noktası Ekleme
Windows Communication Foundation (WCF), istemci Web sitesinde JavaScript'ten çağrılabilen AJAX özellikli ASP.NET bir bitiş noktasını ortaya çıkaran bir hizmet oluşturmanıza olanak tanır. Böyle bir bitiş noktası oluşturmak için, diğer tüm WCF uç noktalarında olduğu gibi bir yapılandırma dosyası kullanabilir veya yapılandırma öğesi gerektirmeyen bir yöntem kullanabilirsiniz. Bu konu ikinci yaklaşımı gösterir.  
  
 ASP.NET AJAX uç noktalarına sahip hizmetler oluşturmak için, hizmetlerin Internet Information Services (IIS) tarafından barındırılması gerekir. Bu yaklaşımı kullanarak ASP.NET bir AJAX uç <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> noktasını etkinleştirmek için,.svc dosyasındaki [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) yönergesinde Fabrika parametresi olarak belirtin. Bu özel fabrika, bir istemci Web sitesinde JavaScript'ten çağrılabilmesi için ASP.NET bir AJAX bitiş noktasını otomatik olarak yapılandıran bileşendir.  
  
 Çalışan bir örnek için, [Yapılandırma olmadan AJAX Hizmeti'ne](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md)bakın.  
  
 Yapılandırma öğelerini kullanarak ASP.NET bir AJAX uç noktasının nasıl yapılandırılabildiğini özetlemek için bkz [ASP.NET.](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)  
  
### <a name="to-create-a-basic-wcf-service"></a>Temel bir WCF hizmeti oluşturmak için  
  
1. Öznitelik ile işaretlenmiş bir arabirim ile <xref:System.ServiceModel.ServiceContractAttribute> temel bir WCF hizmet sözleşmesi tanımlayın. Her işlemi <xref:System.ServiceModel.OperationContractAttribute>. <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> Özelliği ayarladıklı.  
  
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
  
2. Bir `ICalculator` `CalculatorService`ile hizmet sözleşmesi uygulayın.  
  
    ```csharp  
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
  
    //Other operations omitted…  
    ```  
  
3. Ad alanı bloğuna `ICalculator` `CalculatorService` sararak ve uygulamalar için bir ad alanı tanımlayın.  
  
    ```csharp  
    Namespace Microsoft.Ajax.Samples  
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
### <a name="to-host-the-service-in-internet-information-services-without-configuration"></a>Hizmeti yapılandırma olmadan Internet Bilgi Hizmetleri'nde barındırmak için  
  
1. Uygulamada .svc uzantısı bulunan hizmet adlı yeni bir dosya oluşturun. Hizmet için uygun [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) yönergesi bilgilerini ekleyerek bu dosyayı düzenleyin. <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> ASP.NET bir AJAX bitiş noktasını otomatik olarak yapılandırmak için [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) yönergesinde kullanılacağını belirtin.  
  
    ```text
    <%@ServiceHost
        language=c#
        Debug="true"
        Service="Microsoft.Ajax.Samples.CalculatorService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
2. Hizmeti oluşturun ve istemciden arayın. Internet Information Services (IIS) çağrıldığında hizmeti etkinleştirir. IIS'de barındırma hakkında daha fazla bilgi için [bkz.](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)  
  
### <a name="to-call-the-service"></a>Hizmeti aramak için  
  
1. Bitiş noktası .svc dosyasına göre boş bir adreste yapılandırılır, bu nedenle hizmet artık kullanılabilir ve service.svc/\<operation> isteklerigönderilerek çağrılabilir - örneğin, service.svc/Add `Add` operasyon için. Hizmet URL'sini ASP.NET AJAX Script Manager denetiminin Scripts koleksiyonuna girerek kullanabilirsiniz. Örneğin, [Yapılandırma olmadan AJAX Hizmeti'ne](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md)bakın.  
  
## <a name="example"></a>Örnek  
  
 Otomatik olarak yapılandırılan bitiş noktası, temel URL'ye göre boş bir adreste oluşturulur. Yapılandırma dosyası da eklenebilir ve bu yaklaşımla kullanılabilir. Yapılandırma dosyası uç nokta tanımları içeriyorsa, bu uç noktalar otomatik olarak yapılandırılan bitiş noktasına eklenir.  
  
 Örneğin, service.svc kullanır <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> ve hizmet dizini "sabun" göreli adresini kullanarak <xref:System.ServiceModel.BasicHttpBinding> aynı hizmet için bir bitiş noktası tanımlayan bir Web.config dosyası içerir. Bu durumda, hizmet iki uç nokta içerir: biri service.svc'de (ASP.NET AJAX isteklerine yanıt verir) ve diğeri service.svc/soap'da (SOAP isteklerine yanıt verir).  
  
 Yapılandırma dosyası boş bir göreli adreste bir <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> bitiş noktası tanımlar ve kullanılırsa, bir özel durum atılır ve hizmet başlatılmaz.  
  
 Otomatik olarak yapılandırılan bitiş noktasındaki ayarları değiştirmek için yapılandırmayı kullanamazsınız. Herhangi bir ayar (okuyucu kotası gibi) değiştirilmesi gerekiyorsa, .svc <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> dosyasından kaldırarak ve bitiş noktası için bir yapılandırma girişi oluşturarak yapılandırmasız yaklaşımı kullanmamalısınız.  
  
 Hizmetiniz ASP.NET Uyumluluk Modu gerektiriyorsa (örneğin, <xref:System.Web.HttpContext> sınıfı veya ASP.NET yetkilendirme mekanizmalarını kullanıyorsa - bu modu açmak için yine de bir yapılandırma dosyası gerekir. Gerekli yapılandırma öğesi aşağıdaki gibi eklenmesi gereken [ \<serviceHostingEnvironment>](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) öğesidir.  
  
 `<system.serviceModel>`  
  
 `<serviceHostingEnvironment aspNetCompatibilityEnabled="true" /> </system.serviceModel>`  
  
 Daha fazla bilgi için [WCF Hizmetleri ve ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md) konusuna bakın.  
  
 Sınıf <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> türetilmiş bir <xref:System.ServiceModel.Activation.ServiceHostFactory>sınıftır. Hizmet ana bilgisayar fabrika mekanizmasıayrıntılı bir açıklama için, [ServiceHostFactory](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md) konu kullanarak Genişletme Hosting bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ASP.NET AJAX için WCF Hizmetleri Oluşturma](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)
- [Nasıl yapılır: AJAX Etkinleştirilmiş ASP.NET Web Hizmetlerini WCF'ye Taşıma](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
