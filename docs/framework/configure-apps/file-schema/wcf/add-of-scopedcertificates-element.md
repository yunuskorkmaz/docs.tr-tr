---
title: <add><scopedCertificates> öğesinin
ms.date: 03/30/2017
ms.assetid: e21c1ef8-d6d6-4bca-ac5a-6fbf4bd77412
ms.openlocfilehash: b00a342108beca69a906fbf6212915768e98778f
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398339"
---
# <a name="add-of-scopedcertificates-element"></a><span data-ttu-id="b23e4-102">\<> \<ScopedCertificates > öğesi ekleme</span><span class="sxs-lookup"><span data-stu-id="b23e4-102">\<add> of \<scopedCertificates> Element</span></span>
<span data-ttu-id="b23e4-103">Kapsamlı sertifikalar koleksiyonuna bir X. 509.440 sertifikası ekler.</span><span class="sxs-lookup"><span data-stu-id="b23e4-103">Adds an X.509 certificate to the collection of scoped certificates.</span></span>  
  
<span data-ttu-id="b23e4-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b23e4-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b23e4-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="b23e4-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="b23e4-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışlar >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="b23e4-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="b23e4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Endpointdavranışlar >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="b23e4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="b23e4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="b23e4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="b23e4-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="b23e4-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="b23e4-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceCertificate >** ](servicecertificate-of-clientcredentials-element.md)</span><span class="sxs-lookup"><span data-stu-id="b23e4-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate-of-clientcredentials-element.md)</span></span>\
<span data-ttu-id="b23e4-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<scopedCertificates >** ](scopedcertificates-element.md)</span><span class="sxs-lookup"><span data-stu-id="b23e4-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<scopedCertificates>**](scopedcertificates-element.md)</span></span>\
<span data-ttu-id="b23e4-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> Ekle**</span><span class="sxs-lookup"><span data-stu-id="b23e4-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b23e4-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b23e4-113">Syntax</span></span>  
  
