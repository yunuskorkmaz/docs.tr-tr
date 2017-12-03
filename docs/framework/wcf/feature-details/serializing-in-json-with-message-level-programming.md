---
title: "İleti Düzeyi Programlama ile JSON Seri Hale Getirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5f940ba2-57ee-4c49-a779-957c5e7e71fa
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3967cd7002af8ff9aee4c4f25bd2422d2d0ea1ed
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="serializing-in-json-with-message-level-programming"></a><span data-ttu-id="816ea-102">İleti Düzeyi Programlama ile JSON Seri Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="816ea-102">Serializing in Json with Message Level Programming</span></span>
<span data-ttu-id="816ea-103">WCF JSON biçiminde verilerin serileştirilmesi destekler.</span><span class="sxs-lookup"><span data-stu-id="816ea-103">WCF supports serializing data in JSON format.</span></span> <span data-ttu-id="816ea-104">Bu konu, kullanarak türlerinizi serileştirmek için WCF bildirmek açıklar <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span><span class="sxs-lookup"><span data-stu-id="816ea-104">This topic describes how to tell WCF to serialize your types using the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>  
  
## <a name="typed-message-programming"></a><span data-ttu-id="816ea-105">Yazılı ileti programlama</span><span class="sxs-lookup"><span data-stu-id="816ea-105">Typed Message Programming</span></span>  
 <span data-ttu-id="816ea-106"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> Kullanıldığında <xref:System.ServiceModel.Web.WebGetAttribute> veya <xref:System.ServiceModel.Web.WebInvokeAttribute> bir hizmet işlemi uygulanır.</span><span class="sxs-lookup"><span data-stu-id="816ea-106">The <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> is used when the <xref:System.ServiceModel.Web.WebGetAttribute> or the <xref:System.ServiceModel.Web.WebInvokeAttribute> is applied to a service operation.</span></span> <span data-ttu-id="816ea-107">Bu özniteliklerin her ikisini de belirlemenizi sağlayan `RequestFormat` ve `ResponseFormat`.</span><span class="sxs-lookup"><span data-stu-id="816ea-107">Both of these attributes allow you to specify the `RequestFormat` and `ResponseFormat`.</span></span> <span data-ttu-id="816ea-108">JSON istekleri ve yanıtları için kullanmak üzere bu ikisinin ayarlanmış `WebMessageFormat.Json`.</span><span class="sxs-lookup"><span data-stu-id="816ea-108">To use JSON for requests and responses set both of these to `WebMessageFormat.Json`.</span></span>  <span data-ttu-id="816ea-109">JSON kullanmalısınız kullanmak için <xref:System.ServiceModel.WebHttpBinding> otomatik olarak yapılandıran <xref:System.ServiceModel.Description.WebHttpBehavior>.</span><span class="sxs-lookup"><span data-stu-id="816ea-109">In order to use JSON you must use the <xref:System.ServiceModel.WebHttpBinding> which automatically configures the <xref:System.ServiceModel.Description.WebHttpBehavior>.</span></span> <span data-ttu-id="816ea-110">WCF seri hale getirme hakkında daha fazla bilgi için bkz: [seri hale getirme ve seri durumdan çıkarma](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md), [Windows Communication Foundation'da serileştirme](http://msdn.microsoft.com/magazine/cc163569.aspx).</span><span class="sxs-lookup"><span data-stu-id="816ea-110">For more information about WCF serialization, see: [Serialization and Deserialization](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md), [Serialization in Windows Communication Foundation](http://msdn.microsoft.com/magazine/cc163569.aspx).</span></span> <span data-ttu-id="816ea-111">JSON ve WCF hakkında daha fazla bilgi için bkz: [RESTfull Hizmetleri WCF ile giriş](http://msdn.microsoft.com/magazine/dd315413.aspx), [.NET 3.5 WCF hizmetleri oluşturma JSON etkinleştirilmiş](http://www.pluralsight-training.net/community/blogs/fritz/archive/2008/01/31/50121.aspx), ve [WCF,KALANgenelbakış](http://msdn.microsoft.com/netframework/dd547388).</span><span class="sxs-lookup"><span data-stu-id="816ea-111">For more information about JSON and WCF see [An Introduction to RESTfull Services with WCF](http://msdn.microsoft.com/magazine/dd315413.aspx), [Creating JSON-enabled WCF Services in .NET 3.5](http://www.pluralsight-training.net/community/blogs/fritz/archive/2008/01/31/50121.aspx), and [Overview of REST in WCF](http://msdn.microsoft.com/netframework/dd547388).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="816ea-112">JSON kullanarak kullanılmasını gerektiren <xref:System.ServiceModel.WebHttpBinding> ve <xref:System.ServiceModel.Description.WebHttpBehavior> SOAP iletişimi desteklemez.</span><span class="sxs-lookup"><span data-stu-id="816ea-112">Using JSON requires use of <xref:System.ServiceModel.WebHttpBinding> and <xref:System.ServiceModel.Description.WebHttpBehavior> which do not support SOAP communication.</span></span> <span data-ttu-id="816ea-113">İletişim hizmetlerini <xref:System.ServiceModel.WebHttpBinding> istemci-tarafı proxy oluşturmak için Visual Studio'nun hizmet Başvurusu Ekle işlevselliği veya svcutil komut satırı aracını kullanmanız mümkün olmayacak şekilde sunan hizmet meta verilerini desteklemez.</span><span class="sxs-lookup"><span data-stu-id="816ea-113">Services that communicate with the <xref:System.ServiceModel.WebHttpBinding> do not support exposing service metadata so you will not be able to use Visual Studio’s Add Service Reference functionality or the svcutil command-line tool to generate a client-side proxy.</span></span> <span data-ttu-id="816ea-114">Hizmetleri kullanan nasıl programlı olarak çağırabilirsiniz daha fazla bilgi için <xref:System.ServiceModel.WebHttpBinding>, bkz: [REST Hizmetleri WCF ile kullanmak için nasıl](http://blogs.msdn.com/b/pedram/archive/2008/04/21/how-to-consume-rest-services-with-wcf.aspx).</span><span class="sxs-lookup"><span data-stu-id="816ea-114">For more information how you can programmatically call services that use <xref:System.ServiceModel.WebHttpBinding>, see [How to Consume REST Services with WCF](http://blogs.msdn.com/b/pedram/archive/2008/04/21/how-to-consume-rest-services-with-wcf.aspx).</span></span>  
  
## <a name="untyped-message-programming"></a><span data-ttu-id="816ea-115">Türsüz ileti programlama</span><span class="sxs-lookup"><span data-stu-id="816ea-115">Untyped Message Programming</span></span>  
 <span data-ttu-id="816ea-116">Doğrudan türsüz Message nesneleri ile çalışırken, JSON olarak seri hale getirmek için türsüz iletideki açıkça özelliklerini ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="816ea-116">When working directly with untyped Message objects, you must explicitly set the properties on the untyped message to serialize it as JSON.</span></span> <span data-ttu-id="816ea-117">Aşağıdaki kod parçacığını bunun nasıl yapılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="816ea-117">The following code snippet shows how to do this.</span></span>  
  
```  
 Message response = Message.CreateMessage(  
                  MessageVersion.None,    // No SOAP message version  
                             "*",                     // SOAP action, ignored since this is JSON  
                             "Response string: JSON format specified", // Message body  
                             new DataContractJsonSerializer(typeof(string))); // Specify DataContractJsonSerializer  
      response.Properties.Add( WebBodyFormatMessageProperty.Name,   
                    new WebBodyFormatMessageProperty(WebContentFormat.Json)); // Use JSON format  
```  
  
## <a name="see-also"></a><span data-ttu-id="816ea-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="816ea-118">See Also</span></span>  
 [<span data-ttu-id="816ea-119">AJAX tümleştirme ve JSON desteği</span><span class="sxs-lookup"><span data-stu-id="816ea-119">AJAX Integration and JSON Support</span></span>](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)  
 [<span data-ttu-id="816ea-120">Bağımsız JSON seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="816ea-120">Stand-Alone JSON Serialization</span></span>](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md)  
 [<span data-ttu-id="816ea-121">JSON seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="816ea-121">JSON Serialization</span></span>](../../../../docs/framework/wcf/samples/json-serialization.md)
