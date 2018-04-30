---
title: '&lt;serviceCredentials&gt; için &lt;serviceCertificate&gt;'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 597ae6d5-4938-4950-9f5e-b2280e816182
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 16c5c065e805cb672f85dd9ff28f5b5d82d1ffba
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="ltservicecertificategt-of-ltservicecredentialsgt"></a><span data-ttu-id="c78fc-102">&lt;serviceCredentials&gt; için &lt;serviceCertificate&gt;</span><span class="sxs-lookup"><span data-stu-id="c78fc-102">&lt;serviceCertificate&gt; of &lt;serviceCredentials&gt;</span></span>
<span data-ttu-id="c78fc-103">İleti güvenlik modunu kullanarak istemcilere hizmet kimliğini doğrulamak için kullanılan bir X.509 sertifikası belirtin.</span><span class="sxs-lookup"><span data-stu-id="c78fc-103">Specify an X.509 certificate that will be used to authenticate the service to clients using Message security mode.</span></span>  
  
 <span data-ttu-id="c78fc-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c78fc-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="c78fc-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="c78fc-105">\<behaviors></span></span>  
<span data-ttu-id="c78fc-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="c78fc-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="c78fc-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="c78fc-107">\<behavior></span></span>  
<span data-ttu-id="c78fc-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="c78fc-108">\<serviceCredentials></span></span>  
<span data-ttu-id="c78fc-109">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="c78fc-109">\<serviceCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c78fc-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c78fc-110">Syntax</span></span>  
  
