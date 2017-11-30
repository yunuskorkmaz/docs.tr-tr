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
# <a name="membership-and-role-provider"></a>Üyelik ve Rol Sağlayıcısı
Üyelik ve rol sağlayıcısı örneği, bir hizmetin nasıl kullanabileceğinizi gösterir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] kimlik doğrulama ve yetkilendirme istemciler için üyelik ve rol sağlayıcıları.  
  
 Bu örnekte, istemci bir konsol uygulaması (.exe) ve Internet Information Services (IIS) tarafından barındırılan hizmetindeki.  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
 Örnek gösterir nasıl:  
  
-   Bir istemci, kullanıcı adı parola birleşimi kullanılarak doğrulanabilir.  
  
-   Sunucu, istemci kimlik bilgilerine karşı doğrulayabilirsiniz [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] üyelik sağlayıcısı.  
  
-   Sunucu, sunucunun X.509 sertifikası kullanılarak doğrulanabilir.  
  
-   Sunucunun kimliği doğrulanmış istemciyi bir role kullanarak eşleyebilirsiniz [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] rol sağlayıcısı.  
  
-   Sunucu kullanabilir `PrincipalPermissionAttribute` hizmeti tarafından sunulan belirli yöntemlerine erişimi denetleme.  
  
 Üyelik ve rol sağlayıcılarını SQL sunucusu tarafından desteklenen bir deposunu kullanacak şekilde yapılandırılır. Bir bağlantı dizesi ve çeşitli seçenekleri hizmet yapılandırma dosyasında belirtilir. Üyelik sağlayıcısının adı verilen `SqlMembershipProvider` rol sağlayıcısı adı verilen sırada `SqlRoleProvider`.  
  
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
  
 Hizmet Web.config yapılandırma dosyası kullanılarak tanımlanmış hizmeti ile iletişim kurmak için tek bir uç noktasını kullanıma sunar. Uç nokta bir adresi, bağlama ve bir sözleşme oluşur. Bağlama ile standart bir yapılandırılmış `wsHttpBinding`, Windows kimlik doğrulaması için kullanılacak varsayılan olarak. Bu örnek standart ayarlar `wsHttpBinding` kullanıcı adı kimlik doğrulaması kullanacak şekilde. Sunucu sertifikası için hizmet kimlik doğrulaması kullanılacaksa davranışını belirtir. Sunucu sertifikası için aynı değeri içermelidir `SubjectName` olarak `findValue` özniteliğini [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) yapılandırma öğesi. Ayrıca, kimlik doğrulamasının davranışını belirten kullanıcı adı parola çiftleri tarafından gerçekleştirilir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] üyelik sağlayıcısı ve rol eşleme tarafından gerçekleştirilir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] iki sağlayıcıları için tanımlanan adlar belirterek rol sağlayıcısı.  
  
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
  
 Örneği çalıştırdığınızda, istemci altında üç farklı kullanıcı hesapları çeşitli hizmet işlemlerini çağırır: Alice, Bob ve Cahit. İşlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir. "Alice" tamamlanacak kullanıcı olarak yapılan tüm dört çağırır. Kullanıcı "Bob", bir erişim reddedildi hatası bölme yöntemini çağırmak çalışırken almanız gerekir. Kullanıcı "Cahit" bir erişim reddedildi hatası çağrılmaya çalışılırken alır yöntemi çarpın. İstemcisi penceresinde istemciyi aşağı kapatmak için ENTER tuşuna basın.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
