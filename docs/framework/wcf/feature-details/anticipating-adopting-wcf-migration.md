---
title: "Windows Communication Foundation'ı Benimsemeyi Bekleme: Gelecekteki Taşınmayı Kolaylaştırma"
ms.date: 03/30/2017
ms.assetid: f49664d9-e9e0-425c-a259-93f0a569d01b
ms.openlocfilehash: 995bdaaaba96bf8697ea75c1f1a17fa8e51ec2d5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185466"
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-migration"></a><span data-ttu-id="097dd-102">Windows Communication Foundation'ı Benimsemeyi Bekleme: Gelecekteki Taşınmayı Kolaylaştırma</span><span class="sxs-lookup"><span data-stu-id="097dd-102">Anticipating Adopting the Windows Communication Foundation: Easing Future Migration</span></span>
<span data-ttu-id="097dd-103">WCF'ye yeni ASP.NET uygulamalarının gelecekte daha kolay geçişini sağlamak için, aşağıdaki önerilerin yanı sıra önceki önerileri de izleyin.</span><span class="sxs-lookup"><span data-stu-id="097dd-103">To ensure an easier future migration of new ASP.NET applications to WCF, follow the preceding recommendations as well as the following recommendations.</span></span>  
  
## <a name="protocols"></a><span data-ttu-id="097dd-104">Protokoller</span><span class="sxs-lookup"><span data-stu-id="097dd-104">Protocols</span></span>  
 <span data-ttu-id="097dd-105">SOAP 1.2 için 2.0 desteğiASP.NET devre dışı kalım:</span><span class="sxs-lookup"><span data-stu-id="097dd-105">Disable ASP.NET 2.0’s support for SOAP 1.2:</span></span>  
  
```xml  
<configuration>  
     <system.web>  
      <webServices >  
          <protocols>  
           <remove name="HttpSoap12"/>  
          </protocols>
      </webServices>  
     </system.web>
</configuration>  
```  
  
 <span data-ttu-id="097dd-106">WCF, SOAP 1.1 ve SOAP 1.2 gibi farklı protokollere uygun iletilerin farklı uç noktaları kullanarak kullanılmasını gerektirdiğinden bunu yapmak tavsiye edilir.</span><span class="sxs-lookup"><span data-stu-id="097dd-106">Doing so is advisable because WCF requires messages conforming to different protocols, like SOAP 1.1 and SOAP 1.2, to go by using different endpoints.</span></span> <span data-ttu-id="097dd-107">Bir ASP.NET 2.0 Web hizmeti, varsayılan yapılandırma olan SOAP 1.1 ve SOAP 1.2'yi destekleyecek şekilde yapılandırılırsa, orijinal adreste kesinlikle tüm ASP.NET Web ile uyumlu olacak tek bir WCF bitiş noktasına geçirilemez. hizmetin mevcut istemcileri.</span><span class="sxs-lookup"><span data-stu-id="097dd-107">If an ASP.NET 2.0 Web service is configured to support both SOAP 1.1 and SOAP 1.2, which is the default configuration, then it cannot be migrated forward to a single WCF endpoint at the original address that would be certainly be compatible with all of the ASP.NET Web service’s existing clients.</span></span> <span data-ttu-id="097dd-108">Ayrıca 1.1 yerine SOAP 1.2'yi seçmek, hizmetin müşterilerini daha ciddi bir şekilde kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="097dd-108">Also choosing SOAP 1.2 instead of 1.1 will more severely restrict the clientele of the service.</span></span>  
  
