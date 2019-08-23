---
title: <certificateReference>
ms.date: 03/30/2017
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
author: BrucePerlerMS
ms.openlocfilehash: da8ea128466457409334cd0b4ee3246a923f969a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941926"
---
# <a name="certificatereference"></a><span data-ttu-id="dad76-101">\<certificateReference ></span><span class="sxs-lookup"><span data-stu-id="dad76-101">\<certificateReference></span></span>
<span data-ttu-id="dad76-102">Bir sertifika deposundaki bir X. 509.440 sertifikasını bulmak ve doğrulamak için kullanılan ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="dad76-102">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>  
  
 <span data-ttu-id="dad76-103">\<System. IdentityModel. Services ></span><span class="sxs-lookup"><span data-stu-id="dad76-103">\<system.identityModel.services></span></span>  
<span data-ttu-id="dad76-104">\<federationConfiguration ></span><span class="sxs-lookup"><span data-stu-id="dad76-104">\<federationConfiguration></span></span>  
<span data-ttu-id="dad76-105">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="dad76-105">\<serviceCertificate></span></span>  
<span data-ttu-id="dad76-106">\<certificateReference ></span><span class="sxs-lookup"><span data-stu-id="dad76-106">\<certificateReference></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dad76-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dad76-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dad76-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="dad76-108">Attributes and Elements</span></span>  
 <span data-ttu-id="dad76-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="dad76-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dad76-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="dad76-110">Attributes</span></span>  
  
|<span data-ttu-id="dad76-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="dad76-111">Attribute</span></span>|<span data-ttu-id="dad76-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dad76-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dad76-113">storeName</span><span class="sxs-lookup"><span data-stu-id="dad76-113">storeName</span></span>|<span data-ttu-id="dad76-114">X. 509.440 sertifika deposunun adı.</span><span class="sxs-lookup"><span data-stu-id="dad76-114">The name of the X.509 certificate store.</span></span> <span data-ttu-id="dad76-115">Varsayılan değer "My" dır.</span><span class="sxs-lookup"><span data-stu-id="dad76-115">The default is "My".</span></span> <span data-ttu-id="dad76-116">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="dad76-116">Optional.</span></span>|  
|<span data-ttu-id="dad76-117">storeLocation</span><span class="sxs-lookup"><span data-stu-id="dad76-117">storeLocation</span></span>|<span data-ttu-id="dad76-118">X <xref:System.Security.Cryptography.X509Certificates.StoreLocation> . 509.440 sertifika deposunun konumunu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="dad76-118">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the location of the X.509 certificate store.</span></span> <span data-ttu-id="dad76-119">Varsayılan değer "LocalMachine" dır.</span><span class="sxs-lookup"><span data-stu-id="dad76-119">The default value is "LocalMachine".</span></span> <span data-ttu-id="dad76-120">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="dad76-120">Optional.</span></span>|  
|<span data-ttu-id="dad76-121">x509FindType</span><span class="sxs-lookup"><span data-stu-id="dad76-121">x509FindType</span></span>|<span data-ttu-id="dad76-122">Yürütülecek <xref:System.Security.Cryptography.X509Certificates.X509FindType> arama türünü belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="dad76-122">An <xref:System.Security.Cryptography.X509Certificates.X509FindType> value that specifies the type of search that is to be executed.</span></span> <span data-ttu-id="dad76-123">Varsayılan değer "FindBySubjectDistinguishedName" dır.</span><span class="sxs-lookup"><span data-stu-id="dad76-123">The default is "FindBySubjectDistinguishedName".</span></span> <span data-ttu-id="dad76-124">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="dad76-124">Optional.</span></span>|  
|<span data-ttu-id="dad76-125">findValue</span><span class="sxs-lookup"><span data-stu-id="dad76-125">findValue</span></span>|<span data-ttu-id="dad76-126">X. 509.440 sertifika deposunda Aranacak değer.</span><span class="sxs-lookup"><span data-stu-id="dad76-126">The value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="dad76-127">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="dad76-127">Optional.</span></span>|  
|<span data-ttu-id="dad76-128">Ischaindahil</span><span class="sxs-lookup"><span data-stu-id="dad76-128">isChainIncluded</span></span>|<span data-ttu-id="dad76-129">Doğrulamanın sertifika zinciri kullanılarak gerçekleştirilip gerçekleştirilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="dad76-129">Specifies whether validation should be performed by using the certificate chain.</span></span> <span data-ttu-id="dad76-130">Varsayılan değer "true" 'dur; doğrulama, sertifika zinciri kullanılarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="dad76-130">The default is "true"; validation is performed by using the certificate chain.</span></span> <span data-ttu-id="dad76-131">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="dad76-131">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dad76-132">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="dad76-132">Child Elements</span></span>  
 <span data-ttu-id="dad76-133">Yok.</span><span class="sxs-lookup"><span data-stu-id="dad76-133">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dad76-134">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="dad76-134">Parent Elements</span></span>  
  
|<span data-ttu-id="dad76-135">Öğe</span><span class="sxs-lookup"><span data-stu-id="dad76-135">Element</span></span>|<span data-ttu-id="dad76-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dad76-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dad76-137">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="dad76-137">\<serviceCertificate></span></span>](servicecertificate.md)|<span data-ttu-id="dad76-138">Belirteçleri şifrelemek ve şifrelerini çözmek için kullanılan sertifikayı yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="dad76-138">Configures the certificate that is used to encrypt and decrypt tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dad76-139">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dad76-139">Remarks</span></span>  
 <span data-ttu-id="dad76-140">Öğesi `<certificateReference>` , bir sertifika deposundaki bir X. 509.440 sertifikasını bulmak ve doğrulamak için kullanılan ayarları belirler.</span><span class="sxs-lookup"><span data-stu-id="dad76-140">The `<certificateReference>` element specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span> <span data-ttu-id="dad76-141">`<serviceCertificate>` Öğesinin alt öğesi olarak belirtildiğinde, belirteçleri şifrelemek ve şifrelerini çözmek için kullanılan X. 509.440 sertifikasının konumunu ve doğrulama ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="dad76-141">When it is specified as the child element of the `<serviceCertificate>` element, it specifies the location and verification settings of the X.509 certificate that is used to encrypt and decrypt tokens.</span></span> <span data-ttu-id="dad76-142">`<certificateReference>` Öğesi sınıfı<xref:System.ServiceModel.Configuration.CertificateReferenceElement> tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="dad76-142">The `<certificateReference>` element is represented by the <xref:System.ServiceModel.Configuration.CertificateReferenceElement> class.</span></span>
