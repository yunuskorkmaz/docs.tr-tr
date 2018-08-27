---
title: 'Nasıl yapılır: Yapılandırma Kullanmadan ASP.NET AJAX Uç Noktası Ekleme'
ms.date: 03/30/2017
ms.assetid: b05c1742-8d0a-4673-9d71-725b18a3008e
ms.openlocfilehash: 18c02644319dd9d11be39ac4956a4dcf50db3078
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/26/2018
ms.locfileid: "42930818"
---
# <a name="how-to-add-an-aspnet-ajax-endpoint-without-using-configuration"></a>Nasıl yapılır: Yapılandırma Kullanmadan ASP.NET AJAX Uç Noktası Ekleme
Windows Communication Foundation (WCF), istemci Web sitesinde JavaScript'ten çağrılabilen bir ASP.NET AJAX etkinleştirilmiş bir uç nokta hizmetidir oluşturmanıza olanak sağlar. Böyle bir uç nokta oluşturmak için bir yapılandırma dosyası, tüm diğer WCF uç noktaları ile gibi kullanabilir veya yapılandırma öğeleri gerektirmeyen bir yöntem kullanın. Bu konuda, ikinci yaklaşım gösterilmektedir.  
  
 ASP.NET AJAX uç noktaları yapılandırma olmadan hizmetleri oluşturmak için Internet Information Services (IIS) tarafından Hizmetleri barındırılması gerekir. Bu yaklaşımı kullanarak bir ASP.NET AJAX uç noktası etkinleştirmeyi belirtin <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> Fabrika parametresi olarak [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) .svc dosyasında yönergesi. Bu özel fabrika bir ASP.NET AJAX uç noktası otomatik olarak yapılandırır ve böylece istemci Web sitesinde JavaScript'ten çağrılabilir bileşendir.  
  
 Çalışan bir örnek için bkz. [olmadan AJAX Hizmeti Yapılandırması](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).  
  
 Özetini yapılandırma öğeleri kullanarak bir ASP.NET AJAX uç noktası nasıl yapılandıracağınızı öğrenmek için bkz: [nasıl yapılır: ASP.NET AJAX uç noktası eklemek için yapılandırma kullan](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md).  
  
### <a name="to-create-a-basic-wcf-service"></a>Temel bir WCF hizmeti oluşturmak için  
  
1.  İle işaretlenen arabirim ile temel bir WCF sözleşmesi tanımlayın. <xref:System.ServiceModel.ServiceContractAttribute> özniteliği. Her işlemi ile işaretle <xref:System.ServiceModel.OperationContractAttribute>. Ayarladığınızdan emin olun <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> özelliği.  
  
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
  
2.  Uygulama `ICalculator` hizmet söyleşmesi bir `CalculatorService`.  
  
    ```csharp  
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
  
    //Other operations omitted…  
    ```  
  
3.  Tanımlamak için bir ad alanı `ICalculator` ve `CalculatorService` tarafından bir ad alanı bloğunda kaydırmalı uygulamaları.  
  
    ```csharp  
    Namespace Microsoft.Ajax.Samples  
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
### <a name="to-host-the-service-in-internet-information-services-without-configuration"></a>Internet Information Services hizmetinde yapılandırma olmadan barındırmak için  
  
1.  Uygulamada .svc uzantılı hizmeti adlı yeni bir dosya oluşturun. Uygun ekleyerek bu dosyayı Düzenle [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) hizmeti yönerge bilgi. Belirten <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> kullanılacak olan [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) yönergesi, bir ASP.NET AJAX uç noktası otomatik olarak yapılandırılır.  
  
    ```  
    <%@ServiceHost   
        language=c#   
        Debug="true"   
        Service="Microsoft.Ajax.Samples.CalculatorService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
2.  Derleme hizmeti ve istemciden çağırın. Internet Information Services (IIS) çağrıldığında hizmetini etkinleştirir. IIS'de barındırma hakkında daha fazla bilgi için bkz. [nasıl yapılır: IIS'de WCF Hizmeti barındırma](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).  
  
### <a name="to-call-the-service"></a>Hizmeti çağırmak için  
  
1.  Hizmeti kullanıma sunuldu ve service.svc/ için istek göndererek çağrılabilir uç nokta boş bir adresten .svc dosyanın göreli yapılandırılır\<işlemi > - Örneğin, için service.svc/Add `Add` işlemi. ASP.NET AJAX komut dosyası Manager denetim betikleri koleksiyonuna hizmet URL'sini girerek kullanabilirsiniz. Bir örnek için bkz. [olmadan AJAX Hizmeti Yapılandırması](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).  
  
## <a name="example"></a>Örnek  
  
 Göreli temel URL boş bir adresi otomatik olarak yapılandırılmış uç noktası oluşturulur. Bir yapılandırma dosyası da eklenir ve bu yaklaşımı kullanılır. Yapılandırma dosyası, uç nokta tanımları varsa, bu uç noktalar için otomatik olarak yapılandırılan uç noktası eklenir.  
  
 Örneğin, service.svc kullanır <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> ve hizmet dizini kullanarak aynı hizmet için bir uç nokta tanımlayan bir Web.config dosyası içeren <xref:System.ServiceModel.BasicHttpBinding> "soap" göreli adresinde. Bu durumda, iki uç nokta hizmet içerir: (Bu, ASP.NET AJAX isteklerine yanıt verip) service.svc ve (hangi SOAP isteklerine yanıt verip) service.svc/soap başka bir seferde.  
  
 Yapılandırma dosyası boş bir göreli adresinde bir uç nokta tanımlar varsa ve <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> olan kullanıldığında, bir özel durum ve hizmeti başlatılamıyor.  
  
 Yapılandırma, otomatik olarak yapılandırılmış uç noktası ayarlarını değiştirmek için kullanamazsınız. Herhangi bir ayar (örneğin, bir okuyucu kota) olmalıdır değiştirilmesi, yapılandırma gerektirmeyen bir yaklaşım kaldırarak kullanmamalıdır <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> .svc dosya ve uç nokta için bir yapılandırma girişi oluşturma.  
  
 Kullanılıyorsa hizmetinizi ASP.NET uyumluluk modunun - Örneğin, gerektirip gerektirmediğini <xref:System.Web.HttpContext> sınıf ya da ASP.NET yetkilendirme mekanizmalarını - bir yapılandırma dosyası yine de bu modu açmak gerekir. Gerekli yapılandırma öğesi [ \<serviceHostingEnvironment >](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) öğesi gibi eklenmesi gerekir.  
  
 `<system.serviceModel>`  
  
 `<serviceHostingEnvironment aspNetCompatibilityEnabled="true" /> </system.serviceModel>`  
  
 Daha fazla bilgi için [WCF hizmetleri ve ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md) konu.  
  
 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> , Türetilmiş bir sınıfı <xref:System.ServiceModel.Activation.ServiceHostFactory>. Hizmet ana bilgisayar üreteci mekanizması ayrıntılı bir açıklaması için bkz. [genişletme barındırma ServiceHostFactory kullanarak](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md) konu.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ASP.NET AJAX için WCF Hizmetleri Oluşturma](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)  
 [Nasıl yapılır: AJAX Etkinleştirilmiş ASP.NET Web Hizmetlerini WCF'ye Taşıma](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
