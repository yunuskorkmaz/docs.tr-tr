---
description: 'Hakkında daha fazla bilgi edinin: <certificateReference>'
title: <certificateReference>
ms.date: 03/30/2017
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
author: BrucePerlerMS
ms.openlocfilehash: 3404d44457849fb78ae88617d049a2199f2b5509
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99681792"
---
# \<certificateReference>

<span data-ttu-id="630f4-102">Bir sertifika deposundaki bir X. 509.440 sertifikasını bulmak ve doğrulamak için kullanılan ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="630f4-102">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateReference>**  
  
## <a name="syntax"></a><span data-ttu-id="630f4-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="630f4-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="630f4-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="630f4-104">Attributes and Elements</span></span>  

 <span data-ttu-id="630f4-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="630f4-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="630f4-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="630f4-106">Attributes</span></span>  
  
|<span data-ttu-id="630f4-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="630f4-107">Attribute</span></span>|<span data-ttu-id="630f4-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="630f4-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="630f4-109">storeName</span><span class="sxs-lookup"><span data-stu-id="630f4-109">storeName</span></span>|<span data-ttu-id="630f4-110">X. 509.440 sertifika deposunun adı.</span><span class="sxs-lookup"><span data-stu-id="630f4-110">The name of the X.509 certificate store.</span></span> <span data-ttu-id="630f4-111">Varsayılan değer "My" dır.</span><span class="sxs-lookup"><span data-stu-id="630f4-111">The default is "My".</span></span> <span data-ttu-id="630f4-112">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="630f4-112">Optional.</span></span>|  
|<span data-ttu-id="630f4-113">storeLocation</span><span class="sxs-lookup"><span data-stu-id="630f4-113">storeLocation</span></span>|<span data-ttu-id="630f4-114"><xref:System.Security.Cryptography.X509Certificates.StoreLocation>X. 509.440 sertifika deposunun konumunu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="630f4-114">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the location of the X.509 certificate store.</span></span> <span data-ttu-id="630f4-115">Varsayılan değer "LocalMachine" dır.</span><span class="sxs-lookup"><span data-stu-id="630f4-115">The default value is "LocalMachine".</span></span> <span data-ttu-id="630f4-116">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="630f4-116">Optional.</span></span>|  
|<span data-ttu-id="630f4-117">x509FindType</span><span class="sxs-lookup"><span data-stu-id="630f4-117">x509FindType</span></span>|<span data-ttu-id="630f4-118"><xref:System.Security.Cryptography.X509Certificates.X509FindType>Yürütülecek arama türünü belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="630f4-118">An <xref:System.Security.Cryptography.X509Certificates.X509FindType> value that specifies the type of search that is to be executed.</span></span> <span data-ttu-id="630f4-119">Varsayılan değer "FindBySubjectDistinguishedName" dır.</span><span class="sxs-lookup"><span data-stu-id="630f4-119">The default is "FindBySubjectDistinguishedName".</span></span> <span data-ttu-id="630f4-120">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="630f4-120">Optional.</span></span>|  
|<span data-ttu-id="630f4-121">findValue</span><span class="sxs-lookup"><span data-stu-id="630f4-121">findValue</span></span>|<span data-ttu-id="630f4-122">X. 509.440 sertifika deposunda Aranacak değer.</span><span class="sxs-lookup"><span data-stu-id="630f4-122">The value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="630f4-123">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="630f4-123">Optional.</span></span>|  
|<span data-ttu-id="630f4-124">Ischaindahil</span><span class="sxs-lookup"><span data-stu-id="630f4-124">isChainIncluded</span></span>|<span data-ttu-id="630f4-125">Doğrulamanın sertifika zinciri kullanılarak gerçekleştirilip gerçekleştirilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="630f4-125">Specifies whether validation should be performed by using the certificate chain.</span></span> <span data-ttu-id="630f4-126">Varsayılan değer "true" 'dur; doğrulama, sertifika zinciri kullanılarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="630f4-126">The default is "true"; validation is performed by using the certificate chain.</span></span> <span data-ttu-id="630f4-127">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="630f4-127">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="630f4-128">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="630f4-128">Child Elements</span></span>  

 <span data-ttu-id="630f4-129">Yok</span><span class="sxs-lookup"><span data-stu-id="630f4-129">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="630f4-130">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="630f4-130">Parent Elements</span></span>  
  
|<span data-ttu-id="630f4-131">Öğe</span><span class="sxs-lookup"><span data-stu-id="630f4-131">Element</span></span>|<span data-ttu-id="630f4-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="630f4-132">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCertificate>](servicecertificate.md)|<span data-ttu-id="630f4-133">Belirteçleri şifrelemek ve şifrelerini çözmek için kullanılan sertifikayı yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="630f4-133">Configures the certificate that is used to encrypt and decrypt tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="630f4-134">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="630f4-134">Remarks</span></span>  

 <span data-ttu-id="630f4-135">`<certificateReference>`Öğesi, bir sertifika deposundaki bir X. 509.440 sertifikasını bulmak ve doğrulamak için kullanılan ayarları belirler.</span><span class="sxs-lookup"><span data-stu-id="630f4-135">The `<certificateReference>` element specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span> <span data-ttu-id="630f4-136">Öğesinin alt öğesi olarak belirtildiğinde `<serviceCertificate>` , belirteçleri şifrelemek ve şifrelerini çözmek için kullanılan X. 509.440 sertifikasının konumunu ve doğrulama ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="630f4-136">When it is specified as the child element of the `<serviceCertificate>` element, it specifies the location and verification settings of the X.509 certificate that is used to encrypt and decrypt tokens.</span></span> <span data-ttu-id="630f4-137">`<certificateReference>`Öğesi sınıfı tarafından temsil edilir <xref:System.ServiceModel.Configuration.CertificateReferenceElement> .</span><span class="sxs-lookup"><span data-stu-id="630f4-137">The `<certificateReference>` element is represented by the <xref:System.ServiceModel.Configuration.CertificateReferenceElement> class.</span></span>
