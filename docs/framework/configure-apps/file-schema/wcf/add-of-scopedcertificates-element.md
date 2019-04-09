---
title: <add> ' ın <scopedCertificates> öğesi
ms.date: 03/30/2017
ms.assetid: e21c1ef8-d6d6-4bca-ac5a-6fbf4bd77412
ms.openlocfilehash: 06a624d0146745581dfe907d044d1f7d3b857902
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59119684"
---
# <a name="add-of-scopedcertificates-element"></a><span data-ttu-id="43531-102">\<Ekle >, \<scopedCertificates > öğesi</span><span class="sxs-lookup"><span data-stu-id="43531-102">\<add> of \<scopedCertificates> Element</span></span>
<span data-ttu-id="43531-103">Kapsamlı sertifikalar koleksiyonuna bir X.509 sertifikası ekler.</span><span class="sxs-lookup"><span data-stu-id="43531-103">Adds an X.509 certificate to the collection of scoped certificates.</span></span>  
  
 <span data-ttu-id="43531-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="43531-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="43531-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="43531-105">\<behaviors></span></span>  
<span data-ttu-id="43531-106">endpointBehaviors bölümü</span><span class="sxs-lookup"><span data-stu-id="43531-106">endpointBehaviors section</span></span>  
<span data-ttu-id="43531-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="43531-107">\<behavior></span></span>  
<span data-ttu-id="43531-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="43531-108">\<clientCredentials></span></span>  
<span data-ttu-id="43531-109">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="43531-109">\<serviceCertificate></span></span>  
<span data-ttu-id="43531-110">\<scopedCertificates ></span><span class="sxs-lookup"><span data-stu-id="43531-110">\<scopedCertificates></span></span>  
<span data-ttu-id="43531-111">\<Ekle > öğesi için \<scopedCertificates ></span><span class="sxs-lookup"><span data-stu-id="43531-111">\<add> element for \<scopedCertificates></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43531-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="43531-112">Syntax</span></span>  
  