## <a name="service-development"></a><span data-ttu-id="097dd-109">Hizmet Geliştirme</span><span class="sxs-lookup"><span data-stu-id="097dd-109">Service Development</span></span>  
 <span data-ttu-id="097dd-110">WCF, arabirimlere <xref:System.ServiceModel.ServiceContractAttribute> veya sınıflara uygulayarak hizmet sözleşmelerini tanımlamanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="097dd-110">WCF allows you to define service contracts by applying the <xref:System.ServiceModel.ServiceContractAttribute> either to interfaces or to classes.</span></span> <span data-ttu-id="097dd-111">Bunu yapmak çeşitli sınıflar herhangi bir sayı tarafından uygulanabilen bir sözleşme tanımı oluşturur, çünkü bu özniteliği bir sınıf yerine bir arabirime uygulamak için önerilir.</span><span class="sxs-lookup"><span data-stu-id="097dd-111">It is recommended to apply the attribute to an interface rather than to a class, because doing so creates a definition of a contract that can be variously implemented by any number of classes.</span></span> <span data-ttu-id="097dd-112">ASP.NET 2.0, öznitelik in <xref:System.Web.Services.WebService> arabirimlerine ve sınıflara uygulanma seçeneğini destekler.</span><span class="sxs-lookup"><span data-stu-id="097dd-112">ASP.NET 2.0 supports the option of applying the <xref:System.Web.Services.WebService> attribute to interfaces as well as classes.</span></span> <span data-ttu-id="097dd-113">Ancak, daha önce de belirtildiği gibi, ASP.NET 2.0'da bir kusur <xref:System.Web.Services.WebService> vardır ve bu öznitelik bir sınıf yerine arabirime uygulandığında özniteliğin Ad alanı parametresinin hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="097dd-113">However, as mentioned already, there is a defect in ASP.NET 2.0, by which the Namespace parameter of the <xref:System.Web.Services.WebService> attribute has no effect when that attribute is applied to an interface rather than a class.</span></span> <span data-ttu-id="097dd-114">Bir hizmetin ad alanını varsayılan değerden değiştirmek genellikle tavsiye `http://tempuri.org`edilir, öznitelik Ad alanı <xref:System.Web.Services.WebService> parametresini kullanarak, öznitelik veya sınıflara <xref:System.ServiceModel.ServiceContractAttribute> öznitelik uygulayarak ASP.NET Web Hizmetleri tanımlamaya devam edilmelidir.</span><span class="sxs-lookup"><span data-stu-id="097dd-114">Since it is generally advisable to modify the namespace of a service from the default value, `http://tempuri.org`, using the Namespace parameter of the <xref:System.Web.Services.WebService> attribute, one should continue defining ASP.NET Web Services by applying the <xref:System.ServiceModel.ServiceContractAttribute> attribute either to interfaces or to classes.</span></span>  
  
- <span data-ttu-id="097dd-115">Bu arabirimlerin tanımlandığı yöntemlerde mümkün olduğunca az kod alabildiğiniz kadar az koda sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="097dd-115">Have as little code as possible in the methods by which those interfaces are defined.</span></span> <span data-ttu-id="097dd-116">Çalışmalarını diğer sınıflara devretsinler.</span><span class="sxs-lookup"><span data-stu-id="097dd-116">Have them delegate their work to other classes.</span></span> <span data-ttu-id="097dd-117">Yeni WCF hizmet türleri de bu sınıflara kendi maddi çalışma temsilci olabilir.</span><span class="sxs-lookup"><span data-stu-id="097dd-117">New WCF service types could then also delegate their substantive work to those classes.</span></span>  
  
- <span data-ttu-id="097dd-118">Parametreyi `MessageName` kullanarak bir hizmetin işlemleri için <xref:System.Web.Services.WebMethodAttribute>açık adlar sağlayın.</span><span class="sxs-lookup"><span data-stu-id="097dd-118">Provide explicit names for the operations of a service using the `MessageName` parameter of the <xref:System.Web.Services.WebMethodAttribute>.</span></span>  
  
    ```csharp  
    [WebMethod(MessageName="ExplicitName")]  
    string Echo(string input);  
    ```  
  
     <span data-ttu-id="097dd-119">ASP.NET işlemleri için varsayılan adlar WCF tarafından sağlanan varsayılan adlardan farklı olduğundan, bunu yapmak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="097dd-119">Doing so is important, because the default names for operations in ASP.NET are different from the default names supplied by WCF.</span></span> <span data-ttu-id="097dd-120">Açık adlar sağlayarak, varsayılan adlara güvenmekten kaçınırsınız.</span><span class="sxs-lookup"><span data-stu-id="097dd-120">By providing explicit names, you avoid relying on the default ones.</span></span>  
  
