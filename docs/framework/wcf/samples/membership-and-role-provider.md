---
title: Üyelik ve Rol Sağlayıcısı
ms.date: 03/30/2017
ms.assetid: 0d11a31c-e75f-4fcf-9cf4-b7f26e056bcd
ms.openlocfilehash: bff100189c904706f3c7c886945383252ce7bfcb
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43553155"
---
# <a name="membership-and-role-provider"></a><span data-ttu-id="9e8ba-102">Üyelik ve Rol Sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="9e8ba-102">Membership and Role Provider</span></span>
<span data-ttu-id="9e8ba-103">Üyelik ve rol sağlayıcısı örnek, bir hizmetin nasıl kullanabileceğinizi gösterir. [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] kimliğini doğrulama ve yetkilendirme istemciler için üyelik ve rol sağlayıcıları.</span><span class="sxs-lookup"><span data-stu-id="9e8ba-103">The Membership and Role Provider sample demonstrates how a service can use the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] membership and role providers to authenticate and authorize clients.</span></span>  
  
 <span data-ttu-id="9e8ba-104">Bu örnekte, istemci bir konsol uygulaması (.exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.</span><span class="sxs-lookup"><span data-stu-id="9e8ba-104">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9e8ba-105">Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="9e8ba-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="9e8ba-106">Örnek gösterir nasıl:</span><span class="sxs-lookup"><span data-stu-id="9e8ba-106">The sample demonstrates how:</span></span>  
  
-   <span data-ttu-id="9e8ba-107">Bir istemci, kullanıcı adı parola birleşimi kullanarak kimlik doğrulaması yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9e8ba-107">A client can authenticate by using the username-password combination.</span></span>  
  
-   <span data-ttu-id="9e8ba-108">Sunucu, istemci kimlik bilgileri karşı doğrulayabilir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] üyelik sağlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="9e8ba-108">The server can validate the client credentials against the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] membership provider.</span></span>  
  
-   <span data-ttu-id="9e8ba-109">Sunucu, sunucunun X.509 sertifikası kullanılarak doğrulanabilir.</span><span class="sxs-lookup"><span data-stu-id="9e8ba-109">The server can be authenticated by using the server's X.509 certificate.</span></span>  
  
-   <span data-ttu-id="9e8ba-110">Sunucunun kimliği doğrulanmış istemciyi bir role kullanarak eşleyebilirsiniz [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] rol sağlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="9e8ba-110">The server can map the authenticated client to a role by using the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role provider.</span></span>  
  
