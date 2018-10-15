---
title: '&lt;serviceCertificate&gt; Öğesi &lt;kimlik doğrulama&gt;'
ms.date: 03/30/2017
ms.assetid: 733b67b4-08a1-4d25-9741-10046f9357ef
ms.openlocfilehash: 811d54b49d8cd4fddbf196dbb524c5d303805c4f
ms.sourcegitcommit: d88024e6d6d8b242feae5f4007a709379355aa24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2018
ms.locfileid: "49316460"
---
# <a name="ltauthenticationgt-of-ltservicecertificategt-element"></a><span data-ttu-id="4a679-102">&lt;serviceCertificate&gt; Öğesi &lt;kimlik doğrulama&gt;</span><span class="sxs-lookup"><span data-stu-id="4a679-102">&lt;authentication&gt; of &lt;serviceCertificate&gt; Element</span></span>
<span data-ttu-id="4a679-103">SSL/TLS anlaşması kullanılarak elde edilen hizmet sertifikalarının kimlik doğrulaması için istemci proxy tarafından kullanılan ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="4a679-103">Specifies the settings used by the client proxy to authenticate service certificates that are obtained using SSL/TLS negotiation.</span></span>  
  
 <span data-ttu-id="4a679-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="4a679-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="4a679-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="4a679-105">\<behaviors></span></span>  
<span data-ttu-id="4a679-106">endpointBehaviors bölümü</span><span class="sxs-lookup"><span data-stu-id="4a679-106">endpointBehaviors section</span></span>  
<span data-ttu-id="4a679-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="4a679-107">\<behavior></span></span>  
<span data-ttu-id="4a679-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="4a679-108">\<clientCredentials></span></span>  
<span data-ttu-id="4a679-109">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="4a679-109">\<serviceCertificate></span></span>  
<span data-ttu-id="4a679-110">\<kimlik doğrulama ></span><span class="sxs-lookup"><span data-stu-id="4a679-110">\<authentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a679-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4a679-111">Syntax</span></span>  
  
```xml  
<authentication customCertificateValidatorType="String" certificateValidationMode="None/PeerTrust/ChainTrust/PeerOrChainTrust/Custom"  
revocationMode="NoCheck/Online/Offline"   
trustedStoreLocation="LocalMachine/CurrentUser" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4a679-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4a679-112">Attributes and Elements</span></span>  
 <span data-ttu-id="4a679-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4a679-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4a679-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4a679-114">Attributes</span></span>  
  
|<span data-ttu-id="4a679-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4a679-115">Attribute</span></span>|<span data-ttu-id="4a679-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4a679-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4a679-117">customCertificateValidatorType</span><span class="sxs-lookup"><span data-stu-id="4a679-117">customCertificateValidatorType</span></span>|<span data-ttu-id="4a679-118">dize.</span><span class="sxs-lookup"><span data-stu-id="4a679-118">String.</span></span> <span data-ttu-id="4a679-119">Tür ve özel bir tür doğrulamak için kullanılan bir derleme.</span><span class="sxs-lookup"><span data-stu-id="4a679-119">A type and assembly used to validate a custom type.</span></span>|  
|<span data-ttu-id="4a679-120">Certificatevalidationmode'u</span><span class="sxs-lookup"><span data-stu-id="4a679-120">certificateValidationMode</span></span>|<span data-ttu-id="4a679-121">Kimlik bilgilerini doğrulamak için kullanılan üç moddan birini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4a679-121">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="4a679-122">Varsa kümesine `Custom`, sonra da bir customCertificateValidator de sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4a679-122">If set to `Custom`, then a customCertificateValidator must also be supplied.</span></span> <span data-ttu-id="4a679-123">Varsayılan, `ChainTrust` değeridir.</span><span class="sxs-lookup"><span data-stu-id="4a679-123">The default is `ChainTrust`.</span></span>|  
|<span data-ttu-id="4a679-124">revocationMode</span><span class="sxs-lookup"><span data-stu-id="4a679-124">revocationMode</span></span>|<span data-ttu-id="4a679-125">İptal edilen sertifikalar listelerini (CRL) denetlemek için kullanılan modlardan biri.</span><span class="sxs-lookup"><span data-stu-id="4a679-125">One of the modes used to check for a revoked certificate lists (CRL).</span></span> <span data-ttu-id="4a679-126">Varsayılan, `Online` değeridir.</span><span class="sxs-lookup"><span data-stu-id="4a679-126">The default is `Online`.</span></span>|  
|<span data-ttu-id="4a679-127">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="4a679-127">trustedStoreLocation</span></span>|<span data-ttu-id="4a679-128">İki sistem depolama konumlarından biri: `LocalMachine` veya `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="4a679-128">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="4a679-129">Bir hizmet sertifikası istemciye anlaşıldığında, bu değer kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4a679-129">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="4a679-130">Doğrulama işlemi gerçekleştirildiğinde karşı **güvenilir kişiler** depolamak belirtilen depolama konumu.</span><span class="sxs-lookup"><span data-stu-id="4a679-130">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="4a679-131">Varsayılan, `CurrentUser` değeridir.</span><span class="sxs-lookup"><span data-stu-id="4a679-131">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidator-attribute"></a><span data-ttu-id="4a679-132">customCertificateValidator özniteliği</span><span class="sxs-lookup"><span data-stu-id="4a679-132">customCertificateValidator Attribute</span></span>  
  
