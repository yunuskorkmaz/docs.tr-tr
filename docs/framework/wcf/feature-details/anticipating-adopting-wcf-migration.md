---
title: "Windows Communication Foundation'ı Benimsemeyi Bekleme: Gelecekteki Taşınmayı Kolaylaştırma"
ms.date: 03/30/2017
ms.assetid: f49664d9-e9e0-425c-a259-93f0a569d01b
ms.openlocfilehash: b43f509bd49ebe89d7ed0be4c37b3ed179aaeb8c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84576505"
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-migration"></a><span data-ttu-id="f4d66-102">Windows Communication Foundation'ı Benimsemeyi Bekleme: Gelecekteki Taşınmayı Kolaylaştırma</span><span class="sxs-lookup"><span data-stu-id="f4d66-102">Anticipating Adopting the Windows Communication Foundation: Easing Future Migration</span></span>
<span data-ttu-id="f4d66-103">Yeni ASP.NET uygulamalarının WCF 'ye daha kolay bir şekilde geçişini sağlamak için, önceki önerilere ve aşağıdaki önerilere uyun.</span><span class="sxs-lookup"><span data-stu-id="f4d66-103">To ensure an easier future migration of new ASP.NET applications to WCF, follow the preceding recommendations as well as the following recommendations.</span></span>  
  
## <a name="protocols"></a><span data-ttu-id="f4d66-104">Protokoller</span><span class="sxs-lookup"><span data-stu-id="f4d66-104">Protocols</span></span>  
 <span data-ttu-id="f4d66-105">SOAP 1,2 için ASP.NET 2.0 desteğini devre dışı bırakın:</span><span class="sxs-lookup"><span data-stu-id="f4d66-105">Disable ASP.NET 2.0’s support for SOAP 1.2:</span></span>  
  
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
  
 <span data-ttu-id="f4d66-106">WCF, SOAP 1,1 ve SOAP 1,2 gibi farklı protokollerle uyumlu iletiler gerektirdiğinden farklı uç noktalar kullanarak devam etmek önerilir.</span><span class="sxs-lookup"><span data-stu-id="f4d66-106">Doing so is advisable because WCF requires messages conforming to different protocols, like SOAP 1.1 and SOAP 1.2, to go by using different endpoints.</span></span> <span data-ttu-id="f4d66-107">Bir ASP.NET 2,0 Web hizmeti, varsayılan yapılandırma olan hem SOAP 1,1 hem de SOAP 1,2 'ı destekleyecek şekilde yapılandırıldıysa, özgün adresteki tüm ASP.NET Web hizmeti 'nin mevcut istemcileriyle uyumlu olacak şekilde tek bir WCF uç noktasına geçiş yapılamaz.</span><span class="sxs-lookup"><span data-stu-id="f4d66-107">If an ASP.NET 2.0 Web service is configured to support both SOAP 1.1 and SOAP 1.2, which is the default configuration, then it cannot be migrated forward to a single WCF endpoint at the original address that would be certainly be compatible with all of the ASP.NET Web service’s existing clients.</span></span> <span data-ttu-id="f4d66-108">Ayrıca, 1,2 1,1 yerine SOAP ' i seçtiğinizde hizmetin Clientele daha ciddi bir şekilde kısıtlanacaktır.</span><span class="sxs-lookup"><span data-stu-id="f4d66-108">Also choosing SOAP 1.2 instead of 1.1 will more severely restrict the clientele of the service.</span></span>  
  
