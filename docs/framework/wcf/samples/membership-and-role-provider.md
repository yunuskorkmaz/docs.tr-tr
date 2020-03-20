---
title: Üyelik ve Rol Sağlayıcısı
ms.date: 03/30/2017
ms.assetid: 0d11a31c-e75f-4fcf-9cf4-b7f26e056bcd
ms.openlocfilehash: 117be783c2d4a72ff9d1c4509566274b1043a43d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144467"
---
# <a name="membership-and-role-provider"></a><span data-ttu-id="c892c-102">Üyelik ve Rol Sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="c892c-102">Membership and Role Provider</span></span>
<span data-ttu-id="c892c-103">Üyelik ve Rol Sağlayıcı örneği, bir hizmetin ASP.NET üyeliği ve rol sağlayıcıları istemcileri doğrulamak ve yetkilendirmek için nasıl kullanabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c892c-103">The Membership and Role Provider sample demonstrates how a service can use the ASP.NET membership and role providers to authenticate and authorize clients.</span></span>  
  
 <span data-ttu-id="c892c-104">Bu örnekte, istemci bir konsol uygulamasıdır (.exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.</span><span class="sxs-lookup"><span data-stu-id="c892c-104">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c892c-105">Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="c892c-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="c892c-106">Örnek, aşağıdakileri gösterir:</span><span class="sxs-lookup"><span data-stu-id="c892c-106">The sample demonstrates how:</span></span>  
  
- <span data-ttu-id="c892c-107">İstemci, kullanıcı adı-parola birleşimini kullanarak kimlik doğrulaması yapabilir.</span><span class="sxs-lookup"><span data-stu-id="c892c-107">A client can authenticate by using the username-password combination.</span></span>  
  
- <span data-ttu-id="c892c-108">Sunucu, istemci kimlik bilgilerini ASP.NET üyelik sağlayıcısına karşı doğrulayabilir.</span><span class="sxs-lookup"><span data-stu-id="c892c-108">The server can validate the client credentials against the ASP.NET membership provider.</span></span>  
  
- <span data-ttu-id="c892c-109">Sunucunun X.509 sertifikası kullanılarak sunucunun kimliği doğrulanabilir.</span><span class="sxs-lookup"><span data-stu-id="c892c-109">The server can be authenticated by using the server's X.509 certificate.</span></span>  
  
- <span data-ttu-id="c892c-110">Sunucu, ASP.NET rol sağlayıcısını kullanarak kimlik doğrulaması yapılan istemciyi bir role eşleyebilir.</span><span class="sxs-lookup"><span data-stu-id="c892c-110">The server can map the authenticated client to a role by using the ASP.NET role provider.</span></span>  
  
- <span data-ttu-id="c892c-111">Sunucu, hizmet `PrincipalPermissionAttribute` tarafından açığa çıkarılan belirli yöntemlere erişimi denetlemek için kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="c892c-111">The server can use the `PrincipalPermissionAttribute` to control access to certain methods that are exposed by the service.</span></span>  
  
 <span data-ttu-id="c892c-112">Üyelik ve rol sağlayıcıları, SQL Server tarafından desteklenen bir depoyu kullanacak şekilde yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="c892c-112">The membership and role providers are configured to use a store backed by SQL Server.</span></span> <span data-ttu-id="c892c-113">Hizmet yapılandırma dosyasında bir bağlantı dizesi ve çeşitli seçenekler belirtilir.</span><span class="sxs-lookup"><span data-stu-id="c892c-113">A connection string and various options are specified in the service configuration file.</span></span> <span data-ttu-id="c892c-114">Rol sağlayıcısına ad `SqlMembershipProvider` `SqlRoleProvider`verilirken, üyelik sağlayıcısına ad verilir.</span><span class="sxs-lookup"><span data-stu-id="c892c-114">The membership provider is given the name `SqlMembershipProvider` while the role provider is given the name `SqlRoleProvider`.</span></span>  
  
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
  
 <span data-ttu-id="c892c-115">Hizmet, Web.config yapılandırma dosyasını kullanarak tanımlanan hizmetle iletişim kurmak için tek bir bitiş noktasını ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="c892c-115">The service exposes a single endpoint for communicating with the service, which is defined by using the Web.config configuration file.</span></span> <span data-ttu-id="c892c-116">Bitiş noktası bir adres, bir bağlama ve sözleşmeden oluşur.</span><span class="sxs-lookup"><span data-stu-id="c892c-116">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="c892c-117">Bağlama, Windows kimlik doğrulaması kullanmaya varsayılan bir standartla `wsHttpBinding`yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="c892c-117">The binding is configured with a standard `wsHttpBinding`, which defaults to using Windows authentication.</span></span> <span data-ttu-id="c892c-118">Bu örnek, `wsHttpBinding` kullanıcı adı kimlik doğrulaması kullanmak için standart ayarlar.</span><span class="sxs-lookup"><span data-stu-id="c892c-118">This sample sets the standard `wsHttpBinding` to use username authentication.</span></span> <span data-ttu-id="c892c-119">Davranış, sunucu sertifikasının hizmet kimlik doğrulaması için kullanılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c892c-119">The behavior specifies that the server certificate is to be used for service authentication.</span></span> <span data-ttu-id="c892c-120">Sunucu sertifikası, [ \<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) `SubjectName` yapılandırma `findValue` öğesindeki öznitelikle aynı değeri içermelidir.</span><span class="sxs-lookup"><span data-stu-id="c892c-120">The server certificate must contain the same value for the `SubjectName` as the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) configuration element.</span></span> <span data-ttu-id="c892c-121">Buna ek olarak, kullanıcı adı-parola çiftleri kimlik doğrulamasının ASP.NET üyelik sağlayıcısı tarafından gerçekleştirildiğini ve rol eşlemenin ASP.NET rol sağlayıcısı tarafından iki sağlayıcı için tanımlanan adlar belirtilerek gerçekleştirildiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c892c-121">In addition the behavior specifies that authentication of username-password pairs is performed by the ASP.NET membership provider and role mapping is performed by the ASP.NET role provider by specifying the names defined for the two providers.</span></span>  
  
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
  
 <span data-ttu-id="c892c-122">Örneği çalıştırdığınızda, istemci üç farklı kullanıcı hesabı altında çeşitli hizmet işlemlerini çağırır: Alice, Bob ve Charlie.</span><span class="sxs-lookup"><span data-stu-id="c892c-122">When you run the sample, the client calls the various service operations under three different user accounts: Alice, Bob, and Charlie.</span></span> <span data-ttu-id="c892c-123">İşlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="c892c-123">The operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="c892c-124">Kullanıcı "Alice" olarak yapılan dört aramanın tümü başarılı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c892c-124">All four calls made as user "Alice" should succeed.</span></span> <span data-ttu-id="c892c-125">Kullanıcı "Bob" B) yöntemini aramaya çalışırken erişim reddedilen bir hata almalıdır.</span><span class="sxs-lookup"><span data-stu-id="c892c-125">User "Bob" should get an access denied error when trying to call the Divide method.</span></span> <span data-ttu-id="c892c-126">Kullanıcı "Charlie" Çarpma yöntemini aramaya çalışırken erişim reddedilen bir hata almalıdır.</span><span class="sxs-lookup"><span data-stu-id="c892c-126">User "Charlie" should get an access denied error when trying to call the Multiply method.</span></span> <span data-ttu-id="c892c-127">İstemciyi kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="c892c-127">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c892c-128">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="c892c-128">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="c892c-129">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için Windows Communication Foundation Örneklerini Çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="c892c-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
2. <span data-ttu-id="c892c-130">[ASP.NET Uygulama Hizmetleri Veritabanını](https://go.microsoft.com/fwlink/?LinkId=94997)yapılandırdığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="c892c-130">Ensure that you have configured the [ASP.NET Application Services Database](https://go.microsoft.com/fwlink/?LinkId=94997).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="c892c-131">SQL Server Express Edition çalıştırıyorsanız, sunucu adınız .\SQLEXPRESS'tir.</span><span class="sxs-lookup"><span data-stu-id="c892c-131">If you are running SQL Server Express Edition, your server name is .\SQLEXPRESS.</span></span> <span data-ttu-id="c892c-132">Bu sunucu, ASP.NET Uygulama Hizmetleri Veritabanı'nı ve Web.config bağlantı dizesini yapılandırırken kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c892c-132">This server should be used when configuring the ASP.NET Application Services Database as well as in the Web.config connection string.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="c892c-133">ASP.NET işlemesi hesabının bu adımda oluşturulan veritabanında izinleri olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c892c-133">The ASP.NET worker process account must have permissions on the database that is created in this step.</span></span> <span data-ttu-id="c892c-134">Bunu yapmak için sqlcmd yardımcı programını veya SQL Server Management Studio'yu kullanın.</span><span class="sxs-lookup"><span data-stu-id="c892c-134">Use the sqlcmd utility or SQL Server Management Studio to do this.</span></span>  
  
3. <span data-ttu-id="c892c-135">Örneği tek veya bilgisayar lar arası yapılandırmada çalıştırmak için aşağıdaki yönergeleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="c892c-135">To run the sample in a single- or cross-computer configuration, use the following instructions.</span></span>  
  
### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="c892c-136">Örneği aynı bilgisayarda çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="c892c-136">To run the sample on the same computer</span></span>  
  
1. <span data-ttu-id="c892c-137">Yolun Makecert.exe'nin bulunduğu klasörü içerdiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="c892c-137">Make sure that the path includes the folder where Makecert.exe is located.</span></span>  
  
2. <span data-ttu-id="c892c-138">Setup.bat'ı visual studio için Geliştirici Komut Komut Ustem'de yönetici ayrıcalıklarıyla çalıştırın örnek yükleme klasöründen çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c892c-138">Run Setup.bat from the sample install folder in a Developer Command Prompt for Visual Studio run with administrator privileges.</span></span> <span data-ttu-id="c892c-139">Bu, örneği çalıştırmak için gereken hizmet sertifikalarını yükler.</span><span class="sxs-lookup"><span data-stu-id="c892c-139">This installs the service certificates required for running the sample.</span></span>  
  
3. <span data-ttu-id="c892c-140">Client.exe'yi \client\bin'den başlatın.</span><span class="sxs-lookup"><span data-stu-id="c892c-140">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="c892c-141">İstemci etkinliği istemci konsoluygulamasında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="c892c-141">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="c892c-142">İstemci ve hizmet iletişim kuramazsa, [WCF Örnekleri için Sorun Giderme İpuçları'na](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))bakın.</span><span class="sxs-lookup"><span data-stu-id="c892c-142">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="c892c-143">Örneği bilgisayarlarda çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="c892c-143">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="c892c-144">Hizmet bilgisayarında bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c892c-144">Create a directory on the service computer.</span></span> <span data-ttu-id="c892c-145">Internet Information Services (IIS) yönetim aracını kullanarak bu dizin için servicemodelsamples adlı sanal bir uygulama oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c892c-145">Create a virtual application named servicemodelsamples for this directory by using the Internet Information Services (IIS) management tool.</span></span>  
  
2. <span data-ttu-id="c892c-146">Hizmet programı dosyalarını \inetpub\wwwroot\servicemodelsamples'ten hizmet bilgisayarındaki sanal dizine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="c892c-146">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service computer.</span></span> <span data-ttu-id="c892c-147">\bin alt dizinindeki dosyaları kopyaladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="c892c-147">Ensure that you copy the files in the \bin subdirectory.</span></span> <span data-ttu-id="c892c-148">Ayrıca Setup.bat, GetComputerName.vbs ve Cleanup.bat dosyalarını servis bilgisayarına kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="c892c-148">Also copy the Setup.bat, GetComputerName.vbs, and Cleanup.bat files to the service computer.</span></span>  
  
3. <span data-ttu-id="c892c-149">İstemci ikilileri için istemci bilgisayarında bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c892c-149">Create a directory on the client computer for the client binaries.</span></span>  
  
4. <span data-ttu-id="c892c-150">İstemci programı dosyalarını istemci bilgisayarındaki istemci dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="c892c-150">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="c892c-151">Ayrıca Setup.bat, Cleanup.bat ve ImportServiceCert.bat dosyalarını istemciye kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="c892c-151">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5. <span data-ttu-id="c892c-152">Sunucuda, yönetim ayrıcalıkları olan Visual Studio için geliştirici `setup.bat service`komut istemini açın ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c892c-152">On the server, open a Developer Command Prompt for Visual Studio with administrative privileges and run `setup.bat service`.</span></span> <span data-ttu-id="c892c-153">Bağımsız değişkenle birlikte çalışmak, `setup.bat` bilgisayarın tam nitelikli etki alanı adı içeren bir hizmet sertifikası oluşturur ve hizmet sertifikasını Service.cer adlı bir dosyaya aktarın. `service`</span><span class="sxs-lookup"><span data-stu-id="c892c-153">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
6. <span data-ttu-id="c892c-154">Web.config'i bilgisayarın tam nitelikli alan `findValue` adı ile aynı olan yeni sertifika adını [ \<(serviceCertificate>'daki ](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)öznitelikte) yansıtacak şekilde edin.</span><span class="sxs-lookup"><span data-stu-id="c892c-154">Edit Web.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), which is the same as the fully-qualified domain name of the computer.</span></span>  
  
