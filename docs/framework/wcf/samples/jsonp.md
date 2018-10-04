---
title: JSONP
ms.date: 03/30/2017
ms.assetid: c13b4d7b-dac7-4ffd-9f84-765c903511e1
ms.openlocfilehash: 0e284ee6cce4ab513c03e7be402cc9c0f0c4ee1a
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48581920"
---
# <a name="jsonp"></a>JSONP
Bu örnek JSON ile doldurma (JSONP) WCF REST Hizmetleri destekleyecek şekilde nasıl gösterir. JSONP geçerli belgedeki oluşturma betiği etiketlere göre etki alanları arası betikler çağırmak için kullanılan bir kuraldır. Sonuç bir belirtilen geri çağırma işlevi döndürülür. JSONP gibi etiketler fikrini temel `<script src="http://..." >` herhangi bir etki alanından komut değerlendirebilir ve bu etiketlere göre alınan komut diğer işlevleri zaten tanımlanabilir, kapsamında değerlendirilir.

## <a name="demonstrates"></a>Gösteriler
 Etki alanları arası JSONP ile betik oluşturma.

## <a name="discussion"></a>Tartışma
 Örnek sayfa işlendikten sonra dinamik olarak bir betik bloğu tarayıcıda ekleyen bir Web sayfası içerir. Bu betik bloğu tek bir işlem olan WCF REST hizmeti çağıran `GetCustomer`. WCF REST hizmeti, bir müşterinin adı ve bir geri çağırma işlevi adı sarmalanmış adresini döndürür. WCF REST hizmeti yanıt verdiğinde, müşteri verileriyle Web sayfasına geri çağırma işlevi çağrılır ve geri çağırma işlevi, Web sayfasında veri görüntüler. Komut dosyası etiketi ekleme ve yürütme geri çağırma işlevinin ASP.NET AJAX ScriptManager denetimi tarafından otomatik olarak gerçekleştirilir. Kullanım desenini tüm ASP.NET AJAX proxy'leri, ek olarak aşağıdaki kodda gösterildiği gibi JSONP etkinleştirmek için bir satır ile aynıdır:

```csharp
var proxy = new JsonpAjaxService.CustomerService();
proxy.set_enableJsonp(true);
proxy.GetCustomer(onSuccess, onFail, null);
```

 Web sayfasına hizmet kullandığından WCF REST hizmeti çağırabilirsiniz <xref:System.ServiceModel.Description.WebScriptEndpoint> ile `crossDomainScriptAccessEnabled` kümesine `true`. Bu yapılandırmaların her ikisi de altında Web.config dosyasında yapılması \<system.serviceModel > öğesi.

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

 ScriptManager hizmetiyle etkileşimi yönetir ve yerine JSONP erişim el ile uygulanması karmaşıklığını gizler. Zaman `crossDomainScriptAccessEnabled` ayarlanır `true` ve JSON yanıt biçimi için bir işlem olduğundan, WCF altyapısı bir geri çağırma sorgu dizesi parametresi için istek URI'sini inceler ve geri çağırma sorgu dizesi değerini JSON yanıtı sarmalayan parametre. Bu örnekte, Web sayfası şu URI'ye sahip WCF REST hizmeti çağırır.

```
http://localhost:33695/CustomerService/GetCustomer?callback=Sys._json0
```

 Geri çağırma sorgu dizesi parametresinin bir değeri olduğundan `JsonPCallback`, WCF hizmeti aşağıdaki örnekte gösterildiği bir JSONP yanıtı döndürür.

```
Sys._json0({"__type":"Customer:#Microsoft.Samples.Jsonp","Address":"1 Example Way","Name":"Bob"});
```

 Bu JSONP yanıtı JSON, istenen Web sayfasına geri çağırma işlevi adı ile sarmalanmış olarak biçimlendirilmiş müşteri verilerini içerir. ScriptManager etki alanları arası istek gerçekleştirmek için bir komut dosyası etiketini kullanarak bu geri çağırma yürütün ve sonra ASP.NET AJAX proxy GetCustomer çalışması için geçirilen onSuccess işleyicisine sonucu geçirin.

 Örnek iki ASP.NET web uygulamasından oluşur: yalnızca bir WCF hizmetini içerir ve başka bir hizmeti çağıran .aspx Web sayfası içerir. Çözüm çalışırken, Visual Studio 2012 Burada farklı etki alanlarında hizmet ve istemci canlı bir ortam oluşturur farklı noktalarında iki Web sitesi barındırır.

> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\JSONP`  
  
#### <a name="to-run-the-sample"></a>Örnek çalıştırmak için  
  
1.  Çözüm için JSONP örneği açın.  
  
2.  Başlatmak için F5 tuşuna basın `http://localhost:26648/JSONPClientPage.aspx` tarayıcıda.  
  
3.  Sayfa yüklendikten sonra "Name" ve "Address" için metin girişi değerlerle doldurulduğuna dikkat edin.  Tarayıcı sayfa işleme tamamlandıktan sonra bu değerleri WCF Hizmeti çağrısından sağlandı.