## <a name="service-development"></a><span data-ttu-id="f4d66-109">Hizmet geliştirme</span><span class="sxs-lookup"><span data-stu-id="f4d66-109">Service Development</span></span>  
 <span data-ttu-id="f4d66-110">WCF, arabirimleri veya sınıfları uygulayarak hizmet sözleşmeleri tanımlamanızı sağlar <xref:System.ServiceModel.ServiceContractAttribute> .</span><span class="sxs-lookup"><span data-stu-id="f4d66-110">WCF allows you to define service contracts by applying the <xref:System.ServiceModel.ServiceContractAttribute> either to interfaces or to classes.</span></span> <span data-ttu-id="f4d66-111">Özniteliği, bir sınıf yerine bir arabirime uygulamanız önerilir, çünkü bunu yapmak, herhangi bir sayıda sınıf tarafından variously uygulanabilecek bir sözleşmenin tanımını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f4d66-111">It is recommended to apply the attribute to an interface rather than to a class, because doing so creates a definition of a contract that can be variously implemented by any number of classes.</span></span> <span data-ttu-id="f4d66-112">ASP.NET 2,0, <xref:System.Web.Services.WebService> sınıfları arayüzlerin yanı sıra sınıflara uygulama seçeneğini destekler.</span><span class="sxs-lookup"><span data-stu-id="f4d66-112">ASP.NET 2.0 supports the option of applying the <xref:System.Web.Services.WebService> attribute to interfaces as well as classes.</span></span> <span data-ttu-id="f4d66-113">Ancak, zaten bahsedildiği gibi, ASP.NET 2,0 ' de bir hata vardır, bu özniteliğin ad alanı parametresinin <xref:System.Web.Services.WebService> bir sınıf yerine bir arabirime uygulandığında hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="f4d66-113">However, as mentioned already, there is a defect in ASP.NET 2.0, by which the Namespace parameter of the <xref:System.Web.Services.WebService> attribute has no effect when that attribute is applied to an interface rather than a class.</span></span> <span data-ttu-id="f4d66-114">Genellikle, bir hizmetin ad alanını varsayılan değerden değiştirmek önerilir, `http://tempuri.org` öznitelik ad alanı parametresini kullanarak, <xref:System.Web.Services.WebService> bir, <xref:System.ServiceModel.ServiceContractAttribute> özniteliği arabirimlere veya sınıflara uygulayarak ASP.NET Web hizmetlerini tanımlamaya devam etmelidir.</span><span class="sxs-lookup"><span data-stu-id="f4d66-114">Since it is generally advisable to modify the namespace of a service from the default value, `http://tempuri.org`, using the Namespace parameter of the <xref:System.Web.Services.WebService> attribute, one should continue defining ASP.NET Web Services by applying the <xref:System.ServiceModel.ServiceContractAttribute> attribute either to interfaces or to classes.</span></span>  
  
- <span data-ttu-id="f4d66-115">Bu arabirimlerin tanımlandığı metotlarda olabildiğince az kod olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f4d66-115">Have as little code as possible in the methods by which those interfaces are defined.</span></span> <span data-ttu-id="f4d66-116">Çalışmalarını diğer sınıflara devretmek.</span><span class="sxs-lookup"><span data-stu-id="f4d66-116">Have them delegate their work to other classes.</span></span> <span data-ttu-id="f4d66-117">Yeni WCF hizmet türleri, daha sonra bu sınıflara birlikte çalışan işlerini de devredebilir.</span><span class="sxs-lookup"><span data-stu-id="f4d66-117">New WCF service types could then also delegate their substantive work to those classes.</span></span>  
  
- <span data-ttu-id="f4d66-118">Parametresinin parametresini kullanarak bir hizmetin işlemlerine yönelik açık adlar sağlayın `MessageName` <xref:System.Web.Services.WebMethodAttribute> .</span><span class="sxs-lookup"><span data-stu-id="f4d66-118">Provide explicit names for the operations of a service using the `MessageName` parameter of the <xref:System.Web.Services.WebMethodAttribute>.</span></span>  
  
    ```csharp  
    [WebMethod(MessageName="ExplicitName")]  
    string Echo(string input);  
    ```  
  
     <span data-ttu-id="f4d66-119">Bu, ASP.NET içindeki işlemlerin varsayılan adları WCF tarafından sağlanan varsayılan adlardan farklı olduğundan, bunun yapılması önemlidir.</span><span class="sxs-lookup"><span data-stu-id="f4d66-119">Doing so is important, because the default names for operations in ASP.NET are different from the default names supplied by WCF.</span></span> <span data-ttu-id="f4d66-120">Açık adlar sağlayarak varsayılan olanlara bağlı kalmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="f4d66-120">By providing explicit names, you avoid relying on the default ones.</span></span>  
  
