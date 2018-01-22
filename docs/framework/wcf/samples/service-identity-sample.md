---
title: "Hizmet Kimliği Örneği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 79fa8c1c-85bb-4b67-bc67-bfaf721303f8
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5a89839294f74d733ec7f607a0afda53148fbd57
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="service-identity-sample"></a><span data-ttu-id="bd57a-102">Hizmet Kimliği Örneği</span><span class="sxs-lookup"><span data-stu-id="bd57a-102">Service Identity Sample</span></span>
<span data-ttu-id="bd57a-103">Bu hizmet kimliği örneği, bir hizmetin kimliğini ayarlamak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="bd57a-103">This service identity sample demonstrates how to set the identity for a service.</span></span> <span data-ttu-id="bd57a-104">Tasarım zamanında bir istemci hizmetin meta verileri kullanarak kimlik alabilir ve ardından çalışma zamanında istemci hizmetin kimliğini doğrulayabilir.</span><span class="sxs-lookup"><span data-stu-id="bd57a-104">At design time, a client can retrieve the identity using the service's metadata and then at runtime the client can authenticate the service's identity.</span></span> <span data-ttu-id="bd57a-105">Hizmet kimliği kavramı, böylece istemci gelen kimliği doğrulanmamış çağrıları koruma işlemlerinden birini çağırmadan önce bir hizmetin kimliğini doğrulamak bir istemci izin vermektir.</span><span class="sxs-lookup"><span data-stu-id="bd57a-105">The concept of service identity is to allow a client to authenticate a service before calling any of its operations, thereby protecting the client from unauthenticated calls.</span></span> <span data-ttu-id="bd57a-106">Güvenli bir bağlantı üzerinden hizmet ayrıca bir istemcinin kimlik bilgileri erişime izin vermeden önce kimliğini doğrular, ancak bu odak noktası, bu örnek değil.</span><span class="sxs-lookup"><span data-stu-id="bd57a-106">On a secure connection the service also authenticates a client's credentials before allowing it access, but this is not the focus of this sample.</span></span> <span data-ttu-id="bd57a-107">Örnekleri görmek [istemci](../../../../docs/framework/wcf/samples/client.md) sunucu kimlik doğrulaması göster.</span><span class="sxs-lookup"><span data-stu-id="bd57a-107">See the samples in [Client](../../../../docs/framework/wcf/samples/client.md) that show server authentication.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bd57a-108">Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="bd57a-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="bd57a-109">Bu örneği aşağıdaki özellikleri gösterir:</span><span class="sxs-lookup"><span data-stu-id="bd57a-109">This sample illustrates the following features:</span></span>  
  
-   <span data-ttu-id="bd57a-110">Kimlik farklı türde bir hizmet için farklı uç noktalar ayarlamak nasıl.</span><span class="sxs-lookup"><span data-stu-id="bd57a-110">How to set the different types of identity on different endpoints for a service.</span></span> <span data-ttu-id="bd57a-111">Kimlik türlerinin farklı özellikleri vardır.</span><span class="sxs-lookup"><span data-stu-id="bd57a-111">Each type of identity has different capabilities.</span></span> <span data-ttu-id="bd57a-112">Kullanılacak kimlik türü, uç noktanın bağlama üzerinde kullanılan güvenlik kimlik bilgileri türünü bağımlıdır.</span><span class="sxs-lookup"><span data-stu-id="bd57a-112">The type of identity to use is dependent on the type of security credentials used on the endpoint's binding.</span></span>  
  
-   <span data-ttu-id="bd57a-113">Kimlik, ya da yapılandırma veya imperatively kodu bildirimli olarak ayarlanmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="bd57a-113">Identity can either be set declaratively in configuration or imperatively in code.</span></span> <span data-ttu-id="bd57a-114">Genellikle hem istemci hem de hizmet için yapılandırma kimliğini ayarlamak için kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="bd57a-114">Typically for both the client and the service you should use configuration to set the identity.</span></span>  
  
