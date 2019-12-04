---
title: JSONP
ms.date: 03/30/2017
ms.assetid: c13b4d7b-dac7-4ffd-9f84-765c903511e1
ms.openlocfilehash: 82fa0bb09ebdf3ca2325872c2b884f4940de17ed
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715718"
---
# <a name="jsonp"></a>JSONP
Bu örnek, WCF REST hizmetlerinde doldurma (JSONP) ile JSON 'ın nasıl destekleyeceğinizi gösterir. JSONP, geçerli belgede komut dosyası etiketleri oluşturarak etki alanları arası betikleri çağırmak için kullanılan bir kuraldır. Sonuç, belirtilen geri arama işlevinde döndürülür. JSONP, `<script src="http://..." >` gibi etiketlerin herhangi bir etki alanından betikleri değerlendirebileceği ve bu Etiketler tarafından alınan betiğin, diğer işlevlerin zaten tanımlandığı bir kapsamda değerlendirilme fikrini temel alır.

## <a name="demonstrates"></a>Gösterir
 JSONP ile çapraz etki alanı betiği oluşturma.

## <a name="discussion"></a>Tartışma
 Örnek, sayfa tarayıcıda işlendikten sonra dinamik olarak bir betik bloğu ekleyen bir Web sayfası içerir. Bu betik bloğu, `GetCustomer`tek bir işlemi olan bir WCF REST hizmetini çağırır. WCF REST hizmeti, bir geri çağırma işlevi adında Sarmalanan bir müşterinin adını ve adresini döndürür. WCF REST hizmeti yanıt verdiğinde, Web sayfasındaki geri çağırma işlevi müşteri verileriyle çağrılır ve geri arama işlevi, verileri Web sayfasında görüntüler. Betik etiketinin ekleme ve geri çağırma işlevinin yürütülmesi ASP.NET AJAX ScriptManager denetimi tarafından otomatik olarak gerçekleştirilir. Kullanım stili, aşağıdaki kodda gösterildiği gibi, JSONP 'yi etkinleştirmek için bir satırın eklenmesiyle birlikte tüm ASP.NET AJAX proxy 'leriyle aynıdır:

```csharp
var proxy = new JsonpAjaxService.CustomerService();
proxy.set_enableJsonp(true);
proxy.GetCustomer(onSuccess, onFail, null);
```

 Hizmet, `crossDomainScriptAccessEnabled` `true`olarak ayarlanmış <xref:System.ServiceModel.Description.WebScriptEndpoint> kullandığından, Web sayfası WCF REST hizmetini çağırabilir. Bu yapılandırmaların her ikisi de \<System. serviceModel > öğesinin altındaki Web. config dosyasında yapılır.

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

 ScriptManager, hizmetle etkileşimi yönetir ve JSONP erişimini el ile uygulama karmaşıklığını ortadan kaldırır. `crossDomainScriptAccessEnabled` `true` olarak ayarlandığında ve bir işlemin yanıt biçimi JSON olduğunda, WCF altyapısı bir geri çağırma sorgusu dize parametresi için isteğin URI 'sini inceler ve JSON yanıtını geri çağırma sorgu dizesi parametresinin değeriyle kaydırır. Örnekte, Web sayfası WCF REST hizmetini aşağıdaki URI ile çağırır.

```http
http://localhost:33695/CustomerService/GetCustomer?callback=Sys._json0
```

 Geri arama sorgu dizesi parametresinin değeri `JsonPCallback`olduğundan, WCF hizmeti aşağıdaki örnekte gösterilen bir JSONP yanıtı döndürür.

```json
Sys._json0({"__type":"Customer:#Microsoft.Samples.Jsonp","Address":"1 Example Way","Name":"Bob"});
```

 Bu JSONP yanıtı, Web sayfasının istediği geri çağırma işlevi adıyla Sarmalanan JSON olarak biçimlendirilen müşteri verilerini içerir. ScriptManager, etki alanları arası isteği başarmak için bir betik etiketi kullanarak bu geri aramayı yürütür ve sonra sonucu ASP.NET AJAX proxy 'sinin GetCustomer işlemine geçirilen onSuccess işleyicisine iletir.

 Örnek iki ASP.NET Web uygulamalarından oluşur: biri yalnızca bir WCF hizmeti içerir ve diğeri hizmeti çağıran. aspx Web sayfasını içerir. Çözümü çalıştırırken, Visual Studio 2012 farklı bağlantı noktalarında iki Web sitesini barındıracaktır. Bu, hizmetin ve istemcinin farklı etki alanlarında bulunduğu bir ortam oluşturur.

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\JSONP`  
  
#### <a name="to-run-the-sample"></a>Örnek çalıştırmak için  
  
1. JSONP örneği için çözümü açın.  
  
2. Tarayıcıda `http://localhost:26648/JSONPClientPage.aspx` başlatmak için F5 tuşuna basın.  
  
3. Sayfa yüklendikten sonra, "ad" ve "adres" için metin girişlerinin değerlere göre doldurulduğuna dikkat edin.  Bu değerler, tarayıcı sayfayı işlemeyi tamamladıktan sonra WCF hizmetine yapılan çağrıdan sağlanmış.
