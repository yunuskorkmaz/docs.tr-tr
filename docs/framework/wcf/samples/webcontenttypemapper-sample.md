---
title: WebContentTypeMapper Örneği
ms.date: 03/30/2017
ms.assetid: a4fe59e7-44d8-43c6-a1f8-40c45223adca
ms.openlocfilehash: 91e5cca478521a343f7528f878f114b85eff2d08
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44262524"
---
# <a name="webcontenttypemapper-sample"></a><span data-ttu-id="df4c4-102">WebContentTypeMapper Örneği</span><span class="sxs-lookup"><span data-stu-id="df4c4-102">WebContentTypeMapper Sample</span></span>
<span data-ttu-id="df4c4-103">Bu örnek, yeni içerik türleri için Windows Communication Foundation (WCF) ileti gövdesi biçimleri eşlemeyle ilgili bilgi gösterir.</span><span class="sxs-lookup"><span data-stu-id="df4c4-103">This sample demonstrates how to map new content types to Windows Communication Foundation (WCF) message body formats.</span></span>  
  
 <span data-ttu-id="df4c4-104"><xref:System.ServiceModel.Description.WebHttpEndpoint> Öğesi bağlayacaktır JSON, XML veya aynı uç noktasında ham ikili iletileri almak WCF sağlayan Web ileti Kodlayıcı.</span><span class="sxs-lookup"><span data-stu-id="df4c4-104">The <xref:System.ServiceModel.Description.WebHttpEndpoint> element plugs in the Web message encoder, which allows WCF to receive JSON, XML, or raw binary messages at the same endpoint.</span></span> <span data-ttu-id="df4c4-105">Kodlayıcı, HTTP content-type, isteğin bakarak iletinin gövdesi biçimini belirler.</span><span class="sxs-lookup"><span data-stu-id="df4c4-105">The encoder determines the body format of the message by looking at the HTTP content-type of the request.</span></span> <span data-ttu-id="df4c4-106">Bu örnek tanıtır <xref:System.ServiceModel.Channels.WebContentTypeMapper> içerik türü ve gövde biçimi arasındaki eşlemeyi denetlemek kullanıcının sağlar sınıfını.</span><span class="sxs-lookup"><span data-stu-id="df4c4-106">This sample introduces the <xref:System.ServiceModel.Channels.WebContentTypeMapper> class, which allows the user to control the mapping between content type and body format.</span></span>  
  
 <span data-ttu-id="df4c4-107">WCF içerik türleri için varsayılan eşlemeleri sunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="df4c4-107">WCF provides a set of default mappings for content types.</span></span> <span data-ttu-id="df4c4-108">Örneğin, `application/json` JSON değerine eşleyen ve `text/xml` eşleyen XML.</span><span class="sxs-lookup"><span data-stu-id="df4c4-108">For example, `application/json` maps to JSON and `text/xml` maps to XML.</span></span> <span data-ttu-id="df4c4-109">JSON veya XML eşlenmemiş herhangi bir içerik türüne ham ikili biçime eşlenir.</span><span class="sxs-lookup"><span data-stu-id="df4c4-109">Any content type that is not mapped to JSON or XML is mapped to raw binary format.</span></span>  
  
 <span data-ttu-id="df4c4-110">Bazı senaryolarda (örneğin, anında iletme stili API), istemci tarafından döndürülen içerik türü service Geliştirici denetlemez.</span><span class="sxs-lookup"><span data-stu-id="df4c4-110">In some scenarios (for example, push-style APIs), the service developer does not control the content type returned by the client.</span></span> <span data-ttu-id="df4c4-111">Örneğin, istemcilerin JSON olarak döndürebilir `text/javascript` yerine `application/json`.</span><span class="sxs-lookup"><span data-stu-id="df4c4-111">For example, clients might return JSON as `text/javascript` instead of `application/json`.</span></span> <span data-ttu-id="df4c4-112">Bu durumda, hizmet geliştirici, türetilen bir tür sağlamalısınız <xref:System.ServiceModel.Channels.WebContentTypeMapper> belirtilen içerik türü aşağıdaki örnek kodda gösterildiği gibi doğru şekilde işlemek için.</span><span class="sxs-lookup"><span data-stu-id="df4c4-112">In this case, the service developer must provide a type that derives from <xref:System.ServiceModel.Channels.WebContentTypeMapper> to handle the given content type correctly, as shown in the following sample code.</span></span>  
  
