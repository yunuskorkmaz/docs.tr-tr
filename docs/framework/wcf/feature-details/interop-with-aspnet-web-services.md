---
title: ASP.NET Web Hizmetleri ile Birlikte Çalışabilirlik
ms.date: 03/30/2017
ms.assetid: 622422f8-6651-442f-b8be-e654a4aabcac
ms.openlocfilehash: 59ee6412cde152588e8007fe530cc8e5708410e5
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991527"
---
# <a name="interoperability-with-aspnet-web-services"></a><span data-ttu-id="ec0fc-102">ASP.NET Web Hizmetleri ile Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="ec0fc-102">Interoperability with ASP.NET Web Services</span></span>
<span data-ttu-id="ec0fc-103">ASP.NET Web Hizmetleri ve Windows Communication Foundation (WCF) Web Hizmetleri arasında birlikte çalışabilirlik, her iki teknolojiyi kullanarak uygulanan hizmetlerin WS-ı temel profil 1,1 belirtimine uyduğundan emin olarak elde edilebilir.</span><span class="sxs-lookup"><span data-stu-id="ec0fc-103">Interoperability between ASP.NET Web services and Windows Communication Foundation (WCF) Web services can be achieved by ensuring that services implemented using both technologies conform to the WS-I Basic Profile 1.1 specification.</span></span> <span data-ttu-id="ec0fc-104">WS-ı temel profil 1,1 ile uyumlu olan ASP.NET Web Hizmetleri, <xref:System.ServiceModel.BasicHttpBinding>WCF sistem tarafından sunulan bağlama kullanılarak WCF istemcileriyle birlikte çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="ec0fc-104">ASP.NET Web services that conform to WS-I Basic Profile 1.1 are interoperable with WCF clients by using WCF system-provided binding, <xref:System.ServiceModel.BasicHttpBinding>.</span></span>  
  
 <span data-ttu-id="ec0fc-105">Aşağıdaki örnek kodda gösterildiği gibi, <xref:System.Web.Services.WebService> ve <xref:System.Web.Services.WebMethodAttribute> özniteliklerini bir sınıf yerine arabirime eklemek için ASP.NET 2,0 seçeneğini kullanın ve arabirimi uygulamak için bir sınıf yazmak.</span><span class="sxs-lookup"><span data-stu-id="ec0fc-105">Use ASP.NET 2.0 option of adding the <xref:System.Web.Services.WebService> and <xref:System.Web.Services.WebMethodAttribute> attributes to an interface rather than to a class, and writing a class to implement the interface, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="ec0fc-106">Bu seçeneğin kullanılması tercih edilir çünkü <xref:System.Web.Services.WebService> özniteliğe sahip arabirim, hizmet tarafından gerçekleştirilen işlemler için, aynı sözleşmeyi farklı yollarla uygulayabilecek çeşitli sınıflarla yeniden kullanılabilen işlemler için bir sözleşme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ec0fc-106">Using this option is preferred, because the interface with the <xref:System.Web.Services.WebService> attribute constitutes a contract for the operations performed by the service that can be reused with various classes that might implement that same contract in different ways.</span></span>  
  
 <span data-ttu-id="ec0fc-107">`SOAPAction` Http üstbilgisi yerine SOAP iletisinin gövde öğesinin tam adı temelinde yöntemlere yönlendirilmek için özniteliğinikullanmaktankaçının.<xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute></span><span class="sxs-lookup"><span data-stu-id="ec0fc-107">Avoid using the <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> attribute to have messages routed to methods based on the fully-qualified name of the body element of the SOAP message rather than the `SOAPAction` HTTP header.</span></span> <span data-ttu-id="ec0fc-108">WCF, `SOAPAction` iletileri yönlendirme için http üstbilgisini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ec0fc-108">WCF uses the `SOAPAction` HTTP header for routing messages.</span></span>  
  
 <span data-ttu-id="ec0fc-109">Bir türü varsayılan <xref:System.Runtime.Serialization.DataContractSerializer> olarak serihalegetirilenXML,birtürüserihalegetirilenXMLileaynıdır,bu,XMLiçinadalanıaçıkçatanımlanmışolarakbelirtilmelidir.<xref:System.Xml.Serialization.XmlSerializer></span><span class="sxs-lookup"><span data-stu-id="ec0fc-109">The XML into which <xref:System.Xml.Serialization.XmlSerializer> serializes a type by default is semantically identical to the XML into which the <xref:System.Runtime.Serialization.DataContractSerializer> serializes a type, provided the namespace for the XML is explicitly defined.</span></span> <span data-ttu-id="ec0fc-110">WCF 'yi benimseme olasılığına içinde ASP. NETWeb Hizmetleri ile kullanmak için bir veri türü tanımlarken, aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="ec0fc-110">When defining a data type for use with ASP.NETWeb services in anticipation of adopting WCF, do the following:</span></span>  
  
