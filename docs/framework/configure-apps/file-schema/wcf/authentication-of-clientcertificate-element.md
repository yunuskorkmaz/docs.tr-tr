---
title: "&lt;clientCertificate&gt; Öğesi &lt;kimlik doğrulama&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4a55eea2-1826-4026-b911-b7cc9e9c8bfe
caps.latest.revision: "16"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4eb125727d68d1618b32d21612ecfac28eaa5b6b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltauthenticationgt-of-ltclientcertificategt-element"></a><span data-ttu-id="23ad0-102">&lt;clientCertificate&gt; Öğesi &lt;kimlik doğrulama&gt;</span><span class="sxs-lookup"><span data-stu-id="23ad0-102">&lt;authentication&gt; of &lt;clientCertificate&gt; Element</span></span>
<span data-ttu-id="23ad0-103">Bir hizmeti tarafından kullanılan istemci sertifikaları için kimlik doğrulama davranışları belirtir.</span><span class="sxs-lookup"><span data-stu-id="23ad0-103">Specifies authentication behaviors for client certificates used by a service.</span></span>  
  
 <span data-ttu-id="23ad0-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="23ad0-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="23ad0-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="23ad0-105">\<behaviors></span></span>  
<span data-ttu-id="23ad0-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="23ad0-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="23ad0-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="23ad0-107">\<behavior></span></span>  
<span data-ttu-id="23ad0-108">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="23ad0-108">\<serviceCredentials></span></span>  
<span data-ttu-id="23ad0-109">\<clientCertificate ></span><span class="sxs-lookup"><span data-stu-id="23ad0-109">\<clientCertificate></span></span>  
<span data-ttu-id="23ad0-110">\<kimlik doğrulama ></span><span class="sxs-lookup"><span data-stu-id="23ad0-110">\<authentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23ad0-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="23ad0-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="23ad0-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="23ad0-112">Attributes and Elements</span></span>  
 <span data-ttu-id="23ad0-113">Öznitelikler, alt öğelerini ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır</span><span class="sxs-lookup"><span data-stu-id="23ad0-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="23ad0-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="23ad0-114">Attributes</span></span>  
  
