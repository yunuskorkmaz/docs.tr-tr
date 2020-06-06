---
title: <add><scopedCertificates>öğesinin
ms.date: 03/30/2017
ms.assetid: e21c1ef8-d6d6-4bca-ac5a-6fbf4bd77412
ms.openlocfilehash: b00a342108beca69a906fbf6212915768e98778f
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398339"
---
# <a name="add-of-scopedcertificates-element"></a><span data-ttu-id="f2f78-102">\<add>\<scopedCertificates>öğesinin</span><span class="sxs-lookup"><span data-stu-id="f2f78-102">\<add> of \<scopedCertificates> Element</span></span>
<span data-ttu-id="f2f78-103">Kapsamlı sertifikalar koleksiyonuna bir X. 509.440 sertifikası ekler.</span><span class="sxs-lookup"><span data-stu-id="f2f78-103">Adds an X.509 certificate to the collection of scoped certificates.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<scopedCertificates>**](scopedcertificates-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="f2f78-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f2f78-104">Syntax</span></span>  
  
```xml  
<add findValue="String"
     storeLocation="CurrentUser/LocalMachine"
     storeName=" CurrentUser/LocalMachine"
     targetUri="string"
     x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f2f78-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f2f78-105">Attributes and Elements</span></span>  
 <span data-ttu-id="f2f78-106">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="f2f78-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f2f78-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f2f78-107">Attributes</span></span>  
  
|<span data-ttu-id="f2f78-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f2f78-108">Attribute</span></span>|<span data-ttu-id="f2f78-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f2f78-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f2f78-110">HedefUri</span><span class="sxs-lookup"><span data-stu-id="f2f78-110">targetUri</span></span>|<span data-ttu-id="f2f78-111">Dize.</span><span class="sxs-lookup"><span data-stu-id="f2f78-111">String.</span></span> <span data-ttu-id="f2f78-112">Sertifikayla ilişkili hizmetin URI 'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f2f78-112">Specifies the URI of the service associated with the certificate.</span></span>|  
|<span data-ttu-id="f2f78-113">findValue</span><span class="sxs-lookup"><span data-stu-id="f2f78-113">findValue</span></span>|<span data-ttu-id="f2f78-114">Dize.</span><span class="sxs-lookup"><span data-stu-id="f2f78-114">String.</span></span> <span data-ttu-id="f2f78-115">Aranacak değer.</span><span class="sxs-lookup"><span data-stu-id="f2f78-115">The value to search for.</span></span>|  
|<span data-ttu-id="f2f78-116">x509FindType</span><span class="sxs-lookup"><span data-stu-id="f2f78-116">x509FindType</span></span>|<span data-ttu-id="f2f78-117">Listelenen.</span><span class="sxs-lookup"><span data-stu-id="f2f78-117">Enumeration.</span></span> <span data-ttu-id="f2f78-118">Arama yapılacak sertifika alanlarından biri.</span><span class="sxs-lookup"><span data-stu-id="f2f78-118">One of the certificate fields to search.</span></span>|  
|<span data-ttu-id="f2f78-119">storeLocation</span><span class="sxs-lookup"><span data-stu-id="f2f78-119">storeLocation</span></span>|<span data-ttu-id="f2f78-120">Listelenen.</span><span class="sxs-lookup"><span data-stu-id="f2f78-120">Enumeration.</span></span> <span data-ttu-id="f2f78-121">Arama yapılacak iki depolama konumundan biri.</span><span class="sxs-lookup"><span data-stu-id="f2f78-121">One of the two store locations to search.</span></span>|  
|<span data-ttu-id="f2f78-122">storeName</span><span class="sxs-lookup"><span data-stu-id="f2f78-122">storeName</span></span>|<span data-ttu-id="f2f78-123">Listelenen.</span><span class="sxs-lookup"><span data-stu-id="f2f78-123">Enumeration.</span></span> <span data-ttu-id="f2f78-124">Arama yapmak için sistem mağazalarından biri.</span><span class="sxs-lookup"><span data-stu-id="f2f78-124">One of the system stores to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="f2f78-125">findValue özniteliği</span><span class="sxs-lookup"><span data-stu-id="f2f78-125">findValue Attribute</span></span>  
  
|<span data-ttu-id="f2f78-126">Değer</span><span class="sxs-lookup"><span data-stu-id="f2f78-126">Value</span></span>|<span data-ttu-id="f2f78-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f2f78-127">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f2f78-128">Dize</span><span class="sxs-lookup"><span data-stu-id="f2f78-128">String</span></span>|<span data-ttu-id="f2f78-129">Değer, aranmakta olan alana bağlıdır (X509FindType özniteliğiyle belirtilir).</span><span class="sxs-lookup"><span data-stu-id="f2f78-129">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="f2f78-130">Örneğin, bir parmak izi arıyorsanız, değerin onaltılık sayı dizesi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f2f78-130">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="f2f78-131">x509FindType özniteliği</span><span class="sxs-lookup"><span data-stu-id="f2f78-131">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="f2f78-132">Değer</span><span class="sxs-lookup"><span data-stu-id="f2f78-132">Value</span></span>|<span data-ttu-id="f2f78-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f2f78-133">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f2f78-134">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="f2f78-134">Enumeration</span></span>|<span data-ttu-id="f2f78-135">Değerler şunlardır: Findbyparmak izi, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, Findbytımenotyetvalid, FindBySerialNumber, Findbytimedoldu, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, Findbyexten, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="f2f78-135">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="f2f78-136">storeLocation özniteliği</span><span class="sxs-lookup"><span data-stu-id="f2f78-136">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="f2f78-137">Değer</span><span class="sxs-lookup"><span data-stu-id="f2f78-137">Value</span></span>|<span data-ttu-id="f2f78-138">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f2f78-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f2f78-139">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="f2f78-139">Enumeration</span></span>|<span data-ttu-id="f2f78-140">CurrentUser veya LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="f2f78-140">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="f2f78-141">storeName özniteliği</span><span class="sxs-lookup"><span data-stu-id="f2f78-141">storeName Attribute</span></span>  
  
|<span data-ttu-id="f2f78-142">Değer</span><span class="sxs-lookup"><span data-stu-id="f2f78-142">Value</span></span>|<span data-ttu-id="f2f78-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f2f78-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f2f78-144">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="f2f78-144">Enumeration</span></span>|<span data-ttu-id="f2f78-145">Değerler şunlardır: AddressBook, AuthRoot, CertificateAuthority, Izin verilmeyen, My, root, Trustedkişilerim ve TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="f2f78-145">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f2f78-146">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f2f78-146">Child Elements</span></span>  
 <span data-ttu-id="f2f78-147">Yok.</span><span class="sxs-lookup"><span data-stu-id="f2f78-147">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f2f78-148">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f2f78-148">Parent Elements</span></span>  
  
|<span data-ttu-id="f2f78-149">Öğe</span><span class="sxs-lookup"><span data-stu-id="f2f78-149">Element</span></span>|<span data-ttu-id="f2f78-150">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f2f78-150">Description</span></span>|  
|-------------|-----------------|  
|[\<scopedCertificates>](scopedcertificates-element.md)|<span data-ttu-id="f2f78-151">Kimlik doğrulama için belirli hizmetler (kapsamlı) tarafından sunulan X. 509.440 sertifikalarının bir koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f2f78-151">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f2f78-152">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f2f78-152">Remarks</span></span>  
 <span data-ttu-id="f2f78-153">Bu öğe, istemcinin iletişim kurduğu hizmetin URL 'sini temel alarak kullanmak üzere bir hizmet sertifikası yapılandırmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="f2f78-153">This element enables the client to configure a service certificate to use based on the URL of the service it communicates with.</span></span> <span data-ttu-id="f2f78-154">Bu özellikle, bir istemcinin birden çok hizmetle (bitiş hizmeti ve aracı güvenlik belirteci Hizmetleri) iletişim kuramadığı verilen belirteç senaryolarında kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="f2f78-154">This is especially useful in issued token scenarios where a client can be communicating to multiple services (the end service as well as intermediary security token services).</span></span> <span data-ttu-id="f2f78-155">Sertifika tabanlı ileti güvenliği kullanan bağlamalar için, bu sertifika hizmete iletileri şifrelemek için kullanılır ve istemciye yanıtları imzalamak için hizmet tarafından kullanılması beklenir.</span><span class="sxs-lookup"><span data-stu-id="f2f78-155">For bindings that use certificate-based message security, this certificate is used to encrypt messages to the service, and is expected to be used by the service for signing replies to the client.</span></span>  
  
 <span data-ttu-id="f2f78-156">Bir bağlama hizmet için bir sertifika gerektiriyorsa ve hizmet URL 'SI için belirli bir sertifika ScopedCertificates içinde bulunmazsa, varsayılan sertifika kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f2f78-156">If a binding requires a certificate for the service and no specific certificate for the service URL is found in the ScopedCertificates, the default certificate is used.</span></span>  
  
 <span data-ttu-id="f2f78-157">Daha fazla bilgi için bkz. [nasıl yapılır: federe Istemci oluşturma](../../../wcf/feature-details/how-to-create-a-federated-client.md)konusunun "kapsamlı sertifikalar" bölümü.</span><span class="sxs-lookup"><span data-stu-id="f2f78-157">For more information, see the "Scoped Certificates" section of [How to: Create a Federated Client](../../../wcf/feature-details/how-to-create-a-federated-client.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f2f78-158">Örnek</span><span class="sxs-lookup"><span data-stu-id="f2f78-158">Example</span></span>  
 <span data-ttu-id="f2f78-159">Aşağıdaki örnek, koleksiyonu bir X. 509.440 sertifikası ekler.</span><span class="sxs-lookup"><span data-stu-id="f2f78-159">The following example adds an X.509 certificate the collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f2f78-160">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f2f78-160">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>
- [<span data-ttu-id="f2f78-161">Nasıl yapılır: Federe İstemci Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f2f78-161">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="f2f78-162">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="f2f78-162">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="f2f78-163">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="f2f78-163">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="f2f78-164">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="f2f78-164">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
