---
title: "&lt;clientCertificate&gt; Öğesi &lt;sertifikası&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 00297efb-a7f2-4e03-bc2b-943d545610fc
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: bef4067d0fa74aa90841040ca5e6b3ea22f1e499
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltcertificategt-of-ltclientcertificategt-element"></a><span data-ttu-id="14074-102">&lt;clientCertificate&gt; Öğesi &lt;sertifikası&gt;</span><span class="sxs-lookup"><span data-stu-id="14074-102">&lt;certificate&gt; of &lt;clientCertificate&gt; Element</span></span>
<span data-ttu-id="14074-103">Bir X.509 belirtir imzalamak ve iletileri şifrelemek için kullanılan sertifika.</span><span class="sxs-lookup"><span data-stu-id="14074-103">Specifies an X.509 certificate used to sign and encrypt messages.</span></span>  
  
 <span data-ttu-id="14074-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="14074-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="14074-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="14074-105">\<behaviors></span></span>  
<span data-ttu-id="14074-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="14074-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="14074-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="14074-107">\<behavior></span></span>  
<span data-ttu-id="14074-108">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="14074-108">\<serviceCredentials></span></span>  
<span data-ttu-id="14074-109">\<clientCertificate ></span><span class="sxs-lookup"><span data-stu-id="14074-109">\<clientCertificate></span></span>  
<span data-ttu-id="14074-110">\<Sertifika ></span><span class="sxs-lookup"><span data-stu-id="14074-110">\<certificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14074-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="14074-111">Syntax</span></span>  
  
