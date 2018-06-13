---
title: Bağımsız Tanılama Akış Örneği
ms.date: 03/30/2017
ms.assetid: d31c6c1f-292c-4d95-8e23-ed8565970ea5
ms.openlocfilehash: 730cf011208ea1b57929fff4a1953fd3a935335c
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33807765"
---
# <a name="stand-alone-diagnostics-feed-sample"></a>Bağımsız Tanılama Akış Örneği
Bu örnek nasıl dağıtım Windows Communication Foundation (WCF) için akış RSS/Atom oluşturulacağını gösterir. Bu nesne modeli temelleri ve Windows Communication Foundation (WCF) hizmetini üzerinde ayarlamak nasıl gösteren temel bir "Hello World" programıdır.  
  
 WCF özel veri türü döndüren hizmet işlemleri dağıtım akışlarını modeller <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>. Örneklerini <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> RSS 2.0 ve Atom 1.0 biçimleri akışa seri hale getirebilir. Aşağıdaki örnek kod kullanılan sözleşme gösterir.  
  
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
  
 `GetProcesses` İşlemi açıklama ile <xref:System.ServiceModel.Web.WebGetAttribute> WCF HTTP GET nasıl dağıtır denetlemenize olanak sağlayan öznitelik istekleri işlemleri hizmet ve gönderilen iletileri biçimini belirtin.  
  
 Herhangi bir WCF hizmeti gibi kendi kendine yönetilen bir uygulamada bulunan dağıtım akışlarını olabilir. Dağıtım Hizmetleri gerektiren belirli bir bağlama ( <xref:System.ServiceModel.WebHttpBinding>) ve belirli uç noktası davranışı ( <xref:System.ServiceModel.Description.WebHttpBehavior>) düzgün çalışabilmesi için. Yeni <xref:System.ServiceModel.Web.WebServiceHost> sınıfı, belirli bir yapılandırma olmadan böyle uç noktaları oluşturmak için uygun bir API sağlar.  
  
```  
WebServiceHost host = new WebServiceHost(typeof(ProcessService), new Uri("http://localhost:8000/diagnostics"));  
  
            //The WebServiceHost will automatically provide a default endpoint at the base address  
            //using the proper binding (the WebHttpBinding) and endpoint behavior (the WebHttpBehavior)  
```  
  
 Alternatif olarak, kullanabileceğiniz <xref:System.ServiceModel.Activation.WebServiceHostFactory> gelen (Bu teknik Bu örnek kodda değil de gösterilmiştir) eşdeğer işlevselliği sağlamak için IIS tarafından barındırılan .svc dosyası içinde.  
  
```  
<%@ ServiceHost Language="C#|VB" Debug="true" Service="ProcessService" %>  
```  
  
 Bu hizmeti kullanan standart HTTP GET istekleri aldığından, hizmete erişmek için herhangi bir RSS veya ATOM algılayan İstemcisi'ni kullanabilirsiniz. Örneğin, bu hizmet çıktısını giderek görüntüleyebileceğiniz http://localhost:8000/diagnostics/feed/?format=atom veya http://localhost:8000/diagnostics/feed/?format=rss Internet Explorer 7 gibi RSS uyumlu bir tarayıcıda.  
  
 Aynı zamanda [nasıl WCF dağıtım nesnesi modeli eşlemeleri Atom ve RSS](../../../../docs/framework/wcf/feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md) Dağıtılmış veri okumak ve kesinlik temelli kodu kullanarak işlemek için.  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  ' Ndaki yönergeleri ayarlama açıklandığı gibi bilgisayarı HTTP ve HTTPS için doğru adres kayıt izni olduğundan emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözümü oluşturun.  
  
3.  Konsol uygulamasını çalıştırın.  
  
4.  Konsol uygulaması çalışırken gidin http://localhost:8000/diagnostics/feed/?format=atom veya http://localhost:8000/diagnostics/feed/?format=rss RSS uyumlu bir tarayıcı kullanarak.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\DiagnosticsFeed`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF Web HTTP Programlama Modeli](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [WCF Dağıtımı](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)
