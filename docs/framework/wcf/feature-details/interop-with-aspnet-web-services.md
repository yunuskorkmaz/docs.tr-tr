---
title: "ASP.NET Web Hizmetleri ile Birlikte Çalışabilirlik"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 622422f8-6651-442f-b8be-e654a4aabcac
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ef174f457114003e5b2783b50040424d9a96945c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="interoperability-with-aspnet-web-services"></a><span data-ttu-id="e7f4d-102">ASP.NET Web Hizmetleri ile Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="e7f4d-102">Interoperability with ASP.NET Web Services</span></span>
<span data-ttu-id="e7f4d-103">Birlikte çalışabilirlik [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web Hizmetleri ve [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Web Hizmetleri elde edilebilir iki teknolojiyi kullanılarak uygulanan Hizmetleri WS uygun sağlayarak-ı temel Profil 1.1 belirtimini.</span><span class="sxs-lookup"><span data-stu-id="e7f4d-103">Interoperability between [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web services and [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Web services can be achieved by ensuring that services implemented using both technologies conform to the WS-I Basic Profile 1.1 specification.</span></span> [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]<span data-ttu-id="e7f4d-104">Web WS uygun Hizmetleri-ı temel Profil 1.1 birlikte çalışabilir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kullanarak istemcileri [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sistem tarafından sağlanan bir bağlamayı, <xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="e7f4d-104"> Web services that conform to WS-I Basic Profile 1.1 are interoperable with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clients by using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] system-provided binding, <xref:System.ServiceModel.BasicHttpBinding>.</span></span>  
  
 <span data-ttu-id="e7f4d-105">Kullanım [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] ekleme seçeneği <xref:System.Web.Services.WebService> ve <xref:System.Web.Services.WebMethodAttribute> öznitelikleri bir arabirime yerine bir sınıf ve aşağıdaki örnek kodda gösterildiği gibi arabirimini uygulayan bir sınıf yazma.</span><span class="sxs-lookup"><span data-stu-id="e7f4d-105">Use [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] option of adding the <xref:System.Web.Services.WebService> and <xref:System.Web.Services.WebMethodAttribute> attributes to an interface rather than to a class, and writing a class to implement the interface, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="e7f4d-106">Bu seçeneği kullanarak, tercih edilen, çünkü arabirimiyle <xref:System.Web.Services.WebService> özniteliği oluşturduğunu aynı sözleşme farklı şekillerde uygulayabilir çeşitli sınıflarıyla yeniden hizmeti tarafından gerçekleştirilen işlemler için bir sözleşmede.</span><span class="sxs-lookup"><span data-stu-id="e7f4d-106">Using this option is preferred, because the interface with the <xref:System.Web.Services.WebService> attribute constitutes a contract for the operations performed by the service that can be reused with various classes that might implement that same contract in different ways.</span></span>  
  
 <span data-ttu-id="e7f4d-107">Kullanmaktan kaçının <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> yöntemlere yönlendirilmiş iletiler için öznitelik tabanlı SOAP iletisi body öğesi tam olarak nitelenmiş adına yerine `SOAPAction` HTTP üstbilgisi.</span><span class="sxs-lookup"><span data-stu-id="e7f4d-107">Avoid using the <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> attribute to have messages routed to methods based on the fully-qualified name of the body element of the SOAP message rather than the `SOAPAction` HTTP header.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="e7f4d-108">kullanan `SOAPAction` iletileri yönlendirmek için HTTP üstbilgisi.</span><span class="sxs-lookup"><span data-stu-id="e7f4d-108"> uses the `SOAPAction` HTTP header for routing messages.</span></span>  
  
 <span data-ttu-id="e7f4d-109">Hangi içine XML <xref:System.Xml.Serialization.XmlSerializer> serileştiren bir türü varsayılan olarak anlam olarak hangi içine XML aynıdır <xref:System.Runtime.Serialization.DataContractSerializer> ad alanı XML açıkça tanımlanmış için sağlanan bir tür serileştirir.</span><span class="sxs-lookup"><span data-stu-id="e7f4d-109">The XML into which <xref:System.Xml.Serialization.XmlSerializer> serializes a type by default is semantically identical to the XML into which the <xref:System.Runtime.Serialization.DataContractSerializer> serializes a type, provided the namespace for the XML is explicitly defined.</span></span> <span data-ttu-id="e7f4d-110">İle kullanmak için bir veri türü tanımlarken [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]Web Hizmetleri benimsenmesi, kapatıldığını [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="e7f4d-110">When defining a data type for use with [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]Web services in anticipation of adopting [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], do the following:</span></span>  
  
-   <span data-ttu-id="e7f4d-111">XML şeması yerine .NET Framework sınıfları kullanarak türünü tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="e7f4d-111">Define the type using .NET Framework classes rather than XML Schema.</span></span>  
  
-   <span data-ttu-id="e7f4d-112">Yalnızca ekleme <xref:System.SerializableAttribute> ve <xref:System.Xml.Serialization.XmlRootAttribute> sınıfına türünün ad alanını açıkça tanımlamak için ikinci kullanarak.</span><span class="sxs-lookup"><span data-stu-id="e7f4d-112">Add only the <xref:System.SerializableAttribute> and the <xref:System.Xml.Serialization.XmlRootAttribute> to the class, using the latter to explicitly define the namespace for the type.</span></span> <span data-ttu-id="e7f4d-113">Ek özniteliklerden eklemeyin <xref:System.Xml.Serialization> .NET Framework sınıf nasıl XML çevrilmesi denetlemek için ad alanı.</span><span class="sxs-lookup"><span data-stu-id="e7f4d-113">Do not add additional attributes from the <xref:System.Xml.Serialization> namespace to control how the .NET Framework class is to be translated into XML.</span></span>  
  
-   <span data-ttu-id="e7f4d-114">Bu yaklaşım kabul ederek, daha sonra .NET eklenmesi veri Sözleşmelerle içine sınıflarının gerekir <xref:System.Runtime.Serialization.DataContractAttribute> ve <xref:System.Runtime.Serialization.DataMemberAttribute> içine sınıfları aktarım için serileştirilir XML önemli ölçüde değiştirmeden.</span><span class="sxs-lookup"><span data-stu-id="e7f4d-114">By adopting this approach, you should be able to later make the .NET classes into data contracts with the addition of the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> without significantly altering the XML into which the classes are serialized for transmission.</span></span> <span data-ttu-id="e7f4d-115">İleti tarafından kullanılan türleri [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web Hizmetleri, veri sözleşmeleri tarafından olarak işlenebilir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] , başka avantajları arasında oluşturan uygulamalar, daha iyi performans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulamalar.</span><span class="sxs-lookup"><span data-stu-id="e7f4d-115">The types used in messages by [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web services can be processed as data contracts by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications, yielding, among other benefits, better performance in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications.</span></span>  
  
 <span data-ttu-id="e7f4d-116">Internet Information Services (IIS) tarafından sağlanan kimlik doğrulama seçenekleri kullanmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="e7f4d-116">Avoid using the authentication options provided by Internet Information Services (IIS).</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="e7f4d-117">istemcileri onları desteklemez.</span><span class="sxs-lookup"><span data-stu-id="e7f4d-117"> clients do not support them.</span></span> <span data-ttu-id="e7f4d-118">Bir hizmeti güvenli hale getirilmelidir, tarafından sağlanan seçenekleri kullanın. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], çünkü bu seçenekler sağlam ve standart protokollerine dayalıdır.</span><span class="sxs-lookup"><span data-stu-id="e7f4d-118">If a service must be secured, use the options provided by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], because these options are robust and are based on standard protocols.</span></span>  
  
## <a name="performance-impact-caused-by-loading-the-servicemodel-httpmodule"></a><span data-ttu-id="e7f4d-119">ServiceModel HTTP yükleyerek neden performans etkisi</span><span class="sxs-lookup"><span data-stu-id="e7f4d-119">Performance impact caused by loading the ServiceModel HttpModule</span></span>  
 <span data-ttu-id="e7f4d-120">.NET Framework 3.0, WCF `HttpModule` kök Web.config dosyasında her ASP.NET uygulama etkin bir WCF olduğu şekilde yüklendi.</span><span class="sxs-lookup"><span data-stu-id="e7f4d-120">In the .NET Framework 3.0, the WCF `HttpModule` was installed in the root Web.config file such that every ASP.NET application was WCF enabled.</span></span> <span data-ttu-id="e7f4d-121">Kaldırabilmeniz için bu performansını etkileyebilir `ServiceModel` aşağıdaki örnekte gösterildiği gibi Web.config dosyası için.</span><span class="sxs-lookup"><span data-stu-id="e7f4d-121">This might affect performance, so you can remove `ServiceModel` for the Web.config file as shown in the following example.</span></span>  
  
```xml  
<httpModules>  
    <remove name="ServiceModel" />  
<httpModules/>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e7f4d-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e7f4d-122">See Also</span></span>  
 [<span data-ttu-id="e7f4d-123">Nasıl yapılır: WCF Hizmetini ASP.NET Web Hizmeti İstemcileriyle Birlikte Çalışmak için Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e7f4d-123">How to: Configure WCF Service to Interoperate with ASP.NET Web Service Clients</span></span>](../../../../docs/framework/wcf/feature-details/config-wcf-service-with-aspnet-web-service.md)
