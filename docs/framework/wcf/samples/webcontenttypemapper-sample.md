---
title: "WebContentTypeMapper Örneği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a4fe59e7-44d8-43c6-a1f8-40c45223adca
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 34adf191d3edbff33fe989cf036c32104a6754ae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="webcontenttypemapper-sample"></a><span data-ttu-id="b1c7e-102">WebContentTypeMapper Örneği</span><span class="sxs-lookup"><span data-stu-id="b1c7e-102">WebContentTypeMapper Sample</span></span>
<span data-ttu-id="b1c7e-103">Bu örnek, yeni içerik türlerine eşlemek gösterilmiştir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ileti gövdesi biçimleri.</span><span class="sxs-lookup"><span data-stu-id="b1c7e-103">This sample demonstrates how to map new content types to [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] message body formats.</span></span>  
  
 <span data-ttu-id="b1c7e-104"><xref:System.ServiceModel.Description.WebHttpEndpoint> Öğesi takılan sağlayan Web ileti Kodlayıcı içinde [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] JSON, XML veya aynı uç noktada ham ikili iletileri almak için.</span><span class="sxs-lookup"><span data-stu-id="b1c7e-104">The <xref:System.ServiceModel.Description.WebHttpEndpoint> element plugs in the Web message encoder, which allows [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] to receive JSON, XML, or raw binary messages at the same endpoint.</span></span> <span data-ttu-id="b1c7e-105">Kodlayıcı HTTP content-type, isteğin bakarak ileti gövdesinin biçimi belirler.</span><span class="sxs-lookup"><span data-stu-id="b1c7e-105">The encoder determines the body format of the message by looking at the HTTP content-type of the request.</span></span> <span data-ttu-id="b1c7e-106">Bu örnek tanıtır <xref:System.ServiceModel.Channels.WebContentTypeMapper> kullanıcının içerik türü ve gövde biçimi arasında eşleme denetlemesine olanak sağlayan sınıf.</span><span class="sxs-lookup"><span data-stu-id="b1c7e-106">This sample introduces the <xref:System.ServiceModel.Channels.WebContentTypeMapper> class, which allows the user to control the mapping between content type and body format.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="b1c7e-107">içerik türleri için varsayılan eşlemeleri kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="b1c7e-107"> provides a set of default mappings for content types.</span></span> <span data-ttu-id="b1c7e-108">Örneğin, `application/json` eşler için JSON ve `text/xml` XML eşler.</span><span class="sxs-lookup"><span data-stu-id="b1c7e-108">For example, `application/json` maps to JSON and `text/xml` maps to XML.</span></span> <span data-ttu-id="b1c7e-109">Ham ikili biçime JSON veya XML eşlenmemiş herhangi bir içerik türüne eşlenir.</span><span class="sxs-lookup"><span data-stu-id="b1c7e-109">Any content type that is not mapped to JSON or XML is mapped to raw binary format.</span></span>  
  
 <span data-ttu-id="b1c7e-110">Bazı senaryolarda (örneğin, anında iletme stili API), istemci tarafından döndürülen içerik türü hizmet Geliştirici denetlemez.</span><span class="sxs-lookup"><span data-stu-id="b1c7e-110">In some scenarios (for example, push-style APIs), the service developer does not control the content type returned by the client.</span></span> <span data-ttu-id="b1c7e-111">Örneğin, istemcilerin JSON olarak döndürebilir `text/javascript` yerine `application/json`.</span><span class="sxs-lookup"><span data-stu-id="b1c7e-111">For example, clients might return JSON as `text/javascript` instead of `application/json`.</span></span> <span data-ttu-id="b1c7e-112">Bu durumda, hizmet Geliştirici türeyen bir tür sağlamalısınız <xref:System.ServiceModel.Channels.WebContentTypeMapper> belirtilen içerik türü aşağıdaki örnek kodda gösterildiği gibi doğru şekilde işlemek için.</span><span class="sxs-lookup"><span data-stu-id="b1c7e-112">In this case, the service developer must provide a type that derives from <xref:System.ServiceModel.Channels.WebContentTypeMapper> to handle the given content type correctly, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="b1c7e-113">Türü geçersiz kılmanız gerekir <xref:System.ServiceModel.Channels.WebContentTypeMapper.GetMessageFormatForContentType%28System.String%29> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b1c7e-113">The type must override the <xref:System.ServiceModel.Channels.WebContentTypeMapper.GetMessageFormatForContentType%28System.String%29> method.</span></span> <span data-ttu-id="b1c7e-114">Yöntem değerlendirilmelidir `contentType` bağımsız değişkeni ve dönüş aşağıdaki değerlerden biri: <xref:System.ServiceModel.Channels.WebContentFormat.Json>, <xref:System.ServiceModel.Channels.WebContentFormat.Xml>, <xref:System.ServiceModel.Channels.WebContentFormat.Raw>, veya <xref:System.ServiceModel.Channels.WebContentFormat.Default>.</span><span class="sxs-lookup"><span data-stu-id="b1c7e-114">The method must evaluate the `contentType` argument and return one of the following values: <xref:System.ServiceModel.Channels.WebContentFormat.Json>, <xref:System.ServiceModel.Channels.WebContentFormat.Xml>, <xref:System.ServiceModel.Channels.WebContentFormat.Raw>, or <xref:System.ServiceModel.Channels.WebContentFormat.Default>.</span></span> <span data-ttu-id="b1c7e-115">Döndürme <xref:System.ServiceModel.Channels.WebContentFormat.Default> varsayılan Web ileti Kodlayıcı eşlemeleri erteler.</span><span class="sxs-lookup"><span data-stu-id="b1c7e-115">Returning <xref:System.ServiceModel.Channels.WebContentFormat.Default> defers to the default Web message encoder mappings.</span></span> <span data-ttu-id="b1c7e-116">Önceki örnek kodda `text/javascript` içerik türü için JSON eşlenen ve diğer tüm eşlemeleri değişmeden kalır.</span><span class="sxs-lookup"><span data-stu-id="b1c7e-116">In the previous sample code, the `text/javascript` content type is mapped to JSON, and all other mappings remain unchanged.</span></span>  
  
 <span data-ttu-id="b1c7e-117">Kullanılacak `JsonContentTypeMapper` sınıfı, Web.config dosyasında aşağıdakileri kullanın:</span><span class="sxs-lookup"><span data-stu-id="b1c7e-117">To use the `JsonContentTypeMapper` class, use the following in your Web.config:</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>  
    <webHttpEndpoint>  
      <standardEndpoint name="" contentTypeMapper="Microsoft.Samples.WebContentTypeMapper.JsonContentTypeMapper, JsonContentTypeMapper, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
    </webHttpEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="b1c7e-118">JsonContentTypeMapper kullanma gereksinimi doğrulamak için yukarıdaki yapılandırma dosyasından contentTypeMapper özniteliğini kaldırın.</span><span class="sxs-lookup"><span data-stu-id="b1c7e-118">To verify the requirement for using the JsonContentTypeMapper, remove the contentTypeMapper attribute from the above configuration file.</span></span> <span data-ttu-id="b1c7e-119">İstemci sayfası kullanmaya çalışırken yüklenemiyordur `text/javascript` JSON içerik göndermek için.</span><span class="sxs-lookup"><span data-stu-id="b1c7e-119">The client page fails to load when attempting to use `text/javascript` to send JSON content.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b1c7e-120">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="b1c7e-120">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="b1c7e-121">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b1c7e-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="b1c7e-122">Çözüm WebContentTypeMapperSample.sln açıklandığı gibi yapı [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b1c7e-122">Build the solution WebContentTypeMapperSample.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="b1c7e-123">İçin http://localhost/ServiceModelSamples/JCTMClientPage.htm gidin (JCTMClientPage.htm tarayıcıda proje dizininde açık değil).</span><span class="sxs-lookup"><span data-stu-id="b1c7e-123">Navigate to http://localhost/ServiceModelSamples/JCTMClientPage.htm (do not open JCTMClientPage.htm in the browser from within the project directory).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b1c7e-124">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="b1c7e-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b1c7e-125">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="b1c7e-125">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b1c7e-126">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="b1c7e-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b1c7e-127">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="b1c7e-127">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Ajax\WebContentTypeMapper`  
  
## <a name="see-also"></a><span data-ttu-id="b1c7e-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b1c7e-128">See Also</span></span>
