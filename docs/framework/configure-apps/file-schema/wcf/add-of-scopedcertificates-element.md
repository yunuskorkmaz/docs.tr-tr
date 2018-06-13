---
title: '&lt;scopedCertificates&gt; Öğesi &lt;ekleme&gt;'
ms.date: 03/30/2017
ms.assetid: e21c1ef8-d6d6-4bca-ac5a-6fbf4bd77412
ms.openlocfilehash: 0eb2f116fc0a2c7d59b90cea71150c7b46ee39fa
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32746650"
---
# <a name="ltaddgt-of-ltscopedcertificatesgt-element"></a><span data-ttu-id="d6d20-102">&lt;scopedCertificates&gt; Öğesi &lt;ekleme&gt;</span><span class="sxs-lookup"><span data-stu-id="d6d20-102">&lt;add&gt; of &lt;scopedCertificates&gt; Element</span></span>
<span data-ttu-id="d6d20-103">Bir X.509 sertifikası kapsamlı sertifikaları koleksiyonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="d6d20-103">Adds an X.509 certificate to the collection of scoped certificates.</span></span>  
  
 <span data-ttu-id="d6d20-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d6d20-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d6d20-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="d6d20-105">\<behaviors></span></span>  
<span data-ttu-id="d6d20-106">endpointBehaviors bölümü</span><span class="sxs-lookup"><span data-stu-id="d6d20-106">endpointBehaviors section</span></span>  
<span data-ttu-id="d6d20-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="d6d20-107">\<behavior></span></span>  
<span data-ttu-id="d6d20-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="d6d20-108">\<clientCredentials></span></span>  
<span data-ttu-id="d6d20-109">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="d6d20-109">\<serviceCertificate></span></span>  
<span data-ttu-id="d6d20-110">\<scopedCertificates ></span><span class="sxs-lookup"><span data-stu-id="d6d20-110">\<scopedCertificates></span></span>  
<span data-ttu-id="d6d20-111">\<Ekle > öğesi için \<scopedCertificates ></span><span class="sxs-lookup"><span data-stu-id="d6d20-111">\<add> element for \<scopedCertificates></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6d20-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d6d20-112">Syntax</span></span>  
  
