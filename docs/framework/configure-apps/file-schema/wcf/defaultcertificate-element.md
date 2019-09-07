---
title: <defaultCertificate> Öğesi
ms.date: 03/30/2017
ms.assetid: f1ddf364-9a00-45d3-b989-ff381c154ce6
ms.openlocfilehash: cce236bf80fa00f01a3b5f4680d975f83fde0c16
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400422"
---
# <a name="defaultcertificate-element"></a><span data-ttu-id="a7a6b-102">\<defaultCertificate > öğesi</span><span class="sxs-lookup"><span data-stu-id="a7a6b-102">\<defaultCertificate> Element</span></span>
<span data-ttu-id="a7a6b-103">Bir hizmet veya STS bir anlaşma protokolü aracılığıyla bir tane sağlamıyorsa kullanılacak bir X. 509.952 sertifikası belirtir.</span><span class="sxs-lookup"><span data-stu-id="a7a6b-103">Specifies an X.509 certificate to be used when a service or STS does not provide one via a negotiation protocol.</span></span>  
  
<span data-ttu-id="a7a6b-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a7a6b-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a7a6b-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="a7a6b-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="a7a6b-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışlar >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="a7a6b-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="a7a6b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Endpointdavranışlar >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="a7a6b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="a7a6b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="a7a6b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="a7a6b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="a7a6b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="a7a6b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceCertificate >** ](servicecertificate-of-clientcredentials-element.md)</span><span class="sxs-lookup"><span data-stu-id="a7a6b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate-of-clientcredentials-element.md)</span></span>\
<span data-ttu-id="a7a6b-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<defaultCertificate >**</span><span class="sxs-lookup"><span data-stu-id="a7a6b-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultCertificate>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7a6b-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a7a6b-112">Syntax</span></span>  
  
