---
title: Üyelik ve Rol Sağlayıcısı
ms.date: 03/30/2017
ms.assetid: 0d11a31c-e75f-4fcf-9cf4-b7f26e056bcd
ms.openlocfilehash: bff100189c904706f3c7c886945383252ce7bfcb
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43405779"
---
# <a name="membership-and-role-provider"></a>Üyelik ve Rol Sağlayıcısı
Üyelik ve rol sağlayıcısı örnek, bir hizmetin nasıl kullanabileceğinizi gösterir. [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] kimliğini doğrulama ve yetkilendirme istemciler için üyelik ve rol sağlayıcıları.  
  
 Bu örnekte, istemci bir konsol uygulaması (.exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.  
  
 Örnek gösterir nasıl:  
  
-   Bir istemci, kullanıcı adı parola birleşimi kullanarak kimlik doğrulaması yapabilirsiniz.  
  
-   Sunucu, istemci kimlik bilgileri karşı doğrulayabilir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] üyelik sağlayıcısı.  
  
-   Sunucu, sunucunun X.509 sertifikası kullanılarak doğrulanabilir.  
  
-   Sunucunun kimliği doğrulanmış istemciyi bir role kullanarak eşleyebilirsiniz [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] rol sağlayıcısı.  
  
-   Sunucu kullanabilir `PrincipalPermissionAttribute` erişimi denetlemek için hizmet tarafından sunulan belirli yöntem.  
  
 Üyelik ve rol sağlayıcıları, SQL Server tarafından desteklenen bir deposunu kullanmak üzere yapılandırılır. Bir bağlantı dizesi ve çeşitli seçenekleri hizmet yapılandırma dosyasında belirtilir. Üyelik sağlayıcısının adı verilen `SqlMembershipProvider` rol sağlayıcısı adı verilen sırada `SqlRoleProvider`.  
  
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
  
 Hizmet, Web.config yapılandırma dosyası kullanılarak tanımlanmış hizmet ile iletişim kurmak için tek bir uç noktayı kullanıma sunar. Uç nokta, adres, bağlama ve bir sözleşme oluşur. Bir standart yapılandırılmış bağlama `wsHttpBinding`, bunun varsayılan Windows kimlik doğrulaması için kullanılacak. Bu örnek, standart ayarlar `wsHttpBinding` kullanıcı adı kimlik doğrulaması kullanmak için. Sunucu sertifikası hizmet kimlik doğrulaması için kullanılacak olan davranışını belirtir. Sunucu sertifikası için aynı değeri içermelidir `SubjectName` olarak `findValue` özniteliğini [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) yapılandırma öğesi. Buna ek olarak söz konusu kimlik doğrulamasını davranışı belirtir kullanıcı adı parola çiftleri tarafından gerçekleştirilir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] üyelik sağlayıcısı ve rol eşlemesi tarafından gerçekleştirilir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] iki sağlayıcıları için tanımlanan adlar belirterek rol sağlayıcısı.  
  
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
  
 İstemci örneği çalıştırdığınızda, altında üç farklı kullanıcı hesapları çeşitli hizmet işlemleri çağırır: Alice, Bob ve Cahit. İşlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir. Başarısız olması "Gamze adlı" kullanıcı olarak yapılan tüm dört çağrıları. Kullanıcı "Bob", bir erişim reddedildi hatası bölme yöntem çağrılmaya çalışılırken almanız gerekir. Kullanıcı "Cahit" erişim reddedildi hatası çağrılmaya çalışılırken almanız gerekir yöntemi ile çarpın. İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
