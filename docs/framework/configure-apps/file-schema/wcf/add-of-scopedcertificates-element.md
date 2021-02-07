---
description: 'Hakkında daha fazla bilgi edinin: <add> <scopedCertificates> öğe'
title: <add><scopedCertificates>öğesinin
ms.date: 03/30/2017
ms.assetid: e21c1ef8-d6d6-4bca-ac5a-6fbf4bd77412
ms.openlocfilehash: 4c267164ccf065edee79a6aaaa9aaddc14d95909
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99750279"
---
# <a name="add-of-scopedcertificates-element"></a><span data-ttu-id="10575-103">\<add>\<scopedCertificates>öğesinin</span><span class="sxs-lookup"><span data-stu-id="10575-103">\<add> of \<scopedCertificates> Element</span></span>

<span data-ttu-id="10575-104">Kapsamlı sertifikalar koleksiyonuna bir X. 509.440 sertifikası ekler.</span><span class="sxs-lookup"><span data-stu-id="10575-104">Adds an X.509 certificate to the collection of scoped certificates.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<scopedCertificates>**](scopedcertificates-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="10575-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="10575-105">Syntax</span></span>  
  
```xml  
<add findValue="String"
     storeLocation="CurrentUser/LocalMachine"
     storeName=" CurrentUser/LocalMachine"
     targetUri="string"
     x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="10575-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="10575-106">Attributes and Elements</span></span>  

 <span data-ttu-id="10575-107">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="10575-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="10575-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="10575-108">Attributes</span></span>  
  
|<span data-ttu-id="10575-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="10575-109">Attribute</span></span>|<span data-ttu-id="10575-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="10575-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="10575-111">HedefUri</span><span class="sxs-lookup"><span data-stu-id="10575-111">targetUri</span></span>|<span data-ttu-id="10575-112">Dize.</span><span class="sxs-lookup"><span data-stu-id="10575-112">String.</span></span> <span data-ttu-id="10575-113">Sertifikayla ilişkili hizmetin URI 'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="10575-113">Specifies the URI of the service associated with the certificate.</span></span>|  
|<span data-ttu-id="10575-114">findValue</span><span class="sxs-lookup"><span data-stu-id="10575-114">findValue</span></span>|<span data-ttu-id="10575-115">Dize.</span><span class="sxs-lookup"><span data-stu-id="10575-115">String.</span></span> <span data-ttu-id="10575-116">Aranacak değer.</span><span class="sxs-lookup"><span data-stu-id="10575-116">The value to search for.</span></span>|  
|<span data-ttu-id="10575-117">x509FindType</span><span class="sxs-lookup"><span data-stu-id="10575-117">x509FindType</span></span>|<span data-ttu-id="10575-118">Listelenen.</span><span class="sxs-lookup"><span data-stu-id="10575-118">Enumeration.</span></span> <span data-ttu-id="10575-119">Arama yapılacak sertifika alanlarından biri.</span><span class="sxs-lookup"><span data-stu-id="10575-119">One of the certificate fields to search.</span></span>|  
|<span data-ttu-id="10575-120">storeLocation</span><span class="sxs-lookup"><span data-stu-id="10575-120">storeLocation</span></span>|<span data-ttu-id="10575-121">Listelenen.</span><span class="sxs-lookup"><span data-stu-id="10575-121">Enumeration.</span></span> <span data-ttu-id="10575-122">Arama yapılacak iki depolama konumundan biri.</span><span class="sxs-lookup"><span data-stu-id="10575-122">One of the two store locations to search.</span></span>|  
|<span data-ttu-id="10575-123">storeName</span><span class="sxs-lookup"><span data-stu-id="10575-123">storeName</span></span>|<span data-ttu-id="10575-124">Listelenen.</span><span class="sxs-lookup"><span data-stu-id="10575-124">Enumeration.</span></span> <span data-ttu-id="10575-125">Arama yapmak için sistem mağazalarından biri.</span><span class="sxs-lookup"><span data-stu-id="10575-125">One of the system stores to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="10575-126">findValue özniteliği</span><span class="sxs-lookup"><span data-stu-id="10575-126">findValue Attribute</span></span>  
  
|<span data-ttu-id="10575-127">Değer</span><span class="sxs-lookup"><span data-stu-id="10575-127">Value</span></span>|<span data-ttu-id="10575-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="10575-128">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="10575-129">Dize</span><span class="sxs-lookup"><span data-stu-id="10575-129">String</span></span>|<span data-ttu-id="10575-130">Değer, aranmakta olan alana bağlıdır (X509FindType özniteliğiyle belirtilir).</span><span class="sxs-lookup"><span data-stu-id="10575-130">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="10575-131">Örneğin, bir parmak izi arıyorsanız, değerin onaltılık sayı dizesi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="10575-131">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="10575-132">x509FindType özniteliği</span><span class="sxs-lookup"><span data-stu-id="10575-132">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="10575-133">Değer</span><span class="sxs-lookup"><span data-stu-id="10575-133">Value</span></span>|<span data-ttu-id="10575-134">Açıklama</span><span class="sxs-lookup"><span data-stu-id="10575-134">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="10575-135">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="10575-135">Enumeration</span></span>|<span data-ttu-id="10575-136">Değerler şunlardır: Findbyparmak izi, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, Findbytımenotyetvalid, FindBySerialNumber, Findbytimedoldu, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, Findbyexten, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="10575-136">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="10575-137">storeLocation özniteliği</span><span class="sxs-lookup"><span data-stu-id="10575-137">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="10575-138">Değer</span><span class="sxs-lookup"><span data-stu-id="10575-138">Value</span></span>|<span data-ttu-id="10575-139">Açıklama</span><span class="sxs-lookup"><span data-stu-id="10575-139">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="10575-140">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="10575-140">Enumeration</span></span>|<span data-ttu-id="10575-141">CurrentUser veya LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="10575-141">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="10575-142">storeName özniteliği</span><span class="sxs-lookup"><span data-stu-id="10575-142">storeName Attribute</span></span>  
  
|<span data-ttu-id="10575-143">Değer</span><span class="sxs-lookup"><span data-stu-id="10575-143">Value</span></span>|<span data-ttu-id="10575-144">Açıklama</span><span class="sxs-lookup"><span data-stu-id="10575-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="10575-145">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="10575-145">Enumeration</span></span>|<span data-ttu-id="10575-146">Değerler şunlardır: AddressBook, AuthRoot, CertificateAuthority, Izin verilmeyen, My, root, Trustedkişilerim ve TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="10575-146">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="10575-147">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="10575-147">Child Elements</span></span>  

 <span data-ttu-id="10575-148">Yok.</span><span class="sxs-lookup"><span data-stu-id="10575-148">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="10575-149">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="10575-149">Parent Elements</span></span>  
  
|<span data-ttu-id="10575-150">Öğe</span><span class="sxs-lookup"><span data-stu-id="10575-150">Element</span></span>|<span data-ttu-id="10575-151">Açıklama</span><span class="sxs-lookup"><span data-stu-id="10575-151">Description</span></span>|  
|-------------|-----------------|  
|[\<scopedCertificates>](scopedcertificates-element.md)|<span data-ttu-id="10575-152">Kimlik doğrulama için belirli hizmetler (kapsamlı) tarafından sunulan X. 509.440 sertifikalarının bir koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="10575-152">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="10575-153">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="10575-153">Remarks</span></span>  

 <span data-ttu-id="10575-154">Bu öğe, istemcinin iletişim kurduğu hizmetin URL 'sini temel alarak kullanmak üzere bir hizmet sertifikası yapılandırmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="10575-154">This element enables the client to configure a service certificate to use based on the URL of the service it communicates with.</span></span> <span data-ttu-id="10575-155">Bu özellikle, bir istemcinin birden çok hizmetle (bitiş hizmeti ve aracı güvenlik belirteci Hizmetleri) iletişim kuramadığı verilen belirteç senaryolarında kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="10575-155">This is especially useful in issued token scenarios where a client can be communicating to multiple services (the end service as well as intermediary security token services).</span></span> <span data-ttu-id="10575-156">Sertifika tabanlı ileti güvenliği kullanan bağlamalar için, bu sertifika hizmete iletileri şifrelemek için kullanılır ve istemciye yanıtları imzalamak için hizmet tarafından kullanılması beklenir.</span><span class="sxs-lookup"><span data-stu-id="10575-156">For bindings that use certificate-based message security, this certificate is used to encrypt messages to the service, and is expected to be used by the service for signing replies to the client.</span></span>  
  
 <span data-ttu-id="10575-157">Bir bağlama hizmet için bir sertifika gerektiriyorsa ve hizmet URL 'SI için belirli bir sertifika ScopedCertificates içinde bulunmazsa, varsayılan sertifika kullanılır.</span><span class="sxs-lookup"><span data-stu-id="10575-157">If a binding requires a certificate for the service and no specific certificate for the service URL is found in the ScopedCertificates, the default certificate is used.</span></span>  
  
 <span data-ttu-id="10575-158">Daha fazla bilgi için bkz. [nasıl yapılır: federe Istemci oluşturma](../../../wcf/feature-details/how-to-create-a-federated-client.md)konusunun "kapsamlı sertifikalar" bölümü.</span><span class="sxs-lookup"><span data-stu-id="10575-158">For more information, see the "Scoped Certificates" section of [How to: Create a Federated Client](../../../wcf/feature-details/how-to-create-a-federated-client.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="10575-159">Örnek</span><span class="sxs-lookup"><span data-stu-id="10575-159">Example</span></span>  

 <span data-ttu-id="10575-160">Aşağıdaki örnek, koleksiyonu bir X. 509.440 sertifikası ekler.</span><span class="sxs-lookup"><span data-stu-id="10575-160">The following example adds an X.509 certificate the collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="10575-161">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="10575-161">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>
- [<span data-ttu-id="10575-162">Nasıl yapılır: Federe İstemci Oluşturma</span><span class="sxs-lookup"><span data-stu-id="10575-162">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="10575-163">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="10575-163">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="10575-164">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="10575-164">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="10575-165">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="10575-165">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