|<span data-ttu-id="23ad0-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="23ad0-115">Attribute</span></span>|<span data-ttu-id="23ad0-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="23ad0-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="23ad0-117">customCertificateValidatorType</span><span class="sxs-lookup"><span data-stu-id="23ad0-117">customCertificateValidatorType</span></span>|<span data-ttu-id="23ad0-118">İsteğe bağlı dize.</span><span class="sxs-lookup"><span data-stu-id="23ad0-118">Optional string.</span></span> <span data-ttu-id="23ad0-119">Tür ve bir özel tür doğrulamak için kullanılan derleme.</span><span class="sxs-lookup"><span data-stu-id="23ad0-119">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="23ad0-120">Bu öznitelik ne zaman ayarlanmalıdır `certificateValidationMode` ayarlanır `Custom`.</span><span class="sxs-lookup"><span data-stu-id="23ad0-120">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|<span data-ttu-id="23ad0-121">certificateValidationMode değerini</span><span class="sxs-lookup"><span data-stu-id="23ad0-121">certificateValidationMode</span></span>|<span data-ttu-id="23ad0-122">İsteğe bağlı numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="23ad0-122">Optional enumeration.</span></span> <span data-ttu-id="23ad0-123">Kimlik bilgilerini doğrulamak için kullanılan modlarından birini belirtir.</span><span class="sxs-lookup"><span data-stu-id="23ad0-123">Specifies one of the modes used to validate credentials.</span></span> <span data-ttu-id="23ad0-124">Bu özniteliktir <xref:System.ServiceModel.Security.X509CertificateValidationMode> türü.</span><span class="sxs-lookup"><span data-stu-id="23ad0-124">This attribute is of the <xref:System.ServiceModel.Security.X509CertificateValidationMode> type.</span></span> <span data-ttu-id="23ad0-125">Varsa kümesine <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom?displayProperty=nameWithType>, sonra bir `customCertificateValidator` de sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="23ad0-125">If set to <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom?displayProperty=nameWithType>, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="23ad0-126">Varsayılan, <xref:System.ServiceModel.Security.X509CertificateValidationMode.ChainTrust?displayProperty=nameWithType> değeridir.</span><span class="sxs-lookup"><span data-stu-id="23ad0-126">The default is <xref:System.ServiceModel.Security.X509CertificateValidationMode.ChainTrust?displayProperty=nameWithType>.</span></span>|  
|<span data-ttu-id="23ad0-127">includeWindowsGroups</span><span class="sxs-lookup"><span data-stu-id="23ad0-127">includeWindowsGroups</span></span>|<span data-ttu-id="23ad0-128">İsteğe bağlı Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="23ad0-128">Optional Boolean.</span></span> <span data-ttu-id="23ad0-129">Windows grupları güvenlik bağlamında dahil edilip edilmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="23ad0-129">Specifies if Windows groups are included in the security context.</span></span> <span data-ttu-id="23ad0-130">Bu öznitelik ayarını `true` bir tam Grup genişletme sonuçları gibi bir performans etkisi olur.</span><span class="sxs-lookup"><span data-stu-id="23ad0-130">Setting this attribute to `true` has a performance impact, as it results in a full group expansion.</span></span> <span data-ttu-id="23ad0-131">Bu öznitelik ayarlanırsa `false` gruplarının listesini oluşturmak ihtiyacınız yoksa bir kullanıcının ait olduğu.</span><span class="sxs-lookup"><span data-stu-id="23ad0-131">Set this attribute to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|<span data-ttu-id="23ad0-132">mapClientCertificateToWindowsAcccount</span><span class="sxs-lookup"><span data-stu-id="23ad0-132">mapClientCertificateToWindowsAcccount</span></span>|<span data-ttu-id="23ad0-133">Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="23ad0-133">Boolean.</span></span> <span data-ttu-id="23ad0-134">İstemci sertifikası kullanılarak bir Windows kimliğine eşlenen olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="23ad0-134">Specifies whether the client can be mapped to a Windows identity using the certificate.</span></span> <span data-ttu-id="23ad0-135">Bunu yapmak için Active Directory etkinleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="23ad0-135">Active Directory must be enabled to do this.</span></span>|  
|<span data-ttu-id="23ad0-136">revocationMode</span><span class="sxs-lookup"><span data-stu-id="23ad0-136">revocationMode</span></span>|<span data-ttu-id="23ad0-137">İsteğe bağlı numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="23ad0-137">Optional enumeration.</span></span> <span data-ttu-id="23ad0-138">İptal edilen sertifika (RCL) listeler denetlemek için kullanılan modlarından birini.</span><span class="sxs-lookup"><span data-stu-id="23ad0-138">One of the modes used to check for a revoked certificate lists (RCL).</span></span> <span data-ttu-id="23ad0-139">Varsayılan, `Online` değeridir.</span><span class="sxs-lookup"><span data-stu-id="23ad0-139">The default is `Online`.</span></span> <span data-ttu-id="23ad0-140">Bu değer, HTTP taşıma güvenliği kullanırken dikkate alınmaz.</span><span class="sxs-lookup"><span data-stu-id="23ad0-140">This value is ignored when using HTTP transport security.</span></span>|  
|<span data-ttu-id="23ad0-141">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="23ad0-141">trustedStoreLocation</span></span>|<span data-ttu-id="23ad0-142">İsteğe bağlı numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="23ad0-142">Optional enumeration.</span></span> <span data-ttu-id="23ad0-143">İki sistem deposu konumlardan birini: `LocalMachine` veya `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="23ad0-143">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="23ad0-144">Bu değer, bir hizmet sertifikası istemciye anlaşıldığında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="23ad0-144">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="23ad0-145">Doğrulama işlemi gerçekleştirildiğinde karşı **güvenilir kişiler** belirtilen depo konumda saklayın.</span><span class="sxs-lookup"><span data-stu-id="23ad0-145">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="23ad0-146">Varsayılan, `CurrentUser` değeridir.</span><span class="sxs-lookup"><span data-stu-id="23ad0-146">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="23ad0-147">customCertificateValidatorType özniteliği</span><span class="sxs-lookup"><span data-stu-id="23ad0-147">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="23ad0-148">Değer</span><span class="sxs-lookup"><span data-stu-id="23ad0-148">Value</span></span>|<span data-ttu-id="23ad0-149">Açıklama</span><span class="sxs-lookup"><span data-stu-id="23ad0-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="23ad0-150">Dize</span><span class="sxs-lookup"><span data-stu-id="23ad0-150">String</span></span>|<span data-ttu-id="23ad0-151">Tür adı ve derleme ve diğer veri türü bulmak için kullanılan belirtir.</span><span class="sxs-lookup"><span data-stu-id="23ad0-151">Specifies the type name and assembly and other data used to find the type.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="23ad0-152">certificateValidationMode değerini özniteliği</span><span class="sxs-lookup"><span data-stu-id="23ad0-152">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="23ad0-153">Değer</span><span class="sxs-lookup"><span data-stu-id="23ad0-153">Value</span></span>|<span data-ttu-id="23ad0-154">Açıklama</span><span class="sxs-lookup"><span data-stu-id="23ad0-154">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="23ad0-155">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="23ad0-155">Enumeration</span></span>|<span data-ttu-id="23ad0-156">Aşağıdaki değerlerden biri: None, PeerTrust, ChainTrust, PeerOrChainTrust, özel.</span><span class="sxs-lookup"><span data-stu-id="23ad0-156">One of the following values: None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.</span></span><br /><br /> <span data-ttu-id="23ad0-157">Daha fazla bilgi için bkz: [sertifikalarla çalışma](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="23ad0-157">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="23ad0-158">revocationMode özniteliği</span><span class="sxs-lookup"><span data-stu-id="23ad0-158">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="23ad0-159">Değer</span><span class="sxs-lookup"><span data-stu-id="23ad0-159">Value</span></span>|<span data-ttu-id="23ad0-160">Açıklama</span><span class="sxs-lookup"><span data-stu-id="23ad0-160">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="23ad0-161">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="23ad0-161">Enumeration</span></span>|<span data-ttu-id="23ad0-162">Aşağıdaki değerlerden birini: NoCheck, çevrimiçi, çevrimdışı.</span><span class="sxs-lookup"><span data-stu-id="23ad0-162">One of the following values: NoCheck, Online, Offline.</span></span> <span data-ttu-id="23ad0-163">Daha fazla bilgi için bkz: [sertifikalarla çalışma](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="23ad0-163">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="23ad0-164">trustedStoreLocation özniteliği</span><span class="sxs-lookup"><span data-stu-id="23ad0-164">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="23ad0-165">Değer</span><span class="sxs-lookup"><span data-stu-id="23ad0-165">Value</span></span>|<span data-ttu-id="23ad0-166">Açıklama</span><span class="sxs-lookup"><span data-stu-id="23ad0-166">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="23ad0-167">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="23ad0-167">Enumeration</span></span>|<span data-ttu-id="23ad0-168">Aşağıdaki değerlerden birini: `LocalMachine` veya `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="23ad0-168">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="23ad0-169">Varsayılan, `CurrentUser` değeridir.</span><span class="sxs-lookup"><span data-stu-id="23ad0-169">The default is `CurrentUser`.</span></span> <span data-ttu-id="23ad0-170">İstemci uygulaması bir sistem hesabı altında çalışan sonra sertifika genellikle altında olduğu `LocalMachine`.</span><span class="sxs-lookup"><span data-stu-id="23ad0-170">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="23ad0-171">İstemci uygulama bir kullanıcı hesabı altında çalışan sonra sertifikayı genellikle kullanımda `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="23ad0-171">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="23ad0-172">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="23ad0-172">Child Elements</span></span>  
 <span data-ttu-id="23ad0-173">Yok.</span><span class="sxs-lookup"><span data-stu-id="23ad0-173">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="23ad0-174">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="23ad0-174">Parent Elements</span></span>  
  
|<span data-ttu-id="23ad0-175">Öğe</span><span class="sxs-lookup"><span data-stu-id="23ad0-175">Element</span></span>|<span data-ttu-id="23ad0-176">Açıklama</span><span class="sxs-lookup"><span data-stu-id="23ad0-176">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="23ad0-177">\<clientCertificate ></span><span class="sxs-lookup"><span data-stu-id="23ad0-177">\<clientCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)|<span data-ttu-id="23ad0-178">Bir hizmet için bir istemci kimlik doğrulaması için kullanılan bir X.509 sertifikası tanımlar.</span><span class="sxs-lookup"><span data-stu-id="23ad0-178">Defines an X.509 certificate used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="23ad0-179">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="23ad0-179">Remarks</span></span>  
 <span data-ttu-id="23ad0-180">`<authentication>` Öğesi karşılık gelen <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="23ad0-180">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> class.</span></span> <span data-ttu-id="23ad0-181">İstemcilerin nasıl doğrulanır özelleştirmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="23ad0-181">It enables you to customize how clients are authenticated.</span></span> <span data-ttu-id="23ad0-182">Ayarlayabileceğiniz `certificateValidationMode` özniteliğini `None`, `ChainTrust`, `PeerOrChainTrust`, `PeerTrust`, veya `Custom`.</span><span class="sxs-lookup"><span data-stu-id="23ad0-182">You can set the `certificateValidationMode` attribute to `None`, `ChainTrust`, `PeerOrChainTrust`, `PeerTrust`, or `Custom`.</span></span> <span data-ttu-id="23ad0-183">Varsayılan olarak, düzeyini ayarlamak `ChainTrust`, belirten her sertifika biten sertifika hiyerarşisini bulunması gereken bir *kök yetkilisi* zincirinin üstünde.</span><span class="sxs-lookup"><span data-stu-id="23ad0-183">By default, the level is set to `ChainTrust`, which specifies that each certificate must be found in a hierarchy of certificates ending in a *root authority* at the top of the chain.</span></span> <span data-ttu-id="23ad0-184">Bu en güvenli bir moddur.</span><span class="sxs-lookup"><span data-stu-id="23ad0-184">This is the most secure mode.</span></span> <span data-ttu-id="23ad0-185">De değer ayarlayabilirsiniz `PeerOrChainTrust`, kendi kendine verilen sertifikaların (eş güven) güvenilen zincirinde sertifikaları yanı sıra kabul edileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="23ad0-185">You can also set the value to `PeerOrChainTrust`, which specifies that self-issued certificates (peer trust) are accepted as well as certificates that are in a trusted chain.</span></span> <span data-ttu-id="23ad0-186">Bu değer, geliştirme ve kendi kendine verilen sertifikaların güvenilir bir yetkiliden satın alınması değil çünkü hata ayıklama istemcileri ve Hizmetleri zaman kullanılır.</span><span class="sxs-lookup"><span data-stu-id="23ad0-186">This value is used when developing and debugging clients and services because self-issued certificates need not be purchased from a trusted authority.</span></span> <span data-ttu-id="23ad0-187">Bir istemci dağıtımı sırasında kullanmak `ChainTrust` yerine değer.</span><span class="sxs-lookup"><span data-stu-id="23ad0-187">When deploying a client, use the `ChainTrust` value instead.</span></span>  
  
 <span data-ttu-id="23ad0-188">De değer ayarlayabilirsiniz `Custom`.</span><span class="sxs-lookup"><span data-stu-id="23ad0-188">You can also set the value to `Custom`.</span></span> <span data-ttu-id="23ad0-189">Ayarlandığında `Custom` değeri de ayarlamanız gerekir `customCertificateValidatorType` özniteliği bir derleme ve sertifikayı doğrulamak için kullanılan türü.</span><span class="sxs-lookup"><span data-stu-id="23ad0-189">When set to the `Custom` value, you must also set the `customCertificateValidatorType` attribute to an assembly and type used to validate the certificate.</span></span> <span data-ttu-id="23ad0-190">Kendi özel Doğrulayıcısı oluşturmak için Özet devralmalıdır <xref:System.IdentityModel.Selectors.X509CertificateValidator> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="23ad0-190">To create your own custom validator, you must inherit from the abstract <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="23ad0-191">Daha fazla bilgi için bkz: [nasıl yapılır: özel bir sertifika Doğrulayıcı kullanan bir hizmet oluşturma](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span><span class="sxs-lookup"><span data-stu-id="23ad0-191">For more information, see [How to: Create a Service that Employs a Custom Certificate Validator](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="23ad0-192">Örnek</span><span class="sxs-lookup"><span data-stu-id="23ad0-192">Example</span></span>  
 <span data-ttu-id="23ad0-193">Aşağıdaki kod bir X.509 sertifikası ve bir özel doğrulama türü belirtir `<authentication>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="23ad0-193">The following code specifies an X.509 certificate and a custom validation type in the `<authentication>` element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="23ad0-194">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="23ad0-194">See Also</span></span>  
 <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication>  
 <xref:System.ServiceModel.Security.X509CertificateValidationMode>  
 <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.Authentication%2A>  
 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement.Authentication%2A>  
 <xref:System.ServiceModel.Configuration.X509ClientCertificateAuthenticationElement>  
 [<span data-ttu-id="23ad0-195">Güvenlik davranışları</span><span class="sxs-lookup"><span data-stu-id="23ad0-195">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="23ad0-196">Nasıl yapılır: özel bir sertifika Doğrulayıcı kullanan bir hizmet oluşturma</span><span class="sxs-lookup"><span data-stu-id="23ad0-196">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)  
 [<span data-ttu-id="23ad0-197">Sertifikalar ile çalışma</span><span class="sxs-lookup"><span data-stu-id="23ad0-197">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
