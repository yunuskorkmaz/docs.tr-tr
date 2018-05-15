---
title: '&lt;clientCertificate&gt; Öğesi &lt;kimlik doğrulama&gt;'
ms.date: 03/30/2017
ms.assetid: 4a55eea2-1826-4026-b911-b7cc9e9c8bfe
ms.openlocfilehash: ccc184f63428fd4a12b9047c0bcf4416e87f24d2
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltauthenticationgt-of-ltclientcertificategt-element"></a><span data-ttu-id="86333-102">&lt;clientCertificate&gt; Öğesi &lt;kimlik doğrulama&gt;</span><span class="sxs-lookup"><span data-stu-id="86333-102">&lt;authentication&gt; of &lt;clientCertificate&gt; Element</span></span>
<span data-ttu-id="86333-103">Bir hizmeti tarafından kullanılan istemci sertifikaları için kimlik doğrulama davranışları belirtir.</span><span class="sxs-lookup"><span data-stu-id="86333-103">Specifies authentication behaviors for client certificates used by a service.</span></span>  
  
 <span data-ttu-id="86333-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="86333-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="86333-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="86333-105">\<behaviors></span></span>  
<span data-ttu-id="86333-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="86333-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="86333-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="86333-107">\<behavior></span></span>  
<span data-ttu-id="86333-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="86333-108">\<serviceCredentials></span></span>  
<span data-ttu-id="86333-109">\<clientCertificate ></span><span class="sxs-lookup"><span data-stu-id="86333-109">\<clientCertificate></span></span>  
<span data-ttu-id="86333-110">\<kimlik doğrulama ></span><span class="sxs-lookup"><span data-stu-id="86333-110">\<authentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86333-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="86333-111">Syntax</span></span>  
  