-   <span data-ttu-id="bd57a-115">Nasıl özel bir kimlik istemci üzerinde ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="bd57a-115">How to set a custom identity on the client.</span></span> <span data-ttu-id="bd57a-116">Özel bir kimlik mevcut bir türle hizmet çağırmadan önce yetkilendirme kararları için hizmetin kimlik bilgileri bölümünde sağlanan diğer talep bilgilerini inceleyin olanak tanır kimlik, genellikle bir özelleştirmedir.</span><span class="sxs-lookup"><span data-stu-id="bd57a-116">A custom identity is typically a customization of an existing type of identity that enables the client to examine other claim information provided in the service's credentials to make authorization decisions before calling the service.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bd57a-117">Bu örnek identity.com ve bu sertifikadaki RSA anahtarı olarak adlandırılan belirli bir sertifika kimliğini denetler.</span><span class="sxs-lookup"><span data-stu-id="bd57a-117">This sample checks the identity of a specific certificate called identity.com and the RSA key contained within this certificate.</span></span> <span data-ttu-id="bd57a-118">Sertifika ve RSA kimlik türlerinin istemcide yapılandırmasında, bu değerleri almak için kolay bir yol hizmeti WSDL incelemek için bu değerleri nerede serileştirilir kullanıldığında.</span><span class="sxs-lookup"><span data-stu-id="bd57a-118">When using the Certificate and RSA identity types in configuration on the client, an easy way to get these values is to inspect the WSDL for the service where these values are serialized.</span></span>  
  
 <span data-ttu-id="bd57a-119">Aşağıdaki örnek kod, etki alanı ad sunucusu (DNS) ile bir WSHttpBinding kullanarak bir sertifika, hizmet uç noktası kimliğini yapılandırmak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="bd57a-119">The following sample code shows how to configure the identity of a service endpoint with the Domain Name Server (DNS) of a certificate using a WSHttpBinding.</span></span>  
  
```  
//Create a service endpoint and set its identity to the certificate's DNS                 
WSHttpBinding wsAnonbinding = new WSHttpBinding (SecurityMode.Message);  
// Client are Anonymous to the service  
wsAnonbinding.Security.Message.ClientCredentialType = MessageCredentialType.None;  
WServiceEndpoint ep = serviceHost.AddServiceEndpoint(typeof(ICalculator),wsAnonbinding, String.Empty);  
EndpointAddress epa = new EndpointAddress(dnsrelativeAddress,EndpointIdentity.CreateDnsIdentity("identity.com"));  
ep.Address = epa;  
```  
  
 <span data-ttu-id="bd57a-120">Kimlik, App.config dosyasında yapılandırmasında de belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="bd57a-120">The identity can also be specified in configuration in the App.config file.</span></span> <span data-ttu-id="bd57a-121">Aşağıdaki örnek, bir hizmet uç noktası için UPN (kullanıcı asıl adı) kimliğini ayarlamak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="bd57a-121">The following example shows how to set the UPN (User Principal Name) identity for a service endpoint.</span></span>  
  
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
  
 <span data-ttu-id="bd57a-122">Özel bir kimlik türetme tarafından istemcide ayarlanabilir <xref:System.ServiceModel.EndpointIdentity> ve <xref:System.ServiceModel.Security.IdentityVerifier> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="bd57a-122">A custom identity can be set on the client by deriving from the <xref:System.ServiceModel.EndpointIdentity> and the <xref:System.ServiceModel.Security.IdentityVerifier> classes.</span></span> <span data-ttu-id="bd57a-123">Kavramsal olarak <xref:System.ServiceModel.Security.IdentityVerifier> sınıfı, istemci sayılabileceğini hizmetin karşılığıdır `AuthorizationManager` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="bd57a-123">Conceptually the <xref:System.ServiceModel.Security.IdentityVerifier> class can be considered to be the client equivalent of the service's `AuthorizationManager` class.</span></span> <span data-ttu-id="bd57a-124">Aşağıdaki kod örneğinde uygulaması gösterir `OrgEndpointIdentity`, sunucu sertifikasının konu adı ile eşleşmesi için bir kuruluş adı depolar.</span><span class="sxs-lookup"><span data-stu-id="bd57a-124">The following code example shows an implementation of `OrgEndpointIdentity`, which stores an organization name to match in the subject name of the server's certificate.</span></span> <span data-ttu-id="bd57a-125">Kuruluş adı yetkilendirme denetle oluşuyor `CheckAccess` yöntemi `CustomIdentityVerifier` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="bd57a-125">The authorization check for the organization name occurs in the `CheckAccess` method on the `CustomIdentityVerifier` class.</span></span>  
  
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
  
 <span data-ttu-id="bd57a-126">Bu örnek dile özgü kimlik çözüm klasöründe olan identity.com adlı bir sertifika kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="bd57a-126">This sample uses a certificate called identity.com which is in the language-specific Identity solution folder.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="bd57a-127">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="bd57a-127">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="bd57a-128">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bd57a-128">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="bd57a-129">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bd57a-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="bd57a-130">Tek veya çapraz bilgisayar yapılandırmasında örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bd57a-130">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="bd57a-131">Aynı bilgisayara örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="bd57a-131">To run the sample on the same computer</span></span>  
  
