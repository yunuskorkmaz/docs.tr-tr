---
title: 'Nasıl yapılır: ASP.NET AJAX Uç Noktaları için HTTP POST ve HTTP GET İstekleri Arasında Seçim Yapma'
ms.date: 03/30/2017
ms.assetid: b47de82a-4c92-4af6-bceb-a5cb8bb8ede9
ms.openlocfilehash: c74b1acdf3802ab680123cd9d676919fe47236e8
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: tr-TR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051590"
---
# <a name="how-to-choose-between-http-post-and-http-get-requests-for-aspnet-ajax-endpoints"></a>Nasıl yapılır: ASP.NET AJAX Uç Noktaları için HTTP POST ve HTTP GET İstekleri Arasında Seçim Yapma

Windows Communication Foundation (WCF), istemci Web sitesinde JavaScript 'ten çağrılabilen ASP.NET AJAX özellikli bir uç nokta sunan bir hizmet oluşturmanıza olanak sağlar. Bu tür hizmetleri oluşturmaya yönelik temel yordamlar, [nasıl yapılır: ASP.NET AJAX uç noktası eklemek Için yapılandırma kullanma](how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) ve [nasıl yapılır: yapılandırma kullanmadan ASP.NET AJAX uç noktası ekleme](how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md)konusunda ele alınmıştır.  
  
 ASP.NET AJAX, HTTP POST ve HTTP GET fiillerini kullanan işlemleri destekler, varsayılan olarak HTTP POST. Yan etkileri olmayan ve nadiren veya hiç değişmesiz verileri döndüren bir işlem oluştururken bunun yerine HTTP GET kullanın. ALMA işlemlerinin sonuçları önbelleğe alınabilir. Bu, aynı işleme yapılan birden çok çağrının hizmetinize yalnızca bir istek oluşmasına neden olabileceği anlamına gelir. Önbelleğe alma, WCF tarafından yapılmaz, ancak herhangi bir düzeyde (bir kullanıcının tarayıcısında, bir ara sunucuda ve diğer düzeylerde) gerçekleşebilir. Hizmet performansını artırmak istiyorsanız önbelleğe alma avantajlıdır, ancak veriler sık sık değişirse veya işlem bazı eylemler gerçekleştirdiğinde kabul edilebilir olmayabilir.  
  
 Örneğin, bir kullanıcının müzik kitaplığını yönetmek için hizmet tasarlıyorsanız, sanatçı 'yı kullanarak bir albümün başlık avantajına bağlı olarak sanatçıların bulunduğu bir işlem, ancak kullanıcının kişisel koleksiyonuna bir albüm ekleyen bir işlemin POST kullanması gerekir.  
  
 Önbelleğin ömrünü denetlemek için <xref:System.ServiceModel.Web.OutgoingWebResponseContext> türü kullanın. Örneğin, hava durumu tahminlerini saat olarak güncelleştiren bir hizmet tasarlarken, hizmet kullanıcılarının eski verilere erişmesini engellemek için önbellek süresini bir saat veya daha az olacak şekilde Al ' ı kullanın.  
  
 Betik Yöneticisi denetimini kullanan bir ASP.NET AJAX sayfasından hizmetleri kullanırken, komut dosyası Yöneticisi mekanizması işlemin GET veya POST işlemini kullanıp kullanmadığını fark etmeksizin, doğru istek türünün verilmemesini sağlar.  
  
 HTTP GET işlemleri, karmaşık veri sözleşmesi türleri de dahil olmak üzere POST işlemleri tarafından desteklenen tüm giriş parametrelerini kullanır. Ancak çoğu durumda, alma işlemleri için çok karmaşık olan çok fazla parametre veya parametre kullanmaktan kaçınmak, çünkü önbelleğe alma verimliliğini düşürür.  
  
 Bu konu başlığı altında, <xref:System.ServiceModel.Web.WebGetAttribute> <xref:System.ServiceModel.Web.WebInvokeAttribute> hizmet sözleşmesindeki ilgili işlemlere veya ÖZNITELIKLERINI ekleyerek al ve postala arasında nasıl seçim yapılacağı gösterilmektedir. Hizmeti çalıştırmak için gerekli diğer adımlar (hizmeti uygulamak, yapılandırmak ve barındırmak), WCF 'de herhangi bir ASP.NET AJAX hizmeti tarafından kullanılanlarla benzerdir.  
  
 İle işaretlenen bir işlem, <xref:System.ServiceModel.Web.WebGetAttribute> her zaman BIR get isteği kullanır. Ya da iki özniteliği ile işaretlenmemiş bir işlem, <xref:System.ServiceModel.Web.WebInvokeAttribute> BIR post isteği kullanır. , <xref:System.ServiceModel.Web.WebInvokeAttribute> Özelliği aracılığıyla al ve postala (put ve DELETE gibi) dışında DIĞER http fiillerinin kullanılmasına izin verir <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> . Ancak, bu fiiller ASP.NET AJAX tarafından desteklenmez. Hizmeti betik Yöneticisi denetimini kullanarak ASP.NET sayfalarından kullanmayı düşünüyorsanız, <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> özelliğini kullanmayın.  
  
 GET 'e geçiş yapma örneği için bkz. [Temel AJAX Hizmeti](../samples/basic-ajax-service.md) örneği.  
  
 POST kullanan bir örnek için bkz. [http post örneği kullanılarak AJAX Hizmeti](../samples/ajax-service-using-http-post.md) .  
  
