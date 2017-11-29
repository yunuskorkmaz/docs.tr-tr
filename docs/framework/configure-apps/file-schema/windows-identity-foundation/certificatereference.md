---
title: '&lt;certificateReference&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: c8acf4b6d6e6e8a0fcf7d73139a1d2c5ea03f063
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="ltcertificatereferencegt"></a><span data-ttu-id="e15fe-102">&lt;certificateReference&gt;</span><span class="sxs-lookup"><span data-stu-id="e15fe-102">&lt;certificateReference&gt;</span></span>
<span data-ttu-id="e15fe-103">Bul ve bir X.509 sertifikası sertifika deposunda doğrulamak için kullanılan ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="e15fe-103">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>  
  
 <span data-ttu-id="e15fe-104">\<system.identityModel.services ></span><span class="sxs-lookup"><span data-stu-id="e15fe-104">\<system.identityModel.services></span></span>  
<span data-ttu-id="e15fe-105">\<Federationconfiguration'a ></span><span class="sxs-lookup"><span data-stu-id="e15fe-105">\<federationConfiguration></span></span>  
<span data-ttu-id="e15fe-106">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="e15fe-106">\<serviceCertificate></span></span>  
<span data-ttu-id="e15fe-107">\<certificateReference ></span><span class="sxs-lookup"><span data-stu-id="e15fe-107">\<certificateReference></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e15fe-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e15fe-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e15fe-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e15fe-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e15fe-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e15fe-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e15fe-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e15fe-111">Attributes</span></span>  
  
|<span data-ttu-id="e15fe-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e15fe-112">Attribute</span></span>|<span data-ttu-id="e15fe-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e15fe-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e15fe-114">storeName</span><span class="sxs-lookup"><span data-stu-id="e15fe-114">storeName</span></span>|<span data-ttu-id="e15fe-115">X.509 Sertifika deposu adı.</span><span class="sxs-lookup"><span data-stu-id="e15fe-115">The name of the X.509 certificate store.</span></span> <span data-ttu-id="e15fe-116">Varsayılan değer "Benim".</span><span class="sxs-lookup"><span data-stu-id="e15fe-116">The default is "My".</span></span> <span data-ttu-id="e15fe-117">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="e15fe-117">Optional.</span></span>|  
|<span data-ttu-id="e15fe-118">storeLocation</span><span class="sxs-lookup"><span data-stu-id="e15fe-118">storeLocation</span></span>|<span data-ttu-id="e15fe-119">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> X.509 Sertifika deposunun konumu belirten değer.</span><span class="sxs-lookup"><span data-stu-id="e15fe-119">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the location of the X.509 certificate store.</span></span> <span data-ttu-id="e15fe-120">Varsayılan değer "LocalMachine" dir.</span><span class="sxs-lookup"><span data-stu-id="e15fe-120">The default value is "LocalMachine".</span></span> <span data-ttu-id="e15fe-121">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="e15fe-121">Optional.</span></span>|  
|<span data-ttu-id="e15fe-122">X509FindType</span><span class="sxs-lookup"><span data-stu-id="e15fe-122">x509FindType</span></span>|<span data-ttu-id="e15fe-123">Bir <xref:System.Security.Cryptography.X509Certificates.X509FindType> yürütüleceğini arama türünü belirten değer.</span><span class="sxs-lookup"><span data-stu-id="e15fe-123">An <xref:System.Security.Cryptography.X509Certificates.X509FindType> value that specifies the type of search that is to be executed.</span></span> <span data-ttu-id="e15fe-124">Varsayılan değer "FindBySubjectDistinguishedName" dir.</span><span class="sxs-lookup"><span data-stu-id="e15fe-124">The default is "FindBySubjectDistinguishedName".</span></span> <span data-ttu-id="e15fe-125">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="e15fe-125">Optional.</span></span>|  
|<span data-ttu-id="e15fe-126">findValue</span><span class="sxs-lookup"><span data-stu-id="e15fe-126">findValue</span></span>|<span data-ttu-id="e15fe-127">X.509 sertifika deposunda arama için değer.</span><span class="sxs-lookup"><span data-stu-id="e15fe-127">The value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="e15fe-128">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="e15fe-128">Optional.</span></span>|  
|<span data-ttu-id="e15fe-129">isChainIncluded</span><span class="sxs-lookup"><span data-stu-id="e15fe-129">isChainIncluded</span></span>|<span data-ttu-id="e15fe-130">Sertifika zincirini kullanarak doğrulama gerçekleştirilmesi gerekip gerekmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e15fe-130">Specifies whether validation should be performed by using the certificate chain.</span></span> <span data-ttu-id="e15fe-131">Varsayılan değer "true"; doğrulama, sertifika zinciri kullanılarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="e15fe-131">The default is "true"; validation is performed by using the certificate chain.</span></span> <span data-ttu-id="e15fe-132">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="e15fe-132">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e15fe-133">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e15fe-133">Child Elements</span></span>  
 <span data-ttu-id="e15fe-134">Yok.</span><span class="sxs-lookup"><span data-stu-id="e15fe-134">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e15fe-135">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e15fe-135">Parent Elements</span></span>  
  
|<span data-ttu-id="e15fe-136">Öğe</span><span class="sxs-lookup"><span data-stu-id="e15fe-136">Element</span></span>|<span data-ttu-id="e15fe-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e15fe-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e15fe-138">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="e15fe-138">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicecertificate.md)|<span data-ttu-id="e15fe-139">Şifrelemek ve belirteçlerin şifresini çözmek için kullanılan sertifikayı yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="e15fe-139">Configures the certificate that is used to encrypt and decrypt tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e15fe-140">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e15fe-140">Remarks</span></span>  
 <span data-ttu-id="e15fe-141">`<certificateReference>` Öğesi bulmak ve bir X.509 sertifikası sertifika deposunda doğrulamak için kullanılan ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="e15fe-141">The `<certificateReference>` element specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span> <span data-ttu-id="e15fe-142">Bunu belirtildiğinde alt öğesi olarak `<serviceCertficate>` öğesi, şifrelemek ve belirteçlerin şifresini çözmek için kullanılan X.509 sertifikasının konumunu ve doğrulama ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e15fe-142">When it is specified as the child element of the `<serviceCertficate>` element, it specifies the location and verification settings of the X.509 certificate that is used to encrypt and decrypt tokens.</span></span> <span data-ttu-id="e15fe-143">`<certificateReference>` Öğesi ile temsil edilir <xref:System.ServiceModel.Configuration.CertificateReferenceElement> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e15fe-143">The `<certificateReference>` element is represented by the <xref:System.ServiceModel.Configuration.CertificateReferenceElement> class.</span></span>
