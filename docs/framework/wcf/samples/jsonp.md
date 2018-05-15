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
# <a name="jsonp"></a><span data-ttu-id="b348b-102">JSONP</span><span class="sxs-lookup"><span data-stu-id="b348b-102">JSONP</span></span>
<span data-ttu-id="b348b-103">Bu örnek, JSON ile doldurma (JSONP) WCF REST Hizmetleri'nde desteklemek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b348b-103">This sample demonstrates how to support JSON with Padding (JSONP) in WCF REST services.</span></span> <span data-ttu-id="b348b-104">JSONP geçerli belgede oluşturma komut dosyası etiketlerini tarafından etki alanları arası komut çağırmak için kullanılan bir kuraldır.</span><span class="sxs-lookup"><span data-stu-id="b348b-104">JSONP is a convention used to invoke cross-domain scripts by generating script tags in the current document.</span></span> <span data-ttu-id="b348b-105">Sonuç belirtilen geri çağırma işlevi döndürülür.</span><span class="sxs-lookup"><span data-stu-id="b348b-105">The result is returned in a specified callback function.</span></span> <span data-ttu-id="b348b-106">JSONP gibi etiketler fikir üzerinde temel `<script src="http://..." >` herhangi bir etki alanından betiklerini değerlendirilebilir ve bu etiketlerin tarafından alınan komut dosyası diğer işlevleri zaten tanımlanabilir içinde bir kapsamı içinde değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="b348b-106">JSONP is based on the idea that tags such as `<script src="http://..." >` can evaluate scripts from any domain and the script retrieved by those tags is evaluated within a scope in which other functions may already be defined.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="b348b-107">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="b348b-107">Demonstrates</span></span>  
 <span data-ttu-id="b348b-108">Etki alanları arası JSONP ile komut dosyası.</span><span class="sxs-lookup"><span data-stu-id="b348b-108">Cross-domain scripting with JSONP.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="b348b-109">Tartışma</span><span class="sxs-lookup"><span data-stu-id="b348b-109">Discussion</span></span>  
 <span data-ttu-id="b348b-110">Örnek sayfa işlendiği sonra dinamik olarak bir betik bloğu tarayıcıda ekleyen bir Web sayfası içerir.</span><span class="sxs-lookup"><span data-stu-id="b348b-110">The sample includes a Web page that dynamically adds a script block after the page has been rendered in the browser.</span></span> <span data-ttu-id="b348b-111">Bu betik bloğu tek bir işleme sahip bir WCF REST hizmeti çağrıları `GetCustomer`.</span><span class="sxs-lookup"><span data-stu-id="b348b-111">This script block calls a WCF REST service that has a single operation, `GetCustomer`.</span></span> <span data-ttu-id="b348b-112">WCF REST hizmeti, bir müşterinin adını ve bir geri çağırma işlevi adı Sarmalanan adresini döndürür.</span><span class="sxs-lookup"><span data-stu-id="b348b-112">The WCF REST service returns a customer’s name and address wrapped in a callback function name.</span></span> <span data-ttu-id="b348b-113">WCF REST hizmeti yanıtladığında Web sayfasına geri çağırma işlevi müşteri verileriyle çağrılır ve geri çağırma işlevi Web sayfasında veri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="b348b-113">When the WCF REST service responds, the callback function on the Web page is invoked with the customer data and the callback function displays the data on the Web page.</span></span> <span data-ttu-id="b348b-114">Komut dosyası etiketinin ekleme ve geri çağırma işlevi yürütülmesi ASP.NET AJAX ScriptManager denetimi tarafından otomatik olarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="b348b-114">The injection of the script tag and the execution of the callback function is automatically handled by the ASP.NET AJAX ScriptManager control.</span></span> <span data-ttu-id="b348b-115">Kullanım deseni JSONP, aşağıdaki kodda gösterildiği gibi etkinleştirmek için bir satır eklenmesi ile tüm ASP.NET AJAX proxy'leri ile aynıdır:</span><span class="sxs-lookup"><span data-stu-id="b348b-115">The usage pattern is the same as with all ASP.NET AJAX proxies, with the addition of one line to enable JSONP, as shown in the following code:</span></span>  
  
