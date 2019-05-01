---
title: 'Nasıl yapılır: ASP.NET AJAX Uç Noktaları için HTTP POST ve HTTP GET İstekleri Arasında Seçim Yapma'
ms.date: 03/30/2017
ms.assetid: b47de82a-4c92-4af6-bceb-a5cb8bb8ede9
ms.openlocfilehash: 33763a77d1ab1c82af9b9e1fb9c42d72392f8798
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62047236"
---
# <a name="how-to-choose-between-http-post-and-http-get-requests-for-aspnet-ajax-endpoints"></a>Nasıl yapılır: ASP.NET AJAX Uç Noktaları için HTTP POST ve HTTP GET İstekleri Arasında Seçim Yapma

Windows Communication Foundation (WCF), istemci Web sitesinde JavaScript'ten çağrılabilen bir ASP.NET AJAX etkinleştirilmiş bir uç nokta hizmetidir oluşturmanıza olanak sağlar. Bu hizmetler oluşturmaya yönelik temel yordamları ele alınmıştır [nasıl yapılır: ASP.NET AJAX uç noktası eklemek için yapılandırma kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) ve [nasıl yapılır: Yapılandırma kullanmadan ASP.NET AJAX uç noktası ekleme](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).  
  
 ASP.NET AJAX varsayılan olan HTTP POST ile HTTP POST ve GET HTTP fiilleri kullanan işlemleri destekler. Bir işlem oluşturma yan etkileri varsa ve nadiren bağlanan veya hiç değişen verileri döndürür, HTTP GET bunun yerine kullanın. GET işlemleri sonuçlarını, aynı işlemi birden çok çağrı hizmetinize tek bir istekte neden olabilir yani önbelleğe alınabilir. WCF tarafından belirtilmez ancak (tarayıcıda bir kullanıcının, bir ara sunucu ve diğer düzeylere.) herhangi bir düzeyde gerçekleştirilebildiği önbelleğe alma Önbelleğe alma hizmeti performansını artırmak istiyorsanız verileri sık sık değişiyorsa kabul edilebilir olmayabilir ancak veya işlem bir eylem gerçekleştirirse avantajlıdır.  
  
 Örneğin, bir kullanıcının Müzik Kitaplığı yönetmek için hizmeti tasarlıyorsanız, Al kullanarak bir albüm başlık avantajları göre sanatçının arayan bir işlem ancak albüm kullanıcının kişisel koleksiyonuna ekler. bir işlem sonrası kullanmalısınız.  
  
 Önbellek ömrünü denetlemek için kullanın <xref:System.ServiceModel.Web.OutgoingWebResponseContext> türü. Örneğin, hava durumu tahminleri saatlik güncelleştirildi, kullanacağınız döndüren bir hizmet tasarlarken ALIR ancak hizmet kullanıcıları, eski veri erişimini engellemek için bir saat veya daha az önbellek süresi sınırlayın.  
  
 Betik Manager denetim kullanan hizmetler bir ASP.NET AJAX sayfasından kullanırken, işlemin kullandığı GET veya POST - betik manager mekanizması doğru istek türü verilmesi sağlanır olup olmadığını yönelttiğiniz fark etmez.  
  
 HTTP GET işlemleri, karmaşık veri anlaşması türleri dahil olmak üzere sonrası işlemleri tarafından desteklenen tüm giriş parametrelerini kullanın. Ancak, çoğu durumda bu çok fazla parametre veya önbellek verimliliğini azaltır çünkü GET işlemleri çok karmaşık parametreler önlemek için önerilir.  
  
 Bu konuda GET ve POST ekleyerek arasında seçim yapmayı gösteren <xref:System.ServiceModel.Web.WebGetAttribute> veya <xref:System.ServiceModel.Web.WebInvokeAttribute> öznitelikleri hizmet sözleşmesindeki ilgili işlemler. Çalışan hizmeti almak için gereken (uygulama, yapılandırın ve hizmeti barındırmak için) diğer adımları tüm ASP.NET AJAX WCF hizmeti tarafından kullanılan benzerdir.  
  
 Bir işlem ile işaretlenen <xref:System.ServiceModel.Web.WebGetAttribute> her zaman bir GET isteği kullanır. Bir işlem ile işaretlenen <xref:System.ServiceModel.Web.WebInvokeAttribute>, veya değil herhangi bir iki özniteliği ile işaretlenmiş, bir POST isteği kullanır. <xref:System.ServiceModel.Web.WebInvokeAttribute> Diğer HTTP fiilleri, diğer alın ve sonrası (PUT ve DELETE gibi) kullanımına izin verdiği <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> özelliği. Ancak, bu Eylemler, ASP.NET AJAX tarafından desteklenmez. ASP.NET sayfaları komut Yöneticisi denetimini kullanarak hizmetinden kullanmak istiyorsanız, kullanmayın <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> özelliği.  
  
 GET için geçiş, çalışan bir örnek için bkz: [temel AJAX hizmeti](../../../../docs/framework/wcf/samples/basic-ajax-service.md) örnek.  
  
 POST kullanan bir örnek için bkz. [hizmet HTTP POST kullanan AJAX](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) örnek.  
  