1.  <span data-ttu-id="bd57a-132">Üzerinde [!INCLUDE[wxp](../../../../includes/wxp-md.md)] veya [!INCLUDE[wv](../../../../includes/wv-md.md)], kimlik çözümü klasöründeki Identity.pfx sertifika dosyasını MMC ek bileşen aracını kullanarak LocalMachine/My (Kişisel) sertifika deposuna aktarın.</span><span class="sxs-lookup"><span data-stu-id="bd57a-132">On [!INCLUDE[wxp](../../../../includes/wxp-md.md)] or [!INCLUDE[wv](../../../../includes/wv-md.md)], import the Identity.pfx certificate file in the Identity solution folder into the LocalMachine/My (Personal) certificate store using the MMC snap-in tool.</span></span> <span data-ttu-id="bd57a-133">Parola korumalı dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="bd57a-133">This file is password protected.</span></span> <span data-ttu-id="bd57a-134">İçeri aktarma sırasında için bir parola sorulur.</span><span class="sxs-lookup"><span data-stu-id="bd57a-134">During the import you are asked for a password.</span></span> <span data-ttu-id="bd57a-135">Tür `xyz` parola kutusuna.</span><span class="sxs-lookup"><span data-stu-id="bd57a-135">Type `xyz` into the password box.</span></span> <span data-ttu-id="bd57a-136">Daha fazla bilgi için bkz: [nasıl yapılır: MMC ek bileşeni ile sertifikaları görüntüleme](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md) konu.</span><span class="sxs-lookup"><span data-stu-id="bd57a-136">For more information, see the [How to: View Certificates with the MMC Snap-in](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md) topic.</span></span> <span data-ttu-id="bd57a-137">Bunu yaptıktan sonra Setup.bat bir Visual Studio komut istemindeki Currentuser'a/güvenilir Kişiler deposuna istemcide kullanmak için bu sertifikayı kopyaladığı yönetici ayrıcalıklarıyla çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="bd57a-137">Once this is done, run Setup.bat in a Visual Studio command prompt with administrator privileges, which copies this certificate to the CurrentUser/Trusted People store for use on the client.</span></span>  
  
