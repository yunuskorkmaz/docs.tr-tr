---
title: JSONP
ms.date: 03/30/2017
ms.assetid: c13b4d7b-dac7-4ffd-9f84-765c903511e1
ms.openlocfilehash: 37da57a000376f972cd6da9e04be46ddec1b7144
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59767545"
---
# <a name="jsonp"></a><span data-ttu-id="9efcb-102">JSONP</span><span class="sxs-lookup"><span data-stu-id="9efcb-102">JSONP</span></span>
<span data-ttu-id="9efcb-103">Bu örnek JSON ile doldurma (JSONP) WCF REST Hizmetleri destekleyecek şekilde nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="9efcb-103">This sample demonstrates how to support JSON with Padding (JSONP) in WCF REST services.</span></span> <span data-ttu-id="9efcb-104">JSONP geçerli belgedeki oluşturma betiği etiketlere göre etki alanları arası betikler çağırmak için kullanılan bir kuraldır.</span><span class="sxs-lookup"><span data-stu-id="9efcb-104">JSONP is a convention used to invoke cross-domain scripts by generating script tags in the current document.</span></span> <span data-ttu-id="9efcb-105">Sonuç bir belirtilen geri çağırma işlevi döndürülür.</span><span class="sxs-lookup"><span data-stu-id="9efcb-105">The result is returned in a specified callback function.</span></span> <span data-ttu-id="9efcb-106">JSONP gibi etiketler fikrini temel `<script src="http://..." >` herhangi bir etki alanından komut değerlendirebilir ve bu etiketlere göre alınan komut diğer işlevleri zaten tanımlanabilir, kapsamında değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="9efcb-106">JSONP is based on the idea that tags such as `<script src="http://..." >` can evaluate scripts from any domain and the script retrieved by those tags is evaluated within a scope in which other functions may already be defined.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="9efcb-107">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="9efcb-107">Demonstrates</span></span>
 <span data-ttu-id="9efcb-108">Etki alanları arası JSONP ile betik oluşturma.</span><span class="sxs-lookup"><span data-stu-id="9efcb-108">Cross-domain scripting with JSONP.</span></span>

## <a name="discussion"></a><span data-ttu-id="9efcb-109">Tartışma</span><span class="sxs-lookup"><span data-stu-id="9efcb-109">Discussion</span></span>
 <span data-ttu-id="9efcb-110">Örnek sayfa işlendikten sonra dinamik olarak bir betik bloğu tarayıcıda ekleyen bir Web sayfası içerir.</span><span class="sxs-lookup"><span data-stu-id="9efcb-110">The sample includes a Web page that dynamically adds a script block after the page has been rendered in the browser.</span></span> <span data-ttu-id="9efcb-111">Bu betik bloğu tek bir işlem olan WCF REST hizmeti çağıran `GetCustomer`.</span><span class="sxs-lookup"><span data-stu-id="9efcb-111">This script block calls a WCF REST service that has a single operation, `GetCustomer`.</span></span> <span data-ttu-id="9efcb-112">WCF REST hizmeti, bir müşterinin adı ve bir geri çağırma işlevi adı sarmalanmış adresini döndürür.</span><span class="sxs-lookup"><span data-stu-id="9efcb-112">The WCF REST service returns a customer’s name and address wrapped in a callback function name.</span></span> <span data-ttu-id="9efcb-113">WCF REST hizmeti yanıt verdiğinde, müşteri verileriyle Web sayfasına geri çağırma işlevi çağrılır ve geri çağırma işlevi, Web sayfasında veri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="9efcb-113">When the WCF REST service responds, the callback function on the Web page is invoked with the customer data and the callback function displays the data on the Web page.</span></span> <span data-ttu-id="9efcb-114">Komut dosyası etiketi ekleme ve yürütme geri çağırma işlevinin ASP.NET AJAX ScriptManager denetimi tarafından otomatik olarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="9efcb-114">The injection of the script tag and the execution of the callback function is automatically handled by the ASP.NET AJAX ScriptManager control.</span></span> <span data-ttu-id="9efcb-115">Kullanım desenini tüm ASP.NET AJAX proxy'leri, ek olarak aşağıdaki kodda gösterildiği gibi JSONP etkinleştirmek için bir satır ile aynıdır:</span><span class="sxs-lookup"><span data-stu-id="9efcb-115">The usage pattern is the same as with all ASP.NET AJAX proxies, with the addition of one line to enable JSONP, as shown in the following code:</span></span>