- <span data-ttu-id="f4d66-121">WCF, çok biçimli yöntemlerle uygulama işlemlerini desteklemediğinden, ASP.NET Web hizmeti işlemlerini polimorfik yöntemlerle uygulamayın.</span><span class="sxs-lookup"><span data-stu-id="f4d66-121">Do not implement ASP.NET Web service operations with polymorphic methods, because WCF does not support implementing operations with polymorphic methods.</span></span>  
  
- <span data-ttu-id="f4d66-122"><xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute>Http isteklerinin yöntemlere yönlendirileceği SOAPACTION http üst bilgilerine yönelik açık değerler sağlamak için öğesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="f4d66-122">Use the <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute> to provide explicit values for the SOAPAction HTTP headers by which HTTP requests will be routed to methods.</span></span>  
  
    ```csharp  
    [WebMethod]  
    [SoapDocumentMethod(RequestElementName="ExplicitAction")]  
    string Echo(string input);  
    ```  
  
     <span data-ttu-id="f4d66-123">Bu yaklaşımın alınması, ASP.NET tarafından kullanılan varsayılan SOAPAction değerlerini ve WCF 'nin aynı olduğunu aşmak için bir yaklaşım sağlar.</span><span class="sxs-lookup"><span data-stu-id="f4d66-123">Taking this approach will circumvent having to rely on the default SOAPAction values used by ASP.NET and WCF being the same.</span></span>  
  
- <span data-ttu-id="f4d66-124">SOAP uzantıları kullanmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="f4d66-124">Avoid using SOAP extensions.</span></span> <span data-ttu-id="f4d66-125">SOAP uzantıları gerekliyse, kabul edildiği amacının WCF tarafından zaten sağlanmış olan bir özellik olup olmadığını saptayın.</span><span class="sxs-lookup"><span data-stu-id="f4d66-125">If SOAP extensions are required, then determine whether the purpose for which they are being considered is a feature that is already provided by WCF.</span></span> <span data-ttu-id="f4d66-126">Bu durum gerçekten büyük bir durumdur, daha sonra WCF 'yi hemen benimseme seçeneğini yeniden değerlendirin.</span><span class="sxs-lookup"><span data-stu-id="f4d66-126">If that is indeed the case, then reconsider the choice to not adopt WCF right away.</span></span>  
  
## <a name="state-management"></a><span data-ttu-id="f4d66-127">Durum yönetimi</span><span class="sxs-lookup"><span data-stu-id="f4d66-127">State Management</span></span>  
 <span data-ttu-id="f4d66-128">Hizmetlerde durumu sürdürmek zorunda kalmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="f4d66-128">Avoid having to maintain state in services.</span></span> <span data-ttu-id="f4d66-129">Bir uygulamanın ölçeklenebilirliğini tehlikeye atmak için yalnızca durumun korunmasıyla kalmaz, ASP.NET ve WCF 'nin durum yönetimi mekanizmaları çok farklıdır, ancak WCF, ASP.NET uyumluluk modundaki ASP.NET mekanizmalarını destekler.</span><span class="sxs-lookup"><span data-stu-id="f4d66-129">Not only does maintaining state tend to compromise the scalability of an application, but the state management mechanisms of ASP.NET and WCF are very different, although WCF does support the ASP.NET mechanisms in ASP.NET compatibility mode.</span></span>  
  
