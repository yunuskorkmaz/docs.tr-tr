---
title: <certificate> / <peer>
ms.date: 03/30/2017
ms.assetid: 48b69142-c957-4305-a042-c9d0c9a55c0e
ms.openlocfilehash: 8ec839df02af4a01d31192eebc96e4c5e58313e9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91151124"
---
# <a name="certificate-of-peer"></a><span data-ttu-id="d31c7-102">\<certificate> / \<peer></span><span class="sxs-lookup"><span data-stu-id="d31c7-102">\<certificate> of \<peer></span></span>

<span data-ttu-id="d31c7-103">Bir eş tarafından kullanılan bir sertifikayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="d31c7-103">Specifies a certificate used by a peer.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificate>**  
  
## <a name="syntax"></a><span data-ttu-id="d31c7-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="d31c7-104">Syntax</span></span>  
  
```xml  
<certificate findValue = "String"
             storeLocation = "CurrentUser/LocalMachine"
             storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
             X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d31c7-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d31c7-105">Attributes and Elements</span></span>  

 <span data-ttu-id="d31c7-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d31c7-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d31c7-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d31c7-107">Attributes</span></span>  
  
|<span data-ttu-id="d31c7-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d31c7-108">Attribute</span></span>|<span data-ttu-id="d31c7-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d31c7-109">Description</span></span>|  
|---------------|-----------------|  
|`findValue`|<span data-ttu-id="d31c7-110">X. 509.440 sertifika deposunda aranacak değeri içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="d31c7-110">A string that contains the value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="d31c7-111">Özniteliğinde yer alan türün, belirtilen gereksinimleri karşılaması gerekir `x509FindType` .</span><span class="sxs-lookup"><span data-stu-id="d31c7-111">The type contained in the attribute must satisfy the requirements of the specified `x509FindType`.</span></span> <span data-ttu-id="d31c7-112">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="d31c7-112">The default is an empty string.</span></span>|  
|`storeLocation`|<span data-ttu-id="d31c7-113">İstemcinin eşin sertifikasını doğrulamak için kullandığı X. 509.952 sertifika deposunun konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="d31c7-113">Specifies the location of the X.509 certificate store that the client uses to validate the peer's certificate against.</span></span> <span data-ttu-id="d31c7-114">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="d31c7-114">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="d31c7-115">-LocalMachine: yerel makineye atanan sertifika depolama alanı.</span><span class="sxs-lookup"><span data-stu-id="d31c7-115">-   LocalMachine: the certificate store assigned to the local machine.</span></span><br /><span data-ttu-id="d31c7-116">-CurrentUser: geçerli kullanıcıya atanmış sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="d31c7-116">-   CurrentUser: the certificate store assigned to the current user.</span></span><br /><br /> <span data-ttu-id="d31c7-117">Varsayılan değer LocalMachine 'dir.</span><span class="sxs-lookup"><span data-stu-id="d31c7-117">The default is LocalMachine.</span></span>|  
|`storeName`|<span data-ttu-id="d31c7-118">Açılacak X. 509.440 sertifika deposunun adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d31c7-118">Specifies the name of the X.509 certificate store to open.</span></span> <span data-ttu-id="d31c7-119">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="d31c7-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="d31c7-120">-AddressBook: diğer kullanıcılar için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="d31c7-120">-   AddressBook: Certificate store for other users.</span></span><br /><span data-ttu-id="d31c7-121">-AuthRoot: üçüncü taraf sertifika yetkilileri (CA 'Lar) için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="d31c7-121">-   AuthRoot: Certificate store for third-party certificate authorities (CAs).</span></span><br /><span data-ttu-id="d31c7-122">-CertificateAuthority: ara sertifika yetkilileri (CA 'Lar) için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="d31c7-122">-   CertificateAuthority: Certificate store for intermediate certificate authorities (CAs).</span></span><br /><span data-ttu-id="d31c7-123">-İzin verilmeyen: iptal edilen sertifikalar için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="d31c7-123">-   Disallowed: Certificate store for revoked certificates.</span></span><br /><span data-ttu-id="d31c7-124">-My: kişisel sertifikalar için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="d31c7-124">-   My: Certificate store for personal certificates.</span></span><br /><span data-ttu-id="d31c7-125">-Root: güvenilen kök sertifika yetkilileri (CA 'Lar) için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="d31c7-125">-   Root: Certificate store for trusted root certificate authorities (CAs).</span></span><br /><span data-ttu-id="d31c7-126">-Trustedkişiler: doğrudan güvenilen kişiler ve kaynaklar için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="d31c7-126">-   TrustedPeople: Certificate store for directly-trusted people and resources.</span></span><br /><span data-ttu-id="d31c7-127">-TrustedPublisher: doğrudan güvenilen yayımcılar için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="d31c7-127">-   TrustedPublisher: Certificate store for directly-trusted publishers.</span></span><br /><br /> <span data-ttu-id="d31c7-128">Varsayılan My şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="d31c7-128">The default is My.</span></span>|  
|`X509FindType`|<span data-ttu-id="d31c7-129">Yürütülecek X. 509.440 aramasının türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d31c7-129">Defines the type of X.509 search to be executed.</span></span> <span data-ttu-id="d31c7-130">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="d31c7-130">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="d31c7-131">-Findbyparmak Izi</span><span class="sxs-lookup"><span data-stu-id="d31c7-131">-   FindByThumbPrint</span></span><br /><span data-ttu-id="d31c7-132">-FindBySubjectName</span><span class="sxs-lookup"><span data-stu-id="d31c7-132">-   FindBySubjectName</span></span><br /><span data-ttu-id="d31c7-133">- FindBySubjectDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="d31c7-133">-   FindBySubjectDistinguishedName</span></span><br /><span data-ttu-id="d31c7-134">-FindByIssuerName</span><span class="sxs-lookup"><span data-stu-id="d31c7-134">-   FindByIssuerName</span></span><br /><span data-ttu-id="d31c7-135">- FindByIssuerDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="d31c7-135">-   FindByIssuerDistinguishedName</span></span><br /><span data-ttu-id="d31c7-136">-FindBySerialNumber</span><span class="sxs-lookup"><span data-stu-id="d31c7-136">-   FindBySerialNumber</span></span><br /><span data-ttu-id="d31c7-137">-FindByTimeValid</span><span class="sxs-lookup"><span data-stu-id="d31c7-137">-   FindByTimeValid</span></span><br /><span data-ttu-id="d31c7-138">-FindByTimeNotYetValid</span><span class="sxs-lookup"><span data-stu-id="d31c7-138">-   FindByTimeNotYetValid</span></span><br /><span data-ttu-id="d31c7-139">-FindByTemplateName</span><span class="sxs-lookup"><span data-stu-id="d31c7-139">-   FindByTemplateName</span></span><br /><span data-ttu-id="d31c7-140">- FindByApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="d31c7-140">-   FindByApplicationPolicy</span></span><br /><span data-ttu-id="d31c7-141">-FindByCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="d31c7-141">-   FindByCertificatePolicy</span></span><br /><span data-ttu-id="d31c7-142">-FindByExtension</span><span class="sxs-lookup"><span data-stu-id="d31c7-142">-   FindByExtension</span></span><br /><span data-ttu-id="d31c7-143">-FindByKeyUsage</span><span class="sxs-lookup"><span data-stu-id="d31c7-143">-   FindByKeyUsage</span></span><br /><span data-ttu-id="d31c7-144">-FindBySubjectKeyIdentifier</span><span class="sxs-lookup"><span data-stu-id="d31c7-144">-   FindBySubjectKeyIdentifier</span></span><br /><br /> <span data-ttu-id="d31c7-145">Özniteliğinde yer alan türün, `findValue` belirtilen gereksinimleri karşılaması gerekir `X509FindType` .</span><span class="sxs-lookup"><span data-stu-id="d31c7-145">The type contained in the `findValue` attribute must satisfy the requirements of the specified `X509FindType`.</span></span><br /><br /> <span data-ttu-id="d31c7-146">Varsayılan değer FindBySubjectDistinguishedName ' dir.</span><span class="sxs-lookup"><span data-stu-id="d31c7-146">The default value is FindBySubjectDistinguishedName.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d31c7-147">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d31c7-147">Child Elements</span></span>  

 <span data-ttu-id="d31c7-148">Yok.</span><span class="sxs-lookup"><span data-stu-id="d31c7-148">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d31c7-149">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d31c7-149">Parent Elements</span></span>  
  
|<span data-ttu-id="d31c7-150">Öğe</span><span class="sxs-lookup"><span data-stu-id="d31c7-150">Element</span></span>|<span data-ttu-id="d31c7-151">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d31c7-151">Description</span></span>|  
|-------------|-----------------|  
|[\<peer>](peer-of-servicecredentials.md)|<span data-ttu-id="d31c7-152">Eş düğüm için geçerli kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d31c7-152">Specifies the current credentials for a peer node.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d31c7-153">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d31c7-153">Remarks</span></span>  

 <span data-ttu-id="d31c7-154">Bu yapılandırma öğesi `X509Certificate2` , eş kafeste komşuları doğrulanırken kullanılan bir örnek içerir.</span><span class="sxs-lookup"><span data-stu-id="d31c7-154">This configuration element contains an `X509Certificate2` instance used when authenticating neighbors in the peer mesh.</span></span>  
  
 <span data-ttu-id="d31c7-155">Eşler arası programlama hakkında daha fazla bilgi için bkz. eşler [arası ağ iletişimi](../../../wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="d31c7-155">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d31c7-156">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d31c7-156">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateElement>
- <xref:System.ServiceModel.Security.PeerCredential.Certificate%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [<span data-ttu-id="d31c7-157">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="d31c7-157">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="d31c7-158">Eşler Arası Ağ</span><span class="sxs-lookup"><span data-stu-id="d31c7-158">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="d31c7-159">[Eş kanal Iletisi kimlik doğrulaması](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="d31c7-159">[Peer Channel Message Authentication](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="d31c7-160">[Eş kanal özel kimlik doğrulaması](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="d31c7-160">[Peer Channel Custom Authentication](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="d31c7-161">Eş Kanalı Uygulamalarını Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="d31c7-161">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
- [<span data-ttu-id="d31c7-162">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="d31c7-162">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