- <span data-ttu-id="ec0fc-111">Türü, XML şeması yerine .NET Framework sınıfları kullanarak tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="ec0fc-111">Define the type using .NET Framework classes rather than XML Schema.</span></span>  
  
- <span data-ttu-id="ec0fc-112">Türü için ad <xref:System.SerializableAttribute> alanını açıkça <xref:System.Xml.Serialization.XmlRootAttribute> tanımlamak için, ikincisini kullanarak yalnızca ve öğesini sınıfına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ec0fc-112">Add only the <xref:System.SerializableAttribute> and the <xref:System.Xml.Serialization.XmlRootAttribute> to the class, using the latter to explicitly define the namespace for the type.</span></span> <span data-ttu-id="ec0fc-113">.NET Framework sınıfının XML 'e nasıl çevrileceğini denetlemek <xref:System.Xml.Serialization> için ad alanından ek öznitelikler eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="ec0fc-113">Do not add additional attributes from the <xref:System.Xml.Serialization> namespace to control how the .NET Framework class is to be translated into XML.</span></span>  
  
- <span data-ttu-id="ec0fc-114">Bu yaklaşımı benimseerek, daha sonra, <xref:System.Runtime.Serialization.DataContractAttribute> ve sınıflarının iletilmek üzere serileştirildiği XML 'yi önemli ölçüde değiştirmeksizin, .NET sınıflarını daha sonra ve ' <xref:System.Runtime.Serialization.DataMemberAttribute> nin eklenmesiyle veri sözleşmeleri halinde yapabilmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="ec0fc-114">By adopting this approach, you should be able to later make the .NET classes into data contracts with the addition of the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> without significantly altering the XML into which the classes are serialized for transmission.</span></span> <span data-ttu-id="ec0fc-115">ASP.NET Web hizmetlerine göre iletilerde kullanılan türler, WCF uygulamalarında veri sözleşmeleri, diğer avantajlar ve WCF uygulamalarında daha iyi performans gibi işlenebilir.</span><span class="sxs-lookup"><span data-stu-id="ec0fc-115">The types used in messages by ASP.NET Web services can be processed as data contracts by WCF applications, yielding, among other benefits, better performance in WCF applications.</span></span>  
  
 <span data-ttu-id="ec0fc-116">Internet Information Services (IIS) tarafından sunulan kimlik doğrulama seçeneklerini kullanmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="ec0fc-116">Avoid using the authentication options provided by Internet Information Services (IIS).</span></span> <span data-ttu-id="ec0fc-117">WCF istemcileri bunları desteklemez.</span><span class="sxs-lookup"><span data-stu-id="ec0fc-117">WCF clients do not support them.</span></span> <span data-ttu-id="ec0fc-118">Bir hizmetin güvenliğinin sağlanması gerekiyorsa WCF tarafından sağlanan seçenekleri kullanın, çünkü bu seçenekler sağlam ve standart protokolleri temel alır.</span><span class="sxs-lookup"><span data-stu-id="ec0fc-118">If a service must be secured, use the options provided by WCF, because these options are robust and are based on standard protocols.</span></span>  
  
## <a name="performance-impact-caused-by-loading-the-servicemodel-httpmodule"></a><span data-ttu-id="ec0fc-119">ServiceModel HttpModule yüklemesi nedeniyle performans etkisi</span><span class="sxs-lookup"><span data-stu-id="ec0fc-119">Performance impact caused by loading the ServiceModel HttpModule</span></span>  
 <span data-ttu-id="ec0fc-120">.NET Framework 3,0 ' de, WCF `HttpModule` , kök Web. config dosyasında her ASP.NET uygulamasının WCF etkin olduğu gibi yüklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="ec0fc-120">In the .NET Framework 3.0, the WCF `HttpModule` was installed in the root Web.config file such that every ASP.NET application was WCF enabled.</span></span> <span data-ttu-id="ec0fc-121">Bu, aşağıdaki örnekte gösterildiği gibi Web. config `ServiceModel` dosyasını kaldırabilmeniz için performansı etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="ec0fc-121">This might affect performance, so you can remove `ServiceModel` for the Web.config file as shown in the following example.</span></span>  
  
```xml  
<httpModules>  
    <remove name="ServiceModel" />  
<httpModules/>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ec0fc-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ec0fc-122">See also</span></span>

- [<span data-ttu-id="ec0fc-123">Nasıl yapılır: WCF hizmetini ASP.NET Web hizmeti Istemcileriyle birlikte çalışmak üzere yapılandırma</span><span class="sxs-lookup"><span data-stu-id="ec0fc-123">How to: Configure WCF Service to Interoperate with ASP.NET Web Service Clients</span></span>](../../../../docs/framework/wcf/feature-details/config-wcf-service-with-aspnet-web-service.md)