-   <span data-ttu-id="9e8ba-111">Sunucu kullanabilir `PrincipalPermissionAttribute` erişimi denetlemek için hizmet tarafından sunulan belirli yöntem.</span><span class="sxs-lookup"><span data-stu-id="9e8ba-111">The server can use the `PrincipalPermissionAttribute` to control access to certain methods that are exposed by the service.</span></span>  
  
 <span data-ttu-id="9e8ba-112">Üyelik ve rol sağlayıcıları, SQL Server tarafından desteklenen bir deposunu kullanmak üzere yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="9e8ba-112">The membership and role providers are configured to use a store backed by SQL Server.</span></span> <span data-ttu-id="9e8ba-113">Bir bağlantı dizesi ve çeşitli seçenekleri hizmet yapılandırma dosyasında belirtilir.</span><span class="sxs-lookup"><span data-stu-id="9e8ba-113">A connection string and various options are specified in the service configuration file.</span></span> <span data-ttu-id="9e8ba-114">Üyelik sağlayıcısının adı verilen `SqlMembershipProvider` rol sağlayıcısı adı verilen sırada `SqlRoleProvider`.</span><span class="sxs-lookup"><span data-stu-id="9e8ba-114">The membership provider is given the name `SqlMembershipProvider` while the role provider is given the name `SqlRoleProvider`.</span></span>  
  
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
  
 <span data-ttu-id="9e8ba-115">Hizmet, Web.config yapılandırma dosyası kullanılarak tanımlanmış hizmet ile iletişim kurmak için tek bir uç noktayı kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="9e8ba-115">The service exposes a single endpoint for communicating with the service, which is defined by using the Web.config configuration file.</span></span> <span data-ttu-id="9e8ba-116">Uç nokta, adres, bağlama ve bir sözleşme oluşur.</span><span class="sxs-lookup"><span data-stu-id="9e8ba-116">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="9e8ba-117">Bir standart yapılandırılmış bağlama `wsHttpBinding`, bunun varsayılan Windows kimlik doğrulaması için kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="9e8ba-117">The binding is configured with a standard `wsHttpBinding`, which defaults to using Windows authentication.</span></span> <span data-ttu-id="9e8ba-118">Bu örnek, standart ayarlar `wsHttpBinding` kullanıcı adı kimlik doğrulaması kullanmak için.</span><span class="sxs-lookup"><span data-stu-id="9e8ba-118">This sample sets the standard `wsHttpBinding` to use username authentication.</span></span> <span data-ttu-id="9e8ba-119">Sunucu sertifikası hizmet kimlik doğrulaması için kullanılacak olan davranışını belirtir.</span><span class="sxs-lookup"><span data-stu-id="9e8ba-119">The behavior specifies that the server certificate is to be used for service authentication.</span></span> <span data-ttu-id="9e8ba-120">Sunucu sertifikası için aynı değeri içermelidir `SubjectName` olarak `findValue` özniteliğini [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="9e8ba-120">The server certificate must contain the same value for the `SubjectName` as the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) configuration element.</span></span> <span data-ttu-id="9e8ba-121">Buna ek olarak söz konusu kimlik doğrulamasını davranışı belirtir kullanıcı adı parola çiftleri tarafından gerçekleştirilir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] üyelik sağlayıcısı ve rol eşlemesi tarafından gerçekleştirilir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] iki sağlayıcıları için tanımlanan adlar belirterek rol sağlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="9e8ba-121">In addition the behavior specifies that authentication of username-password pairs is performed by the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] membership provider and role mapping is performed by the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role provider by specifying the names defined for the two providers.</span></span>  
  
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
  
 <span data-ttu-id="9e8ba-122">İstemci örneği çalıştırdığınızda, altında üç farklı kullanıcı hesapları çeşitli hizmet işlemleri çağırır: Alice, Bob ve Cahit.</span><span class="sxs-lookup"><span data-stu-id="9e8ba-122">When you run the sample, the client calls the various service operations under three different user accounts: Alice, Bob, and Charlie.</span></span> <span data-ttu-id="9e8ba-123">İşlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="9e8ba-123">The operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="9e8ba-124">Başarısız olması "Gamze adlı" kullanıcı olarak yapılan tüm dört çağrıları.</span><span class="sxs-lookup"><span data-stu-id="9e8ba-124">All four calls made as user "Alice" should succeed.</span></span> <span data-ttu-id="9e8ba-125">Kullanıcı "Bob", bir erişim reddedildi hatası bölme yöntem çağrılmaya çalışılırken almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9e8ba-125">User "Bob" should get an access denied error when trying to call the Divide method.</span></span> <span data-ttu-id="9e8ba-126">Kullanıcı "Cahit" erişim reddedildi hatası çağrılmaya çalışılırken almanız gerekir yöntemi ile çarpın.</span><span class="sxs-lookup"><span data-stu-id="9e8ba-126">User "Charlie" should get an access denied error when trying to call the Multiply method.</span></span> <span data-ttu-id="9e8ba-127">İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="9e8ba-127">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="9e8ba-128">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="9e8ba-128">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="9e8ba-129">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9e8ba-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="9e8ba-130">Yapılandırdığınızdan emin olun [ASP.NET uygulama hizmetleri veritabanına](https://go.microsoft.com/fwlink/?LinkId=94997).</span><span class="sxs-lookup"><span data-stu-id="9e8ba-130">Ensure that you have configured the [ASP.NET Application Services Database](https://go.microsoft.com/fwlink/?LinkId=94997).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9e8ba-131">SQL Server Express Edition çalıştırıyorsanız, sunucu adıdır. \SQLEXPRESS.</span><span class="sxs-lookup"><span data-stu-id="9e8ba-131">If you are running SQL Server Express Edition, your server name is .\SQLEXPRESS.</span></span> <span data-ttu-id="9e8ba-132">Bu sunucu yapılandırırken kullanılmalıdır [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uygulama hizmetleri veritabanına de Web.config bağlantı dizesi olduğu gibi.</span><span class="sxs-lookup"><span data-stu-id="9e8ba-132">This server should be used when configuring the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Application Services Database as well as in the Web.config connection string.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9e8ba-133">[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Çalışan işlem hesabı, bu adımda oluşturulan veritabanı üzerinde izinleri olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9e8ba-133">The [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] worker process account must have permissions on the database that is created in this step.</span></span> <span data-ttu-id="9e8ba-134">Bunu yapmak için SQL Server Management Studio ve sqlcmd yardımcı programını kullanın.</span><span class="sxs-lookup"><span data-stu-id="9e8ba-134">Use the sqlcmd utility or SQL Server Management Studio to do this.</span></span>  
  
3.  <span data-ttu-id="9e8ba-135">Tek veya çoklu bilgisayar yapılandırmasında örneği çalıştırmak için aşağıdaki yönergeleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="9e8ba-135">To run the sample in a single- or cross-computer configuration, use the following instructions.</span></span>  
  
### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="9e8ba-136">Örneği aynı bilgisayarda çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="9e8ba-136">To run the sample on the same computer</span></span>  
  
1.  <span data-ttu-id="9e8ba-137">Yolun Makecert.exe bulunduğu klasörü içerdiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="9e8ba-137">Make sure that the path includes the folder where Makecert.exe is located.</span></span>  
  
2.  <span data-ttu-id="9e8ba-138">Visual Studio komut istemini yönetici ayrıcalıklarıyla çalıştırın örnek yükleme klasöründe Setup.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9e8ba-138">Run Setup.bat from the sample install folder in a Visual Studio command prompt run with administrator privileges.</span></span> <span data-ttu-id="9e8ba-139">Bu örneği çalıştırmak için gereken hizmet sertifikaları yükler.</span><span class="sxs-lookup"><span data-stu-id="9e8ba-139">This installs the service certificates required for running the sample.</span></span>  
  
3.  <span data-ttu-id="9e8ba-140">Client.exe \client\bin başlatın.</span><span class="sxs-lookup"><span data-stu-id="9e8ba-140">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="9e8ba-141">İstemci etkinliği istemci konsol uygulamasında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="9e8ba-141">Client activity is displayed on the client console application.</span></span>  
  
4.  <span data-ttu-id="9e8ba-142">İstemci ve hizmet iletişim kurabildiğini bilmiyorsanız bkz [sorun giderme ipuçları](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="9e8ba-142">If the client and service are not able to communicate, see [Troubleshooting Tips](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="9e8ba-143">Bilgisayarlar arasında örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="9e8ba-143">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="9e8ba-144">Hizmet bilgisayarda bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9e8ba-144">Create a directory on the service computer.</span></span> <span data-ttu-id="9e8ba-145">Internet Information Services (IIS) yönetim aracını kullanarak bu dizin için servicemodelsamples adlı sanal bir uygulama oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9e8ba-145">Create a virtual application named servicemodelsamples for this directory by using the Internet Information Services (IIS) management tool.</span></span>  
  
2.  <span data-ttu-id="9e8ba-146">Hizmet program dosyaları \inetpub\wwwroot\servicemodelsamples hizmeti bilgisayarında sanal dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="9e8ba-146">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service computer.</span></span> <span data-ttu-id="9e8ba-147">Dosyaları \bin alt dizinde kopyalama emin olun.</span><span class="sxs-lookup"><span data-stu-id="9e8ba-147">Ensure that you copy the files in the \bin subdirectory.</span></span> <span data-ttu-id="9e8ba-148">Ayrıca hizmet bilgisayara Setup.bat GetComputerName.vbs ve Cleanup.bat dosyaları kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="9e8ba-148">Also copy the Setup.bat, GetComputerName.vbs, and Cleanup.bat files to the service computer.</span></span>  
  
3.  <span data-ttu-id="9e8ba-149">İstemci ikili dosyaları için istemci bilgisayarda bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9e8ba-149">Create a directory on the client computer for the client binaries.</span></span>  
  
4.  <span data-ttu-id="9e8ba-150">İstemci program dosyaları istemci bilgisayarda istemci dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="9e8ba-150">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="9e8ba-151">Aynı zamanda istemciye Setup.bat Cleanup.bat ve ImportServiceCert.bat dosyaları kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="9e8ba-151">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5.  <span data-ttu-id="9e8ba-152">Sunucusunda, yönetici ayrıcalıklarına sahip bir Visual Studio komut istemi açın ve çalıştırın `setup.bat service`.</span><span class="sxs-lookup"><span data-stu-id="9e8ba-152">On the server, open a Visual Studio command prompt with administrative privileges and run `setup.bat service`.</span></span> <span data-ttu-id="9e8ba-153">Çalışan `setup.bat` ile `service` bağımsız değişkeni bilgisayarın tam etki alanı adı ile bir hizmet sertifikası oluşturur ve hizmet sertifikası Service.cer adlı bir dosyaya dışarı aktarır.</span><span class="sxs-lookup"><span data-stu-id="9e8ba-153">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
6.  <span data-ttu-id="9e8ba-154">Yeni sertifika adını yansıtacak şekilde Web.config'i düzenlemek (içinde `findValue` özniteliğini [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), bilgisayarın tam etki alanı adıyla aynı olduğu.</span><span class="sxs-lookup"><span data-stu-id="9e8ba-154">Edit Web.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), which is the same as the fully-qualified domain name of the computer.</span></span>  
  
7.  <span data-ttu-id="9e8ba-155">Service.cer dosya hizmeti dizinden istemci bilgisayarda istemci dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="9e8ba-155">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8.  <span data-ttu-id="9e8ba-156">İstemci bilgisayarda Client.exe.config dosyasında hizmetinizin yeni adresiyle eşleşecek şekilde uç nokta adresi değiştirin.</span><span class="sxs-lookup"><span data-stu-id="9e8ba-156">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="9e8ba-157">İstemci, yönetici ayrıcalıklarına sahip bir Visual Studio komut istemi açın ve ImportServiceCert.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9e8ba-157">On the client, open a Visual Studio command prompt with administrative privileges and run ImportServiceCert.bat.</span></span> <span data-ttu-id="9e8ba-158">Bu hizmet sertifikası Service.cer dosyasından CurrentUser - TrustedPeople deposuna aktarır.</span><span class="sxs-lookup"><span data-stu-id="9e8ba-158">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
10. <span data-ttu-id="9e8ba-159">İstemci bilgisayarda bir komut istemi'nden Client.exe başlatın.</span><span class="sxs-lookup"><span data-stu-id="9e8ba-159">On the client computer, launch Client.exe from a command prompt.</span></span> <span data-ttu-id="9e8ba-160">İstemci ve hizmet iletişim kurabildiğini bilmiyorsanız bkz [sorun giderme ipuçları](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="9e8ba-160">If the client and service are not able to communicate, see [Troubleshooting Tips](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="9e8ba-161">Sonra örnek temizlemek için</span><span class="sxs-lookup"><span data-stu-id="9e8ba-161">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="9e8ba-162">Örnek çalıştıran tamamladıktan sonra Cleanup.bat samples klasöründe çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9e8ba-162">Run Cleanup.bat in the samples folder after you have finished running the sample.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9e8ba-163">Bu betik, bu örnek, bilgisayarlar arasında çalıştırırken bir istemcide hizmet sertifikaları kaldırmaz.</span><span class="sxs-lookup"><span data-stu-id="9e8ba-163">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="9e8ba-164">Bilgisayarlar arasında sertifikaları kullanan bir Windows Communication Foundation (WCF) örnekleri çalıştırırsanız, CurrentUser - TrustedPeople deposu yüklü hizmet sertifikalarını Temizle emin olun.</span><span class="sxs-lookup"><span data-stu-id="9e8ba-164">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="9e8ba-165">Bunu yapmak için aşağıdaki komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` örneğin: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="9e8ba-165">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
  
## <a name="the-setup-batch-file"></a><span data-ttu-id="9e8ba-166">Kurulum toplu iş dosyası</span><span class="sxs-lookup"><span data-stu-id="9e8ba-166">The Setup Batch File</span></span>  
 <span data-ttu-id="9e8ba-167">Bu örnekle dahil Setup.bat toplu iş dosyası ile ilgili sertifika sunucusu sertifika tabanlı güvenlik gerektiren şirket içinde barındırılan bir uygulamayı çalıştırmak için sunucu yapılandırmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e8ba-167">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="9e8ba-168">Bu toplu iş dosyası bilgisayarlarda çalışmaya veya barındırılan olmayan bir durumda çalışması için değiştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="9e8ba-168">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>  
  
 <span data-ttu-id="9e8ba-169">Aşağıda, böylece uygun yapılandırmasında çalıştırılacak değiştirilebilir toplu iş dosyaları farklı bölümlerini kısa bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e8ba-169">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration.</span></span>  
  
-   <span data-ttu-id="9e8ba-170">Sunucu sertifikası oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="9e8ba-170">Creating the server certificate.</span></span>  
  
     <span data-ttu-id="9e8ba-171">Setup.bat toplu iş dosyasından aşağıdaki satırları kullanılacak sunucu sertifikası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9e8ba-171">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="9e8ba-172">% Sunucu_adı % değişkeni, sunucu adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="9e8ba-172">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="9e8ba-173">Kendi sunucu adını belirtmek için bu değişkeni değiştirin.</span><span class="sxs-lookup"><span data-stu-id="9e8ba-173">Change this variable to specify your own server name.</span></span> <span data-ttu-id="9e8ba-174">Bu toplu iş dosyası için localhost olarak varsayılır.</span><span class="sxs-lookup"><span data-stu-id="9e8ba-174">This batch file defaults it to localhost.</span></span>  
  
     <span data-ttu-id="9e8ba-175">Sertifikayı LocalMachine depolama konumu altında (Kişisel) My deposunda depolanır.</span><span class="sxs-lookup"><span data-stu-id="9e8ba-175">The certificate is stored in My (Personal) store under the LocalMachine store location.</span></span>  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   <span data-ttu-id="9e8ba-176">Sunucu sertifikasını istemcinin güvenilen sertifika depolama alanına yükleniyor.</span><span class="sxs-lookup"><span data-stu-id="9e8ba-176">Installing the server certificate into the client's trusted certificate store.</span></span>  
  
     <span data-ttu-id="9e8ba-177">İstemci güvenilir kişiler uygulamasına Setup.bat toplu dosya kopyalama sunucu sertifikasının aşağıdaki satırları depolayın.</span><span class="sxs-lookup"><span data-stu-id="9e8ba-177">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="9e8ba-178">MakeCert.exe tarafından oluşturulan sertifikaları örtük olarak istemci sistemi tarafından güvenilir değildir çünkü bu adım gereklidir.</span><span class="sxs-lookup"><span data-stu-id="9e8ba-178">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="9e8ba-179">Bir istemci güvenilen kök sertifikayı kök erişim izni verilmiş bir sertifika zaten varsa — örneğin, Microsoft tarafından verilen sertifika — sunucu sertifikasında istemci sertifika deposunun doldurulması, bu adım gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="9e8ba-179">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="9e8ba-180">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9e8ba-180">See Also</span></span>
