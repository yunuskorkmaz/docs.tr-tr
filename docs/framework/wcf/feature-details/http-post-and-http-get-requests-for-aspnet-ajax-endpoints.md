---
title: "Nasıl yapılır: ASP.NET AJAX Uç Noktaları için HTTP POST ve HTTP GET İstekleri Arasında Seçim Yapma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b47de82a-4c92-4af6-bceb-a5cb8bb8ede9
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fa8aceace03d1abb3bb83de1262331485f12ded3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-choose-between-http-post-and-http-get-requests-for-aspnet-ajax-endpoints"></a>Nasıl yapılır: ASP.NET AJAX Uç Noktaları için HTTP POST ve HTTP GET İstekleri Arasında Seçim Yapma
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]JavaScript'ten bir istemci Web sitesinde çağrılabilen bir ASP.NET AJAX etkin bir uç nokta kullanıma sunan bir hizmet oluşturmanıza olanak sağlar. Bu tür hizmetlerin oluşturmak için temel yordamlar ele alınmıştır [nasıl yapılır: ASP.NET AJAX uç noktası eklemek için yapılandırma kullan](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) ve [nasıl yapılır: ASP.NET AJAX uç nokta olmadan kullanarak yapılandırması eklemek](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).  
  
 ASP.NET AJAX'ı varsayılan olan HTTP POST ile HTTP POST ve HTTP GET fiilleri kullanan işlemler destekler. Bir işlem oluşturma hiçbir yan etkileri varsa ve nadiren bağlanan veya hiç değişen verileri döndürür, HTTP GET yerine kullanın. GET işlemlerin sonuçlarını, yani aynı işlem için birden fazla çağrı hizmetiniz için yalnızca bir istekte sonuçlanabilir önbelleğe alınabilir. Önbelleğe alma işlem [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ancak (tarayıcıda bir kullanıcının, bir proxy sunucusu ve diğer düzeylerdeki.) herhangi bir düzeyde yer alabilir Önbelleğe alma veriler sık değişiyorsa kabul edilebilir olmayabilir ancak veya hizmet performansını artırmak istiyorsanız işlemi bazı eylemler gerçekleştiriyorsa avantajlıdır.  
  
 Örneğin, bir kullanıcının Müzik Kitaplığı yönetmek için hizmeti tanımlıyorsanız, GET kullanarak bir albüm başlık avantajları göre sanatçı arayan bir işlem, ancak bir albümü kullanıcının kişisel koleksiyona ekler bir işlem sonrası kullanmalısınız.  
  
 Önbellek ömrünü denetlemek için kullandığı <xref:System.ServiceModel.Web.OutgoingWebResponseContext> türü. Örneğin, döndürür hava tahminleri saatlik güncelleştirildi, kullanacağınız bir hizmet tasarlarken GET ancak hizmet kullanıcıların eski veri erişimini engellemek için önbelleğe alma süresi bir saat veya daha az sınırlamak.  
  
 Komut dosyası Manager denetim kullanan hizmetler bir ASP.NET AJAX sayfasından kullanırken, işlemin kullandığı GET veya POST - komut dosyası manager mekanizması doğru istek türü verilmesi sağlanır olup olmadığını fark etmez.  
  
 HTTP GET işlemleri karmaşık veri sözleşme türleri dahil olmak üzere gönderme işlemleri tarafından desteklenen giriş parametreleri kullanın. Ancak, çoğu durumda çok fazla parametreleri veya çünkü önbellek verimliliği azaltır, GET işlemlerinde çok karmaşık parametreleri önlemek için önerilir.  
  
 Bu konu, GET ve POST ekleyerek arasında seçmek gösterilmiştir <xref:System.ServiceModel.Web.WebGetAttribute> veya <xref:System.ServiceModel.Web.WebInvokeAttribute> hizmet sözleşmesi ilgili işlemlerinde özniteliklerini. Hizmet çalışıyor almak için gerekli olan (uygulamak, yapılandırma ve hizmet barındırmak için) diğer adımlar herhangi bir ASP.NET AJAX hizmeti tarafından kullanılan benzerdir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 Bir işlem olarak <xref:System.ServiceModel.Web.WebGetAttribute> her zaman bir GET isteği kullanır. Bir işlem olarak <xref:System.ServiceModel.Web.WebInvokeAttribute>, veya değil herhangi iki özniteliği ile işaretlenmiş, bir POST isteği kullanır. <xref:System.ServiceModel.Web.WebInvokeAttribute> Üzerinden diğer HTTP fiillerini, diğer GET ve POST (koy ve Sil gibi) daha kullanılmasına izin verir <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> özelliği. Ancak, bu fiiller ASP.NET AJAX tarafından desteklenmez. ASP.NET sayfaları komut dosyası Yöneticisi denetimini kullanarak hizmetinden kullanmak istiyorsanız, kullanmayın <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> özelliği.  
  
 GET geçiş, çalışan bir örnek için bkz: [temel AJAX hizmeti](../../../../docs/framework/wcf/samples/basic-ajax-service.md) örnek.  
  
 POST kullanan bir örnek için bkz: [AJAX hizmeti kullanarak HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) örnek.  
  
