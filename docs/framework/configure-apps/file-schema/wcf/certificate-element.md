---
description: 'Daha fazla bilgi edinin: <certificate> öğesi'
title: <certificate> Öğesi
ms.date: 03/30/2017
ms.assetid: 9b3d9233-ef35-477a-bf5d-efd1e80a52f4
ms.openlocfilehash: 3f67435d86f19f81c1f6fe1fe2a9a8afbef69e53
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639139"
---
# <a name="certificate-element"></a><span data-ttu-id="c4eb0-103">\<certificate> Öğesi</span><span class="sxs-lookup"><span data-stu-id="c4eb0-103">\<certificate> Element</span></span>

<span data-ttu-id="c4eb0-104">Eşler arası istemciler için ileti imzalama ve şifreleme için kullanılacak bir X. 509.952 sertifikası belirtir.</span><span class="sxs-lookup"><span data-stu-id="c4eb0-104">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer clients.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificate>**  
  
## <a name="syntax"></a><span data-ttu-id="c4eb0-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="c4eb0-105">Syntax</span></span>  
  
```xml  
<certificate findValue="String"
             storeLocation="LocalMachine/CurrentUser"
             storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
             X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c4eb0-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c4eb0-106">Attributes and Elements</span></span>  

 <span data-ttu-id="c4eb0-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c4eb0-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c4eb0-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c4eb0-108">Attributes</span></span>  
  
|<span data-ttu-id="c4eb0-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c4eb0-109">Attribute</span></span>|<span data-ttu-id="c4eb0-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c4eb0-110">Description</span></span>|  
|---------------|-----------------|  
|`findValue`|<span data-ttu-id="c4eb0-111">X. 509.440 sertifika deposunda aranacak değeri içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="c4eb0-111">A string that contains the value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="c4eb0-112">Özniteliğinde yer alan türün, belirtilen gereksinimleri karşılaması gerekir `x509FindType` .</span><span class="sxs-lookup"><span data-stu-id="c4eb0-112">The type contained in the attribute must satisfy the requirements of the specified `x509FindType`.</span></span> <span data-ttu-id="c4eb0-113">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="c4eb0-113">The default is an empty string.</span></span>|  
|`storeLocation`|<span data-ttu-id="c4eb0-114">İstemcinin eşin sertifikasını doğrulamak için kullandığı X. 509.952 sertifika deposunun konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="c4eb0-114">Specifies the location of the X.509 certificate store that the client uses to validate the peer's certificate against.</span></span> <span data-ttu-id="c4eb0-115">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="c4eb0-115">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="c4eb0-116">-LocalMachine: yerel makineye atanan sertifika depolama alanı.</span><span class="sxs-lookup"><span data-stu-id="c4eb0-116">-   LocalMachine: the certificate store assigned to the local machine.</span></span><br /><span data-ttu-id="c4eb0-117">-CurrentUser: geçerli kullanıcıya atanmış sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="c4eb0-117">-   CurrentUser: the certificate store assigned to the current user.</span></span><br /><br /> <span data-ttu-id="c4eb0-118">Varsayılan değer LocalMachine 'dir.</span><span class="sxs-lookup"><span data-stu-id="c4eb0-118">The default is LocalMachine.</span></span>|  
|`storeName`|<span data-ttu-id="c4eb0-119">Açılacak X. 509.440 sertifika deposunun adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c4eb0-119">Specifies the name of the X.509 certificate store to open.</span></span> <span data-ttu-id="c4eb0-120">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="c4eb0-120">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="c4eb0-121">-AddressBook: diğer kullanıcılar için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="c4eb0-121">-   AddressBook: Certificate store for other users.</span></span><br /><span data-ttu-id="c4eb0-122">-AuthRoot: üçüncü taraf sertifika yetkilileri (CA 'Lar) için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="c4eb0-122">-   AuthRoot: Certificate store for third-party certification authorities (CAs).</span></span><br /><span data-ttu-id="c4eb0-123">-CertificateAuthority: ara sertifika yetkilileri (CA 'Lar) için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="c4eb0-123">-   CertificateAuthority: Certificate store for intermediate certification authorities (CAs).</span></span><br /><span data-ttu-id="c4eb0-124">-İzin verilmeyen: iptal edilen sertifikalar için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="c4eb0-124">-   Disallowed: Certificate store for revoked certificates.</span></span><br /><span data-ttu-id="c4eb0-125">-My: kişisel sertifikalar için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="c4eb0-125">-   My: Certificate store for personal certificates.</span></span><br /><span data-ttu-id="c4eb0-126">-Root: güvenilen kök sertifika yetkilileri (CA 'Lar) için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="c4eb0-126">-   Root: Certificate store for trusted root certification authorities (CAs).</span></span><br /><span data-ttu-id="c4eb0-127">-Trustedkişiler: doğrudan güvenilen kişiler ve kaynaklar için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="c4eb0-127">-   TrustedPeople: Certificate store for directly-trusted people and resources.</span></span><br /><span data-ttu-id="c4eb0-128">-TrustedPublisher: doğrudan güvenilen yayımcılar için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="c4eb0-128">-   TrustedPublisher: Certificate store for directly-trusted publishers.</span></span><br /><br /> <span data-ttu-id="c4eb0-129">Varsayılan My şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="c4eb0-129">The default is My.</span></span>|  
|`X509FindType`|<span data-ttu-id="c4eb0-130">Yürütülecek X. 509.440 aramasının türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c4eb0-130">Defines the type of X.509 search to be executed.</span></span> <span data-ttu-id="c4eb0-131">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="c4eb0-131">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="c4eb0-132">-Findbyparmak Izi</span><span class="sxs-lookup"><span data-stu-id="c4eb0-132">-   FindByThumbPrint</span></span><br /><span data-ttu-id="c4eb0-133">-FindBySubjectName</span><span class="sxs-lookup"><span data-stu-id="c4eb0-133">-   FindBySubjectName</span></span><br /><span data-ttu-id="c4eb0-134">- FindBySubjectDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="c4eb0-134">-   FindBySubjectDistinguishedName</span></span><br /><span data-ttu-id="c4eb0-135">-FindByIssuerName</span><span class="sxs-lookup"><span data-stu-id="c4eb0-135">-   FindByIssuerName</span></span><br /><span data-ttu-id="c4eb0-136">- FindByIssuerDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="c4eb0-136">-   FindByIssuerDistinguishedName</span></span><br /><span data-ttu-id="c4eb0-137">-FindBySerialNumber</span><span class="sxs-lookup"><span data-stu-id="c4eb0-137">-   FindBySerialNumber</span></span><br /><span data-ttu-id="c4eb0-138">-FindByTimeValid</span><span class="sxs-lookup"><span data-stu-id="c4eb0-138">-   FindByTimeValid</span></span><br /><span data-ttu-id="c4eb0-139">-FindByTimeNotYetValid</span><span class="sxs-lookup"><span data-stu-id="c4eb0-139">-   FindByTimeNotYetValid</span></span><br /><span data-ttu-id="c4eb0-140">-FindByTemplateName</span><span class="sxs-lookup"><span data-stu-id="c4eb0-140">-   FindByTemplateName</span></span><br /><span data-ttu-id="c4eb0-141">- FindByApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="c4eb0-141">-   FindByApplicationPolicy</span></span><br /><span data-ttu-id="c4eb0-142">-FindByCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="c4eb0-142">-   FindByCertificatePolicy</span></span><br /><span data-ttu-id="c4eb0-143">-FindByExtension</span><span class="sxs-lookup"><span data-stu-id="c4eb0-143">-   FindByExtension</span></span><br /><span data-ttu-id="c4eb0-144">-FindByKeyUsage</span><span class="sxs-lookup"><span data-stu-id="c4eb0-144">-   FindByKeyUsage</span></span><br /><span data-ttu-id="c4eb0-145">-FindBySubjectKeyIdentifier</span><span class="sxs-lookup"><span data-stu-id="c4eb0-145">-   FindBySubjectKeyIdentifier</span></span><br /><br /> <span data-ttu-id="c4eb0-146">Özniteliğinde yer alan türün, `findValue` belirtilen gereksinimleri karşılaması gerekir `X509FindType` .</span><span class="sxs-lookup"><span data-stu-id="c4eb0-146">The type contained in the `findValue` attribute must satisfy the requirements of the specified `X509FindType`.</span></span><br /><br /> <span data-ttu-id="c4eb0-147">Varsayılan değer FindBySubjectDistinguishedName ' dir.</span><span class="sxs-lookup"><span data-stu-id="c4eb0-147">The default value is FindBySubjectDistinguishedName.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c4eb0-148">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c4eb0-148">Child Elements</span></span>  

 <span data-ttu-id="c4eb0-149">Yok.</span><span class="sxs-lookup"><span data-stu-id="c4eb0-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c4eb0-150">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c4eb0-150">Parent Elements</span></span>  
  
|<span data-ttu-id="c4eb0-151">Öğe</span><span class="sxs-lookup"><span data-stu-id="c4eb0-151">Element</span></span>|<span data-ttu-id="c4eb0-152">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c4eb0-152">Description</span></span>|  
|-------------|-----------------|  
|[\<peer>](peer-of-clientcredentials-element.md)|<span data-ttu-id="c4eb0-153">Eşler arası istemcilerin kimlik doğrulaması sırasında kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c4eb0-153">Specifies credentials used when authenticating peer-to-peer clients.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c4eb0-154">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c4eb0-154">Remarks</span></span>  

 <span data-ttu-id="c4eb0-155">Bu yapılandırma öğesi, eş kafeste komşuları doğrulanırken kullanılan bir X509Certificate2 örneği içeriyor.</span><span class="sxs-lookup"><span data-stu-id="c4eb0-155">This configuration element contains a X509Certificate2 instance used when authenticating neighbors in the peer mesh.</span></span>  
  
 <span data-ttu-id="c4eb0-156">Eşler arası programlama hakkında daha fazla bilgi için bkz. eşler [arası ağ iletişimi](../../../wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="c4eb0-156">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4eb0-157">Örnek</span><span class="sxs-lookup"><span data-stu-id="c4eb0-157">Example</span></span>  

 <span data-ttu-id="c4eb0-158">Aşağıdaki kod, eşler arası bir senaryoda kullanılan sertifikanın nasıl bulunacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c4eb0-158">The following code specifies how to find the certificate used in a peer-to-peer scenario.</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="MyEndpointBehavior">
      <clientCredentials>
        <peer>
          <certificate findValue="www.contoso.com"
                       storeLocation="LocalMachine"
                       x509FindType="FindByIssuerName" />
        </peer>
      </clientCredentials>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="c4eb0-159">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c4eb0-159">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateElement>
- <xref:System.ServiceModel.Security.PeerCredential.Certificate%2A>
- [<span data-ttu-id="c4eb0-160">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="c4eb0-160">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="c4eb0-161">Eşler Arası Ağ</span><span class="sxs-lookup"><span data-stu-id="c4eb0-161">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="c4eb0-162">[Eş kanal Iletisi kimlik doğrulaması](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="c4eb0-162">[Peer Channel Message Authentication](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="c4eb0-163">[Eş kanal özel kimlik doğrulaması](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="c4eb0-163">[Peer Channel Custom Authentication](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="c4eb0-164">Eş Kanalı Uygulamalarını Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="c4eb0-164">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