```xml  
<defaultCertificate findValue="String"
                    storeLocation=" CurrentUser/LocalMachine"
                    storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                    x509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialiNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a7a6b-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a7a6b-113">Attributes and Elements</span></span>  
 <span data-ttu-id="a7a6b-114">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="a7a6b-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a7a6b-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a7a6b-115">Attributes</span></span>  
  
|<span data-ttu-id="a7a6b-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a7a6b-116">Attribute</span></span>|<span data-ttu-id="a7a6b-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a7a6b-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a7a6b-118">findValue</span><span class="sxs-lookup"><span data-stu-id="a7a6b-118">findValue</span></span>|<span data-ttu-id="a7a6b-119">Dizisinde.</span><span class="sxs-lookup"><span data-stu-id="a7a6b-119">String.</span></span> <span data-ttu-id="a7a6b-120">Aranacak değer.</span><span class="sxs-lookup"><span data-stu-id="a7a6b-120">The value to search for.</span></span>|  
|<span data-ttu-id="a7a6b-121">x509FindType</span><span class="sxs-lookup"><span data-stu-id="a7a6b-121">x509FindType</span></span>|<span data-ttu-id="a7a6b-122">Listelenen.</span><span class="sxs-lookup"><span data-stu-id="a7a6b-122">Enumeration.</span></span> <span data-ttu-id="a7a6b-123">Arama yapılacak sertifika alanlarından biri.</span><span class="sxs-lookup"><span data-stu-id="a7a6b-123">One of the certificate fields to search.</span></span>|  
|<span data-ttu-id="a7a6b-124">storeLocation</span><span class="sxs-lookup"><span data-stu-id="a7a6b-124">storeLocation</span></span>|<span data-ttu-id="a7a6b-125">Listelenen.</span><span class="sxs-lookup"><span data-stu-id="a7a6b-125">Enumeration.</span></span> <span data-ttu-id="a7a6b-126">Aranacak iki sistem depolama konumundan biri.</span><span class="sxs-lookup"><span data-stu-id="a7a6b-126">One of the two system store locations to search.</span></span>|  
|<span data-ttu-id="a7a6b-127">storeName</span><span class="sxs-lookup"><span data-stu-id="a7a6b-127">storeName</span></span>|<span data-ttu-id="a7a6b-128">Listelenen.</span><span class="sxs-lookup"><span data-stu-id="a7a6b-128">Enumeration.</span></span> <span data-ttu-id="a7a6b-129">Arama yapmak için sistem mağazalarından biri.</span><span class="sxs-lookup"><span data-stu-id="a7a6b-129">One of the system stores to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="a7a6b-130">findValue özniteliği</span><span class="sxs-lookup"><span data-stu-id="a7a6b-130">findValue Attribute</span></span>  
  
|<span data-ttu-id="a7a6b-131">Değer</span><span class="sxs-lookup"><span data-stu-id="a7a6b-131">Value</span></span>|<span data-ttu-id="a7a6b-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a7a6b-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a7a6b-133">Dize</span><span class="sxs-lookup"><span data-stu-id="a7a6b-133">String</span></span>|<span data-ttu-id="a7a6b-134">Değer, aranmakta olan alana bağlıdır (X509FindType özniteliğiyle belirtilir).</span><span class="sxs-lookup"><span data-stu-id="a7a6b-134">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="a7a6b-135">Örneğin, bir parmak izi arıyorsanız, değerin onaltılık sayı dizesi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a7a6b-135">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="a7a6b-136">x509FindType özniteliği</span><span class="sxs-lookup"><span data-stu-id="a7a6b-136">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="a7a6b-137">Değer</span><span class="sxs-lookup"><span data-stu-id="a7a6b-137">Value</span></span>|<span data-ttu-id="a7a6b-138">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a7a6b-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a7a6b-139">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="a7a6b-139">Enumeration</span></span>|<span data-ttu-id="a7a6b-140">Değerler şunlardır: Findbyparmak izi, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, Findbytımenotyetvalid, FindBySerialNumber, Findbytimedoldu, FindByTemplateName , FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="a7a6b-140">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="a7a6b-141">storeLocation özniteliği</span><span class="sxs-lookup"><span data-stu-id="a7a6b-141">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="a7a6b-142">Değer</span><span class="sxs-lookup"><span data-stu-id="a7a6b-142">Value</span></span>|<span data-ttu-id="a7a6b-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a7a6b-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a7a6b-144">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="a7a6b-144">Enumeration</span></span>|<span data-ttu-id="a7a6b-145">CurrentUser veya LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="a7a6b-145">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="a7a6b-146">storeName özniteliği</span><span class="sxs-lookup"><span data-stu-id="a7a6b-146">storeName Attribute</span></span>  
  
|<span data-ttu-id="a7a6b-147">Değer</span><span class="sxs-lookup"><span data-stu-id="a7a6b-147">Value</span></span>|<span data-ttu-id="a7a6b-148">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a7a6b-148">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a7a6b-149">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="a7a6b-149">Enumeration</span></span>|<span data-ttu-id="a7a6b-150">Değerler şunlardır: AddressBook, AuthRoot, CertificateAuthority, Izin verilmeyen, My, root, Trustedkişilerim ve TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="a7a6b-150">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a7a6b-151">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a7a6b-151">Child Elements</span></span>  
 <span data-ttu-id="a7a6b-152">Yok.</span><span class="sxs-lookup"><span data-stu-id="a7a6b-152">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a7a6b-153">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a7a6b-153">Parent Elements</span></span>  
  
|<span data-ttu-id="a7a6b-154">Öğe</span><span class="sxs-lookup"><span data-stu-id="a7a6b-154">Element</span></span>|<span data-ttu-id="a7a6b-155">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a7a6b-155">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a7a6b-156">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="a7a6b-156">\<serviceCertificate></span></span>](servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="a7a6b-157">İstemciye bir hizmetin kimlik doğrulaması yapılırken kullanılacak sertifikayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="a7a6b-157">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a7a6b-158">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a7a6b-158">Remarks</span></span>  
 <span data-ttu-id="a7a6b-159">Sertifika tabanlı ileti güvenliği kullanan bağlamalar için, bu yapılandırma öğesi tarafından belirtilen sertifika, iletileri hizmete şifrelemek için kullanılır ve istemciye yanıtları imzalamak için hizmet tarafından kullanılması beklenir.</span><span class="sxs-lookup"><span data-stu-id="a7a6b-159">For bindings that use certificate-based message security, certificate specified by this configuration element is used to encrypt messages to the service and is expected to be used by the service for signing replies to the client.</span></span> <span data-ttu-id="a7a6b-160">Bir hizmet tarafından hiçbir sertifika belirtilmediğinde kullanılacak tek bir sertifika depolar.</span><span class="sxs-lookup"><span data-stu-id="a7a6b-160">It stores a single certificate to be used when no certificate is specified by a service.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7a6b-161">Örnek</span><span class="sxs-lookup"><span data-stu-id="a7a6b-161">Example</span></span>  
 <span data-ttu-id="a7a6b-162">Aşağıdaki örnek, URI 'si ile `http://www.contoso.com` başlayan uç noktalar için kullanılacak bir sertifikayı ve sertifika anlaşması gerçekleştirmeyin diğer tüm uç noktalar için kullanılacak bir sertifikayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="a7a6b-162">The following example specifies a certificate to use for endpoints whose URI begins with `http://www.contoso.com` and a certificate to use for all other endpoints that do not perform certificate negotiation.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a7a6b-163">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a7a6b-163">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509DefaultServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.DefaultCertificate%2A>
- [<span data-ttu-id="a7a6b-164">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="a7a6b-164">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="a7a6b-165">\<kimlik doğrulama ></span><span class="sxs-lookup"><span data-stu-id="a7a6b-165">\<authentication></span></span>](authentication-of-clientcertificate-element.md)
- [<span data-ttu-id="a7a6b-166">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="a7a6b-166">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="a7a6b-167">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="a7a6b-167">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
