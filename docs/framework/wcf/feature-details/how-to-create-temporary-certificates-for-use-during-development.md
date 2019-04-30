---
title: 'Nasıl yapılır: Geliştirme Sırasında Kullanmak için Geçici Sertifikalar Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], creating temporary certificates
- temporary certificates [WCF]
ms.assetid: bc5f6637-5513-4d27-99bb-51aad7741e4a
ms.openlocfilehash: d45f18b0b8fe4e0cc9667091e166c80691faa2d4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61773301"
---
# <a name="how-to-create-temporary-certificates-for-use-during-development"></a>Nasıl yapılır: Geliştirme Sırasında Kullanmak için Geçici Sertifikalar Oluşturma

Güvenli hizmet veya Windows Communication Foundation (WCF) kullanan istemci geliştirirken, genellikle bir kimlik bilgisi olarak kullanılacak bir X.509 sertifikası sağlamak gereklidir. Sertifika bilgisayar güvenilen kök sertifika yetkilileri deposunda bulunan kök yetkilisi sertifikalarıyla oluşan bir zincir, genellikle parçasıdır. Bir sertifika zinciri olan sertifika genellikle kök yetkilisi kuruluşunuz veya iş birimi olduğu kümesi kapsam olanak tanır. Bu geliştirme zamanında benzetmek için güvenlik gereksinimlerini karşılamak için iki sertifika oluşturabilirsiniz. İlk otomatik olarak imzalanan bir sertifika olduğundan güvenilen kök sertifika yetkilileri deposunda yerleştirilir ve ikinci sertifikayı ilk konumdan oluşturulur ve yerel makine konumun Kişisel depolama alanı kişisel mağazasında şirket içinde veya yerleştirilir. Geçerli kullanıcı konumu. Bu konuda, Powershell kullanarak bu iki sertifikaları oluşturma adımlarında size kılavuzluk eder [New-SelfSignedCertificate)](/powershell/module/pkiclient/new-selfsignedcertificate) cmdlet'i.

