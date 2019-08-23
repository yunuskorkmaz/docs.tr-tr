---
title: <authentication><serviceCertificate> öğesinin
ms.date: 03/30/2017
ms.assetid: 733b67b4-08a1-4d25-9741-10046f9357ef
ms.openlocfilehash: d770ba1f9a0a18c927b3a4bf6d4141286e3a380c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919990"
---
# <a name="authentication-of-servicecertificate-element"></a><span data-ttu-id="8a6e1-102">\<\<ServiceCertificate > öğesinin kimlik doğrulama ></span><span class="sxs-lookup"><span data-stu-id="8a6e1-102">\<authentication> of \<serviceCertificate> Element</span></span>
<span data-ttu-id="8a6e1-103">SSL/TLS anlaşması kullanılarak elde edilen hizmet sertifikalarının kimlik doğrulaması için istemci proxy tarafından kullanılan ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="8a6e1-103">Specifies the settings used by the client proxy to authenticate service certificates that are obtained using SSL/TLS negotiation.</span></span>  
  
 <span data-ttu-id="8a6e1-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="8a6e1-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="8a6e1-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="8a6e1-105">\<behaviors></span></span>  
<span data-ttu-id="8a6e1-106">Endpointdavranışlar bölümü</span><span class="sxs-lookup"><span data-stu-id="8a6e1-106">endpointBehaviors section</span></span>  
<span data-ttu-id="8a6e1-107">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="8a6e1-107">\<behavior></span></span>  
<span data-ttu-id="8a6e1-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="8a6e1-108">\<clientCredentials></span></span>  
<span data-ttu-id="8a6e1-109">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="8a6e1-109">\<serviceCertificate></span></span>  
<span data-ttu-id="8a6e1-110">\<kimlik doğrulama ></span><span class="sxs-lookup"><span data-stu-id="8a6e1-110">\<authentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a6e1-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8a6e1-111">Syntax</span></span>  
  
