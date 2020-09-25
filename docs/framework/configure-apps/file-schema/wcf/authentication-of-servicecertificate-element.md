---
title: <authentication><serviceCertificate>öğesinin
ms.date: 03/30/2017
ms.assetid: 733b67b4-08a1-4d25-9741-10046f9357ef
ms.openlocfilehash: c6f2578d85971740e5bd3d75151305a475187492
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201596"
---
# <a name="authentication-of-servicecertificate-element"></a><span data-ttu-id="f560c-102">\<authentication>\<serviceCertificate>öğesinin</span><span class="sxs-lookup"><span data-stu-id="f560c-102">\<authentication> of \<serviceCertificate> Element</span></span>

<span data-ttu-id="f560c-103">SSL/TLS anlaşması kullanılarak elde edilen hizmet sertifikalarının kimlik doğrulaması için istemci proxy tarafından kullanılan ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="f560c-103">Specifies the settings used by the client proxy to authenticate service certificates that are obtained using SSL/TLS negotiation.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<authentication>**  
  
## <a name="syntax"></a><span data-ttu-id="f560c-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="f560c-104">Syntax</span></span>  
  
```xml  
<authentication customCertificateValidatorType="String"
                certificateValidationMode="None/PeerTrust/ChainTrust/PeerOrChainTrust/Custom"
                revocationMode="NoCheck/Online/Offline"
                trustedStoreLocation="LocalMachine/CurrentUser" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f560c-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f560c-105">Attributes and Elements</span></span>  

 <span data-ttu-id="f560c-106">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="f560c-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f560c-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f560c-107">Attributes</span></span>  
  
|<span data-ttu-id="f560c-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f560c-108">Attribute</span></span>|<span data-ttu-id="f560c-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f560c-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f560c-110">Customcercertificate Atevalidatortype</span><span class="sxs-lookup"><span data-stu-id="f560c-110">customCertificateValidatorType</span></span>|<span data-ttu-id="f560c-111">Dize.</span><span class="sxs-lookup"><span data-stu-id="f560c-111">String.</span></span> <span data-ttu-id="f560c-112">Özel bir türü doğrulamak için kullanılan tür ve derleme.</span><span class="sxs-lookup"><span data-stu-id="f560c-112">A type and assembly used to validate a custom type.</span></span>|  
|<span data-ttu-id="f560c-113">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="f560c-113">certificateValidationMode</span></span>|<span data-ttu-id="f560c-114">Kimlik bilgilerini doğrulamak için kullanılan üç moddan birini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f560c-114">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="f560c-115">Olarak ayarlanırsa `Custom` , bir Customcercertificate Atevalidator da sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f560c-115">If set to `Custom`, then a customCertificateValidator must also be supplied.</span></span> <span data-ttu-id="f560c-116">Varsayılan değer: `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="f560c-116">The default is `ChainTrust`.</span></span>|  
|<span data-ttu-id="f560c-117">Revocationmodu</span><span class="sxs-lookup"><span data-stu-id="f560c-117">revocationMode</span></span>|<span data-ttu-id="f560c-118">İptal edilen bir sertifika listesini (CRL) denetlemek için kullanılan modlardan biri.</span><span class="sxs-lookup"><span data-stu-id="f560c-118">One of the modes used to check for a revoked certificate lists (CRL).</span></span> <span data-ttu-id="f560c-119">Varsayılan değer: `Online`.</span><span class="sxs-lookup"><span data-stu-id="f560c-119">The default is `Online`.</span></span>|  
|<span data-ttu-id="f560c-120">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="f560c-120">trustedStoreLocation</span></span>|<span data-ttu-id="f560c-121">İki sistem depolama konumlarından biri: `LocalMachine` veya `CurrentUser` .</span><span class="sxs-lookup"><span data-stu-id="f560c-121">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="f560c-122">Bu değer, bir hizmet sertifikası istemciye anlaşılırken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f560c-122">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="f560c-123">Doğrulama, belirtilen depo konumundaki **güvenilir kişiler** deposuna göre gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="f560c-123">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="f560c-124">Varsayılan değer: `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="f560c-124">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidator-attribute"></a><span data-ttu-id="f560c-125">Customcercertificate Atevalidator özniteliği</span><span class="sxs-lookup"><span data-stu-id="f560c-125">customCertificateValidator Attribute</span></span>  
  
