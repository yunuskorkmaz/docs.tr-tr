---
title: <certificateReference>
ms.date: 03/30/2017
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
author: BrucePerlerMS
ms.openlocfilehash: 47d432a84d070476ddffd9b98a4ba46d8163bdc3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152820"
---
# <a name="certificatereference"></a><span data-ttu-id="c1cd5-101">\<sertifikaReferans></span><span class="sxs-lookup"><span data-stu-id="c1cd5-101">\<certificateReference></span></span>
<span data-ttu-id="c1cd5-102">Bir sertifika deposunda X.509 sertifikasını bulmak ve doğrulamak için kullanılan ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="c1cd5-102">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>  
  
<span data-ttu-id="c1cd5-103">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c1cd5-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c1cd5-104">&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)</span><span class="sxs-lookup"><span data-stu-id="c1cd5-104">&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)</span></span>\
<span data-ttu-id="c1cd5-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<federasyonKonfigürasyon>**](federationconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="c1cd5-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)</span></span>\
<span data-ttu-id="c1cd5-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceSertifika>**](servicecertificate.md)</span><span class="sxs-lookup"><span data-stu-id="c1cd5-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate.md)</span></span>\
<span data-ttu-id="c1cd5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sertifikaReferans>**</span><span class="sxs-lookup"><span data-stu-id="c1cd5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateReference>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1cd5-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c1cd5-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c1cd5-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c1cd5-109">Attributes and Elements</span></span>  
 <span data-ttu-id="c1cd5-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c1cd5-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c1cd5-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c1cd5-111">Attributes</span></span>  
  
|<span data-ttu-id="c1cd5-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c1cd5-112">Attribute</span></span>|<span data-ttu-id="c1cd5-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c1cd5-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c1cd5-114">Storename</span><span class="sxs-lookup"><span data-stu-id="c1cd5-114">storeName</span></span>|<span data-ttu-id="c1cd5-115">X.509 sertifika deposunun adı.</span><span class="sxs-lookup"><span data-stu-id="c1cd5-115">The name of the X.509 certificate store.</span></span> <span data-ttu-id="c1cd5-116">Varsayılan değer "Benim"dir.</span><span class="sxs-lookup"><span data-stu-id="c1cd5-116">The default is "My".</span></span> <span data-ttu-id="c1cd5-117">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="c1cd5-117">Optional.</span></span>|  
|<span data-ttu-id="c1cd5-118">Storelocation</span><span class="sxs-lookup"><span data-stu-id="c1cd5-118">storeLocation</span></span>|<span data-ttu-id="c1cd5-119">X.509 sertifika deposunun konumunu belirten bir <xref:System.Security.Cryptography.X509Certificates.StoreLocation> değer.</span><span class="sxs-lookup"><span data-stu-id="c1cd5-119">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the location of the X.509 certificate store.</span></span> <span data-ttu-id="c1cd5-120">Varsayılan değer "LocalMachine"dir.</span><span class="sxs-lookup"><span data-stu-id="c1cd5-120">The default value is "LocalMachine".</span></span> <span data-ttu-id="c1cd5-121">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="c1cd5-121">Optional.</span></span>|  
|<span data-ttu-id="c1cd5-122">X509findtype</span><span class="sxs-lookup"><span data-stu-id="c1cd5-122">x509FindType</span></span>|<span data-ttu-id="c1cd5-123">Yürütülecek arama türünü belirten bir <xref:System.Security.Cryptography.X509Certificates.X509FindType> değer.</span><span class="sxs-lookup"><span data-stu-id="c1cd5-123">An <xref:System.Security.Cryptography.X509Certificates.X509FindType> value that specifies the type of search that is to be executed.</span></span> <span data-ttu-id="c1cd5-124">Varsayılan "FindBySubjectDistinguishedName"dir.</span><span class="sxs-lookup"><span data-stu-id="c1cd5-124">The default is "FindBySubjectDistinguishedName".</span></span> <span data-ttu-id="c1cd5-125">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="c1cd5-125">Optional.</span></span>|  
|<span data-ttu-id="c1cd5-126">findValue</span><span class="sxs-lookup"><span data-stu-id="c1cd5-126">findValue</span></span>|<span data-ttu-id="c1cd5-127">X.509 sertifika deposunda aranacak değer.</span><span class="sxs-lookup"><span data-stu-id="c1cd5-127">The value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="c1cd5-128">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="c1cd5-128">Optional.</span></span>|  
|<span data-ttu-id="c1cd5-129">isChainIncluded</span><span class="sxs-lookup"><span data-stu-id="c1cd5-129">isChainIncluded</span></span>|<span data-ttu-id="c1cd5-130">Sertifika zinciri kullanılarak doğrulamanın yapılıp yapılmaması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c1cd5-130">Specifies whether validation should be performed by using the certificate chain.</span></span> <span data-ttu-id="c1cd5-131">Varsayılan "true"; doğrulama sertifika zinciri kullanılarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="c1cd5-131">The default is "true"; validation is performed by using the certificate chain.</span></span> <span data-ttu-id="c1cd5-132">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="c1cd5-132">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c1cd5-133">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c1cd5-133">Child Elements</span></span>  
 <span data-ttu-id="c1cd5-134">None</span><span class="sxs-lookup"><span data-stu-id="c1cd5-134">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c1cd5-135">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c1cd5-135">Parent Elements</span></span>  
  
|<span data-ttu-id="c1cd5-136">Öğe</span><span class="sxs-lookup"><span data-stu-id="c1cd5-136">Element</span></span>|<span data-ttu-id="c1cd5-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c1cd5-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c1cd5-138">\<serviceSertifika></span><span class="sxs-lookup"><span data-stu-id="c1cd5-138">\<serviceCertificate></span></span>](servicecertificate.md)|<span data-ttu-id="c1cd5-139">Belirteçleri şifrelemek ve şifresini çözmek için kullanılan sertifikayı yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="c1cd5-139">Configures the certificate that is used to encrypt and decrypt tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c1cd5-140">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c1cd5-140">Remarks</span></span>  
 <span data-ttu-id="c1cd5-141">Öğe, `<certificateReference>` bir sertifika deposunda X.509 sertifikasını bulmak ve doğrulamak için kullanılan ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="c1cd5-141">The `<certificateReference>` element specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span> <span data-ttu-id="c1cd5-142">`<serviceCertificate>` Öğenin alt öğesi olarak belirtildiğinde, belirteçleri şifrelemek ve şifresini çözmek için kullanılan X.509 sertifikasının konum ve doğrulama ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c1cd5-142">When it is specified as the child element of the `<serviceCertificate>` element, it specifies the location and verification settings of the X.509 certificate that is used to encrypt and decrypt tokens.</span></span> <span data-ttu-id="c1cd5-143">Öğe `<certificateReference>` <xref:System.ServiceModel.Configuration.CertificateReferenceElement> sınıf tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="c1cd5-143">The `<certificateReference>` element is represented by the <xref:System.ServiceModel.Configuration.CertificateReferenceElement> class.</span></span>