## <a name="exception-handling"></a><span data-ttu-id="f4d66-130">Özel Durum İşleme</span><span class="sxs-lookup"><span data-stu-id="f4d66-130">Exception Handling</span></span>  
 <span data-ttu-id="f4d66-131">Bir hizmet tarafından gönderilecek ve alınacak veri türlerinin yapılarını tasarlarken, bir hizmette bir istemciye iletmek isteyebileceğiniz farklı özel durum türlerini temsil etmek için de tasarım yapıları.</span><span class="sxs-lookup"><span data-stu-id="f4d66-131">In designing the structures of the data types to be sent and received by a service, also design structures to represent the various types of exceptions that might occur within a service that one might wish to convey to a client.</span></span>  
  
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
  
 <span data-ttu-id="f4d66-132">Bu tür sınıflara, kendilerini XML 'e serileştirme yeteneği verin:</span><span class="sxs-lookup"><span data-stu-id="f4d66-132">Give such classes the ability to serialize themselves to XML:</span></span>  
  
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
  
 <span data-ttu-id="f4d66-133">Sınıflar daha sonra açıkça oluşturulan örneklerin ayrıntılarını sağlamak için kullanılabilir <xref:System.Web.Services.Protocols.SoapException> :</span><span class="sxs-lookup"><span data-stu-id="f4d66-133">The classes can then be used to provide the details for explicitly thrown <xref:System.Web.Services.Protocols.SoapException> instances:</span></span>  
  
```csharp  
AnticipatedException exception = new AnticipatedException();  
exception.AnticipatedExceptionInformation = "…";  
throw new SoapException(  
     "Fault occurred",  
     SoapException.ClientFaultCode,  
     Context.Request.Url.AbsoluteUri,  
     exception.ToXML());  
```  
  
 <span data-ttu-id="f4d66-134">Bu özel durum sınıfları, <xref:System.ServiceModel.FaultException%601> Yeni bir hata oluşturması IÇIN WCF sınıfıyla birlikte yeniden kullanılabilir`FaultException<AnticipatedException>(anticipatedException);`</span><span class="sxs-lookup"><span data-stu-id="f4d66-134">These exception classes will be readily reusable with the WCF <xref:System.ServiceModel.FaultException%601> class to throw a new `FaultException<AnticipatedException>(anticipatedException);`</span></span>  
  
## <a name="security"></a><span data-ttu-id="f4d66-135">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="f4d66-135">Security</span></span>  
 <span data-ttu-id="f4d66-136">Aşağıda bazı güvenlik önerileri verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f4d66-136">The following are some security recommendations.</span></span>  
  
- <span data-ttu-id="f4d66-137">ASP.NET 2,0 profillerinin kullanmaktan kaçının, bu hizmet WCF 'ye geçirildiğinde ASP.NET tümleştirme modunun kullanımını kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="f4d66-137">Avoid using ASP.NET 2.0 Profiles, as using them would restrict the use of ASP.NET Integration Mode if the service was migrated to WCF.</span></span>  
  
- <span data-ttu-id="f4d66-138">ASP.NET Web Hizmetleri, Internet Information Services (IIS) kullanan ACL 'Leri desteklediğinden, WCF, ASP.NET Web Hizmetleri barındırmak için IIS 'ye bağlı olduğundan ve WCF 'nin IIS 'de barındırılması gerekmeyen için, ACL 'Leri kullanmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="f4d66-138">Avoid using ACLs to control access to services, as ASP.NET Web services supports ACLs using Internet Information Services (IIS), WCF does not—because ASP.NET Web services depend on IIS for hosting, and WCF does not necessarily have to be hosted in IIS.</span></span>  
  
- <span data-ttu-id="f4d66-139">Bir hizmetin kaynaklarına erişimi yetkilendirmek için ASP.NET 2,0 rol sağlayıcılarını kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="f4d66-139">Do consider using ASP.NET 2.0 Role Providers for authorizing access to the resources of a service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4d66-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f4d66-140">See also</span></span>

- [<span data-ttu-id="f4d66-141">Windows Communication Foundation'ı Benimsemeyi Bekleme: Gelecekteki Tümleştirmeyi Kolaylaştırma</span><span class="sxs-lookup"><span data-stu-id="f4d66-141">Anticipating Adopting the Windows Communication Foundation: Easing Future Integration</span></span>](anticipating-adopting-the-wcf-easing-future-integration.md)
