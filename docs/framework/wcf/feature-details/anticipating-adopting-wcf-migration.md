---
title: "Windows Communication Foundation'ı Benimsemeyi Bekleme: Gelecekteki Geçişi Kolaylaştırma"
ms.date: 03/30/2017
ms.assetid: f49664d9-e9e0-425c-a259-93f0a569d01b
ms.openlocfilehash: 4492626c2cb0958f8aa79fa2b511d9aa9e90b16a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59176390"
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-migration"></a><span data-ttu-id="9832e-102">Windows Communication Foundation'ı Benimsemeyi Bekleme: Gelecekteki Geçişi Kolaylaştırma</span><span class="sxs-lookup"><span data-stu-id="9832e-102">Anticipating Adopting the Windows Communication Foundation: Easing Future Migration</span></span>
<span data-ttu-id="9832e-103">Yeni ASP.NET uygulamalarını wcf'ye TAŞIMA daha kolay gelecekteki geçişini sağlamak için yukarıdaki öneriler ve bunun yanı sıra aşağıdaki önerileri uygulayın.</span><span class="sxs-lookup"><span data-stu-id="9832e-103">To ensure an easier future migration of new ASP.NET applications to WCF, follow the preceding recommendations as well as the following recommendations.</span></span>  
  
## <a name="protocols"></a><span data-ttu-id="9832e-104">Protokolleri</span><span class="sxs-lookup"><span data-stu-id="9832e-104">Protocols</span></span>  
 <span data-ttu-id="9832e-105">ASP.NET 2.0'ın SOAP 1.2 desteği devre dışı bırakın:</span><span class="sxs-lookup"><span data-stu-id="9832e-105">Disable ASP.NET 2.0’s support for SOAP 1.2:</span></span>  
  
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
  
 <span data-ttu-id="9832e-106">WCF SOAP 1.1 ve SOAP 1.2 gibi farklı protokollere uyumludur iletileri farklı uç noktaları kullanarak Git gerektirdiğinden Bunun yapılması önerilir.</span><span class="sxs-lookup"><span data-stu-id="9832e-106">Doing so is advisable because WCF requires messages conforming to different protocols, like SOAP 1.1 and SOAP 1.2, to go by using different endpoints.</span></span> <span data-ttu-id="9832e-107">ASP.NET 2.0 Web hizmeti SOAP 1.1 hem olamaz sonra varsayılan yapılandırma, SOAP 1.2 desteklemek üzere yapılandırılmış tek bir WCF uç noktasına kesinlikle olabilecek özgün adresten İleri geçirdiyseniz, tüm ASP.NET Web ile uyumlu olacak hizmetin mevcut istemciler.</span><span class="sxs-lookup"><span data-stu-id="9832e-107">If an ASP.NET 2.0 Web service is configured to support both SOAP 1.1 and SOAP 1.2, which is the default configuration, then it cannot be migrated forward to a single WCF endpoint at the original address that would be certainly be compatible with all of the ASP.NET Web service’s existing clients.</span></span> <span data-ttu-id="9832e-108">Ayrıca 1.1 yerine SOAP 1.2 seçme clientele hizmetinin daha ciddi bir şekilde kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="9832e-108">Also choosing SOAP 1.2 instead of 1.1 will more severely restrict the clientele of the service.</span></span>  
  
