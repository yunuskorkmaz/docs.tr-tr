---
title: <certificate> Öğesi
ms.date: 03/30/2017
ms.assetid: 9b3d9233-ef35-477a-bf5d-efd1e80a52f4
ms.openlocfilehash: 0594f04ab17a9561e895efcc92e97c16e77c0a4d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926198"
---
# <a name="certificate-element"></a><span data-ttu-id="6db47-102">\<Sertifika > öğesi</span><span class="sxs-lookup"><span data-stu-id="6db47-102">\<certificate> Element</span></span>
<span data-ttu-id="6db47-103">Eşler arası istemciler için ileti imzalama ve şifreleme için kullanılacak bir X. 509.952 sertifikası belirtir.</span><span class="sxs-lookup"><span data-stu-id="6db47-103">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer clients.</span></span>  
  
 <span data-ttu-id="6db47-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="6db47-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="6db47-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="6db47-105">\<behaviors></span></span>  
<span data-ttu-id="6db47-106">\<Endpointdavranışlar ></span><span class="sxs-lookup"><span data-stu-id="6db47-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="6db47-107">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="6db47-107">\<behavior></span></span>  
<span data-ttu-id="6db47-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="6db47-108">\<clientCredentials></span></span>  
<span data-ttu-id="6db47-109">\<eş ></span><span class="sxs-lookup"><span data-stu-id="6db47-109">\<peer></span></span>  
<span data-ttu-id="6db47-110">\<Sertifika ></span><span class="sxs-lookup"><span data-stu-id="6db47-110">\<certificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6db47-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6db47-111">Syntax</span></span>  
  