- <span data-ttu-id="097dd-121">WCF çok morfik yöntemlerle işlemleri uygulama desteklemez, çünkü ASP.NET Web hizmet işlemleri çok morfik yöntemlerle uygulamayın.</span><span class="sxs-lookup"><span data-stu-id="097dd-121">Do not implement ASP.NET Web service operations with polymorphic methods, because WCF does not support implementing operations with polymorphic methods.</span></span>  
  
- <span data-ttu-id="097dd-122">SOAPAction <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute> HTTP üstbilgilerine, HTTP isteklerinin yöntemlere yönlendirileceği açık değerleri sağlamak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="097dd-122">Use the <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute> to provide explicit values for the SOAPAction HTTP headers by which HTTP requests will be routed to methods.</span></span>  
  
    ```csharp  
    [WebMethod]  
    [SoapDocumentMethod(RequestElementName="ExplicitAction")]  
    string Echo(string input);  
    ```  
  
     <span data-ttu-id="097dd-123">Bu yaklaşımın yanı, ASP.NET ve WCF tarafından kullanılan varsayılan SOAPAction değerlerinin aynı olmasına güvenmek zorunda kalmanın ardından gelecektir.</span><span class="sxs-lookup"><span data-stu-id="097dd-123">Taking this approach will circumvent having to rely on the default SOAPAction values used by ASP.NET and WCF being the same.</span></span>  
  
- <span data-ttu-id="097dd-124">SOAP uzantıları kullanmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="097dd-124">Avoid using SOAP extensions.</span></span> <span data-ttu-id="097dd-125">SOAP uzantıları gerekiyorsa, değerlendirilme amaçlarının WCF tarafından zaten sağlanan bir özellik olup olmadığını belirleyin.</span><span class="sxs-lookup"><span data-stu-id="097dd-125">If SOAP extensions are required, then determine whether the purpose for which they are being considered is a feature that is already provided by WCF.</span></span> <span data-ttu-id="097dd-126">Bu gerçekten durumda, o zaman hemen WCF benimsemek değil seçim yeniden düşünün.</span><span class="sxs-lookup"><span data-stu-id="097dd-126">If that is indeed the case, then reconsider the choice to not adopt WCF right away.</span></span>  
  
## <a name="state-management"></a><span data-ttu-id="097dd-127">Devlet Yönetimi</span><span class="sxs-lookup"><span data-stu-id="097dd-127">State Management</span></span>  
 <span data-ttu-id="097dd-128">Hizmetlerde durumu korumak zorunda kalmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="097dd-128">Avoid having to maintain state in services.</span></span> <span data-ttu-id="097dd-129">WCF ASP.NET uyumluluk modunda ASP.NET mekanizmaları desteklemesine rağmen, devletin korunması bir uygulamanın ölçeklenebilirliğinden ödün vermekle kalmıyor, aynı zamanda ASP.NET ve WCF'nin devlet yönetim mekanizmaları da çok farklıdır.</span><span class="sxs-lookup"><span data-stu-id="097dd-129">Not only does maintaining state tend to compromise the scalability of an application, but the state management mechanisms of ASP.NET and WCF are very different, although WCF does support the ASP.NET mechanisms in ASP.NET compatibility mode.</span></span>  
  
## <a name="exception-handling"></a><span data-ttu-id="097dd-130">Özel Durum İşleme</span><span class="sxs-lookup"><span data-stu-id="097dd-130">Exception Handling</span></span>  
 <span data-ttu-id="097dd-131">Bir hizmet tarafından gönderilecek ve alınacak veri türlerinin yapılarını tasarlarken, istemciye iletmek isteyebileceği bir hizmet içinde oluşabilecek çeşitli özel durum türlerini temsil edecek yapılar da tasarlar.</span><span class="sxs-lookup"><span data-stu-id="097dd-131">In designing the structures of the data types to be sent and received by a service, also design structures to represent the various types of exceptions that might occur within a service that one might wish to convey to a client.</span></span>  
  
