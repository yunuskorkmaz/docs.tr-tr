---
title: '&lt;certificateReference&gt;'
ms.date: 03/30/2017
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
author: BrucePerlerMS
ms.openlocfilehash: e04dc90134aadfb8af7b0800c7144963d267f513
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47206897"
---
# <a name="ltcertificatereferencegt"></a><span data-ttu-id="364cf-102">&lt;certificateReference&gt;</span><span class="sxs-lookup"><span data-stu-id="364cf-102">&lt;certificateReference&gt;</span></span>
<span data-ttu-id="364cf-103">Bulmak ve bir sertifika deposunda bir X.509 sertifikasını doğrulamak için kullanılan ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="364cf-103">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>  
  
 <span data-ttu-id="364cf-104">\<System.IdentityModel.Services ></span><span class="sxs-lookup"><span data-stu-id="364cf-104">\<system.identityModel.services></span></span>  
<span data-ttu-id="364cf-105">\<Federationconfiguration'a ></span><span class="sxs-lookup"><span data-stu-id="364cf-105">\<federationConfiguration></span></span>  
<span data-ttu-id="364cf-106">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="364cf-106">\<serviceCertificate></span></span>  
<span data-ttu-id="364cf-107">\<certificateReference ></span><span class="sxs-lookup"><span data-stu-id="364cf-107">\<certificateReference></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="364cf-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="364cf-108">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
      <certificateReference   
        storeName="AddressBook||AuthRoot||CertificateAuthority||Disallowed||My||Root||TrustedPeople||TrustedPublisher"  
        storeLocation="CurrentUser||LocalMachine"  
        x509FindType="FindByThumbprint||FindBySubjectName||FindBySubjectDistinguishedName||FindByIssuerName||FindByIssuerDistinguishedName||FindBySerialNumber||FindByTimeValid||FindByTimeNotYetValid||FindByTimeExpired||FindByTemplateName||FindByApplicationPolicy||FindByCertificatePolicy||FindByExtension||FindByKeyUsage||FindBySubjectKeyIdentifier"  
        findValue=xs:String  
        isChainIncluded=xs:Boolean >  
      </certificateReference>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="364cf-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="364cf-109">Attributes and Elements</span></span>  
 <span data-ttu-id="364cf-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="364cf-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="364cf-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="364cf-111">Attributes</span></span>  
  
|<span data-ttu-id="364cf-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="364cf-112">Attribute</span></span>|<span data-ttu-id="364cf-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="364cf-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="364cf-114">storeName</span><span class="sxs-lookup"><span data-stu-id="364cf-114">storeName</span></span>|<span data-ttu-id="364cf-115">X.509 Sertifika deposunun adı.</span><span class="sxs-lookup"><span data-stu-id="364cf-115">The name of the X.509 certificate store.</span></span> <span data-ttu-id="364cf-116">Varsayılan değer "My".</span><span class="sxs-lookup"><span data-stu-id="364cf-116">The default is "My".</span></span> <span data-ttu-id="364cf-117">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="364cf-117">Optional.</span></span>|  
|<span data-ttu-id="364cf-118">storeLocation</span><span class="sxs-lookup"><span data-stu-id="364cf-118">storeLocation</span></span>|<span data-ttu-id="364cf-119">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> X.509 Sertifika deposunun konumunu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="364cf-119">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the location of the X.509 certificate store.</span></span> <span data-ttu-id="364cf-120">"LocalMachine" varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="364cf-120">The default value is "LocalMachine".</span></span> <span data-ttu-id="364cf-121">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="364cf-121">Optional.</span></span>|  
|<span data-ttu-id="364cf-122">X509FindType</span><span class="sxs-lookup"><span data-stu-id="364cf-122">x509FindType</span></span>|<span data-ttu-id="364cf-123">Bir <xref:System.Security.Cryptography.X509Certificates.X509FindType> yürütüleceğini arama türünü belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="364cf-123">An <xref:System.Security.Cryptography.X509Certificates.X509FindType> value that specifies the type of search that is to be executed.</span></span> <span data-ttu-id="364cf-124">"FindBySubjectDistinguishedName" varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="364cf-124">The default is "FindBySubjectDistinguishedName".</span></span> <span data-ttu-id="364cf-125">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="364cf-125">Optional.</span></span>|  
|<span data-ttu-id="364cf-126">findValue</span><span class="sxs-lookup"><span data-stu-id="364cf-126">findValue</span></span>|<span data-ttu-id="364cf-127">X.509 sertifika deposunda aranacak değer.</span><span class="sxs-lookup"><span data-stu-id="364cf-127">The value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="364cf-128">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="364cf-128">Optional.</span></span>|  
|<span data-ttu-id="364cf-129">isChainIncluded</span><span class="sxs-lookup"><span data-stu-id="364cf-129">isChainIncluded</span></span>|<span data-ttu-id="364cf-130">Sertifika zinciri kullanarak doğrulama gerçekleştirilip gerçekleştirilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="364cf-130">Specifies whether validation should be performed by using the certificate chain.</span></span> <span data-ttu-id="364cf-131">Varsayılan değer: "true"; Sertifika zinciri kullanarak doğrulama gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="364cf-131">The default is "true"; validation is performed by using the certificate chain.</span></span> <span data-ttu-id="364cf-132">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="364cf-132">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="364cf-133">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="364cf-133">Child Elements</span></span>  
 <span data-ttu-id="364cf-134">Yok.</span><span class="sxs-lookup"><span data-stu-id="364cf-134">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="364cf-135">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="364cf-135">Parent Elements</span></span>  
  
|<span data-ttu-id="364cf-136">Öğe</span><span class="sxs-lookup"><span data-stu-id="364cf-136">Element</span></span>|<span data-ttu-id="364cf-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="364cf-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="364cf-138">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="364cf-138">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicecertificate.md)|<span data-ttu-id="364cf-139">Şifreleme ve belirteç şifre çözme için kullanılan sertifikayı yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="364cf-139">Configures the certificate that is used to encrypt and decrypt tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="364cf-140">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="364cf-140">Remarks</span></span>  
 <span data-ttu-id="364cf-141">`<certificateReference>` Öğesi bulmak ve bir sertifika deposunda bir X.509 sertifikasını doğrulamak için kullanılan ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="364cf-141">The `<certificateReference>` element specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span> <span data-ttu-id="364cf-142">Bunu belirtildiğinde alt öğesi olarak `<serviceCertficate>` öğesi, şifreleme ve belirteç şifre çözme için kullanılan X.509 sertifikasının konumunu ve doğrulama ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="364cf-142">When it is specified as the child element of the `<serviceCertficate>` element, it specifies the location and verification settings of the X.509 certificate that is used to encrypt and decrypt tokens.</span></span> <span data-ttu-id="364cf-143">`<certificateReference>` Öğesi tarafından temsil edilen <xref:System.ServiceModel.Configuration.CertificateReferenceElement> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="364cf-143">The `<certificateReference>` element is represented by the <xref:System.ServiceModel.Configuration.CertificateReferenceElement> class.</span></span>
