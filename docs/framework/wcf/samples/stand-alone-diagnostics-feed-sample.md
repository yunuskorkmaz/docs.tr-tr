---
title: Bağımsız Tanılama Akış Örneği
ms.date: 03/30/2017
ms.assetid: d31c6c1f-292c-4d95-8e23-ed8565970ea5
ms.openlocfilehash: 6b83bda154a76fe10487da00359e0ceace8ce8cb
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044676"
---
# <a name="stand-alone-diagnostics-feed-sample"></a>Bağımsız Tanılama Akış Örneği
Bu örnek, Windows Communication Foundation (WCF) ile dağıtım için bir RSS/Atom akışının nasıl oluşturulacağını gösterir. Nesne modelinin temellerini ve bir Windows Communication Foundation (WCF) hizmeti üzerinde ayarlamayı gösteren temel bir "Merhaba Dünya" programıdır.  
  
 WCF, <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>özel bir veri türü döndüren hizmet işlemleri olarak genel yayımlama akışlarını modeller. Örnekleri, bir akışı hem RSS 2,0 hem de Atom 1,0 biçimlerine seri hale getirebilirsiniz.<xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> Aşağıdaki örnek kodda kullanılan sözleşme gösterilmektedir.  
  
```  
[ServiceContract(Namespace = "")]  
    interface IDiagnosticsService  
    {  
        [OperationContract]  
        //The [WebGet] attribute controls how WCF dispatches  
        //HTTP requests to service operations based on a URI suffix  
        //(the part of the request URI after the endpoint address)  
        //using the HTTP GET method. The UriTemplate specifies a relative  
        //path of 'feed', and specifies that the format is  
        //supplied using a query string.   
        [WebGet(UriTemplate="feed?format={format}")]  
        [ServiceKnownType(typeof(Atom10FeedFormatter))]  
        [ServiceKnownType(typeof(Rss20FeedFormatter))]  
        SyndicationFeedFormatter GetProcesses(string format);  
    }  
```  
  
 Bu işlem, WCF 'nin hizmet <xref:System.ServiceModel.Web.WebGetAttribute> işlemlerine http get isteklerini nasıl dağıtmakta olduğunu denetlemenizi ve gönderilen iletilerin biçimini belirlemenizi sağlayan özniteliğiyle birlikte açıklanmış. `GetProcesses`  
  
 Herhangi bir WCF hizmeti gibi, dağıtım akışları da herhangi bir yönetilen uygulamada barındırılabilir. Dağıtım Hizmetleri, doğru şekilde çalışması için belirli <xref:System.ServiceModel.WebHttpBinding>bir bağlama () ve belirli bir uç <xref:System.ServiceModel.Description.WebHttpBehavior>nokta davranışı () gerektirir. Yeni <xref:System.ServiceModel.Web.WebServiceHost> sınıf, belirli bir yapılandırma olmadan bu tür uç noktaları oluşturmak için uygun bir API sağlar.  
  
```  
WebServiceHost host = new WebServiceHost(typeof(ProcessService), new Uri("http://localhost:8000/diagnostics"));  
  
            //The WebServiceHost will automatically provide a default endpoint at the base address  
            //using the proper binding (the WebHttpBinding) and endpoint behavior (the WebHttpBehavior)  
```  
  
 Alternatif olarak, eşdeğer işlevselliği <xref:System.ServiceModel.Activation.WebServiceHostFactory> sağlamak için IIS tarafından barındırılan bir. svc dosyası içinden kullanabilirsiniz (Bu teknik, bu örnek kodda gösterilmez).  
  
```  
<%@ ServiceHost Language="C#|VB" Debug="true" Service="ProcessService" %>  
```  
  
 Bu hizmet, standart HTTP GET kullanarak istekleri aldığından, hizmete erişmek için herhangi bir RSS veya ATOM kullanan istemci kullanabilirsiniz. Örneğin, RSS kullanan bir tarayıcıda `http://localhost:8000/diagnostics/feed/?format=atom` veya `http://localhost:8000/diagnostics/feed/?format=rss` ' a giderek bu hizmetin çıkışını görüntüleyebilirsiniz.
  
 Ayrıca, dağıtılmış verileri okumak ve bunu zorunlu kodla işlemek için [WCF dağıtım nesnesi modelinin atom ve RSS 'ye nasıl eşlendiğini](../../../../docs/framework/wcf/feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md) de kullanabilirsiniz.  
  
```  
XmlReader reader = XmlReader.Create( "http://localhost:8000/diagnostics/feed/?format=rss",  
new XmlReaderSettings()  
{  
//MaxCharactersInDocument can be used to control the maximum amount of data   
//read from the reader and helps prevent OutOfMemoryException  
MaxCharactersInDocument = 1024 * 64  
} );  
  
SyndicationFeed feed = SyndicationFeed.Load( reader );  
  
foreach (SyndicationItem i in feed.Items)  
{  
        XmlSyndicationContent content = i.Content as XmlSyndicationContent;  
        ProcessData pd = content.ReadContent<ProcessData>();  
  
        Console.WriteLine(i.Title.Text);  
        Console.WriteLine(pd.ToString());  
}  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik kurulum yordamında](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)bulunan yönergeleri ayarlama bölümünde açıklandığı gibi, bilgisayarda http ve https için doğru adres kayıt iznine sahip olduğunuzdan emin olun.  
  
2. Çözümü oluşturun.  
  
3. Konsol uygulamasını çalıştırın.  
  
4. Konsol uygulaması çalışırken, RSS kullanan bir tarayıcıya gidin `http://localhost:8000/diagnostics/feed/?format=atom` veya `http://localhost:8000/diagnostics/feed/?format=rss` bu tarayıcıyı kullanın.  
  
> [!IMPORTANT]
> Örnekler bilgisayarınızda zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\DiagnosticsFeed`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Web HTTP Programlama Modeli](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [WCF Dağıtımı](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)