```xml  
<serviceCertificate findValue="String"   
    storeLocation="LocalMachine/CurrentUser"  
    storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c78fc-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c78fc-111">Attributes and Elements</span></span>  
 <span data-ttu-id="c78fc-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c78fc-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c78fc-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c78fc-113">Attributes</span></span>  
  
|<span data-ttu-id="c78fc-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c78fc-114">Attribute</span></span>|<span data-ttu-id="c78fc-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c78fc-115">Description</span></span>|  
|---------------|-----------------|  
|`findValue`|<span data-ttu-id="c78fc-116">X.509 sertifika deposunda arama için değer içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="c78fc-116">A string that contains the value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="c78fc-117">Özniteliğinde bulunan türü belirtilen X509FindType gereksinimlerini karşılaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c78fc-117">The type contained in the attribute must satisfy the requirements of the specified X509FindType.</span></span> <span data-ttu-id="c78fc-118">Varsayılan boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="c78fc-118">The default is an empty string.</span></span>|  
|`storeLocation`|<span data-ttu-id="c78fc-119">Sunucu sertifikasının karşı doğrulamak için istemcinin kullandığı X.509 sertifika depolama konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="c78fc-119">Specifies the location of the X.509 certificate store that the client uses to validate the server’s certificate against.</span></span> <span data-ttu-id="c78fc-120">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="c78fc-120">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="c78fc-121">-LocalMachine: Yerel Makine sertifika deposuna.</span><span class="sxs-lookup"><span data-stu-id="c78fc-121">-   LocalMachine: the certificate store assigned to the local machine.</span></span><br /><span data-ttu-id="c78fc-122">-Currentuser'a: sertifika deposuna geçerli kullanıcıya atanmış.</span><span class="sxs-lookup"><span data-stu-id="c78fc-122">-   CurrentUser: the certificate store assigned to the current user.</span></span><br /><br /> <span data-ttu-id="c78fc-123">LocalMachine varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="c78fc-123">The default is LocalMachine.</span></span>|  
|`storeName`|<span data-ttu-id="c78fc-124">Açmak için X.509 Sertifika deposu adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c78fc-124">Specifies the name of the X.509 certificate store to open.</span></span> <span data-ttu-id="c78fc-125">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="c78fc-125">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="c78fc-126">-Adres Defteri: Diğer kullanıcılar sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="c78fc-126">-   AddressBook: Certificate store for other users.</span></span><br /><span data-ttu-id="c78fc-127">-AuthRoot: sertifika deposunu üçüncü taraf sertifika yetkilileri (CA'lar) için.</span><span class="sxs-lookup"><span data-stu-id="c78fc-127">-   AuthRoot: Certificate store for third-party certification authorities (CAs).</span></span><br /><span data-ttu-id="c78fc-128">-CertificatAuthority: Ara sertifika yetkilileri (CA'lar) sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="c78fc-128">-   CertificatAuthority: Certificate store for intermediate certification authorities (CAs).</span></span><br /><span data-ttu-id="c78fc-129">-İzin verilmeyen: mağaza iptal edilen sertifikaları için sertifika.</span><span class="sxs-lookup"><span data-stu-id="c78fc-129">-   Disallowed: Certificate store for revoked certificates.</span></span><br /><span data-ttu-id="c78fc-130">-My: Sertifika deposunda kişisel sertifikalar için.</span><span class="sxs-lookup"><span data-stu-id="c78fc-130">-   My: Certificate store for personal certificates.</span></span><br /><span data-ttu-id="c78fc-131">-Kök: Güvenilen kök sertifika yetkilileri (CA'lar) sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="c78fc-131">-   Root: Certificate store for trusted root certification authorities (CAs).</span></span><br /><span data-ttu-id="c78fc-132">-TrustedPeople: Doğrudan güvenilir kişiler ve kaynaklar sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="c78fc-132">-   TrustedPeople: Certificate store for directly trusted people and resources.</span></span><br /><span data-ttu-id="c78fc-133">-TrustedPublisher: Doğrudan Güvenilen Yayımcılar sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="c78fc-133">-   TrustedPublisher: Certificate store for directly trusted publishers.</span></span><br /><br /> <span data-ttu-id="c78fc-134">Varsayılan değer My.</span><span class="sxs-lookup"><span data-stu-id="c78fc-134">The default is My.</span></span>|  
|`x509FindType`|<span data-ttu-id="c78fc-135">Yürütülecek X.509 arama türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c78fc-135">Defines the type of X.509 search to be executed.</span></span> <span data-ttu-id="c78fc-136">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="c78fc-136">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="c78fc-137">-FindByThumbprint</span><span class="sxs-lookup"><span data-stu-id="c78fc-137">-   FindByThumbprint</span></span><br /><span data-ttu-id="c78fc-138">-FindBySubjectName</span><span class="sxs-lookup"><span data-stu-id="c78fc-138">-   FindBySubjectName</span></span><br /><span data-ttu-id="c78fc-139">-FindBySubjectDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="c78fc-139">-   FindBySubjectDistinguishedName</span></span><br /><span data-ttu-id="c78fc-140">-FindByIssuerName</span><span class="sxs-lookup"><span data-stu-id="c78fc-140">-   FindByIssuerName</span></span><br /><span data-ttu-id="c78fc-141">-FindByIssuerDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="c78fc-141">-   FindByIssuerDistinguishedName</span></span><br /><span data-ttu-id="c78fc-142">-FindBySerialNumber</span><span class="sxs-lookup"><span data-stu-id="c78fc-142">-   FindBySerialNumber</span></span><br /><span data-ttu-id="c78fc-143">-FindByTimeValid</span><span class="sxs-lookup"><span data-stu-id="c78fc-143">-   FindByTimeValid</span></span><br /><span data-ttu-id="c78fc-144">-FindByTimeNotYetValid</span><span class="sxs-lookup"><span data-stu-id="c78fc-144">-   FindByTimeNotYetValid</span></span><br /><span data-ttu-id="c78fc-145">-FindByTemplateName</span><span class="sxs-lookup"><span data-stu-id="c78fc-145">-   FindByTemplateName</span></span><br /><span data-ttu-id="c78fc-146">-FindByApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="c78fc-146">-   FindByApplicationPolicy</span></span><br /><span data-ttu-id="c78fc-147">-FindByCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="c78fc-147">-   FindByCertificatePolicy</span></span><br /><span data-ttu-id="c78fc-148">-FindByExtension</span><span class="sxs-lookup"><span data-stu-id="c78fc-148">-   FindByExtension</span></span><br /><span data-ttu-id="c78fc-149">-FindByKeyUsage</span><span class="sxs-lookup"><span data-stu-id="c78fc-149">-   FindByKeyUsage</span></span><br /><span data-ttu-id="c78fc-150">-FindBySubjectKeyIdentifier</span><span class="sxs-lookup"><span data-stu-id="c78fc-150">-   FindBySubjectKeyIdentifier</span></span><br /><br /> <span data-ttu-id="c78fc-151">İçinde yer alan türü `findValue` özniteliği belirtilen X509FindType gereksinimlerini karşılaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c78fc-151">The type contained in the `findValue` attribute must satisfy the requirements of the specified X509FindType.</span></span><br /><br /> <span data-ttu-id="c78fc-152">FindBySubjectDistinguishedName varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="c78fc-152">The default value is FindBySubjectDistinguishedName.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c78fc-153">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c78fc-153">Child Elements</span></span>  
 <span data-ttu-id="c78fc-154">Yok.</span><span class="sxs-lookup"><span data-stu-id="c78fc-154">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c78fc-155">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c78fc-155">Parent Elements</span></span>  
  
|<span data-ttu-id="c78fc-156">Öğe</span><span class="sxs-lookup"><span data-stu-id="c78fc-156">Element</span></span>|<span data-ttu-id="c78fc-157">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c78fc-157">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c78fc-158">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="c78fc-158">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="c78fc-159">Hizmet kimlik doğrulaması kullanmak için kimlik bilgilerini belirtir ve istemci kimlik doğrulaması ilgili ayarları.</span><span class="sxs-lookup"><span data-stu-id="c78fc-159">Specifies the credential to be used in authenticating the service, and the client credential validation related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c78fc-160">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c78fc-160">Remarks</span></span>  
 <span data-ttu-id="c78fc-161">İleti güvenlik modunu kullanarak istemcilere hizmet kimliğini doğrulamak için kullanılan bir X.509 sertifikasını belirtmek için bu öğeyi kullanın.</span><span class="sxs-lookup"><span data-stu-id="c78fc-161">Use this element to specify an X.509 certificate that will be used to authenticate the service to clients using Message security mode.</span></span> <span data-ttu-id="c78fc-162">Düzenli aralıklarla yenilenmesi bir sertifika kullanıyorsanız, parmak izi değiştirir.</span><span class="sxs-lookup"><span data-stu-id="c78fc-162">If you are using a certificate that will be periodically renewed, then its thumbprint will change.</span></span> <span data-ttu-id="c78fc-163">Bu durumda konu adı olarak kullanın `x509FindType` sertifika ile aynı konu adı verilmesi için.</span><span class="sxs-lookup"><span data-stu-id="c78fc-163">In that case, use the subject name as the `x509FindType` because the certificate can be reissued with the same subject name.</span></span>  
  
 <span data-ttu-id="c78fc-164">Öğe kullanma hakkında daha fazla bilgi için bkz: [nasıl yapılır: istemci kimlik bilgileri değerlerini belirtme](../../../../../docs/framework/wcf/how-to-specify-client-credential-values.md).</span><span class="sxs-lookup"><span data-stu-id="c78fc-164">For more information about using the element, see [How to: Specify Client Credential Values](../../../../../docs/framework/wcf/how-to-specify-client-credential-values.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c78fc-165">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c78fc-165">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.ServiceCertificate%2A>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>  
 <xref:System.ServiceModel.Description.ServiceCredentials.ServiceCertificate%2A>  
 [<span data-ttu-id="c78fc-166">Nasıl yapılır: İstemci Kimlik Bilgileri Değerlerini Belirtme</span><span class="sxs-lookup"><span data-stu-id="c78fc-166">How to: Specify Client Credential Values</span></span>](../../../../../docs/framework/wcf/how-to-specify-client-credential-values.md)  
 [<span data-ttu-id="c78fc-167">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="c78fc-167">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
