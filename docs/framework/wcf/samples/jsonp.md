---
title: JSONP
ms.date: 03/30/2017
ms.assetid: c13b4d7b-dac7-4ffd-9f84-765c903511e1
ms.openlocfilehash: 9f24ccb5ba14e0b43f0e3f911a1672db5821d228
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70039551"
---
# <a name="jsonp"></a><span data-ttu-id="cf6cd-102">JSONP</span><span class="sxs-lookup"><span data-stu-id="cf6cd-102">JSONP</span></span>
<span data-ttu-id="cf6cd-103">Bu örnek, WCF REST hizmetlerinde doldurma (JSONP) ile JSON 'ın nasıl destekleyeceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="cf6cd-103">This sample demonstrates how to support JSON with Padding (JSONP) in WCF REST services.</span></span> <span data-ttu-id="cf6cd-104">JSONP, geçerli belgede komut dosyası etiketleri oluşturarak etki alanları arası betikleri çağırmak için kullanılan bir kuraldır.</span><span class="sxs-lookup"><span data-stu-id="cf6cd-104">JSONP is a convention used to invoke cross-domain scripts by generating script tags in the current document.</span></span> <span data-ttu-id="cf6cd-105">Sonuç, belirtilen geri arama işlevinde döndürülür.</span><span class="sxs-lookup"><span data-stu-id="cf6cd-105">The result is returned in a specified callback function.</span></span> <span data-ttu-id="cf6cd-106">JSONP, gibi etiketlerin `<script src="http://..." >` herhangi bir etki alanındaki betikleri değerlendirebileceği ve bu Etiketler tarafından alınan betiklerin, diğer işlevlerin zaten tanımlandığı bir kapsamda değerlendirilme fikrini temel alır.</span><span class="sxs-lookup"><span data-stu-id="cf6cd-106">JSONP is based on the idea that tags such as `<script src="http://..." >` can evaluate scripts from any domain and the script retrieved by those tags is evaluated within a scope in which other functions may already be defined.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="cf6cd-107">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="cf6cd-107">Demonstrates</span></span>
 <span data-ttu-id="cf6cd-108">JSONP ile çapraz etki alanı betiği oluşturma.</span><span class="sxs-lookup"><span data-stu-id="cf6cd-108">Cross-domain scripting with JSONP.</span></span>

## <a name="discussion"></a><span data-ttu-id="cf6cd-109">Tartışma</span><span class="sxs-lookup"><span data-stu-id="cf6cd-109">Discussion</span></span>
 <span data-ttu-id="cf6cd-110">Örnek, sayfa tarayıcıda işlendikten sonra dinamik olarak bir betik bloğu ekleyen bir Web sayfası içerir.</span><span class="sxs-lookup"><span data-stu-id="cf6cd-110">The sample includes a Web page that dynamically adds a script block after the page has been rendered in the browser.</span></span> <span data-ttu-id="cf6cd-111">Bu betik bloğu, `GetCustomer`tek bir IŞLEMI olan bir WCF REST hizmetini çağırır.</span><span class="sxs-lookup"><span data-stu-id="cf6cd-111">This script block calls a WCF REST service that has a single operation, `GetCustomer`.</span></span> <span data-ttu-id="cf6cd-112">WCF REST hizmeti, bir geri çağırma işlevi adında Sarmalanan bir müşterinin adını ve adresini döndürür.</span><span class="sxs-lookup"><span data-stu-id="cf6cd-112">The WCF REST service returns a customer’s name and address wrapped in a callback function name.</span></span> <span data-ttu-id="cf6cd-113">WCF REST hizmeti yanıt verdiğinde, Web sayfasındaki geri çağırma işlevi müşteri verileriyle çağrılır ve geri arama işlevi, verileri Web sayfasında görüntüler.</span><span class="sxs-lookup"><span data-stu-id="cf6cd-113">When the WCF REST service responds, the callback function on the Web page is invoked with the customer data and the callback function displays the data on the Web page.</span></span> <span data-ttu-id="cf6cd-114">Betik etiketinin ekleme ve geri çağırma işlevinin yürütülmesi ASP.NET AJAX ScriptManager denetimi tarafından otomatik olarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="cf6cd-114">The injection of the script tag and the execution of the callback function is automatically handled by the ASP.NET AJAX ScriptManager control.</span></span> <span data-ttu-id="cf6cd-115">Kullanım stili, aşağıdaki kodda gösterildiği gibi, JSONP 'yi etkinleştirmek için bir satırın eklenmesiyle birlikte tüm ASP.NET AJAX proxy 'leriyle aynıdır:</span><span class="sxs-lookup"><span data-stu-id="cf6cd-115">The usage pattern is the same as with all ASP.NET AJAX proxies, with the addition of one line to enable JSONP, as shown in the following code:</span></span>

