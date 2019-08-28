---
title: Üyelik ve Rol Sağlayıcısı
ms.date: 03/30/2017
ms.assetid: 0d11a31c-e75f-4fcf-9cf4-b7f26e056bcd
ms.openlocfilehash: 139d85a1ec36509690f35f24c7ddf04716a7e909
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70039448"
---
# <a name="membership-and-role-provider"></a><span data-ttu-id="f774c-102">Üyelik ve Rol Sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="f774c-102">Membership and Role Provider</span></span>
<span data-ttu-id="f774c-103">Üyelik ve rol sağlayıcısı örneği, bir hizmetin, istemcilerin kimliğini doğrulamak ve yetkilendirmek için ASP.NET üyeliğini ve rol sağlayıcılarını nasıl kullanabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="f774c-103">The Membership and Role Provider sample demonstrates how a service can use the ASP.NET membership and role providers to authenticate and authorize clients.</span></span>  
  
 <span data-ttu-id="f774c-104">Bu örnekte, istemci bir konsol uygulaması (. exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.</span><span class="sxs-lookup"><span data-stu-id="f774c-104">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f774c-105">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="f774c-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="f774c-106">Örnek şunu gösterir:</span><span class="sxs-lookup"><span data-stu-id="f774c-106">The sample demonstrates how:</span></span>  
  
- <span data-ttu-id="f774c-107">İstemci Kullanıcı adı-parola birleşimini kullanarak kimlik doğrulaması yapabilir.</span><span class="sxs-lookup"><span data-stu-id="f774c-107">A client can authenticate by using the username-password combination.</span></span>  
  
- <span data-ttu-id="f774c-108">Sunucu, ASP.NET üyelik sağlayıcısına karşı istemci kimlik bilgilerini doğrulayabilir.</span><span class="sxs-lookup"><span data-stu-id="f774c-108">The server can validate the client credentials against the ASP.NET membership provider.</span></span>  
  
- <span data-ttu-id="f774c-109">Sunucunun sunucu X. 509.440 sertifikası kullanılarak kimlik doğrulaması yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="f774c-109">The server can be authenticated by using the server's X.509 certificate.</span></span>  
  
- <span data-ttu-id="f774c-110">Sunucu, ASP.NET rol sağlayıcısını kullanarak kimliği doğrulanmış istemciyi bir rolle eşleyebilir.</span><span class="sxs-lookup"><span data-stu-id="f774c-110">The server can map the authenticated client to a role by using the ASP.NET role provider.</span></span>  
  
- <span data-ttu-id="f774c-111">Sunucu, `PrincipalPermissionAttribute` hizmet tarafından sunulan belirli yöntemlere erişimi denetlemek için kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="f774c-111">The server can use the `PrincipalPermissionAttribute` to control access to certain methods that are exposed by the service.</span></span>  
  
 <span data-ttu-id="f774c-112">Üyelik ve rol sağlayıcıları, SQL Server tarafından desteklenen bir depoyu kullanacak şekilde yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="f774c-112">The membership and role providers are configured to use a store backed by SQL Server.</span></span> <span data-ttu-id="f774c-113">Hizmet yapılandırma dosyasında bir bağlantı dizesi ve çeşitli seçenekler belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f774c-113">A connection string and various options are specified in the service configuration file.</span></span> <span data-ttu-id="f774c-114">Rol sağlayıcısına ad `SqlRoleProvider`verildiğinde üyelik sağlayıcısına ad `SqlMembershipProvider` verilir.</span><span class="sxs-lookup"><span data-stu-id="f774c-114">The membership provider is given the name `SqlMembershipProvider` while the role provider is given the name `SqlRoleProvider`.</span></span>  
  
```xml  
<!-- Set the connection string for SQL Server -->  
<connectionStrings>  
  <add name="SqlConn"   
       connectionString="Data Source=localhost;Integrated Security=SSPI;Initial Catalog=aspnetdb;" />  
</connectionStrings>  
  
<system.web>  
  <!-- Configure the Sql Membership Provider -->  
  <membership defaultProvider="SqlMembershipProvider" userIsOnlineTimeWindow="15">  
    <providers>  
      <clear />  
      <add   
        name="SqlMembershipProvider"   
        type="System.Web.Security.SqlMembershipProvider"   
        connectionStringName="SqlConn"  
        applicationName="MembershipAndRoleProviderSample"  
        enablePasswordRetrieval="false"  
        enablePasswordReset="false"  
        requiresQuestionAndAnswer="false"  
        requiresUniqueEmail="true"  
        passwordFormat="Hashed" />  
    </providers>  
  </membership>  
  
  <!-- Configure the Sql Role Provider -->  
  <roleManager enabled ="true"   
               defaultProvider ="SqlRoleProvider" >  
    <providers>  
      <add name ="SqlRoleProvider"   
           type="System.Web.Security.SqlRoleProvider"   
           connectionStringName="SqlConn"   
           applicationName="MembershipAndRoleProviderSample"/>  
    </providers>  
  </roleManager>  
</system.web>  
```  
  
 <span data-ttu-id="f774c-115">Hizmet, Web. config yapılandırma dosyası kullanılarak tanımlanan hizmetle iletişim kurmak için tek bir uç nokta sunar.</span><span class="sxs-lookup"><span data-stu-id="f774c-115">The service exposes a single endpoint for communicating with the service, which is defined by using the Web.config configuration file.</span></span> <span data-ttu-id="f774c-116">Uç nokta bir adres, bağlama ve bir anlaşmada oluşur.</span><span class="sxs-lookup"><span data-stu-id="f774c-116">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="f774c-117">Bağlama, varsayılan olarak Windows kimlik doğrulamasını `wsHttpBinding`kullanan bir standart ile yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="f774c-117">The binding is configured with a standard `wsHttpBinding`, which defaults to using Windows authentication.</span></span> <span data-ttu-id="f774c-118">Bu örnek Kullanıcı adı kimlik `wsHttpBinding` doğrulamasını kullanmak için standart ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f774c-118">This sample sets the standard `wsHttpBinding` to use username authentication.</span></span> <span data-ttu-id="f774c-119">Davranış, sunucu sertifikasının hizmet kimlik doğrulaması için kullanılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f774c-119">The behavior specifies that the server certificate is to be used for service authentication.</span></span> <span data-ttu-id="f774c-120">Sunucu sertifikası, `SubjectName` `findValue` [ServiceCertificate > yapılandırma öğesinde özniteliğiyle aynı değeri içermelidir. \<](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="f774c-120">The server certificate must contain the same value for the `SubjectName` as the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) configuration element.</span></span> <span data-ttu-id="f774c-121">Ayrıca davranış, Kullanıcı adı-parola çiftlerinin kimlik doğrulamasının ASP.NET üyelik sağlayıcısı tarafından gerçekleştirildiğini belirtir ve rol eşleme, iki sağlayıcı için tanımlanan adları belirterek ASP.NET rol sağlayıcısı tarafından gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="f774c-121">In addition the behavior specifies that authentication of username-password pairs is performed by the ASP.NET membership provider and role mapping is performed by the ASP.NET role provider by specifying the names defined for the two providers.</span></span>  
  
```xml  
<system.serviceModel>  
  
  <protocolMapping>  
    <add scheme="http" binding="wsHttpBinding" />  
  </protocolMapping>  
  
  <bindings>  
    <wsHttpBinding>  
      <!-- Set up a binding that uses Username as the client credential type -->  
      <binding>  
        <security mode ="Message">  
          <message clientCredentialType ="UserName"/>  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
  
  <behaviors>  
    <serviceBehaviors>  
      <behavior>  
        <!-- Configure role based authorization to use the Role Provider -->  
        <serviceAuthorization principalPermissionMode ="UseAspNetRoles"  
                              roleProviderName ="SqlRoleProvider" />  
        <serviceCredentials>  
          <!-- Configure user name authentication to use the Membership Provider -->  
          <userNameAuthentication userNamePasswordValidationMode ="MembershipProvider"   
                                  membershipProviderName ="SqlMembershipProvider"/>  
          <!-- Configure the service certificate -->  
          <serviceCertificate storeLocation ="LocalMachine"   
                              storeName ="My"   
                              x509FindType ="FindBySubjectName"  
                              findValue ="localhost" />  
        </serviceCredentials>  
        <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
        <serviceDebug includeExceptionDetailInFaults="false" />  
        <serviceMetadata httpGetEnabled="true"/>  
      </behavior>  
    </serviceBehaviors>  
  </behaviors>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="f774c-122">Örneği çalıştırdığınızda, istemci üç farklı kullanıcı hesabı altında çeşitli hizmet işlemlerini çağırır: Çiğdem, Bob ve Charlie.</span><span class="sxs-lookup"><span data-stu-id="f774c-122">When you run the sample, the client calls the various service operations under three different user accounts: Alice, Bob, and Charlie.</span></span> <span data-ttu-id="f774c-123">İşlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="f774c-123">The operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="f774c-124">"Gamze" kullanıcısı olarak yapılan tüm dört çağrı başarılı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f774c-124">All four calls made as user "Alice" should succeed.</span></span> <span data-ttu-id="f774c-125">"Bob" kullanıcısının, bölme yöntemini çağırmaya çalışırken bir erişim reddedildi hatası alması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f774c-125">User "Bob" should get an access denied error when trying to call the Divide method.</span></span> <span data-ttu-id="f774c-126">"Charlie" kullanıcısının, çarpma yöntemini çağırmaya çalışırken bir erişim reddedildi hatası alması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f774c-126">User "Charlie" should get an access denied error when trying to call the Multiply method.</span></span> <span data-ttu-id="f774c-127">İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="f774c-127">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f774c-128">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="f774c-128">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="f774c-129">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="f774c-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
2. <span data-ttu-id="f774c-130">[ASP.NET uygulama Hizmetleri veritabanını](https://go.microsoft.com/fwlink/?LinkId=94997)yapılandırdığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="f774c-130">Ensure that you have configured the [ASP.NET Application Services Database](https://go.microsoft.com/fwlink/?LinkId=94997).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="f774c-131">SQL Server Express Edition çalıştırıyorsanız, sunucu adınız .\SQLEXPRESS. olur.</span><span class="sxs-lookup"><span data-stu-id="f774c-131">If you are running SQL Server Express Edition, your server name is .\SQLEXPRESS.</span></span> <span data-ttu-id="f774c-132">Bu sunucu, ASP.NET Uygulama Hizmetleri veritabanı ve Web. config bağlantı dizesinde yapılandırılırken kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f774c-132">This server should be used when configuring the ASP.NET Application Services Database as well as in the Web.config connection string.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="f774c-133">ASP.NET çalışan işlem hesabının, bu adımda oluşturulan veritabanında izinleri olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f774c-133">The ASP.NET worker process account must have permissions on the database that is created in this step.</span></span> <span data-ttu-id="f774c-134">Bunu yapmak için sqlcmd yardımcı programını veya SQL Server Management Studio kullanın.</span><span class="sxs-lookup"><span data-stu-id="f774c-134">Use the sqlcmd utility or SQL Server Management Studio to do this.</span></span>  
  
3. <span data-ttu-id="f774c-135">Örneği tek veya bir çoklu bilgisayar yapılandırmasında çalıştırmak için aşağıdaki yönergeleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="f774c-135">To run the sample in a single- or cross-computer configuration, use the following instructions.</span></span>  
  
### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="f774c-136">Örneği aynı bilgisayarda çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="f774c-136">To run the sample on the same computer</span></span>  
  
1. <span data-ttu-id="f774c-137">Yolun, MakeCert. exe ' nin bulunduğu klasörü içerdiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="f774c-137">Make sure that the path includes the folder where Makecert.exe is located.</span></span>  
  
2. <span data-ttu-id="f774c-138">Visual Studio 'nun yönetici ayrıcalıklarıyla çalışması için Geliştirici Komut İstemi örnek yükleme klasöründen Setup. bat dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="f774c-138">Run Setup.bat from the sample install folder in a Developer Command Prompt for Visual Studio run with administrator privileges.</span></span> <span data-ttu-id="f774c-139">Bu, örneği çalıştırmak için gereken hizmet sertifikalarını kurar.</span><span class="sxs-lookup"><span data-stu-id="f774c-139">This installs the service certificates required for running the sample.</span></span>  
  
3. <span data-ttu-id="f774c-140">\Client\bin. adresinden Client. exe ' yi Başlat</span><span class="sxs-lookup"><span data-stu-id="f774c-140">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="f774c-141">İstemci etkinliği istemci konsol uygulamasında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="f774c-141">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="f774c-142">İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="f774c-142">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="f774c-143">Örneği bilgisayarlar arasında çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="f774c-143">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="f774c-144">Hizmet bilgisayarında bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f774c-144">Create a directory on the service computer.</span></span> <span data-ttu-id="f774c-145">Internet Information Services (IIS) yönetim aracını kullanarak bu dizin için servicemodelsamples adlı bir sanal uygulama oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f774c-145">Create a virtual application named servicemodelsamples for this directory by using the Internet Information Services (IIS) management tool.</span></span>  
  
2. <span data-ttu-id="f774c-146">Hizmet programı dosyalarını \inetpub\wwwroot\servicemodelsamples adresinden hizmet bilgisayarındaki sanal dizine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="f774c-146">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service computer.</span></span> <span data-ttu-id="f774c-147">Dosyaları \bin alt dizininde kopyalamadiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="f774c-147">Ensure that you copy the files in the \bin subdirectory.</span></span> <span data-ttu-id="f774c-148">Ayrıca Setup. bat, GetComputerName. vbs ve Cleanup. bat dosyalarını da hizmet bilgisayarına kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="f774c-148">Also copy the Setup.bat, GetComputerName.vbs, and Cleanup.bat files to the service computer.</span></span>  
  
3. <span data-ttu-id="f774c-149">İstemci bilgisayarda istemci ikilileri için bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f774c-149">Create a directory on the client computer for the client binaries.</span></span>  
  
4. <span data-ttu-id="f774c-150">İstemci programı dosyalarını istemci bilgisayardaki istemci dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="f774c-150">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="f774c-151">Ayrıca Setup. bat, Cleanup. bat ve ImportServiceCert. bat dosyalarını istemciye kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="f774c-151">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5. <span data-ttu-id="f774c-152">Sunucusunda, yönetim ayrıcalıklarına sahip Visual Studio için bir Geliştirici Komut İstemi açın ve çalıştırın `setup.bat service`.</span><span class="sxs-lookup"><span data-stu-id="f774c-152">On the server, open a Developer Command Prompt for Visual Studio with administrative privileges and run `setup.bat service`.</span></span> <span data-ttu-id="f774c-153">Bağımsız`service` değişkeniyle birlikte çalıştırmak `setup.bat` , bilgisayarın tam etki alanı adına sahip bir hizmet sertifikası oluşturur ve hizmet sertifikasını Service. cer adlı bir dosyaya aktarır.</span><span class="sxs-lookup"><span data-stu-id="f774c-153">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
6. <span data-ttu-id="f774c-154">Web. config dosyasını, bilgisayarın tam etki alanı adıyla aynı olan yeni `findValue` sertifika adını ( [ \<ServiceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)özniteliğinde) yansıtacak şekilde düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="f774c-154">Edit Web.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), which is the same as the fully-qualified domain name of the computer.</span></span>  
  
7. <span data-ttu-id="f774c-155">Service. cer dosyasını hizmet dizininden istemci bilgisayarındaki istemci dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="f774c-155">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8. <span data-ttu-id="f774c-156">İstemci bilgisayardaki Client. exe. config dosyasında, uç noktanın adres değerini hizmetinizin yeni adresiyle eşleşecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="f774c-156">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="f774c-157">İstemcisinde, yönetim ayrıcalıklarına sahip bir Visual Studio Geliştirici Komut İstemi açın ve ImportServiceCert. bat dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="f774c-157">On the client, open a Developer Command Prompt for Visual Studio with administrative privileges and run ImportServiceCert.bat.</span></span> <span data-ttu-id="f774c-158">Bu, hizmet sertifikasını Service. cer dosyasından CurrentUser-Trustedkişiler deposuna aktarır.</span><span class="sxs-lookup"><span data-stu-id="f774c-158">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
10. <span data-ttu-id="f774c-159">İstemci bilgisayarda, bir komut isteminden Client. exe ' yi başlatın.</span><span class="sxs-lookup"><span data-stu-id="f774c-159">On the client computer, launch Client.exe from a command prompt.</span></span> <span data-ttu-id="f774c-160">İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="f774c-160">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="f774c-161">Örnekten sonra temizlemek için</span><span class="sxs-lookup"><span data-stu-id="f774c-161">To clean up after the sample</span></span>  
  
- <span data-ttu-id="f774c-162">Örneği çalıştırmayı bitirdikten sonra Samples klasöründe Cleanup. bat dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="f774c-162">Run Cleanup.bat in the samples folder after you have finished running the sample.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f774c-163">Bu betik, bilgisayarlar arasında bu örneği çalıştırırken bir istemcideki hizmet sertifikalarını kaldırmaz.</span><span class="sxs-lookup"><span data-stu-id="f774c-163">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="f774c-164">Bilgisayarlar arasında sertifika kullanan Windows Communication Foundation (WCF) örneklerini çalıştırırsanız, CurrentUser-Trustedkişiler deposuna yüklenmiş olan hizmet sertifikalarını temizlediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="f774c-164">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="f774c-165">Bunu yapmak için aşağıdaki komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`Örneğin: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="f774c-165">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
  
## <a name="the-setup-batch-file"></a><span data-ttu-id="f774c-166">Kurulum toplu Iş dosyası</span><span class="sxs-lookup"><span data-stu-id="f774c-166">The Setup Batch File</span></span>  
 <span data-ttu-id="f774c-167">Bu örneğe eklenen Setup. bat toplu iş dosyası, sunucu sertifika tabanlı güvenlik gerektiren şirket içinde barındırılan bir uygulamayı çalıştırmak için sunucuyu ilgili sertifikalarla yapılandırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="f774c-167">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="f774c-168">Bu toplu iş dosyasının bilgisayarlarda çalışmak veya barındırılmayan bir durumda çalışması için değiştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="f774c-168">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>  
  
 <span data-ttu-id="f774c-169">Aşağıdakiler, uygun yapılandırmada çalışacak şekilde değiştirilebilecek şekilde, toplu iş dosyalarının farklı bölümlerine kısa bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="f774c-169">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration.</span></span>  
  
- <span data-ttu-id="f774c-170">Sunucu sertifikası oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="f774c-170">Creating the server certificate.</span></span>  
  
     <span data-ttu-id="f774c-171">Setup. bat toplu iş dosyasından aşağıdaki satırlar kullanılacak sunucu sertifikasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f774c-171">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="f774c-172">% SERVER_NAME% değişkeni sunucu adını belirtiyor.</span><span class="sxs-lookup"><span data-stu-id="f774c-172">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="f774c-173">Kendi sunucu adınızı belirtmek için bu değişkeni değiştirin.</span><span class="sxs-lookup"><span data-stu-id="f774c-173">Change this variable to specify your own server name.</span></span> <span data-ttu-id="f774c-174">Bu toplu iş dosyası varsayılan olarak localhost 'tur.</span><span class="sxs-lookup"><span data-stu-id="f774c-174">This batch file defaults it to localhost.</span></span>  
  
     <span data-ttu-id="f774c-175">Sertifika, LocalMachine depolama konumu altında (kişisel) deposunda depolanır.</span><span class="sxs-lookup"><span data-stu-id="f774c-175">The certificate is stored in My (Personal) store under the LocalMachine store location.</span></span>  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
- <span data-ttu-id="f774c-176">Sunucu sertifikasını istemcinin güvenilen sertifika deposuna yükleme.</span><span class="sxs-lookup"><span data-stu-id="f774c-176">Installing the server certificate into the client's trusted certificate store.</span></span>  
  
     <span data-ttu-id="f774c-177">Setup. bat toplu iş dosyası 'ndaki aşağıdaki satırlar, sunucu sertifikasını istemci güvenilir kişiler deposuna kopyalar.</span><span class="sxs-lookup"><span data-stu-id="f774c-177">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="f774c-178">Bu adım, MakeCert. exe tarafından oluşturulan sertifikaların istemci sistemi tarafından örtük olarak güvenilir olmadığından gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f774c-178">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="f774c-179">İstemci tarafından güvenilen kök sertifikada kök sertifikaya sahip bir sertifikanız zaten varsa (örneğin, Microsoft tarafından verilen bir sertifika), istemci sertifikası deposunu sunucu sertifikasıyla doldurmanın bu adımı gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="f774c-179">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
