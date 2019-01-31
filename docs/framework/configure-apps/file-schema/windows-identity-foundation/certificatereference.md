---
title: <certificateReference>
ms.date: 03/30/2017
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
author: BrucePerlerMS
ms.openlocfilehash: 6c9c77f96ff6032de43d9b5a257bc0796a19b858
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55269347"
---
# <a name="certificatereference"></a><span data-ttu-id="3e26b-101">\<certificateReference ></span><span class="sxs-lookup"><span data-stu-id="3e26b-101">\<certificateReference></span></span>
<span data-ttu-id="3e26b-102">Bulmak ve bir sertifika deposunda bir X.509 sertifikasını doğrulamak için kullanılan ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="3e26b-102">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>  
  
 <span data-ttu-id="3e26b-103">\<System.IdentityModel.Services ></span><span class="sxs-lookup"><span data-stu-id="3e26b-103">\<system.identityModel.services></span></span>  
<span data-ttu-id="3e26b-104">\<Federationconfiguration'a ></span><span class="sxs-lookup"><span data-stu-id="3e26b-104">\<federationConfiguration></span></span>  
<span data-ttu-id="3e26b-105">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="3e26b-105">\<serviceCertificate></span></span>  
<span data-ttu-id="3e26b-106">\<certificateReference ></span><span class="sxs-lookup"><span data-stu-id="3e26b-106">\<certificateReference></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e26b-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3e26b-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3e26b-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3e26b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="3e26b-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3e26b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3e26b-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3e26b-110">Attributes</span></span>  
  
|<span data-ttu-id="3e26b-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3e26b-111">Attribute</span></span>|<span data-ttu-id="3e26b-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3e26b-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3e26b-113">storeName</span><span class="sxs-lookup"><span data-stu-id="3e26b-113">storeName</span></span>|<span data-ttu-id="3e26b-114">X.509 Sertifika deposunun adı.</span><span class="sxs-lookup"><span data-stu-id="3e26b-114">The name of the X.509 certificate store.</span></span> <span data-ttu-id="3e26b-115">Varsayılan değer "My".</span><span class="sxs-lookup"><span data-stu-id="3e26b-115">The default is "My".</span></span> <span data-ttu-id="3e26b-116">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="3e26b-116">Optional.</span></span>|  
|<span data-ttu-id="3e26b-117">storeLocation</span><span class="sxs-lookup"><span data-stu-id="3e26b-117">storeLocation</span></span>|<span data-ttu-id="3e26b-118">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> X.509 Sertifika deposunun konumunu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="3e26b-118">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the location of the X.509 certificate store.</span></span> <span data-ttu-id="3e26b-119">"LocalMachine" varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="3e26b-119">The default value is "LocalMachine".</span></span> <span data-ttu-id="3e26b-120">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="3e26b-120">Optional.</span></span>|  
|<span data-ttu-id="3e26b-121">X509FindType</span><span class="sxs-lookup"><span data-stu-id="3e26b-121">x509FindType</span></span>|<span data-ttu-id="3e26b-122">Bir <xref:System.Security.Cryptography.X509Certificates.X509FindType> yürütüleceğini arama türünü belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="3e26b-122">An <xref:System.Security.Cryptography.X509Certificates.X509FindType> value that specifies the type of search that is to be executed.</span></span> <span data-ttu-id="3e26b-123">"FindBySubjectDistinguishedName" varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="3e26b-123">The default is "FindBySubjectDistinguishedName".</span></span> <span data-ttu-id="3e26b-124">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="3e26b-124">Optional.</span></span>|  
|<span data-ttu-id="3e26b-125">findValue</span><span class="sxs-lookup"><span data-stu-id="3e26b-125">findValue</span></span>|<span data-ttu-id="3e26b-126">X.509 sertifika deposunda aranacak değer.</span><span class="sxs-lookup"><span data-stu-id="3e26b-126">The value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="3e26b-127">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="3e26b-127">Optional.</span></span>|  
|<span data-ttu-id="3e26b-128">isChainIncluded</span><span class="sxs-lookup"><span data-stu-id="3e26b-128">isChainIncluded</span></span>|<span data-ttu-id="3e26b-129">Sertifika zinciri kullanarak doğrulama gerçekleştirilip gerçekleştirilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3e26b-129">Specifies whether validation should be performed by using the certificate chain.</span></span> <span data-ttu-id="3e26b-130">Varsayılan değer: "true"; Sertifika zinciri kullanarak doğrulama gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="3e26b-130">The default is "true"; validation is performed by using the certificate chain.</span></span> <span data-ttu-id="3e26b-131">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="3e26b-131">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3e26b-132">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3e26b-132">Child Elements</span></span>  
 <span data-ttu-id="3e26b-133">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="3e26b-133">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3e26b-134">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3e26b-134">Parent Elements</span></span>  
  
|<span data-ttu-id="3e26b-135">Öğe</span><span class="sxs-lookup"><span data-stu-id="3e26b-135">Element</span></span>|<span data-ttu-id="3e26b-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3e26b-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3e26b-137">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="3e26b-137">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicecertificate.md)|<span data-ttu-id="3e26b-138">Şifreleme ve belirteç şifre çözme için kullanılan sertifikayı yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="3e26b-138">Configures the certificate that is used to encrypt and decrypt tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3e26b-139">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3e26b-139">Remarks</span></span>  
 <span data-ttu-id="3e26b-140">`<certificateReference>` Öğesi bulmak ve bir sertifika deposunda bir X.509 sertifikasını doğrulamak için kullanılan ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="3e26b-140">The `<certificateReference>` element specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span> <span data-ttu-id="3e26b-141">Bunu belirtildiğinde alt öğesi olarak `<serviceCertficate>` öğesi, şifreleme ve belirteç şifre çözme için kullanılan X.509 sertifikasının konumunu ve doğrulama ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="3e26b-141">When it is specified as the child element of the `<serviceCertficate>` element, it specifies the location and verification settings of the X.509 certificate that is used to encrypt and decrypt tokens.</span></span> <span data-ttu-id="3e26b-142">`<certificateReference>` Öğesi tarafından temsil edilen <xref:System.ServiceModel.Configuration.CertificateReferenceElement> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="3e26b-142">The `<certificateReference>` element is represented by the <xref:System.ServiceModel.Configuration.CertificateReferenceElement> class.</span></span>