```xml  
<authentication  
customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
includeWindowsGroups="Boolean"  
mapClientCertificateToWindowsAccount="Boolean"  
revocationMode="NoCheck/Online/Offline"  
trustedStoreLocation="CurrentUser/LocalMachine"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="86333-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="86333-112">Attributes and Elements</span></span>  
 <span data-ttu-id="86333-113">Öznitelikler, alt öğelerini ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır</span><span class="sxs-lookup"><span data-stu-id="86333-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="86333-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="86333-114">Attributes</span></span>  
  
|<span data-ttu-id="86333-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="86333-115">Attribute</span></span>|<span data-ttu-id="86333-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="86333-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="86333-117">customCertificateValidatorType</span><span class="sxs-lookup"><span data-stu-id="86333-117">customCertificateValidatorType</span></span>|<span data-ttu-id="86333-118">İsteğe bağlı dize.</span><span class="sxs-lookup"><span data-stu-id="86333-118">Optional string.</span></span> <span data-ttu-id="86333-119">Tür ve bir özel tür doğrulamak için kullanılan derleme.</span><span class="sxs-lookup"><span data-stu-id="86333-119">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="86333-120">Bu öznitelik ne zaman ayarlanmalıdır `certificateValidationMode` ayarlanır `Custom`.</span><span class="sxs-lookup"><span data-stu-id="86333-120">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|<span data-ttu-id="86333-121">certificateValidationMode değerini</span><span class="sxs-lookup"><span data-stu-id="86333-121">certificateValidationMode</span></span>|<span data-ttu-id="86333-122">İsteğe bağlı numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="86333-122">Optional enumeration.</span></span> <span data-ttu-id="86333-123">Kimlik bilgilerini doğrulamak için kullanılan modlarından birini belirtir.</span><span class="sxs-lookup"><span data-stu-id="86333-123">Specifies one of the modes used to validate credentials.</span></span> <span data-ttu-id="86333-124">Bu özniteliktir <xref:System.ServiceModel.Security.X509CertificateValidationMode> türü.</span><span class="sxs-lookup"><span data-stu-id="86333-124">This attribute is of the <xref:System.ServiceModel.Security.X509CertificateValidationMode> type.</span></span> <span data-ttu-id="86333-125">Varsa kümesine <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom?displayProperty=nameWithType>, sonra bir `customCertificateValidator` de sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="86333-125">If set to <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom?displayProperty=nameWithType>, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="86333-126">Varsayılan, <xref:System.ServiceModel.Security.X509CertificateValidationMode.ChainTrust?displayProperty=nameWithType> değeridir.</span><span class="sxs-lookup"><span data-stu-id="86333-126">The default is <xref:System.ServiceModel.Security.X509CertificateValidationMode.ChainTrust?displayProperty=nameWithType>.</span></span>|  
|<span data-ttu-id="86333-127">includeWindowsGroups</span><span class="sxs-lookup"><span data-stu-id="86333-127">includeWindowsGroups</span></span>|<span data-ttu-id="86333-128">İsteğe bağlı Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="86333-128">Optional Boolean.</span></span> <span data-ttu-id="86333-129">Windows grupları güvenlik bağlamında dahil edilip edilmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="86333-129">Specifies if Windows groups are included in the security context.</span></span> <span data-ttu-id="86333-130">Bu öznitelik ayarını `true` bir tam Grup genişletme sonuçları gibi bir performans etkisi olur.</span><span class="sxs-lookup"><span data-stu-id="86333-130">Setting this attribute to `true` has a performance impact, as it results in a full group expansion.</span></span> <span data-ttu-id="86333-131">Bu öznitelik ayarlanırsa `false` gruplarının listesini oluşturmak ihtiyacınız yoksa bir kullanıcının ait olduğu.</span><span class="sxs-lookup"><span data-stu-id="86333-131">Set this attribute to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|<span data-ttu-id="86333-132">mapClientCertificateToWindowsAcccount</span><span class="sxs-lookup"><span data-stu-id="86333-132">mapClientCertificateToWindowsAcccount</span></span>|<span data-ttu-id="86333-133">Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="86333-133">Boolean.</span></span> <span data-ttu-id="86333-134">İstemci sertifikası kullanılarak bir Windows kimliğine eşlenen olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="86333-134">Specifies whether the client can be mapped to a Windows identity using the certificate.</span></span> <span data-ttu-id="86333-135">Bunu yapmak için Active Directory etkinleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="86333-135">Active Directory must be enabled to do this.</span></span>|  
|<span data-ttu-id="86333-136">revocationMode</span><span class="sxs-lookup"><span data-stu-id="86333-136">revocationMode</span></span>|<span data-ttu-id="86333-137">İsteğe bağlı numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="86333-137">Optional enumeration.</span></span> <span data-ttu-id="86333-138">İptal edilen sertifika (RCL) listeler denetlemek için kullanılan modlarından birini.</span><span class="sxs-lookup"><span data-stu-id="86333-138">One of the modes used to check for a revoked certificate lists (RCL).</span></span> <span data-ttu-id="86333-139">Varsayılan, `Online` değeridir.</span><span class="sxs-lookup"><span data-stu-id="86333-139">The default is `Online`.</span></span> <span data-ttu-id="86333-140">Bu değer, HTTP taşıma güvenliği kullanırken dikkate alınmaz.</span><span class="sxs-lookup"><span data-stu-id="86333-140">This value is ignored when using HTTP transport security.</span></span>|  
|<span data-ttu-id="86333-141">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="86333-141">trustedStoreLocation</span></span>|<span data-ttu-id="86333-142">İsteğe bağlı numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="86333-142">Optional enumeration.</span></span> <span data-ttu-id="86333-143">İki sistem deposu konumlardan birini: `LocalMachine` veya `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="86333-143">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="86333-144">Bu değer, bir hizmet sertifikası istemciye anlaşıldığında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="86333-144">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="86333-145">Doğrulama işlemi gerçekleştirildiğinde karşı **güvenilir kişiler** belirtilen depo konumda saklayın.</span><span class="sxs-lookup"><span data-stu-id="86333-145">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="86333-146">Varsayılan, `CurrentUser` değeridir.</span><span class="sxs-lookup"><span data-stu-id="86333-146">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="86333-147">customCertificateValidatorType özniteliği</span><span class="sxs-lookup"><span data-stu-id="86333-147">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="86333-148">Değer</span><span class="sxs-lookup"><span data-stu-id="86333-148">Value</span></span>|<span data-ttu-id="86333-149">Açıklama</span><span class="sxs-lookup"><span data-stu-id="86333-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="86333-150">Dize</span><span class="sxs-lookup"><span data-stu-id="86333-150">String</span></span>|<span data-ttu-id="86333-151">Tür adı ve derleme ve diğer veri türü bulmak için kullanılan belirtir.</span><span class="sxs-lookup"><span data-stu-id="86333-151">Specifies the type name and assembly and other data used to find the type.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="86333-152">certificateValidationMode değerini özniteliği</span><span class="sxs-lookup"><span data-stu-id="86333-152">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="86333-153">Değer</span><span class="sxs-lookup"><span data-stu-id="86333-153">Value</span></span>|<span data-ttu-id="86333-154">Açıklama</span><span class="sxs-lookup"><span data-stu-id="86333-154">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="86333-155">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="86333-155">Enumeration</span></span>|<span data-ttu-id="86333-156">Aşağıdaki değerlerden biri: None, PeerTrust, ChainTrust, PeerOrChainTrust, özel.</span><span class="sxs-lookup"><span data-stu-id="86333-156">One of the following values: None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.</span></span><br /><br /> <span data-ttu-id="86333-157">Daha fazla bilgi için bkz: [sertifikalarla çalışma](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="86333-157">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="86333-158">revocationMode özniteliği</span><span class="sxs-lookup"><span data-stu-id="86333-158">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="86333-159">Değer</span><span class="sxs-lookup"><span data-stu-id="86333-159">Value</span></span>|<span data-ttu-id="86333-160">Açıklama</span><span class="sxs-lookup"><span data-stu-id="86333-160">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="86333-161">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="86333-161">Enumeration</span></span>|<span data-ttu-id="86333-162">Aşağıdaki değerlerden birini: NoCheck, çevrimiçi, çevrimdışı.</span><span class="sxs-lookup"><span data-stu-id="86333-162">One of the following values: NoCheck, Online, Offline.</span></span> <span data-ttu-id="86333-163">Daha fazla bilgi için bkz: [sertifikalarla çalışma](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="86333-163">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="86333-164">trustedStoreLocation özniteliği</span><span class="sxs-lookup"><span data-stu-id="86333-164">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="86333-165">Değer</span><span class="sxs-lookup"><span data-stu-id="86333-165">Value</span></span>|<span data-ttu-id="86333-166">Açıklama</span><span class="sxs-lookup"><span data-stu-id="86333-166">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="86333-167">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="86333-167">Enumeration</span></span>|<span data-ttu-id="86333-168">Aşağıdaki değerlerden birini: `LocalMachine` veya `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="86333-168">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="86333-169">Varsayılan, `CurrentUser` değeridir.</span><span class="sxs-lookup"><span data-stu-id="86333-169">The default is `CurrentUser`.</span></span> <span data-ttu-id="86333-170">İstemci uygulaması bir sistem hesabı altında çalışan sonra sertifika genellikle altında olduğu `LocalMachine`.</span><span class="sxs-lookup"><span data-stu-id="86333-170">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="86333-171">İstemci uygulama bir kullanıcı hesabı altında çalışan sonra sertifikayı genellikle kullanımda `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="86333-171">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="86333-172">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="86333-172">Child Elements</span></span>  
 <span data-ttu-id="86333-173">Yok.</span><span class="sxs-lookup"><span data-stu-id="86333-173">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="86333-174">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="86333-174">Parent Elements</span></span>  
  
