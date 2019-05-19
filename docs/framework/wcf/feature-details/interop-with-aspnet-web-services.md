---
title: ASP.NET Web Hizmetleri ile Birlikte Çalışabilirlik
ms.date: 03/30/2017
ms.assetid: 622422f8-6651-442f-b8be-e654a4aabcac
ms.openlocfilehash: c1b027eda315a76778e772235dc5f66e03c9d83e
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65875540"
---
# <a name="interoperability-with-aspnet-web-services"></a><span data-ttu-id="d9b3a-102">ASP.NET Web Hizmetleri ile Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="d9b3a-102">Interoperability with ASP.NET Web Services</span></span>
<span data-ttu-id="d9b3a-103">ASP.NET Web Hizmetleri ve Windows Communication Foundation (WCF) Web hizmetleri arasında birlikte çalışabilirlik sağlayarak hem teknolojiler kullanılarak uygulanan Hizmetleri WS uygun gerçekleştirilebilir-ı Basic Profile 1.1 belirtimi.</span><span class="sxs-lookup"><span data-stu-id="d9b3a-103">Interoperability between ASP.NET Web services and Windows Communication Foundation (WCF) Web services can be achieved by ensuring that services implemented using both technologies conform to the WS-I Basic Profile 1.1 specification.</span></span> <span data-ttu-id="d9b3a-104">ASP.NET Web Hizmetleri, uygun WS-ı Basic Profile 1.1 ile WCF istemcileri birlikte çalışabilen WCF sistem tarafından sağlanan bağlama kullanarak <xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="d9b3a-104">ASP.NET Web services that conform to WS-I Basic Profile 1.1 are interoperable with WCF clients by using WCF system-provided binding, <xref:System.ServiceModel.BasicHttpBinding>.</span></span>  
  
 <span data-ttu-id="d9b3a-105">Kullanım [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] ekleme seçeneği <xref:System.Web.Services.WebService> ve <xref:System.Web.Services.WebMethodAttribute> bir arabirim yerine bir sınıf ve arabirim uygulamak için bir sınıf aşağıdaki örnek kodda gösterildiği gibi yazmak için öznitelikler.</span><span class="sxs-lookup"><span data-stu-id="d9b3a-105">Use [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] option of adding the <xref:System.Web.Services.WebService> and <xref:System.Web.Services.WebMethodAttribute> attributes to an interface rather than to a class, and writing a class to implement the interface, as shown in the following sample code.</span></span>  
  
```  
[WebService]  
public interface IEcho  
{  
    [WebMethod]  
    string Echo(string input);  
}  
  
public class Service : IEcho  
{  
  
   public string Echo(string input)  
   {  
        return input;  
    }  
}  
```  
  
 <span data-ttu-id="d9b3a-106">Bu seçenek kullanılarak tercih edilir, çünkü arabirimiyle <xref:System.Web.Services.WebService> özniteliği aynı sözleşme farklı şekillerde uygulayabilir, çeşitli sınıflarla yeniden kullanılabilir bir hizmet tarafından gerçekleştirilen işlemleri için bir sözleşmeyi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d9b3a-106">Using this option is preferred, because the interface with the <xref:System.Web.Services.WebService> attribute constitutes a contract for the operations performed by the service that can be reused with various classes that might implement that same contract in different ways.</span></span>  
  
 <span data-ttu-id="d9b3a-107">Kullanmaktan kaçının <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> yöntemlere yönlendirilmiş iletiler için öznitelik SOAP iletisinin gövde öğesi tam olarak nitelenmiş adını temel alarak yerine `SOAPAction` HTTP üstbilgisi.</span><span class="sxs-lookup"><span data-stu-id="d9b3a-107">Avoid using the <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> attribute to have messages routed to methods based on the fully-qualified name of the body element of the SOAP message rather than the `SOAPAction` HTTP header.</span></span> <span data-ttu-id="d9b3a-108">WCF kullanan `SOAPAction` iletileri yönlendirmek için HTTP üstbilgisi.</span><span class="sxs-lookup"><span data-stu-id="d9b3a-108">WCF uses the `SOAPAction` HTTP header for routing messages.</span></span>  
  
 <span data-ttu-id="d9b3a-109">XML'e <xref:System.Xml.Serialization.XmlSerializer> serileştiren bir türü varsayılan olarak anlamı da XML'e aynıdır <xref:System.Runtime.Serialization.DataContractSerializer> ad alanı XML açıkça tanımlanmış için sağlanan bir türü seri hale getirir.</span><span class="sxs-lookup"><span data-stu-id="d9b3a-109">The XML into which <xref:System.Xml.Serialization.XmlSerializer> serializes a type by default is semantically identical to the XML into which the <xref:System.Runtime.Serialization.DataContractSerializer> serializes a type, provided the namespace for the XML is explicitly defined.</span></span> <span data-ttu-id="d9b3a-110">ASP.NETWeb Hizmetleri ile kullanmak için bir veri türü benimsemenin WCF kapatıldığını tanımlarken aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="d9b3a-110">When defining a data type for use with ASP.NETWeb services in anticipation of adopting WCF, do the following:</span></span>  
  
