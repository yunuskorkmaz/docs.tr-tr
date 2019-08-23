---
title: <defaultCertificate> Öğesi
ms.date: 03/30/2017
ms.assetid: f1ddf364-9a00-45d3-b989-ff381c154ce6
ms.openlocfilehash: 93410e815a156f91db1962f05fb1aa6baca7f955
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919245"
---
# <a name="defaultcertificate-element"></a><span data-ttu-id="c9767-102">\<defaultCertificate > öğesi</span><span class="sxs-lookup"><span data-stu-id="c9767-102">\<defaultCertificate> Element</span></span>
<span data-ttu-id="c9767-103">Bir hizmet veya STS bir anlaşma protokolü aracılığıyla bir tane sağlamıyorsa kullanılacak bir X. 509.952 sertifikası belirtir.</span><span class="sxs-lookup"><span data-stu-id="c9767-103">Specifies an X.509 certificate to be used when a service or STS does not provide one via a negotiation protocol.</span></span>  
  
 <span data-ttu-id="c9767-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c9767-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="c9767-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="c9767-105">\<behaviors></span></span>  
<span data-ttu-id="c9767-106">Endpointdavranışlar bölümü</span><span class="sxs-lookup"><span data-stu-id="c9767-106">endpointBehaviors section</span></span>  
<span data-ttu-id="c9767-107">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="c9767-107">\<behavior></span></span>  
<span data-ttu-id="c9767-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="c9767-108">\<clientCredentials></span></span>  
<span data-ttu-id="c9767-109">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="c9767-109">\<serviceCertificate></span></span>  
<span data-ttu-id="c9767-110">\<defaultCertificate ></span><span class="sxs-lookup"><span data-stu-id="c9767-110">\<defaultCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9767-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c9767-111">Syntax</span></span>  
  
