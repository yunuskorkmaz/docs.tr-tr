---
title: <authentication><clientCertificate>öğesinin
ms.date: 03/30/2017
ms.assetid: 4a55eea2-1826-4026-b911-b7cc9e9c8bfe
ms.openlocfilehash: 13296dbc2b3bc8836770197a1549586c841b4635
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201609"
---
# <a name="authentication-of-clientcertificate-element"></a><span data-ttu-id="56316-102">\<authentication>\<clientCertificate>öğesinin</span><span class="sxs-lookup"><span data-stu-id="56316-102">\<authentication> of \<clientCertificate> Element</span></span>

<span data-ttu-id="56316-103">Bir hizmet tarafından kullanılan istemci sertifikaları için kimlik doğrulaması davranışlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="56316-103">Specifies authentication behaviors for client certificates used by a service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCertificate>**](clientcertificate-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<authentication>**  
  
## <a name="syntax"></a><span data-ttu-id="56316-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="56316-104">Syntax</span></span>  
  
```xml  
<authentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                includeWindowsGroups="Boolean"
                mapClientCertificateToWindowsAccount="Boolean"
                revocationMode="NoCheck/Online/Offline"
                trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="56316-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="56316-105">Attributes and Elements</span></span>  

 <span data-ttu-id="56316-106">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="56316-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="56316-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="56316-107">Attributes</span></span>  
  
|<span data-ttu-id="56316-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="56316-108">Attribute</span></span>|<span data-ttu-id="56316-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="56316-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="56316-110">Customcercertificate Atevalidatortype</span><span class="sxs-lookup"><span data-stu-id="56316-110">customCertificateValidatorType</span></span>|<span data-ttu-id="56316-111">İsteğe bağlı dize.</span><span class="sxs-lookup"><span data-stu-id="56316-111">Optional string.</span></span> <span data-ttu-id="56316-112">Özel bir türü doğrulamak için kullanılan tür ve derleme.</span><span class="sxs-lookup"><span data-stu-id="56316-112">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="56316-113">Bu öznitelik `certificateValidationMode` , olarak ayarlandığında ayarlanmalıdır `Custom` .</span><span class="sxs-lookup"><span data-stu-id="56316-113">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|<span data-ttu-id="56316-114">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="56316-114">certificateValidationMode</span></span>|<span data-ttu-id="56316-115">İsteğe bağlı sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="56316-115">Optional enumeration.</span></span> <span data-ttu-id="56316-116">Kimlik bilgilerini doğrulamak için kullanılan modlardan birini belirtir.</span><span class="sxs-lookup"><span data-stu-id="56316-116">Specifies one of the modes used to validate credentials.</span></span> <span data-ttu-id="56316-117">Bu öznitelik <xref:System.ServiceModel.Security.X509CertificateValidationMode> türü.</span><span class="sxs-lookup"><span data-stu-id="56316-117">This attribute is of the <xref:System.ServiceModel.Security.X509CertificateValidationMode> type.</span></span> <span data-ttu-id="56316-118">Olarak ayarlanırsa <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom?displayProperty=nameWithType> , bir `customCertificateValidator` de sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="56316-118">If set to <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom?displayProperty=nameWithType>, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="56316-119">Varsayılan değer: <xref:System.ServiceModel.Security.X509CertificateValidationMode.ChainTrust?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="56316-119">The default is <xref:System.ServiceModel.Security.X509CertificateValidationMode.ChainTrust?displayProperty=nameWithType>.</span></span>|  
|<span data-ttu-id="56316-120">IncludeWindowsGroups</span><span class="sxs-lookup"><span data-stu-id="56316-120">includeWindowsGroups</span></span>|<span data-ttu-id="56316-121">İsteğe bağlı Boolean.</span><span class="sxs-lookup"><span data-stu-id="56316-121">Optional Boolean.</span></span> <span data-ttu-id="56316-122">Windows gruplarının güvenlik bağlamına dahil edilip edilmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="56316-122">Specifies if Windows groups are included in the security context.</span></span> <span data-ttu-id="56316-123">Bu özniteliğin olarak ayarlanması `true` , tam grup genişlemesiyle sonuçlandığından performans etkisine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="56316-123">Setting this attribute to `true` has a performance impact, as it results in a full group expansion.</span></span> <span data-ttu-id="56316-124">`false`Bir kullanıcının ait olduğu grupların listesini oluşturmanız gerekmiyorsa, bu özniteliği olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="56316-124">Set this attribute to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|<span data-ttu-id="56316-125">mapClientCertificateToWindowsAccount</span><span class="sxs-lookup"><span data-stu-id="56316-125">mapClientCertificateToWindowsAccount</span></span>|<span data-ttu-id="56316-126">Boolean.</span><span class="sxs-lookup"><span data-stu-id="56316-126">Boolean.</span></span> <span data-ttu-id="56316-127">İstemcinin sertifikayı kullanarak bir Windows kimliğiyle eşleştirilip eşlenmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="56316-127">Specifies whether the client can be mapped to a Windows identity using the certificate.</span></span> <span data-ttu-id="56316-128">Bunu yapmak için Active Directory etkinleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="56316-128">Active Directory must be enabled to do this.</span></span>|  
|<span data-ttu-id="56316-129">Revocationmodu</span><span class="sxs-lookup"><span data-stu-id="56316-129">revocationMode</span></span>|<span data-ttu-id="56316-130">İsteğe bağlı sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="56316-130">Optional enumeration.</span></span> <span data-ttu-id="56316-131">İptal edilen sertifika listelerini (RCL) denetlemek için kullanılan modlardan biri.</span><span class="sxs-lookup"><span data-stu-id="56316-131">One of the modes used to check for a revoked certificate lists (RCL).</span></span> <span data-ttu-id="56316-132">Varsayılan değer: `Online`.</span><span class="sxs-lookup"><span data-stu-id="56316-132">The default is `Online`.</span></span> <span data-ttu-id="56316-133">HTTP taşıma güvenliği kullanılırken bu değer yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="56316-133">This value is ignored when using HTTP transport security.</span></span>|  
|<span data-ttu-id="56316-134">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="56316-134">trustedStoreLocation</span></span>|<span data-ttu-id="56316-135">İsteğe bağlı sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="56316-135">Optional enumeration.</span></span> <span data-ttu-id="56316-136">İki sistem depolama konumlarından biri: `LocalMachine` veya `CurrentUser` .</span><span class="sxs-lookup"><span data-stu-id="56316-136">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="56316-137">Bu değer, bir hizmet sertifikası istemciye anlaşılırken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="56316-137">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="56316-138">Doğrulama, belirtilen depo konumundaki **güvenilir kişiler** deposuna göre gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="56316-138">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="56316-139">Varsayılan değer: `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="56316-139">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="56316-140">Customcercertificate Atevalidatortype özniteliği</span><span class="sxs-lookup"><span data-stu-id="56316-140">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="56316-141">Değer</span><span class="sxs-lookup"><span data-stu-id="56316-141">Value</span></span>|<span data-ttu-id="56316-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="56316-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="56316-143">Dize</span><span class="sxs-lookup"><span data-stu-id="56316-143">String</span></span>|<span data-ttu-id="56316-144">Türü bulmak için kullanılan tür adını ve derlemeyi ve diğer verileri belirtir.</span><span class="sxs-lookup"><span data-stu-id="56316-144">Specifies the type name and assembly and other data used to find the type.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="56316-145">certificateValidationMode özniteliği</span><span class="sxs-lookup"><span data-stu-id="56316-145">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="56316-146">Değer</span><span class="sxs-lookup"><span data-stu-id="56316-146">Value</span></span>|<span data-ttu-id="56316-147">Açıklama</span><span class="sxs-lookup"><span data-stu-id="56316-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="56316-148">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="56316-148">Enumeration</span></span>|<span data-ttu-id="56316-149">Şu değerlerden biri: None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.</span><span class="sxs-lookup"><span data-stu-id="56316-149">One of the following values: None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.</span></span><br /><br /> <span data-ttu-id="56316-150">Daha fazla bilgi için bkz. [sertifikalarla çalışma](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="56316-150">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="56316-151">revocationMode özniteliği</span><span class="sxs-lookup"><span data-stu-id="56316-151">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="56316-152">Değer</span><span class="sxs-lookup"><span data-stu-id="56316-152">Value</span></span>|<span data-ttu-id="56316-153">Açıklama</span><span class="sxs-lookup"><span data-stu-id="56316-153">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="56316-154">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="56316-154">Enumeration</span></span>|<span data-ttu-id="56316-155">Şu değerlerden biri: NoCheck, çevrimiçi, çevrimdışı.</span><span class="sxs-lookup"><span data-stu-id="56316-155">One of the following values: NoCheck, Online, Offline.</span></span> <span data-ttu-id="56316-156">Daha fazla bilgi için bkz. [sertifikalarla çalışma](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="56316-156">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="56316-157">trustedStoreLocation özniteliği</span><span class="sxs-lookup"><span data-stu-id="56316-157">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="56316-158">Değer</span><span class="sxs-lookup"><span data-stu-id="56316-158">Value</span></span>|<span data-ttu-id="56316-159">Açıklama</span><span class="sxs-lookup"><span data-stu-id="56316-159">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="56316-160">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="56316-160">Enumeration</span></span>|<span data-ttu-id="56316-161">Şu değerlerden biri: `LocalMachine` veya `CurrentUser` .</span><span class="sxs-lookup"><span data-stu-id="56316-161">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="56316-162">Varsayılan değer: `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="56316-162">The default is `CurrentUser`.</span></span> <span data-ttu-id="56316-163">İstemci uygulaması bir sistem hesabı altında çalışıyorsa, sertifika genellikle altında olur `LocalMachine` .</span><span class="sxs-lookup"><span data-stu-id="56316-163">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="56316-164">İstemci uygulaması bir kullanıcı hesabı altında çalışıyorsa, sertifika genellikle içinde olur `CurrentUser` .</span><span class="sxs-lookup"><span data-stu-id="56316-164">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="56316-165">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="56316-165">Child Elements</span></span>  

 <span data-ttu-id="56316-166">Yok.</span><span class="sxs-lookup"><span data-stu-id="56316-166">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="56316-167">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="56316-167">Parent Elements</span></span>  
  
|<span data-ttu-id="56316-168">Öğe</span><span class="sxs-lookup"><span data-stu-id="56316-168">Element</span></span>|<span data-ttu-id="56316-169">Açıklama</span><span class="sxs-lookup"><span data-stu-id="56316-169">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCertificate>](clientcertificate-of-servicecredentials.md)|<span data-ttu-id="56316-170">Bir hizmette istemcinin kimliğini doğrulamak için kullanılan bir X. 509.440 sertifikası tanımlar.</span><span class="sxs-lookup"><span data-stu-id="56316-170">Defines an X.509 certificate used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="56316-171">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="56316-171">Remarks</span></span>  

 <span data-ttu-id="56316-172">`<authentication>`Öğesi sınıfına karşılık gelir <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> .</span><span class="sxs-lookup"><span data-stu-id="56316-172">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> class.</span></span> <span data-ttu-id="56316-173">İstemcilerin nasıl doğrulandığını özelleştirmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="56316-173">It enables you to customize how clients are authenticated.</span></span> <span data-ttu-id="56316-174">Özniteliğini,,, `certificateValidationMode` veya olarak `None` ayarlayabilirsiniz `ChainTrust` `PeerOrChainTrust` `PeerTrust` `Custom` .</span><span class="sxs-lookup"><span data-stu-id="56316-174">You can set the `certificateValidationMode` attribute to `None`, `ChainTrust`, `PeerOrChainTrust`, `PeerTrust`, or `Custom`.</span></span> <span data-ttu-id="56316-175">Varsayılan olarak, düzeyi olarak ayarlanır `ChainTrust` ; Bu, her bir sertifikanın, zincirinin en üstündeki bir *kök yetkilide* sonlanan sertifikaların hiyerarşisinde bulunması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="56316-175">By default, the level is set to `ChainTrust`, which specifies that each certificate must be found in a hierarchy of certificates ending in a *root authority* at the top of the chain.</span></span> <span data-ttu-id="56316-176">En güvenli mod budur.</span><span class="sxs-lookup"><span data-stu-id="56316-176">This is the most secure mode.</span></span> <span data-ttu-id="56316-177">Ayrıca, `PeerOrChainTrust` otomatik olarak verilen sertifikaların (eş güven) kabul edildiğini ve güvenilen bir zincirdeki sertifikaların kabul edildiğini belirten değerini olarak da ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="56316-177">You can also set the value to `PeerOrChainTrust`, which specifies that self-issued certificates (peer trust) are accepted as well as certificates that are in a trusted chain.</span></span> <span data-ttu-id="56316-178">Bu değer, istemci ve Hizmetleri geliştirirken ve hata ayıkladığında kullanılır çünkü kendinden verilen sertifikaların güvenilir bir yetkilinizden satın alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="56316-178">This value is used when developing and debugging clients and services because self-issued certificates need not be purchased from a trusted authority.</span></span> <span data-ttu-id="56316-179">Bir istemciyi dağıttığınızda, `ChainTrust` bunun yerine değeri kullanın.</span><span class="sxs-lookup"><span data-stu-id="56316-179">When deploying a client, use the `ChainTrust` value instead.</span></span>  
  
 <span data-ttu-id="56316-180">Değerini olarak da ayarlayabilirsiniz `Custom` .</span><span class="sxs-lookup"><span data-stu-id="56316-180">You can also set the value to `Custom`.</span></span> <span data-ttu-id="56316-181">`Custom`Değere ayarlandığında, `customCertificateValidatorType` bir derlemeyi ve sertifikayı doğrulamak için kullanılan türünü de ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="56316-181">When set to the `Custom` value, you must also set the `customCertificateValidatorType` attribute to an assembly and type used to validate the certificate.</span></span> <span data-ttu-id="56316-182">Kendi özel Doğrulayıcısı oluşturmak için soyut sınıftan devralması gerekir <xref:System.IdentityModel.Selectors.X509CertificateValidator> .</span><span class="sxs-lookup"><span data-stu-id="56316-182">To create your own custom validator, you must inherit from the abstract <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="56316-183">Daha fazla bilgi için bkz. [nasıl yapılır: özel bir sertifika Doğrulayıcı kullanan bir hizmet oluşturma](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span><span class="sxs-lookup"><span data-stu-id="56316-183">For more information, see [How to: Create a Service that Employs a Custom Certificate Validator](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="56316-184">Örnek</span><span class="sxs-lookup"><span data-stu-id="56316-184">Example</span></span>  

 <span data-ttu-id="56316-185">Aşağıdaki kod, öğesinde bir X. 509.952 sertifikası ve özel bir doğrulama türü belirtir `<authentication>` .</span><span class="sxs-lookup"><span data-stu-id="56316-185">The following code specifies an X.509 certificate and a custom validation type in the `<authentication>` element.</span></span>  
  
```xml  
<serviceBehaviors>
  <behavior name="myServiceBehavior">
    <clientCertificate>
      <certificate findValue="www.cohowinery.com"
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
  
## <a name="see-also"></a><span data-ttu-id="56316-186">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="56316-186">See also</span></span>

- <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication>
- <xref:System.ServiceModel.Security.X509CertificateValidationMode>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.Authentication%2A>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement.Authentication%2A>
- <xref:System.ServiceModel.Configuration.X509ClientCertificateAuthenticationElement>
- [<span data-ttu-id="56316-187">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="56316-187">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="56316-188">Nasıl yapılır: Özel Bir Sertifika Doğrulayıcı Kullanan Bir Hizmet Oluşturma</span><span class="sxs-lookup"><span data-stu-id="56316-188">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)
- [<span data-ttu-id="56316-189">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="56316-189">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