```xml  
<add findValue="String"
     storeLocation="CurrentUser/LocalMachine"
     storeName=" CurrentUser/LocalMachine"
     targetUri="string"
     x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b23e4-114">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b23e4-114">Attributes and Elements</span></span>  
 <span data-ttu-id="b23e4-115">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="b23e4-115">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b23e4-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b23e4-116">Attributes</span></span>  
  
|<span data-ttu-id="b23e4-117">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b23e4-117">Attribute</span></span>|<span data-ttu-id="b23e4-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b23e4-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b23e4-119">HedefUri</span><span class="sxs-lookup"><span data-stu-id="b23e4-119">targetUri</span></span>|<span data-ttu-id="b23e4-120">Dizisinde.</span><span class="sxs-lookup"><span data-stu-id="b23e4-120">String.</span></span> <span data-ttu-id="b23e4-121">Sertifikayla ilişkili hizmetin URI 'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b23e4-121">Specifies the URI of the service associated with the certificate.</span></span>|  
|<span data-ttu-id="b23e4-122">findValue</span><span class="sxs-lookup"><span data-stu-id="b23e4-122">findValue</span></span>|<span data-ttu-id="b23e4-123">Dizisinde.</span><span class="sxs-lookup"><span data-stu-id="b23e4-123">String.</span></span> <span data-ttu-id="b23e4-124">Aranacak değer.</span><span class="sxs-lookup"><span data-stu-id="b23e4-124">The value to search for.</span></span>|  
|<span data-ttu-id="b23e4-125">x509FindType</span><span class="sxs-lookup"><span data-stu-id="b23e4-125">x509FindType</span></span>|<span data-ttu-id="b23e4-126">Listelenen.</span><span class="sxs-lookup"><span data-stu-id="b23e4-126">Enumeration.</span></span> <span data-ttu-id="b23e4-127">Arama yapılacak sertifika alanlarından biri.</span><span class="sxs-lookup"><span data-stu-id="b23e4-127">One of the certificate fields to search.</span></span>|  
|<span data-ttu-id="b23e4-128">storeLocation</span><span class="sxs-lookup"><span data-stu-id="b23e4-128">storeLocation</span></span>|<span data-ttu-id="b23e4-129">Listelenen.</span><span class="sxs-lookup"><span data-stu-id="b23e4-129">Enumeration.</span></span> <span data-ttu-id="b23e4-130">Arama yapılacak iki depolama konumundan biri.</span><span class="sxs-lookup"><span data-stu-id="b23e4-130">One of the two store locations to search.</span></span>|  
|<span data-ttu-id="b23e4-131">storeName</span><span class="sxs-lookup"><span data-stu-id="b23e4-131">storeName</span></span>|<span data-ttu-id="b23e4-132">Listelenen.</span><span class="sxs-lookup"><span data-stu-id="b23e4-132">Enumeration.</span></span> <span data-ttu-id="b23e4-133">Arama yapmak için sistem mağazalarından biri.</span><span class="sxs-lookup"><span data-stu-id="b23e4-133">One of the system stores to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="b23e4-134">findValue özniteliği</span><span class="sxs-lookup"><span data-stu-id="b23e4-134">findValue Attribute</span></span>  
  
|<span data-ttu-id="b23e4-135">Değer</span><span class="sxs-lookup"><span data-stu-id="b23e4-135">Value</span></span>|<span data-ttu-id="b23e4-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b23e4-136">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b23e4-137">Dize</span><span class="sxs-lookup"><span data-stu-id="b23e4-137">String</span></span>|<span data-ttu-id="b23e4-138">Değer, aranmakta olan alana bağlıdır (X509FindType özniteliğiyle belirtilir).</span><span class="sxs-lookup"><span data-stu-id="b23e4-138">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="b23e4-139">Örneğin, bir parmak izi arıyorsanız, değerin onaltılık sayı dizesi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b23e4-139">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="b23e4-140">x509FindType özniteliği</span><span class="sxs-lookup"><span data-stu-id="b23e4-140">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="b23e4-141">Değer</span><span class="sxs-lookup"><span data-stu-id="b23e4-141">Value</span></span>|<span data-ttu-id="b23e4-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b23e4-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b23e4-143">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="b23e4-143">Enumeration</span></span>|<span data-ttu-id="b23e4-144">Değerler şunlardır: Findbyparmak izi, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, Findbytımenotyetvalid, FindBySerialNumber, Findbytimedoldu, FindByTemplateName , FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="b23e4-144">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="b23e4-145">storeLocation özniteliği</span><span class="sxs-lookup"><span data-stu-id="b23e4-145">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="b23e4-146">Değer</span><span class="sxs-lookup"><span data-stu-id="b23e4-146">Value</span></span>|<span data-ttu-id="b23e4-147">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b23e4-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b23e4-148">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="b23e4-148">Enumeration</span></span>|<span data-ttu-id="b23e4-149">CurrentUser veya LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="b23e4-149">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="b23e4-150">storeName özniteliği</span><span class="sxs-lookup"><span data-stu-id="b23e4-150">storeName Attribute</span></span>  
  
|<span data-ttu-id="b23e4-151">Değer</span><span class="sxs-lookup"><span data-stu-id="b23e4-151">Value</span></span>|<span data-ttu-id="b23e4-152">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b23e4-152">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b23e4-153">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="b23e4-153">Enumeration</span></span>|<span data-ttu-id="b23e4-154">Değerler şunlardır: AddressBook, AuthRoot, CertificateAuthority, Izin verilmeyen, My, root, Trustedkişilerim ve TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="b23e4-154">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b23e4-155">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b23e4-155">Child Elements</span></span>  
 <span data-ttu-id="b23e4-156">Yok.</span><span class="sxs-lookup"><span data-stu-id="b23e4-156">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b23e4-157">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b23e4-157">Parent Elements</span></span>  
  
|<span data-ttu-id="b23e4-158">Öğe</span><span class="sxs-lookup"><span data-stu-id="b23e4-158">Element</span></span>|<span data-ttu-id="b23e4-159">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b23e4-159">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b23e4-160">\<scopedCertificates ></span><span class="sxs-lookup"><span data-stu-id="b23e4-160">\<scopedCertificates></span></span>](scopedcertificates-element.md)|<span data-ttu-id="b23e4-161">Kimlik doğrulama için belirli hizmetler (kapsamlı) tarafından sunulan X. 509.440 sertifikalarının bir koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b23e4-161">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b23e4-162">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b23e4-162">Remarks</span></span>  
 <span data-ttu-id="b23e4-163">Bu öğe, istemcinin iletişim kurduğu hizmetin URL 'sini temel alarak kullanmak üzere bir hizmet sertifikası yapılandırmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="b23e4-163">This element enables the client to configure a service certificate to use based on the URL of the service it communicates with.</span></span> <span data-ttu-id="b23e4-164">Bu özellikle, bir istemcinin birden çok hizmetle (bitiş hizmeti ve aracı güvenlik belirteci Hizmetleri) iletişim kuramadığı verilen belirteç senaryolarında kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="b23e4-164">This is especially useful in issued token scenarios where a client can be communicating to multiple services (the end service as well as intermediary security token services).</span></span> <span data-ttu-id="b23e4-165">Sertifika tabanlı ileti güvenliği kullanan bağlamalar için, bu sertifika hizmete iletileri şifrelemek için kullanılır ve istemciye yanıtları imzalamak için hizmet tarafından kullanılması beklenir.</span><span class="sxs-lookup"><span data-stu-id="b23e4-165">For bindings that use certificate-based message security, this certificate is used to encrypt messages to the service, and is expected to be used by the service for signing replies to the client.</span></span>  
  
 <span data-ttu-id="b23e4-166">Bir bağlama hizmet için bir sertifika gerektiriyorsa ve hizmet URL 'SI için belirli bir sertifika ScopedCertificates içinde bulunmazsa, varsayılan sertifika kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b23e4-166">If a binding requires a certificate for the service and no specific certificate for the service URL is found in the ScopedCertificates, the default certificate is used.</span></span>  
  
 <span data-ttu-id="b23e4-167">Daha fazla bilgi için bkz [. nasıl yapılır: Federasyon Istemcisi](../../../wcf/feature-details/how-to-create-a-federated-client.md)oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b23e4-167">For more information, see the "Scoped Certificates" section of [How to: Create a Federated Client](../../../wcf/feature-details/how-to-create-a-federated-client.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b23e4-168">Örnek</span><span class="sxs-lookup"><span data-stu-id="b23e4-168">Example</span></span>  
 <span data-ttu-id="b23e4-169">Aşağıdaki örnek, koleksiyonu bir X. 509.440 sertifikası ekler.</span><span class="sxs-lookup"><span data-stu-id="b23e4-169">The following example adds an X.509 certificate the collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b23e4-170">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b23e4-170">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>
- [<span data-ttu-id="b23e4-171">Nasıl yapılır: Federe Istemci oluşturma</span><span class="sxs-lookup"><span data-stu-id="b23e4-171">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="b23e4-172">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="b23e4-172">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="b23e4-173">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="b23e4-173">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="b23e4-174">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="b23e4-174">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
