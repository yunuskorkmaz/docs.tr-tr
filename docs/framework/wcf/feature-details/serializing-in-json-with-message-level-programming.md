---
description: "Hakkında daha fazla bilgi edinin: Ileti düzeyinde programlama ile JSON 'da serileştirme"
title: İleti Düzeyi Programlama ile JSON Seri Hale Getirme
ms.date: 03/30/2017
ms.assetid: 5f940ba2-57ee-4c49-a779-957c5e7e71fa
ms.openlocfilehash: 715e44b0e2137197f5883e2327288555513f29cd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793551"
---
# <a name="serializing-in-json-with-message-level-programming"></a><span data-ttu-id="211fd-103">İleti Düzeyi Programlama ile JSON Seri Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="211fd-103">Serializing in Json with Message Level Programming</span></span>

<span data-ttu-id="211fd-104">WCF, JSON biçimindeki verilerin serileştirilmesinin kullanılmasını destekler.</span><span class="sxs-lookup"><span data-stu-id="211fd-104">WCF supports serializing data in JSON format.</span></span> <span data-ttu-id="211fd-105">Bu konuda, WCF 'yi kullanarak türlerinizi serileştirmek için nasıl söyleyeceğinizi açıklanmaktadır <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> .</span><span class="sxs-lookup"><span data-stu-id="211fd-105">This topic describes how to tell WCF to serialize your types using the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>  
  
## <a name="typed-message-programming"></a><span data-ttu-id="211fd-106">Yazılan Ileti programlama</span><span class="sxs-lookup"><span data-stu-id="211fd-106">Typed Message Programming</span></span>  

 <span data-ttu-id="211fd-107">, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> <xref:System.ServiceModel.Web.WebGetAttribute> Veya <xref:System.ServiceModel.Web.WebInvokeAttribute> bir hizmet işlemine uygulandığında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="211fd-107">The <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> is used when the <xref:System.ServiceModel.Web.WebGetAttribute> or the <xref:System.ServiceModel.Web.WebInvokeAttribute> is applied to a service operation.</span></span> <span data-ttu-id="211fd-108">Bu özniteliklerin her ikisi de belirtmenizi sağlar `RequestFormat` `ResponseFormat` .</span><span class="sxs-lookup"><span data-stu-id="211fd-108">Both of these attributes allow you to specify the `RequestFormat` and `ResponseFormat`.</span></span> <span data-ttu-id="211fd-109">İstekleri ve yanıtları için JSON kullanmak.</span><span class="sxs-lookup"><span data-stu-id="211fd-109">To use JSON for requests and responses.</span></span> <span data-ttu-id="211fd-110">her ikisini de olarak ayarlayın `WebMessageFormat.Json` .</span><span class="sxs-lookup"><span data-stu-id="211fd-110">set both of these to `WebMessageFormat.Json`.</span></span>  <span data-ttu-id="211fd-111">JSON kullanmak için, <xref:System.ServiceModel.WebHttpBinding> ' yi otomatik olarak yapılandıran öğesini kullanmanız gerekir <xref:System.ServiceModel.Description.WebHttpBehavior> .</span><span class="sxs-lookup"><span data-stu-id="211fd-111">In order to use JSON, you must use the <xref:System.ServiceModel.WebHttpBinding>, which automatically configures the <xref:System.ServiceModel.Description.WebHttpBehavior>.</span></span> <span data-ttu-id="211fd-112">WCF serileştirme hakkında daha fazla bilgi için bkz. [serileştirme ve seri durumundan çıkarma](serialization-and-deserialization.md).</span><span class="sxs-lookup"><span data-stu-id="211fd-112">For more information about WCF serialization, see [Serialization and Deserialization](serialization-and-deserialization.md).</span></span> <span data-ttu-id="211fd-113">JSON ve WCF hakkında daha fazla bilgi için bkz. [hizmet istasyonu-WCF Ile yeniden hizmet vermek Için bir giriş](/archive/msdn-magazine/2009/january/service-station-an-introduction-to-restful-services-with-wcf).</span><span class="sxs-lookup"><span data-stu-id="211fd-113">For more information about JSON and WCF, see [Service Station - An Introduction To RESTful Services With WCF](/archive/msdn-magazine/2009/january/service-station-an-introduction-to-restful-services-with-wcf).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="211fd-114">JSON kullanımı, <xref:System.ServiceModel.WebHttpBinding> <xref:System.ServiceModel.Description.WebHttpBehavior> SOAP iletişimini desteklemeyen ve kullanımını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="211fd-114">Using JSON requires use of <xref:System.ServiceModel.WebHttpBinding> and <xref:System.ServiceModel.Description.WebHttpBehavior> which do not support SOAP communication.</span></span> <span data-ttu-id="211fd-115">İle iletişim kuran hizmetler, <xref:System.ServiceModel.WebHttpBinding> hizmet meta verilerinin sunulmasını desteklemez; böylece, istemci tarafı proxy oluşturmak Için Visual Studio 'nun hizmet başvurusu Ekle işlevselliğini veya Svcutil komut satırı aracını kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="211fd-115">Services that communicate with the <xref:System.ServiceModel.WebHttpBinding> do not support exposing service metadata so you will not be able to use Visual Studio’s Add Service Reference functionality or the svcutil command-line tool to generate a client-side proxy.</span></span> <span data-ttu-id="211fd-116">Tarafından kullanılan Hizmetleri programlı olarak nasıl çağırabilmeniz hakkında daha fazla bilgi için <xref:System.ServiceModel.WebHttpBinding> bkz. [WCF Ile Rest hizmetlerini kullanma](/archive/blogs/pedram/how-to-consume-rest-services-with-wcf).</span><span class="sxs-lookup"><span data-stu-id="211fd-116">For more information how you can programmatically call services that use <xref:System.ServiceModel.WebHttpBinding>, see [How to Consume REST Services with WCF](/archive/blogs/pedram/how-to-consume-rest-services-with-wcf).</span></span>  
  
