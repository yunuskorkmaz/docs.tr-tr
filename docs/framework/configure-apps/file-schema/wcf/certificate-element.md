---
title: <certificate> Öğe
ms.date: 03/30/2017
ms.assetid: 9b3d9233-ef35-477a-bf5d-efd1e80a52f4
ms.openlocfilehash: eea8130911ca3780a6e4e753c17877e58c50b139
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59164274"
---
# <a name="certificate-element"></a><span data-ttu-id="86e9a-102">\<Sertifika > öğesi</span><span class="sxs-lookup"><span data-stu-id="86e9a-102">\<certificate> Element</span></span>
<span data-ttu-id="86e9a-103">İmzalama ve eşler arası istemcileri için iletileri şifrelemek için bir X.509 sertifikasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="86e9a-103">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer clients.</span></span>  
  
 <span data-ttu-id="86e9a-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="86e9a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="86e9a-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="86e9a-105">\<behaviors></span></span>  
<span data-ttu-id="86e9a-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="86e9a-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="86e9a-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="86e9a-107">\<behavior></span></span>  
<span data-ttu-id="86e9a-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="86e9a-108">\<clientCredentials></span></span>  
<span data-ttu-id="86e9a-109">\<Eş ></span><span class="sxs-lookup"><span data-stu-id="86e9a-109">\<peer></span></span>  
<span data-ttu-id="86e9a-110">\<Sertifika ></span><span class="sxs-lookup"><span data-stu-id="86e9a-110">\<certificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86e9a-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="86e9a-111">Syntax</span></span>  
  
