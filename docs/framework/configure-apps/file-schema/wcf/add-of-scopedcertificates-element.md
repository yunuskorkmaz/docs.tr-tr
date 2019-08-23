---
title: <add><scopedCertificates> öğesinin
ms.date: 03/30/2017
ms.assetid: e21c1ef8-d6d6-4bca-ac5a-6fbf4bd77412
ms.openlocfilehash: 9756d37527fcf888cad930b24677ae8e6a2c8fba
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920049"
---
# <a name="add-of-scopedcertificates-element"></a><span data-ttu-id="c7592-102">\<> \<ScopedCertificates > öğesi ekleme</span><span class="sxs-lookup"><span data-stu-id="c7592-102">\<add> of \<scopedCertificates> Element</span></span>
<span data-ttu-id="c7592-103">Kapsamlı sertifikalar koleksiyonuna bir X. 509.440 sertifikası ekler.</span><span class="sxs-lookup"><span data-stu-id="c7592-103">Adds an X.509 certificate to the collection of scoped certificates.</span></span>  
  
 <span data-ttu-id="c7592-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c7592-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="c7592-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="c7592-105">\<behaviors></span></span>  
<span data-ttu-id="c7592-106">Endpointdavranışlar bölümü</span><span class="sxs-lookup"><span data-stu-id="c7592-106">endpointBehaviors section</span></span>  
<span data-ttu-id="c7592-107">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="c7592-107">\<behavior></span></span>  
<span data-ttu-id="c7592-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="c7592-108">\<clientCredentials></span></span>  
<span data-ttu-id="c7592-109">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="c7592-109">\<serviceCertificate></span></span>  
<span data-ttu-id="c7592-110">\<scopedCertificates ></span><span class="sxs-lookup"><span data-stu-id="c7592-110">\<scopedCertificates></span></span>  
<span data-ttu-id="c7592-111">\<ScopedCertificates için \<> öğesi ekleyin ></span><span class="sxs-lookup"><span data-stu-id="c7592-111">\<add> element for \<scopedCertificates></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7592-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c7592-112">Syntax</span></span>  
  
