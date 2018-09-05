---
title: 'Nasıl yapılır: Geliştirme Sırasında Kullanmak için Geçici Sertifikalar Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], creating temporary certificates
- temporary certificates [WCF]
ms.assetid: bc5f6637-5513-4d27-99bb-51aad7741e4a
ms.openlocfilehash: d3b051c7ea152606721388ea35b6f508eada1c5d
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43524371"
---
# <a name="how-to-create-temporary-certificates-for-use-during-development"></a><span data-ttu-id="3d226-102">Nasıl yapılır: Geliştirme Sırasında Kullanmak için Geçici Sertifikalar Oluşturma</span><span class="sxs-lookup"><span data-stu-id="3d226-102">How to: Create Temporary Certificates for Use During Development</span></span>
<span data-ttu-id="3d226-103">Güvenli hizmet veya Windows Communication Foundation (WCF) kullanan istemci geliştirirken, genellikle bir kimlik bilgisi olarak kullanılacak bir X.509 sertifikası sağlamak gereklidir.</span><span class="sxs-lookup"><span data-stu-id="3d226-103">When developing a secure service or client using Windows Communication Foundation (WCF), it is often necessary to supply an X.509 certificate to be used as a credential.</span></span> <span data-ttu-id="3d226-104">Sertifika bilgisayar güvenilen kök sertifika yetkilileri deposunda bulunan kök yetkilisi sertifikalarıyla oluşan bir zincir, genellikle parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="3d226-104">The certificate typically is part of a chain of certificates with a root authority found in the Trusted Root Certification Authorities store of the computer.</span></span> <span data-ttu-id="3d226-105">Bir sertifika zinciri olan sertifika genellikle kök yetkilisi kuruluşunuz veya iş birimi olduğu kümesi kapsam olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="3d226-105">Having a certificate chain enables you to scope a set of certificates where typically the root authority is from your organization or business unit.</span></span> <span data-ttu-id="3d226-106">Bu geliştirme zamanında benzetmek için güvenlik gereksinimlerini karşılamak için iki sertifika oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3d226-106">To emulate this at development time, you can create two certificates to satisfy the security requirements.</span></span> <span data-ttu-id="3d226-107">İlk otomatik olarak imzalanan bir sertifika olduğundan güvenilen kök sertifika yetkilileri deposunda yerleştirilir ve ikinci sertifikayı ilk konumdan oluşturulur ve yerel makine konumun Kişisel depolama alanı kişisel mağazasında şirket içinde veya yerleştirilir. Geçerli kullanıcı konumu.</span><span class="sxs-lookup"><span data-stu-id="3d226-107">The first is a self-signed certificate that is placed in the Trusted Root Certification Authorities store, and the second certificate is created from the first and is placed in either the Personal store of the Local Machine location, or the Personal store of the Current User location.</span></span> <span data-ttu-id="3d226-108">Bu konuda kullanarak bu iki sertifikaları oluşturma adımlarında size kılavuzluk eder [sertifika oluşturma Aracı (MakeCert.exe)](https://go.microsoft.com/fwlink/?LinkId=248185), tarafından sağlanan [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] SDK.</span><span class="sxs-lookup"><span data-stu-id="3d226-108">This topic walks through the steps to create these two certificates using the [Certificate Creation Tool (MakeCert.exe)](https://go.microsoft.com/fwlink/?LinkId=248185), which is provided by the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] SDK.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3d226-109">Sertifika Oluşturma aracı oluşturur sertifikalar yalnızca sınama amacıyla sağlanır.</span><span class="sxs-lookup"><span data-stu-id="3d226-109">The certificates the Certification Creation tool generates are provided for testing purposes only.</span></span> <span data-ttu-id="3d226-110">Bir hizmet veya istemci dağıtımı sırasında bir sertifika yetkilisi tarafından sağlanan uygun bir sertifikayı kullanmak emin olun.</span><span class="sxs-lookup"><span data-stu-id="3d226-110">When deploying a service or client, be sure to use an appropriate certificate provided by a certification authority.</span></span> <span data-ttu-id="3d226-111">Bu da gelen olabilir bir [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] sertifika kuruluşunuzdaki sunucuya veya bir üçüncü taraf.</span><span class="sxs-lookup"><span data-stu-id="3d226-111">This could either be from a [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] certificate server in your organization or a third party.</span></span>  
>   
>  <span data-ttu-id="3d226-112">Varsayılan olarak, [Makecert.exe (sertifika oluşturma aracı)](https://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d) , kök yetkilisi adlı sertifikalar oluşturur "kök Ajans **."**</span><span class="sxs-lookup"><span data-stu-id="3d226-112">By default, the [Makecert.exe (Certificate Creation Tool)](https://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d) creates certificates whose root authority is called "Root Agency **."**</span></span> <span data-ttu-id="3d226-113">"Kök Ajans" güvenilen kök sertifika yetkilileri deposunda olmadığından bu bu sertifikaları güvenli hale getirir.</span><span class="sxs-lookup"><span data-stu-id="3d226-113">Because the "Root Agency" is not in the Trusted Root Certification Authorities store, this makes these certificates insecure.</span></span> <span data-ttu-id="3d226-114">Güvenilen kök sertifika yetkilileri yerleştirilir, otomatik olarak imzalanan bir sertifika oluşturmak store dağıtım ortamınızı daha yakından taklit eden bir geliştirme ortamı olarak oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="3d226-114">Creating a self-signed certificate that is placed in the Trusted Root Certification Authorities store enables you to create a development environment that more closely simulates your deployment environment.</span></span>  
  
 <span data-ttu-id="3d226-115">Oluşturma ve sertifikaları kullanma hakkında daha fazla bilgi için bkz. [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="3d226-115">For more information about creating and using certificates, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span> <span data-ttu-id="3d226-116">Bir kimlik bilgisi olarak bir sertifika kullanma hakkında daha fazla bilgi için bkz. [Hizmetleri güvenli hale getirme ve istemciler](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md).</span><span class="sxs-lookup"><span data-stu-id="3d226-116">For more information about using a certificate as a credential, see [Securing Services and Clients](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md).</span></span> <span data-ttu-id="3d226-117">Microsoft Authenticode teknolojisi kullanılarak hakkında bir öğretici için bkz [Authenticode genel bakış ve öğreticiler](https://go.microsoft.com/fwlink/?LinkId=88919).</span><span class="sxs-lookup"><span data-stu-id="3d226-117">For a tutorial about using Microsoft Authenticode technology, see [Authenticode Overviews and Tutorials](https://go.microsoft.com/fwlink/?LinkId=88919).</span></span>  
  
### <a name="to-create-a-self-signed-root-authority-certificate-and-export-the-private-key"></a><span data-ttu-id="3d226-118">Otomatik olarak imzalanan kök yetkilisi sertifikası oluşturma ve özel anahtarı dışarı aktar</span><span class="sxs-lookup"><span data-stu-id="3d226-118">To create a self-signed root authority certificate and export the private key</span></span>  
  
1.  <span data-ttu-id="3d226-119">MakeCert.exe aracı ile aşağıdaki anahtarlar kullanın:</span><span class="sxs-lookup"><span data-stu-id="3d226-119">Use the MakeCert.exe tool with the following switches:</span></span>  
  
    1.  <span data-ttu-id="3d226-120">`-n` `subjectName`.</span><span class="sxs-lookup"><span data-stu-id="3d226-120">`-n` `subjectName`.</span></span> <span data-ttu-id="3d226-121">Konu adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="3d226-121">Specifies the subject name.</span></span> <span data-ttu-id="3d226-122">Kuraldır konu adıyla önek olarak eklemek için "CN =" "Ortak adı" için.</span><span class="sxs-lookup"><span data-stu-id="3d226-122">The convention is to prefix the subject name with "CN = " for "Common Name".</span></span>  
  
    2.  <span data-ttu-id="3d226-123">`-r`.</span><span class="sxs-lookup"><span data-stu-id="3d226-123">`-r`.</span></span> <span data-ttu-id="3d226-124">Sertifika otomatik olarak imzalanan olacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="3d226-124">Specifies that the certificate will be self-signed.</span></span>  
  
    3.  <span data-ttu-id="3d226-125">`-sv` `privateKeyFile`.</span><span class="sxs-lookup"><span data-stu-id="3d226-125">`-sv` `privateKeyFile`.</span></span> <span data-ttu-id="3d226-126">Özel anahtar kapsayıcısı içeren dosyayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="3d226-126">Specifies the file that contains the private key container.</span></span>  
  
     <span data-ttu-id="3d226-127">Örneğin, aşağıdaki komut bir konu adı ile otomatik olarak imzalanan bir sertifika oluşturur. "CN = TempCA."</span><span class="sxs-lookup"><span data-stu-id="3d226-127">For example, the following command creates a self-signed certificate with a subject name of "CN=TempCA."</span></span>  
  
    ```  
    makecert -n "CN=TempCA" -r -sv TempCA.pvk TempCA.cer  
    ```  
  
     <span data-ttu-id="3d226-128">Özel anahtarını korumak için bir parola girmeniz istenir.</span><span class="sxs-lookup"><span data-stu-id="3d226-128">You will be prompted to provide a password to protect the private key.</span></span> <span data-ttu-id="3d226-129">Bu kök sertifika tarafından imzalanmış bir sertifika oluşturmak için bu parola gereklidir.</span><span class="sxs-lookup"><span data-stu-id="3d226-129">This password is required when creating a certificate signed by this root certificate.</span></span>  
  
### <a name="to-create-a-new-certificate-signed-by-a-root-authority-certificate"></a><span data-ttu-id="3d226-130">Kök yetkilisi sertifikası tarafından imzalanmış yeni bir sertifika oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="3d226-130">To create a new certificate signed by a root authority certificate</span></span>  
  
1.  <span data-ttu-id="3d226-131">MakeCert.exe aracı ile aşağıdaki anahtarlar kullanın:</span><span class="sxs-lookup"><span data-stu-id="3d226-131">Use the MakeCert.exe tool with the following switches:</span></span>  
  
    1.  <span data-ttu-id="3d226-132">`-sk` `subjectKey`.</span><span class="sxs-lookup"><span data-stu-id="3d226-132">`-sk` `subjectKey`.</span></span> <span data-ttu-id="3d226-133">Özel anahtarı tutan öznenin anahtar kapsayıcısı konumunu.</span><span class="sxs-lookup"><span data-stu-id="3d226-133">The location of the subject's key container that holds the private key.</span></span> <span data-ttu-id="3d226-134">Bir anahtar kapsayıcı mevcut değilse oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="3d226-134">If a key container does not exist, one is created.</span></span> <span data-ttu-id="3d226-135">-Sk veya - sv seçeneğinin kullanılması durumunda JoeSoft adlı bir anahtar kapsayıcı varsayılan olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="3d226-135">If neither of the -sk or -sv options is used, a key container called JoeSoft is created by default.</span></span>  
  
    2.  <span data-ttu-id="3d226-136">`-n` `subjectName`.</span><span class="sxs-lookup"><span data-stu-id="3d226-136">`-n` `subjectName`.</span></span> <span data-ttu-id="3d226-137">Konu adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="3d226-137">Specifies the subject name.</span></span> <span data-ttu-id="3d226-138">Kuraldır konu adıyla önek olarak eklemek için "CN =" "Ortak adı" için.</span><span class="sxs-lookup"><span data-stu-id="3d226-138">The convention is to prefix the subject name with "CN = " for "Common Name".</span></span>  
  
    3.  <span data-ttu-id="3d226-139">`-iv` `issuerKeyFile`.</span><span class="sxs-lookup"><span data-stu-id="3d226-139">`-iv` `issuerKeyFile`.</span></span> <span data-ttu-id="3d226-140">Verenin özel anahtar dosyasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="3d226-140">Specifies the issuer's private key file.</span></span>  
  
    4.  <span data-ttu-id="3d226-141">`-ic` `issuerCertFile`.</span><span class="sxs-lookup"><span data-stu-id="3d226-141">`-ic` `issuerCertFile`.</span></span> <span data-ttu-id="3d226-142">Verenin sertifika konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="3d226-142">Specifies the location of the issuer's certificate.</span></span>  
  
     <span data-ttu-id="3d226-143">Örneğin, aşağıdaki komutu tarafından imzalanmış bir sertifika oluşturur `TempCA` kök yetkilisi sertifikası konu adı ile `"CN=SignedByCA"` verenin özel anahtarı kullanarak.</span><span class="sxs-lookup"><span data-stu-id="3d226-143">For example, the following command creates a certificate signed by the `TempCA` root authority certificate with a subject name of `"CN=SignedByCA"` using the private key of the issuer.</span></span>  
  
    ```  
    makecert -sk SignedByCA -iv TempCA.pvk -n "CN=SignedByCA" -ic TempCA.cer SignedByCA.cer -sr currentuser -ss My  
    ```  
  
## <a name="installing-a-certificate-in-the-trusted-root-certification-authorities-store"></a><span data-ttu-id="3d226-144">Güvenilen kök sertifika yetkilileri Store sertifika yükleme</span><span class="sxs-lookup"><span data-stu-id="3d226-144">Installing a Certificate in the Trusted Root Certification Authorities Store</span></span>  
 <span data-ttu-id="3d226-145">Kendinden imzalı bir sertifika oluşturulduktan sonra güvenilen kök sertifika yetkilileri deposunda yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3d226-145">Once a self-signed certificate is created, you can install it in the Trusted Root Certification Authorities store.</span></span> <span data-ttu-id="3d226-146">İmzalanmış herhangi bir sertifika ile bu noktada sertifika, bilgisayar tarafından güvenilmiyor.</span><span class="sxs-lookup"><span data-stu-id="3d226-146">Any certificates that are signed with the certificate at this point are trusted by the computer.</span></span> <span data-ttu-id="3d226-147">Artık ihtiyacınız hemen sonra bu nedenle, sertifika deposundan silin.</span><span class="sxs-lookup"><span data-stu-id="3d226-147">For this reason, delete the certificate from the store as soon as you no longer need it.</span></span> <span data-ttu-id="3d226-148">İle imzalanmış tüm sertifikaları bu kök yetkilisi sertifikası sildiğinizde, yetkisiz haline gelir.</span><span class="sxs-lookup"><span data-stu-id="3d226-148">When you delete this root authority certificate, all other certificates that signed with it become unauthorized.</span></span> <span data-ttu-id="3d226-149">Kök yetkilisi sertifikaları yapabildiği sertifikaların bir grup gerektiğinde kapsamlandırılabilir olarak yalnızca bir mekanizması mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="3d226-149">Root authority certificates are simply a mechanism whereby a group of certificates can be scoped as necessary.</span></span> <span data-ttu-id="3d226-150">Örneğin, eşler arası uygulamalar, genellikle gerek yoktur kök yetkilisi için yalnızca bir bireyin kimliği tarafından sağlanan, sertifika güven için.</span><span class="sxs-lookup"><span data-stu-id="3d226-150">For example, in peer-to-peer applications, there is typically no need for a root authority because you simply trust the identity of an individual by its supplied certificate.</span></span>  
  
#### <a name="to-install-a-self-signed-certificate-in-the-trusted-root-certification-authorities"></a><span data-ttu-id="3d226-151">Güvenilen kök sertifika yetkilileri otomatik olarak imzalanan bir sertifika yüklemek için</span><span class="sxs-lookup"><span data-stu-id="3d226-151">To install a self-signed certificate in the Trusted Root Certification Authorities</span></span>  
  
1.  <span data-ttu-id="3d226-152">Sertifika ek bileşenini açın.</span><span class="sxs-lookup"><span data-stu-id="3d226-152">Open the certificate snap-in.</span></span> <span data-ttu-id="3d226-153">Daha fazla bilgi için [nasıl yapılır: MMC ek bileşeni ile sertifikaları görüntüleme](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="3d226-153">For more information, see [How to: View Certificates with the MMC Snap-in](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span></span>  
  
2.  <span data-ttu-id="3d226-154">Sertifika ya da depolamak için klasörü açın **yerel bilgisayar** veya **geçerli kullanıcının**.</span><span class="sxs-lookup"><span data-stu-id="3d226-154">Open the folder to store the certificate, either the **Local Computer** or the **Current User**.</span></span>  
  
3.  <span data-ttu-id="3d226-155">Açık **güvenilen kök sertifika yetkilileri** klasör.</span><span class="sxs-lookup"><span data-stu-id="3d226-155">Open the **Trusted Root Certification Authorities** folder.</span></span>  
  
4.  <span data-ttu-id="3d226-156">Sağ tıklayın **sertifikaları** klasörü ve tıklatın **tüm görevler**, ardından **alma**.</span><span class="sxs-lookup"><span data-stu-id="3d226-156">Right-click the **Certificates** folder and click **All Tasks**, then click **Import**.</span></span>  
  
5.  <span data-ttu-id="3d226-157">Ekrandaki Sihirbazı izleyin TempCa.cer depoya içeri aktarma yönergeleri.</span><span class="sxs-lookup"><span data-stu-id="3d226-157">Follow the on-screen wizard instructions to import the TempCa.cer into the store.</span></span>  
  
## <a name="using-certificates-with-wcf"></a><span data-ttu-id="3d226-158">WCF ile sertifikaları kullanma</span><span class="sxs-lookup"><span data-stu-id="3d226-158">Using Certificates With WCF</span></span>  
 <span data-ttu-id="3d226-159">Geçici sertifikalar ayarladıktan sonra sertifikaları bir istemci kimlik bilgisi türü belirtin WCF çözümleri geliştirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3d226-159">Once you have set up the temporary certificates, you can use them to develop WCF solutions that specify certificates as a client credential type.</span></span> <span data-ttu-id="3d226-160">Örneğin, aşağıdaki XML yapılandırması ileti güvenliği ve bir sertifika istemci kimlik bilgileri türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="3d226-160">For example, the following XML configuration specifies message security and a certificate as the client credential type.</span></span>  
  
#### <a name="to-specify-a-certificate-as-the-client-credential-type"></a><span data-ttu-id="3d226-161">Sertifika istemci kimlik bilgisi türü belirtmek için</span><span class="sxs-lookup"><span data-stu-id="3d226-161">To specify a certificate as the client credential type</span></span>  
  
-   <span data-ttu-id="3d226-162">Hizmet yapılandırma dosyasında aşağıdaki XML iletisi ve sertifika için istemci kimlik bilgisi türü güvenlik modu ayarlamak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="3d226-162">In the configuration file for a service, use the following XML to set the security mode to message, and the client credential type to certificate.</span></span>  
  
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
  
 <span data-ttu-id="3d226-163">Bir istemci için yapılandırma dosyasında, sertifikası olan bir kullanıcının deposunda bulunamadı ve SubjectName alanın değeri "CohoWinery." için arama yaparak bulunabilir belirtmek için aşağıdaki XML kullanın.</span><span class="sxs-lookup"><span data-stu-id="3d226-163">In the configuration file for a client, use the following XML to specify that the certificate is found in the user’s store, and can be found by searching the SubjectName field for the value "CohoWinery."</span></span>  
  
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
  
 <span data-ttu-id="3d226-164">WCF'de sertifikaları kullanma hakkında daha fazla bilgi için bkz. [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="3d226-164">For more information about using certificates in WCF, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="3d226-165">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="3d226-165">.NET Framework Security</span></span>  
 <span data-ttu-id="3d226-166">Geçici kök yetkilisi sertifikalarını sildiğinizden emin olun **güvenilen kök sertifika yetkilileri** ve **kişisel** sertifikayı sağ tıklatıp sonra tıklatarak klasörleri  **Silme**.</span><span class="sxs-lookup"><span data-stu-id="3d226-166">Be sure to delete any temporary root authority certificates from the **Trusted Root Certification Authorities** and **Personal** folders by right-clicking the certificate, then clicking **Delete**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d226-167">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3d226-167">See Also</span></span>  
 [<span data-ttu-id="3d226-168">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="3d226-168">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="3d226-169">Nasıl yapılır: MMC Ek Bileşeni ile Sertifikaları Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="3d226-169">How to: View Certificates with the MMC Snap-in</span></span>](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)  
 [<span data-ttu-id="3d226-170">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="3d226-170">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
