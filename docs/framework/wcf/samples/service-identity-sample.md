---
title: Hizmet Kimliği Örneği
ms.date: 03/30/2017
ms.assetid: 79fa8c1c-85bb-4b67-bc67-bfaf721303f8
ms.openlocfilehash: 8cd6688802628a484cc9fe1fc1dffa82ddecd12a
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43872510"
---
# <a name="service-identity-sample"></a><span data-ttu-id="f5dbb-102">Hizmet Kimliği Örneği</span><span class="sxs-lookup"><span data-stu-id="f5dbb-102">Service Identity Sample</span></span>
<span data-ttu-id="f5dbb-103">Bu hizmet kimliği örneği bir hizmet için kimlik gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f5dbb-103">This service identity sample demonstrates how to set the identity for a service.</span></span> <span data-ttu-id="f5dbb-104">Tasarım zamanında istemci hizmet meta verileri kullanarak kimliğini alabilir ve ardından çalışma zamanında istemci hizmetin kimliğini doğrulayabilir.</span><span class="sxs-lookup"><span data-stu-id="f5dbb-104">At design time, a client can retrieve the identity using the service's metadata and then at runtime the client can authenticate the service's identity.</span></span> <span data-ttu-id="f5dbb-105">Hizmet kimliği kavramı, böylece istemci kimliği doğrulanmamış çağrılarından koruma işlemlerinden birini çağırmadan önce bir hizmet kimlik doğrulaması bir istemci izin vermektir.</span><span class="sxs-lookup"><span data-stu-id="f5dbb-105">The concept of service identity is to allow a client to authenticate a service before calling any of its operations, thereby protecting the client from unauthenticated calls.</span></span> <span data-ttu-id="f5dbb-106">Güvenli bir bağlantı üzerinden hizmet de istemci kimlik bilgileri erişime izin vermeden önce kimliğini doğrular, ancak bu odak noktası, bu örnek değil.</span><span class="sxs-lookup"><span data-stu-id="f5dbb-106">On a secure connection the service also authenticates a client's credentials before allowing it access, but this is not the focus of this sample.</span></span> <span data-ttu-id="f5dbb-107">Örnekleri görmek [istemci](../../../../docs/framework/wcf/samples/client.md) sunucu kimlik doğrulaması göster.</span><span class="sxs-lookup"><span data-stu-id="f5dbb-107">See the samples in [Client](../../../../docs/framework/wcf/samples/client.md) that show server authentication.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f5dbb-108">Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="f5dbb-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="f5dbb-109">Bu örnek aşağıdaki özellikleri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="f5dbb-109">This sample illustrates the following features:</span></span>  
  
-   <span data-ttu-id="f5dbb-110">Nasıl bir hizmet için farklı uç noktalar şirket farklı türde kimlik ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="f5dbb-110">How to set the different types of identity on different endpoints for a service.</span></span> <span data-ttu-id="f5dbb-111">Kimlik türlerinin farklı özelliklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="f5dbb-111">Each type of identity has different capabilities.</span></span> <span data-ttu-id="f5dbb-112">Uç noktanın bağlamada kullanılan güvenlik kimlik bilgileri türünü kullanmak için kimlik türü bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="f5dbb-112">The type of identity to use is dependent on the type of security credentials used on the endpoint's binding.</span></span>  
  
-   <span data-ttu-id="f5dbb-113">Kimlik, ya da yapılandırma veya kesin kod bildirimli olarak ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="f5dbb-113">Identity can either be set declaratively in configuration or imperatively in code.</span></span> <span data-ttu-id="f5dbb-114">Genellikle hem istemci hem de hizmet için kimlik yapılandırma kullanmalısınız.</span><span class="sxs-lookup"><span data-stu-id="f5dbb-114">Typically for both the client and the service you should use configuration to set the identity.</span></span>  
  