```xml  
<certificate findValue="String"
             storeLocation="LocalMachine/CurrentUser"
             storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
             X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="86e9a-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="86e9a-112">Attributes and Elements</span></span>  
 <span data-ttu-id="86e9a-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="86e9a-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="86e9a-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="86e9a-114">Attributes</span></span>  
  
|<span data-ttu-id="86e9a-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="86e9a-115">Attribute</span></span>|<span data-ttu-id="86e9a-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="86e9a-116">Description</span></span>|  
|---------------|-----------------|  
|`findValue`|<span data-ttu-id="86e9a-117">X.509 sertifika deposunda aranacak değeri içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="86e9a-117">A string that contains the value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="86e9a-118">Özniteliğinde bulunan türü belirtilen gereksinimleri karşılaması gerekir `x509FindType`.</span><span class="sxs-lookup"><span data-stu-id="86e9a-118">The type contained in the attribute must satisfy the requirements of the specified `x509FindType`.</span></span> <span data-ttu-id="86e9a-119">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="86e9a-119">The default is an empty string.</span></span>|  
|`storeLocation`|<span data-ttu-id="86e9a-120">Eşin sertifikasını doğrulamak için istemcinin kullandığı X.509 Sertifika deposunun konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="86e9a-120">Specifies the location of the X.509 certificate store that the client uses to validate the peer's certificate against.</span></span> <span data-ttu-id="86e9a-121">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="86e9a-121">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="86e9a-122">-LocalMachine: yerel makineye atanmış sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="86e9a-122">-   LocalMachine: the certificate store assigned to the local machine.</span></span><br /><span data-ttu-id="86e9a-123">-CurrentUser: geçerli kullanıcıya atanmış sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="86e9a-123">-   CurrentUser: the certificate store assigned to the current user.</span></span><br /><br /> <span data-ttu-id="86e9a-124">LocalMachine varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="86e9a-124">The default is LocalMachine.</span></span>|  
|`storeName`|<span data-ttu-id="86e9a-125">Açılacak X.509 Sertifika deposunun adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="86e9a-125">Specifies the name of the X.509 certificate store to open.</span></span> <span data-ttu-id="86e9a-126">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="86e9a-126">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="86e9a-127">-Adres Defteri: Diğer kullanıcılar için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="86e9a-127">-   AddressBook: Certificate store for other users.</span></span><br /><span data-ttu-id="86e9a-128">-AuthRoot: Üçüncü taraf sertifika yetkilileri (CA'lar) için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="86e9a-128">-   AuthRoot: Certificate store for third-party certification authorities (CAs).</span></span><br /><span data-ttu-id="86e9a-129">-CertificateAuthority: Ara Sertifika yetkilileri (CA'lar) için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="86e9a-129">-   CertificateAuthority: Certificate store for intermediate certification authorities (CAs).</span></span><br /><span data-ttu-id="86e9a-130">-İzin verilmedi: İptal edilen sertifikalar için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="86e9a-130">-   Disallowed: Certificate store for revoked certificates.</span></span><br /><span data-ttu-id="86e9a-131">-My: Kişisel Sertifikalar için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="86e9a-131">-   My: Certificate store for personal certificates.</span></span><br /><span data-ttu-id="86e9a-132">-Kök: Güvenilen kök sertifika yetkilileri (CA'lar) için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="86e9a-132">-   Root: Certificate store for trusted root certification authorities (CAs).</span></span><br /><span data-ttu-id="86e9a-133">-TrustedPeople: Sertifika deposu-doğrudan güvenilen kişiler ve kaynaklar.</span><span class="sxs-lookup"><span data-stu-id="86e9a-133">-   TrustedPeople: Certificate store for directly-trusted people and resources.</span></span><br /><span data-ttu-id="86e9a-134">-TrustedPublisher: Doğrudan Güvenilen Yayımcılar sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="86e9a-134">-   TrustedPublisher: Certificate store for directly-trusted publishers.</span></span><br /><br /> <span data-ttu-id="86e9a-135">Varsayılan değer benim.</span><span class="sxs-lookup"><span data-stu-id="86e9a-135">The default is My.</span></span>|  
|`X509FindType`|<span data-ttu-id="86e9a-136">Yürütülecek X.509 arama türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="86e9a-136">Defines the type of X.509 search to be executed.</span></span> <span data-ttu-id="86e9a-137">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="86e9a-137">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="86e9a-138">-FindByThumbPrint</span><span class="sxs-lookup"><span data-stu-id="86e9a-138">-   FindByThumbPrint</span></span><br /><span data-ttu-id="86e9a-139">-FindBySubjectName</span><span class="sxs-lookup"><span data-stu-id="86e9a-139">-   FindBySubjectName</span></span><br /><span data-ttu-id="86e9a-140">-FindBySubjectDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="86e9a-140">-   FindBySubjectDistinguishedName</span></span><br /><span data-ttu-id="86e9a-141">-FindByIssuerName</span><span class="sxs-lookup"><span data-stu-id="86e9a-141">-   FindByIssuerName</span></span><br /><span data-ttu-id="86e9a-142">-FindByIssuerDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="86e9a-142">-   FindByIssuerDistinguishedName</span></span><br /><span data-ttu-id="86e9a-143">-FindBySerialNumber</span><span class="sxs-lookup"><span data-stu-id="86e9a-143">-   FindBySerialNumber</span></span><br /><span data-ttu-id="86e9a-144">-FindByTimeValid</span><span class="sxs-lookup"><span data-stu-id="86e9a-144">-   FindByTimeValid</span></span><br /><span data-ttu-id="86e9a-145">-FindByTimeNotYetValid</span><span class="sxs-lookup"><span data-stu-id="86e9a-145">-   FindByTimeNotYetValid</span></span><br /><span data-ttu-id="86e9a-146">-   FindByTemplateName</span><span class="sxs-lookup"><span data-stu-id="86e9a-146">-   FindByTemplateName</span></span><br /><span data-ttu-id="86e9a-147">-FindByApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="86e9a-147">-   FindByApplicationPolicy</span></span><br /><span data-ttu-id="86e9a-148">-FindByCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="86e9a-148">-   FindByCertificatePolicy</span></span><br /><span data-ttu-id="86e9a-149">-FindByExtension</span><span class="sxs-lookup"><span data-stu-id="86e9a-149">-   FindByExtension</span></span><br /><span data-ttu-id="86e9a-150">-   FindByKeyUsage</span><span class="sxs-lookup"><span data-stu-id="86e9a-150">-   FindByKeyUsage</span></span><br /><span data-ttu-id="86e9a-151">-FindBySubjectKeyIdentifier</span><span class="sxs-lookup"><span data-stu-id="86e9a-151">-   FindBySubjectKeyIdentifier</span></span><br /><br /> <span data-ttu-id="86e9a-152">Bulunan tür `findValue` öznitelik belirtilen gereksinimleri karşılaması gerekir `X509FindType`.</span><span class="sxs-lookup"><span data-stu-id="86e9a-152">The type contained in the `findValue` attribute must satisfy the requirements of the specified `X509FindType`.</span></span><br /><br /> <span data-ttu-id="86e9a-153">FindBySubjectDistinguishedName varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="86e9a-153">The default value is FindBySubjectDistinguishedName.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="86e9a-154">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="86e9a-154">Child Elements</span></span>  
 <span data-ttu-id="86e9a-155">Yok.</span><span class="sxs-lookup"><span data-stu-id="86e9a-155">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="86e9a-156">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="86e9a-156">Parent Elements</span></span>  
  
|<span data-ttu-id="86e9a-157">Öğe</span><span class="sxs-lookup"><span data-stu-id="86e9a-157">Element</span></span>|<span data-ttu-id="86e9a-158">Açıklama</span><span class="sxs-lookup"><span data-stu-id="86e9a-158">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="86e9a-159">\<Eş ></span><span class="sxs-lookup"><span data-stu-id="86e9a-159">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|<span data-ttu-id="86e9a-160">Eşler arası istemcilerin kimlik doğrulaması için kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="86e9a-160">Specifies credentials used when authenticating peer-to-peer clients.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="86e9a-161">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="86e9a-161">Remarks</span></span>  
 <span data-ttu-id="86e9a-162">Bu yapılandırma öğesi içinde Eş Ağ Komşuları kimlik doğrulaması için kullanılan bir X509Certificate2 örneği içerir.</span><span class="sxs-lookup"><span data-stu-id="86e9a-162">This configuration element contains a X509Certificate2 instance used when authenticating neighbors in the peer mesh.</span></span>  
  
 <span data-ttu-id="86e9a-163">Eşler arası programlama hakkında daha fazla bilgi için bkz. [eşler arası ağ](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="86e9a-163">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="86e9a-164">Örnek</span><span class="sxs-lookup"><span data-stu-id="86e9a-164">Example</span></span>  
 <span data-ttu-id="86e9a-165">Aşağıdaki kod, bir eşler arası senaryosunda kullanılan sertifikanın nasıl belirtir.</span><span class="sxs-lookup"><span data-stu-id="86e9a-165">The following code specifies how to find the certificate used in a peer-to-peer scenario.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="86e9a-166">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="86e9a-166">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateElement>
- <xref:System.ServiceModel.Security.PeerCredential.Certificate%2A>
- [<span data-ttu-id="86e9a-167">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="86e9a-167">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="86e9a-168">Eşler Arası Ağ</span><span class="sxs-lookup"><span data-stu-id="86e9a-168">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)
- [<span data-ttu-id="86e9a-169">Eş kanal ileti kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="86e9a-169">Peer Channel Message Authentication</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))
- [<span data-ttu-id="86e9a-170">Eş kanal özel kimlik doğrulama</span><span class="sxs-lookup"><span data-stu-id="86e9a-170">Peer Channel Custom Authentication</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))
- [<span data-ttu-id="86e9a-171">Eş Kanalı Uygulamalarını Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="86e9a-171">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
