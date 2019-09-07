---
title: <authentication><serviceCertificate> öğesinin
ms.date: 03/30/2017
ms.assetid: 733b67b4-08a1-4d25-9741-10046f9357ef
ms.openlocfilehash: 29170f032469b4d55b50f57ca06ce403a5aeaf2c
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398220"
---
# <a name="authentication-of-servicecertificate-element"></a><span data-ttu-id="89544-102">\<\<ServiceCertificate > öğesinin kimlik doğrulama ></span><span class="sxs-lookup"><span data-stu-id="89544-102">\<authentication> of \<serviceCertificate> Element</span></span>
<span data-ttu-id="89544-103">SSL/TLS anlaşması kullanılarak elde edilen hizmet sertifikalarının kimlik doğrulaması için istemci proxy tarafından kullanılan ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="89544-103">Specifies the settings used by the client proxy to authenticate service certificates that are obtained using SSL/TLS negotiation.</span></span>  
  
<span data-ttu-id="89544-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="89544-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="89544-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="89544-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="89544-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışlar >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="89544-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="89544-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Endpointdavranışlar >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="89544-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="89544-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="89544-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="89544-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="89544-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="89544-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceCertificate >** ](servicecertificate-of-clientcredentials-element.md)</span><span class="sxs-lookup"><span data-stu-id="89544-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate-of-clientcredentials-element.md)</span></span>\
<span data-ttu-id="89544-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<kimlik doğrulama >**</span><span class="sxs-lookup"><span data-stu-id="89544-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<authentication>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89544-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="89544-112">Syntax</span></span>  
  