```xml  
<add findValue="String"
     storeLocation="CurrentUser/LocalMachine"
     storeName=" CurrentUser/LocalMachine"
     targetUri="string"
     x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c7592-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c7592-113">Attributes and Elements</span></span>  
 <span data-ttu-id="c7592-114">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="c7592-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c7592-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c7592-115">Attributes</span></span>  
  
|<span data-ttu-id="c7592-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c7592-116">Attribute</span></span>|<span data-ttu-id="c7592-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c7592-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c7592-118">HedefUri</span><span class="sxs-lookup"><span data-stu-id="c7592-118">targetUri</span></span>|<span data-ttu-id="c7592-119">Dizisinde.</span><span class="sxs-lookup"><span data-stu-id="c7592-119">String.</span></span> <span data-ttu-id="c7592-120">Sertifikayla ilişkili hizmetin URI 'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c7592-120">Specifies the URI of the service associated with the certificate.</span></span>|  
|<span data-ttu-id="c7592-121">findValue</span><span class="sxs-lookup"><span data-stu-id="c7592-121">findValue</span></span>|<span data-ttu-id="c7592-122">Dizisinde.</span><span class="sxs-lookup"><span data-stu-id="c7592-122">String.</span></span> <span data-ttu-id="c7592-123">Aranacak değer.</span><span class="sxs-lookup"><span data-stu-id="c7592-123">The value to search for.</span></span>|  
|<span data-ttu-id="c7592-124">x509FindType</span><span class="sxs-lookup"><span data-stu-id="c7592-124">x509FindType</span></span>|<span data-ttu-id="c7592-125">Listelenen.</span><span class="sxs-lookup"><span data-stu-id="c7592-125">Enumeration.</span></span> <span data-ttu-id="c7592-126">Arama yapılacak sertifika alanlarından biri.</span><span class="sxs-lookup"><span data-stu-id="c7592-126">One of the certificate fields to search.</span></span>|  
|<span data-ttu-id="c7592-127">storeLocation</span><span class="sxs-lookup"><span data-stu-id="c7592-127">storeLocation</span></span>|<span data-ttu-id="c7592-128">Listelenen.</span><span class="sxs-lookup"><span data-stu-id="c7592-128">Enumeration.</span></span> <span data-ttu-id="c7592-129">Arama yapılacak iki depolama konumundan biri.</span><span class="sxs-lookup"><span data-stu-id="c7592-129">One of the two store locations to search.</span></span>|  
|<span data-ttu-id="c7592-130">storeName</span><span class="sxs-lookup"><span data-stu-id="c7592-130">storeName</span></span>|<span data-ttu-id="c7592-131">Listelenen.</span><span class="sxs-lookup"><span data-stu-id="c7592-131">Enumeration.</span></span> <span data-ttu-id="c7592-132">Arama yapmak için sistem mağazalarından biri.</span><span class="sxs-lookup"><span data-stu-id="c7592-132">One of the system stores to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="c7592-133">findValue özniteliği</span><span class="sxs-lookup"><span data-stu-id="c7592-133">findValue Attribute</span></span>  
  
|<span data-ttu-id="c7592-134">Değer</span><span class="sxs-lookup"><span data-stu-id="c7592-134">Value</span></span>|<span data-ttu-id="c7592-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c7592-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c7592-136">Dize</span><span class="sxs-lookup"><span data-stu-id="c7592-136">String</span></span>|<span data-ttu-id="c7592-137">Değer, aranmakta olan alana bağlıdır (X509FindType özniteliğiyle belirtilir).</span><span class="sxs-lookup"><span data-stu-id="c7592-137">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="c7592-138">Örneğin, bir parmak izi arıyorsanız, değerin onaltılık sayı dizesi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c7592-138">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="c7592-139">x509FindType özniteliği</span><span class="sxs-lookup"><span data-stu-id="c7592-139">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="c7592-140">Değer</span><span class="sxs-lookup"><span data-stu-id="c7592-140">Value</span></span>|<span data-ttu-id="c7592-141">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c7592-141">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c7592-142">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="c7592-142">Enumeration</span></span>|<span data-ttu-id="c7592-143">Değerler şunlardır: Findbyparmak izi, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, Findbytımenotyetvalid, FindBySerialNumber, Findbytimedoldu, FindByTemplateName , FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="c7592-143">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="c7592-144">storeLocation özniteliği</span><span class="sxs-lookup"><span data-stu-id="c7592-144">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="c7592-145">Değer</span><span class="sxs-lookup"><span data-stu-id="c7592-145">Value</span></span>|<span data-ttu-id="c7592-146">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c7592-146">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c7592-147">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="c7592-147">Enumeration</span></span>|<span data-ttu-id="c7592-148">CurrentUser veya LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="c7592-148">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="c7592-149">storeName özniteliği</span><span class="sxs-lookup"><span data-stu-id="c7592-149">storeName Attribute</span></span>  
  
|<span data-ttu-id="c7592-150">Değer</span><span class="sxs-lookup"><span data-stu-id="c7592-150">Value</span></span>|<span data-ttu-id="c7592-151">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c7592-151">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c7592-152">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="c7592-152">Enumeration</span></span>|<span data-ttu-id="c7592-153">Değerler şunlardır: AddressBook, AuthRoot, CertificateAuthority, Izin verilmeyen, My, root, Trustedkişilerim ve TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="c7592-153">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c7592-154">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c7592-154">Child Elements</span></span>  
 <span data-ttu-id="c7592-155">Yok.</span><span class="sxs-lookup"><span data-stu-id="c7592-155">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c7592-156">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c7592-156">Parent Elements</span></span>  
  
|<span data-ttu-id="c7592-157">Öğe</span><span class="sxs-lookup"><span data-stu-id="c7592-157">Element</span></span>|<span data-ttu-id="c7592-158">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c7592-158">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c7592-159">\<scopedCertificates ></span><span class="sxs-lookup"><span data-stu-id="c7592-159">\<scopedCertificates></span></span>](scopedcertificates-element.md)|<span data-ttu-id="c7592-160">Kimlik doğrulama için belirli hizmetler (kapsamlı) tarafından sunulan X. 509.440 sertifikalarının bir koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c7592-160">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c7592-161">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c7592-161">Remarks</span></span>  
 <span data-ttu-id="c7592-162">Bu öğe, istemcinin iletişim kurduğu hizmetin URL 'sini temel alarak kullanmak üzere bir hizmet sertifikası yapılandırmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="c7592-162">This element enables the client to configure a service certificate to use based on the URL of the service it communicates with.</span></span> <span data-ttu-id="c7592-163">Bu özellikle, bir istemcinin birden çok hizmetle (bitiş hizmeti ve aracı güvenlik belirteci Hizmetleri) iletişim kuramadığı verilen belirteç senaryolarında kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="c7592-163">This is especially useful in issued token scenarios where a client can be communicating to multiple services (the end service as well as intermediary security token services).</span></span> <span data-ttu-id="c7592-164">Sertifika tabanlı ileti güvenliği kullanan bağlamalar için, bu sertifika hizmete iletileri şifrelemek için kullanılır ve istemciye yanıtları imzalamak için hizmet tarafından kullanılması beklenir.</span><span class="sxs-lookup"><span data-stu-id="c7592-164">For bindings that use certificate-based message security, this certificate is used to encrypt messages to the service, and is expected to be used by the service for signing replies to the client.</span></span>  
  
 <span data-ttu-id="c7592-165">Bir bağlama hizmet için bir sertifika gerektiriyorsa ve hizmet URL 'SI için belirli bir sertifika ScopedCertificates içinde bulunmazsa, varsayılan sertifika kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c7592-165">If a binding requires a certificate for the service and no specific certificate for the service URL is found in the ScopedCertificates, the default certificate is used.</span></span>  
  
 <span data-ttu-id="c7592-166">Daha fazla bilgi için bkz [. nasıl yapılır: Federasyon Istemcisi](../../../wcf/feature-details/how-to-create-a-federated-client.md)oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c7592-166">For more information, see the "Scoped Certificates" section of [How to: Create a Federated Client](../../../wcf/feature-details/how-to-create-a-federated-client.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c7592-167">Örnek</span><span class="sxs-lookup"><span data-stu-id="c7592-167">Example</span></span>  
 <span data-ttu-id="c7592-168">Aşağıdaki örnek, koleksiyonu bir X. 509.440 sertifikası ekler.</span><span class="sxs-lookup"><span data-stu-id="c7592-168">The following example adds an X.509 certificate the collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c7592-169">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c7592-169">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>
- [<span data-ttu-id="c7592-170">Nasıl yapılır: Federe Istemci oluşturma</span><span class="sxs-lookup"><span data-stu-id="c7592-170">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="c7592-171">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="c7592-171">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="c7592-172">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="c7592-172">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="c7592-173">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="c7592-173">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
