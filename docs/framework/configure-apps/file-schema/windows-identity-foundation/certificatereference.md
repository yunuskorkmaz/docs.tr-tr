---
title: <certificateReference>
ms.date: 03/30/2017
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
author: BrucePerlerMS
ms.openlocfilehash: 782ca3344774b8412a18e3cf13bff5f969751ea3
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252151"
---
# <a name="certificatereference"></a><span data-ttu-id="9bc57-101">\<certificateReference ></span><span class="sxs-lookup"><span data-stu-id="9bc57-101">\<certificateReference></span></span>
<span data-ttu-id="9bc57-102">Bir sertifika deposundaki bir X. 509.440 sertifikasını bulmak ve doğrulamak için kullanılan ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="9bc57-102">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>  
  
<span data-ttu-id="9bc57-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9bc57-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9bc57-104">&nbsp;&nbsp;[ **\<System. IdentityModel. Services >** ](system-identitymodel-services.md)</span><span class="sxs-lookup"><span data-stu-id="9bc57-104">&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)</span></span>\
<span data-ttu-id="9bc57-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<federationConfiguration >** ](federationconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="9bc57-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)</span></span>\
<span data-ttu-id="9bc57-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceCertificate >** ](servicecertificate.md)</span><span class="sxs-lookup"><span data-stu-id="9bc57-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate.md)</span></span>\
<span data-ttu-id="9bc57-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<certificateReference >**</span><span class="sxs-lookup"><span data-stu-id="9bc57-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateReference>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bc57-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9bc57-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9bc57-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9bc57-109">Attributes and Elements</span></span>  
 <span data-ttu-id="9bc57-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9bc57-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9bc57-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9bc57-111">Attributes</span></span>  
  
|<span data-ttu-id="9bc57-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="9bc57-112">Attribute</span></span>|<span data-ttu-id="9bc57-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9bc57-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9bc57-114">storeName</span><span class="sxs-lookup"><span data-stu-id="9bc57-114">storeName</span></span>|<span data-ttu-id="9bc57-115">X. 509.440 sertifika deposunun adı.</span><span class="sxs-lookup"><span data-stu-id="9bc57-115">The name of the X.509 certificate store.</span></span> <span data-ttu-id="9bc57-116">Varsayılan değer "My" dır.</span><span class="sxs-lookup"><span data-stu-id="9bc57-116">The default is "My".</span></span> <span data-ttu-id="9bc57-117">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="9bc57-117">Optional.</span></span>|  
|<span data-ttu-id="9bc57-118">storeLocation</span><span class="sxs-lookup"><span data-stu-id="9bc57-118">storeLocation</span></span>|<span data-ttu-id="9bc57-119">X <xref:System.Security.Cryptography.X509Certificates.StoreLocation> . 509.440 sertifika deposunun konumunu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="9bc57-119">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the location of the X.509 certificate store.</span></span> <span data-ttu-id="9bc57-120">Varsayılan değer "LocalMachine" dır.</span><span class="sxs-lookup"><span data-stu-id="9bc57-120">The default value is "LocalMachine".</span></span> <span data-ttu-id="9bc57-121">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="9bc57-121">Optional.</span></span>|  
|<span data-ttu-id="9bc57-122">x509FindType</span><span class="sxs-lookup"><span data-stu-id="9bc57-122">x509FindType</span></span>|<span data-ttu-id="9bc57-123">Yürütülecek <xref:System.Security.Cryptography.X509Certificates.X509FindType> arama türünü belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="9bc57-123">An <xref:System.Security.Cryptography.X509Certificates.X509FindType> value that specifies the type of search that is to be executed.</span></span> <span data-ttu-id="9bc57-124">Varsayılan değer "FindBySubjectDistinguishedName" dır.</span><span class="sxs-lookup"><span data-stu-id="9bc57-124">The default is "FindBySubjectDistinguishedName".</span></span> <span data-ttu-id="9bc57-125">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="9bc57-125">Optional.</span></span>|  
|<span data-ttu-id="9bc57-126">findValue</span><span class="sxs-lookup"><span data-stu-id="9bc57-126">findValue</span></span>|<span data-ttu-id="9bc57-127">X. 509.440 sertifika deposunda Aranacak değer.</span><span class="sxs-lookup"><span data-stu-id="9bc57-127">The value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="9bc57-128">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="9bc57-128">Optional.</span></span>|  
|<span data-ttu-id="9bc57-129">Ischaindahil</span><span class="sxs-lookup"><span data-stu-id="9bc57-129">isChainIncluded</span></span>|<span data-ttu-id="9bc57-130">Doğrulamanın sertifika zinciri kullanılarak gerçekleştirilip gerçekleştirilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9bc57-130">Specifies whether validation should be performed by using the certificate chain.</span></span> <span data-ttu-id="9bc57-131">Varsayılan değer "true" 'dur; doğrulama, sertifika zinciri kullanılarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="9bc57-131">The default is "true"; validation is performed by using the certificate chain.</span></span> <span data-ttu-id="9bc57-132">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="9bc57-132">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9bc57-133">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9bc57-133">Child Elements</span></span>  
 <span data-ttu-id="9bc57-134">Yok.</span><span class="sxs-lookup"><span data-stu-id="9bc57-134">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9bc57-135">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9bc57-135">Parent Elements</span></span>  
  
|<span data-ttu-id="9bc57-136">Öğe</span><span class="sxs-lookup"><span data-stu-id="9bc57-136">Element</span></span>|<span data-ttu-id="9bc57-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9bc57-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9bc57-138">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="9bc57-138">\<serviceCertificate></span></span>](servicecertificate.md)|<span data-ttu-id="9bc57-139">Belirteçleri şifrelemek ve şifrelerini çözmek için kullanılan sertifikayı yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="9bc57-139">Configures the certificate that is used to encrypt and decrypt tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9bc57-140">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9bc57-140">Remarks</span></span>  
 <span data-ttu-id="9bc57-141">Öğesi `<certificateReference>` , bir sertifika deposundaki bir X. 509.440 sertifikasını bulmak ve doğrulamak için kullanılan ayarları belirler.</span><span class="sxs-lookup"><span data-stu-id="9bc57-141">The `<certificateReference>` element specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span> <span data-ttu-id="9bc57-142">`<serviceCertificate>` Öğesinin alt öğesi olarak belirtildiğinde, belirteçleri şifrelemek ve şifrelerini çözmek için kullanılan X. 509.440 sertifikasının konumunu ve doğrulama ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="9bc57-142">When it is specified as the child element of the `<serviceCertificate>` element, it specifies the location and verification settings of the X.509 certificate that is used to encrypt and decrypt tokens.</span></span> <span data-ttu-id="9bc57-143">`<certificateReference>` Öğesi sınıfı<xref:System.ServiceModel.Configuration.CertificateReferenceElement> tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="9bc57-143">The `<certificateReference>` element is represented by the <xref:System.ServiceModel.Configuration.CertificateReferenceElement> class.</span></span>