7. <span data-ttu-id="c892c-155">Service.cer dosyasını servis dizininden istemci bilgisayarındaki istemci dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="c892c-155">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8. <span data-ttu-id="c892c-156">İstemci bilgisayarındaki Client.exe.config dosyasında, hizmetinyeni adresiyle eşleşecek şekilde bitiş noktasının adres değerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="c892c-156">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="c892c-157">İstemcide, yönetim ayrıcalıklarına sahip Visual Studio için bir Geliştirici Komut Komut Ustem'i açın ve ImportServiceCert.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c892c-157">On the client, open a Developer Command Prompt for Visual Studio with administrative privileges and run ImportServiceCert.bat.</span></span> <span data-ttu-id="c892c-158">Bu, hizmet sertifikasını Service.cer dosyasından CurrentUser - Trusted People deposuna aktarabilir.</span><span class="sxs-lookup"><span data-stu-id="c892c-158">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
10. <span data-ttu-id="c892c-159">İstemci bilgisayarında, istemci.exe'yi komut isteminden başlatın.</span><span class="sxs-lookup"><span data-stu-id="c892c-159">On the client computer, launch Client.exe from a command prompt.</span></span> <span data-ttu-id="c892c-160">İstemci ve hizmet iletişim kuramazsa, [WCF Örnekleri için Sorun Giderme İpuçları'na](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))bakın.</span><span class="sxs-lookup"><span data-stu-id="c892c-160">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="c892c-161">Örnekten sonra temizlemek için</span><span class="sxs-lookup"><span data-stu-id="c892c-161">To clean up after the sample</span></span>  
  
