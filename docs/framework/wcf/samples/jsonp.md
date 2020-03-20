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
# <a name="jsonp"></a><span data-ttu-id="8fadb-102">JSONP</span><span class="sxs-lookup"><span data-stu-id="8fadb-102">JSONP</span></span>
<span data-ttu-id="8fadb-103">Bu örnek, WCF REST hizmetlerinde JSON'un Doldurma (JSONP) ile nasıl desteklanacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="8fadb-103">This sample demonstrates how to support JSON with Padding (JSONP) in WCF REST services.</span></span> <span data-ttu-id="8fadb-104">JSONP, geçerli belgede komut dosyası etiketleri oluşturarak etki alanları arası komut dosyalarını çağırmak için kullanılan bir kuraldır.</span><span class="sxs-lookup"><span data-stu-id="8fadb-104">JSONP is a convention used to invoke cross-domain scripts by generating script tags in the current document.</span></span> <span data-ttu-id="8fadb-105">Sonuç, belirtilen bir geri arama işlevinde döndürülür.</span><span class="sxs-lookup"><span data-stu-id="8fadb-105">The result is returned in a specified callback function.</span></span> <span data-ttu-id="8fadb-106">JSONP, herhangi bir etki alanından komut dosyalarını değerlendirebilen etiketler ve `<script src="http://..." >` bu etiketler tarafından alınan komut dosyası gibi etiketlerin, diğer işlevlerin zaten tanımlanmış olabileceği bir kapsamda değerlendirildiği fikrine dayanır.</span><span class="sxs-lookup"><span data-stu-id="8fadb-106">JSONP is based on the idea that tags such as `<script src="http://..." >` can evaluate scripts from any domain and the script retrieved by those tags is evaluated within a scope in which other functions may already be defined.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="8fadb-107">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="8fadb-107">Demonstrates</span></span>
 <span data-ttu-id="8fadb-108">JSONP ile çapraz etki alanı komut dosyası.</span><span class="sxs-lookup"><span data-stu-id="8fadb-108">Cross-domain scripting with JSONP.</span></span>

## <a name="discussion"></a><span data-ttu-id="8fadb-109">Tartışma</span><span class="sxs-lookup"><span data-stu-id="8fadb-109">Discussion</span></span>
 <span data-ttu-id="8fadb-110">Örnek, sayfa tarayıcıda işlendikten sonra dinamik olarak komut dosyası bloğu ekleyen bir Web sayfası içerir.</span><span class="sxs-lookup"><span data-stu-id="8fadb-110">The sample includes a Web page that dynamically adds a script block after the page has been rendered in the browser.</span></span> <span data-ttu-id="8fadb-111">Bu komut dosyası bloğu, tek bir işlem `GetCustomer`olan bir WCF REST hizmetini çağırır.</span><span class="sxs-lookup"><span data-stu-id="8fadb-111">This script block calls a WCF REST service that has a single operation, `GetCustomer`.</span></span> <span data-ttu-id="8fadb-112">WCF REST hizmeti, geri arama işlevi adına sarılmış bir müşterinin adını ve adresini döndürür.</span><span class="sxs-lookup"><span data-stu-id="8fadb-112">The WCF REST service returns a customer’s name and address wrapped in a callback function name.</span></span> <span data-ttu-id="8fadb-113">WCF REST hizmeti yanıt verdiğinde, Web sayfasındaki geri arama işlevi müşteri verileriyle birlikte çağrılır ve geri arama işlevi Web sayfasındaki verileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="8fadb-113">When the WCF REST service responds, the callback function on the Web page is invoked with the customer data and the callback function displays the data on the Web page.</span></span> <span data-ttu-id="8fadb-114">Komut dosyası etiketinin enjeksiyonu ve geri arama işlevinin yürütülmesi, ASP.NET AJAX ScriptManager denetimi tarafından otomatik olarak işlenir.</span><span class="sxs-lookup"><span data-stu-id="8fadb-114">The injection of the script tag and the execution of the callback function is automatically handled by the ASP.NET AJAX ScriptManager control.</span></span> <span data-ttu-id="8fadb-115">Kullanım deseni, aşağıdaki kodda gösterildiği gibi JSONP'yi etkinleştirmek için bir satır eklenmesiyle, tüm ASP.NET AJAX vekilleriyle aynıdır:</span><span class="sxs-lookup"><span data-stu-id="8fadb-115">The usage pattern is the same as with all ASP.NET AJAX proxies, with the addition of one line to enable JSONP, as shown in the following code:</span></span>

