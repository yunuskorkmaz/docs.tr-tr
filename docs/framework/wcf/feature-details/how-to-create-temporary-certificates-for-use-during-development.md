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
# <a name="how-to-create-temporary-certificates-for-use-during-development"></a><span data-ttu-id="e4e01-103">Nasıl yapılır: Geliştirme Sırasında Kullanmak için Geçici Sertifikalar Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e4e01-103">How to: Create Temporary Certificates for Use During Development</span></span>

<span data-ttu-id="e4e01-104">Windows Communication Foundation (WCF) kullanarak güvenli bir hizmet veya istemci geliştirirken, genellikle kimlik bilgisi olarak kullanılacak bir X. 509.440 sertifikası sağlamak gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e4e01-104">When developing a secure service or client using Windows Communication Foundation (WCF), it is often necessary to supply an X.509 certificate to be used as a credential.</span></span> <span data-ttu-id="e4e01-105">Sertifika genellikle bilgisayarın güvenilen kök sertifika yetkilileri deposunda bulunan bir kök yetkiliyle bir Sertifika zincirinin parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="e4e01-105">The certificate typically is part of a chain of certificates with a root authority found in the Trusted Root Certification Authorities store of the computer.</span></span> <span data-ttu-id="e4e01-106">Bir sertifika zinciri olması, genellikle kök yetkilisinin kuruluşunuzun veya iş biriminden olduğu bir sertifika kümesini kapsamlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="e4e01-106">Having a certificate chain enables you to scope a set of certificates where typically the root authority is from your organization or business unit.</span></span> <span data-ttu-id="e4e01-107">Geliştirme zamanında buna öykünmek için, güvenlik gereksinimlerini karşılamak üzere iki sertifika oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e4e01-107">To emulate this at development time, you can create two certificates to satisfy the security requirements.</span></span> <span data-ttu-id="e4e01-108">Birincisi, güvenilen kök sertifika yetkilileri deposuna yerleştirilmiş otomatik olarak imzalanan bir sertifikadır ve ikinci sertifika birinciden oluşturulur ve yerel makine konumunun kişisel deposuna ya da geçerli kullanıcı konumunun kişisel deposuna yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="e4e01-108">The first is a self-signed certificate that is placed in the Trusted Root Certification Authorities store, and the second certificate is created from the first and is placed in either the Personal store of the Local Machine location, or the Personal store of the Current User location.</span></span> <span data-ttu-id="e4e01-109">Bu konu, PowerShell [New-SelfSignedCertificate)](/powershell/module/pkiclient/new-selfsignedcertificate) cmdlet 'ini kullanarak bu iki sertifikayı oluşturma adımlarında size kılavuzluk eder.</span><span class="sxs-lookup"><span data-stu-id="e4e01-109">This topic walks through the steps to create these two certificates using the Powershell [New-SelfSignedCertificate)](/powershell/module/pkiclient/new-selfsignedcertificate) cmdlet.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e4e01-110">New-SelfSignedCertificate cmdlet 'inin oluşturduğu sertifikalar yalnızca sınama amacıyla sağlanır.</span><span class="sxs-lookup"><span data-stu-id="e4e01-110">The certificates that the New-SelfSignedCertificate cmdlet generates are provided for testing purposes only.</span></span> <span data-ttu-id="e4e01-111">Bir hizmet veya istemci dağıtıldığında, bir sertifika yetkilisi tarafından sunulan uygun bir sertifikayı kullandığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="e4e01-111">When deploying a service or client, be sure to use an appropriate certificate provided by a certification authority.</span></span> <span data-ttu-id="e4e01-112">Bu, kuruluşunuzdaki bir Windows Server sertifika sunucusundan veya üçüncü bir tarafa ait olabilir.</span><span class="sxs-lookup"><span data-stu-id="e4e01-112">This could either be from a Windows Server certificate server in your organization or a third party.</span></span>
>
> <span data-ttu-id="e4e01-113">Varsayılan olarak, [New-SelfSignedCertificate](/powershell/module/pkiclient/new-selfsignedcertificate) cmdlet 'i, kendinden imzalı sertifikalar oluşturur ve bu sertifikalar güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="e4e01-113">By default, the [New-SelfSignedCertificate](/powershell/module/pkiclient/new-selfsignedcertificate) cmdlet creates certificates that are self-signed and these certificates are insecure.</span></span> <span data-ttu-id="e4e01-114">Otomatik olarak imzalanan sertifikaların güvenilen kök sertifika yetkilileri deposuna yerleştirilmesi, dağıtım ortamınızı daha yakından taklit eden bir geliştirme ortamı oluşturmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="e4e01-114">Placing the self-signed certificates in the Trusted Root Certification Authorities store enables you to create a development environment that more closely simulates your deployment environment.</span></span>

 <span data-ttu-id="e4e01-115">Sertifika oluşturma ve kullanma hakkında daha fazla bilgi için bkz. [sertifikalarla çalışma](working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="e4e01-115">For more information about creating and using certificates, see [Working with Certificates](working-with-certificates.md).</span></span> <span data-ttu-id="e4e01-116">Kimlik bilgisi olarak sertifika kullanma hakkında daha fazla bilgi için bkz. [Hizmetleri ve Istemcileri güvenli hale getirme](securing-services-and-clients.md).</span><span class="sxs-lookup"><span data-stu-id="e4e01-116">For more information about using a certificate as a credential, see [Securing Services and Clients](securing-services-and-clients.md).</span></span> <span data-ttu-id="e4e01-117">Microsoft Authenticode teknolojisini kullanma hakkında bir öğretici için bkz. [Authenticode genel bakış ve öğreticiler](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms537360(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="e4e01-117">For a tutorial about using Microsoft Authenticode technology, see [Authenticode Overviews and Tutorials](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms537360(v=vs.85)).</span></span>

## <a name="to-create-a-self-signed-root-authority-certificate-and-export-the-private-key"></a><span data-ttu-id="e4e01-118">Otomatik olarak imzalanan bir kök yetkili sertifikası oluşturmak ve özel anahtarı dışarı aktarmak için</span><span class="sxs-lookup"><span data-stu-id="e4e01-118">To create a self-signed root authority certificate and export the private key</span></span>

<span data-ttu-id="e4e01-119">Aşağıdaki komut, geçerli kullanıcı Kişisel deposunda "RootCA" konu adına sahip kendinden imzalı bir sertifika oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e4e01-119">The following command creates a self-signed certificate with a subject name of "RootCA" in the Current User Personal store.</span></span>

```powershell
$rootcert = New-SelfSignedCertificate -CertStoreLocation Cert:\CurrentUser\My -DnsName "RootCA" -TextExtension @("2.5.29.19={text}CA=true") -KeyUsage CertSign,CrlSign,DigitalSignature
```

<span data-ttu-id="e4e01-120">Sertifikayı bir PFX dosyasına aktardığımızda, daha sonraki bir adımda gereken yere aktarılabilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="e4e01-120">We need to export the certificate to a PFX file so that it can be imported to where it's needed in a later step.</span></span> <span data-ttu-id="e4e01-121">Özel anahtarla bir sertifika dışarı aktarılırken, bunu korumak için bir parola gerekir.</span><span class="sxs-lookup"><span data-stu-id="e4e01-121">When exporting a certificate with the private key, a password is needed to protect it.</span></span> <span data-ttu-id="e4e01-122">Parolayı bir `SecureString` öğesine kaydeder ve sertifikayı ilişkili özel anahtarla BIR PFX dosyasına aktarmak Için [Export-pfxcertificate](/powershell/module/pkiclient/export-pfxcertificate) cmdlet 'ini kullanın.</span><span class="sxs-lookup"><span data-stu-id="e4e01-122">We save the password in a `SecureString` and use the [Export-PfxCertificate](/powershell/module/pkiclient/export-pfxcertificate) cmdlet to export the certificate with the associated private key to a PFX file.</span></span> <span data-ttu-id="e4e01-123">Ayrıca, [Export-Certificate](/powershell/module/pkiclient/export-certificate) cmdlet 'ini kullanarak yalnızca genel sertifikayı CRT dosyasına kaydettik.</span><span class="sxs-lookup"><span data-stu-id="e4e01-123">We also save just the public certificate into a CRT file using the [Export-Certificate](/powershell/module/pkiclient/export-certificate) cmdlet.</span></span>

```powershell
[System.Security.SecureString]$rootcertPassword = ConvertTo-SecureString -String "password" -Force -AsPlainText
[String]$rootCertPath = Join-Path -Path 'cert:\CurrentUser\My\' -ChildPath "$($rootcert.Thumbprint)"
Export-PfxCertificate -Cert $rootCertPath -FilePath 'RootCA.pfx' -Password $rootcertPassword
Export-Certificate -Cert $rootCertPath -FilePath 'RootCA.crt'
```

## <a name="to-create-a-new-certificate-signed-by-a-root-authority-certificate"></a><span data-ttu-id="e4e01-124">Kök yetkilisi sertifikası tarafından imzalanmış yeni bir sertifika oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e4e01-124">To create a new certificate signed by a root authority certificate</span></span>

<span data-ttu-id="e4e01-125">Aşağıdaki komut, `RootCA` veren 'in özel anahtarını kullanarak "SignedByRootCA" konu adı ile imzalanmış bir sertifika oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e4e01-125">The following command creates a certificate signed by the `RootCA` with a subject name of "SignedByRootCA" using the private key of the issuer.</span></span>

```powershell
$testCert = New-SelfSignedCertificate -CertStoreLocation Cert:\LocalMachine\My -DnsName "SignedByRootCA" -KeyExportPolicy Exportable -KeyLength 2048 -KeyUsage DigitalSignature,KeyEncipherment -Signer $rootCert
```

<span data-ttu-id="e4e01-126">Benzer şekilde, imzalı sertifikayı özel anahtarla bir PFX dosyasına ve yalnızca ortak anahtara bir CRT dosyasına kaydedebiliyoruz.</span><span class="sxs-lookup"><span data-stu-id="e4e01-126">Similarly, we save the signed certificate with private key into a PFX file and just the public key into a CRT file.</span></span>

```powershell
[String]$testCertPath = Join-Path -Path 'cert:\LocalMachine\My\' -ChildPath "$($testCert.Thumbprint)"
Export-PfxCertificate -Cert $testCertPath -FilePath testcert.pfx -Password $rootcertPassword
Export-Certificate -Cert $testCertPath -FilePath testcert.crt
```

## <a name="installing-a-certificate-in-the-trusted-root-certification-authorities-store"></a><span data-ttu-id="e4e01-127">Güvenilen kök sertifika yetkilileri deposuna sertifika yükleme</span><span class="sxs-lookup"><span data-stu-id="e4e01-127">Installing a Certificate in the Trusted Root Certification Authorities Store</span></span>

<span data-ttu-id="e4e01-128">Otomatik olarak imzalanan bir sertifika oluşturulduktan sonra, güvenilen kök sertifika yetkilileri deposuna yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e4e01-128">Once a self-signed certificate is created, you can install it in the Trusted Root Certification Authorities store.</span></span> <span data-ttu-id="e4e01-129">Bu noktada sertifikayla imzalanan tüm sertifikalara bilgisayar tarafından güvenililir.</span><span class="sxs-lookup"><span data-stu-id="e4e01-129">Any certificates that are signed with the certificate at this point are trusted by the computer.</span></span> <span data-ttu-id="e4e01-130">Bu nedenle, sertifikayı artık ihtiyaç duyulmaz depolamadan silin.</span><span class="sxs-lookup"><span data-stu-id="e4e01-130">For this reason, delete the certificate from the store as soon as you no longer need it.</span></span> <span data-ttu-id="e4e01-131">Bu kök yetkili sertifikasını sildiğinizde, onunla imzalanan tüm diğer sertifikalar yetkilendirilmemiş hale gelir.</span><span class="sxs-lookup"><span data-stu-id="e4e01-131">When you delete this root authority certificate, all other certificates that signed with it become unauthorized.</span></span> <span data-ttu-id="e4e01-132">Kök yetkili sertifikaları, bir sertifika grubunun gerekli olarak kapsam oluşturabildiği bir mekanizmadır.</span><span class="sxs-lookup"><span data-stu-id="e4e01-132">Root authority certificates are simply a mechanism whereby a group of certificates can be scoped as necessary.</span></span> <span data-ttu-id="e4e01-133">Örneğin, eşler arası uygulamalarda, genellikle bir kök yetkili gereksinimi yoktur, çünkü yalnızca bir bireyin kimliğini sağlanan sertifikayla güvende olursunuz.</span><span class="sxs-lookup"><span data-stu-id="e4e01-133">For example, in peer-to-peer applications, there is typically no need for a root authority because you simply trust the identity of an individual by its supplied certificate.</span></span>

### <a name="to-install-a-self-signed-certificate-in-the-trusted-root-certification-authorities"></a><span data-ttu-id="e4e01-134">Güvenilen kök sertifika yetkililerine otomatik olarak imzalanan sertifika yüklemek için</span><span class="sxs-lookup"><span data-stu-id="e4e01-134">To install a self-signed certificate in the Trusted Root Certification Authorities</span></span>

1. <span data-ttu-id="e4e01-135">Sertifika ek bileşenini açın.</span><span class="sxs-lookup"><span data-stu-id="e4e01-135">Open the certificate snap-in.</span></span> <span data-ttu-id="e4e01-136">Daha fazla bilgi için bkz. [nasıl yapılır: MMC ek bileşeni Ile sertifikaları görüntüleme](how-to-view-certificates-with-the-mmc-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="e4e01-136">For more information, see [How to: View Certificates with the MMC Snap-in](how-to-view-certificates-with-the-mmc-snap-in.md).</span></span>

2. <span data-ttu-id="e4e01-137">Sertifikayı **Yerel bilgisayar** veya **Geçerli Kullanıcı**olarak depolamak için klasörü açın.</span><span class="sxs-lookup"><span data-stu-id="e4e01-137">Open the folder to store the certificate, either the **Local Computer** or the **Current User**.</span></span>

3. <span data-ttu-id="e4e01-138">**Güvenilen kök sertifika yetkilileri** klasörünü açın.</span><span class="sxs-lookup"><span data-stu-id="e4e01-138">Open the **Trusted Root Certification Authorities** folder.</span></span>

4. <span data-ttu-id="e4e01-139">**Sertifikalar** klasörüne sağ tıklayın ve **Tüm görevler**' e ve ardından **içeri aktar**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e4e01-139">Right-click the **Certificates** folder and click **All Tasks**, then click **Import**.</span></span>

5. <span data-ttu-id="e4e01-140">RootCA. pfx 'i depoya aktarmak için ekrandaki sihirbaz yönergelerini izleyin.</span><span class="sxs-lookup"><span data-stu-id="e4e01-140">Follow the on-screen wizard instructions to import the RootCA.pfx into the store.</span></span>

## <a name="using-certificates-with-wcf"></a><span data-ttu-id="e4e01-141">WCF Ile sertifika kullanma</span><span class="sxs-lookup"><span data-stu-id="e4e01-141">Using certificates With WCF</span></span>

<span data-ttu-id="e4e01-142">Geçici sertifikaları ayarladıktan sonra, sertifikaları istemci kimlik bilgisi türü olarak belirten WCF çözümleri geliştirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e4e01-142">Once you have set up the temporary certificates, you can use them to develop WCF solutions that specify certificates as a client credential type.</span></span> <span data-ttu-id="e4e01-143">Örneğin, aşağıdaki XML yapılandırması ileti güvenliğini ve istemci kimlik bilgisi türü olarak bir sertifikayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="e4e01-143">For example, the following XML configuration specifies message security and a certificate as the client credential type.</span></span>

### <a name="to-specify-a-certificate-as-the-client-credential-type"></a><span data-ttu-id="e4e01-144">İstemci kimlik bilgisi türü olarak bir sertifika belirtmek için</span><span class="sxs-lookup"><span data-stu-id="e4e01-144">To specify a certificate as the client credential type</span></span>

1. <span data-ttu-id="e4e01-145">Bir hizmetin yapılandırma dosyasında, güvenlik modunu ileti olarak ve istemci kimlik bilgisi türünü sertifikaya ayarlamak için aşağıdaki XML 'i kullanın.</span><span class="sxs-lookup"><span data-stu-id="e4e01-145">In the configuration file for a service, use the following XML to set the security mode to message, and the client credential type to certificate.</span></span>

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

2. <span data-ttu-id="e4e01-146">Bir istemcinin yapılandırma dosyasında, sertifikanın kullanıcının deposunda bulunduğunu belirtmek için aşağıdaki XML 'i kullanın ve "Cohowınaraı" değeri için SubjectName alanında arama yaparak bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="e4e01-146">In the configuration file for a client, use the following XML to specify that the certificate is found in the user’s store, and can be found by searching the SubjectName field for the value "CohoWinery."</span></span>

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

<span data-ttu-id="e4e01-147">WCF 'de sertifika kullanma hakkında daha fazla bilgi için bkz. [sertifikalarla çalışma](working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="e4e01-147">For more information about using certificates in WCF, see [Working with Certificates](working-with-certificates.md).</span></span>

## <a name="net-framework-security"></a><span data-ttu-id="e4e01-148">.NET Framework güvenliği</span><span class="sxs-lookup"><span data-stu-id="e4e01-148">.NET Framework security</span></span>

<span data-ttu-id="e4e01-149">Sertifikaya sağ tıklayıp **Sil**' e tıklayarak, **Güvenilen kök sertifika yetkililerinden** ve **Kişisel** klasörlerden herhangi bir geçici kök yetkilisi sertifikasını sildiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="e4e01-149">Be sure to delete any temporary root authority certificates from the **Trusted Root Certification Authorities** and **Personal** folders by right-clicking the certificate, then clicking **Delete**.</span></span>

## <a name="see-also"></a><span data-ttu-id="e4e01-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e4e01-150">See also</span></span>

- [<span data-ttu-id="e4e01-151">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="e4e01-151">Working with Certificates</span></span>](working-with-certificates.md)
- [<span data-ttu-id="e4e01-152">Nasıl yapılır: MMC Ek Bileşeni ile Sertifikaları Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="e4e01-152">How to: View Certificates with the MMC Snap-in</span></span>](how-to-view-certificates-with-the-mmc-snap-in.md)
- [<span data-ttu-id="e4e01-153">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="e4e01-153">Securing Services and Clients</span></span>](securing-services-and-clients.md)