## <a name="service-development"></a><span data-ttu-id="9832e-109">Hizmet geliştirme</span><span class="sxs-lookup"><span data-stu-id="9832e-109">Service Development</span></span>  
 <span data-ttu-id="9832e-110">WCF hizmet sözleşmelerini uygulayarak tanımlamanıza izin verir <xref:System.ServiceModel.ServiceContractAttribute> arabirimleri veya sınıflar.</span><span class="sxs-lookup"><span data-stu-id="9832e-110">WCF allows you to define service contracts by applying the <xref:System.ServiceModel.ServiceContractAttribute> either to interfaces or to classes.</span></span> <span data-ttu-id="9832e-111">Bunun yapılması, bu nedenle herhangi bir sayıda sınıfları teknolojiye uygulanabilir bir sözleşme tanımı oluşturur çünkü bir arabirim yerine bir sınıf özniteliği uygulamak için önerilir.</span><span class="sxs-lookup"><span data-stu-id="9832e-111">It is recommended to apply the attribute to an interface rather than to a class, because doing so creates a definition of a contract that can be variously implemented by any number of classes.</span></span> <span data-ttu-id="9832e-112">ASP.NET 2.0 uygulama seçeneğini destekler <xref:System.Web.Services.WebService> öznitelik sınıflarının yanı sıra arabirimleri.</span><span class="sxs-lookup"><span data-stu-id="9832e-112">ASP.NET 2.0 supports the option of applying the <xref:System.Web.Services.WebService> attribute to interfaces as well as classes.</span></span> <span data-ttu-id="9832e-113">Ancak, önceden belirtildiği gibi yoktur, ASP.NET 2. 0'da, bir hata Namespace parametresi <xref:System.Web.Services.WebService> özniteliği bu öznitelik, bir sınıf yerine bir arabirim uygulandığında hiçbir etkiye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="9832e-113">However, as mentioned already, there is a defect in ASP.NET 2.0, by which the Namespace parameter of the <xref:System.Web.Services.WebService> attribute has no effect when that attribute is applied to an interface rather than a class.</span></span> <span data-ttu-id="9832e-114">Varsayılan değer, bir hizmet ad alanı değiştirmek için genellikle tavsiye olduğundan `http://tempuri.org`, Namespace parametresini kullanarak <xref:System.Web.Services.WebService> öznitelik, bir çalışmaya devam ASP.NET Web hizmetlerini uygulayarak tanımlama <xref:System.ServiceModel.ServiceContractAttribute> arabirimleri veya Sınıf özniteliği.</span><span class="sxs-lookup"><span data-stu-id="9832e-114">Since it is generally advisable to modify the namespace of a service from the default value, `http://tempuri.org`, using the Namespace parameter of the <xref:System.Web.Services.WebService> attribute, one should continue defining ASP.NET Web Services by applying the <xref:System.ServiceModel.ServiceContractAttribute> attribute either to interfaces or to classes.</span></span>  
  
-   <span data-ttu-id="9832e-115">Bu arabirimleri tarafından tanımlanan yöntemler olabildiğince küçük kod sahip.</span><span class="sxs-lookup"><span data-stu-id="9832e-115">Have as little code as possible in the methods by which those interfaces are defined.</span></span> <span data-ttu-id="9832e-116">Çalışmalarını diğer sınıflar için temsilci sağlayın.</span><span class="sxs-lookup"><span data-stu-id="9832e-116">Have them delegate their work to other classes.</span></span> <span data-ttu-id="9832e-117">Yeni bir WCF Hizmeti türleri, bu sınıfların substantive işlerini de atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9832e-117">New WCF service types could then also delegate their substantive work to those classes.</span></span>  
  
-   <span data-ttu-id="9832e-118">Kullanarak bir hizmet işlemleri için açık adlar sağlayan `MessageName` parametresinin <xref:System.Web.Services.WebMethodAttribute>.</span><span class="sxs-lookup"><span data-stu-id="9832e-118">Provide explicit names for the operations of a service using the `MessageName` parameter of the <xref:System.Web.Services.WebMethodAttribute>.</span></span>  
  
    ```csharp  
    [WebMethod(MessageName="ExplicitName")]  
    string Echo(string input);  
    ```  
  
     <span data-ttu-id="9832e-119">ASP.NET'te işlemleri için varsayılan adlar WCF tarafından sağlanan varsayılan adları farklı olduğundan Bunun yapılması önemlidir.</span><span class="sxs-lookup"><span data-stu-id="9832e-119">Doing so is important, because the default names for operations in ASP.NET are different from the default names supplied by WCF.</span></span> <span data-ttu-id="9832e-120">Açık bir ad sağlayarak, varsayılan değerleri bağlı olan kaçının.</span><span class="sxs-lookup"><span data-stu-id="9832e-120">By providing explicit names, you avoid relying on the default ones.</span></span>  
  
