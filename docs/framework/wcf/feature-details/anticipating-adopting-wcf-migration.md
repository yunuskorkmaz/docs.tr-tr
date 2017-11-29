---
title: "Windows Communication Foundation'ı Benimsemeyi Bekleme: Gelecekteki Taşınmayı Kolaylaştırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f49664d9-e9e0-425c-a259-93f0a569d01b
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 375274cd1b67b6dc71d3e66e1c1f063a81db7d8e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-migration"></a><span data-ttu-id="10043-102">Windows Communication Foundation'ı Benimsemeyi Bekleme: Gelecekteki Taşınmayı Kolaylaştırma</span><span class="sxs-lookup"><span data-stu-id="10043-102">Anticipating Adopting the Windows Communication Foundation: Easing Future Migration</span></span>
<span data-ttu-id="10043-103">Yeni ASP.NET uygulamaları için daha kolay gelecekteki geçişini sağlamak için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], yukarıdaki öneriler ve bunun yanı sıra aşağıdaki önerileri uygulayın.</span><span class="sxs-lookup"><span data-stu-id="10043-103">To ensure an easier future migration of new ASP.NET applications to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], follow the preceding recommendations as well as the following recommendations.</span></span>  
  
## <a name="protocols"></a><span data-ttu-id="10043-104">protokolleri</span><span class="sxs-lookup"><span data-stu-id="10043-104">Protocols</span></span>  
 <span data-ttu-id="10043-105">SOAP 1.2 ASP.NET 2.0'in desteğini devre dışı bırakın:</span><span class="sxs-lookup"><span data-stu-id="10043-105">Disable ASP.NET 2.0’s support for SOAP 1.2:</span></span>  
  
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
  
 <span data-ttu-id="10043-106">Bunun yapılması önerilir çünkü [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] farklı uç noktalar kullanarak Git iletileri SOAP 1.1 ve SOAP 1.2 gibi farklı protokollere uyumludur gerektirir.</span><span class="sxs-lookup"><span data-stu-id="10043-106">Doing so is advisable because [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] requires messages conforming to different protocols, like SOAP 1.1 and SOAP 1.2, to go by using different endpoints.</span></span> <span data-ttu-id="10043-107">Bir ASP.NET 2.0 Web hizmeti SOAP 1.1 ve SOAP 1.2, varsayılan yapılandırmadır desteklemek üzere yapılandırıldığı sonra İleri tek bir geçirilemez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uç nokta olacak özgün adresinde kesinlikle tüm ASP ile uyumlu .NET web Service'in mevcut istemciler.</span><span class="sxs-lookup"><span data-stu-id="10043-107">If an ASP.NET 2.0 Web service is configured to support both SOAP 1.1 and SOAP 1.2, which is the default configuration, then it cannot be migrated forward to a single [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint at the original address that would be certainly be compatible with all of the ASP.NET Web service’s existing clients.</span></span> <span data-ttu-id="10043-108">Ayrıca 1.1 yerine SOAP 1.2 seçme hizmet clientele daha ciddi bir şekilde kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="10043-108">Also choosing SOAP 1.2 instead of 1.1 will more severely restrict the clientele of the service.</span></span>  
  
## <a name="service-development"></a><span data-ttu-id="10043-109">Hizmet geliştirme</span><span class="sxs-lookup"><span data-stu-id="10043-109">Service Development</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="10043-110">Hizmet sözleşmeleri uygulayarak tanımlamanıza olanak verir <xref:System.ServiceModel.ServiceContractAttribute> arabirimleri ya sınıfları sağlar.</span><span class="sxs-lookup"><span data-stu-id="10043-110"> allows you to define service contracts by applying the <xref:System.ServiceModel.ServiceContractAttribute> either to interfaces or to classes.</span></span> <span data-ttu-id="10043-111">Bunu yaptığınızda bu nedenle herhangi bir sayıda sınıfları teknolojiye uygulanabileceği bir sözleşme tanımının oluşturduğundan arabirime yerine bir sınıfa öznitelik uygulamak için önerilir.</span><span class="sxs-lookup"><span data-stu-id="10043-111">It is recommended to apply the attribute to an interface rather than to a class, because doing so creates a definition of a contract that can be variously implemented by any number of classes.</span></span> <span data-ttu-id="10043-112">ASP.NET 2.0 destekler, uygulamanın seçeneği <xref:System.Web.Services.WebService> öznitelik sınıfları yanı sıra arabirimleri.</span><span class="sxs-lookup"><span data-stu-id="10043-112">ASP.NET 2.0 supports the option of applying the <xref:System.Web.Services.WebService> attribute to interfaces as well as classes.</span></span> <span data-ttu-id="10043-113">Ancak, önceden belirtildiği gibi yok ASP.NET 2. 0'da, bir üründe, Namespace parametresinin <xref:System.Web.Services.WebService> özniteliği hiçbir etkisi bu özniteliği bir sınıf yerine bir arabirim uygulandığında.</span><span class="sxs-lookup"><span data-stu-id="10043-113">However, as mentioned already, there is a defect in ASP.NET 2.0, by which the Namespace parameter of the <xref:System.Web.Services.WebService> attribute has no effect when that attribute is applied to an interface rather than a class.</span></span> <span data-ttu-id="10043-114">Sonra varsayılan değerden http://tempuri.org, Namespace parametresini kullanarak bir hizmet ad alanı değiştirmek için genellikle önerilir <xref:System.Web.Services.WebService> öznitelik, bir devam etmelidir ASP.NET Web Hizmetleri uygulayarak tanımlama <xref:System.ServiceModel.ServiceContractAttribute> arabirimleri veya sınıfları özniteliği.</span><span class="sxs-lookup"><span data-stu-id="10043-114">Since it is generally advisable to modify the namespace of a service from the default value, http://tempuri.org, using the Namespace parameter of the <xref:System.Web.Services.WebService> attribute, one should continue defining ASP.NET Web Services by applying the <xref:System.ServiceModel.ServiceContractAttribute> attribute either to interfaces or to classes.</span></span>  
  