2.  Yapılandırdığınızdan emin olun [ASP.NET uygulama hizmetleri veritabanına](https://go.microsoft.com/fwlink/?LinkId=94997).  
  
    > [!NOTE]
    >  SQL Server Express Edition çalıştırıyorsanız, sunucu adıdır. \SQLEXPRESS. Bu sunucu yapılandırırken kullanılmalıdır [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uygulama hizmetleri veritabanına de Web.config bağlantı dizesi olduğu gibi.  
  
    > [!NOTE]
    >  [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Çalışan işlem hesabı, bu adımda oluşturulan veritabanı üzerinde izinleri olmalıdır. Bunu yapmak için SQL Server Management Studio ve sqlcmd yardımcı programını kullanın.  
  
3.  Tek veya çoklu bilgisayar yapılandırmasında örneği çalıştırmak için aşağıdaki yönergeleri kullanın.  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>Örneği aynı bilgisayarda çalıştırmak için  
  
1.  Yolun Makecert.exe bulunduğu klasörü içerdiğinden emin olun.  
  
2.  Visual Studio komut istemini yönetici ayrıcalıklarıyla çalıştırın örnek yükleme klasöründe Setup.bat çalıştırın. Bu örneği çalıştırmak için gereken hizmet sertifikaları yükler.  
  
3.  Client.exe \client\bin başlatın. İstemci etkinliği istemci konsol uygulamasında görüntülenir.  
  
4.  İstemci ve hizmet iletişim kurabildiğini bilmiyorsanız bkz [sorun giderme ipuçları](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-run-the-sample-across-computers"></a>Bilgisayarlar arasında örneği çalıştırmak için  
  
1.  Hizmet bilgisayarda bir dizin oluşturun. Internet Information Services (IIS) yönetim aracını kullanarak bu dizin için servicemodelsamples adlı sanal bir uygulama oluşturun.  
  
2.  Hizmet program dosyaları \inetpub\wwwroot\servicemodelsamples hizmeti bilgisayarında sanal dizinine kopyalayın. Dosyaları \bin alt dizinde kopyalama emin olun. Ayrıca hizmet bilgisayara Setup.bat GetComputerName.vbs ve Cleanup.bat dosyaları kopyalayın.  
  
3.  İstemci ikili dosyaları için istemci bilgisayarda bir dizin oluşturun.  
  
4.  İstemci program dosyaları istemci bilgisayarda istemci dizinine kopyalayın. Aynı zamanda istemciye Setup.bat Cleanup.bat ve ImportServiceCert.bat dosyaları kopyalayın.  
  
5.  Sunucusunda, yönetici ayrıcalıklarına sahip bir Visual Studio komut istemi açın ve çalıştırın `setup.bat service`. Çalışan `setup.bat` ile `service` bağımsız değişkeni bilgisayarın tam etki alanı adı ile bir hizmet sertifikası oluşturur ve hizmet sertifikası Service.cer adlı bir dosyaya dışarı aktarır.  
  
6.  Yeni sertifika adını yansıtacak şekilde Web.config'i düzenlemek (içinde `findValue` özniteliğini [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), bilgisayarın tam etki alanı adıyla aynı olduğu.  
  
7.  Service.cer dosya hizmeti dizinden istemci bilgisayarda istemci dizinine kopyalayın.  
  
8.  İstemci bilgisayarda Client.exe.config dosyasında hizmetinizin yeni adresiyle eşleşecek şekilde uç nokta adresi değiştirin.  
  
9. İstemci, yönetici ayrıcalıklarına sahip bir Visual Studio komut istemi açın ve ImportServiceCert.bat çalıştırın. Bu hizmet sertifikası Service.cer dosyasından CurrentUser - TrustedPeople deposuna aktarır.  
  
10. İstemci bilgisayarda bir komut istemi'nden Client.exe başlatın. İstemci ve hizmet iletişim kurabildiğini bilmiyorsanız bkz [sorun giderme ipuçları](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-clean-up-after-the-sample"></a>Sonra örnek temizlemek için  
  
-   Örnek çalıştıran tamamladıktan sonra Cleanup.bat samples klasöründe çalıştırın.  
  
> [!NOTE]
>  Bu betik, bu örnek, bilgisayarlar arasında çalıştırırken bir istemcide hizmet sertifikaları kaldırmaz. Bilgisayarlar arasında sertifikaları kullanan bir Windows Communication Foundation (WCF) örnekleri çalıştırırsanız, CurrentUser - TrustedPeople deposu yüklü hizmet sertifikalarını Temizle emin olun. Bunu yapmak için aşağıdaki komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` örneğin: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
  
## <a name="the-setup-batch-file"></a>Kurulum toplu iş dosyası  
 Bu örnekle dahil Setup.bat toplu iş dosyası ile ilgili sertifika sunucusu sertifika tabanlı güvenlik gerektiren şirket içinde barındırılan bir uygulamayı çalıştırmak için sunucu yapılandırmanıza olanak sağlar. Bu toplu iş dosyası bilgisayarlarda çalışmaya veya barındırılan olmayan bir durumda çalışması için değiştirilmesi gerekir.  
  
 Aşağıda, böylece uygun yapılandırmasında çalıştırılacak değiştirilebilir toplu iş dosyaları farklı bölümlerini kısa bir genel bakış sağlar.  
  
-   Sunucu sertifikası oluşturuluyor.  
  
     Setup.bat toplu iş dosyasından aşağıdaki satırları kullanılacak sunucu sertifikası oluşturun. % Sunucu_adı % değişkeni, sunucu adını belirtir. Kendi sunucu adını belirtmek için bu değişkeni değiştirin. Bu toplu iş dosyası için localhost olarak varsayılır.  
  
     Sertifikayı LocalMachine depolama konumu altında (Kişisel) My deposunda depolanır.  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   Sunucu sertifikasını istemcinin güvenilen sertifika depolama alanına yükleniyor.  
  
     İstemci güvenilir kişiler uygulamasına Setup.bat toplu dosya kopyalama sunucu sertifikasının aşağıdaki satırları depolayın. MakeCert.exe tarafından oluşturulan sertifikaları örtük olarak istemci sistemi tarafından güvenilir değildir çünkü bu adım gereklidir. Bir istemci güvenilen kök sertifikayı kök erişim izni verilmiş bir sertifika zaten varsa — örneğin, Microsoft tarafından verilen sertifika — sunucu sertifikasında istemci sertifika deposunun doldurulması, bu adım gerekli değildir.  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.
