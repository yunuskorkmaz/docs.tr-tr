---
title: JSONP
ms.date: 03/30/2017
ms.assetid: c13b4d7b-dac7-4ffd-9f84-765c903511e1
ms.openlocfilehash: 6b5b42285539c2334bccaa04e1ba179d2cf0046c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183566"
---
# <a name="jsonp"></a>JSONP
Bu örnek, WCF REST hizmetlerinde JSON'un Doldurma (JSONP) ile nasıl desteklanacağını göstermektedir. JSONP, geçerli belgede komut dosyası etiketleri oluşturarak etki alanları arası komut dosyalarını çağırmak için kullanılan bir kuraldır. Sonuç, belirtilen bir geri arama işlevinde döndürülür. JSONP, herhangi bir etki alanından komut dosyalarını değerlendirebilen etiketler ve `<script src="http://..." >` bu etiketler tarafından alınan komut dosyası gibi etiketlerin, diğer işlevlerin zaten tanımlanmış olabileceği bir kapsamda değerlendirildiği fikrine dayanır.

## <a name="demonstrates"></a>Gösteriler
 JSONP ile çapraz etki alanı komut dosyası.

## <a name="discussion"></a>Tartışma
 Örnek, sayfa tarayıcıda işlendikten sonra dinamik olarak komut dosyası bloğu ekleyen bir Web sayfası içerir. Bu komut dosyası bloğu, tek bir işlem `GetCustomer`olan bir WCF REST hizmetini çağırır. WCF REST hizmeti, geri arama işlevi adına sarılmış bir müşterinin adını ve adresini döndürür. WCF REST hizmeti yanıt verdiğinde, Web sayfasındaki geri arama işlevi müşteri verileriyle birlikte çağrılır ve geri arama işlevi Web sayfasındaki verileri görüntüler. Komut dosyası etiketinin enjeksiyonu ve geri arama işlevinin yürütülmesi, ASP.NET AJAX ScriptManager denetimi tarafından otomatik olarak işlenir. Kullanım deseni, aşağıdaki kodda gösterildiği gibi JSONP'yi etkinleştirmek için bir satır eklenmesiyle, tüm ASP.NET AJAX vekilleriyle aynıdır:

```csharp
var proxy = new JsonpAjaxService.CustomerService();
proxy.set_enableJsonp(true);
proxy.GetCustomer(onSuccess, onFail, null);
```

 Web sayfası WCF REST hizmetini çağırabilir, çünkü <xref:System.ServiceModel.Description.WebScriptEndpoint> `crossDomainScriptAccessEnabled` hizmet `true`ile 'yi ' için ayarla'yı kullanıyor. Bu yapılandırmaların her ikisi de system.serviceModel \<> öğesi altında Web.config dosyasında yapılır.

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

 ScriptManager hizmetle etkileşimi yönetir ve JSONP erişimini el ile uygulamanın karmaşıklığını gizler. Ne `crossDomainScriptAccessEnabled` zaman `true` ayarlanır ve bir işlem için yanıt biçimi JSON olduğunu, WCF altyapısı bir geri arama sorgusu dize parametresi için istek URI inceler ve geri arama sorgusu dize parametresi değeri ile JSON yanıtı sarar. Örnekte, Web sayfası WCF REST hizmetini aşağıdaki URI ile çağırır.

```http
http://localhost:33695/CustomerService/GetCustomer?callback=Sys._json0
```

 Geri arama sorgusu dize parametresi `JsonPCallback`değeri olduğundan, WCF hizmeti aşağıdaki örnekte gösterilen bir JSONP yanıtını döndürür.

```json
Sys._json0({"__type":"Customer:#Microsoft.Samples.Jsonp","Address":"1 Example Way","Name":"Bob"});
```

 Bu JSONP yanıtı, Web sayfasının istediği geri arama işlevi adı ile sarılmış JSON olarak biçimlendirilmiş müşteri verilerini içerir. ScriptManager, etki alanı arası isteği gerçekleştirmek için bir komut dosyası etiketi kullanarak bu geri aramayı yürütecek ve sonucu ASP.NET AJAX proxy'sinin GetCustomer işlemine geçirilen onSuccess işleyicisine iletir.

 Örnek iki ASP.NET web uygulamasından oluşur: biri yalnızca bir WCF hizmeti içerir, diğeri ise hizmeti çağıran .aspx web sayfasını içerir. Visual Studio 2012, çözümü çalıştırırken, iki web sitesini farklı bağlantı noktalarında barındıracak ve bu da hizmetin ve istemcinin farklı etki alanlarında yaşadığı bir ortam oluşturur.

> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\JSONP`  
  
#### <a name="to-run-the-sample"></a>Örnek çalıştırmak için  
  
1. JSONP Örneği için çözümü açın.  
  
2. Tarayıcıda başlatmak `http://localhost:26648/JSONPClientPage.aspx` için F5 tuşuna basın.  
  
3. Sayfa yüklendikten sonra "Ad" ve "Adres" metin girişlerinin değerlerle doldurulur.  Bu değerler, tarayıcı sayfayı oluşturmayı bitirdikten sonra WCF hizmetine yapılan bir aramadan sağlanmıştır.
