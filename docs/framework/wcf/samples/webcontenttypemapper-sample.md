---
title: WebContentTypeMapper Örneği
ms.date: 03/30/2017
ms.assetid: a4fe59e7-44d8-43c6-a1f8-40c45223adca
ms.openlocfilehash: 1b15651859fd17673caf898df02c2b74a85d7612
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038535"
---
# <a name="webcontenttypemapper-sample"></a><span data-ttu-id="5a893-102">WebContentTypeMapper Örneği</span><span class="sxs-lookup"><span data-stu-id="5a893-102">WebContentTypeMapper Sample</span></span>
<span data-ttu-id="5a893-103">Bu örnek, yeni içerik türlerinin Windows Communication Foundation (WCF) ileti gövdesi biçimlerine nasıl eşleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="5a893-103">This sample demonstrates how to map new content types to Windows Communication Foundation (WCF) message body formats.</span></span>  
  
 <span data-ttu-id="5a893-104"><xref:System.ServiceModel.Description.WebHttpEndpoint> Öğesi, WCF 'nin aynı uç noktada JSON, XML veya ham ikili mesajlar almasına izin veren Web ileti Kodlayıcısı ' nı takar.</span><span class="sxs-lookup"><span data-stu-id="5a893-104">The <xref:System.ServiceModel.Description.WebHttpEndpoint> element plugs in the Web message encoder, which allows WCF to receive JSON, XML, or raw binary messages at the same endpoint.</span></span> <span data-ttu-id="5a893-105">Kodlayıcı, isteğin HTTP içerik türüne bakarak iletinin gövde biçimini belirler.</span><span class="sxs-lookup"><span data-stu-id="5a893-105">The encoder determines the body format of the message by looking at the HTTP content-type of the request.</span></span> <span data-ttu-id="5a893-106">Bu örnek, kullanıcının <xref:System.ServiceModel.Channels.WebContentTypeMapper> içerik türü ve gövde biçimi arasındaki eşlemeyi denetlemesine olanak tanıyan sınıfını tanıtır.</span><span class="sxs-lookup"><span data-stu-id="5a893-106">This sample introduces the <xref:System.ServiceModel.Channels.WebContentTypeMapper> class, which allows the user to control the mapping between content type and body format.</span></span>  
  
 <span data-ttu-id="5a893-107">WCF, içerik türleri için bir varsayılan eşlemeler kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="5a893-107">WCF provides a set of default mappings for content types.</span></span> <span data-ttu-id="5a893-108">Örneğin, `application/json` JSON ile eşlenir ve `text/xml` XML ile eşlenir.</span><span class="sxs-lookup"><span data-stu-id="5a893-108">For example, `application/json` maps to JSON and `text/xml` maps to XML.</span></span> <span data-ttu-id="5a893-109">JSON veya XML ile eşlenmemiş herhangi bir içerik türü ham ikili biçime eşlenir.</span><span class="sxs-lookup"><span data-stu-id="5a893-109">Any content type that is not mapped to JSON or XML is mapped to raw binary format.</span></span>  
  
 <span data-ttu-id="5a893-110">Bazı senaryolarda (örneğin, gönderme stili API 'Leri), hizmet geliştiricisi istemci tarafından döndürülen içerik türünü denetlemez.</span><span class="sxs-lookup"><span data-stu-id="5a893-110">In some scenarios (for example, push-style APIs), the service developer does not control the content type returned by the client.</span></span> <span data-ttu-id="5a893-111">Örneğin, istemciler `text/javascript` `application/json`yerine JSON döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="5a893-111">For example, clients might return JSON as `text/javascript` instead of `application/json`.</span></span> <span data-ttu-id="5a893-112">Bu durumda, hizmet geliştiricisi aşağıdaki örnek kodda gösterildiği gibi, verilen içerik türünü <xref:System.ServiceModel.Channels.WebContentTypeMapper> doğru bir şekilde işlemek için öğesinden türetilen bir tür sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="5a893-112">In this case, the service developer must provide a type that derives from <xref:System.ServiceModel.Channels.WebContentTypeMapper> to handle the given content type correctly, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="5a893-113">Tür, <xref:System.ServiceModel.Channels.WebContentTypeMapper.GetMessageFormatForContentType%28System.String%29> yöntemi geçersiz kılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5a893-113">The type must override the <xref:System.ServiceModel.Channels.WebContentTypeMapper.GetMessageFormatForContentType%28System.String%29> method.</span></span> <span data-ttu-id="5a893-114">Yöntemi `contentType` , bağımsız değişkeni değerlendirmeli ve şu değerlerden birini döndürmelidir: <xref:System.ServiceModel.Channels.WebContentFormat.Xml> <xref:System.ServiceModel.Channels.WebContentFormat.Json>,, <xref:System.ServiceModel.Channels.WebContentFormat.Raw>veya <xref:System.ServiceModel.Channels.WebContentFormat.Default>.</span><span class="sxs-lookup"><span data-stu-id="5a893-114">The method must evaluate the `contentType` argument and return one of the following values: <xref:System.ServiceModel.Channels.WebContentFormat.Json>, <xref:System.ServiceModel.Channels.WebContentFormat.Xml>, <xref:System.ServiceModel.Channels.WebContentFormat.Raw>, or <xref:System.ServiceModel.Channels.WebContentFormat.Default>.</span></span> <span data-ttu-id="5a893-115">Varsayılan <xref:System.ServiceModel.Channels.WebContentFormat.Default> Web ileti Kodlayıcısı eşlemelerine erteleyiciler döndürülüyor.</span><span class="sxs-lookup"><span data-stu-id="5a893-115">Returning <xref:System.ServiceModel.Channels.WebContentFormat.Default> defers to the default Web message encoder mappings.</span></span> <span data-ttu-id="5a893-116">Önceki örnek kodda, `text/javascript` içerik türü json ile eşlenir ve diğer tüm eşlemeler değişmeden kalır.</span><span class="sxs-lookup"><span data-stu-id="5a893-116">In the previous sample code, the `text/javascript` content type is mapped to JSON, and all other mappings remain unchanged.</span></span>  
  
 <span data-ttu-id="5a893-117">`JsonContentTypeMapper` Sınıfını kullanmak için, Web. config dosyasında aşağıdakileri kullanın:</span><span class="sxs-lookup"><span data-stu-id="5a893-117">To use the `JsonContentTypeMapper` class, use the following in your Web.config:</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>  
    <webHttpEndpoint>  
      <standardEndpoint name="" contentTypeMapper="Microsoft.Samples.WebContentTypeMapper.JsonContentTypeMapper, JsonContentTypeMapper, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
    </webHttpEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="5a893-118">JsonContentTypeMapper kullanma gereksinimini doğrulamak için, yukarıdaki yapılandırma dosyasından contentTypeMapper özniteliğini kaldırın.</span><span class="sxs-lookup"><span data-stu-id="5a893-118">To verify the requirement for using the JsonContentTypeMapper, remove the contentTypeMapper attribute from the above configuration file.</span></span> <span data-ttu-id="5a893-119">JSON içeriğini göndermek için kullanılmaya `text/javascript` çalışıldığında istemci sayfası yükleme başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="5a893-119">The client page fails to load when attempting to use `text/javascript` to send JSON content.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5a893-120">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="5a893-120">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="5a893-121">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="5a893-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="5a893-122">[Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)bölümünde açıklandığı gibi WebContentTypeMapperSample. sln çözümünü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5a893-122">Build the solution WebContentTypeMapperSample.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="5a893-123">' A gidin (bir proje dizininin içinden JCTMClientPage. htm dosyasını tarayıcıda açmayın). `http://localhost/ServiceModelSamples/JCTMClientPage.htm`</span><span class="sxs-lookup"><span data-stu-id="5a893-123">Navigate to `http://localhost/ServiceModelSamples/JCTMClientPage.htm` (do not open JCTMClientPage.htm in the browser from within the project directory).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5a893-124">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="5a893-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5a893-125">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="5a893-125">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="5a893-126">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin.</span><span class="sxs-lookup"><span data-stu-id="5a893-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5a893-127">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="5a893-127">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Ajax\WebContentTypeMapper`  