```  
public class JsonContentTypeMapper : WebContentTypeMapper  
{  
    public override WebContentFormat  
               GetMessageFormatForContentType(string contentType)  
    {  
        if (contentType == "text/javascript")  
        {  
            return WebContentFormat.Json;  
        }  
        else  
        {  
            return WebContentFormat.Default;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="df4c4-113">Türü geçersiz kılmanız gerekir <xref:System.ServiceModel.Channels.WebContentTypeMapper.GetMessageFormatForContentType%28System.String%29> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="df4c4-113">The type must override the <xref:System.ServiceModel.Channels.WebContentTypeMapper.GetMessageFormatForContentType%28System.String%29> method.</span></span> <span data-ttu-id="df4c4-114">Yöntem değerlendirmelidir `contentType` bağımsız değişkeni ve dönüş aşağıdaki değerlerden biri: <xref:System.ServiceModel.Channels.WebContentFormat.Json>, <xref:System.ServiceModel.Channels.WebContentFormat.Xml>, <xref:System.ServiceModel.Channels.WebContentFormat.Raw>, veya <xref:System.ServiceModel.Channels.WebContentFormat.Default>.</span><span class="sxs-lookup"><span data-stu-id="df4c4-114">The method must evaluate the `contentType` argument and return one of the following values: <xref:System.ServiceModel.Channels.WebContentFormat.Json>, <xref:System.ServiceModel.Channels.WebContentFormat.Xml>, <xref:System.ServiceModel.Channels.WebContentFormat.Raw>, or <xref:System.ServiceModel.Channels.WebContentFormat.Default>.</span></span> <span data-ttu-id="df4c4-115">Döndüren <xref:System.ServiceModel.Channels.WebContentFormat.Default> varsayılan Web ileti Kodlayıcı eşlemelere erteler.</span><span class="sxs-lookup"><span data-stu-id="df4c4-115">Returning <xref:System.ServiceModel.Channels.WebContentFormat.Default> defers to the default Web message encoder mappings.</span></span> <span data-ttu-id="df4c4-116">Önceki örnek kodda `text/javascript` içerik türü için JSON eşlenen ve diğer tüm eşlemeleri değişmeden kalır.</span><span class="sxs-lookup"><span data-stu-id="df4c4-116">In the previous sample code, the `text/javascript` content type is mapped to JSON, and all other mappings remain unchanged.</span></span>  
  
 <span data-ttu-id="df4c4-117">Kullanılacak `JsonContentTypeMapper` sınıf, uygulamanızın Web.config dosyasında aşağıdakileri kullanın:</span><span class="sxs-lookup"><span data-stu-id="df4c4-117">To use the `JsonContentTypeMapper` class, use the following in your Web.config:</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>  
    <webHttpEndpoint>  
      <standardEndpoint name="" contentTypeMapper="Microsoft.Samples.WebContentTypeMapper.JsonContentTypeMapper, JsonContentTypeMapper, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
    </webHttpEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="df4c4-118">JsonContentTypeMapper kullanma gereksinimi doğrulamak için yukarıdaki yapılandırma dosyasından contentTypeMapper özniteliği kaldırın.</span><span class="sxs-lookup"><span data-stu-id="df4c4-118">To verify the requirement for using the JsonContentTypeMapper, remove the contentTypeMapper attribute from the above configuration file.</span></span> <span data-ttu-id="df4c4-119">İstemci sayfa kullanmaya çalışırken yüklenemiyordur `text/javascript` JSON içerik göndermek için.</span><span class="sxs-lookup"><span data-stu-id="df4c4-119">The client page fails to load when attempting to use `text/javascript` to send JSON content.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="df4c4-120">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="df4c4-120">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="df4c4-121">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="df4c4-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="df4c4-122">' % S'çözüm WebContentTypeMapperSample.sln açıklandığı gibi oluşturmak [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="df4c4-122">Build the solution WebContentTypeMapperSample.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="df4c4-123">Gidin http://localhost/ServiceModelSamples/JCTMClientPage.htm (JCTMClientPage.htm tarayıcıda proje dizininden açmayın).</span><span class="sxs-lookup"><span data-stu-id="df4c4-123">Navigate to http://localhost/ServiceModelSamples/JCTMClientPage.htm (do not open JCTMClientPage.htm in the browser from within the project directory).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="df4c4-124">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="df4c4-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="df4c4-125">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="df4c4-125">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="df4c4-126">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="df4c4-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="df4c4-127">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="df4c4-127">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Ajax\WebContentTypeMapper`  
  
## <a name="see-also"></a><span data-ttu-id="df4c4-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="df4c4-128">See Also</span></span>
