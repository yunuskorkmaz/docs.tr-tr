---
title: "Üyelik ve Rol Sağlayıcısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0d11a31c-e75f-4fcf-9cf4-b7f26e056bcd
caps.latest.revision: "16"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f2107c5ae03330eb82567ab483dcd7003a35e189
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="membership-and-role-provider"></a><span data-ttu-id="2794f-102">Üyelik ve Rol Sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="2794f-102">Membership and Role Provider</span></span>
<span data-ttu-id="2794f-103">Üyelik ve rol sağlayıcısı örneği, bir hizmetin nasıl kullanabileceğinizi gösterir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] kimlik doğrulama ve yetkilendirme istemciler için üyelik ve rol sağlayıcıları.</span><span class="sxs-lookup"><span data-stu-id="2794f-103">The Membership and Role Provider sample demonstrates how a service can use the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] membership and role providers to authenticate and authorize clients.</span></span>  
  
 <span data-ttu-id="2794f-104">Bu örnekte, istemci bir konsol uygulaması (.exe) ve Internet Information Services (IIS) tarafından barındırılan hizmetindeki.</span><span class="sxs-lookup"><span data-stu-id="2794f-104">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2794f-105">Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="2794f-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="2794f-106">Örnek gösterir nasıl:</span><span class="sxs-lookup"><span data-stu-id="2794f-106">The sample demonstrates how:</span></span>  
  
-   <span data-ttu-id="2794f-107">Bir istemci, kullanıcı adı parola birleşimi kullanılarak doğrulanabilir.</span><span class="sxs-lookup"><span data-stu-id="2794f-107">A client can authenticate by using the username-password combination.</span></span>  
  
-   <span data-ttu-id="2794f-108">Sunucu, istemci kimlik bilgilerine karşı doğrulayabilirsiniz [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] üyelik sağlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="2794f-108">The server can validate the client credentials against the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] membership provider.</span></span>  
  
-   <span data-ttu-id="2794f-109">Sunucu, sunucunun X.509 sertifikası kullanılarak doğrulanabilir.</span><span class="sxs-lookup"><span data-stu-id="2794f-109">The server can be authenticated by using the server's X.509 certificate.</span></span>  
  
-   <span data-ttu-id="2794f-110">Sunucunun kimliği doğrulanmış istemciyi bir role kullanarak eşleyebilirsiniz [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] rol sağlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="2794f-110">The server can map the authenticated client to a role by using the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role provider.</span></span>  
  