```csharp
var proxy = new JsonpAjaxService.CustomerService();
proxy.set_enableJsonp(true);
proxy.GetCustomer(onSuccess, onFail, null);
```

 <span data-ttu-id="9efcb-116">Web sayfasına hizmet kullandığından WCF REST hizmeti çağırabilirsiniz <xref:System.ServiceModel.Description.WebScriptEndpoint> ile `crossDomainScriptAccessEnabled` kümesine `true`.</span><span class="sxs-lookup"><span data-stu-id="9efcb-116">The Web page can call the WCF REST service because the service is using the <xref:System.ServiceModel.Description.WebScriptEndpoint> with `crossDomainScriptAccessEnabled` set to `true`.</span></span> <span data-ttu-id="9efcb-117">Bu yapılandırmaların her ikisi de altında Web.config dosyasında yapılması \<system.serviceModel > öğesi.</span><span class="sxs-lookup"><span data-stu-id="9efcb-117">Both of these configurations are done in the Web.config file under the \<system.serviceModel> element.</span></span>

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

 <span data-ttu-id="9efcb-118">ScriptManager hizmetiyle etkileşimi yönetir ve yerine JSONP erişim el ile uygulanması karmaşıklığını gizler.</span><span class="sxs-lookup"><span data-stu-id="9efcb-118">ScriptManager manages the interaction with the service and hides away the complexity of manually implementing JSONP access.</span></span> <span data-ttu-id="9efcb-119">Zaman `crossDomainScriptAccessEnabled` ayarlanır `true` ve JSON yanıt biçimi için bir işlem olduğundan, WCF altyapısı bir geri çağırma sorgu dizesi parametresi için istek URI'sini inceler ve geri çağırma sorgu dizesi değerini JSON yanıtı sarmalayan parametre.</span><span class="sxs-lookup"><span data-stu-id="9efcb-119">When `crossDomainScriptAccessEnabled` is set to `true` and the response format for an operation is JSON, the WCF infrastructure inspects the URI of the request for a callback query string parameter and wraps the JSON response with the value of the callback query string parameter.</span></span> <span data-ttu-id="9efcb-120">Bu örnekte, Web sayfası şu URI'ye sahip WCF REST hizmeti çağırır.</span><span class="sxs-lookup"><span data-stu-id="9efcb-120">In the sample, the Web page calls the WCF REST service with the following URI.</span></span>

```
http://localhost:33695/CustomerService/GetCustomer?callback=Sys._json0
```

 <span data-ttu-id="9efcb-121">Geri çağırma sorgu dizesi parametresinin bir değeri olduğundan `JsonPCallback`, WCF hizmeti aşağıdaki örnekte gösterildiği bir JSONP yanıtı döndürür.</span><span class="sxs-lookup"><span data-stu-id="9efcb-121">Because the callback query string parameter has a value of `JsonPCallback`, the WCF service returns a JSONP response shown in the following example.</span></span>

```
Sys._json0({"__type":"Customer:#Microsoft.Samples.Jsonp","Address":"1 Example Way","Name":"Bob"});
```

 <span data-ttu-id="9efcb-122">Bu JSONP yanıtı JSON, istenen Web sayfasına geri çağırma işlevi adı ile sarmalanmış olarak biçimlendirilmiş müşteri verilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="9efcb-122">This JSONP response includes the customer data formatted as JSON, wrapped with the callback function name that the Web page requested.</span></span> <span data-ttu-id="9efcb-123">ScriptManager etki alanları arası istek gerçekleştirmek için bir komut dosyası etiketini kullanarak bu geri çağırma yürütün ve sonra ASP.NET AJAX proxy GetCustomer çalışması için geçirilen onSuccess işleyicisine sonucu geçirin.</span><span class="sxs-lookup"><span data-stu-id="9efcb-123">ScriptManager will execute this callback using a script tag to accomplish the cross-domain request, and then pass the result to the onSuccess handler that was passed to the GetCustomer operation of the ASP.NET AJAX proxy.</span></span>

 <span data-ttu-id="9efcb-124">Örnek iki ASP.NET web uygulamasından oluşur: yalnızca bir WCF hizmetini içerir ve başka bir hizmeti çağıran .aspx Web sayfası içerir.</span><span class="sxs-lookup"><span data-stu-id="9efcb-124">The sample consists of two ASP.NET web applications: one contains just a WCF service, and another one contains the .aspx webpage, which calls the service.</span></span> <span data-ttu-id="9efcb-125">Çözüm çalışırken, Visual Studio 2012 Burada farklı etki alanlarında hizmet ve istemci canlı bir ortam oluşturur farklı noktalarında iki Web sitesi barındırır.</span><span class="sxs-lookup"><span data-stu-id="9efcb-125">When running the solution, Visual Studio 2012 will host the two websites on different ports, which creates an environment where the service and client live on different domains.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="9efcb-126">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="9efcb-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9efcb-127">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="9efcb-127">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9efcb-128">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="9efcb-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9efcb-129">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="9efcb-129">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\JSONP`  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="9efcb-130">Örnek çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="9efcb-130">To run the sample</span></span>  
  
1. <span data-ttu-id="9efcb-131">Çözüm için JSONP örneği açın.</span><span class="sxs-lookup"><span data-stu-id="9efcb-131">Open the solution for the JSONP Sample.</span></span>  
  
2. <span data-ttu-id="9efcb-132">Başlatmak için F5 tuşuna basın `http://localhost:26648/JSONPClientPage.aspx` tarayıcıda.</span><span class="sxs-lookup"><span data-stu-id="9efcb-132">Press F5 to launch `http://localhost:26648/JSONPClientPage.aspx` in the browser.</span></span>  
  
3. <span data-ttu-id="9efcb-133">Sayfa yüklendikten sonra "Name" ve "Address" için metin girişi değerlerle doldurulduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="9efcb-133">Notice that after the page loads, the text inputs for "Name" and "Address" are populated by values.</span></span>  <span data-ttu-id="9efcb-134">Tarayıcı sayfa işleme tamamlandıktan sonra bu değerleri WCF Hizmeti çağrısından sağlandı.</span><span class="sxs-lookup"><span data-stu-id="9efcb-134">These values were supplied from a call to the WCF service after the browser finished rendering the page.</span></span>