|<span data-ttu-id="4a679-133">Değer</span><span class="sxs-lookup"><span data-stu-id="4a679-133">Value</span></span>|<span data-ttu-id="4a679-134">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4a679-134">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4a679-135">Dize</span><span class="sxs-lookup"><span data-stu-id="4a679-135">String</span></span>|<span data-ttu-id="4a679-136">Tür adı ve derleme ve diğer veri türünü bulmak için kullanılan belirtir.</span><span class="sxs-lookup"><span data-stu-id="4a679-136">Specifies the type name and assembly and other data used to find the type.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="4a679-137">Certificatevalidationmode'u özniteliği</span><span class="sxs-lookup"><span data-stu-id="4a679-137">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="4a679-138">Değer</span><span class="sxs-lookup"><span data-stu-id="4a679-138">Value</span></span>|<span data-ttu-id="4a679-139">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4a679-139">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4a679-140">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="4a679-140">Enumeration</span></span>|<span data-ttu-id="4a679-141">Aşağıdaki değerlerden biri: hiçbiri, PeerTrust, ChainTrust, PeerOrChainTrust, özel.</span><span class="sxs-lookup"><span data-stu-id="4a679-141">One of the following values: None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.</span></span><br /><br /> <span data-ttu-id="4a679-142">Daha fazla bilgi için [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="4a679-142">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="4a679-143">revocationMode özniteliği</span><span class="sxs-lookup"><span data-stu-id="4a679-143">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="4a679-144">Değer</span><span class="sxs-lookup"><span data-stu-id="4a679-144">Value</span></span>|<span data-ttu-id="4a679-145">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4a679-145">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4a679-146">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="4a679-146">Enumeration</span></span>|<span data-ttu-id="4a679-147">Aşağıdaki değerlerden biri: NoCheck, çevrimiçi, çevrimdışı.</span><span class="sxs-lookup"><span data-stu-id="4a679-147">One of the following values: NoCheck, Online, Offline.</span></span><br /><br /> <span data-ttu-id="4a679-148">Daha fazla bilgi için [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="4a679-148">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="4a679-149">trustedStoreLocation özniteliği</span><span class="sxs-lookup"><span data-stu-id="4a679-149">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="4a679-150">Değer</span><span class="sxs-lookup"><span data-stu-id="4a679-150">Value</span></span>|<span data-ttu-id="4a679-151">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4a679-151">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4a679-152">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="4a679-152">Enumeration</span></span>|<span data-ttu-id="4a679-153">Aşağıdaki değerlerden biri: LocalMachine ya da CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="4a679-153">One of the following values: LocalMachine or CurrentUser.</span></span> <span data-ttu-id="4a679-154">CurrentUser varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="4a679-154">The default is CurrentUser.</span></span> <span data-ttu-id="4a679-155">İstemci uygulama bir sistem hesabı altında çalışıyorsa, sertifika genellikle altında LocalMachine dizisidir.</span><span class="sxs-lookup"><span data-stu-id="4a679-155">If the client application is running under a system account, then the certificate is typically under LocalMachine.</span></span> <span data-ttu-id="4a679-156">İstemci uygulama bir kullanıcı hesabı altında çalışıyorsa, sertifika genellikle içinde CurrentUser dizisidir.</span><span class="sxs-lookup"><span data-stu-id="4a679-156">If the client application is running under a user account, then the certificate is typically in CurrentUser.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4a679-157">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4a679-157">Child Elements</span></span>  
 <span data-ttu-id="4a679-158">Yok.</span><span class="sxs-lookup"><span data-stu-id="4a679-158">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4a679-159">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4a679-159">Parent Elements</span></span>  
  
