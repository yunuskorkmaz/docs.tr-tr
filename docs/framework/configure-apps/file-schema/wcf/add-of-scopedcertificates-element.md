---
title: "&lt;scopedCertificates&gt; Öğesi &lt;ekleme&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e21c1ef8-d6d6-4bca-ac5a-6fbf4bd77412
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: eff535f7eb779a69c2368f3ad815f1eb124946ff
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-of-ltscopedcertificatesgt-element"></a><span data-ttu-id="c5a6a-102">&lt;scopedCertificates&gt; Öğesi &lt;ekleme&gt;</span><span class="sxs-lookup"><span data-stu-id="c5a6a-102">&lt;add&gt; of &lt;scopedCertificates&gt; Element</span></span>
<span data-ttu-id="c5a6a-103">Bir X.509 sertifikası kapsamlı sertifikaları koleksiyonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="c5a6a-103">Adds an X.509 certificate to the collection of scoped certificates.</span></span>  
  
 <span data-ttu-id="c5a6a-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="c5a6a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="c5a6a-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="c5a6a-105">\<behaviors></span></span>  
<span data-ttu-id="c5a6a-106">endpointBehaviors bölümü</span><span class="sxs-lookup"><span data-stu-id="c5a6a-106">endpointBehaviors section</span></span>  
<span data-ttu-id="c5a6a-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="c5a6a-107">\<behavior></span></span>  
<span data-ttu-id="c5a6a-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="c5a6a-108">\<clientCredentials></span></span>  
<span data-ttu-id="c5a6a-109">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="c5a6a-109">\<serviceCertificate></span></span>  
<span data-ttu-id="c5a6a-110">\<scopedCertificates ></span><span class="sxs-lookup"><span data-stu-id="c5a6a-110">\<scopedCertificates></span></span>  
<span data-ttu-id="c5a6a-111">\<Ekle > öğesi için \<scopedCertificates ></span><span class="sxs-lookup"><span data-stu-id="c5a6a-111">\<add> element for \<scopedCertificates></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5a6a-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c5a6a-112">Syntax</span></span>  
  
