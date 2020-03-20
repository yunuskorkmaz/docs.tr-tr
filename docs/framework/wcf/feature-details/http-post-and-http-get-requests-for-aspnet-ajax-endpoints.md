---
title: 'Nasıl yapılır: ASP.NET AJAX Uç Noktaları için HTTP POST ve HTTP GET İstekleri Arasında Seçim Yapma'
ms.date: 03/30/2017
ms.assetid: b47de82a-4c92-4af6-bceb-a5cb8bb8ede9
ms.openlocfilehash: 0f7a221d1fd14b4a978683f008858e35cbd2df19
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184751"
---
# <a name="how-to-choose-between-http-post-and-http-get-requests-for-aspnet-ajax-endpoints"></a>Nasıl yapılır: ASP.NET AJAX Uç Noktaları için HTTP POST ve HTTP GET İstekleri Arasında Seçim Yapma

Windows Communication Foundation (WCF), istemci Web sitesinde JavaScript'ten çağrılabilen AJAX özellikli ASP.NET bir bitiş noktasını ortaya çıkaran bir hizmet oluşturmanıza olanak tanır. Bu tür hizmetleri oluşturmak için temel yordamlar [nasıl tartışılır: ASP.NET bir AJAX Bitiş Noktası Eklemek için Yapılandırmayı Kullanın](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) ve Nasıl [Yapılır: Yapılandırmayı Kullanmadan ASP.NET bir AJAX Bitiş Noktası Ekleyin.](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md)  
  
 ASP.NET AJAX, HTTP POST ve HTTP GET fiillerini kullanan işlemleri destekler ve http post varsayılan dır. Hiçbir yan etkisi olmayan ve nadiren veya hiç değişmeyen verileri döndüren bir işlem oluştururken, bunun yerine HTTP GET'i kullanın. GET işlemlerinin sonuçları önbelleğe alınabilir, bu da aynı işlemi birden çok aramanın hizmetinize yalnızca bir istekle sonuçlanabileceği anlamına gelir. Önbelleğe alma WCF tarafından yapılmaz, ancak herhangi bir düzeyde (kullanıcının tarayıcısında, proxy sunucusunda ve diğer düzeylerde) gerçekleşebilir. Hizmet performansını artırmak istiyorsanız önbelleğe alma avantajlıdır, ancak veriler sık sık değişirse veya işlem bazı eylemlergerçekleştirirse kabul edilebilir olmayabilir.  
  
 Örneğin, bir kullanıcının müzik kitaplığını yönetmek için hizmet tasarlıyorsanız, bir albümün başlığına göre sanatçıyı arayan bir işlem GET'i kullanmanın avantajlarından yararlanır, ancak kullanıcının kişisel koleksiyonuna albüm ekleyen bir işlem POST'u kullanmalıdır.  
  
 Önbelleğin kullanım ömrünü denetlemek <xref:System.ServiceModel.Web.OutgoingWebResponseContext> için türü kullanın. Örneğin, hava durumu tahminlerini saatlik olarak güncelleştiren bir hizmet tasarlarken, HIZMET kullanıcılarının eski verilere erişmesini önlemek için GET'i ancak önbellek süresini bir saat veya daha az ile sınırlandırırsınız.  
  
 Komut Dosyası Yöneticisi denetimini kullanan ASP.NET bir AJAX sayfasından gelen hizmetleri kullanırken, işlemin GET veya POST'u kullanıp kullanmadığı fark etmez - komut dosyası yöneticisi mekanizması doğru istek türünün verilmesini sağlar.  
  
 HTTP GET işlemleri, karmaşık veri sözleşmesi türleri de dahil olmak üzere POST işlemleri tarafından desteklenen tüm giriş parametrelerini kullanır. Ancak, çoğu durumda önbelleğe alma verimliliğini azalttığı için GET işlemlerinde çok karmaşık olan çok fazla parametre veya parametreden kaçınmak önerilir.  
  
 Bu konu, hizmet sözleşmesindeki ilgili işlemlere <xref:System.ServiceModel.Web.WebGetAttribute> <xref:System.ServiceModel.Web.WebInvokeAttribute> veya öznitelikleri ekleyerek GET ve POST arasında nasıl seçim yapılacağını gösterir. Hizmeti çalıştırmak için gereken diğer adımlar (hizmeti uygulamak, yapılandırmak ve barındırmak için), WCF'deki herhangi bir ASP.NET AJAX hizmeti tarafından kullanılanlara benzer.  
  
 <xref:System.ServiceModel.Web.WebGetAttribute> Her zaman GET isteği yle işaretlenmiş bir işlem kullanır. <xref:System.ServiceModel.Web.WebInvokeAttribute>'ile işaretlenmiş veya iki özetmenle işaretlenmemiş bir işlem, bir POST isteği kullanır. Özellik <xref:System.ServiceModel.Web.WebInvokeAttribute> aracılığıyla <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> GET ve POST (PUT ve DELETE gibi) dışındaki diğer HTTP fiillerinin kullanımına izin verir. Ancak bu fiiller ASP.NET AJAX tarafından desteklenmemektedir. Komut Dosyası Yöneticisi denetimini kullanarak ASP.NET sayfadaki hizmeti kullanmak <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> istiyorsanız, özelliği kullanmayın.  
  
 GET'e geçiş için çalışan bir örnek için [Temel AJAX Hizmeti](../../../../docs/framework/wcf/samples/basic-ajax-service.md) örneğine bakın.  
  
 POST kullanan bir örnek [için, HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) örneğini kullanarak AJAX Hizmeti'ne bakın.  
  
