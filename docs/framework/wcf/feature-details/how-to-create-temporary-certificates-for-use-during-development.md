---
title: 'Nasıl yapılır: Geliştirme Sırasında Kullanmak için Geçici Sertifikalar Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], creating temporary certificates
- temporary certificates [WCF]
ms.assetid: bc5f6637-5513-4d27-99bb-51aad7741e4a
ms.openlocfilehash: d45f18b0b8fe4e0cc9667091e166c80691faa2d4
ms.sourcegitcommit: a3db1a9eafca89f95ccf361bc1833b47fbb2bb30
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/04/2019
ms.locfileid: "58921331"
---
# <a name="how-to-create-temporary-certificates-for-use-during-development"></a><span data-ttu-id="51e96-102">Nasıl yapılır: Geliştirme Sırasında Kullanmak için Geçici Sertifikalar Oluşturma</span><span class="sxs-lookup"><span data-stu-id="51e96-102">How to: Create Temporary Certificates for Use During Development</span></span>

<span data-ttu-id="51e96-103">Güvenli hizmet veya Windows Communication Foundation (WCF) kullanan istemci geliştirirken, genellikle bir kimlik bilgisi olarak kullanılacak bir X.509 sertifikası sağlamak gereklidir.</span><span class="sxs-lookup"><span data-stu-id="51e96-103">When developing a secure service or client using Windows Communication Foundation (WCF), it is often necessary to supply an X.509 certificate to be used as a credential.</span></span> <span data-ttu-id="51e96-104">Sertifika bilgisayar güvenilen kök sertifika yetkilileri deposunda bulunan kök yetkilisi sertifikalarıyla oluşan bir zincir, genellikle parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="51e96-104">The certificate typically is part of a chain of certificates with a root authority found in the Trusted Root Certification Authorities store of the computer.</span></span> <span data-ttu-id="51e96-105">Bir sertifika zinciri olan sertifika genellikle kök yetkilisi kuruluşunuz veya iş birimi olduğu kümesi kapsam olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="51e96-105">Having a certificate chain enables you to scope a set of certificates where typically the root authority is from your organization or business unit.</span></span> <span data-ttu-id="51e96-106">Bu geliştirme zamanında benzetmek için güvenlik gereksinimlerini karşılamak için iki sertifika oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="51e96-106">To emulate this at development time, you can create two certificates to satisfy the security requirements.</span></span> <span data-ttu-id="51e96-107">İlk otomatik olarak imzalanan bir sertifika olduğundan güvenilen kök sertifika yetkilileri deposunda yerleştirilir ve ikinci sertifikayı ilk konumdan oluşturulur ve yerel makine konumun Kişisel depolama alanı kişisel mağazasında şirket içinde veya yerleştirilir. Geçerli kullanıcı konumu.</span><span class="sxs-lookup"><span data-stu-id="51e96-107">The first is a self-signed certificate that is placed in the Trusted Root Certification Authorities store, and the second certificate is created from the first and is placed in either the Personal store of the Local Machine location, or the Personal store of the Current User location.</span></span> <span data-ttu-id="51e96-108">Bu konuda, Powershell kullanarak bu iki sertifikaları oluşturma adımlarında size kılavuzluk eder [New-SelfSignedCertificate)](/powershell/module/pkiclient/new-selfsignedcertificate) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="51e96-108">This topic walks through the steps to create these two certificates using the Powershell [New-SelfSignedCertificate)](/powershell/module/pkiclient/new-selfsignedcertificate) cmdlet.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="51e96-109">New-SelfSignedCertificate cmdlet oluşturur sertifikalar yalnızca sınama amacıyla sağlanır.</span><span class="sxs-lookup"><span data-stu-id="51e96-109">The certificates that the New-SelfSignedCertificate cmdlet generates are provided for testing purposes only.</span></span> <span data-ttu-id="51e96-110">Bir hizmet veya istemci dağıtımı sırasında bir sertifika yetkilisi tarafından sağlanan uygun bir sertifikayı kullanmak emin olun.</span><span class="sxs-lookup"><span data-stu-id="51e96-110">When deploying a service or client, be sure to use an appropriate certificate provided by a certification authority.</span></span> <span data-ttu-id="51e96-111">Bu, kuruluşunuzdaki Windows Server sertifika sunucusu arasında ya da üçüncü bir tarafa.</span><span class="sxs-lookup"><span data-stu-id="51e96-111">This could either be from a Windows Server certificate server in your organization or a third party.</span></span>
>
> <span data-ttu-id="51e96-112">Varsayılan olarak, [New-SelfSignedCertificate](/powershell/module/pkiclient/new-selfsignedcertificate) cmdlet'i otomatik olarak imzalanan sertifikalar oluşturur ve bu sertifikaları güvenli değil.</span><span class="sxs-lookup"><span data-stu-id="51e96-112">By default, the [New-SelfSignedCertificate](/powershell/module/pkiclient/new-selfsignedcertificate) cmdlet creates certificates that are self-signed and these certificates are insecure.</span></span> <span data-ttu-id="51e96-113">Otomatik olarak imzalanan sertifikaları Güvenilen kök sertifika yetkilileri yerleştirme store dağıtım ortamınızı daha yakından taklit eden bir geliştirme ortamı olarak oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="51e96-113">Placing the self-signed certificates in the Trusted Root Certification Authorities store enables you to create a development environment that more closely simulates your deployment environment.</span></span>

 <span data-ttu-id="51e96-114">Oluşturma ve sertifikaları kullanma hakkında daha fazla bilgi için bkz. [Working with Certificates](working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="51e96-114">For more information about creating and using certificates, see [Working with Certificates](working-with-certificates.md).</span></span> <span data-ttu-id="51e96-115">Bir kimlik bilgisi olarak bir sertifika kullanma hakkında daha fazla bilgi için bkz. [Hizmetleri güvenli hale getirme ve istemciler](securing-services-and-clients.md).</span><span class="sxs-lookup"><span data-stu-id="51e96-115">For more information about using a certificate as a credential, see [Securing Services and Clients](securing-services-and-clients.md).</span></span> <span data-ttu-id="51e96-116">Microsoft Authenticode teknolojisi kullanılarak hakkında bir öğretici için bkz [Authenticode genel bakış ve öğreticiler](https://go.microsoft.com/fwlink/?LinkId=88919).</span><span class="sxs-lookup"><span data-stu-id="51e96-116">For a tutorial about using Microsoft Authenticode technology, see [Authenticode Overviews and Tutorials](https://go.microsoft.com/fwlink/?LinkId=88919).</span></span>

## <a name="to-create-a-self-signed-root-authority-certificate-and-export-the-private-key"></a><span data-ttu-id="51e96-117">Otomatik olarak imzalanan kök yetkilisi sertifikası oluşturma ve özel anahtarı dışarı aktar</span><span class="sxs-lookup"><span data-stu-id="51e96-117">To create a self-signed root authority certificate and export the private key</span></span>

<span data-ttu-id="51e96-118">Aşağıdaki komut, "RootCA" geçerli kullanıcının kişisel depoda bir konu adıyla otomatik olarak imzalanan bir sertifika oluşturur.</span><span class="sxs-lookup"><span data-stu-id="51e96-118">The following command creates a self-signed certificate with a subject name of "RootCA" in the Current User Personal store.</span></span>

```powershell
PS $rootCert = New-SelfSignedCertificate -CertStoreLocation cert:\CurrentUser\My -DnsName "RootCA" -TextExtension @("1.3.6.1.4.1.311.21.10={text}1.3.6.1.5.5.7.3.1,1.3.6.1.5.5.7.3.2")
```

<span data-ttu-id="51e96-119">Böylece daha sonraki bir adımda gerekli yerlerde için aktarılabilen sertifikayı bir PFX dosyasına aktarmak ihtiyacımız var.</span><span class="sxs-lookup"><span data-stu-id="51e96-119">We need to export the certificate to a PFX file so that it can be imported to where it's needed in a later step.</span></span> <span data-ttu-id="51e96-120">Özel anahtara sahip bir sertifika verilirken korunması için bir parola gereklidir.</span><span class="sxs-lookup"><span data-stu-id="51e96-120">When exporting a certificate with the private key, a password is needed to protect it.</span></span> <span data-ttu-id="51e96-121">Biz Parolayı Kaydet bir `SecureString` ve [dışarı aktarma-PfxCertificate](/powershell/module/pkiclient/export-pfxcertificate) sertifikayı bir PFX dosyasına ilişkili özel anahtarla dışarı aktarmak için cmdlet'ini.</span><span class="sxs-lookup"><span data-stu-id="51e96-121">We save the password in a `SecureString` and use the [Export-PfxCertificate](/powershell/module/pkiclient/export-pfxcertificate) cmdlet to export the certificate with the associated private key to a PFX file.</span></span> <span data-ttu-id="51e96-122">Biz CRT kullanarak dosyanın içine de yalnızca ortak sertifikayı kaydetmek [sertifika verme](/powershell/module/pkiclient/export-certificate) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="51e96-122">We also save just the public certificate into a CRT file using the [Export-Certificate](/powershell/module/pkiclient/export-certificate) cmdlet.</span></span>

```powershell
PS [System.Security.SecureString]$rootcertPassword = ConvertTo-SecureString -String "password" -Force -AsPlainText
PS [String]$rootCertPath = Join-Path -Path 'cert:\CurrentUser\My\' -ChildPath "$($rootcert.Thumbprint)"
PS Export-PfxCertificate -Cert $rootCertPath -FilePath 'RootCA.pfx' -Password $rootcertPassword
PS Export-Certificate -Cert $rootCertPath -FilePath 'RootCA.crt'
```

## <a name="to-create-a-new-certificate-signed-by-a-root-authority-certificate"></a><span data-ttu-id="51e96-123">Kök yetkilisi sertifikası tarafından imzalanmış yeni bir sertifika oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="51e96-123">To create a new certificate signed by a root authority certificate</span></span>

<span data-ttu-id="51e96-124">Aşağıdaki komut tarafından imzalanmış bir sertifika oluşturur `RootCA` "SignedByRootCA verenin özel anahtarı kullanarak", bir konu adına sahip.</span><span class="sxs-lookup"><span data-stu-id="51e96-124">The following command creates a certificate signed by the `RootCA` with a subject name of "SignedByRootCA" using the private key of the issuer.</span></span>

```powershell
PS $testCert = New-SelfSignedCertificate -CertStoreLocation Cert:\LocalMachine\My -DnsName "SignedByRootCA" -KeyExportPolicy Exportable -KeyLength 2048 -KeyUsage DigitalSignature,KeyEncipherment -Signer $rootCert
```

<span data-ttu-id="51e96-125">Benzer şekilde, biz imzalı sertifikanın özel anahtara sahip bir PFX dosyası ve ortak anahtarı yalnızca bir CRT dosyasına kaydedin.</span><span class="sxs-lookup"><span data-stu-id="51e96-125">Similarly, we save the signed certificate with private key into a PFX file and just the public key into a CRT file.</span></span>

```powershell
PS [String]$testCertPath = Join-Path -Path 'cert:\LocalMachine\My\' -ChildPath "$($testCert.Thumbprint)"
PS Export-PfxCertificate -Cert $testCertPath -FilePath testcert.pfx -Password $rootcertPassword
PS Export-Certificate -Cert $testCertPath -FilePath testcert.crt
```

## <a name="installing-a-certificate-in-the-trusted-root-certification-authorities-store"></a><span data-ttu-id="51e96-126">Güvenilen kök sertifika yetkilileri Store sertifika yükleme</span><span class="sxs-lookup"><span data-stu-id="51e96-126">Installing a Certificate in the Trusted Root Certification Authorities Store</span></span>

<span data-ttu-id="51e96-127">Kendinden imzalı bir sertifika oluşturulduktan sonra güvenilen kök sertifika yetkilileri deposunda yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="51e96-127">Once a self-signed certificate is created, you can install it in the Trusted Root Certification Authorities store.</span></span> <span data-ttu-id="51e96-128">İmzalanmış herhangi bir sertifika ile bu noktada sertifika, bilgisayar tarafından güvenilmiyor.</span><span class="sxs-lookup"><span data-stu-id="51e96-128">Any certificates that are signed with the certificate at this point are trusted by the computer.</span></span> <span data-ttu-id="51e96-129">Artık ihtiyacınız hemen sonra bu nedenle, sertifika deposundan silin.</span><span class="sxs-lookup"><span data-stu-id="51e96-129">For this reason, delete the certificate from the store as soon as you no longer need it.</span></span> <span data-ttu-id="51e96-130">İle imzalanmış tüm sertifikaları bu kök yetkilisi sertifikası sildiğinizde, yetkisiz haline gelir.</span><span class="sxs-lookup"><span data-stu-id="51e96-130">When you delete this root authority certificate, all other certificates that signed with it become unauthorized.</span></span> <span data-ttu-id="51e96-131">Kök yetkilisi sertifikaları yapabildiği sertifikaların bir grup gerektiğinde kapsamlandırılabilir olarak yalnızca bir mekanizması mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="51e96-131">Root authority certificates are simply a mechanism whereby a group of certificates can be scoped as necessary.</span></span> <span data-ttu-id="51e96-132">Örneğin, eşler arası uygulamalar, genellikle gerek yoktur kök yetkilisi için yalnızca bir bireyin kimliği tarafından sağlanan, sertifika güven için.</span><span class="sxs-lookup"><span data-stu-id="51e96-132">For example, in peer-to-peer applications, there is typically no need for a root authority because you simply trust the identity of an individual by its supplied certificate.</span></span>

### <a name="to-install-a-self-signed-certificate-in-the-trusted-root-certification-authorities"></a><span data-ttu-id="51e96-133">Güvenilen kök sertifika yetkilileri otomatik olarak imzalanan bir sertifika yüklemek için</span><span class="sxs-lookup"><span data-stu-id="51e96-133">To install a self-signed certificate in the Trusted Root Certification Authorities</span></span>

1. <span data-ttu-id="51e96-134">Sertifika ek bileşenini açın.</span><span class="sxs-lookup"><span data-stu-id="51e96-134">Open the certificate snap-in.</span></span> <span data-ttu-id="51e96-135">Daha fazla bilgi için [nasıl yapılır: MMC ek bileşeni ile sertifikaları görüntüleme](how-to-view-certificates-with-the-mmc-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="51e96-135">For more information, see [How to: View Certificates with the MMC Snap-in](how-to-view-certificates-with-the-mmc-snap-in.md).</span></span>

2. <span data-ttu-id="51e96-136">Sertifika ya da depolamak için klasörü açın **yerel bilgisayar** veya **geçerli kullanıcının**.</span><span class="sxs-lookup"><span data-stu-id="51e96-136">Open the folder to store the certificate, either the **Local Computer** or the **Current User**.</span></span>

3. <span data-ttu-id="51e96-137">Açık **güvenilen kök sertifika yetkilileri** klasör.</span><span class="sxs-lookup"><span data-stu-id="51e96-137">Open the **Trusted Root Certification Authorities** folder.</span></span>

4. <span data-ttu-id="51e96-138">Sağ tıklayın **sertifikaları** klasörü ve tıklatın **tüm görevler**, ardından **alma**.</span><span class="sxs-lookup"><span data-stu-id="51e96-138">Right-click the **Certificates** folder and click **All Tasks**, then click **Import**.</span></span>

5. <span data-ttu-id="51e96-139">Ekrandaki Sihirbazı izleyin RootCA.pfx depoya içeri aktarma yönergeleri.</span><span class="sxs-lookup"><span data-stu-id="51e96-139">Follow the on-screen wizard instructions to import the RootCA.pfx into the store.</span></span>

## <a name="using-certificates-with-wcf"></a><span data-ttu-id="51e96-140">WCF ile sertifika kullanma</span><span class="sxs-lookup"><span data-stu-id="51e96-140">Using certificates With WCF</span></span>

<span data-ttu-id="51e96-141">Geçici sertifikalar ayarladıktan sonra sertifikaları bir istemci kimlik bilgisi türü belirtin WCF çözümleri geliştirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="51e96-141">Once you have set up the temporary certificates, you can use them to develop WCF solutions that specify certificates as a client credential type.</span></span> <span data-ttu-id="51e96-142">Örneğin, aşağıdaki XML yapılandırması ileti güvenliği ve bir sertifika istemci kimlik bilgileri türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="51e96-142">For example, the following XML configuration specifies message security and a certificate as the client credential type.</span></span>

### <a name="to-specify-a-certificate-as-the-client-credential-type"></a><span data-ttu-id="51e96-143">Sertifika istemci kimlik bilgisi türü belirtmek için</span><span class="sxs-lookup"><span data-stu-id="51e96-143">To specify a certificate as the client credential type</span></span>

1. <span data-ttu-id="51e96-144">Hizmet yapılandırma dosyasında aşağıdaki XML iletisi ve sertifika için istemci kimlik bilgisi türü güvenlik modu ayarlamak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="51e96-144">In the configuration file for a service, use the following XML to set the security mode to message, and the client credential type to certificate.</span></span>

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

2. <span data-ttu-id="51e96-145">Bir istemci için yapılandırma dosyasında, sertifikası olan bir kullanıcının deposunda bulunamadı ve SubjectName alanın değeri "CohoWinery." için arama yaparak bulunabilir belirtmek için aşağıdaki XML kullanın.</span><span class="sxs-lookup"><span data-stu-id="51e96-145">In the configuration file for a client, use the following XML to specify that the certificate is found in the user’s store, and can be found by searching the SubjectName field for the value "CohoWinery."</span></span>

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

<span data-ttu-id="51e96-146">WCF'de sertifikaları kullanma hakkında daha fazla bilgi için bkz. [Working with Certificates](working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="51e96-146">For more information about using certificates in WCF, see [Working with Certificates](working-with-certificates.md).</span></span>

## <a name="net-framework-security"></a><span data-ttu-id="51e96-147">.NET Framework güvenliği</span><span class="sxs-lookup"><span data-stu-id="51e96-147">.NET Framework security</span></span>

<span data-ttu-id="51e96-148">Geçici kök yetkilisi sertifikalarını sildiğinizden emin olun **güvenilen kök sertifika yetkilileri** ve **kişisel** sertifikayı sağ tıklatıp sonra tıklatarak klasörleri  **Silme**.</span><span class="sxs-lookup"><span data-stu-id="51e96-148">Be sure to delete any temporary root authority certificates from the **Trusted Root Certification Authorities** and **Personal** folders by right-clicking the certificate, then clicking **Delete**.</span></span>

## <a name="see-also"></a><span data-ttu-id="51e96-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="51e96-149">See also</span></span>

- [<span data-ttu-id="51e96-150">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="51e96-150">Working with Certificates</span></span>](working-with-certificates.md)
- [<span data-ttu-id="51e96-151">Nasıl yapılır: MMC Ek Bileşeni ile Sertifikaları Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="51e96-151">How to: View Certificates with the MMC Snap-in</span></span>](how-to-view-certificates-with-the-mmc-snap-in.md)
- [<span data-ttu-id="51e96-152">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="51e96-152">Securing Services and Clients</span></span>](securing-services-and-clients.md)
