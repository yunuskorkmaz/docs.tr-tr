---
description: 'Daha fazla bilgi edinin: JSONP'
title: JSONP
ms.date: 03/30/2017
ms.assetid: c13b4d7b-dac7-4ffd-9f84-765c903511e1
ms.openlocfilehash: 83236f3d40a9dfeaf2ab0e521a227fb6dfc461f6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99726344"
---
# <a name="jsonp"></a>JSONP

Bu örnek, WCF REST hizmetlerinde doldurma (JSONP) ile JSON 'ın nasıl destekleyeceğinizi gösterir. JSONP, geçerli belgede komut dosyası etiketleri oluşturarak etki alanları arası betikleri çağırmak için kullanılan bir kuraldır. Sonuç, belirtilen geri arama işlevinde döndürülür. JSONP, gibi etiketlerin `<script src="http://..." >` herhangi bir etki alanındaki betikleri değerlendirebileceği ve bu Etiketler tarafından alınan betiklerin, diğer işlevlerin zaten tanımlandığı bir kapsamda değerlendirilme fikrini temel alır.

## <a name="demonstrates"></a>Gösteriler

 JSONP ile çapraz etki alanı betiği oluşturma.

## <a name="discussion"></a>Tartışma

 Örnek, sayfa tarayıcıda işlendikten sonra dinamik olarak bir betik bloğu ekleyen bir Web sayfası içerir. Bu betik bloğu, tek bir işlemi olan bir WCF REST hizmetini çağırır `GetCustomer` . WCF REST hizmeti, bir geri çağırma işlevi adında Sarmalanan bir müşterinin adını ve adresini döndürür. WCF REST hizmeti yanıt verdiğinde, Web sayfasındaki geri çağırma işlevi müşteri verileriyle çağrılır ve geri arama işlevi, verileri Web sayfasında görüntüler. Betik etiketinin ekleme ve geri çağırma işlevinin yürütülmesi ASP.NET AJAX ScriptManager denetimi tarafından otomatik olarak gerçekleştirilir. Kullanım stili, aşağıdaki kodda gösterildiği gibi, JSONP 'yi etkinleştirmek için bir satırın eklenmesiyle birlikte tüm ASP.NET AJAX proxy 'leriyle aynıdır:

```csharp
var proxy = new JsonpAjaxService.CustomerService();
proxy.set_enableJsonp(true);
proxy.GetCustomer(onSuccess, onFail, null);
```

 Web sayfası WCF REST hizmetini çağırabilir çünkü hizmet ' i ' olarak ayarlanmış olarak kullanıyor <xref:System.ServiceModel.Description.WebScriptEndpoint> `crossDomainScriptAccessEnabled` `true` . Bu yapılandırmaların her ikisi de öğesi altındaki Web.config dosyasında yapılır \<system.serviceModel> .

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

 ScriptManager, hizmetle etkileşimi yönetir ve JSONP erişimini el ile uygulama karmaşıklığını ortadan kaldırır. `crossDomainScriptAccessEnabled`Olarak ayarlandığında `true` ve bir işlemin yanıt biçimi JSON olduğunda, WCF altyapısı bir geri çağırma sorgusu dize parametresi IÇIN isteğin URI 'sini INCELER ve JSON yanıtını geri çağırma sorgu dizesi parametresinin değeriyle kaydırır. Örnekte, Web sayfası WCF REST hizmetini aşağıdaki URI ile çağırır.

```http
http://localhost:33695/CustomerService/GetCustomer?callback=Sys._json0
```

 Geri arama sorgu dizesi parametresinin değeri olduğundan `JsonPCallback` , WCF hizmeti aşağıdaki örnekte gösterilen BIR JSONP yanıtı döndürür.

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
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\JSONP`  
  
#### <a name="to-run-the-sample"></a>Örnek çalıştırmak için  
  
1. JSONP örneği için çözümü açın.  
  
2. Tarayıcıda başlatmak için F5 tuşuna basın `http://localhost:26648/JSONPClientPage.aspx` .  
  
3. Sayfa yüklendikten sonra, "ad" ve "adres" için metin girişlerinin değerlere göre doldurulduğuna dikkat edin.  Bu değerler, tarayıcı sayfayı işlemeyi tamamladıktan sonra WCF hizmetine yapılan çağrıdan sağlanmış.