```xml  
<add findValue="String"  
          storeLocation="CurrentUser/LocalMachine"  
          storeName=" CurrentUser/LocalMachine"  
          targetUri="string"  
         x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"   
/>   
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c5a6a-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c5a6a-113">Attributes and Elements</span></span>  
 <span data-ttu-id="c5a6a-114">Öznitelikler, alt öğelerini ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır</span><span class="sxs-lookup"><span data-stu-id="c5a6a-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c5a6a-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c5a6a-115">Attributes</span></span>  
  
|<span data-ttu-id="c5a6a-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c5a6a-116">Attribute</span></span>|<span data-ttu-id="c5a6a-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c5a6a-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c5a6a-118">Hedefuri</span><span class="sxs-lookup"><span data-stu-id="c5a6a-118">targetUri</span></span>|<span data-ttu-id="c5a6a-119">Dize.</span><span class="sxs-lookup"><span data-stu-id="c5a6a-119">String.</span></span> <span data-ttu-id="c5a6a-120">Sertifikayla ilişkili hizmet URI'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c5a6a-120">Specifies the URI of the service associated with the certificate.</span></span>|  
|<span data-ttu-id="c5a6a-121">findValue</span><span class="sxs-lookup"><span data-stu-id="c5a6a-121">findValue</span></span>|<span data-ttu-id="c5a6a-122">Dize.</span><span class="sxs-lookup"><span data-stu-id="c5a6a-122">String.</span></span> <span data-ttu-id="c5a6a-123">Aranacak değer.</span><span class="sxs-lookup"><span data-stu-id="c5a6a-123">The value to search for.</span></span>|  
|<span data-ttu-id="c5a6a-124">X509FindType</span><span class="sxs-lookup"><span data-stu-id="c5a6a-124">x509FindType</span></span>|<span data-ttu-id="c5a6a-125">Sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="c5a6a-125">Enumeration.</span></span> <span data-ttu-id="c5a6a-126">Aranacak sertifika alanlardan biri.</span><span class="sxs-lookup"><span data-stu-id="c5a6a-126">One of the certificate fields to search.</span></span>|  
|<span data-ttu-id="c5a6a-127">storeLocation</span><span class="sxs-lookup"><span data-stu-id="c5a6a-127">storeLocation</span></span>|<span data-ttu-id="c5a6a-128">Sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="c5a6a-128">Enumeration.</span></span> <span data-ttu-id="c5a6a-129">İki birini aramak için konuma depolayın.</span><span class="sxs-lookup"><span data-stu-id="c5a6a-129">One of the two store locations to search.</span></span>|  
|<span data-ttu-id="c5a6a-130">storeName</span><span class="sxs-lookup"><span data-stu-id="c5a6a-130">storeName</span></span>|<span data-ttu-id="c5a6a-131">Sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="c5a6a-131">Enumeration.</span></span> <span data-ttu-id="c5a6a-132">Sistem aramak için depolar.</span><span class="sxs-lookup"><span data-stu-id="c5a6a-132">One of the system stores to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="c5a6a-133">findValue özniteliği</span><span class="sxs-lookup"><span data-stu-id="c5a6a-133">findValue Attribute</span></span>  
  
|<span data-ttu-id="c5a6a-134">Değer</span><span class="sxs-lookup"><span data-stu-id="c5a6a-134">Value</span></span>|<span data-ttu-id="c5a6a-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c5a6a-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c5a6a-136">Dize</span><span class="sxs-lookup"><span data-stu-id="c5a6a-136">String</span></span>|<span data-ttu-id="c5a6a-137">Değer (X509FindType özniteliği tarafından belirtilen) alan bağlıdır Aranmakta.</span><span class="sxs-lookup"><span data-stu-id="c5a6a-137">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="c5a6a-138">Örneğin, bir parmak izi için arama değeri bir onaltılık sayı dizesi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c5a6a-138">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="c5a6a-139">x509FindType özniteliği</span><span class="sxs-lookup"><span data-stu-id="c5a6a-139">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="c5a6a-140">Değer</span><span class="sxs-lookup"><span data-stu-id="c5a6a-140">Value</span></span>|<span data-ttu-id="c5a6a-141">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c5a6a-141">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c5a6a-142">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="c5a6a-142">Enumeration</span></span>|<span data-ttu-id="c5a6a-143">Değerler şunlardır: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="c5a6a-143">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="c5a6a-144">storeLocation özniteliği</span><span class="sxs-lookup"><span data-stu-id="c5a6a-144">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="c5a6a-145">Değer</span><span class="sxs-lookup"><span data-stu-id="c5a6a-145">Value</span></span>|<span data-ttu-id="c5a6a-146">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c5a6a-146">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c5a6a-147">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="c5a6a-147">Enumeration</span></span>|<span data-ttu-id="c5a6a-148">Currentuser'a veya LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="c5a6a-148">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="c5a6a-149">storeName özniteliği</span><span class="sxs-lookup"><span data-stu-id="c5a6a-149">storeName Attribute</span></span>  
  
|<span data-ttu-id="c5a6a-150">Değer</span><span class="sxs-lookup"><span data-stu-id="c5a6a-150">Value</span></span>|<span data-ttu-id="c5a6a-151">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c5a6a-151">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c5a6a-152">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="c5a6a-152">Enumeration</span></span>|<span data-ttu-id="c5a6a-153">Değerler: adres defteri, AuthRoot, sertifika yetkilisi, izin verilmeyen, My, kök, TrustedPeople ve TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="c5a6a-153">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c5a6a-154">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c5a6a-154">Child Elements</span></span>  
 <span data-ttu-id="c5a6a-155">Yok.</span><span class="sxs-lookup"><span data-stu-id="c5a6a-155">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c5a6a-156">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c5a6a-156">Parent Elements</span></span>  
  
|<span data-ttu-id="c5a6a-157">Öğe</span><span class="sxs-lookup"><span data-stu-id="c5a6a-157">Element</span></span>|<span data-ttu-id="c5a6a-158">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c5a6a-158">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c5a6a-159">\<scopedCertificates ></span><span class="sxs-lookup"><span data-stu-id="c5a6a-159">\<scopedCertificates></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md)|<span data-ttu-id="c5a6a-160">X.509 sertifikaları (kimlik doğrulaması için kapsamlı) belirli hizmetleri tarafından sağlanan bir koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c5a6a-160">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c5a6a-161">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c5a6a-161">Remarks</span></span>  
 <span data-ttu-id="c5a6a-162">Bu öğe kurduğu hizmetinin URL'sini göre hizmet sertifikasını kullanmak üzere yapılandırmak istemci sağlar.</span><span class="sxs-lookup"><span data-stu-id="c5a6a-162">This element enables the client to configure a service certificate to use based on the URL of the service it communicates with.</span></span> <span data-ttu-id="c5a6a-163">Bu, özellikle bir istemci birden fazla hizmet için (son hizmet yanı sıra Ara güvenlik belirteci Hizmetleri) burada iletişim verilen belirteç senaryolarda kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="c5a6a-163">This is especially useful in issued token scenarios where a client can be communicating to multiple services (the end service as well as intermediary security token services).</span></span> <span data-ttu-id="c5a6a-164">Bu sertifika, sertifika tabanlı ileti güvenliği kullanan bağlamaları için hizmet iletileri şifrelemek için kullanılan ve istemci yanıtlar imzalama hizmeti tarafından kullanılacak beklenen.</span><span class="sxs-lookup"><span data-stu-id="c5a6a-164">For bindings that use certificate-based message security, this certificate is used to encrypt messages to the service, and is expected to be used by the service for signing replies to the client.</span></span>  
  
 <span data-ttu-id="c5a6a-165">Bir bağlama hizmeti ve URL ScopedCertificates bulunan hizmet için belirli bir sertifika için bir sertifika gerektiriyorsa, varsayılan sertifika kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c5a6a-165">If a binding requires a certificate for the service and no specific certificate for the service URL is found in the ScopedCertificates, the default certificate is used.</span></span>  
  
 <span data-ttu-id="c5a6a-166">Daha fazla bilgi için "Sertifikalar kapsamlı" bölümüne bakın [nasıl yapılır: federe istemci oluşturma](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md).</span><span class="sxs-lookup"><span data-stu-id="c5a6a-166">For more information, see the "Scoped Certificates" section of [How to: Create a Federated Client](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c5a6a-167">Örnek</span><span class="sxs-lookup"><span data-stu-id="c5a6a-167">Example</span></span>  
 <span data-ttu-id="c5a6a-168">Aşağıdaki örnek, bir X.509 sertifikası koleksiyona ekler.</span><span class="sxs-lookup"><span data-stu-id="c5a6a-168">The following example adds an X.509 certificate the collection.</span></span>  
  
```xml  
<behaviors>  
 <endpointBehaviors>  
  <behavior name="MyEndpointBehavior">  
   <clientCredentials>  
    <serviceCertificate>  
     <scopedCertificates>  
      <add targetUri="http://www.contoso.com"   
       findValue="www.Contoso.com"   
       storeLocation="LocalMachine"  
       storeName="Root"   
       x509FindType="FindByIssuerName" />  
     </scopedCertificates>  
    </serviceCertificate>  
   </clientCredentials>  
  </behavior>  
 </endpointBehaviors>  
</behaviors>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c5a6a-169">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c5a6a-169">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>  
 <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>  
 <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>  
 [<span data-ttu-id="c5a6a-170">Nasıl yapılır: Federe İstemci Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c5a6a-170">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [<span data-ttu-id="c5a6a-171">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="c5a6a-171">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="c5a6a-172">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="c5a6a-172">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="c5a6a-173">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="c5a6a-173">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
