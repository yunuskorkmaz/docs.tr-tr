---
title: 'Nasıl yapılır: ASP.NET AJAX Uç Noktaları için HTTP POST ve HTTP GET İstekleri Arasında Seçim Yapma'
ms.date: 03/30/2017
ms.assetid: b47de82a-4c92-4af6-bceb-a5cb8bb8ede9
ms.openlocfilehash: 6de32c798e7d0db5ad2d8f6666d6c5d1714250d5
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991575"
---
# <a name="how-to-choose-between-http-post-and-http-get-requests-for-aspnet-ajax-endpoints"></a>Nasıl yapılır: ASP.NET AJAX Uç Noktaları için HTTP POST ve HTTP GET İstekleri Arasında Seçim Yapma

Windows Communication Foundation (WCF), istemci Web sitesinde JavaScript 'ten çağrılabilen ASP.NET AJAX özellikli bir uç nokta sunan bir hizmet oluşturmanıza olanak sağlar. Bu tür hizmetleri oluşturmaya yönelik temel yordamlar şu şekilde açıklanmıştır [: ASP.NET AJAX uç noktası](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) eklemek için yapılandırma kullanın ve [şunları yapın: Yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md)kullanmadan bir ASP.NET AJAX uç noktası ekleyin.  
  
 ASP.NET AJAX, HTTP POST ve HTTP GET fiillerini kullanan işlemleri destekler, varsayılan olarak HTTP POST. Yan etkileri olmayan ve nadiren veya hiç değişmesiz verileri döndüren bir işlem oluştururken bunun yerine HTTP GET kullanın. ALMA işlemlerinin sonuçları önbelleğe alınabilir. Bu, aynı işleme yapılan birden çok çağrının hizmetinize yalnızca bir istek oluşmasına neden olabileceği anlamına gelir. Önbelleğe alma, WCF tarafından yapılmaz, ancak herhangi bir düzeyde (bir kullanıcının tarayıcısında, bir ara sunucuda ve diğer düzeylerde) gerçekleşebilir. Hizmet performansını artırmak istiyorsanız önbelleğe alma avantajlıdır, ancak veriler sık sık değişirse veya işlem bazı eylemler gerçekleştirdiğinde kabul edilebilir olmayabilir.  
  
 Örneğin, bir kullanıcının müzik kitaplığını yönetmek için hizmet tasarlıyorsanız, sanatçı 'yı kullanarak bir albümün başlık avantajına bağlı olarak sanatçıların bulunduğu bir işlem, ancak kullanıcının kişisel koleksiyonuna bir albüm ekleyen bir işlemin POST kullanması gerekir.  
  
 Önbelleğin ömrünü denetlemek için <xref:System.ServiceModel.Web.OutgoingWebResponseContext> türü kullanın. Örneğin, hava durumu tahminlerini saat olarak güncelleştiren bir hizmet tasarlarken, hizmet kullanıcılarının eski verilere erişmesini engellemek için önbellek süresini bir saat veya daha az olacak şekilde Al ' ı kullanın.  
  
 Betik Yöneticisi denetimini kullanan bir ASP.NET AJAX sayfasından hizmetleri kullanırken, komut dosyası Yöneticisi mekanizması işlemin GET veya POST işlemini kullanıp kullanmadığını fark etmeksizin, doğru istek türünün verilmemesini sağlar.  
  
 HTTP GET işlemleri, karmaşık veri sözleşmesi türleri de dahil olmak üzere POST işlemleri tarafından desteklenen tüm giriş parametrelerini kullanır. Ancak çoğu durumda, alma işlemleri için çok karmaşık olan çok fazla parametre veya parametre kullanmaktan kaçınmak, çünkü önbelleğe alma verimliliğini düşürür.  
  
 Bu konu başlığı altında, <xref:System.ServiceModel.Web.WebGetAttribute> hizmet sözleşmesindeki ilgili işlemlere veya <xref:System.ServiceModel.Web.WebInvokeAttribute> özniteliklerini ekleyerek al ve postala arasında nasıl seçim yapılacağı gösterilmektedir. Hizmeti çalıştırmak için gerekli diğer adımlar (hizmeti uygulamak, yapılandırmak ve barındırmak), WCF 'de herhangi bir ASP.NET AJAX hizmeti tarafından kullanılanlarla benzerdir.  
  
 İle işaretlenen bir işlem, <xref:System.ServiceModel.Web.WebGetAttribute> her zaman bir get isteği kullanır. Ya da iki özniteliği ile <xref:System.ServiceModel.Web.WebInvokeAttribute>işaretlenmemiş bir işlem, bir post isteği kullanır. , <xref:System.ServiceModel.Web.WebInvokeAttribute> Özelliği<xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> aracılığıyla al ve postala (put ve DELETE gibi) dışında diğer http fiillerinin kullanılmasına izin verir. Ancak, bu fiiller ASP.NET AJAX tarafından desteklenmez. Hizmeti betik Yöneticisi denetimini kullanarak ASP.net sayfalarından kullanmayı düşünüyorsanız, <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> özelliğini kullanmayın.  
  
 GET 'e geçiş yapma örneği için bkz. [Temel AJAX Hizmeti](../../../../docs/framework/wcf/samples/basic-ajax-service.md) örneği.  
  
 POST kullanan bir örnek için bkz. [http post örneği kullanılarak AJAX Hizmeti](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) .  
  