- <span data-ttu-id="c892c-162">Örneği çalıştırmayı bitirdikten sonra örnekler klasöründe Cleanup.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c892c-162">Run Cleanup.bat in the samples folder after you have finished running the sample.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c892c-163">Bu komut dosyası, bu örneği bilgisayarlar da çalıştırırken istemcideki hizmet sertifikalarını kaldırmaz.</span><span class="sxs-lookup"><span data-stu-id="c892c-163">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="c892c-164">Bilgisayarlar arasında sertifika kullanan Windows Communication Foundation (WCF) örneklerini çalıştırdıysanız, CurrentUser - Trusted People mağazasında yüklenen hizmet sertifikalarını temizlediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="c892c-164">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="c892c-165">Bunu yapmak için aşağıdaki komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` Örneğin: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="c892c-165">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
  
## <a name="the-setup-batch-file"></a><span data-ttu-id="c892c-166">Kurulum Toplu Dosyası</span><span class="sxs-lookup"><span data-stu-id="c892c-166">The Setup Batch File</span></span>  
 <span data-ttu-id="c892c-167">Bu örnekte yer alan Setup.bat toplu dosyası, sunucu sertifikası tabanlı güvenlik gerektiren kendi kendine barındırılan bir uygulamayı çalıştırmak için sunucuyu ilgili sertifikalarla yapılandırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="c892c-167">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="c892c-168">Bu toplu iş dosyası, bilgisayarlar arasında çalışmak veya barındırılmayan bir durumda çalışmak için değiştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="c892c-168">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>  
  
 <span data-ttu-id="c892c-169">Aşağıda, uygun yapılandırmada çalışacak şekilde değiştirilebilmeleri için toplu iş dosyalarının farklı bölümlerine kısa bir genel bakış sağlanacaktır.</span><span class="sxs-lookup"><span data-stu-id="c892c-169">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration.</span></span>  
  
- <span data-ttu-id="c892c-170">Sunucu sertifikası oluşturma.</span><span class="sxs-lookup"><span data-stu-id="c892c-170">Creating the server certificate.</span></span>  
  
     <span data-ttu-id="c892c-171">Setup.bat toplu dosyasından aşağıdaki satırlar kullanılacak sunucu sertifikasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c892c-171">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="c892c-172">%SERVER_NAME değişkeni sunucu adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c892c-172">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="c892c-173">Kendi sunucu adınızı belirtmek için bu değişkeni değiştirin.</span><span class="sxs-lookup"><span data-stu-id="c892c-173">Change this variable to specify your own server name.</span></span> <span data-ttu-id="c892c-174">Bu toplu iş dosyası varsayılan olarak localhost'a aktarır.</span><span class="sxs-lookup"><span data-stu-id="c892c-174">This batch file defaults it to localhost.</span></span>  
  
     <span data-ttu-id="c892c-175">Sertifika, LocalMachine mağazasının altında Benim (Kişisel) mağazamda depolanır.</span><span class="sxs-lookup"><span data-stu-id="c892c-175">The certificate is stored in My (Personal) store under the LocalMachine store location.</span></span>  
  
    ```console
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
- <span data-ttu-id="c892c-176">Sunucu sertifikasını istemcinin güvenilir sertifika deposuna yükleme.</span><span class="sxs-lookup"><span data-stu-id="c892c-176">Installing the server certificate into the client's trusted certificate store.</span></span>  
  
     <span data-ttu-id="c892c-177">Setup.bat toplu iş dosyasındaki aşağıdaki satırlar, sunucu sertifikasını istemcigüvenilir kişiler deposuna kopyalar.</span><span class="sxs-lookup"><span data-stu-id="c892c-177">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="c892c-178">Makecert.exe tarafından oluşturulan sertifikalar istemci sistemi tarafından dolaylı olarak güvenilen olmadığından bu adım gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c892c-178">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="c892c-179">İstemci tarafından güvenilen kök sertifikasına dayanan bir sertifikanız varsa (örneğin, Microsoft tarafından verilmiş bir sertifika- istemci sertifika deposunu sunucu sertifikasıyla doldurma adımı gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="c892c-179">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```bat  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
