---
description: 'Hakkında daha fazla bilgi edinin: ASP.NET Web Hizmetleri ile birlikte çalışabilirlik'
title: ASP.NET Web Hizmetleri ile Birlikte Çalışabilirlik
ms.date: 03/30/2017
ms.assetid: 622422f8-6651-442f-b8be-e654a4aabcac
ms.openlocfilehash: f5e439bac3be4c12231653f7059792792edbc21e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802742"
---
# <a name="interoperability-with-aspnet-web-services"></a><span data-ttu-id="09c0f-103">ASP.NET Web Hizmetleri ile Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="09c0f-103">Interoperability with ASP.NET Web Services</span></span>

<span data-ttu-id="09c0f-104">ASP.NET Web Hizmetleri ve Windows Communication Foundation (WCF) Web Hizmetleri arasında birlikte çalışabilirlik, her iki teknolojiyi kullanarak uygulanan hizmetlerin WS-ı temel profil 1,1 belirtimine uyduğundan emin olarak elde edilebilir.</span><span class="sxs-lookup"><span data-stu-id="09c0f-104">Interoperability between ASP.NET Web services and Windows Communication Foundation (WCF) Web services can be achieved by ensuring that services implemented using both technologies conform to the WS-I Basic Profile 1.1 specification.</span></span> <span data-ttu-id="09c0f-105">WS-ı temel profil 1,1 ile uyumlu olan ASP.NET Web Hizmetleri, WCF sistem tarafından sunulan bağlama kullanılarak WCF istemcileriyle birlikte çalışabilir <xref:System.ServiceModel.BasicHttpBinding> .</span><span class="sxs-lookup"><span data-stu-id="09c0f-105">ASP.NET Web services that conform to WS-I Basic Profile 1.1 are interoperable with WCF clients by using WCF system-provided binding, <xref:System.ServiceModel.BasicHttpBinding>.</span></span>  
  
 <span data-ttu-id="09c0f-106"><xref:System.Web.Services.WebService> <xref:System.Web.Services.WebMethodAttribute> Aşağıdaki örnek kodda gösterildiği gibi, ve özniteliklerini bir sınıf yerine arabirime eklemek için ASP.NET 2,0 seçeneğini kullanın ve arabirimi uygulamak için bir sınıf yazmak.</span><span class="sxs-lookup"><span data-stu-id="09c0f-106">Use ASP.NET 2.0 option of adding the <xref:System.Web.Services.WebService> and <xref:System.Web.Services.WebMethodAttribute> attributes to an interface rather than to a class, and writing a class to implement the interface, as shown in the following sample code.</span></span>  
  