|<span data-ttu-id="4a679-160">Öğe</span><span class="sxs-lookup"><span data-stu-id="4a679-160">Element</span></span>|<span data-ttu-id="4a679-161">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4a679-161">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4a679-162">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="4a679-162">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="4a679-163">İstemci bir hizmete kimlik doğrulaması yapılırken kullanılacak sertifikayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="4a679-163">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4a679-164">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4a679-164">Remarks</span></span>  
 <span data-ttu-id="4a679-165">`certificateValidationMode` Bu yapılandırma öğesinin özniteliği sertifikaların kimliğini doğrulamak için kullanılan güven düzeyini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4a679-165">The `certificateValidationMode` attribute of this configuration element specifies the level of trust used to authenticate certificates.</span></span> <span data-ttu-id="4a679-166">Varsayılan olarak, düzeyi `ChainTrust`, her bir sertifikanın sertifika zinciri üst kısmındaki bir güvenilen sertifika yetkilisi ile biten bir hiyerarşideki bulunması gereken belirtir.</span><span class="sxs-lookup"><span data-stu-id="4a679-166">By default, the level is set to `ChainTrust`, which specifies that each certificate must be found in a hierarchy of certificates ending in a trusted certification authority at the top of the chain.</span></span> <span data-ttu-id="4a679-167">En güvenli mod budur.</span><span class="sxs-lookup"><span data-stu-id="4a679-167">This is the most secure mode.</span></span> <span data-ttu-id="4a679-168">De değer ayarlayabilirsiniz `PeerOrChainTrust`, kendi kendine verilen sertifikaların (eş güven) güvenilen bir zinciri olan sertifikaları yanı sıra kabul edildiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4a679-168">You can also set the value to `PeerOrChainTrust`, which specifies that self-issued certificates (peer trust) are accepted as well as certificates that are in a trusted chain.</span></span> <span data-ttu-id="4a679-169">Bu değer, geliştirme ve istemciler ve hizmetler kendi kendine verilen sertifikaların güvenilir yetkilisinden satın alınması değil çünkü hata ayıklama kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4a679-169">This value is used when developing and debugging clients and services because self-issued certificates need not be purchased from a trusted authority.</span></span> <span data-ttu-id="4a679-170">Bir istemci dağıtırken kullanırsınız `ChainTrust` yerine değeri.</span><span class="sxs-lookup"><span data-stu-id="4a679-170">When deploying a client, use the `ChainTrust` value instead.</span></span> <span data-ttu-id="4a679-171">De değer ayarlayabilirsiniz `Custom` veya `None`.</span><span class="sxs-lookup"><span data-stu-id="4a679-171">You can also set the value to `Custom` or `None`.</span></span> <span data-ttu-id="4a679-172">Kullanılacak `Custom` değeri ayarlamanız gerekir `customCertificateValidator` öznitelik bir bütünleştirilmiş kod ve sertifikayı doğrulamak için kullanılan tür.</span><span class="sxs-lookup"><span data-stu-id="4a679-172">To use the `Custom` value, you must also set the `customCertificateValidator` attribute to an assembly and type used to validate the certificate.</span></span> <span data-ttu-id="4a679-173">Kendi özel Doğrulayıcı sağlayıcısı oluşturmak için soyut X509CertificateValidator sınıftan devralmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4a679-173">To create your own custom validator, you must inherit from the abstract X509CertificateValidator class.</span></span> <span data-ttu-id="4a679-174">Daha fazla bilgi için [nasıl yapılır: özel bir sertifika Doğrulayıcı kullanan bir hizmet oluşturma](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span><span class="sxs-lookup"><span data-stu-id="4a679-174">For more information, see [How to: Create a Service that Employs a Custom Certificate Validator](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span></span>  
  
 <span data-ttu-id="4a679-175">`revocationMode` Özniteliği belirtir nasıl sertifika iptali için denetlenir.</span><span class="sxs-lookup"><span data-stu-id="4a679-175">The `revocationMode` attribute specifies how certificates are checked for revocation.</span></span> <span data-ttu-id="4a679-176">Varsayılan değer `online` gösteren sertifika iptali için otomatik olarak denetlenir.</span><span class="sxs-lookup"><span data-stu-id="4a679-176">The default is `online` which indicates that certificates will be checked automatically for revocation.</span></span> <span data-ttu-id="4a679-177">Daha fazla bilgi için [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="4a679-177">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4a679-178">Örnek</span><span class="sxs-lookup"><span data-stu-id="4a679-178">Example</span></span>  
 <span data-ttu-id="4a679-179">Aşağıdaki örnek, iki görevleri gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="4a679-179">The following example does two tasks.</span></span> <span data-ttu-id="4a679-180">Bir hizmet uç noktaları ile iletişim kurulurken etki alanı adını kullanmak istemci sertifikası ilk belirtir `www.contoso.com` HTTP protokolü üzerinden.</span><span class="sxs-lookup"><span data-stu-id="4a679-180">It first specifies a service certificate for the client to use when communicating with endpoints whose domain name is `www.contoso.com` over the HTTP protocol.</span></span> <span data-ttu-id="4a679-181">İkinci olarak, kimlik doğrulaması sırasında kullanılan iptal modu ve depolama konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="4a679-181">Second, it specifies the revocation mode and store location used during authentication.</span></span>  
  
```xml  
<serviceCertificate>  
  <defaultCertificate findValue="www.contoso.com"   
                      storeLocation="LocalMachine"  
                      storeName="TrustedPeople"   
                      x509FindType="FindByIssuerDistinguishedName" />  
  <scopedCertificates>  
     <add targetUri="http://www.contoso.com"   
          findValue="www.contoso.com" storeLocation="LocalMachine"  
                  storeName="Root" x509FindType="FindByIssuerName" />  
  </scopedCertificates>  
  <authentication revocationMode="Online"   
   trustedStoreLocation="LocalMachine" />  
</serviceCertificate>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4a679-182">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4a679-182">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.Authentication%2A>  
 <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication>  
 [<span data-ttu-id="4a679-183">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="4a679-183">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="4a679-184">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="4a679-184">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="4a679-185">Nasıl yapılır: Özel Bir Sertifika Doğrulayıcı Kullanan Bir Hizmet Oluşturma</span><span class="sxs-lookup"><span data-stu-id="4a679-185">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)  
 [<span data-ttu-id="4a679-186">\<kimlik doğrulama ></span><span class="sxs-lookup"><span data-stu-id="4a679-186">\<authentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md)  
 [<span data-ttu-id="4a679-187">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="4a679-187">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="4a679-188">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="4a679-188">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