### <a name="to-create-a-wcf-service-that-responds-to-http-get-or-http-post-requests"></a>Bir WCF hizmeti oluşturma, HTTP GET veya HTTP POST isteklerini yanıtlar  
  
1.  Temel bir tanımlamak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet sözleşmesini bir arabirim ile işaretlenmiş <xref:System.ServiceModel.ServiceContractAttribute> özniteliği. Her işlemiyle işaretlemek <xref:System.ServiceModel.OperationContractAttribute>. Ekleme <xref:System.ServiceModel.Web.WebGetAttribute> bir işlem HTTP GET isteklerine yanıt vermesi gerektiğini iznine özniteliği. Ayrıca ekleyebileceğiniz <xref:System.ServiceModel.Web.WebInvokeAttribute> HTTP POST açıkça belirtmek için öznitelik veya HTTP POST için varsayılan olarak bir öznitelik belirtmeyin.  
  
    ```  
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
  
2.  Uygulama `IMusicService` hizmet sözleşmesine bir `MusicService`.  
  
    ```  
    public class MusicService : IMusicService  
    {  
        public void AddAlbum(string user, string album)  
        {  
            //Add implementation here.  
        }  
  
         //Other operations omitted…  
    }  
    ```  
  
3.  Hizmet uygulaması .svc uzantısıyla adlı yeni bir dosya oluşturun. Uygun ekleyerek bu dosyayı düzenlemek [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) hizmet için yönerge bilgileri. Belirtmek <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> kullanılacak olan [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) yönergesi ASP.NET AJAX uç noktası otomatik olarak yapılandırılır.  
  
    ```  
    <%@ServiceHost   
        language=c#   
        Debug="true"   
        Service="Microsoft.Ajax.Samples.MusicService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
### <a name="to-call-the-service"></a>Hizmeti çağırmak için  
  
1.  Tarayıcıyı kullanarak hizmetinizin GET işlemleri herhangi bir istemci kod olmadan test edebilirsiniz. Örneğin, hizmetiniz "http://example.com/service.svc" adresinde yapılandırdıysanız, ardından "http://example.com/service.svc/LookUpArtist?album=SomeAlbum" tarayıcınızın adres çubuğuna yazarak hizmet çağırır ve yanıt olması neden olur indirilen veya görüntülenir.  
  
2.  Diğer bir ASP.NET AJAX Hizmetleri aynı şekilde GET işlemleriyle Hizmetleri'ni kullanabilirsiniz - hizmet girerek betikleri koleksiyona ASP.NET AJAX komut dosyası Yöneticisi'nin URL kontrol. Bir örnek için bkz: [temel AJAX hizmeti](../../../../docs/framework/wcf/samples/basic-ajax-service.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ASP.NET AJAX için WCF Hizmetleri Oluşturma](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)  
 [Nasıl yapılır: AJAX Etkinleştirilmiş ASP.NET Web Hizmetlerini WCF'ye Taşıma](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