2.  <span data-ttu-id="bd57a-138">Üzerinde [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], içinde örnek yükleme klasöründen Setup.bat çalıştırmak bir [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] komut istemini yönetici ayrıcalıklarına sahip.</span><span class="sxs-lookup"><span data-stu-id="bd57a-138">On [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], run Setup.bat from the sample install folder inside a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] command prompt with administrator privileges.</span></span> <span data-ttu-id="bd57a-139">Bu örneği çalıştırmak için gerekli tüm sertifikalar yükler.</span><span class="sxs-lookup"><span data-stu-id="bd57a-139">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bd57a-140">Setup.bat toplu iş dosyası çalıştırılmak üzere tasarlanmış bir [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] komut istemi.</span><span class="sxs-lookup"><span data-stu-id="bd57a-140">The Setup.bat batch file is designed to be run from a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt.</span></span> <span data-ttu-id="bd57a-141">İçinde PATH ortam değişkeni ayarlamak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] komut istemi Setup.bat komut dosyası için gereken yürütülebilir dosyalar içeren dizine işaret eder.</span><span class="sxs-lookup"><span data-stu-id="bd57a-141">The PATH environment variable set within the [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span> <span data-ttu-id="bd57a-142">Örnekle tamamladığınızda Cleanup.bat çalıştırarak sertifikaları kaldırdığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="bd57a-142">Ensure that you remove the certificates by running Cleanup.bat when you have finished with the sample.</span></span> <span data-ttu-id="bd57a-143">Diğer güvenlik örnekleri aynı sertifikaları kullanır.</span><span class="sxs-lookup"><span data-stu-id="bd57a-143">Other security samples use the same certificates.</span></span>  
  
3.  <span data-ttu-id="bd57a-144">Service.exe \service\bin dizininden başlatın.</span><span class="sxs-lookup"><span data-stu-id="bd57a-144">Launch Service.exe from the \service\bin directory.</span></span> <span data-ttu-id="bd57a-145">Hizmet hazır olduğunu bildirir ve tuşuna bir istem görüntüler gösterir sağlamak \<Enter > Hizmet sonlandırılacak.</span><span class="sxs-lookup"><span data-stu-id="bd57a-145">Ensure that the service indicates that it is ready and displays a prompt to Press \<Enter> to terminate the service.</span></span>  
  
4.  <span data-ttu-id="bd57a-146">Client.exe \client\bin dizinden veya derlemek ve çalıştırmak için Visual Studio'da F5'e basarak başlatın.</span><span class="sxs-lookup"><span data-stu-id="bd57a-146">Launch Client.exe from \client\bin directory or by pressing F5 in Visual Studio to build and run.</span></span> <span data-ttu-id="bd57a-147">İstemci etkinliği istemci konsol uygulaması görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="bd57a-147">Client activity is displayed on the client console application.</span></span>  
  