```csharp
var proxy = new JsonpAjaxService.CustomerService();
proxy.set_enableJsonp(true);
proxy.GetCustomer(onSuccess, onFail, null);
```

 <span data-ttu-id="8fadb-116">Web sayfası WCF REST hizmetini çağırabilir, çünkü <xref:System.ServiceModel.Description.WebScriptEndpoint> `crossDomainScriptAccessEnabled` hizmet `true`ile 'yi ' için ayarla'yı kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="8fadb-116">The Web page can call the WCF REST service because the service is using the <xref:System.ServiceModel.Description.WebScriptEndpoint> with `crossDomainScriptAccessEnabled` set to `true`.</span></span> <span data-ttu-id="8fadb-117">Bu yapılandırmaların her ikisi de system.serviceModel \<> öğesi altında Web.config dosyasında yapılır.</span><span class="sxs-lookup"><span data-stu-id="8fadb-117">Both of these configurations are done in the Web.config file under the \<system.serviceModel> element.</span></span>

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

 <span data-ttu-id="8fadb-118">ScriptManager hizmetle etkileşimi yönetir ve JSONP erişimini el ile uygulamanın karmaşıklığını gizler.</span><span class="sxs-lookup"><span data-stu-id="8fadb-118">ScriptManager manages the interaction with the service and hides away the complexity of manually implementing JSONP access.</span></span> <span data-ttu-id="8fadb-119">Ne `crossDomainScriptAccessEnabled` zaman `true` ayarlanır ve bir işlem için yanıt biçimi JSON olduğunu, WCF altyapısı bir geri arama sorgusu dize parametresi için istek URI inceler ve geri arama sorgusu dize parametresi değeri ile JSON yanıtı sarar.</span><span class="sxs-lookup"><span data-stu-id="8fadb-119">When `crossDomainScriptAccessEnabled` is set to `true` and the response format for an operation is JSON, the WCF infrastructure inspects the URI of the request for a callback query string parameter and wraps the JSON response with the value of the callback query string parameter.</span></span> <span data-ttu-id="8fadb-120">Örnekte, Web sayfası WCF REST hizmetini aşağıdaki URI ile çağırır.</span><span class="sxs-lookup"><span data-stu-id="8fadb-120">In the sample, the Web page calls the WCF REST service with the following URI.</span></span>

```http
http://localhost:33695/CustomerService/GetCustomer?callback=Sys._json0
```

 <span data-ttu-id="8fadb-121">Geri arama sorgusu dize parametresi `JsonPCallback`değeri olduğundan, WCF hizmeti aşağıdaki örnekte gösterilen bir JSONP yanıtını döndürür.</span><span class="sxs-lookup"><span data-stu-id="8fadb-121">Because the callback query string parameter has a value of `JsonPCallback`, the WCF service returns a JSONP response shown in the following example.</span></span>

```json
Sys._json0({"__type":"Customer:#Microsoft.Samples.Jsonp","Address":"1 Example Way","Name":"Bob"});
```

 <span data-ttu-id="8fadb-122">Bu JSONP yanıtı, Web sayfasının istediği geri arama işlevi adı ile sarılmış JSON olarak biçimlendirilmiş müşteri verilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="8fadb-122">This JSONP response includes the customer data formatted as JSON, wrapped with the callback function name that the Web page requested.</span></span> <span data-ttu-id="8fadb-123">ScriptManager, etki alanı arası isteği gerçekleştirmek için bir komut dosyası etiketi kullanarak bu geri aramayı yürütecek ve sonucu ASP.NET AJAX proxy'sinin GetCustomer işlemine geçirilen onSuccess işleyicisine iletir.</span><span class="sxs-lookup"><span data-stu-id="8fadb-123">ScriptManager will execute this callback using a script tag to accomplish the cross-domain request, and then pass the result to the onSuccess handler that was passed to the GetCustomer operation of the ASP.NET AJAX proxy.</span></span>

 <span data-ttu-id="8fadb-124">Örnek iki ASP.NET web uygulamasından oluşur: biri yalnızca bir WCF hizmeti içerir, diğeri ise hizmeti çağıran .aspx web sayfasını içerir.</span><span class="sxs-lookup"><span data-stu-id="8fadb-124">The sample consists of two ASP.NET web applications: one contains just a WCF service, and another one contains the .aspx webpage, which calls the service.</span></span> <span data-ttu-id="8fadb-125">Visual Studio 2012, çözümü çalıştırırken, iki web sitesini farklı bağlantı noktalarında barındıracak ve bu da hizmetin ve istemcinin farklı etki alanlarında yaşadığı bir ortam oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8fadb-125">When running the solution, Visual Studio 2012 will host the two websites on different ports, which creates an environment where the service and client live on different domains.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8fadb-126">Numuneler makinenize zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="8fadb-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="8fadb-127">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="8fadb-127">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="8fadb-128">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="8fadb-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8fadb-129">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="8fadb-129">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\JSONP`  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="8fadb-130">Örnek çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="8fadb-130">To run the sample</span></span>  
  
1. <span data-ttu-id="8fadb-131">JSONP Örneği için çözümü açın.</span><span class="sxs-lookup"><span data-stu-id="8fadb-131">Open the solution for the JSONP Sample.</span></span>  
  
2. <span data-ttu-id="8fadb-132">Tarayıcıda başlatmak `http://localhost:26648/JSONPClientPage.aspx` için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="8fadb-132">Press F5 to launch `http://localhost:26648/JSONPClientPage.aspx` in the browser.</span></span>  
  
3. <span data-ttu-id="8fadb-133">Sayfa yüklendikten sonra "Ad" ve "Adres" metin girişlerinin değerlerle doldurulur.</span><span class="sxs-lookup"><span data-stu-id="8fadb-133">Notice that after the page loads, the text inputs for "Name" and "Address" are populated by values.</span></span>  <span data-ttu-id="8fadb-134">Bu değerler, tarayıcı sayfayı oluşturmayı bitirdikten sonra WCF hizmetine yapılan bir aramadan sağlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="8fadb-134">These values were supplied from a call to the WCF service after the browser finished rendering the page.</span></span>