```xml  
<certificate findValue = "String"   
storeLocation = "CurrentUser/LocalMachine"  
storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="14074-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="14074-112">Attributes and Elements</span></span>  
 <span data-ttu-id="14074-113">Öznitelikler, alt öğelerini ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır</span><span class="sxs-lookup"><span data-stu-id="14074-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="14074-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="14074-114">Attributes</span></span>  
  
|<span data-ttu-id="14074-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="14074-115">Attribute</span></span>|<span data-ttu-id="14074-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="14074-116">Description</span></span>|  
|---------------|-----------------|  
|`findValue`|<span data-ttu-id="14074-117">X.509 sertifika deposunda arama için değer içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="14074-117">A string that contains the value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="14074-118">Özniteliğinde bulunan türü belirtilen X509FindType gereksinimlerini karşılaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="14074-118">The type contained in the attribute must satisfy the requirements of the specified X509FindType.</span></span> <span data-ttu-id="14074-119">Varsayılan boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="14074-119">The default is an empty string.</span></span>|  
|`storeLocation`|<span data-ttu-id="14074-120">Sunucu sertifikasının karşı doğrulamak için istemcinin kullandığı X.509 sertifika depolama konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="14074-120">Specifies the location of the X.509 certificate store that the client uses to validate the server’s certificate against.</span></span> <span data-ttu-id="14074-121">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="14074-121">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="14074-122">-LocalMachine: Yerel Makine sertifika deposuna.</span><span class="sxs-lookup"><span data-stu-id="14074-122">-   LocalMachine: the certificate store assigned to the local machine.</span></span><br /><span data-ttu-id="14074-123">-Currentuser'a: sertifika deposuna geçerli kullanıcıya atanmış.</span><span class="sxs-lookup"><span data-stu-id="14074-123">-   CurrentUser: the certificate store assigned to the current user.</span></span><br /><br /> <span data-ttu-id="14074-124">LocalMachine varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="14074-124">The default is LocalMachine.</span></span>|  
|`storeName`|<span data-ttu-id="14074-125">Açmak için X.509 Sertifika deposu adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="14074-125">Specifies the name of the X.509 certificate store to open.</span></span> <span data-ttu-id="14074-126">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="14074-126">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="14074-127">-Adres Defteri: Diğer kullanıcılar sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="14074-127">-   AddressBook: Certificate store for other users.</span></span><br /><span data-ttu-id="14074-128">-AuthRoot: sertifika deposunu üçüncü taraf sertifika yetkilileri (CA'lar) için.</span><span class="sxs-lookup"><span data-stu-id="14074-128">-   AuthRoot: Certificate store for third-party certification authorities (CAs).</span></span><br /><span data-ttu-id="14074-129">-CertificationAuthority: Ara sertifika yetkilileri (CA'lar) sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="14074-129">-   CertificationAuthority: Certificate store for intermediate certification authorities (CAs).</span></span><br /><span data-ttu-id="14074-130">-İzin verilmeyen: mağaza iptal edilen sertifikaları için sertifika.</span><span class="sxs-lookup"><span data-stu-id="14074-130">-   Disallowed: Certificate store for revoked certificates.</span></span><br /><span data-ttu-id="14074-131">-My: Sertifika deposunda kişisel sertifikalar için.</span><span class="sxs-lookup"><span data-stu-id="14074-131">-   My: Certificate store for personal certificates.</span></span><br /><span data-ttu-id="14074-132">-Kök: Güvenilen kök sertifika yetkilileri (CA'lar) sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="14074-132">-   Root: Certificate store for trusted root certification authorities (CAs).</span></span><br /><span data-ttu-id="14074-133">-TrustedPeople: Doğrudan güvenilir kişiler ve kaynaklar sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="14074-133">-   TrustedPeople: Certificate store for directly trusted people and resources.</span></span><br /><span data-ttu-id="14074-134">-TrustedPublisher: Doğrudan Güvenilen Yayımcılar sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="14074-134">-   TrustedPublisher: Certificate store for directly trusted publishers.</span></span><br /><br /> <span data-ttu-id="14074-135">Varsayılan değer My.</span><span class="sxs-lookup"><span data-stu-id="14074-135">The default is My.</span></span>|  
|`X509FindType`|<span data-ttu-id="14074-136">Yürütülecek X.509 arama türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="14074-136">Defines the type of X.509 search to be executed.</span></span> <span data-ttu-id="14074-137">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="14074-137">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="14074-138">-FindByThumbPrint</span><span class="sxs-lookup"><span data-stu-id="14074-138">-   FindByThumbPrint</span></span><br /><span data-ttu-id="14074-139">-FindBySubjectName</span><span class="sxs-lookup"><span data-stu-id="14074-139">-   FindBySubjectName</span></span><br /><span data-ttu-id="14074-140">-FindBySubjectDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="14074-140">-   FindBySubjectDistinguishedName</span></span><br /><span data-ttu-id="14074-141">-FindByIssuerName</span><span class="sxs-lookup"><span data-stu-id="14074-141">-   FindByIssuerName</span></span><br /><span data-ttu-id="14074-142">-FindByIssuerDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="14074-142">-   FindByIssuerDistinguishedName</span></span><br /><span data-ttu-id="14074-143">-FindBySerialNumber</span><span class="sxs-lookup"><span data-stu-id="14074-143">-   FindBySerialNumber</span></span><br /><span data-ttu-id="14074-144">-FindByTimeValid</span><span class="sxs-lookup"><span data-stu-id="14074-144">-   FindByTimeValid</span></span><br /><span data-ttu-id="14074-145">-FindByTimeNotYetValid</span><span class="sxs-lookup"><span data-stu-id="14074-145">-   FindByTimeNotYetValid</span></span><br /><span data-ttu-id="14074-146">-FindByTemplateName</span><span class="sxs-lookup"><span data-stu-id="14074-146">-   FindByTemplateName</span></span><br /><span data-ttu-id="14074-147">-FindByApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="14074-147">-   FindByApplicationPolicy</span></span><br /><span data-ttu-id="14074-148">-FindByCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="14074-148">-   FindByCertificatePolicy</span></span><br /><span data-ttu-id="14074-149">-FindByExtension</span><span class="sxs-lookup"><span data-stu-id="14074-149">-   FindByExtension</span></span><br /><span data-ttu-id="14074-150">-FindByKeyUsage</span><span class="sxs-lookup"><span data-stu-id="14074-150">-   FindByKeyUsage</span></span><br /><span data-ttu-id="14074-151">-FindBySubjectKeyIdentifier</span><span class="sxs-lookup"><span data-stu-id="14074-151">-   FindBySubjectKeyIdentifier</span></span><br /><br /> <span data-ttu-id="14074-152">İçinde yer alan türü `findValue` özniteliği belirtilen X509FindType gereksinimlerini karşılaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="14074-152">The type contained in the `findValue` attribute must satisfy the requirements of the specified X509FindType.</span></span><br /><br /> <span data-ttu-id="14074-153">FindBySubjectDistinguishedName varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="14074-153">The default value is FindBySubjectDistinguishedName.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="14074-154">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="14074-154">Child Elements</span></span>  
 <span data-ttu-id="14074-155">Yok.</span><span class="sxs-lookup"><span data-stu-id="14074-155">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="14074-156">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="14074-156">Parent Elements</span></span>  
  
|<span data-ttu-id="14074-157">Öğe</span><span class="sxs-lookup"><span data-stu-id="14074-157">Element</span></span>|<span data-ttu-id="14074-158">Açıklama</span><span class="sxs-lookup"><span data-stu-id="14074-158">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="14074-159">\<clientCertificate ></span><span class="sxs-lookup"><span data-stu-id="14074-159">\<clientCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)||  
  
## <a name="remarks"></a><span data-ttu-id="14074-160">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="14074-160">Remarks</span></span>  
 <span data-ttu-id="14074-161">`<certificate>` Hizmeti istemcisi ile önceden güvenli bir şekilde iletişim kurmak için istemci sertifikasının olması gerekir, öğe kullanılır.</span><span class="sxs-lookup"><span data-stu-id="14074-161">The `<certificate>` element is used when the service must have the client's certificate in advance to communicate securely with the client.</span></span> <span data-ttu-id="14074-162">Bu, çift yönlü iletişim düzeni kullanırken oluşur.</span><span class="sxs-lookup"><span data-stu-id="14074-162">This occurs when using the duplex communication pattern.</span></span> <span data-ttu-id="14074-163">Daha tipik istek/yanıt desende istemci sertifikasını istemciye yanıt imzalamak ve şifrelemek için hizmet kullanır istekte içerir.</span><span class="sxs-lookup"><span data-stu-id="14074-163">In the more typical request/response pattern, the client includes its certificate in the request, which the service uses to encrypt and sign its response back to the client.</span></span> <span data-ttu-id="14074-164">Çift yönlü iletişimi düzeninde ancak, hizmeti istemciden gelen istekte yok ve bu nedenle önceden istemciye ileti güvenliğini sağlamak için istemci sertifikasını gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="14074-164">In the duplex communication pattern, however, the service does not have a request from the client and therefore it needs the client's certificate in advance to secure the message to the client.</span></span> <span data-ttu-id="14074-165">Bu nedenle bir bant dışı anlaşma istemci sertifikasını elde etmek ve bu öğe kullanarak sertifikayı belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="14074-165">Therefore you must obtain the client's certificate in an out-of-band negotiation, and specify the certificate using this element.</span></span> <span data-ttu-id="14074-166">Çift yönlü hizmetler hakkında daha fazla bilgi için bkz: [nasıl yapılır: çift yönlü sözleşme oluşturma](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="14074-166">For more information about duplex services, see [How to: Create a Duplex Contract](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="14074-167">Örnek</span><span class="sxs-lookup"><span data-stu-id="14074-167">Example</span></span>  
 <span data-ttu-id="14074-168">Aşağıdaki kod uygun bir bulma belirtir X.509 sertifikasını ve özel doğrulama yazın `<authentication>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="14074-168">The following code specifies how to find an appropriate X.509 certificate and a custom validation type in the `<authentication>` element.</span></span>  
  
