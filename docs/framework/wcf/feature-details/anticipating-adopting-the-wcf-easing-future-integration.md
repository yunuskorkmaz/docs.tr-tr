---
description: 'Hakkında daha fazla bilgi edinin: Windows Communication Foundation benimsemeyi bekleme benimseme: gelecekteki tümleştirme kolaylaştırıcı'
title: "Windows Communication Foundation'ı Benimsemeyi Bekleme: Gelecekteki Tümleştirmeyi Kolaylaştırma"
ms.date: 03/30/2017
ms.assetid: 3028bba8-6355-4ee0-9ecd-c56e614cb474
ms.openlocfilehash: 512e35e8a4cd6057c96e96a1474f393c3f006525
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99643884"
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-integration"></a><span data-ttu-id="e8017-103">Windows Communication Foundation'ı Benimsemeyi Bekleme: Gelecekteki Tümleştirmeyi Kolaylaştırma</span><span class="sxs-lookup"><span data-stu-id="e8017-103">Anticipating Adopting the Windows Communication Foundation: Easing Future Integration</span></span>

<span data-ttu-id="e8017-104">ASP.NET bugün kullanıyorsanız ve gelecekte WCF kullanmayı düşünüyorsanız, bu konuda yeni ASP.NET Web hizmetlerinin WCF uygulamalarıyla birlikte iyi şekilde çalışmasını sağlamak için rehberlik sağlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="e8017-104">If you use ASP.NET today, and anticipate using WCF in the future, this topic provides guidance to ensure that new ASP.NET Web services will work well together with WCF applications.</span></span>  
  
## <a name="general-recommendations"></a><span data-ttu-id="e8017-105">Genel öneriler</span><span class="sxs-lookup"><span data-stu-id="e8017-105">General Recommendations</span></span>  

 <span data-ttu-id="e8017-106">Tüm yeni hizmetler için ASP.NET 2,0 benimseyin.</span><span class="sxs-lookup"><span data-stu-id="e8017-106">Adopt ASP.NET 2.0 for any new services.</span></span> <span data-ttu-id="e8017-107">Bu işlem, yeni sürümün geliştirmeleri ve geliştirmeleri için erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="e8017-107">Doing so will provide access to the improvements and enhancements of the new version.</span></span> <span data-ttu-id="e8017-108">Ancak, ASP.NET 2,0 bileşenlerini aynı uygulamadaki WCF bileşenleriyle birlikte kullanma olasılığa de izin verir.</span><span class="sxs-lookup"><span data-stu-id="e8017-108">However, it will also allow for the possibility of using ASP.NET 2.0 components together with WCF components in the same application.</span></span>  
  
## <a name="protocols"></a><span data-ttu-id="e8017-109">Protokoller</span><span class="sxs-lookup"><span data-stu-id="e8017-109">Protocols</span></span>  

 <span data-ttu-id="e8017-110">ASP.NET 2.0 'ın, WS-ı temel profil 1,1 ile uyumluluğunu doğrulamak için yeni tesis kullanın:</span><span class="sxs-lookup"><span data-stu-id="e8017-110">Use ASP.NET 2.0’s new facility for validating conformity to the WS-I Basic Profile 1.1:</span></span>  
  
```csharp  
[WebService(Namespace = "http://tempuri.org/")]  
[WebServiceBinding(  
     ConformsTo = WsiProfiles.BasicProfile1_1,  
     EmitConformanceClaims=true)]  
public interface IEcho  
```  
  
 <span data-ttu-id="e8017-111">WS-ı temel profil 1,1 ile uyumlu olan ASP.NET Web Hizmetleri, WCF istemcileri ile önceden tanımlanmış WCF kullanılarak birlikte çalışabilir <xref:System.ServiceModel.BasicHttpBinding> .</span><span class="sxs-lookup"><span data-stu-id="e8017-111">ASP.NET Web services that conform to WS-I Basic Profile 1.1 will be interoperable with WCF clients by using WCF predefined binding, <xref:System.ServiceModel.BasicHttpBinding>.</span></span>  
  
## <a name="service-development"></a><span data-ttu-id="e8017-112">Hizmet geliştirme</span><span class="sxs-lookup"><span data-stu-id="e8017-112">Service Development</span></span>  

 <span data-ttu-id="e8017-113"><xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute>SOAPACTION http üstbilgisi yerıne soap iletisinin gövde öğesinin tam adına bağlı olarak yöntemlere yönlendirilmek için özniteliğini kullanmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="e8017-113">Avoid using the <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> attribute to have messages routed to methods based on the fully-qualified name of the body element of the SOAP message rather than the SOAPAction HTTP header.</span></span> <span data-ttu-id="e8017-114">WCF iletileri yönlendirmek için SOAPAction HTTP üstbilgisini kullanır.</span><span class="sxs-lookup"><span data-stu-id="e8017-114">WCF uses the SOAPAction HTTP header for routing messages.</span></span>  
  