```csharp
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
  
 <span data-ttu-id="09c0f-107">Bu seçeneğin kullanılması tercih edilir çünkü özniteliğe sahip arabirim, <xref:System.Web.Services.WebService> hizmet tarafından gerçekleştirilen işlemler için, aynı sözleşmeyi farklı yollarla uygulayabilecek çeşitli sınıflarla yeniden kullanılabilen işlemler için bir sözleşme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="09c0f-107">Using this option is preferred, because the interface with the <xref:System.Web.Services.WebService> attribute constitutes a contract for the operations performed by the service that can be reused with various classes that might implement that same contract in different ways.</span></span>  
  
 <span data-ttu-id="09c0f-108"><xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute>Http üstbilgisi yerıne soap iletisinin gövde öğesinin tam adı temelinde yöntemlere yönlendirilmek için özniteliğini kullanmaktan kaçının `SOAPAction` .</span><span class="sxs-lookup"><span data-stu-id="09c0f-108">Avoid using the <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> attribute to have messages routed to methods based on the fully-qualified name of the body element of the SOAP message rather than the `SOAPAction` HTTP header.</span></span> <span data-ttu-id="09c0f-109">WCF, `SOAPAction` iletileri yönlendirme için http üstbilgisini kullanır.</span><span class="sxs-lookup"><span data-stu-id="09c0f-109">WCF uses the `SOAPAction` HTTP header for routing messages.</span></span>  
  
 <span data-ttu-id="09c0f-110"><xref:System.Xml.Serialization.XmlSerializer>Bir türü varsayılan olarak seri hale getirilen XML, bir türü seri hale getirilen XML ile aynıdır, bu, <xref:System.Runtime.Serialization.DataContractSerializer> XML için ad alanı açıkça tanımlanmış olarak belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="09c0f-110">The XML into which <xref:System.Xml.Serialization.XmlSerializer> serializes a type by default is semantically identical to the XML into which the <xref:System.Runtime.Serialization.DataContractSerializer> serializes a type, provided the namespace for the XML is explicitly defined.</span></span> <span data-ttu-id="09c0f-111">WCF 'yi benimseme olasılığına içinde ASP. NETWeb Hizmetleri ile kullanmak için bir veri türü tanımlarken, aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="09c0f-111">When defining a data type for use with ASP.NETWeb services in anticipation of adopting WCF, do the following:</span></span>  
  
- <span data-ttu-id="09c0f-112">Türü, XML şeması yerine .NET Framework sınıfları kullanarak tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="09c0f-112">Define the type using .NET Framework classes rather than XML Schema.</span></span>  
  
- <span data-ttu-id="09c0f-113"><xref:System.SerializableAttribute> <xref:System.Xml.Serialization.XmlRootAttribute> Türü için ad alanını açıkça tanımlamak için, ikincisini kullanarak yalnızca ve öğesini sınıfına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="09c0f-113">Add only the <xref:System.SerializableAttribute> and the <xref:System.Xml.Serialization.XmlRootAttribute> to the class, using the latter to explicitly define the namespace for the type.</span></span> <span data-ttu-id="09c0f-114"><xref:System.Xml.Serialization>.NET Framework SıNıFıNıN XML 'e nasıl çevrileceğini denetlemek için ad alanından ek öznitelikler eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="09c0f-114">Do not add additional attributes from the <xref:System.Xml.Serialization> namespace to control how the .NET Framework class is to be translated into XML.</span></span>  
  
- <span data-ttu-id="09c0f-115">Bu yaklaşımı benimseerek, daha sonra, <xref:System.Runtime.Serialization.DataContractAttribute> ve <xref:System.Runtime.Serialization.DataMemberAttribute> sınıflarının iletilmek üzere SERILEŞTIRILDIĞI XML 'yi önemli ölçüde değiştirmeksizin, .NET sınıflarını daha sonra ve ' nin eklenmesiyle veri sözleşmeleri halinde yapabilmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="09c0f-115">By adopting this approach, you should be able to later make the .NET classes into data contracts with the addition of the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> without significantly altering the XML into which the classes are serialized for transmission.</span></span> <span data-ttu-id="09c0f-116">ASP.NET Web hizmetlerine göre iletilerde kullanılan türler, WCF uygulamalarında veri sözleşmeleri, diğer avantajlar ve WCF uygulamalarında daha iyi performans gibi işlenebilir.</span><span class="sxs-lookup"><span data-stu-id="09c0f-116">The types used in messages by ASP.NET Web services can be processed as data contracts by WCF applications, yielding, among other benefits, better performance in WCF applications.</span></span>  
  
 <span data-ttu-id="09c0f-117">Internet Information Services (IIS) tarafından sunulan kimlik doğrulama seçeneklerini kullanmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="09c0f-117">Avoid using the authentication options provided by Internet Information Services (IIS).</span></span> <span data-ttu-id="09c0f-118">WCF istemcileri bunları desteklemez.</span><span class="sxs-lookup"><span data-stu-id="09c0f-118">WCF clients do not support them.</span></span> <span data-ttu-id="09c0f-119">Bir hizmetin güvenliğinin sağlanması gerekiyorsa WCF tarafından sağlanan seçenekleri kullanın, çünkü bu seçenekler sağlam ve standart protokolleri temel alır.</span><span class="sxs-lookup"><span data-stu-id="09c0f-119">If a service must be secured, use the options provided by WCF, because these options are robust and are based on standard protocols.</span></span>  
  
## <a name="performance-impact-caused-by-loading-the-servicemodel-httpmodule"></a><span data-ttu-id="09c0f-120">ServiceModel HttpModule yüklemesi nedeniyle performans etkisi</span><span class="sxs-lookup"><span data-stu-id="09c0f-120">Performance impact caused by loading the ServiceModel HttpModule</span></span>  

 <span data-ttu-id="09c0f-121">.NET Framework 3,0 ' de, WCF `HttpModule` her ASP.net UYGULAMASıNıN WCF etkin olduğu gibi kök Web.config dosyasına yüklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="09c0f-121">In the .NET Framework 3.0, the WCF `HttpModule` was installed in the root Web.config file such that every ASP.NET application was WCF enabled.</span></span> <span data-ttu-id="09c0f-122">Bu, `ServiceModel` Aşağıdaki örnekte gösterildiği gibi Web.config dosyasına kaldırabilmeniz için performansı etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="09c0f-122">This might affect performance, so you can remove `ServiceModel` for the Web.config file as shown in the following example.</span></span>  
  
```xml  
<httpModules>  
    <remove name="ServiceModel" />  
</httpModules>
```  
  
## <a name="see-also"></a><span data-ttu-id="09c0f-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="09c0f-123">See also</span></span>

- [<span data-ttu-id="09c0f-124">Nasıl yapılır: WCF Hizmetini ASP.NET Web Hizmeti İstemcileriyle Birlikte Çalışmak için Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="09c0f-124">How to: Configure WCF Service to Interoperate with ASP.NET Web Service Clients</span></span>](config-wcf-service-with-aspnet-web-service.md)