```xml  
<add findValue="String"
     storeLocation="CurrentUser/LocalMachine"
     storeName=" CurrentUser/LocalMachine"
     targetUri="string"
     x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="43531-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="43531-113">Attributes and Elements</span></span>  
 <span data-ttu-id="43531-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="43531-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="43531-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="43531-115">Attributes</span></span>  
  
|<span data-ttu-id="43531-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="43531-116">Attribute</span></span>|<span data-ttu-id="43531-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="43531-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="43531-118">Hedefuri</span><span class="sxs-lookup"><span data-stu-id="43531-118">targetUri</span></span>|<span data-ttu-id="43531-119">dize.</span><span class="sxs-lookup"><span data-stu-id="43531-119">String.</span></span> <span data-ttu-id="43531-120">Sertifikayla ilişkili hizmetin URI belirtir.</span><span class="sxs-lookup"><span data-stu-id="43531-120">Specifies the URI of the service associated with the certificate.</span></span>|  
|<span data-ttu-id="43531-121">findValue</span><span class="sxs-lookup"><span data-stu-id="43531-121">findValue</span></span>|<span data-ttu-id="43531-122">dize.</span><span class="sxs-lookup"><span data-stu-id="43531-122">String.</span></span> <span data-ttu-id="43531-123">Aranacak değer.</span><span class="sxs-lookup"><span data-stu-id="43531-123">The value to search for.</span></span>|  
|<span data-ttu-id="43531-124">X509FindType</span><span class="sxs-lookup"><span data-stu-id="43531-124">x509FindType</span></span>|<span data-ttu-id="43531-125">Sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="43531-125">Enumeration.</span></span> <span data-ttu-id="43531-126">Aranacak sertifika alanlardan biri.</span><span class="sxs-lookup"><span data-stu-id="43531-126">One of the certificate fields to search.</span></span>|  
|<span data-ttu-id="43531-127">storeLocation</span><span class="sxs-lookup"><span data-stu-id="43531-127">storeLocation</span></span>|<span data-ttu-id="43531-128">Sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="43531-128">Enumeration.</span></span> <span data-ttu-id="43531-129">İki birini aranacak konumların depolayın.</span><span class="sxs-lookup"><span data-stu-id="43531-129">One of the two store locations to search.</span></span>|  
|<span data-ttu-id="43531-130">storeName</span><span class="sxs-lookup"><span data-stu-id="43531-130">storeName</span></span>|<span data-ttu-id="43531-131">Sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="43531-131">Enumeration.</span></span> <span data-ttu-id="43531-132">Aranacak bir sistemin depolar.</span><span class="sxs-lookup"><span data-stu-id="43531-132">One of the system stores to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="43531-133">findValue özniteliği</span><span class="sxs-lookup"><span data-stu-id="43531-133">findValue Attribute</span></span>  
  
|<span data-ttu-id="43531-134">Değer</span><span class="sxs-lookup"><span data-stu-id="43531-134">Value</span></span>|<span data-ttu-id="43531-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="43531-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="43531-136">Dize</span><span class="sxs-lookup"><span data-stu-id="43531-136">String</span></span>|<span data-ttu-id="43531-137">Değer (X509FindType özniteliği tarafından belirtilen) alan bağlıdır Aranan.</span><span class="sxs-lookup"><span data-stu-id="43531-137">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="43531-138">Örneğin, bir parmak izi için arama değeri bir dize onaltılık bir sayı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="43531-138">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="43531-139">x509FindType özniteliği</span><span class="sxs-lookup"><span data-stu-id="43531-139">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="43531-140">Değer</span><span class="sxs-lookup"><span data-stu-id="43531-140">Value</span></span>|<span data-ttu-id="43531-141">Açıklama</span><span class="sxs-lookup"><span data-stu-id="43531-141">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="43531-142">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="43531-142">Enumeration</span></span>|<span data-ttu-id="43531-143">Değerler şunlardır: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName , FindByApplicationPolicy FindByCertificatePolicy, FindByExtension FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="43531-143">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="43531-144">storeLocation özniteliği</span><span class="sxs-lookup"><span data-stu-id="43531-144">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="43531-145">Değer</span><span class="sxs-lookup"><span data-stu-id="43531-145">Value</span></span>|<span data-ttu-id="43531-146">Açıklama</span><span class="sxs-lookup"><span data-stu-id="43531-146">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="43531-147">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="43531-147">Enumeration</span></span>|<span data-ttu-id="43531-148">LocalMachine ya da CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="43531-148">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="43531-149">storeName özniteliği</span><span class="sxs-lookup"><span data-stu-id="43531-149">storeName Attribute</span></span>  
  
|<span data-ttu-id="43531-150">Değer</span><span class="sxs-lookup"><span data-stu-id="43531-150">Value</span></span>|<span data-ttu-id="43531-151">Açıklama</span><span class="sxs-lookup"><span data-stu-id="43531-151">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="43531-152">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="43531-152">Enumeration</span></span>|<span data-ttu-id="43531-153">Değerler şunlardır: Adres Defteri, AuthRoot, CertificateAuthority, My izni, kök, TrustedPeople ve TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="43531-153">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="43531-154">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="43531-154">Child Elements</span></span>  
 <span data-ttu-id="43531-155">Yok.</span><span class="sxs-lookup"><span data-stu-id="43531-155">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="43531-156">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="43531-156">Parent Elements</span></span>  
  
|<span data-ttu-id="43531-157">Öğe</span><span class="sxs-lookup"><span data-stu-id="43531-157">Element</span></span>|<span data-ttu-id="43531-158">Açıklama</span><span class="sxs-lookup"><span data-stu-id="43531-158">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="43531-159">\<scopedCertificates ></span><span class="sxs-lookup"><span data-stu-id="43531-159">\<scopedCertificates></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md)|<span data-ttu-id="43531-160">Belirli hizmetler (kapsamlı kimlik doğrulaması için) tarafından sağlanan X.509 Sertifika koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="43531-160">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="43531-161">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="43531-161">Remarks</span></span>  
 <span data-ttu-id="43531-162">Bu öğe kullanmak için hizmet sertifikası yapılandırmak istemci kurduğu hizmet URL'sini temel sağlar.</span><span class="sxs-lookup"><span data-stu-id="43531-162">This element enables the client to configure a service certificate to use based on the URL of the service it communicates with.</span></span> <span data-ttu-id="43531-163">Bu, özellikle bir istemci birden çok hizmeti (uç hizmetinin yanı sıra Ara güvenlik belirteci hizmetlerine) burada iletişim verilen belirteç senaryolarda yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="43531-163">This is especially useful in issued token scenarios where a client can be communicating to multiple services (the end service as well as intermediary security token services).</span></span> <span data-ttu-id="43531-164">Bu sertifika, sertifika tabanlı ileti güvenliği kullanan bağlamaları için hizmet iletileri şifrelemek için kullanılır ve istemciye yanıt imzalama için hizmet tarafından kullanılmak üzere beklenir.</span><span class="sxs-lookup"><span data-stu-id="43531-164">For bindings that use certificate-based message security, this certificate is used to encrypt messages to the service, and is expected to be used by the service for signing replies to the client.</span></span>  
  
 <span data-ttu-id="43531-165">Bağlama, hizmet ve URL ScopedCertificates içinde bulunan hizmet için belirli bir sertifika için bir sertifika gerektiriyorsa, varsayılan sertifika kullanılır.</span><span class="sxs-lookup"><span data-stu-id="43531-165">If a binding requires a certificate for the service and no specific certificate for the service URL is found in the ScopedCertificates, the default certificate is used.</span></span>  
  
 <span data-ttu-id="43531-166">Daha fazla bilgi için "Sertifikalar kapsamlı" bölümüne bakın. [nasıl yapılır: Federe istemci oluşturma](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md).</span><span class="sxs-lookup"><span data-stu-id="43531-166">For more information, see the "Scoped Certificates" section of [How to: Create a Federated Client](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="43531-167">Örnek</span><span class="sxs-lookup"><span data-stu-id="43531-167">Example</span></span>  
 <span data-ttu-id="43531-168">Aşağıdaki örnek koleksiyonuna bir X.509 sertifikası ekler.</span><span class="sxs-lookup"><span data-stu-id="43531-168">The following example adds an X.509 certificate the collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="43531-169">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="43531-169">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>
- [<span data-ttu-id="43531-170">Nasıl yapılır: Federe İstemci Oluşturma</span><span class="sxs-lookup"><span data-stu-id="43531-170">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="43531-171">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="43531-171">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="43531-172">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="43531-172">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
- [<span data-ttu-id="43531-173">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="43531-173">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
