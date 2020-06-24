---
title: 'Nasıl yapılır: Geliştirme Sırasında Kullanmak için Geçici Sertifikalar Oluşturma'
description: Bir PowerShell cmdlet 'ini kullanarak güvenli bir WCF hizmeti veya istemcisi geliştirmekte kullanılmak üzere iki geçici X. 509.952 sertifikası oluşturma hakkında bilgi edinin.
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], creating temporary certificates
- temporary certificates [WCF]
ms.assetid: bc5f6637-5513-4d27-99bb-51aad7741e4a
ms.openlocfilehash: 0a21548386639a9f6a8c8572e5d7928ffdb270d6
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247045"
---
# <a name="how-to-create-temporary-certificates-for-use-during-development"></a>Nasıl yapılır: Geliştirme Sırasında Kullanmak için Geçici Sertifikalar Oluşturma

Windows Communication Foundation (WCF) kullanarak güvenli bir hizmet veya istemci geliştirirken, genellikle kimlik bilgisi olarak kullanılacak bir X. 509.440 sertifikası sağlamak gereklidir. Sertifika genellikle bilgisayarın güvenilen kök sertifika yetkilileri deposunda bulunan bir kök yetkiliyle bir Sertifika zincirinin parçasıdır. Bir sertifika zinciri olması, genellikle kök yetkilisinin kuruluşunuzun veya iş biriminden olduğu bir sertifika kümesini kapsamlamanıza olanak sağlar. Geliştirme zamanında buna öykünmek için, güvenlik gereksinimlerini karşılamak üzere iki sertifika oluşturabilirsiniz. Birincisi, güvenilen kök sertifika yetkilileri deposuna yerleştirilmiş otomatik olarak imzalanan bir sertifikadır ve ikinci sertifika birinciden oluşturulur ve yerel makine konumunun kişisel deposuna ya da geçerli kullanıcı konumunun kişisel deposuna yerleştirilir. Bu konu, PowerShell [New-SelfSignedCertificate)](/powershell/module/pkiclient/new-selfsignedcertificate) cmdlet 'ini kullanarak bu iki sertifikayı oluşturma adımlarında size kılavuzluk eder.

> [!IMPORTANT]
> New-SelfSignedCertificate cmdlet 'inin oluşturduğu sertifikalar yalnızca sınama amacıyla sağlanır. Bir hizmet veya istemci dağıtıldığında, bir sertifika yetkilisi tarafından sunulan uygun bir sertifikayı kullandığınızdan emin olun. Bu, kuruluşunuzdaki bir Windows Server sertifika sunucusundan veya üçüncü bir tarafa ait olabilir.
>
> Varsayılan olarak, [New-SelfSignedCertificate](/powershell/module/pkiclient/new-selfsignedcertificate) cmdlet 'i, kendinden imzalı sertifikalar oluşturur ve bu sertifikalar güvenli değildir. Otomatik olarak imzalanan sertifikaların güvenilen kök sertifika yetkilileri deposuna yerleştirilmesi, dağıtım ortamınızı daha yakından taklit eden bir geliştirme ortamı oluşturmanızı sağlar.

 Sertifika oluşturma ve kullanma hakkında daha fazla bilgi için bkz. [sertifikalarla çalışma](working-with-certificates.md). Kimlik bilgisi olarak sertifika kullanma hakkında daha fazla bilgi için bkz. [Hizmetleri ve Istemcileri güvenli hale getirme](securing-services-and-clients.md). Microsoft Authenticode teknolojisini kullanma hakkında bir öğretici için bkz. [Authenticode genel bakış ve öğreticiler](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms537360(v=vs.85)).

## <a name="to-create-a-self-signed-root-authority-certificate-and-export-the-private-key"></a>Otomatik olarak imzalanan bir kök yetkili sertifikası oluşturmak ve özel anahtarı dışarı aktarmak için

Aşağıdaki komut, geçerli kullanıcı Kişisel deposunda "RootCA" konu adına sahip kendinden imzalı bir sertifika oluşturur.

```powershell
$rootcert = New-SelfSignedCertificate -CertStoreLocation Cert:\CurrentUser\My -DnsName "RootCA" -TextExtension @("2.5.29.19={text}CA=true") -KeyUsage CertSign,CrlSign,DigitalSignature
```

Sertifikayı bir PFX dosyasına aktardığımızda, daha sonraki bir adımda gereken yere aktarılabilmesi gerekir. Özel anahtarla bir sertifika dışarı aktarılırken, bunu korumak için bir parola gerekir. Parolayı bir `SecureString` öğesine kaydeder ve sertifikayı ilişkili özel anahtarla BIR PFX dosyasına aktarmak Için [Export-pfxcertificate](/powershell/module/pkiclient/export-pfxcertificate) cmdlet 'ini kullanın. Ayrıca, [Export-Certificate](/powershell/module/pkiclient/export-certificate) cmdlet 'ini kullanarak yalnızca genel sertifikayı CRT dosyasına kaydettik.

```powershell
[System.Security.SecureString]$rootcertPassword = ConvertTo-SecureString -String "password" -Force -AsPlainText
[String]$rootCertPath = Join-Path -Path 'cert:\CurrentUser\My\' -ChildPath "$($rootcert.Thumbprint)"
Export-PfxCertificate -Cert $rootCertPath -FilePath 'RootCA.pfx' -Password $rootcertPassword
Export-Certificate -Cert $rootCertPath -FilePath 'RootCA.crt'
```

