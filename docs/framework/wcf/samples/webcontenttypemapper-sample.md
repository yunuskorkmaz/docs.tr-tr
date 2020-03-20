---
title: WebContentTypeMapper Örneği
ms.date: 03/30/2017
ms.assetid: a4fe59e7-44d8-43c6-a1f8-40c45223adca
ms.openlocfilehash: 540e5e775cf7b2a5a5b585d98772415653fa833a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143570"
---
# <a name="webcontenttypemapper-sample"></a><span data-ttu-id="10deb-102">WebContentTypeMapper Örneği</span><span class="sxs-lookup"><span data-stu-id="10deb-102">WebContentTypeMapper Sample</span></span>
<span data-ttu-id="10deb-103">Bu örnek, yeni içerik türlerinin Windows Communication Foundation (WCF) ileti gövdesi biçimleriyle nasıl eşlendirilebildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="10deb-103">This sample demonstrates how to map new content types to Windows Communication Foundation (WCF) message body formats.</span></span>  
  
 <span data-ttu-id="10deb-104">WCF'nin <xref:System.ServiceModel.Description.WebHttpEndpoint> aynı uç noktada JSON, XML veya ham ikili iletiler almasını sağlayan Web iletisi kodlayıcısındaki öğe takılır.</span><span class="sxs-lookup"><span data-stu-id="10deb-104">The <xref:System.ServiceModel.Description.WebHttpEndpoint> element plugs in the Web message encoder, which allows WCF to receive JSON, XML, or raw binary messages at the same endpoint.</span></span> <span data-ttu-id="10deb-105">Kodlayıcı, isteğin HTTP içerik türüne bakarak iletinin gövde biçimini belirler.</span><span class="sxs-lookup"><span data-stu-id="10deb-105">The encoder determines the body format of the message by looking at the HTTP content-type of the request.</span></span> <span data-ttu-id="10deb-106">Bu örnek, <xref:System.ServiceModel.Channels.WebContentTypeMapper> kullanıcının içerik türü ve gövde biçimi arasındaki eşlemi denetlemesini sağlayan sınıfı tanıtır.</span><span class="sxs-lookup"><span data-stu-id="10deb-106">This sample introduces the <xref:System.ServiceModel.Channels.WebContentTypeMapper> class, which allows the user to control the mapping between content type and body format.</span></span>  
  
 <span data-ttu-id="10deb-107">WCF, içerik türleri için varsayılan eşlemeler kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="10deb-107">WCF provides a set of default mappings for content types.</span></span> <span data-ttu-id="10deb-108">Örneğin, `application/json` JSON haritaları `text/xml` ve XML eşler.</span><span class="sxs-lookup"><span data-stu-id="10deb-108">For example, `application/json` maps to JSON and `text/xml` maps to XML.</span></span> <span data-ttu-id="10deb-109">JSON veya XML'e eşlenmemiş herhangi bir içerik türü ham ikili biçime eşlenir.</span><span class="sxs-lookup"><span data-stu-id="10deb-109">Any content type that is not mapped to JSON or XML is mapped to raw binary format.</span></span>  
  
 <span data-ttu-id="10deb-110">Bazı senaryolarda (örneğin, push-style API'ler), hizmet geliştiricisi istemci tarafından döndürülen içerik türünü denetlemez.</span><span class="sxs-lookup"><span data-stu-id="10deb-110">In some scenarios (for example, push-style APIs), the service developer does not control the content type returned by the client.</span></span> <span data-ttu-id="10deb-111">Örneğin, istemciler JSON `text/javascript` yerine `application/json`döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="10deb-111">For example, clients might return JSON as `text/javascript` instead of `application/json`.</span></span> <span data-ttu-id="10deb-112">Bu durumda, hizmet geliştiricisi, aşağıdaki örnek <xref:System.ServiceModel.Channels.WebContentTypeMapper> kodda gösterildiği gibi, verilen içerik türünü doğru şekilde işlemek için türetilen bir tür sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="10deb-112">In this case, the service developer must provide a type that derives from <xref:System.ServiceModel.Channels.WebContentTypeMapper> to handle the given content type correctly, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="10deb-113">Tür <xref:System.ServiceModel.Channels.WebContentTypeMapper.GetMessageFormatForContentType%28System.String%29> yöntemi geçersiz kılmalı.</span><span class="sxs-lookup"><span data-stu-id="10deb-113">The type must override the <xref:System.ServiceModel.Channels.WebContentTypeMapper.GetMessageFormatForContentType%28System.String%29> method.</span></span> <span data-ttu-id="10deb-114">Yöntem `contentType` bağımsız değişkeni değerlendirmeli ve aşağıdaki <xref:System.ServiceModel.Channels.WebContentFormat.Json>değerlerden birini döndürmelidir: , , <xref:System.ServiceModel.Channels.WebContentFormat.Xml> <xref:System.ServiceModel.Channels.WebContentFormat.Raw>, veya <xref:System.ServiceModel.Channels.WebContentFormat.Default>.</span><span class="sxs-lookup"><span data-stu-id="10deb-114">The method must evaluate the `contentType` argument and return one of the following values: <xref:System.ServiceModel.Channels.WebContentFormat.Json>, <xref:System.ServiceModel.Channels.WebContentFormat.Xml>, <xref:System.ServiceModel.Channels.WebContentFormat.Raw>, or <xref:System.ServiceModel.Channels.WebContentFormat.Default>.</span></span> <span data-ttu-id="10deb-115">Varsayılan <xref:System.ServiceModel.Channels.WebContentFormat.Default> Web iletisi kodlayıcı eşlemelerine ertelemeler.</span><span class="sxs-lookup"><span data-stu-id="10deb-115">Returning <xref:System.ServiceModel.Channels.WebContentFormat.Default> defers to the default Web message encoder mappings.</span></span> <span data-ttu-id="10deb-116">Önceki örnek kodda `text/javascript` içerik türü JSON'a eşlenir ve diğer tüm eşlemeler değişmeden kalır.</span><span class="sxs-lookup"><span data-stu-id="10deb-116">In the previous sample code, the `text/javascript` content type is mapped to JSON, and all other mappings remain unchanged.</span></span>  
  
 <span data-ttu-id="10deb-117">`JsonContentTypeMapper` Sınıfı kullanmak için Web.config'inizde aşağıdakileri kullanın:</span><span class="sxs-lookup"><span data-stu-id="10deb-117">To use the `JsonContentTypeMapper` class, use the following in your Web.config:</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>  
    <webHttpEndpoint>  
      <standardEndpoint name="" contentTypeMapper="Microsoft.Samples.WebContentTypeMapper.JsonContentTypeMapper, JsonContentTypeMapper, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
    </webHttpEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="10deb-118">JsonContentTypeMapper'ı kullanma gereksinimini doğrulamak için yukarıdaki yapılandırma dosyasından contentTypeMapper özniteliğini kaldırın.</span><span class="sxs-lookup"><span data-stu-id="10deb-118">To verify the requirement for using the JsonContentTypeMapper, remove the contentTypeMapper attribute from the above configuration file.</span></span> <span data-ttu-id="10deb-119">İstemci sayfası JSON içeriğini `text/javascript` göndermeye çalışırken yüklenmez.</span><span class="sxs-lookup"><span data-stu-id="10deb-119">The client page fails to load when attempting to use `text/javascript` to send JSON content.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="10deb-120">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="10deb-120">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="10deb-121">Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.</span><span class="sxs-lookup"><span data-stu-id="10deb-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="10deb-122">[Windows İletişim Temel Örnekleri Bina](../../../../docs/framework/wcf/samples/building-the-samples.md)açıklandığı gibi çözüm WebContentTypeMapperSample.sln oluşturun.</span><span class="sxs-lookup"><span data-stu-id="10deb-122">Build the solution WebContentTypeMapperSample.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="10deb-123">Gidin `http://localhost/ServiceModelSamples/JCTMClientPage.htm` (proje dizininin içinden tarayıcıda JCTMClientPage.htm'yi açmayın).</span><span class="sxs-lookup"><span data-stu-id="10deb-123">Navigate to `http://localhost/ServiceModelSamples/JCTMClientPage.htm` (do not open JCTMClientPage.htm in the browser from within the project directory).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="10deb-124">Numuneler makinenize zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="10deb-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="10deb-125">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="10deb-125">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="10deb-126">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="10deb-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="10deb-127">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="10deb-127">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Ajax\WebContentTypeMapper`  
