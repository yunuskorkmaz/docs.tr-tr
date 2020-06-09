---
title: Bağımsız Tanılama Akış Örneği
ms.date: 03/30/2017
ms.assetid: d31c6c1f-292c-4d95-8e23-ed8565970ea5
ms.openlocfilehash: 0402805b7eb5b0b224db32eb07780743e5f32fb3
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600925"
---
# <a name="stand-alone-diagnostics-feed-sample"></a>Bağımsız Tanılama Akış Örneği
Bu örnek, Windows Communication Foundation (WCF) ile dağıtım için bir RSS/Atom akışının nasıl oluşturulacağını gösterir. Nesne modelinin temellerini ve bir Windows Communication Foundation (WCF) hizmeti üzerinde ayarlamayı gösteren temel bir "Merhaba Dünya" programıdır.  
  
 WCF, özel bir veri türü döndüren hizmet işlemleri olarak genel yayımlama akışlarını modeller <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> . Örnekleri <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> , bir akışı hem RSS 2,0 hem de Atom 1,0 biçimlerine seri hale getirebilirsiniz. Aşağıdaki örnek kodda kullanılan sözleşme gösterilmektedir.  
  
```csharp  
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
  
 `GetProcesses`Bu işlem, <xref:System.ServiceModel.Web.WebGetAttribute> WCF 'nin HIZMET IŞLEMLERINE http get isteklerini nasıl dağıtmakta olduğunu denetlemenizi ve gönderilen iletilerin biçimini belirlemenizi sağlayan özniteliğiyle birlikte açıklanmış.  
  
 Herhangi bir WCF hizmeti gibi, dağıtım akışları da herhangi bir yönetilen uygulamada barındırılabilir. Dağıtım Hizmetleri <xref:System.ServiceModel.WebHttpBinding> , <xref:System.ServiceModel.Description.WebHttpBehavior> doğru şekilde çalışması için belirli bir bağlama () ve belirli bir uç nokta davranışı () gerektirir. Yeni <xref:System.ServiceModel.Web.WebServiceHost> sınıf, belirli bir yapılandırma olmadan bu tür uç noktaları oluşturmak için uygun BIR API sağlar.  
  
```csharp  
WebServiceHost host = new WebServiceHost(typeof(ProcessService), new Uri("http://localhost:8000/diagnostics"));  
  
            //The WebServiceHost will automatically provide a default endpoint at the base address  
            //using the proper binding (the WebHttpBinding) and endpoint behavior (the WebHttpBehavior)  
```  
  
 Alternatif olarak, <xref:System.ServiceModel.Activation.WebServiceHostFactory> eşdeğer işlevselliği sağlamak IÇIN IIS tarafından barındırılan bir. svc dosyası içinden kullanabilirsiniz (Bu teknik, bu örnek kodda gösterilmez).  
  
```xml
<% @ServiceHost Language="C#|VB" Debug="true" Service="ProcessService" %>
```
  
 Bu hizmet, standart HTTP GET kullanarak istekleri aldığından, hizmete erişmek için herhangi bir RSS veya ATOM kullanan istemci kullanabilirsiniz. Örneğin, `http://localhost:8000/diagnostics/feed/?format=atom` `http://localhost:8000/diagnostics/feed/?format=rss` RSS kullanan bir tarayıcıda veya ' a giderek bu hizmetin çıkışını görüntüleyebilirsiniz.
  
 Ayrıca, dağıtılmış verileri okumak ve bunu zorunlu kodla işlemek için [WCF dağıtım nesnesi modelinin atom ve RSS 'ye nasıl eşlendiğini](../feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md) de kullanabilirsiniz.  
  
```csharp
XmlReader reader = XmlReader.Create( "http://localhost:8000/diagnostics/feed/?format=rss",
    new XmlReaderSettings()
    {
        //MaxCharactersInDocument can be used to control the maximum amount of data
        //read from the reader and helps prevent OutOfMemoryException
        MaxCharactersInDocument = 1024 * 64
    } );

SyndicationFeed feed = SyndicationFeed.Load(reader);

foreach (SyndicationItem i in feed.Items)
{
    XmlSyndicationContent content = i.Content as XmlSyndicationContent;
    ProcessData pd = content.ReadContent<ProcessData>();

    Console.WriteLine(i.Title.Text);
    Console.WriteLine(pd.ToString());
}
```
  
## <a name="set-up-build-and-run-the-sample"></a>Örneği kurma, oluşturma ve çalıştırma
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik kurulum yordamında](one-time-setup-procedure-for-the-wcf-samples.md)bulunan yönergeleri ayarlama bölümünde açıklandığı gibi, bilgisayarda http ve https için doğru adres kayıt iznine sahip olduğunuzdan emin olun.

2. Çözümü derleyin.

3. Konsol uygulamasını çalıştırın.

4. Konsol uygulaması çalışırken, `http://localhost:8000/diagnostics/feed/?format=atom` `http://localhost:8000/diagnostics/feed/?format=rss` RSS kullanan bir tarayıcıya gidin veya bu tarayıcıyı kullanın.

> [!IMPORTANT]
> Örnekler bilgisayarınızda zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\DiagnosticsFeed`

## <a name="see-also"></a>Ayrıca bkz.

- [WCF Web HTTP Programlama Modeli](../feature-details/wcf-web-http-programming-model.md)
- [WCF Dağıtımı](../feature-details/wcf-syndication.md)
