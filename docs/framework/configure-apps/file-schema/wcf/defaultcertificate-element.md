---
title: '&lt;defaultCertificate&gt; Öğesi'
ms.date: 03/30/2017
ms.assetid: f1ddf364-9a00-45d3-b989-ff381c154ce6
ms.openlocfilehash: a4af1c6ec452b24634fa50162fa71f069e2451f5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32751018"
---
# <a name="ltdefaultcertificategt-element"></a><span data-ttu-id="e42e8-102">&lt;defaultCertificate&gt; Öğesi</span><span class="sxs-lookup"><span data-stu-id="e42e8-102">&lt;defaultCertificate&gt; Element</span></span>
<span data-ttu-id="e42e8-103">Kullanılacak bir X.509 sertifikası belirtir ne zaman bir hizmeti veya STS sağlamaz anlaşması protokolü aracılığıyla bir.</span><span class="sxs-lookup"><span data-stu-id="e42e8-103">Specifies an X.509 certificate to be used when a service or STS does not provide one via a negotiation protocol.</span></span>  
  
 <span data-ttu-id="e42e8-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e42e8-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e42e8-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="e42e8-105">\<behaviors></span></span>  
<span data-ttu-id="e42e8-106">endpointBehaviors bölümü</span><span class="sxs-lookup"><span data-stu-id="e42e8-106">endpointBehaviors section</span></span>  
<span data-ttu-id="e42e8-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="e42e8-107">\<behavior></span></span>  
<span data-ttu-id="e42e8-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="e42e8-108">\<clientCredentials></span></span>  
<span data-ttu-id="e42e8-109">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="e42e8-109">\<serviceCertificate></span></span>  
<span data-ttu-id="e42e8-110">\<defaultCertificate ></span><span class="sxs-lookup"><span data-stu-id="e42e8-110">\<defaultCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e42e8-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e42e8-111">Syntax</span></span>  
  