-   <span data-ttu-id="f5dbb-115">Nasıl özel bir kimlik istemci üzerinde ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="f5dbb-115">How to set a custom identity on the client.</span></span> <span data-ttu-id="f5dbb-116">Özel kimlik hizmeti çağırmadan önce yetkilendirme kararları vermek için hizmetin kimlik bilgileri sağlanan başka talep bilgileri incelemek istemci sağlayan kimlik var olan bir tür genellikle bir özelleştirmedir.</span><span class="sxs-lookup"><span data-stu-id="f5dbb-116">A custom identity is typically a customization of an existing type of identity that enables the client to examine other claim information provided in the service's credentials to make authorization decisions before calling the service.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f5dbb-117">Bu örnek identity.com ve bu sertifikadaki RSA anahtarı adlı belirli bir sertifika kimliği denetler.</span><span class="sxs-lookup"><span data-stu-id="f5dbb-117">This sample checks the identity of a specific certificate called identity.com and the RSA key contained within this certificate.</span></span> <span data-ttu-id="f5dbb-118">İstemci yapılandırması sertifika ve RSA kimlik türlerini kullanarak, bu değerleri almak için kolay bir yol hizmeti için WSDL incelemek için bu değerleri nerede serileştirilir andır.</span><span class="sxs-lookup"><span data-stu-id="f5dbb-118">When using the Certificate and RSA identity types in configuration on the client, an easy way to get these values is to inspect the WSDL for the service where these values are serialized.</span></span>  
  
 <span data-ttu-id="f5dbb-119">Aşağıdaki örnek kod, bir hizmet uç noktası kimliği etki alanı adı sunucusu (DNS) ile bir WSHttpBinding kullanarak bir sertifika yapılandırmak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f5dbb-119">The following sample code shows how to configure the identity of a service endpoint with the Domain Name Server (DNS) of a certificate using a WSHttpBinding.</span></span>  
  
```  
//Create a service endpoint and set its identity to the certificate's DNS                 
WSHttpBinding wsAnonbinding = new WSHttpBinding (SecurityMode.Message);  
// Client are Anonymous to the service  
wsAnonbinding.Security.Message.ClientCredentialType = MessageCredentialType.None;  
WServiceEndpoint ep = serviceHost.AddServiceEndpoint(typeof(ICalculator),wsAnonbinding, String.Empty);  
EndpointAddress epa = new EndpointAddress(dnsrelativeAddress,EndpointIdentity.CreateDnsIdentity("identity.com"));  
ep.Address = epa;  
```  
  
 <span data-ttu-id="f5dbb-120">Kimlik, App.config dosyasında yapılandırmasında de belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="f5dbb-120">The identity can also be specified in configuration in the App.config file.</span></span> <span data-ttu-id="f5dbb-121">Aşağıdaki örnek, bir hizmet uç noktası için UPN (kullanıcı asıl adı) kimliğini ayarlamak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f5dbb-121">The following example shows how to set the UPN (User Principal Name) identity for a service endpoint.</span></span>  
  
```xml  
<endpoint address="upnidentity"  
        behaviorConfiguration=""  
        binding="wsHttpBinding"  
        bindingConfiguration="WSHttpBinding_Windows"  
        name="WSHttpBinding_ICalculator_Windows"  
        contract="Microsoft.ServiceModel.Samples.ICalculator">  
  <!-- Set the UPN identity for this endpoint -->  
  <identity>  
      <userPrincipalName value="host\myservice.com" />  
  </identity >  
</endpoint>  
```  
  
 <span data-ttu-id="f5dbb-122">Özel kimlik türeterek istemcide ayarlanabilir <xref:System.ServiceModel.EndpointIdentity> ve <xref:System.ServiceModel.Security.IdentityVerifier> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="f5dbb-122">A custom identity can be set on the client by deriving from the <xref:System.ServiceModel.EndpointIdentity> and the <xref:System.ServiceModel.Security.IdentityVerifier> classes.</span></span> <span data-ttu-id="f5dbb-123">Kavramsal olarak <xref:System.ServiceModel.Security.IdentityVerifier> sınıfı kabul istemci olarak denk olan hizmetin `AuthorizationManager` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f5dbb-123">Conceptually the <xref:System.ServiceModel.Security.IdentityVerifier> class can be considered to be the client equivalent of the service's `AuthorizationManager` class.</span></span> <span data-ttu-id="f5dbb-124">Aşağıdaki kod örneği uygulanışı gösterilmektedir `OrgEndpointIdentity`, sunucu sertifikasının konu adını eşleştirmek için bir kuruluş adı depolar.</span><span class="sxs-lookup"><span data-stu-id="f5dbb-124">The following code example shows an implementation of `OrgEndpointIdentity`, which stores an organization name to match in the subject name of the server's certificate.</span></span> <span data-ttu-id="f5dbb-125">Kuruluş adı yetkilendirme denetle oluşuyor `CheckAccess` metodunda `CustomIdentityVerifier` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f5dbb-125">The authorization check for the organization name occurs in the `CheckAccess` method on the `CustomIdentityVerifier` class.</span></span>  
  