## <a name="to-create-a-wcf-service-that-responds-to-http-get-or-http-post-requests"></a>HTTP GET veya HTTP POST isteklerine yanıt veren bir WCF hizmeti oluşturmak için
  
1. Özniteliği ile işaretlenmiş bir arabirimle birlikte temel bir WCF hizmeti sözleşmesi tanımlayın <xref:System.ServiceModel.ServiceContractAttribute> . Her işlemi ile işaretleyin <xref:System.ServiceModel.OperationContractAttribute> . <xref:System.ServiceModel.Web.WebGetAttribute>Bir işlemin http get isteklerine yanıt vermesi gereken belirtmek özniteliğini ekleyin. Ayrıca, http post <xref:System.ServiceModel.Web.WebInvokeAttribute> ' ı varsayılan olarak belirtmek için özniteliğini veya bir özniteliği belirtmeyeceğinizi de ekleyebilirsiniz.
  
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
  
2. `IMusicService`Hizmet sözleşmesini bir ile uygulayın `MusicService` .
  
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
  
3. Uygulamada. svc uzantısıyla yeni bir dosya adlı hizmet oluşturun. Hizmet için uygun [ \@ ServiceHost](../../configure-apps/file-schema/wcf-directive/servicehost.md) yönergesi bilgilerini ekleyerek bu dosyayı düzenleyin. <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>ASP.NET AJAX uç noktasını otomatik olarak yapılandırmak için [ \@ ServiceHost](../../configure-apps/file-schema/wcf-directive/servicehost.md) yönergesinde kullanılacağını belirtin.  
  
    ```aspx-csharp
    <%@ServiceHost
        language=c#
        Debug="true"
        Service="Microsoft.Ajax.Samples.MusicService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
## <a name="to-call-the-service"></a>Hizmeti çağırmak için  
  
1. Hizmetini, tarayıcıyı kullanarak, herhangi bir istemci kodu olmadan hizmetinizin Al işlemlerini test edebilirsiniz. Örneğin, hizmetiniz `http://example.com/service.svc` adreste yapılandırılmışsa, `http://example.com/service.svc/LookUpArtist?album=SomeAlbum` tarayıcı adres çubuğuna yazarak hizmeti çağırır ve yanıt İndirilme veya görüntülenmesine neden olur.
  
2. GET Operations ile hizmetleri diğer ASP.NET AJAX hizmetleriyle aynı şekilde kullanabilirsiniz. hizmet URL 'sini ASP.NET AJAX betik Yöneticisi denetiminin betikler koleksiyonuna girerek. Bir örnek için bkz. [Temel AJAX Hizmeti](../samples/basic-ajax-service.md).
  
## <a name="see-also"></a>Ayrıca bkz.

- [ASP.NET AJAX için WCF Hizmetleri Oluşturma](creating-wcf-services-for-aspnet-ajax.md)
- [Nasıl yapılır: AJAX Etkinleştirilmiş ASP.NET Web Hizmetlerini WCF'ye Taşıma](how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
