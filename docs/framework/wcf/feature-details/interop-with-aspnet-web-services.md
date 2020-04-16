---
title: ASP.NET Web Hizmetleri ile Birlikte Çalışabilirlik
ms.date: 03/30/2017
ms.assetid: 622422f8-6651-442f-b8be-e654a4aabcac
ms.openlocfilehash: 41810d8044e4b7ff3193950a914edbf1e61cffb1
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81464087"
---
# <a name="interoperability-with-aspnet-web-services"></a><span data-ttu-id="a8457-102">ASP.NET Web Hizmetleri ile Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="a8457-102">Interoperability with ASP.NET Web Services</span></span>
<span data-ttu-id="a8457-103">ASP.NET Web hizmetleri ile Windows Communication Foundation (WCF) Web hizmetleri arasında birlikte çalışabilirlik, her iki teknoloji kullanılarak uygulanan hizmetlerin WS-I Temel Profil 1.1 belirtimine uygun olmasını sağlayarak elde edilebilir.</span><span class="sxs-lookup"><span data-stu-id="a8457-103">Interoperability between ASP.NET Web services and Windows Communication Foundation (WCF) Web services can be achieved by ensuring that services implemented using both technologies conform to the WS-I Basic Profile 1.1 specification.</span></span> <span data-ttu-id="a8457-104">WS-I Temel Profil 1.1'e uygun ASP.NET Web hizmetleri, <xref:System.ServiceModel.BasicHttpBinding>WCF sistemi tarafından sağlanan bağlama kullanılarak WCF istemcileri ile birlikte çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="a8457-104">ASP.NET Web services that conform to WS-I Basic Profile 1.1 are interoperable with WCF clients by using WCF system-provided binding, <xref:System.ServiceModel.BasicHttpBinding>.</span></span>  
  
 <span data-ttu-id="a8457-105">ASP.NET 2.0 seçeneğini kullanarak <xref:System.Web.Services.WebService> <xref:System.Web.Services.WebMethodAttribute> sınıfyerine arabirime ve öznitelikleri ekleme ve aşağıdaki örnek kodda gösterildiği gibi arabirimi uygulamak için bir sınıf yazma seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="a8457-105">Use ASP.NET 2.0 option of adding the <xref:System.Web.Services.WebService> and <xref:System.Web.Services.WebMethodAttribute> attributes to an interface rather than to a class, and writing a class to implement the interface, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="a8457-106">Öznitelik ile <xref:System.Web.Services.WebService> arabirim farklı şekillerde aynı sözleşmeyi uygulayabilir çeşitli sınıflar ile yeniden kullanılabilir hizmet tarafından gerçekleştirilen işlemler için bir sözleşme oluşturduğundan, bu seçeneğin kullanılması tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="a8457-106">Using this option is preferred, because the interface with the <xref:System.Web.Services.WebService> attribute constitutes a contract for the operations performed by the service that can be reused with various classes that might implement that same contract in different ways.</span></span>  
  
 <span data-ttu-id="a8457-107">İletilerin <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> `SOAPAction` HTTP üstbilgiyerine SOAP iletisinin gövde öğesinin tam nitelikli adını temel alan yöntemlere yönlendirilmiş olması için özniteliği kullanmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="a8457-107">Avoid using the <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> attribute to have messages routed to methods based on the fully-qualified name of the body element of the SOAP message rather than the `SOAPAction` HTTP header.</span></span> <span data-ttu-id="a8457-108">WCF iletileri yönlendirme için `SOAPAction` HTTP üstbilgisini kullanır.</span><span class="sxs-lookup"><span data-stu-id="a8457-108">WCF uses the `SOAPAction` HTTP header for routing messages.</span></span>  
  
 <span data-ttu-id="a8457-109">Bir türü varsayılan <xref:System.Xml.Serialization.XmlSerializer> olarak serileştiren XML, XML'in ad alanının açıkça tanımlanması koşuluyla, bir türü <xref:System.Runtime.Serialization.DataContractSerializer> serileştirdiği XML ile anlamsal olarak aynıdır.</span><span class="sxs-lookup"><span data-stu-id="a8457-109">The XML into which <xref:System.Xml.Serialization.XmlSerializer> serializes a type by default is semantically identical to the XML into which the <xref:System.Runtime.Serialization.DataContractSerializer> serializes a type, provided the namespace for the XML is explicitly defined.</span></span> <span data-ttu-id="a8457-110">WCF'yi benimseme beklentisiyle ASP.NETWeb hizmetlerinde kullanılmak üzere bir veri türü tanımlarken aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="a8457-110">When defining a data type for use with ASP.NETWeb services in anticipation of adopting WCF, do the following:</span></span>  
  
