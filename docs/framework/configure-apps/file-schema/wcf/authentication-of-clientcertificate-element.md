---
description: 'Hakkında daha fazla bilgi edinin: <authentication> <clientCertificate> öğe'
title: <authentication><clientCertificate>öğesinin
ms.date: 03/30/2017
ms.assetid: 4a55eea2-1826-4026-b911-b7cc9e9c8bfe
ms.openlocfilehash: 346e1012fd9d799b093be15381aebbc026ea2591
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749902"
---
# <a name="authentication-of-clientcertificate-element"></a><span data-ttu-id="e31db-103">\<authentication>\<clientCertificate>öğesinin</span><span class="sxs-lookup"><span data-stu-id="e31db-103">\<authentication> of \<clientCertificate> Element</span></span>

<span data-ttu-id="e31db-104">Bir hizmet tarafından kullanılan istemci sertifikaları için kimlik doğrulaması davranışlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e31db-104">Specifies authentication behaviors for client certificates used by a service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCertificate>**](clientcertificate-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<authentication>**  
  
## <a name="syntax"></a><span data-ttu-id="e31db-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="e31db-105">Syntax</span></span>  
  
```xml  
<authentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                includeWindowsGroups="Boolean"
                mapClientCertificateToWindowsAccount="Boolean"
                revocationMode="NoCheck/Online/Offline"
                trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e31db-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e31db-106">Attributes and Elements</span></span>  

 <span data-ttu-id="e31db-107">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="e31db-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e31db-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e31db-108">Attributes</span></span>  
  
|<span data-ttu-id="e31db-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e31db-109">Attribute</span></span>|<span data-ttu-id="e31db-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e31db-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e31db-111">Customcercertificate Atevalidatortype</span><span class="sxs-lookup"><span data-stu-id="e31db-111">customCertificateValidatorType</span></span>|<span data-ttu-id="e31db-112">İsteğe bağlı dize.</span><span class="sxs-lookup"><span data-stu-id="e31db-112">Optional string.</span></span> <span data-ttu-id="e31db-113">Özel bir türü doğrulamak için kullanılan tür ve derleme.</span><span class="sxs-lookup"><span data-stu-id="e31db-113">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="e31db-114">Bu öznitelik `certificateValidationMode` , olarak ayarlandığında ayarlanmalıdır `Custom` .</span><span class="sxs-lookup"><span data-stu-id="e31db-114">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|<span data-ttu-id="e31db-115">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="e31db-115">certificateValidationMode</span></span>|<span data-ttu-id="e31db-116">İsteğe bağlı sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="e31db-116">Optional enumeration.</span></span> <span data-ttu-id="e31db-117">Kimlik bilgilerini doğrulamak için kullanılan modlardan birini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e31db-117">Specifies one of the modes used to validate credentials.</span></span> <span data-ttu-id="e31db-118">Bu öznitelik <xref:System.ServiceModel.Security.X509CertificateValidationMode> türü.</span><span class="sxs-lookup"><span data-stu-id="e31db-118">This attribute is of the <xref:System.ServiceModel.Security.X509CertificateValidationMode> type.</span></span> <span data-ttu-id="e31db-119">Olarak ayarlanırsa <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom?displayProperty=nameWithType> , bir `customCertificateValidator` de sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e31db-119">If set to <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom?displayProperty=nameWithType>, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="e31db-120">Varsayılan değer: <xref:System.ServiceModel.Security.X509CertificateValidationMode.ChainTrust?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e31db-120">The default is <xref:System.ServiceModel.Security.X509CertificateValidationMode.ChainTrust?displayProperty=nameWithType>.</span></span>|  
|<span data-ttu-id="e31db-121">IncludeWindowsGroups</span><span class="sxs-lookup"><span data-stu-id="e31db-121">includeWindowsGroups</span></span>|<span data-ttu-id="e31db-122">İsteğe bağlı Boolean.</span><span class="sxs-lookup"><span data-stu-id="e31db-122">Optional Boolean.</span></span> <span data-ttu-id="e31db-123">Windows gruplarının güvenlik bağlamına dahil edilip edilmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e31db-123">Specifies if Windows groups are included in the security context.</span></span> <span data-ttu-id="e31db-124">Bu özniteliğin olarak ayarlanması `true` , tam grup genişlemesiyle sonuçlandığından performans etkisine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="e31db-124">Setting this attribute to `true` has a performance impact, as it results in a full group expansion.</span></span> <span data-ttu-id="e31db-125">`false`Bir kullanıcının ait olduğu grupların listesini oluşturmanız gerekmiyorsa, bu özniteliği olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e31db-125">Set this attribute to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|<span data-ttu-id="e31db-126">mapClientCertificateToWindowsAccount</span><span class="sxs-lookup"><span data-stu-id="e31db-126">mapClientCertificateToWindowsAccount</span></span>|<span data-ttu-id="e31db-127">Boolean.</span><span class="sxs-lookup"><span data-stu-id="e31db-127">Boolean.</span></span> <span data-ttu-id="e31db-128">İstemcinin sertifikayı kullanarak bir Windows kimliğiyle eşleştirilip eşlenmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e31db-128">Specifies whether the client can be mapped to a Windows identity using the certificate.</span></span> <span data-ttu-id="e31db-129">Bunu yapmak için Active Directory etkinleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="e31db-129">Active Directory must be enabled to do this.</span></span>|  
|<span data-ttu-id="e31db-130">Revocationmodu</span><span class="sxs-lookup"><span data-stu-id="e31db-130">revocationMode</span></span>|<span data-ttu-id="e31db-131">İsteğe bağlı sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="e31db-131">Optional enumeration.</span></span> <span data-ttu-id="e31db-132">İptal edilen sertifika listelerini (RCL) denetlemek için kullanılan modlardan biri.</span><span class="sxs-lookup"><span data-stu-id="e31db-132">One of the modes used to check for a revoked certificate lists (RCL).</span></span> <span data-ttu-id="e31db-133">Varsayılan değer: `Online`.</span><span class="sxs-lookup"><span data-stu-id="e31db-133">The default is `Online`.</span></span> <span data-ttu-id="e31db-134">HTTP taşıma güvenliği kullanılırken bu değer yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="e31db-134">This value is ignored when using HTTP transport security.</span></span>|  
|<span data-ttu-id="e31db-135">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="e31db-135">trustedStoreLocation</span></span>|<span data-ttu-id="e31db-136">İsteğe bağlı sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="e31db-136">Optional enumeration.</span></span> <span data-ttu-id="e31db-137">İki sistem depolama konumlarından biri: `LocalMachine` veya `CurrentUser` .</span><span class="sxs-lookup"><span data-stu-id="e31db-137">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="e31db-138">Bu değer, bir hizmet sertifikası istemciye anlaşılırken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e31db-138">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="e31db-139">Doğrulama, belirtilen depo konumundaki **güvenilir kişiler** deposuna göre gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="e31db-139">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="e31db-140">Varsayılan değer: `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="e31db-140">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="e31db-141">Customcercertificate Atevalidatortype özniteliği</span><span class="sxs-lookup"><span data-stu-id="e31db-141">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="e31db-142">Değer</span><span class="sxs-lookup"><span data-stu-id="e31db-142">Value</span></span>|<span data-ttu-id="e31db-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e31db-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e31db-144">Dize</span><span class="sxs-lookup"><span data-stu-id="e31db-144">String</span></span>|<span data-ttu-id="e31db-145">Türü bulmak için kullanılan tür adını ve derlemeyi ve diğer verileri belirtir.</span><span class="sxs-lookup"><span data-stu-id="e31db-145">Specifies the type name and assembly and other data used to find the type.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="e31db-146">certificateValidationMode özniteliği</span><span class="sxs-lookup"><span data-stu-id="e31db-146">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="e31db-147">Değer</span><span class="sxs-lookup"><span data-stu-id="e31db-147">Value</span></span>|<span data-ttu-id="e31db-148">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e31db-148">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e31db-149">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="e31db-149">Enumeration</span></span>|<span data-ttu-id="e31db-150">Şu değerlerden biri: None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.</span><span class="sxs-lookup"><span data-stu-id="e31db-150">One of the following values: None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.</span></span><br /><br /> <span data-ttu-id="e31db-151">Daha fazla bilgi için bkz. [sertifikalarla çalışma](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="e31db-151">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="e31db-152">revocationMode özniteliği</span><span class="sxs-lookup"><span data-stu-id="e31db-152">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="e31db-153">Değer</span><span class="sxs-lookup"><span data-stu-id="e31db-153">Value</span></span>|<span data-ttu-id="e31db-154">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e31db-154">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e31db-155">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="e31db-155">Enumeration</span></span>|<span data-ttu-id="e31db-156">Şu değerlerden biri: NoCheck, çevrimiçi, çevrimdışı.</span><span class="sxs-lookup"><span data-stu-id="e31db-156">One of the following values: NoCheck, Online, Offline.</span></span> <span data-ttu-id="e31db-157">Daha fazla bilgi için bkz. [sertifikalarla çalışma](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="e31db-157">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="e31db-158">trustedStoreLocation özniteliği</span><span class="sxs-lookup"><span data-stu-id="e31db-158">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="e31db-159">Değer</span><span class="sxs-lookup"><span data-stu-id="e31db-159">Value</span></span>|<span data-ttu-id="e31db-160">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e31db-160">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e31db-161">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="e31db-161">Enumeration</span></span>|<span data-ttu-id="e31db-162">Şu değerlerden biri: `LocalMachine` veya `CurrentUser` .</span><span class="sxs-lookup"><span data-stu-id="e31db-162">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="e31db-163">Varsayılan değer: `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="e31db-163">The default is `CurrentUser`.</span></span> <span data-ttu-id="e31db-164">İstemci uygulaması bir sistem hesabı altında çalışıyorsa, sertifika genellikle altında olur `LocalMachine` .</span><span class="sxs-lookup"><span data-stu-id="e31db-164">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="e31db-165">İstemci uygulaması bir kullanıcı hesabı altında çalışıyorsa, sertifika genellikle içinde olur `CurrentUser` .</span><span class="sxs-lookup"><span data-stu-id="e31db-165">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e31db-166">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e31db-166">Child Elements</span></span>  

 <span data-ttu-id="e31db-167">Yok.</span><span class="sxs-lookup"><span data-stu-id="e31db-167">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e31db-168">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e31db-168">Parent Elements</span></span>  
  
|<span data-ttu-id="e31db-169">Öğe</span><span class="sxs-lookup"><span data-stu-id="e31db-169">Element</span></span>|<span data-ttu-id="e31db-170">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e31db-170">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCertificate>](clientcertificate-of-servicecredentials.md)|<span data-ttu-id="e31db-171">Bir hizmette istemcinin kimliğini doğrulamak için kullanılan bir X. 509.440 sertifikası tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e31db-171">Defines an X.509 certificate used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e31db-172">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e31db-172">Remarks</span></span>  

 <span data-ttu-id="e31db-173">`<authentication>`Öğesi sınıfına karşılık gelir <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> .</span><span class="sxs-lookup"><span data-stu-id="e31db-173">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> class.</span></span> <span data-ttu-id="e31db-174">İstemcilerin nasıl doğrulandığını özelleştirmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="e31db-174">It enables you to customize how clients are authenticated.</span></span> <span data-ttu-id="e31db-175">Özniteliğini,,, `certificateValidationMode` veya olarak `None` ayarlayabilirsiniz `ChainTrust` `PeerOrChainTrust` `PeerTrust` `Custom` .</span><span class="sxs-lookup"><span data-stu-id="e31db-175">You can set the `certificateValidationMode` attribute to `None`, `ChainTrust`, `PeerOrChainTrust`, `PeerTrust`, or `Custom`.</span></span> <span data-ttu-id="e31db-176">Varsayılan olarak, düzeyi olarak ayarlanır `ChainTrust` ; Bu, her bir sertifikanın, zincirinin en üstündeki bir *kök yetkilide* sonlanan sertifikaların hiyerarşisinde bulunması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e31db-176">By default, the level is set to `ChainTrust`, which specifies that each certificate must be found in a hierarchy of certificates ending in a *root authority* at the top of the chain.</span></span> <span data-ttu-id="e31db-177">En güvenli mod budur.</span><span class="sxs-lookup"><span data-stu-id="e31db-177">This is the most secure mode.</span></span> <span data-ttu-id="e31db-178">Ayrıca, `PeerOrChainTrust` otomatik olarak verilen sertifikaların (eş güven) kabul edildiğini ve güvenilen bir zincirdeki sertifikaların kabul edildiğini belirten değerini olarak da ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e31db-178">You can also set the value to `PeerOrChainTrust`, which specifies that self-issued certificates (peer trust) are accepted as well as certificates that are in a trusted chain.</span></span> <span data-ttu-id="e31db-179">Bu değer, istemci ve Hizmetleri geliştirirken ve hata ayıkladığında kullanılır çünkü kendinden verilen sertifikaların güvenilir bir yetkilinizden satın alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e31db-179">This value is used when developing and debugging clients and services because self-issued certificates need not be purchased from a trusted authority.</span></span> <span data-ttu-id="e31db-180">Bir istemciyi dağıttığınızda, `ChainTrust` bunun yerine değeri kullanın.</span><span class="sxs-lookup"><span data-stu-id="e31db-180">When deploying a client, use the `ChainTrust` value instead.</span></span>  
  
 <span data-ttu-id="e31db-181">Değerini olarak da ayarlayabilirsiniz `Custom` .</span><span class="sxs-lookup"><span data-stu-id="e31db-181">You can also set the value to `Custom`.</span></span> <span data-ttu-id="e31db-182">`Custom`Değere ayarlandığında, `customCertificateValidatorType` bir derlemeyi ve sertifikayı doğrulamak için kullanılan türünü de ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e31db-182">When set to the `Custom` value, you must also set the `customCertificateValidatorType` attribute to an assembly and type used to validate the certificate.</span></span> <span data-ttu-id="e31db-183">Kendi özel Doğrulayıcısı oluşturmak için soyut sınıftan devralması gerekir <xref:System.IdentityModel.Selectors.X509CertificateValidator> .</span><span class="sxs-lookup"><span data-stu-id="e31db-183">To create your own custom validator, you must inherit from the abstract <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="e31db-184">Daha fazla bilgi için bkz. [nasıl yapılır: özel bir sertifika Doğrulayıcı kullanan bir hizmet oluşturma](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span><span class="sxs-lookup"><span data-stu-id="e31db-184">For more information, see [How to: Create a Service that Employs a Custom Certificate Validator](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e31db-185">Örnek</span><span class="sxs-lookup"><span data-stu-id="e31db-185">Example</span></span>  

 <span data-ttu-id="e31db-186">Aşağıdaki kod, öğesinde bir X. 509.952 sertifikası ve özel bir doğrulama türü belirtir `<authentication>` .</span><span class="sxs-lookup"><span data-stu-id="e31db-186">The following code specifies an X.509 certificate and a custom validation type in the `<authentication>` element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e31db-187">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e31db-187">See also</span></span>

- <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication>
- <xref:System.ServiceModel.Security.X509CertificateValidationMode>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.Authentication%2A>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement.Authentication%2A>
- <xref:System.ServiceModel.Configuration.X509ClientCertificateAuthenticationElement>
- [<span data-ttu-id="e31db-188">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="e31db-188">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="e31db-189">Nasıl yapılır: Özel Bir Sertifika Doğrulayıcı Kullanan Bir Hizmet Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e31db-189">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)
- [<span data-ttu-id="e31db-190">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="e31db-190">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