```xml  
<authentication customCertificateValidatorType="String"
                certificateValidationMode="None/PeerTrust/ChainTrust/PeerOrChainTrust/Custom"
                revocationMode="NoCheck/Online/Offline"
                trustedStoreLocation="LocalMachine/CurrentUser" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8a6e1-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8a6e1-112">Attributes and Elements</span></span>  
 <span data-ttu-id="8a6e1-113">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="8a6e1-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8a6e1-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8a6e1-114">Attributes</span></span>  
  
|<span data-ttu-id="8a6e1-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="8a6e1-115">Attribute</span></span>|<span data-ttu-id="8a6e1-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8a6e1-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8a6e1-117">customCertificateValidatorType</span><span class="sxs-lookup"><span data-stu-id="8a6e1-117">customCertificateValidatorType</span></span>|<span data-ttu-id="8a6e1-118">Dizisinde.</span><span class="sxs-lookup"><span data-stu-id="8a6e1-118">String.</span></span> <span data-ttu-id="8a6e1-119">Özel bir türü doğrulamak için kullanılan tür ve derleme.</span><span class="sxs-lookup"><span data-stu-id="8a6e1-119">A type and assembly used to validate a custom type.</span></span>|  
|<span data-ttu-id="8a6e1-120">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="8a6e1-120">certificateValidationMode</span></span>|<span data-ttu-id="8a6e1-121">Kimlik bilgilerini doğrulamak için kullanılan üç moddan birini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8a6e1-121">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="8a6e1-122">Olarak `Custom`ayarlanırsa, bir customcercertificate atevalidator da sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8a6e1-122">If set to `Custom`, then a customCertificateValidator must also be supplied.</span></span> <span data-ttu-id="8a6e1-123">Varsayılan, `ChainTrust` değeridir.</span><span class="sxs-lookup"><span data-stu-id="8a6e1-123">The default is `ChainTrust`.</span></span>|  
|<span data-ttu-id="8a6e1-124">Revocationmodu</span><span class="sxs-lookup"><span data-stu-id="8a6e1-124">revocationMode</span></span>|<span data-ttu-id="8a6e1-125">İptal edilen bir sertifika listesini (CRL) denetlemek için kullanılan modlardan biri.</span><span class="sxs-lookup"><span data-stu-id="8a6e1-125">One of the modes used to check for a revoked certificate lists (CRL).</span></span> <span data-ttu-id="8a6e1-126">Varsayılan, `Online` değeridir.</span><span class="sxs-lookup"><span data-stu-id="8a6e1-126">The default is `Online`.</span></span>|  
|<span data-ttu-id="8a6e1-127">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="8a6e1-127">trustedStoreLocation</span></span>|<span data-ttu-id="8a6e1-128">İki sistem depolama konumlarından biri: `LocalMachine` veya. `CurrentUser`</span><span class="sxs-lookup"><span data-stu-id="8a6e1-128">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="8a6e1-129">Bu değer, bir hizmet sertifikası istemciye anlaşılırken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8a6e1-129">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="8a6e1-130">Doğrulama, belirtilen depo konumundaki **güvenilir kişiler** deposuna göre gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="8a6e1-130">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="8a6e1-131">Varsayılan, `CurrentUser` değeridir.</span><span class="sxs-lookup"><span data-stu-id="8a6e1-131">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidator-attribute"></a><span data-ttu-id="8a6e1-132">Customcercertificate Atevalidator özniteliği</span><span class="sxs-lookup"><span data-stu-id="8a6e1-132">customCertificateValidator Attribute</span></span>  
  
|<span data-ttu-id="8a6e1-133">Değer</span><span class="sxs-lookup"><span data-stu-id="8a6e1-133">Value</span></span>|<span data-ttu-id="8a6e1-134">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8a6e1-134">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8a6e1-135">Dize</span><span class="sxs-lookup"><span data-stu-id="8a6e1-135">String</span></span>|<span data-ttu-id="8a6e1-136">Türü bulmak için kullanılan tür adını ve derlemeyi ve diğer verileri belirtir.</span><span class="sxs-lookup"><span data-stu-id="8a6e1-136">Specifies the type name and assembly and other data used to find the type.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="8a6e1-137">certificateValidationMode özniteliği</span><span class="sxs-lookup"><span data-stu-id="8a6e1-137">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="8a6e1-138">Değer</span><span class="sxs-lookup"><span data-stu-id="8a6e1-138">Value</span></span>|<span data-ttu-id="8a6e1-139">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8a6e1-139">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8a6e1-140">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="8a6e1-140">Enumeration</span></span>|<span data-ttu-id="8a6e1-141">Aşağıdaki değerlerden biri: None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.</span><span class="sxs-lookup"><span data-stu-id="8a6e1-141">One of the following values: None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.</span></span><br /><br /> <span data-ttu-id="8a6e1-142">Daha fazla bilgi için bkz. [sertifikalarla çalışma](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="8a6e1-142">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="8a6e1-143">revocationMode özniteliği</span><span class="sxs-lookup"><span data-stu-id="8a6e1-143">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="8a6e1-144">Değer</span><span class="sxs-lookup"><span data-stu-id="8a6e1-144">Value</span></span>|<span data-ttu-id="8a6e1-145">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8a6e1-145">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8a6e1-146">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="8a6e1-146">Enumeration</span></span>|<span data-ttu-id="8a6e1-147">Aşağıdaki değerlerden biri: NoCheck, çevrimiçi, çevrimdışı.</span><span class="sxs-lookup"><span data-stu-id="8a6e1-147">One of the following values: NoCheck, Online, Offline.</span></span><br /><br /> <span data-ttu-id="8a6e1-148">Daha fazla bilgi için bkz. [sertifikalarla çalışma](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="8a6e1-148">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="8a6e1-149">trustedStoreLocation özniteliği</span><span class="sxs-lookup"><span data-stu-id="8a6e1-149">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="8a6e1-150">Değer</span><span class="sxs-lookup"><span data-stu-id="8a6e1-150">Value</span></span>|<span data-ttu-id="8a6e1-151">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8a6e1-151">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8a6e1-152">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="8a6e1-152">Enumeration</span></span>|<span data-ttu-id="8a6e1-153">Aşağıdaki değerlerden biri: LocalMachine veya CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="8a6e1-153">One of the following values: LocalMachine or CurrentUser.</span></span> <span data-ttu-id="8a6e1-154">Varsayılan değer CurrentUser ' dır.</span><span class="sxs-lookup"><span data-stu-id="8a6e1-154">The default is CurrentUser.</span></span> <span data-ttu-id="8a6e1-155">İstemci uygulaması bir sistem hesabı altında çalışıyorsa, sertifika genellikle LocalMachine altında olur.</span><span class="sxs-lookup"><span data-stu-id="8a6e1-155">If the client application is running under a system account, then the certificate is typically under LocalMachine.</span></span> <span data-ttu-id="8a6e1-156">İstemci uygulaması bir kullanıcı hesabı altında çalışıyorsa, sertifika genellikle CurrentUser içinde olur.</span><span class="sxs-lookup"><span data-stu-id="8a6e1-156">If the client application is running under a user account, then the certificate is typically in CurrentUser.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8a6e1-157">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8a6e1-157">Child Elements</span></span>  
 <span data-ttu-id="8a6e1-158">Yok.</span><span class="sxs-lookup"><span data-stu-id="8a6e1-158">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8a6e1-159">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8a6e1-159">Parent Elements</span></span>  
  
|<span data-ttu-id="8a6e1-160">Öğe</span><span class="sxs-lookup"><span data-stu-id="8a6e1-160">Element</span></span>|<span data-ttu-id="8a6e1-161">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8a6e1-161">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8a6e1-162">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="8a6e1-162">\<serviceCertificate></span></span>](servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="8a6e1-163">İstemciye bir hizmetin kimlik doğrulaması yapılırken kullanılacak sertifikayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="8a6e1-163">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8a6e1-164">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8a6e1-164">Remarks</span></span>  
 <span data-ttu-id="8a6e1-165">Bu yapılandırma öğesinin özniteliği, sertifikaların kimliğini doğrulamak için kullanılan güven düzeyini belirtir. `certificateValidationMode`</span><span class="sxs-lookup"><span data-stu-id="8a6e1-165">The `certificateValidationMode` attribute of this configuration element specifies the level of trust used to authenticate certificates.</span></span> <span data-ttu-id="8a6e1-166">Varsayılan olarak, düzeyi olarak `ChainTrust`ayarlanır; Bu, her bir sertifikanın, zincirin en üstündeki güvenilen bir sertifika yetkilisi ile biten sertifikalar hiyerarşisinde bulunması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8a6e1-166">By default, the level is set to `ChainTrust`, which specifies that each certificate must be found in a hierarchy of certificates ending in a trusted certification authority at the top of the chain.</span></span> <span data-ttu-id="8a6e1-167">En güvenli mod budur.</span><span class="sxs-lookup"><span data-stu-id="8a6e1-167">This is the most secure mode.</span></span> <span data-ttu-id="8a6e1-168">Ayrıca, otomatik olarak verilen sertifikaların ( `PeerOrChainTrust`eş güven) kabul edildiğini ve güvenilen bir zincirdeki sertifikaların kabul edildiğini belirten değerini olarak da ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8a6e1-168">You can also set the value to `PeerOrChainTrust`, which specifies that self-issued certificates (peer trust) are accepted as well as certificates that are in a trusted chain.</span></span> <span data-ttu-id="8a6e1-169">Bu değer, istemci ve Hizmetleri geliştirirken ve hata ayıkladığında kullanılır çünkü kendinden verilen sertifikaların güvenilir bir yetkilinizden satın alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8a6e1-169">This value is used when developing and debugging clients and services because self-issued certificates need not be purchased from a trusted authority.</span></span> <span data-ttu-id="8a6e1-170">Bir istemciyi dağıttığınızda, bunun yerine `ChainTrust` değeri kullanın.</span><span class="sxs-lookup"><span data-stu-id="8a6e1-170">When deploying a client, use the `ChainTrust` value instead.</span></span> <span data-ttu-id="8a6e1-171">Ayrıca, değerini veya `Custom` `None`olarak ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8a6e1-171">You can also set the value to `Custom` or `None`.</span></span> <span data-ttu-id="8a6e1-172">`Custom` Değerini kullanmak için, bir derlemeyi ve sertifikayı doğrulamak için `customCertificateValidator` kullanılan türünü de özniteliğini ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8a6e1-172">To use the `Custom` value, you must also set the `customCertificateValidator` attribute to an assembly and type used to validate the certificate.</span></span> <span data-ttu-id="8a6e1-173">Kendi özel Doğrulayıcısı oluşturmak için soyut X509CertificateValidator sınıfından devralması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8a6e1-173">To create your own custom validator, you must inherit from the abstract X509CertificateValidator class.</span></span> <span data-ttu-id="8a6e1-174">Daha fazla bilgi için [nasıl yapılır: Özel bir sertifika Doğrulayıcı](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)kullanan bir hizmet oluşturun.</span><span class="sxs-lookup"><span data-stu-id="8a6e1-174">For more information, see [How to: Create a Service that Employs a Custom Certificate Validator](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span></span>  
  
 <span data-ttu-id="8a6e1-175">Özniteliği `revocationMode` , sertifikaların iptal için nasıl denetleneceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8a6e1-175">The `revocationMode` attribute specifies how certificates are checked for revocation.</span></span> <span data-ttu-id="8a6e1-176">Varsayılan `online` değer, sertifikaların iptal için otomatik olarak denetleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="8a6e1-176">The default is `online` which indicates that certificates will be checked automatically for revocation.</span></span> <span data-ttu-id="8a6e1-177">Daha fazla bilgi için bkz. [sertifikalarla çalışma](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="8a6e1-177">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8a6e1-178">Örnek</span><span class="sxs-lookup"><span data-stu-id="8a6e1-178">Example</span></span>  
 <span data-ttu-id="8a6e1-179">Aşağıdaki örnek iki görevi yapar.</span><span class="sxs-lookup"><span data-stu-id="8a6e1-179">The following example does two tasks.</span></span> <span data-ttu-id="8a6e1-180">İlk olarak, etki alanı adı `www.contoso.com` http protokolünün üzerinde olan uç noktalarla iletişim kurarken istemcinin kullanması için bir hizmet sertifikası belirtir.</span><span class="sxs-lookup"><span data-stu-id="8a6e1-180">It first specifies a service certificate for the client to use when communicating with endpoints whose domain name is `www.contoso.com` over the HTTP protocol.</span></span> <span data-ttu-id="8a6e1-181">İkincisi, kimlik doğrulama sırasında kullanılan iptal modunu ve depolama konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="8a6e1-181">Second, it specifies the revocation mode and store location used during authentication.</span></span>  
  
```xml  
<serviceCertificate>
  <defaultCertificate findValue="www.contoso.com"
                      storeLocation="LocalMachine"
                      storeName="TrustedPeople"
                      x509FindType="FindByIssuerDistinguishedName" />
  <scopedCertificates>
     <add targetUri="http://www.contoso.com"
          findValue="www.contoso.com"
          storeLocation="LocalMachine"
          storeName="Root"
          x509FindType="FindByIssuerName" />
  </scopedCertificates>
  <authentication revocationMode="Online"
                  trustedStoreLocation="LocalMachine" />
</serviceCertificate>
```  
  
## <a name="see-also"></a><span data-ttu-id="8a6e1-182">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8a6e1-182">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.Authentication%2A>
- <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication>
- [<span data-ttu-id="8a6e1-183">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="8a6e1-183">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="8a6e1-184">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="8a6e1-184">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="8a6e1-185">Nasıl yapılır: Özel bir sertifika Doğrulayıcı kullanan bir hizmet oluşturma</span><span class="sxs-lookup"><span data-stu-id="8a6e1-185">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)
- [<span data-ttu-id="8a6e1-186">\<kimlik doğrulama ></span><span class="sxs-lookup"><span data-stu-id="8a6e1-186">\<authentication></span></span>](authentication-of-clientcertificate-element.md)
- [<span data-ttu-id="8a6e1-187">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="8a6e1-187">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="8a6e1-188">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="8a6e1-188">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
