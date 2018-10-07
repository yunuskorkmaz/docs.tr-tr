---
title: '&lt;defaultCertificate&gt; Öğesi'
ms.date: 03/30/2017
ms.assetid: f1ddf364-9a00-45d3-b989-ff381c154ce6
ms.openlocfilehash: 9b99ee36fdb924ea12f3023984a3aa4b590937e8
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2018
ms.locfileid: "48847860"
---
# <a name="ltdefaultcertificategt-element"></a><span data-ttu-id="c81d9-102">&lt;defaultCertificate&gt; Öğesi</span><span class="sxs-lookup"><span data-stu-id="c81d9-102">&lt;defaultCertificate&gt; Element</span></span>
<span data-ttu-id="c81d9-103">Kullanılacak olan X.509 sertifikasını belirtir, STS veya hizmetin sağlamadığı anlaşma protokolü aracılığıyla.</span><span class="sxs-lookup"><span data-stu-id="c81d9-103">Specifies an X.509 certificate to be used when a service or STS does not provide one via a negotiation protocol.</span></span>  
  
 <span data-ttu-id="c81d9-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c81d9-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="c81d9-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="c81d9-105">\<behaviors></span></span>  
<span data-ttu-id="c81d9-106">endpointBehaviors bölümü</span><span class="sxs-lookup"><span data-stu-id="c81d9-106">endpointBehaviors section</span></span>  
<span data-ttu-id="c81d9-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="c81d9-107">\<behavior></span></span>  
<span data-ttu-id="c81d9-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="c81d9-108">\<clientCredentials></span></span>  
<span data-ttu-id="c81d9-109">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="c81d9-109">\<serviceCertificate></span></span>  
<span data-ttu-id="c81d9-110">\<defaultCertificate ></span><span class="sxs-lookup"><span data-stu-id="c81d9-110">\<defaultCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c81d9-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c81d9-111">Syntax</span></span>  
  
