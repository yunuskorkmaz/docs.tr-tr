---
description: 'Daha fazla bilgi edinin: <defaultCertificate> öğesi'
title: <defaultCertificate> Öğesi
ms.date: 03/30/2017
ms.assetid: f1ddf364-9a00-45d3-b989-ff381c154ce6
ms.openlocfilehash: 580236e521e91c8b475586f6c6378630960f233c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803925"
---
# <a name="defaultcertificate-element"></a><span data-ttu-id="7f674-103">\<defaultCertificate> Öğesi</span><span class="sxs-lookup"><span data-stu-id="7f674-103">\<defaultCertificate> Element</span></span>

<span data-ttu-id="7f674-104">Bir hizmet veya STS bir anlaşma protokolü aracılığıyla bir tane sağlamıyorsa kullanılacak bir X. 509.952 sertifikası belirtir.</span><span class="sxs-lookup"><span data-stu-id="7f674-104">Specifies an X.509 certificate to be used when a service or STS does not provide one via a negotiation protocol.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultCertificate>**  
  
## <a name="syntax"></a><span data-ttu-id="7f674-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="7f674-105">Syntax</span></span>  
  
```xml  
<defaultCertificate findValue="String"
                    storeLocation=" CurrentUser/LocalMachine"
                    storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                    x509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialiNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7f674-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7f674-106">Attributes and Elements</span></span>  

 <span data-ttu-id="7f674-107">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="7f674-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7f674-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7f674-108">Attributes</span></span>  
  
|<span data-ttu-id="7f674-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="7f674-109">Attribute</span></span>|<span data-ttu-id="7f674-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7f674-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7f674-111">findValue</span><span class="sxs-lookup"><span data-stu-id="7f674-111">findValue</span></span>|<span data-ttu-id="7f674-112">Dize.</span><span class="sxs-lookup"><span data-stu-id="7f674-112">String.</span></span> <span data-ttu-id="7f674-113">Aranacak değer.</span><span class="sxs-lookup"><span data-stu-id="7f674-113">The value to search for.</span></span>|  
|<span data-ttu-id="7f674-114">x509FindType</span><span class="sxs-lookup"><span data-stu-id="7f674-114">x509FindType</span></span>|<span data-ttu-id="7f674-115">Listelenen.</span><span class="sxs-lookup"><span data-stu-id="7f674-115">Enumeration.</span></span> <span data-ttu-id="7f674-116">Arama yapılacak sertifika alanlarından biri.</span><span class="sxs-lookup"><span data-stu-id="7f674-116">One of the certificate fields to search.</span></span>|  
|<span data-ttu-id="7f674-117">storeLocation</span><span class="sxs-lookup"><span data-stu-id="7f674-117">storeLocation</span></span>|<span data-ttu-id="7f674-118">Listelenen.</span><span class="sxs-lookup"><span data-stu-id="7f674-118">Enumeration.</span></span> <span data-ttu-id="7f674-119">Aranacak iki sistem depolama konumundan biri.</span><span class="sxs-lookup"><span data-stu-id="7f674-119">One of the two system store locations to search.</span></span>|  
|<span data-ttu-id="7f674-120">storeName</span><span class="sxs-lookup"><span data-stu-id="7f674-120">storeName</span></span>|<span data-ttu-id="7f674-121">Listelenen.</span><span class="sxs-lookup"><span data-stu-id="7f674-121">Enumeration.</span></span> <span data-ttu-id="7f674-122">Arama yapmak için sistem mağazalarından biri.</span><span class="sxs-lookup"><span data-stu-id="7f674-122">One of the system stores to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="7f674-123">findValue özniteliği</span><span class="sxs-lookup"><span data-stu-id="7f674-123">findValue Attribute</span></span>  
  
|<span data-ttu-id="7f674-124">Değer</span><span class="sxs-lookup"><span data-stu-id="7f674-124">Value</span></span>|<span data-ttu-id="7f674-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7f674-125">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7f674-126">Dize</span><span class="sxs-lookup"><span data-stu-id="7f674-126">String</span></span>|<span data-ttu-id="7f674-127">Değer, aranmakta olan alana bağlıdır (X509FindType özniteliğiyle belirtilir).</span><span class="sxs-lookup"><span data-stu-id="7f674-127">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="7f674-128">Örneğin, bir parmak izi arıyorsanız, değerin onaltılık sayı dizesi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="7f674-128">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="7f674-129">x509FindType özniteliği</span><span class="sxs-lookup"><span data-stu-id="7f674-129">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="7f674-130">Değer</span><span class="sxs-lookup"><span data-stu-id="7f674-130">Value</span></span>|<span data-ttu-id="7f674-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7f674-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7f674-132">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="7f674-132">Enumeration</span></span>|<span data-ttu-id="7f674-133">Değerler şunlardır: Findbyparmak izi, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, Findbytımenotyetvalid, FindBySerialNumber, Findbytimedoldu, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, Findbyexten, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="7f674-133">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="7f674-134">storeLocation özniteliği</span><span class="sxs-lookup"><span data-stu-id="7f674-134">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="7f674-135">Değer</span><span class="sxs-lookup"><span data-stu-id="7f674-135">Value</span></span>|<span data-ttu-id="7f674-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7f674-136">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7f674-137">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="7f674-137">Enumeration</span></span>|<span data-ttu-id="7f674-138">CurrentUser veya LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="7f674-138">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="7f674-139">storeName özniteliği</span><span class="sxs-lookup"><span data-stu-id="7f674-139">storeName Attribute</span></span>  
  
|<span data-ttu-id="7f674-140">Değer</span><span class="sxs-lookup"><span data-stu-id="7f674-140">Value</span></span>|<span data-ttu-id="7f674-141">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7f674-141">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7f674-142">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="7f674-142">Enumeration</span></span>|<span data-ttu-id="7f674-143">Değerler şunlardır: AddressBook, AuthRoot, CertificateAuthority, Izin verilmeyen, My, root, Trustedkişilerim ve TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="7f674-143">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7f674-144">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7f674-144">Child Elements</span></span>  

 <span data-ttu-id="7f674-145">Yok.</span><span class="sxs-lookup"><span data-stu-id="7f674-145">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7f674-146">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7f674-146">Parent Elements</span></span>  
  
|<span data-ttu-id="7f674-147">Öğe</span><span class="sxs-lookup"><span data-stu-id="7f674-147">Element</span></span>|<span data-ttu-id="7f674-148">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7f674-148">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCertificate>](servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="7f674-149">İstemciye bir hizmetin kimlik doğrulaması yapılırken kullanılacak sertifikayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="7f674-149">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7f674-150">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7f674-150">Remarks</span></span>  

 <span data-ttu-id="7f674-151">Sertifika tabanlı ileti güvenliği kullanan bağlamalar için, bu yapılandırma öğesi tarafından belirtilen sertifika, iletileri hizmete şifrelemek için kullanılır ve istemciye yanıtları imzalamak için hizmet tarafından kullanılması beklenir.</span><span class="sxs-lookup"><span data-stu-id="7f674-151">For bindings that use certificate-based message security, certificate specified by this configuration element is used to encrypt messages to the service and is expected to be used by the service for signing replies to the client.</span></span> <span data-ttu-id="7f674-152">Bir hizmet tarafından hiçbir sertifika belirtilmediğinde kullanılacak tek bir sertifika depolar.</span><span class="sxs-lookup"><span data-stu-id="7f674-152">It stores a single certificate to be used when no certificate is specified by a service.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7f674-153">Örnek</span><span class="sxs-lookup"><span data-stu-id="7f674-153">Example</span></span>  

 <span data-ttu-id="7f674-154">Aşağıdaki örnek, URI 'SI ile başlayan uç noktalar için kullanılacak bir sertifikayı `http://www.contoso.com` ve sertifika anlaşması gerçekleştirmeyin diğer tüm uç noktalar için kullanılacak bir sertifikayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="7f674-154">The following example specifies a certificate to use for endpoints whose URI begins with `http://www.contoso.com` and a certificate to use for all other endpoints that do not perform certificate negotiation.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7f674-155">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7f674-155">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509DefaultServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.DefaultCertificate%2A>
- [<span data-ttu-id="7f674-156">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="7f674-156">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [\<authentication>](authentication-of-clientcertificate-element.md)
- [<span data-ttu-id="7f674-157">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="7f674-157">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="7f674-158">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="7f674-158">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