```xml  
<authentication customCertificateValidatorType="String"
                certificateValidationMode="None/PeerTrust/ChainTrust/PeerOrChainTrust/Custom"
                revocationMode="NoCheck/Online/Offline"
                trustedStoreLocation="LocalMachine/CurrentUser" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="89544-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="89544-113">Attributes and Elements</span></span>  
 <span data-ttu-id="89544-114">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="89544-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="89544-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="89544-115">Attributes</span></span>  
  
|<span data-ttu-id="89544-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="89544-116">Attribute</span></span>|<span data-ttu-id="89544-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="89544-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="89544-118">customCertificateValidatorType</span><span class="sxs-lookup"><span data-stu-id="89544-118">customCertificateValidatorType</span></span>|<span data-ttu-id="89544-119">Dizisinde.</span><span class="sxs-lookup"><span data-stu-id="89544-119">String.</span></span> <span data-ttu-id="89544-120">Özel bir türü doğrulamak için kullanılan tür ve derleme.</span><span class="sxs-lookup"><span data-stu-id="89544-120">A type and assembly used to validate a custom type.</span></span>|  
|<span data-ttu-id="89544-121">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="89544-121">certificateValidationMode</span></span>|<span data-ttu-id="89544-122">Kimlik bilgilerini doğrulamak için kullanılan üç moddan birini belirtir.</span><span class="sxs-lookup"><span data-stu-id="89544-122">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="89544-123">Olarak `Custom`ayarlanırsa, bir customcercertificate atevalidator da sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="89544-123">If set to `Custom`, then a customCertificateValidator must also be supplied.</span></span> <span data-ttu-id="89544-124">Varsayılan, `ChainTrust` değeridir.</span><span class="sxs-lookup"><span data-stu-id="89544-124">The default is `ChainTrust`.</span></span>|  
|<span data-ttu-id="89544-125">Revocationmodu</span><span class="sxs-lookup"><span data-stu-id="89544-125">revocationMode</span></span>|<span data-ttu-id="89544-126">İptal edilen bir sertifika listesini (CRL) denetlemek için kullanılan modlardan biri.</span><span class="sxs-lookup"><span data-stu-id="89544-126">One of the modes used to check for a revoked certificate lists (CRL).</span></span> <span data-ttu-id="89544-127">Varsayılan, `Online` değeridir.</span><span class="sxs-lookup"><span data-stu-id="89544-127">The default is `Online`.</span></span>|  
|<span data-ttu-id="89544-128">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="89544-128">trustedStoreLocation</span></span>|<span data-ttu-id="89544-129">İki sistem depolama konumlarından biri: `LocalMachine` veya. `CurrentUser`</span><span class="sxs-lookup"><span data-stu-id="89544-129">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="89544-130">Bu değer, bir hizmet sertifikası istemciye anlaşılırken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="89544-130">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="89544-131">Doğrulama, belirtilen depo konumundaki **güvenilir kişiler** deposuna göre gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="89544-131">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="89544-132">Varsayılan, `CurrentUser` değeridir.</span><span class="sxs-lookup"><span data-stu-id="89544-132">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidator-attribute"></a><span data-ttu-id="89544-133">Customcercertificate Atevalidator özniteliği</span><span class="sxs-lookup"><span data-stu-id="89544-133">customCertificateValidator Attribute</span></span>  
  
|<span data-ttu-id="89544-134">Değer</span><span class="sxs-lookup"><span data-stu-id="89544-134">Value</span></span>|<span data-ttu-id="89544-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="89544-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="89544-136">Dize</span><span class="sxs-lookup"><span data-stu-id="89544-136">String</span></span>|<span data-ttu-id="89544-137">Türü bulmak için kullanılan tür adını ve derlemeyi ve diğer verileri belirtir.</span><span class="sxs-lookup"><span data-stu-id="89544-137">Specifies the type name and assembly and other data used to find the type.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="89544-138">certificateValidationMode özniteliği</span><span class="sxs-lookup"><span data-stu-id="89544-138">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="89544-139">Değer</span><span class="sxs-lookup"><span data-stu-id="89544-139">Value</span></span>|<span data-ttu-id="89544-140">Açıklama</span><span class="sxs-lookup"><span data-stu-id="89544-140">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="89544-141">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="89544-141">Enumeration</span></span>|<span data-ttu-id="89544-142">Aşağıdaki değerlerden biri: None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.</span><span class="sxs-lookup"><span data-stu-id="89544-142">One of the following values: None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.</span></span><br /><br /> <span data-ttu-id="89544-143">Daha fazla bilgi için bkz. [sertifikalarla çalışma](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="89544-143">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="89544-144">revocationMode özniteliği</span><span class="sxs-lookup"><span data-stu-id="89544-144">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="89544-145">Değer</span><span class="sxs-lookup"><span data-stu-id="89544-145">Value</span></span>|<span data-ttu-id="89544-146">Açıklama</span><span class="sxs-lookup"><span data-stu-id="89544-146">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="89544-147">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="89544-147">Enumeration</span></span>|<span data-ttu-id="89544-148">Aşağıdaki değerlerden biri: NoCheck, çevrimiçi, çevrimdışı.</span><span class="sxs-lookup"><span data-stu-id="89544-148">One of the following values: NoCheck, Online, Offline.</span></span><br /><br /> <span data-ttu-id="89544-149">Daha fazla bilgi için bkz. [sertifikalarla çalışma](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="89544-149">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="89544-150">trustedStoreLocation özniteliği</span><span class="sxs-lookup"><span data-stu-id="89544-150">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="89544-151">Değer</span><span class="sxs-lookup"><span data-stu-id="89544-151">Value</span></span>|<span data-ttu-id="89544-152">Açıklama</span><span class="sxs-lookup"><span data-stu-id="89544-152">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="89544-153">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="89544-153">Enumeration</span></span>|<span data-ttu-id="89544-154">Aşağıdaki değerlerden biri: LocalMachine veya CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="89544-154">One of the following values: LocalMachine or CurrentUser.</span></span> <span data-ttu-id="89544-155">Varsayılan değer CurrentUser ' dır.</span><span class="sxs-lookup"><span data-stu-id="89544-155">The default is CurrentUser.</span></span> <span data-ttu-id="89544-156">İstemci uygulaması bir sistem hesabı altında çalışıyorsa, sertifika genellikle LocalMachine altında olur.</span><span class="sxs-lookup"><span data-stu-id="89544-156">If the client application is running under a system account, then the certificate is typically under LocalMachine.</span></span> <span data-ttu-id="89544-157">İstemci uygulaması bir kullanıcı hesabı altında çalışıyorsa, sertifika genellikle CurrentUser içinde olur.</span><span class="sxs-lookup"><span data-stu-id="89544-157">If the client application is running under a user account, then the certificate is typically in CurrentUser.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="89544-158">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="89544-158">Child Elements</span></span>  
 <span data-ttu-id="89544-159">Yok.</span><span class="sxs-lookup"><span data-stu-id="89544-159">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="89544-160">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="89544-160">Parent Elements</span></span>  
  
|<span data-ttu-id="89544-161">Öğe</span><span class="sxs-lookup"><span data-stu-id="89544-161">Element</span></span>|<span data-ttu-id="89544-162">Açıklama</span><span class="sxs-lookup"><span data-stu-id="89544-162">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="89544-163">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="89544-163">\<serviceCertificate></span></span>](servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="89544-164">İstemciye bir hizmetin kimlik doğrulaması yapılırken kullanılacak sertifikayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="89544-164">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="89544-165">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="89544-165">Remarks</span></span>  
 <span data-ttu-id="89544-166">Bu yapılandırma öğesinin özniteliği, sertifikaların kimliğini doğrulamak için kullanılan güven düzeyini belirtir. `certificateValidationMode`</span><span class="sxs-lookup"><span data-stu-id="89544-166">The `certificateValidationMode` attribute of this configuration element specifies the level of trust used to authenticate certificates.</span></span> <span data-ttu-id="89544-167">Varsayılan olarak, düzeyi olarak `ChainTrust`ayarlanır; Bu, her bir sertifikanın, zincirin en üstündeki güvenilen bir sertifika yetkilisi ile biten sertifikalar hiyerarşisinde bulunması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="89544-167">By default, the level is set to `ChainTrust`, which specifies that each certificate must be found in a hierarchy of certificates ending in a trusted certification authority at the top of the chain.</span></span> <span data-ttu-id="89544-168">En güvenli mod budur.</span><span class="sxs-lookup"><span data-stu-id="89544-168">This is the most secure mode.</span></span> <span data-ttu-id="89544-169">Ayrıca, otomatik olarak verilen sertifikaların ( `PeerOrChainTrust`eş güven) kabul edildiğini ve güvenilen bir zincirdeki sertifikaların kabul edildiğini belirten değerini olarak da ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="89544-169">You can also set the value to `PeerOrChainTrust`, which specifies that self-issued certificates (peer trust) are accepted as well as certificates that are in a trusted chain.</span></span> <span data-ttu-id="89544-170">Bu değer, istemci ve Hizmetleri geliştirirken ve hata ayıkladığında kullanılır çünkü kendinden verilen sertifikaların güvenilir bir yetkilinizden satın alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="89544-170">This value is used when developing and debugging clients and services because self-issued certificates need not be purchased from a trusted authority.</span></span> <span data-ttu-id="89544-171">Bir istemciyi dağıttığınızda, bunun yerine `ChainTrust` değeri kullanın.</span><span class="sxs-lookup"><span data-stu-id="89544-171">When deploying a client, use the `ChainTrust` value instead.</span></span> <span data-ttu-id="89544-172">Ayrıca, değerini veya `Custom` `None`olarak ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="89544-172">You can also set the value to `Custom` or `None`.</span></span> <span data-ttu-id="89544-173">`Custom` Değerini kullanmak için, bir derlemeyi ve sertifikayı doğrulamak için `customCertificateValidator` kullanılan türünü de özniteliğini ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="89544-173">To use the `Custom` value, you must also set the `customCertificateValidator` attribute to an assembly and type used to validate the certificate.</span></span> <span data-ttu-id="89544-174">Kendi özel Doğrulayıcısı oluşturmak için soyut X509CertificateValidator sınıfından devralması gerekir.</span><span class="sxs-lookup"><span data-stu-id="89544-174">To create your own custom validator, you must inherit from the abstract X509CertificateValidator class.</span></span> <span data-ttu-id="89544-175">Daha fazla bilgi için [nasıl yapılır: Özel bir sertifika Doğrulayıcı](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)kullanan bir hizmet oluşturun.</span><span class="sxs-lookup"><span data-stu-id="89544-175">For more information, see [How to: Create a Service that Employs a Custom Certificate Validator](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span></span>  
  
 <span data-ttu-id="89544-176">Özniteliği `revocationMode` , sertifikaların iptal için nasıl denetleneceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="89544-176">The `revocationMode` attribute specifies how certificates are checked for revocation.</span></span> <span data-ttu-id="89544-177">Varsayılan `online` değer, sertifikaların iptal için otomatik olarak denetleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="89544-177">The default is `online` which indicates that certificates will be checked automatically for revocation.</span></span> <span data-ttu-id="89544-178">Daha fazla bilgi için bkz. [sertifikalarla çalışma](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="89544-178">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="89544-179">Örnek</span><span class="sxs-lookup"><span data-stu-id="89544-179">Example</span></span>  
 <span data-ttu-id="89544-180">Aşağıdaki örnek iki görevi yapar.</span><span class="sxs-lookup"><span data-stu-id="89544-180">The following example does two tasks.</span></span> <span data-ttu-id="89544-181">İlk olarak, etki alanı adı `www.contoso.com` http protokolünün üzerinde olan uç noktalarla iletişim kurarken istemcinin kullanması için bir hizmet sertifikası belirtir.</span><span class="sxs-lookup"><span data-stu-id="89544-181">It first specifies a service certificate for the client to use when communicating with endpoints whose domain name is `www.contoso.com` over the HTTP protocol.</span></span> <span data-ttu-id="89544-182">İkincisi, kimlik doğrulama sırasında kullanılan iptal modunu ve depolama konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="89544-182">Second, it specifies the revocation mode and store location used during authentication.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="89544-183">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="89544-183">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.Authentication%2A>
- <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication>
- [<span data-ttu-id="89544-184">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="89544-184">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="89544-185">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="89544-185">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="89544-186">Nasıl yapılır: Özel bir sertifika Doğrulayıcı kullanan bir hizmet oluşturma</span><span class="sxs-lookup"><span data-stu-id="89544-186">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)
- [<span data-ttu-id="89544-187">\<kimlik doğrulama ></span><span class="sxs-lookup"><span data-stu-id="89544-187">\<authentication></span></span>](authentication-of-clientcertificate-element.md)
- [<span data-ttu-id="89544-188">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="89544-188">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="89544-189">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="89544-189">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