```xml  
<defaultCertificate findValue="String"
                    storeLocation=" CurrentUser/LocalMachine"
                    storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                    x509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialiNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c9767-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c9767-112">Attributes and Elements</span></span>  
 <span data-ttu-id="c9767-113">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="c9767-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c9767-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c9767-114">Attributes</span></span>  
  
|<span data-ttu-id="c9767-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c9767-115">Attribute</span></span>|<span data-ttu-id="c9767-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c9767-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c9767-117">findValue</span><span class="sxs-lookup"><span data-stu-id="c9767-117">findValue</span></span>|<span data-ttu-id="c9767-118">Dizisinde.</span><span class="sxs-lookup"><span data-stu-id="c9767-118">String.</span></span> <span data-ttu-id="c9767-119">Aranacak değer.</span><span class="sxs-lookup"><span data-stu-id="c9767-119">The value to search for.</span></span>|  
|<span data-ttu-id="c9767-120">x509FindType</span><span class="sxs-lookup"><span data-stu-id="c9767-120">x509FindType</span></span>|<span data-ttu-id="c9767-121">Listelenen.</span><span class="sxs-lookup"><span data-stu-id="c9767-121">Enumeration.</span></span> <span data-ttu-id="c9767-122">Arama yapılacak sertifika alanlarından biri.</span><span class="sxs-lookup"><span data-stu-id="c9767-122">One of the certificate fields to search.</span></span>|  
|<span data-ttu-id="c9767-123">storeLocation</span><span class="sxs-lookup"><span data-stu-id="c9767-123">storeLocation</span></span>|<span data-ttu-id="c9767-124">Listelenen.</span><span class="sxs-lookup"><span data-stu-id="c9767-124">Enumeration.</span></span> <span data-ttu-id="c9767-125">Aranacak iki sistem depolama konumundan biri.</span><span class="sxs-lookup"><span data-stu-id="c9767-125">One of the two system store locations to search.</span></span>|  
|<span data-ttu-id="c9767-126">storeName</span><span class="sxs-lookup"><span data-stu-id="c9767-126">storeName</span></span>|<span data-ttu-id="c9767-127">Listelenen.</span><span class="sxs-lookup"><span data-stu-id="c9767-127">Enumeration.</span></span> <span data-ttu-id="c9767-128">Arama yapmak için sistem mağazalarından biri.</span><span class="sxs-lookup"><span data-stu-id="c9767-128">One of the system stores to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="c9767-129">findValue özniteliği</span><span class="sxs-lookup"><span data-stu-id="c9767-129">findValue Attribute</span></span>  
  
|<span data-ttu-id="c9767-130">Değer</span><span class="sxs-lookup"><span data-stu-id="c9767-130">Value</span></span>|<span data-ttu-id="c9767-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c9767-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c9767-132">Dize</span><span class="sxs-lookup"><span data-stu-id="c9767-132">String</span></span>|<span data-ttu-id="c9767-133">Değer, aranmakta olan alana bağlıdır (X509FindType özniteliğiyle belirtilir).</span><span class="sxs-lookup"><span data-stu-id="c9767-133">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="c9767-134">Örneğin, bir parmak izi arıyorsanız, değerin onaltılık sayı dizesi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c9767-134">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="c9767-135">x509FindType özniteliği</span><span class="sxs-lookup"><span data-stu-id="c9767-135">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="c9767-136">Değer</span><span class="sxs-lookup"><span data-stu-id="c9767-136">Value</span></span>|<span data-ttu-id="c9767-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c9767-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c9767-138">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="c9767-138">Enumeration</span></span>|<span data-ttu-id="c9767-139">Değerler şunlardır: Findbyparmak izi, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, Findbytımenotyetvalid, FindBySerialNumber, Findbytimedoldu, FindByTemplateName , FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="c9767-139">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="c9767-140">storeLocation özniteliği</span><span class="sxs-lookup"><span data-stu-id="c9767-140">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="c9767-141">Değer</span><span class="sxs-lookup"><span data-stu-id="c9767-141">Value</span></span>|<span data-ttu-id="c9767-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c9767-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c9767-143">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="c9767-143">Enumeration</span></span>|<span data-ttu-id="c9767-144">CurrentUser veya LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="c9767-144">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="c9767-145">storeName özniteliği</span><span class="sxs-lookup"><span data-stu-id="c9767-145">storeName Attribute</span></span>  
  
|<span data-ttu-id="c9767-146">Değer</span><span class="sxs-lookup"><span data-stu-id="c9767-146">Value</span></span>|<span data-ttu-id="c9767-147">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c9767-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c9767-148">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="c9767-148">Enumeration</span></span>|<span data-ttu-id="c9767-149">Değerler şunlardır: AddressBook, AuthRoot, CertificateAuthority, Izin verilmeyen, My, root, Trustedkişilerim ve TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="c9767-149">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c9767-150">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c9767-150">Child Elements</span></span>  
 <span data-ttu-id="c9767-151">Yok.</span><span class="sxs-lookup"><span data-stu-id="c9767-151">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c9767-152">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c9767-152">Parent Elements</span></span>  
  
|<span data-ttu-id="c9767-153">Öğe</span><span class="sxs-lookup"><span data-stu-id="c9767-153">Element</span></span>|<span data-ttu-id="c9767-154">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c9767-154">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c9767-155">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="c9767-155">\<serviceCertificate></span></span>](servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="c9767-156">İstemciye bir hizmetin kimlik doğrulaması yapılırken kullanılacak sertifikayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="c9767-156">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c9767-157">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c9767-157">Remarks</span></span>  
 <span data-ttu-id="c9767-158">Sertifika tabanlı ileti güvenliği kullanan bağlamalar için, bu yapılandırma öğesi tarafından belirtilen sertifika, iletileri hizmete şifrelemek için kullanılır ve istemciye yanıtları imzalamak için hizmet tarafından kullanılması beklenir.</span><span class="sxs-lookup"><span data-stu-id="c9767-158">For bindings that use certificate-based message security, certificate specified by this configuration element is used to encrypt messages to the service and is expected to be used by the service for signing replies to the client.</span></span> <span data-ttu-id="c9767-159">Bir hizmet tarafından hiçbir sertifika belirtilmediğinde kullanılacak tek bir sertifika depolar.</span><span class="sxs-lookup"><span data-stu-id="c9767-159">It stores a single certificate to be used when no certificate is specified by a service.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c9767-160">Örnek</span><span class="sxs-lookup"><span data-stu-id="c9767-160">Example</span></span>  
 <span data-ttu-id="c9767-161">Aşağıdaki örnek, URI 'si ile `http://www.contoso.com` başlayan uç noktalar için kullanılacak bir sertifikayı ve sertifika anlaşması gerçekleştirmeyin diğer tüm uç noktalar için kullanılacak bir sertifikayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="c9767-161">The following example specifies a certificate to use for endpoints whose URI begins with `http://www.contoso.com` and a certificate to use for all other endpoints that do not perform certificate negotiation.</span></span>  
  
```xml  
<serviceCertificate>
  <defaultCertificate findValue="www.contoso.com"
                      storeLocation="LocalMachine"
                      storeName="TrustedPeople"
                      x509FindType="FindByIssuerDistinguishedName" />
  <scopedCertificates>
    <add targetUri="http://www.contoso.com"
         findValue="www.contoso.com"
         storeLocation="LocalMachine"
         storeName="Root"
         x509FindType="FindByIssuerName" />
  </scopedCertificates>
  <authentication revocationMode="Online"
                  trustedStoreLocation="LocalMachine" />
</serviceCertificate>
```  
  
## <a name="see-also"></a><span data-ttu-id="c9767-162">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c9767-162">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509DefaultServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.DefaultCertificate%2A>
- [<span data-ttu-id="c9767-163">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="c9767-163">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="c9767-164">\<kimlik doğrulama ></span><span class="sxs-lookup"><span data-stu-id="c9767-164">\<authentication></span></span>](authentication-of-clientcertificate-element.md)
- [<span data-ttu-id="c9767-165">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="c9767-165">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="c9767-166">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="c9767-166">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
