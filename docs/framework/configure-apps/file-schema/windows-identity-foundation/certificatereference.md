---
title: <certificateReference>
ms.date: 03/30/2017
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
author: BrucePerlerMS
ms.openlocfilehash: c21e5186b8afdf8c72cbfc605af94c95bc2bc0d5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201388"
---
# \<certificateReference>

<span data-ttu-id="29d0a-101">Bir sertifika deposundaki bir X. 509.440 sertifikasını bulmak ve doğrulamak için kullanılan ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="29d0a-101">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateReference>**  
  
## <a name="syntax"></a><span data-ttu-id="29d0a-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="29d0a-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="29d0a-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="29d0a-103">Attributes and Elements</span></span>  

 <span data-ttu-id="29d0a-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="29d0a-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="29d0a-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="29d0a-105">Attributes</span></span>  
  
|<span data-ttu-id="29d0a-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="29d0a-106">Attribute</span></span>|<span data-ttu-id="29d0a-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="29d0a-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="29d0a-108">storeName</span><span class="sxs-lookup"><span data-stu-id="29d0a-108">storeName</span></span>|<span data-ttu-id="29d0a-109">X. 509.440 sertifika deposunun adı.</span><span class="sxs-lookup"><span data-stu-id="29d0a-109">The name of the X.509 certificate store.</span></span> <span data-ttu-id="29d0a-110">Varsayılan değer "My" dır.</span><span class="sxs-lookup"><span data-stu-id="29d0a-110">The default is "My".</span></span> <span data-ttu-id="29d0a-111">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="29d0a-111">Optional.</span></span>|  
|<span data-ttu-id="29d0a-112">storeLocation</span><span class="sxs-lookup"><span data-stu-id="29d0a-112">storeLocation</span></span>|<span data-ttu-id="29d0a-113"><xref:System.Security.Cryptography.X509Certificates.StoreLocation>X. 509.440 sertifika deposunun konumunu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="29d0a-113">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the location of the X.509 certificate store.</span></span> <span data-ttu-id="29d0a-114">Varsayılan değer "LocalMachine" dır.</span><span class="sxs-lookup"><span data-stu-id="29d0a-114">The default value is "LocalMachine".</span></span> <span data-ttu-id="29d0a-115">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="29d0a-115">Optional.</span></span>|  
|<span data-ttu-id="29d0a-116">x509FindType</span><span class="sxs-lookup"><span data-stu-id="29d0a-116">x509FindType</span></span>|<span data-ttu-id="29d0a-117"><xref:System.Security.Cryptography.X509Certificates.X509FindType>Yürütülecek arama türünü belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="29d0a-117">An <xref:System.Security.Cryptography.X509Certificates.X509FindType> value that specifies the type of search that is to be executed.</span></span> <span data-ttu-id="29d0a-118">Varsayılan değer "FindBySubjectDistinguishedName" dır.</span><span class="sxs-lookup"><span data-stu-id="29d0a-118">The default is "FindBySubjectDistinguishedName".</span></span> <span data-ttu-id="29d0a-119">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="29d0a-119">Optional.</span></span>|  
|<span data-ttu-id="29d0a-120">findValue</span><span class="sxs-lookup"><span data-stu-id="29d0a-120">findValue</span></span>|<span data-ttu-id="29d0a-121">X. 509.440 sertifika deposunda Aranacak değer.</span><span class="sxs-lookup"><span data-stu-id="29d0a-121">The value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="29d0a-122">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="29d0a-122">Optional.</span></span>|  
|<span data-ttu-id="29d0a-123">Ischaindahil</span><span class="sxs-lookup"><span data-stu-id="29d0a-123">isChainIncluded</span></span>|<span data-ttu-id="29d0a-124">Doğrulamanın sertifika zinciri kullanılarak gerçekleştirilip gerçekleştirilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="29d0a-124">Specifies whether validation should be performed by using the certificate chain.</span></span> <span data-ttu-id="29d0a-125">Varsayılan değer "true" 'dur; doğrulama, sertifika zinciri kullanılarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="29d0a-125">The default is "true"; validation is performed by using the certificate chain.</span></span> <span data-ttu-id="29d0a-126">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="29d0a-126">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="29d0a-127">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="29d0a-127">Child Elements</span></span>  

 <span data-ttu-id="29d0a-128">Yok</span><span class="sxs-lookup"><span data-stu-id="29d0a-128">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="29d0a-129">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="29d0a-129">Parent Elements</span></span>  
  
|<span data-ttu-id="29d0a-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="29d0a-130">Element</span></span>|<span data-ttu-id="29d0a-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="29d0a-131">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCertificate>](servicecertificate.md)|<span data-ttu-id="29d0a-132">Belirteçleri şifrelemek ve şifrelerini çözmek için kullanılan sertifikayı yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="29d0a-132">Configures the certificate that is used to encrypt and decrypt tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="29d0a-133">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="29d0a-133">Remarks</span></span>  

 <span data-ttu-id="29d0a-134">`<certificateReference>`Öğesi, bir sertifika deposundaki bir X. 509.440 sertifikasını bulmak ve doğrulamak için kullanılan ayarları belirler.</span><span class="sxs-lookup"><span data-stu-id="29d0a-134">The `<certificateReference>` element specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span> <span data-ttu-id="29d0a-135">Öğesinin alt öğesi olarak belirtildiğinde `<serviceCertificate>` , belirteçleri şifrelemek ve şifrelerini çözmek için kullanılan X. 509.440 sertifikasının konumunu ve doğrulama ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="29d0a-135">When it is specified as the child element of the `<serviceCertificate>` element, it specifies the location and verification settings of the X.509 certificate that is used to encrypt and decrypt tokens.</span></span> <span data-ttu-id="29d0a-136">`<certificateReference>`Öğesi sınıfı tarafından temsil edilir <xref:System.ServiceModel.Configuration.CertificateReferenceElement> .</span><span class="sxs-lookup"><span data-stu-id="29d0a-136">The `<certificateReference>` element is represented by the <xref:System.ServiceModel.Configuration.CertificateReferenceElement> class.</span></span>