```xml  
<defaultCertificate findValue="String"   
storeLocation=" CurrentUser/LocalMachine"  
storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"   
x509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialiNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c81d9-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c81d9-112">Attributes and Elements</span></span>  
 <span data-ttu-id="c81d9-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c81d9-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c81d9-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c81d9-114">Attributes</span></span>  
  
|<span data-ttu-id="c81d9-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c81d9-115">Attribute</span></span>|<span data-ttu-id="c81d9-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c81d9-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c81d9-117">findValue</span><span class="sxs-lookup"><span data-stu-id="c81d9-117">findValue</span></span>|<span data-ttu-id="c81d9-118">dize.</span><span class="sxs-lookup"><span data-stu-id="c81d9-118">String.</span></span> <span data-ttu-id="c81d9-119">Aranacak değer.</span><span class="sxs-lookup"><span data-stu-id="c81d9-119">The value to search for.</span></span>|  
|<span data-ttu-id="c81d9-120">X509FindType</span><span class="sxs-lookup"><span data-stu-id="c81d9-120">x509FindType</span></span>|<span data-ttu-id="c81d9-121">Sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="c81d9-121">Enumeration.</span></span> <span data-ttu-id="c81d9-122">Aranacak sertifika alanlardan biri.</span><span class="sxs-lookup"><span data-stu-id="c81d9-122">One of the certificate fields to search.</span></span>|  
|<span data-ttu-id="c81d9-123">storeLocation</span><span class="sxs-lookup"><span data-stu-id="c81d9-123">storeLocation</span></span>|<span data-ttu-id="c81d9-124">Sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="c81d9-124">Enumeration.</span></span> <span data-ttu-id="c81d9-125">İki sistem depolama biri Aranacak Konum.</span><span class="sxs-lookup"><span data-stu-id="c81d9-125">One of the two system store locations to search.</span></span>|  
|<span data-ttu-id="c81d9-126">storeName</span><span class="sxs-lookup"><span data-stu-id="c81d9-126">storeName</span></span>|<span data-ttu-id="c81d9-127">Sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="c81d9-127">Enumeration.</span></span> <span data-ttu-id="c81d9-128">Aranacak bir sistemin depolar.</span><span class="sxs-lookup"><span data-stu-id="c81d9-128">One of the system stores to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="c81d9-129">findValue özniteliği</span><span class="sxs-lookup"><span data-stu-id="c81d9-129">findValue Attribute</span></span>  
  
|<span data-ttu-id="c81d9-130">Değer</span><span class="sxs-lookup"><span data-stu-id="c81d9-130">Value</span></span>|<span data-ttu-id="c81d9-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c81d9-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c81d9-132">Dize</span><span class="sxs-lookup"><span data-stu-id="c81d9-132">String</span></span>|<span data-ttu-id="c81d9-133">Değer (X509FindType özniteliği tarafından belirtilen) alan bağlıdır Aranan.</span><span class="sxs-lookup"><span data-stu-id="c81d9-133">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="c81d9-134">Örneğin, bir parmak izi için arama değeri bir dize onaltılık bir sayı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c81d9-134">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="c81d9-135">x509FindType özniteliği</span><span class="sxs-lookup"><span data-stu-id="c81d9-135">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="c81d9-136">Değer</span><span class="sxs-lookup"><span data-stu-id="c81d9-136">Value</span></span>|<span data-ttu-id="c81d9-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c81d9-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c81d9-138">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="c81d9-138">Enumeration</span></span>|<span data-ttu-id="c81d9-139">Değerler: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="c81d9-139">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="c81d9-140">storeLocation özniteliği</span><span class="sxs-lookup"><span data-stu-id="c81d9-140">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="c81d9-141">Değer</span><span class="sxs-lookup"><span data-stu-id="c81d9-141">Value</span></span>|<span data-ttu-id="c81d9-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c81d9-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c81d9-143">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="c81d9-143">Enumeration</span></span>|<span data-ttu-id="c81d9-144">LocalMachine ya da CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="c81d9-144">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="c81d9-145">storeName özniteliği</span><span class="sxs-lookup"><span data-stu-id="c81d9-145">storeName Attribute</span></span>  
  
|<span data-ttu-id="c81d9-146">Değer</span><span class="sxs-lookup"><span data-stu-id="c81d9-146">Value</span></span>|<span data-ttu-id="c81d9-147">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c81d9-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c81d9-148">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="c81d9-148">Enumeration</span></span>|<span data-ttu-id="c81d9-149">Değerler: adres defteri, AuthRoot, CertificateAuthority izin verilmeyen, My, kök ve TrustedPeople TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="c81d9-149">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c81d9-150">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c81d9-150">Child Elements</span></span>  
 <span data-ttu-id="c81d9-151">Yok.</span><span class="sxs-lookup"><span data-stu-id="c81d9-151">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c81d9-152">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c81d9-152">Parent Elements</span></span>  
  
|<span data-ttu-id="c81d9-153">Öğe</span><span class="sxs-lookup"><span data-stu-id="c81d9-153">Element</span></span>|<span data-ttu-id="c81d9-154">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c81d9-154">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c81d9-155">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="c81d9-155">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="c81d9-156">İstemci bir hizmete kimlik doğrulaması yapılırken kullanılacak sertifikayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="c81d9-156">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c81d9-157">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c81d9-157">Remarks</span></span>  
 <span data-ttu-id="c81d9-158">Sertifika tabanlı ileti güvenliği kullanan bağlamaları için bu yapılandırma öğesi tarafından belirtilen sertifika hizmeti iletileri şifrelemek için kullanılır ve istemciye yanıt imzalama için hizmet tarafından kullanılmak üzere bekleniyor.</span><span class="sxs-lookup"><span data-stu-id="c81d9-158">For bindings that use certificate-based message security, certificate specified by this configuration element is used to encrypt messages to the service and is expected to be used by the service for signing replies to the client.</span></span> <span data-ttu-id="c81d9-159">Bu sertifika bir hizmet tarafından belirtildiğinde kullanılacak tek bir sertifika depolar.</span><span class="sxs-lookup"><span data-stu-id="c81d9-159">It stores a single certificate to be used when no certificate is specified by a service.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c81d9-160">Örnek</span><span class="sxs-lookup"><span data-stu-id="c81d9-160">Example</span></span>  
 <span data-ttu-id="c81d9-161">Aşağıdaki örnek, URI ile başlayan uç noktalar için kullanılacak sertifikayı belirtir `http://www.contoso.com` ve sertifika anlaşmasını gerçekleştiren değil tüm diğer uç noktalar için kullanılacak bir sertifika.</span><span class="sxs-lookup"><span data-stu-id="c81d9-161">The following example specifies a certificate to use for endpoints whose URI begins with `http://www.contoso.com` and a certificate to use for all other endpoints that do not perform certificate negotiation.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c81d9-162">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c81d9-162">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.X509DefaultServiceCertificateElement>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.DefaultCertificate%2A>  
 [<span data-ttu-id="c81d9-163">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="c81d9-163">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="c81d9-164">\<kimlik doğrulama ></span><span class="sxs-lookup"><span data-stu-id="c81d9-164">\<authentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md)  
 [<span data-ttu-id="c81d9-165">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="c81d9-165">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="c81d9-166">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="c81d9-166">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