-   <span data-ttu-id="2794f-111">Sunucu kullanabilir `PrincipalPermissionAttribute` hizmeti tarafından sunulan belirli yöntemlerine erişimi denetleme.</span><span class="sxs-lookup"><span data-stu-id="2794f-111">The server can use the `PrincipalPermissionAttribute` to control access to certain methods that are exposed by the service.</span></span>  
  
 <span data-ttu-id="2794f-112">Üyelik ve rol sağlayıcılarını SQL sunucusu tarafından desteklenen bir deposunu kullanacak şekilde yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="2794f-112">The membership and role providers are configured to use a store backed by SQL Server.</span></span> <span data-ttu-id="2794f-113">Bir bağlantı dizesi ve çeşitli seçenekleri hizmet yapılandırma dosyasında belirtilir.</span><span class="sxs-lookup"><span data-stu-id="2794f-113">A connection string and various options are specified in the service configuration file.</span></span> <span data-ttu-id="2794f-114">Üyelik sağlayıcısının adı verilen `SqlMembershipProvider` rol sağlayıcısı adı verilen sırada `SqlRoleProvider`.</span><span class="sxs-lookup"><span data-stu-id="2794f-114">The membership provider is given the name `SqlMembershipProvider` while the role provider is given the name `SqlRoleProvider`.</span></span>  
  
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
  
 <span data-ttu-id="2794f-115">Hizmet Web.config yapılandırma dosyası kullanılarak tanımlanmış hizmeti ile iletişim kurmak için tek bir uç noktasını kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="2794f-115">The service exposes a single endpoint for communicating with the service, which is defined by using the Web.config configuration file.</span></span> <span data-ttu-id="2794f-116">Uç nokta bir adresi, bağlama ve bir sözleşme oluşur.</span><span class="sxs-lookup"><span data-stu-id="2794f-116">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="2794f-117">Bağlama ile standart bir yapılandırılmış `wsHttpBinding`, Windows kimlik doğrulaması için kullanılacak varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="2794f-117">The binding is configured with a standard `wsHttpBinding`, which defaults to using Windows authentication.</span></span> <span data-ttu-id="2794f-118">Bu örnek standart ayarlar `wsHttpBinding` kullanıcı adı kimlik doğrulaması kullanacak şekilde.</span><span class="sxs-lookup"><span data-stu-id="2794f-118">This sample sets the standard `wsHttpBinding` to use username authentication.</span></span> <span data-ttu-id="2794f-119">Sunucu sertifikası için hizmet kimlik doğrulaması kullanılacaksa davranışını belirtir.</span><span class="sxs-lookup"><span data-stu-id="2794f-119">The behavior specifies that the server certificate is to be used for service authentication.</span></span> <span data-ttu-id="2794f-120">Sunucu sertifikası için aynı değeri içermelidir `SubjectName` olarak `findValue` özniteliğini [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="2794f-120">The server certificate must contain the same value for the `SubjectName` as the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) configuration element.</span></span> <span data-ttu-id="2794f-121">Ayrıca, kimlik doğrulamasının davranışını belirten kullanıcı adı parola çiftleri tarafından gerçekleştirilir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] üyelik sağlayıcısı ve rol eşleme tarafından gerçekleştirilir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] iki sağlayıcıları için tanımlanan adlar belirterek rol sağlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="2794f-121">In addition the behavior specifies that authentication of username-password pairs is performed by the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] membership provider and role mapping is performed by the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role provider by specifying the names defined for the two providers.</span></span>  
  
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
  
 <span data-ttu-id="2794f-122">Örneği çalıştırdığınızda, istemci altında üç farklı kullanıcı hesapları çeşitli hizmet işlemlerini çağırır: Alice, Bob ve Cahit.</span><span class="sxs-lookup"><span data-stu-id="2794f-122">When you run the sample, the client calls the various service operations under three different user accounts: Alice, Bob, and Charlie.</span></span> <span data-ttu-id="2794f-123">İşlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="2794f-123">The operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="2794f-124">"Alice" tamamlanacak kullanıcı olarak yapılan tüm dört çağırır.</span><span class="sxs-lookup"><span data-stu-id="2794f-124">All four calls made as user "Alice" should succeed.</span></span> <span data-ttu-id="2794f-125">Kullanıcı "Bob", bir erişim reddedildi hatası bölme yöntemini çağırmak çalışırken almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2794f-125">User "Bob" should get an access denied error when trying to call the Divide method.</span></span> <span data-ttu-id="2794f-126">Kullanıcı "Cahit" bir erişim reddedildi hatası çağrılmaya çalışılırken alır yöntemi çarpın.</span><span class="sxs-lookup"><span data-stu-id="2794f-126">User "Charlie" should get an access denied error when trying to call the Multiply method.</span></span> <span data-ttu-id="2794f-127">İstemcisi penceresinde istemciyi aşağı kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="2794f-127">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2794f-128">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="2794f-128">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="2794f-129">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2794f-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="2794f-130">Yapılandırdığınızdan emin olun [ASP.NET uygulama hizmetleri veritabanına](http://go.microsoft.com/fwlink/?LinkId=94997).</span><span class="sxs-lookup"><span data-stu-id="2794f-130">Ensure that you have configured the [ASP.NET Application Services Database](http://go.microsoft.com/fwlink/?LinkId=94997).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2794f-131">SQL Server Express Edition çalıştırıyorsanız, sunucu adıdır. \SQLEXPRESS.</span><span class="sxs-lookup"><span data-stu-id="2794f-131">If you are running SQL Server Express Edition, your server name is .\SQLEXPRESS.</span></span> <span data-ttu-id="2794f-132">Bu sunucuyu yapılandırırken kullanılmalıdır [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uygulama hizmetleri veritabanına de olduğu gibi Web.config bağlantı dizesidir.</span><span class="sxs-lookup"><span data-stu-id="2794f-132">This server should be used when configuring the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Application Services Database as well as in the Web.config connection string.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2794f-133">[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Çalışan işlem hesabı, bu adımda oluşturulan veritabanı üzerinde izinleri olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2794f-133">The [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] worker process account must have permissions on the database that is created in this step.</span></span> <span data-ttu-id="2794f-134">Bunu yapmak için sqlcmd yardımcı programını veya SQL Server Management Studio kullanın.</span><span class="sxs-lookup"><span data-stu-id="2794f-134">Use the sqlcmd utility or SQL Server Management Studio to do this.</span></span>  
  
3.  <span data-ttu-id="2794f-135">Tek veya çapraz bilgisayar yapılandırmasında örneği çalıştırmak için aşağıdaki yönergeleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="2794f-135">To run the sample in a single- or cross-computer configuration, use the following instructions.</span></span>  
  
### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="2794f-136">Aynı bilgisayara örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="2794f-136">To run the sample on the same computer</span></span>  
  
1.  <span data-ttu-id="2794f-137">Yolun Makecert.exe bulunduğu klasörü içerdiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="2794f-137">Make sure that the path includes the folder where Makecert.exe is located.</span></span>  
  
2.  <span data-ttu-id="2794f-138">Visual Studio komut istemini yönetici ayrıcalıklarıyla çalıştırın örnek yükleme klasöründeki Setup.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="2794f-138">Run Setup.bat from the sample install folder in a Visual Studio command prompt run with administrator privileges.</span></span> <span data-ttu-id="2794f-139">Bu örneği çalıştırmak için gereken hizmet sertifikaları yükler.</span><span class="sxs-lookup"><span data-stu-id="2794f-139">This installs the service certificates required for running the sample.</span></span>  
  
3.  <span data-ttu-id="2794f-140">Client.exe \client\bin başlatın.</span><span class="sxs-lookup"><span data-stu-id="2794f-140">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="2794f-141">İstemci etkinliği istemci konsol uygulaması görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="2794f-141">Client activity is displayed on the client console application.</span></span>  
  
4.  <span data-ttu-id="2794f-142">İstemci ve hizmet iletişim kurabildiğinden değilseniz bkz [sorun giderme ipuçları](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="2794f-142">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="2794f-143">Bilgisayarlar arasında örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="2794f-143">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="2794f-144">Hizmet bilgisayarda bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2794f-144">Create a directory on the service computer.</span></span> <span data-ttu-id="2794f-145">Internet Information Services (IIS) yönetim aracını kullanarak bu dizin için servicemodelsamples adlı bir sanal uygulama oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2794f-145">Create a virtual application named servicemodelsamples for this directory by using the Internet Information Services (IIS) management tool.</span></span>  
  
2.  <span data-ttu-id="2794f-146">Hizmet program dosyalarını \inetpub\wwwroot\servicemodelsamples hizmeti bilgisayarında sanal dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="2794f-146">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service computer.</span></span> <span data-ttu-id="2794f-147">\Bin alt dizinindeki dosyaları kopyalayın emin olun.</span><span class="sxs-lookup"><span data-stu-id="2794f-147">Ensure that you copy the files in the \bin subdirectory.</span></span> <span data-ttu-id="2794f-148">Ayrıca Setup.bat, GetComputerName.vbs ve Cleanup.bat dosyaları hizmet bilgisayara kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="2794f-148">Also copy the Setup.bat, GetComputerName.vbs, and Cleanup.bat files to the service computer.</span></span>  
  
3.  <span data-ttu-id="2794f-149">İstemci ikili dosyalarının için istemci bilgisayarda bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2794f-149">Create a directory on the client computer for the client binaries.</span></span>  
  
4.  <span data-ttu-id="2794f-150">İstemci program dosyaları istemci bilgisayarda istemci dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="2794f-150">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="2794f-151">Ayrıca istemciye Setup.bat, Cleanup.bat ve ImportServiceCert.bat dosyalarını kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="2794f-151">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5.  <span data-ttu-id="2794f-152">Sunucusunda yönetici ayrıcalıklarına sahip bir Visual Studio komut istemi açın ve Çalıştır `setup.bat service`.</span><span class="sxs-lookup"><span data-stu-id="2794f-152">On the server, open a Visual Studio command prompt with administrative privileges and run `setup.bat service`.</span></span> <span data-ttu-id="2794f-153">Çalışan `setup.bat` ile `service` bağımsız değişkeni bilgisayarın tam etki alanı adı ile bir hizmet sertifikası oluşturur ve hizmet sertifikası Service.cer adlı bir dosyaya aktarır.</span><span class="sxs-lookup"><span data-stu-id="2794f-153">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
6.  <span data-ttu-id="2794f-154">Web.config dosyasını yeni sertifika yansıtacak şekilde düzenleyin (içinde `findValue` özniteliğini [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), bilgisayarın tam etki alanı adı ile aynı olduğu.</span><span class="sxs-lookup"><span data-stu-id="2794f-154">Edit Web.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), which is the same as the fully-qualified domain name of the computer.</span></span>  
  
7.  <span data-ttu-id="2794f-155">Service.cer dosya hizmeti dizininden istemci bilgisayarda istemci dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="2794f-155">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8.  <span data-ttu-id="2794f-156">İstemci bilgisayardaki Client.exe.config dosyasında yeni adresi hizmetinizin eşleştirmek için uç nokta adresi değerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="2794f-156">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="2794f-157">İstemci üzerinde yönetici ayrıcalıklarına sahip bir Visual Studio komut istemi açın ve ImportServiceCert.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="2794f-157">On the client, open a Visual Studio command prompt with administrative privileges and run ImportServiceCert.bat.</span></span> <span data-ttu-id="2794f-158">Bu hizmet sertifikası Service.cer dosyadan Currentuser'a - TrustedPeople deposunu alır.</span><span class="sxs-lookup"><span data-stu-id="2794f-158">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
10. <span data-ttu-id="2794f-159">İstemci bilgisayarda bir komut isteminden Client.exe başlatın.</span><span class="sxs-lookup"><span data-stu-id="2794f-159">On the client computer, launch Client.exe from a command prompt.</span></span> <span data-ttu-id="2794f-160">İstemci ve hizmet iletişim kurabildiğinden değilseniz bkz [sorun giderme ipuçları](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="2794f-160">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="2794f-161">Örnek sonra temizlemek için</span><span class="sxs-lookup"><span data-stu-id="2794f-161">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="2794f-162">Örnek çalıştıran bitirdikten sonra Cleanup.bat samples klasöründen çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="2794f-162">Run Cleanup.bat in the samples folder after you have finished running the sample.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2794f-163">Bu komut, bu örnek bilgisayarlar arasında çalıştırırken bir istemcide hizmet sertifikaları kaldırmaz.</span><span class="sxs-lookup"><span data-stu-id="2794f-163">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="2794f-164">Çalıştırırsanız [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] bilgisayarlar arasında sertifikaları kullanma örnekleri Currentuser'a - TrustedPeople deposu yüklü hizmet sertifikalarını temizlemek emin olun.</span><span class="sxs-lookup"><span data-stu-id="2794f-164">If you have run [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="2794f-165">Bunu yapmak için aşağıdaki komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` örneğin: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="2794f-165">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
  
## <a name="the-setup-batch-file"></a><span data-ttu-id="2794f-166">Kurulum toplu iş dosyası</span><span class="sxs-lookup"><span data-stu-id="2794f-166">The Setup Batch File</span></span>  
 <span data-ttu-id="2794f-167">Bu örnekle dahil Setup.bat toplu iş dosyası, sunucu sertifika tabanlı güvenlik gerektiren kendini barındıran bir uygulamayı çalıştırmak için ilgili sertifikalarla sunucu yapılandırmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="2794f-167">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="2794f-168">Bu toplu iş dosyası bilgisayarlar arasında iş ya da barındırılan olmayan bir durumda çalışması için değiştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="2794f-168">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>  
  
 <span data-ttu-id="2794f-169">Aşağıdakiler, böylece uygun yapılandırmada çalışacak biçimde değiştirilebilir toplu iş dosyaları farklı bölümlerini kısa bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="2794f-169">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration.</span></span>  
  
-   <span data-ttu-id="2794f-170">Sunucu sertifikası oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="2794f-170">Creating the server certificate.</span></span>  
  
     <span data-ttu-id="2794f-171">Aşağıdaki satırları Setup.bat toplu iş dosyasından kullanılacak sunucu sertifikası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2794f-171">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="2794f-172">% Sunucu_adı % değişkeni sunucusunun adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="2794f-172">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="2794f-173">Kendi sunucu adını belirtmek için bu değişkeni değiştirin.</span><span class="sxs-lookup"><span data-stu-id="2794f-173">Change this variable to specify your own server name.</span></span> <span data-ttu-id="2794f-174">Bu toplu iş dosyası için localhost olarak varsayar.</span><span class="sxs-lookup"><span data-stu-id="2794f-174">This batch file defaults it to localhost.</span></span>  
  
     <span data-ttu-id="2794f-175">Sertifika, LocalMachine depolama konumu altında (Kişisel) My deposunda saklanır.</span><span class="sxs-lookup"><span data-stu-id="2794f-175">The certificate is stored in My (Personal) store under the LocalMachine store location.</span></span>  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   <span data-ttu-id="2794f-176">Sunucu sertifikası istemcinin güvenilen sertifika deposuna yükleme.</span><span class="sxs-lookup"><span data-stu-id="2794f-176">Installing the server certificate into the client's trusted certificate store.</span></span>  
  
     <span data-ttu-id="2794f-177">İstemci güvenilir kişiler içine Setup.bat toplu dosya kopyalama sunucu sertifikasının aşağıdaki satırları depolar.</span><span class="sxs-lookup"><span data-stu-id="2794f-177">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="2794f-178">MakeCert.exe tarafından oluşturulan sertifikaları örtük olarak istemci sistemi tarafından güvenilir değil çünkü bu adım gereklidir.</span><span class="sxs-lookup"><span data-stu-id="2794f-178">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="2794f-179">Bir istemci güvenilen kök sertifikasını kökü belirtilmiş bir sertifikanız zaten varsa — örneğin, Microsoft tarafından verilen sertifika — sunucu sertifikasına sahip istemci sertifika deposunun doldurulması, bu adım gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="2794f-179">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="2794f-180">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2794f-180">See Also</span></span>
