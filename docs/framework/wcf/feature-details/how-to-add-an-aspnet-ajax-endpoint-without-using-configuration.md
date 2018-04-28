---
title: 'Nasıl yapılır: Yapılandırma Kullanmadan ASP.NET AJAX Uç Noktası Ekleme'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b05c1742-8d0a-4673-9d71-725b18a3008e
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d82febd776bfc51e3e9725701253ed19996349b5
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="how-to-add-an-aspnet-ajax-endpoint-without-using-configuration"></a>Nasıl yapılır: Yapılandırma Kullanmadan ASP.NET AJAX Uç Noktası Ekleme
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] JavaScript'ten bir istemci Web sitesinde çağrılabilen bir ASP.NET AJAX etkin bir uç nokta kullanıma sunan bir hizmet oluşturmanıza olanak sağlar. Bu tür bir uç nokta oluşturmak için tüm diğer WCF uç noktaları gibi bir yapılandırma dosyası kullanın veya tüm yapılandırma öğeleri gerektirmeyen bir yöntemi kullanabilirsiniz. Bu konuda, ikinci bir yaklaşım gösterilir.  
  
 ASP.NET AJAX uç noktaları yapılandırma olmadan hizmetleri oluşturmak için hizmetler Internet Information Services (IIS) tarafından barındırılması gerekir. Bu yaklaşımı kullanarak bir ASP.NET AJAX uç noktası etkinleştirmeyi belirtin <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> Fabrika parametresi olarak [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) .svc dosyasındaki yönergesi. Bu özel fabrika ASP.NET AJAX uç noktası otomatik olarak yapılandırır ve böylece istemci Web sitesinde JavaScript'ten çağrılabilir bileşendir.  
  
 Çalışan bir örnek için bkz: [olmadan AJAX Hizmeti Yapılandırması](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).  
  
 Yapılandırma öğeleri kullanarak bir ASP.NET AJAX uç noktası yapılandırmak nasıl ana hattı için bkz: [nasıl yapılır: ASP.NET AJAX uç noktası eklemek için yapılandırma kullan](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md).  
  
### <a name="to-create-a-basic-wcf-service"></a>Temel bir WCF hizmeti oluşturmak için  
  
1.  Temel bir tanımlamak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet sözleşmesini bir arabirim ile işaretlenmiş <xref:System.ServiceModel.ServiceContractAttribute> özniteliği. Her işlemiyle işaretlemek <xref:System.ServiceModel.OperationContractAttribute>. Ayarladığınızdan emin olun <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> özelliği.  
  
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
  
2.  Uygulama `ICalculator` hizmet sözleşmesine bir `CalculatorService`.  
  
    ```csharp  
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
  
    //Other operations omitted…  
    ```  
  
3.  Bir ad alanı için tanımlayın `ICalculator` ve `CalculatorService` bir ad alanı bloğunda kaydırma tarafından uygulamaları.  
  
    ```csharp  
    Namespace Microsoft.Ajax.Samples  
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
### <a name="to-host-the-service-in-internet-information-services-without-configuration"></a>Internet Information Services hizmeti yapılandırma olmadan barındırmak için  
  
1.  Hizmet uygulaması .svc uzantısıyla adlı yeni bir dosya oluşturun. Uygun ekleyerek bu dosyayı düzenlemek [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) hizmet için yönerge bilgileri. Belirtmek <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> kullanılacak olan [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) yönergesi ASP.NET AJAX uç noktası otomatik olarak yapılandırılır.  
  
    ```  
    <%@ServiceHost   
        language=c#   
        Debug="true"   
        Service="Microsoft.Ajax.Samples.CalculatorService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
2.  Yapı Hizmeti ve istemciden çağırın. Internet Information Services (IIS) çağrıldığında hizmetini etkinleştirir. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] IIS, barındırma bkz [nasıl yapılır: IIS'de WCF Hizmeti barındırma](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).  
  
### <a name="to-call-the-service"></a>Hizmeti çağırmak için  
  
1.  Hizmet kullanıma sunulmuştur ve service.svc/ için istek göndererek çağrılabilir uç nokta .svc dosyasıyla ilişkili boş bir adresindeki yapılandırıldığından\<işlemi > - Örneğin, service.svc/Add için `Add` işlemi. Hizmet URL'si ASP.NET AJAX komut dosyası Manager denetim betikleri koleksiyonuna girerek kullanabilirsiniz. Bir örnek için bkz: [olmadan AJAX Hizmeti Yapılandırması](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).  
  
## <a name="example"></a>Örnek  
  
 Temel URL göreli boş bir adresindeki otomatik olarak yapılandırılan uç noktası oluşturuldu. Bir yapılandırma dosyası da eklenir ve Bu yaklaşımda kullanılır. Yapılandırma dosyası uç nokta tanımları içeriyorsa, bu uç noktaları otomatik olarak yapılandırılan uç noktası eklenir.  
  
 Örneğin, service.svc kullanır <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> ve hizmeti dizini kullanarak aynı hizmet için bir uç nokta tanımlayan bir Web.config dosyası içeren <xref:System.ServiceModel.BasicHttpBinding> "soap" göreli adresindeki. Bu durumda, iki uç nokta hizmet içerir: tek (, ASP.NET AJAX isteklerine yanıt verir) service.svc ve başka bir (hangi SOAP isteklerine yanıt verir) service.svc/soap.  
  
 Yapılandırma dosyası boş bir göreli adresinde bir uç nokta tanımlıyorsa ve <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> olduğu kullanıldığında, bir özel durum ve hizmeti başlatılamıyor.  
  
 Otomatik olarak yapılandırılan uç noktası ayarlarını değiştirmek için yapılandırma kullanamaz. Herhangi bir ayarı (örneğin, bir okuyucu kota) olmalıdır, değiştirilebilir, yapılandırma serbest yaklaşım kaldırarak kullanmamalısınız <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> .svc dosyasındaki ve uç nokta için bir yapılandırma girişi oluşturma.  
  
 Bunu kullanıyorsa, hizmetiniz ASP.NET uyumluluk modu - Örneğin, gerektirip gerektirmediğini <xref:System.Web.HttpContext> sınıfı veya ASP.NET yetkilendirme mekanizmaları - bir yapılandırma dosyası bu modu etkinleştirmek için hala gerekli değildir. Gerekli yapılandırma öğesi [ \<serviceHostingEnvironment >](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) gibi eklenmelidir öğesi.  
  
 `<system.serviceModel>`  
  
 `<serviceHostingEnvironment aspNetCompatibilityEnabled="true" /> </system.serviceModel>`  
  
 Daha fazla bilgi için bkz: [WCF hizmetleri ve ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md) konu.  
  
 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> Sınıftır türetilen bir sınıftan <xref:System.ServiceModel.Activation.ServiceHostFactory>. Hizmet ana bilgisayar üreteci mekanizması ayrıntılı bir açıklaması için bkz: [genişletme barındırma ServiceHostFactory kullanarak](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md) konu.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ASP.NET AJAX için WCF Hizmetleri Oluşturma](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)  
 [Nasıl yapılır: AJAX Etkinleştirilmiş ASP.NET Web Hizmetlerini WCF'ye Taşıma](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