-   <span data-ttu-id="9832e-121">WCF polimorfik yöntemlerle uygulama işlemlerini desteklemediğinden, ASP.NET Web hizmeti işlemleri çok biçimli yöntemleriyle kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="9832e-121">Do not implement ASP.NET Web service operations with polymorphic methods, because WCF does not support implementing operations with polymorphic methods.</span></span>  
  
-   <span data-ttu-id="9832e-122">Kullanım <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute> açık değerler tarafından hangi HTTP isteklerinin yöntemlere yönlendirilecek SOAPAction HTTP üst bilgilerini sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="9832e-122">Use the <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute> to provide explicit values for the SOAPAction HTTP headers by which HTTP requests will be routed to methods.</span></span>  
  
    ```csharp  
    [WebMethod]  
    [SoapDocumentMethod(RequestElementName="ExplicitAction")]  
    string Echo(string input);  
    ```  
  
     <span data-ttu-id="9832e-123">Bu yaklaşımı, varsayılan ASP.NET ve WCF aynı anda tarafından kullanılan SOAPAction değerleri kullanan gerek kalmadan aşmak.</span><span class="sxs-lookup"><span data-stu-id="9832e-123">Taking this approach will circumvent having to rely on the default SOAPAction values used by ASP.NET and WCF being the same.</span></span>  
  
-   <span data-ttu-id="9832e-124">SOAP uzantıları kullanmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="9832e-124">Avoid using SOAP extensions.</span></span> <span data-ttu-id="9832e-125">SOAP uzantıları gerekiyorsa, bunlar kabul amacı zaten WCF tarafından sağlanan bir özellik olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="9832e-125">If SOAP extensions are required, then determine whether the purpose for which they are being considered is a feature that is already provided by WCF.</span></span> <span data-ttu-id="9832e-126">Ardından, aslında durumda, WCF hemen benimsemeye değil seçimi yeniden gözden geçir.</span><span class="sxs-lookup"><span data-stu-id="9832e-126">If that is indeed the case, then reconsider the choice to not adopt WCF right away.</span></span>  
  
## <a name="state-management"></a><span data-ttu-id="9832e-127">Durum Yönetimi</span><span class="sxs-lookup"><span data-stu-id="9832e-127">State Management</span></span>  
 <span data-ttu-id="9832e-128">Hizmetleri'nde durumunu korumak üzere yapmamaya</span><span class="sxs-lookup"><span data-stu-id="9832e-128">Avoid having to maintain state in services.</span></span> <span data-ttu-id="9832e-129">Yalnızca durum koruma uygulamasının ölçeklenebilirliğini aşmaya eğilimli yapar, ancak WCF ASP.NET mekanizmaları ASP.NET uyumluluk modunda desteklese de ASP.NET ve WCF durumu yönetim sistemleri çok farklı.</span><span class="sxs-lookup"><span data-stu-id="9832e-129">Not only does maintaining state tend to compromise the scalability of an application, but the state management mechanisms of ASP.NET and WCF are very different, although WCF does support the ASP.NET mechanisms in ASP.NET compatibility mode.</span></span>  
  
## <a name="exception-handling"></a><span data-ttu-id="9832e-130">Özel Durum İşleme</span><span class="sxs-lookup"><span data-stu-id="9832e-130">Exception Handling</span></span>  
 <span data-ttu-id="9832e-131">Gönderilen ve alınan bir hizmet tarafından aktarılacak veri türlerini yapıları tasarlarken, ayrıca tek bir hizmet içinde oluşabilecek özel durumları çeşitli türlerini temsil etmek için tasarım yapıları istemciye iletmek isteyebilir.</span><span class="sxs-lookup"><span data-stu-id="9832e-131">In designing the structures of the data types to be sent and received by a service, also design structures to represent the various types of exceptions that might occur within a service that one might wish to convey to a client.</span></span>  
  
