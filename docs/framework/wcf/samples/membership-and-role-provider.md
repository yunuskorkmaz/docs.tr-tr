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
# <a name="membership-and-role-provider"></a>Üyelik ve Rol Sağlayıcısı
Üyelik ve rol sağlayıcısı örneği, bir hizmetin, istemcilerin kimliğini doğrulamak ve yetkilendirmek için ASP.NET üyeliğini ve rol sağlayıcılarını nasıl kullanabileceğinizi gösterir.  
  
 Bu örnekte, istemci bir konsol uygulaması (. exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
 Örnek şunu gösterir:  
  
- İstemci Kullanıcı adı-parola birleşimini kullanarak kimlik doğrulaması yapabilir.  
  
- Sunucu, ASP.NET üyelik sağlayıcısına karşı istemci kimlik bilgilerini doğrulayabilir.  
  
- Sunucunun sunucu X. 509.440 sertifikası kullanılarak kimlik doğrulaması yapılabilir.  
  
- Sunucu, ASP.NET rol sağlayıcısını kullanarak kimliği doğrulanmış istemciyi bir rolle eşleyebilir.  
  
- Sunucu, `PrincipalPermissionAttribute` hizmet tarafından sunulan belirli yöntemlere erişimi denetlemek için kullanabilir.  
  
 Üyelik ve rol sağlayıcıları, SQL Server tarafından desteklenen bir depoyu kullanacak şekilde yapılandırılır. Hizmet yapılandırma dosyasında bir bağlantı dizesi ve çeşitli seçenekler belirtilmiştir. Rol sağlayıcısına ad `SqlRoleProvider`verildiğinde üyelik sağlayıcısına ad `SqlMembershipProvider` verilir.  
  
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
  
 Hizmet, Web. config yapılandırma dosyası kullanılarak tanımlanan hizmetle iletişim kurmak için tek bir uç nokta sunar. Uç nokta bir adres, bağlama ve bir anlaşmada oluşur. Bağlama, varsayılan olarak Windows kimlik doğrulamasını `wsHttpBinding`kullanan bir standart ile yapılandırılır. Bu örnek Kullanıcı adı kimlik `wsHttpBinding` doğrulamasını kullanmak için standart ayarlar. Davranış, sunucu sertifikasının hizmet kimlik doğrulaması için kullanılacağını belirtir. Sunucu sertifikası, `SubjectName` `findValue` [ServiceCertificate > yapılandırma öğesinde özniteliğiyle aynı değeri içermelidir. \<](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) Ayrıca davranış, Kullanıcı adı-parola çiftlerinin kimlik doğrulamasının ASP.NET üyelik sağlayıcısı tarafından gerçekleştirildiğini belirtir ve rol eşleme, iki sağlayıcı için tanımlanan adları belirterek ASP.NET rol sağlayıcısı tarafından gerçekleştirilir.  
  
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
  
 Örneği çalıştırdığınızda, istemci üç farklı kullanıcı hesabı altında çeşitli hizmet işlemlerini çağırır: Çiğdem, Bob ve Charlie. İşlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir. "Gamze" kullanıcısı olarak yapılan tüm dört çağrı başarılı olmalıdır. "Bob" kullanıcısının, bölme yöntemini çağırmaya çalışırken bir erişim reddedildi hatası alması gerekir. "Charlie" kullanıcısının, çarpma yöntemini çağırmaya çalışırken bir erişim reddedildi hatası alması gerekir. İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
2. [ASP.NET uygulama Hizmetleri veritabanını](https://go.microsoft.com/fwlink/?LinkId=94997)yapılandırdığınızdan emin olun.  
  
    > [!NOTE]
    > SQL Server Express Edition çalıştırıyorsanız, sunucu adınız .\SQLEXPRESS. olur. Bu sunucu, ASP.NET Uygulama Hizmetleri veritabanı ve Web. config bağlantı dizesinde yapılandırılırken kullanılmalıdır.  
  
    > [!NOTE]
    > ASP.NET çalışan işlem hesabının, bu adımda oluşturulan veritabanında izinleri olmalıdır. Bunu yapmak için sqlcmd yardımcı programını veya SQL Server Management Studio kullanın.  
  
3. Örneği tek veya bir çoklu bilgisayar yapılandırmasında çalıştırmak için aşağıdaki yönergeleri kullanın.  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>Örneği aynı bilgisayarda çalıştırmak için  
  
1. Yolun, MakeCert. exe ' nin bulunduğu klasörü içerdiğinden emin olun.  
  
2. Visual Studio 'nun yönetici ayrıcalıklarıyla çalışması için Geliştirici Komut İstemi örnek yükleme klasöründen Setup. bat dosyasını çalıştırın. Bu, örneği çalıştırmak için gereken hizmet sertifikalarını kurar.  
  
3. \Client\bin. adresinden Client. exe ' yi Başlat İstemci etkinliği istemci konsol uygulamasında görüntülenir.  
  
4. İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-run-the-sample-across-computers"></a>Örneği bilgisayarlar arasında çalıştırmak için  
  
1. Hizmet bilgisayarında bir dizin oluşturun. Internet Information Services (IIS) yönetim aracını kullanarak bu dizin için servicemodelsamples adlı bir sanal uygulama oluşturun.  
  
2. Hizmet programı dosyalarını \inetpub\wwwroot\servicemodelsamples adresinden hizmet bilgisayarındaki sanal dizine kopyalayın. Dosyaları \bin alt dizininde kopyalamadiğinizden emin olun. Ayrıca Setup. bat, GetComputerName. vbs ve Cleanup. bat dosyalarını da hizmet bilgisayarına kopyalayın.  
  
3. İstemci bilgisayarda istemci ikilileri için bir dizin oluşturun.  
  
4. İstemci programı dosyalarını istemci bilgisayardaki istemci dizinine kopyalayın. Ayrıca Setup. bat, Cleanup. bat ve ImportServiceCert. bat dosyalarını istemciye kopyalayın.  
  
5. Sunucusunda, yönetim ayrıcalıklarına sahip Visual Studio için bir Geliştirici Komut İstemi açın ve çalıştırın `setup.bat service`. Bağımsız`service` değişkeniyle birlikte çalıştırmak `setup.bat` , bilgisayarın tam etki alanı adına sahip bir hizmet sertifikası oluşturur ve hizmet sertifikasını Service. cer adlı bir dosyaya aktarır.  
  
6. Web. config dosyasını, bilgisayarın tam etki alanı adıyla aynı olan yeni `findValue` sertifika adını ( [ \<ServiceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)özniteliğinde) yansıtacak şekilde düzenleyin.  
  
7. Service. cer dosyasını hizmet dizininden istemci bilgisayarındaki istemci dizinine kopyalayın.  
  
8. İstemci bilgisayardaki Client. exe. config dosyasında, uç noktanın adres değerini hizmetinizin yeni adresiyle eşleşecek şekilde değiştirin.  
  
9. İstemcisinde, yönetim ayrıcalıklarına sahip bir Visual Studio Geliştirici Komut İstemi açın ve ImportServiceCert. bat dosyasını çalıştırın. Bu, hizmet sertifikasını Service. cer dosyasından CurrentUser-Trustedkişiler deposuna aktarır.  
  
10. İstemci bilgisayarda, bir komut isteminden Client. exe ' yi başlatın. İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-clean-up-after-the-sample"></a>Örnekten sonra temizlemek için  
  
- Örneği çalıştırmayı bitirdikten sonra Samples klasöründe Cleanup. bat dosyasını çalıştırın.  
  
> [!NOTE]
> Bu betik, bilgisayarlar arasında bu örneği çalıştırırken bir istemcideki hizmet sertifikalarını kaldırmaz. Bilgisayarlar arasında sertifika kullanan Windows Communication Foundation (WCF) örneklerini çalıştırırsanız, CurrentUser-Trustedkişiler deposuna yüklenmiş olan hizmet sertifikalarını temizlediğinizden emin olun. Bunu yapmak için aşağıdaki komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`Örneğin: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
  
## <a name="the-setup-batch-file"></a>Kurulum toplu Iş dosyası  
 Bu örneğe eklenen Setup. bat toplu iş dosyası, sunucu sertifika tabanlı güvenlik gerektiren şirket içinde barındırılan bir uygulamayı çalıştırmak için sunucuyu ilgili sertifikalarla yapılandırmanıza olanak tanır. Bu toplu iş dosyasının bilgisayarlarda çalışmak veya barındırılmayan bir durumda çalışması için değiştirilmesi gerekir.  
  
 Aşağıdakiler, uygun yapılandırmada çalışacak şekilde değiştirilebilecek şekilde, toplu iş dosyalarının farklı bölümlerine kısa bir genel bakış sağlar.  
  
- Sunucu sertifikası oluşturuluyor.  
  
     Setup. bat toplu iş dosyasından aşağıdaki satırlar kullanılacak sunucu sertifikasını oluşturur. % SERVER_NAME% değişkeni sunucu adını belirtiyor. Kendi sunucu adınızı belirtmek için bu değişkeni değiştirin. Bu toplu iş dosyası varsayılan olarak localhost 'tur.  
  
     Sertifika, LocalMachine depolama konumu altında (kişisel) deposunda depolanır.  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
- Sunucu sertifikasını istemcinin güvenilen sertifika deposuna yükleme.  
  
     Setup. bat toplu iş dosyası 'ndaki aşağıdaki satırlar, sunucu sertifikasını istemci güvenilir kişiler deposuna kopyalar. Bu adım, MakeCert. exe tarafından oluşturulan sertifikaların istemci sistemi tarafından örtük olarak güvenilir olmadığından gereklidir. İstemci tarafından güvenilen kök sertifikada kök sertifikaya sahip bir sertifikanız zaten varsa (örneğin, Microsoft tarafından verilen bir sertifika), istemci sertifikası deposunu sunucu sertifikasıyla doldurmanın bu adımı gerektirmez.  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