## <a name="to-create-a-wcf-service-that-responds-to-http-get-or-http-post-requests"></a>HTTP GET veya HTTP POST isteklerine yanıt veren bir WCF hizmeti oluşturmak için
  
1. <xref:System.ServiceModel.ServiceContractAttribute> Özniteliği ile işaretlenmiş bir arabirimle birlikte temel bir WCF hizmeti sözleşmesi tanımlayın. Her işlemi ile <xref:System.ServiceModel.OperationContractAttribute>işaretleyin. Bir işlemin http get isteklerine yanıt vermesi gereken belirtmek özniteliğiniekleyin.<xref:System.ServiceModel.Web.WebGetAttribute> Ayrıca, http post ' <xref:System.ServiceModel.Web.WebInvokeAttribute> ı varsayılan olarak belirtmek için özniteliğini veya bir özniteliği belirtmeyeceğinizi de ekleyebilirsiniz.
  
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
  
2. Hizmet sözleşmesini bir `MusicService`ile uygulayın. `IMusicService`
  
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
  
3. Uygulamada. svc uzantısıyla yeni bir dosya adlı hizmet oluşturun. Hizmet için uygun [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) yönergesi bilgilerini ekleyerek bu dosyayı düzenleyin. ASP.NET AJAX uç noktasını otomatik olarak yapılandırmak için [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) yönergesinde kullanılacağını belirtin. <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>  
  
    ```
    <%@ServiceHost   
        language=c#   
        Debug="true"   
        Service="Microsoft.Ajax.Samples.MusicService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
## <a name="to-call-the-service"></a>Hizmeti çağırmak için  
  
1. Hizmetini, tarayıcıyı kullanarak, herhangi bir istemci kodu olmadan hizmetinizin Al işlemlerini test edebilirsiniz. Örneğin, hizmetiniz `http://example.com/service.svc` adreste yapılandırılmışsa, tarayıcı adres çubuğuna yazarak `http://example.com/service.svc/LookUpArtist?album=SomeAlbum` hizmeti çağırır ve yanıt İndirilme veya görüntülenmesine neden olur.
  
2. GET Operations ile hizmetleri diğer ASP.NET AJAX hizmetleriyle aynı şekilde kullanabilirsiniz. hizmet URL 'sini ASP.NET AJAX betik Yöneticisi denetiminin betikler koleksiyonuna girerek. Bir örnek için bkz. [Temel AJAX Hizmeti](../../../../docs/framework/wcf/samples/basic-ajax-service.md).
  
## <a name="see-also"></a>Ayrıca bkz.

- [ASP.NET AJAX için WCF Hizmetleri Oluşturma](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)
- [Nasıl yapılır: AJAX etkin ASP.NET Web hizmetlerini WCF 'ye geçirme](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