-   <span data-ttu-id="10043-115">Bu arabirimleri tanımlanan yöntemler mümkün olduğunca küçük koda sahip.</span><span class="sxs-lookup"><span data-stu-id="10043-115">Have as little code as possible in the methods by which those interfaces are defined.</span></span> <span data-ttu-id="10043-116">İşlerini başka sınıfların temsilci sağlayın.</span><span class="sxs-lookup"><span data-stu-id="10043-116">Have them delegate their work to other classes.</span></span> <span data-ttu-id="10043-117">Yeni [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet türleri sonra ayrıca temsilci bu sınıfların substantive iş.</span><span class="sxs-lookup"><span data-stu-id="10043-117">New [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service types could then also delegate their substantive work to those classes.</span></span>  
  
-   <span data-ttu-id="10043-118">Kullanarak hizmet işlemleri için açık adlar sağlayan `MessageName` parametresinin <xref:System.Web.Services.WebMethodAttribute>.</span><span class="sxs-lookup"><span data-stu-id="10043-118">Provide explicit names for the operations of a service using the `MessageName` parameter of the <xref:System.Web.Services.WebMethodAttribute>.</span></span>  
  
    ```  
    [WebMethod(MessageName="ExplicitName")]  
    string Echo(string input);  
    ```  
  
     <span data-ttu-id="10043-119">Bunun yapılması önemlidir, ASP.NET işlemleri için varsayılan adlar tarafından sağlanan varsayılan adlarından farklı olduğundan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="10043-119">Doing so is important, because the default names for operations in ASP.NET are different from the default names supplied by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="10043-120">Açık adları sağlayarak, varsayılan değerleri bağlı kaçının.</span><span class="sxs-lookup"><span data-stu-id="10043-120">By providing explicit names, you avoid relying on the default ones.</span></span>  
  
-   <span data-ttu-id="10043-121">ASP.NET Web hizmeti işlemleri çok biçimli yöntemleriyle çünkü kullanılmaz [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] biçimli yöntemleriyle uygulama işlemlerini desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="10043-121">Do not implement ASP.NET Web service operations with polymorphic methods, because [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not support implementing operations with polymorphic methods.</span></span>  
  
-   <span data-ttu-id="10043-122">Kullanım <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute> tarafından hangi HTTP isteklerinin yöntemlere yönlendirilecek SOAPAction HTTP üstbilgilerinin açık değerlerini sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="10043-122">Use the <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute> to provide explicit values for the SOAPAction HTTP headers by which HTTP requests will be routed to methods.</span></span>  
  
    ```  
    [WebMethod]  
    [SoapDocumentMethod(RequestElementName="ExplicitAction")]  
    string Echo(string input);  
    ```  
  
     <span data-ttu-id="10043-123">Bu yaklaşımı aşmak SOAPAction değerleri ASP.NET tarafından kullanılan varsayılan yararlanmayı sahip ve [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aynı anda.</span><span class="sxs-lookup"><span data-stu-id="10043-123">Taking this approach will circumvent having to rely on the default SOAPAction values used by ASP.NET and [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] being the same.</span></span>  
  
-   <span data-ttu-id="10043-124">SOAP uzantılarını kullanmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="10043-124">Avoid using SOAP extensions.</span></span> <span data-ttu-id="10043-125">SOAP uzantılarını gerekirse, ardından, bunlar olarak kabul edilir amacı tarafından sağlanan bir özellik olup olmadığını [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="10043-125">If SOAP extensions are required, then determine whether the purpose for which they are being considered is a feature that is already provided by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="10043-126">Gerçekten durumda değil benimsemeyi seçimi alan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hemen.</span><span class="sxs-lookup"><span data-stu-id="10043-126">If that is indeed the case, then reconsider the choice to not adopt [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] right away.</span></span>  
  
## <a name="state-management"></a><span data-ttu-id="10043-127">Durum Yönetimi</span><span class="sxs-lookup"><span data-stu-id="10043-127">State Management</span></span>  
 <span data-ttu-id="10043-128">Hizmetleri'ndeki durumunu korumak üzere olmamasına özen gösterin.</span><span class="sxs-lookup"><span data-stu-id="10043-128">Avoid having to maintain state in services.</span></span> <span data-ttu-id="10043-129">Yalnızca durum koruma uygulama ölçeklenebilirlik ancak ASP.NET durum yönetimi mekanizmaları tehlikeye eğilimindedir ve [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] çok farklı olan ancak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ASP.NET ASP.NET uyumluluğu mekanizmaları modu.</span><span class="sxs-lookup"><span data-stu-id="10043-129">Not only does maintaining state tend to compromise the scalability of an application, but the state management mechanisms of ASP.NET and [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] are very different, although [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does support the ASP.NET mechanisms in ASP.NET compatibility mode.</span></span>  
  
## <a name="exception-handling"></a><span data-ttu-id="10043-130">Özel Durum İşleme</span><span class="sxs-lookup"><span data-stu-id="10043-130">Exception Handling</span></span>  
 <span data-ttu-id="10043-131">Gönderilen ve hizmeti tarafından alınan veri türlerinin yapıları tasarlarken, ayrıca bir hizmet içinde oluşabilir ve bir özel durum çeşitli türlerde temsil etmek için tasarım yapıları istemciye iletmek isteyebilir.</span><span class="sxs-lookup"><span data-stu-id="10043-131">In designing the structures of the data types to be sent and received by a service, also design structures to represent the various types of exceptions that might occur within a service that one might wish to convey to a client.</span></span>  
  
```  
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
  
 <span data-ttu-id="10043-132">Bu tür sınıflar kendileri için XML serileştirme olanağı verir:</span><span class="sxs-lookup"><span data-stu-id="10043-132">Give such classes the ability to serialize themselves to XML:</span></span>  
  
```  
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
  
 <span data-ttu-id="10043-133">Sınıflar sonra açıkça durum için ayrıntılarını sağlamak için kullanılabilir <xref:System.Web.Services.Protocols.SoapException> örnekleri:</span><span class="sxs-lookup"><span data-stu-id="10043-133">The classes can then be used to provide the details for explicitly thrown <xref:System.Web.Services.Protocols.SoapException> instances:</span></span>  
  
```  
AnctipatedException exception = new AnticipatedException();  
exception.AnticipatedExceptionInformation = "…";  
throw new SoapException(  
     "Fault occurred",  
     SoapException.ClientFaultCode,  
     Context.Request.Url.AbsoluteUri,  
     exception.ToXML());  
```  
  
 <span data-ttu-id="10043-134">Bu özel durum sınıfları ile kolayca yeniden kullanılabilir[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] <xref:System.ServiceModel.FaultException%601> yeni bir özel durum sınıfı`FaultException<AnticipatedException>(anticipatedException);`</span><span class="sxs-lookup"><span data-stu-id="10043-134">These exception classes will be readily reusable with the[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<xref:System.ServiceModel.FaultException%601> class to throw a new `FaultException<AnticipatedException>(anticipatedException);`</span></span>  
  
## <a name="security"></a><span data-ttu-id="10043-135">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="10043-135">Security</span></span>  
 <span data-ttu-id="10043-136">Bazı güvenlik önerileri verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="10043-136">The following are some security recommendations.</span></span>  
  
-   <span data-ttu-id="10043-137">Kaçının kullanarak olarak ASP.NET 2.0 profillerini kullanarak kısıtlamak ASP.NET tümleştirme modu kullanmak için hizmet geçirildiyse [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="10043-137">Avoid using ASP.NET 2.0 Profiles, as using them would restrict the use of ASP.NET Integration Mode if the service was migrated to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
-   <span data-ttu-id="10043-138">ASP.NET Web hizmetlerini destekleyen olarak Internet Information Services (IIS) kullanarak ACL'ler hizmetlerine erişimi denetlemek için ACL kullanmaktan kaçının [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] yok; çünkü ASP.NET Web hizmetlerini barındırmak için IIS üzerinde bağlı ve WCF mutlaka yok IIS'de barındırılması.</span><span class="sxs-lookup"><span data-stu-id="10043-138">Avoid using ACLs to control access to services, as ASP.NET Web services supports ACLs using Internet Information Services (IIS), [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not—because ASP.NET Web services depend on IIS for hosting, and WCF does not necessarily have to be hosted in IIS.</span></span>  
  
-   <span data-ttu-id="10043-139">Bir hizmet kaynaklara erişim yetkisi vermek için ASP.NET 2.0 rol sağlayıcıları kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="10043-139">Do consider using ASP.NET 2.0 Role Providers for authorizing access to the resources of a service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10043-140">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="10043-140">See Also</span></span>  
 [<span data-ttu-id="10043-141">Windows Communication Foundation'ı benimsemeyi bekleme: gelecekteki tümleştirmeyi kolaylaştırma</span><span class="sxs-lookup"><span data-stu-id="10043-141">Anticipating Adopting the Windows Communication Foundation: Easing Future Integration</span></span>](../../../../docs/framework/wcf/feature-details/anticipating-adopting-the-wcf-easing-future-integration.md)