```  
// This custom EndpointIdentity stores an organization name   
public class OrgEndpointIdentity : EndpointIdentity  
{  
    private string orgClaim;  
    public OrgEndpointIdentity(string orgName)  
    {  
        orgClaim = orgName;  
    }  
    public string OrganizationClaim  
    {  
        get { return orgClaim; }  
        set { orgClaim = value; }  
    }  
}  
  
//This custom IdentityVerifier uses the supplied OrgEndpointIdentity to  
//check that X.509 certificate's distinguished name claim contains  
//the organization name e.g. the string value "O=Contoso"   
class CustomIdentityVerifier : IdentityVerifier  
{  
    public override bool CheckAccess(EndpointIdentity identity, AuthorizationContext authContext)  
    {  
        bool returnvalue = false;  
        foreach (ClaimSet claimset in authContext.ClaimSets)  
        {  
            foreach (Claim claim in claimset)  
            {  
                if (claim.ClaimType == "http://schemas.microsoft.com/ws/2005/05/identity/claims/x500distinguishedname")  
                {  
                    X500DistinguishedName name = (X500DistinguishedName)claim.Resource;  
                    if (name.Name.Contains(((OrgEndpointIdentity)identity).OrganizationClaim))  
                    {  
                        Console.WriteLine("Claim Type: {0}",claim.ClaimType);  
                        Console.WriteLine("Right: {0}", claim.Right);  
                        Console.WriteLine("Resource: {0}",claim.Resource);  
                        Console.WriteLine();  
                        returnvalue = true;  
                    }  
                }  
            }  
        }  
        return returnvalue;  
    }  
}  
```  
  
 <span data-ttu-id="f5dbb-126">Bu örnek için dile özgü kimlik Çözüm klasörü içinde olan identity.com adı verilen bir sertifika kullanır.</span><span class="sxs-lookup"><span data-stu-id="f5dbb-126">This sample uses a certificate called identity.com which is in the language-specific Identity solution folder.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f5dbb-127">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="f5dbb-127">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="f5dbb-128">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f5dbb-128">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="f5dbb-129">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f5dbb-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="f5dbb-130">Tek veya çoklu bilgisayar yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f5dbb-130">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="f5dbb-131">Örneği aynı bilgisayarda çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="f5dbb-131">To run the sample on the same computer</span></span>  
  
1.  <span data-ttu-id="f5dbb-132">Üzerinde [!INCLUDE[wxp](../../../../includes/wxp-md.md)] veya [!INCLUDE[wv](../../../../includes/wv-md.md)], kimlik Çözüm klasörü'ndeki Identity.pfx sertifika dosyası MMC ek bileşenini aracını kullanarak LocalMachine/My (Kişisel) sertifika deposuna aktarın.</span><span class="sxs-lookup"><span data-stu-id="f5dbb-132">On [!INCLUDE[wxp](../../../../includes/wxp-md.md)] or [!INCLUDE[wv](../../../../includes/wv-md.md)], import the Identity.pfx certificate file in the Identity solution folder into the LocalMachine/My (Personal) certificate store using the MMC snap-in tool.</span></span> <span data-ttu-id="f5dbb-133">Parola korumalı dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="f5dbb-133">This file is password protected.</span></span> <span data-ttu-id="f5dbb-134">İçeri aktarma sırasında parola istenir.</span><span class="sxs-lookup"><span data-stu-id="f5dbb-134">During the import you are asked for a password.</span></span> <span data-ttu-id="f5dbb-135">Tür `xyz` parola kutusu içine.</span><span class="sxs-lookup"><span data-stu-id="f5dbb-135">Type `xyz` into the password box.</span></span> <span data-ttu-id="f5dbb-136">Daha fazla bilgi için [nasıl yapılır: MMC ek bileşeni ile sertifikaları görüntüleme](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md) konu.</span><span class="sxs-lookup"><span data-stu-id="f5dbb-136">For more information, see the [How to: View Certificates with the MMC Snap-in](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md) topic.</span></span> <span data-ttu-id="f5dbb-137">Bunu yaptıktan sonra Setup.bat bir Visual Studio komut, istemcide kullanılmak CurrentUser/güvenilir Kişiler deposuna kopyalar. Bu sertifika istemini yönetici ayrıcalıklarıyla çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="f5dbb-137">Once this is done, run Setup.bat in a Visual Studio command prompt with administrator privileges, which copies this certificate to the CurrentUser/Trusted People store for use on the client.</span></span>  
  