|<span data-ttu-id="86333-175">Öğe</span><span class="sxs-lookup"><span data-stu-id="86333-175">Element</span></span>|<span data-ttu-id="86333-176">Açıklama</span><span class="sxs-lookup"><span data-stu-id="86333-176">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="86333-177">\<clientCertificate ></span><span class="sxs-lookup"><span data-stu-id="86333-177">\<clientCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)|<span data-ttu-id="86333-178">Bir hizmet için bir istemci kimlik doğrulaması için kullanılan bir X.509 sertifikası tanımlar.</span><span class="sxs-lookup"><span data-stu-id="86333-178">Defines an X.509 certificate used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="86333-179">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="86333-179">Remarks</span></span>  
 <span data-ttu-id="86333-180">`<authentication>` Öğesi karşılık gelen <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="86333-180">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> class.</span></span> <span data-ttu-id="86333-181">İstemcilerin nasıl doğrulanır özelleştirmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="86333-181">It enables you to customize how clients are authenticated.</span></span> <span data-ttu-id="86333-182">Ayarlayabileceğiniz `certificateValidationMode` özniteliğini `None`, `ChainTrust`, `PeerOrChainTrust`, `PeerTrust`, veya `Custom`.</span><span class="sxs-lookup"><span data-stu-id="86333-182">You can set the `certificateValidationMode` attribute to `None`, `ChainTrust`, `PeerOrChainTrust`, `PeerTrust`, or `Custom`.</span></span> <span data-ttu-id="86333-183">Varsayılan olarak, düzeyini ayarlamak `ChainTrust`, belirten her sertifika biten sertifika hiyerarşisini bulunması gereken bir *kök yetkilisi* zincirinin üstünde.</span><span class="sxs-lookup"><span data-stu-id="86333-183">By default, the level is set to `ChainTrust`, which specifies that each certificate must be found in a hierarchy of certificates ending in a *root authority* at the top of the chain.</span></span> <span data-ttu-id="86333-184">Bu en güvenli bir moddur.</span><span class="sxs-lookup"><span data-stu-id="86333-184">This is the most secure mode.</span></span> <span data-ttu-id="86333-185">De değer ayarlayabilirsiniz `PeerOrChainTrust`, kendi kendine verilen sertifikaların (eş güven) güvenilen zincirinde sertifikaları yanı sıra kabul edileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="86333-185">You can also set the value to `PeerOrChainTrust`, which specifies that self-issued certificates (peer trust) are accepted as well as certificates that are in a trusted chain.</span></span> <span data-ttu-id="86333-186">Bu değer, geliştirme ve kendi kendine verilen sertifikaların güvenilir bir yetkiliden satın alınması değil çünkü hata ayıklama istemcileri ve Hizmetleri zaman kullanılır.</span><span class="sxs-lookup"><span data-stu-id="86333-186">This value is used when developing and debugging clients and services because self-issued certificates need not be purchased from a trusted authority.</span></span> <span data-ttu-id="86333-187">Bir istemci dağıtımı sırasında kullanmak `ChainTrust` yerine değer.</span><span class="sxs-lookup"><span data-stu-id="86333-187">When deploying a client, use the `ChainTrust` value instead.</span></span>  
  
 <span data-ttu-id="86333-188">De değer ayarlayabilirsiniz `Custom`.</span><span class="sxs-lookup"><span data-stu-id="86333-188">You can also set the value to `Custom`.</span></span> <span data-ttu-id="86333-189">Ayarlandığında `Custom` değeri de ayarlamanız gerekir `customCertificateValidatorType` özniteliği bir derleme ve sertifikayı doğrulamak için kullanılan türü.</span><span class="sxs-lookup"><span data-stu-id="86333-189">When set to the `Custom` value, you must also set the `customCertificateValidatorType` attribute to an assembly and type used to validate the certificate.</span></span> <span data-ttu-id="86333-190">Kendi özel Doğrulayıcısı oluşturmak için Özet devralmalıdır <xref:System.IdentityModel.Selectors.X509CertificateValidator> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="86333-190">To create your own custom validator, you must inherit from the abstract <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="86333-191">Daha fazla bilgi için bkz: [nasıl yapılır: özel bir sertifika Doğrulayıcı kullanan bir hizmet oluşturma](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span><span class="sxs-lookup"><span data-stu-id="86333-191">For more information, see [How to: Create a Service that Employs a Custom Certificate Validator](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="86333-192">Örnek</span><span class="sxs-lookup"><span data-stu-id="86333-192">Example</span></span>  
 <span data-ttu-id="86333-193">Aşağıdaki kod bir X.509 sertifikası ve bir özel doğrulama türü belirtir `<authentication>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="86333-193">The following code specifies an X.509 certificate and a custom validation type in the `<authentication>` element.</span></span>  
  
```xml  
<serviceBehaviors>  
 <behavior name="myServiceBehavior">  
  <clientCertificate>  
   <certificate   
         findValue="www.cohowinery.com"   
         storeLocation="CurrentUser"   
         storeName="TrustedPeople"  
         x509FindType="FindByIssuerName" />  
   <authentication customCertificateValidatorType="MyTypes.Coho"  
    certificateValidationMode="Custom"   
    revocationMode="Offline"  
    includeWindowsGroups="false"   
    mapClientCertificateToWindowsAccount="true" />  
  </clientCertificate>  
 </behavior>  
</serviceBehaviors>  
```  
  
## <a name="see-also"></a><span data-ttu-id="86333-194">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="86333-194">See Also</span></span>  
 <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication>  
 <xref:System.ServiceModel.Security.X509CertificateValidationMode>  
 <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.Authentication%2A>  
 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement.Authentication%2A>  
 <xref:System.ServiceModel.Configuration.X509ClientCertificateAuthenticationElement>  
 [<span data-ttu-id="86333-195">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="86333-195">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="86333-196">Nasıl yapılır: Özel Bir Sertifika Doğrulayıcı Kullanan Bir Hizmet Oluşturma</span><span class="sxs-lookup"><span data-stu-id="86333-196">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)  
 [<span data-ttu-id="86333-197">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="86333-197">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
