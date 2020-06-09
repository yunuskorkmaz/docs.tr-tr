---
title: "Windows Communication Foundation'ı Benimsemeyi Bekleme: Gelecekteki Tümleştirmeyi Kolaylaştırma"
ms.date: 03/30/2017
ms.assetid: 3028bba8-6355-4ee0-9ecd-c56e614cb474
ms.openlocfilehash: 6392194b3124c999031123225dcc28c8de6171e9
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84576531"
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-integration"></a><span data-ttu-id="3724d-102">Windows Communication Foundation'ı Benimsemeyi Bekleme: Gelecekteki Tümleştirmeyi Kolaylaştırma</span><span class="sxs-lookup"><span data-stu-id="3724d-102">Anticipating Adopting the Windows Communication Foundation: Easing Future Integration</span></span>
<span data-ttu-id="3724d-103">ASP.NET bugün kullanıyorsanız ve gelecekte WCF kullanmayı düşünüyorsanız, bu konuda yeni ASP.NET Web hizmetlerinin WCF uygulamalarıyla birlikte iyi şekilde çalışmasını sağlamak için rehberlik sağlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="3724d-103">If you use ASP.NET today, and anticipate using WCF in the future, this topic provides guidance to ensure that new ASP.NET Web services will work well together with WCF applications.</span></span>  
  
## <a name="general-recommendations"></a><span data-ttu-id="3724d-104">Genel öneriler</span><span class="sxs-lookup"><span data-stu-id="3724d-104">General Recommendations</span></span>  
 <span data-ttu-id="3724d-105">Tüm yeni hizmetler için ASP.NET 2,0 benimseyin.</span><span class="sxs-lookup"><span data-stu-id="3724d-105">Adopt ASP.NET 2.0 for any new services.</span></span> <span data-ttu-id="3724d-106">Bu işlem, yeni sürümün geliştirmeleri ve geliştirmeleri için erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="3724d-106">Doing so will provide access to the improvements and enhancements of the new version.</span></span> <span data-ttu-id="3724d-107">Ancak, ASP.NET 2,0 bileşenlerini aynı uygulamadaki WCF bileşenleriyle birlikte kullanma olasılığa de izin verir.</span><span class="sxs-lookup"><span data-stu-id="3724d-107">However, it will also allow for the possibility of using ASP.NET 2.0 components together with WCF components in the same application.</span></span>  
  
## <a name="protocols"></a><span data-ttu-id="3724d-108">Protokoller</span><span class="sxs-lookup"><span data-stu-id="3724d-108">Protocols</span></span>  
 <span data-ttu-id="3724d-109">ASP.NET 2.0 'ın, WS-ı temel profil 1,1 ile uyumluluğunu doğrulamak için yeni tesis kullanın:</span><span class="sxs-lookup"><span data-stu-id="3724d-109">Use ASP.NET 2.0’s new facility for validating conformity to the WS-I Basic Profile 1.1:</span></span>  
  
```csharp  
[WebService(Namespace = "http://tempuri.org/")]  
[WebServiceBinding(  
     ConformsTo = WsiProfiles.BasicProfile1_1,  
     EmitConformanceClaims=true)]  
public interface IEcho  
```  
  
 <span data-ttu-id="3724d-110">WS-ı temel profil 1,1 ile uyumlu olan ASP.NET Web Hizmetleri, WCF istemcileri ile önceden tanımlanmış WCF kullanılarak birlikte çalışabilir <xref:System.ServiceModel.BasicHttpBinding> .</span><span class="sxs-lookup"><span data-stu-id="3724d-110">ASP.NET Web services that conform to WS-I Basic Profile 1.1 will be interoperable with WCF clients by using WCF predefined binding, <xref:System.ServiceModel.BasicHttpBinding>.</span></span>  
  
## <a name="service-development"></a><span data-ttu-id="3724d-111">Hizmet geliştirme</span><span class="sxs-lookup"><span data-stu-id="3724d-111">Service Development</span></span>  
 <span data-ttu-id="3724d-112"><xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute>SOAPACTION http üstbilgisi yerıne soap iletisinin gövde öğesinin tam adına bağlı olarak yöntemlere yönlendirilmek için özniteliğini kullanmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="3724d-112">Avoid using the <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> attribute to have messages routed to methods based on the fully-qualified name of the body element of the SOAP message rather than the SOAPAction HTTP header.</span></span> <span data-ttu-id="3724d-113">WCF iletileri yönlendirmek için SOAPAction HTTP üstbilgisini kullanır.</span><span class="sxs-lookup"><span data-stu-id="3724d-113">WCF uses the SOAPAction HTTP header for routing messages.</span></span>  
  
