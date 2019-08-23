---
title: Hizmet Kimliği Örneği
ms.date: 03/30/2017
ms.assetid: 79fa8c1c-85bb-4b67-bc67-bfaf721303f8
ms.openlocfilehash: 999e05918eb7ac852336136a1e7512a2e9d7b9db
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964532"
---
# <a name="service-identity-sample"></a><span data-ttu-id="c9c72-102">Hizmet Kimliği Örneği</span><span class="sxs-lookup"><span data-stu-id="c9c72-102">Service Identity Sample</span></span>
<span data-ttu-id="c9c72-103">Bu hizmet kimliği örneği, bir hizmetin kimliğini nasıl ayarlayabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="c9c72-103">This service identity sample demonstrates how to set the identity for a service.</span></span> <span data-ttu-id="c9c72-104">Tasarım zamanında, istemci, hizmetin meta verilerini kullanarak kimliği alabilir ve çalışma zamanında istemci hizmetin kimliğini doğrulayabilir.</span><span class="sxs-lookup"><span data-stu-id="c9c72-104">At design time, a client can retrieve the identity using the service's metadata and then at runtime the client can authenticate the service's identity.</span></span> <span data-ttu-id="c9c72-105">Hizmet kimliği kavramı, bir istemcinin işlemlerini çağırmadan önce bir hizmetin kimliğini doğrulamasına izin ver, böylelikle de istemciyi kimliği doğrulanmamış çağrılardan koruyor.</span><span class="sxs-lookup"><span data-stu-id="c9c72-105">The concept of service identity is to allow a client to authenticate a service before calling any of its operations, thereby protecting the client from unauthenticated calls.</span></span> <span data-ttu-id="c9c72-106">Güvenli bir bağlantıda hizmet, erişim izni vermeden önce bir istemcinin kimlik bilgilerini doğrular, ancak bu, bu örneğin odağı değildir.</span><span class="sxs-lookup"><span data-stu-id="c9c72-106">On a secure connection the service also authenticates a client's credentials before allowing it access, but this is not the focus of this sample.</span></span> <span data-ttu-id="c9c72-107">[İstemcide](../../../../docs/framework/wcf/samples/client.md) sunucu kimlik doğrulamasını gösteren örneklere bakın.</span><span class="sxs-lookup"><span data-stu-id="c9c72-107">See the samples in [Client](../../../../docs/framework/wcf/samples/client.md) that show server authentication.</span></span>

> [!NOTE]
> <span data-ttu-id="c9c72-108">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="c9c72-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

 <span data-ttu-id="c9c72-109">Bu örnek aşağıdaki özellikleri göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="c9c72-109">This sample illustrates the following features:</span></span>

- <span data-ttu-id="c9c72-110">Bir hizmetin farklı uç noktalarında farklı kimlik türlerini ayarlama.</span><span class="sxs-lookup"><span data-stu-id="c9c72-110">How to set the different types of identity on different endpoints for a service.</span></span> <span data-ttu-id="c9c72-111">Her kimlik türünün farklı becerileri vardır.</span><span class="sxs-lookup"><span data-stu-id="c9c72-111">Each type of identity has different capabilities.</span></span> <span data-ttu-id="c9c72-112">Kullanılacak kimliğin türü, uç noktanın bağlamasında kullanılan güvenlik kimlik bilgilerinin türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="c9c72-112">The type of identity to use is dependent on the type of security credentials used on the endpoint's binding.</span></span>

- <span data-ttu-id="c9c72-113">Kimlik, yapılandırmada veya imperatively kodunda bildirimli olarak ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="c9c72-113">Identity can either be set declaratively in configuration or imperatively in code.</span></span> <span data-ttu-id="c9c72-114">Genellikle, hem istemci hem de hizmet için, kimliği ayarlamak için yapılandırmayı kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c9c72-114">Typically for both the client and the service you should use configuration to set the identity.</span></span>