```csharp  
[Serializable]  
[XmlRoot(Namespace="ExplicitNamespace", IsNullable=true)]  
public partial class AnticipatedException
{
    private string anticipatedExceptionInformationField;  

    public string AnticipatedExceptionInformation
    {  
        get {
            return this.anticipatedExceptionInformationField;  
        }  
        set {  
            this.anticipatedExceptionInformationField = value;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="097dd-132">Bu tür sınıflara kendilerini XML'e serileştirme olanağı verin:</span><span class="sxs-lookup"><span data-stu-id="097dd-132">Give such classes the ability to serialize themselves to XML:</span></span>  
  
```csharp  
public XmlNode ToXML()  
{  
     XmlSerializer serializer = new XmlSerializer(  
      typeof(AnticipatedException));  
     MemoryStream memoryStream = new MemoryStream();  
     XmlTextWriter writer = new XmlTextWriter(  
     memoryStream, UnicodeEncoding.UTF8);  
     serializer.Serialize(writer, this);  
     XmlDocument document = new XmlDocument();  
     document.LoadXml(new string(  
     UnicodeEncoding.UTF8.GetChars(  
     memoryStream.GetBuffer())).Trim());  
    return document.DocumentElement;  
}  
```  
  
 <span data-ttu-id="097dd-133">Sınıflar daha sonra açıkça atılan <xref:System.Web.Services.Protocols.SoapException> örnekler için ayrıntıları sağlamak için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="097dd-133">The classes can then be used to provide the details for explicitly thrown <xref:System.Web.Services.Protocols.SoapException> instances:</span></span>  
  
```csharp  
AnticipatedException exception = new AnticipatedException();  
exception.AnticipatedExceptionInformation = "…";  
throw new SoapException(  
     "Fault occurred",  
     SoapException.ClientFaultCode,  
     Context.Request.Url.AbsoluteUri,  
     exception.ToXML());  
```  
  
 <span data-ttu-id="097dd-134">Bu özel durum sınıfları, WCF <xref:System.ServiceModel.FaultException%601> sınıfı yla kolayca yeniden kullanılabilir hale gelir ve yeni bir`FaultException<AnticipatedException>(anticipatedException);`</span><span class="sxs-lookup"><span data-stu-id="097dd-134">These exception classes will be readily reusable with the WCF <xref:System.ServiceModel.FaultException%601> class to throw a new `FaultException<AnticipatedException>(anticipatedException);`</span></span>  
  
## <a name="security"></a><span data-ttu-id="097dd-135">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="097dd-135">Security</span></span>  
 <span data-ttu-id="097dd-136">Aşağıda bazı güvenlik önerileri veremeleri yer alıyor.</span><span class="sxs-lookup"><span data-stu-id="097dd-136">The following are some security recommendations.</span></span>  
  
- <span data-ttu-id="097dd-137">Hizmet WCF'ye geçirilmişse, 2.0 Profillerini ASP.NET kullanmaktan kaçının, çünkü bunları kullanmak ASP.NET Tümleştirme Modu'nun kullanımını kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="097dd-137">Avoid using ASP.NET 2.0 Profiles, as using them would restrict the use of ASP.NET Integration Mode if the service was migrated to WCF.</span></span>  
  
- <span data-ttu-id="097dd-138">ASP.NET Web hizmetleri Internet Information Services (IIS) kullanarak ALA'ları desteklediği için, hizmetlere erişimi denetlemek için ALA'lar kullanmaktan kaçının, çünkü ASP.NET Web hizmetleri barındırma için IIS'ye bağlıdır ve WCF'nin IIS'de barındırılması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="097dd-138">Avoid using ACLs to control access to services, as ASP.NET Web services supports ACLs using Internet Information Services (IIS), WCF does not—because ASP.NET Web services depend on IIS for hosting, and WCF does not necessarily have to be hosted in IIS.</span></span>  
  
- <span data-ttu-id="097dd-139">Bir hizmetin kaynaklarına erişim yetkisi vermek için ASP.NET 2.0 Rol Sağlayıcıları kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="097dd-139">Do consider using ASP.NET 2.0 Role Providers for authorizing access to the resources of a service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="097dd-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="097dd-140">See also</span></span>

- [<span data-ttu-id="097dd-141">Windows Communication Foundation'ı Benimsemeyi Bekleme: Gelecekteki Tümleştirmeyi Kolaylaştırma</span><span class="sxs-lookup"><span data-stu-id="097dd-141">Anticipating Adopting the Windows Communication Foundation: Easing Future Integration</span></span>](../../../../docs/framework/wcf/feature-details/anticipating-adopting-the-wcf-easing-future-integration.md)
