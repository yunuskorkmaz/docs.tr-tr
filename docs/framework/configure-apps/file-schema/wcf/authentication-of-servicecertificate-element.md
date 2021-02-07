---
description: 'Hakkında daha fazla bilgi edinin: <authentication> <serviceCertificate> öğe'
title: <authentication><serviceCertificate>öğesinin
ms.date: 03/30/2017
ms.assetid: 733b67b4-08a1-4d25-9741-10046f9357ef
ms.openlocfilehash: 35a94f4f9c089f86aef38e7e9a1115a7cd22a325
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749889"
---
# <a name="authentication-of-servicecertificate-element"></a><span data-ttu-id="a5fd0-103">\<authentication>\<serviceCertificate>öğesinin</span><span class="sxs-lookup"><span data-stu-id="a5fd0-103">\<authentication> of \<serviceCertificate> Element</span></span>

<span data-ttu-id="a5fd0-104">SSL/TLS anlaşması kullanılarak elde edilen hizmet sertifikalarının kimlik doğrulaması için istemci proxy tarafından kullanılan ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="a5fd0-104">Specifies the settings used by the client proxy to authenticate service certificates that are obtained using SSL/TLS negotiation.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<authentication>**  
  
## <a name="syntax"></a><span data-ttu-id="a5fd0-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="a5fd0-105">Syntax</span></span>  
  
```xml  
<authentication customCertificateValidatorType="String"
                certificateValidationMode="None/PeerTrust/ChainTrust/PeerOrChainTrust/Custom"
                revocationMode="NoCheck/Online/Offline"
                trustedStoreLocation="LocalMachine/CurrentUser" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a5fd0-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a5fd0-106">Attributes and Elements</span></span>  

 <span data-ttu-id="a5fd0-107">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="a5fd0-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a5fd0-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a5fd0-108">Attributes</span></span>  
  
|<span data-ttu-id="a5fd0-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a5fd0-109">Attribute</span></span>|<span data-ttu-id="a5fd0-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a5fd0-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a5fd0-111">Customcercertificate Atevalidatortype</span><span class="sxs-lookup"><span data-stu-id="a5fd0-111">customCertificateValidatorType</span></span>|<span data-ttu-id="a5fd0-112">Dize.</span><span class="sxs-lookup"><span data-stu-id="a5fd0-112">String.</span></span> <span data-ttu-id="a5fd0-113">Özel bir türü doğrulamak için kullanılan tür ve derleme.</span><span class="sxs-lookup"><span data-stu-id="a5fd0-113">A type and assembly used to validate a custom type.</span></span>|  
|<span data-ttu-id="a5fd0-114">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="a5fd0-114">certificateValidationMode</span></span>|<span data-ttu-id="a5fd0-115">Kimlik bilgilerini doğrulamak için kullanılan üç moddan birini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a5fd0-115">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="a5fd0-116">Olarak ayarlanırsa `Custom` , bir Customcercertificate Atevalidator da sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a5fd0-116">If set to `Custom`, then a customCertificateValidator must also be supplied.</span></span> <span data-ttu-id="a5fd0-117">Varsayılan değer: `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="a5fd0-117">The default is `ChainTrust`.</span></span>|  
|<span data-ttu-id="a5fd0-118">Revocationmodu</span><span class="sxs-lookup"><span data-stu-id="a5fd0-118">revocationMode</span></span>|<span data-ttu-id="a5fd0-119">İptal edilen bir sertifika listesini (CRL) denetlemek için kullanılan modlardan biri.</span><span class="sxs-lookup"><span data-stu-id="a5fd0-119">One of the modes used to check for a revoked certificate lists (CRL).</span></span> <span data-ttu-id="a5fd0-120">Varsayılan değer: `Online`.</span><span class="sxs-lookup"><span data-stu-id="a5fd0-120">The default is `Online`.</span></span>|  
|<span data-ttu-id="a5fd0-121">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="a5fd0-121">trustedStoreLocation</span></span>|<span data-ttu-id="a5fd0-122">İki sistem depolama konumlarından biri: `LocalMachine` veya `CurrentUser` .</span><span class="sxs-lookup"><span data-stu-id="a5fd0-122">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="a5fd0-123">Bu değer, bir hizmet sertifikası istemciye anlaşılırken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a5fd0-123">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="a5fd0-124">Doğrulama, belirtilen depo konumundaki **güvenilir kişiler** deposuna göre gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="a5fd0-124">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="a5fd0-125">Varsayılan değer: `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="a5fd0-125">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidator-attribute"></a><span data-ttu-id="a5fd0-126">Customcercertificate Atevalidator özniteliği</span><span class="sxs-lookup"><span data-stu-id="a5fd0-126">customCertificateValidator Attribute</span></span>  
  
