---
title: Bağımsız Tanılama Akış Örneği
ms.date: 03/30/2017
ms.assetid: d31c6c1f-292c-4d95-8e23-ed8565970ea5
ms.openlocfilehash: 29d8caee48925040db9f1812f015870e3a1272bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144012"
---
# <a name="stand-alone-diagnostics-feed-sample"></a>Bağımsız Tanılama Akış Örneği
Bu örnek, Windows Communication Foundation (WCF) ile sendikasyon için bir RSS/Atom beslemesi oluşturmanın nasıl olduğunu göstermektedir. Nesne modelinin temellerini ve windows communication foundation (WCF) hizmetinde nasıl kurulabildiğini gösteren temel bir "Hello World" programıdır.  
  
 WCF modelleri sendikasyon akışları özel bir veri türünü <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>döndüren hizmet işlemleri olarak, . RsS <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> 2.0 ve Atom 1.0 biçimlerine bir akışı serihale getirebilirsiniz. Aşağıdaki örnek kod, kullanılan sözleşmeyi gösterir.  
  
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
  
 İşlem, `GetProcesses` WCF'nin http <xref:System.ServiceModel.Web.WebGetAttribute> GET isteklerini hizmet işlemlerine nasıl gönderdiğini denetlemenize ve gönderilen iletilerin biçimini belirtmenize olanak tanıyan öznitelikle açıklamalı olarak açıklanır.  
  
 Herhangi bir WCF hizmeti gibi, sendikasyon akışları da yönetilen herhangi bir uygulamada kendi kendine barındırılabilir. Sendikasyon hizmetleri, düzgün çalışması <xref:System.ServiceModel.WebHttpBinding>için belirli bir bağlama (the) ve belirli bir bitiş noktası davranışı (the) <xref:System.ServiceModel.Description.WebHttpBehavior>gerektirir. Yeni <xref:System.ServiceModel.Web.WebServiceHost> sınıf, belirli yapılandırma olmadan bu tür uç noktaları oluşturmak için kullanışlı bir API sağlar.  
  
```csharp  
WebServiceHost host = new WebServiceHost(typeof(ProcessService), new Uri("http://localhost:8000/diagnostics"));  
  
            //The WebServiceHost will automatically provide a default endpoint at the base address  
            //using the proper binding (the WebHttpBinding) and endpoint behavior (the WebHttpBehavior)  
```  
  
 Alternatif olarak, eşdeğer <xref:System.ServiceModel.Activation.WebServiceHostFactory> işlevsellik sağlamak için IIS tarafından barındırılan .svc dosyasının içinden kullanabilirsiniz (bu teknik bu örnek kodda gösterilmez).  
  
```xml
<%@ ServiceHost Language="C#|VB" Debug="true" Service="ProcessService" %>
```
  
 Bu hizmet, HTTP GET standardını kullanarak istek aldığından, hizmete erişmek için herhangi bir RSS veya ATOM'a duyarlı istemcik kullanabilirsiniz. Örneğin, RSS'ye duyarlı bir tarayıcıda `http://localhost:8000/diagnostics/feed/?format=atom` veya `http://localhost:8000/diagnostics/feed/?format=rss` bu hizmetin çıktısını görüntüleyebilirsiniz.
  
 Ayrıca, sendikasyon verilerini okumak ve zorunlu kodu kullanarak işlemek [için WCF Sendikasyon Nesnesi Model Eşlerini Atom ve RSS'ye nasıl](../../../../docs/framework/wcf/feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md) kullanabilirsiniz.  
  
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
  
## <a name="set-up-build-and-run-the-sample"></a>Örneği ayarlama, oluşturma ve çalıştırma
  
1. Windows Communication Foundation Samples için [Tek Seferlik Kurulum Prosedürü'nde](one-time-setup-procedure-for-the-wcf-samples.md)belirtilen şekilde bilgisayarda HTTP ve HTTPS için doğru adres kayıt iznine sahip olduğundan emin olun.

2. Çözümü derleyin.

3. Konsol uygulamasını çalıştırın.

4. Konsol uygulaması çalışırken, RSS'ye duyarlı bir tarayıcıya `http://localhost:8000/diagnostics/feed/?format=atom` gidin veya `http://localhost:8000/diagnostics/feed/?format=rss` bu tarayıcıyı kullanarak gidin.

> [!IMPORTANT]
> Örnekler bilgisayarınıza zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\DiagnosticsFeed`

## <a name="see-also"></a>Ayrıca bkz.

- [WCF Web HTTP Programlama Modeli](../feature-details/wcf-web-http-programming-model.md)
- [WCF Dağıtımı](../feature-details/wcf-syndication.md)