```xml  
<certificate findValue="String"
             storeLocation="LocalMachine/CurrentUser"
             storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
             X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6db47-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6db47-112">Attributes and Elements</span></span>  
 <span data-ttu-id="6db47-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6db47-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6db47-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6db47-114">Attributes</span></span>  
  
|<span data-ttu-id="6db47-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="6db47-115">Attribute</span></span>|<span data-ttu-id="6db47-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6db47-116">Description</span></span>|  
|---------------|-----------------|  
|`findValue`|<span data-ttu-id="6db47-117">X. 509.440 sertifika deposunda aranacak değeri içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="6db47-117">A string that contains the value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="6db47-118">Özniteliğinde yer alan türün, belirtilen `x509FindType`gereksinimleri karşılaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6db47-118">The type contained in the attribute must satisfy the requirements of the specified `x509FindType`.</span></span> <span data-ttu-id="6db47-119">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="6db47-119">The default is an empty string.</span></span>|  
|`storeLocation`|<span data-ttu-id="6db47-120">İstemcinin eşin sertifikasını doğrulamak için kullandığı X. 509.952 sertifika deposunun konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="6db47-120">Specifies the location of the X.509 certificate store that the client uses to validate the peer's certificate against.</span></span> <span data-ttu-id="6db47-121">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="6db47-121">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="6db47-122">-LocalMachine: yerel makineye atanan sertifika depolama alanı.</span><span class="sxs-lookup"><span data-stu-id="6db47-122">-   LocalMachine: the certificate store assigned to the local machine.</span></span><br /><span data-ttu-id="6db47-123">-CurrentUser: geçerli kullanıcıya atanmış sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="6db47-123">-   CurrentUser: the certificate store assigned to the current user.</span></span><br /><br /> <span data-ttu-id="6db47-124">Varsayılan değer LocalMachine 'dir.</span><span class="sxs-lookup"><span data-stu-id="6db47-124">The default is LocalMachine.</span></span>|  
|`storeName`|<span data-ttu-id="6db47-125">Açılacak X. 509.440 sertifika deposunun adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6db47-125">Specifies the name of the X.509 certificate store to open.</span></span> <span data-ttu-id="6db47-126">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="6db47-126">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="6db47-127">-AddressBook: Diğer kullanıcılar için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="6db47-127">-   AddressBook: Certificate store for other users.</span></span><br /><span data-ttu-id="6db47-128">-AuthRoot: Üçüncü taraf sertifika yetkilileri (CA 'Lar) için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="6db47-128">-   AuthRoot: Certificate store for third-party certification authorities (CAs).</span></span><br /><span data-ttu-id="6db47-129">CertificateAuthority Ara sertifika yetkilileri (CA 'Lar) için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="6db47-129">-   CertificateAuthority: Certificate store for intermediate certification authorities (CAs).</span></span><br /><span data-ttu-id="6db47-130">Veril İptal edilen sertifikalar için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="6db47-130">-   Disallowed: Certificate store for revoked certificates.</span></span><br /><span data-ttu-id="6db47-131">My Kişisel Sertifikalar için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="6db47-131">-   My: Certificate store for personal certificates.</span></span><br /><span data-ttu-id="6db47-132">Asıl Güvenilen kök sertifika yetkilileri (CA 'Lar) için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="6db47-132">-   Root: Certificate store for trusted root certification authorities (CAs).</span></span><br /><span data-ttu-id="6db47-133">TrustedPeople Doğrudan güvenilen kişiler ve kaynaklar için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="6db47-133">-   TrustedPeople: Certificate store for directly-trusted people and resources.</span></span><br /><span data-ttu-id="6db47-134">-TrustedPublisher: Doğrudan güvenilen yayımcılar için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="6db47-134">-   TrustedPublisher: Certificate store for directly-trusted publishers.</span></span><br /><br /> <span data-ttu-id="6db47-135">Varsayılan My.</span><span class="sxs-lookup"><span data-stu-id="6db47-135">The default is My.</span></span>|  
|`X509FindType`|<span data-ttu-id="6db47-136">Yürütülecek X. 509.440 aramasının türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6db47-136">Defines the type of X.509 search to be executed.</span></span> <span data-ttu-id="6db47-137">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="6db47-137">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="6db47-138">-Findbyparmak Izi</span><span class="sxs-lookup"><span data-stu-id="6db47-138">-   FindByThumbPrint</span></span><br /><span data-ttu-id="6db47-139">-FindBySubjectName</span><span class="sxs-lookup"><span data-stu-id="6db47-139">-   FindBySubjectName</span></span><br /><span data-ttu-id="6db47-140">- FindBySubjectDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="6db47-140">-   FindBySubjectDistinguishedName</span></span><br /><span data-ttu-id="6db47-141">-FindByIssuerName</span><span class="sxs-lookup"><span data-stu-id="6db47-141">-   FindByIssuerName</span></span><br /><span data-ttu-id="6db47-142">- FindByIssuerDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="6db47-142">-   FindByIssuerDistinguishedName</span></span><br /><span data-ttu-id="6db47-143">-FindBySerialNumber</span><span class="sxs-lookup"><span data-stu-id="6db47-143">-   FindBySerialNumber</span></span><br /><span data-ttu-id="6db47-144">-FindByTimeValid</span><span class="sxs-lookup"><span data-stu-id="6db47-144">-   FindByTimeValid</span></span><br /><span data-ttu-id="6db47-145">-FindByTimeNotYetValid</span><span class="sxs-lookup"><span data-stu-id="6db47-145">-   FindByTimeNotYetValid</span></span><br /><span data-ttu-id="6db47-146">-FindByTemplateName</span><span class="sxs-lookup"><span data-stu-id="6db47-146">-   FindByTemplateName</span></span><br /><span data-ttu-id="6db47-147">- FindByApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="6db47-147">-   FindByApplicationPolicy</span></span><br /><span data-ttu-id="6db47-148">-FindByCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="6db47-148">-   FindByCertificatePolicy</span></span><br /><span data-ttu-id="6db47-149">-FindByExtension</span><span class="sxs-lookup"><span data-stu-id="6db47-149">-   FindByExtension</span></span><br /><span data-ttu-id="6db47-150">-FindByKeyUsage</span><span class="sxs-lookup"><span data-stu-id="6db47-150">-   FindByKeyUsage</span></span><br /><span data-ttu-id="6db47-151">-FindBySubjectKeyIdentifier</span><span class="sxs-lookup"><span data-stu-id="6db47-151">-   FindBySubjectKeyIdentifier</span></span><br /><br /> <span data-ttu-id="6db47-152">`findValue` Özniteliğinde yer alan türün, belirtilen `X509FindType`gereksinimleri karşılaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6db47-152">The type contained in the `findValue` attribute must satisfy the requirements of the specified `X509FindType`.</span></span><br /><br /> <span data-ttu-id="6db47-153">Varsayılan değer FindBySubjectDistinguishedName ' dir.</span><span class="sxs-lookup"><span data-stu-id="6db47-153">The default value is FindBySubjectDistinguishedName.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6db47-154">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6db47-154">Child Elements</span></span>  
 <span data-ttu-id="6db47-155">Yok.</span><span class="sxs-lookup"><span data-stu-id="6db47-155">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6db47-156">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6db47-156">Parent Elements</span></span>  
  
|<span data-ttu-id="6db47-157">Öğe</span><span class="sxs-lookup"><span data-stu-id="6db47-157">Element</span></span>|<span data-ttu-id="6db47-158">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6db47-158">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6db47-159">\<eş ></span><span class="sxs-lookup"><span data-stu-id="6db47-159">\<peer></span></span>](peer-of-clientcredentials-element.md)|<span data-ttu-id="6db47-160">Eşler arası istemcilerin kimlik doğrulaması sırasında kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6db47-160">Specifies credentials used when authenticating peer-to-peer clients.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6db47-161">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6db47-161">Remarks</span></span>  
 <span data-ttu-id="6db47-162">Bu yapılandırma öğesi, eş kafeste komşuları doğrulanırken kullanılan bir X509Certificate2 örneği içeriyor.</span><span class="sxs-lookup"><span data-stu-id="6db47-162">This configuration element contains a X509Certificate2 instance used when authenticating neighbors in the peer mesh.</span></span>  
  
 <span data-ttu-id="6db47-163">Eşler arası programlama hakkında daha fazla bilgi için bkz. eşler [arası ağ iletişimi](../../../wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="6db47-163">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6db47-164">Örnek</span><span class="sxs-lookup"><span data-stu-id="6db47-164">Example</span></span>  
 <span data-ttu-id="6db47-165">Aşağıdaki kod, eşler arası bir senaryoda kullanılan sertifikanın nasıl bulunacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6db47-165">The following code specifies how to find the certificate used in a peer-to-peer scenario.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6db47-166">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6db47-166">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateElement>
- <xref:System.ServiceModel.Security.PeerCredential.Certificate%2A>
- [<span data-ttu-id="6db47-167">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="6db47-167">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="6db47-168">Eşler Arası Ağ</span><span class="sxs-lookup"><span data-stu-id="6db47-168">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="6db47-169">[Eş kanal Iletisi kimlik doğrulaması](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="6db47-169">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="6db47-170">[Eş kanal özel kimlik doğrulaması](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="6db47-170">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="6db47-171">Eş Kanalı Uygulamalarını Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="6db47-171">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
