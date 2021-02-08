---
description: 'Daha fazla bilgi edinin: WebContentTypeMapper örneği'
title: WebContentTypeMapper Örneği
ms.date: 03/30/2017
ms.assetid: a4fe59e7-44d8-43c6-a1f8-40c45223adca
ms.openlocfilehash: 274672bb8db1dc845b1cc1ced58b4c4a92232e9b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99798153"
---
# <a name="webcontenttypemapper-sample"></a><span data-ttu-id="0cb8b-103">WebContentTypeMapper Örneği</span><span class="sxs-lookup"><span data-stu-id="0cb8b-103">WebContentTypeMapper Sample</span></span>

<span data-ttu-id="0cb8b-104">Bu örnek, yeni içerik türlerinin Windows Communication Foundation (WCF) ileti gövdesi biçimlerine nasıl eşleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0cb8b-104">This sample demonstrates how to map new content types to Windows Communication Foundation (WCF) message body formats.</span></span>  
  
 <span data-ttu-id="0cb8b-105"><xref:System.ServiceModel.Description.WebHttpEndpoint>Öğesi, WCF 'nin aynı uç noktada JSON, XML veya ham ikili mesajlar almasına izin veren Web ileti Kodlayıcısı ' nı takar.</span><span class="sxs-lookup"><span data-stu-id="0cb8b-105">The <xref:System.ServiceModel.Description.WebHttpEndpoint> element plugs in the Web message encoder, which allows WCF to receive JSON, XML, or raw binary messages at the same endpoint.</span></span> <span data-ttu-id="0cb8b-106">Kodlayıcı, isteğin HTTP içerik türüne bakarak iletinin gövde biçimini belirler.</span><span class="sxs-lookup"><span data-stu-id="0cb8b-106">The encoder determines the body format of the message by looking at the HTTP content-type of the request.</span></span> <span data-ttu-id="0cb8b-107">Bu örnek <xref:System.ServiceModel.Channels.WebContentTypeMapper> , kullanıcının içerik türü ve gövde biçimi arasındaki eşlemeyi denetlemesine olanak tanıyan sınıfını tanıtır.</span><span class="sxs-lookup"><span data-stu-id="0cb8b-107">This sample introduces the <xref:System.ServiceModel.Channels.WebContentTypeMapper> class, which allows the user to control the mapping between content type and body format.</span></span>  
  
 <span data-ttu-id="0cb8b-108">WCF, içerik türleri için bir varsayılan eşlemeler kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="0cb8b-108">WCF provides a set of default mappings for content types.</span></span> <span data-ttu-id="0cb8b-109">Örneğin, `application/json` JSON ile eşlenir ve `text/xml` XML ile eşlenir.</span><span class="sxs-lookup"><span data-stu-id="0cb8b-109">For example, `application/json` maps to JSON and `text/xml` maps to XML.</span></span> <span data-ttu-id="0cb8b-110">JSON veya XML ile eşlenmemiş herhangi bir içerik türü ham ikili biçime eşlenir.</span><span class="sxs-lookup"><span data-stu-id="0cb8b-110">Any content type that is not mapped to JSON or XML is mapped to raw binary format.</span></span>  
  
 <span data-ttu-id="0cb8b-111">Bazı senaryolarda (örneğin, gönderme stili API 'Leri), hizmet geliştiricisi istemci tarafından döndürülen içerik türünü denetlemez.</span><span class="sxs-lookup"><span data-stu-id="0cb8b-111">In some scenarios (for example, push-style APIs), the service developer does not control the content type returned by the client.</span></span> <span data-ttu-id="0cb8b-112">Örneğin, istemciler yerine JSON döndürebilir `text/javascript` `application/json` .</span><span class="sxs-lookup"><span data-stu-id="0cb8b-112">For example, clients might return JSON as `text/javascript` instead of `application/json`.</span></span> <span data-ttu-id="0cb8b-113">Bu durumda, hizmet geliştiricisi <xref:System.ServiceModel.Channels.WebContentTypeMapper> Aşağıdaki örnek kodda gösterildiği gibi, verilen içerik türünü doğru bir şekilde işlemek için öğesinden türetilen bir tür sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="0cb8b-113">In this case, the service developer must provide a type that derives from <xref:System.ServiceModel.Channels.WebContentTypeMapper> to handle the given content type correctly, as shown in the following sample code.</span></span>  
  
```csharp  
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
  
 <span data-ttu-id="0cb8b-114">Tür, yöntemi geçersiz kılmalıdır <xref:System.ServiceModel.Channels.WebContentTypeMapper.GetMessageFormatForContentType%28System.String%29> .</span><span class="sxs-lookup"><span data-stu-id="0cb8b-114">The type must override the <xref:System.ServiceModel.Channels.WebContentTypeMapper.GetMessageFormatForContentType%28System.String%29> method.</span></span> <span data-ttu-id="0cb8b-115">Yöntemi, `contentType` bağımsız değişkeni değerlendirmeli ve şu değerlerden birini döndürmelidir: <xref:System.ServiceModel.Channels.WebContentFormat.Json> , <xref:System.ServiceModel.Channels.WebContentFormat.Xml> , <xref:System.ServiceModel.Channels.WebContentFormat.Raw> veya <xref:System.ServiceModel.Channels.WebContentFormat.Default> .</span><span class="sxs-lookup"><span data-stu-id="0cb8b-115">The method must evaluate the `contentType` argument and return one of the following values: <xref:System.ServiceModel.Channels.WebContentFormat.Json>, <xref:System.ServiceModel.Channels.WebContentFormat.Xml>, <xref:System.ServiceModel.Channels.WebContentFormat.Raw>, or <xref:System.ServiceModel.Channels.WebContentFormat.Default>.</span></span> <span data-ttu-id="0cb8b-116"><xref:System.ServiceModel.Channels.WebContentFormat.Default>Varsayılan Web ileti Kodlayıcısı eşlemelerine erteleyiciler döndürülüyor.</span><span class="sxs-lookup"><span data-stu-id="0cb8b-116">Returning <xref:System.ServiceModel.Channels.WebContentFormat.Default> defers to the default Web message encoder mappings.</span></span> <span data-ttu-id="0cb8b-117">Önceki örnek kodda, `text/javascript` içerik türü json ile eşlenir ve diğer tüm eşlemeler değişmeden kalır.</span><span class="sxs-lookup"><span data-stu-id="0cb8b-117">In the previous sample code, the `text/javascript` content type is mapped to JSON, and all other mappings remain unchanged.</span></span>  
  
 <span data-ttu-id="0cb8b-118">Sınıfını kullanmak için `JsonContentTypeMapper` Web.config aşağıdakileri kullanın:</span><span class="sxs-lookup"><span data-stu-id="0cb8b-118">To use the `JsonContentTypeMapper` class, use the following in your Web.config:</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>  
    <webHttpEndpoint>  
      <standardEndpoint name="" contentTypeMapper="Microsoft.Samples.WebContentTypeMapper.JsonContentTypeMapper, JsonContentTypeMapper, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
    </webHttpEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="0cb8b-119">JsonContentTypeMapper kullanma gereksinimini doğrulamak için, yukarıdaki yapılandırma dosyasından contentTypeMapper özniteliğini kaldırın.</span><span class="sxs-lookup"><span data-stu-id="0cb8b-119">To verify the requirement for using the JsonContentTypeMapper, remove the contentTypeMapper attribute from the above configuration file.</span></span> <span data-ttu-id="0cb8b-120">JSON içeriğini göndermek için kullanılmaya çalışıldığında istemci sayfası yükleme başarısız olur `text/javascript` .</span><span class="sxs-lookup"><span data-stu-id="0cb8b-120">The client page fails to load when attempting to use `text/javascript` to send JSON content.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0cb8b-121">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="0cb8b-121">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="0cb8b-122">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="0cb8b-122">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="0cb8b-123">[Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)bölümünde açıklandığı gibi WebContentTypeMapperSample. sln çözümünü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0cb8b-123">Build the solution WebContentTypeMapperSample.sln as described in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="0cb8b-124">' A gidin `http://localhost/ServiceModelSamples/JCTMClientPage.htm` (tarayıcıda JCTMClientPage.htm proje dizininden açmayın).</span><span class="sxs-lookup"><span data-stu-id="0cb8b-124">Navigate to `http://localhost/ServiceModelSamples/JCTMClientPage.htm` (do not open JCTMClientPage.htm in the browser from within the project directory).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="0cb8b-125">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="0cb8b-125">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0cb8b-126">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="0cb8b-126">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="0cb8b-127">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="0cb8b-127">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0cb8b-128">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="0cb8b-128">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Ajax\WebContentTypeMapper`  