## <a name="to-create-a-new-certificate-signed-by-a-root-authority-certificate"></a>Kök yetkilisi sertifikası tarafından imzalanmış yeni bir sertifika oluşturmak için

Aşağıdaki komut, `RootCA` veren 'in özel anahtarını kullanarak "SignedByRootCA" konu adı ile imzalanmış bir sertifika oluşturur.

```powershell
$testCert = New-SelfSignedCertificate -CertStoreLocation Cert:\LocalMachine\My -DnsName "SignedByRootCA" -KeyExportPolicy Exportable -KeyLength 2048 -KeyUsage DigitalSignature,KeyEncipherment -Signer $rootCert
```

Benzer şekilde, imzalı sertifikayı özel anahtarla bir PFX dosyasına ve yalnızca ortak anahtara bir CRT dosyasına kaydedebiliyoruz.

```powershell
[String]$testCertPath = Join-Path -Path 'cert:\LocalMachine\My\' -ChildPath "$($testCert.Thumbprint)"
Export-PfxCertificate -Cert $testCertPath -FilePath testcert.pfx -Password $rootcertPassword
Export-Certificate -Cert $testCertPath -FilePath testcert.crt
```

## <a name="installing-a-certificate-in-the-trusted-root-certification-authorities-store"></a>Güvenilen kök sertifika yetkilileri deposuna sertifika yükleme

Otomatik olarak imzalanan bir sertifika oluşturulduktan sonra, güvenilen kök sertifika yetkilileri deposuna yükleyebilirsiniz. Bu noktada sertifikayla imzalanan tüm sertifikalara bilgisayar tarafından güvenililir. Bu nedenle, sertifikayı artık ihtiyaç duyulmaz depolamadan silin. Bu kök yetkili sertifikasını sildiğinizde, onunla imzalanan tüm diğer sertifikalar yetkilendirilmemiş hale gelir. Kök yetkili sertifikaları, bir sertifika grubunun gerekli olarak kapsam oluşturabildiği bir mekanizmadır. Örneğin, eşler arası uygulamalarda, genellikle bir kök yetkili gereksinimi yoktur, çünkü yalnızca bir bireyin kimliğini sağlanan sertifikayla güvende olursunuz.

### <a name="to-install-a-self-signed-certificate-in-the-trusted-root-certification-authorities"></a>Güvenilen kök sertifika yetkililerine otomatik olarak imzalanan sertifika yüklemek için

1. Sertifika ek bileşenini açın. Daha fazla bilgi için bkz. [nasıl yapılır: MMC ek bileşeni Ile sertifikaları görüntüleme](how-to-view-certificates-with-the-mmc-snap-in.md).

2. Sertifikayı **Yerel bilgisayar** veya **Geçerli Kullanıcı**olarak depolamak için klasörü açın.

3. **Güvenilen kök sertifika yetkilileri** klasörünü açın.

4. **Sertifikalar** klasörüne sağ tıklayın ve **Tüm görevler**' e ve ardından **içeri aktar**' a tıklayın.

5. RootCA. pfx 'i depoya aktarmak için ekrandaki sihirbaz yönergelerini izleyin.

## <a name="using-certificates-with-wcf"></a>WCF Ile sertifika kullanma

Geçici sertifikaları ayarladıktan sonra, sertifikaları istemci kimlik bilgisi türü olarak belirten WCF çözümleri geliştirmek için kullanabilirsiniz. Örneğin, aşağıdaki XML yapılandırması ileti güvenliğini ve istemci kimlik bilgisi türü olarak bir sertifikayı belirtir.

### <a name="to-specify-a-certificate-as-the-client-credential-type"></a>İstemci kimlik bilgisi türü olarak bir sertifika belirtmek için

1. Bir hizmetin yapılandırma dosyasında, güvenlik modunu ileti olarak ve istemci kimlik bilgisi türünü sertifikaya ayarlamak için aşağıdaki XML 'i kullanın.

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

2. Bir istemcinin yapılandırma dosyasında, sertifikanın kullanıcının deposunda bulunduğunu belirtmek için aşağıdaki XML 'i kullanın ve "Cohowınaraı" değeri için SubjectName alanında arama yaparak bulunabilir.

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

WCF 'de sertifika kullanma hakkında daha fazla bilgi için bkz. [sertifikalarla çalışma](working-with-certificates.md).

## <a name="net-framework-security"></a>.NET Framework güvenliği

Sertifikaya sağ tıklayıp **Sil**' e tıklayarak, **Güvenilen kök sertifika yetkililerinden** ve **Kişisel** klasörlerden herhangi bir geçici kök yetkilisi sertifikasını sildiğinizden emin olun.

## <a name="see-also"></a>Ayrıca bkz.

- [Sertifikalarla Çalışma](working-with-certificates.md)
- [Nasıl yapılır: MMC Ek Bileşeni ile Sertifikaları Görüntüleme](how-to-view-certificates-with-the-mmc-snap-in.md)
- [Hizmet ve İstemcileri Güvenli Hale Getirme](securing-services-and-clients.md)