5.  <span data-ttu-id="bd57a-148">İstemci ve hizmet iletişim kurabildiğinden değilseniz bkz [sorun giderme ipuçları](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="bd57a-148">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="bd57a-149">Bilgisayarlar arasında örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="bd57a-149">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="bd57a-150">Örnek istemci parçası oluşturmadan önce hizmet uç noktası adresi Client.cs dosyasında değeri değiştirdiğinizden emin olun `CallServiceCustomClientIdentity` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="bd57a-150">Before building the client part of the sample, be sure to change the value for the service's endpoint address in the Client.cs file in the `CallServiceCustomClientIdentity` method.</span></span> <span data-ttu-id="bd57a-151">Ardından örnek oluşturun.</span><span class="sxs-lookup"><span data-stu-id="bd57a-151">Then build the sample.</span></span>  
  
2.  <span data-ttu-id="bd57a-152">Hizmet bilgisayarda bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="bd57a-152">Create a directory on the service computer.</span></span>  
  
3.  <span data-ttu-id="bd57a-153">Hizmet program dosyalarını service\bin hizmeti bilgisayarında dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="bd57a-153">Copy the service program files from service\bin to the directory on the service computer.</span></span> <span data-ttu-id="bd57a-154">Ayrıca Setup.bat ve Cleanup.bat dosyalarını hizmet bilgisayara kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="bd57a-154">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
4.  <span data-ttu-id="bd57a-155">İstemci ikili dosyalarının için istemci bilgisayarda bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="bd57a-155">Create a directory on the client computer for the client binaries.</span></span>  
  
5.  <span data-ttu-id="bd57a-156">İstemci program dosyaları istemci bilgisayarda istemci dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="bd57a-156">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="bd57a-157">Ayrıca istemciye Setup.bat, Cleanup.bat ve ImportServiceCert.bat dosyalarını kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="bd57a-157">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
6.  <span data-ttu-id="bd57a-158">Hizmeti, Çalıştır `setup.bat service` yönetici ayrıcalıklarına sahip bir Visual Studio Komut İstemi'nde açılır.</span><span class="sxs-lookup"><span data-stu-id="bd57a-158">On the service, run `setup.bat service` in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="bd57a-159">Çalışan `setup.bat` ile `service` bağımsız değişkeni bilgisayarın tam etki alanı adı ile bir hizmet sertifikası oluşturur ve hizmet sertifikası Service.cer adlı bir dosyaya aktarır.</span><span class="sxs-lookup"><span data-stu-id="bd57a-159">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
7.  <span data-ttu-id="bd57a-160">Service.cer dosya hizmeti dizininden istemci bilgisayarda istemci dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="bd57a-160">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8.  <span data-ttu-id="bd57a-161">İstemci bilgisayardaki Client.exe.config dosyasında yeni adresi hizmetinizin eşleştirmek için uç nokta adresi değerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="bd57a-161">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="bd57a-162">Değiştirilmelidir birden çok örneği vardır.</span><span class="sxs-lookup"><span data-stu-id="bd57a-162">There are multiple instances that must be changed.</span></span>  
  
9. <span data-ttu-id="bd57a-163">İstemci üzerinde yönetici ayrıcalıklarına sahip açılan bir Visual Studio komut istemi ImportServiceCert.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="bd57a-163">On the client, run ImportServiceCert.bat in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="bd57a-164">Bu hizmet sertifikası Service.cer dosyadan Currentuser'a - TrustedPeople deposunu alır.</span><span class="sxs-lookup"><span data-stu-id="bd57a-164">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
10. <span data-ttu-id="bd57a-165">Hizmet bilgisayarda komut isteminden Service.exe başlatın.</span><span class="sxs-lookup"><span data-stu-id="bd57a-165">On the service computer, launch the Service.exe from the command prompt.</span></span>  
  
11. <span data-ttu-id="bd57a-166">İstemci bilgisayarda bir komut isteminden Client.exe başlatın.</span><span class="sxs-lookup"><span data-stu-id="bd57a-166">On the client computer, launch Client.exe from a command prompt.</span></span> <span data-ttu-id="bd57a-167">İstemci ve hizmet iletişim kurabildiğinden değilseniz bkz [sorun giderme ipuçları](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="bd57a-167">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="bd57a-168">Örnek sonra temizlemek için</span><span class="sxs-lookup"><span data-stu-id="bd57a-168">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="bd57a-169">Örnek çalıştıran tamamladıktan sonra Cleanup.bat samples klasöründen çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="bd57a-169">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bd57a-170">Bu komut, bu örnek bilgisayarlar arasında çalıştırırken bir istemcide hizmet sertifikaları kaldırmaz.</span><span class="sxs-lookup"><span data-stu-id="bd57a-170">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="bd57a-171">Çalıştırırsanız [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] bilgisayarlar arasında sertifikaları kullanma örnekleri Currentuser'a - TrustedPeople deposu yüklü hizmet sertifikalarını temizlemek emin olun.</span><span class="sxs-lookup"><span data-stu-id="bd57a-171">If you have run [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="bd57a-172">Bunu yapmak için aşağıdaki komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` örneğin: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="bd57a-172">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd57a-173">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bd57a-173">See Also</span></span>