```csharp  
[Serializable]  
[XmlRoot(  
     Namespace="ExplicitNamespace", IsNullable=true)]  
    public partial class AnticipatedException {  
  
     private string anticipatedExceptionInformationField;  
  
     public string AnticipatedExceptionInformation {  
      get {  
          return this.anticipatedExceptionInformationField;  
          }  
      set {  
          this.anticipatedExceptionInformationField = value;  
          }  
     }  
}  
```  
  
 <span data-ttu-id="9832e-132">Bu tür sınıflar kendileri için XML seri hale getirme olanağı sağlar:</span><span class="sxs-lookup"><span data-stu-id="9832e-132">Give such classes the ability to serialize themselves to XML:</span></span>  
  
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
  
 <span data-ttu-id="9832e-133">Sınıflar için açıkça durum ayrıntılarını sağlamak için daha sonra kullanılabilir <xref:System.Web.Services.Protocols.SoapException> örnekleri:</span><span class="sxs-lookup"><span data-stu-id="9832e-133">The classes can then be used to provide the details for explicitly thrown <xref:System.Web.Services.Protocols.SoapException> instances:</span></span>  
  
```csharp  
AnctipatedException exception = new AnticipatedException();  
exception.AnticipatedExceptionInformation = "…";  
throw new SoapException(  
     "Fault occurred",  
     SoapException.ClientFaultCode,  
     Context.Request.Url.AbsoluteUri,  
     exception.ToXML());  
```  
  
 <span data-ttu-id="9832e-134">Bu özel durum sınıfları WCF ile kolayca yeniden kullanılabilir olacaktır <xref:System.ServiceModel.FaultException%601> sınıfının yeni bir `FaultException<AnticipatedException>(anticipatedException);`</span><span class="sxs-lookup"><span data-stu-id="9832e-134">These exception classes will be readily reusable with the WCF <xref:System.ServiceModel.FaultException%601> class to throw a new `FaultException<AnticipatedException>(anticipatedException);`</span></span>  
  
## <a name="security"></a><span data-ttu-id="9832e-135">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="9832e-135">Security</span></span>  
 <span data-ttu-id="9832e-136">Bazı güvenlik önerileri aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="9832e-136">The following are some security recommendations.</span></span>  
  
-   <span data-ttu-id="9832e-137">Önlemek ASP.NET 2.0 profilleri kullanarak olarak sınırlandıracak ASP.NET tümleştirme modu kullanımını hizmet WCF'ye geçirdiyseniz.</span><span class="sxs-lookup"><span data-stu-id="9832e-137">Avoid using ASP.NET 2.0 Profiles, as using them would restrict the use of ASP.NET Integration Mode if the service was migrated to WCF.</span></span>  
  
-   <span data-ttu-id="9832e-138">ASP.NET Web Hizmetleri Internet Information Services (IIS) kullanarak ACL'leri destekler, hizmetlere erişimi denetlemek için ACL'leri kullanmaktan kaçının, WCF desteklemez; çünkü ASP.NET Web hizmetlerini barındırmak için IIS üzerinde bağlıdır ve WCF gerekmeyen gerekmez IIS'de barındırılan.</span><span class="sxs-lookup"><span data-stu-id="9832e-138">Avoid using ACLs to control access to services, as ASP.NET Web services supports ACLs using Internet Information Services (IIS), WCF does not—because ASP.NET Web services depend on IIS for hosting, and WCF does not necessarily have to be hosted in IIS.</span></span>  
  
-   <span data-ttu-id="9832e-139">Bir hizmetin kaynaklara erişim yetkisi vermek için ASP.NET 2.0 rol sağlayıcıları kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="9832e-139">Do consider using ASP.NET 2.0 Role Providers for authorizing access to the resources of a service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9832e-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9832e-140">See also</span></span>

- [<span data-ttu-id="9832e-141">Windows Communication Foundation'ı benimsemeyi bekleme: Gelecekteki tümleştirmeyi kolaylaştırma</span><span class="sxs-lookup"><span data-stu-id="9832e-141">Anticipating Adopting the Windows Communication Foundation: Easing Future Integration</span></span>](../../../../docs/framework/wcf/feature-details/anticipating-adopting-the-wcf-easing-future-integration.md)
