---
title: "Windows Communication Foundation'ı Benimsemeyi Bekleme: Gelecekteki Tümleştirmeyi Kolaylaştırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3028bba8-6355-4ee0-9ecd-c56e614cb474
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ccf6e5363da872d3902c12713bd19f5820370428
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-integration"></a><span data-ttu-id="f23d0-102">Windows Communication Foundation'ı Benimsemeyi Bekleme: Gelecekteki Tümleştirmeyi Kolaylaştırma</span><span class="sxs-lookup"><span data-stu-id="f23d0-102">Anticipating Adopting the Windows Communication Foundation: Easing Future Integration</span></span>
<span data-ttu-id="f23d0-103">ASP.NET bugün kullanıyorsanız ve kullanarak düşündüğünüz [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] gelecekte bu konuda yeni ASP.NET Web hizmetleri de ile birlikte çalışacağından emin olmak için yönergeler sağlanmaktadır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulamalar.</span><span class="sxs-lookup"><span data-stu-id="f23d0-103">If you use ASP.NET today, and anticipate using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] in the future, this topic provides guidance to ensure that new ASP.NET Web services will work well together with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications.</span></span>  
  
## <a name="general-recommendations"></a><span data-ttu-id="f23d0-104">Genel öneriler</span><span class="sxs-lookup"><span data-stu-id="f23d0-104">General Recommendations</span></span>  
 <span data-ttu-id="f23d0-105">ASP.NET 2.0 için yeni hizmetlerin benimser.</span><span class="sxs-lookup"><span data-stu-id="f23d0-105">Adopt ASP.NET 2.0 for any new services.</span></span> <span data-ttu-id="f23d0-106">Bunun yapılması geliştirmeleri ve yeni sürümün geliştirmeleri erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="f23d0-106">Doing so will provide access to the improvements and enhancements of the new version.</span></span> <span data-ttu-id="f23d0-107">Ancak, bu da ASP.NET 2.0 bileşenleri ile birlikte kullanma olasılığını için sağlayacak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aynı uygulama bileşenleri.</span><span class="sxs-lookup"><span data-stu-id="f23d0-107">However, it will also allow for the possibility of using ASP.NET 2.0 components together with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] components in the same application.</span></span>  
  
## <a name="protocols"></a><span data-ttu-id="f23d0-108">protokolleri</span><span class="sxs-lookup"><span data-stu-id="f23d0-108">Protocols</span></span>  
 <span data-ttu-id="f23d0-109">ASP.NET 2. 0'ın yeni tesis ws uygunluk doğrulamak için kullanın-ı temel Profil 1.1:</span><span class="sxs-lookup"><span data-stu-id="f23d0-109">Use ASP.NET 2.0’s new facility for validating conformity to the WS-I Basic Profile 1.1:</span></span>  
  
```  
[WebService(Namespace = "http://tempuri.org/")]  
[WebServiceBinding(  
     ConformsTo = WsiProfiles.BasicProfile1_1,  
     EmitConformanceClaims=true)]  
public interface IEcho  
```  
  
 <span data-ttu-id="f23d0-110">WS uygun ASP.NET Web Hizmetleri-ı temel Profil 1.1 birlikte çalışabilir olacaktır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kullanarak istemcileri [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bağlama, önceden tanımlanmış <xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="f23d0-110">ASP.NET Web services that conform to WS-I Basic Profile 1.1 will be interoperable with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clients by using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] predefined binding, <xref:System.ServiceModel.BasicHttpBinding>.</span></span>  
  
## <a name="service-development"></a><span data-ttu-id="f23d0-111">Hizmet geliştirme</span><span class="sxs-lookup"><span data-stu-id="f23d0-111">Service Development</span></span>  
 <span data-ttu-id="f23d0-112">Kullanmaktan kaçının <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> yöntemlere yönlendirilmiş iletiler için öznitelik SOAPAction HTTP üstbilgisi yerine SOAP iletisi body öğesi tam olarak nitelenmiş adını temel alarak.</span><span class="sxs-lookup"><span data-stu-id="f23d0-112">Avoid using the <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> attribute to have messages routed to methods based on the fully-qualified name of the body element of the SOAP message rather than the SOAPAction HTTP header.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="f23d0-113">SOAPAction HTTP üstbilgisi iletileri yönlendirmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="f23d0-113"> uses the SOAPAction HTTP header for routing messages.</span></span>  
  