## <a name="to-create-a-wcf-service-that-responds-to-http-get-or-http-post-requests"></a>Bir WCF hizmeti oluşturmak için HTTP GET veya POST HTTP isteklerine yanıt
  
1. İle işaretlenen arabirim ile temel bir WCF sözleşmesi tanımlayın. <xref:System.ServiceModel.ServiceContractAttribute> özniteliği. Her işlemi ile işaretle <xref:System.ServiceModel.OperationContractAttribute>. Ekleme <xref:System.ServiceModel.Web.WebGetAttribute> bir işlem HTTP GET isteklerine yanıt vermesini işleyebileceği için özniteliği. Ayrıca ekleyebilirsiniz <xref:System.ServiceModel.Web.WebInvokeAttribute> HTTP POST açıkça belirtmek için özniteliği veya bir öznitelik varsayılan olarak HTTP POST belirtmeyin.
  
    ```csharp
    [ServiceContract]  
    public interface IMusicService  
    {  
        //This operation uses a GET method.  
        [OperationContract]  
        [WebGet]  
        string LookUpArtist(string album);  
  
        //This operation will use a POST method.  
        [OperationContract]  
        [WebInvoke]  
        void AddAlbum(string user, string album);  
  
        //This operation will use POST method by default  
        //since nothing else is explicitly specified.  
        [OperationContract]  
        string[] GetAlbums(string user);  
  
        //Other operations omitted…  
  
    }  
    ```  
  
2. Uygulama `IMusicService` hizmet söyleşmesi bir `MusicService`.
  
    ```csharp
    public class MusicService : IMusicService  
    {  
        public void AddAlbum(string user, string album)  
        {  
            //Add implementation here.  
        }  
  
         //Other operations omitted…  
    }  
    ```  
  
3. Uygulamada .svc uzantılı hizmeti adlı yeni bir dosya oluşturun. Uygun ekleyerek bu dosyayı Düzenle [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) hizmeti yönerge bilgi. Belirten <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> kullanılacak olan [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) yönergesi, bir ASP.NET AJAX uç noktası otomatik olarak yapılandırılır.  
  
    ```  
    <%@ServiceHost   
        language=c#   
        Debug="true"   
        Service="Microsoft.Ajax.Samples.MusicService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
## <a name="to-call-the-service"></a>Hizmeti çağırmak için  
  
1. Tarayıcıyı kullanarak herhangi bir istemci kod olmadan hizmetinizin GET işlemleri test edebilirsiniz. Örneğin, hizmetiniz, yapılandırılması durumunda `http://example.com/service.svc` sonra yazarak adresi `http://example.com/service.svc/LookUpArtist?album=SomeAlbum` tarayıcı adres çubuğuna hizmeti çağırır ve indirdiğiniz ya da görüntülenen yanıt neden olur.
  
2. Diğer bir ASP.NET AJAX Hizmetleri aynı şekilde GET işlemleri ile Hizmetleri'ni kullanabilirsiniz - URL ASP.NET AJAX komut Yöneticisi'nin betikleri koleksiyonuna hizmet girerek denetim. Bir örnek için bkz. [temel AJAX hizmeti](../../../../docs/framework/wcf/samples/basic-ajax-service.md).
  
## <a name="see-also"></a>Ayrıca bkz.

- [ASP.NET AJAX için WCF Hizmetleri Oluşturma](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)
- [Nasıl yapılır: AJAX etkinleştirilmiş ASP.NET Web hizmetlerini WCF'ye taşıma](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
