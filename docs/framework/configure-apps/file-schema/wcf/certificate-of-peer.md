---
description: 'Hakkında daha fazla bilgi <certificate> edinin: <peer>'
title: <certificate> / <peer>
ms.date: 03/30/2017
ms.assetid: 48b69142-c957-4305-a042-c9d0c9a55c0e
ms.openlocfilehash: e48a96a3f1fa486b19289584ae0c059eb5b7048d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639061"
---
# <a name="certificate-of-peer"></a><span data-ttu-id="2d240-103">\<certificate> / \<peer></span><span class="sxs-lookup"><span data-stu-id="2d240-103">\<certificate> of \<peer></span></span>

<span data-ttu-id="2d240-104">Bir eş tarafından kullanılan bir sertifikayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="2d240-104">Specifies a certificate used by a peer.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificate>**  
  
## <a name="syntax"></a><span data-ttu-id="2d240-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="2d240-105">Syntax</span></span>  
  
```xml  
<certificate findValue = "String"
             storeLocation = "CurrentUser/LocalMachine"
             storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
             X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2d240-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2d240-106">Attributes and Elements</span></span>  

 <span data-ttu-id="2d240-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2d240-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2d240-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2d240-108">Attributes</span></span>  
  
|<span data-ttu-id="2d240-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="2d240-109">Attribute</span></span>|<span data-ttu-id="2d240-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2d240-110">Description</span></span>|  
|---------------|-----------------|  
|`findValue`|<span data-ttu-id="2d240-111">X. 509.440 sertifika deposunda aranacak değeri içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="2d240-111">A string that contains the value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="2d240-112">Özniteliğinde yer alan türün, belirtilen gereksinimleri karşılaması gerekir `x509FindType` .</span><span class="sxs-lookup"><span data-stu-id="2d240-112">The type contained in the attribute must satisfy the requirements of the specified `x509FindType`.</span></span> <span data-ttu-id="2d240-113">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="2d240-113">The default is an empty string.</span></span>|  
|`storeLocation`|<span data-ttu-id="2d240-114">İstemcinin eşin sertifikasını doğrulamak için kullandığı X. 509.952 sertifika deposunun konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="2d240-114">Specifies the location of the X.509 certificate store that the client uses to validate the peer's certificate against.</span></span> <span data-ttu-id="2d240-115">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="2d240-115">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="2d240-116">-LocalMachine: yerel makineye atanan sertifika depolama alanı.</span><span class="sxs-lookup"><span data-stu-id="2d240-116">-   LocalMachine: the certificate store assigned to the local machine.</span></span><br /><span data-ttu-id="2d240-117">-CurrentUser: geçerli kullanıcıya atanmış sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="2d240-117">-   CurrentUser: the certificate store assigned to the current user.</span></span><br /><br /> <span data-ttu-id="2d240-118">Varsayılan değer LocalMachine 'dir.</span><span class="sxs-lookup"><span data-stu-id="2d240-118">The default is LocalMachine.</span></span>|  
|`storeName`|<span data-ttu-id="2d240-119">Açılacak X. 509.440 sertifika deposunun adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="2d240-119">Specifies the name of the X.509 certificate store to open.</span></span> <span data-ttu-id="2d240-120">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="2d240-120">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="2d240-121">-AddressBook: diğer kullanıcılar için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="2d240-121">-   AddressBook: Certificate store for other users.</span></span><br /><span data-ttu-id="2d240-122">-AuthRoot: üçüncü taraf sertifika yetkilileri (CA 'Lar) için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="2d240-122">-   AuthRoot: Certificate store for third-party certificate authorities (CAs).</span></span><br /><span data-ttu-id="2d240-123">-CertificateAuthority: ara sertifika yetkilileri (CA 'Lar) için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="2d240-123">-   CertificateAuthority: Certificate store for intermediate certificate authorities (CAs).</span></span><br /><span data-ttu-id="2d240-124">-İzin verilmeyen: iptal edilen sertifikalar için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="2d240-124">-   Disallowed: Certificate store for revoked certificates.</span></span><br /><span data-ttu-id="2d240-125">-My: kişisel sertifikalar için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="2d240-125">-   My: Certificate store for personal certificates.</span></span><br /><span data-ttu-id="2d240-126">-Root: güvenilen kök sertifika yetkilileri (CA 'Lar) için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="2d240-126">-   Root: Certificate store for trusted root certificate authorities (CAs).</span></span><br /><span data-ttu-id="2d240-127">-Trustedkişiler: doğrudan güvenilen kişiler ve kaynaklar için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="2d240-127">-   TrustedPeople: Certificate store for directly-trusted people and resources.</span></span><br /><span data-ttu-id="2d240-128">-TrustedPublisher: doğrudan güvenilen yayımcılar için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="2d240-128">-   TrustedPublisher: Certificate store for directly-trusted publishers.</span></span><br /><br /> <span data-ttu-id="2d240-129">Varsayılan My şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="2d240-129">The default is My.</span></span>|  
|`X509FindType`|<span data-ttu-id="2d240-130">Yürütülecek X. 509.440 aramasının türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2d240-130">Defines the type of X.509 search to be executed.</span></span> <span data-ttu-id="2d240-131">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="2d240-131">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="2d240-132">-Findbyparmak Izi</span><span class="sxs-lookup"><span data-stu-id="2d240-132">-   FindByThumbPrint</span></span><br /><span data-ttu-id="2d240-133">-FindBySubjectName</span><span class="sxs-lookup"><span data-stu-id="2d240-133">-   FindBySubjectName</span></span><br /><span data-ttu-id="2d240-134">- FindBySubjectDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="2d240-134">-   FindBySubjectDistinguishedName</span></span><br /><span data-ttu-id="2d240-135">-FindByIssuerName</span><span class="sxs-lookup"><span data-stu-id="2d240-135">-   FindByIssuerName</span></span><br /><span data-ttu-id="2d240-136">- FindByIssuerDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="2d240-136">-   FindByIssuerDistinguishedName</span></span><br /><span data-ttu-id="2d240-137">-FindBySerialNumber</span><span class="sxs-lookup"><span data-stu-id="2d240-137">-   FindBySerialNumber</span></span><br /><span data-ttu-id="2d240-138">-FindByTimeValid</span><span class="sxs-lookup"><span data-stu-id="2d240-138">-   FindByTimeValid</span></span><br /><span data-ttu-id="2d240-139">-FindByTimeNotYetValid</span><span class="sxs-lookup"><span data-stu-id="2d240-139">-   FindByTimeNotYetValid</span></span><br /><span data-ttu-id="2d240-140">-FindByTemplateName</span><span class="sxs-lookup"><span data-stu-id="2d240-140">-   FindByTemplateName</span></span><br /><span data-ttu-id="2d240-141">- FindByApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="2d240-141">-   FindByApplicationPolicy</span></span><br /><span data-ttu-id="2d240-142">-FindByCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="2d240-142">-   FindByCertificatePolicy</span></span><br /><span data-ttu-id="2d240-143">-FindByExtension</span><span class="sxs-lookup"><span data-stu-id="2d240-143">-   FindByExtension</span></span><br /><span data-ttu-id="2d240-144">-FindByKeyUsage</span><span class="sxs-lookup"><span data-stu-id="2d240-144">-   FindByKeyUsage</span></span><br /><span data-ttu-id="2d240-145">-FindBySubjectKeyIdentifier</span><span class="sxs-lookup"><span data-stu-id="2d240-145">-   FindBySubjectKeyIdentifier</span></span><br /><br /> <span data-ttu-id="2d240-146">Özniteliğinde yer alan türün, `findValue` belirtilen gereksinimleri karşılaması gerekir `X509FindType` .</span><span class="sxs-lookup"><span data-stu-id="2d240-146">The type contained in the `findValue` attribute must satisfy the requirements of the specified `X509FindType`.</span></span><br /><br /> <span data-ttu-id="2d240-147">Varsayılan değer FindBySubjectDistinguishedName ' dir.</span><span class="sxs-lookup"><span data-stu-id="2d240-147">The default value is FindBySubjectDistinguishedName.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2d240-148">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2d240-148">Child Elements</span></span>  

 <span data-ttu-id="2d240-149">Yok.</span><span class="sxs-lookup"><span data-stu-id="2d240-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2d240-150">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2d240-150">Parent Elements</span></span>  
  
|<span data-ttu-id="2d240-151">Öğe</span><span class="sxs-lookup"><span data-stu-id="2d240-151">Element</span></span>|<span data-ttu-id="2d240-152">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2d240-152">Description</span></span>|  
|-------------|-----------------|  
|[\<peer>](peer-of-servicecredentials.md)|<span data-ttu-id="2d240-153">Eş düğüm için geçerli kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="2d240-153">Specifies the current credentials for a peer node.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2d240-154">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2d240-154">Remarks</span></span>  

 <span data-ttu-id="2d240-155">Bu yapılandırma öğesi `X509Certificate2` , eş kafeste komşuları doğrulanırken kullanılan bir örnek içerir.</span><span class="sxs-lookup"><span data-stu-id="2d240-155">This configuration element contains an `X509Certificate2` instance used when authenticating neighbors in the peer mesh.</span></span>  
  
 <span data-ttu-id="2d240-156">Eşler arası programlama hakkında daha fazla bilgi için bkz. eşler [arası ağ iletişimi](../../../wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="2d240-156">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d240-157">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2d240-157">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateElement>
- <xref:System.ServiceModel.Security.PeerCredential.Certificate%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [<span data-ttu-id="2d240-158">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="2d240-158">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="2d240-159">Eşler Arası Ağ</span><span class="sxs-lookup"><span data-stu-id="2d240-159">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="2d240-160">[Eş kanal Iletisi kimlik doğrulaması](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="2d240-160">[Peer Channel Message Authentication](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="2d240-161">[Eş kanal özel kimlik doğrulaması](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="2d240-161">[Peer Channel Custom Authentication](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="2d240-162">Eş Kanalı Uygulamalarını Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="2d240-162">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
- [<span data-ttu-id="2d240-163">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="2d240-163">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