- <span data-ttu-id="d9b3a-111">XML şeması yerine .NET Framework sınıfları kullanarak türünü tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="d9b3a-111">Define the type using .NET Framework classes rather than XML Schema.</span></span>  
  
- <span data-ttu-id="d9b3a-112">Yalnızca ekleme <xref:System.SerializableAttribute> ve <xref:System.Xml.Serialization.XmlRootAttribute> sınıf türünün ad alanını açıkça tanımlamak için ikinci kullanarak.</span><span class="sxs-lookup"><span data-stu-id="d9b3a-112">Add only the <xref:System.SerializableAttribute> and the <xref:System.Xml.Serialization.XmlRootAttribute> to the class, using the latter to explicitly define the namespace for the type.</span></span> <span data-ttu-id="d9b3a-113">Ek öznitelikleri eklemeyin <xref:System.Xml.Serialization> nasıl XML'e çevrilmesi için .NET Framework sınıf olduğunu denetlemek için ad alanı.</span><span class="sxs-lookup"><span data-stu-id="d9b3a-113">Do not add additional attributes from the <xref:System.Xml.Serialization> namespace to control how the .NET Framework class is to be translated into XML.</span></span>  
  
- <span data-ttu-id="d9b3a-114">Bu yaklaşım benimseyerek, daha sonra ek olarak veri sözleşmeleri içine .NET sınıfları oluşturmak erişebileceğinizi <xref:System.Runtime.Serialization.DataContractAttribute> ve <xref:System.Runtime.Serialization.DataMemberAttribute> içine sınıfları aktarım için serileştirilir XML önemli ölçüde boyutlandırabiliriz.</span><span class="sxs-lookup"><span data-stu-id="d9b3a-114">By adopting this approach, you should be able to later make the .NET classes into data contracts with the addition of the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> without significantly altering the XML into which the classes are serialized for transmission.</span></span> <span data-ttu-id="d9b3a-115">İletileri ASP.NET Web Hizmetleri tarafından kullanılan türleri veri sözleşmeleri sonuçlanmıyor WCF uygulamalarında daha iyi performans diğer avantajlarının yanı sıra WCF uygulamaları tarafından işlenebilir.</span><span class="sxs-lookup"><span data-stu-id="d9b3a-115">The types used in messages by ASP.NET Web services can be processed as data contracts by WCF applications, yielding, among other benefits, better performance in WCF applications.</span></span>  
  
 <span data-ttu-id="d9b3a-116">Internet Information Services (IIS) tarafından sağlanan kimlik doğrulama seçenekleri kullanmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="d9b3a-116">Avoid using the authentication options provided by Internet Information Services (IIS).</span></span> <span data-ttu-id="d9b3a-117">WCF istemcileri onları desteklemez.</span><span class="sxs-lookup"><span data-stu-id="d9b3a-117">WCF clients do not support them.</span></span> <span data-ttu-id="d9b3a-118">Bir hizmeti güvenli hale getirilmelidir, çünkü bu seçenekler, sağlam ve standardı protokollerine dayalıdır WCF tarafından sağlanan seçenekleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="d9b3a-118">If a service must be secured, use the options provided by WCF, because these options are robust and are based on standard protocols.</span></span>  
  
## <a name="performance-impact-caused-by-loading-the-servicemodel-httpmodule"></a><span data-ttu-id="d9b3a-119">ServiceModel HttpModule yükleyerek nedeniyle performans etkisi</span><span class="sxs-lookup"><span data-stu-id="d9b3a-119">Performance impact caused by loading the ServiceModel HttpModule</span></span>  
 <span data-ttu-id="d9b3a-120">.NET Framework 3.0, WCF `HttpModule` kök Web.config dosyasında her bir ASP.NET uygulaması etkinleştirilmiş WCF olduğu şekilde yüklendi.</span><span class="sxs-lookup"><span data-stu-id="d9b3a-120">In the .NET Framework 3.0, the WCF `HttpModule` was installed in the root Web.config file such that every ASP.NET application was WCF enabled.</span></span> <span data-ttu-id="d9b3a-121">Bu nedenle bu performansını etkileyebilir `ServiceModel` aşağıdaki örnekte gösterildiği gibi Web.config dosyası için.</span><span class="sxs-lookup"><span data-stu-id="d9b3a-121">This might affect performance, so you can remove `ServiceModel` for the Web.config file as shown in the following example.</span></span>  
  
```xml  
<httpModules>  
    <remove name="ServiceModel" />  
<httpModules/>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d9b3a-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d9b3a-122">See also</span></span>

- [<span data-ttu-id="d9b3a-123">Nasıl yapılır: WCF hizmetini ASP.NET Web hizmeti istemcileriyle birlikte çalışmak için yapılandırma</span><span class="sxs-lookup"><span data-stu-id="d9b3a-123">How to: Configure WCF Service to Interoperate with ASP.NET Web Service Clients</span></span>](../../../../docs/framework/wcf/feature-details/config-wcf-service-with-aspnet-web-service.md)