## <a name="untyped-message-programming"></a><span data-ttu-id="211fd-117">Türsüz Ileti programlama</span><span class="sxs-lookup"><span data-stu-id="211fd-117">Untyped Message Programming</span></span>  

 <span data-ttu-id="211fd-118">Türsüz Ileti nesneleriyle doğrudan çalışırken, türsüz iletideki özellikleri JSON olarak seri hale getirmek için açıkça ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="211fd-118">When working directly with untyped Message objects, you must explicitly set the properties on the untyped message to serialize it as JSON.</span></span> <span data-ttu-id="211fd-119">Aşağıdaki kod parçacığında bunun nasıl yapılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="211fd-119">The following code snippet shows how to do this.</span></span>  
  
```csharp
 Message response = Message.CreateMessage(  
                  MessageVersion.None,    // No SOAP message version  
                             "*",                     // SOAP action, ignored since this is JSON  
                             "Response string: JSON format specified", // Message body  
                             new DataContractJsonSerializer(typeof(string))); // Specify DataContractJsonSerializer  
      response.Properties.Add( WebBodyFormatMessageProperty.Name,
                    new WebBodyFormatMessageProperty(WebContentFormat.Json)); // Use JSON format  
```  
  
## <a name="see-also"></a><span data-ttu-id="211fd-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="211fd-120">See also</span></span>

- [<span data-ttu-id="211fd-121">AJAX Tümleştirme ve JSON Desteği</span><span class="sxs-lookup"><span data-stu-id="211fd-121">AJAX Integration and JSON Support</span></span>](ajax-integration-and-json-support.md)
- [<span data-ttu-id="211fd-122">Bağımsız JSON Seri Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="211fd-122">Stand-Alone JSON Serialization</span></span>](stand-alone-json-serialization.md)
- [<span data-ttu-id="211fd-123">JSON serileştirme</span><span class="sxs-lookup"><span data-stu-id="211fd-123">JSON Serialization</span></span>](../samples/json-serialization.md)