## <a name="data-representation"></a><span data-ttu-id="3724d-114">Veri gösterimi</span><span class="sxs-lookup"><span data-stu-id="3724d-114">Data Representation</span></span>  
 <span data-ttu-id="3724d-115"><xref:System.Xml.Serialization.XmlSerializer>Bir türü varsayılan olarak seri hale getirilen XML, bir türü seri hale getirilen XML ile aynıdır, bu, <xref:System.Runtime.Serialization.DataContractSerializer> XML için ad alanı açıkça tanımlanmış olarak belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="3724d-115">The XML into which <xref:System.Xml.Serialization.XmlSerializer> serializes a type by default is semantically identical to the XML into which the <xref:System.Runtime.Serialization.DataContractSerializer> serializes a type, provided the namespace for the XML is explicitly defined.</span></span> <span data-ttu-id="3724d-116">Daha sonra WCF 'yi benimseme olasılığına 'de ASP.NET Web Hizmetleri ile kullanmak için bir veri türü tanımlarken, şunları yapın:</span><span class="sxs-lookup"><span data-stu-id="3724d-116">When defining a data type for use with ASP.NET Web services in anticipation of adopting WCF in the future, do the following:</span></span>  
  
1. <span data-ttu-id="3724d-117">Türü, XML şeması yerine .NET Framework sınıfları kullanarak tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="3724d-117">Define the type using .NET Framework classes rather than XML Schema.</span></span>  
  
2. <span data-ttu-id="3724d-118"><xref:System.SerializableAttribute> <xref:System.Xml.Serialization.XmlRootAttribute> Türü için ad alanını açıkça tanımlamak için, ikincisini kullanarak yalnızca ve öğesini sınıfına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3724d-118">Add only the <xref:System.SerializableAttribute> and the <xref:System.Xml.Serialization.XmlRootAttribute> to the class, using the latter to explicitly define the namespace for the type.</span></span> <span data-ttu-id="3724d-119"><xref:System.Xml.Serialization>.NET Framework SıNıFıNıN XML 'e nasıl çevrileceğini denetlemek için ad alanından ek öznitelikler eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="3724d-119">Do no add additional attributes from the <xref:System.Xml.Serialization> namespace to control how the .NET Framework class is to be translated into XML.</span></span>  
  
 <span data-ttu-id="3724d-120">Bu yaklaşımı benimseerek, daha sonra, <xref:System.Runtime.Serialization.DataContractAttribute> ve <xref:System.Runtime.Serialization.DataMemberAttribute> sınıflarının iletilmek üzere SERILEŞTIRILDIĞI XML 'yi önemli ölçüde değiştirmeksizin, .NET sınıflarını daha sonra ve ' nin eklenmesiyle veri sözleşmeleri halinde yapabilmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="3724d-120">By adopting this approach, you should be able to later make the .NET classes into data contracts with the addition of the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> without significantly altering the XML into which the classes are serialized for transmission.</span></span> <span data-ttu-id="3724d-121">ASP.NET Web hizmetlerine göre iletilerde kullanılan türler, WCF uygulamalarında veri sözleşmeleri, diğer avantajlar arasında, WCF uygulamalarında daha iyi performans olarak işlenebilecektir.</span><span class="sxs-lookup"><span data-stu-id="3724d-121">The types used in messages by ASP.NET Web services will be able to be processed as data contracts by WCF applications, yielding, amongst other benefits, better performance in WCF applications.</span></span>  
  
## <a name="security"></a><span data-ttu-id="3724d-122">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="3724d-122">Security</span></span>  
 <span data-ttu-id="3724d-123">Internet Information Services (IIS) tarafından sunulan kimlik doğrulama seçeneklerini kullanmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="3724d-123">Avoid using the authentication options provided by Internet Information Services (IIS).</span></span> <span data-ttu-id="3724d-124">WCF istemcileri bunları desteklemez.</span><span class="sxs-lookup"><span data-stu-id="3724d-124">WCF clients do not support them.</span></span> <span data-ttu-id="3724d-125">Bir hizmetin güvenliğinin sağlanması gerekiyorsa, bu seçenekler daha zengin ve standart protokollerin temel aldığı için WCF tarafından sağlanan seçenekleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="3724d-125">If a service needs to be secured, use the options provided by WCF, because these options are richer and are based on standard protocols.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3724d-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3724d-126">See also</span></span>

- [<span data-ttu-id="3724d-127">Windows Communication Foundation'ı Benimsemeyi Bekleme: Gelecekteki Taşınmayı Kolaylaştırma</span><span class="sxs-lookup"><span data-stu-id="3724d-127">Anticipating Adopting the Windows Communication Foundation: Easing Future Migration</span></span>](anticipating-adopting-wcf-migration.md)