- <span data-ttu-id="c9c72-115">İstemci üzerinde özel bir kimlik ayarlama.</span><span class="sxs-lookup"><span data-stu-id="c9c72-115">How to set a custom identity on the client.</span></span> <span data-ttu-id="c9c72-116">Özel kimlik, genellikle istemcinin hizmeti çağırmadan önce yetkilendirme kararları vermek için hizmetin kimlik bilgilerinde belirtilen diğer talep bilgilerini incelemesini sağlayan mevcut bir kimlik türünün özelleştirilmesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="c9c72-116">A custom identity is typically a customization of an existing type of identity that enables the client to examine other claim information provided in the service's credentials to make authorization decisions before calling the service.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="c9c72-117">Bu örnek, identity.com adlı belirli bir sertifikanın kimliğini ve bu sertifika içinde bulunan RSA anahtarını denetler.</span><span class="sxs-lookup"><span data-stu-id="c9c72-117">This sample checks the identity of a specific certificate called identity.com and the RSA key contained within this certificate.</span></span> <span data-ttu-id="c9c72-118">İstemci üzerindeki yapılandırmada sertifika ve RSA Kimlik türleri kullanılırken, bu değerleri almanın kolay bir yolu, bu değerlerin serileştirildiği hizmet için WSDL 'yi incelekullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="c9c72-118">When using the Certificate and RSA identity types in configuration on the client, an easy way to get these values is to inspect the WSDL for the service where these values are serialized.</span></span>

 <span data-ttu-id="c9c72-119">Aşağıdaki örnek kod, bir hizmet uç noktasının kimliğini bir WSHttpBinding kullanarak bir sertifikanın etki alanı adı sunucusu (DNS) ile yapılandırmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="c9c72-119">The following sample code shows how to configure the identity of a service endpoint with the Domain Name Server (DNS) of a certificate using a WSHttpBinding.</span></span>

```csharp
//Create a service endpoint and set its identity to the certificate's DNS
WSHttpBinding wsAnonbinding = new WSHttpBinding (SecurityMode.Message);
// Client are Anonymous to the service
wsAnonbinding.Security.Message.ClientCredentialType = MessageCredentialType.None;
WServiceEndpoint ep = serviceHost.AddServiceEndpoint(typeof(ICalculator),wsAnonbinding, String.Empty);
EndpointAddress epa = new EndpointAddress(dnsrelativeAddress,EndpointIdentity.CreateDnsIdentity("identity.com"));
ep.Address = epa;
```

 <span data-ttu-id="c9c72-120">Kimlik, App. config dosyasındaki yapılandırmada de belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="c9c72-120">The identity can also be specified in configuration in the App.config file.</span></span> <span data-ttu-id="c9c72-121">Aşağıdaki örnekte, bir hizmet uç noktası için UPN (Kullanıcı asıl adı) kimliğinin nasıl ayarlanacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c9c72-121">The following example shows how to set the UPN (User Principal Name) identity for a service endpoint.</span></span>

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

 <span data-ttu-id="c9c72-122">Özel bir kimlik, <xref:System.ServiceModel.EndpointIdentity> <xref:System.ServiceModel.Security.IdentityVerifier> ve sınıflarından türeterek istemci üzerinde ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="c9c72-122">A custom identity can be set on the client by deriving from the <xref:System.ServiceModel.EndpointIdentity> and the <xref:System.ServiceModel.Security.IdentityVerifier> classes.</span></span> <span data-ttu-id="c9c72-123">Kavramsal olarak <xref:System.ServiceModel.Security.IdentityVerifier> sınıf, `AuthorizationManager` hizmetin sınıfının istemci eşdeğeri olarak düşünülebilir.</span><span class="sxs-lookup"><span data-stu-id="c9c72-123">Conceptually the <xref:System.ServiceModel.Security.IdentityVerifier> class can be considered to be the client equivalent of the service's `AuthorizationManager` class.</span></span> <span data-ttu-id="c9c72-124">Aşağıdaki kod örneğinde `OrgEndpointIdentity`, bir kuruluş adını, sunucu sertifikasının konu adı ile eşleşecek şekilde depolayan bir uygulamasını gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c9c72-124">The following code example shows an implementation of `OrgEndpointIdentity`, which stores an organization name to match in the subject name of the server's certificate.</span></span> <span data-ttu-id="c9c72-125">Kuruluş adı için yetkilendirme denetimi, `CheckAccess` `CustomIdentityVerifier` sınıfındaki yönteminde oluşur.</span><span class="sxs-lookup"><span data-stu-id="c9c72-125">The authorization check for the organization name occurs in the `CheckAccess` method on the `CustomIdentityVerifier` class.</span></span>