- <span data-ttu-id="a8457-111">XML Şeması yerine .NET Framework sınıflarını kullanarak türü tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="a8457-111">Define the type using .NET Framework classes rather than XML Schema.</span></span>  
  
- <span data-ttu-id="a8457-112">Türü için <xref:System.SerializableAttribute> ad <xref:System.Xml.Serialization.XmlRootAttribute> alanını açıkça tanımlamak için ikincisini kullanarak yalnızca ve sınıfa ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a8457-112">Add only the <xref:System.SerializableAttribute> and the <xref:System.Xml.Serialization.XmlRootAttribute> to the class, using the latter to explicitly define the namespace for the type.</span></span> <span data-ttu-id="a8457-113">.NET Framework sınıfının <xref:System.Xml.Serialization> XML'e nasıl çevrileceğini denetlemek için ad alanından ek öznitelikler eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="a8457-113">Do not add additional attributes from the <xref:System.Xml.Serialization> namespace to control how the .NET Framework class is to be translated into XML.</span></span>  
  
- <span data-ttu-id="a8457-114">Bu yaklaşımı benimseyerek, .NET sınıflarını daha sonra veri sözleşmelerine ekleyerek <xref:System.Runtime.Serialization.DataContractAttribute> <xref:System.Runtime.Serialization.DataMemberAttribute> ve sınıfların iletim için seri hale getirildiği XML'yi önemli ölçüde değiştirmeden yapabilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a8457-114">By adopting this approach, you should be able to later make the .NET classes into data contracts with the addition of the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> without significantly altering the XML into which the classes are serialized for transmission.</span></span> <span data-ttu-id="a8457-115">ASP.NET Web hizmetleri tarafından iletilerde kullanılan türler, WCF uygulamaları tarafından veri sözleşmeleri olarak işlenebilir ve wcf uygulamalarında diğer avantajların yanı sıra daha iyi performans sağlar.</span><span class="sxs-lookup"><span data-stu-id="a8457-115">The types used in messages by ASP.NET Web services can be processed as data contracts by WCF applications, yielding, among other benefits, better performance in WCF applications.</span></span>  
  
 <span data-ttu-id="a8457-116">Internet Information Services (IIS) tarafından sağlanan kimlik doğrulama seçeneklerini kullanmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="a8457-116">Avoid using the authentication options provided by Internet Information Services (IIS).</span></span> <span data-ttu-id="a8457-117">WCF istemcileri bunları desteklemez.</span><span class="sxs-lookup"><span data-stu-id="a8457-117">WCF clients do not support them.</span></span> <span data-ttu-id="a8457-118">Bir hizmetin güvence altına alınması gerekiyorsa, bu seçenekler sağlam olduğundan ve standart protokollere dayandığından WCF tarafından sağlanan seçenekleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="a8457-118">If a service must be secured, use the options provided by WCF, because these options are robust and are based on standard protocols.</span></span>  
  
## <a name="performance-impact-caused-by-loading-the-servicemodel-httpmodule"></a><span data-ttu-id="a8457-119">ServiceModel HttpModule'in yüklenmesinden kaynaklanan performans etkisi</span><span class="sxs-lookup"><span data-stu-id="a8457-119">Performance impact caused by loading the ServiceModel HttpModule</span></span>  
 <span data-ttu-id="a8457-120">.NET Framework 3.0'da, `HttpModule` WCF root Web.config dosyasına her ASP.NET uygulamanın WCF etkin olduğunu yüklenmiş.</span><span class="sxs-lookup"><span data-stu-id="a8457-120">In the .NET Framework 3.0, the WCF `HttpModule` was installed in the root Web.config file such that every ASP.NET application was WCF enabled.</span></span> <span data-ttu-id="a8457-121">Bu performansı etkileyebilir, böylece `ServiceModel` aşağıdaki örnekte gösterildiği gibi Web.config dosyası için kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a8457-121">This might affect performance, so you can remove `ServiceModel` for the Web.config file as shown in the following example.</span></span>  
  
```xml  
<httpModules>  
    <remove name="ServiceModel" />  
</httpModules>
```  
  
## <a name="see-also"></a><span data-ttu-id="a8457-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a8457-122">See also</span></span>

- [<span data-ttu-id="a8457-123">Nasıl yapılır: WCF Hizmetini ASP.NET Web Hizmeti İstemcileriyle Birlikte Çalışmak için Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a8457-123">How to: Configure WCF Service to Interoperate with ASP.NET Web Service Clients</span></span>](../../../../docs/framework/wcf/feature-details/config-wcf-service-with-aspnet-web-service.md)
