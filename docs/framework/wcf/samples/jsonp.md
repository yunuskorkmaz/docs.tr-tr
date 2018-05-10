---
title: JSONP
ms.date: 03/30/2017
ms.assetid: c13b4d7b-dac7-4ffd-9f84-765c903511e1
ms.openlocfilehash: 9002597ef662c78b6519ab0c04700cddf7ee3714
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
---
# <a name="jsonp"></a>JSONP
Bu örnek, JSON ile doldurma (JSONP) WCF REST Hizmetleri'nde desteklemek gösterilmiştir. JSONP geçerli belgede oluşturma komut dosyası etiketlerini tarafından etki alanları arası komut çağırmak için kullanılan bir kuraldır. Sonuç belirtilen geri çağırma işlevi döndürülür. JSONP gibi etiketler fikir üzerinde temel `<script src="http://..." >` herhangi bir etki alanından betiklerini değerlendirilebilir ve bu etiketlerin tarafından alınan komut dosyası diğer işlevleri zaten tanımlanabilir içinde bir kapsamı içinde değerlendirilir.  
  
## <a name="demonstrates"></a>Gösteriler  
 Etki alanları arası JSONP ile komut dosyası.  
  
## <a name="discussion"></a>Tartışma  
 Örnek sayfa işlendiği sonra dinamik olarak bir betik bloğu tarayıcıda ekleyen bir Web sayfası içerir. Bu betik bloğu tek bir işleme sahip bir WCF REST hizmeti çağrıları `GetCustomer`. WCF REST hizmeti, bir müşterinin adını ve bir geri çağırma işlevi adı Sarmalanan adresini döndürür. WCF REST hizmeti yanıtladığında Web sayfasına geri çağırma işlevi müşteri verileriyle çağrılır ve geri çağırma işlevi Web sayfasında veri görüntüler. Komut dosyası etiketinin ekleme ve geri çağırma işlevi yürütülmesi ASP.NET AJAX ScriptManager denetimi tarafından otomatik olarak gerçekleştirilir. Kullanım deseni JSONP, aşağıdaki kodda gösterildiği gibi etkinleştirmek için bir satır eklenmesi ile tüm ASP.NET AJAX proxy'leri ile aynıdır:  
  
```csharp  
var proxy = new JsonpAjaxService.CustomerService();  
proxy.set_enableJsonp(true);  
proxy.GetCustomer(onSuccess, onFail, null);  
```  
  
 Hizmet tarafından kullanıldığından Web sayfası WCF REST hizmeti çağırabilirsiniz <xref:System.ServiceModel.Description.WebScriptEndpoint> ile `crossDomainScriptAccessEnabled` kümesine `true`. Bu yapılandırmalar her ikisi de altında Web.config dosyasında yapılması \<system.serviceModel > öğesi.  
  
```xml  
<system.serviceModel>  
  <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>  
  <standardEndpoints>  
    <webScriptEndpoint>  
      <standardEndpoint name="" crossDomainScriptAccessEnabled="true"/>  
    </webScriptEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 ScriptManager hizmetiyle etkileşimi yönetir ve hemen el ile JSONP erişim uygulama karmaşıklığını gizler. Zaman `crossDomainScriptAccessEnabled` ayarlanır `true` ve bir işlem yanıt biçimi JSON, WCF altyapı URI isteği bir geri çağırma sorgu dizesi parametresinin değerini inceler ve geri çağırma sorgu dizesi değeri ile JSON yanıt sarmalar parametre. Örnekte, aşağıdaki URI ile WCF REST hizmeti Web sayfasını çağırır.  
  
```  
http://localhost:33695/CustomerService/GetCustomer?callback=Sys._json0  
```  
  
 Geri çağırma sorgu dizesi parametresinin değerini içerdiğinden `JsonPCallback`, WCF hizmeti aşağıdaki örnekte gösterildiği bir JSONP yanıtı döndürür.  
  
```  
Sys._json0({"__type":"Customer:#Microsoft.Samples.Jsonp","Address":"1 Example Way","Name":"Bob"});  
```  
  
 Bu JSONP yanıt, istenen Web sayfasının geri çağırma işlevi adıyla Sarmalanan JSON olarak biçimlendirilmiş müşteri verilerini içerir. ScriptManager etki alanları arası istek gerçekleştirmek için bir komut dosyası etiketini kullanarak bu geri çağırma yürütün ve sonra ASP.NET AJAX proxy GetCustomer çalışması için geçirilen onSuccess işleyicisine sonucu geçirin.  
  
 Örnek iki ASP.NET web uygulamalarının oluşur: biri yalnızca bir WCF hizmeti ve başka bir hizmeti çağıran .aspx Web sayfası içerir. Çözüm çalıştırırken [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] farklı bağlantı noktaları üzerindeki iki Web siteleri, burada hizmet ve istemci Canlı farklı etki alanlarında bir ortam oluşturur barındıracak.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\JSONP`  
  
#### <a name="to-run-the-sample"></a>Örnek çalıştırmak için  
  
1.  Çözüm için JSONP örneği açın.  
  
2.  Başlatmak için F5 tuşuna basın `http://localhost:26648/JSONPClientPage.aspx` tarayıcıda.  
  
3.  Sayfa yüklendikten sonra "Name" ve "Adres" için metin girişleri değerlerle doldurulur dikkat edin.  Sayfa işleme tarayıcı tamamladıktan sonra bu değerler WCF Hizmeti çağrısından sağlanmadı.