```xml  
<add findValue="String"  
          storeLocation="CurrentUser/LocalMachine"  
          storeName=" CurrentUser/LocalMachine"  
          targetUri="string"  
         x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"   
/>   
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d6d20-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d6d20-113">Attributes and Elements</span></span>  
 <span data-ttu-id="d6d20-114">Öznitelikler, alt öğelerini ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır</span><span class="sxs-lookup"><span data-stu-id="d6d20-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d6d20-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d6d20-115">Attributes</span></span>  
  
|<span data-ttu-id="d6d20-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d6d20-116">Attribute</span></span>|<span data-ttu-id="d6d20-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d6d20-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d6d20-118">Hedefuri</span><span class="sxs-lookup"><span data-stu-id="d6d20-118">targetUri</span></span>|<span data-ttu-id="d6d20-119">Dize.</span><span class="sxs-lookup"><span data-stu-id="d6d20-119">String.</span></span> <span data-ttu-id="d6d20-120">Sertifikayla ilişkili hizmet URI'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d6d20-120">Specifies the URI of the service associated with the certificate.</span></span>|  
|<span data-ttu-id="d6d20-121">findValue</span><span class="sxs-lookup"><span data-stu-id="d6d20-121">findValue</span></span>|<span data-ttu-id="d6d20-122">Dize.</span><span class="sxs-lookup"><span data-stu-id="d6d20-122">String.</span></span> <span data-ttu-id="d6d20-123">Aranacak değer.</span><span class="sxs-lookup"><span data-stu-id="d6d20-123">The value to search for.</span></span>|  
|<span data-ttu-id="d6d20-124">X509FindType</span><span class="sxs-lookup"><span data-stu-id="d6d20-124">x509FindType</span></span>|<span data-ttu-id="d6d20-125">Sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="d6d20-125">Enumeration.</span></span> <span data-ttu-id="d6d20-126">Aranacak sertifika alanlardan biri.</span><span class="sxs-lookup"><span data-stu-id="d6d20-126">One of the certificate fields to search.</span></span>|  
|<span data-ttu-id="d6d20-127">storeLocation</span><span class="sxs-lookup"><span data-stu-id="d6d20-127">storeLocation</span></span>|<span data-ttu-id="d6d20-128">Sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="d6d20-128">Enumeration.</span></span> <span data-ttu-id="d6d20-129">İki birini aramak için konuma depolayın.</span><span class="sxs-lookup"><span data-stu-id="d6d20-129">One of the two store locations to search.</span></span>|  
|<span data-ttu-id="d6d20-130">storeName</span><span class="sxs-lookup"><span data-stu-id="d6d20-130">storeName</span></span>|<span data-ttu-id="d6d20-131">Sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="d6d20-131">Enumeration.</span></span> <span data-ttu-id="d6d20-132">Sistem aramak için depolar.</span><span class="sxs-lookup"><span data-stu-id="d6d20-132">One of the system stores to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="d6d20-133">findValue özniteliği</span><span class="sxs-lookup"><span data-stu-id="d6d20-133">findValue Attribute</span></span>  
  
|<span data-ttu-id="d6d20-134">Değer</span><span class="sxs-lookup"><span data-stu-id="d6d20-134">Value</span></span>|<span data-ttu-id="d6d20-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d6d20-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d6d20-136">Dize</span><span class="sxs-lookup"><span data-stu-id="d6d20-136">String</span></span>|<span data-ttu-id="d6d20-137">Değer (X509FindType özniteliği tarafından belirtilen) alan bağlıdır Aranmakta.</span><span class="sxs-lookup"><span data-stu-id="d6d20-137">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="d6d20-138">Örneğin, bir parmak izi için arama değeri bir onaltılık sayı dizesi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d6d20-138">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="d6d20-139">x509FindType özniteliği</span><span class="sxs-lookup"><span data-stu-id="d6d20-139">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="d6d20-140">Değer</span><span class="sxs-lookup"><span data-stu-id="d6d20-140">Value</span></span>|<span data-ttu-id="d6d20-141">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d6d20-141">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d6d20-142">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="d6d20-142">Enumeration</span></span>|<span data-ttu-id="d6d20-143">Değerler şunlardır: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="d6d20-143">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="d6d20-144">storeLocation özniteliği</span><span class="sxs-lookup"><span data-stu-id="d6d20-144">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="d6d20-145">Değer</span><span class="sxs-lookup"><span data-stu-id="d6d20-145">Value</span></span>|<span data-ttu-id="d6d20-146">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d6d20-146">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d6d20-147">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="d6d20-147">Enumeration</span></span>|<span data-ttu-id="d6d20-148">Currentuser'a veya LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="d6d20-148">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="d6d20-149">storeName özniteliği</span><span class="sxs-lookup"><span data-stu-id="d6d20-149">storeName Attribute</span></span>  
  
|<span data-ttu-id="d6d20-150">Değer</span><span class="sxs-lookup"><span data-stu-id="d6d20-150">Value</span></span>|<span data-ttu-id="d6d20-151">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d6d20-151">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d6d20-152">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="d6d20-152">Enumeration</span></span>|<span data-ttu-id="d6d20-153">Değerler: adres defteri, AuthRoot, sertifika yetkilisi, izin verilmeyen, My, kök, TrustedPeople ve TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="d6d20-153">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d6d20-154">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d6d20-154">Child Elements</span></span>  
 <span data-ttu-id="d6d20-155">Yok.</span><span class="sxs-lookup"><span data-stu-id="d6d20-155">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d6d20-156">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d6d20-156">Parent Elements</span></span>  
  
|<span data-ttu-id="d6d20-157">Öğe</span><span class="sxs-lookup"><span data-stu-id="d6d20-157">Element</span></span>|<span data-ttu-id="d6d20-158">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d6d20-158">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d6d20-159">\<scopedCertificates ></span><span class="sxs-lookup"><span data-stu-id="d6d20-159">\<scopedCertificates></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md)|<span data-ttu-id="d6d20-160">X.509 sertifikaları (kimlik doğrulaması için kapsamlı) belirli hizmetleri tarafından sağlanan bir koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d6d20-160">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d6d20-161">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d6d20-161">Remarks</span></span>  
 <span data-ttu-id="d6d20-162">Bu öğe kurduğu hizmetinin URL'sini göre hizmet sertifikasını kullanmak üzere yapılandırmak istemci sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6d20-162">This element enables the client to configure a service certificate to use based on the URL of the service it communicates with.</span></span> <span data-ttu-id="d6d20-163">Bu, özellikle bir istemci birden fazla hizmet için (son hizmet yanı sıra Ara güvenlik belirteci Hizmetleri) burada iletişim verilen belirteç senaryolarda kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="d6d20-163">This is especially useful in issued token scenarios where a client can be communicating to multiple services (the end service as well as intermediary security token services).</span></span> <span data-ttu-id="d6d20-164">Bu sertifika, sertifika tabanlı ileti güvenliği kullanan bağlamaları için hizmet iletileri şifrelemek için kullanılan ve istemci yanıtlar imzalama hizmeti tarafından kullanılacak beklenen.</span><span class="sxs-lookup"><span data-stu-id="d6d20-164">For bindings that use certificate-based message security, this certificate is used to encrypt messages to the service, and is expected to be used by the service for signing replies to the client.</span></span>  
  
 <span data-ttu-id="d6d20-165">Bir bağlama hizmeti ve URL ScopedCertificates bulunan hizmet için belirli bir sertifika için bir sertifika gerektiriyorsa, varsayılan sertifika kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d6d20-165">If a binding requires a certificate for the service and no specific certificate for the service URL is found in the ScopedCertificates, the default certificate is used.</span></span>  
  
 <span data-ttu-id="d6d20-166">Daha fazla bilgi için "Sertifikalar kapsamlı" bölümüne bakın [nasıl yapılır: federe istemci oluşturma](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md).</span><span class="sxs-lookup"><span data-stu-id="d6d20-166">For more information, see the "Scoped Certificates" section of [How to: Create a Federated Client](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6d20-167">Örnek</span><span class="sxs-lookup"><span data-stu-id="d6d20-167">Example</span></span>  
 <span data-ttu-id="d6d20-168">Aşağıdaki örnek, bir X.509 sertifikası koleksiyona ekler.</span><span class="sxs-lookup"><span data-stu-id="d6d20-168">The following example adds an X.509 certificate the collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d6d20-169">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d6d20-169">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>  
 <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>  
 <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>  
 [<span data-ttu-id="d6d20-170">Nasıl yapılır: Federe İstemci Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d6d20-170">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [<span data-ttu-id="d6d20-171">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="d6d20-171">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="d6d20-172">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="d6d20-172">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="d6d20-173">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="d6d20-173">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