> [!IMPORTANT]
> New-SelfSignedCertificate cmdlet oluşturur sertifikalar yalnızca sınama amacıyla sağlanır. Bir hizmet veya istemci dağıtımı sırasında bir sertifika yetkilisi tarafından sağlanan uygun bir sertifikayı kullanmak emin olun. Bu, kuruluşunuzdaki Windows Server sertifika sunucusu arasında ya da üçüncü bir tarafa.
>
> Varsayılan olarak, [New-SelfSignedCertificate](/powershell/module/pkiclient/new-selfsignedcertificate) cmdlet'i otomatik olarak imzalanan sertifikalar oluşturur ve bu sertifikaları güvenli değil. Otomatik olarak imzalanan sertifikaları Güvenilen kök sertifika yetkilileri yerleştirme store dağıtım ortamınızı daha yakından taklit eden bir geliştirme ortamı olarak oluşturmanıza olanak sağlar.

 Oluşturma ve sertifikaları kullanma hakkında daha fazla bilgi için bkz. [Working with Certificates](working-with-certificates.md). Bir kimlik bilgisi olarak bir sertifika kullanma hakkında daha fazla bilgi için bkz. [Hizmetleri güvenli hale getirme ve istemciler](securing-services-and-clients.md). Microsoft Authenticode teknolojisi kullanılarak hakkında bir öğretici için bkz [Authenticode genel bakış ve öğreticiler](https://go.microsoft.com/fwlink/?LinkId=88919).

## <a name="to-create-a-self-signed-root-authority-certificate-and-export-the-private-key"></a>Otomatik olarak imzalanan kök yetkilisi sertifikası oluşturma ve özel anahtarı dışarı aktar

Aşağıdaki komut, "RootCA" geçerli kullanıcının kişisel depoda bir konu adıyla otomatik olarak imzalanan bir sertifika oluşturur.

```powershell
PS $rootCert = New-SelfSignedCertificate -CertStoreLocation cert:\CurrentUser\My -DnsName "RootCA" -TextExtension @("1.3.6.1.4.1.311.21.10={text}1.3.6.1.5.5.7.3.1,1.3.6.1.5.5.7.3.2")
```

Böylece daha sonraki bir adımda gerekli yerlerde için aktarılabilen sertifikayı bir PFX dosyasına aktarmak ihtiyacımız var. Özel anahtara sahip bir sertifika verilirken korunması için bir parola gereklidir. Biz Parolayı Kaydet bir `SecureString` ve [dışarı aktarma-PfxCertificate](/powershell/module/pkiclient/export-pfxcertificate) sertifikayı bir PFX dosyasına ilişkili özel anahtarla dışarı aktarmak için cmdlet'ini. Biz CRT kullanarak dosyanın içine de yalnızca ortak sertifikayı kaydetmek [sertifika verme](/powershell/module/pkiclient/export-certificate) cmdlet'i.

```powershell
PS [System.Security.SecureString]$rootcertPassword = ConvertTo-SecureString -String "password" -Force -AsPlainText
PS [String]$rootCertPath = Join-Path -Path 'cert:\CurrentUser\My\' -ChildPath "$($rootcert.Thumbprint)"
PS Export-PfxCertificate -Cert $rootCertPath -FilePath 'RootCA.pfx' -Password $rootcertPassword
PS Export-Certificate -Cert $rootCertPath -FilePath 'RootCA.crt'
```

## <a name="to-create-a-new-certificate-signed-by-a-root-authority-certificate"></a>Kök yetkilisi sertifikası tarafından imzalanmış yeni bir sertifika oluşturmak için

Aşağıdaki komut tarafından imzalanmış bir sertifika oluşturur `RootCA` "SignedByRootCA verenin özel anahtarı kullanarak", bir konu adına sahip.

```powershell
PS $testCert = New-SelfSignedCertificate -CertStoreLocation Cert:\LocalMachine\My -DnsName "SignedByRootCA" -KeyExportPolicy Exportable -KeyLength 2048 -KeyUsage DigitalSignature,KeyEncipherment -Signer $rootCert
```

Benzer şekilde, biz imzalı sertifikanın özel anahtara sahip bir PFX dosyası ve ortak anahtarı yalnızca bir CRT dosyasına kaydedin.

```powershell
PS [String]$testCertPath = Join-Path -Path 'cert:\LocalMachine\My\' -ChildPath "$($testCert.Thumbprint)"
PS Export-PfxCertificate -Cert $testCertPath -FilePath testcert.pfx -Password $rootcertPassword
PS Export-Certificate -Cert $testCertPath -FilePath testcert.crt
```

## <a name="installing-a-certificate-in-the-trusted-root-certification-authorities-store"></a>Güvenilen kök sertifika yetkilileri Store sertifika yükleme

Kendinden imzalı bir sertifika oluşturulduktan sonra güvenilen kök sertifika yetkilileri deposunda yükleyebilirsiniz. İmzalanmış herhangi bir sertifika ile bu noktada sertifika, bilgisayar tarafından güvenilmiyor. Artık ihtiyacınız hemen sonra bu nedenle, sertifika deposundan silin. İle imzalanmış tüm sertifikaları bu kök yetkilisi sertifikası sildiğinizde, yetkisiz haline gelir. Kök yetkilisi sertifikaları yapabildiği sertifikaların bir grup gerektiğinde kapsamlandırılabilir olarak yalnızca bir mekanizması mevcuttur. Örneğin, eşler arası uygulamalar, genellikle gerek yoktur kök yetkilisi için yalnızca bir bireyin kimliği tarafından sağlanan, sertifika güven için.

### <a name="to-install-a-self-signed-certificate-in-the-trusted-root-certification-authorities"></a>Güvenilen kök sertifika yetkilileri otomatik olarak imzalanan bir sertifika yüklemek için

1. Sertifika ek bileşenini açın. Daha fazla bilgi için [nasıl yapılır: MMC ek bileşeni ile sertifikaları görüntüleme](how-to-view-certificates-with-the-mmc-snap-in.md).

2. Sertifika ya da depolamak için klasörü açın **yerel bilgisayar** veya **geçerli kullanıcının**.

3. Açık **güvenilen kök sertifika yetkilileri** klasör.

4. Sağ tıklayın **sertifikaları** klasörü ve tıklatın **tüm görevler**, ardından **alma**.

5. Ekrandaki Sihirbazı izleyin RootCA.pfx depoya içeri aktarma yönergeleri.

## <a name="using-certificates-with-wcf"></a>WCF ile sertifika kullanma

Geçici sertifikalar ayarladıktan sonra sertifikaları bir istemci kimlik bilgisi türü belirtin WCF çözümleri geliştirmek için kullanabilirsiniz. Örneğin, aşağıdaki XML yapılandırması ileti güvenliği ve bir sertifika istemci kimlik bilgileri türünü belirtir.

### <a name="to-specify-a-certificate-as-the-client-credential-type"></a>Sertifika istemci kimlik bilgisi türü belirtmek için

1. Hizmet yapılandırma dosyasında aşağıdaki XML iletisi ve sertifika için istemci kimlik bilgisi türü güvenlik modu ayarlamak için kullanın.

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

2. Bir istemci için yapılandırma dosyasında, sertifikası olan bir kullanıcının deposunda bulunamadı ve SubjectName alanın değeri "CohoWinery." için arama yaparak bulunabilir belirtmek için aşağıdaki XML kullanın.

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

WCF'de sertifikaları kullanma hakkında daha fazla bilgi için bkz. [Working with Certificates](working-with-certificates.md).

## <a name="net-framework-security"></a>.NET Framework güvenliği

Geçici kök yetkilisi sertifikalarını sildiğinizden emin olun **güvenilen kök sertifika yetkilileri** ve **kişisel** sertifikayı sağ tıklatıp sonra tıklatarak klasörleri  **Silme**.

## <a name="see-also"></a>Ayrıca bkz.

- [Sertifikalarla Çalışma](working-with-certificates.md)
- [Nasıl yapılır: MMC ek bileşeni ile sertifikaları görüntüleme](how-to-view-certificates-with-the-mmc-snap-in.md)
- [Hizmet ve İstemcileri Güvenli Hale Getirme](securing-services-and-clients.md)