## <a name="data-representation"></a><span data-ttu-id="e8017-115">Veri gösterimi</span><span class="sxs-lookup"><span data-stu-id="e8017-115">Data Representation</span></span>  

 <span data-ttu-id="e8017-116"><xref:System.Xml.Serialization.XmlSerializer>Bir türü varsayılan olarak seri hale getirilen XML, bir türü seri hale getirilen XML ile aynıdır, bu, <xref:System.Runtime.Serialization.DataContractSerializer> XML için ad alanı açıkça tanımlanmış olarak belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="e8017-116">The XML into which <xref:System.Xml.Serialization.XmlSerializer> serializes a type by default is semantically identical to the XML into which the <xref:System.Runtime.Serialization.DataContractSerializer> serializes a type, provided the namespace for the XML is explicitly defined.</span></span> <span data-ttu-id="e8017-117">Daha sonra WCF 'yi benimseme olasılığına 'de ASP.NET Web Hizmetleri ile kullanmak için bir veri türü tanımlarken, şunları yapın:</span><span class="sxs-lookup"><span data-stu-id="e8017-117">When defining a data type for use with ASP.NET Web services in anticipation of adopting WCF in the future, do the following:</span></span>  
  
1. <span data-ttu-id="e8017-118">Türü, XML şeması yerine .NET Framework sınıfları kullanarak tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="e8017-118">Define the type using .NET Framework classes rather than XML Schema.</span></span>  
  
2. <span data-ttu-id="e8017-119"><xref:System.SerializableAttribute> <xref:System.Xml.Serialization.XmlRootAttribute> Türü için ad alanını açıkça tanımlamak için, ikincisini kullanarak yalnızca ve öğesini sınıfına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e8017-119">Add only the <xref:System.SerializableAttribute> and the <xref:System.Xml.Serialization.XmlRootAttribute> to the class, using the latter to explicitly define the namespace for the type.</span></span> <span data-ttu-id="e8017-120"><xref:System.Xml.Serialization>.NET Framework SıNıFıNıN XML 'e nasıl çevrileceğini denetlemek için ad alanından ek öznitelikler eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="e8017-120">Do no add additional attributes from the <xref:System.Xml.Serialization> namespace to control how the .NET Framework class is to be translated into XML.</span></span>  
  
 <span data-ttu-id="e8017-121">Bu yaklaşımı benimseerek, daha sonra, <xref:System.Runtime.Serialization.DataContractAttribute> ve <xref:System.Runtime.Serialization.DataMemberAttribute> sınıflarının iletilmek üzere SERILEŞTIRILDIĞI XML 'yi önemli ölçüde değiştirmeksizin, .NET sınıflarını daha sonra ve ' nin eklenmesiyle veri sözleşmeleri halinde yapabilmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="e8017-121">By adopting this approach, you should be able to later make the .NET classes into data contracts with the addition of the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> without significantly altering the XML into which the classes are serialized for transmission.</span></span> <span data-ttu-id="e8017-122">ASP.NET Web hizmetlerine göre iletilerde kullanılan türler, WCF uygulamalarında veri sözleşmeleri, diğer avantajlar arasında, WCF uygulamalarında daha iyi performans olarak işlenebilecektir.</span><span class="sxs-lookup"><span data-stu-id="e8017-122">The types used in messages by ASP.NET Web services will be able to be processed as data contracts by WCF applications, yielding, amongst other benefits, better performance in WCF applications.</span></span>  
  
## <a name="security"></a><span data-ttu-id="e8017-123">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="e8017-123">Security</span></span>  

 <span data-ttu-id="e8017-124">Internet Information Services (IIS) tarafından sunulan kimlik doğrulama seçeneklerini kullanmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="e8017-124">Avoid using the authentication options provided by Internet Information Services (IIS).</span></span> <span data-ttu-id="e8017-125">WCF istemcileri bunları desteklemez.</span><span class="sxs-lookup"><span data-stu-id="e8017-125">WCF clients do not support them.</span></span> <span data-ttu-id="e8017-126">Bir hizmetin güvenliğinin sağlanması gerekiyorsa, bu seçenekler daha zengin ve standart protokollerin temel aldığı için WCF tarafından sağlanan seçenekleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="e8017-126">If a service needs to be secured, use the options provided by WCF, because these options are richer and are based on standard protocols.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8017-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e8017-127">See also</span></span>

- [<span data-ttu-id="e8017-128">Windows Communication Foundation'ı Benimsemeyi Bekleme: Gelecekteki Geçişi Kolaylaştırma</span><span class="sxs-lookup"><span data-stu-id="e8017-128">Anticipating Adopting the Windows Communication Foundation: Easing Future Migration</span></span>](anticipating-adopting-wcf-migration.md)
