---
title: <certificateReference>
ms.date: 03/30/2017
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
author: BrucePerlerMS
ms.openlocfilehash: c7dc9cfff15e70eff0086cfd98a19f3360ab8bb0
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67423035"
---
# <a name="certificatereference"></a><span data-ttu-id="b5504-101">\<certificateReference ></span><span class="sxs-lookup"><span data-stu-id="b5504-101">\<certificateReference></span></span>
<span data-ttu-id="b5504-102">Bulmak ve bir sertifika deposunda bir X.509 sertifikasını doğrulamak için kullanılan ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="b5504-102">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>  
  
 <span data-ttu-id="b5504-103">\<System.IdentityModel.Services ></span><span class="sxs-lookup"><span data-stu-id="b5504-103">\<system.identityModel.services></span></span>  
<span data-ttu-id="b5504-104">\<Federationconfiguration'a ></span><span class="sxs-lookup"><span data-stu-id="b5504-104">\<federationConfiguration></span></span>  
<span data-ttu-id="b5504-105">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="b5504-105">\<serviceCertificate></span></span>  
<span data-ttu-id="b5504-106">\<certificateReference ></span><span class="sxs-lookup"><span data-stu-id="b5504-106">\<certificateReference></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5504-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b5504-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b5504-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b5504-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b5504-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b5504-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b5504-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b5504-110">Attributes</span></span>  
  
|<span data-ttu-id="b5504-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b5504-111">Attribute</span></span>|<span data-ttu-id="b5504-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b5504-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b5504-113">storeName</span><span class="sxs-lookup"><span data-stu-id="b5504-113">storeName</span></span>|<span data-ttu-id="b5504-114">X.509 Sertifika deposunun adı.</span><span class="sxs-lookup"><span data-stu-id="b5504-114">The name of the X.509 certificate store.</span></span> <span data-ttu-id="b5504-115">Varsayılan değer "My".</span><span class="sxs-lookup"><span data-stu-id="b5504-115">The default is "My".</span></span> <span data-ttu-id="b5504-116">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="b5504-116">Optional.</span></span>|  
|<span data-ttu-id="b5504-117">storeLocation</span><span class="sxs-lookup"><span data-stu-id="b5504-117">storeLocation</span></span>|<span data-ttu-id="b5504-118">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> X.509 Sertifika deposunun konumunu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="b5504-118">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the location of the X.509 certificate store.</span></span> <span data-ttu-id="b5504-119">"LocalMachine" varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="b5504-119">The default value is "LocalMachine".</span></span> <span data-ttu-id="b5504-120">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="b5504-120">Optional.</span></span>|  
|<span data-ttu-id="b5504-121">X509FindType</span><span class="sxs-lookup"><span data-stu-id="b5504-121">x509FindType</span></span>|<span data-ttu-id="b5504-122">Bir <xref:System.Security.Cryptography.X509Certificates.X509FindType> yürütüleceğini arama türünü belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="b5504-122">An <xref:System.Security.Cryptography.X509Certificates.X509FindType> value that specifies the type of search that is to be executed.</span></span> <span data-ttu-id="b5504-123">"FindBySubjectDistinguishedName" varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="b5504-123">The default is "FindBySubjectDistinguishedName".</span></span> <span data-ttu-id="b5504-124">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="b5504-124">Optional.</span></span>|  
|<span data-ttu-id="b5504-125">findValue</span><span class="sxs-lookup"><span data-stu-id="b5504-125">findValue</span></span>|<span data-ttu-id="b5504-126">X.509 sertifika deposunda aranacak değer.</span><span class="sxs-lookup"><span data-stu-id="b5504-126">The value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="b5504-127">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="b5504-127">Optional.</span></span>|  
|<span data-ttu-id="b5504-128">isChainIncluded</span><span class="sxs-lookup"><span data-stu-id="b5504-128">isChainIncluded</span></span>|<span data-ttu-id="b5504-129">Sertifika zinciri kullanarak doğrulama gerçekleştirilip gerçekleştirilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b5504-129">Specifies whether validation should be performed by using the certificate chain.</span></span> <span data-ttu-id="b5504-130">Varsayılan değer: "true"; Sertifika zinciri kullanarak doğrulama gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="b5504-130">The default is "true"; validation is performed by using the certificate chain.</span></span> <span data-ttu-id="b5504-131">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="b5504-131">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b5504-132">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b5504-132">Child Elements</span></span>  
 <span data-ttu-id="b5504-133">Yok.</span><span class="sxs-lookup"><span data-stu-id="b5504-133">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b5504-134">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b5504-134">Parent Elements</span></span>  
  
|<span data-ttu-id="b5504-135">Öğe</span><span class="sxs-lookup"><span data-stu-id="b5504-135">Element</span></span>|<span data-ttu-id="b5504-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b5504-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b5504-137">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="b5504-137">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicecertificate.md)|<span data-ttu-id="b5504-138">Şifreleme ve belirteç şifre çözme için kullanılan sertifikayı yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="b5504-138">Configures the certificate that is used to encrypt and decrypt tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b5504-139">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b5504-139">Remarks</span></span>  
 <span data-ttu-id="b5504-140">`<certificateReference>` Öğesi bulmak ve bir sertifika deposunda bir X.509 sertifikasını doğrulamak için kullanılan ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="b5504-140">The `<certificateReference>` element specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span> <span data-ttu-id="b5504-141">Bunu belirtildiğinde alt öğesi olarak `<serviceCertificate>` öğesi, şifreleme ve belirteç şifre çözme için kullanılan X.509 sertifikasının konumunu ve doğrulama ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b5504-141">When it is specified as the child element of the `<serviceCertificate>` element, it specifies the location and verification settings of the X.509 certificate that is used to encrypt and decrypt tokens.</span></span> <span data-ttu-id="b5504-142">`<certificateReference>` Öğesi tarafından temsil edilen <xref:System.ServiceModel.Configuration.CertificateReferenceElement> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b5504-142">The `<certificateReference>` element is represented by the <xref:System.ServiceModel.Configuration.CertificateReferenceElement> class.</span></span>