2.  <span data-ttu-id="f5dbb-138">Üzerinde [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], Setup.bat örnek yükleme klasörü içinde çalıştırılan bir [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] yönetici ayrıcalıklarıyla bir komut istemi.</span><span class="sxs-lookup"><span data-stu-id="f5dbb-138">On [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], run Setup.bat from the sample install folder inside a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] command prompt with administrator privileges.</span></span> <span data-ttu-id="f5dbb-139">Bu örneği çalıştırmak için gerekli olan tüm sertifikaları yükler.</span><span class="sxs-lookup"><span data-stu-id="f5dbb-139">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f5dbb-140">Setup.bat toplu iş dosyası çalıştırılmak üzere tasarlanmış bir [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] komut istemi.</span><span class="sxs-lookup"><span data-stu-id="f5dbb-140">The Setup.bat batch file is designed to be run from a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt.</span></span> <span data-ttu-id="f5dbb-141">İçinde PATH ortam değişkenini ayarlamak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] komut istemi Setup.bat betiği tarafından gereken yürütülebilir dosyaları içeren dizine işaret eder.</span><span class="sxs-lookup"><span data-stu-id="f5dbb-141">The PATH environment variable set within the [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span> <span data-ttu-id="f5dbb-142">Örnek ile tamamladığınızda Cleanup.bat çalıştırarak, sertifikaları kaldırdığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="f5dbb-142">Ensure that you remove the certificates by running Cleanup.bat when you have finished with the sample.</span></span> <span data-ttu-id="f5dbb-143">Diğer güvenlik örnekleri aynı sertifikalarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="f5dbb-143">Other security samples use the same certificates.</span></span>  
  
3.  <span data-ttu-id="f5dbb-144">Service.exe \service\bin dizinden başlatın.</span><span class="sxs-lookup"><span data-stu-id="f5dbb-144">Launch Service.exe from the \service\bin directory.</span></span> <span data-ttu-id="f5dbb-145">Hizmet hazır olduğunda ve bir istem görüntüler tuşuna gösterdiğini olun \<Enter > hizmeti sonlandırmak için.</span><span class="sxs-lookup"><span data-stu-id="f5dbb-145">Ensure that the service indicates that it is ready and displays a prompt to Press \<Enter> to terminate the service.</span></span>  
  
4.  <span data-ttu-id="f5dbb-146">Client.exe \client\bin dizinden veya derlemek ve çalıştırmak için Visual Studio'da F5 tuşuna basarak başlatın.</span><span class="sxs-lookup"><span data-stu-id="f5dbb-146">Launch Client.exe from \client\bin directory or by pressing F5 in Visual Studio to build and run.</span></span> <span data-ttu-id="f5dbb-147">İstemci etkinliği istemci konsol uygulamasında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="f5dbb-147">Client activity is displayed on the client console application.</span></span>  
  