```xml  
<defaultCertificate findValue="String"   
storeLocation=" CurrentUser/LocalMachine"  
storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"   
x509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialiNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e42e8-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e42e8-112">Attributes and Elements</span></span>  
 <span data-ttu-id="e42e8-113">Öznitelikler, alt öğelerini ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır</span><span class="sxs-lookup"><span data-stu-id="e42e8-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e42e8-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e42e8-114">Attributes</span></span>  
  
|<span data-ttu-id="e42e8-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e42e8-115">Attribute</span></span>|<span data-ttu-id="e42e8-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e42e8-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e42e8-117">findValue</span><span class="sxs-lookup"><span data-stu-id="e42e8-117">findValue</span></span>|<span data-ttu-id="e42e8-118">Dize.</span><span class="sxs-lookup"><span data-stu-id="e42e8-118">String.</span></span> <span data-ttu-id="e42e8-119">Aranacak değer.</span><span class="sxs-lookup"><span data-stu-id="e42e8-119">The value to search for.</span></span>|  
|<span data-ttu-id="e42e8-120">X509FindType</span><span class="sxs-lookup"><span data-stu-id="e42e8-120">x509FindType</span></span>|<span data-ttu-id="e42e8-121">Sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="e42e8-121">Enumeration.</span></span> <span data-ttu-id="e42e8-122">Aranacak sertifika alanlardan biri.</span><span class="sxs-lookup"><span data-stu-id="e42e8-122">One of the certificate fields to search.</span></span>|  
|<span data-ttu-id="e42e8-123">storeLocation</span><span class="sxs-lookup"><span data-stu-id="e42e8-123">storeLocation</span></span>|<span data-ttu-id="e42e8-124">Sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="e42e8-124">Enumeration.</span></span> <span data-ttu-id="e42e8-125">İki sistem birini aramak için konuma depolayın.</span><span class="sxs-lookup"><span data-stu-id="e42e8-125">One of the two system store locations to search.</span></span>|  
|<span data-ttu-id="e42e8-126">storeName</span><span class="sxs-lookup"><span data-stu-id="e42e8-126">storeName</span></span>|<span data-ttu-id="e42e8-127">Sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="e42e8-127">Enumeration.</span></span> <span data-ttu-id="e42e8-128">Sistem aramak için depolar.</span><span class="sxs-lookup"><span data-stu-id="e42e8-128">One of the system stores to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="e42e8-129">findValue özniteliği</span><span class="sxs-lookup"><span data-stu-id="e42e8-129">findValue Attribute</span></span>  
  
|<span data-ttu-id="e42e8-130">Değer</span><span class="sxs-lookup"><span data-stu-id="e42e8-130">Value</span></span>|<span data-ttu-id="e42e8-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e42e8-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e42e8-132">Dize</span><span class="sxs-lookup"><span data-stu-id="e42e8-132">String</span></span>|<span data-ttu-id="e42e8-133">Değer (X509FindType özniteliği tarafından belirtilen) alan bağlıdır Aranmakta.</span><span class="sxs-lookup"><span data-stu-id="e42e8-133">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="e42e8-134">Örneğin, bir parmak izi için arama değeri bir onaltılık sayı dizesi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e42e8-134">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="e42e8-135">x509FindType özniteliği</span><span class="sxs-lookup"><span data-stu-id="e42e8-135">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="e42e8-136">Değer</span><span class="sxs-lookup"><span data-stu-id="e42e8-136">Value</span></span>|<span data-ttu-id="e42e8-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e42e8-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e42e8-138">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="e42e8-138">Enumeration</span></span>|<span data-ttu-id="e42e8-139">Değerler şunlardır: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="e42e8-139">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="e42e8-140">storeLocation özniteliği</span><span class="sxs-lookup"><span data-stu-id="e42e8-140">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="e42e8-141">Değer</span><span class="sxs-lookup"><span data-stu-id="e42e8-141">Value</span></span>|<span data-ttu-id="e42e8-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e42e8-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e42e8-143">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="e42e8-143">Enumeration</span></span>|<span data-ttu-id="e42e8-144">Currentuser'a veya LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="e42e8-144">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="e42e8-145">storeName özniteliği</span><span class="sxs-lookup"><span data-stu-id="e42e8-145">storeName Attribute</span></span>  
  
|<span data-ttu-id="e42e8-146">Değer</span><span class="sxs-lookup"><span data-stu-id="e42e8-146">Value</span></span>|<span data-ttu-id="e42e8-147">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e42e8-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e42e8-148">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="e42e8-148">Enumeration</span></span>|<span data-ttu-id="e42e8-149">Değerler: adres defteri, AuthRoot, sertifika yetkilisi, izin verilmeyen, My, kök, TrustedPeople ve TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="e42e8-149">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e42e8-150">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e42e8-150">Child Elements</span></span>  
 <span data-ttu-id="e42e8-151">Yok.</span><span class="sxs-lookup"><span data-stu-id="e42e8-151">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e42e8-152">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e42e8-152">Parent Elements</span></span>  
  
|<span data-ttu-id="e42e8-153">Öğe</span><span class="sxs-lookup"><span data-stu-id="e42e8-153">Element</span></span>|<span data-ttu-id="e42e8-154">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e42e8-154">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e42e8-155">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="e42e8-155">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="e42e8-156">İstemci bir hizmete kimlik doğrulanırken kullanılacak bir sertifika belirtir.</span><span class="sxs-lookup"><span data-stu-id="e42e8-156">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e42e8-157">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e42e8-157">Remarks</span></span>  
 <span data-ttu-id="e42e8-158">Sertifika tabanlı ileti güvenliği kullanan bağlamaları için bu yapılandırma öğesi tarafından belirtilen sertifika hizmet iletileri şifrelemek için kullanılır ve istemciye yanıt imzalama hizmeti tarafından kullanılacak beklenmektedir.</span><span class="sxs-lookup"><span data-stu-id="e42e8-158">For bindings that use certificate-based message security, certificate specified by this configuration element is used to encrypt messages to the service and is expected to be used by the service for signing replies to the client.</span></span> <span data-ttu-id="e42e8-159">Sertifika bir hizmet tarafından belirtildiğinde kullanılacak tek bir sertifika depolar.</span><span class="sxs-lookup"><span data-stu-id="e42e8-159">It stores a single certificate to be used when no certificate is specified by a service.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e42e8-160">Örnek</span><span class="sxs-lookup"><span data-stu-id="e42e8-160">Example</span></span>  
 <span data-ttu-id="e42e8-161">Aşağıdaki örnek, URI başlıyorsa uç noktalar için kullanılacak bir sertifika belirtir http://www.contoso.com ve sertifikası anlaşması gerçekleştiren değil tüm diğer uç noktalar için kullanılacak bir sertifika.</span><span class="sxs-lookup"><span data-stu-id="e42e8-161">The following example specifies a certificate to use for endpoints whose URI begins with http://www.contoso.com and a certificate to use for all other endpoints that do not perform certificate negotiation.</span></span>  
  
```xml  
<serviceCertificate>  
  <defaultCertificate findValue="www.contoso.com"   
                      storeLocation="LocalMachine"  
                      storeName="TrustedPeople"   
                      x509FindType="FindByIssuerDistinguishedName" />  
  <scopedCertificates>  
     <add targetUri="http://www.contoso.com"   
          findValue="www.contoso.com" storeLocation="LocalMachine"  
                  storeName="Root" x509FindType="FindByIssuerName" />  
  </scopedCertificates>  
  <authentication revocationMode="Online"   
   trustedStoreLocation="LocalMachine" />  
</serviceCertificate>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e42e8-162">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e42e8-162">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.X509DefaultServiceCertificateElement>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.DefaultCertificate%2A>  
 [<span data-ttu-id="e42e8-163">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="e42e8-163">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="e42e8-164">\<kimlik doğrulama ></span><span class="sxs-lookup"><span data-stu-id="e42e8-164">\<authentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md)  
 [<span data-ttu-id="e42e8-165">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="e42e8-165">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="e42e8-166">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="e42e8-166">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
