---
title: Üyelik ve Rol Sağlayıcısı
ms.date: 03/30/2017
ms.assetid: 0d11a31c-e75f-4fcf-9cf4-b7f26e056bcd
ms.openlocfilehash: e532f35a2c4cd9f53006c088956eadff616d2005
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90543595"
---
# <a name="membership-and-role-provider"></a><span data-ttu-id="ca4f8-102">Üyelik ve Rol Sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="ca4f8-102">Membership and Role Provider</span></span>
<span data-ttu-id="ca4f8-103">Üyelik ve rol sağlayıcısı örneği, bir hizmetin, istemcilerin kimliğini doğrulamak ve yetkilendirmek için ASP.NET üyeliğini ve rol sağlayıcılarını nasıl kullanabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="ca4f8-103">The Membership and Role Provider sample demonstrates how a service can use the ASP.NET membership and role providers to authenticate and authorize clients.</span></span>  
  
 <span data-ttu-id="ca4f8-104">Bu örnekte, istemci bir konsol uygulaması (. exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.</span><span class="sxs-lookup"><span data-stu-id="ca4f8-104">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ca4f8-105">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="ca4f8-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="ca4f8-106">Örnek şunu gösterir:</span><span class="sxs-lookup"><span data-stu-id="ca4f8-106">The sample demonstrates how:</span></span>  
  
- <span data-ttu-id="ca4f8-107">İstemci Kullanıcı adı-parola birleşimini kullanarak kimlik doğrulaması yapabilir.</span><span class="sxs-lookup"><span data-stu-id="ca4f8-107">A client can authenticate by using the username-password combination.</span></span>  
  
- <span data-ttu-id="ca4f8-108">Sunucu, ASP.NET üyelik sağlayıcısına karşı istemci kimlik bilgilerini doğrulayabilir.</span><span class="sxs-lookup"><span data-stu-id="ca4f8-108">The server can validate the client credentials against the ASP.NET membership provider.</span></span>  
  
- <span data-ttu-id="ca4f8-109">Sunucunun sunucu X. 509.440 sertifikası kullanılarak kimlik doğrulaması yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="ca4f8-109">The server can be authenticated by using the server's X.509 certificate.</span></span>  
  
- <span data-ttu-id="ca4f8-110">Sunucu, ASP.NET rol sağlayıcısını kullanarak kimliği doğrulanmış istemciyi bir rolle eşleyebilir.</span><span class="sxs-lookup"><span data-stu-id="ca4f8-110">The server can map the authenticated client to a role by using the ASP.NET role provider.</span></span>  
  
- <span data-ttu-id="ca4f8-111">Sunucu, `PrincipalPermissionAttribute` hizmet tarafından sunulan belirli yöntemlere erişimi denetlemek için kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="ca4f8-111">The server can use the `PrincipalPermissionAttribute` to control access to certain methods that are exposed by the service.</span></span>  
  
 <span data-ttu-id="ca4f8-112">Üyelik ve rol sağlayıcıları, SQL Server tarafından desteklenen bir depoyu kullanacak şekilde yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="ca4f8-112">The membership and role providers are configured to use a store backed by SQL Server.</span></span> <span data-ttu-id="ca4f8-113">Hizmet yapılandırma dosyasında bir bağlantı dizesi ve çeşitli seçenekler belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ca4f8-113">A connection string and various options are specified in the service configuration file.</span></span> <span data-ttu-id="ca4f8-114">`SqlMembershipProvider`Rol sağlayıcısına ad verildiğinde üyelik sağlayıcısına ad verilir `SqlRoleProvider` .</span><span class="sxs-lookup"><span data-stu-id="ca4f8-114">The membership provider is given the name `SqlMembershipProvider` while the role provider is given the name `SqlRoleProvider`.</span></span>  
  
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
  
 <span data-ttu-id="ca4f8-115">Hizmet, Web.config yapılandırma dosyası kullanılarak tanımlanan hizmetle iletişim kurmak için tek bir uç nokta sunar.</span><span class="sxs-lookup"><span data-stu-id="ca4f8-115">The service exposes a single endpoint for communicating with the service, which is defined by using the Web.config configuration file.</span></span> <span data-ttu-id="ca4f8-116">Uç nokta bir adres, bağlama ve bir anlaşmada oluşur.</span><span class="sxs-lookup"><span data-stu-id="ca4f8-116">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="ca4f8-117">Bağlama, `wsHttpBinding` Varsayılan olarak Windows kimlik doğrulamasını kullanan bir standart ile yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="ca4f8-117">The binding is configured with a standard `wsHttpBinding`, which defaults to using Windows authentication.</span></span> <span data-ttu-id="ca4f8-118">Bu örnek `wsHttpBinding` Kullanıcı adı kimlik doğrulamasını kullanmak için standart ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ca4f8-118">This sample sets the standard `wsHttpBinding` to use username authentication.</span></span> <span data-ttu-id="ca4f8-119">Davranış, sunucu sertifikasının hizmet kimlik doğrulaması için kullanılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ca4f8-119">The behavior specifies that the server certificate is to be used for service authentication.</span></span> <span data-ttu-id="ca4f8-120">Sunucu sertifikası, `SubjectName` `findValue` yapılandırma öğesindeki özniteliğiyle aynı değeri içermelidir [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) .</span><span class="sxs-lookup"><span data-stu-id="ca4f8-120">The server certificate must contain the same value for the `SubjectName` as the `findValue` attribute in the [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) configuration element.</span></span> <span data-ttu-id="ca4f8-121">Ayrıca davranış, Kullanıcı adı-parola çiftlerinin kimlik doğrulamasının ASP.NET üyelik sağlayıcısı tarafından gerçekleştirildiğini belirtir ve rol eşleme, iki sağlayıcı için tanımlanan adları belirterek ASP.NET rol sağlayıcısı tarafından gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="ca4f8-121">In addition the behavior specifies that authentication of username-password pairs is performed by the ASP.NET membership provider and role mapping is performed by the ASP.NET role provider by specifying the names defined for the two providers.</span></span>  
  
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
  
 <span data-ttu-id="ca4f8-122">Örneği çalıştırdığınızda, istemci üç farklı kullanıcı hesabı altında çeşitli hizmet işlemlerini çağırır: Gamze, Bob ve Charlie.</span><span class="sxs-lookup"><span data-stu-id="ca4f8-122">When you run the sample, the client calls the various service operations under three different user accounts: Alice, Bob, and Charlie.</span></span> <span data-ttu-id="ca4f8-123">İşlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="ca4f8-123">The operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="ca4f8-124">"Gamze" kullanıcısı olarak yapılan tüm dört çağrı başarılı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ca4f8-124">All four calls made as user "Alice" should succeed.</span></span> <span data-ttu-id="ca4f8-125">"Bob" kullanıcısının, bölme yöntemini çağırmaya çalışırken bir erişim reddedildi hatası alması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ca4f8-125">User "Bob" should get an access denied error when trying to call the Divide method.</span></span> <span data-ttu-id="ca4f8-126">"Charlie" kullanıcısının, çarpma yöntemini çağırmaya çalışırken bir erişim reddedildi hatası alması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ca4f8-126">User "Charlie" should get an access denied error when trying to call the Multiply method.</span></span> <span data-ttu-id="ca4f8-127">İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="ca4f8-127">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ca4f8-128">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="ca4f8-128">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="ca4f8-129">Çözüm için C# veya Visual Basic .NET sürümü oluşturmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="ca4f8-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
2. <span data-ttu-id="ca4f8-130">[ASP.NET uygulama Hizmetleri veritabanını](https://go.microsoft.com/fwlink/?LinkId=94997)yapılandırdığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="ca4f8-130">Ensure that you have configured the [ASP.NET Application Services Database](https://go.microsoft.com/fwlink/?LinkId=94997).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="ca4f8-131">SQL Server Express Edition çalıştırıyorsanız, sunucu adınız .\SQLEXPRESS. olur.</span><span class="sxs-lookup"><span data-stu-id="ca4f8-131">If you are running SQL Server Express Edition, your server name is .\SQLEXPRESS.</span></span> <span data-ttu-id="ca4f8-132">Bu sunucu, Web.config bağlantı dizesinde olduğu gibi, ASP.NET Uygulama Hizmetleri veritabanı yapılandırılırken de kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ca4f8-132">This server should be used when configuring the ASP.NET Application Services Database as well as in the Web.config connection string.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="ca4f8-133">ASP.NET çalışan işlem hesabının, bu adımda oluşturulan veritabanında izinleri olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ca4f8-133">The ASP.NET worker process account must have permissions on the database that is created in this step.</span></span> <span data-ttu-id="ca4f8-134">Bunu yapmak için sqlcmd yardımcı programını veya SQL Server Management Studio kullanın.</span><span class="sxs-lookup"><span data-stu-id="ca4f8-134">Use the sqlcmd utility or SQL Server Management Studio to do this.</span></span>  
  
3. <span data-ttu-id="ca4f8-135">Örneği tek veya bir çoklu bilgisayar yapılandırmasında çalıştırmak için aşağıdaki yönergeleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="ca4f8-135">To run the sample in a single- or cross-computer configuration, use the following instructions.</span></span>  
  
### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="ca4f8-136">Örneği aynı bilgisayarda çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="ca4f8-136">To run the sample on the same computer</span></span>  
  
1. <span data-ttu-id="ca4f8-137">Yolun Makecert.exe bulunduğu klasörü içerdiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="ca4f8-137">Make sure that the path includes the folder where Makecert.exe is located.</span></span>  
  
2. <span data-ttu-id="ca4f8-138">Visual Studio için Geliştirici Komut İstemi örnek install klasöründen yönetici ayrıcalıklarıyla Çalıştır ' a Setup.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ca4f8-138">Run Setup.bat from the sample install folder in a Developer Command Prompt for Visual Studio run with administrator privileges.</span></span> <span data-ttu-id="ca4f8-139">Bu, örneği çalıştırmak için gereken hizmet sertifikalarını kurar.</span><span class="sxs-lookup"><span data-stu-id="ca4f8-139">This installs the service certificates required for running the sample.</span></span>  
  
3. <span data-ttu-id="ca4f8-140">\Client\bin. 'den başlatma Client.exe</span><span class="sxs-lookup"><span data-stu-id="ca4f8-140">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="ca4f8-141">İstemci etkinliği istemci konsol uygulamasında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="ca4f8-141">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="ca4f8-142">İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="ca4f8-142">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="ca4f8-143">Örneği bilgisayarlar arasında çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="ca4f8-143">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="ca4f8-144">Hizmet bilgisayarında bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ca4f8-144">Create a directory on the service computer.</span></span> <span data-ttu-id="ca4f8-145">Internet Information Services (IIS) yönetim aracını kullanarak bu dizin için servicemodelsamples adlı bir sanal uygulama oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ca4f8-145">Create a virtual application named servicemodelsamples for this directory by using the Internet Information Services (IIS) management tool.</span></span>  
  
2. <span data-ttu-id="ca4f8-146">Hizmet programı dosyalarını \inetpub\wwwroot\servicemodelsamples adresinden hizmet bilgisayarındaki sanal dizine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="ca4f8-146">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service computer.</span></span> <span data-ttu-id="ca4f8-147">Dosyaları \bin alt dizininde kopyalamadiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="ca4f8-147">Ensure that you copy the files in the \bin subdirectory.</span></span> <span data-ttu-id="ca4f8-148">Ayrıca, Setup.bat, GetComputerName. vbs ve Cleanup.bat dosyalarını hizmet bilgisayarına kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="ca4f8-148">Also copy the Setup.bat, GetComputerName.vbs, and Cleanup.bat files to the service computer.</span></span>  
  
3. <span data-ttu-id="ca4f8-149">İstemci bilgisayarda istemci ikilileri için bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ca4f8-149">Create a directory on the client computer for the client binaries.</span></span>  
  
4. <span data-ttu-id="ca4f8-150">İstemci programı dosyalarını istemci bilgisayardaki istemci dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="ca4f8-150">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="ca4f8-151">Ayrıca Setup.bat, Cleanup.bat ve ImportServiceCert.bat dosyalarını istemciye kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="ca4f8-151">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5. <span data-ttu-id="ca4f8-152">Sunucusunda, yönetim ayrıcalıklarına sahip Visual Studio için bir Geliştirici Komut İstemi açın ve çalıştırın `setup.bat service` .</span><span class="sxs-lookup"><span data-stu-id="ca4f8-152">On the server, open a Developer Command Prompt for Visual Studio with administrative privileges and run `setup.bat service`.</span></span> <span data-ttu-id="ca4f8-153">`setup.bat`Bağımsız değişkeniyle birlikte çalıştırmak, `service` bilgisayarın tam etki alanı adına sahip bir hizmet sertifikası oluşturur ve hizmet sertifikasını Service. cer adlı bir dosyaya aktarır.</span><span class="sxs-lookup"><span data-stu-id="ca4f8-153">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
6. <span data-ttu-id="ca4f8-154">Web.config, `findValue` [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) bilgisayarın tam etki alanı adıyla aynı olan yeni sertifika adını (içindeki özniteliğinde) yansıtacak şekilde düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="ca4f8-154">Edit Web.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), which is the same as the fully-qualified domain name of the computer.</span></span>  
  
7. <span data-ttu-id="ca4f8-155">Service. cer dosyasını hizmet dizininden istemci bilgisayarındaki istemci dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="ca4f8-155">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8. <span data-ttu-id="ca4f8-156">İstemci bilgisayardaki Client.exe.config dosyasında, uç noktanın adres değerini hizmetinizin yeni adresiyle eşleşecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="ca4f8-156">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="ca4f8-157">İstemcisinde, yönetim ayrıcalıklarına sahip bir Visual Studio Geliştirici Komut İstemi açın ve ImportServiceCert.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ca4f8-157">On the client, open a Developer Command Prompt for Visual Studio with administrative privileges and run ImportServiceCert.bat.</span></span> <span data-ttu-id="ca4f8-158">Bu, hizmet sertifikasını Service. cer dosyasından CurrentUser-Trustedkişiler deposuna aktarır.</span><span class="sxs-lookup"><span data-stu-id="ca4f8-158">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
10. <span data-ttu-id="ca4f8-159">İstemci bilgisayarda, bir komut isteminden Client.exe başlatın.</span><span class="sxs-lookup"><span data-stu-id="ca4f8-159">On the client computer, launch Client.exe from a command prompt.</span></span> <span data-ttu-id="ca4f8-160">İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="ca4f8-160">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="ca4f8-161">Örnekten sonra temizlemek için</span><span class="sxs-lookup"><span data-stu-id="ca4f8-161">To clean up after the sample</span></span>  
  
- <span data-ttu-id="ca4f8-162">Örneği çalıştırmayı bitirdikten sonra Samples klasöründe Cleanup.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ca4f8-162">Run Cleanup.bat in the samples folder after you have finished running the sample.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ca4f8-163">Bu betik, bilgisayarlar arasında bu örneği çalıştırırken bir istemcideki hizmet sertifikalarını kaldırmaz.</span><span class="sxs-lookup"><span data-stu-id="ca4f8-163">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="ca4f8-164">Bilgisayarlar arasında sertifika kullanan Windows Communication Foundation (WCF) örneklerini çalıştırırsanız, CurrentUser-Trustedkişiler deposuna yüklenmiş olan hizmet sertifikalarını temizlediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="ca4f8-164">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="ca4f8-165">Bunu yapmak için şu komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` Örneğin: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com` .</span><span class="sxs-lookup"><span data-stu-id="ca4f8-165">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
  
## <a name="the-setup-batch-file"></a><span data-ttu-id="ca4f8-166">Kurulum toplu Iş dosyası</span><span class="sxs-lookup"><span data-stu-id="ca4f8-166">The Setup Batch File</span></span>  
 <span data-ttu-id="ca4f8-167">Bu örneğe eklenen Setup.bat Batch dosyası, sunucu sertifika tabanlı güvenlik gerektiren şirket içinde barındırılan bir uygulamayı çalıştırmak için sunucuyu ilgili sertifikalarla yapılandırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="ca4f8-167">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="ca4f8-168">Bu toplu iş dosyasının bilgisayarlarda çalışmak veya barındırılmayan bir durumda çalışması için değiştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="ca4f8-168">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>  
  
 <span data-ttu-id="ca4f8-169">Aşağıdakiler, uygun yapılandırmada çalışacak şekilde değiştirilebilecek şekilde, toplu iş dosyalarının farklı bölümlerine kısa bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="ca4f8-169">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration.</span></span>  
  
- <span data-ttu-id="ca4f8-170">Sunucu sertifikası oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="ca4f8-170">Creating the server certificate.</span></span>  
  
     <span data-ttu-id="ca4f8-171">Setup.bat Batch dosyasından aşağıdaki satırlar kullanılacak sunucu sertifikasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ca4f8-171">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="ca4f8-172">% SERVER_NAME% değişkeni sunucu adını belirtiyor.</span><span class="sxs-lookup"><span data-stu-id="ca4f8-172">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="ca4f8-173">Kendi sunucu adınızı belirtmek için bu değişkeni değiştirin.</span><span class="sxs-lookup"><span data-stu-id="ca4f8-173">Change this variable to specify your own server name.</span></span> <span data-ttu-id="ca4f8-174">Bu toplu iş dosyası varsayılan olarak localhost 'tur.</span><span class="sxs-lookup"><span data-stu-id="ca4f8-174">This batch file defaults it to localhost.</span></span>  
  
     <span data-ttu-id="ca4f8-175">Sertifika, LocalMachine depolama konumu altında (kişisel) deposunda depolanır.</span><span class="sxs-lookup"><span data-stu-id="ca4f8-175">The certificate is stored in My (Personal) store under the LocalMachine store location.</span></span>  
  
    ```console
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
- <span data-ttu-id="ca4f8-176">Sunucu sertifikasını istemcinin güvenilen sertifika deposuna yükleme.</span><span class="sxs-lookup"><span data-stu-id="ca4f8-176">Installing the server certificate into the client's trusted certificate store.</span></span>  
  
     <span data-ttu-id="ca4f8-177">Setup.bat Batch dosyasındaki aşağıdaki satırlar, sunucu sertifikasını istemci güvenilir kişiler deposuna kopyalar.</span><span class="sxs-lookup"><span data-stu-id="ca4f8-177">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="ca4f8-178">Makecert.exe tarafından oluşturulan sertifikalara istemci sistemi tarafından örtük olarak güvenilmediğinden Bu adım gereklidir.</span><span class="sxs-lookup"><span data-stu-id="ca4f8-178">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="ca4f8-179">İstemci tarafından güvenilen kök sertifikada kök sertifikaya sahip bir sertifikanız zaten varsa (örneğin, Microsoft tarafından verilen bir sertifika), istemci sertifikası deposunu sunucu sertifikasıyla doldurmanın bu adımı gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="ca4f8-179">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```bat  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```