```xml  
<serviceBehaviors>  
 <behavior name="myServiceBehavior">  
  <clientCertificate>  
   <certificate   
         findValue="www.cohowinery.com"   
         storeLocation="CurrentUser"   
         storeName="TrustedPeople"  
         x509FindType="FindByIssuerName" />  
   <authentication customCertificateValidatorType="MyTypes.Coho"  
    certificateValidationMode="Custom"   
    revocationMode="Offline"  
    includeWindowsGroups="false"   
    mapClientCertificateToWindowsAccount="true" />  
  </clientCertificate>  
 </behavior>  
</serviceBehaviors>  
```  
  
## <a name="see-also"></a><span data-ttu-id="14074-169">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="14074-169">See Also</span></span>  
 <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.Certificate%2A>  
 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement.Certificate%2A>  
 <xref:System.ServiceModel.Configuration.X509ClientCertificateCredentialsElement>  
 [<span data-ttu-id="14074-170">Güvenlik davranışları</span><span class="sxs-lookup"><span data-stu-id="14074-170">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="14074-171">Nasıl yapılır: özel bir sertifika Doğrulayıcı kullanan bir hizmet oluşturma</span><span class="sxs-lookup"><span data-stu-id="14074-171">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)  
 [<span data-ttu-id="14074-172">Sertifikalar ile çalışma</span><span class="sxs-lookup"><span data-stu-id="14074-172">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
