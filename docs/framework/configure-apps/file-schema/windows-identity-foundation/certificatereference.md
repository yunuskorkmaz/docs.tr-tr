---
title: '&lt;certificateReference&gt;'
ms.date: 03/30/2017
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: e0f9a826a4c8d292346d9efee7970a82b88fb612
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32756845"
---
# <a name="ltcertificatereferencegt"></a><span data-ttu-id="61709-102">&lt;certificateReference&gt;</span><span class="sxs-lookup"><span data-stu-id="61709-102">&lt;certificateReference&gt;</span></span>
<span data-ttu-id="61709-103">Bul ve bir X.509 sertifikası sertifika deposunda doğrulamak için kullanılan ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="61709-103">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>  
  
 <span data-ttu-id="61709-104">\<system.identityModel.services ></span><span class="sxs-lookup"><span data-stu-id="61709-104">\<system.identityModel.services></span></span>  
<span data-ttu-id="61709-105">\<Federationconfiguration'a ></span><span class="sxs-lookup"><span data-stu-id="61709-105">\<federationConfiguration></span></span>  
<span data-ttu-id="61709-106">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="61709-106">\<serviceCertificate></span></span>  
<span data-ttu-id="61709-107">\<certificateReference ></span><span class="sxs-lookup"><span data-stu-id="61709-107">\<certificateReference></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61709-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="61709-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="61709-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="61709-109">Attributes and Elements</span></span>  
 <span data-ttu-id="61709-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="61709-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="61709-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="61709-111">Attributes</span></span>  
  
|<span data-ttu-id="61709-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="61709-112">Attribute</span></span>|<span data-ttu-id="61709-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="61709-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="61709-114">storeName</span><span class="sxs-lookup"><span data-stu-id="61709-114">storeName</span></span>|<span data-ttu-id="61709-115">X.509 Sertifika deposu adı.</span><span class="sxs-lookup"><span data-stu-id="61709-115">The name of the X.509 certificate store.</span></span> <span data-ttu-id="61709-116">Varsayılan değer "Benim".</span><span class="sxs-lookup"><span data-stu-id="61709-116">The default is "My".</span></span> <span data-ttu-id="61709-117">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="61709-117">Optional.</span></span>|  
|<span data-ttu-id="61709-118">storeLocation</span><span class="sxs-lookup"><span data-stu-id="61709-118">storeLocation</span></span>|<span data-ttu-id="61709-119">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> X.509 Sertifika deposunun konumu belirten değer.</span><span class="sxs-lookup"><span data-stu-id="61709-119">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the location of the X.509 certificate store.</span></span> <span data-ttu-id="61709-120">Varsayılan değer "LocalMachine" dir.</span><span class="sxs-lookup"><span data-stu-id="61709-120">The default value is "LocalMachine".</span></span> <span data-ttu-id="61709-121">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="61709-121">Optional.</span></span>|  
|<span data-ttu-id="61709-122">X509FindType</span><span class="sxs-lookup"><span data-stu-id="61709-122">x509FindType</span></span>|<span data-ttu-id="61709-123">Bir <xref:System.Security.Cryptography.X509Certificates.X509FindType> yürütüleceğini arama türünü belirten değer.</span><span class="sxs-lookup"><span data-stu-id="61709-123">An <xref:System.Security.Cryptography.X509Certificates.X509FindType> value that specifies the type of search that is to be executed.</span></span> <span data-ttu-id="61709-124">Varsayılan değer "FindBySubjectDistinguishedName" dir.</span><span class="sxs-lookup"><span data-stu-id="61709-124">The default is "FindBySubjectDistinguishedName".</span></span> <span data-ttu-id="61709-125">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="61709-125">Optional.</span></span>|  
|<span data-ttu-id="61709-126">findValue</span><span class="sxs-lookup"><span data-stu-id="61709-126">findValue</span></span>|<span data-ttu-id="61709-127">X.509 sertifika deposunda arama için değer.</span><span class="sxs-lookup"><span data-stu-id="61709-127">The value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="61709-128">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="61709-128">Optional.</span></span>|  
|<span data-ttu-id="61709-129">isChainIncluded</span><span class="sxs-lookup"><span data-stu-id="61709-129">isChainIncluded</span></span>|<span data-ttu-id="61709-130">Sertifika zincirini kullanarak doğrulama gerçekleştirilmesi gerekip gerekmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="61709-130">Specifies whether validation should be performed by using the certificate chain.</span></span> <span data-ttu-id="61709-131">Varsayılan değer "true"; doğrulama, sertifika zinciri kullanılarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="61709-131">The default is "true"; validation is performed by using the certificate chain.</span></span> <span data-ttu-id="61709-132">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="61709-132">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="61709-133">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="61709-133">Child Elements</span></span>  
 <span data-ttu-id="61709-134">Yok.</span><span class="sxs-lookup"><span data-stu-id="61709-134">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="61709-135">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="61709-135">Parent Elements</span></span>  
  
|<span data-ttu-id="61709-136">Öğe</span><span class="sxs-lookup"><span data-stu-id="61709-136">Element</span></span>|<span data-ttu-id="61709-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="61709-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="61709-138">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="61709-138">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicecertificate.md)|<span data-ttu-id="61709-139">Şifrelemek ve belirteçlerin şifresini çözmek için kullanılan sertifikayı yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="61709-139">Configures the certificate that is used to encrypt and decrypt tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="61709-140">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="61709-140">Remarks</span></span>  
 <span data-ttu-id="61709-141">`<certificateReference>` Öğesi bulmak ve bir X.509 sertifikası sertifika deposunda doğrulamak için kullanılan ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="61709-141">The `<certificateReference>` element specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span> <span data-ttu-id="61709-142">Bunu belirtildiğinde alt öğesi olarak `<serviceCertficate>` öğesi, şifrelemek ve belirteçlerin şifresini çözmek için kullanılan X.509 sertifikasının konumunu ve doğrulama ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="61709-142">When it is specified as the child element of the `<serviceCertficate>` element, it specifies the location and verification settings of the X.509 certificate that is used to encrypt and decrypt tokens.</span></span> <span data-ttu-id="61709-143">`<certificateReference>` Öğesi ile temsil edilir <xref:System.ServiceModel.Configuration.CertificateReferenceElement> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="61709-143">The `<certificateReference>` element is represented by the <xref:System.ServiceModel.Configuration.CertificateReferenceElement> class.</span></span>
