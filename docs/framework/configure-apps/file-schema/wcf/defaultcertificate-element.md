---
title: <defaultCertificate> Öğesi
ms.date: 03/30/2017
ms.assetid: f1ddf364-9a00-45d3-b989-ff381c154ce6
ms.openlocfilehash: cce236bf80fa00f01a3b5f4680d975f83fde0c16
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400422"
---
# <a name="defaultcertificate-element"></a><span data-ttu-id="02026-102">\<defaultCertificate> Öğesi</span><span class="sxs-lookup"><span data-stu-id="02026-102">\<defaultCertificate> Element</span></span>
<span data-ttu-id="02026-103">Bir hizmet veya STS bir anlaşma protokolü aracılığıyla bir tane sağlamıyorsa kullanılacak bir X. 509.952 sertifikası belirtir.</span><span class="sxs-lookup"><span data-stu-id="02026-103">Specifies an X.509 certificate to be used when a service or STS does not provide one via a negotiation protocol.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultCertificate>**  
  
## <a name="syntax"></a><span data-ttu-id="02026-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="02026-104">Syntax</span></span>  
  
```xml  
<defaultCertificate findValue="String"
                    storeLocation=" CurrentUser/LocalMachine"
                    storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                    x509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialiNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="02026-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="02026-105">Attributes and Elements</span></span>  
 <span data-ttu-id="02026-106">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="02026-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="02026-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="02026-107">Attributes</span></span>  
  
|<span data-ttu-id="02026-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="02026-108">Attribute</span></span>|<span data-ttu-id="02026-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="02026-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="02026-110">findValue</span><span class="sxs-lookup"><span data-stu-id="02026-110">findValue</span></span>|<span data-ttu-id="02026-111">Dize.</span><span class="sxs-lookup"><span data-stu-id="02026-111">String.</span></span> <span data-ttu-id="02026-112">Aranacak değer.</span><span class="sxs-lookup"><span data-stu-id="02026-112">The value to search for.</span></span>|  
|<span data-ttu-id="02026-113">x509FindType</span><span class="sxs-lookup"><span data-stu-id="02026-113">x509FindType</span></span>|<span data-ttu-id="02026-114">Listelenen.</span><span class="sxs-lookup"><span data-stu-id="02026-114">Enumeration.</span></span> <span data-ttu-id="02026-115">Arama yapılacak sertifika alanlarından biri.</span><span class="sxs-lookup"><span data-stu-id="02026-115">One of the certificate fields to search.</span></span>|  
|<span data-ttu-id="02026-116">storeLocation</span><span class="sxs-lookup"><span data-stu-id="02026-116">storeLocation</span></span>|<span data-ttu-id="02026-117">Listelenen.</span><span class="sxs-lookup"><span data-stu-id="02026-117">Enumeration.</span></span> <span data-ttu-id="02026-118">Aranacak iki sistem depolama konumundan biri.</span><span class="sxs-lookup"><span data-stu-id="02026-118">One of the two system store locations to search.</span></span>|  
|<span data-ttu-id="02026-119">storeName</span><span class="sxs-lookup"><span data-stu-id="02026-119">storeName</span></span>|<span data-ttu-id="02026-120">Listelenen.</span><span class="sxs-lookup"><span data-stu-id="02026-120">Enumeration.</span></span> <span data-ttu-id="02026-121">Arama yapmak için sistem mağazalarından biri.</span><span class="sxs-lookup"><span data-stu-id="02026-121">One of the system stores to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="02026-122">findValue özniteliği</span><span class="sxs-lookup"><span data-stu-id="02026-122">findValue Attribute</span></span>  
  
|<span data-ttu-id="02026-123">Değer</span><span class="sxs-lookup"><span data-stu-id="02026-123">Value</span></span>|<span data-ttu-id="02026-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="02026-124">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="02026-125">Dize</span><span class="sxs-lookup"><span data-stu-id="02026-125">String</span></span>|<span data-ttu-id="02026-126">Değer, aranmakta olan alana bağlıdır (X509FindType özniteliğiyle belirtilir).</span><span class="sxs-lookup"><span data-stu-id="02026-126">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="02026-127">Örneğin, bir parmak izi arıyorsanız, değerin onaltılık sayı dizesi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="02026-127">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="02026-128">x509FindType özniteliği</span><span class="sxs-lookup"><span data-stu-id="02026-128">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="02026-129">Değer</span><span class="sxs-lookup"><span data-stu-id="02026-129">Value</span></span>|<span data-ttu-id="02026-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="02026-130">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="02026-131">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="02026-131">Enumeration</span></span>|<span data-ttu-id="02026-132">Değerler şunlardır: Findbyparmak izi, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, Findbytımenotyetvalid, FindBySerialNumber, Findbytimedoldu, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, Findbyexten, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="02026-132">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="02026-133">storeLocation özniteliği</span><span class="sxs-lookup"><span data-stu-id="02026-133">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="02026-134">Değer</span><span class="sxs-lookup"><span data-stu-id="02026-134">Value</span></span>|<span data-ttu-id="02026-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="02026-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="02026-136">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="02026-136">Enumeration</span></span>|<span data-ttu-id="02026-137">CurrentUser veya LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="02026-137">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="02026-138">storeName özniteliği</span><span class="sxs-lookup"><span data-stu-id="02026-138">storeName Attribute</span></span>  
  
|<span data-ttu-id="02026-139">Değer</span><span class="sxs-lookup"><span data-stu-id="02026-139">Value</span></span>|<span data-ttu-id="02026-140">Açıklama</span><span class="sxs-lookup"><span data-stu-id="02026-140">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="02026-141">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="02026-141">Enumeration</span></span>|<span data-ttu-id="02026-142">Değerler şunlardır: AddressBook, AuthRoot, CertificateAuthority, Izin verilmeyen, My, root, Trustedkişilerim ve TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="02026-142">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="02026-143">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="02026-143">Child Elements</span></span>  
 <span data-ttu-id="02026-144">Yok.</span><span class="sxs-lookup"><span data-stu-id="02026-144">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="02026-145">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="02026-145">Parent Elements</span></span>  
  
|<span data-ttu-id="02026-146">Öğe</span><span class="sxs-lookup"><span data-stu-id="02026-146">Element</span></span>|<span data-ttu-id="02026-147">Açıklama</span><span class="sxs-lookup"><span data-stu-id="02026-147">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCertificate>](servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="02026-148">İstemciye bir hizmetin kimlik doğrulaması yapılırken kullanılacak sertifikayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="02026-148">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="02026-149">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="02026-149">Remarks</span></span>  
 <span data-ttu-id="02026-150">Sertifika tabanlı ileti güvenliği kullanan bağlamalar için, bu yapılandırma öğesi tarafından belirtilen sertifika, iletileri hizmete şifrelemek için kullanılır ve istemciye yanıtları imzalamak için hizmet tarafından kullanılması beklenir.</span><span class="sxs-lookup"><span data-stu-id="02026-150">For bindings that use certificate-based message security, certificate specified by this configuration element is used to encrypt messages to the service and is expected to be used by the service for signing replies to the client.</span></span> <span data-ttu-id="02026-151">Bir hizmet tarafından hiçbir sertifika belirtilmediğinde kullanılacak tek bir sertifika depolar.</span><span class="sxs-lookup"><span data-stu-id="02026-151">It stores a single certificate to be used when no certificate is specified by a service.</span></span>  
  
## <a name="example"></a><span data-ttu-id="02026-152">Örnek</span><span class="sxs-lookup"><span data-stu-id="02026-152">Example</span></span>  
 <span data-ttu-id="02026-153">Aşağıdaki örnek, URI 'SI ile başlayan uç noktalar için kullanılacak bir sertifikayı `http://www.contoso.com` ve sertifika anlaşması gerçekleştirmeyin diğer tüm uç noktalar için kullanılacak bir sertifikayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="02026-153">The following example specifies a certificate to use for endpoints whose URI begins with `http://www.contoso.com` and a certificate to use for all other endpoints that do not perform certificate negotiation.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="02026-154">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="02026-154">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509DefaultServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.DefaultCertificate%2A>
- [<span data-ttu-id="02026-155">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="02026-155">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [\<authentication>](authentication-of-clientcertificate-element.md)
- [<span data-ttu-id="02026-156">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="02026-156">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="02026-157">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="02026-157">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
