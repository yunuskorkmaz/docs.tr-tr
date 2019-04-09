---
title: Bağımsız Tanılama Akış Örneği
ms.date: 03/30/2017
ms.assetid: d31c6c1f-292c-4d95-8e23-ed8565970ea5
ms.openlocfilehash: 841bcd38516251fe1de306cbf52371d027b8cb36
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59102147"
---
# <a name="stand-alone-diagnostics-feed-sample"></a>Bağımsız Tanılama Akış Örneği
Bu örnek, bir RSS/Atom sendikasyonu Windows Communication Foundation (WCF) ile akış oluşturma işlemini gösterir. Nesne modeli temellerini ve Windows Communication Foundation (WCF) hizmet üzerinde ayarlanan gösterilmektedir temel bir "Merhaba Dünya" programı var.  
  
 WCF dağıtım akışlarını döndüren özel veri türü, hizmet işlemleri modeller <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>. Örneklerini <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> RSS 2.0 ve Atom 1.0 biçimleri akışa serileştirebiliyorsa. Aşağıdaki örnek kod kullanılan sözleşme gösterir.  
  
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
  
 `GetProcesses` İşlemi ile ek açıklamalı <xref:System.ServiceModel.Web.WebGetAttribute> nasıl WCF HTTP GET gönderir denetlemenize olanak sağlayan öznitelik istekleri hizmet işlemlerine ve gönderilen iletilerin biçimini belirtmek için.  
  
 Herhangi bir WCF hizmeti gibi kendi kendine yönetilen bir uygulamada bulunan dağıtım akışlarını olabilir. Dağıtım Hizmetleri özel bir bağlama gerektirir ( <xref:System.ServiceModel.WebHttpBinding>) ve belirli bir uç nokta davranışı ( <xref:System.ServiceModel.Description.WebHttpBehavior>) düzgün çalışabilmesi için. Yeni <xref:System.ServiceModel.Web.WebServiceHost> sınıfı, belirli bir yapılandırma olmadan bu uç noktaları oluşturmak için uygun bir API sağlar.  
  
```  
WebServiceHost host = new WebServiceHost(typeof(ProcessService), new Uri("http://localhost:8000/diagnostics"));  
  
            //The WebServiceHost will automatically provide a default endpoint at the base address  
            //using the proper binding (the WebHttpBinding) and endpoint behavior (the WebHttpBehavior)  
```  
  
 Alternatif olarak, <xref:System.ServiceModel.Activation.WebServiceHostFactory> gelen bir IIS tarafından barındırılan .svc dosyasında (Bu tekniği Bu örnek kodu değil de gösterilmiştir) eşdeğer bir işlevselliği sağlamak için.  
  
```  
<%@ ServiceHost Language="C#|VB" Debug="true" Service="ProcessService" %>  
```  
  
 Bu hizmeti kullanarak standart HTTP GET isteklerini aldığından, hizmete erişmek için herhangi bir RSS veya ATOM algılayan İstemcisi'ni kullanabilirsiniz. Giderek bu hizmet çıktısı gibi görüntüleyebilirsiniz `http://localhost:8000/diagnostics/feed/?format=atom` veya `http://localhost:8000/diagnostics/feed/?format=rss` RSS uyumlu bir tarayıcıda.
  
 Ayrıca [nasıl WCF dağıtım nesnesi modeli eşlenir Atom ve RSS](../../../../docs/framework/wcf/feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md) Dağıtılmış veri okuyup kesin kod kullanarak işleyin.  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Kurulum yönergelerinde açıklandığı gibi bilgisayarı HTTP ve HTTPS için doğru adres kayıt izni olduğundan emin olun [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözümü oluşturun.  
  
3.  Konsol uygulamasını çalıştırın.  
  
4.  Konsol uygulaması çalışırken gidin `http://localhost:8000/diagnostics/feed/?format=atom` veya `http://localhost:8000/diagnostics/feed/?format=rss` RSS uyumlu bir tarayıcı kullanarak.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\DiagnosticsFeed`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Web HTTP Programlama Modeli](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [WCF Dağıtımı](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)