2.  Yapılandırdığınızdan emin olun [ASP.NET uygulama hizmetleri veritabanına](http://go.microsoft.com/fwlink/?LinkId=94997).  
  
    > [!NOTE]
    >  SQL Server Express Edition çalıştırıyorsanız, sunucu adıdır. \SQLEXPRESS. Bu sunucuyu yapılandırırken kullanılmalıdır [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uygulama hizmetleri veritabanına de olduğu gibi Web.config bağlantı dizesidir.  
  
    > [!NOTE]
    >  [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Çalışan işlem hesabı, bu adımda oluşturulan veritabanı üzerinde izinleri olmalıdır. Bunu yapmak için sqlcmd yardımcı programını veya SQL Server Management Studio kullanın.  
  
3.  Tek veya çapraz bilgisayar yapılandırmasında örneği çalıştırmak için aşağıdaki yönergeleri kullanın.  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>Aynı bilgisayara örneği çalıştırmak için  
  
1.  Yolun Makecert.exe bulunduğu klasörü içerdiğinden emin olun.  
  
2.  Visual Studio komut istemini yönetici ayrıcalıklarıyla çalıştırın örnek yükleme klasöründeki Setup.bat çalıştırın. Bu örneği çalıştırmak için gereken hizmet sertifikaları yükler.  
  
3.  Client.exe \client\bin başlatın. İstemci etkinliği istemci konsol uygulaması görüntülenir.  
  
4.  İstemci ve hizmet iletişim kurabildiğinden değilseniz bkz [sorun giderme ipuçları](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-run-the-sample-across-computers"></a>Bilgisayarlar arasında örneği çalıştırmak için  
  
1.  Hizmet bilgisayarda bir dizin oluşturun. Internet Information Services (IIS) yönetim aracını kullanarak bu dizin için servicemodelsamples adlı bir sanal uygulama oluşturun.  
  
2.  Hizmet program dosyalarını \inetpub\wwwroot\servicemodelsamples hizmeti bilgisayarında sanal dizinine kopyalayın. \Bin alt dizinindeki dosyaları kopyalayın emin olun. Ayrıca Setup.bat, GetComputerName.vbs ve Cleanup.bat dosyaları hizmet bilgisayara kopyalayın.  
  
3.  İstemci ikili dosyalarının için istemci bilgisayarda bir dizin oluşturun.  
  
4.  İstemci program dosyaları istemci bilgisayarda istemci dizinine kopyalayın. Ayrıca istemciye Setup.bat, Cleanup.bat ve ImportServiceCert.bat dosyalarını kopyalayın.  
  
5.  Sunucusunda yönetici ayrıcalıklarına sahip bir Visual Studio komut istemi açın ve Çalıştır `setup.bat service`. Çalışan `setup.bat` ile `service` bağımsız değişkeni bilgisayarın tam etki alanı adı ile bir hizmet sertifikası oluşturur ve hizmet sertifikası Service.cer adlı bir dosyaya aktarır.  
  
6.  Web.config dosyasını yeni sertifika yansıtacak şekilde düzenleyin (içinde `findValue` özniteliğini [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), bilgisayarın tam etki alanı adı ile aynı olduğu.  
  
7.  Service.cer dosya hizmeti dizininden istemci bilgisayarda istemci dizinine kopyalayın.  
  
8.  İstemci bilgisayardaki Client.exe.config dosyasında yeni adresi hizmetinizin eşleştirmek için uç nokta adresi değerini değiştirin.  
  
9. İstemci üzerinde yönetici ayrıcalıklarına sahip bir Visual Studio komut istemi açın ve ImportServiceCert.bat çalıştırın. Bu hizmet sertifikası Service.cer dosyadan Currentuser'a - TrustedPeople deposunu alır.  
  
10. İstemci bilgisayarda bir komut isteminden Client.exe başlatın. İstemci ve hizmet iletişim kurabildiğinden değilseniz bkz [sorun giderme ipuçları](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-clean-up-after-the-sample"></a>Örnek sonra temizlemek için  
  
-   Örnek çalıştıran bitirdikten sonra Cleanup.bat samples klasöründen çalıştırın.  
  
> [!NOTE]
>  Bu komut, bu örnek bilgisayarlar arasında çalıştırırken bir istemcide hizmet sertifikaları kaldırmaz. Çalıştırırsanız [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] bilgisayarlar arasında sertifikaları kullanma örnekleri Currentuser'a - TrustedPeople deposu yüklü hizmet sertifikalarını temizlemek emin olun. Bunu yapmak için aşağıdaki komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` örneğin: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
  
## <a name="the-setup-batch-file"></a>Kurulum toplu iş dosyası  
 Bu örnekle dahil Setup.bat toplu iş dosyası, sunucu sertifika tabanlı güvenlik gerektiren kendini barındıran bir uygulamayı çalıştırmak için ilgili sertifikalarla sunucu yapılandırmanıza olanak sağlar. Bu toplu iş dosyası bilgisayarlar arasında iş ya da barındırılan olmayan bir durumda çalışması için değiştirilmesi gerekir.  
  
 Aşağıdakiler, böylece uygun yapılandırmada çalışacak biçimde değiştirilebilir toplu iş dosyaları farklı bölümlerini kısa bir genel bakış sağlar.  
  
-   Sunucu sertifikası oluşturuluyor.  
  
     Aşağıdaki satırları Setup.bat toplu iş dosyasından kullanılacak sunucu sertifikası oluşturun. % Sunucu_adı % değişkeni sunucusunun adını belirtir. Kendi sunucu adını belirtmek için bu değişkeni değiştirin. Bu toplu iş dosyası için localhost olarak varsayar.  
  
     Sertifika, LocalMachine depolama konumu altında (Kişisel) My deposunda saklanır.  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   Sunucu sertifikası istemcinin güvenilen sertifika deposuna yükleme.  
  
     İstemci güvenilir kişiler içine Setup.bat toplu dosya kopyalama sunucu sertifikasının aşağıdaki satırları depolar. MakeCert.exe tarafından oluşturulan sertifikaları örtük olarak istemci sistemi tarafından güvenilir değil çünkü bu adım gereklidir. Bir istemci güvenilen kök sertifikasını kökü belirtilmiş bir sertifikanız zaten varsa — örneğin, Microsoft tarafından verilen sertifika — sunucu sertifikasına sahip istemci sertifika deposunun doldurulması, bu adım gerekli değildir.  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.