## <a name="data-representation"></a><span data-ttu-id="f23d0-114">Veri temsili</span><span class="sxs-lookup"><span data-stu-id="f23d0-114">Data Representation</span></span>  
 <span data-ttu-id="f23d0-115">Hangi içine XML <xref:System.Xml.Serialization.XmlSerializer> serileştiren bir türü varsayılan olarak anlam olarak hangi içine XML aynıdır <xref:System.Runtime.Serialization.DataContractSerializer> ad alanı XML açıkça tanımlanmış için sağlanan bir tür serileştirir.</span><span class="sxs-lookup"><span data-stu-id="f23d0-115">The XML into which <xref:System.Xml.Serialization.XmlSerializer> serializes a type by default is semantically identical to the XML into which the <xref:System.Runtime.Serialization.DataContractSerializer> serializes a type, provided the namespace for the XML is explicitly defined.</span></span> <span data-ttu-id="f23d0-116">Ne zaman kullanmak için bir veri türü ile ASP.NET Web tanımlama izin ver Hizmetleri benimsenmesi bir kapatıldığını içinde [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] gelecekte, aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="f23d0-116">When defining a data type for use with ASP.NET Web services in anticipation of adopting [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] in the future, do the following:</span></span>  
  
1.  <span data-ttu-id="f23d0-117">XML şeması yerine .NET Framework sınıfları kullanarak türünü tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="f23d0-117">Define the type using .NET Framework classes rather than XML Schema.</span></span>  
  
2.  <span data-ttu-id="f23d0-118">Yalnızca ekleme <xref:System.SerializableAttribute> ve <xref:System.Xml.Serialization.XmlRootAttribute> sınıfına türünün ad alanını açıkça tanımlamak için ikinci kullanarak.</span><span class="sxs-lookup"><span data-stu-id="f23d0-118">Add only the <xref:System.SerializableAttribute> and the <xref:System.Xml.Serialization.XmlRootAttribute> to the class, using the latter to explicitly define the namespace for the type.</span></span> <span data-ttu-id="f23d0-119">Yapmak hiçbir ek özniteliklerinden Ekle <xref:System.Xml.Serialization> .NET Framework sınıf nasıl XML çevrilmesi denetlemek için ad alanı.</span><span class="sxs-lookup"><span data-stu-id="f23d0-119">Do no add additional attributes from the <xref:System.Xml.Serialization> namespace to control how the .NET Framework class is to be translated into XML.</span></span>  
  
 <span data-ttu-id="f23d0-120">Bu yaklaşım kabul ederek, daha sonra .NET eklenmesi veri Sözleşmelerle içine sınıflarının gerekir <xref:System.Runtime.Serialization.DataContractAttribute> ve <xref:System.Runtime.Serialization.DataMemberAttribute> içine sınıfları aktarım için serileştirilir XML önemli ölçüde değiştirmeden.</span><span class="sxs-lookup"><span data-stu-id="f23d0-120">By adopting this approach, you should be able to later make the .NET classes into data contracts with the addition of the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> without significantly altering the XML into which the classes are serialized for transmission.</span></span> <span data-ttu-id="f23d0-121">ASP.NET Web Hizmetleri tarafından mesajlarında türleri tarafından veri sözleşmeleri olarak işlenmesi kuramaz [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] , başka avantajları arasında oluşturan uygulamalar, daha iyi performans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulamalar.</span><span class="sxs-lookup"><span data-stu-id="f23d0-121">The types used in messages by ASP.NET Web services will be able to be processed as data contracts by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications, yielding, amongst other benefits, better performance in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications.</span></span>  
  
## <a name="security"></a><span data-ttu-id="f23d0-122">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="f23d0-122">Security</span></span>  
 <span data-ttu-id="f23d0-123">Internet Information Services (IIS) tarafından sağlanan kimlik doğrulama seçenekleri kullanmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="f23d0-123">Avoid using the authentication options provided by Internet Information Services (IIS).</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="f23d0-124">istemcileri onları desteklemez.</span><span class="sxs-lookup"><span data-stu-id="f23d0-124"> clients do not support them.</span></span> <span data-ttu-id="f23d0-125">Bir hizmeti güvenli hale gerekiyorsa tarafından sağlanan seçenekleri kullanın [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], çünkü bu seçenekler daha zengin ve standart protokollerine dayalıdır.</span><span class="sxs-lookup"><span data-stu-id="f23d0-125">If a service needs to be secured, use the options provided by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], because these options are richer and are based on standard protocols.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f23d0-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f23d0-126">See Also</span></span>  
 [<span data-ttu-id="f23d0-127">Windows Communication Foundation'ı benimsemeyi bekleme: gelecekteki taşınmayı kolaylaştırma</span><span class="sxs-lookup"><span data-stu-id="f23d0-127">Anticipating Adopting the Windows Communication Foundation: Easing Future Migration</span></span>](../../../../docs/framework/wcf/feature-details/anticipating-adopting-wcf-migration.md)
