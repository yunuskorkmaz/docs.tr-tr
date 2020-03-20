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
# <a name="membership-and-role-provider"></a>Üyelik ve Rol Sağlayıcısı
Üyelik ve Rol Sağlayıcı örneği, bir hizmetin ASP.NET üyeliği ve rol sağlayıcıları istemcileri doğrulamak ve yetkilendirmek için nasıl kullanabileceğini gösterir.  
  
 Bu örnekte, istemci bir konsol uygulamasıdır (.exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.  
  
> [!NOTE]
> Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.  
  
 Örnek, aşağıdakileri gösterir:  
  
- İstemci, kullanıcı adı-parola birleşimini kullanarak kimlik doğrulaması yapabilir.  
  
- Sunucu, istemci kimlik bilgilerini ASP.NET üyelik sağlayıcısına karşı doğrulayabilir.  
  
- Sunucunun X.509 sertifikası kullanılarak sunucunun kimliği doğrulanabilir.  
  
- Sunucu, ASP.NET rol sağlayıcısını kullanarak kimlik doğrulaması yapılan istemciyi bir role eşleyebilir.  
  
- Sunucu, hizmet `PrincipalPermissionAttribute` tarafından açığa çıkarılan belirli yöntemlere erişimi denetlemek için kullanabilir.  
  
 Üyelik ve rol sağlayıcıları, SQL Server tarafından desteklenen bir depoyu kullanacak şekilde yapılandırılır. Hizmet yapılandırma dosyasında bir bağlantı dizesi ve çeşitli seçenekler belirtilir. Rol sağlayıcısına ad `SqlMembershipProvider` `SqlRoleProvider`verilirken, üyelik sağlayıcısına ad verilir.  
  
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
  
 Hizmet, Web.config yapılandırma dosyasını kullanarak tanımlanan hizmetle iletişim kurmak için tek bir bitiş noktasını ortaya çıkarır. Bitiş noktası bir adres, bir bağlama ve sözleşmeden oluşur. Bağlama, Windows kimlik doğrulaması kullanmaya varsayılan bir standartla `wsHttpBinding`yapılandırılır. Bu örnek, `wsHttpBinding` kullanıcı adı kimlik doğrulaması kullanmak için standart ayarlar. Davranış, sunucu sertifikasının hizmet kimlik doğrulaması için kullanılacağını belirtir. Sunucu sertifikası, [ \<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) `SubjectName` yapılandırma `findValue` öğesindeki öznitelikle aynı değeri içermelidir. Buna ek olarak, kullanıcı adı-parola çiftleri kimlik doğrulamasının ASP.NET üyelik sağlayıcısı tarafından gerçekleştirildiğini ve rol eşlemenin ASP.NET rol sağlayıcısı tarafından iki sağlayıcı için tanımlanan adlar belirtilerek gerçekleştirildiğini belirtir.  
  
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
  
 Örneği çalıştırdığınızda, istemci üç farklı kullanıcı hesabı altında çeşitli hizmet işlemlerini çağırır: Alice, Bob ve Charlie. İşlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir. Kullanıcı "Alice" olarak yapılan dört aramanın tümü başarılı olmalıdır. Kullanıcı "Bob" B) yöntemini aramaya çalışırken erişim reddedilen bir hata almalıdır. Kullanıcı "Charlie" Çarpma yöntemini aramaya çalışırken erişim reddedilen bir hata almalıdır. İstemciyi kapatmak için istemci penceresinde ENTER tuşuna basın.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için Windows Communication Foundation Örneklerini Çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.  
  