|<span data-ttu-id="a5fd0-127">Değer</span><span class="sxs-lookup"><span data-stu-id="a5fd0-127">Value</span></span>|<span data-ttu-id="a5fd0-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a5fd0-128">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a5fd0-129">Dize</span><span class="sxs-lookup"><span data-stu-id="a5fd0-129">String</span></span>|<span data-ttu-id="a5fd0-130">Türü bulmak için kullanılan tür adını ve derlemeyi ve diğer verileri belirtir.</span><span class="sxs-lookup"><span data-stu-id="a5fd0-130">Specifies the type name and assembly and other data used to find the type.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="a5fd0-131">certificateValidationMode özniteliği</span><span class="sxs-lookup"><span data-stu-id="a5fd0-131">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="a5fd0-132">Değer</span><span class="sxs-lookup"><span data-stu-id="a5fd0-132">Value</span></span>|<span data-ttu-id="a5fd0-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a5fd0-133">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a5fd0-134">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="a5fd0-134">Enumeration</span></span>|<span data-ttu-id="a5fd0-135">Şu değerlerden biri: None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.</span><span class="sxs-lookup"><span data-stu-id="a5fd0-135">One of the following values: None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.</span></span><br /><br /> <span data-ttu-id="a5fd0-136">Daha fazla bilgi için bkz. [sertifikalarla çalışma](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="a5fd0-136">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="a5fd0-137">revocationMode özniteliği</span><span class="sxs-lookup"><span data-stu-id="a5fd0-137">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="a5fd0-138">Değer</span><span class="sxs-lookup"><span data-stu-id="a5fd0-138">Value</span></span>|<span data-ttu-id="a5fd0-139">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a5fd0-139">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a5fd0-140">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="a5fd0-140">Enumeration</span></span>|<span data-ttu-id="a5fd0-141">Şu değerlerden biri: NoCheck, çevrimiçi, çevrimdışı.</span><span class="sxs-lookup"><span data-stu-id="a5fd0-141">One of the following values: NoCheck, Online, Offline.</span></span><br /><br /> <span data-ttu-id="a5fd0-142">Daha fazla bilgi için bkz. [sertifikalarla çalışma](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="a5fd0-142">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="a5fd0-143">trustedStoreLocation özniteliği</span><span class="sxs-lookup"><span data-stu-id="a5fd0-143">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="a5fd0-144">Değer</span><span class="sxs-lookup"><span data-stu-id="a5fd0-144">Value</span></span>|<span data-ttu-id="a5fd0-145">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a5fd0-145">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a5fd0-146">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="a5fd0-146">Enumeration</span></span>|<span data-ttu-id="a5fd0-147">Şu değerlerden biri: LocalMachine ya da CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="a5fd0-147">One of the following values: LocalMachine or CurrentUser.</span></span> <span data-ttu-id="a5fd0-148">Varsayılan değer CurrentUser ' dır.</span><span class="sxs-lookup"><span data-stu-id="a5fd0-148">The default is CurrentUser.</span></span> <span data-ttu-id="a5fd0-149">İstemci uygulaması bir sistem hesabı altında çalışıyorsa, sertifika genellikle LocalMachine altında olur.</span><span class="sxs-lookup"><span data-stu-id="a5fd0-149">If the client application is running under a system account, then the certificate is typically under LocalMachine.</span></span> <span data-ttu-id="a5fd0-150">İstemci uygulaması bir kullanıcı hesabı altında çalışıyorsa, sertifika genellikle CurrentUser içinde olur.</span><span class="sxs-lookup"><span data-stu-id="a5fd0-150">If the client application is running under a user account, then the certificate is typically in CurrentUser.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a5fd0-151">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a5fd0-151">Child Elements</span></span>  

 <span data-ttu-id="a5fd0-152">Yok.</span><span class="sxs-lookup"><span data-stu-id="a5fd0-152">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a5fd0-153">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a5fd0-153">Parent Elements</span></span>  
  
|<span data-ttu-id="a5fd0-154">Öğe</span><span class="sxs-lookup"><span data-stu-id="a5fd0-154">Element</span></span>|<span data-ttu-id="a5fd0-155">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a5fd0-155">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCertificate>](servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="a5fd0-156">İstemciye bir hizmetin kimlik doğrulaması yapılırken kullanılacak sertifikayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="a5fd0-156">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a5fd0-157">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a5fd0-157">Remarks</span></span>  

 <span data-ttu-id="a5fd0-158">`certificateValidationMode`Bu yapılandırma öğesinin özniteliği, sertifikaların kimliğini doğrulamak için kullanılan güven düzeyini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a5fd0-158">The `certificateValidationMode` attribute of this configuration element specifies the level of trust used to authenticate certificates.</span></span> <span data-ttu-id="a5fd0-159">Varsayılan olarak, düzeyi olarak ayarlanır `ChainTrust` ; Bu, her bir sertifikanın, zincirin en üstündeki güvenilen bir sertifika yetkilisi ile biten sertifikalar hiyerarşisinde bulunması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a5fd0-159">By default, the level is set to `ChainTrust`, which specifies that each certificate must be found in a hierarchy of certificates ending in a trusted certification authority at the top of the chain.</span></span> <span data-ttu-id="a5fd0-160">En güvenli mod budur.</span><span class="sxs-lookup"><span data-stu-id="a5fd0-160">This is the most secure mode.</span></span> <span data-ttu-id="a5fd0-161">Ayrıca, `PeerOrChainTrust` otomatik olarak verilen sertifikaların (eş güven) kabul edildiğini ve güvenilen bir zincirdeki sertifikaların kabul edildiğini belirten değerini olarak da ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a5fd0-161">You can also set the value to `PeerOrChainTrust`, which specifies that self-issued certificates (peer trust) are accepted as well as certificates that are in a trusted chain.</span></span> <span data-ttu-id="a5fd0-162">Bu değer, istemci ve Hizmetleri geliştirirken ve hata ayıkladığında kullanılır çünkü kendinden verilen sertifikaların güvenilir bir yetkilinizden satın alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a5fd0-162">This value is used when developing and debugging clients and services because self-issued certificates need not be purchased from a trusted authority.</span></span> <span data-ttu-id="a5fd0-163">Bir istemciyi dağıttığınızda, `ChainTrust` bunun yerine değeri kullanın.</span><span class="sxs-lookup"><span data-stu-id="a5fd0-163">When deploying a client, use the `ChainTrust` value instead.</span></span> <span data-ttu-id="a5fd0-164">Ayrıca, değerini veya olarak ayarlayabilirsiniz `Custom` `None` .</span><span class="sxs-lookup"><span data-stu-id="a5fd0-164">You can also set the value to `Custom` or `None`.</span></span> <span data-ttu-id="a5fd0-165">Değerini kullanmak için `Custom` , `customCertificateValidator` bir derlemeyi ve sertifikayı doğrulamak için kullanılan türünü de özniteliğini ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a5fd0-165">To use the `Custom` value, you must also set the `customCertificateValidator` attribute to an assembly and type used to validate the certificate.</span></span> <span data-ttu-id="a5fd0-166">Kendi özel Doğrulayıcısı oluşturmak için soyut X509CertificateValidator sınıfından devralması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a5fd0-166">To create your own custom validator, you must inherit from the abstract X509CertificateValidator class.</span></span> <span data-ttu-id="a5fd0-167">Daha fazla bilgi için bkz. [nasıl yapılır: özel bir sertifika Doğrulayıcı kullanan bir hizmet oluşturma](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span><span class="sxs-lookup"><span data-stu-id="a5fd0-167">For more information, see [How to: Create a Service that Employs a Custom Certificate Validator](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span></span>  
  
 <span data-ttu-id="a5fd0-168">`revocationMode`Özniteliği, sertifikaların iptal için nasıl denetleneceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a5fd0-168">The `revocationMode` attribute specifies how certificates are checked for revocation.</span></span> <span data-ttu-id="a5fd0-169">Varsayılan değer, `online` sertifikaların iptal için otomatik olarak denetleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a5fd0-169">The default is `online` which indicates that certificates will be checked automatically for revocation.</span></span> <span data-ttu-id="a5fd0-170">Daha fazla bilgi için bkz. [sertifikalarla çalışma](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="a5fd0-170">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5fd0-171">Örnek</span><span class="sxs-lookup"><span data-stu-id="a5fd0-171">Example</span></span>  

 <span data-ttu-id="a5fd0-172">Aşağıdaki örnek iki görevi yapar.</span><span class="sxs-lookup"><span data-stu-id="a5fd0-172">The following example does two tasks.</span></span> <span data-ttu-id="a5fd0-173">İlk olarak, etki alanı adı HTTP protokolünün üzerinde olan uç noktalarla iletişim kurarken istemcinin kullanması için bir hizmet sertifikası belirtir `www.contoso.com` .</span><span class="sxs-lookup"><span data-stu-id="a5fd0-173">It first specifies a service certificate for the client to use when communicating with endpoints whose domain name is `www.contoso.com` over the HTTP protocol.</span></span> <span data-ttu-id="a5fd0-174">İkincisi, kimlik doğrulama sırasında kullanılan iptal modunu ve depolama konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="a5fd0-174">Second, it specifies the revocation mode and store location used during authentication.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a5fd0-175">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a5fd0-175">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.Authentication%2A>
- <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication>
- [<span data-ttu-id="a5fd0-176">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="a5fd0-176">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="a5fd0-177">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="a5fd0-177">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="a5fd0-178">Nasıl yapılır: Özel Bir Sertifika Doğrulayıcı Kullanan Bir Hizmet Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a5fd0-178">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)
- [\<authentication>](authentication-of-clientcertificate-element.md)
- [<span data-ttu-id="a5fd0-179">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="a5fd0-179">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="a5fd0-180">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="a5fd0-180">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