5.  <span data-ttu-id="f5dbb-148">İstemci ve hizmet iletişim kurabildiğini bilmiyorsanız bkz [sorun giderme ipuçları](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="f5dbb-148">If the client and service are not able to communicate, see [Troubleshooting Tips](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="f5dbb-149">Bilgisayarlar arasında örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="f5dbb-149">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="f5dbb-150">İstemci parçası oluşturmadan önce Client.cs dosyasında hizmetin uç nokta adresi değerini değiştirmek mutlaka `CallServiceCustomClientIdentity` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f5dbb-150">Before building the client part of the sample, be sure to change the value for the service's endpoint address in the Client.cs file in the `CallServiceCustomClientIdentity` method.</span></span> <span data-ttu-id="f5dbb-151">Ardından örnek oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f5dbb-151">Then build the sample.</span></span>  
  
2.  <span data-ttu-id="f5dbb-152">Hizmet bilgisayarda bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f5dbb-152">Create a directory on the service computer.</span></span>  
  
3.  <span data-ttu-id="f5dbb-153">Hizmet program dosyaları service\bin hizmeti bilgisayarında dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="f5dbb-153">Copy the service program files from service\bin to the directory on the service computer.</span></span> <span data-ttu-id="f5dbb-154">Ayrıca Setup.bat ve Cleanup.bat dosyaları hizmet bilgisayara kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="f5dbb-154">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
4.  <span data-ttu-id="f5dbb-155">İstemci ikili dosyaları için istemci bilgisayarda bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f5dbb-155">Create a directory on the client computer for the client binaries.</span></span>  
  
5.  <span data-ttu-id="f5dbb-156">İstemci program dosyaları istemci bilgisayarda istemci dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="f5dbb-156">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="f5dbb-157">Aynı zamanda istemciye Setup.bat Cleanup.bat ve ImportServiceCert.bat dosyaları kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="f5dbb-157">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
6.  <span data-ttu-id="f5dbb-158">Hizmette çalıştıracak `setup.bat service` yönetici ayrıcalıklarına sahip bir Visual Studio Komut İstemi'nde açılır.</span><span class="sxs-lookup"><span data-stu-id="f5dbb-158">On the service, run `setup.bat service` in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="f5dbb-159">Çalışan `setup.bat` ile `service` bağımsız değişkeni bilgisayarın tam etki alanı adı ile bir hizmet sertifikası oluşturur ve hizmet sertifikası Service.cer adlı bir dosyaya dışarı aktarır.</span><span class="sxs-lookup"><span data-stu-id="f5dbb-159">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
7.  <span data-ttu-id="f5dbb-160">Service.cer dosya hizmeti dizinden istemci bilgisayarda istemci dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="f5dbb-160">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8.  <span data-ttu-id="f5dbb-161">İstemci bilgisayarda Client.exe.config dosyasında hizmetinizin yeni adresiyle eşleşecek şekilde uç nokta adresi değiştirin.</span><span class="sxs-lookup"><span data-stu-id="f5dbb-161">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="f5dbb-162">Değiştirilmesi gereken birden çok örneği vardır.</span><span class="sxs-lookup"><span data-stu-id="f5dbb-162">There are multiple instances that must be changed.</span></span>  
  
9. <span data-ttu-id="f5dbb-163">İstemcide ImportServiceCert.bat yönetici ayrıcalıklarıyla açılan bir Visual Studio komut isteminde çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="f5dbb-163">On the client, run ImportServiceCert.bat in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="f5dbb-164">Bu hizmet sertifikası Service.cer dosyasından CurrentUser - TrustedPeople deposuna aktarır.</span><span class="sxs-lookup"><span data-stu-id="f5dbb-164">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
10. <span data-ttu-id="f5dbb-165">Hizmet bilgisayarda Service.exe komut istemini başlatın.</span><span class="sxs-lookup"><span data-stu-id="f5dbb-165">On the service computer, launch the Service.exe from the command prompt.</span></span>  
  
11. <span data-ttu-id="f5dbb-166">İstemci bilgisayarda bir komut istemi'nden Client.exe başlatın.</span><span class="sxs-lookup"><span data-stu-id="f5dbb-166">On the client computer, launch Client.exe from a command prompt.</span></span> <span data-ttu-id="f5dbb-167">İstemci ve hizmet iletişim kurabildiğini bilmiyorsanız bkz [sorun giderme ipuçları](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="f5dbb-167">If the client and service are not able to communicate, see [Troubleshooting Tips](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="f5dbb-168">Sonra örnek temizlemek için</span><span class="sxs-lookup"><span data-stu-id="f5dbb-168">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="f5dbb-169">Bu örneği çalıştırmadan tamamladıktan sonra Cleanup.bat samples klasöründe çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="f5dbb-169">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f5dbb-170">Bu betik, bu örnek, bilgisayarlar arasında çalıştırırken bir istemcide hizmet sertifikaları kaldırmaz.</span><span class="sxs-lookup"><span data-stu-id="f5dbb-170">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="f5dbb-171">Bilgisayarlar arasında sertifikaları kullanan bir Windows Communication Foundation (WCF) örnekleri çalıştırırsanız, CurrentUser - TrustedPeople deposu yüklü hizmet sertifikalarını Temizle emin olun.</span><span class="sxs-lookup"><span data-stu-id="f5dbb-171">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="f5dbb-172">Bunu yapmak için aşağıdaki komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` örneğin: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="f5dbb-172">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5dbb-173">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f5dbb-173">See Also</span></span>