2. [ASP.NET Uygulama Hizmetleri Veritabanını](https://go.microsoft.com/fwlink/?LinkId=94997)yapılandırdığınızdan emin olun.  
  
    > [!NOTE]
    > SQL Server Express Edition çalıştırıyorsanız, sunucu adınız .\SQLEXPRESS'tir. Bu sunucu, ASP.NET Uygulama Hizmetleri Veritabanı'nı ve Web.config bağlantı dizesini yapılandırırken kullanılmalıdır.  
  
    > [!NOTE]
    > ASP.NET işlemesi hesabının bu adımda oluşturulan veritabanında izinleri olmalıdır. Bunu yapmak için sqlcmd yardımcı programını veya SQL Server Management Studio'yu kullanın.  
  
3. Örneği tek veya bilgisayar lar arası yapılandırmada çalıştırmak için aşağıdaki yönergeleri kullanın.  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>Örneği aynı bilgisayarda çalıştırmak için  
  
1. Yolun Makecert.exe'nin bulunduğu klasörü içerdiğinden emin olun.  
  
2. Setup.bat'ı visual studio için Geliştirici Komut Komut Ustem'de yönetici ayrıcalıklarıyla çalıştırın örnek yükleme klasöründen çalıştırın. Bu, örneği çalıştırmak için gereken hizmet sertifikalarını yükler.  
  
3. Client.exe'yi \client\bin'den başlatın. İstemci etkinliği istemci konsoluygulamasında görüntülenir.  
  
4. İstemci ve hizmet iletişim kuramazsa, [WCF Örnekleri için Sorun Giderme İpuçları'na](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))bakın.  
  
### <a name="to-run-the-sample-across-computers"></a>Örneği bilgisayarlarda çalıştırmak için  
  
1. Hizmet bilgisayarında bir dizin oluşturun. Internet Information Services (IIS) yönetim aracını kullanarak bu dizin için servicemodelsamples adlı sanal bir uygulama oluşturun.  
  
2. Hizmet programı dosyalarını \inetpub\wwwroot\servicemodelsamples'ten hizmet bilgisayarındaki sanal dizine kopyalayın. \bin alt dizinindeki dosyaları kopyaladığınızdan emin olun. Ayrıca Setup.bat, GetComputerName.vbs ve Cleanup.bat dosyalarını servis bilgisayarına kopyalayın.  
  
3. İstemci ikilileri için istemci bilgisayarında bir dizin oluşturun.  
  
4. İstemci programı dosyalarını istemci bilgisayarındaki istemci dizinine kopyalayın. Ayrıca Setup.bat, Cleanup.bat ve ImportServiceCert.bat dosyalarını istemciye kopyalayın.  
  
5. Sunucuda, yönetim ayrıcalıkları olan Visual Studio için geliştirici `setup.bat service`komut istemini açın ve çalıştırın. Bağımsız değişkenle birlikte çalışmak, `setup.bat` bilgisayarın tam nitelikli etki alanı adı içeren bir hizmet sertifikası oluşturur ve hizmet sertifikasını Service.cer adlı bir dosyaya aktarın. `service`  
  
6. Web.config'i bilgisayarın tam nitelikli alan `findValue` adı ile aynı olan yeni sertifika adını [ \<(serviceCertificate>'daki ](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)öznitelikte) yansıtacak şekilde edin.  
  
7. Service.cer dosyasını servis dizininden istemci bilgisayarındaki istemci dizinine kopyalayın.  
  
8. İstemci bilgisayarındaki Client.exe.config dosyasında, hizmetinyeni adresiyle eşleşecek şekilde bitiş noktasının adres değerini değiştirin.  
  
9. İstemcide, yönetim ayrıcalıklarına sahip Visual Studio için bir Geliştirici Komut Komut Ustem'i açın ve ImportServiceCert.bat çalıştırın. Bu, hizmet sertifikasını Service.cer dosyasından CurrentUser - Trusted People deposuna aktarabilir.  
  
10. İstemci bilgisayarında, istemci.exe'yi komut isteminden başlatın. İstemci ve hizmet iletişim kuramazsa, [WCF Örnekleri için Sorun Giderme İpuçları'na](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))bakın.  
  
### <a name="to-clean-up-after-the-sample"></a>Örnekten sonra temizlemek için  
  
- Örneği çalıştırmayı bitirdikten sonra örnekler klasöründe Cleanup.bat çalıştırın.  
  
> [!NOTE]
> Bu komut dosyası, bu örneği bilgisayarlar da çalıştırırken istemcideki hizmet sertifikalarını kaldırmaz. Bilgisayarlar arasında sertifika kullanan Windows Communication Foundation (WCF) örneklerini çalıştırdıysanız, CurrentUser - Trusted People mağazasında yüklenen hizmet sertifikalarını temizlediğinizden emin olun. Bunu yapmak için aşağıdaki komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` Örneğin: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
  
## <a name="the-setup-batch-file"></a>Kurulum Toplu Dosyası  
 Bu örnekte yer alan Setup.bat toplu dosyası, sunucu sertifikası tabanlı güvenlik gerektiren kendi kendine barındırılan bir uygulamayı çalıştırmak için sunucuyu ilgili sertifikalarla yapılandırmanıza olanak tanır. Bu toplu iş dosyası, bilgisayarlar arasında çalışmak veya barındırılmayan bir durumda çalışmak için değiştirilmelidir.  
  
 Aşağıda, uygun yapılandırmada çalışacak şekilde değiştirilebilmeleri için toplu iş dosyalarının farklı bölümlerine kısa bir genel bakış sağlanacaktır.  
  
- Sunucu sertifikası oluşturma.  
  
     Setup.bat toplu dosyasından aşağıdaki satırlar kullanılacak sunucu sertifikasını oluşturur. %SERVER_NAME değişkeni sunucu adını belirtir. Kendi sunucu adınızı belirtmek için bu değişkeni değiştirin. Bu toplu iş dosyası varsayılan olarak localhost'a aktarır.  
  
     Sertifika, LocalMachine mağazasının altında Benim (Kişisel) mağazamda depolanır.  
  
    ```console
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
- Sunucu sertifikasını istemcinin güvenilir sertifika deposuna yükleme.  
  
     Setup.bat toplu iş dosyasındaki aşağıdaki satırlar, sunucu sertifikasını istemcigüvenilir kişiler deposuna kopyalar. Makecert.exe tarafından oluşturulan sertifikalar istemci sistemi tarafından dolaylı olarak güvenilen olmadığından bu adım gereklidir. İstemci tarafından güvenilen kök sertifikasına dayanan bir sertifikanız varsa (örneğin, Microsoft tarafından verilmiş bir sertifika- istemci sertifika deposunu sunucu sertifikasıyla doldurma adımı gerekli değildir.  
  
    ```bat  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