```csharp  
var proxy = new JsonpAjaxService.CustomerService();  
proxy.set_enableJsonp(true);  
proxy.GetCustomer(onSuccess, onFail, null);  
```  
  
 <span data-ttu-id="b348b-116">Hizmet tarafından kullanıldığından Web sayfası WCF REST hizmeti çağırabilirsiniz <xref:System.ServiceModel.Description.WebScriptEndpoint> ile `crossDomainScriptAccessEnabled` kümesine `true`.</span><span class="sxs-lookup"><span data-stu-id="b348b-116">The Web page can call the WCF REST service because the service is using the <xref:System.ServiceModel.Description.WebScriptEndpoint> with `crossDomainScriptAccessEnabled` set to `true`.</span></span> <span data-ttu-id="b348b-117">Bu yapılandırmalar her ikisi de altında Web.config dosyasında yapılması \<system.serviceModel > öğesi.</span><span class="sxs-lookup"><span data-stu-id="b348b-117">Both of these configurations are done in the Web.config file under the \<system.serviceModel> element.</span></span>  
  
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
  
 <span data-ttu-id="b348b-118">ScriptManager hizmetiyle etkileşimi yönetir ve hemen el ile JSONP erişim uygulama karmaşıklığını gizler.</span><span class="sxs-lookup"><span data-stu-id="b348b-118">ScriptManager manages the interaction with the service and hides away the complexity of manually implementing JSONP access.</span></span> <span data-ttu-id="b348b-119">Zaman `crossDomainScriptAccessEnabled` ayarlanır `true` ve bir işlem yanıt biçimi JSON, WCF altyapı URI isteği bir geri çağırma sorgu dizesi parametresinin değerini inceler ve geri çağırma sorgu dizesi değeri ile JSON yanıt sarmalar parametre.</span><span class="sxs-lookup"><span data-stu-id="b348b-119">When `crossDomainScriptAccessEnabled` is set to `true` and the response format for an operation is JSON, the WCF infrastructure inspects the URI of the request for a callback query string parameter and wraps the JSON response with the value of the callback query string parameter.</span></span> <span data-ttu-id="b348b-120">Örnekte, aşağıdaki URI ile WCF REST hizmeti Web sayfasını çağırır.</span><span class="sxs-lookup"><span data-stu-id="b348b-120">In the sample, the Web page calls the WCF REST service with the following URI.</span></span>  
  
```  
http://localhost:33695/CustomerService/GetCustomer?callback=Sys._json0  
```  
  
 <span data-ttu-id="b348b-121">Geri çağırma sorgu dizesi parametresinin değerini içerdiğinden `JsonPCallback`, WCF hizmeti aşağıdaki örnekte gösterildiği bir JSONP yanıtı döndürür.</span><span class="sxs-lookup"><span data-stu-id="b348b-121">Because the callback query string parameter has a value of `JsonPCallback`, the WCF service returns a JSONP response shown in the following example.</span></span>  
  
```  
Sys._json0({"__type":"Customer:#Microsoft.Samples.Jsonp","Address":"1 Example Way","Name":"Bob"});  
```  
  
 <span data-ttu-id="b348b-122">Bu JSONP yanıt, istenen Web sayfasının geri çağırma işlevi adıyla Sarmalanan JSON olarak biçimlendirilmiş müşteri verilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="b348b-122">This JSONP response includes the customer data formatted as JSON, wrapped with the callback function name that the Web page requested.</span></span> <span data-ttu-id="b348b-123">ScriptManager etki alanları arası istek gerçekleştirmek için bir komut dosyası etiketini kullanarak bu geri çağırma yürütün ve sonra ASP.NET AJAX proxy GetCustomer çalışması için geçirilen onSuccess işleyicisine sonucu geçirin.</span><span class="sxs-lookup"><span data-stu-id="b348b-123">ScriptManager will execute this callback using a script tag to accomplish the cross-domain request, and then pass the result to the onSuccess handler that was passed to the GetCustomer operation of the ASP.NET AJAX proxy.</span></span>  
  
 <span data-ttu-id="b348b-124">Örnek iki ASP.NET web uygulamalarının oluşur: biri yalnızca bir WCF hizmeti ve başka bir hizmeti çağıran .aspx Web sayfası içerir.</span><span class="sxs-lookup"><span data-stu-id="b348b-124">The sample consists of two ASP.NET web applications: one contains just a WCF service, and another one contains the .aspx webpage, which calls the service.</span></span> <span data-ttu-id="b348b-125">Çözüm çalıştırırken [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] farklı bağlantı noktaları üzerindeki iki Web siteleri, burada hizmet ve istemci Canlı farklı etki alanlarında bir ortam oluşturur barındıracak.</span><span class="sxs-lookup"><span data-stu-id="b348b-125">When running the solution, [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] will host the two websites on different ports, which creates an environment where the service and client live on different domains.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b348b-126">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="b348b-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b348b-127">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="b348b-127">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b348b-128">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="b348b-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b348b-129">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="b348b-129">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\JSONP`  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="b348b-130">Örnek çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="b348b-130">To run the sample</span></span>  
  
1.  <span data-ttu-id="b348b-131">Çözüm için JSONP örneği açın.</span><span class="sxs-lookup"><span data-stu-id="b348b-131">Open the solution for the JSONP Sample.</span></span>  
  
2.  <span data-ttu-id="b348b-132">Başlatmak için F5 tuşuna basın `http://localhost:26648/JSONPClientPage.aspx` tarayıcıda.</span><span class="sxs-lookup"><span data-stu-id="b348b-132">Press F5 to launch `http://localhost:26648/JSONPClientPage.aspx` in the browser.</span></span>  
  
3.  <span data-ttu-id="b348b-133">Sayfa yüklendikten sonra "Name" ve "Adres" için metin girişleri değerlerle doldurulur dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="b348b-133">Notice that after the page loads, the text inputs for "Name" and "Address" are populated by values.</span></span>  <span data-ttu-id="b348b-134">Sayfa işleme tarayıcı tamamladıktan sonra bu değerler WCF Hizmeti çağrısından sağlanmadı.</span><span class="sxs-lookup"><span data-stu-id="b348b-134">These values were supplied from a call to the WCF service after the browser finished rendering the page.</span></span>