```csharp
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

 <span data-ttu-id="c9c72-126">Bu örnek, dile özgü kimlik çözüm klasöründeki identity.com adlı bir sertifika kullanır.</span><span class="sxs-lookup"><span data-stu-id="c9c72-126">This sample uses a certificate called identity.com which is in the language-specific Identity solution folder.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c9c72-127">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="c9c72-127">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="c9c72-128">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="c9c72-128">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="c9c72-129">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="c9c72-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="c9c72-130">Örneği tek veya bir çoklu bilgisayar yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="c9c72-130">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="c9c72-131">Örneği aynı bilgisayarda çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="c9c72-131">To run the sample on the same computer</span></span>

1. <span data-ttu-id="c9c72-132">[!INCLUDE[wxp](../../../../includes/wxp-md.md)] Veya[!INCLUDE[wv](../../../../includes/wv-md.md)]üzerinde, kimlik çözüm klasöründeki Identity. pfx sertifika dosyasını, MMC ek bileşeni aracını kullanarak LocalMachine/My (Personal) sertifika deposuna aktarın.</span><span class="sxs-lookup"><span data-stu-id="c9c72-132">On [!INCLUDE[wxp](../../../../includes/wxp-md.md)] or [!INCLUDE[wv](../../../../includes/wv-md.md)], import the Identity.pfx certificate file in the Identity solution folder into the LocalMachine/My (Personal) certificate store using the MMC snap-in tool.</span></span> <span data-ttu-id="c9c72-133">Bu dosya parola korumalıdır.</span><span class="sxs-lookup"><span data-stu-id="c9c72-133">This file is password protected.</span></span> <span data-ttu-id="c9c72-134">İçeri aktarma sırasında sizden bir parola istenir.</span><span class="sxs-lookup"><span data-stu-id="c9c72-134">During the import you are asked for a password.</span></span> <span data-ttu-id="c9c72-135">Parola `xyz` kutusuna yazın.</span><span class="sxs-lookup"><span data-stu-id="c9c72-135">Type `xyz` into the password box.</span></span> <span data-ttu-id="c9c72-136">Daha fazla bilgi için bkz [. nasıl yapılır: MMC ek bileşeni](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md) ile sertifikaları görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="c9c72-136">For more information, see the [How to: View Certificates with the MMC Snap-in](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md) topic.</span></span> <span data-ttu-id="c9c72-137">Bu işlem tamamlandıktan sonra, bu sertifikayı istemcide kullanılmak üzere geçerli kullanıcı/güvenilir kişiler deposuna kopyalayan yönetici ayrıcalıklarına sahip Visual Studio için Geliştirici Komut İstemi Setup. bat dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c9c72-137">Once this is done, run Setup.bat in a Developer Command Prompt for Visual Studio with administrator privileges, which copies this certificate to the CurrentUser/Trusted People store for use on the client.</span></span>

2. <span data-ttu-id="c9c72-138">Üzerinde [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], yönetici ayrıcalıklarıyla bir Visual Studio 2012 komut istemi içindeki örnek yükleme klasöründen Setup. bat dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c9c72-138">On [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], run Setup.bat from the sample install folder inside a Visual Studio 2012 command prompt with administrator privileges.</span></span> <span data-ttu-id="c9c72-139">Bu, örneği çalıştırmak için gereken tüm sertifikaları kurar.</span><span class="sxs-lookup"><span data-stu-id="c9c72-139">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="c9c72-140">Setup. bat toplu iş dosyası bir Visual Studio 2012 komut Isteminden çalıştırılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="c9c72-140">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="c9c72-141">Visual Studio 2012 komut Isteminde ayarlanan PATH ortam değişkeni Setup. bat betiği için gereken yürütülebilir dosyaları içeren dizine işaret eder.</span><span class="sxs-lookup"><span data-stu-id="c9c72-141">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span> <span data-ttu-id="c9c72-142">Örnek ile işiniz bittiğinde Cleanup. bat dosyasını çalıştırarak sertifikaları kaldırtığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="c9c72-142">Ensure that you remove the certificates by running Cleanup.bat when you have finished with the sample.</span></span> <span data-ttu-id="c9c72-143">Diğer güvenlik örnekleri aynı sertifikaları kullanır.</span><span class="sxs-lookup"><span data-stu-id="c9c72-143">Other security samples use the same certificates.</span></span>  
  
3. <span data-ttu-id="c9c72-144">\Service\bin dizininden Service. exe ' yi başlatın.</span><span class="sxs-lookup"><span data-stu-id="c9c72-144">Launch Service.exe from the \service\bin directory.</span></span> <span data-ttu-id="c9c72-145">Hizmetin hazırlandığını belirttiğinden emin olun ve hizmeti sonlandırmak için > Enter tuşuna basarak \<bir istem görüntüler.</span><span class="sxs-lookup"><span data-stu-id="c9c72-145">Ensure that the service indicates that it is ready and displays a prompt to Press \<Enter> to terminate the service.</span></span>  
  
4. <span data-ttu-id="c9c72-146">Oluşturmak ve çalıştırmak için, \client\bin dizininden veya Visual Studio 'daki F5 tuşuna basarak Client. exe ' yi başlatın.</span><span class="sxs-lookup"><span data-stu-id="c9c72-146">Launch Client.exe from \client\bin directory or by pressing F5 in Visual Studio to build and run.</span></span> <span data-ttu-id="c9c72-147">İstemci etkinliği istemci konsol uygulamasında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="c9c72-147">Client activity is displayed on the client console application.</span></span>  
  
5. <span data-ttu-id="c9c72-148">İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="c9c72-148">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="c9c72-149">Örneği bilgisayarlar arasında çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="c9c72-149">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="c9c72-150">Örneğin istemci bölümünü oluşturmadan önce, `CallServiceCustomClientIdentity` yöntemin Client.cs dosyasındaki hizmetin uç nokta adresinin değerini değiştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="c9c72-150">Before building the client part of the sample, be sure to change the value for the service's endpoint address in the Client.cs file in the `CallServiceCustomClientIdentity` method.</span></span> <span data-ttu-id="c9c72-151">Ardından örnek oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c9c72-151">Then build the sample.</span></span>  
  
2. <span data-ttu-id="c9c72-152">Hizmet bilgisayarında bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c9c72-152">Create a directory on the service computer.</span></span>  
  
3. <span data-ttu-id="c9c72-153">Hizmet programı dosyalarını service\bin konumundan hizmet bilgisayarındaki dizine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="c9c72-153">Copy the service program files from service\bin to the directory on the service computer.</span></span> <span data-ttu-id="c9c72-154">Ayrıca Setup. bat ve Cleanup. bat dosyalarını da hizmet bilgisayarına kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="c9c72-154">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
4. <span data-ttu-id="c9c72-155">İstemci bilgisayarda istemci ikilileri için bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c9c72-155">Create a directory on the client computer for the client binaries.</span></span>  
  
5. <span data-ttu-id="c9c72-156">İstemci programı dosyalarını istemci bilgisayardaki istemci dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="c9c72-156">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="c9c72-157">Ayrıca Setup. bat, Cleanup. bat ve ImportServiceCert. bat dosyalarını istemciye kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="c9c72-157">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
6. <span data-ttu-id="c9c72-158">Hizmette, yönetici ayrıcalıklarıyla açılan `setup.bat service` bir Visual Studio için geliştirici komut istemi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c9c72-158">On the service, run `setup.bat service` in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="c9c72-159">Bağımsız`service` değişkeniyle birlikte çalıştırmak `setup.bat` , bilgisayarın tam etki alanı adına sahip bir hizmet sertifikası oluşturur ve hizmet sertifikasını Service. cer adlı bir dosyaya aktarır.</span><span class="sxs-lookup"><span data-stu-id="c9c72-159">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
7. <span data-ttu-id="c9c72-160">Service. cer dosyasını hizmet dizininden istemci bilgisayarındaki istemci dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="c9c72-160">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8. <span data-ttu-id="c9c72-161">İstemci bilgisayardaki Client. exe. config dosyasında, uç noktanın adres değerini hizmetinizin yeni adresiyle eşleşecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="c9c72-161">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="c9c72-162">Değiştirilmesi gereken birden çok örnek vardır.</span><span class="sxs-lookup"><span data-stu-id="c9c72-162">There are multiple instances that must be changed.</span></span>  
  
9. <span data-ttu-id="c9c72-163">İstemcide, yönetici ayrıcalıklarıyla açılan bir Geliştirici Komut İstemi Visual Studio için ImportServiceCert. bat dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c9c72-163">On the client, run ImportServiceCert.bat in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="c9c72-164">Bu, hizmet sertifikasını Service. cer dosyasından CurrentUser-Trustedkişiler deposuna aktarır.</span><span class="sxs-lookup"><span data-stu-id="c9c72-164">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
10. <span data-ttu-id="c9c72-165">Hizmet bilgisayarında, komut isteminden Service. exe ' yi başlatın.</span><span class="sxs-lookup"><span data-stu-id="c9c72-165">On the service computer, launch the Service.exe from the command prompt.</span></span>  
  
11. <span data-ttu-id="c9c72-166">İstemci bilgisayarda, bir komut isteminden Client. exe ' yi başlatın.</span><span class="sxs-lookup"><span data-stu-id="c9c72-166">On the client computer, launch Client.exe from a command prompt.</span></span> <span data-ttu-id="c9c72-167">İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="c9c72-167">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="c9c72-168">Örnekten sonra temizlemek için</span><span class="sxs-lookup"><span data-stu-id="c9c72-168">To clean up after the sample</span></span>  
  
- <span data-ttu-id="c9c72-169">Örneği çalıştırmayı bitirdikten sonra Samples klasöründe Cleanup. bat dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c9c72-169">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c9c72-170">Bu betik, bilgisayarlar arasında bu örneği çalıştırırken bir istemcideki hizmet sertifikalarını kaldırmaz.</span><span class="sxs-lookup"><span data-stu-id="c9c72-170">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="c9c72-171">Bilgisayarlar arasında sertifika kullanan Windows Communication Foundation (WCF) örneklerini çalıştırırsanız, CurrentUser-Trustedkişiler deposuna yüklenmiş olan hizmet sertifikalarını temizlediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="c9c72-171">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="c9c72-172">Bunu yapmak için aşağıdaki komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`Örneğin: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="c9c72-172">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>