```csharp
var proxy = new JsonpAjaxService.CustomerService();
proxy.set_enableJsonp(true);
proxy.GetCustomer(onSuccess, onFail, null);
```

 <span data-ttu-id="cf6cd-116">Web sayfası WCF REST hizmetini çağırabilir çünkü hizmet ' i ' olarak <xref:System.ServiceModel.Description.WebScriptEndpoint> `crossDomainScriptAccessEnabled` `true`ayarlanmış olarak kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="cf6cd-116">The Web page can call the WCF REST service because the service is using the <xref:System.ServiceModel.Description.WebScriptEndpoint> with `crossDomainScriptAccessEnabled` set to `true`.</span></span> <span data-ttu-id="cf6cd-117">Bu yapılandırmaların her ikisi de \<System. ServiceModel > öğesinin altındaki Web. config dosyasında yapılır.</span><span class="sxs-lookup"><span data-stu-id="cf6cd-117">Both of these configurations are done in the Web.config file under the \<system.serviceModel> element.</span></span>

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

 <span data-ttu-id="cf6cd-118">ScriptManager, hizmetle etkileşimi yönetir ve JSONP erişimini el ile uygulama karmaşıklığını ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="cf6cd-118">ScriptManager manages the interaction with the service and hides away the complexity of manually implementing JSONP access.</span></span> <span data-ttu-id="cf6cd-119">`crossDomainScriptAccessEnabled` Olarak`true` ayarlandığında ve bir işlemin yanıt biçimi JSON olduğunda, WCF altyapısı bir geri çağırma sorgusu dize parametresi için isteğin URI 'sini inceler ve JSON yanıtını geri çağırma sorgu dizesinin değeriyle sarar parametresinin.</span><span class="sxs-lookup"><span data-stu-id="cf6cd-119">When `crossDomainScriptAccessEnabled` is set to `true` and the response format for an operation is JSON, the WCF infrastructure inspects the URI of the request for a callback query string parameter and wraps the JSON response with the value of the callback query string parameter.</span></span> <span data-ttu-id="cf6cd-120">Örnekte, Web sayfası WCF REST hizmetini aşağıdaki URI ile çağırır.</span><span class="sxs-lookup"><span data-stu-id="cf6cd-120">In the sample, the Web page calls the WCF REST service with the following URI.</span></span>

```
http://localhost:33695/CustomerService/GetCustomer?callback=Sys._json0
```

 <span data-ttu-id="cf6cd-121">Geri arama sorgu dizesi parametresinin değeri `JsonPCallback`olduğundan, WCF hizmeti aşağıdaki örnekte gösterilen bir JSONP yanıtı döndürür.</span><span class="sxs-lookup"><span data-stu-id="cf6cd-121">Because the callback query string parameter has a value of `JsonPCallback`, the WCF service returns a JSONP response shown in the following example.</span></span>

```
Sys._json0({"__type":"Customer:#Microsoft.Samples.Jsonp","Address":"1 Example Way","Name":"Bob"});
```

 <span data-ttu-id="cf6cd-122">Bu JSONP yanıtı, Web sayfasının istediği geri çağırma işlevi adıyla Sarmalanan JSON olarak biçimlendirilen müşteri verilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="cf6cd-122">This JSONP response includes the customer data formatted as JSON, wrapped with the callback function name that the Web page requested.</span></span> <span data-ttu-id="cf6cd-123">ScriptManager, etki alanları arası isteği başarmak için bir betik etiketi kullanarak bu geri aramayı yürütür ve sonra sonucu ASP.NET AJAX proxy 'sinin GetCustomer işlemine geçirilen onSuccess işleyicisine iletir.</span><span class="sxs-lookup"><span data-stu-id="cf6cd-123">ScriptManager will execute this callback using a script tag to accomplish the cross-domain request, and then pass the result to the onSuccess handler that was passed to the GetCustomer operation of the ASP.NET AJAX proxy.</span></span>

 <span data-ttu-id="cf6cd-124">Örnek iki ASP.NET Web uygulamalarından oluşur: biri yalnızca bir WCF hizmeti içerir ve diğeri hizmeti çağıran. aspx Web sayfasını içerir.</span><span class="sxs-lookup"><span data-stu-id="cf6cd-124">The sample consists of two ASP.NET web applications: one contains just a WCF service, and another one contains the .aspx webpage, which calls the service.</span></span> <span data-ttu-id="cf6cd-125">Çözümü çalıştırırken, Visual Studio 2012 farklı bağlantı noktalarında iki Web sitesini barındıracaktır. Bu, hizmetin ve istemcinin farklı etki alanlarında bulunduğu bir ortam oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cf6cd-125">When running the solution, Visual Studio 2012 will host the two websites on different ports, which creates an environment where the service and client live on different domains.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cf6cd-126">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="cf6cd-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="cf6cd-127">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="cf6cd-127">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="cf6cd-128">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin.</span><span class="sxs-lookup"><span data-stu-id="cf6cd-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="cf6cd-129">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="cf6cd-129">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\JSONP`  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="cf6cd-130">Örnek çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="cf6cd-130">To run the sample</span></span>  
  
1. <span data-ttu-id="cf6cd-131">JSONP örneği için çözümü açın.</span><span class="sxs-lookup"><span data-stu-id="cf6cd-131">Open the solution for the JSONP Sample.</span></span>  
  
2. <span data-ttu-id="cf6cd-132">Tarayıcıda başlatmak `http://localhost:26648/JSONPClientPage.aspx` için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="cf6cd-132">Press F5 to launch `http://localhost:26648/JSONPClientPage.aspx` in the browser.</span></span>  
  
3. <span data-ttu-id="cf6cd-133">Sayfa yüklendikten sonra, "ad" ve "adres" için metin girişlerinin değerlere göre doldurulduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="cf6cd-133">Notice that after the page loads, the text inputs for "Name" and "Address" are populated by values.</span></span>  <span data-ttu-id="cf6cd-134">Bu değerler, tarayıcı sayfayı işlemeyi tamamladıktan sonra WCF hizmetine yapılan çağrıdan sağlanmış.</span><span class="sxs-lookup"><span data-stu-id="cf6cd-134">These values were supplied from a call to the WCF service after the browser finished rendering the page.</span></span>
