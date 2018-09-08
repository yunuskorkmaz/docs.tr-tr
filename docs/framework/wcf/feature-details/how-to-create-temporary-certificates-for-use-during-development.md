---
title: 'Nasıl yapılır: Geliştirme Sırasında Kullanmak için Geçici Sertifikalar Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], creating temporary certificates
- temporary certificates [WCF]
ms.assetid: bc5f6637-5513-4d27-99bb-51aad7741e4a
ms.openlocfilehash: ca495c23b30144013b8efe22b7bf6f3cf38b16cd
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44195722"
---
# <a name="how-to-create-temporary-certificates-for-use-during-development"></a>Nasıl yapılır: Geliştirme Sırasında Kullanmak için Geçici Sertifikalar Oluşturma
Güvenli hizmet veya Windows Communication Foundation (WCF) kullanan istemci geliştirirken, genellikle bir kimlik bilgisi olarak kullanılacak bir X.509 sertifikası sağlamak gereklidir. Sertifika bilgisayar güvenilen kök sertifika yetkilileri deposunda bulunan kök yetkilisi sertifikalarıyla oluşan bir zincir, genellikle parçasıdır. Bir sertifika zinciri olan sertifika genellikle kök yetkilisi kuruluşunuz veya iş birimi olduğu kümesi kapsam olanak tanır. Bu geliştirme zamanında benzetmek için güvenlik gereksinimlerini karşılamak için iki sertifika oluşturabilirsiniz. İlk otomatik olarak imzalanan bir sertifika olduğundan güvenilen kök sertifika yetkilileri deposunda yerleştirilir ve ikinci sertifikayı ilk konumdan oluşturulur ve yerel makine konumun Kişisel depolama alanı kişisel mağazasında şirket içinde veya yerleştirilir. Geçerli kullanıcı konumu. Bu konuda, Powershell kullanarak bu iki sertifikaları oluşturma adımlarında size kılavuzluk eder [New-SelfSignedCertificate)](https://docs.microsoft.com/en-us/powershell/module/pkiclient/new-selfsignedcertificate?view=win10-ps) cmdlet'i.  
  
> [!IMPORTANT]
>  New-SelfSignedCertificate cmdlet oluşturur sertifikalar yalnızca sınama amacıyla sağlanır. Bir hizmet veya istemci dağıtımı sırasında bir sertifika yetkilisi tarafından sağlanan uygun bir sertifikayı kullanmak emin olun. Bu, kuruluşunuzdaki Windows Server sertifika sunucusu arasında ya da üçüncü bir tarafa.  
>   
>  Varsayılan olarak, [New-SelfSignedCertificate](https://docs.microsoft.com/en-us/powershell/module/pkiclient/new-selfsignedcertificate?view=win10-ps) cmdlet'i otomatik olarak imzalanan sertifikalar oluşturur ve bu sertifikaları güvenli değil. Otomatik olarak imzalanan sertifikaları Güvenilen kök sertifika yetkilileri yerleştirme store dağıtım ortamınızı daha yakından taklit eden bir geliştirme ortamı olarak oluşturmanıza olanak sağlar.  
  
 Oluşturma ve sertifikaları kullanma hakkında daha fazla bilgi için bkz. [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md). Bir kimlik bilgisi olarak bir sertifika kullanma hakkında daha fazla bilgi için bkz. [Hizmetleri güvenli hale getirme ve istemciler](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md). Microsoft Authenticode teknolojisi kullanılarak hakkında bir öğretici için bkz [Authenticode genel bakış ve öğreticiler](https://go.microsoft.com/fwlink/?LinkId=88919).  
  
### <a name="to-create-a-self-signed-root-authority-certificate-and-export-the-private-key"></a>Otomatik olarak imzalanan kök yetkilisi sertifikası oluşturma ve özel anahtarı dışarı aktar  
  
Aşağıdaki komut, "RootCA" geçerli kullanıcının kişisel depoda bir konu adıyla otomatik olarak imzalanan bir sertifika oluşturur. 
```
PS $rootCert = New-SelfSignedCertificate -CertStoreLocation cert:\CurrentUser\My -DnsName "RootCA" -TextExtension @("1.3.6.1.4.1.311.21.10={text}1.3.6.1.5.5.7.3.1,1.3.6.1.5.5.7.3.2")
```
Böylece daha sonraki bir adımda gerekli yerlerde için aktarılabilen sertifikayı bir PFX dosyasına aktarmak ihtiyacımız var. Özel anahtara sahip bir sertifika verilirken korunması için bir parola gereklidir. Biz Parolayı Kaydet bir `SecureString` ve [dışarı aktarma-PfxCertificate](https://docs.microsoft.com/en-us/powershell/module/pkiclient/export-pfxcertificate?view=win10-ps) sertifikayı bir PFX dosyasına ilişkili özel anahtarla dışarı aktarmak için cmdlet'ini. Biz CRT kullanarak dosyanın içine de yalnızca ortak sertifikayı kaydetmek [sertifika verme](https://docs.microsoft.com/en-us/powershell/module/pkiclient/export-certificate?view=win10-ps) cmdlet'i.
```
PS [System.Security.SecureString]$rootcertPassword = ConvertTo-SecureString -String "password" -Force -AsPlainText
PS [String]$rootCertPath = Join-Path -Path 'cert:\CurrentUser\My\' -ChildPath "$($rootcert.Thumbprint)"
PS Export-PfxCertificate -Cert $rootCertPath -FilePath 'RootCA.pfx' -Password $rootcertPassword
PS Export-Certificate -Cert $rootCertPath -FilePath 'RootCA.crt'
```

### <a name="to-create-a-new-certificate-signed-by-a-root-authority-certificate"></a>Kök yetkilisi sertifikası tarafından imzalanmış yeni bir sertifika oluşturmak için  
  
Aşağıdaki komut tarafından imzalanmış bir sertifika oluşturur `RootCA` "SignedByRootCA verenin özel anahtarı kullanarak", bir konu adına sahip.
```
PS $testCert = New-SelfSignedCertificate -CertStoreLocation Cert:\LocalMachine\My -DnsName "SignedByRootCA" -KeyExportPolicy Exportable -KeyLength 2048 -KeyUsage DigitalSignature,KeyEncipherment -Signer $rootCert 
```
Benzer şekilde, biz imzalı sertifikanın özel anahtara sahip bir PFX dosyası ve ortak anahtarı yalnızca bir CRT dosyasına kaydedin.
```
PS [String]$testCertPath = Join-Path -Path 'cert:\LocalMachine\My\' -ChildPath "$($testCert.Thumbprint)"
PS Export-PfxCertificate -Cert $testCertPath -FilePath testcert.pfx -Password $rootcertPassword 
PS Export-Certificate -Cert $testCertPath -FilePath testcert.crt        
```
  
## <a name="installing-a-certificate-in-the-trusted-root-certification-authorities-store"></a>Güvenilen kök sertifika yetkilileri Store sertifika yükleme  
 Kendinden imzalı bir sertifika oluşturulduktan sonra güvenilen kök sertifika yetkilileri deposunda yükleyebilirsiniz. İmzalanmış herhangi bir sertifika ile bu noktada sertifika, bilgisayar tarafından güvenilmiyor. Artık ihtiyacınız hemen sonra bu nedenle, sertifika deposundan silin. İle imzalanmış tüm sertifikaları bu kök yetkilisi sertifikası sildiğinizde, yetkisiz haline gelir. Kök yetkilisi sertifikaları yapabildiği sertifikaların bir grup gerektiğinde kapsamlandırılabilir olarak yalnızca bir mekanizması mevcuttur. Örneğin, eşler arası uygulamalar, genellikle gerek yoktur kök yetkilisi için yalnızca bir bireyin kimliği tarafından sağlanan, sertifika güven için.  
  
#### <a name="to-install-a-self-signed-certificate-in-the-trusted-root-certification-authorities"></a>Güvenilen kök sertifika yetkilileri otomatik olarak imzalanan bir sertifika yüklemek için  
  
1.  Sertifika ek bileşenini açın. Daha fazla bilgi için [nasıl yapılır: MMC ek bileşeni ile sertifikaları görüntüleme](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).  
  
2.  Sertifika ya da depolamak için klasörü açın **yerel bilgisayar** veya **geçerli kullanıcının**.  
  
3.  Açık **güvenilen kök sertifika yetkilileri** klasör.  
  
4.  Sağ tıklayın **sertifikaları** klasörü ve tıklatın **tüm görevler**, ardından **alma**.  
  
5.  Ekrandaki Sihirbazı izleyin TempCa.cer depoya içeri aktarma yönergeleri.  
  
## <a name="using-certificates-with-wcf"></a>WCF ile sertifikaları kullanma  
 Geçici sertifikalar ayarladıktan sonra sertifikaları bir istemci kimlik bilgisi türü belirtin WCF çözümleri geliştirmek için kullanabilirsiniz. Örneğin, aşağıdaki XML yapılandırması ileti güvenliği ve bir sertifika istemci kimlik bilgileri türünü belirtir.  
  
#### <a name="to-specify-a-certificate-as-the-client-credential-type"></a>Sertifika istemci kimlik bilgisi türü belirtmek için  
  
-   Hizmet yapılandırma dosyasında aşağıdaki XML iletisi ve sertifika için istemci kimlik bilgisi türü güvenlik modu ayarlamak için kullanın.  
  
    ```xml  
    <bindings>       
      <wsHttpBinding>  
        <binding name="CertificateForClient">  
          <security>  
            <message clientCredentialType="Certificate" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    ```  
  
 Bir istemci için yapılandırma dosyasında, sertifikası olan bir kullanıcının deposunda bulunamadı ve SubjectName alanın değeri "CohoWinery." için arama yaparak bulunabilir belirtmek için aşağıdaki XML kullanın.  
  
```xml  
<behaviors>  
  <endpointBehaviors>  
    <behavior name="CertForClient">  
      <clientCredentials>  
        <clientCertificate findValue="CohoWinery" x509FindType="FindBySubjectName" />  
       </clientCredentials>  
     </behavior>  
   </endpointBehaviors>  
</behaviors>  
```  
  
 WCF'de sertifikaları kullanma hakkında daha fazla bilgi için bkz. [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Geçici kök yetkilisi sertifikalarını sildiğinizden emin olun **güvenilen kök sertifika yetkilileri** ve **kişisel** sertifikayı sağ tıklatıp sonra tıklatarak klasörleri  **Silme**.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sertifikalarla Çalışma](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Nasıl yapılır: MMC Ek Bileşeni ile Sertifikaları Görüntüleme](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)  
 [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