|<span data-ttu-id="f560c-126">Değer</span><span class="sxs-lookup"><span data-stu-id="f560c-126">Value</span></span>|<span data-ttu-id="f560c-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f560c-127">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f560c-128">Dize</span><span class="sxs-lookup"><span data-stu-id="f560c-128">String</span></span>|<span data-ttu-id="f560c-129">Türü bulmak için kullanılan tür adını ve derlemeyi ve diğer verileri belirtir.</span><span class="sxs-lookup"><span data-stu-id="f560c-129">Specifies the type name and assembly and other data used to find the type.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="f560c-130">certificateValidationMode özniteliği</span><span class="sxs-lookup"><span data-stu-id="f560c-130">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="f560c-131">Değer</span><span class="sxs-lookup"><span data-stu-id="f560c-131">Value</span></span>|<span data-ttu-id="f560c-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f560c-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f560c-133">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="f560c-133">Enumeration</span></span>|<span data-ttu-id="f560c-134">Şu değerlerden biri: None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.</span><span class="sxs-lookup"><span data-stu-id="f560c-134">One of the following values: None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.</span></span><br /><br /> <span data-ttu-id="f560c-135">Daha fazla bilgi için bkz. [sertifikalarla çalışma](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="f560c-135">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="f560c-136">revocationMode özniteliği</span><span class="sxs-lookup"><span data-stu-id="f560c-136">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="f560c-137">Değer</span><span class="sxs-lookup"><span data-stu-id="f560c-137">Value</span></span>|<span data-ttu-id="f560c-138">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f560c-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f560c-139">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="f560c-139">Enumeration</span></span>|<span data-ttu-id="f560c-140">Şu değerlerden biri: NoCheck, çevrimiçi, çevrimdışı.</span><span class="sxs-lookup"><span data-stu-id="f560c-140">One of the following values: NoCheck, Online, Offline.</span></span><br /><br /> <span data-ttu-id="f560c-141">Daha fazla bilgi için bkz. [sertifikalarla çalışma](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="f560c-141">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="f560c-142">trustedStoreLocation özniteliği</span><span class="sxs-lookup"><span data-stu-id="f560c-142">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="f560c-143">Değer</span><span class="sxs-lookup"><span data-stu-id="f560c-143">Value</span></span>|<span data-ttu-id="f560c-144">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f560c-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f560c-145">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="f560c-145">Enumeration</span></span>|<span data-ttu-id="f560c-146">Şu değerlerden biri: LocalMachine ya da CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="f560c-146">One of the following values: LocalMachine or CurrentUser.</span></span> <span data-ttu-id="f560c-147">Varsayılan değer CurrentUser ' dır.</span><span class="sxs-lookup"><span data-stu-id="f560c-147">The default is CurrentUser.</span></span> <span data-ttu-id="f560c-148">İstemci uygulaması bir sistem hesabı altında çalışıyorsa, sertifika genellikle LocalMachine altında olur.</span><span class="sxs-lookup"><span data-stu-id="f560c-148">If the client application is running under a system account, then the certificate is typically under LocalMachine.</span></span> <span data-ttu-id="f560c-149">İstemci uygulaması bir kullanıcı hesabı altında çalışıyorsa, sertifika genellikle CurrentUser içinde olur.</span><span class="sxs-lookup"><span data-stu-id="f560c-149">If the client application is running under a user account, then the certificate is typically in CurrentUser.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f560c-150">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f560c-150">Child Elements</span></span>  

 <span data-ttu-id="f560c-151">Yok.</span><span class="sxs-lookup"><span data-stu-id="f560c-151">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f560c-152">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f560c-152">Parent Elements</span></span>  
  
|<span data-ttu-id="f560c-153">Öğe</span><span class="sxs-lookup"><span data-stu-id="f560c-153">Element</span></span>|<span data-ttu-id="f560c-154">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f560c-154">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCertificate>](servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="f560c-155">İstemciye bir hizmetin kimlik doğrulaması yapılırken kullanılacak sertifikayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="f560c-155">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f560c-156">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f560c-156">Remarks</span></span>  

 <span data-ttu-id="f560c-157">`certificateValidationMode`Bu yapılandırma öğesinin özniteliği, sertifikaların kimliğini doğrulamak için kullanılan güven düzeyini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f560c-157">The `certificateValidationMode` attribute of this configuration element specifies the level of trust used to authenticate certificates.</span></span> <span data-ttu-id="f560c-158">Varsayılan olarak, düzeyi olarak ayarlanır `ChainTrust` ; Bu, her bir sertifikanın, zincirin en üstündeki güvenilen bir sertifika yetkilisi ile biten sertifikalar hiyerarşisinde bulunması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f560c-158">By default, the level is set to `ChainTrust`, which specifies that each certificate must be found in a hierarchy of certificates ending in a trusted certification authority at the top of the chain.</span></span> <span data-ttu-id="f560c-159">En güvenli mod budur.</span><span class="sxs-lookup"><span data-stu-id="f560c-159">This is the most secure mode.</span></span> <span data-ttu-id="f560c-160">Ayrıca, `PeerOrChainTrust` otomatik olarak verilen sertifikaların (eş güven) kabul edildiğini ve güvenilen bir zincirdeki sertifikaların kabul edildiğini belirten değerini olarak da ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f560c-160">You can also set the value to `PeerOrChainTrust`, which specifies that self-issued certificates (peer trust) are accepted as well as certificates that are in a trusted chain.</span></span> <span data-ttu-id="f560c-161">Bu değer, istemci ve Hizmetleri geliştirirken ve hata ayıkladığında kullanılır çünkü kendinden verilen sertifikaların güvenilir bir yetkilinizden satın alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f560c-161">This value is used when developing and debugging clients and services because self-issued certificates need not be purchased from a trusted authority.</span></span> <span data-ttu-id="f560c-162">Bir istemciyi dağıttığınızda, `ChainTrust` bunun yerine değeri kullanın.</span><span class="sxs-lookup"><span data-stu-id="f560c-162">When deploying a client, use the `ChainTrust` value instead.</span></span> <span data-ttu-id="f560c-163">Ayrıca, değerini veya olarak ayarlayabilirsiniz `Custom` `None` .</span><span class="sxs-lookup"><span data-stu-id="f560c-163">You can also set the value to `Custom` or `None`.</span></span> <span data-ttu-id="f560c-164">Değerini kullanmak için `Custom` , `customCertificateValidator` bir derlemeyi ve sertifikayı doğrulamak için kullanılan türünü de özniteliğini ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f560c-164">To use the `Custom` value, you must also set the `customCertificateValidator` attribute to an assembly and type used to validate the certificate.</span></span> <span data-ttu-id="f560c-165">Kendi özel Doğrulayıcısı oluşturmak için soyut X509CertificateValidator sınıfından devralması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f560c-165">To create your own custom validator, you must inherit from the abstract X509CertificateValidator class.</span></span> <span data-ttu-id="f560c-166">Daha fazla bilgi için bkz. [nasıl yapılır: özel bir sertifika Doğrulayıcı kullanan bir hizmet oluşturma](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span><span class="sxs-lookup"><span data-stu-id="f560c-166">For more information, see [How to: Create a Service that Employs a Custom Certificate Validator](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span></span>  
  
 <span data-ttu-id="f560c-167">`revocationMode`Özniteliği, sertifikaların iptal için nasıl denetleneceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f560c-167">The `revocationMode` attribute specifies how certificates are checked for revocation.</span></span> <span data-ttu-id="f560c-168">Varsayılan değer, `online` sertifikaların iptal için otomatik olarak denetleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f560c-168">The default is `online` which indicates that certificates will be checked automatically for revocation.</span></span> <span data-ttu-id="f560c-169">Daha fazla bilgi için bkz. [sertifikalarla çalışma](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="f560c-169">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f560c-170">Örnek</span><span class="sxs-lookup"><span data-stu-id="f560c-170">Example</span></span>  

 <span data-ttu-id="f560c-171">Aşağıdaki örnek iki görevi yapar.</span><span class="sxs-lookup"><span data-stu-id="f560c-171">The following example does two tasks.</span></span> <span data-ttu-id="f560c-172">İlk olarak, etki alanı adı HTTP protokolünün üzerinde olan uç noktalarla iletişim kurarken istemcinin kullanması için bir hizmet sertifikası belirtir `www.contoso.com` .</span><span class="sxs-lookup"><span data-stu-id="f560c-172">It first specifies a service certificate for the client to use when communicating with endpoints whose domain name is `www.contoso.com` over the HTTP protocol.</span></span> <span data-ttu-id="f560c-173">İkincisi, kimlik doğrulama sırasında kullanılan iptal modunu ve depolama konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="f560c-173">Second, it specifies the revocation mode and store location used during authentication.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f560c-174">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f560c-174">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.Authentication%2A>
- <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication>
- [<span data-ttu-id="f560c-175">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="f560c-175">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="f560c-176">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="f560c-176">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="f560c-177">Nasıl yapılır: Özel Bir Sertifika Doğrulayıcı Kullanan Bir Hizmet Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f560c-177">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)
- [\<authentication>](authentication-of-clientcertificate-element.md)
- [<span data-ttu-id="f560c-178">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="f560c-178">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="f560c-179">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="f560c-179">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