## <a name="to-create-a-wcf-service-that-responds-to-http-get-or-http-post-requests"></a>HTTP GET veya HTTP POST isteklerine yanıt veren bir WCF hizmeti oluşturmak için
  
1. Öznitelik ile işaretlenmiş bir arabirim ile <xref:System.ServiceModel.ServiceContractAttribute> temel bir WCF hizmet sözleşmesi tanımlayın. Her işlemi <xref:System.ServiceModel.OperationContractAttribute>. <xref:System.ServiceModel.Web.WebGetAttribute> Bir işlemin HTTP GET isteklerine yanıt vermesi gerektiğini şart koşturacak özniteliği ekleyin. Ayrıca, HTTP <xref:System.ServiceModel.Web.WebInvokeAttribute> POST'u açıkça belirtmek için öznitelik ekleyebilir veya HTTP POST varsayılan bir öznitelik belirtemezsiniz.
  
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
  
2. Bir `IMusicService` `MusicService`ile hizmet sözleşmesi uygulayın.
  
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
  
3. Uygulamada .svc uzantısı bulunan hizmet adlı yeni bir dosya oluşturun. Hizmet için uygun [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) yönergesi bilgilerini ekleyerek bu dosyayı düzenleyin. <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> ASP.NET bir AJAX bitiş noktasını otomatik olarak yapılandırmak için [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) yönergesinde kullanılacağını belirtin.  
  
    ```
    <%@ServiceHost
        language=c#
        Debug="true"
        Service="Microsoft.Ajax.Samples.MusicService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
## <a name="to-call-the-service"></a>Hizmeti aramak için  
  
1. Tarayıcıyı kullanarak hizmetinizin GET işlemlerini herhangi bir istemci kodu olmadan test edebilirsiniz. Örneğin, hizmetiniz `http://example.com/service.svc` adreste yapılandırılırsa, `http://example.com/service.svc/LookUpArtist?album=SomeAlbum` tarayıcı adresi çubuğuna yazmak hizmeti çağırır ve yanıtın indirilmesine veya görüntülenmesine neden olur.
  
2. GET işlemlerindeki hizmetleri, ASP.NET AJAX Script Manager denetiminin Scripts koleksiyonuna hizmet URL'sini girerek, diğer ASP.NET AJAX hizmetleriyle aynı şekilde kullanabilirsiniz. Örneğin, [Temel AJAX Hizmeti'ne](../../../../docs/framework/wcf/samples/basic-ajax-service.md)bakın.
  
## <a name="see-also"></a>Ayrıca bkz.

- [ASP.NET AJAX için WCF Hizmetleri Oluşturma](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)
- [Nasıl yapılır: AJAX Etkinleştirilmiş ASP.NET Web Hizmetlerini WCF'ye Taşıma](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
